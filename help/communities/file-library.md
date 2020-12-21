---
title: Dateibibliothek
seo-title: Dateibibliothek
description: Mit der Funktion "Dateibibliothek"können angemeldete Site-Besucher Dateien hochladen, verwalten und herunterladen
seo-description: Mit der Funktion "Dateibibliothek"können angemeldete Site-Besucher Dateien hochladen, verwalten und herunterladen
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 68%

---


# Dateibibliothek {#file-library-feature}

## Einführung {#introduction}

Mithilfe der Dateibibliothek können angemeldete Besucher der Site (Community-Mitglieder) Dateien auf die Community-Site hochladen, sie dort verwalten oder von dort herunterladen.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Dateibibliotheksfunktion zu einer AEM
* Konfigurationseinstellungen für die Komponente `File Library`

## Hinzufügen einer Dateibibliothek zu einer Seite {#adding-a-file-library-to-a-page}

Um eine `File Library`-Komponente zu einer Seite im Autorenmodus hinzuzufügen, suchen Sie die Komponente

* `Communities / File Library`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-file-library.md#essentials-for-client-side) einbezogen werden, wird die `File Library`-Komponente wie folgt angezeigt:

![chlimage_1-430](assets/chlimage_1-430.png)

## Konfigurieren der Dateibibliothek {#configuring-file-library}

Wählen Sie die platzierte Komponente `File Library` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Kommentar, Registerkarte {#comments-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Kommentare]** fest, ob und wie Kommentare zu hochgeladenen Dateien angezeigt werden:

* **[!UICONTROL Kommentare in Dateien zulassen]** Ist diese Option aktiviert, werden Kommentare zu hochgeladenen Dateien zugelassen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare pro Seite]** Mit dieser Option wird die Anzahl der Kommentare und Antworten beschränkt, die pro Seite angezeigt werden. Der Standardwert ist 
**10**.

* **[!UICONTROL Max. Dateigröße]** Dieser Wert beschränkt die Größe der hochgeladenen Datei. Die Standardbeschränkung ist 104857600 (10 MB).

* **[!UICONTROL Maximale Nachrichtenlänge]** Die Anzahl der Zeichen, die in das Textfeld eingegeben werden kann. Der Standardwert ist 4096 Zeichen.

* **[!UICONTROL Zulässige Dateitypen]** Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **[!UICONTROL Rich-Text-Editor]** Ist diese Option aktiviert, können Kommentare mit Markup versehen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Löschen von]**
KommentarenWenn diese Option aktiviert ist, können Benutzer ihre eigenen Kommentare löschen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Tagging zulassen]** Ist diese Option aktiviert, können Dateien Kennzeichnungen zugewiesen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulässige]**
NamespacesWenn Tagging zulassen aktiviert ist, sind die verfügbaren Tags auf die aktivierten Namensraum beschränkt. Wenn keine aktiviert ist, sind alle zulässig. In der Standardeinstellung werden alle Namespaces zugelassen.

* **[!UICONTROL Empfehlungsgrenze]** Ist die Option „Tagging zulassen“ aktiviert, wird mit dieser Einstellung die Anzahl der vorgeschlagenen Tags eingegrenzt. Wurde der Wert „-1“ festgelegt, werden beliebig viele Tags eingeblendet. Der Standardwert ist -1.

* **[!UICONTROL &quot;]**
Abstimmung zulassen&quot;Wenn diese Option aktiviert ist, wird die Möglichkeit zur Auswahl einer Datei aktiviert. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen von]**
FolgendemWenn aktiviert, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder über neue Beiträge  [](notifications.md) benachrichtigt werden können. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Threaded]**
Replies zulassenWenn aktiviert, erlauben Sie Antworten auf gepostete Kommentare. Diese Option ist standardmäßig deaktiviert.

### Benutzermoderation, Registerkarte {#user-moderation-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Benutzermoderation]** fest, wie Kommentare moderiert werden sollen, falls diese zugelassen sind:

* **[!UICONTROL Vor der Moderation]** Ist diese Option aktiviert, müssen Kommentare vor ihrer Veröffentlichung zunächst genehmigt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare löschen]** Ist diese Option aktiviert, kann der Besucher, der den Kommentar veröffentlicht hat, diesen auch wieder löschen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Kommentare ablehnen]** Ist diese Option aktiviert, können ausgewählte Mitglieder Kommentare ablehnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare schließen/erneut öffnen]** Ist diese Option aktiviert, können ausgewählte Mitglieder Kommentare schließen oder erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare kennzeichnen]** Ist diese Option aktiviert, können Besucher Kommentare als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kennzeichnungsgründen]** Ist diese Option aktiviert, können Besucher aus einer Dropdown-Liste den Grund auswählen, aus dem ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]** Ist diese Option aktiviert, können Besucher einen eigenen Grund dafür eingeben, warum sie Kommentare als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]** Geben Sie an, wie oft ein Kommentar von Besuchern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (
**1**).

* **[!UICONTROL Kennzeichnungslimit]** Geben Sie an, wie oft ein Kommentar als unangemessen gekennzeichnet werden muss, bevor er aus dem öffentlichen Bereich ausgeblendet wird. Diese Zahl muss größer als oder gleich dem Wert 
**Schwellenwert für Moderation**. Der Standardwert ist 5.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Essentials zur Dateibibliothek](essentials-file-library.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).
