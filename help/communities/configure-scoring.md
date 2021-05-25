---
title: Grundlagen zu Scoring und Abzeichen
seo-title: Grundlagen zu Scoring und Abzeichen
description: Übersicht über die Funktionen Scoring und Badges
seo-description: Übersicht über die Funktionen Scoring und Badges
uuid: 858ca54f-b416-445d-a449-cef7eed33926
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ddb86546-d04b-4967-937b-50a19b0237a0
exl-id: 84aa46d5-4ca4-4f6e-b0b9-fc9907be00a5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 1%

---

# Grundlagen zu Scoring und Badges {#scoring-and-badges-essentials}

Die AEM Communities-Scoring- und -Badges-Funktion bietet die Möglichkeit, Community-Mitglieder zu identifizieren und zu belohnen.

Die Details zur Einrichtung der Funktion finden Sie unter

* [Communities-Scoring und -Abzeichen](implementing-scoring.md)

Diese Seite enthält zusätzliche technische Details:

* Anzeigen eines Zeichens](#displaying-badges) als Bild oder Text[
* Aktivieren der umfangreichen [Debug-Protokollierung](#debug-log-for-scoring-and-badging)
* Wie Sie [auf UGC](#ugc-for-scoring-and-badging) im Zusammenhang mit Scoring und Badging zugreifen

>[!CAUTION]
>
>Die in CRXDE Lite sichtbare Implementierungsstruktur kann sich ändern.

## Anzeigen von Abzeichen {#displaying-badges}

Ob ein Badge als Text oder Bild angezeigt wird, wird auf der Clientseite in der HBS-Vorlage gesteuert.

Suchen Sie beispielsweise nach `this.isAssigned` in `/libs/social/forum/components/hbs/topic/list-item.hbs`:

```
{{#each author.badges}}

  {{#if this.isAssigned}}

    <div class="scf-badge-text">

      {{this.title}}

    </div>

  {{/if}}

{{/each}}

{{#each author.badges}}

  {{#unless this.isAssigned}}

    <img class="scf-badge-image" alt="{{this.title}}" title="{{this.title}}" src="{{this.imageUrl}}" />

  {{/unless}}

{{/each}}
```

Wenn &quot;true&quot;, zeigt isAssigned an, dass das Zeichen für eine Rolle zugewiesen wurde und das Zeichen als Text angezeigt werden soll.

Wenn &quot;false&quot;, zeigt an, dass der Badge für einen Gewinn zugewiesen wurde und der Badge als Bild angezeigt werden soll.

Alle Änderungen an diesem Verhalten sollten in einem benutzerdefinierten Skript vorgenommen werden (entweder Überschreiben oder Überlagerung). Siehe [Clientseitige Anpassung](client-customize.md).

## Debug Log for Scoring and Badging {#debug-log-for-scoring-and-badging}

Um Scoring und Badging zu debuggen, kann eine benutzerdefinierte Protokolldatei eingerichtet werden. Der Inhalt dieser Protokolldatei kann dann dem Support zur Verfügung gestellt werden, wenn Probleme mit der Funktion auftreten.

Detaillierte Anweisungen finden Sie unter [Benutzerdefinierte Protokolldatei erstellen](../../help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

So richten Sie eine Slinglog-Datei schnell ein:

1. Greifen Sie auf **[!UICONTROL Adobe Experience Manager Web Console Log Support]** zu, z. B.

   * http://localhost:4502/system/console/slinglog

1. Wählen Sie **[!UICONTROL Neue Protokollfunktion hinzufügen]**

   1. Wählen Sie `DEBUG` für **[!UICONTROL Protokollebene]** aus.
   1. Geben Sie einen Namen für **[!UICONTROL Protokolldatei]** ein, z. B.

      * logs/scoring-debug.log
   1. Geben Sie zwei **[!UICONTROL Logger]** (class)-Einträge ein (mithilfe des Symbols `+` ).

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. Wählen Sie **[!UICONTROL Speichern]** aus



![chlimage_1-248](assets/chlimage_1-248.png)

So zeigen Sie Protokolleinträge an:

* Über die Web-Konsole

   * Unter dem Menü **[!UICONTROL Status]**
   * Wählen Sie **[!UICONTROL Protokolldateien]**
   * Suchen Sie nach dem Namen Ihrer Protokolldatei, z. B. `scoring-debug`.

* Auf der lokalen Festplatte des Servers

   * Die Protokolldatei befindet sich unter &lt;*server-install-dir*/crx-quickstart/logs/&lt;*log-file-name*.log
   * Beispiel: `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## UGC für Scoring und Badging {#ugc-for-scoring-and-badging}

Es ist möglich, die UGC im Zusammenhang mit Scoring und Badging anzuzeigen, wenn das ausgewählte SRP entweder JSRP oder MSRP, aber nicht ASRP ist. (Wenn Sie diese Begriffe nicht kennen, finden Sie weitere Informationen unter [Community-Inhaltsspeicherung](working-with-srp.md) und [Übersicht über den Speicher-Ressourcenanbieter](srp.md).)

Die Beschreibungen für den Zugriff auf Scoring- und Badging-Daten verwenden JSRP, da auf die UGC über [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) leicht zugegriffen werden kann.

**JSRP für Autor**: Das Experimentieren in der Autorenumgebung führt zu benutzergenerierten Inhalten, die nur in der Autorenumgebung sichtbar sind.

**JSRP bei der Veröffentlichung**: Ebenso ist es bei Tests in der Veröffentlichungsumgebung erforderlich, auf die CRXDE Lite mit Administratorrechten in einer Veröffentlichungsinstanz zuzugreifen. Wenn die Veröffentlichungsinstanz im [Produktionsmodus](../../help/sites-administering/production-ready.md) (Ausführungsmodus nosamplecontent) ausgeführt wird, muss die CRXDE Lite [aktiviert werden.](../../help/sites-administering/enabling-crxde-lite.md)

Der Basisspeicherort von UGC auf JSRP ist `/content/usergenerated/asi/jcr/`.

### Scoring- und Badging-APIs {#scoring-and-badging-apis}

Die folgenden APIs stehen zur Verwendung zur Verfügung:

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

Die neuesten Javadocs für die installierten [Releases](deploy-communities.md#LatestReleases) stehen Entwicklern aus dem Adobe-Repository zur Verfügung. Siehe [Verwenden von Maven für Communities: Javadocs](maven.md#javadocs).

**Speicherort und Format der UGC im Repository können sich ohne Warnung** ändern.

### Beispiel-Setup {#example-setup}

Die Screenshots von Repository-Daten stammen aus der Einrichtung von Scoring und Badging für ein Forum auf zwei verschiedenen AEM Sites:

1. Eine AEM Site mit einer eindeutigen ID (Community-Site, die mithilfe des Assistenten erstellt wurde):

   * Verwenden der Site &quot;Erste Schritte - Tutorial&quot;(Einstieg), die während des [Tutorials für die ersten Schritte](getting-started.md) erstellt wurde
   * Suchen Sie den Knoten der Forumsseite .

      * `/content/sites/engage/en/forum/jcr:content`
   * Hinzufügen von Scoring- und Badging-Eigenschaften

      * `scoringRules = [/etc/community/scoring/rules/comments-scoring,`

         `/etc/community/scoring/rules/forums-scoring]`
      * `badgingRules =[/etc/community/badging/rules/comments-scoring,`

         `/etc/community/badging/rules/forums-scoring]`
   * Suchen Sie den Knoten der Forumkomponente .

      * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Eigenschaft hinzufügen, um Badge anzuzeigen

      * `allowBadges = true`
   * Ein Benutzer meldet sich an, erstellt ein Forenthema und erhält ein Bronze-Zeichen





1. Eine AEM-Site *ohne* eindeutige ID:

   * Verwenden des [Community Components-Handbuchs](components-guide.md)
   * Suchen Sie den Knoten der Forumsseite .

      * `/content/community-components/en/forum/jcr:content`
   * Hinzufügen von Scoring- und Badging-Eigenschaften

      ```
      scoringRules = [/etc/community/scoring/rules/comments-scoring,
      /etc/community/scoring/rules/forums-scoring]
      ```

      ```
      badgingRules =[/etc/community/badging/rules/comments-scoring,
      /etc/community/badging/rules/forums-scoring]
      ```

   * Suchen Sie den Knoten der Forumkomponente .

      * `/content/community-components/en/forum/jcr:content/content/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Eigenschaft hinzufügen, um Badge anzuzeigen

      * `allowBadges = true`
   * Ein Benutzer meldet sich an, erstellt ein Forenthema und erhält ein Bronze-Zeichen




1. Benutzern wird über cURL ein Moderatorzeichen zugewiesen:

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" http://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

Da ein Benutzer zwei Bronze-Abzeichen gesammelt und ein Moderator-Abzeichen erhalten hat, wird der Benutzer mit seinem Forumseintrag wie folgt angezeigt:

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>Dieses Beispiel folgt nicht den folgenden Best Practices:
>
>* Die Namen von Scoring-Regeln sollten global eindeutig sein. sollten sie nicht mit demselben Namen enden.\
   >  Ein Beispiel dafür, was *not* zu tun hat:\
   >  /etc/community/scoring/rules/site1/forums-scoring\
   >  /etc/community/scoring/rules/site2/forums-scoring
   >
   >
* Erstellen von Unique Badge-Bildern für verschiedene AEM Sites

>



### Auf Scoring-UGC {#access-scoring-ugc} zugreifen

Die Verwendung der [APIs](#scoring-and-badging-apis) wird empfohlen.

Zu Ermittlungszwecken wird mithilfe von JSRP zum Beispiel der Basisordner mit Bewertungen

* `/content/usergenerated/asi/jcr/scoring`

Der untergeordnete Knoten von `scoring`ist der Name der Scoring-Regel. Daher empfiehlt es sich, dass die Namen von Scoring-Regeln auf einem Server global eindeutig sind.

Für die Geometrixx Engage-Site befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Scoring-Regel, der Site-ID der Community-Site ( `engage-ba81p`), einer eindeutigen ID und der ID des Benutzers verknüpft ist:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Auf der Guide-Site &quot;Community-Komponenten&quot;befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Scoring-Regel, einer Standard-ID ( `default-site`), einer eindeutigen ID und der ID des Benutzers konstruiert wurde:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

Die Punktzahl wird in der Eigenschaft `scoreValue_tl` gespeichert, die direkt einen Wert oder indirekt einen atomicCounter enthalten kann.

![chlimage_1-251](assets/chlimage_1-251.png)

### Zugriffs-Badging-UGC {#access-badging-ugc}

Die Verwendung der [APIs](#scoring-and-badging-apis) wird empfohlen.

Zu Untersuchungszwecken wird mithilfe von JSRP beispielsweise der Basisordner mit Informationen zu zugewiesenen oder vergebenen Abzeichen wie folgt angezeigt:

* /content/usergenerated/asi/jcr

gefolgt von dem Pfad zum Profil des Benutzers, der in einen Badges-Ordner endet, z. B.

* /home/users/community/w271OOup2Z4DjnOQrviv/profile/badges

#### Ausgezeichnetes Zeichen {#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### zugewiesenes Zeichen {#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## Zusätzliche Informationen {#additional-information}

So zeigen Sie eine sortierte Liste von Mitgliedern basierend auf Punkten an:

* [Leaderboard-](functions.md#leaderboard-function) Funktion zur Einbeziehung in eine Community-Site oder Gruppenvorlage.
* [Leaderboard-Komponente](enabling-leaderboard.md), die Komponente mit Funktionen für Leaderboard, für die Seitenbearbeitung.
