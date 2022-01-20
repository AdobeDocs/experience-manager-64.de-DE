---
title: Erlebnis der veröffentlichten Site
seo-title: Experience the Published Site
description: Auf einer veröffentlichten Site zur Aktivierung navigieren
seo-description: Browse to a published site for enablement
uuid: 1bfefa8a-fd9c-4ca8-b2ff-add79776c8ae
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 26715b94-e2ea-4da7-a0e2-3e5a367ac1cd
exl-id: bdf91013-2136-464a-a637-a3047144ec98
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 3%

---

# Erlebnis der veröffentlichten Site {#experience-the-published-site}


**[⇐ Erstellen und Zuweisen von Aktivierungsressourcen](resource.md)**

## Navigieren zur neuen Site bei der Veröffentlichung {#browse-to-new-site-on-publish}

Nachdem die neu erstellte Community-Site und ihre Aktivierungsressourcen und der Lernpfad veröffentlicht wurden, können Sie die Seite &quot;Aktivierungstutorial&quot;nutzen.

Beginnen Sie mit dem Durchsuchen der URL, die beim Erstellen der Site angezeigt wird, aber auf dem Veröffentlichungsserver, z. B.

* Autoren-URL = [http://localhost:4502/content/sites/enable/en.html](http://localhost:4502/content/sites/enable/en.html)
* Veröffentlichungs-URL = [http://localhost:4503/content/sites/enable/en.html](http://localhost:4503/content/sites/enable/en.html)

Wenn die Variable [Standard-Startseite festgelegt](enablement-create-site.md#changethedefaulthomepage), und navigieren Sie dann einfach zu [http://localhost:4503/](http://localhost:4503/) sollte die Site starten.

Bei der ersten Ankunft auf der veröffentlichten Site wäre der Site-Besucher in der Regel nicht bereits angemeldet und anonym.

**http://localhost:4503/content/sites/enable/en.html**

![chlimage_1-433](assets/chlimage_1-433.png)

## Anonymer Site-Besucher {#anonymous-site-visitor}

Einem anonymen Site-Besucher wird sofort die Anmeldeseite für diese private Aktivierungs-Community-Site angezeigt. Beachten Sie, dass es keine Option gibt, sich selbst zu registrieren oder sich bei Facebook oder Twitter anzumelden.

Beachten Sie, dass auf dieser Homepage vier Menüpunkte angezeigt werden: `Assignments, Ski Catalog, What's New` und `Discussions`, jedoch kann keine erreicht werden, ohne sich anzumelden.

>[!NOTE]
>
>Es ist möglich, anonymen Zugriff auf eine Aktivierungs-Site zu gewähren, ohne dass Besucher der Site sich selbst registrieren können.\
>Wenn eine Aktivierungsressource auf `show in catalog` und `allow anonymous access`können anonyme Site-Besucher Ressourcen im Katalog anzeigen.

### Verhindern des anonymen Zugriffs auf JCR {#prevent-anonymous-access-on-jcr}

Bei einer bekannten Einschränkung wird der Community-Site-Inhalt anonymen Besuchern über jcr-Inhalte und json bereitgestellt, obwohl **[!UICONTROL Anonymen Zugriff zulassen]** für den Inhalt der Site deaktiviert ist. Dieses Verhalten kann jedoch mithilfe von Sling-Einschränkungen als Problemumgehung gesteuert werden.

Gehen Sie wie folgt vor, um den Inhalt Ihrer Community-Site vor dem Zugriff anonymer Benutzer durch jcr-Inhalte und JSON zu schützen:

1. Wechseln Sie in der AEM-Autoreninstanz zu https://&lt;host>:&lt;port>/editor.html/content/site/&lt;sitename>.html.

   >[!NOTE]
   >
   >Gehen Sie nicht zur lokalisierten Site.

1. Navigieren Sie zu **[!UICONTROL Seiteneigenschaften]**.

   ![page-properties-1](assets/page-properties-1.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL Erweitert]**.
1. Aktivieren **[!UICONTROL Authentifizierungspflicht]**.

   ![site-authentication-1](assets/site-authentication-1.png)

1. Fügen Sie den Pfad der Anmeldeseite hinzu. Beispiel: `/content/......./GetStarted`.
1. Veröffentlichen Sie die Seite.

## Teilnehmer/innen {#enrolled-member}

Dieses Erlebnis hängt von Benutzern ab. `Riley Taylor` und `Sidney Croft` be [created](enablement-setup.md#publishcreateenablementmembers) und [assigned](resource.md#settings) der *Skiunterricht* Lernpfad durch ihre Mitgliedschaft in *Community-Ski-Klasse* hinzugefügt.

Anmelden mit

* `Username: riley`
* `Password: password`

Wenn das Benutzerprofil nicht durch Selbstregistrierung erstellt wurde und sich ein Mitglied zum ersten Mal anmeldet, wird seine Profilseite angezeigt, sodass es nach Bedarf überprüft und geändert werden kann.

Wenn sich das Mitglied das nächste Mal anmeldet, wird die durch das erste Menüelement identifizierte Startseite angezeigt.

![chlimage_1-434](assets/chlimage_1-434.png)

### Zuweisungen {#assignments}

Auf der Seite &quot;Zuweisungen&quot;werden dem Mitglied alle Lernpfade und Aktivierungsressourcen angezeigt, die ihm spezifisch zugewiesen sind.

Jede Zuweisung bietet grundlegende Informationen zu

* Der Zuweisungstyp
* Ob es sich um eine neue Zuweisung handelt
* Der Name
* Für die Art der Zuweisung relevante Angaben
* Ansprechpartner, Experte und Autor für die Zuweisung (falls vorhanden)

Der Zuweisungstyp wird durch ein Symbol oben links auf der Karte angezeigt. Das Bild einer Straße ist für einen Lernpfad mit der Anzahl der enthaltenen Aktivierungsressourcen.

![chlimage_1-435](assets/chlimage_1-435.png)

Auswählen *Skiunterricht* zeigt die beiden Aktivierungsressourcen an, auf die der Lernpfad verweist.

![chlimage_1-436](assets/chlimage_1-436.png)

Auswählen *Skiunterricht 1* öffnet die Detailseite der Aktivierungsressource.

Auf der Detailseite kann das Mitglied lernen, [rate](rating.md) Lektion erstellen und hinzufügen [Kommentare](comments.md). Jede Mitgliederaktivität wird im Abschnitt Neue Funktionen der Site angezeigt.

Interaktionen mit der Aktivierungsressource werden im Abschnitt Bericht beschrieben, auf den in der Autorenumgebung zugegriffen werden kann.

![chlimage_1-437](assets/chlimage_1-437.png)

### Ski-Katalog {#ski-catalog}

Die Seite Ski-Katalog ist der Katalog der Aktivierungsressourcen, die mit Tags aus dem `Tutorial` Namespace. Die beiden *Skiunterricht* -Ressourcen mit dem Tag `Skiing` -Tag, sodass, wenn andere Tags als `All` oder `Tutorial: Sports / Skiing` ausgewählt ist, wird nichts angezeigt.

Wenn einem Mitglied weder direkt noch über einen Lernpfad Aktivierungsressourcen zugewiesen wurden, ist es möglich, mit Aktivierungsressourcen in einem Katalog zu interagieren und Feedback über Kommentare und Bewertungen zu geben.

![chlimage_1-438](assets/chlimage_1-438.png)

### Diskussionen {#discussions}

Zusätzlich zur Bewertung und Kommentierung von Aktivierungsressourcen ([wenn aktiviert](enablement-create-site.md#step33asettings)), die Community-Site-Vorlage, von der aus `Enablement Tutorial` wurde erstellt, enthält [Forumsfunktion](functions.md#forum-function) (Titel ist `Discussions)`.

Wählen Sie die `Discussions`einen Link erstellen und ein Thema posten.

Melden Sie sich ab und melden Sie sich als Sidney Croft (Sidney/Passwort) an und antworten Sie auf die Frage sowie Folgen Sie dem Thema.

Beachten Sie, dass es neben der Inline-Moderation Optionen gibt, um das Thema in sozialen Medien zu teilen oder das Thema per E-Mail zu versenden.

![chlimage_1-439](assets/chlimage_1-439.png)

### Neue Funktionen {#what-s-new}

Die `What's New` Menüelement ist der Titel, der dem [Aktivitäts-Stream-Funktion](functions.md#activity-stream-function) in der Struktur dieser Community-Site.

Wählen Sie noch als Sidney angemeldet die `What's New` -Link, um die Aktivität anzuzeigen.

![chlimage_1-440](assets/chlimage_1-440.png)

## Vertrauenswürdiger Community-Mitglied {#trusted-community-member}

Dieses Erlebnis setzt voraus ` [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)` den Rollen von [Moderator](enablement-create-site.md#moderation) und [Ressourcenkontakt](resource.md#settings).

Anmelden mit

* `Username: quinn`
* `Password: password`

Nach der Anmeldung erscheint ein neues Menüelement. `Administration`, was angezeigt wird, weil dem Mitglied die Rolle des Moderators zugewiesen wurde.

![chlimage_1-441](assets/chlimage_1-441.png)

Die Startseite wird durch das erste Menüelement Zuweisungen identifiziert. Quinn ist der Ansprechpartner für Moderator und Aktivierungsressource und wurde nicht in Aktivierungsressourcen oder Lernpfaden eingeschrieben, sodass nichts angezeigt werden kann.

### Administration {#administration}

Aktivitäten der beiden Lernenden; `Riley Taylor` und `Sidney Croft. By s`die `Administration`-Link, um auf die Moderationskonsole zuzugreifen, kann Quinn die [Massenmoderationskonsole](moderation.md) , um ihre Beiträge zu moderieren.

Wenn Sie das Symbol für das seitliche Bedienfeld auswählen, werden die Filter geöffnet, die für die Suche nach Community-Inhalten verwendet werden.

Wenn Sie den Mauszeiger über eine Kommentarkarte bewegen, werden Moderationsaktionen angezeigt.

![chlimage_1-442](assets/chlimage_1-442.png)

## Berichte zur Autoreninstanz {#reports-on-author}

Es gibt zwei Möglichkeiten, auf die Berichterstellung für Lernende und Aktivierungsressourcen zuzugreifen.

Navigieren Sie auf der Autoreninstanz zum **Communities [Ressourcenkonsole](resources.md)**, wo die Aktivierungsressourcen verwaltet werden, und nach Auswahl einer Community-Site können Berichte für

* Alle Aktivierungsressourcen und Lernpfade
* Eine spezifische Aktivierungsressource oder ein Lernpfad

Navigieren Sie zum **Communities [Berichtkonsole](reports.md)** und erstellen Sie Berichte gemäß

* Zuweisung zu Aktivierungsressourcen und Lernpfaden
* Beiträge auf einer Community-Site über einen bestimmten Zeitraum
* Ansichten (Site-Besuche) einer Community-Site über einen bestimmten Zeitraum

* Beiträge und Ansichten können sich auf alle Inhalte oder auf bestimmte Inhalte beziehen:

   * Forum
   * Forumthema
   * Frage und Antwort
   * Frage
   * Blog
   * Blog-Artikel
   * Kalender
   * Kalenderereignis

### Ressourcenkonsole {#resources-console}

Mit ein wenig Aktivität und Interaktion mit den Ressourcen auf der Veröffentlichungsinstanz lohnt es sich, die Berichte auf der Autoreninstanz anzuzeigen.

* Beim Autor
* Anmelden mit Administratorrechten
* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Communities > Ressourcen]**
* Wählen Sie die `Enablement Tutorial` site
* Wählen Sie die `Report`Symbol für eine Zusammenfassung aller Ressourcen
* Wählen Sie eine Ressource aus und dann die `Report`Symbol für einen Bericht zu dieser Ressource

Beachten Sie, dass es wahrscheinlich zu früh ist, Daten aus Adobe Analytics anzuzeigen, die zwischen 1 und 12 Stunden dauern können. Die grundlegende SCORM-Berichterstellung ist jedoch bereits verfügbar.

#### Bericht über die Ressourcen für Ski-Lektionen {#ski-lessons-resource-report}

![chlimage_1-443](assets/chlimage_1-443.png)

#### Bericht &quot;Skilehrer/innen&quot; {#ski-lessons-user-report}

* Auswählen **[!UICONTROL Communities > Ressourcen]**

* Karte öffnen `Enablement Tutorial`
* Karte öffnen `Ski Lessons`
* `select Report, User Report`

![chlimage_1-444](assets/chlimage_1-444.png)

### Berichte-Konsole {#reports-console}

Die Berichte-Konsole ermöglicht die Erstellung von Berichten für

* **Zuweisungen** für jede Aktivierungs-Community-Site
* **Ansichten** für jede Community-Site
* **Beiträge** für jede Community-Site

Für Zuweisungsberichte:

* Beim Autor
* Anmelden mit Administratorrechten
* Navigieren Sie zu **[!UICONTROL Communities > Berichte > Zuweisungsbericht]**
* Wählen Sie eine **[!UICONTROL Site]** aus dem Pulldown-Menü (wählen Sie `Enablement Tutorial`)

* Auswählen **[!UICONTROL Gruppe]** (auswählen `Community Ski Class`)

* Wählen Sie eine **[!UICONTROL Zuweisung]** (auswählen `Ski Lessons`)

* Auswählen **[!UICONTROL Erzeugen]**

![chlimage_1-445](assets/chlimage_1-445.png)

Für Berichte zu Ansichten:

* Beim Autor
* Anmelden mit Administratorrechten
* Navigieren Sie zu **[!UICONTROL Communities > Berichte > Bericht &quot;Ansichten&quot;]**
* Wählen Sie eine **[!UICONTROL Site]** aus dem Pulldown-Menü (wählen Sie `Enablement Tutorial`)

* Auswählen **[!UICONTROL Content-Typ]** (auswählen `all`)

* Wählen Sie eine **[!UICONTROL Datumsbereich]** (auswählen `Last 7 days`)

* Auswählen **[!UICONTROL Erzeugen]**

![chlimage_1-446](assets/chlimage_1-446.png)

**[⇐ Erstellen und Zuweisen von Aktivierungsressourcen](resource.md)**
