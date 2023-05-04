---
title: Asset-Überwachung – Best Practices
description: Best Practices zur Überwachung der Umgebung und Leistung Ihrer [!DNL Experience Manager] Instanz nach der Bereitstellung.
contentOwner: AG
feature: Asset Management
role: Admin,Architect
exl-id: edbb275a-5ead-4ed2-8708-29e766081d75
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 27%

---

# Assets-Überwachung – Best Practices {#assets-monitoring-best-practices}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Aus Sicht von Adobe Experience Manager Assets sollte die Überwachung die Beobachtung und Berichterstattung zu den folgenden Prozessen und Technologien umfassen:

* SystemCPU
* Systemspeicherauslastung
* IO- und IO-Wartezeit der Systemdiskette
* Systemnetzwerk-IO
* JMX MBeans für:

   * Heap-Auslastung
   * Asynchrone Prozesse, z. B. Workflows

* Integritätsprüfungen der OSGi-Konsole

Normalerweise kann die Überwachung in [!DNL Assets] auf zwei Arten durchgeführt werden: Live-Überwachung und Langzeitüberwachung.

## Live-Überwachung {#live-monitoring}

Sie sollten während der Leistungstestphase Ihrer Entwicklung oder in Situationen mit hoher Auslastung eine Live-Überwachung durchführen, um die Leistungsmerkmale Ihrer Umgebung zu verstehen. Normalerweise sollte die Live-Überwachung mit einer Suite von Tools durchgeführt werden. Im Folgenden finden Sie einige Empfehlungen:

* [Visual VM](https://visualvm.github.io/): Mit Visual VM können Sie ausführliche Java-VM-Informationen anzeigen, z. B. CPU-Auslastung oder Java-Speicherauslastung. Darüber hinaus können Sie Code, der auf einer Instanz ausgeführt wird, testen und auswerten.
* [Oben](https://man7.org/linux/man-pages/man1/top.1.html): Oben ist ein Linux-Befehl, der ein Dashboard öffnet, das Nutzungsstatistiken anzeigt, einschließlich CPU-, Speicher- und I/O-Nutzung. Er bietet einen allgemeinen Überblick darüber, was auf einer Instanz geschieht.
* [oberste](https://hisham.hm/htop/): Htop ist ein interaktiver Prozess-Viewer. Zusätzlich zu den von Top bereitgestellten Funktionen bietet es eine detaillierte CPU- und Speicherbelegung. „Htop“ kann auf den meisten Linux-Systemen mit dem Befehl `yum install htop` oder `apt-get install htop` installiert werden.

* [Iotop](https://guichaz.free.fr/iotop/): Iotop ist ein detailliertes Dashboard zur Verwendung von Datenträger-IO. Darin werden anhand von Balken und Anzeigen die Prozesse, für die Datenträger-I/O-Vorgänge genutzt werden, sowie die verwendete Menge dargestellt. „Iotop“ kann auf den meisten Linux-Systemen mit dem Befehl `yum install iotop` oder `apt-get install iotop` installiert werden.

* [iftop](https://www.ex-parrot.com/pdw/iftop/): Wenn Sie detaillierte Informationen zur Ethernet-/Netzwerknutzung anzeigen. Iftop zeigt die Statistiken der einzelnen Kommunikationskanäle über die Entitäten an, die das Ethernet verwenden, und die Menge der von ihnen verwendeten Bandbreite. „Iftop“ kann auf den meisten Linux-Systemen mit dem Befehl `yum install iftop` oder `apt-get install iftop` installiert werden.

* Java Flight Recorder (JFR): Ein kommerzielles Tool von Oracle, das Sie in Umgebungen, die nicht für die Produktion bestimmt sind, kostenlos nutzen können. Ausführliche Informationen finden Sie unter [Verwenden von Java Flight Recorder zum Diagnostizieren von CQ-Laufzeitproblemen](https://cq-ops.tumblr.com/post/73865704329/how-to-use-java-flight-recorder-to-diagnose-cq).
* [!DNL Experience Manager] error.log-Datei: Sie können die [!DNL Experience Manager] error.log für Details zu den im System protokollierten Fehlern. Verwenden Sie den Befehl `tail -F quickstart/logs/error.log` um Fehler zu identifizieren, die Sie untersuchen sollten.
* [Workflow-Konsole](../sites-administering/workflows.md): Nutzen Sie die Workflow-Konsole, um Workflows zu überwachen, die Verzögerungen aufweisen oder hängen.

Normalerweise verwenden Sie diese Tools zusammen, um eine umfassende Vorstellung von der Leistung Ihrer [!DNL Experience Manager] -Instanz.

>[!NOTE]
>
>Diese Tools sind Standardwerkzeuge und werden von Adobe nicht direkt unterstützt. Sie benötigen keine zusätzlichen Lizenzen.

![chlimage_1-142](assets/chlimage_1-142.png) ![chlimage_1-143](assets/chlimage_1-143.png)

## Langfristige Überwachung {#long-term-monitoring}

Langfristige Überwachung einer [!DNL Experience Manager] -Instanz umfasst die Überwachung der gleichen Live-Übertragungen für eine längere Dauer. Sie umfasst auch die Definition von Warnhinweisen, die speziell für Ihre Umgebung gelten.

### Protokollaggregation und Reporting {#log-aggregation-and-reporting}

Es gibt verschiedene Tools zum Aggregieren von Protokollen, z. B. Splunk(TM) und Elastic Search/Logstash/Kabana (ELK). So beurteilen Sie die Betriebszeit Ihrer [!DNL Experience Manager] müssen Sie beispielsweise die für Ihr System spezifischen Protokollereignisse verstehen und Warnhinweise erstellen, die auf ihnen basieren. Wenn Sie Ihre Entwicklungs- und Betriebsabläufe gut kennen, können Sie den Prozess der Protokollaggregation besser optimieren, um kritische Warnungen zu generieren.

### Umgebungsüberwachung {#environment-monitoring}

Die Umgebungsüberwachung umfasst die Überwachung folgender Elemente:

* Netzwerkdurchsatz
* Datenträger-E
* Arbeitsspeicher
* CPU-Auslastung
* JMX MBeans
* Externe Websites

Sie benötigen externe Tools wie NewRelic(TM) und AppDynamics(TM), um jedes Element zu überwachen. Mithilfe dieser Tools können Sie systemspezifische Warnhinweise definieren, z. B. hohe Systemauslastung, Workflow-Sicherung, Fehler bei der Konsistenzprüfung oder nicht authentifizierten Zugriff auf Ihre Website. Adobe empfiehlt keine bestimmten Tools gegenüber anderen. Suchen Sie nach dem Tool, das für Sie funktioniert, und nutzen Sie es, um die diskutierten Elemente zu überwachen.

#### Interne Anwendungsüberwachung {#internal-application-monitoring}

Die interne Anwendungsüberwachung umfasst das Überwachen der Anwendungskomponenten, aus denen der [!DNL Experience Manager]-Stapel besteht, z. B. JVM, das Inhalts-Repository und die Überwachung mit benutzerdefiniertem Anwendungs-Code, der auf der Plattform erstellt wird. Im Allgemeinen wird sie über JMX MBeans durchgeführt, die direkt von vielen beliebten Überwachungslösungen wie SolarWinds (TM), HP OpenView(TM), Hyperic(TM), Zabbix(TM) und anderen überwacht werden können. Für Systeme, die keine direkte Verbindung zu JMX unterstützen, können Sie Shell-Skripte schreiben, um die JMX-Daten zu extrahieren und für diese Systeme in einem Format verfügbar zu machen, das sie nativ verstehen.

Der Remotezugriff auf die JMX MBeans ist standardmäßig nicht aktiviert. Weitere Informationen zur Überwachung per JMX finden Sie unter [Überwachung und Verwaltung per JMX-Technologie](https://docs.oracle.com/javase/7/docs/technotes/guides/management/agent.html).

In vielen Fällen ist eine Grundlinie erforderlich, um eine Statistik effektiv zu überwachen. Um eine Grundlinie zu erstellen, beobachten Sie das System unter normalen Arbeitsbedingungen für einen vorab festgelegten Zeitraum und identifizieren Sie dann die normale Metrik.

**JVM-Überwachung**

Wie alle Java-basierten Anwendungsstapel ist auch [!DNL Experience Manager] von den Ressourcen abhängig, die über die zugrunde liegende Java Virtual Machine bereitgestellt werden. Sie können den Status vieler dieser Ressourcen über Platform MXBeans überwachen, die von JVM verfügbar gemacht werden. Weitere Informationen zu MXBeans finden Sie unter [Verwenden von Platform MBean Server und Platform MXBeans](https://docs.oracle.com/javase/7/docs/technotes/guides/management/mxbeans.html).

Hier sind einige Baseline-Parameter angegeben, die Sie für JVM überwachen können:

Arbeitsspeicher

* `MBean: lava.lang:type=Memory`
* URL: */system/console/jmx/java.lang:type=Memory*
* Instanzen: Alle Server
* Alarmschwellenwert: Wenn die Heap- oder Nicht-Heap-Speicherauslastung 75 % des entsprechenden maximalen Speichers überschreitet.
* Alarmdefinition: Entweder ist der Systemspeicher unzureichend oder der Code weist ein Speicherleck auf. Analysieren Sie einen Thread-Dump, um zu einer Definition zu gelangen.

**Hinweis**: Die von diesem Bean bereitgestellten Informationen werden in Byte ausgedrückt.

Threads

* MBean: `java.lang:type=Threading`
* URL: */system/console/jmx/java.lang:type=Threading*
* Instanzen: Alle Server
* Alarmschwellenwert: Wenn die Anzahl der Threads größer ist als 150 % der Baseline.
* Alarmdefinition: Entweder gibt es einen aktiven Runaway-Prozess oder ein ineffizienter Vorgang verbraucht eine große Menge an Ressourcen. Analysieren Sie einen Thread-Dump, um zu einer Definition zu gelangen.

**[!DNL Experience Manager]Monitoring**

[!DNL Experience Manager] stellt über JMX auch einen Satz mit Statistiken und Vorgängen bereit. Diese Daten können dazu beitragen, die Systemintegrität zu bewerten und potenzielle Probleme zu identifizieren, bevor sie für Benutzende eine Beeinträchtigung darstellen. Weitere Informationen finden Sie in der [Dokumentation](/help/sites-administering/jmx-console.md) zu [!DNL Experience Manager] JMX MBeans.

Hier sind einige Baseline-Parameter angegeben, die Sie für [!DNL Experience Manager] überwachen können:

Replikationsagenten

* MBean: `com.adobe.granite.replication:type=agent,id=”<AGENT_NAME>”`
* URL: */system/console/jmx/com.adobe.granite.replication:type=agent,id=&quot;&lt;agent_name>&quot;*
* Instanzen: Eine Autoren- und alle Veröffentlichungsinstanzen (für Flush-Agenten)
* Alarmschwellenwert: Wenn der Wert von `QueueBlocked` ist &quot;true&quot;oder der Wert von `QueueNumEntries` ist größer als 150% des Ausgangswertes.

* Alarmdefinition: Vorhandensein einer blockierten Warteschlange im System, die angibt, dass das Replikationsziel ausfällt oder nicht erreichbar ist. Häufig führen Netzwerk- oder Infrastrukturprobleme dazu, dass übermäßige Einträge in die Warteschlange gestellt werden, was die Systemleistung beeinträchtigen kann.

**Hinweis**: Ersetzen Sie für die Parameter MBean und URL `<AGENT_NAME>` mit dem Namen des Replikationsagenten, den Sie überwachen möchten.

Sitzungszähler

* MBean: `org.apache.jackrabbit.oak:id=7,name="OakRepository Statistics",type="RepositoryStats"`
* URL: */system/console/jmx/org.apache.jackrabbit.oak:id=7,name=&quot;OakRepository Statistics&quot;,type*=&quot;RepositoryStats&quot;
* Instanzen: Alle Server
* Alarmschwellenwert: Wenn offene Sitzungen die Grundlinie um mehr als 50 % überschreiten.
* Alarmdefinition: Sitzungen können durch einen Code geöffnet und nie geschlossen werden. Dies kann im Laufe der Zeit langsam passieren und schließlich zu Speicherlecks im System führen. Während die Anzahl der Sitzungen in einem System schwanken sollte, sollten sie nicht kontinuierlich steigen.

Konsistenzprüfungen

Konsistenzprüfungen, die in der [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md#health-reports) über entsprechende JMX MBeans zur Überwachung verfügen. Sie können jedoch benutzerdefinierte Konsistenzprüfungen schreiben, um zusätzliche Systemstatistiken verfügbar zu machen.

Im Folgenden finden Sie einige vordefinierte Konsistenzprüfungen, die zur Überwachung hilfreich sind:

* Systemprüfungen

   * MBean: `org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck*
   * Instanzen: Ein Autor, alle Veröffentlichungs-Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Der Status einer dieser Metriken lautet entweder WARN oder CRITICAL. Weitere Informationen zur Ursache des Problems finden Sie im Protokollattribut.

* Replikations-Warteschlange

   * MBean: `org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck*
   * Instanzen: Ein Autor, alle Veröffentlichungs-Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Der Status einer dieser Metriken lautet entweder WARN oder CRITICAL. Überprüfen Sie das Protokollattribut auf weitere Informationen zur Warteschlange, die das Problem verursacht hat.

* Antwortleistung

   * MBean: `org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck*
   * Instanzen: Alle Server
   * Alarmdauer: Wenn der Status nicht OK ist
   * Alarmdefinition: Der Status einer dieser Metriken lautet entweder WARN oder CRITICAL. Überprüfen Sie das Protokollattribut auf weitere Informationen zur Warteschlange, die das Problem verursacht hat.

* Abfrageleistung

   * MBean: `org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name= queriesStatus,type=HealthCheck*
   * Instanzen: Ein Autor, alle Veröffentlichungs-Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Eine oder mehrere Abfragen werden im System langsam ausgeführt. Weitere Informationen zu den Abfragen, die das Problem verursacht haben, finden Sie im Protokollattribut .

* Aktive Bundles

   * MBean: org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck*
   * Instanzen: Alle Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Vorhandensein inaktiver oder ungelöster OSGi-Bundles im System. Weitere Informationen zu den Bundles, die das Problem verursacht haben, finden Sie im Protokollattribut .

* Fehlerprotokoll

   * MBean: `org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck*
   * Instanzen: Alle Server
   * Alarmschwellenwert: Wenn der Status nicht OK ist
   * Alarmdefinition: Die Protokolldateien enthalten Fehler. Weitere Informationen zur Ursache des Problems finden Sie im Protokollattribut.

## Häufige Probleme und Lösungen  {#common-issues-and-resolutions}

Im Rahmen der Überwachung können Sie, wenn Sie auf Probleme stoßen, einige Fehlerbehebungsaufgaben ausführen, um häufige Probleme mit [!DNL Experience Manager] Instanzen:

* Führen Sie die Tar-Komprimierung häufig durch, falls Sie TarMK nutzen. Weitere Informationen finden Sie unter [Wartung des Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
* Überprüfen Sie die `OutOfMemoryError`-Protokolle. Weitere Informationen finden Sie unter [Analysieren von Speicherproblemen](https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html).
* Überprüfen Sie die Protokolle auf Verweise auf unindizierte Abfragen, Baumdurchläufe oder Indexdurchläufe. Diese weisen auf nicht indizierte Abfragen oder unzureichend indizierte Abfragen hin. Best Practices zur Optimierung der Abfrage- und Indizierungsleistung finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
* Überprüfen Sie mithilfe der Workflow-Konsole, ob Ihre Workflows erwartungsgemäß funktionieren. Schließen Sie nach Möglichkeit mehrere Workflows in einen einzigen Workflow zusammen.
* Suchen Sie über die Live-Überwachung nach weiteren Engpässen oder einem hohen Verbrauch bestimmter Ressourcen.
* Untersuchen Sie die Ausspeisepunkte aus dem Client-Netzwerk und die Einspeisung verweist auf die [!DNL Experience Manager] Instanznetzwerk, einschließlich Dispatcher. Häufig handelt es sich um Engpässe. Weitere Informationen finden Sie unter [Überlegungen zum Assets-Netzwerk](assets-network-considerations.md).
* Aktualisieren Sie Ihre [!DNL Experience Manager] Server. Möglicherweise haben Sie eine unzureichende Größe [!DNL Experience Manager] -Instanz. Der Adobe Kunden-Support kann Sie dabei unterstützen, festzustellen, ob Ihr Server ggf. zu klein ausgelegt ist.
* Untersuchen Sie die Dateien `access.log` und `error.log` auf Einträge, die zu Fehlerzeitpunkten erstellt wurden. Suchen Sie nach Mustern, die möglicherweise auf benutzerdefinierte Code-Anomalien hinweisen. Fügen Sie sie zur Liste der Ereignisse hinzu, die Sie überwachen.
