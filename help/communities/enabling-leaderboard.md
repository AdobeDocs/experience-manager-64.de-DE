---
title: Leader-Funktion
seo-title: Leader-Funktion
description: Hinzufügen einer Leaderboard-Komponente zu einer Seite
seo-description: Hinzufügen einer Leaderboard-Komponente zu einer Seite
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
translation-type: tm+mt
source-git-commit: 1bbd917ef20c4a618e93af66ffe8a6cfc8448e78
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 17%

---


# Leader-Funktion {#leaderboard-feature}

## Einführung {#introduction}

Die `Leaderboard` Komponente bietet die Möglichkeit, einen Eindruck davon zu erhalten, wie Mitglieder innerhalb der Gemeinschaft interagieren, indem sie Mitglieder nach Punkten (Basis-Scoring) oder ihrem Fachwissen (Advanced Scoring) einstufen.

Bevor Sie die Komponente &quot;Lederboard&quot;auf eine Seite einfügen, müssen Sie die Bewertung und Abzeichen der [Communities konfigurieren](implementing-scoring.md).

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der `Leaderboard` Komponente zu einer [Community-Site](overview.md#community-sites)

* Configuration settings for the `Leaderboard` component

## Adding a Leaderboard to a Page {#adding-a-leaderboard-to-a-page}

To add a `Leaderboard` component to a page in author mode, locate the component

* `Communities / Leaderboard`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

For necessary information, visit [Communities Components Basics](basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![chlimage_1-8](assets/chlimage_1-8.png)

## Leaderboard konfigurieren {#configuring-leaderboard}

Select the placed `Leaderboard` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### Registerkarte „Settings“{#settings-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** an, welche Informationen zum Element angezeigt werden sollen:

* **[!UICONTROL Anzeigename]** Ein beschreibender Name, der für die Pinnwand angezeigt werden soll und den Regeln entspricht, die für die Anzeige von Abzeichen und Ergebnissen ausgewählt wurden.

   Der Standardwert ist `Leaderboard`, wenn nichts eingegeben wurde.

* **[!UICONTROL Abzeichen]** Wenn aktiviert, wird eine Spalte für Symbole mit Zeichen in die Lederboard aufgenommen.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kennzeichenname]** Wenn aktiviert, wird eine Spalte für den Kennzeichennamen in der Lederboard eingefügt.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Verwenden Sie Avatar]** Wenn aktiviert, wird das Avatarbild des Mitglieds neben dem Namen des Mitglieds mit dem Profil des Mitglieds verknüpft.

   Diese Option ist standardmäßig deaktiviert.

### Registerkarte &quot;Regeln&quot; {#rules-tab}

Auf der Registerkarte &quot; **[!UICONTROL Regeln]** &quot;finden Sie die Community-Site und die zugehörigen Scoring- und Badging-Regeln.

* **[!UICONTROL Regelspeicherort]**(erforderlich) Der Speicherort, an dem die Regel für Bewertung/Abzeichen konfiguriert ist.

* **[!UICONTROL Bewertungsregel]**(erforderlich) Spezifische Regel, die die anzuzeigenden Ergebnisse generiert.

* **[!UICONTROL Badging-Regel]**(erforderlich) Spezifische Regel, die das anzuzeigende Zeichen generiert.

* **[!UICONTROL Zeigt die pro Seite anzuzeigende]** Anzahl der Mitglieder an.

   Der Standardwert ist 10.

## Beispiel: Hauptplatine der Teilnehmer {#example-participants-leaderboard}

Dieser Bericht des Lederboards beruht auf der Anwendung grundlegender Bewertungsregeln.

Konfiguration der Leaderboard-Komponente:

* **[!UICONTROL Registerkarte &quot;Einstellungen]** &quot;:

   * Anzeigename = `Participation Board`
   * `checked`:

      * Abzeichen
      * Abzeichenname
      * Avatar verwenden

* **[!UICONTROL Registerkarte Regeln]** :

   * Speicherort für Regel = `/content/sites/communities/jcr:content`
   * Bewertungsregel = `/etc/community/scoring/rules/forums-scoring`
   * Abzeichenregel = `/etc/community/badging/rules/reference-badging`
   * Anzeigelimit = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## Beispiel: Expert Leaderboard {#example-experts-leaderboard}

Dieser Bericht des Lederboards ist das Ergebnis der Anwendung erweiterter Bewertungsregeln.

Konfiguration der Leaderboard-Komponente:

* **[!UICONTROL Registerkarte &quot;Einstellungen]** &quot;:

   * Anzeigename = `Expertise Board`
   * `checked`:

      * Abzeichen
      * Avatar verwenden

* **[!UICONTROL Registerkarte Regeln]** :

   * Speicherort für Regel = `/content/sites/communities/jcr:content`
   * Bewertungsregel = `/etc/community/scoring/rules/adv-forums-scoring`
   * Abzeichenregel = `/etc/community/badging/rules/adv-forums-badging`
   * Anzeigelimit = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Leaderboard Essentials](leaderboard.md) page for developers.

Anweisungen zum Erstellen von Regeln finden Sie auf der Seite &quot;Bewertung [und Abzeichen](implementing-scoring.md) für Administratoren&quot;.
