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
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 2%

---

# Communities-Benachrichtigungen {#communities-notifications}

## Überblick {#overview}

AEM Communities bietet einen Benachrichtigungsabschnitt, in dem Ereignisse angezeigt werden, die für das angemeldete Community-Mitglied von Interesse sind.

Benachrichtigungen ähneln [Aktivitäten](essentials-activities.md) und [Abonnements](subscriptions.md), da sie aus

* Das Mitglied, das Inhalte veröffentlicht
* Das Mitglied, das einem anderen Mitglied folgt
* Das Mitglied, das bestimmte Themen, Artikel und andere Threads von Inhalten verfolgt

Was unterscheidet Benachrichtigungen von Aktivitäten und Abonnements?

* Ein Link zum Benachrichtigungsabschnitt ist immer in der Kopfzeile einer Community-Site vorhanden
   * Für Aktivitäten muss die [Aktivitäts-Stream-Funktion](functions.md#activity-stream-function) in die Struktur der Community-Site aufgenommen werden.
   * Abonnements erfordern [Konfiguration von E-Mail](email.md)
* Die Implementierung von Benachrichtigungen erfolgt über skalierbare und Pluggable Kanäle
   * Aktivitäten sind nur im Internet verfügbar
   * Abonnements sind nur per E-Mail verfügbar

Ab Communities [FP1](deploy-communities.md#latestfeaturepack) sind die verfügbaren Benachrichtigungskanäle

* Der Webkanal, auf den über den Link `Notifications` zugegriffen wird
* Der E-Mail-Kanal, der bei ordnungsgemäßer E-Mail-Konfiguration verfügbar ist

Zukünftige Kanäle sind Mobilgeräte und Desktop.

### Voraussetzungen {#requirements}

**E-Mail konfigurieren**

E-Mail muss konfiguriert werden, damit der E-Mail-Kanal funktioniert.

Anweisungen zum Einrichten von E-Mails finden Sie unter [Konfigurieren von E-Mail](analytics.md).

**Aktivieren Sie die Folgen**

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind möglich: [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendar](calendar.md), [filelibrary](file-library.md) und [comments](comments.md).

Beachten Sie, dass

* Komponenten, die in der Community [Site-Vorlagen](sites.md) und [Gruppenvorlagen](tools-groups.md) verwendet werden, können bereits so konfiguriert sein, dass Folgendes zulässig ist

* Mitgliederprofile sind bereits so konfiguriert, dass andere Mitglieder folgen können

## Benachrichtigungen aus folgenden {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

Die Schaltfläche **Folgen** bietet die Möglichkeit, Einträgen als Aktivitäten, Abonnements und/oder Benachrichtigungen zu folgen. Jedes Mal, wenn die Schaltfläche **Folgen** ausgewählt wird, können Sie eine Auswahl ein- oder ausschalten. Die Auswahl `Email Subscriptions` ist nur bei Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Nach**. Zur Vereinfachung können Sie `Unfollow All` auswählen, um alle Methoden zu deaktivieren.

Die Schaltfläche **Folgen** wird angezeigt

* Beim Anzeigen des Profils eines anderen Mitglieds
* Auf einer Hauptseite mit Funktionen wie Foren, Fragen und Antworten und Blogs
   * Folgt allen Aktivitäten für diese allgemeine Funktion
* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blog-Artikel
   * Folgt allen Aktivitäten für diesen spezifischen Eintrag

## Verwalten von Benachrichtigungseinstellungen {#managing-notification-settings}

Über den Link Benachrichtigungseinstellungen auf der Seite Benachrichtigungen können die einzelnen Mitglieder verwalten, wie Benachrichtigungen empfangen werden.

Der Webkanal ist immer aktiviert.

![chlimage_1-255](assets/chlimage_1-255.png)

Der E-Mail-Kanal, der auf einer ordnungsgemäßen [Konfiguration von E-Mail](email.md) basiert, bietet dieselben Einstellungen wie für den Webkanal.

Der E-Mail-Kanal ist standardmäßig deaktiviert.

![chlimage_1-256](assets/chlimage_1-256.png)

Es kann von einem Mitglied aktiviert werden, hängt aber dennoch von der E-Mail-Konfiguration ab.

![chlimage_1-257](assets/chlimage_1-257.png)

## Ansehen der Benachrichtigungen {#viewing-notifications}

### Webbenachrichtigungen {#web-notifications}

Ein [Assistent, der die Community-Site](sites-console.md) erstellt hat, enthält jetzt einen Link zur Funktion `Notifications` in der Kopfzeilenleiste der Site oberhalb des Banners. Im Gegensatz zu Nachrichten werden Benachrichtigungen für jede Community-Site erstellt, während Nachrichten während des Site-Erstellungsprozesses aktiviert werden müssen.

Beim Besuch der veröffentlichten Site werden durch Auswahl des Links `Notifications` alle Benachrichtigungen für das Mitglied angezeigt.

![chlimage_1-258](assets/chlimage_1-258.png)

### E-Mail-Benachrichtigungen {#email-notifications}

Wenn der E-Mail-Kanal aktiviert ist, erhält das Mitglied eine E-Mail mit einem Link zum Inhalt im Web.

![chlimage_1-259](assets/chlimage_1-259.png)
