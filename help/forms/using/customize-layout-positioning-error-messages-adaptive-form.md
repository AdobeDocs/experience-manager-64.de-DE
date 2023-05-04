---
title: Anpassen des Layouts und der Positionierung von Fehlermeldungen eines adaptiven Formulars
seo-title: Customize layout and positioning of error messages of an adaptive form
description: Sie können das Layout und die Positionierung der Fehlermeldungen eines adaptiven Formulars anpassen.
seo-description: You can customize layout and positioning of the error messages of an adaptive for.
uuid: 18b6d770-8b68-4aa0-b866-6325a6ceabcf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: e1431ad9-3bae-4ac3-97e2-96dcbfce1f71
exl-id: a57bd3c4-2d50-4089-8279-1e403e9469bf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 38%

---

# Layout und Positionierung von Fehlermeldungen eines adaptiven Formulars anpassen {#customize-layout-and-positioning-of-error-messages-of-an-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können das Layout und die Positionierung der Fehlermeldungen eines adaptiven Formulars anpassen. Sie können die folgenden Anpassungen vornehmen:

* Position und Layout der Beschriftung eines Felds ohne Ändern der entsprechenden CSS-Eigenschaften anpassen
* Position von Inline-Fehlermeldungen anpassen
* Inhalt der dynamischen Hilfeanzeige anpassen
* Position der Feldkomponenten (Beschriftung, Widget, Kurzbeschreibung, Langbeschreibung und Komponenten der Hilfeanzeige) anpassen, ohne die entsprechenden CSS-Eigenschaften zu ändern

## Layout von Feldern anpassen {#customize-layout-of-fields}

Sie können das Layout eines einzelnen Felds oder aller Felder anpassen, um die Position von Beschriftungen und Fehlermeldungen zu ändern. Führen Sie die folgenden Schritte aus, um ein benutzerdefiniertes Layout auf ein Feld anzuwenden:

### Layout eines einzelnen Felds anpassen {#customize-layout-of-a-single-field}

Führen Sie die folgenden Schritte aus, um ein benutzerdefiniertes Layout auf ein einzelnes Feld anzuwenden:

1. Öffnen Sie das Formular im **Stilmodus**. Um das Formular im Stilmodus zu öffnen, tippen Sie in der Seitensymbolleiste auf ![canvas-drop-down](assets/canvas-drop-down.png) > **Stil**.
1. Wählen Sie in der Randleiste unter **Formularobjekte** das Feld aus und tippen Sie auf die Bearbeiten-Schaltfläche ![edit-button](assets/edit-button.png).
1. Wählen Sie den Status des Feldes, das Sie anpassen möchten, und geben Sie den Stil für diesen Status an.

   ![Festlegen des Inline-Stils für ein Feld](assets/edit-error-state.png)

### Layout aller Felder eines Formulars anpassen {#customize-layout-of-all-the-fields-of-a-form}

Mit AEM Forms können Sie jetzt ein Design erstellen und es auf Ihr Formular anwenden. Mit dem Design-Editor können Sie die Formatierung von Formularkomponenten an einer Stelle festlegen. Wenn Sie ein Design erstellen, geben Sie die Formatierung auf Komponentenebene an. Weitere Informationen zu Themen finden Sie unter [Designs in AEM Forms](/help/forms/using/themes.md).

Erstellen Sie ein Design mit dem Design-Editor, um das Layout aller Felder in Ihrem Formular anzupassen. Nachdem Sie ein Design erstellt haben, führen Sie die folgenden Schritte aus, um es auf ein Formular anzuwenden:

1. Öffnen Sie das Formular im Bearbeitungsmodus.
1. Wählen Sie im Bearbeitungsmodus eine Komponente aus und tippen Sie anschließend auf ![field-level](assets/field-level.png) > **Container für ein adaptives Formular** und dann auf ![cmppr](assets/cmppr.png).
1. Wählen Sie in der Seitenleiste unter Adaptives Formulardesign das Design aus, das Sie mit dem Design-Editor erstellt haben.

## Benutzerdefiniertes Feldlayout erstellen {#create-a-custom-field-layout}

1. Öffnen Sie CRXDE Lite. Die Standard-URL ist `https://[Server]:[Port]/crx/de`.
1. Kopieren Sie ein Feldlayout vom Knoten /libs/fd/af/layouts/field (z. B. defaultFieldLayout) in den Knoten /apps (z. B. /apps/af-field-layout).
1. Benennen Sie den kopierten Knoten und die Datei defaultFieldLayout.jsp um. Beispielsweise in „errorOnRight.jsp“. 

1. Ändern Sie die Werte der Eigenschaften „qtip“ und „jcr:description“ des kopierten Knotens. Ändern Sie z. B. den Wert der Eigenschaften in „Error On Right“ 

1. Um neue Stile und Verhaltensweisen hinzuzufügen, erstellen Sie eine Client-Bibliothek im Knoten /etc .

   Erstellen Sie z. B. im Verzeichnis „/etc/af-field-layout-clientlib“ den Knoten „client-library“. Fügen Sie die Kategorieneigenschaft mit dem Wert „af.field.errorOnRight“ und die style.less-Datei mit folgendem Code hinzu:

   ```css
   .widgetErrorWrapper {
   
    height: 38px;
    margin: 5px;
   
    .guideFieldWidget{
    width: 60%;
    float: left; 
    }
   
    .guideFieldError{
    overflow:hidden;
    width:40%; 
    }
   
   }
   ```

1. Beziehen Sie zur Verbesserung des Erscheinungsbilds und der Verhaltensweise die in der Layout-Datei (errorOnRight.jsp) erstellte Clientbibliothek ein.
1. Öffnen Sie das Dialogfeld „Bearbeiten“ und wählen Sie **Formatieren**. Im **Feldlayout konfigurieren** in der Dropdown-Liste, das neu erstellte Layout auswählen und auf **OK**.

Das Package ErrorOnRight.zip enthält Code, um Fehlermeldungen auf der rechten Seite der Felder anzuzeigen.

[Datei laden](assets/erroronright.zip)
