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
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 63%

---

# Funktion „Forum“{#forum-feature}

## Einführung {#introduction}

Die Forumsfunktion bietet einen Bereich, in dem angemeldete Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung Folgendes tun können:

* Erstellen neuer Themen
* Themen anzeigen und beantworten
* Thema folgen
* Forum durchsuchen
* Moderieren von Forumsinhalten
* Verschieben von Forumthemen von einer Seite auf eine andere

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Forumsfunktion zu einer AEM
* Konfigurationseinstellungen für die Komponente `Forum`

## Hinzufügen eines Forums zu einer Seite {#adding-a-forum-to-a-page}

Um eine Komponente `Forum` im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Forum`

Ziehen Sie es an die gewünschte Stelle auf einer Seite, auf der das Forum erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-forum.md#essentials-for-client-side) enthalten sind, wird die `Forum`Komponente wie folgt angezeigt:

![chlimage_1-60](assets/chlimage_1-60.png)

## Konfigurieren eines Forums {#configuring-a-forum}

Wählen Sie die platzierte Komponente `Forum` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Registerkarte „Settings“{#settings-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die Einstellungen für Themen und Antworten fest:

* **[!UICONTROL Themen pro Seite]** Definiert die Anzahl der Themen/Posts, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]** Ist diese Option aktiviert, müssen Themen zunächst genehmigt werden, bevor sie öffentlich zugänglich gemacht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Geschlossen]** Ist diese Option aktiviert, können im Forum keine neuen Themen und Kommentare erstellt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Rich-Text-Editor]** Ist diese Option aktiviert, können Themen und Kommentare mit Markup versehen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Tagging zulassen]** Ist diese Option aktiviert, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **[!UICONTROL Tag-Feld]**). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]** Ist diese Option aktiviert, können Themen oder Kommentaren Dateien hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen]**
Folgende Funktion ist aktiviert. Fügen Sie für Forumsbeiträge die folgende Funktion hinzu, damit Mitglieder über neue Beiträge  [](notifications.md) benachrichtigt werden können. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen von]**
PinningIst diese Option aktiviert, können Forumsthemen an den Anfang der Themenliste verschoben werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen]**
von speziellen Inhalten Ist diese Option aktiviert, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL E-Mail-]**
Abonnements zulassenIst diese Option aktiviert, können Mitglieder per E-Mail über neue Beiträge benachrichtigt werden ([Abonnement](subscriptions.md)). Erfordert die Überprüfung von `Allow Following` und die Konfiguration von [E-Mail](email.md). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Max File]**
SizeRelevant nur, wenn 
`Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige]**
DateitypenNur relevant, wenn 
`Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Maximale Größe der Bilddatei anhängenNur relevant, wenn]**
die Option &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Antworten mit Diskussionsfaden zulassen]** Ist diese Option aktiviert, können Kommentare zum Thema hinterlassen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Anmerkungen und Themen ermöglichen]** Ist diese Option aktiviert, können Mitglieder von ihnen veröffentlichte Kommentare und Themen löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]** Ist diese Option aktiviert, kann die Funktion „Abstimmung“ Themen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Breadcrumbs anzeigen]** Ist diese Option aktiviert, werden Breadcrumbs für die Navigation auf den Themenseiten eingeblendet. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Display]**
BadgesWenn diese Option aktiviert ist, zeigen Sie mit dem Blogeintrag eines Mitglieds verdiente und zugewiesene  [](implementing-scoring.md) Abzeichen an. Diese Option ist standardmäßig deaktiviert.

>[!NOTE]
>
>Es kann erforderlich sein, sowohl `AllowThreaded Replies` als auch `Allow users to Delete Comments and Topics` zu überprüfen, um Kommentare zu einem Thema zu aktivieren.

### Registerkarte Benutzermoderation {#user-moderation-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Benutzermoderation]** an, wie die veröffentlichten Themen und Antworten (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Posts ablehnen]** Ist diese Option aktiviert, können moderierende Mitglieder Beiträge ablehnen und so verhindern, dass diese im Forum veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]** Ist diese Option aktiviert, können moderierende Mitglieder Themen für die weitere Bearbeitung oder Kommentare schließen oder bereits geschlossene Themen erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen verschiebenWenn diese Option aktiviert ist, können Moderatoren auf Veröffentlichungsseite Themen verschieben.]**
Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Posts kennzeichnen]** Ist diese Option aktiviert, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kennzeichnungsgründen]** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem ein Thema oder ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Themen oder Kommentare als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]** Geben Sie an, wie oft ein Thema oder ein Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **[!UICONTROL Kennzeichnungslimit]** Geben Sie an, wie oft ein Thema oder ein Kommentar als unangemessen gekennzeichnet werden muss, bevor es oder er aus dem öffentlichen Bereich ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

### Registerkarte &quot;Tag-Feld&quot;{#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert) verwendet werden können.

* **[!UICONTROL Zulässige]**
NamespacesRelevant , wenn  `Allow Tagging` unter der Registerkarte  **** Einstellungen aktiviert ist. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **[!UICONTROL Empfehlungsgrenze]** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Der Standardwert ist 
**-** 1 (keine Beschränkungen).

### Registerkarte &quot;Übersetzung&quot;{#translation-tab}

Auf der Registerkarte **[!UICONTROL Übersetzung]** können Sie festlegen, ob bei für die Community-Site aktivierter Übersetzungsoption der gesamte Thread oder nur bestimmte Posts übersetzt werden sollen.

* **[!UICONTROL Alles übersetzen]** Ist diese Option aktiviert, wird der Forums-Thread in die Sprache des Benutzers übersetzt. Diese Option ist standardmäßig deaktiviert.

### Registerkarte &quot;Sortiereinstellungen&quot;{#sort-settings-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Sortiereinstellungen]** an, wie die veröffentlichten Kommentare sortiert werden sollen, wenn sie angezeigt werden.

* **[!UICONTROL Sortieren]**
nach Alle zulässigen Sortieroptionen aktivieren: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **[!UICONTROL Als]**
DefaultPull festlegen, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden soll. Der Standardwert ist 
`Newest`.

* **[!UICONTROL Zeitoptionen für Analytics-]**
Sortierung auswählen Pulldown zum Auswählen einer der folgenden Optionen 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. Der Standardwert ist `All`.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Forumsgrundlagen](essentials-forum.md).

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).

Informationen zur Übersetzung von veröffentlichten Themen und Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](translate-ugc.md).
