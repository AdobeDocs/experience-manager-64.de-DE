---
title: Aktivitäts-Stream in der Zeitleiste
description: 'Dieser Artikel beschreibt, wie Sie Aktivitätsprotokolle für Assets in der Zeitleiste anzeigen können. '
contentOwner: AG
feature: Asset-Verwaltung
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 98%

---


# Aktivitäts-Stream in der Zeitleiste {#activity-stream-in-timeline}

Diese Funktion zeigt Aktivitätsprotokolle für Assets in der Timeline an. Wenn Sie einen der folgenden Asset-bezogenen Vorgänge in Adobe Experience Manager (AEM) Assets durchführen, aktualisiert die Aktivitäts-Stream-Funktion die Timeline, um die Aktivität anzuzeigen.

Folgende Vorgänge werden im Aktivitäts-Stream protokolliert:

* Erstellen
* Löschen
* Download (einschließlich Ausgabedarstellungen)
* Veröffentlichen
* Veröffentlichung rückgängig machen
* Genehmigen
* Ablehnen
* Verschieben

Die in der Zeitleiste angezeigten Aktivitätsprotokolle werden aus dem Ordner `/var/audit/com.day.cq.dam/content/dam` in CRX abgerufen, in dem Protokolldateien gespeichert werden.

Außerdem wird die Timeline-Aktivität protokolliert, wenn neue Assets hochgeladen oder vorhandene Assets geändert und in AEM über [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) oder das [AEM-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=de) gespeichert werden.

>[!NOTE]
>
>Übergangsarbeitsabläufe werden nicht in der Timeline angezeigt, da keine Verlaufsinformationen für diese Arbeitsabläufe gespeichert werden.

Um den Aktivitäts-Stream anzuzeigen, führen Sie einen oder mehrere Vorgänge für die Assets aus, wählen Sie das Asset aus und wählen Sie dann **[!UICONTROL Zeitleiste]** aus der GlobalNav-Liste aus.

![timeline-3](assets/timeline-3.png)

In der Zeitleiste wird der Aktivitäts-Stream für die mit den Assets ausgeführten Vorgänge angezeigt.

![Aktivität_stream](assets/activity_stream.png)

>[!NOTE]
>
>Der standardmäßige Speicherort für Aufgaben des Typs **Veröffentlichen** und **Veröffentlichung rückgängig machen** befindet sich in `/var/audit/com.day.cq.replication/content`. Für Aufgaben des Typs **Verschieben** ist der standardmäßige Speicherort `/var/audit/com.day.cq.wcm.core.page`.
