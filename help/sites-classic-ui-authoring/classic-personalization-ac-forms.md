---
title: Erstellen von Adobe Campaign-Formularen in AEM
seo-title: Creating Adobe Campaign Forms in AEM
description: Mit AEM können Sie Formulare erstellen und bearbeiten, die auf Ihrer Website mit Adobe Campaign interagieren. Bestimmte Felder können in Ihre Formulare eingefügt und der Adobe Campaign-Datenbank zugeordnet werden.
seo-description: AEM lets you create and use forms that interact with Adobe Campaign on your website. Specific fields can be inserted into your forms and mapped to the Adobe Campaign database.
uuid: 7b1028f3-268a-4d4d-bc9f-acd176f5ef3d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 3086a8a1-8d2e-455a-a055-91b07d31ea65
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 53%

---


# Erstellen von Adobe Campaign-Formularen in AEM{#creating-adobe-campaign-forms-in-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit AEM können Sie Formulare erstellen und bearbeiten, die auf Ihrer Website mit Adobe Campaign interagieren. Bestimmte Felder können in Ihre Formulare eingefügt und der Adobe Campaign-Datenbank zugeordnet werden.

Sie können neue Kontaktanmeldungen, -abmeldungen und Benutzerprofildaten verwalten und gleichzeitig deren Daten in Ihre Adobe Campaign-Datenbank integrieren.

Um Adobe Campaign forms in AEM zu verwenden, müssen Sie die folgenden Schritte ausführen, die in diesem Dokument beschrieben werden:

1. Stellen Sie eine Vorlage zur Verfügung.
1. Erstellen Sie ein Formular.
1. Bearbeiten Sie den Formularinhalt.

Standardmäßig sind drei Formulartypen für Adobe Campaign verfügbar:

* Profil speichern
* Dienst abonnieren
* Abmeldung von einem Dienst

Diese Formulare definieren einen URL-Parameter, der den verschlüsselten Primärschlüssel eines Adobe Campaign-Profils akzeptiert. Basierend auf diesem URL-Parameter aktualisiert das Formular die Daten des zugehörigen Adobe Campaign-Profils.

Obwohl Sie diese Formulare unabhängig voneinander erstellen, generieren Sie in einem typischen Anwendungsfall einen personalisierten Link zu einer Formularseite innerhalb des Newsletter-Inhalts, damit Empfänger den Link öffnen und Anpassungen an ihren Profildaten vornehmen können (unabhängig davon, ob sie sich abmelden, abonnieren oder ihr Profil aktualisieren).

Das Formular wird basierend auf dem Benutzer automatisch aktualisiert. Siehe [Bearbeiten von Formularinhalten](#editing-form-content) für weitere Informationen.

## Verfügbarmachen von Vorlagen {#making-a-template-available}

Damit Sie für Adobe Campaign spezifische Formulare erstellen können, müssen Sie die verschiedenen Vorlagen in Ihrer AEM-Anwendung verfügbar machen.

Weitere Informationen hierzu finden Sie in der [Vorlagendokumentation](/help/sites-developing/page-templates-static.md#templateavailability).

Überprüfen Sie zunächst, ob die Verbindung zwischen der Autoren- und der Veröffentlichungsinstanz und Adobe Campaign funktioniert. Siehe [Integration mit Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) oder [Integration mit Adobe Campaign 6.1](/help/sites-administering/campaignonpremise.md).

>[!NOTE]
>
>Stellen Sie sicher, dass die Eigenschaft **acMapping** im Knoten **jcr:content** der Seite auf den Wert **mapRecipient** bzw. **Profil** eingestellt ist, wenn Sie mit Adobe Campaign 6.1.x oder Adobe Campaign Standard arbeiten.

### Erstellen von Formularen {#creating-a-form}

1. Beginnen Sie mit siteadmin.
1. Durchsuchen Sie die Baumstruktur so lange, bis Sie den Ort finden, an dem Sie das Formular auf der gewünschten Website erstellen möchten.
1. Wählen Sie **Neu** > **Neue Seite...** aus.
1. Wählen Sie entweder die Vorlage **Adobe Campaign-Profil (AC 6.1)** oder **Adobe Campaign-Profil (ACS)** aus und geben Sie die Seiteneigenschaften ein.

   >[!NOTE]
   >
   >Ist die Vorlage nicht verfügbar, finden Sie Informationen hierzu im Abschnitt [Verfügbarmachen von Vorlagen](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate).

1. Klicken Sie auf **Erstellen**, um das Formular zu erstellen.

   ![chlimage_1-187](assets/chlimage_1-187.png)

   Sie können dann [Bearbeiten und Konfigurieren des Formularinhalts](#editing-form-content).

## Bearbeiten von Formularinhalten {#editing-form-content}

Für Adobe Campaign dedizierte Forms verfügen über bestimmte Komponenten. Diese Komponenten bieten die Möglichkeit, jedes Formularfeld mit einem Feld in der Adobe Campaign-Datenbank zu verknüpfen.

>[!NOTE]
>
>Ist die gewünschte Vorlage nicht verfügbar, finden Sie weitere Informationen hierzu unter [Verfügbarmachen von Vorlagen](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate).

In diesem Abschnitt werden nur für Adobe Campaign spezifische Verknüpfungen behandelt. Weitere Informationen und einen allgemeineren Überblick darüber, wie Sie Formulare in Adobe Experience Manager verwenden, finden Sie unter [Komponenten des Bearbeitungsmodus](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md).

1. Navigieren Sie zu dem Formular, das Sie bearbeiten möchten.
1. Wählen Sie in der Toolbox **Seite** > **Seiteneigenschaften...** aus und navigieren Sie zur Registerkarte **Cloud-Services** des Popup-Fensters.
1. Fügen Sie den Adobe Campaign-Service hinzu, indem Sie auf **Service hinzufügen** klicken und anschließend aus der Dropdown-Liste der Services die Konfiguration auswählen, die Ihrer Adobe Campaign-Instanz entspricht. Diese Konfiguration wird bei der Einrichtung der Verbindung zwischen den Instanzen durchgeführt. Weitere Informationen finden Sie unter [Verbinden von AEM mit Adobe Campaign](/help/sites-administering/campaignonpremise.md#connecting-aem-to-adobe-campaign).

   >[!NOTE]
   >
   >Entsperren Sie (falls nötig) die Konfiguration, indem Sie auf das Schloss klicken. Der Adobe Campaign-Service kann nun hinzugefügt werden.

1. Greifen Sie auf die allgemeinen Parameter des Formulars zu, indem Sie auf die Schaltfläche **Bearbeiten** klicken, die sich am Anfang des Formulars befindet. Auf der Registerkarte **Formular** können Sie eine Dankeseite auswählen, zu der der Benutzer nach der Überprüfung des Formulars weitergeleitet wird.

   Im Formular **Erweitert** können Sie den Formulartyp auswählen. Das Feld **Post-Optionen** ermöglicht Ihnen die Wahl zwischen drei Typen von Adobe Campaign-Formularen:

   * **Adobe Campaign: Profil speichern**: ermöglicht die Erstellung oder Aktualisierung eines Empfängers in Adobe Campaign (Standardwert).
   * **Adobe Campaign: Abonnieren von Diensten**: ermöglicht die Verwaltung der Empfängeranmeldungen in Adobe Campaign.
   * **Adobe Campaign: Abmeldung von Diensten**: ermöglicht Ihnen, die Abonnements eines Empfängers in Adobe Campaign abzubrechen.

   Über das Feld **Aktionskonfiguration** können Sie angeben, ob Sie das Empfängerprofil in der Adobe Campaign-Datenbank erstellen möchten, falls es noch nicht vorhanden ist. Aktivieren Sie hierzu die Option **Nicht vorhandene Benutzer erstellen**.

1. Fügen Sie die ausgewählten Komponenten hinzu, indem Sie sie aus der Toolbox ziehen und in das Formular ablegen. Weitere Informationen zu den verfügbaren Adobe Campaign-spezifischen Komponenten finden Sie unter [Adobe-Formularkomponenten](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md).

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Konfigurieren Sie die hinzugefügten Felder, indem Sie doppelt darauf klicken. Auf der Registerkarte **Adobe Campaign** können Sie das Feld mit einem Feld in der Empfängertabelle von Adobe Campaign verknüpfen. Sie können zudem ebenfalls festlegen, ob das Feld Teil des Abstimmschlüssels ist, mit dessen Hilfe bereits in der Adobe Campaign-Datenbank erfasste Empfänger identifiziert werden können.

   >[!CAUTION]
   >
   >Der **Elementname** muss für jedes Formularfeld unterschiedlich sein. Ändern Sie ihn bei Bedarf.
   >
   >Jedes Formular muss eine Komponente des Typs **Verschlüsselter Primärschlüssel** aufweisen, damit die Empfänger in der Adobe Campaign-Datenbank ordnungsgemäß verwaltet werden können.

1. Aktivieren Sie die Seite, indem Sie in der Toolbox **Seite** > **Seite aktivieren** auswählen. Die Seite wird auf Ihrer Site aktiviert. Sie können sie anzeigen, indem Sie zu Ihrer AEM Veröffentlichungsinstanz wechseln. Die Daten in der Adobe Campaign-Datenbank werden aktualisiert, sobald ein Formular validiert wurde.

## Testen eines Formulars {#testing-a-form}

Nachdem Sie ein Formular erstellt und den Formularinhalt bearbeitet haben, können Sie manuell testen, ob das Formular erwartungsgemäß funktioniert.

>[!NOTE]
>
>Jedes Formular muss eine Komponente des Typs **Verschlüsselter Primärschlüssel** aufweisen. Wählen Sie aus den Komponenten Adobe Campaign aus, sodass nur die entsprechenden Komponenten angezeigt werden.
>
>Obwohl Sie bei diesem Verfahren die EPK-Nummer manuell eingeben, erhalten Benutzer in der Praxis einen Link zu dieser Seite (ob sie sich abmelden, abonnieren oder Ihr Profil aktualisieren möchten) in einem Newsletter. Je nach Benutzer wird der EPK automatisch aktualisiert.
>
>Verwenden Sie zur Herstellung dieser Verknüpfung die Variable **Hauptressourcenkennung** (Adobe Campaign Standard) oder **Verschlüsselte Kennung** (Adobe Campaign 6.1) (beispielsweise in einer Komponente des Typs **Text und Personalisierung (Kampagne)**), die eine Verknüpfung mit dem EPK in Adobe Campaign herstellt.

Dazu müssen Sie das EPK eines Adobe Campaign-Profils manuell abrufen und an die URL anhängen:

1. So rufen Sie den verschlüsselten Primärschlüssel (EPK) eines Adobe Campaign-Profils ab:

   * Navigieren Sie in Adobe Campaign Standard zu **Profile und Zielgruppen** > **Profile**. Hier werden alle vorhandenen Profile aufgeführt. Stellen Sie sicher, dass das Feld **Hauptressourcenkennung** in einer der Spalten angezeigt wird (dies kann durch Klicken oder Tippen auf **Liste konfigurieren** eingestellt werden). Kopieren Sie die Hauptressourcenkennung des gewünschten Profils.
   * Navigieren Sie in Adobe Campaign 6.11 zu **Profile und Ziele** > **Empfänger**. Hier werden alle vorhandenen Profile aufgeführt. Stellen Sie sicher, dass das Feld **Verschlüsselte Kennung** in einer der Spalten angezeigt wird (dies kann durch einen Rechtsklick auf einen Eintrag und die Auswahl von **Liste konfigurieren...** eingestellt werden). Kopieren Sie die verschlüsselte Kennung des gewünschten Profils.

1. Öffnen Sie in AEM die Formularseite in der Veröffentlichungsinstanz und fügen Sie den EPK aus Schritt 1 als URL-Parameter an: Verwenden Sie den gleichen Namen, den Sie zuvor in der EPK-Komponente beim Erstellen des Formulars verwendet haben (Beispiel: `?epk=...`).
1. Mit dem Formular können jetzt die mit dem verknüpften Adobe Campaign-Profil verknüpften Daten und Abonnements geändert werden. Nachdem Sie einige Felder geändert und das Formular übermittelt haben, können Sie in Adobe Campaign überprüfen, ob die entsprechenden Daten aktualisiert wurden.

Die Daten in der Adobe Campaign-Datenbank werden aktualisiert, sobald ein Formular validiert wurde.
