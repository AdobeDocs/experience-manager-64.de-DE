---
title: App-Vorlagen und -Komponenten
seo-title: App Templates and Components
description: Auf dieser Seite erfahren Sie mehr über App-Vorlagen und -Komponenten. Es enthält detaillierte Informationen zur Struktur von Vorlagen.
seo-description: Follow this page to learn about App Templates and Components. It provides detailed information on the structure of templates.
uuid: ba2fd91b-de5a-4f39-a976-5455f9983669
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 7f31c6a7-92d5-4a87-a9f0-68a82b834d5a
exl-id: 5480ac38-f651-4211-94f6-c588fb44ad55
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 54%

---

# App-Vorlagen und -Komponenten{#app-templates-and-components}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Eine Vorlage wird verwendet, um eine Seite zu erstellen. Sie definiert, welche Komponenten im ausgewählten Umfang genutzt werden können. Eine Vorlage ist eine Hierarchie von Knoten, die dieselbe Struktur aufweist wie die zu erstellende Seite, aber keine Inhalte.

Jede Vorlage stellt Ihnen eine Auswahl an Komponenten bereit, die Sie verwenden können.

* Vorlagen bestehen aus [Komponenten](/help/sites-developing/components.md).
* Komponenten nutzen Widgets und bieten Zugriff auf Widgets. Mit Widgets werden die Inhalte gerendert.

>[!NOTE]
>
>Informationen zum Entwickeln Ihrer AEM-Anwendung mithilfe von CRXDE Lite finden Sie unter [Entwickeln mit CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

Eine Vorlage ist die Basis einer Seite.

Um eine Seite zu erstellen, muss die Vorlage kopiert werden (Knotenbaum **/apps/&lt;myapp>/templates/&lt;mytemplate>**) an die entsprechende Position im Site-Baum: Dies geschieht, wenn eine Seite mit dem **Websites** Registerkarte.

Über diesen Kopiervorgang erhält die Seite auch ihren anfänglichen Inhalt (in der Regel nur den Inhalt der obersten Ebene) und die Eigenschaft sling:resourceType, den Pfad zur Seitenkomponente, die zum Rendern der Seite genutzt wird (alles im untergeordneten Knoten jcr:content).

## Struktur einer Vorlage {#structure-of-a-template}

Zwei Aspekte müssen berücksichtigt werden:

* die Struktur der Vorlage selbst
* die Struktur des Inhalts, der bei Verwendung einer Vorlage erstellt wird

Eine Vorlage wird unter einem Knoten des Typs **cq:Template** erstellt.

Verschiedene Eigenschaften können festgelegt werden, insbesondere:

* **jcr:title** – Titel für die Vorlage; wird beim Erstellen einer Seite im Dialogfeld angezeigt
* **jcr:description** – Beschreibung für die Vorlage; wird beim Erstellen einer Seite im Dialogfeld angezeigt

Dieser Knoten enthält *a jcr:content (cq:PageContent)* Knoten, der als Grundlage für den Inhaltsknoten der resultierenden Seiten verwendet wird; diese Referenz verwendet, *sling:resourceType*, die Komponente, die zum Rendern des tatsächlichen Inhalts einer neuen Seite verwendet werden soll.

>[!NOTE]
>
>Informationen zu den Grundlagen für Vorlagen und Komponenten in AEM finden Sie in den folgenden Ressourcen:
>
>* [Vorlagen](/help/sites-developing/templates.md)
>* [Komponenten](/help/sites-developing/components.md)
>


Nachdem Sie über grundlegende Kenntnisse zu Vorlagen und Komponenten verfügen, lesen Sie die folgenden Ressourcen:

* [Erstellen und Hinzufügen von Vorlagen und Komponenten](/help/mobile/mobile-ondemand-app-templates.md)
* [Verwenden von Inhaltseigenschaften zum Exportieren von Inhalten](/help/mobile/on-demand-content-properties-exporting.md)
* [Best Practices](/help/mobile/best-practices-aem-mobile.md)
* [Entwickeln von AEM Mobile Content Services](/help/mobile/developing-content-services.md)

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu zusätzlichen Themen zu mobilen Apps finden Sie unter den folgenden Links:

* [Mobil mit Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md)
* [Testen von mobilen Apps](/help/mobile/develop-mobile-apps-testing.md)
