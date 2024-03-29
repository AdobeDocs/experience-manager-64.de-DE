---
title: Erweitern der Asset-Suche
description: Erweiterung der Suchfunktionen von [!DNL Experience Manager] Assets werden nicht standardmäßig nach Assets anhand von Zeichenfolgen gesucht.
contentOwner: AG
feature: Search
role: Developer
exl-id: d68c735f-2699-4923-a7e7-4d1356eae335
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 63%

---

# Erweitern der Asset-Suche {#extending-assets-search}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können die Suchfunktionen von Adobe Experience Manager Assets erweitern. Vorkonfiguriert, [!DNL Experience Manager] Assets sucht nach Assets anhand von Zeichenfolgen.

Die Suchfunktion wird über die QueryBuilder-Schnittstelle durchgeführt und lässt sich mit mehreren Eigenschaften anpassen. Sie können den Standardsatz der Eigenschaften im folgenden Verzeichnis überlagern: `/apps/dam/content/search/searchpanel/facets`.

Sie können dem [!DNL Experience Manager] Asset-Admin-Bedienfeld.

>[!CAUTION]
>
>Seit Einführung von [!DNL Experience Manager] 6.4 ist die klassische Benutzeroberfläche veraltet. Informationen zur Ankündigung finden Sie unter [Eingestellte und entfernte Funktionen](../release-notes/deprecated-removed-features.md). Es wird empfohlen, die Touch-optimierte Benutzeroberfläche zu verwenden. Informationen zu Anpassungen finden Sie unter [Suchfacetten](search-facets.md).

## Überlagerung {#overlaying}

Um die vorkonfigurierten Eigenschaften zu überlagern, kopieren Sie den Knoten `facets` aus `/libs/dam/content/search/searchpanel` nach `/apps/dam/content/search/searchpanel/` oder geben Sie eine weitere `facetURL`-Eigenschaft in die Konfiguration des Suchfensters ein (standardmäßig `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

![screen_shot_2012-06-05at113619am](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>Standardmäßig wird die Verzeichnisstruktur unter / `apps` existiert nicht und muss erstellt werden. Stellen Sie sicher, dass die Knotentypen mit den Typen unter / übereinstimmen. `libs`.

## Hinzufügen von Registerkarten {#adding-tabs}

Sie können zusätzliche Suchregisterkarten hinzufügen, indem Sie sie im [!DNL Experience Manager] Asset-Admin. So erstellen Sie weitere Registerkarten:

1. Erstellen Sie die Ordnerstruktur `/apps/wcm/core/content/damadmin/tabs,`, falls noch nicht vorhanden, kopieren Sie den Knoten `tabs` aus `/libs/wcm/core/content/damadmin` und fügen Sie ihn ein.
1. Erstellen und konfigurieren Sie die zweite Registerkarte wie gewünscht.

   >[!NOTE]
   >
   >Wenn Sie ein zweites siteadminsearchpanel erstellen, stellen Sie sicher, dass Sie eine `id` -Eigenschaft, um Formularkonflikte zu vermeiden.

## Erstellen benutzerdefinierter Eigenschaften {#creating-custom-predicates}

[!DNL Experience Manager] Assets umfasst einen Satz vordefinierter Eigenschaften, mit denen eine Asset-Freigaben-Seite angepasst werden kann. Diese Art der Anpassung einer Asset-Freigabe wird unter [Erstellen und Konfigurieren einer Asset-Freigaben-Seite](assets-finder-editor.md#creating-and-configuring-an-asset-share-page) beschrieben.

[!DNL Experience Manager]-Entwicklerinnen und -Entwickler können neben den bereits vorhandenen Prädikaten auch eigene Prädikate erstellen. Hierfür können sie die [QueryBuilder-API](/help/sites-developing/querybuilder-api.md) verwenden.

Um benutzerdefinierte Eigenschaften erstellen zu können, benötigen Sie Grundlagenkenntnisse über das [Widget-Framework](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html).

Es empfiehlt sich, ein vorhandenes Prädikat zu kopieren und anzupassen. Beispielprädikate finden Sie unter `/libs/cq/search/components/predicates`.

### Beispiel: Einfaches Eigenschaftsprädikat erstellen   {#example-build-a-simple-property-predicate}

So erstellen Sie ein Eigenschaftsprädikat:

1. Erstellen Sie einen Komponentenordner in Ihrem Projektverzeichnis, z. B. `/apps/geometrixx/components/titlepredicate`.
1. Hinzufügen `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Fügen Sie `titlepredicate.jsp` hinzu.

   ```xml
   <%--
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
   
       });
   
   </script>
   ```

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. Um eine Komponente bearbeitbar zu machen, fügen Sie in CRXDE einen Knoten hinzu `cq:editConfig` Primärtyp `cq:EditConfig`. Damit Sie Absätze entfernen können, fügen Sie die Eigenschaft `cq:actions` mit mehreren Werten mit dem einzelnen Wert **LÖSCHEN** hinzu.
1. Navigieren Sie zu Ihrem Browser und auf Ihrer Beispielseite (z. B. `press.html`) in den Designmodus wechseln und Ihre neue Komponente für das Prädikat-Absatzsystem aktivieren (z. B. **left**).

1. Im Modus **Bearbeiten** ist die neue Komponente jetzt im Sidekick verfügbar (in der **Suchgruppe**). Fügen Sie die Komponente in die Spalte **Eigenschaften** ein, geben Sie einen Suchbegriff – z. B. **Raute** – ein und klicken Sie auf das Lupensymbol, um die Suche zu starten.

   >[!NOTE]
   >
   >Stellen Sie beim Suchen sicher, dass der Begriff korrekt eingegeben wird und auch die Groß-/Kleinschreibung stimmt.

### Beispiel: Einfache Gruppeneigenschaft erstellen {#example-build-a-simple-group-predicate}

So erstellen Sie eine Gruppeneigenschaft:

1. Erstellen Sie einen Komponentenordner in Ihrem Projektverzeichnis, z. B. `/apps/geometrixx/components/picspredicate`.
1. Hinzufügen `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Hinzufügen `titlepredicate.jsp`:

   ```java
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
   
       });
   ```

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. Um eine Komponente bearbeitbar zu machen, fügen Sie in CRXDE einen Knoten hinzu `cq:editConfig` Primärtyp `cq:EditConfig`. Um Absätze entfernen zu können, fügen Sie eine `cq:actions`-Mehrwerteigenschaft mit `DELETE` als einzigem Wert hinzu.
1. Navigieren Sie zu Ihrem Browser und auf Ihrer Beispielseite (z. B. `press.html`) in den Designmodus wechseln und Ihre neue Komponente für das Prädikat-Absatzsystem aktivieren (z. B. **left**).
1. Im Modus **Bearbeiten** ist die neue Komponente jetzt im Sidekick verfügbar (in der **Suchgruppe**). Fügen Sie die Komponente in die Spalte **Eigenschaften** ein.

### Installierte Eigenschaften-Widgets {#installed-predicate-widgets}

Die folgenden Eigenschaften sind als vorkonfigurierte ExtJS-Widgets verfügbar.

### FulltextPredicate   {#fulltextpredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `fulltext` |
| searchCallback | Funktion | Callback zum Auslösen der Suche bei Ereignis `keyup`. Standardwert ist `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `property` |
| propertyName | Zeichenfolge | Name der JCR-Eigenschaft. Standardwert ist `jcr:title` |
| defaultValue | Zeichenfolge | Vorgegebener Standardwert. |

### PathPredicate {#pathpredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `path` |
| rootPath | Zeichenfolge | Stammpfad der Eigenschaft. Standardwert ist `/content/dam` |
| pathFieldPredicateName | Zeichenfolge | Standardwert ist `folder` |
| showFlatOption | Boolesch | Markierung zum Anzeigen des Kontrollkästchen `search in subfolders`. Standardwert ist „true“. |

### DatePredicate {#datepredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `daterange` |
| propertyname | Zeichenfolge | Name der JCR-Eigenschaft. Standardwert ist `jcr:content/jcr:lastModified` |
| defaultValue | Zeichenfolge | Vorgegebener Standardwert |

### OptionsPredicate {#optionspredicate}

| Eigenschaft | Typ | Beschreibung |
|---|---|---|
| title | Zeichenfolge | Fügt einen zusätzlichen oberen Titel hinzu |
| predicateName | Zeichenfolge | Name der Eigenschaft. Standardwert ist `daterange` |
| propertyname | Zeichenfolge | Name der JCR-Eigenschaft. Standardwert ist `jcr:content/metadata/cq:tags` |
| collapse | Zeichenfolge | Ebene der Reduzierung. Standardwert ist `level1` |
| triggerSearch | Boolesch | Markierung zum Auslösen der Suche nach Aktivierung. Standardwert ist „false“ |
| searchCallback | Funktion | Callback zum Auslösen der Suche. Standardwert ist `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | Nummer | Zeitlimit, nach dem searchCallback ausgelöst wird. Standardwert ist 800 ms. |

## Anpassen der Suchergebnisse {#customizing-search-results}

Die Darstellung von Suchergebnissen in einer Asset-Freigaben-Seite wird durch die ausgewählte Linse geregelt. [!DNL Experience Manager] Assets enthält einen Satz vordefinierter Linsen, mit denen eine Asset-Freigabe-Seite angepasst werden kann. Diese Art der Anpassung einer Asset-Freigabe wird unter [Erstellen und Konfigurieren einer Asset-Freigaben-Seite](assets-finder-editor.md#creating-and-configuring-an-asset-share-page) beschrieben.

Zusätzlich zu den bereits vorhandenen Linsen können [!DNL Experience Manager]-Entwicklerinnen und -Entwickler auch eigene Linsen erstellen.
