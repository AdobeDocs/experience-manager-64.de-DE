---
title: 'Tutorial "NICHT VERÖFFENTLICHEN": Anwenden von Regeln auf adaptive Formularfelder"'
seo-title: Apply rules to adaptive form fields
description: 'Erstellen Sie Regeln, um einem adaptiven Formular Interaktivität, Geschäftslogik und intelligente Validierungen hinzuzufügen. '
seo-description: Create rules to add interactivity, business logic, and smart validations to an adaptive form.
page-status-flag: de-activated
uuid: 60f142aa-81ca-4333-8614-85a01e23e917
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 982eddba-2350-40e7-8a42-db02d28cf133
feature: Adaptive Forms
exl-id: bb65b6d7-5bbf-4cc5-a468-9ea8465f7a07
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 66%

---

# Schulung: Wenden Sie Regeln auf adaptive Formularfelder an {#tutorial-apply-rules-to-adaptive-form-fields}

![06-apply-rules-to-adaptive-form_main](assets/06-apply-rules-to-adaptive-form_main.png)

Diese Schulung ist ein Schritt in der Reihe [Erstellen Ihres ersten adaptives Formulars](/help/forms/using/create-your-first-adaptive-form.md). Adobe empfiehlt, die Serie in chronologischer Reihenfolge zu verfolgen, um den vollständigen Anwendungsfall der Schulung zu verstehen, auszuführen und zu demonstrieren.

## Über die Schulung {#about-the-tutorial}

Sie können Regeln erstellen, um einem adaptiven Formular Interaktivität, Geschäftslogik und intelligente Validierungen hinzuzufügen. Adaptive Formulare verfügen über einen integrierten Regeleditor. Der Regeleditor bietet eine Drag-and-Drop-Funktionalität, ähnlich wie bei Einführungen. Die Drag-and-Drop-Methode ist die schnellste und einfachste Methode zum Erstellen von Regeln. Der Regeleditor bietet außerdem ein Code-Fenster für Benutzer, die ihre Programmierfähigkeiten testen oder die Regeln weiterentwickeln möchten.

Sie können mehr über den Regeleditor unter [Regeleditor für adaptive Formulare](/help/forms/using/rule-editor.md) erfahren.

Am Ende der Schulung lernen Sie Regeln zu erstellen, um Folgendes zu tun: 

* Aufrufen eines Formulardatenmodell-Dienstes, um Daten aus der Datenbank abzurufen
* Aufrufen eines Formulardatenmodell-Dienstes, um Daten zur Datenbank hinzuzufügen
* Ausführen einer Validierungsprüfung und Anzeigen von Fehlermeldungen

Interaktive GIF-Bilder am Ende jedes Abschnitts der Schulung helfen Ihnen dabei, die Funktionalität des Formulars, das Sie gerade erstellen, schnell zu lernen und zu validieren. 

## Schritt 1: Abrufen eines benutzerdefinierten Datensatzes aus der Datenbank {#retrieve-customer-record}

Sie haben ein Formulardatenmodell erstellt wie im Artikel [Formulardatenmodell erstellen](/help/forms/using/create-form-data-model.md) beschrieben. Jetzt können Sie den Regeleditor verwenden, um die Formulardatenmodelldienste aufzurufen, um Informationen aus der Datenbank abzurufen und ihr hinzuzufügen.

Jedem Kunden ist eine eindeutige Kunden-ID-Nummer zugeordnet, anhand derer er relevante Kundendaten in einer Datenbank identifizieren kann. Das folgende Verfahren verwendet die Kunden-ID, um Informationen aus der Datenbank abzurufen:

1. Öffnen Sie Ihr adaptives Formular zum Bearbeiten.

   [http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)

1. Tippen Sie auf das Feld **[!UICONTROL Kunden-ID]** und tippen Sie auf das Symbol **[!UICONTROL Regeln bearbeiten]**. Das Fenster „Regeleditor“ wird geöffnet.
1. Tippen Sie auf das Symbol **[!UICONTROL + Erstellen]**, um eine Regel hinzuzufügen. Es öffnet den visuellen Editor.

   Im Visual Editor wird die **[!UICONTROL WENN]** -Anweisung ist standardmäßig ausgewählt. Außerdem das Formularobjekt (in diesem Fall **[!UICONTROL Kunden-ID]**), von wo aus Sie den Regeleditor gestartet haben, wird im Abschnitt **[!UICONTROL WENN]** -Anweisung.

1. Tippen Sie auf **[!UICONTROL Status auswählen]** und wählen Sie **[!UICONTROL geändert]**.

   ![whencustomeridischanged](assets/whencustomeridischanged.png)

1. In der Anweisung **[!UICONTROL THEN]** wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen.]**
1. Wählen Sie den Dienst **[!UICONTROL Versandadresse abrufen]** aus der Dropdown-Liste **[!UICONTROL Auswählen]**.
1. Ziehen Sie die **[!UICONTROL Kunden-ID]** von der Registerkarte &quot;Formularobjekte&quot;zum **[!UICONTROL Objekt ablegen oder hier auswählen]** im Feld **[!UICONTROL EINGABE]** ankreuzen.

   ![dropobjectstoinputfield-retrieveData](assets/dropobjectstoinputfield-retrievedata.png)

1. Ziehen Sie die **[!UICONTROL Kunden-ID, Name, Versandadresse, Bundesland und Postleitzahl]** von der Registerkarte &quot;Formularobjekte&quot;zum **[!UICONTROL Objekt ablegen oder hier auswählen]** im Feld **[!UICONTROL AUSGABE]** ankreuzen.

   ![dropobjectstooutputfield-retrieveData](assets/dropobjectstooutputfield-retrievedata.png)

   Tippen Sie auf **[!UICONTROL Fertig]**, um die Regel zu speichern. Tippen Sie im Fenster des Regeleditors auf **[!UICONTROL Schließen]**.

1. Zeigen Sie das adaptive Formular in der Vorschau an. Geben Sie eine ID im Feld **[!UICONTROL Kunden-ID]** ein. Das Formular kann nun Kundendaten aus der Datenbank abrufen.

   ![retrieve-information](assets/retrieve-information.gif)

## Schritt 2: Fügen Sie die aktualisierte Kundenadresse zur Datenbank hinzu {#updated-customer-address}

Nachdem die Kundendaten aus der Datenbank abgerufen wurden, können Sie die Lieferadresse, das Bundesland und die Postleitzahl aktualisieren. Das folgende Verfahren ruft einen Formulardatenmodelldienst auf, um Kundeninformationen in der Datenbank zu aktualisieren:

1. Wählen Sie das Feld **[!UICONTROL Senden]** und tippen Sie auf das Symbol **[!UICONTROL Regeln bearbeiten]**. Das Fenster „Regeleditor“ wird geöffnet.
1. Wählen Sie die **[!UICONTROL Submit - Click]** und tippen Sie auf **[!UICONTROL Bearbeiten]** Symbol. Die Optionen zum Bearbeiten der Senderegel werden angezeigt.

   ![submit-rule](assets/submit-rule.png)

   In der WHEN-Option wird die **[!UICONTROL Einsenden]** und **[!UICONTROL angeklickt wird]** -Optionen bereits ausgewählt sind.

   ![submit-is-clicked](assets/submit-is-clicked.png)

1. Tippen Sie in der Option **[!UICONTROL THEN]** auf **[!UICONTROL + Anweisung hinzufügen]**. Wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]**.
1. Wählen Sie den Dienst **[!UICONTROL Versandadresse aktualisieren]** aus der Dropdown-Liste **[!UICONTROL Auswählen]**.

   ![update-shipping-address](assets/update-shipping-address.png)

1. ![dropobjectstoinputfield-updatedata](assets/dropobjectstoinputfield-updatedata.png)

   Ziehen Sie die **[!UICONTROL Versandadresse, Bundesland und Postleitzahl]** -Feld von der Registerkarte &quot;Formularobjekte&quot;bis zur entsprechenden Tabelleneigenschaft mit dem Namen .property (z. B. customerdetails.shippingAddress) der **[!UICONTROL Objekt ablegen oder hier auswählen]** im Feld **[!UICONTROL EINGABE]** ankreuzen. Alle Felder mit dem Präfix tablename (in diesem Anwendungsbeispiel &quot;customerdetails&quot;) dienen als Eingabedaten für den Aktualisierungsdienst. Der gesamte Inhalt in diesen Feldern wird in der Datenquelle aktualisiert.

   >[!NOTE]
   >
   >Ziehen Sie die **[!UICONTROL Name]** und **[!UICONTROL Kunden-ID]** -Felder zur entsprechenden tablename.property hinzu (z. B. customerdetails.name). Der Name und die ID des Kunden sollten nicht versehentlich aktualisiert werden.

1. Ziehen Sie das Feld **[!UICONTROL Kunden-ID]** per Drag-and-Drop von der Registerkarte „Formularobjekte“ in das Feld „ID“ im Feld **[!UICONTROL INPUT]**. Felder ohne Präfix  tablename (in diesem Anwendungsfall beispielsweise customerdetails ) dient als Suchparameter für den Aktualisierungsdienst. Die **[!UICONTROL id]** -Feld in diesem Anwendungsfall identifiziert einen Datensatz in der Tabelle mit Kundendetails eindeutig.
1. Tippen Sie auf **[!UICONTROL Fertig]**, um die Regel zu speichern. Tippen Sie im Fenster des Regeleditors auf **[!UICONTROL Schließen]**.
1. Zeigen Sie das adaptive Formular in der Vorschau an. Rufen Sie Details eines Kunden ab, aktualisieren Sie die Lieferadresse und senden Sie das Formular ab. Wenn Sie Details des gleichen Kunden erneut abrufen, wird die aktualisierte Lieferadresse angezeigt.

## Schritt 3: (Abschnitt „Bonus“) Verwenden Sie den Code-Editor, um Validierungen auszuführen und Fehlermeldungen anzuzeigen {#step-bonus-section-use-the-code-editor-to-run-validations-and-display-error-messages}

Sie sollten die Validierung des Formulars durchführen, um sicherzustellen, dass die im Formular eingegebenen Daten korrekt sind und im Falle von fehlerhaften Daten eine Fehlermeldung angezeigt wird. Wenn beispielsweise eine nicht vorhandene Kunden-ID in das Formular eingegeben wird, sollte eine Fehlermeldung angezeigt werden.

Adaptive Formulare bieten mehrere Komponenten mit integrierten Validierungen, z. B. E-Mail, und numerische Felder, die Sie für häufige Anwendungsfälle verwenden können. Verwenden Sie den Regeleditor für erweiterte Anwendungsfälle, um z. B. eine Fehlermeldung anzuzeigen, wenn die Datenbank null (0) Datensätze (keine Datensätze) zurückgibt. 

Das folgende Verfahren zeigt, wie Sie eine Regel erstellen, die eine Fehlermeldung anzeigt, wenn die im Formular eingegebene Kunden-ID nicht in der Datenbank vorhanden ist. Die Regel stellt außerdem den Fokus auf das Feld Kunden-ID und setzt es zurück. Die Regel verwendet [die dataIntegrationUtils-API des Formulardatenmodelldienstes](/help/forms/using/invoke-form-data-model-services.md) , um zu überprüfen, ob die Kunden-ID in der Datenbank vorhanden ist.

1. Tippen Sie auf **[!UICONTROL Kunden-ID]** und tippen Sie auf `Edit Rules` Symbol. Das Fenster „Regeleditor“ wird geöffnet.
1. Tippen Sie auf das Symbol **[!UICONTROL + Erstellen]**, um eine Regel hinzuzufügen. Es öffnet den visuellen Editor.

   Im Visual Editor wird die **[!UICONTROL WENN]** -Anweisung ist standardmäßig ausgewählt. Außerdem das Formularobjekt (in diesem Fall **[!UICONTROL Kunden-ID]**), von wo aus Sie den Regeleditor gestartet haben, wird im Abschnitt **[!UICONTROL WENN]** -Anweisung.

1. Tippen Sie auf **[!UICONTROL Status auswählen]** und wählen Sie **[!UICONTROL geändert]**.

   ![whencustomeridischanged](assets/whencustomeridischanged.png)

   In der Anweisung **[!UICONTROL THEN]** wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen.]**

1. Wechseln Sie von **[!UICONTROL Visual Editor]** zu **[!UICONTROL Code Editor]**. Die Schaltersteuerung befindet sich auf der rechten Seite des Fensters. Der Code-Editor wird geöffnet und zeigt Code ähnlich dem Folgenden an:

   ![code-editor](assets/code-editor.png)

1. Ersetzen Sie den Eingabevariablenabschnitt durch den folgenden Code:

   ```
   var inputs = {
       "id" : this
   };
   ```

1. Ersetzen Sie den Abschnitt guidelib.dataIntegrationUtils.executeOperation (operationInfo, Eingaben, Ausgaben) durch den folgenden Code:

   ```
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, function (result) {
     if (result) {
         result = JSON.parse(result);
       customer_Name.value = result.name;
       customer_Shipping_Address = result.shippingAddress;
     } else {
       if(window.confirm("Invalid Customer ID. Provide a valid customer ID")) {
             customer_Name.value = " ";
            guideBridge.setFocus(customer_ID);
       }
     }
   });
   ```

1. Zeigen Sie das adaptive Formular in der Vorschau an. Geben Sie eine falsche Kunden-ID ein. Eine Fehlermeldung wird angezeigt.

   ![display-validation-error](assets/display-validation-error.gif)
