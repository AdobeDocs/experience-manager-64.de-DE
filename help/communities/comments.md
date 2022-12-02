---
title: Verwenden von Kommentaren
seo-title: Using Comments
description: Mit der Kommentarfunktion können angemeldete Site-Besucher ihre Meinungen und ihr Wissen austauschen
seo-description: Comments feature lets signed-in site visitors share their opinions and knowledge
uuid: 30fc48ac-134c-4acb-a65c-398855c93829
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: b074ebfa-2894-4a2d-aa8e-28168049971a
exl-id: 8ad5ce3e-c5dd-48d7-8812-43172eda36cc
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 38%

---

# Verwenden von Kommentaren {#using-comments}

## Einführung {#introduction}

Die Kommentarfunktion ermöglicht es angemeldeten Site-Besuchern (Mitgliedern), ihre Meinung und ihre Kenntnisse bezüglich der Site-Inhalte kundzutun. Diese Funktion ist in der Regel bereits in anderen Funktionen enthalten, kann jedoch auch beliebigen Websites hinzugefügt werden.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen `Comments`zu einer Seite
* Konfigurationseinstellungen für `Comments`component

>[!NOTE]
>
>Das anonyme Posten von Kommentaren wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können.

## Hinzufügen von Kommentaren zu einer Seite {#adding-comments-to-a-page}

So fügen Sie eine `Comments`-Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Comments`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. in die Nähe einer Eigenschaft, die Benutzer kommentieren sollen, oder fügen Sie die Komponente am Ende der Seite ein.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](essentials-comments.md#essentials-for-client-side) eingeschlossen sind, wird die `Comments`wird angezeigt.

![chlimage_1-428](assets/chlimage_1-428.png)

>[!NOTE]
>
>Nur eine `Comments`-Komponente auf einer Seite vorhanden sein. Beachten Sie, dass mehrere Communities-Funktionen bereits Kommentare enthalten, wie z. B. Blog, Kalender, Forum, Fragen und Antworten.

## Konfigurieren von Kommentaren {#configuring-comments}

Wählen Sie die platzierte `Comments` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure.png) ![Kommentareinstellungen](assets/commentssettings.png)

### Registerkarte &quot;Kommentare&quot; {#comments-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Kommentare]** fest, wie Benutzer Kommentare eingeben sollen.

* **[!UICONTROL Antworten zulassen]**

   Ist diese Option aktiviert, können Mitglieder auf vorhandene Kommentare antworten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare pro Seite]**

   Schränkt die Anzahl der pro Seite angezeigten Kommentare sowie die Anzahl der angezeigten Antworten ein. Der Standardwert ist 10.

* **[!UICONTROL Datei-Uploads zulassen]**

   Wenn diese Option aktiviert ist, wird die Option zum Hochladen einer Datei mit dem Texteingabefeld angezeigt. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Max. Dateigröße]**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Dieser Wert begrenzt die Größe der hochgeladenen Datei. Der Standardwert ist 10 MB.

* **[!UICONTROL Maximale Nachrichtenlänge]**

   Maximale Zeichenanzahl, die in das Textfeld eingegeben werden kann. Der Standardwert ist 4096 Zeichen.

* **[!UICONTROL Zulässige Dateitypen]**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, sind nicht angegebene Dateitypen nicht zulässig. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Rich-Text-Editor]**

   Wenn diese Option aktiviert ist, können Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**

   Wenn diese Option aktiviert ist, wird das Texteingabefeld angezeigt. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Folgende zulassen]**

   Wenn diese Option aktiviert ist, können Mitglieder Kommentare folgen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abzeichen anzeigen]**

   Wenn diese Option aktiviert ist, können Sie die Anzeige von verdienten und vergebenen Abzeichen zulassen. Diese Option ist standardmäßig deaktiviert.

### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **[!UICONTROL Benutzermoderation]** Registerkarte angeben, wie die veröffentlichten Kommentare verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

* **[!UICONTROL Vor der Moderation]**

   Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungs-Site angezeigt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare löschen]**

   Wenn diese Option aktiviert ist, kann das Mitglied, das den Kommentar veröffentlicht hat, ihn löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare ablehnen]**

   Wenn diese Option aktiviert ist, können Moderatoren Kommentare ablehnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare schließen/erneut öffnen]**

   Wenn diese Option aktiviert ist, können Moderatoren Kommentare schließen und erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare kennzeichnen]**

   Ist diese Option aktiviert, können Mitglieder Kommentare als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kenn-zeichnungsgründen]**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**

   Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Kommentars als unangemessen eingeben. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**

   Geben Sie an, wie oft ein Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (1).

* **[!UICONTROL Kennzeichnungslimit]**

   Geben Sie an, wie oft ein Kommentar gekennzeichnet werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Dieser Wert muss größer als der oder gleich dem **[!UICONTROL Schwellenwert für Moderation]** sein. Der Standardwert ist 5.

### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

Unter dem **[!UICONTROL Sortiereinstellungen]** festlegen, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **[!UICONTROL Sortierfeld]**

   Ziehen Sie nach unten, um eines von `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`oder `Most Liked`.

* **[!UICONTROL Sortierreihenfolge]**

   Ziehen Sie nach unten, um eines von `Ascending` oder `Descending`.

### Ändern in einen benutzerdefinierten Kommentartyp {#changing-to-a-custom-comment-type}

Durch Änderung des Kommentarressourcentyps generiert das Kommentarsystem nicht mehr mithilfe des Standardsystems eine Instanz eines Kommentars, sondern mithilfe einer Einstellung, die von Entwicklern definiert (erweitert) wurde.

Sobald die benutzerdefinierten Ressourcentypen bekannt sind, geben Sie [Designmodus](../../help/sites-authoring/default-components-designmode.md) und doppelklicken Sie auf die platzierte `Comments` -Komponente, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Unter dem **[!UICONTROL Ressourcentypen]** Registerkarte den benutzerdefinierten resourceType für neue Instanzen der `Comments or Voting`Komponenten:

![chlimage_1-429](assets/chlimage_1-429.png)

* **[!UICONTROL Kommentarressourcentyp]**

   Navigieren Sie zum resourceType eines erweiterten `comment`Komponente (einzelner Kommentar) in /apps. Beispiel: `/apps/social/commons/components/hbs/comments/comment`

   Diese Ressource identifiziert den resourceType des UGC, der erstellt wurde, wenn ein Besucher einen Kommentar veröffentlicht.

* **[!UICONTROL Abstimmungs-Ressourcentyp]**

   Navigieren Sie zum resourceType eines erweiterten `voting`-Komponente in /apps. Beispiel: `/apps/social/components/hbs/voting`

   Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wurde, wenn ein Besucher eine Stimme sendet.

* **[!UICONTROL Ressourcentyp des Kommentars]**

   Navigieren Sie zum resourceType eines erweiterten `comments`-Komponente (Kommentarsystem) in /apps. Leer lassen, es sei denn, die Seitenvorlage [dynamisch enthält](scf.md#add-or-include-a-communities-component) das Kommentar-System im zugrunde liegenden Skript, anstatt als Ressource (Kommentarknoten) zur Seite hinzugefügt zu werden. Weitere Informationen finden Sie unter [{{include}} Helper](handlebars-helpers.md#include).

## Site-Besuchererlebnis {#site-visitor-experience}

### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer den Kommentar verfasst hat.

### Mitglieder {#members}

Abhängig von der Konfiguration können angemeldete Besucher Folgendes tun:

* Posten eines neuen Kommentars
* Bearbeiten eigener Kommentare
* Löschen eigener Kommentare
* Andere Kommentare kennzeichnen

### Anonym {#anonymous}

Nicht registrierte oder angemeldete Besucher können veröffentlichte Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Kommentare hinzufügen und keine Kommentare anderer Benutzer kennzeichnen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen zu Kommentaren](essentials-comments.md) für Entwickler.

Informationen zur Moderation von geposteten Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zur Übersetzung von Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](translate-ugc.md).
