---
title: Erstellen von Adobe Campaign-Formularen in AEM
seo-title: Creating Adobe Campaign Forms in AEM
description: Mit AEM können Sie Formulare erstellen und bearbeiten, die auf Ihrer Website mit Adobe Campaign interagieren
seo-description: AEM lets you create and use forms that interact with Adobe Campaign on your website
uuid: 61778ea7-c4d7-43ee-905f-f3ecb752aae2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: d53ef3e2-14ca-4444-b563-be67be15c040
exl-id: 347ce0a6-6d39-4342-8d0d-4ec76633146d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 39%

---

# Erstellen von Adobe Campaign-Formularen in AEM {#creating-adobe-campaign-forms-in-aem}

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

Weitere Informationen hierzu finden Sie in der [Vorlagendokumentation](/help/sites-developing/templates.md#template-availability).

## Erstellen von Formularen {#creating-a-form}

Überprüfen Sie zunächst, ob die Verbindung zwischen der Autoren- und der Veröffentlichungsinstanz und Adobe Campaign funktioniert. Siehe [Integration mit Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) oder [Integration mit Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md).

>[!NOTE]
>
>Stellen Sie sicher, dass die Eigenschaft **acMapping** im Knoten **jcr:content** der Seite auf den Wert **mapRecipient** bzw. **profile** eingestellt ist, wenn Sie mit Adobe Campaign Classic oder Adobe Campaign Standard arbeiten.

1. Navigieren Sie in AEM unter „Sites“ an den Ort, an dem Sie eine neue Seite erstellen möchten.
1. Erstellen Sie eine Seite, wählen Sie **Adobe Campaign Classic-Profil** oder **Adobe Campaign Standard-Profil** aus und klicken Sie auf **Weiter**.

   ![chlimage_1-43](assets/chlimage_1-43.png)

   >[!NOTE]
   >
   >Ist die gewünschte Vorlage nicht verfügbar, finden Sie weitere Informationen hierzu unter [Verfügbarmachen von Vorlagen](/help/sites-developing/templates.md#template-availability).

1. Im **Name** -Feld den Namen der Seite hinzufügen. Es muss sich um einen gültigen JCR-Namen handeln.
1. Im **Titel** ein, geben Sie einen Titel ein und klicken Sie auf **Erstellen**.
1. Öffnen Sie die Seite und wählen Sie **Eigenschaften öffnen** Fügen Sie in Cloud Services die Adobe Campaign-Konfiguration hinzu und wählen Sie das Häkchen aus, um Ihre Änderungen zu speichern.

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Auf der Seite im **Formularstart** -Komponente, wählen Sie den Formulartyp aus, den sie lautet: **Abonnieren, Abmelden,** oder **Profil speichern**. Pro Formular kann nur ein Typ gewählt werden. Sie können den [Inhalt des Formulars nun bearbeiten](#editing-form-content).

## Bearbeiten von Formularinhalten {#editing-form-content}

Für Adobe Campaign dedizierte Forms verfügen über bestimmte Komponenten. Diese Komponenten bieten die Möglichkeit, jedes Formularfeld mit einem Feld in der Adobe Campaign-Datenbank zu verknüpfen.

>[!NOTE]
>
>Ist die gewünschte Vorlage nicht verfügbar, finden Sie weitere Informationen hierzu unter [Verfügbarmachen von Vorlagen](/help/sites-authoring/adobe-campaign.md).

In diesem Abschnitt werden nur für Adobe Campaign spezifische Verknüpfungen behandelt. Weitere Informationen und einen allgemeineren Überblick darüber, wie Sie Formulare in Adobe Experience Manager verwenden, finden Sie unter [Komponenten des Bearbeitungsmodus](/help/sites-authoring/default-components-foundation.md).

1. Wählen Sie **Eigenschaften öffnen** aus. Fügen Sie den Cloud-Services die Adobe Campaign-Konfiguration hinzu und klicken Sie auf das Häkchen, um die Änderungen zu übernehmen.

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. Klicken Sie auf der Seite in der Komponente **Formular-Start** auf das Symbol für die Konfiguration.

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. Klicken Sie auf die Registerkarte **Erweitert**, wählen Sie den Formulartyp (**Abonnieren, Abonnement kündigen** oder **Profil speichern**) aus und klicken Sie auf **OK.** Pro Formular kann nur ein Typ gewählt werden.

   * **Adobe Campaign: Profil speichern**: ermöglicht die Erstellung oder Aktualisierung eines Empfängers in Adobe Campaign (Standardwert).
   * **Adobe Campaign: Abonnieren von Diensten**: ermöglicht die Verwaltung der Empfängeranmeldungen in Adobe Campaign.
   * **Adobe Campaign: Abmeldung von Diensten**: ermöglicht Ihnen, die Abonnements eines Empfängers in Adobe Campaign abzubrechen.

1. Sie müssen über eine **Verschlüsselter Primärer Schlüssel** -Komponente in jedem Formular. Diese Komponente definiert, welcher URL-Parameter zum Akzeptieren des verschlüsselten Primärschlüssels eines Adobe Campaign-Profils verwendet wird. Wählen Sie aus den Komponenten Adobe Campaign aus, sodass nur die entsprechenden Komponenten angezeigt werden.
1. Ziehen Sie die Komponente **Verschlüsselter Primärschlüssel** an eine beliebige Stelle im Formular und klicken oder tippen Sie auf Sie das Symbol für die **Konfiguration**. Im **Adobe Campaign** -Registerkarte einen beliebigen Namen für den URL-Parameter angeben. Klicken oder tippen Sie auf das Häkchen, um Ihre Änderungen zu speichern.

   Generierte Links zu diesem Formular müssen diesen URL-Parameter verwenden und ihn dem verschlüsselten Primärschlüssel eines Adobe Campaign-Profils zuweisen. Der verschlüsselte Primärschlüssel muss ordnungsgemäß URL (Prozent)-kodiert sein.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. Fügen Sie dem Formular nach Bedarf Komponenten hinzu, z. B. ein Textfeld, ein Datumsfeld, ein Kontrollkästchen, ein Optionsfeld usw. Siehe [Adobe Campaign-Formularkomponenten](/help/sites-authoring/adobe-campaign-components.md) für weitere Informationen zu den einzelnen Komponenten.
1. Klicken Sie auf das Symbol Konfiguration , um die Komponente zu öffnen. Ändern Sie beispielsweise in der Komponente **Textfeld (Kampagne)** den Titel und den Text.

   Klicken Sie auf **Adobe Campaign**, um das Formularfeld mit einer Adobe Campaign-Metadatenvariable zu verknüpfen. Wenn Sie das Formular senden, wird das zugeordnete Feld in Adobe Campaign aktualisiert. In der Variablenauswahl sind nur Felder mit übereinstimmenden Typen verfügbar (z. B. Zeichenfolgenvariablen für Textfelder).

   ![chlimage_1-48](assets/chlimage_1-48.png)

   >[!NOTE]
   >
   >Sie können in der Empfängertabelle aufgeführte Felder wie auf der folgenden Seite beschrieben hinzufügen oder entfernen: [https://blogs.adobe.com/experiencedelivers/experience-management/aem-campaign-integration/](https://blogs.adobe.com/experiencedelivers/experience-management/aem-campaign-integration/)

1. Klicken **Seite veröffentlichen**. Die Seite wird auf Ihrer Site aktiviert. Sie können sie anzeigen, indem Sie zu Ihrer AEM Veröffentlichungsinstanz wechseln. Sie können auch [Formular testen](#testing-a-form).

   >[!CAUTION]
   >
   >Sie müssen dem anonymen Benutzer im Cloud-Service Leseberechtigungen erteilen, um Formulare in der Veröffentlichungsumgebung verwenden zu können. Beachten Sie jedoch die potenziellen Sicherheitsprobleme bei der Bereitstellung von Leseberechtigungen für den anonymen Benutzer und stellen Sie sicher, dass Sie dies verringern, indem Sie beispielsweise den Dispatcher konfigurieren.

## Testen eines Formulars {#testing-a-form}

Nachdem Sie ein Formular erstellt und den Formularinhalt bearbeitet haben, können Sie manuell testen, ob das Formular erwartungsgemäß funktioniert.

>[!NOTE]
>
>Jedes Formular muss eine Komponente des Typs **Verschlüsselter Primärschlüssel** aufweisen. Wählen Sie aus den Komponenten Adobe Campaign aus, sodass nur die entsprechenden Komponenten angezeigt werden.
>
>Obwohl Sie bei diesem Verfahren die EPK-Nummer manuell eingeben, erhalten Benutzer in der Praxis einen Link zu dieser Seite (ob sie sich abmelden, abonnieren oder Ihr Profil aktualisieren möchten) in einem Newsletter. Je nach Benutzer wird der EPK automatisch aktualisiert.
>
>Verwenden Sie zum Erstellen dieses Links die Variable **Hauptressourcenkennung** (Adobe Campaign Standard) oder **Verschlüsselte Kennung** (Adobe Campaign Classic) (beispielsweise in einer Komponente des Typs **Text und Personalisierung (Kampagne)**), die eine Verknüpfung mit dem EPK in Adobe Campaign herstellt.

Dazu müssen Sie das EPK eines Adobe Campaign-Profils manuell abrufen und an die URL anhängen:

1. So rufen Sie den verschlüsselten Primärschlüssel (EPK) eines Adobe Campaign-Profils ab:

   * Navigieren Sie in Adobe Campaign Standard zu **Profile und Zielgruppen** > **Profile**. Hier werden alle vorhandenen Profile aufgeführt. Stellen Sie sicher, dass das Feld **Hauptressourcenkennung** in einer der Spalten angezeigt wird (dies kann durch Klicken oder Tippen auf **Liste konfigurieren** eingestellt werden). Kopieren Sie die Hauptressourcenkennung des gewünschten Profils.
   * Navigieren Sie in Adobe Campaign Classic zu **Profile und Ziele** > **Empfänger**. Hier sind alle vorhandenen Profile aufgeführt. Stellen Sie sicher, dass das Feld **Verschlüsselte Kennung** in einer der Spalten angezeigt wird (dies kann durch einen Rechtsklick auf einen Eintrag und die Auswahl von **Liste konfigurieren…** eingestellt werden). Kopieren Sie die verschlüsselte Kennung des gewünschten Profils.

1. Öffnen Sie in AEM die Formularseite in der Veröffentlichungsinstanz und fügen Sie den EPK aus Schritt 1 als URL-Parameter an: Verwenden Sie den gleichen Namen, den Sie zuvor in der EPK-Komponente beim Erstellen des Formulars verwendet haben (Beispiel: `?epk=...`).
1. Mit dem Formular können jetzt die mit dem verknüpften Adobe Campaign-Profil verknüpften Daten und Abonnements geändert werden. Nachdem Sie einige Felder geändert und das Formular übermittelt haben, können Sie in Adobe Campaign überprüfen, ob die entsprechenden Daten aktualisiert wurden.

Die Daten in der Adobe Campaign-Datenbank werden aktualisiert, sobald ein Formular validiert wurde.
