---
title: Forumsfunktion
seo-title: Forum Feature
description: Hinzufügen und Konfigurieren der Forumsfunktion
seo-description: How to add and configure the forum feature
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 2%

---

# Forumsfunktion {#forum-feature}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Die Forumsfunktion bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung, in dem Folgendes möglich ist:

* Erstellen neuer Themen
* Themen anzeigen und beantworten
* Thema folgen
* Forum durchsuchen
* Moderieren von Forumsinhalten
* Verschieben von Forumthemen von einer Seite auf eine andere

In diesem Abschnitt der Dokumentation wird

* Hinzufügen der Forumsfunktion zu einer AEM
* Konfigurationseinstellungen für `Forum`component

## Hinzufügen eines Forums zu einer Seite {#adding-a-forum-to-a-page}

So fügen Sie eine `Forum` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Forum`

Ziehen Sie es an die gewünschte Stelle auf einer Seite, auf der das Forum erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](essentials-forum.md#essentials-for-client-side) eingeschlossen sind, wird die `Forum`wird angezeigt:

![chlimage_1-60](assets/chlimage_1-60.png)

## Konfigurieren eines Forums {#configuring-a-forum}

Wählen Sie die platzierte `Forum` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Registerkarte Einstellungen {#settings-tab}

Unter dem **[!UICONTROL Einstellungen]** Registerkarte Einstellungen für Themen und Antworten festlegen:

* **[!UICONTROL Themen pro Seite]**
Definiert die Anzahl der Themen/Beiträge, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]**
Wenn diese Option aktiviert ist, muss das Posten von Themen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Geschlossen]**
Wenn diese Option aktiviert ist, können im Forum keine neuen Themen und Kommentare erstellt werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Rich-Text-Editor]**
Wenn diese Option aktiviert ist, können Themen und Kommentare mit Markup eingegeben werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Tagging zulassen]**
Wenn diese Option aktiviert ist, können Mitglieder ihrem Beitrag Tag-Beschriftungen hinzufügen (siehe **[!UICONTROL Tag-Feld]** Registerkarte). Die Option Standard ist deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]**
Wenn diese Option aktiviert ist, können dem Thema oder Kommentar Dateianlagen hinzugefügt werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Folgende erlauben]**
Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumsbeiträge hinzu, mit der Mitglieder [benachrichtigt](notifications.md) von neuen Stellen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Zulassen von Pinnwänden]**
Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste gesetzt werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Zulassen von speziellen Inhalten]**
Wenn diese Option aktiviert ist, kann die Idee als [präsentierte Inhalte](featured.md). Die Option Standard ist deaktiviert.

* **[!UICONTROL E-Mail-Abonnements zulassen]**
Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge informiert werden ([Abonnement](subscriptions.md)). Erfordert `Allow Following` zu überprüfen und [E-Mail konfiguriert](email.md). Die Option Standard ist deaktiviert.

* **[!UICONTROL Maximale Dateigröße]**
Nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe einer hochgeladenen Datei (in Byte). Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige Dateitypen]**
Nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, dürfen nicht angegebene nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Maximale Dateigröße für Bildanhang]**
Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Maximale Anzahl der Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Threaded-Antworten zulassen]**
Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die zum Thema gepostet wurden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Kommentaren und Themen ermöglichen]**
Wenn diese Option aktiviert ist, können Mitglieder die von ihnen veröffentlichten Kommentare und Themen löschen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**
Wenn diese Option aktiviert ist, fügen Sie die Abstimmungsfunktion in ein Thema ein. Die Option Standard ist deaktiviert.

* **[!UICONTROL Breadcrumbs anzeigen]**
Wenn diese Option aktiviert ist, zeigen Sie Navigations-Breadcrumbs auf Themenseiten an. Die Option Standard ist aktiviert.

* **[!UICONTROL Anzeigemarken]**
Wenn diese Option aktiviert ist, zeigen Sie Earned und Assored [Badges](implementing-scoring.md) mit dem Blogeintrag eines Mitglieds. Die Option Standard ist deaktiviert.

>[!NOTE]
>
>Es kann erforderlich sein, beide `AllowThreaded Replies` und `Allow users to Delete Comments and Topics` , um Kommentare zu einem Thema zu aktivieren.

### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **[!UICONTROL Benutzermoderation]** -Registerkarte angeben, wie die veröffentlichten Themen und Antworten (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Posts verweigern]**
Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Die Option Standard ist deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]**
Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Thema möglicherweise erneut öffnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Verschieben von Themen]**
Wenn diese Option aktiviert ist, lassen Sie zu, dass Moderatoren auf Veröffentlichungsseite Themen verschieben. Die Option Standard ist aktiviert.

* **[!UICONTROL Posts kennzeichnen]**
Wenn diese Option aktiviert ist, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Liste der Kennzeichnungsgründe]**
Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Themen oder Kommentare als unangemessen gekennzeichnet werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**
Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**
Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **[!UICONTROL Kennzeichnungslimit]**
Geben Sie an, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Wenn der Wert auf -1 festgelegt ist, wird das gekennzeichnete Thema oder der Kommentar nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für Moderation sein. Der Standardwert ist 5.

### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Unter dem **[!UICONTROL Tag-Feld]** Registerkarte die Tags, die angewendet werden können, sofern dies unter der Variablen **[!UICONTROL Einstellungen]** Registerkarte, sind entsprechend den ausgewählten Namespaces begrenzt.

* **[!UICONTROL Zulässige Namespaces]**
Relevant, wenn `Allow Tagging` wird unter dem **[!UICONTROL Einstellungen]** Registerkarte. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Der Standardwert ist &quot;none&quot;, was bedeutet, dass alle Namespaces zulässig sind.

* **[!UICONTROL Empfehlungslimit]**
Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Standardwert ist 
**-** 1 (keine Beschränkungen).

### Tab &quot;Übersetzung&quot; {#translation-tab}

Unter dem **[!UICONTROL Übersetzung]** -Registerkarte, wenn die Übersetzung für die Community-Site aktiviert ist, kann die Übersetzung so eingestellt sein, dass das gesamte Thema oder ausgewählte Beiträge übersetzt werden.

* **[!UICONTROL Alle übersetzen]**
Wenn diese Option aktiviert ist, wird der Forum-Thread in die bevorzugte Sprache des Benutzers übersetzt. Die Option Standard ist deaktiviert.

### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

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

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Forumsgrundlagen](essentials-forum.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).

Informationen zur Übersetzung von veröffentlichten Themen und Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](translate-ugc.md).
