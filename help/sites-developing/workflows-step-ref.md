---
title: Referenz für Workflow-Schritte
seo-title: Referenz für Workflow-Schritte
description: 'null'
seo-description: 'null'
uuid: 72a64495-d1b1-49e7-8257-d6b2ed36961c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 25f0e0f7-9570-4748-81cb-ccec6492c0b4
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '2833'
ht-degree: 72%

---


# Referenz für Workflow-Schritte{#workflow-step-reference}

Workflow-Modelle beinhalten eine Reihe von Schritten unterschiedlichen Typs. Je nach Typ können diese Schritte mit Parametern und Skripten konfiguriert und erweitert werden, um die gewünschten Funktionen und Steuerungsoptionen bereitzustellen.

>[!NOTE]
>
>In diesem Abschnitt werden die standardmäßigen Workflow-Schritte behandelt.
>
>Informationen zu Schritten für spezifische Module finden Sie unter:
>
>* [Referenz für Workflow-Schritte in AEM Forms](/help/forms/using/aem-forms-workflow-step-reference.md)
>* [Verarbeitung von Assets mithilfe von Medien-Handlern und Workflows](/help/assets/media-handlers.md)

>



## Schritt-Eigenschaften {#step-properties}

Each step component has a **[!UICONTROL Step Properties]** dialog that lets you define and edit the required properties.

### Schritt-Eigenschaften – Registerkarte „Allgemein“{#step-properties-common-tab}

Eine Kombination der folgenden Eigenschaften ist für die meisten Workflow-Schrittkomponenten im Eigenschaften-Dialogfeld auf der Registerkarte **[!UICONTROL Allgemein]** verfügbar:

* **[!UICONTROL Titel]**

   Der Titel des Schritts.

* **[!UICONTROL Beschreibung]**

   Eine Beschreibung des Schritts.

* **[!UICONTROL Workflow-Status]**

   Eine Dropdown-Auswahl, um eine [Phase](/help/sites-developing/workflows.md#workflow-stages) auf den Schritt anzuwenden.

* **[!UICONTROL Zeitüberschreitung]**

   Der Zeitraum, nach dem der Schritt mit der Zeitüberschreitung abgeschlossen wird.

   You can select between: **[!UICONTROL Off]**, **[!UICONTROL Immediate]**, **[!UICONTROL 1h]**, **[!UICONTROL 6h]**, **[!UICONTROL 12h]**, **[!UICONTROL 24h]**.

* **[!UICONTROL Zeitüberschreitungs-Handler]**

   Der Handler, der den Workflow steuert, wenn der Schritt beendet wird; Beispiel:

   `Auto Advancer`

* **[!UICONTROL Handler-Modus]**

   Wählen Sie diese Option, um den Workflow automatisch zum nächsten Schritt nach der Ausführung zu verschieben. Wenn diese Option nicht ausgewählt ist, muss das Implementierungsskript den Workflow weiterleiten.

#### Schritt-Eigenschaften – Registerkarte „Benutzer/Gruppe“{#step-properties-user-group-tab}

Die folgenden Eigenschaften sind für viele Workflow-Schrittkomponenten im Eigenschaften-Dialogfeld auf der Registerkarte **[!UICONTROL Benutzer/Gruppe]** verfügbar:

* **[!UICONTROL Benachrichtigen Sie den Benutzer per E-Mail]**

   * Sie können Teilnehmer benachrichtigen, indem Sie eine E-Mail senden, sobald der Workflow einen Schritt erreicht hat.
   * Wenn diese Option aktiviert ist, wird eine E-Mail an den mit der Eigenschaft **[!UICONTROL Benutzer/Gruppe]** definierten Benutzer oder an alle Mitglieder einer Gruppe (falls definiert) gesendet.

* **[!UICONTROL Benutzer/Gruppe]**

   * Sie können einen Benutzer oder eine Gruppe aus einem Dropdown-Menü auswählen.
   * Falls Sie den Schritt einem bestimmten Benutzer zuweisen, kann nur dieser Benutzer Aktionen für den Schritt durchführen.
   * If you assign the step to an entire group, then when the workflow reaches this step all users in this group will have the action in their **[!UICONTROL Workflow Inbox]**.
   * Weitere Informationen finden Sie unter [Teilnehmen an Workflows](/help/sites-authoring/workflows-participating.md).

## UND-Teilung {#and-split}

The **[!UICONTROL AND Split]** creates a split in the workflow, after which both branches will be active. Sie fügen jeder Verzweigung nach Bedarf Workflow-Schritte hinzu. Mit diesem Schritt können Sie mehrere Prozesspfade in einem Workflow einrichten. Sie können z. B. mehrere Bewertungsschritte parallel zulassen, sodass Sie Zeit sparen.

![wf-26](assets/wf-26.png)

### UND-Teilung – Konfiguration {#and-split-configuration}

* Edit the **[!UICONTROL AND Split]** properties:

   * **[!UICONTROL Teilungsname]**: einen Namen für erläuternde Zwecke zuweisen.
   * Wählen Sie die Anzahl der erforderlichen Verzweigungen aus: 2, 3, 4 oder 5.

* Fügen Sie bei Bedarf Workflow-Schritte zu den Verzweigungen hinzu.

   ![wf-27](assets/wf-27.png)

## Container-Schritt {#container-step}

A **[!UICONTROL Container]** step starts another workflow model that runs as a child workflow.

This **[!UICONTROL Container]]**lets you reuse workflow models to implement common sequences of steps. Beispielsweise kann ein Übersetzungs-Workflow-Modell in mehreren Bearbeitungs-Workflows verwendet werden.

![wf-28](assets/wf-28.png)

### Container-Schritt – Konfiguration {#container-step-configuration}

Verwenden und bearbeiten Sie die folgenden Registerkarten, um den Schritt zu konfigurieren:

* [**[!UICONTROL Allgemein]**](#step-properties-common-tab)
* **[!UICONTROL Container]**

   * **[!UICONTROL Untergeordneter Workflow]**: Wählen Sie den zu startenden Workflow aus.

## Zum Schritt wechseln {#goto-step}

Mit der Option **[!UICONTROL Zum Schritt wechseln]** können Sie den nächsten auszuführenden Schritt im Workflow-Modell angeben, je nach Ergebnis des ECMA-Skripts:

* `true`: **[!UICONTROL Zum Schritt wechseln]** wird abgeschlossen und das Workflow-Modul führt den angegebenen Schritt aus.

* `false`: **[!UICONTROL Zum Schritt wechseln]** wird abgeschlossen und der nächste auszuführende Schritt wird von der normalen Routinglogik bestimmt.

Mit **[!UICONTROL Zum Schritt wechseln]** können Sie erweiterte Routingstrukturen im Workflow-Modell implementieren. For example, to implement a loop, the **[!UICONTROL Goto Step]** can be defined to execute a prior step in the workflow, with the script evaluating a loop condition.

### Zum Schritt wechseln – Konfiguration {#goto-step-configuration}

Verwenden und bearbeiten Sie die folgenden Registerkarten, um den Schritt zu konfigurieren:

* [**[!UICONTROL Allgemein]**](#step-properties-common-tab)
* **[!UICONTROL Prozess]**

   * **[!UICONTROL Der zu]folgende Schritt **: Wählen Sie den auszuführenden Schritt aus.
   * **[!UICONTROL Skriptpfad]**: Der Pfad zum ECMAScript, der bestimmt, ob der **[!UICONTROL Goto-Schritt]** ausgeführt werden soll.
   * **[!UICONTROL Skript]**: Das ECMAScript, das bestimmt, ob der **[!UICONTROL Goto-Schritt]** ausgeführt werden soll.

>[!CAUTION]
>
>Geben Sie entweder den **[!UICONTROL Skriptpfad]** oder das **[!UICONTROL Skript]** an. Die beiden Optionen können nicht gleichzeitig verwendet werden. Wenn Sie für beide Eigenschaften Werte angeben, verwendet der Schritt die Option **[!UICONTROL Skriptpfad]**.

#### Simulieren einer for-Schleife {#simulating-a-for-loop}

Um eine for-Schleife zu simulieren, müssen Sie die Zahl der erfolgten Schleifeniterationen überwachen:

* Die Zahl steht in der Regel für einen Index der Elemente, für die im Workflow Aktionen erfolgen.
* Die Zahl wird als Beendigungskriterium der Schleife ausgewertet.

Um beispielsweise einen Workflow zu implementieren, der eine Aktion für mehrere JCR-Knoten durchführt, können Sie eine Schleifenzahl als Index für die Knoten verwenden. To persist the count, store an `integer` value in the data map of the workflow instance. Verwenden Sie das Skript für **[!UICONTROL Zum Schritt wechseln]**, um die Zahl zu erhöhen und mit den Beendigungskriterien zu vergleichen.

```
function check(){
   var count=0;
   var keyname="loopcount"
   try{
      if (workflowData.getMetaDataMap().containsKey(keyname)){ 
        log.info("goto script: found loopcount key");
        count= parseInt(workflowData.getMetaDataMap().get(keyname))+1;
      } 
 
     workflowData.getMetaDataMap().put(keyname,count);
 
     }catch(err) {
         log.info(err.message);
         return false;
    }
   if (parseInt(count) <7){
       return true;
   } else {
      return false;
   }
}
```

## ODER-Teilung {#or-split}

Mit der **[!UICONTROL ODER-Teilung]** wird der Workflow so geteilt, dass nur eine Verzweigung aktiv bleibt. Mit diesem Schritt können Sie bedingte Prozesspfade in einem Workflow einrichten. Sie fügen jeder Verzweigung nach Bedarf Workflow-Schritte hinzu.

>[!NOTE]
>
>Weitere Informationen zum Erstellen einer ODER-Teilung finden Sie unter [https://helpx.adobe.com/experience-manager/using/aem64_workflow_servlet.html](https://helpx.adobe.com/experience-manager/using/aem64_workflow_servlet.html)

![wf-29](assets/wf-29.png)

### ODER-Teilung – Konfiguration {#or-split-configuration}

* Edit the **[!UICONTROL OR Split]** properties:

   * **[!UICONTROL Allgemein]**

      * Wählen Sie die Anzahl der erforderlichen Verzweigungen aus: 2, 3, 4 oder 5.
   * **[!UICONTROL Zweig:*x*>]**

      * **[!UICONTROL Skriptpfad]**: Der Pfad zu einer Datei, die das Skript enthält.
      * **[!UICONTROL Skript]**: Fügen Sie das Skript im Feld hinzu.
      * **[!UICONTROL Standardroute]**: Die Standardverzweigung wird verwendet, wenn mehrere Verzweigungen als „true“ ausgewertet werden. Sie können nur eine Verzweigung als Standard festlegen.

   >[!NOTE]
   >
   >Es gibt eine separate Registerkarte für jede Verzweigung:
   >
   >* Das Skript jeder Verzweigung wird einzeln ausgewertet.
   >* Die Verzweigungen werden von links nach rechts ausgewertet.
   >* Das erste Skript, das &quot;true&quot;ergibt, wird ausgeführt.
   >* Wenn keine Verzweigung &quot;true&quot;ergibt, wird der Workflow nicht weitergeleitet.


   >[!CAUTION]
   >
   >Geben Sie entweder den **[!UICONTROL Skriptpfad]** oder das **[!UICONTROL Skript]** an. Die beiden Optionen können nicht gleichzeitig verwendet werden. Wenn Sie für beide Eigenschaften Werte angeben, verwendet der Schritt die Option **[!UICONTROL Skriptpfad]**.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Definieren einer Regel für eine ODER-Teilung](/help/sites-developing/workflows-models.md#example-defining-a-rule-for-an-or-split).

* Fügen Sie bei Bedarf Workflow-Schritte zu den Verzweigungen hinzu.

## Teilnehmer-Schritte und -Auswahl {#participant-steps-and-choosers}

### Teilnehmer-Schritt {#participant-step}

Mit der Option **[!UICONTROL Teilnehmer-Schritt]** können Sie einer bestimmten Aktion Eigentümerrechte zuweisen. Der Workflow wird nur fortgesetzt, wenn der Benutzer diesen Schritt manuell bestätigt hat. Die Option wird verwendet, wenn Sie einer Person eine Aktion in einem Workflow zuweisen möchten, z. B. einen Bewertungsschritt.

Obwohl sie nicht direkt damit im Zusammenhang steht, muss die Benutzerautorisierung beim Zuweisen einer Aktion berücksichtigt werden. Der Benutzer muss Zugriff auf die Seite mit der Workflow-Nutzlast haben.

#### Teilnehmer-Schritt – Konfiguration {#participant-step-configuration}

Verwenden und bearbeiten Sie die folgenden Registerkarten, um den Schritt zu konfigurieren:

* [**[!UICONTROL Allgemein]**](#step-properties-common-tab)
* [**[!UICONTROL Benutzer/Gruppe]**](#step-properties-user-group-tab)

>[!NOTE]
>
>Der Workflow-Initiator wird immer benachrichtigt, wenn:
>
>* der Workflow abgeschlossen (beendet) wurde.
>* der Workflow abgebrochen (beendet) wurde.

>



>[!NOTE]
>
>Einige Eigenschaften müssen konfiguriert werden, um E-Mail-Benachrichtigungen zu aktivieren. Sie können die E-Mail-Vorlage auch anpassen oder eine E-Mail-Vorlage für eine neue Sprache hinzufügen. See [Configuring Email Notification](/help/sites-administering/notification.md) to configure email notifications in AEM.

### Dialogfeld „Teilnehmer-Schritt“{#dialog-participant-step}

Verwenden Sie ein Dialogfeld **[!UICONTROL Teilnehmer-Schritt]**, um Daten des Benutzers zu erfassen, dem das Arbeitselement zugewiesen wird. Dieser Schritt eignet sich für das Erfassen kleiner Datenmengen, die später im Workflow verwendet werden.

Nach Abschluss des Schritts enthält das Dialogfeld **[!UICONTROL Arbeits-Element fertig stellen]** die Felder, die Sie für dieses Dialogfeld definiert haben. Die in den Feldern erfassten Daten werden in den Knoten der Workflow-Nutzlast gespeichert. Nachfolgende Workflow-Schritte können die Werte aus dem Repository auslesen.

Um den Schritt zu konfigurieren, geben Sie die Gruppe oder den Benutzer, der bzw. dem das Arbeitselement zugewiesen werden soll, sowie den Pfad zum Dialogfeld an.

#### Dialogfeld „Teilnehmer-Schritt“ – Konfiguration {#dialog-participant-step-configuration}

Verwenden und bearbeiten Sie die folgenden Registerkarten, um den Schritt zu konfigurieren:

* [**[!UICONTROL Allgemein]**](#step-properties-common-tab)
* [**[!UICONTROL Benutzer/Gruppe]**](#step-properties-user-group-tab)
* **[!UICONTROL Dialogfeld]**

   * **[!UICONTROL-Dialogpfad**: Der Pfad zum Knoten &quot;dialog&quot;des von Ihnen erstellten [Dialogfelds](#dialog-participant-step-creating-a-dialog).

#### Dialog Participant Step – Creating a dialog{#dialog-participant-step-creating-a-dialog}

So erstellen Sie ein Dialogfeld:

* Entscheiden Sie, wo die erfassten Daten [in der Nutzlast gespeichert werden](#dialog-participant-step-storing-data-in-the-payload).
* [Definieren des Dialogs; Hierzu gehört auch die Definition der Felder, die zum Erfassen (und Speichern) der Daten](#dialog-participant-step-dialog-definition)verwendet werden.

#### Dialogfeld „Teilnehmer-Schritt“ – Speichern von Daten in der Nutzlast {#dialog-participant-step-storing-data-in-the-payload}

Sie können Widget-Daten in der Workflow-Nutzlast oder in den Metadaten des Arbeitselements speichern. Das Format der `name`-Eigenschaft des Widget-Knotens bestimmt, wo die Daten gespeichert werden.

* **[!UICONTROL Daten mit der Nutzlast speichern]**

   * Um Widget-Daten als Eigenschaft der Workflow-Nutzlast zu speichern, verwenden Sie das folgende Format für den Wert der Eigenschaft name des Widget-Knotens:

      `./jcr:content/nodename`

   * Die Daten werden in der `nodename`-Eigenschaft des Nutzlastknotens gespeichert. Falls der Knoten diese Eigenschaft nicht enthält, wird die Eigenschaft erstellt.
   * Wenn Daten mit der Nutzlast gespeichert werden, wird der Wert der Eigenschaft bei nachfolgender Verwendung des Dialogfelds mit derselben Nutzlast überschrieben.

* **[!UICONTROL Daten mit dem Arbeitselement speichern]**

   * Um Widget-Daten als Eigenschaft der Metadaten des Arbeitselements zu speichern, verwenden Sie das folgende Format für den Wert der name-Eigenschaft:

      `nodename`

   * The data is stored in the `nodename` property of the work item `metadata`. Die Daten werden beibehalten, wenn das Dialogfeld anschließend von derselben Nutzlast verwendet wird.

#### Dialogfeld „Teilnehmer-Schritt“ – Definieren des Dialogfelds {#dialog-participant-step-dialog-definition}

1. **[!UICONTROL Dialogfeldstruktur]**

   Dialogfelder für das Dialogfeld „Teilnehmer-Schritt&quot; ähneln den Dialogfeldern, die Sie für Bearbeitungskomponenten erstellen. Sie werden gespeichert in:

   `/apps/myapp/workflow/dialogs`

   Dialogfelder für die Touch-optimierte Standardbenutzeroberfläche weisen folgende Knotenstruktur auf:

   ```xml
   newComponent (cq:Component)
     |- cq:dialog (nt:unstructured)
       |- content 
         |- layout 
           |- items 
             |- column 
               |- items 
                 |- component0
                 |- component1
                 |- ...
   ```

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Erstellen und Konfigurieren eines Dialogfelds](/help/sites-developing/developing-components.md#creating-and-configuring-a-dialog).

1. **[!UICONTROL Eigenschaft „Dialogpfad“]**

   The **[!UICONTROL Dialog Participant Step]** has the **[!UICONTROL Dialog Path]** property (together with the properties of a [Participant Step](#participant-step)). Der Wert der Eigenschaft **[!UICONTROL Dialogpfad]** entspricht dem Pfad zum Knoten `dialog` im Dialogfeld.

   Das Dialogfeld kann sich beispielsweise in einer Komponente mit dem Namen `EmailWatch` befindet, die im Knoten gespeichert ist:

   `/apps/myapp/workflows/dialogs`

   Für die Touch-optimierte Benutzeroberfläche wird folgender Wert für die Eigenschaft **[!UICONTROL Dialogpfad]** verwendet:

   `/apps/myapp/workflow/dialogs/EmailWatch/cq:dialog`

   ![wf-30](assets/wf-30.png)

1. **Beispiel für eine Dialogfelddefinition**

   Das folgende XML-Code-Snippet steht für ein Dialogfeld, bei dem der `String`-Wert im Knoten `watchEmail` des Nutzlastinhalts gespeichert wird. Der Titelknoten steht für die [TextField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/textfield/index.html)-Komponente:

   ```xml
   jcr:primaryType="nt:unstructured" 
       jcr:title="Watcher Email Address Dialog" 
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout jcr:primaryType="nt:unstructured" 
               margin="false" 
               sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
           />
           <items jcr:primaryType="nt:unstructured">
               <column jcr:primaryType="nt:unstructured"
                   sling:resourceType="granite/ui/components/foundation/container">
                   <items jcr:primaryType="nt:unstructured">
                       <title jcr:primaryType="nt:unstructured" 
                           fieldLabel="Notification Email Address" 
                           name="./jcr:content/watchEmails"
                           sling:resourceType="granite/ui/components/foundation/form/textfield"
                       />
                   </items>
               </column>
           </items>
       </content>
   </cq:dialog>
   ```

   Bei diesem Beispiel sieht das Dialogfeld für eine Touch-optimierte Benutzeroberfläche wie folgt aus:

   ![chlimage_1-177](assets/chlimage_1-177.png)

### Dynamischer Teilnehmer – Schritt {#dynamic-participant-step}

Die Komponente **[!UICONTROL Dynamischer Teilnehmer – Schritt]** ähnelt der Komponente **[!UICONTROL Teilnehmer – Schritt]**, allerdings wird der Teilnehmer automatisch während der Laufzeit ausgewählt.

Um diesen Schritt zu konfigurieren, wählen Sie eine **[!UICONTROL Teilnehmerauswahl]** zum Identifizieren des Teilnehmers, dem das Arbeitselement zugewiesen werden soll, und ein Dialogfeld aus.

#### Dynamischer Teilnehmer – Schritt – Konfiguration {#dynamic-participant-step-configuration}

Verwenden und bearbeiten Sie die folgenden Registerkarten, um den Schritt zu konfigurieren:

* [**[!UICONTROL Allgemein]**](#step-properties-common-tab)
* **[!UICONTROL Teilnehmer-Auswähler]**

   * **[!UICONTROL Teilnehmer-Auswähler]**: der Name der [Teilnehmerauswahl, den Sie erstellen](#dynamic-participant-step-developing-the-participant-chooser).
   * **[!UICONTROL Argumente]**: Alle erforderlichen Argumente.
   * **[!UICONTROL E-Mail]**: Legt fest, ob eine E-Mail-Benachrichtigung an den Benutzer gesendet werden soll.

* **[!UICONTROL Dialogfeld]**

   * **[!UICONTROL Dialogpfad]**: Der Pfad zum Dialogfeldknoten des [Dialogfelds, das Sie erstellen (wie beim **Dialogfeld „Teilnehmer-Schritt“**)](#dialog-participant-step-creating-a-dialog).

#### Dynamischer Teilnehmer – Schritt – Entwickeln der Teilnehmerauswahl {#dynamic-participant-step-developing-the-participant-chooser}

Sie erstellen die Teilnehmerauswahl. Dabei können Sie beliebige Logik oder Kriterien für die Auswahl verwenden. Beispielsweise kann die Teilnehmerauswahl den Benutzer (innerhalb einer Gruppe) auswählen, dem die wenigsten Arbeitselemente zugewiesen sind. You can create any number of participant choosers to use with different instances of the **Dynamic Participant Step *]*component in your workflow models.

Erstellen Sie einen OSGi-Dienst oder ein ECMA-Skript zum Auswählen eines Benutzers, dem das Arbeitselement zugewiesen werden soll.

* **[!UICONTROL ECMA-Skript]**

   Skripte müssen eine getParticipant-Funktion enthalten, mit der eine Benutzer-ID als `String`-Wert zurückgegeben wird. Store your custom scripts in, for example, the `/apps/myapp/workflow/scripts` folder, or a subfolder.

   Ein Beispielskript ist in einer Standard-AEM-Instanz enthalten:

   `/libs/workflow/scripts/initiator-participant-chooser.ecma`

   >[!CAUTION]
   >
   >Sie dürfen *keinerlei* Änderungen im Pfad `/libs` vornehmen.
   >
   >
   >This is because the content of `/libs` is overwritten the next time you upgrade your instance (and may be overwritten when you apply either a hotfix or feature pack).

   Mit diesem Skript wird der Workflow-Initiator als Teilnehmer ausgewählt:

   ```
   function getParticipant() {
       return workItem.getWorkflow().getInitiator();
   }
   ```

   >[!NOTE]
   >
   >The **[!UICONTROL Workflow Initiator Participant Chooser]** component extends the **[!UICONTROL Dynamic Participant Step]** and uses this script as the step implementation.

* **[!UICONTROL OSGi-Dienst]**

   Services must implement the [com.day.cq.workflow.exec.ParticipantStepChooser](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/ParticipantStepChooser.html) interface. Die Schnittstelle definiert die folgenden Mitglieder:

   * `SERVICE_PROPERTY_LABEL` Feld: Verwenden Sie dieses Feld, um den Namen der Teilnehmerauswahl anzugeben. Der Name wird in einer Liste der verfügbaren Teilnehmerauswahlen in den Eigenschaften **[!UICONTROL Dynamischer Teilnehmer – Schritt]** angezeigt.
   * `getParticipant` Methode: Gibt die dynamisch aufgelöste Principal-ID als `String` Wert zurück.

   >[!CAUTION]
   >
   >The `getParticipant` method returns the dynamically resolved Principal id. Dies kann entweder eine Gruppen-ID oder eine Benutzer-ID sein.
   >
   >
   >Eine Gruppen-ID kann jedoch nur für eine Komponente **[!UICONTROL Teilnehmer-Schritt]** verwendet werden, wenn eine Liste der Teilnehmer zurückgegeben wird. For a **[!UICONTROL Dynamic Participant Step]** an empty list is returned and this cannot be used for delegation.

   Um die Implementierung für Komponenten **[!UICONTROL Dynamischer Teilnehmer – Schritt]** verfügbar zu machen, fügen Sie die Java-Klasse zum OSGi-Bundle hinzu, das den Dienst exportiert, und stellen Sie das Bundle auf dem AEM-Server bereit.

   >[!NOTE]
   >
   >Die **[!UICONTROL zufallsbasierte Teilnehmerauswahl]** ist ein Sampling-Dienst, der willkürlich einen Benutzer auswählt ( `com.day.cq.workflow.impl.process.RandomParticipantChooser`). The **[!UICONTROL Random Participant Chooser]** step component sample extends the **[!UICONTROL Dynamic Participant Step]** and uses this service as the step implementation.

#### Dynamischer Teilnehmer – Schritt – Beispiel für Teilnehmerauswahldienst {#dynamic-participant-step-example-participant-chooser-service}

Die folgende Java-Klasse implementiert die `ParticipantStepChooser`-Oberfläche. Die Klasse gibt den Namen des Teilnehmers zurück, der den Workflow initiiert hat. The code uses the same logic that the sample script ( `initator-participant-chooser.ecma`) uses.

Die `@Property` Anmerkung setzt den Wert des `SERVICE_PROPERTY_LABEL` Felds auf `Workflow Initiator Participant Chooser`.

```java
package com.adobe.example;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.osgi.framework.Constants;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.adobe.granite.workflow.WorkflowException;
import com.adobe.granite.workflow.WorkflowSession;
import com.adobe.granite.workflow.exec.ParticipantStepChooser;
import com.adobe.granite.workflow.exec.WorkItem;
import com.adobe.granite.workflow.metadata.MetaDataMap;

@Component
@Service
@Properties({
        @Property(name = Constants.SERVICE_DESCRIPTION, value = "An example implementation of a dynamic participant chooser."),
        @Property(name = ParticipantStepChooser.SERVICE_PROPERTY_LABEL, value = "Workflow Initiator Participant Chooser (service)") })
public class InitiatorParticipantChooser implements ParticipantStepChooser {

 private Logger logger = LoggerFactory.getLogger(this.getClass());

 public String getParticipant(WorkItem arg0, WorkflowSession arg1,
   MetaDataMap arg2) throws WorkflowException {

  String initiator = arg0.getWorkflow().getInitiator();
  logger.info("Assigning Dynamic Participant Step work item to {}",initiator);

  return initiator;
 }
}
```

In the **[!UICONTROL Dynamic Participant Step]** properties dialog, the **[!UICONTROL Participant Chooser]** list includes the item `Workflow Initiator Participant Chooser (script)`, which represents this service.

``Wenn das Workflow-Modell gestartet wird, wird in der Protokolldatei die ID des Benutzers angegeben, der den Workflow initiiert hat und dem das Arbeitselement zugewiesen ist. In diesem Beispiel hat der Benutzer `admin` den Workflow gestartet.

`13.09.2015 15:48:53.037 *INFO* [10.176.129.223 [1347565733037] POST /etc/workflow/instances HTTP/1.1] com.adobe.example.InitiatorParticipantChooser Assigning Dynamic Participant Step work item to admin`

### Formular „Teilnehmer – Schritt“{#form-participant-step}

**[!UICONTROL Formular „Teilnehmer – Schritt“]** zeigt beim Öffnen des Arbeitselements ein Formular an. Wenn der Benutzer das Formular ausfüllt und absendet, werden die Daten in den Knoten der Workflow-Nutzlast gespeichert.

Um diesen Schritt zu konfigurieren, geben Sie die Gruppe oder den Benutzer, der/dem das Arbeitselement zugewiesen werden soll, und den Pfad zum Formular an.

>[!CAUTION]
>
>This section deals with the [Forms section of Foundation Components for Page Authoring](/help/sites-authoring/default-components-foundation.md#form).

#### Formular „Teilnehmer – Schritt“ – Konfiguration {#form-participant-step-configuration}

Verwenden und bearbeiten Sie die folgenden Registerkarten, um den Schritt zu konfigurieren:

* [**[!UICONTROL Allgemein]**](#step-properties-common-tab)
* [**[!UICONTROL Benutzer/Gruppe]**](#step-properties-user-group-tab)
* **[!UICONTROL Formular]**

   * **[!UICONTROL-Formularpfad**: Der Pfad zum erstellten [Formular](#form-participant-step-creating-the-form).

#### Formular „Teilnehmer – Schritt“ - Erstellen des Formulars {#form-participant-step-creating-the-form}

Erstellen Sie wie gewohnt ein Formular mit einem **[!UICONTROL Formular „Teilnehmer – Schritt“]**. Formulare für Formular „Teilnehmer – Schritt“ müssen wie folgt konfiguriert werden:

* Für den **[!UICONTROL Beginn der Formularkomponente]** muss die **[!UICONTROL Eigenschaft Aktionstyp]** auf `Edit Workflow Controlled Resource(s)`eingestellt sein.

* The **[!UICONTROL Start of Form]** component must have a value for the `Form Identifier` property.

* Für die Formularkomponenten muss die Eigenschaft **Elementname** auf den Pfad des Knotens verweisen, in dem die Felddaten gespeichert werden. Der Pfad muss auf einen Knoten im Nutzlastinhalt des Workflows verweisen. Der Wert verwendet das folgende Format:

   `./jcr:content/path_to_node`

* The form must include a **[!UICONTROL Workflow Submit Button(s)]** component. Sie konfigurieren keine Eigenschaften für die Komponente.

Die Workflow-Anforderungen bestimmen, wo Felddaten gespeichert werden sollen. Beispielsweise können Felddaten verwendet werden, um die Eigenschaften von Seiteninhalten zu konfigurieren. The following value of an **[!UICONTROL Element Name]** property stores field data as the value of the `redirectTarget` property of the `jcr:content` node:

`./jcr:content/redirectTarget`

Im folgenden Beispiel werden die Felddaten als Inhalt einer **[!UICONTROL Text]**-Komponente auf der Nutzlastseite verwendet:

`./jcr:content/par/text_3/text`

``Das erste Beispiel kann für eine beliebige Seite verwendet werden, die von der `cq:Page`-Komponente gerendert wird. Das zweite Beispiel kann nur verwendet werden, wenn die Nutzlastseite eine ****-Komponente mit der ID `text_3`text_  beinhaltet.

Das Formular kann sich an einer beliebigen Stelle im Repository befinden, Workflow-Benutzer müssen jedoch berechtigt sein, das Formular zu lesen.

### Zufallsbasierte Teilnehmerauswahl {#random-participant-chooser}

Der Schritt **[!UICONTROL Zufallsbasierte Teilnehmerauswahl]** bezieht sich auf eine Teilnehmerauswahl, die das erzeugte Arbeitselement einem willkürlich aus einer Liste ausgewählten Benutzer zuweist.

![wf-31](assets/wf-31.png)

#### Zufallsbasierte Teilnehmerauswahl – Konfiguration {#random-participant-chooser-configuration}

Verwenden und bearbeiten Sie die folgenden Registerkarten, um den Schritt zu konfigurieren:

* [**[!UICONTROL Allgemein]**](#step-properties-common-tab)
* **[!UICONTROL Argumente]**

   * **[!UICONTROL Teilnehmer]**: Gibt die Liste der zur Auswahl stehenden Benutzer an. Um einen Benutzer zur Liste hinzuzufügen, klicken Sie auf **[!UICONTROL Element hinzufügen]** und geben Sie den Stammpfad des Benutzerknotens oder die Benutzer-ID an. Die Reihenfolge der Benutzer hat keine Auswirkungen auf die Wahrscheinlichkeit, mit der diesen ein Arbeitselement zugeordnet wird.

### Workflow-Initiator-Teilnehmerauswahl {#workflow-initiator-participant-chooser}

Der Schritt **[!UICONTROL Workflow-Initiator-Teilnehmerauswahl]** bezieht sich auf eine Teilnehmerauswahl, bei der das erzeugte Arbeitselement dem Benutzer zugewiesen wird, der den Workflow gestartet hat. Bei diesem Schritt muss nur die Eigenschaft **[!UICONTROL Allgemein]** konfiguriert werden.

#### Workflow-Initiator-Teilnehmerauswahl – Konfiguration {#workflow-initiator-participant-chooser-configuration}

Um diesen Schritt zu konfigurieren, bearbeiten Sie die folgenden Registerkarten:

* [**[!UICONTROL Allgemein]**](#step-properties-common-tab)

## Prozessschritt {#process-step}

A **[!UICONTROL Process Step]** runs an ECMAScript or calls an OSGi service to perform automatic processing.

![wf-32](assets/wf-32.png)

### Prozessschritt – Konfiguration {#process-step-configuration}

Verwenden und bearbeiten Sie die folgenden Registerkarten, um den Schritt zu konfigurieren:

* [**[!UICONTROL Allgemein]**](#step-properties-common-tab)
* **[!UICONTROL Prozess]**

   * **[!UICONTROL Prozess]**: Die Implementierung des Prozesses, die durchgeführt werden soll. Wählen Sie im Dropdown-Menü den Dienst ECMAScript oder OSGi aus. Informationen:

      * zu den standardmäßigen ECMA-Skripten und OSGi-Diensten finden Sie unter [Integrierte Prozesse für Prozessschritte](/help/sites-developing/workflows-process-ref.md).
      * Creating ECMAScripts for a **[!UICONTROL Process]** step, see [Implementing a Process Step with an ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript).
      * Creating OSGi services for a **[!UICONTROL Process]** step, see [Implementing a Process Step with a Java Class](/help/sites-developing/workflows-customizing-extending.md#implementing-a-process-step-with-a-java-class).
   * **[!UICONTROL Handler-Modus]**: Wählen Sie diese Option aus, um den Workflow nach der Ausführung automatisch an den nächsten Schritt weiterzuleiten. Wenn diese Option nicht ausgewählt ist, muss das Implementierungsskript den Workflow weiterleiten.
   * **[!UICONTROL Argumente]**: An den Prozess zu übergebende Argumente.


