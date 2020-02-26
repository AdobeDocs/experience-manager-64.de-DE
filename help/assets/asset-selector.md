---
title: Asset-Wähler
description: Erfahren Sie, wie Sie mit dem Asset-Wähler Metadaten für Assets in Adobe Experience Manager (AEM) suchen, filtern, durchsuchen und abrufen. Erfahren Sie außerdem mehr über das benutzerdefinierte Anpassen der Oberfläche des Asset-Wählers.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Asset-Wähler {#asset-selector}

>[!NOTE]
>
>Der Asset-Wähler wurde in früheren AEM-Versionen als [Asset-Auswahl](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) bezeichnet.

Mit dem Asset-Wähler können Sie in Adobe Experience Manager (AEM) Assets nach Assets suchen und diese filtern und durchsuchen. Außerdem können Sie die Metadaten der Assets abrufen, die Sie über den Asset-Wähler auswählen. Sie können die Benutzeroberfläche des Asset-Wählers mit unterstützten Anforderungsparametern starten, um sie anzupassen. Mit diesen Parametern wird der Kontext des Asset-Wählers für ein bestimmtes Szenario festgelegt.

Currently, you can pass the request parameters `Asset Type` (*Image/Video/Text*) and `Selection mode` (*Single/Multiple*) as contextual information for the asset selector, which remains intact throughout the selection.

The asset selector uses the HTML5 **Window.postMessage** message to send data for the selected asset to the recipient.

Der Asset-Wähler basiert auf dem Vokabular der Foundation-Auswahl von Granite. Standardmäßig befindet sich der Asset-Wähler im Modus „Durchsuchen“. Sie können jedoch mithilfe der Omniture Search-Erfahrung Filter anwenden, um Ihre Suche nach bestimmten Assets zu verfeinern.

You can integrate any web page (irrespective of whether it is part of the CQ container) with the asset selector (`https://[AEM_server]:[port]/aem/assetpicker.html`).

## Kontextparameter {#contextual-parameters}

Sie können die folgenden Anforderungsparameter in einer URL übergeben, um den Asset-Wähler in einem bestimmten Kontext zu starten:

| Name | Werte | Beispiel | Zweck |
|---|---|---|---|
| resource suffix (B) | Ordnerpfad als Ressourcensuffix in der URL:`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | To launch the asset selector with a particular folder selected, for example with the folder `/content/dam/we-retail/en/activities` selected, the URL should be of the form: `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | Wenn beim Starten des Asset-Wählers ein bestimmter Ordner ausgewählt sein soll, können Sie ihn als Ressourcensuffix übergeben. |
| mode | single, multiple | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | Im Modus „multiple“ können Sie mit dem Asset-Wähler mehrere Assets gleichzeitig auswählen. |
| mimetype | mimetype(s) (`/jcr:content/metadata/dc:format`) of an asset (wildcard also supported) | <ul><li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*presentation&mimetype=*png`</li></ul> | Verwenden Sie diese Option zum Filtern von Assets anhand von MIME-Typen. |
| dialog | true, false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | Verwenden Sie diese Parameter, um die Asset-Auswahl als Granite-Dialog zu öffnen. Diese Option ist nur verfügbar, wenn Sie die Asset-Auswahl über das Granite Path Field starten und als pickerSrc-URL konfigurieren. |
| assettype (S) | images, documents, multimedia, archives | <ul><li>`http://localhost:4502/aem/assetpicker.html`<br>`?assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=archives`</li> | Verwenden Sie diese Option, um die Asset-Typen basierend auf dem übergebenen Wert zu filtern. |
| root | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | Verwenden Sie diese Option, um den Stammordner für den Asset-Wähler anzugeben. In diesem Fall können Sie mit dem Asset-Wähler nur untergeordnete Assets (direkt/indirekt) unter dem Stammordner auswählen. |

## Verwenden der Asset-Auswahl {#using-the-asset-selector}

1. To access the asset selector interface, go to `https://[AEM_server]:[port]/aem/assetpicker`.
1. Navigieren Sie zum gewünschten Ordner und wählen Sie mindestens ein Asset aus.

   ![chlimage_1-441](assets/chlimage_1-441.png)

   Alternativ dazu können Sie über das OmniSearch-Feld nach dem gewünschten Asset suchen und es dann auswählen.

   ![chlimage_1-442](assets/chlimage_1-442.png)

   Wenn Sie das OmniSearch-Feld zum Suchen nach Assets verwenden, können Sie im Bereich **[!UICONTROL Filter]** verschiedene Filter auswählen, um Ihre Suche einzugrenzen.

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. Tap/click **[!UICONTROL Select]** from the toolbar.
