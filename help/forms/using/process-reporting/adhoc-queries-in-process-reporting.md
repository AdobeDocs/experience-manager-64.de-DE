---
title: Ad-hoc-Abfragen in Prozessberichten
seo-title: Ad-hoc Queries in Process Reporting
description: Erstellen Sie benutzerdefinierte Abfragen, um nach AEM Forms on JEE-Prozess- und Aufgabendetails in Process Reporting zu suchen.
seo-description: Create custom queries to search for AEM Forms on JEE  process and task details in Process Reporting
uuid: bcd9eecd-5c83-402d-8533-a27f6b346191
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 812f9212-2732-4966-a7fa-389aa2332c7e
exl-id: a5ac05b2-076a-4d3d-8325-32813657a7b3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1668'
ht-degree: 0%

---

# Ad-hoc-Abfragen in Prozessberichten {#ad-hoc-queries-in-process-reporting}

Mit Ad-hoc-Abfragen in Process Reporting können Sie benutzerdefinierte Abfragen erstellen, mit denen Sie nach Prozess- und Aufgabendetails der in Ihrer AEM Forms-Umgebung definierten AEM Forms-Prozessinstanzen suchen können.

Ad-hoc-Abfragen können auch mithilfe von Prozess- und Aufgabeneigenschaftsfiltern definiert werden. Diese Filter können dann gespeichert und zur späteren Ausführung der Berichte verwendet werden.

[**Prozesssuche**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-search-p): Suchen Sie nach Prozessinstanzen mit einem benutzerdefinierten Suchfilter basierend auf Prozessattributen.

[**Prozessdetails**](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-process-task-details-p): Zeigen Sie Details einer Prozessinstanz an, indem Sie die Prozess-ID angeben.

**Aufgabensuche**: Suchen Sie anhand von Aufgabenattributen nach Aufgabeninstanzen mit einem benutzerdefinierten Suchfilter.

**Aufgabendetails**: Zeigen Sie Details einer Aufgabeninstanz an, indem Sie die Aufgaben-ID angeben.

## Prozesse und Aufgaben {#processes-and-tasks}

Die Schritte zum Erstellen von Filtern und Ausführen von Abfragen für Prozessdetails sind dieselben wie für Aufgaben.

Das bedeutet, dass sich die Benutzeroberflächen für die Prozesssuche und Aufgabensuche nur in den Feldern, nach denen Sie suchen können, und in den Suchergebnissen zurückgegebenen Feldern unterscheiden. Dies liegt einfach daran, dass zwar viele der Felder identisch sind, bestimmte Felder jedoch für Prozesse spezifisch sind und bestimmte Felder für Aufgaben spezifisch sind.

In diesem Artikel werden die Beschreibungen der Abschnitte Prozess-/Aufgabensuche und Prozess-/Aufgabendetails beschrieben. An geeigneten Orten werden alle spezifischen Unterschiede speziell ausgewiesen.

## Prozess-/Aufgabensuche {#process-task-search}

Sie verwenden die Prozess-/Aufgabensuche, um Filter zum Abfragen von Prozess-/Aufgabeninstanzen zu definieren.

### So erstellen Sie eine Prozess-/Aufgabensuchabfrage {#to-create-a-process-task-search-query}

1. Um die gespeicherten Prozess-/Aufgabensuchabfragen anzuzeigen oder eine Abfrage zu erstellen, klicken Sie auf **Ad-hoc-Abfragen** und klicken Sie anschließend auf **Prozess-/Aufgabensuche**.

   ![search_nodes](assets/search_nodes.png)

   Die **Meine Filter** wird rechts neben der Baumansicht angezeigt.

   Im **Meine Filter** können Sie neue Ad-hoc-Abfragen erstellen und auf klicken, um zuvor gespeicherte Abfragen auszuführen.

   ![my_filters_panel](assets/my_filters_panel.png)

1. Um eine vorhandene Abfrage auszuführen, klicken Sie einfach auf die Abfrage im **Meine Filter** Bereich.
1. Um eine Abfrage zu erstellen, klicken Sie auf **Hinzufügen** (+).

   Die **Filter erstellen** angezeigt.

   ![create_filter_panel](assets/create_filter_panel.png)

   Eine Abfrage besteht aus einem oder mehreren Abfragefiltern. Um einen Filter zu erstellen, fügen Sie der Abfrage eine Filterzeile hinzu. Standardmäßig wird der Abfrage eine Filterzeile hinzugefügt.

   **So definieren Sie Filter**

   1. Wählen Sie ein Feld aus.

      ![filter_field](assets/filter_field.png)

      >[!NOTE]
      >
      >Die Feldliste enthält die Felder, die für den AEM Forms-Prozess/die Aufgabe spezifisch sind.

   1. Wählen Sie eine Bedingung aus.

      ![filter_condition](assets/filter_condition.png)

      >[!NOTE]
      >
      >Die aufgeführten Bedingungen hängen von dem Attribut ab, das zum Filtern ausgewählt wurde.

   1. Geben Sie einen Wert ein.

      ![filter_value](assets/filter_value.png)

   1. Um der Abfrage einen weiteren Filter hinzuzufügen, klicken Sie auf **Add(+)** rechts neben der Filterzeile.

      Um einen Filter aus der Abfrage zu entfernen, klicken Sie auf **Löschen(-)** rechts neben der Filterzeile.

      ![filter_add_del](assets/filter_add_del.png)

Nachdem Sie eine Abfrage erstellt haben, verwenden Sie die Optionen oben rechts im **Filter erstellen** -Bedienfeld zu:

* **Abbrechen**: Abbrechen Sie die Änderungen und kehren Sie zur **Meine Filter** Bereich.

* **Ausführen**: Führen Sie die aktuelle Abfrage aus, um die Ergebnisse anzuzeigen bzw. zu überprüfen. In diesem Fall müssen Sie die Abfrage nicht speichern, bevor Sie die Abfrage ausführen. Sie können die Ergebnisse überprüfen, bei Bedarf Änderungen vornehmen und dann die Abfrage speichern, wenn Sie mit der Ausgabe zufrieden sind.

* **Speichern**: Speichern Sie den Filter. Der Filter kann dann über die **Meine Filter** Bereich.

### Optionen im Bereich &quot;Meine Filter&quot; {#options-in-my-filters-panel}

Verwenden Sie die Optionen in der **Meine Filter** Bedienfeld zu **Hinzufügen** ![lc_pr_add_filter](assets/lc_pr_add_filter.png), **Bearbeiten** ![lc_pr_delete_filter](assets/lc_pr_delete_filter.png)oder **Löschen** ![lc_pr_edit_filter](assets/lc_pr_edit_filter.png)eine Ad-hoc-Abfrage.

![my_filters_options](assets/my_filters_options.png)

### So führen Sie eine Suchabfrage aus {#to-execute-a-search-query}

1. Um eine Abfrage auszuführen, klicken Sie auf den Filter im **Meine Filter** oder klicken Sie auf **Ausführen** -Schaltfläche, wenn Sie einen Filter erstellen oder bearbeiten.
1. Die Ergebnisse der Abfrage werden in der **Bericht** -Bedienfeld der **Prozessberichterstellung** Fenster.

   ![process_search_result](assets/process_search_result.png)

   Sie können die Suchergebnisse mithilfe des Paginierungs-Bedienfelds, das am unteren Rand des Berichts angezeigt wird, paginieren.

   ![process_result_pgn](assets/process_result_pgn.png)

   Im **Anzeige** die Anzahl der Ergebnisse wählen, die pro Seite angezeigt werden sollen.

   Im **Seite** eingeben, geben Sie eine Seitenzahl ein, um direkt zu dieser Seite zu gelangen.

1. Die folgenden Felder werden in einem Prozesssuchergebnis angezeigt:

   * **Prozess-ID**: Die Kennung des Prozesses. Das Feld ist per Hyperlink gekennzeichnet. Wenn Sie in diesem Feld auf eine Prozess-ID klicken, werden Sie zum **[!UICONTROL Prozessdetails]** -Bedienfeld für den Prozess.
   * **Initiator**: Der AEM Forms-Benutzer, der die Prozessinstanz gestartet hat
   * **Erstellte Zeit**: Datum und Uhrzeit des Starts der Prozessinstanz
   * **Abgeschlossene Zeit**: Datum und Uhrzeit des Abschlusses der Prozessinstanz
   * **Dauer**: Die Dauer von Beginn bis Ende der Prozessinstanz
   * **Status**: Der aktuelle Status der Prozessinstanz.

   Standardmäßig wird das Ergebnis nach Prozess-ID sortiert. Um das Ergebnis jedoch nach einem der Felder zu sortieren, klicken Sie auf den Feldtitel.

   Da es sich bei der Sortierung um einen Umschalter handelt, klicken Sie auf eine Spaltenüberschrift, um das Ergebnis aufsteigend zu sortieren, und klicken Sie erneut auf die Spalte, um es in absteigender Reihenfolge zu sortieren.

   Gleichermaßen werden die folgenden Felder in einem Task Search-Ergebnis angezeigt:

   * **Task-ID**: Die ID der Aufgabe. Das Feld ist per Hyperlink gekennzeichnet. Wenn Sie in diesem Feld auf eine Aufgaben-ID klicken, werden Sie zum **[!UICONTROL Aufgabendetails]** -Bedienfeld für die Aufgabe.
   * **Initiator**: Der AEM Forms-Benutzer, der die Prozessinstanz gestartet hat
   * **Erstellte Zeit**: Datum und Uhrzeit des Starts der Prozessinstanz

   * **Abgeschlossene Zeit**: Datum und Uhrzeit des Abschlusses der Prozessinstanz
   * **Dauer**: Die Dauer von Beginn bis Ende der Prozessinstanz
   * **Status**: Der aktuelle Status der Prozessinstanz.

   Standardmäßig wird das Ergebnis nach Aufgabe-ID sortiert. Um das Ergebnis jedoch nach einem der Felder zu sortieren, klicken Sie auf den Feldtitel. Das Ergebnis wird nach der Spalte sortiert, die durch einen dunklen Pfeil neben der Spaltenüberschrift angezeigt wird.

   Da es sich bei der Sortierung um einen Umschalter handelt, klicken Sie auf eine Feldüberschrift, um das Ergebnis aufsteigend zu sortieren, und klicken Sie erneut auf diese Option, um es in absteigender Reihenfolge zu sortieren. Die aktuelle Sortierreihenfolge (aufsteigend/absteigend) wird durch die Richtung des dunklen Pfeils neben der Spaltenüberschrift angezeigt.

   ![task_search_result](assets/task_search_result.png)

1. Klicken Sie auf die Schaltfläche in der Leiste ![lc_pr_rail_button](assets/lc_pr_rail_button.png) oben links zum Reduzieren der **Meine Filter** und erweitert den für die **Bericht** Bereich.
1. Verwenden Sie die Optionen oben rechts im **Bericht** -Bedienfeld, um Vorgänge für das Abfrageergebnis durchzuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Exportieren in CSV**: Exportieren Sie die Berichtsdaten in eine kommagetrennte Datei.

   >[!NOTE]
   >
   >Wenn Sie einen Bericht exportieren, wird das gesamte Suchergebnis in eine CSV-Datei exportiert und nicht nur in die aktuelle Seite

## Prozess-/Aufgabendetails {#process-task-details}

Sie verwenden die **Prozessdetails** -Bereich, um die Details eines bestimmten Prozesses anzuzeigen.

Auf ähnliche Weise verwenden Sie die **Aufgabendetails** um die Details einer bestimmten Aufgabe anzuzeigen.

### So zeigen Sie Prozess-/Aufgabendetails an {#to-view-process-task-details}

Sie können die Details eines bestimmten AEM Forms-Prozesses/einer bestimmten Aufgabe anzeigen:

* **Aus einem Prozess-/Aufgabensuchergebnis**
* **Durch Eingabe der Prozess-/Aufgaben-ID im Bereich &quot;Prozess-/Aufgabendetails&quot;**

#### Aus einem Prozess-/Aufgabensuchergebnis {#from-a-process-task-search-result}

1. Führen Sie eine Prozess-/Aufgabensuche aus. Weitere Informationen finden Sie unter [So führen Sie eine Prozesssuchabfrage aus](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md#p-to-execute-a-search-query-p).

   Beachten Sie, dass die im Ergebnis zurückgegebenen Prozess-IDs per Hyperlink verknüpft sind.

   ![process_id_list](assets/process_id_list.png)

1. Klicken Sie auf eine Prozess-ID in der Liste, um die Details dieses Prozesses im **Prozessdetails** Bereich.

   Die **Prozess-/Aufgabendetails** Das Abfrageergebnis zeigt Details zu den Aufgaben/Formularen an, die in dem Prozess/der Aufgabe enthalten sind.

   Standardmäßig wird das Ergebnis nach Aufgabe/Formular-ID sortiert. Um das Ergebnis jedoch nach einem der Felder zu sortieren, klicken Sie auf den Feldtitel. Die Spalte, nach der das Ergebnis sortiert wird, wird durch einen dunklen Pfeil neben der Spaltenüberschrift angezeigt.

   Da es sich bei der Sortierung um einen Umschalter handelt, klicken Sie auf eine Feldüberschrift, um das Ergebnis aufsteigend zu sortieren, und klicken Sie erneut auf diese Option, um es in absteigender Reihenfolge zu sortieren. Die aktuelle Sortierreihenfolge (aufsteigend/absteigend) wird durch die Richtung des dunklen Pfeils neben der Spaltenüberschrift angezeigt.

   **Ergebnis der Prozessdetails**

   ![process_details](assets/process_details.png)

   **Linke Leiste:** Zeigt die folgenden Details des ausgewählten Prozesses an:

   * Name des Prozesses
   * Zeitpunkt der Prozesserstellung
   * Zeitpunkt des Prozessabschlusses
   * Prozessdauer
   * Prozessstatus
   * Prozessinitiator

   **Oben rechts:** Zeigt die folgenden Details zu den Aufgaben an, aus denen der ausgewählte Prozess besteht:

   * Aufgaben-ID
   * Aufgabenname
   * Aufgabenbesitzer
   * Zeitpunkt der Aufgabenerstellung
   * Zeitpunkt der Aufgabenaktualisierung
   * Zeitpunkt der Aufgabenfertigstellung
   * Aufgabendauer
   * Aufgabenstatus

   **Bereich unten rechts:** Zeigt die folgenden Details zum Prozessverlauf des ausgewählten Prozesses an:

   * Prozessname
   * Prozessinitiator
   * Datum der Prozessaktualisierung
   * Zeitpunkt des Prozessabschlusses
   * Prozessstatus

   **Ergebnis der Aufgabendetails**

   ![Aufgabendetails](assets/task_details.png)

   **Linke Leiste:** Zeigt die folgenden Details der ausgewählten Aufgabe an:

   * Aufgabenname
   * Kennung des Prozesses, zu dem diese Aufgabe gehört
   * Aufgabenbeschreibung
   * Zeitpunkt der Aufgabenerstellung
   * Zeitpunkt der Aufgabenfertigstellung
   * Aufgabendauer
   * Aufgabenstatus
   * Ausgewählter Aufgabenweg

   **Oben rechts:** Zeigt die folgenden Details zu den Formularen an, aus denen die ausgewählte Aufgabe besteht:

   * Formular-ID
   * Datum der Formularerstellung
   * Datum der Formularaktualisierung
   * Formularvorlagen-URL

   **Bereich unten rechts:** Zeigt die folgenden Details zum Prozessverlauf der ausgewählten Aufgabe an:

   * Aufgabenzuweisungstyp
   * Aufgabenbesitzer
   * Erstellungsdatum der Aufgabenzuweisung
   * Zeitpunkt der Aufgabenaktualisierung






1. Klicken **Zurück zur Prozess-/Aufgabensuche** , um zum Suchergebnis zurückzukehren, aus dem die Prozess-/Aufgabendetails heruntergefahren wurden.

   ![back_to_search](assets/back_to_search.png)

   Wenn die Prozess-/Aufgabendetails jedoch durch Eingabe einer bestimmten Prozess-/Aufgabenkennung gefunden wurden, werden Sie durch Klicken auf Zurück zum Prozess/Aufgabensuche zurück zu **Prozess-/Aufgabensuche**, ohne Suchergebnisse anzuzeigen.

#### Durch Eingabe der Prozess-/Aufgaben-ID im Bereich &quot;Prozess-/Aufgabendetails&quot; {#by-entering-the-process-task-id-in-the-process-task-details-panel-br}

1. Navigieren Sie zu **Prozess-/Aufgabendetails** Bereich.

   ![details_nodes](assets/details_nodes.png)

1. Geben Sie im Textfeld Prozess-/Aufgaben-ID die Prozess-/Aufgaben-ID ein.

   ![process_details-1](assets/process_details-1.png)

   Die Felder im **Prozess-/Aufgabendetails** Abfrageergebnisse sind Felder, die für einen AEM Forms-Prozess/eine Aufgabe spezifisch sind.

   Für einen Prozess zeigt das Abfrageergebnis die Details der im Prozess enthaltenen Aufgaben an.

   Für eine Aufgabe zeigt das Abfrageergebnis die Details der in der Aufgabe enthaltenen Formulare an.
