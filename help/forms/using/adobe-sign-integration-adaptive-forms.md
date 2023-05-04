---
title: Integrieren von Acrobat Sign mit AEM Forms
seo-title: Integrate Acrobat Sign with AEM Forms
description: Erfahren Sie, wie Sie Acrobat Sign für AEM Forms konfigurieren.
seo-description: Learn how to configure Acrobat Sign for AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Acrobat Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 39%

---

# Integrieren von Acrobat Sign mit AEM Forms {#integrate-adobe-sign-with-aem-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Acrobat Sign ermöglicht Workflows für die elektronische Signatur für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit Acrobat Sign und adaptiven Formularen füllt ein Benutzer ein adaptives Formular in **Dienstanmeldung**. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstleister gesendet. Der Dienstanbieter überprüft die Anwendung und verwendet Acrobat Sign, um die Anwendung zu kennzeichnen. Um ähnliche Workflows für elektronische Signaturen zu aktivieren, können Sie Acrobat Sign in AEM Forms integrieren.

Um Acrobat Sign mit AEM Forms zu verwenden, konfigurieren Sie Acrobat Sign in AEM Cloud Services:

## Voraussetzungen {#prerequisites}

Sie benötigen Folgendes, um Acrobat Sign in AEM Forms zu integrieren:

* Ein aktiver [Acrobat Sign-Entwicklerkonto.](https://acrobat.adobe.com/de/de/why-adobe/developer-form.html)
* Ein [SSL aktiviert](/help/sites-administering/ssl-by-default.md) AEM Forms-Server.
* Ein [Acrobat Sign API-Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Anmeldeinformationen (Client-ID und Client Secret) der Acrobat Sign-API-Anwendung.
* Entfernen Sie bei der Neukonfiguration die vorhandene Acrobat Sign-Konfiguration aus der Autoren- und der Veröffentlichungsinstanz.
* Verwenden Sie [identische Schlüssel](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) für Autoren- und Veröffentlichungsinstanzen.

## Konfigurieren von Acrobat Sign mit AEM Forms {#configure-adobe-sign-with-aem-forms}

Nachdem die Voraussetzungen erfüllt sind, führen Sie die folgenden Schritte aus, um Acrobat Sign mit AEM Forms in der -Autoreninstanz zu konfigurieren:

1. Navigieren Sie auf der AEM Forms-Autoreninstanz zu **Tools** ![hammer](assets/hammer.png) > **Allgemein** > **Konfigurations-Browser**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurations-Browser.](/help/sites-administering/configurations.md)
1. Tippen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurationscontainer für Cloud-Dienste erstellt.
1. Navigieren Sie zu **Instrumente** ![Hammer](assets/hammer.png) > **Cloud Services** > **Acrobat Sign** und wählen Sie den Konfigurationscontainer aus, den Sie im obigen Schritt erstellt haben.

   >[!NOTE]
   >
   >Sie können entweder die Schritte 1 bis 4 ausführen, um einen neuen Konfigurationscontainer zu erstellen und eine Acrobat Sign-Konfiguration im Container zu erstellen, oder die vorhandene `global` Ordner in **Instrumente** ![Hammer](assets/hammer.png) > **Cloud Services** > **Acrobat Sign**. Wenn Sie die Konfiguration im neuen Konfigurations-Container erstellen, dürfen Sie beim Erstellen eines adaptiven Formulars nicht vergessen, den Container-Namen im Feld **[!UICONTROL Konfigurations-Container]** anzugeben.

   >[!NOTE]
   Vergewissern Sie sich, dass die URL der Cloud-Dienste-Konfigurationsseite mit **HTTPS** beginnt. Wenn nicht, [SSL aktivieren](/help/sites-administering/ssl-by-default.md) für den AEM Forms-Server.

1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]** , um die Acrobat Sign-Konfiguration in AEM Forms zu erstellen.
1. Im **[!UICONTROL Allgemein]** des **[!UICONTROL Acrobat Sign-Konfiguration erstellen]** Seite, geben Sie eine **Name** für die Konfiguration und tippen Sie auf **Nächste**. Sie können optional einen Titel angeben und durchsuchen, um ein Miniaturbild für die Konfiguration auszuwählen.

1. Kopieren Sie die URL im aktuellen Browser-Fenster in einen Texteditor. Es ist erforderlich, die Acrobat Sign-Anwendung mit AEM Forms zu konfigurieren.

1. Konfigurieren Sie OAuth-Einstellungen für die Acrobat Sign-Anwendung:

   1. Öffnen Sie ein Browserfenster und melden Sie sich beim Acrobat Sign-Entwicklerkonto an.
   1. Wählen Sie die für AEM Forms konfigurierte Anwendung aus und tippen Sie auf OAuth für Anwendung konfigurieren.
   1. Im **Umleitungs-URL** Fügen Sie die im vorherigen Schritt kopierte HTTPS-URL hinzu und klicken Sie auf **Speichern**.
   1. Aktivieren Sie die folgenden OAuth-Einstellungen für die Acrobat Sign-Anwendung und klicken Sie auf **Speichern**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Schrittweise Informationen zum Konfigurieren von OAuth-Einstellungen für eine Acrobat Sign-Anwendung und zum Abrufen der Schlüssel finden Sie unter [oAuth-Einstellungen für die Anwendung konfigurieren](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) Entwicklerdokumentation.

   ![OAuth Config](assets/oauthconfig_new.png)

1. Gehen Sie zurück zu **Acrobat Sign-Konfiguration erstellen** Seite. Auf der Registerkarte **[!UICONTROL Einstellungen]** wird im Feld **[!UICONTROL OAuth URL]** die folgende Standard-URL angegeben:

   `https://secure.na1.echosign.com/public/oauth`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard.

   Sie können den Wert für die Datenbank-Shard ändern. Starten Sie den Server neu, um den neuen Wert für die Datenbank-Shard verwenden zu können.

1. Geben Sie die **Client-ID** (auch als Anwendungs-ID bezeichnet) und das **Client-Geheimnis** an. Wählen Sie die **Acrobat Sign auch für Anlagen aktivieren** Option zum Anhängen von Dateien an ein adaptives Formular an das entsprechende Acrobat Sign-Dokument, das zum Signieren gesendet wird.

   Tippen **[!UICONTROL Verbindung zu Acrobat Sign herstellen]**. Wenn Sie zur Eingabe der Anmeldeinformationen aufgefordert werden, geben Sie den Benutzernamen und das Kennwort des beim Erstellen der Acrobat Sign-Anwendung verwendeten Kontos an.

   Tippen **[!UICONTROL Erstellen]** , um die Acrobat Sign-Konfiguration zu erstellen.

1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://'[server]:[port]'/system/console/configMgr`.
1. Öffnen Sie **Forms Common-Konfigurations-Service.**
1. Wählen Sie im Feld **Zulassen** **Alle Benutzer** – alle Benutzer, anonym oder angemeldet, können Anhänge in der Vorschau ansehen, Formulare überprüfen und unterzeichnen – und klicken Sie auf **Speichern.** Die Autoreninstanz ist für die Verwendung von Acrobat Sign konfiguriert.
1. Verwenden Sie [Replikation](/help/sites-deploying/replication.md), um eine identische Konfiguration für die entsprechenden Veröffentlichungsinstanzen zu erstellen.

Jetzt ist Acrobat Sign in AEM Forms integriert und kann in adaptiven Formularen verwendet werden. nach [Verwenden des Acrobat Sign-Dienstes in einem adaptiven Formular](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), geben Sie den oben erstellten Konfigurationscontainer in den Eigenschaften des adaptiven Formulars an.

## Konfigurieren von Acrobat Sign Scheduler zum Synchronisieren des Signaturstatus {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Ein für Acrobat Sign aktiviertes adaptives Formular wird erst gesendet, nachdem alle Unterzeichner den Unterzeichnungsvorgang abgeschlossen haben. Standardmäßig ist geplant, dass die Acrobat Sign-Planungsdienste die Signiererantwort alle 24 Stunden überprüfen (abfragen). Sie können das Standardintervall für Ihre Umgebung ändern. Führen Sie zum Anpassen des Standardintervalls folgende Schritte durch:

1. Melden Sie sich mit Administratorberechtigungen beim AEM Forms-Server an und navigieren Sie zu **Instrumente** > **Aktivitäten** > **Web-Konsole**.

   Sie können auch folgende URL in einem Browser-Fenster öffnen:
   `https://[localhost]:'port'/system/console/configMgr`

1. Suchen und öffnen Sie die **Acrobat Sign Configuration Service** -Option. Geben Sie einen [Cron-Ausdruck](https://en.wikipedia.org/wiki/Cron#CRON_expression) in das Feld **Status-Aktualisierungs-Scheduler-Ausdruck** und klicken Sie auf **Speichern**. Um beispielsweise den Konfigurations-Service täglich um 00:00 Uhr auszuführen, geben Sie `0 0 0 1/1 * ? *` im Feld **Ausdruck für Status-Update-Planung** an.

Das Standardintervall für die Synchronisierung des Status von Acrobat Sign wurde geändert.

## Ähnliche Artikel {#related-articles}

* [Verwenden von Acrobat Sign in einem adaptiven Formular](../../forms/using/working-with-adobe-sign.md)
* [Verwenden von Acrobat Sign mit AEM Forms (Video)](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/forms-and-sign/introduction.html?lang=de)
* [Integrieren von Acrobat Sign mit AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
