---
title: Funktion „Fragen-und-Antworten-Forum“
seo-title: Funktion „Fragen-und-Antworten-Forum“
description: Hinzufügen der Funktion des QnA-Forums zu einer Seite
seo-description: Hinzufügen der Funktion des QnA-Forums zu einer Seite
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Funktion „Fragen-und-Antworten-Forum“{#q-a-forum-feature}

## Einführung {#introduction}

Das Forum für Fragen und Antworten bietet Community-Mitgliedern einen Raum, Fragen zu stellen und zu beantworten:

* Neue Fragen erstellen
* Inline-Bilder (mit Drag-and-Drop-Unterstützung)
* Fragen anzeigen und beantworten
* Nach einer Frage suchen
* Hilfe beim Moderieren des QnA-Inhalts
* Identifizieren Sie die besten Antworten.
* QnA-Fragen von einer Seite auf eine andere verschieben

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Funktion des QnA-Forums zu einer AEM-Site
* Configuration settings for the `QnA`component

## Hinzufügen eines Fragen-und-Antworten-Forums zu einer Seite {#adding-a-q-a-forum-to-a-page}

Um eine `QnA` Komponente einer Seite im Autorenmodus hinzuzufügen, verwenden Sie den Komponenten-Browser, um sie zu suchen `Communities / QnA` und auf eine Seite zu ziehen, auf der das QnA-Forum angezeigt werden soll.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](qna-essentials.md#essentials-for-client-side) are included, this is how the `QnA` component will appear:

![chlimage_1-280](assets/chlimage_1-280.png)

### Konfigurieren von Fragen und Antworten {#configuring-qna}

Select the placed `QnA` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Registerkarte „Settings“{#settings-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die Einstellungen für Themen (Fragen) und Antworten fest:

* **[!UICONTROL Themen pro Seite]** Definiert die Anzahl der Fragen/Posts, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]** Ist diese Option aktiviert, müssen Themen zunächst genehmigt werden, bevor sie öffentlich zugänglich gemacht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Geschlossen]** Ist diese Option aktiviert, können im Forum keine neuen Fragen und Kommentare veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Rich-Text-Editor]** Ist diese Option aktiviert, können Themen und Kommentare mit Markup versehen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Tagging zulassen]** Ist diese Option aktiviert, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **[!UICONTROL Tag-Feld]**). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]** Ist diese Option aktiviert, können Fragen oder Kommentaren Dateien hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Max. Dateigröße]** Relevant nur, wenn `Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige Dateitypen]** Relevant nur, wenn `Allow File Uploads` aktiviert. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **[!UICONTROL Max. Größe]** der Bilddatei anhängen ist nur relevant, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Zulassen]** Wenn diese Option aktiviert ist, fügen Sie folgende Funktion für Forumbeiträge hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](notifications.md) werden können. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Veröffentlichen]** zulassen Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste eingefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL E-Mail-Abonnements]** zulassen Wenn diese Option aktiviert ist, erlauben Sie Mitgliedern, über neue Beiträge per E-Mail ([Abonnement](subscriptions.md)) benachrichtigt zu werden. Muss überprüft `Allow Following` und [E-Mail konfiguriert](email.md)werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Antworten zulassen]** Ist diese Option aktiviert, können Kommentare zur Frage hinterlassen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Anmerkungen und Themen ermöglichen]** Ist diese Option aktiviert, können Mitglieder eigens veröffentlichte Kommentare und Fragen löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]** Ist diese Option aktiviert, kann die Funktion „Abstimmung“ Fragen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Ausgewählte Antwort an den Anfang verschieben]** Ist diese Option aktiviert, ist die erste angezeigte Antwort eine ausgewählte Antwort. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Anzeigen von Abzeichen]** Wenn aktiviert, zeigen Sie verdiente und zugewiesene [Abzeichen](implementing-scoring.md) mit dem Blog-Eintrag eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Wenn Sie]** die Option &quot;Vorgestellte Inhalte zulassen&quot;aktivieren, kann die Idee als [speziellen Inhalt](featured.md)identifiziert werden. Diese Option ist standardmäßig deaktiviert.

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Under the **[!UICONTROL User Moderation]** tab, specify how the posted topics (quetions) and answers (user generated content) are managed. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Antworten verweigern]** Ist diese Option aktiviert, können moderierende Mitglieder Antworten ablehnen und so verhindern, dass diese Beiträge im Fragen-und-Antworten-Forum veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]** Ist diese Option aktiviert, können moderierende Mitglieder Fragen (Themen) für die weitere Bearbeitung oder Beantwortung schließen oder bereits geschlossene Fragen erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen]** verschieben Wenn diese Option aktiviert ist, können Sie Moderatoren auf Veröffentlichungsseite das Verschieben von Fragen zulassen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Posts kennzeichnen]** Ist diese Option aktiviert, können Mitglieder Fragen oder Antworten anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kennzeichnungsgründen]** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem eine Frage oder Antwort als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Fragen oder Antworten als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]** Geben Sie an, wie oft eine Frage oder Antwort von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **[!UICONTROL Kennzeichnungslimit]** Geben Sie an, wie oft eine Frage oder Antwort als unangemessen gekennzeichnet werden muss, bevor sie aus dem öffentlichen Bereich ausgeblendet wird. Bei einem Wert von -1 wird die gekennzeichnete Frage oder Antwort nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert) verwendet werden können.

* **[!UICONTROL Zulässige Namespaces]** Relevant, wenn `Allow Tagging` sie auf der Registerkarte **Einstellungen** markiert sind. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **[!UICONTROL Empfehlungsgrenze]** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Ein Wert von `-1` bedeutet keine Grenzen. Der Standardwert ist 0.

#### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie auf der Registerkarte &quot; **[!UICONTROL Sortiereinstellungen]** &quot;an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **[!UICONTROL Sortieren nach]** Aktivieren aller zulässigen Sortierungsoptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **[!UICONTROL Als Standard]**-Pulldown festlegen, um eine der aktivierten Sortieroptionen als Standard festzulegen. Der Standardwert ist `Newest`.

* **[!UICONTROL Wählen Sie die Zeitoptionen für die Analytics-Sortierung]** Pulldown aus, um eine von `All, Last 24 Hours, Last 7 Days, Last 30 Days`auszuwählen. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Identifizieren von Antworten {#identifying-answers}

Eine Antwort kann mit der `Select Answer` Schaltfläche als richtige oder nützliche Antwort gekennzeichnet werden. Nachdem eine Frage als &quot;Beantwortet&quot;markiert wurde, kann erst eine andere Antwort ausgewählt werden, wenn die erste mit der `Unmark Chosen Answer`Schaltfläche deaktiviert wurde.

Once selected as a viable answer, it may be unselected using the `Unmark Chosen Answer` button.

Sobald eine Antwort als praktikable Antwort ausgewählt wurde, wird auf der Hauptseite der QnA neben dem Fragethema ein Hinweis darauf angezeigt, dass die Frage angezeigt `Answered`wurde.

### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderatoren- oder Administrationsrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer die Frage oder Antwort verfasst hat.

Zudem ist es diesen Benutzern auch möglich, Antworten zu identifizieren.

### Mitglieder {#members}

Abhängig von der Konfiguration können angemeldete Besucher Folgendes tun:

* Eine neue Frage posten
* Bearbeiten oder Löschen von erstellten Fragen
* Kann auch Fragen oder Antworten anderer hervorheben
* Kann Antworten auf von ihnen erstellte Fragen identifizieren

### Anonym {#anonymous}

Site-Besucher, die sich nicht angemeldet haben, können lediglich bereits veröffentlichte Fragen und Antworten lesen und diese übersetzen (falls unterstützt), sind jedoch nicht dazu in der Lage, selbst Fragen oder Antworten zu verfassen oder die Beiträge anderer zu markieren.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Grundlagen von Fragen und Antworten](qna-essentials.md).

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).
