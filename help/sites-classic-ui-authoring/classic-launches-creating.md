---
title: Erstellen von Launches
seo-title: Creating Launches
description: Erstellen Sie einen Launch, um die Aktualisierung einer neuen Version bestehender Web-Seiten für die zukünftige Aktivierung zu aktivieren. Wenn Sie einen Launch erstellen, können Sie einen Titel und die Quellseite angeben.
seo-description: Create a launch to enable the updating of a new version of existing web pages for future activation. When you create a Launch, you specify a title and the source page.
uuid: e67608a9-e6c9-42f3-bd1d-63a5fa87ae18
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 48826f03-6731-49c5-a6c5-6e2fb718f912
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 2f5c022e-bd98-4912-9409-d08137a1caf1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 66%

---

# Erstellen von Launches{#creating-launches}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erstellen Sie einen Launch, um die Aktualisierung einer neuen Version bestehender Web-Seiten für die zukünftige Aktivierung zu aktivieren. Wenn Sie einen Launch erstellen, können Sie einen Titel und die Quellseite angeben:

* Der Titel wird im **Sidekick** angezeigt, wo Autoren ihn bearbeiten können.
* Die untergeordneten Seiten der Quellseiten werden standardmäßig in den Launch eingeschlossen. Sie können bei Bedarf nur die Quellseite verwenden.
* Standardmäßig [Live Copy](/help/sites-administering/msm.md) aktualisiert die Launch-Seiten automatisch, wenn sich die Quellseiten ändern. Zur Vermeidung automatischer Änderungen können Sie festlegen, dass eine statische Kopie erstellt wird.

Optional können Sie das **Launch-Datum** (und die Uhrzeit) für die Bewerbung und Aktivierung der Launch-Seiten angeben. Das **Launch-Datum** funktioniert allerdings nur in Kombination mit der Kennzeichnung **Produktionsbereit** (siehe [Bearbeiten einer Launch-Konfiguration](/help/sites-classic-ui-authoring/classic-launches-editing.md#editing-a-launch-configuration)). Damit die Aktionen automatisch erfolgen, muss beides festgelegt werden.

## Erstellen eines Launches {#creating-a-launch}

Mit dem folgenden Verfahren wird ein Launch erstellt.

1. Öffnen Sie die Verwaltungsseite für die Website ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin)).
1. Klicken **Neu...** then **Neuer Launch..**.
1. Im **Launch erstellen** -Dialogfeld Werte für die folgenden Eigenschaften angeben:

   * **Launch-Titel**: Der Name des Launches. Der Name sollte für Autoren aussagekräftig sein.
   * **Quellseite**: Der Pfad zu der Seite, für die der Launch erstellt werden soll. Standardmäßig sind alle untergeordneten Seiten eingeschlossen.
   * **Unterseiten ausschließen**: Wählen Sie diese Option, um den Launch nur für die Quellseite und nicht für die untergeordneten Seiten zu erstellen. Standardmäßig ist diese Option nicht aktiviert. 
   * **Synchronisieren**: Wählen Sie diese Option, um den Inhalt von Launch-Seiten automatisch zu aktualisieren, wenn die Quellseiten sich ändern. Dies wird erreicht, indem der Start zu einem [Live Copy](/help/sites-administering/msm.md).
   * **Launch-Datum**: Das Datum und die Uhrzeit für die Aktivierung der Launch-Kopie (abhängig von der Markierung **Produktionsbereit**. Siehe [Launches: Reihenfolge von Ereignissen](/help/sites-authoring/launches.md#launches-the-order-of-events)).

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Klicken Sie auf **Erstellen**.

## Löschen von Launches {#deleting-a-launch}

Sie können einen Launch auch löschen.

1. Wählen Sie den erforderlichen Launch in der [Launch-Konsole](/help/sites-classic-ui-authoring/classic-launches.md) aus.
1. Klicken Sie auf **Löschen**. Der Vorgang muss bestätigt werden:

   ![chlimage_1-100](assets/chlimage_1-100.png)

   >[!CAUTION]
   >
   >Beim Löschen von verschachtelten Launches sollten Sie zuerst die niedrigeren Ebenen löschen.
