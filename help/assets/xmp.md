---
title: XMP Metadaten
description: Erfahren Sie mehr über den XMP (Extensible Metadata Platform)-Metadatenstandard, der von [!DNL Experience Manager] Assets für die Metadatenverwaltung. XMP liefert ein Standardformat für die Erstellung, die Verarbeitung und den Austausch von Metadaten für eine Vielzahl an Programmen.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 32c4ca3d-2e9e-46a3-b4c7-70dcc50daaaa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 62%

---

# XMP-Metadaten {#xmp-metadata}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

XMP (Extensible Metadata Platform) ist der Metadatenstandard, der von [!DNL Experience Manager] Assets für die gesamte Metadatenverwaltung. XMP liefert ein Standardformat für die Erstellung, die Verarbeitung und den Austausch von Metadaten für eine Vielzahl an Programmen.

XMP bietet nicht nur universelle Metadatenkodierung, die in alle Dateiformate eingebettet werden kann, sondern auch ein [Rich-Content-Modell](xmp.md#xmp-core-concepts). Außerdem wird XMP [von Adobe](xmp.md#advantages-of-xmp) und anderen Unternehmen unterstützt, sodass Benutzer, die XMP in Kombination mit  Assets einsetzen, über eine leistungsstarke Plattform verfügen.[!DNL Experience Manager]

Die [XMP-Spezifikation](https://www.adobe.com/devnet/xmp.html) wird von Adobe zur Verfügung gestellt.

## Was ist XMP? {#what-is-xmp}

[!DNL Experience Manager] Assets unterstützt nativ die XMP - die Extensible Metadata Platform, die von Adobe geleitet wird. XMP ist ein Standard für die Verarbeitung und Speicherung von standardisierten und proprietären Metadaten in digitalen Assets. XMP ist als der gemeinsame Standard konzipiert, dank dem mehrere Programme effektiv mit Metadaten arbeiten können.

Produktionsexperten nutzen beispielsweise die integrierte XMP-Unterstützung innerhalb der Adobe-Programme, um Informationen über mehrere Dateiformate hinweg zu übergeben. Die [!DNL Experience Manager] Das Assets-Repository extrahiert die XMP-Metadaten, verwendet sie zur Verwaltung des Inhaltslebenszyklus und bietet die Möglichkeit, Automatisierungs-Workflows zu erstellen.

XMP standardisiert die Art, wie Metadaten definiert, erstellt und verarbeitet werden, indem ein Datenmodell, ein Speichermodell und Schemata bereitgestellt werden. Diese Grundlagen werden alle in diesem Abschnitt behandelt.

Alle Legacy-Metadaten aus EXIF, ID3 oder Microsoft Office werden automatisch in XMP übersetzt. Diese können erweitert werden, um kundenspezifische Metadatenschemata wie Produktkataloge zu unterstützen.

Metadaten in XMP bestehen aus einer Reihe von Eigenschaften. Diese Eigenschaften sind immer mit einer\
bestimmte als Ressource bezeichnete Stelle; Das heißt, die Eigenschaften beziehen sich auf die Ressource. Bei XMP ist die Ressource stets das Asset.

### Adobe {#adobe}

Adobe hat den XMP-Standard zunächst im Rahmen von Adobe Acrobat eingeführt. Mittlerweile ist der XMP-Standard weit verbreitet.

### XMP-Ökosystem {#xmp-ecosystem}

XMP definiert ein [Metadatenmodell](https://de.wikipedia.org/wiki/Metadaten), das mit jedem definierten Satz von Metadatenelementen verwendet werden kann. XMP definiert außerdem bestimmte [Schemata](https://de.wikipedia.org/wiki/Schemasprache_(XML)) für Standardeigenschaften, die für die Aufzeichnung des Verlaufs einer Ressource nützlich sind, während sie mehrere Verarbeitungsschritte durchläuft – von der Aufnahme über [Scannen](https://de.wikipedia.org/wiki/Scanner_(Datenerfassung)) oder Verfassen als Text und Bildbearbeitungsschritte (wie [Zuschneiden](https://de.wikipedia.org/wiki/Cropping_%28image%29) oder Farbkorrektur) bis hin zur Zusammensetzung in das endgültige Bild. XMP ermöglicht es jedem Softwareprogramm oder Gerät, eigene Informationen zu einer digitalen Ressource hinzuzufügen, die dann in der endgültigen digitalen Datei gespeichert werden kann.

XMP wird am häufigsten mit einer Untergruppe des [W3C](https://de.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://de.wikipedia.org/wiki/Resource_Description_Framework) (RDF) serialisiert und gespeichert, das wiederum in [XML](https://de.wikipedia.org/wiki/Extensible_Markup_Language) ausgedrückt wird.

## Vorteile von XMP {#advantages-of-xmp}

XMP bietet die folgenden Vorteile gegenüber anderen Kodierungsstandards und Schemata:

* XMP-basierte Metadaten sind sehr leistungsstark und fein granuliert.
* Mit XMP können Sie mehrere Werte für eine Eigenschaft festlegen.
* XMP verfügt über eine standardisierte Kodierung, mit der Sie mühelos Metadaten austauschen können.
* XMP ist erweiterbar. Sie können Ihren Assets zusätzliche Informationen hinzufügen.

### Erweiterbar {#extensible}

Das XMP-Standardformat ist erweiterbar, sodass Sie den XMP-Daten benutzerdefinierte Arten von Metadaten hinzufügen können. Bei EXIF ist dies dagegen nicht möglich. Die feste Liste der Eigenschaften kann nicht erweitert werden.

>[!NOTE]
>
>XMP lässt im Allgemeinen nicht zu, dass binäre Datentypen eingebettet werden. Um binäre Daten in XMP, z. B. Miniaturansichten, zu übertragen, müssen sie in einem XML-freundlichen Format wie Base64 kodiert werden.

## XMP Hauptkonzepte {#xmp-core-concepts}

In den folgenden Abschnitten werden die wesentlichen Grundlagen von XMP beschrieben, einschließlich Namespaces und Schemata, Eigenschaften und Werten sowie Sprachalternativen.

### Namespaces und Schemata {#namespaces-and-schemata}

Ein XMP-Schema ist ein Satz von Eigenschaftsnamen in einem gemeinsamen XML-Namespace, der Folgendes enthält:\
Datentyp und beschreibende Informationen. Ein XMP-Schema wird durch seinen XML-Namespace-URI identifiziert. Die Verwendung von Namespaces verhindert Konflikte zwischen Eigenschaften in verschiedenen Schemas, die denselben Namen, aber eine andere Bedeutung haben.

Beispiel: Die Eigenschaft **Creator** in zwei unabhängig voneinander entwickelten Schemata kann einerseits für die Person stehen, die das Asset erstellt hat, oder andererseits für das Programm, von dem das Asset erstellt wurde (z. B. Adobe Photoshop).

### Eigenschaften und Werte {#properties-and-values}

XMP kann Eigenschaften von einem oder mehreren der Schemata umfassen.

Viele Adobe-Programme verwenden beispielsweise Folgendes:

* Dublin Core-Schema: dc:title, dc:creator, dc:subject, dc:format, dc:rights
* XMP Basisschema: xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* XMP Rights Management-Schema: xmpRights:WebStatement, xmpRights:Marked
* XMP Medienverwaltungsschema: xmpMM:DocumentID

### Sprachalternativen {#language-alternatives}

XMP bietet Ihnen die Möglichkeit, eine **xml:lang** -Eigenschaft auf Texteigenschaften festzulegen, um die Sprache des Textes anzugeben.
