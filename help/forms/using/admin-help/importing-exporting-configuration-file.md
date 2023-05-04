---
title: Importieren und Exportieren der Konfigurationsdatei
seo-title: Importing and exporting the configuration file
description: Erfahren Sie, wie Sie die Konfigurationsdatei importieren und exportieren, um Servervoreinstellungen zu bearbeiten oder eine andere AEM Forms-Produktinstanz zu konfigurieren.
seo-description: Learn how to import and export the configuration file in order to edit server preferences or configure another AEM forms product instance.
uuid: 32e8a709-2d7c-4740-9533-d53aa751bc58
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c1636537-f7dc-48d8-a3f0-9052bcd28b62
exl-id: dbad776a-60fd-4fcc-ba2a-a2f379f5462c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 6%

---

# Importieren und Exportieren der Konfigurationsdatei {#importing-and-exporting-the-configuration-file}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Verwenden Sie die Seite Manuelle Konfiguration , um eine Kopie der Konfigurationseinstellungen im XML-Format herunterzuladen. Die Einstellungen in dieser Datei steuern alle Servervoreinstellungen. Sie können die Datei dann bearbeiten und wieder auf den Server hochladen. Sie können die Datei auch verwenden, um eine andere AEM Forms-Produktinstanz zu konfigurieren.

Um Sicherheitsrisiken zu vermeiden, ist der Wert des Bindungskennworts für den Ordnerserver nicht in einer exportierten Konfigurationsdatei enthalten. Aktualisieren Sie das Kennwort in der XML-Datei, bevor Sie die Datei in ein neues System importieren.

>[!NOTE]
>
>Beim Import der Konfigurationsdatei werden AEM Formulare anhand der Informationen in der Datei neu konfiguriert. Nur ein Systemadministrator oder ein Professional Services-Berater, der mit dem AEM Forms-Produkt und XML vertraut ist, sollte eine Änderung der Konfigurationsdatei in Erwägung ziehen. Möglicherweise müssen sie die Konfigurationsdatei bearbeiten, um beispielsweise eine beschädigte Einstellung neu zu konfigurieren.

**Konfigurationsinformationen exportieren**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Konfigurationsdateien importieren und exportieren&quot;.
1. Klicken Sie auf Exportieren. Wenn Sie Microsoft Internet Explorer verwenden, werden Sie aufgefordert, einen Speicherort für die Datei anzugeben. Wenn Sie Firefox verwenden, wird die Datei auf Ihrem Desktop gespeichert.

**Konfigurationsinformationen importieren**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Konfigurationsdateien importieren und exportieren&quot;.
1. Klicken Sie auf Durchsuchen , um die Konfigurationsdatei zu suchen, klicken Sie auf Importieren und dann auf OK.
