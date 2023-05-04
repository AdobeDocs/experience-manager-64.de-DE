---
title: Verwenden von CAPTCHA in adaptiven Formularen
seo-title: Using CAPTCHA in adaptive forms
description: Erfahren Sie, wie Sie AEM CAPTCHA- oder Google reCAPTCHA-Dienst in adaptiven Formularen konfigurieren.
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in adaptive forms.
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
feature: Adaptive Forms
exl-id: 1129004b-5e8b-42fd-98ed-f203edde93b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 58%

---

# Verwenden von CAPTCHA in adaptiven Formularen {#using-captcha-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine Herausforderung dar und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms unterstützt CAPTCHA in adaptiven Formularen. Sie können den reCAPTCHA-Dienst von Google verwenden, um CAPTCHA zu implementieren.

>[!NOTE]
>
>AEM Forms unterstützt nur reCaptcha v2. Es werden keine anderen Versionen unterstützt.
>
>CAPTCHA in adaptiven Formularen wird im Offline-Modus in der AEM Forms-App nicht unterstützt.

## Konfigurieren des reCAPTCHA-Service von Google {#google-recaptcha}

Formularautoren können den reCAPTCHA-Dienst von Google verwenden, um CAPTCHA in adaptive Formulare zu implementieren. Es bietet erweiterte CAPTCHA-Funktionen zum Schutz Ihrer Site. Weitere Informationen zur Funktionsweise von reCAPTCHA finden Sie unter [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![recaptcha](assets/recaptcha.png)

Implementieren des reCAPTCHA-Diensts in AEM Forms:

1. Erhalten [reCAPTCHA API-Schlüsselpaar](https://www.google.com/recaptcha/admin) aus Google. Er enthält einen Site- und einen Geheimschlüssel.
1. Erstellen Sie einen Konfigurations-Container für Cloud Services.

   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
      * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurations-Browser.](/help/sites-administering/configurations.md)
   1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloudkonfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud Service-Konfigurationen zu erstellen und zu konfigurieren.

      1. Wählen Sie im Konfigurationsbrowser den Ordner **[!UICONTROL global]** und tippen Sie auf **[!UICONTROL Eigenschaften]**.
      1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloudkonfigurationen]**.
      1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.
   1. Tippen Sie im Konfigurationsbrowser auf **[!UICONTROL Erstellen]**.
   1. Legen Sie im Dialogfeld „Konfiguration erstellen“ einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloudkonfigurationen]**.
   1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den für Cloud Service-Konfigurationen aktivierten Ordner zu erstellen.


1. Konfigurieren Sie den Cloud Service für reCAPTCHA.

   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools](assets/tools.png) >  **Cloud Services**.
   1. Tippen **[!UICONTROL reCAPTCHA]**. Die Seite Konfigurationen wird geöffnet. Wählen Sie den im vorherigen Schritt erstellten Konfigurations-Container und tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Geben Sie Namen, Site- und Geheimschlüssel für den reCAPTCHA-Service an und tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud Service-Konfiguration zu erstellen.
   1. Geben Sie im Dialogfeld „Komponente bearbeiten“ die Site- und Geheimschlüssel an, die Sie in Schritt 1 erhalten haben. Tippen Sie auf **[!UICONTROL Einstellungen speichern]** und anschließend auf **[!UICONTROL OK]**, um die Konfiguration abzuschließen.

   Sobald der reCAPTCHA-Dienst konfiguriert ist, ist er zur Verwendung in adaptiven Formularen verfügbar. Weitere Informationen finden Sie unter [Verwenden von CAPTCHA in adaptiven Formularen](#using-captcha).

## Verwenden von CAPTCHA in adaptiven Formularen {#using-captcha}

So verwenden Sie CAPTCHA in adaptiven Formularen:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der beim Erstellen des adaptiven Formulars ausgewählte Konfigurationscontainer den reCAPTCHA-Cloud-Service enthält. Sie können auch die Eigenschaften des adaptiven Formulars bearbeiten, um den mit dem Formular verknüpften Konfigurationscontainer zu ändern.

1. Ziehen Sie aus dem Komponenten-Browser die **[!UICONTROL Captcha]** auf das adaptive Formular.

   >[!NOTE]
   >
   >Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird außerdem nicht empfohlen, CAPTCHA in einem Bereich zu verwenden, der für verzögertes Laden markiert ist, oder in einem Fragment.

   >[!NOTE]
   >
   >Captcha ist zeitkritisch und läuft in etwa einer Minute ab. Daher wird empfohlen, die Captcha-Komponente direkt vor der Senden-Schaltfläche im adaptiven Formular zu platzieren.

1. Wählen Sie die CAPTCHA-Komponente aus, die Sie hinzugefügt haben, und tippen Sie auf ![cmppr](assets/cmppr.png), um ihre Eigenschaften zu bearbeiten.
1. Geben Sie einen Titel für das CAPTCHA-Widget an. Der Standardwert ist **CAPTCHA**. Wählen Sie **[!UICONTROL Titel ausblenden]**, wenn der Titel nicht angezeigt werden soll.
1. Wählen Sie aus der Dropdown-Liste des **[!UICONTROL CAPTCHA-Service]** die Option **[!UICONTROL reCAPTCHA]** aus, um den reCAPTCHA-Service zu aktivieren, wenn Sie ihn wie in [reCAPTCHA-Service von Google](#google-recaptcha) beschrieben konfiguriert haben. Wählen Sie eine Konfiguration aus der Dropdown-Liste „Einstellungen“. Wählen Sie außerdem als Größe für das reCAPTCHA-Widget **[!UICONTROL Normal]** oder **[!UICONTROL Kompakt]** aus.

   >[!NOTE]
   >
   >Wählen Sie nicht **[!UICONTROL Standard]** aus der Dropdown-Liste „CAPTCHA-Service“ aus, da der standardmäßige AEM-CAPTCHA-Service nicht mehr unterstützt wird.

1. Speichern Sie die Eigenschaften.

Der reCAPTCHA-Dienst wird im adaptiven Formular aktiviert. Sie können das Formular in der Vorschau anzeigen und die CAPTCHA-Funktionsweise sehen.
