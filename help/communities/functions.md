---
title: Community-Funktionen
seo-title: Community-Funktionen
description: Erfahren Sie, wie Sie auf die Konsole "Community-Funktionen"zugreifen
seo-description: Erfahren Sie, wie Sie auf die Konsole "Community-Funktionen"zugreifen
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
role: Admin
exl-id: 2007336d-d75c-4e01-af81-181751c04cfe
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '2542'
ht-degree: 6%

---

# Community-Funktionen {#community-functions}

Die Art der Funktionen, die von einem Community-Erlebnis erwartet werden, ist bekannt. Community-Funktionen sind als Community-Funktionen verfügbar. Im Grunde sind es eine oder mehrere Seiten, die vorab mit dem Netzwerk verbunden sind, um eine Community-Funktion zu implementieren, die mehr erfordert, als einfach eine Komponente zu einer Seite im Autorenmodus hinzuzufügen. Sie sind die Bausteine, mit denen die Struktur einer [Community-Site-Vorlage](sites.md) definiert wird, von der aus Community-Sites [erstellt](sites-console.md) sind.

Nachdem eine Community-Site erstellt wurde, kann den resultierenden Seiten mithilfe des standardmäßigen [AEM Authoring-Modus](../../help/sites-authoring/editing-content.md) Inhalt hinzugefügt werden.

Eine Reihe von Community-Funktionen ist sofort verfügbar, wie in der Konsole Community-Funktionen zu sehen ist. In zukünftigen Versionen werden mehr Community-Funktionen bereitgestellt und es können auch benutzerdefinierte Funktionen erstellt werden.

>[!NOTE]
>
>Die Konsolen zum Erstellen von [Community-Sites](sites-console.md), [Community-Site-Vorlagen](sites.md), [Community-Gruppenvorlagen](tools-groups.md) und [Community-Funktionen](functions.md) sind nur zur Verwendung in der Autorenumgebung vorgesehen.

## Community-Funktionskonsole {#community-functions-console}

In der Autorenumgebung, um die Konsole für Community-Funktionen zu erreichen

* Über die globale Navigation: **[!UICONTROL Tools > Communities > Community-Funktionen]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Vordefinierte Funktionen {#pre-built-functions}

Im Folgenden finden Sie eine kurze Beschreibung der Funktionen, die mit AEM Communities bereitgestellt werden. Jede Funktion besteht aus einer oder mehreren AEM Seiten, die Communities-Komponenten enthalten und mit einer Funktion verbunden sind, die einfach in eine [Community-Site-Vorlage](sites.md) integriert werden kann.

Eine Community-Site-Vorlage bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Benutzerprofile, Benachrichtigungen, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

### Titel und URL-Einstellungen {#title-and-url-settings}

**** Titel und  **** URLs sind Eigenschaften, die allen Community-Funktionen gemein sind.

Wenn einer Community-Site-Vorlage eine Community-Funktion hinzugefügt oder [die Struktur einer Community-Site geändert wird, wird der Dialog der Funktion geöffnet, sodass Titel und URL konfiguriert werden können.](sites-console.md#modifying-site-properties)

#### Konfiguration der Funktionsdetails {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Titel]**
(
*erforderlich*) Der Text, der im Menü der Funktionen für die Site angezeigt wird

* **[!UICONTROL URL]**
 (*erforderlich*) Der Name, mit dem der URI generiert wird. Der Name muss den [Benennungskonventionen](../../help/sites-developing/naming-conventions.md) entsprechen, die von AEM und JCR festgelegt werden.

Verwenden Sie beispielsweise die aus dem Tutorial [Erste Schritte](getting-started.md) erstellte Site, falls

* Titel = Webseite
* URL = Seite

Dann lautet die URL zur Seite http://local_host:4503/content/sites/engage/en/page.html und der Menülink für die Seite wird wie folgt angezeigt:

![chlimage_1-381](assets/chlimage_1-381.png)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Die Aktivitäts-Stream-Funktion ist eine Seite mit der Komponente [Aktivitäts-Streams](activities.md) mit allen ausgewählten Ansichten (alle Aktivitäten, Benutzeraktivitäten und Folgeaktivitäten). Siehe auch [Aktivitäts-Stream-Grundlagen](essentials-activities.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Siehe [Titel und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Ansicht &quot;Meine Aktivitäten&quot;anzeigen]**
Ist diese Option aktiviert, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der Aktivitäten basierend auf denen gefiltert werden, die innerhalb der Community vom aktuellen Mitglied generiert wurden. Diese Option ist standardmäßig aktiviert.

* ****
Ansicht &quot;Alle Aktivitäten&quot;anzeigenIst diese Option aktiviert, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, die alle Aktivitäten enthält, die innerhalb der Community generiert wurden, auf die das aktuelle Mitglied Zugriff hat. Diese Option ist standardmäßig aktiviert.

* ****
Ansicht &quot;News Feed anzeigen&quot;Ist diese Option aktiviert, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der Aktivitäten nach denen gefiltert werden, denen das aktuelle Mitglied folgt. Diese Option ist standardmäßig aktiviert.

### Zuweisungsfunktion {#assignments-function}

Die Zuweisungsfunktion ist die grundlegende Funktion, die eine [Community-Site für die Aktivierung](overview.md#enablement-community) definiert. Sie ermöglicht die Zuweisung von Aktivierungsressourcen an Community-Mitglieder. Siehe auch [Zuweisungsgrundlagen](essentials-assignments.md) für Entwickler.

Diese Funktion ist als Funktion des [Aktivierungs-Add-ons](enablement.md) verfügbar. Das Aktivierungs-Add-on erfordert zusätzliche Lizenzierung für die Verwendung in einer Produktionsumgebung.

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für [Titel und URL-Einstellungen](#title-and-url-settings).

### Blogfunktion {#blog-function}

Die Blog-Funktion ist eine Seite mit einer [Blog-Komponente](blog-feature.md), die für Tagging, Datei-Uploads konfiguriert ist, gefolgt von Mitgliedern zur Selbstbearbeitung, Abstimmung und Moderation. Siehe auch [Blog Essentials](blog-developer-basics.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-383](assets/chlimage_1-383.png)

* Siehe [Titel und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Zulassen von privilegierten]**
MitgliedernIst diese Option aktiviert, können privilegierte Mitglieder im Blog nur Artikel erstellen, indem eine  [privilegierte Mitgliedergruppe](users.md#privileged-members-group) ausgewählt werden kann. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder erstellen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassen Ist diese Option aktiviert, können Mitglieder Dateien im Blog hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Replies zulassenIst diese Option nicht aktiviert, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, Antworten auf Kommentare sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Zulassen von speziellem]**
InhaltIst diese Option aktiviert, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Kalenderfunktion {#calendar-function}

Die Kalenderfunktion ist eine Seite mit einer [Kalenderkomponente](calendar.md), die für das Tagging konfiguriert ist. Siehe auch [Kalendergrundlagen](calendar-basics-for-developers.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-384](assets/chlimage_1-384.png)

* Siehe [Titel und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Pinning zulassen]**
Ist diese Option aktiviert, können Themenantworten an den Anfang der Kommentarliste angehängt werden. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Zulassen von privilegierten]**
MitgliedernIst diese Option aktiviert, können privilegierte Mitglieder im Blog nur Artikel erstellen, indem eine  [privilegierte Mitgliedergruppe](users.md#privileged-members-group) ausgewählt werden kann. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder erstellen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassen Ist diese Option aktiviert, können Mitglieder Dateien im Blog hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Replies zulassenIst diese Option nicht aktiviert, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, Antworten auf Kommentare sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Zulassen von speziellem]**
InhaltIst diese Option aktiviert, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Katalogfunktion {#catalog-function}

Die Katalogfunktion bietet Mitgliedern der [Aktivierungs-Community](overview.md#enablement-community) die Möglichkeit, Aktivierungsressourcen zu durchsuchen, die ihnen nicht zugewiesen sind. Siehe [Tagging von Aktivierungsressourcen](tag-resources.md) und [Kataloggrundlagen](catalog-developer-essentials.md) für Entwickler.

Alle Aktivierungsressourcen und Lernpfade für die Community-Site werden in allen Katalogen angezeigt, wenn ihre Eigenschaft ` [Show in Catalog](resources.md)` auf &quot;true&quot;gesetzt ist. Um Ressourcen und Lernpfade explizit einzuschließen, müssen Sie einen [Pre-Filter](catalog-developer-essentials.md#pre-filters) auf den Katalog anwenden.

Wenn sie einer Vorlage hinzugefügt wird, ermöglicht die Konfiguration die Angabe von Tag-Namespaces, die zum Konfigurieren des Tag-Filters verwendet werden, der den Besuchern der Site angezeigt wird:

![catalogfunc](assets/catalogfunc.png)

* Siehe [Titel und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Alle Namespaces auswählen]**

   * Die ausgewählten Tag-Namespaces definieren, welche Tags von Besuchern zum Filtern der Liste der im Katalog aufgelisteten Aktivierungsressourcen ausgewählt werden können.
   * Wenn diese Option aktiviert ist, sind alle für die Community-Site zulässigen Tag-Namespaces verfügbar.
   * Wenn diese Option deaktiviert ist, können Sie einen oder mehrere Namespaces auswählen, die für die Community-Site zulässig sind.
   * Diese Option ist standardmäßig aktiviert.

### Funktion für spezielle Inhalte {#featured-content-function}

Die Funktion für speziellen Inhalt ist eine Seite mit einer [Komponente für speziellen Inhalt](featured.md), die so konfiguriert ist, dass Kommentare hinzugefügt und gelöscht werden können.

Die Möglichkeit, Inhalt zu erstellen, kann pro Komponente erlaubt oder untersagt sein (siehe [Blog-Funktion](#blog-function), [Kalenderfunktion](#calendar-function), [Forumfunktion](#forum-function), [Ideationsfunktion](#ideation-function) und [QnA-Funktion](#qna-function)).

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für [Titel und URL-Einstellungen](#title-and-url-settings).

### Dateibibliotheksfunktion {#file-library-function}

Die Dateibibliotheksfunktion ist eine Seite mit einer [Dateibibliothekskomponente](file-library.md), die so konfiguriert ist, dass Kommentare hinzugefügt und gelöscht werden können.

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für [Titel und URL-Einstellungen](#title-and-url-settings).

### Forumsfunktion {#forum-function}

Die Forumsfunktion ist eine Seite mit einer [Forumkomponente](forum.md), die für Tagging, Datei-Uploads konfiguriert ist, gefolgt von Mitgliedern zur Selbstbearbeitung, Abstimmung und Moderation.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Siehe [Titel und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Pinning zulassen]**
Ist diese Option aktiviert, können Themenantworten an den Anfang der Kommentarliste angehängt werden. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Privilegierte]**
Mitglieder zulassenIst diese Option aktiviert, können privilegierte Mitglieder nur Themen posten, indem sie eine  [privilegierte Mitgliedergruppe](users.md#privileged-members-group) auswählen. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge posten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassen Ist diese Option aktiviert, können Mitglieder Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Replies zulassen Ist diese Option nicht aktiviert, sind im Forum Kommentare zu einem Thema zulässig, Antworten auf diese Kommentare sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Zulassen von speziellem]**
InhaltIst diese Option aktiviert, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Gruppenfunktion {#groups-function}

>[!CAUTION]
>
>Die Gruppenfunktion muss *nicht* die *erste oder einzige* Funktion in der Struktur einer Site oder in einer Community-Site-Vorlage sein.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](#page-function), muss zuerst eingeschlossen und aufgelistet werden.

Die Funktion &quot;Gruppen&quot;bietet Community-Mitgliedern die Möglichkeit, Untergruppen innerhalb der Community-Site in der Veröffentlichungsumgebung zu erstellen.

Abhängig von [settings](sites-console.md#groupmanagement), wenn die Funktion &quot;Gruppen&quot;in einer [Community-Site-Vorlage](sites.md) enthalten ist, können die Gruppen öffentlich oder privat sein und eine oder mehrere Community-Gruppenvorlagen können so konfiguriert werden, dass sie eine Auswahl von Vorlagen bereitstellen, wenn die Community-Gruppe tatsächlich erstellt wird (z. B. aus der Veröffentlichungsumgebung). Eine [Community-Gruppenvorlage](tools-groups.md) gibt an, welche Communities-Funktionen für die Gruppenseiten erstellt werden, z. B. Foren und Kalender.

Wenn eine Community-Gruppe erstellt wird, wird eine Mitgliedergruppe für die neue Gruppe dynamisch erstellt, der Mitglieder zugewiesen oder hinzugefügt werden können. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Ab Communities [Feature Pack 1](deploy-communities.md#latestfeaturepack) werden Community-Gruppen in der Autorenumgebung mithilfe der [Communities Sites-Gruppenkonsole](groups.md) erstellt und können bei Aktivierung in der Veröffentlichungsumgebung erstellt werden.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-386](assets/chlimage_1-386.png)

* Siehe [Titel und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Gruppenvorlagen auswählen]**
Ein Pulldown-Menü, das die Auswahl einer oder mehrerer aktivierter Gruppenvorlagen ermöglicht, aus denen der künftige Ersteller einer neuen Community-Gruppe (in der Veröffentlichungsumgebung) wählen kann.

* **[!UICONTROL Privilegierte]**
Mitglieder zulassenIst diese Option aktiviert, können privilegierte Mitglieder nur Themen posten, indem sie eine  [privilegierte Sicherheitsgruppe](users.md#privileged-members-group) auswählen. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge posten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Erstellung]**
von Veröffentlichungen zulassenIst diese Option aktiviert, können autorisierte Community-Mitglieder eine Gruppe in der Veröffentlichungsumgebung erstellen. Wenn diese Option deaktiviert ist, können neue Gruppen (Untergruppen) nur in der Autorenumgebung über die Gruppenkonsole der Communities-Sites erstellt werden.

   Der Standardwert ist `checked`.

### Ideen-Funktion {#ideation-function}

Die Ideenfunktion ist eine Seite mit einer [Ideationskomponente](ideation-feature.md).

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem der Standardtitel und die URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt sind:

![chlimage_1-387](assets/chlimage_1-387.png)

* Siehe [Titel und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Privilegierte]**
Mitglieder zulassenIst diese Option aktiviert, können privilegierte Mitglieder nur Themen posten, indem sie eine  [privilegierte Sicherheitsgruppe](users.md#privileged-members-group) auswählen. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge posten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassen Ist diese Option aktiviert, können Mitglieder Dateien hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Replies zulassen Ist diese Option nicht aktiviert, sind Antworten (Kommentare) auf ein Thema zulässig, Antworten auf Kommentare sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Zulassen von speziellem]**
InhaltIst diese Option aktiviert, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

### Leaderboard-Funktion {#leaderboard-function}

Die Leaderboard-Funktion ist eine Seite mit einer [Leaderboard-Komponente](enabling-leaderboard.md).

**HINWEIS**: Die Leaderboard-Komponente muss weiter konfiguriert werden,  ** nachdem eine Community-Site aus einer Community-Vorlage erstellt wurde, die die Leaderboard-Funktion enthält. Die [Regeln](enabling-leaderboard.md#rules-tab) der Leaderboard-Komponente müssen angegeben werden, was von der Konfiguration von [Scoring und Badges](implementing-scoring.md) für die Community-Site abhängt.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem der Standardtitel und die URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt sind:

![chlimage_1-388](assets/chlimage_1-388.png)

* Siehe [Titel und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Display]**
BadgeIst diese Option aktiviert, wird eine Spalte für Badge-Symbole in die Leaderboard eingefügt.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Badge-]**
Name anzeigenIst diese Option aktiviert, wird eine Spalte für den Badge-Namen in die Leaderboard aufgenommen.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Anzeigen von]**
AvatarIst diese Option aktiviert, wird das Avatarbild des Mitglieds neben dem Namen des Mitglieds in das Leaderboard eingefügt und mit seinem Mitgliederprofil verknüpft.

   Diese Option ist standardmäßig deaktiviert.

### Seitenfunktion {#page-function}

Die Seitenfunktion fügt der Community-Site eine leere Seite hinzu, auf der sie mit den Funktionen der Community-Site verknüpft ist: Login, Menü, Benachrichtigungen, Messaging, Design und Branding. Inhalte können der Seite mit dem [standardmäßigen AEM-Authoring-Modus](../../help/sites-authoring/editing-content.md) hinzugefügt werden.

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für [Titel und URL-Einstellungen](#title-and-url-settings).

### Fragen/Antworten-Funktion {#qna-function}

Die QnA-Funktion ist eine Seite mit einer [QnA-Komponente](working-with-qna.md), die für Tagging, Datei-Uploads konfiguriert ist, gefolgt von Mitgliedern zur Selbstbearbeitung, Abstimmung und Moderation.

Wenn sie einer Vorlage hinzugefügt wird, ermöglicht die Konfiguration die Beschränkung auf privilegierte Mitglieder:

![chlimage_1-389](assets/chlimage_1-389.png)

* Siehe [Titel und URL-Einstellungen](#title-and-url-settings)
* **[!UICONTROL Pinning zulassen]**
Ist diese Option aktiviert, können Themenantworten an den Anfang der Kommentarliste angehängt werden. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Privilegierte]**
Mitglieder zulassenIst diese Option aktiviert, dürfen privilegierte Mitglieder nur Fragen posten, indem sie eine Auswahl einer  [privilegierten Mitgliedergruppe](users.md#privileged-members-group) zulassen. Wenn diese Option nicht aktiviert ist, dürfen alle Community-Mitglieder Beiträge posten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassenIst diese Option aktiviert, können Mitglieder Dateien im Forum zur Überprüfung hochladen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Threaded]**
Replies zulassen Ist diese Option nicht aktiviert, können im Forum Kommentare (Antworten) zu einer geposteten Frage eingesehen werden. Antworten auf Antworten sind jedoch nicht zulässig. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Zulassen von speziellem]**
InhaltIst diese Option aktiviert, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig aktiviert.

## Community-Funktion erstellen {#create-community-function}

Die Möglichkeit, eine Community-Funktion zu erstellen, wird durch Auswahl des Symbols `Create Community Function` oben in der Community Functions Console erreicht. Mehrere Funktionen, die auf demselben AEM Blueprint basieren, können erstellt und dann durch Öffnen im Bearbeitungsmodus des Autors eindeutig angepasst werden.

![chlimage_1-390](assets/chlimage_1-390.png)

### Name der Community-Funktion {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

Im Bereich &quot;Community Function Name&quot;werden ein Name, eine Beschreibung und ob die Funktion aktiviert oder deaktiviert ist konfiguriert:

* **[!UICONTROL Community-Funktionsname]**
Der Funktionsname, der für die Anzeige und Speicherung verwendet wird

* **[!UICONTROL Community-Funktion]**
BeschreibungDie Funktionsbeschreibung für die Anzeige

* **[!UICONTROL Deaktiviert/]**
AktiviertEin Umschalter, der steuert, ob die Funktion referenzierbar ist

### AEM-Blueprint {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

Im Bedienfeld `AEM Blueprint` können Sie den Blueprint auswählen, der der zugrunde liegenden Implementierung der Community-Funktion entspricht.

Die Community-Funktion ist eine Mini-Site, die aus einer oder mehreren Seiten besteht und vorab für die Integration in eine Community-Site kabelgebunden ist, einschließlich Anmelde-, Benutzer-Profilen, Benachrichtigungen, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen. Nachdem die Funktion erstellt wurde, ist es möglich, die Funktion [im Bearbeitungsmodus des Autors zu öffnen und die Seiten- und/oder Komponenteneinstellungen anzupassen.](#open-community-function)

Da die Community-Funktion als [Live Copy](../../help/sites-administering/msm.md#live-copies) eines [Blueprint](../../help/sites-administering/msm-livecopy.md#creatingablueprint) implementiert ist, ist es möglich, Änderungen an einer Funktion zu implementieren, die sich auf alle Community-Site-Seiten auswirken, die aus der [Community-Site-Vorlage](sites.md) oder [Community-Gruppenvorlage](tools-groups.md) erstellt wurden, die die Funktion enthält. Es ist auch möglich, die Zuordnung einer Seite zu ihrem übergeordneten Blueprint zu trennen, um Änderungen auf Seitenebene vorzunehmen.

Siehe auch [Multi Site Manager](../../help/sites-administering/msm.md).

### Miniaturansicht {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

Im Bedienfeld &quot;Miniaturansichten&quot;kann ein Bild hochgeladen werden, das in der Konsole [Community-Funktionen](#community-functions-console) angezeigt wird.

## Community-Funktion öffnen {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Wählen Sie das Symbol `Open Community Function` aus, um in den Bearbeitungsmodus für den Autor zu wechseln und den Seiteninhalt zu erstellen und die Konfiguration der Funktionskomponente(n) zu ändern.

### Konfigurieren von Komponenten {#configuring-components}

Eine Community-Funktion wird als Live Copy eines AEM Blueprints implementiert, deren Details unter [Multi Site Manager](../../help/sites-administering/msm.md) dokumentiert sind.

Es ist möglich, nicht nur Seiteninhalte zu erstellen, sondern Komponenten zu konfigurieren.

Wenn Sie eine Komponente auf einer Seite einer erstellten Community-Site konfigurieren, kann es erforderlich sein, die [Vererbung](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) abzubrechen, um die Komponente zu konfigurieren. Nach Abschluss der Konfiguration sollte die Vererbung wieder hergestellt werden.

Weitere Informationen zur Konfiguration finden Sie unter [Communities-Komponenten](author-communities.md) für Autoren.

## Community-Funktion bearbeiten {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Wählen Sie das Symbol `Edit Community Function` aus, um die Eigenschaften der Funktion unter Verwendung derselben Bedienfelder wie [Erstellen einer Community-Funktion](#create-community-function) zu bearbeiten, einschließlich Aktivieren oder Deaktivieren der Funktion.
