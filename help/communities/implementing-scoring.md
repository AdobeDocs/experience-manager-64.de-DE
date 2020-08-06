---
title: Communities - Bewertung und Abzeichen
seo-title: Communities - Bewertung und Abzeichen
description: Mit AEM Communities-Scoring und -Kennzeichen können Sie Community-Mitglieder identifizieren und belohnen
seo-description: Mit AEM Communities-Scoring und -Kennzeichen können Sie Community-Mitglieder identifizieren und belohnen
uuid: ca6f22d6-f25d-4f26-b589-81d1f2c830f9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b19b3c24-82a0-468c-a077-9f3edb96afc9
tagskeywords: scoring, badging, badges, gamification
translation-type: tm+mt
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '2885'
ht-degree: 3%

---


# Communities - Bewertung und Abzeichen {#communities-scoring-and-badges}

## Übersicht {#overview}

Die AEM Communities-Funktion für Scoring und Abzeichen bietet die Möglichkeit, Community-Mitglieder zu identifizieren und zu belohnen.

Wichtigste Aspekte der Bewertung und Abzeichen sind:

* [Kennzeichen](#assign-and-revoke-badges) zur Identifizierung der Rolle eines Mitglieds in der Community zuweisen

* [Grundlegende Vergabe von Abzeichen](#enable-scoring) an Mitglieder zur Förderung ihrer Teilnahme (Menge der erstellten Inhalte)
* [Erweiterte Vergabe von Kennzeichen](advanced.md) zur Identifizierung von Mitgliedern als Experten (Qualität der erstellten Inhalte)

**Beachten Sie** , dass die Vergabe von Kennzeichen [nicht standardmäßig](implementing-scoring.md#main-pars-text-237875536)aktiviert ist.

>[!CAUTION]
>
>Die in der CRXDE Lite angezeigte Implementierungsstruktur kann sich ändern, sobald die Benutzeroberfläche verfügbar ist.

## Zeichen {#badges}

Kennzeichen werden unter dem Namen eines Mitglieds platziert, um entweder ihre Rolle oder ihr Ansehen in der Gemeinschaft anzugeben. Abzeichen können entweder als Bild oder als Name angezeigt werden. Wenn der Name als Bild angezeigt wird, wird er als alternativer Text für die Barrierefreiheit eingefügt.

Standardmäßig befinden sich Abzeichen im Repository unter

* /etc/community/badging/images

Wenn sie an einem anderen Ort gespeichert sind, sollten sie von allen gelesen werden können.

Die Kennzeichen werden in UGC differenziert, ob sie gemäß den Regeln zugewiesen wurden oder verdient wurden. Derzeit werden zugewiesene Kennzeichen als Text und verdiente Kennzeichen als Bild angezeigt.

### Benutzeroberfläche der Bademanagement {#badge-management-ui}

Die Communities [Badges-Konsole](badges.md) bietet die Möglichkeit, benutzerdefinierte Abzeichen hinzuzufügen, die für ein Mitglied angezeigt werden können, wenn es verdient (verliehen) oder eine bestimmte Rolle in der Community übernimmt (zugewiesen).

### Zugewiesene Abzeichen {#assigned-badges}

Rollenbasierte Abzeichen werden von einem Administrator entsprechend ihrer Rolle in der Community Mitgliedern zugewiesen.

Zugewiesene (und gewarnte) Abzeichen werden im ausgewählten [SRP](srp.md) gespeichert und sind nicht direkt zugänglich. Solange keine grafische Benutzeroberfläche verfügbar ist, können rollenbasierte Abzeichen nur mit Code oder cURL zugewiesen werden. Anweisungen zu cURL finden Sie im Abschnitt [Zuweisen und Sperren von Kennzeichen](#assign-and-revoke-badges).

In der Version sind drei rollenbasierte Abzeichen enthalten:

* Moderator

   `/etc/community/badging/images/moderator/jcr:content/moderator.png`

* Gruppenmanager

   `/etc/community/badging/images/group-manager/jcr:content/group-manager.png`

* Privilegiertes Mitglied

   `/etc/community/badging/images/privileged-member/jcr:content/privileged-member.png`

![chlimage_1-366](assets/chlimage_1-366.png)

### Ausgegebene Kennzeichen {#awarded-badges}

Belohnungsbasierte Abzeichen werden vom Bewertungsdienst an Mitglieder der Gemeinde vergeben, die auf Regeln beruhen, die für ihre Aktivität in der Gemeinde gelten.

Damit Kennzeichen als Belohnung für Aktivität erscheinen, müssen zwei Dinge geschehen:

* Die Kennzeichnung muss für die Feature-Komponente [aktiviert](#enable-badges-for-component) sein.
* Auf die Seite (oder den Vorläufer), auf der die Komponente platziert wird, müssen Scoring- und Kennzeichnungsregeln [angewendet](#apply-rules-to-content) werden

In der Version sind drei belohnungsbasierte Abzeichen enthalten:

* Gold

   `/etc/community/badging/images/gold-badge/jcr:content/gold.png`

* Silber

   `/etc/community/badging/images/silver-badge/jcr:content/silver.png`

* Bronze

   `/etc/community/badging/images/bronze-badge/jcr:content/bronze.png`

![chlimage_1-367](assets/chlimage_1-367.png)

>[!NOTE]
>
>Bewertungsregeln können so konfiguriert werden, dass negative Punkte für Beiträge zugewiesen werden, die als unangemessen gekennzeichnet sind und sich daher auf den Ergebniswert auswirken. Sobald ein Abzeichen jedoch verdient wurde, wird es aufgrund von Änderungen der Punktreduzierung oder der Bewertungsregel nicht automatisch entfernt.
>
>Zuerkannte Abzeichen können wie zugewiesene Abzeichen widerrufen werden. Siehe Abschnitt [Abzeichen zuweisen und Sperren](#assign-and-revoke-badges) . Zukünftige Verbesserungen beinhalten eine Benutzeroberfläche zur Verwaltung der Abzeichen der Mitglieder.

### Benutzerdefinierte Abzeichen {#custom-badges}

Benutzerdefinierte Kennzeichen können mit der [Badges-Konsole](badges.md) installiert und entweder zugewiesen oder in Kennzeichnungsregeln angegeben werden.

Bei der Installation über die Badges-Konsole werden benutzerdefinierte Abzeichen automatisch in die Veröffentlichungs-Umgebung repliziert.

## Bewertung aktivieren {#enable-scoring}

Die Bewertung ist nicht standardmäßig aktiviert. Die grundlegenden Schritte zur Einrichtung und Aktivierung der Bewertung und Vergabe von Abzeichen sind:

* Identifizieren Sie die Regeln für Ertragspunkte ([Bewertungsregeln](#scoring-rules)).
* Weisen Sie für Punkte, die nach Bewertungsregeln gesammelt werden, [Abzeichen](#badges) zu ([Kennzeichnungsregeln](#badging-rules))

* [Scoring- und Kennzeichnungsregeln auf eine Community-Site anwenden](#apply-rules-to-content)
* [Aktivieren der Markierung für Community-Funktionen](#enable-badges-for-component)

Siehe Abschnitt [Schnelltest](#quick-test) , um die Bewertung für eine Community-Site mit den standardmäßigen Scoring- und Kennzeichnungsregeln für Foren und Kommentare zu aktivieren.

### Regeln auf Inhalt anwenden {#apply-rules-to-content}

Um die Bewertung und Abzeichen zu aktivieren, fügen Sie die Eigenschaften `scoringRules` und `badgingRules`zu einem beliebigen Knoten in der Inhaltsstruktur der Site hinzu.

Wenn die Site bereits veröffentlicht wurde, veröffentlichen Sie die Site nach Anwendung aller Regeln und aktivierenden Komponenten erneut.

Die Regeln, die für eine badging-fähige Komponente gelten, sind die Regeln für die aktuelle Node oder deren Vorgänger.

Wenn der Knoten vom Typ `cq:Page` (empfohlen) ist, fügen Sie mithilfe von CRXDE|Lite die Eigenschaften seinem `jcr:content`Knoten hinzu.

| **Eigenschaft** | **Typ** | **Beschreibung** |
|---|---|---|
| badgingRules | Zeichenfolge[] | eine Array-Liste von [Kennzeichnungsregeln](#badging-rules) |
| scoringRules | Zeichenfolge[] | eine Array-Liste von [Bewertungsregeln](#scoring-rules) |

>[!NOTE]
>
>Wenn eine Bewertungsregel keine Auswirkungen auf die Zuweisung von Kennzeichen zu haben scheint, stellen Sie sicher, dass die Bewertungsregel nicht von der scoringRules-Eigenschaft der Kennzeichnungsregel blockiert wurde. Siehe Abschnitt mit dem Titel [Regeln](#badging-rules)für die Kennzeichnung.

### Kennzeichen für Komponente aktivieren {#enable-badges-for-component}

Die Scoring- und Bading-Regeln werden nur für Instanzen von Komponenten angewendet, die das Abzeichnen durch Bearbeiten der Komponentenkonfiguration im [Authoring-Modus](author-communities.md)aktiviert haben.

Eine boolesche Eigenschaft aktiviert `allowBadges`bzw. deaktiviert die Anzeige von Kennzeichen für eine Komponenteninstanz. Es kann im [Komponentenbearbeitungsdialogfeld](author-communities.md) für Forum-, QnA- und Kommentarkomponenten konfiguriert werden, indem ein Kontrollkästchen mit der Bezeichnung **Anzeigemarke aktiviert wird**.

#### Beispiel: allowBadges for Forum-Komponenteninstanz {#example-allowbadges-for-forum-component-instance}

![chlimage_1-368](assets/chlimage_1-368.png)

>[!NOTE]
>
>Jede Komponente kann überlagert werden, um Abzeichen mit dem HBS-Code anzuzeigen, der in Foren, QnA und Kommentaren zu finden ist.

## Bewertungsregeln {#scoring-rules}

Bewertungsregeln sind die Grundlage für die Verleihung von Abzeichen.

Jede Bewertungsregel ist ganz einfach eine Liste einer oder mehrerer Unterregeln. Bewertungsregeln werden auf den Inhalt der Community-Site angewendet, um die Regeln zu identifizieren, die bei Aktivierung von Kennzeichen angewendet werden.

Bewertungsregeln werden geerbt, jedoch nicht additiv. Beispiel:

* Wenn page2 Scoring rule2 enthält und seine Vorgängerseite1 Scoring Rule1 enthält
* Eine Aktion auf einer Komponente &quot;page2&quot;ruft sowohl Regel1 als auch Regel2 auf
* Wenn beide Regeln anwendbare Unterregeln für dasselbe enthalten `topic/verb`:

   * Nur die Unterregel aus Regel 2 wirkt sich auf das Ergebnis aus
   * Die Ergebnisse beider Unterregeln werden nicht zusammen addiert

Wenn es mehr als eine Bewertungsregel gibt, werden die Ergebnisse für jede Regel separat beibehalten.

Bewertungsregeln sind Nodes vom Typ `cq:Page` mit Eigenschaften auf dem `jcr:content`Knoten, die die Liste der Unterregeln angeben, die sie definieren.

Scores werden in SRP gespeichert.

>[!NOTE]
>
>Best Practice: Benennen Sie jede Bewertungsregel eindeutig.
>
>Die Namen von Bewertungsregeln sollten global eindeutig sein. sie sollten nicht mit demselben Namen enden.
>
>Ein Beispiel dafür, was *nicht* zu tun ist:\
>/etc/community/scoring/rules/site1/forums-scoring\
>/etc/community/scoring/rules/site2/forums-scoring

### Bewertungsunterregeln {#scoring-sub-rules}

Die Bewertungsunterregeln enthalten die Eigenschaften, die die Werte für die Teilnahme an der Community detailliert angeben.

Jede Bewertungsunterregel identifiziert

* Welche Aktivitäten werden verfolgt?
* Welche spezifische Gemeinschaftsfunktion ist betroffen?
* Wie viele Punkte wurden vergeben?

Standardmäßig werden Punkte an das Mitglied vergeben, das aktiv ist, es sei denn, die Unterregel legt fest, dass der Eigentümer des Inhalts die Punkte erhält ( `forOwner`).

Jede Unterregel kann in einer oder mehreren Bewertungsregeln enthalten sein.

Der Name der Unterregel folgt in der Regel dem Muster der Verwendung eines *Subjekts, Objekts* und *Verb*. Beispiel:

* member-comment-create
* member-receive-Votum

Unter-Regeln sind Nodes vom Typ `cq:Page` mit Eigenschaften auf ihrem `jcr:content`Knoten, die die [Verben und Themen](#topics-and-verbs) angeben.

<table> 
 <tbody> 
  <tr> 
   <th>Eigenschaft</th> 
   <th>Typ</th> 
   <th> Wert Beschreibung</th> 
  </tr> 
  <tr> 
   <td><i><code>VERB</code></i></td> 
   <td>Long</td> 
   <td> 
    <ul> 
     <li>erforderlich; das Verb entspricht einer Ereignis-Aktion</li> 
     <li>Es muss mindestens eine Verb-Eigenschaft vorhanden sein</li> 
     <li>das Verb muss in allen UPPERCASE eingegeben werden</li> 
     <li>Es können mehrere Eigenschaften von Verb vorhanden sein, jedoch keine Duplikat</li> 
     <li>der Wert ist der Wert, der für dieses Ereignis gelten soll</li> 
     <li>der Wert kann positiv oder negativ sein</li> 
     <li>Eine Liste der Verben, die in der Version unterstützt werden, finden Sie im Abschnitt <a href="#topics-and-verbs">Themen und Verben</a> .</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>topics</code></td> 
   <td>Zeichenfolge[]</td> 
   <td> 
    <ul> 
     <li>optional; beschränkt Unterregel auf Community-Komponenten, die nach Ereignis-Themen identifiziert werden</li> 
     <li>falls angegeben: value ist eine Zeichenfolge mit mehreren Werten für Ereignis-Themen</li> 
     <li>Eine Liste der Themen in der Version finden Sie im Abschnitt <a href="#topics-and-verbs">Themen und Verben</a> .</li> 
     <li>ist standardmäßig auf alle Themen anzuwenden, die mit dem bzw. den Verb(en) verbunden sind</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>forOwner</code></td> 
   <td>Boolesch</td> 
   <td> 
    <ul> 
     <li>optional; nicht relevant, wenn ein Mitglied mit Inhalten handelt, die ihm gehören</li> 
     <li>Wenn "true", wird das Ergebnis auf den Eigentümer des Inhalts angewendet, auf den reagiert wird</li> 
     <li>Wenn false, Punktzahl auf die Aktion des Mitglieds anwenden</li> 
     <li>default ist false</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>scoringType</code></td> 
   <td>Zeichenfolge</td> 
   <td> 
    <ul> 
     <li>optional; erkennt die Bewertungsmaschine</li> 
     <li>if "basic" gibt die Bewertungsmaschine basierend auf der Menge an 
      <ul> 
       <li>in der Version enthalten</li> 
      </ul> </li> 
     <li>if "advanced", gibt die Bewertungsmaschine auf der Grundlage von Qualität und Menge an 
      <ul> 
       <li>erfordert ein <a href="advanced.md">zusätzliches Paket</a></li> 
      </ul> </li> 
     <li>default ist "basic"</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

### Einbezogene Bewertungsregeln und Unterregeln {#included-scoring-rules-and-sub-rules}

In der Version sind zwei Bewertungsregeln für die [Forenfunktion](functions.md#forum-function) enthalten (eine für die Foren- und Kommentarkomponenten der Funktion &quot;Forum&quot;):

1. /etc/community/scoring/rules/comments-scoring

   * subRules[] =

      /etc/community/scoring/rules/sub-rules/member-comment-create

      /etc/community/scoring/rules/sub-rules/member-receive-Votum

      /etc/community/scoring/rules/sub-rules/member-give

      /etc/community/scoring/rules/sub-rules/member-is-moderated

1. /etc/community/scoring/rules/forums-scoring

   * subRules[] =

      /etc/community/scoring/rules/sub-rules/member-forum-create

      /etc/community/scoring/rules/sub-rules/member-receive-Votum

      /etc/community/scoring/rules/sub-rules/member-give

      /etc/community/scoring/rules/sub-rules/member-is-moderated

**Hinweise:**

* Sowohl `rules`als auch `sub-rules` Knoten sind vom Typ cq:Page

* `subRules`ist ein Attribut des Typs String[] auf der `jcr:content` Knoten der Regel

* `sub-rules` kann für verschiedene Bewertungsregeln freigegeben werden
* `rules`sollte sich in einem Repository mit Leserechte für alle befinden

   * Regelnamen müssen unabhängig vom Ort eindeutig sein

### Aktivieren benutzerdefinierter Bewertungsregeln {#activating-custom-scoring-rules}

Änderungen oder Ergänzungen, die an Bewertungsregeln oder Unterregeln in der Autorenregel vorgenommen wurden, müssen bei der Veröffentlichung installiert werden.

## Abstandsregeln {#badging-rules}

Kennzeichnungsregeln verknüpfen Bewertungsregeln mit Kennzeichen, indem sie Folgendes angeben:

* Welche Bewertungsregel
* Das Ergebnis, das erforderlich ist, um eine bestimmte Markierung erhalten zu werden

Kennzeichnungsregeln sind Nodes vom Typ `cq:Page` mit Eigenschaften auf ihrem `jcr:content`Knoten, die Bewertungsregeln mit Bewertungen und Abzeichen korrelieren.

Die Kennzeichnungsregeln bestehen aus einer obligatorischen `thresholds`Eigenschaft, bei der es sich um eine geordnete Liste von Kennzahlen handelt, die Kennzeichen zugeordnet sind. Die Ergebnisse müssen in zunehmendem Wert angeordnet werden. Beispiel:

* `1|/etc/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * Für den Gewinn von 1 Punkt wird ein Bronzemarkt erwartet

* `60|/etc/community/badging/images/silver-badge/jcr:content/silver.png`

   * Ein Silberabzeichen wird vergeben, wenn 60 Punkte gesammelt wurden

* `80|/etc/community/badging/images/gold-badge/jcr:content/gold.png`

   * Wenn 80 Punkte gesammelt wurden, wird ein Goldabzeichen erwartet

Kennzeichnungsregeln werden mit Bewertungsregeln gepaart, die bestimmen, wie Punkte akkumuliert werden. Siehe Abschnitt Regeln [auf Inhalt](#apply-rules-to-content)anwenden.

Die `scoringRules`Eigenschaft einer Kennzeichnungsregel schränkt lediglich ein, welche Bewertungsregeln mit dieser speziellen Kennzeichnungsregel verknüpft werden können.

>[!NOTE]
>
>Optimale Vorgehensweise: Sie können individuelle Abzeichen für jede AEM Website erstellen.

![chlimage_1-369](assets/chlimage_1-369.png)

<table> 
 <tbody> 
  <tr> 
   <th>Eigenschaft</th> 
   <th>Typ</th> 
   <th>Wert Beschreibung</th> 
  </tr> 
  <tr> 
   <td>Schwellenwerte</td> 
   <td>Zeichenfolge[]</td> 
   <td><em>(erforderlich)</em> Eine Zeichenfolge mit mehreren Werten im Format 'number|path' 
    <ul> 
     <li>number = score</li> 
     <li>| = vertikaler Zeilenabstand (U+007C)</li> 
     <li>path = vollständiger Pfad zur Abzeichen-Bildressource</li> 
    </ul> Die Zeichenfolgen müssen so angeordnet sein, dass die Zahlen an Wert zunehmen und zwischen Zahl und Pfad kein Leerzeichen angezeigt wird.<br /> Beispieleintrag:<br /> <code>80|/etc/community/badging/images/gold-badge/jcr:content/gold.png</code></td> 
  </tr> 
  <tr> 
   <td>badgingType</td> 
   <td>Zeichenfolge</td> 
   <td><em>(optional)</em> Identifiziert die Bewertungsmaschine als "Basis"oder "Fortgeschritten". Wenn die erweiterte Scoring-Engine gewünscht wird, finden Sie weitere Informationen unter <a href="advanced.md">Erweiterte Scoring- und Badges-Funktion</a>. Der Standardwert ist "basic".</td> 
  </tr> 
  <tr> 
   <td> 
    <code>scoringRules </code></td> 
   <td>Zeichenfolge[]</td> 
   <td>(<em>optional</em>) Eine Zeichenfolge mit mehreren Werten, mit der die Kennzeichnungsregel auf durch die Bewertungsregeln identifizierte Ereignis beschränkt wird</td> 
  </tr> 
 </tbody> 
</table>

### Einbezogene Kennzeichnungsregeln {#included-badging-rules}

In der Version sind zwei Kennzeichnungsregeln enthalten, die den Bewertungsregeln für [Foren und Kommentare entsprechen](#includedscoringrules).

* /etc/community/badging/rules/comments-badging
* /etc/community/badging/rules/forums-badging

**Hinweise:**

* `rules` Nodes vom Typ cq:Page
* `rules`sollte sich in einem Repository mit Leserechte für alle befinden

   * Regelnamen müssen unabhängig vom Ort eindeutig sein

### Aktivieren benutzerdefinierter Kennzeichnungsregeln {#activating-custom-badging-rules}

Änderungen oder Ergänzungen an den Kennzeichnungsregeln oder Bildern, die in der Authoring-Umgebung vorgenommen wurden, müssen bei der Veröffentlichung installiert werden.

## Zuteilen und Entziehen von Abzeichen {#assign-and-revoke-badges}

Abzeichen können Mitgliedern entweder über die [Mitgliederkonsole](members.md#badges-tab) oder programmgesteuert mithilfe von cURL-Befehlen zugewiesen werden.

Die folgenden cURL-Befehle zeigen, was für eine HTTP-Anforderung zum Zuweisen und Sperren von Kennzeichen erforderlich ist. Das Basisformat lautet:

cURL -i -X POST -H *header* -u *signin * -F *operation * -F *badge * *member-Profil-url*

*header* = &quot;Accept:application/json&quot;\
Benutzerdefinierter Header zum Übergeben an den Server (erforderlich)

*signin* = administrator-id:password\
Beispiel: admin:admin

*operation* = &quot;:operation=social:assignBadge&quot; OR &quot;:operation=social:deleteBadge&quot;

*badge* = &quot;badgeContentPath=*badge-image-file*&quot;

*badge-image-file* = der Speicherort der Badge-Bilddatei im Repository\
Beispiel: /etc/community/badging/images/moderator/jcr:content/moderator.png

*member-Profil-url* = Endpunkt für das Profil des Mitglieds beim Veröffentlichen\
Beispiel: https://&lt;server>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>Die *Member-Profil-URL*
>
>* Kann auf eine Autoreninstanz verweisen, wenn der [Tunneldienst](users.md#tunnel-service) aktiviert ist
>* Kann ein undurchsichtiger, zufälliger Name sein - siehe Checkliste für die [Sicherheit](../../help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) hinsichtlich der zulässigen IDs

>



### Beispiele: {#examples}

#### Moderatorenabzeichen zuweisen {#assign-a-moderator-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

#### Sperren eines zugewiesenen Silber-Kennzeichens {#revoke-an-assigned-silver-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:deleteBadge" -F "badgeContentPath=/etc/community/badging/images/silver/jcr:content/silver.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

>[!NOTE]
>
>Die Verwendung von cURL zum Zuweisen und Sperren von Abzeichen funktioniert für jedes Abzeichen-Bild, aber wenn sie anstelle von verdient zugewiesen werden, werden sie als zugewiesene Abzeichen markiert und entsprechend behandelt.

## Bewertung und Abzeichen für benutzerdefinierte Komponenten {#scoring-and-badges-for-custom-components}

Scoring- und Badging-Regeln können für benutzerdefinierte Komponenten erstellt werden, indem die für die Komponente erstellten Ereignis-Themen mit Verben verknüpft werden.

## Themen und Verben {#topics-and-verbs}

Wenn Mitglieder mit Communities-Funktionen interagieren, werden Ereignis gesendet, die asynchrone Listener auslösen können, z. B. Benachrichtigungen und Scoring.

Die SocialEvent-Instanz einer Komponente zeichnet die Ereignis auf, `actions`die für eine `topic`Komponente auftreten. Das SocialEvent enthält eine Methode, um eine mit der Aktion `verb`verbundene Aktion zurückzugeben. Es gibt eine *n-1* Beziehung zwischen `actions`und `verbs`.

Für die bereitgestellten Communities-Komponenten beschreiben die folgenden Tabellen die `verbs`definierten für jede `topic`verfügbare Komponente, die in [Bewertungsunterregeln](#scoring-sub-rules)verwendet werden kann.

>[!NOTE]
>
>Eine neue boolesche Eigenschaft aktiviert bzw. deaktiviert `allowBadges`die Anzeige von Kennzeichen für eine Komponenteninstanz. Es kann in aktualisierten Dialogfeldern [zum Bearbeiten von](author-communities.md) Komponenten mithilfe eines Kontrollkästchens mit der Bezeichnung **Anzeigemarke** konfiguriert werden.

**[Kalenderkomponente](calendar.md)**SocialEvent`topic`= com/adobe/cq/social/calendar

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt ein Ereignis im Kalender |
| HINZUFÜGEN | Mitgliederkommentare für ein Kalendertool |
| UPDATE | Ereignis oder Kommentar des Mitglieds wird bearbeitet |
| DELETE | Ereignis oder Kommentar des Mitglieds wird gelöscht |

**[Kommentarkomponente](comments.md)**SocialEvent`topic`= com/adobe/cq/social/comment

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Kommentar |
| HINZUFÜGEN | Antworten des Mitglieds auf Kommentar |
| UPDATE | Kommentar des Mitglieds wird bearbeitet |
| DELETE | Kommentar des Mitglieds wird gelöscht |

**[File Library Component](file-library.md)**SocialEvent`topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Ordner |
| ANLAGE | Mitglied lädt eine Datei hoch |
| UPDATE | Mitglied aktualisiert einen Ordner oder eine Datei |
| DELETE | löscht einen Ordner oder eine Datei |

**[Forum Component](forum.md)**SocialEvent`topic`= com/adobe/cq/social/forum

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Forumthema |
| HINZUFÜGEN | Mitgliederantworten zum Forenthema |
| UPDATE | Forenthema oder Antwort des Mitglieds wird bearbeitet |
| DELETE | Forenthema oder Antwort des Mitglieds wird gelöscht |

**[Protokoll Component](blog-feature.md)**SocialEvent`topic`= com/adobe/cq/social/Protokoll

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Blog-Artikel |
| HINZUFÜGEN | Kommentare zu einem Blog-Artikel |
| UPDATE | Blog-Artikel oder Kommentar des Mitglieds wird bearbeitet |
| DELETE | Blog-Artikel oder Kommentar des Mitglieds wird gelöscht |

**[QnA Component](working-with-qna.md)**SocialEvent`topic`= com/adobe/cq/social/qna

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt eine QnA-Frage |
| HINZUFÜGEN | Mitglied erstellt eine QnA-Antwort |
| UPDATE | Frage oder Antwort des Mitglieds zur Servicequalität des Mitglieds wird bearbeitet |
| SELECT | Antwort des Mitglieds ausgewählt |
| AUSWAHL aufheben | Die Antwort des Mitglieds wird deaktiviert |
| DELETE | Frage oder Antwort des Mitglieds zur Servicequalitätsprüfung wird gelöscht |

**[Reviews Component](reviews.md)**SocialEvent`topic`= com/adobe/cq/social/review

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Review |
| UPDATE | Überprüfung des Mitglieds wird bearbeitet |
| DELETE | Überprüfung des Mitglieds wird gelöscht |

**[Bewertungskomponente](rating.md)**SocialEvent`topic`= com/adobe/cq/social/tally/rating

| **Verb** | **Beschreibung** |
|---|---|
| HINZUFÜGEN | Der Inhalt des Mitglieds wurde bewertet |
| RATING ENTFERNEN | der Inhalt des Mitglieds wurde heruntergesetzt |

**[Abstimmungskomponente](voting.md)**SocialEvent`topic`= com/adobe/cq/social/tally/stimmberechtigt

| **Verb** | **Beschreibung** |
|---|---|
| HINZUFÜGEN ABSTIMMUNG | Der Inhalt des Mitglieds wurde abgestimmt |
| ABSTIMMUNG ENTFERNEN | Inhalt des Mitglieds wurde abgelehnt |

**Moderationsaktivierte Komponenten** SocialEvent `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschreibung** |
|---|---|
| DENY | Inhalt des Mitglieds wird verweigert |
| FLAG-AS-INAPPROPRIATE | Inhalt des Mitglieds wird markiert |
| UNFLAG-AS-INAPPROPRIATE | Der Inhalt des Mitglieds ist unmarkiert |
| AKZEPT | Der Inhalt des Mitglieds wird vom Moderator genehmigt |
| SCHLIESSEN | Mitglied schließt Kommentar zu Bearbeitungen und Antworten |
| OPEN | Mitglied öffnet Kommentar erneut |

### Ereignis für benutzerdefinierte Komponenten {#custom-component-events}

Bei einer benutzerdefinierten Komponente wird ein SocialEvent instanziiert, um die Ereignis der Komponente als `actions`die für eine `topic`Komponente auftretenden Ereignisse aufzuzeichnen.

Um die Bewertung zu unterstützen, muss das SocialEvent die Methode überschreiben, `getVerb()` sodass für jede Methode ein passender Wert zurückgegeben `verb`wird `action`. Die für eine Aktion `verb` zurückgegebene kann eine häufig verwendete (z. B. `POST`) oder eine für die Komponente spezialisierte (z. B. `ADD RATING`) Aktion sein. Es gibt eine *n-1* Beziehung zwischen `actions`und `verbs`.

## Fehlerbehebung {#troubleshooting}

### Abzeichen werden nicht angezeigt {#badges-are-not-appearing}

Wenn für den Inhalt der Website Scoring- und Kennzeichnungsregeln angewendet wurden, für keine Aktivität Kennzeichen angezeigt werden, stellen Sie sicher, dass für die Komponenteninstanz Kennzeichen aktiviert wurden.

Siehe [Aktivieren von Abzeichen für Komponenten](#enable-badges-for-component).

### Bewertungsregel hat keine Auswirkung {#scoring-rule-has-no-effect}

Wenn für den Inhalt der Website Scoring- und Kennzeichnungsregeln angewendet wurden und für einige Aktionen, aber nicht für andere Kennzeichen vergeben werden, überprüfen Sie, ob die Kennzeichnungsregel die anzuwendenden Bewertungsregeln nicht eingeschränkt hat.

Siehe auch `scoringRules`Eigenschaft von [Badging Rules](#badging-rules).

### Groß-/Kleinschreibung {#case-sensitive-typo}

Bei den meisten Eigenschaften und Werten, insbesondere bei den Verben, wird die Groß-/Kleinschreibung beachtet. Verbs müssen in einer Scoring-Unterregel als alle UPPERCASE verwendet werden.

Wenn die Funktion nicht wie erwartet funktioniert, stellen Sie sicher, dass die Daten korrekt eingegeben wurden.

## Schnelltest {#quick-test}

Mithilfe der Website &quot;Erste [Schritte - Tutorial](getting-started.md) &quot;(Interaktion) können Sie schnell Scoring und Abzeichen ausprobieren:

* CRXDE Lite beim Autor aufrufen
* Gehen Sie zur Basisseite:

   * /content/sites/engagement/de/jcr:content

* Hinzufügen der badgingRules-Eigenschaft:

   * **Name**: `badgingRules`
   * **Typ**: `String`
   * Wählen Sie **[!UICONTROL Multi]**
   * Auswählen **[!UICONTROL Hinzufügen]**
   * Geben Sie Folgendes ein `/etc/community/badging/rules/forums-badging`
   * Wählen Sie nun eine der folgenden Optionen aus `+`
   * Geben Sie Folgendes ein `/etc/community/badging/rules/comments-badging`
   * Wählen Sie **[!UICONTROL OK]** aus

* Hinzufügen der Eigenschaft scoringRules:

   * **Name**: `scoringRules`
   * **Typ**: `String`
   * Wählen Sie **[!UICONTROL Multi]**
   * Auswählen **[!UICONTROL Hinzufügen]**
   * Geben Sie Folgendes ein `/etc/community/scoring/rules/forums-scoring`
   * Wählen Sie nun eine der folgenden Optionen aus `+`
   * Geben Sie Folgendes ein `/etc/community/scoring/rules/comments-scoring`
   * Wählen Sie **[!UICONTROL OK]** aus

* Select **[!UICONTROL Save All]**

![chlimage_1-370](assets/chlimage_1-370.png)

Stellen Sie dann sicher, dass die Forum- und Kommentarkomponenten die Anzeige von Abzeichen zulassen:

* Wieder mit CRXDE Lite
* Zur Forumkomponente navigieren

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* Hinzufügen boolesche Eigenschaft allowBadges, falls erforderlich, und stellen Sie sicher, dass sie wahr ist

   * **Name**: `allowBadges`
   * **Typ**: `Boolean`
   * **Wert**: `true`

![chlimage_1-371](assets/chlimage_1-371.png)

Veröffentlichen Sie anschließend [erneut](sites-console.md#publishing-the-site) die Community-Site.

Schließlich

* Zur Komponente in der Veröffentlichungsinstanz navigieren
* Melden Sie sich als Community-Mitglied an (z. B. weston.mccall@dodgit.com)
* Neues Forenthema posten
* Die Seite muss aktualisiert werden, damit das Abzeichen angezeigt wird

   * Abmelden und sich als anderes Community-Mitglied anmelden (z. B. aaron.mcdonald@mailinator.com)

* Forum auswählen

Dies sollte dem Community-Mitglied ein Bronzemarke mit seinem Forenbeitrag sichtbar machen, da der erste Schwellenwert der ersten Regel, die das Forums-Abzeichen vorgibt, ein Wert von 1 ist.

![Bronzebadse](assets/bronzebadge.png)

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Scoring and Badges Essentials](configure-scoring.md) page for developers.

Informationen zur erweiterten Scoring-Engine finden Sie unter [Erweiterte Scoring- und Badges-Funktion](advanced.md).

Die konfigurierbare Leaderboard- [Komponente](enabling-leaderboard.md) und - [Funktion](functions.md#leaderboard-function) vereinfacht die Anzeige von Mitgliedern und deren Ergebnissen auf einer Community-Site.
