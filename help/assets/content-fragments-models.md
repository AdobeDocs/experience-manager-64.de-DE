---
title: Inhaltsfragmentmodelle
seo-title: Content Fragment Models
description: Inhaltsfragmentmodelle werden verwendet, um Inhaltsfragmente mit strukturiertem Inhalt zu erstellen.
seo-description: Content Fragment Models are used to create content fragments with structured content.
uuid: 59176a32-1255-4a46-ad00-344bde843ea6
content-type: reference
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 45e67357-4524-4d25-b5f1-21182b8e803c
exl-id: 39ed07ec-54a6-4387-8435-e891726c411c
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 68%

---

# Inhaltsfragmentmodelle {#content-fragment-models}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!CAUTION]
>
>Einige Inhaltsfragmentfunktionen erfordern die Anwendung von [AEM 6.4 Service Pack 2 (6.4.2.0 oder höher)](../release-notes/sp-release-notes.md).

Inhaltsfragmentmodelle definieren die Struktur des Inhalts für Ihre [Inhaltsfragmente](content-fragments.md).

## Aktivieren von Inhaltsfragmentmodellen   {#enable-content-fragment-models}

>[!CAUTION]
>
>Wenn Sie nicht aktivieren **[!UICONTROL Inhaltsfragmentmodelle]**, die **[!UICONTROL Erstellen]** ist nicht für die Erstellung neuer Modelle verfügbar.

Um Inhaltsfragmentmodelle zu aktivieren, müssen Sie:

* Aktivieren der Verwendung von Inhaltsfragmentmodellen im Konfigurationsmanager
* Wenden Sie die Konfiguration auf Ihren Assets-Ordner an.

### Aktivieren Sie Inhaltsfragmentmodelle in Configuration Manager   {#enable-content-fragment-models-in-configuration-manager}

Um [ein neues Inhaltsfragmentmodell zu erstellen](#creating-a-content-fragment-model), **müssen** Sie Inhaltsfragmentmodelle zunächst über Configuration Manager aktivieren:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** und öffnen Sie dann den **[!UICONTROL Konfigurations-Browser]**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurations-Browser.](/help/sites-administering/configurations.md)
1. Wählen Sie den entsprechenden Speicherort für Ihre Web-Seite aus.
1. Öffnen Sie über **[!UICONTROL Erstellen]** das Dialogfeld, in dem Sie:

   1. einen **[!UICONTROL Titel]** angeben,
   1. **[!UICONTROL Inhaltsfragmentmodelle]** auswählen, um deren Verwendung zu aktivieren.

   ![cfm-6420-09](assets/cfm-6420-09.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Definition zu speichern.

### Anwenden der Konfiguration auf Ihren Assets-Ordner {#apply-the-configuration-to-your-assets-folder}

Wenn die Konfiguration **[!UICONTROL Global]** für Inhaltsfragmentmodelle aktiviert wurde, können alle von Benutzern erstellten Modelle in jedem beliebigen Assets-Ordner verwendet werden.

Um eine andere Konfiguration (d. h. nicht „Global“) mit einem vergleichbaren Assets-Ordner zu verwenden, müssen Sie die Verbindung definieren. Dies geschieht mithilfe der **[!UICONTROL Konfiguration]** auf der Registerkarte **[!UICONTROL Cloud Services]** der **[!UICONTROL Ordnereigenschaften]** des entsprechenden Ordners.

## Erstellen eines Inhaltsfragmentmodells {#creating-a-content-fragment-model}

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** und öffnen Sie dann **[!UICONTROL Inhaltsfragmentmodelle]**.
1. Navigieren Sie zu dem Ordner, der Ihrer [Konfiguration](#enable-content-fragment-models).
1. Verwendung **[!UICONTROL Erstellen]** , um den Assistenten zu öffnen.

   >[!CAUTION]
   >
   >Wenn die [Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde](#enable-content-fragment-models), ist die Option **Erstellen** nicht verfügbar.

1. Geben Sie den **[!UICONTROL Modell-Titel]** an. Sie können bei Bedarf auch eine **[!UICONTROL Beschreibung]** hinzufügen.

   ![cfm-6420-10](assets/cfm-6420-10.png)

1. Verwendung **[!UICONTROL Erstellen]** , um das leere Modell zu speichern. Eine Meldung weist auf den Erfolg der Aktion hin. Sie können **[!UICONTROL Öffnen]** das Modell sofort bearbeiten oder **[!UICONTROL Fertig]** , um zur Konsole zurückzukehren.

## Definieren des Inhaltsfragmentmodells {#defining-your-content-fragment-model}

Das Inhaltsfragmentmodell definiert effektiv die Struktur der resultierenden Inhaltsfragmente. Mithilfe des Modell-Editors können Sie die erforderlichen Felder hinzufügen und konfigurieren:

>[!CAUTION]
>
>Die Bearbeitung eines vorhandenen Inhaltsfragmentmodells kann sich auf abhängige Fragmente auswirken.

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** und öffnen Sie dann **[!UICONTROL Inhaltsfragmentmodelle]**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Öffnen Sie das zu **[!UICONTROL bearbeitende]** Modell; nutzen Sie dazu entweder die entsprechende Schnellaktion oder wählen Sie das Modell und anschließend die Aktion aus der Symbolleiste aus.

   Nach dem Öffnen zeigt der Modell-Editor Folgendes an:

   * left: bereits definierte Felder
   * Rechts: verfügbare **[!UICONTROL Datentypen]** für das Erstellen von Feldern (und **[!UICONTROL Eigenschaften]**, die für erstellte Felder verwendet werden können)

   >[!NOTE]
   >
   >Wenn ein Feld **Erforderlich**, die **Titel** im linken Bereich angezeigt wird, wird mit einem Sternchen (**&amp;ast;**).

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
>Das Löschen eines Inhaltsfragmentmodells kann sich auf abhängige Fragmente auswirken.

So löschen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** und öffnen Sie dann **[!UICONTROL Inhaltsfragmentmodelle]**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließend die Option **[!UICONTROL Löschen]** aus der Symbolleiste aus.

   >[!NOTE]
   >
   >Wenn auf das Modell verwiesen wird, wird eine Warnung angezeigt. Ergreifen Sie entsprechende Maßnahmen.

## Veröffentlichen eines Inhaltsfragmentmodells {#publishing-a-content-fragment-model}

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

So veröffentlichen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** und öffnen Sie dann **[!UICONTROL Inhaltsfragmentmodelle]**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **[!UICONTROL Veröffentlichen]** aus der Symbolleiste aus.

   >[!NOTE]
   >
   >Wenn Sie Inhaltsfragmente veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.
