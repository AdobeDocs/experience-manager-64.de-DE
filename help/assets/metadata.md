---
title: Verwalten von Metadaten Ihrer digitalen Assets
description: Erfahren Sie mehr über die Metadatentypen und wie Sie mit Adobe Experience Manager Assets Metadaten für Assets verwalten können, um die Kategorisierung und Organisation von Assets zu vereinfachen. Mit Adobe Experience Manager Assets können Sie beliebige Metadaten mit Ihren Assets behalten und verwalten und Assets automatisch basierend auf ihren Metadaten organisieren und verarbeiten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5ef4c4e42165819191c6e3810c36183110f3f34a

---


# Verwalten von Metadaten Ihrer digitalen Assets {#managing-metadata-for-digital-assets}

Adobe Experience Manager Assets speichert Metadaten für jedes Asset. Dies erleichtert die Kategorisierung und Organisation von Assets und hilft Menschen, die nach einem bestimmten Asset suchen. Mit der Möglichkeit, Metadaten aus Dateien zu extrahieren, die in Experience Manager Assets hochgeladen wurden, kann das Metadaten-Management in den kreativen Workflow integriert werden. Mit Experience Manager können Sie Metadaten mit Ihren Assets verwalten und verwalten. So können Sie Assets automatisch basierend auf den Metadaten organisieren und verarbeiten.

* [XMP-Metadaten](xmp.md)
* [Anleitung zum Bearbeiten oder Hinzufügen von Metadaten](meta-edit.md)
* [Metadaten-Schemareferenz](meta-ref.md)

## Die Bedeutung von Metadaten {#why-we-need-metadata}

Metadaten sind Informationen über Daten. In dieser Hinsicht beziehen sich Daten auf Ihr digitales Asset, z. B. ein Bild. Metadaten sind für eine effiziente Asset-Verwaltung von entscheidender Bedeutung.

Metadaten sind alle für ein Asset verfügbaren Daten, die jedoch nicht unbedingt in diesem Bild enthalten sind. Beispiele für Metadaten:

* Name des Assets.
* Zeitpunkt und Datum der letzten Änderung.
* Größe des Assets, wie es im Repository gespeichert wurde.
* Name des Ordners, in dem er enthalten ist.
* Zugehörige Assets oder angewendete Tags.

Dies sind die grundlegenden Metadateneigenschaften, die Experience Manager für Assets verwalten kann. Dadurch können Benutzer alle Assets anzeigen, die beispielsweise nach ihrem letzten Änderungsdatum geordnet sind. Dies ist nützlich, wenn Sie herausfinden möchten, welche Assets dem Repository kürzlich hinzugefügt wurden.

Sie können digitalen Assets auch Daten auf höherer Ebene hinzufügen – darunter:

* Asset-Typ (ist es ein Bild, ein Video, ein Audioclip oder ein Dokument?)
* Eigentümer des Assets.
* Titel des Assets.
* Beschreibung des Assets.
* Tags, die einem Asset zugewiesen sind.

Mit mehr Metadaten können Sie Assets genauer einteilen. Außerdem erweisen sie sich als nützlich, wenn die Menge digitaler Daten ansteigt. Es ist möglich, einige hundert Dateien zu verwalten, die nur auf den Dateinamen basieren. Dieser Ansatz ist jedoch nicht skalierbar und fällt schnell unter, wenn die Zahl der beteiligten Personen und die Zahl der verwalteten Assets steigt.

Wenn Metadaten Assets hinzugefügt werden, steigt auch der Wert der Assets, da diese dadurch,

* einfacher zugänglich wird: Es kann viel leichter gefunden werden.
* einfacher zu verwalten wird: Sie können Assets mit denselben Eigenschaften einfacher finden und ändern.
* komplexer wird: Je mehr Metadaten Sie einem Asset hinzugefügt haben, desto wichtiger wird die Verwaltung der Metadaten.

Aus diesen Gründen bietet Experience Manager Assets die richtigen Möglichkeiten zum Erstellen, Verwalten und Austauschen von Metadaten für Ihre digitalen Assets.

## Metadatentypen {#types-of-metadata}

Die beiden grundlegenden Metadatentypen sind technische Metadaten und beschreibende Metadaten.

Technische Metadaten eignen sich für Softwareanwendungen, die mit digitalen Assets arbeiten und nicht manuell gepflegt werden sollten. Experience Manager Assets und andere Software bestimmen automatisch technische Metadaten und die Metadaten können sich ändern, wenn das Asset geändert wird. Welche technischen Metadaten für ein Asset verfügbar sind, hängt größtenteils vom Dateityp des Assets ab. Beispiele für technische Metadaten:

* Dateigröße
* Abmessungen (Höhe und Breite) eines Bildes
* Bitrate einer Audio- oder Videodatei
* Auflösung (Detailstufe) eines Bildes

Beschreibende Metadaten sind solche, die sich auf die Anwendungsdomäne beziehen – etwa das Unternehmen, aus dem ein Asset stammt. Beschreibende Metadaten können nicht automatisch bestimmt werden. Es wird manuell oder halbautomatisch erstellt. Beispielsweise kann eine GPS-fähige Kamera automatisch den Breiten- und Längengrad verfolgen und Geotag für das Bild hinzufügen.

Da der manuelle Aufwand für die Erstellung beschreibender Metadaten sehr kostspielig ist, wurden Standards aufgestellt, um den Austausch von Metadaten über Softwaresysteme und Organisationen hinweg zu erleichtern.

Experience Manager Assets unterstützt alle relevanten Standards für das Metadatenmanagement.

Aufgrund der Wichtigkeit von Metadaten und des hohen manuellen Arbeitsaufwands für ihre Erstellung wurden Standards aufgestellt, die den Austausch erleichtern.

## Encoding standards {#encoding-standards}

Es gibt verschiedene Möglichkeiten, Metadaten in Dateien einzubetten. Dazu werden die folgenden Kodierungsstandards unterstützt:

* XMP: verwendet von Experience Manager Assets, um die extrahierten Metadaten im Repository zu speichern.
* ID3: für Audio- und Videodateien
* Exif: für Bilddateien.
* Andere/Legacy: aus Microsoft Word, PowerPoint, Excel usw.

### XMP {#xmp}

Die Extensible Metadata Platform (XMP) ist ein offener Standard, der von Experience Manager Assets für das gesamte Metadatenmanagement verwendet wird. Die standardmäßige Angebot-Metadaten-Kodierung, die in alle Dateiformate eingebettet werden kann. Adobe und andere Firmen unterstützen den XMP-Standard, da er ein Rich-Content-Modell bietet. Benutzer des XMP-Standards und von Experience Manager Assets verfügen über eine leistungsstarke Plattform, auf der sie aufbauen können. Weitere Informationen finden Sie unter [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

In diesen ID3-Tags gespeicherte Daten werden angezeigt, wenn Sie eine digitale Audiodatei auf dem Computer oder einem tragbaren MP3-Player abspielen.

ID3-Tags wurden für das MP3-Dateiformat entwickelt. Weitere Informationen zu Formaten:

* ID3-Tags funktionieren in MP3- und mp3PRO-Dateien.
* WAV weist keine Tags auf.
* WMA verfügt über proprietäre Tags, die keine Open-Source-Implementierung zulassen.
* Ogg Vorbis nutzt Xiph-Kommentare, die in den Ogg-Container eingebettet sind.
* AAC verwendet ein proprietäres Tagging-Format.

### Exif {#exif}

Das austauschbare Bilddateiformat (Exif) ist das beliebteste Metadatenformat für die Digitalfotografie. Es bietet eine Möglichkeit zum Einbetten eines festen Wortschatzes mit Metadateneigenschaften in viele Dateiformate wie JPEG, TIFF, RIFF und WAV. Exif speichert Metadaten als Paare eines Metadatennamens und eines Metadatenwerts. Diese Metadaten-Name-Wert-Paare werden auch als Tags bezeichnet, nicht zu verwechseln mit dem Tagging in Experience Manager. Da Exif automatisch von modernen Digitalkameras erstellt und durch moderne Grafiksoftware unterstützt wird, kann es als kleinster gemeinsamer Nenner für das Metadaten-Management angesehen werden.

Eine wichtige Einschränkung von Exif besteht darin, dass einige gängige Bilddateiformate wie BMP, GIF oder PNG diese nicht unterstützen.

Metadatenfelder, die normalerweise von Exif definiert werden, sind technischer Natur und werden nur in begrenztem Umfang für die Verwaltung beschreibender Metadaten verwendet. Aus diesem Grund werden in Experience Manager Assets Angebot-Zuordnungen von Exif-Eigenschaften zu [allgemeinen Metadatenschemata](metadata-schemas.md) und zu [XMP](xmp-writeback.md)erstellt.

### Other metadata {#other-metadata}

Andere Metadaten, die aus Dateien eingebettet werden können, sind Microsoft Word, PowerPoint, Excel usw.

## Metadata schemata {#metadata-schemata}

Metadaten-Schema sind vordefinierte Sätze von Metadateneigenschaftsdefinitionen, die in verschiedenen Anwendungen verwendet werden können. Eigenschaften sind stets mit einem Asset verknüpft. Das heißt, die Eigenschaften beziehen sich auf die Ressource.

Sie können auch eigene Metadaten-Schemata entwerfen, wenn keine vorhanden ist, die Ihren Anforderungen entsprechen. Vorhandene Informationen nicht Duplikat. Das Trennen von Schemata innerhalb eines Unternehmens erleichtert die Freigabe von Metadaten. Experience Manager bietet Ihnen eine standardmäßige Liste der beliebtesten Metadaten-Schemata. Die Liste hilft Ihnen, Ihre Metadatenstrategie zu starten und schnell die benötigten Metadateneigenschaften auszuwählen.

Die unterstützten Metadaten-Schemata sind unten aufgeführt.

### Standard metadata {#standard-metadata}

* dc – Dublin Core: Das wichtigste und am häufigsten verwendete Metadatenset.
* DICOM – Digital Imaging and Communications in Medicine.
* Iptc4xmpCore &amp; iptc4xmpExt - International Press Communications Standard - viele themenspezifische Metadaten.
* rdf – Resource Description Framework: Für generische semantische Webmetadaten.
* XMP – Extensible Metadata Platform.
* xmpBJ – Einfaches Auftrags-Ticketing.

### Application-specific metadata {#application-specific-metadata}

Die anwendungsspezifischen Metadaten enthalten technische und beschreibende Metadaten. Diese Metadaten können unter Umständen nicht von anderen Anwendungen verwendet werden. Wenn Sie z. B. ein Asset mit Adobe Fotoshop-Metadaten haben und eine andere Anwendung zum Rendern von Bildern versucht, auf die Metadaten zuzugreifen, ist es möglicherweise nicht möglich, auf die Metadaten zuzugreifen. Wenn Sie feststellen, dass Ihre Assets viele anwendungsspezifische Metadaten enthalten, können Sie einen Workflow-Schritt erstellen, der eine anwendungsspezifische Eigenschaft in eine Standardeigenschaft ändert.

* acdsee - metadata managed by the ACDSee program [www.acdsee.com/](https://www.acdsee.com/).
* album: Adobe Photoshop-Album.
* cq - wird von Experience Manager Assets verwendet.
* dam - wird von Experience Manager Assets verwendet.
* dex: Optima SC Description Explorer.
* crs: Adobe Photoshop Camera Raw.
* lr: Adobe Lightroom.
* mediapro: IView MediaPro.
* MicrosoftPhoto und MP: Microsoft Photo.
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

Das Erstellen von durch Metadaten angetriebenen Workflows hilft Ihnen, einige Prozesse zu automatisieren, was die Effizienz verbessert. In einem metadatengesteuerten Workflow liest das Workflow-Managementsystem den Workflow und führt anschließend einige vordefinierte Aktionen aus. Im Folgenden finden Sie einige Beispiele für den Einsatz metadatengesteuerter Workflows:

* Der Workflow kann prüfen, ob ein Bild einen Titel aufweist. Falls nicht, wird ein bestimmter Benutzer darüber benachrichtigt, dass er einen Titel hinzufügen muss.
* Der Workflow kann prüfen, ob ein Copyright-Hinweis für ein Asset dessen Verteilung zulässt. Falls ja, wird das Asset an einen Server gesendet. Andernfalls wird das Asset an einen anderen Server gesendet.
* Ein Workflow kann Assets ohne vordefinierte, obligatorische Metadaten oder mit *ungültigen* Metadaten suchen.
