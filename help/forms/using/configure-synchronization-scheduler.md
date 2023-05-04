---
title: Konfigurieren der Synchronisierungsplanung
seo-title: Configuring the synchronization scheduler
description: Erfahren Sie, wie Sie Assets migrieren und synchronisieren, den Synchronisierungs-Scheduler konfigurieren und Ordner zum Anordnen von Assets verwenden.
seo-description: Learn how to migrate and sync assets, configure sync scheduler, and use folders to arrange assets.
uuid: a6445b45-9c1c-4483-a32e-453648c488c5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 2c8cea3c-8d8b-41d4-8ef9-a0ada8f86be6
role: Admin
exl-id: 7f1c4bac-accf-43e4-9439-89c5420d50f2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 54%

---

# Konfigurieren der Synchronisierungsplanung {#configuring-the-synchronization-scheduler}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Standardmäßig wird der Synchronisierungs-Scheduler alle 3 Minuten ausgeführt, um alle im Repository geänderten und aktualisierten Assets über LiveCycle Workbench 11 zu synchronisieren. Anwendungen, die Formulare und Ressourcen enthalten, sind in der AEM Forms-Benutzeroberfläche sichtbar, sobald der Synchronisierungsprozess abgeschlossen ist.

## Ändern des Intervalls für den Synchronisierungs-Scheduler {#change-interval-of-the-synchronization-scheduler}

Führen Sie die folgenden Schritte aus, um das Intervall des Synchronisierungs-Scheduler zu ändern:

1. Melden Sie sich bei AEM Configuration Manager an. Die URL des Configuration Managers lautet `https://[Server]:[Port]/lc/system/console/configMgr`

1. Suchen Sie das Bundle **FormsManagerConfiguration** und öffnen Sie es.

1. Geben Sie für die Option **Häufigkeit für Synchronisierungs-Scheduler** einen neuen Wert an.

   Die Einheit für die Frequenz ist Minuten. Wenn Sie beispielsweise die Planung so konfigurieren möchten, dass sie alle 60 Minuten ausgeführt wird, geben Sie &quot;60&quot;an.

## Synchronisieren von Assets {#synchronizing-assets}

Sie können die Option **Assets aus Repository synchronisieren** verwenden, um die Elemente manuell zu synchronisieren. Führen Sie die folgenden Schritte aus, um die Assets manuell zu synchronisieren:

1. Melden Sie sich bei AEM Forms an. Die Standardeinstellung ist `https://[Server]:[Port]/lc/aem/forms/`.

   ![AEM Forms-Benutzeroberfläche](assets/aem_forms_ui.png)

   **Abbildung:** *Benutzeroberfläche von AEM Forms*

1. Klicken Sie auf das Symbol ![aem6forms_sync](assets/aem6forms_sync.png) in der Symbolleiste. Wenn im zuletzt konfigurierten Pfad keine Elemente vorhanden sind, wird das nachfolgende Dialogfeld angezeigt. Klicken Sie auf **Start**, um die Synchronisierung zu starten.

   ![Das Dialogfeld „Synchronisierung“](assets/migrate-and-syncronize.png)

   **Abbildung:** *Dialogfeld „Synchronisierung“*

## Fehlerbehebung bei Synchronisierungsfehlern {#troubleshooting-synchronization-error}

Sie können neue Anwendungen im Workflow-Designer (LiveCycle Workbench) erstellen.

Wenn eine neu erstellte Anwendung und ein Ordner unter /content/dam/formsanddocuments identische Namen haben, wird der Fehler „*Ein Element mit demselben Namen wie diese Anwendung ist bereits auf der Stammebene vorhanden.*“ protokolliert. 

Benennen Sie zum Beheben des Konflikts die Anwendung um und synchronisieren Sie die Elemente manuell.

![Das Dialogfeld „Konflikte bei der Synchronisierung von Elementen“](assets/sync-conflict.png)

**Abbildung:** *Dialogfeld „Konflikte bei der Synchronisierung von Elementen“*
