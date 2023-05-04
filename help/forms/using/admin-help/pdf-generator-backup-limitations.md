---
title: Einschränkungen bei der Sicherung von PDF Generator
seo-title: PDF Generator backup limitations
description: Erfahren Sie mehr über die Backup-Einschränkungen von PDF Generator.
seo-description: Learn about PDF Generator backup limitations.
uuid: 9537ffde-4396-46d1-81ea-edcd25923ffb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 23386353-b2bf-49f1-947a-dd7587bba175
noindex: true
exl-id: d2ba9881-02b6-470b-b110-7d4609e6ab24
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 17%

---

# Einschränkungen bei der Sicherung von PDF Generator {#pdf-generator-backup-limitations}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der temporäre Ordner, den PDF Generator zum Konvertieren von Dateien verwendet, kann nicht gesichert werden. Obwohl der Dienst ordnungsgemäß wiederhergestellt wird, können Daten verloren gehen, da PDF Generator den Inhalt des temporären Ordners in festgelegten Zeitabständen überprüft und löscht.
