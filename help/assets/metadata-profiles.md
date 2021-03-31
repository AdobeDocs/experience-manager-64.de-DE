---
title: Verwenden von Metadaten-Profilen zum Anwenden von Standardmetadaten auf alle Assets in einem Ordner
description: Informieren Sie sich über Metadatenprofile für Assets. Erfahren Sie, wie Sie Metadatenprofile erstellen und auf Ordner-Assets anwenden können.
contentOwner: AG
feature: 'Metadaten  '
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 65%

---


# Metadatenprofile {#metadata-profiles}

Mit einem Metadaten-Profil können Sie Standardmetadaten auf Assets in einem Ordner anwenden. Erstellen Sie ein Metadaten-Profil und wenden Sie es auf einen Ordner an. Alle Assets, die Sie anschließend in den Ordner hochladen, übernehmen die Standardmetadaten, die Sie im Metadaten-Profil konfiguriert haben.

## Hinzufügen eines Metadatenprofils {#adding-a-metadata-profile}

1. Tippen Sie auf oder klicken Sie auf das AEM, navigieren Sie zu **[!UICONTROL Tools > Assets > Metadata Profils]** und tippen Sie dann auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Titel für das Metadatenprofil ein, etwa Beispielmetadaten, und klicken Sie auf **[!UICONTROL Senden]**. Das **[!UICONTROL Formular bearbeiten]** für das Metadaten-Profil wird angezeigt.

   ![chlimage_1-480](assets/chlimage_1-480.png)

1. Klicken Sie auf eine Komponente und konfigurieren Sie deren Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Klicken Sie beispielsweise auf die Komponente **[!UICONTROL Beschreibung]** und bearbeiten Sie die zugehörigen Eigenschaften.

   ![chlimage_1-481](assets/chlimage_1-481.png)

   Bearbeiten Sie die folgenden Eigenschaften für die Komponente **[!UICONTROL Beschreibung]**:

   * **[!UICONTROL Feldbeschriftung]**: Der Anzeigename der Metadateneigenschaft. Dieser dient lediglich als Referenz für den Benutzer.
   * **[!UICONTROL Zu Eigenschaft]** zuordnen: Der Wert dieser Eigenschaft stellt den relativen Pfad/Namen zu dem Asset-Knoten bereit, in dem er im Repository gespeichert wird. Der Wert sollte immer mit dem Beginn übereinstimmen,  `./` da er angibt, dass sich der Pfad unter der Node des Assets befindet.

   ![chlimage_1-482](assets/chlimage_1-482.png)

   Der Wert, den Sie für **[!UICONTROL Zu Eigenschaft zuordnen]** angeben, wird als Eigenschaft unter dem Metadatenknoten des Assets gespeichert. Beispiel: Wenn Sie `/jcr:content/metadata/dc:desc` als Name von **[!UICONTROL Zu Eigenschaft zuordnen]** angeben, wird der Wert `dc:desc` von AEM Assets im Metadatenknoten des Assets gespeichert.

   * **[!UICONTROL Standardwert]**: Mit dieser Eigenschaft können Sie einen Standardwert für die Metadatenkomponente hinzufügen. Wenn Sie beispielsweise „Meine Beschreibung“ angeben, wird dieser Wert der Eigenschaft `dc:desc` im Metadatenknoten des Assets zugewiesen.

   ![chlimage_1-483](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >Fügen Sie einer neuen Metadateneigenschaft einen Standardwert hinzu (der in der nicht bereits vorhanden ist). `/jcr:content/metadata` vorhanden ist) einen Standardwert hinzufügen, werden die Eigenschaft und deren Wert nicht standardmäßig auf der Eigenschaftsseite des Assets angezeigt. **** Um die neue Eigenschaft auf der Seite [!UICONTROL Properties] des Assets Ansicht, ändern Sie das entsprechende Schema-Formular.

1. (Optional) Hinzufügen weitere Komponenten auf der Registerkarte **[!UICONTROL Formular bearbeiten]** aus der Registerkarte **[!UICONTROL Formular erstellen]** und konfigurieren Sie ihre Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Die folgenden Eigenschaften sind auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbar:

| Komponente | Eigenschaften |
|---|---|
| [!UICONTROL Bereichs-Kopfzeile] | Feldbeschriftung, <br> Beschreibung |
| [!UICONTROL Einzelzeilentext] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Mehrwerttext] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Zahl] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Datum] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Standard-Tags] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert, <br> Beschreibung |

![chlimage_1-484](assets/chlimage_1-484.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**. Das Metadaten-Profil wird der Liste der Profil auf der Seite **[!UICONTROL Metadaten-Profil]** hinzugefügt.

   ![chlimage_1-485](assets/chlimage_1-485.png)

## Kopieren eines Metadatenprofils {#copying-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadaten-Profil]** ein Profil aus, um eine Kopie davon zu erstellen.

   ![chlimage_1-486](assets/chlimage_1-486.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Kopieren]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Metadaten-Profil kopieren]** einen Titel für die neue Kopie des Profils ein.
1. Klicken Sie auf **[!UICONTROL Kopieren]**. Eine Kopie des Profils wird in der Liste der Profil auf der Seite **[!UICONTROL Metadaten-Profil]** angezeigt.

   ![chlimage_1-487](assets/chlimage_1-487.png)

## Löschen eines Metadatenprofils {#deleting-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das zu löschende Profil aus.

   ![chlimage_1-488](assets/chlimage_1-488.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Metadaten-Profil löschen]**.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Löschen]**, um den Löschvorgang zu bestätigen. Das Metadaten-Profil wird aus der Liste gelöscht.

## Anwenden eines Metadatenprofils auf Ordner {#applying-a-metadata-profile-to-folders}

Wenn Sie ein Metadatenprofil zu einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Demzufolge können Sie einem Ordner nur ein Metadatenprofil zuweisen. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Metadatenprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen wurde, werden in der Benutzeroberfläche durch den Namen des Profils angegeben, der im Kartennamen angezeigt wird.

![chlimage_1-489](assets/chlimage_1-489.png)

Sie können Metadatenprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

### Anwenden von Metadatenprofilen auf bestimmte Ordner {#applying-metadata-profiles-to-specific-folders}

Sie können ein Metadatenprofil über das Menü **[!UICONTROL Werkzeuge]** oder, falls Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** auf einen Ordner anwenden. In diesem Abschnitt wird beschrieben, wie Sie Metadatenprofile auf beide Arten auf Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Anwenden von Metadatenprofilen auf Ordner über die Benutzeroberfläche „Profile“ {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools > Assets > Videoprofile]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.

   ![chlimage_1-490](assets/chlimage_1-490.png)

1. Tippen Sie auf **[!UICONTROL Metadatenprofil auf Ordner anwenden]** und wählen Sie mindestens einen Ordner aus, den Sie verwenden möchten, um neu hochgeladene Assets zu empfangen. Tippen Sie anschließend auf **[!UICONTROL Fertig]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Anwenden von Metadatenprofilen auf Ordner aus „Eigenschaften“ {#applying-metadata-profiles-to-folders-from-properties}

1. Tippen Sie auf der linken Leiste auf **[!UICONTROL Assets]** und navigieren Sie dann zu dem Ordner, auf den Sie ein Metadatenprofil anwenden möchten.
1. Tippen Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und tippen Sie anschließend auf **[!UICONTROL Eigenschaften]**.

1. Wählen Sie die Registerkarte **[!UICONTROL Metadatenprofile]** aus. Wählen Sie anschließend das Profil aus dem Dropdownmenü aus und klicken Sie auf **[!UICONTROL Speichern]**.

   ![chlimage_1-491](assets/chlimage_1-491.png)

   Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

### Globales Anwenden eines Metadatenprofils {#applying-a-metadata-profile-globally}

Profile können nicht nur auf einzelne Ordner, sondern auch global angewendet werden. Dann wird allen Inhalten, die Sie in AEM Assets in beliebigen Ordnern hochladen, das ausgewählte Profil zugeordnet. Gehen Sie wie folgt vor, um ein Metadaten-Profil global anzuwenden:

1. Führen Sie einen der folgenden Schritte aus:

   * Navigieren Sie zu `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` und wenden Sie das entsprechende Profil an. Tippen oder klicken Sie auf **[!UICONTROL Speichern]**.

      ![chlimage_1-492](assets/chlimage_1-492.png)

   * Navigieren Sie in CRXDE Lite zum folgenden Knoten: `/content/dam/jcr:content`. Fügen Sie die Eigenschaft `metadataProfile:/etc/dam/metadata/dynamicmedia/<name_of_metadata_profile>` hinzu und tippen Sie auf **[!UICONTROL Alle speichern]**.

      ![chlimage_1-493](assets/chlimage_1-493.png)

## Entfernen eines Metadaten-Profils aus Ordnern {#removing-a-metadata-profile-from-folders}

Wenn Sie ein Metadatenprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, verbleibt jedoch intakt.

Sie können ein Metadatenprofil aus einem Ordner im Menü **[!UICONTROL Tools]** entfernen. Wenn Sie sich im Ordner befinden, ist dies über die **[!UICONTROL Eigenschaften]** möglich. In diesem Abschnitt wird beschrieben, wie Sie Metadatenprofile auf beide Arten aus Ordnern entfernen.

### Entfernen von Metadaten-Profilen aus Ordnern über die Profils-Benutzeroberfläche {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

Gehen Sie wie folgt vor, um ein Metadaten-Profil über die Benutzeroberfläche von Profilen aus Ordnern zu entfernen:

1. Tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools > Assets > Videoprofile]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Tippen Sie auf **[!UICONTROL Metadaten-Profil aus Ordner(n)]** entfernen und wählen Sie den Ordner bzw. mehrere Ordner aus, aus dem bzw. denen Sie ein Profil entfernen möchten. Tippen Sie anschließend auf **[!UICONTROL Fertig]**.

   Sie können bestätigen, dass das Metadatenprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Entfernen von Metadaten-Profilen aus Ordnern mithilfe von Eigenschaften {#removing-metadata-profiles-from-folders-via-properties}

1. Tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Assets]** und dann in den Ordner, aus dem Sie ein Metadatenprofil entfernen möchten.
1. Tippen Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und tippen Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Metadaten-Profil]** und dann **[!UICONTROL Keine]** aus dem Dropdownmenü. Tippen Sie auf **[!UICONTROL Speichern]**.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.
