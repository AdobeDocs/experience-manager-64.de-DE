---
title: Verwalten von Metadaten Ihrer digitalen Assets
description: In diesem Abschnitt erfahren Sie alles über die Arten von Metadaten und darüber wie Sie mit AEM Assets Metadaten einfacher verwalten, kategorisieren und organisieren können. Sie können mit den Assets beliebige Metadaten speichern und verwalten. Daher ermöglicht AEM Assets die automatische Organisation und Verarbeitung von Assets basierend auf ihren Metadaten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a57c8d08a9c4063b27eac240eb939b287fecc755

---


# Verwalten von Metadaten Ihrer digitalen Assets {#managing-metadata-for-digital-assets}

Adobe Experience Manager (AEM) speichert Metadaten für jedes Asset. So können Assets einfacher kategorisiert und organisiert und spezielle Assets leichter von Benutzern gefunden werden. Metadaten können aus in AEM Assets hochgeladenen Dateien extrahiert werden. Damit lässt sich die Metadatenverwaltung in den kreativen Workflow integrieren. Sie können mit den Assets beliebige Metadaten speichern und verwalten. Daher ermöglicht AEM Assets die automatische Organisation und Verarbeitung von Assets basierend auf ihren Metadaten.

* [XMP-Metadaten](xmp.md)
* [Anleitung zum Bearbeiten oder Hinzufügen von Metadaten](meta-edit.md)
* [Metadaten-Schemareferenz](meta-ref.md)

## Die Bedeutung von Metadaten {#why-we-need-metadata}

Metadaten sind Informationen über Daten. In diesem Zusammenhang beziehen sich Daten auf das Asset, mit dem Sie arbeiten (z. B. ein Bild). Metadaten sind wichtig, da Benutzer mit ihnen Assets effizienter verwalten können.

Metadaten stellen die Sammlung aller für dieses Bild verfügbaren Daten dar, die nicht unbedingt im Bild selbst enthalten sind, wie:

* der Name des Assets
* Datum und Uhrzeit der letzten Bearbeitung
* die Größe des Bildes bei Speicherung im Repository
* der Name des Ordners, der das Bild enthält
* die zugehörigen Bilder oder angewendeten Tags

Dies sind die grundlegenden Metadateneigenschaften, die von AEM für Assets verwaltet werden können. So können Benutzer beispielsweise alle Assets sortiert nach dem Datum der letzten Änderung anzeigen. Das ist nützlich, wenn sie ermitteln möchten, welche Assets zuletzt dem Repository hinzugefügt wurden.

Sie können digitalen Assets auch Daten auf höherer Ebene hinzufügen – darunter:

* der Typ des Assets (Bild, Video, Audioclip oder Dokument)
* der Eigentümer des Assets
* der Titel des Assets
* die Beschreibung des Assets
* die Tags, die einem Asset zugewiesen wurden

Mit mehr Metadaten können Sie Assets genauer einteilen. Außerdem erweisen sie sich als nützlich, wenn die Menge digitaler Daten ansteigt. Eine Einzelperson kann zwar eine Liste mit einigen Hundert Dateien einfach anhand ihrer Dateinamen verwalten, aber dieser Ansatz ist nicht ausreichend, wenn die Anzahl der beteiligten Personen und verwalteten Assets steigt.

Wenn Metadaten Assets hinzugefügt werden, steigt auch der Wert der Assets, da diese dadurch

* einfacher zugänglich werden: Sie können viel einfacher gefunden werden.
* einfacher zu verwalten werden: Sie können Assets mit denselben Eigenschaften einfacher finden und ändern.
* komplexer werden: Je mehr Metadaten Sie einem Asset hinzugefügt haben, desto wichtiger wird die Verwaltung der Metadaten.

Aus diesen Gründen erhalten Sie mit AEM-Assets die richtigen Mittel, Metadaten für digitale Assets zu erstellen, zu verwalten und auszutauschen.

## Metadatentypen {#types-of-metadata}

Es gibt zwei grundlegende Metadatentypen:

* Technische Metadaten
* Beschreibende Metadaten

### Technische Metadaten {#technical-metadata}

Technische Metadaten eignen sich für Softwareanwendungen, die mit digitalen Assets arbeiten und nicht manuell gepflegt werden sollten. Technische Metadaten können automatisch von AEM-Assets und anderer Software bestimmt werden und können sich ändern, wenn das Asset bearbeitet wird. Welche technischen Metadaten für ein Asset verfügbar sind, hängt größtenteils vom Dateityp des Assets ab. Beispiele für technische Metadaten:

* Größe einer Datei
* Abmessungen (Höhe und Breite) eines Bildes
* Bitrate einer Audio- oder Videodatei
* Auflösung (Detailebene) eines Bildes

### Beschreibende Metadaten {#descriptive-metadata}

Beschreibende Metadaten sind solche, die sich auf die Anwendungsdomäne beziehen – etwa das Unternehmen, aus dem ein Asset stammt. Beschreibende Metadaten können nicht automatisch bestimmt werden. Sie müssen manuell oder halbautomatisch erstellt werden. Beispiel: Eine GPS-fähige Kamera kann den Längen- und Breitengrad, an dem ein Bild aufgenommen wurde, automatisch verfolgen und diese Informationen den Metadaten des Bildes hinzufügen.

Da der manuelle Aufwand für die Erstellung beschreibender Metadaten sehr kostspielig ist, wurden Standards aufgestellt, um den Austausch von Metadaten über Softwaresysteme und Organisationen hinweg zu erleichtern.

AEM-Assets unterstützt alle relevanten Standards für die Metadatenverwaltung.

Aufgrund der Wichtigkeit von Metadaten und des hohen manuellen Arbeitsaufwands für ihre Erstellung wurden Standards aufgestellt, die den Austausch erleichtern.

## Encoding standards {#encoding-standards}

Metadaten können auf mehrere verschiedene Arten in Dateien eingebettet werden. Dazu werden die folgenden Kodierungsstandards unterstützt:

* XMP: Damit speichert AEM-Assets die extrahierten Metadaten im Repository.
* ID3: für Audio- und Videodateien
* EXIF: für Bilddateien
* Andere/Legacy: aus Microsoft Word, PowerPoint, Excel usw.

### XMP {#xmp}

XMP bedeutet Extensible Metadata Platform und ist der Metadatenstandard, der von AEM Assets für das gesamte Metadatenmanagement verwendet wird. XMP bietet nicht nur eine universelle Metadaten-Kodierung, die in alle Dateiformate eingebettet werden kann, sondern bietet auch ein Rich-Content-Modell und wird von Adobe und anderen Unternehmen unterstützt, sodass Benutzer von XMP in Kombination mit AEM Assets eine leistungsstarke Plattform haben, auf der sie aufbauen können.

### ID3 {#id}

In diesen ID3-Tags gespeicherte Daten werden angezeigt, wenn Sie eine digitale Audiodatei auf dem Computer oder einem tragbaren MP3-Player abspielen.

ID3-Tags wurden für das MP3-Dateiformat entwickelt. Weitere Informationen zu Formaten:

* ID3-Tags funktionieren in MP3- und MP3pro-Dateien.
* WAV weist keine Tags auf.
* WMA verfügt über proprietäre Tags, die keine Open Source-Implementierung zulassen.
* Ogg Vorbis nutzt Xiph-Kommentare, die in den Ogg-Container eingebettet sind.
* AAC verwendet ein proprietäres Tagging-Format.

### EXIF {#exif}

EXIF steht für „Exchangeable Image File Format“ (austauschbares Bilddateiformat) und ist das in der digitalen Fotografie am häufigsten verwendete Metadatenformat. Es ermöglicht die Einbettung von festen Begriffen für Metadateneigenschaften in mehrere Dateiformate wie

* JPEG
* TIFF
* RIFF
* WAV

Eine wesentliche Einschränkung bei EXIF ist der Umstand, dass das Format nicht von anderen gängigen Bilddateiformaten wie BMP, GIF oder PNG unterstützt wird.

EXIF speichert Metadaten als Paare aus dem Metadatennamen und dem Metadatenwert. Die Name-Wert-Paare für Metadaten werden auch als Tags bezeichnet (nicht zu verwechseln mit dem Tagging in AEM).

Da EXIF automatisch von modernen Digitalkameras erstellt und in moderner Grafiksoftware unterstützt wird, kann es als der kleinste gemeinsame Nenner für die Metadatenverwaltung betrachtet werden.

Die meisten der von EXIF definierten Metadatenfelder sind besonders technisch und eignen sich nur bedingt für die Verwaltung beschreibender Metadaten. For this reason, AEM Assets offers mapping of EXIF properties into [common metadata schemata](metadata-schemas.md) and into [XMP](xmp-writeback.md), the powerful metadata format AEM Assets uses for metadata management.

### Other metadata {#other-metadata}

Andere Metadaten, die aus Dateien eingebettet werden können, sind Microsoft Word, PowerPoint, Excel usw.

## Metadata schemata {#metadata-schemata}

Metadatenschemata sind vordefinierte Sets aus Metadaten-Eigenschaftsdefinitionen, die in einer Vielzahl von Anwendungen eingesetzt werden können. Eigenschaften sind stets mit einem Asset verknüpft. Das heißt, die Eigenschaften beziehen sich auf die Ressource.

Sie können Ihre eigenen Metadatenschemata entwerfen, wenn keine vorhanden sind, die Ihren Anforderungen entsprechen (achten Sie aber darauf, keine bereits vorhandenen Schemata zu duplizieren). Innerhalb eines Unternehmens kann die organisationsübergreifende Freigabe von Metadaten durch eine Trennung der Schemata erleichtert werden.

AEM stellt eine standardmäßige Liste der am häufigsten verwendeten Metadatenschemata bereit, sodass Sie Ihre Metadatenstrategie schnell implementieren und die benötigten Metadateneigenschaften aus einem bereits definierten Schema auswählen können.

Im folgenden Abschnitt werden die unterstützten Metadatenschemata aufgelistet.

### Standard metadata {#standard-metadata}

* dc – Dublin Core: Das wichtigste und am häufigsten verwendete Metadatenset
* DICOM – Digital Imaging and Communications in Medicine
* Iptc4xmpCore &amp; iptc4xmpExt - International Press Communications Standard - viele themenspezifische Metadaten
* rdf – Resource Description Framework: Für generische semantische Webmetadaten
* XMP – Extensible Metadata Platform
* xmpBJ – Einfaches Auftrags-Ticketing

### Application-specific metadata {#application-specific-metadata}

>[!NOTE]
>
>Anwendungsspezifische Metadaten umfassen technische und beschreibende Metadaten. Diese Metadaten können unter Umständen nicht von anderen Anwendungen verwendet werden. Beispiel: Wenn Sie ein Asset mit Adobe Photoshop-Metadaten bearbeiten und eine andere Bild-Render-Anwendung versucht, auf die Metadaten zuzugreifen, ist dies eventuell nicht möglich. Wenn Ihre Assets zahlreiche anwendungsspezifische Metadaten enthalten, können Sie einen Workflow-Schritt erstellen, der die anwendungsspezifische Eigenschaft in eine Standardeigenschaft ändert.

* acdsee - metadata managed by the ACDSee program [www.acdsee.com/](https://www.acdsee.com/)
* album: Adobe Photoshop-Album
* cq - wird von AEM Assets verwendet
* dam: Von AEM-Assets verwendet
* dex: Optima SC Description Explorer
* crs: Adobe Photoshop Camera Raw
* lr: Adobe Lightroom
* mediapro: IView MediaPro
* MicrosoftPhoto und MP: Microsoft Photo
* pdf und pdfx
* photoshop und psAux: Adobe Photoshop

### Digital Rights Management metadata {#digital-rights-management-metadata}

* cc: Creative Commons
* xmpRights
* plus - Picture Licensing Universal System - https://www.useplus.com/
* Prism - https://www.idealliance.org/prism-metadata für Veröffentlichungsanforderungen für Standard-Metadaten
* prl: Prism Rights Language
* pur: Prism Usage Rights
* xmpPlus: Integration von PLUS in XMP

### Photography-specific metadata {#photography-specific-metadata}

* exif: zahlreiche technische Informationen von der Kamera, einschließlich GPS-Position
* crs: Photoshop Camera Raw
* Iptc4xmpCore und iptc4xmpExt
* TIFF: Bildmetadaten (nicht nur für TIFF-Bilder)

### Print-specific metadata {#print-specific-metadata}

* pdf und pdfx - Adobe PDF- und Drittanbieteranwendungen
* prism - [www.prismstandard.org](https://www.prismstandard.org) Publishing Requirements for Industry Standard Metadata
* XMP
* xmpPG: XMP für paginierten Text

### Multimedia-specific metadata {#multimedia-specific-metadata}

* xmpDM: Dynamic Media
* xmpMM: Medien-Management

## Metadata-driven workflows {#metadata-driven-workflows}

Das Erstellen von metadatenbasierten Workflows hilft Ihnen, einige Prozesse zu automatisieren, was die Effizienz verbessert. In einem metadatengesteuerten Workflow liest das Workflow-Managementsystem den Workflow und führt anschließend einige vordefinierte Aktionen aus. Im Folgenden finden Sie einige Beispiele für den Einsatz metadatengesteuerter Workflows:

* Der Workflow kann prüfen, ob ein Bild einen Titel aufweist. Falls nicht, wird ein bestimmter Benutzer darüber benachrichtigt, dass er einen Titel hinzufügen muss.
* Der Workflow kann prüfen, ob ein Copyright-Hinweis für ein Asset dessen Verteilung zulässt. Falls ja, wird das Asset an einen Server gesendet. Andernfalls wird das Asset an einen anderen Server gesendet.
* Ein Workflow kann Assets ohne vordefinierte, obligatorische Metadaten oder mit *ungültigen* Metadaten suchen.
