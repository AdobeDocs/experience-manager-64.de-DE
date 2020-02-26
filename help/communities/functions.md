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

---


# Community-Funktionen {#community-functions}

Die Art der Funktionen, die von einer Community-Erfahrung erwartet werden, sind bekannt. Community-Funktionen sind als Community-Funktionen verfügbar. Sie sind im Wesentlichen eine oder mehrere Seiten, die vorab verkabelt sind, um eine Community-Funktion zu implementieren, die mehr erfordert, als einfach eine Komponente zu einer Seite im Autorenmodus hinzuzufügen. Sie sind die Bausteine, mit denen die Struktur einer [Community-Site-Vorlage](sites.md) definiert wird, aus der Community-Sites [erstellt](sites-console.md)werden.

Nachdem eine Community-Site erstellt wurde, können den resultierenden Seiten Inhalte im Standard- [AEM-Authoring-Modus](../../help/sites-authoring/editing-content.md)hinzugefügt werden.

Eine Reihe von Community-Funktionen sind sofort verfügbar, wie in der Community-Funktionkonsole zu sehen ist. Weitere Community-Funktionen werden in zukünftigen Versionen bereitgestellt und benutzerdefinierte Funktionen können ebenfalls erstellt werden.

>[!NOTE]
>
>Die Konsolen zum Erstellen von [Community-Sites](sites-console.md), [Community-Site-Vorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md) und [Community-Funktionen](functions.md) sind nur für die Verwendung in der Autorenumgebung vorgesehen.

## Community Functions Console {#community-functions-console}

In der Autorenumgebung zur Konsole der Community-Funktionen

* Aus globaler Navigation: **[!UICONTROL Werkzeuge > Communities > Community-Funktionen]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Vordefinierte Funktionen {#pre-built-functions}

Im Folgenden finden Sie eine kurze Beschreibung der Funktionen, die mit AEM Communities bereitgestellt werden. Jede Funktion besteht aus einer oder mehreren AEM-Seiten, die Communities-Komponenten enthalten, die zu einer Funktion verdrahtet sind, die problemlos in eine [Community-Site-Vorlage](sites.md)integriert werden kann.

Eine Community-Site-Vorlage bietet die Struktur einer Community-Site, einschließlich Anmeldung, Benutzerprofile, Benachrichtigungen, Nachrichten, Site-Menü, Suche, Themen und Branding-Funktionen.

### Titel- und URL-Einstellungen {#title-and-url-settings}

**Titel** und **URL** sind Eigenschaften, die allen Community-Funktionen gemein sind.

Wenn eine Community-Funktion zu einer Community-Site-Vorlage hinzugefügt oder hinzugefügt wird, wenn die Struktur einer Community-Site [geändert](sites-console.md#modifying-site-properties) wird, wird der Dialog der Funktion geöffnet, damit Titel und URL konfiguriert werden können.

#### Konfiguration der Funktionsdetails {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Titel]**(*erforderlich*) Der Text, der im Menü der Funktionen für die Site angezeigt wird

* **[!UICONTROL URL]**(*erforderlich*) Der Name, mit dem der URI generiert wird. Der Name muss den [Benennungskonventionen](../../help/sites-developing/naming-conventions.md) von AEM und JCR entsprechen.

Verwenden Sie zum Beispiel die Site, die nach dem Tutorial [Erste](getting-started.md) Schritte erstellt wurde, wenn

* Titel = Webseite
* URL = Seite

Dann lautet die URL zur Seite http://local_host:4503/content/sites/engage/en/page.html und der Menülink für die Seite wie folgt:

![chlimage_1-381](assets/chlimage_1-381.png)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Die Aktivitätsstream-Funktion ist eine Seite mit einer [Activity Streams-Komponente](activities.md) mit allen ausgewählten Ansichten (alle Aktivitäten, Benutzeraktivitäten und Follower). Siehe auch [Activity Stream Essentials](essentials-activities.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Ansicht]**&quot;Meine Aktivitäten&quot;anzeigen Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der Aktivitäten basierend auf den Aktivitäten gefiltert werden, die innerhalb der Community vom aktuellen Mitglied generiert wurden. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Ansicht]**&quot;Alle Aktivitäten&quot;anzeigen Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, die alle Aktivitäten enthält, die innerhalb der Community generiert wurden, auf die das aktuelle Mitglied Zugriff hat. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Ansicht]**&quot;News Feed&quot;anzeigen Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der Aktivitäten nach denen gefiltert werden, denen das aktuelle Mitglied folgt. Diese Option ist standardmäßig aktiviert.

### Zuweisungsfunktion {#assignments-function}

Die Zuweisungsfunktion ist die grundlegende Funktion, die eine [Community-Site für die Aktivierung](overview.md#enablement-community)definiert. Es ermöglicht die Zuweisung von Ressourcen zur Aktivierung an Community-Mitglieder. Siehe auch Grundlegende [Aufgaben](essentials-assignments.md) für Entwickler.

Diese Funktion ist als Funktion des [Aktivieren-Add-ons](enablement.md)verfügbar. Für das Aktivieren-Add-on sind zusätzliche Lizenzen für die Verwendung in einer Produktionsumgebung erforderlich.

Wenn eine Vorlage hinzugefügt wird, wird nur die [Titel- und URL-Einstellungen](#title-and-url-settings)konfiguriert.

### Blogfunktion {#blog-function}

Die Blog-Funktion ist eine Seite mit einer [Blog-Komponente](blog-feature.md) , die für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist. Siehe auch [Blog Essentials](blog-developer-basics.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-383](assets/chlimage_1-383.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Privilegierte Mitglieder]** zulassen Wenn aktiviert, erlaubt der Blog nur privilegierten Mitgliedern, Artikel zu erstellen, indem die Auswahl einer Gruppe [privilegierter Mitglieder](users.md#privileged-members-group)erlaubt wird. Wenn diese Option nicht aktiviert ist, können alle Community-Mitglieder erstellen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads]** zulassenWenn diese Option aktiviert ist, können Mitglieder im Blog Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded Replies (Threaded Replies) zulassen]** Wenn diese Option nicht aktiviert ist, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, Antworten auf Kommentare sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte Inhalte]** zulassen Wenn diese Option aktiviert ist, kann die Idee als [speziellen Inhalt](featured.md)identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Kalenderfunktion {#calendar-function}

Die Kalenderfunktion ist eine Seite mit einer [Kalenderkomponente](calendar.md) , die für das Tagging konfiguriert wurde. Siehe auch [Calendar Essentials](calendar-basics-for-developers.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-384](assets/chlimage_1-384.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Pinning]** zulassen Wenn aktiviert, ermöglicht das Forum, dass Themenantworten an den Anfang der Liste der Kommentare gebunden werden. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Privilegierte Mitglieder]** zulassen Wenn aktiviert, erlaubt der Blog nur privilegierten Mitgliedern, Artikel zu erstellen, indem die Auswahl einer Gruppe [privilegierter Mitglieder](users.md#privileged-members-group)erlaubt wird. Wenn diese Option nicht aktiviert ist, können alle Community-Mitglieder erstellen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads]** zulassenWenn diese Option aktiviert ist, können Mitglieder im Blog Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded Replies (Threaded Replies) zulassen]** Wenn diese Option nicht aktiviert ist, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, Antworten auf Kommentare sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte Inhalte]** zulassen Wenn diese Option aktiviert ist, kann die Idee als [speziellen Inhalt](featured.md)identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Katalogfunktion {#catalog-function}

Die Katalogfunktion ermöglicht es [Mitgliedern der Community](overview.md#enablement-community) , die Aktivierungsressourcen zu durchsuchen, die ihnen nicht zugewiesen sind. Siehe [Tagging-Aktivierungsressourcen](tag-resources.md) und [KatalogEssentials](catalog-developer-essentials.md) für Entwickler.

Alle Aktivierungsressourcen und Lernpfade für die Community-Site werden in allen Katalogen angezeigt, wenn deren Eigenschaft auf &quot;true&quot;gesetzt ` [Show in Catalog](resources.md)`ist. Um explizit Ressourcen und Lernpfade einzubeziehen, müssen Sie einen [Vorfilter](catalog-developer-essentials.md#pre-filters) auf den Katalog anwenden.

Wenn sie einer Vorlage hinzugefügt wird, ermöglicht die Konfiguration die Angabe von Tag-Namespace(en), mit denen der Tag-Filter konfiguriert wird, der den Besuchern der Site angezeigt wird:

![katalogfunc](assets/catalogfunc.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Alle Namespaces auswählen]**

   * Die ausgewählten Tag-Namespaces definieren, welche Tags von Besuchern zum Filtern der Liste der im Katalog aufgelisteten Aktivierungsressourcen ausgewählt werden können.
   * Wenn diese Option aktiviert ist, sind alle für die Community-Site zulässigen Tag-Namespaces verfügbar.
   * Wenn diese Option deaktiviert ist, können Sie einen oder mehrere Namespaces auswählen, die für die Community-Site zulässig sind.
   * Diese Option ist standardmäßig aktiviert.

### Funktion für spezielle Inhalte {#featured-content-function}

Die Funktion für speziellen Inhalt ist eine Seite mit einer Komponente[ für ](featured.md)speziellen Inhalt, die so konfiguriert ist, dass Kommentare hinzugefügt und gelöscht werden können.

Die Funktion zum Feature von Inhalten kann pro Komponente zugelassen oder deaktiviert werden (siehe [Blog-Funktion](#blog-function), [Kalenderfunktion](#calendar-function), [Forumsfunktion](#forum-function), [Ideenfunktion](#ideation-function)und [QnA-Funktion](#qna-function)).

Wenn eine Vorlage hinzugefügt wird, wird nur die [Titel- und URL-Einstellungen](#title-and-url-settings)konfiguriert.

### Dateibibliotheksfunktion {#file-library-function}

Die Dateibibliotheksfunktion ist eine Seite mit einer [Dateibibliothekskomponente](file-library.md) , mit der Kommentare hinzugefügt und gelöscht werden können.

Wenn eine Vorlage hinzugefügt wird, wird nur die [Titel- und URL-Einstellungen](#title-and-url-settings)konfiguriert.

### Forumsfunktion {#forum-function}

Die Forumsfunktion ist eine Seite mit einer [Forumkomponente](forum.md) , die für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Pinning]** zulassen Wenn aktiviert, ermöglicht das Forum, dass Themenantworten an den Anfang der Liste der Kommentare gebunden werden. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Privilegierte Mitglieder]** zulassen Wenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer [privilegierten Mitgliedergruppe](users.md#privileged-members-group)erlaubt. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads]** zulassen Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded Replies]** zulassen Wenn nicht aktiviert, erlaubt das Forum Kommentare zu einem Thema, Antworten auf diese Kommentare sind nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte Inhalte]** zulassen Wenn diese Option aktiviert ist, kann die Idee als [speziellen Inhalt](featured.md)identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Gruppenfunktion {#groups-function}

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;darf *nicht* die *erste oder einzige* Funktion in der Struktur einer Site oder in einer Community-Site-Vorlage sein.
>
>Jede andere Funktion, wie die [Seitenfunktion](#page-function), muss eingeschlossen und zuerst aufgeführt werden.

Die Funktion &quot;Gruppen&quot;bietet Community-Mitgliedern die Möglichkeit, Untergruppen auf der Community-Site in der Veröffentlichungsumgebung zu erstellen.

Je nach [Einstellungen](sites-console.md#groupmanagement) , wenn die Funktion &quot;Gruppen&quot;in einer [Community-Site-Vorlage](sites.md)enthalten ist, können die Gruppen öffentlich oder privat sein, und eine oder mehrere Community-Gruppenvorlagen können so konfiguriert werden, dass eine Auswahl von Vorlagen bereitgestellt wird, wenn die Community-Gruppe erstellt wird (z. B. aus der Veröffentlichungsumgebung). Eine [Community-Gruppenvorlage](tools-groups.md) gibt an, welche Communities-Funktionen für die Gruppenseiten erstellt werden, z. B. Foren und Kalender.

Wenn eine Community-Gruppe erstellt wird, wird eine Mitgliedsgruppe dynamisch für die neue Gruppe erstellt, der Mitglieder zugewiesen oder hinzugefügt werden können. For more information, see [Managing Users and User Groups](users.md).

Ab Communities [Feature Pack 1](deploy-communities.md#latestfeaturepack)werden Community-Gruppen in der Autorenumgebung mithilfe der Gruppenkonsole[für ](groups.md)Communities erstellt und können in der Veröffentlichungsumgebung erstellt werden, wenn sie aktiviert sind.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-386](assets/chlimage_1-386.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Wählen Sie Gruppenvorlagen]** Ein Pulldown-Menü, das die Auswahl einer oder mehrerer aktivierter Gruppenvorlagen ermöglicht, aus denen der künftige Ersteller einer neuen Community-Gruppe (in der Veröffentlichungsumgebung) wählen kann.

* **[!UICONTROL Privilegierte Mitglieder]** zulassen Wenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer [privilegierten Sicherheitsgruppe](users.md#privileged-members-group)erlaubt. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Erstellen]** von Veröffentlichungen zulassen Wenn diese Option aktiviert ist, können autorisierte Community-Mitglieder eine Gruppe in der Veröffentlichungsumgebung erstellen. Wenn diese Option deaktiviert ist, können neue Gruppen (Untergruppen) nur in der Autorenumgebung aus der Gruppenkonsole der Communities Sites erstellt werden.

   Der Standardwert ist `checked`.

### Ideen-Funktion {#ideation-function}

Die Ideationsfunktion ist eine Seite mit einer [Ideationskomponente](ideation-feature.md).

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem die standardmäßigen Titel- und URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt werden:

![chlimage_1-387](assets/chlimage_1-387.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Privilegierte Mitglieder]** zulassen Wenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer [privilegierten Sicherheitsgruppe](users.md#privileged-members-group)erlaubt. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads]** zulassen Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded Replies (Threaded Replies) zulassen]** Wenn diese Option nicht aktiviert ist, sind Antworten (Kommentare) auf ein Thema zulässig, Antworten auf Kommentare sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte Inhalte]** zulassen Wenn diese Option aktiviert ist, kann die Idee als [speziellen Inhalt](featured.md)identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Leaderboard-Funktion {#leaderboard-function}

Die Lederboard-Funktion ist eine Seite mit einer [Leaderboard-Komponente](enabling-leaderboard.md).

**HINWEIS**: Die Komponente Leaderboard muss weiter konfiguriert werden, *nachdem* eine Community-Site aus einer Community-Vorlage erstellt wurde, die die Funktion Leaderboard enthält. Die [Regeln](enabling-leaderboard.md#rules-tab) der Komponente &quot;Leaderboard&quot;müssen angegeben werden, die von der Konfiguration der [Bewertung und Abzeichen](implementing-scoring.md) der Community-Site abhängen.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem die standardmäßigen Titel- und URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt werden:

![chlimage_1-388](assets/chlimage_1-388.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Anzeigemarke]** Wenn aktiviert, wird eine Spalte für Symbole mit Zeichen in der Leiste angezeigt.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Name der Markierung]** anzeigen Wenn aktiviert, wird eine Spalte für den Namen der Markierung in der Lederboard eingefügt.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Avatar]** anzeigen Wenn aktiviert, wird das Avatarbild des Mitglieds neben dem Namen des Mitglieds mit dem Mitgliederprofil verknüpft.

   Diese Option ist standardmäßig deaktiviert.

### Seitenfunktion {#page-function}

Die Seitenfunktion fügt der Community-Site eine leere Seite hinzu, auf der sie in die Funktionen der Community-Site verdrahtet wird: Login, Menü, Benachrichtigungen, Messaging, Design und Branding. Inhalte können der Seite im [Standard-AEM-Authoring-Modus](../../help/sites-authoring/editing-content.md)hinzugefügt werden.

Wenn eine Vorlage hinzugefügt wird, wird nur die [Titel- und URL-Einstellungen](#title-and-url-settings)konfiguriert.

### Fragen/Antworten-Funktion {#qna-function}

Die QnA-Funktion ist eine Seite mit einer [QnA-Komponente](working-with-qna.md) , die für Tagging, Dateiuploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist.

Wenn eine Vorlage hinzugefügt wird, erlaubt die Konfiguration die Beschränkung auf privilegierte Mitglieder:

![chlimage_1-389](assets/chlimage_1-389.png)

* Siehe [Titel- und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Pinning]** zulassen Wenn aktiviert, ermöglicht das Forum, dass Themenantworten an den Anfang der Liste der Kommentare gebunden werden. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Privilegierte Mitglieder]** zulassen Wenn diese Option aktiviert ist, erlaubt das QnA-Forum nur privilegierten Mitgliedern, Fragen zu stellen, indem es die Auswahl einer [privilegierten Mitgliedergruppe](users.md#privileged-members-group)erlaubt. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Dateiuploads]** zulassen Wenn diese Option aktiviert ist, können Mitglieder im QnA-Forum Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded Replies]** zulassen Wenn nicht aktiviert, ermöglicht das QnA-Forum Kommentare (Antworten) zu einer geposteten Frage, Antworten auf Antworten sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Vorgestellte Inhalte]** zulassen Wenn diese Option aktiviert ist, kann die Idee als [speziellen Inhalt](featured.md)identifiziert werden. Diese Option ist standardmäßig aktiviert.

## Community-Funktion erstellen {#create-community-function}

Die Möglichkeit, eine Community-Funktion zu erstellen, wird durch Auswahl des `Create Community Function` Symbols oben in der Community Functions-Konsole erreicht. Mehrere Funktionen, die auf demselben AEM-Blueprint basieren, können erstellt und dann durch Öffnen im Autorenbearbeitungsmodus eindeutig angepasst werden.

![chlimage_1-390](assets/chlimage_1-390.png)

### Name der Community-Funktion {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

Im Bereich &quot;Community-Funktionsname&quot;werden ein Name und eine Beschreibung sowie die Konfiguration der Funktion aktiviert oder deaktiviert:

* **[!UICONTROL Community-Funktionsname]** Der für die Anzeige und Speicherung verwendete Funktionsname

* **[!UICONTROL Beschreibung]** der Community-Funktion Die Funktionsbeschreibung für die Anzeige

* **[!UICONTROL Deaktiviert/Deaktiviert]** Ein Umschalter, der steuert, ob die Funktion referenzierbar ist

### AEM-Blueprint {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

Auf dem `AEM Blueprint` Bedienfeld können Sie den Entwurf auswählen, der die zugrunde liegende Implementierung der Community-Funktion ist.

Die Community-Funktion ist eine Mini-Site, die aus einer oder mehreren Seiten besteht und zur Einbindung in eine Community-Site vorkonfiguriert ist, einschließlich Anmeldung, Benutzerprofile, Benachrichtigungen, Nachrichten, Site-Menü, Suche, Themen und Branding-Funktionen. Nachdem die Funktion erstellt wurde, ist es möglich, die Funktion[ im Autorenbearbeitungsmodus zu ](#open-community-function)öffnen und die Seiten- und/oder Komponenteneinstellungen anzupassen.

Da die Community-Funktion als [Live-Kopie](../../help/sites-administering/msm.md#live-copies) eines [Blueprints](../../help/sites-administering/msm-livecopy.md#creatingablueprint)implementiert wird, ist es möglich, Änderungen an einer Funktion zu implementieren, die alle Community-Site-Seiten betreffen, die aus der [Community-Site-Vorlage](sites.md) oder [Community-Gruppenvorlage](tools-groups.md) , die die Funktion enthält, erstellt wurden. Es ist auch möglich, die Verknüpfung einer Seite mit dem übergeordneten Entwurf zu trennen, um Änderungen auf Seitenebene vorzunehmen.

Siehe auch [Multi-Site-Manager](../../help/sites-administering/msm.md).

### Miniatur {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

Im Bereich &quot;Miniaturansicht&quot;kann ein Bild hochgeladen werden, um es in der Konsole &quot; [Community-Funktionen&quot;anzuzeigen](#community-functions-console).

## Community-Funktion öffnen {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Wählen Sie das `Open Community Function` Symbol aus, um zum Authoring des Seiteninhalts und zum Ändern der Konfiguration der Funktionskomponente(n) in den Bearbeitungsmodus zu wechseln.

### Konfigurieren von Komponenten {#configuring-components}

Eine Community-Funktion wird als Live Copy eines AEM-Blueprints implementiert, dessen Details unter [Multi-Site-Manager](../../help/sites-administering/msm.md)dokumentiert sind.

Es ist möglich, nicht nur Seiteninhalte zu erstellen, sondern Komponenten zu konfigurieren.

Wenn Sie eine Komponente auf einer Seite einer erstellten Community-Site konfigurieren, ist es ggf. erforderlich, die [Vererbung](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) abzubrechen, um die Komponente zu konfigurieren. Die Vererbung sollte nach Abschluss der Konfiguration wiederhergestellt werden.

Konfigurationsdetails finden Sie unter [Communities-Komponenten](author-communities.md) für Autoren.

## Community-Funktion bearbeiten {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Wählen Sie das `Edit Community Function` Symbol aus, um die Eigenschaften der Funktion in denselben Bedienfeldern zu bearbeiten wie beim [Erstellen einer Community-Funktion](#create-community-function), einschließlich Aktivieren oder Deaktivieren der Funktion.
