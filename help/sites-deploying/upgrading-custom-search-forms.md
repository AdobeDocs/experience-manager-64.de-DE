---
title: Upgrades von benutzerdefinierten Suchformularen
seo-title: Upgrading Custom Search Forms
description: In diesem Artikel werden die Anpassungen erläutert, die nach einem Upgrade erfolgen müssen, damit benutzerdefinierte Suchformulare ordnungsgemäß funktionieren.
seo-description: This article details the adjustments that are required after an upgrade in order for the custom search forms to function.
uuid: 35b8fbb9-5951-4e1c-bf04-4471a55b9cb0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: a08cee9c-e981-4483-8bdc-e6353977f854
feature: Upgrading
exl-id: f55e2fe7-04ac-4368-b580-b8950d90548e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1721'
ht-degree: 80%

---

# Upgrades von benutzerdefinierten Suchformularen{#upgrading-custom-search-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In AEM 6.2 hat sich der Speicherort, an dem die benutzerdefinierte Search Forms im Repository gespeichert ist, geändert. Nach dem Upgrade werden diese von ihrem Speicherort in 6.1 unter:

* /apps/cq/gui/content/facets

an einen neuen Speicherort unter:

* /conf/global/settings/cq/search/facets

Daher müssen nach einem Upgrade manuelle Anpassungen vorgenommen werden, damit die Formulare weiterhin funktionieren.

Dies gilt sowohl für neue Search Forms als auch für standardmäßige Forms, die angepasst wurden.

Weitere Informationen finden Sie in der Dokumentation unter [Suchfacetten](/help/assets/search-facets.md).

## Ändern der Eigenschaft „resourceType“ {#changing-the-resourcetype-property}

Sofern nicht anders angegeben, muss für die meisten Anpassungen nach einem Upgrade die Eigenschaft `sling:resourceType` für die konfigurierten benutzerdefinierten Suchformulare geändert werden. Dies ist erforderlich, damit die Eigenschaft auf den richtigen Speicherort des Rendering-Skripts verweist.

Sie können die Eigenschaft wie folgt ändern:

1. Öffnen von CRXDE Lite über `https://server:port/crx/de/index.jsp`
1. Navigieren Sie zum Speicherort des Knotens, der angepasst werden muss, wie in der Liste der [Forms für benutzerdefinierte Suche](/help/sites-deploying/upgrading-custom-search-forms.md#list-of-custom-search-forms) unten.
1. Klicken Sie auf den Knoten. Klicken Sie im rechten Eigenschaftenbereich auf und ändern Sie die **sling:resourceType** -Eigenschaft.
1. Speichern Sie abschließend die Änderungen, indem Sie die **Alle speichern** Schaltfläche.

## Liste der Forms für benutzerdefinierte Suche {#list-of-custom-search-forms}

Nachstehend finden Sie eine Liste aller benutzerdefinierten Suchformulare und der Änderungen, die nach dem Upgrade erforderlich sind. Sie beziehen sich auf die Namen unter `/conf/global/settings/cq/search/facets/sites/items`.

### Volltext-Eigenschaft mit dem Knotennamen „fulltext“ {#fulltext-predicate-with-node-name-fulltext}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1</td> 
   <td>fulltext</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/fulltextpredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td>Nicht zutreffend</td> 
  </tr>
 </tbody>
</table>

In AEM 6.1 war die standardmäßige Volltexteigenschaft Teil des Suchformulars. In 6.2 wurde das Volltextfeld durch OmniSearch ersetzt. Diese Eigenschaft wird programmgesteuert übersprungen und kann entfernt werden.

**Aktion:** Entfernen Sie den Knoten vollständig.

### Andere Volltexteigenschaften {#other-fulltext-predicates}

<table> 
 <tbody>
  <tr>
   <td>Knoten in Standard-Suche von in 6.1</td> 
   <td>Nicht zutreffend</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/fulltextpredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/fulltextpredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Pfadbrowser-Eigenschaften {#path-browser-predicates}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>path</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/pathpredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/pathpredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Tags-Eigenschaften {#tags-predicates}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>Tags</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/common/admin/customsearch/searchpredicates/tagspredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/tagspredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft **resourceType** an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Seitenstatus-Eigenschaft {#page-status-predicate}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>pagestatuspredicate</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/pagestatuspredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td>Nicht zutreffend</td> 
  </tr>
 </tbody>
</table>

Der Seitenstatus wurde durch zwei Options-Eigenschaftsprädikate ersetzt, jeweils eins für den Veröffentlichungs- und eins für den LiveCopy-Status.

**Aktionen:**

* Entfernen Sie den Knoten `pagestatuspredicate`
* Kopieren Sie den Knoten

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/publishstatuspredicate`
   * in `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Kopieren Sie den Knoten

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/livecopystatuspredicate`
   * in `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Stellen Sie sicher, dass Sie die Eigenschaft `listOrder` für den Knoten `analyticspredicate` auf „**8**“ setzen. Dies ist erforderlich, um Konflikte zu vermeiden.

### Datumsbereichseigenschaften {#date-range-predicates}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>daterangepredicate</td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.1</td> 
   <td>cq/gui/components/common/admin/customsearch/searchpredicates/daterangepredicate</td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>common/admin/customsearch/searchpredicates/daterangepredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Ausgeblendet   Filter {#hidden-filter}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>Typ</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>granite/ui/components/foundation/form/hidden</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>granite/ui/components/foundation/form/hidden</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Keine Anpassung.

### Analytics-Eigenschaft {#analytics-predicate}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>analyticspredicate</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/analyticspredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/analyticspredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Eigenschaft für Bereich {#range-predicate}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>Nicht zutreffend</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/rangepredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/rangepredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

>[!NOTE]
>
>Hinweis: Im Gegensatz zu 6.1 rendert das Bereichsprädikat kein Tag mehr in der Suchleiste.

### Options-Eigenschaftsprädikat {#options-property-predicate}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>Nicht zutreffend</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/optionspredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/optionspredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Reglerbereichseigenschaft {#slider-range-predicate}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>Nicht zutreffend</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/sliderrangepredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/sliderrangepredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Komponenteneigenschaft {#components-predicate}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>Nicht zutreffend</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/componentspredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/componentspredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Verfassereigenschaft {#author-predicate}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>Nicht zutreffend</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/userpredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/userpredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Vorlageneigenschaft {#templates-predicate}

<table> 
 <tbody>
  <tr>
   <td>Knoten im Standard-Suchformular in 6.1<br /> <br /> </td> 
   <td>Nicht zutreffend</td> 
  </tr>
  <tr>
   <td><p>Ressourcentyp in 6.1</p> </td> 
   <td><p>cq/gui/components/siteadmin/admin/searchpanel/searchpredicates/templatespredicate</p> </td> 
  </tr>
  <tr>
   <td>Ressourcentyp in 6.2</td> 
   <td><p>cq/gui/components<strong>/coral/</strong>siteadmin/admin/searchpanel/searchpredicates/templatespredicate</p> </td> 
  </tr>
 </tbody>
</table>

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

## Asset-Admin-Suchschiene {#assets-admin-search-rail}

Die unten genannten Knoten beziehen sich auf die Namen in `/conf/global/settings/dam/search/facets/assets/items`.

### Volltext-Eigenschaft mit dem Knotennamen „fulltext“ {#fulltext-predicate-with-node-name-fulltext-1}

| Knoten im Standard-Suchformular in 6.1 | fulltext |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/fulltextpredicate |
| Ressourcentyp in 6.2 | Nicht zutreffend |

In 6.1 war die standardmäßige Volltexteigenschaft Teil des Suchformulars. In Version 6.2 wurde das Volltext-Feld durch OmniSearch ersetzt. Diese Eigenschaft wird programmgesteuert übersprungen und kann entfernt werden.

**Aktion:** Entfernen Sie den oben genannten Knoten.

### Pfad-Browser-Eigenschaften {#path-browser-predicates-1}

| Knoten im Standard-Suchformular in 6.1 | pathbrowser |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/pathbrowserpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/pathbrowserpredicate |

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Eigenschaften des MIME-Typs {#mime-type-predicates}

| Knoten im Standard-Suchformular in 6.1 | mimetype |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Dateigrößen-Eigenschaften {#file-size-predicates}

| Knoten im Standard-Suchformular in 6.1 | filesize |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/filesizepredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/sliderangepredicate |

**Aktion:** Passen Sie die Eigenschaft `resourceType` wie beim oben für 6.2 angegebenen Pfad an.

### Eigenschaften für letzte Änderung des Assets {#asset-last-modified-predicates}

| Knoten im Standard-Suchformular in 6.1 | assetlastmodifiedpredicate |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/assetlastmodifiedpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/assetlastmodifiedpredicate |

Aktion: Passen Sie die Eigenschaft „resourceType“ an (fügen Sie „/coral“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Veröffentlichungseigenschaft {#publish-predicate}

| Knoten im Standard-Suchformular in 6.1 | publish |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/publishpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/publishpredicate |

**Aktionen:**

* Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

* Fügen Sie eine Eigenschaft `optionPaths` (vom Typ „String“) mit folgendem Wert hinzu: `/libs/dam/options/predicates/publish`

* Fügen Sie die Eigenschaft `singleSelect` mit dem booleschen Wert `true` hinzu.

### Statuseigenschaften {#status-predicates}

| Knoten im Standard-Suchformular in 6.1 | status |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Eigenschaften für Gültigkeitsdauer {#expiry-status-predicates}

| Knoten im Standard-Suchformular in 6.1 | expirystatus |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/expiredassetpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/expiredassetpredicate |

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Eigenschaften für Metadaten-Gültigkeit {#metadata-validity-predicates}

| Knoten im Standard-Suchformular in 6.1 | metadatavalidity |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Bewertungseigenschaften {#rating-predicates}

| Knoten im Standard-Suchformular in 6.1 | Bewertung |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/ratingpredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/sliderangepredicate |

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Ausrichtungseigenschaft {#orientation-predicate}

| Knoten im Standard-Suchformular in 6.1 | Ausrichtung |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/tagsfilterpredicate |
| Ressourcentyp in 6.2 | cq/gui/components/coral/common/admin/customsearch/searchpredicates/tagspredicate |

**Aktionen:**

* Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

* Fügen Sie eine Eigenschaft `fieldLabel` mit dem gleichen Wert wie für die Eigenschaft `text` auf demselben Knoten hinzu.

* Fügen Sie eine Eigenschaft `emptyText` mit dem gleichen Wert wie für die Eigenschaft `text` auf demselben Knoten hinzu.

* Fügen Sie eine Eigenschaft `rootPath` mit dem gleichen Wert wie für die Eigenschaft `optionPaths` auf demselben Knoten hinzu.

### Stileigenschaft {#style-predicate}

| Knoten im Standard-Suchformular in 6.1 | Stil |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/tagsfilterpredicate |
| Ressourcentyp in 6.2 | cq/gui/components/coral/common/admin/customsearch/searchpredicates/tagspredicate |

**Aktionen:**

* Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

* Fügen Sie eine Eigenschaft `fieldLabel` mit dem gleichen Wert wie für die Eigenschaft `text` auf demselben Knoten hinzu.

* Fügen Sie eine Eigenschaft `emptyText` mit dem gleichen Wert wie für die Eigenschaft `text` auf demselben Knoten hinzu.

* Fügen Sie eine Eigenschaft `rootPath` mit dem gleichen Wert wie für die Eigenschaft `optionPaths` auf demselben Knoten hinzu.

### Videoformat-Eigenschaften {#video-format-predicates}

| Knoten im Standard-Suchformular in 6.1 | videoFormat |
|---|---|
| Ressourcentyp in 6.1 | dam/gui/components/admin/customsearch/searchpredicates/optionspredicate |
| Ressourcentyp in 6.2 | dam/gui/coral/components/admin/customsearch/searchpredicates/optionspredicate |

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).

### Eigenschaft für Haupt-Asset {#mainasset-predicate}

| Knoten im Standard-Suchformular in 6.1 | mainasset |
|---|---|
| Ressourcentyp in 6.1 | granite/ui/components/foundation/form/hidden |
| Ressourcentyp in 6.2 | granite/ui/components/coral/foundation/form/hidden |

**Aktion:** Passen Sie die Eigenschaft `resourceType` an (fügen Sie „**/coral**“ wie beim oben für 6.2 angegebenen Pfad hinzu).
