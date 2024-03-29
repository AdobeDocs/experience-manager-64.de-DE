---
title: Kaskadierende Metadaten
description: In diesem Artikel wird die Definition kaskadierender Metadaten für Assets beschrieben.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: ea6187e8-075d-4666-afc5-01c97deccc11
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 42%

---

# Kaskadierende Metadaten {#cascading-metadata}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Artikel wird die Definition kaskadierender Metadaten für Assets beschrieben.

>[!CAUTION]
>
>Kaskadierende Metadaten werden für Inhaltsfragmente nicht unterstützt.

Beim Erfassen der Metadateninformationen eines Assets stellen Benutzer Informationen in den verschiedenen verfügbaren Feldern bereit. Sie können bestimmte Metadatenfelder oder Feldwerte anzeigen, die von den in den anderen Feldern ausgewählten Optionen abhängen. Eine solche bedingte Anzeige von Metadaten wird als kaskadierende Metadaten bezeichnet. Mit anderen Worten, Sie können eine Abhängigkeit zwischen einem bestimmten Metadatenfeld/-wert und einem oder mehreren Feldern und/oder deren Werten erstellen.

Verwenden Sie Metadatenschemata, um Regeln für die Anzeige kaskadierender Metadaten zu definieren. Wenn Ihr Metadatenschema beispielsweise ein Feld vom Typ Asset enthält, können Sie einen geeigneten Satz von Feldern definieren, die je nach ausgewähltem Asset-Typ angezeigt werden sollen.

Im Folgenden finden Sie einige Anwendungsfälle, für die Sie kaskadierende Metadaten definieren können:

* Wenn der Benutzerstandort erforderlich ist, zeigen Sie relevante Stadtnamen basierend auf der Wahl des Benutzers für Land und Bundesland an.
* Laden Sie relevante Markennamen in eine Liste, die auf der Produktkategorie des Benutzers basiert.
* Schalten Sie die Sichtbarkeit eines bestimmten Felds basierend auf dem in einem anderen Feld angegebenen Wert um. Zeigen Sie beispielsweise separate Felder für die Versandadresse an, wenn der Benutzer die Sendung an einer anderen Adresse erhalten möchte.
* Legen Sie ein Feld basierend auf dem in einem anderen Feld angegebenen Wert als Pflichtfeld fest.
* Ändern Sie die für ein bestimmtes Feld angezeigten Optionen basierend auf dem in einem anderen Feld angegebenen Wert.
* Legen Sie den Standard-Metadatenwert in einem bestimmten Feld basierend auf dem in einem anderen Feld angegebenen Wert fest.

## Erstellen kaskadierender Metadaten in [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Stellen Sie sich ein Szenario vor, in dem kaskadierende Metadaten basierend auf dem ausgewählten Asset-Typ angezeigt werden sollen. Beispiele

* Zeigen Sie für ein Video geeignete Felder wie Format, Codec, Dauer usw. an.
* Zeigen Sie für ein Word- oder PDF-Dokument Felder wie Seitenzahl, Autor usw. an.

Zeigen Sie unabhängig vom ausgewählten Asset-Typ die Copyright-Informationen als erforderliches Feld an.

1. Tippen oder klicken Sie auf das [!DNL Experience Manager]-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Schemas]**.
1. Wählen Sie auf der Seite **[!UICONTROL Schemaformulare]** ein Schemaformular aus und tippen oder klicken Sie dann in der Symbolleiste auf **[!UICONTROL Bearbeiten]**, um das Schema zu bearbeiten.

   ![Auswahlformular](assets/select_form.png)

1. (Optional) Erstellen Sie im Metadatenschema-Editor ein neues Feld, das an Bedingungen geknüpft werden soll. Geben Sie einen Namen und einen Eigenschaftspfad im **[!UICONTROL Einstellungen]** Registerkarte.

   Um eine neue Registerkarte zu erstellen, tippen/klicken Sie auf **[!UICONTROL +]** , um eine Registerkarte hinzuzufügen und anschließend ein Metadatenfeld hinzuzufügen.

   ![Registerkarte hinzufügen](assets/add_tab.png)

1. Fügen Sie ein Dropdown-Feld für den Asset-Typ hinzu. Geben Sie einen Namen und einen Eigenschaftspfad im **[!UICONTROL Einstellungen]** Registerkarte. Fügen Sie eine optionale Beschreibung hinzu.

   ![Asset-Typ-Field](assets/asset_type_field.png)

1. Schlüssel-Wert-Paare sind die Optionen, die einem Formularbenutzer zur Verfügung gestellt werden. Sie können die Schlüssel-Wert-Paare entweder manuell oder aus einer JSON-Datei bereitstellen.

   * Um die Werte manuell anzugeben, wählen Sie **[!UICONTROL Manuelles Hinzufügen]** und tippen/klicken Sie **[!UICONTROL Auswahl hinzufügen]** und geben Sie den Optionstext und -wert an. Geben Sie beispielsweise die Asset-Typen Video, PDF, Word und Bild an.
   * Um die Werte dynamisch aus einer JSON-Datei abzurufen, wählen Sie **[!UICONTROL Über JSON-Pfad hinzufügen]** und geben Sie den Pfad der JSON-Datei an. [!DNL Experience Manager] ruft die Schlüssel-Wert-Paare in Echtzeit ab, wenn das Formular dem Anwender angezeigt wird.

   Beide Optionen schließen sich gegenseitig aus. Sie können die Optionen nicht aus einer JSON-Datei importieren und manuell bearbeiten.

   ![Auswahlmöglichkeiten hinzufügen](assets/add_choice.png)

   >[!NOTE]
   >
   >Wenn Sie eine JSON-Datei hinzufügen, werden die Schlüssel-Wert-Paare nicht im Metadatenschema-Editor angezeigt, sind jedoch im veröffentlichten Formular verfügbar.

   >[!NOTE]
   >
   >Wenn Sie Auswahlmöglichkeiten hinzufügen und auf das Dropdown-Feld klicken, wird die Benutzeroberfläche verzerrt dargestellt und das Löschsymbol für die Auswahlmöglichkeiten funktioniert nicht mehr. Wenn Sie die Optionen zum Dropdown-Menü hinzufügen, klicken Sie erst wieder in das Dropdown-Menü, wenn Sie die Änderungen speichern. Wenn dieses Problem auftritt, speichern Sie das Schema und öffnen Sie es erneut, um die Bearbeitung fortzusetzen.

1. (Optional) Fügen Sie die anderen erforderlichen Felder hinzu. Beispielsweise das Format, den Codec und die Dauer für das Asset-Typ-Video.

   Fügen Sie auf ähnliche Weise abhängige Felder für andere Asset-Typen hinzu. Fügen Sie bei Dokumenten-Assets wie PDF- und Word-Dateien beispielsweise die Felder „Seitenanzahl“ und „Autor“ hinzu.

   ![Videoabhängigkeitsfelder](assets/video_dependent_fields.png)

1. Um eine Abhängigkeit zwischen dem Feld „Asset-Typ“ und anderen Feldern zu erstellen, wählen Sie das abhängige Feld aus und öffnen Sie die Registerkarte **[!UICONTROL Regeln]**.

   ![Abhängigkeitsfeld auswählen](assets/select_dependentfield.png)

1. Wählen Sie unter **[!UICONTROL Anforderung]** die Option **[!UICONTROL Erforderlich, basierend auf neuer Regel]** aus.
1. Tippen/Klicken Sie auf **[!UICONTROL Regel hinzufügen]** und wählen Sie das Feld **[!UICONTROL Asset-Typ]**, um eine Abhängigkeit zu erstellen. Wählen Sie auch den Feldwert, auf dessen Grundlage die Abhängigkeit erstellt werden soll. Wählen Sie in diesem Fall **[!UICONTROL Video]** aus. Tippen/Klicken Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu speichern.

   ![Regel festlegen](assets/define_rule.png)

   >[!NOTE]
   >
   >Dropdown-Listen mit manuell vordefinierten Werten können mit Regeln verwendet werden. Dropdown-Menüs mit konfiguriertem JSON-Pfad können nicht mit Regeln verwendet werden, die vordefinierte Werte verwenden, um Bedingungen anzuwenden. Wenn die Werte zur Laufzeit aus einer JSON-Datei geladen werden, ist es nicht möglich, vordefinierte Regeln anzuwenden.

1. Wählen Sie unter **[!UICONTROL Sichtbarkeit]** die Option **[!UICONTROL Sichtbar, basierend auf neuer Regel]** aus.

1. Tippen/Klicken Sie auf **[!UICONTROL Regel hinzufügen]** und wählen Sie das Feld **[!UICONTROL Asset-Typ]**, um eine Abhängigkeit zu erstellen. Wählen Sie auch den Feldwert, auf dessen Grundlage die Abhängigkeit erstellt werden soll. Wählen Sie in diesem Fall **[!UICONTROL Video]** aus. Tippen/Klicken Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu speichern.

   ![Sichtbarkeitsregel festlegen](assets/define_visibilityrule.png)

   >[!NOTE]
   >
   >Durch Tippen/Klicken auf Leerzeichen (oder einen anderen Ort als Werte) werden die Werte zurückgesetzt. In diesem Fall müssen Sie sie erneut auswählen.

   >[!NOTE]
   >
   >Sie können die Bedingungen **[!UICONTROL Anforderung]** und **[!UICONTROL Sichtbarkeit]** unabhängig voneinander anwenden.

1. Erstellen Sie auf ähnliche Weise eine Abhängigkeit zwischen dem Wert Video im Feld Asset-Typ und anderen Feldern wie Codec und Dauer.
1. Wiederholen Sie die Schritte, um eine Abhängigkeit zwischen Dokumenten-Assets (PDF und Word) im Feld **[!UICONTROL Asset-Typ]** und Feldern wie Seitenzahl und Autor zu erstellen.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Wenden Sie das Metadatenschema auf einen Ordner an.

1. Navigieren Sie zu dem Ordner, auf den Sie das Metadatenschema angewendet haben, und öffnen Sie die Eigenschaftenseite eines Assets. Je nach Ihrer Auswahl im Feld Asset-Typ werden relevante kaskadierende Metadatenfelder angezeigt.

   ![Kaskadierende Metadaten für Video-Assets](assets/video_asset.png)

   *Abbildung: Kaskadierende Metadaten für Video-Assets*

   ![Kaskadierende Metadaten für Dokumenten-Assets](assets/doc_type_fields.png)

   *Abbildung: Kaskadierende Metadaten für Dokumenten-Assets*
