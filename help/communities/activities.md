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

Die Aktivitäten eines angemeldeten Community-Mitglieds, wie z.B. das Posten in einem Forum oder Blog, werden in einem Stream gesammelt, der durch die Konfiguration der `Activity Streams`-Komponente gefiltert und angezeigt werden kann.

Diese Verfolgungsmöglichkeit bietet eine zusätzliche Art der Aktivitätenansicht, mit der Community-Mitglieder interessanten Beiträgen oder den Aktivitäten anderer Mitglieder folgen können.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Aktivität Streams-Komponente zu einer AEM Site
* Konfigurationseinstellungen für die Aktivität Streams-Komponente

## Hinzufügen von Aktivitäts-Streams zu einer Seite {#adding-activity-streams-to-a-page}

Wenn Sie eine `Activity Streams`-Komponente zu einer Seite im Autorenmodus hinzufügen möchten, verwenden Sie den Komponenten-Browser, um

* `Communities / Activity Streams`

und ziehen Sie die Komponente an die gewünschte Stelle auf einer Seite, auf der Aktivitäts-Streams angezeigt werden sollen.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-activities.md#essentials-for-client-side) einbezogen werden, wird die `Activity Streams`-Komponente wie folgt angezeigt:

![chlimage_1-195](assets/chlimage_1-195.png)

## Konfigurieren von Aktivitäts-Streams {#configuring-activity-streams}

Wählen Sie die platzierte Komponente `Activity Streams` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-196](assets/chlimage_1-196.png)

Auf der Registerkarte **[!UICONTROL Benutzeraktivitäten]** können Sie festlegen, welche Aktivitäten angezeigt werden sollen:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Max. Anzahl der]**
AktivitätenDie Anzahl der anzuzeigenden Aktivitäten
* **[!UICONTROL Stream-Ressourcenpfad]** Feld leer lassen, um standardmäßig auf die Community-Site oder die Community-Gruppe zu verweisen. Mit dem Stream-Ressourcenpfad wird die Aktivitätenquelle festgelegt. Standardmäßig ist das Feld leer.
* **[!UICONTROL Ansicht der Benutzeraktivitäten anzeigen]** Ist diese Option aktiviert, findet sich auf der Aktivitätenseite eine Registerkarte, mit der Aktivitäten nach denjenigen Elementen gefiltert werden können, die vom aktuellen Mitglied innerhalb der Community generiert wurden. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL Alle Aktivitäten anzeigen]**
Wenn aktiviert, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, die alle Aktivitäten enthält, die innerhalb der Community generiert wurden, auf die das aktuelle Mitglied Zugriff hat. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL Anzeige Nach]**
AnsichtWenn aktiviert, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der die Aktivitäten der Filter basieren, denen das aktuelle Mitglied folgt. Diese Option ist standardmäßig aktiviert.

## Nach der Ansicht {#following-view}

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind zulässig: [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendar](calendar.md), [fileLibrary](file-library.md) und [comments](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

Mit der Schaltfläche **Folgen** können Sie Einstiege als Aktivitäten, [Benachrichtigungen](notifications.md) und/oder [Abonnement](subscriptions.md) folgen. Jedes Mal, wenn die Schaltfläche **Folgen** ausgewählt ist, können Sie eine Auswahl ein- oder ausschalten. Die Auswahl `Email Subscriptions` ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, wird der Text der Schaltfläche in **Nach** geändert. Aus praktischen Gründen können Sie `Unfollow All` auswählen, um alle Methoden auszuschalten.

Die Schaltfläche **Folgen** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds
* Auf einer Hauptseite mit Funktionen wie Foren, QnA und Blogs
   * Folgt der gesamten Aktivität für diese allgemeine Funktion

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Beantwortung einer Frage oder einen Blog-Artikel
   * Folgt der gesamten Aktivität für diesen spezifischen Eintrag

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Aktivitäts-Streams-Grundlagen](essentials-activities.md).
