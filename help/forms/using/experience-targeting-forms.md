---
title: Erstellen zielgerichteter Erlebnisse in AEM Forms
seo-title: Create targeted experiences in AEM Forms
description: 'Mithilfe von AEM Forms können Sie personalisierte Erlebnisse für bestimmte Zielgruppen bieten. '
seo-description: Use Target in AEM Forms to create customized experiences for targeted customers.
uuid: 174b6054-8fe3-4ab2-8afd-435e5dff9044
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integrations
discoiquuid: 6cf54a08-d429-4a58-8429-a1cb784448d1
exl-id: 5a10ffea-2c69-4902-9754-399bd2e125f1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 31%

---

# Erstellen zielgerichteter Erlebnisse in AEM Forms {#create-targeted-experiences-in-aem-forms}

## Integrieren von Adobe Target mit AEM Forms {#integrate-adobe-target-with-aem-forms}

Durch die Integration von Adobe Target mit AEM können Sie die personalisierte Erlebnisse für bestimmte Zielgruppen erstellen. Mit Adobe Target können Sie A/B-Tests erstellen, Benutzerreaktionen messen und personalisierte Web-Inhalte für die anzusprechenden Benutzer generieren. Sie können Adobe Target in AEM Forms integrieren, um Bildkomponenten adaptiver Formulare und interaktiver Kommunikation auszuwählen.

Konfigurieren Sie Adobe Target in AEM für die Verwendung mit adaptiven Formularen und interaktiver Kommunikation, siehe [Erstellen einer Target-Konfiguration in AEM](/help/sites-administering/target.md) und [Framework hinzufügen](/help/sites-administering/target.md).

>[!NOTE]
>
>Targeting funktioniert, wenn Ihr adaptives Formular oder Ihre interaktive Kommunikation mit einem Hostnamen oder einer IP-Adresse wiedergegeben wird. Es schlägt fehl, wenn das adaptive Formular oder die interaktive Kommunikation mit localhost wiedergegeben wird.

## Target- Aktivität erstellen {#creating-a-target-activity}

1. Tippen **Adobe Experience Manager > Personalisierung > Aktivitäten**.

   `https://<hostname>:<port>/libs/cq/personalization/touch-ui/content/v2/activities.html`

1. Tippen Sie auf der Seite &quot;Aktivitäten&quot;auf **Erstellen > Marke erstellen**.
1. Sie werden aufgefordert, eine Vorlage auswählen und Eigenschaften einzugeben.

   Vorlage auswählen, tippen Sie auf **Weiter.** Geben Sie den Titel Ihrer Marke im Abschnitt Eigenschaften ein und tippen Sie auf **Erstellen Sie.**
Ihre Marke wird jetzt auf der Seite Aktivitäten aufgeführt.

1. Tippen Sie auf der Seite „Aktivitäten“ auf Ihre Marke.
1. Tippen Sie im Übergeordneten Bereich Ihrer Marke auf **Erstellen** > **Aktivität erstellen**.

   Beim Erstellen einer Aktivität geben Sie deren Details, Ziel und Einstellungen an.

   Der Detailbereich enthält den Namen, die Targeting-Engine und die Zielsetzung. Wenn Sie Adobe Target als Targeting-Engine wählen, wird die Option für die Target-Cloud-Konfiguration aktiviert. Wählen Sie Ihre Target-Cloud-Konfiguration, wählen Sie den Aktivitätstyp, geben Sie das Ziel der Aktivität an und tippen Sie auf **Nächste**. Interaktive Kommunikation unterstützt nur den Aktivitätstyp Erlebnis-Targeting .

   Im Abschnitt „Target“ können Sie das Erlebnis für die Zielgruppe hinzufügen und benennen. Klicken **Erlebnis hinzufügen** um die **Zielgruppe auswählen** und **Erlebnis benennen** Optionen. Tippen **Zielgruppe auswählen** um eine Liste der Zielgruppen und ihrer Quelle anzuzeigen. Wählen Sie eine Zielgruppe aus der Liste „Zielgruppenname“ aus. Tippen **Erlebnis hinzufügen** , um das Erlebnis zu benennen, und tippen Sie auf **Nächste**.

   Im Abschnitt „Ziele und Einstellungen“ können Sie den Zeitplan und die Priorität für Ihre Aktivität festlegen. Legen Sie das Startdatum, Enddatum und die Priorität der Aktivität, Zielmetrik und zusätzlichen Metrik fest und tippen Sie auf **Speichern**.

   Die Aktivität wird jetzt in Ihrer Markenseite aufgeführt.

   >[!NOTE]
   >
   >Sie können den Fehler &quot;Ihre Aktivität wurde gespeichert, aber nicht mit Target synchronisiert&quot;ignorieren. Grund: Das folgende Erlebnis hat keine Angebote&quot;, wenn es beim Speichern der Aktivität auftritt.

1. Um Target zu aktivieren, bearbeiten Sie die .jsp-Datei, um Client-Bibliotheken einzuschließen, die Ihre adaptive Formularvorlage verwendet.

   Klicken Sie beispielsweise in der vordefinierten Implementierung auf **Instrumente** >  **CRXDE Lite**.

   Geben Sie in der Adressleiste der CRXDE Lite /libs/fd/af/components/page/base/head.jsp ein, um die Datei head.jsp zu bearbeiten.

   Diese Implementierung verwendet die Vorlage simpleEnrollment . In dieser Implementierung müssen Sie die Datei head.jsp wie folgt ändern und dabei die folgenden Clientbibliotheken aufnehmen:

   `<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>`

   `<cq:include path="clientcontext_optimized" resourceType="/libs/cq/personalization/components/clientcontext_optimized"/>`

   `<cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>`

1. Um das Target-Framework für adaptive Formulare zu aktivieren, navigieren Sie zu Ihrem Formular oder zu Ihrer interaktiven Kommunikation und öffnen Sie es im Bearbeitungsmodus.

   Um ein Formular oder eine interaktive Kommunikation im Bearbeitungsmodus zu öffnen, tippen Sie auf **Auswählen** und tippen Sie dann auf **Öffnen**.

   Alternativ dazu werden vier Schaltflächen angezeigt, wenn Sie den Mauszeiger über das Formular- oder interaktive Kommunikationssymbol bewegen, ohne es auszuwählen. Sie können auf die **Bearbeiten** angezeigt, um das Formular im Bearbeitungsmodus zu öffnen.

1. Tippen Sie in der Seitensymbolleiste auf **Seiteninformationen** ![theme-options](assets/theme-options.png) > **Eigenschaften öffnen**.
1. Wählen Sie im Tab Allgemein eine Konfiguration für die **Adobe Target** -Feld. Tippen Sie auf **Speichern und schließen**.

## Anwenden der erstellten Aktivität auf ein Bild eines adaptiven Formulars oder ein interaktives Kommunikationsbild {#applying-created-activity-to-an-adaptive-form-image-or-an-interactive-communication-image}

1. Öffnen Sie das adaptive Formular und die interaktive Kommunikation zur Bearbeitung. Wenn Sie eine interaktive Kommunikation öffnen, öffnen Sie den Webkanal.

1. Fügen Sie im Authoring-Modus Ihrer interaktiven Kommunikation oder Ihres adaptiven Formulars ein Bild hinzu, das als Ziel ausgewählt werden soll.

   >[!NOTE]
   >
   >AEM Forms unterstützt nur Targeting von Bildkomponenten. Stellen Sie sicher, dass das Bedienfeld, in dem sich die Bildkomponente befindet, keine andere Komponente enthält und die Anzahl der Spalten für das Bedienfeld auf 1 eingestellt ist.

1. Zwischen **Bearbeiten** nach **Targeting** -Modus. Die Option zum Wechseln der Modi befindet sich oben rechts.
1. Wählen Sie eine **MARKE** auswählen **AKTIVITÄT** und tippen Sie auf **Targeting starten**. Die **Zielgruppen** auf der rechten Seite des Editors angezeigt.

   ![Targeting-Menü](assets/targeting-menu.png)

1. Wählen Sie eine Zielgruppe aus dem **Zielgruppen** und tippen Sie auf das gewünschte Bild. Ein Menü wird angezeigt. Tippen Sie im Menü auf **Target**. Tippen Sie auf das Bild und tippen Sie auf **Konfigurieren**. Wählen Sie im Eigenschaftenfenster das Bild aus, das für die ausgewählte Audience angezeigt werden soll. Wiederholen Sie den Schritt für alle Zielgruppen. Das Erlebnis-Targeting ist für das Bild in der interaktiven Kommunikation oder im adaptiven Formular aktiviert.

## Überprüfen Sie, ob die erstellte Aktivität mit dem Target-Server synchronisiert wird. {#check-if-the-created-activity-syncs-with-the-target-server}

Aktivitäten, die für das Targeting verwendet werden, werden mit dem Target-Server synchronisiert. Um zu überprüfen, ob Ihre Aktivität mit dem Zielserver synchron ist, überprüfen Sie den Status Ihrer Aktivität auf Ihrer Markenseite.

Vergewissern Sie sich, dass die Aktivität den Status „Synchronisiert“ aufweist.

## Target-Verhalten validieren {#validate-target-behavior}

Target-Verhalten validieren:

* Verwenden Sie Targeting mit `wcmmode preview` im Autorenmodus
* Verwenden Sie Targeting mit `wcmmode preview` und `wcmmode disabled` im Veröffentlichungsmodus

## Targeting für die Bildkomponente überwachen {#monitor-targeting-for-the-image-component}

Um das Targeting für Bildkomponenten in Ihrem Formular zu überwachen, veröffentlichen Sie Ihre Bilder und Aktivitäten sowie das adaptive Formular.

## Offene Probleme {#open-issues}

Ausdruck für die Sichtbarkeit: Festlegen des Fokus schläft für Targeting-Bilder auf adaptiven Formularen fehl.
