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


# Leaderboard-Funktion {#leaderboard-feature}

## Einführung {#introduction}

Die `Leaderboard`-Komponente bietet die Möglichkeit, sich ein Gefühl dafür zu verschaffen, wie Mitglieder innerhalb der Community interagieren, indem sie Mitglieder nach gewonnenen Punkten (Basissortierung) oder ihrem Fachwissen (fortgeschrittenes Scoring) einstufen.

Bevor Sie die Lederboard-Komponente auf eine Seite setzen, müssen Sie [Communities Scoring and Badges](implementing-scoring.md) konfigurieren.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Komponente `Leaderboard` zu einer [Community-Site](overview.md#community-sites)

* Konfigurationseinstellungen für die Komponente `Leaderboard`

## Hinzufügen einer Pinnwand zu einer Seite {#adding-a-leaderboard-to-a-page}

Um eine `Leaderboard`-Komponente zu einer Seite im Autorenmodus hinzuzufügen, suchen Sie die Komponente

* `Communities / Leaderboard`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Bei der ursprünglichen Platzierung auf einer Community-Site wird die Komponente wie folgt angezeigt:

![chlimage_1-8](assets/chlimage_1-8.png)

## Leaderboard {#configuring-leaderboard} konfigurieren

Wählen Sie die platzierte Komponente `Leaderboard` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### Registerkarte „Settings“{#settings-tab}

Geben Sie unter der Registerkarte **[!UICONTROL Einstellungen]** an, welche Informationen zum Element angezeigt werden sollen:

* **[!UICONTROL Anzeigename]**
Ein beschreibender Name, der für die Pinnwand angezeigt werden soll und den Regeln entspricht, die für die Anzeige von Abzeichen und Ergebnissen ausgewählt wurden.

   Der Standardwert ist `Leaderboard`, wenn nichts eingegeben wurde.

* ****
BadgeWenn aktiviert, wird eine Spalte für Symbole mit Zeichen in die Lederboard aufgenommen.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL KennzeichennameWenn]**
aktiviert, wird eine Spalte für den Kennzeichennamen in der Lederboard eingefügt.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Verwenden Sie]**
AvatarWenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds neben dem Namen des Mitglieds mit dem Profil des Mitglieds verknüpft.

   Diese Option ist standardmäßig deaktiviert.

### Registerkarte Regeln {#rules-tab}

Auf der Registerkarte **[!UICONTROL Regeln]** finden Sie die Community-Site und die zugehörigen Scoring- und Bading-Regeln

* **[!UICONTROL Regelspeicherort]**
 (erforderlich) Der Speicherort, an dem die Regel für Bewertung/Abzeichen konfiguriert ist.

* **[!UICONTROL Bewertungsregel]**
 (erforderlich) Spezifische Regel, die die anzuzeigenden Ergebnisse generiert.

* **[!UICONTROL Badging-Regel]**
 (erforderlich) Spezifische Regel, die das anzuzeigende Zeichen generiert.

* **[!UICONTROL Zeigt]**
LimitAnzahl der Mitglieder an, die pro Seite angezeigt werden.

   Der Standardwert ist 10.

## Beispiel: Hauptplatine der Teilnehmer {#example-participants-leaderboard}

Dieser Bericht des Lederboards beruht auf der Anwendung grundlegender Bewertungsregeln.

Konfiguration der Leaderboard-Komponente:

* **** Einstellungsstab:

   * Anzeigename = `Participation Board`
   * `checked`:

      * Abzeichen
      * Abzeichenname
      * Avatar verwenden

* **** Rulestab:

   * Speicherort für Regel = `/content/sites/communities/jcr:content`
   * Bewertungsregel = `/etc/community/scoring/rules/forums-scoring`
   * Abzeichenregel = `/etc/community/badging/rules/reference-badging`
   * Anzeigelimit = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## Beispiel: Expert Leaderboard {#example-experts-leaderboard}

Dieser Bericht des Lederboards ist das Ergebnis der Anwendung erweiterter Bewertungsregeln.

Konfiguration der Leaderboard-Komponente:

* **** Einstellungsstab:

   * Anzeigename = `Expertise Board`
   * `checked`:

      * Abzeichen
      * Avatar verwenden

* **** Rulestab:

   * Speicherort für Regel = `/content/sites/communities/jcr:content`
   * Bewertungsregel = `/etc/community/scoring/rules/adv-forums-scoring`
   * Abzeichenregel = `/etc/community/badging/rules/adv-forums-badging`
   * Anzeigelimit = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Leaderboard Essentials](leaderboard.md) für Entwickler.

Anweisungen zum Erstellen von Regeln finden Sie auf der Seite [Bewertung und Abzeichen](implementing-scoring.md) für Administratoren.
