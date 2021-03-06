---
title: Asset-Überwachung – Best Practices
description: Best Practices zur Überwachung der Umgebung und Leistung Ihrer [!DNL Experience Manager] Instanz nach der Bereitstellung.
contentOwner: AG
feature: Asset Management
role: Admin,Architect
exl-id: edbb275a-5ead-4ed2-8708-29e766081d75
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '1745'
ht-degree: 74%

---

# Assets-Überwachung – Best Practices {#assets-monitoring-best-practices}

Aus Sicht von Adobe Experience Manager Assets sollte die Überwachung die Beobachtung und Berichterstattung zu den folgenden Prozessen und Technologien umfassen:

* System-CPU
* Systemspeicherauslastung
* I/O-Vorgänge und -Wartezeit des Systemdatenträgers
* I/O-Vorgänge des Systemnetzwerks
* JMX MBeans für:

   * Heap-Auslastung
   * Asynchrone Prozesse, z. B. Workflows

* Integritätsprüfungen der OSGi-Konsole

In der Regel [!DNL Assets] kann auf zwei Arten überwacht werden: Live-Überwachung und Langzeitüberwachung.

## Live-Überwachung {#live-monitoring}

Es ist ratsam, die Live-Überwachung während der Leistungstestphase Ihres Entwicklungsprozesses oder in Situationen mit hoher Auslastung durchzuführen, um sich mit den Leistungsmerkmalen Ihrer Umgebung vertraut zu machen. Normalerweise sollte für die Live-Überwachung eine Tool-Suite eingesetzt werden. Einige Empfehlungen:

* [Visual VM](https://visualvm.github.io/): Mit Visual VM können Sie detaillierte Java-VM-Informationen anzeigen, einschließlich CPU-Auslastung und Java-Speicherbelegung. Außerdem können Sie Code prüfen und auswerten, der auf einer Instanz ausgeführt wird.
* [Top](https://man7.org/linux/man-pages/man1/top.1.html): „Top“ ist ein Linux-Befehl zum Öffnen eines Dashboards, in dem Auslastungsstatistiken angezeigt werden, z. B. zur CPU-, Arbeitsspeicher- und I/O-Auslastung. Darin können Sie sich einen allgemeinen Überblick über die Vorgänge auf einer Instanz verschaffen.
* [Htop](https://hisham.hm/htop/): „Htop“ ist ein interaktives Anzeigeprogramm für Prozesse. Es enthält ausführliche Informationen zur Auslastung von CPU und Arbeitsspeicher, die über die Informationen von „Top“ hinausgehen. Htop kann auf den meisten Linux-Systemen mit `yum install htop` oder `apt-get install htop`.

* [Iotop](https://guichaz.free.fr/iotop/): „Iotop“ ist ein ausführliches Dashboard für die I/O-Auslastung von Datenträgern. Darin werden anhand von Balken und Anzeigen die Prozesse, für die Datenträger-I/O-Vorgänge genutzt werden, sowie die verwendete Menge dargestellt. Iotop kann auf den meisten Linux-Systemen mit `yum install iotop` oder `apt-get install iotop`.

* [Iftop](https://www.ex-parrot.com/pdw/iftop/): Mit „Iftop“ werden ausführliche Informationen zur Ethernet-/Netzwerkauslastung angezeigt. Es werden Statistiken pro Kommunikationskanal auf den Entitäten zur Ethernet-Verwendung und zur genutzten Bandbreite angegeben. Iftop kann auf den meisten Linux-Systemen mit `yum install iftop` oder `apt-get install iftop`.

* Java Flight Recorder (JFR): Ein kommerzielles Tool von Oracle, das Sie in Umgebungen, die nicht für die Produktion bestimmt sind, kostenlos nutzen können. Weitere Informationen finden Sie unter [Verwenden von Java Flight Recorder zur Diagnose von CQ-Laufzeitproblemen](https://cq-ops.tumblr.com/post/73865704329/how-to-use-java-flight-recorder-to-diagnose-cq).
* [!DNL Experience Manager] error.log-Datei: Sie können die [!DNL Experience Manager] error.log für Details zu den im System protokollierten Fehlern. Verwenden Sie den Befehl `tail -F quickstart/logs/error.log` um Fehler zu identifizieren, die Sie untersuchen sollten.
* [Workflow-Konsole](../sites-administering/workflows.md): Nutzen Sie die Workflow-Konsole, um Workflows zu überwachen, die Verzögerungen aufweisen oder hängen.

Normalerweise verwenden Sie diese Tools zusammen, um eine umfassende Vorstellung von der Leistung Ihrer [!DNL Experience Manager] -Instanz.

>[!NOTE]
>
>Dies sind Standardtools ohne direkte Unterstützung durch Adobe. Hierfür sind keine zusätzlichen Lizenzen erforderlich.

![chlimage_1-142](assets/chlimage_1-142.png) ![chlimage_1-143](assets/chlimage_1-143.png)

## Langzeitüberwachung {#long-term-monitoring}

Langfristige Überwachung einer [!DNL Experience Manager] -Instanz umfasst die Überwachung der gleichen Live-Übertragungen für eine längere Dauer. Außerdem werden Warnungen definiert, die speziell auf Ihre Umgebung zugeschnitten sind.

### Protokollaggregation und Berichterstellung {#log-aggregation-and-reporting}

Es sind mehrere Tools zum Aggregieren von Protokollen verfügbar, z. B. Splunk(TM) und Elastic Search/Logstash/Kabana (ELK). So beurteilen Sie die Betriebszeit Ihrer [!DNL Experience Manager] müssen Sie beispielsweise die für Ihr System spezifischen Protokollereignisse verstehen und Warnhinweise erstellen, die auf ihnen basieren. Ein gutes Wissen über Ihre Entwicklungs- und Betriebspraktiken kann Ihnen dabei helfen, besser zu verstehen, wie Sie Ihren Protokollaggregationsprozess so einstellen können, dass er kritische Warnhinweise generiert.

### Umgebungsüberwachung {#environment-monitoring}

Die Umgebungsüberwachung umfasst die Überwachung der folgenden Punkte:

* Netzwerkdurchsatz
* Datenträger-I/O-Vorgänge
* Arbeitsspeicher
* CPU-Auslastung
* JMX MBeans
* Externe Websites

Sie benötigen externe Tools, z. B. NewRelic(TM) und AppDynamics(TM), um die einzelnen Elemente zu überwachen. Mit diesen Tools können Sie spezifische Warnungen für Ihr System generieren, z. B. für hohe Systemauslastung, Workflow-Stau, Fehler bei Integritätsprüfungen oder nicht authentifizierten Zugriff auf Ihre Website. Adobe spricht keinerlei Empfehlungen für bestimmte Tools aus. Ermitteln Sie, welches Tool für Ihre Zwecke am besten geeignet ist, und setzen Sie es dann ein, um die erwähnten Punkte zu überwachen.

#### Interne Anwendungsüberwachung {#internal-application-monitoring}

Die interne Anwendungsüberwachung umfasst die Überwachung der Anwendungskomponenten, aus denen die [!DNL Experience Manager] stapeln, einschließlich JVM, des Inhalts-Repositorys und Überwachung durch benutzerdefinierten Anwendungscode, der auf der Plattform erstellt wurde. Im Allgemeinen wird dies mithilfe von JMX MBeans durchgeführt, die mit vielen beliebten Überwachungslösungen, z. B. SolarWinds (TM), HP OpenView(TM), Hyperic(TM), Zabbix(TM) und anderen, direkt überwacht werden können. Für Systeme, für die keine direkte Verbindung mit JMX unterstützt wird, können Sie Shell-Skripte schreiben, um die JMX-Daten zu extrahieren und für diese Systeme in einem Format verfügbar zu machen, das nativ verstanden wird.

Der Remotezugriff auf die JMX MBeans ist standardmäßig nicht aktiviert. Weitere Informationen zur Überwachung per JMX finden Sie unter [Überwachung und Verwaltung per JMX-Technologie](https://docs.oracle.com/javase/7/docs/technotes/guides/management/agent.html).

In vielen Fällen ist für das effektive Überwachen eines statistischen Werts ein Ausgangswert (Baseline) erforderlich. Zum Erstellen einer Baseline beobachten Sie das System über einen bestimmten Zeitraum unter normalen Arbeitsbedingungen und ermitteln dann die Metrik für diesen Normalfall.

**JVM-Überwachung**

Wie bei jedem Java-basierten Anwendungsstapel [!DNL Experience Manager] hängt von den Ressourcen ab, die über die zugrunde liegende Java Virtual Machine bereitgestellt werden. Sie können den Status von vielen dieser Ressourcen über Platform MXBeans überwachen, die per JVM verfügbar gemacht werden. Weitere Informationen zu MXBeans finden Sie unter [Verwenden von Platform MBean Server und Platform MXBeans](https://docs.oracle.com/javase/7/docs/technotes/guides/management/mxbeans.html).

Hier sind einige Baselineparameter angegeben, die Sie für JVM überwachen können:

Arbeitsspeicher

* `MBean: lava.lang:type=Memory`
* URL: */system/console/jmx/java.lang:type=Memory*
* Instanzen: Alle Server
* Alarmschwellenwert: Wenn die Arbeitsspeicherauslastung (Heap oder Nicht-Heap) 75 % der jeweiligen maximalen Arbeitsspeichergröße überschreitet.
* Alarmdefinition: Entweder ist der Arbeitsspeicher des Systems unzureichend oder der Code weist ein Speicherleck auf. Analysieren Sie eine Thread-Sicherungskopie, um eine Definition zu erhalten.

**Hinweis**: Die von diesem Bean-Element gelieferten Informationen werden in Byte ausgedrückt.

Threads

* MBean: `java.lang:type=Threading`
* URL: */system/console/jmx/java.lang:type=Threading*
* Instanzen: Alle Server
* Alarmschwellenwert: Wenn die Anzahl von Threads größer als 150 % des Ausgangswerts ist.
* Alarmdefinition: Entweder ist ein aktiver ausufernder Prozess vorhanden, oder ein ineffizienter Vorgang verbraucht eine große Menge von Ressourcen. Analysieren Sie eine Thread-Sicherungskopie, um eine Definition zu erhalten.

**[!DNL Experience Manager]Monitoring**

[!DNL Experience Manager] stellt über JMX auch einen Satz mit Statistiken und Vorgängen bereit. Diese Daten können dazu beitragen, die Systemintegrität zu bewerten und potenzielle Probleme zu identifizieren, bevor sie für Benutzer eine Beeinträchtigung darstellen. Weitere Informationen finden Sie in der [Dokumentation](/help/sites-administering/jmx-console.md) zu JMX MBeans.[!DNL Experience Manager]

Im Folgenden finden Sie einige Ausgangsparameter, die Sie überwachen können [!DNL Experience Manager]:

Replikationsagenten

* MBean: `com.adobe.granite.replication:type=agent,id=”<AGENT_NAME>”`
* URL: */system/console/jmx/com.adobe.granite.replication:type=agent,id=”&lt;AGENT-NAME>”*
* Instanzen: Eine Autoren- und alle Veröffentlichungsinstanzen (für Flush-Agenten)
* Alarmschwellenwert: Wenn der Wert von `QueueBlocked` „true“ lautet oder der Wert von `QueueNumEntries` größer als 150 % der Baseline ist.

* Alarmdefinition: Blockierte Warteschlange im System. Dies ist ein Hinweis darauf, dass das Replikationsziel ausgefallen oder nicht erreichbar ist. Häufig führen Netzwerk- oder Infrastrukturprobleme dazu, dass eine übermäßig hohe Zahl von Einträgen in eine Warteschlange eingereiht wird, und dies kann sich negativ auf die Systemleistung auswirken.

**Hinweis**: Ersetzen Sie für die Parameter MBean und URL `<AGENT_NAME>` mit dem Namen des Replikationsagenten, den Sie überwachen möchten.

Sitzungszähler

* MBean: `org.apache.jackrabbit.oak:id=7,name="OakRepository Statistics",type="RepositoryStats"`
* URL: */system/console/jmx/org.apache.jackrabbit.oak:id=7,name=&quot;OakRepository Statistics&quot;,type*=&quot;RepositoryStats&quot;
* Instanzen: Alle Server
* Alarmschwellenwert: Wenn geöffnete Sitzungen die Baseline um mehr als 50 % überschreiten.
* Alarmdefinition: Sitzungen werden ggf. über einen Teil des Codes geöffnet und nicht geschlossen. Dies kann im Laufe der Zeit langsam erfolgen und schließlich zu Speicherlecks im System führen. Es ist zwar normal, dass die Anzahl von Sitzungen in einem System schwankt, aber sie sollte nicht beständig ansteigen.

Konsistenzprüfungen

Konsistenzprüfungen, die über das [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md#health-reports) durchgeführt werden können, verfügen über entsprechende JMX MBeans für die Überwachung. Sie können aber benutzerdefinierte Konsistenzprüfungen schreiben, um zusätzliche Systemstatistiken bereitzustellen.

Hier sind einige im Lieferumfang enthaltene Konsistenzprüfungen aufgeführt, die für die Überwachung verwendet werden können:

* Systemprüfungen

   * MBean: `org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck*
   * Instanzen: ein Autoren-, alle Veröffentlichungsserver
   * Alarmschwellenwert: Wenn der Status nicht „OK“ lautet.
   * Alarmdefinition: Der Status einer dieser Metriken lautet entweder WARN oder CRITICAL. Weitere Informationen zur Ursache des Problems finden Sie unter dem Protokollattribut.

* Replikations-Warteschlange

   * MBean: `org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck*
   * Instanzen: ein Autoren-, alle Veröffentlichungsserver
   * Alarmschwellenwert: Wenn der Status nicht „OK“ lautet.
   * Alarmdefinition: Der Status einer dieser Metriken lautet entweder WARN oder CRITICAL. Weitere Informationen zu der Warteschlange, die das Problem verursacht hat, finden Sie unter dem Protokollattribut.

* Antwortleistung

   * MBean: `org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck*
   * Instanzen: Alle Server
   * Alarmdauer: Wenn der Status nicht „OK“ lautet.
   * Alarmdefinition: Der Status einer dieser Metriken lautet entweder WARN oder CRITICAL. Weitere Informationen zu der Warteschlange, die das Problem verursacht hat, finden Sie unter dem Protokollattribut.

* Abfrageleistung

   * MBean: `org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name= queriesStatus,type=HealthCheck*
   * Instanzen: ein Autoren-, alle Veröffentlichungsserver
   * Alarmschwellenwert: Wenn der Status nicht „OK“ lautet.
   * Alarmdefinition: Mindestens eine Abfrage im System wird nur langsam ausgeführt. Weitere Informationen zu den Abfragen, die das Problem verursachen, finden Sie unter dem Protokollattribut.

* Aktive Bundles

   * MBean: org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck*
   * Instanzen: Alle Server
   * Alarmschwellenwert: Wenn der Status nicht „OK“ lautet.
   * Alarmdefinition: Inaktive oder ungelöste OSGi-Bundles im System. Weitere Informationen zu den Bundles, die das Problem verursachen, finden Sie unter dem Protokollattribut.

* Fehlerprotokoll

   * MBean: `org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck*
   * Instanzen: Alle Server
   * Alarmschwellenwert: Wenn der Status nicht „OK“ lautet.
   * Alarmdefinition: Die Protokolldateien enthalten Fehler. Weitere Informationen zur Ursache des Problems finden Sie unter dem Protokollattribut.

## Häufige Probleme und Lösungen  {#common-issues-and-resolutions}

Im Rahmen der Überwachung können Sie, wenn Sie auf Probleme stoßen, einige Fehlerbehebungsaufgaben ausführen, um häufige Probleme mit [!DNL Experience Manager] Instanzen:

* Führen Sie die Tar-Komprimierung häufig durch, falls Sie TarMK nutzen. Weitere Informationen finden Sie unter [Wartung des Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
* Überprüfen `OutOfMemoryError` Protokolle. Weitere Informationen finden Sie unter [Analysieren von Speicherproblemen](https://helpx.adobe.com/de/experience-manager/kb/AnalyzeMemoryProblems.html).
* Prüfen Sie die Protokolle auf Verweise auf nicht indizierte Abfragen, Baumstrukturdurchläufe oder Indexdurchläufe. Dies deutet auf nicht indizierte bzw. fehlerhaft indizierte Abfragen hin. Best Practices zur Optimierung der Abfrage- und Indizierungsleistung finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
* Verwenden Sie die Workflow-Konsole, um sicherzustellen, dass Ihre Workflows erwartungsgemäß durchgeführt werden. Fassen Sie mehrere Workflows nach Möglichkeit zu einem einzelnen Workflow zusammen.
* Suchen Sie über die Live-Überwachung nach weiteren Engpässen oder einem hohen Verbrauch bestimmter Ressourcen.
* Untersuchen Sie die Ausspeisepunkte aus dem Client-Netzwerk und die Einspeisung verweist auf die [!DNL Experience Manager] Instanznetzwerk, einschließlich Dispatcher. Häufig sind dies Bereiche, in denen es zu Engpässen kommt. Weitere Informationen finden Sie unter [Überlegungen zum Assets-Netzwerk](assets-network-considerations.md).
* Aktualisieren Sie Ihre [!DNL Experience Manager] Server. Möglicherweise haben Sie eine unzureichende Größe [!DNL Experience Manager] -Instanz. Der Kundensupport von Adobe kann Ihnen dabei helfen, festzustellen, ob Ihr Server zu groß ist.
* Untersuchen Sie die Dateien `access.log` und `error.log` auf Einträge, die zu Fehlerzeitpunkten erstellt wurden. Suchen Sie nach Mustern, die ggf. auf Anomalien im benutzerdefinierten Code hinweisen. Fügen Sie diese der Liste mit den zu überwachenden Ereignissen hinzu.
