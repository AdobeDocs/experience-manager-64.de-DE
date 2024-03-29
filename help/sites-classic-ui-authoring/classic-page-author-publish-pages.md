---
title: Veröffentlichen von Seiten
seo-title: Publishing Pages
description: Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, soll er auf Ihrer öffentlichen Website verfügbar gemacht werden.
seo-description: Once you have created and reviewed your content on the author environment, the goal is to make it available on your public website.
uuid: 2b1cb08b-dbe9-4032-8527-15a11aa59d51
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 80c9f4b7-d59f-4ed1-a457-300756962708
exl-id: 7b3f58df-036e-46a8-913e-e695de34ddd7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 47%

---

# Veröffentlichen von Seiten{#publishing-pages}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, muss dieser auf der öffentlichen Website (der Veröffentlichungsumgebung) verfügbar gemacht werden.

Dies wird als Veröffentlichen einer Seite bezeichnet. Wenn Sie eine Seite aus der Veröffentlichungsumgebung entfernen möchten, wird dies als Rückgängigmachen der Veröffentlichung bezeichnet. Beim Veröffentlichen und Rückgängigmachen der Veröffentlichung bleibt die Seite in der Autorenumgebung für weitere Änderungen verfügbar, bis Sie sie löschen.

Sie können eine Seite auch sofort oder zu einem vordefinierten Zeitpunkt (Datum/Uhrzeit) in der Zukunft veröffentlichen bzw. deren Veröffentlichung rückgängig machen.

>[!NOTE]
>
>Bestimmte Begriffe im Zusammenhang mit der Veröffentlichung können verwirrt werden:
>
>* **Veröffentlichen/Veröffentlichung rückgängig machen**
   >  Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihren Inhalt in Ihrer Veröffentlichungsumgebung verfügbar machen (oder dies rückgängig machen).
>
>* **Aktivieren/Deaktivieren**
   >  Diese Begriffe sind Synonyme für das Veröffentlichen/Rückgängigmachen der Veröffentlichung.
>
>* **Replizieren/Replikation**
   >  Dies sind technische Begriffe, die für die Verschiebung von Daten (z. B. Seiteninhalten, Dateien, Code, Benutzerkommentaren) zwischen Umgebungen verwendet werden, z. B. beim Veröffentlichen oder Zurückreplizieren von Benutzerkommentaren.
>


>[!NOTE]
>
>Wenn Sie nicht über die erforderlichen Berechtigungen zum Veröffentlichen einer bestimmten Seite verfügen:
>
>* Es wird ein Workflow ausgelöst, der die entsprechende Person über Ihre Veröffentlichungsanfrage informiert.
>* Eine Meldung wird angezeigt (für einen kurzen Zeitraum), um Sie darüber zu informieren.
>


## Veröffentlichen einer Seite {#publishing-a-page}

Es gibt zwei Methoden zum Aktivieren einer Seite:

* [Mit der Websites-Konsole](#activating-a-page-from-the-websites-console)
* [Mit dem Sidekick auf der Seite selbst](#activating-a-page-from-sidekick)

>[!NOTE]
>
>Mit [Tree aktivieren](#howtoactivateacompletesectiontreeofyourwebsite) in der Tools-Konsole können Sie auch eine Unterbaumstruktur mit mehreren Seiten aktivieren.

### Aktivieren einer Seite über die Websites-Konsole {#activating-a-page-from-the-websites-console}

Sie können Seiten in der Websites-Konsole aktivieren. Nachdem Sie eine Seite geöffnet und deren Inhalt geändert haben, kehren Sie zur Websites-Konsole zurück:

1. Wählen Sie in der Websites-Konsole die Seite aus, die Sie aktivieren möchten.
1. Auswählen **Aktivieren**, entweder über das obere Menü oder das Dropdown-Menü auf dem ausgewählten Seitenelement.

   Um den Inhalt einer Seite und alle zugehörigen Unterseiten zu aktivieren, verwenden Sie die [**Tools**-Konsole](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#howtoactivateacompletesectiontreeofyourwebsite).

   ![screen_shot_2012-02-08at13817pm](assets/screen_shot_2012-02-08at13817pm.png)

   >[!NOTE]
   >
   >Gegebenenfalls werden Sie von AEM aufgefordert, alle Assets zu aktivieren bzw. zu reaktivieren, die mit der Seite verknüpft sind. Sie können die Kontrollkästchen zum Aktivieren dieser Assets aktivieren oder deaktivieren.

1. Gegebenenfalls werden Sie von AEM aufgefordert, alle Assets zu aktivieren bzw. zu reaktivieren, die mit der Seite verknüpft sind. Sie können die Kontrollkästchen zum Aktivieren dieser Assets aktivieren oder deaktivieren.

   ![chlimage_1-135](assets/chlimage_1-135.png)

1. AEM WCM aktiviert den ausgewählten Inhalt. Die veröffentlichten Seiten werden im [Websites-Konsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) (grün markiert) mit Informationen darüber, wer den Inhalt aktiviert hat, sowie Datum und Uhrzeit der Aktivierung.

   ![screen_shot_2012-02-08at14335pm](assets/screen_shot_2012-02-08at14335pm.png)

### Aktivieren einer Seite über den Sidekick {#activating-a-page-from-sidekick}

Sie können eine Seite auch aktivieren, wenn sie zur Bearbeitung geöffnet ist.

Nachdem Sie die Seite geöffnet und ihren Inhalt geändert haben, führen Sie folgende Schritte durch:

1. Wählen Sie die **Seite** im Sidekick.
1. Klicken Sie auf **Seite aktivieren**.

   Oben rechts im Fenster wird eine Meldung angezeigt, die die Aktivierung der Seite bestätigt.

## Rückgängigmachen der Veröffentlichung einer Seite {#unpublishing-a-page}

Um eine Seite aus der Veröffentlichungsumgebung zu entfernen, deaktivieren Sie den Inhalt.

So deaktivieren Sie eine Seite:

1. Wählen Sie in der Websites-Konsole die Seite aus, die Sie deaktivieren möchten.
1. Auswählen **Deaktivieren**, entweder über das obere Menü oder das Dropdown-Menü auf dem ausgewählten Seitenelement. Sie werden aufgefordert, den Löschvorgang zu bestätigen.

   ![screen_shot_2012-02-08at14859pm](assets/screen_shot_2012-02-08at14859pm.png)

1. Aktualisieren Sie die [Websites-Konsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console). Der Inhalt wird rot hervorgehoben, wodurch angezeigt wird, dass er nicht mehr veröffentlicht ist.

   ![screen_shot_2012-02-08at15018pm](assets/screen_shot_2012-02-08at15018pm.png)

## Später aktivieren/deaktivieren {#activate-deactivate-later}

### Später aktivieren {#activate-later}

So planen Sie die Aktivierung einer Seite für einen späteren Zeitpunkt:

1. Öffnen Sie in der Websites-Konsole das Menü **Aktivieren** und wählen Sie die Option **Später aktivieren** aus.
1. Geben Sie in dem daraufhin angezeigten Dialogfeld Datum und Uhrzeit für die Aktivierung ein und klicken Sie auf **OK**. Dadurch wird eine Version der Seite erstellt, die zum angegebenen Zeitpunkt aktiviert wird.

   ![screen_shot_2012-02-08at14751pm](assets/screen_shot_2012-02-08at14751pm.png)

Durch die spätere Aktivierung wird ein Workflow gestartet, mit dem diese Seitenversion zum angegebenen Zeitpunkt aktiviert wird. Umgekehrt startet die Deaktivierung später einen Workflow, um diese Version der Seite zu einem bestimmten Zeitpunkt zu deaktivieren.

Wenn Sie diese Aktivierung/Deaktivierung abbrechen möchten, gehen Sie zu [Workflow-Konsole](/help/sites-administering/workflows-administering.md#main-pars-title-3-yjqslz-refd) , um den entsprechenden Workflow zu beenden.

### Später deaktivieren {#deactivate-later}

So planen Sie die Deaktivierung einer Seite für einen späteren Zeitpunkt:

1. Öffnen Sie in der Websites-Konsole das Menü **Deaktivieren** und wählen Sie die Option **Später deaktivieren** aus.

1. Geben Sie in dem daraufhin angezeigten Dialogfeld Datum und Uhrzeit für die Deaktivierung ein und klicken Sie auf **OK**.

   ![screen_shot_2012-02-08at15129pm](assets/screen_shot_2012-02-08at15129pm.png)

Mit **Später deaktivieren** wird ein Workflow zur Deaktivierung der Seite zum angegebenen Zeitpunkt gestartet.

Wenn Sie diese Deaktivierung abbrechen möchten, gehen Sie zu [Workflow-Konsole](/help/sites-administering/workflows-administering.md#main-pars-title-3-yjqslz-refd) , um den entsprechenden Workflow zu beenden.

## Geplante Aktivierung/Deaktivierung (Einschaltzeit/Ausschaltzeit) {#scheduled-activation-deactivation-on-off-time}

Über die Optionen **Einschaltzeit** und **Ausschaltzeit** können Sie Zeiten auswählen, zu denen eine Seite veröffentlicht bzw. ihre Veröffentlichung rückgängig gemacht werden soll. Diese Optionen können in den [Seiteneigenschaften](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) definiert werden.

### Bestimmen des Seitenveröffentlichungsstatus - Klassische Benutzeroberfläche {#determining-page-publication-status-classic-ui}

Der Status wird im [Websites-Konsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console). Die Farben geben den Veröffentlichungsstatus an.

## Aktivieren eines vollständigen Abschnitts (Baums) Ihrer Website {#activating-a-complete-section-tree-of-your-website}

Aus dem **Websites** -Tab können Sie die einzelnen Seiten aktivieren. Wenn Sie eine beträchtliche Anzahl von Inhaltsseiten eingegeben oder aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es einfacher sein, den gesamten Baum in einer Aktion zu aktivieren. Sie können auch einen Probelauf durchführen, um eine Aktivierung zu emulieren und hervorzuheben, welche Seiten aktiviert werden.

1. Öffnen Sie die **Tools**-Konsole, indem Sie sie auf dem **Startbildschirm** auswählen, und doppelklicken Sie dann auf **Replikation**, um die Konsole zu öffnen (`http://localhost:4502/etc/replication.html`).

   ![screen_shot_2012-02-08at125033pm](assets/screen_shot_2012-02-08at125033pm.png)

1. Klicken Sie in der Konsole **Replikation** auf **Tree aktivieren**.

   Das folgende Fenster (`http://localhost:4502/etc/replication/treeactivation.html`) wird angezeigt.

   ![screen_shot_2012-02-08at125033pm-1](assets/screen_shot_2012-02-08at125033pm-1.png)

1. Geben Sie den **Startpfad** ein. Dies ist der Pfad zum Stammverzeichnis des Abschnitts, den Sie aktivieren (veröffentlichen) möchten. Diese Seite und alle darunter liegenden Seiten werden bei der Aktivierung (bzw. bei der Emulation, falls ein Probelauf ausgewählt wurde) berücksichtigt.
1. Aktivieren Sie die Auswahlkriterien nach Bedarf:

   * **Nur geändert**: nur Seiten aktivieren, die geändert wurden.
   * **Nur aktivierte**: nur Seiten aktivieren, die bereits vorher aktiviert waren. Dies stellt eine Art von Reaktivierung dar.
   * **Ignorieren deaktiviert**: ignorieren Sie alle deaktivierten Seiten.

1. Wählen Sie die gewünschte Aktion aus:

   1. Wählen Sie **Probelauf** aus, wenn Sie überprüfen möchten, welche Seiten aktiviert *würden*. Dabei handelt es sich lediglich um eine Emulation, bei der keine Seiten tatsächlich aktiviert werden.
   1. Wählen Sie **Aktivieren** aus, wenn die Seiten aktiviert werden sollen.
