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
source-git-commit: 8b83be510a67fadaa666f2ba96fbb3fc82b9cb3d

---


# Inhaltsfragmentmodelle {#content-fragment-models}

>[!CAUTION]
>
>Einige Inhaltsfragmentfunktionen erfordern die Anwendung von [AEM 6.4 Service Pack 2 (6.4.2.0) oder höher](../release-notes/sp-release-notes.md).

Inhaltsfragmentmodelle definieren die Struktur des Inhalts für Ihre [Inhaltsfragmente](content-fragments.md).

## Aktivieren von Inhaltsfragmentmodellen {#enable-content-fragment-models}

>[!CAUTION]
>
>If you do not enable **[!UICONTROL Content Fragment Models]**, the **[!UICONTROL Create]** option will not be available for creating new models.

Gehen Sie wie folgt vor, um Inhaltsfragmentmodelle zu aktivieren:

* Aktivieren Sie die Verwendung von Inhaltsfragmentmodellen im Konfigurations-Manager
* Wenden Sie die Konfiguration auf Ihren Assets-Ordner an

### Aktivieren Sie Inhaltsfragmentmodelle im Konfigurations-Manager {#enable-content-fragment-models-in-configuration-manager}

Um [ein neues Inhaltsfragmentmodell zu erstellen](#creating-a-content-fragment-model), **müssen** Sie Inhaltsfragmentmodelle zunächst über den Konfigurations-Manager aktivieren:

1. Navigieren Sie zu **[!UICONTROL Werkzeuge]**, **[!UICONTROL Allgemein]** und öffnen Sie dann den **[!UICONTROL Konfigurationsbrowser]**.
1. Wählen Sie den entsprechenden Speicherort für Ihre Webseite aus.
1. Use **[!UICONTROL Create]** to open the dialog, where you:

   1. Geben Sie einen **[!UICONTROL Titel]** an.
   1. Select **[!UICONTROL Content Fragment Models]** to enable their use.
   ![cfm-6420-09](assets/cfm-6420-09.png)

1. Select **[!UICONTROL Create]** to save the definition.

### Wenden Sie die Konfiguration auf Ihren Assets-Ordner an {#apply-the-configuration-to-your-assets-folder}

Wenn die Konfiguration **[!UICONTROL Global]** für Inhaltsfragmentmodelle aktiviert wurde, können alle von Benutzern erstellten Modelle in jedem beliebigen Assets-Ordner verwendet werden.

Um andere Konfigurationen (also außer globale) mit einem vergleichbaren Asset-Ordner zu verwenden, müssen Sie die Verbindung definieren. Dies geschieht mithilfe der **[!UICONTROL Konfiguration]** auf der Registerkarte **[!UICONTROL Cloud Services]** der **[!UICONTROL Ordnereigenschaften]** des entsprechenden Ordners.

## Erstellen eines Inhaltsfragmentmodells {#creating-a-content-fragment-model}

1. Navigate to **[!UICONTROL Tools]**, **[!UICONTROL Assets]**, then open **[!UICONTROL Content Fragment Models]**.
1. Navigieren Sie zu dem entsprechenden Ordner für Ihre [Konfiguration](#enable-content-fragment-models).
1. Öffnen Sie den Assistenten über **[!UICONTROL Erstellen]**.

   >[!CAUTION]
   >
   >Wenn die [Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde](#enable-content-fragment-models), ist die Option **Erstellen** nicht verfügbar.

1. Geben Sie den **[!UICONTROL Modelltitel]** an. Sie können bei Bedarf auch eine **[!UICONTROL Beschreibung]** hinzufügen.

   ![cfm-6420-10](assets/cfm-6420-10.png)

1. Speichern Sie das leere Modell über **[!UICONTROL Erstellen]**. Eine Benachrichtigung zeigt an, dass der Vorgang erfolgreich abgeschlossen wurde. Daraufhin können Sie das Modell über die Option **[!UICONTROL Öffnen]** direkt bearbeiten oder über **[!UICONTROL Fertig]** zur Konsole zurückkehren.

## Definieren Ihres Inhaltsfragmentmodells {#defining-your-content-fragment-model}

Das Inhaltsfragmentmodell definiert effektiv die Struktur des daraus entstehenden Inhaltsmodells. Mit dem Modell-Editor können Sie die erforderlichen Felder hinzufügen und konfigurieren:

>[!CAUTION]
>
>Die Bearbeitung eines vorhandenen Inhaltsfragmentmodells kann sich auf abhängige Fragmente auswirken.

1. Navigate to **[!UICONTROL Tools]**, **[!UICONTROL Assets]**, then open **[!UICONTROL Content Fragment Models]**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Öffnen Sie das zu **[!UICONTROL bearbeitende]** Modell; nutzen Sie dazu entweder die entsprechende Schnellaktion oder wählen Sie das Modell und anschließend die Aktion aus der Anwendungssymbolleiste aus.

   Wenn das Modell geöffnet ist, finden Sie Folgendes im Editor:

   * Links: bereits definierte Felder
   * rechts: **[!UICONTROL Datentypen]**, die zum Erstellen von Feldern verfügbar sind (und **[!UICONTROL Eigenschaften]** für die Verwendung nach Erstellung der Felder)
   >[!NOTE]
   >
   >When a field is **Required**, the **Label** indicated in the left pane will be marked with an asterix (**&amp;ast;**).

   ![cfm-6420-12](assets/cfm-6420-12.png)

1. **So fügen Sie ein Feld hinzu**

   * Ziehen Sie einen erforderlichen Datentyp an die entsprechende Stelle für ein Feld:
   ![cfm-6420-12](assets/cfm-6420-11.png)

   * Wenn ein Feld zum Modell hinzugefügt wurde, werden im rechten Fenster die **Eigenschaften** angezeigt, die für diesen speziellen Datentyp definiert werden können. Hier können Sie festlegen, was für dieses Feld erforderlich ist. Beispiel:
   ![cfm-6420-13](assets/cfm-6420-13.png)

1. **So entfernen Sie ein Feld**

   Wählen Sie das entsprechende Feld aus und klicken/tippen Sie auf das Papierkorb-Symbol. Sie werden aufgefordert, den Vorgang zu bestätigen.

   ![cf-32](assets/cf-32.png)

1. After adding all required fields, and defining the properties, use **[!UICONTROL Save]** to persist the definition. Beispiel:

   ![cfm-6420-14](assets/cfm-6420-14.png)

## Löschen eines Inhaltsfragmentmodells {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>Das Löschen eines Inhaltsfragmentmodells wirkt sich unter Umständen auf abhängige Fragmente aus.

So löschen Sie ein Inhaltsfragmentmodell:

1. Navigate to **[!UICONTROL Tools]**, **[!UICONTROL Assets]**, then open **[!UICONTROL Content Fragment Models]**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließend die Option **[!UICONTROL Löschen]** aus der Anwendungssymbolleiste aus.

   >[!NOTE]
   >
   >Wenn es Verweise auf das Modell gibt, wird Ihnen ein Warnhinweis angezeigt. Ergreifen Sie die entsprechenden Maßnahmen.

## Veröffentlichen eines Inhaltsfragmentmodells {#publishing-a-content-fragment-model}

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

So veröffentlichen Sie ein Inhaltsfragmentmodell:

1. Navigate to **[!UICONTROL Tools]**, **[!UICONTROL Assets]**, then open **[!UICONTROL Content Fragment Models]**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **[!UICONTROL Löschen]** aus der Anwendungssymbolleiste aus.

   >[!NOTE]
   >
   >Wenn Sie Inhaltsfragmente veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

