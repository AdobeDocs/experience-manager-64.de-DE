---
title: Inhaltsfragmentmodelle
seo-title: Inhaltsfragmentmodelle
description: Inhaltsfragmentmodelle werden verwendet, um Inhaltsfragmente mit strukturierten Inhalten zu erstellen.
seo-description: Inhaltsfragmentmodelle werden verwendet, um Inhaltsfragmente mit strukturierten Inhalten zu erstellen.
uuid: 59176a32-1255-4a46-ad00-344bde843ea6
content-type: reference
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 45e67357-4524-4d25-b5f1-21182b8e803c
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 91%

---


# Inhaltsfragmentmodelle {#content-fragment-models}

>[!CAUTION]
>
>Einige Inhaltsfragment-Funktionen erfordern die Anwendung von [AEM 6.4 Service Pack 2 (6.4.2.0) oder höher](../release-notes/sp-release-notes.md).

Inhaltsfragmentmodelle definieren die Struktur des Inhalts für Ihre [Inhaltsfragmente](content-fragments.md).

## Aktivieren von Inhaltsfragmentmodellen   {#enable-content-fragment-models}

>[!CAUTION]
>
>If you do not enable **[!UICONTROL Content Fragment Models]**, the **[!UICONTROL Create]** option will not be available for creating new models.

Gehen Sie wie folgt vor, um Inhaltsfragmentmodelle zu aktivieren:

* Aktivieren Sie die Verwendung von Inhaltsfragmentmodellen im Konfigurations-Manager
* Wenden Sie die Konfiguration auf Ihren Assets-Ordner an

### Aktivieren Sie Inhaltsfragmentmodelle in Configuration Manager   {#enable-content-fragment-models-in-configuration-manager}

Um [ein neues Inhaltsfragmentmodell zu erstellen](#creating-a-content-fragment-model), **müssen** Sie Inhaltsfragmentmodelle zunächst über Configuration Manager aktivieren:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** und öffnen Sie dann den **[!UICONTROL Konfigurations-Browser]**.
   * See the [Configuration Browser documentation](/help/sites-administering/configurations.md) for more information.
1. Wählen Sie den entsprechenden Speicherort für Ihre Web-Seite aus.
1. Öffnen Sie über **[!UICONTROL Erstellen]** das Dialogfeld, in dem Sie:

   1. einen **[!UICONTROL Titel]** angeben,
   1. **[!UICONTROL Inhaltsfragmentmodelle]** auswählen, um deren Verwendung zu aktivieren.

   ![cfm-6420-09](assets/cfm-6420-09.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Definition zu speichern.

### Wenden Sie die Konfiguration auf Ihren Assets-Ordner an {#apply-the-configuration-to-your-assets-folder}

Wenn die Konfiguration **[!UICONTROL Global]** für Inhaltsfragmentmodelle aktiviert wurde, können alle von Benutzern erstellten Modelle in jedem beliebigen Assets-Ordner verwendet werden.

Um eine andere Konfiguration (d. h. nicht „Global“) mit einem vergleichbaren Assets-Ordner zu verwenden, müssen Sie die Verbindung definieren. Dies geschieht mithilfe der **[!UICONTROL Konfiguration]** auf der Registerkarte **[!UICONTROL Cloud Services]** der **[!UICONTROL Ordnereigenschaften]** des entsprechenden Ordners.

## Erstellen eines Inhaltsfragmentmodells {#creating-a-content-fragment-model}

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** und öffnen Sie dann **[!UICONTROL Inhaltsfragmentmodelle]**.
1. Navigieren Sie zu dem entsprechenden Ordner für Ihre [Konfiguration](#enable-content-fragment-models).
1. Öffnen Sie den Assistenten über **[!UICONTROL Erstellen]**.

   >[!CAUTION]
   >
   >Wenn die [Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde](#enable-content-fragment-models), ist die Option **Erstellen** nicht verfügbar.

1. Geben Sie den **[!UICONTROL Modelltitel]** an. Sie können bei Bedarf auch eine **[!UICONTROL Beschreibung]** hinzufügen.

   ![cfm-6420-10](assets/cfm-6420-10.png)

1. Speichern Sie das leere Modell über **[!UICONTROL Erstellen]**. Eine Benachrichtigung zeigt an, dass der Vorgang erfolgreich abgeschlossen wurde. Daraufhin können Sie das Modell über die Option **[!UICONTROL Öffnen]** direkt bearbeiten oder über **[!UICONTROL Fertig]** zur Konsole zurückkehren.

## Definieren des Inhaltsfragmentmodells   {#defining-your-content-fragment-model}

Das Inhaltsfragmentmodell definiert effektiv die Struktur des daraus entstehenden Inhaltsmodells. Mit dem Modell-Editor können Sie die erforderlichen Felder hinzufügen und konfigurieren:

>[!CAUTION]
>
>Die Bearbeitung eines vorhandenen Inhaltsfragmentmodells kann sich auf abhängige Fragmente auswirken.

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** und öffnen Sie dann **[!UICONTROL Inhaltsfragmentmodelle]**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Öffnen Sie das zu **[!UICONTROL bearbeitende]** Modell; nutzen Sie dazu entweder die entsprechende Schnellaktion oder wählen Sie das Modell und anschließend die Aktion aus der Anwendungssymbolleiste aus.

   Wenn das Modell geöffnet ist, finden Sie Folgendes im Editor:

   * Links: bereits definierte Felder
   * Rechts: verfügbare **[!UICONTROL Datentypen]** für das Erstellen von Feldern (und **[!UICONTROL Eigenschaften]**, die für erstellte Felder verwendet werden können)

   >[!NOTE]
   >
   >When a field is **Required**, the **Label** indicated in the left pane will be marked with an asterix (**&amp;ast;**).

   ![cfm-6420-12](assets/cfm-6420-12.png)

1. **So fügen Sie ein Feld hinzu**

   * Ziehen Sie einen erforderlichen Datentyp an die entsprechende Stelle für ein Feld:

   ![cfm-6420-11](assets/cfm-6420-11.png)

   * Wenn ein Feld zum Modell hinzugefügt wurde, werden im rechten Fenster die **Eigenschaften** angezeigt, die für diesen speziellen Datentyp definiert werden können. Hier können Sie festlegen, was für dieses Feld erforderlich ist. Beispiel:

   ![cfm-6420-13](assets/cfm-6420-13.png)

1. **So entfernen Sie ein Feld**

   Wählen Sie das entsprechende Feld aus und klicken/tippen Sie auf das Papierkorb-Symbol. Sie werden aufgefordert, den Vorgang zu bestätigen.

   ![cf-32](assets/cf-32.png)

1. Wenn Sie alle erforderlichen Felder festgelegt und deren Eigenschaften definiert haben, speichern Sie die Definition über **[!UICONTROL Speichern]**. Beispiel:

   ![cfm-6420-14](assets/cfm-6420-14.png)

## Löschen eines Inhaltsfragmentmodells {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>Das Löschen eines Inhaltsfragmentmodells wirkt sich unter Umständen auf abhängige Fragmente aus.

So löschen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** und öffnen Sie dann **[!UICONTROL Inhaltsfragmentmodelle]**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließend die Option **[!UICONTROL Löschen]** aus der Anwendungssymbolleiste aus.

   >[!NOTE]
   >
   >Wenn es Verweise auf das Modell gibt, wird Ihnen ein Warnhinweis angezeigt. Ergreifen Sie die entsprechenden Maßnahmen.

## Veröffentlichen eines Inhaltsfragmentmodells   {#publishing-a-content-fragment-model}

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

So veröffentlichen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** und öffnen Sie dann **[!UICONTROL Inhaltsfragmentmodelle]**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **[!UICONTROL Löschen]** aus der Anwendungssymbolleiste aus.

   >[!NOTE]
   >
   >Wenn Sie Inhaltsfragmente veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

