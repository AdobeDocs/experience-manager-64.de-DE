---
title: Herunterladen digitaler Assets aus [!DNL Adobe Experience Manager].
description: Erfahren Sie, wie Sie Assets aus  [!DNL Adobe Experience Manager]  herunterladen und die Download-Funktion aktivieren oder deaktivieren.
contentOwner: AG
feature: Asset Management,Asset Distribution
role: User
exl-id: bfe4d597-1080-4de5-a100-73a5175863d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 75%

---

# Herunterladen von Assets aus [!DNL Adobe Experience Manager] {#download-assets-from-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können Assets einschließlich der statischen und dynamischen Ausgabedarstellungen herunterladen. Sie haben auch die Möglichkeit, eine E-Mail mit Links zu Assets direkt von [!DNL Adobe Experience Manager Assets] aus zu senden. Heruntergeladene Assets werden in einer ZIP-Datei gebündelt. Die komprimierte ZIP-Datei hat für den Exportauftrag eine maximale Dateigröße von 1 GB. Es sind maximal 500 Assets pro Exportauftrag zulässig.

>[!NOTE]
>
>Empfänger von E-Mails müssen Mitglieder der Gruppe `dam-users` sein, um auf den ZIP-Download-Link in der E-Mail zugreifen zu können. Um die Assets herunterladen zu können, müssen diese Mitglieder über die Berechtigung zum Starten von Workflows verfügen, die das Herunterladen von Assets auslösen.

Die Asset-Typen „Bildset“, „Rotationsset“ „Set für gemischte Medien“ und „Karussellset“ können nicht heruntergeladen werden.

Gehen Sie wie folgt vor, um Assets herunterzuladen:

1. Tippen Sie in der linken oberen Ecke von AEM auf die [!DNL Experience Manager] -Logo und tippen Sie dann in der linken Leiste auf **[!UICONTROL Navigation]**.
1. Tippen Sie auf der Navigationsseite auf **[!UICONTROL Assets]** > **[!UICONTROL Dateien.]**
1. Navigieren Sie zu einem Ordner mit den Assets, die Sie herunterladen möchten.
1. Wählen Sie den Ordner oder ein oder mehrere Assets im Ordner aus.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Herunterladen.]**

   ![Verfügbare Optionen beim Herunterladen von Assets aus AEM Assets](/help/assets/assets/asset_download_dialog.png)

   *Abbildung: Optionen des Dialogfelds „Herunterladen“.*

1. Wählen Sie im Dialogfeld „Herunterladen“ die gewünschten Download-Optionen aus.

   | Export- oder Download-Optionen | Beschreibung |
   |---|---|
   | **[!UICONTROL Separaten Ordner für jedes Asset erstellen]** | Wählen Sie diese Option, um jedes Asset, das Sie herunterladen – einschließlich der Assets in Unterordnern, die unter dem übergeordneten Ordner des Assets verschachtelt sind – in einen Ordner auf Ihrem lokalen Computer aufzunehmen. Wenn diese Option nicht ausgewählt ist, wird standardmäßig die Ordnerhierarchie ignoriert und alle Assets werden in einen Ordner auf Ihrem lokalen Computer heruntergeladen. |
   | **[!UICONTROL E-Mail]** | Eine E-Mail-Benachrichtigung wird an den Benutzer gesendet. Standardmäßige E-Mail-Vorlagen finden Sie in folgenden Ordnern:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> Vorlagen, die Sie während der Implementierung anpassen, stehen an den folgenden Speicherorten zur Verfügung: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>Sie können mandantenspezifische benutzerdefinierte Vorlagen in folgenden Ordnern speichern:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Assets]** | Wählen Sie diese Option, um das Asset in seiner Originalform ohne Ausgabedarstellungen herunterzuladen.<br>Die Option „Teilassets“ ist verfügbar, wenn das Asset Teil-Asset enthält. |
   | **[!UICONTROL Ausgabeformate]** | Eine Ausgabedarstellung ist die binäre Darstellung eines Assets. Assets verfügen über eine primäre Darstellung - die der hochgeladenen Datei. Sie können außerdem mehrere Darstellungen aufweisen. <br> Mit dieser Option können Sie die Ausgabedarstellungen auswählen, die heruntergeladen werden sollen. Die verfügbaren Ausgabedarstellungen hängen vom ausgewählten Asset ab. Die Option ist verfügbar, wenn das Asset über Ausgabedarstellungen verfügt. |
   | **[!UICONTROL Dynamische Ausgabeformate]** | Wählen Sie diese Option, um eine Reihe von alternativen Ausgabedarstellungen in Echtzeit zu erstellen. Wenn Sie diese Option auswählen, wählen Sie auch die Ausgabeformate aus, die Sie dynamisch erstellen möchten, indem Sie aus dem [Bildvorgabe](image-presets.md) Liste. <br>Außerdem können Sie Größe und Einheit, Format, Farbraum, Auflösung und beliebige Bild-Modifikatoren auswählen (um das Bild z. B. umzukehren). Die Option ist nur verfügbar, wenn Sie [!DNL Dynamic Media] aktiviert haben. |

1. Tippen Sie im Dialogfeld auf **[!UICONTROL Herunterladen.]**.

Wenn Sie einen Ordner zum Herunterladen auswählen, wird die vollständige Asset-Hierarchie unter dem Ordner heruntergeladen. Um jedes heruntergeladene Asset (einschließlich Assets in untergeordneten Ordnern, die unter dem übergeordneten Ordner verschachtelt sind) in einen einzelnen Ordner einzuschließen, wählen Sie **[!UICONTROL Separaten Ordner für jedes Asset erstellen]**.

## Aktivieren des Asset-Download-Servlets {#enable-asset-download-servlet}

Das Standard-Servlet in [!DNL Experience Manager] ermöglicht es authentifizierten Benutzern, beliebig große, gleichzeitige Download-Anforderungen für die Erstellung von ZIP-Dateien mit für sie sichtbaren Assets zu stellen, die den Server und das Netzwerk überlasten können. Um potenzielle DoS-Risiken zu reduzieren, die durch diese Funktion verursacht werden, ist die `AssetDownloadServlet`-OSGi-Komponente für Veröffentlichungsinstanzen standardmäßig deaktiviert.

Um das Herunterladen von Assets aus Ihrem DAM zu ermöglichen (z. B. bei Verwendung von Asset Share Commons oder einer anderen portalähnlichen Implementierung), aktivieren Sie das Servlet manuell über eine OSGi-Konfiguration. Adobe empfiehlt, die zulässige Download-Größe so gering wie möglich zu halten, ohne dass sich dies auf die täglichen Download-Anforderungen auswirkt. Ein hoher Wert kann sich auf die Leistung auswirken.

1. Erstellen Sie einen Ordner mit einer Namenskonvention, die den Veröffentlichungs-Ausführungsmodus (`config.publish`) adressiert: `/apps/<your-app-name>/config.publish`. Um Konfigurationseigenschaften für einen Laufmodus zu definieren, siehe [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).
1. Erstellen Sie im Konfigurationsordner eine Datei des Typs `nt:file` mit dem Namen `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Füllen Sie `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` wie folgt. Legt eine maximale Größe (in Byte) für den Download als Wert von `asset.download.prezip.maxcontentsize` fest. Im folgenden Beispiel wird die maximale Größe des ZIP-Downloads auf maximal 100 KB konfiguriert.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Deaktivieren des Asset-Download-Servlets {#disable-asset-download-servlet}

Das `Asset Download Servlet` kann in einer [!DNL Experience Manager]-Veröffentlichungsinstanz deaktiviert werden, indem die Dispatcher-Konfiguration so aktualisiert wird, dass sie alle Asset-Download-Anfragen blockiert. Das Servlet kann auch manuell direkt über die OSGi-Konsole deaktiviert werden.

1. Um Asset-Download-Anfragen über eine Dispatcher-Konfiguration zu blockieren, bearbeiten Sie die `dispatcher.any`-Konfiguration und fügen Sie dem [Filterabschnitt](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-access-to-content-filter) eine Regel hinzu. `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. Um die OSGi-Komponente in einer Veröffentlichungsinstanz zu deaktivieren, rufen Sie die OSGi-Konsole unter `http://[aem_server]:[port]/system/console/components` auf. Suchen Sie `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` und klicken Sie auf **[!UICONTROL Deaktivieren]**.

>[!MORELIKETHIS]
>
>* [Herunterladen von DRM-geschützten Assets](drm.md).
>* [Herunterladen von Assets mit dem Experience Manager-Desktop-Programm auf einem Windows- oder Mac-Desktop](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app.html).
>* [Herunterladen von Assets mit Adobe Assets Link aus den unterstützten Adobe Creative Cloud-Programmen](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html).

