---
title: Funktion „Fragen-und-Antworten-Forum“
seo-title: Q&A Forum Feature
description: Hinzufügen der Funktion "Fragen und Antworten"zu einer Seite
seo-description: Adding the QnA forum feature to a page
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
exl-id: af16f4df-ed8e-40e4-b117-3d612e122947
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 59%

---

# Funktion „Fragen-und-Antworten-Forum“ {#q-a-forum-feature}

## Einführung {#introduction}

Die Funktion des Forums Fragen und Antworten bietet Community-Mitgliedern die Möglichkeit, Fragen zu stellen und zu beantworten:

* Neue Fragen erstellen
* Inline-Bilder (mit Drag-and-Drop-Unterstützung)
* Fragen anzeigen und beantworten
* Suchen nach Fragen
* Moderieren des QnA-Inhalts
* Identifizieren der besten Antworten
* Verschieben von Fragen zur Abfrage von einer Seite auf eine andere

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Funktion &quot;Fragen und Antworten&quot;zu einer AEM
* Konfigurationseinstellungen für `QnA`component

## Hinzufügen eines Fragen-und-Antworten-Forums zu einer Seite {#adding-a-q-a-forum-to-a-page}

So fügen Sie eine `QnA` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / QnA` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der das Forum zur Frage der Antworten erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](qna-essentials.md#essentials-for-client-side) eingeschlossen sind, wird die `QnA` wird angezeigt:

![chlimage_1-280](assets/chlimage_1-280.png)

### Konfigurieren von Fragen und Antworten {#configuring-qna}

Wählen Sie die platzierte `QnA` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Registerkarte „Settings“ {#settings-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die Einstellungen für Themen (Fragen) und Antworten fest:

* **[!UICONTROL Themen pro Seite]** Definiert die Anzahl der Fragen/Posts, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]** Ist diese Option aktiviert, müssen Themen zunächst genehmigt werden, bevor sie öffentlich zugänglich gemacht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Geschlossen]** Ist diese Option aktiviert, können im Forum keine neuen Fragen und Kommentare veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Rich-Text-Editor]** Ist diese Option aktiviert, können Themen und Kommentare mit Markup versehen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Tagging zulassen]** Ist diese Option aktiviert, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **[!UICONTROL Tag-Feld]**). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]** Ist diese Option aktiviert, können Fragen oder Kommentaren Dateien hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Maximale Dateigröße]**
Nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige Dateitypen]**
Nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Maximale Dateigröße für Bildanhang]**
Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Folgende erlauben]**
Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumsbeiträge hinzu, mit der Mitglieder [benachrichtigt](notifications.md) von neuen Stellen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen von Pinnwänden]**
Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste gesetzt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL E-Mail-Abonnements zulassen]**
Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge informiert werden ([Abonnement](subscriptions.md)). Erfordert `Allow Following` zu überprüfen und [E-Mail konfiguriert](email.md). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Antworten zulassen]** Ist diese Option aktiviert, können Kommentare zur Frage hinterlassen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Anmerkungen und Themen ermöglichen]** Ist diese Option aktiviert, können Mitglieder eigens veröffentlichte Kommentare und Fragen löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]** Ist diese Option aktiviert, kann die Funktion „Abstimmung“ Fragen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Ausgewählte Antwort an den Anfang verschieben]** Ist diese Option aktiviert, ist die erste angezeigte Antwort eine ausgewählte Antwort. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Anzeigemarken]**
Wenn diese Option aktiviert ist, zeigen Sie Earned und Assored [Badges](implementing-scoring.md) mit dem Blogeintrag eines Mitglieds. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen von speziellen Inhalten]**
Wenn diese Option aktiviert ist, kann die Idee als [präsentierte Inhalte](featured.md). Diese Option ist standardmäßig deaktiviert.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **[!UICONTROL Benutzermoderation]** festlegen, wie die veröffentlichten Themen (Fragen) und Antworten (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Antworten verweigern]** Ist diese Option aktiviert, können moderierende Mitglieder Antworten ablehnen und so verhindern, dass diese Beiträge im Fragen-und-Antworten-Forum veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]** Ist diese Option aktiviert, können moderierende Mitglieder Fragen (Themen) für die weitere Bearbeitung oder Beantwortung schließen oder bereits geschlossene Fragen erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Verschieben von Themen]**
Wenn diese Option aktiviert ist, können Moderatoren auf Veröffentlichungsseite Fragen verschieben. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Posts kennzeichnen]** Ist diese Option aktiviert, können Mitglieder Fragen oder Antworten anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kennzeichnungsgründen]** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem eine Frage oder Antwort als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Fragen oder Antworten als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]** Geben Sie an, wie oft eine Frage oder Antwort von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **[!UICONTROL Kennzeichnungslimit]** Geben Sie an, wie oft eine Frage oder Antwort als unangemessen gekennzeichnet werden muss, bevor sie aus dem öffentlichen Bereich ausgeblendet wird. Bei einem Wert von -1 wird die gekennzeichnete Frage oder Antwort nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert) verwendet werden können.

* **[!UICONTROL Zulässige Namespaces]**
Relevant, wenn 
`Allow Tagging` wird unter dem **Einstellungen** Registerkarte. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **[!UICONTROL Empfehlungsgrenze]** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Ein Wert von 
`-1` bedeutet keine Beschränkungen. Der Standardwert ist 0.

#### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

Unter dem **[!UICONTROL Sortiereinstellungen]** festlegen, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **[!UICONTROL Sortieren nach]**
Aktivieren Sie alle zulässigen Sortieroptionen: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **[!UICONTROL Als Standard festlegen]**
Ziehen Sie den Mauszeiger nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden sollen. Der Standardwert ist 
`Newest`.

* **[!UICONTROL Zeitoptionen für Analytics-Sortierung auswählen]**
Ziehen Sie nach unten, um eines von 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Identifizieren von Antworten {#identifying-answers}

Eine Antwort kann mit der Variablen `Select Answer` Schaltfläche. Nachdem eine Frage als beantwortet markiert wurde, kann erst eine andere Antwort ausgewählt werden, nachdem die erste mit der Variablen `Unmark Chosen Answer`Schaltfläche.

Nach Auswahl als praktikable Antwort kann die Auswahl mithilfe der Variablen `Unmark Chosen Answer` Schaltfläche.

Sobald eine Antwort als praktikable Antwort ausgewählt wurde, ein Hinweis darauf, dass die Frage `Answered`wird neben dem Fragethema auf der Hauptseite der Fragen angezeigt.

### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderatoren- oder Administrationsrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer die Frage oder Antwort verfasst hat.

Zudem ist es diesen Benutzern auch möglich, Antworten zu identifizieren.

### Mitglieder {#members}

Abhängig von der Konfiguration können angemeldete Besucher Folgendes tun:

* Eine neue Frage posten
* Von ihnen erstellte Fragen bearbeiten oder löschen
* Kann auch Fragen oder Antworten anderer kennzeichnen
* Kann Antworten auf von ihnen erstellte Fragen identifizieren

### Anonym {#anonymous}

Site-Besucher, die sich nicht angemeldet haben, können lediglich bereits veröffentlichte Fragen und Antworten lesen und diese übersetzen (falls unterstützt), sind jedoch nicht dazu in der Lage, selbst Fragen oder Antworten zu verfassen oder die Beiträge anderer zu markieren.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Grundlagen von Fragen und Antworten](qna-essentials.md).

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).
