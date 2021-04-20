---
title: Integrieren von Assets in den Aktivitäts-Stream
description: Beschreibt die Aufzeichnungsfunktionen von AEM und wie Sie AEM zum Aufzeichnen bestimmter Ereignisse konfigurieren.
contentOwner: AG
feature: Asset Management
role: Developer
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 76%

---


# Integrieren von Assets in den Aktivitäts-Stream {#integrating-assets-with-activity-stream}

Adobe Experience Manager (AEM) Assets-Benutzer führen zahlreiche Aktionen durch, z. B. das Erstellen, Hochladen und Löschen von Assets. Diese Aktionen können aufgezeichnet werden, sodass Sie einen Benutzeraktivitätenverlauf erstellen können. In diesem Abschnitt werden die Aufzeichnungsfunktionen von AEM beschrieben und gezeigt, und wie Sie AEM zum Aufzeichnen bestimmter Ereignisse konfigurieren.

## Überlegungen zur Leistung und Standardverhalten {#performance-considerations-and-default-behavior}

Diese Integration kann CPU- und Speicherplatz-intensiv sein, beispielsweise beim Massenimport. Aus diesen Gründen ist die AEM Assets-Integration mit dem Aktivität Stream standardmäßig deaktiviert.

## Unterstützte Aktionsereignisse {#supported-action-events}

Die folgenden Ereignisse können zur Aufzeichnung konfiguriert werden:

* Lizenz akzeptiert (ACCEPTED)
* Asset erstellt (ASSET_CREATED)
* Asset verschoben (ASSET_MOVED)
* Asset entfernt (ASSET_REMOVED)
* Lizenz abgelehnt (REJECTED)
* Asset heruntergeladen (DOWNLOADED)
* Asset versioniert (VERSIONED)
* Asset-Version wiederhergestellt (RESTORED)
* Asset-Metadaten aktualisiert (METADATA_UPDATED)
* Asset veröffentlicht auf externem System (PUBLISHED_EXTERNAL)
* Original des Assets aktualisiert (ORIGINAL_UPDATED)
* Asset-Ausgabeformat aktualisiert (RENDITION_UPDATED)
* Asset-Ausgabeformat entfernt (RENDITION_REMOVED)
* Unter-Asset aktualisiert (SUBASSET_UPDATED)
* Unter-Asset entfernt (SUBASSET_REMOVED)

## Konfigurieren der AEM Assets-Ereignisaufzeichnung {#configuring-aem-assets-events-recording}

Die [Webkonsole](/help/sites-deploying/configuring-osgi.md) bietet Zugriff auf die AEM Assets-Ereignis-Recorder-Abstimmung. Gehen Sie wie folgt vor, um den AEM Assets Ereignis-Recorder zu konfigurieren:

1. Navigieren Sie zur **[!UICONTROL Web-Konsole]**.

1. Klicken Sie auf **[!UICONTROL Konfiguration]**.

1. Doppelklicken Sie auf **[!UICONTROL Day CQ DAM-Ereignisaufzeichnung]**.

1. Aktivieren Sie die Option **[!UICONTROL Diesen Service aktivieren]**.

1. Wählen Sie, welche **[!UICONTROL Ereignistypen]** im Benutzer-Aktivitäts-Stream aufgezeichnet werden sollen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Lesen aufgezeichneter Ereignisse {#reading-recorded-events}

Die aufgezeichneten Ereignisse werden als Aktivitäten gespeichert. Sie können sie programmgesteuert mit der [ActivityManager-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html) lesen.
