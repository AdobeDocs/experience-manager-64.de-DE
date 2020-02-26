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
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Communities-Benachrichtigungen {#communities-notifications}

## Überblick {#overview}

AEM Communities bietet einen Benachrichtigungsabschnitt, der Ereignisse anzeigt, die für das in Community-Mitgliedern signierte Mitglied von Interesse sind.

Benachrichtigungen ähneln [Aktivitäten](essentials-activities.md) und [Abonnements](subscriptions.md) , die sich aus

* Das Mitglied, das Inhalte veröffentlicht
* Das Mitglied, das sich für ein anderes Mitglied entschieden hat
* Das Mitglied, das sich dafür entschieden hat, bestimmten Themen, Artikeln und anderen Inhaltsthreads zu folgen

Was unterscheidet Benachrichtigungen von Aktivitäten und Abonnements

* Ein Link zum Abschnitt &quot;Benachrichtigungen&quot;ist immer in der Kopfzeile einer Community-Site vorhanden
   * Aktivitäten erfordern, dass die [Aktivitätsstream-Funktion](functions.md#activity-stream-function) in die Struktur der Community-Site einbezogen wird.
   * Abonnements müssen [per E-Mail konfiguriert werden](email.md)
* Die Implementierung von Benachrichtigungen erfolgt über skalierbare und Plug-ins
   * Aktivitäten sind nur im Internet verfügbar
   * Abonnements sind nur per E-Mail verfügbar

Ab Communities [FP1](deploy-communities.md#latestfeaturepack)sind die verfügbaren Benachrichtigungskanäle

* Der Webkanal, auf den über den `Notifications` Link zugegriffen wird
* Der E-Mail-Kanal, der verfügbar ist, wenn E-Mail richtig konfiguriert ist

Zukünftige Kanäle sind Mobil und Desktop.

### Voraussetzungen {#requirements}

**Email konfigurieren**

Die E-Mail-Benachrichtigung muss so konfiguriert sein, dass der E-Mail-Kanal funktioniert.

Anweisungen zum Einrichten der E-Mail finden Sie unter E-Mail [konfigurieren](analytics.md).

**Verfolgung aktivieren**

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind zulässig: [Blog](blog-feature.md), [Forum](forum.md), [QnA](working-with-qna.md), [Kalender](calendar.md), [Dateibibliothek](file-library.md)[](comments.md)undKommentare.

Beachten Sie, dass

* Komponenten, die in Community- [Site-Vorlagen](sites.md) und [Gruppenvorlagen](tools-groups.md) verwendet werden, können bereits konfiguriert werden, um Folgendes zuzulassen:

* Mitgliederprofile sind bereits so konfiguriert, dass andere Mitglieder folgen können

## Benachrichtigungen von {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

Über die Schaltfläche **Folgen** können Sie Einsendungen als Aktivitäten, Abonnements und/oder Benachrichtigungen verfolgen. Bei jeder Auswahl der Schaltfläche &quot; **Folgen** &quot;können Sie eine Auswahl ein- oder ausschalten. Die `Email Subscriptions` Auswahl ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, wird der Text der Schaltfläche in **Folgendem** geändert. Aus praktischen Gründen ist es möglich, alle Methoden `Unfollow All` zu deaktivieren.

Die Schaltfläche **Folgen** wird angezeigt

* Beim Anzeigen des Profils eines anderen Mitglieds
* Auf einer Hauptseite mit Funktionen wie Foren, QnA und Blogs
   * Folgt allen Aktivitäten für diese allgemeine Funktion
* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Beantwortung einer Frage oder einen Blog-Artikel
   * Folgt allen Aktivitäten für diesen spezifischen Eintrag

## Verwalten von Benachrichtigungseinstellungen {#managing-notification-settings}

Wenn Sie auf der Seite &quot;Benachrichtigungen&quot;den Link &quot;Benachrichtigungseinstellungen&quot;auswählen, können Sie verwalten, wie Benachrichtigungen empfangen werden.

Der Webkanal ist immer aktiviert.

![chlimage_1-255](assets/chlimage_1-255.png)

Der E-Mail-Kanal, der auf einer ordnungsgemäßen [Konfiguration von E-Mail](email.md)beruht, bietet dieselben Einstellungen wie für den Webkanal.

Der E-Mail-Kanal ist standardmäßig deaktiviert.

![chlimage_1-256](assets/chlimage_1-256.png)

Es kann von einem Mitglied aktiviert werden, hängt aber dennoch von der Konfiguration der E-Mail ab.

![chlimage_1-257](assets/chlimage_1-257.png)

## Ansehen der Benachrichtigungen {#viewing-notifications}

### Webbenachrichtigungen {#web-notifications}

Ein [Assistent, der eine Community-Site](sites-console.md) erstellt hat, enthält jetzt einen Link zur `Notifications` Funktion in der Kopfzeilenleiste der Site oberhalb des Banners. Im Gegensatz zu Nachrichten werden Benachrichtigungen für jede Community-Site erstellt, während Nachrichten während des Site-Erstellungsprozesses aktiviert werden müssen.

Wenn Sie die veröffentlichte Site besuchen, werden bei Auswahl des `Notifications` Links alle Benachrichtigungen für das Mitglied angezeigt.

![chlimage_1-258](assets/chlimage_1-258.png)

### E-Mail-Benachrichtigungen {#email-notifications}

Wenn der E-Mail-Kanal aktiviert ist, erhält das Mitglied eine E-Mail, die einen Link zum Inhalt im Web enthält.

![chlimage_1-259](assets/chlimage_1-259.png)

