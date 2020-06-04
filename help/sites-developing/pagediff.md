---
title: Entwicklung und Seitenvergleich
seo-title: Entwicklung und Seitenvergleich
description: 'null'
seo-description: 'null'
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 6de5e6f12f123ca2ec45358a138becc410c89e4e
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 46%

---


# Entwicklung und Seitenvergleich{#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Autoren möchten die aktuelle Seite mit einer vorherigen Version parallel vergleichen, wobei die Unterschiede hervorgehoben werden.

Mit dem Seitenvergleich können Benutzer die aktuelle Seite mit Launches, früheren Versionen usw. vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-authoring/page-diff.md).

## Vorgangsdetails {#operation-details}

Beim Vergleich von Versionen einer Seite wird die vorherige Version, die der Benutzer vergleichen möchte, von AEM im Hintergrund neu erstellt, um den Unterschied zu erleichtern. Dies ist erforderlich, damit der Inhalt [für einen Vergleich](/help/sites-authoring/page-diff.md#presentation-of-differences)nebeneinander gerendert werden kann.

Dieser Erholungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert kein Eingreifen. Administratoren, die das Repository beispielsweise in CRX DE Lite anzeigen, sehen diese neu erstellten Versionen jedoch in der Inhaltsstruktur.

Abhängig vom AEM-Patch-Level ist das Verhalten unterschiedlich und erfordert möglicherweise bestimmte Berechtigungen, um ordnungsgemäß funktionieren zu können.

### Vor AEM 6.4.3 {#prior-to-aem}

Beim Vergleich von Inhalten wird die gesamte Struktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/content/versionhistory/<userId>/<site structure>`

Da AEM beim Einsatz des Mechanismus zum Abweichen von Seiten die vorherige Version der Seite neu erstellt, muss der Benutzer über bestimmte JCR-Berechtigungen verfügen, um die Funktion verwenden zu können.

>[!CAUTION]
>
>Um die Funktion zum Trennen von Seiten verwenden zu können, muss der Benutzer über die Berechtigung zum **Ändern/Erstellen/Löschen** auf dem Knoten verfügen `/content/versionhistory`.

### Ab AEM 6.4.3 {#as-of-aem}

Beim Vergleich von Inhalten wird die gesamte Struktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Dieser Inhalt wird von einem Dienstbenutzer erstellt, der über die Berechtigung verfügt, die Sichtbarkeit auf den aktuellen Benutzer zu beschränken. Aus diesem Grund sind keine speziellen Berechtigungen erforderlich.

Eine Bereinigungs-Aufgabe wird automatisch ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Entwicklerbeschränkungen {#developer-limitations}

Previously, in Classic UI, special development consideration had to be made to facilitate AEM diffing (such as using `cq:text` tag lib, or custom integrating the `DiffService` OSGi service into components). Für die neue Vergleichsfunktion ist dies nicht mehr notwendig, da sie clientseitig durch DOM-Vergleich ausgeführt wird.

Es gibt jedoch einige Einschränkungen, die der Entwickler beachten muss.

* Diese Funktion verwendet CSS-Klassen ohne Namespace im AEM-Produkt. Wenn andere benutzerdefinierte oder externe CSS-Klassen mit denselben Namen auf der Seite verwendet werden, kann dies die Anzeige des Vergleichs beeinflussen.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Da der Vergleich clientseitig ist und beim Laden der Seite ausgeführt wird, werden keine Änderungen am DOM berücksichtigt, die vorgenommen wurden, nachdem der clientseitige Vergleichsdienst ausgeführt wurde. Dies kann Folgendes beeinflussen:

   * Komponenten, die AJAX verwenden, um Inhalte einzubeziehen
   * Einzelseiten-Webanwendungen
   * JavaScript-basierte Komponenten, die den DOM bei Benutzerinteraktionen manipulieren.

