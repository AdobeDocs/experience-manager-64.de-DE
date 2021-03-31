---
title: Aktivieren der Duplikatserkennung
description: Erfahren Sie, wie Sie die Erkennung von Asset-Duplikaten in AEM aktivieren.
contentOwner: AG
feature: Asset-Verwaltung, Asset-Berichte
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 60%

---


# Aktivieren der Duplikatserkennung {#enabling-duplicate-detection}

Wenn Sie versuchen, ein Asset hochzuladen, das in Adobe Experience Manager (AEM) Assets vorhanden ist, wird das Asset von der Funktion zur Duplikatserkennung als Duplikat identifiziert. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Öffnen Sie die Seite **[!UICONTROL Adobe Experience Manager Web Console Configuration]** unter `https://[server]:[port]/system/console/configMgr`.
1. Bearbeiten Sie die Konfiguration für das Servlet **[!UICONTROL Day CQ DAM Asset]** erstellen.
1. Wählen Sie die Option **[!UICONTROL Duplikat erkennen]** und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

Die Funktion zur Duplikatserkennung ist nun in AEM Assets aktiviert. Wenn ein Benutzer versucht, ein Asset hochzuladen, das in AEM vorhanden ist, prüft das System auf Konflikte und zeigt diese an. Die Assets werden mit dem SHA-1-Hash identifiziert, der bei `jcr:content/metadata/dam:sha1` gespeichert ist. Das bedeutet, dass Duplikat-Assets unabhängig von den Dateinamen erkannt werden.

>[!MORELIKETHIS]
>
>* [Duplikat-Assets im vorhandenen Repository (ein Tutorial von Community-Mitgliedern)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

