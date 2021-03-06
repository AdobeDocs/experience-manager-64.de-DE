---
title: Datenspeicherbereinigung
seo-title: Data Store Garbage Collection
description: Erfahren Sie, wie Sie die Datenspeicherbereinigung zur Freigabe von Festplattenspeicher konfigurieren können.
seo-description: Learn how to configure Data Store Garbage Collection to free up disk space.
uuid: 1f49e9e9-3a0d-4687-844d-8a32fb30f2b4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5ee9d11a-85c2-440d-b487-a38d04dc040b
exl-id: 83b9a9cb-3f86-472b-b9dc-6ec633003481
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1888'
ht-degree: 80%

---

# Datenspeicherbereinigung {#data-store-garbage-collection}

Wenn ein herkömmliches WCM-Asset entfernt wird, kann der Verweis zum zugrunde liegenden Datenspeichersatz aus der Knotenhierarchie entfernt werden. Der Datenspeichersatz selbst bleibt allerdings bestehen. Dieser nicht referenzierte Datenspeichersatz wird dadurch zu „Garbage“, der nicht aufbewahrt werden muss. In Instanzen mit einer Reihe von Garbage-Assets ist es von Vorteil, diese loszuwerden, um Speicherplatz zu behalten und um die Sicherung sowie die Leistung bei der Dateisystemwartung zu optimieren.

Meist neigen WCM-Anwendungen dazu, Informationen zu sammeln. Gelöscht werden die Informationen allerdings bei Weitem nicht so oft. Auch wenn neue Bilder hinzugefügt werden und sogar wenn alte Versionen ersetzt werden, behält das Versionskontrollsystem dennoch die alte Version bei und unterstützt bei Bedarf die Möglichkeit, zu dieser Version zurückzukehren. Daher wird der Großteil der Inhalte, die wir zum System hinzufügen, permanent gespeichert. Was ist also die typische Quelle für „Garbage“ im Repository, die wir bereinigen möchten?

AEM verwendet das Repository als Speicher für eine Reihe von internen Aktivitäten und Bereinigungsaktivitäten:

* Zusammengestellte und heruntergeladene Pakete
* Für die Veröffentlichungsreplikation erstellte temporäre Dateien
* Workflow-Payload
* Während des DAM-Renderings temporär erstellte Assets

Wenn eines dieser temporären Objekte groß genug ist, Speicherplatz im Datenspeicher zu beanspruchen, und wenn das Objekt schließlich nicht mehr genutzt wird, bleibt der Datenspeichersatz selbst als „Garbage“ vorhanden. In einer typischen WCM-Autoren-/Veröffentlichungsanwendung ist die größte Quelle von „Garbage“ dieser Art in der Regel der Prozess der Aktivierung der Veröffentlichung. Wenn Daten auf Publish repliziert werden, werden sie zunächst in Sammlungen in einem effizienten Datenformat namens &quot;Durbo&quot;erfasst und im Repository unter `/var/replication/data`. Die Datenbundles übersteigen oft den kritischen Größenschwellenwert für den Datenspeicher und werden daher als Datenspeichersätze gespeichert. Wenn die Replikation abgeschlossen ist, wird der Knoten in `/var/replication/data` wird gelöscht, aber der Datenspeichersatz bleibt als &quot;Müll&quot;.

Eine weitere Quelle von wiederherstellbarem Garbage sind Pakete. Paketdaten werden – wie alles andere auch – im Repository und bei Paketen, die größer sind als 4 KB, im Datenspeicher gespeichert. Während eines Entwicklungsprojekts oder im Laufe der Zeit können Pakete bei der Wartung eines Systems viele Male zusammengestellt und neu erstellt werden, wobei jede Version zu einem neuen Datenspeichersatz führt, durch den der Datensatz der vorherigen Version verwaist.

## Wie funktioniert die automatische Datenspeicherbereinigung? {#how-does-data-store-garbage-collection-work}

Wenn das Repository mit einem externen Datenspeicher konfiguriert wurde, [wird die automatische Datenspeicherbereinigung im Rahmen des wöchentlichen Wartungsfensters automatisch ausgeführt](/help/sites-administering/data-store-garbage-collection.md#automating-data-store-garbage-collection). Der Systemadministrator kann auch [Ausführen der automatischen Datenspeicherbereinigung](#running-data-store-garbage-collection) nach Bedarf. Im Allgemeinen wird empfohlen, dass die Datenspeicherbereinigung regelmäßig durchgeführt wird, doch die folgenden Faktoren sollten bei der Planung von Datenspeicherbereinigungen berücksichtigt werden:

* Datenspeicherbereinigungen nehmen Zeit in Anspruch und können die Leistung beieinträchtigen, was entsprechend eingeplant werden sollte.
* Das Entfernen der „Garbage“-Datensätze im Datenspeicher hat keinen Einfluss auf die normale Leistung. Es handelt sich also nicht um eine Leistungsoptimierung.
* Wenn die Speichernutzung und damit verbundene Faktoren wie die Sicherungszeiten kein Problem darstellen, kann die automatische Datenspeicherbereinigung auf sichere Weise zeitlich verschoben werden.

Der Datenspeicherbereiniger merkt sich zunächst den aktuellen Zeitstempel, wenn der Prozess beginnt. Die Sammlung der Daten wird mithilfe eines Multi-Pass-Mark-/Sweep-Pattern-Algorithmus durchgeführt.

In der ersten Phase führt der Datenspeicherbereiniger einen umfassenden Durchlauf durch die gesamten Repository-Inhalte durch. Zu jedem Inhaltsobjekt mit einem Verweis zum Datenspeichersatz sucht er die Datei im Dateisystem, führt eine Metadatenaktualisierung durch und ändert das „Zuletzt geändert“- oder MTIME-Attribut. An diesem Punkt erhalten Dateien, auf die in dieser Phase zugegriffen wurde, einen neueren Zeitstempel als den ursprünglichen Baseline-Zeitstempel.

In der zweiten Phase durchläuft der Datenspeicherbereiniger die physische Verzeichnisstruktur des Datenspeichers auf eine sehr ähnliche Weise wie eine Suche. Er untersucht das „Zuletzt geändert“- oder MTIME-Attribut der Datei und bestimmt Folgendes:

* Wenn das MTIME neuer als der ursprüngliche Baseline-Zeitstempel ist, wurde die Datei entweder in der ersten Phase gefunden oder es handelt sich um eine völlig neue Datei, die dem Repository während des laufenden Bereinigungsprozesses hinzugefügt wurde. In beiden Fällen wird der Datensatz als aktiv betrachtet und die Datei ist nicht zu löschen.
* Wenn das MTIME-Attribut vor dem ursprünglichen Baseline-Zeitstempel liegt, handelt es sich bei der Datei nicht um eine aktiv referenzierte Datei und sie wird als entfernbarer „Garbage“ betrachtet.

Dieser Ansatz funktioniert bei einem einzelnen Knoten mit einem privaten Datenspeicher sehr gut. Handelt es sich jedoch um einen freigegebenen Datenspeicher, bedeutet dies, dass potenziell aktive Live-Verweise auf Datenspeichersätze von anderen Repositorys nicht geprüft werden und dass aktive referenzierte Dateien gegebenenfalls fälschlicherweise entfernt werden. Der Systemadministrator muss vor der Planung jedweder Datenspeicherbereinigungen auf jeden Fall über die Freigabestruktur des Datenspeichers Bescheid wissen. Er darf nur dann den einfachen integrierten Prozess zur automatischen Datenspeicherbereinigung verwenden, wenn bekannt ist, dass der Datenspeicher nicht freigegeben ist.

>[!NOTE]
>
>Wenn Sie die automatische Bereinigung für einen eingerichteten Cluster- oder freigegebenen Speicher (mit Mongo oder Segment-Tar) durchführen, werden im Protokoll möglicherweise Warnungen angezeigt, wonach bestimmte Blob-IDs nicht gelöscht werden können. Dies geschieht, weil Blob-IDs, die in einer vorherigen Speicherbereinigung gelöscht wurden, fälschlicherweise von anderen Cluster- oder freigegebenen Knoten referenziert werden, die keine Informationen über die ID-Löschungen haben. Daher wird bei der automatischen Bereinigung eine Warnung protokolliert, wenn versucht wird, eine bereits im vorherigen Durchgang gelöschte ID zu entfernen. Dieses Verhalten wirkt sich weder auf die Leistung noch auf die Funktionalität aus.

## Ausführen der automatischen Datenspeicherbereinigung {#running-data-store-garbage-collection}

Die automatische Datenspeicherbereinigung kann je nach dem eingerichteten Datenspeicher, auf dem AEM ausgeführt wird, auf drei Arten erfolgen:

1. Via [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md) - ein Speicherbereinigungsmechanismus, der normalerweise für die Bereinigung von Knotenspeichern verwendet wird.

1. Über die [Automatische Datenspeicherbereinigung](/help/sites-administering/data-store-garbage-collection.md#running-data-store-garbage-collection-via-the-operations-dashboard) – ein Bereinigungsmechanismus speziell für externe Datenspeicher, der im Vorgangs-Dashboard verfügbar ist
1. Über die [JMX-Konsole](/help/sites-administering/jmx-console.md)

Wenn TarMK sowohl als Knotenspeicher als auch als Datenspeicher verwendet wird, kann die Versionsbereinigung für beide Speicher eingesetzt werden. Wenn jedoch ein externer Datenspeicher wie der Dateisystemdatenspeicher konfiguriert ist, muss die Datenspeicherbereinigung explizit und separat von der Versionsbereinigung ausgelöst werden. Automatische Datenspeicherbereinigung kann über das Vorgangs-Dashboard oder die JMX-Konsole ausgelöst werden.

In der folgenden Tabelle sind die Speicherbereinigungstypen aufgeführt, die für alle unterstützten Datenspeicherbereitstellungen in AEM 6 zu verwenden sind:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Knotenspeicher</strong><br /> </td> 
   <td><strong>Datenspeicher</strong></td> 
   <td><strong>Abfallsammlung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>TarMK</td> 
   <td>TarMK</td> 
   <td>Revisionsbereinigung (Binärdateien sind mit dem Segmentspeicher verknüpft)</td> 
  </tr> 
  <tr> 
   <td>TarMK</td> 
   <td>Externes Dateisystem</td> 
   <td><p>Aufgabe zur automatischen Datenspeicherbereinigung über das Vorgangs-Dashboard</p> <p>JMX-Konsole</p> </td> 
  </tr> 
  <tr> 
   <td>MongoDB</td> 
   <td>MongoDB</td> 
   <td><p>Aufgabe zur automatischen Datenspeicherbereinigung über das Vorgangs-Dashboard</p> <p>JMX-Konsole</p> </td> 
  </tr> 
  <tr> 
   <td>MongoDB</td> 
   <td>Externes Dateisystem</td> 
   <td><p>Aufgabe zur automatischen Datenspeicherbereinigung über das Vorgangs-Dashboard</p> <p>JMX-Konsole</p> </td> 
  </tr> 
 </tbody> 
</table>

### Ausführen der automatischen Datenspeicherbereinigung über das Vorgangs-Dashboard {#running-data-store-garbage-collection-via-the-operations-dashboard}

Das integrierte, über das [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md) verfügbare wöchentliche Wartungsfenster beinhaltet die integrierte Aufgabe, die Datenspeicherbereinigung sonntags um 1 Uhr nachts durchzuführen.

Wenn Sie die automatische Datenspeicherbereinigung zu einem anderen Zeitpunkt ausführen müssen, kann diese auch manuell über das Vorgangs-Dashboard ausgelöst werden.

Vor der Ausführung der automatischen Datenspeicherbereinigung sollten Sie prüfen, ob zu dem Zeitpunkt keine Sicherungen ausgeführt werden.

1. Öffnen Sie das Vorgangs-Dashboard über **Navigation** > **Tools** > **Vorgänge** > **Wartung**.
1. Klicken oder tippen Sie auf **Wöchentliches Wartungsfenster**.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Wählen Sie die Aufgabe **Automatische Datenspeicherbereinigung** und klicken oder tippen Sie auf das Symbol **Ausführen**.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. Die automatische Datenspeicherbereinigung wird ausgeführt und der Status wird im Dashboard angezeigt.

   ![chlimage_1-123](assets/chlimage_1-123.png)

>[!NOTE]
>
>Die Aufgabe zur Durchführung der automatischen Datenspeicherbereinigung wird nur angezeigt, wenn Sie einen externen Dateidatenspeicher konfiguriert haben. Siehe [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](/help/sites-deploying/data-store-config.md#file-data-store) für Informationen zum Einrichten eines Dateidatenspeichers.

### Ausführen der automatischen Datenspeicherbereinigung über die JMX-Konsole {#running-data-store-garbage-collection-via-the-jmx-console}

In diesem Abschnitt wird die manuelle Ausführung der automatischen Datenspeicherbereinigung über die JMX-Konsole erläutert. Wenn Ihre Installation ohne einen externen Datenspeicher eingerichtet wurde, gilt dies nicht für Ihre Installation. Sehen Sie sich stattdessen die Anweisungen zur Ausführung der Versionsbereinigung unter [Wartung von Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository) an.

>[!NOTE]
>
>Wenn Sie TarMK mit einem externen Datenspeicher ausführen, müssen Sie zunächst die Versionsbereinigung ausführen, damit die Speicherbereinigung effektiv sein kann.

So führen Sie die Speicherbereinigung durch:

1. Markieren Sie in der Apache Felix OSGi Management Console die Registerkarte **Main** und wählen Sie aus dem folgenden Menü **JMX** aus
1. Suchen Sie danach und klicken Sie auf die **Repository Manager** MBean (oder navigieren Sie zu `https://<host>:<port>/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Drepository+manager%2Ctype%3DRepositoryManagement`).
1. Klicken Sie auf **startDataStoreGC(boolean markOnly)**.
1. eingeben`true`&quot; für die `markOnly` Parameter, falls erforderlich:

   | **Option** | **Beschreibung** |
   |---|---|
   | boolean markOnly | Auf &quot;true&quot;setzen, um nur Verweise zu markieren und nicht im Mark- und Sweep-Vorgang zu fegen. Dieser Modus wird verwendet, wenn der zugrunde liegende BlobStore für mehrere verschiedene Repositorys freigegeben ist. Setzen Sie den Parameter in allen anderen Fällen auf „false“, um eine vollständige Speicherbereinigung durchzuführen. |

1. Klicken Sie auf **Invoke**. CRX führt die Speicherbereinigung durch und zeigt an, wenn diese abgeschlossen ist.

>[!NOTE]
>
>Die automatische Datenspeicherbereinigung erfasst keine Dateien, die in den letzten 24 Stunden gelöscht wurden.

>[!NOTE]
>
>Die Aufgabe zur automatischen Datenspeicherbereinigung wird nur gestartet, wenn Sie einen externen Dateidatenspeicher konfiguriert haben. Wenn kein externer Dateidatenspeicher konfiguriert wurde, gibt die Aufgabe die Nachricht zurück `Cannot perform operation: no service of type BlobGCMBean found` nach dem Aufrufen. Siehe [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](/help/sites-deploying/data-store-config.md#file-data-store) für Informationen zum Einrichten eines Dateidatenspeichers.

## Automatisieren der automatischen Datenspeicherbereinigung {#automating-data-store-garbage-collection}

Wenn möglich sollte die automatische Datenspeicherbereinigung ausgeführt werden, wenn das System nicht stark ausgelastet ist – so zum Beispiel am Morgen.

Das integrierte, über das [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md) verfügbare wöchentliche Wartungsfenster beinhaltet die integrierte Aufgabe, die Datenspeicherbereinigung sonntags um 1 Uhr nachts durchzuführen. Sie sollten außerdem überprüfen, ob zu diesem Zeitpunkt keine Sicherungen durchgeführt werden. Der Start des Wartungsfensters kann bei Bedarf über das Dashboard angepasst werden.

>[!NOTE]
>
>Der Grund dafür, sie nicht gleichzeitig auszuführen, besteht darin, dass alte (und nicht verwendete) Datenspeicherdateien ebenfalls gesichert werden, sodass die Binärdateien immer noch im Backup vorhanden sind, wenn sie auf eine alte Revision zurückgesetzt werden müssen.

Wenn Sie die automatische Datenspeicherbereinigung nicht mit dem wöchentlichen Wartungsfenster im Vorgangs-Dashboard ausführen möchten, kann sie auch mit den HTTP-Clients wget oder curl automatisiert werden. Im Folgenden finden Sie ein Beispiel für die Automatisierung der Sicherung mithilfe von curl:

>[!CAUTION]
>
>Im folgenden Beispiel müssen gegebenenfalls verschiedene Parameter des `curl`-Befehls für Ihre Instanz konfiguriert werden, so zum Beispiel Hostname (`localhost`), Port (`4502`), Admin-Kennwort (`xyz`) und verschiedene Parameter für die tatsächliche automatische Datenspeicherbereinigung.

Im Folgenden finden Sie ein Beispiel für einen curl-Befehl zum Aufrufen der automatischen Datenspeicherbereinigung über die Befehlszeile:

```shell
curl -u admin:admin -X POST --data markOnly=true  http://localhost:4503/system/console/jmx/org.apache.jackrabbit.oak"%"3Aname"%"3Drepository+manager"%"2Ctype"%"3DRepositoryManagement/op/startDataStoreGC/boolean
```

Der curl-Befehl wird sofort zurückgegeben.

## Prüfen der Datenspeicherkonsistenz {#checking-data-store-consistency}

Die Datenspeicherkonsistenzprüfung meldet sämtliche fehlenden Datenspeicherbinärdateien, die dennoch referenziert werden. Führen Sie die folgenden Schritte aus, um eine Konsistenzprüfung zu starten:

1. Gehen Sie zur JMX-Konsole. Informationen zur Verwendung der JMX-Konsole finden Sie unter [diesem Artikel](/help/sites-administering/jmx-console.md#using-the-jmx-console).

1. Suchen Sie nach dem MBean **Blob GC** und klicken Sie darauf.

1. Klicken Sie auf `checkConsistency()` Link.

Nach dem Abschluss der Konsistenzprüfung wird eine Meldung mit der Zahl der als fehlend gemeldeten Binärdateien angezeigt. Ist die Zahl größer als 0, prüfen Sie das `error.log`, um weitere Details zu fehlenden Binärdateien anzuzeigen.

Im Folgenden finden Sie ein Beispiel dafür, wie die fehlenden Binärdateien in den Protokollen gemeldet werden:

```xml
11:32:39.673 INFO [main] MarkSweepGarbageCollector.java:600 Consistency check found [1] missing blobs
```

```xml
11:32:39.673 WARN [main] MarkSweepGarbageCollector.java:602 Consistency check failure in the blob store : DataStore backed BlobStore [org.apache.jackrabbit.oak.plugins.blob.datastore.OakFileDataStore], check missing candidates in file /tmp/gcworkdir-1467352959243/gccand-1467352959243
```
