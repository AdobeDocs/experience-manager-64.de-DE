---
title: Verwenden von Metadatenprofilen zum Anwenden von Standardmetadaten auf alle Assets in einem Ordner
description: Erfahren Sie mehr über Metadatenprofile für Assets. Erfahren Sie, wie Sie ein Metadatenprofil erstellen und es auf Ordner-Assets anwenden.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: a7b0f1d6-7deb-4565-8c7f-27cad7cd6bf8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 51%

---

# Metadatenprofile {#metadata-profiles}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit einem Metadatenprofil können Sie Standardmetadaten auf Assets in einem Ordner anwenden. Erstellen Sie ein Metadatenprofil und wenden Sie es auf einen Ordner an. Jedes Asset, das Sie anschließend in den Ordner hochladen, übernimmt die Standardmetadaten, die Sie im Metadatenprofil konfiguriert haben.

## Hinzufügen eines Metadatenprofils {#adding-a-metadata-profile}

1. Tippen oder klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Tools > Assets > Metadatenprofile]** und tippen Sie anschließend auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Titel für das Metadatenprofil ein, z. B. Beispielmetadaten, und klicken Sie auf **[!UICONTROL Einsenden]**. Die **[!UICONTROL Formular bearbeiten]** für das Metadatenprofil angezeigt.

   ![chlimage_1-480](assets/chlimage_1-480.png)

1. Klicken Sie auf eine Komponente und konfigurieren Sie deren Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Klicken Sie beispielsweise auf die Komponente **[!UICONTROL Beschreibung]** und bearbeiten Sie die zugehörigen Eigenschaften.

   ![chlimage_1-481](assets/chlimage_1-481.png)

   Bearbeiten Sie die folgenden Eigenschaften für die Komponente **[!UICONTROL Beschreibung]**:

   * **[!UICONTROL Feldbezeichnung]**: Der Anzeigename der Metadateneigenschaft. Dieser dient lediglich als Referenz für den Benutzer.
   * **[!UICONTROL Zu Eigenschaft zuordnen]**: Der Wert dieser Eigenschaft liefert den relativen Pfad/Namen zum Asset-Knoten, unter dem er im Repository gespeichert ist. Der Wert sollte immer mit `./` weil dies anzeigt, dass sich der Pfad unter dem Knoten des Assets befindet.

   ![chlimage_1-482](assets/chlimage_1-482.png)

   Der Wert, den Sie für **[!UICONTROL Zu Eigenschaft zuordnen]** angeben, wird als Eigenschaft unter dem Metadatenknoten des Assets gespeichert. Beispiel: Wenn Sie `/jcr:content/metadata/dc:desc` als Name des **[!UICONTROL Zu Eigenschaft zuordnen]**, [!DNL Experience Manager] Assets speichert den Wert `dc:desc` im Metadatenknoten des Assets.

   * **[!UICONTROL Standardwert]**: Mit dieser Eigenschaft können Sie einen Standardwert für die Metadatenkomponente hinzufügen. Wenn Sie beispielsweise „Meine Beschreibung“ angeben, wird dieser Wert der Eigenschaft `dc:desc` im Metadatenknoten des Assets zugewiesen.

   ![chlimage_1-483](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >Hinzufügen eines Standardwert zu einer neuen Metadateneigenschaft (die noch nicht im vorhanden ist). `/jcr:content/metadata` -Knoten) zeigt die Eigenschaft und deren Wert nicht auf der **[!UICONTROL Eigenschaften]** standardmäßig angezeigt. So zeigen Sie die neue Eigenschaft im [!UICONTROL Eigenschaften] -Seite des Assets ändern Sie das entsprechende Schemaformular.

1. (Optional) Fügen Sie dem **[!UICONTROL Formular bearbeiten]** von **[!UICONTROL Formular erstellen]** und konfigurieren Sie ihre Eigenschaften im **[!UICONTROL Einstellungen]** Registerkarte. Die folgenden Eigenschaften sind über die **[!UICONTROL Formular erstellen]** tab:

| Komponente | Eigenschaften |
|---|---|
| [!UICONTROL Bereichs-Kopfzeile] | Feldbezeichnung, <br>-Beschreibung |
| [!UICONTROL Einzeilentext] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Mehrfachwerttext] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Zahl] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Datum] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Standard-Tags] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert, <br> Beschreibung |

![chlimage_1-484](assets/chlimage_1-484.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**. Das Metadatenprofil wird zur Profilliste im **[!UICONTROL Metadatenprofile]** Seite.

   ![chlimage_1-485](assets/chlimage_1-485.png)

## Kopieren eines Metadatenprofils {#copying-a-metadata-profile}

1. Aus dem **[!UICONTROL Metadatenprofile]** ein Profil auswählen, um eine Kopie davon zu erstellen.

   ![chlimage_1-486](assets/chlimage_1-486.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Kopieren]**.
1. Im **[!UICONTROL Kopieren von Metadatenprofilen]** einen Titel für die neue Kopie des Profils eingeben.
1. Klicken **[!UICONTROL Kopieren]**. Eine Kopie des Profils wird in der Profilliste im **[!UICONTROL Metadatenprofile]** Seite.

   ![chlimage_1-487](assets/chlimage_1-487.png)

## Löschen eines Metadatenprofils {#deleting-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das zu löschende Profil aus.

   ![chlimage_1-488](assets/chlimage_1-488.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Metadatenprofile löschen]**.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Löschen]** , um den Löschvorgang zu bestätigen. Das Metadatenprofil wird aus der Liste gelöscht.

## Anwenden eines Metadatenprofils auf Ordner {#applying-a-metadata-profile-to-folders}

Wenn Sie ein Metadatenprofil zu einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Das bedeutet, dass Sie einem Ordner nur ein Metadatenprofil zuweisen können. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Metadatenprofil zugewiesen haben, überschreibt das neue Profil das vorherige Profil. Die zuvor vorhandenen Ordner-Assets bleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen wurde, werden in der Benutzeroberfläche durch den Namen des Profils angegeben, der im Kartennamen angezeigt wird.

![chlimage_1-489](assets/chlimage_1-489.png)

Sie können Metadatenprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

### Anwenden von Metadatenprofilen auf bestimmte Ordner {#applying-metadata-profiles-to-specific-folders}

Sie können ein Metadatenprofil über das Menü **[!UICONTROL Tools]** oder, falls Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** auf einen Ordner anwenden. In diesem Abschnitt wird beschrieben, wie Sie Metadatenprofile auf beide Arten auf Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Anwenden von Metadatenprofilen auf Ordner über die Benutzeroberfläche „Profile“ {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Tippen Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Tools > Assets > Metadatenprofile]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.

   ![chlimage_1-490](assets/chlimage_1-490.png)

1. Tippen Sie auf **[!UICONTROL Metadatenprofil auf Ordner anwenden]** und wählen Sie mindestens einen Ordner aus, den Sie verwenden möchten, um neu hochgeladene Assets zu empfangen. Tippen Sie anschließend auf **[!UICONTROL Fertig]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Anwenden von Metadatenprofilen auf Ordner aus „Eigenschaften“ {#applying-metadata-profiles-to-folders-from-properties}

1. Tippen Sie auf der linken Leiste auf **[!UICONTROL Assets]** und navigieren Sie dann zu dem Ordner, auf den Sie ein Metadatenprofil anwenden möchten.
1. Tippen Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und tippen Sie anschließend auf **[!UICONTROL Eigenschaften]**.

1. Wählen Sie die **[!UICONTROL Metadatenprofile]** und wählen Sie das Profil aus dem Dropdown-Menü aus und klicken Sie auf **[!UICONTROL Speichern]**.

   ![chlimage_1-491](assets/chlimage_1-491.png)

   Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

### Globales Anwenden eines Metadatenprofils {#applying-a-metadata-profile-globally}

Zusätzlich zur Anwendung eines Profils auf einen Ordner können Sie auch ein Profil global anwenden, sodass alle Inhalte, die in hochgeladen wurden, [!DNL Experience Manager] auf Assets in einem beliebigen Ordner das ausgewählte Profil angewendet wird. Gehen Sie wie folgt vor, um ein Metadatenprofil global anzuwenden:

1. Führen Sie einen der folgenden Schritte aus:

   * Navigieren Sie zu `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` und wenden Sie das entsprechende Profil an und tippen oder klicken Sie auf **[!UICONTROL Speichern]**.

      ![chlimage_1-492](assets/chlimage_1-492.png)

   * Navigieren Sie in CRXDE Lite zum folgenden Knoten: `/content/dam/jcr:content`. Fügen Sie die Eigenschaft `metadataProfile:/etc/dam/metadata/dynamicmedia/<name_of_metadata_profile>` hinzu und tippen Sie auf **[!UICONTROL Alle speichern]**.

      ![chlimage_1-493](assets/chlimage_1-493.png)

## Entfernen eines Metadatenprofils aus Ordnern {#removing-a-metadata-profile-from-folders}

Wenn Sie ein Metadatenprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung von Dateien, die in den Ordnern stattgefunden hat, bleibt jedoch intakt.

Sie können ein Metadatenprofil aus einem Ordner im Menü **[!UICONTROL Tools]** entfernen. Wenn Sie sich im Ordner befinden, ist dies über die **[!UICONTROL Eigenschaften]** möglich. In diesem Abschnitt wird beschrieben, wie Sie Metadatenprofile auf beide Arten aus Ordnern entfernen.

### Entfernen von Metadatenprofilen aus Ordnern über die Benutzeroberfläche „Profile“ {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

Gehen Sie wie folgt vor, um über die Benutzeroberfläche &quot;Profile&quot;ein Metadatenprofil aus Ordnern zu entfernen:

1. Tippen Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Tools > Assets > Metadatenprofile]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Tippen **[!UICONTROL Entfernen von Metadatenprofilen aus Ordnern]** und wählen Sie den Ordner oder mehrere Ordner aus, aus denen Sie ein Profil entfernen möchten, und tippen Sie dann auf **[!UICONTROL Fertig]**.

   Sie können bestätigen, dass das Metadatenprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Entfernen von Metadatenprofilen aus Ordnern über &quot;Eigenschaften&quot; {#removing-metadata-profiles-from-folders-via-properties}

1. Tippen Sie auf [!DNL Experience Manager] Logo und Navigation **[!UICONTROL Assets]** und dann in den Ordner, aus dem Sie ein Metadatenprofil entfernen möchten.
1. Tippen Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und tippen Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie die **[!UICONTROL Metadatenprofile]** Registerkarte und wählen Sie **[!UICONTROL Keines]** aus dem Dropdown-Menü. Tippen Sie auf **[!UICONTROL Speichern]**.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.
