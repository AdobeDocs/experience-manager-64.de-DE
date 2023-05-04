---
title: Hinzufügen von ContextHub zu Seiten und Zugreifen auf Speicher
seo-title: Adding ContextHub to Pages and Accessing Stores
description: Fügen Sie Ihren Seiten ContextHub hinzu, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen
seo-description: Add ContextHub to your pages to enable the ContextHub features and to link to the ContextHub Javascript libraries
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
exl-id: 99efe308-bf8a-41ad-8203-b57fce20820c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 59%

---

# Hinzufügen von ContextHub zu Seiten und Zugreifen auf Speicher {#adding-contexthub-to-pages-and-accessing-stores}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Fügen Sie Ihren Seiten ContextHub hinzu, um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen

Die ContextHub-JavaScript-API ermöglicht den Zugriff auf die von ContextHub verwalteten Kontextdaten. Auf dieser Seite werden die Hauptfunktionen der API für den Zugriff auf Kontextdaten und die Bearbeitung von Kontextdaten kurz beschrieben. Ausführlichere Informationen und Code-Beispiele finden Sie unter den Links zur API-Referenzdokumentation.

## Hinzufügen von ContextHub zu einer Seitenkomponente {#adding-contexthub-to-a-page-component}

Um die ContextHub-Funktionen zu aktivieren und eine Verknüpfung mit den ContextHub-JavaScript-Bibliotheken herzustellen, fügen Sie die ContextHub-Komponente in die `head` auf Ihrer Seite. Der JSP-Code für Ihre Seitenkomponente ähnelt dem folgenden Beispiel:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

Beachten Sie, dass Sie auch konfigurieren müssen, ob die ContextHub-Symbolleiste im Vorschaumodus angezeigt wird. Siehe [Ein- und Ausblenden der ContextHub-Benutzeroberfläche](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui).

## Informationen zu ContextHub-Speichern {#about-contexthub-stores}

Verwenden Sie ContextHub-Stores, um Kontextdaten beizubehalten. ContextHub bietet die folgenden Storetypen, die die Grundlage aller Storetypen bilden:

* [PersistedStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

Alle Speichertypen sind Erweiterungen der Klasse [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core). Informationen zum Erstellen eines neuen Storetyps finden Sie unter [Erstellen benutzerdefinierter Stores](/help/sites-developing/ch-extend.md#creating-custom-store-candidates). Weitere Informationen zu Beispiel-Store-Typen finden Sie unter [Beispiele für ContextHub-Store-Kandidaten](/help/sites-developing/ch-samplestores.md).

### Beibehaltungsmodi {#persistence-modes}

ContextHub-Stores verwenden einen der folgenden Persistenzmodi:

* **Lokal:** Verwendet HTML5 localStorage , um Daten beizubehalten. Lokaler Speicher wird sitzungsübergreifend im Browser beibehalten.
* **Sitzung:** Verwendet „sessionStorage“ (HTML5), um Daten beizubehalten. Sitzungsspeicher wird für die Dauer der Browser-Sitzung beibehalten und steht für alle Browser-Fenster zur Verfügung.
* **Cookie:** Verwendet die native Unterstützung von Cookies durch den Browser für die Datenspeicherung. Cookie-Daten werden in HTTP-Anfrage an den bzw. vom Server gesendet.
* **Window.name:** Verwendet die Eigenschaft „window.name“, um Daten beizubehalten.
* **Speicher:** Verwendet ein JavaScript-Objekt, um Daten beizubehalten.

Standardmäßig verwendet ContextHub den lokalen Persistenzmodus. Wenn der Browser HTML5 localStorage nicht unterstützt oder zulässt, wird die Sitzungspersistenz verwendet. Wenn der Browser HTML5 sessionStorage nicht unterstützt oder zulässt, wird die Persistenz Window.name verwendet.

### Store-Daten {#store-data}

Intern speichern Sie Daten in einer Baumstruktur, sodass Werte als primäre Typen oder komplexe Objekte hinzugefügt werden können. Wenn Sie komplexe Objekte zu Stores hinzufügen, bilden die Objekteigenschaften Zweige in der Datenstruktur. Im folgenden Beispiel wird das folgende komplexe Objekt einem leeren, als Store bezeichneten Ort hinzugefügt:

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

Die Baumstruktur der Speicherdaten kann wie folgt gestaltet werden:

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

Die Baumstruktur definiert Datenelemente im Speicher als Schlüssel-Wert-Paare. Im obigen Beispiel entspricht der Schlüssel `/number` dem Wert `321` und der Schlüssel `/data/country` dem Wert `Switzerland`.

### Bearbeiten von Objekten {#manipulating-objects}

Für die Bearbeitung von JavaScript-Objekten stellt ContextHub die Klasse [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) bereit. Mithilfe der Funktionen dieser Klasse können Sie JavaScript-Objekte bearbeiten, bevor Sie sie einem Store hinzufügen oder nachdem Sie sie aus einem Store abgerufen haben.

Darüber hinaus bietet die Klasse [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) Funktionen zum Serialisieren von Objekten zu Zeichenfolgen und zum Deserialisieren von Zeichenfolgen zu Objekten. Verwenden Sie diese Klasse zur Behandlung von JSON-Daten, um Browser zu unterstützen, die nativ nicht über die Funktionen `JSON.parse` und `JSON.stringify` verfügen.

## Interagieren mit ContextHub-Stores {#interacting-with-contexthub-stores}

Verwenden Sie das JavaScript-Objekt [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants), um einen Store als JavaScript-Objekt abzurufen. Nach dem Abrufen des Store-Objekts können Sie die darin enthaltenen Daten bearbeiten. Verwenden Sie zum Abrufen des Stores die Funktion [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) oder [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name).

### Zugreifen auf Store-Daten {#accessing-store-data}

Die JavaScript-Klasse [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) definiert mehrere Funktionen für die Interaktion mit Store-Daten. Die folgenden Funktionen ermöglichen das Speichern und Abrufen mehrerer in Objekten enthaltener Datenelemente:

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

Einzelne Datenelemente werden als Satz von Schlüssel/Wert-Paaren gespeichert. Um Werte zu speichern und abzurufen, geben Sie den entsprechenden Schlüssel an:

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

Beachten Sie, dass benutzerdefinierte Speicherkandidaten weitere Funktionen definieren können, die den Zugriff auf Speicherdaten ermöglichen.

>[!NOTE]
>
>ContextHub kennt nicht standardmäßig die aktuell angemeldeten Benutzer, die auf Veröffentlichungs-Servern verwendet werden, und diese Benutzer werden von ContextHub als &quot;Anonym&quot;betrachtet.
>
>Sie können ContextHub über angemeldete Benutzer informieren, indem Sie den Profilspeicher laden, wie in der implementierten [Referenz-Site &quot;We.Retail&quot;](/help/sites-developing/we-retail.md). Siehe Abschnitt [relevanter Code auf GitHub hier](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### ContextHub-Ereignisse {#contexthub-eventing}

ContextHub enthält ein Ereignis-Framework, das automatische Reaktionen auf Store-Ereignisse ermöglicht. Jedes Store-Objekt enthält ein Objekt vom Typ [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing), das als Eigenschaft [`eventing`](/help/sites-developing/contexthub-api.md#eventing) des Stores verfügbar ist. Verwenden Sie die Funktion [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) oder [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents), um eine JavaScript-Funktion an ein Store-Ereignis zu binden.

## Bearbeiten von Cookies mithilfe von ContextHub {#using-context-hub-to-manipulate-cookies}

Die ContextHub JavaScript API bietet Browser-übergreifende Unterstützung für die Behandlung der Cookies von Browsern. Der Namespace [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) definiert eine Reihe von Funktionen zum Erstellen, Bearbeiten und Löschen von Cookies.

## Ermitteln aufgelöster ContextHub-Segmente {#determining-resolved-contexthub-segments}

Mit der ContextHub-Segment-Engine können Sie ermitteln, welche der registrierten Segmente im aktuellen Kontext aufgelöst werden. Verwenden Sie die Funktion „getResolvedSegments“ der Klasse [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager), um aufgelöste Segmente abzurufen. Verwenden Sie anschließend die Funktion `getName` oder `getPath` der Klasse [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment), um auf ein Segment zu testen.

### Installierte Segmente {#installed-segments}

ContextHub-Segmente werden unter dem Knoten `/conf/we-retail/settings/wcm/segments` installiert.

* weiblich
* female-over-30
* female-under-30
* männlich
* male-over-30
* male-under-30
* order-value-75-to-100
* order-value-over-100
* über 30
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

* Weiblich oder männlich wird anhand der `gender` Datenelement der [profile](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) speichern.

* Das Alter wird anhand des Seitendatenelements des Profilspeichers bestimmt.
* Die Staffel wird aus dem Datenelement &quot;latitude&quot;des [Geolocation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) speichern und das Monatsdatenelement des surferinfo -Stores.

>[!WARNING]
>
>Die installierten Segmente werden als Referenzkonfigurationen bereitgestellt, um Ihnen bei der Erstellung einer eigenen dedizierten Konfiguration für Ihr Projekt zu helfen, und sollten daher nicht direkt verwendet werden.

## Protokollieren von Debug-Meldungen für ContextHub {#logging-debug-messages-for-contexthub}

Konfigurieren Sie den Adobe Granite ContextHub-OSGi-Service (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) für die Protokollierung detaillierter Debug-Meldungen, die bei der Entwicklung hilfreich sind.

Der Service kann entweder mithilfe der [Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) oder mit einem [JCR-Knoten im Repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) konfiguriert werden:

* Web-Konsole: Wählen Sie zum Protokollieren von Debug-Meldungen die Debug-Eigenschaft aus.
* JCR-Knoten: Legen Sie zum Protokollieren von Debug-Meldungen die boolesche Eigenschaft `com.adobe.granite.contexthub.debug` auf `true` fest.

## Überblick über das ContextHub-Framework {#see-an-overview-of-the-contexthub-framework}

ContextHub bietet eine [Diagnoseseite](/help/sites-developing/ch-diagnostics.md), auf der Sie einen Überblick über das ContextHub-Framework erhalten.
