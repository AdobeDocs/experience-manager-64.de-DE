---
title: Cloud Service-Konfigurationen
description: Sie können die vorhandenen Instanzen erweitern, um Ihre eigenen Konfigurationen zu erstellen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
exl-id: d2b8503e-8ac1-4617-ad76-b05d1e80a6b6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 66%

---

# Cloud Service-Konfigurationen{#cloud-service-configurations}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Konfigurationen dienen dazu, die Logik und Struktur zum Speichern von Dienstkonfigurationen bereitzustellen.

Sie können die vorhandenen Instanzen erweitern, um Ihre eigenen Konfigurationen zu erstellen.

## Konzepte {#concepts}

Die bei der Entwicklung der Konfigurationen verwendeten Prinzipien basieren auf folgenden Konzepten:

* Dienste/Adapter werden zum Abrufen der Konfigurationen verwendet.
* Konfigurationen (z. B. Eigenschaften/Absätze) werden von den übergeordneten Elementen übernommen.
* Referenziert von Analyseknoten nach Pfad.
* Einfach erweiterbar.
* Sie können auch komplexere Konfigurationen unterstützen, z. B. [Adobe Analytics ](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics).
* Unterstützung für Abhängigkeiten (z. B. benötigen [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)-Plug-ins eine [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)-Konfiguration).

## Struktur {#structure}

Der Basispfad der Konfigurationen lautet:

`/etc/cloudservices`.

Für jeden Konfigurationstyp werden eine Vorlage und eine Komponente bereitgestellt. Auf diese Weise können Konfigurationsvorlagen nach der Anpassung die meisten Anforderungen erfüllen.

Um eine Konfiguration für einen neuen Dienste bereitzustellen, müssen Sie:

* eine Dienstseite erstellen, und zwar unter

   `/etc/cloudservices`

* unter dieser

   * eine Konfigurationsvorlage
   * eine Konfigurationskomponente

Die Vorlage und die Komponente müssen `sling:resourceSuperType` von der Basisvorlage erben:

`cq/cloudserviceconfigs/templates/configpage`

bzw. von der Basiskomponente:

`cq/cloudserviceconfigs/components/configpage`

Der Dienstanbieter sollte auch die Dienstseite bereitstellen:

`/etc/cloudservices/<service-name>`

### Vorlage {#template}

Ihre Vorlage erweitert die Basisvorlage:

`cq/cloudserviceconfigs/templates/configpage`

und definiert einen `resourceType`, der auf die angepasste Komponente verweist.

```xml
/libs/cq/analytics/templates/sitecatalyst
sling:resourceSuperType = cq/cloudserviceconfigs/templates/configpage
allowedChildren = /libs/cq/analytics/templates/sitecatalyst
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
componentReference = cq/analytics/components/sitecatalyst
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/sitecatalystpage

/libs/cq/analytics/templates/generictracker
sling:resourceSuperType = cq/cloudservices/templates/configpage
allowedChildren = /libs/cq/analytics/templates/generictracker
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/generictrackerpage
```

### Komponenten {#components}

Ihre Komponente sollte die Basiskomponente erweitern:

`cq/cloudserviceconfigs/templates/configpage`

```xml
/libs/cq/analytics/components/sitecatalystpage

/libs/cq/analytics/components/generictrackerpage
```

Nach dem Einrichten der Vorlage und der Komponente können Sie Ihre Konfiguration hinzufügen, indem Sie unter folgendem Pfad untergeordnete Seiten hinzufügen:

`/etc/cloudservices/<service-name>`

### Inhaltsmodell {#content-model}

Das Inhaltsmodell wird als `cq:Page` in folgendem Verzeichnis gespeichert:

`/etc/cloudservices/<service-name>(/*)`

```xml
/etc/cloudservices
/etc/cloudservices/service-name
/etc/cloudservices/service-name/config
/etc/cloudservices/service-name/config/inherited-config
```

Die Konfigurationen werden unter dem untergeordneten Knoten `jcr:content` gespeichert.

* Feste Eigenschaften, die in einem Dialogfeld definiert wurden, sollten direkt auf dem Knoten `jcr:node` gespeichert werden.
* Dynamische Elemente (die `parsys` oder `iparsys` nutzen) speichern die Komponentendaten auf einem untergeordneten Knoten.

```xml
/etc/cloudservices/service/config/jcr:content as nt:unstructured
propertyname
*
par/component/ as cq:Component
propertyname
*
```

### API {#api}

Referenzdokumentation zur API finden Sie unter [com.day.cq.wcm.webservicesupport](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html).

### AEM-Integration {#aem-integration}

Verfügbare Dienste sind auf der Registerkarte **Cloud-Services** des Dialogfelds **Seiteneigenschaften** aufgeführt (bei jeder Seite, die von `foundation/components/page` oder `wcm/mobile/components/page` erbt).

Die Registerkarte bietet außerdem Folgendes:

* einen Link zum Speicherort, an dem Sie den Dienst aktivieren können
* eine Konfiguration (Unterknoten des Dienstes) aus einem Pfadfeld auswählen

#### Kennwortverschlüsselung {#password-encryption}

Beim Speichern von Benutzeranmeldeinformationen für den Dienst sollten alle Kennwörter verschlüsselt werden.

Sie können dies erreichen, indem Sie ein ausgeblendetes Formularfeld hinzufügen. Dieses Feld sollte im Eigenschaftsnamen die Anmerkung `@Encrypted` enthalten; d. h. im Feld `password` würde der Name wie folgt geschrieben:

`password@Encrypted`

Diese Eigenschaft wird dann automatisch (mit dem `CryptoSupport`-Dienst) durch den `EncryptionPostProcessor` verschlüsselt.

>[!NOTE]
>
>Dies ist mit den standardmäßigen ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)`-Anmerkungen vergleichbar.

>[!NOTE]
>
>Standardmäßig verschlüsselt der `EcryptionPostProcessor` nur `POST`-Anfragen an `/etc/cloudservices`.

#### Zusätzliche Eigenschaften für die jcr:content-Knoten der Dienstseite {#additional-properties-for-service-page-jcr-content-nodes}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Eigenschaft</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>componentReference</td> 
   <td>Referenzpfad zu einer Komponente, die automatisch in die Seite aufgenommen werden soll.<br /> Dies wird für zusätzliche Funktionen und JS-Einschlüsse genutzt.<br /> Dazu gehört die Komponente auf der Seite, auf der <br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> enthalten ist (normalerweise vor dem <code>body</code>-Tag).<br /> Bei Analytics und Target schließen wir damit zusätzliche Funktionen ein, z. B. JavaScript-Aufrufe, um das Verhalten der Besucher nachzuverfolgen.</td> 
  </tr> 
  <tr> 
   <td>description</td> 
   <td>Kurze Beschreibung des Dienstes.<br /> </td> 
  </tr> 
  <tr> 
   <td>descriptionExtended</td> 
   <td>Erweiterte Beschreibung des Dienstes.</td> 
  </tr> 
  <tr> 
   <td>ranking</td> 
   <td>Position des Dienstes in der Rangfolge zur Verwendung in Listen.</td> 
  </tr> 
  <tr> 
   <td>selectableChildren</td> 
   <td>Filter zum Anzeigen von Konfigurationen im Dialogfeld „Seiteneigenschaften“</td> 
  </tr> 
  <tr> 
   <td>serviceUrl</td> 
   <td>URL zur Website des Dienstes.</td> 
  </tr> 
  <tr> 
   <td>serviceUrlLabel</td> 
   <td>Titel für Dienst-URL.</td> 
  </tr> 
  <tr> 
   <td>thumbnailPath</td> 
   <td>Pfad zur Miniaturansicht für den Dienst.</td> 
  </tr> 
  <tr> 
   <td>visible</td> 
   <td>Sichtbarkeit im Dialogfeld „Seiteneigenschaften“, standardmäßig sichtbar (optional)</td> 
  </tr> 
 </tbody> 
</table>

### Anwendungsfälle {#use-cases}

Diese Dienste werden standardmäßig bereitgestellt:

* [Tracker-Snippets](/help/sites-administering/external-providers.md) (Google, WebTrends usw.)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [Test&amp;Target](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
* [Dynamic Media](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>Siehe auch [Erstellen eines benutzerdefinierten Cloud-Dienstes](/help/sites-developing/extending-cloud-config-custom-cloud.md).
