---
title: Auditprotokollwartung in AEM 6
seo-title: Audit Log Maintenance in AEM 6
description: Erfahren Sie mehr über die Auditprotokollwartung in AEM.
feature: Operations
seo-description: Lear about Audit Log Maintenance in AEM.
uuid: 212de4df-6bf4-434c-94e1-74186d21945a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 565d89de-b3ca-41a5-8e1c-d10905c25fb5
exl-id: bcbdab55-4871-4c7f-b82a-b7d8280e82e3
source-git-commit: 40a4e01eea3e20fda6d0b2c8af985f905039e320
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 81%

---

# Auditprotokollwartung in AEM 6{#audit-log-maintenance-in-aem}

AEM-Ereignisse, die sich für die Auditprotokollierung qualifizieren, generieren eine große Menge archivierter Daten. Diese Datenmenge kann im Laufe der Zeit aufgrund von Replikationen, Asset-Uploads und anderen Systemaktivitäten schnell anwachsen.

Die Auditprotokollwartung beinhaltet mehrere Funktionsbestandteile, die die Auditprotokollwartung gemäß spezifischen Richtlinien automatisieren können.

Sie werden als konfigurierbare wöchentliche Wartungsaufgabe implementiert und sind über die Überwachungskonsole des Vorgangs-Dashboard verfügbar.

Weitere Informationen finden Sie in der [Dokumentation zum Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

Es gibt drei Arten von Optionen zur Auditprotokolllöschung:

1. [Seiten-Auditprotokolllöschung](/help/sites-administering/operations-audit-log.md#configure-page-audit-log-purging)
1. [DAM-Auditprotokolllöschung](/help/sites-administering/operations-audit-log.md#configure-dam-audit-log-purging)
1. [Replizierungs-Auditprotokolllöschung](/help/sites-administering/operations-audit-log.md#configure-replication-audit-log-purging)

Jede der Optionen kann durch Erstellen von Regeln in der Web-Konsole von AEM konfiguriert werden. Nachdem sie konfiguriert wurden, können Sie sie auslösen, indem Sie zu **Tools > Vorgänge > Wartung > Wöchentliches Wartungsfenster** wechseln und die **AuditLog-Wartungsaufgabe** ausführen.

## Konfigurieren der Seiten-Auditprotokolllöschung {#configure-page-audit-log-purging}

Führen Sie zum Konfigurieren der Auditprotokolllöschung die folgenden Schritte aus:

1. Navigieren Sie zum Admin der Web-Konsole, indem Sie Ihren Browser auf `http://localhost:4502/system/console/configMgr/`

1. Suchen Sie nach einem Element mit dem Namen **Seitenaudit Protokollbereinigungsregel** und klicken Sie darauf.

   ![chlimage_1-365](assets/chlimage_1-365.png)

1. Konfigurieren Sie als Nächstes den Löschungsplaner gemäß Ihren Anforderungen. Die verfügbaren Optionen sind:

   * **Rule name:** der Name der Auditrichtlinienregel
   * **Content path:** der Inhalts-Pfad, auf den die Regel angewandt wird;
   * **Minimum age:** die Zeit in Tagen, für die die Auditprotokolle aufbewahrt werden müssen
   * **Audit log type:** der Typ des zu löschenden Auditprotokolls

   >[!NOTE]
   >
   >Der Inhaltspfad gilt nur für untergeordnete Elemente der `/var/audit/com.day.cq.wcm.core.page` Knoten im Repository.

1. Speichern Sie die Regel.
1. Die gerade von Ihnen erstellte Regel muss im Vorgangs-Dashboard vorhanden sein, um ausgeführt werden zu können. Gehen Sie hierzu über den AEM-Begrüßungsbildschirm zu **Tools > Vorgänge > Wartung**.

1. Klicken Sie auf die Karte **Wöchentliches Wartungsfenster**.

1. Sie finden die Wartungsaufgabe, die bereits im **AuditLog-Wartungsaufgabe** Karte.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Sie können entweder das Datum der nächsten Ausführung ermitteln, es konfigurieren oder es durch das Drücken der Wiedergabetaste manuell ausführen.

Wenn in AEM 6.3 das geplante Wartungsfenster geschlossen wird, bevor die Aufgabe &quot;Auditprotokoll-Bereinigung&quot;abgeschlossen werden kann, wird die Aufgabe automatisch beendet. Sie wird fortgesetzt, wenn das nächste Wartungsfenster beginnt.

**Mit AEM 6.4** können Sie eine ausgeführte Auditprotokoll-Bereinigungsaufgabe manuell anhalten, indem Sie auf die **Anhalten** Symbol. Bei der nächsten Ausführung wird die Aufgabe auf sichere Art und Weise wiederaufgenommen.

>[!NOTE]
>
>Das Anhalten der Wartungsaufgabe bedeutet, dass ihre Ausführung verschoben wird, ohne den Überblick über den aktuell bereits ausgeführten Auftrag zu verlieren.

## Konfigurieren der DAM-Auditprotokolllöschung {#configure-dam-audit-log-purging}

1. Navigieren Sie zur Systemkonsole unter *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Suchen Sie nach **DAM audit Log Purge rule** und klicken Sie auf das Ergebnis.
1. Konfigurieren Sie im nächsten Fenster Ihre Regel entsprechend: Die Optionen sind:

   * **Rule name:** der Name der Auditrichtlinienregel
   * **Content path:** der Inhalts-Pfad, auf den die Regel angewandt wird
   * **Minimum age:** die Zeit in Tagen, für die die Auditprotokolle aufbewahrt werden müssen
   * **Audit Log Dam event types:** der Typ der zu löschenden DAM-Prüfereignisse

1. Klicken Sie auf **Speichern**, um Ihre Konfiguration zu speichern.

## Konfigurieren der Replizierungs-Auditprotokolllöschung  {#configure-replication-audit-log-purging}

1. Navigieren Sie zur Systemkonsole unter *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Suchen Sie nach **Replication audit Log Purge Scheduler** und klicken Sie auf das Ergebnis.
1. Konfigurieren Sie im nächsten Fenster Ihre Regel entsprechend: Die Optionen sind:

   * **Rule name:** der Name der Auditrichtlinienregel
   * **Content path:** der Inhalts-Pfad, auf den die Regel angewandt wird
   * **Minimum age:** die Zeit in Tagen, für die die Auditprotokolle aufbewahrt werden müssen
   * **Audit log Replication event types:** der Typ der zu löschenden Replikationsprüfereignisse

1. Klicken Sie auf **Speichern**, um Ihre Konfiguration zu speichern.
