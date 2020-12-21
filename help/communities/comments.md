---
title: Verwenden von Kommentaren
seo-title: Verwenden von Kommentaren
description: Kommentarfunktion ermöglicht es angemeldeten Site-Besuchern, ihre Meinung und ihr Wissen zu teilen
seo-description: Kommentarfunktion ermöglicht es angemeldeten Site-Besuchern, ihre Meinung und ihr Wissen zu teilen
uuid: 30fc48ac-134c-4acb-a65c-398855c93829
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: b074ebfa-2894-4a2d-aa8e-28168049971a
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 38%

---


# Verwenden von Kommentaren {#using-comments}

## Einführung {#introduction}

Die Kommentarfunktion ermöglicht es angemeldeten Site-Besuchern (Mitgliedern), ihre Meinung und ihre Kenntnisse bezüglich der Site-Inhalte kundzutun. Diese Funktion ist in der Regel bereits in anderen Funktionen enthalten, kann jedoch auch beliebigen Websites hinzugefügt werden.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen von `Comments`zu einer Seite
* Konfigurationseinstellungen für die Komponente `Comments`

>[!NOTE]
>
>Das anonyme Posten von Kommentaren wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können.

## Hinzufügen von Kommentaren zu einer Seite {#adding-comments-to-a-page}

Um einer Seite im Autorenmodus eine `Comments`Komponente hinzuzufügen, suchen Sie im Komponentenbrowser nach

* `Communities / Comments`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. in die Nähe einer Eigenschaft, die Benutzer kommentieren sollen, oder fügen Sie die Komponente am Ende der Seite ein.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-comments.md#essentials-for-client-side) einbezogen werden, wird die `Comments`Komponente so angezeigt.

![chlimage_1-428](assets/chlimage_1-428.png)

>[!NOTE]
>
>Auf einer Seite kann nur eine `Comments`Komponente vorhanden sein. Beachten Sie, dass mehrere Communities-Funktionen bereits Kommentare enthalten, z. B. ein Blog, ein Kalender, ein Forum, eine QnA-Datei und Rezensionen.

## Konfigurieren von Kommentaren {#configuring-comments}

Wählen Sie die platzierte Komponente `Comments` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![](assets/configure.png) ![configuringCommentsSettings](assets/commentssettings.png)

### Kommentar, Registerkarte {#comments-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Kommentare]** fest, wie Benutzer Kommentare eingeben sollen.

* **[!UICONTROL Antworten zulassen]**

   Wenn diese Option aktiviert ist, können Mitglieder auf vorhandene Kommentare antworten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare pro Seite]**

   Begrenzt die Anzahl der pro Seite angezeigten Kommentare sowie die Anzahl der angezeigten Antworten. Der Standardwert ist 10.

* **[!UICONTROL Datei-Uploads zulassen]**

   Wenn diese Option aktiviert ist, wird die Option zum Hochladen einer Datei mit dem Texteingabefeld angezeigt. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Max. Dateigröße]**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Dieser Wert begrenzt die Größe der hochgeladenen Datei. Der Standardwert ist 10 MB.

* **[!UICONTROL Maximale Nachrichtenlänge]**

   Maximale Anzahl von Zeichen, die in das Textfeld eingegeben werden können. Der Standardwert ist 4096 Zeichen.

* **[!UICONTROL Zulässige Dateitypen]**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, sind nicht angegebene Dateitypen nicht zulässig. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **[!UICONTROL Rich-Text-Editor]**

   Wenn diese Option aktiviert ist, können Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**

   Wenn diese Option aktiviert ist, wird das Textfeld zur Eingabe angezeigt. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Folgende zulassen]**

   Wenn diese Option aktiviert ist, können Sie den Mitgliedern Kommentare folgen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abzeichen anzeigen]**

   Wenn diese Option aktiviert ist, lassen Sie die Anzeige von verdienten und zuerkannten Abzeichen zu. Diese Option ist standardmäßig deaktiviert.

### Benutzermoderation, Registerkarte {#user-moderation-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Benutzermoderation]** an, wie die veröffentlichten Kommentare verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Vor der Moderation]**

   Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungssite angezeigt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare löschen]**

   Wenn diese Option aktiviert ist, kann das Mitglied, das den Kommentar veröffentlicht hat, ihn löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare ablehnen]**

   Wenn diese Option aktiviert ist, können Moderatoren Kommentare ablehnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare schließen/erneut öffnen]**

   Wenn diese Option aktiviert ist, können Moderatoren Kommentare schließen und erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare kennzeichnen]**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, Kommentare als unangemessen zu kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kenn-zeichnungsgründen]**

   Wenn diese Option aktiviert ist, können die Mitglieder aus einer Dropdown-Liste auswählen, aus welchem Grund sie einen Kommentar als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, einen eigenen Grund für die Kennzeichnung eines Kommentars als unangemessen einzugeben. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**

   Geben Sie an, wie oft ein Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (1).

* **[!UICONTROL Kennzeichnungslimit]**

   Geben Sie an, wie oft ein Kommentar markiert werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Dieser Wert muss größer als der oder gleich dem **[!UICONTROL Schwellenwert für Moderation]** sein. Der Standardwert ist 5.

### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie unter der Registerkarte **[!UICONTROL Sortiereinstellungen]** an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **[!UICONTROL Sortierfeld]**

   Ziehen Sie nach unten, um eines von `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed` oder `Most Liked` auszuwählen.

* **[!UICONTROL Sortierreihenfolge]**

   Ziehen Sie nach unten, um eines von `Ascending` oder `Descending` auszuwählen.

### Ändern in einen benutzerdefinierten Kommentartyp {#changing-to-a-custom-comment-type}

Durch Änderung des Kommentarressourcentyps generiert das Kommentarsystem nicht mehr mithilfe des Standardsystems eine Instanz eines Kommentars, sondern mithilfe einer Einstellung, die von Entwicklern definiert (erweitert) wurde.

Sobald die benutzerdefinierten Ressourcentypen bekannt sind, geben Sie [Designmodus](../../help/sites-authoring/default-components-designmode.md) ein und klicken Sie mit der Dublette auf die platzierte `Comments`-Komponente, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Geben Sie auf der Registerkarte **[!UICONTROL Ressourcentypen]** den benutzerdefinierten resourceType für neue Instanzen der `Comments or Voting`Komponenten an:

![chlimage_1-429](assets/chlimage_1-429.png)

* **[!UICONTROL Kommentarressourcentyp]**

   Navigieren Sie zum resourceType einer erweiterten `comment`Komponente (einzelner Kommentar) in /apps. Beispiel: `/apps/social/commons/components/hbs/comments/comment`

   Diese Ressource identifiziert den resourceType des UGC, der erstellt wird, wenn ein Besucher einen Kommentar veröffentlicht.

* **[!UICONTROL Abstimmungs-Ressourcentyp]**

   Navigieren Sie zum resourceType einer erweiterten `voting`Komponente in /apps. Beispiel: `/apps/social/components/hbs/voting`

   Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wird, wenn ein Besucher eine Abstimmung veröffentlicht.

* **[!UICONTROL System-Ressourcen-Typ kommentieren]**

   Navigieren Sie zum resourceType einer erweiterten `comments`Komponente (Kommentarsystem) in /apps. Lassen Sie das Feld leer, es sei denn, die Seitenvorlage [enthält dynamisch](scf.md#add-or-include-a-communities-component) das Kommentarsystem im zugrunde liegenden Skript, anstatt der Seite als Ressource (Kommentarknoten) hinzugefügt zu werden. Weitere Informationen erhalten Sie in den Hilfethemen des[{{include}}-Helpers](handlebars-helpers.md#include).

## Site-Besuchererlebnis {#site-visitor-experience}

### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer den Kommentar verfasst hat.

### Mitglieder {#members}

Abhängig von der Konfiguration können angemeldete Besucher Folgendes tun:

* Posten eines neuen Kommentars
* Eigene Kommentare bearbeiten
* eigenen Kommentar löschen
* Kommentare anderer markieren

### Anonym {#anonymous}

Nicht registrierte oder angemeldete Besucher können veröffentlichte Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Kommentare hinzufügen und keine Kommentare anderer Benutzer kennzeichnen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Grundlegende Kommentare](essentials-comments.md) für Entwickler.

Moderation geposteter Kommentare finden Sie unter [Moderieren von benutzergenerierten Inhalten](moderate-ugc.md).

Informationen zur Übersetzung von Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](translate-ugc.md).
