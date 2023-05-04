---
title: Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus
seo-title: Enabling and disabling safe backup mode
description: Auf der Seite "Sicherungseinstellungen"können Sie AEM Formulare im abgesicherten Sicherungsmodus ausführen, damit Sie die Datenbank und den Ordner des globalen Dokumentenspeichers (GDS) zuverlässig sichern können. Erfahren Sie, wie Sie den abgesicherten Sicherungsmodus aktivieren und deaktivieren.
seo-description: On the Backup Settings page, you can operate AEM forms in safe backup mode so that you can reliably back up your database and Global Document Storage (GDS) (GDS) directory. Learn how to enable and disable safe backup mode.
uuid: 2fdeaeaf-e969-40a4-8aee-1f2b627d3942
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fda71e4-78a1-4581-9d02-bf06a75c3bcb
exl-id: 309a8cef-e84d-485b-9a7c-786a93e83c85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 8%

---

# Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus {#enabling-and-disabling-safe-backup-mode}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Auf der Seite &quot;Sicherungseinstellungen&quot;können Sie AEM Formulare im abgesicherten Sicherungsmodus ausführen, damit Sie die Datenbank und den Ordner des globalen Dokumentenspeichers (GDS) zuverlässig sichern können.

Während AEM Formulare im abgesicherten Sicherungsmodus ausgeführt werden, funktioniert sie normal, mit der Ausnahme, dass sie keine Dateien aktiv aus dem Ordner des globalen Dokumentenspeichers entfernen.

>[!NOTE]
>
>Durch Festlegen dieser Option wird Ihr System nicht gesichert. Sie bereitet Ihr System auf die Sicherung vor.

## Aktivieren des abgesicherten Sicherungsmodus {#enable-safe-backup-mode}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Core-Systemeinstellungen&quot;> &quot;Sicherungseinstellungen&quot;.
1. Wählen Sie auf der Seite &quot;Sicherungseinstellungen&quot;die Option &quot;Im abgesicherten Sicherungsmodus arbeiten&quot;und klicken Sie auf &quot;OK&quot;.

>[!NOTE]
>
>Wenn das System bereits im abgesicherten Sicherungsmodus ausgeführt wird, wird keine neue Reservierung erstellt, wenn Sie auf OK klicken.

## Abgesicherten Sicherungsmodus deaktivieren {#disable-safe-backup-mode}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Core-Systemeinstellungen&quot;> &quot;Sicherungseinstellungen&quot;.
1. Deaktivieren Sie auf der Seite &quot;Sicherungseinstellungen&quot;die Option &quot;Im abgesicherten Sicherungsmodus arbeiten&quot;und klicken Sie auf &quot;OK&quot;.
