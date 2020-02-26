---
title: Datenauslösende Asset-Änderung
seo-title: Datenauslösende Asset-Änderung
description: In diesem Verwendungsfallbeispiel erfahren Sie, wie Sie personalisierte Inhalte basierend auf bestimmten Voraussetzungen (z. B. Wetter Ihres Standorts) erzielen.
seo-description: In diesem Verwendungsfallbeispiel erfahren Sie, wie Sie personalisierte Inhalte basierend auf bestimmten Voraussetzungen (z. B. Wetter Ihres Standorts) erzielen.
uuid: 8e557e4c-a6e2-4e4a-87bd-e01e2ff0043d
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: example
topic-tags: use-case-examples
discoiquuid: 878a2354-0990-4b21-b1ab-b9b33b50e353
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Datenauslösende Asset-Änderung{#data-triggered-asset-change}

## Nutzungsszenario – Beschreibung {#use-case-description}

In diesem Verwendungsfallbeispiel wird beschrieben, wie Sie personalisierte Inhalte basierend auf dem Wetter Ihres Standorts erzielen.

Das folgende AEM Screens-Projekt nutzt die AEM-Personalisierung, zu der ContextHub, die Segmentierungsengine und die Benutzeroberfläche für das Content-Targeting gehören.

Dieser Anwendungsfall liefert Inhalte, die auf der Grundlage des aktuellen Wetters an jedem Standort personalisiert werden, wenn das Wetter:

* *Sonnig, es zeigt Sommerkleidung*
* *kalt, es zeigt Winterkleidung*

>[!NOTE]
>
>Zu Demonstrationszwecken erfasst dieser Anwendungsfall Ihren Geo-Standort, um die Inhaltsaktualisierung zu präsentieren. Sie können die Geo-Position der Ausgabe manuell in verschiedenen Szenarien aktualisieren.

### Voraussetzungen {#preconditions}

Bevor Sie mit diesem Anwendungsfall beginnen, sollten Sie Folgendes wissen:

* [Personalisierung   ](/help/sites-administering/personalization.md)
* [Konfigurieren von ContextHub](/help/sites-administering/contexthub-config.md)
* [Konfigurieren der Segmentierung mit ContextHub](/help/sites-administering/segmentation.md)
* [Verfassen zielgerichteter Inhalte im Targeting-Modus](/help/sites-authoring/content-targeting-touch.md)

### Hauptakteure {#primary-actors}

Autoren von Inhalten

## Grundlegender Ablauf: Einrichten des Projekts {#basic-flow-setting-up-the-project}

Führen Sie die folgenden Schritte aus, um ein Projekt einzurichten, das die durch die Datenausgabe ausgelösten Asset-Änderungen darstellt:

1. Create an AEM Screens Project named as **DataTriggerAsset**, as shown below.

   ![screen_shot_2019-02-28at120427pm](assets/screen_shot_2019-02-28at120427pm.png)

1. **Erstellen eines Sequenzkanals**

   1. Wählen Sie den Ordner **Kanäle** aus und klicken Sie auf **Erstellen**, um den Assistenten zum Erstellen eines Kanals zu öffnen.
   1. Select **Sequence Channel** from the wizard and create the channel titled as **DataTrigger**.
   ![screen_shot_2019-02-28at120710pm](assets/screen_shot_2019-02-28at120710pm.png)

1. **Hinzufügen von Inhalten zu Sequenzkanälen**

   1. Select the channel **DataTrigger**.
   1. Klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Editor zu öffnen. Ziehen Sie einige Assets in Ihren Kanal.
   ![screen_shot_2019-02-28at21511pm](assets/screen_shot_2019-02-28at21511pm.png)

   >[!NOTE]
   >
   >Sie dürfen dem Editor nur die Standardbilder hinzufügen. Die Bilder, die Sie ersetzen möchten, müssen dem Editor hinzugefügt werden, wenn Sie in Schritt 6 zum Targeting-Modus wechseln.

1. **ContextHub- und Targeting-Konfigurationen festlegen**

   1. Navigieren Sie zu **DataTriggerAsset** —> **Kanäle** —> **DataTrigger** und klicken Sie in der Aktionsleiste auf **Eigenschaften** .
   1. Klicken Sie auf die Registerkarte **Personalisierung** .
   ![screen_shot_2019-02-28at10644pm](assets/screen_shot_2019-02-28at10644pm.png)

1. **Hinzufügen von ContextHub- und Targeting-Konfigurationen**

   1. Für Demozwecke laden Sie das unten stehende Inhaltspaket herunter.
   1. Nachdem Sie das Paket auf Ihre AEM-Instanz heruntergeladen haben, müssen Sie den ContextHub- und den Segmentpfad festlegen:
   * Legen Sie für **ContextHub** den Pfad wie folgt fest: ***/libs/settings/cloudsettings/legacy/contexthub***
   * Legen Sie für **Segmentpfad** den Pfad wie folgt fest: ***/conf/data-Trigger/settings/wcm/segments***
   Datenauslöser

   [Datei laden](assets/data-triggers-1_00.zip)

   >[!NOTE]
   >
   >Weitere Informationen zum Konfigurieren von ContextHub und Segmentierung finden Sie unter:
   >
   >* [Konfigurieren von ContextHub](/help/sites-administering/contexthub-config.md)
   >* [Konfigurieren der Segmentierung mit ContextHub](/help/sites-administering/segmentation.md)


   ![screen_shot_2019-02-28at31502pm](assets/screen_shot_2019-02-28at31502pm.png)

   Klicken Sie auf **Speichern und schließen**.

1. **Wechseln in den Modus „Targeting“**

   1. Navigieren Sie zu **DataTriggerAsset** > **Kanäle** > **DataTrigger** und klicken Sie in der Aktionsleiste auf **Bearbeiten** .
   1. Wählen Sie **Targeting** aus der Menüleiste unter **Bearbeiten**.
   ![screen_shot_2019-02-28at21849pm](assets/screen_shot_2019-02-28at21849pm.png)

1. **Hinzufügen des zielgerichteten Inhalts**

   1. Wählen Sie **Datenauslöser** in **BRAND** und **Saisonale Datenauslöser **in **AKTIVITÄT**.
   1. Click the **Start Targeting**
   ![screen_shot_2019-02-28at31953pm](assets/screen_shot_2019-02-28at31953pm.png)

1. **Definieren der Zielkomponente**

   1. Wählen Sie die Komponente aus, für die Sie zielgerichteten Inhalt haben möchten.
   1. Klicken Sie auf die Schaltfläche **Target** , um das Targeting für diese Komponente zu aktivieren.
   1. Definieren Sie den Inhalt für jede Variation, indem Sie die Variation in den **Zielgruppen** in der Seitenleiste auswählen und den Inhalt nach Bedarf anpassen.
   >[!NOTE]
   >
   >Um das Bedienfeld &quot; **Assets** &quot;im Editor auszublenden, müssen Sie auf den Pfeil nach links im rechten Bedienfeld klicken, wie in der Abbildung unten dargestellt.

   ![target](assets/target.gif)

## Anzeigen der Ergebnisse {#viewing-the-results}

Nachdem Sie die vorhergehenden Schritte ausgeführt haben, führen Sie die folgenden Schritte aus, um die Ergebnisse in der Vorschau anzuzeigen und anzuzeigen:

1. Klicken Sie im Editor auf **Vorschau** .

   ![target2](assets/target2.gif)

1. Um zu zeigen, wie sich das Bild ändert, je nach Position und Temperatur Ihres Bereichs, können Sie manuell auf das ContextHub-Symbol klicken, wie unten dargestellt.

   Sobald Sie die Position aktualisieren, wird die Temperatur in diesem Bereich erfasst und das Bild wird mit der Winterauswahl aktualisiert und ersetzt das Sommerklickbild.

   ![target3](assets/target3.gif)

