---
title: Grundlagen zu Scoring und Abzeichen
seo-title: Grundlagen zu Scoring und Abzeichen
description: Übersicht über die Funktionen "Bewertung und Abzeichen"
seo-description: Übersicht über die Funktionen "Bewertung und Abzeichen"
uuid: 858ca54f-b416-445d-a449-cef7eed33926
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ddb86546-d04b-4967-937b-50a19b0237a0
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 1%

---


# Grundlagen zu Scoring und Kennzeichen {#scoring-and-badges-essentials}

Die AEM Communities-Funktion für Scoring und Abzeichen bietet die Möglichkeit, Community-Mitglieder zu identifizieren und zu belohnen.

Die Details zur Einrichtung der Funktion finden Sie unter

* [Communities - Bewertung und Abzeichen](implementing-scoring.md)

Diese Seite enthält weitere technische Details:

* Anzeigen eines Kennzeichens](#displaying-badges) als Bild oder Text[
* So aktivieren Sie die umfassende [Debugging-Protokollierung](#debug-log-for-scoring-and-badging)
* Wie greifen Sie auf UGC](#ugc-for-scoring-and-badging) im Zusammenhang mit Scoring und Abzeichen zu?[

>[!CAUTION]
>
>Die in der CRXDE Lite sichtbare Implementierungsstruktur kann sich ändern.

## Anzeigen von Kennzeichen {#displaying-badges}

Ob ein Zeichen als Text oder Bild angezeigt wird, wird auf der Clientseite in der HBS-Vorlage gesteuert.

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

Wenn &quot;true&quot;, zeigt isAssigned an, dass das Zeichen für eine Rolle zugewiesen wurde und das Zeichen als Text angezeigt werden sollte.

Wenn &quot;false&quot;festgelegt ist, zeigt Zugewiesen an, dass das Abzeichen für eine Ergebnisbewertung vergeben wurde und das Abzeichen als Bild angezeigt werden sollte.

Änderungen an diesem Verhalten sollten in einem benutzerdefinierten Skript vorgenommen werden (entweder Überschreiben oder Überlagerung). Siehe [Clientseitige Anpassung](client-customize.md).

## Debug-Protokoll für Bewertung und Abzeichen {#debug-log-for-scoring-and-badging}

Um das Debugging von Scoring und Abzeichen zu unterstützen, kann eine benutzerdefinierte Protokolldatei eingerichtet werden. Der Inhalt dieser Protokolldatei kann dann dem Kundensupport zur Verfügung gestellt werden, wenn Probleme mit der Funktion auftreten.

Ausführliche Anweisungen finden Sie unter [Benutzerspezifische Protokolldatei erstellen](../../help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

So richten Sie eine Slinglog-Datei schnell ein:

1. Zugriff auf die **[!UICONTROL Adobe Experience Manager Web Console Log Support]**, z. B.

   * http://localhost:4502/system/console/slinglog

1. Wählen Sie **[!UICONTROL Hinzufügen neue Protokollfunktion]**

   1. Wählen Sie `DEBUG` für **[!UICONTROL Protokollebene]**
   1. Geben Sie einen Namen für **[!UICONTROL Protokolldatei]** ein, z. B.

      * logs/scoring-debug.log
   1. Geben Sie zwei **[!UICONTROL Logger]** (class)-Einträge ein (mit dem `+`-Symbol)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. Wählen Sie **[!UICONTROL Speichern]** aus



![chlimage_1-248](assets/chlimage_1-248.png)

So zeigen Sie Protokolleinträge an:

* Über die Web-Konsole

   * Im Menü **[!UICONTROL Status]**
   * Wählen Sie **[!UICONTROL Protokolldateien]**
   * Suchen Sie nach dem Namen Ihrer Protokolldatei, z. B. `scoring-debug`

* Auf dem lokalen Datenträger des Servers

   * Die Protokolldatei befindet sich unter &lt;*server-install-dir*/crx-quickstart/logs/&lt;*log-file-name*.log
   * Beispiel: `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## UGC für Scoring und Bading {#ugc-for-scoring-and-badging}

Es ist möglich, die UGC in Bezug auf die Bewertung und Abzeichen zu Ansichten, wenn die gewählte SRP entweder JSRP oder MSRP, aber nicht ASRP ist. (Wenn Sie mit diesen Begriffen nicht vertraut sind, lesen Sie [Community Content Datenspeicherung](working-with-srp.md) und [Übersicht über den Datenspeicherung Resource Provider](srp.md).)

Die Beschreibungen für den Zugriff auf Scoring- und Abzeichen-Daten verwenden JSRP, da der Zugriff auf die UGC mit [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) einfach ist.

**JSRP für Autor**: Das Experimentieren in der Autorendatei führt zu einer UGC, die nur in der Autorenversion der Umgebung sichtbar ist.

**JSRP bei Veröffentlichung**: Ebenso ist es bei Tests auf der Umgebung &quot;Veröffentlichen&quot;erforderlich, auf die CRXDE Lite mit Administratorrechten auf einer Instanz im Veröffentlichungsmodus zuzugreifen. Wenn die Instanz im Veröffentlichungsmodus im Produktionsmodus [ausgeführt wird (nicht im Ausführungsmodus zum Abrufen von Inhalten), muss die CRXDE Lite [aktiviert werden.](../../help/sites-administering/production-ready.md)](../../help/sites-administering/enabling-crxde-lite.md)

Der Basisspeicherort von UGC auf JSRP ist `/content/usergenerated/asi/jcr/`.

### Scoring- und Badging-APIs {#scoring-and-badging-apis}

Die folgenden APIs stehen zur Verwendung zur Verfügung:

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

Die neuesten JavaScript-Dateien für die installierten [Releases](deploy-communities.md#LatestReleases) stehen Entwicklern aus dem Adoben-Repository zur Verfügung. Siehe [Maven für Communities verwenden: Javadocs](maven.md#javadocs).

**Speicherort und Format des UGC im Repository können ohne Warnung** geändert werden.

### Beispiel-Setup {#example-setup}

Die Screenshots der Repository-Daten stammen aus der Einrichtung von Scoring und Abzeichen für ein Forum auf zwei verschiedenen AEM Websites:

1. Eine AEM mit einer eindeutigen ID (Community-Site, die mithilfe des Assistenten erstellt wurde):

   * Verwenden der Website &quot;Erste Schritte&quot;-Lernprogramm (Interaktion), die während des [Lernprogramms &quot;Erste Schritte&quot;](getting-started.md) erstellt wurde
   * Suchen Sie den Knoten der Forumseite

      * `/content/sites/engage/en/forum/jcr:content`
   * hinzufügen und Abzeichen

      * `scoringRules = [/etc/community/scoring/rules/comments-scoring,`

         `/etc/community/scoring/rules/forums-scoring]`
      * `badgingRules =[/etc/community/badging/rules/comments-scoring,`

         `/etc/community/badging/rules/forums-scoring]`
   * Suchen Sie den Knoten der Forumkomponente

      * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * hinzufügen Eigenschaft zum Anzeigen von Abzeichen

      * `allowBadges = true`
   * Ein Benutzer meldet sich an, erstellt ein Forenthema und erhält eine Bronze-Abzeichen





1. Eine AEM-Site *ohne* eine eindeutige ID:

   * Verwenden des Handbuchs [Community-Komponenten](components-guide.md)
   * Suchen Sie den Knoten der Forumseite

      * `/content/community-components/en/forum/jcr:content`
   * hinzufügen und Abzeichen

      ```
      scoringRules = [/etc/community/scoring/rules/comments-scoring,
      /etc/community/scoring/rules/forums-scoring]
      ```

      ```
      badgingRules =[/etc/community/badging/rules/comments-scoring,
      /etc/community/badging/rules/forums-scoring]
      ```

   * Suchen Sie den Knoten der Forumkomponente

      * `/content/community-components/en/forum/jcr:content/content/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * hinzufügen Eigenschaft zum Anzeigen von Abzeichen

      * `allowBadges = true`
   * Ein Benutzer meldet sich an, erstellt ein Forenthema und erhält eine Bronze-Abzeichen




1. Dem Benutzer wird mithilfe von cURL ein Moderator-Abzeichen zugewiesen:

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" http://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

Da ein Benutzer zwei Bronze-Abzeichen erhalten hat und ein Moderator-Abzeichen erhalten hat, wird der Benutzer mit seinem Foreneintrag wie folgt angezeigt:

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>Dieses Beispiel folgt nicht den folgenden bewährten Verfahren:
>
>* Die Namen von Bewertungsregeln sollten global eindeutig sein. sie sollten nicht mit demselben Namen enden.\
   >  Beispiel für die folgenden Aufgaben:**\
   >  /etc/community/scoring/rules/site1/forums-scoring\
   >  /etc/community/scoring/rules/site2/forums-scoring
   >
   >
* Erstellen von eindeutigen Abzeichen-Bildern für verschiedene AEM Sites

>



### Zugriff auf Scoring-UGC {#access-scoring-ugc}

Die Verwendung der [APIs](#scoring-and-badging-apis) wird empfohlen.

Zu Ermittlungszwecken ist der Basisordner, der Ergebnisse enthält, z. B. mithilfe von JSRP

* `/content/usergenerated/asi/jcr/scoring`

Der untergeordnete Knoten von `scoring`ist der Name der Bewertungsregel. Eine Best Practice ist daher, dass die Namen von Bewertungsregeln auf einem Server global eindeutig sind.

Für die Geometrixx Engage-Site befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Bewertungsregel, der Site-ID der Community ( `engage-ba81p`), einer eindeutigen ID und der ID des Benutzers verknüpft ist:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Auf der Guide-Site &quot;Community-Komponenten&quot;befinden sich der Benutzer und sein Ergebnis in einem Pfad, der mit dem Namen der Bewertungsregel, einer Standard-ID ( `default-site`), einer eindeutigen ID und der ID des Benutzers erstellt wurde:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

Das Ergebnis wird in der Eigenschaft `scoreValue_tl` gespeichert, die direkt nur einen Wert enthält oder indirekt auf einen atomicCounter verweist.

![chlimage_1-251](assets/chlimage_1-251.png)

### Zugriffskennzeichen-UGC {#access-badging-ugc}

Die Verwendung der [APIs](#scoring-and-badging-apis) wird empfohlen.

Zu Ermittlungszwecken wird beispielsweise mithilfe von JSRP der Basisordner mit Informationen über zugewiesene oder zugewiesene Kennzeichen wie folgt angezeigt:

* /content/usergenerated/asi/jcr

Nach dem Pfad zum Profil des Benutzers, der in einem Ablagenordner endet, z. B.

* /home/users/community/w271OOup2Z4DjnOQrviv/Profil/badges

#### Ausgezeichnetes Zeichen {#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### zugewiesenes Zeichen {#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## Zusätzliche Informationen {#additional-information}

So zeigen Sie eine sortierte Liste der Mitglieder basierend auf Punkten an:

* [Leaderboard-](functions.md#leaderboard-function) Funktion zur Einbeziehung in eine Community-Site- oder Gruppenvorlage.
* [Komponente](enabling-leaderboard.md) &quot;Leaderboard&quot;, die spezielle Komponente der Funktion &quot;Leaderboard&quot;, zum Erstellen von Seiten.

