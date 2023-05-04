---
title: Hinzufügen von Anhängen
seo-title: Adding attachments
description: Fotos und Notizen als Anmerkungen zu Ihrer Aufgabe in der AEM Forms-App hinzufügen
seo-description: Add photographs and scribble notes as annotations to your task in the AEM Forms app
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
exl-id: ad1cc63a-cf99-456b-8b83-0605fb3ac6ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 55%

---

# Hinzufügen von Anhängen {#adding-attachments}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Hinzufügen von Anhängen in Formularen, die mit AEM Forms Workflow-Server (AEM Forms on JEE) synchronisiert werden {#adding-annotations}

Mit der AEM Forms-App können Sie Bilder, Notizen und Textanmerkungen an das mit dem AEM Forms JEE-Server synchronisierte Formular anhängen. Wenn Ihr Formular von einem AEM Forms Workflow-Server geladen wird, werden Ihre Anhänge zum Formular hinzugefügt. Sie können auf die Schaltfläche für Anhänge ![attachments-app](assets/attachments-app.png) tippen, um alle Anhänge in einem Formular gemeinsam anzuzeigen. Die rote Benachrichtigung gibt die Anzahl von Anhänge im Formular an. Wenn keine Anhänge im Formular vorhanden sind, wird die rote Benachrichtigungsschaltfläche nicht angezeigt. Falls keine Anhänge im Formular vorhanden sind, erhalten Sie Optionen zum Anhängen von Fotos oder Notizen, wenn Sie auf die Schaltfläche für Anhänge ![attch](assets/attch.png) tippen.

Ihre Optionen sind:

* **[!UICONTROL Galerie]**: Hiermit können Sie ein Bild aus den auf dem Gerät gespeicherten Bildern hinzufügen.

* **[!UICONTROL Kamera]**: Hiermit können Sie ein Foto aufnehmen und es zum Formular hinzufügen. 

* **[!UICONTROL Hinweise]**: Hiermit können Sie eine Notiz oder Textanmerkung hinzufügen. Verwenden Sie ![Freihand](assets/scribble.png), um eine Notiz hinzuzufügen und ![Tastatur](assets/keyboard.png), um einen Textkommentar hinzuzufügen.

>[!NOTE]
>
>Die von einem Benutzer hinzugefügten Anhänge sind für andere Benutzer des Programms AEM Forms sichtbar. Die von einem Benutzer hinzugefügten Bilder können von anderen Benutzern können nicht gelöscht werden.

### Der Bildschirm „Anhänge“ {#the-attachments-screen}

Um alle Anhänge zusammen an einem Ort zu sehen, tippen Sie auf ![attachments-app](assets/attachments-app.png). Hier können Sie Anhänge hinzufügen, umbenennen und löschen.

![Alle Anhänge an einem Ort](assets/attachments-screen.png)

Verwenden Sie die Schaltfläche mit dem **Pluszeichen** (+) im Bildschirm „Anhänge“, um ein weiteres Bild, eine weitere Notiz oder einen weiteren Text anzufügen.

### Hinzufügen eines Fotos {#adding-a-photograph}

Sie können die Kamera Ihres Mobilgeräts oder gespeicherte Bilder auf Ihrem Gerät verwenden, um ein Bild im Formular anzuhängen.

1. Tippen Sie am unteren Fensterrand auf die Schaltfläche für Anhänge ![attch](assets/attch.png).
1. Tippen Sie im Popup-Menü, das angezeigt wird, auf **[!UICONTROL Galerie]** oder **[!UICONTROL Kamera]**.
1. Führen Sie je nach ausgewählter Option Folgendes aus:

   1. Wenn Sie **[!UICONTROL Kamera]**.

      Machen Sie ein Foto. Tippen Sie anschließend auf die Schaltfläche **[!UICONTROL Verwenden]** ![use-pic](assets/use-pic.png).

      Tippen Sie alternativ auf die Schaltfläche **[!UICONTROL Erneut aufnehmen]** ![retake](assets/retake.png), um erneut ein Foto aufzunehmen.

   1. Wenn Sie **[!UICONTROL Galerie]**.

      Der Bildbrowser des Geräts wird angezeigt. Tippen Sie in der Bildauswahl Ihres Geräts auf das Bild, das Sie anhängen möchten.

### Hinzufügen einer Notiz {#adding-a-note}

Mit der Option **Notizen** können Sie dem Formular Freihandskizzen oder Textanhänge hinzufügen.

1. Tippen Sie am unteren Fensterrand auf die Schaltfläche für Anhänge ![attch](assets/attch.png).
1. Tippen **[!UICONTROL Hinweise]** im angezeigten Popup-Fenster.
1. Erfassen Sie in der Benutzeroberfläche &quot;Notizen&quot;, die gestartet wird, ein Freihand-Scribble.

   ![Freihand-Benutzeroberfläche](assets/scribble-ui.png)
   **Abbildung:** *Scribble*

   Sie können die folgenden Optionen in der Scribble-Benutzeroberfläche verwenden:

   * **[!UICONTROL Löschen]**: Löscht den Bildschirm.
   * **[!UICONTROL Fertig]**: Hängt das aktuelle Scribble an.
   * **[!UICONTROL Abbrechen]**: Verwirft das aktuelle Scribble und beendet die Scribble-Benutzeroberfläche.
   * ![Tastatur](assets/keyboard.png): Löscht die Skizze und ermöglicht die Eingabe einer Textnotiz.

   ![Tastatur im AEM Forms-Programm Scribble](assets/keyboard-inapp.png)

## Anlagen in Formularen, die mit den AEM Forms-Servern ohne AEM Forms Workflow (AEM Forms unter OSGi) synchronisiert werden {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Anlagen für mobile Formulare, die mit AEM Forms OSGi-Servern synchronisiert werden, funktionieren ähnlich wie die AEM Forms JEE-Server.

Anlagen auf Formularebene werden nicht für adaptive Formulare unterstützt, die in der App von einem AEM Forms OSGi-Server geladen werden. Um Bilder oder Textanmerkungen anzuhängen, aktivieren Sie Anlagen auf Feldebene im Formular, wenn Sie es erstellen. Ziehen Sie die Dateianlagenkomponente aus dem Komponenten-Browser in das Feld.

Bei adaptiven Formularen können Sie die angehängten Dateien im Datensatzdokument (DoR) anzeigen. Weitere Informationen finden Sie unter [Generierung eines Datensatzdokuments für adaptive Nicht-XFA-Formulare](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
