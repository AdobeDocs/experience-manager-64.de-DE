---
title: Verwenden von Adobe Sign in einem adaptiven Formular
seo-title: Verwenden von Adobe Sign in einem adaptiven Formular
description: 'Indem Sie Workflows mit e-Signatur (Adobe Sign) für ein adaptives Formular aktivieren, können Sie Signatur-Workflows automatisieren, Prozesse mit einer oder mehreren Signaturen vereinfachen und Formulare elektronisch von Mobilgeräten aus signieren. '
seo-description: Indem Sie Workflows mit e-Signatur (Adobe Sign) für ein adaptives Formular aktivieren, können Sie Signatur-Workflows automatisieren, Prozesse mit einer oder mehreren Signaturen vereinfachen und Formulare elektronisch von Mobilgeräten aus signieren.
uuid: 9c65dc44-c1a5-44df-8659-6efbe347575b
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 29fc297e-0a95-4d2a-bfe6-5676d53624db
noindex: true
feature: Adaptives Forms, Adobe Sign
translation-type: tm+mt
source-git-commit: 5944eab0bf38551970685eaa98d90c4459720245
workflow-type: tm+mt
source-wordcount: '3596'
ht-degree: 68%

---


# Verwenden von Adobe Sign in einem adaptiven Formular {#using-adobe-sign-in-an-adaptive-form}

Indem Sie Workflows mit e-Signatur (Adobe Sign) für ein adaptives Formular aktivieren, können Sie Signatur-Workflows automatisieren, Prozesse mit einer oder mehreren Signaturen vereinfachen und Formulare elektronisch von Mobilgeräten aus signieren.

Adobe Sign ermöglicht Workflows mit e-Signaturen für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. a.

In einem typischen Szenario mit Adobe Sign und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um eine Dienstleistung zu beantragen. Beispielsweise sind für einen Hypotheken- und oder Kreditkartenantrag rechtskräftige Signaturen von allen Kreditnehmern und Mitantragstellern erforderlich. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie Adobe Sign in AEM Forms integrieren. Einige weitere Anwendungsbeispiele für Adobe Sign sind:

* Geschäftsabschlüsse von jedem Gerät aus mit vollautomatischen Prozessen für Vorschlag, Angebot und Vertrag.
* Schnelleres Abschließen von Prozessen im Personalwesen und Zugang zu digitalen Abläufen für Ihre Mitarbeiter.
* Kürzere Vertragszyklen und schnelleres Onboarding Ihrer Lieferanten.
* Erstellen digitaler Workflows zur Automatisierung häufig verwendeter Prozesse.

Die Integration von Adobe Sign in AEM Forms unterstützt die folgenden Funktionen:

* Workflows für Signaturen eines einzelnen oder mehrerer Benutzer
* Workflows mit sequenzieller und simultaner Signatur
* Abläufe für Signaturen innerhalb und außerhalb des Formulars
* Signieren von Formularen als anonymer oder angemeldeter Benutzer
* Dynamische Signaturvorgänge (Integration mit AEM Forms-Workflow)
* Authentifizierung über eine Wissensdatenbank, ein Telefon und soziale Profile

Erfahren Sie mehr über die bewährten Vorgehensweisen bei der Verwendung von Adobe Sign mit adaptiven Formularen](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684), um bessere Unterschriftserfahrungen zu erstellen.[

## Voraussetzungen {#prerequisites}

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind, bevor Sie Adobe Sign in einem adaptiven Formular verwenden:

* Vergewissern Sie sich, dass der AEM Forms-Cloud-Service für die Verwendung von Adobe Sign konfiguriert ist. Weitere Informationen finden Sie unter [Integrieren von Adobe Sign mit AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).
* Halten Sie die Liste der Unterzeichner bereit. Sie benötigen mindestens eine E-Mail-Adresse für jeden Unterzeichner.

## Adobe Sign für adaptive Formulare konfigurieren {#configure-adobe-sign-for-an-adaptive-form}

Führen Sie die folgenden Schritte durch, um Adobe Sign für adaptive Formulare zu konfigurieren:

1. [Eigenschaften von adaptiven Formularen für Adoben bearbeiten](#enableadobesign)
1. [Adobe Sign-Felder zu adaptivem Formular hinzufügen](#addadobesignfieldstoanadaptiveform)
1. [Adobe Sign für adaptives Formular aktivieren](#enableadobsignforanadaptiveform)
1. [Cloud-Service von Adobe Sign für adaptives Formular wählen](#selectadobesigncloudserviceforanadaptiveform)

1. [Adobe Sign-Unterzeichner zu adaptivem Formular hinzufügen](#addsignerstoanadaptiveform)
1. [Senden-Aktion für adaptives Formular wählen](#selectsubmitactionforanadaptiveform)

![signer-details](assets/signer-details.png)

### Adaptive Formulareigenschaften für Adobe Sign bearbeiten{#enableadobesign}

Konfigurieren Sie die Eigenschaften adaptiver Formulare für Adobe Sign für ein vorhandenes oder ein neues adaptives Formular.

[Erstellen eines adaptiven Formulars für Adobe ](/help/forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) Signature beschreibt die Schritte zum Erstellen eines grundlegenden adaptiven Formulars. Weitere Optionen zum Erstellen eines adaptiven Formulars finden Sie unter [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md).

#### Erstellen eines adaptiven Formulars für Adobe Sign {#create-an-adaptive-form-for-adobe-sign}

Führen Sie die folgenden Schritte aus, um ein adaptives Formular für Adobe Sign zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms und Dokumente]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Adaptives Formular]**. Eine Liste von Vorlagen wird angezeigt. Wählen Sie die Vorlage aus und tippen Sie auf **[!UICONTROL Weiter]**.
1. Auf der Registerkarte **[!UICONTROL Basic]**:

   1. Geben Sie für das adaptive Formular **Name** und **Titel** an.
   1. Wählen Sie den [Configuration Container](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) aus, der beim Konfigurieren von Adobe Sign mit AEM Forms erstellt wurde.

      >[!NOTE]
      >
      >Die Dropdown-Liste **[!UICONTROL Adobe Sign Cloud Service]** zeigt die Cloud-Services an, die im Container Konfiguration konfiguriert sind, den Sie in diesem Feld auswählen. Die Dropdown-Liste **[!UICONTROL Adobe Sign Cloud Service]** steht im Abschnitt **[!UICONTROL Elektronische Signatur]** der Eigenschaften des adaptiven Formulars zur Verfügung, wenn Sie die Option **[!UICONTROL Adobe Sign aktivieren]** auswählen.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Formularmodell]** eine der folgenden Optionen:

   * Wählen Sie die Option **[!UICONTROL Formularvorlage als Dokument der Datensatzvorlage]** zuordnen und wählen Sie ein Dokument der Datensatzvorlage aus. Wenn Sie ein auf einer Formularvorlage basierendes adaptives Formular verwenden, werden nur die Dokumente, die zum Unterschreiben gesendet werden, angezeigt, die auf der zugehörigen Formularvorlage basieren. Es werden nicht alle Felder des adaptiven Formulars angezeigt.
   * Wählen Sie die Option **[!UICONTROL Dokument aus Datensatz erzeugen]**. Wenn Sie ein adaptives Formular mit aktivierter Option &quot;Dokument aus Datensatz&quot;verwenden, zeigt das zum Unterschreiben gesendete Dokument alle Felder des adaptiven Formulars an.

1. Tippen Sie auf **[!UICONTROL Erstellen.]** Es wird ein adaptives Formular mit aktiviertem Zeichen erstellt, das zum Hinzufügen von Adobe Sign-Feldern verwendet werden kann.

#### Bearbeiten eines adaptiven Formulars für Adobe Sign {#editafsign}

Führen Sie die folgenden Schritte aus, um Adobe Sign in einem vorhandenen adaptiven Formular zu verwenden:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** **[!UICONTROL Forms und Dokumente]**.
1. Wählen Sie das adaptive Formular aus und tippen Sie auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Basic]** den [Configuration Container](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) aus, der beim Konfigurieren von Adobe Sign mit AEM Forms erstellt wurde.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Formularmodell]** eine der folgenden Optionen:

   * Wählen Sie die Option **[!UICONTROL Formularvorlage als Dokument der Datensatzvorlage]** zuordnen und wählen Sie ein Dokument der Datensatzvorlage aus. Wenn Sie ein auf einer Formularvorlage basierendes adaptives Formular verwenden, werden nur die Dokumente, die zum Unterschreiben gesendet werden, angezeigt, die auf der zugehörigen Formularvorlage basieren. Es werden nicht alle Felder des adaptiven Formulars angezeigt.
   * Wählen Sie die Option **[!UICONTROL Dokument aus Datensatz erzeugen]**. Wenn Sie ein adaptives Formular mit aktivierter Option &quot;Dokument aus Datensatz&quot;verwenden, zeigt das zum Unterschreiben gesendete Dokument alle Felder des adaptiven Formulars an.

1. Tippen Sie auf **[!UICONTROL Speichern und Schließen]**. Das adaptive Formular ist für Adobe Sign aktiviert.

### Adobe Sign-Felder zu adaptivem Formular hinzufügen {#addadobesignfieldstoanadaptiveform}

Adobe Sign verfügt über verschiedene Felder, die in einem adaptiven Formular platziert werden können. In diese Felder können verschiedene Datentypen wie Signaturen, Initialen, Firma oder Titel eingegeben. Sie helfen dabei, beim Unterschreiben zusätzliche Informationen zusammen mit den Signaturen zu erfassen. Sie können die Adobe Sign Block-Komponente verwenden, um Adobe Sign-Felder an verschiedenen Stellen in einem adaptiven Formular zu platzieren.

Gehen Sie wie folgt vor, um einem adaptiven Formular Felder hinzuzufügen und eine Reihe von Optionen für diese Felder anzupassen:

1. Ziehen Sie die Komponente **Adobe Sign Block** aus dem Komponentenbrowser in das adaptive Formular. Die Adobe Sign Block-Komponente enthält alle unterstützten Adobe Sign-Felder. Standardmäßig wird dem adaptiven Formular ein Feld **Unterschrift** hinzugefügt.

   ![sign-block](assets/sign-block.png)

   Standardmäßig ist der Adobe Sign Block im veröffentlichten adaptiven Formular nicht sichtbar. Er wird nur in den Signaturdokumenten angezeigt. Sie können die Sichtbarkeit von Adobe Sign Block in den Eigenschaften der Adobe Sign Block-Komponente ändern.

   >[!NOTE]
   >
   >* Für die Verwendung von Adobe Sign in einem adaptiven Formular ist Adobe Sign Block nicht zwingend erforderlich. Wenn Sie den Adobe Sign-Block nicht verwenden und keine Felder für die Unterzeichner hinzufügen, wird das Standardunterschriftsfeld unten in den unterschreibenden Dokumenten angezeigt.
   >* Verwenden Sie den Adobe Sign-Block nur für adaptive Formulare, die automatisch ein Datensatzdokument generieren. Wenn Sie das Datensatzdokument mithilfe einer benutzerdefinierten XDP-Datei generieren oder ein formularvorlagenbasiertes adaptives Formular verwenden, wird Adobe Sign nicht benötigt.


1. Wählen Sie die Komponente **Adobe Sign Block** und tippen Sie auf das Symbol **Bearbeiten** ![aem_6_3_edit](assets/aem_6_3_edit.png). Es werden Optionen zum Hinzufügen von Feldern und zum Formatieren der Darstellung von Feldern angezeigt.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A. Adobe Sign-Felder** auswählen und hinzufügen. **B.** Erweitern des Adobe Sign-Blocks auf Ansicht im Vollbildmodus

1. Tippen Sie auf das Symbol **Adobe Sign Field** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png). Optionen zum Auswählen und Hinzufügen von Adobe Sign-Feldern werden angezeigt.

   Erweitern Sie das Dropdown-Feld **Typ**, um ein Adobe Sign-Feld auszuwählen, und tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um das ausgewählte Feld zum Adobe Sign-Block hinzuzufügen. Die Dropdown-Liste **Typ** enthält die Feldtypen Signatur, Signiererinformationen und Daten. Die Integration von Adobe Sign in AEM Forms unterstützt nur die in der Dropdown-Liste „Typ“ angegebenen Felder. Ausführliche Informationen zu Adobe Sign-Feldern finden Sie in der [Adobe Sign-Dokumentation](https://helpx.adobe.com/sign/help/field-types.html).

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   Es ist obligatorisch, einen eindeutigen Namen für ein Feld anzugeben. Sie können auch die Option „Erforderlich“ aktivieren, um ein Feld als Pflichtfeld zu markieren. Für manche Adobe Sign-Felder stehen außer den Optionen **Name** und **Erforderlich** weitere Optionen verfügbar. Dies kann z. B. Maske oder mehrzeilig sein. Geben Sie außerdem eindeutige Namen für die einzelnen Adobe Sign-Felder an, unabhängig davon, ob diese Felder sich im selben oder in verschiedenen Adobe Sign-Blöcken befinden.

### Adobe Sign für adaptives Formular aktivieren {#enableadobsignforanadaptiveform}

Adobe Sign ist standardmäßig nicht für adaptive Formulare aktiviert. Gehen Sie wie folgt vor, um es zu aktivieren:

1. Tippen Sie im Inhaltsbrowser auf **Form Container** und dann auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an.
1. Erweitern Sie im Eigenschaftenbrowser das Akkordeon **Elektronische Signatur** und wählen Sie die Option **Adobe Sign aktivieren**. Dadurch wird Adobe Sign für ein adaptives Formular aktiviert.

### Cloud-Service von Adobe Sign und Signaturreihenfolge wählen  {#selectadobesigncloudserviceforanadaptiveform}

Sie können mehrere Adobe Sign-Dienste für eine Instanz von AEM Forms konfigurieren. Es empfiehlt sich, für jede Funktion (Personalwesen, Finanzen usw.) eine eigene Gruppe von Diensten zu verwenden. Dies erleichtert die Verfolgung und Berichterstellung für signierte Dokumente. So könnte beispielsweise eine Bank mehrere Abteilungen umfassen. In diesem Fall können Sie für jede Abteilung eine eigene Konfiguration einrichten, damit die Dokumente leichter zu verfolgen sind.

Ein Dokument kann auch mehrere Unterzeichner haben. Beispielsweise können bei einem Kreditkartenantrag mehrere Antragsteller vorhanden sein. Die Bank benötigt die Unterschriften aller Antragsteller, bevor sie mit der Bearbeitung beginnt. Bei Szenarien mit mehreren Unterzeichnern können Sie wählen, ob diese das Dokument nacheinander oder simultan unterschreiben sollen.

Führen Sie die folgenden Schritte aus, um einen Cloud-Service und die Reihenfolge für die Unterzeichnung zu wählen:

![cloud-service](assets/cloud-service.png)

1. Tippen Sie im Inhaltsbrowser auf **Form Container** und dann auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an.
1. Erweitern Sie im Eigenschaftenbrowser das Akkordeon **Elektronische Signatur** und wählen Sie die Option **Adobe Sign aktivieren**. Dadurch wird Adobe Sign für ein adaptives Formular aktiviert.
1. Wählen Sie einen Cloud-Dienst aus der bereits konfigurierten Liste der Adobe Sign Cloud-Services aus.

   Wenn die Liste der **Cloud-Services von Adobe Sign** leer ist, befolgen Sie die Anweisungen zum [Konfigurieren von Adobe Sign mit AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md), um den Dienst zu konfigurieren.

   Die Dropdown-Liste Liste die Cloud-Dienste, die im Ordner `global` unter Tools > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** vorhanden sind. Darüber hinaus werden in der Dropdown-Liste auch die Cloud-Dienste Liste, die in dem Ordner vorhanden sind, den Sie beim Erstellen eines adaptiven Formulars im Feld **[!UICONTROL Configuration Container]** auswählen.

1. Wählen Sie die Signaturreihenfolge im Dialogfeld **Benutzer können signieren**. Adobe Sign-Unterzeichner können ein adaptives Formular **sequenziell**, d. h. nacheinander, oder **simultan** in beliebiger Reihenfolge unterschreiben.

   Bei sequenzieller Reihenfolge erhält jeder Unterzeichner das Formular einzeln. Nachdem ein Unterzeichner das Dokument signiert hat, wird das Formular an den nächsten Unterzeichner gesendet und so weiter.

   Bei simultaner Reihenfolge können mehrere Unterzeichner ein Formular gleichzeitig signieren.

1. [hinzufügen Sie Unterzeichner zu einem adaptiven ](#addsignerstoanadaptiveform) Formular und tippen Sie auf das Symbol Fertig, um die Änderungen zu speichern.

### Unterzeichner zu adaptivem Formular hinzufügen {#addsignerstoanadaptiveform}

Sie können für ein adaptives Formular nur einen oder mehrere Unterzeichner festlegen. Wenn Sie einen Unterzeichner hinzufügen, können Sie außerdem Authentifizierungsdetails für den Unterzeichner konfigurieren. Sie können auch wählen, ob die Person, die das Formular ausfüllt, zugleich der Unterzeichner sein muss. Führen Sie die folgenden Schritte durch, um einen Unterzeichner hinzuzufügen und seine Details anzugeben:

1. Tippen Sie im Inhaltsbrowser auf **Form Container** und dann auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an.
1. Erweitern Sie im Eigenschaftenbrowser das Akkordeon **Elektronische Signatur** und wählen Sie die Option **Adobe Sign aktivieren**. Dadurch wird Adobe Sign für ein adaptives Formular aktiviert.
1. Tippen Sie auf **Unterscheibende Person hinzufügen** unter **Signiererkonfiguration.** Es wird ein Unterzeichner zum adaptiven Formular hinzugefügt. Sie können dem adaptiven Formular mehreren Adobe Sign-Unterzeichner hinzufügen.
1. ![phone-details](assets/phone-details.png)

   Klicken Sie auf das Symbol **Bearbeiten** ![aem_6_3_edit](assets/aem_6_3_edit.png), um die folgenden Informationen zum Unterzeichner anzugeben:

   * **Titel:** Geben Sie einen Titel an, um einen Unterzeichner eindeutig zu identifizieren.
   * **Sind der Unterzeichner und die Person, die das Formular ausfüllt, identisch?:** Wählen Sie  **Ja**, wenn Formularbenutzer und erster Unterzeichner dieselbe Person sind. Wenn für die Option **Nein** eingestellt ist, können Sie die Komponente für den Signaturschritt nicht im adaptiven Formular verwenden. Wenn die Komponente für „Unterschriftsschritt“ im Formular enthalten ist, wird automatisch „Ja“ für das Feld festgelegt.
   * **E-Mail-Adresse der unterzeichnenden Person:** Geben Sie die E-Mail-Adresse des Unterzeichners an. Der Unterzeichner erhält die zu unterschreibenden Dokumente/das Formular unter der angegebenen E-Mail-Adresse. Sie können eine E-Mail-Adresse verwenden, die in einem Formularfeld im AEM-Benutzerprofil des angemeldeten Benutzers angegeben ist, oder manuell eine E-Mail-Adresse eingeben. Dieser Schritt ist obligatorisch. Wenn Sie nur einen Unterzeichner konfiguriert haben, stellen Sie außerdem sicher, dass dessen E-Mail-Adresse nicht mit dem Adobe Sign-Konto identisch ist, das zum Konfigurieren von AEM-Cloud-Services verwendet wird.
   * **Authentifizierungsmethode für unterzeichnende Person:** Geben Sie die Methode zum Authentifizieren eines Benutzers an, bevor Sie ein Formular zum Signieren öffnen. Sie können die Authentifizierung per Telefon, Wissensdatenbank und Profil in sozialem Netzwerk wählen.

   >[!NOTE]
   >
   >* Bei der Authentifizierung über soziale Netzwerke steht standardmäßig eine Option zum Authentifizieren über Facebook, Google und LinkedIn zur Verfügung. Wenden Sie sich an den Adobe Sign-Support, wenn Sie weitere Anbieter von Authentifizierung über soziale Netzwerke aktivieren möchten.


   * **Auszufüllende oder zu unterzeichnende Adobe Sign Felder:** Wählen Sie die Adobe Sign-Felder für den Unterzeichner. Ein adaptives Formular kann mehrere Adobe Sign-Felder umfassen. Sie können bestimmte Felder für einen bestimmten Unterzeichner aktivieren. Das Feld zeigt alle verfügbaren Adobe Sign-Blöcke an. Wenn Sie einen Block auswählen, werden alle Felder des Blocks ausgewählt. Über das X-Symbol können Sie die Auswahl eines Feldes aufheben.

   ![signer-details-1](assets/signer-details-1.png)

   Die Abbildung oben zeigt zwei Adobe Sign-Blöcke als Beispiel: Personal-Information und Office-details

   Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). Der Unterzeichner wird hinzugefügt und konfiguriert.

### Senden-Aktion für adaptives Formular wählen {#selectsubmitactionforanadaptiveform}

Nachdem Sie dem adaptiven Formular Adobe Sign-Felder hinzugefügt, Adobe Sign über den Formular-Container aktiviert, den Cloud-Service von Adobe Sign gewählt und Adobe Sign-Unterzeichner hinzugefügt haben, wählen Sie die geeignete Übermittlungsaktion für das adaptive Formular. Ausführliche Informationen zu Übermittlungsaktionen für adaptive Formulare finden Sie unter [Konfigurieren der Übermittlungsaktion](/help/forms/using/configuring-submit-actions.md).

Ein für Adobe Sign aktiviertes adaptives Formular wird darüber hinaus erst übermittelt, nachdem alle Unterzeichner es signiert haben. Teilweise signierte Formulare finden Sie im Abschnitt „Ausstehende Signatur“ im Forms-Portal. Der Adobe Sign Configuration Service fragt den Adobe Sign-Server in [regelmäßige Abständen](/help/forms/using/adobe-sign-integration-adaptive-forms.md) ab, um den Status der Signaturen zu überprüfen. Wenn alle Unterzeichner das Formular signiert haben, wird der Dienst für die Übermittlungsaktion gestartet und das Formular übermittelt. Wenn Sie eine benutzerdefinierte Übermittlungsaktion verwenden und Adobe Sign im Formular verwendet wird, aktualisieren Sie Ihre benutzerdefinierte Übermittlungsaktion, sodass der Dienst für die Übermittlungsaktion verwendet wird.

>[!NOTE]
>
>Die Daten des adaptiven Formulars werden vorübergehend im Forms-Portal gespeichert. Es wird empfohlen, [benutzerdefinierte Datenspeicherung für Forms Portal](/help/forms/using/configuring-draft-submission-storage.md) zu verwenden. Dadurch wird sichergestellt, dass keine persönlichen Daten (PII) auf AEM-Servern gespeichert werden.

Damit ist der Ablauf zur Formularunterzeichnung vollständig. Sie können das Formular in der Vorschau anzeigen, um die Signaturerfahrung zu überprüfen. Im veröffentlichten Formular werden die Felder des Adobe Sign-Blocks angezeigt, wenn ein Unterzeichner das Formular per E-Mail zum Unterschreiben erhält. Diese Erfahrung wird auch als Signieren außerhalb des Formulars bezeichnet. Sie können auch einen Ablauf zum Signieren innerhalb des Formulars für den ersten Unterzeichner konfigurieren. Eine detaillierte Anleitung finden Sie unter [Formularinternen Signaturvorgang erstellen](/help/forms/using/working-with-adobe-sign.md#create-in-form-signing-experience).

## Konfigurieren von Cloud-Signaturen für ein adaptives Formular {#configure-cloud-signatures-for-an-adaptive-form}

Cloud-basierte digitale Signaturen oder Remote-Signaturen sind eine neue Generation digitaler Signaturen, die über Desktop, Mobilgeräte und das Web funktioniert — und die höchste Kompatibilitätsstufe und die höchste Sicherheit für die Signiererauthentifizierung erfüllen. Sie können ein adaptives Formular mit Cloud-basierten digitalen Signaturen signieren.

Nachdem Sie die Eigenschaften des adaptiven Formulars für das Zeichen der Adobe [ bearbeitet haben, führen Sie die folgenden Schritte aus, um einem adaptiven Formular ein Cloud-Signaturfeld hinzuzufügen:](#enableadobesign)

1. Ziehen Sie die Komponente **Adobe Sign Block** aus dem Komponentenbrowser in das adaptive Formular. Die Adobe Sign Block-Komponente enthält alle unterstützten Adobe Sign-Felder. Standardmäßig wird dem adaptiven Formular ein Feld **Unterschrift** hinzugefügt.

   ![sign-block](assets/sign-block.png)

1. Wählen Sie die Komponente **Adobe Sign Block** und tippen Sie auf das Symbol **Bearbeiten** ![aem_6_3_edit](assets/aem_6_3_edit.png). Es werden Optionen zum Hinzufügen von Feldern und zum Formatieren der Darstellung von Feldern angezeigt.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A. Adobe Sign-Felder** auswählen und hinzufügen. **B.** Erweitern des Adobe Sign-Blocks auf Ansicht im Vollbildmodus

1. Tippen Sie auf das Symbol **Adobe Sign Field** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png). Optionen zum Auswählen und Hinzufügen von Adobe Sign-Feldern werden angezeigt.

   Erweitern Sie das Dropdown-Feld **Typ**, um **Digitale Signatur** auszuwählen, und tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um das ausgewählte Feld zum Adobe Sign-Block hinzuzufügen.

   ![digital_signatures](assets/digital_signatures.png)

   Es ist obligatorisch, einen eindeutigen Namen für ein Feld anzugeben.

   Anwenden digitaler Signaturen auf das adaptive Formular mit:

   * Cloud-Signaturen: Signieren Sie mit einer [digitalen ID](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html), die von einem Trust-Dienstleister gehostet wird.
   * Adobe Acrobat oder Reader: Laden Sie das Dokument mit Adobe Acrobat oder Reader herunter und öffnen Sie es, um sich mit einer Chipkarte, einem USB-Token oder einer dateibasierten digitalen ID zu signieren.

   Nachdem Sie das Cloud-Signaturfeld zum adaptiven Formular hinzugefügt haben, führen Sie die folgenden Schritte aus, um den Konfigurationsprozess abzuschließen:

   * [Adobe Sign für adaptives Formular aktivieren](#enableadobsignforanadaptiveform)
   * [Cloud-Service von Adobe Sign für adaptives Formular wählen](#selectadobesigncloudserviceforanadaptiveform)
   * [Adobe Sign-Unterzeichner zu adaptivem Formular hinzufügen](#addsignerstoanadaptiveform)
   * [Senden-Aktion für adaptives Formular wählen](#selectsubmitactionforanadaptiveform)


## Formularinternen Signaturvorgang erstellen {#create-in-form-signing-experience}

Ein Benutzer kann ein adaptives Formular beim Ausfüllen auch signieren. Diese Erfahrung wird auch formularinternes Signieren bezeichnet. Dieser Ablauf steht nur für den ersten Unterzeichner in einer Umgebung mit mehreren Unterzeichnern zur Verfügung. Gehen Sie Führen Sie die folgenden Schritte aus, um einen Ablauf für formularinternes Signieren für ein adaptives Formular zu erstellen:

1. [Fügen Sie die Komponente für Signaturschritt hinzu und konfigurieren Sie sie](#add-and-configure-the-signature-step-component).
1. [Fügen Sie die Komponente für Übersichtsschritt hinzu](#configure-the-thank-you-page-or-summary-step-component).

![in-form-signing-experience](assets/in-form-signing-experience.png)

### Komponente für Signaturschritt hinzufügen und konfigurieren {#add-and-configure-the-signature-step-component}

Mit der Komponente für Signaturschritt können Sie einen Bereich für die elektronische Unterschrift unter dem ausgefüllten Formular bereitstellen. Bei der Ausgabe des Abschnitts mit der Komponente für Signaturschritt wird eine signierbare PDF-Version des ausgefüllten Formulars angezeigt. Die Signaturschritt-Komponente nimmt die volle für das Formular verfügbare Breite ein. Wir empfehlen, keine anderen Komponenten in dem Abschnitt zu platzieren, der die Signaturschritt-Komponente enthält.

Führen Sie die folgenden Schritte aus, um die Signaturschritt-Komponente zu konfigurieren:

1. Ziehen Sie die Komponente **Unterschriftsschritt** aus dem Komponentenbrowser in das Formular.
1. Wählen Sie die neu hinzugefügte Unterschriftsschritt-Komponente aus und tippen Sie auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Signaturschritts an. Konfigurieren Sie die folgenden Eigenschaften:

   * **Elementname**: Geben Sie den Namen der Komponente an.
   * **Titel:** Geben Sie den eindeutigen Titel der Komponente an.
   * **Vorlagennachricht:** Geben Sie die Nachricht an, die angezeigt werden soll, während die Signatur-PDF geladen wird. Die Adobe Sign-Dienste benötigen einige Zeit, um Signatur-PDF vorzubereiten und zu laden.
   * **Signaturdienst:** Wählen Sie die Option **Adobe Sign** aus.
   * **Frühere E-Sign-Komponente verwenden:** Wenn Sie das entsprechende adaptive Formular in [AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md) oder die AEM Forms-App verwenden oder das zugrunde liegende adaptive Formular eine ältere E-Sign-Komponente enthält, wählen Sie die Option **Legacy-E-Sign-Komponente verwenden**.
   * **Konfiguration**: Wählen Sie eine Konfiguration (Adobe Sign Cloud Service). Diese Dropdown-Liste ist nur verfügbar, wenn die Option **Frühere E-Sign Komponente verwenden** aktiviert ist.

   Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Änderungen zu speichern.

   ![signature-step](assets/signature-step.png)

   >[!NOTE]
   >
   >* Wenn Sie die Komponente **[!UICONTROL Unterschriftsschritt]** in das Formular ziehen und dort ablegen, wird für die Option **[!UICONTROL Wird das Formular von derselben Person ausgefüllt und unterzeichnet?]** automatisch **Ja** festgelegt. Dies ist für die Funktionsfähigkeit des Formulars erforderlich.
   >* In adaptiven Formularen mit Adobe Sign wird die Verwendung der Schaltfläche „Senden“ in dem Abschnitt oder Bedienfeld, in dem die Komponente für Signaturschritt verwendet wird, nicht unterstützt. Sie können einen Übersichtsschritt nach dem Unterschriftsschritt für die manuelle Übermittlung hinzufügen oder eine automatische Übermittlung nach dem Intervallsatz mit dem [Adobe Sign Configuration Service](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status) auslösen.


### Komponente für Danksagungsseite oder Zusammenfassungsschritt konfigurieren {#configure-the-thank-you-page-or-summary-step-component}

Die Komponente **Zusammenfassungsschritt** übermittelt automatisch das Formular, füllt die Informationen auf der angepassten Zusammenfassungsseite aus und zeigt die Zusammenfassung des übermittelten Formulars an. Sie ruft darüber hinaus die erforderlichen Informationen in der Rückgabezuordnung ab. Die Komponente Zusammenfassungsschritt nimmt die volle Breite des Formulars ein. Es wird empfohlen, keine andere Komponente im Abschnitt mit der Komponente Zusammenfassungsschritt zu verwenden.

Damit ist der Ablauf zur formularinternen Unterzeichnung vollständig. Sie können das Formular in der Vorschau anzeigen, um die Signaturerfahrung zu überprüfen.

## Häufig gestellte Fragen {#frequently-asked-questions}

**F: Es ist möglich, ein adaptives Formular in ein anderes adaptives Formular einzubetten. Kann das eingebettete adaptive Formular für Adobe Sign aktiviert werden?**

**Ans:** Nein, AEM Forms unterstützt nicht die Verwendung eines adaptiven Formulars, das ein für Adobe Sign aktiviertes adaptives Formular zum Signieren einbettet.

**Q: Wenn ich ein adaptives Formular mit der erweiterten Vorlage erstellen und es zur Bearbeitung öffnen möchte, wird die Fehlermeldung &quot;Elektronische Signaturen oder Unterzeichner sind nicht korrekt konfiguriert&quot; angezeigt. angezeigt. Wie behebe ich den Fehler?**

**A:** Adaptive Formulare, die die erweiterte Vorlage nutzen, sind für die Verwendung von Adobe Sign konfiguriert. Um den Fehler zu beheben, erstellen  Sie eine Adobe Sign Cloud-Konfiguration, wählen Sie sie aus und konfigurieren Sie einen Adobe Sign-Unterzeichner für das adaptive Formular.

**F: Kann ich Adobe Sign-Text-Tags in einer statischen Textkomponente eines adaptiven Formulars verwenden?**

**A:** Ja, Sie können Text-Tags in einer Textkomponente verwenden, um Adobe Sign-Felder einem adaptiven Formular mit [Datensatzdokument](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) hinzuzufügen (nur Option für automatisch generiertes Datensatzdokument). Informationen zu den Verfahren und Regeln zum Erstellen eines Text-Tags finden Sie in der [Adobe Sign-Dokumentation](https://helpx.adobe.com/sign/help/text-tags.html). Beachten Sie außerdem, dass adaptive Formulare Text-Tags nur begrenzt unterstützen. Sie können die Text-Tags verwenden, um nur die von Adobe Sign Block unterstützten Felder zu erstellen.

**F: AEM Forms stellt sowohl den Adobe Sign Block als auch die Unterschriftsschritt-Komponenten zur Verfügung. Können beide zusammen in einem adaptiven Formular verwendet werden?**

**Antwort:** Sie können beide Komponenten gleichzeitig in einem Formular verwenden. Beachten Sie die folgenden Empfehlungen für die Verwendung dieser Komponenten:

**Adobe Sign-Block:** Sie können den Adobe Sign-Block verwenden, um Adobe Sign-Felder an einer beliebigen Stelle im adaptiven Formular hinzuzufügen. Dies ermöglicht es auch, den Unterzeichnern bestimmte Felder zuzuweisen. Bei der Vorschau oder Veröffentlichung eines adaptiven Formulars ist Adobe Sign Block standardmäßig nicht sichtbar. Diese Blöcke werden nur in den Signaturdokumenten angezeigt. Im Signaturdokument sind nur die einem Unterzeichner zugewiesenen Felder aktiviert. Der Adobe Sign-Block für den ersten und die folgenden Unterzeichner verwendet werden.

**Signaturschrittkomponente:** Sie können die Signaturschrittkomponente verwenden, um eine formularinterne Signaturfunktion zu erstellen. Damit kann nur der erste Unterzeichner unterschreiben, während das Formular ausgefüllt wird. Bei der Ausgabe des Abschnitts mit der Signaturschritt-Komponente wird eine signierbare PDF-Version des Formulars angezeigt. In der Regel ist dies der letzte oder der vorletzte Abschnitt, auf den die Übersichtskomponente eines Formulars folgt.

