---
title: Konfigurieren von AEM Assets mit Brand Portal
description: Erfahren Sie, wie AEM Assets mit Brand Portal integriert wird, um Assets und Sammlungen in Brand Portal zu veröffentlichen.
contentOwner: VG
feature: Brand Portal
role: Admin
exl-id: cde35555-259f-4d16-999f-2b93d597b8a5
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 69%

---

# Konfigurieren von AEM Assets mit Brand Portal {#configure-integration-64}

Adobe Experience Manager Assets wird mit Brand Portal über konfiguriert. [!DNL Adobe I/O], wodurch ein IMS-Token zur Autorisierung Ihres Brand Portal-Mandanten abgerufen wird.

>[!NOTE]
>
>Konfigurieren von AEM Assets mit Brand Portal über [!DNL Adobe I/O] wird in AEM 6.4.8.0 und höher unterstützt.
>
>Zuvor wurde Brand Portal über das alte OAuth-Gateway in der klassischen Benutzeroberfläche konfiguriert. Das Gateway ruft mithilfe des JWT-Token-Austauschs ein IMS-Zugriffstoken zur Autorisierung ab.

>[!TIP]
>
>***Nur für Bestandskunden***
>
>Es wird empfohlen, weiterhin die vorhandene alte OAuth-Gateway-Konfiguration zu verwenden. Falls Probleme mit der alten OAuth-Gateway-Konfiguration auftreten, löschen Sie die vorhandene Konfiguration und erstellen Sie eine neue Konfiguration über die [!DNL Adobe I/O].

In diesem Hilfeartikel werden die folgenden beiden Anwendungsfälle beschrieben:

* [Neue Konfiguration](#configure-new-integration-64): Wenn Sie ein neuer Brand Portal-Benutzer sind und Ihre AEM Assets-Autoreninstanz mit Brand Portal konfigurieren möchten, können Sie eine neue Konfiguration in [!DNL Adobe I/O].
* [Upgrade der Konfiguration](#upgrade-integration-64): Wenn Sie bereits ein Brand Portal-Benutzer sind und Ihre AEM Assets-Autoreninstanz mit Brand Portal auf dem alten OAuth Gateway konfiguriert ist, wird empfohlen, die vorhandenen Konfigurationen zu löschen und eine neue Konfiguration auf [!DNL Adobe I/O].

Benutzer dieser Hilfe sollten mit den folgenden Technologien vertraut sein:

* Installieren, Konfigurieren und Verwalten von Adobe Experience Manager- und AEM-Paketen

* Verwenden von Linux- und Microsoft Windows-Betriebssystemen

## Voraussetzungen {#prerequisites}

Sie benötigen Folgendes, um AEM Assets mit Brand Portal zu konfigurieren:

* Eine betriebsbereite AEM Assets-Autoreninstanz mit dem neuesten Service Pack.
* Brand Portal-Mandanten-URL
* Ein Benutzer mit Systemadministrator-Berechtigungen für die IMS-Organisation des Brand Portal-Mandanten

[Herunterladen und Installieren von AEM 6.4](#aemquickstart)

[Laden Sie das aktuelle AEM Service Pack herunter und installieren Sie es](#servicepack)

### Herunterladen und Installieren von AEM 6.4 {#aemquickstart}

Es wird empfohlen, AEM 6.4 zu verwenden, um eine AEM Autoreninstanz einzurichten. Wenn Sie AEM nicht eingerichtet haben, laden Sie es von den folgenden Speicherorten herunter:

* Wenn Sie bereits ein AEM-Kunde sind, laden Sie AEM 6.4 von der [Adobe-Lizenzierungs-Website](http://licensing.adobe.com) herunter.

* Wenn Sie ein Adobe-Partner sind, fordern Sie über das [Adobe Partner Training-Programm](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) AEM 6.4 an.

Anweisungen zum Einrichten einer AEM- Autoreninstanz finden Sie nach dem Herunterladen von AEM unter [Bereitstellen und Verwalten](https://helpx.adobe.com/de/experience-manager/6-4/sites/deploying/using/deploy.html#defaultlocalinstall).

### Herunterladen und Installieren des neuesten AEM Service Packs {#servicepack}

Detaillierte Anweisungen finden Sie unter

* [Versionshinweise zum AEM 6.4 Service Pack](https://helpx.adobe.com/de/experience-manager/6-4/release-notes/sp-release-notes.html)

**Support kontaktieren** , wenn Sie das neueste AEM oder Service Pack nicht finden können.

## Erstellen einer Konfiguration {#configure-new-integration-64}

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, wenn Sie AEM Assets zum ersten Mal mit Brand Portal konfigurieren:

1. [Abrufen eines öffentlichen Zertifikats](#public-certificate)
1. [Erstellen [!DNL Adobe I/O] Integration](#createnewintegration)
1. [Erstellen der Konfiguration des IMS-Kontos](#create-ims-account-configuration)
1. [Konfigurieren von Cloud Service](#configure-the-cloud-service)
1. [Testen der Konfiguration](#test-integration)

>[!NOTE]
>
>Eine AEM Assets-Autoreninstanz darf nur mit einem Brand Portal-Mandanten konfiguriert werden.

### Erstellen der IMS-Konfiguration {#create-ims-configuration}

Die IMS-Konfiguration authentifiziert Ihren Brand Portal-Mandanten mit der Autoreninstanz von AEM Assets.

Die IMS-Konfiguration umfasst zwei Schritte:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Erstellen der Konfiguration des IMS-Kontos](#create-ims-account-configuration)

### Abrufen eines öffentlichen Zertifikats {#public-certificate}

Mit dem öffentlichen Zertifikat können Sie Ihr Profil bei [!DNL Adobe I/O].

1. Melden Sie sich bei Ihrer AEM Assets-Autoreninstanz an. Standard-URL: http:// localhost:4502/aem/start.html
1. Von **Instrumente** ![Instrumente](assets/tools.png) Bedienfeld, navigieren Sie zu **[!UICONTROL Sicherheit]** >> **[!UICONTROL Adobe IMS-Konfigurationen]**.

   ![Benutzeroberfläche der Adobe IMS-Kontokonfiguration](assets/ims-config1.png)

1. Die Seite für Adobe IMS-Konfigurationen wird geöffnet.

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Dadurch gelangen Sie zum **[!UICONTROL Technische Kontokonfiguration für Adobe IMS]** Seite.

1. Standardmäßig wird die Registerkarte **Zertifikat** geöffnet.

   Wählen Sie in **Cloud-Lösung** die Option **[!UICONTROL Adobe Brand Portal]** aus.

1. Markieren Sie das Kontrollkästchen **[!UICONTROL Neues Zertifikat erstellen]** und geben Sie eine **alias** für das Zertifikat. Der Alias dient als Name des Dialogfelds.

1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Ein Dialogfeld wird angezeigt. Klicken Sie auf **[!UICONTROL OK]**, um das öffentliche Zertifikat zu generieren.

   ![Zertifikat erstellen](assets/ims-config2.png)

1. Klicken Sie auf **[!UICONTROL Öffentlichen Schlüssel herunterladen]** und speichern Sie die Zertifikatdatei *AEM-Adobe-IMS.crt* auf Ihrem Computer. Die Zertifikatdatei wird verwendet, um [erstellen [!DNL Adobe I/O] Integration](#createnewintegration).

   ![Zertifikat herunterladen](assets/ims-config3.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Um auf der Registerkarte **Konto** das Adobe IMS-Konto zu erstellen, benötigen Sie die Integrationsdetails. Lassen Sie diese Seite vorerst offen.

   Öffnen Sie eine neue Registerkarte und [Erstellen [!DNL Adobe I/O] Integration](#createnewintegration) um die Integrationsdetails für IMS-Kontokonfigurationen abzurufen.

### Erstellen [!DNL Adobe I/O] Integration {#createnewintegration}

[!DNL Adobe I/O] -Integration generiert API-Schlüssel, Client Secret und Payload (JWT), die zum Einrichten der IMS-Kontokonfigurationen erforderlich sind.

1. Anmelden bei [!DNL Adobe I/O] Konsole mit Systemadministrator-Berechtigungen für die IMS-Organisation des Brand Portal-Mandanten.

   Standard-URL: [https://console.adobe.io/](https://console.adobe.io/)

1. Klicken Sie auf **[!UICONTROL Integration erstellen]**.

1. Wählen Sie **[!UICONTROL Auf API zugreifen]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   ![Neue Integration erstellen](assets/create-new-integration1.png)

1. Eine neue Integrationsseite wird geöffnet.

   Wählen Sie Ihre Organisation aus der Dropdown-Liste aus.

   Wählen Sie in **[!UICONTROL Experience Cloud]** den Eintrag **[!UICONTROL AEM Brand Portal]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   Wenn die Option „Brand Portal“ für Sie deaktiviert ist, stellen Sie sicher, dass Sie die richtige Organisation aus dem Dropdown-Feld über der Option **[!UICONTROL Adobe Services]** ausgewählt haben. Wenn Sie Ihre Organisation nicht kennen, wenden Sie sich an Ihren Administrator.

   ![Integration erstellen](assets/create-new-integration2.png)

1. Geben Sie einen Namen und eine Beschreibung für die Integration an. Klicken Sie auf **[!UICONTROL Eine Datei von Ihrem Computer auswählen]** und laden Sie die `AEM-Adobe-IMS.crt`-Datei hoch, die im Abschnitt [Öffentliche Zertifikate erhalten](#public-certificate) heruntergeladen wurde.

1. Wählen Sie das Profil Ihrer Organisation aus.

   Sie können auch das Standardprofil **[!UICONTROL Assets Brand Portal]** auswählen und auf **[!UICONTROL Integration erstellen]** klicken. Die Integration wird erstellt.

1. Klicken Sie auf **[!UICONTROL Weiter zu Integrationsdetails]**, um die Integrationsinformationen anzuzeigen.

   Kopieren Sie den **[!UICONTROL API-Schlüssel]**.

   Klicken Sie auf **[!UICONTROL Client-Geheimnis abrufen]** und kopieren Sie den Client-Geheimnisschlüssel.

   ![API-Schlüssel, Client-Geheimnis und Payload-Daten einer Integration ](assets/create-new-integration3.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL JWT]** und kopieren Sie die **[!UICONTROL JWT-Payload]**.

   API-Schlüssel, Client-Geheimnisschlüssel und JWT-Payload-Informationen werden verwendet, um eine IMS-Kontokonfiguration zu erstellen.

### Erstellen der Konfiguration des IMS-Kontos {#create-ims-account-configuration}

Stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Erstellen [!DNL Adobe I/O] Integration](#createnewintegration)

**Schritte zum Erstellen der Konfiguration des IMS-Kontos:**

1. Öffnen Sie die Seite „IMS-Konfiguration“, Registerkarte **[!UICONTROL Konten]**. Sie haben die Seite am Ende des Abschnitts [Abrufen eines öffentlichen Zertifikats](#public-certificate) geöffnet gelassen.

1. Geben Sie einen **[!UICONTROL Titel]** für das IMS-Konto an.

   Geben Sie in **[!UICONTROL Autorisierungsserver]** die URL ein: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Fügen Sie den API-Schlüssel, das Client Secret und die JWT-Payload ein, die Sie am Ende von [Erstellen [!DNL Adobe I/O] Integration](#createnewintegration).

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Die Integration wird erstellt.

   ![IMS-Kontokonfiguration](assets/create-new-integration6.png)

1. Wählen Sie die IMS-Konfiguration aus und klicken Sie auf **[!UICONTROL Systemdiagnose]**. Das folgende Dialogfeld wird angezeigt.

   Klicken Sie auf **[!UICONTROL Prüfen]**. Bei erfolgreicher Verbindung wird die Meldung *Token erfolgreich abgerufen* angezeigt.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Sie dürfen nur eine IMS-Konfiguration haben. Erstellen Sie nicht mehrere IMS-Konfigurationen.
>
>Vergewissern Sie sich, dass die IMS-Konfiguration die Konsistenzprüfung besteht. Wenn die Konfiguration die Konsistenzprüfung nicht besteht, ist sie ungültig. Sie müssen sie löschen und eine neue gültige Konfiguration erstellen.

### Konfigurieren von Cloud Service {#configure-the-cloud-service}

Führen Sie die folgenden Schritte aus, um eine Cloud Service-Konfiguration für Brand Portal zu erstellen:

1. Melden Sie sich bei Ihrer AEM Assets-Autoreninstanz an

   Standard-URL: http:// localhost:4502/aem/start.html
1. Von **Instrumente** ![Instrumente](assets/tools.png) Bedienfeld, navigieren Sie zu **[!UICONTROL Cloud Services > > AEM Brand Portal]**.

   Die Seite zur Brand Portal-Konfiguration wird geöffnet.

1. Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Geben Sie einen **[!UICONTROL Titel]** für die Konfiguration ein.

   Wählen Sie die im Schritt erstellte IMS-Konfiguration aus und [erstellen Sie die IMS-Kontokonfiguration](#create-ims-account-configuration).

   Geben Sie in **[!UICONTROL Dienst-URL]** Ihre Brand Portal-Mandanten-URL ein.

   ![](assets/create-cloud-service.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Cloud-Konfiguration wird erstellt. Ihre AEM Assets-Autoreninstanz ist jetzt mit dem Brand Portal-Mandanten integriert.

### Testen der Konfiguration {#test-integration}

1. Melden Sie sich bei Ihrer AEM Assets-Autoreninstanz an

   Standard-URL: http:// localhost:4502/aem/start.html

1. Von **Instrumente** ![Instrumente](assets/tools.png) Bedienfeld, navigieren Sie zu **[!UICONTROL Bereitstellung > Replikation]**.

   ![](assets/test-integration1.png)

1. Die Replikationsseite wird geöffnet.

   Klicken **[!UICONTROL Agenten für Autor]**.

   ![](assets/test-integration2.png)

1. Für jeden Mandanten werden vier Replikationsagenten erstellt.

   Suchen Sie die Replikationsagenten Ihres Brand Portal-Mandanten.

   Klicken Sie auf die Replikationsagenten-URL.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >Die Replikationsagenten funktionieren parallel und teilen die Auftragsverteilung gleichmäßig auf, wodurch die Veröffentlichungsgeschwindigkeit im Vergleich zur ursprünglichen Geschwindigkeit vervierfacht wird. Wenn der Cloud-Service konfiguriert wurde, sind keine zusätzlichen Konfigurationsschritte erforderlich, um die Replikationsagenten zu aktivieren. Sie werden standardmäßig aktiviert, um die parallele Veröffentlichung mehrerer Assets zu ermöglichen.

1. Um die Verbindung zwischen AEM Assets Author und Brand Portal zu überprüfen, klicken Sie auf **[!UICONTROL Verbindung testen]**.

   ![](assets/test-integration4.png)

1. Sehen Sie sich den unteren Bereich der Testergebnisse an, um zu prüfen, ob die Replikation erfolgreich war.

   ![](assets/test-integration5.png)


1. Überprüfen Sie die Testergebnisse für alle vier Replikationsagenten einzeln.

   >[!NOTE]
   >
   >Vermeiden Sie es, einen der Replikationsagenten zu deaktivieren, da dies dazu führen kann, dass die Replikation einiger Assets fehlschlägt.
   >
   >Stellen Sie sicher, dass alle vier Replikationsagenten so konfiguriert sind, dass Zeitüberschreitungsfehler vermieden werden. Siehe [Beheben von Problemen beim parallelen Veröffentlichen in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html?lang=de#connection-timeout).

Brand Portal wurde erfolgreich mit Ihrer AEM Assets-Autoreninstanz konfiguriert. Sie haben nun die folgenden Möglichkeiten:

* [Veröffentlichen von Assets aus AEM Assets in Brand Portal](../assets/brand-portal-publish-assets.md)
* [Veröffentlichen von Ordnern aus AEM Assets in Brand Portal](../assets/brand-portal-publish-folder.md)
* [Veröffentlichen von Sammlungen aus AEM Assets in Brand Portal](../assets/brand-portal-publish-collection.md)
* [Konfigurieren der Asset-Beschaffung](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=de) Ermöglichen es den Brand Portal-Benutzern, Assets in AEM Assets beizutragen und zu veröffentlichen.

## Upgrade der Konfiguration {#upgrade-integration-64}

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um vorhandene Konfigurationen zu aktualisieren:

1. [Überprüfen von laufenden Aufträgen](#verify-jobs)
1. [Löschen von vorhandenen Konfigurationen](#delete-existing-configuration)
1. [Erstellen einer Konfiguration](#configure-new-integration-64)

### Überprüfen von laufenden Aufträgen {#verify-jobs}

Stellen Sie sicher, dass in Ihrer AEM Assets-Autoreninstanz kein Veröffentlichungsauftrag ausgeführt wird, bevor Sie Änderungen vornehmen. Dazu können Sie alle vier Replikationsagenten überprüfen und sicherstellen, dass die Warteschlange ideal/leer ist.

1. Melden Sie sich bei Ihrer AEM Assets-Autoreninstanz an

   Standard-URL: http:// localhost:4502/aem/start.html

1. Von **Instrumente** ![Instrumente](assets/tools.png) Bedienfeld, navigieren Sie zu **[!UICONTROL Bereitstellung > Replikation]**.

1. Die Replikationsseite wird geöffnet.

   Klicken **[!UICONTROL Agenten für Autor]**.

   ![](assets/test-integration2.png)

1. Suchen Sie die Replikationsagenten Ihres Brand Portal-Mandanten.

   Stellen Sie sicher, dass für alle Replikationsagenten die **Warteschlange im Leerlauf ist** und kein Veröffentlichungsauftrag aktiv ist.

   ![](assets/test-integration3.png)

### Löschen von vorhandenen Konfigurationen {#delete-existing-configuration}

Sie müssen beim Löschen der vorhandenen Konfiguration die folgende Checkliste ausführen.

* Alle vier Replikationsagenten löschen
* Cloud-Dienst löschen
* Mac-Benutzer löschen

Führen Sie die folgenden Schritte aus, um die vorhandene Konfiguration zu löschen:

1. Melden Sie sich bei Ihrer AEM Assets-Autoreninstanz an und öffnen Sie CRX Lite als Administrator.

   Standard-URL: http:// localhost:4502/crx/de/index.jsp

1. Navigieren Sie zu `/etc/replications/agents.author` und löschen Sie alle vier Replikationsagenten Ihres Brand Portal-Mandanten.

   ![](assets/delete-replication-agent.png)

1. Navigieren Sie zu `/etc/cloudservices/mediaportal` und löschen Sie die **Cloud Service-Konfiguration**.

   ![](assets/delete-cloud-service.png)

1. Navigieren Sie zu `/home/users/mac` und löschen Sie die **Mac-Benutzer** Ihres Brand Portal-Mandanten.

   ![](assets/delete-mac-user.png)


Sie können jetzt [Konfiguration erstellen](#configure-new-integration-64) auf Ihrer AEM 6.4-Autoreninstanz in [!DNL Adobe I/O].



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

Nach erfolgreicher Replikation können Sie Assets, Ordner und Sammlungen in Brand Portal veröffentlichen. Weitere Details finden Sie unter:

* [Veröffentlichen von Assets in Brand Portal](brand-portal-publish-assets.md)
* [Veröffentlichen von Assets und Ordnern in Brand Portal](brand-portal-publish-folder.md)
* [Veröffentlichen von Sammlungen in Brand Portal](brand-portal-publish-collection.md)
