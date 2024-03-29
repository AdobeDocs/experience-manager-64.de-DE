---
title: Optimierte Smart-Tags
description: Optimierte Smart-Tags
uuid: 4452ca05-1f20-4f80-884a-a739ae7b8b0e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
discoiquuid: c1b52aac-1eaf-4cfa-801f-77aeca0d90ea
feature: Smart Tags,Search
role: User
exl-id: 21a9f130-ea91-45bf-adc8-8a73a2a00c77
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1550'
ht-degree: 55%

---

# Optimierte Smart-Tags {#enhanced-smart-tags}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Überblick über optimierte Smart-Tags {#overview-of-enhanced-smart-tags}

Organisationen, die mit digitalen Assets arbeiten, verwenden zunehmend taxonomiegesteuertes Vokabular in Asset-Metadaten. Sie enthält im Wesentlichen eine Liste von Keywords, mit denen Mitarbeiter, Partner und Kunden häufig auf digitale Assets einer bestimmten Klasse verweisen und nach ihnen suchen. Das Tagging von Assets mit einem taxonomiegesteuerten Vokabular stellt sicher, dass sie durch Tag-basierte Suchen einfach identifiziert und abgerufen werden können.

Verglichen mit dem Vokabular natürlicher Sprachen hilft das Tagging digitaler Assets anhand einer Geschäftstaxonomie dabei, sie am Geschäft eines Unternehmens auszurichten, und stellt dabei sicher, dass nur die relevantesten Assets bei der Suche angezeigt werden.

So könnte beispielsweise ein Automobilhersteller Bilder von Autos mit Tags versehen, die die Modellnamen darstellen, sodass nur relevante Bilder angezeigt werden, wenn für das Erstellen einer Werbekampagne nach verschiedenen Modellen gesucht wird.

Damit der Smart Content Service die richtigen Tags anwendet, müssen Sie ihn so trainieren, dass er Ihre Taxonomie erkennt. Um den Dienst zu trainieren, müssen Sie zunächst einen Satz von Assets sowie Tags kuratieren, die diese Assets bestmöglich beschreiben. Wenden Sie diese Tags auf die Assets an und führen Sie einen Trainings-Workflow aus, um dem Dienst das Lernen zu erleichtern.

Sobald ein Tag trainiert wurde und bereit ist, kann der Dienst dieses Tag über einen Tagging-Workflow auf Assets anwenden.

Im Hintergrund verwendet der Smart Content Service das KI-Framework von Adobe Sensei, um seinen Bilderkennungsalgorithmus auf Ihre Tag-Struktur und Ihre Unternehmenstaxonomie zu trainieren. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden.

Smart Content Service ist ein Cloud-Service, der auf [!DNL Adobe I/O] gehostet wird. Um sie in Adobe Experience Manager verwenden zu können, muss der Systemadministrator Ihre [!DNL Experience Manager] Instanz mit [!DNL Adobe I/O].

Zusammenfassend sind hier die wichtigsten Schritte zur Verwendung des Smart Content Service aufgeführt:

* Onboarding
* Überprüfen von Assets und Tags (Taxonomiedefinition)
* Trainieren des Smart Content Service
* Automatisches Tagging

![Flussdiagramm](assets/flowchart.gif)

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Verwendung des Smart Content Service Folgendes sicher, um eine Integration in [!DNL Adobe I/O] zu erstellen:

* Es ist ein Adobe ID-Konto mit Administratorrechten für die Organisation vorhanden.
* Der Smart Content Service ist für Ihre Organisation aktiviert.

## Onboarding {#onboarding}

Der Smart Content Service ist als kostenpflichtiges Add-on für [!DNL Experience Manager] erhältlich. Nach dem Kauf erhält die bzw. der Admin Ihrer Organisation eine E-Mail mit dem Link zu [!DNL Adobe I/O].

Die bzw. der Admin kann über diesen Link den Smart Content Service mit [!DNL Experience Manager] integrieren. So integrieren Sie den Dienst in [!DNL Experience Manager] Assets, siehe [Konfigurieren von Smart-Tags](config-smart-tagging.md).

Das Onboarding ist abgeschlossen, wenn die bzw. der Admin den Service konfiguriert und Benutzende in [!DNL Experience Manager] hinzufügt.

## Überprüfen von Assets und Tags {#reviewing-assets-and-tags}

Nachdem Sie integriert wurden, sollten Sie zunächst eine Reihe von Tags identifizieren, die diese Bilder am besten im Kontext Ihres Unternehmens beschreiben.

Stellen Sie dann einen Satz mit Bildern zusammen, die Ihr Produkt bestmöglich für eine bestimmte Geschäftsanforderung darstellen. Stellen Sie sicher, dass die Assets in Ihrem Satz den [Richtlinien für das Trainieren des Smart Content Service](smart-tags-training-guidelines.md) entsprechen.

Fügen Sie die Assets zu einem Ordner hinzu und wenden Sie die Tags auf jedes Asset auf der Eigenschaftenseite an. Führen Sie dann den Trainings-Workflow für diesen Ordner aus. Der kuratierte Satz von Assets ermöglicht es dem Smart Content Service, mithilfe Ihrer Taxonomiedefinitionen effektiv mehr Assets zu trainieren.

>[!NOTE]
>
>1. Training ist ein unwiderruflicher Prozess. Adobe empfiehlt, die Tags im kuratierten Satz von Assets lange vor dem Trainieren des Smart Content Service für die Tags zu überprüfen.
>1. Lesen Sie bitte [Trainings-Richtlinien für Smart Content Service](smart-tags-training-guidelines.md) vor dem Starten des Trainings für ein beliebiges Tag.
>1. Adobe empfiehlt Ihnen, mindestens zwei unterschiedliche Tags zu verwenden, wenn Sie den Smart Content Service zum ersten Mal trainieren.

>


## Trainieren des Smart Content Service {#training-the-smart-content-service}

Damit der Smart Content Service die Taxonomie Ihres Unternehmens erkennen kann, sollten Sie den Dienst auf einen Asset-Satz ausführen, der bereits für Ihr Unternehmen relevante Tags enthält. Nach dem Training kann der Dienst dieselbe Taxonomie auf einen ähnlichen Satz von Assets anwenden.

Sie können den Dienst mehrmals trainieren, um die Fähigkeit zu verbessern, relevante Tags anzuwenden. Führen Sie nach jedem Trainings-Zyklus einen Tagging-Workflow aus und überprüfen Sie, ob Ihre Assets angemessen mit Tags versehen sind.

Sie können den Smart Content Service regelmäßig oder auf Anforderung trainieren.

>[!NOTE]
>
>Der Trainings-Workflow wird nur für Ordner ausgeführt.

### Regelmäßige Ausbildung {#periodic-training}

Sie können festlegen, dass der Smart Content Service regelmäßig mit den Assets und zugewiesenen Tags in einem Ordner trainiert wird. Öffnen Sie die Eigenschaftsseite Ihres Asset-Ordners, wählen Sie **[!UICONTROL Smart-Tags aktivieren]** in der Registerkarte **[!UICONTROL Details]** aus und speichern Sie die Änderungen.

![enable_smart_tags](assets/enable_smart_tags.png)

Wenn Sie diese Option für einen Ordner auswählt haben, führt [!DNL Experience Manager] automatisch einen Trainings-Workflow aus, um den Smart Content Service mit den Assets im Ordner und deren Tags zu trainieren. Standardmäßig wird der Trainings-Workflow samstags um 12:30 Uhr wöchentlich ausgeführt.

### On-Demand-Schulung {#on-demand-training}

Sie können den Smart Content Service bei Bedarf über die Workflow-Konsole trainieren.

1. Tippen/klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Tools > Workflow > Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflowmodelle]** den Workflow für das **[!UICONTROL Smart-Tags-Training]** aus und tippen/klicken Sie dann in der Symbolleiste auf **[!UICONTROL Workflow starten]**.
1. Suchen Sie im Dialogfeld **[!UICONTROL Workflow ausführen]** nach dem Payload-Ordner, der die mit Tags versehenen Assets für das Trainieren des Services enthält.
1. Geben Sie einen Titel für den Workflow an und fügen Sie einen Kommentar hinzu. Tippen/klicken Sie dann auf **[!UICONTROL Ausführen]**. Die Assets und Tags werden für das Training übermittelt.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Wenn die Assets in einem Ordner für das Training verarbeitet wurden, werden für zukünftige Trainingszyklen nur die modifizierten Assets verarbeitet.

### Anzeigen von Schulungsberichten {#viewing-training-reports}

Um sicherzustellen, dass der Smart Content Service auf Ihre Tags im Asset-Trainingssatz trainiert ist, überprüfen Sie den Bericht zum Trainings-Workflow über die Berichte-Konsole.

1. Tippen/klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Tools > Assets > Berichte]**.
1. Tippen/Klicken Sie auf der Seite **[!UICONTROL Asset-Berichte]** auf **[!UICONTROL Erstellen]**.
1. Wählen Sie den Bericht **[!UICONTROL Smart-Tags-Training]** aus und tippen/klicken Sie dann in der Symbolleiste auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Titel und eine Beschreibung für den Bericht an. Lassen Sie unter **[!UICONTROL Berichtplanen]** die Option **[!UICONTROL Jetzt]** aktiviert. Wenn Sie den Bericht für einen späteren Zeitpunkt planen möchten, wählen Sie **[!UICONTROL Später]** und geben Sie ein Datum und eine Uhrzeit an. Tippen/Klicken Sie dann in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Asset-Berichte]** den erstellten Bericht aus. Um den Bericht anzuzeigen, tippen/klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Ansicht]**.
1. Prüfen Sie die Details des Berichts.

   Der Bericht zeigt den Trainings-Status der von Ihnen trainierten Tags an. Grün gibt in der Spalte **[!UICONTROL Trainingsstatus]** an, dass der Smart Content Service für das Tag trainiert wird. Gelb bedeutet, dass der Service für ein bestimmtes Tag nicht vollständig trainiert ist. Fügen Sie in diesem Fall weitere Bilder mit dem jeweiligen Tag hinzu und führen Sie den Trainings-Workflow aus, um den Service vollständig für das Tag zu trainieren.

   Wenn Ihre Tags in diesem Bericht nicht angezeigt werden, führen Sie den Trainings-Workflow für diese Tags erneut aus.

1. Um den Bericht herunterzuladen, wählen Sie ihn aus der Liste aus und tippen/klicken Sie auf **[!UICONTROL Download]** in der Symbolleiste. Der Bericht wird als Excel-Datei heruntergeladen.

## Automatisches Tagging von Assets {#tagging-assets-automatically}

Nachdem Sie den Smart Content Service trainiert haben, können Sie im Tagging-Workflow automatisch passende Tags auf einen anderen Satz ähnlicher Assets anwenden.

Sie können den Tagging-Workflow regelmäßig oder bei Bedarf ausführen.

>[!NOTE]
>
>Der Tagging-Workflow wird sowohl für Assets als auch für Ordner ausgeführt.

### Periodisches Tagging {#periodic-tagging}

Sie können den Smart Content Service aktivieren, um Assets in einem Ordner regelmäßig mit Tags zu versehen. Öffnen Sie die Eigenschaftsseite Ihres Asset-Ordners, wählen Sie **[!UICONTROL Smart-Tags aktivieren]** in der Registerkarte **[!UICONTROL Details]** aus und speichern Sie die Änderungen.

Wenn diese Option für einen Ordner ausgewählt ist, versieht der Smart Content Service die Assets innerhalb des Ordners automatisch mit Tags. Standardmäßig wird der Tagging-Workflow jeden Tag um 0:00 Uhr ausgeführt.

### Tagging bei Bedarf {#on-demand-tagging}

Sie können den Tagging-Workflow wie folgt Trigger haben, um Ihre Assets sofort mit Tags zu versehen:

* Workflow-Konsole
* Zeitleiste

>[!NOTE]
>
>Wenn Sie den Tagging-Workflow über die Zeitleiste ausführen, können Sie Tags gleichzeitig auf maximal 15 Assets anwenden.

#### Tagging von Assets über die Workflow-Konsole {#tagging-assets-from-the-workflow-console}

1. Tippen/klicken Sie auf [!DNL Experience Manager] -Logo und navigieren Sie zu **[!UICONTROL Tools > Workflow > Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflowmodelle]** den Workflow **[!UICONTROL DAM Smart Tags Assets]** aus und tippen/klicken Sie dann in der Symbolleiste auf **[!UICONTROL Workflow starten]**.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Suchen Sie im Dialogfeld **[!UICONTROL Workflow ausführen]** den Payload-Ordner mit den Assets, auf die Sie automatisch Tags anwenden möchten.
1. Geben Sie einen Titel für den Workflow und optional einen Kommentar an. Tippen/klicken Sie dann auf **[!UICONTROL Ausführen]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Navigieren Sie zum Asset-Ordner und überprüfen Sie die Tags, um zu überprüfen, ob der Smart Content Service Ihre Assets ordnungsgemäß mit Tags versehen hat. Weitere Informationen finden Sie unter [Verwalten von Smart-Tags](managing-smart-tags.md).

#### Tagging von Assets über die Timeline {#tagging-assets-from-the-timeline}

1. Wählen Sie über die Assets-Benutzeroberfläche den Ordner mit Assets bzw. bestimmte Assets aus, auf die Sie Smart-Tags anwenden möchten.
1. Tippen/klicken Sie auf das GlobalNav-Symbol und öffnen Sie die Timeline.
1. Tippen/klicken Sie unten auf den Pfeil und dann auf **[!UICONTROL Workflow starten]**.

   ![start_workflow](assets/start_workflow.png)

1. Wählen Sie den Workflow **[!UICONTROL DAM Smart-Tag-Assets]** aus und geben Sie einen Titel für den Workflow an.
1. Tippen/klicken **[!UICONTROL Starten]**. Der Workflow wendet Ihre Tags auf Assets an. Navigieren Sie zum Asset-Ordner und überprüfen Sie die Tags, um zu überprüfen, ob der Smart Content Service Ihre Assets ordnungsgemäß mit Tags versehen hat. Weitere Informationen finden Sie unter [Verwalten von Smart-Tags](managing-smart-tags.md).

>[!NOTE]
>
>In zukünftigen Tagging-Zyklen werden nur geänderte Assets mit neu trainierten Tags versehen.
>
>Allerdings werden auch unveränderte Assets mit Tags versehen, wenn das Intervall zwischen dem letzten und dem aktuellen Tagging-Zyklus für den Tagging-Workflow 24 Stunden überschreitet.
>
>Bei periodischen Tagging-Workflows werden unveränderte Assets mit Tags versehen, wenn die Lücke 6 Monate überschreitet.
