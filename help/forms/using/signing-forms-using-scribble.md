---
title: Anwenden elektronischer Signaturen auf ein Formular mithilfe der Freihandsignatur
seo-title: Apply electronic signatures to a form using scribble signatures
description: Signieren von Formularen mit Freihandsignaturen
seo-description: Signing forms using scribble
uuid: e807d0de-6d5f-458e-be3e-273ed7a521c0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 6a806727-28c5-430e-9a83-b43e0e9d9e1c
feature: Adaptive Forms
exl-id: a870c4b7-4040-4bd8-b477-286ebe6a4b01
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 90%

---

# Anwenden elektronischer Signaturen auf ein Formular mithilfe der Freihandsignatur  {#apply-electronic-signatures-to-a-form-using-scribble-signatures}

Sie können die Komponente **Freihandsignatur** und die Komponente **Signaturschritt** verwenden, um eine Signatur in ein adaptives Formular zu zeichnen. Die Signaturschritt-Komponente zeigt eine PDF-Version des adaptiven Formulars an. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare, um die Signaturschritt-Komponente zu verwenden.

Wie unten dargestellt stellen beide Komponenten ein Fenster zum Signieren eines Formulars bereit. Sie können auch auf das Geolocation-Symbol ![aem_6_3_geolocation](assets/aem_6_3_geolocation.png) klicken, um der Signatur Geolocation-Informationen hinzuzufügen.

![Dialogfeld für Freihandsignatur](assets/scribble-signature.png)

## Adaptives Formular konfigurieren, um Freihandsignatur zu verwenden {#configure-an-adaptive-form-to-use-scribble-signature}

1. Erstellen Sie ein adaptives Formular mit aktivierter Option „Datensatzdokument“ oder basierend auf eine Formularvorlage. Einzelschritte finden Sie unter [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md).
1. Ziehen Sie die Komponente **Freihandsignatur** aus dem Komponenten-Browser in das adaptive Formular.
1. Tippen Sie auf das Symbol **Konfigurieren** (![configure](assets/configure.png)). Dadurch wird der Eigenschaftenbrowser geöffnet und Eigenschaften der Komponente „Freihandsignatur“ angezeigt. Konfigurieren Sie die Eigenschaften der Komponente „Freihandsignatur“.
1. Ziehen Sie die Signaturschritt-Komponente aus dem Komponenten-Browser in das adaptive Formular.

   >[!NOTE]
   >
   >Die Komponente „Signaturschritt“ nimmt die gesamte für das Formular verfügbare Breite ein. Wir empfehlen, keine anderen Komponenten in dem Abschnitt zu platzieren, der die Komponente „Signaturschritt“ enthält.

1. Tippen Sie im Inhaltsbrowser auf **Formular-Container** und dann auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet, der die Eigenschaften des Containers für adaptive Formulare anzeigt. Navigieren Sie zu **Container für adaptive Formulare** > **Elektronische Signatur** und die Auswahl der **Acrobat Sign aktivieren** -Option. Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Änderungen zu speichern.

   >[!NOTE]
   >
   >Wenn Sie einem adaptiven Formular eine Signaturschritt-Komponente hinzufügen, wird die Option Acrobat Sign aktivieren automatisch ausgewählt.

1. Tippen Sie auf das Symbol **Konfigurieren** (![configure](assets/configure.png)). Dadurch wird der Eigenschaftenbrowser geöffnet, der die Eigenschaften des Signaturschritts anzeigt. Konfigurieren Sie die folgenden Eigenschaften:

   * **Elementname**: Geben Sie den Namen der Komponente an.
   * **Titel:** Geben Sie den eindeutigen Titel der Komponente an.
   * **Vorlagennachricht**: Geben Sie die Nachricht an, die angezeigt werden soll, während das PDF-Signaturdokument geladen wird. Acrobat Sign-Dienste benötigen einige Zeit, um Signatur-PDF vorzubereiten und zu laden.
   * **Signaturdienst**: Wählen Sie die Option **Freihandsignatur** aus.
   * **CSS-Klasse**: Geben Sie ggf. die CSS-Klasse der Client-Bibliothek an. Es wird empfohlen, anstelle der CSS-Klasse [Designs](/help/forms/using/themes.md) und [Inline-Stile](/help/forms/using/inline-style-adaptive-forms.md) zu verwenden.

   Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Änderungen zu speichern. Die Signatur wurde erfolgreich konfiguriert.

   Wenn Sie jetzt ein Formular ausfüllen, wird eine PDF-Version des adaptiven Formulars angezeigt und es sind Optionen zum Signieren des PDF-Dokuments verfügbar. Weitere Informationen finden Sie unter [Unterschreiben eines adaptiven Formulars mit Freihandsignatur](/help/forms/using/signing-forms-using-scribble.md#p-sign-an-adaptive-form-using-scribble-signature-p). 

## Unterschreiben eines adaptiven Formulars mit Freihandsignatur {#sign-an-adaptive-form-using-scribble-signature}

1. Wenn Sie ein adaptives Formular ausgefüllt und die Signaturschritt-Seite erreichen, wird der Signaturbildschirm angezeigt.

   ![Signaturbildschirm für EchoSign-Seite](assets/esignscribblesign.jpg)

1. Klicken Sie auf **[!UICONTROL Signieren]**. Das Dialogfeld „Freihandsignatur“ wird angezeigt. Signieren Sie das Formular und klicken Sie auf das Symbol „Fertig“ ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Signatur zu speichern.

   ![Dialogfeld für Freihandsignatur](assets/scribblewidget.jpg)

1. Klicken Sie auf „Abschließen“, um den Signiervorgang abzuschließen.

   ![Signiervorgang abschließen](assets/scribblecomplete.jpg)

Die Signaturen werden dem Formular hinzugefügt und die Formularsteuerung wechselt zum nächsten Bereich.
