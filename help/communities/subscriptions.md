---
title: Communities-Abonnements
seo-title: Communities Subscriptions
description: Community-Mitglieder interagieren per E-Mail mit anderen Mitgliedern
seo-description: Community members interact with other members through email
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
role: Admin
exl-id: 8a756328-0405-49b7-b94d-3dd5a87c782a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 4%

---

# Communities-Abonnements {#communities-subscriptions}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Als Communitys [FP1](deploy-communities.md#latestfeaturepack), können Community-Mitglieder mit der Community per E-Mail über eine Funktion interagieren, die als Abonnements bezeichnet wird.

Abonnements ähneln [Benachrichtigungen](notifications.md) wie Mitglieder abonnieren können, wenn sie Blog-Artikel, Foren-Themen oder Fragen zur Frage nach Fragen.

Unterscheidet Anmeldungen von Benachrichtigungen:

* Mitglieder dürfen sich nicht bei folgenden anderen Mitgliedern anmelden
* Die einzige Aktion, die Mitglieder ergreifen müssen, ist die Auswahl `Email Subscriptions` wenn
* Wenn die E-Mail-Antwort konfiguriert ist, können Mitglieder Inhalte effektiv posten, indem sie einfach auf die erhaltene E-Mail antworten

### Voraussetzungen {#requirements}

**E-Mail konfigurieren**

E-Mail muss konfiguriert werden, damit Abonnements funktionieren und Mitglieder per E-Mail antworten können.

Anweisungen zum Einrichten von E-Mails finden Sie unter [E-Mail konfigurieren](email.md).

**Aktivieren von Abonnements und Folgen**

Komponenten müssen zur Aktivierung von Abonnements konfiguriert werden *und* folgt. Funktionen, die Abonnements zulassen [blog](blog-feature.md), [Forum](forum.md) und [Fragen und Antworten](working-with-qna.md).

## Abonnements aus folgenden {#subscriptions-from-following}

![chlimage_1-5](assets/chlimage_1-5.png)

Die **Folgen** -Schaltfläche bietet die Möglichkeit, auf Einträge als Aktivitäten, Abonnements und/oder Benachrichtigungen zu folgen. Jedes Mal, wenn **Folgen** ausgewählt ist, können Sie die Auswahl ein- oder ausschalten.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Folgende**. Zur Vereinfachung können Sie `Unfollow All` , um alle Methoden auszuschalten.

Die **Folgen** -Schaltfläche enthält die `Email Subscriptions` nur dann, wenn ein Forum, eine Frage oder ein Blog zur Aktivierung von E-Mail-Abonnements konfiguriert ist. Diese Schaltfläche wird angezeigt

* Auf der Hauptseite mit den Funktionen für das aktivierte Forum, Fragen und Antworten oder Blog

   * sendet eine E-Mail für alle Aktivitäten unter dieser Funktion

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blog-Artikel

   * Sendet eine E-Mail, wenn Aktivitäten für diesen spezifischen Eintrag vorhanden sind

## Antwort per E-Mail {#reply-by-email}

Wenn E-Mail [konfiguriert für Antwort per E-Mail](email.md#configure-polling-importer), erhält der Abonnent eine E-Mail mit dem veröffentlichten Inhalt und einen Link zum Online-Inhalt.

Wenn sie auf die E-Mail antworten, erscheint der von ihnen in der Antwort eingegebene Inhalt als Online-Inhalt.

![chlimage_1-6](assets/chlimage_1-6.png)

Die Dauer, die für die Veröffentlichung einer Antwort benötigt wird, wird durch die Variable [Aktualisierungsintervall des Abruf-Importtools](email.md#configure-polling-importer).

![chlimage_1-7](assets/chlimage_1-7.png)
