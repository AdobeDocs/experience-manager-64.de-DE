---
title: Allgemeine Versionshinweise zu Adobe Experience Manager 6.4
seo-title: Release Notes
description: 'Die Hinweise zu Adobe Experience Manager 6.4 enthalten Versionshinweise, Neuerungen, Installationsanweisungen und detaillierte Änderungslisten. '
seo-description: Adobe Experience Manager 6.4 notes outlining the release information, what's new, how to install and detailed change lists.
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
exl-id: ee034595-2d2a-4887-86c4-6bf0770da6a2
source-git-commit: 722a82c1048105c18d59dfc35815548f9b7eace4
workflow-type: tm+mt
source-wordcount: '2751'
ht-degree: 80%

---

# Allgemeine Versionshinweise zu Adobe Experience Manager 6.4 {#general-release-notes-for-adobe-experience-manager}

## Versionshinweise {#release-information}

| Produkt | Adobe Experience Manager |
|---|---|
| Version | 6.4 |
| Typ | Hauptversion |
| Datum der allgemeinen Verfügbarkeit | 4. April 2018 |
| Empfohlene Updates | Informationen hierzu finden Sie unter [AEM-Versionen und -Updates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de) |

### Wissenswertes {#trivia}

Der Veröffentlichungszyklus für diese Version von Adobe Experience Manager startete am 27. April 2017, durchlief 22 Iterationen zur Qualitätssicherung und Fehlerbehebung und endete am 22. März 2018. Insgesamt wurden in dieser Version 704 kundenbezogene Probleme behandelt, einschließlich Verbesserungen und neuer Funktionen.

Adobe Experience Manager 6.4 ist seit dem 4. April 2018 allgemein verfügbar.

>[!NOTE]
>
>Adobe empfiehlt die Installation des neuesten Service Packs, da alle neuen Feature Packs nur über bereitgestellt werden. [Service Packs](https://helpx.adobe.com/de/experience-manager/maintenance-releases-roadmap.html).

## Neuerungen {#what-s-new}

Adobe Experience Manager 6.4 ist eine Upgrade-Version für die Codebasis von Adobe Experience Manager 6.3. Die Software bietet neue und erweiterte Funktionen, wichtige Kundenkorrekturen, Erweiterungen für Kunden mit hoher Priorität und allgemeine Fehlerbehebungen, die auf die Produktstabilisierung ausgerichtet sind. Sie umfasst auch die meisten aller Adobe Experience Manager 6.3 Feature Packs, Hotfixes und Service Packs.

Die nachstehende Liste bietet eine Übersicht, während die nachfolgenden Seiten die vollständigen Details auflisten.

### Experience Manager Foundation {#experience-manager-foundation}

Vollständige Liste der Änderungen in [AEM Foundation](wcm-platform.md).

Die Plattform von Adobe Experience Manager 6.4 basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java Content Repository: Apache Jackrabbit Oak 1.8.2.

Quickstart verwendet Eclipse Jetty 9.3.22 als Servlet-Engine.

#### Benutzeroberfläche {#user-interface}

Die Benutzeroberfläche wurde verbessert, um sie effizienter und benutzerfreundlicher zu gestalten.

* [Neue Inhaltsstrukturleiste](/help/sites-authoring/basic-handling.md#content-tree) zur schnellen Navigation in Hierarchien. In Verbindung mit der Listenansicht sind damit wieder dieselben Interaktionen wie in der klassischen Benutzeroberfläche möglich.
* Verbesserte Funktion zum Scrollen in der Karten- und Listenansicht großer Ordner.
* [Verbesserte Interaktion mit den Suchergebnissen](/help/sites-authoring/search.md) – über die Schaltfläche „Zurück“ lässt sich das vorherige Suchergebnis wieder aufrufen.
* [Zusätzliche Tastenkombinationen](/help/sites-authoring/keyboard-shortcuts.md) für die gängigsten Aktionen, etwa das Öffnen einer bestimmten Leiste, das Bearbeiten, Verschieben und Löschen von Elementen oder das Öffnen von Eigenschaften.
* [Möglichkeit zum Deaktivieren von Tastaturbefehlen](/help/sites-authoring/user-properties.md) (diese können unter „Voreinstellungen“ aktiviert bzw. deaktiviert werden).
* [Keine weitere Anzeige von Zeitstempeln in der gesamten Benutzeroberfläche](/help/sites-authoring/user-properties.md) nach sieben Tagen (als Standardeinstellung in den Voreinstellungen festgelegt).

Weitere Informationen zu diesen Funktionen finden Sie in der [Dokumentation für die Bearbeitung.](/help/sites-authoring/home.md)

>[!CAUTION]
>
>Adobe plant keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. In AEM 6.4 ist die klassische Benutzeroberfläche integriert und Kunden, die ein Upgrade auf diese Version durchführen, können diese wie gehabt verwenden. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird. [Weitere Informationen](/help/sites-deploying/ui-recommendations.md).

#### Content-Repository {#content-repository}

* Schnellere und effizientere Komprimierung durch die Online-Revisionsbereinigung. Interne Tests haben gezeigt, dass die neue Tail-Komprimierung bis zu 10-mal schneller ist und im Vergleich zu AEM 6.3 mehr Plattenplatz mit weniger IOPS zurückgewinnen kann. Dies führt zu geringeren Leistungseinbußen bei Ausführung der Online-Revisionsbereinigung. Weitere Informationen finden Sie auf der [Dokumentationsseite](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes). 

* Fortlaufende Revisionsbereinigung für MongoMK ersetzt geplante Revisionsbereinigung.
* Verbesserte Effizienz bei der Revisionsbereinigung von Dokument-Knotenspeichern.

#### Suche und Indizierung {#search-indexing}

* Erweiterte Unterstützung für Indizierungsvorgänge über oak-run (CLI):

   * Indexkonsistenzüberprüfung
   * Indizierungsstatistiken
   * Import oder Export von Indexkonfigurationen
   * Neuindizierung

* Verringertes Repository-Wachstum im Zusammenhang mit Lucene für eine verbesserte Gesamtleistung des Systems

Weitere Informationen finden Sie auf [dieser Dokumentationsseite](/help/sites-deploying/indexing-via-the-oak-run-jar.md).

#### Überwachung {#monitoring}

* Eine neue [Systemübersicht](/help/sites-administering/operations-dashboard.md#system-overview) bietet eine Momentaufnahme aller leistungsbezogenen Systemstatus und Aktivitäten.
* Neue [Konsistenzprüfungen](/help/sites-administering/operations-dashboard.md#health-checks) für Indizierung, Abfragen und Wartung

#### Projekte und Workflows {#projects-and-workflows}

* Neuer [Workflow-Editor zum Erstellen und Bearbeiten von Workflow-Modellen](/help/sites-developing/workflows-models.md)

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### Upgrade von früheren Versionen {#upgrade-from-earlier-version}

* [Abwärtskompatibilität](/help/sites-deploying/backward-compatibility.md): Durch die Abwärtskompatibilität von Version 6.4 bleibt Ihr benutzerdefinierter Code in den meisten Fällen kompatibel. Außerdem verringert sich dadurch der mit dem Upgrade verbundene Aufwand.
* [Analyse der Upgrade-Komplexität](/help/sites-deploying/pattern-detector.md): Ein neues Mustererkennungstool analysiert vorab die Komplexität von Upgrades.
* [Repository-Neustrukturierung](/help/sites-deploying/repository-restructuring.md): erhebliche Umstrukturierung (in erster Linie /etc), um einfachere Upgrades zu erleichtern und Best Practices für die Implementierung zu fördern
* Weitere Informationen zu Upgrades finden Sie auf [dieser Seite](/help/sites-deploying/upgrade.md).

### Experience Manager Sites {#experience-manager-sites}

Vollständige Liste der Änderungen in [AEM Sites und Add-ons](sites.md).

#### Fluid Experiences {#fluid-experiences}

Mit der Einführung von Fluid Experiences Anfang 2017 und unterstützt durch Inhaltsfragmente, Erlebnisfragmente und Content Services hat Adobe die Entwicklung von Content Management mit Multi-Channel-Fokussierung eingeläutet. Mit AEM 6.4 werden die einzelnen Bereiche maßgeblich erweitert:

**[Inhaltsfragmente](/help/assets/content-fragments.md)**

Neu in 6.4 sind ein Visual Editor für [Inhaltsmodelle](/help/assets/content-fragments-models.md) und eine neue [konfigurierbare Komponente](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/content-fragment-component.html) zur Bereitstellung von flexiblen HTML-Ausgaben und JSON für die Einbindung in Content Services.

**Experience Fragments**

Das Erstellen von Varianten in einem Fragment mit identischem Inhalt, aber unterschiedlichem Layout gestaltet sich jetzt dank Baukastenprinzip effizienter. Zusätzlich zum Senden von Experience Fragments an Facebook und Pinterest ist es jetzt möglich, sie als Angebot an Adobe Target zu senden.

**Content Services**

Es wurden verschiedene Verbesserungen am Sling Model Exporter und den Kernkomponenten vorgenommen, um eine robuste JSON-Ausgabe zur Einbettung von Inhalten in mobile Apps und Erlebnisse bereitzustellen, die mit Einzelseitenanwendungen erstellt wurden.

#### Schnellere Erstellung von Sites {#gettings-sites-built-quicker}

Mit AEM 6.4 ist die Transformation zum Komponentenmodell der nächsten Generation abgeschlossen. Das mit Version 6.3 eingeführte und nun durch das Stilsystem ergänzte Kernkomponentenkonzept ermöglicht das effiziente Erstellen neuer bzw. Erweitern vorhandener Sites.

Empfohlenes Tutorial zur optimalen Nutzung des neuen Komponentenmodells: [Erste Schritte mit AEM Sites – WKND-Tutorial](https://docs.adobe.com/content/help/de-DE/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

#### Screens-Add-on {#screens-add-on}

AEM Screens steht für die Bereitstellung einer konsistenten Botschaft über alle Marketingkanäle, einschließlich Digital Signage- und Kiosk-Netzwerken. Mit Einführung von AEM 6.4 wird die Ausführung des Signage Player unter Microsoft Windows und Google Chrome OS unterstützt. Darüber hinaus sind Erweiterungen für die Geräteverwaltung per Fernzugriff und Zeitpläne (Gruppen von Kanälen) verfügbar.

Weitere Informationen zu Screens-Aktualisierungen finden Sie unter [AEM Screens-Benutzerhandbuch](https://docs.adobe.com/content/help/de-DE/experience-manager-screens/user-guide/aem-screens-introduction.html).

### Experience Manager Communities {#experience-manager-communities}

AEM 6.4 bietet eine Vielzahl neuer Funktionen und Erweiterungen für Communities. Vollständige Liste der Änderungen in [AEM Communities](communities-release-notes.md). Highlights dieser Version:

#### Verbesserte Moderation {#enhancements-to-moderation}

**Automatische Spamerkennung** 

Es gibt nun eine neue Engine zur Spamerkennung, mit der sich unerwünschte benutzergenerierte Inhalte auf Community-Sites und in Community-Gruppen herausfiltern lassen. Sobald die Engine unter „system/console/configMgr“ aktiviert wurde, markiert sie benutzergenerierte Inhalte anhand entsprechender vordefinierter Begriffe als Spam. Weitere Informationen über die Engine zur Spamerkennung finden Sie unter [Automatische Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md#spam-detection).

![Spamerkennung](assets/spamdetection.png)

**Neue Filter für „Fragen und Antworten“**

Die Massenmoderations-Konsole wurde um die neuen Filter „Beantwortet“ und „Nicht beantwortet“ ergänzt, um das Filtern von Fragen zu ermöglichen. Weitere Informationen zur Verwendung der Statusfilter „Beantwortet“ und „Nicht beantwortet“ finden Sie unter [Massenmoderation benutzergenerierter Inhalte](/help/communities/moderation.md#main-pars-note-521961797).

**Lesezeichen für Moderationsfilter**

Es gibt nun die Möglichkeit, die vordefinierten Moderationsfilter in der Moderatoren-Konsole mit Lesezeichen zu versehen. Diese Filter werden an das Ende der URL-Zeichenfolge angehängt und können daher gemeinsam genutzt, wiederverwendet und später wieder aufgerufen werden. Weitere Informationen zum Erstellen von Lesezeichen finden Sie unter [Massenmoderations-Konsole](/help/communities/moderation.md#main-pars-note-429176623).

#### Löschen von benutzergenerierten Inhalten und Benutzerprofilen {#delete-ugc-and-user-profiles}

AEM 6.4 Communities stellt [vorkonfigurierte APIs](/help/communities/user-ugc-management-service.md) und [Beispielservlets](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) bereit, um Endbenutzern die Kontrolle über ihre Daten zu ermöglichen. Diese APIs ermöglichen es zudem datenverarbeitenden Unternehmen, die DSGVO-Anforderungen der EU zu erfüllen.

#### Verbesserte Site- und Gruppenverwaltung {#enhancements-to-site-and-group-management}

**Erstellen von Gruppen mit mehreren Gebietsschemas in einem einzigen Schritt**

Es ist nun möglich, mehrsprachige Gruppen in einem Arbeitsgang zu erstellen. Um derartige Gruppen zu erstellen, können Benutzer über die Sites-Konsole zur Gruppensammlung der gewünschten Community-Site navigieren. Erstellen Sie eine Gruppe und geben Sie die gewünschten Sprachen auf der Seite „Community-Gruppenvorlage“ an. Weitere Informationen zu dieser Funktion finden Sie unter [Community-Gruppen-Konsole](/help/communities/groups.md).

![multilingualgroup](assets/multilingualgroup.png)

**[Löschen von Community-Sites und -Gruppen mit nur einem Klick](/help/communities/groups.md)**

Beim Zugriff über die globale Navigation ist für die betreffenden Sites und Gruppen nun das Symbol „Löschen“ verfügbar. Damit werden alle Elemente und Inhalte, die der jeweiligen Site oder Gruppe zugeordnet sind, gelöscht und sämtliche Benutzerzuordnungen entfernt. Weitere Informationen zu dieser Funktion finden Sie unter [Verwalten von Community-Sites](/help/communities/create-site.md#main-pars-text-fe17) und [Verwalten von Community-Gruppen](/help/communities/groups.md#main-pars-text-5e8c).

#### Verbesserte Aktivierung {#enhancements-to-enablement}

In Gruppen sind nun Katalog- und Zuweisungsfunktionen verfügbar. Dies ermöglicht die gezielte Erstellung, Verwaltung und Veröffentlichung von Schulungsinhalten für bestimmte Community-Mitglieder. Weitere Informationen zum Aktivieren von Community-Gruppen finden Sie unter [Verwalten von Aktivierungsressourcen](/help/communities/resource.md).

![assignmentcatalog](assets/assignmentcatalog.png)

### Experience Manager Assets {#experience-manager-assets}

AEM 6.4 wurde um mehrere neue Funktionen und Verbesserungen für Assets ergänzt, darunter eine neue verbesserte Creative Cloud-Integration, wichtige Innovationen im Bereich der künstlichen Intelligenz, verbesserte Metadatenverwaltung, Verbesserungen bei der Berichterstellung und allgemeine Verbesserungen des Benutzererlebnisses. Vollständige Liste der Änderungen in [AEM Assets](assets.md). Die Highlights der Version sind:

**Adobe Asset Link**

Mit Adobe Asset Link in Creative Cloud für Unternehmen lässt sich die Zusammenarbeit zwischen Kreativen und Marketingexperten bei der Erstellung von Inhalten optimieren. Es handelt sich um eine neue native Funktion in Creative Cloud für Unternehmen, die Photoshop, Illustrator und InDesign mit AEM verbindet - ohne dass Kreative ihre Werkzeuge ihrer Wahl überlassen müssen.

Weitere Informationen zu dieser Funktion, den damit verbundenen Systemanforderungen sowie zum Zugriff darauf finden Sie unter [Adobe Asset Link](https://www.adobe.com/de/creativecloud/business/enterprise/adobe-asset-link.html).

![adobe_asset_link](assets/adobe_asset_link.png)

**AEM-Desktop-Programm**

AEM Desktop-Programm wurde auf Version 1.8 aktualisiert, die mit AEM 6.4 kompatibel ist. Die vollständige Liste der Änderungen für AEM Desktop-Programm finden Sie in einer speziellen [Versionshinweise zum AEM-Desktop-Programm](https://docs.adobe.com/content/help/de-DE/experience-manager-desktop-app/using/release-notes.html) Dokument.

Zu den Verbesserungen, die seit Veröffentlichung von AEM 6.3 eingeführt wurden, gehören die Möglichkeit, hierarchische Ordner im Hintergrund hochzuladen, eine neue Benutzeroberfläche zur Überwachung von Asset-Vorgängen im Hintergrund, Verbesserungen beim Caching, Arbeiten im Netzwerk und bei der Anmeldung sowie allgemeine Verbesserungen hinsichtlich der Stabilität. Die Dokumentation umfasst außerdem ein [Handbuch mit Best Practices](https://docs.adobe.com/content/help/de/experience-manager-desktop-app/using/using.html).

**Adobe Sensei Services**

Zu den neuen Funktionen gehören optimierte Smart-Tags, mit denen die Taxonomien der jeweiligen Unternehmen erfasst werden und digitale Assets automatisch mit unternehmensspezifischen Tags versehen werden können, sowie die intelligente mehrsprachige Suche, die die Auffindbarkeit von Inhalten in mehreren Sprachen durch die unmittelbare Übersetzung von Suchbegriffen verbessert. Weitere Informationen zu dieser Funktion finden Sie unter [Optimierte Smart-Tags](/help/assets/enhanced-smart-tags.md).

![extended_smart_tags2](assets/enhanced_smart_tags2.png)

**Metadaten**

Zu den zahlreichen Verbesserungen, die mit dieser Version eingeführt wurden, gehört die Möglichkeit, Metadaten für eine große Anzahl von Assets und erweiterte Metadatenkonstrukte wie [kaskadierende Metadaten](/help/assets/cascading-metadata.md) gleichzeitig zu importieren und exportieren.

**Berichte**

Die Asset-Berichterstellung wurde in AEM 6.4 grundlegend überarbeitet und enthält jetzt ein neues Reporting-Framework, ein neues Benutzererlebnis und mehr OOTB-Berichte für Anwendungsfälle von Kunden. Weitere Informationen zum Erstellen unterschiedlicher Berichte finden Sie unter [Asset-Berichte](/help/assets/asset-reports.md).

**Benutzererlebnis**

Es wurden zahlreiche Verbesserungen eingeführt, um das Durchsuchen, Suchen und Verwalten von Assets zu verbessern, u. a. verbesserte Scrollfunktionen, eine Schaltfläche, mit der zu den letzten Suchergebnissen zurückgekehrt werden kann, und verbesserte Suchfilter. Die vollständige Liste finden Sie unter [AEM Assets](assets.md).

**Brand Portal**

Es wurden verschiedene Verbesserungen in den Bereichen Metadaten, Berichterstellung, digitale Rechte, Anmeldung und Veröffentlichungsleistung bei der Asset-Verteilung eingeführt. Informationen zu den neuen Verbesserungen und Funktionen finden Sie unter [Neue Funktionen in AEM Assets Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/introduction/whats-new.html).

#### Dynamic Media-Add-on {#dynamic-media-add-on}

AEM 6.4 umfasst zahlreiche neue Funktionen und Verbesserungen für dynamische Medien. Die vollständige Liste finden Sie unter [AEM Assets](assets.md). Hier einige der wichtigsten Highlights:

**Smartes Zuschneiden**

Das auf Adobe Sensei basierende smarte Zuschneiden ermöglicht es, Bilder automatisch so zuzuschneiden, dass das gewünschte Motiv unabhängig von der Bildschirmgröße zu sehen ist, um ein responsives Design zu erzielen. Sie können die Zuschnitte in der Vorschau anzeigen und bei Bedarf manuell anpassen. Die Funktion ermöglicht darüber hinaus die automatische Erstellung von Mustern für Produktbilder.

Weitere Informationen zum smarten Zuschneiden finden Sie in der Dokumentation zu [Bildprofilen](/help/assets/image-profiles.md).

Weitere Informationen zum smarten Zuschneiden in der Komponente „Dynamic Media“ finden Sie unter [Hinzufügen von Assets mit dynamischen Medien zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).

**Intelligente Bildbearbeitung**

Intelligente Bildbearbeitung nutzt die individuellen anzeigebezogenen Eigenschaften jedes Benutzers, um automatisch für sein Erlebnis optimierte Bilder bereitzustellen, was zu einer besseren Leistung und Interaktion führt.

Weitere Informationen finden Sie in der Dokumentation zur [intelligenten Bildbearbeitung](/help/assets/imaging-faq.md).

![smart_crop](assets/smart_crop.png)

**Neue Mediensegmente und Viewer-Verbesserungen**

Neue Viewer, darunter Panorama- und VR-Viewer, ermöglichen es Ihnen, noch intensivere Erlebnisse bereitzustellen.

Weitere Informationen finden Sie in der Dokumentation zu [Panoramabildern](/help/assets/panoramic-images.md).

### Experience Manager Forms {#experience-manager-forms}

AEM 6.4 Forms wurde um zahlreiche neue Funktionen und Erweiterungen ergänzt. Hier einige der Highlights:

* Interaktive Multi-Channel-Kommunikation
* Automatisches Ausfüllen der interaktiven Kommunikation über Geschäftsanwendungen
* Modernisierung von Workflows und Unterstützung mobiler Arbeitskräfte
* Lazy-Loading-Fragmente
* Einfaches Upgrade von LiveCycle auf Experience Manager Forms 6.4

Weitere Informationen hierzu finden Sie auf der Seite mit Versionshinweisen zu [AEM Forms](forms.md). Siehe auch [Zusammenfassung der neuen Funktionen und Verbesserungen in AEM 6.4 Forms](/help/forms/using/whats-new.md) für Informationen zu neuen und verbesserten Funktionen und Dokumentationsressourcen.

### Experience Manager Livefyre {#experience-manager-livefyre}

Livefyre lässt sich mit AEM 6.4-Instanzen integrieren. Weitere Informationen zur Integration von Livefyre mit AEM finden Sie auf den folgenden Seiten:

* [Integrieren mit Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)

### Kundenorientierte Entwicklung nutzen {#leverage-customer-focused-development}

Adobe verwendet ein kundenorientiertes Entwicklungsmodell, das es den Kunden ermöglicht, zu allen Phasen des Entwicklungsprozesses von der Spezifikation bis zur Entwicklung und zum Test beizutragen. Unser Dank geht an alle beteiligten Kunden und Partner in diesem Prozess.

Adobe hält die erforderlichen Vorgehensweisen und Prozesse bereit, um die Erfassung, Priorisierung und Verfolgung kundenorientierter Fehlerbehebungs- und Verbesserungsanforderungsentwicklung zu ermöglichen. Die [Adobe Marketing Cloud Support Portal](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) ist in das Adobe Enhancement &amp; Defect Tracking System integriert. Kundenprobleme werden, wenn möglich, gemeinsam mit dem Kundendienst identifiziert und gelöst. Bei einer Weiterleitung an Forschung und Entwicklung werden alle Kundeninformationen erfasst und zu Priorisierungs- und Berichterstellungszwecken verwendet. Bei der Entwicklung haben bezahlte Support- und Garantieprobleme sowie bezahlte Kundenerweiterungen Priorität.

Dieser Prozess der Priorisierung hat zu mehr als 500 kundenorientierten Änderungen geführt, die in AEM 6.4 vorgenommen wurden.

## Liste der Dateien, die Teil der Version sind {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Standalone-Schnellstart: cq-quickstart-6.4.0.jar
* Anwendungsserver-Schnellstart: cq-quickstart-6.4.0.war
* Dispatcher 4.3.1 oder höher für verschiedene Webserver und Plattformen. Siehe [Downloadlink](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html).
* Plug-in für Eclipse IDE. [Mehr dazu und Download](/help/sites-developing/aem-eclipse.md).

* Erweiterung für den Brackets-Code-Editor. [Mehr dazu und Download](/help/sites-developing/aem-brackets.md).
* Maven-/Gradle-Abhängigkeiten. Siehe [Downloadlink](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/).

**Sites**

* Kernkomponenten ([GitHub-Projekt](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components))
* We.Retail-Referenzimplementierung ([weitere Informationen](/help/sites-developing/we-retail.md))
* Projekt-Blueprint-Archetyp ([GitHub-Projekt](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype))
* AEM Screens-Player für verschiedene Zielplattformen ([Download](https://download.macromedia.com/screens/))
* Smart Content-Sprachmodelle. Englisch ist vorinstalliert, weitere Sprachen können heruntergeladen werden.

   * [Deutsch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Spanisch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italienisch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Französisch](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [AEM Modernisierungs-Tools](/help/sites-developing/modernization-tools.md) Migrieren von Komponenten der klassischen Benutzeroberfläche zu Coral 3

**Assets**

* Adobe Experience Manager-Desktop-Programm ([mehr dazu](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) und [herunterladen](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html))

* Paket zum Hinzufügen eines erweiterten PDF-Rasterizers ([weitere Informationen](/help/assets/aem-pdf-rasterizer.md) und [Download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg))

* Paket zum Hinzufügen von erweiterter Rohbildunterstützung ([weitere Informationen](/help/assets/camera-raw.md))

**Formulare**

* Pakete für Funktionen in AEM Forms:

   * [adobe-aemfd-aix-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-linux-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-solaris-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-win-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-osx-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)

## Sprachen {#languages}

Die Benutzeroberfläche ist in den folgenden Sprachen verfügbar:

* Englisch
* Deutsch
* Französisch
* Spanisch
* Italienisch
* Brasilianisches Portugiesisch
* Japanisch
* Vereinfachtes Chinesisch
* Traditionelles Chinesisch (begrenzte Unterstützung)
* Koreanisch

Experience Manager 6.4 ist für GB18030-2005 CITS zertifiziert und kann daher den chinesischen Kodierungsstandard verwenden.

## Installieren und Aktualisieren {#install-update}

Setup-Anforderungen finden Sie in den [Installationsanweisungen](/help/sites-deploying/custom-standalone-install.md).

Detaillierte Anweisungen finden Sie in der [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md).

## Unterstützte Plattformen {#supported-platforms}

Sie finden die gesamte Matrix für unterstützte Plattformen einschließlich Supportebene unter [Technische Anforderungen für AEM 6.4](/help/sites-deploying/technical-requirements.md)..

>[!NOTE]
>
>Oracle ist auf ein LTS-Modell (Long Term Support) für Oracle Java SE-Produkte umgestiegen. Java 9 und 10 sind Nicht-LTS-Versionen von Oracle (siehe [Oracle Java SE-Support-Roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe unterstützt nur LTS-Releases von Java beim Ausführen von AEM in einer Produktionsumgebung. Daher ist Java 8 die empfohlene Version für die Verwendung mit AEM 6.4.

## Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe prüft kontinuierlich den Bedarf an Funktionen im Produkt und ersetzt ggf. Funktionen durch leistungsstärkere Versionen oder implementiert ausgewählte Teile neu, um besser auf zukünftige Erwartungen oder Erweiterungen vorbereitet zu sein.

Lesen Sie die Liste veralteter und entfernter Funktionen in [Adobe Experience Manager 6.4](deprecated-removed-features.md). Die Seite enthält auch Vorankündigungen für Änderungen im Jahr 2019 und wichtige Hinweise für Kunden, die frühere Versionen aktualisieren.

## Detaillierte Änderungslisten {#detailed-changes-lists}

[AEM Sites](sites.md)

[AEM Assets](assets.md)

[AEM Communities](communities-release-notes.md)

[AEM Forms](forms.md)

[AEM Foundation](wcm-platform.md)

## Bekannte Probleme {#known-issues}

[Liste der bekannten Probleme](known-issues.md)

### Produktdownload und Support (beschränkte Websites) {#product-download-and-support-restricted-sites}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/).
* Produktaktualisierungen, Patches und Pakete für zusätzliche Funktionen in [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Kundensupport über Admin Console](https://adminconsole.adobe.com/). Weitere Informationen finden Sie unter [Neues Adobe-Supporterlebnis](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
