---
title: Moderieren von Community-Inhalten
seo-title: Moderating Community Content
description: Moderationskonzepte und -aktionen
seo-description: Moderation concepts and actions
uuid: a24d09e7-3260-4eec-844e-97e6849c94d8
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d11b8fc8-5e98-4a77-a536-d445ac88e1b3
role: Admin
exl-id: 9865b366-b9e5-40f3-8863-789ccfb792f5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1548'
ht-degree: 3%

---

# Moderieren von Community-Inhalten {#moderating-community-content}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Community-Inhalte, auch als benutzergenerierte Inhalte (UGC) bezeichnet, werden erstellt, wenn ein Mitglied (der angemeldete Site-Besucher) Inhalte von einer veröffentlichten Community-Site durch Interaktion mit einer der folgenden Community-Komponenten veröffentlicht:

* [Blog](blog-feature.md): Mitglieder posten Blogartikel oder Kommentare
* [Kalender](calendar.md): Mitglieder posten ein Kalenderereignis oder einen Kommentar
* [Kommentare](comments.md): Mitglieder posten Kommentare oder Antworten auf Kommentare
* [Forum](forum.md): Mitglieder posten ein neues Thema oder antworten auf ein Thema
* [Idee](ideation-feature.md): Mitglieder posten eine Idee oder einen Kommentar
* [Fragen und Antworten](working-with-qna.md): Mitglieder Fragen erstellen oder Fragen beantworten
* [Überprüfungen](reviews.md): Mitglieder posten einen Kommentar bei der Bewertung eines Elements

Die Moderation der benutzergenerierten Inhalte ist nützlich, um positive Beiträge zu erkennen und negative zu begrenzen (z. B. Spam und missbräuchliche Sprache). UGC kann in verschiedenen Umgebungen moderiert werden:

* [Massenmoderationskonsole](moderation.md)

   Auf die Moderationskonsole können Administratoren zugreifen und [Community-Moderatoren](users.md) in der öffentlichen Umgebung sowie von Administratoren in der Autorenumgebung. Dies ist möglich, wenn Community-Inhalte in einer [gemeinsamer Speicher](working-with-srp.md).

* [Kontextbezogene Moderation](in-context.md)

   Die Moderation in der Veröffentlichungsumgebung kann von Administratoren und Community-Moderatoren direkt auf der Seite durchgeführt werden, auf der der Inhalt veröffentlicht wurde.

## Moderationsaktionen {#moderation-actions}

Die Aktionen, die für veröffentlichte Inhalte (UGC) durchgeführt werden können, hängen von der Benutzeridentität und der Umgebung ab. Die folgende Tabelle verwendet die folgende Terminologie, um die verschiedenen Rollen entsprechend der Benutzeridentität zu beschreiben:

* `Admin`\
   Ein Benutzer, der Mitglied von [community-administrators](users.md) Gruppe
* `Moderator`
Mitglied eines [Community-Moderatoren](users.md#publishenvironmentusersandgroups) Gruppe (hat [Moderatorberechtigungen](in-context.md#moderatorpermissions))
* `Creator`\
   Der Benutzer, der den Inhalt veröffentlicht hat
* `Member`\
   Ein angemeldeter Benutzer ohne spezielle Berechtigungen
* `Visitor`
Anonymer Benutzer

<table> 
 <tbody>
  <tr>
   <td> </td> 
   <td><strong>Admin</strong></td> 
   <td><strong>Moderator</strong></td> 
   <td><strong>Ersteller</strong></td> 
   <td><strong>Mitglied</strong></td> 
   <td><strong>Besucher</strong></td> 
   <td><strong>Ereignis<br /> Ausgelöst</strong></td> 
   <td><strong>Vormoderiert</strong></td> 
  </tr>
  <tr>
   <td><strong>Bearbeiten/<br /> Löschen</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>Ausschneiden</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>Ablehnen</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>Close/<br /> Neu öffnen</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td>X<br /> </td> 
  </tr>
  <tr>
   <td><strong>Markierung/<br /> Markierung entfernen</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>Zulassen</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td>X</td> 
  </tr>
 </tbody>
</table>

### Bearbeiten/Löschen {#edit-delete}

Nachdem ein Beitrag erstellt wurde, kann er vom Ersteller, einem Administrator oder Community-Moderator bearbeitet oder gelöscht werden.

Wenn UGC gelöscht wird, wird es aus dem Repository entfernt und kann nicht wiederhergestellt werden.

### Ausschneiden {#cut}

Administratoren oder Community-Moderatoren können ein oder mehrere Forenthemen oder Fragen der Fragen der Frage von einem Ort zum anderen verschieben. Dies umfasst von einer Community-Site zu einer anderen Community-Site, sofern dasselbe Mitglied über Moderationsberechtigungen auf beiden Sites verfügt.

Durch Auswahl der Aktion &quot;Ausschneiden&quot;wird der Inhalt in die Zwischenablage kopiert. Es können mehrere Beiträge kopiert und als Gruppe an den neuen Speicherort verschoben werden.

![CUG](assets/cutugc.png) ![putbackugc](assets/putbackugc.png)

Wenn Inhalte in der Zwischenablage vorhanden sind, wird an der anderen Stelle neben &quot;Neuer Beitrag&quot;die Schaltfläche &quot;Einfügen&quot;angezeigt, wobei eine Zahl die Anzahl der Beiträge angibt, die eingefügt werden sollen. Die Schaltfläche &quot;Einfügen&quot;enthält eine Option zum Löschen der Zwischenablage, anstatt sie einzufügen.

![chlimage_1-218](assets/chlimage_1-218.png) ![chlimage_1-219](assets/chlimage_1-219.png)

### Ablehnen {#deny}

Ein Moderator kann verhindern, dass UGC auf der veröffentlichten Site sichtbar bleibt. Administratoren und Community-Moderatoren steht der Beitrag weiterhin zur Verfügung und wird als Spam bezeichnet.

### Schließen/erneut öffnen {#close-reopen}

Die Aktion Schließen bezieht sich auf den gesamten Diskussionsthread (ein Forenthema oder der ursprüngliche Kommentar) und enthält alle nachfolgenden Beiträge oder Antworten.

Wenn keine weiteren Antworten möglich sind, sind auch keine Moderationsaktionen zulässig.

Um Vorgänge auszuführen, muss das Thema oder der Kommentar erneut geöffnet werden.

Die Aktion Schließen/Neu öffnen kann von Administratoren oder Community-Moderatoren durchgeführt werden.

### Markierung/Markierung aufheben {#flag-unflag}

Die Kennzeichnung ist eine Möglichkeit für jedes angemeldete Mitglied, mit Ausnahme des Erstellers des Inhalts, anzugeben, dass ein Problem mit dem Inhalt eines Beitrags besteht. Nach der Kennzeichnung wird ein Symbol zum Aufheben der Markierung angezeigt, mit dem dasselbe Mitglied die Kennzeichnung des Inhalts aufheben kann.

Die kontextbezogene Moderation kann so konfiguriert werden, dass Mitglieder beim Kennzeichnen eines Beitrags einen Grund auswählen können. Die Liste der auswählbaren Flag-Gründe ist konfigurierbar, einschließlich der Angabe, ob ein benutzerdefinierter Grund angegeben werden kann. Der Flag-Grund wird mit der UGC gespeichert, der Grund Trigger jedoch keine bestimmte Aktion. Nur die Anzahl der Flags Trigger eine Benachrichtigung. Gekennzeichnete Inhalte werden als solche kommentiert, sodass Moderatoren darauf reagieren können.

Das System verfolgt alle Kennzeichnungen, die markiert sind, und den Grund der Kennzeichnung und sendet ein Ereignis, wenn der Schwellenwert erreicht ist. Wenn die UGC von einem Community-Moderator zugelassen wird, werden diese Flags archiviert. Nach der Erlaubnis und Archivierung würden bei nachfolgenden Flaggschiffen sie so archiviert, als gäbe es keine vorherigen Flaggings.

### Zulassen {#allow}

Die Aktion Zulassen ist eine Option für benutzergenerierte Inhalte, die in einem vormoderierten System gekennzeichnet, abgelehnt oder nicht genehmigt wurde. Mit der Aktion Zulassen werden alle gekennzeichneten oder abgelehnten/Spam-Status gelöscht und alle gekennzeichneten Daten werden archiviert.

## Allgemeine Moderationskonzepte {#common-moderation-concepts}

### Vormoderation {#premoderation}

Wenn UGC vormoderiert ist, wird der Beitrag erst dann auf der veröffentlichten Site angezeigt, wenn er durch eine Moderationsaktion genehmigt wurde. Während der Erstellung einer [Community-Site](sites-console.md), das Kontrollkästchen ` [Content is Premoderated](sites-console.md#moderation)` aktiviert die Vormoderation für die gesamte Site. Sobald Komponenten auf einer Seite platziert sind, können Komponenten, die Moderation unterstützen, mit einer Einstellung im Bearbeitungsdialogfeld für die Vormoderation konfiguriert werden:

* [Kommentare](comments.md) und [Bewertungen](reviews.md)

   on **[!UICONTROL Benutzermoderation]** Registerkarte, aktivieren **[!UICONTROL Vormoderation]**

* [Forum](forum.md), [Idee](ideation-feature.md), [Fragen und Antworten](working-with-qna.md)und [calendar](calendar.md) on **[!UICONTROL Einstellungen]** Registerkarte, aktivieren **[!UICONTROL Moderiert]**

### Spam-Erkennung {#spam-detection}

Die Spam-Erkennung ist eine Funktion der automatischen Moderation, die unerwünschte Teile gesendeter benutzergenerierter Inhalte herausfiltert, indem diese als Spam gekennzeichnet werden. Nach der Aktivierung wird anhand einer vorkonfigurierten Sammlung von Spam-Wörtern ermittelt, ob der vom Benutzer erstellte Inhalt Spam ist oder nicht. Die standardmäßigen Spam-Wörter finden Sie unter

`/libs/settings/community/sites/moderation/spamdetector-conf/profiles/spam_words.txt`.

Um jedoch die standardmäßigen Spam-Wörter anzupassen oder zu erweitern, erstellen Sie eine Reihe von Wörtern im Verzeichnis /apps, die der Struktur der standardmäßigen Spam-Wörter folgen, indem Sie [Overlay](overlay-comments.md).

Ein benutzergenerierter Beitrag (über alle Inhaltstypen hinweg, z. B. Blogs, Foren und Kommentare), der Spam-Wörter enthält, wird mit dem Text &quot;Dieser Beitrag wurde als Spam klassifiziert&quot;über dem Beitrag markiert.

Moderatoren können einen solchen Beitrag sehen und denselben markieren, um die Anzeige auf der Site zu ermöglichen oder zu verweigern. Moderationsaktionen für diese Beiträge können entweder kontextbezogen oder über die Massenmoderations-Benutzeroberfläche durchgeführt werden.

![Spamerkennung](assets/spamdetection.png)

Gehen Sie wie folgt vor, um die Spamerkennungs-Engine zu aktivieren:

1. Öffnen [Web-Konsole](http://localhost:4502/system/console/configMgr), indem Sie `/system/console/configMgr`.

1. Suchen **[!UICONTROL Automatische AEM Communities-Moderation]** und bearbeiten Sie sie.
1. Fügen Sie die `SpamProcess` eingeben.

![spamprocess](assets/spamprocess.png)

>[!NOTE]
>
>Die Spam-Erkennung wird nur für das englische Gebietsschema implementiert.

### Empfindung {#sentiment}

Das Sentiment wird anhand der Anzahl positiver und negativer Suchbegriffe ([Schlagwörter](#configuringwatchwords)) in einem Beitrag vorhanden ist (UGC).

Die Sentimentanalyse verwendet einen Satz vorkonfigurierter Regeln und berechnet das Sentiment der UGC. Die Standardregeln befinden sich unter `/libs/cq/workflow/components/workflow/social/sentiments/rules.`

Der Wert, den die Regeln generieren, reicht von 1 (alle negativen, keine positiven Wörter) bis 10 (alle positiven, keine negativen Wörter). Der Sentimentwert 5 ist ein neutrales Sentiment und der Standardwert.

Die in der Komponente /libs definierten Regeln sind:

* Regel 1: Setzen Sie den Wert auf 1, wenn keine positiven und mindestens ein negatives Wort vorhanden sind.
* Regel 2: Setzen Sie den Wert auf 10, wenn keine negativen Wörter vorhanden sind und mindestens ein positives Wort
* Regel 3: Setzen Sie den Wert auf 3, wenn es mehr negative Wörter als positive Wörter gibt.
* Regel 4: Setzen Sie den Wert auf 8, wenn es positivere Wörter als negative Wörter gibt.

Um Regeln zu überschreiben oder hinzuzufügen, erstellen Sie einen Regelsatz im Verzeichnis /apps entsprechend der Struktur der Standardregeln. Bearbeiten Sie die Sentimentkonfiguration, um den Speicherort der Regeln anzugeben.

Nach der Analyse wird das Sentiment mit dem UGC gespeichert.

Aus dem [Massenmoderationskonsole](moderation.md)kann UGC basierend darauf gefiltert und angezeigt werden, ob das Sentiment negativ, neutral oder positiv ist.

#### Schlagwörter {#watchwords}

AEM Communities bietet einen *Watchword-Analyzer *als einen Schritt im Prozess zur Bewertung [sentiment](#sentiment). Der Beitrag zum Sentimentwert, der von Schlagwörtern bereitgestellt wird, ist auf einen Vergleich von negativen und positiven Schlagwörtern, die im veröffentlichten Inhalt verwendet werden, sowie verbotenen Wörtern zurückzuführen.

#### Konfigurieren von Sentimenten und Schlagwörtern {#configure-sentiment-and-watchwords}

Die Liste positiver und negativer Schlagwörter kann wie die Sentimentregeln angepasst werden.

Die Standardliste der Schlagwörter kann als Eigenschaften eines Knotens im Repository eingegeben werden, ähnlich wie die Standardliste oder indem der Standard durch Konfiguration des OSGi-Dienstes überschrieben wird `sentimentprocess.name`mit der Wortliste.

Die **sentimentprocess.name** kann auch geändert werden, um auf den Speicherort eines benutzerdefinierten Satzes von Sentimentregeln zu verweisen.

So konfigurieren Sie Sentiment und Schlagwörter:

* Auf einer Autoreninstanz
* Als Administrator anmelden
* Öffnen [Web-Konsole](http://localhost:4502/system/console/configMgr)
* Suchen `sentimentprocess.name`
* Wählen Sie die Konfiguration aus, die im Bearbeitungsmodus geöffnet werden soll

![sentimentprocess](assets/sentimentprocess.png)

* **Positive Watchwords**
Eine kommagetrennte Liste von Wörtern, die zu einem positiven Sentiment beitragen, das die Standardwerte außer Kraft setzt. Der Standardwert ist eine leere Liste.

* **Negative Schlagwörter**
Eine kommagetrennte Liste von Wörtern, die zu einem negativen Sentiment beitragen, das die Standardwerte außer Kraft setzt. Der Standardwert ist eine leere Liste.

* **Expliziter Pfad zum Watchwords-Knoten**
Der Repository-Speicherort eines Knotens, der den Standard enthält 
`positive` und `negative` Eigenschaften, die standardmäßige Schlagwörter angeben. Der Standardwert ist `/libs/settings/community/watchwords/default`.

* **Sentimentregeln**
Der Repository-Speicherort der Regeln zur Berechnung des Sentiments basierend auf positiven und negativen Schlagwörtern. Der Standardwert ist 
`/libs/cq/workflow/components/workflow/social/sentiments/rules` (es ist jedoch kein Workflow mehr beteiligt).

Im Folgenden finden Sie ein Beispiel für einen benutzerdefinierten Eintrag für die standardmäßigen Schlagwörter, wenn `Explicit Path to Watchwords Node` auf `/libs/settings/community/watchwords/default`.

![crxde](assets/crxde.png)

### Moderatorberechtigungen {#moderator-permissions}

Die folgenden Berechtigungen werden, wenn sie derselben Ressource zugewiesen sind, zusammen als **`moderator permissions`**:

* `Read`
* **`Modify`**
* `Create`
* `Delete`
* `Replicate`
