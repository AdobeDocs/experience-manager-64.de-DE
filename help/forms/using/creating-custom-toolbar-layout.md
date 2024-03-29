---
title: Erstellen eines benutzerdefinierten Symbolleisten-Layouts
seo-title: Creating custom toolbar layout
description: Sie können ein Symbolleistenlayout für das Formular festlegen. Das Symbolleistenlayout definiert die Befehle und das Layout der Symbolleiste im Formular.
seo-description: You can specify a toolbar layout for the form. The toolbar layout defines the commands and the layout of the toolbar on the form.
uuid: da60342c-f802-4264-9da4-c333df9359c2
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: c69bb229-d680-4a55-9b2d-cd5ad0f83a9e
exl-id: 1b273437-8d71-4224-bdcd-0ae522ae8913
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 49%

---

# Erstellen eines benutzerdefinierten Symbolleisten-Layouts {#creating-custom-toolbar-layout}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Symbolleistenlayouts {#layout}

Wenn Sie ein adaptives Formular erstellen, können Sie ein Symbolleistenlayout für das Formular festlegen. Das Symbolleistenlayout definiert die Befehle und das Layout der Symbolleiste im Formular.

Die Verwendung des Symbolleistenlayouts beruht in hohem Maße auf der clientseitigen Verarbeitung, die von komplexem JavaScript- und CSS-Code gesteuert wird. Die Organisation und Optimierung der Bereitstellung dieses Codes kann äußerst kompliziert sein. Um Abhilfe zu schaffen, stellt AEM clientseitige Bibliotheksordner zur Verfügung, mit denen Sie Ihren clientseitigen Code im Repository speichern, in Kategorien gruppieren und definieren können, wann und wie jede Codekategorie dem Client bereitgestellt werden soll. Das clientseitige Bibliotheksystem übernimmt dann das Erstellen der korrekten Links in der endgültigen Webseite, um den korrekten Code zu laden. Detaillierte Informationen finden Sie unter [Funktionsweise clientseitiger Bibliotheken in AEM.](/help/sites-developing/clientlibs.md)

![Beispiellayout der Symbolleiste](assets/default_toolbar_layout.png)
**Abbildung:** *Beispiellayout der Symbolleiste*

Adaptive Formulare bieten einen Satz vordefinierter Layouts:

![Standardmäßig verfügbare Symbolleistenlayouts ](assets/toolbar1.png)
**Abbildung:** *Vordefinierte Symbolleistenlayouts*

Darüber hinaus können Sie ein benutzerdefiniertes Symbolleistenlayout erstellen.

Das folgende Verfahren beschreibt die Schritte zum Erstellen einer benutzerdefinierten Symbolleiste, die drei Aktionen in der Symbolleiste und die anderen Aktionen in einer Dropdown-Liste in der Symbolleiste anzeigt.

Das angehängte Inhaltspaket enthält den gesamten unten beschriebenen Code. Nach der Installation des Inhaltspakets öffnen Sie `/content/forms/af/CustomLayoutDemo.html`, um das Beispiel für ein benutzerdefiniertes Symbolleisten-Layout anzuzeigen.

CustomToolbarLayoutDemo.zip

[Datei abrufen](assets/customtoolbarlayoutdemo.zip)
Beispiel für ein benutzerdefiniertes Symbolleisten-Layout

## So erstellen Sie ein benutzerdefiniertes Symbolleistenlayout {#layout-1}

1. Erstellen Sie einen Ordner, um Ihre benutzerdefinierten Symbolleistenlayouts zu verwalten. Beispiel:

   `/apps/customlayout/toolbar`.

   Um ein benutzerdefiniertes Layout zu erstellen, können Sie eines der standardmäßigen Symbolleistenlayouts verwenden (und anpassen), die im folgenden Ordner verfügbar sind:

   `/libs/fd/af/layouts/toolbar`

   Kopieren Sie zum Beispiel den Knoten `mobileFixedToolbarLayout` aus dem Ordner `/libs/fd/af/layouts/toolbar` in den Ordner `/apps/customlayout/toolbar`.

   Kopieren Sie außerdem „toolbarCommon.jsp“ in den Ordner `/apps/customlayout/toolbar`/.

   >[!NOTE]
   >
   >Der Ordner, den Sie für die benutzerdefinierten Layouts erstellen, muss mit dem Ordner `apps` erstellt werden.

1. Benennen Sie den kopierten Knoten `mobileFixedToolbarLayout` in `customToolbarLayout.` um.

   Geben Sie außerdem eine relevante Beschreibung für den Knoten an. Ändern Sie beispielsweise die jcr:description des Knotens in **Benutzerdefiniertes Layout für Symbolleiste**.

   Die Eigenschaft `guideComponentType` des Knotens legt den Layouttyp fest. In diesem Fall ist der Layouttyp „Symbolleiste“. Daher wird er in der Auswahl-Dropdown-Liste für das Symbolleistenlayout angezeigt.

   ![Ein Knoten mit relevanter Beschreibung](assets/toolbar3.png)

   Ein Knoten mit relevanter Beschreibung

   Das neue benutzerdefinierte Symbolleistenlayout wird im Dialogfeld **Adaptive Form Toolbar** (Symbolleiste des adaptiven Formulars) angezeigt.

   ![Liste der verfügbaren Symbolleistenlayouts](assets/toolbar4.png)

   Liste der verfügbaren Symbolleisten-Layouts

   >[!NOTE]
   >
   >Die im vorherigen Schritt aktualisierte Beschreibung wird in der Dropdown-Liste Layout angezeigt.

1. Wählen Sie dieses benutzerdefinierte Symbolleistenlayout aus und klicken Sie auf &quot;OK&quot;.

   Fügen Sie clientlib (javascript und css) im Knoten `/etc/customlayout` hinzu und nehmen Sie den Verweis der clientlib in `customToolbarLayout.jsp` auf.

   ![Pfad der Datei customToolbarLayout.css](assets/toolbar_3.png)

   Pfad der Datei customToolbarLayout.css

   Beispiel `customToolbarLayout.jsp`:

   ```php
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <cq:includeClientLib categories="customtoolbarlayout" />
   <c:if test="${isEditMode}">
           <cq:includeClientLib categories="customtoolbarlayoutauthor" />
   </c:if>
   <div class="guidetoolbar mobileToolbar mobilecustomToolbar" data-guide-position-class="guide-element-hide">
       <div data-guide-scroll-indicator="true"></div>            
       <%@include file="../toolbarCommon.jsp" %>
   </div>
   ```

   >[!NOTE]
   >
   >Fügen Sie die guidetoolbar-Klasse für das Layout hinzu. Der vordefinierte Stil für die Symbolleiste wird in Bezug auf die guidetoolbar-Klasse definiert.

   Beispiel `toolBarCommon.jsp`:

   ```php
   <%@taglib prefix="fn" uri="https://java.sun.com/jsp/jstl/functions"%>
   <%--------------------  
   This code iterates over all the tool bar items using the guideToolbar bean.
   If the number of toolbar items are more than 3, then we create a dropdown menu using bootstrap for other actions present in the toolbar.
   In both desktop and mobile devices, the layout is different.    
   ---------------------------------%>
   
   <c:forEach items="${guideToolbar.items}" var="toolbarItem" varStatus="loop">
       <c:choose>
         <c:when test="${loop.index gt 2}">
      <c:choose>
       <c:when test="${loop.index eq 3}">
                     <div class="btn-group dropdown">   
                       <button type="button" class="btn btn-primary dropdown-toggle label" data-toggle="dropdown">Actions <span class="caret"></span></button>
                       <button type="button" class="btn btn-primary dropdown-toggle icon" data-toggle="dropdown"><span class="glyphicon glyphicon-th-list"></span></button>
             <ul class="dropdown-menu" role="menu">
                           <li>
                               <div id="${toolbarItem.id}_guide-item">
                                 <sling:include path="${toolbarItem.path}" resourceType="${toolbarItem.resourceType}"/>
                              </div>
                           </li>
                           <c:if test="${loop.index eq (fn:length(guideToolbar.items)-1)}">
                                </ul>
                                </div>
                           </c:if>
       </c:when>
       <c:when test="${loop.index eq (fn:length(guideToolbar.items)-1)}">
                          <li>
                                     <div id="${toolbarItem.id}_guide-item">
                                         <sling:include path="${toolbarItem.path}" resourceType="${toolbarItem.resourceType}"/>
                                     </div>
                           </li>
                       </ul>
                     </div>
   
       </c:when>
       <c:otherwise>
         <li>
          <div id="${toolbarItem.id}_guide-item">
           <sling:include path="${toolbarItem.path}" resourceType="${toolbarItem.resourceType}"/>
          </div>
         </li>
       </c:otherwise>
      </c:choose>
         </c:when>
         <c:otherwise>         
     <div id="${toolbarItem.id}_guide-item">
           <sling:include path="${toolbarItem.path}" resourceType="${toolbarItem.resourceType}"/>
        </div>
         </c:otherwise>
    </c:choose>   
   </c:forEach>
   ```

   Das CSS, das im Knoten clientlib vorhanden ist:

   ```css
   .mobilecustomToolbar .dropdown {
       display: inline-block;    
   }
   
   .mobilecustomToolbar .dropdown {
       float: right;   
   }
   
   .mobilecustomToolbar .dropdown > button {
      padding: 6px 12px;  
   }         
   
   .mobilecustomToolbar .dropdown .guideFieldWidget, .mobilecustomToolbar .dropdown .guideFieldWidget button {
       width: 100%;   
   }         
   
   .mobilecustomToolbar .dropdown .caret{
       border-bottom: 6px solid;
       border-right: 6px solid transparent;
       border-left: 6px solid transparent;
    border-top: transparent;                                     
   }
   
   .mobilecustomToolbar .dropdown-menu{
    top: auto;
    bottom: 100%;                            
   }
   
   .mobilecustomToolbar .btn-group {            
    vertical-align: super;            
   }
   
   .mobilecustomToolbar .glyphicon {
    font-size: 24px;
   }
   
   @media (max-width: 767px){                                       
   
    .mobilecustomToolbar .dropdown .guideButton .iconButton-icon {
      display: none;
       }  
   
       .mobilecustomToolbar .dropdown .guideButton .iconButton-label {
      display: inline-block;
       } 
   
       .mobilecustomToolbar .dropdown .guideButton button {
      background-color: #013853;
       }
   
    .mobilecustomToolbar .btn-group {            
     vertical-align: top;            
    }    
   
   }
   ```

>[!NOTE]
>
>Die im vorherigen Schritt aktualisierte Beschreibung wird in der Dropdown-Liste Layout angezeigt.

![Desktop-Ansicht der Symbolleiste mit benutzerdefiniertem Layout](assets/toolbar_1.png)
**Abbildung:** *Desktop-Ansicht der Symbolleiste mit benutzerdefiniertem Layout*
