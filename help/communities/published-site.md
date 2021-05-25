---
title: Erlebnis der veröffentlichten Site
seo-title: Erlebnis der veröffentlichten Site
description: Navigieren zu einer veröffentlichten Site
seo-description: Navigieren zu einer veröffentlichten Site
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
exl-id: 8f716a59-1116-4855-baeb-3997de71b55f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 2%

---

# Erleben Sie die veröffentlichte Site {#experience-the-published-site}

## Navigieren Sie zur neuen Site auf der Veröffentlichungsinstanz {#browse-to-new-site-on-publish}

Nachdem die neu erstellte Communities-Site veröffentlicht wurde, navigieren Sie zur URL, die beim Erstellen der Site angezeigt wird, aber auf dem Veröffentlichungsserver, z. B.

* Autoren-URL = http://localhost:4502/content/sites/engage/en.html
* Veröffentlichungs-URL = http://localhost:4503/content/sites/engage/en.html

Um Verwirrungen zu vermeiden, welches Mitglied bei der Autoren- und Veröffentlichungsinstanz angemeldet ist, wird empfohlen, für jede Instanz unterschiedliche Browser zu verwenden.

Bei der ersten Ankunft auf der veröffentlichten Site wäre der Site-Besucher in der Regel nicht bereits angemeldet und anonym.

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-311](assets/chlimage_1-311.png)

## Anonymer Site-Besucher {#anonymous-site-visitor}

Einem anonymen Site-Besucher wird in der Benutzeroberfläche Folgendes angezeigt:

* Titel der Site. Tutorial zu den ersten Schritten
* Kein Profillink
* Keine Nachrichtenverbindung
* Kein Benachrichtigungslink
* Suchfeld
* Anmelde-Link
* Das Markenbanner
* Menülinks für die Komponenten, die in der Referenz-Site-Vorlage enthalten sind

Wenn Sie verschiedene Links auswählen, befinden sie sich im schreibgeschützten Modus.

## Verhindern des anonymen Zugriffs auf JCR {#prevent-anonymous-access-on-jcr}

Durch eine bekannte Einschränkung wird der Community-Site-Inhalt anonymen Besuchern über JCR-Inhalt und JSON bereitgestellt, obwohl **Anonymen Zugriff zulassen** für den Site-Inhalt deaktiviert ist. Dieses Verhalten kann jedoch mithilfe von Sling-Einschränkungen als Problemumgehung gesteuert werden.

Gehen Sie wie folgt vor, um den Inhalt Ihrer Community-Site vor dem Zugriff anonymer Benutzer durch jcr-Inhalte und JSON zu schützen:

1. Wechseln Sie in der AEM-Autoreninstanz zu https://&lt;Host>:&lt;Port>/editor.html/content/site/&lt;Site-Name>.html.

   >[!NOTE]
   >
   >Gehen Sie nicht zur lokalisierten Site.

1. Navigieren Sie zu **[!UICONTROL Seiteneigenschaften]**.

   ![site-authentication](assets/site-authentication.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL Erweitert]**.

   ![page-properties](assets/page-properties.png)

1. Aktivieren Sie **[!UICONTROL Authentifizierungspflicht]**.
1. Fügen Sie den Pfad der Anmeldeseite hinzu. Beispiel: `/content/......./GetStarted`.
1. Veröffentlichen Sie die Seite.

## Vertrauenswürdige Community-Mitglieder {#trusted-community-member}

Dieses Erlebnis setzt voraus, dass [Aaron McDonald](tutorials.md#demo-users) die Rollen von [Community Manager und Moderator](create-site.md#roles) zugewiesen wurde. Wenn nicht, kehren Sie zur Autorenumgebung zurück zu [ändern Sie die Site-Einstellungen](sites-console.md#modifying-site-properties) und wählen Sie Aaron McDonald als Community-Manager und Moderator aus.

Wählen Sie in der oberen rechten Ecke `Log in` aus und signieren Sie mit dem Benutzernamen &quot;aaron.mcdonald@mailinator.com&quot; und dem Kennwort &quot;password&quot;. Beachten Sie die Möglichkeit, sich mit Twitter- oder Facebook-Anmeldeinformationen anzumelden.

![chlimage_1-312](assets/chlimage_1-312.png)

Nach der Anmeldung erscheint ein neues Menüelement `Administration`, das angezeigt wird, da dem Mitglied die Rolle Moderator zugewiesen wurde. Die Auswahl verschiedener Links ist interessanter.

![chlimage_1-313](assets/chlimage_1-313.png)

Beachten Sie, dass die Kalenderseite die Startseite ist, da die ausgewählte Referenz-Site-Vorlage zuerst die Kalenderfunktion, gefolgt von der Aktivitäts-Stream-Funktion, der Forumsfunktion usw. enthält. Diese Struktur ist in der Konsole [Site-Vorlage](sites.md#edit-site-template) oder beim Ändern der Site-Eigenschaften in der Autorenumgebung sichtbar:

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>Weitere Informationen zu Communities-Komponenten und -Funktionen finden Sie unter
>
>* [Communities-Komponenten](author-communities.md)  (für Autoren)
>* [Komponenten-, Funktionen- und Funktionsgrundlagen](essentials.md)  (für Entwickler)

>



## Forum link {#forum-link}

Klicken Sie auf den Link Forum , um die grundlegende Forumsfunktion anzuzeigen.

Mitglieder können ein neues Thema posten oder einem Thema folgen.

Besucher der Site können Beiträge auf verschiedene Weise anzeigen und sortieren.

![chlimage_1-315](assets/chlimage_1-315.png)

## Gruppenlink {#groups-link}

Da Aaron ein Gruppenadministrator ist, kann Aaron durch Auswahl des Links Gruppen eine neue Community-Gruppe erstellen, indem es eine Gruppenvorlage und ein Bild auswählt, ob die Gruppe offen oder geheim ist, und Mitglieder einlädt.

Dies ist ein Beispiel, bei dem eine Gruppe in der Veröffentlichungsumgebung erstellt wird.

Gruppen können auch in der Autorenumgebung erstellt und innerhalb der Community-Site in der Autorenumgebung verwaltet werden (die [Community-Gruppenkonsole](groups.md)). Das Erlebnis von [Erstellen von Gruppen für Autor](nested-groups.md) ist als Nächstes in diesem Tutorial verfügbar.

![chlimage_1-316](assets/chlimage_1-316.png)

Erstellen einer Referenzgruppe:

1. Wählen Sie **[!UICONTROL Neue Gruppe]**
1. **[!UICONTROL Registerkarte „Settings“]**
   * Gruppenname: `Sports`
   * Beschreibung: `A parent group for various sporting groups`
   * Gruppen-URL-Name: `sports`
   * Wählen Sie `Open Group` aus (erlauben Sie jedem Community-Mitglied die Teilnahme, indem Sie Mitglied werden).
1. **[!UICONTROL Registerkarte &quot;Vorlage&quot;]**
   * Wählen Sie `Reference Group` aus (enthält eine Gruppenfunktion in ihrer Struktur, um verschachtelte Gruppen zuzulassen)
1. Wählen Sie **[!UICONTROL Gruppe erstellen]**

![chlimage_1-317](assets/chlimage_1-317.png)

Nachdem eine neue Gruppe erstellt wurde, wählen Sie **die neue Gruppe &quot;Sport**&quot;aus, um zwei Gruppen (verschachtelt) darin zu erstellen. Da eine Site-Struktur nicht mit der Funktion &quot;Gruppen&quot;beginnen kann, müssen Sie nach dem Öffnen der Gruppe &quot;Sport&quot;den Link Gruppen auswählen:

![chlimage_1-318](assets/chlimage_1-318.png)

Der zweite Satz von Links, angefangen mit `Blog`, gehört zur aktuell ausgewählten Gruppe, der `Sports`Gruppe. Durch Auswahl des Links &quot;Sport&quot; `Groups` können zwei Gruppen innerhalb der Gruppe &quot;Sport&quot;verschachtelt werden.

Fügen Sie beispielsweise zwei n `ew groups.` hinzu.

* Eins mit dem Namen `Baseball`
   * Lassen Sie es als `Open Group` (erforderliche Mitgliedschaft) eingestellt
   * Wählen Sie auf der Registerkarte Vorlagen die Option `Conversational Group` aus.
* Eins mit dem Namen `Gymnastics`
   * Ändern Sie die Einstellung in `Member Only Group` (eingeschränkte Mitgliedschaft)
   * Wählen Sie auf der Registerkarte Vorlagen die Option `Conversational Group` aus.

**Hinweis**:

* Eine Aktualisierung der Seite kann erforderlich sein, bevor beide Gruppen angezeigt werden
* Diese Vorlage enthält *nicht *die Funktion &quot;Gruppen&quot;, sodass keine weitere Verschachtelung von Gruppen möglich ist.
* Auf der Autoreninstanz bietet die [Gruppenkonsole](groups.md) eine dritte Wahl - eine `Public Group` (optionale Mitgliedschaft)

Nachdem beide Gruppen erstellt wurden, wählen Sie die Baseball-Gruppe, eine offene Gruppe, und beachten Sie die Links: `Discussions` `What's New` `Members`
Die Links der Gruppe werden unter den Links der Hauptseite angezeigt und zeigen Folgendes an:

![chlimage_1-319](assets/chlimage_1-319.png)

Navigieren Sie auf der Autoreninstanz mit Administratorrechten zur Konsole [Communities-Gruppen](members.md) und fügen Sie Weston McCall zur Gruppe `Community Engage Gymnastics <uid> Members` hinzu.

Melden Sie sich weiterhin als Aaron McDonald an und sehen Sie sich die Gruppen in der Sportgruppe als anonymen Site-Besucher an:

* Von der Startseite
* Link auswählen `Groups`Link
* Link auswählen `Sports`Link
* Wählen Sie den Link &quot;Sports&#39; `Groups`aus

Nur die Baseballgruppe wird sichtbar sein.

Melden Sie sich als Weston McCall (weston.mccall@dodgit.com / Kennwort) an und navigieren Sie zum selben Speicherort. Beachten Sie, dass Weston die Gruppe `Join` öffnen `Baseball` und entweder `enter or Leave` die private Gruppe `Gymnastics`kann.

![chlimage_1-320](assets/chlimage_1-320.png)

## Web Page link {#web-page-link}

Zeigen Sie die grundlegende Webseite der Site an, indem Sie den Link Webseite auswählen. Die standardmäßigen AEM-Authoring-Tools können verwendet werden, um Inhalte zu dieser Seite in der Autorenumgebung hinzuzufügen.

Wechseln Sie beispielsweise zur Instanz **author**, öffnen Sie den Ordner `engage` in der Konsole [Communities Sites](sites-console.md) und wählen Sie das Symbol **Site öffnen** aus, um in den Bearbeitungsmodus für Autoren zu wechseln. Wählen Sie dann den Vorschaumodus aus, um den Link `Web Page`auszuwählen, und wählen Sie dann den Bearbeitungsmodus, um die Komponenten Titel und Text hinzuzufügen. Veröffentlichen Sie zuletzt entweder nur die Seite oder die gesamte Site neu.

![chlimage_1-321](assets/chlimage_1-321.png)

## Administrationslink {#administration-link}

Wenn das Community-Mitglied über Moderationsberechtigungen verfügt, wird der Link Administration angezeigt. Wenn Sie ihn auswählen, wird der veröffentlichte Community-Inhalt angezeigt und es kann [moderiert](moderate-ugc.md) in einer Weise sein, die der [Moderationskonsole](moderation.md) in der Autorenumgebung ähnelt.

Verwenden Sie die Zurück-Schaltfläche des Browsers, um zur veröffentlichten Site zurückzukehren. Die meisten Konsolen können nicht über die globale Navigation in der Veröffentlichungsumgebung aufgerufen werden.

![chlimage_1-322](assets/chlimage_1-322.png)

## Selbstregistrierung {#self-registration}

Nach dem Abmelden ist es möglich, eine neue Benutzerregistrierung zu erstellen.

* Wählen Sie nun eine der folgenden Optionen aus `Log In`
* Wählen Sie nun eine der folgenden Optionen aus `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

Standardmäßig ist die E-Mail-Adresse die Anmelde-ID. Wenn diese Option deaktiviert ist, kann der Besucher seine eigene Anmelde-ID (Benutzername) eingeben. Der Benutzername muss in der Veröffentlichungsumgebung eindeutig sein.

Nachdem Sie den Namen, die E-Mail-Adresse und das Kennwort des Benutzers angegeben haben, können Sie durch die Auswahl von `Sign Up`den Benutzer erstellen und signieren.

Nach der Anmeldung ist die erste angezeigte Seite ihre `Profile`Seite, die sie personalisieren können.

![chlimage_1-325](assets/chlimage_1-325.png)

Wenn das Mitglied seine Anmelde-ID vergisst, kann es mithilfe seiner E-Mail-Adresse abgerufen werden.

![chlimage_1-326](assets/chlimage_1-326.png)
