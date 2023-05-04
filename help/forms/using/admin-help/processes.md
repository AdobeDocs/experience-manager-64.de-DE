---
title: Verwalten von Prozessen
seo-title: Managing Processes
description: Auf der Seite "Prozessliste"werden die Prozesse angezeigt, die von einem Benutzer initiiert oder automatisch gestartet wurden. Erfahren Sie mehr über die Verwaltung der Prozesse.
seo-description: The Process List page shows the processes that a user has initiated or that were started automatically. Learn more about managing the processes.
uuid: 4cd17400-681a-4e40-996c-7dda57ce449a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 37e702c2-8716-4360-a3eb-d9877b28cc86
exl-id: 322cc7c2-0f24-4ed9-9af2-61b036324f46
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 40%

---

# Verwalten von Prozessen {#managing-processes}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Auf der Seite &quot;Prozessliste&quot;werden die Prozesse angezeigt, die von einem Benutzer initiiert oder automatisch gestartet wurden.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Arbeitsablauf für Formulare“. Die Prozessliste enthält die folgenden Informationen:

   **Prozessname - Version:** Der Name des Prozesses, wie in Workbench definiert.

   **Anwendung:** Die Anwendung, zu der der Prozess gehört, wie in Workbench definiert.

   **Status:** Aktiv bedeutet, dass es sich um den Prozess handelt, der für die Prozessversion aktiviert wurde. Inaktiv bedeutet, dass der Prozess eine alte Version ist, von der immer noch Prozessinstanzen vorhanden sind.

   **Erstellungsdatum:** Datum und Uhrzeit der Bereitstellung des Prozesses.

1. Klicken Sie auf einen Prozessnamen, um seine Prozessinstanzen auf der Seite &quot;Prozessinstanz&quot;anzuzeigen.

## Arbeiten mit Prozessinstanzen {#working-with-process-instances}

Wenn Sie über die Seite &quot;Prozessliste&quot;auf die Seite &quot;Prozessinstanz&quot;zugreifen, werden alle Prozessinstanzen des ausgewählten Prozesses aufgelistet. Wenn Sie nach der Durchführung einer Suche auf die Seite &quot;Prozessinstanz&quot;zugreifen, werden nur die gefundenen Prozessinstanzen aufgelistet.

Für jede Prozessinstanz werden in der Liste die folgenden Informationen angezeigt:

**Prozess-ID:** Dieser Bezeichner wird vom Formular-Workflow zugewiesen, wenn der Prozess instanziiert (d. h. von einem Benutzer oder einem automatisierten Schritt initiiert) wird. Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname - Version:** Der Name des Prozesses, wie in Workbench definiert.

**Status:** Zeigt an, ob die Prozessinstanz normal ausgeführt wird, den Status wechselt oder beendet wurde. (Siehe Informationen zum Status von Prozessinstanzen.)

**Erstellungsdatum:** Datum und die Uhrzeit, zu der die Prozessinstanz erstellt wurde.

**Aktualisierungsdatum:** Datum und Uhrzeit der letzten Änderung des Status der Prozessinstanz.

Auf der Seite &quot;Prozessinstanz&quot;können Sie die folgenden Aufgaben ausführen:

* Wählen Sie eine Prozessinstanz aus, um Details wie Vorgänge und Teilprozesse anzuzeigen. Wenn Sie eine Prozessinstanz auswählen, wird die Seite &quot;Prozessinstanzdetails&quot;angezeigt.
* Prozessinstanzen aussetzen, aussetzen oder beenden.
* Suchen Sie nach einer Prozessinstanz. Um eine Suche zu starten, klicken Sie auf &quot;Suchen&quot;.

### Informationen zum Status von Prozessinstanzen {#about-process-instance-statuses}

Eine Prozessinstanz, einschließlich Teilprozessen, kann die folgenden Status haben:

**ABGESCHLOSSEN:** Alle Zweige und Vorgänge in der Prozessinstanz wurden abgeschlossen. Dies ist der endgültige Status einer Prozessinstanz.

**ABSCHLIESSEND:** Der Status der Prozessinstanz ist dabei, auf ABGESCHLOSSEN zu wechseln.

**INITIALISIERT:** Die Prozessinstanz wurde erstellt, wird aber noch nicht ausgeführt. Dies ist der erste Status einer Prozessinstanz.

**WIRD AUSGEFÜHRT:** Die Prozessinstanz wird normal ausgeführt. Möglicherweise ist ein automatischer Schritt aktiv oder die Prozessinstanz empfängt eventuell Benutzereingaben bzw. wartet auf Benutzerinteraktion.

**AUSGESETZT:** Die Prozessinstanz wurde von einem Administrator oder einem Schritt im Prozess ausgesetzt. Bis zur Änderung des Status werden keine weiteren Vorgänge ausgeführt.

**AUSSETZEND:** Der Status ist dabei, auf AUSGESETZT zu wechseln. Wenn ein Vorgang so angelegt wurde, dass er Aussetzanforderungen ignoriert, und dieser noch nicht abgeschlossen ist, muss dieser Vorgang zuerst abgeschlossen werden, damit die Prozessinstanz ausgesetzt werden kann.

**BEENDET:** Die Prozessinstanz wurde von einem Administrator beendet.

**ABSCHLIESSEND:** Der Status ist dabei, auf BEENDET zu wechseln. Wenn ein Vorgang so angelegt wurde, dass er Beenden-Anforderungen ignoriert, und dieser noch nicht abgeschlossen ist, muss dieser Vorgang zuerst abgeschlossen werden, damit die Prozessinstanz beendet werden kann.

**AUSSETZUNG WIRD AUFGEHOBEN:** Der Status ist dabei, von AUSGESETZT auf WIRD AUSGEFÜHRT zu wechseln.

>[!NOTE]
>
>Wenn eine Anforderung zum Ändern des Status einer Prozessinstanz gestellt wird (z. B. zum Aussetzen oder Beenden), wird die Anforderung in die Befehlswarteschlange für den Arbeitsablauf für Formulare eingereiht. Je nach Größe der Warteschlange und der Gesamtverarbeitungsgeschwindigkeit ändert sich der angezeigte Status möglicherweise erst, wenn die Seite mindestens einmal neu geladen wurde.

### Aussetzen oder Aufheben der Aussetzung von Prozessinstanzen {#suspend-or-unsuspend-process-instances}

Wenn Sie ein Problem beheben müssen oder wissen, dass eine Prozessinstanz aufgrund einer externen Bedingung in einem späteren Schritt auf ein Problem stoßen wird, können Sie die Prozessinstanz vorübergehend aussetzen.

Sie können Prozessinstanzen mit dem Status WIRD AUSGEFÜHRT aussetzen.

Nachdem Sie eine Prozessinstanz ausgesetzt haben, ändert sich ihr Status in AUSSETZEN, WIRD AUSGESETZT und der Prozess wird beim aktuellen Vorgang angehalten. Die Prozessinstanz bleibt in diesem Status, bis der Status in UNSUSPENDED geändert wird.

Nur Prozessinstanzen mit dem Status AUSGESETZT können in AUSGESETZT geändert werden.

Wenn Sie das Aussetzen einer Prozessinstanz aufheben, ändert sich ihr Status in WIRD AUSGEFÜHRT und der Vorgang wird dort fortgesetzt, wo er ausgesetzt wurde.

Wenn Sie eine Prozessinstanz aussetzen, die andere Prozesse (untergeordnete Prozesse) mithilfe ihres Aufrufvorgangs aufgerufen hat, werden die untergeordneten Prozesse ebenfalls ausgesetzt.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Arbeitsablauf für Formulare“. 
1. Wählen Sie auf der Seite &quot;Prozessinstanz&quot;den Prozess aus und klicken Sie auf Aussetzen oder Aussetzen aufheben .

### Prozessinstanzen beenden {#terminate-a-process-instances}

Wenn ein Vorgang einer Prozessinstanz angehalten wurde oder eine andere Fehlerbedingung aufgetreten ist oder Sie die Ausführung einer Prozessinstanz erzwingen müssen, können Sie die Prozessinstanz beenden.

Sie können Prozessinstanzen mit einem beliebigen Status beenden.

Wenn Sie eine Prozessinstanz beenden, ändert sich ihr Status in BEENDET, dann BEENDET und der Prozess wird beim aktuellen Vorgang beendet. Es werden keine weiteren Vorgänge ausgeführt und alle damit verbundenen Vorgänge und Aufgaben werden beendet.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Arbeitsablauf für Formulare“. 
1. Wählen Sie auf der Seite &quot;Prozessinstanz&quot;den Prozess aus und klicken Sie auf &quot;Beenden&quot;.

## Arbeiten mit Prozessinstanzdetails {#working-with-process-instance-details}

Auf der Seite &quot;Prozessinstanzdetail&quot;wird der Verlauf einer Prozessinstanz angezeigt.

Im Bereich &quot;Zusammenfassung&quot;werden grundlegende Informationen zur Prozessinstanz angezeigt.

Auf der Registerkarte Vorgänge wird jeder Vorgang für die Prozessinstanz in der Reihenfolge angezeigt, in der er von Anfang bis Ende abgeschlossen wurde und die folgenden Informationen enthält:

**Vorgangsnamen:** Der Name des Vorgangs, wie in Workbench definiert.

**Status:** Zeigt an, ob der Vorgang normal ausgeführt wird oder beendet wurde. (Siehe Informationen zum Status von Prozessinstanzen.)

**Zweigname:** Der Name des Zweigs, wie in Workbench definiert.

**Startdatum:** Datum und Uhrzeit des Starts des Vorgangs.

**Abschlussdatum:** Datum und Uhrzeit des Abschlusses des Vorgangs.

Ein Teilprozess ist eine Prozessinstanz, die von einem anderen Prozess gestartet und unabhängig von diesem anderen Prozess ausgeführt wird. Teilprozesse werden nur angezeigt, wenn sie im Rahmen des Prozesses in Workbench entworfen wurden. Auf der Registerkarte Teilprozesse wird jeder Teilprozess mit den folgenden Informationen angezeigt:

**Prozess-ID:** Diese positive Ganzzahl wird vom Formular-Workflow zugewiesen, wenn der Prozess instanziiert (d. h. von einem Benutzer oder einem automatisierten Schritt initiiert) wird. Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname - Version:** Der Prozessname, wie in Designer definiert.

**Status:** Zeigt an, ob die Prozessinstanz normal ausgeführt wird, den Status wechselt oder beendet wurde. (Siehe Informationen zum Status von Prozessinstanzen.)

**Erstellungsdatum:** Datum und Uhrzeit der Erstellung des Teilprozesses.

**Aktualisierungsdatum:** Datum und Uhrzeit, zu der der Status des Unterprozesses zuletzt geändert wurde.

Auf der Seite &quot;Prozessinstanzdetail&quot;können Sie die folgenden Aufgaben ausführen:

* Wählen Sie einen Vorgang aus, um Details dazu anzuzeigen. Wenn Sie einen Vorgang auswählen, wird die Seite &quot;Vorgangsdetails&quot;angezeigt.
* Wählen Sie einen Teilprozess aus, um Details dazu anzuzeigen. Wenn Sie einen Teilprozess auswählen, wird die Seite &quot;Prozessinstanzdetail&quot;angezeigt.
* Vorgänge oder Teilprozesse je nach Status beenden oder wiederholen.

### Über den Vorgangsstatus {#about-operation-statuses}

Ein Vorgang (ein Schritt in einem Prozess) kann die folgenden Status haben:

**ABGESCHLOSSEN:** Der Vorgang wurde abgeschlossen.

**WIRD AUSGEFÜHRT:** Der Vorgang wird normal ausgeführt. Möglicherweise empfängt er Benutzereingaben oder wartet auf Benutzerinteraktion oder ein automatischer Schritt kann aktiv sein.

**VERZÖGERT:** Während der Verarbeitung des Prozesses ist ein Problem aufgetreten. Auf der Seite „Angehaltene Vorgänge“ können Sie den Fehler oder die Ausnahme überprüfen.

**BEENDET:** Der Vorgang wurde von einem Administrator beendet.

### Vorgänge oder Teilprozesse beenden {#terminate-operations-or-subprocesses}

Wenn ein Vorgang oder Teilprozess angehalten wurde oder eine andere Fehlerbedingung aufgetreten ist oder Sie die Ausführung eines Vorgangs oder Teilprozesses erzwingen müssen, können Sie ihn beenden.

Sie können einen Vorgang beenden, der AUSGEFÜHRT wird.

Wenn Sie einen Vorgang beenden, ändert sich sein Status in BEENDET. Der Vorgang wird nicht abgeschlossen und die Ausführung der Prozessinstanz wird beendet.

Sie können einen Teilprozess mit einem beliebigen Status beenden.

Wenn Sie einen Teilprozess beenden, wechselt dessen Status zu BEENDEN, dann BEENDET, und die Prozessinstanz stoppt bei den aktuellen Vorgängen. Im Teilprozess werden keine weiteren Vorgänge ausgeführt, obwohl die übergeordnete Prozessinstanz weiter ausgeführt wird.

Sie können Prozesse mit Gateway-Elementen im Prozessdiagramm nicht beenden. Wenn Sie versuchen, diese Prozesstypen zu beenden, sind die Vorgänge innerhalb der Gateway-Elemente nicht betroffen. Um Vorgänge zu beenden, die sich in einem Gateway-Element befinden, müssen Sie die Vorgänge direkt beenden.

1. Klicken Sie auf der Seite &quot;Prozessinstanzdetails&quot;auf die Registerkarte Vorgänge oder die Registerkarte Teilprozesse .
1. Wählen Sie den Vorgang oder Teilprozess aus und klicken Sie auf Beenden.

### Vorgang wiederholen {#retry-an-operation}

Sie können den Vorgang mit dem Status &quot;STALLED&quot;wiederholen.

Wenn Sie einen Vorgang wiederholen, wird eine Anforderung zum Neustart des Vorgangs an den Forms-Workflow gesendet. Wenn die Anfrage erfolgreich war, wechselt der Status zu WIRD AUSGEFÜHRT. Wenn der Vorgang nicht neu gestartet werden kann, bleibt er ANGEHALTEN und Sie müssen ihn möglicherweise beenden.

1. Klicken Sie auf der Seite &quot;Details der Prozessinstanz&quot;auf die Registerkarte Vorgänge .
1. Wählen Sie den Vorgang aus und klicken Sie auf &quot;Wiederholen&quot;.

## Arbeiten mit Vorgängen {#working-with-operations}

Auf der Seite &quot;Vorgangsdetails&quot;wird eine Zusammenfassung eines Vorgangs in einem Prozess und der aktuellen Benutzerzuweisungen angezeigt.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Arbeitsablauf für Formulare“. 
1. Klicken Sie auf einen Prozessnamen, um seine Prozessinstanzen anzuzeigen. Klicken Sie auf eine Prozessinstanz, um die Seite &quot;Prozessinstanzdetails&quot;anzuzeigen, und wählen Sie dann einen Vorgang aus, um die Seite &quot;Vorgangsdetails&quot;anzuzeigen.

   Für jede Aufgabe werden in der Liste die folgenden Informationen angezeigt:

   **Prozessname - Version:** Der Name des Prozesses, wie in Workbench definiert.

   **Anwendung:** Die Anwendung, zu der der Prozess gehört, wie in Workbench definiert.

   **Status:** Aktiv bedeutet, dass es sich um den Prozess handelt, der für die Prozessversion aktiviert wurde. Inaktiv bedeutet, dass der Prozess eine alte Version ist, von der immer noch Prozessinstanzen vorhanden sind.

   **Ertsllungsdatum:** Datum und Uhrzeit der Bereitstellung des Prozesses.
