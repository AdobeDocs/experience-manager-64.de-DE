---
title: Übersicht der Statusüberwachung
seo-title: Overview of Health Monitor
description: Dieses Dokument bietet einen Überblick über den Health Monitor und Details dazu, wie Sie darauf zugreifen können.
seo-description: This document provides the overview of the Health monitor, and details about how you can access it.
uuid: 5934fd2d-80a5-4c6d-b3ee-882c2865705b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c303e967-944d-40b0-96ca-f91e2f42a0d0
exl-id: 70ccc0ae-04c6-4af9-9150-72d0d71c945f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---

# Übersicht der Statusüberwachung {#overview-of-health-monitor}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Health Monitor stellt wichtige Informationen zum AEM Forms-System bereit, z. B. Serverinformationen, Speicherbelegung und Prozessorauslastung. Außerdem stehen Work Manager-Statistiken zur Verfügung, z. B. die Anzahl der Arbeitselemente oder Aufträge in der Warteschlange und deren Status. Sie können die folgenden Aufgaben mit Health Monitor ausführen:

* Überprüfen Sie, ob das System ordnungsgemäß ausgeführt wird.
* Anzeigen von Informationen zur Diagnose von Systemproblemen bei deren Auftreten
* Ausführen von Vorgängen für Arbeitselemente oder Aufträge mit Problemen
* Bereinigen veralteter Datensätze aus der Job Manager-Datenbank

Die Seite &quot;Health Monitor&quot;in Administration Console verfügt über drei Registerkarten:

* Auf der Registerkarte System werden Diagramme zur Ressourcenüberwachung und Informationen zum Formularserver (oder Knoten in einer Clusterumgebung) angezeigt. (Siehe [Systeminformationen anzeigen](/help/forms/using/admin-help/view-system-information.md#view-system-information).
* Auf der Registerkarte &quot;Work Manager&quot;werden Daten angezeigt, die mit Work Manager in Verbindung stehen, z. B. die Anzahl der Arbeitselemente in der Warteschlange von Work Manager. Sie können die Informationen anhand verschiedener Kriterien filtern oder einzelne Arbeitselemente mithilfe der Vorgangstools verwalten. (Siehe [Anzeigen von Statistiken im Zusammenhang mit Work Manager](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).
* Auf der Registerkarte &quot;Zeitplaner für die Auftragsbereinigung&quot;können Sie veraltete Datensätze aus der Job Manager-Datenbank bereinigen. (Siehe [Job Manager-Datenbank um Datensätze bereinigen](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).

Die Webseite &quot;Health Monitor&quot;enthält Statistiken, die über eine Gemfire-API erfasst wurden. Diese API erkennt automatisch alle Knoten in einem Cluster. Außerdem werden Sicherheitsprobleme behoben, die auftreten, wenn Statistiken von Proxyservern oder Lastenausgleichern erfasst werden. Es stehen Java-Optionen zum Optimieren von Health Monitor zur Verfügung, mit deren Hilfe Sie die Auswirkungen auf die Leistung der AEM Forms-Umgebung reduzieren können. (Siehe [Optimieren der Leistung von Health Monitor](/help/forms/using/admin-help/fine-tuning-health-monitor-performance.md#fine-tuning-health-monitor-performance).

**Auf Health Monitor zugreifen**

1. Klicken Sie in Administration Console oben rechts auf der Seite auf Health Monitor .
