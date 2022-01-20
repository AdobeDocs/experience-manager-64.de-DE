---
title: XMP-Writeback zu Ausgabedarstellungen
description: Erfahren Sie, wie die XMP-Writeback-Funktion die Metadaten für ein Asset an alle oder spezifische Ausgabeformate des Elements propagiert.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 456f8c91-aacf-4db5-a329-2d1650ff0f2f
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 61%

---

# XMP-Writeback zu Ausgabedarstellungen {#xmp-writeback-to-renditions}

Die XMP-Writeback-Funktion in [!DNL Adobe Experience Manager Assets] repliziert Änderungen von Metadaten in den Ausgabedarstellungen des Original-Assets. Wenn Sie die Metadaten für ein Asset in Assets ändern oder das Asset hochladen, werden die Änderungen zunächst im Metadatenknoten in der Asset-Hierarchie gespeichert.

Mit der XMP-Writeback-Funktion können Sie die Metadatenänderungen in alle oder nur in bestimmte Ausgabedarstellungen des Assets kopieren. Die Funktion schreibt nur die Metadateneigenschaften zurück, die den Namespace `jcr` verwenden, d. h. eine Eigenschaft namens `dc:title` wird zurückgeschrieben, eine Eigenschaft namens `mytitle` jedoch nicht.

Stellen Sie sich vor, Sie ändern die Eigenschaft [!UICONTROL Titel] des Assets `Classic Leather` in `Nylon`.

![Metadaten](assets/metadata.png)

In diesem Fall wird die [!DNL Experience Manager] Assets speichert die Änderungen an der **[!UICONTROL Titel]** -Eigenschaft in `dc:title` -Parameter für die in der Asset-Hierarchie gespeicherten Asset-Metadaten.

![metadata_stored](assets/metadata_stored.png)

[!DNL Experience Manager Assets] propagiert die Metadatenänderungen jedoch nicht automatisch in die Ausgabedarstellungen eines Assets. Siehe [Wie wird XMP Writeback aktiviert?](#enabling-xmp-writeback).

## Aktivieren der XMP-Writeback-Funktion {#enabling-xmp-writeback}

Um Metadatenänderungen beim Hochladen des Assets in die Ausgabeformate zu propagieren, bearbeiten Sie die Konfiguration **Adobe CQ DAM Rendition Maker** in Configuration Manager.

1. Öffnen Sie Configuration Manager über `https://[aem_server]:[port]/system/console/configMgr`.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]**.
1. Wählen Sie die Option **[!UICONTROL XMP propagieren]** aus und speichern Sie die Änderungen.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Aktivieren XMP Writeback für bestimmte Ausgabeformate {#enabling-xmp-writeback-for-specific-renditions}

Damit die XMP-Writeback-Funktion die Metadatenänderungen in die Ausgabeformate kopieren kann, müssen Sie diese Ausgabeformate im Workflow-Schritt „XMP-Writeback-Vorgang“ des Workflows „DAM-Metadaten-Writeback“ angeben. Standardmäßig ist dieser Schritt mit dem ursprünglichen Format konfiguriert.

Führen Sie folgende Schritte durch, damit die XMP-Writeback-Funktion Metadaten in die Ausgabeformat-Miniaturansichten „140.100.png“ und „319.319.png“ übertragen.

1. Navigieren Sie in Experience Manager zu **[!UICONTROL Tools > Workflow > Modelle]**.
1. Aus dem [!UICONTROL Modelle] Seite, öffnen Sie die **[!UICONTROL DAM-Metadaten-Writeback]** Workflow-Modell.
1. Öffnen Sie auf der Eigenschaftsseite **[!UICONTROL DAM-Metadaten-Writeback]** den Schritt **[!UICONTROL XMP-Writeback-Vorgang]**.
1.  Tippen/Klicken Sie im Dialogfeld **[!UICONTROL Schritt-Eigenschaften]** auf die Registerkarte **[!UICONTROL Prozess]**.
1. Im **[!UICONTROL Argumente]** Feld, hinzufügen `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Tippen/klicken **[!UICONTROL OK]**.

   ![Schritteigenschaften](assets/step_properties.png)

1. Um die Pyramid-TIFF-Ausgabeformate für Dynamic Media-Bilder mit den neuen Attributen neu zu generieren, fügen Sie die **[!UICONTROL Dynamic Media Process Image Assets]** Schritt zum Workflow &quot;DAM-Metadaten-Writeback&quot;.
PTIFF-Ausgabeformate werden nur lokal im Dynamic Media Hybridmodus erstellt und gespeichert. Speichern Sie den Workflow.

Die Metadatenänderungen werden in die Ausgabeformate übertragen `thumbnail.140.100.png` und `thumbnail.319.319.png` des Assets und nicht der anderen.

>[!NOTE]
>
>XMP Probleme beim Writeback unter 64 Bit Linux finden Sie unter [Aktivieren XMP Writeback auf 64-Bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Weitere Informationen zu unterstützten Plattformen finden Sie unter [Voraussetzungen für XMP Zurückschreiben von Metadaten](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtern von XMP-Metadaten {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] unterstützt sowohl die Blockierungsliste- als auch die Zulassungsliste-Filterung von Eigenschaften/Knoten für XMP Metadaten, die aus Asset-Binärdateien gelesen und in JCR gespeichert werden, wenn Assets erfasst werden.

Bei der Filterung über eine Blockierungsliste können Sie alle XMP-Metadateneigenschaften importieren – mit Ausnahme der Eigenschaften, für die ein Ausschluss angegeben ist. Jedoch ist der Name der zu filternden Knoten für Elementtypen wie INDD-Dateien mit enormen Mengen an XMP-Metadaten (z. B. 1.000 Knoten mit 10.000 Eigenschaften) nicht immer bereits im Voraus bekannt. Wenn beim Filtern mit einer Blockierungsliste eine große Anzahl von Assets mit zahlreichen XMP Metadaten importiert werden kann, wird die [!DNL Experience Manager] -Instanz oder -Cluster auf Stabilitätsprobleme stoßen, z. B. blockierte Beobachtungswarteschlangen.

Durch Filtern von XMP-Metadaten über die Zulassungsliste wird dieses Problem behoben, indem Sie die zu importierenden XMP-Eigenschaften definieren können. Auf diese Weise werden andere/unbekannte XMP-Eigenschaften ignoriert. Aus Gründen der Abwärtskompatibilität können Sie einige dieser Eigenschaften dem Filter hinzufügen, der eine Blockierungsliste verwendet.

>[!NOTE]
>
>Die Filterung funktioniert nur für aus XMP-Quellen in Asset-Binärdateien abgeleitete Eigenschaften. Bei Eigenschaften, die aus XMP-fremden Quellen wie EXIF- und IPTC-Formaten abgeleitet wurden, funktioniert die Filterung nicht. Beispielsweise wird das Datum der Asset-Erstellung in der Eigenschaft `CreateDate` in EXIF TIFF gespeichert. [!DNL Experience Manager] speichert diesen Wert im Metadatenfeld mit dem Namen `exif:DateTimeOriginal`. Da es sich um eine andere Quelle als XMP handelt, funktioniert die Filterung nicht bei dieser Eigenschaft.

1. Öffnen Sie Configuration Manager über `https://[aem_server]:[port]/system/console/configMgr`.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM XmpFilter]**.
1. Um die Filterfunktion mit einer Zulassungsliste anzuwenden, klicken Sie auf **[!UICONTROL Zulassungsliste auf XMP-Eigenschaften anwenden]** und geben Sie die Eigenschaften an, die in das Feld **[!UICONTROL Zulässige XML-Namen für XMP-Filterfunktion]** importiert werden sollen.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Um die blockierten XMP nach Anwendung der Filterung über die Zulassungsliste herauszufiltern, geben Sie diese in der **[!UICONTROL Blockierte XML-Namen für XMP Filterung]** ankreuzen. Speichern Sie die Änderungen.

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Blockierungsliste auf XMP-Eigenschaften anwenden]** ist standardmäßig ausgewählt. Mit anderen Worten, das Filtern über eine Blockierungsliste ist standardmäßig aktiviert. Um diese Filterung zu deaktivieren, deaktivieren Sie die Option **[!UICONTROL Anwenden der Blockierungsliste auf XMP Eigenschaften]** -Option.
