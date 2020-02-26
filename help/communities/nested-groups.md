---
title: Erstellen von verschachtelten Gruppen
seo-title: Erstellen von verschachtelten Gruppen
description: Verschachtelte Gruppen erstellen
seo-description: Verschachtelte Gruppen erstellen
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc

---


# Erstellen von verschachtelten Gruppen {#authoring-nested-groups}

## Erstellen von Gruppen beim Autor {#creating-groups-on-author}

Beim Autor über die globale Navigation

* Wählen Sie **[!UICONTROL Communities > Sites]**
* Wählen Sie **[!UICONTROL den Ordner]** &quot;engagement&quot;aus, um ihn zu öffnen
* Wählen Sie die Karte für die Site &quot;Erste **[!UICONTROL Schritte - Lernprogramm]** - Englisch&quot;
   * Kartenbild auswählen
   * Symbol *nicht* auswählen

Das Ergebnis ist, die [Gruppenkonsole](groups.md)zu erreichen:

![chlimage_1-53](assets/chlimage_1-53.png)

Die Funktion &quot;Gruppen&quot;wird als Ordner angezeigt, in dem Instanzen von Gruppen erstellt werden. Wählen Sie den Ordner &quot;Gruppen&quot;, um ihn zu öffnen. Die bei der Veröffentlichung erstellte Gruppe ist sichtbar.

![chlimage_1-54](assets/chlimage_1-54.png)

## Hauptkunstgruppe erstellen {#create-main-arts-group}

Diese Gruppe kann erstellt werden, da die Sitestruktur für den Einsatz eine Gruppenfunktion enthält. Die Konfiguration der Funktion in der `Reference Template` Standardeinstellung der Site ermöglicht die Auswahl einer aktivierten Gruppenvorlage. Die Vorlage, die für diese neue Gruppe gewählt wird, ist somit die `Reference Group`.

Diese Konsolen sind der Communities Sites-Konsole sehr ähnlich.

* Gruppe **[!UICONTROL erstellen auswählen]**
* `1 Community Group Template`:
   * Community-Gruppentitel: Kunst
   * Community-Gruppenbeschreibung: Eine übergeordnete Gruppe für verschiedene Kunstgruppen.
   * Community-Gruppenstamm: Als Standard *beibehalten*
   * Zusätzliche verfügbare Community-Gruppensprache(n): Wählen Sie im Pulldown-Menü die verfügbaren Gemeinschaftsgruppensprachen aus. Das Menü zeigt alle Sprachen an, in denen die übergeordnete Community-Site erstellt wurde. Benutzer können in diesem Schritt eine der folgenden Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.
   * Community-Gruppenname: Kunst
   * Vorlage: nach unten ziehen, um `Reference Group`
   * Wählen Sie nun eine der folgenden Optionen aus `Next`
      ![parenttonestedgroup](assets/parenttonestedgroup.png)

Führen Sie mit den folgenden Einstellungen weitere Schritte durch:

* **2 Design**
   * Sie können den Entwurf ändern oder zulassen, dass der Entwurf der übergeordneten Site standardmäßig verwendet wird
   * Wählen Sie **[!UICONTROL Weiter]**
* **3 Einstellungen**
   * **Moderation**
      * Leer lassen (von der übergeordneten Site übernehmen)
   * **Mitgliedschaft**
      * use default `Optional Membership`
   * **Miniatur**
      * `optional`
   * Wählen Sie nun eine der folgenden Optionen aus `Next`
* Wählen Sie **[!UICONTROL Erstellen]**

### Verschachteln von Gruppen innerhalb der Artgruppe {#nesting-groups-within-arts-group}

Der `groups` Ordner sollte nun zwei Gruppen enthalten (es kann erforderlich sein, die Seite zu aktualisieren).

![createcCommunity-Gruppe](assets/createcommunitygroup.png)

####  Gruppe veröffentlichen{#publish-group}

Bewegen Sie den Mauszeiger vor dem Erstellen von innerhalb der `arts`Gruppe verschachtelten Gruppen über die `arts` Karte und wählen Sie das Symbol &quot;Veröffentlichen&quot;, um sie zu veröffentlichen.

![chlimage_1-55](assets/chlimage_1-55.png)

Warten Sie auf die Bestätigung, dass die Gruppe veröffentlicht wurde.

![chlimage_1-56](assets/chlimage_1-56.png)

Die `arts` Gruppe sollte auch einen `groups` Ordner enthalten, der jedoch leer ist und in dem neue Gruppen erstellt werden können. Navigieren Sie zum Ordner &quot;art group&quot;und erstellen Sie 3 verschachtelte Gruppen mit jeweils unterschiedlichen Mitgliedseinstellungen:

1. Sichtbar
   * Titel: `Visual Arts`
   * Name: `visual`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Optional Membership`eine öffentliche Gruppe, die allen Mitgliedern offen steht
1. Audition
   * Titel: `Auditory Arts`
   * Name: `auditory`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Required Membership`eine offene Gruppe aus, der Mitglieder beitreten können

1. Verlauf

   * Titel: `Art History`
   * Name: `history`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Restricted Membership`eine geheime Gruppe aus, die als Beispiel nur für eingeladene Mitglieder sichtbar ist und [Demobenutzer](tutorials.md#demo-users) einlädt `emily.andrews@mailinator.com`

Aktualisieren Sie die Seite, um alle drei verschachtelten Gruppen (Unter-Communities) anzuzeigen.

Falls erforderlich, navigieren Sie über die Communities Sites-Konsole zu den verschachtelten Gruppen:

* Ordner **[!UICONTROL für Interaktion auswählen]**
* Karte **[!UICONTROL Erste Schritte]** auswählen
* Ordner &quot; **[!UICONTROL Gruppen&quot;auswählen]**
* Karte **[!UICONTROL für Kunst auswählen]**
* Ordner &quot; **[!UICONTROL Gruppen&quot;auswählen]**

![chlimage_1-57](assets/chlimage_1-57.png)

## Veröffentlichungsgruppen {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Nach der Veröffentlichung der Haupt-Community-Site muss

* Jede Gruppe einzeln veröffentlichen
   * Warten auf Bestätigung der Veröffentlichung der Gruppe
* Veröffentlichen Sie die übergeordnete Gruppe, bevor Sie in
   * Alle Gruppen müssen von oben nach unten veröffentlicht werden.

![chlimage_1-59](assets/chlimage_1-59.png)

## Erlebnis bei Veröffentlichung {#experience-on-publish}

Es ist möglich, die verschiedenen Gruppen bei der Anmeldung zu erleben, zum Beispiel mit der [Demo-Benutzer](tutorials.md#demo-users) für

* Mitglied der Gruppe &quot;Kunst/Verlauf&quot;: emily.andrews@mailinator.com/Kennwort
   * Die eingeschränkte (geheime) Gruppe, Kunst/Geschichte, ist sichtbar
   * Kann optionale (öffentliche) Gruppen anzeigen
   * Kann eingeschränkten (offenen) Gruppen beitreten
* Gruppenmanager: aaron.mcdonald@mailinator.com/Kennwort
   * Kann optionale (öffentliche) Gruppen anzeigen
   * kann eingeschränkte (offene) Gruppen beitreten
   * Wird keine eingeschränkten (geheimen) Gruppen sehen

Greifen Sie auf die Communities [Members and Groups consoles](members.md) on author zu, um weitere Benutzer zu verschiedenen Mitgliedergruppen hinzuzufügen, die den Community-Gruppen entsprechen.
