---
title: Anleitung zum Bearbeiten oder Hinzufügen von Metadaten
description: Erfahren Sie mehr über Asset-Metadaten in AEM Assets und lernen Sie die verschiedenen Bearbeitungsmöglichkeiten kennen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Anleitung zum Bearbeiten oder Hinzufügen von Metadaten {#how-to-edit-or-add-metadata}

Metadaten sind zusätzliche Informationen zum Element, die durchsucht werden können. Beim Hochladen eines Bildes werden sie automatisch extrahiert. Sie können die vorhandenen Metadaten bearbeiten oder neue Metadateneigenschaften vorhandenen Feldern hinzufügen (etwa wenn ein Metadatenfeld leer ist).

Da Unternehmen gesteuertes und zuverlässiges Metadatenvokabular benötigen, lässt AEM Assets das Adhoc-Hinzufügen von neuen Metadateneigenschaften nicht zu. Autoren können keine neuen Metadatenfelder für Assets hinzufügen, Entwickler hingegen schon. Informationen finden Sie unter [Erstellen neuer Metadateneigenschaften für Assets](meta-edit.md#editing-metadata-schema).

## Bearbeiten von Metadaten für ein Asset {#editing-metadata-for-an-asset}

So bearbeiten Sie Metadaten:

1. Führen Sie einen der folgenden Schritte aus:

   * From the Assets UI, select the asset and click/tap the **[!UICONTROL View Properties]** icon from the toolbar.
   * From the asset thumbnail, select the **[!UICONTROL View Properties]** quick action.
   * From the asset page, click/tap the **[!UICONTROL View Properties]** icon ![info icon](assets/do-not-localize/info_icon.png) from the toolbar.
   Auf der Asset-Seite werden alle Metadaten des Assets angezeigt. Diese Metadaten wurden beim Hochladen (Erfassen) in AEM Assets automatisch extrahiert.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Nehmen Sie die gewünschten Änderungen an den Metadaten unter den verschiedenen Registerkarten vor und tippen/klicken Sie nach Abschluss der Bearbeitung in der Symbolleiste auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Tippen/Klicken Sie auf **[!UICONTROL Schließen]**, um zur Assets-Weboberfläche zurückzukehren.

   >[!NOTE]
   >
   >Ein leeres Textfeld gibt an, dass kein Metadatenset vorhanden ist. Sie können einen Wert in das Feld eingeben und speichern, um diese Metadateneigenschaft hinzuzufügen. 

Änderungen an den Metadaten eines Assets werden als Teil der XMP-Daten in die ursprüngliche Binärdatei zurückgeschrieben. Dies geschieht über den Writeback-Workflow der AEM-Metadaten. Änderungen an den vorhandenen Eigenschaften (z. B. `dc:title`) werden überschrieben und neu erstellte Eigenschaften (einschließlich benutzerdefinierten Eigenschaften wie `cq:tags`) werden zusammen mit dem Schema hinzugefügt.

XMP-Writeback wird für die in [Technische Anforderungen](/help/sites-deploying/technical-requirements.md) beschriebenen Plattformen und Dateiformate unterstützt und aktiviert.

## Bearbeiten von Metadatenschemata {#editing-metadata-schema}

Weitere Informationen zur Bearbeitung von Metadatenschemata finden Sie unter [Bearbeiten von Metadaten-Schemaformularen](metadata-schemas.md#editing-metadata-schema-forms).

## Registrieren eines benutzerdefinierten Namespace in AEM {#registering-a-custom-namespace-within-aem}

Sie können eigene Namespaces in AEM hinzufügen. Es gibt vordefinierte Namespaces wie cq, jcr und sling. Sie können aber auch einen Namespace für Ihre Repository-Metadaten und die XML-Verarbeitung hinzufügen.

1. Go to the node type administration page `https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Click or tap **[!UICONTROL Namespaces]** at the top of the page. Die Seite zur Namespace-Verwaltung wird in einem Fenster angezeigt. 

1. To add a namespace, click or tap **[!UICONTROL New]** at the bottom.
1. Specify a custom namespace in the XML namespace convention (Specify the id in the form of a URI and an associated prefix for the id), and click or tap **[!UICONTROL Save]**.
