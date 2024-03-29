---
title: Konfigurieren der Server-Einstellungen
seo-title: Configuring Server Settings
description: Auf der Seite "Servereinstellungen"können Sie auf die Einstellungen für E-Mails, Aufgabenbenachrichtigungen und Administratorbenachrichtigungen zugreifen.
seo-description: The Server Settings page provides access to email, task notification and administrator notification settings.
uuid: 73b51ac0-56e5-4748-bb33-e3986c69eb2d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e047a95e-0acb-438a-8d27-f005c0adc508
exl-id: 7933efeb-618a-4c38-8e5e-593be8ebb00c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2661'
ht-degree: 22%

---

# Konfigurieren der Server-Einstellungen {#configuring-server-settings}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Seite &quot;Servereinstellungen&quot;bietet Zugriff auf verschiedene Einstellungen für den Arbeitsablauf für Formulare:

* **E-Mail-Einstellungen** die ausgehende E-Mail-Nachrichten sowie die für diese Nachrichten verwendeten E-Mail-Server-Einstellungen aktivieren. (Siehe [E-Mail-Einstellungen konfigurieren](configuring-server-settings.md#configuring-email-settings).
* **Aufgabenbenachrichtigungseinstellungen,** die mit E-Mail-Benachrichtigungen an Endbenutzer und Gruppen gesendeten Nachrichten zu Aufgaben aktivieren, deaktivieren oder ändern. (Siehe [Benachrichtigungen für Benutzer und Gruppen konfigurieren](configuring-server-settings.md#configuring-notifications-for-users-and-groups).)
* **Administratorbenachrichtigungseinstellungen,** die mit E-Mail-Benachrichtigungen gesendeten Nachrichten zu Verwaltungsaufgaben aktivieren, deaktivieren oder ändern. (Siehe [Benachrichtigungen für Administratoren konfigurieren](configuring-server-settings.md#configuring-notifications-for-administrators).

## E-Mail-Einstellungen konfigurieren {#configuring-email-settings}

Sie können ein E-Mail-Konto für den Formularserver angeben, über das dieser E-Mail-Nachrichten an AEM Benutzer und Administratoren von Formularen sendet. Diese E-Mail-Nachrichten werden verwendet, um Benutzer auf die Aufgaben aufmerksam zu machen, die sie ausführen müssen, den Benutzer über Aufgaben zu informieren, für die ein Termin erreicht wurde, und den Administrator über eventuelle Prozessfehler zu informieren.

Um das Senden von E-Mail-Nachrichten zwischen AEM Formularen und Benutzern zu aktivieren, konfigurieren Sie die Einstellungen für ausgehende E-Mails auf der Seite E-Mail-Einstellungen . Ausgehende E-Mails müssen einen SMTP-Server verwenden.

Damit AEM Forms eingehende E-Mail-Nachrichten von Benutzern empfangen und verarbeiten kann, müssen Sie einen E-Mail-Endpunkt für den Complete Task-Dienst erstellen. (Siehe [E-Mail-Endpunkt für den Complete Task-Dienst erstellen](/help/forms/using/admin-help/configuring-email-endpoints.md#create-an-email-endpoint-for-the-complete-task-service)).

Wenn Ihre Prozesse ohne E-Mail-Empfang konzipiert und implementiert wurden, müssen Sie keine der Optionen auf der Seite E-Mail-Einstellungen konfigurieren.

### Ausgehende E-Mail-Einstellungen konfigurieren {#configure-outgoing-email-settings}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Servereinstellungen&quot;> &quot;E-Mail-Einstellungen&quot;.
1. Wählen Sie Ausgehende Nachrichten aktivieren aus.
1. Geben Sie in das Feld SMTP Server den Namen des E-Mail-Servers oder die IP-Adresse ein. Alle Benachrichtigungs-E-Mail-Nachrichten aus dem Arbeitsablauf für Formulare werden von diesem E-Mail-Server gesendet.
1. Geben Sie in die Felder &quot;Benutzername&quot;und &quot;Kennwort&quot;den Anmeldenamen und das Kennwort ein, die verwendet werden sollen, wenn der SMTP-Server eine Authentifizierung erfordert. Lassen Sie sie leer, wenn die anonyme Anmeldung zulässig ist.
1. Geben Sie im Feld &quot;E-Mail-Adresse&quot;die E-Mail-Adresse ein, die als Rücksenderadresse für E-Mail-Nachrichten verwendet werden soll, die vom Arbeitsablauf für Formulare gesendet werden.

   >[!NOTE]
   >
   >Wenn Sie Microsoft Exchange Server verwenden und die E-Mail-Adresse eine ungültige E-Mail-Adresse ist, kann der Microsoft Exchange-Server keine E-Mail an die Verteilerlisten senden. Um dieses Problem zu beheben, aktivieren Sie die Option **Externe Kommunikation aktivieren** separat für jede Verteilerliste auf Microsoft Exchange Server. 

1. Klicken Sie auf Speichern.

>[!NOTE]
>
>Wenn Sie falsche Informationen eingeben, können Sie auf Abbrechen klicken, um zur zuvor angezeigten Seite zurückzukehren.

### E-Mail-Vorlagen für die Verwendung von AEM Forms Workspace konfigurieren {#configuring-email-templates-to-use-html-workspace}

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

Standardmäßig enthalten die von AEM Formularen gesendeten E-Mails Links zu Flex Workspace (nicht mehr unterstützt für AEM Forms on JEE). Sie können AEM Forms so konfigurieren, das E-Mails mit Links zu AEM Forms Workspace gesendet werden. Weitere Informationen zu den Vorteilen von AEM Forms Workspace gegenüber Flex Workspace (nicht mehr unterstützt für AEM Forms on JEE) finden Sie unter [this](/help/forms/using/features-html-workspace-available-flex.md) Artikel.

1. Klicken Sie in Administration Console auf &quot;Startseite&quot;> &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Servereinstellungen&quot;> &quot;Aufgabenbenachrichtigungen&quot;.
1. Öffnen Sie die Aufgabenzuweisungsvorlage.
1. Legen Sie die Vorlage in den Aufgabenbenachrichtigungen auf folgendes fest:  `https://@@notification-host@@:8080/lc/libs/ws/index.html?taskId=@@taskid@@`

   ```as3
   https://@@notification-host@@:8080/lc/libs/ws/index.html?taskId=@@taskid@@
   ```

## Benachrichtigungen für Benutzer und Gruppen konfigurieren {#configuring-notifications-for-users-and-groups}

Auf der Seite &quot;Aufgabenbenachrichtigung&quot;können Sie Vorlagen konfigurieren, die der Arbeitsablauf für Formulare verwendet, um die E-Mail-Benachrichtigungen zu generieren, die an Benutzer und Gruppen gesendet werden. Sie können die Benachrichtigungen mithilfe von Variablen des Arbeitsablaufs für Formulare anpassen und formatieren.

Sie konfigurieren die folgenden Benachrichtigungstypen für Benutzer und Gruppen:

* Erinnerungen
* Aufgabenzuweisungen
* Termine

Um E-Mail-Benachrichtigungen für eine Gruppe zu generieren, geben Sie in User Management eine E-Mail-Adresse für die Gruppe an. <!--Fix broken link See Setting up and organizing users -->Wenn der Arbeitsablauf für Formulare eine E-Mail-Benachrichtigung an eine Gruppe sendet, geht die Benachrichtigung an jedes Mitglied der Gruppe, dessen E-Mail-Adresse angegeben ist. Wenn ein Mitglied der Gruppe eine E-Mail-Benachrichtigung erhält und die Aufgabe anfordern möchte, muss das Mitglied in der E-Mail-Benachrichtigung auf den Anforderungslink klicken, wodurch die Aufgabendetailseite in Workspace geöffnet wird. Von dort aus kann das Mitglied das Arbeitselement entweder anfordern oder anfordern und öffnen.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

### Erinnerungen für Benutzer oder Gruppen konfigurieren {#configure-reminders-for-users-or-groups}

Sie können Erinnerungsbenachrichtigungen an den zugewiesenen Benutzer oder die zugewiesene Gruppe senden, wenn ein Termin zum Abschließen einer Aufgabe näher rückt. Die Regeln, die genau bestimmen, wann eine Erinnerungsbenachrichtigung gesendet wird, werden vom Prozessentwickler festgelegt.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Servereinstellungen&quot;> &quot;Aufgabenbenachrichtigungen&quot;.
1. Klicken Sie unter &quot;Benachrichtigungstyp&quot;für Benutzer auf Erinnerung oder für Gruppen auf Gruppe - Erinnerung .
1. Wählen Sie &quot;Erinnerung aktivieren&quot;oder &quot;Gruppe - Erinnerung aktivieren&quot;.
1. (Nur für Benutzerbenachrichtigungen) Um eine Anlage des Formulars und seiner Daten mit der Erinnerungsnachricht einzuschließen, wählen Sie &quot;Formulardaten einschließen&quot;.
1. Geben Sie in das Feld Betreff den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Geben Sie im Feld &quot;Benachrichtigungsvorlage&quot;den Text für den Nachrichtentext der E-Mail ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Wählen Sie in der Liste &quot;Nachrichtenformat&quot;das Format aus, in dem die E-Mail-Nachricht gesendet wird, entweder HTML oder Text. Das Standardformat ist HTML.
1. Wählen Sie in der Liste E-Mail-Kodierung das Kodierungsformat für die E-Mail-Nachricht aus. Die Standardeinstellung ist UTF-8, die von den meisten Benutzern außerhalb Japans verwendet wird. Benutzer in Japan können &quot;ISO2022-JP&quot;auswählen.
1. Klicken Sie auf Speichern.

### Benachrichtigungen für Aufgabenzuweisungen für Benutzer oder Gruppen konfigurieren {#configure-task-assignment-notifications-for-users-or-groups}

Sie können Benachrichtigungen über Aufgabenzuweisungen an einen Benutzer oder eine Gruppe senden, wenn ihm eine Aufgabe zugewiesen wird.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Servereinstellungen&quot;> &quot;Aufgabenbenachrichtigungen&quot;.
1. Klicken Sie unter &quot;Benachrichtigungstyp&quot;für Benutzer auf Aufgabenzuweisung oder für Gruppen auf Gruppe - Aufgabenzuweisung .
1. Wählen Sie &quot;Aufgabenzuweisung für Benutzer aktivieren&quot;oder &quot;Gruppe - Aufgabenzuweisung für Gruppen aktivieren&quot;.
1. (Nur für Benutzerbenachrichtigungen) Um eine Anlage des Formulars und seiner Daten in die E-Mail-Nachricht zur Aufgabenzuweisung einzuschließen, wählen Sie &quot;Formulardaten einschließen&quot;.
1. Geben Sie in das Feld Betreff den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Geben Sie im Feld &quot;Benachrichtigungsvorlage&quot;den Text für den Nachrichtentext der E-Mail ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Wählen Sie in der Liste &quot;Nachrichtenformat&quot;das Format aus, in dem die E-Mail-Nachricht gesendet wird, entweder HTML oder Text. Das Standardformat ist HTML.
1. Wählen Sie in der Liste E-Mail-Kodierung das Kodierungsformat für die E-Mail-Nachricht aus. Die Standardeinstellung ist UTF-8, die von den meisten Benutzern außerhalb Japans verwendet wird. Benutzer in Japan können &quot;ISO2022-JP&quot;auswählen.
1. Klicken Sie auf Speichern.

### Konfigurieren von Terminbenachrichtigungen für Benutzer oder Gruppen {#configure-deadline-notifications-for-users-or-groups}

Sie können Benutzern und Gruppen Terminbenachrichtigungen senden, wenn die Frist für die Bearbeitung einer zugewiesenen Aufgabe abgelaufen ist. Eine Terminbenachrichtigung ist in der Regel informativ, da der Benutzer die zugewiesene Aufgabe nicht mehr bearbeiten kann.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Servereinstellungen&quot;> &quot;Aufgabenbenachrichtigungen&quot;.
1. Klicken Sie unter &quot;Benachrichtigungstyp&quot;auf &quot;Deadline (für Benutzer)&quot;oder &quot;Gruppe - Deadline&quot;(für Gruppen).
1. Wählen Sie &quot;Deadline aktivieren&quot;oder &quot;Gruppe - Deadline aktivieren&quot;.
1. Geben Sie in das Feld Betreff den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Geben Sie im Feld &quot;Benachrichtigungsvorlage&quot;den Text für den Nachrichtentext der E-Mail ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Wählen Sie in der Liste &quot;Nachrichtenformat&quot;das Format aus, in dem die E-Mail-Nachricht gesendet wird, entweder HTML oder Text. Das Standardformat ist HTML.
1. Wählen Sie in der Liste E-Mail-Kodierung das Kodierungsformat für die E-Mail-Nachricht aus. Die Standardeinstellung ist UTF-8, die von den meisten Benutzern außerhalb Japans verwendet wird. Benutzer in Japan können &quot;ISO2022-JP&quot;auswählen.
1. Klicken Sie auf Speichern.

### Das Tag DO NOT DELETE für alle E-Mails ausblenden {#hide-the-do-not-delete-tag-for-all-emails}

Sie können die E-Mails so konfigurieren, dass der Verfolgungstag „DO NOT DELETE“ in allen E-Mails ausgeblendet wird, die in einem am Menschen orientierten Prozess gesendet werden.

## Benachrichtigungen für Administratoren konfigurieren {#configuring-notifications-for-administrators}

Sie können Vorlagen konfigurieren, die der Arbeitsablauf für Formulare verwendet, um die E-Mail-Benachrichtigungen zu generieren, die an Administratoren gesendet werden.

Sie konfigurieren die folgenden Benachrichtigungstypen für Administratoren:

* Angehaltener Zweig
* Angehaltener Vorgang

### Benachrichtigungen bei angehaltenen Zweigen konfigurieren {#configure-stalled-branch-notifications}

Wenn ein Zweig anhält (also die Fortsetzung absichtlich oder wegen eines Fehlers beendet wird), können Sie eine E-Mail-Benachrichtigung an einen Administrator oder einen anderen Benutzer senden, der dann das Problem untersuchen kann.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Servereinstellungen&quot;> &quot;Administratorbenachrichtigungen&quot;.
1. Klicken Sie unter &quot;Benachrichtigungstyp&quot;auf &quot;Angehaltener Zweig&quot;.
1. Wählen Sie Angehaltene Verzweigung aktivieren aus.
1. Geben Sie in das Feld &quot;E-Mail-Adresse&quot;die Adressen der Benutzer ein, die benachrichtigt werden sollen, wenn eine Verzweigung anhält. Sie müssen das Format „Benutzer@Domain.com“ verwenden und jede Adresse durch ein Komma abtrennen. Normalerweise ist diese E-Mail-Adresse für einen Administrator bestimmt.
1. Geben Sie in das Feld Betreff den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Geben Sie im Feld &quot;Benachrichtigungsvorlage&quot;den Text für den Nachrichtentext der E-Mail ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Wählen Sie in der Liste &quot;Nachrichtenformat&quot;das Format aus, in dem die E-Mail-Nachricht gesendet wird, entweder HTML oder Text. Das Standardformat ist HTML.
1. Wählen Sie in der Liste E-Mail-Kodierung das Kodierungsformat für die E-Mail-Nachricht aus. Der Standardwert ist UTF-8, den die meisten Benutzer außerhalb Japans verwenden. Benutzer in Japan können &quot;ISO2022-JP&quot;auswählen.
1. Klicken Sie auf Speichern.

### Benachrichtigungen bezüglich angehaltener Vorgänge konfigurieren {#configure-stalled-operation-notifications}

Wenn ein Vorgang angehalten wird (also die Fortsetzung absichtlich oder aufgrund eines Fehlers beendet wird), können Sie eine E-Mail-Benachrichtigung an einen Administrator oder einen anderen Benutzer senden, der das Problem untersuchen kann.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Servereinstellungen&quot;> &quot;Administratorbenachrichtigungen&quot;.
1. Klicken Sie unter &quot;Benachrichtigungstyp&quot;auf &quot;Angehaltener Vorgang&quot;.
1. Wählen Sie &quot;Angehaltener Vorgang aktivieren&quot;.
1. Geben Sie im Feld &quot;E-Mail-Adressen&quot;die Adressen der Benutzer ein, die benachrichtigt werden sollen, wenn ein Vorgang anhält. Sie müssen das Format „Benutzer@Domain.com“ verwenden und jede Adresse durch ein Komma abtrennen. Normalerweise ist diese E-Mail-Adresse für einen Administrator bestimmt.
1. Geben Sie in das Feld Betreff den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications)
1. Geben Sie im Feld &quot;Benachrichtigungsvorlage&quot;den Text für den Nachrichtentext der E-Mail ein. Dieses Feld enthält bereits den Standardtext. Weitere Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Benachrichtigungen anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Klicken Sie auf Speichern.

## Inhalt von Benachrichtigungen anpassen {#customizing-the-content-of-notifications}

Die Seiten &quot;Aufgabenbenachrichtigungen&quot;und &quot;Administratorbenachrichtigungen&quot;bieten verschiedene Funktionen, mit denen Sie Benachrichtigungsinhalte anpassen können:

* Rich-Text-Editor
* Variablenauswahl
* URL-Generierung

### Rich-Text-Editor {#rich-text-editor}

Der Bereich &quot;Benachrichtigungsvorlage&quot;ist ein Rich-Text-Editor, mit dem Sie HTML für die E-Mail-Benachrichtigungsinhalte generieren können. Es bietet Schriftart- und Absatzformatierungsoptionen, die unter dem Feld &quot;Benachrichtigungsvorlage&quot;zu finden sind. Zu den Optionen gehören Schriftart, Größe, Stil und Farbe sowie Absatzausrichtung und Aufzählungszeichen.

### URL-Generierung {#url-generation}

Nur für Aufgabenbenachrichtigungen umfasst der Forms-Workflow zwei vordefinierte URL-Konfigurationen, die Sie aus der Liste &quot;URL-Erstellung&quot;in das Feld &quot;Benachrichtigungsvorlage&quot;ziehen und dann anpassen können:

* OpenTask ist für die Benachrichtigungstypen Erinnerung und Aufgabenzuweisung verfügbar. Diese URL bietet eine Verknüpfung mit der Aufgabe in Workspace, wodurch der Benutzer schnell aus der E-Mail-Benachrichtigung heraus auf die Aufgabe zugreifen kann. Wenn Sie die OpenTask-URL in das Feld &quot;Benachrichtigungsvorlage&quot;ziehen, weist die URL folgendes Format auf:

   `https://@@notification-host@@:<PORT>/workpace/Main.html?taskId=@@taskid@@`

* ClaimTask ist für die Benachrichtigungstypen Gruppe - Erinnerung und Gruppe - Aufgabenzuweisung verfügbar. Diese URL bietet einen Link zur Aufgabendetailseite in Workspace, auf der der Benutzer das Arbeitselement entweder anfordern oder anfordern und öffnen kann. Wenn Sie die ClaimTask-URL in das Feld &quot;Benachrichtigungsvorlage&quot;ziehen, weist die URL das folgende Format auf:

   `https://@@notification-host@@:<PORT>/workpace/Main.html?taskId=@@taskid@@`

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

Wenn Ihre Lösung in einer Cluster-Umgebung bereitgestellt wird, ersetzen Sie `@@notification-host@@` durch die Cluster-Adresse.

`<`*PORT* `>` ist die Port-Nummer des HTTP-Listeners für den Programm-Server. Der Standardanschluss für HTTP-Listener für die unterstützten Anwendungsserver lautet wie folgt:

**JBoss:** 8080

**Oracle WebLogic Server**: 7001

**IBM WebSphere**: 9080

Damit diese URLs korrekt funktionieren, müssen Sie `<`*PORT* `>` durch die Port-Nummer ersetzen, die für Ihre Umgebung geeignet ist.

>[!NOTE]
>
>Wenn Sie eine andere benutzerdefinierte Webanwendung als Forms verwenden, um Benutzern Zugriff auf die Aufgaben zu gewähren, müssen Sie stattdessen ein URL-Format verwenden, das für Ihre benutzerdefinierte Anwendung geeignet ist.

### Variablenauswahl {#variable-picker}

Die Variablenauswahlliste bietet nützliche Variablen, die Sie per Drag &amp; Drop in die Felder &quot;Betreff&quot;oder &quot;Benachrichtigungsvorlage&quot;ziehen können. Beim Ablegen einer Variablen in einem der Felder „Betreff“ oder „Benachrichtigungsvorlage“ ändert sich deren Name in den tatsächlichen Namen der Variablen des Workflows für Formulare mit je zwei führenden und nachfolgenden @-Symbolen, z. B. `@@taskid@@`.

Für Erinnerungen, Aufgabenzuweisungen und Termine für Benutzer und Gruppen können Sie die folgenden Variablen in den Feldern „Betreff“ und „Benachrichtigungsvorlage“ verwenden:

**description** Der Inhalt der Eigenschaft „Beschreibung“, wie in Workbench im Benutzervorgang (Startpunkt oder Vorgang zum Zuweisen einer oder mehrerer Aufgaben) für den Prozess definiert.

**instructions**: Der Inhalt der Eigenschaft „Aufgabenanweisungen“, wie in Workbench im Benutzervorgang für den Prozess definiert.

**notification-host** Der Host-Name des AEM Forms-Programm-Servers.

**process-name** Der Name des Vorgangs.

**operation-name** Der Name des Schritts.

**taskid** Die eindeutige Kennung der aktuellen Aufgabe.

**actions** Erzeugt eine nummerierte Liste gültiger Routen (z. B. Genehmigen, Ablehnen), auf die der Empfänger klicken kann.

Zusätzlich können für Gruppenerinnerungen, Gruppenaufgabenzuweisungen und Gruppentermine folgende Variablen verwendet werden:

**group-name** Der Name der Gruppe, der das Arbeitselement zugeordnet ist.

>[!NOTE]
>
>Wenn eine Variable keinen Wert hat, wird nichts zurückgegeben.

Für angehaltene Zweige können Sie die folgenden Variablen in den Feldern Betreff und Benachrichtigungsvorlage verwenden:

**branch-id** Die Zweig-ID.

**process-id** Die Prozessinstanz-ID.

**notification-host** Der Host-Name des AEM Forms-Programm-Servers.

Für angehaltene Vorgänge können Sie die folgenden Variablen in den Feldern „Betreff“ und „Benachrichtigungsvorlage“ verwenden:

**action-id** Die Vorgangs-ID.

**branch-id** Die Zweig-ID.

**process-id** Die Prozessinstanz-ID.

**notification-host** Der Host-Name des AEM Forms-Programm-Servers.

### Variable im Feld &quot;Betreff&quot;verwenden {#using-a-variable-in-the-subject-box}

Wenn Sie den folgenden Text in das Feld &quot;Betreff&quot;für Benachrichtigungen über Aufgabenzuweisungen eingeben:

`Please complete task @@taskid@@`

Erhält der Benutzer eine E-Mail-Nachricht mit dem folgenden Betreff, wenn die Aufgabe 376 zugewiesen ist:

`Please complete task 376`

### Verwenden von Variablen im Feld &quot;Benachrichtigungsvorlage&quot; {#using-variables-in-the-notification-template-box}

Wenn Sie den folgenden Text in das Feld &quot;Benachrichtigungsvorlage&quot;für Benachrichtigungen über angehaltene Verzweigungen eingeben:

`Branch @@branch-id@@ has stalled! You have received this notification from @@notification-host@@.`

Erhält der Administrator eine E-Mail-Nachricht mit folgendem Inhalt, wenn die Zweignummer „4868“ und der Name des Servers `ServerXYZ` ist:

`Branch 4868 has stalled! You have received this notification from ServerXYZ.`

## Verbindungen zur Business Activity Monitoring konfigurieren {#configuring-business-activity-monitoring-connections}

Business Activity Monitoring, ein optionales Modul, bietet eine Reihe operativer Dashboards, die eine Echtzeit-Sichtbarkeit Ihrer Vorgänge und wichtigen Leistungsindikatoren bieten.

Auf der Seite &quot;BAM-Konfigurationseinstellungen&quot;legen Sie die Verbindungen zum Server fest, auf dem BAM ausgeführt wird, damit prozessbezogene Ereignisse verfolgt und an diesen Server übertragen werden können.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Servereinstellungen&quot;> &quot;BAM-Konfigurationseinstellungen&quot;.
1. Geben Sie in das Feld &quot;BAM Host&quot;den Namen des Servers ein, auf dem BAM ausgeführt wird. Die Standardeinstellung ist localhost.
1. Geben Sie in das Feld &quot;BAM Port&quot;den Anschluss ein, über den eine Verbindung zu dem Server hergestellt werden soll, auf dem BAM ausgeführt wird. Der standardmäßige BAM-Port für JBoss ist 8080, WebLogic ist 7001 und WebSphere ist 9080.
1. Geben Sie in das Feld &quot;Server Host&quot;den Namen oder die IP-Adresse des Host-Formularservers ein. Der Standardwert lautet localhost.
1. Geben Sie in das Feld &quot;Server Port&quot;die vom Formularserver verwendete Anschlussnummer ein.
1. Geben Sie in die Felder &quot;Benutzername&quot;und &quot;Kennwort&quot;die entsprechende Benutzer-ID und das Kennwort für den Zugriff auf den BAM-Server ein. Der Standardbenutzername lautet CognosNowAdmin und das Standardkennwort lautet manager.
1. Klicken Sie auf Speichern.
