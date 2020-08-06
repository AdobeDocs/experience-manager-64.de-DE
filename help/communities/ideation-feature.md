---
title: Ideenfunktion
seo-title: Ideenfunktion
description: Hinzufügen und Konfigurieren der Funktion "Idee"
seo-description: Hinzufügen und Konfigurieren der Funktion "Idee"
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 40%

---


# Ideenfunktion {#ideation-feature}

## Einführung {#introduction}

Die Funktion &quot;Zielversion&quot;bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Umgebung &quot;Veröffentlichen&quot;für:

* Erstellen Sie Ideen, die mit der Community geteilt werden sollen
* Ansicht und Kommentar zu Ideen
* Folgen Sie einer Idee
* Abstimmung über eine Idee

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Suchfunktion zu einer AEM Site
* Konfigurationseinstellungen für die Komponente &quot;Idee&quot;

## Adding a Ideation to a Page {#adding-a-ideation-to-a-page}

Wenn Sie einer Seite im Autorenmodus eine `Ideation` Komponente hinzufügen möchten, verwenden Sie den Komponenten-Browser, um sie zu suchen `Communities / Ideation` und auf eine Seite zu ziehen, auf der die Idee angezeigt werden soll.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](ideation.md#essentials-for-client-side) are included, this is how the `Ideation`component will appear:

![chlimage_1-29](assets/chlimage_1-29.png)

## Konfigurieren einer Idee {#configuring-an-ideation}

Select the placed `Ideation` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Registerkarte „Settings“{#settings-tab}

Under the **[!UICONTROL Settings]** tab, specify settings for ideas and comments:

* **[!UICONTROL Ideentitel]** Der Anzeigentitel für die Idee. Der Standardwert ist 
`Ideation`.

* **[!UICONTROL Ideenbeschreibung]** Eine Beschreibung, die als Untertitel für die Idee angezeigt werden soll. Standard ist keine Beschreibung.

* **[!UICONTROL Themen pro Seite]** Definiert die Anzahl der pro Seite angezeigten Ideen/Beiträge. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]** Wenn diese Option aktiviert ist, muss die Veröffentlichung von Ideen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungssite angezeigt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Wenn]** diese Option aktiviert ist, wird das Ideenforum für neue Ideen und Kommentare geschlossen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Rich Text Editor]** Wenn aktiviert, können Ideen und Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Tagging zulassen]** Ist diese Option aktiviert, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **[!UICONTROL Tag-Feld]**). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads]** zulassen: Wenn diese Option aktiviert ist, können Sie zulassen, dass der Idee oder dem Kommentar Dateianlagen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Max. Dateigröße]** nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zugelassene Dateitypen]** relevant nur, wenn 
`Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **[!UICONTROL Max. Größe]** der Bilddatei anhängen ist nur relevant, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Antworten]** zulassen Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die zur Idee gepostet wurden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Erlauben Sie Benutzern, Kommentare und Themen]** zu löschen,sofern diese markiert sind, Mitgliedern das Löschen der von ihnen veröffentlichten Kommentare und Ideen zu gestatten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen]** Wenn diese Option aktiviert ist, fügen Sie folgende Funktion für Ideenbeiträge hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](notifications.md) werden können. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL E-Mail-Abonnements]** zulassen Wenn diese aktiviert sind, erlauben Sie den Mitgliedern, über neue Beiträge per E-Mail ([Abonnement](subscriptions.md)) benachrichtigt zu werden. Muss überprüft `Allow Following` und [E-Mail konfiguriert](email.md)werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]** Wenn aktiviert, lassen Sie die Abstimmung über die Kommentare einer Idee zu. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Anzeigen von Abzeichen]** Wenn aktiviert, zeigen Sie verdiente und zugewiesene [Abzeichen](implementing-scoring.md) mit der Idee eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Wenn Sie]** die Option &quot;Vorgestellte Inhalte zulassen&quot;aktivieren, kann die Idee als [speziellen Inhalt](featured.md)identifiziert werden. Diese Option ist standardmäßig deaktiviert.

### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Under the **[!UICONTROL User Moderation]** tab, specify how the posted ideas and comments (user generated content) are managed. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Posts ablehnen]** Ist diese Option aktiviert, können moderierende Mitglieder Beiträge ablehnen und so verhindern, dass diese im Forum veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]** Ist diese Option aktiviert, können moderierende Mitglieder Themen für die weitere Bearbeitung oder Kommentare schließen oder bereits geschlossene Themen erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Posts kennzeichnen]** Ist diese Option aktiviert, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kennzeichnungsgründen]** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem ein Thema oder ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Themen oder Kommentare als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]** Geben Sie an, wie oft ein Thema oder ein Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **[!UICONTROL Kennzeichnungslimit]** Geben Sie an, wie oft ein Thema oder ein Kommentar als unangemessen gekennzeichnet werden muss, bevor es oder er aus dem öffentlichen Bereich ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

### Tag-Feld, Registerkarte {#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert) verwendet werden können.

* **[!UICONTROL Zulässige Namensraum]** relevant, wenn 
`Allow Tagging` unter der Registerkarte **Einstellungen** markiert. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namensraum umfasst &quot;Standard-Tags&quot;(den standardmäßigen Namensraum) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **[!UICONTROL Empfehlungsgrenze]** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Ein Wert von 
**-** 1 bedeutet keine Begrenzung. Der Standardwert ist 0.

### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie auf der Registerkarte &quot; **[!UICONTROL Sortiereinstellungen]** &quot;an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **[!UICONTROL Sortieren nach]** Aktivieren aller zulässigen Sortierungsoptionen: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **[!UICONTROL Als Standard]**-Pulldown festlegen, um eine der aktivierten Sortieroptionen als Standard festzulegen. Der Standardwert ist 
`Newest`.

* **[!UICONTROL Wählen Sie die Zeitoptionen für die Analytics-Sortierung]**, um eine der folgenden Optionen auszuwählen: 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Erstellen einer Idee {#creating-idea}

Wie bei allen Community-Funktionen, wenn nicht angemeldet, kann ein Site-Besucher nur Ideen lesen und Ansicht andere Meinungen (durch Kommentare und Abstimmung/Gefällt mir).

Nach der Anmeldung kann ein Mitglied eine neue Idee erstellen.

![chlimage_1-32](assets/chlimage_1-32.png)

Bevor Sie die Idee einreichen, kann das Mitglied einen Entwurf speichern.

Durch Auswahl der `Save as Draft` Schaltfläche wird ein Entwurf gespeichert.

![chlimage_1-33](assets/chlimage_1-33.png)

Wenn Sie gespeicherte Entwürfe auf der `My Drafts` Registerkarte anzeigen, wählen Sie `Read More` die Option, um wieder in den Bearbeitungsmodus zu wechseln:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Feedback bereitstellen {#providing-feedback}

Sobald die Idee veröffentlicht ist, können sich andere Mitglieder anmelden, die Idee ( `Read More`) öffnen und die Idee mögen, um so zur Stimmenauszählung hinzuzufügen und Kommentare.

![chlimage_1-35](assets/chlimage_1-35.png)

### Zusätzliche Informationen {#additional-information}

More information may be found on the [Ideation Essentials](ideation.md) page for developers.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).
