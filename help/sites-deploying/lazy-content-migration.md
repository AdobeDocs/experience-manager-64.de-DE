---
title: Lazy-Content-Migration
seo-title: Lazy Content Migration
description: Erfahren Sie mehr über die Migration verzögerter Inhalte in AEM 6.4.
seo-description: Learn about Lazy Content Migration in AEM 6.4.
uuid: 9c84f7fe-31d3-4b63-8975-9e75a6c44b7d
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 282a828a-edb2-4643-9bf7-ec30c29dc6ce
feature: Upgrading
exl-id: 8dc2dfb8-037f-40ae-a962-ced89dd3fdd0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 19%

---

# Lazy-Content-Migration{#lazy-content-migration}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Aus Gründen der Abwärtskompatibilität, des Inhalts und der Konfiguration in **/etc** und **/content** Ab AEM 6.3 wird bei der Aktualisierung nicht sofort berührt oder umgewandelt. Dies geschieht, um sicherzustellen, dass die Abhängigkeiten von Kundenanwendungen von diesen Strukturen intakt bleiben. Die Funktionalität für diese Inhaltsstrukturen ist weiterhin identisch, auch wenn der Inhalt in einer vordefinierten AEM 6.4 an einem anderen Ort gehostet wird.

Auch wenn nicht alle dieser Standorte automatisch umgewandelt werden können, gibt es einige Verzögerungen `CodeUpgradeTasks` auch als &quot;Lazy Content Migration&quot;bezeichnet. Kunden können diese automatischen Umwandlungen auslösen, indem sie die Instanz mit der folgenden Systemeigenschaft neu starten:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Dadurch wird während der Migration `CodeUpgradeTasks` ausgeführt.

Das Ziel ist zwar eine effiziente Ausführung, aber dieser Aktualisierungsprozess ist synchron und führt daher abhängig von der Menge des zu verarbeitenden Inhalts zu Ausfallzeiten. Es wird empfohlen, die Ausführungszeiten in einer Staging-Umgebung vor einem Produktionssystem zu bewerten, um ein entsprechendes Wartungsfenster zu planen.

Da dies normalerweise auch eine Anpassung der Anwendung erfordert, sollte diese Aktivität zusammen mit der entsprechenden Anwendungsbereitstellung durchgeführt werden.

Nachfolgend finden Sie eine vollständige Liste aller in Version 6.4 eingeführten `CodeUpgradeTasks`:

| **Name** | **Relevant für AEM Versionen vor** | **Migrationstyp  ** | **Details** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Unmittelbar |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Unmittelbar | Ermittelt alle `LiveRelationShips` aus `VersionStorage`, die gelöscht wurden, und fügt die Ausschlusseigenschaft zum übergeordneten Element hinzu. |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Unmittelbar | Strukturiert Cloud-Dienste für die standardmäßige sichere Einrichtung um |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Unmittelbar | Entfernt eigenschaftsbasierte Verknüpfungen aus **/content** nach **/conf** (ersetzt durch den OSGi-Mechanismus) generiert die entsprechende OSGi-Konfiguration |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Unmittelbar | Aufgrund der Verarbeitung von merge_preserve überschreibt die standardmäßig sichere Ablehnungsregel die erteilten Berechtigungen, was dazu führt, dass bei der Aktualisierung neu angeordnet werden muss |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Unmittelbar | Erkennt Komponenten, die das Widget Html5SmartFile verwenden, sucht nach der Verwendung der Komponente im Inhalt und strukturiert die Persistenz neu, indem die Binärdatei auf einer Ebene nach unten verschoben und nicht auf Komponentenebene gespeichert wird. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Unmittelbar | Verschiebt alte Stilprojekte aus **/etc/projects** nach **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Unmittelbar | Führt eine Containerschicht in die Hierarchie (Bereiche) ein und passt Verweise an. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Unmittelbar | Legt feste Ortsnamen für Zielkomponenten fest. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Unmittelbar | Komplexe Transformation von Workflow-Modellen, die aus 6.2-Strukturen, Instanzen, Benachrichtigungen bestehen und dann vom Backup-Speicherort aus zusammenführen **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt Assets, benutzerdefinierte Metadatenschemata und Verarbeitungsprofile aus **/apps** nach **/conf** und übersetzt das Metadatenschema und die Metadatenprofilformulare von coral2 in coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt Assets und benutzerdefinierte Suchfacetten aus **/apps** nach **/conf** und übersetzt das Metadatenschema und die Metadatenprofilformulare von coral2 in coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Unmittelbar | Aktualisiert InboxItems für die Sortierung von Inbox-Elementen (Anpassen von Metadaten für eine effiziente Sortierung) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Unmittelbar | Passt die Eigenschaft metadataSchema im Ordner an, indem relative Pfade zu **/conf** anstelle von **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Unmittelbar | Anpassen der Navigationsstruktur |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt benutzerdefinierte Konfigurationen für die Überwachungs-Dashboards aus **/libs** und **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Unmittelbar | Übersetzt die Eigenschaft processingProfile (bis 6.1 verwendet) in Assets, um mit der Struktur 6.3 und höher abzugleichen. Passt außerdem die relativen Pfade des Profils an **/conf** anstelle von **/apps**. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Unmittelbar | Aktualisierungsaufgabe, die veraltete Menüeinträge in CRXDE Lite und Web-Konsole bei einem Upgrade entfernt. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Verzögert | Verschieben von SRP-Cloud-Konfigurationen, Konfigurationen von Community-Schlagwörtern, Bereinigung **/etc/social** und **/etc/enablement** (alle Verweise und Daten müssen angepasst werden, wenn die Lazy Migration ausgeführt wird - von dieser Struktur sollte kein Anwendungsteil mehr abhängig sein). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Verzögert | Bereinigungen **/etc/cloudsettings** (enthält ContextHub-Konfiguration). Die Konfiguration wird beim ersten Zugriff automatisch migriert. Falls die Migration verzögerter Inhalte zusammen mit der Aktualisierung dieses Inhalts in gestartet wird **/etc/cloudsettings** muss vor der Aktualisierung über das -Paket erhalten und neu installiert werden, damit die implizite Umwandlung eintritt, zusammen mit einer nachfolgenden Deinstallation des Pakets nach Abschluss. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Verzögert | Passt die alte Titelstruktur an den Titel im Benutzerprofilknoten an. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Verzögert | Migrieren von Commerce-Inhalten aus **/etc/commerce** nach **/var/commerce**. Während der Migration werden Inhalte verschoben und Verweise auf verschobene Inhalte aktualisiert, um den neuen Speicherort widerzuspiegeln. |
