---
title: ContextHub
seo-title: ContextHub
description: ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten
seo-description: ContextHub is a framework for storing, manipulating, and presenting context data
uuid: 14e6ff4f-ffbe-454a-b2ec-a35333526e27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: acf5c17a-95b7-43ba-9734-241e20f4f374
exl-id: 0a6b815a-5055-4c44-96d1-ff238b4285f3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 55%

---

# ContextHub{#contexthub}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. Die Client-seitige JavaScript-API ermöglicht Ihnen den Zugriff auf die Daten zur Personalisierung von Inhalten.

>[!NOTE]
>
>Die [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md) implementiert ContextHub und kann als Referenz dienen, wenn Sie ContextHub in Ihr eigenes Projekt integrieren.

>[!CAUTION]
>
>Der Pfad, der die ContextHub-Beispielkonfiguration enthält, die von der [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md) verwendet wird (`/libs/settings/cloudsettings/legacy`), sollte nur als Referenz zum Erstellen einer eigenen Konfiguration verwendet werden.
>
>Es sollte nicht in einem Projekt als eigene ContextHub-Konfiguration verwendet werden.

## Persistenz {#persistence}

ContextHub speichert persistente Kontextdaten auf dem Client. Mit der ContextHub-JavaScript-API können Sie auf Speicher zugreifen, um Daten bei Bedarf zu erstellen, zu aktualisieren und zu löschen. Daher stellt ContextHub eine Datenschicht auf Ihren Seiten dar.

Jeder ContextHub-Store ist eine Instanz eines vordefinierten Storetyps:

* ContextHub stellt verschiedene [Beispielspeicherarten bereit](/help/sites-developing/ch-samplestores.md).
* Verwenden AEM Konsolen für [Stores erstellen](/help/sites-administering/contexthub-config.md#creating-a-contexthub-store).
* Entwickler können [anwenderdefinierte Speichertypen erstellen](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).
* Entwickler können [Zugriffsspeicherdaten](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) über JavaScript.

## Segmentierung {#segmentation}

ContextHub enthält eine Segmentierungsmaschine, die Segmente verwaltet und bestimmt, welche Segmente für den aktuellen Kontext aufgelöst werden. Mehrere Segmente sind definiert. Sie können die JavaScript-API verwenden, um [aufgelöste Segmente bestimmen](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments).

## Präsentation {#presentation}

Die [ContextHub-Symbolleiste](/help/sites-authoring/ch-previewing.md) ermöglicht es Marketern und Autoren, gespeicherte Daten anzuzeigen und zu bearbeiten, um das Anwendererlebnis beim Erstellen von Seiten zu simulieren. Die Symbolleiste besteht aus Gruppen von UI-Modulen, die Zugriff auf ContextHub-Stores bieten.

Jedes ContextHub-UI-Modul ist eine Instanz eines vordefinierten Modultyps:

* ContextHub bietet mehrere [Beispielmodultypen](/help/sites-developing/ch-samplemodules.md).
* Verwenden AEM Konsolen für [Benutzeroberflächenmodule hinzufügen](/help/sites-administering/contexthub-config.md#adding-a-ui-module)und [gruppieren sie in UI-Modi](/help/sites-administering/contexthub-config.md#adding-a-ui-mode).

* Entwickler können [Erstellen benutzerdefinierter Modultypen](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

Entwickler müssen [Fügen Sie die ContextHub-Komponente zur Seite hinzu.](/help/sites-developing/ch-adding.md).
