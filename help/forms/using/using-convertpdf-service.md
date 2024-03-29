---
title: ConvertPDF-Service
seo-title: ConvertPDF Service
description: Verwenden Sie den AEM Forms ConvertPDF-Dienst, um PDF-Dokumente in PostScript- oder Bilddateien zu konvertieren.
seo-description: Use AEM Forms ConvertPDF service to convert PDF documents to PostScript or image files.
uuid: 7fa94c8c-485b-4a77-bcd3-ed716e3cf316
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: 5ec4f0ec-a9fd-4571-9b9a-278f4622c028
exl-id: a6fe7794-3c31-4706-9e23-fe63a506b0bc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 21%

---

# ConvertPDF-Dienst {#convertpdf-service}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Der Convert PDF-Dienst konvertiert PDF-Dokumente in PostScript- oder Bilddateien (JPEG, JPEG 2000, PNG und TIFF). Die Konvertierung eines PDF-Dokuments in PostScript ist für den unbeaufsichtigten serverbasierten Druck auf einem beliebigen PostScript-Drucker nützlich. Das Konvertieren eines PDF-Dokuments in eine mehrseitige TIFF-Datei ist bei der Archivierung von Dokumenten in Content-Management-Systemen praktisch, die keine PDF-Dokumente unterstützen.

Mit dem Convert PDF-Dienst können Sie Folgendes ausführen:

* Konvertieren von PDF-Dokumenten in PostScript – Beim Konvertieren in PostScript können Sie den Konvertierungsvorgang verwenden, um das Quelldokument anzugeben und festzulegen, ob es in PostScript Level 2 oder 3 konvertiert werden soll. Das PDF-Dokument, das Sie in eine PostScript-Datei konvertieren, muss nicht interaktiv sein.
* Konvertieren Sie PDF-Dokumente in die Bildformate JPEG, JPEG 2000, PNG und TIFF. Beim Konvertieren in eines dieser Bildformate können Sie den Konvertierungsvorgang verwenden, um das Quelldokument und eine Spezifikation für Bildoptionen anzugeben. Die Spezifikation enthält verschiedene Voreinstellungen, z. B. das Bildkonvertierungsformat, die Bildauflösung und die Farbkonvertierung.

## Eigenschaften des Dienstes konfigurieren   {#properties}

Sie können die **AEMFD ConvertPDF-Dienst** in AEM Console , um Eigenschaften für diesen Dienst zu konfigurieren. Die Standard-URL der AEM-Konsole lautet `https://[host]:[port]/system/console/configMgr`.

## Verwenden des Dienstes {#using-the-service}

Der ConvertPDF-Dienst stellt die beiden folgenden APIs bereit:

* **[toPS](https://helpx.adobe.com/de/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toPS)**: Konvertiert ein PDF-Dokument in eine PostScript-Datei.

* **[toImage](https://helpx.adobe.com/de/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage)**: Konvertiert ein PDF-Dokument in eine Bilddatei. Unterstützte Bildformate sind JPEG, JPEG2000, PNG und TIFF.

### Verwenden der toPS-API mit einer JSP oder Servlets {#using-tops-api-with-a-jsp-or-servlets}

```java
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToPSOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.PSLevel,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation 
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // please replace this with path to your document
String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for 
 // the flat PDF file which needs to be converted 
 // to PostScript

 Document inputPDF = new Document(documentPath);

 // options object to pass to toPS API
 ToPSOptionsSpec toPSOptions = new ToPSOptionsSpec();

 // mandatory option to pass, sets PostScript langauge
 toPSOptions.setPsLevel(PSLevel.LEVEL_3);

 // invoke toPS method to convert inputPDF to PostScript
 Document convertedPS = cpdfService.toPS(inputPDF, toPSOptions);

 // save converted PostScript file to disk
 convertedPS.copyToFile(new File("C:/temp/out.ps"));

%>
```

### Verwenden der toImage-API mit einer JSP oder Servlets {#using-toimage-api-with-a-jsp-or-servlets}

```java
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToImageOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.ImageConvertFormat,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation 
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // please replace this with path to your document
 String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for 
 // the flat PDF file which needs to be converted 
 // to image

 Document inputPDF = new Document(documentPath);

 // options object to pass to toImage API
 ToImageOptionsSpec toImageOptions = new ToImageOptionsSpec();

 // mandatory option to pass, image format
 toImageOptions.setImageConvertFormat(ImageConvertFormat.JPEG);

 // invoke toImage method to convert inputPDF to Image
 List<Document> convertedImages = cpdfService.toImage(inputPDF, toImageOptions);

 // save converted image files to disk
 for(int i=0;i<convertedImages.size();i++){
     Document pageImage = convertedImages.get(i);
     pageImage.copyToFile(new File("C:/temp/out_"+(i+1)+".jpeg"));
 }

%>
```

### Verwenden des ConvertPDF-Dienstes mit AEM Workflows {#using-convertpdf-service-with-aem-workflows}

Das Ausführen des ConvertPDF-Dienstes über einen Workflow ähnelt dem Ausführen über JSP/Servlet.

Der einzige Unterschied besteht darin, dass der Dienst von JSP/Servlet ausgeführt wird. Das Dokumentobjekt ruft automatisch eine Instanz des ResourceResolver-Objekts aus dem ResourceResolverHelper-Objekt ab. Dieser automatische Mechanismus\
funktioniert nicht, wenn der Code aus einem Workflow aufgerufen wird. Bei einem Workflow müssen Sie ausdrücklich eine Instanz des ResourceResolver-Objekts an die Dokument-Klassen-Konstruktor übermitteln. Anschließend verwendet das Dokumentobjekt\
bereitgestelltes ResourceResolver -Objekt zum Lesen von Inhalten aus dem Repository.

Der folgende Beispiel-Workflow-Prozess konvertiert das Eingabedokument in ein PostScript-Dokument. Der Code wird in ECMAScript geschrieben und das Dokument wird als Workflow-Payload übergeben:

```
/*
 * Imports 
 */
var ConvertPdfService = Packages.com.adobe.fd.cpdf.api.ConvertPdfService;
var ToPSOptionsSpec = Packages.com.adobe.fd.cpdf.api.ToPSOptionsSpec;
var PSLevel = Packages.com.adobe.fd.cpdf.api.enumeration.PSLevel;
var Document = Packages.com.adobe.aemfd.docmanager.Document;
var File = Packages.java.io.File;
var ResourceResolverFactory = Packages.org.apache.sling.api.resource.ResourceResolverFactory;

// get reference to ConvertPdfService
var cpdfService = sling.getService(ConvertPdfService);

/*
 * workflow payload and path to it
 */
var payload = graniteWorkItem.getWorkflowData().getPayload();
var payload_path = payload.toString();

/* Create resource resolver using current session 
 * this resource resolver needs to be passed to Document
 * object constructor when file is to be read from 
 * crx repository. 
 */

/* get ResourceResolverFactory service reference , used 
 * to construct resource resolver
 */
var resourceResolverFactory = sling.getService(ResourceResolverFactory);

var authInfo = {
    "user.jcr.session":graniteWorkflowSession.getSession()
};

var resourceResolver = resourceResolverFactory.getResourceResolver(authInfo);

// Create Document object from payload_path 
var inputDocument = new Document(payload_path, resourceResolver);

// options object to be passed to toPS operation
var toPSOptions = new ToPSOptionsSpec();

// Set PostScript Language Three
toPSOptions.setPsLevel(PSLevel.LEVEL_3);

// invoke toPS operation to convert inputDocument to PS
var convertedPS = cpdfService.toPS(inputDocument, toPSOptions);

// save converted PostScript file to disk
convertedPS.copyToFile(new File("C:/temp/out.ps"));
```
