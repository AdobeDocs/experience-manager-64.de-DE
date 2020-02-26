---
title: Übersicht über AEM Communities
seo-title: Übersicht über AEM Communities
description: Überblick über die Funktionen und Einrichtung von AEM Communities
seo-description: Überblick über die Funktionen und Einrichtung von AEM Communities
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7

---


# Übersicht über AEM Communities {#aem-communities-overview}

Mit Adobe Experience Manager (AEM) Communities lässt sich leicht eine interne Communitysite erstellen, die verbesserte Leistung und optimierte Siteverwaltung bietet und aus Besuchern wertvolle Communitymitglieder macht.

Wenden Sie sich an Ihren Kundenbetreuer, um Informationen zur Lizenzierung von AEM Communities sowie zu zusätzlichen Lizenzierungen für Aktivierungsfunktionen und Adobe Analytics zu erhalten.

## Communities - Funktionen {#communities-features}

AEM Communities ermöglicht die Entwicklung einer Beziehung zu Site-Besuchern, die über Blogs, Q&amp;A- und Ereigniskalender informiert werden und gleichzeitig Einblicke in Foren, Kommentare und andere Community-Inhalte gewinnen, die häufig als benutzergenerierte Inhalte (UGC) bezeichnet werden.

Darüber hinaus ermöglichen AEM Communities die Moderation durch vertrauenswürdige Mitglieder in der Veröffentlichungsumgebung, die Anmeldung in sozialen Netzwerken mit Twitter und Facebook, die Inline-Übersetzung von Community-Inhalten, die Erstellung von Community-Gruppen von der veröffentlichten Community-Site, die Bewertung von Auszeichnungen, die Dateifreigabe, Benachrichtigungen und Aktivitätsströme.

Communities-Funktionen können mithilfe der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) , die auf GitHub.com öffentlich verfügbar ist, oder mit der neuen We.Retail-Referenzimplementierung demonstriert werden.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM-Site, die mit einem einfachen Assistenten erstellt wurde und zu einer Website mit vielen häufig verwendeten Funktionen führt, die bereits mit der Site verkabelt sind.

Der [Site-Erstellungsassistent](sites-console.md):

* Assembliert Funktionen der Site, basierend auf der ausgewählten [Community-Site-Vorlage](sites.md) , die
   * Basiert auf [Community-Funktionen](#community-functions)
   * Optionale [Community-Gruppen](#communitygroups) -Funktion
* Verwendet Einstellungen zum Konfigurieren:
   * Moderation
   * Anmeldung
   * Übersetzung
* Bietet wichtige Funktionen:
   * Responsive Design: Verwendet [Twitter-Bootstrap-Designs](https://getbootstrap.com)
   * Anmelden: Selbstregistrierung, [Social-Anmeldung](social-login.md), Benutzerprofile
   * Benachrichtigungen: Mitglieder sehen Ereignisse, die für sie relevant sind
   * Messaging: Mitglieder können innerhalb der Community-Site Nachrichten senden oder empfangen
   * Suchen: Möglichkeit der Suche innerhalb der Community-Site
   * Sprachwechsel: Möglichkeit zur Auswahl einer Sprache für eine [mehrsprachige Site](../../help/sites-administering/translation.md)
   * Verwaltung: Zugriff für autorisierte Mitglieder zur Moderation und Verwaltung von Benutzern auf der Community-Site
* Dadurch werden viele Authoring-Schritte auf Seitenebene vermieden:
   * Branding: Optionales Hochladen eines Bannerbilds zur Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü: Navigationslinks werden für die Funktionen bereitgestellt, die in der Community-Site-Vorlage enthalten sind

Informationen zum schnellen Erstellen einer neuen Community-Site finden Sie unter [Erste Schritte mit AEM Communities](getting-started.md).

## Persistenz von Gemeinschaftsinhalten {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, erfordert AEM Communities einen gemeinsamen Store speziell für benutzerdefinierte Inhalte (UGC), die von allen AEM-Instanzen (Autoren- und Veröffentlichungsinstanzen) freigegeben werden.

Der Zugriff auf Community-Inhalte erfolgt über den Speicher-Ressourcenanbieter (SRP), der eine Ebene bereitstellt, die den Zugriff von der zugrunde liegenden Topologie trennt und einen gemeinsamen Speicher für UGC unterstützt.

Weitere Informationen über die Persistenz von Community-Inhalten und empfohlene Bereitstellungen finden Sie unter:

* [Community-Inhaltsspeicherung](working-with-srp.md): beschreibt die verfügbaren SRP-Speicheroptionen für UGC
* [Empfohlene Topologien](topologies.md): Diskussion der Topologien auf der Grundlage von Anwendungsfällen und SRP-Auswahl
* [Aktualisierung auf AEM 6.3 Communities](upgrade.md): enthält nützliche Informationen zu UGC beim Wechsel zu AEM 6.3.

## Communities Konsolen {#communities-consoles}

In der Autorenumgebung bietet die globale Navigationskonsole Zugriff auf die [Communities-Konsole](consoles.md), die Folgendes enthält:

* [Sites-Konsole](sites-console.md)

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * [Community Groups](groups.md) Console

* [Moderatoren-Konsole](moderation.md)

   * Allgemeine Benutzeroberfläche für Massenmoderation in Autoren- und Veröffentlichungsumgebungen
   * Neue Filterkriterien

* [Mitglieder und Gruppen](members.md) - Verwaltungskonsolen

   * Ermöglicht das Erstellen und Verwalten von Benutzern (Mitgliedern) im Veröffentlichungsmodus in der Autorenumgebung
   * Möglichkeit zum Verbot von Mitgliedern
   * Ermöglicht das Erstellen und Verwalten von Gruppen (Benutzergruppen) auf der Seite der Veröffentlichung in der Autorenumgebung

* [Report](reports.md) Console

   * Ermöglicht die Erstellung von Berichten zu Zuweisungen, Beiträgen und Ansichten

* [Ressourcenkonsole](resources.md)

   * Bietet die Möglichkeit, Aktivierungsressourcen und Lernpfade zu erstellen
   * Ermöglicht Zugriff auf Berichte zu Aktivierungsressourcen und Lernpfaden

Die Konsole für globale Tools bietet Zugriff auf die folgenden Communities-Tools:

* [Site-Vorlagenkonsole](tools.md#sitetemplatesconsole)

   * Erstellen und Verwalten von Community-Site-Vorlagen

* [Gruppenvorlagen](tools.md#grouptemplatesconsole) -Konsole

   * Erstellen und Verwalten von Community-Gruppenvorlagen

* [Community Functions](tools.md#communityfunctionsconsole) Console

   * Community-Funktionen erstellen und verwalten

* [Speicherkonfigurationskonsole](tools.md#storageconfiguratonconsole)

   * Auswählen und Konfigurieren des [gemeinsamen Speichers](working-with-srp.md) für die Site

* [Komponenten-Leitfaden](components-guide.md)

   * Eine Beispielsite, [Community-Komponenten](http://localhost:4502/editor.html/content/community-components/en.html), die eine Stichprobe aller Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit bietet, mit ihnen zu experimentieren

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung einer Community-Site basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage, die aus Community-Funktionen und Community-Gruppenvorlagen besteht, bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Benutzerprofile, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

Siehe [Site-Vorlagenkonsole](sites.md).

## Community-Funktionen {#community-functions}

Die zu erwartenden Merkmale einer Community-Erfahrung sind bekannt. Bei AEM Communities sind diese Funktionen als Bausteine, auch als Community-Funktionen bezeichnet, verfügbar.

Community-Funktionen sind normale AEM-Seiten, die aus Komponenten bestehen, die zu einer Funktion verdrahtet sind, die leicht in eine Community-Site-Vorlage integriert werden kann.

See the [Community Functions console](functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht die dynamische Erstellung einer Unter-Community innerhalb einer Community-Site durch autorisierte Benutzer und Community-Mitglieder aus der Autor- und Veröffentlichungsumgebung .

In der Autorenumgebung können Community-Gruppen (Unter-Communities) innerhalb einer bestehenden Community-Site oder in einer vorhandenen Gruppe verschachtelt erstellt werden, wenn die Struktur der Vorlage die Funktion [Gruppen enthält](functions.md#groups-function).

Das Erstellen einer Community-Gruppe erfordert die Auswahl einer Community-Gruppenvorlage, die das Design der Community-Gruppen-Seite(n) bereitstellt. Wenn eine Funktion &quot;Gruppen&quot;zu einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass entweder eine Gruppenvorlage angegeben wird oder eine Auswahl von Vorlagen zum Zeitpunkt der Erstellung einer neuen Community-Gruppe bereitgestellt wird.

Siehe auch:

* [Site-Gruppenkonsole](groups.md) - Erstellen von Unter-Communities in der Autorenumgebung
* [Gruppenvorlagen-Konsole](tools-groups.md) - Erstellen der Sitestruktur für Gruppen
* [Erste Schritte mit AEM Communities](getting-started.md) - Lernprogramm zum schnellen Erstellen einer Community-Site mit verschachtelten Gruppen

## Community-Komponenten {#community-components}

Die [Community-Komponenten](author-communities.md) , aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM-Site hinzuzufügen.

Der Leitfaden[ zu ](components-guide.md)Community-Komponenten steht zur interaktiven Erforschung der Komponenten zur Verfügung.

## Communities {#types-of-communities}

### Einsatzgemeinschaft {#engagement-community}

Eine Interaktionsgemeinschaft ist eine Community-Site, auf der Kunden zur Information, zum Abrufen von Feedback und zur Interaktion mit Community-Mitgliedern eingeladen werden.

Zu den Funktionen einer Interaktionsgemeinschaft zählen:

* Anmeldung
* Messaging
* Foren
* Comments
* Reviews
* Bewertungen
* Abstimmung
* Blogs
* Gruppen
* Kalender
* Übersetzung
* Moderation
* Benachrichtigungen
* Bewertung und Abzeichen
* Analytics-Berichte

Informationen zum schnellen Erstellen einer neuen Interaktionsgemeinschaft finden Sie unter [Erste Schritte mit AEM Communities](getting-started.md).

### Aktivierungsgemeinschaft {#enablement-community}

Eine Community-Community ist eine Community-Site, die Funktionen zum Online-Lernen enthält.

Zu den Funktionen einer Community für die Aktivierung gehören:

* Alle Funktionen einer [Interaktionsgemeinschaft](#engagement-community)
* Möglichkeit, Mitgliedern und Mitgliedsgruppen Inhalte und Lernressourcen zuzuweisen
* Unterstützung von SCORM-Inhalten, z. B. Quiz und Tests
* Nachverfolgung des Abschlusses von Zuweisungen
* Zugriff auf Reports &amp; Analysen
* Möglichkeit, über eine Lernressource in Foren, Nachrichten, Kommentaren und Bewertungen zu sprechen

Wenn das [Enablement-Add-on konfiguriert](enablement.md)ist, kann eine Community für die Aktivierung erstellt werden. Dies erfordert zusätzliche Lizenzen für die Verwendung in einer Produktionsumgebung. Eine Community-Site für die Aktivierung enthält die [Zuweisungsfunktion](#community-functions).

Um die Erstellung einer neuen Community für die Aktivierung zu vereinfachen, besuchen Sie [Erste Schritte mit AEM Communities für die Aktivierung](getting-started-enablement.md).

## AEM-Democomputer {#aem-demo-machine}

Die [AEM-Demomaschine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM- [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) [](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)undFormsaus, die häufig mehr Setup erfordern, als eine QuickStart-Instanz zu starten. Die AEM Demo Machine richtet zusätzliche [Infrastruktur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) wie MongoDB, Solr, MySQL, FFmpeg und E-Mail-Server ein.

Die AEM-Demomaschine besteht aus

* Eine [grafische Benutzeroberfläche](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Apache ANT-Skripten mit konfigurierbaren [Eigenschaften](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) und [Zielen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Pakete zur InstallationDie AEM Demo Machine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 und AEM 6.3 unter Windows, MacOS und Linux getestet.

Für AEM Demo Machine ist eine gültige AEM-Lizenz erforderlich.

>[!NOTE]
>
>Sehen Sie sich eine [Videoeinführung](https://www.youtube.com/watch?v=zEE_zkR9fVQ&feature=youtu.be) zum AEM Demo Machine an (13:26).

## Dokumentation zu AEM Communities {#aem-communities-documentation}

* Visit [Deploying Communities](deploy-communities.md) to learn about recommended deployments.

* Besuchen Sie [Administering Communities Sites](administer-landing.md) , um mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, das Tagging, Benachrichtigungen, das Scoring und Abzeichen zu erfahren.

* Visit [Developing Communities](communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.

* Unter [Authoring Communities-Komponenten](author-communities.md) erfahren Sie, wie Sie Communities-Komponenten erstellen und konfigurieren.

