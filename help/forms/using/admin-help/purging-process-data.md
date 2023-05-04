---
title: Bereinigen von Prozessdaten
seo-title: Purging process data
description: Prozessdaten, die beim Aufrufen eines langlebigen Prozesses generiert werden, können zu groß werden, was zu einer geringeren AEM der Formularleistung und zur Verwendung unnötigen Festplattenspeichers führt. Erfahren Sie, wie Sie Prozessdaten bereinigen können.
seo-description: Process data that is generated when a long-lived process is invoked can become too large, resulting in lower AEM forms performance and the use of unnecessary disk space. See how you can purge process data.
uuid: 2f04452c-71c6-452c-88c2-7560d35e7dec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3157bb92-4b07-40f2-be4c-8f5807f9a380
exl-id: ecedde63-abbb-4e69-901e-1e4b7a59f539
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 16%

---

# Bereinigen von Prozessdaten {#purging-process-data}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Prozessdaten, die beim Aufrufen eines langlebigen Prozesses generiert werden, können zu groß werden, was zu einer geringeren AEM der Formularleistung und zur Verwendung unnötigen Festplattenspeichers führt. Es empfiehlt sich, Prozessdaten zu löschen, wenn Datensätze nicht mehr benötigt werden. AEM Formulare bieten mehrere Möglichkeiten, Prozessdaten zu bereinigen:

* Sie können Administration Console verwenden, um eine einmalige Bereinigung veralteter Datensätze im Zusammenhang mit langlebigen Prozessen durchzuführen oder regelmäßige automatische Bereinigungen zu planen. (Siehe [Job Manager-Datenbank um Datensätze bereinigen](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).
* Sie können die Java-API und Webdienst-API von AEM Forms verwenden, um Prozessdaten im Zusammenhang mit langlebigen Prozessen programmgesteuert zu bereinigen. (Siehe &quot;Bereinigen von Prozessdaten&quot;in [Programmieren mit AEM Formularen](https://www.adobe.com/go/learn_aemforms_programming_63_de).
* Verwenden Sie das Tool zur Prozessbereinigung, um Prozesse basierend auf dem Prozessnamen und anderen Parametern zu bereinigen. Weitere Informationen finden Sie in der Datei „Bitte lesen“ zur Prozessbereinigung, die sich unter „*[aem_forms-Stammordner]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt“ befindet.
