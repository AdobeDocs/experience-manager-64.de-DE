---
title: Arbeiten mit Adobe Dimension-Assets
description: Arbeiten mit Adobe Dimension-Assets in AEM 3D
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: be8f6361-607d-4529-aef0-e8978dfd04b4
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---

# Arbeiten mit Adobe Dimension-Assets {#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>Das AEM 3D Feature Pack in AEM 6.4 wird nicht mehr unterstützt. Adobe empfiehlt, die Funktion für 3D-Elemente in [AEM als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) oder [AEM 6.5.3 oder höher zu verwenden.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) beim Arbeiten mit Adobe Dimension-Assets.

Das AEM 3D Feature Pack unterstützt Adobe Dimension-Assets (`.dn`-Dateien) in AEM Assets, AEM Sites und AEM Screens.

Ein neuer 3D-Viewer, der auf dem Open-Standard glTF basiert, bietet Vorschau- und Sites- und Screens-Anzeigefunktionen für Adobe Dimension-Assets.

## Informationen zum Cloud-basierten Konvertierungsdienst {#about-the-cloud-based-conversion-service}

Wenn ein Dimensionen-Asset in AEM hochgeladen wird, wird eine Kopie der Datei an einen Cloud-basierten Dienst weitergeleitet, der in Amazon AWS gehostet wird. Dieser Dienst konvertiert vom Dateiformat der Adobe-proprietären Dimension in das offene Standardformat glTF. Das konvertierte 3D-Modell wird als binärer glTF (`.glb`) verpackt. AEM speichert das konvertierte Modell mit dem Asset der primären Dimension als Darstellung.

Sie können das Konvertierungsformat `.glb` auf zwei Arten konfigurieren (Anweisungen finden Sie unter Installieren und Konfigurieren von AEM 3D](install-config-3d.md)):[

* Schließen Sie Adobe-spezifische Erweiterungen ein, um die Visualisierungsqualität zu maximieren, wenn Sie den glTF-Viewer für die Adobe verwenden, um Assets für die Dimension in AEM Assets, AEM Sites oder AEM Screens Ansicht. Dadurch sind die Darstellungen von `.glb` mit den meisten Drittanbieteranwendungen inkompatibel.
* Schließen Sie Adoben-spezifische Erweiterungen aus, um die Kompatibilität der Darstellung `.glb` mit Drittanbieteranwendungen zu erreichen. Dies schränkt die visuelle Qualität bei der Anzeige in AEM Assets, AEM Sites oder AEM Screens ein (z. B. keine IBL-Beleuchtung), um die Qualität typischer Drittanbieteranwendungen zu simulieren.

Die Übertragung der Dimension-/glTF-Dateien von oder auf Amazon AWS und ihre temporäre Datenspeicherung in AWS sind vollständig gesichert. Diese Dateien bestehen in Amazon AWS nur über einen minimalen Zeitraum. Normalerweise höchstens wenige Minuten während des normalen Betriebs.

Um die Unterstützung für Dimension-Assets zu aktivieren, müssen Sie über die Adobe Anmeldeinformationen für den Zugriff auf den Konvertierungsdienst erhalten. Siehe [Installieren und Konfigurieren von AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Wenn Sie die angegebenen Anmeldeinformationen installieren und verwenden, verstehen Sie, dass Ihre Adobe Dimension 3D-Assets an den in Amazon AWS gehosteten, Cloud-basierten Konvertierungsdienst übertragen und von diesem verarbeitet werden.

### Anzeigen auf AEM Assets {#viewing-on-aem-assets}

Das AEM 3D Feature Pack enthält einen neuen Viewer, der auf dem offenen glTF-Standard basiert, der zur Ansicht von Adobe Dimension-Assets verwendet wird. Dieser Viewer wird automatisch ausgewählt, wenn eine Dimension-Datei oder eine komprimierte glTF-Datei in der Detail-Ansicht in AEM Assets oder mit der 3D-Komponente in AEM Sites geöffnet wird.

Beachten Sie, dass sich die Benutzeroberfläche des glTF-Viewers etwas von dem Standard-3D-Viewer unterscheidet, der für alle anderen 3D-Asset-Typen verwendet wird.

#### Siehe auch: {#see-also-the-following}

* [AEM 3D-Version ](/help/release-notes/aem3d-release-notes.md) enthält Einschränkungen und Einschränkungen für Dn-Assets und den glTF-Viewer.
* [Arbeiten mit der ](using-the-3d-sites-component.md) Komponente &quot;3D-Sites&quot;für Komponenteneigenschaften, die für Adobe Dimension-Assets spezifisch sind.
* [Installieren und Konfigurieren AEM 3](install-config-3d.md) DPS zum Konfigurieren des Cloud-basierten Konvertierungsdiensts.
