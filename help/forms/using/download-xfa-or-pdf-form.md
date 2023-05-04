---
title: Herunterladen von XFA- oder PDF-Formularvorlagen
seo-title: Download an XFA or a PDF form template
description: Sie können Formulare aus dem Repository in das lokale System exportieren und die heruntergeladenen Formulare in das neue Repository migrieren.
seo-description: You can export forms from the repository to the local system and migrate the downloaded forms to new repository.
uuid: 5f7fbd14-cb9d-4749-8708-7efe49df89d7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 6699e0e7-fd42-41ae-86a2-3b940d905111
role: Admin
exl-id: 68d881c6-7507-4018-b40e-205604221d0c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 38%

---

# Herunterladen von XFA- oder PDF-Formularvorlagen {#download-an-xfa-or-a-pdf-form-template}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Download-Vorgang ermöglicht, wie der Name schon sagt, den Export von Formularen aus dem Repository in das lokale System. In Kombination mit dem Upload-Vorgang hilft dieser Vorgang Ihnen bei der Migration Ihrer Formulare von einem Repository zu einem anderen.

In AEM Forms wird der Download-Vorgang für die folgenden Asset-Typen unterstützt:

* Formularvorlagen (XFA Forms)
* PDF forms
* Dokumente (flache PDF-Dateien)

AEM Forms unterstützt den Download dieser Formulartypen einzeln oder in einem Ordner mit einem oder mehreren unterstützten Formularen.

Abgesehen von diesen Elementen können Sie den `Resource`-Elementtyp herunterladen, wenn er in einem Ordner vorhanden ist. Diese Funktion wird bereitgestellt, damit Sie neben dem Formular die Ressource herunterladen können, auf die ein XFA-Formular verweist.

## Herunterladen von einem oder mehreren Formularen {#download-one-or-more-forms}

1. Melden Sie sich bei der AEM Forms-Benutzeroberfläche unter `https://<server>:<port>/aem/forms.html` an.

1. Navigieren Sie zum Speicherort des Assets, das Sie herunterladen möchten.

1. Wählen Sie das Asset aus. Klicken Sie auf der Symbolleiste auf **[!UICONTROL Herunterladen]** ![aem6forms_download](assets/aem6forms_download.png).

   >[!NOTE]
   >
   >Sie können nur ein Formular zum Herunterladen auswählen. Wenn Sie mehrere Formulare herunterladen möchten, müssen Sie sie als Ordner herunterladen.

1. Klicken Sie im eingeblendeten Dialogfeld auf **[!UICONTROL Herunterladen]**.

   AEM Forms generiert eine ZIP-Datei, die die ausgewählte Datei oder den ausgewählten Ordner enthält.

   Wenn Sie einen Ordner herunterladen, werden die unterstützten Assets innerhalb des Ordners in ihre vorhandene Hierarchie heruntergeladen.

   Die ZIP-Datei wird im Ordner `Downloads` auf Ihrem System gespeichert.

## Überlegungen zum Upload-Vorgang {#related-considerations-for-the-upload-operation}

* Sie können die ZIP-Datei an einen anderen Speicherort im selben Repository oder in einem anderen Repository hochladen.
* Die Hierarchie der Assets in einem Ordner wird während des Upload-Vorgangs beibehalten
* Änderungen, die vor dem Download an den Metadaten der heruntergeladenen Assets vorgenommen werden, werden beim Hochladen angezeigt. 
