---
title: Aktivitäts-Stream in der Timeline
description: 'Dieser Artikel beschreibt, wie Sie Aktivitätsprotokolle für Assets in der Timeline anzeigen können. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Aktivitäts-Stream in der Timeline {#activity-stream-in-timeline}

Diese Funktion zeigt Aktivitätsprotokolle für Assets in der Timeline an. Wenn Sie einen der folgenden Asset-bezogenen Vorgänge in Adobe Experience Manager (AEM) Assets durchführen, aktualisiert die Aktivitäts-Stream-Funktion die Timeline, um die Aktivität anzuzeigen.

Folgende Vorgänge werden im Aktivitäts-Stream protokolliert:

* Erstellen
* Löschen
* Download (einschließlich Wiedergaben)
* Veröffentlichen
* Veröffentlichung rückgängig machen
* Genehmigen
* Ablehnen
* Verschieben

Die Aktivitätsprotokolle, die in der Timeline angezeigt werden sollen, werden von dem Speicherort `/var/audit/com.day.cq.dam/content/dam` in CRX abgerufen, unter dem Protokolldateien gespeichert werden.

Darüber hinaus wird die Timeline-Aktivität protokolliert, wenn neue Assets hochgeladen oder vorhandene geändert und über [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) oder die [AEM-Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html) in AEM eingecheckt werden.

>[!NOTE]
>
>Vorübergehende Arbeitsabläufe werden nicht in der Zeitleiste angezeigt, da keine Verlaufsinformationen für diese Arbeitsabläufe gespeichert werden.

Um den Aktivitätsstream anzuzeigen, führen Sie einen oder mehrere Vorgänge für die Assets aus, wählen Sie das Asset aus und wählen Sie dann **[!UICONTROL Timeline]** aus der GlobalNav-Liste aus.

![timeline-3](assets/timeline-3.png)

In der Timeline wird der Aktivitäts-Stream für die mit den Assets ausgeführten Vorgänge angezeigt.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>Der Standardspeicherort für Protokolle zu **Veröffentlichen**- und **Rückgängigmachen der Veröffentlichung** ist `/var/audit/com.day.cq.replication/content`. Bei **Verschieben**-Aufgaben ist der Standardspeicherort `/var/audit/com.day.cq.wcm.core.page`.
