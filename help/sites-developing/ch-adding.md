---
title: Hinzufügen von ContextHub zu Seiten und Zugreifen auf Speicher
seo-title: Hinzufügen von ContextHub zu Seiten und Zugreifen auf Speicher
description: Fügen Sie Ihren Seiten ContextHub hinzu, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen.
seo-description: Fügen Sie Ihren Seiten ContextHub hinzu, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen.
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 78%

---


# Hinzufügen von ContextHub zu Seiten und Zugreifen auf Speicher {#adding-contexthub-to-pages-and-accessing-stores}

Fügen Sie Ihren Seiten ContextHub hinzu, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen.

Die ContextHub-JavaScript-API ermöglicht den Zugriff auf die von ContextHub verwalteten Kontextdaten. Diese Seite enthält einen kurzen Überblick über die wichtigsten Funktionen der API für den Zugriff auf Kontextdaten und deren Bearbeitung. Ausführlichere Informationen und Codebeispiele finden Sie unter den Links zur API-Referenzdokumentation.

## Hinzufügen von ContextHub zu einer Seitenkomponente {#adding-contexthub-to-a-page-component}

Schließen Sie die contexthub-Komponente in den Bereich `head` Ihrer Seite ein, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen. Der JSP-Code für Ihre Seitenkomponente sieht in etwa wie im folgenden Beispiel aus:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

Beachten Sie, dass Sie auch konfigurieren müssen, ob die ContextHub-Symbolleiste im Vorschaumodus angezeigt werden soll. Siehe [Ein- und Ausblenden der ContextHub-Benutzeroberfläche](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui).

## Informationen zu ContextHub-Speichern {#about-contexthub-stores}

Verwenden Sie ContextHub-Speicher, um Kontextdaten beizubehalten. ContextHub bietet folgende Arten von Speichern, die die Grundlage für alle Speichertypen bilden:

* [PersistedStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

Alle Speichertypen sind Erweiterungen der Klasse [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core). Weitere Informationen zur Erstellung eines neuen Speichertyps finden Sie unter [Erstellen benutzerdefinierter Speicher](/help/sites-developing/ch-extend.md#creating-custom-store-candidates). Weitere Informationen zu Beispielspeichertypen finden Sie unter [Beispielkandidaten für ContextHub-Speicher](/help/sites-developing/ch-samplestores.md).

### Beibehaltungsmodi {#persistence-modes}

ContextHub-Speicher verwenden einen der folgenden Beibehaltungsmodi:

* **Lokal:** Verwendet „localStorage“ (HTML5), um Daten beizubehalten. Lokaler Speicher wird im Browser sitzungsübergreifend beibehalten.
* **Sitzung:** Verwendet HTML5 sessionStorage, um Daten zu erhalten. Sitzungsspeicher wird für die Dauer der Browsersitzung beibehalten und steht für alle Browserfenster zur Verfügung.
* **Cookie:** Verwendet die native Cookie-Unterstützung des Browsers für die Datenspeicherung. Cookie-Daten werden in HTTP-Anforderungen an den bzw. vom Server gesendet.
* **Window.name:** Verwendet die Eigenschaft „window.name“, um Daten beizubehalten.
* **Speicher:** Verwendet ein JavaScript-Objekt, um Daten beizubehalten.

ContextHub verwendet standardmäßig den lokalen Beibehaltungsmodus. Falls der Browser „localStorage“ (HTML5) nicht unterstützt oder nicht zulässt, wird die Sitzungsbeibehaltung verwendet. Falls der Browser „sessionStorage“ (HTML5) nicht unterstützt oder nicht zulässt, wird die Beibehaltung vom Typ „Window.name“ verwendet.

### Store-Daten {#store-data}

Store-Daten bilden intern eine Baumstruktur. Dadurch können Werte als primäre Typen oder als komplexe Objekte hinzugefügt werden. Wenn Sie Stores komplexe Objekte hinzufügen, bilden die Objekteigenschaften Verzweigungen in der Datenstruktur. Beispielsweise wird das folgende komplexe Objekt einem leeren Store mit dem Namen &quot;Speicherort&quot;hinzugefügt:

```xml
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

Die Baumstruktur der Store-Daten kann wie folgt dargestellt werden:

```xml
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

Die Baumstruktur definiert Datenelemente im Store als Schlüssel-Wert-Paare. In the above example, the key `/number` corresponds with the value `321`, and the key `/data/country` corresponds with the value `Switzerland`.

### Bearbeiten von Objekten {#manipulating-objects}

ContextHub provides the [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) class for manipulating Javascript objects. Mithilfe der Funktionen dieser Klasse können Sie JavaScript-Objekte bearbeiten, bevor Sie sie einem Store hinzufügen oder nachdem Sie sie aus einem Store abgerufen haben.

Additionally, the [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) class provides functions for serializing objects to stings, and deserializing strings to objects. Use this class for handling JSON data to support browsers that do not natively include the `JSON.parse` and `JSON.stringify` functions.

## Interagieren mit ContextHub-Stores {#interacting-with-contexthub-stores}

Verwenden Sie das JavaScript-Objekt [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants), um einen Store als JavaScript-Objekt abzurufen. Nach dem Abrufen des Store-Objekts können Sie die darin enthaltenen Daten bearbeiten. Use the [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) or the [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) function to obtain the store.

### Zugreifen auf Store-Daten {#accessing-store-data}

The [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) Javascript class defines several functions for interacting with store data. Die folgenden Funktionen ermöglichen das Speichern und Abrufen mehrerer in Objekten enthaltener Datenelemente:

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

Einzelne Datenelemente werden als Schlüssel-Wert-Paare gespeichert. Zum Speichern und Abrufen von Werten muss der entsprechende Schlüssel angegeben werden:

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

Beachten Sie, dass benutzerdefinierte Speicherkandidaten weitere Funktionen definieren können, die den Zugriff auf Store-Daten ermöglichen.

>[!NOTE]
>
>Standardmäßig sind ContextHub die derzeit bei Veröffentlichungsservern angemeldeten Benutzer nicht bekannt und solche Benutzer werden von ContextHub als anonyme Benutzer betrachtet.
>
>Sie können dafür sorgen, dass ContextHub angemeldete Benutzer erkennt, indem Sie den Profilspeicher laden, wie in der [We.Retail-Referenzsite](/help/sites-developing/we-retail.md) implementiert. Den relevanten Code finden Sie [auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### ContextHub-Ereignisse {#contexthub-eventing}

ContextHub enthält ein Ereignisframework, das automatische Reaktionen auf Store-Ereignisse ermöglicht. Jedes Storeobjekt enthält ein Objekt vom Typ [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing), das als Eigenschaft [`eventing`](/help/sites-developing/contexthub-api.md#eventing) des Stores verfügbar ist. Verwenden Sie die Funktion [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) oder [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents), um eine JavaScript-Funktion an ein Store-Ereignis zu binden.

## Bearbeiten von Cookies mithilfe von ContextHub {#using-context-hub-to-manipulate-cookies}

Die ContextHub-API bietet browserübergreifende Unterstützung für die Behandlung von Browser-Cookies. The [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) namespace defines several functions for creating, manipulating, and deleting cookies.

## Ermitteln aufgelöster ContextHub-Segmente {#determining-resolved-contexthub-segments}

Mit der ContextHub-Segment-Engine können Sie ermitteln, welche der registrierten Segmente im aktuellen Kontext aufgelöst werden. Verwenden Sie die Funktion „getResolvedSegments“ der Klasse [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager), um aufgelöste Segmente abzurufen. Then, use the `getName` or `getPath` function of the [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) class to test for a segment.

### Installierte Segmente {#installed-segments}

ContextHub segments are installed below the `/conf/we-retail/settings/wcm/segments` node.

* female
* female-over-30
* female-under-30
* male
* male-over-30
* male-under-30
* order-value-75-to-100
* order-value-over-100
* over-30
* summer
* summer-female
* summer-female-over-30
* summer-female-under-30
* summer-male
* summer-male-over-30
* summer-male-under-30
* under-30
* winter
* winter-female
* winter-female-over-30
* winter-female-under-30
* winter-male
* winter-male-over-30
* winter-male-under-20

Die Regeln zur Auflösung dieser Segmente werden wie folgt zusammengefasst:

* „female“ oder „male“ wird auf der Grundlage des Datenelements `gender` des Stores [profile](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) bestimmt.

* Das Alter wird auf der Grundlage des Datenelements „age“ des Stores „profile“ bestimmt.
* Season is determined from the latitude data item of the [geolocation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) store, and the month data item of the surferinfo store.

>[!WARNING]
>
>Die installierten Segmente werden als Referenzkonfigurationen bereitgestellt, um Ihnen bei der Erstellung Ihrer eigenen dedizierten Konfiguration für Ihr Projekt zu helfen und sollten daher nicht direkt verwendet werden.

## Protokollieren von Debugmeldungen für ContextHub {#logging-debug-messages-for-contexthub}

Configure the Adobe Granite ContextHub OSGi service (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) to log detailed Debug messages that are useful when developing.

To configure the service you can either use the [Web Console](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) or use a [JCR node in the repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository):

* Web-Konsole: Wählen Sie zum Protokollieren von Debugmeldungen die Debugeigenschaft aus.
* JCR node: To log Debug messages, set the boolean `com.adobe.granite.contexthub.debug` property to `true`.

## Überblick über das ContextHub-Framework {#see-an-overview-of-the-contexthub-framework}

ContextHub bietet eine [Diagnoseseite](/help/sites-developing/ch-diagnostics.md), auf der Sie sich einen Überblick über das ContextHub-Framework verschaffen können.
