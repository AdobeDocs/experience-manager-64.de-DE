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
exl-id: e62b7c0d-5004-4672-9fdc-566ece2785c9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 32%

---

# Aktivitäts-Streams-Funktion {#activity-streams-feature}

## Einführung {#introduction}

Die Aktivitäten eines angemeldeten Community-Mitglieds, z. B. das Posten in einem Forum oder Blog, werden in einem Stream erfasst, der durch die Konfiguration der `Activity Streams`-Komponente auf verschiedene Weise gefiltert und angezeigt werden kann.

Diese Verfolgungsmöglichkeit bietet eine zusätzliche Art der Aktivitätenansicht, mit der Community-Mitglieder interessanten Beiträgen oder den Aktivitäten anderer Mitglieder folgen können.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Aktivitäts-Streams-Komponente zu einer AEM Site
* Konfigurationseinstellungen für die Komponente &quot;Aktivitäts-Streams&quot;

## Hinzufügen von Aktivitäts-Streams zu einer Seite {#adding-activity-streams-to-a-page}

Wenn Sie im Autorenmodus eine `Activity Streams`-Komponente zu einer Seite hinzufügen möchten, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Activity Streams`

und ziehen Sie die Komponente an die gewünschte Stelle auf einer Seite, auf der Aktivitäts-Streams angezeigt werden sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-activities.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Activity Streams` so angezeigt:

![chlimage_1-195](assets/chlimage_1-195.png)

## Konfigurieren von Aktivitäts-Streams {#configuring-activity-streams}

Wählen Sie die platzierte Komponente `Activity Streams` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-196](assets/chlimage_1-196.png)

Auf der Registerkarte **[!UICONTROL Benutzeraktivitäten]** können Sie festlegen, welche Aktivitäten angezeigt werden sollen:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Maximale Anzahl an]**
AktivitätenDie Anzahl der anzuzeigenden Aktivitäten
* **[!UICONTROL Stream-Ressourcenpfad]** Feld leer lassen, um standardmäßig auf die Community-Site oder die Community-Gruppe zu verweisen. Mit dem Stream-Ressourcenpfad wird die Aktivitätenquelle festgelegt. Standardmäßig ist das Feld leer.
* **[!UICONTROL Ansicht der Benutzeraktivitäten anzeigen]** Ist diese Option aktiviert, findet sich auf der Aktivitätenseite eine Registerkarte, mit der Aktivitäten nach denjenigen Elementen gefiltert werden können, die vom aktuellen Mitglied innerhalb der Community generiert wurden. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL Alle Aktivitäten anzeigen]**
Ist diese Option aktiviert, enthält die Aktivitätsseite eine Registerkarte, die alle Aktivitäten enthält, die innerhalb der Community generiert wurden, auf die das aktuelle Mitglied Zugriff hat. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL Anzeige nach]**
AnsichtIst diese Option aktiviert, enthält die Aktivitätsseite eine Registerkarte, auf der Aktivitäten nach denen gefiltert werden, denen das aktuelle Mitglied folgt. Diese Option ist standardmäßig aktiviert.

## Nach Ansicht {#following-view}

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind möglich: [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendar](calendar.md), [filelibrary](file-library.md) und [comments](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

Die Schaltfläche **Folgen** bietet eine Möglichkeit, Einträgen als Aktivitäten, [Benachrichtigungen](notifications.md) und/oder [Abonnements](subscriptions.md) zu folgen. Jedes Mal, wenn die Schaltfläche **Folgen** ausgewählt wird, können Sie eine Auswahl ein- oder ausschalten. Die Auswahl `Email Subscriptions` ist nur bei Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Nach**. Zur Vereinfachung können Sie `Unfollow All` auswählen, um alle Methoden zu deaktivieren.

Die Schaltfläche **Folgen** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds
* Auf einer Hauptseite mit Funktionen wie Foren, Fragen und Antworten und Blogs
   * Folgt allen Aktivitäten für diese allgemeine Funktion

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blog-Artikel
   * Folgt allen Aktivitäten für diesen spezifischen Eintrag

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Aktivitäts-Streams-Grundlagen](essentials-activities.md).
