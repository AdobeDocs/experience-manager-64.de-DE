---
title: Verwenden eines Formulardatenmodells
seo-title: Use form data model
description: Erfahren Sie, wie Sie mit dem Formulardatenmodell adaptive Formulare und interaktive Kommunikation erstellen und verwenden können.
seo-description: Learn how to use form data model to create and work with adaptive forms and interactive communications.
uuid: 9a8bd44a-34a1-41ef-a57b-d5e3dd0a77ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 7a1bfd43-39b1-478b-a294-92c78eaebbf2
feature: Form Data Model
exl-id: 39408af6-439c-4ade-8062-155be9141dfa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1288'
ht-degree: 48%

---

# Verwenden eines Formulardatenmodells {#use-form-data-model}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

![](do-not-localize/data-integeration.png)

Mit der AEM Forms-Datenintegration können Sie unterschiedliche Backend-Datenquellen verwenden, um ein Formulardatenmodell zu erstellen, das Sie als Schema in verschiedenen adaptiven Formularen und interaktiven Kommunikationsarbeitsabläufen verwenden können. Dazu müssen Sie Datenquellen konfigurieren und ein Formulardatenmodell basierend auf Datenmodellobjekten und Diensten erstellen, die in Datenquellen verfügbar sind. Weitere Informationen finden Sie in den folgenden Themen:

* [Datenintegration für AEM Forms](/help/forms/using/data-integration.md)
* [Konfigurieren von Datenquellen](/help/forms/using/configure-data-sources.md)
* [Erstellen des Formulardatenmodells](/help/forms/using/create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell](/help/forms/using/work-with-form-data-model.md)

Ein Formulardatenmodell ist eine Erweiterung des JSON-Schemas, die Sie wie folgt verwenden können:

* [Adaptive Formulare und Fragmente erstellen](#create-af)
* [Interaktive Kommunikation und Bausteine wie Text, Liste und Bedingungsfragmente erstellen](#create-ic)
* [Vorschau für interaktive Kommunikation mit Beispieldaten](#preview-ic)
* [Adaptive Formulare und interaktive Kommunikation ausfüllen](#prefill)
* [Gesendete adaptive Formulardaten zurück in Datenquellen schreiben](#write-af)
* [Dienste über Regeln für adaptive Formulare aufrufen](#invoke-services)

## Erstellen adaptiver Formulare und Fragmente {#create-af}

Sie können [adaptive Formulare](/help/forms/using/creating-adaptive-form.md) und [adaptive Formularfragmente](/help/forms/using/adaptive-form-fragments.md) basierend auf einem Formulardatenmodell. Gehen Sie wie folgt vor, um beim Erstellen eines adaptiven Formulars oder adaptiven Formularfragments ein Formulardatenmodell zu verwenden:

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Bildschirm „Eigenschaften hinzufügen“ **[!UICONTROL Formulardatenmodell]** aus der Dropdown-Liste **[!UICONTROL Auswählen]**.

   ![create-af-1](assets/create-af-1.png)

1. Tippen Sie auf **[!UICONTROL Formulardatenmodell auswählen]**, um es zu erweitern. Alle verfügbaren Formulardatenmodelle werden aufgelistet.

   Wählen Sie ein Formulardatenmodell aus.

   ![create-af-2](assets/create-af-2.png)

1. (**Nur adaptive Formularfragmente**) Sie können ein adaptives Formularfragment erstellen, das auf nur einem Datenmodellobjekt in einem Formulardatenmodell basiert. Erweitern **[!UICONTROL Definitionen des Formulardatenmodells]** Dropdown-Liste. Es listet alle Datenmodellobjekte im angegebenen Formulardatenmodell auf. Wählen Sie ein Datenmodellobjekt aus der Liste aus.

   ![create-af-3](assets/create-af-3.png)

Sobald das auf einem Formulardatenmodell basierende adaptive Formular oder Formularfragment erstellt ist, werden Formulardatenobjekte auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des Inhaltsbrowsers im Editor für adaptive Formulare angezeigt.

>[!NOTE]
>
>Für adaptive Formularfragmente werden nur das beim Verfassen gewählte Datenmodellobjekt und die mit diesem verknüpften Datenmodellobjekte auf der Registerkarte „Datenmodellobjekte“ angezeigt.

![data-model-object-tab](assets/data-model-objects-tab.png)

Indem Sie Datenmodellobjekte in das adaptive Formular oder Fragment ziehen und dort ablegen, können Sie Formularfelder hinzufügen. Die hinzugefügten Formularfelder behalten die Metadateneigenschaften bei und binden mit den Datenmodellobjekteigenschaften. Durch die Bindung wird sichergestellt, dass die Feldwerte bei der Formularübermittlung in den entsprechenden Datenquellen aktualisiert und vorausgefüllt werden, wenn das Formular wiedergegeben wird.

## Interaktive Kommunikation erstellen {#create-ic}

Sie können eine interaktive Kommunikation basierend auf einem Formulardatenmodell erstellen, mit dem Sie die interaktive Kommunikation mit Daten aus konfigurierten Datenquellen vorbefüllen können. Darüber hinaus können die Bausteine einer interaktiven Kommunikation wie Text-, Listen- und Bedingungsdokumentfragmente auf einem Formulardatenmodell basieren.

Sie können beim Erstellen einer interaktiven Kommunikation oder eines Dokumentfragments ein Formulardatenmodell auswählen. Die folgende Abbildung zeigt die Registerkarte Allgemein des Dialogfelds Interaktive Kommunikation erstellen .

![create-ic](assets/create-ic.png)

Registerkarte &quot;Allgemein&quot;im Dialogfeld &quot;Interaktive Kommunikation erstellen&quot;

Weitere Informationen finden Sie unter:

[Interaktive Kommunikation erstellen](/help/forms/using/create-interactive-communication.md)

[Text in interaktiven Kommunikationen](/help/forms/using/texts-interactive-communications.md)

[Bedingungen in interaktiven Kommunikationen](/help/forms/using/conditions-interactive-communications.md)

[Fragmente aufführen](/help/forms/using/lists.md)

## Vorschau mit Beispieldaten {#preview-ic}

Mit dem Formulardatenmodell-Editor können Sie Beispieldaten für Datenmodellobjekte im Formulardatenmodell generieren und bearbeiten. Sie können diese Daten verwenden, um interaktive Kommunikation und adaptive Formulare in der Vorschau anzuzeigen und zu testen. Sie müssen die Beispieldaten vor der Vorschau generieren, wie beschrieben unter [Arbeiten mit einem Formulardatenmodell](/help/forms/using/work-with-form-data-model.md#sample).

So zeigen Sie eine Vorschau einer interaktiven Kommunikation mit Musterformulardaten an:

1. Navigieren Sie auf dem AEM-Server zu **[!UICONTROL Formulare > Formulare und Dokumente]**.
1. Wählen Sie eine interaktive Kommunikation und tippen Sie auf **[!UICONTROL Vorschau]** in der Symbolleiste, um **[!UICONTROL Webkanal]**, **[!UICONTROL Druckkanal]** oder **[!UICONTROL Beide Kanäle]** auszuwählen und eine Vorschau der interaktiven Kommunikation anzuzeigen.
1. Stellen Sie im Vorschau-Dialogfeld [*Kanal*] sicher, dass **[!UICONTROL Testdaten des Formulardatenmodells]** ausgewählt ist, und tippen Sie auf **[!UICONTROL Vorschau]**.

Die interaktive Kommunikation öffnet sich mit vorbefüllten Beispieldaten.

![web-preview](assets/web-preview.png)

Um ein adaptives Formular mit Beispieldaten in der Vorschau anzuzeigen, öffnen Sie das adaptive Formular im Autorenmodus und tippen Sie auf **[!UICONTROL Vorschau]**.

## Vorbefüllen mit dem Formulardatenmodelldienst {#prefill}

AEM Forms bietet einen vordefinierten Vorbefüllungs-Dienst für Formulardatenmodelle, den Sie für adaptive Formulare und interaktive Kommunikation basierend auf dem Formulardatenmodell aktivieren können. Der Vorbefüllungs-Dienst fragt Datenquellen für Datenmodellobjekte im adaptiven Formular und in der interaktiven Kommunikation ab und füllt dementsprechend beim Rendern des Formulars oder der Kommunikation Daten vorab.

Um den Vorbefüllungs-Dienst für Formulardatenmodell für ein adaptives Formular zu aktivieren, öffnen Sie die Eigenschaften des Containers für adaptive Formulare und wählen Sie **[!UICONTROL Vorfüllservice für Formulardatenmodell]** von **[!UICONTROL Vorbefüllungs-Dienst]** im Akkordeon Allgemein angezeigt. Speichern Sie anschließend die Eigenschaften.

![prefill-service](assets/prefill-service.png)

Um den Vorbefüllungs-Dienst für Formulardatenmodelle in einer interaktiven Kommunikation zu konfigurieren, können Sie im Dropdown-Liste für den Vorbefüllungs-Dienst den Vorbefüllungs-Dienst für Formulardatenmodelle während der Erstellung auswählen, oder später, indem Sie die Eigenschaften ändern.

![edit-ic-props](assets/edit-ic-props.png)

Dialogfeld &quot;Eigenschaften bearbeiten&quot;für eine interaktive Kommunikation

## Gesendete adaptive Formulardaten in Datenquellen schreiben {#write-af}

Sie können ein auf einem Formulardatenmodell basierendes Formular so konfigurieren, dass die vom Benutzer im Formular übermittelten Daten für ein Datenmodellobjekt bei der Übermittlung in dessen Datenquellen geschrieben werden. Um diesen Anwendungsfall zu erreichen, stellt AEM Forms [Übermittlungsaktion für Formulardatenmodell](/help/forms/using/configuring-submit-actions.md), ist standardmäßig nur für adaptive Formulare verfügbar, die auf einem Formulardatenmodell basieren. Durch diese Aktion werden übermittelte Daten für ein Datenmodellobjekt in dessen Datenquelle geschrieben.

Um die Übermittlungsaktion für Formulardatenmodelle zu konfigurieren, öffnen Sie die Adaptive Form-Container-Eigenschaften und wählen Sie **[!UICONTROL Übermitteln mit dem Formulardatenmodell]** aus dem Dropdown-Menü „Übermittlungsaktion“ unter dem Akkordeon „Übermittlung“. Suchen Sie dann ein Datenmodellobjekt und wählen Sie es aus dem **[!UICONTROL Name des zu sendenden Datenmodellobjekts]** Dropdown-Liste. Speichern Sie die Eigenschaften.

Beim Senden des Formulars werden die Daten für das konfigurierte Datenmodellobjekt in die entsprechende Datenquelle geschrieben.

![data-submission](assets/data-submission.png)

Sie können auch Formularanhänge mit der Objekteigenschaft des binären Datenmodells an eine Datenquelle senden. Führen Sie folgende Schritte aus, um Anlagen an eine JDBC-Datenquelle zu senden:

1. Fügen Sie dem Formulardatenmodell ein Datenmodellobjekt hinzu, das eine binäre Eigenschaft enthält.
1. Ziehen Sie im adaptiven Formular die Komponente **[!UICONTROL Dateianhang]** aus dem Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Tippen Sie auf die hinzugefügte Komponente, um sie auszuwählen, und tippen Sie dann auf ![settings_icon](assets/settings_icon.png), um den Eigenschaftenbrowser für die Komponente zu öffnen.
1. Tippen Sie im Feld „Bindungsverweis“ auf ![foldersearch_18](assets/foldersearch_18.png), navigieren Sie zur binären Eigenschaft, die Sie im Formulardatenmodell hinzugefügt haben, und wählen Sie sie aus. Konfigurieren Sie weitere Eigenschaften entsprechend.

   Tippen Sie auf ![check-button](assets/check-button.png), um die Eigenschaften zu speichern. Das Anlagenfeld ist jetzt an die binäre Eigenschaft des Formulardatenmodells gebunden.

1. Aktivieren Sie im Abschnitt Übermittlung der Eigenschaften des Containers für adaptive Formulare die Option **[!UICONTROL Übermitteln von Formularanlagen]**. Er sendet den Anhang im Feld der binären Eigenschaft bei der Formularübermittlung an die Datenquelle.

## Dienste in adaptiven Formularen mithilfe von Regeln aufrufen {#invoke-services}

In einem auf einem Formulardatenmodell basierenden adaptiven Formular können Sie [Regeln erstellen](/help/forms/using/rule-editor.md), um die im Formulardatenmodell konfigurierten Dienste aufzurufen. Für die Operation **[!UICONTROL Dienste aufrufen]** werden alle verfügbaren Dienste im Formulardatenmodell aufgelistet und Sie können die Eingabe- und Ausgabefelder für den Dienst wählen. Sie können auch die **Wert einstellen** Regeltyp zum Aufrufen eines Formulardatenmodelldienstes und zum Festlegen des Werts eines Felds auf die vom Dienst zurückgegebene Ausgabe.

Beispielsweise ruft folgende Regel einen Get-Service auf, für den die Mitarbeiter-ID als Eingabe angegeben werden muss und der die entsprechenden Werte in den Feldern für die Angehörigen-ID, den Nachnamen, den Vornamen und das Geschlecht zurückgibt.

![invoke-service](assets/invoke-service.png)

Darüber hinaus können Sie mithilfe der `guidelib.dataIntegrationUtils.executeOperation`-API ein JavaScript im Codeeditor für den Regeleditor schreiben. Informationen zur API finden Sie unter [API zum Aufrufen des Formulardatenmodelldienstes](/help/forms/using/invoke-form-data-model-services.md).
