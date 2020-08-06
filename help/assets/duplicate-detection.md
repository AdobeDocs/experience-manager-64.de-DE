---
title: Aktivieren der Duplikatserkennung
description: Erfahren Sie, wie Sie die Erkennung von Asset-Duplikaten in AEM aktivieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26e860cd513d70d748f872e2ce445a042d075bc6
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 61%

---


# Aktivieren der Duplikatserkennung {#enabling-duplicate-detection}

Wenn Sie versuchen, ein Asset hochzuladen, das in Adobe Experience Manager (AEM) Assets vorhanden ist, wird das Asset von der Funktion zur Duplikatserkennung als Duplikat identifiziert. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Open the **[!UICONTROL Adobe Experience Manager Web Console Configuration]** page at `https://[server]:[port]/system/console/configMgr`.
1. Edit the configuration for the servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Select the **[!UICONTROL detect duplicate]** option, and click/tap **[!UICONTROL Save]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

Die Funktion zur Duplikatserkennung ist nun in AEM Assets aktiviert. Wenn ein Benutzer versucht, ein Asset hochzuladen, das in AEM vorhanden ist, prüft das System auf Konflikte und zeigt diese an. The assets are identified using SHA-1 hash stored at `jcr:content/metadata/dam:sha1`, which means duplicate assets are detected irrespective of the filenames.

>[!MORELIKETHIS]
>
>* [Duplikat-Assets im vorhandenen Repository (ein Tutorial von Community-Mitgliedern)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

