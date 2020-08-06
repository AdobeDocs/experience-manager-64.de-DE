---
title: Aktivitäts-Streams-Funktion
seo-title: Aktivitäts-Streams-Funktion
description: Aktivitäten eines angemeldeten Community-Mitglieds
seo-description: Aktivitäten eines angemeldeten Community-Mitglieds
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 32%

---


# Aktivitäts-Streams-Funktion {#activity-streams-feature}

## Einführung {#introduction}

The activities of a signed in community member, such as posting to a forum or blog, are collected into a stream which may be filtered and displayed in various ways through configuration of the `Activity Streams` component.

Diese Verfolgungsmöglichkeit bietet eine zusätzliche Art der Aktivitätenansicht, mit der Community-Mitglieder interessanten Beiträgen oder den Aktivitäten anderer Mitglieder folgen können.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Aktivität Streams-Komponente zu einer AEM Site
* Konfigurationseinstellungen für die Aktivität Streams-Komponente

## Hinzufügen von Aktivitäts-Streams zu einer Seite {#adding-activity-streams-to-a-page}

If it is desired to add an `Activity Streams` component to a page in author mode, use the component browser to locate

* `Communities / Activity Streams`

und ziehen Sie die Komponente an die gewünschte Stelle auf einer Seite, auf der Aktivitäts-Streams angezeigt werden sollen.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](essentials-activities.md#essentials-for-client-side) are included, this is how the `Activity Streams` component will appear:

![chlimage_1-195](assets/chlimage_1-195.png)

## Konfigurieren von Aktivitäts-Streams {#configuring-activity-streams}

Select the placed `Activity Streams` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-196](assets/chlimage_1-196.png)

Auf der Registerkarte **[!UICONTROL Benutzeraktivitäten]** können Sie festlegen, welche Aktivitäten angezeigt werden sollen:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Max. Anzahl der Aktivitäten]** Die Anzahl der anzuzeigenden Aktivitäten
* **[!UICONTROL Stream-Ressourcenpfad]** Feld leer lassen, um standardmäßig auf die Community-Site oder die Community-Gruppe zu verweisen. Mit dem Stream-Ressourcenpfad wird die Aktivitätenquelle festgelegt. Standardmäßig ist das Feld leer.
* **[!UICONTROL Ansicht der Benutzeraktivitäten anzeigen]** Ist diese Option aktiviert, findet sich auf der Aktivitätenseite eine Registerkarte, mit der Aktivitäten nach denjenigen Elementen gefiltert werden können, die vom aktuellen Mitglied innerhalb der Community generiert wurden. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL Ansicht]**&quot;Alle Aktivitäten anzeigen&quot;Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, die alle Aktivitäten enthält, die innerhalb der Community generiert wurden, auf die das aktuelle Mitglied Zugriff hat. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL Anzeige Nach Ansicht]** Wenn aktiviert, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der die Aktivitäten der Filter basierend auf denen des aktuellen Mitglieds folgen. Diese Option ist standardmäßig aktiviert.

## FOLGENDE Ansicht {#following-view}

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind zulässig: [Blog](blog-feature.md), [Forum](forum.md), [QnA](working-with-qna.md), [Kalender](calendar.md), [Dateibibliothek](file-library.md)[](comments.md)undKommentare.

![chlimage_1-198](assets/chlimage_1-198.png)

Über die Schaltfläche **Folgen** können Sie Einsendungen als Aktivitäten, [Benachrichtigungen](notifications.md)und/oder [Abonnements](subscriptions.md)folgen. Bei jeder Auswahl der Schaltfläche &quot; **Folgen** &quot;können Sie eine Auswahl ein- oder ausschalten. Die `Email Subscriptions` Auswahl ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, wird der Text der Schaltfläche in **Folgendem** geändert. Aus praktischen Gründen ist es möglich, alle Methoden `Unfollow All` zu deaktivieren.

Die Schaltfläche &quot; **Folgen** &quot;wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds
* Auf einer Hauptseite mit Funktionen wie Foren, QnA und Blogs
   * Folgt der gesamten Aktivität für diese allgemeine Funktion

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Beantwortung einer Frage oder einen Blog-Artikel
   * Folgt der gesamten Aktivität für diesen spezifischen Eintrag

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Aktivitäts-Streams-Grundlagen](essentials-activities.md).
