---
title: Versionshinweise zu Livefyre Feature Pack 2.0.6
seo-title: Livefyre Feature Pack 2.0.6 Release Notes
description: Versionshinweise zu Livefyre Feature Pack 2.0.6
seo-description: Livefyre Feature Pack 2.0.6 Release Notes
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
exl-id: e09d2d59-41f0-4cf2-bcf3-ec3dbc3b8474
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 5%

---

# Versionshinweise zu Livefyre Feature Pack 2.0.6 {#livefyre-feature-pack-release-notes}

## Versionshinweise {#release-information}

| Produkte | Livefyre Feature Pack 2.0.6 |
|--- |--- |
| Version | 2,0,6 |
| Typ | Neue Funktionen |
| Datum | 31. August 2018 |
| Download-URL | Wenden Sie sich an Ihren Administrator |
| Kompatibilität (*) | AEM 6.4 SP1, 6.4, 6.3 GA und 6.2 SP1 |
| Beschreibung | Mit diesem Package können Sie die branchenführenden Kuratierungsfunktionen von Livefyre in Ihre AEM integrieren, sodass Sie wertvolle benutzergenerierte Inhalte (UGC) aus sozialen Netzwerken in Minutenschnelle auf Ihrer Site veröffentlichen können. |

## Was ist in Livefyre Feature Pack 2.0.6 enthalten? {#what-is-included-in-livefyre-feature-pack}

Dieses Paket integriert die branchenführenden Kuratierungsfunktionen von Livefyre in Ihre AEM-Instanz, sodass Sie wertvolle benutzergenerierte Inhalte (UGC) in Minutenschnelle von sozialen Netzwerken auf Ihrer Site veröffentlichen können. Dieses Paket umfasst drei verschiedene Komponenten:

**Importieren von UGC-Inhalten in AEM Assets**

* Importieren Sie mit dem UGC Importer von Twitter und Instagram benutzerdefinierte Inhalte (UGC) aus Livefyre Studio in AEM Assets.
* Rufen Sie Ihre Livefyre-Bibliothek auf.
* Suchen Sie in Twitter und Instagram mithilfe der Livefyre Social-Suche in Echtzeit.
* Verwalten von Rechten auf der benutzergenerierten Inhalte.

**Hinzufügen von Livefyre-Komponenten zu AEM Sites oder Communities**

* Erstellen und passen Sie mit einer Suite von Social-Komponenten, einschließlich Karten, Galerien und Media Walls, sofort dynamische und ansprechende Erlebnisse an.
* Veröffentlichen Sie UGC in AEM Sites oder Communities.

**Importieren von Produktkatalogen in Livefyre mit AEM Commerce**

* Integrieren Sie Ihren vorhandenen Produktkatalog nahtlos in Livefyre, um die Benutzerinteraktion und -konvertierung auf Ihren Sites zu fördern und für benutzergenerierte Inhalte mit Shopping-Funktion zu sorgen.
* Bearbeiten oder löschen Sie Elemente in Ihrem AEM Commerce-Produktkatalog und aktualisieren Sie automatisch Änderungen in Livefyre.

Hilfe zur Installation finden Sie unter [Integration mit Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html).

### Zusätzliche Versionsinformationen {#additional-release-information}

Aufgrund von Aktualisierungen, die sich auf die Aggregation von Inhalten aus Nicht-Business-Benutzerkonten von Instagram auswirken, können wir keine Kommentare mehr in Ihrem Namen posten oder automatisch nach Antworten des Autors suchen. [Klicken Sie hier, um mehr zu erfahren](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6 unterstützt AEM klassische Benutzeroberfläche nicht.

#### Neue Funktion oder Verbesserung {#new-feature-or-improvement}

* Es wurde die Möglichkeit hinzugefügt, benutzergenerierte Inhalte zu durchsuchen, bevor in Livefyre soziale Konten für Rechteanforderungen eingerichtet werden. Sie müssen soziale Konten einrichten, um Berechtigungen anzufordern, oder die Rechteanforderung überschreiben, wenn Sie Eigentümer des Inhalts sind.
* Instagram und Twitter [Workflow für UGC-Rechteanforderungen](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html) wurde aktualisiert, um den neuesten APIs zu entsprechen.
* Der Berechtigungsstatus und die entsprechenden Aktionen werden jetzt auf dem Bildschirm mit den Rechteanforderungen angezeigt.

#### Fehlerbehebungen {#bug-fixes}

* Es wurde ein Problem behoben, bei dem das Löschen eines Social-Kontos in Livefyre Studio, das für die Rechteanforderung verwendet wurde, einen Fehler beim Laden der UGC-Bibliothek in AEM verursachte.
* Es wurde ein Problem behoben, bei dem die Asset-Anzahl in Livefyre Studio nicht mit der Asset-Anzahl in der AEM UGC-Bibliothek übereinstimmte.
* Es wurde ein Problem in der UGC-Bibliothek behoben, bei dem gefilterte Ergebnisse angezeigt wurden, nachdem die Filteroptionen zurückgesetzt wurden.
* Es wurde ein Problem mit AEM Commerce behoben, bei dem durch Aktionsaufrufe Benutzer zur falschen URL weitergeleitet wurden.
* Es wurde ein Problem in AEM Sites behoben, durch das beim Ziehen und Ablegen mehrerer Komponenten in den ParSys-Platzhalter diese nicht mehr angezeigt wurde.
* Es wurde ein Problem behoben, bei dem behinderte Social-Konten zur Auswahl verfügbar waren, wenn eine Rechteanforderung gesendet wurde.
* Es wurde ein Problem behoben, bei dem beim Ziehen und Ablegen von benutzergenerierten Inhalten aus Assets in Sites ein Fehler auftrat.
* Es wurde ein Problem behoben, durch das beim Ziehen und Ablegen von Chat- und Liveblog-Komponenten in Sites die App nicht erstellt wurde.
* Es wurde ein Problem behoben, bei dem die Kommentar-App einen Fehler verursachte, wenn Benutzer versuchten, einen Kommentar abzugeben.
* Es wurde ein Problem behoben, durch das beim Hinzufügen der Livefyre Media Wall App zu einer Site ein zusätzlicher Knoten im Java Content Repository erstellt wurde.
* Es wurde ein Problem behoben, das Seitenumbrüche und Konsolenfehler bei der UGC-Suche in Instagram verursachte.
* Es wurde ein Problem behoben, bei dem Instagram-Benutzersymbole API-Fehler in Assets generierten.
* Es wurde ein Problem behoben, durch das die App &quot;Bewertungen&quot;zu einer Site ohne vordefiniertes Format hinzugefügt wurde.
* Es wurde ein Problem mit der Touch-optimierten Benutzeroberfläche und der Inline-Bearbeitung behoben.
* Fehlerkorrektur - Beim Importieren bestimmter Instagram-Bild-Assets tritt jetzt kein Fehler mehr auf.
* Es wurde ein Problem behoben, bei dem der Livefyre-HTTP-Client in AEM keine Proxy-Konfiguration unterstützte.
