---
title: Fehlerbehebung bei Replikationsproblemen
seo-title: Troubleshooting Replication
description: Dieser Artikel enthält Informationen zur Fehlerbehebung bei Replikationsproblemen.
seo-description: This article provides information on how to troubleshoot replication issues.
uuid: 7c3fdaad-0916-4159-a26c-17ff8c6617fe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: configuring
discoiquuid: e862c8a9-b5b6-4857-a154-03d3ffac3e67
feature: Configuring
exl-id: e83317bb-e69c-4e2c-92f8-4f613786e7ae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 58%

---

# Fehlerbehebung bei Replikationsproblemen{#troubleshooting-replication}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Auf dieser Seite finden Sie Informationen zur Fehlerbehebung bei Replikationsproblemen.

## Problem {#problem}

Die Replikation (Nicht-Rückwärtsreplikation) schlägt aus irgendeinem Grund fehl.

## Auflösung {#resolution}

Es gibt verschiedene Gründe, warum eine Replikation fehlschlägt. In diesem Artikel wird der Ansatz erläutert, den man bei der Analyse dieser Probleme wählen könnte.

**Werden beim Klicken auf die Schaltfläche „Aktivieren“ irgendwelche Replikationen ausgelöst? Wenn NICHT, gehen Sie wie folgt vor:**

1. Gehen Sie zu /crx/explorer (CQ5.5) und melden Sie sich als Administrator an.
1. Öffnen Sie &quot;Content Explorer&quot;.
1. Überprüfen Sie, ob der Knoten „/bin/replicate“ oder „/bin/replicate.json“ vorhanden ist. Wenn der Knoten vorhanden ist, löschen Sie ihn und speichern Sie ihn.

**Werden die Replikationen in den Warteschlangen des Replikationsagenten in die Warteschlange gestellt?**

Wechseln Sie zu /etc/replication/agents.author.html und klicken Sie dann auf die Replikationsagenten, um dies zu überprüfen.

**Wenn eine oder einige Agentenwarteschlangen hängen geblieben sind:**

1. Lautet der Status der Warteschlange **gesperrt**? Wenn dies der Fall ist, wird die Veröffentlichungsinstanz nicht ausgeführt oder reagiert sie überhaupt nicht? Überprüfen Sie die Veröffentlichungsinstanz, um das Problem zu ermitteln (d. h. überprüfen Sie die Protokolle, um festzustellen, ob der Fehler „OutOfMemory“ oder ein anderes Problem vorliegt). Wenn es dann im Allgemeinen langsam ist, nehmen Sie Thread-Dumps und analysieren Sie sie.
1. Lautet der Status der Warteschlange **Warteschlange ist aktiv - x ausstehend**? Möglicherweise wurde der Replikationsauftrag durch einen SocketRead-Vorgang unterbrochen und wartet auf eine Reaktion der Veröffentlichungsinstanz oder des Dispatchers. Das bedeutet, dass u. U. eine hohe Last auf der Veröffentlichungsinstanz oder dem Dispatcher vorliegt oder dass diese durch eine Sperre unterbrochen wurden. Nehmen Sie in diesem Fall Thread-Sicherheitskopien von der Autoren- und Veröffentlichungsinstanz vor.

   * Öffnen Sie die Thread-Sicherheitskopien von der Autoreninstanz in einem Thread-Dump-Analyzer und überprüfen Sie, ob der Sling-Ereignisauftrag des Replikationsagenten in einem socketRead-Vorgang feststeckt.
   * Öffnen Sie die Thread-Sicherungskopien der Veröffentlichungsinstanz in einem Analyzer für Thread-Sicherungskopien und analysieren Sie, aus welchen Grund die Veröffentlichungsinstanz möglicherweise nicht reagiert. Dabei sollte ein Thread mit „POST /bin/receive“ im Namen angezeigt werden. Dies ist der Thread, der die Replikation von der Autoreninstanz empfängt.

**Wenn alle Agentenwarteschlangen hängen geblieben sind:**

1. Möglicherweise kann ein bestimmter Teil des Inhalts aufgrund eines beschädigten Repositorys oder eines anderen Problems nicht unter /var/replication/data serialisiert werden. Überprüfen Sie die Datei „logs/error.log“ auf einen entsprechenden Fehler. Gehen Sie wie folgt vor, um das fehlerhafte Replikationselement zu entfernen:

   1. Gehen Sie zu https://&lt;host>:&lt;port>/crx und melden Sie sich als Administrator an. Gehen Sie in CQ5.5 zu https://&lt;host>:&lt;port>/crx/explorer .
   1. Klicken Sie auf &quot;Content Explorer&quot;.
   1. Klicken Sie im Fenster &quot;Content Explorer&quot; auf die Lupe rechts oben im Fenster und ein Suchdialogfeld wird angezeigt.
   1. Wählen Sie das Optionsfeld &quot;XPath&quot;.
   1. Geben Sie in das Feld &quot;Abfrage&quot;die Abfrage /jcr:root/var/eventing/jobs//element(&amp;ast;,slingevent:Job) order by @slingevent:created ein.
   1. Klicken Sie auf &quot;Suchen&quot;
   1. Die in den Ergebnissen ganz oben angezeigten Elemente sind die aktuellen Sling-Eventing-Aufträge. Klicken Sie auf jedes Element und suchen Sie nach den feststeckenden Replikationen, die mit denen oben in der Warteschlange übereinstimmen.

1. Möglicherweise liegt ein Problem mit den Auftragswarteschlangen des Sling-Eventing-Frameworks vor. Versuchen Sie, das Bundle org.apache.sling.event in der /system/console neu zu starten.
1. Möglicherweise ist die Auftragsverarbeitung vollständig deaktiviert. Dies kann in der Felix-Konsole auf der Registerkarte „Sling Eventing“ überprüft werden. Überprüfen Sie, ob es angezeigt wird - Apache Sling Eventing (JOB PROCESSING IST DEAKTIVIERT!)

   * Ist dies der Fall, überprüfen Sie auf der Registerkarte „Configuration“ der Felix-Konsole den Apache Sling Job Event Handler. Möglicherweise ist das Kontrollkästchen für „Job Processing Enabled“ deaktiviert. Falls es aktiviert ist und weiter „Job Processing Disabled“ angezeigt wird, überprüfen Sie, ob unter „/apps/system/config“ eine Überlagerung vorhanden ist, die die Auftragsverarbeitung deaktiviert. Versuchen Sie, einen osgi:config -Knoten für jobmanager.enabled mit einem booleschen Wert &quot;true&quot;zu erstellen und überprüfen Sie erneut, ob die Aktivierung gestartet wurde und keine Aufträge mehr in der Warteschlange sind.

1. Möglicherweise ist auch der Status der Konfiguration „DefaultJobManager“ inkonsistent. Dies kann vorkommen, wenn jemand die Konfiguration &quot;Apache Sling Job Event Handler&quot;über die OSGiconsole manuell ändert (z. B. die Eigenschaft &quot;Job Processing Enabled&quot;deaktivieren und erneut aktivieren und die Konfiguration speichern).

   * Dies führt dazu, dass der Status der unter „crx-quickstart/launchpad/config/org/apache/sling/event/impl/jobs/DefaultJobManager.config“ gespeicherten Konfiguration für „DefaultJobManager“ inkonsistent wird. Obwohl die Eigenschaft &quot;Apache Sling Job Event Handler&quot;anzeigt, dass &quot;Job Processing Enabled&quot;aktiviert ist, wird beim Navigieren zur Registerkarte &quot;Sling Eventing&quot;die Meldung &quot;JOB PROCESSING IS DISABLED&quot;angezeigt und die Replikation funktioniert nicht.
   * Um dieses Problem zu beheben, müssen Sie zur Seite „Konfiguration“ der OSGi-Konsole navigieren und die Konfiguration „Apache Sling Job Event Handler“ löschen. Starten Sie dann den Master-Knoten des Clusters neu, um den Status der Konfiguration wieder konsistent zu machen. Dadurch sollte das Problem behoben werden, und die Replikation funktioniert wieder.

**Erstellen Sie eine replication.log**

In manchen Fällen kann es hilfreich sein, wenn alle Replikationsprotokolle auf DEBUG-Ebene in separate Protokolldateien geschrieben werden. Gehen Sie hierfür wie folgt vor:

1. Navigieren Sie zu `https://host:port/system/console/configMgr` und melden Sie sich als Administrator an.
1. Suchen Sie nach der Apache Sling Logging Logger-Factory-Konfiguration und erstellen Sie eine Instanz, indem Sie auf die **+**-Schaltfläche rechts neben der Factory-Konfiguration klicken. Dadurch wird eine neue Protokollierungslogger erstellt.
1. Legen Sie die Konfiguration wie folgt fest:

   * Protokollierungsebene: DEBUG
   * Protokolldateipfad: *(CQ5.4 und 5.3)* ../logs/replication.log *(CQ5.5)* logs/replication.log
   * Kategorien: com.day.cq.replication

1. Wenn Sie vermuten, dass das Problem in irgendeiner Weise mit Sling-Eventing/Aufträgen in Verbindung steht, können Sie dieses Java-Paket auch unter Kategorien hinzufügen: org.apache.sling.event

### Anhalten der Replikationsagenten-Warteschlange  {#pausing-replication-agent-queue}

In manchen Fällen ist es u. U. nützlich, die Replikations-Warteschlange anzuhalten, um die Last auf dem Autorensystem zu reduzieren, ohne dieses zu deaktivieren. Dies ist derzeit nur durch das vorübergehende Konfigurieren eines ungültigen Ports möglich. Ab 5.4 können Sie die Pausenschaltfläche in der Warteschlange des Replikationsagenten sehen. Sie hat einige Einschränkungen.

1. Der Status wird nicht beibehalten. Wenn Sie einen Server neu starten oder ein Replikations-Bundle recycelt wird, wird der Status wieder ausgeführt.
1. Beim Anhalten für kurze Zeiträume tritt ein Leerlauf ein (OOB nach einer Stunde ohne Aktivitäten mit Replikation durch andere Threads), nicht jedoch für längere Zeiträume. Dies liegt an einer Funktion von Apache Sling, die Threads im Leerlauf verhindert. Überprüfen Sie also, ob ein Auftragswarteschlangen-Thread länger nicht verwendet wurde. Ist dies der Fall, werden Bereinigungszyklen gestartet. Durch den Bereinigungszyklus wird der Thread gestoppt und die Einstellung zum Anhalten wird nicht beibehalten. Da Aufträge gespeichert werden, wird ein neuer Thread zum Verarbeiten der Warteschlange initiiert, der keine Details über die angehaltene Konfiguration umfasst. Aufgrund dieser Warteschlange wird der Status &quot;Wird ausgeführt&quot;.

### Seitenberechtigungen werden bei der Benutzeraktivierung nicht repliziert {#page-permissions-are-not-replicated-on-user-activation}

Seitenberechtigungen werden nicht repliziert, da sie für die Knoten gespeichert werden, auf die Zugriff erteilt wird, und nicht für die Benutzer.

Im Allgemeinen sollten Seitenberechtigungen nicht von der Autoreninstanz auf der Veröffentlichungsinstanz repliziert werden und stellen keine Standardeinstellung dar. Der Grund hierfür ist, das die Zugriffsrechte in diesen beiden Umgebungen unterschiedlich sein müssen. Daher wird empfohlen, ACLs auf der Veröffentlichungsinstanz separat vom Autor zu konfigurieren.

### Replikations-Warteschlange blockiert bei der Replikation von Namespace-Informationen vom Autor zur Veröffentlichung {#replication-queue-blocked-when-replicating-namespace-information-from-author-to-publish}

In einigen Fällen wird die Replikations-Warteschlange beim Versuch blockiert, Namensrauminformationen von der Autoreninstanz auf die Veröffentlichungsinstanz zu replizieren. Dies geschieht, weil der Replikationsbenutzer nicht die Berechtigung `jcr:namespaceManagement` hat. Um dieses Problem zu vermeiden, stellen Sie Folgendes sicher:

* Der Replikationsbenutzer (wie auf der Registerkarte [Transport](/help/sites-deploying/replication.md#replication-agents-configuration-parameters) unter „Benutzer“ konfiguriert) existiert auch auf der Veröffentlichungsinstanz.
* Der Benutzer hat Lese- und Schreibrechte für den Pfad, in dem der Inhalt installiert ist.
* Der Benutzer hat die Berechtigung `jcr:namespaceManagement` auf Repository-Ebene. Sie können die Berechtigungen wie folgt erteilen:

1. Melden Sie sich als Admin bei CRX/DE (`http://localhost:4502/crx/de/index.jsp`) an.
1. Klicken Sie auf **Zugriffssteuerung** Registerkarte.
1. Auswählen **Repository**.
1. Klicken **Eintrag hinzufügen** (das Pluszeichen).
1. Geben Sie den Namen des Benutzers ein.
1. Wählen Sie in der Liste der Berechtigungen `jcr:namespaceManagement` aus.
1. Klicken Sie auf „OK“.
