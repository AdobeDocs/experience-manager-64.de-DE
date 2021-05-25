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
exl-id: c72b246d-442e-4841-810d-1045e83f60f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 68%

---

# Dateibibliothek {#file-library-feature}

## Einführung {#introduction}

Mithilfe der Dateibibliothek können angemeldete Besucher der Site (Community-Mitglieder) Dateien auf die Community-Site hochladen, sie dort verwalten oder von dort herunterladen.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Dateibibliotheksfunktion zu einer AEM Site
* Konfigurationseinstellungen für die Komponente `File Library`

## Hinzufügen einer Dateibibliothek zu einer Seite {#adding-a-file-library-to-a-page}

Um eine `File Library`-Komponente zu einer Seite im Autorenmodus hinzuzufügen, suchen Sie die Komponente

* `Communities / File Library`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-file-library.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `File Library` so angezeigt:

![chlimage_1-430](assets/chlimage_1-430.png)

## Konfigurieren der Dateibibliothek {#configuring-file-library}

Wählen Sie die platzierte Komponente `File Library` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Registerkarte &quot;Kommentare&quot;{#comments-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Kommentare]** fest, ob und wie Kommentare zu hochgeladenen Dateien angezeigt werden:

* **[!UICONTROL Kommentare in Dateien zulassen]** Ist diese Option aktiviert, werden Kommentare zu hochgeladenen Dateien zugelassen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare pro Seite]** Mit dieser Option wird die Anzahl der Kommentare und Antworten beschränkt, die pro Seite angezeigt werden. Der Standardwert ist 
**10**.

* **[!UICONTROL Max. Dateigröße]** Dieser Wert beschränkt die Größe der hochgeladenen Datei. Die Standardbeschränkung ist 104857600 (10 MB).

* **[!UICONTROL Maximale Nachrichtenlänge]** Die Anzahl der Zeichen, die in das Textfeld eingegeben werden kann. Der Standardwert ist 4096 Zeichen.

* **[!UICONTROL Zulässige Dateitypen]** Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Rich-Text-Editor]** Ist diese Option aktiviert, können Kommentare mit Markup versehen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Kommentare löschen]**
Ist diese Option aktiviert, können Benutzer eigene Kommentare löschen. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Tagging zulassen]** Ist diese Option aktiviert, können Dateien Kennzeichnungen zugewiesen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulässige]**
NamespacesWenn die Option Tagging zulassen aktiviert ist, sind die verfügbaren Tags auf die aktivierten Namespaces beschränkt. Wenn keines aktiviert ist, sind alle zulässig. In der Standardeinstellung werden alle Namespaces zugelassen.

* **[!UICONTROL Empfehlungsgrenze]** Ist die Option „Tagging zulassen“ aktiviert, wird mit dieser Einstellung die Anzahl der vorgeschlagenen Tags eingegrenzt. Wurde der Wert „-1“ festgelegt, werden beliebig viele Tags eingeblendet. Der Standardwert ist -1.

* **[!UICONTROL Abstimmung zulassen]**
Ist diese Option aktiviert, wird die Möglichkeit zur Auswahl einer Datei aktiviert. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zulassen]**
Folgende Funktion ist aktiviert. Fügen Sie die folgende Funktion für Blogartikel hinzu, damit Mitglieder über neue Beiträge  [](notifications.md) benachrichtigt werden können. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Threaded]**
Replies zulassenIst diese Option aktiviert, können Antworten auf gepostete Kommentare zugelassen werden. Diese Option ist standardmäßig deaktiviert.

### Registerkarte Benutzermoderation {#user-moderation-tab}

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

* **[!UICONTROL Kennzeichnungslimit]** Geben Sie an, wie oft ein Kommentar als unangemessen gekennzeichnet werden muss, bevor er aus dem öffentlichen Bereich ausgeblendet wird. Diese Zahl muss größer oder gleich der 
**Schwellenwert für Moderation**. Der Standardwert ist 5.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Dateibibliothek-Grundlagen](essentials-file-library.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).
