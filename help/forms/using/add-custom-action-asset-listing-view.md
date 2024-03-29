---
title: Hinzufügen benutzerdefinierter Aktionen zur Ansicht „Asset-Auflistung“
seo-title: Add custom action to the Asset Listing view
description: In diesem Artikel erfahren Sie, wie Sie der Ansicht "Asset-Auflistung"benutzerdefinierte Aktionen hinzufügen
seo-description: This article teaches how to add custom action to the Asset Listing view
uuid: 72ce6c24-2758-4888-b797-1b134acc54d2
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: b35ea921-182f-4371-90f6-482d22694b42
feature: Correspondence Management
exl-id: 00b3efc5-ef1c-4b9d-957d-2eda01c0b985
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1396'
ht-degree: 68%

---

# Hinzufügen benutzerdefinierter Aktionen zur Ansicht „Asset-Auflistung“ {#add-custom-action-to-the-asset-listing-view}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Mit der Correspondence Management-Lösung können Sie benutzerdefinierte Aktionen zur Benutzeroberfläche &quot;Assets verwalten&quot;hinzufügen.

Sie können der Ansicht &quot;Asset-Auflistung&quot;eine benutzerdefinierte Aktion hinzufügen für:

* Ein oder mehrere Asset-Typen oder Briefe
* Ausführung (Aktion/Befehl wird aktiv) bei Auswahl einzelner, mehrerer Assets/Briefe oder ohne Auswahl

Diese Anpassung wird mit dem Szenario veranschaulicht, das der Ansicht &quot;Asset-Auflistung&quot;für Briefe den Befehl &quot;Einfache PDF herunterladen&quot;hinzufügt. Mit diesem Anpassungsszenario können Ihre Benutzer eine einfache PDF eines einzelnen ausgewählten Briefs herunterladen.

### Voraussetzungen {#prerequisites}

Um das folgende Szenario oder ein ähnliches Szenario abzuschließen, benötigen Sie Kenntnisse über:

* CRX
* JavaScript
* Java

## Szenario: Fügen Sie der Benutzeroberfläche der Liste &quot;Briefe&quot;einen Befehl hinzu, um eine einfache PDF-Version eines Briefs herunterzuladen. {#addcommandtoletters}

Im Folgenden wird der Befehl &quot;Einfache PDF herunterladen&quot;zur Ansicht &quot;Asset-Auflistung für Briefe&quot;hinzugefügt, mit dem Ihre Benutzer einfache PDF des ausgewählten Briefs herunterladen können. Mithilfe dieser Schritte mit dem entsprechenden Code und den entsprechenden Parametern können Sie weitere Funktionen für ein anderes Asset hinzufügen, z. B. Datenwörterbücher oder Texte.

Führen Sie die folgenden Schritte aus, um Correspondence Management so anzupassen, dass Ihre Benutzer eine einfache PDF mit Briefen herunterladen können:

1. Wechseln Sie zu `https://[server]:[port]/[ContextPath]/crx/de` und melden Sie sich als Administrator an.

1. Erstellen Sie im Programmordner einen Ordner mit dem Namen „items“ mit einem ähnlichen Pfad/einer ähnlichen Struktur wie der Ordner „items“, der sich im Auswahlordner befindet, indem Sie folgende Schritte durchführen:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL items]** unter dem folgenden Pfad und wählen Sie **[!UICONTROL Überlagerungsknoten]**:

      `/libs/fd/cm/ma/gui/content/cmassets/jcr:content/body/content/header/items/selection/items`

      >[!NOTE]
      >
      >Dieser Pfad ist spezifisch für das Erstellen einer Aktion, die mit der Auswahl eines oder mehrerer Assets/Briefe funktioniert. Wenn Sie eine Aktion erstellen möchten, die ohne Auswahl funktioniert, müssen Sie stattdessen einen Überlagerungsknoten für den folgenden Pfad erstellen und die verbleibenden Schritte entsprechend ausführen:
      >
      >
      >`/libs/fd/cm/ma/gui/content/cmassets/jcr:content/body/content/header/items/default/items`

      ![Knoten erstellen](assets/1_itemscreatenode.png)

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **[!UICONTROL Pfad]**: /libs/fd/cm/ma/gui/content/cmassets/jcr:content/body/content/header/items/selection/items

      **[!UICONTROL Speicherort]**: /apps/

      **[!UICONTROL Knotentypen abgleichen]**: Ausgewählt

      ![Überlagerungsknoten](assets/2_createnodedownloadflatpdf.png)

   1. Klicken Sie auf **[!UICONTROL OK]**. Die Ordnerstruktur wird im Apps-Ordner erstellt.

      Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Fügen Sie unter dem neu erstellten Ordner „items“ einen Knoten für die benutzerdefinierte Schaltfläche/Aktion in einem bestimmten Asset hinzu (Beispiel: downloadFlatPDF), indem Sie folgende Schritte durchführen:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL items]** und wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Knoten erstellen]**.

   1. Stellen Sie sicher, dass das Dialogfeld „Knoten erstellen“ folgende Werte aufweist und klicken Sie auf **[!UICONTROL OK]**:

      **[!UICONTROL Name]**: downloadFlatPDF (oder der Name, den Sie dieser Eigenschaft geben möchten)

      **[!UICONTROL Typ:]** nt:unstructured

   1. Klicken Sie auf den von Ihnen erstellten Knoten (hier: downloadFlatPDF). CRX zeigt die Eigenschaften des Knotens an.
   1. Fügen Sie dem Knoten (hier: downloadFlatPDF) die folgenden Eigenschaften hinzu und klicken Sie auf **[!UICONTROL Alle speichern]**:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Name</strong></td> 
    <td><strong>Typ</strong></td> 
    <td><strong>Wert und Beschreibung</strong></td> 
    </tr> 
    <tr> 
    <td>Klasse</td> 
    <td>Zeichenfolge</td> 
    <td>foundation-collection-action</td> 
    </tr> 
    <tr> 
    <td>foundation-collection-action</td> 
    <td>Zeichenfolge</td> 
    <td><p>{"target": ".cq-manageasset-admin-childpages", "activeSelectionCount": "single","type": "LETTER"}<br /> <br /> <br /> <strong>activeSelectionCount</strong> kann sich auf einzelne oder mehrere Assets beziehen, und es können ein einzelnes oder mehrere Assets für die Durchführung von benutzerdefinierten Aktionen ausgewählt werden.</p> <p><strong>type</strong> kann einen oder mehrere der folgenden Typen enthalten (mehrere Einträge werden durch Komma getrennt): LETTER,TEXT,LIST,CONDITION,DATADICTIONARY</p> </td> 
    </tr> 
    <tr> 
    <td>Symbol</td> 
    <td>Zeichenfolge</td> 
    <td>icon-download<br /> <br /> Das Symbol, das Correspondence Management auf der linken Seite Ihres Befehls/Menüs anzeigt. Informationen zu den verfügbaren Symbolen und Einstellungen finden Sie in der <a href="https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de" target="_blank">CoralUI Icons-Dokumentation</a>.<br /> </td> 
    </tr> 
    <tr> 
    <td>jcr:primaryType</td> 
    <td>Name</td> 
    <td>nt:unstructured</td> 
    </tr> 
    <tr> 
    <td>rel</td> 
    <td>Zeichenfolge</td> 
    <td>download-flach-pdf-button</td> 
    </tr> 
    <tr> 
    <td>sling:resourceType</td> 
    <td>Zeichenfolge</td> 
    <td>granite/ui/components/endor/actionbar/button</td> 
    </tr> 
    <tr> 
    <td>text</td> 
    <td>Zeichenfolge</td> 
    <td>Einfache PDF herunterladen (oder eine andere Bezeichnung)<br /> <br /> Der Befehl, der in der Benutzeroberfläche "Asset-Auflistung"angezeigt wird</td> 
    </tr> 
    <tr> 
    <td>title</td> 
    <td>Zeichenfolge</td> 
    <td>Herunterladen einer flachen PDF des ausgewählten Briefs (oder einer anderen Beschriftung/Alternativtext)<br /> <br /> Der Titel ist der Alternativtext, den Correspondence Management anzeigt, wenn der Benutzer den Mauszeiger über den benutzerdefinierten Befehl bewegt.</td> 
    </tr> 
    </tbody> 
    </table>

1. Erstellen Sie im Programmordner einen Ordner mit dem Namen „js“ mit einem ähnlichen Pfad/einer ähnlichen Struktur zum Ordner „items“, der sich im Administratorordner befindet, indem Sie folgende Schritte durchführen:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL js]** unter dem folgenden Pfad und wählen Sie **[!UICONTROL Überlagerungsknoten]**: &quot;

      `/libs/fd/cm/ma/gui/components/admin/clientlibs/admin/js`

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **[!UICONTROL Pfad:]** /libs/fd/cm/ma/gui/components/admin/clientlibs/admin/js

      **[!UICONTROL Speicherort]**: /apps/

      **[!UICONTROL Übereinstimmende Knotentypen:]** Ausgewählt

   1. Klicken Sie auf **[!UICONTROL OK]**. Die Ordnerstruktur wird im Apps-Ordner erstellt. Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Erstellen Sie im Ordner „js“ eine Datei mit dem Namen „formaction.js“ mit dem Code für Aktionsbearbeitung der Schaltfläche, indem Sie folgende Schritte durchführen:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL js]** mit dem folgenden Pfad und wählen Sie **[!UICONTROL Erstellen > Datei erstellen]**:

      `/apps/fd/cm/ma/gui/components/admin/clientlibs/admin/js`

      Benennen Sie die Datei als „formaction.js“.

   1. Doppelklicken Sie auf die Datei, um sie in CRX zu öffnen.
   1. Kopieren Sie in der Datei „formaction.js“ (unter der /apps-Verzweigung), den Code aus der Datei „formaction.js“ am folgenden Speicherort:

      `/libs/fd/cm/ma/gui/components/admin/clientlibs/admin/js/formaction.js`

      Hängen Sie dann den folgenden Code an das Ende der Datei „formaction.js“ (unter der /apps-Verzweigung) an und klicken Sie auf **[!UICONTROL Alle speichern]**:

      ```
      /* Action url for xml file to be added.*/
      var ACTION_URL = "/apps/fd/cm/ma/gui/content/commons/actionhandlers/items/letterpdfdownloader.html";
      
      /* File upload handling*/
      var fileSelectedHandler = function(e){
          if(e && e.target && e.target.value)
              $(".downloadLetterPDFBtn").removeAttr('disabled');
          else
              $(".downloadLetterPDFBtn").attr('disabled','disabled');
      }
      
      /*Handing of Download button in pop up.*/
      var downloadClickHandler = function(){
          $('#downloadLetterPDFDilaog').modal("hide");
          var element = $('.foundation-selections-item');
          var path = $(element).data("path");
          $("#fileUploadForm").attr('action', ACTION_URL + "?letterId="+path).submit();
      }
      
      /*Click handling on action button.*/
      $(document).on("click",'.download-flat-pdf-button',function(e){
          $("#uploadSamepledata").val("");
           if($('#downloadLetterPDFDilaog').length == 0){
              $(document).on("click",".downloadLetterPDFBtn",downloadClickHandler);
              $(document).on("change","#uploadSamepledata",fileSelectedHandler);
              $("body").append(downloadLetterPDFDilaog);
          }
            $('#downloadLetterPDFDilaog').modal("show");
      });
      
      /*Download popup.*/
      var downloadLetterPDFDilaog = '<div id="downloadLetterPDFDilaog" class="coral-Modal notice " role="dialog"  aria-hidden="true">'+
          '<form id="fileUploadForm" method="POST" enctype="multipart/form-data">'+
              '<div class="coral-Modal-header">'+
                  '<h2 class="coral-Modal-title coral-Heading coral-Heading--2" id="modal-header1443020790107-label" tabindex="0">Download Letter as PDF.</h2>'+
                  '<button type="button" class="coral-MinimalButton coral-Modal-closeButton" data-dismiss="modal">×</button>'+
              '</div>'+
              '<div class="coral-Modal-body" id="modal-header1443020790107-message" role="document" tabindex="0">'+
                  '<div class="coral-Modal-message">'+
                      '<p></p>'+
                  '</div>'+
                  '<div class="coral-Modal-uploader">'+
                      '<p>Select sample data for letter.</p>'+
                      '<input type="file" id="uploadSamepledata" name="file" accept=".xml" size="70px">'+
                  '</div>'+
              '</div>'+
           '</form>'+
              '<div class="coral-Modal-footer">'+
                  '<button type="button" class="coral-Button" data-dismiss="modal">Cancel</button>'+
                  '<button type="button" class="coral-Button coral-Button--primary downloadLetterPDFBtn" disabled="disabled">Download</button>'+
              '</div>'+
      '</div>';
      ```

      Der Code, den Sie in diesem Schritt hinzufügen, überschreibt den Code im Ordner &quot;libs&quot;. Kopieren Sie daher den vorherigen Code in die Datei &quot;formaction.js&quot;in der Verzweigung /apps . Durch das Kopieren des Codes aus der /libs-Verzweigung in die /apps-Verzweigung wird sichergestellt, dass auch die vorherigen Funktionen funktionieren.

      Der obige Code dient der briefspezifischen Aktionsbearbeitung des in diesem Verfahren erstellten Befehls. Für die Aktionsbearbeitung anderer Assets ändern Sie den JavaScript-Code.

1. Erstellen Sie im Programmordner einen Ordner mit dem Namen „items“ mit einem ähnlichen Pfad/einer ähnlichen Struktur wie der Ordner „items“, der sich im Ordner „actionhandlers“ befindet, indem Sie folgende Schritte durchführen:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL items]** unter dem folgenden Pfad und wählen Sie **[!UICONTROL Überlagerungsknoten]**:

      `/libs/fd/cm/ma/gui/content/commons/actionhandlers/items/`

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **[!UICONTROL Pfad]**: /libs/fd/cm/ma/gui/content/commons/actionhandlers/items/

      **[!UICONTROL Speicherort]**: /apps/

      **[!UICONTROL Übereinstimmende Knotentypen:]** Ausgewählt

   1. Klicken Sie auf **[!UICONTROL OK]**. Die Ordnerstruktur wird im Apps-Ordner erstellt.

   1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Fügen Sie unter dem neu erstellten Ordner „items“ einen Knoten für die benutzerdefinierte Schaltfläche/Aktion in einem bestimmten Asset hinzu (Beispiel: letterpdfdownloader), indem Sie folgende Schritte durchführen:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner „items“ und wählen Sie **[!UICONTROL Erstellen > Knoten erstellen]**.

   1. Stellen Sie sicher, dass das Dialogfeld „Knoten erstellen“ folgende Werte aufweist und klicken Sie auf **[!UICONTROL OK]**:

      **[!UICONTROL Name]**: letterpdfdownloader (oder der Name, den Sie dieser Eigenschaft geben möchten – muss eindeutig sein. Wenn Sie hier einen anderen Namen verwenden, geben Sie denselben Namen auch in der Variablen ACTION_URL der Datei „formaction.js“ an.)

      **[!UICONTROL Typ:]** nt:unstructured

   1. Klicken Sie auf den von Ihnen erstellten Knoten (hier: downloadFlatPDF). CRX zeigt die Eigenschaften des Knotens an.

   1. Fügen Sie dem Knoten (hier: letterpdfdownloader) die folgenden Eigenschaften hinzu und klicken Sie auf **[!UICONTROL Alle speichern]**:

      | **Name** | **Typ** | **Wert** |
      |---|---|---|
      | sling:resourceType | Zeichenfolge | fd/cm/ma/gui/components/admin/clientlibs/admin |

1. Erstellen Sie eine Datei mit dem Namen „POST.jsp“ mit dem Code für die Aktionsbearbeitung des Befehls im folgenden Speicherort:

   /apps/fd/cm/ma/gui/components/admin/clientlibs/admin

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL admin]** unter dem folgenden Pfad und wählen Sie **[!UICONTROL Erstellen > Datei erstellen]**:

      /apps/fd/cm/ma/gui/components/admin/clientlibs/admin

      Benennen Sie die Datei als „POST.jsp“. (Der Dateiname darf nur „POST.jsp“ lauten.)

   1. Doppelklicken Sie auf die Datei **[!UICONTROL POST.jsp]**, um sie in CRX zu öffnen.
   1. Fügen Sie der Datei „POST.jsp“ folgenden Code hinzu und klicken Sie auf **[!UICONTROL Alle speichern]**:

      Dieser Code ist spezifisch für den Brief-Renderdienst. Fügen Sie diesem Code für jedes andere Asset die Java-Bibliotheken dieses Assets hinzu. Weitere Informationen zu AEM Forms-APIs finden Sie unter [AEM Forms-API](https://adobe.com/go/learn_aemforms_javadocs_63_en).

      Weitere Informationen zu AEM-Bibliotheken finden Sie unter den AEM-[Komponenten](/help/sites-developing/components.md).

      ```xml
      /*Import libraries. Here we are downloading letter flat pdf with input xml data so we require letterRender Api. For any other Module functionality we need to first import that library. */            
      <%@include file="/libs/foundation/global.jsp"%>
      <!DOCTYPE html lang="en" PUBLIC "-//W3C//DTD XHTML 1.1//EN" "https://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
      <%@page import="com.adobe.icc.ddg.api.*"%>
      <%@page import="com.adobe.icc.dbforms.obj.*"%>
      <%@page import="com.adobe.icc.render.obj.*" %>
      <%@page import="com.adobe.icc.services.api.*" %>
      <%@page import="org.apache.sling.api.resource.*" %>
      <%@page import="java.io.File" %>
      <%@page import="java.util.*" %>
      <%@page import="com.adobe.livecycle.content.appcontext.AppContextManager"%>
      <%@page import=" com.adobe.icc.dbforms.exceptions.ICCException"%>
      <%@page import="java.io.InputStream" %>
      <%@page import="java.io.FileInputStream" %>
      <%@page import="org.apache.commons.io.IOUtils" %>
      <%@page session="false" contentType="text/html; charset=utf-8"%>
      <%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0"%>
      <%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %>
       <%@page session="false" contentType="text/html; charset=utf-8"%>
      <%
         AppContextManager.setCurrentAppContext("/content/apps/cm");
         /*Get letter id sent in js file.*/
          String letterId = request.getParameter("letterId");
          if(letterId.lastIndexOf("?") != -1)
              letterId = letterId.substring(0, letterId.indexOf("?"));
          String fileName = null;
          String letterName = null;
          InputStream inputStream = null;
          /*Get xml file data*/
          if (slingRequest.getRequestParameter("file") != null)
              inputStream = slingRequest.getRequestParameter("file").getInputStream();
          if(letterId != null){
              String xmlData = null;
              try{
                  xmlData = IOUtils.toString(inputStream, "UTF-8");
              }
              catch (Exception e) {
                  log.error("Xml data does not exists.");
              }
              /*letter Name from letter letter id.*/
              letterName = letterId.substring(letterId.lastIndexOf("/")+1);
              /*Invoking letter render services API.*/
              LetterRenderService letterRenderService = sling.getService(LetterRenderService.class);
              /*using CM renderLetter api to get pdfbytes.*/
              PDFResponseType  pdfResponseType= letterRenderService.renderLetter(letterId,xmlData,true,false,false,false);
              byte[] bytes = null;
              /*Downloading pdf bytes as pdf.*/
              if(pdfResponseType != null && pdfResponseType.getFile() != null){
                  bytes = pdfResponseType.getFile().getDocument();
                  /*set the response header to enable download*/
                  response.setContentType("application/OCTET-STREAM");
                  response.setHeader("Content-Disposition", "attachment;filename=\"" + letterName + ".pdf\"");
                  response.setHeader("Pragma", "cache");
                  response.setHeader("Cache-Control", "private");
                  out.clear();
                  response.getOutputStream().write(bytes);
              }
          }
          else{
              log.error("Letter id does not exists.");
          }
      %>
      ```

## Herunterladen einer einfachen PDF eines Briefs mithilfe von benutzerdefinierten Funktionen {#download-flat-pdf-of-a-letter-using-the-custom-functionality}

Nachdem Sie eine benutzerdefinierte Funktion zum Herunterladen einer einfachen PDF Ihrer Briefe hinzugefügt haben, können Sie eine einfache PDF-Version des von Ihnen ausgewählten Briefs herunterladen, indem Sie folgende Schritte durchführen:

1. Wechseln Sie zu `https://[server]:[port]/[ContextPath]/projects.html` und melden Sie sich an.

1. Wählen Sie **[!UICONTROL Formulare > Briefe]**. Correspondence Management listet die im System verfügbaren Briefe auf.
1. Klicken Sie auf **[!UICONTROL Auswählen]** und dann auf einen Brief, um diesen auszuwählen.
1. Wählen Sie **[!UICONTROL Mehr]** > &lt;Einfache PDF herunterladen> (die anhand der Informationen in diesem Artikel erstellte benutzerdefinierte Funktion). Das Dialogfeld „Brief als PDF herunterladen“ wird angezeigt.

   Der Name des Menüelements, die Funktionalität und der Alternativtext entsprechen der Anpassung, die im [Szenario: Hinzufügen eines Befehls zur Benutzeroberfläche der Liste „Briefe“, um eine einfache PDF-Version eines Briefs herunterzuladen](#addcommandtoletters) erstellt wurde.

   ![Benutzerdefinierte Funktion: Einfache PDF herunterladen](assets/5_downloadflatpdf.png)

1. Wählen Sie im Dialogfeld „Brief als PDF herunterladen“ die entsprechende XML-Datei aus, anhand derer die Daten in der PDF ausgefüllt werden sollen.

   >[!NOTE]
   >
   >Vor dem Herunterladen des Briefs als einfache PDF können Sie mithilfe der Option **[!UICONTROL Bericht erstellen]** die XML-Datei mit den Daten für den Brief erstellen.

   ![Brief als PDF herunterladen](assets/6_downloadflatpdf.png)

   Der Brief wird als einfache PDF auf Ihren Computer heruntergeladen.
