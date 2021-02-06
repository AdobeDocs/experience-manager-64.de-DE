---
title: Community-Funktionen
seo-title: Community-Funktionen
description: Erfahren Sie, wie Sie auf die Community Functions-Konsole zugreifen.
seo-description: Erfahren Sie, wie Sie auf die Community Functions-Konsole zugreifen.
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '2542'
ht-degree: 6%

---


# Community-Funktionen {#community-functions}

Die Art der Funktionen, die von einer Community-Erfahrung erwartet werden, sind bekannt. Community-Funktionen sind als Community-Funktionen verfügbar. Sie sind im Wesentlichen eine oder mehrere Seiten, die vorab verkabelt sind, um eine Community-Funktion zu implementieren, die mehr erfordert, als einfach eine Komponente zu einer Seite im Autorenmodus hinzuzufügen. Sie sind die Bausteine, mit denen die Struktur einer [Community-Site-Vorlage](sites.md) definiert wird, aus der Community-Sites [erstellt werden.](sites-console.md)

Nachdem eine Community-Site erstellt wurde, können den resultierenden Seiten Inhalte mit dem Standard [AEM Authoring-Modus](../../help/sites-authoring/editing-content.md) hinzugefügt werden.

Eine Reihe von Community-Funktionen sind sofort verfügbar, wie in der Community-Funktionkonsole zu sehen ist. In zukünftigen Versionen werden weitere Community-Funktionen bereitgestellt und es können auch benutzerdefinierte Funktionen erstellt werden.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](sites-console.md), [Community-Sitevorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md) und [Community-Funktionen](functions.md) sind nur für die Verwendung in der Autor-Umgebung vorgesehen.

## Community Functions Console {#community-functions-console}

In der Umgebung &quot;Autor&quot;zur Konsole der Community-Funktionen

* Aus globaler Navigation: **[!UICONTROL Tools > Communities > Community Functions]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Vorgefertigte Funktionen {#pre-built-functions}

Im Folgenden werden die mit AEM Communities gelieferten Funktionen kurz beschrieben. Jede Funktion besteht aus einer oder mehreren AEM Seiten, die Communities-Komponenten enthalten, die zu einer Funktion verdrahtet sind, die leicht in eine [Community-Site-Vorlage](sites.md) integriert werden kann.

Eine Community-Site-Vorlage bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Profile, Benachrichtigungen, Nachrichten, Site-Menü, Suche, Themen und Branding-Funktionen.

### Titel- und URL-Einstellungen {#title-and-url-settings}

**Titel** und  **** URLs sind Eigenschaften, die allen Community-Funktionen gemein sind.

Wenn eine Community-Funktion zu einer Community-Site-Vorlage hinzugefügt oder hinzugefügt wird, wenn [die Struktur einer Community-Site geändert wird, wird der Dialog der Funktion geöffnet, damit Titel und URL konfiguriert werden können.](sites-console.md#modifying-site-properties)

#### Konfiguration der Funktionsdetails {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Titel]**
(
*Erforderlich*) Der Text, der im Menü der Funktionen für die Site angezeigt wird

* **[!UICONTROL URL]**
 (*erforderlich*) Der Name, mit dem der URI generiert wird. Der Name muss den von AEM und JCR festgelegten Benennungskonventionen](../../help/sites-developing/naming-conventions.md) entsprechen.[

Verwenden Sie zum Beispiel die Site, die nach dem Tutorial [Erste Schritte](getting-started.md) erstellt wurde, wenn

* Titel = Webseite
* URL = Seite

Dann lautet die URL zur Seite http://local_host:4503/content/sites/engage/en/page.html und der Menülink für die Seite wie folgt:

![chlimage_1-381](assets/chlimage_1-381.png)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Die Stream-Funktion der Aktivität ist eine Seite mit der Aktivität [Aktivität Streams component](activities.md), auf der alle Ansichten ausgewählt sind (alle Aktivitäten, Benutzergruppen und folgende). Siehe auch [Aktivität Stream Essentials](essentials-activities.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Ansicht &quot;Meine Aktivitäten&quot;]**
anzeigenWenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der die Aktivitäten der Filter basieren, die auf den vom aktuellen Mitglied innerhalb der Community generierten  basieren. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Ansicht &quot;Alle Aktivitäten anzeigen&quot;]**
Wenn aktiviert, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, die alle Aktivitäten enthält, die innerhalb der Community generiert wurden, auf die das aktuelle Mitglied Zugriff hat. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Ansicht &quot;News-Feed anzeigen&quot;]**
Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der die Aktivitäten der Filter basieren, denen das aktuelle Mitglied folgt. Diese Option ist standardmäßig aktiviert.

### Zuweisungsfunktion {#assignments-function}

Die Zuweisungsfunktion ist die grundlegende Funktion, die eine [Community-Site für die Aktivierung](overview.md#enablement-community) definiert. Es ermöglicht die Zuweisung von Ressourcen zur Aktivierung an Community-Mitglieder. Siehe auch [Zuweisungsgrundlagen](essentials-assignments.md) für Entwickler.

Diese Funktion ist als Funktion des [Aktivieren-Add-ons](enablement.md) verfügbar. Für das Aktivieren-Add-on sind zusätzliche Lizenzen für die Verwendung in einer Produktions-Umgebung erforderlich.

Wenn eine Vorlage hinzugefügt wird, ist die einzige Konfiguration für die Einstellungen [Titel und URL](#title-and-url-settings).

### Blogfunktion {#blog-function}

Die Blog-Funktion ist eine Seite mit einer [Blog-Komponente](blog-feature.md), die für Tagging, Datei-Uploads konfiguriert ist, der folgenden folgt, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation. Siehe auch [Blog Essentials](blog-developer-basics.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-383](assets/chlimage_1-383.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Privilegierte]**
Mitglieder zulassenWenn diese Option aktiviert ist, erlaubt der Blog nur privilegierten Mitgliedern, Artikel zu erstellen, indem die Auswahl einer Gruppe von  [privilegierten Mitgliedern](users.md#privileged-members-group) erlaubt wird. Wenn diese Option nicht aktiviert ist, können alle Community-Mitglieder erstellen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassenWenn diese Option aktiviert ist, können Mitglieder im Blog Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Replies zulassen Wenn nicht markiert, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, Antworten auf Kommentare sind nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte]**
Inhalte zulassenWenn diese Option aktiviert ist, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Kalenderfunktion {#calendar-function}

Die Kalenderfunktion ist eine Seite mit einer [Kalenderkomponente](calendar.md), die für das Tagging konfiguriert ist. Siehe auch [Kalendergrundlagen](calendar-basics-for-developers.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-384](assets/chlimage_1-384.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Erlauben Sie]**
PinningWenn aktiviert, ermöglicht das Forum, Themenantworten an den Anfang der Liste der Kommentare zu veröffentlichen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Privilegierte]**
Mitglieder zulassenWenn diese Option aktiviert ist, erlaubt der Blog nur privilegierten Mitgliedern, Artikel zu erstellen, indem die Auswahl einer Gruppe von  [privilegierten Mitgliedern](users.md#privileged-members-group) erlaubt wird. Wenn diese Option nicht aktiviert ist, können alle Community-Mitglieder erstellen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassenWenn diese Option aktiviert ist, können Mitglieder im Blog Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Replies zulassen Wenn nicht markiert, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, Antworten auf Kommentare sind nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte]**
Inhalte zulassenWenn diese Option aktiviert ist, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Katalogfunktion {#catalog-function}

Die Katalogfunktion bietet Mitgliedern der [Aktivieren-Community](overview.md#enablement-community) die Möglichkeit, Aktivierungsressourcen zu durchsuchen, die ihnen nicht zugewiesen sind. Siehe [Tagging-Aktivierungsressourcen](tag-resources.md) und [Kataloggrundsätze](catalog-developer-essentials.md) für Entwickler.

Alle Aktivierungsressourcen und Lernpfade für die Community-Site werden in allen Katalogen angezeigt, wenn ihre Eigenschaft ` [Show in Catalog](resources.md)` auf true gesetzt ist. Um explizit Ressourcen und Lernpfade einzubeziehen, müssen Sie einen [Vorfilter](catalog-developer-essentials.md#pre-filters) auf den Katalog anwenden.

Wenn eine Vorlage hinzugefügt wird, ermöglicht die Konfiguration die Angabe von Tag-Namensräumen, die zum Konfigurieren des Tag-Filters verwendet werden, der den Site-Besuchern angezeigt wird:

![katalogfunc](assets/catalogfunc.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Alle Namespaces auswählen]**

   * Die ausgewählten Tag-Namensraum definieren, welche Tags von Besuchern zum Filtern der Liste der im Katalog aufgelisteten Aktivierungsressourcen ausgewählt werden können.
   * Wenn diese Option aktiviert ist, sind alle für die Community-Site zulässigen Tag-Namensraum verfügbar.
   * Wenn diese Option deaktiviert ist, können Sie einen oder mehrere Namensraum auswählen, die für die Community-Site zulässig sind.
   * Diese Option ist standardmäßig aktiviert.

### Funktion für spezielle Inhalte {#featured-content-function}

Die Funktion für speziellen Inhalt ist eine Seite mit einer [Komponente für speziellen Inhalt](featured.md), die so konfiguriert ist, dass Kommentare hinzugefügt und gelöscht werden können.

Die Funktion zum Feature von Inhalten kann pro Komponente zugelassen oder deaktiviert werden (siehe [Blog-Funktion](#blog-function), [Kalenderfunktion](#calendar-function), [Forum-Funktion](#forum-function), [Ideenfunktion](#ideation-function) und [QnA-Funktion](#qna-function)).

Wenn eine Vorlage hinzugefügt wird, ist die einzige Konfiguration für die Einstellungen [Titel und URL](#title-and-url-settings).

### Dateibibliotheksfunktion {#file-library-function}

Die Dateibibliotheksfunktion ist eine Seite mit einer [Dateibibliothekskomponente](file-library.md), auf der Kommentare hinzugefügt und gelöscht werden können.

Wenn eine Vorlage hinzugefügt wird, ist die einzige Konfiguration für die Einstellungen [Titel und URL](#title-and-url-settings).

### Forumsfunktion {#forum-function}

Die Forumfunktion ist eine Seite mit einer [Forumkomponente](forum.md), die für Tagging, Datei-Uploads konfiguriert ist, der folgenden folgt, Mitgliedern zur Selbstbearbeitung, Abstimmung und Moderation.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Erlauben Sie]**
PinningWenn aktiviert, ermöglicht das Forum, Themenantworten an den Anfang der Liste der Kommentare zu veröffentlichen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Privilegierte]**
Mitglieder zulassenWenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern das Posten von Themen, indem es die Auswahl einer  [privilegierten Mitgliedergruppe](users.md#privileged-members-group) erlaubt. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassenWenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Antworten zulassen Wenn nicht aktiviert, erlaubt das Forum Kommentare zu einem Thema, Antworten auf diese Kommentare sind nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte]**
Inhalte zulassenWenn diese Option aktiviert ist, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Gruppenfunktion {#groups-function}

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;muss *nicht* die Funktion *first noch die einzige Funktion* in der Struktur einer Site oder in einer Vorlage einer Community-Site sein.
>
>Jede andere Funktion, wie z. B. die Funktion [page](#page-function), muss eingeschlossen und zuerst aufgelistet werden.

Die Gruppenfunktion bietet Community-Mitgliedern die Möglichkeit, Untergruppen auf der Community-Site in der Umgebung zum Veröffentlichen zu erstellen.

Abhängig von [den Einstellungen](sites-console.md#groupmanagement), wenn die Funktion &quot;Groups&quot;in einer [Community-Site-Vorlage](sites.md) enthalten ist, können die Gruppen öffentlich oder privat sein und eine oder mehrere Community-Gruppenvorlagen können so konfiguriert werden, dass eine Auswahl von Vorlagen bereitgestellt wird, wenn die Community-Umgebung tatsächlich erstellt wird (z. B. aus der Veröffentlichungsgruppe). Eine [Community-Gruppenvorlage](tools-groups.md) gibt an, welche Communities-Funktionen für die Gruppenseiten erstellt werden, z. B. Foren und Kalender.

Wenn eine Community-Gruppe erstellt wird, wird eine Mitgliedsgruppe dynamisch für die neue Gruppe erstellt, der Mitglieder zugewiesen oder hinzugefügt werden können. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Ab Communities [Feature Pack 1](deploy-communities.md#latestfeaturepack) werden Community-Gruppen in der Autorengruppe mit der [Communities Sites&#39;-Konsole](groups.md) erstellt und können in der Umgebung &quot;Veröffentlichen&quot;erstellt werden, wenn sie aktiviert sind.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-386](assets/chlimage_1-386.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Wählen Sie Gruppenvorlagen]**
Ein Pulldown-Menü, das die Auswahl einer oder mehrerer aktivierter Gruppenvorlagen ermöglicht, aus denen der künftige Ersteller einer neuen Community-Umgebung (in der Veröffentlichungsgruppe) wählen kann.

* **[!UICONTROL Privilegierte]**
Mitglieder zulassenWenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer  [privilegierten Sicherheitsgruppe](users.md#privileged-members-group) erlaubt. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Veröffentlichungserstellung zulassen]**
Wenn diese Option aktiviert ist, können autorisierte Community-Mitglieder eine Gruppe in der Umgebung &quot;Veröffentlichen&quot;erstellen. Wenn diese Option nicht aktiviert ist, können neue Gruppen (Untergruppen) nur in der Autorengruppe in der Umgebung &quot;Communities Sites&quot;erstellt werden.

   Der Standardwert ist `checked`.

### Ideen-Funktion {#ideation-function}

Die Ideationsfunktion ist eine Seite mit einer [Ideationskomponente](ideation-feature.md).

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem die standardmäßigen Titel- und URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt werden:

![chlimage_1-387](assets/chlimage_1-387.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Privilegierte]**
Mitglieder zulassenWenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer  [privilegierten Sicherheitsgruppe](users.md#privileged-members-group) erlaubt. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassenWenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Replies zulassen Wenn nicht aktiviert, ist die Idee, Antworten (Kommentare) auf ein Thema zuzulassen, aber Antworten auf Kommentare sind nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte]**
Inhalte zulassenWenn diese Option aktiviert ist, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Leaderboard-Funktion {#leaderboard-function}

Die Leader-Funktion ist eine Seite mit einer [Leaderboard-Komponente](enabling-leaderboard.md).

**HINWEIS**: Die Komponente Leaderboard muss weiter konfiguriert werden,  ** nachdem eine Community-Site aus einer Community-Vorlage erstellt wurde, die die Funktion Leaderboard enthält. Die [Regeln](enabling-leaderboard.md#rules-tab) der Komponente &quot;Leaderboard&quot;müssen angegeben werden, die von der Konfiguration von [Scoring und Abzeichen](implementing-scoring.md) für die Community-Site abhängen.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem die standardmäßigen Titel- und URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt werden:

![chlimage_1-388](assets/chlimage_1-388.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Display]**
BadgeWenn aktiviert, wird eine Spalte für Symbole mit Zeichen in die Lederboard aufgenommen.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Anzeigename]**
Wenn aktiviert, wird eine Spalte für den Namen des Kennzeichens in der Zeichenfläche angezeigt.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Anzeigen von]**
AvatarWenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds neben dem Namen des Mitglieds mit dem Profil des Mitglieds verknüpft.

   Diese Option ist standardmäßig deaktiviert.

### Seitenfunktion {#page-function}

Die Seitenfunktion fügt der Community-Site eine leere Seite hinzu, auf der sie in die Funktionen der Community-Site verdrahtet wird: Login, Menü, Benachrichtigungen, Messaging, Theming und Branding. Inhalte können der Seite im [Standard-AEM-Authoring-Modus](../../help/sites-authoring/editing-content.md) hinzugefügt werden.

Wenn eine Vorlage hinzugefügt wird, ist die einzige Konfiguration für die Einstellungen [Titel und URL](#title-and-url-settings).

### Fragen/Antworten-Funktion {#qna-function}

Die QnA-Funktion ist eine Seite mit einer [QnA-Komponente](working-with-qna.md), die für Tagging, Datei-Uploads konfiguriert ist, gefolgt von Mitgliedern zur Selbstbearbeitung, Abstimmung und Moderation.

Wenn eine Vorlage hinzugefügt wird, erlaubt die Konfiguration die Beschränkung auf privilegierte Mitglieder:

![chlimage_1-389](assets/chlimage_1-389.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Erlauben Sie]**
PinningWenn aktiviert, ermöglicht das Forum, Themenantworten an den Anfang der Liste der Kommentare zu veröffentlichen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Privilegierte]**
Mitglieder zulassenWenn diese Option aktiviert ist, erlaubt das QnA-Forum nur privilegierten Mitgliedern, Fragen zu stellen, indem es die Auswahl einer  [privilegierten Mitgliedergruppe](users.md#privileged-members-group) erlaubt. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassenWenn diese Option aktiviert ist, bietet das QnA-Forum Mitgliedern die Möglichkeit, Dateien hochzuladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Replies zulassen Wenn nicht aktiviert, ermöglicht das QnA-Forum Kommentare (Antworten) zu einer geposteten Frage, Antworten auf Antworten sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte]**
Inhalte zulassenWenn diese Option aktiviert ist, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

## Community-Funktion erstellen {#create-community-function}

Die Möglichkeit, eine Community-Funktion zu erstellen, wird durch Auswahl des `Create Community Function`-Symbols oben in der Community Functions-Konsole erreicht. Mehrere Funktionen, die auf demselben AEM Blueprint basieren, können erstellt und dann durch Öffnen im Autorenbearbeitungsmodus eindeutig angepasst werden.

![chlimage_1-390](assets/chlimage_1-390.png)

### Name der Community-Funktion {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

Im Bedienfeld &quot;Community-Funktionsname&quot;werden ein Name und eine Beschreibung sowie die Konfiguration der Funktion aktiviert oder deaktiviert:

* **[!UICONTROL Community-]**
FunktionsnameDer für die Anzeige und Datenspeicherung verwendete Funktionsname

* **[!UICONTROL Beschreibung]**
der Community-FunktionDie Funktionsbeschreibung für die Anzeige

* **[!UICONTROL Deaktiviert/]**
AktiviertEin Umschalter, der steuert, ob die Funktion referenzierbar ist

### AEM-Blueprint {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

Im Bedienfeld `AEM Blueprint` können Sie den Entwurf auswählen, der die zugrunde liegende Implementierung der Community-Funktion ist.

Die Community-Funktion ist eine Mini-Site, die aus einer oder mehreren Seiten besteht und zur Einbindung in eine Community-Site vorkonfiguriert ist. Dazu gehören Anmeldung, Profil, Benachrichtigungen, Nachrichten, Site-Menü, Suche, Themen und Branding-Funktionen. Nachdem die Funktion erstellt wurde, ist es möglich, die Funktion [im Autorenbearbeitungsmodus zu öffnen und die Seiten- und/oder Komponenteneinstellungen anzupassen.](#open-community-function)

Da die Community-Funktion als [Live Copy](../../help/sites-administering/msm.md#live-copies) eines [Blueprints](../../help/sites-administering/msm-livecopy.md#creatingablueprint) implementiert ist, ist es möglich, Änderungen an einer Funktion zu implementieren, die alle Community-Site-Seiten betrifft, die aus der [Community-Site-Vorlage](sites.md) oder [Community-Gruppenvorlage](tools-groups.md) erstellt wurden, die die die Funktion enthält. Es ist auch möglich, die Verknüpfung einer Seite mit dem übergeordneten Entwurf zu trennen, um Änderungen auf Seitenebene vorzunehmen.

Siehe auch [Multi-Site-Manager](../../help/sites-administering/msm.md).

### Miniaturansicht  {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

Im Bereich &quot;Miniaturansicht&quot;kann ein Bild hochgeladen werden, um es in der Konsole [Community-Funktionen](#community-functions-console) anzuzeigen.

## Community-Funktion öffnen {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Klicken Sie auf das Symbol `Open Community Function`, um in den Bearbeitungsmodus für Autoren zum Authoring des Seiteninhalts und zum Ändern der Konfiguration der Funktionskomponente(n) zu wechseln.

### Konfigurieren von Komponenten {#configuring-components}

Eine Community-Funktion wird als Live Copy eines AEM Blueprints implementiert, dessen Details unter [Multi-Site-Manager](../../help/sites-administering/msm.md) dokumentiert sind.

Es ist möglich, nicht nur Seiteninhalte zu erstellen, sondern Komponenten zu konfigurieren.

Wenn Sie eine Komponente auf einer Seite einer erstellten Community-Site konfigurieren, ist es möglicherweise erforderlich, [Vererbung](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) abzubrechen, um die Komponente zu konfigurieren. Die Vererbung sollte nach Abschluss der Konfiguration wiederhergestellt werden.

Konfigurationsdetails finden Sie unter [Communities Components](author-communities.md) für Autoren.

## Community-Funktion bearbeiten {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Klicken Sie auf das Symbol `Edit Community Function`, um die Eigenschaften der Funktion mit denselben Bedienfeldern wie [Erstellen einer Community-Funktion](#create-community-function) zu bearbeiten, einschließlich Aktivieren oder Deaktivieren der Funktion.
