---
title: Analysieren der Seitenleistung
seo-title: Analyzing Page Performance
description: Verwenden Sie die Seite "Content Insight", um die Leistung der Seite zu analysieren, die Sie erstellen.
seo-description: Use the Content Insight page to analyze the performance of the page that you are authoring
uuid: 6b8a489d-f262-495d-adff-125c9a2c49b9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: ead74e39-3b07-488e-aeb1-fcb4aa6ff200
exl-id: dc24edaf-ca1d-4a6b-a2dc-86677267e18d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 24%

---

# Analysieren der Seitenleistung{#analyzing-page-performance}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Öffnen Sie die [Content Insight](/help/sites-authoring/content-insights.md) Seite, um die Leistung der Seite zu analysieren, die Sie erstellen. Konfigurieren Sie den Berichtszeitraum, um Ihre Analyse zu fokussieren.

## Öffnen von Analytics und Recommendations für eine Seite {#opening-analytics-and-recommendations-for-a-page}

Gehen Sie wie folgt vor, um Analytics und Recommendations für eine Seite anzuzeigen:

1. Navigieren Sie zu der Seite, die Sie analysieren möchten.
1. Klicken oder tippen Sie in der Symbolleiste auf **Analysen und Empfehlungen**.

   >[!NOTE]
   >
   >Analysen und Empfehlungen für eine Seite werden nur dann angezeigt, wenn AEM zur [Integration mit Adobe Analytics](/help/sites-administering/adobeanalytics-connect.md) konfiguriert wurde.

   ![screen_shot_2017-11-29at135651](assets/screen_shot_2017-11-29at135651.png)

## Ändern des Berichtszeitraums {#changing-the-reporting-period}

Ändern Sie die folgenden zeitbezogenen Aspekte der Analyseberichte:

* Der Zeitraum, in dem die Meldung erfolgen soll.
* Die Granularität der Daten.

Die Tools zum Ändern der zeitbezogenen Aspekte der Berichte werden oben auf der Inhaltseinblick-Seite angezeigt. ![chlimage_1-249](assets/chlimage_1-249.png)

### Ändern des Berichtszeitraums {#changing-the-reporting-period-1}

Ändern Sie den Berichtszeitraum der Seite &quot;Content Insight&quot;, um Ihre Analyse der Seitenaktivität auf einen bestimmten Zeitraum zu konzentrieren. Wenn Sie den Berichtszeitraum ändern, wird der Bericht automatisch aktualisiert. Der schattierte Bereich im Zeitrahmen stellt den Berichtszeitraum dar. Die Daten im Zeitrahmen werden von links nach rechts erhöht.

![chlimage_1-250](assets/chlimage_1-250.png)

So ändern Sie den Berichtszeitraum einer Inhaltseinblick-Seite:

1. Wenn der Zeitrahmen nicht oben auf der Seite angezeigt wird, klicken oder tippen Sie auf das Symbol Zeitrahmen umschalten .

   ![](do-not-localize/chlimage_1-22.png)

1. Um das Anfangsdatum des Berichtszeitraums zu ändern, ziehen Sie den Kreis, der links neben dem schattierten Bereich angezeigt wird, zum gewünschten Startdatum.

   Wenn Sie die linke Seite des schattierten Bereichs nicht sehen können, verwenden Sie die Bildlaufleiste, um ihn anzuzeigen.

1. Um das Enddatum des Berichtszeitraums zu ändern, ziehen Sie den Kreis, der rechts neben dem schattierten Bereich angezeigt wird, zum gewünschten Enddatum.

### Ändern der Granularität des Berichtszeitraums {#changing-the-granularity-of-the-reporting-period}

Ändern Sie die Zeitdauer, die jeder Datenpunkt in einem Bericht umfasst. Wenn beispielsweise die Granularität &quot;Woche&quot;ausgewählt ist, stellt jeder Datenpunkt im Bericht &quot;Ansichten&quot;die Anzahl der Ansichten für eine Woche dar.

![screen_shot_2017-11-29at141001](assets/screen_shot_2017-11-29at141001.png)

Die Granularität wirkt sich auf die Berichte aus, die Daten in Bezug auf die Zeit darstellen, z. B. die Berichte „Ansichten“ und „Durchschnittliche Aufenthaltsdauer auf der Seite in Minuten“. Die Granularität wirkt sich auch auf die Größe des Zeitrahmens aus.

1. Wenn das Granularitätssteuerelement nicht angezeigt wird, klicken oder tippen Sie auf das Symbol Granularität umschalten .

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Klicken oder tippen Sie auf die gewünschte Granularität. Nach der Auswahl wird der Bericht automatisch entsprechend der Granularität aktualisiert.

## Zuweisen von Aufgaben für SEO Recommendations {#assigning-tasks-for-seo-recommendations}

Verwenden Sie den SEO Recommendations-Bericht, um Aufgaben zur Verbesserung der Seitenanzeige für Suchmaschinen zu erstellen. Für jede Empfehlung im Bericht, für die kein Häkchen angebracht ist, können Sie eine Aufgabe erstellen, die Sie einem Benutzer zuweisen, um die erforderliche Arbeit durchzuführen.

![chlimage_1-252](assets/chlimage_1-252.png)

Der Status der SEO-Empfehlung gibt an, wenn die Aufgabe erstellt, aber noch nicht abgeschlossen ist.

![chlimage_1-253](assets/chlimage_1-253.png)

Wenn sie erstellt wurde, wird die Aufgabe in der Aufgabenliste des Benutzers angezeigt. Weitere Informationen zu Aufgaben finden Sie unter [Arbeiten mit Aufgaben](/help/sites-authoring/task-content.md).

Gehen Sie wie folgt vor, um eine Aufgabe für eine SEO-Empfehlung zu erstellen.

1. Klicken oder tippen Sie auf das Informationssymbol für die SEO-Empfehlung.

   ![](do-not-localize/chlimage_1-23.png)

1. Klicken Sie auf das umkreiste Dreieckssymbol, das neben dem Informationssymbol angezeigt wird.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Füllen Sie die angezeigten Formularfelder aus und tippen Sie auf Erstellen:

   * Projekt: Wählen Sie das Projekt aus, in dem die Aufgabe erstellt werden soll.
   * Name: Der Name, der die Aufgabe identifiziert. Der Standardname ist der Titel der SEO-Empfehlung.
   * Zuweisen zu: Wählen Sie den Benutzer aus, dem die Aufgabe zugewiesen werden soll. Geben Sie den Namen des Benutzers ein, um die Liste zu filtern.
   * Beschreibung: Eine Beschreibung der Aktivität, die erforderlich ist, um die Aufgabe abzuschließen. Die Standardbeschreibung ist die Information, die der SEO-Empfehlung beigefügt ist.
   * Aufgabenpriorität: Die Priorität der Aufgabe.
   * Fälligkeitsdatum: Das Datum, bis zu dem die Aufgabe abgeschlossen sein soll.

1. Klicken oder tippen Sie auf „Fertig“, um die Meldung „Aufgabe erstellt“ zu schließen.

>[!NOTE]
>
>Die erstellte Aufgabe enthält auch den Pfad zu der Seite, für die die SEO-Empfehlung gilt.
