---
title: Aktivieren der Duplikatserkennung
description: Erfahren Sie, wie Sie die Erkennung doppelter Assets in AEM aktivieren.
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 26%

---

# Aktivieren der Duplikatserkennung {#enabling-duplicate-detection}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Sie versuchen, ein Asset hochzuladen, das in Adobe Experience Manager Assets vorhanden ist, wird es von der Funktion zur Duplikatserkennung als Duplikat identifiziert. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Öffnen Sie die **[!UICONTROL Konfiguration der Adobe Experience Manager-Web-Konsole]** page at `https://[server]:[port]/system/console/configMgr`.
1. Bearbeiten Sie die Konfiguration für das Servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Wählen Sie die **[!UICONTROL Duplikat erkennen]** und klicken/tippen Sie auf **[!UICONTROL Speichern]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

Die Funktion zur Duplikatserkennung ist jetzt in aktiviert. [!DNL Experience Manager] Assets. Wenn ein Benutzer versucht, ein in AEM vorhandenes Asset hochzuladen, prüft das System den Konflikt und zeigt es an. Die Elemente werden mit dem unter `jcr:content/metadata/dam:sha1` gespeicherten SHA-1-Hash identifiziert, d. h. doppelte Assets werden unabhängig von den Dateinamen erkannt.

>[!MORELIKETHIS]
>
>* [Duplizieren von Assets in einem vorhandenen Repository (ein Tutorial von Community-Mitgliedern)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

