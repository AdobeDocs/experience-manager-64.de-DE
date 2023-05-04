---
title: Automatisches Speichern eines adaptiven Formulars
seo-title: Auto-save an adaptive form
description: Sie können ein adaptives Formular so konfigurieren, dass der Inhalt basierend auf einem Ereignis oder einem vordefinierten Zeitintervall automatisch gespeichert wird
seo-description: You can configure an adaptive form to automatically start saving the content based on an event or a pre-defined time-interval
uuid: 0fe9a389-269b-438a-9489-d9d1d09558a1
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: d519ac4e-6d29-4a69-874e-792acabe87ff
feature: Adaptive Forms
exl-id: 073734e9-449b-463a-b539-d73e11f50fa4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 43%

---

# Adaptives Formular automatisch speichern {#auto-save-an-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können ein adaptives Formular so konfigurieren, dass der Inhalt basierend auf einem Ereignis oder einem vordefinierten Zeitintervall automatisch gespeichert wird. Standardmäßig werden Inhalte eines adaptiven Formulars in einer Benutzeraktion gespeichert, z. B. durch Drücken der Schaltfläche &quot;Speichern&quot;. Die Option &quot;Automatisches Speichern&quot;ist in folgenden Bereichen hilfreich:

* Automatisches Speichern des Inhalts für anonyme und angemeldete Benutzer
* Inhalt eines Formulars ohne oder mit minimalem Benutzereingriff speichern
* Speichern von Inhalt eines Formulars basierend auf einem Benutzerereignis starten
* Wiederholtes Speichern des Formularinhalts nach einem bestimmten Zeitintervall

## Automatisches Speichern für ein adaptives Formular aktivieren {#enable-autosave-for-an-adaptive-form}

Bei einem adaptiven Formular ist die Option &quot;Automatisches Speichern&quot;nicht standardmäßig aktiviert. Sie können die Option „Automatisches Speichern“ über den Abschnitt **Automatisches Speichern** eines adaptiven Formulars aktivieren. Der Abschnitt **Automatisches Speichern** bietet mehrere weitere Konfigurationsoptionen. Führen Sie zum Aktivieren und Konfigurieren der Option „Automatisches Speichern“ für ein adaptives Formular folgende Schritte durch: 

1. Um auf den Abschnitt für das automatische Speichern in den Eigenschaften zuzugreifen, wählen Sie eine Komponente aus und tippen Sie auf ![Feldebene](assets/field-level.png) > **[!UICONTROL Container für ein adaptives Formular]** und anschließend auf ![cmppr](assets/cmppr.png).
1. Im **[!UICONTROL Automatisches Speichern]** Abschnitt **[!UICONTROL Aktivieren]** die Option &quot;Automatisches Speichern&quot;.
1. Im **[!UICONTROL Adaptives Formularereignis]** Geben Sie 1 oder TRUE ein, um das Formular automatisch zu speichern, wenn es in den Browser geladen wird. Sie können auch einen bedingten Ausdruck für ein Ereignis angeben, das, wenn es ausgelöst wird und &quot;true&quot;zurückgibt, mit dem Speichern des Formularinhalts beginnt.
1. Geben Sie den Trigger an. Das automatische Speichern wird basierend auf Ihrer Konfiguration ausgelöst. Ihre Optionen sind:

   * **[!UICONTROL Zeitbasiert:]** Wählen Sie diese Option, um den Inhalt anhand eines bestimmtes Zeitintervalls zu speichern.
   * **[!UICONTROL Ereignisbasiert:]** Wählen Sie diese Option, um den Inhalt beim Auslösen eines Ereignisses zu speichern.

   Wenn Sie einen Trigger auswählen, ist das Feld &quot;Strategiekonfiguration&quot;aktiviert. Das Feld &quot;Strategiekonfiguration&quot;ermöglicht Folgendes:

   * ein Zeitintervall angeben, wenn Sie **[!UICONTROL Zeitbasiert]** für den Auslöser wählen.
   * Den Namen des Ereignisses angeben, wenn Sie **[!UICONTROL Ereignisbasiert]** für den Auslöser wählen.

   Sie können auch eine eigene benutzerdefinierte Strategie erstellen und der Liste hinzufügen. Weitere Informationen finden Sie unter [Benutzerdefinierte Strategie zum automatischen Speichern von Formularen implementieren](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p).

1. (Nur zeitbasiertes automatisches Speichern) Führen Sie die folgenden Schritte aus, um die Optionen für das zeitbasierte automatische Speichern zu konfigurieren.

   1. Im **[!UICONTROL Automatisches Speichern in diesem Intervall]** Legen Sie das Zeitintervall in Sekunden fest. Das Formular wird wiederholt gespeichert, nachdem die im Intervallfeld angegebene Anzahl von Sekunden abgelaufen ist.

1. (Nur ereignisbasiertes automatisches Speichern) Führen Sie die folgenden Schritte aus, um Optionen für ereignisbasiertes automatisches Speichern zu konfigurieren.

   1. Geben Sie im Feld **Automatisch nach diesem Ereignis speichern** ein [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html)-Ereignis an. Das Formular wird immer dann gespeichert, wenn der Ausdruck „TRUE“ ergibt.

1. (Optional) Um den Inhalt automatisch für anonyme Benutzer zu speichern, wählen Sie die Option **Automatisches Speichern für anonyme Benutzer aktivieren** und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Damit die Option zum automatischen Speichern für anonyme Benutzer funktioniert, stellen Sie sicher, dass Sie den allgemeinen Forms-Konfigurationsdienst so konfiguriert ist, dass alle Benutzer Formulare in der Vorschau anzeigen, überprüfen und zu signieren können.
   >
   >Um den Service zu konfigurieren, wechseln Sie zur Konfiguration der AEM-Web-Konsole unter `https://[server]:[host]/system/console/configMgr` und bearbeiten Sie den **[!UICONTROL allgemeinen Konfigurations-Service von Forms]** so, dass die Option **[!UICONTROL Alle Benutzer]** im Feld **[!UICONTROL Zulassen]** ausgewählt wird, und speichern Sie dann die Konfiguration.

## Implementieren einer benutzerdefinierten Strategie zum Aktivieren der automatischen Speicherung für adaptive Formulare {#implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms}

Sie können ein benutzerdefiniertes Ereignis implementieren, um die Funktion zum automatischen Speichern Trigger. Führen Sie die folgenden Schritte aus, um das benutzerdefinierte Ereignis zu erstellen und zu implementieren:

1. Erstellen Sie Client-Bibliotheks- und Client-Bibliotheksordner. Ausführliche Anweisungen finden Sie unter in [Verwenden clientseitiger Bibliotheksdokumente](/help/sites-developing/clientlibs.md). 

   Beispiel: Das folgende Skript verwendet das benutzerdefinierte Ereignis `emailFocusChange`, um die Funktion für automatisches Speichern auszulösen:

   ```
   window.addEventListener("bridgeInitializeStart", function (){   
       guideBridge.connect(function () { guideBridge.on("elementFocusChanged", function (event,data) { 
           if(data.target.name === 'Email') {
               guideBridge.trigger("emailFocusChange");
           }
       });
      });
   });
   ```

   >[!NOTE]
   >
   >Eine Kategorieeigenschaft wird beim Erstellen von Clientbibliothekordnern definiert. Halten Sie den der Kategorieeigenschaft zugewiesenen Wert bereit.

1. Öffnen Sie das adaptive Formular im Authoring-Modus.

1. Wählen Sie im Bearbeitungsmodus eine Komponente aus und tippen Sie anschließend auf ![field-level](assets/field-level.png) > **[!UICONTROL Container für ein adaptives Formular]** und dann auf ![cmppr](assets/cmppr.png).
1. Öffnen Sie in den Eigenschaften die **[!UICONTROL Allgemein]** Abschnitt. Im **[!UICONTROL Client-Bibliothekskategorie]** Geben Sie den Wert der Kategorieeigenschaft ein, die beim Erstellen der Client-Bibliotheksordner definiert wurde.
1. Öffnen Sie den Abschnitt Automatisches Speichern . Im **[!UICONTROL Automatisches Speichern nach diesem Ereignis]** ein benutzerdefiniertes Ereignis angeben, das bereits in der Client-Bibliothek definiert ist. Klicken Sie auf **[!UICONTROL OK]**.
