---
title: Best Practices für die Assets-Abladung
description: Empfohlene Anwendungsfälle und Best Practices für die Abladung der Workflows zur Asset-Aufnahme und -Replikation in AEM Assets.
contentOwner: AG
feature: Asset-Verwaltung
role: Business Practitioner,Administrator
exl-id: 3ecc8988-add1-47d5-80b4-984beb4d8dab
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1820'
ht-degree: 78%

---

# Best Practices für die Assets-Abladung {#assets-offloading-best-practices}

>[!WARNING]
>
>Diese Funktion wird ab AEM 6.4 nicht mehr unterstützt und in AEM 6.5 entfernt. Planen Sie entsprechend.

Durch die Verarbeitung großer Dateien und Ausführung von Workflows in Adobe Experience Manager (AEM) Assets kann ein erheblicher Teil von CPU, Speicher und I/O-Ressourcen in Beschlag genommen werden. Insbesondere die Größe der Assets, die Workflows, die Anzahl der Benutzer und die Häufigkeit der Asset-Aufnahme können sich auf die Gesamtleistung des Systems auswirken. Zu den ressourcenintensivsten Vorgängen gehören die AEM-Workflows zur Asset-Aufnahme und Replikation. Eine intensive Nutzung dieser Workflows in einer AEM-Autoreninstanz kann die Bearbeitungseffizienz beeinträchtigen.

Werden diese Aufgaben auf dedizierte Worker-Instanzen abgeladen, kann sich der CPU-, Speicher- und I/O-Mehraufwand reduzieren. Im Allgemeinen lautet die Idee hinter der Abladung, dass Aufgaben mit hohem CPU-/Speicher-/Ressourcenverbrauch auf dedizierte Worker-Instanzen verteilt werden. In den folgenden Abschnitten werden empfohlene Anwendungsbeispiele für die Assets-Abladung beschrieben.

## AEM Assets-Abladung {#aem-assets-offloading}

AEM Assets implementiert eine native Asset-spezifische Workflow-Erweiterung zur Abladung. Als Basis dient hierbei die generische Workflow-Erweiterung des Abladeframeworks, wobei allerdings zusätzliche Asset-spezifische Funktionen in der Implementierung enthalten sind. Das Ziel der Assets-Abladung besteht darin, den Workflow „DAM-Update-Asset“ auf einem hochgeladenen Asset effizient auszuführen. Mittels Assets-Abladung erlangen Sie eine größere Kontrolle über die Aufnahmeworkflows.

## Komponenten der AEM Assets-Abladung {#aem-assets-offloading-components}

Die folgende Abbildung zeigt die Hauptkomponenten des Asset-Abladeprozesses:

![chlimage_1-55](assets/chlimage_1-55.png)

### Workflow „Asset-Abladung für DAM-Update“{#dam-update-asset-offloading-workflow}

Der Workflow &quot;Asset-Abladung für DAM-Update&quot;wird auf dem primären (Autoren-)Server ausgeführt, auf den der Benutzer die Assets hochlädt. Dieser Workflow wird von einem regulären Workflowstarter ausgelöst. Statt das hochgeladene Asset zu verarbeiten, erstellt der Abladeworkflow einen neuen Auftrag mit dem Thema *com/adobe/granite/workflow/offloading*. Der Abladeworkflow fügt den Namen des Zielworkflows – in diesem Fall den DAM-Update-Asset-Workflow – und den Pfad des Assets der Nutzlast des Auftrags hinzu. Nach Erstellung des Abladeauftrags wartet der Ablade-Workflow auf der primären Instanz, bis der Abladeauftrag ausgeführt wurde.

### Job Manager {#job-manager}

Der Job Manager verteilt neue Aufträge an Worker-Instanzen. Beim Design des Verteilungsmechanismus muss an die Themenaktivierung gedacht werden. Aufträge können Instanzen nur dann zugewiesen werden, wenn das Thema des entsprechenden Auftrags aktiviert ist. Deaktivieren Sie das Thema `com/adobe/granite/workflow/offloading` auf der primären INstanz und aktivieren Sie es auf dem Worker, um sicherzustellen, dass der Auftrag dem Worker zugewiesen ist.

### AEM-Abladung {#aem-offloading}

Das Abladeframework identifiziert Aufträge zur Workflow-Abladung, die Worker-Instanzen zugewiesen sind, und transportiert diese physisch, einschließlich Nutzlast (etwa aufzunehmende Bilder), an Worker. 

### Job Consumer „Workflow-Abladung“  {#workflow-offloading-job-consumer}

Sobald ein Auftrag auf den Worker geschrieben wurde, ruft der Job Manager den Job Consumer auf, der für das Thema *com/adobe/granite/workflow/offloading* verantwortlich ist. Der Job Consumer führt dann den Workflow „DAM-Update-Asset“ auf dem Asset aus.

## Sling-Topologie {#sling-topology}

Die Sling-Topologie gruppiert AEM-Instanzen und ermöglicht deren gegenseitige Erkennung, und zwar unabhängig von der zugrundeliegenden Persistenz. Dank dieser Eigenschaft der Sling-Topologie können Sie Topologien für Nicht-Cluster-, Cluster- und Mischszenarien erstellen. Eine Instanz kann Eigenschaften gegenüber der gesamten Topologie offenlegen. Das Framework bietet Callbacks für das Listening auf Änderungen in der Topologie (Instanzen und Eigenschaften). Die Sling-Topologie bildet die Grundlage für Sling-verteilte Aufträge.

### Sling-verteilte Aufträge  {#sling-distributed-jobs}

Sling-verteilte Aufträge vereinfachen die Verteilung von Aufträgen unter Instanzen, die zur Topologie gehören. Sling-Aufträge basieren auf dem Funktionsprinzip. Ein Auftrag wird durch sein Auftragsthema definiert. Um einen Auftrag auszuführen, muss eine Instanz einen Job Consumer für ein bestimmtes Auftragsthema bereitstellen. Das Auftragsthema ist die wichtigste Triebfeder des Verteilungsmechanismus.

Aufträge werden nur an die Instanzen verteilt, die einen Job Consumer für das Thema bieten. Durch Aktivieren/Deaktivieren der Job Consumer einer Instanz können Sie die Funktionen einer Instanz definieren und den Verteilungsmechanismus beeinflussen. Die verfügbaren Job Consumer einer Instanz werden an die gesamte Topologie übertragen.

In diesem Kontext bezieht sich der Begriff Verteilung auf die Zuweisung eines Auftrags zu einer bestimmten Instanz, die einen Job Consumer bereitstellt. Die Zuweisung zu einer Instanz wird im Repository gespeichert. Anders ausgedrückt: Sling-verteilte Aufträge können standardmäßig einer beliebigen Instanz in der Topologie zugewiesen werden. Allerdings können andere Aufträge nur von den Instanzen ausgeführt werden, die dasselbe Repository nutzen. Dies bedeutet, dass diese Aufträge ausschließlich von Instanzen ein und desselben Clusters ausgeführt werden können. Aufträge, die Instanzen eines anderen Clusters zugewiesen sind, werden nicht ausgeführt.

### Granite-Abladeframework  {#granite-offloading-framework}

Das Granite-Abladeframework ergänzt die Sling-Auftragsverteilung, um Aufträge, die Nicht-Cluster-Instanzen zugewiesen sind, auszuführen. Eine Verteilung (Instanzzuweisung) findet nicht statt. Jedoch werden an Nicht-Cluster-Instanzen verteilte Sling-Aufträge identifiziert und zwecks Ausführung an die Zielinstanz transportiert. Derzeit wird bei der Abladung für diesen Auftragstransport auf die Replikation zurückgegriffen. Zum Ausführen eines Auftrags werden im Rahmen der Abladung die Ein- und Ausgabe definiert, die dann in Kombination mit dem Auftrag zur Auftragsnutzlast werden.

Sling-verteilte Aufträge stellen das Auftrags- und Verteilungsframework bereit. Die Granite-Abladung übernimmt den Transport nur für den Sonderfall, dass Aufträge an Nicht-Cluster-Instanzen verteilt werden.

Neben dem Transport bietet das Abladeframework eine Erweiterung für die Workflow-Engine. Damit kann das Framework verteilte Aufträge als Teil des Workflows erstellen und auf deren Fertigstellung warten, bevor der Workflow fortgesetzt wird. Implementiert wird das Framework über die Workflow-API für externe Schritte der Workflow-Engine. Eine der Erweiterungen ermöglicht die generische Verteilung von Workflows. Die Verteilung einzelner Workflowschritte wird nicht unterstützt.

Das Abladeframework wird zudem mit einer Benutzeroberfläche bereitgestellt, um die Aktivierung von Auftragsthemen über die gesamte Topologie hinweg zu visualisieren und zu steuern. Über die Benutzeroberfläche lässt sich die Themenaktivierung Sling-verteilter Aufträge bequem konfigurieren. Die Abladung kann auch ohne die Benutzeroberfläche eingerichtet werden.

## Allgemeine Leitlinien und Best Practices für die Asset-Abladung  {#general-guidance-and-best-practices-for-asset-offloading}

Jede Implementierung ist einzigartig und daher gibt es auch keine Universal-Abladekonfiguration. In den folgenden Abschnitten werden Leitlinien und Best Practices zum Abladen der Asset-Aufnahme beschrieben.

Die Asset-Abladung bedeutet einen Mehraufwand für das System, auch für den Betrieb. Wenn die Asset-Aufnahme zu einer Belastung mit entsprechenden Problemen führt, empfiehlt Adobe, zunächst die Konfiguration ohne Abladung zu optimieren. Ziehen Sie die folgenden Möglichkeiten in Betracht, bevor Sie sich für eine Asset-Abladung entscheiden:

* Skalierung der Hardware
* Optimierung von Workflows
* Nutzung von Verlaufsworkflows
* Anzahl der für Workflows verwendeten Kerne begrenzen

Wenn Sie zu dem Schluss kommen, dass die Assets-Abladung ein für Sie geeigneter Ansatz ist, sollten Sie die folgenden Adobe-Leitlinien berücksichtigen:

* Es wird eine TarMK-basierte Bereitstellung empfohlen.
* Die TarMK-basierte Assets-Abladung ist nicht für eine übermäßige horizontale Skalierung vorgesehen.
* Stellen Sie sicher, dass die Netzwerkleistung zwischen Autor und Workern zufriedenstellend ist.

### Empfohlene Bereitstellung zur Assets-Abladung  {#recommended-assets-offloading-deployment}

Mit AEM und Oak sind verschiedene Bereitstellungszenarien möglich. Zur Assets-Abladung wird eine TarMK-basierte Bereitstellung mit freigegebenem Datenspeicher empfohlen. Die folgende Grafik zeigt die empfohlene Bereitstellung:

![chlimage_1-56](assets/chlimage_1-56.png)

Details zum Konfigurieren von Datenspeichern finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM](../sites-deploying/data-store-config.md).

### Deaktivieren der automatischen Agentenverwaltung  {#turning-off-automatic-agent-management}

Adobe empfiehlt eine Deaktivierung der automatischen Agentenverwaltung, weil diese keine Unterstützung für die nicht binäre Replikation bietet und zur Verwirrung beim Einrichten einer neuen Abladetopologie führen kann. Darüber hinaus unterstützt es nicht automatisch den Weiterleitungsreplikationsfluss, der für die Binärdatei-lose Replikation erforderlich ist.

1. Öffnen Sie Configuration Manager über die URL `http://localhost:4502/system/console/configMgr`.
1. Öffnen Sie die Konfiguration für `OffloadingAgentManager` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`).
1. Deaktivieren Sie die automatische Agentenverwaltung.

### Verwenden der Vorwärtsreplikation  {#using-forward-replication}

Standardmäßig kommt beim Abladetransport die Rückwärtsreplikation zum Einsatz, um die abgeladenen Assets per Pull-Vorgang vom Worker zurück an die primäre Instanz zu übertragen. Die Agenten für die Rückwärtsreplikation bieten keine Unterstützung für die nicht binäre Replikation. Sie sollten die Abladung zur Nutzung der Vorwärtsreplikation konfigurieren, um die abgeladenen Assets per Push-Vorgang zurück vom Worker an die primäre Instanz zu übertragen.

1. Wenn Sie von der Standardkonfiguration mit Rückwärtsreplikation migrieren, deaktivieren oder löschen Sie alle Agenten mit den Namen &quot; `offloading_outbox`&quot;und &quot; `offloading_reverse_*`&quot;auf Primär- und Worker, wobei &amp;ast; stellt die Sling-ID der Zielinstanz dar.
1. Erstellen Sie auf jedem Worker einen Agenten für die Vorwärtsreplikation, der auf die primäre Instanz verweist. Das Verfahren entspricht dem Erstellen von Forward Agents von der primären zu der Worker-Aktivität. Anweisungen zum Einrichten von Replikationsagenten für die Abladung finden Sie unter [Erstellen von Replikationsagenten für die Abladung](../sites-deploying/offloading.md#creating-replication-agents-for-offloading) .
1. Öffnen Sie die Konfiguration für `OffloadingDefaultTransporter` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`).
1. Ändern Sie den Wert der Eigenschaft `default.transport.agent-to-master.prefix` von `offloading_reverse` in `offloading`.

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### Verwendung von freigegebenem Datenspeicher und nicht binärer Replikation zwischen Autor und Workern  {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

Die Verwendung der Binärdatei-losen Replikation wird empfohlen, um den Transportaufwand für die Asset-Abladung zu reduzieren. Weitere Informationen zum Einrichten der nicht binären Replikation für einen freigegebenen Datenspeicher finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM](/help/sites-deploying/data-store-config.md). Die Vorgehensweise ist bei der Assets-Abladung nicht anders, es sind lediglich andere Replikationsagenten beteiligt. Da die Binärdatei-lose Replikation nur mit Agenten für die Weiterreplikation funktioniert, sollten Sie auch die Vorwärtsreplikation für alle Abladeagenten verwenden.

### Deaktivieren von Transportpaketen {#turning-off-transport-packages}

Standardmäßig wird beim Abladen ein Inhaltspaket erstellt, das den Abladeauftrag und die Auftragsnutzlast (das ursprüngliche Asset) enthält und dieses einzelne Abladepaket über eine einzige Replikationsanforderung transportiert. Die Erstellung dieser Abladepakete ist im Falle einer nicht binären Replikation kontraproduktiv, weil Binärdateien beim Erstellen des Pakets wieder in das Paket serialisiert werden. Die Verwendung dieser Transportpakete kann deaktiviert werden, was dazu führt, dass der Abladeauftrag und die Payload in mehreren Replikationsanfragen übertragen werden, eine für jeden Payload-Eintrag. Auf diese Weise können Sie die Vorteile der nicht binären Replikation nutzen. 

1. Öffnen Sie die Komponentenkonfiguration der Komponente *OffloadingDefaultTransporter* unter [http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)
1. Deaktivieren Sie die Eigenschaft *Replikationspaket (default.transport.contentpackage)*.

### Deaktivieren des Transports von Workflow-Modellen {#disabling-the-transport-of-workflow-model}

Standardmäßig fügt der Abladeworkflow *DAM-Update-Asset-Abladung* das Workflow-Modell hinzu, um den Worker zur Auftrags-Payload aufzurufen. Da dieser Workflow dem vordefinierten Modell *DAM Update Asset* folgt, kann diese zusätzliche Payload entfernt werden.

Wenn das Workflow-Modell von der Auftragsnutzlast deaktiviert wird, achten Sie darauf, die Änderungen mithilfe anderer Tools, etwa Package Manager, an das referenzierte Workflow-Modell zu verteilen.

Um den Transport des Workflow-Modells zu deaktivieren, ändern Sie den Worfklow „Asset-Abladung für DAM-Update“.

1. Öffnen Sie die Workflow-Konsole unter [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).
1. Öffnen Sie die Registerkarte „Modelle“.
1. Öffnen Sie das Workflow-Modell DAM-Update-Asset-Abladung .
1. Öffnen Sie die Schritteigenschaften für den Schritt &quot;DAM-Workflow-Abladung&quot;.
1. Öffnen Sie die Registerkarte Argumente und deaktivieren Sie die Optionen Modell zur Eingabe hinzufügen und Modell zur Ausgabe hinzufügen .
1. Speichern Sie die Änderungen am Modell.

### Optimieren des Abrufintervalls  {#optimizing-the-polling-interval}

Die Workflow-Abladung wird mithilfe eines externen Workflows auf der primären Instanz implementiert, der den Abschluss des abgeladenen Workflows auf dem Worker abfragt. Das standardmäßige Abrufintervall für die externen Workflow-Prozesse beträgt fünf Sekunden. Adobe empfiehlt, dass Sie das Abrufintervall des Assets-Abladeschritts auf mindestens 15 Sekunden erhöhen, um den abladebezogenen Mehraufwand auf der primären Instanz zu reduzieren.

1. Öffnen Sie die Workflow-Konsole unter [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).

1. Öffnen Sie die Registerkarte „Modelle“.
1. Öffnen Sie das Workflow-Modell DAM-Update-Asset-Abladung .
1. Öffnen Sie die Schritteigenschaften für den Schritt &quot;DAM-Workflow-Abladung&quot;.
1. Öffnen Sie die Registerkarte &quot;Commons&quot;und passen Sie den Wert der Eigenschaft &quot;Period&quot;an.
1. Speichern Sie die Änderungen am Modell.

## Weitere Ressourcen  {#more-resources}

Dieses Dokument konzentriert sich auf die Asset-Abladung. Weitere Informationen zum Thema Abladung finden Sie u. a. in den folgenden Dokumenten:

* [Abladen von Aufträgen](/help/sites-deploying/offloading.md)
* [Offloader für Assets-Workflows](/help/sites-administering/workflow-offloader.md)
