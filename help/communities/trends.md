---
title: Aktivitätstrends
seo-title: Aktivitätstrends
description: Hinzufügen einer Liste zur Community-Aktivität zu einer Seite
seo-description: Hinzufügen einer Liste zur Community-Aktivität zu einer Seite
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 29%

---


# Aktivitätstrends {#activity-trends}

## Einführung {#introduction}

Die Komponente `Community Activity List` bietet die Möglichkeit, Trendinformationen über Beiträge und Ansichten von Mitgliedern sowie Beiträge und Ansichten von Inhalten hinzuzufügen.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Komponente `Community Activity List` zu einer [Community-Site](overview.md#community-sites)

* Konfigurationseinstellungen für die Komponente `Community Activity List`

## Anforderung {#requirement}

Daten für das `Community Activity List` stehen nur zur Verfügung, wenn Adobe Analytics für die Community-Site lizenziert und konfiguriert ist.

Siehe [Analytics-Konfiguration für Communities-Funktionen](analytics.md).

## Hinzufügen einer Community-Aktivität-Liste zu einer Seite {#adding-a-community-activity-list-to-a-page}

Um einer Seite im Autorenmodus eine `Community Activity List`-Komponente hinzuzufügen, suchen Sie die Komponente `Communities / Community Activity List` und ziehen Sie sie an die gewünschte Position auf einer Seite.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![chlimage_1-227](assets/chlimage_1-227.png)

## Konfigurieren der Community-Aktivität-Liste {#configuring-community-activity-list}

Wählen Sie die platzierte Komponente `Community Activity List` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

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

   Die Anzahl der zu Liste Elemente.

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

   Bietet die Möglichkeit, die Aktivität auf eine Untergruppe der Site, z. B. einen bestimmten Blog, zu erweitern.

   Standardmäßig ist die Community-Site ausgewählt.

* **[!UICONTROL Gesammelte Mitgliederzahl]**

   Wenn diese Option deaktiviert ist, werden nur Beiträge der obersten Ebene gezählt. Wenn der Kontext z. B. die Stammseite ist (Standard), zeigt `Activity Type`von `Posts`keine Aktivität an, da es nicht möglich ist, Inhalte auf der Stammeseite zu posten. Ist diese Option aktiviert, werden auch die Ergebnisse aller untergeordneten Seiten eingeschlossen.

   Diese Option ist standardmäßig aktiviert.

## Beispielseite mit vier Komponenten {#example-page-with-components}

Konfiguration **Wichtigste Besucher** (Top Visitors): Typ = Mitglieder, Aktivitätstyp = Ansichten

**Top-** Mitarbeiter-Konfiguration: Typ = Member, Aktivität type = Beiträge

**Top-** ContentConfig: Typ = Aktivität, Typ = Ansichten,

**Trending** ContentConfig: Typ = Aktivität, Typ = Beiträge

![chlimage_1-230](assets/chlimage_1-230.png)
