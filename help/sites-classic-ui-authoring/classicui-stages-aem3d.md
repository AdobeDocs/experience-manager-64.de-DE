---
title: Informationen zur Verwendung von Bühnen in AEM 3D
seo-title: Wissenswertes zur Verwendung von Bühnen in AEM 3D
description: Bühnen sind platzsparende 3D-Szenendateien, die die grundlegende Anzeigeumgebung (Beleuchtung, Hintergründe, Bodenflächen oder andere feste Geometrie), optionale vordefinierte Kameras und Rendereinstellungen für Renderer von Drittanbietern bereitstellen.
seo-description: Bühnen sind platzsparende 3D-Szenendateien, die die grundlegende Anzeigeumgebung (Beleuchtung, Hintergründe, Bodenflächen oder andere feste Geometrie), optionale vordefinierte Kameras und Rendereinstellungen für Renderer von Drittanbietern bereitstellen.
uuid: 303ecbbd-131e-4c6f-812a-1e056b1e1d63
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: cbcfbe88-e60c-446c-bbfe-2509831d6c22
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42

---


# Wissenswertes zur Verwendung von Bühnen in AEM 3D{#about-the-use-of-stages-in-aem-d}

Bühnen sind platzsparende 3D-Szenendateien, die die grundlegende Anzeigeumgebung (Beleuchtung, Hintergründe, Bodenflächen oder andere feste Geometrie), optionale vordefinierte Kameras und Rendereinstellungen für Renderer von Drittanbietern bereitstellen.

>[!NOTE]
>
>Das Format OBJ 3D unterstützt kein Licht. Deshalb kann es nicht verwendet werden, um Bühnen für AEM 3D bereitzustellen.

Das Dateiformat der Bühne bestimmt, welchen Renderer Sie für diese Bühne verwenden können. For example, if Autodesk® Maya® is used for high-quality rendering, the stage must be in `.ma` or `.mb` format. Wenn Sie beabsichtigen, den standardmäßigen Rapid Refine™-Renderer zu verwenden, ist jedes unterstützte Bühnen-Dateiformat akzeptabel.

Alle Rendereinstellungen in AEM 3D, mit Ausnahme des Ausgabebildtyps und der -größe, müssen vor dem Hochladen in AEM vorkonfiguriert und in der Bühnendatei gespeichert werden.

