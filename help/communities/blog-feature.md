---
title: Blogfunktion
seo-title: Blogfunktion
description: Community-Informationen im Journalformat
seo-description: Community-Informationen im Journalformat
uuid: 01f1a547-d22b-4da6-a69c-ab420e5a9e19
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d5519211-8a04-4699-97bc-e162ec0f3781
exl-id: 12ae8b4c-73c5-4ec9-beea-b682b55ebdfd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 48%

---

# Blogfunktion {#blog-feature}

## Einführung {#introduction}

Die Blogfunktion für AEM Communities wurde von einer Erstellungsaktivität in eine richtige Community-Aktivität umgewandelt, die in der Veröffentlichungsumgebung stattfindet.

Die Blogfunktion unterstützt die Bereitstellung von Community-Informationen in einem Aufzeichnungsformat. Blogeinträge werden in der Veröffentlichungsumgebung von autorisierten Mitgliedern (registrierten, angemeldeten Benutzern) vorgenommen.

Die Blogfunktion bietet Folgendes:

* Erstellung von Blogartikeln und -kommentaren in der Veröffentlichungsumgebung
* Bearbeiten von Rich-Text
* Inline-Bilder (mit Drag-and-Drop-Unterstützung)
* Eingebetteter Inhalt in sozialen Netzwerken ([Unterstützung von oEmbed](blog-developer-basics.md#allowing-rich-media))
* Entwurfsmodus
* Geplantes Veröffentlichen
* Erstellen im Auftrag (ein [privilegiertes Mitglied](users.md#privileged-members-group) kann Inhalte im Namen eines anderen Community-Mitglieds erstellen)
* [In-Kontext- und Massenmoderation](moderate-ugc.md) von Blogartikeln und -kommentaren

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Blog-Funktion zu einer AEM Site
* Konfigurationseinstellungen für Blogkomponenten

>[!NOTE]
>
>Die Komponenten `Journal`und `Journal Sidebar` haben die Titel `Blog` und `Blog Sidebar`.
>
>Die Blogfunktion in AEM 6.0 und älteren Versionen wurde eingestellt. Sie beruhte auf einer Vorlage und beschränkte das Verfassen von Inhalten ausschließlich auf die Autorenumgebung.

## Hinzufügen von Blog-Komponenten zu einer Seite {#adding-blog-components-to-a-page}

Wenn Sie im Autorenmodus einen Blog zu einer Seite hinzufügen möchten, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Blog`
* `Communities / Blog Sidebar`

Ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der der Blog erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](blog-developer-basics.md#essentials-for-client-side) enthalten sind, wird die `Blog`Komponente wie folgt angezeigt:

![chlimage_1-147](assets/chlimage_1-147.png)

Und wie das `Blog Sidebar` angezeigt wird:

![chlimage_1-148](assets/chlimage_1-148.png)

### Konfigurieren eines Blogs {#configuring-blog}

Wählen Sie die platzierte Komponente `Blog` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure ](assets/chlimage_1-149.png) ![iconBlog settings](assets/Blog-configure.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die grundlegenden Eigenschaften des Blogs an:

* **[!UICONTROL Attachment Thumbnail zulassen]**
Ist diese Option aktiviert, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **[!UICONTROL Maximale Größe für Miniaturansichten anhängen Maximale Größe]**
(in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **[!UICONTROL Min. Bildgröße für]**
MiniaturansichtenMindestgröße (in Byte) des Bildes zum Generieren von Miniaturansichten für Inline-Bilder. Der Standardwert ist 100000 Bytes (100 KB).

* **[!UICONTROL Maximale]**
Größe der MiniaturansichtenMaximale Größe (in Pixel) des Miniaturbilds für Inline-Bilder. Der Standardwert ist 800 x 800.

* **[!UICONTROL Zulassen von privilegierten]**
MitgliedernIst diese Option aktiviert, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **[!UICONTROL Zulässige privilegierte]**
MitgliederFügen Sie die berechtigten Mitglieder hinzu, die Inhalte erstellen dürfen.

* **[!UICONTROL Vom Benutzer generierte Inhalte im Authoring-]**
Modus blockieren Ist diese Option aktiviert, wird benutzergenerierter Inhalt bei der Bearbeitung im Autorenmodus blockiert.

* **[!UICONTROL Journaltitel]** Der Blogname, der auf der Seite angezeigt werden soll.
   >Hinweis:
   >Der Journaltitel wird verwendet, um automatisch eine URL für den Blog zu erstellen. Maximal 50 Zeichen (mit 5 zusätzlichen Zeichen für Eindeutigkeit) werden aus dem hier angegebenen Journaltitel verwendet, um eine URL für den Blog zu erstellen.

* **[!UICONTROL Journalbeschreibung]** Die Beschreibung des Blogs.

* **[!UICONTROL Themen pro Seite]**

   Definiert die Anzahl der Blogeinträge/Kommentare, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]**

   Wenn diese Option aktiviert ist, muss das Posten von Blogeinträgen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Geschlossen]**

   Wenn diese Option aktiviert ist, ist der Blog für neue Blog-Einträge und Kommentare geschlossen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Rich-Text-Editor]**

   Wenn diese Option aktiviert ist, können Blogeinträge und Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Tagging zulassen]**

   Wenn diese Option aktiviert ist, können Mitglieder ihrem Beitrag Tag-Beschriftungen hinzufügen (siehe Registerkarte **[!UICONTROL Tag-Feld]** ). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]**

   Wenn diese Option aktiviert ist, können Sie einem Blogeintrag oder Kommentar Dateianlagen hinzufügen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Max. Dateigröße]**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige Dateitypen]**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Maximale Dateigröße für Bildanhang]**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Antworten zulassen]**

   Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die auf den Blogeintrag gepostet wurden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Anmerkungen und Themen ermöglichen]**

   Wenn diese Option aktiviert ist, können Mitglieder die Kommentare und Blogeinträge löschen, die sie veröffentlicht haben. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Folgende zulassen]**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder [benachrichtigt](notifications.md) über neue Beiträge werden können. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL E-Mail-Abonnements zulassen]**

   Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge benachrichtigt werden ([subscription](subscriptions.md)). Erfordert die Überprüfung von `Allow Following` und die Konfiguration von [E-Mail](email.md). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**

   Wenn diese Option aktiviert ist, fügen Sie die Funktion Abstimmung in einen Blogeintrag ein. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abzeichen anzeigen]**

   Wenn diese Option aktiviert ist, zeigen Sie verdiente und zugewiesene [Badges](implementing-scoring.md) mit dem Blogeintrag eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Feature-Inhalt zulassen]**

   Wenn diese Option aktiviert ist, kann die Idee als [spezieller Inhalt](featured.md) identifiziert werden. Diese Option ist standardmäßig deaktiviert.

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Benutzermoderation]** die Moderationseinstellungen an:

* **[!UICONTROL Posts ablehnen]**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]**

   Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Thema möglicherweise erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Posts kennzeichnen]**

   Wenn diese Option aktiviert ist, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kenn-zeichnungsgründen]**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Themen oder Kommentare als unangemessen gekennzeichnet werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**

   Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen eingeben. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**

   Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **[!UICONTROL Kennzeichnungslimit]**

   Geben Sie an, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot;{#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** können Sie angeben, welche Tags verwendet werden dürfen, wenn die Option **[!UICONTROL Tagging zulassen]** auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert wurde:

* **[!UICONTROL Zulässige Namespaces]**

   Relevant, wenn `Allow Tagging` auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert ist. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **[!UICONTROL Empfehlungsgrenze]**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert -1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

### Konfigurieren einer Blog-Seitenleiste  {#configuring-blog-sidebar}

Wenn Sie auf die Komponente `Blog Sidebar` doppelklicken, wird ein Dialogfeld zum Bearbeiten geöffnet.

Auf der Registerkarte **[!UICONTROL Journal-Sidebar-Einstellungen]** können Sie das Datumsformat für Archive festlegen und angeben, welche Eintragstypen in der Seitenleiste aufgeführt werden sollen:

![chlimage_1-151](assets/chlimage_1-151.png)

* **[!UICONTROL Datumsformat]**

   Das Format, das für die Anzeige von Archiven von Blogeinträgen verwendet wird. In diesem Format finden sich Platzhalter, die der Java-Konvention folgen.

   * JJJJ: lange Jahresangabe, z. B. 2015
   * JJ: kurze Jahresangabe, z. B. 15
   * MMMMM: vollständiger Monat, z. B. Juni
   * MMM: abgekürzter Monat, z. B. Jun
   * MM: Monatszahl, z. B. 06

   Der Standardwert ist &quot;jjjj MMMMM&quot;, der beispielsweise &quot;Juni 2015&quot;anzeigen würde.

* **[!UICONTROL Ansichtstyp]**

   Der Titel und der Typ der Blogeinträge, die in der Seitenleiste angezeigt werden sollen. Die können aus folgenden Kategorien wählen:

   * Autoren
   * Kategorien
   * Archive

* **[!UICONTROL Journal-Komponentenpfad]**

   *(Optional)* Der Speicherort der Blog-Ressource, von der aus Blog-Artikel aufgelistet werden sollen. Wenn Sie das Feld leer lassen, wird die Komponente von resourceType `social/journal/components/hbs/journal` verwendet, die auf derselben Seite angezeigt wird.

   * Beispiel: `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **[!UICONTROL Empfehlungsgrenze]**

   Die Anzahl der anzuzeigenden Blogartikel. Der Wert -1 bedeutet keine Begrenzung. Der Standardwert ist -1.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung wird bei der Blogfunktion der neueste Blogartikel angezeigt, gefolgt von älteren Einträgen, die absteigend nach Erstellungsdatum sortiert sind. Blog-Seitenleisten ermöglichen es Besuchern der Site, einen Filter anzuwenden, um die Auswahl der anzuzeigenden Artikel einzuschränken.

Dem Blogartikel folgt ein Link, über den Kommentare gelesen oder verfasst werden können.

Wurde ein Blogartikel ausgewählt, werden der Artikel sowie zugehörige Kommentare eingeblendet (falls aktiviert).

Die Verfügbarkeit weiterer Optionen hängt davon ab, ob der Site-Besucher Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonymer Besucher ist.

### Arbeiten mit Artikeln  {#working-with-articles}

Wenn Sie einen neuen Blogartikel erstellen, können Sie aus folgenden Optionen wählen:

1. Sofort veröffentlichen
1. Einen Entwurf veröffentlichen
1. An einem geplanten Datum und zu einer geplanten Uhrzeit veröffentlichen

Die Blogartikel erscheinen auf der entsprechenden Registerkarte („Veröffentlicht“, „Entwürfe“ oder „Geplant“) und können von Mitgliedern bei der Veröffentlichung bearbeitet werden.

#### Moderatoren und Administratoren  {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er [Moderationsaufgaben](moderate-ugc.md) für alle Blogartikel und Komponenten des Blogs durchführen (je nach Berechtigungen durch die Konfiguration der Komponente).

![chlimage_1-152](assets/chlimage_1-152.png)

### Mitglieder {#members}

Wenn der angemeldete Benutzer Community-Mitglied oder [privilegiertes Mitglied](users.md#privileged-members-group) ist (je nach Konfiguration), kann er `New Article` auswählen, um einen neuen Blog-Artikel zu erstellen und zu posten.

Insbesondere können sie:

* Erstellen eines neuen Blogartikels
* Posten eines neuen Blogartikels im Namen eines anderen Mitglieds
* Posten eines Kommentars zu einem Blogartikel
* Bearbeiten eigener Blogartikel oder Kommentare
* Löschen eigener Blogartikel oder Kommentare
* Kennzeichnen von Blogartikeln oder -kommentaren anderer Benutzer

![chlimage_1-153](assets/chlimage_1-153.png) ![chlimage_1-154](assets/chlimage_1-154.png)

### Anonym {#anonymous}

Nicht angemeldete Besucher können veröffentlichte Blogartikel und Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Artikel oder Kommentare hinzufügen und keine Artikel und Kommentare anderer Benutzer kennzeichnen.

![chlimage_1-155](assets/chlimage_1-155.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Blog-Grundlagen](blog-developer-basics.md).

Informationen zur Moderation von Blogartikeln und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von Blogartikeln und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).

Informationen zur Übersetzung von Blogartikeln und Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](translate-ugc.md).
