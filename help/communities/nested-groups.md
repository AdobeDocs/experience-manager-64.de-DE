---
title: Verfassen verschachtelter Gruppen
seo-title: Verfassen verschachtelter Gruppen
description: Erstellen verschachtelter Gruppen
seo-description: Erstellen verschachtelter Gruppen
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
exl-id: 87be7ffe-d937-4e85-8d90-5b7c356f0876
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 4%

---

# Erstellen verschachtelter Gruppen {#authoring-nested-groups}

## Erstellen von Gruppen in der Autoreninstanz {#creating-groups-on-author}

Auf der Autoreninstanz über die globale Navigation

* Wählen Sie **[!UICONTROL Communities > Sites]** aus.
* Wählen Sie **[!UICONTROL Ordner]** aktivieren, um ihn zu öffnen
* Wählen Sie die Karte für die englische Site **[!UICONTROL Tutorial zu den ersten Schritten]** aus.
   * Kartenbild auswählen
   * *not* Symbol auswählen

Das Ergebnis ist, die [Gruppenkonsole](groups.md) zu erreichen:

![chlimage_1-53](assets/chlimage_1-53.png)

Die Funktion &quot;Gruppen&quot;wird als Ordner angezeigt, in dem Instanzen von Gruppen erstellt werden. Wählen Sie den Ordner Gruppen aus, um ihn zu öffnen. Die in der Veröffentlichung erstellte Gruppe ist sichtbar.

![chlimage_1-54](assets/chlimage_1-54.png)

## Hauptdarstellungsgruppe erstellen {#create-main-arts-group}

Diese Gruppe kann erstellt werden, da die Site-Struktur für die Interaktion eine Gruppenfunktion enthält. Die Konfiguration der Funktion im `Reference Template` der Site ermöglicht standardmäßig die Auswahl einer beliebigen aktivierten Gruppenvorlage. Die für diese neue Gruppe ausgewählte Vorlage ist daher `Reference Group`.

Diese Konsolen ähneln der Communities Sites-Konsole.

* Wählen Sie **[!UICONTROL Gruppe erstellen]**
* `1 Community Group Template`:
   * Community-Gruppentitel: Kunst
   * Community-Gruppenbeschreibung: Eine übergeordnete Gruppe für verschiedene Kunstgruppen.
   * Community-Gruppenstamm: *Lassen Sie als Standard*
   * Zusätzliche verfügbare Community-Gruppensprache(n): Wählen Sie über das Pulldown-Menü die verfügbaren Community-Gruppensprachen aus. Im Menü werden alle Sprachen angezeigt, in denen die übergeordnete Community-Site erstellt wird. Benutzer können in diesem Schritt unter diesen Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.
   * Community-Gruppenname: Kunst
   * Vorlage: nach unten ziehen, um `Reference Group` auszuwählen
   * Wählen Sie nun eine der folgenden Optionen aus `Next`

      ![parenttonestedgroup](assets/parenttonestedgroup.png)

Fahren Sie mit den folgenden Einstellungen durch die anderen Bedienfelder:

* **2 Design**
   * Sie können das Design ändern oder zulassen, dass standardmäßig das Design der übergeordneten Site verwendet wird
   * Wählen Sie **[!UICONTROL Weiter]** aus
* **3 Einstellungen**
   * **Moderation**
      * Leer lassen (von der übergeordneten Site übernehmen)
   * **Mitgliedschaft**
      * Standard `Optional Membership` verwenden
   * **Miniaturansicht**
      * `optional`
   * Wählen Sie nun eine der folgenden Optionen aus `Next`
* Wählen Sie **[!UICONTROL Erstellen]**

### Verschachtelung von Gruppen innerhalb der Artgruppe {#nesting-groups-within-arts-group}

Der Ordner `groups` sollte jetzt zwei Gruppen enthalten (es kann erforderlich sein, die Seite zu aktualisieren).

![createcommunitygroup](assets/createcommunitygroup.png)

####  Gruppe veröffentlichen{#publish-group}

Bevor Sie in der Gruppe `arts`verschachtelte Gruppen erstellen, halten Sie den Mauszeiger über die Karte `arts` und wählen Sie das Veröffentlichungssymbol aus, um sie zu veröffentlichen.

![chlimage_1-55](assets/chlimage_1-55.png)

Warten Sie auf die Bestätigung, dass die Gruppe veröffentlicht wurde.

![chlimage_1-56](assets/chlimage_1-56.png)

Die Gruppe `arts` sollte auch einen Ordner `groups` enthalten, der jedoch leer ist und in dem neue Gruppen erstellt werden können. Navigieren Sie zum Ordner &quot;Arts-Gruppe&quot;und erstellen Sie 3 verschachtelte Gruppen mit jeweils unterschiedlichen Mitgliedschaftseinstellungen:

1. Besuchszeit
   * Titel: `Visual Arts`
   * Name: `visual`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: select `Optional Membership`
Eine öffentliche Gruppe, die allen Mitgliedern offen steht
1. Zielgruppe
   * Titel: `Auditory Arts`
   * Name: `auditory`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: select `Required Membership`
Eine offene Gruppe, der Mitglieder beitreten können

1. Verlauf

   * Titel: `Art History`
   * Name: `history`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: select `Restricted Membership`
Eine geheime Gruppe, die beispielsweise nur für eingeladene Mitglieder sichtbar ist, lädt 
[Demobenutzer](tutorials.md#demo-users) `emily.andrews@mailinator.com`

Aktualisieren Sie die Seite, um alle drei verschachtelten Gruppen (Untergruppen) anzuzeigen.

Navigieren Sie ggf. über die Communities Sites-Konsole zu den verschachtelten Gruppen:

* Wählen Sie **[!UICONTROL engagieren Sie den Ordner]**
* Wählen Sie die Karte **[!UICONTROL Erste Schritte - Tutorial]** aus.
* Wählen Sie **[!UICONTROL Gruppenordner]** aus.
* Wählen Sie **[!UICONTROL arts card]** aus.
* Wählen Sie **[!UICONTROL Gruppenordner]** aus.

![chlimage_1-57](assets/chlimage_1-57.png)

## Verlagsgruppen {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Nach der Veröffentlichung der Haupt-Community-Site ist es erforderlich,

* Jede Gruppe einzeln veröffentlichen
   * Warten auf Bestätigung der Veröffentlichung der Gruppe
* Veröffentlichen Sie die übergeordnete Gruppe, bevor Sie in verschachtelte Gruppen veröffentlichen
   * Alle Gruppen müssen von oben nach unten veröffentlicht werden.

![chlimage_1-59](assets/chlimage_1-59.png)

## Erlebnis bei der Veröffentlichung {#experience-on-publish}

Es ist möglich, die verschiedenen Gruppen zu erleben, wenn sie angemeldet sind, z. B. mit den [Demobenutzern](tutorials.md#demo-users), die für

* Mitglied der Gruppe Kunst/Verlauf : emily.andrews@mailinator.com/password
   * Die eingeschränkte (geheime) Gruppe, Kunst/Verlauf, wird angezeigt
   * Kann optionale (öffentliche) Gruppen anzeigen
   * Können eingeschränkten (offenen) Gruppen beitreten
* Gruppenmanager: aaron.mcdonald@mailinator.com/password
   * Kann optionale (öffentliche) Gruppen anzeigen
   * kann eingeschränkten (offenen) Gruppen beitreten
   * Angehaltene (geheime) Gruppen werden nicht angezeigt

Greifen Sie auf die Communities [Mitglieder und Gruppen-Konsolen](members.md) auf der Autoreninstanz zu, um weitere Benutzer zu verschiedenen Mitgliedergruppen hinzuzufügen, die den Community-Gruppen entsprechen.
