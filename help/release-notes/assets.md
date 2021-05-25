---
title: Versionshinweise zu AEM Assets
seo-title: AEM Assets
description: Spezifische Versionshinweise für Adobe Experience Manager 6.4 Assets.
seo-description: Spezifische Versionshinweise für Adobe Experience Manager 6.4 Assets.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
exl-id: 3f2cb2f9-2a4e-4c5d-b937-b693f27e11da
source-git-commit: 55e904cb24bac68c0b1bbea59786cb4c0c711d61
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 60%

---

# AEM Assets Versionshinweise {#aem-assets-release-notes}

Die wichtigsten Funktionen, Highlights und Verbesserungen in AEM 6.4 Assets werden in diesen Versionshinweisen behandelt. Ausführliche Informationen finden Sie unter den angegebenen Links.

## Adobe Asset Link {#adobe-asset-link}

Mit Adobe Asset Link in Creative Cloud für Unternehmen lässt sich die Zusammenarbeit zwischen Kreativen und Marketingexperten bei der Erstellung von Inhalten optimieren. Es handelt sich um eine neue native Funktion in Creative Cloud für Unternehmen, die eine direkte Verbindung zu AEM Assets über Adobe Photoshop, Adobe Illustrator oder Adobe InDesign ermöglicht, ohne diese Tools verlassen zu müssen.

Weitere Informationen zu Funktionen, Voraussetzungen und Zugriff finden Sie auf der Seite [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) .

## Verbesserte Smart-Tags (unterstützt von Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4 führt zusätzlich zu Smart-Tags, die in AEM 6.3 eingeführt wurden, eine auf künstlicher Intelligenz basierende Funktion für optimierte Smart-Tags ein.

* Smart Content Service lernt die Unternehmenstaxonomie des Kunden und verwendet sie, um digitale Assets automatisch mit kundenrelevanten Tags zu versehen, die nicht nur allgemeine Tags sind. Dadurch lassen sich Asset erheblich schneller auffinden, wodurch die Markteinführungszeit verkürzt wird.
* Adobe Sensei unterstützt den Smart Content Service, mit dem Sie den Bilderkennungsalgorithmus auf Ihre Unternehmenstaxonomie trainieren können. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf ähnliche Assets anzuwenden.

Um AEM Assets Enhanced Smart Tags zu verwenden, installieren Sie das [neueste Service Pack von AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de).

## Smart Translation Search (powered by Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4 verfügt über eine Funktion zur intelligenten Übersetzungssuche, die mehrsprachige Suchszenarien unterstützt. Unternehmen mit weltweit verstreuten Teams können nun in verschiedenen Sprachen nach Assets suchen, ohne auf kostspielige und zeitraubende Übersetzungs-Workflows angewiesen zu sein. 

* Die Suchabfrage wird ohne manuelles Eingreifen übersetzt.
* Smart-Tags werden auf Englisch generiert und in andere Sprachen maschinell übersetzt.
* Die mehrsprachige Suche wird mit der Open-Source-Bibliothek Apache Joshua erstellt, die mehr als 50 Sprachen unterstützt.

## Benutzererlebnis {#user-experience}

AEM 6.4 bietet erhebliche Verbesserungen beim Benutzererlebnis in den Bereichen Durchsuchen, Suchen, mehrseitige Assets und Administrations-Tools. Details:

Verbesserungen durchsuchen

* Neue Inhaltsstrukturleiste zur schnellen Navigation in Asset-Hierarchien. In Verbindung mit der Listenansicht steht damit wieder das Interaktionsmodell der klassischen Benutzeroberfläche zum Durchsuchen von Asset-Hierarchien zur Verfügung.
* Neue Tastaturbefehle, z. B. m zum Verschieben von Assets, p zum Öffnen der Eigenschaftenseite, Strg + C zum Kopieren und vieles mehr.
* Verbesserte Scrollfunktion, Lazy-Loading-Erlebnis in der Karten- und Listenansicht beim Durchsuchen einer großen Anzahl von Elementen.
* Verbesserte Kartenansicht mit Unterstützung für unterschiedlich große Karten basierend auf der Anzeigeeinstellung.
* Verbesserte Asset-Details in Benutzererlebnissen mit Option zur Anzeige, Navigation zum vorherigen oder nächsten Asset sowie Einblendung der Anzahl der Assets und des aktuellen Assets.

Suchverbesserungen

* Neue Schaltfläche, mit der zu den letzten Suchergebnissen zurückgekehrt werden kann, ohne die Suchanfrage erneut eingeben zu müssen.
* Neuer Zähler für Suchergebnisse, um die Anzahl der Suchergebnisse anzuzeigen.
* Verbesserter Suchfilter für Dateitypen mit der Möglichkeit, Suchergebnisse basierend auf differenzierten MIME-Typen wie JPG, PNG und PSD im Vergleich zu früheren Bild-, Dokument- und Multimediaoptionen zu filtern.
* Verbesserte Suchfilter mit genauen Zeitstempeln anstelle der bisherigen Zeitschiebereglerfunktion.

Verbesserungen an Assets mit mehreren Seiten

* Assets mit Mehrseitenformaten lassen sich nun mit weniger Klicks durchsuchen.
* Verbesserte Unterstützung von Kommentaren und Anmerkungen, die alle auf Asset-Ebene statt auf Seitenebene gesammelt werden.

Verbesserungen bei Admin Tools

* Verbesserte Eigenschaftenauswahl in den Admin Tools für Metadaten, Suche und Berichte mit Vervollständigungs- und Suchfunktion, um die Abläufe für Administratoren zu vereinfachen.

Kataloge

* Verbessertes Benutzererlebnis, Anpassung an die Benutzeroberfläche &quot;Vorlagen&quot;. Weitere Informationen finden Sie unter [Catalog Producer](../sites-administering/catalog-producer.md).

## Metadaten   {#metadata}

AEM 6.4 umfasst mehrere erweiterte Metadatenverwaltungsfunktionen, um Metadaten skalierbar zu verwalten und die Integrität der Metadaten mithilfe von Regeln und Überprüfungen durchzusetzen. Die wichtigsten Funktionen:

* Neue Funktion zum Massenexport von Metadaten (alle oder Auswahl) für eine große Anzahl von Assets im CSV-Format zur Bearbeitung, Freigabe und Drittanbieterintegration.
* Neue Funktion zum Massenimport von Metadaten, mit der CSV-Dateien importiert werden können, um in einem Schritt für mehrere Assets neue Metadaten hinzuzufügen und vorhandene Metadaten zu aktualisieren. Dieser Vorgang ist asynchron und behindert nicht die Systemleistung. Anschließend wird der Benutzer über das Benachrichtigungssystem von AEM informiert.
* Mithilfe des Metadatenschema-Tools lassen sich neue kaskadierende und kontextbezogene Metadaten erstellen. Es ist nun möglich, Ketten von Abhängigkeiten und Wertezuordnungen zwischen Feldern zu definieren. Sie können auch den Kontext festlegen, in dem Metadaten-Formularfelder ein- und ausgeblendet werden. Auf diese Weise können abhängig von Werten in anderen Feldern jeweils nur relevante Felder angezeigt werden.

## Berichte {#reports}

AEM 6.4 bietet wichtige Verbesserungen bei der Asset-Berichterstellung:

* Neues, (für große Repositorys) skalierbares Bericht-Framework auf Unternehmensebene, das Sling-Aufträge für die asynchrone Verarbeitung von Berichtanforderungen anwendet. Sie können die Berichterstellung zu einem bestimmten Zeitpunkt planen. Sie können einem Bericht auch benutzerdefinierte Spalten hinzufügen.
* Neue OOTB-Berichte, die von Kunden am häufigsten angefragt werden, wie z. B. Festplattennutzung, Dateien, Linkfreigaben, In Brand Portal veröffentlichen und Smart-Tags-Training.
* Neue Benutzeroberfläche zum Erstellen und Verwalten von Berichten mit differenzierten Optionen und Möglichkeiten zum Zugriff auf archivierte Berichte sowie zum Abruf des Status der Berichterstellung („Erfolg“, „Fehlgeschlagen“, „In Warteschlange“ usw.).

## Brand Portal {#brand-portal}

* **6.3-Plattform-Upgrade**: Brand Portal wurde von AEM 6.0 auf AEM 6.3 aktualisiert. Dabei wurden einige neue Funktionen und Leistungsverbesserungen eingeführt.
* **Paralleles Veröffentlichen**: Statt bisher nur einer können nun bis zu Replikationen zwischen AEM Assets und Brand Portal erfolgen, wodurch die Veröffentlichung erheblich beschleunigt wird.
* **Veröffentlichen von Schemata und Suchfacetten**: Möglichkeit, Metadatenschemata und benutzerdefinierte Suchfacetten in Brand Portal zu veröffentlichen, wodurch doppelte Arbeit vermieden wird.
* **Massenveröffentlichen von Tags**: Möglichkeit, die Taxonomie (zusammen mit der Hierarchie) in Brand Portal zu veröffentlichen, wodurch doppelte Arbeit vermieden wird.
* **Selbstregistrierung oder Zugriff anfordern**: Workflow für nicht registrierte Benutzer in Brand Portal.
* **In-App-Wartungsbenachrichtigung**: Benachrichtigungen werden lange im Voraus angezeigt, um Störungen im Geschäftsablauf zu vermeiden.
* **Verbesserte Berichterstellung**: Es sind nun OOTB-Berichte zu Downloads, Veröffentlichungen und Linkfreigaben verfügbar.
* **DRM-basierte Beschränkungen**: Nach Ablauf eines lizenzierten Assets steht dieses nicht mehr in Brand Portal zum Download zur Verfügung.

## AEM-Desktop-Programm {#aem-desktop-app}

AEM Desktop-Programm wird auf Version 1.8 aktualisiert, die mit AEM 6.4 kompatibel ist. Die vollständige Liste der Änderungen für AEM Desktop-Programm finden Sie in einem dedizierten Dokument [AEM des Desktop-Programms Versionshinweise](https://docs.adobe.com/content/help/de-DE/experience-manager-desktop-app/using/release-notes.html) .\
Hier finden Sie eine Liste AEM Highlights des -Desktop-Programms seit der Veröffentlichung von AEM 6.3:

* Möglichkeit, hierarchische Ordner im Hintergrund hochzuladen.
* Benutzeroberfläche zur Überwachung von Asset-Uploads im Hintergrund.
* Verbesserungen beim Caching, einschließlich einer Benutzeroberfläche zur Verwaltung von Caching-Parametern.
* Erweiterte Unterstützung für AEM-Authentifizierungskonfigurationen (SAML/SSO) und Netzwerkproxy.
* Unterstützungsmöglichkeit: einfachen Zugriff auf Protokolle über die Benutzeroberfläche.
* Verbesserte Stabilität und Fehlerbehebung bei Problemen auf Kundenseite.

Um den Zugriff auf die Dokumentation und Best Practices zu erleichtern, stehen die folgenden Dokumentationen zur Verfügung:

* [Benutzerhandbuch](https://docs.adobe.com/content/help/de/experience-manager-desktop-app/using/using.html) für Endbenutzer, die mit der Anwendung arbeiten.
* [Installationshandbuch](https://docs.adobe.com/content/help/de-DE/experience-manager-desktop-app/using/install-upgrade.html), das für Administratoren bestimmt ist, AEM und AEM Desktop-Programm für die Zusammenarbeit einzurichten

## Mehrstufiger Speicher {#tiered-storage}

AEM 6.4 enthält eine Reihe von Funktionen, die verschiedene Voreinstellungen für mehrstufigen Speicher unterstützen und Lebenszyklusregeln implementieren. Die Speicheroptionen unterstützen u. a. auch Public Clouds, nämlich AWS oder Azure.

* Die Möglichkeit für Benutzer, die Speicherklasse nach Belieben auszuwählen und später zu ändern und Regeln für die Speicherung von Assets von einer Klasse in eine andere zu definieren oder den Lebenszyklus ihrer Assets zu verwalten.
* Die Möglichkeit für Benutzer, ihre Speicherkosten durch die Wahl einer anderen AWS- oder Azure-Option zu senken.

Eine Übersicht der unterstützten Plattformen finden Sie in der [Dokumentation der technischen Anforderungen](../sites-deploying/technical-requirements.md).

## Geschlossene Benutzergruppe {#closed-user-group}

* In AEM 6.4 bietet Closed User Group (Geschlossene Benutzergruppe) oder CUG die Möglichkeit, den Ordnerzugriff auf die Veröffentlichungsinstanz zu beschränken. Es ist eine Touch-UI-Option, Prinzipale über die Ordnereigenschaftenseite auf Ordnerebene hinzuzufügen und sie auf alle Ordner und Unterordner/Assets innerhalb von anzuwenden.
* Wenn im Veröffentlichungsmodus eine CUG konfiguriert ist und die Autorisierung für einen Ordner aktiviert ist, werden Benutzer zu einer Anmeldeseite weitergeleitet, wenn sie versuchen, auf den Ordner zuzugreifen. Daher können autorisierte Benutzer erst nach erfolgreicher Anmeldung auf den Ordner und seine Assets zugreifen. Entsprechend beschränkt die geschlossene Benutzergruppe den Lesezugriff auf eine bestimmte Struktur im Content-Repository für alle Benutzer außer ausgewählten Prinzipalen.

## Dynamic Media-Add-on {#dynamic-media-add-on}

Dynamic Media in 6.4 unterstützt einen neuen Modus, in dem Master-Assets über die Web-Benutzeroberfläche von AEM Assets hochgeladen und verwaltet werden und dynamische Ausgabeformate und andere Funktionen für dynamische Medien im Hintergrund vom Cloud-Bereitstellungservice für dynamische Medien verwaltet werden.

In diesem Modus (der mit der Veröffentlichung von [AEM 6.3 Feature Packs 14410 und 18912](https://helpx.adobe.com/de/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html) eingeführt wurde) profitieren Benutzer von End-to-End-Asset-Management- und Dynamic Media-Funktionen über die moderne AEM Assets-Web-Benutzeroberfläche und nutzen weiterhin die Bereitstellungsdienste, die abwärtskompatibel mit Dynamic Media Classic (Scene7) sind, einschließlich der Bereitstellungs-URLs, die unverändert sind.

Darüber hinaus werden mit AEM 6.4 neue, auf Adobe Sensei basierende Funktionen, Erweiterungen für neue Medien wie VR und 3D, Dynamic Media-Viewer und Unterstützung für Erlebnisfragmente in interaktiven Bildern und Karussellbannern eingeführt.

### Smartes Zuschneiden (powered by Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* Smartes Zuschneiden ermöglicht es, Bilder automatisch so zuzuschneiden, dass das gewünschte Motiv unabhängig von der Bildschirmgröße zu sehen ist, um ein responsives Design zu erzielen. Sie können die Zuschnitte in der Vorschau anzeigen und bei Bedarf manuell anpassen.
* Die Funktion ermöglicht darüber hinaus die automatische Erstellung von Mustern für Produktbilder. Die automatische Mustergenerierung hilft dabei, Farbfelder, Produktmuster oder beides automatisch zu den Produktbildern hinzuzufügen.

Weitere Informationen finden Sie in der Dokumentation zu [Bildprofilen](../assets/image-profiles.md).

Weitere Informationen zum smarten Zuschneiden in der Komponente Dynamic Media finden Sie in der Dokumentation zum [Hinzufügen von Assets mit dynamischen Medien zu Seiten](../assets/adding-dynamic-media-assets-to-pages.md).

### Intelligente Bildbearbeitung {#smart-imaging}

* Intelligente Bildbearbeitung nutzt die individuellen anzeigebezogenen Eigenschaften jedes Benutzers, um automatisch für sein Erlebnis optimierte Bilder bereitzustellen, was zu einer besseren Leistung und Interaktion führt.
* Bilder werden automatisch in verschiedene Formate konvertiert, basierend auf den Browser-Funktionen.
* Die Einstellungen für die Bildqualität werden im Browser festgelegt und entsprechend angewendet. Diese Informationen sorgen bei begrenzter Bandbreite und langsamen Verbindungsgeschwindigkeiten für eine akzeptable Bildladeleistung.

Weitere Informationen finden Sie in der Dokumentation zur [intelligenten Bildbearbeitung](../assets/imaging-faq.md).

### Verbesserungen für neue Medien und Viewer {#emerging-media-amp-viewer-enhancements}

* Es werden neue Viewer unterstützt, die den Benutzern bessere, immersive Erlebnisse bieten.
* Mit dem Panorama-Viewer können Sie Benutzer ansprechen und Raumszenen, -eigenschaften, -standorte und -landschaften besser erleben. Weitere Informationen finden Sie in der Dokumentation zu [Panoramabildern](../assets/panoramic-images.md).

* VR Viewer bietet interaktive Erlebnisse für Eigenschaften, Standorte und Landschaften.
* Vertikaler Bilder-Viewer wurde für Produktbilder optimiert.
* Verbesserte Möglichkeit zum Zugriff auf die Tastatur.
