---
title: Auslagern von Aufträgen
seo-title: Offloading Jobs
description: Erfahren Sie, wie Sie AEM Instanzen in einer Topologie konfigurieren und verwenden, um bestimmte Verarbeitungstypen durchzuführen.
seo-description: Learn how to configure and use AEM instances in a topology in order to perform specific types of processing.
uuid: e971d403-dfd2-471f-b23d-a67e35f1ed88
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 370151df-3b8e-41aa-b586-5c21ecb55ffe
feature: Configuring
exl-id: b10bf1b6-0360-45ca-b1aa-f4184cbfb5c0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2818'
ht-degree: 42%

---

# Auslagern von Aufträgen{#offloading-jobs}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Durch die Abladung werden Verarbeitungsaufgaben in einer Topologie auf die Instanzen des Experience Managers verteilt. Mit der Abladung können Sie bestimmte Experience Manager-Instanzen zur Durchführung bestimmter Verarbeitungsarten verwenden. Durch eine spezialisierte Verarbeitung können Sie die Nutzung der verfügbaren Serverressourcen maximieren.

Die Abladung basiert auf den [Discovery](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html)- und JobManager-Funktionen von Apache Sling. Um die Abladung zu nutzen, müssen Sie Experience Manager-Cluster zu einer Topologie hinzufügen und die von den Clustern verarbeiteten Aufgabenthemen identifizieren. Cluster bestehen aus einer oder mehreren Experience Manager-Instanzen, sodass eine Instanz als Cluster gilt.

Informationen zum Hinzufügen von Instanzen zu einer Topologie finden Sie unter [Verwalten von Topologien](/help/sites-deploying/offloading.md#administering-topologies).

### Auftragsverteilung {#job-distribution}

Die Sling JobManager- und JobConsumer-Dienste ermöglichen die Erstellung von Aufträgen, die in einer Topologie verarbeitet werden:

* JobManager: Ein Dienst, der Aufträge für bestimmte Themen erstellt.
* JobConsumer: Ein Dienst, der Aufträge für ein oder mehrere Themen ausführt. Mehrere JobConsumer-Dienste können für dasselbe Thema registriert werden.

Wenn JobManager einen Auftrag erstellt, wählt das Abladungs-Framework einen Experience Manager-Cluster in der Topologie aus, um den Auftrag auszuführen:

* Der Cluster muss eine oder mehrere Instanzen enthalten, die einen JobConsumer ausführen, der für das Auftragsthema registriert ist.
* Das Thema muss für mindestens eine Instanz im Cluster aktiviert sein.

Siehe [Konfigurieren der Themennutzung](/help/sites-deploying/offloading.md#configuring-topic-consumption) für Informationen zur Raffinierung der Auftragsverteilung.

![chlimage_1-109](assets/chlimage_1-109.png)

Wenn das Abladungs-Framework einen Cluster auswählt, um einen Auftrag auszuführen, und der Cluster aus mehreren Instanzen besteht, bestimmt die Sling Distribution, welche Instanz im Cluster den Auftrag ausführt.

### Auftrags-Payloads {#job-payloads}

Das Abladungs-Framework unterstützt Auftrags-Payloads, die Aufträge mit Ressourcen im Repository verknüpfen. Auftrags-Payloads sind nützlich, wenn Aufträge für Verarbeitungsressourcen erstellt und der Auftrag auf einen anderen Computer abgeladen wird.

Bei der Erstellung eines Auftrags befindet sich die Payload nur auf der Instanz, die den Auftrag erstellt. Beim Abladen des Auftrags stellen Replikationsagenten sicher, dass die Payload auf der Instanz erstellt wird, die den Auftrag schließlich verarbeitet. Wenn die Auftragsausführung abgeschlossen ist, führt die Rückwärtsreplikation dazu, dass die Payload zurück in die Instanz kopiert wird, die den Auftrag erstellt hat.

## Verwalten von Topologien {#administering-topologies}

Topologien sind lose verknüpfte Experience Manager-Cluster, die an der Abladung beteiligt sind. Ein Cluster besteht aus einer oder mehreren Experience Manager-Serverinstanzen (eine Instanz gilt als Cluster).

Jede Experience Manager-Instanz führt die folgenden Abladedienste aus:

* Discovery-Dienst: Sendet Anforderungen an einen Topologie-Connector, um in die Topologie aufgenommen zu werden.
* Topologie-Connector: Erhält die Join-Anfragen und akzeptiert oder lehnt jede Anfrage ab.

Der Discovery-Dienst aller Topologiemitglieder verweist auf den Topologie-Connector eines der Mitglieder. In den folgenden Abschnitten wird dieses Mitglied als Stammmitglied bezeichnet.

![chlimage_1-110](assets/chlimage_1-110.png)

Jeder Cluster in der Topologie enthält eine Instanz, die als Leader erkannt wird. Der Cluster-Leader interagiert für die anderen Cluster-Mitglieder mit der Topologie. Wenn der Leader den Cluster verlässt, wird automatisch ein neuer Leader für den Cluster ausgewählt.

### Anzeigen der Topologie {#viewing-the-topology}

Mit dem Topologie-Browser können Sie den Status der Topologie überprüfen, zu der die Experience Manager-Instanz gehört. Im Topologie-Browser werden die Cluster und Instanzen der Topologie angezeigt.

Für jeden Cluster sehen Sie eine Liste von Cluster-Mitgliedern, die die Reihenfolge angibt, in der jedes Mitglied dem Cluster beigetreten ist, und das Mitglied der Leader ist. Die Eigenschaft „Aktuell“ gibt die Instanz an, die Sie derzeit verwalten.

Für jede Instanz des Clusters werden verschiedene topologiebezogene Eigenschaften angezeigt:

* Eine Zulassungsliste mit Themen für den JobConsumer der Instanz.
* Die Endpunkte, die für die Verbindung mit der Topologie verfügbar gemacht werden.
* Die Auftragsthemen, für die die Instanz zum Abladen registriert ist.
* Die Auftragsthemen, die die Instanz verarbeitet.

1. Klicken Sie in der Touch-Benutzeroberfläche auf die Registerkarte Tools . ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Klicken Sie im Bereich &quot;Granite-Vorgänge&quot;auf Browser-Abladung .
1. Klicken Sie im Navigationsfenster auf &quot;Topologie-Browser&quot;.

   Die an der Topologie teilnehmenden Cluster werden angezeigt.

   ![chlimage_1-111](assets/chlimage_1-111.png)

1. Klicken Sie auf einen Cluster, um eine Liste der Instanzen im Cluster mit ihrer ID, ihrem aktuellen Status und dem Status &quot;Leader&quot;anzuzeigen.
1. Klicken Sie auf eine Instanz-ID, um detailliertere Eigenschaften anzuzeigen.

Sie können auch die Web-Konsole zum Anzeigen von Topologie-Informationen verwenden. Die Konsole enthält weitere Informationen zu den Topologie-Clustern:

* Welche Instanz ist die lokale Instanz?
* Die Topologie-Connector-Dienste, mit denen diese Instanz eine Verbindung zur Topologie (ausgehend) herstellt, und die Dienste, die eine Verbindung zu dieser Instanz herstellen (eingehende).
* Ändern Sie den Verlauf für die Topologie- und Instanzeigenschaften.

Gehen Sie wie folgt vor, um die Seite „Topology Management“ der Web-Konsole zu öffnen:

1. Öffnen Sie die Web-Konsole in Ihrem Browser. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klicken Sie auf Haupt > Topologieverwaltung.

   ![chlimage_1-112](assets/chlimage_1-112.png)

### Konfigurieren der Topologiemitgliedschaft {#configuring-topology-membership}

Der ressourcenbasierte Apache Sling-Erkennungsdienst wird auf jeder Instanz ausgeführt, um zu steuern, wie Experience Manager-Instanzen mit einer Topologie interagieren.

Der Discovery-Dienst sendet regelmäßig POST-Anforderungen (Heartbeats) an Topologie-Connector-Dienste, um Verbindungen mit der Topologie herzustellen und aufrechtzuerhalten. Der Topologie-Connector-Dienst verwaltet eine Zulassungsliste mit IP-Adressen oder Host-Namen, die Mitglied der Topologie werden dürfen:

* Um eine Instanz zum Topologie-Mitglied zu machen, geben Sie die URL für den Topologie-Connector-Dienst des Stamm-Mitglieds an.
* Damit eine Instanz einer Topologie beitreten kann, fügen Sie die Instanz zur Zulassungsliste des Topologie-Connector-Dienstes des Stammmitglieds hinzu.

Verwenden Sie die Web-Konsole oder einen sling:OsgiConfig -Knoten, um die folgenden Eigenschaften des Diensts org.apache.sling.discovery.impt.Config zu konfigurieren:

<table> 
 <tbody> 
  <tr> 
   <th>Eigenschaftsname</th> 
   <th>OSGi-Name</th> 
   <th>Beschreibung</th> 
   <th>Standardwert</th> 
  </tr> 
  <tr> 
   <td>Heartbeat-Timeout (Sekunden)</td> 
   <td>heartbeatTimeout</td> 
   <td>Die Zeit in Sekunden, die auf eine Heartbeat-Antwort gewartet wird, bevor die Targeting-Instanz als nicht verfügbar betrachtet wird. </td> 
   <td>20</td> 
  </tr> 
  <tr> 
   <td>Heartbeat-Intervall (Sekunden)</td> 
   <td>heartbeatInterval</td> 
   <td>Die Zeit in Sekunden zwischen Heartbeats.</td> 
   <td>15</td> 
  </tr> 
  <tr> 
   <td>Minimale Ereignisverzögerung (Sekunden)</td> 
   <td>minEventDelay</td> 
   <td><p>Wenn eine Änderung an der Topologie eintritt, die Zeit der Verzögerung für die Änderung des Status von TOPOLOGY_CHANGING zu TOPOLOGY_CHANGED. Jede Änderung, die eintritt, wenn der Status TOPOLOGY_CHANGING lautet, erhöht die Verzögerung um diesen Zeitraum.</p> <p>Diese Verzögerung verhindert, dass Listener mit Ereignissen überflutet werden. </p> <p>Um keine Verzögerung zu verwenden, geben Sie 0 oder eine negative Zahl an.</p> </td> 
   <td>3</td> 
  </tr> 
  <tr> 
   <td>Topologie-Connector-URLs</td> 
   <td>topologyConnectorUrls</td> 
   <td>Die URLs der Topologie-Connector-Dienste zum Senden von Heartbeat-Nachrichten.</td> 
   <td>http://localhost:4502/libs/sling/topology/connector</td> 
  </tr> 
  <tr> 
   <td>Topologie-Connectoren-Zulassungsliste</td> 
   <td>topologyConnectorWhitelist</td> 
   <td>Die Liste der IP-Adressen oder Hostnamen, die der lokale Topologie-Connector-Dienst in der Topologie zulässt. </td> 
   <td><p>localhost</p> <p>127.0.0.1</p> </td> 
  </tr> 
  <tr> 
   <td>Repository-Deskriptorname</td> 
   <td>leaderElectionRepositoryDescriptor</td> 
   <td> </td> 
   <td>&lt;kein Wert&gt;</td> 
  </tr> 
 </tbody> 
</table>

Gehen Sie wie folgt vor, um eine CQ-Instanz mit dem Stamm-Mitglied einer Topologie zu verbinden. Die Instanz verweist dann auf die Topologie-Connector-URL des Stamm-Mitglieds der Topologie. Führen Sie dieses Verfahren für alle Mitglieder der Topologie durch.

1. Öffnen Sie die Web-Konsole in Ihrem Browser. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klicken Sie auf Haupt > Topologieverwaltung.
1. Klicken Sie auf Discovery-Dienst konfigurieren .
1. Fügen Sie ein Element zur Eigenschaft „Topology Connector URLs“ hinzu und geben Sie die URL des Topologie-Connector-Dienstes für das Stamm-Mitglied der Topologie an. Die URL hat die Form https://rootservername:4502/libs/sling/topology/connector.

Führen Sie die folgenden Schritte für das Stamm-Mitglied der Topologie aus. Dadurch werden die Namen der anderen Topologiemitglieder zur Discovery Service-Zulassungsliste hinzugefügt.

1. Öffnen Sie die Web-Konsole in Ihrem Browser. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klicken Sie auf Haupt > Topologieverwaltung.
1. Klicken Sie auf Discovery-Dienst konfigurieren .
1. Fügen Sie für jedes Topologiemitglied ein Element zur Eigenschaft „Topologie-Connectoren-Zulassungsliste“ hinzu und geben Sie den Hostnamen oder die IP-Adresse des Topologiemitglieds an.

## Konfigurieren der Themennutzung {#configuring-topic-consumption}

Verwenden Sie die Browser-Abladung, um die Themenverarbeitung für die Experience Manager-Instanzen in der Topologie zu konfigurieren. Sie können die von jeder Instanz verarbeiteten Themen angeben. Um beispielsweise Ihre Topologie so zu konfigurieren, dass nur eine Instanz Themen eines bestimmten Typs verbraucht, deaktivieren Sie das Thema auf allen Instanzen außer einer.

Aufträge werden auf Instanzen verteilt, bei denen das zugehörige Thema mithilfe der Round-Robin-Logik aktiviert ist.

1. Klicken Sie in der Touch-Benutzeroberfläche auf die Registerkarte Tools . ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Klicken Sie im Bereich &quot;Granite-Vorgänge&quot;auf Browser-Abladung .
1. Klicken Sie im Navigationsfenster auf Browser-Abladung.

   Die Abladethemen und die Serverinstanzen, die die Themen verarbeiten können, werden angezeigt.

   ![chlimage_1-113](assets/chlimage_1-113.png)

1. Um die Nutzung eines Themas für eine Instanz zu deaktivieren, klicken Sie unter dem Themennamen neben der Instanz auf Deaktivieren .
1. Um die Verarbeitung aller Themen für eine Instanz zu konfigurieren, klicken Sie auf die Instanz-ID unter einem beliebigen Thema.

   ![chlimage_1-114](assets/chlimage_1-114.png)

1. Klicken Sie auf eine der folgenden Schaltflächen neben einem Thema, um das Verbrauchsverhalten für die Instanz zu konfigurieren, und klicken Sie dann auf Speichern:

   * Aktiviert: Diese Instanz verbraucht Aufträge dieses Themas.
   * Deaktiviert: Diese Instanz verarbeitet keine Aufträge für dieses Thema.
   * Exklusiv: Diese Instanz verarbeitet nur Aufträge für dieses Thema.

   **Hinweis:** Wenn Sie für ein Thema die Option Exklusiv auswählen, werden alle anderen Themen automatisch auf Deaktiviert gesetzt.

### Installierte Job Consumer {#installed-job-consumers}

Die Installation von Experience Manager umfasst mehrere implementierte JobConsumer-Dienste. Die Themen, für die diese JobConsumer-Dienste registriert sind, werden im Abladebrowser angezeigt. Bei den weiteren angezeigten Themen handelt es sich um von benutzerdefinierten JobConsumer-Diensten registrierte Themen. In der folgenden Tabelle werden die standardmäßigen JobConsumers beschrieben.

| Auftragsthema | Service-PID | Beschreibung |
|---|---|---|
| / | org.apache.sling.event.impl.jobs.deprecated.EventAdminBridge | Mit Apache Sling installiert. Verarbeitet Aufträge, die vom OSGi-Event-Admin-Dienst aus Gründen der Abwärtskompatibilität generiert werden. |
| com/day/cq/replication/job/&amp;ast; | com.day.cq.replication.impl.AgentManagerImpl | Ein Replikationsagent, der Auftrags-Payloads repliziert. |
| com/adobe/granite/workflow/offloading | com.adobe.granite.workflow.core.offloading.WorkflowOffloadingJobConsumer | Verarbeitet Aufträge, die der Workflow &quot;DAM Update Asset Offloader&quot;generiert. |

### Deaktivieren und Aktivieren von Themen für eine Instanz {#disabling-and-enabling-topics-for-an-instance}

Der Apache Sling Job Consumer Manager-Dienst stellt Eigenschaften für die Zulassungsliste und Blockierungsliste von Themen bereit. Konfigurieren Sie diese Eigenschaften, um die Verarbeitung von bestimmten Themen auf einer Experience Manager-Instanz zu aktivieren oder zu deaktivieren.

**Hinweis:** Wenn die Instanz zu einer Topologie gehört, können Sie Themen auch mit der Browser-Abladung auf einem beliebigen Computer der Topologie aktivieren oder deaktivieren.

Die Logik, mit der die Liste der aktivierten Themen erstellt wird, lässt zunächst alle Themen in der Zulassungsliste zu und entfernt dann Themen, die sich auf der Blockierungsliste befinden. Standardmäßig sind alle Themen aktiviert (der Wert für die Zulassungsliste lautet `*`) und keine Themen deaktiviert sind (die Blockierungsliste hat keinen Wert).

Verwenden Sie die Web-Konsole oder einen `sling:OsgiConfig`-Knoten, um die folgenden Eigenschaften zu konfigurieren. Für `sling:OsgiConfig`-Knoten lautet die PID des Job Consumer Manager-Dienstes „org.apache.sling.event.impl.jobs.JobConsumerManager“.

| Eigenschaftsname in der Web-Konsole | OSGi-ID | Beschreibung |
|---|---|---|
| Themen-Whitelist | job.consumermanager.whitelist | Eine Liste der Themen, die vom lokalen JobManager-Dienst verarbeitet werden. Der Standardwert „&amp;ast;“ sorgt dafür, dass alle Themen an den registrierten TopicConsumer-Dienst gesendet werden. |
| Themen-Blacklist | job.consumermanager.blacklist | Eine Liste der Themen, die vom lokalen JobManager-Dienst nicht verarbeitet werden. |

## Erstellen von Replikationsagenten für die Abladung {#creating-replication-agents-for-offloading}

Das Abladungs-Framework überträgt Ressourcen mittels Replikation zwischen Autoren- und Worker-Instanzen. Das Framework erstellt automatisch Replikationsagenten, wenn Instanzen Mitglied der Topologie werden. Die Agenten werden mit Standardwerten erstellt. Sie müssen das Kennwort, das die Agenten für die Authentifizierung verwenden, manuell ändern.

>[!CAUTION]
>
>Es ist ein bekanntes Problem bei automatisch generierten Replikationsagenten, dass neue Agenten manuell erstellt werden müssen. Befolgen Sie das Verfahren unter [Probleme bei der Verwendung der automatisch generierten Replikationsagenten](/help/sites-deploying/offloading.md#problems-using-the-automatically-generated-replication-agents) bevor Sie die Agenten für die Abladung erstellen.

Erstellen Sie die Replikationsagenten, die Auftrags-Payloads zwischen Instanzen für die Abladung übertragen. Die nachfolgende Darstellung zeigt die erforderlichen Agenten für die Abladung von der Autoren- an die Worker-Instanz. Die Autoreninstanz hat die Sling-ID 1 und die Worker-Instanz die Sling-ID 2:

![chlimage_1-115](assets/chlimage_1-115.png)

Für dieses Setup sind die folgenden drei Agenten erforderlich:

1. Ein ausgehender Agent in der Autoreninstanz, der auf die Worker-Instanz repliziert.
1. Ein Rückwärtsagent auf der Autoreninstanz, der aus dem Postausgang auf der Worker-Instanz abruft.
1. Ein Postausgangsagent auf der Worker-Instanz.

Dieses Replikationsschema gleicht dem für Autoren- und Veröffentlichungsinstanzen verwendeten. Für die Abladesituation sind jedoch alle beteiligten Instanzen Autoreninstanzen.

>[!NOTE]
>
>Das Abladungs-Framework nutzt die Topologie zum Abrufen der IP-Adressen der Abladungsinstanzen. Basierend auf diesen IP-Adressen erstellt das Framework dann automatisch die Replikationsagenten. Wenn sich die IP-Adressen der Abladeinstanzen später ändern, wird die Änderung nach dem Neustart der Instanz automatisch in der Topologie übernommen. Das Abladungs-Framework aktualisiert jedoch nicht automatisch die Replikationsagenten mit den neuen IP-Adressen. Um diese Situation zu vermeiden, verwenden Sie feste IP-Adressen für alle Instanzen in der Topologie.

### Benennen der Replikationsagenten für die Abladung {#naming-the-replication-agents-for-offloading}

Verwenden Sie ein spezielles Format für die Eigenschaft ***Name*** des Replikationsagenten, damit das Abladungs-Framework automatisch den richtigen Agenten für bestimmte Worker-Instanzen nutzt.

**Benennung des ausgehenden Agenten auf der Autoreninstanz:**

`offloading_<slingid>`, wobei `<slingid>` die Sling-ID der Worker-Instanz ist.

Beispiel: `offloading_f5c8494a-4220-49b8-b079-360a72f71559`

**Benennung des Rückwärtsagenten auf der Autoreninstanz:**

`offloading_reverse_<slingid>`, wobei `<slingid>` die Sling-ID der Worker-Instanz ist.

Beispiel: `offloading_reverse_f5c8494a-4220-49b8-b079-360a72f71559`

**Benennung des Postausgangs auf der Worker-Instanz:**

`offloading_outbox`

### Erstellen des ausgehenden Agenten {#creating-the-outgoing-agent}

1. Erstellen Sie einen **Replikationsagenten** auf der Autoreninstanz. (Siehe [Dokumentation für Replikationsagenten](/help/sites-deploying/replication.md)). Geben Sie einen beliebigen **Titel an**. Der **Name** muss der Namenskonvention entsprechen.
1. Erstellen Sie den Agenten mit den folgenden Eigenschaften:

   | Eigenschaft | Wert |
   |---|---|
   | Einstellungen > Serialisierungstyp | Standard |
   | Transport > Transport-URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Transport > Transport-Benutzer | Replikationsbenutzer auf Zielinstanz |
   | Transport > Transport Passoword | Replizieren des Benutzerkennworts auf der Zielinstanz |
   | Erweitert > HTTP-Methode | POST |
   | Trigger > Standard ignorieren | True |

### Erstellen des Rückwärtsagenten {#creating-the-reverse-agent}

1. Erstellen Sie einen **Rückwärts-Replikationsagenten** auf der Autoreninstanz. (Siehe [Dokumentation für Replikationsagenten](/help/sites-deploying/replication.md). Geben Sie einen beliebigen **Titel an**. Der **Name** muss der Namenskonvention entsprechen.
1. Erstellen Sie den Agenten mit den folgenden Eigenschaften:

   | Eigenschaft | Wert |
   |---|---|
   | Einstellungen > Serialisierungstyp | Standard |
   | Transport > Transport-URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Transport > Transport-Benutzer | Replikationsbenutzer auf Zielinstanz |
   | Transport > Transport Passoword | Replizieren des Benutzerkennworts auf der Zielinstanz |
   | Erweitert > HTTP-Methode | GET |

### Erstellen des Postausgangs-Agenten {#creating-the-outbox-agent}

1. Erstellen Sie einen **Replikationsagenten** auf der Worker-Instanz. (Siehe [Dokumentation für Replikationsagenten](/help/sites-deploying/replication.md). Geben Sie einen beliebigen **Titel an**. Der **Name** muss `offloading_outbox` lauten.
1. Erstellen Sie den Agenten mit den folgenden Eigenschaften.

   | Eigenschaft | Wert |
   |---|---|
   | Einstellungen > Serialisierungstyp | Standard |
   | Transport > Transport-URI | repo://var/replication/outbox |
   | Trigger > Standard ignorieren | True |

### Suchen der Sling-ID {#finding-the-sling-id}

Rufen Sie die Sling-ID einer Experience Manager-Instanz mit einer der folgenden Methoden ab:

* Öffnen Sie die Web-Konsole und suchen Sie in den Sling-Einstellungen nach dem Wert der Eigenschaft für die Sling-ID ([http://localhost:4502/system/console/status-slingsettings](http://localhost:4502/system/console/status-slingsettings)). Diese Methode ist nützlich, wenn die Instanz noch nicht Teil der Topologie ist.
* Ist sie bereits Teil der Topologie, verwenden Sie den Topologie-Browser.

## Abladen der Verarbeitung von DAM-Assets {#offloading-the-processing-of-dam-assets}

Konfigurieren Sie die Instanzen einer Topologie, sodass bestimmte Instanzen die Hintergrundverarbeitung von Assets durchführen, die in DAM hinzugefügt oder aktualisiert werden.

Standardmäßig führt Experience Manager den Workflow DAM-Update-Asset aus, wenn sich ein DAM-Asset ändert oder ein Asset zu DAM hinzugefügt wird. Ändern Sie das Standardverhalten so, dass Experience Manager stattdessen den Workflow DAM Update Asset Offloader ausführt. Dieser Workflow generiert einen JobManager-Auftrag mit dem Thema `com/adobe/granite/workflow/offloading`. Konfigurieren Sie dann die Topologie so, dass der Auftrag an einen dedizierten Worker abgeladen wird.

>[!CAUTION]
>
>Bei Verwendung mit Workflow-Abladung sollte kein Workflow vorübergehend sein. Beispielsweise darf der Workflow DAM-Update-Asset nicht vorübergehend sein, wenn er für die Asset-Abladung verwendet wird. Informationen zum Festlegen/Aufheben der Übergangs-Markierung in einem Workflow finden Sie unter [Übergangs-Workflows](/help/assets/performance-tuning-guidelines.md#workflows).

Im folgenden Verfahren werden die folgenden Eigenschaften für die Abladetopologie angenommen:

* Eine oder mehrere Experience Manager-Instanzen sind Authoring-Instanzen, mit denen Benutzer interagieren, um DAM-Assets hinzuzufügen oder zu aktualisieren.
* Benutzer, die nicht direkt mit einer oder mehreren Experience Manager-Instanzen interagieren, die die DAM-Assets verarbeiten. Diese Instanzen sind der Hintergrundverarbeitung von DAM-Assets gewidmet.

1. Konfigurieren Sie auf jeder Experience Manager-Instanz den Discovery-Dienst so, dass er auf den Stamm-Topography-Connector verweist. (Siehe [Konfigurieren der Topologiemitgliedschaft](#title4).
1. Konfigurieren Sie den Stamm-Topography-Connector so, dass sich die Verbindungsinstanzen auf der Zulassungsliste befinden.
1. Öffnen Sie den Browser &quot;Abladung&quot; und deaktivieren Sie die `com/adobe/granite/workflow/offloading` Thema zu den Instanzen, mit denen Benutzer interagieren, um DAM-Assets hochzuladen oder zu ändern.

   ![chlimage_1-116](assets/chlimage_1-116.png)

1. Konfigurieren Sie in jeder Instanz, mit der Benutzer interagieren, um DAM-Assets hochzuladen oder zu ändern, Workflow-Starter für die Verwendung des Workflows DAM-Update-Asset-Abladung :

   1. Öffnen Sie die Workflow-Konsole.
   1. Klicken Sie auf die Registerkarte Starter .
   1. Suchen Sie die beiden Starter-Konfigurationen, die den Workflow &quot;DAM-Update-Asset&quot;ausführen. Ein Starter-Konfigurationsereignistyp ist &quot;Knoten erstellt&quot;und der andere Typ &quot;Knoten geändert&quot;.
   1. Ändern Sie beide Ereignistypen so, dass sie den Workflow &quot;Asset-Abladung für DAM-Update&quot;ausführen. (Informationen zu Starter-Konfigurationen finden Sie unter [Starten von Workflows bei Knotenänderung](/help/sites-administering/workflows-starting.md).

1. Deaktivieren Sie auf den Instanzen, die die Hintergrundverarbeitung von DAM-Assets durchführen, die Workflow-Starter, die den Workflow DAM-Update-Asset ausführen.

## Weiterführende Literatur {#further-reading}

Zusätzlich zu den auf dieser Seite dargestellten Details können Sie auch Folgendes lesen:

* Weitere Information zur Verwendung von Java-APIs für die Erstellung von Aufträgen und JobConsumer-Diensten finden Sie unter [Erstellen und Nutzen von Aufträgen für die Abladung](/help/sites-developing/dev-offloading.md).
* Allgemeine Richtlinien und Best Practices für die Asset-Abladung finden Sie unter [Allgemeine Richtlinien und Best Practices für die Asset-Abladung](/help/assets/assets-offloading-best-practices.md#general-guidance-and-best-practices-for-asset-offloading).
* Informationen zum Deaktivieren der automatischen Erstellung von Abladeagenten finden Sie unter [Deaktivieren der automatischen Agentenverwaltung](/help/assets/assets-offloading-best-practices.md#turning-off-automatic-agent-management).
