---
title: Asset-Workflow-Offloader
seo-title: Assets Workflow Offloader
description: Erfahren Sie mehr über den Asset Workflow-Offloader.
seo-description: Learn about the Assets Workflow Offloader.
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
exl-id: 2ca8e786-042b-44f6-ac60-834eca64f79f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 3%

---

# Asset-Workflow-Offloader{#assets-workflow-offloader}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit dem Assets-Workflow-Offloader können Sie mehrere Instanzen von Adobe Experience Manager (AEM) Assets aktivieren, um die Verarbeitungslast auf der primären (führenden) Instanz zu reduzieren. Die Verarbeitungslast wird auf die führende Instanz und die verschiedenen Offloader-Instanzen (Worker) verteilt, die Sie ihr hinzufügen. Die Verteilung der Verarbeitungslast von Assets erhöht die Effizienz und Geschwindigkeit, mit der AEM Assets Assets verarbeitet. Darüber hinaus hilft es bei der Zuordnung dedizierter Ressourcen zur Verarbeitung von Assets eines bestimmten MIME-Typs. Sie können beispielsweise einen bestimmten Knoten in Ihrer Topologie nur der Verarbeitung von InDesign-Assets zuweisen.

## Konfigurieren der Offloader-Topologie {#configure-offloader-topology}

Verwenden Sie Configuration Manager, um die URL für die führende Instanz und die Hostnamen der Offloader-Instanzen für Verbindungsanfragen in der führenden Instanz hinzuzufügen.

1. Tippen/klicken Sie auf das AEM-Logo und wählen Sie **Instrumente** > **Aktivitäten** > **Web-Konsole** , um Configuration Manager zu öffnen.
1. Wählen Sie in der Web-Konsole **Sling** >  **Topologieverwaltung**.

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Tippen/klicken Sie auf der Seite &quot;Topologieverwaltung&quot;auf die **Konfigurieren des Discovery.Oak-Dienstes** Link.

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. Geben Sie auf der Seite &quot;Konfiguration des Discovery-Dienstes&quot;die Connector-URL für die führende Instanz im **Topologie-Connector-URLs** -Feld.

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. Im **Whitelist zum Topologie-Connector** -Feld IP-Adresse oder Hostnamen der Offloader-Instanzen angeben, die eine Verbindung mit der führenden Instanz herstellen dürfen. Tippen oder klicken Sie auf **Speichern**.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. Um die Offloader-Instanzen anzuzeigen, die mit der führenden Instanz verbunden sind, gehen Sie zu **Instrumente** > **Implementierung** > **Topologie** und tippen/klicken Sie auf die Cluster-Ansicht.

## Abladung deaktivieren {#disable-offloading}

1. Tippen/klicken Sie auf das AEM-Logo und wählen Sie **Instrumente** > **Implementierung** > **Abladung**. Die **Browser-Abladung** Seite zeigt Themen und die Serverinstanzen an, die die Themen nutzen können.

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. Deaktivieren Sie die *com/adobe/granite/workflow/offloading* Thema auf den führenden Instanzen, mit denen Benutzer interagieren, um AEM Assets hochzuladen oder zu ändern.

   ![chlimage_1-49](assets/chlimage_1-49.png)

## Konfigurieren von Workflow-Startern auf der führenden Instanz {#configure-workflow-launchers-on-the-leader-instance}

Konfigurieren von Workflow-Startern für die Verwendung der **DAM-Update-Asset-Abladung** Workflow auf der führenden Instanz anstelle der **DAM-Update-Asset** Arbeitsablauf.

1. Tippen/klicken Sie auf das AEM-Logo und wählen Sie **Instrumente** > **Workflow** > **Starter** , um **Workflow-Starter** Konsole.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. Suchen Sie die beiden Starter-Konfigurationen mit dem Ereignistyp . **Knoten erstellt** und **Knoten geändert** , die die **DAM-Update-Asset** Arbeitsablauf.
1. Aktivieren Sie für jede Konfiguration das Kontrollkästchen davor und tippen/klicken Sie auf die **Eigenschaften anzeigen** Symbol in der Symbolleiste, um die **Starter-Eigenschaften** angezeigt.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Aus dem **Workflow** Liste, wählen Sie **DAM-Update-Asset-Abladung** und tippen/klicken **Speichern**.

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. Tippen/klicken Sie auf das AEM-Logo und wählen Sie **Instrumente** > **Workflow** > **Modelle** , um **Workflow-Modelle** Seite.
1. Wählen Sie die **DAM-Update-Asset-Abladung** Workflow und tippen/klicken Sie **Bearbeiten** aus der Symbolleiste, um die Details anzuzeigen.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Anzeigen des Kontextmenüs für **DAM-Workflow-Abladung** und wählen Sie **Bearbeiten**. Überprüfen Sie den Eintrag im **Auftragsthema** des **Generische Argumente** im Konfigurationsdialogfeld.

   ![chlimage_1-54](assets/chlimage_1-54.png)

## Deaktivieren der Workflow-Starter für die Offloader-Instanzen {#disable-the-workflow-launchers-on-the-offloader-instances}

Deaktivieren Sie die Workflow-Starter, die die **DAM-Update-Asset** Workflow in der Leader-Instanz.

1. Tippen/klicken Sie auf das AEM-Logo und wählen Sie **Instrumente** > **Workflow** > **Starter** , um **Workflow-Starter** Konsole.

   ![chlimage_1-55](assets/chlimage_1-55.png)

1. Suchen Sie die beiden Starter-Konfigurationen mit dem Ereignistyp . **Knoten erstellt** und **Knoten geändert** , die die **DAM-Update-Asset** Arbeitsablauf.
1. Aktivieren Sie für jede Konfiguration das Kontrollkästchen davor und tippen/klicken Sie auf die **Eigenschaften anzeigen** Symbol in der Symbolleiste, um die **Starter-Eigenschaften** angezeigt.

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. Ziehen Sie im Bereich &quot;Aktivieren&quot;den Regler, um den Workflow-Starter zu deaktivieren, und tippen/klicken Sie auf . **Speichern** , um sie zu deaktivieren.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Laden Sie alle Assets vom Typ &quot;Bild&quot;in die führende Instanz hoch. Überprüfen Sie die Miniaturansichten, die von der abgeladenen Instanz für das Asset generiert und zurückportiert wurden.
