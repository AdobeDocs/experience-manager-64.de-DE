---
title: Blogfunktion
seo-title: Blogfunktion
description: Gemeinschaftsinformationen in journalistischer Form
seo-description: Gemeinschaftsinformationen in journalistischer Form
uuid: 01f1a547-d22b-4da6-a69c-ab420e5a9e19
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d5519211-8a04-4699-97bc-e162ec0f3781
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 48%

---


# Blogfunktion {#blog-feature}

## Einführung {#introduction}

Die Blogfunktion für AEM Communities wurde von einer Erstellungsaktivität in eine richtige Community-Aktivität umgewandelt, die in der Veröffentlichungsumgebung stattfindet.

Die Blogfunktion unterstützt die Bereitstellung von Community-Informationen in einem Aufzeichnungsformat. Blog-Einträge werden in der Umgebung &quot;Veröffentlichen&quot;von autorisierten Mitgliedern (registrierte, angemeldete Benutzer) vorgenommen.

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
* Konfigurationseinstellungen für Blog-Komponenten

>[!NOTE]
>
>Die Komponenten `Journal`und `Journal Sidebar` sind mit `Blog` und `Blog Sidebar`.
>
>Die Blogfunktion in AEM 6.0 und älteren Versionen wurde eingestellt. Sie beruhte auf einer Vorlage und beschränkte das Verfassen von Inhalten ausschließlich auf die Autorenumgebung.

## Hinzufügen von Blog-Komponenten zu einer Seite {#adding-blog-components-to-a-page}

Wenn Sie im Autorenmodus einen Blog zu einer Seite hinzufügen möchten, suchen Sie im Komponentenbrowser nach

* `Communities / Blog`
* `Communities / Blog Sidebar`

Ziehen Sie sie auf eine Seite, auf der der Blog erscheinen soll.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](blog-developer-basics.md#essentials-for-client-side) are included, this is how the `Blog`component will appear:

![chlimage_1-147](assets/chlimage_1-147.png)

Und wie das `Blog Sidebar` aussehen wird:

![chlimage_1-148](assets/chlimage_1-148.png)

### Konfigurieren eines Blogs {#configuring-blog}

Select the placed `Blog` component to access and select the `Configure` icon which opens the edit dialog.

![Symboleinstellungen](assets/chlimage_1-149.png) für ![Blog konfigurieren](assets/Blog-configure.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die grundlegenden Eigenschaften des Blogs an:

* **[!UICONTROL &quot;Miniaturansicht]** zulassen&quot;Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **[!UICONTROL Maximale Größe]** der Miniaturansicht der Anlage (in Pixel). Der Standardwert ist 800 x 800.

* **[!UICONTROL Min. Bildgröße für Miniaturansichten]**. Mindestgröße (in Byte) des Bildes für die Erstellung von Miniaturbildern für Inline-Bilder. Der Standardwert ist 100000 Byte (100 KB).

* **[!UICONTROL Maximale Größe]** der Miniaturansicht des Inline-Bildes (in Pixel). Der Standardwert ist 800 x 800.

* **[!UICONTROL Privilegierte Mitglieder]** zulassen Wenn diese Option aktiviert ist, dürfen nur Privilegierte Mitglieder Inhalte erstellen.

* **[!UICONTROL Zulässige privilegierte Mitglieder]** Hinzufügen die privilegierten Mitglieder, die Inhalte erstellen dürfen.

* **[!UICONTROL Blockieren benutzergenerierter Inhalte im Bearbeitungsmodus]**&quot;Autor&quot;Blockieren Sie,wenn diese Option aktiviert ist, beim Bearbeiten im Autorenmodus den vom Benutzer erstellten Inhalt.

* **[!UICONTROL Journaltitel]** Der Blogname, der auf der Seite angezeigt werden soll.
   >Hinweis:
   >Mit dem Protokoll-Titel wird automatisch eine URL für den Blog erstellt. Maximal 50 Zeichen (mit 5 zusätzlichen Zeichen zur Eindeutigkeit) werden aus dem hier angegebenen Protokoll-Titel verwendet, um eine URL für den Blog zu erstellen.

* **[!UICONTROL Journalbeschreibung]** Die Beschreibung des Blogs.

* **[!UICONTROL Themen pro Seite]**

   Definiert die Anzahl der Blog-Einträge/Kommentare pro Seite. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]**

   Wenn diese Option aktiviert ist, muss die Veröffentlichung von Blog-Einträgen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungssite erscheinen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Geschlossen]**

   Wenn diese Option aktiviert ist, wird der Blog für neue Blog-Einträge und Kommentare geschlossen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Rich-Text-Editor]**

   Wenn diese Option aktiviert ist, können Blog-Einträge und Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Tagging zulassen]**

   If checked, allow members to add tag labels to their post (see **[!UICONTROL Tag field]** tab). Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]**

   Wenn diese Option aktiviert ist, können Sie zulassen, dass dem Blog-Eintrag oder -Kommentar Dateianlagen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Max. Dateigröße]**

   Relevant nur, wenn `Allow File Uploads` aktiviert. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige Dateitypen]**

   Relevant nur, wenn `Allow File Uploads` aktiviert. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **[!UICONTROL Maximale Dateigröße für Bildanhang]**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Antworten zulassen]**

   Wenn diese Option aktiviert ist, lassen Sie Antworten auf Kommentare zu, die im Blog-Eintrag veröffentlicht wurden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Anmerkungen und Themen ermöglichen]**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, die von ihnen veröffentlichten Kommentare und Blog-Einträge zu löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Folgende zulassen]**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](notifications.md) werden können. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL E-Mail-Abonnements zulassen]**

   Wenn diese Option aktiviert ist, können Sie den Mitgliedern per E-Mail ([Abonnement](subscriptions.md)) eine Benachrichtigung über neue Beiträge erlauben. Muss überprüft `Allow Following` und [E-Mail konfiguriert](email.md)werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**

   Wenn diese Option aktiviert ist, fügen Sie die Funktion &quot;Abstimmung&quot;in einen Blog-Eintrag ein. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abzeichen anzeigen]**

   Wenn diese Option aktiviert ist, zeigen Sie verdiente und zugewiesene [Abzeichen](implementing-scoring.md) mit dem Blog-Eintrag eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Feature-Inhalt zulassen]**

   Wenn diese Option aktiviert ist, kann die Idee als [spezieller Inhalt](featured.md)identifiziert werden. Diese Option ist standardmäßig deaktiviert.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Benutzermoderation]** die Moderationseinstellungen an:

* **[!UICONTROL Posts ablehnen]**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge verweigern und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]**

   Wenn diese Option aktiviert ist, können Moderatoren mit vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Änderungen und Kommentare vorzunehmen, und ein Thema erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Posts kennzeichnen]**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, die Themen oder Kommentare anderer als unangemessen zu kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kenn-zeichnungsgründen]**

   Wenn diese Option aktiviert ist, können die Mitglieder aus einer Dropdown-Liste auswählen, aus welchem Grund sie ein Thema oder einen Kommentar als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen einzugeben. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**

   Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **[!UICONTROL Kennzeichnungslimit]**

   Geben Sie an, wie oft ein Thema oder Kommentar markiert werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** können Sie angeben, welche Tags verwendet werden dürfen, wenn die Option **[!UICONTROL Tagging zulassen]** auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert wurde:

* **[!UICONTROL Zulässige Namespaces]**

   Relevant, wenn `Allow Tagging` unter der Registerkarte **[!UICONTROL Einstellungen]** markiert wurde. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namensraum umfasst &quot;Standard-Tags&quot;(den standardmäßigen Namensraum) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **[!UICONTROL Empfehlungsgrenze]**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert -1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

### Konfigurieren einer Blog-Seitenleiste {#configuring-blog-sidebar}

When you double-click the `Blog Sidebar` component, an edit dialog opens up.

Auf der Registerkarte **[!UICONTROL Journal-Sidebar-Einstellungen]** können Sie das Datumsformat für Archive festlegen und angeben, welche Eintragstypen in der Seitenleiste aufgeführt werden sollen:

![chlimage_1-151](assets/chlimage_1-151.png)

* **[!UICONTROL Datumsformat]**

   Das Format, das für die Anzeige von Archiven von Blog-Einträgen verwendet wird. In diesem Format finden sich Platzhalter, die der Java-Konvention folgen.

   * JJJJ: lange Jahresangabe, z. B. 2015
   * JJ: kurze Jahresangabe, z. B. 15
   * MMMMM: vollständiger Monat, z. B. Juni
   * MMM: abgekürzter Monat, z. B. Jun
   * MM: Monatszahl, z. B. 06

   Der Standardwert ist &quot;yyyy MMMMM&quot;, der z. B. &quot;Juni 2015&quot;anzeigen würde.

* **[!UICONTROL Ansichtstyp]**

   Titel und Typ der Blog-Einträge, die in der Seitenleiste angezeigt werden sollen. Die können aus folgenden Kategorien wählen:

   * Autoren
   * Kategorien
   * Archive

* **[!UICONTROL Journal-Komponentenpfad]**

   *(Optional)* Der Speicherort der Blog-Ressource, aus der Blog-Artikel aufgelistet werden sollen. Wenn Sie das Feld leer lassen, verwenden Sie die Komponente von resourceType `social/journal/components/hbs/journal` , die auf derselben Seite angezeigt wird.

   * Beispiel: `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **[!UICONTROL Empfehlungsgrenze]**

   Die Anzahl der anzuzeigenden Blog-Artikel. Der Wert -1 bedeutet keine Begrenzung. Der Standardwert ist -1.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung wird bei der Blogfunktion der neueste Blogartikel angezeigt, gefolgt von älteren Einträgen, die absteigend nach Erstellungsdatum sortiert sind. Blog-Seitenleisten ermöglichen es Besuchern der Site, einen Filter anzuwenden, um die Auswahl der anzuzeigenden Artikel einzuschränken.

Dem Blogartikel folgt ein Link, über den Kommentare gelesen oder verfasst werden können.

Wurde ein Blogartikel ausgewählt, werden der Artikel sowie zugehörige Kommentare eingeblendet (falls aktiviert).

Die Verfügbarkeit weiterer Optionen hängt davon ab, ob der Site-Besucher Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonymer Besucher ist.

### Arbeiten mit Artikeln {#working-with-articles}

Wenn Sie einen neuen Blogartikel erstellen, können Sie aus folgenden Optionen wählen:

1. Sofort veröffentlichen
1. Einen Entwurf veröffentlichen
1. An einem geplanten Datum und zu einer geplanten Uhrzeit veröffentlichen

Die Blogartikel erscheinen auf der entsprechenden Registerkarte („Veröffentlicht“, „Entwürfe“ oder „Geplant“) und können von Mitgliedern bei der Veröffentlichung bearbeitet werden.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er [Moderationsaufgaben](moderate-ugc.md) für alle Blogartikel und Komponenten des Blogs durchführen (je nach Berechtigungen durch die Konfiguration der Komponente).

![chlimage_1-152](assets/chlimage_1-152.png)

### Mitglieder {#members}

When the signed in user is a community member or [privileged member](users.md#privileged-members-group) (depending on configuration), they are able to select `New Article` to create and post a new blog article.

Insbesondere können sie

* Erstellen eines neuen Blog-Artikels
* Posten Sie einen neuen Blog-Artikel im Auftrag eines anderen Mitglieds
* Posten eines Kommentars zu einem Blog-Artikel
* Bearbeiten Sie einen eigenen Blog-Artikel oder -Kommentar
* Löschen Sie einen eigenen Blog-Artikel oder -Kommentar
* Markieren von Blog-Artikeln oder -Kommentaren anderer Benutzer

![chlimage_1-153](assets/chlimage_1-153.png) ![chlimage_1-154](assets/chlimage_1-154.png)

### Anonym {#anonymous}

Nicht angemeldete Besucher können veröffentlichte Blogartikel und Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Artikel oder Kommentare hinzufügen und keine Artikel und Kommentare anderer Benutzer kennzeichnen.

![chlimage_1-155](assets/chlimage_1-155.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Blog-Grundlagen](blog-developer-basics.md).

Informationen zur Moderation von Blogartikeln und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von Blogartikeln und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).

Informationen zur Übersetzung von Blogartikeln und Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](translate-ugc.md).
