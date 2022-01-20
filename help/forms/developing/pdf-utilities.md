---
title: Arbeiten mit PDF Utilities
seo-title: Working with PDF Utilities
description: Verwenden Sie den PDF Utilities-Dienst, um zwischen PDF- und XDP-Dateiformaten zu konvertieren, PDF-Dokumenteigenschaften festzulegen und abzurufen und XMP Metadaten zu bearbeiten.
seo-description: Use the PDF Utilities service to convert between PDF and XDP file formats, set and retrieve PDF document properties, and manipulate XMP metadata.
uuid: a2ea2359-c547-4f1b-b6ca-f276f816e36a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: d816bf2e-5236-4084-b7c4-c32b72cdff97
role: Developer
exl-id: 1fdabd73-ee74-426b-b815-68022ea27c4e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2565'
ht-degree: 5%

---

# Arbeiten mit PDF Utilities {#working-with-pdf-utilities}

**Über den PDF Utilities-Dienst**

Der PDF Utilities-Dienst kann zwischen PDF- und XDP-Dateiformaten konvertieren, PDF-Dokumenteigenschaften festlegen und abrufen und XMP Metadaten bearbeiten. Bevor Sie beispielsweise ein PDF-Dokument in ein anderes Format konvertieren, sollten Sie seine Eigenschaften überprüfen, um zu bestimmen, welcher Dienstvorgang für die Konvertierung aufgerufen werden soll.

Sie können diese Aufgaben mithilfe des PDF Utilities-Dienstes ausführen:

* Konvertieren Sie PDF-Dokumente in XDP-Dokumente.
* Konvertieren Sie XDP-Dokumente in PDF-Dokumente. (Siehe [Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents).
* Abrufen von PDF-Dokumenteigenschaften. (Siehe [Abrufen von PDF Document Properties](pdf-utilities.md#retrieving-pdf-document-properties).
* Speichern Sie ein PDF-Dokument und optimieren Sie es für eine schnelle Webanzeige. (Siehe [Festlegen von PDF Document Save Modi](pdf-utilities.md#setting-pdf-document-save-modes).

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PDF-Dokumenten in XDP-Dokumente {#converting-pdf-documents-into-xdp-documents}

Sie können die Java- und Webdienst-APIs von PDF Utilities verwenden, um PDF-Dokumente programmgesteuert in XDP-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um ein PDF-Dokument in ein XDP-Dokument zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Konvertierungsvorgang PDF in XDP auf.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert ausführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem eine `PDFUtilityServiceClient` -Objekt. Mit der Webdienst-API wird dies durch die Verwendung einer `PDFUtilityServiceService` -Objekt.

**Aufrufen des Konvertierungsvorgangs PDF in XDP**

Nachdem Sie den Service-Client erstellt haben, können Sie den PDF-zu-XDP-Konvertierungsvorgang aufrufen.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Java-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Webdienst-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Java-API {#convert-pdf-documents-into-xdp-documents-using-the-java-api}

Konvertieren Sie PDF-Dokumente mithilfe der PDF Utilities-API (Java) in XDP-Dokumente:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-pdfutility-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie eine `PDFUtilityServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Aufrufen des Konvertierungsvorgangs PDF in XDP

   Rufen Sie zum Ausführen der Konvertierung die `PDFUtilityServiceClient` -Objekt `convertPDFtoXDP` -Methode und Übergabe einer `com.adobe.idp.Document` -Objekt, das die PDF-Datei darstellt. Die Methode gibt eine `com.adobe.idp.Document` -Objekt, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Webdienst-API {#convert-pdf-documents-into-xdp-documents-using-the-web-service-api}

Konvertieren Sie PDF-Dokumente mithilfe der PDF Utilities-API (Webdienst) in XDP-Dokumente:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie eine `PDFUtilityServiceService` -Objekt mithilfe des Proxy-Klassenkonstruktors.

1. Aufrufen des Konvertierungsvorgangs PDF in XDP

   Rufen Sie die `PDFUtilityServiceService` -Objekt `convertPDFtoXDP` -Methode und Übergabe einer `BLOB` -Objekt, das die PDF-Datei darstellt. Die Methode gibt eine `BLOB` -Objekt, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Konvertieren von XDP-Dokumenten in PDF-Dokumente {#converting-xdp-documents-into-pdf-documents}

Sie können die Java- und Webdienst-APIs von PDF Utilities verwenden, um XDP-Dokumente programmgesteuert in PDF-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Gehen Sie wie folgt vor, um ein XDP-Dokument in ein PDF-Dokument zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Konvertierungsvorgang &quot;XDP auf PDF&quot;auf.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert ausführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem eine `PDFUtilityServiceClient` -Objekt. Mit der Webdienst-API wird dies durch die Verwendung einer `PDFUtilityServiceService` -Objekt.

**Aufrufen des Konvertierungsvorgangs &quot;XDP auf PDF&quot;**

Nachdem Sie den Service-Client erstellt haben, können Sie den Konvertierungsvorgang &quot;XDP zu PDF&quot;aufrufen.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der Java-API](pdf-utilities.md#convert-xdp-documents-into-pdf-documents-using-the-java-api)

[Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der Webdienst-API](pdf-utilities.md#converting-xdp-documents-into-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der Java-API {#convert-xdp-documents-into-pdf-documents-using-the-java-api}

Konvertieren Sie XDP-Dokumente mithilfe der PDF Utilities-API (Java) in PDF-Dokumente:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-pdfutility-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie eine `PDFUtilityServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Aufrufen des Konvertierungsvorgangs &quot;XDP auf PDF&quot;

   Rufen Sie zum Ausführen der Konvertierung die `PDFUtilityServiceClient` -Objekt `convertXDPtoPDF` -Methode und Übergabe einer `com.adobe.idp.Document` -Objekt, das die XDP-Datei darstellt. Die Methode gibt eine `com.adobe.idp.Document` -Objekt, das die neu erstellte PDF-Datei darstellt.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von XDP-Dokumenten in PDF-Dokumente mithilfe der Webdienst-API {#converting-xdp-documents-into-pdf-documents-using-the-web-service-api}

Konvertieren Sie XDP-Dokumente mithilfe der PDF Utilities-API (Webdienst-API) in PDF-Dokumente:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie eine `PDFUtilityServiceService` -Objekt mithilfe des Proxy-Klassenkonstruktors.

1. Aufrufen des Konvertierungsvorgangs &quot;XDP auf PDF&quot;

   Rufen Sie zum Ausführen der Konvertierung die `PDFUtilityServiceService` -Objekt `convertXDPtoPDF` -Methode und Übergabe einer `BLOB` -Objekt, das die XDP-Datei darstellt. Die Methode gibt eine `BLOB` -Objekt, das die neu erstellte PDF-Datei darstellt.

**Siehe auch**

[Konvertieren von XDP-Dokumenten in PDF-Dokumente](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Abrufen von PDF Document Properties {#retrieving-pdf-document-properties}

Sie können die Java- und Webdienst-APIs von PDF Utilities verwenden, um Eigenschaften von PDF-Dokumenten programmgesteuert abzurufen, z. B. ob es sich bei dem Dokument um ein ausfüllbares Formular oder um die zum Lesen des Dokuments erforderliche Acrobat-Mindestversion handelt.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um PDF-Dokumenteigenschaften abzurufen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Vorgang zum Abrufen der Eigenschaften auf.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert ausführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem eine `PDFUtilityServiceClient` -Objekt. Mit der Webdienst-API wird dies mithilfe einer `PDFUtilityServiceService` -Objekt.

**Abrufen der Eigenschaften**

Nachdem Sie den Service-Client erstellt haben, können Sie den Vorgang zum Abrufen der Eigenschaften aufrufen.

**Siehe auch**

[Abrufen von PDF-Dokumenteigenschaften mithilfe der Java-API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-java-api)

[Abrufen von PDF-Dokumenteigenschaften mithilfe der Webdienst-API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von PDF-Dokumenteigenschaften mithilfe der Java-API {#retrieve-pdf-document-properties-using-the-java-api}

Abrufen von PDF-Dokumenteigenschaften mithilfe der PDF Utilities-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-pdfutility-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie eine `PDFUtilityServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Abrufen der Eigenschaften

   Rufen Sie zum Ausführen der Konvertierung die `PDFUtilityServiceClient` -Objekt `getPDFProperties` -Methode verwenden und Folgendes übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das PDF-Dokument darstellt.
   * A `PDFPropertiesOptionSpec` -Objekt, das die Eigenschaften enthält, die ausgewertet werden sollen.

   Die Methode gibt eine `PDFPropertiesResult` -Objekt, das die Ergebnisse der Abfrage enthält.

**Siehe auch**

[Abrufen von PDF Document Properties](pdf-utilities.md#retrieving-pdf-document-properties)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von PDF-Dokumenteigenschaften mithilfe der Webdienst-API {#retrieve-pdf-document-properties-using-the-web-service-api}

Abrufen von PDF-Dokumenteigenschaften mithilfe der PDF Utilities-Webdienst-API:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie eine `PDFUtilityServiceService` -Objekt mithilfe des Proxy-Klassenkonstruktors.

1. Abrufen der Eigenschaften

   Rufen Sie zum Ausführen der Konvertierung die `PDFUtilityServiceService` -Objekt `getPDFProperties` -Methode verwenden und Folgendes übergeben:

   * A `BLOB` -Objekt, das das PDF-Dokument darstellt.
   * A `PDFPropertiesOptionSpec` -Objekt, das die Eigenschaften enthält, die ausgewertet werden sollen.

   Die Methode gibt eine `PDFPropertiesResult` -Objekt, das die Ergebnisse der Abfrage enthält.

**Siehe auch**

[Abrufen von PDF Document Properties](pdf-utilities.md#retrieving-pdf-document-properties)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Festlegen von PDF Document Save Modi {#setting-pdf-document-save-modes}

Sie können die Java- und Webdienst-APIs des PDF Utilities-Dienstes verwenden, um programmgesteuert einen Speichermodus für ein PDF-Dokument festzulegen. Wenn Sie mit dem PDF Utilities-Dienst einen Speichermodus festlegen, legt der PDF Utilities-Dienst nur den Speichermodus fest und speichert das PDF-Dokument nicht. Das PDF-Dokument wird gespeichert, wenn es an einen anderen Dienstvorgang übergeben wird. Beispielsweise können Sie den PDF Utilities-Dienst verwenden, um einen bestimmten Speichermodus festzulegen und ihn an den Encryption-Dienst zu übergeben, in dem das PDF-Dokument gespeichert und verschlüsselt wird.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So legen Sie die Speicheroption für PDF-Dokumente fest:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Legen Sie den Speichermodus fest.
1. Rufen Sie den Speichervorgang auf.
1. Übergeben Sie das PDF-Dokument an einen anderen Vorgang.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie einen PDF Utilities-Vorgang programmgesteuert ausführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem eine `PDFUtilityServiceClient` -Objekt. Mit der Webdienst-API wird dies mithilfe einer `PDFUtilityServiceService` -Objekt.

**Speichern-Modus festlegen**

Sie können eine der folgenden Speicheroptionen auswählen:

* `INCREMENTAL`: So sparen Sie schrittweise, um die zum Speichern erforderliche Zeit zu verkürzen
* `FAST_WEB_VIEW`: Speichern für schnelle Webanzeige
* `FULL`: So speichern Sie mit einem vollständigen Speichern (ohne Optimierungen)

**Aufrufen des Vorgangs &quot;save style&quot;**

Nachdem Sie den Service-Client erstellt haben, können Sie den Vorgang zum Abrufen der Eigenschaften aufrufen.

**Übergeben des PDF-Dokuments an einen anderen AEM Forms-Vorgang**

Sobald der PDF Utilities-Dienst den angegebenen Speichermodus festgelegt hat, übergeben Sie das PDF-Dokument an einen anderen AEM Forms-Vorgang. Nach der Rückgabe dieses Vorgangs wird das PDF-Dokument im angegebenen Modus gespeichert. Wenn Sie beispielsweise den PDF Utilities-Dienst verwenden, um die `FAST_WEB_VIEW` -Modus und übergeben Sie dann das PDF-Dokument an den Dienst für die Verschlüsselung `encryptUsingPassword` -Vorgang, wird das zurückgegebene PDF-Dokument mit einem Kennwort verschlüsselt und im `FAST_WEB_VIEW` -Modus.

>[!NOTE]
>
>Der Schnellstart, der diesem Abschnitt zugeordnet ist, legt die `FAST_WEB_VIEW` und übergibt dann das PDF-Dokument an den Dienst für die Verschlüsselung `encryptUsingPassword` Vorgang.

**Siehe auch**

[Festlegen von PDF-Dokumentspeicheroptionen mithilfe der Java-API](pdf-utilities.md#set-pdf-document-save-options-using-the-java-api)

[Festlegen von PDF-Dokumentspeicheroptionen mithilfe der Webdienst-API](pdf-utilities.md#set-pdf-document-save-options-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Festlegen von PDF-Dokumentspeicheroptionen mithilfe der Java-API {#set-pdf-document-save-options-using-the-java-api}

Legen Sie die PDF-Dokumentspeicheroptionen mithilfe der PDF Utilities-API (Java) fest:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-pdfutility-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie eine `PDFUtilityServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Speichern-Modus festlegen

   * Erstellen Sie ein Objekt `PDFUtilitySaveMode`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Speichermodus fest, indem Sie die `PDFUtilitySaveMode` -Objekt `setSaveStyle` -Methode verwenden und einen string -Wert übergeben, der den Speichermodus angibt. Um beispielsweise für eine schnelle Webanzeige zu speichern, übergeben Sie `FAST_WEB_VIEW`.

1. Aufrufen des Vorgangs &quot;save style&quot;

   Rufen Sie die `PDFUtilityServiceClient` -Objekt `setSaveMode` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das PDF-Dokument darstellt.
   * A `PDFUtilitySaveMode` -Objekt, das den zu verwendenden Speicherstil enthält.
   * Ein boolescher Wert, der bestimmt, ob vorherige Einstellungen überschrieben werden sollen.

   Die Methode gibt eine `com.adobe.idp.Document` -Objekt, das mit dem angegebenen Speicherstil formatiert wurde.

1. Übergeben des PDF-Dokuments an einen anderen AEM Forms-Vorgang

   * Übergeben Sie die zurückgegebene `com.adobe.idp.Document` -Objekt zu einem anderen AEM Forms-Vorgang hinzu.

**Siehe auch**

[Festlegen von PDF Document Save Modi](pdf-utilities.md#setting-pdf-document-save-modes)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Festlegen von PDF-Dokumentspeicheroptionen mithilfe der Webdienst-API {#set-pdf-document-save-options-using-the-web-service-api}

Legen Sie die PDF-Dokumentspeicheroptionen mithilfe der PDF Utilities-API (Webdienst) fest:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des PDF Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie eine `PDFUtilityServiceService` -Objekt mithilfe des Proxy-Klassenkonstruktors.

1. Speichern-Modus festlegen

   * Erstellen Sie ein Objekt `PDFUtilitySaveMode`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Speichermodus fest, indem Sie dem `PDFUtilitySaveMode` -Objekt `saveStyle` -Methode, die den Speichermodus angibt. Um beispielsweise eine schnelle Webanzeige zu speichern, geben Sie `FAST_WEB_VIEW`.

1. Aufrufen des Vorgangs &quot;save style&quot;

   Rufen Sie die `PDFUtilityServiceService` -Objekt `setSaveMode` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das PDF-Dokument darstellt.
   * A `PDFUtilitySaveMode` -Objekt, das den zu verwendenden Speicherstil enthält.
   * Ein boolescher Wert, der bestimmt, ob vorherige Einstellungen überschrieben werden sollen.

   Die Methode gibt eine `BLOB` -Objekt, das mit dem angegebenen Speicherstil formatiert wurde. Sie können dieses Objekt dann als PDF-Dokument speichern.

1. Übergeben des PDF-Dokuments an einen anderen Forms-Vorgang

   * Übergeben Sie die zurückgegebene `BLOB` -Objekt zu einem anderen AEM Forms-Vorgang hinzu.

**Siehe auch**

[Festlegen von PDF Document Save Modi](pdf-utilities.md#setting-pdf-document-save-modes)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Bereinigen von PDF-Dokumenten {#sanitizing-pdf-documents}

Sie können die Java-APIs von PDF Utilities verwenden, um PDF-Dokumente programmgesteuert in XDP-Dokumente zu konvertieren.

>[!NOTE]
>
>Weitere Informationen zum PDF Utilities-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Führen Sie die folgenden Schritte aus, um das PDF-Dokument zu bereinigen:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDFUtilityService-Client.
1. Rufen Sie den Bereinigungsvorgang auf.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Schließen Sie die erforderlichen JAR-Dateien ein, um eine Client-Anwendung mit Java zu erstellen.

**Erstellen eines PDFUtilityService-Clients**

Bevor Sie programmgesteuert einen Bereinigungsvorgang durchführen können, müssen Sie einen PDFUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem eine `PDFUtilityServiceClient` -Objekt.

**Aufrufen des Konvertierungsvorgangs PDF in XDP**

Nachdem Sie den Service-Client erstellt haben, können Sie den Bereinigungsvorgang aufrufen.

**Siehe auch**

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Java-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[Konvertieren von PDF-Dokumenten in XDP-Dokumente mithilfe der Webdienst-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bereinigen von PDF-Dokumenten mit der Java-API {#sanitize-pdf-documents-using-the-java-api}

Bereinigen von Dokumenten mithilfe der PDF Utilities-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-pdfutility-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines PDFUtilityService-Clients

   Erstellen Sie eine `PDFUtilityServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Aufrufen des Konvertierungsvorgangs PDF in XDP

   Rufen Sie zum Ausführen der Konvertierung die `PDFUtilityServiceClient` -Objekt `convertPDFtoXDP` -Methode und Übergabe einer `com.adobe.idp.Document` -Objekt, das die PDF-Datei darstellt. Die Methode gibt eine `com.adobe.idp.Document` -Objekt, das die neu erstellte XDP-Datei darstellt.

**Siehe auch**

[Bereinigen von PDF-Dokumenten](/help/forms/developing/pdf-utilities-service-java-api.md#quick-start-soap-mode-sanitizing-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
