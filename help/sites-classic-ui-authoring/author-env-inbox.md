---
title: Ihr Posteingang
seo-title: Your Inbox
description: Sie können Benachrichtigungen aus verschiedenen Bereichen von AEM erhalten, z. B. Benachrichtigungen zu Arbeitselementen oder Aufgaben, die Aktionen darstellen, die Sie für Seiteninhalte ausführen müssen.
seo-description: You can receive notifications from various areas of AEM such as notification about work items or tasks that represent actions that you need to perform on page content.
uuid: 90a3b4db-add9-47d4-a95d-fcc3863d6255
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 71f16254-336f-41bf-bf75-f69ba1051d59
exl-id: e7111c21-1f38-4d0d-ac4b-c83133c0d8d6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 27%

---

# Ihr Posteingang{#your-inbox}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können Benachrichtigungen aus verschiedenen Bereichen von AEM erhalten, z. B. Benachrichtigungen zu Arbeitselementen oder Aufgaben, die Aktionen darstellen, die Sie für Seiteninhalte ausführen müssen.

Sie erhalten diese Benachrichtigungen in zwei Postfächern, die durch den Benachrichtigungstyp getrennt sind:

* Ein Posteingang, in dem Sie die Benachrichtigungen sehen können, die Sie durch Abonnements erhalten, wird im folgenden Abschnitt beschrieben.
* Ein spezieller Posteingang für Workflow-Elemente wird im Dokument [Teilnehmen an Workflows](/help/sites-classic-ui-authoring/classic-workflows-participating.md) beschrieben.

## Anzeigen Ihrer Benachrichtigungen {#viewing-your-notifications}

So zeigen Sie Ihre Benachrichtigungen an:

1. Öffnen Sie den Benachrichtigungs-Posteingang: im **Websites** -Konsole, klicken Sie auf die Benutzerschaltfläche oben rechts und wählen Sie **Benachrichtigungs-Posteingang**.

   ![screen_shot_2012-02-08at105226am](assets/screen_shot_2012-02-08at105226am.png)

   >[!NOTE]
   >
   >Sie können auch direkt im Browser auf die Konsole zugreifen. Beispiel:
   >
   >` https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Ihre Benachrichtigungen werden angezeigt. Sie können nach Bedarf Aktionen durchführen:

   * [Abonnieren von Benachrichtigungen](#subscribing-to-notifications)
   * [Verarbeiten von Benachrichtigungen](#processing-your-notifications)

   ![chlimage_1-8](assets/chlimage_1-8.jpeg)

## Abonnieren von Benachrichtigungen {#subscribing-to-notifications}

Abonnieren von Benachrichtigungen:

1. Öffnen Sie den Benachrichtigungs-Posteingang: im **Websites** -Konsole, klicken Sie auf die Benutzerschaltfläche oben rechts und wählen Sie **Benachrichtigungs-Posteingang**.

   ![screen_shot_2012-02-08at105226am-1](assets/screen_shot_2012-02-08at105226am-1.png)

   >[!NOTE]
   >
   >Sie können auch direkt im Browser auf die Konsole zugreifen. Beispiel:
   >
   >`https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Klicken Sie oben links auf **Konfigurieren...**, um das Konfigurationsdialogfeld zu öffnen.

   ![screen_shot_2012-02-08at111056am](assets/screen_shot_2012-02-08at111056am.png)

1. Wählen Sie den Benachrichtigungskanal aus:

   * **Posteingang**: Benachrichtigungen werden in Ihrem AEM Posteingang angezeigt.
   * **Email**: Benachrichtigungen werden an die in Ihrem Benutzerprofil definierte E-Mail-Adresse gesendet.

   >[!NOTE]
   >
   >Einige Einstellungen müssen konfiguriert werden, um per E-Mail benachrichtigt zu werden. Sie können auch die E-Mail-Vorlage anpassen oder eine E-Mail-Vorlage für eine neue Sprache hinzufügen. Siehe [Konfigurieren von E-Mail-Benachrichtigungen](/help/sites-administering/notification.md#configuringemailnotification) um E-Mail-Benachrichtigungen in AEM zu konfigurieren.

1. Wählen Sie die Seitenaktionen aus, für die Sie eine Benachrichtigung erhalten möchten:

   * Aktiviert: wenn eine Seite aktiviert wurde.
   * Deaktiviert: wenn eine Seite deaktiviert wurde.
   * Gelöscht (Syndizierung): wenn das Löschen einer Seite repliziert wurde.

      Wenn eine Seite gelöscht oder verschoben wird, wird automatisch eine Löschaktion repliziert: Die Seite wird in der Quellinstanz, in der die Löschaktion durchgeführt wurde, und in der von den Replikationsagenten definierten Zielinstanz gelöscht.

   * Geändert: wenn eine Seite geändert wurde.
   * Erstellt: wenn eine Seite erstellt wurde.
   * Gelöscht: wenn eine Seite durch die Seitenlöschaktion gelöscht wurde.
   * Ausgerollt: wenn ein Rollout einer Seite durchgeführt wurde.

1. Definieren Sie die Pfade der Seiten, für die Sie benachrichtigt werden:

   * Klicken **Hinzufügen** , um der Tabelle eine neue Zeile hinzuzufügen.
   * Klicken Sie auf die Tabellenzelle **Pfad**, und geben Sie den Pfad ein, z. B. `/content/docs`.
   * Um über alle Seiten in der Unter-Baumstruktur Benachrichtigungen zu erhalten, setzen Sie **Exakt?** auf **Nein**.

      Um über nur über die angegebene Seite Benachrichtigungen zu erhalten, setzen Sie **Exakt?** nach **Ja**.

   * Um die Regel zuzulassen, legen Sie **Regel** nach **Zulassen**. Wenn auf **Ablehnen**, wird die Regel verweigert, aber nicht entfernt und kann später zugelassen werden.

   Um eine Definition zu entfernen, wählen Sie die Zeile aus, indem Sie auf eine Tabellenzelle klicken, und klicken Sie auf **Löschen**.

1. Klicken **OK** , um die Konfiguration zu speichern.

## Verarbeiten von Benachrichtigungen {#processing-your-notifications}

Wenn Sie ausgewählt haben, dass Sie Benachrichtigungen in Ihrem AEM-Posteingang erhalten, werden die Benachrichtigungen an das Postfach versendet. Sie können [Anzeigen von Benachrichtigungen](#viewing-your-notifications) Wählen Sie dann die erforderlichen Benachrichtigungen aus, um:

* Genehmigen Sie sie durch Klicken auf **Genehmigen**: der Wert in **Lesen** Spalte ist auf **true**.

* Löschen durch Klicken auf **Löschen**.

![chlimage_1-9](assets/chlimage_1-9.jpeg)
