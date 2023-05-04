---
title: Frage- und Forumsfunktion
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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 2%

---

# Frage- und Forumsfunktion {#q-a-forum-feature}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Die Funktion des Forums Fragen und Antworten bietet Community-Mitgliedern die Möglichkeit, Fragen zu stellen und zu beantworten:

* Neue Fragen erstellen
* Inline-Bilder (mit Drag &amp; Drop-Unterstützung)
* Fragen anzeigen und beantworten
* Suchen nach Fragen
* Moderieren des QnA-Inhalts
* Identifizieren der besten Antworten
* Verschieben von Fragen zur Abfrage von einer Seite auf eine andere

In diesem Abschnitt der Dokumentation wird

* Hinzufügen der Funktion &quot;Fragen und Antworten&quot;zu einer AEM
* Konfigurationseinstellungen für `QnA`component

## Hinzufügen eines Fragen- und Verwaltungsforums zu einer Seite {#adding-a-q-a-forum-to-a-page}

So fügen Sie eine `QnA` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / QnA` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der das Forum zur Frage der Antworten erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](qna-essentials.md#essentials-for-client-side) eingeschlossen sind, wird die `QnA` wird angezeigt:

![chlimage_1-280](assets/chlimage_1-280.png)

### Konfigurieren von Fragen und Antworten {#configuring-qna}

Wählen Sie die platzierte `QnA` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Registerkarte Einstellungen {#settings-tab}

Unter dem **[!UICONTROL Einstellungen]** Registerkarte Einstellungen für Themen (Fragen) und Antworten (Antworten) festlegen:

* **[!UICONTROL Themen pro Seite]**
Definiert die Anzahl der Fragen/Beiträge, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]**
Wenn diese Option aktiviert ist, muss das Posten von Themen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Geschlossen]**
Wenn diese Option aktiviert ist, können im Forum keine neuen Fragen und Kommentare gestellt werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Rich-Text-Editor]**
Wenn diese Option aktiviert ist, können Themen und Kommentare mit Markup eingegeben werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Tagging zulassen]**
Wenn diese Option aktiviert ist, können Mitglieder ihrem Beitrag Tag-Beschriftungen hinzufügen (siehe **[!UICONTROL Tag-Feld]** Registerkarte). Die Option Standard ist deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]**
Wenn diese Option aktiviert ist, können der Frage oder dem Kommentar Dateianlagen hinzugefügt werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Maximale Dateigröße]**
Nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe einer hochgeladenen Datei (in Byte). Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige Dateitypen]**
Nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, dürfen nicht angegebene nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Maximale Dateigröße für Bildanhang]**
Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Maximale Anzahl der Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Folgende erlauben]**
Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumsbeiträge hinzu, mit der Mitglieder [benachrichtigt](notifications.md) von neuen Stellen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Zulassen von Pinnwänden]**
Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste gesetzt werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL E-Mail-Abonnements zulassen]**
Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge informiert werden ([Abonnement](subscriptions.md)). Erfordert `Allow Following` zu überprüfen und [E-Mail konfiguriert](email.md). Die Option Standard ist deaktiviert.

* **[!UICONTROL Antworten zulassen]**
Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die auf die Frage gepostet wurden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Kommentaren und Themen ermöglichen]**
Wenn diese Option aktiviert ist, können Mitglieder die von ihnen veröffentlichten Kommentare und Fragen löschen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**
Wenn diese Option aktiviert ist, fügen Sie die Funktion Abstimmung einer Frage hinzu. Die Option Standard ist deaktiviert.

* **[!UICONTROL Ausgewählte Antwort nach oben verschieben]**
Wenn diese Option aktiviert ist, ist die erste angezeigte Antwort eine ausgewählte Antwort. Die Option Standard ist aktiviert.

* **[!UICONTROL Anzeigemarken]**
Wenn diese Option aktiviert ist, zeigen Sie Earned und Assored [Badges](implementing-scoring.md) mit dem Blogeintrag eines Mitglieds. Die Option Standard ist deaktiviert.

* **[!UICONTROL Zulassen von speziellen Inhalten]**
Wenn diese Option aktiviert ist, kann die Idee als [präsentierte Inhalte](featured.md). Die Option Standard ist deaktiviert.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **[!UICONTROL Benutzermoderation]** festlegen, wie die veröffentlichten Themen (Fragen) und Antworten (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Antworten verweigern]**
Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern gepostete Antworten ablehnen und verhindern, dass die Antwort im öffentlichen Frage- und A-Forum erscheint. Die Option Standard ist deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]**
Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern eine Frage (Thema) schließen, um weitere Bearbeitungen und Antworten vorzunehmen, und eine Frage auch erneut öffnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Verschieben von Themen]**
Wenn diese Option aktiviert ist, können Moderatoren auf Veröffentlichungsseite Fragen verschieben. Die Option Standard ist deaktiviert.

* **[!UICONTROL Posts kennzeichnen]**
Ist diese Option aktiviert, können Mitglieder Fragen oder Antworten anderer Mitglieder als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Liste der Kennzeichnungsgründe]**
Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem eine Frage oder Antwort als unangemessen gekennzeichnet wird. Die Option Standard ist deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**
Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung einer Frage oder Antwort als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**
Geben Sie an, wie oft eine Frage oder Antwort von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **[!UICONTROL Kennzeichnungslimit]**
Geben Sie an, wie oft eine Frage oder Antwort gekennzeichnet werden muss, bevor sie aus der öffentlichen Ansicht ausgeblendet wird. Wenn der Wert auf -1 gesetzt ist, wird die gekennzeichnete Frage oder Antwort nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für Moderation sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Unter dem **[!UICONTROL Tag-Feld]** Registerkarte die Tags, die angewendet werden können, sofern dies unter der Variablen **[!UICONTROL Einstellungen]** Registerkarte, sind entsprechend den ausgewählten Namespaces begrenzt.

* **[!UICONTROL Zulässige Namespaces]**
Relevant, wenn 
`Allow Tagging` wird unter dem **Einstellungen** Registerkarte. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Der Standardwert ist &quot;none&quot;, was bedeutet, dass alle Namespaces zulässig sind.

* **[!UICONTROL Empfehlungslimit]**
Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Ein Wert von 
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

### Antworten identifizieren {#identifying-answers}

Eine Antwort kann mit der Variablen `Select Answer` Schaltfläche. Nachdem eine Frage als beantwortet markiert wurde, kann erst eine andere Antwort ausgewählt werden, nachdem die erste mit der Variablen `Unmark Chosen Answer`Schaltfläche.

Nach Auswahl als praktikable Antwort kann die Auswahl mithilfe der Variablen `Unmark Chosen Answer` Schaltfläche.

Sobald eine Antwort als praktikable Antwort ausgewählt wurde, ein Hinweis darauf, dass die Frage `Answered`wird neben dem Fragethema auf der Hauptseite der Fragen angezeigt.

### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorberechtigungen verfügt, kann er die durch die Konfiguration der Komponente zulässigen Moderationsaufgaben ausführen, unabhängig davon, wer die Frage oder Antwort verfasst hat.

Sie können auch Antworten identifizieren.

### Mitglieder {#members}

Wenn der Besucher der Site angemeldet ist, kann er je nach Konfiguration

* Eine neue Frage posten
* Von ihnen erstellte Fragen bearbeiten oder löschen
* Kann auch Fragen oder Antworten anderer kennzeichnen
* Kann Antworten auf von ihnen erstellte Fragen identifizieren

### Anonym {#anonymous}

Besucher der Website, die nicht angemeldet sind, dürfen nur veröffentlichte Fragen und Antworten lesen, sie übersetzen, sofern sie unterstützt werden, dürfen jedoch weder eine Frage noch eine Antwort hinzufügen noch die Beiträge anderer kennzeichnen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen der quantitativen Lockerung](qna-essentials.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).
