---
title: Hinzufügen von Schriftarten für das Grafik-Rendering
seo-title: Hinzufügen von Schriftarten für das Grafik-Rendering
description: In AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch Ihren Inhalten entnommen wird.
seo-description: In AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch Ihren Inhalten entnommen wird.
uuid: 67d9b10f-e986-4d29-bde2-10e08075fe17
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6af48ef5-75e6-4b66-bc0d-ecf254b1c4ef
translation-type: tm+mt
source-git-commit: 00317d1ba79f10e98b4c52713d845092b7cc6c2e
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 63%

---


# Hinzufügen von Schriftarten für das Grafik-Rendering{#adding-fonts-for-graphic-rendering}

AEM ermöglicht Ihnen die Erstellung von Grafiken mit dynamisch aus Ihren Inhalten stammendem Text.

Hierfür können Sie auch Ihre eigenen Schriftarten hochladen und verwenden.

Derzeit unterstützen alle Implementierungen der Java-Plattform [TrueType](https://en.wikipedia.org/wiki/Truetype)-Schriftarten.

1. Öffnen Sie die CRXDE Lite und navigieren Sie zum Projektanwendungsordner:

   `/apps/<your-project>/`

1. Under `/apps/<your-project>/` create a new node:

   * **Name**: `fonts`
   * **Typ**: `sling:Folder`

   Speichern Sie alle Änderungen.

1. Kopieren Sie die Schriftarten-Dateien in diesen Ordner, z. B. mit WebDAV.

   >[!NOTE]
   >
   >Font files in the repository must have the suffix `*.ttf` or `*.TTF`.

1. Aktualisieren Sie die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) von [Day Commons GFX Font Helper](/help/sites-deploying/osgi-configuration-settings.md). Add the path to your fonts folder; i.e. `/apps/<your-project>/fonts`.

1. Kehren Sie zu CRXDE Lite zurück. You should now see a `.fontlist` node in your folder containing the name of the imported fonts.

   Diese Schriftarten stehen jetzt für die Verwendung in der Java-API zur Verfügung.

Ausführliche Informationen zur Verwendung der Schriftarten in der Java-API finden Sie in der [Dokumentation zur Font-Klasse der Java-API](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).

