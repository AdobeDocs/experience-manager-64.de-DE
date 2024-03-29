---
title: Überwachen von AEM Forms-Bereitstellungen
seo-title: Monitoring AEM forms deployments
description: Sie können AEM Formularbereitstellungen sowohl auf Systemebene als auch auf interner Ebene überwachen. Erfahren Sie mehr über das Überwachen von AEM Forms-Bereitstellungen für dieses Dokument.
seo-description: You can monitor AEM forms deployments from both a system level and an internal level. Learn more about monitoring AEM forms deployments from this document.
uuid: 032b7a93-3069-4ad5-a8c6-4c160f290669
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b3e7bca0-5aaf-4f28-bddb-fd7e8ed72ee8
exl-id: d2cd532b-4086-4553-ac26-f311da6d5ca9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 34%

---

# Überwachen von AEM Forms-Bereitstellungen {#monitoring-aem-forms-deployments}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können AEM Formularbereitstellungen sowohl auf Systemebene als auch auf interner Ebene überwachen. Sie können spezialisierte Verwaltungswerkzeuge wie HP OpenView, IBM Tivoli und CA UniCenter sowie einen JMX-Monitor eines Drittanbieters mit dem Namen *JConsole* , um speziell die Java-Aktivität zu überwachen. Die Implementierung einer Überwachungsstrategie verbessert die Verfügbarkeit, Zuverlässigkeit und Leistung Ihrer AEM Formularbereitstellungen.

Weitere Informationen zum Überwachen AEM Formularbereitstellungen finden Sie unter [Ein technischer Leitfaden zur Überwachung AEM Formularbereitstellungen](https://www.adobe.com/devnet/livecycle/pdfs/lc_monitoring_wp_ue.pdf

).

## Überwachung mit MBeans {#monitoring-using-mbeans}

AEM forms bietet zwei registrierte MBeans, die Navigations- und Statistikinformationen bereitstellen. Dies sind die einzigen MBeans, die für Integration und Inspektion unterstützt werden:

* **ServiceStatistic:** Diese MBean stellt Informationen über den Dienstnamen und die Version bereit.
* **OperationStatistic:** Diese MBean stellt die Statistik jedes Formularserverdienstes bereit. Hier können Administratoren Informationen zu einem bestimmten Dienst abrufen, z. B. Aufrufzeit, Fehleranzahl usw.

### Öffentliche ServiceStatisticMbean-Schnittstellen {#servicestatisticmbean-public-interfaces}

Auf diese öffentlichen Schnittstellen von ServiceStatistic MBean kann zu Testzwecken zugegriffen werden:

```as3
 public String getServiceId();  
 public int getMajorVersion();  
 public int getMinorVersion();
```

### Öffentliche OperationStatisticMbean-Schnittstellen {#operationstatisticmbean-public-interfaces}

Auf diese öffentlichen Schnittstellen von OperationStatistic MBean kann zu Testzwecken zugegriffen werden:

```as3
 // InvocationCount: The number of times the method is invoked.  
 public long getInvocationCount();  
 // InvocationStartTime: The time at which the method started to execute.  
 public long getInvocationStartTime();  
 // InvocationEndTime: The time at which the method finished execution.  
 public long getInvocationEndTime();  
 // InvocationTime: The time taken for the execution of the method.  
 public long getInvocationTime();  
 // LastSamplingDateTime: Convert InvocationStartTime to a formatted string  
 public String getLastSamplingDateTime();  
 // MaxInvocationTime: The maximum time taken for the execution of the method.  
 public long getMaxInvocationTime();  
 // MinInvocationTime: The minimum time taken for the execution of the method.  
 public long getMinInvocationTime();  
 // AverageInvocationTime: the averege execution time taken for the execution of the method.  
 public double getAverageInvocationTime();  
 // ExceptionCount: The number of times the method has thrown an Exception.  
 public long getExceptionCount();  
 // ExceptionMessage: The message of the last exception occurred.  
 public String getExeptionMessage();  
 public void setExceptionMessage(String errorMessage);
```

### MBean Tree &amp; Operation Statistics {#mbean-tree-operation-statistics}

Mithilfe einer JMX-Konsole (JConsole) sind Statistiken von OperationStatistic MBean verfügbar. Diese Statistiken sind Attribute von MBean und können unter der folgenden Hierarchiestruktur navigiert werden:

**MBean-Struktur**

**Adobe-Domain-Name:** Hängt vom Anwendungsserver ab. Wenn der Anwendungsserver die Domain nicht definiert, lautet die Standard-Domain „adobe.com“.

**ServiceType:** AdobeService ist der Name, der zum Auflisten aller Services verwendet wird.

**AdobeServiceName:** Service-Name oder Service-ID.

**Version:** Version des Service.

**Vorgangsstatistiken**

**Aufrufzeit:** Die Dauer für die Ausführung der Methode. Dies schließt nicht die Zeit ein, die zum Serialisieren der Anfrage, zum Übertragen der Anfrage vom Client zum Server und zum Deserialisieren erforderlich ist.

**Anzahl der Aufrufe:** Die Häufigkeit, mit der der Service aufgerufen wird.

**Durchschnittliche Aufrufzeit:** Durchschnittliche Zeit aller Aufrufe, die seit dem Start des Servers ausgeführt wurden.

**Maximale Aufrufzeit:** Die Dauer des längsten Aufrufs, der seit dem Start des Servers ausgeführt wurde.

**Minimale Aufrufzeit:** Die Dauer des kürzesten Aufrufs, der seit dem Start des Servers ausgeführt wurde.

**Anzahl der Ausnahmen:** Anzahl der Aufrufe, bei denen Fehler aufgetreten sind.

**Ausnahmemeldung:** Die Fehlermeldung über die letzte aufgetretene Ausnahme.

**Letztes Sampling: Datum, Zeit:** Das Datum des letzten Aufrufs.

**Zeiteinheit:** Der Standardwert ist Millisekunde.

Um die JMX-Überwachung zu aktivieren, benötigen die Anwendungsserver in der Regel einige Konfigurationen. Weitere Informationen finden Sie in der Dokumentation zum Anwendungsserver .

### Beispiele zum Einrichten eines offenen JMX-Zugriffs {#examples-of-how-to-set-up-open-jmx-access}

**JBoss 4.0.3/4.2.0 - Konfigurieren des JVM-Starts**

Um MBeans von JConsole anzuzeigen, konfigurieren Sie die JVM-Startparameter des JBoss-Anwendungsservers. Stellen Sie sicher, dass JBoss über die Datei &quot;run.bat/sh&quot;gestartet wurde.

1. Bearbeiten Sie die Datei &quot;run.bat&quot;, die sich unter &quot;InstallJBoss/bin&quot;befindet.
1. Suchen Sie die Zeile JAVA_OPTS und fügen Sie Folgendes hinzu:

   ```as3
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

**WebLogic 9.2/10 - JVM-Start konfigurieren**

1. Bearbeiten Sie die Datei &quot;startWebLogic.bat&quot;, die sich unter &quot;*&quot;befindet. [WebLogic-Homepage]*/user_projects/domains/Adobe_Live_Cycle/bin.
1. Suchen Sie die Zeile JAVA_OPTS und fügen Sie Folgendes hinzu:

   ```as3
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

1. Starten Sie WebLogic neu.

>[!NOTE]
>
>Für WebLogic können Sie über Remote oder IIOP auf das MBean zugreifen.

**Remote-Zugriff auf MBean**

1. Starten Sie JConsole für neue Verbindung und klicken Sie auf die Registerkarte Remote .
1. Geben Sie den Hostnamen und Port ein (9088, die Nummer, die Sie bei den Startoptionen von JVM angegeben haben).

**Websphere 6.1 - JVM-Start konfigurieren**

1. Fügen Sie in der Admin Console (Anwendungsserver > Server1 > Prozessdefinition > JVM) die folgende Zeile in das Feld für das generische JVM-Argument hinzu:

   ```as3
    -Djavax.management.builder.initial= -Dcom.sun.management.jmxremote
   ```

1. Fügen Sie die folgenden drei Zeilen in der Datei /opt/IBM/WebSphere/AppServer/java/jre/lib/management/management.properties hinzu oder heben Sie die Auskommentierung auf (oder &lt;your websphere=&quot;&quot; jre=&quot;&quot;>lib/management/management.properties):

   ```as3
    com.sun.management.jmxremote.port=9999 //any port you like, but make sure you use this port when you connect  
    com.sun.management.jmxremote.authenticate=false  
    com.sun.management.jmxremote.ssl=false
   ```

1. Starten Sie WebSphere neu.
