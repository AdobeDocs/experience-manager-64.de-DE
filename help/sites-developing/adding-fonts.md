---
title: Hinzufügen von Schriftarten für das Grafik-Rendering
seo-title: Adding Fonts for Graphic-Rendering
description: In AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch Ihren Inhalten entnommen wird.
seo-description: AEM allows you to generate graphics incorporating text dynamically taken from your content
uuid: 67d9b10f-e986-4d29-bde2-10e08075fe17
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6af48ef5-75e6-4b66-bc0d-ecf254b1c4ef
exl-id: f29868e3-d05c-4898-94d1-0c77ab6b72eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 66%

---

# Hinzufügen von Schriftarten für das Grafik-Rendering{#adding-fonts-for-graphic-rendering}

In AEM können Sie Grafiken erstellen, die Text enthalten, der dynamisch Ihren Inhalten entnommen wird..

Hierfür können Sie auch Ihre eigenen Schriftarten hochladen und verwenden.

Derzeit unterstützen alle Implementierungen der Java-Plattform [TrueType](https://en.wikipedia.org/wiki/Truetype)-Schriftarten.

1. Öffnen Sie die CRXDE Lite und navigieren Sie zum Ordner der Projektanwendung:

   `/apps/<your-project>/`

1. under `/apps/<your-project>/` einen neuen Knoten erstellen:

   * **Name**: `fonts`
   * **Typ**: `sling:Folder`

   Speichern Sie alle Änderungen.

1. Kopieren Sie die Schriftarten-Dateien in diesen Ordner, z. B. mit WebDAV.

   >[!NOTE]
   >
   >Schriftdateien im Repository müssen das Suffix aufweisen `*.ttf` oder `*.TTF`.

1. Aktualisieren Sie die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) von [Day Commons GFX Font Helper](/help/sites-deploying/osgi-configuration-settings.md). Fügen Sie den Pfad zum Ordner &quot;Schriftarten&quot;hinzu. d. h. `/apps/<your-project>/fonts`.

1. Kehren Sie zu CRXDE Lite zurück. Sie sollten jetzt eine `.fontlist` Knoten in Ihrem Ordner, der den Namen der importierten Schriftarten enthält.

   Diese Schriftarten stehen jetzt für die Verwendung in der Java-API zur Verfügung.

Ausführliche Informationen zur Verwendung der Schriftarten in der Java-API finden Sie in der [Dokumentation zur Font-Klasse der Java-API](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
