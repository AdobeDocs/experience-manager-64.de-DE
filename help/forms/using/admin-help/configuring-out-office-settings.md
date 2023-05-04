---
title: Konfigurieren von Abwesenheitseinstellungen
seo-title: Configuring Out of Office Settings
description: Die Abwesenheitsfunktion ermöglicht es Ihnen, Zeiträume anzugeben, in denen ein Benutzer nicht im Hause und deshalb nicht in der Lage ist, vom Arbeitsablauf für AEM Forms zugewiesene Aufgaben auszuführen.
seo-description: The Out of Office feature enables you to specify when a user will be out of the office and unable to complete tasks assigned by AEM forms.
uuid: 0d01df0a-aa6a-40e5-bf24-423ed1c932cc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 30312159-58a5-4781-b554-29dcbce696cb
exl-id: 8787ffa9-9ddc-439d-9934-8913d1ed459e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 15%

---

# Konfigurieren von Abwesenheitseinstellungen {#configuring-out-of-office-settings}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Abwesenheitsfunktion ermöglicht es Benutzern und Administratoren, Zeiträume anzugeben, in denen ein Benutzer nicht im Hause und deshalb nicht in der Lage ist, vom Arbeitsablauf für AEM Forms zugewiesene Aufgaben auszuführen. Während ein Benutzer auf Abwesenheit festgelegt ist, werden seine Aufgaben einem oder mehreren bestimmten Benutzern zugewiesen. Benutzer können ihre Abwesenheitseinstellungen in Workspace ändern bzw. Administratoren können die Einstellungen im Auftrag eines Benutzers im Arbeitsablauf für Formulare ändern.

Beim Erstellen eines Prozesses kann der Workbench-Benutzer angeben, ob eine Aufgabe aufgrund von Abwesenheitseinstellungen umgeleitet werden kann.

## Abwesenheitsinformationen eines Benutzers anzeigen {#view-a-user-s-out-of-office-information}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Abwesenheit&quot;.
1. Im Feld oben auf der Seite &quot;Abwesenheit&quot;können Sie einen der folgenden Schritte ausführen:

   **Suche nach Name**

   Wählen Sie die Option Suche nach Name aus. Geben Sie den gesamten Benutzernamen oder einen Teil davon ein und klicken Sie auf &quot;Suchen&quot;. Wenn Sie das Feld leer lassen, gibt der Forms-Workflow eine Liste aller Benutzer zurück

   **Suche nach Datumsbereich**

   Wählen Sie die Option Suche nach Datumsbereich aus. Geben Sie die Daten von und bis sowie die gewünschten Zeitstempel an, um das Suchergebnis einzuschränken. Klicken Sie auf „Suchen“.

1. Klicken Sie auf einen Benutzernamen, um die Abwesenheitsinformationen des Benutzers unter der Liste der Benutzer anzuzeigen.

## Abwesenheitsstatus eines Benutzers ändern {#change-a-user-s-out-of-office-status}

1. Suchen Sie den Benutzer, wie unter [Abwesenheitsinformationen eines Benutzers anzeigen](configuring-out-office-settings.md#view-a-user-s-out-of-office-information).
1. Klicken Sie auf den Namen des Benutzers, den Sie ändern möchten.
1. Aus dem *Benutzername* derzeit aufgeführt ist, wählen Sie entweder &quot;Im Büro&quot;oder &quot;Nicht im Hause&quot;aus.
1. Klicken Sie auf Speichern.

## Einen Abwesenheitsdatumsbereich für einen Benutzer hinzufügen {#add-an-out-of-office-date-range-for-a-user}

1. Suchen Sie den Benutzer, wie unter [Abwesenheitsinformationen eines Benutzers anzeigen](configuring-out-office-settings.md#view-a-user-s-out-of-office-information).
1. Klicken Sie auf den Namen des Benutzers, den Sie ändern möchten.
1. Klicken Sie auf Datumsbereich hinzufügen .
1. Geben Sie eine Startzeit und Endzeit ein. Sie können auf das Kalendersymbol klicken, um ein Datum auszuwählen. Wenn Sie keine Endzeit angeben, wird der Benutzer auf unbestimmte Zeit als abwesend festgelegt.
1. Klicken Sie auf Speichern.

## Benutzer für Abwesenheitsaufgaben zuweisen {#assign-a-user-for-out-of-office-tasks}

Während ein Benutzer nicht im Büro ist, können Sie einen oder mehrere Benutzer zuweisen, die alle neuen Aufgaben für den Benutzer ausführen. Sie können die folgenden Konfigurationen einrichten:

* Weisen Sie alle neuen Aufgaben einem festgelegten Standardbenutzer zu.
* Weisen Sie keine Aufgaben zu. Neue Aufgaben bleiben dem abwesenden Benutzer zugewiesen.
* Weisen Sie einen Standardbenutzer zu, der die meisten Aufgaben des Benutzers erhält, geben Sie jedoch an, dass Aufgaben aus bestimmten Prozessen anderen Benutzern neu zugewiesen werden oder dem Abwesenheitsbenutzer zugewiesen bleiben.
* Weisen Sie keinen Standardbenutzer zu, sondern weisen Sie bestimmten Benutzern bestimmte Aufgaben aus bestimmten Prozessen zu.

   1. Suchen Sie den Benutzer, wie unter [Abwesenheitsinformationen eines Benutzers anzeigen](configuring-out-office-settings.md#view-a-user-s-out-of-office-information).
   1. Klicken Sie auf den Namen des Benutzers, den Sie ändern möchten.
   1. Wählen Sie in der Liste &quot;Standardbenutzer für Abwesenheitsaufgaben&quot;einen Benutzer aus der Liste aus. Wenn Sie keinen Standardbenutzer für den Empfang neu zugewiesener Elemente festlegen möchten, wählen Sie &quot;Nicht zuweisen&quot;aus.

      Wenn der entsprechende Benutzername nicht in der Liste angezeigt wird, klicken Sie auf &quot;Benutzer suchen&quot;und suchen Sie im Dialogfeld &quot;Benutzer suchen&quot;nach dem Benutzer. Wählen Sie den entsprechenden Benutzer aus der Liste aus und klicken Sie auf Benutzer auswählen . Sie können auch im Dialogfeld &quot;Benutzer suchen&quot;auf &quot;Zeitplan des Benutzers anzeigen&quot;klicken, um den Abwesenheitszeitplan des ausgewählten Benutzers anzuzeigen.

   1. Wenn Prozesse vorhanden sind, die nicht an den Standardbenutzer gesendet werden sollen, klicken Sie auf Ausnahme hinzufügen , wählen Sie den Prozess aus und wählen Sie einen anderen Benutzer aus der Liste aus. Sie können auch Nicht zuweisen auswählen, damit die Aufgabe dem abwesenden Benutzer zugewiesen bleibt.
   1. Klicken Sie auf Speichern.
