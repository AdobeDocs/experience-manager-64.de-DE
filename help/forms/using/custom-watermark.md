---
title: Wasserzeichen in der PDF-Briefvorschau
seo-title: Wasserzeichen in der PDF-Briefvorschau
description: Erfahren Sie, wie Sie benutzerdefinierte Wasserzeichen in der PDF-Briefvorschau erstellen.
seo-description: Erfahren Sie, wie Sie benutzerdefinierte Wasserzeichen in der PDF-Briefvorschau erstellen.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 58%

---


# Wasserzeichen in der PDF-Briefvorschau {#custom-watermark-in-letter-pdf-preview}

## Übersicht {#overview}

Agent-Benutzer zeigen in der Benutzeroberfläche „Korrespondenz erstellen“ die Korrespondenz in der endgültigen Form an, in der sie zur Nachbearbeitung gesendet wird, z. B. für E-Mails oder zum Drucken.

Um die nicht autorisierte Verwendung dieser Daten zu verhindern, können Unternehmen der PDF-Vorschau ein Wasserzeichen hinzufügen. Das standardmäßige Wasserzeichen ist „VORSCHAU“ und wird über die gesamte PDF hinweg angezeigt.

To enable the watermark in preview PDF, select the **[!UICONTROL Apply Watermark]** During Preview option in **[!UICONTROL Correspondence Management Configurations]** at `https://[server]:[port]/system/console/configMgr`.

![default-watermark](assets/default-watermark.png)

Sie können folgende Schritte verwenden, um den Text und das Erscheinungsbild des Wasserzeichens anzupassen:

## Passen Sie die Benutzeroberfläche „Korrespondenz erstellen“ an {#customizewatermark-}

1. Go to `https://[server]:[port]/[ContextPath]/crx/de` and login as Administrator.
1. In the apps folder, create a folder named **[!UICONTROL previewwatermark]** with path/structure similar to the previewwatermark folder in the libs folder:

   1. Right-click the **previewwatermark **folder at the following path and select **Overlay Node**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:** /libs/fd/cm/configFiles/previewwatermark

      **Überlagerungsort:** /apps/

      **Knotentypen abgleichen:** Überprüft

      >[!NOTE]
      >
      >Nehmen Sie keine Änderungen in der /libs-Verzweigung vor. Alle Änderungen, die Sie vornehmen, gehen möglicherweise verloren, da diese Verzweigung sich ändern kann, wenn Sie:
      >
      >* Ihre Instanz aktualisieren
      >* Ein Hotfix anwenden
      >* Ein Feature Pack installieren


   1. Klicken Sie auf **OK** und dann auf **Alle speichern**. The **[!UICONTROL previewwatermark]** folder is created in the specified path.

1. Copy and paste the ddx file from &quot;/libs/fd/cm/configFiles/previewwatermark&quot; folder to &quot;/apps/fd/cm/configFiles/previewwatermark&quot; folder and click **[!UICONTROL Save All]**.
1. Nehmen Sie in der ddx-Datei unter „/apps/fd/cm/configFiles/previewwatermark/“ die gewünschten Änderungen vor.

   ```
   <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
    <PDF result="output.pdf">
     <PDF source="input.pdf"/>
           <Watermark opacity="15%" rotation="45">
            <StyledText>
                     <p font-family="Georgia" font-size="70pt" color="black" font-weight="bold">
                         PREVIEW
                    </p>
            </StyledText>
           </Watermark>
    </PDF>
   </DDX>
   ```

   For information on customizing the watermark appearance, text, and alignment, see Adding and removing watermarks and backgrounds in the [Assembler Service and DDX Reference](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf) document.

   >[!NOTE]
   >
   >In der ddx-Datei sollten die Verweise auf das Ergebnis und die Quelle für output.pdf und input.pdf unverändert bleiben. Der Name der ddx-Datei darf nicht geändert werden.

1. Klicken Sie auf **Alle speichern**.

