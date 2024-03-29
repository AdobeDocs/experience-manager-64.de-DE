---
title: Sicherungs- und Wiederherstellungsstrategie für AEM Forms
seo-title: Backup and recovery strategy for AEM forms
description: Erfahren Sie, wie Sie eine Strategie implementieren, um Daten zu sichern und sicherzustellen, dass diese mit den AEM Forms-daten verbleiben.
seo-description: Learn how to implement a strategy to back up data and ensuring that it remains in sync with the AEM forms data.
uuid: 98fc3115-76e5-4e58-aa30-3601866a441f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f192a8a3-1116-4d32-9b57-b53d532c0dbf
exl-id: ee5b0a82-5dd8-4ea6-885c-6154fd41ef4c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 21%

---

# Sicherungs- und Wiederherstellungsstrategie für AEM Forms{#backup-and-recovery-strategy-for-aem-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Ihre AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank speichert, sind Sie dafür verantwortlich, eine Strategie zur Sicherung dieser Daten zu implementieren und sicherzustellen, dass diese mit den AEM Formulardaten synchronisiert bleiben. Außerdem muss die Anwendung so konzipiert sein, dass sie robust genug ist, um ein Szenario zu handhaben, in dem die zusätzlichen Datenbanken nicht mehr synchronisiert werden. Es wird dringend empfohlen, alle Datenbankoperationen im Kontext einer Transaktion durchzuführen, um einen konsistenten Zustand zu gewährleisten.

Nachdem Sie erkannt haben, wie AEM Formulare verwendet werden, bestimmen Sie, welche Dateien wie oft gesichert werden müssen und welches Sicherungsfenster verfügbar sein soll.

>[!NOTE]
>
>Wie bei allen anderen Aspekten Ihrer AEM Forms-Implementierung muss Ihre Sicherungs- und Wiederherstellungsstrategie in einer Entwicklungs- oder Staging-Umgebung entwickelt und getestet werden, bevor sie in der Produktion verwendet wird, um sicherzustellen, dass die gesamte Lösung erwartungsgemäß und ohne Datenverlust funktioniert.

Adobe Experience Manager (AEM) ist ein integraler Bestandteil AEM Formulare. Daher müssen Sie AEM und AEM Formularsicherung sichern, da Correspondence Management Solution und Dienste wie Forms Manager auf Daten basieren, die im AEM Teil AEM Formulars gespeichert sind. Um Datenverlust zu vermeiden, müssen die spezifischen AEM formularspezifischen Daten so gesichert werden, dass GDS und AEM (Repository) mit Datenbankverweisen korrelieren. Datenbank, GDS, AEM und Stammordner für Inhalte müssen auf einem Computer mit demselben DNS wiederhergestellt werden. Name als Original.

## Sicherungsarten {#types-of-backups}

Die Sicherungsstrategie für AEM Formulare umfasst zwei Arten von Sicherungen:

**System-Image:** Ein vollständiges System-Backup, mit dem Sie den Inhalt Ihres Computers wiederherstellen können, wenn die Festplatte oder der gesamte Computer nicht mehr funktioniert. Eine Systemabbildsicherung ist nur vor der Bereitstellung von AEM Forms in der Produktionsumgebung erforderlich. Interne Unternehmensrichtlinien bestimmen dann, wie oft Systemabbildsicherungen erforderlich sind.

**AEM Forms-spezifische Daten:** Anwendungsdaten befinden sich in der Datenbank, in Global Document Storage (GDS) sowie dem AEM-Repository und müssen in Echtzeit gesichert werden. Der globale Dokumentenspeicher ist ein Ordner, in dem dauerhaft in einem Prozess verwendete Dateien gespeichert werden. Diese Dateien können PDF, Richtlinien oder Formularvorlagen enthalten.

>[!NOTE]
>
>Wenn Content Services (nicht mehr unterstützt) installiert ist, sichern Sie auch den Stammordner für Inhalte. Siehe [Stammordner für Inhalte (nur Content Services)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

Die Datenbank wird zum Speichern von Formularartefakten, Dienstkonfigurationen, Prozessstatus und Datenbankverweisen auf GDS-Dateien verwendet. Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, werden persistente Daten und Dokumente im globalen Dokumentenspeicher ebenfalls in der Datenbank gespeichert. Die Datenbank kann mithilfe der folgenden Methoden gesichert und wiederhergestellt werden:

* **Snapshot-Sicherungsmodus** gibt an, dass sich das AEM Forms-System entweder für unbegrenzte Zeit oder für eine angegebene Anzahl von Minuten im Sicherungsmodus befindet, nach deren Ablauf der Sicherungsmodus nicht mehr aktiv ist. Um den Snapshot-Sicherungsmodus zu starten oder zu beenden, können Sie eine der folgenden Optionen verwenden. Nach einem Wiederherstellungsszenario sollte der Snapshot-Sicherungsmodus nicht aktiviert werden.

   * Verwenden Sie die Seite &quot;Sicherungseinstellungen&quot;in Administration Console. Um in den Snapshot-Modus zu wechseln, aktivieren Sie das Kontrollkästchen Im abgesicherten Sicherungsmodus arbeiten . Deaktivieren Sie das Kontrollkästchen, um den Snapshot-Modus zu beenden.
   * Verwenden Sie das Skript LCBackupMode (siehe [Sichern Sie die Ordner &quot;Datenbank&quot;, &quot;Ordner des globalen Dokumentenspeichers&quot;und &quot;Stammordner für Inhalte&quot;.](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)). Zum Beenden des Snapshot-Sicherungsmodus legen Sie im Skriptargument den `continuousCoverage`-Parameter auf `false` fest oder verwenden Sie die Option `leaveContinuousCoverage`.
   * Verwenden Sie die bereitgestellte Backup-/Wiederherstellungs-API. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* **Datensicherung** -Modus zeigt an, dass sich das System immer im Sicherungsmodus befindet, wobei eine neue Sicherungsmodussitzung initiiert wird, sobald die vorherige Sitzung veröffentlicht wird. Mit dem kontinuierlichen Sicherungsmodus ist kein Timeout verbunden. Wenn das LCBackupMode-Skript oder die APIs aufgerufen werden, um den kontinuierlichen Sicherungsmodus zu beenden, beginnt eine neue kontinuierliche Sicherungsmodussitzung. Dieser Modus ist nützlich, um kontinuierliche Sicherungen zu unterstützen, aber dennoch das Bereinigen alter und nicht benötigter Dokumente aus dem Ordner des globalen Dokumentenspeichers zu ermöglichen. Der kontinuierliche Sicherungsmodus wird auf der Seite &quot;Sicherung und Wiederherstellung&quot;nicht unterstützt. Nach einem Wiederherstellungsszenario ist der kontinuierliche Sicherungsmodus weiterhin aktiviert. Sie können den kontinuierlichen Sicherungsmodus mithilfe des bereitgestellten LCBackupMode-Skripts mit der Option `leaveContinuousCoverage` deaktivieren.

>[!NOTE]
>
>Durch Beenden des kontinuierlichen Sicherungsmodus wird unmittelbar eine neue Sicherungsmodussitzung ausgelöst. Wenn Sie den kontinuierlichen Sicherungsmodus vollständig deaktivieren möchten, verwenden Sie die Option `leaveContinuousCoverage` im Skript. Damit wird die vorhandene Sicherungssitzung überschrieben. Im Snapshot-Sicherungsmodus können Sie den Sicherungsmodus wie gewohnt beenden.

Um Datenverlust zu vermeiden, müssen die AEM formularspezifischen Daten so gesichert werden, dass die Dokumente für den Ordner des globalen Dokumentenspeichers und den Stammordner für Inhalte mit den Datenbankverweisen korrelieren.

>[!NOTE]
>
>Wenn der globale Dokumentenspeicher im Dateisystem und nicht in der Datenbank gespeichert ist, führen Sie die Datenbanksicherung vor der Sicherung des globalen Dokumentenspeichers durch.

## Besondere Hinweise für Sicherung und Wiederherstellung {#special-considerations-for-backup-and-recovery}

Verwenden Sie die folgenden Richtlinien, wenn Sie AEM Formulare aufgrund der folgenden Änderungen in einer anderen Umgebung wiederherstellen müssen:

* Änderung der IP-Adresse, des Hostnamens oder Ports des AEM forms-Servers
* Änderung der Laufwerksbuchstaben oder des Ordnerpfads
* Änderung an einem anderen Datenbankhost, Port oder Namen

In der Regel werden solche Wiederherstellungsszenarien durch Hardwarefehler des Servers verursacht, der als Host für den Anwendungsserver, Datenbankserver oder Formularserver dient. Zusätzlich zu den AEM formularspezifischen Konfigurationen, die in diesem Abschnitt beschrieben werden, sollten Sie auch die erforderlichen Änderungen für andere Teile der AEM Forms-Bereitstellung vornehmen, z. B. Lastenausgleich und Firewalls, wenn sich der Hostname oder die IP-Adresse eines AEM forms-Servers ändert.

### Was nicht geändert werden kann {#what-cannot-be-changed}

Auch wenn Sie den Datenbankserver und viele andere Parameter ändern können, können Sie den Typ des Anwendungsservers oder den Datenbanktyp nicht ändern, wenn Sie AEM Formulare aus einer Sicherung wiederherstellen. Wenn Sie beispielsweise eine AEM Forms-Sicherung wiederherstellen, können Sie den Anwendungsserver nicht von JBoss in WebLogic oder die Datenbank von Oracle in DB2 ändern. Darüber hinaus müssen wiederhergestellte AEM Formulare dieselben Dateisystempfade wie der Schriftartenordner verwenden.

### Neustart nach einer Wiederherstellung {#restarting-after-a-recovery}

Bevor Sie den Formularserver nach einer Wiederherstellung neu starten, gehen Sie wie folgt vor:

1. Starten Sie das System im Wartungsmodus.
1. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass Form Manager mit AEM Formularen im Wartungsmodus synchronisiert wird:

   1. Gehen Sie zu https://&lt;*server*>:&lt;*port*>/lc/fm und melden Sie sich mit Ihren Administrator-/Passwort-Anmeldeinformationen an.
   1. Klicken Sie oben rechts auf den Namen des Benutzers (in diesem Fall &quot;Super Administrator&quot;).
   1. Klicken **Admin-Optionen**.
   1. Klicken **Starten** , um Assets aus dem Repository zu synchronisieren.

1. In einer Cluster-Umgebung sollte der primäre Knoten (in Bezug auf AEM) vor den sekundären Knoten in Betrieb sein.
1. Stellen Sie sicher, dass keine Prozesse von internen oder externen Quellen wie den Web-, SOAP- oder EJB-Prozessinitiatoren initiiert werden, bis der normale Betrieb des Systems validiert ist.

Wenn die AEM Forms-Hauptdatenbank verschoben oder geändert wird, lesen Sie die Installationshandbücher für Ihren Anwendungsserver, um Informationen zum Aktualisieren der Informationen zur Datenbankverbindung für die AEM Datenquellen IDP_DS und EDC_DS zu erhalten.

### Hostname oder IP-Adresse des AEM forms ändern {#changing-the-aem-forms-hostname-or-ip-address}

Wenn Sie in einem Cluster TCP-Zwischenspeicherung anstelle von UDP verwenden, müssen Sie die Cache-Locator-Konfiguration aktualisieren. Siehe &quot;Zwischenspeicherungs-Locators konfigurieren (nur Zwischenspeicherung mit TCP)&quot;im Konfigurationshandbuch, das für Ihren Anwendungsserver relevant ist.

### Dateisystempfade für AEM Forms-Knoten ändern {#changing-the-aem-forms-node-file-system-paths}

Wenn Sie die Dateisystempfade für einen eigenständigen Knoten ändern, müssen Sie die entsprechenden Verweise in Voreinstellungen, anderen Systemkonfigurationen, benutzerdefinierten Anwendungen und bereitgestellten AEM Forms-Anwendungen aktualisieren. Andererseits müssen bei einem Cluster alle Knoten dieselbe Dateisystempfad-Konfiguration verwenden. Sie müssen den Stammordner des globalen Dokumentenspeichers (GDS) festlegen und sicherstellen, dass er auf eine Kopie des wiederhergestellten GDS verweist, die mit der wiederhergestellten Datenbank synchronisiert ist. Das Festlegen des GDS-Pfades ist wichtig, da der GDS Daten enthalten kann, die bei jedem Neustart des Anwendungsservers beibehalten werden sollen.

In einer Clusterumgebung sollte die Dateisystempfad-Konfiguration des Repositorys für alle Clusterknoten vor der Sicherung und nach der Wiederherstellung gleich sein.

Verwenden Sie das `LCSetGDS`-Skript im Ordner `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline`, um den GDS-Pfad festzulegen, nachdem Sie die Datei-System-Pfade geändert haben. Einzelheiten finden Sie in der `ReadMe.txt`-Datei im selben Ordner. Wenn der alte GDS-Ordnerpfad nicht verwendet werden kann, muss das `LCSetGDS`-Skript verwendet werden, um den neuen Pfad für den GDS festzulegen, bevor Sie AEM Forms starten.

>[!NOTE]
>
>Dies ist der einzige Umstand, unter dem Sie dieses Skript verwenden sollten, um den Speicherort des globalen Dokumentenspeichers zu ändern. Um den Speicherorts für den Ordner des globalen Dokumentenspeichers zu ändern, während AEM Forms ausgeführt wird, verwenden Sie Administration Console. (Siehe [Allgemeine AEM Forms-Einstellungen konfigurieren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)*.) *

Nachdem Sie den GDS-Pfad festgelegt haben, starten Sie den Formularserver im Wartungsmodus und verwenden Sie Administration Console, um die verbleibenden Dateisystempfade für den neuen Knoten zu aktualisieren. Nachdem Sie überprüft haben, ob alle erforderlichen Konfigurationen aktualisiert wurden, starten Sie AEM Formulare neu und testen Sie sie.
