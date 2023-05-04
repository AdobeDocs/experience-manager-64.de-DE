---
title: Benutzerdefiniertes Wasserzeichen in der PDF-Briefvorschau
seo-title: Custom watermark in letter PDF preview
description: Erfahren Sie, wie Sie in der Briefvorschau ein benutzerdefiniertes Wasserzeichen erstellen.
seo-description: Learn how to create custom watermark in letter PDF preview.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
feature: Correspondence Management
exl-id: 8aeabd95-948d-4a54-b593-1eda8ddd731b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 47%

---

# Benutzerdefiniertes Wasserzeichen in der PDF-Briefvorschau {#custom-watermark-in-letter-pdf-preview}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Agent-Benutzer zeigen in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;die Korrespondenz in der endgültigen Form an, in der sie zur Nachbearbeitung gesendet wird, z. B. zum E-Mail-Versand oder zum Drucken.

Um die unbefugte Verwendung dieser Daten zu verhindern, können Unternehmen ein Wasserzeichen auf der Vorschau-PDF festlegen. Das standardmäßige Wasserzeichen ist „VORSCHAU“ und wird über die gesamte PDF hinweg angezeigt.

Um das Wasserzeichen in der Vorschau-PDF zu aktivieren, wählen Sie die **[!UICONTROL Wasserzeichen anwenden]** Option &quot;Während der Vorschau&quot;in **[!UICONTROL Correspondence Management-Konfigurationen]** at `https://[server]:[port]/system/console/configMgr`.

![default-watermark](assets/default-watermark.png)

Sie können die folgenden Schritte verwenden, um den Text und das Erscheinungsbild des Wasserzeichens anzupassen:

## Anpassen des Wasserzeichens in der PDF-Vorschau in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot; {#customizewatermark-}

1. Wechseln Sie zu `https://[server]:[port]/[ContextPath]/crx/de` und melden Sie sich als „Administrator“ an.
1. Erstellen Sie im Anwendungsordner einen Ordner mit dem Namen **[!UICONTROL previewwatermark]**, dessen Pfad/Struktur der des Ordners „previewwatermark“ im Ordner „libs“ entspricht:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner &quot;previewwatermark&quot;unter dem folgenden Pfad und wählen Sie **Überlagerungsknoten**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:** /libs/fd/cm/configFiles/previewwatermark

      **Überlagerungsspeicherort:** /apps/

      **Knotentypen abgleichen:** Überprüft

      >[!NOTE]
      >
      >Ändern Sie die /libs-Verzweigung nicht. Alle Änderungen, die Sie vornehmen, können verloren gehen, da sich diese Verzweigung ändern kann, wenn Sie:
      >
      >* Aktualisierung Ihrer Instanz
      >* Anwenden eines Hotfixes
      >* Installieren eines Feature Packs


   1. Klicken Sie auf **OK** und dann auf **Alle speichern**. Der Ordner **[!UICONTROL previewwatermark]** wird unter dem angegebenen Pfad erstellt.

1. Kopieren Sie die ddx-Datei aus dem Ordner „/libs/fd/cm/configFiles/previewwatermark“ in den Ordner „/apps/fd/cm/configFiles/previewwatermark“ und klicken Sie auf **[!UICONTROL Alle speichern]**.
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

   Informationen zum Anpassen des Erscheinungsbildes, des Textes und der Ausrichtung des Wasserzeichens finden Sie unter Hinzufügen und Entfernen von Wasserzeichen und Hintergründen im Dokument [Assembler Service und DDX-Referenz](https://help.adobe.com/de_DE/livecycle/11.0/ddxRef.pdf).

   >[!NOTE]
   >
   >In der ddx-Datei sollten die Verweise auf &quot;result&quot;und &quot;source&quot;in output.pdf und input.pdf unverändert bleiben. Der Name der Datei ddx sollte ebenfalls nicht geändert werden.

1. Klicken Sie auf **Alle speichern**.
