---
title: Formularzentrierte Workflows in OSGi – Schritt-Referenz
seo-title: Forms-centric workflow on OSGi - Step Reference
description: Forms-zentrierte Workflows auf OSGi-Schritte ermöglichen Ihnen das schnelle Erstellen adaptiver formularbasierter Workflows.
seo-description: Forms-centric workflow on OSGi steps allow you rapidly build adaptive forms based workflows.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: AEM Docs
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
exl-id: f8e25989-6ed3-4b35-95e5-fbfd7c51d622
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4673'
ht-degree: 47%

---

# Formularzentrierte Workflows in OSGi - Schritt-Referenz {#forms-centric-workflow-on-osgi-step-reference}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Schritte für den Forms-Workflow {#forms-workflow-steps}

Forms-Workflow-Schritte führen AEM Forms-spezifische Vorgänge in einem AEM Workflow aus. Diese Schritte ermöglichen Ihnen das schnelle Erstellen eines Forms-zentrierten Workflows für adaptive Formulare auf OSGi. Diese Workflows können zur Entwicklung grundlegender Prüfungs- und Genehmigungs-Workflows, interner und übergreifender Geschäftsprozesse verwendet werden. Sie können auch Forms Workflow-Schritte verwenden, um Document Services zu starten, in den Acrobat Sign-Signatur-Workflow zu integrieren und andere AEM Forms-Vorgänge auszuführen. Sie benötigen [AEM Forms-Add-on](https://www.adobe.com/go/learn_aemforms_documentation_63_de) , um diese Schritte in einem Workflow zu verwenden.

## Schritt „Aufgabe zuweisen“ {#assign-task-step}

Der Schritt &quot;Aufgabe zuweisen&quot;erstellt eine Aufgabe und weist sie einem Benutzer oder einer Gruppe zu. Neben der Zuweisung der Aufgabe gibt die Komponente auch das adaptive Formular oder nicht interaktive PDF für die Aufgabe an. Das adaptive Formular ist erforderlich, um Benutzereingaben zu akzeptieren, und nicht interaktive PDF oder ein schreibgeschütztes adaptives Formular wird für schreibgeschützte Workflows verwendet.

Sie können mit dieser Komponente auch das Verhalten der Aufgabe steuern. Erstellen Sie beispielsweise ein automatisches Datensatzdokument, weisen Sie die Aufgabe einem bestimmten Benutzer oder einer bestimmten Gruppe zu, geben Sie den Pfad der gesendeten Daten an, geben Sie den Pfad der Daten an, die vorausgefüllt werden sollen, und legen Sie Standardaktionen fest. Der Schritt „Aufgabe zuweisen“ hat folgende Eigenschaften:

* **Titel:** Titel der Aufgabe. Der Titel wird im AEM-Posteingang angezeigt.
* **Beschreibung:** Erläuterung der in der Aufgabe ausgeführten Vorgänge. Diese Informationen sind für andere Prozessentwickler nützlich, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

* **Pfad für Miniaturansichten:** Pfad der Aufgabenminiatur. Wenn kein Pfad angegeben ist, wird für ein adaptives Formular eine Standardminiatur angezeigt und für das Datensatzdokument ein Standardsymbol.
* **Workflow-Phase:** Ein Workflow kann mehrere Phasen enthalten. Diese werden im AEM-Posteingang angezeigt. Sie können diese Schritte in den Eigenschaften des Modells definieren (Sidekick > Seite > Seiteneigenschaften > Schritte).
* **Priorität:** Die ausgewählte Priorität wird in der AEM Inbox angezeigt. Die verfügbaren Optionen sind &quot;Hoch&quot;, &quot;Mittel&quot;und &quot;Niedrig&quot;. Der Standardwert ist &quot;Mittel&quot;.
* **Fälligkeitsdatum:** Geben Sie die Anzahl der Tage oder Stunden an, nach denen die Aufgabe als überfällig markiert wird. Wenn Sie **Aus**, wird die Aufgabe nie als überfällig markiert. Sie können auch einen Zeitüberschreitungshandler festlegen, um bestimmte Aufgaben auszuführen, nachdem die Aufgabe überfällig ist.

* **Tage:** Die Anzahl der Tage, nach denen die Aufgabe abgeschlossen werden soll. Die Anzahl der Tage wird gezählt, nachdem die Aufgabe einem Benutzer zugewiesen wurde. Wenn eine Aufgabe nicht abgeschlossen ist und die im Feld Tage angegebene Anzahl von Tagen überschreitet, wird bei Auswahl dieser Option nach dem Fälligkeitsdatum ein Timeout-Handler ausgelöst.
* **Stunden:** Die Anzahl der Stunden, in denen die Aufgabe abgeschlossen werden soll. Die Anzahl der Stunden wird gezählt, nachdem die Aufgabe einem Benutzer zugewiesen wurde. Wenn eine Aufgabe nicht abgeschlossen und die Anzahl der Stunden im Feld „Stunden“ überschritten wurde, wird bei Auswahl dieser Option nach der entsprechenden Stundenanzahl ein Zeitüberschreitungshandler ausgelöst.
* **Zeitüberschreitung nach Fälligkeitsdatum:** Wählen Sie diese Option, um das Auswahlfeld „Zeitüberschreitungshandler“ zu aktivieren.
* **Zeitüberschreitungshandler:** Wählen Sie das Skript aus, das ausgeführt werden soll, wenn der Schritt „Aufgabe zuweisen“ das Fälligkeitsdatum überschreitet. Skripte, die im CRX-Repository unter [apps]/fd/dashboard/scripts/timeoutHandler abgelegt werden, stehen zur Auswahl. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet.
* **Markieren Sie Aktion und Kommentar aus der letzten Aufgabe in „Aufgabendetails“:** Wählen Sie diese Option, um die letzte ausgeführte Aktion und den Kommentar, der im Abschnitt „Aufgabendetail“ einer Aufgabe erhalten wurde, anzuzeigen.
* **Typ:** Wählen Sie den Typ des Dokuments, das ausgefüllt werden soll, wenn der Workflow gestartet wird. Sie können ein adaptives Formular, ein schreibgeschütztes adaptives Formular oder ein nicht interaktives PDF-Dokument auswählen.
* **Adaptives Formular verwenden**: Geben Sie die Methode zum Suchen des adaptiven Eingabeformulars an. Sie können das adaptive Formular verwenden, das in einem absoluten Pfad verfügbar ist, als Nutzlast an den Workflow übermittelt wird oder in einem Pfad verfügbar ist, der mithilfe einer Variablen berechnet wurde. Sie können eine Variable des Typs „Zeichenfolge“ verwenden, um den Pfad anzugeben.
* **Adaptiver Formularpfad**: Geben Sie den Pfad des adaptiven Formulars an. Das Feld ist verfügbar, wenn Sie im Feld Typ ein adaptives Formular oder eine schreibgeschützte Option für ein adaptives Formular verwenden und im Feld Adaptives Formular verwenden die Option absoluter Pfad verwenden.
* **PDF Path:** Geben Sie den Pfad eines nicht interaktiven PDF-Dokuments an. Das Feld ist verfügbar, wenn Sie im Feld „Typ“ ein nicht interaktives PDF-Dokument auswählen. Der Pfad ist immer relativ zur Payload. Beispiel: [Payload_Directory]/Workflow/PDF/credit-card.pdf. Der Pfad ist im CRX-Repository nicht vorhanden. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie benötigen eine Option &quot;Datensatzdokument&quot;aktiviert oder auf Formularvorlagen basierende adaptive Formulare, um die Option PDF-Pfad verwenden zu können.
* **Geben Sie für abgeschlossene Aufgaben das adaptive Formular als**: Wenn eine Aufgabe als abgeschlossen markiert ist, können Sie das adaptive Formular als schreibgeschütztes adaptives Formular oder als PDF-Dokument wiedergeben. Sie benötigen eine Option &quot;Datensatzdokument&quot;aktiviert oder auf Formularvorlagen basierende adaptive Formulare, um das adaptive Formular als Datensatzdokument wiederzugeben.
* **Vorausgefüllte Informationen:** Die folgenden Felder dienen als Eingaben für die Aufgabe:

   * **Datendateipfad:** Pfad der Eingabedatendatei (.json oder .xml). Der Pfad ist immer relativ zur Payload. Beispielsweise enthält die Datei die Daten, die über eine AEM-Posteingangsanwendung für das Formular übermittelt werden. Ein Beispielpfad ist [Payload_Directory]/workflow/data.
   * **Anlagenpfad:** Die am Speicherort verfügbaren Anlagen werden an das Formular angehängt, das mit der Aufgabe verknüpft ist. Der Pfad ist immer relativ zur Payload. Ein Beispielpfad ist [Payload_Directory]/attachments/

* **Gesendete Informationen:** Die folgenden Felder dienen als Ausgabespeicherorte für die Aufgabe:

   * **Datendateipfad:** Pfad der Datendatei (.json oder .xml). Die Datendatei enthält Informationen, die über das zugeordnete Formular übermittelt werden. Der Pfad ist immer relativ zur Payload. Zum Beispiel [Payload_Directory]/Workflow/data, wobei „data“ für eine Datei steht.
   * **Anlagenpfad:** Pfad zum Speichern der in einer Aufgabe bereitgestellten Formularanhänge.
   * **Pfad des Datensatzdokuments:** Pfad zum Speichern einer Datensatzdokumentdatei. Beispielsweise [Payload_Directory]/DocumentofRecord/credit-card.pdf. Das Datensatzdokument wird nicht generiert, wenn das Pfadfeld leer gelassen wird. Der Pfad ist immer relativ zur Payload.

* **Optionen zuweisen:** Geben Sie die Methode an, um die Aufgabe einem Benutzer zuzuweisen. Sie können die Aufgabe dynamisch einem Benutzer oder einer Gruppe zuweisen, indem Sie das Skript „Teilnehmerauswahl“ verwenden oder die Aufgabe einem bestimmten AEM-Benutzer oder einer bestimmten Gruppe zuweisen.
* **Teilnehmerauswahl:** Die Option ist verfügbar, wenn die **Dynamisch für einen Benutzer oder eine Gruppe** im Feld Optionen zuweisen ausgewählt ist. Sie können ein ECMAScript oder einen Service verwenden, um einen Benutzer oder eine Gruppe dynamisch auszuwählen. Weitere Informationen finden Sie unter [Dynamische Zuweisung eines Workflows an Benutzer](https://helpx.adobe.com/de/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) und [Erstellen eines benutzerdefinierten Adobe Experience Manager Dynamic Participant-Schritts.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de&amp;CID=RedirectAEMCommunityKautuk)

* **Teilnehmer:** Das Feld ist verfügbar, wenn die Option **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** im Feld Teilnehmerauswahl ausgewählt ist. In diesem Feld können Sie Benutzer oder Gruppen für die Option „RandomParticipantChooser“ auswählen.

* **Argumente:** Das Feld ist verfügbar, wenn ein anderes als das Skript „RandomParticipantChoose“ im Feld „Teilnehmerauswahl“ ausgewählt wurde. In diesem Feld können Sie eine Liste mit durch Kommas getrennten Argumenten für das im Feld „Teilnehmerauswahl“ ausgewählte Skript angeben.

* **Benutzer oder Gruppe:** Die Aufgabe wurde dem ausgewählten Benutzer oder der Gruppe zugewiesen. Die Option ist verfügbar, wenn die Option **Zu einem bestimmten Benutzer bzw. einer bestimmten Gruppe** im Feld Optionen zuweisen ausgewählt ist. Das Feld listet alle Benutzer und Gruppen der Workflow-Benutzergruppe auf.

* **Bevollmächtigten per E-Mail benachrichtigen:** Wählen Sie diese Option, um E-Mail-Benachrichtigungen an den Bevollmächtigten zu senden. Diese Benachrichtigungen werden gesendet, wenn einem Benutzer eine Aufgabe zugewiesen wird. Bevor Sie die Option verwenden, aktivieren Sie die Benachrichtigungen über AEM Web-Konsole. Eine schrittweise Anleitung finden Sie unter [E-Mail-Benachrichtigungen für den Schritt &quot;Aufgabe zuweisen&quot;konfigurieren](/help/forms/using/aem-forms-workflow.md)

* **HTML-E-Mail-Vorlage**: Wählen Sie die E-Mail-Vorlage für die Benachrichtigungs-E-Mail. Um eine Vorlage zu bearbeiten, ändern Sie die Datei unter /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt im crx-Repository.
* **Delegation zulassen an:** AEM Posteingang bietet eine Option für den angemeldeten Benutzer, den zugewiesenen Workflow an einen anderen Benutzer zu delegieren. Sie können innerhalb derselben Gruppe oder an den Workflow-Benutzer einer anderen Gruppe delegieren. Wenn die Aufgabe einem einzelnen Benutzer zugewiesen ist und die Option **Delegierung an Mitglieder der Gruppe an Verantwortlichen zulassen** aktiviert ist, kann die Aufgabe nicht an einen anderen Benutzer oder eine andere Gruppe übertragen werden.

* **Standardaktionen:** Standardmäßig sind die Aktionen &quot;Senden&quot;, &quot;Speichern&quot;und &quot;Zurücksetzen&quot;verfügbar. Alle Standardaktionen sind standardmäßig aktiviert.
* **Route-Variable:** Name der Route-Variablen. Die Route-Variable erfasst benutzerdefinierte Aktionen, die ein Benutzer im AEM-Posteingang auswählt.
* **Routen:** Eine Aufgabe kann zu verschiedenen Routen verzweigen. Bei Auswahl im AEM-Posteingang gibt die Route einen Wert zurück, und der Workflow verzweigt basierend auf der ausgewählten Route.
* **Routentitel**: Geben Sie den Titel für die an. Er wird im AEM-Posteingang angezeigt.
* **Korallensymbol**: Geben Sie das HTML-Attribut eines Korallensymbols an. Die Adobe CoralUI-Bibliothek bietet eine Vielzahl von Touch-First-Symbolen. Sie können ein Symbol für die Route auswählen und verwenden. Es wird zusammen mit dem Titel im AEM-Posteingang angezeigt.
* **Zulassen, dass Verantwortlicher Kommentare hinzufügt**: Wählen Sie diese Option, um Kommentare für die Aufgabe zu aktivieren. Ein Verantwortlicher kann die Kommentare innerhalb des AEM-Posteingangs zum Zeitpunkt der Aufgabenübermittlung hinzufügen.
* **Bevollmächtigten erlauben, Anlagen zur Aufgabe hinzuzufügen**: Wählen Sie diese Option aus, um Anlagen für die Aufgabe zu aktivieren. Ein Verantwortlicher kann die Anhänge im AEM-Posteingang zum Zeitpunkt der Aufgabenübermittlung hinzufügen.
* **Ausgabepfad der Aufgabenanlagen**: Geben Sie den Speicherort des Anlagenordners an. Der Speicherort ist relativ zur Payload.
* **Verwenden benutzerdefinierter Metadaten:** Wählen Sie diese Option aus, um das benutzerdefinierte Metadatenfeld zu aktivieren. Benutzerdefinierte Metadaten werden in E-Mail-Vorlagen verwendet.
* **Benutzerdefinierte Metadaten:** Wählen Sie benutzerdefinierte Metadaten für die E-Mail-Vorlagen. Die benutzerdefinierten Metadaten sind im CRX-Repository unter apps/fd/dashboard/scripts/metadataScripts verfügbar. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie können auch einen Service für die benutzerdefinierten Metadaten verwenden. Sie können auch die Schnittstelle `WorkitemUserMetadataService` erweitern, um benutzerdefinierte Metadaten bereitzustellen.

* **Daten aus vorherigen Schritten anzeigen**: Wählen Sie - falls verfügbar - diese Option aus, um den Bevollmächtigten das Anzeigen früherer Bevollmächtigter, bereits vorgenommener Aktionen, Kommentare zu dieser Aufgabe und des Nachweisdokuments über abgeschlossene Aufgaben zu ermöglichen.
* **Daten aus allen nachfolgenden Schritten einblenden:** Wählen Sie diese Option, um dem aktuellen Bearbeiter zu ermöglichen, die durchgeführte Aktion und Kommentare, die von nachfolgenden Beauftragten zur Aufgabe hinzugefügt wurden, anzuzeigen. Außerdem kann der aktuelle Bevollmächtigte ein Datensatzdokument der abgeschlossenen Aufgabe anzeigen, sofern verfügbar.
* **Sichtbarkeit des Datentyps:** Standardmäßig kann ein Bevollmächtigter ein Datensatzdokument, Bevollmächtigte, durchgeführte Aktionen und Kommentare anzeigen, die von früheren und nachfolgenden Bevollmächtigten hinzugefügt wurden. Verwenden Sie die Option „Sichtbarkeit des Datentyps“, um den Typ der für die Verantwortlichen sichtbaren Daten zu begrenzen.

## Schritt „E-Mail senden“ {#send-email-step}

Verwenden Sie den E-Mail-Schritt, um eine E-Mail zu senden, z. B. eine E-Mail mit einem Datensatzdokument, eine Verknüpfung eines adaptiven Formulars, eine Verknüpfung einer interaktiven Kommunikation oder ein angehängtes PDF-Dokument. Schritt E-Mail senden unterstützt [HTML-E-Mail](https://en.wikipedia.org/wiki/HTML_email). HTML-E-Mails sind responsiv und passen sich an den E-Mail-Client und die Bildschirmgröße der Empfänger an. Sie können eine HTML-E-Mail-Vorlage verwenden, um das Erscheinungsbild, das Farbschema und Verhalten der E-Mail zu definieren.

Beim E-Mail-Schritt wird der Day CQ Mail Service zum Senden von E-Mails verwenden. Stellen Sie vor Verwendung des E-Mail-Schritts sicher, dass die Variable [E-Mail-Dienst](/help/forms/using/aem-forms-workflow.md) konfiguriert ist. Der E-Mail-Schritt hat folgende Eigenschaften:

**Titel:** Der Titel des Schritts hilft, den Schritt im Workflow-Editor zu identifizieren.

**Beschreibung:** Erklärungen können für andere Entwickler nützlich sein, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

**E-Mail-Betreff:** Betreff kann aus Workflow-Metadaten abgerufen oder manuell angegeben werden. Wählen Sie die **Literal** Option zur manuellen Angabe eines Betreffs oder zur Auswahl der **Aus Workflow-Metadaten abrufen** -Option, um den Betreff aus einer Metadateneigenschaft abzurufen.

**HTML-E-Mail-Vorlage**: HTML-Vorlage für die E-Mail. Sie können Variablen in einer E-Mail-Vorlage spezifizieren. Der E-Mail-Schritt extrahiert und zeigt alle Variablen an, die in einer Vorlage für Eingaben enthalten sind.

**E-Mail-Vorlagen-Metadaten**: Der Wert der E-Mail-Vorlagenvariablen kann ein benutzerspezifizierter Wert, der Pfad eines Assets auf dem Autoren- oder Veröffentlichungs-Server, ein Bild oder eine Workflow-Metadateneigenschaft sein.

* **Literal:** Verwenden Sie die Option, wenn Sie den genauen Wert kennen, der angegeben werden soll. Beispiel: [beispiel@beispiel.com](mailto:example@example.com).

* **Workflow-Metadaten:** Verwenden Sie die Option , wenn der zu verwendende Wert in einer Workflow-Metadateneigenschaft gespeichert wird. Geben Sie nach Auswahl der Option den Namen der Metadateneigenschaft in das leere Textfeld unter der Option Workflow-Metadaten ein. Beispiel: e-mailAdresse.
* **Asset-URL**: Verwenden Sie diese Option zum Einbetten eines Weblinks einer interaktiven Kommunikation in die E-Mail. Nachdem Sie die Option ausgewählt haben, suchen Sie nach der interaktiven Kommunikation, die eingebettet werden soll. Das Asset kann sich auf dem Autoren- oder Veröffentlichungsserver befinden.
* **Bild:** Verwenden Sie die Option , um ein Bild in die E-Mail einzubetten. Nachdem Sie die Option ausgewählt haben, suchen Sie nach dem entsprechenden Bild und wählen Sie es aus. Die Bildoption ist nur für die Bild-Tags (&lt;img src=&quot;&amp;ast;&quot; />) verfügbar, die in der E-Mail-Vorlage verfügbar sind.

**E-Mail-Adresse des Absenders/Empfängers:** Wählen Sie die **Literal** Option zur manuellen Angabe einer E-Mail-Adresse oder zur Auswahl der **Aus Workflow-Metadaten abrufen** -Option zum Abrufen der E-Mail-Adresse aus einer Metadateneigenschaft. Sie können auch eine Liste von Metadateneigenschaften-Arrays für die Option **Aus Workflow-Metadaten abrufen** angeben.

**Dateianlagenpfad:** Das am angegebenen Speicherort verfügbare Asset wird an die E-Mail angehängt. Der Pfad des Assets kann relativ zur Payload oder zum absoluten Pfad sein. Ein Beispielpfad ist [Payload_Directory]/attachments/

**Dateiname:** Name der E-Mail-Anhangsdatei. Der E-Mail-Schritt ändert den Originaldateinamen des Anhangs in den angegebenen Dateinamen. Der Name kann manuell angegeben oder aus einer Workflow-Metadateneigenschaft abgerufen werden. Verwenden Sie die Option **Literal**, wenn Sie den genauen zu spezifizierenden Wert kennen. Verwenden Sie die Option **Aus Workflow-Metadaten abrufen**, wenn der zu verwendende Wert in einer Workflow-Metadateneigenschaft gespeichert wird.

## Schritt „Datensatzdokument generieren“ {#generate-document-of-record-step}

Wenn ein Formular ausgefüllt oder übermittelt wird, können Sie das Formular drucken oder als Dokument speichern. Dies wird als Datensatzdokument (DoR) bezeichnet. Sie können den Schritt Datensatzdokument generieren verwenden, um eine schreibgeschützte oder interaktive PDF-Version eines adaptiven Formulars zu erstellen. Die PDF-Version enthält Informationen, die im Formular ausgefüllt sind, zusammen mit dem Layout des adaptiven Formulars.

Der Schritt „Datensatzdokument generieren“ hat folgende Eigenschaften:

**Adaptives Formular verwenden**: Geben Sie die Methode zum Suchen des adaptiven Eingabeformulars an. Sie können das adaptive Formular verwenden, das in einem absoluten Pfad verfügbar ist, als Nutzlast an den Workflow übermittelt wird oder in einem Pfad verfügbar ist, der mithilfe einer Variablen berechnet wurde. Sie können eine Variable des Typs „Zeichenfolge“ verwenden, um den Pfad anzugeben.

**Adaptiver Formularpfad**: Geben Sie den Pfad des adaptiven Formulars an. Das Feld ist verfügbar, wenn Sie im Feld Typ ein adaptives Formular oder eine schreibgeschützte Option für ein adaptives Formular verwenden und im Feld Adaptives Formular verwenden die Option absoluter Pfad verwenden.

**Eingabedatenpfad:** Pfad der Eingabedaten für das adaptive Formular. Sie können die Daten an einem Speicherort relativ zur Payload beibehalten oder einen absoluten Pfad der Daten angeben. Die Eingabedaten werden mit dem adaptiven Formular zusammengeführt, um ein Datensatzdokument zu erstellen.

**Pfad für Eingabeanlage:** Pfad für Eingabeanlage: Pfad der Anlagen. Diese Anhänge sind im Datensatzdokument enthalten. Sie können die Anlagen an einem Speicherort relativ zur Payload belassen oder einen absoluten Pfad der Anlagen angeben.

Wenn Sie den Pfad eines Ordners angeben, z. B. Anhänge, werden alle Dateien, die direkt im Ordner verfügbar sind, an das Datensatzdokument angehängt. Wenn Dateien in den Ordnern verfügbar sind, die im angegebenen Pfad für den Anhang direkt verfügbar sind, werden die Dateien im Datensatzdokument als Anhänge aufgenommen. Wenn sich Ordner in direkt verfügbaren Ordnern befinden, werden diese übersprungen.

**Generierter Pfad für Datensatzdokument:** Geben Sie den Speicherort an, unter dem ein Datensatzdokument gespeichert werden soll. Sie können den Payload-Ordner überschreiben oder das Datensatzdokument an einem Speicherort innerhalb des Payload-Ordners platzieren.

**Gebietsschema**: Geben Sie die Sprache des Datensatzdokuments an.

## Schritt „Formulardatenmodell-Service aufrufen“ {#invoke-form-data-model-service-step}

Sie können [AEM Forms-Datenintegration](/help/forms/using/data-integration.md) verwenden, um unterschiedliche Datenquellen zu konfigurieren und Verbindungen zu ihnen herzustellen. Diese Datenquellen können eine Datenbank, ein Webdienst, ein REST-Dienst, ein OData-Dienst und eine CRM-Lösung sein. Mit der AEM Forms-Datenintegration können Sie ein Formulardatenmodell erstellen, das verschiedene Dienste umfasst, um Datenabruf-, Additions- und Aktualisierungsvorgänge für die konfigurierte Datenbank durchzuführen. Sie können den **Schritt „Formulardatenmodelldienst aufrufen“** verwenden, um ein Formulardatenmodell (FDM) zu wählen und die Dienste des FDM abzurufen, zu aktualisieren oder Daten unterschiedlichen Datenquellen hinzuzufügen.

Zur Erläuterung der Eingaben in die Felder des Schritts werden die folgende Datenbanktabelle und die JSON-Datei als Beispiel verwendet:

**Beispiel-Tabelle mit Kundendetails**

<table> 
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
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
* **Eingabe für Dienste > Bereitstellen von Eingabedaten mithilfe von Literal, Workflow-Metadaten und einer JSON-Datei**: Ein Dienst kann mehrere Argumente haben. Wählen Sie die Option aus, um den Wert der Dienstargumente aus einer Workflow-Metadateneigenschaft oder einem JSON-Objekt abzurufen, oder geben Sie den Wert direkt in das bereitgestellte Textfeld ein:

   * **Literal:** Verwenden Sie die Option, wenn Sie den genauen Wert kennen, der angegeben werden soll. Beispiel: srose@we.info.
   * **Aus Workflow-Metadaten abrufen:** Verwenden Sie die Option , wenn der zu verwendende Wert in einer Workflow-Metadateneigenschaft gespeichert wird. Beispiel: e-mailAddress.
   * **JSON Dot Notation:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer JSON-Datei enthalten ist. Beispielsweise ist die Option &quot;insurance.customerDetails.emailAddress.The JSON Dot Notation&quot;nur verfügbar, wenn die Option Eingabefelder aus Eingabe-JSON zuordnen ausgewählt ist.
   * **Zuordnen von Eingabefelder aus der Eingabe JSON:** Geben Sie den Pfad einer JSON-Datei an, um den Eingabewert einiger Service-Parameter aus der JSON-Datei abzurufen. Der Pfad der JSON-Datei kann relativ zur Payload oder ein absoluter Pfad sein.

* **Eingabe für Dienste > Bereitstellen von Eingabedaten mithilfe einer JSON-Datei:** Wählen Sie die Option aus, um Werte für alle Argumente aus einer JSON-Datei abzurufen.
* **Eingabe-JSON-Dateipfad**: Pfad der JSON-Datei mit Werten für alle Service-Argumente. Der Pfad der JSON-Datei kann **relativ zur Payload** oder ein **absoluter Pfad** sein.

* **JSON Dot Notation:** Lassen Sie das Feld leer, um alle Objekte der angegebenen JSON-Datei als Eingabe für Dienstargumente zu verwenden. Um ein bestimmtes JSON-Objekt aus der angegebenen JSON-Datei als Eingabe für Service-Argumente zu lesen, geben Sie die Dot Notation für das JSON-Objekt an, z. B. wenn Sie eine JSON ähnlich wie am Anfang des Abschnitts aufgeführt haben, geben Sie „insurance.customerDetails“ an, um alle Details eines Kunden als Eingabe für den Service anzugeben.
* **Ausgabe des Dienstes > Zuordnen und Schreiben von Ausgabewerten zu Metadaten:** Wählen Sie die Option zum Speichern der Ausgabewerte als Eigenschaften des Metadatenknotens der Workflow-Instanz im crx-Repository aus. Geben Sie den Namen der Metadateneigenschaft an und wählen Sie das entsprechende Service-Ausgabeattribut, das der Metadateneigenschaft zugeordnet werden soll, ordnen Sie z. B. die vom Ausgabe-Service zurückgegebene Telefonnummer der Eigenschaft „phone_number“ der Workflow-Metadaten zu.
* **Ausgabe des Dienstes > Ausgabe als JSON speichern:** Wählen Sie die Option zum Speichern der Ausgabewerte in einer JSON-Datei aus.
* **Pfad der JSON-Ausgabedatei:** Pfad zum Speichern der JSON-Ausgabedatei. Der Pfad der JSON-Ausgabedatei kann relativ zur Payload oder einem absoluten Pfad sein.

## Schritt „Dokument signieren“ {#sign-document-step}

Der Schritt Dokument signieren ermöglicht Ihnen die Verwendung von Acrobat Sign zum Signieren von Dokumenten. Der Schritt „Dokument signieren“ hat folgende Eigenschaften:

* **Name der Vereinbarung:** Geben Sie den Titel der Vereinbarung an. Der Name der Vereinbarung wird Teil des Betreffs und des Textkörpers der E-Mail, die an die Unterzeichner gesendet wird.
* **Gebietsschema:** Geben Sie die Sprache für die E-Mail- und Bestätigungsoptionen an. 
* **Acrobat Sign Cloud-Konfiguration**: Wählen Sie eine Acrobat Sign Cloud-Konfiguration aus. Wenn Sie Acrobat Sign nicht für AEM Forms konfiguriert haben, finden Sie weitere Informationen unter [Integrieren von Acrobat Sign mit AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Zu signierendes Dokument:** Sie können ein Dokument an einem Speicherort auswählen, der relativ zur Payload ist, die Payload als Dokument verwenden oder einen absoluten Pfad des Dokuments angeben.
* **Pfad für Eingabeanlage:** Wählen Sie eine Anlage aus. Diese Anlagen sind im Signaturdokument enthalten. Sie können die Anlagen an einem Speicherort relativ zur Payload belassen oder einen absoluten Pfad der Anlagen angeben.

   Wenn Sie den Pfad eines Ordners angeben, z. B. Anhänge, werden alle Dateien, die direkt im Ordner verfügbar sind, an das Datensatzdokument angehängt. Wenn Dateien in den Ordnern verfügbar sind, die im angegebenen Anlagenpfad direkt verfügbar sind, werden die Dateien im Signaturdokument als Anlagen aufgenommen. Wenn sich Ordner in direkt verfügbaren Ordnern befinden, werden diese übersprungen.
* **Tage bis Abgabetermin:** Ein Dokument wird als „fällig“ (Abgabetermin überschritten) gekennzeichnet, nachdem für die im Feld **Tage bis Abgabetermin** angegebene Anzahl von Tagen keine Aktivität für die Aufgabe ermittelt wurde. Die Anzahl der Tage wird gezählt, nachdem das Dokument einem Benutzer zur Unterzeichnung zugewiesen wurde.

* **Häufigkeit der E-Mail-Erinnerung:** Sie können eine Erinnerungs-E-Mail im täglichen oder wöchentlichen Intervall senden. Die Woche wird ab dem Tag gezählt, an dem das Dokument einem Benutzer zum Signieren zugewiesen wurde.
* **Signaturprozess:** Sie können ein Dokument in einer sequenziellen oder parallelen Reihenfolge signieren. Bei sequenzieller Reihenfolge erhält jeweils nur ein Unterzeichner das Formular zur Unterzeichnung. Nachdem der erste Unterzeichner das Signieren des Dokuments abgeschlossen hat, wird das Dokument an den zweiten Unterzeichner gesendet usw. Bei paralleler Reihenfolge können mehrere Unterzeichner ein Formular gleichzeitig signieren.

* **Umleitungs-URL:** Geben Sie eine Umleitungs-URL an. Nachdem das Dokument signiert wurde, können Sie den Verantwortlichen an eine URL umleiten. Normalerweise enthält diese URL eine Dankesnachricht oder weitere Anweisungen.
* **Workflow-Phase:** Ein Workflow kann mehrere Phasen enthalten. Diese werden im AEM-Posteingang angezeigt. Sie können diese Schritte in den Eigenschaften des Modells definieren (Sidekick > Seite > Seiteneigenschaften > Schritte).
* **Unterzeichner wählen:** Geben Sie die Methode zum Auswählen von Unterzeichnern für das Dokument an. Sie können den Workflow einem Benutzer oder einer Gruppe dynamisch zuweisen oder manuell Details zu einem Unterzeichner hinzufügen.
* **Skript oder Dienst zur Auswahl von Unterzeichnern:** Die Option ist nur verfügbar, wenn im Feld Unterzeichner auswählen die Option Dynamisch ausgewählt ist. Sie können ein ECMAScript oder einen Service angeben, um Unterzeichner und Verifizierungsoptionen für ein Dokument auszuwählen.

* **Unterzeichnerdetails:** Die Option ist nur verfügbar, wenn die Option „Manuell“ im Feld „Unterzeichner auswählen“ ausgewählt ist. Geben Sie die E-Mail-Adresse an und wählen Sie einen optionalen Verifizierungsmechanismus aus. Bevor Sie einen zweistufigen Überprüfungsmechanismus auswählen, stellen Sie sicher, dass die entsprechende Überprüfungsoption für das konfigurierte Acrobat Sign-Konto aktiviert ist.
* **Statusvariable:** Ein für Acrobat Sign aktiviertes Dokument speichert den Signaturstatus des Dokuments in einer Variablen. Geben Sie den Namen der Statusvariable (adobeSignStatus) an. Eine Statusvariable einer Instanz ist in CRXDE unter /etc/workflow/instances/&lt;Server>/&lt;Datum/Uhrzeit>/&lt;Instanz des Workflow-Modells>/workItems/&lt;Knoten>/metaData verfügbar und enthält den Status einer Variablen.
* **Signed Document Path:** Geben Sie den Speicherort für signierte Dokumente an. Sie können die Payload-Datei überschreiben oder das signierte Dokument an einem Speicherort im Payload-Verzeichnis ablegen.

## Document Services-Schritte {#document-services-steps}

AEM Document Services sind eine Reihe von Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten. AEM Forms bietet einen separaten AEM Workflow-Schritt für jeden Dokumentdienst:

### Schritt &quot;Dokumentzeitstempel anwenden&quot; {#apply-document-time-stamp-step}

Fügen Sie einem Dokument einen Zeitstempel hinzu. Sie geben Dokumentdetails wie den Pfad des Eingabedokuments, den Namen des Eingabedokuments und den Speicherort für exportierte Daten an. Sie können die vorhandene Payload-Datei überschreiben oder einen anderen Dateinamen wählen, um Daten in einer anderen Datei im Payload-Ordner zu speichern.

### Schritt „In Bild umwandeln“ {#convert-to-image-step}

Konvertiert ein PDF-Dokument in eine Bilddatei. Unterstützte Bildformate sind JPEG, JPEG2000, PNG und TIFF. Die folgenden Informationen gelten für Konvertierungen in TIFF-Bilder:

* Eine mehrseitige TIFF-Datei wird generiert.
* Einige Anmerkungen sind nicht in TIFF-Bildern enthalten. Anmerkungen, für die Acrobat das Erscheinungsbild generieren muss, sind nicht enthalten.

### Schritt „Nach PDF/A konvertieren“ {#convert-to-pdf-a-step}

Konvertiert ein PDF-Dokument mithilfe der bereitgestellten Optionen in das PDF/A-Format. Die PDF/A-Version des Portable Document Format (PDF) ist auf die Archivierung und Langzeitarchivierung von Dokumenten spezialisiert. 

### Schritt &quot;In PS konvertieren&quot; {#convert-to-ps-step}

Konvertieren von PDF-Dokumenten in PostScript – Beim Konvertieren in PostScript können Sie den Konvertierungsvorgang verwenden, um das Quelldokument anzugeben und festzulegen, ob es in PostScript Level 2 oder 3 konvertiert werden soll. Das PDF-Dokument, das Sie in eine PostScript-Datei konvertieren, muss nicht interaktiv sein.

### Schritt &quot;PDF erstellen&quot;mit dem angegebenen Typ {#create-pdf-from-specified-type-step}

Generieren Sie ein PDF-Dokument aus einer Eingabedatei. Das Eingabedokument kann relativ zur Payload sein, einen absoluten Pfad haben oder selbst Payload sein.

### Schritt &quot;PDF aus URL/HTML/ZIP erstellen&quot; {#create-pdf-from-url-html-zip-step}

Generiert ein PDF-Dokument aus der bereitgestellten URL-, HTML- und ZIP-Datei.

### Schritt &quot;Daten exportieren&quot; {#export-data-step}

Exportiert Daten aus einer PDF forms- oder XDP-Datei. Sie müssen den Dateipfad des Eingabedokuments und das Exportdatenformat eingeben. Die Optionen für &quot;Datenformat exportieren&quot;sind &quot;Auto&quot;, &quot;XDP&quot;und &quot;XmlData&quot;.

### Export PDF zum angegebenen Typschritt {#export-pdf-to-specified-type-step}

Konvertiert ein PDF-Dokument in ein ausgewähltes Format.

### Schritt &quot;Nicht-interaktive PDF generieren&quot; {#generate-non-interactive-pdf-step}

Erstellen Sie eine nicht interaktive PDF. Es sind verschiedene Anpassungsoptionen verfügbar. 

### Schritt &quot;Daten importieren&quot; {#import-data-step}

Führt Formulardaten in einem PDF-Formular zusammen. Sie können Formulardaten in ein PDF-Formular importieren.

### Schritt „DDX aufrufen“ {#invoke-ddx-step}

Führt die DDX-Datei auf der angegebenen Zuordnung von Eingabedokumenten aus und gibt die bearbeiteten PDF-Dokumente zurück.

### Optimize PDF {#optimize-pdf-step}

Optimiert PDF-Dateien durch Reduzierung ihrer Größe. Als Ergebnis dieser Konvertierung erhalten Sie PDF-Dateien, die eventuell kleiner sind als die Originalversionen. Bei diesem Vorgang werden auch PDF-Dokumente in die in den Optimierungsparametern angegebene PDF-Version konvertiert.

In den Optimierungseinstellungen wird festgelegt, wie Dateien optimiert werden. Im Folgenden finden Sie Beispieleinstellungen:

* PDF-Zielversion
* Verwerfen von Objekten wie JavaScript-Aktionen und eingebetteten Seitenminiaturansichten
* Verwerfen von Benutzerdaten wie Kommentaren und Dateianlagen
* Verwerfen ungültiger oder nicht verwendeter Einstellungen
* Komprimieren unkomprimierter Daten oder Verwenden effizienterer Komprimierungsalgorithmen
* Entfernen eingebetteter Schriftarten
* Festlegen von Transparenzwerten

### Schritt &quot;PDF Formular rendern&quot; {#render-pdf-form-step}

Gibt ein in Form Designer (XDP) erstelltes Formular in ein PDF-Formular zurück.

### Schritt &quot;Dokument sichern&quot; {#secure-document-step}

Verschlüsseln, Signieren und Zertifizieren eines Dokuments. AEM Forms unterstützt sowohl die kennwortbasierte als auch die zertifikatbasierte Verschlüsselung. Sie können auch zwischen verschiedenen Algorithmen zum Signieren von Dokumenten wählen. Beispiel: SHA-256 und SH-512. Sie können den Workflow-Schritt auch verwenden, um PDF-Dokumente zu lesen. Der Workflow-Schritt bietet Optionen zum Aktivieren von Barcode-Dekodierung, digitalen Signaturen, Importieren und Exportieren von PDF-Daten und anderen Optionen.

### Schritt &quot;An Drucker senden&quot; {#send-to-printer-step}

Senden Sie ein Dokument direkt an einen Drucker. Es unterstützt die folgenden Druckerzugriffsmechanismen:

* **Drucker mit direktem Zugriff**: Ein Drucker, der auf demselben Computer installiert ist, wird als Drucker mit direktem Zugriff bezeichnet und der Computer heißt Druckerhost. Dieser Druckertyp kann ein lokaler Drucker sein, der direkt mit dem Computer verbunden ist.
* **Drucker mit indirektem Zugriff**: Auf den Drucker, der auf einem Druckserver installiert ist, kann von anderen Computern aus zugegriffen werden. Es stehen Technologien wie das Common UNIX® Printing System (CUPS) und das LPD-Protokoll (Line Printer Daemon) zur Verfügung, um eine Verbindung zu einem Netzwerkdrucker herzustellen. Um auf einen Drucker mit indirektem Zugriff zuzugreifen, geben Sie die IP-Adresse oder den Hostnamen des Druckservers an. Mit diesem Mechanismus können Sie ein Dokument an einen LPD-URI senden, wenn das Netzwerk über eine LPD verfügt. Mit dem Mechanismus können Sie das Dokument zu jedem Drucker weiterleiten, der mit dem Netzwerk verbunden ist, auf dem ein LPD ausgeführt wird.
