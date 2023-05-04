---
title: "IBM DB2-Datenbank: Befehle zur regelmäßigen Wartung ausführen"
seo-title: "IBM DB2 database: Running commands for regular maintenance"
description: Das Dokument listet IBM DB2-Befehle auf, die für die regelmäßige Wartung Ihrer AEM Forms-Datenbank empfohlen werden.
seo-description: This document lists IBM DB2 commands that are recommended for regular maintenance of your AEM forms database.
uuid: 235d59df-b9b9-4770-8b7d-00713701c3c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a62b68b4-7735-49b1-8938-f0d9e4c4a051
exl-id: b4877c24-3450-44b6-adcd-78a694b28857
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 63%

---

# IBM DB2-Datenbank: Ausführen von Befehlen zur regelmäßigen Wartung {#ibm-db-database-running-commands-for-regular-maintenance}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die folgenden IBM DB2-Befehle werden für die regelmäßige Wartung Ihrer AEM Forms-Datenbank empfohlen. Detaillierte Informationen zur Wartung und Leistungsoptimierung Ihrer DB2-Datenbank finden Sie unter *IBM DB2-Administrationshandbuch*.

* **runstats:** Dieser Befehl aktualisiert Statistiken, die die physischen Merkmale einer Datenbanktabelle sowie der dazugehörigen Indizes beschreiben. Von AEM Forms generierte dynamische SQL-Anweisungen verwenden automatisch diese aktualisierten Statistiken. Für statische SQL-Anweisungen, die innerhalb einer Datenbank erstellt wurden, muss jedoch auch der Befehl `db2rbind` ausgeführt werden.
* **db2rbind**: Dieser Befehl bindet alle Pakete in der Datenbank erneut. Rufen Sie diesen Befehl nach Ausführung des Dienstprogramms `runstats` aus, um alle Pakete in der Datenbank erneut zu überprüfen.
* **reorg table oder index**: Dieser Befehl überprüft, ob eine Reorganisation von Tabellen oder Indizes erforderlich ist.

   Da Ihre Datenbanken wachsen und sich ändern, ist die Neuberechnung von Tabellenstatistiken entscheidend für die Verbesserung der Datenbankleistung und sollte regelmäßig erfolgen. Diese Befehle können entweder manuell mithilfe von Skripten oder mithilfe eines Cron-Auftrags ausgeführt werden.

>[!NOTE]
>
>Vor Ausführung des Befehls `runstats` ist es erforderlich, dass die Datenbank Daten enthält und mindestens eine Synchronisierung erfolgt ist.

Bei einer kleinen Datenbank (z. B. 10000 Benutzer oder 2500 Gruppen) reicht es aus, den Befehl `runstats` aufzurufen, um die für Synchronisierungen erforderliche Zeit zu reduzieren.

Führen Sie bei größeren Datenbanken (z. B. 100000 Benutzer oder 10000 Gruppen) den Befehl `reorg` aus, bevor Sie den Befehl `runstats` ausführen.

## Befehl „runstats“ auf die AEM Forms-Datenbank anwenden {#use-the-runstats-command-on-your-aem-forms-database}

Führen Sie den Befehl `runstats` für die folgenden AEM Forms-Datenbanktabellen und -indizes aus.

>[!NOTE]
>
>Der Befehl `runstats` muss nur während der ersten Datenbanksynchronisation ausgeführt werden. Er muss jedoch während dieses Prozesses zweimal ausgeführt werden: einmal während der Synchronisierung von Benutzern und Gruppen und dann während der Synchronisierung von Gruppenmitgliedern. Stellen Sie sicher, dass das Skript bei jeder Ausführung vollständig ausgeführt wird.

Die ordnungsgemäße Syntax und Verwendung wird in der Dokumentation des Datenbankherstellers beschrieben. Im Folgenden wird `<schema>` verwendet, um das Schema zu bezeichnen, das Ihrem DB2-Benutzernamen zugeordnet ist. Wenn Sie eine einfache DB2-Standardinstallation haben, ist dies der Datenbankschemaname.

```as3
     TABLE <schema>.EDCPRINCIPALGROUPENTITY 
  
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY 
  
     TABLE <schema>.EDCPRINCIPALENTITY 
  
     TABLE <schema>.EDCPRINCIPALUSERENTITY 
  
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY 
  
     TABLE <schema>.EDCPRINCIPALENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALUSERENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALGROUPENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY FOR INDEXES ALL
```

## Führen Sie den Befehl reorg auf Ihrer AEM-Formulardatenbank aus {#run-the-reorg-command-on-your-aem-forms-database}

Führen Sie den Befehl `reorg` für die folgenden AEM Forms-Datenbanktabellen und -indizes aus. Die ordnungsgemäße Syntax und Verwendung wird in der Dokumentation des Datenbankherstellers beschrieben.

```as3
     TABLE <schema>.EDCPRINCIPALGROUPENTITY 
  
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY 
  
     TABLE <schema>.EDCPRINCIPALENTITY 
  
     TABLE <schema>.EDCPRINCIPALUSERENTITY 
  
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALUSERENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGROUPENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY
```
