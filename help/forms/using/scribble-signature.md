---
title: Verwenden der Scribble-Signatur in HTML5-Formularen
seo-title: Using Scribble Signature in HTML5 forms
description: HTML5-Formulare werden zunehmend auf Touch-Geräten verwendet. Eine gängige Voraussetzung ist die Unterstützung von Signaturen. Die Unterschrift von Dokumenten auf Mobilgeräten wird zu einer anerkannten Methode zur Unterzeichnung von Formularen auf Mobilgeräten.
seo-description: HTML5 forms are increasingly used on touch devices, and one common requirement is to support signatures. Signing documents on mobile devices is becoming an accepted way of signing forms on mobile devices.
uuid: afac2d37-ef0d-428b-aed7-64a00d62792d
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: designer
discoiquuid: abb5513f-c824-4dc2-8617-29ea47684afe
feature: Designer
exl-id: 8b6b151d-2422-4261-9edb-66efe3d33f8b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 25%

---

# Verwenden der Scribble-Signatur in HTML5-Formularen {#using-scribble-signature-in-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

HTML5-Formulare werden zunehmend auf Touch-Geräten verwendet. Eine gängige Voraussetzung ist die Unterstützung von Signaturen. Die Skripterstellung (Schreiben mit einem Stift oder Finger) wird zu einer gängigen Methode, Formulare auf Mobilgeräten zu signieren. HTML5 Forms und Designer bieten jetzt auf dem Formular ein Feld für die Scribble-Signatur. Wenn das Formular im Browser wiedergegeben wird, kann man diese Felder mit einem Stil, einer Maus oder einem Touch kennzeichnen.

## Entwerfen eines Formulars mithilfe des Scribble-Signatur-Felds {#how-to-design-a-form-using-scribble-signature-field}

1. Öffnen Sie ein Formular in Forms Designer.
1. Ziehen das Scribble-Signatur-Feld auf die Seite.

   ![designer_scribble](assets/designer_scribble.png)

   >[!NOTE]
   >
   >Die Abmessungen des in Forms Designer ausgewählten Feldes werden beim Rendern des Feldes berücksichtigt. Die Dimension des wiedergegebenen Signaturfelds wird jedoch auf der Grundlage des Seitenverhältnisses des Felds und nicht anhand der in Forms Designer festgelegten Dimension berechnet.

1. Konfigurieren Sie das Scribble-Signatur-Feld.

   Das Scribble-Signatur -Feld kennzeichnet beim Signieren auf iPad standardmäßig Geolocation-Informationen als obligatorisch (und ist für andere Geräte optional). Dieses Standardverhalten kann außer Kraft gesetzt werden, indem der Wert der Eigenschaft `geoLocMandatoryOnIpad` geändert wird. Diese Eigenschaft wird als Extras im Scribble-Signatur-Feld bereitgestellt. Die Schritte zur Änderung sind:

   1. Wählen Sie im Formular das Scribble-Signatur -Feld aus.
   1. Wählen Sie die Registerkarte **XML-Quelle.**

      >[!NOTE]
      >
      >Um die Registerkarte „XML-Quelle“ zu öffnen, klicken Sie auf **Ansicht** > **XML-Quelle**.

   1. Suchen Sie das Tag `<ui>` im Tag `<field>` und ändern Sie den Quell-Code so, dass er wie folgt aussieht:

      ```xml
      <extras name="x-scribble-add-on">
      <boolean name="geoLocMandatoryOnIpad">0</boolean>
      </extras>
      ```

   1. Wählen Sie die **Designansicht** Registerkarte. Klicken Sie im Bestätigungsfeld auf **Ja**.
   1. Speichern Sie das Formular.

1. Wiedergabe des Formulars in einem unterstützten Geräte-/Desktop-Browser.

## Benutzeroberfläche für Scribble-Signaturen {#interfacing-with-the-scribble-signatures}

### Signing {#signing}

Nachdem dem Formular ein Scribble-Signatur-Feld hinzugefügt und wiedergegeben wurde, wird durch Klicken oder Tippen auf das Feld ein Dialogfeld geöffnet. Der Benutzer kann mithilfe einer Maus, eines Fingers oder eines Stylus eine Signatur in dem gepunkteten Bereich, der durch ein gepunktetes Rechteck gekennzeichnet ist, kritzeln.

![geolocation](assets/geolocation.png)

**A.** Pinsel **B.** Radiergummi **C.** Geolocation **D.** Geografische Informationen

### Geotagging {#geo-tagging}

Wenn Sie beim Erstellen des Scribble auf das Geolocation-Symbol klicken, werden geografische Informationen und die Uhrzeit in das Feld eingebettet.

>[!NOTE]
In iPad ist standardmäßig das Einbetten von Geolocation-Informationen obligatorisch.

In der iPad wird das Geolocation-Symbol nicht standardmäßig angezeigt und die Geolocation-Informationen werden automatisch eingebettet, wenn Sie auf **OK**.

Diese Einstellung kann auf iPads geändert werden, indem in den init-Parametern des Feldes der Wert des Parameters `geoLocManadatoryOnIpad` auf `0` gesetzt wird.

* Wenn Geolocation-Informationen erforderlich sind, wird dem Benutzer ein reduzierter Zeichenbereich angezeigt. Geolocation-Text wird hinzugefügt, wenn der Benutzer auf **OK** auf dem anderen Bereich.
* In anderen Fällen wird dem Benutzer ein vollständiger Bereich angezeigt, in dem er zu verwenden ist. Wenn der Benutzer Geolocation-Informationen einbetten möchte, wird die Größe dieses Bereichs so geändert, dass der Geolocation-Text berücksichtigt wird.

### Signatur löschen {#clearing-a-signature}

Bei dieser Funktion kann ein Benutzer auf das Symbol **Radiergummi** klicken, um den Inhalt des Felds zu löschen und von vorne zu beginnen. Wenn Geolocation-Informationen hinzugefügt wurden, werden sie ebenfalls gelöscht.

### Speichern einer Signatur {#saving-a-signature}

Klicken Sie auf **OK** speichert das Scribble als Bild im Feld. Das Bild und die Werte können zur weiteren Verarbeitung an den Server gesendet werden. Nachdem ein Benutzer geklickt hat **OK**, ist das Scribble-Feld gesperrt. Die Signatur kann nicht mit dem Scribble-Widget erneut bearbeitet werden.

Durch Tippen oder Klicken auf das Scribble-Feld wird das Dialogfeld im schreibgeschützten Modus geöffnet.

![3](assets/3.png)

### Auswählen der Schriftgröße {#selecting-pen-size}

Klicken Sie auf das Symbol **Pinsel**, um eine Liste der verfügbaren Stiftgrößen anzuzeigen. Klicken oder tippen Sie auf eine Schriftgröße, um den entsprechenden Stift zu verwenden.

### Löschen von Signaturen aus dem Formular {#delete-signatures-from-the-form}

So löschen Sie die Signaturen aus dem Formular:

* (Mobilgeräte) Drücken Sie lange auf das Signaturfeld und tippen Sie im Bestätigungsdialogfeld auf **Ja**.
* (Desktop) Bewegen Sie den Mauszeiger über das Signaturfeld und klicken Sie auf das **Abbrechen** und klicken Sie im Bestätigungsdialogfeld auf **Ja**.
