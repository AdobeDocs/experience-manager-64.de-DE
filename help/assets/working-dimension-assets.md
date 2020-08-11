---
title: Arbeiten mit Adobe Dimension-Assets
seo-title: Arbeiten mit Adobe Dimension-Assets
description: Arbeiten mit Adobe Dimension-Assets in AEM 3D
seo-description: Arbeiten mit Adobe Dimension-Assets in AEM 3D
uuid: 476e6758-b3a1-42ba-a18d-bfc407c6a72e
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 4a601c2a-4ea1-4308-8ae8-704155f63c21
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 1%

---


# Arbeiten mit Adobe Dimension-Assets {#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>Das AEM 3D Feature Pack in AEM 6.4 wird nicht mehr unterstützt. Adobe empfiehlt, die Funktion für 3D-Elemente in [AEM als Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) oder [AEM 6.5.3 oder höher zu verwenden.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html) beim Arbeiten mit Adobe Dimension-Assets.

Das AEM 3D Feature Pack unterstützt Adobe Dimension-Assets (`.dn` Dateien) in AEM Assets, AEM Sites und AEM Screens.

Ein neuer 3D-Viewer, der auf dem Open-Standard glTF basiert, bietet Vorschau- und Sites- und Screens-Anzeigefunktionen für Adobe Dimension-Assets.

## Informationen zum Cloud-basierten Konvertierungsdienst {#about-the-cloud-based-conversion-service}

Wenn ein Dimensionen-Asset in AEM hochgeladen wird, wird eine Kopie der Datei an einen Cloud-basierten Dienst weitergeleitet, der in Amazon AWS gehostet wird. Dieser Dienst konvertiert vom Dateiformat der Adobe-proprietären Dimension in das offene Standardformat glTF. Das konvertierte 3D-Modell wird als binärer glTF (`.glb`) verpackt. AEM speichert das konvertierte Modell mit dem Asset der primären Dimension als Darstellung.

Sie können das `.glb` Konvertierungsformat auf zwei Arten konfigurieren (Anweisungen finden Sie unter [Installieren und Konfigurieren AEM 3D](install-config-3d.md) ):

* Schließen Sie Adobe-spezifische Erweiterungen ein, um die Visualisierungsqualität zu maximieren, wenn Sie den glTF-Viewer für die Adobe verwenden, um Assets für die Dimension in AEM Assets, AEM Sites oder AEM Screens Ansicht. This makes the `.glb` renditions incompatible with most third-party applications.
* Exclude Adobe-specific extensions to achieve compatibility of the `.glb` rendition with third-party applications. Dies schränkt die visuelle Qualität bei der Anzeige in AEM Assets, AEM Sites oder AEM Screens ein (z. B. keine IBL-Beleuchtung), um die Qualität typischer Drittanbieteranwendungen zu simulieren.

Die Übertragung der Dimension-/glTF-Dateien von oder auf Amazon AWS und ihre temporäre Datenspeicherung in AWS sind vollständig gesichert. Diese Dateien bestehen in Amazon AWS nur über einen minimalen Zeitraum. Normalerweise höchstens wenige Minuten während des normalen Betriebs.

To enable support for Dimension assets, you must obtain credentials from Adobe for accessing the conversion service. Siehe [Installieren und Konfigurieren von AEM 3D](install-config-3d.md).

>[!NOTE]
>
>If you install and use the provided credentials, you understand and agree that your Adobe Dimension 3D assets will be transferred to--and processed by--the Adobe-managed, cloud-based conversion service hosted in Amazon AWS.

### Viewing on AEM Assets {#viewing-on-aem-assets}

The AEM 3D feature pack includes a new viewer based on the glTF open standard which is used to view Adobe Dimension assets. This viewer is selected automatically when opening a Dimension file or a zipped glTF into the Detail view in AEM Assets or with the 3D component in AEM Sites.

Beachten Sie, dass sich die Benutzeroberfläche des glTF-Viewers etwas von dem Standard-3D-Viewer unterscheidet, der für alle anderen 3D-Asset-Typen verwendet wird.

#### See also the following: {#see-also-the-following}

* [AEM 3D-Versionshinweise](/help/release-notes/aem3d-release-notes.md) zu Einschränkungen und Einschränkungen für Dn-Assets und den glTF-Viewer.
* [Arbeiten mit der Komponente](using-the-3d-sites-component.md) &quot;3D-Sites&quot;für für Adobe Dimension-Assets spezifische Komponenteneigenschaften.
* [Installieren und Konfigurieren AEM 3D](install-config-3d.md) zum Konfigurieren des Cloud-basierten Konvertierungsdiensts.

