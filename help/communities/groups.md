---
title: Konsole für Community-Gruppen
seo-title: Community Groups Console
description: Gruppenkonsole ermöglicht die Erstellung von Community-Gruppen
seo-description: Groups console lets you create Community groups
uuid: 7dac2d1b-78fc-4b39-a2cb-100f1e220c23
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1293c01a-7308-494a-ab48-bd9938205b81
pagetitle: Community Groups Console
role: Admin
exl-id: f8f19ad6-d6cd-4abd-bc31-6baba3e0356e
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '1628'
ht-degree: 2%

---

# Konsole für Community-Gruppen {#community-groups-console}

Die Gruppenkonsole bietet Zugriff auf das Erstellen von Community-Gruppen, wenn die [Vorlagenstruktur](sites-console.md#step1) enthält [Gruppenfunktion](functions.md#groups-function).

* Gruppen können innerhalb anderer Gruppen verschachtelt sein. Dies geschieht, wenn die [Struktur der neuen Gruppe](tools-groups.md) enthält die Funktion &quot;Gruppen&quot;.
* Nur für die Autorenumgebung gibt es einen Gruppenerstellungsassistenten, der dem Erstellungsassistenten für die Site ähnelt.
* Beim Hinzufügen einer Gruppenfunktion zu einer Community-Site-Struktur oder einer Community-Gruppenstruktur ist es konfigurierbar, ob Mitglieder Gruppen aus der Veröffentlichungsumgebung erstellen können.

Von den drei enthaltenen Gruppenvorlagen ist nur die `Reference Group` -Vorlage enthält eine Gruppenfunktion in ihrer Struktur.

Mehrere Facetten von Community-Gruppen sind:

* Erstellung: Neue Gruppe kann auf der Autoreninstanz und optional auf der Veröffentlichungsinstanz erstellt werden
* Kontrolle: kann offen oder geheim sein
* Verschachtelung: Eine Gruppe kann null oder mehr Gruppen enthalten

>[!NOTE]
>
>Community-Gruppen, die in der Veröffentlichungsumgebung vor dem [Existenz der Community-Gruppenkonsole](https://helpx.adobe.com/in/experience-manager/6-3/communities/using/version-history.html#FeaturePack1FP1), wird nicht in der Community-Gruppenkonsole aufgeführt und kann daher nicht über die Konsole geändert werden.

>[!NOTE]
>
>Diese Gruppenkonsole, auf die nur über die Communities Sites-Konsole zugegriffen werden kann, ist nicht mit dem Mitglied zu verwechseln [Gruppenkonsole](members.md) für die Verwaltung von Mitgliedergruppen.
>
>Mitgliedergruppen sind Benutzergruppen, die in der Veröffentlichungsumgebung registriert sind und über die Autorenumgebung mithilfe der [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Gruppenerstellung {#group-creation}

So greifen Sie auf die Gruppenkonsole zu:

* Beim Autor melden Sie sich mit Administratorrechten an
* Über die globale Navigation: **[!UICONTROL Communities > Sites]**
* Wählen Sie einen vorhandenen Community-Site-Ordner aus, um ihn zu öffnen
* Auswählen einer Instanz einer Community-Site im Ordner

   * Die Struktur der Community-Site muss eine Gruppenfunktion enthalten
   * Diese Screenshots stammen aus dem Tutorial Erste Schritte nach [Erstellen von Gruppen in der Veröffentlichungsinstanz](published-site.md)

![chlimage_1-133](assets/chlimage_1-133.png)

Wählen Sie die **[!UICONTROL Gruppenordner]** um es zu öffnen.

Beim Öffnen werden alle vorhandenen Gruppen angezeigt, unabhängig davon, ob sie im Autor- oder Veröffentlichungsmodus erstellt wurden.

In dieser Gruppenkonsole ist es möglich, neue Gruppen zu erstellen.

![chlimage_1-134](assets/chlimage_1-134.png)

* Auswählen **[!UICONTROL Gruppe erstellen]** button

### Schritt 1: Community-Gruppenvorlage {#step-community-group-template}

![multilingualgroup](assets/multilingualgroup.png)

* **[!UICONTROL Community-Gruppentitel]**: Ein Anzeigetitel für die Gruppe.

   Der Titel wird auf der veröffentlichten Site für die Gruppe angezeigt.

* **[!UICONTROL Community-Gruppenbeschreibung]**: Eine Beschreibung der Gruppe.
* **[!UICONTROL Community-Gruppenstamm]**: Der Stammpfad zur Gruppe.

   Der Standardstamm ist die übergeordnete Site, der Stamm kann jedoch an einen beliebigen Ort auf der Website verschoben werden. Es wird nicht empfohlen, sie zu ändern.

* **[!UICONTROL Zusätzliche verfügbare Community-Gruppensprachen]** Menü: Verwenden Sie das Pulldown-Menü, um die verfügbaren Community-Gruppensprachen auszuwählen. Im Menü werden alle Sprachen angezeigt, in denen die übergeordnete Community-Site erstellt wird. Benutzer können in diesem Schritt unter diesen Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.

* **[!UICONTROL Community-Gruppenname]**: Der Name der Stammseite der Gruppe, der in der URL angezeigt wird

   * Überprüfen Sie den Namen, da er nach der Erstellung der Gruppe nicht einfach geändert werden kann.
   * Die Basis-URL wird unter dem `Community Group Name`
   * Hängen Sie für eine gültige URL &quot;.html&quot;an.

      *Beispiel*, `http://localhost:4502/content/sites/mysight/en/mygroup.html`

* **[!UICONTROL Community-Gruppenvorlage]** Menü: Verwenden Sie das Pulldown-Menü, um eine verfügbare [Community-Gruppenvorlage](tools.md).

### Schritt 2: Design {#step-design}

#### GEMEINSCHAFTSGRUPPENTHEMEN {#community-group-theme}

![communityGrouptheme](assets/communitygrouptheme.png)

Das Framework verwendet `Twitter Bootstrap` , um ein responsives, flexibles Design auf die Site zu bringen. Es kann eines der vielen vorab geladenen Bootstrap-Designs ausgewählt werden, um die ausgewählte Community-Gruppenvorlage zu gestalten. Andernfalls kann ein Bootstrap-Design hochgeladen werden.

Wenn diese Option aktiviert ist, wird das Design mit einem undurchsichtigen blauen Häkchen überlagert.

Es ist möglich, ein Design auszuwählen, das sich vom Design der übergeordneten Site unterscheidet.

Nach der Veröffentlichung der Community-Site ist es möglich, [Eigenschaften bearbeiten](#modifying-group-properties) und wählen Sie ein anderes Design aus.

#### GEMEINSCHAFTSGRUPPENBRANCHE {#community-group-branding}

![chlimage_1-135](assets/chlimage_1-135.png)

Community-Site-Branding ist ein Bild, das oben auf jeder Seite als Kopfzeile angezeigt wird. Es ist möglich, ein Banner für die Gruppe anzuzeigen, das sich von anderen Seiten der Site unterscheidet.

Die Bildgröße sollte der erwarteten Anzeige der Seite im Browser und einer Höhe von 120 Pixel entsprechen.

Beachten Sie beim Erstellen oder Auswählen eines Bildes Folgendes:

* Die Bildhöhe wird vom oberen Rand des Bildes auf 120 Pixel zugeschnitten
* Das Bild wird am linken Rand des Browser-Fensters fixiert
* Die Größe des Bildes wird nicht geändert, d. h. wenn die Bildbreite ...

   * Weniger als die Browser-Breite, wird das Bild horizontal wiederholt
   * Größer als die Breite des Browsers, wird das Bild scheinbar zugeschnitten

### Schritt 3: Einstellungen {#step-settings}

#### MODERATION {#moderation}

![chlimage_1-136](assets/chlimage_1-136.png)

Standardmäßig wird die Liste der Moderatoren der übergeordneten Community-Site übernommen.

Es ist möglich, für die Gruppe spezifische Moderatoren hinzuzufügen:

* Suchen Sie nach Mitgliedern (aus der Veröffentlichungsumgebung), um sie als Moderatoren hinzuzufügen.

#### MITGLIEDSCHAFT {#membership}

Die Mitgliedschaftseinstellung ermöglicht die Auswahl einer der drei Möglichkeiten, eine Community-Gruppe zu sichern.

![chlimage_1-137](assets/chlimage_1-137.png)

* Optionale Mitgliedschaft

   Wenn diese Option ausgewählt ist, ist die Community-Gruppe eine öffentliche Gruppe. Mitglieder der Site können an der Gruppe teilnehmen und Beiträge posten, ohne sich explizit der Gruppe anzuschließen. Diese Option ist standardmäßig ausgewählt.
* Erforderliche Mitgliedschaft

   Wenn ausgewählt, ist die Community-Gruppe eine offene Gruppe. Community-Site-Mitglieder können den Inhalt der Gruppe anzeigen, müssen jedoch der Gruppe beitreten, bevor sie Inhalte posten können. Mitglieder werden durch Auswahl von `Join` in der Veröffentlichungsumgebung. Die Option Standard ist nicht ausgewählt.

* Eingeschränkte Mitgliedschaft

   Wenn ausgewählt, ist die Community-Gruppe eine geheime Gruppe. Die Mitglieder der Gemeinschaft müssen ausdrücklich eingeladen werden. Eingeladene Mitglieder werden in das Suchfeld eingegeben. Mitglieder können später über die [Mitglieder und Gruppenkonsolen](members.md) die Autorenumgebung. Die Option Standard ist nicht ausgewählt.

#### MINIATUR {#thumbnail}

![chlimage_1-138](assets/chlimage_1-138.png)

Die Miniaturansicht ist ein Bild, das für die Gruppe bei der Autoren- und Veröffentlichungsinstanz angezeigt wird.

Die optimale Größe für ein Gruppenbild beträgt 170 x 90 Pixel in einem unterstützten Bildformat (z. B. JPG oder PNG).

Wenn kein Bild hinzugefügt wird, wird ein Standardbild angezeigt.

![chlimage_1-139](assets/chlimage_1-139.png)

### Schritt 4: Gruppe erstellen {#step-create-group}

![chlimage_1-140](assets/chlimage_1-140.png)

Falls Anpassungen erforderlich sind, verwenden Sie die **Zurück** -Schaltfläche, um sie zu erstellen.

Einmal **Erstellen** ausgewählt und gestartet wurde, kann die Erstellung der Gruppe nicht unterbrochen werden.

Nach Abschluss des Vorgangs wird die Karte für die neue Unter-Community-Site (Gruppe) in der Communities Sites-Gruppen-Konsole angezeigt. Von dort aus können Autoren Seiteninhalte hinzufügen oder Administratoren können die Eigenschaften der Site ändern.

![createcommunitygroup-1](assets/createcommunitygroup-1.png)

>[!NOTE]
>
>Die Gruppe wird in allen Sprachen erstellt, wie in [Schritt 1: Community-Gruppenvorlage](groups.md#step1communitygrouptemplate) in Zusätzliche verfügbare Community-Gruppensprachen in der Community-Gruppenkonsole der jeweiligen Community-Sites.

## Bearbeiten von Gruppeninhalten {#authoring-group-content}

![chlimage_1-141](assets/chlimage_1-141.png)

Der Seiteninhalt einer Gruppe kann mit denselben Tools wie jede andere AEM erstellt werden. Um die Gruppe für die Bearbeitung zu öffnen, wählen Sie das Symbol Site öffnen aus, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen.

## Ändern von Gruppeneigenschaften {#modifying-group-properties}

Die Eigenschaften einer bestehenden Unter-Community-Site, die beim Erstellen einer Community-Gruppe angegeben wurde, können durch Auswahl des Symbols Site bearbeiten geändert werden, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen:

![chlimage_1-142](assets/chlimage_1-142.png)

Die Details der folgenden Eigenschaften stimmen mit den Beschreibungen überein, die im Abschnitt [Gruppenerstellung](#group-creation) Abschnitt. Jede verschachtelte Gruppe kann geändert werden, unabhängig davon, ob sie in der Veröffentlichungsumgebung oder in der Autorenumgebung erstellt wurde.

![chlimage_1-143](assets/chlimage_1-143.png)

### Standard ändern {#modify-basic}

Das BASIC-Bedienfeld ermöglicht die Änderung von

* Community-Gruppenname
* Community-Gruppenbeschreibung

Der Community-Gruppenname darf nicht geändert werden.

Die Auswahl einer anderen Community-Gruppenvorlage hätte keine Auswirkungen auf eine bestehende Community-Gruppensite, da keine Verbindung zwischen Vorlagen und Sites besteht.

Stattdessen wird die [STRUKTUR](#modify-structure) der Unter-Community geändert werden.

### Struktur ändern {#modify-structure}

Das Bedienfeld STRUKTUR ermöglicht die Änderung der Struktur, die ursprünglich aus der Community-Gruppenvorlage erstellt wurde, die beim Erstellen der Unter-Community-Site aus der Autoren- oder Veröffentlichungsumgebung ausgewählt wurde. Im Bereich können Sie

* Zusätzliche Drag-and-Drop-Funktionen [Community-Funktionen](functions.md) in die Site-Struktur
* Auf einer Instanz einer Community-Funktion in der Site-Struktur:

   * **`gear icon`**

      Einstellungen bearbeiten, einschließlich Anzeigentitel und URL-Name sowie [privilegierte Mitgliedergruppen](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      Entfernen (Löschen) von Funktionen aus der Site-Struktur

   * **`grid icon`**

      Ändern Sie die Reihenfolge der Funktionen, wie sie in der Navigationsleiste auf oberster Ebene der Site angezeigt werden.

>[!CAUTION]
>
>Der Anzeigentitel kann ohne Nebenwirkungen geändert werden. Es wird jedoch nicht empfohlen, den URL-Namen einer Community-Funktion zu bearbeiten, die zu einer Community-Site gehört.
>
>Wenn Sie beispielsweise die URL umbenennen, werden vorhandene UGC nicht verschoben, sodass der UGC-Wert &quot;verloren&quot;wird.

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;muss *not* die *first noch die einzige* in der Site-Struktur.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](functions.md#page-function), muss zuerst eingeschlossen und aufgelistet werden.

#### Beispiel: Hinzufügen einer Kalenderfunktion zu einer SubCommunity-Struktur (Gruppe) {#example-adding-a-calendar-function-to-a-sub-community-group-structure}

![chlimage_1-144](assets/chlimage_1-144.png)

### Design ändern {#modify-design}

Das DESIGN-Bedienfeld ermöglicht die Änderung des Designs:

* [Community-Gruppen-Design](#community-group-theme)
* [Community-Gruppen-Branding](#community-group-branding)

   * Scrollen Sie zum unteren Rand des Bedienfelds, um das Markenbild zu ändern.

### Einstellungen ändern {#modify-settings}

Das Bedienfeld &quot;EINSTELLUNGEN&quot;ermöglicht das Hinzufügen einer Community [Moderatoren](#moderation).

### Mitgliedschaft ändern {#modify-membership}

Die [MITGLIEDSCHAFT](#membership) -Bedienfeld ist nur informativ. Es ist nicht möglich, die Art der festgelegten Gruppenmitgliedschaft zu ändern, unabhängig davon, ob sie optional, erforderlich oder eingeschränkt ist.

### Miniaturansicht ändern {#modify-thumbnail}

Die [THUMBNAIL](#thumbnail) -Bedienfeld kann ein Bild hochgeladen werden, das die Community-Gruppe für Site-Besucher in der Veröffentlichungsumgebung sowie in der Gruppenkonsole der Communities-Site in der Autorenumgebung darstellt.

## Veröffentlichen der Gruppe {#publishing-the-group}

![chlimage_1-145](assets/chlimage_1-145.png)

Nachdem eine Community-Gruppe neu erstellt oder geändert wurde, ist es möglich, die Gruppe zu veröffentlichen (zu aktivieren), indem Sie die `Publish Site` Symbol.

Nachdem die Gruppe erfolgreich veröffentlicht wurde, wird eine Meldung angezeigt:

![chlimage_1-146](assets/chlimage_1-146.png)

>[!CAUTION]
>
>Die übergeordnete Community-Site und die übergeordneten Gruppen sollten bereits veröffentlicht worden sein.
>
>Die Community-Site und verschachtelte Gruppen sollten von oben nach unten veröffentlicht werden.

## Löschen der Gruppe {#deleting-the-group}

![deleteicon](assets/deleteicon.png)

Löschen Sie eine Gruppe aus der Community-Gruppenkonsole, indem Sie auf das Symbol Gruppe löschen klicken, das beim Bewegen der Maus über die Gruppe angezeigt wird.

Dadurch werden alle mit der Gruppe verknüpften Elemente entfernt, z. B. der gesamte Inhalt der Gruppe wird dauerhaft gelöscht und die Benutzermitgliedschaften werden aus dem System entfernt.
