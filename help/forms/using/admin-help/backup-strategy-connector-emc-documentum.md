---
title: Sicherungsstrategie für Connector für EMC Documentum-Benutzer
seo-title: Backup strategy for Connector for EMC Documentum users
description: Erfahren Sie, wie Sie eine Sicherungsstrategie für EMC Documentum-Benutzer erstellen.
seo-description: Check how to create a backup strategy for Connector for EMC Documentum users.
uuid: 5d8a0476-5231-4e1d-96c4-ae3df68e09f0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e83b1a59-a730-4d22-9d58-1c9c38e5d534
exl-id: 933c3903-2040-41f4-b803-4d672ce9a2dc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 19%

---

# Sicherungsstrategie für Connector für EMC Documentum-Benutzer {#backup-strategy-for-connector-for-emc-documentum-users}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Connector für EMC Documentum installiert ist, muss Ihre Sicherungs- und Wiederherstellungsstrategie zusätzlich zu den Anweisungen in diesem Kapitel eine Sicherung (oder Wiederherstellung) des Computers umfassen, auf dem das entsprechende ECM-System installiert ist. (Siehe die Dokumentation zu ECM Documentum ).

Sichern Sie Ihre AEM Forms-Umgebung mithilfe des ECM-Repositorys und führen Sie die folgenden Aufgaben aus:

* Sichern Sie AEM Formulare gemäß den Anweisungen in diesem Dokument.
* Sichern Sie Ihr ECM Documentum-System, indem Sie die Anweisungen unter [EMC Documentum Content Server sichern](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#back-up-the-emc-documentum-content-server).

Führen Sie die folgenden Schritte aus, um die AEM Forms-Umgebung mithilfe des ECM-Repositorys wiederherzustellen:

* Stellen Sie das entsprechende ECM-System gemäß den Anweisungen unter [EMC Documentum Content Server wiederherstellen](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#restore-the-emc-documentum-content-server).
* Stellen Sie AEM Formulare anhand der in diesem Dokument beschriebenen Anweisungen wieder her.
