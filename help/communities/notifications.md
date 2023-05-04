---
title: Communities-Benachrichtigungen
seo-title: Communities Notifications
description: AEM Communities verfügt über Benachrichtigungen, die Ereignisse anzeigen, die für das angemeldete Community-Mitglied von Interesse sind
seo-description: AEM Communities has notifications that display events of interest to the signed-in community member
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Admin
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 3%

---

# Communities-Benachrichtigungen {#communities-notifications}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

AEM Communities bietet einen Benachrichtigungsabschnitt, in dem Ereignisse angezeigt werden, die für das angemeldete Community-Mitglied von Interesse sind.

Benachrichtigungen ähneln [activities](essentials-activities.md) und [subscriptions](subscriptions.md) , die sich aus

* Das Mitglied, das Inhalte veröffentlicht
* Das Mitglied, das einem anderen Mitglied folgt
* Das Mitglied, das bestimmte Themen, Artikel und andere Threads von Inhalten verfolgt

Was unterscheidet Benachrichtigungen von Aktivitäten und Abonnements?

* Ein Link zum Benachrichtigungsabschnitt ist immer in der Kopfzeile einer Community-Site vorhanden
   * Die Aktivitäten erfordern [Aktivitäts-Stream-Funktion](functions.md#activity-stream-function) in die Struktur der Community-Site aufgenommen werden.
   * Abonnements erforderlich [E-Mail-Konfiguration](email.md)
* Die Implementierung von Benachrichtigungen erfolgt über skalierbare und Pluggable Kanäle
   * Aktivitäten sind nur im Internet verfügbar
   * Abonnements sind nur per E-Mail verfügbar

Als Communitys [FP1](deploy-communities.md#latestfeaturepack), sind die verfügbaren Benachrichtigungskanäle

* Der Webkanal, auf den mithilfe der `Notifications` link
* Der E-Mail-Kanal, der bei ordnungsgemäßer E-Mail-Konfiguration verfügbar ist

Zukünftige Kanäle sind Mobilgeräte und Desktop.

### Voraussetzungen {#requirements}

**E-Mail konfigurieren**

E-Mail muss konfiguriert werden, damit der E-Mail-Kanal funktioniert.

Anweisungen zum Einrichten von E-Mails finden Sie unter [E-Mail konfigurieren](analytics.md).

**Aktivieren Sie die Folgen**

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Funktionen, die Folgendes ermöglichen [blog](blog-feature.md), [Forum](forum.md), [Fragen und Antworten](working-with-qna.md), [calendar](calendar.md), [fileLibrary](file-library.md)und [Kommentare](comments.md).

Beachten Sie Folgendes:

* In der Community verwendete Komponenten [Site-Vorlagen](sites.md) und [Gruppenvorlagen](tools-groups.md) kann bereits so konfiguriert sein, dass Folgendes zulässig ist

* Mitgliederprofile sind bereits so konfiguriert, dass andere Mitglieder folgen können

## Benachrichtigungen aus folgenden {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

Die **Folgen** -Schaltfläche bietet die Möglichkeit, auf Einträge als Aktivitäten, Abonnements und/oder Benachrichtigungen zu folgen. Jedes Mal, wenn **Folgen** ausgewählt ist, können Sie die Auswahl ein- oder ausschalten. Die `Email Subscriptions` Die Auswahl ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Folgende**. Zur Vereinfachung können Sie `Unfollow All` , um alle Methoden auszuschalten.

Die **Folgen** wird angezeigt

* Beim Anzeigen des Profils eines anderen Mitglieds
* Auf einer Hauptseite mit Funktionen wie Foren, Fragen und Antworten und Blogs
   * Folgt allen Aktivitäten für diese allgemeine Funktion
* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blog-Artikel
   * Folgt allen Aktivitäten für diesen spezifischen Eintrag

## Verwalten von Benachrichtigungseinstellungen {#managing-notification-settings}

Über den Link Benachrichtigungseinstellungen auf der Seite Benachrichtigungen können die einzelnen Mitglieder verwalten, wie Benachrichtigungen empfangen werden.

Der Webkanal ist immer aktiviert.

![chlimage_1-255](assets/chlimage_1-255.png)

Der E-Mail-Kanal, der auf die ordnungsgemäße [E-Mail-Konfiguration](email.md), stellt dieselben Einstellungen wie für den Webkanal bereit.

Der E-Mail-Kanal ist standardmäßig deaktiviert.

![chlimage_1-256](assets/chlimage_1-256.png)

Es kann von einem Mitglied aktiviert werden, hängt aber dennoch von der E-Mail-Konfiguration ab.

![chlimage_1-257](assets/chlimage_1-257.png)

## Ansehen der Benachrichtigungen {#viewing-notifications}

### Webbenachrichtigungen {#web-notifications}

A [Assistent erstellte Community-Site](sites-console.md) enthält jetzt einen Link zum `Notifications` in der Kopfzeilenleiste der Site oberhalb des Banners. Im Gegensatz zu Nachrichten werden Benachrichtigungen für jede Community-Site erstellt, während Nachrichten während des Site-Erstellungsprozesses aktiviert werden müssen.

Wählen Sie beim Besuch der veröffentlichten Site die `Notifications` -Link zeigt alle Benachrichtigungen für das Mitglied an.

![chlimage_1-258](assets/chlimage_1-258.png)

### E-Mail-Benachrichtigungen {#email-notifications}

Wenn der E-Mail-Kanal aktiviert ist, erhält das Mitglied eine E-Mail mit einem Link zum Inhalt im Web.

![chlimage_1-259](assets/chlimage_1-259.png)
