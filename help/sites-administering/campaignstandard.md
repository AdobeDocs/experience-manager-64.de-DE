---
title: Integrieren mit Adobe Campaign Standard
seo-title: Integrating with Adobe Campaign Standard
description: Integrieren mit Adobe Campaign Standard
seo-description: Integrating with Adobe Campaign Standard.
uuid: ef31339e-d925-499c-b8fb-c00ad01e38ad
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 5c0fec99-7b1e-45d6-a115-e498d288e9e1
exl-id: d8d62c2f-3aa5-4fc9-8f42-86d75b6558ce
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 69%

---

# Integrieren mit Adobe Campaign Standard{#integrating-with-adobe-campaign-standard}

>[!NOTE]
>
>In dieser Dokumentation wird beschrieben, wie Sie AEM mit Adobe Campaign Standard, der abonnementbasierten Lösung, integrieren. Wenn Sie Adobe Campaign 6.1 verwenden, finden Sie die entsprechenden Anweisungen in [Integrieren mit Adobe Campaign 6.1](/help/sites-administering/campaignonpremise.md).

Adobe Campaign ermöglicht die Verwaltung von Inhalten und Formularen für die Übermittlung per E-Mail direkt in Adobe Experience Manager.

Damit Sie beide Lösungen gleichzeitig verwenden können, müssen Sie sie zunächst miteinander verknüpfen. Dies umfasst Konfigurationsschritte in Adobe Campaign und Adobe Experience Manager. Diese Schritte werden in diesem Dokument detailliert beschrieben.

Die Arbeit mit Adobe Campaign in AEM bietet die Möglichkeit, über Adobe Campaign E-Mails und Formulare zu versenden. Dies wird beschrieben in [Arbeiten mit Adobe Campaign](/help/sites-authoring/campaign.md).

Des Weiteren sind unter Umständen die folgenden Themen relevant, wenn Sie AEM mit [Adobe Campaign](https://docs.campaign.adobe.com/doc/standard/de/home.html) integrieren:

* [Best Practices für E-Mail-Vorlagen](/help/sites-administering/best-practices-for-email-templates.md)
* [Fehlerbehebung bei der Adobe Campaign-Integration](/help/sites-administering/troubleshooting-campaignintegration.md)

Hinsichtlich der Erweiterung einer Adobe Campaign-Integration sind folgende Seiten empfehlenswert:

* [Erstellen benutzerspezifischer Erweiterungen](/help/sites-developing/extending-campaign-extensions.md)
* [Erstellen benutzerdefinierter Formularzuordnungen](/help/sites-developing/extending-campaign-form-mapping.md)

## Konfigurieren von Adobe Campaign {#configuring-adobe-campaign}

Die Konfiguration von Adobe Campaign umfasst Folgendes:

1. Konfiguration des Benutzers **aemserver**
1. Erstellung eines dedizierten externen Kontos
1. Überprüfung der Option „AEMResourceTypeFilter“
1. Erstellung einer dedizierten Bereitstellungsvorlage

>[!NOTE]
>
>Um diese Vorgänge auszuführen, müssen Sie über die **Administration** Rolle in Adobe Campaign.

### Voraussetzungen {#prerequisites}

Stellen Sie im Voraus sicher, dass Sie über die folgenden Elemente verfügen:

* [Eine AEM-Autoreninstanz](/help/sites-deploying/deploy.md#getting-started)
* [Eine AEM-Veröffentlichungsinstanz](/help/sites-deploying/deploy.md#author-and-publish-installs)
* [Eine Adobe Campaign-Instanz](https://docs.adobe.com/content/docs/de/campaign/ACS.html)

>[!CAUTION]
>
>Die im Abschnitt [Konfigurieren von Adobe Campaign](#configuring-adobe-campaign) und [Konfigurieren von Adobe Experience Manager](#configuring-adobe-experience-manager) -Abschnitte sind erforderlich, damit die Integrationsfunktionen zwischen AEM und Adobe Campaign ordnungsgemäß funktionieren.

### Konfigurieren des Benutzers „aemserver“ {#configuring-the-aemserver-user}

Die **aemserver** -Benutzer muss in Adobe Campaign konfiguriert sein. Die **aemserver** ist ein technischer Anwender, der verwendet wird, um den AEM-Server mit Adobe Campaign zu verbinden.

Navigieren Sie zu **Administration** >  **Benutzer und Sicherheit** >  **Benutzer** und wählen Sie die **aemserver** Benutzer. Klicken Sie darauf, um die Benutzereinstellungen zu öffnen.

* Sie müssen für diesen Benutzer ein Kennwort festlegen. Dies kann nicht über die Benutzeroberfläche erledigt werden. Diese Konfiguration muss von einem technischen Administrator in REST erledigt werden.
* Sie können diesem Benutzer bestimmte Rollen zuweisen, z. B. **deliveryPrepare**, wodurch der Benutzer Sendungen erstellen und bearbeiten kann.

### Konfigurieren eines externen Adobe Experience Manager-Kontos {#configuring-an-adobe-experience-manager-external-account}

Sie müssen ein externes Konto konfigurieren, das es Ihnen ermöglicht, Adobe Campaign mit Ihrer AEM-Instanz zu verknüpfen.

>[!NOTE]
>
>Stellen Sie in AEM sicher, dass Sie das Kennwort für den Benutzer „campaign-remote“ festlegen. Sie müssen dieses Kennwort festlegen, um Adobe Campaign mit AEM zu verknüpfen. Melden Sie sich als Administrator an und wählen Sie an der Benutzeradministrationskonsole den Benutzer „campaign-remote“. Klicken Sie dann auf **Kennwort festlegen**.

Konfigurieren Sie ein externes AEM-Konto wie folgt:

1. Navigieren Sie zu **Administration** > **Anwendungseinstellungen** > **Externe Konten**.

   ![chlimage_1-124](assets/chlimage_1-124.png)

1. Standardeinstellung auswählen **aemInstance** ein externes Konto erstellen oder durch Klicken auf das **Erstellen** Schaltfläche.
1. Auswählen **Adobe Experience Manager** i n **Typ** und geben Sie die Zugriffsparameter ein, die für Ihre AEM Authoring-Instanz verwendet werden: Server-Adresse, Kontoname und Kennwort.

   >[!NOTE]
   >
   >Hängen Sie an die URL keinen abschließenden Schrägstrich **/** an, sonst funktioniert die Verknüpfung nicht.

1. Stellen Sie sicher, dass die Variable **Aktiviert** Kontrollkästchen aktiviert ist, klicken Sie auf **Speichern** , um Ihre Änderungen zu speichern.

### Überprüfen der Option „AEMResourceTypeFilter“ {#verifying-the-aemresourcetypefilter-option}

Die **AEMResourceTypeFilter** wird verwendet, um AEM Ressourcentypen zu filtern, die in Adobe Campaign verwendet werden können. Dies ermöglicht Adobe Campaign das Abrufen von AEM-Inhalten, die speziell für die ausschließliche Verwendung in Adobe Campaign entwickelt wurden.

Diese Option ist vorkonfiguriert. Falls Sie an dieser Option Änderungen vornehmen, funktioniert die Integration unter Umständen nicht.

Überprüfen Sie wie folgt, ob die Option **AEMResourceTypeFilter** konfiguriert ist:

1. Wechseln Sie zu **Administration** > **Anwendungseinstellungen** > **Optionen**.
1. In der Liste können Sie sicherstellen, dass die **AEMResourceTypeFilter** angezeigt und die Pfade korrekt sind.

### Erstellen einer AEM-spezifischen E-Mail-Bereitstellungsvorlage {#creating-an-aem-specific-email-delivery-template}

Die AEM-Funktion ist in den E-Mail-Vorlagen von Adobe Campaign standardmäßig deaktiviert. Sie haben die Möglichkeit, eine neue E-Mail-Bereitstellungsvorlage für die Erstellung von E-Mails mit AEM-Inhalten zu konfigurieren.

Erstellen Sie AEM-spezifische E-Mail-Bereitstellungsvorlagen wie folgt:

1. Wechseln Sie zu **Ressourcen** > **Vorlagen** > **Bereitstellungsvorlagen**.
1. **Auswahl aktivieren** durch Klicken auf das Häkchen in der Aktionsleiste und Auswählen des vorhandenen **Standard-E-Mail (Mail)** Standardvorlage erstellen und diese dann duplizieren, indem Sie auf die **Kopieren** Symbol und Klicken auf **Bestätigen**.
1. Deaktivieren Sie den Auswahlmodus, indem Sie auf die Schaltfläche **x** und öffnen Sie die neu erstellte **Kopie der Standard-E-Mail (Mail)** Vorlage und wählen Sie **Eigenschaften bearbeiten** über die Symbolleiste des Vorlagen-Dashboards.

   Sie können die **Beschriftung** der Vorlage ändern.

1. Legen Sie im Abschnitt **Inhalt** der Eigenschaften **Adobe Experience Manager** als **Inhaltsquelle** fest. Wählen Sie dann das zuvor erstellte externe Konto aus und klicken Sie auf **Bestätigen**.

   Speichern Sie Ihre Änderungen, indem Sie auf **Bestätigen** und anschließend auf **Speichern** klicken.

   Für die aus dieser Vorlage erstellten E-Mail-Bereitstellungen ist die AEM-Inhaltsfunktion aktiviert.

   ![chlimage_1-125](assets/chlimage_1-125.png)

## Konfigurieren von Adobe Experience Manager {#configuring-adobe-experience-manager}

Zum Konfigurieren von AEM müssen Sie folgende Schritte ausführen:

* die Replikation zwischen Instanzen konfigurieren
* AEM mit Adobe Campaign verknüpfen
* den Externalizer konfigurieren

### Konfigurieren der Replikation zwischen AEM-Instanzen {#configuring-replication-between-aem-instances}

Inhalte, die in der AEM-Autoreninstanz erstellt werden, werden zunächst an die Veröffentlichungsinstanz übermittelt. Diese Veröffentlichungsinstanz übermittelt die Inhalte dann an Adobe Campaign. Der Replikationsagent muss deshalb so konfiguriert werden, dass er aus der AEM-Autoreninstanz in die AEM-Veröffentlichungsinstanz repliziert.

>[!NOTE]
>
>Möchten Sie nicht die Replikations-URL sondern stattdessen die öffentlich zugängliche URL verwenden, so haben Sie die Möglichkeit, die **Öffentliche URL** in der folgenden Konfigurationseinstellung in OSGi festzulegen (**Tools** > **Web-Konsole** > **OSGi-Konfiguration > AEM-Kampagnenintegration – Konfiguration**):
**Öffentliche URL:** com.day.cq.mcm.campaign.impl.IntegrationConfigImpl#aem.mcm.campaign.publicUrl

Dieser Schritt ist auch erforderlich, um bestimmte Autoreninstanzkonfigurationen in die Veröffentlichungsinstanz zu replizieren.

So konfigurieren Sie die Replikation zwischen AEM-Instanzen:

1. Wählen Sie in der Authoring-Instanz **AEM**> **Tools **Symbol > **Implementierung** > **Replikation** > **Agenten für Autor** Klicken Sie auf **Standardagent**.

   ![chlimage_1-126](assets/chlimage_1-126.png)

   >[!NOTE]
   Verwenden Sie nach Möglichkeit nicht localhost (eine lokale Kopie von AEM), wenn Sie die Integration mit Adobe Campaign konfigurieren, außer die Veröffentlichungs- und Autoreninstanz befinden sich auf demselben Computer.

1. Klicken **Bearbeiten** und wählen Sie dann **Verkehr** Registerkarte.
1. Konfigurieren Sie den URI, indem Sie **localhost** durch die IP-Adresse oder die Adresse der AEM-Veröffentlichungsinstanz ersetzen.

   ![chlimage_1-127](assets/chlimage_1-127.png)

### Verknüpfen von AEM mit Adobe Campaign {#connecting-aem-to-adobe-campaign}

Bevor Sie AEM und Adobe Campaign zusammen verwenden können, müssen Sie die beiden Lösungen verknüpfen, damit sie miteinander kommunizieren können.

1. Stellen Sie eine Verbindung mit Ihrer AEM-Autoreninstanz her.
1. Auswählen **Instrumente** > **Aktivitäten** > **Cloud** > **Cloud Services**, dann **Jetzt konfigurieren** im Abschnitt &quot;Adobe Campaign&quot;.

   ![chlimage_1-128](assets/chlimage_1-128.png)

1. Erstellen Sie eine neue Konfiguration durch Eingabe einer **Titel** und klicken Sie auf **Erstellen** oder wählen Sie die vorhandene Konfiguration aus, die Sie mit Ihrer Adobe Campaign-Instanz verknüpfen möchten.
1. Passen Sie die Konfiguration so an, dass sie den Parametern Ihrer Adobe Campaign-Instanz entspricht.

   * **Benutzername**: **aemserver**, der für die Herstellung der Verbindung zwischen den beiden Lösungen verwendete Adobe Campaign AEM Integrationspaket-Operator.
   * **Kennwort**: Das Adobe Campaign-Kennwort des aemserver-Operators. Unter Umständen müssen Sie das Kennwort für diesen Operator direkt in Adobe Campaign erneut angeben.
   * **API-Endpunkt**: URL der Adobe Campaign-Instanz.

1. Auswählen **Verbindung zu Adobe Campaign herstellen** und klicken Sie auf **OK**.

   ![chlimage_1-129](assets/chlimage_1-129.png)

   >[!NOTE]
   Nachdem Sie [die E-Mail erstellt und veröffentlicht haben](/help/sites-authoring/campaign.md), müssen Sie die Konfiguration auf der Veröffentlichungsinstanz erneut veröffentlichen.

   ![chlimage_1-130](assets/chlimage_1-130.png)

>[!NOTE]
Prüfen Sie Folgendes, falls die Verbindung nicht hergestellt werden kann:
* Möglicherweise tritt ein Zertifikatfehler auf, wenn Sie eine sichere Verbindung (https) mit einer Adobe Campaign-Instanz herstellen. Sie müssen das Adobe Campaign-Instanzzertifikat der Datei &quot;cacerts&quot;Ihres JDK hinzufügen.
* Weitere Informationen finden Sie in [Fehlerbehebung bei der AEM/Adobe Campaign-Integration](/help/sites-administering/troubleshooting-campaignintegration.md).


### Konfigurieren des Externalizers {#configuring-the-externalizer}

Sie müssen [den Externalizer](/help/sites-developing/externalizer.md) in AEM auf der Autoreninstanz konfigurieren. Der Externalizer ist ein OSGi-Dienst, der es Ihnen ermöglicht, Ressourcenpfade in externe, absolute URLs umzuwandeln. Dieser Dienst bietet einen zentralen Ort für die Konfiguration und Erstellung von externen URLs.

Allgemeine Anweisungen finden Sie unter [Konfigurieren des Externalizers](/help/sites-developing/externalizer.md). Stellen Sie für die Adobe Campaign-Integration sicher, dass Sie den Veröffentlichungsserver unter `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl` nicht auf `localhost:4503` aber auf einen Server, der über die Adobe Campaign-Konsole erreichbar ist.

Wenn er auf `localhost:4503` oder einen anderen Server, den Adobe Campaign nicht erreichen kann, verweist, werden Ihre Bilder auf der Adobe Campaign-Konsole nicht angezeigt.

![chlimage_1-131](assets/chlimage_1-131.png)
