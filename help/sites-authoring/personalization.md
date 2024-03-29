---
title: Personalisierung und Content-Targeting
seo-title: Personalization and Content Targeting
description: Erfahren Sie, wie AEM personalisierte Inhalte erstellen kann
seo-description: Learn how AEM can create personalized content
uuid: 3a1aaa3d-5f57-4fb7-a4be-523f0d274b79
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 850da0da-f7c3-4dd7-bb06-404c14a2a791
exl-id: 669e2509-e563-46ff-b01c-3f05ec196df5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 64%

---

# Personalisierung und Content-Targeting {#personalization}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Personalisierung und Content-Targeting {#personalization-and-content-targeting}

AEM stellt eine Reihe von Tools zur Bearbeitung von Inhalten für eine bestimmte Zielgruppe und die Darstellung personalisierter Erlebnisse bereit.

## Targeting-Modus {#targeting-mode}

[Verfassen Sie zielgerichtete Inhalte](/help/sites-authoring/content-targeting-touch.md) im Targeting-Modus von AEM. Der Targeting-Modus und die Targeting-Komponente sind wichtige Werkzeuge für die Erstellung von Erlebnisinhalten für Ihre Marketing-Aktivitäten.

## Aktivitäten {#activities}

Aktivitäten definieren und organisieren Ihre Marketing-Maßnahmen. Aktivitäten umfassen die Zielgruppen und den Zeitraum, in dem die Zielgruppenbestimmung erfolgt.

So enthält der We.Retail-Produktkatalog beispielsweise Teaser, die die Aufmerksamkeit auf Produkte der aktuellen Saison lenken sollen. In der Aktivität „Sommersport“ sind die Marketing-Segmente definiert, die während der Sommermonate gezielt angesprochen werden sollen.

Aktivitäten identifizieren auch [Targeting-Engine](/help/sites-authoring/personalization.md#targeting-engine) , die Ihre Seiten verwenden.

Mit der [Aktivitätskonsole](/help/sites-authoring/activitylib.md) können Sie die Aktivitäten Ihrer Marken erstellen und verwalten. Sie können auch Aktivitäten erstellen, während Sie [zielgerichtete Inhalte erstellen](/help/sites-authoring/content-targeting-touch.md).

## Erlebnisse {#experiences}

Legen Sie für jede Aktivität ein oder mehr Erlebnisse fest, in denen die gewünschten Zielgruppen identifiziert sind. Mit AEM verfügen Sie über die Möglichkeit, die Inhalte jedes Erlebnisses gezielt zu steuern.

Zielgruppen basieren auf Marketingsegmenten, die entweder in AEM oder Adobe Target erstellt werden. Öffnet ein Besucher eine Web-Seite, bestimmt die Seitenlogik die Zielgruppe, in die er fällt, und zeigt die für diese Zielgruppe erstellten Inhalte an.

Mit einer Aktivität können beispielsweise Erlebnisse für zwei verschiedene Zielgruppen festgelegt werden: Frauen über 30 und Frauen unter 30. Die Damenabteilung der We.Retail-Website zeigt für die beiden Erlebnisse unterschiedliche Inhalte an.

Sie definieren Erlebnisse für eine Aktivität. Sie können die [Aktivitätskonsole](/help/sites-authoring/activitylib.md#adding-editing-an-activity-using-the-activities-console) oder [Targeting-Modus](/help/sites-authoring/content-targeting-touch.md#adding-and-removing-experiences-using-targeting-mode) , um einer Aktivität Erlebnisse hinzuzufügen.

## Angebote {#offers}

Ein Angebot ist Inhalt, der an einer Stelle auf einer Seite für ein Erlebnis angezeigt wird. Verwenden Sie verschiedene Angebote für verschiedene Erlebnisse, um die Effektivität des Inhalts für Ihre Zielgruppen zu maximieren.

Beispielsweise könnte die Damenabteilung einer We.Retail-Beispiel-Website Angebote als das Teaser-Bild verwenden, das oben auf der Seite eingeblendet wird. Für Erlebnisse für Frauen über 30 werden andere Angebote eingesetzt als für Frauen unter 30.

Verwenden Sie die [Angebotskonsole](/help/sites-authoring/offerlib.md) , um Angebote zu erstellen, die Sie in mehreren Erlebnissen verwenden können. Erstellen Sie Angebote für einzelne Anwendungen oder fügen Sie Angebote aus einer Angebotsbibliothek hinzu, wenn [Verfassen zielgerichteter Inhalte](/help/sites-authoring/content-targeting-touch.md).

## Targeting-Engine {#targeting-engine}

Die Targeting-Engine ist der Mechanismus, der die Logik für zielgerichtete Inhalte steuert. [Aktivitäten](/help/sites-authoring/activitylib.md) sind so konfiguriert, dass eine von zwei verfügbaren Targeting-Engines verwendet wird: AEM oder Adobe Target.

### AEM {#aem}

AEM bietet eine integrierte Targeting-Engine, die Seitenanfragen verarbeitet und den anzuzeigenden Inhalt bestimmt. Bei der Verwendung der AEM Targeting-Engine sind Sie auf den Einsatz von Segmenten beschränkt, die in AEM erstellt wurden, um die Zielgruppen Ihrer Erlebnisse festzulegen.

### Adobe Target {#adobe-target}

Mit der Targeting-Engine von Adobe Target werden von Seitenbesuchen gesammelte Informationen in Adobe Target verfolgt.

* Bei der Verwendung dieser Targeting-Engine setzen Sie Segmente ein, die Sie aus Adobe Target importieren, um die Zielgruppen Ihrer Erlebnisse zu bestimmen.
* Aktivitäten, die die Adobe Target-Engine verwenden, sind [mit Target synchronisiert](/help/sites-authoring/activitylib.md#synchronizing-activities-with-adobe-target).

Sie können diese Engine verwenden, wenn Sie über eine [Integration mit Adobe Target](/help/sites-administering/opt-in.md) verfügen.
