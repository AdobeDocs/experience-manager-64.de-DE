---
title: In-Context-Moderation
seo-title: In-Context Moderation
description: So führen Sie Moderatoraktionen durch
seo-description: How to perform moderator actions
uuid: 282a8bea-2822-4e5c-b9f4-4d9a5380d895
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ee104f6f-123b-4a6e-9031-849fc1318cc5
role: Admin
exl-id: a7678273-81f6-4089-ac73-2458d940e374
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---

# In-Context-Moderation {#in-context-moderation}

Für AEM Communities kann die Moderation von Administratoren und vertrauenswürdigen Community-Mitgliedern direkt auf der veröffentlichten Seite erfolgen, auf der die Community-Inhalte veröffentlicht wurden.

Bei Verwendung von [Moderationskonsole](moderation.md)enthalten die für den Inhalt angezeigten Informationen einen Link zur veröffentlichten Seite, um den Zugriff auf zusätzliche Moderationsaktionen zu ermöglichen, die bei der Moderation im Kontext verfügbar sind.

## Moderationsaktionen {#moderation-actions}

Eine Beschreibung der [Moderationsaktionen](moderate-ugc.md#moderation-actions).

## Moderationsbenutzeroberfläche {#moderation-ui}

Die Benutzeroberfläche, die dem Moderator auf der Veröffentlichungsinstanz angezeigt wird, ist im Dialogfeld für die Veröffentlichung und Verwaltung benutzergenerierter Inhalte (UGC) enthalten. Die Elemente der Benutzeroberfläche werden durch den Status des Site-Besuchers bestimmt - unabhängig davon, ob sie ...

1. Das Mitglied, das den Inhalt veröffentlicht hat
1. Moderator eines vertrauenswürdigen Mitglieds
1. Administrator
1. Angemeldet, aber weder Administrator, Moderator noch Autor des Inhalts
1. Nicht angemeldet

## Beispiel {#example}

Verwenden der [Geometrixx Engage](http://localhost:4503/content/sites/engage/en.html) Site erstellt, wenn [Erste Schritte mit AEM Communities](getting-started.md)können Sie schnell einen Thread in einem Forum einrichten, in dem Sie verschiedene Moderationsaktivitäten in der Veröffentlichungsumgebung erleben können, wie unten dargestellt.

Aaron McDonald (aaron.mcdonald@mailinator.com) wurde als vertrauenswürdiges Community-Mitglied identifiziert, indem er ihn bei der Erstellung der Website zur Community-Interaktion-Moderatoren-Gruppe hinzufügte.

Rebekah Larsen (rebekah.larsen@trashymail.com) kann als Mitglied der Community-Engagement-Mitgliedergruppe hinzugefügt werden, indem die [Mitgliederkonsole](members.md).

Weitere Informationen zu Community-Benutzergruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

### Forumbeiträge erstellen {#create-the-forum-posts}

* Als Rebekah Larsen anmelden (rebekah.larsen@trashymail.com)

   * Forum auswählen
   * Neuen Beitrag auswählen
   * Betreff eingeben

      Wann wird der Nektar in der Humming-Vogelzucht geändert?

   * Textkörper eingeben

      Ich hatte nicht viel Erfolg, wenn ich jedes Jahr eine Kolibris aufhänge. Anscheinend kommen sie an ein oder zwei Tagen, dann ist es so. Ich ändere es einmal in der Woche ist das zu lang? Muss ich es früher ändern?
   * Beitrag auswählen
   * Log Out auswählen

* Als Aaron McDonald anmelden (aaron.mcdonald@mailinator.com)

   * Forum auswählen
   * Wählen Sie für das Thema &quot;Hummingbird&quot;die Option &quot;Mehr lesen&quot;
   * Geben Sie den Kommentar für Antwort posten ein.

      Ich wechsele meine Woche einmal und bekomme sie von Mai bis Oktober.

   * Antwort auswählen
   * Log Out auswählen

* Als Andrew Schäffer anmelden (andrew.schaeffer@trashymail.com)

   * Forum auswählen
   * Wählen Sie für das Thema &quot;Hummingbird&quot;die Option &quot;Mehr lesen&quot;
   * Geben Sie den Kommentar für Antwort posten ein.

      Ich verkaufe Nektar und Feeds - besuchen Sie https://my.viral.url/

   * Antwort auswählen
   * Log Out auswählen

### Anonymer Site-Besucher (#5) {#anonymous-site-visitor}

Im Folgenden finden Sie eine Ansicht des Forums, das von einem Site-Besucher gesehen wird, der nicht angemeldet ist (5).

Ein anonymer Site-Besucher kann nur das Forum anzeigen, jedoch keine Inhalte posten und keine Moderationsaktionen durchführen.

![chlimage_1](assets/chlimage_1.png)

### Neues Mitglied (#4) {#new-member}

Melden Sie sich auf der Autoreninstanz als Administrator an und fügen Sie Boyd Larsen (boyd.larsen@dodgit.com) als neues Mitglied der Community-Interaktionsmitgliedern-Gruppe hinzu, indem Sie die [Mitgliederkonsole](members.md)und dann abmelden.

Melden Sie sich bei der Veröffentlichung als Boyd Larsen an und greifen Sie auf den Thread zu, indem Sie `Forum`, und dann `Read more` für den Kolibris Post.

Hinweis

* Boyd hat nicht am Forum teilgenommen
* Boyd kann nichts löschen
* Boyd ist angemeldet und kann Inhalte beantworten oder kennzeichnen

Lassen Sie Boyd Flag auswählen, um den von Andrew veröffentlichten Inhalt zu kennzeichnen.

Abmelden

![chlimage_1-1](assets/chlimage_1-1.png)

### Administrator (#3) {#administrator}

Melden Sie sich als Administrator (Admin) an und greifen Sie auf den Thread zu, indem Sie &quot;Forum&quot;auswählen und dann &quot;Mehr lesen&quot;für einen Beitrag auswählen.

Hinweis

* Admin kann kennzeichnen, löschen, bearbeiten, ablehnen, ausschneiden, schließen, fixieren, Funktion
* Der Administrator kann Administration auswählen, um auf die Moderationskonsole zuzugreifen.

![Community-Admin-Forum](assets/communityadmin-forum.png)

Wählen Sie das Menüelement Administration aus, um auf [Moderationskonsole](moderation.md) aus der Veröffentlichungsumgebung.

Beachten Sie, dass für einen Administrator alle moderierbaren Inhalte sichtbar sind, nicht nur Inhalte von der Community-Site &quot;Geometrixx Engage&quot;.

Der Suchfilter ist ein Seitenelement, das geöffnet oder geschlossen wird.

Abmelden.

![moderationconsole-publish](assets/moderationconsole-publish.png)

### Community-Moderator (#2) {#community-moderator}

Melden Sie sich als Aaron McDonald (aaron.mcdonal@mailinator.com) an, ein Community-Moderator, und greifen Sie auf den Thread zu, indem Sie Forum auswählen, und lesen Sie dann mehr für den Komingbird-Post.

Hinweis

* Aaron kann seinen eigenen Beitrag beantworten, löschen, bearbeiten oder ablehnen
* Aaron kann auch andere Inhalte kennzeichnen/zulassen, antworten, löschen, bearbeiten, ablehnen
* Aaron kann das Forenthema ausschneiden, um es in ein anderes Forum zu verschieben, für das er moderiert
* Aaron kann Administration auswählen, um auf die Moderationskonsole zuzugreifen.

![chlimage_1-2](assets/chlimage_1-2.png)

Wählen Sie das Menüelement Administration aus, um auf [Moderationskonsole](moderation.md) aus der Veröffentlichungsumgebung.

Beachten Sie, dass für einen Community-Moderator nur moderierbare Inhalte von der Geometrixx Engage Community-Site angezeigt werden.

Beachten Sie, dass der Community-Moderator dieselben Optionen wie der Administrator hat (Bild ist mit geschlossener Suchseitenleiste), aber keinen Zugriff auf andere AEM Konsolen hat.

Abmelden.

![moderatoraccess](assets/moderatoraccess.png)

### Inhaltsautor (#1) {#content-author}

Melden Sie sich als Rebekah Larsen (rebekah.larsen@mailinator.com) an, ein Community-Mitglied, das den Thread gestartet hat, und greifen Sie durch die Auswahl von Forum auf den Thread zu, und lesen Sie dann mehr für den Hummingbird-Post.

Hinweis

* Rebekah kann ihren eigenen Beitrag löschen oder bearbeiten
* Rebekah kann auch auf andere Inhalte antworten oder diese kennzeichnen
* Rebekah kann nicht auf die Moderationskonsole zugreifen

![chlimage_1-3](assets/chlimage_1-3.png)
