---
title: Prozessdaten bereinigen
seo-title: Purging process data
description: Prozessdaten, die beim Aufrufen eines Prozesses mit langer Lebensdauer generiert werden, können zu stark anwachsen, was zu einer Beeinträchtigung der Leistung von AEM Forms und zur Belegung von unnötigem Speicherplatz führt. Erfahren Sie, wie Sie Prozessdaten bereinigen können.
seo-description: Process data that is generated when a long-lived process is invoked can become too large, resulting in lower AEM forms performance and the use of unnecessary disk space. See how you can purge process data.
uuid: 2f04452c-71c6-452c-88c2-7560d35e7dec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3157bb92-4b07-40f2-be4c-8f5807f9a380
exl-id: ecedde63-abbb-4e69-901e-1e4b7a59f539
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 100%

---

# Prozessdaten bereinigen {#purging-process-data}

Prozessdaten, die beim Aufrufen eines Prozesses mit langer Lebensdauer generiert werden, können zu stark anwachsen, was zu einer Beeinträchtigung der Leistung von AEM Forms und zur Belegung von unnötigem Speicherplatz führt. Es empfiehlt sich, Prozessdaten zu bereinigen, wenn die Aufzeichnungen nicht mehr gebraucht werden. AEM Forms bietet mehrere Möglichkeiten, Prozessdaten zu bereinigen:

* Sie können Administration Console verwenden, um eine einmalige Bereinigung von veralteten Datensätzen im Zusammenhang mit dauerhaft genutzten Prozessen auszuführen oder regelmäßige automatische Bereinigungen zu planen. (Siehe [Job Manager-Datenbank um Aufzeichnungen bereinigen](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)
* Sie können die AEM Forms Java-API und die Webdienst-API verwenden, um Prozessdaten im Zusammenhang mit dauerhaft genutzten Prozessen programmgesteuert zu bereinigen. (Siehe „Bereinigen von Prozessdaten“ in [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).)
* Verwenden Sie das Prozessbereinigungswerkzeug zum Bereinigen von Prozessen anhand des Prozessnamens und anderer Parameter. Weitere Informationen finden Sie in der Datei „Bitte lesen“ zur Prozessbereinigung, die sich unter „*[aem_forms-Stammordner]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt“ befindet.
