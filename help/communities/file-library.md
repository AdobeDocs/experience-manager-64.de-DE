---
title: Dateibibliothek-Funktion
seo-title: File Library Feature
description: Mit der Funktion "Dateibibliothek"können angemeldete Site-Besucher Dateien hochladen, verwalten und herunterladen
seo-description: The File Library feature lets signed-in site visitors upload, manage, and download files
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
exl-id: c72b246d-442e-4841-810d-1045e83f60f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 3%

---

# Dateibibliothek-Funktion {#file-library-feature}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Die Dateibibliotheksfunktion bietet angemeldeten Site-Besuchern (Community-Mitgliedern) die Möglichkeit, Dateien innerhalb der Community-Site hochzuladen, zu verwalten und herunterzuladen.

In diesem Abschnitt der Dokumentation wird

* Hinzufügen der Dateibibliotheksfunktion zu einer AEM Site
* Konfigurationseinstellungen für `File Library` component

## Hinzufügen einer Dateibibliothek zu einer Seite {#adding-a-file-library-to-a-page}

So fügen Sie eine `File Library` Komponente auf einer Seite im Autorenmodus zu finden, die Komponente

* `Communities / File Library`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](essentials-file-library.md#essentials-for-client-side) eingeschlossen sind, wird die `File Library` wird angezeigt:

![chlimage_1-430](assets/chlimage_1-430.png)

## Dateibibliothek konfigurieren {#configuring-file-library}

Wählen Sie die platzierte `File Library` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Registerkarte &quot;Kommentare&quot; {#comments-tab}

Unter dem **[!UICONTROL Kommentare]** -Registerkarte angeben, ob und wie Kommentare für hochgeladene Dateien angezeigt werden:

* **[!UICONTROL Kommentare zu Dateien zulassen]**
Wenn diese Option aktiviert ist, lassen Sie Kommentare zu hochgeladenen Dateien zu. Die Option Standard ist deaktiviert.

* **[!UICONTROL Kommentare pro Seite]**
Schränkt die Anzahl der pro Seite angezeigten Kommentare sowie die Anzahl der angezeigten Antworten ein. Der Standardwert ist 
**10**.

* **[!UICONTROL Maximale Dateigröße]**
Dieser Wert begrenzt die Größe der hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **[!UICONTROL Max. Nachrichtenlänge]**
Maximale Zeichenanzahl, die in das Textfeld eingegeben werden kann. Der Standardwert beträgt 4096 Zeichen.

* **[!UICONTROL Zulässige Dateitypen]**
Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, sind nicht angegebene Dateitypen nicht zulässig. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **[!UICONTROL Rich-Text-Editor]**
Wenn diese Option aktiviert ist, können Kommentare mit Markup eingegeben werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Kommentare löschen]**
Wenn diese Option aktiviert ist, können Benutzer ihre eigenen Kommentare löschen. Die Option Standard ist aktiviert.

* **[!UICONTROL Tagging zulassen]**
Wenn diese Option aktiviert ist, wird die Möglichkeit zum Hinzufügen eines Tags zur Datei aktiviert. Die Option Standard ist deaktiviert.

* **[!UICONTROL Zulässige Namespaces]**
Wenn die Option Tagging zulassen aktiviert ist, sind die verfügbaren Tags auf die aktivierten Namespaces beschränkt. Wenn keines aktiviert ist, sind alle zulässig. Der Standardwert ist alle Namespaces.

* **[!UICONTROL Empfehlungslimit]**
Wenn die Option Tagging zulassen aktiviert ist, beschränkt diese Einstellung die Anzahl der vorgeschlagenen Tags, die angezeigt werden sollen. Wenn auf -1 gesetzt, gibt es keine Begrenzung. Der Standardwert ist -1.

* **[!UICONTROL Abstimmung zulassen]**
Wenn diese Option aktiviert ist, wird die Möglichkeit zur Auswahl einer Datei aktiviert. Die Option Standard ist deaktiviert.

* **[!UICONTROL Folgende erlauben]**
Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder [benachrichtigt](notifications.md) von neuen Stellen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Threaded-Antworten zulassen]**
Ist diese Option aktiviert, können Antworten auf gepostete Kommentare zugelassen werden. Die Option Standard ist deaktiviert.

### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **[!UICONTROL Benutzermoderation]** -Tab konfigurieren Sie die Moderation von Kommentaren, falls Kommentare zulässig sind:

* **[!UICONTROL Vormoderation]**
Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungs-Site angezeigt werden. Die Option Standard ist deaktiviert.

* **[!UICONTROL Kommentare löschen]**
Wenn diese Option aktiviert ist, kann der Besucher, der den Kommentar veröffentlicht hat, ihn löschen. Die Option Standard ist aktiviert.

* **[!UICONTROL Kommentare ablehnen]**
Ist diese Option aktiviert, können Moderatoren vertrauenswürdiger Mitglieder Kommentare ablehnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Kommentare schließen/erneut öffnen]**
Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Kommentare schließen und erneut öffnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Kommentare kennzeichnen]**
Ist diese Option aktiviert, können Besucher Kommentare als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **[!UICONTROL Liste der Kennzeichnungsgründe]**
Wenn diese Option aktiviert ist, können Besucher aus einer Dropdown-Liste den Grund auswählen, aus dem ein Kommentar als unangemessen gekennzeichnet wird. Die Option Standard ist deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**
Wenn diese Option aktiviert ist, können Besucher einen eigenen Grund für die Kennzeichnung eines Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**
Geben Sie an, wie oft ein Kommentar von Besuchern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (
**1**).

* **[!UICONTROL Kennzeichnungslimit]**
Geben Sie an, wie oft ein Kommentar gekennzeichnet werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Diese Zahl muss größer oder gleich der 
**Schwellenwert für Moderation**. Der Standardwert ist 5.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen zur Dateibibliothek](essentials-file-library.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](tag-ugc.md).
