---
title: Übersicht über AEM Communities
seo-title: Übersicht über AEM Communities
description: Überblick über AEM Communities-Funktionen und -Einrichtung
seo-description: Überblick über AEM Communities-Funktionen und -Einrichtung
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
exl-id: 3a8b21f8-75da-4867-9a8a-80fddf7946ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
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

AEM Communities ermöglicht die Entwicklung einer Beziehung zu Site-Besuchern, die über Blogs, Fragen und Antworten und Ereigniskalender informiert werden und gleichzeitig Einblicke durch Foren, Kommentare und andere Community-Inhalte erhalten, die häufig als benutzergenerierte Inhalte (UGC) bezeichnet werden.

Darüber hinaus ermöglicht AEM Communities die Moderation durch vertrauenswürdige Mitglieder in der Veröffentlichungsumgebung, die Anmeldung in sozialen Netzwerken mit Twitter und Facebook, die Inline-Übersetzung von Community-Inhalten, die Erstellung von Community-Gruppen von der veröffentlichten Community-Site, die Auswertung von Bewertungen zu Auszeichnungen, die Dateifreigabe, Benachrichtigungen und Aktivitäts-Streams.

Communities-Funktionen können mit der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki), die öffentlich auf GitHub.com verfügbar ist, oder mit der neuen We.Retail-Referenzimplementierung demonstriert werden.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM Site, die mit einem einfachen Assistenten erstellt wurde, was zu einer Website mit vielen allgemeinen Funktionen führt, die vorab an die Site angeschlossen sind.

Der [Website-Erstellungsassistent](sites-console.md):

* Assembliert Funktionen der Site, basierend auf der ausgewählten [Community-Site-Vorlage](sites.md), die
   * Erstellt aus [Community-Funktionen](#community-functions)
   * Optionale Funktion [Community-Gruppen](#communitygroups)
* Verwendet Einstellungen zum Konfigurieren von:
   * Moderation
   * Anmeldung
   * Übersetzung
* Bietet wichtige Funktionen:
   * Responsives Design: Verwendet [Twitter-Bootstrap-Designs](https://getbootstrap.com)
   * Anmelden: Selbstregistrierung, [Anmeldung in sozialen Netzwerken](social-login.md), Benutzerprofile
   * Benachrichtigungen: Mitglieder sehen Ereignisse, die für sie relevant sind
   * Messaging: Mitglieder können Nachrichten innerhalb der Community-Site senden oder empfangen
   * Suchen: Möglichkeit, innerhalb der Community-Site zu suchen
   * Sprachwechsel: Möglichkeit zur Auswahl einer Sprache für eine [mehrsprachige Site](../../help/sites-administering/translation.md)
   * Administration: Zugriff für autorisierte Mitglieder zur Moderation und Verwaltung von Benutzern auf der Community-Site
* Beseitigt viele Bearbeitungsschritte auf Seitenebene:
   * Branding: Optionaler Upload eines Bannerbilds für die Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü: Navigationslinks werden für die Funktionen bereitgestellt, die in der Community-Site-Vorlage enthalten sind

Um die schnelle Erstellung einer neuen Community-Site zu erleben, besuchen Sie [Erste Schritte mit AEM Communities](getting-started.md).

## Community-Inhaltsbeständigkeit {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, erfordert AEM Communities einen gemeinsamen Speicher, der speziell für benutzergenerierte Inhalte (UGC) verwendet wird, die von allen AEM (Autoren- und Veröffentlichungsinstanzen) gemeinsam verwendet werden.

Der Zugriff auf Community-Inhalte erfolgt über den Speicher-Ressourcenanbieter (SRP), der eine Ebene bereitstellt, um den Zugriff von der zugrunde liegenden Topologie zu trennen, und einen gemeinsamen Speicher für benutzergenerierte Inhalte unterstützt.

Weitere Informationen zur Persistenz von Community-Inhalten und zu empfohlenen Bereitstellungen finden Sie unter:

* [Community-Inhaltsspeicherung](working-with-srp.md): beschreibt die verfügbaren SRP-Speicheroptionen für UGC
* [Empfohlene Topologien](topologies.md): Erörtert Topologien basierend auf Anwendungsfall und SRP-Auswahl
* [Aktualisierung auf AEM 6.3 Communities](upgrade.md): bietet nützliche Informationen zu benutzergenerierten Inhalten beim Wechsel zu AEM 6.3.

## Communities-Konsolen {#communities-consoles}

In der Autorenumgebung bietet die globale Navigationskonsole Zugriff auf die [Communities-Konsole](consoles.md), die Folgendes enthält:

* [Sites-Konsole](sites-console.md)

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * [Community-](groups.md) Gruppenkonsole

* [Moderatoren-Konsole](moderation.md)

   * Allgemeine Benutzeroberfläche für Massenmoderation für Autoren- und Veröffentlichungsumgebungen
   * Neue Filterkriterien

* [Mitglieder und ](members.md) Groupsmanagement-Konsolen

   * Ermöglicht das Erstellen und Verwalten von Benutzern (Mitgliedern) auf der Veröffentlichungsseite in der Autorenumgebung
   * Möglichkeit, Mitglieder zu verbieten
   * Ermöglicht die Erstellung und Verwaltung von auf der Veröffentlichungsseite befindlichen Benutzergruppen (Mitgliedergruppen) in der Autorenumgebung

* [](reports.md) ReportConsole

   * Ermöglicht die Erstellung von Berichten über Zuweisungen, Beiträge und Ansichten

* [](resources.md) Ressourcenkonsole

   * Ermöglicht das Erstellen von Aktivierungsressourcen und Lernpfaden
   * Ermöglicht Zugriff auf Berichte zu Aktivierungsressourcen und Lernpfaden

Die globale Tools-Konsole bietet Zugriff auf die folgenden Communities-Tools:

* [Site-](tools.md#sitetemplatesconsole) Vorlagenkonsole

   * Erstellen und Verwalten von Community-Site-Vorlagen

* [Gruppenvorlagen-](tools.md#grouptemplatesconsole) Konsole

   * Erstellen und Verwalten von Community-Gruppenvorlagen

* [Community ](tools.md#communityfunctionsconsole) Functions Console

   * Community-Funktionen erstellen und verwalten

* [Speicherkonfigurationskonsole ](tools.md#storageconfiguratonconsole) 

   * Wählen Sie den [gemeinsamen Speicher](working-with-srp.md) für die Site aus und konfigurieren Sie ihn.

* [Komponenten-Leitfaden](components-guide.md)

   * Eine Beispielsite, [Community-Komponenten](http://localhost:4502/editor.html/content/community-components/en.html), die eine Stichprobe aller Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit bietet, mit ihnen zu experimentieren

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung von Community-Sites basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage bestehend aus Community-Funktionen und Community-Gruppenvorlagen bietet die Struktur für eine Community-Site, einschließlich Anmelde-, Benutzer-, Messaging-, Site-Menü-, Such-, Themen- und Branding-Funktionen.

Siehe [Site-Vorlagen-Konsole](sites.md).

## Community-Funktionen {#community-functions}

Die von einer Community-Erfahrung erwarteten Funktionen sind bekannt. Mit AEM Communities sind diese Funktionen als Bausteine verfügbar, die als Community-Funktionen bezeichnet werden.

Community-Funktionen sind normale AEM Seiten, die aus Komponenten bestehen, die zu einer Funktion verbunden sind, die einfach in eine Community-Site-Vorlage integriert werden kann.

Siehe [Community Functions Console](functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht die dynamische Erstellung einer Unter-Community auf einer Community-Site durch autorisierte Benutzer und Community-Mitglieder aus der Autoren- und Veröffentlichungsumgebung.

In der Autorenumgebung können Community-Gruppen (Untergruppen) innerhalb einer vorhandenen Community-Site erstellt oder in einer vorhandenen Gruppe verschachtelt werden, wenn die Struktur der Vorlage die [Gruppenfunktion](functions.md#groups-function) enthält.

Das Erstellen einer Community-Gruppe erfordert die Auswahl einer Community-Gruppenvorlage, die das Design der Community-Gruppen-Seite(n) bereitstellt. Wenn eine Gruppenfunktion einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass entweder eine Gruppenvorlage angegeben oder zum Zeitpunkt der Erstellung einer neuen Community-Gruppe eine Auswahl an Vorlagen bereitgestellt wird.

Siehe auch:

* [Site-Gruppen-Konsole](groups.md)  - Erstellen von Untergruppen in der Autorenumgebung
* [Gruppenvorlagen-Konsole](tools-groups.md)  - Erstellen der Site-Struktur für Gruppen
* [Erste Schritte mit AEM Communities](getting-started.md)  - Tutorial zum schnellen Erstellen einer Community-Site mit verschachtelten Gruppen

## Community-Komponenten {#community-components}

Die [Community-Komponenten](author-communities.md), aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM Site hinzuzufügen.

Das [Handbuch zu Community-Komponenten](components-guide.md) ist für die interaktive Untersuchung der Komponenten verfügbar.

## Communities-Typen {#types-of-communities}

### Interaktionsgemeinschaft {#engagement-community}

Eine Interaktionsgemeinschaft ist eine Community-Site, auf der Kunden zur Information, zum Abruf von Feedback und zur Interaktion als Community-Mitglieder angesprochen werden.

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
* Scoring und Abzeichen
* Analytics-Reporting

Um schnell eine neue Interaktionsgemeinschaft zu erstellen, besuchen Sie [Erste Schritte mit AEM Communities](getting-started.md).

### Aktivierungs-Community {#enablement-community}

Eine Aktivierungs-Community ist eine Community-Site, die Funktionen für Online-Lernen enthält.

Zu den Funktionen einer Aktivierungs-Community zählen:

* Alle Funktionen einer [Interaktionsgemeinde](#engagement-community)
* Möglichkeit, Mitgliedern und Mitgliedergruppen Inhalte und Lernressourcen zuzuweisen
* Unterstützt SCORM-Inhalte wie Quizze und Tests
* Verfolgen des Zuweisungsabschlusses
* Zugriff auf Reporting und Analysen
* Möglichkeit, über Foren, Nachrichten, Kommentare und Bewertungen über eine Lernressource zu sprechen

Eine Aktivierungs-Community kann erstellt werden, wenn das [Aktivierungs-Add-on](enablement.md) konfiguriert ist. Dies erfordert zusätzliche Lizenzen für die Verwendung in einer Produktionsumgebung. Eine Aktivierungs-Community-Site enthält die [Zuweisungsfunktion](#community-functions).

Um die Erstellung einer neuen Aktivierungs-Community zu vereinfachen, besuchen Sie [Erste Schritte mit AEM Communities für die Aktivierung](getting-started-enablement.md).

## AEM Demomaschine {#aem-demo-machine}

Die [AEM-Demomaschine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) und [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms) aus, die häufig mehr Setup erfordern als lediglich eine QuickStart-Instanz. Die AEM Demo Machine richtet zusätzliche [Infrastruktur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) ein, wie MongoDB-, Solr-, MySQL-, FFmpeg- und E-Mail-Server.

Die AEM Demomaschine besteht aus

* Eine [grafische Benutzeroberfläche](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Apache ANT-Skripte mit konfigurierbaren [Eigenschaften](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) und [Zielgruppen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Zu installierende Pakete
Die AEM Demo Machine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 und AEM 6.3 unter Windows, MacOS und Linux getestet.

Für AEM Demo Machine ist eine gültige AEM Lizenz erforderlich.

>[!NOTE]
>
>Zeigen Sie eine [Videoeinführung](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) zur AEM Demomaschine an (13:26).

## Dokumentation zu AEM Communities {#aem-communities-documentation}

* Besuchen Sie [Communities bereitstellen](deploy-communities.md) , um mehr über empfohlene Bereitstellungen zu erfahren.

* Besuchen Sie [Verwalten von Communities-Sites](administer-landing.md) , um mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, Tagging, Benachrichtigungen, Scoring und Abzeichen zu erfahren.

* Besuchen Sie [Communities entwickeln](communities.md) , um mehr über das Social-Komponenten-Framework (SCF) zu erfahren und Communities-Komponenten und -Funktionen anzupassen.

* Besuchen Sie [Erstellen von Communities-Komponenten](author-communities.md) , um zu erfahren, wie Sie Communities-Komponenten erstellen und konfigurieren.
