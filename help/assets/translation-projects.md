---
title: Erstellen von Übersetzungsprojekten
description: Erfahren Sie, wie Sie Übersetzungsprojekte in AEM erstellen.
contentOwner: AG
feature: Translation
role: Architect,Admin
exl-id: 1b931fef-eed0-4758-993d-cdf8d478fb6f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1975'
ht-degree: 62%

---

# Erstellen von Übersetzungsprojekten {#creating-translation-projects}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Um eine Sprachkopie zu erstellen, führen Sie einen der folgenden Sprachkopie-Workflows aus, die in der Assets-Benutzeroberfläche in der Leiste Verweise verfügbar sind:

**Erstellen und übersetzen**

In diesem Workflow werden zu übersetzende Assets in den Sprachstamm der Sprache kopiert, in die Sie übersetzen möchten. Darüber hinaus wird je nach gewählten Optionen in der Projektekonsole ein Übersetzungsprojekt für die Assets erstellt. Abhängig von den Einstellungen kann das Übersetzungsprojekt manuell gestartet oder automatisch ausgeführt werden, sobald das Übersetzungsprojekt erstellt wurde.

**Aktualisieren von Sprachkopien**

Sie führen diesen Workflow aus, um eine zusätzliche Gruppe von Assets zu übersetzen und sie in eine Sprachkopie für ein bestimmtes Gebietsschema einzuschließen. In diesem Fall werden die übersetzten Assets zu dem Zielordner hinzugefügt, der bereits zuvor übersetzte Assets enthält.

>[!NOTE]
>
>Asset-Binärdateien werden nur übersetzt, wenn der Übersetzungsanbieter die Übersetzung von Binärdateien unterstützt.

>[!NOTE]
>
>Wenn Sie einen Übersetzungs-Workflow für komplexe Assets wie PDF- und InDesign-Dateien starten, werden deren Teil-Assets oder Ausgabeformate (falls vorhanden) nicht zur Übersetzung übermittelt.

## Workflow für das Erstellen und Übersetzen {#create-and-translate-workflow}

Mit dem Workflow &quot;Erstellen und übersetzen&quot;generieren Sie erstmals Sprachkopien für eine bestimmte Sprache. Der Workflow bietet die folgenden Optionen:

* Nur Struktur erstellen
* Erstellen eines neuen Übersetzungsprojekts
* Hinzufügen zu einem vorhandenen Übersetzungsprojekt

### Nur Struktur erstellen {#create-structure-only}

Verwenden Sie die Option **Nur Struktur erstellen**, um eine Zielordnerhierarchie im Zielsprachenstamm zu erstellen und die Hierarchie des Quellordners im Ausgangssprachenstamm widerzuspiegeln. In diesem Fall werden Quellelemente in den Zielordner kopiert. Es wird jedoch kein Übersetzungsprojekt generiert.

1. Wählen Sie in der Assets-Benutzeroberfläche den Quellordner aus, für den Sie eine Struktur im Zielsprachenstamm erstellen möchten.
1. Wechseln Sie zum Bereich **[!UICONTROL Verweise]** und klicken/tippen Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Klicken/tippen Sie unten auf **[!UICONTROL Erstellen und übersetzen]**.

   ![chlimage_1-58](assets/chlimage_1-58.png)

1. Wählen Sie aus der Liste **[!UICONTROL Zielsprachen]** die Sprache, für die Sie eine Ordnerstruktur erstellen möchten.

   ![chlimage_1-59](assets/chlimage_1-59.png)

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Nur Struktur erstellen]**.

   ![chlimage_1-60](assets/chlimage_1-60.png)

1. Klicken/tippen Sie auf **[!UICONTROL Erstellen]**. Die neue Struktur für die Zielsprache wird unter **[!UICONTROL Sprachkopien]** aufgeführt.

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Klicken/tippen Sie auf die Struktur aus der Liste und dann auf **[!UICONTROL In Assets einblenden]**, um zur Ordnerstruktur in der Zielsprache zu navigieren.

   ![chlimage_1-62](assets/chlimage_1-62.png)

### Erstellen eines neuen Übersetzungsprojekts {#create-a-new-translation-project}

Wenn Sie diese Option verwenden, werden die zu übersetzenden Assets in den Sprachstamm der Sprache kopiert, in die Sie übersetzen möchten. Je nach den von Ihnen gewählten Optionen wird in der Projektekonsole ein Übersetzungsprojekt für die Assets erstellt. Abhängig von den Einstellungen kann das Übersetzungsprojekt manuell gestartet oder automatisch ausgeführt werden, sobald das Übersetzungsprojekt erstellt wurde.

1. Wählen Sie in der Assets-Benutzeroberfläche den Quellordner aus, für den Sie eine Sprachkopie erstellen möchten.
1. Wechseln Sie zum Bereich **[!UICONTROL Verweise]** und klicken/tippen Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**.

   ![chlimage_1-63](assets/chlimage_1-63.png)

1. Klicken/tippen Sie unten auf **[!UICONTROL Erstellen und übersetzen]**.

   ![chlimage_1-64](assets/chlimage_1-64.png)

1. Wählen Sie aus der Liste **[!UICONTROL Zielsprachen]** die Sprache(n), für die Sie eine Ordnerstruktur erstellen möchten.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Neues Übersetzungsprojekt erstellen]**.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Geben Sie im Feld **[!UICONTROL Projekttitel]** einen Namen für das Projekt ein.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Klicken/tippen Sie auf **[!UICONTROL Erstellen]**. Assets aus dem Quellordner werden in die Zielordner für die Gebietsschemas kopiert, die Sie in Schritt 4 gewählt haben.

   ![chlimage_1-68](assets/chlimage_1-68.png)

1. Um zum Ordner zu navigieren, wählen Sie die Sprachkopie und klicken Sie auf **[!UICONTROL In Assets einblenden]**.

   ![chlimage_1-69](assets/chlimage_1-69.png)

1. Gehen Sie zur Projektekonsole. Der Übersetzungsordner wird in die Projektekonsole kopiert.

   ![chlimage_1-70](assets/chlimage_1-70.png)

1. Öffnen Sie den Ordner, um das Übersetzungsprojekt anzuzeigen.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. Klicken/tippen Sie auf das Projekt, um die Detailseite zu öffnen.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen.

   ![chlimage_1-73](assets/chlimage_1-73.png)

   Weitere Informationen zum Auftragsstatus finden Sie unter [Überwachen des Status eines Übersetzungsauftrags](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Navigieren Sie zur Assets-Benutzeroberfläche und öffnen Sie die Seite Eigenschaften für jedes der übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

   ![chlimage_1-74](assets/chlimage_1-74.png)

   >[!NOTE]
   >
   >Diese Funktion ist sowohl für Assets als auch für Ordner verfügbar. Wenn ein Asset anstelle eines Ordners ausgewählt wird, wird die gesamte Ordnerhierarchie bis zum Sprachstamm kopiert, um eine Sprachkopie für das Asset zu erstellen.

### Hinzufügen zu einem vorhandenen Übersetzungsprojekt {#add-to-existing-translation-project}

Wenn Sie diese Option verwenden, wird der Übersetzungs-Workflow für Assets ausgeführt, die Sie dem Quellordner hinzufügen, nachdem Sie einen vorherigen Übersetzungs-Workflow ausgeführt haben. Nur die neu hinzugefügten Assets werden in den Zielordner kopiert, der zuvor übersetzte Assets enthält. In diesem Fall wird kein neues Übersetzungsprojekt erstellt.

1. Navigieren Sie in der Assets-Benutzeroberfläche zum Quellordner, der nicht übersetzte Assets enthält.
1. Wählen Sie ein Asset, das Sie übersetzen möchten, und wechseln Sie zum Bereich **[!UICONTROL Verweise]**. Im Abschnitt **[!UICONTROL Sprachkopien]** wird die Anzahl der Übersetzungskopien angezeigt, die momentan verfügbar sind.
1. Klicken/tippen Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**. Eine Liste der verfügbaren Übersetzungskopien wird angezeigt.
1. Klicken/tippen Sie unten auf **[!UICONTROL Erstellen und übersetzen]**.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Wählen Sie aus der Liste **[!UICONTROL Zielsprachen]** die Sprache(n), für die Sie eine Ordnerstruktur erstellen möchten.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]**, um den Übersetzungs-Workflow für den Ordner auszuführen.

   ![chlimage_1-77](assets/chlimage_1-77.png)

   >[!NOTE]
   >
   >Wenn Sie die **[!UICONTROL Hinzufügen zu einem vorhandenen Übersetzungsprojekt]** -Option, wird Ihr Übersetzungsprojekt nur dann zu einem bereits vorhandenen Projekt hinzugefügt, wenn Ihre Projekteinstellungen genau mit den Einstellungen des bereits vorhandenen Projekts übereinstimmen. Andernfalls wird ein neues Projekt erstellt.

1. Wählen Sie aus der Liste **[!UICONTROL Vorhandenes Übersetzungsprojekt]** ein Projekt, dem das zu übersetzende Asset hinzugefügt werden soll.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Klicken/tippen Sie auf **[!UICONTROL Erstellen]**. Die zu übersetzenden Assets werden dem Zielordner hinzugefügt. Der aktualisierte Ordner wird unter **[!UICONTROL Sprachkopien]** aufgeführt.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Gehen Sie zur Projektkonsole und öffnen Sie das vorhandene Übersetzungsprojekt, dem Sie Assets hinzugefügt haben.
1. Klicken/tippen Sie auf das Übersetzungsprojekt, um die Seite mit den Projektdetails anzuzeigen.

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Klicken/tippen Sie unten auf der Kachel **Übersetzungsauftrag** auf das Auslassungszeichen, um die Assets im Übersetzungs-Workflow anzuzeigen. In der Übersetzungsauftragsliste werden auch Einträge für Asset-Metadaten und -Tags aufgeführt. Diese Einträge geben an, dass die Metadaten und Tags für die Assets ebenfalls übersetzt werden.

   >[!NOTE]
   >
   >Wenn Sie den Eintrag für Tags oder Metadaten löschen, werden keine Tags oder Metadaten für die Assets übersetzt.

   >[!NOTE]
   >
   >Wenn Sie maschinelle Übersetzung verwenden, werden Asset-Binärdateien nicht übersetzt.

   >[!NOTE]
   >
   >Wenn das Asset, das Sie zum Übersetzungsauftrag hinzufügen, Teil-Assets enthält, wählen Sie die Teil-Assets und entfernen Sie sie, damit die Übersetzung fehlerfrei fortgesetzt werden kann.

1. Um die Übersetzung der Assets zu starten, klicken/tippen Sie auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf den Pfeil und wählen Sie aus der Liste die Option **[!UICONTROL Start.]**

   ![chlimage_1-81](assets/chlimage_1-81.png)

   Eine Meldung informiert Sie darüber, dass mit der Ausführung des Übersetzungsauftrags begonnen wird.

   ![chlimage_1-82](assets/chlimage_1-82.png)

1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken/tippen Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen.

   ![chlimage_1-83](assets/chlimage_1-83.png)

   Weitere Informationen finden Sie unter [Überwachen des Status eines Übersetzungsauftrags](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Nach Abschluss des Übersetzungsvorgangs ändert sich der Status in „Bereit für Überprüfung“. Navigieren Sie zur Assets-Benutzeroberfläche und öffnen Sie die Seite Eigenschaften für jedes der übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

## Aktualisieren von Sprachkopien {#update-language-copies}

Führen Sie diesen Workflow aus, um zusätzliche Assets zu übersetzen und sie in eine Sprachkopie für ein bestimmtes Gebietsschema einzuschließen. In diesem Fall werden die übersetzten Assets zu dem Zielordner hinzugefügt, der bereits zuvor übersetzte Assets enthält. Je nach Auswahl der Optionen wird ein Übersetzungsprojekt erstellt oder ein vorhandenes Übersetzungsprojekt für die neuen Assets aktualisiert. Der Workflow Sprachkopien aktualisieren umfasst die folgenden Optionen:

* Erstellen eines neuen Übersetzungsprojekts
* Hinzufügen zu einem vorhandenen Übersetzungsprojekt

### Erstellen eines neuen Übersetzungsprojekts {#create-a-new-translation-project-1}

Wenn Sie diese Option verwenden, wird ein Übersetzungsprojekt für die Gruppe von Assets erstellt, für die Sie eine Sprachkopie aktualisieren möchten.

1. Wählen Sie in der Assets-Benutzeroberfläche den Quellordner aus, dem Sie ein Asset hinzugefügt haben.
1. Öffnen Sie den Bereich **[!UICONTROL Referenzen]** und tippen/klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**, um die Liste der Sprachkopien anzuzeigen.
1. Aktivieren Sie das Kontrollkästchen vor **[!UICONTROL Sprachkopien]** und wählen Sie dann den Zielordner aus, der dem entsprechenden Gebietsschema entspricht.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Klicken/tippen Sie am unteren Rand auf **[!UICONTROL Sprachkopien aktualisieren]**.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Neues Übersetzungsprojekt erstellen]**.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. Geben Sie im Feld **[!UICONTROL Projekttitel]** einen Namen für das Projekt ein.

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Klicken/tippen Sie auf **[!UICONTROL Start]**.
1. Gehen Sie zur Projektekonsole. Der Übersetzungsordner wird in die Projektekonsole kopiert.

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Öffnen Sie den Ordner, um das Übersetzungsprojekt anzuzeigen.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. Klicken/tippen Sie auf das Projekt, um die Detailseite zu öffnen.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Um die Übersetzung der Assets zu starten, klicken Sie auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf den Pfeil und wählen Sie aus der Liste die Option **[!UICONTROL Start]**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   Eine Meldung informiert Sie darüber, dass mit der Ausführung des Übersetzungsauftrags begonnen wird.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken/tippen Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen.

   ![chlimage_1-93](assets/chlimage_1-93.png)

   Weitere Informationen zum Auftragsstatus finden Sie unter [Überwachen des Status eines Übersetzungsauftrags](../sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Navigieren Sie zur Assets-Benutzeroberfläche und öffnen Sie die Seite Eigenschaften für jedes der übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

### Hinzufügen zu einem vorhandenen Übersetzungsprojekt {#add-to-existing-translation-project-1}

Wenn Sie diese Option verwenden, wird die Gruppe der Assets zu einem vorhandenen Übersetzungsprojekt hinzugefügt, um die Sprachkopien für das von Ihnen gewählte Gebietsschema zu aktualisieren.

1. Wählen Sie in der Assets-Benutzeroberfläche den Quellordner aus, dem Sie einen Asset-Ordner hinzugefügt haben.
1. Öffnen Sie den Bereich **[!UICONTROL Verweise]** und klicken/tippen Sie auf **[!UICONTROL Sprachkopien]** unter **[!UICONTROL Kopien]**, um die Liste der Sprachkopien anzuzeigen.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Sprachkopien]**, um alle Sprachkopien auszuwählen. Heben Sie die Auswahl anderer Kopien auf. Nur die Sprachkopien, die den gewünschten Gebietsschemata entsprechen, sollten ausgewählt bleiben.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Klicken/tippen Sie am unteren Rand auf **[!UICONTROL Sprachkopien aktualisieren]**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]**.

   ![chlimage_1-97](assets/chlimage_1-97.png)

1. Wählen Sie aus der Liste **[!UICONTROL Vorhandenes Übersetzungsprojekt]** ein Projekt, dem das zu übersetzende Asset hinzugefügt werden soll.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. Klicken/tippen Sie auf **[!UICONTROL Start]**.
1. Führen Sie Schritt 9 bis 14 des Verfahrens [Zu vorhandenem Übersetzungsprojekt hinzufügen](translation-projects.md#add-to-existing-translation-project) aus, um den Vorgang abzuschließen.

## Erstellen temporärer Sprachkopien {#creating-temporary-language-copies}

Wenn Sie einen Übersetzungs-Workflow ausführen, um eine Sprachkopie mit bearbeiteten Versionen der ursprünglichen Assets zu aktualisieren, wird die vorhandene Sprachkopie beibehalten, bis Sie die übersetzten Assets genehmigen. [!DNL Experience Manager] Assets speichert die neu übersetzten Assets an einem temporären Speicherort und aktualisiert die vorhandene Sprachkopie, nachdem Sie die Assets explizit genehmigt haben. Wenn Sie die Assets ablehnen, bleibt die Sprachkopie unverändert.

1. Tippen/Klicken Sie unter **[!UICONTROL Sprachkopien]**, für die Sie bereits eine Sprachkopie erstellt haben, auf den Quellstammordner und dann auf **[!UICONTROL In Assets anzeigen]**, um den Ordner in Assets zu öffnen.[!DNL Experience Manager]

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Wählen Sie in der Assets-Benutzeroberfläche ein bereits übersetztes Asset aus und klicken/tippen Sie auf die **[!UICONTROL Bearbeiten]** in der Symbolleiste, um das Asset im Bearbeitungsmodus zu öffnen.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. Bearbeiten Sie das Asset und speichern Sie die Änderungen.
1. Führen Sie Schritt 2 bis 14 des Verfahrens [Zu vorhandenem Übersetzungsprojekt hinzufügen](#add-to-existing-translation-project) aus, um die Sprachkopie zu aktualisieren.
1. Klicken/tippen Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen. Der Liste der Assets auf der Seite **[!UICONTROL Übersetzungsauftrag]** können Sie den temporären Speicherort der übersetzten Version des Assets entnehmen.

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. Aktivieren Sie das Kontrollkästchen neben **[!UICONTROL Titel]**.
1. Klicken/tippen Sie in der Symbolleiste auf **[!UICONTROL Übersetzung bestätigen]** und dann im Dialogfeld auf **[!UICONTROL Annehmen]**, um das übersetzte Asset im Zielordner mit der übersetzten Version des bearbeiteten Assets zu überschreiben.

   ![chlimage_1-102](assets/chlimage_1-102.png)

   >[!NOTE]
   >
   >Damit der Übersetzungs-Workflow die Ziel-Assets aktualisieren kann, akzeptieren Sie sowohl das Asset als auch die Metadaten.

   Klicken/tippen Sie auf **[!UICONTROL Übersetzung ablehnen]**, um die ursprünglich übersetzte Version des Assets im Zielgebietsschema-Stamm beizubehalten und die bearbeitete Version abzulehnen.

   ![chlimage_1-103](assets/chlimage_1-103.png)

1. Navigieren Sie zur Konsole „Assets“ und öffnen Sie die Seite mit den Eigenschaften für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

Tipps zum effizienten Übersetzen von Metadaten finden Sie auf dieser archivierten Seite über [5 Schritte zur effizienten Übersetzung von Metadaten](https://web.archive.org/web/20181217033517/https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/).
