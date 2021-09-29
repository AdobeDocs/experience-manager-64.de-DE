---
title: Aktivieren der Duplikatserkennung
description: Erfahren Sie, wie Sie die Erkennung von Asset-Duplikaten in AEM aktivieren.
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 40%

---

# Aktivieren der Duplikatserkennung {#enabling-duplicate-detection}

Wenn Sie versuchen, ein Asset hochzuladen, das in Adobe Experience Manager Assets vorhanden ist, wird es von der Funktion zur Duplikatserkennung als Duplikat identifiziert. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Öffnen Sie die Seite **[!UICONTROL Adobe Experience Manager Web Console Configuration]** unter `https://[server]:[port]/system/console/configMgr`.
1. Bearbeiten Sie die Konfiguration für das Servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Wählen Sie die Option **[!UICONTROL Duplikat erkennen]** aus und klicken/tippen Sie auf **[!UICONTROL Speichern]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

Die Funktion zur Duplikatserkennung ist jetzt in [!DNL Experience Manager] Assets aktiviert. Wenn ein Benutzer versucht, ein Asset hochzuladen, das in AEM vorhanden ist, prüft das System auf Konflikte und zeigt diese an. Die Assets werden mit dem SHA-1-Hash identifiziert, der unter `jcr:content/metadata/dam:sha1` gespeichert ist. Das bedeutet, dass doppelte Assets unabhängig von den Dateinamen erkannt werden.

>[!MORELIKETHIS]
>
>* [Duplizieren von Assets in einem vorhandenen Repository (ein Tutorial von Community-Mitgliedern)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

