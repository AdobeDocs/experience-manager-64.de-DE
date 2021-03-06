---
title: Lazy-Content-Migration
seo-title: Lazy Content Migration
description: Erfahren Sie mehr über die Lazy-Content-Migration in AEM 6.4.
seo-description: Learn about Lazy Content Migration in AEM 6.4.
uuid: 9c84f7fe-31d3-4b63-8975-9e75a6c44b7d
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 282a828a-edb2-4643-9bf7-ec30c29dc6ce
feature: Upgrading
exl-id: 8dc2dfb8-037f-40ae-a962-ced89dd3fdd0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 96%

---

# Lazy-Content-Migration{#lazy-content-migration}

Aus Gründen der Abwärtskompatibilität werden Content und Konfigurationen in **/etc** und **/content** ab AEM 6.3 bei der Aktualisierung nicht sofort behandelt oder konvertiert. Damit wird sichergestellt, dass Abhängigkeiten in Kundenanwendungen von diesen Strukturen intakt bleiben. Die zu diesen Content-Strukturen gehörende Funktionalität bleibt unverändert, auch wenn der AEM 6.4-Inhalt an einem anderen Speicherort gehostet wird.

Möglicherweise können nicht alle Speicherorte automatisch umgewandelt werden. Es gibt aber auch einige verzögerte `CodeUpgradeTasks`, die auch als Lazy-Content-Migration bezeichnet werden. Kunden können diese automatischen Umwandlungen auslösen, indem sie die Instanz mit der folgenden Systemeigenschaft neu starten:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Dadurch wird während der Migration `CodeUpgradeTasks` ausgeführt.

Auch wenn eine effiziente Durchführung angestrebt wird, ist dieser Aktualisierungsprozess synchron und erfordert daher eine Ausfallzeit, die vom Umfang des Contents abhängt, der verarbeitet werden muss. Es empfiehlt sich, die Ausführungszeiten in einer Stagingumgebung zu ermitteln, bevor die Durchführung im Produktionssystem erfolgt, um ein passendes Wartungsfenster planen zu können.

Da hierbei in der Regel auch die Anwendung angepasst werden muss, sollte diese Aktivität zusammen mit der entsprechenden Anwendungsbereitstellung durchgeführt werden.

Nachfolgend finden Sie eine vollständige Liste aller in Version 6.4 eingeführten `CodeUpgradeTasks`:

| **Name** | **Relevant für AEM-Versionen vor**  | **Migrationstyp**  | **Details** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Unmittelbar |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Unmittelbar | Ermittelt alle `LiveRelationShips` aus `VersionStorage`, die gelöscht wurden, und fügt die Ausschlusseigenschaft zum übergeordneten Element hinzu. |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Unmittelbar | Strukturiert Cloudservices für ein standardmäßig sicheres Setup um. |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Unmittelbar | Entfernt auf Eigenschaften basierende Verknüpfungen von **/content** mit **/conf** (wird durch den OSGi-Mechanismus ersetzt), generiert die entsprechende OSGi-Konfiguration. |
| `Cq62FormsContentUpgrade` | &lt; 6,2 | Unmittelbar | Aufgrund der merge_preserve-Behandlung überschreibt die Ablehnungsregel für die standardmäßige Sicherheit vorhandene Berechtigungen, die bei der Aktualisierung neu angeordnet werden müssen. |
| `CQ62Html5SmartFileUpgrade` | &lt; 6,2 | Unmittelbar | Ermittelt Komponenten, die das Html5SmartFile-Widget verwenden, sucht nach der Verwendung der Komponenten im Inhalt und strukturiert die Persistenz neu, indem die Binärdatei um eine Ebene nach unten verschoben und nicht auf Komponentenebene gespeichert wird. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6,2 | Unmittelbar | Verschiebt alte Projekte aus **/etc/projects** in **/content/projects**  |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6,2 | Unmittelbar | Erstellt eine Containerebene in der Hierarchie (Bereiche) und passt Verweise an. |
| `Cq62TargetContentUpgrade` | &lt; 6,2 | Unmittelbar | Legt feste Speicherortnamen für Zielkomponenten fest. |
| `Cq62WorkflowContentUpgrade` | &lt; 6,2 | Unmittelbar | Komplexe Umwandlung von Strukturen, Instanzen, Benachrichtigungen von Workflow-Modellen vor 6.2 und anschließendes erneutes Zusammenführen vom Sicherungsordner aus **/var/backup**  |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt Assets, benutzerdefinierte Metadaten-Schemata und Verarbeitungsprofile aus **/apps** in **/conf** und überführt das Metadatenschema und Metadatenprofilformulare von coral2 in coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6,3 | Unmittelbar | Verschiebt Assets und benutzerdefinierte Suchfacetten aus **/apps** in **/conf** und überführt das Metadatenschema und Metadatenprofilformulare von coral2 in coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6,3 | Unmittelbar | Aktualisiert InboxItems für die Sortierung von Posteingangselementen (Anpassen der Metadaten für eine effiziente Sortierung). |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6,3 | Unmittelbar | Passt die metadataSchema-Eigenschaft für Ordner an, indem relative Pfade zu **/conf** statt zu **/apps** führen. |
| `CQ63MobileAppsNavUpgrade` | &lt; 6,3 | Unmittelbar | Anpassen der Navigationsstruktur. |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6,3 | Unmittelbar | Verschiebt benutzerdefinierte Konfigurationen für die Überwachungs-Dashboards von **/libs** und **/apps**.  |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6,3 | Unmittelbar | Passt die processingProfile-Eigenschaft (wurde bis 6.1 verwendet) in Assets an die ab 6.3 verwendete Struktur an. Passt außerdem die relativen Pfade des Profils an, die zu **/conf** statt zu **/apps** führen. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6,3 | Unmittelbar | Aktualisierungsaufgabe, die bei einem Upgrade veraltete Menüeinträge aus CRXDE Lite und der Web-Konsole entfernt. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6,3 | Verzögert | Verschiebt SRP-Cloudkonfigurationen, Community-Schlagwortkonfigurationen, bereinigt **/etc/social** und **/etc/enablement** (alle Verweise und Daten müssen angepasst werden, wenn die Lazy-Migration ausgeführt wird – es dürfen keine Anwendungsteile weiterhin von dieser Struktur abhängig sein). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Verzögert | Bereinigt **/etc/cloudsettings** (enthält die ContextHub-Konfiguration). Die Konfiguration wird beim ersten Zugriff automatisch migriert. Für den Fall, dass die Lazy-Content-Migration zusammen mit der Aktualisierung gestartet wird, muss vor der Aktualisierung der Inhalt in **/etc/cloudsettings** über ein Paket gesichert und dann erneut installiert werden, damit die implizite Umwandlung stattfindet und das Paket nach Abschluss deinstalliert wird. |
| `CQ64UsersTitleFixTask` | &lt; 6,4 | Verzögert | Passt die alte Titelstruktur an den Titel im Benutzerprofilknoten an. |
| `CQ64CommerceMigrationTask` | &lt; 6,4 | Verzögert | Migrieren von Commerce-Inhalten aus **/etc/commerce** nach **/var/commerce**. Während der Migration werden Inhalte verschoben und Verweise auf verschobene Inhalte werden aktualisiert, um den neuen Speicherort widerzuspiegeln. |
