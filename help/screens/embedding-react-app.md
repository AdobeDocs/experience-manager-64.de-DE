---
title: Einbetten einer REACT-Anwendung mit dem AEM SPA Editor und Integration mit AEM Screens Analytics
seo-title: Einbetten einer REACT-Anwendung mit dem AEM SPA Editor und Integration mit AEM Screens Analytics
description: Auf dieser Seite erfahren Sie, wie Sie eine interaktive Single Page Application mithilfe von REACT (oder Angular) mit dem AEM SPA-Editor einbetten, der von Geschäftsleuten in AEM konfiguriert werden kann, und wie Sie Ihre interaktive Anwendung offline in Adobe Analytics integrieren.
seo-description: Auf dieser Seite erfahren Sie, wie Sie eine interaktive Single Page Application mithilfe von REACT (oder Angular) mit dem AEM SPA-Editor einbetten, der von Geschäftsleuten in AEM konfiguriert werden kann, und wie Sie Ihre interaktive Anwendung offline in Adobe Analytics integrieren.
uuid: 02ae67bb-058a-4aa9-b484-0c60a8d897ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 70fdeeb8-0c82-44f3-a6fa-ee4dfb32a90b
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Einbetten einer REACT-Anwendung mit dem AEM SPA Editor und Integration mit AEM Screens Analytics{#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

In diesem Abschnitt erfahren Sie, wie Sie mit REACT (oder Angular) unter Einsatz des AEM SPA Editors eine interaktive Single Page Application einbetten, die von Geschäftsexperten in AEM konfiguriert werden kann. Außerdem lernen Sie, wie Sie Ihre interaktive Anwendung mit Adobe Analytics im Offline-Modus integrieren können.

## Verwenden des AEM SPA Editors {#using-the-aem-spa-editor}

Gehen Sie wie folgt vor, um den AEM SPA Editor zu verwenden:

1. Klonen Sie die AEM SPA Editor-Repo unter [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Dieser Archetyp erstellt ein Adobe Experience Manager-Projekt mit minimalen Umfang als Ausgangspunkt für Ihre eigenen SPA-Projekte. Die Eigenschaften, die bei Verwendung dieses Archetyps angegeben werden müssen, ermöglichen es, alle Teile dieses Projekts beliebig zu benennen.

1. Folgen Sie den Readme-Anweisungen, um ein AEM SPA Editor-Archetypprojekt zu erstellen:

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >Wir verwenden als **GroupId** den Wert ***com.adobe.aem.screens*** und als **ArtifactId** den Wert ***Meine Beispiel-SPA*** (die Standardeinstellung). Sie können nach Bedarf Ihre eigenen Parameter auswählen.

1. Nachdem das Projekt erstellt wurde, verwenden Sie entweder eine IDE oder einen Editor Ihrer Wahl und importieren Sie das erstellte Maven-Projekt.
1. Stellen Sie in Ihrer lokalen AEM-Instanz mit dem Befehl ***mvn clean install -PautoInstallPackage*** bereit.

### Bearbeiten von Inhalten in der REACT-App {#editing-content-in-the-react-app}

Bearbeiten von Inhalten in der REACT-App:

1. Navigieren Sie zu ***http://localhost:4502/editor.html/content/mysamplespa/en/home.html*** (ersetzen Sie Hostname, Port und Projektname, falls zutreffend).
1. Sie sollten den Text bearbeiten können, der in der Anwendung „Hello World“ angezeigt wird.

### Hinzufügen der interaktiven REACT-App zu AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Gehen Sie wie folgt vor, um die interaktive REACT-App AEM Screens hinzuzufügen:

1. Erstellen Sie ein neues AEM Screens-Projekt. Weitere Infos finden Sie unter [Erstellen und Verwalten von Projekten](/help/screens/creating-a-screens-project.md).

   >[!NOTE]
   >
   >Erstellen Sie einen **Sequenzkanal**, während Sie einen Kanal im Ordner **Kanäle** Ihres Screens-Projekts erstellen.
   >
   >Weitere Infos finden Sie unter [Erstellen und Verwalten von Kanälen](/help/screens/managing-channels.md).

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. Bearbeiten Sie einen beliebigen Sequenzkanal und ziehen Sie eine eingebettete Seitenkomponente per Drag-and-Drop.

   Weitere Infos finden Sie unter [Hinzufügen von Komponenten zu Kanälen](/help/screens/adding-components-to-a-channel.md).

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie beim Zuweisen des Kanals zur Anzeige das Benutzerinteraktionsereignis hinzufügen.

1. Klicken Sie in der Aktionsleiste auf **Bearbeiten**, um die Eigenschaften des Sequenzkanals zu bearbeiten.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Ziehen Sie die Komponente **Eingebettete Seite** per Drag-and-Drop und wählen Sie die Homepage unter der Anwendung „mysamplespa“ aus, z. B. ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Registrieren Sie einen Player für dieses Projekt. Sie sollten Ihre interaktive Anwendung jetzt auf AEM Screens anzeigen können.

   Einzelheiten zur Registrierung eines Geräts finden Sie unter [Geräteregistrierung](/help/screens/device-registration.md).

## Integrieren der SPA mit Adobe Analytics mit Offline-Funktionen über AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Gehen Sie wie folgt vor, um die SPA mit Adobe Analytics mit Offline-Funktionen über AEM Screens zu integrieren:

1. Konfigurieren Sie Adobe Analytics in AEM Screens.

   Refer to [Configuring Adobe Analytics with AEM Screens](/help/screens/configuring-adobe-analytics-aem-screens.md) to learn how to perform sequencing in Adobe Analytics with AEM Screens and send custom events using offline Adobe Analytics.

1. Bearbeiten Sie Ihre React-App in der IDE/dem Editor Ihrer Wahl (insbesondere die Textkomponente oder eine andere Komponente, die Sie zum Ausgeben von Ereignissen verwenden möchten).
1. Fügen Sie beim Klick- oder anderen Ereignis, das Sie für Ihre Komponente erfassen möchten, die Analyseinformationen mit dem Standarddatenmodell hinzu.

   Refer to [Configuring Adobe Analytics with AEM Screen](/help/screens/configuring-adobe-analytics-aem-screens.md)s for more details.

1. Rufen Sie die AEM Screens Analytics API auf, um das Ereignis offline zu speichern und es in Bursts an Adobe Analytics zu senden.

   Beispiel:

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().getTime(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().getTime(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().getTime(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >Die Player-Firmware fügt den gesendeten benutzerspezifischen Analysedaten automatisch weitere Details zum Player und seiner Laufzeitumgebung hinzu. Daher müssen Sie möglicherweise keine Details zu Betriebssystemen und Geräten auf niedriger Ebene erfassen, es sei denn, dies ist absolut notwendig. Sie müssen sich nur auf die Geschäftsanalysedaten konzentrieren.

