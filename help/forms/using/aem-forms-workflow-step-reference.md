---
title: Formularzentrierte Workflows in OSGi - Schritt-Referenz
seo-title: Formularzentrierte Workflows in OSGi - Schritt-Referenz
description: Der formularzentrierte Workflow in OSGi-Schritten ermöglicht das schnelle Erstellen adaptiver formularbasierter Workflows.
seo-description: Der formularzentrierte Workflow in OSGi-Schritten ermöglicht das schnelle Erstellen adaptiver formularbasierter Workflows.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: aheimoz
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
translation-type: tm+mt
source-git-commit: 36baba4ee20dd3d7d23bc50bfa91129588f55d32
workflow-type: tm+mt
source-wordcount: '4561'
ht-degree: 87%

---


# Formularzentrierte Workflows in OSGi - Schritt-Referenz {#forms-centric-workflow-on-osgi-step-reference}

## Schritte für den Forms-Workflow {#forms-workflow-steps}

Schritte für den Forms-Workflow führen AEM Forms-spezifische Vorgänge in einem AEM-Workflow durch. Diese Schritte ermöglichen das schnelle Erstellen adaptiver formularzentrierter Workflows auf OSGi. Diese Workflows können für die Entwicklung grundlegender Überprüfungs- oder Genehmigungs-Workflows, interner und „across-the-firewall“-Geschäftsprozesse verwendet werden. Sie können die Forms-Workflow-Schritte außerdem verwenden, um Document Services zu starten, Adobe Sign-Signatur-Workflow zu integrieren und andere AEM Forms-Vorgänge auszuführen. Sie benötigen das [AEM Forms Add-On](https://www.adobe.com/go/learn_aemforms_documentation_63), um diese Schritte in einem Workflow zu verwenden.

## Schritt „Aufgaben zuweisen“ {#assign-task-step}

Der Schritt „Aufgaben zuweisen“ erstellt eine Aufgabe und weist sie einem Benutzer oder einer Gruppe zu. Zusammen mit der Zuweisung der Aufgabe gibt die Komponente außerdem das adaptive Formular oder die nicht interaktive PDF-Datei für die Aufgabe an. Das adaptive Formular ist erforderlich, damit die Benutzer Eingaben vornehmen können, und die nicht interaktive PDF-Datei oder ein schreibgeschütztes adaptives Formular wird in Workflows verwendet, die nur zur Prüfung dienen.

Sie können mit dieser Komponente auch das Verhalten der Aufgabe steuern. Beispielsweise das Erstellen eines automatischen Datensatzdokuments, die Zuweisung der Aufgabe zu einem bestimmten Benutzer oder einer Gruppe, das Angeben des Pfads der gesendeten Daten, das Angeben des Pfads der Daten, die im Voraus ausgefüllt werden sollen und das Angeben der Standardaktionen. Schritt „Aufgaben zuweisen“ hat folgende Eigenschaften:

* **Titel:** Bezeichnung der Aufgabe. Der Titel wird in der AEM Inbox angezeigt.
* **Beschreibung:** Erläuterung der Vorgänge, die in der Aufgabe ausgeführt werden. Diese Informationen sind für andere Prozessentwickler nützlich, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

* **Miniaturbildpfad:** Pfad des Aufgabenminiaturbilds. Wenn kein Pfad angegeben ist, wird für ein adaptives Formular das Standardminiaturbild angezeigt und für das Datensatzdokument wird ein Standardsymbol angezeigt.
* **Workflow-Phase:** Ein Workflow kann mehrere Phasen enthalten. Diese Phasen werden in der AEM Inbox angezeigt. Sie können diese Phasen in den Eigenschaften des Modells definieren (Sidekick > Seite> Seiteneigenschaften > Phasen).
* **Priorität:** Die ausgewählte Priorität wird in der AEM Inbox angezeigt. Die verfügbaren Optionen sind „Hoch“, „Mittel“ und „Niedrig“. Der Standardwert ist „Mittel“.
* **Fälligkeitsdatum:** Geben Sie die Anzahl der Tage oder Stunden an, nach denen die Aufgabe als „überfällig“ markiert wird. Wenn Sie **Aus** wählen, dann wird die Aufgabe nie als „überfällig“ markiert. Sie können auch einen Zeitüberschreitungs-Handler angeben, um bestimmte Aufgaben auszuführen, nachdem die Aufgabe überfällig ist.

* **Tage:** Die Anzahl der Tage, nach denen die Aufgabe abgeschlossen werden soll. Die Anzahl der Tage wird gezählt, nachdem die Aufgabe einem Benutzer zugewiesen wurde. Wenn eine Aufgabe nicht abgeschlossen wurde und die Anzahl der Tage im Feld „Tage“ überschreitet, wird bei Auswahl dieser Option nach den fälligen Tagen ein Zeitüberschreitungshandler ausgelöst.
* **Stunden:** Die Anzahl der Tage, innerhalb derer die Aufgabe abgeschlossen werden soll. Die Anzahl der Stunden wird gezählt, nachdem die Aufgabe einem Benutzer zugewiesen wurde. Wenn eine Aufgabe nicht abgeschlossen wurde und die Anzahl der Stunden im Feld „Stunden“ überschreitet, wird bei Auswahl dieser Option nach den fälligen Stunden ein Zeitüberschreitungshandler ausgelöst.
* **Zeitüberschreitung nach Fälligkeitsdatum:** Wählen Sie diese Option, um das Auswahlfeld „Zeitüberschreitungshandler“ zu aktivieren.
* **Zeitüberschreitungshandler:** Wählen Sie das Skript aus, das ausgeführt werden soll, wenn der Schritt „Aufgabe zuweisen“ das Fälligkeitsdatum überschreitet. Scripts placed in the CRX-repository at [apps]/fd/dashboard/scripts/timeoutHandler are available for selection. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet.
* **Markieren Sie Aktion und Kommentar aus der letzten Aufgabe in „Aufgabendetails“:** Wählen Sie diese Option, um die letzte ausgeführte Aktion und den Kommentar, der im Abschnitt „Aufgabendetail“ einer Aufgabe erhalten wurde, anzuzeigen.
* **Typ:** Wählen Sie den Typ des Dokuments, das ausgefüllt werden soll, wenn der Workflow gestartet wird. Sie können ein adaptives Formular, ein schreibgeschütztes adaptives Formular oder ein nicht interaktives PDF-Dokument auswählen.
* **Adaptives Formular verwenden:** Geben Sie die Methode zum Suchen des adaptiven Eingabefelds an. Sie können das adaptive Formular verwenden, das unter einem absoluten Pfad verfügbar ist, als Nutzlast an den Workflow übermittelt wird oder in einem Pfad verfügbar ist, der mithilfe einer Variablen berechnet wurde. Sie können eine Variable des Typs String verwenden, um den Pfad anzugeben.
* **Adaptiver Formularpfad**: Geben Sie den Pfad des adaptiven Formulars an. Das Feld ist verfügbar, wenn Sie im Feld &quot;Typ&quot;ein adaptives Formular oder eine schreibgeschützte Option für ein adaptives Formular in Verbindung mit der Option &quot;Absoluter Pfad&quot;im Feld &quot;Adaptives Formular verwenden&quot;verwenden.
* **PDF-Pfad:** Geben Sie den Pfad eines nicht interaktiven PDF-Dokuments an. Das Feld ist verfügbar, wenn Sie im Feld „Typ“ ein nicht interaktives PDF-Dokument auswählen. Der Pfad ist immer relativ zur Payload. For example, [Payload_Directory]/Workflow/PDF/credit-card.pdf. Der Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare, um die PDF-Pfad-Komponente zu verwenden.
* **Für abgeschlossene Aufgaben rendern Sie das adaptive Formular wie folgt**: Wenn eine Aufgabe als abgeschlossen markiert ist, können Sie das adaptive Formular als schreibgeschütztes adaptives Formular oder PDF-Dokument ausgeben. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare zum Rendern des adaptiven Formulars als Datensatzdokument.
* **Vorab auszufüllende Angaben:** Die folgenden unten aufgeführten Felder dienen als Eingaben für die Aufgabe: 

   * **Datendateipfad :** Pfad der Eingabedatendatei (.json oder .xml). Der Pfad ist immer relativ zur Payload. Beispielsweise enthält die Datei die Daten, die für das Formular über eine AEM Inbox-Anwendung gesendet werden. An example path is [Payload_Directory]/workflow/data.
   * **Anlagenpfad:** Anlagen, die am Speicherort verfügbar sind, werden an das Formular angehängt, das mit der Aufgabe verknüpft ist. Der Pfad ist immer relativ zur Payload. An example path is [Payload_Directory]/attachments/

* **Gesendete Informationen:** Die folgenden Felder dienen als Ausgabespeicherorte für die Aufgabe:

   * **Datendateipfad:** Pfad der Datendatei (.json oder .xml). Die Datendatei enthält Informationen, die über das zugeordnete Formular übermittelt werden. Der Pfad ist immer relativ zur Payload. For example, [Payload_Directory]/Workflow/data, where data is a file.
   * **Anlagenpfad:** Pfad zum Speichern der Formularanlagen in einer Aufgabe.
   * **Datensatzdokumentpfad:** Pfad zum Speichern einer Datensatzdokumentdatei. For example, [Payload_Directory]/DocumentofRecord/credit-card.pdf. Das Datensatzdokument wird nicht generiert, wenn das Feld „Pfad“ leer ist. Der Pfad ist immer relativ zur Payload.

* **Optionen zuweisen:** Geben Sie die Methode an, mit der die Aufgabe einem Benutzer zugewiesen werden soll. Sie können die Aufgabe dynamisch einem Benutzer oder einer Gruppe zuweisen, indem Sie das Skript „Teilnehmerauswahl“ verwenden oder die Aufgabe einem bestimmten AEM-Benutzer oder einer bestimmten Gruppe zuweisen.
* **Teilnehmerauswahl:** Die Option ist verfügbar, wenn die Option **Dynamically to a user or group (Dynamisch zu einem Benutzer oder einer Gruppe)** im Feld „Optionen zuweisen“ ausgewählt ist. Sie können ein ECMAScript oder einen Dienst verwenden, um einen Benutzer oder eine Gruppe dynamisch auszuwählen. Weitere Informationen finden Sie im Abschnitt [Dynamisches Zuweisen eines Workflows zu Benutzern](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) und [Erstellen eines benutzerdefinierten Schritts „Dynamischer Teilnehmer in Adobe Experience Manager“.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Teilnehmer:** Das Feld ist verfügbar, wenn die Option **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** im Feld „Teilnehmerauswahl“ ausgewählt ist. In diesem Feld können Sie Benutzer oder Gruppen für die Option „RandomParticipantChooser“ auswählen.

* **Argumente:** Das Feld ist verfügbar, wenn ein anderes als das Skript „RandomParticipantChoose“ im Feld „Teilnehmerauswahl“ ausgewählt wurde. In diesem Feld können Sie eine Liste mit durch Kommas getrennten Argumenten für das im Feld „Teilnehmerauswahl“ ausgewählte Skript angeben.

* **Benutzer oder Gruppe:** Die Aufgabe wurde dem ausgewählten Benutzer oder der Gruppe zugewiesen. Die Option ist verfügbar, wenn die Option **To a specific user or group (Zu einer bestimmten Benutzer bzw. einer bestimmten Gruppe)** im Feld „Optionen zuweisen“ ausgewählt ist. Das Feld listet alle Benutzer und Gruppen der Workflow-Benutzergruppe auf.

* **Bevollmächtigten per E-Mail benachrichtigen:** Wählen Sie diese Option, um E-Mail-Benachrichtigungen an den Bevollmächtigten zu senden. Diese Benachrichtigungen werden gesendet, wenn eine Aufgabe einem Benutzer zugewiesen wird. Aktivieren Sie die Benachrichtigungen von AEM Web Console, bevor Sie die Option verwenden. Für schrittweise Anweisungen siehe [Konfigurieren von E-Mail-Benachrichtigungen für den Schritt „Aufgabe zuweisen“](/help/forms/using/aem-forms-workflow.md)

* **HTML-E-Mail-Vorlage**: Wählen Sie die E-Mail-Vorlage für die Benachrichtigungs-E-Mail. Um eine Vorlage zu bearbeiten, ändern Sie die Datei unter /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt im CRX-Repository.
* **Delegierung zulassen an:** AEM Inbox bietet dem angemeldeten Benutzer eine Option, den zugewiesenen Workflow an einen anderen Benutzer zu übertragen. Sie dürfen innerhalb derselben Gruppe oder an den Workflow-Benutzer einer anderen Gruppe delegieren. Wenn die Aufgabe einem einzelnen Benutzer zugewiesen ist und die Option **Delegierung an Mitglieder der Bevollmächtigten-Gruppe zulassen** aktiviert ist, kann die Aufgabe nicht an einen anderen Benutzer oder eine andere Gruppe übertragen werden.

* **Standardaktionen:** Standardmäßig sind die Aktionen „Senden“, „Speichern“ und „Zurücksetzen“ verfügbar. Alle Standardaktionen sind standardmäßig aktiviert.
* **Route-Variable:** Name der Route-Variablen. Die Route-Variable erfasst benutzerdefinierte Aktionen, die ein Benutzer in der AEM Inbox auswählt.
* **Routen:** Eine Aufgabe kann auf verschiedene Routen verzweigen. Bei Auswahl in AEM Inbox gibt die Route einen Wert zurück, und der Workflow verzweigt basierend auf der ausgewählten Route.
* **Titel**: Geben Sie den Titel für die Route an. Der Titel wird in der AEM Inbox angezeigt.
* **Korallen-Symbol:** Geben Sie das HTML-Attribut eines Korallensymbols an. Die Adobe CorelUI-Bibliothek bietet eine Vielzahl von Touch-First-Symbolen. Sie können ein Symbol für die Route auswählen und verwenden. Es wird zusammen mit dem Titel in AEM Inbox angezeigt.
* **Bevollmächtigtem erlauben, Kommentare einzufügen**: Wählen Sie diese Option, um Kommentare für die Aufgabe zu aktivieren. Ein Beauftragter kann die Kommentare innerhalb der AEM Inbox zum Zeitpunkt des Aufgabenversands hinzufügen.
* **Bevollmächtigtem erlauben, Anlage(n) der Aufgabe hinzuzufügen**: Wählen Sie diese Option, um Anlagen für die Aufgabe zu aktivieren. Ein Beauftragter kann die Anlagen in der AEM Inbox zum Zeitpunkt der Aufgabensendung hinzufügen.
* **Ausgabepfad von Aufgabenanlagen**: Geben Sie den Speicherort des Anlagenordners an. Der Speicherort ist relativ zur Payload.
* **Benutzerdefinierte Metadaten verwenden:** Wählen Sie diese Option, um das benutzerdefinierte Metadatenfeld zu aktivieren. Benutzerdefinierte Metadaten werden in E-Mail-Vorlagen verwendet.
* **Benutzerdefinierte Metadaten:** Wählen Sie benutzerdefinierte Metadaten für die E-Mail-Vorlagen. Die benutzerdefinierten Metadaten sind im CRX-Repository unter apps/fd/dashboard/scripts/metadataScripts verfügbar. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie können auch einen Dienst für die benutzerdefinierten Metadaten verwenden. You can also extend the `WorkitemUserMetadataService` interface to provide custom metadata.

* **Daten aus vorherigen Schritten anzeigen**: Wählen Sie - falls verfügbar - diese Option aus, um den Bevollmächtigten das Anzeigen früherer Bevollmächtigter, bereits vorgenommener Aktionen, Kommentare zu dieser Aufgabe und des Nachweisdokuments über abgeschlossene Aufgaben zu ermöglichen.
* **Daten aus allen nachfolgenden Schritten einblenden:** Wählen Sie diese Option, um dem aktuellen Bearbeiter zu ermöglichen, die durchgeführte Aktion und Kommentare, die von nachfolgenden Beauftragten zur Aufgabe hinzugefügt wurden, anzuzeigen. Außerdem kann sich der aktuelle Bevollmächtigte ein Dokument als Nachweis über die abgeschlossenen Aufgaben anzeigen lassen - sofern verfügbar.
* **Sichtbarkeit des Datentyps:** Standardmäßig kann ein Bevollmächtigter ein Datensatzdokument, Bevollmächtigte, durchgeführte Aktionen und Kommentare anzeigen, die frühere und nachfolgende Bevollmächtigte hinzugefügt haben. Verwenden Sie die Option „Sichtbarkeit von Datentyp“, um den Typ der für die Bevollmächtigten sichtbaren Daten zu begrenzen.

## Schritt „E-Mail senden“{#send-email-step}

Verwenden Sie den E-Mail-Schritt, um eine E-Mail zu senden, z. B. eine E-Mail mit einem Dokument, einen Link eines adaptiven Formulars, einen Link einer interaktiven Kommunikation oder ein angehängtes PDF-Dokument. Der Schritt „E-Mail senden“ unterstützt [HTML-E-Mails](https://en.wikipedia.org/wiki/HTML_email). HTML-E-Mails sind responsive und passen sich an den E-Mail-Client und die Bildschirmgröße des Empfängers an. Sie können eine HTML-E-Mail-Vorlage verwenden, um das Erscheinungsbild, das Farbschema und Verhalten der E-Mail zu definieren.

Der E-Mail-Schritt verwendet den Day CQ Mail-Dienst Bevor Sie den E-Mail-Schritt verwenden, stellen Sie sicher, dass der [E-Mail-Dienst](/help/forms/using/aem-forms-workflow.md) konfiguriert wurde. Der E-Mail-Schritt hat die folgenden Eigenschaften:

**Titel:** Der Titel des Schritts hilft beim Identifizieren des Schritts im Workflow-Editor.

**Beschreibung:** Erklärungen können für andere Entwickler nützlich sein, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

**E-Mail-Betreff:** Betreff kann aus Workflow-Metadaten abgerufen oder manuell angegeben werden. Wählen Sie die Option **Literal**, um einen Betreff manuell anzugeben, oder wählen Sie die Option **Aus Workflow-Metadaten abrufen**, um den Betreff aus einer Metadateneigenschaft abzurufen.

**HTML-E-Mail-Vorlage**: HTML-Vorlage für die E-Mail. Sie können diese Variablen in einer E-Mail-Vorlage verwenden. Der E-Mail-Schritt extrahiert und zeigt alle Variablen an, die in einer Vorlage für Eingaben enthalten sind. 

**E-Mail-Vorlagenmetadaten:** Der Wert der E-Mail-Vorlagenvariablen kann ein vom Benutzer angegebener Wert, der Pfad eines Assets auf dem Autor oder dem Veröffentlichungsserver, Bild oder eine Workflow-Metadateneigenschaft sein.

* **Literal:** Verwenden Sie die Option, wenn Sie den genauen, zu spezifizierenden Wert kennen. Beispiel: [example@example.com](mailto:example@example.com).

* **Workflow-Metadaten:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird. Nachdem Sie die Option ausgewählt haben, geben Sie den Namen der Metadateneigenschaft in das leere Textfeld unter der Option „Workflow-Metadaten“ ein. Zum Beispiel emailAddress.
* **Asset-URL:** Verwenden Sie die Option, um einen Weblink einer interaktiven Kommunikation mit der E-Mail einzubetten. Wählen Sie nach Auswahl der Option die einzubettende interaktive Kommunikation aus. Das Asset kann sich auf dem Autoren- oder dem Veröffentlichungsserver befinden.
* **Bild:** Verwenden Sie die Option, um ein Bild in die E-Mail einzubetten. Nachdem Sie die Option ausgewählt haben, suchen Sie nach dem entsprechenden Bild und wählen Sie es aus. Die Bildoption ist nur für die Bild-Tags (&lt;img src=&quot;&amp;ast;&quot;/>) verfügbar, die in der E-Mail-Vorlage verfügbar sind.

**E-Mail-Adresse des Absenders/Empfängers:** Wählen Sie die Option &quot; **Literal** &quot;, um manuell eine E-Mail-Adresse anzugeben, oder wählen Sie die Option &quot; **Abrufen von Workflow-Metadaten** &quot;, um die E-Mail-Adresse aus einer Metadateneigenschaft abzurufen. Sie können auch eine Liste von Metadaten-Eigenschaften-Arrays für die Option **Aus Workflow-Metadaten abrufen** angeben.

**Pfad für Dateianhang:** Das am angegebenen Speicherort verfügbare Asset wird an die E-Mail angehängt. Der Pfad des Assets kann relativ zur Payload oder zum absoluten Pfad sein. An example path is [Payload_Directory]/attachments/

**Dateiname:** Name der E-Mail-Anhangsdatei. Der E-Mail-Schritt ändert den ursprünglichen Dateinamen der Anlage in den angegebenen Dateinamen. Der Name kann manuell angegeben oder aus einer Workflow-Metadateneigenschaft abgerufen werden. Verwenden Sie die Option **Literal**, wenn Sie den genauen zu spezifizierenden Wert kennen. Verwenden Sie die Option **Von Workflow-Metadaten abrufen**, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird.

## Schritt „Generieren von Datensatzdokument“{#generate-document-of-record-step}

Wenn ein Formular ausgefüllt oder eingereicht wird, können Sie das Formular in gedruckter Form oder als Dokument speichern. Dies wird als Datensatzdokument (DOR) bezeichnet. Sie können den Schritt „Generieren von Datensatzdokument“ verwenden, um eine schreibgeschützte oder interaktive PDF-Version eines adaptiven Formulars zu erstellen. Die PDF-Version enthält Informationen, die zusammen mit dem Layout des adaptiven Formulars in das Formular eingegeben werden.

Der Schritt „Nachweisdokument“ hat die folgenden Eigenschaften:

**Adaptives Formular** verwenden: Geben Sie die Methode zum Suchen des adaptiven Eingabefelds an. Sie können das adaptive Formular verwenden, das unter einem absoluten Pfad verfügbar ist, als Nutzlast an den Workflow übermittelt wird oder in einem Pfad verfügbar ist, der mithilfe einer Variablen berechnet wurde. Sie können eine Variable des Typs String verwenden, um den Pfad anzugeben.

**Adaptiver Formularpfad**: Geben Sie den Pfad des adaptiven Formulars an. Das Feld ist verfügbar, wenn Sie im Feld &quot;Typ&quot;ein adaptives Formular oder eine schreibgeschützte Option für ein adaptives Formular in Verbindung mit der Option &quot;Absoluter Pfad&quot;im Feld &quot;Adaptives Formular verwenden&quot;verwenden.

**Pfad für Eingabedaten:** Pfad der Eingabedaten für das adaptive Formular. Sie können die Daten relativ zur Payload an einem Speicherort belassen oder einen absoluten Pfad für die Daten angeben. Die Eingabedaten werden mit dem adaptiven Formular zusammengeführt, um ein Datensatzdokument zu erstellen.

**Pfad Eingabeanlage:** Pfad Eingabeanlage: Pfad der Anlagen. Diese Anhänge sind im Datensatzdokument enthalten. Sie können die Anlagen relativ zur Payload an einem Speicherort belassen oder einen absoluten Pfad für die Anlagen angeben.

Wenn Sie den Pfad eines Ordners angeben, z. B. Anlagen, werden alle Dateien, die direkt im Ordner verfügbar sind, an das Datensatzdokument angehängt. Wenn Dateien in den Ordnern verfügbar sind, die im angegebenen Pfad für den Anhang direkt verfügbar sind, werden die Dateien im Datensatzdokument als Anlagen aufgenommen. Wenn sich Ordner in direkt verfügbaren Ordnern befinden, werden diese übersprungen.

**Generierter Pfad von Datensatzdokument** Geben Sie den Speicherort für ein Datensatzdokument an. Sie können den Nutzdatenordner überschreiben oder das Datensatzdokument an einem Speicherort innerhalb des Nutzdatenordners platzieren.

**Gebietsschema**: Geben Sie die Sprache des Datensatzdokuments an.

## Schritt „Formulardatenmodelldienst aufrufen“ {#invoke-form-data-model-service-step}

Sie können [AEM Forms-Datenintegration](/help/forms/using/data-integration.md) verwenden, um unterschiedliche Datenquellen zu konfigurieren und Verbindungen zu ihnen herzustellen. Diese Datenquellen können eine Datenbank, ein Webdienst, ein REST-Dienst, ein OData-Dienst und eine CRM-Lösung sein. Mit AEM Forms-Datenintegration können Sie ein Formulardatenmodell erstellen, das verschiedene Dienste umfasst, um Vorgänge zum Datenabruf, Hinzufügen und Aktualisieren in der konfigurierten Datenbank durchzuführen. Sie können den **Schritt „Formulardatenmodelldienst aufrufen“** verwenden, um ein Formulardatenmodell (FDM) zu wählen und die Dienste des FDM abzurufen, zu aktualisieren oder Daten unterschiedlichen Datenquellen hinzuzufügen.

Um die Eingaben für Felder des Schritts zu erläutern, werden die folgende Datenbanktabelle und JSON-Datei als Beispiel verwendet:

**Beispiel: Tabelle „Kundendetails“**

<table> 
 <tbody> 
  <tr> 
   <td>Property</td> 
   <td>Wert<br /> </td> 
  </tr> 
  <tr> 
   <td>Vorname<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>Nachname</td> 
   <td>Rose</td> 
  </tr> 
  <tr> 
   <td>Kunden-ID</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>E-Mail-Adresse<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**JSON-Beispieldatei**

```
{ 
  customer: { 
   firstName: "Sarah", 
   lastName:"Rose", 
   customerId: "1", 
   emailAddress:"srose@we.info" 
 }, 
  insurance: {
   customerId: "1", 
  policyType: "Premium,
  policyNumber: "Premium-521499",
  customerDetails: { 
   firstName: "Sarah",
   lastName: "Rose",
   customerId: "1",
   emailAddress: "srose@we.info" 
  }
 }
}
```

Der Schritt „Formulardatenmodelldienst aufrufen“ enthält die folgenden Felder, um Formulardatenmodellvorgänge zu vereinfachen:

* **Titel:** Bezeichnung des Schrittes. Dies erleichtert die Identifizierung dieses Schritts im Workflow-Editor.
* **Beschreibung:** Erklärungen können für andere Entwickler nützlich sein, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

* **Pfad für Formulardatenmodell**: Wählen Sie ein Formulardatenmodell auf dem Server aus.

* **Dienst**: Liste der Dienste, die das ausgewählte Formulardatenmodell bereitstellt.
* **Eingabe für Dienste > Bereitstellung von Eingabedaten mit Literal, Workflow-Metadaten und einer JSON-Datei** : Ein Dienst kann mehrere Argumente haben. Wählen Sie die Option zum Abrufen des Werts der Service-Parameter aus einer Workflow-Metadateneigenschaft, einem JSON-Objekt, oder geben Sie den Wert direkt in das bereitgestellte Textfeld ein:

   * **Literal:** Verwenden Sie die Option, wenn Sie den genauen zu spezifizierenden Wert kennen. Beispiel: srose@we.info.
   * **Aus Workflow-Metadaten abrufen:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird. Zum Beispiel emailAddress.
   * **JSON Dot Notation:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer JSON-Datei enthalten ist. Z. B. ist die Option „insurance.customerDetails.emailAddress.The JSON Dot Notation“ nur verfügbar, wenn Eingabefelder zur Eingabe von JSON-Eingabeoptionen ausgewählt sind.
   * **Zuordnen von Eingabefelder aus der Eingabe JSON:** Geben Sie den Pfad einer JSON-Datei an, um den Eingabewert einiger Service-Parameter aus der JSON-Datei abzurufen. Der Pfad der JSON-Datei kann relativ zur Payload oder einem absoluten Pfad sein.

* **Eingabe für Dienste > Angeben von Eingabedaten mit einer JSON-Datei:** Wählen Sie die Option, um Werte für alle Argumente aus einer JSON-Datei abzurufen.
* **Ausgabe JSON-Dateipfad**: Pfad der JSON-Datei, die Werte für alle Service-Parameter enthält. Der Pfad der JSON-Datei kann **relativ zur Payload** oder einem **absoluten Pfad** sein.

* **JSON Dot Notation:** Lassen Sie das Feld leer, um alle Objekte der angegebenen JSON-Datei als Eingabe für Service-Parameter zu verwenden. Um ein bestimmtes JSON-Objekt aus der angegebenen JSON-Datei als Eingabe für Service-Parameter zu lesen, geben Sie die Dot Notation für das JSON-Objekt an, z. B. wenn Sie ein JSON ähnlich wie am Anfang des Abschnitts aufgeführt haben, geben Sie insurance.customerDetails an, um alle Details eines Kunden als Eingabe für den Dienst anzugeben.
* **Ausgabe des Dienstes > Zuordnen von Ausgabewerten zu den Metadaten:** Wählen Sie die Option zum Speichern der Ausgabewerte als Eigenschaften des Metadatenknotens der Workflow-Instanz im CRX-Repository. Geben Sie den Namen der Metadateneigenschaft an und wählen Sie das entsprechende Dienstausgabeattribut, das der Metadateneigenschaft zugeordnet werden soll, ordnen Sie z. B. die vom Output-Dienst zurückgegebene Telefonnummer mit der Eigenschaft phone_number den Workflow-Metadaten zu.
* **Output of service > Save output as JSON:** Wählen Sie die Option zum Speichern der Ausgabewerte in einer JSON-Datei aus.
* **Ausgabe JSON-Dateipfad** Pfad zum Speichern der JSON-Ausgabedatei. Der Pfad der JSON-Ausgabedatei kann relativ zur Payload oder einem absoluten Pfad sein.

## Schritt „Dokument signieren“ {#sign-document-step}

Mit dem Schritt „Dokument signieren“ können Sie Adobe Sign zum Signieren von Dokumenten verwenden. Der Schritt „Dokument signieren“ hat folgende Eigenschaften:

* **Name der Vereinbarung:** Geben Sie den Titel der Vereinbarung an. Der Name der Vereinbarung wird Teil des Betreffs und des Nachrichtentextes der E-Mail, die an die Unterzeichner gesendet wird.
* **Gebietsschema:** Geben Sie die Sprache für die E-Mail- und Bestätigungsoptionen an.
* **Cloud-Konfiguration für Adobe Sign**: Wählen Sie eine Adobe Sign Cloud-Konfiguration. Wenn Sie Adobe Sign für AEM Forms nicht konfiguriert haben, lesen Sie den Abschnitt [Adobe Sign in AEM Forms integrieren](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Zu signierendes Dokument:** Sie können ein Dokument an einem Speicherort relativ zur Payload auswählen, Nutzdaten als Dokument verwenden oder einen absoluten Pfad für das Dokument angeben.
* **Tage bis Abgabetermin:** Ein Dokument wird als „fällig“ (Abgabetermin überschritten) gekennzeichnet, nachdem für die im Feld **Tage bis Abgabetermin** angegebene Anzahl von Tagen keine Aktivität für die Aufgabe ermittelt wurde. Die Anzahl der Tage wird gezählt, nachdem das Dokument einem Benutzer zur Unterzeichnung zugewiesen wurde.

* **Häufigkeit der E-Mail-Erinnerung:** Sie können eine Erinnerungs-E-Mail im täglichen oder wöchentlichen Intervall senden. Die Woche wird ab dem Tag gezählt, an dem das Dokument einem Benutzer zum Signieren zugewiesen wurde.
* **Signaturvorgang:** Sie können ein Dokument in einer sequenziellen oder parallelen Reihenfolge signieren. Bei sequenzieller Anordnung erhält jeder Unterzeichner das Formular in Folge. Nachdem der erste Unterzeichner das Dokument signiert hat, wird das Formular an den nächsten Unterzeichner gesendet und so weiter. Bei paralleler Anordnung können mehrere Unterzeichner ein Formular gleichzeitig signieren.

* **Umleitungs-URL:** Geben Sie eine Umleitungs-URL an. Nachdem das Dokument signiert wurde, können Sie den Empfänger an eine URL umleiten. Normalerweise enthält diese URL eine Dankesnachricht oder weitere Anweisungen.
* **Workflow-Phase:** Ein Workflow kann mehrere Phasen enthalten. Diese Phasen werden in der AEM Inbox angezeigt. Sie können diese Phasen in den Eigenschaften des Modells definieren (Sidekick > Seite> Seiteneigenschaften > Phasen).
* **Unterzeichner wählen:** Geben Sie die Methode zum Auswählen von Unterzeichnern für das Dokument an. Sie können den Workflow einem Benutzer oder einer Gruppe dynamisch zuweisen oder manuell Details einem Unterzeichner hinzufügen.
* **Skript oder Dienst zur Auswahl von Unterzeichnern:** Die Option ist nur verfügbar, wenn die Option „Dynamisch“ im Feld „Unterzeichner auswählen“ ausgewählt ist. Sie können ein ECMAScript oder einen Dienst angeben, um Unterzeichner und Überprüfungsoptionen für ein Dokument auszuwählen.

* **Unterzeichnerdetails:** Die Option ist nur verfügbar, wenn die Option „Manuell“ im Feld „Unterzeichner auswählen“ ausgewählt ist. Geben Sie die E-Mail-Adresse an und wählen Sie einen optionalen Bestätigungsmechanismus. Bevor Sie einen Zwei-Schritt-Bestätigungsmechanismus auswählen, vergewissern Sie sich, dass die entsprechende Verifizierungsoption für das konfigurierte Adobe Sign-Konto aktiviert ist.
* **Statusvariable:** Ein Adobe Sign-aktiviertes Dokument speichert den Signaturstatus des Dokuments in einer Variablen. Geben Sie den Namen der Statusvariable (adobeSignStatus) an. Eine Statusvariable einer Instanz ist in CRXDE unter /etc/workflow/instances/&lt;server>/&lt;date-time>/&lt;instance of workflow model>/workItems/&lt;node>/metaData enthält den Status einer Variablen verfügbar.
* **Pfad für signiertes Dokument:** Geben Sie den Speicherort für die unterzeichneten Dokumente an. Sie können die Nutzdatendatei (Payload file) überschreiben oder das signierte Dokument an einem Speicherort innerhalb des Nutzdatenordners platzieren.

## Schritt „Document Services“{#document-services-steps}

Bei AEM Document Services handelt es sich um einen Satz an OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten. AEM Forms stellt für jeden Dokumentendienst einen separaten AEM-Workflow-Schritt bereit:

### Schritt „Dokumentzeitstempel einfügen“{#apply-document-time-stamp-step}

Fügen Sie einen Zeitstempel in das Dokument ein. Sie geben Dokumentdetails wie den Pfad des Eingabedokuments, den Namen des Eingabedokuments und den Speicherort für die exportierten Daten an. Sie können die vorhandene Payload-Datei überschreiben oder einen anderen Dateinamen wählen, um Daten in einer anderen Datei im Nutzdatenordner zu speichern.

### Schritt „In Bild umwandeln“ {#convert-to-image-step}

Konvertiert ein PDF-Dokument in eine Bilddatei. Unterstützte Bildformate sind JPEG, JPEG2000, PNG und TIFF. Die folgenden Informationen gelten für Konvertierungen in TIFF-Bilder:

* Eine mehrseitige TIFF-Datei wird generiert.
* Einige Anmerkungen sind nicht in TIFF-Bildern enthalten. Anmerkungen, die Acrobat zur Erstellung ihrer Darstellung benötigen, sind nicht enthalten.

### Schritt „Nach PDF/A konvertieren“ {#convert-to-pdf-a-step}

Konvertiert ein PDF-Dokument mit den verfügbaren Optionen in das PDF/A-Format. Die PDF/A-Version des Portable Document Format (PDF) ist auf die Archivierung und Langzeitarchivierung von Dokumenten spezialisiert. 

### Schritt „Konvertieren nach PS“{#convert-to-ps-step}

Konvertieren von PDF-Dokumenten in PostScript – Beim Konvertieren in PostScript können Sie für den Konvertierungsvorgang das Quelldokument und die PostScript-Ebene (2 oder 3) angeben. Das PDF-Dokument, das in eine PostScript-Datei konvertiert wird, muss nicht interaktiv sein.

### Schritt „PDF vom angegebenen Typ erstellen“ {#create-pdf-from-specified-type-step}

Generiert ein PDF-Dokument aus einer Eingabedatei. Das Eingabe-Dokument kann relativ zur Nutzlast sein, einen absoluten Pfad haben oder selbst Nutzlast sein.

### Schritt „PDF aus URL/HTML/ZIP erstellen“{#create-pdf-from-url-html-zip-step}

Erstellt ein PDF-Dokument anhand der bereitgestellten URL-, HTML- und ZIP-Datei.

### Schritt „Daten exportieren“ {#export-data-step}

Exportiert Daten aus einem PDF-Formular oder aus einer XDP-Datei Sie müssen den Dateipfad des Eingabedokuments und das Exportdatenformat eingeben. Die Optionen für das Exportdatenformat sind Auto, XDP und XmlData.

### Schritt „PDF in den angegebenen Format exportieren“ {#export-pdf-to-specified-type-step}

Konvertiert ein PDF-Dokument in ein ausgewähltes Format.

### Schritt „Nicht interaktive PDF-Dateien generieren“ {#generate-non-interactive-pdf-step}

Generieren Sie eine nicht interaktive PDF-Datei. Es bietet verschiedene Anpassungsoptionen.

### Schritt „Daten importieren“{#import-data-step}

Führt Formulardaten in einem PDF-Formular zusammen. Sie können Formulardaten in ein PDF-Formular importieren.

### Schritt „DDX aufrufen“ {#invoke-ddx-step}

Führt die DDX-Datei in der angegebenen Zuordnung von Eingabedokumenten aus und gibt die veränderten PDF-Dokumente zurück.

### Schritt „PDF optimieren“ {#optimize-pdf-step}

Optimiert PDF-Dateien durch Reduzierung ihrer Größe. Das Ergebnis dieser Konvertierung sind PDF-Dateien, die kleiner als ihre Originalversionen sein können. Bei diesem Vorgang werden außerdem PDF-Dokumente in die in den Optimierungsparametern angegebene PDF-Version konvertiert.

Die Optimierungseinstellungen geben an, wie Dateien optimiert werden. Hier sind Beispieleinstellungen:

* Zielgruppe PDF-Version
* Objekte wie JavaScript-Aktionen und eingebettete Seitenminiaturen verwerfen
* Verwerfen von Benutzerdaten wie Kommentaren und Dateianlagen
* Ungültige oder nicht verwendete Einstellungen verwerfen
* Komprimieren unkomprimierter Daten oder Verwenden effizienterer Komprimierungsalgorithmen
* Entfernen von eingebetteten Schriftarten
* Festlegen von Transparenzwerten

### Schritt „PDF-Formular ausgeben“ {#render-pdf-form-step}

Rendert ein Formular, das in Form Designer (XDP) erstellt wurde, in ein PDF-Formular.

### Schritt „Dokument absichern“ {#secure-document-step}

Verschlüsseln, signieren und zertifizieren Sie ein Dokument. AEM Forms unterstützt sowohl die kennwortbasierte als auch die zertifikatsbasierte Verschlüsselung. Sie können auch zwischen verschiedenen Algorithmen zum Signieren von Dokumenten wählen. Zum Beispiel SHA-256 und SH-512. Sie können den Workflow-Schritt zum Reader Extending von PDF-Dokumenten verwenden. Der Workflow-Schritt bietet Optionen zum Aktivieren von Barcode-Dekodierung, digitalen Signaturen, Importieren und Exportieren von PDF-Daten und anderen Optionen.

### Schritt „An Drucker senden“{#send-to-printer-step}

Senden Sie ein Dokument direkt an einen Drucker. Der Dienst unterstützt die folgenden Druckerzugriffsmechanismen:

* **Drucker mit direktem Zugriff**: Ein Drucker, der auf demselben Computer installiert ist, wird als Drucker mit direktem Zugriff und der Computer als Druckerhost bezeichnet. Dieser Druckertyp kann ein lokaler Drucker sein, der direkt an den Computer angeschlossen ist.
* **Drucker mit indirektem Zugriff**: Der Drucker, der auf einem Druckserver installiert ist, steht für den Zugriff von anderen Computern zur Verfügung. Es stehen Technologien wie das Common UNIX® Printing System (CUPS) und das LDP-Protokoll (Line Printer Daemon) zur Verfügung, um eine Verbindung zu einem Netzwerkdrucker herzustellen. Um auf einen Drucker mit indirektem Zugriff zuzugreifen, geben Sie die IP- oder Hostnamen des Druckservers an. Bei Verwendung dieses Mechanismus können Sie ein Dokument an einen LPD-URI senden, wenn im Netzwerk ein LP-Daemon ausgeführt wird. Mit dem Mechanismus können Sie das Dokument zu jedem Drucker weiterleiten, der mit dem Netzwerk verbunden ist, in dem ein LP-Daemon ausgeführt wird.

