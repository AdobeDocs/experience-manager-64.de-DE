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

## Communities - Funktionen {#communities-features}

AEM Communities ermöglicht die Entwicklung einer Beziehung zu Site-Besuchern, die über Blogs, Q&amp;A- und Ereignis-Kalender informiert werden und gleichzeitig Einblicke in Foren, Kommentare und andere Community-Inhalte gewinnen, die häufig als benutzergenerierte Inhalte (UGC) bezeichnet werden.

Darüber hinaus ermöglicht AEM Communities die Moderation durch vertrauenswürdige Mitglieder in der Veröffentlichungs-Umgebung, die Anmeldung in sozialen Netzwerken mit Twitter und Facebook, die Inline-Übersetzung von Community-Inhalten, die Erstellung von Community-Gruppen von der veröffentlichten Community-Site aus, die Bewertung von Auszeichnungen, Dateifreigabe, Benachrichtigungen und Aktivitäten-Streams.

Communities Features können mithilfe der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) , die öffentlich auf GitHub.com verfügbar ist, oder mit der neuen We.Retail Referenzimplementierung demonstriert werden.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM Site, die mit einem einfachen Assistenten erstellt wurde, der zu einer Website mit vielen allgemeinen Funktionen führt, die bereits mit der Site verkabelt sind.

Der [Site-Erstellungsassistent](sites-console.md):

* Assembliert Funktionen der Site, basierend auf der ausgewählten [Community-Site-Vorlage](sites.md) , die
   * Basiert auf [Community-Funktionen](#community-functions)
   * Optionale [Community-Gruppen](#communitygroups) -Funktion
* Verwendet Einstellungen zum Konfigurieren:
   * Moderation
   * Anmeldung
   * Übersetzung
* Bietet wichtige Funktionen:
   * Responsive Design: Verwendet [Twitter-Bootstrap-Themen](https://getbootstrap.com)
   * Anmelden: Selbstregistrierung, [Anmeldung](social-login.md)in sozialen Netzwerken, Profile von Benutzern
   * Benachrichtigungen: Die Abgeordneten sehen Ereignisse, die für sie relevant sind
   * Messaging: Mitglieder können innerhalb der Community-Site Nachrichten senden oder empfangen
   * Suchen: Möglichkeit der Suche innerhalb der Community-Site
   * Sprachwechsel: Möglichkeit zur Auswahl einer Sprache für eine [mehrsprachige Site](../../help/sites-administering/translation.md)
   * Verwaltung: Zugriff für autorisierte Mitglieder zur Moderation und Verwaltung von Benutzern auf der Community-Site
* Dadurch werden viele Authoring-Schritte auf Seitenebene vermieden:
   * Branding: Optionales Hochladen eines Bannerbilds zur Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü: Navigationslinks werden für die Funktionen bereitgestellt, die in der Community-Site-Vorlage enthalten sind

Um eine neue Community-Site schnell zu erstellen, besuchen Sie [Erste Schritte mit AEM Communities](getting-started.md).

## Persistenz von Gemeinschaftsinhalten {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, benötigt AEM Communities einen gemeinsamen Store speziell für benutzergenerierte Inhalte (UGC), die von allen AEM (Autor- und Veröffentlichungsinstanzen) freigegeben werden.

Der Zugriff auf Community-Inhalte erfolgt über den Datenspeicherung Resource Provider (SRP), eine Ebene, die den Zugriff von der zugrunde liegenden Topologie trennt und einen gemeinsamen Speicher für UGC unterstützt.

Weitere Informationen über die Persistenz von Community-Inhalten und empfohlene Bereitstellungen finden Sie unter:

* [Community Content Datenspeicherung](working-with-srp.md): beschreibt die verfügbaren Optionen für die SRP-Datenspeicherung für UGC
* [Empfohlene Topologien](topologies.md): diskutiert Topologien auf der Grundlage von Anwendungsfällen und SRP-Auswahl.
* [Upgrade auf AEM 6.3 Communities](upgrade.md): bietet nützliche Informationen zu UGC beim Wechsel zu AEM 6.3.

## Communities Konsolen {#communities-consoles}

In der Authoring-Umgebung bietet die globale Navigationskonsole Zugriff auf die [Communities-Konsole](consoles.md), die Folgendes enthält:

* [Sites-Konsole](sites-console.md)

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * [Community Groups](groups.md) Console

* [Moderatoren-Konsole](moderation.md)

   * Allgemeine Benutzeroberfläche für Massenmoderation für Autor- und Veröffentlichungsfunktionen
   * Neue Filterkriterien

* [Mitglieder und Gruppen](members.md) - Verwaltungskonsolen

   * Ermöglicht das Erstellen und Verwalten von Benutzern (Mitgliedern) auf der Veröffentlichungsseite über die Authoring-Umgebung
   * Möglichkeit zum Verbot von Mitgliedern
   * Ermöglicht das Erstellen und Verwalten von Benutzergruppen (Benutzergruppen) im Veröffentlichungsmodus aus der Umgebung des Autors

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

* [Datenspeicherung Configuration](tools.md#storageconfiguratonconsole) Console

   * Auswählen und Konfigurieren des [gemeinsamen Speichers](working-with-srp.md) für die Site

* [Komponenten-Leitfaden](components-guide.md)

   * Eine Beispielsite, [Community-Komponenten](http://localhost:4502/editor.html/content/community-components/en.html), die eine Stichprobe aller Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit bietet, mit ihnen zu experimentieren

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung einer Community-Site basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage, die aus Community-Funktionen und Community-Gruppenvorlagen besteht, bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Benutzerdaten, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

Siehe [Site-Vorlagenkonsole](sites.md).

## Community-Funktionen {#community-functions}

Die zu erwartenden Merkmale einer Community-Erfahrung sind bekannt. Mit AEM Communities sind diese Funktionen als Bausteine verfügbar, auch als Community-Funktionen bezeichnet.

Community-Funktionen sind normale AEM Seiten, die aus Komponenten bestehen, die zu einer Funktion verdrahtet sind, die leicht in eine Community-Site-Vorlage integriert werden kann.

See the [Community Functions console](functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht es einer Unter-Community, dynamisch innerhalb einer Community-Site von autorisierten Benutzern und Community-Mitgliedern aus Autor- und Veröffentlichungs-Umgebung erstellt zu werden.

Aus der Autorenfunktion können Community-Gruppen (Untergruppen) innerhalb einer bestehenden Community-Umgebung erstellt oder in einer vorhandenen Gruppe verschachtelt werden, wenn die Vorlagenstruktur die [Gruppenfunktion](functions.md#groups-function)enthält.

Das Erstellen einer Community-Gruppe erfordert die Auswahl einer Community-Gruppenvorlage, die das Design der Community-Gruppen-Seite(n) bereitstellt. Wenn eine Funktion &quot;Gruppen&quot;zu einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass entweder eine Gruppenvorlage angegeben wird oder eine Auswahl von Vorlagen zum Zeitpunkt der Erstellung einer neuen Community-Gruppe bereitgestellt wird.

Siehe auch:

* [Site-Gruppenkonsole](groups.md) - Erstellen von Unter-Communities in der Authoring-Umgebung
* [Gruppenvorlagen-Konsole](tools-groups.md) - Erstellen der Sitestruktur für Gruppen
* [Erste Schritte mit AEM Communities](getting-started.md) - Lernprogramm zum schnellen Erstellen einer Community-Site mit verschachtelten Gruppen

## Community-Komponenten {#community-components}

Die [Community-Komponenten](author-communities.md) , aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM Site hinzuzufügen.

Der Leitfaden [zu](components-guide.md) Community-Komponenten steht zur interaktiven Erforschung der Komponenten zur Verfügung.

## Arten von Gemeinschaften {#types-of-communities}

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

Besuchen Sie [Erste Schritte mit AEM Communities](getting-started.md), um schnell eine neue Interaktionsgemeinschaft zu erstellen.

### Aktivierungsgemeinschaft {#enablement-community}

Eine Community-Community ist eine Community-Site, die Funktionen zum Online-Lernen enthält.

Zu den Funktionen einer Community für die Aktivierung gehören:

* Alle Funktionen einer [Interaktionsgemeinschaft](#engagement-community)
* Möglichkeit, Mitgliedern und Mitgliedsgruppen Inhalte und Lernressourcen zuzuweisen
* Unterstützung von SCORM-Inhalten, z. B. Quiz und Tests
* Nachverfolgung des Abschlusses von Zuweisungen
* Zugriff auf Berichte und Analysen
* Möglichkeit, über eine Lernressource in Foren, Nachrichten, Kommentaren und Bewertungen zu sprechen

Wenn das [Enablement-Add-on konfiguriert](enablement.md)ist, kann eine Community für die Aktivierung erstellt werden. Dies erfordert zusätzliche Lizenzen für die Verwendung in einer Produktions-Umgebung. Eine Community-Site für die Aktivierung enthält die [Zuweisungsfunktion](#community-functions).

Um die Erstellung einer neuen Community für die Aktivierung zu vereinfachen, besuchen Sie [Erste Schritte mit AEM Communities für die Aktivierung](getting-started-enablement.md).

## AEM {#aem-demo-machine}

Die [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) [](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)undFormsaus, die häufig mehr Setup erfordern als das Starten einer QuickStart-Instanz. Die AEM Demo Machine richtet zusätzliche [Infrastruktur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) wie MongoDB, Solr, MySQL, FFmpeg und E-Mail-Server ein.

Die AEM Demomaschine besteht aus

* Eine [grafische Benutzeroberfläche](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Apache ANT-Skripten mit konfigurierbaren [Eigenschaften](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) und [Zielgruppen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Pakete zur InstallationDie AEM Demo Machine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 und AEM 6.3 unter Windows, MacOS und Linux getestet.

Für AEM Demo Machine ist eine gültige AEM Lizenz erforderlich.

>[!NOTE]
>
>Ansicht einer [Videovorstellung](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) zur AEM Demomaschine (13:26).

## AEM Communities-Dokumentation {#aem-communities-documentation}

* Visit [Deploying Communities](deploy-communities.md) to learn about recommended deployments.

* Besuchen Sie [Administering Communities Sites](administer-landing.md) , um mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, das Tagging, Benachrichtigungen, das Scoring und Abzeichen zu erfahren.

* Visit [Developing Communities](communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.

* Unter [Authoring Communities-Komponenten](author-communities.md) erfahren Sie, wie Sie Communities-Komponenten erstellen und konfigurieren.

