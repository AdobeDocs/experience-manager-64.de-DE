---
title: Hinzufügen von Anhängen
seo-title: Hinzufügen von Anhängen
description: Fotos und Notizen als Anmerkungen zu Aufgaben in der AEM Forms-App hinzufügen
seo-description: Fotos und Notizen als Anmerkungen zu Aufgaben in der AEM Forms-App hinzufügen
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
translation-type: tm+mt
source-git-commit: 0ce79686522da4fb3d017068b623c76f81c6b23a

---


# Hinzufügen von Anhängen {#adding-attachments}

## Adding attachments in forms synced with AEM Forms Workflow server (AEM Forms on JEE) {#adding-annotations}

Mit der AEM Forms-App können Sie Bilder, Notizen und Kommentare zu Ihrem Formular hinzufügen, das mit dem AEM Forms JEE-Server synchronisiert wird. Wenn das Formular von einem AEM Forms Workflow-Server geladen wird, werden die Anlagen zu dem Formular hinzugefügt. You can tap the attachment button ![attachments-app](assets/attachments-app.png) to see all the attachments in a form together. Die rote Benachrichtigung gibt die Anzahl von Anlagen im Formular an. Wenn keine Anlagen im Formular vorhanden sind, wird die rote Benachrichtigungsschaltfläche nicht angezeigt. If there are no attachments in the form, when you tap the attachments button ![attch](assets/attch.png), you get options to attach photos or scribbles.

Ihre Optionen sind:

* **[!UICONTROL Galerie]**: Hiermit können Sie ein Bild aus den auf dem Gerät gespeicherten hinzufügen.

* **[!UICONTROL Kamera]**: Hiermit können Sie ein Foto aufnehmen und es zum Formular hinzufügen. 

* **[!UICONTROL Hinweise]**: Hiermit können Sie eine Notiz oder Textanmerkung hinzufügen. Use ![scribble](assets/scribble.png) to add a scribble, and ![keyboard](assets/keyboard.png) to add a text note.

>[!NOTE]
>
>Von einem Benutzer hinzugefügte Anlagen sind für andere Benutzer der AEM Forms-App sichtbar. Andere Benutzer können die Anlagen nicht löschen, die von einem Benutzer hinzugefügt werden.


### Der Bildschirm „Anlagen“{#the-attachments-screen}

To see all the attachments in a place, tap ![attachments-app](assets/attachments-app.png). Hier können Sie Anlagen hinzufügen, umbenennen und löschen.

![Alle Anlagen an einem Ort](assets/attachments-screen.png)

Verwenden Sie die Schaltfläche mit dem **Pluszeichen** (+) im Bildschirm „Anlagen“, um ein weiteres Bild, eine weitere Notiz oder einen weiteren Text anzufügen.

### Hinzufügen eines Fotos {#adding-a-photograph}

Sie können die Kamera Ihres Mobilgeräts oder auf Ihrem Gerät gespeicherte Bilder verwenden, um ein Bild im Formular anzuhängen.

1. Tap the attachment button ![attch](assets/attch.png) at the bottom of the window.
1. Tippen Sie auf **[!UICONTROL Galerie]** oder **[!UICONTROL Kamera]** im Popup-Menü, das angezeigt wird.
1. Führen Sie je nach ausgewählter Option einen der folgenden Schritte aus:

   1. Wenn Sie **[!UICONTROL Kamera]** auswählen:

      Nehmen Sie ein Foto auf. Then tap the **[!UICONTROL Use]** ![use-pic](assets/use-pic.png) button.

      Or tap the **[!UICONTROL Retake]** ![retake](assets/retake.png) button to retake the photograph.

   1. Wenn Sie **[!UICONTROL Galerie]** auswählen:

      Das Dialogfeld für die Bildauswahl wird eingeblendet. In der Bildauswahl Ihres Geräts tippen Sie auf das Bild, das Sie anfügen möchten.

### Hinzufügen einer Notiz {#adding-a-note}

Mit der Option **Notizen** können Sie dem Formular Freihand-Scribbles oder Textanlagen hinzufügen.

1. Tap the attachment button ![attch](assets/attch.png) at the bottom of the window.
1. Tippen Sie auf **[!UICONTROL Notizen]** im Popup-Menü, das angezeigt wird.
1. Dadurch wird die Benutzeroberfläche „Notizen“ gestartet, auf der Sie ein Freihand-Scribble erfassen können.

   ![Scribble-Benutzeroberfläche](assets/scribble-ui.png)
   **Abbildung:** *Scribble*

   Sie können die folgenden Optionen in der Scribble-Benutzeroberfläche verwenden:

   * **[!UICONTROL Clear]**: Löscht den gesamten Bildschirm.
   * **[!UICONTROL Fertig]**: Fügt das aktuelle Scribble hinzu.
   * **[!UICONTROL Abbrechen]**: Verwirft das aktuelle Scribble und beendet die Scribble-Benutzeroberfläche.
   * ![Tastatur](assets/keyboard.png): Löscht das Scribble und ermöglicht das Hinzufügen einer Textanmerkung.
   ![Tastatur in AEM Forms-App-Scribble](assets/keyboard-inapp.png)

## Attachments in forms synced with the AEM Forms servers without AEM Forms Workflow (AEM Forms on OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Anlagen für Mobile Forms, die mit AEM Forms OSGi-Servern synchronisiert werden, funktionieren ähnlich wie die AEM Forms JEE-Server.

Anlagen auf Formularebene werden für adaptive Formulare, die in der AEM Forms-App von einem AEM Forms OSGi-Server geladen werden, nicht unterstützt. Um Bilder oder Textanmerkungen hinzuzufügen, aktivieren Sie Anlagen auf Feldebene im Formular, wenn Sie es erstellen. Ziehen Sie die Dateianlagenkomponente aus dem Komponenten-Browser in das Feld.

Bei adaptiven Formularen können Sie die angehängten Dateien im Datensatzdokument (DoR) anzeigen. Siehe [Generierung eines Datensatzdokuments für adaptive Nicht-XFA-Formulare](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
