---
title: Verwenden der Bewertungszusammenfassung (Anzeige)
seo-title: Using Reviews and Reviews Summary (Display)
description: Hinzufügen der Komponenten "Bewertungszusammenfassung"und "Bewertungszusammenfassung"zu einer Seite
seo-description: Adding the Reviews and Reviews Summary components to a page
uuid: bd1ccee7-b26b-4a27-b1ea-89609f5080af
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bf4e7809-8def-4647-aaa6-3ac36865511f
exl-id: 5aae7744-73cc-472b-a4e6-ecd88284b70c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 2%

---

# Verwenden der Bewertungszusammenfassung (Anzeige) {#using-reviews-and-reviews-summary-display}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die `Reviews`Komponente ist ein Verbund aus [ `Comments`](comments.md) und [ `Rating`](rating.md) gebrauchsfertige Komponenten.

Die `Reviews Summary (Display)` -Komponente bietet eine Zusammenfassung einer aktiven oder geschlossenen Instanz eines `Reviews` -Komponente für die Anzeige an einem anderen Ort der Site.

>[!NOTE]
>
>Das anonyme Posten eines Reviews wird nicht unterstützt. Besucher der Site müssen sich registrieren (Mitglied werden) und sich anmelden, um teilnehmen zu können. Der angemeldete Besucher kann seine Überprüfung jederzeit aktualisieren.

## Hinzufügen einer Überprüfung zu einer Seite {#adding-a-review-to-a-page}

So fügen Sie eine `Reviews` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / Reviews` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position relativ zur Funktion, die Benutzer überprüfen können.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](reviews-basics.md#essentials-for-client-side) eingeschlossen sind, wird die `Reviews`wird angezeigt.

![chlimage_1-340](assets/chlimage_1-340.png)

## Konfigurieren von Überprüfungen {#configuring-reviews}

Wählen Sie die platzierte `Reviews` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-341](assets/chlimage_1-341.png)

Unter dem **[!UICONTROL Zulässige Bewertungen]** -Tab die vollständige Liste der Bewertungen angeben, die den Mitgliedern angezeigt werden sollen. Das erste Rating sollte eine allgemeine/allgemeine Gesamtrating sein, da es das Rating ist, das die durchschnittliche Bewertung für die `Review Summary (Display)` -Komponente. Die nächsten beiden Bewertungen in der Standardkonfiguration sollten einen anderen Titel erhalten als &quot;Unterbewertung 1&quot;oder &quot;Unterbewertung 2&quot;.

![chlimage_1-342](assets/chlimage_1-342.png)

* **[!UICONTROL Zulässige Bewertungen]**

   Eine Liste von Bewertungen, aus denen ein Mitglied wählen kann.

   Verwenden Sie die Schaltflächen nach oben, nach unten und zum Löschen, um die sichtbaren Auswahlen zu ändern.

   Klicken **[!UICONTROL Element hinzufügen]** , um eine weitere Bewertungsoption hinzuzufügen.

Unter dem **[!UICONTROL Erforderliche Bewertungen]** Registerkarte erneut Elemente aus der Liste der **[!UICONTROL Zulässige Bewertungen]** die bewertet werden müssen. Wenn ein Element nur auf der Registerkarte Zulässige Bewertungen angegeben wird, kann es beim Senden durch das Mitglied nicht markiert bleiben.

Auf der Website sind erforderliche Bewertungen mit einem Sternchen gekennzeichnet. Wenn ein Element erforderlich ist und nicht markiert bleibt, wird dem Mitglied eine Nachricht angezeigt und die Übermittlung verweigert, bis alle erforderlichen Bewertungen markiert sind.

![chlimage_1-343](assets/chlimage_1-343.png)

* **[!UICONTROL Erforderliche Bewertungen]**

   Eine Untergruppe zulässiger Ratings, die angibt, welche Ratings erforderlich sind.

   Verwenden Sie die Schaltflächen nach oben, nach unten und zum Löschen, um die sichtbaren Auswahlen zu ändern.

   Klicken **[!UICONTROL Element hinzufügen]** , um eine weitere Antwortoption hinzuzufügen.

>[!NOTE]
>
>Wenn ein Element in der Variablen **[!UICONTROL Erforderliche Bewertungen]** Registerkarte, die nicht im **[!UICONTROL Zulässige Bewertungen]** und dann nicht in den zu bewertenden Elementen enthalten ist.

Unter dem **[!UICONTROL Überprüfungen]** -Registerkarte angeben, wie Überprüfungen verarbeitet werden.

![chlimage_1-344](assets/chlimage_1-344.png)

* **[!UICONTROL Antworten zulassen]**
Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Überprüfungen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Geschlossen]**
Wenn diese Option aktiviert ist, wird die Überprüfung für neue Überprüfungen und Antworten gesperrt. Die Option Standard ist deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]**
Wenn diese Option aktiviert ist, können Dateianlagen für die Überprüfung hochgeladen werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Maximale Dateigröße]**
Nur relevant, wenn **[!UICONTROL Datei-Uploads zulassen]** aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 10 MB.

* **[!UICONTROL Max. Nachrichtenlänge]**
Maximale Zeichenanzahl, die in das Textfeld eingegeben werden kann. Der Standardwert beträgt 4096 Zeichen.

* **[!UICONTROL Zulässige Dateitypen]**
Nur relevant, wenn **[!UICONTROL Datei-Uploads zulassen]** aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, sind nicht angegebene Dateitypen nicht zulässig. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Rich-Text-Editor]**
Wenn diese Option aktiviert ist, können Beiträge mit Markup eingegeben werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**
Wenn diese Option aktiviert ist, nehmen Sie die Abstimmungsfunktion für ein Thema auf. Die Option Standard ist deaktiviert.

Unter dem **[!UICONTROL Benutzermoderation]** Registerkarte angeben, wie die veröffentlichten Reviews verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

![chlimage_1-345](assets/chlimage_1-345.png)

* **[!UICONTROL Vormoderation]**
Wenn diese Option aktiviert ist, müssen Überprüfungen genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Bewertungen löschen]**
Wenn diese Option aktiviert ist, kann das Mitglied, das die Überprüfung veröffentlicht hat, sie löschen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Reviews verweigern]**
Wenn diese Option aktiviert ist, können Moderatoren Bewertungen ablehnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Prüfungen schließen/erneut öffnen]**
Wenn diese Option aktiviert ist, können Moderatoren Bewertungen schließen und erneut öffnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Flag-Reviews]**
Ist diese Option aktiviert, können Mitglieder Bewertungen als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Liste der Kennzeichnungsgründe]**
Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem eine Überprüfung als unangemessen gekennzeichnet wird. Die Option Standard ist deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**
Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund dafür eingeben, warum eine Überprüfung als unangemessen gekennzeichnet wird. Die Option Standard ist deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**
Geben Sie an, wie oft eine Überprüfung von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (1).

* **[!UICONTROL Kennzeichnungslimit]**
Geben Sie an, wie oft eine Überprüfung gekennzeichnet werden muss, bevor sie in der öffentlichen Ansicht ausgeblendet wird. Diese Zahl muss größer oder gleich der **[!UICONTROL Schwellenwert für Moderation]**. Der Standardwert ist 5.

### Hinzufügen einer Bewertungszusammenfassung (Anzeige) zu einer Seite {#adding-a-review-summary-display-to-a-page}

So fügen Sie eine `Reviews Summary (Display)` Komponente auf einer Seite im Autorenmodus zu finden, die Komponente

* `Communities / Reviews Summary (Display)`

und ziehen Sie sie an eine Stelle auf einer Seite, auf der eine Zusammenfassung einer aktiven oder geschlossenen Überprüfung angezeigt werden soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](reviews-basics.md#essentials-for-client-side) eingeschlossen sind, wird die `Reviews Summary (Display)`wird angezeigt.

![chlimage_1-346](assets/chlimage_1-346.png)

>[!NOTE]
>
>Der &quot;Durchschnitt&quot;spiegelt die Stimmen für den ersten Punkt wider, der auf den Registerkarten &quot;Zulässige Bewertungen&quot;der zusammengefassten Überprüfung aufgeführt ist.

### Konfigurieren der Bewertungszusammenfassung (Anzeige) {#configuring-reviews-summary-display}

Wählen Sie die platzierte `Reviews Summary (Display)` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-347](assets/chlimage_1-347.png)

Unter dem **[!UICONTROL Bewertungszusammenfassung]** tab

![chlimage_1-348](assets/chlimage_1-348.png)

* `Review Path`

   die platzierte Instanz der `reviews`-Komponente zusammenfassen, z. B. wenn sie der Webseite der [Geometrixx Engage-Site,](getting-started.md) der Pfad lautet:

   /content/sites/engage/en/page/jcr:content/content/primary/views

* `Include histogram`

   Wenn diese Option aktiviert ist, zeigen Sie ein Balkendiagramm an, das angibt, wie viele Sternbewertungen es in den zusammengefassten Reviews gibt. Die Option Standard ist deaktiviert.

### Ändern zu einem benutzerdefinierten Überprüfungstyp {#changing-to-a-custom-review-type}

Die Komponente &quot;Bewertungen&quot;verwendet das Kommentarsystem.

Durch Änderung des Kommentar-Ressourcentyps generiert das Kommentarsystem nicht mehr eine Instanz eines Kommentars, die standardmäßig verwendet wird, sondern eine, die von Entwicklern angepasst (erweitert) wurde.

Sobald die benutzerdefinierten Ressourcentypen bekannt sind, geben Sie [Designmodus](../../help/sites-authoring/default-components-designmode.md) und doppelklicken Sie auf die platzierte `Comments` -Komponente, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Unter dem **[!UICONTROL Ressourcentypen]** Registerkarte den benutzerdefinierten resourceType für neue Instanzen der `Comments or Voting`Komponenten:

![chlimage_1-349](assets/chlimage_1-349.png)

* **[!UICONTROL Kommentarressourcentyp]**

   Navigieren Sie zum resourceType eines erweiterten `comment`Komponente (einzelner Kommentar) in /apps. Beispiel: `/apps/social/commons/components/hbs/comments/comment`

   Diese Ressource identifiziert den resourceType des UGC, der erstellt wurde, wenn ein Besucher einen Kommentar veröffentlicht.

* **[!UICONTROL Abstimmungs-Ressourcentyp]**

   Navigieren Sie zum resourceType eines erweiterten `voting`-Komponente in /apps. Beispiel: `/apps/social/components/hbs/voting`

   Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wurde, wenn ein Besucher eine Stimme sendet.

* **[!UICONTROL Ressourcentyp des Kommentars]**

   Navigieren Sie zum resourceType eines erweiterten `comments`-Komponente (Kommentarsystem) in /apps. Leer lassen, es sei denn, die Seitenvorlage [dynamisch enthält](scf.md#add-or-include-a-communities-component) das Kommentar-System im zugrunde liegenden Skript, anstatt als Ressource (Kommentarknoten) zur Seite hinzugefügt zu werden. Weitere Informationen finden Sie unter [{{include}} Helper](handlebars-helpers.md#include)

## Site-Besuchererlebnis {#site-visitor-experience}

### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorberechtigungen verfügt, kann er die durch die Konfiguration der Komponente zulässigen Moderationsaufgaben ausführen, unabhängig davon, wer den Review verfasst hat.

### Mitglieder {#members}

Wenn der Besucher der Site angemeldet ist, kann er je nach Konfiguration

* Neuen Review posten
* Bearbeiten einer eigenen Überprüfung
* Löschen einer eigenen Überprüfung
* Anderen Überprüfungskommentaren zuweisen

Pro Mitglied ist nur eine Bewertung zulässig. Das Mitglied kann sein Rating jederzeit ändern.

### Anonym {#anonymous}

Besucher der Website, die nicht angemeldet sind, dürfen veröffentlichte Rezensionen nur lesen, übersetzen, sofern sie unterstützt werden. Sie dürfen jedoch keine Bewertung oder einen Review hinzufügen und auch keine Reviewkommentare anderer Benutzer kennzeichnen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen überprüfen](reviews-basics.md) für Entwickler.

Informationen zur Moderation von geposteten Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zur Übersetzung geposteter Kommentare finden Sie unter [Übersetzen benutzergenerierter Inhalte](translate-ugc.md).
