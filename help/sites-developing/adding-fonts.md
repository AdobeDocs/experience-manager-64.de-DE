---
title: Hinzufügen von Schriftarten für das Grafik-Rendering
seo-title: Adding Fonts for Graphic-Rendering
description: AEM ermöglicht die Erstellung von Grafiken, die Text enthalten, der dynamisch aus Ihrem Inhalt übernommen wird
seo-description: AEM allows you to generate graphics incorporating text dynamically taken from your content
uuid: 67d9b10f-e986-4d29-bde2-10e08075fe17
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6af48ef5-75e6-4b66-bc0d-ecf254b1c4ef
exl-id: f29868e3-d05c-4898-94d1-0c77ab6b72eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 75%

---

# Hinzufügen von Schriftarten für das Grafik-Rendering{#adding-fonts-for-graphic-rendering}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM ermöglicht die Erstellung von Grafiken, die Text enthalten, der dynamisch aus Ihrem Inhalt übernommen wird.

Hierfür können Sie auch Ihre eigenen Schriftarten hochladen und verwenden.

Derzeit unterstützen alle Implementierungen der Java-Plattform [TrueType](https://de.wikipedia.org/wiki/TrueType)-Schriftarten.

1. Öffnen Sie CRXDE Lite und navigieren Sie zu Ihrem Projekt-Programmordner:

   `/apps/<your-project>/`

1. Erstellen Sie unter `/apps/<your-project>/` einen neuen Knoten:

   * **Name**: `fonts`
   * **Typ**: `sling:Folder`

   Speichern Sie alle Änderungen.

1. Kopieren Sie die Schriftarten-Dateien in diesen Ordner, z. B. mit WebDAV.

   >[!NOTE]
   >
   >Die Schriftarten-Dateien im Repository müssen die Dateiendung `*.ttf` oder `*.TTF` aufweisen.

1. Aktualisieren Sie die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) von [Day Commons GFX Font Helper](/help/sites-deploying/osgi-configuration-settings.md). Fügen Sie den Pfad zum Schriftarten-Ordner hinzu, d. h. `/apps/<your-project>/fonts`.

1. Kehren Sie zu CRXDE Lite zurück. Sie sollten jetzt in Ihrem Ordner einen Knoten namens `.fontlist` sehen, der den Namen der importierten Schriftarten enthält.

   Diese Schriftarten stehen jetzt für die Verwendung in der Java-API zur Verfügung.

Ausführliche Informationen zur Verwendung der Schriftarten in der Java-API finden Sie in der [Dokumentation zur Font-Klasse der Java-API](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
