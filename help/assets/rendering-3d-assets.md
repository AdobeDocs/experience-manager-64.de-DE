---
title: Rendern von 3D-Assets
seo-title: Rendern von 3D-Assets
description: Erfahren Sie, wie Sie 3D-Assets, die Sie in AEM bearbeitet und gespeichert haben, rendern, um 2D-Bilder für Ihre Webseiten zu erstellen.
seo-description: Erfahren Sie, wie Sie 3D-Assets, die Sie in AEM bearbeitet und gespeichert haben, rendern, um 2D-Bilder für Ihre Webseiten zu erstellen.
uuid: ee4d669c-72b1-4f7a-9a68-a7c6d59c7856
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5b044519-d034-4f05-98c5-f1b299a3ea37
exl-id: 3eecec53-0b39-4783-8730-f08705183941
feature: 3D-Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 78%

---

# Rendern von 3D-Assets {#rendering-d-assets}

Sie können 3D-Assets rendern, die Sie in AEM bearbeitet und gespeichert haben, um 2D-Bilder für die Verwendung in Ihren Webseiten zu erstellen.

Siehe [Bearbeiten des Seiteninhalts](/help/sites-authoring/qg-page-authoring.md#editing-your-page-content).

## Leistungsaspekte beim Rendern von 3D-Assets {#performance-considerations-when-rendering-d-assets}

Das Rendern von 3D-Inhalten benötigt erhebliche Serverressourcen wie CPU und Arbeitsspeicher. Daher kann das Rendern häufig sehr zeitaufwendig sein. Die Zeit für das Rendern variiert in Abhängigkeit von verschiedenen Faktoren neben der offensichtlichen Modellgröße und Serverhardware erheblich:

* **Renderer-Auswahl**.

   Beim Standard-Renderer von AEM 3D, Rapid Refine™, haben schnelle Renderzeiten Priorität vor Qualität. Dennoch liefert er für viele Anwendungen qualitativ hochwertige Ergebnisse. Renderer, die von Drittanbieteranwendungen bereitgestellt werden (z. B. V-Ray™ oder NVIDIA® Mental Ray® aus Autodesk® Maya® oder Autodesk® 3ds Max®V-Ray™) sind breit konfigurierbar. Die Entscheidung über Qualität oder Leistung wird beim Entwurf der Bühnen getroffen.

* **IBL im Vergleich zur herkömmlichen Beleuchtung**.

   Dieser Aspekt hat kaum Einfluss auf den Standard-Renderer Rapid Refine. Renderer von Drittanbietern wie Mental Ray rendern IBL-Bühnen jedoch beträchtlich langsamer als die herkömmlichen Punkt- oder Spotlichter.

Der Rapid Refine-Renderer benötigt in der Regel nur wenige Minuten für das Rendern von großen Bildern. Bei Drittanbieter kommt es häufig zu Renderzeiten von vielen Minuten oder gar Stunden, wenn maximale Qualität eingestellt ist.

Umrechnungs-, Verarbeitungs- und Renderaufträge werden in die Warteschlange des Servers gestellt, um eine Überlastung des Servers zu vermeiden. In der Kartenansicht ist auf den zuletzt geladenen Assets die Meldung „Auf Rendern warten… “ zu sehen. Sie weist darauf hin, dass zunächst andere Verarbeitungs- oder Renderaufträge abgeschlossen werden müssen, bevor der aktuelle Renderauftrag beginnen kann.

>[!NOTE]
>
>Ein 3D-Asset wird immer mit den ursprünglichen Materialien gerendert – unabhängig davon, welche Materialien in der interaktiven AEM 3D-Ansicht angezeigt werden. Diese Funktion gilt für den integrierten Renderer Rapid Refine und alle nativen Renderer.

**So rendern Sie 3D-Assets**:

1. Öffnen Sie ein 3D-Asset zur Anzeige.

   Siehe [Anzeigen von 3D-Assets](viewing-3d-assets.md).

1. Tippen Sie in Adobe Experience Manager auf der Seite **[!UICONTROL Navigation]** auf **[!UICONTROL Assets]**.
1. Tippen Sie oben rechts auf der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** auf **[!UICONTROL Kartenansicht]**.
1. Navigieren Sie zu einem 3D-Asset, das Sie rendern möchten.
1. Tippen Sie auf die Karte des 3D-Assets, um das Asset auf der Seite mit den Asset-Details zu öffnen.
1. Tippen Sie in der linken oberen Ecke der Seite auf die Dropdown-Liste und wählen Sie **[!UICONTROL Rendern]**.

   ![chlimage_1-369](assets/chlimage_1-369.png)

1. Tippen Sie in der rechten oberen Ecke der Seite mit den Asset-Details auf das Symbol **[!UICONTROL Stage Selector]** (Spotlight) und wählen Sie dann einen Anzeigenamen mit dem Hintergrund und der Beleuchtung aus, die Sie auf das 3D-Objekt anwenden möchten.

   Siehe [Informationen zu Bühnen in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

   ![chlimage_1-370](assets/chlimage_1-370.png)

   **[!UICONTROL Symbol für Bühnen-Auswahl]**

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Render]** auf der linken Seite der Asset-Details einen Renderer aus.

   Der Standard-Renderer **Rapid Refine** ist immer verfügbar. Wenn die ausgewählte Bühne ein natives Format hat, ist auch der entsprechende Drittpartei-Renderer in der Liste verfügbar und kann ausgewählt werden.

   Siehe [Informationen zu Bühnen in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

1. Gehen Sie folgendermaßen vor:

   * Geben Sie in die Felder **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** die Pixelbreite und -höhe ein, die das Bild gerendert werden soll.
   * Geben Sie im Feld **[!UICONTROL Bildname]** den Namen des gerenderten Bildes ein.
   * Geben Sie im Feld **[!UICONTROL Exportpfad]** den Pfad ein, in dem das gerenderte Bild gespeichert werden soll. Oder tippen Sie auf das Symbol **[!UICONTROL Durchsuchen]** und navigieren Sie zu einem Speicherort.
   * (Optional) Aktivieren oder deaktivieren Sie das Kontrollkästchen **[!UICONTROL Vorhandenes Bild überschreiben]e**.

1. Tippen Sie in der rechten oberen Ecke der Seite mit den Asset-Details auf das Symbol **[!UICONTROL Kamera-Auswahl]**. Wählen Sie eine Kameraansicht aus, die Sie auf das gerenderte Bild anwenden möchten.

   Die linken und rechten sowie oberen und unteren Balken sind sichtbarere Indikatoren dafür, welche Teile der Ansicht gerendert werden. Wenn die Kamera von der ausgewählten Bühne bereitgestellt wird, können Sie eine vordefinierte Kamera auswählen. 

   ![chlimage_1-371](assets/chlimage_1-371.png)

   **[!UICONTROL Symbol für Kameraauswahl]**

1. Tippen Sie auf **[!UICONTROL Renderer starten]**, um den Renderprozess zu starten.

   In der vorübergehend angezeigten Meldung wird Ihnen mitgeteilt, dass die Wiedergabe begonnen hat. Aus praktischen Gründen enthält diese Meldung auch eine Verknüpfung zum ausgewählten Ausgabeordner, damit Sie direkt darauf zugreifen können.
