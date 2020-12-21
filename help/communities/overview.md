---
title: Übersicht über AEM Communities
seo-title: Übersicht über AEM Communities
description: Überblick über die Funktionen und die Einrichtung von AEM Communities
seo-description: Überblick über die Funktionen und die Einrichtung von AEM Communities
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
translation-type: tm+mt
source-git-commit: 1375282df15b1a1a1ab5ed760190af8d6288970e
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 5%

---


# Übersicht über AEM Communities {#aem-communities-overview}

Mit Adobe Experience Manager (AEM) Communities lässt sich leicht eine interne Communitysite erstellen, die verbesserte Leistung und optimierte Siteverwaltung bietet und aus Besuchern wertvolle Communitymitglieder macht.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## Communities-Funktionen {#communities-features}

AEM Communities ermöglicht die Entwicklung einer Beziehung zu Site-Besuchern, die über Blogs, Q&amp;A- und Ereignis-Kalender informiert werden und gleichzeitig Einblicke in Foren, Kommentare und andere Community-Inhalte gewinnen, die häufig als benutzergenerierte Inhalte (UGC) bezeichnet werden.

Darüber hinaus ermöglicht AEM Communities die Moderation durch vertrauenswürdige Mitglieder in der Veröffentlichungs-Umgebung, die Anmeldung in sozialen Netzwerken mit Twitter und Facebook, die Inline-Übersetzung von Community-Inhalten, die Erstellung von Community-Gruppen von der veröffentlichten Community-Site aus, die Bewertung von Auszeichnungen, Dateifreigabe, Benachrichtigungen und Aktivitäten-Streams.

Communities-Funktionen können mit der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki), die öffentlich auf GitHub.com verfügbar ist, oder mit der neuen We.Retail-Referenzimplementierung demonstriert werden.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM Site, die mit einem einfachen Assistenten erstellt wurde, der zu einer Website mit vielen allgemeinen Funktionen führt, die bereits mit der Site verkabelt sind.

Der [Site-Erstellungsassistent](sites-console.md):

* Assembliert Funktionen der Site, basierend auf der ausgewählten [Community-Site-Vorlage](sites.md), die
   * Erstellt aus [Community-Funktionen](#community-functions)
   * Optionale Funktion [Community-Gruppen](#communitygroups)
* Verwendet Einstellungen zum Konfigurieren:
   * Moderation
   * Anmeldung
   * Übersetzung
* Bietet wichtige Funktionen:
   * Responsive Design: Verwendet [Twitter-Bootstrap-Themen](https://getbootstrap.com)
   * Anmelden: Selbstregistrierung, [Social-Anmeldung](social-login.md), Profil des Benutzers
   * Benachrichtigungen: Die Abgeordneten sehen Ereignisse, die für sie relevant sind
   * Messaging: Mitglieder können innerhalb der Community-Site Nachrichten senden oder empfangen
   * Suchen: Möglichkeit der Suche innerhalb der Community-Site
   * Sprachwechsel: Möglichkeit zur Auswahl einer Sprache für eine [mehrsprachige Site](../../help/sites-administering/translation.md)
   * Verwaltung: Zugriff für autorisierte Mitglieder zur Moderation und Verwaltung von Benutzern auf der Community-Site
* Dadurch werden viele Authoring-Schritte auf Seitenebene vermieden:
   * Branding: Optionales Hochladen eines Bannerbilds zur Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü: Navigationslinks werden für die Funktionen bereitgestellt, die in der Community-Site-Vorlage enthalten sind

Um eine neue Community-Site schnell zu erstellen, besuchen Sie [Erste Schritte mit AEM Communities](getting-started.md).

## Persistenz von Community-Inhalten {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, benötigt AEM Communities einen gemeinsamen Store speziell für benutzergenerierte Inhalte (UGC), die von allen AEM (Autor- und Veröffentlichungsinstanzen) freigegeben werden.

Der Zugriff auf Community-Inhalte erfolgt über den Datenspeicherung Resource Provider (SRP), eine Ebene, die den Zugriff von der zugrunde liegenden Topologie trennt und einen gemeinsamen Speicher für UGC unterstützt.

Weitere Informationen über die Persistenz von Community-Inhalten und empfohlene Bereitstellungen finden Sie unter:

* [Community Content Datenspeicherung](working-with-srp.md): beschreibt die verfügbaren Optionen für die SRP-Datenspeicherung für UGC
* [Empfohlene Topologien](topologies.md): diskutiert Topologien auf der Grundlage von Anwendungsfällen und SRP-Auswahl.
* [Upgrade auf AEM 6.3 Communities](upgrade.md): bietet nützliche Informationen zu UGC beim Wechsel zu AEM 6.3.

## Communities Konsolen {#communities-consoles}

In der Authoring-Umgebung bietet die globale Navigationskonsole Zugriff auf die Konsole [Communities](consoles.md), die Folgendes enthält:

* [Sites-Konsole](sites-console.md)

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * [Community ](groups.md) Groupsconsole

* [Moderatoren-Konsole](moderation.md)

   * Allgemeine Benutzeroberfläche für Massenmoderation für Autor- und Veröffentlichungsfunktionen
   * Neue Filterkriterien

* [Mitglieder und ](members.md) Groupsmanagement-Konsolen

   * Ermöglicht das Erstellen und Verwalten von Benutzern (Mitgliedern) auf der Veröffentlichungsseite über die Authoring-Umgebung
   * Möglichkeit zum Verbot von Mitgliedern
   * Ermöglicht das Erstellen und Verwalten von Benutzergruppen (Benutzergruppen) im Veröffentlichungsmodus aus der Umgebung des Autors

* [](reports.md) ReportConsole

   * Ermöglicht die Erstellung von Berichten zu Zuweisungen, Beiträgen und Ansichten

* [](resources.md) ResourceConsole

   * Bietet die Möglichkeit, Aktivierungsressourcen und Lernpfade zu erstellen
   * Ermöglicht Zugriff auf Berichte zu Aktivierungsressourcen und Lernpfaden

Die Konsole für globale Tools bietet Zugriff auf die folgenden Communities-Tools:

* [Site-](tools.md#sitetemplatesconsole) Vorlagenkonsole

   * Erstellen und Verwalten von Community-Site-Vorlagen

* [Group ](tools.md#grouptemplatesconsole) TemplatesConsole

   * Erstellen und Verwalten von Community-Gruppenvorlagen

* [Community ](tools.md#communityfunctionsconsole) FunctionsConsole

   * Community-Funktionen erstellen und verwalten

* [Datenspeicherung ](tools.md#storageconfiguratonconsole) ConfigurationConsole

   * Wählen Sie den [gemeinsamen Speicher](working-with-srp.md) für die Site aus und konfigurieren Sie ihn

* [Komponenten-Leitfaden](components-guide.md)

   * Eine Beispielsite, [Community-Komponenten](http://localhost:4502/editor.html/content/community-components/en.html), die eine Stichprobe aller Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit bereitstellt, mit ihnen zu experimentieren

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung einer Community-Site basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage, die aus Community-Funktionen und Community-Gruppenvorlagen besteht, bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Benutzerdaten, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

Siehe [Site-Vorlagenkonsole](sites.md).

## Community-Funktionen {#community-functions}

Die zu erwartenden Merkmale einer Community-Erfahrung sind bekannt. Mit AEM Communities sind diese Funktionen als Bausteine verfügbar, auch als Community-Funktionen bezeichnet.

Community-Funktionen sind normale AEM Seiten, die aus Komponenten bestehen, die zu einer Funktion verdrahtet sind, die leicht in eine Community-Site-Vorlage integriert werden kann.

Siehe [Community Functions console](functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht es einer Unter-Community, dynamisch innerhalb einer Community-Site von autorisierten Benutzern und Community-Mitgliedern aus Autor- und Veröffentlichungs-Umgebung erstellt zu werden.

Aus der Umgebung des Autors können Community-Gruppen (Untergruppen) innerhalb einer bestehenden Community-Site erstellt oder innerhalb einer vorhandenen Gruppe verschachtelt werden, wenn die Vorlagenstruktur die Funktion [Groups](functions.md#groups-function) enthält.

Das Erstellen einer Community-Gruppe erfordert die Auswahl einer Community-Gruppenvorlage, die das Design der Community-Gruppen-Seite(n) bereitstellt. Wenn eine Funktion &quot;Gruppen&quot;zu einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass entweder eine Gruppenvorlage angegeben wird oder eine Auswahl von Vorlagen zum Zeitpunkt der Erstellung einer neuen Community-Gruppe bereitgestellt wird.

Siehe auch:

* [Site-Gruppenkonsole](groups.md)  - Erstellen von Unter-Communities in der Authoring-Umgebung
* [Gruppenvorlagen-Konsole](tools-groups.md)  - Erstellen der Sitestruktur für Gruppen
* [Erste Schritte mit AEM Communities](getting-started.md)  - Lernprogramm zum schnellen Erstellen einer Community-Site mit verschachtelten Gruppen

## Community-Komponenten {#community-components}

Die [Community-Komponenten](author-communities.md), aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM Site hinzuzufügen.

Das Handbuch [Community-Komponenten](components-guide.md) steht für die interaktive Erforschung der Komponenten zur Verfügung.

## Communities-Typen {#types-of-communities}

### Einsatzgemeinschaft {#engagement-community}

Eine Interaktionsgemeinschaft ist eine Community-Site, auf der Kunden zur Information, zum Abrufen von Feedback und zur Interaktion mit Community-Mitgliedern eingeladen werden.

Zu den Funktionen einer Interaktionsgemeinschaft zählen:

* Anmeldung
* Messaging
* Foren
* Kommentare
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

Um eine neue Interaktionsgemeinschaft schnell zu erstellen, besuchen Sie [Erste Schritte mit AEM Communities](getting-started.md).

### Aktivierungs-Community {#enablement-community}

Eine Community-Community ist eine Community-Site, die Funktionen zum Online-Lernen enthält.

Zu den Funktionen einer Community für die Aktivierung gehören:

* Alle Funktionen einer [Einsatzgemeinschaft](#engagement-community)
* Möglichkeit, Mitgliedern und Mitgliedsgruppen Inhalte und Lernressourcen zuzuweisen
* Unterstützung von SCORM-Inhalten, z. B. Quiz und Tests
* Nachverfolgung des Abschlusses von Zuweisungen
* Zugriff auf Berichte und Analysen
* Möglichkeit, über eine Lernressource in Foren, Nachrichten, Kommentaren und Bewertungen zu sprechen

Eine Aktivierungs-Community kann erstellt werden, wenn das [Enablement-Add-on](enablement.md) konfiguriert ist. Dies erfordert zusätzliche Lizenzen für die Verwendung in einer Produktions-Umgebung. Eine Community-Site für Aktivierungszwecke enthält die Funktion [Zuweisungen](#community-functions).

Um die Erstellung einer neuen Community für die Aktivierung zu vereinfachen, besuchen Sie [Erste Schritte mit AEM Communities für die Aktivierung](getting-started-enablement.md).

## AEM Demo-Maschine {#aem-demo-machine}

Die [AEM-Demomaschine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) und [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms) aus, die oft mehr Setup erfordern als eine QuickStart-Instanz. Die AEM Demo Machine richtet weitere [Infrastruktur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) ein, wie MongoDB, Solr, MySQL, FFmpeg und E-Mail-Server.

Die AEM Demomaschine besteht aus

* A [grafische Benutzeroberfläche](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Apache ANT-Skripten mit konfigurierbaren [Eigenschaften](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) und [Zielgruppen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Zu installierende Pakete
Die AEM Demo Machine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 und AEM 6.3 unter Windows, MacOS und Linux getestet.

Für AEM Demo Machine ist eine gültige AEM Lizenz erforderlich.

>[!NOTE]
>
>Ansicht a [video introduction](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) to the AEM Demo Machine (13:26).

## AEM Communities-Dokumentation {#aem-communities-documentation}

* Weitere Informationen zu empfohlenen Bereitstellungen finden Sie unter [Bereitstellen von Communities](deploy-communities.md).

* Besuchen Sie [Sites für Administrationsgemeinschaften](administer-landing.md), um mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, das Taggen, Benachrichtigungen, das Scoring und Abzeichen zu erfahren.

* Besuchen Sie [Developing Communities](communities.md), um mehr über das Social-Komponenten-Framework (SCF) zu erfahren und Communities-Komponenten und -Funktionen anzupassen.

* Unter [Komponenten für Authoring-Communities](author-communities.md) erfahren Sie, wie Sie mit Communities-Komponenten erstellen und konfigurieren.

