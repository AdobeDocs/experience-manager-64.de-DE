---
title: Einrichten von Dynamic Media
seo-title: Setting Up Dynamic Media
description: Zum Einrichten von Dynamic Media müssen Sie Dynamic Media konfigurieren und Bild- sowie Viewer-Vorgaben verwalten.
seo-description: To set up dynamic media, you need to configure dynamic media and manage image and viewer presets
uuid: bcd1f9ab-4201-4222-9e4a-ba82b3c7cd6c
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 36a4a4e7-8bb2-4853-b335-cf9148be410c
exl-id: dd43de7b-8556-4e3f-9d90-14f0f5bd13e7
feature: Configuration
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 57%

---

# Einrichten von Dynamic Media  {#setting-up-dynamic-media}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit [Dynamic Media](https://www.adobe.com/de/solutions/web-experience-management/dynamic-media.html) können Sie Assets durch die On-Demand-Bereitstellung visuell ansprechender Merchandising- und Marketing-Assets verwalten, die automatisch für das Internet sowie mobile und Social-Media-Websites skaliert werden. Über ein Set von Master-Assets generiert und liefert Dynamic Media durch ein globales, skalierbares, leistungsoptimiertes Netzwerk mehrere Varianten vielfältiger Inhalte in Echtzeit.

>[!NOTE]
>
>In dieser Dokumentation werden Dynamic Media-Funktionen beschrieben, die direkt in AEM integriert sind. Wenn Sie Dynamic Media Classic in AEM verwenden, lesen Sie [Dokumentation zur Dynamic Media Classic-Integration](/help/sites-administering/scene7.md).
>
>Siehe [Szenario für die doppelte Verwendung](/help/sites-administering/scene7.md#dual-use-scenario) für Fälle, in denen Sie möglicherweise AEM verwenden möchten, die in Dynamic Media Classic gemeinsam mit Dynamic Media integriert sind.

Wenn Sie dynamische Medien verwalten, sind die folgenden Themen von Interesse:

* [Konfigurieren des Dynamic Media-Scene7-Modus](config-dms7.md) - Verwenden Sie diese Konfiguration, wenn Sie ein neuer Dynamic Media-Kunde sind.
* [Konfigurieren des Dynamic Media-Hybridmodus](config-dynamic.md) - Verwenden Sie diese Konfiguration, wenn Sie bereits Dynamic Media-Kunde sind und AEM aktualisieren.
* [Verwalten von Bildvorgaben](managing-image-presets.md)
* [Verwalten von Viewer-Vorgaben](managing-viewer-presets.md)
* [Fehlerbehebung bei Dynamic Media – Scene7-Modus](troubleshoot-dms7.md)

Weitere Informationen finden Sie in den folgenden Themen:

* [Videokodierung und Videoprofile](video-profiles.md)
* [Bildprofile](image-profiles.md)

>[!NOTE]
>
>**Beachten Sie Folgendes, wenn Sie ein Upgrade durchführen:**
>
>* Sobald Sie AEM eingerichtet haben und verwenden, ist Dynamic Media für jedes Asset, das Sie hochladen, automatisch aktiviert (sofern nicht ausdrücklich vom Systemadministrator deaktiviert). Wenn Sie sich auf einer aktualisierten AEM-Instanz befinden und Dynamic Media noch nicht verwendet haben, müssen Sie Assets ggf. erneut verarbeiten, um Dynamic Media für die Assets verwenden zu können.

