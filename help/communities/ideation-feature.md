---
title: Ideen-Funktion
seo-title: Ideation Feature
description: Hinzufügen und Konfigurieren der Funktion "Idee"
seo-description: Adding and configuring the Ideation feature
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
exl-id: 391885f2-e46d-4eb4-9c88-509233505df8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 2%

---

# Ideen-Funktion {#ideation-feature}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Die Filterfunktion bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung für:

* Erstellen von Ideen für die Community
* Ideen anzeigen und kommentieren
* Folgen Sie einer Idee
* Abstimmung über eine Idee

In diesem Abschnitt der Dokumentation wird

* Hinzufügen der Filterfunktion zu einer AEM Site
* Konfigurationseinstellungen für die Komponente &quot;Idee&quot;

## Hinzufügen einer Idee zu einer Seite {#adding-a-ideation-to-a-page}

So fügen Sie eine `Ideation` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / Ideation` und ziehen Sie sie an die gewünschte Stelle auf der Seite, auf der die Idee erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](ideation.md#essentials-for-client-side) eingeschlossen sind, wird die `Ideation`wird angezeigt:

![chlimage_1-29](assets/chlimage_1-29.png)

## Konfigurieren einer Idee {#configuring-an-ideation}

Wählen Sie die platzierte `Ideation` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Registerkarte Einstellungen {#settings-tab}

Unter dem **[!UICONTROL Einstellungen]** Registerkarte Einstellungen für Ideen und Kommentare festlegen:

* **[!UICONTROL Ideentitel]**
Der Anzeigetitel für die Idee. Der Standardwert ist 
`Ideation`.

* **[!UICONTROL Ideenbeschreibung]**
Eine Beschreibung, die als Untertitel für die Idee angezeigt wird. Der Standardwert ist keine Beschreibung.

* **[!UICONTROL Themen pro Seite]**
Definiert die Anzahl der pro Seite angezeigten Ideen/Beiträge. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]**
Wenn diese Option aktiviert ist, muss die Veröffentlichung von Ideen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Geschlossen]**
Wenn diese Option aktiviert ist, steht das Ideenforum neuen Ideen und Kommentaren offen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Rich-Text-Editor]**
Wenn diese Option aktiviert ist, können Ideen und Kommentare mit Markup eingegeben werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Tagging zulassen]**
Wenn diese Option aktiviert ist, können Mitglieder ihrem Beitrag Tag-Beschriftungen hinzufügen (siehe **[!UICONTROL Tag-Feld]** Registerkarte). Die Option Standard ist deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]**
Wenn diese Option aktiviert ist, können der Idee oder dem Kommentar Dateianlagen hinzugefügt werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Maximale Dateigröße]**
Nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe einer hochgeladenen Datei (in Byte). Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige Dateitypen]**
Nur relevant, wenn 
`Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, dürfen nicht angegebene nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Maximale Dateigröße für Bildanhang]**
Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Maximale Anzahl der Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Antworten zulassen]**
Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die zur Idee gepostet wurden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Kommentaren und Themen ermöglichen]**
Wenn diese Option aktiviert ist, können Mitglieder die Kommentare und Ideen löschen, die sie veröffentlicht haben. Die Option Standard ist deaktiviert.

* **[!UICONTROL Folgende erlauben]**
Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Ideenbeiträge hinzu, mit der Mitglieder [benachrichtigt](notifications.md) von neuen Stellen. Die Option Standard ist deaktiviert.

* **[!UICONTROL E-Mail-Abonnements zulassen]**
Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge informiert werden ([Abonnement](subscriptions.md)). Erfordert `Allow Following` zu überprüfen und [E-Mail konfiguriert](email.md). Die Option Standard ist deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**
Sofern aktiviert, können Sie über die Kommentare einer Idee abstimmen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Anzeigemarken]**
Wenn diese Option aktiviert ist, zeigen Sie Earned und Assored [Badges](implementing-scoring.md) mit der Idee eines Mitglieds. Die Option Standard ist deaktiviert.

* **[!UICONTROL Zulassen von speziellen Inhalten]**
Wenn diese Option aktiviert ist, kann die Idee als [präsentierte Inhalte](featured.md). Die Option Standard ist deaktiviert.

### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **[!UICONTROL Benutzermoderation]** -Registerkarte angeben, wie die veröffentlichten Ideen und Kommentare (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Posts verweigern]**
Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Die Option Standard ist deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]**
Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Thema möglicherweise erneut öffnen. Die Option Standard ist deaktiviert.

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
Relevant, wenn 
`Allow Tagging` wird unter dem **Einstellungen** Registerkarte. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Der Standardwert ist &quot;none&quot;, was bedeutet, dass alle Namespaces zulässig sind.

* **[!UICONTROL Empfehlungslimit]**
Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Ein Wert von 
**-** 1 bedeutet keine Begrenzung. Der Standardwert ist 0.

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

## Site-Besuchererlebnis {#site-visitor-experience}

### Erstellen einer Idee {#creating-idea}

Wie bei allen Communities-Funktionen kann ein Besucher der Site, falls er nicht angemeldet ist, nur Ideen lesen und andere Meinungen ansehen (durch Kommentare und Abstimmung/Gefällt mir).

Nach der Anmeldung kann ein Mitglied eine neue Idee erstellen.

![chlimage_1-32](assets/chlimage_1-32.png)

Vor dem Senden der Idee kann das Mitglied einen Entwurf speichern.

Durch Auswahl der `Save as Draft` -Schaltfläche verwenden, wird ein Entwurf gespeichert.

![chlimage_1-33](assets/chlimage_1-33.png)

Beim Anzeigen gespeicherter Entwürfe im `My Drafts` Registerkarte, wählen Sie `Read More` , um wieder in den Bearbeitungsmodus zu wechseln:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Feedback geben {#providing-feedback}

Sobald die Idee veröffentlicht wurde, können sich andere Mitglieder anmelden und die Idee öffnen ( `Read More`) und wie die Idee, so zur Stimmenanzahl, und Kommentare.

![chlimage_1-35](assets/chlimage_1-35.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Ideengrundlagen](ideation.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).
