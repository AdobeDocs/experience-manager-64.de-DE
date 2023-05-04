---
title: Verwenden eines adaptiven Formulars in HTML Workspace
seo-title: Using an adaptive form in HTML Workspace
description: Verwenden eines adaptiven Formulars in HTML Workspace
seo-description: Using an adaptive form in HTML Workspace
uuid: 1ebe81ae-5c0b-4c07-8cd1-86efdf8415be
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 2f514072-81d9-48de-8369-cca94a330f1d
exl-id: 88fa9c80-4eae-4663-a6c8-abbf1921444e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 56%

---

# Verwenden eines adaptiven Formulars in HTML Workspace {#using-an-adaptive-form-in-html-workspace}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit AEM Forms on JEE können adaptive Formulare in HTML Workspace verwendet werden.

Da während des Prozess-Designs ein XDP ausgewählt werden kann, wurde die Funktion zum Durchsuchen eines bestehenden adaptiven Formular-AEM-Repository hinzugefügt. Mit der Funktion kann der Prozess-Designer ein adaptives Formular sowohl in „Ausgangspunkt“ als auch in „Aufgabe“ konfigurieren.

## Prozessdesign {#process-design-experience}

Führen Sie die folgenden Schritte aus, um die Verwendung adaptiver Formulare im Prozessentwurf zu ermöglichen:

* In &quot;Aufgabe zuweisen&quot;und &quot;Ausgangspunkt&quot;können Sie beim Zuweisen eines Formular-Assets zu einer Aufgabe zu einem adaptiven Formular-Asset im CRX-Repository navigieren.
* Im Eigenschaftenblatt &quot;Aufgabe zuweisen/Ausgangspunkt&quot;können Sie die Symbolleiste der obersten Ebene/die globale Symbolleiste eines adaptiven Formulars ausblenden.
* Sie können neue Aktionsprofile für Wiedergabe- und Sendeaktionen in adaptiven Formularen verwenden.

### Export und Import von LiveCycle-Anwendungen {#livecycle-application-export-and-import}

Da sich adaptive Formulare im AEM-Repository befinden, enthält der LiveCycle-Anwendungsexport nur die Verweise für verwendete adaptive Formulare. Deshalb umfasst der Export und Import des LiveCycle-Programms zwei Schritte. Die LiveCycle-Anwendung enthält Prozessdefinitionen usw. Ein separates Paket, das adaptive Formulare enthält, wird als ZIP-Datei aus AEM exportiert. Beim Importieren wird die LiveCycle-Anwendung über Workbench importiert und adaptive Formulare werden über AEM importiert.

## Anwendererlebnis des adaptiven Formulars in HTML Workspace {#user-experience-of-adaptive-form-in-html-workspace}

HTML Workspace bietet einige adaptive formularspezifische Steuerelemente zusätzlich zu den Steuerelementen, die für mobile Formulare verfügbar sind. Benutzer können in HTML Workspace Anlagen hinzufügen, speichern, signieren, senden und navigieren, wenn sie eine Aufgabe oder einen Startpunkt öffnen. Im Folgenden finden Sie die Details:

1. Um **Dateien anzuhängen, verwenden Sie Aufgabenanlagen, wie es in Mobile Forms der Fall war. Schaltflächen für Dateianhänge des adaptiven Formulars werden ausgeblendet.

1. Klicken Sie zum Speichern des adaptiven Formulars auf **Speichern**, genau wie in Mobile Forms. Schaltflächen zum Speichern des adaptiven Formulars werden ausgeblendet.

1. Verwenden Sie zum Senden eines adaptiven Formulars die Schaltfläche **Senden** oder die verfügbaren Route-Aktionen, wie in Mobile Forms. Schaltflächen zum Senden des adaptiven Formulars werden ausgeblendet.

1. **Sichtbarkeit der globalen Symbolleiste des adaptiven Formulars**: Wenn im Prozess-Designer die globale Symbolleiste/die Symbolleiste der obersten Ebene ausgeblendet wird, werden die Symbolleiste und die Schaltflächen nicht auf adaptiven Formularen angezeigt.

1. **Navigationssteuerelemente des Arbeitsbereichs für adaptive Formulare**: Die Schaltflächen „Weiter“/„Zurück“ zusammen mit den Schaltflächen „Speichern“, „Senden“ und „Route-Aktion“ sind für ein adaptives Formular in HTML Workspace verfügbar. Klicken Sie auf die Schaltflächen „Weiter/Zurück“, um zwischen den Bereichen der adaptiven Formulare in HTML Workspace zu navigieren. Die Schaltflächen „Weiter/Zurück“ ermöglichen die Navigation, ähnlich der Navigationssteuerelemente in der Ansicht „Mobil“ der adaptiven Formulare.

1. **eSign-Services und die Übersichtskomponente des adaptiven Formulars**: Die Übersichtskomponente ist in HTML Workspace nicht funktional. Anders ausgedrückt: Wenn ein adaptives Formular über eine Zusammenfassungskomponente verfügt, ist es im Arbeitsbereich nicht sichtbar. Anstelle des automatischen Sendevorgangs in der Design-Komponente klickt der Workspace-Benutzer auf die Übermittlungs- oder Routenaktion in HTML Workspace. Nachdem ein Dokument signiert wurde, ist es als reduziertes signiertes Dokument sichtbar. Klicken **Einsenden** oder einer Route-Aktion, um die Aufgabe oder den Startpunkt zu schließen/abzuschließen.

   Das signierte Dokument wird vom eSign-Dienste-Server erfasst und die Daten-XML-Datei wird im nächsten Schritt weitergeleitet.

## Schritte zum Verwenden adaptiver Formulare im Prozessdesign {#steps-to-use-adaptive-forms-in-process-design}

1. Öffnen Sie Adobe Experience Manager Forms Workbench.

1. Wählen Sie **Datei > Neu > Anwendung** ais oder verwenden Sie das bestehende Programm, um ein Programm zu erstellen.

   ![Neue Anwendung erstellen](assets/create_new_appl.png)

1. Erstellen Sie einen Prozess oder verwenden Sie einen vorhandenen Prozess im Programm.

   ![Neuen Prozess erstellen](assets/create_new_process.png)

1. Erstellen Sie einen Ausgangspunkt oder einen Vorgang „Aufgabe zuweisen“ und doppelklicken Sie darauf.
1. Wählen Sie im Abschnitt **[!UICONTROL Präsentation und Daten]** **[!UICONTROL Ein CRX-Element verwenden]** und klicken Sie vor den Elementen auf die Ellipsen.

   ![Use a CRX asset](assets/use_crx_asset.png)

1. Wählen Sie das adaptive Formular aus, das durch Benutzeroberfläche „Elemente verwalten“ erstellt wurde, und klicken Sie auf **[!UICONTROL OK]**.

   ![Ein adaptives Formular auswählen](assets/selecting_form.png)

   >[!NOTE]
   >
   >Weitere Informationen zum Erstellen eines adaptiven Formulars finden Sie unter [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md).
   >
   >Weitere Informationen zur Erstellung eines Prozesses finden Sie unter [Erstellen und Verwalten von Prozessen](https://help.adobe.com/de_DE/AEMForms/6.1/WorkbenchHelp/WS92d06802c76abadb-1cc35bda128261a20dd-7ff7.2.html).
