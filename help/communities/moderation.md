---
title: Moderationskonsole
seo-title: Moderationskonsole
description: Zugriff auf die Moderationskonsole
seo-description: Zugriff auf die Moderationskonsole
uuid: 920124b9-af6f-4622-adb6-b8e294c5607d
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 6c405543-e339-4916-aa0f-b61d0b798cf3
translation-type: tm+mt
source-git-commit: f78f83ef3b9373bcbee3e5179a9bbec4d9462255

---


# Moderation Console {#moderation-console}

In AEM Communities ist eine Massenmoderation [von Community-Inhalten](moderate-ugc.md) sowohl in der Autor- als auch in der Veröffentlichungsumgebung durch Administratoren und Community-Moderatoren möglich (vertrauenswürdige Community-Mitglieder, die als Moderatoren zugewiesen sind).

Administratoren und Community-Moderatoren können auch [kontextbezogene Moderationen](in-context.md) in der Veröffentlichungsumgebung durchführen.

Eine Funktion aller [Community-Sites](sites-console.md) ist ein `Administration`Menüpunkt, der Benutzern mit Administratorrechten zur Verfügung steht. Der `Administration`Link bietet Zugriff auf die Moderationskonsole.

In der Moderationskonsole haben Administratoren und Community-Moderatoren Zugriff auf alle benutzergenerierten Inhalte (UGC), für die sie über die Berechtigung zum Moderieren verfügen. Wenn es zulässig ist, mehrere Sites zu moderieren, ist es möglich, Beiträge über alle Sites hinweg anzuzeigen oder nach ausgewählten Communities-Sites zu filtern.

Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Die Moderationskonsole unterstützt:
* Massenmäßige Moderationsaufgaben durchführen
* UGC-Suche
* Ansicht von UGC-Details
* Ansicht von UGC-Autorendetails

Nur bei der Anmeldung als Administrator oder als Mitglied mit ` [moderator permissions](in-context.md#identifyingtrustedmembers)`dürfen Moderationsaufgaben ausgeführt werden.

## Zugriff auf Veröffentlichungsumgebung {#publish-environment-access}

Der Zugriff auf die Moderationskonsole von einer veröffentlichten Community-Site erfolgt über einen Link &quot;Administration&quot;, der angezeigt wird, wenn ein Community-Moderator angemeldet ist.

![publishweretail](assets/publishweretail.png)

Über den Link Administration wird die Moderationskonsole angezeigt:

![moderationconsole-publish](assets/moderationconsole-publish.png)

## Zugriff auf Autorenumgebung {#author-environment-access}

In der Autorenumgebung zur Moderationskonsole

* Aus globaler Navigation: **[!UICONTROL Navigation > Communities > Moderation]**

Moderationsaufgaben können nur ausgeführt werden, wenn sie als Administrator oder als Mitglied mit angemeldet ` [moderator permissions](in-context.md#identifyingtrustedmembers)`sind. Der einzige Community-Inhalt, der angezeigt wird, ist der, den das angemeldete Mitglied moderieren darf.

>[!NOTE]
>
>UGC aus der Veröffentlichungsumgebung ist nur beim Autor sichtbar, wenn das ausgewählte SRP einen gemeinsamen Store implementiert. Der Standardspeicher ist beispielsweise JSRP, kein gemeinsamer Speicher für Autoren und Veröffentlichungen. Weitere Informationen finden Sie unter [Community-Inhaltsspeicher](working-with-srp.md).

![moderationconsoleauthor](assets/moderationconsoleauthor.png)

## Benutzeroberfläche der Moderationskonsole {#moderation-console-ui}

Abgesehen von der linken Navigationsleiste (die beim Autor, aber nicht bei der Veröffentlichung angezeigt wird) verfügt die Moderations-Benutzeroberfläche über die folgenden Hauptbereiche:

* **[Navigationsleiste oben](#top-navigation-bar)**
* **[Symbolleiste](#toolbar)**
* **[Inhaltsbereich](#content-area)**

### Top Navigation Bar {#top-navigation-bar}

Die obere Navigationsleiste ist für alle Konsolen konstant. Weitere Informationen finden Sie unter [Grundlegende Handhabung](../../help/sites-authoring/basic-handling.md).

### Symbolleiste {#toolbar}

Die Symbolleiste, die sich unterhalb der oberen Navigationsleiste befindet, bietet den folgenden Umschalter auf der linken Seite:

* [Die Filterleiste](moderation.md#filter-rail) öffnet eine Leiste, die eine Auswahl von Eigenschaften zum Filtern des Inhalts ermöglicht.

Die Symbolleiste, die sich unterhalb der oberen Navigationsleiste befindet, bietet den folgenden Umschalter auf der linken Seite:

![toggleswitch](assets/toggleswitch.png)

[Filterschiene](moderation.md#filter-rail)\
Öffnet eine Leiste bei Auswahl der Option &quot;Suchen&quot;, die eine Auswahl von Eigenschaften zum Filtern des Inhalts ermöglicht.

![filterrail](assets/filterrail.png)

### Inhaltsbereich {#content-area}

Der Inhaltsbereich enthält Informationen für veröffentlichte UGC:

* Die UGC veröffentlicht
* Mitgliedsname
* Mitglied Avatar
* Speicherort des Beitrags
* Zeitpunkt der Veröffentlichung
* Anzahl der Antworten auf den Beitrag
* [Mit dem Beitrag verknüpftes Sentiment](moderate-ugc.md#sentiment)
* Bei Genehmigung wird ein Häkchen angezeigt
* Wenn eine Anlage vorhanden ist, wird eine Paperclip angezeigt

>[!NOTE]
>
>Der Inhaltsbereich verfügt über einen *unendlichen Bildlauf*, sodass Sie mit dem Bildlauf fortfahren können, bis das Ende des Inhalts erreicht ist. Die Symbolleiste bleibt auch beim Scrollen in einer festen, sichtbaren Position über dem Inhaltsbereich.

### Filterleiste {#filter-rail}

![chlimage_1-472](assets/chlimage_1-472.png)

Das Seitensymbol öffnet die Filterleiste. Die Filterleiste, die links neben dem Inhaltsbereich angezeigt wird, bietet verschiedene Filter, von denen jede unmittelbar auf das referenzierte UGC wirkt, das im Inhaltsbereich angezeigt wird.

Die Filter in den einzelnen Kategorien werden **** ODER-zugeordnet, und die Filter in den verschiedenen Kategorien werden zusammen **** ANDed zugeordnet.

Wenn Sie beispielsweise sowohl **Frage** als auch **Antwort** aktivieren, sehen Sie Inhalte, die entweder eine **Frage** *oder* eine **Antwort** sind.

Wenn Sie jedoch **Frage** und **Ausstehend** aktivieren, werden nur Inhalte angezeigt, die eine **Frage** und **Ausstehend** sind.

>[!NOTE]
>
>Community-Moderatoren können die vordefinierten Filter in der Benutzeroberfläche der Moderationskonsole mit einem Lesezeichen versehen. Da diese Filter an das Ende der URL angehängt werden (als Abfragezeichenfolgen-Parameter), können Moderatoren später zu den mit Lesezeichen versehenen Filtern zurückkehren und diese Links gemeinsam nutzen.

![searicon](assets/searchicon.png)

Wenn die Filterleiste geöffnet ist, wird das Seitenbedienfeld durch das Symbol Suchen geschlossen. Um die Filterleiste zu schließen und nur den vom Benutzer erstellten Inhalt anzuzeigen, klicken Sie auf das Suchsymbol und wählen Sie die Option &quot;Nur Inhalt&quot;.

#### Inhalts-Pfad {#content-path}

Der Inhaltspfad beschränkt die Anzeige des Referenz-UGC auf die im angegebenen Inhalts-Repository abgelegten Beiträge.

![content-path](assets/content-path.png)

#### Textsuche {#text-search}

Die Textsuche beschränkt die angezeigte UGC auf Beiträge, die den eingegebenen Text enthalten.

![chlimage_1-473](assets/chlimage_1-473.png)

#### Website {#site}

Site beschränkt die referenzierte UGC auf Beiträge auf ausgewählte Community-Sites. Wenn keine Sites markiert sind, werden alle Verweise auf UGC angezeigt.

![chlimage_1-474](assets/chlimage_1-474.png)

>[!NOTE]
>
>Wenn ein Administrator auf die Massenmoderationskonsole zugreift, werden alle Verweise auf UGC angezeigt, einschließlich Sites, die nicht mit dem [Site-Erstellungsassistenten](sites-console.md)erstellt wurden, wie z. B. die Geometrixx-Beispiele.
>
>Wenn ein Mitglied einer vertrauenswürdigen Community auf die Massenmoderationskonsole zugreift, werden nur Verweise auf UGC angezeigt, die für Community-Sites erstellt wurden, die das Mitglied moderieren darf, und können mit dem Site-Filter gefiltert werden.

#### Inhaltstyp {#content-type}

Content Type beschränkt die referenzierte UGC auf Beiträge des ausgewählten Ressourcentyps. Es können ein oder mehrere der folgenden Typen ausgewählt werden. Alle Typen werden angezeigt, wenn keine ausgewählt ist.

* **Kommentar**
* **Forumthema**
* **Forumsantwort**
* **Frage**
* **Antwort**
* **Blog-Artikel**
* **Blog-Kommentar**
* **Kalenderereignis**
* **Kalenderkommentar**
* **Ordner in Dateibibliothek**
* **Dokument in Dateibibliothek**
* **Idee**
* **Ideen-Kommentar**

![content-types](assets/content-types.png)

#### Zusätzliche Inhaltstypen {#additional-content-types}

So fügen Sie zusätzliche Ressourcen zum Filtern hinzu:

* Auf der Authoring-Instanz
* Anmelden als Administrator
* Open [Web Console](http://localhost:4502/system/console/configMgr)
* Suchen `AEM Communities Moderation Dashboard Filters`
* Wählen Sie die Konfiguration aus, die im Bearbeitungsmodus geöffnet werden soll
* Geben Sie den ResourceType einer Komponente ein, nach der gefiltert werden soll
   * Geben Sie zum Beispiel Folgendes ein, um nach eingeschlossenen Abstimmungskomponenten zu filtern:\
      `Voting=social/tally/components/hbs/voting`

![chlimage_1-475](assets/chlimage_1-475.png)

* Wählen Sie Speichern
* Communities - Moderationskonsole aktualisieren

Das Ergebnis ist ein neuer auswählbarer Filter `Voting`unter der `Content Type` Filtergruppe.

Wenn dieser Filter ausgewählt ist, zeigt der Inhalt des Dashboards UGC an, das mit einem der eingegebenen ResourceTypes übereinstimmt.

#### Status {#status}

Der Status beschränkt die referenzierte UGC auf Beiträge mit dem ausgewählten Status, bei denen es sich um einen oder mehrere Beiträge mit dem Status Ausstehend, Genehmigt, Verweigert oder Schließen sowie Entwurf oder Geplant für Blog-Artikel und Beantwortet oder Nicht beantwortet für Fragen zur Servicequalitätsprüfung handeln kann. Wenn keine ausgewählt ist, werden alle angezeigt.

>[!NOTE]
>
>Wenn nur der Status &quot;Nicht beantwortet&quot;ausgewählt ist, wird dem Moderator der gesamte Inhalt (für alle Inhaltstypen) mit Ausnahme der beantworteten Fragen angezeigt. Dies liegt daran, dass die Eigenschaft, die für die Antwort Frage verantwortlich ist, bei nicht beantworteten Fragen und anderen Inhalten wie Forenthema, Blog-Artikel oder Kommentaren nicht vorhanden ist.

![Status](assets/statuses.png)

#### Kennzeichnung {#flagging}

Durch die Kennzeichnung wird die Anzeige des referenzierten UGC auf Beiträge beschränkt, die markiert oder ausgeblendet sind.

Sobald ein Inhaltselement markiert ist, bleibt es gekennzeichnet, bis Sie die Markierung für dieses Inhaltselement aufheben, indem Sie erneut auf die Schaltfläche &quot; **[!UICONTROL Flag]** &quot;klicken. Beachten Sie, dass es keine Kennzeichnungsebenen gibt, wie z. B. wichtig oder nachfolgende.

![chlimage_1-476](assets/chlimage_1-476.png)

#### Mitglieder {#members}

Mitglieder beschränken die referenzierte UGC, die für UGC angezeigt wird, gepostet durch den angegebenen Mitgliedsnamen.

![chlimage_1-477](assets/chlimage_1-477.png)

#### Veröffentlichungszeitraum {#posted-in-the-last}

&quot;Gepostet in der letzten&quot;beschränkt die referenzierte Benutzerkontensteuerung auf Beiträge, die in der letzten Stunde, dem letzten Tag, der letzten Woche, dem letzten Monat oder dem letzten Jahr erstellt wurden.

![chlimage_1-478](assets/chlimage_1-478.png)

#### Empfindung {#sentiment}

[Das Sentiment](moderate-ugc.md#sentiment) beschränkt die referenzierte UGC auf Beiträge mit einem Sentimentwert, der entweder positiv, negativ oder neutral ist.

![chlimage_1-479](assets/chlimage_1-479.png)

## Moderationsaktionen {#moderation-actions}

[Moderationsaktionen](moderate-ugc.md#moderation-actions) können für eine oder mehrere Auswahlen im Inhaltsbereich oder beim Anzeigen von Inhaltsdetails durchgeführt werden.

Wenn Sie die Beiträge stapelweise moderieren möchten, klicken Sie im Inhaltsbereich auf das Symbol Auswählen ( ![Auswahl](assets/selecticon.png)) eines Beitrags, das angezeigt wird, wenn Sie mit der Maus (Desktop) darauf zeigen oder einen Finger auf dem Beitrag drücken (Mobil). Auf diese Weise können Sie den Mehrfachauswahlmodus aufrufen und die nachfolgenden Beiträge auswählen, die per Mausklick gepostet werden sollen. Verwenden Sie die in der Symbolleiste angezeigten Schaltflächen, um Moderationsaktionen für die ausgewählten Beiträge durchzuführen. Alle Aktionen werden zur Bestätigung aufgefordert.

Um einen einzelnen Beitrag im Inhaltsbereich zu moderieren, halten Sie den Mauszeiger über ihn (Desktop) oder drücken Sie die Eingabetaste und halten Sie den Finger auf dem Beitrag (Mobil), sodass Schaltflächen auf dem Beitrag angezeigt werden. Wenn Sie mit einem einzigen Inhaltsdetail arbeiten, wird nur eine Löschaktion zur Bestätigung aufgefordert.

### Moderieren mehrerer Beiträge {#moderating-multiple-posts}

Geben Sie den Massenauswahlmodus ein, indem Sie auf das `Select` Symbol für einen Beitrag klicken:

![select-icon](assets/select-icon.png)

Um den Massenauswahlmodus zu beenden, wählen Sie in der Symbolleiste das Symbol zum Abbrechen (x) aus:

Folgende Moderationsaktionen können an mehreren Beiträgen durchgeführt werden:

* Ablehnen
* Löschen
* Beiträge schließen/erneut öffnen

Die Symbole für diese Aktionen werden nur dann in der Symbolleiste angezeigt, wenn mehrere Beiträge ausgewählt sind.

![bulkmedium](assets/bulkmoderate.png)

### Moderieren eines einzelnen Beitrags {#moderating-a-single-post}

Im Auswahlmodus ist es möglich,

* Benutzerdetails anzeigen, indem Sie den Benutzernamen auswählen
* Zeigen Sie den Beitrag im Kontext an, indem Sie den Link zum Beitrag auswählen
* [Antwort](#reply)
* [Gastzugang](#allow)
* [Ablehnen](#deny)
* [Löschen](#delete)
* [Schließen](#close)
* Anzeigen [des Moderationsverlaufs](#moderation-history)
* [Details anzeigen](#viewdetails)

In der Kartenansicht über den Symbolen für Moderationsaktionen ist der Text des Beitrags vorhanden, und unten sind die Daten, die anzeigen

* Wenn Antworten vorliegen, und wenn ja, vor der Anzahl der Antworten
* Wenn gekennzeichnet wurde
* Wurde genehmigt
* Zeitpunkt der Veröffentlichung des UGC

![singleselectmode](assets/singleselectmode.png)

#### Antwort {#reply}

![chlimage_1-480](assets/chlimage_1-480.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, wird ein Symbol zum Antworten angezeigt, wenn der UGC-Typ Antworten unterstützt und so konfiguriert ist, dass Antworten zulässig sind.

#### Gastzugang {#allow}

![chlimage_1-481](assets/chlimage_1-481.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, wird das Symbol Zulassen angezeigt, wenn der Beitrag markiert oder verweigert wurde. Wenn die Option &quot;Zulassen&quot;markiert ist, werden alle Flags gelöscht.

#### Ablehnen {#deny}

![chlimage_1-482](assets/chlimage_1-482.png)

Die Aktion &quot;Moderation **verweigern** &quot;steht nur für moderierte Inhalte zur Verfügung und wird nur im Mehrfachauswahlmodus bei nicht moderierten Inhalten angezeigt.

Nicht moderierte Inhalte werden immer genehmigt.

Moderierte Inhalte werden zunächst in den Status &quot;Ausstehend&quot;versetzt und können später geändert werden, um genehmigt oder verweigert zu werden.

Inhalt, der den Status &quot;Ausstehend&quot;verlässt, kann nie in den Status &quot;Ausstehend&quot;zurückkehren. Inhalte, die als genehmigt oder verweigert markiert sind, können jederzeit in einen anderen Status geändert werden.

#### Löschen {#delete}

![chlimage_1-483](assets/chlimage_1-483.png)

In einem Auswahl- oder Massenmodus können Sie Elemente auswählen und löschen. Die Löschaktion führt zu einem Bestätigungsdialogfeld. Nach dem Löschen verschwinden diese Elemente sofort aus dem Inhaltsbereich. **Sobald UGC gelöscht wurde, wird es dauerhaft aus dem Repository entfernt und kann später nicht mehr abgerufen werden.**

#### Schließen {#close}

![chlimage_1-484](assets/chlimage_1-484.png)

Beim Arbeiten mit einem einzelnen Beitrag wird ein Schließen-Symbol angezeigt, wenn der UGC-Typ die Möglichkeit unterstützt, weitere Beiträge für diese Ressource zu verhindern.

#### Moderationsverlauf {#moderation-history}

![chlimage_1-485](assets/chlimage_1-485.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, wird ein Symbol für den Moderationsverlauf angezeigt, wenn Sie den Mauszeiger darüber halten. Wenn Sie das Symbol auswählen, wird ein Fenster mit einem Verlauf der Aktionen angezeigt, die in Bezug auf den UGC-Beitrag durchgeführt wurden.

Um zur Inhaltsbereichsanzeige mehrerer UGC-Beiträge zurückzukehren, wählen Sie das X in der oberen rechten Ecke des Ansichtsdetailbereichs.

Beispiel:

![chlimage_1-486](assets/chlimage_1-486.png)

#### Details anzeigen {#view-detail}

![chlimage_1-487](assets/chlimage_1-487.png)

Wenn Sie mit einem einzelnen Beitrag arbeiten, können Sie weitere Details anzeigen, indem Sie das UGC im Detailmodus öffnen.

Bewegen Sie dazu den Mauszeiger über den Beitrag, um das Symbol anzuzeigen, und wählen Sie es aus, um einen Bereich mit weiteren Details zum Beitrag anzuzeigen. `View Detail`

Um zur Inhaltsbereichsanzeige mehrerer UGC-Beiträge zurückzukehren, wählen Sie das X in der oberen rechten Ecke des Ansichtsdetailbereichs.

Beispiel:

![chlimage_1-488](assets/chlimage_1-488.png)

