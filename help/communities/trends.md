---
title: Aktivitätstrends
seo-title: Aktivitätstrends
description: Hinzufügen einer Community-Aktivitätsliste-Komponente zu einer Seite
seo-description: Hinzufügen einer Community-Aktivitätsliste-Komponente zu einer Seite
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Aktivitätstrends {#activity-trends}

## Einführung {#introduction}

The `Community Activity List` component provides the ability to add trending information regarding posts and views by members as well as posts and views of content.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der `Community Activity List` Komponente zu einer [Community-Site](overview.md#community-sites)

* Configuration settings for the `Community Activity List` component

## Anforderung {#requirement}

Daten für die `Community Activity List` sind nur verfügbar, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-Funktionen](analytics.md).

## Adding a Community Activity List to a Page {#adding-a-community-activity-list-to-a-page}

Um einer Seite im Autorenmodus eine `Community Activity List` Komponente hinzuzufügen, suchen Sie die Komponente `Communities / Community Activity List` und ziehen Sie sie auf eine Seite.

For necessary information, visit [Communities Components Basics](basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![chlimage_1-227](assets/chlimage_1-227.png)

## Konfigurieren der Community-Aktivitätsliste {#configuring-community-activity-list}

Select the placed `Community Activity List` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-228](assets/chlimage_1-228.png)

Legen Sie auf der Registerkarte **[!UICONTROL Kommentare]** fest, ob und wie Kommentare zu hochgeladenen Dateien angezeigt werden:

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Typ]**

   Geben Sie an, ob Daten zu Community-Mitgliedern oder benutzergenerierten Inhalten (UGC) angezeigt werden sollen.

   Die folgenden Optionen stehen zur Auswahl
   * `Members`
   * `Content`
   Der Standardwert ist `Members`.

* **[!UICONTROL Anzeigetitel]**

   Ein beschreibender Titel, der über den Daten angezeigt werden soll, z. B. `Trending Content`.

   Standardmäßig ist kein Name eingegeben.

* **[!UICONTROL Anzeigezahl]**

   Die Anzahl der anzuzeigenden Elemente.

   Der Standardwert ist 10.

* **[!UICONTROL Aktivitätstyp]**

   Wählen Sie eines von
   * `Views`(Seitenbesuche)
   * `Posts`(UGC erstellen)
   * `Follows`
   * `Likes`
   Die Standardeinstellung lautet „Ansichten“.

* **[!UICONTROL Zeitraum]**

   Wählen Sie eines von
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`
   Der Standardwert ist `Total`.

* **[!UICONTROL Kontextpfad]**

   Bietet die Möglichkeit, die Aktivität auf eine Teilmenge der Site zu beschränken, z. B. auf einen bestimmten Blog.

   Standardmäßig ist die Community-Site ausgewählt.

* **[!UICONTROL Gesammelte Mitgliederzahl]**

   Wenn diese Option deaktiviert ist, werden nur Beiträge der obersten Ebene gezählt. For example, if the context is the root page (the default), then an `Activity Type`of `Posts`will never show any activity as there is no ability to post content to the root page. Ist diese Option aktiviert, werden auch die Ergebnisse aller untergeordneten Seiten eingeschlossen.

   Diese Option ist standardmäßig aktiviert.

## Beispielseite mit vier Komponenten {#example-page-with-components}

Konfiguration **Wichtigste Besucher** (Top Visitors): Typ = Mitglieder, Aktivitätstyp = Ansichten

**Konfiguration der wichtigsten Mitarbeiter** : Typ = Mitglieder, Aktivitätstyp = Beiträge

**Konfiguration des Hauptinhalts** : Typ = Inhalt, Aktivitätstyp = Ansichten,

**Konfigurieren des Trendinhalts** : Typ = Inhalt, Aktivitätstyp = Beiträge

![chlimage_1-230](assets/chlimage_1-230.png)
