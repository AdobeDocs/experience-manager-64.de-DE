---
title: Konsole für Community-Gruppen
seo-title: Konsole für Community-Gruppen
description: In der Gruppenkonsole können Sie Community-Gruppen erstellen
seo-description: In der Gruppenkonsole können Sie Community-Gruppen erstellen
uuid: 7dac2d1b-78fc-4b39-a2cb-100f1e220c23
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1293c01a-7308-494a-ab48-bd9938205b81
pagetitle: Community Groups Console
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1643'
ht-degree: 3%

---


# Konsole für Community-Gruppen {#community-groups-console}

Die Konsole &quot;Gruppen&quot;bietet Zugriff auf das Erstellen von Community-Gruppen, wenn die [Vorlagenstruktur](sites-console.md#step1) einer Community-Site die [groups-Funktion](functions.md#groups-function) enthält.

* Gruppen können in anderen Gruppen verschachtelt sein. Dies geschieht, wenn die [Struktur der neuen Gruppe](tools-groups.md) die Funktion groups enthält.
* Nur für die Umgebung des Autors gibt es einen Assistenten zum Erstellen von Gruppen, der dem Assistenten zum Erstellen der Site ähnelt.
* Ob Mitglieder Gruppen aus der Umgebung &quot;Veröffentlichen&quot;erstellen können, ist beim Hinzufügen einer Gruppenfunktion zu einer Community-Site- oder Community-Gruppenstruktur konfigurierbar.

Von den drei enthaltenen Gruppenvorlagen enthält nur die `Reference Group`-Vorlage eine Gruppenfunktion in ihrer Struktur.

Mehrere Facetten von Gemeinschaftsgruppen sind:

* Erstellung: Neue Gruppe kann beim Autor und optional beim Veröffentlichen erstellt werden
* Kontrolle: kann offen oder geheim sein
* Verschachtelung: eine Gruppe kann null oder mehr Gruppen enthalten

>[!NOTE]
>
>Gemeinschaftsgruppen, die in der Umgebung zum Veröffentlichen vor dem [Vorhandensein der Community Groups-Konsole](https://helpx.adobe.com/in/experience-manager/6-3/communities/using/version-history.html#FeaturePack1FP1) erstellt wurden, werden nicht in der Community Groups-Konsole aufgeführt und können daher nicht mithilfe der Konsole geändert werden.

>[!NOTE]
>
>Diese Gruppenkonsole, die nur über die Communities Sites-Konsole zugänglich ist, ist nicht mit dem Mitglied [Groups console](members.md) für die Verwaltung von Mitgliedsgruppen zu verwechseln.
>
>Mitgliedergruppen sind Benutzergruppen, die in der Umgebung &quot;Veröffentlichen&quot;registriert sind und von der Autorengruppe aus über den [Tunneldienst](deploy-communities.md#tunnel-service-on-author) aufgerufen werden können.

## Gruppenerstellung {#group-creation}

So greifen Sie auf die Konsole &quot;Gruppen&quot;zu:

* Melden Sie sich beim Autor mit Administratorberechtigungen an
* Aus globaler Navigation: **[!UICONTROL Communities > Sites]**
* Wählen Sie einen vorhandenen Community-Site-Ordner aus, um ihn zu öffnen
* Wählen Sie eine Instanz einer Community-Site im Ordner aus

   * Die Struktur der Community-Site muss eine Gruppenfunktion enthalten
   * Diese Screenshots stammen aus dem Tutorial &quot;Erste Schritte&quot;, nach dem [Erstellen von Gruppen im Veröffentlichungsmodus](published-site.md)

![chlimage_1-133](assets/chlimage_1-133.png)

Wählen Sie den Ordner **[!UICONTROL Gruppen]** aus, um ihn zu öffnen.

Beim Öffnen werden alle vorhandenen Gruppen angezeigt, unabhängig davon, ob sie beim Autor oder beim Veröffentlichen erstellt wurden.

In dieser Konsole &quot;Gruppen&quot;können neue Gruppen erstellt werden.

![chlimage_1-134](assets/chlimage_1-134.png)

* Schaltfläche **[!UICONTROL Gruppe erstellen]**

### Schritt 1: Community-Gruppenvorlage {#step-community-group-template}

![multilingualgroup](assets/multilingualgroup.png)

* **[!UICONTROL Community-Gruppentitel]**: Ein Anzeigentitel für die Gruppe.

   Der Titel wird auf der veröffentlichten Site für die Gruppe angezeigt.

* **[!UICONTROL Community-Gruppenbeschreibung]**: Eine Beschreibung der Gruppe.
* **[!UICONTROL Community-Gruppenstamm]**: Der Stammpfad zur Gruppe.

   Der Standardstamm ist die übergeordnete Site, der Stammordner kann jedoch an einen beliebigen Ort innerhalb der Website verschoben werden. Es wird nicht empfohlen, es zu ändern.

* **[!UICONTROL Menü &quot;Zusätzliche verfügbare Sprachen in Community-Gruppen&quot;]** : Verwenden Sie das Pulldown-Menü, um die verfügbaren Gemeinschaftsgruppensprachen auszuwählen. Das Menü zeigt alle Sprachen an, in denen die übergeordnete Community-Site erstellt wurde. Benutzer können in diesem Schritt eine der folgenden Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Konsole &quot;Gruppen&quot;der jeweiligen Community-Sites erstellt.

* **[!UICONTROL Community-Gruppenname]**: Der Name der Stammseite der Gruppe, die in der URL angezeigt wird

   * Überprüfen Sie die Dublette, da der Name nach dem Erstellen der Gruppe nicht einfach geändert werden kann.
   * Die Basis-URL wird unter dem `Community Group Name` angezeigt
   * Für eine gültige URL hängen Sie &quot;.html&quot;an

      *Beispiel*, `http://localhost:4502/content/sites/mysight/en/mygroup.html`

* **[!UICONTROL Community-]** Gruppenvorlagen-Menü: Verwenden Sie das Pulldown-Menü, um eine verfügbare  [Community-Gruppenvorlage](tools.md) auszuwählen.

### Schritt 2: Design {#step-design}

#### GEMEINSCHAFTSGRUPPENTHEMEN {#community-group-theme}

![communityGrouptheme](assets/communitygrouptheme.png)

Das Framework verwendet [Twitter-Bootstrap](https://twitterbootstrap.org/), um ein reaktionsfähiges, flexibles Design auf die Site zu bringen. Es kann eines der vielen vorgeladenen Bootstrap-Themen ausgewählt werden, um die ausgewählte Community-Gruppenvorlage zu gestalten, oder ein Bootstrap-Design wird hochgeladen.

Wenn diese Option aktiviert ist, wird das Design mit einem undurchsichtigen blauen Häkchen überlagert.

Es ist möglich, ein Design auszuwählen, das sich vom Design der übergeordneten Site unterscheidet.

Nach der Veröffentlichung der Community-Site ist es möglich, die Eigenschaften [zu bearbeiten und ein anderes Design auszuwählen.](#modifying-group-properties)

#### GEMEINSCHAFTSGRUPPENBRANCHE {#community-group-branding}

![chlimage_1-135](assets/chlimage_1-135.png)

Das Branding einer Community-Site ist ein Bild, das als Kopfzeile am oberen Rand jeder Seite angezeigt wird. Es ist möglich, ein Banner für die Gruppe anzuzeigen, das sich von anderen Seiten der Site unterscheidet.

Das Bild sollte so groß sein, dass es im Browser wie erwartet angezeigt wird, und 120 Pixel hoch.

Beachten Sie beim Erstellen oder Auswählen eines Bildes Folgendes:

* Die Bildhöhe wird auf 120 Pixel abgeschnitten, gemessen von der oberen Kante des Bilds
* Das Bild wird am linken Rand des Browserfensters fixiert
* Die Bildgröße wird nicht geändert, d. h., wenn die Bildbreite ...

   * Weniger als die Browserbreite, wird das Bild horizontal wiederholt
   * Größer als die Browserbreite, scheint das Bild abgeschnitten zu sein

### Schritt 3: Einstellungen {#step-settings}

#### MODERATION {#moderation}

![chlimage_1-136](assets/chlimage_1-136.png)

Standardmäßig wird die Liste der Moderatoren auf der übergeordneten Community-Site geerbt.

Es ist möglich, für die Gruppe spezifische Moderatoren hinzuzufügen:

* Nach Mitgliedern suchen (aus der Umgebung der Veröffentlichung), um sie als Moderatoren hinzuzufügen

#### MITGLIEDSCHAFT {#membership}

Die Mitgliedschaftseinstellung ermöglicht die Auswahl einer der drei Möglichkeiten, eine Community-Gruppe zu sichern.

![chlimage_1-137](assets/chlimage_1-137.png)

* Optionale Mitgliedschaft

   Bei Auswahl dieser Option ist die Community-Gruppe eine öffentliche Gruppe. Site-Mitglieder können an der Gruppe und an Beiträgen teilnehmen, ohne explizit der Gruppe beizutreten. Diese Option ist standardmäßig ausgewählt.
* Erforderliche Mitgliedschaft

   Wenn diese Option aktiviert ist, ist die Community-Gruppe eine offene Gruppe. Die Mitglieder der Community-Site können den Gruppeninhalt Ansichten vornehmen, müssen sich jedoch der Gruppe anschließen, bevor sie Inhalte veröffentlichen können. Mitglieder werden durch Klicken auf die Schaltfläche `Join` in der Umgebung zum Veröffentlichen hinzugefügt. &quot;Standard&quot;ist nicht ausgewählt.

* Eingeschränkte Mitgliedschaft

   Wenn diese Option aktiviert ist, ist die Community-Gruppe eine geheime Gruppe. Die Mitglieder der Gemeinschaft müssen ausdrücklich eingeladen werden. Eingeladene Mitglieder werden in das Suchfeld eingegeben. Mitglieder können später mit der Umgebung [Mitglieder und Gruppen hinzugefügt werden. ](members.md) &quot;Standard&quot;ist nicht ausgewählt.

#### MINIATUR {#thumbnail}

![chlimage_1-138](assets/chlimage_1-138.png)

Die Miniaturansicht ist ein Bild, das bei Autor und Veröffentlichung für die Gruppe angezeigt wird.

Die optimale Größe für ein Gruppenbild beträgt 170 x 90 Pixel in einem unterstützten Bildformat (z. B. JPG oder PNG).

Wenn kein Bild hinzugefügt wird, wird ein Standardbild angezeigt.

![chlimage_1-139](assets/chlimage_1-139.png)

### Schritt 4: Gruppe erstellen {#step-create-group}

![chlimage_1-140](assets/chlimage_1-140.png)

Wenn Anpassungen erforderlich sind, verwenden Sie die Schaltfläche **Zurück**, um sie vorzunehmen.

Wenn **Create** ausgewählt und gestartet wurde, kann der Vorgang zum Erstellen der Gruppe nicht unterbrochen werden.

Nach Abschluss des Vorgangs wird die Karte für die neue Subcommunity-Site (Gruppe) in der Communities Sites Groups-Konsole angezeigt, von der aus Autoren Seiteninhalte hinzufügen können oder Administratoren die Eigenschaften der Site ändern können.

![createccommunity-group-1](assets/createcommunitygroup-1.png)

>[!NOTE]
>
>Die Gruppe wird in allen Sprachen erstellt, wie in [Schritt 1 angegeben: Community-Gruppenvorlage](groups.md#step1communitygrouptemplate) in &quot;Zusätzliche verfügbare Community-Gruppensprachen&quot;in der Community-Gruppenkonsole der jeweiligen Community-Sites.

## Authoring-Gruppeninhalt {#authoring-group-content}

![chlimage_1-141](assets/chlimage_1-141.png)

Der Seiteninhalt einer Gruppe kann mit denselben Werkzeugen wie jede andere AEM erstellt werden. Um die Gruppe zum Authoring zu öffnen, wählen Sie das Symbol &quot;Site öffnen&quot;, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen.

## Ändern der Gruppeneigenschaften {#modifying-group-properties}

Die Eigenschaften einer bestehenden Subcommunity-Site, die während des Community-Gruppenerstellungsprozesses angegeben wurden, können geändert werden, indem Sie das Symbol &quot;Site bearbeiten&quot;auswählen, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppenkarte bewegen:

![chlimage_1-142](assets/chlimage_1-142.png)

Die Details der folgenden Eigenschaften stimmen mit den Beschreibungen im Abschnitt [Gruppenerstellung](#group-creation) überein. Verschachtelte Gruppen können geändert werden, unabhängig davon, ob sie in der Umgebung &quot;Veröffentlichen&quot;oder in der Umgebung &quot;Autor&quot;erstellt wurden.

![chlimage_1-143](assets/chlimage_1-143.png)

### Basic {#modify-basic} ändern

Das BASIC-Bedienfeld ermöglicht die Änderung von

* Community-Gruppenname
* Community-Gruppenbeschreibung

Der Community-Gruppenname darf nicht geändert werden.

Die Auswahl einer anderen Community-Gruppenvorlage hätte keine Auswirkungen auf eine bestehende Community-Gruppensite, da keine Verbindung zwischen Vorlagen und Sites bestehen bleibt.

Stattdessen kann die [STRUKTUR](#modify-structure) der Untergemeinschaft geändert werden.

### Struktur ändern {#modify-structure}

Das STRUKTURbedienfeld ermöglicht die Änderung der Struktur, die ursprünglich aus der Community-Gruppenvorlage erstellt wurde, die beim Erstellen der Unter-Community-Site entweder aus der Autor- oder der Veröffentlichungs-Umgebung ausgewählt wurde. Über den Bereich können Sie

* Ziehen Sie zusätzliche [Community-Funktionen](functions.md) in die Site-Struktur.
* Auf einer Instanz einer Community-Funktion in der Site-Struktur:

   * **`gear icon`**

      Einstellungen bearbeiten, einschließlich des Anzeigentitels und des URL-Namens sowie der Gruppen [privilegierter Mitglieder](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      Entfernen (Löschen) von Funktionen aus der Site-Struktur

   * **`grid icon`**

      Die Reihenfolge der Funktionen ändern, die in der Navigationsleiste auf der obersten Navigationsebene der Site angezeigt werden

>[!CAUTION]
>
>Der Anzeigentitel kann ohne Nebenwirkungen geändert werden, es wird jedoch nicht empfohlen, den URL-Namen einer Community-Funktion zu bearbeiten, die zu einer Community-Site gehört.
>
>Wenn Sie beispielsweise die URL umbenennen, wird die vorhandene UGC nicht verschoben, sodass die UGC verliert wird.

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;darf weder die Funktion *first noch die Funktion* in der Sitestruktur sein.**
>
>Jede andere Funktion, wie z. B. die Funktion [page](functions.md#page-function), muss eingeschlossen und zuerst aufgelistet werden.

#### Beispiel: Hinzufügen einer Kalenderfunktion zu einer SubCommunity-(Gruppen-)Struktur {#example-adding-a-calendar-function-to-a-sub-community-group-structure}

![chlimage_1-144](assets/chlimage_1-144.png)

### Design ändern {#modify-design}

Das DESIGN-Bedienfeld ermöglicht die Änderung des Designs:

* [Community-Gruppen-Design](#community-group-theme)
* [Community-Gruppen-Branding](#community-group-branding)

   * Blättern Sie nach unten im Bedienfeld, um das Markenbild zu ändern

### Einstellungen ändern {#modify-settings}

Das Bedienfeld &quot;EINSTELLUNGEN&quot;ermöglicht es, Community [Moderatoren](#moderation) hinzuzufügen.

### Mitgliedschaft ändern {#modify-membership}

Das Fenster [MEMBERSHIP](#membership) enthält nur Informationen. Es ist nicht möglich, die Art der Gruppenmitgliedschaft zu ändern, unabhängig davon, ob sie freiwillig, erforderlich oder eingeschränkt ist.

### Miniaturansicht ändern {#modify-thumbnail}

Das Bedienfeld [THUMBNAIL](#thumbnail) ermöglicht es, ein Bild hochzuladen, das die Community-Gruppe für Site-Besucher in der Veröffentlichungs-Umgebung sowie in der Communities Site-Gruppenkonsole in der Autor-Umgebung darstellt.

## Veröffentlichen der Gruppe {#publishing-the-group}

![chlimage_1-145](assets/chlimage_1-145.png)

Nachdem eine Community-Gruppe neu erstellt oder geändert wurde, kann die Gruppe durch Auswahl des Symbols `Publish Site` veröffentlicht (aktiviert) werden.

Nachdem die Gruppe erfolgreich veröffentlicht wurde, wird eine Meldung angezeigt:

![chlimage_1-146](assets/chlimage_1-146.png)

>[!CAUTION]
>
>Die übergeordnete Community-Site und die übergeordneten Gruppen hätten bereits veröffentlicht werden sollen.
>
>Die Community-Site und verschachtelte Gruppen sollten von oben nach unten veröffentlicht werden.

## Löschen der Gruppe {#deleting-the-group}

![deleteicon](assets/deleteicon.png)

Löschen Sie eine Gruppe aus der Community-Gruppenkonsole, indem Sie auf das Symbol &quot;Gruppe löschen&quot;klicken, das angezeigt wird, wenn Sie den Mauszeiger über die Gruppe halten.

Dadurch werden alle mit der Gruppe verknüpften Elemente entfernt, zum Beispiel wird der gesamte Inhalt der Gruppe dauerhaft gelöscht und die Benutzermitgliedschaften werden aus dem System entfernt.
