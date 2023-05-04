---
title: Importieren und Exportieren der PDF Generator-Konfigurationsdateien
seo-title: Importing and exporting PDF Generator configuration files
description: Erfahren Sie, wie Sie PDF Generator-Konfigurationsdateien importieren und exportieren.
seo-description: Learn how to import and export PDF Generator configuration files.
uuid: 3367253b-d222-4c5f-9455-a1810d96112e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e25c1b35-73eb-4353-8e39-a2d4cdccd101
feature: PDF Generator
exl-id: 57673410-b8f1-494e-b4a0-c6724bab643c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 12%

---

# Importieren und Exportieren der PDF Generator-Konfigurationsdateien {#importing-and-exporting-pdf-generator-configuration-files}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Konfigurationsdatei enthält die PDF Generator-Konvertierungsinformationen, einschließlich PDF, Dateityp und Sicherheitseinstellungen.

>[!NOTE]
>
>Sie können die Zeitlimiteinstellung für PDF Generator nicht ändern, indem Sie eine benutzerdefinierte Datei &quot;native2pdfconfig.xml&quot;importieren. Die Zeitlimiteinstellung in dieser Datei dient nur zu Informationszwecken und zeigt die aktuelle Einstellung in PDF Generator an. Informationen zum Ändern der Zeitlimiteinstellung finden Sie unter &quot;Festlegen von Leistungsparametern für PDF Generator&quot;unter [Installieren und Bereitstellen von AEM](https://www.adobe.com/go/learn_aemforms_installJBoss_63_de).

## Aktuelle Konfigurationsdatei exportieren {#export-your-current-configuration-file}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Exportkonfiguration&quot;.
1. Um die Einstellungen zu exportieren, wählen Sie die entsprechende Option aus:

   * Um alle benannten Einstellungen zu exportieren, wählen Sie Gesamte Konfiguration herunterladen aus.
   * Um nur eine Adobe PDF-Einstellung, Sicherheitseinstellung oder Dateitypeinstellung zu exportieren, wählen Sie &quot;Minimale Konfiguration herunterladen&quot;aus.

      Wenn Sie eine Mindestkonfiguration exportieren, wählen Sie die zu exportierenden Einstellungen für Adobe PDF, Sicherheit und Dateityp aus.

1. Klicken Sie auf Herunterladen und speichern Sie die XML-Datei an einem entsprechenden Speicherort.

## Importieren einer Konfigurationsdatei {#import-a-configuration-file}

>[!NOTE]
>
>Ihr System wird basierend auf den Informationen in der importierten Datei neu konfiguriert.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Importkonfiguration&quot;.
1. Wählen Sie &quot;Vorhandene Konfigurationsdatei importieren&quot;.
1. Um den Speicherort der Datei im Feld &quot;Konfigurationsdatei&quot;anzugeben, klicken Sie auf &quot;Durchsuchen&quot;, um die Datei zu suchen und auszuwählen, und klicken Sie dann auf **Import**.

## Alle Ebenen in AutoCAD-Dateien konvertieren {#convert-all-layers-within-autocad-files}

Standardmäßig konvertiert PDF Generator nur die Standardebene von AutoCAD-Dateien in PDF anstelle aller Ebenen in der Datei. Gehen Sie wie folgt vor, um alle Ebenen zu konvertieren.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Exportkonfiguration&quot;.
1. Wählen Sie Gesamte Konfiguration herunterladen und klicken Sie auf Herunterladen.
1. Öffnen Sie die heruntergeladene Datei in einem Texteditor und fügen Sie unterhalb des Tags `AutoCAD`, aber innerhalb des Tags `PDFMaker` den Text `convertAllPages="true"` hinzu.
1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Importkonfiguration&quot;.
1. Wählen Sie &quot;Vorhandene Konfigurationsdatei importieren&quot;aus, geben Sie die aktualisierte Datei an und klicken Sie auf &quot;Importieren&quot;.

   Bei allen AutoCAD-Dateien, die mithilfe der geänderten Konfigurationsdatei konvertiert werden, werden alle Ebenen konvertiert.

## Zurücksetzen der Konfiguration auf die ursprünglichen Einstellungen, die mit PDF Generator installiert wurden {#reset-your-configuration-to-the-original-settings-installed-with-pdf-generator}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Konfigurationsdateien&quot;> &quot;Importkonfiguration&quot;.
1. Wählen Sie &quot;Konfiguration auf Standardeinstellungen zurücksetzen&quot;und klicken Sie auf &quot;Importieren&quot;.
