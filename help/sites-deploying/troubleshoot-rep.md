---
title: Fehlerbehebung bei Replikationsproblemen
seo-title: Troubleshooting Replication
description: Dieser Artikel stellt Informationen zur Fehlerbehebung bei Replikationsproblemen bereit.
seo-description: This article provides information on how to troubleshoot replication issues.
uuid: 7c3fdaad-0916-4159-a26c-17ff8c6617fe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: configuring
discoiquuid: e862c8a9-b5b6-4857-a154-03d3ffac3e67
feature: Configuring
exl-id: e83317bb-e69c-4e2c-92f8-4f613786e7ae
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1270'
ht-degree: 80%

---

# Fehlerbehebung bei Replikationsproblemen{#troubleshooting-replication}

Diese Seite stellt Informationen zur Fehlerbehebung bei Replikationsproblemen bereit.

## Problem {#problem}

Die Replikation (nicht die Rückwärtsreplikation) schlägt aus irgendeinem Grund fehl.

## Auflösung {#resolution}

Es gibt verschiedene Gründe, warum eine Replikation fehlschlägt. Dieser Artikel beschreibt die mögliche Vorgehensweise beim Analysieren der Probleme.

**Werden beim Klicken auf die Schaltfläche „Aktivieren“ irgendwelche Replikationen ausgelöst? Falls NICHT, gehen Sie wie folgt vor:**

1. Gehen Sie zu /crx/explorer (CQ5.5) und melden Sie sich als Administrator an.
1. Öffnen Sie „Content Explorer“.
1. Überprüfen Sie, ob der Knoten „/bin/replicate“ oder „/bin/replicate.json“ vorhanden ist. Falls er vorhanden ist, löschen Sie den Knoten und speichern Sie die Änderung.

**Werden die Replikationen in den Warteschlangen der Replikationsagenten gespeichert?**

Gehen Sie dazu zu /etc/replication/agents.author.html und klicken Sie dann auf die Replikationsagenten, die überprüft werden sollen.

**Wenn eine oder einige Agentenwarteschlangen hängen geblieben sind:**

1. Zeigt die Warteschlange an **blockiert** status? Wenn dies der Fall ist, wird die Veröffentlichungsinstanz nicht ausgeführt oder reagiert sie überhaupt nicht? Überprüfen Sie die Veröffentlichungsinstanz, um das Problem zu ermitteln (d. h. überprüfen Sie die Protokolle, um festzustellen, ob der Fehler „OutOfMemory“ oder ein anderes Problem vorliegt). Wenn die Instanz nur allgemein langsam ist, analysieren Sie die Thread-Sicherungskopien.
1. Zeigt den Warteschlangenstatus an **Warteschlange ist aktiv - # ausstehend**? Möglicherweise wurde der Replikationsauftrag durch einen SocketRead-Vorgang unterbrochen und wartet auf eine Reaktion der Veröffentlichungsinstanz oder des Dispatchers. Das bedeutet, dass u. U. eine hohe Last auf der Veröffentlichungsinstanz oder dem Dispatcher vorliegt oder dass diese durch eine Sperre unterbrochen wurden. Überprüfen Sie in diesem Fall die Thread-Sicherungskopien der Autoren- und Veröffentlichungsinstanzen.

   * Öffnen Sie die Thread-Sicherungskopien der Autoreninstanz in einem Analyzer für Thread-Sicherungskopien und prüfen Sie, ob der Sling-Eventing-Auftrag des Replikationsagenten durch einen SocketRead-Vorgang unterbrochen wurde.
   * Öffnen Sie die Thread-Sicherungskopien der Veröffentlichungsinstanz in einem Analyzer für Thread-Sicherungskopien und analysieren Sie, aus welchen Grund die Veröffentlichungsinstanz möglicherweise nicht reagiert. Sie sollten einen Thread mit der POST /bin/receive im Namen sehen, d. h. den Thread, der die Replikation von der Autoreninstanz erhält.

**Wenn alle Agentenwarteschlangen hängen geblieben sind:**

1. Es ist möglich, dass ein bestimmtes Inhaltselement aufgrund einer Beschädigung des Repositorys oder eines anderen Problems nicht unter /var/replication/data serialisiert werden kann. Überprüfen Sie logs/error.log auf einen zugehörigen Fehler. Gehen Sie wie folgt vor, um das fehlerhafte Replikationselement zu entfernen:

   1. Gehen Sie zu https://&lt;host>:&lt;port>/crx und melden Sie sich als Administrator an. Gehen Sie in CQ5.5 zu https://&lt;host>:&lt;port>/crx/explorer .
   1. Klicken Sie auf „Content Explorer“.
   1. Klicken Sie im Fenster „Content Explorer“ in der oberen rechten Ecke auf die Schaltfläche mit der Lupe. Daraufhin wird ein Suchdialogfeld angezeigt.
   1. Wählen Sie die Optionsschaltfläche „XPath“ aus.
   1. Geben Sie in das Feld &quot;Abfrage&quot;die Abfrage /jcr:root/var/eventing/jobs//element(&amp;ast;,slingevent:Job) order by @slingevent:created ein.
   1. Klicken Sie auf „Suchen“.
   1. Die in den Ergebnissen ganz oben angezeigten Elemente sind die aktuellen Sling-Eventing-Aufträge. Klicken Sie auf die einzelnen Aufträge, um nach den unterbrochenen Replikationen zu suchen, die mit dem oben in der Warteschlange Angezeigten übereinstimmen.

1. Möglicherweise liegt ein Problem mit den Auftragswarteschlangen des Sling-Eventing-Frameworks vor. Versuchen Sie, das Bundle „org.apache.sling.event“ in „/system/console“ neu zu starten.
1. Möglicherweise ist die Auftragsverarbeitung vollständig deaktiviert. Dies kann in der Felix-Konsole auf der Registerkarte „Sling Eventing“ überprüft werden. Prüfen Sie, ob Folgendes angezeigt wird: „Apache Sling Eventing (JOB PROCESSING IS DISABLED!“)

   * Ist dies der Fall, überprüfen Sie auf der Registerkarte „Configuration“ der Felix-Konsole den Apache Sling Job Event Handler. Möglicherweise ist das Kontrollkästchen für „Job Processing Enabled“ deaktiviert. Falls es aktiviert ist und weiter „Job Processing Disabled“ angezeigt wird, überprüfen Sie, ob unter „/apps/system/config“ eine Überlagerung vorhanden ist, die die Auftragsverarbeitung deaktiviert. Versuchen Sie, einen „osgi:config“-Knoten für „jobmanager.enabled“ zu erstellen, dessen boolescher Wert auf „true“ gesetzt ist, und vergewissern Sie sich erneut, ob die Aktivierung gestartet wurde und keine Aufträge mehr in der Warteschlange vorhanden sind.

1. Möglicherweise ist auch der Status der Konfiguration „DefaultJobManager“ inkonsistent. Dies kann vorkommen, wenn die Konfiguration für „Apache Sling Job Event Handler“ über die OSGi-Konsole manuell geändert wird (z. B. durch Deaktivieren und erneutes Aktivieren der Eigenschaft „Job Processing Enabled“ und Speichern der Konfiguration).

   * Dies führt dazu, dass der Status der unter „crx-quickstart/launchpad/config/org/apache/sling/event/impl/jobs/DefaultJobManager.config“ gespeicherten Konfiguration für „DefaultJobManager“ inkonsistent wird. Obwohl die Eigenschaft „Apache Sling Job Event Handler“ anzeigt, dass „Job Processing Enabled“ aktiviert ist, wird auf der Registerkarte „Sling Eventing“ die Nachricht „JOB PROCESSING IS DISABLED“ angezeigt und die Replikation funktioniert nicht.
   * Um dieses Problem zu beheben, müssen Sie zur Konfigurationsseite der OSGi-Konsole navigieren und die Konfiguration &quot;Apache Sling Job Event Handler&quot;löschen. Starten Sie dann den Master-Knoten des Clusters neu, um den Status der Konfiguration wieder konsistent zu machen. Damit sollte das Problem behoben sein und die Replikation sollte wieder funktionieren.

**Erstellen einer „replication.log“-Datei**

In manchen Fällen kann es hilfreich sein, wenn alle Replikationsprotokolle auf DEBUG-Ebene in separate Protokolldateien geschrieben werden. Gehen Sie hierfür wie folgt vor:

1. Navigieren Sie zu `https://host:port/system/console/configMgr` und melden Sie sich als Administrator an.
1. Suchen Sie die Apache Sling Logging Logger-Factory und erstellen Sie eine Instanz, indem Sie auf **+** rechts neben der Werkskonfiguration. Dadurch wird eine neue Logging Logger-Konfiguration erstellt.
1. Richten Sie die Konfiguration wie folgt ein:

   * Protokollebene: DEBUG
   * Protokolldateipfad: *(CQ5.4 und 5.3)* ../logs/replication.log *(CQ5.5)* logs/replication.log
   * Kategorien: com.day.cq.replication

1. Wenn Sie annehmen, dass das Problem in irgendeiner Weise mit „eventing/jobs“ von Sling verknüpft ist, können Sie auch dieses Java-Paket unter „categories:org.apache.sling.event“ hinzufügen.

### Anhalten der Warteschlange des Replikationsagenten  {#pausing-replication-agent-queue}

In manchen Fällen ist es u. U. nützlich, die Replikations-Warteschlange anzuhalten, um die Last auf dem Autorensystem zu reduzieren, ohne dieses zu deaktivieren. Dies ist derzeit nur durch das vorübergehende Konfigurieren eines ungültigen Ports möglich. Ab Version 5.4 steht eine Schaltfläche zum Anhalten für die Warteschlange des Replikations-Agenten zur Verfügung, jedoch mit einigen Einschränkungen.

1. Der Status wird nicht gespeichert, d. h. wenn Sie einen Server neu starten oder ein Replikations-Bundle wiederverwenden, kehrt die Warteschlange wieder in den Ausführungsstatus zurück.
1. Beim Anhalten für kurze Zeiträume tritt ein Leerlauf ein (OOB nach einer Stunde ohne Aktivitäten mit Replikation durch andere Threads), nicht jedoch für längere Zeiträume. Dies liegt an einer Funktion von Apache Sling, die Threads im Leerlauf verhindert. Überprüfen Sie also, ob ein Auftragswarteschlangen-Thread länger nicht verwendet wurde. Ist dies der Fall, werden Bereinigungszyklen gestartet. Durch den Bereinigungszyklus wird der Thread gestoppt und die Einstellung zum Anhalten wird nicht beibehalten. Da Aufträge gespeichert werden, wird ein neuer Thread zum Verarbeiten der Warteschlange initiiert, der keine Details über die angehaltene Konfiguration umfasst. Aus diesem Grund wird die Warteschlange in den Ausführungsstatus gesetzt.

### Seitenberechtigungen werden bei der Benutzeraktivierung nicht repliziert {#page-permissions-are-not-replicated-on-user-activation}

Seitenberechtigungen werden nicht repliziert, da sie für die Knoten gespeichert werden, auf die Zugriff erteilt wird, und nicht für die Benutzer.

Im Allgemeinen sollten Seitenberechtigungen nicht von der Autoreninstanz auf der Veröffentlichungsinstanz repliziert werden und stellen keine Standardeinstellung dar. Der Grund hierfür ist, das die Zugriffsrechte in diesen beiden Umgebungen unterschiedlich sein müssen. Es wird deshalb empfohlen, auf der Veröffentlichungs- und der Autoreninstanz separate Zugriffskontrolllisten (ACLs) zu konfigurieren.

### Replikations-Warteschlange blockiert bei der Replikation von Namensrauminformationen von der Autoren- zur Veröffentlichungsinstanz {#replication-queue-blocked-when-replicating-namespace-information-from-author-to-publish}

In einigen Fällen wird die Replikations-Warteschlange beim Versuch blockiert, Namensrauminformationen von der Autoreninstanz auf die Veröffentlichungsinstanz zu replizieren. Dies geschieht, weil der Replikationsbenutzer nicht über `jcr:namespaceManagement` Berechtigung. Um dieses Problem zu vermeiden, stellen Sie Folgendes sicher:

* Replikationsbenutzer (wie unter der [Verkehr](/help/sites-deploying/replication.md#replication-agents-configuration-parameters) tab>Benutzer) auch in der Veröffentlichungsinstanz vorhanden.
* Der Benutzer hat Lese- und Schreibrechte für den Pfad, in dem der Inhalt installiert ist.
* Der Benutzer hat `jcr:namespaceManagement` auf Repository-Ebene. Sie können die Berechtigungen wie folgt erteilen:

1. Melden Sie sich bei CRX/DE an ( `http://localhost:4502/crx/de/index.jsp`) als Administrator.
1. Klicken Sie auf die Registerkarte **Zugriffssteuerung**.
1. Wählen Sie **Repository** aus.
1. Klicken Sie auf **Eintrag hinzufügen** (das Plussymbol).
1. Geben Sie den Namen des Benutzers ein.
1. Auswählen `jcr:namespaceManagement` aus der Liste der Berechtigungen.
1. Klicken Sie auf OK.
