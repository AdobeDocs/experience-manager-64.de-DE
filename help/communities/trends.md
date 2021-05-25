---
title: Aktivitätstrends
seo-title: Aktivitätstrends
description: Hinzufügen einer Community-Aktivitätslisten-Komponente zu einer Seite
seo-description: Hinzufügen einer Community-Aktivitätslisten-Komponente zu einer Seite
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
exl-id: a2cb9738-98a5-4ea6-8d5a-a6c0aa04cd32
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 29%

---

# Aktivitätstrends {#activity-trends}

## Einführung {#introduction}

Die Komponente `Community Activity List` bietet die Möglichkeit, Trendinformationen zu Beiträgen und Ansichten von Mitgliedern sowie Beiträgen und Ansichten von Inhalten hinzuzufügen.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Komponente `Community Activity List` zu einer [Community-Site](overview.md#community-sites)

* Konfigurationseinstellungen für die Komponente `Community Activity List`

## Anforderung {#requirement}

Daten für `Community Activity List` sind nur verfügbar, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-Funktionen](analytics.md).

## Hinzufügen einer Community-Aktivitätenliste zu einer Seite {#adding-a-community-activity-list-to-a-page}

Um eine Komponente `Community Activity List` im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie die Komponente `Communities / Community Activity List` und ziehen Sie sie an die gewünschte Stelle auf einer Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![chlimage_1-227](assets/chlimage_1-227.png)

## Konfigurieren der Community-Aktivitätenliste {#configuring-community-activity-list}

Wählen Sie die platzierte Komponente `Community Activity List` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

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

   Die Anzahl der aufzulistenden Elemente.

   Der Standardwert ist 10.

* **[!UICONTROL Aktivitätstyp]**

   Wählen Sie eine von
   * `Views`(Seitenbesuche)
   * `Posts`(Erstellen von benutzergenerierten Inhalten)
   * `Follows`
   * `Likes`

   Die Standardeinstellung lautet „Ansichten“.

* **[!UICONTROL Zeitraum]**

   Wählen Sie eine von
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   Der Standardwert ist `Total`.

* **[!UICONTROL Kontextpfad]**

   Bietet die Möglichkeit, die Aktivität auf eine Teilmenge der Site zu beschränken, z. B. einen bestimmten Blog.

   Standardmäßig ist die Community-Site ausgewählt.

* **[!UICONTROL Gesammelte Mitgliederzahl]**

   Wenn diese Option deaktiviert (deaktiviert) ist, werden nur Beiträge der obersten Ebene gezählt. Wenn der Kontext beispielsweise die Stammseite ist (Standardeinstellung), zeigt ein `Activity Type`von `Posts`keine Aktivität an, da keine Möglichkeit besteht, Inhalte auf der Stammseite zu posten. Ist diese Option aktiviert, werden auch die Ergebnisse aller untergeordneten Seiten eingeschlossen.

   Diese Option ist standardmäßig aktiviert.

## Beispielseite mit vier Komponenten {#example-page-with-components}

Konfiguration **Wichtigste Besucher** (Top Visitors): Typ = Mitglieder, Aktivitätstyp = Ansichten

**Top** Contributorsconfig: Typ = Mitglieder, Aktivitätstyp = Beiträge

**Top** ContentConfig: Typ = Inhalt, Aktivitätstyp = Ansichten,

**Trending** ContentConfig: Typ = Inhalt, Aktivitätstyp = Beiträge

![chlimage_1-230](assets/chlimage_1-230.png)
