---
title: Entwicklung und Seitenvergleich
seo-title: Developing and Page Diff
description: Entwicklung und Seitenvergleich
seo-description: null
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
exl-id: 365e944d-d8a3-4f4e-8925-88629845232f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 79%

---

# Entwicklung und Seitenvergleich{#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Autoren möchten die aktuelle Seite mit einer vorherigen Version parallel vergleichen, wobei die Unterschiede hervorgehoben werden.

Mit dem Seitenvergleich können Benutzer die aktuelle Seite mit Launches, früheren Versionen usw. vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-authoring/page-diff.md).

## Details zum Vorgang {#operation-details}

Beim Vergleichen von Versionen einer Seite wird die vorherige Version, die der Benutzer vergleichen möchte, von AEM im Hintergrund neu erstellt, um den Vergleich zu erleichtern. Dies ist erforderlich, um den Inhalt für einen [direkten parallelen Vergleich](/help/sites-authoring/page-diff.md#presentation-of-differences) rendern zu können.

Dieser Wiederherstellungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert keinen Eingriff. Administratoren, die das Repository beispielsweise in CRX DE Lite anzeigen, sehen diese neu erstellten Versionen jedoch in der Inhaltsstruktur.

Abhängig von der AEM Patch-Ebene ist das Verhalten unterschiedlich und erfordert möglicherweise bestimmte Berechtigungen, um ordnungsgemäß zu funktionieren.

### Vor AEM 6.4.3 {#prior-to-aem}

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/content/versionhistory/<userId>/<site structure>`

Da bei Verwendung des Seitenvergleichsmechanismus AEM die vorherige Version der Seite neu erstellt wird, muss der Benutzer über bestimmte JCR-Berechtigungen verfügen, um die Funktion verwenden zu können.

>[!CAUTION]
>
>Um die Seitenvergleichsfunktion verwenden zu können, muss der Benutzer über die **Ändern/Erstellen/Löschen** Berechtigung auf dem Knoten `/content/versionhistory`.

### Ab AEM 6.4.3 {#as-of-aem}

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Dieser Inhalt wird von einem Dienstbenutzer erstellt, der über Berechtigungen verfügt, die die Sichtbarkeit auf den aktuellen Benutzer beschränken. Aus diesem Grund sind keine speziellen Berechtigungen erforderlich.

Es wird automatisch eine Bereinigungsaufgabe ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Entwicklerbeschränkungen {#developer-limitations}

Früher in der klassischen Benutzeroberfläche musste bei der Entwicklung besondere Rücksicht genommen werden, um die AEM-Vergleichsfunktion zu unterstützen (z. B. die Verwendung der Tag-Bibliothek `cq:text` oder eine individuelle Integration des OSGi-Dienstes `DiffService` in Komponenten). Für die neue Vergleichsfunktion ist dies nicht mehr notwendig, da sie Client-seitig durch DOM-Vergleich ausgeführt wird.

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
