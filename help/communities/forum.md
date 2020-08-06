---
title: Funktion „Forum“
seo-title: Funktion „Forum“
description: Hinzufügen und Konfigurieren der Forumsfunktion
seo-description: Hinzufügen und Konfigurieren der Forumsfunktion
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 63%

---


# Funktion „Forum“{#forum-feature}

## Einführung {#introduction}

Die Forumsfunktion bietet einen Bereich, in dem angemeldete Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung Folgendes tun können:

* Erstellen neuer Themen
* Ansicht und Beantwortung von Themen
* Thema
* Forum suchen
* Hilfe beim Moderieren des Foruminhalts
* Verschieben von Forumthemen von einer Seite auf eine andere

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Forumsfunktion zu einer AEM Site
* Configuration settings for the `Forum`component

## Hinzufügen eines Forums zu einer Seite {#adding-a-forum-to-a-page}

To add a `Forum` component to a page in author mode, use the component browser to locate

* `Communities / Forum`

Ziehen Sie es auf eine Seite, auf der das Forum erscheinen soll.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](essentials-forum.md#essentials-for-client-side) are included, this is how the `Forum`component will appear:

![chlimage_1-60](assets/chlimage_1-60.png)

## Konfigurieren eines Forums {#configuring-a-forum}

Select the placed `Forum` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Registerkarte „Settings“{#settings-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die Einstellungen für Themen und Antworten fest:

* **[!UICONTROL Themen pro Seite]** Definiert die Anzahl der Themen/Posts, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]** Ist diese Option aktiviert, müssen Themen zunächst genehmigt werden, bevor sie öffentlich zugänglich gemacht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Geschlossen]** Ist diese Option aktiviert, können im Forum keine neuen Themen und Kommentare erstellt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Rich-Text-Editor]** Ist diese Option aktiviert, können Themen und Kommentare mit Markup versehen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Tagging zulassen]** Ist diese Option aktiviert, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **[!UICONTROL Tag-Feld]**). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]** Ist diese Option aktiviert, können Themen oder Kommentaren Dateien hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen]** Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumbeiträge hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](notifications.md) werden können. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Veröffentlichen]** zulassen Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Liste der Themen eingefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Wenn Sie]** die Option &quot;Vorgestellte Inhalte zulassen&quot;aktivieren, kann die Idee als [speziellen Inhalt](featured.md)identifiziert werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL E-Mail-Abonnements]** zulassen Wenn diese aktiviert sind, erlauben Sie den Mitgliedern, über neue Beiträge per E-Mail ([Abonnement](subscriptions.md)) benachrichtigt zu werden. Muss überprüft `Allow Following` und [E-Mail konfiguriert](email.md)werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Max. Dateigröße]** nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zugelassene Dateitypen]** relevant nur, wenn 
`Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **[!UICONTROL Max. Größe]** der Bilddatei anhängen ist nur relevant, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Antworten mit Diskussionsfaden zulassen]** Ist diese Option aktiviert, können Kommentare zum Thema hinterlassen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Anmerkungen und Themen ermöglichen]** Ist diese Option aktiviert, können Mitglieder von ihnen veröffentlichte Kommentare und Themen löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]** Ist diese Option aktiviert, kann die Funktion „Abstimmung“ Themen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Breadcrumbs anzeigen]** Ist diese Option aktiviert, werden Breadcrumbs für die Navigation auf den Themenseiten eingeblendet. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Anzeigen von Abzeichen]** Wenn aktiviert, zeigen Sie verdiente und zugewiesene [Abzeichen](implementing-scoring.md) mit dem Blog-Eintrag eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

>[!NOTE]
>
>Es kann erforderlich sein, Kommentare zu einem Thema sowohl zu prüfen `AllowThreaded Replies` als auch `Allow users to Delete Comments and Topics` zu aktivieren.

### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Under the **[!UICONTROL User Moderation]** tab, specify how the posted topics and replies (user generated content) are managed. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Posts ablehnen]** Ist diese Option aktiviert, können moderierende Mitglieder Beiträge ablehnen und so verhindern, dass diese im Forum veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]** Ist diese Option aktiviert, können moderierende Mitglieder Themen für die weitere Bearbeitung oder Kommentare schließen oder bereits geschlossene Themen erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen]** verschieben Wenn diese Option aktiviert ist, können Sie Moderatoren auf der Veröffentlichungsseite das Verschieben von Themen gestatten. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Posts kennzeichnen]** Ist diese Option aktiviert, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kennzeichnungsgründen]** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem ein Thema oder ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Themen oder Kommentare als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]** Geben Sie an, wie oft ein Thema oder ein Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **[!UICONTROL Kennzeichnungslimit]** Geben Sie an, wie oft ein Thema oder ein Kommentar als unangemessen gekennzeichnet werden muss, bevor es oder er aus dem öffentlichen Bereich ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

### Tag-Feld, Registerkarte {#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert) verwendet werden können.

* **[!UICONTROL Zulässige Namensraum]** Relevant, wenn `Allow Tagging` auf der Registerkarte &quot; **[!UICONTROL Einstellungen]** &quot;aktiviert ist. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namensraum umfasst &quot;Standard-Tags&quot;(den standardmäßigen Namensraum) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **[!UICONTROL Empfehlungsgrenze]** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Der Standardwert ist 
**-** 1 (keine Beschränkungen).

### Registerkarte &quot;Übersetzung&quot; {#translation-tab}

Auf der Registerkarte **[!UICONTROL Übersetzung]** können Sie festlegen, ob bei für die Community-Site aktivierter Übersetzungsoption der gesamte Thread oder nur bestimmte Posts übersetzt werden sollen.

* **[!UICONTROL Alles übersetzen]** Ist diese Option aktiviert, wird der Forums-Thread in die Sprache des Benutzers übersetzt. Diese Option ist standardmäßig deaktiviert.

### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie auf der Registerkarte &quot; **[!UICONTROL Sortiereinstellungen]** &quot;an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **[!UICONTROL Sortieren nach]** Aktivieren aller zulässigen Sortierungsoptionen: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **[!UICONTROL Als Standard]**-Pulldown festlegen, um eine der aktivierten Sortieroptionen als Standard festzulegen. Der Standardwert ist 
`Newest`.

* **[!UICONTROL Wählen Sie die Zeitoptionen für die Analytics-Sortierung]**, um eine der folgenden Optionen auszuwählen: 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. Der Standardwert ist `All`.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Forumsgrundlagen](essentials-forum.md).

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).

Informationen zur Übersetzung von veröffentlichten Themen und Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](translate-ugc.md).
