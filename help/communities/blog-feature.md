---
title: Blog-Funktion
seo-title: Blog Feature
description: Community-Informationen im Journalformat
seo-description: Community information in a journaling format
uuid: 01f1a547-d22b-4da6-a69c-ab420e5a9e19
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d5519211-8a04-4699-97bc-e162ec0f3781
exl-id: 12ae8b4c-73c5-4ec9-beea-b682b55ebdfd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1632'
ht-degree: 6%

---

# Blog-Funktion {#blog-feature}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Die Blog-Funktion für AEM Communities wurde von einer Authoring-Aktivität zu einer echten Community-Aktivität, die in der Veröffentlichungsumgebung stattfindet, geändert.

Die Blog-Funktion unterstützt die Bereitstellung von Community-Informationen in einem Journaling-Format. Blogeinträge werden in der Veröffentlichungsumgebung von autorisierten Mitgliedern (registrierten, angemeldeten Benutzern) vorgenommen.

Die Blog-Funktion bietet:

* Publishing-seitige Erstellung von Blogartikeln und Kommentaren
* Rich-Text-Bearbeitung
* Inline-Bilder (mit Drag &amp; Drop-Unterstützung)
* Eingebetteter Inhalt in sozialen Netzwerken ([Einbettungsunterstützung](blog-developer-basics.md#allowing-rich-media))
* Entwurfsmodus
* Geplante Veröffentlichung
* Erstellen Sie im Namen (a [privilegiertes Mitglied](users.md#privileged-members-group) kann Inhalte im Namen eines anderen Community-Mitglieds erstellen)
* [In-Kontext- und Massenmoderation](moderate-ugc.md) von Blogartikeln und Kommentaren

In diesem Abschnitt der Dokumentation wird

* Hinzufügen der Blog-Funktion zu einer AEM Site
* Konfigurationseinstellungen für Blogkomponenten

>[!NOTE]
>
>Die Komponenten `Journal`und `Journal Sidebar` werden `Blog` und `Blog Sidebar`.
>
>Die Blogfunktion in AEM 6.0 und früheren Versionen wurde entfernt. Sie basierte auf einer Vorlage und erlaubte es Autoren nur, Inhalte in der Autorenumgebung zu erstellen.

## Hinzufügen von Blog-Komponenten zu einer Seite {#adding-blog-components-to-a-page}

Wenn Sie im Autorenmodus einen Blog zu einer Seite hinzufügen möchten, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Blog`
* `Communities / Blog Sidebar`

Ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der der Blog erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](blog-developer-basics.md#essentials-for-client-side) eingeschlossen sind, wird die `Blog`wird angezeigt:

![chlimage_1-147](assets/chlimage_1-147.png)

Und wie die `Blog Sidebar` wird angezeigt:

![chlimage_1-148](assets/chlimage_1-148.png)

### Blog konfigurieren {#configuring-blog}

Wählen Sie die platzierte `Blog` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![Symbol zum Konfigurieren](assets/chlimage_1-149.png) ![Blog-Einstellungen](assets/Blog-configure.png)

#### Registerkarte Einstellungen {#settings-tab}

Unter dem **[!UICONTROL Einstellungen]** -Registerkarte die grundlegenden Funktionen des Blogs festlegen:

* **[!UICONTROL Miniaturansicht des Anhangs zulassen]**
Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **[!UICONTROL Maximale Größe der Miniaturansichten anhängen]**
Maximale Größe (in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **[!UICONTROL Mindestbildgröße für Miniaturansichten]**
Mindestgröße (in Byte) des Bildes zum Generieren von Miniaturansichten für Inline-Bilder. Der Standardwert ist 100000 Bytes (100 KB).

* **[!UICONTROL Maximale Größe der Miniaturansichten]**
Maximale Größe (in Pixel) des Miniaturbilds für Inline-Bilder. Der Standardwert ist 800 x 800.

* **[!UICONTROL Zulassen von berechtigten Mitgliedern]**
Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **[!UICONTROL Zugelassene berechtigte Mitglieder]**
Fügen Sie die berechtigten Mitglieder hinzu, die Inhalte erstellen dürfen.

* **[!UICONTROL Vom Benutzer generierte Inhalte im Bearbeitungsmodus des Autors blockieren]**
Wenn diese Option aktiviert ist, wird benutzergenerierter Inhalt bei der Bearbeitung im Autorenmodus blockiert.

* **[!UICONTROL Journaltitel]**
Der Blogtitel, der auf der Seite angezeigt werden soll.
   >Hinweis:
   >Der Journaltitel wird verwendet, um automatisch eine URL für den Blog zu erstellen. Maximal 50 Zeichen (mit 5 zusätzlichen Zeichen für Eindeutigkeit) werden aus dem hier angegebenen Journaltitel verwendet, um eine URL für den Blog zu erstellen.

* **[!UICONTROL Journalbeschreibung]**
Die Blogbeschreibung.

* **[!UICONTROL Themen pro Seite]**

   Definiert die Anzahl der Blogeinträge/Kommentare, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **[!UICONTROL Moderiert]**

   Wenn diese Option aktiviert ist, muss das Posten von Blogeinträgen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Geschlossen]**

   Wenn diese Option aktiviert ist, ist der Blog für neue Blog-Einträge und Kommentare geschlossen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Rich-Text-Editor]**

   Wenn diese Option aktiviert ist, können Blogeinträge und Kommentare mit Markup eingegeben werden. Die Option Standard ist aktiviert.

* **[!UICONTROL Tagging zulassen]**

   Wenn diese Option aktiviert ist, können Mitglieder ihrem Beitrag Tag-Beschriftungen hinzufügen (siehe **[!UICONTROL Tag-Feld]** Registerkarte). Die Option Standard ist deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]**

   Wenn diese Option aktiviert ist, können Sie einem Blogeintrag oder Kommentar Dateianlagen hinzufügen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Max. Dateigröße]**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe einer hochgeladenen Datei (in Byte). Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Zulässige Dateitypen]**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, dürfen nicht angegebene nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Maximale Dateigröße für Bildanhang]**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Maximale Anzahl der Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **[!UICONTROL Antworten zulassen]**

   Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die auf den Blogeintrag gepostet wurden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Benutzern das Löschen von Anmerkungen und Themen ermöglichen]**

   Wenn diese Option aktiviert ist, können Mitglieder die Kommentare und Blogeinträge löschen, die sie veröffentlicht haben. Die Option Standard ist deaktiviert.

* **[!UICONTROL Folgende zulassen]**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder [benachrichtigt](notifications.md) von neuen Stellen. Die Option Standard ist deaktiviert.

* **[!UICONTROL E-Mail-Abonnements zulassen]**

   Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge informiert werden ([Abonnement](subscriptions.md)). Erfordert `Allow Following` zu überprüfen und [E-Mail konfiguriert](email.md). Die Option Standard ist deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**

   Wenn diese Option aktiviert ist, fügen Sie die Funktion Abstimmung in einen Blogeintrag ein. Die Option Standard ist deaktiviert.

* **[!UICONTROL Abzeichen anzeigen]**

   Wenn diese Option aktiviert ist, zeigen Sie Earned und Assored [Badges](implementing-scoring.md) mit dem Blogeintrag eines Mitglieds. Die Option Standard ist deaktiviert.

* **[!UICONTROL Feature-Inhalt zulassen]**

   Wenn diese Option aktiviert ist, kann die Idee als [präsentierte Inhalte](featured.md). Die Option Standard ist deaktiviert.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **[!UICONTROL Benutzermoderation]** -Tab, geben Sie die Moderationseinstellungen an:

* **[!UICONTROL Posts ablehnen]**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Die Option Standard ist deaktiviert.

* **[!UICONTROL Themen schließen/erneut öffnen]**

   Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Thema möglicherweise erneut öffnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Posts kennzeichnen]**

   Wenn diese Option aktiviert ist, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Liste mit Kenn-zeichnungsgründen]**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Themen oder Kommentare als unangemessen gekennzeichnet werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**

   Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**

   Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **[!UICONTROL Kennzeichnungslimit]**

   Geben Sie an, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Wenn der Wert auf -1 festgelegt ist, wird das gekennzeichnete Thema oder der Kommentar nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für Moderation sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Unter dem **[!UICONTROL Tag-Feld]** -Registerkarte angeben, welche Tags bei **[!UICONTROL Tagging zulassen]** wird auf der Seite **[!UICONTROL Einstellungen]** tab:

* **[!UICONTROL Zugelassene Namespaces]**

   Relevant, wenn `Allow Tagging` wird unter dem **[!UICONTROL Einstellungen]** Registerkarte. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Der Standardwert ist &quot;none&quot;, was bedeutet, dass alle Namespaces zulässig sind.

* **[!UICONTROL Empfehlungsgrenze]**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert -1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

### Konfigurieren der Blog-Seitenleiste {#configuring-blog-sidebar}

Wenn Sie auf die `Blog Sidebar` -Komponente ein Dialogfeld zum Bearbeiten geöffnet.

Unter dem **[!UICONTROL Journal-Seitenleisten-Einstellungen]** -Registerkarte das Datumsformat für Archive festlegen und angeben, welche Art von Einträgen in der Seitenleiste angezeigt werden sollen:

![chlimage_1-151](assets/chlimage_1-151.png)

* **[!UICONTROL Datumsformat]**

   Das Format, das für die Anzeige von Archiven von Blogeinträgen verwendet wird. Das Format verwendet Platzhalter, die der Java-Konvention folgen.

   * jjjj: vollständiges Jahr, z. B. &quot;2015&quot;
   * yy: kurze Jahreszahl, z. B. &quot;15&quot;
   * MMMMM: Vollmonat, z. B. Juni
   * MMM: kurzen Monat, wie Jun
   * MM: Monatsnummer, z. B. 06

   Der Standardwert ist &quot;jjjj MMMMM&quot;, der beispielsweise &quot;Juni 2015&quot;anzeigen würde.

* **[!UICONTROL Ansichtstyp]**

   Der Titel und der Typ der Blogeinträge, die in der Seitenleiste angezeigt werden sollen. Die Wahl liegt zwischen

   * Autoren
   * Kategorien
   * Archive

* **[!UICONTROL Journal-Komponentenpfad]**

   *(Optional)* Der Speicherort der Blog-Ressource, von der aus Blog-Artikel aufgelistet werden sollen. Wenn das Feld leer gelassen wird, wird die Komponente von resourceType verwendet. `social/journal/components/hbs/journal` wird auf derselben Seite angezeigt.

   * Beispiel: `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **[!UICONTROL Empfehlungsgrenze]**

   Die Anzahl der anzuzeigenden Blogartikel. Der Wert -1 bedeutet keine Begrenzung. Der Standardwert ist -1.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung zeigt die Blogfunktion den neuesten Blogartikel gefolgt von älteren Blogartikeln in absteigender Reihenfolge der Erstellung an. Blog-Seitenleisten ermöglichen es Site-Besuchern, Filter anzuwenden, um die Auswahl der angezeigten Blog-Artikel zu beschränken.

Dem Blogartikel folgt ein Link zum Posten oder Anzeigen von Kommentaren.

Wenn ein Blogartikel ausgewählt ist, werden der Blogartikel und die Kommentare angezeigt (sofern aktiviert).

Andere Möglichkeiten hängen davon ab, ob der Besucher der Site Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonym ist.

### Arbeiten mit Artikeln {#working-with-articles}

Beim Erstellen eines neuen Blogartikels haben Sie die Wahl zwischen

1. Sofort veröffentlichen
1. Entwurf veröffentlichen
1. An einem geplanten Datum und zu einer geplanten Uhrzeit veröffentlichen

Die Blogartikel werden auf der entsprechenden Registerkarte (Veröffentlicht, Entwürfe oder Geplant) für Mitglieder angezeigt, die in der Lage sind, sie in der Veröffentlichung zu erstellen.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorberechtigungen verfügt, kann er [Moderationsaufgaben](moderate-ugc.md) (wie durch die Konfiguration der Komponente erlaubt) auf allen Blogartikeln und Kommentaren, die in einem Blog veröffentlicht werden.

![chlimage_1-152](assets/chlimage_1-152.png)

### Mitglieder {#members}

Wenn der angemeldete Benutzer Community-Mitglied ist oder [privilegiertes Mitglied](users.md#privileged-members-group) (je nach Konfiguration) können sie `New Article` , um einen neuen Blogartikel zu erstellen und zu posten.

Insbesondere können sie:

* Erstellen eines neuen Blogartikels
* Posten eines neuen Blogartikels im Namen eines anderen Mitglieds
* Posten eines Kommentars zu einem Blogartikel
* Bearbeiten eigener Blogartikel oder Kommentare
* Löschen eigener Blogartikel oder Kommentare
* Kennzeichnen von Blogartikeln oder -kommentaren anderer Benutzer

![chlimage_1-153](assets/chlimage_1-153.png) ![chlimage_1-154](assets/chlimage_1-154.png)

### Anonym {#anonymous}

Besucher der Website, die nicht angemeldet sind, dürfen nur veröffentlichte Blogartikel und Kommentare lesen, sie übersetzen, falls unterstützt, aber keine Blog-Artikel oder -Kommentare hinzufügen oder die Artikel oder Kommentare anderer kennzeichnen.

![chlimage_1-155](assets/chlimage_1-155.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Blog-Grundlagen](blog-developer-basics.md) für Entwickler.

Informationen zur Moderation von Blogeinträgen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von Blogeinträgen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).

Informationen zur Übersetzung von Blogeinträgen und Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](translate-ugc.md).
