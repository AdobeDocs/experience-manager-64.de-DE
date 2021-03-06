---
title: Übersicht der Statusüberwachung
seo-title: Overview of Health Monitor
description: Dieses Dokument bietet einen Überblick über den Health Monitor und Details darüber, wie Sie darauf zugreifen können.
seo-description: This document provides the overview of the Health monitor, and details about how you can access it.
uuid: 5934fd2d-80a5-4c6d-b3ee-882c2865705b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c303e967-944d-40b0-96ca-f91e2f42a0d0
exl-id: 70ccc0ae-04c6-4af9-9150-72d0d71c945f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 100%

---

# Übersicht der Statusüberwachung {#overview-of-health-monitor}

Health Monitor stellt wichtige Information zum AEM Forms-System, z. B. Serverinformationen, Speicherbelegung und Prozessorauslastung, bereit. Außerdem werden Work Manager-Statistiken, z. B. die Anzahl der Arbeitselemente oder Aufträge in der Warteschlange und ihr jeweiliger Status, bereitgestellt. Sie können die folgenden Aufgaben mithilfe von Health Monitor ausführen:

* Sicherstellen, dass Ihr System ordnungsgemäß ausgeführt wird.
* Anzeigen von Informationen, um Systemprobleme bei ihrem Auftreten sofort festzustellen
* Vorgänge an Arbeitselementen oder Aufträgen durchführen, die Probleme aufweisen
* Job Manager-Datenbank um veraltete Datensätze bereinigen

Die Seite „Health Monitor“ in Administration Console verfügt über drei Registerkarten:

* Auf der Registerkarte „System“ werden Diagramme zur Ressourcenüberwachung und Informationen zum Formularserver (oder Knoten in einer Clusterumgebung) angezeigt. (Siehe [Systeminformationen anzeigen](/help/forms/using/admin-help/view-system-information.md#view-system-information).)
* Auf der Registerkarte „Work Manager“ werden Daten mit Bezug auf Work Manager, z. B. die Anzahl der Arbeitselemente in der Warteschlange von Work Manager, angezeigt. Sie können die Informationen mithilfe von verschiedenen Kriterien filtern oder einzelne Arbeitselemente mithilfe der Vorgangstools verwalten. (Siehe [Statistiken mit Bezug auf Work Manager anzeigen](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).)
* Mithilfe der Registerkarte „Zeitplaner für die Auftragsbereinigung“ können Sie die Job Manager-Datenbank um veraltete Aufzeichnungen bereinigen. (Siehe [Job Manager-Datenbank um Aufzeichnungen bereinigen](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)

Die Health Monitor-Webseite wird mit Statistiken, die mithilfe einer Gemfire-API gesammelt werden, aufgefüllt. Diese API erkennt automatisch alle Knoten in einem Cluster. Sie löst auch Sicherheitsprobleme, die auftreten, wenn Statistiken von Proxyservern oder einem Lastenausgleich gesammelt werden. Es stehen Java-Optionen zum Optimieren von Health Monitor zur Verfügung, mit deren Hilfe Sie die Auswirkungen auf die Leistung der AEM Forms-Umgebung reduzieren können. (Siehe [Leistung von Health Monitor optimieren](/help/forms/using/admin-help/fine-tuning-health-monitor-performance.md#fine-tuning-health-monitor-performance).)

**Auf die Zustandsüberwachung zugreifen**

1. Klicken Sie in Administration Console in der rechten oberen Ecke der Seite auf „Health Monitor“.
