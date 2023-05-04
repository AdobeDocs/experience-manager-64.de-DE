---
title: Integrieren von Assets in den Aktivitäts-Stream
description: Beschreibt die Aufzeichnungsfunktionen von [!DNL Experience Manager] und wie Sie [!DNL Experience Manager] , um bestimmte Ereignisse aufzuzeichnen.
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 38%

---

# Integrieren von Assets in den Aktivitäts-Stream {#integrating-assets-with-activity-stream}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Benutzer von Adobe Experience Manager Assets führen viele Aktionen durch, z. B. das Erstellen, Hochladen und Löschen von Assets. Diese Aktionen können aufgezeichnet werden, sodass Sie einen Benutzeraktivitätenverlauf erstellen können. In diesem Abschnitt werden die Aufzeichnungsfunktionen von [!DNL Experience Manager] und die Konfigration von [!DNL Experience Manager] zum Aufzeichnen bestimmter Ereignisse beschrieben.

## Leistungsaspekte und Standardverhalten {#performance-considerations-and-default-behavior}

Diese Integration kann CPU- und Speicherplatz-intensiv sein, beispielsweise beim Massenimport. Aus diesen Gründen [!DNL Experience Manager] Die Integration von Assets mit dem Aktivitäts-Stream ist standardmäßig deaktiviert.

## Unterstützte Aktionsereignisse {#supported-action-events}

Die folgenden Ereignisse können zur Aufzeichnung konfiguriert werden:

* Lizenz akzeptiert (AKZEPTIERT)
* Asset erstellt (ASSET_CREATED)
* Asset verschoben (ASSET_MOVED)
* Asset entfernt (ASSET_REMOVED)
* Lizenz abgelehnt (ABGELEHNT)
* Asset heruntergeladen (HERUNTERGELADEN)
* Asset versioniert (VERSIONED)
* Asset-Version wiederhergestellt (RESTORED)
* Asset-Metadaten aktualisiert (METADATA_UPDATED)
* Asset in externem System veröffentlicht (PUBLISHED_EXTERNAL)
* Original des Assets aktualisiert (ORIGINAL_UPDATED)
* Asset-Ausgabedarstellung aktualisiert (RENDITION_UPDATED)
* Asset-Ausgabedarstellung entfernt (RENDITION_REMOVED)
* Unter-Asset aktualisiert (SUBASSET_UPDATED)
* Unter-Asset entfernt (SUBASSET_REMOVED)

## Konfiguration [!DNL Assets] Ereignisaufzeichnung {#configuring-aem-assets-events-recording}

Die [Webkonsole](/help/sites-deploying/configuring-osgi.md) bietet Zugriff auf [!DNL Assets] Optimierung der Ereignisaufzeichnung. So konfigurieren Sie die [!DNL Assets] Ereignisaufzeichnung: Gehen Sie wie folgt vor:

1. Navigieren Sie zum **[!UICONTROL Webkonsole]**

1. Klicken Sie auf **[!UICONTROL Konfiguration]**.

1. Doppelklicken Sie auf **[!UICONTROL Day CQ DAM-Ereignisaufzeichnung]**.

1. Aktivieren Sie die Option **[!UICONTROL Diesen Service aktivieren]**.

1. Wählen Sie, welche **[!UICONTROL Ereignistypen]** im Benutzer-Aktivitäts-Stream aufgezeichnet werden sollen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Lesen aufgezeichneter Ereignisse {#reading-recorded-events}

Die aufgezeichneten Ereignisse werden als Aktivitäten gespeichert. Sie können sie programmgesteuert lesen, indem Sie die [ActivityManager-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
