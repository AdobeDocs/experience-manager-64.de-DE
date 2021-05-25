---
title: Grundlagen zu Communities-Komponenten
seo-title: Grundlagen zu Communities-Komponenten
description: Hinzufügen von Communities-Funktionen zu AEM Sites im Bearbeitungsmodus und Konfigurieren von Komponenten
seo-description: Hinzufügen von Communities-Funktionen zu AEM Sites im Bearbeitungsmodus und Konfigurieren von Komponenten
uuid: c017a7c5-40d1-4592-9317-96fd727dac86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 21714581-7645-4b47-a9b0-9f1424013240
exl-id: 17fbee1c-5657-442a-8c9d-1456b853f666
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 61%

---

# Grundlagen zu Communities-Komponenten {#communities-components-basics}

## Überblick {#overview}

Im Autorenabschnitt der Dokumentation finden Sie Informationen zum Hinzufügen von Communities-Funktionen zu AEM Sites im Bearbeitungsmodus sowie eine Beschreibung der Komponentenkonfigurationen.

Komponenten können mithilfe einer AEM-Instanz und dem interaktiven [Handbuch zu Community-Komponenten](components-guide.md) untersucht werden.

## Auf Communities-Komponenten zugreifen {#accessing-communities-components}

Wenn Sie Seiteninhalte verfassen und die zugrunde liegende Vorlage Änderungen am Design der Seite zulässt, können Komponenten aktiviert werden, die im Komponenten-Browser noch nicht als Teil des Seitendesigns verfügbar sind.

Die verfügbaren Communities-Komponenten sind [hier](author-communities.md#available-communities-components) aufgeführt.

>[!NOTE]
>
>Allgemeine Informationen zum Authoring finden Sie in der [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation zu [Grundlegender Umgang](../../help/sites-authoring/basic-handling.md).

### Designmodus aktivieren {#entering-design-mode}

Wenn keine **Communities**-Komponente im Komponenten-Browser (Sidekick) gefunden wird, müssen Sie `Design Mode` eingeben, um weitere Communities-Komponenten hinzuzufügen. Möglicherweise müssen Sie zudem [erforderliche Client-seitige Bibliotheken](#required-clientlibs) (clientlibs) hinzufügen.

Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](../../help/sites-authoring/default-components-designmode.md).

Im Folgenden finden Sie Bilder zur Auswahl einiger Communities-Komponenten und deren Anzeige im Komponenten-Browser:

![chlimage_1-424](assets/chlimage_1-424.png)

Die ausgewählten Komponenten werden jetzt im Komponenten-Browser angezeigt:

![chlimage_1-425](assets/chlimage_1-425.png)

## Erforderliche Clientlibs {#required-clientlibs}

[Client-seitige Bibliotheken](../../help/sites-developing/clientlibs.md) (clientlibs) werden für die ordnungsgemäße Ausführung (JavaScript) und Formatierung (CSS) der Komponenten benötigt.

Wird eine Communities-Komponente einer Seite hinzugefügt und führt dies zur Ausgabe einer Fehlermeldung sowie einem unerwarteten Layoutergebnis, sollte zunächst überprüft werden, ob die für die Communities-Komponente erforderlichen clientlibs hinzugefügt wurden. Weitere Informationen finden Sie unter [Clientlibs für Communities-Komponenten](clientlibs.md).

### Beispiel: Ursprünglich platzierte Bewertungen ohne Client-Bibliotheken.. {#example-initially-placed-reviews-without-client-libraries}

![chlimage_1-426](assets/chlimage_1-426.png)

### ... Und mit Client-Bibliotheken {#and-with-client-libraries}

![chlimage_1-427](assets/chlimage_1-427.png)

## Tagging {#tagging}

Viele Communities-Funktionen lassen sich so konfigurieren, dass Mitglieder veröffentlichte (gepostete) Inhalte in der Veröffentlichungsumgebung taggen können.

Ist das Tagging von Inhalten freigeschaltet, werden die für Mitglieder in der Veröffentlichungsumgebung verfügbaren Namespaces möglicherweise durch die Konfiguration der Community-Site beschränkt. Informationen hierzu finden Sie in der [Community-Sites-Konsole](sites-console.md#tagging).

Funktionen, die Tagging ermöglichen: [blog](blog-feature.md), [calendar](calendar.md), [Dateibibliothek](file-library.md), [Forum](forum.md)

Funktionen, die Tags verwenden: [catalog](catalog.md), [search](search.md), [Social Tag Cloud](tagcloud.md)

Informationen zum Verfassen:

* [Verwenden von Tags](../../help/sites-authoring/tags.md)

Verwaltungsinformationen:

* Erstellen von Tag-Namespaces (Taxonomie): [Verwalten von Tags](../../help/sites-administering/tags.md)
* Community-Site-Konfiguration: siehe [TAGGING](sites-console.md#tagging)
* [Tagging benutzergenerierter Inhalte](../../help/sites-authoring/tags.md)
* [Tagging von Aktivierungsressourcen](tag-resources.md)

Entwicklerinformationen:

* [AEM-Tagging-Framework](../../help/sites-developing/framework.md)
* [Tagging-Grundlagen](tag.md)
