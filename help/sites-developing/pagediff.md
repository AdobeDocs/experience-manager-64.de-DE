---
title: Entwicklung und Seitenvergleich
seo-title: Entwicklung und Seitenvergleich
description: Entwicklung und Seitenvergleich
seo-description: 'null'
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 73%

---


# Entwicklung und Seitenvergleich{#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Autoren möchten die aktuelle Seite mit einer vorherigen Version parallel vergleichen, wobei die Unterschiede hervorgehoben werden.

Mit dem Seitenvergleich können Benutzer die aktuelle Seite mit Launches, früheren Versionen usw. vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-authoring/page-diff.md).

## Details zum Vorgang {#operation-details}

Beim Vergleichen von Versionen einer Seite wird die vorherige Version, die der Benutzer vergleichen möchte, von AEM im Hintergrund neu erstellt, um den Vergleich zu erleichtern. Dies ist erforderlich, um den Inhalt für einen [direkten parallelen Vergleich](/help/sites-authoring/page-diff.md#presentation-of-differences) rendern zu können.

Dieser Wiederherstellungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert keinen Eingriff. Administratoren, die das Repository beispielsweise in CRX DE Lite anzeigen, sehen diese neu erstellten Versionen jedoch in der Inhaltsstruktur.

Je nach AEM Patch-Level ist das Verhalten unterschiedlich und erfordert möglicherweise bestimmte Berechtigungen, um ordnungsgemäß funktionieren zu können.

### Vor AEM 6.4.3 {#prior-to-aem}

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/content/versionhistory/<userId>/<site structure>`

Wenn Sie den Mechanismus zum Abweichen von Seiten verwenden, erstellt AEM die vorherige Version der Seite neu, damit die Funktion verwendet werden kann, muss der Benutzer über bestimmte JCR-Berechtigungen verfügen.

>[!CAUTION]
>
>Um die Funktion &quot;page diff&quot;verwenden zu können, muss der Benutzer über die Berechtigung **Ändern/Erstellen/Löschen** auf dem Knoten `/content/versionhistory` verfügen.

### Ab AEM 6.4.3 {#as-of-aem}

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Dieser Inhalt wird von einem Dienstbenutzer erstellt, der über die Berechtigung verfügt, die Sichtbarkeit auf den aktuellen Benutzer zu beschränken. Aus diesem Grund sind keine speziellen Berechtigungen erforderlich.

Es wird automatisch eine Bereinigungsaufgabe ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Entwicklerbeschränkungen {#developer-limitations}

In der klassischen Benutzeroberfläche mussten bisher besondere Entwicklungsabwägungen vorgenommen werden, um die AEM zu vereinfachen (z. B. `cq:text` tag lib oder benutzerspezifische Integration des `DiffService` OSGi-Dienstes in Komponenten). Für die neue Vergleichsfunktion ist dies nicht mehr notwendig, da sie clientseitig durch DOM-Vergleich ausgeführt wird.

Es gibt jedoch einige Einschränkungen, die der Entwickler beachten muss.

* Diese Funktion verwendet CSS-Klassen ohne Namespace im AEM-Produkt. Wenn andere benutzerdefinierte oder externe CSS-Klassen mit denselben Namen auf der Seite verwendet werden, kann dies die Anzeige des Vergleichs beeinflussen.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Da der Vergleich Client-seitig ist und beim Laden der Seite ausgeführt wird, werden keine Änderungen am DOM berücksichtigt, die vorgenommen wurden, nachdem der Cient-seitige Vergleichs-Service ausgeführt wurde. Dies kann Folgendes beeinflussen:

   * Komponenten, die AJAX verwenden, um Inhalte einzubeziehen
   * Single Page Applications
   * JavaScript-basierte Komponenten, die den DOM bei Benutzerinteraktionen manipulieren.

