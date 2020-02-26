---
title: Suchen
seo-title: Suchen
description: Rasches Auffinden Ihrer Inhalte dank umfassender Suchfunktionen
seo-description: Rasches Auffinden Ihrer Inhalte dank umfassender Suchfunktionen
uuid: 1e80cf85-653f-4dde-930a-de05415b994f
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: cd87e1e8-5329-4e60-ac9d-2705f54d0da6
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Suche{#search-features}

Die Autorenumgebung von AEM bietet abhängig vom Ressourcentyp verschiedene Möglichkeiten zur Inhaltssuche.

>[!NOTE]
>
>Außerhalb der Autorenumgebung stehen auch andere Verfahren für die Suche zur Verfügung, wie der [Query Builder](/help/sites-developing/querybuilder-api.md) und [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Grundlagen zur Suche {#search-basics}

Die Suchfunktion ist über die obere Symbolleiste verfügbar:

![](do-not-localize/chlimage_1-17.png)

Die Suchleiste bietet Ihnen folgende Möglichkeiten:

* Suchen nach einem bestimmten Keyword, Pfad oder Tag. 
* Filtern nach ressourcenspezifischen Kriterien, wie Änderungsdatumsangaben, Seitenstatus, Dateigröße usw.
* Definieren und Verwenden einer [gespeicherten Suche](#saved-searches), die auf den oben genannten Kriterien basiert.

>[!NOTE]
>
>Search can also be invoked by using the hotkey `/` (forward slash) whenever the search rail is visible.

## Suchen und Filtern {#search-and-filter}

So durchsuchen und filtern Sie Ressourcen: 

1. Öffnen Sie die Option **Suchen** (mit der Lupe in der Symbolleiste) und geben Sie den Suchbegriff ein. Es werden Empfehlungen angezeigt, die Sie dann auswählen können:

   ![screen_shot_2018-03-23at101404](assets/screen_shot_2018-03-23at101404.png)

   Standardmäßig sind die Suchergebnisse auf den aktuellen Speicherort beschränkt (d. h. Konsole und Ressourcentyp): 

   ![screen_shot_2018-03-23at101445](assets/screen_shot_2018-03-23at101445.png)

1. Falls erforderlich, können Sie den Positionsfilter entfernen (wählen Sie dazu **X** neben dem Filter aus, den Sie entfernen möchten), um alle Konsolen/Ressourcentypen zu durchsuchen.
1. Die Ergebnisse werden angezeigt, und zwar gruppiert nach Konsole und Ressourcentyp.

   Sie können entweder eine spezifische Ressource (für eine spätere Aktion) oder eine Drilldown-Suche auswählen, indem Sie den erforderlichen Ressourcentyp auswählen, z. B. **Alle Sites anzeigen**: 

   ![screen_shot_2018-03-23at101523](assets/screen_shot_2018-03-23at101523.png)

1. Wenn Sie weitere Details anzeigen möchten, wählen Sie das Symbol für die Seitenleiste (oben links) aus, um den Seitenbereich **Filter und Optionen** zu öffnen.

   ![](do-not-localize/screen_shot_2018-03-23at101542.png)

   Je nach Ressourcentyp zeigt die Suche eine vordefinierte Auswahl von Such-/Filterkriterien an.

   Im Seitenbereich können Sie folgende Elemente auswählen:

   * Gespeicherte Suchvorgänge
   * Verzeichnisse, die durchsucht werden sollen
   * Tags
   * Suchkriterien, z. B. Änderungsdatum, Veröffentlichungsstatus, Live Copy-Status. 
   >[!NOTE]
   >
   >Die Suchkriterien können variieren:
   >
   >* abhängig vom ausgewählten Ressourcentyp – beispielsweise sind die Kriterien „Assets“ und „Communities“ nach Themen spezialisiert.
   >* je nach Instanz, da die [Suchformulare](/help/sites-administering/search-forms.md) (entsprechend der Stelle in AEM) angepasst werden können.


   ![screen_shot_2018-03-23at101619](assets/screen_shot_2018-03-23at101619.png)

1. Sie können auch zusätzliche Suchbegriffe hinzufügen: 

   ![screen_shot_2018-03-23at101710](assets/screen_shot_2018-03-23at101710.png)

1. Schließen Sie die **Suche** mit dem **X** (oben rechts).

>[!NOTE]
>
>Die Suchkriterien werden bei Auswahl eines Elements in den Suchergebnissen beibehalten.
>
>Bei Auswahl eines Elements auf der Seite mit den Suchergebnissen bleiben die Suchkriterien erhalten, wenn Sie über die Zurück-Schaltfläche des Browsers zur Suchseite zurückkehren.

## Saved Searches {#saved-searches}

Sie können nicht nur nach zahlreichen Facetten suchen, sondern auch eine bestimmte Suchkonfiguration speichern, um diese später abzurufen und zu verwenden:

1. Definieren Sie die Suchkriterien und wählen Sie **Speichern**.

   ![screen_shot_2018-03-23at101710-1](assets/screen_shot_2018-03-23at101710-1.png)

1. Weisen Sie einen Namen zu und wählen Sie **Speichern** zur Bestätigung:

   ![screen_shot_2018-03-23at101852](assets/screen_shot_2018-03-23at101852.png)

1. Die gespeicherte Suche ist außerdem in der Auswahl verfügbar, wenn Sie das nächste Mal auf den Suchbereich zugreifen:

   ![screen_shot_2018-03-23at102128](assets/screen_shot_2018-03-23at102128.png)

1. Nach dem Speichern können Sie:

   * **x** (für den Namen der gespeicherten Suche) verwenden, um eine neue Abfrage zu starten. Die gespeicherte Suche selbst wird nicht gelöscht.
   * die Option **Gespeicherte Suche bearbeiten** verwenden, die Suchbedingungen ändern und dann erneut auf **Speichern** klicken.

Gespeicherte Suchen können geändert werden, indem Sie die gespeicherte Suche auswählen und unten im Suchfeld auf **Gespeicherte Suche bearbeiten** klicken.

![screen_shot_2018-03-23at102213](assets/screen_shot_2018-03-23at102213.png)

