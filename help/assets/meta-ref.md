---
title: Metadatenschema-Referenz
description: Erfahren Sie mehr über Standardkonventionen für die Beschreibung von Asset-Metadaten, einschließlich Dublin Core, IPTC und anderen Metadatenschemata.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 883bebc6-8bbc-43b1-91e5-9e2bf2470b6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 50%

---

# Metadatenschema-Referenz {#metadata-schemata-reference}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die folgende Referenz enthält Informationen zu bestimmten Metadatenschemata (in alphabetischer Reihenfolge) sowie eine Liste mit Eigenschaften und den zugehörigen Definitionen.

## Dublin Core {#dublin-core}

Dublin Core-Metadaten bieten einen standardisierten Satz von Konventionen zur Beschreibung von Assets, um deren Auffindbarkeit zu verbessern. In [!DNL Experience Manager] Assets, Dublin Core, beschreibt digitale Assets, einschließlich Video, Ton, Bildern und Dokumenten.

Der einfache Dublin Core Metadata Element Set (DCMES) enthält 15 Metadatenelemente, wie in der folgenden Tabelle aufgeführt. Jedes Dublin Core-Element ist optional und kann wiederholt werden. Sie können Dublin Core-Metadateninformationen genauso wie solche für medientypspezifische Metadaten hinzufügen oder löschen.

Zusätzlich zum DCMES wurden auch noch andere Metadatenelemente von der Dublin Core Initiative erstellt. Weitere Informationen finden Sie unter [Dublin Core Initiative](https://dublincore.org/).

| Eigenschaft | Beschreibung |
|---|---|
| contributor | Die Personen oder das Unternehmen, diedafür verantwortlich sind, zum Inhalt beizutragen. |
| coverage | Der geografische Standort oder Zeitraum, den das Asset abdeckt. |
| creator | Die Personen oder das Unternehmen, die dafür verantwortlich sind, den Inhalt zu erstellen. |
| date | Datum oder Zeitraum, mit dem das Asset verknüpft ist. |
| description | Weitere Informationen zum Asset. |
| format | Das Dateiformat, das physische Medium oder die Dimensionen des Assets. [!DNL Experience Manager] verwendet dc:format , um den MIME-Typ des Assets anzugeben. |
| identifier | Eine eindeutige Referenz zum Asset. |
| language | Die Sprache des Assets (z. B. „en“ für Englisch). |
| publisher | Die Personen oder das Unternehmen, die dafür verantwortlich sind, das Asset verfügbar zu machen. |
| relation | Ein zugehöriges Asset. |
| rights | Informationen dazu, wer die Rechte für dieses Asset besitzt. |
| source | Ein zugehöriges Asset, aus dem das Asset abgeleitet wurde. |
| subject | Das Thema des Assets. |
| title | Ein Name für das Asset. |
| type | Die Art oder das Genre des Assets. |

## IPTC {#iptc}

Der International Press Telecommunications Council (IPTC) ist ein Konsortium von Nachrichtenagenturen auf der ganzen Welt - eines seiner Ziele ist die Entwicklung und Aufrechterhaltung technischer Standards. Die IPTC hat eine Reihe von Fotometadaten-Standards für Bilder definiert, die fast universell von Fotografen akzeptiert werden. Diese Metadatenstandards waren Teil des umfassenderen Standards IPTC Information Interchange Model (IIM), der in den 90er Jahren erstellt wurde.

Obwohl die IPTC-Kopfzeileninformationen größtenteils durch XMP ersetzt wurden, stehen ein IPTC-Kernschema und ein Erweiterungsschema für XMP zur Verfügung. In Bildprogrammen werden sowohl XMP als auch IPTC-Eigenschaften synchronisiert.
