---
title: Aktivitäts-Streams-Funktion
seo-title: Activity Streams Feature
description: Aktivitäten eines angemeldeten Community-Mitglieds
seo-description: Activities of a signed-in community member
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
exl-id: e62b7c0d-5004-4672-9fdc-566ece2785c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 3%

---

# Aktivitäts-Streams-Funktion {#activity-streams-feature}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Die Aktivitäten eines angemeldeten Community-Mitglieds, wie das Posten in einem Forum oder Blog, werden in einem Stream erfasst, der durch die Konfiguration der `Activity Streams` -Komponente.

Die Möglichkeit, zu folgen, bietet eine weitere Ansicht der Aktivitäten, wenn Community-Mitglieder Beiträge von Interesse verfolgen oder den Aktivitäten anderer Community-Mitglieder folgen.

In diesem Abschnitt der Dokumentation wird

* Hinzufügen der Aktivitäts-Streams-Komponente zu einer AEM Site
* Konfigurationseinstellungen für die Komponente &quot;Aktivitäts-Streams&quot;

## Hinzufügen von Aktivitäts-Streams zu einer Seite {#adding-activity-streams-to-a-page}

Wenn Sie eine `Activity Streams` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Activity Streams`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der Aktivitäts-Streams angezeigt werden sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](essentials-activities.md#essentials-for-client-side) eingeschlossen sind, wird die `Activity Streams` wird angezeigt:

![chlimage_1-195](assets/chlimage_1-195.png)

## Konfigurieren von Aktivitäts-Streams {#configuring-activity-streams}

Wählen Sie die platzierte `Activity Streams` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-196](assets/chlimage_1-196.png)

Unter dem **[!UICONTROL Benutzeraktivitäten]** angeben, welche Aktivitäten angezeigt werden sollen:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Maximale Aktivitätsanzahl]**
Die Anzahl der anzuzeigenden Aktivitäten
* **[!UICONTROL Pfad der Stream-Ressource]**
Leer lassen, um die Community-Site oder Community-Gruppe standardmäßig zu verwenden. Der Pfad der Stream-Ressource identifiziert die Quelle der Aktivitäten. Der Standardwert ist leer.
* **[!UICONTROL Anzeigen der Ansicht von Benutzeraktivitäten]**
Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der Aktivitäten auf der Basis der vom aktuellen Mitglied innerhalb der Community generierten Aktivitäten filtert. Die Option Standard ist aktiviert.
* **[!UICONTROL Ansicht &quot;Alle Aktivitäten&quot;anzeigen]**
Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der alle in der Community generierten Aktivitäten enthält, auf die das aktuelle Mitglied Zugriff hat. Die Option Standard ist aktiviert.
* **[!UICONTROL Anzeige nach Ansicht]**
Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der Aktivitäten nach denen filtert, denen das aktuelle Mitglied folgt. Die Option Standard ist aktiviert.

## Folgende Ansicht {#following-view}

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Funktionen, die Folgendes ermöglichen [blog](blog-feature.md), [Forum](forum.md), [Fragen und Antworten](working-with-qna.md), [calendar](calendar.md), [fileLibrary](file-library.md)und [Kommentare](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

Die **Folgen** -Schaltfläche bietet die Möglichkeit, Einträgen als Aktivitäten zu folgen. [Benachrichtigungen](notifications.md)und/oder [subscriptions](subscriptions.md). Jedes Mal, wenn **Folgen** ausgewählt ist, können Sie die Auswahl ein- oder ausschalten. Die `Email Subscriptions` Die Auswahl ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Folgende**. Zur Vereinfachung können Sie `Unfollow All` , um alle Methoden auszuschalten.

Die **Folgen** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds
* Auf einer Hauptseite mit Funktionen wie Foren, Fragen und Antworten und Blogs
   * Folgt allen Aktivitäten für diese allgemeine Funktion

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blog-Artikel
   * Folgt allen Aktivitäten für diesen spezifischen Eintrag

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen zu Aktivitäts-Streams](essentials-activities.md) für Entwickler.
