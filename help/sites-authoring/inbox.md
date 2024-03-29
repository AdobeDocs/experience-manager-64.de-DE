---
title: Ihr Posteingang
seo-title: Your Inbox
description: Verwalten Ihrer Aufgaben im Posteingang
seo-description: Managing your tasks with the inbox
uuid: ddd48019-ce69-4a47-be2b-5b66ae2fe3c8
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 8b607b55-2412-469f-856b-0a3dea4b0efb
exl-id: 9037f21c-5392-4322-af0d-7e220c810954
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 42%

---

# Ihr Posteingang{#your-inbox}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können Benachrichtigungen aus verschiedenen AEM erhalten, einschließlich Workflows und Projekten. Beispiel: about:

* Aufgaben:

   * diese können auch an verschiedenen Stellen in der AEM Benutzeroberfläche erstellt werden, z. B. unter **Projekte**,
   * diese können das Produkt eines Workflows sein. **Aufgabe erstellen** oder **Projektaufgabe erstellen** Schritt.

* Workflows:

   * Arbeitselemente, die Aktionen darstellen, die Sie für Seiteninhalte ausführen müssen;

      * diese sind das Produkt des Workflows **Teilnehmer** Schritte
   * Fehlerelemente, damit Administratoren den fehlgeschlagenen Schritt erneut ausführen können.


Sie erhalten diese Benachrichtigungen in Ihrem eigenen Posteingang, in dem Sie sie anzeigen und Maßnahmen ergreifen können.

>[!NOTE]
>
>Vordefinierte AEM enthalten vordefinierte Aufgaben, die der Administrator-Benutzergruppe zugewiesen sind. Siehe [Vordefinierte Verwaltungsaufgaben](#out-of-the-box-administrative-tasks) für Details.

>[!NOTE]
>
>Weitere Informationen zu den Elementtypen finden Sie unter:
>
>* [Projekte](/help/sites-authoring/touch-ui-managing-projects.md)
>* [Projekte – Arbeiten mit Aufgaben](/help/sites-authoring/task-content.md)
>* [Workflows](/help/sites-authoring/workflows.md)
>* [Formulare](/help/forms/home.md)
>


## Posteingang in der Kopfzeile {#inbox-in-the-header}

In sämtlichen Konsolen wird in der Kopfzeile die Anzahl der aktuell in Ihrem Posteingang vorhandenen Elemente angezeigt. Die Anzeige kann auch geöffnet werden, um einen schnellen Zugriff auf die Seiten zu ermöglichen, für die Aktionen erforderlich sind, oder um auf den Posteingang zuzugreifen:

![wf-80](assets/wf-80.png)

>[!NOTE]
>
>Bestimmte Aktionen werden auch in der [Kartenansicht der jeweiligen Ressource](/help/sites-authoring/basic-handling.md#card-view) angezeigt.

## Vordefinierte Verwaltungsaufgaben  {#out-of-the-box-administrative-tasks}

Standardmäßig AEM mit vier Aufgaben vorab geladen, die der Administrator-Benutzergruppe zugewiesen sind.

* [Analysen und Targeting konfigurieren](/help/sites-administering/opt-in.md)
* [AEM-Sicherheitsprüfliste anwenden](/help/sites-administering/security-checklist.md)
* Aggregierte Sammlung von Nutzungsstatistiken aktivieren
* [Konfigurieren von HTTPS](/help/sites-administering/ssl-by-default.md)

## Öffnen des Posteingangs {#opening-the-inbox}

So öffnen Sie den Benachrichtigungs-Posteingang in AEM:

1. Klicken/tippen Sie auf die Anzeige in der Symbolleiste.

1. Wählen Sie **Alle anzeigen** aus. Der **AEM-Posteingang** wird geöffnet. Im Posteingang werden Elemente aus den Bereichen Workflows, Projekte und Aufgaben angezeigt.
1. Die Standardansicht ist die [Listenansicht](#inbox-list-view), Sie können aber auch zur [Kalenderansicht ](#inbox-calendar-view)wechseln. Dies erfolgt mit der Ansichtsauswahl (Symbolleiste oben rechts).

   Für beide Ansichten können Sie auch [Anzeigeeinstellungen](#inbox-view-settings); Die verfügbaren Optionen hängen von der aktuellen Ansicht ab.

   ![wf-79](assets/wf-79.png)

>[!NOTE]
>
>Der Posteingang fungiert als Konsole. Verwenden Sie daher die [globale Navigation](/help/sites-authoring/basic-handling.md#global-navigation) oder die [Suche](/help/sites-authoring/search.md), um zu einer anderen Position zu navigieren, wenn Sie fertig sind.

### Posteingang – Listenansicht {#inbox-list-view}

Diese Ansicht listet alle Elemente zusammen mit wichtigen relevanten Informationen auf:

![wf-82](assets/wf-82.png)

### Posteingang – Kalenderansicht {#inbox-calendar-view}

Diese Ansicht zeigt Elemente entsprechend ihrer Position im Kalender und der von Ihnen ausgewählten genauen Ansicht an:

![wf-93](assets/wf-93.png)

Sie haben folgende Möglichkeiten:

* eine bestimmte Ansicht auswählen (**Zeitleiste**,**Spalte** oder **Liste**)

* die Aufgaben angeben, die gemäß **Zeitplan**; **Alle**, **Geplant**, **In Bearbeitung**, **Bald fällig**, **Überfällig**

* detailliertere Informationen zu einem Element anzeigen
* Wählen Sie einen Datumsbereich aus, um die Ansicht zu fokussieren:

![wf-91](assets/wf-91.png)

### Posteingang – Anzeigeeinstellungen {#inbox-view-settings}

Für beide Ansichten (Liste und Kalender) können Sie Einstellungen definieren:

* **Kalenderansicht**

   Für **Kalenderansicht** Sie können Folgendes konfigurieren:

   * **Gruppieren nach**
   * **Zeitplan** oder **Ohne**
   * **Kartengröße**

   ![wf-92](assets/wf-92.png)

* **Listenansicht**

   Für **Listenansicht** Sie können den Sortiermechanismus konfigurieren:

   * **Sortieren nach**
   * **Sortierreihenfolge**

   ![wf-83](assets/wf-83.png)

## Anwenden von Aktionen auf ein Element {#taking-action-on-an-item}

1. Um eine Aktion auf ein Element anzuwenden, wählen Sie die Miniatur des gewünschten Elements aus. In der Symbolleiste werden Symbole für die Aktionen angezeigt, die auf dieses Element anwendbar sind:

   ![wf-84](assets/wf-84.png)

   Die entsprechend dem ausgewählten Element verfügbaren Aktionen können Folgendes umfassen:

   * **Abschließen** einer Aktion, z. B. einer Aufgabe oder eines Workflow-Elements
   * **Neu zuweisen**/**Delegieren** ein Element.
   * **Öffnen** ein Element; Je nach Elementtyp kann diese Aktion:

      * Anzeigen der Objekteigenschaften
      * Öffnen Sie das entsprechende Dashboard oder den entsprechenden Assistenten für weitere Aktionen.
      * geöffnete zugehörige Dokumentation
   * **Schritt zurück** zu einem vorherigen Schritt.
   * Anzeigen der Payload eines Workflows.
   * Erstellen eines Projekts auf Basis des Elements.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter:
   >
   >* Workflow-Elemente - [Teilnehmen an Workflows](/help/sites-authoring/workflows-participating.md)


1. Je nach ausgewähltem Element wird eine Aktion gestartet. Beispiel:

   * wird ein der Aktion entsprechendes Dialogfeld geöffnet.
   * Ein Aktionsassistent wird gestartet.
   * eine Dokumentationsseite geöffnet wird.

   Beispiel: **Neu zuweisen** öffnet ein Dialogfeld:

   ![wf-85](assets/wf-85.png)

   Je nachdem, ob ein Dialogfeld, ein Assistent oder eine Dokumentationsseite geöffnet wurde, können Sie Folgendes durchführen:

   * die geeigneten Maßnahmen zu bestätigen; z. B. Neu zuweisen.
   * Abbrechen der Aktion.
   * Rückwärtspfeil; Wenn beispielsweise ein Aktionsassistent oder eine Dokumentationsseite geöffnet wurde, können Sie zum Posteingang zurückkehren.


## Erstellen einer Aufgabe {#creating-a-task}

Im Posteingang können Sie Aufgaben erstellen:

1. Auswählen **Erstellen**, dann **Aufgabe**.
1. Füllen Sie die erforderlichen Felder im **Allgemein** und **Erweitert** Registerkarten; nur die **Titel** ist obligatorisch, alle anderen sind optional:

   * **Allgemein**:

      * **Titel**
      * **Projekt**
      * **Bevollmächtigter**
      * **Inhalt**; dies dient, ähnlich wie bei der Payload, als Verweis von der Aufgabe auf eine Position im Repository.
      * **Beschreibung**
      * **Aufgabenpriorität**
      * **Startdatum**
      * **Fälligkeitsdatum**

   ![wf-86](assets/wf-86.png)

   * **Erweitert**

      * **Name**: wird verwendet, um die URL zu bilden; Wenn das Feld leer ist, basiert es auf der **Titel**.

   ![wf-87](assets/wf-87.png)

1. Klicken Sie auf **Übermitteln**.

## Erstellen eines Projekts {#creating-a-project}

Für bestimmte Aufgaben können Sie eine [Projekt](/help/sites-authoring/projects.md) basierend auf dieser Aufgabe:

1. Wählen Sie die gewünschte Aufgabe aus, indem Sie auf die Miniaturansicht tippen/klicken.

   >[!NOTE]
   >
   >Für die Erstellung eines Projekts können nur Aufgaben verwendet werden, die im **Posteingang** über die Option **Erstellen** erstellt wurden.
   >
   >Arbeitselemente (aus einem Workflow) können nicht zum Erstellen eines Projekts verwendet werden.

1. Wählen Sie **Projekt erstellen** aus der Symbolleiste aus, um den Assistenten zu öffnen.
1. Wählen Sie die entsprechende Vorlage aus und **Nächste**.
1. Geben Sie die erforderlichen Eigenschaften an:

   * **Allgemein**

      * **Titel**
      * **Beschreibung**
      * **Startdatum**
      * **Fälligkeitsdatum**
      * **Benutzer** und Rolle
   * **Erweitert**

      * **Name**
   >[!NOTE]
   >
   >Siehe [Erstellen eines Projekts](/help/sites-authoring/touch-ui-managing-projects.md#creating-a-project) für vollständige Informationen.

1. Auswählen **Erstellen** , um die Aktion zu bestätigen.

## Filtern von Elementen im AEM-Posteingang {#filtering-items-in-the-aem-inbox}

Sie können die aufgeführten Elemente filtern:

1. Öffnen Sie den **AEM-Posteingang**.

1. Öffnen Sie die Filterauswahl:

   ![wf-88](assets/wf-88.png)

1. Sie können die Elemente nach verschiedenen Kriterien filtern, wobei viele davon weiter eingegrenzt werden können, z. B.:

   ![wf-89](assets/wf-89.png)

   >[!NOTE]
   >
   >Bei Verwendung der [Listenansicht](#inbox-list-view) können Sie außerdem über die [Anzeigeeinstellungen](#inbox-view-settings) die Sortierreihenfolge festlegen.
