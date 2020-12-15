---
title: Informationen zur Verwendung von Bühnen in AEM 3D
seo-title: Informationen zur Verwendung von Bühnen in AEM 3D
description: Bühnen sind kleine Dateien mit 3D-Szenen, die zur Bereitstellung der grundlegenden Anzeigeumgebung dienen.
seo-description: Bühnen sind kleine Dateien mit 3D-Szenen, die zur Bereitstellung der grundlegenden Anzeigeumgebung dienen.
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
translation-type: tm+mt
source-git-commit: 9cc06c16122b98146c51ac61d7fa27553a9d971e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 69%

---


# Informationen zur Verwendung von Bühnen in AEM 3D {#about-the-use-of-stages-in-aem-d}

Bühnen sind platzsparende 3D-Szenendateien, die die grundlegende Anzeigeumgebung (Beleuchtung, Hintergründe, Bodenflächen oder andere feste Geometrie), optionale vordefinierte Kameras und Rendereinstellungen für Renderer von Drittanbietern bereitstellen.

>[!NOTE]
>
>Das Format **[!UICONTROL OBJ 3D]** unterstützt keine Beleuchtung. Deshalb kann es nicht verwendet werden, um Bühnen für AEM 3D bereitzustellen.

Das Dateiformat der Bühne bestimmt, welchen Renderer Sie für diese Bühne verwenden können. Wenn z. B. Autodesk® Maya® für eine hochwertige Wiedergabe verwendet wird, muss die Bühne im Format `.ma` oder `.mb` vorliegen. Wenn Sie beabsichtigen, den standardmäßigen Rapid Refine™-Renderer zu verwenden, ist jedes unterstützte Bühnen-Dateiformat akzeptabel.

Alle Rendereinstellungen in AEM 3D mit Ausnahme des Ausgabebildtyps und der -größe müssen vorkonfiguriert und in der Stage-Datei gespeichert werden, bevor sie in AEM hochgeladen werden.