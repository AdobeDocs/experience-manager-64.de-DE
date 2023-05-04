---
title: Sichern der AEM Forms-Daten
seo-title: Backing up the AEM forms data
description: In diesem Dokument werden die Schritte beschrieben, die zum Ausführen einer Onlinesicherung der AEM Forms-Datenbank, des globalen Dokumentenspeichers und des Stammordners für Inhalte erforderlich sind.
seo-description: This document describes the steps that are required to complete a hot, or online, backup of the AEM forms database, the GDS, and Content Storage Root directories.
uuid: ac7856be-e3b7-4b81-b8b9-fc909b5907b4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 52187196-b091-4683-85ae-cc7c250dee54
exl-id: d86cf58f-6595-4f37-977f-09437a7f89f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1576'
ht-degree: 23%

---

# Sichern der AEM Forms-Daten {#backing-up-the-aem-forms-data}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Abschnitt werden die Schritte beschrieben, die zum Ausführen einer Onlinesicherung der AEM Forms-Datenbank, des globalen Dokumentenspeichers und des Stammordners für Inhalte erforderlich sind.

Nachdem AEM Formulare installiert und in Produktionsbereichen bereitgestellt wurden, sollte der Datenbankadministrator eine vollständige Erstsicherung (Cold Backup) der Datenbank durchführen. Die Datenbank muss für dieses Backup heruntergefahren werden. Anschließend sollten regelmäßig differenzielle oder inkrementelle (oder heiße) Sicherungen der Datenbank durchgeführt werden.

Um eine erfolgreiche Sicherung und Wiederherstellung sicherzustellen, muss jederzeit eine Systemabbildsicherung verfügbar sein. Wenn dann ein Verlust eintritt, können Sie Ihre gesamte Umgebung in einem konsistenten Zustand wiederherstellen.

Durch die gleichzeitige Sicherung der Datenbank mit den Sicherungen des Ordners des globalen Dokumentenspeichers, AEM und des Stammordners für Inhalte können diese Systeme bei Bedarf synchronisiert werden.

Für das in diesem Abschnitt beschriebene Sicherungsverfahren müssen Sie den abgesicherten Sicherungsmodus aktivieren, bevor Sie die AEM Forms-Datenbank, AEM Repository, den Ordner des globalen Dokumentenspeichers und den Stammordner für Inhalte sichern. Nach Abschluss der Sicherung müssen Sie den abgesicherten Sicherungsmodus beenden. Der abgesicherte Sicherungsmodus wird verwendet, um dauerhaft genutzte Dokumente zu kennzeichnen, die sich im globalen Dokumentenspeicher befinden. Dieser Modus stellt sicher, dass der automatisierte Dateibereinigungsmechanismus (der Datei-Wächter) abgelaufene Dateien erst löscht, wenn der abgesicherte Sicherungsmodus verfügbar ist. Die Sicherung des globalen Dokumentenspeichers muss mit einer Datenbanksicherung synchronisiert werden.

Wie oft der Speicherort des globalen Dokumentenspeichers gesichert werden muss, hängt davon ab, wie AEM Formulare verwendet werden und welche Sicherungsfenster verfügbar sind. Das Sicherungsfenster kann durch langlebige Prozesse beeinflusst werden, da sie mehrere Tage lang ausgeführt werden können. Wenn Sie Dateien in diesem Ordner kontinuierlich ändern, hinzufügen und entfernen, sollten Sie den Speicherort des globalen Dokumentenspeichers häufiger sichern.

Wenn die Datenbank, wie im vorherigen Abschnitt beschrieben, im Protokollierungsmodus ausgeführt wird, müssen die Datenbankprotokolle ebenfalls häufig gesichert werden, damit sie im Falle eines Medienfehlers zur Wiederherstellung der Datenbank verwendet werden können.

>[!NOTE]
>
>Dateien, auf die nicht verwiesen wird, bleiben möglicherweise nach dem Wiederherstellungsprozess im Ordner des globalen Dokumentenspeichers erhalten. Dies ist derzeit eine bekannte Einschränkung.

## Sichern Sie die Ordner &quot;Datenbank&quot;, &quot;Ordner des globalen Dokumentenspeichers&quot;, &quot;AEM Repository&quot;und &quot;Stammordner für Inhalte&quot;. {#back-up-the-database-gds-aem-repository-and-content-storage-root-directories}

Sie müssen AEM Formulare entweder im abgesicherten Sicherungsmodus (Snapshot-Modus) oder im kontinuierlichen Sicherungsmodus (kontinuierliche Sicherung) ausführen. Bevor Sie AEM Formulare in einen der Sicherungsmodi einstellen, stellen Sie Folgendes sicher:

* Überprüfen Sie die Systemversion und zeichnen Sie die Patches oder Updates auf, die seit der letzten vollständigen Systemabbildsicherung angewendet wurden.
* Wenn Sie Sicherungen im Rollierenden oder Snapshot-Modus verwenden, stellen Sie sicher, dass Ihre Datenbank mit den richtigen Protokolleinstellungen für Hot-Backups der Datenbank konfiguriert ist. (Siehe [AEM Formulardatenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).

Beachten Sie zusätzlich die folgenden Richtlinien für den Sicherungs-/Wiederherstellungsprozess.

* Sichern Sie den Ordner des globalen Dokumentenspeichers mithilfe eines verfügbaren Betriebssystems oder eines Backup-Dienstprogramms eines Drittanbieters. (Siehe [GDS-Speicherort](/help/forms/using/admin-help/files-back-recover.md#gds-location).
* (Optional) Sichern Sie den Stammordner für Inhalte mithilfe eines verfügbaren Betriebssystems oder eines Sicherungs- und Dienstprogramms eines Drittanbieters. (Siehe [Speicherort des Stammordners für Inhalte (eigenständige Umgebung)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-stand-alone-environment) oder [Speicherort des Stammordners für Inhalte (Clusterumgebung)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-clustered-environment).)
* Sichern Sie  Autor- und Veröffentlichungsinstanzen (Sicherungskopie des CRX-Repository).

   Um die Correspondence Management Solution-Umgebung zu sichern, führen Sie die Schritte für die Autoren- und Veröffentlichungsinstanzen aus, wie unter [Sicherung und Wiederherstellung](/help/sites-administering/backup-and-restore.md).

   Beachten Sie beim Sichern der Autoren- und Veröffentlichungsinstanzen die folgenden Punkte:

   * Stellen Sie sicher, dass die Sicherung für Autoren- und Veröffentlichungsinstanzen synchronisiert wird, um gleichzeitig zu starten. Obwohl Sie Autoren- und Veröffentlichungsinstanzen während der Sicherung weiterhin verwenden können, wird empfohlen, während der Sicherung kein Asset zu veröffentlichen, um nicht erfasste Änderungen zu vermeiden. Warten Sie, bis die Sicherung der Autoren- und Veröffentlichungsinstanzen beendet ist, bevor Sie neue Assets veröffentlichen.
   * Die vollständige Sicherung des Autorknotens umfasst die Sicherung der Daten von Forms Manager und AEM Forms Workspace.
   * Workbench-Entwickler können ihre Prozesse weiterhin lokal bearbeiten. Sie sollten während der Backup-Phase keine neuen Prozesse bereitstellen.
   * Die Entscheidung über die Dauer jeder Sicherungssitzung (für den kontinuierlichen Sicherungsmodus) sollte auf der Gesamtzeit basieren, die zum Sichern aller Daten in AEM Formularen benötigt wird (DB, GDS, AEM Repository und alle anderen zusätzlichen benutzerdefinierten Daten).

Sie sollten die AEM Forms-Datenbank einschließlich aller Transaktionsprotokolle sichern. (Siehe [AEM Formulardatenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database). Weitere Informationen finden Sie im entsprechenden Knowledge Base-Artikel für Ihre Datenbank:

* [Oracle-Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403624)
* [Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403625)
* [Microsoft SQL Server-Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403623)
* [DB2-Sicherung und -Wiederherstellung für AEM Formulare](https://www.adobe.com/go/kb403626)

Diese Artikel enthalten Anleitungen zu grundlegenden Datenbankfunktionen für die Sicherung und Wiederherstellung von Daten. Sie sind nicht als allumfassende technische Leitfäden für die Sicherungs- und Wiederherstellungsfunktion der Datenbank eines bestimmten Anbieters gedacht. Sie beschreiben Befehle, die zum Erstellen einer zuverlässigen Datenbanksicherungsstrategie für Ihre AEM Forms-Anwendungsdaten erforderlich sind.

>[!NOTE]
>
>Die Datenbanksicherung muss abgeschlossen sein, bevor Sie mit der Sicherung des globalen Dokumentenspeichers beginnen. Wenn die Datenbanksicherung nicht abgeschlossen ist, sind Ihre Daten nicht synchronisiert.

### Wechseln der Sicherungsmodi {#entering-the-backup-modes}

Sie können entweder Administration Console, den Befehl &quot;LCBackupMode&quot;oder die mit der AEM Formularinstallation verfügbare API verwenden, um den Sicherungsmodus zu aktivieren und zu beenden. Beachten Sie, dass die Option Administration Console für die kontinuierliche Sicherung nicht verfügbar ist. sollten Sie entweder die Befehlszeilenoption oder die API verwenden. <!-- Fix broken link For information about using the API to enter and leave backup modes, see AEM forms API Reference on Help and Tutorials page. -->

>[!NOTE]
>
>Wenn Sie SSL auf dem Formularserver konfiguriert haben, können Sie den Formularserver nicht mithilfe des Skripts &quot;LCBackupMode.CMD&quot;im Sicherungsmodus ausführen.

**Administration Console verwenden, um den abgesicherten Sicherungsmodus zu aktivieren**

1. Melden Sie sich bei der Administration-Console an.
1. Klicken Sie auf Einstellungen > Core-Systemeinstellungen > Backup-Dienstprogramme.
1. Wählen Sie &quot;Im abgesicherten Sicherungsmodus arbeiten&quot;und klicken Sie auf &quot;OK&quot;.

   Bei dieser Methode werden AEM Formulare unbegrenzt in den Sicherungsmodus versetzt (kein Timeout), und es wird der Snapshot-Modus anstatt des kontinuierlichen Sicherungsmodus ausgeführt.

**Befehlszeilenoption verwenden, um in den abgesicherten Sicherungsmodus zu wechseln**

Sie können die `LCBackupMode`-Skripte verwenden, um AEM Forms über die Befehlszeilenschnittstelle in den abgesicherten Sicherungsmodus zu versetzen.

1. Legen Sie „ADOBE_LIVECYCLE“ fest und starten Sie den Anwendungsserver.
1. Zum Ordner `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` wechseln.
1. Bearbeiten Sie je nach Betriebssystem das Skript `LCBackupMode.cmd` oder `LCBackupMode.sh`, um für Ihr System geeignete Standardwerte anzugeben.
1. Führen Sie an der Befehlszeile den folgenden Befehl in einer einzelnen Zeile aus:

   * (Windows) `LCBackupMode.cmd enter [-Host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `] [-label=`*Label-Name* `] [-timeout=`*Sekunden* `]`
   * (Linux, UNIX) `LCBackupMode.sh enter [-host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `] [-label=`*Label-Name* `]`

   Die Parameter in den vorherigen Befehlen sind wie folgt definiert:

   `Host` ist der Name des Hosts, auf dem AEM Forms ausgeführt wird.

   `port` ist der WebServices-Anschluss des Anwendungsservers, auf dem AEM Forms ausgeführt wird.

   `user` ist der Benutzername des AEM Forms-Administrators.

   `password` ist das Kennwort des AEM Forms-Administrators.

   `label` ist die Textbeschriftung dieser Sicherung (kann eine beliebige Zeichenfolge sein).

   `timeout` ist die Anzahl der Sekunden, nach denen der Backup-Modus automatisch beendet wird. Sie kann zwischen 0 und 10.080 liegen. Wenn der Wert 0 beträgt, was der Standardwert ist, wird der Sicherungsmodus nie unterbrochen.

   Weitere Informationen zur Befehlszeilenschnittstelle für den Sicherungsmodus finden Sie in der Datei &quot;Readme&quot;im Ordner &quot;BackupRestoreCommandline&quot;.

### Sicherungsmodi verlassen {#leaving-backup-modes}

Sie können entweder die Administration Console oder die Befehlszeilenoption verwenden, um den Sicherungsmodus zu deaktivieren.

**Den abgesicherten Sicherungsmodus deaktivieren (Snapshot-Modus)**

Führen Sie die folgenden Aufgaben aus, um mit Administration Console AEM Formulare aus dem abgesicherten Sicherungsmodus (Snapshot-Modus) zu entfernen.

1. Melden Sie sich bei der Administration-Console an.
1. Klicken Sie auf Einstellungen > Core-Systemeinstellungen > Backup-Dienstprogramme.
1. Deaktivieren Sie die Option &quot;Im abgesicherten Sicherungsmodus arbeiten&quot;und klicken Sie auf &quot;OK&quot;.

**Alle Sicherungsmodi beibehalten**

Sie können die Befehlszeilenschnittstelle verwenden, um den abgesicherten Sicherungsmodus (Snapshot-Modus) für AEM Forms zu deaktivieren bzw. die aktuelle Sicherungsmodussitzung (kontinuierlicher Modus) zu beenden. Beachten Sie, dass Sie Administration Console nicht verwenden können, um den kontinuierlichen Sicherungsmodus zu deaktivieren. Im kontinuierlichen Sicherungsmodus sind die Steuerelemente &quot;Backup Utilities&quot;in Administration Console deaktiviert. Sie müssen entweder den API-Aufruf oder den Befehl LCBackupMode verwenden.

1. Zum Ordner `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` wechseln.
1. Bearbeiten Sie je nach Betriebssystem das Skript `LCBackupMode.cmd` oder `LCBackupMode.sh`, um für Ihr System geeignete Standardwerte anzugeben.

   >[!NOTE]
   >
   >Sie müssen den Ordner JAVA_HOME wie im entsprechenden Kapitel für Ihren Anwendungsserver in [Vorbereiten der Installation AEM Formulare](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_de)*.*

1. Führen Sie den folgenden Befehl in einer einzelnen Zeile aus:

   * (Windows) `LCBackupMode.cmd leaveContinuousCoverage [-Host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `]`
   * (Linux, UNIX) `LCBackupMode.sh leaveContinuousCoverage [-Host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `]`

      Die Parameter in den vorherigen Befehlen sind wie folgt definiert:

      `Host` ist der Name des Hosts, auf dem AEM Forms ausgeführt wird.

      `port` ist der Anschluss, an dem AEM Forms auf dem Anwendungsserver ausgeführt wird.

      `user` ist der Benutzername des AEM Forms-Administrators.

      `password` ist das Kennwort des AEM Forms-Administrators.

      `leaveContinuousCoverage` Verwenden Sie diese Option, um den kontinuierlichen Sicherungsmodus vollständig zu deaktivieren.
   >[!NOTE]
   >
   >Solange der Sicherungsmodus deaktiviert ist, kann die kontinuierliche Abdeckung nicht wiederhergestellt werden. Alle Änderungen während dieser Zeit sind nicht geschützt.

   >[!NOTE]
   >
   >Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, sind der Snapshot-Sicherungsmodus und der kontinuierliche Sicherungsmodus nicht verfügbar.

   Weitere Informationen zur Befehlszeilenschnittstelle für den Sicherungsmodus finden Sie in der Datei &quot;readme&quot;im Ordner &quot;BackupRestoreCommandline&quot;.
