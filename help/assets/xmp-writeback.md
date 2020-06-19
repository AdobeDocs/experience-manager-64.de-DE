---
title: XMP-Writeback in Ausgabeformaten
description: Erfahren Sie, wie die XMP-Writeback-Funktion die Metadaten für ein Asset an alle oder spezifische Ausgabeformate des Elements propagiert.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 46%

---


# XMP-Writeback in Ausgabeformaten {#xmp-writeback-to-renditions}

Die XMP-Writeback-Funktion in Adobe Experience Manager (AEM) Assets repliziert Änderungen von Asset-Metadaten in den Ausgabeformaten des Assets.

Wenn Sie die Metadaten für ein Asset innerhalb von AEM Assets oder beim Hochladen des Assets ändern, werden Änderungen zunächst innerhalb des Asset-Knotens in CRX-De gespeichert.

Die XMP-Funktion &quot;Schriftarterfassung&quot;propagiert die Änderungen der Metadaten an alle oder bestimmte Darstellungen des Assets.

Stellen Sie sich vor, Sie ändern die Eigenschaft [!UICONTROL Titel] des Assets `Classic Leather` in `Nylon`.

![Metadaten](assets/metadata.png)

In diesem Fall speichert AEM Assets die Änderungen an der Eigenschaft **[!UICONTROL Titel]** im Parameter `dc:title` der in der Elementhierarchie gespeicherten Asset-Metadaten.

![metadata_stored](assets/metadata_stored.png)

AEM Assets propagiert die Metadatenänderungen jedoch nicht automatisch in die Ausgabeformate eines Assets.

Mit der XMP-Funktion &quot;Schriftarterfassung&quot;können Sie die Metadatenänderungen an alle oder bestimmte Darstellungen des Assets weiterleiten. Die Änderungen werden allerdings nicht unter dem Metadatenknoten in der Asset-Hierarchie gespeichert. Stattdessen werden die Änderungen mit dieser Funktion in die Binärdateien für die Ausgabeformate eingebettet.

## XMP-Schreibback aktivieren {#enabling-xmp-writeback}

Um Metadatenänderungen beim Hochladen des Assets in die Ausgabeformate zu propagieren, bearbeiten Sie die Konfiguration **Adobe CQ DAM Rendition Maker** in Configuration Manager.

1. Öffnen Sie Configuration Manager von `https://[aem_server]:[port]/system/console/configMgr`.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]**.
1. Wählen Sie die Option **[!UICONTROL XMP propagieren]** aus und speichern Sie die Änderungen.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Enable XMP writeback for specific renditions {#enabling-xmp-writeback-for-specific-renditions}

Damit die XMP-Writeback-Funktion die Metadatenänderungen in die Ausgabeformate kopieren kann, müssen Sie diese Ausgabeformate im Workflow-Schritt „XMP-Writeback-Vorgang“ des Workflows „DAM-Metadaten-Writeback“ angeben. Standardmäßig ist dieser Schritt mit dem ursprünglichen Format konfiguriert.

Führen Sie folgende Schritte durch, damit die XMP-Writeback-Funktion Metadaten in die Ausgabeformat-Miniaturansichten „140.100.png“ und „319.319.png“ übertragen.

1. Navigieren Sie in Experience Manager zu **[!UICONTROL Tools > Workflow > Modelle]**.
1. From the [!UICONTROL Models] page, open the **[!UICONTROL DAM Metadata Writeback]** workflow model.
1. Öffnen Sie auf der Eigenschaftsseite **[!UICONTROL DAM-Metadaten-Writeback]** den Schritt **[!UICONTROL XMP-Writeback-Vorgang]**.
1.  Tippen/Klicken Sie im Dialogfeld **[!UICONTROL Schritt-Eigenschaften]** auf die Registerkarte **[!UICONTROL Prozess]**.
1. In the **[!UICONTROL Arguments]** box, add `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Tap/click **[!UICONTROL OK]**.

   ![Schritteigenschaften](assets/step_properties.png)

1. To regenerate the pyramid TIFF renditions for Dynamic Media images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the DAM Metadata Writeback workflow.
PTIFF-Darstellungen werden nur lokal im Hybrid-Modus von Dynamic Media erstellt und gespeichert. Speichern Sie den Workflow.

The metadata changes are propagated to the renditions `thumbnail.140.100.png` and `thumbnail.319.319.png` of the asset, and not the others.

>[!NOTE]
>
>For XMP writeback issues in 64 bit Linux, see [How to enable XMP write-back on 64-bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>For more information about supported platforms, see [XMP metadata write-back prerequisites](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtern von XMP-Metadaten {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] unterstützt das blockierungsliste- und zulassungsliste-Filtern von Eigenschaften/Knoten für XMP-Metadaten, die aus Asset-Binärdateien gelesen und in JCR gespeichert werden, wenn Assets aufgenommen werden.

Beim Filtern mit einer blockierungsliste können Sie alle XMP-Metadateneigenschaften mit Ausnahme der Eigenschaften importieren, die für den Ausschluss angegeben wurden. Jedoch ist der Name der zu filternden Knoten für Elementtypen wie INDD-Dateien mit enormen Mengen an XMP-Metadaten (z. B. 1.000 Knoten mit 10.000 Eigenschaften) nicht immer bereits im Voraus bekannt. Wenn beim Filtern mit einer blockierungsliste eine große Anzahl von Assets mit zahlreichen XMP-Metadaten importiert werden kann, kann es bei der AEM-Instanz oder dem AEM-Cluster zu Stabilitätsproblemen kommen, z. B. zu verstopften Beobachtungswarteschlangen.

Das Filtern von XMP-Metadaten über zulassungsliste behebt dieses Problem, indem Sie die zu importierenden XMP-Eigenschaften definieren können. Auf diese Weise werden alle anderen oder unbekannten XMP-Eigenschaften ignoriert. Zur Abwärtskompatibilität können Sie einige dieser Eigenschaften zum Filter hinzufügen, der eine blockierungsliste verwendet.

>[!NOTE]
>
>Die Filterung funktioniert nur für aus XMP-Quellen in Asset-Binärdateien abgeleitete Eigenschaften. Bei Eigenschaften, die aus XMP-fremden Quellen wie EXIF- und IPTC-Formaten abgeleitet wurden, funktioniert die Filterung nicht. Beispielsweise wird das Datum der Asset-Erstellung in der Eigenschaft `CreateDate` in EXIF TIFF gespeichert. AEM stores this value in the metadata field named `exif:DateTimeOriginal`. Da es sich um eine andere Quelle als XMP handelt, funktioniert die Filterung nicht bei dieser Eigenschaft.

1. Öffnen Sie Configuration Manager von `https://[aem_server]:[port]/system/console/configMgr`.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM XmpFilter]**.
1. To apply filtering via an allowed list, select **[!UICONTROL Apply Allowlist to XMP Properties]**, and specify the properties to be imported in the **[!UICONTROL Allowed XML Names for XMP filtering]** box.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Um blockierte XMP-Eigenschaften nach dem Anwenden der Filterung über zulassungsliste zu filtern, geben Sie diese im Feld **[!UICONTROL Blockierte XML-Namen für die XMP-Filterung]** an. Speichern Sie die Änderungen.

   >[!NOTE]
   >
   >The **[!UICONTROL Apply Blocklist to XMP Properties]** option is selected by default. Das heißt, das Filtern mit einer blockierungsliste ist standardmäßig aktiviert. To disable such filtering, deselect the **[!UICONTROL Apply Blocklist to XMP Properties]** option.
