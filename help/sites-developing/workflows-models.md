---
title: Erstellen von Workflow-Modellen
seo-title: Creating Workflow Models
description: Sie erstellen ein Workflow-Modell, um die Schritte zu definieren, die ausgeführt werden, wenn ein Benutzer den Workflow startet.
seo-description: You create a workflow model to define the series of steps executed when a user starts the workflow.
uuid: 53d94176-4d5f-4ab3-9628-6b7d44f81139
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 9d2dba11-0d2d-4aed-b941-c8ade9bb7bfa
exl-id: d9c9db5f-9788-460f-ac09-88dd3c911edd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2483'
ht-degree: 42%

---

# Erstellen von Workflow-Modellen{#creating-workflow-models}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!CAUTION]
>
>Informationen zur Verwendung der klassischen Benutzeroberfläche finden Sie in der [Dokumentation zu AEM 6.3](https://helpx.adobe.com/de/experience-manager/6-3/sites-developing/workflows-models.html) als Referenz.

Sie erstellen eine [Workflow-Modell](/help/sites-developing/workflows.md#model) , um die Schritte zu definieren, die beim Starten des Workflows ausgeführt werden. Sie können auch Modelleigenschaften definieren, um beispielsweise festzulegen, ob es sich um einen Übergangs-Workflow oder einen Workflow mit mehreren Ressourcen handelt.

Wenn ein Benutzer einen Workflow startet, wird eine Instanz gestartet. Dies ist das entsprechende Laufzeitmodell, das erstellt wird, wenn Sie [Synchronisieren](#sync-your-workflow-generate-a-runtime-model) Ihre Änderungen.

## Erstellen eines neuen Workflows {#creating-a-new-workflow}

Wenn Sie zum ersten Mal ein neues Workflow-Modell erstellen, enthält es Folgendes:

* Die Schritte **[!UICONTROL Fluss-Start]** und **[!UICONTROL Fluss-Ende]**.

   Diese stellen den Anfang und das Ende des Workflows dar. Diese Schritte sind erforderlich und können nicht bearbeitet oder entfernt werden.

* Ein **Teilnehmer**-Beispielschritt namens **Schritt 1**.

   Dieser Schritt ist so konfiguriert, dass er dem Workflow-Initiator ein Arbeitselement zuordnet. Sie können diesen Schritt nach Bedarf bearbeiten oder löschen und Schritte hinzufügen.

Gehen Sie folgendermaßen vor, um einen neuen Workflow mit dem Editor zu erstellen:

1. Öffnen Sie die **[!UICONTROL Workflow-Modelle]** Konsole; durch **[!UICONTROL Instrumente]**, **[!UICONTROL Workflow]**, **[!UICONTROL Modelle]** oder beispielsweise:

   [http://localhost:4502/aem/workflow](http://localhost:4502/aem/workflow)

1. Wählen Sie **[!UICONTROL Erstellen]** und dann **[!UICONTROL Modell erstellen]** aus.
1. Die **[!UICONTROL Workflow-Modell hinzufügen]** angezeigt. Geben Sie die **[!UICONTROL Titel]** und **[!UICONTROL Name]** (optional) vor Auswahl **[!UICONTROL Fertig]**.
1. Das neue Modell wird nun in der **[!UICONTROL Workflow-Modelle-Konsole]** aufgeführt.
1. Wählen Sie Ihren neuen Workflow aus und öffnen Sie ihn dann, indem Sie auf [**[!UICONTROL Bearbeiten ]**klicken, um ihn zu konfigurieren](#editing-a-workflow):

   ![wf-01](assets/wf-01.png)

>[!NOTE]
>
>Wenn Sie Modelle programmgesteuert (mithilfe eines CRX-Pakets) erstellen, können Sie auch einen Unterordner erstellen:
>
>`/var/workflow/models`
>
>Beispiel: `/var/workflow/models/prototypes`
>
>Dieser Ordner kann dann für [Verwalten des Zugriffs auf die Modelle in diesem Ordner](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that).

## Workflow bearbeiten {#editing-a-workflow}

Sie können jedes vorhandene Workflow-Modell bearbeiten, um:

* [Definieren von Schritten](#adding-a-step-to-a-model) und [parameters](#configuring-a-workflow-step)

* Konfigurieren von Workflow-Eigenschaften, einschließlich [Phasen](#configuring-workflow-stages-that-show-workflow-progress), [ob der Workflow vorübergehend ist](#creating-a-transient-workflow) und/oder [verwendet mehrere Ressourcen](#configuring-a-workflow-for-multi-resource-support)

Bearbeiten von [**Standard oder veraltet** (vordefinierter) Workflow](#editing-a-default-or-legacy-workflow-for-the-first-time) einen zusätzlichen Schritt umfasst, um sicherzustellen, dass ein [sichere Kopie](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) vor der Durchführung Ihrer Änderungen durchgeführt werden.

Wenn Aktualisierungen Ihres Workflows abgeschlossen sind, müssen Sie **[!UICONTROL Synchronisieren]** nach **[!UICONTROL Laufzeitmodell erstellen]**. Siehe [Workflow synchronisieren](#sync-your-workflow-generate-a-runtime-model) für Details.

### Workflow synchronisieren - Laufzeitmodell erstellen {#sync-your-workflow-generate-a-runtime-model}

**Synchronisieren** (direkt in der Editor-Symbolleiste) generiert eine [Laufzeitmodell](/help/sites-developing/workflows.md#runtime-model). Das Laufzeitmodell ist das Modell, das tatsächlich verwendet wird, wenn ein Benutzer einen Workflow startet. Wenn Sie Ihre Änderungen nicht durch Klicken auf **[!UICONTROL Sync]** synchronisieren, stehen diese nicht zur Laufzeit zur Verfügung.

Wenn Sie (oder ein anderer Benutzer) Änderungen am Workflow vornehmen, müssen Sie **[!UICONTROL Synchronisieren]** um ein Laufzeitmodell zu generieren - auch wenn einzelne Dialogfelder (z. B. für Schritte) über eigene Speicheroptionen verfügten.

Wenn die Änderungen mit dem (gespeicherten) Laufzeitmodell synchronisiert werden, **[!UICONTROL Synchronisiert]** stattdessen angezeigt.

Einige Schritte verfügen über obligatorische Felder und/oder eine integrierte Validierung. Wenn diese Bedingungen nicht erfüllt sind, wird beim Versuch, einen Fehler angezeigt **[!UICONTROL Synchronisieren]** das Modell. Etwa wenn für einen **[!UICONTROL Teilnehmer]**-Schritt kein Teilnehmer definiert wurde:

![wf-21](assets/wf-21.png)

### Erstmalige Bearbeitung eines Standard- oder Legacy-Workflows {#editing-a-default-or-legacy-workflow-for-the-first-time}

Wenn Sie eine [Standardmodell und/oder Legacy-Modell](/help/sites-developing/workflows.md#workflow-types) zur Bearbeitung:

* Die **[!UICONTROL Schritte]** -Browser nicht verfügbar (linke Seite).
* Die Symbolleiste weist eine Option zum **[!UICONTROL Bearbeiten]** auf (auf der rechten Seite).
* Zunächst werden das Modell und seine Eigenschaften im schreibgeschützten Modus wie folgt dargestellt:

   * Standard-Workflows befinden sich unter `/libs`.
   * Ältere Workflows befinden sich unter `/etc`

Auswählen **[!UICONTROL Bearbeiten]** wird:

* eine Kopie des Workflows unter `/conf` gespeichert
* erstellen **[!UICONTROL Schritte]** Browser verfügbar
* es möglich, Änderungen vorzunehmen.

>[!NOTE]
>
>Unter [Speicherorte von Workflow-Modellen](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) finden Sie weitere Informationen.

![wf-22](assets/wf-22.png)

### Hinzufügen eines Schritts zu einem Modell {#adding-a-step-to-a-model}

Sie müssen Ihrem Modell Schritte hinzufügen, um die auszuführende Aktivität darzustellen. Jeder Schritt führt eine bestimmte Aktivität aus. Eine Auswahl von Schritt-Komponenten ist in einer AEM-Standardinstanz verfügbar.

Wenn Sie ein Modell bearbeiten, werden die verfügbaren Schritte in den verschiedenen Gruppen der **[!UICONTROL Schritte]** Browser. Beispiel:

![wf-10](assets/wf-10.png)

>[!NOTE]
>
>Informationen zu den Komponenten des primären Schritts, die mit AEM installiert werden, finden Sie unter [Referenz zu Workflow-Schritten](/help/sites-developing/workflows-step-ref.md).

**So fügen Sie einem Modell einen Schritt hinzu**:

1. Öffnen Sie ein vorhandenes Workflow-Modell zur Bearbeitung. Wählen Sie in der **[!UICONTROL Workflow-Modelle-Konsole]** das gewünschte Modell aus und klicken Sie anschließend auf **[!UICONTROL Bearbeiten]**.
1. Öffnen Sie die **[!UICONTROL Schritte]** Browser; using **[!UICONTROL Seitliches Bedienfeld ein/aus]**, ganz links in der oberen Symbolleiste. Folgende Informationen/Optionen sind verfügbar:

   * **[!UICONTROL Filter]** für bestimmte Schritte.
   * Verwenden Sie die Dropdown-Auswahl, um die Auswahl auf eine bestimmte Gruppe von Schritten zu beschränken.
   * Über das Symbol ![wf-stepinfo-icon](assets/wf-stepinfo-icon.png) zum Anzeigen von Breschreibungen können Sie weitere Informationen zum jeweiligen Schritt anzeigen.

   ![wf-02](assets/wf-02.png)

1. Ziehen Sie die entsprechenden Schritte an die gewünschte Position im Modell.

   Beispiel: eine **[!UICONTROL Teilnehmer-Schritt]**.

   Nachdem es zum Fluss hinzugefügt wurde, können Sie [Schritt konfigurieren](#configuring-a-workflow-step).

   ![wf-03](assets/wf-03.png)

1. Fügen Sie nach Bedarf beliebig viele Schritte oder andere Aktualisierungen hinzu.

   Zur Laufzeit werden die Schritte in der Reihenfolge ausgeführt, in der sie im Modell angezeigt werden. Nachdem Sie Schritt-Komponenten hinzugefügt haben, können Sie sie an eine andere Position im Modell ziehen.

   Sie können auch vorhandene Schritte kopieren, ausschneiden, einfügen, gruppieren oder löschen. wie bei [Seiteneditor.](/help/sites-authoring/editing-content.md)

   Unterteilte Schritte können auch mithilfe der Symbolleistenoption ![wf-collapseexpand-toolbar-icon](assets/wf-collapseexpand-toolbar-icon.png) ein- oder ausgeblendet werden. 

1. Bestätigen Sie Ihre Änderungen, indem Sie in der Editor-Symbolleiste auf **[!UICONTROL Sync]** klicken, um das Laufzeitmodell zu generieren.

   Siehe [Workflow synchronisieren](#sync-your-workflow-generate-a-runtime-model) für Details.

### Konfigurieren eines Workflow-Schritts {#configuring-a-workflow-step}

Sie können **Konfigurieren** und passen Sie das Verhalten eines Workflow-Schritts mithilfe des **[!UICONTROL Schritt-Eigenschaften]** Dialogfelder.

1. So öffnen Sie die **[!UICONTROL Schritt-Eigenschaften]** Dialogfeld für einen Schritt:

   * Tippen Sie auf den Schritt im Workflow-Modell und wählen Sie **[!UICONTROL Konfigurieren]** aus der Komponenten-Symbolleiste.
   * Doppelklicken Sie auf den Schritt.

   >[!NOTE]
   >
   >Informationen zu den Komponenten des primären Schritts, die mit AEM installiert werden, finden Sie unter [Referenz zu Workflow-Schritten](/help/sites-developing/workflows-step-ref.md).

1. Konfigurieren Sie die **[!UICONTROL Schritt-Eigenschaften]** nach Bedarf; Je nach Schritttyp stehen verschiedene verfügbare Eigenschaften zur Verfügung. Es können auch mehrere Registerkarten verfügbar sein. Beispiel: der standardmäßige **[!UICONTROL Teilnehmer-Schritt]**, der in einem neuen Workflow als `Step 1` enthalten ist:

   ![wf-11](assets/wf-11.png)

1. Bestätigen Sie die Änderungen durch Klicken auf das Häkchen-Symbol.
1. Bestätigen Sie Ihre Änderungen, indem Sie in der Editor-Symbolleiste auf **[!UICONTROL Sync]** klicken, um das Laufzeitmodell zu generieren.

   Siehe [Workflow synchronisieren](#sync-your-workflow-generate-a-runtime-model) für Details.

### Erstellen eines Verlaufs-Workflows {#creating-a-transient-workflow}

Sie können eine [Übergangs](/help/sites-developing/workflows.md#transient-workflows) Workflow-Modell beim Erstellen eines neuen Modells oder durch Bearbeiten eines vorhandenen Modells:

1. Öffnen Sie das Workflow-Modell für [Bearbeiten](#editing-a-workflow).
1. Auswählen **[!UICONTROL Workflow-Modelleigenschaften]** aus der Symbolleiste.
1. Aktivieren Sie im Dialogfeld **[!UICONTROL Übergangs-Workflow]** (bzw. bei Bedarf deaktivieren):

   ![wf-07](assets/wf-07.png)

1. Bestätigen Sie die Änderung mit **[!UICONTROL Speichern und schließen]** und klicken Sie anschließend in der Editor-Symbolleiste auf **[!UICONTROL Sync]**, um das Laufzeitmodell zu generieren.

   Siehe [Workflow synchronisieren](#sync-your-workflow-generate-a-runtime-model) für Details.

>[!NOTE]
>
>Wenn Sie einen Workflow in [transient](/help/sites-developing/workflows.md#transient-workflows) AEM speichert keinen Workflow-Verlauf. Aus diesem Grund werden in der [Zeitleiste](/help/sites-authoring/basic-handling.md#timeline) keine Informationen zu diesem Workflow angezeigt. [](/help/sites-authoring/basic-handling.md#timeline)

### Workflow-Modelle in der Touch-Benutzeroberfläche verfügbar machen {#make-workflow-models-available-in-touchui}

Befolgen Sie die Konfiguration, wenn ein Workflow-Modell der klassischen Benutzeroberfläche im Auswahl-Popup-Menü der **[!UICONTROL Zeitleiste]** in der Touch-Benutzeroberfläche fehlt und verfügbar gemacht werden muss. Die folgenden Schritte zeigen die Verwendung des Workflow-Modells namens **[!UICONTROL Aktivierungsanfrage]**.

1. Vergewissern Sie sich, dass das Modell nicht in der Touch-Benutzeroberfläche verfügbar ist. Greifen Sie über den Pfad `/assets.html/content/dam` auf ein Asset zu. Auswählen eines Assets. Öffnen Sie **[!UICONTROL Zeitleiste]** in der linken Leiste. Klicken Sie auf **[!UICONTROL Workflow starten]** und bestätigen Sie, dass das **[!UICONTROL Aktivierungsanfrage]**-Modell nicht in der Popup-Liste vorhanden ist.

1. Navigieren Sie wie folgt: **[!UICONTROL Tools > Allgemein > Tagging]**. Wählen Sie **[!UICONTROL Workflow]**.

1. Wählen Sie **[!UICONTROL Erstellen > Tag erstellen]**. Legen Sie den **[!UICONTROL Titel]** als `DAM` und den **[!UICONTROL Namen]** als `dam` fest. Klicken Sie auf **[!UICONTROL Übermitteln]**.
   ![Tag im Workflow-Modell erstellen](assets/workflow_create_tag.png)

1. Gehen Sie zu **[!UICONTROL Tools > Workflow > Modelle]**. Wählen Sie **[!UICONTROL Aktivierungsanfrage]** aus und wählen Sie dann **[!UICONTROL Bearbeiten]**.

1. Auswählen **[!UICONTROL Bearbeiten]** , dann öffnen **[!UICONTROL Workflow-Modelleigenschaften]**. Navigieren Sie zu **[!UICONTROL Allgemein]** Registerkarte.

1. Fügen Sie `Workflow : DAM` zum Feld **[!UICONTROL Tags]** hinzu. Bestätigen Sie die Auswahl mit dem Häkchen.

1. Bestätigen Sie das Hinzufügen des Tags mit **[!UICONTROL Speichern und schließen]**.
   ![Seiteneigenschaften des Modells bearbeiten](assets/workflow_model_edit_activation1.png)

1. Schließen Sie den Prozess mit **[!UICONTROL Synchronisieren]** ab. Der Workflow ist jetzt in der Touch-optimierten Benutzeroberfläche verfügbar.

### Konfigurieren eines Workflows für die Unterstützung mehrerer Ressourcen {#configuring-a-workflow-for-multi-resource-support}

Sie können ein Workflow-Modell für [Unterstützung mehrerer Ressourcen](/help/sites-developing/workflows.md#multi-resource-support) beim Erstellen eines neuen Modells oder durch Bearbeiten eines vorhandenen Modells:

1. Öffnen Sie das Workflow-Modell für [Bearbeiten](#editing-a-workflow).
1. Auswählen **[!UICONTROL Workflow-Modelleigenschaften]** aus der Symbolleiste.

1. Aktivieren Sie im Dialogfeld **[!UICONTROL Unterstützung mehrerer Ressourcen]** (bzw. bei Bedarf deaktivieren):

   ![wf-08](assets/wf-08.png)

1. Bestätigen Sie die Änderung mit **[!UICONTROL Speichern und schließen]** und klicken Sie anschließend in der Editor-Symbolleiste auf **[!UICONTROL Sync]**, um das Laufzeitmodell zu generieren.

   Siehe [Workflow synchronisieren](#sync-your-workflow-generate-a-runtime-model) für Details.

### Konfigurieren von Workflow-Phasen (die den Workflow-Fortschritt anzeigen) {#configuring-workflow-stages-that-show-workflow-progress}

Die [Workflow-Phasen](/help/sites-developing/workflows.md#workflow-stages) sind hilfreich, um den Fortschritt eines Workflows beim Ausführen von Aufgaben anzuzeigen.

>[!CAUTION]
>
>Wenn Workflow-Phasen definiert sind in **[!UICONTROL Seiteneigenschaften]**, aber nicht für einen der Workflow-Schritte verwendet wird, zeigt die Fortschrittsleiste keinen Fortschritt an (unabhängig vom aktuellen Workflow-Schritt).

Die verfügbaren Phasen werden in den Workflow-Modellen definiert. vorhandene Workflow-Modelle können aktualisiert werden, um Statusdefinitionen einzuschließen. Sie können eine beliebige Anzahl von Phasen für das Workflow-Modell definieren.

Zu definieren **[!UICONTROL Phasen]** für Ihren Workflow:

1. Öffnen Sie Ihr Workflow-Modell zur Bearbeitung.
1. Auswählen **[!UICONTROL Workflow-Modelleigenschaften]** aus der Symbolleiste. Öffnen Sie dann die **[!UICONTROL Phasen]** Registerkarte.
1. Fügen Sie Ihre Anforderungen hinzu (und positionieren Sie sie) **[!UICONTROL Phasen]**. Sie können eine beliebige Anzahl von Phasen für das Workflow-Modell definieren.

   Beispiel:

   ![wf-08-1](assets/wf-08-1.png)

1. Klicken **[!UICONTROL Speichern und schließen]** , um die Eigenschaften zu speichern.
1. Weisen Sie jedem Schritt im Workflow-Modell eine Phase zu. Beispiel:

   ![wf-09](assets/wf-09.png)

   Eine Phase kann mehreren Schritten zugewiesen werden. Beispiel:

   | **Schritt** | **Staging** |
   |---|---|
   | Schritt 1 | Erstellen |
   | Schritt 2 | Erstellen |
   | Schritt 3 | Überprüfung |
   | Schritt 4 | Genehmigen |
   | Schritt 5 | Genehmigen |
   | Schritt 6 | Fertig stellen |

1. Bestätigen Sie Ihre Änderungen, indem Sie in der Editor-Symbolleiste auf **[!UICONTROL Sync]** klicken, um das Laufzeitmodell zu generieren.

   Siehe [Workflow synchronisieren](#sync-your-workflow-generate-a-runtime-model) für Details.

## Exportieren eines Workflow-Modells in ein Package {#exporting-a-workflow-model-in-a-package}

1. Erstellen Sie ein neues Paket mit dem [Package Manager](/help/sites-administering/package-manager.md#package-manager):

   1. Navigieren Sie zum Package Manager über **[!UICONTROL Instrumente]**, **[!UICONTROL Implementierung]**, **[!UICONTROL Pakete]**.
   1. Klicken Sie auf **[!UICONTROL Paket erstellen]**.
   1. Geben Sie die **[!UICONTROL Paketname]** und ggf. weitere Details.
   1. Klicken Sie auf **[!UICONTROL OK]**.

1. Klicken Sie in der Symbolleiste Ihres neuen Pakets auf **[!UICONTROL Bearbeiten]**.

1. Öffnen Sie die Registerkarte **[!UICONTROL Filter]**.

1. Wählen Sie **[!UICONTROL Filter hinzufügen]** und geben Sie den Pfad zum *Design* Ihres Workflow-Modells ein:

   `/conf/global/settings/workflow/models/<*your-model-name*>`

   Klicken Sie auf **[!UICONTROL Fertig]**.

1. Auswählen **[!UICONTROL Filter hinzufügen]** und geben Sie den Pfad Ihrer *runtime* Workflow-Modell:

   `/var/workflow/models/<*your-model-name*>`

   Klicken Sie auf **[!UICONTROL Fertig]**.

1. Fügen Sie zusätzliche Filter für benutzerdefinierte Skripte hinzu, die von Ihrem Modell verwendet werden.
1. Klicken **[!UICONTROL Speichern]** um Ihre Filterdefinitionen zu bestätigen.
1. Auswählen **[!UICONTROL Build]** in der Symbolleiste Ihrer Package-Definition.
1. Auswählen **[!UICONTROL Download]** aus der Paketsymbolleiste.

## Verwenden von Workflows zur Verarbeitung von Formularübermittlungen {#using-workflows-to-process-form-submissions}

Sie können ein Formular konfigurieren, das vom ausgewählten Workflow verarbeitet werden soll. Wenn Benutzer das Formular übermitteln, wird eine neue Workflow-Instanz mit den Daten der Formularübermittlung als Payload erstellt.

So konfigurieren Sie den Workflow für Ihr Formular:

1. Erstellen Sie eine neue Seite und öffnen Sie sie zur Bearbeitung.
1. Hinzufügen einer **[!UICONTROL Formular]** -Komponente auf der Seite.
1. Konfigurieren Sie die **[!UICONTROL Formularstart]** -Komponente, die auf der Seite angezeigt wurde.
1. Wählen Sie mithilfe von **[!UICONTROL Workflow starten]** den gewünschten Workflow aus den verfügbaren Optionen aus:

   ![wf-12](assets/wf-12.png)

1. Bestätigen Sie die neue Formularkonfiguration mit dem Häkchen.

## Testen von Workflows {#testing-workflows}

Beim Testen eines Workflows ist es sinnvoll, verschiedene Payload-Typen zu verwenden, auch solche, die sich von denen unterscheiden, für die der Workflow entwickelt wurde. Wenn Sie beispielsweise möchten, dass Ihr Workflow für die Verwendung mit Assets ausgelegt ist, testen Sie ihn, indem Sie eine Seite als Payload festlegen und sicherstellen, dass keine Fehler auftreten.

Testen Sie Ihren neuen Workflow beispielsweise wie folgt:

1. [Starten Sie Ihr Workflow-Modell](/help/sites-administering/workflows-starting.md) über die Konsole.
1. Definieren Sie die **[!UICONTROL Payload]** und bestätigen Ihre Eingaben.

1. Nehmen Sie die erforderlichen Schritte vor, damit der Workflow fortgesetzt wird.
1. Überwachen Sie die Protokolldateien während der Ausführung des Workflows.

Sie können auch AEM für die Anzeige konfigurieren **[!UICONTROL DEBUG]** Meldungen in den Protokolldateien. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md). Wenn die Entwicklung abgeschlossen ist, legen Sie die Einstellung für die **[!UICONTROL Protokollebene]** wieder auf **[!UICONTROL Informationen]** fest.

## Beispiele {#examples}

### Beispiel: Erstellen eines (einfachen) Workflows zum Akzeptieren oder Ablehnen einer Veröffentlichungsanforderung {#example-creating-a-simple-workflow-to-accept-or-reject-a-request-for-publication}

Um einige der Möglichkeiten zur Erstellung eines Workflows zu veranschaulichen, wird im folgenden Beispiel eine Variante des Workflows `Publish Example` erstellt.

1. [Erstellen Sie ein neues Workflow-Modell](#creating-a-new-workflow).

   Der neue Workflow enthält:

   * **[!UICONTROL Prozessstart]**
   * `Step 1`
   * **[!UICONTROL Prozessende]**

1. Löschen Sie `Step 1` (da es sich um den falschen Schritttyp für dieses Beispiel handelt):

   * Klicken Sie auf den Schritt und klicken Sie in der Komponenten-Symbolleiste auf **[!UICONTROL Löschen]**. Bestätigen Sie die Aktion.

1. Aus dem **[!UICONTROL Workflow]** Auswahl des Schrittbrowsers, Ziehen Sie eine **[!UICONTROL Teilnehmer-Schritt]** auf den Workflow zu platzieren und zwischen **[!UICONTROL Flussstart]** und **[!UICONTROL Flussende*]*.
1. So öffnen Sie das Dialogfeld &quot;Eigenschaften&quot;:

   * Klicken Sie auf den Teilnehmer-Schritt und klicken Sie in der Komponenten-Symbolleiste auf **[!UICONTROL Konfigurieren]**.
   * Doppelklicken Sie auf den Teilnehmer-Schritt.

1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** `Validate Content` als **[!UICONTROL Titel]** und **[!UICONTROL Beschreibung]** ein.
1. Öffnen Sie die **[!UICONTROL Benutzer/Gruppe]** tab:

   * Aktivieren **[!UICONTROL Benutzer per E-Mail benachrichtigen]**.
   * Wählen Sie für das Feld **[!UICONTROL Benutzer/Gruppe]** die Option `Administrator` (`admin`) aus.

   >[!NOTE]
   >
   >Für zu sendende E-Mails: [die E-Mail-Dienst- und Benutzerkontodetails müssen konfiguriert werden](/help/sites-administering/notification.md).

1. Bestätigen Sie die Änderungen durch Klicken auf das Häkchen-Symbol.

   Daraufhin wird wieder die Übersicht über das Workflow-Modell angezeigt. Der Teilnehmer-Schritt ist nun in `Validate Content` umbenannt.

1. Ziehen Sie eine **[!UICONTROL ODER-Teilung]** auf den Workflow und positionieren Sie sie zwischen `Validate Content` und **[!UICONTROL Fluss-Ende]**.
1. Öffnen Sie die **[!UICONTROL Oder Aufspaltung]** für die Konfiguration.
1. Konfigurieren:

   * **[!UICONTROL Häufig]**: select **[!UICONTROL 2 Verzweigungen]**
   * **[!UICONTROL Verzweigung 1]**: select **[!UICONTROL Standardroute]**.
   * **[!UICONTROL Zweig 2]**: sicherstellen **[!UICONTROL Standardroute]** nicht ausgewählt ist.

1. Bestätigen Sie die Änderungen an der **[!UICONTROL ODER-Teilung]**.
1. Ziehen Sie eine **[!UICONTROL Teilnehmer-Schritt]** Öffnen Sie in der linken Verzweigung die Eigenschaften, geben Sie die folgenden Werte an und bestätigen Sie dann die Änderungen:

   * **[!UICONTROL Titel]**: `Reject Publish Request`
   * **[!UICONTROL Benutzer/Gruppe]**: z. B. `projects-administrators`
   * **[!UICONTROL Benachrichtigen des Benutzers per E-Mail]**: Aktivieren Sie dieses Kontrollkästchen, damit die Benutzer per E-Mail benachrichtigt werden.

1. Ziehen Sie einen **[!UICONTROL Prozessschritt]** auf den rechten Zweig, öffnen Sie die Eigenschaften, geben Sie die folgenden Werte an und bestätigen Sie die Änderungen:

   * **[!UICONTROL Titel]**: `Publish Page as Requested`
   * **[!UICONTROL Prozess]**: Wählen Sie `Activate Page` aus. Durch diesen Prozess wird die ausgewählte Seite in den Publisher-Instanzen veröffentlicht.

1. Klicken **[!UICONTROL Synchronisieren]** (Editor-Symbolleiste), um das Laufzeitmodell zu generieren.

   Siehe [Workflow synchronisieren](#sync-your-workflow-generate-a-runtime-model) für Details.

   Ihr neues Workflow-Modell sieht wie folgt aus:

   ![wf-13](assets/wf-13.png)

1. Wenden Sie diesen Workflow auf Ihre Seite an, sodass Benutzer, die zur Phase **[!UICONTROL Fertig stellen]** übergehen, den Schritt **[!UICONTROL Inhalt überprüfen]** auswählen können, egal ob sie die **[!UICONTROL Seite wie angefordert veröffentlichen]** oder die **[!UICONTROL Anfrage zur Veröffentlichung ablehnen]** möchten.

   ![chlimage_1-182](assets/chlimage_1-182.png)

### Beispiel: Definieren einer Regel für eine ODER-Teilung     {#example-defining-a-rule-for-an-or-split}

**[!UICONTROL ODER-Teilung]** -Schritte ermöglichen es Ihnen, bedingte Verarbeitungspfade in Ihren Workflow einzufügen.

So definieren Sie eine ODER-Regel:

1. Erstellen Sie zwei Skripte und speichern Sie sie im Repository, z. B. unter:

   `/apps/myapp/workflow/scripts`

   >[!NOTE]
   >
   >Die Skripte müssen eine [Funktion `check()`](#function-check) aufweisen, die einen booleschen Wert zurückgibt.

1. Bearbeiten Sie den Workflow und fügen Sie die **[!UICONTROL ODER-Teilung]** zum Modell.
1. Eigenschaften von bearbeiten **[!UICONTROL Verzweigung 1]** des **[!UICONTROL ODER-Teilung]**:

   * Definieren Sie dies als **[!UICONTROL Standardroute]**, indem Sie den **[!UICONTROL Wert]** auf `true` festlegen.
   * Geben Sie für **[!UICONTROL Regel]** den Pfad zum Skript an. Beispiel:

      `/apps/myapp/workflow/scripts/myscript1.ecma`
   >[!NOTE]
   >
   >Sie können die Reihenfolge der Verzweigungen ändern, sofern dies erforderlich ist.

1. Bearbeiten Sie die Eigenschaften von **[!UICONTROL Zweig 2]** der **[!UICONTROL ODER-Teilung]**:

   * Geben Sie für **[!UICONTROL Regel]** den Pfad zum anderen Skript an. Beispiel:

      `/apps/myapp/workflow/scripts/myscript2.ecma`

1. Legen Sie die Eigenschaften der einzelnen Schritte in jedem Zweig fest. Stellen Sie sicher, dass die Einstellung für **[!UICONTROL Benutzer/Gruppe]** festlegt ist.
1. Klicken **Synchronisieren** (Editor-Symbolleiste), um Ihre Änderungen am Laufzeitmodell beizubehalten.

   Siehe [Workflow synchronisieren](#sync-your-workflow-generate-a-runtime-model) für Details.

#### Funktionsprüfung() {#function-check}

>[!NOTE]
>
>Siehe [Verwenden von ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript).

Das folgende Beispielskript gibt `true` zurück, wenn es sich bei dem Knoten um einen `JCR_PATH` unter `/content/we-retail/us/en` handelt:

```
function check() {
    if (workflowData.getPayloadType() == "JCR_PATH") {
      var path = workflowData.getPayload().toString();
      var node = jcrSession.getItem(path);

      if (node.getPath().indexOf("/content/we-retail/us/en") >= 0) {
       return true;
      } else {
       return false;
      } 
     } else {
      return false;
     }
}
```

### Beispiel: Benutzerdefinierte Aktivierungsanfrage {#example-customized-request-for-activation}

Sie können jeden vordefinierten Workflow anpassen. Um ein benutzerdefiniertes Verhalten zu erhalten, überlagern Sie Details des entsprechenden Workflows.

Beispiel: **[!UICONTROL Aktivierungsanfrage]**. Dieser Workflow wird zum Veröffentlichen von Seiten in **[!UICONTROL Sites]** und wird automatisch ausgelöst, wenn ein Inhaltsautor nicht über die entsprechenden Replikationsrechte verfügt. Weitere Informationen finden Sie unter [Anpassen der Seitenbearbeitung – Anpassen des Workflows „Aktivierungsanfrage“](/help/sites-developing/customizing-page-authoring-touch.md#customizing-the-request-for-activation-workflow).
