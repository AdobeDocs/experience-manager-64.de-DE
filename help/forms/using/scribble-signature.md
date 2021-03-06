---
title: Verwenden der Scribble-Signatur in HTML5-Formularen
seo-title: Using Scribble Signature in HTML5 forms
description: 'HTML5-Formulare werden zunehmend auf Touch-Geräten verwendet. Sie sind eine allgemeine Voraussetzung zur Unterstützung von Signaturen. Das Unterzeichnen von Dokumenten auf mobilen Geräten ist eine immer gängigere Form der Unterzeichnung von Formularen. '
seo-description: HTML5 forms are increasingly used on touch devices, and one common requirement is to support signatures. Signing documents on mobile devices is becoming an accepted way of signing forms on mobile devices.
uuid: afac2d37-ef0d-428b-aed7-64a00d62792d
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: designer
discoiquuid: abb5513f-c824-4dc2-8617-29ea47684afe
feature: Designer
exl-id: 8b6b151d-2422-4261-9edb-66efe3d33f8b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 89%

---

# Verwenden der Scribble-Signatur in HTML5-Formularen {#using-scribble-signature-in-html-forms}

HTML5-Formulare werden zunehmend auf Touch-Geräten verwendet. Sie sind eine allgemeine Voraussetzung zur Unterstützung von Signaturen. Die Scribble-Signatur (Schreiben mit dem Eingabestift oder mit dem Finger) ist eine immer gängigere Form der Unterzeichnung von Formularen auf mobilen Geräten. HTML5 Forms und Designer bieten jetzt auf dem Formular ein Feld für die Scribble-Signatur. Wenn das Formular im Browser angezeigt wird, können Benutzer mit einem Eingabestifts, einer Maus oder mit einer Berührung in diesem Feld unterzeichnen.

## Entwerfen eines Formulars mit einem Feld für Scribble-Signaturen {#how-to-design-a-form-using-scribble-signature-field}

1. Öffnen Sie ein Formular in Forms Designer.
1. Ziehen das Scribble-Signatur-Feld auf die Seite.

   ![designer_scribble](assets/designer_scribble.png)

   >[!NOTE]
   >
   >Dimensionen des in Forms Designer ausgewählten Felds werden bei der Wiedergabe des Felds angezeigt. Allerdings wird die Größe des angezeigten Unterschriftenfeldes basierend auf dem Seitenverhältnis des Felds und nicht anhand der in Forms Designer festgelegten Größe berechnet.

1. Konfigurieren Sie das Scribble-Signatur-Feld.

   Beim Unterschreiben auf einem iPad werden am Scribble-Signatur-Feld standardmäßig die geografischen Informationen als Pflichtangabe markiert. (Diese Angabe ist auf anderen Geräten optional.) Dieses Standardverhalten kann außer Kraft gesetzt werden, indem der Wert der Eigenschaft `geoLocMandatoryOnIpad`   geändert wird. Diese Eigenschaft wird auf dem Scribble-Signatur-Feld als Extras-Option bereitgestellt. Die Schritte zum Ändern dieser Einstellung:

   1. Wählen Sie im Formular das Scribble-Signatur-Feld.
   1. Wählen Sie die Registerkarte **XML-Quelle.**

      >[!NOTE]
      >
      >Um die Registerkarte &quot;XML-Quelle&quot;zu öffnen, klicken Sie auf **Ansicht** >  **XML-Quelle**.

   1. Suchen Sie die `<ui>` -Tag im `<field>` Taggen und ändern Sie den Quellcode so, dass er wie folgt aussieht:

      ```xml
      <extras name="x-scribble-add-on">
      <boolean name="geoLocMandatoryOnIpad">0</boolean>
      </extras>
      ```

   1. Wählen Sie die Registerkarte **Designansicht**. Klicken Sie im Bestätigungsfeld auf **Ja**.
   1. Speichern Sie das Formular.

1. Geben Sie das Formular in einem Browser auf einem unterstützten Gerät/Desktop wieder.

## Benutzeroberfläche für Scribble-Signaturen {#interfacing-with-the-scribble-signatures}

### Signing {#signing}

Nachdem ein Scribble-Signatur-Feld dem Formular hinzugefügt wurde und das Formular angezeigt wird, wird beim Klicken oder Tippen auf das Feld ein Dialogfeld geöffnet. Der Benutzer kann mit einer Maus, mit dem Finger oder einem Eingabestift im gepunkteten Rechteck unterschreiben.

![Geolocation](assets/geolocation.png)

**A.** Pinsel **B.** Radiergummi **C.** Geolocation **D.** Geolocation-Informationen

### Geotagging {#geo-tagging}

Wenn Sie beim Einfügen der Signatur auf das Geotargeting-Symbol klicken, werden geografische Informationen und die Uhrzeit in das Feld eingebettet.

>[!NOTE]
Das Einbetten der geografischen Informationen ist auf einem iPad obligatorisch.

Auf einem iPad wird das Geotargeting-Symbol standardmäßig nicht angezeigt. Die geografischen Informationen werden automatisch eingebettet, wenn Sie auf **OK** klicken.

Diese Einstellung kann auf iPads geändert werden, indem in den init-Parametern des Feldes der Wert des Parameters `geoLocManadatoryOnIpad` auf `0` gesetzt wird.

* Wenn die Angabe geografischer Informationen obligatorisch ist, wird dem Benutzer ein kleinerer Bereich zum Zeichnen angezeigt. Der Geotagging-Text wird hinzugefügt, wenn der Benutzer auf dem anderen Bereich auf das Symbol **OK** klickt.
* In anderen Fällen wird dem Benutzer der komplette Bereich angezeigt. Wenn der Benutzer sich dazu entscheidet, geografische Informationen hinzuzufügen, wird die Größe des Bereichs angepasst, um den Geotagging-Text einzufügen.

### Löschen einer Signatur {#clearing-a-signature}

Bei Verwendung dieser Funktion kann ein Benutzer auf die **Radiergummi** -Symbol, um das Feld zu löschen und von vorn zu beginnen. Wenn zuvor geografische Informationen hinzugefügt wurden, werden diese ebenfalls gelöscht.

### Speichern einer Signatur {#saving-a-signature}

Durch Klicken auf das Symbol **OK** wird die Unterschrift als ein Bild im Feld gespeichert. Das Bild und die Werte können zur weiteren Bearbeitung an den Server gesendet werden. Sobald der Benutzer auf **OK** geklickt hat, wird das Unterschriftsfeld gesperrt. Die Unterschrift kann nicht mehr mithilfe des Scribble-Widgets bearbeitet werden.

Durch Tippen oder Klicken auf das Unterschriftsfeld wird das Dialogfeld im schreibgeschützten Modus geöffnet.

![3](assets/3.png)

### Auswählen der Schriftgröße {#selecting-pen-size}

Klicken Sie auf das Symbol **Pinsel**, um eine Liste der verfügbaren Stiftgrößen anzuzeigen. Klicken oder Tippen Sie auf eine Schriftgröße, die verwendet werden soll.

### Löschen von Unterschriften aus dem Formular {#delete-signatures-from-the-form}

Löschen der Unterschriften aus dem Formular

* (Auf mobilen Geräten) Drücken Sie lang auf das Unterschriftsfeld und tippen Sie im Bestätigungsdialogfeld auf **Ja**.
* (Desktop) Bewegen Sie die Maus über das Unterschriftsfeld, klicken Sie auf das Symbol **Abbrechen** und klicken Sie im Bestätigungsdialogfeld auf **Ja**.
