---
title: Arbeiten mit Dynamic Media
seo-title: Working with Dynamic Media
description: Informationen zur Verwendung von Dynamic Media zum Bereitstellen von Assets für den Gebrauch in Web, Mobile und Social Media
seo-description: Learn how to use Dynamic Media to deliver assets for consumption on web, mobile, and social sites.
uuid: 4dc0f436-d20e-4e8b-aeff-5515380fa44d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: a8063d43-923a-42ac-9a16-0c7fadd8f73f
exl-id: f8a3936e-82b5-46c7-9614-b97162e27d6a
feature: Asset Management,Renditions
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 70%

---

# Arbeiten mit Dynamic Media {#working-with-dynamic-media}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit [Dynamic Media](https://www.adobe.com/de/solutions/web-experience-management/dynamic-media.html) können Sie visuell ansprechende Merchandising- und Marketing-Assets nach Bedarf bereitstellen, die automatisch für die Anzeige auf Web- sowie Mobile- und Social-Media-Sites skaliert werden. Mithilfe einer Reihe Übergeordneter Assets generiert und liefert Dynamic Media mehrere Varianten ansprechender Inhalte in Echtzeit über sein globales, skalierbares und leistungsoptimiertes Netzwerk.

Dynamische Medien ermöglichen interaktive Anzeigeerlebnisse wie Zoom, Drehen um 360 Grad und Videos. Dynamic Media verfügt über eine einzigartige Integration der Workflows der Adobe Experience Manager Digital Asset Management (Assets)-Lösung, um den Digital-Campaign-Verwaltungsprozess zu vereinfachen und zu optimieren.

<!-- DEAD ARTICLE >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Einsatzmöglichkeiten für Dynamic Media {#what-you-can-do-with-dynamic-media}

Mit Dynamic Media können Sie Assets vor ihrer Veröffentlichung verwalten. Eine ausführliche Beschreibung der allgemeinen Arbeit mit digitalen Assets finden Sie in [Arbeiten mit digitalen Assets](managing-assets-touch-ui.md). Die allgemeinen Themen umfassen das Hochladen, Herunterladen, Bearbeiten und Veröffentlichen von Assets, das Anzeigen und Bearbeiten von Eigenschaften und die Suche nach Assets.

Zu den Funktionen, die nur für Dynamic Media verfügbar sind, gehören:

* [Karussellbanner](carousel-banners.md)
* [Bildsets](image-sets.md)
* [Interaktive Bilder](interactive-images.md)
* [Interaktive Videos](interactive-videos.md)
* [Gemischte Mediensets](mixed-media-sets.md)
* [Panoramabilder](panoramic-images.md)

* [Rotationssets](spin-sets.md)
* [Video](video.md)
* [Bereitstellen von Dynamic Media-Assets](delivering-dynamic-media-assets.md)
* [Verwalten von Assets](managing-assets.md)
* [Verwenden von Schnellansichten zum Erstellen benutzerdefinierter Popups](custom-pop-ups.md)

Siehe auch [Einrichten von Dynamic Media](administering-dynamic-media.md).

>[!NOTE]
>
>Informationen zu den Unterschieden zwischen der Verwendung von Dynamic Media und der Integration von Dynamic Media Classic in AEM finden Sie unter [Dynamic Media Classic-Integration versus Dynamic Media](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media).

## Aktivierte und deaktivierte Dynamic Media-Funktion im Vergleich {#dynamic-media-on-versus-dynamic-media-off}

Anhand der folgenden Merkmale können Sie erkennen, ob Dynamic Media aktiviert ist:

* Dynamische Ausgabedarstellungen sind beim Herunterladen oder Anzeigen von Assets in der Vorschau verfügbar.
* Bildsets, Rotationssets und Sets für gemischte Medien sind verfügbar.
* PTIFF-Ausgabedarstellungen werden erstellt.

Wenn Sie auf ein Bild-Asset klicken, sieht die Ansicht des Assets in Dynamic Media anders aus [enabled](config-dynamic.md#enabling-dynamic-media). Dynamic Media nutzt die On-Demand-HTML5-Viewer.

### Dynamische Ausgabedarstellungen {#dynamic-renditions}

Dynamische Ausgabedarstellungen wie Bild- und Viewer-Vorgaben (unter **[!UICONTROL Dynamisch]**) sind verfügbar, wenn Dynamic Media aktiviert ist.

![chlimage_1-358](assets/chlimage_1-358.png)

### Bildsets, Rotationssets und Sets für gemischte Medien {#image-sets-spins-sets-mixed-media-sets}

Bildsets, Rotationssets und Sets für gemischte Medien sind verfügbar, wenn Dynamic Media aktiviert ist.

![chlimage_1-359](assets/chlimage_1-359.png)

### PTIFF-Ausgabedarstellungen {#ptiff-renditions}

Assets mit aktivierter Dynamic Media-Funktion umfassen `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### Änderung der Asset-Ansichten {#asset-views-change}

Wenn Dynamic Media aktiviert ist, können Sie die Ansicht durch Klicken auf die Schaltflächen `+` und `-` vergrößern und verkleinern. Sie können durch Klicken oder Tippen auch einen bestimmten Bereich vergrößern. Außerdem können Sie die Originalansicht wiederherstellen und das Bild durch Klicken auf die diagonalen Pfeile im Vollbildmodus anzeigen. Eine Ansicht mit aktivierter Dynamic Media-Funktion sieht wie folgt aus:

![chlimage_1-361](assets/chlimage_1-361.png)

Wenn Dynamic Media deaktiviert ist, können Sie die Ansicht vergrößern und verkleinern und die Originalgröße wiederherstellen:

![chlimage_1-362](assets/chlimage_1-362.png)
