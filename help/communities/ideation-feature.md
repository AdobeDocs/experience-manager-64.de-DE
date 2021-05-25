---
title: Ideen-Funktion
seo-title: Ideen-Funktion
description: Hinzufügen und Konfigurieren der Funktion "Idee"
seo-description: Hinzufügen und Konfigurieren der Funktion "Idee"
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
exl-id: 391885f2-e46d-4eb4-9c88-509233505df8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 40%

---

# Ideenfunktion {#ideation-feature}

## Einführung {#introduction}

Die Filterfunktion bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung für:

* Erstellen von Ideen für die Community
* Ideen anzeigen und kommentieren
* Folgen Sie einer Idee
* Abstimmung über eine Idee

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Filterfunktion zu einer AEM Site
* Konfigurationseinstellungen für die Komponente &quot;Idee&quot;

## Hinzufügen einer Idee zu einer Seite {#adding-a-ideation-to-a-page}

Um eine Komponente `Ideation` im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie im Komponenten-Browser nach `Communities / Ideation` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der die Idee erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](ideation.md#essentials-for-client-side) enthalten sind, wird die `Ideation`Komponente wie folgt angezeigt:

![chlimage_1-29](assets/chlimage_1-29.png)

## Konfigurieren einer Idee {#configuring-an-ideation}

Wählen Sie die platzierte Komponente `Ideation` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Registerkarte „Settings“{#settings-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** Einstellungen für Ideen und Kommentare fest:

* **[!UICONTROL Ideen-]**
TitelDer Anzeigentitel für die Idee. Der Standardwert ist 
`Ideation`.

* **[!UICONTROL Idee]**
BeschreibungEine Beschreibung, die als Untertitel für die Idee angezeigt wird. Der Standardwert ist keine Beschreibung.

* **[!UICONTROL Themen pro]**
SeiteDefiniert die Anzahl der Ideen/Beiträge, die pro Seite angezeigt werden. Der Standardwert ist 10.

* ****
ModeriertIst diese Option aktiviert, muss das Posten von Ideen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Diese Option ist standardmäßig deaktiviert.

* ****
ClosedIst diese Option aktiviert, können im Ideenforum keine neuen Ideen und Kommentare eingesehen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Rich-Text-]**
EditorIst diese Option aktiviert, können Ideen und Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Tagging zulassen]** Ist diese Option aktiviert, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **[!UICONTROL Tag-Feld]**). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-]**
Uploads zulassenIst diese Option aktiviert, können der Idee oder dem Kommentar Dateianlagen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Max File]**
SizeRelevant nur, wenn 
`Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige]**
DateitypenNur relevant, wenn 
`Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Maximale Größe der Bilddatei anhängenNur relevant, wenn]**
die Option &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Antworten zulassen]**
Ist diese Option aktiviert, können Antworten auf Kommentare zu der Idee erstellt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Kommentaren und]**
Themen ermöglichen Ist diese Option aktiviert, können Mitglieder die von ihnen veröffentlichten Kommentare und Ideen löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen]**
Folgende Funktion ist aktiviert. Fügen Sie für Ideen-Beiträge die folgende Funktion hinzu, damit Mitglieder über neue Beiträge  [](notifications.md) benachrichtigt werden können. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL E-Mail-]**
Abonnements zulassenIst diese Option aktiviert, können Mitglieder per E-Mail über neue Beiträge benachrichtigt werden ([Abonnement](subscriptions.md)). Erfordert die Überprüfung von `Allow Following` und die Konfiguration von [E-Mail](email.md). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**
Ist diese Option aktiviert, können Sie über die Kommentare einer Idee abstimmen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Display]**
BadgesWenn diese Option aktiviert ist, zeigen Sie mit der Idee eines Mitglieds verdiente und zugewiesene  [](implementing-scoring.md) Abzeichen an. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen]**
von speziellen Inhalten Ist diese Option aktiviert, kann die Idee als  [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig deaktiviert.

### Registerkarte Benutzermoderation {#user-moderation-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Benutzermoderation]** an, wie die veröffentlichten Ideen und Kommentare (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Posts ablehnen]** Ist diese Option aktiviert, können moderierende Mitglieder Beiträge ablehnen und so verhindern, dass diese im Forum veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]** Ist diese Option aktiviert, können moderierende Mitglieder Themen für die weitere Bearbeitung oder Kommentare schließen oder bereits geschlossene Themen erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Posts kennzeichnen]** Ist diese Option aktiviert, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kennzeichnungsgründen]** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem ein Thema oder ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Themen oder Kommentare als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]** Geben Sie an, wie oft ein Thema oder ein Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **[!UICONTROL Kennzeichnungslimit]** Geben Sie an, wie oft ein Thema oder ein Kommentar als unangemessen gekennzeichnet werden muss, bevor es oder er aus dem öffentlichen Bereich ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

### Registerkarte &quot;Tag-Feld&quot;{#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert) verwendet werden können.

* **[!UICONTROL Zulässige]**
NamespacesRelevant, wenn 
`Allow Tagging` wird unter der Registerkarte  **** Einstellungen überprüft. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **[!UICONTROL Empfehlungsgrenze]** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Ein Wert von 
**-** 1 bedeutet keine Begrenzung. Der Standardwert ist 0.

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

## Site-Besuchererlebnis {#site-visitor-experience}

### Erstellen einer Idee {#creating-idea}

Wie bei allen Communities-Funktionen kann ein Besucher der Site, falls er nicht angemeldet ist, nur Ideen lesen und andere Meinungen ansehen (durch Kommentare und Abstimmung/Gefällt mir).

Nach der Anmeldung kann ein Mitglied eine neue Idee erstellen.

![chlimage_1-32](assets/chlimage_1-32.png)

Vor dem Senden der Idee kann das Mitglied einen Entwurf speichern.

Durch Auswahl der Schaltfläche `Save as Draft` wird ein Entwurf gespeichert.

![chlimage_1-33](assets/chlimage_1-33.png)

Wenn Sie gespeicherte Entwürfe auf der Registerkarte `My Drafts` anzeigen, wählen Sie `Read More` aus, um wieder in den Bearbeitungsmodus zu wechseln:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Feedback geben {#providing-feedback}

Sobald die Idee veröffentlicht wurde, können sich andere Mitglieder anmelden, die Idee ( `Read More`) öffnen und die Idee mögen, so zur Stimmenanzahl hinzufügen und Kommentare machen.

![chlimage_1-35](assets/chlimage_1-35.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Ideen-Grundlagen](ideation.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).
