---
title: Erstellen und Verwalten von Assetüberprüfungen in Formularen
seo-title: Creating and managing reviews for assets in forms
description: Bei einer Überprüfung handelt es sich um einen Mechanismus, bei dem mindestens ein Prüfer Assets kommentieren kann, die in einem Formular verfügbar sind.
seo-description: A Review is a mechanism that allows one or more reviewers to comment on an asset that is available in a form.
uuid: 6b1aa54f-d03c-483a-a398-6522b285194c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 43fd720f-2a5a-47fb-b9d9-d19f866cd0a0
feature: Adaptive Forms
exl-id: ff113288-a69a-4083-82a6-4c65c5062411
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 77%

---

# Erstellen und Verwalten von Assetüberprüfungen in Formularen  {#creating-and-managing-reviews-for-assets-in-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Überprüfung {#review}

Bei einer Überprüfung handelt es sich um einen Mechanismus, bei dem mindestens ein Reviewer Kommentare zu einem Asset machen kann, das in einem Formular verfügbar ist.

## Einrichten einer Überprüfung {#setting-up-a-review}

1. Gehen Sie zur Registerkarte „Formulare“ und wählen Sie ein Formular aus.
1. Wenn für das Asset derzeit keine Überprüfung durchgeführt wird, wird in der Aktionsleiste das Symbol ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) zum Starten einer Überprüfung angezeigt. Klicken Sie auf das Symbol zum Starten einer Überprüfung (![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png)).
1. Geben Sie folgende Informationen ein:

   * Überprüfungsname (erforderlich): Darf alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.
   * Überprüfungsbeschreibung (optional): Beschreibung des Zwecks/Inhalts der Überprüfung.
   * Überprüfungstermin (optional): Datum, an dem die Überprüfung beendet wird. Wenn die Frist bereits abgelaufen ist, wird die Aufgabe als „überfällig“ angezeigt.
   * Reviewer: Es muss mindestens ein Reviewer angegeben werden. Verwenden Sie das Kombinationsfeld, um Reviewer hinzuzufügen. Beim Eingeben eines Namens werden alle übereinstimmenden Namen aufgelistet. einen Namen auswählen und auf Hinzufügen klicken.

1. Füllen Sie alle weiteren Details aus und klicken Sie auf Start.

### Aktionen beim Einrichten von Überprüfungen {#actions-that-occur-when-a-review-is-set-up}

In diesem Abschnitt wird beschrieben, was passiert, wenn eine Überprüfung erstellt bzw. eingerichtet wird.

1. Eine neue Überprüfungsaufgabe wird erstellt und dem Initiator der Überprüfung zugewiesen.
1. Allen Reviewern wird eine Überprüfungsaufgabe zugeteilt. Die Aufgabe wird im Abschnitt Benachrichtigungen angezeigt. Reviewer können auf eine Benachrichtigung klicken oder zum Posteingang wechseln, um die Aufgabe anzuzeigen. Reviewer können per Klick die Überprüfungsaufgabe öffnen, das Formular anzeigen und Kommentare hinzufügen.

   ![Warnung bei Reviewerbenachrichtigungen](assets/noti.png)
   **Abbildung:** *Warnung zur Reviewer-Benachrichtigung*

1. Das Kommentarfeld ist für den Initiator und die Reviewer der Assets verfügbar. Andere können die Kommentare anzeigen, jedoch keine Kommentare schreiben.

## Verwalten einer Überprüfung {#managing-a-review}

>[!NOTE]
>
>Nur laufende Überprüfungen können geändert werden. Abgeschlossene Überprüfungen können nicht geändert werden.

1. Gehen Sie zur Registerkarte „Formulare“ und wählen Sie ein Formular aus.

1. Wenn bei einem Asset eine Überprüfung in Bearbeitung ist und Sie der Initiator der Überprüfung sind, wird in der Aktionsleiste das Symbol ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) zum Verwalten von Überprüfungen angezeigt. Nur Initiatoren von Überprüfungen können die Überprüfung verwalten (aktualisieren/beenden).

   Klicken Sie auf das Symbol ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) zum Verwalten der Überprüfung.

   Für Benutzer, die nicht der Initiator sind, ist das Symbol zum Verwalten von Überprüfungen deaktiviert.

1. Es wird ein Bildschirm mit folgenden Informationen anzeigt:

   * **Überprüfungsname**: Kann nicht bearbeitet werden.
   * **Überprüfungsbeschreibung**: Kann bearbeitet werden.
   * **Überprüfungstermin**: Kann bearbeitet werden. Die Werte für Datum und Uhrzeit des Termins können geändert werden, wenn sie in der Zukunft liegen.
   * **Reviewer**: Kann bearbeitet werden. Sie können Reviewer hinzufügen oder entfernen. Wenn eine Aufgabe überfällig ist, können Sie Reviewer erst hinzufügen, wenn Sie den Termin verlängern und er über das aktuelle Datum hinausgeht.

1. Bearbeiten Sie die erforderlichen Felder und klicken Sie auf Aktualisieren.

   ![Überprüfen des aktuellen Status im Task Manager](assets/tskmgr.png)
   **Abbildung:** *Aktualisierten Status in Task Manager überprüfen*

1. Zum Beenden der Überprüfung klicken Sie auf „Beenden“.

### Aktionen beim Bearbeiten einer Überprüfung {#actions-that-occur-when-a-review-is-modified}

In diesem Abschnitt wird beschrieben, was beim Beenden/Ändern von Überprüfungen passiert:

1. Wenn die Überprüfungsbeschreibung geändert wird, wird die entsprechende Aufgabe der Reviewer und des Initiators aktualisiert.
1. Wenn der Überprüfungstermin geändert wird, wird die entsprechende Aufgabe der Reviewer mit dem neuen Datum aktualisiert.

1. Wenn ein Reviewer entfernt wird:

   ![Entfernen eines Reviewers](assets/removeduser.png)
   **Abbildung:** *Validierer entfernen*

   1. Wenn die zugewiesene Aufgabe unvollständig ist, wird sie beendet.
   1. Der Reviewer kann das Asset nicht mehr kommentieren.

1. Wenn ein Reviewer hinzugefügt wird:

   ![Hinzufügen eines Reviewers](assets/addedreviewer.png)
   **Abbildung:** *Validierungsverantwortliche hinzufügen*

   1. Eine Überprüfungsaufgabe wird erstellt und dem neu hinzugefügten Reviewer zugewiesen.
   1. Der neu hinzugefügte Reviewer kann dem Asset Kommentare hinzufügen.

1. Wenn eine Überprüfung abgeschlossen wird:

   1. **Reviewer**: Bei allen Reviewern werden zugewiesene unvollständige Aufgaben beendet. Die Aufgabe wird im Benachrichtigungsabschnitt des Reviewers nicht mehr als „Ausstehend“ angezeigt.
   1. **Initiator**: Die dem Initiator der Überprüfung zugewiesene Aufgabe ist als abgeschlossen markiert. Die Aufgabe wird aus dem Benachrichtigungsabschnitt des Initiators der Überprüfung entfernt.
   1. **Alle**: Die Überprüfung wird im Abschnitt Frühere Prüfungen angezeigt. Es können keine weiteren Kommentare hinzugefügt werden.
