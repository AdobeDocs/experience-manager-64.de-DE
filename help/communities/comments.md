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

* Adding `Comments`to a page
* Configuration settings for the `Comments`component

>[!NOTE]
>
>Das anonyme Posten von Kommentaren wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können.

## Hinzufügen von Kommentaren zu einer Seite {#adding-comments-to-a-page}

To add a `Comments`component to a page in author mode, use the component browser to locate

* `Communities / Comments`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. in die Nähe einer Eigenschaft, die Benutzer kommentieren sollen, oder fügen Sie die Komponente am Ende der Seite ein.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](essentials-comments.md#essentials-for-client-side) are included, this is how the `Comments`component will appear.

![chlimage_1-428](assets/chlimage_1-428.png)

>[!NOTE]
>
>Only one `Comments`component may exist on a page. Beachten Sie, dass mehrere Communities-Funktionen bereits Kommentare enthalten, z. B. ein Blog, ein Kalender, ein Forum, eine QnA-Datei und Rezensionen.

## Konfigurieren von Kommentaren {#configuring-comments}

Select the placed `Comments` component to access and select the `Configure` icon which opens the edit dialog.

![Kommentareinstellungen](assets/configure.png) ![konfigurieren](assets/commentssettings.png)

### Comments tab {#comments-tab}

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

### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Under the **[!UICONTROL User Moderation]** tab, specify how the posted comments are managed. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

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

Geben Sie auf der Registerkarte &quot; **[!UICONTROL Sortiereinstellungen]** &quot;an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **[!UICONTROL Sortierfeld]**

   Ziehen Sie nach unten, um einen von `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`oder `Most Liked`auszuwählen.

* **[!UICONTROL Sortierreihenfolge]**

   Ziehen Sie nach unten, um einen von `Ascending` oder `Descending`auszuwählen.

### Ändern in einen benutzerdefinierten Kommentartyp {#changing-to-a-custom-comment-type}

Durch Änderung des Kommentarressourcentyps generiert das Kommentarsystem nicht mehr mithilfe des Standardsystems eine Instanz eines Kommentars, sondern mithilfe einer Einstellung, die von Entwicklern definiert (erweitert) wurde.

Once the custom resource types is known, enter [Design Mode](../../help/sites-authoring/default-components-designmode.md) and double click on the placed `Comments` component to open a dialog with an additional tab.

Under the **[!UICONTROL Resource Types]** tab, specify the custom resourceType for new instances of the `Comments or Voting`components:

![chlimage_1-429](assets/chlimage_1-429.png)

* **[!UICONTROL Kommentarressourcentyp]**

   Navigieren Sie zum resourceType einer erweiterten `comment`Komponente (ein einzelner Kommentar) in /apps. Beispiel: `/apps/social/commons/components/hbs/comments/comment`

   Diese Ressource identifiziert den resourceType des UGC, der erstellt wird, wenn ein Besucher einen Kommentar veröffentlicht.

* **[!UICONTROL Abstimmungs-Ressourcentyp]**

   Navigieren Sie zum resourceType einer erweiterten `voting`Komponente in /apps. Beispiel: `/apps/social/components/hbs/voting`

   Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wird, wenn ein Besucher eine Abstimmung veröffentlicht.

* **[!UICONTROL System-Ressourcen-Typ kommentieren]**

   Navigieren Sie zum resourceType einer erweiterten `comments`Komponente (Kommentarsystem) in /apps. Leave blank unless the page template [dynamically includes](scf.md#add-or-include-a-communities-component) the Comment System in the underlying script instead of being added to the page as a resource (comments node). Weitere Informationen erhalten Sie in den Hilfethemen des[{{include}}-Helpers](handlebars-helpers.md#include).

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

More information may be found on the [Comments Essentials](essentials-comments.md) page for developers.

For moderation of posted comments, see [Moderating User Generated Content](moderate-ugc.md).

Informationen zur Übersetzung von Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](translate-ugc.md).
