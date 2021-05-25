---
title: Communities-Abonnements
seo-title: Communities-Abonnements
description: 'Community-Mitglieder interagieren per E-Mail mit anderen Mitgliedern '
seo-description: 'Community-Mitglieder interagieren per E-Mail mit anderen Mitgliedern '
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
role: Administrator
exl-id: 8a756328-0405-49b7-b94d-3dd5a87c782a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 3%

---

# Communities-Abonnements {#communities-subscriptions}

## Überblick {#overview}

Ab Communities [FP1](deploy-communities.md#latestfeaturepack) können Community-Mitglieder per E-Mail mit der Community interagieren, indem sie eine Funktion verwenden, die als Abonnements bezeichnet wird.

Abonnements ähneln [Benachrichtigungen](notifications.md), da Mitglieder sich abonnieren können, wenn sie Blog-Artikel, Forenthemen oder Fragen zur Frage stellen.

Unterscheidet Anmeldungen von Benachrichtigungen:

* Mitglieder dürfen sich nicht bei folgenden anderen Mitgliedern anmelden
* Die einzige Aktion, die Mitglieder ergreifen müssen, besteht darin, `Email Subscriptions` auszuwählen, wenn sie
* Wenn die E-Mail-Antwort konfiguriert ist, können Mitglieder Inhalte effektiv posten, indem sie einfach auf die erhaltene E-Mail antworten

### Voraussetzungen {#requirements}

**E-Mail konfigurieren**

E-Mail muss konfiguriert werden, damit Abonnements funktionieren und Mitglieder per E-Mail antworten können.

Anweisungen zum Einrichten von E-Mails finden Sie unter [Konfigurieren von E-Mail](email.md).

**Aktivieren von Abonnements und Folgen**

Komponenten müssen so konfiguriert sein, dass folgende Abonnements aktiviert werden: *und*. Funktionen, die Abonnements zulassen, sind [blog](blog-feature.md), [forum](forum.md) und [QnA](working-with-qna.md).

## Abonnements aus folgenden {#subscriptions-from-following}

![chlimage_1-5](assets/chlimage_1-5.png)

Die Schaltfläche **Folgen** bietet die Möglichkeit, Einträgen als Aktivitäten, Abonnements und/oder Benachrichtigungen zu folgen. Jedes Mal, wenn die Schaltfläche **Folgen** ausgewählt wird, können Sie eine Auswahl ein- oder ausschalten.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Nach**. Zur Vereinfachung können Sie `Unfollow All` auswählen, um alle Methoden zu deaktivieren.

Die Schaltfläche **Folgen** enthält nur dann die Option `Email Subscriptions`, wenn ein Forum, eine Frage oder ein Blog zur Aktivierung von E-Mail-Abonnements konfiguriert ist. Diese Schaltfläche wird angezeigt

* Auf der Hauptseite mit den Funktionen für das aktivierte Forum, Fragen und Antworten oder Blog

   * sendet eine E-Mail für alle Aktivitäten unter dieser Funktion

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blog-Artikel

   * Sendet eine E-Mail, wenn Aktivitäten für diesen spezifischen Eintrag vorhanden sind

## Antworten nach E-Mail {#reply-by-email}

Wenn die E-Mail-Adresse [für die Antwort per E-Mail](email.md#configure-polling-importer) konfiguriert ist, erhält das Abonnent eine E-Mail mit dem veröffentlichten Inhalt und einen Link zum Online-Inhalt.

Wenn sie auf die E-Mail antworten, erscheint der von ihnen in der Antwort eingegebene Inhalt als Online-Inhalt.

![chlimage_1-6](assets/chlimage_1-6.png)

Die Zeitdauer, die für die Veröffentlichung einer Antwort benötigt wird, wird durch das Update-Intervall des [Abruf-Importtools](email.md#configure-polling-importer) gesteuert.

![chlimage_1-7](assets/chlimage_1-7.png)
