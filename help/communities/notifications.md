---
title: Communities-Benachrichtigungen
seo-title: Communities-Benachrichtigungen
description: AEM Communities verfügt über Benachrichtigungen, die Ereignisse anzeigen, die für das angemeldete Community-Mitglied von Interesse sind
seo-description: AEM Communities verfügt über Benachrichtigungen, die Ereignisse anzeigen, die für das angemeldete Community-Mitglied von Interesse sind
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 2%

---


# Communities-Benachrichtigungen {#communities-notifications}

## Überblick {#overview}

AEM Communities stellt einen Benachrichtigungsabschnitt bereit, der Ereignisse anzeigt, die für das Mitglied der Community von Interesse sind.

Benachrichtigungen ähneln [Aktivitäten](essentials-activities.md) und [Abonnements](subscriptions.md), da sie möglicherweise aus

* Das Mitglied, das Inhalte veröffentlicht
* Das Mitglied, das sich für ein anderes Mitglied entschieden hat
* Das Mitglied, das sich dafür entschieden hat, bestimmten Themen, Artikeln und anderen Inhaltsthreads zu folgen

Was Benachrichtigungen von Aktivitäten und Abonnements unterscheidet, ist

* Ein Link zum Abschnitt &quot;Benachrichtigungen&quot;ist immer in der Kopfzeile einer Community-Site vorhanden
   * Aktivitäten erfordern, dass die Stream-Funktion [Aktivität](functions.md#activity-stream-function) in die Struktur der Community-Site einbezogen wird.
   * Für Abonnement ist [Konfiguration der E-Mail](email.md) erforderlich
* Die Implementierung von Benachrichtigungen erfolgt über skalierbare und Plugin-fähige Kanal
   * Aktivitäten sind nur im Internet verfügbar
   * Abonnement stehen nur per E-Mail zur Verfügung

Ab Communities [FP1](deploy-communities.md#latestfeaturepack) sind die verfügbaren Benachrichtigungs-Kanal

* Der Web-Kanal, auf den über den Link `Notifications` zugegriffen wird
* Der E-Mail-Kanal, der verfügbar ist, wenn E-Mail richtig konfiguriert ist

Zukünftige Kanal sind mobile Geräte und Desktop-PCs.

### Voraussetzungen {#requirements}

**Email konfigurieren**

Die E-Mail-Benachrichtigung muss so konfiguriert sein, dass der E-Mail-Kanal funktioniert.

Anweisungen zum Einrichten der E-Mail finden Sie unter [Konfigurieren der E-Mail](analytics.md).

**Verfolgung aktivieren**

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind zulässig: [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendar](calendar.md), [fileLibrary](file-library.md) und [comments](comments.md).

Beachten Sie, dass

* Komponenten, die in Community [Site-Vorlagen](sites.md) und [Gruppenvorlagen](tools-groups.md) verwendet werden, können bereits konfiguriert werden, um Folgendes zuzulassen

* Die Profile der Mitgliedstaaten sind bereits so konfiguriert, dass andere Mitglieder folgen können

## Benachrichtigungen von{#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

Mit der Schaltfläche **Folgen** können Sie Einsendungen als Aktivitäten, Abonnements und/oder Benachrichtigungen verfolgen. Jedes Mal, wenn die Schaltfläche **Folgen** ausgewählt ist, können Sie eine Auswahl ein- oder ausschalten. Die Auswahl `Email Subscriptions` ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, wird der Text der Schaltfläche in **Nach** geändert. Aus praktischen Gründen können Sie `Unfollow All` auswählen, um alle Methoden auszuschalten.

Die Schaltfläche **Folgen** wird angezeigt

* Beim Anzeigen des Profils eines anderen Mitglieds
* Auf einer Hauptseite mit Funktionen wie Foren, QnA und Blogs
   * Folgt der gesamten Aktivität für diese allgemeine Funktion
* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Beantwortung einer Frage oder einen Blog-Artikel
   * Folgt der gesamten Aktivität für diesen spezifischen Eintrag

## Verwalten der Benachrichtigungseinstellungen {#managing-notification-settings}

Wenn Sie auf der Seite &quot;Benachrichtigungen&quot;den Link &quot;Benachrichtigungseinstellungen&quot;auswählen, können Sie verwalten, wie Benachrichtigungen empfangen werden.

Der Web-Kanal ist immer aktiviert.

![chlimage_1-255](assets/chlimage_1-255.png)

Der E-Mail-Kanal, der auf der richtigen [Konfiguration von email](email.md) basiert, stellt dieselben Einstellungen wie für den Web-Kanal bereit.

Der E-Mail-Kanal ist standardmäßig deaktiviert.

![chlimage_1-256](assets/chlimage_1-256.png)

Es kann von einem Mitglied aktiviert werden, hängt aber dennoch von der Konfiguration der E-Mail ab.

![chlimage_1-257](assets/chlimage_1-257.png)

## Ansehen der Benachrichtigungen {#viewing-notifications}

### Webbenachrichtigungen {#web-notifications}

Ein [Assistent, der eine Community-Site](sites-console.md) erstellt hat, enthält jetzt einen Link zur Funktion `Notifications` in der Kopfzeilenleiste der Site oberhalb des Banners. Im Gegensatz zu Nachrichten werden Benachrichtigungen für jede Community-Site erstellt, während Nachrichten während des Site-Erstellungsprozesses aktiviert werden müssen.

Wenn Sie die veröffentlichte Site besuchen, werden bei Auswahl des Links `Notifications` alle Benachrichtigungen für das Mitglied angezeigt.

![chlimage_1-258](assets/chlimage_1-258.png)

### E-Mail-Benachrichtigungen {#email-notifications}

Wenn der E-Mail-Kanal aktiviert ist, erhält das Mitglied eine E-Mail mit einer Verknüpfung zum Inhalt im Web.

![chlimage_1-259](assets/chlimage_1-259.png)

