---
title: Konfigurationsdatei importieren und exportieren
seo-title: Importing and exporting the configuration file
description: Erfahren Sie, wie Sie die Konfigurationsdatei importieren und exportieren, damit Sie Serverpräferenzen bearbeiten oder eine andere AEM Forms-Produktinstanz konfigurieren können.
seo-description: Learn how to import and export the configuration file in order to edit server preferences or configure another AEM forms product instance.
uuid: 32e8a709-2d7c-4740-9533-d53aa751bc58
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c1636537-f7dc-48d8-a3f0-9052bcd28b62
exl-id: dbad776a-60fd-4fcc-ba2a-a2f379f5462c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 100%

---

# Konfigurationsdatei importieren und exportieren {#importing-and-exporting-the-configuration-file}

Auf der Seite „Manuelle Konfiguration“ können Sie eine Kopie der Konfigurationseinstellungen im XML-Format herunterladen. Die Einstellungen in dieser Datei steuern sämtliche Servervoreinstellungen. Sie können die Datei dann bearbeiten und wieder auf den Server hochladen. Sie können die Datei auch zum Konfigurieren einer weiteren AEM Forms-Produktinstanz verwenden.

Um Sicherheitsrisiken zu vermeiden, ist der Wert für das Bindungskennwort des Ordnerservers nicht in einer exportierten Konfigurationsdatei enthalten. Aktualisieren Sie das Kennwort in der XML-Datei vor dem Import der Datei in ein neues System.

>[!NOTE]
>
>Beim Importieren der Konfigurationsdatei wird AEM Forms basierend auf den Informationen in der Datei neu konfiguriert. Nur ein Systemadministrator oder ein versierter IT-Berater, der mit dem AEM Forms-Produkt und XML vertraut ist, sollte die Konfigurationsdatei ändern. Die Bearbeitung der Konfigurationsdatei kann beispielsweise erforderlich sein, um eine fehlerhafte Einstellung neu zu konfigurieren.

**Konfigurationsinformationen exportieren**

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Exportieren“. Wenn Sie Microsoft Internet Explorer verwenden, werden Sie aufgefordert, einen Speicherort für die Datei anzugeben. Bei Verwendung von Firefox wird die Datei auf dem Desktop gespeichert.

**Konfigurationsinformationen importieren**

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die Konfigurationsdatei zu suchen, dann auf „Importieren“ und schließlich auf „OK“.
