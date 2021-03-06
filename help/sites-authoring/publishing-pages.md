---
title: Veröffentlichen von Seiten
seo-title: Publishing Pages
description: Veröffentlichen von Seiten
seo-description: null
uuid: 1222859d-ef8d-462e-a125-b76e6cfec26d
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8f2714bc-9d6c-4e6f-97a1-3b4f977348c5
source-git-commit: d01eee7602945b8d3cb3ad004ccf5ad6cbc4c73c
workflow-type: tm+mt
source-wordcount: '1680'
ht-degree: 88%

---


# Veröffentlichen von Seiten{#publishing-pages}

Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, [muss dieser auf der öffentlichen Website (der Veröffentlichungsumgebung) verfügbar gemacht werden](/help/sites-authoring/author.md#concept-of-authoring-and-publishing).

Dies wird als Veröffentlichung einer Seite bezeichnet. Wenn Sie eine Seite aus der Veröffentlichungsumgebung entfernen, wird dies als Rückgängigmachen der Veröffentlichung bezeichnet. Während der Veröffentlichung und des Rückgängigmachens der Veröffentlichung bleibt die Seite so lange in der Bearbeitungsumgebung verfügbar und kann geändert werden, bis Sie sie löschen.

Sie können eine Seite auch sofort oder zu einem vordefinierten künftigen Zeitpunkt (Datum/Uhrzeit) veröffentlichen bzw. ihre Veröffentlichung rückgängig machen.

>[!NOTE]
>
>Manche Begriffe im Zusammenhang mit dem Veröffentlichen können leicht verwechselt werden:
>
>* **Veröffentlichen/Veröffentlichung rückgängig machen**
   >  Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihren Inhalt in Ihrer Veröffentlichungsumgebung verfügbar machen (oder dies rückgängig machen).
>
>* **Aktivieren/Deaktivieren**
   >  Diese Begriffe sind Synonyme für das Veröffentlichen/Rückgängigmachen der Veröffentlichung.
>
>* **Replizieren/Replikation**
   >  Dies sind die technischen Begriffe, die die Verschiebung von Daten (z. B. Seiteninhalt, Dateien, Code, Benutzerkommentare) von einer Umgebung in eine andere beschreiben, z. B. bei der Veröffentlichung oder umgekehrten Replizierung von Benutzerkommentaren.
>


>[!NOTE]
>
>Wenn Sie nicht über die erforderlichen Berechtigungen für das Veröffentlichen einer bestimmten Seite verfügen:
>
>* Ein Workflow wird ausgelöst, der die entsprechende Person über Ihre Veröffentlichungsanfrage informiert.
>* Dieser [Workflow wurde möglicherweise von Ihrem Entwicklerteam angepasst](/help/sites-developing/workflows-models.md).
>* Sie werden in einer Mitteilung darüber informiert, dass der Workflow ausgelöst wurde.

>


## Veröffentlichen von Seiten {#publishing-pages-2}

Abhängig davon, wo Sie sich gerade befinden, können Sie Veröffentlichungen folgendermaßen vornehmen:

* [Im Seiten-Editor](/help/sites-authoring/publishing-pages.md#publishing-from-the-editor)
* [In der Sites-Konsole](/help/sites-authoring/publishing-pages.md#publishing-from-the-console)

### Veröffentlichungen im Editor {#publishing-from-the-editor}

Wenn Sie eine Seite bearbeiten, kann sie direkt im Editor veröffentlicht werden.

1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Menü zu öffnen, und danach die Option **Seite veröffentlichen**.

   ![screen_shot_2018-03-21at152734](assets/screen_shot_2018-03-21at152734.png)

1. Je nachdem, ob die Seite Verweise enthält, die veröffentlicht werden müssen, geschieht Folgendes:

   * Die Seite wird direkt veröffentlicht, wenn keine Verweise veröffentlicht werden müssen.
   * Wenn die Seite Verweise enthält, die veröffentlicht werden müssen, werden diese im **Veröffentlichungsassistenten** aufgeführt und Sie können eine der folgenden Aktionen ausführen:

      * Geben Sie an, welche Assets, Tags usw. Sie mit der Seite veröffentlichen möchten, und wählen Sie **Veröffentlichen** aus, um den Vorgang abzuschließen.
      * Mit **Abbrechen** können Sie den Vorgang abbrechen.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. Mit **Veröffentlichen** wird die Seite in der Veröffentlichungsumgebung repliziert. Im Seiteneditor wird ein Hinweis angezeigt, in dem die Veröffentlichung bestätigt wird.

   ![screen_shot_2018-03-21at152840](assets/screen_shot_2018-03-21at152840.png)

   Wird diese Seite in der Konsole dargestellt, ist der aktualisierte Veröffentlichungsstatus sichtbar.

   ![screen_shot_2018-03-21at152951](assets/screen_shot_2018-03-21at152951.png)

>[!NOTE]
>
>Im Editor kann nur eine teilweise Veröffentlichung vorgenommen werden, d. h. nur die ausgewählten und keine untergeordneten Seiten werden veröffentlicht.

>[!NOTE]
>
>Seiten, auf die im Editor über [Aliasnamen](/help/sites-authoring/editing-page-properties.md#advanced) zugegriffen wird, können nicht veröffentlicht werden. Veröffentlichungsoptionen im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.

### Veröffentlichungen über die Konsole {#publishing-from-the-console}

In der Sites-Konsole gibt es zwei Möglichkeiten zur Veröffentlichung:

* [Quick Publish](/help/sites-authoring/publishing-pages.md#quick-publish)
* [Veröffentlichung verwalten](/help/sites-authoring/publishing-pages.md#manage-publication)

#### Quick Publish {#quick-publish}

**Quick Publish** wird für einfache Fälle verwendet. Die ausgewählten Seiten werden damit sofort ohne weitere Interaktion veröffentlicht. Aus diesem Grund werden auch alle nicht-veröffentlichten Verweise ebenfalls automatisch veröffentlicht.

So veröffentlichen Sie eine Seite mit der Funktion „Quick Publish“:

1. Wählen Sie die gewünschten Seiten in der Sites-Konsole aus und klicken Sie auf die Schaltfläche **Quick Publish**.

   ![screen_shot_2018-03-21at153115](assets/screen_shot_2018-03-21at153115.png)

1. Bestätigen Sie im Dialogfeld Quick Publish die Veröffentlichung, indem Sie auf **Veröffentlichen** oder abbrechen durch Klicken auf **Abbrechen**. Beachten Sie, dass auch alle unveröffentlichten Verweise ebenfalls automatisch veröffentlicht werden.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Bei der Veröffentlichung der Seite erscheint eine Warnmeldung, in der die Veröffentlichung bestätigt wird.

>[!NOTE]
>
>Die Option „Quick Publish“ ermöglicht nur die teilweise Veröffentlichung, d. h. nur die ausgewählten und keine untergeordneten Seiten werden veröffentlicht.

#### Veröffentlichung verwalten {#manage-publication}

**Veröffentlichung verwalten** bietet mehr Optionen als „Quick Publish“. Mit dieser Funktion können Sie auch untergeordnete Seiten einschließen, Verweise anpassen, alle nötigen Workflows starten und bei Bedarf zu einem späteren Zeitpunkt veröffentlichen.

So veröffentlichen Sie eine Seite bzw. machen ihre Veröffentlichung rückgängig mit „Veröffentlichung verwalten“:

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.

   ![screen_shot_2018-03-21at153309](assets/screen_shot_2018-03-21at153309.png)

1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Im ersten Schritt **Optionen** haben Sie folgende Möglichkeiten:

   * Veröffentlichen Sie die ausgewählte Seite oder machen Sie die Veröffentlichung rückgängig.
   * Führen Sie diese Aktion sofort oder zu einem späteren Zeitpunkt aus.

   Bei der späteren Veröffentlichung wird ein Workflow gestartet, mit dem die ausgewählten Seiten zur angegebenen Zeit veröffentlicht werden. Entsprechend wird durch die Auswahl des Rückgängigmachens der Veröffentlichung zu einem späteren Zeitpunkt der entsprechende Workflow für die ausgewählten Seiten zum angegebenen Zeitpunkt gestartet.

   Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole [Workflow](/help/sites-administering/workflows.md), um den entsprechenden Workflow zu beenden.

   ![chlimage_1-52](assets/chlimage_1-52.png)

   Klicken Sie auf **Weiter**, um fortzufahren.

1. Im nächsten Schritt des Assistenten &quot;Veröffentlichung verwalten&quot;wird Folgendes ausgeführt: **Anwendungsbereich** können Sie den Umfang der Veröffentlichung/Rückgängigmachung definieren, z. B. um untergeordnete Seiten einzuschließen und/oder Verweise einzuschließen.

   ![screen_shot_2018-03-21at153354](assets/screen_shot_2018-03-21at153354.png)

   Mit der Schaltfläche **Inhalt hinzufügen** können Sie zusätzliche Seiten zur Liste der zu veröffentlichenden Seiten hinzufügen, falls Sie dies noch nicht vor dem Starten des Assistenten „Veröffentlichung verwalten“ getan haben.

   Durch Klicken auf die Schaltfläche „Inhalt hinzufügen“ wird der [Pfad-Browser](/help/sites-authoring/author-environment-tools.md#path-browser) gestartet, mit dem Inhalte ausgewählt werden können.

   Wählen Sie die gewünschten Seiten aus und klicken Sie dann auf **Auswählen**, um den Inhalt dem Assistenten hinzuzufügen, oder auf „Abbrechen“, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   Im Assistenten können Sie dann ein Element in der Liste auswählen, um es weiter zu konfigurieren:

   * Untergeordnete Elemente einschließen
   * Das Element aus der Auswahl entfernen
   * Seine veröffentlichten Verweise verwalten

   ![screen_shot_2018-03-21at153450](assets/screen_shot_2018-03-21at153450.png)

   Durch Klicken auf **Untergeordnete Elemente einbeziehen** wird ein Dialogfeld geöffnet, in dem Sie folgende Möglichkeiten haben:

   * Nur unmittelbar untergeordnete Elemente einbeziehen.
   * Nur geänderte Seiten einbeziehen.
   * Nur bereits veröffentlichte Seiten einbeziehen.

   Klicken Sie auf **Hinzufügen**, um die untergeordneten Seiten zur Liste der Seiten hinzuzufügen, die je nach Auswahloptionen veröffentlicht werden sollen oder deren Veröffentlichung rückgängig gemacht werden soll. Klicken Sie auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   ![chlimage_1-53](assets/chlimage_1-53.png)

   Dort sehen Sie die hinzugefügten Seiten entsprechend Ihrer Auswahl im Dialogfeld „Untergeordnete Elemente einbeziehen“.

   Zur Ansicht und zum Ändern der Verweise, die für eine Seite veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll, wählen Sie sie aus und klicken Sie anschließend auf die Schaltfläche **Veröffentlichte Verweise**.

   ![screen_shot_2018-03-21at153801](assets/screen_shot_2018-03-21at153801.png)

   Die **Veröffentlichte Verweise** zeigt die Verweise für den ausgewählten Inhalt an. Standardmäßig sind alle ausgewählt und werden veröffentlicht bzw. die Veröffentlichung wird rückgängig gemacht. Sie können sie aber auch deaktivieren, um die Auswahl aufzuheben, sodass sie nicht in die Aktion einbezogen werden.

   Klicken **Fertig** speichern Sie Ihre Änderungen oder **Abbrechen** , um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   ![screen_shot_2018-03-21at153824](assets/screen_shot_2018-03-21at153824.png)

   Im Assistenten wird die Spalte **Verweise** aktualisiert und zeigt Ihre Auswahl von Verweisen an, die veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll.

   ![screen_shot_2018-03-21at153925](assets/screen_shot_2018-03-21at153925.png)

1. Klicken Sie auf **Veröffentlichen**, um den Vorgang abzuschließen.

   In der Sites-Konsole wird die Veröffentlichung durch eine Benachrichtigung bestätigt.

   ![screen_shot_2018-03-21at153951](assets/screen_shot_2018-03-21at153951.png)

1. Wenn die veröffentlichten Seiten mit Workflows verknüpft sind, werden diese im abschließenden **Workflow**-Schritt des Veröffentlichungsassistenten gezeigt.

   >[!NOTE]
   >
   >Der gezeigte **Workflow**-Schritt hängt von den Rechten des jeweiligen Benutzers ab. Siehe [vorheriger Hinweis auf dieser Seite](/help/sites-authoring/publishing-pages.md) hinsichtlich der Veröffentlichungsberechtigungen [Zugriff auf Workflows verwalten](/help/sites-administering/workflows-managing.md) und [Anwenden von Workflows auf Seiten](/help/sites-authoring/workflows-applying.md) für Details.

   Die Ressourcen werden gemäß den ausgelösten Workflows gruppiert, wobei Sie für jede Ressource folgende Möglichkeiten haben:

   * Definieren des Workflow-Titels
   * Beibehalten des Workflow-Pakets, vorausgesetzt der Workflow [unterstützt mehrere Ressourcen](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support)
   * Definieren des Titels des Workflow-Pakets, sofern die Option zum Beibehalten des Workflow-Pakets ausgewählt wurde

   Klicken **Veröffentlichen** oder **Später veröffentlichen**, um die Veröffentlichung abzuschließen.

   ![chlimage_1-54](assets/chlimage_1-54.png)

## Veröffentlichen von Seiten rückgängig machen {#unpublishing-pages}

Wenn Sie die Veröffentlichung einer Seite rückgängig machen, wird sie aus der Veröffentlichungsumgebung gelöscht, sodass sie nicht mehr für Ihre Leser verfügbar ist.

[Ähnlich wie beim Veröffentlichen](/help/sites-authoring/publishing-pages.md#publishing-pages) können Sie auch die Veröffentlichung einer oder mehrerer Seiten aufheben:

* [Im Seiten-Editor](/help/sites-authoring/publishing-pages.md#unpublishing-from-the-editor)
* [In der Sites-Konsole](/help/sites-authoring/publishing-pages.md#unpublishing-from-the-console)

### Rückgängigmachen der Veröffentlichung im Editor {#unpublishing-from-the-editor}

Wenn Sie die Veröffentlichung einer von Ihnen bearbeiteten Seite rückgängig machen möchten, wählen Sie analog zur [Veröffentlichung einer Seite](/help/sites-authoring/publishing-pages.md#publishing-from-the-editor) im Menü **Seiteninformationen** die Option **Veröffentlichung der Seite rückgängig machen** aus.

>[!NOTE]
>
>Die Veröffentlichung von Seiten, auf die im Editor über [Aliasnamen](/help/sites-authoring/editing-page-properties.md#advanced) zugegriffen wird, kann nicht rückgängig gemacht werden. Veröffentlichungsoptionen im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.

### Rückgängigmachen der Veröffentlichung in der Konsole {#unpublishing-from-the-console}

Ebenso wie Sie [die Option „Veröffentlichung verwalten“ zur Veröffentlichung verwenden](/help/sites-authoring/publishing-pages.md#manage-publication), können Sie damit auch eine Veröffentlichung aufheben.

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie im ersten Schritt **Optionen** die Option **Veröffentlichung aufheben** anstelle der Standardoption **Veröffentlichen** aus.

   ![chlimage_1-55](assets/chlimage_1-55.png)

   Die Auswahl von „Später veröffentlichen“ startet einen Workflow zur Veröffentlichung der Seite zum angegebenen Zeitpunkt. Entsprechend startet die Auswahl von „Später deaktivieren“ einen Workflow zum Rückgängigmachen der Veröffentlichung der ausgewählten Seiten zum angegebenen Zeitpunkt.

   Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole [Workflow](/help/sites-administering/workflows.md), um den entsprechenden Workflow zu beenden.

1. Um das Rückgängigmachen der Veröffentlichung abzuschließen, fahren Sie mit dem Assistenten ähnlich wie beim [Veröffentlichen der Seite](/help/sites-authoring/publishing-pages.md#manage-publication) fort.

## Veröffentlichen und Rückgängigmachen der Veröffentlichung eines Baums {#publishing-and-unpublishing-a-tree}

Wenn Sie allerdings eine große Zahl von Inhaltsseiten erstellt bzw. aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es praktischer sein, mit einer einzigen Aktion den gesamten Baum zu veröffentlichen.

Dazu können Sie in der Sites-Konsole die Option [Veröffentlichung verwalten](/help/sites-authoring/publishing-pages.md#manage-publication) verwenden.

1. Wählen Sie in der Sites-Konsole die Stammseite des Baums aus, den Sie veröffentlichen möchten bzw. dessen Veröffentlichung Sie rückgängig machen möchten, und danach **Veröffentlichung verwalten**.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie „Veröffentlichen“ oder „Veröffentlichung aufheben“ sowie den Zeitpunkt aus und danach **Weiter**, um fortzufahren.
1. Wählen Sie im Schritt **Bereich** die Stammseite aus und danach **Untergeordnete Elemente einbeziehen**.

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. Deaktivieren Sie im Dialogfeld **Untergeordnete Elemente einbeziehen** die folgenden Optionen:

   * Nur unmittelbar untergeordnete Elemente einbeziehen
   * Nur bereits veröffentlichte Seiten einbeziehen

   Diese Optionen sind standardmäßig ausgewählt. Sie müssen also darauf achten, diese Auswahl aufzuheben. Klicken Sie auf **Hinzufügen**, um den Inhalt beim Veröffentlichen bzw. beim Rückgängigmachen der Veröffentlichung hinzuzufügen.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Im Assistenten **Veröffentlichung verwalten** wird der Inhalt des Baums zur Überprüfung aufgelistet. Sie können die Auswahl weiter anpassen, indem Sie zusätzliche Seiten hinzuzufügen oder ausgewählte Seiten entfernen.

   ![screen_shot_2018-03-21at154237](assets/screen_shot_2018-03-21at154237.png)

   Sie können die zu veröffentlichenden Verweise auch in der Option **Veröffentlichte Verweise** überprüfen.

1. [Fahren Sie mit dem Assistenten Veröffentlichung verwalten wie gewohnt fort.](#manage-publication) , um die Veröffentlichung des Baums abzuschließen oder dessen Veröffentlichung aufzuheben.

## Bestimmen des Veröffentlichungsstatus {#determining-publication-status}

Sie können den Veröffentlichungsstatus einer Seite bestimmen:

* In der [Ressourcenübersicht in der Sites-Konsole](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)

   ![screen_shot_2018-03-21at154336](assets/screen_shot_2018-03-21at154336.png)

   Der Veröffentlichungsstatus wird in der Sites-Konsole in der Ansicht [Karte](/help/sites-authoring/basic-handling.md#card-view), [Spalte](/help/sites-authoring/basic-handling.md#column-view) und [Liste](/help/sites-authoring/basic-handling.md#list-view) angezeigt.

* in der [Zeitleisten](/help/sites-authoring/basic-handling.md#timeline)

   ![screen_shot_2018-03-21at154420](assets/screen_shot_2018-03-21at154420.png)

* im Menü [Seiteninformationen](/help/sites-authoring/author-environment-tools.md#page-information) beim Bearbeiten einer Seite

   ![screen_shot_2018-03-21at154456](assets/screen_shot_2018-03-21at154456.png)

