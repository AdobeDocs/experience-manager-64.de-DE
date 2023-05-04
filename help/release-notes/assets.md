---
title: Versionshinweise zu AEM Assets
seo-title: AEM Assets
description: Spezifische Versionshinweise zu Adobe Experience Manager 6.4 Assets.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Assets.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
exl-id: 3f2cb2f9-2a4e-4c5d-b937-b693f27e11da
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 3%

---

# Versionshinweise zu AEM Assets {#aem-assets-release-notes}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die wichtigsten Funktionen, Highlights und Verbesserungen in AEM 6.4 Assets werden in diesen Versionshinweisen behandelt. Ausführliche Informationen finden Sie unter den angegebenen Links.

## Adobe Asset Link {#adobe-asset-link}

Adobe Asset Link in Creative Cloud für Unternehmen optimiert die Zusammenarbeit zwischen Kreativen und Marketingexperten bei der Inhaltserstellung. Es handelt sich um eine neue native Funktion in Creative Cloud für Unternehmen, die eine direkte Verbindung zu AEM Assets über Adobe Photoshop, Adobe Illustrator oder Adobe InDesign ermöglicht, ohne diese Tools verlassen zu müssen.

Weitere Informationen zu Funktionen, Voraussetzungen und Zugriff finden Sie unter [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) Seite.

## Verbesserte Smart-Tags (mit Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4 führt zusätzlich zu Smart-Tags, die in AEM 6.3 eingeführt wurden, eine auf künstlicher Intelligenz basierende Funktion für optimierte Smart-Tags ein.

* Smart Content Service lernt die Unternehmenstaxonomie des Kunden und verwendet sie, um digitale Assets automatisch mit kundenrelevanten Tags zu versehen, die nicht nur allgemeine Tags sind. Sie verbessert die Entdeckung von Vermögenswerten erheblich und verkürzt die Markteinführungszeit.
* Adobe Sensei unterstützt den Smart Content Service, mit dem Sie den Bilderkennungsalgorithmus auf Ihre Unternehmenstaxonomie trainieren können. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf ähnliche Assets anzuwenden.

Um AEM Assets Enhanced Smart Tags zu verwenden, installieren Sie die [neuestes Service Pack für AEM 6.4](https://helpx.adobe.com/de/experience-manager/aem-releases-updates.html).

## Smart Translation Search (basierend auf Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4 verfügt über eine Funktion zur intelligenten Übersetzungssuche, die mehrsprachige Suchszenarien unterstützt. Kunden mit global verteilten Teams in mehreren Sprachen haben jetzt Zugriff auf die Suche in verschiedenen Sprachen, ohne teure und zeitaufwendige Übersetzungs-Workflows durchlaufen zu müssen.

* Die Suchabfrage wird ohne manuelles Eingreifen übersetzt.
* Smart-Tags werden auf Englisch generiert und in andere Sprachen maschinell übersetzt.
* Die mehrsprachige Suche wird mit der Open-Source-Bibliothek Apache Joshua erstellt, die mehr als 50 Sprachen unterstützt.

## Anwendererlebnis {#user-experience}

AEM 6.4 bietet erhebliche Verbesserungen beim Benutzererlebnis in den Bereichen Durchsuchen, Suchen, mehrseitige Assets und Administrations-Tools. Details unten:

Verbesserungen durchsuchen

* Neue Leiste &quot;Inhaltsstruktur&quot;, um schnell in einer Asset-Hierarchie zu navigieren. In Kombination mit der Listenansicht wird dadurch das Interaktionsmodell der klassischen Benutzeroberfläche zum Durchsuchen von Asset-Hierarchien wiederhergestellt.
* Neue Tastaturbefehle, z. B. m zum Verschieben von Assets, p zum Öffnen der Eigenschaftenseite, Strg + C zum Kopieren und vieles mehr.
* Verbessertes Scrollen, verzögertes Laden in der Karten- und Listenansicht zum Durchsuchen einer großen Anzahl von Assets.
* Verbesserte Kartenansicht mit Unterstützung für verschiedene Karten unterschiedlicher Größe, basierend auf der Anzeigeeinstellung.
* Verbesserte Asset-Detailerfahrung mit der Möglichkeit, zum &quot;vorherigen&quot;oder &quot;nächsten&quot;Asset zu navigieren und die Anzahl der Assets sowie das aktuelle Asset anzuzeigen.

Suchverbesserungen

* Neue Schaltfläche Zurück zur Suche mit der Möglichkeit, zu einem Suchelement zu navigieren und in den Suchergebnissen an dieselbe Position zurückzukehren, ohne die Suchabfrage erneut auszuführen.
* Neue Suchergebnisanzahl zur Anzeige der Anzahl der Suchergebnisse.
* Verbesserter Suchfilter für Dateitypen mit der Möglichkeit, Suchergebnisse basierend auf differenzierten MIME-Typen wie JPG, PNG und PSD zu filtern, im Vergleich zu früheren Bild-, Dokument- und Multimediaoptionen.
* Verbesserte Suchfilter mit präzisen Zeitstempeln anstelle der bisherigen Zeitschieberegler-Funktion.

Verbesserungen an Assets mit mehreren Seiten

* Verbessertes Durchsuchen mehrseitiger Assets mit reduzierter Anzahl an Klicks.
* Verbesserte Unterstützung von Kommentaren und Anmerkungen, bei denen alle auf Asset-Ebene und nicht auf Seitenebene erstellt wurden.

Verbesserungen bei Admin Tools

* Verbesserte Eigenschaftsauswahl in den Admin Tools für Metadaten, Suche und Berichte mit Typvorschau und Browserfunktion, um das Admin-Erlebnis zu vereinfachen.

Kataloge

* Verbessertes Benutzererlebnis, Anpassung an die Benutzeroberfläche &quot;Vorlagen&quot;. Weitere Informationen finden Sie unter [Catalog Producer](../sites-administering/catalog-producer.md).

## Metadaten {#metadata}

AEM 6.4 umfasst mehrere erweiterte Metadatenverwaltungsfunktionen, mit denen Metadaten skaliert verwaltet und die Metadatenintegrität durch Regeln und Überprüfungen durchgesetzt werden kann. Hier finden Sie die wichtigsten Funktionen:

* Neue Massenexport-Funktion für Metadaten zum Exportieren (aller, selektiven) Metadaten für eine große Anzahl von Assets im CSV-Format zur Bearbeitung, Freigabe und Drittanbieterintegration.
* Neue Funktion zum Massen-Metadatenimport zum Importieren von CSV-Dateien zum Hinzufügen neuer Metadaten und zum Aktualisieren vorhandener Metadaten für mehrere Assets in einem Schritt. Dieser Vorgang ist asynchron und behindert nicht die Systemleistung. Nach Abschluss wird der Benutzer über AEM Benachrichtigungssystem benachrichtigt.
* Neue kaskadierende und kontextbezogene Metadaten mit dem Metadatenschema-Tool. Es ist jetzt möglich, Abhängigkeitsketten und Wertzuordnungen zwischen Feldern zu definieren. Sie können auch den Kontext definieren, in dem Metadatenformularfelder angezeigt/ausgeblendet werden. Auf diese Weise können Sie je nach Werten in anderen Feldern jederzeit nur relevante Felder anzeigen.

## Berichte {#reports}

AEM 6.4 bietet wichtige Verbesserungen bei der Asset-Berichterstellung:

* Neues Berichterstellungs-Framework auf Unternehmensebene, skalierbar (für große Repositorys), das Sling-Aufträge für die asynchrone Verarbeitung von Berichtsanforderungen anwendet. Sie können den Bericht zu einem bestimmten Datum und einer bestimmten Uhrzeit planen. Sie können einem Bericht auch benutzerdefinierte Spalten hinzufügen.
* Neue OOTB-Berichte, die von Kunden am häufigsten angefragt werden, wie z. B. Festplattennutzung, Dateien, Linkfreigaben, In Brand Portal veröffentlichen und Smart-Tags-Training.
* Neue Benutzeroberfläche zur Berichterstellung und -verwaltung mit feinen Optionen, Möglichkeit zum Zugriff auf archivierte Berichte, Anzeige des Status der Berichtsausführung (Erfolg, fehlgeschlagen, in die Warteschlange gestellt usw.).

## Brand Portal {#brand-portal}

* **6.3 Plattform-Upgrade**: Brand Portal wurde von AEM 6.0 auf AEM 6.3 aktualisiert, mit neuen Funktionen und Leistungsverbesserungen.
* **Paralleles Veröffentlichen**: Zwischen AEM Assets und Brand Portal (früher 1) können bis zu Replikationen auftreten, die die Veröffentlichungsleistung erheblich verbessern.
* **Veröffentlichen von Schemata und Suchfacetten**: Möglichkeit, Metadatenschemata und benutzerdefinierte Suchfacetten in Brand Portal zu veröffentlichen, wodurch doppelte Arbeit vermieden wird.
* **Veröffentlichen von Massen-Tags**: Möglichkeit, die Taxonomie (zusammen mit der Hierarchie) in Brand Portal zu veröffentlichen, wodurch doppelte Arbeit vermieden wird.
* **Selbstregistrierung oder Zugriff anfordern**: Workflow für nicht registrierte Benutzer in Brand Portal.
* **In-App-Wartungsbenachrichtigung (auf dem Bildschirm)**: Benachrichtigungen werden lange im Voraus angezeigt, um Störungen im Unternehmen zu vermeiden.
* **Berichterstellungsverbesserungen**: Drei OOTB-Berichte sind verfügbar: Downloads, Veröffentlichungen und Linkfreigaben.
* **DRM-basierte Einschränkungen**: Nachdem ein lizenziertes Asset abgelaufen ist, kann es nicht mehr von Brand Portal heruntergeladen werden.

## AEM-Desktop-Programm {#aem-desktop-app}

AEM -Desktop-Programm wird auf Version 1.8 aktualisiert, die mit AEM 6.4 kompatibel ist. Die vollständige Liste der Änderungen für AEM -Desktop-Programm finden Sie in einer speziellen [Versionshinweise zum AEM-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=de) Dokument.\
Hier finden Sie eine Liste AEM Highlights des -Desktop-Programms seit der Veröffentlichung von AEM 6.3:

* Möglichkeit zum Hochladen hierarchischer Ordner im Hintergrund.
* Benutzeroberfläche zum Überwachen von Asset-Uploads im Hintergrund.
* Verbesserungen beim Caching, einschließlich einer Benutzeroberfläche zum Verwalten von Caching-Parametern.
* Umfassende Unterstützung für AEM Authentifizierungskonfigurationen (SAML/SSO) und Netzwerk-Proxy.
* Unterstützungsmöglichkeit: einfachen Zugriff auf Protokolle über die Benutzeroberfläche.
* Verbesserte Stabilität und Fehlerbehebungen für Kundenprobleme.

Um den Zugriff auf die Dokumentation und Best Practices zu erleichtern, finden Sie die folgende Dokumentation:

* [Benutzerhandbuch](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de), die sich an Endbenutzer richtet, die mit der Anwendung arbeiten.
* [Installationshandbuch](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/install-upgrade.html), die darauf abzielt, dass Administratoren AEM und AEM Desktop-Programm für die Zusammenarbeit einrichten

## Tiered Storage {#tiered-storage}

AEM 6.4 umfasst eine Reihe von Funktionen, die verschiedene Tiered Storage-Voreinstellungen unterstützen und Lebenszyklusregeln implementieren. Die Speicheroptionen unterstützen auch öffentliche Clouds - AWS oder Azure (sind jedoch nicht beschränkt).

* Die Möglichkeit für Benutzer, die Speicherklasse nach Belieben auszuwählen und später zu ändern und Regeln für die Speicherung von Assets von einer Klasse in eine andere zu definieren oder den Lebenszyklus ihrer Assets zu verwalten.
* Möglichkeit für Benutzer, ihre Speicherkosten durch Auswahl eines anderen AWS oder Azure zu senken.

Eine Übersicht der unterstützten Plattformen finden Sie im Abschnitt [Technische Anforderungsdokumentation](../sites-deploying/technical-requirements.md).

## Geschlossene Benutzergruppe {#closed-user-group}

* In AEM 6.4 bietet Closed User Group (Geschlossene Benutzergruppe) oder CUG die Möglichkeit, den Ordnerzugriff auf die Veröffentlichungsinstanz zu beschränken. Es ist eine Touch-UI-Option, Prinzipale über die Ordnereigenschaftenseite auf Ordnerebene hinzuzufügen und sie auf alle Ordner und Unterordner/Assets innerhalb von anzuwenden.
* Wenn im Veröffentlichungsmodus eine CUG konfiguriert ist und die Autorisierung für einen Ordner aktiviert ist, werden Benutzer zu einer Anmeldeseite weitergeleitet, wenn sie versuchen, auf den Ordner zuzugreifen. Daher können autorisierte Benutzer erst nach erfolgreicher Anmeldung auf den Ordner und seine Assets zugreifen. Daher beschränkt CUG den Lesezugriff auf eine bestimmte Struktur im Inhalts-Repository für alle außer ausgewählten Prinzipalen.

## Dynamic Media-Add-on {#dynamic-media-add-on}

Dynamic Media in 6.4 unterstützt einen neuen Modus, in dem Übergeordnete Assets über die AEM Assets-Web-Benutzeroberfläche hochgeladen und verwaltet werden und dynamische Ausgabedarstellungen und andere Dynamic Media-Funktionen im Hintergrund vom Dynamic Media-Cloud-Bereitstellungsdienst verarbeitet werden.

In diesem Modus (wird zuerst mit der Veröffentlichung von [AEM 6.3 Feature Packs 14410 und 18912](https://helpx.adobe.com/de/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)) nutzen, profitieren Benutzer von End-to-End-Asset-Management und Dynamic Media-Funktionen, die die moderne AEM Assets-Web-Benutzeroberfläche verwenden, und nutzen weiterhin die Bereitstellungsdienste, die abwärtskompatibel mit Dynamic Media Classic (Scene7) sind - einschließlich der Bereitstellungs-URLs, die unverändert sind.

Darüber hinaus bietet AEM 6.4 neue Funktionen, die von Adobe Sensei unterstützt werden, Verbesserungen für neue Medien wie VR und 3D, Dynamic Media-Viewer und Unterstützung für Experience Fragments in interaktiven Bildern und Karussellbannern.

### Smartes Zuschneiden (basierend auf Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* Smartes Zuschneiden bietet automatisch zerstörungsfreies Zuschneiden von Bildern, um den Zielpunkt für responsives Design zu erhalten. Sie können zugeschnittene Vorschläge in der Vorschau anzeigen und bei Bedarf manuell anpassen.
* Diese Funktion ermöglicht auch die automatisierte Mustergenerierung für Produktbilder. Mit der automatischen Mustergenerierung können Sie Produktbildern automatisch Farbmuster, Mustermuster oder beides hinzufügen.

Siehe [Bildprofile](../assets/image-profiles.md) Dokumentation .

Siehe auch [Hinzufügen von Dynamic Media-Assets zu Seiten](../assets/adding-dynamic-media-assets-to-pages.md) Dokumentation , um mehr über die Verwendung von smartem Zuschneiden mit der Dynamic Media-Komponente zu erfahren.

### Intelligente Bildbearbeitung {#smart-imaging}

* Intelligente Bildbearbeitung nutzt die individuellen anzeigebezogenen Eigenschaften jedes Benutzers, um automatisch für sein Erlebnis optimierte Bilder bereitzustellen, was zu einer besseren Leistung und Interaktion führt.
* Bilder werden basierend auf den Browserfunktionen automatisch in verschiedene Formate konvertiert.
* Bildqualitätseinstellungen werden im Browser festgelegt und angewendet. Diese Intelligenz hält die Leistung beim Laden von Bildern für eine begrenzte Bandbreite und langsame Verbindungsgeschwindigkeiten akzeptabel.

Siehe [Intelligente Bildbearbeitung](../assets/imaging-faq.md) Dokumentation .

### Neue Verbesserungen bei Medien und Viewern {#emerging-media-amp-viewer-enhancements}

* Es werden neue Viewer unterstützt, die Benutzern bessere, interaktive Erlebnisse bieten.
* Mit dem Panorama-Viewer können Sie Benutzer ansprechen und Raumszenen, -eigenschaften, -standorte und -landschaften besser erleben. Siehe [Panoramabilder](../assets/panoramic-images.md) Dokumentation.

* VR Viewer bietet interaktive Erlebnisse für Eigenschaften, Standorte und Landschaften.
* Vertikaler Bild-Viewer für Produktbilder optimiert.
* Verbesserungen bei der Barrierefreiheit der Tastatur.
