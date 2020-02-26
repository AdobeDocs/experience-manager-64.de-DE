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
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f

---


# Arbeiten mit Adobe Dimension-Assets {#working-with-adobe-dimension-assets}

Das AEM 3D Feature Pack unterstützt Adobe Dimension-Assets (`.dn` Dateien) in AEM Assets, AEM Sites und AEM Screens.

Ein neuer 3D-Viewer, der auf dem offenen Standard glTF basiert, bietet Funktionen zum Anzeigen von Vorschau und Sites und Bildschirmen für Adobe Dimension-Assets.

## Informationen zum Cloud-basierten Konvertierungsdienst {#about-the-cloud-based-conversion-service}

Wenn ein Dimension-Asset in AEM hochgeladen wird, wird eine Kopie der Datei an einen von Adobe verwalteten Cloud-basierten Dienst weitergeleitet, der in Amazon AWS gehostet wird. Dieser Dienst konvertiert vom proprietären Dimension-Dateiformat von Adobe in das offene glTF-Standardformat. Das konvertierte 3D-Modell wird als binärer glTF (`.glb`) verpackt. AEM speichert das konvertierte Modell mit dem primären Dimension-Asset als Darstellung.

Sie können das `.glb` Konvertierungsformat auf zwei Arten konfigurieren (Anweisungen finden Sie unter [Installieren und Konfigurieren von AEM 3D](install-config-3d.md) ):

* Schließen Sie Adobe-spezifische Erweiterungen ein, um die visuelle Qualität zu maximieren, wenn Sie mit dem Adobe glTF-Viewer Dimensionselemente in AEM Assets, AEM Sites oder AEM Screens anzeigen. Dadurch sind die `.glb` Darstellungen mit den meisten Drittanbieteranwendungen nicht kompatibel.
* Schließen Sie Adobe-spezifische Erweiterungen aus, um die Kompatibilität der `.glb` Darstellung mit Drittanbieteranwendungen zu erreichen. Dadurch wird die visuelle Qualität bei der Anzeige in AEM Assets, AEM Sites oder AEM Screens (z. B. ohne IBL-Beleuchtung) eingeschränkt, um die Qualität typischer Drittanbieteranwendungen zu simulieren.

Die Übertragung der Dimensions-/glTF-Dateien auf oder von Amazon AWS und deren temporärer Speicher in AWS sind vollständig gesichert. Diese Dateien bestehen in Amazon AWS nur über einen minimalen Zeitraum. Normalerweise höchstens wenige Minuten während des normalen Betriebs.

Um die Unterstützung für Dimension-Assets zu aktivieren, müssen Sie beim Zugriff auf den Konvertierungsdienst Anmeldeinformationen von Adobe erhalten. Siehe [Installieren und Konfigurieren von AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Wenn Sie die angegebenen Anmeldeinformationen installieren und verwenden, verstehen Sie, dass Ihre Adobe Dimension 3D-Assets an den von Adobe verwalteten, Cloud-basierten Konvertierungsdienst übertragen und von diesem verarbeitet werden, der in Amazon AWS gehostet wird.

### Anzeigen auf AEM Assets {#viewing-on-aem-assets}

Das AEM 3D Feature Pack enthält einen neuen Viewer, der auf dem offenen glTF-Standard basiert, der zum Anzeigen von Adobe Dimension-Assets verwendet wird. Dieser Viewer wird automatisch ausgewählt, wenn eine Dimensionsdatei oder eine komprimierte glTF in der Detailansicht von AEM Assets oder mit der 3D-Komponente in AEM Sites geöffnet wird.

Beachten Sie, dass sich die Benutzeroberfläche des glTF-Viewers etwas von dem Standard-3D-Viewer unterscheidet, der für alle anderen 3D-Asset-Typen verwendet wird.

#### See also the following: {#see-also-the-following}

* [AEM 3D-Versionshinweise](/help/release-notes/aem3d-release-notes.md) zu Einschränkungen und Einschränkungen für Dn-Assets und den glTF-Viewer.
* [Arbeiten mit der Komponente](using-the-3d-sites-component.md) &quot;3D-Sites&quot;für für Adobe Dimension-Assets spezifische Komponenteneigenschaften
* [Installieren und Konfigurieren von AEM 3D](install-config-3d.md) zum Konfigurieren des Cloud-basierten Konvertierungsdiensts.

