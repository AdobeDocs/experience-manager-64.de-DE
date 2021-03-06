---
title: Konvertieren zwischen Dateiformaten und PDF
seo-title: Converting Between File Formatsand PDF
description: Verwenden Sie den Generate PDF-Dienst, um native Dateiformate in PDF zu konvertieren. Generate PDF-Dienst konvertiert auch PDF in andere Dateiformate und optimiert die Größe von PDF-Dokumenten.
seo-description: Use the Generate PDF service to convert native file formats to PDF. Generate PDF service also converts PDF to other file formats and optimizes the size of PDF documents.
uuid: f72ad603-c996-4d48-9bfc-bed7bf776af6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 180cac3f-6378-42bc-9a47-60f9f08a7103
role: Developer
exl-id: 79091a75-2669-453f-9560-e58bfffa3487
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '7872'
ht-degree: 4%

---

# Konvertieren zwischen Dateiformaten und PDF {#converting-between-file-formatsand-pdf}

**Über den Generate PDF-Dienst**

Der Generate PDF-Dienst kann zahlreiche native Dateiformate in PDF konvertieren. Er kann außerdem PDF-Dokumente in andere Dateiformate konvertieren und die Größe von PDF-Dokumenten optimieren.

Der Generate PDF-Dienst verwendet native Anwendungen, um die folgenden Dateiformate in PDF zu konvertieren. Sofern nicht anders aufgeführt, werden nur die deutschen, französischen, englischen und japanischen Versionen dieser Anwendungen unterstützt. *Nur Windows* zeigt nur Unterstützung für Windows Server® 2003 und Windows Server 2008 an.

* Microsoft Office 2003 und 2007 zum Konvertieren von DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX, XPS und PUB (nur Windows)

   >[!NOTE]
   >
   >Acrobat® 9.2 oder höher ist erforderlich, um das Microsoft XPS-Format in PDF zu konvertieren.

* Autodesk AutoCAD 2005, 2006, 2007, 2008 und 2009 zum Konvertieren von DWF, DWG und DXW (nur auf Englisch)
* Corel WordPerfect 12 und X4 zum Konvertieren von WPD, QPW, SHW (nur auf Englisch)
* OpenOffice 2.0, 2.4, 3.0.1 und 3.1 zum Konvertieren von ODT, ODS, ODP, ODG, ODF, SXW, SXI, SXC, SXD, DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX und PUB

   >[!NOTE]
   >
   >Der Generate PDF-Dienst unterstützt keine 64-Bit-Versionen von OpenOffice.

* Adobe Photoshop® CS2 zum Konvertieren von PSD (nur Windows)

   >[!NOTE]
   >
   >Photoshop CS3 und CS4 werden nicht unterstützt, da sie Windows Server 2003 oder Windows Server 2008 nicht unterstützen.

* Adobe FrameMaker® 7.2 und 8 zum Konvertieren von FM (nur Windows)
* Adobe PageMaker® 7.0 zum Konvertieren von PMD, PM6, P65 und PM (nur Windows)
* Native Formate, die von Drittanbieteranwendungen unterstützt werden (erfordert Entwicklung von Setup-Dateien speziell für die Anwendung) (nur Windows)

Der Generate PDF-Dienst kann folgende standardbasierte Dateiformate in PDF konvertieren.

* Videoformate: SWF, FLV (nur Windows)
* Bildformate: JPEG, JPG, JP2, J2Kí, JPC, J2C, GIF, BMP, TIFF, TIF, PNG, JPF
* HTML (Windows, Sun™ Solaris™ und Linux®)

Der Generate PDF-Dienst kann PDF-Dateien in die folgenden Dateiformate konvertieren (nur Windows):

* Encapsulated PostScript (EPS)
* HTML3.2
* HTML 4.01 mit CSS 1.0
* DOC (Microsoft Word-Format)
* RTF
* Text (sowohl barrierefrei als auch unverschlüsselt)
* XML
* PDF/A-1a, die nur den DeviceRGB-Farbraum verwendet
* PDF/A-1b, der nur den DeviceRGB-Farbraum verwendet

Der Generate PDF-Dienst erfordert die Ausführung der folgenden Verwaltungsaufgaben:

* Installieren der erforderlichen nativen Anwendungen auf dem Computer, der als Host für AEM Forms dient
* Installieren Sie Adobe Acrobat Professional oder Acrobat Pro Extended 9.2 auf dem Computer, der als Host für AEM Forms dient
* Ausführen von Einrichtungsaufgaben nach der Installation

Diese Aufgaben werden unter Installieren und Bereitstellen von AEM Forms mithilfe von JBoss Turnkey beschrieben.

Mithilfe des Generate PDF-Dienstes können Sie diese Aufgaben ausführen:

* Konvertieren Sie von nativen Dateiformaten in PDF.
* Konvertieren Sie HTML-Dokumente in PDF-Dokumente.
* Konvertieren Sie PDF-Dokumente in Dateiformate.

>[!NOTE]
>
>Weitere Informationen zum Generate PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von Word-Dokumenten in PDF-Dokumente {#converting-word-documents-to-pdf-documents}

In diesem Abschnitt wird beschrieben, wie Sie mit der PDF-API generieren ein Microsoft Word-Dokument programmgesteuert in ein PDF-Dokument konvertieren können.

>[!NOTE]
>
>Weitere Informationen zu weiteren Dateiformaten finden Sie unter [Hinzufügen der Unterstützung für weitere native Dateiformate](converting-file-formats-pdf.md#adding-support-for-additional-native-file-formats).

>[!NOTE]
>
>Weitere Informationen zum Generate PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um ein Microsoft Word-Dokument in ein PDF-Dokument zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF-Client generieren .
1. Rufen Sie die zu konvertierende Datei in ein PDF-Dokument ab.
1. Konvertieren Sie die Datei in ein PDF-Dokument.
1. Rufen Sie die Ergebnisse ab.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Generate PDF Client**

Bevor Sie programmgesteuert einen PDF generieren -Vorgang durchführen können, erstellen Sie einen PDF-Dienstclient &quot;Generate&quot;. Wenn Sie die Java-API verwenden, erstellen Sie eine `GeneratePdfServiceClient` -Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie eine `GeneratePDFServiceService` -Objekt.

**Rufen Sie die zu konvertierende Datei in ein PDF-Dokument ab.**

Rufen Sie das Microsoft Word-Dokument ab, das in ein PDF-Dokument konvertiert werden soll.

**Datei in ein PDF-Dokument konvertieren**

Nachdem Sie den Client des Generate PDF-Dienstes erstellt haben, können Sie den `createPDF2` -Methode. Diese Methode benötigt Informationen über das zu konvertierende Dokument, einschließlich der Dateierweiterung.

**Ergebnisse abrufen**

Nachdem die Datei in ein PDF-Dokument konvertiert wurde, können Sie die Ergebnisse abrufen. Nachdem Sie beispielsweise eine Word-Datei in ein PDF-Dokument konvertiert haben, können Sie das PDF-Dokument abrufen und speichern.

**Siehe auch**

[Konvertieren von Word-Dokumenten in PDF-Dokumente mithilfe der Java-API](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-java-api)

[Konvertieren von Word-Dokumenten in PDF-Dokumente mithilfe der Webdienst-API](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zum Generieren der PDF Service-API](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Konvertieren von Word-Dokumenten in PDF-Dokumente mithilfe der Java-API {#convert-word-documents-to-pdf-documents-using-the-java-api}

Konvertieren Sie ein Microsoft Word-Dokument mithilfe der Generate PDF API (Java) in ein PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-generatepdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF-Client generieren .

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `GeneratePdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie die zu konvertierende Datei in ein PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das die mit seinem Konstruktor zu konvertierende Word-Datei darstellt. Übergeben Sie einen string -Wert, der den Speicherort der Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Konvertieren Sie die Datei in ein PDF-Dokument.

   Konvertieren Sie die Datei in ein PDF-Dokument, indem Sie die `GeneratePdfServiceClient` -Objekt `createPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das die zu konvertierende Datei darstellt.
   * A `java.lang.String` -Objekt, das die Dateierweiterung enthält.
   * A `java.lang.String` -Objekt, das die Dateitypeinstellungen enthält, die bei der Konvertierung verwendet werden sollen. Dateitypeinstellungen bieten Konvertierungseinstellungen für verschiedene Dateitypen, z. B. .doc oder .xls.
   * A `java.lang.String` -Objekt, das den Namen der zu verwendenden PDF-Einstellungen enthält. Sie können beispielsweise `Standard`.
   * A `java.lang.String` -Objekt, das den Namen der zu verwendenden Sicherheitseinstellungen enthält.
   * Ein optionales `com.adobe.idp.Document` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen.
   * Ein optionales `com.adobe.idp.Document` -Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen.

   Die `createPDF2` -Methode gibt eine `CreatePDFResult` -Objekt, das das neue PDF-Dokument und eine Protokollinformationen enthält. Die Protokolldatei enthält in der Regel Fehler- oder Warnmeldungen, die von der Konvertierungsanforderung generiert wurden.

1. Rufen Sie die Ergebnisse ab.

   Führen Sie die folgenden Schritte aus, um das PDF-Dokument abzurufen:

   * Rufen Sie die `CreatePDFResult` -Objekt `getCreatedDocument` -Methode, die eine `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument aus dem im vorherigen Schritt erstellten Objekt zu extrahieren.

   Wenn Sie die `createPDF2` -Methode zum Abrufen des Protokolldokuments (nicht anwendbar auf HTML-Konvertierungen), führen Sie die folgenden Schritte aus:

   * Rufen Sie die `CreatePDFResult` -Objekt `getLogDocument` -Methode. Dadurch wird eine `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das Protokolldokument zu extrahieren.


**Siehe auch**

[Zusammenfassung der Schritte](converting-file-formats-pdf.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Konvertieren eines Microsoft Word-Dokuments in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-a-microsoft-word-document-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von Word-Dokumenten in PDF-Dokumente mithilfe der Webdienst-API {#convert-word-documents-to-pdf-documents-using-the-web-service-api}

Konvertieren Sie ein Microsoft Word-Dokument mithilfe der Generate PDF API (Webdienst) in ein PDF-Dokument:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF-Client generieren .

   * Erstellen Sie eine `GeneratePDFServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `GeneratePDFServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Geben Sie jedoch `?blob=mtom`.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `GeneratePDFServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie die zu konvertierende Datei in ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird verwendet, um die Datei zu speichern, die Sie in ein PDF-Dokument konvertieren möchten.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort der zu konvertierenden Datei und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisung zu `MTOM` -Eigenschaft den Inhalt des Byte-Arrays.

1. Konvertieren Sie die Datei in ein PDF-Dokument.

   Konvertieren Sie die Datei in ein PDF-Dokument, indem Sie die `GeneratePDFServiceService` -Objekt `CreatePDF2` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das die zu konvertierende Datei darstellt.
   * Eine Zeichenfolge, die die Dateierweiterung enthält.
   * A `java.lang.String` -Objekt, das die Dateitypeinstellungen enthält, die bei der Konvertierung verwendet werden sollen. Dateitypeinstellungen bieten Konvertierungseinstellungen für verschiedene Dateitypen, z. B. .doc oder .xls.
   * Ein string -Objekt, das die zu verwendenden PDF-Einstellungen enthält. Sie können Folgendes angeben `Standard`.
   * Ein string -Objekt, das die zu verwendenden Sicherheitseinstellungen enthält. Sie können Folgendes angeben `No Security`.
   * Ein optionales `BLOB` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen.
   * Ein optionales `BLOB` -Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen.
   * Ein Ausgabeparameter vom Typ `BLOB` , der durch die `CreatePDF2` -Methode. Die `CreatePDF2` -Methode füllt dieses Objekt mit dem konvertierten Dokument. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ein Ausgabeparameter vom Typ `BLOB` , der durch die `CreatePDF2` -Methode. Die `CreatePDF2` -Methode füllt dieses Objekt mit dem Protokolldokument. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

1. Rufen Sie die Ergebnisse ab.

   * Rufen Sie das konvertierte PDF-Dokument ab, indem Sie die `BLOB` -Objekt `MTOM` in ein Byte-Array. Das Byte-Array stellt das konvertierte PDF-Dokument dar. Stellen Sie sicher, dass Sie die `BLOB` -Objekt, das als Ausgabeparameter für die `createPDF2` -Methode.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des konvertierten PDF-Dokuments darstellt.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-file-formats-pdf.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Konvertieren von HTML-Dokumenten in PDF-Dokumente {#converting-html-documents-to-pdf-documents}

In diesem Abschnitt wird beschrieben, wie Sie mit der PDF-API generieren HTML-Dokumente programmgesteuert in PDF-Dokumente konvertieren können.

>[!NOTE]
>
>Weitere Informationen zum Generate PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Führen Sie die folgenden Schritte aus, um ein HTML-Dokument in ein PDF-Dokument zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF-Client generieren .
1. Rufen Sie den HTML-Inhalt ab, der in ein PDF-Dokument konvertiert werden soll.
1. Konvertieren Sie den HTML-Inhalt in ein PDF-Dokument.
1. Rufen Sie die Ergebnisse ab.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Generate PDF Client**

Bevor Sie programmgesteuert einen PDF generieren -Vorgang durchführen können, müssen Sie einen PDF-Dienstclient für Generate erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `GeneratePdfServiceClient` -Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie eine `GeneratePDFServiceService`.

**Abrufen des HTML-Inhalts zum Konvertieren in ein PDF-Dokument**

Verweisen Sie auf HTML-Inhalte, die Sie in ein PDF-Dokument konvertieren möchten. Sie können auf HTML-Inhalte wie eine HTML- oder HTML-Datei verweisen, auf die über eine URL zugegriffen werden kann.

**Konvertieren des HTML-Inhalts in ein PDF-Dokument**

Nachdem Sie den Dienst-Client erstellt haben, können Sie den entsprechenden PDF-Erstellungsvorgang aufrufen. Dieser Vorgang benötigt Informationen zum zu konvertierenden Dokument, einschließlich des Pfads zum Zieldokument.

**Ergebnisse abrufen**

Nachdem der HTML-Inhalt in ein PDF-Dokument konvertiert wurde, können Sie die Ergebnisse abrufen und das PDF-Dokument speichern.

**Siehe auch**

[Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-java-api)

[Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Webdienst-API](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zum Generieren der PDF Service-API](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API {#convert-html-content-to-a-pdf-document-using-the-java-api}

Konvertieren Sie ein HTML-Dokument mithilfe der Generate PDF API (Java) in ein PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-generatepdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF-Client generieren .

   Erstellen Sie eine `GeneratePdfServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Rufen Sie den HTML-Inhalt ab, der in ein PDF-Dokument konvertiert werden soll.

   Rufen Sie HTML-Inhalte ab, indem Sie eine Zeichenfolgenvariable erstellen und eine URL zuweisen, die auf HTML-Inhalte verweist.

1. Konvertieren Sie den HTML-Inhalt in ein PDF-Dokument.

   Rufen Sie die `GeneratePdfServiceClient` -Objekt `htmlToPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * A `java.lang.String` -Objekt, das die URL der zu konvertierenden HTML-Datei enthält.
   * A `java.lang.String` -Objekt, das die Dateitypeinstellungen enthält, die bei der Konvertierung verwendet werden sollen. Dateitypeinstellungen können Spider-Level enthalten.
   * A `java.lang.String` -Objekt, das den Namen der zu verwendenden Sicherheitseinstellungen enthält.
   * Ein optionales `com.adobe.idp.Document` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen. Wenn diese Informationen nicht angegeben werden, werden die Einstellungen automatisch anhand der drei vorangehenden Parameter ausgewählt.
   * Ein optionales `com.adobe.idp.Document` -Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen.

1. Rufen Sie die Ergebnisse ab.

   Die `htmlToPDF2` -Methode gibt eine `HtmlToPdfResult` -Objekt, das das neue generierte PDF-Dokument enthält. Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Rufen Sie die `HtmlToPdfResult` -Objekt `getCreatedDocument` -Methode. Dadurch wird eine `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument aus dem im vorherigen Schritt erstellten Objekt zu extrahieren.

**Siehe auch**

[Konvertieren von HTML-Dokumenten in PDF-Dokumente](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[Schnellstart (SOAP-Modus): Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Webdienst-API {#convert-html-content-to-a-pdf-document-using-the-web-service-api}

Konvertieren Sie HTML-Inhalte mithilfe der Generate PDF API (Webdienst) in ein PDF-Dokument:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF-Client generieren .

   * Erstellen Sie eine `GeneratePDFServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `GeneratePDFServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Geben Sie jedoch `?blob=mtom`.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `GeneratePDFServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie den HTML-Inhalt ab, der in ein PDF-Dokument konvertiert werden soll.

   Rufen Sie HTML-Inhalte ab, indem Sie eine Zeichenfolgenvariable erstellen und eine URL zuweisen, die auf HTML-Inhalte verweist.

1. Konvertieren Sie den HTML-Inhalt in ein PDF-Dokument.

   Konvertieren Sie den HTML-Inhalt in ein PDF-Dokument, indem Sie die `GeneratePDFServiceService` -Objekt `HtmlToPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * Eine Zeichenfolge, die den zu konvertierenden HTML-Inhalt enthält.
   * A `java.lang.String` -Objekt, das die Dateitypeinstellungen enthält, die bei der Konvertierung verwendet werden sollen.
   * Ein string -Objekt, das die zu verwendenden Sicherheitseinstellungen enthält.
   * Ein optionales `BLOB` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen.
   * Ein optionales `BLOB` -Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen.
   * Ein Ausgabeparameter vom Typ `BLOB` , der durch die `CreatePDF2` -Methode. Die `CreatePDF2` -Methode füllt dieses Objekt mit dem konvertierten Dokument. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

1. Rufen Sie die Ergebnisse ab.

   * Rufen Sie das konvertierte PDF-Dokument ab, indem Sie die `BLOB` -Objekt `MTOM` in ein Byte-Array. Das Byte-Array stellt das konvertierte PDF-Dokument dar. Stellen Sie sicher, dass Sie die `BLOB` -Objekt, das als Ausgabeparameter für die `HtmlToPDF2` -Methode.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des konvertierten PDF-Dokuments darstellt.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Konvertieren von HTML-Dokumenten in PDF-Dokumente](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Konvertieren von PDF-Dokumenten in Nicht-Bildformate {#converting-pdf-documents-to-non-image-formats}

In diesem Abschnitt wird beschrieben, wie Sie mit der PDF Java-API und der Web-Service-API ein PDF-Dokument programmgesteuert in eine RTF-Datei konvertieren können. Dies ist ein Beispiel für ein Nicht-Bildformat. Andere Nicht-Bildformate sind HTML, Text, DOC und EPS. Stellen Sie beim Konvertieren eines PDF-Dokuments in RTF sicher, dass das PDF-Dokument keine Formularelemente wie eine Senden-Schaltfläche enthält. Formularelemente werden nicht konvertiert.

>[!NOTE]
>
>Weitere Informationen zum Generate PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Führen Sie die folgenden Schritte aus, um ein PDF-Dokument in einen der unterstützten Typen zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF-Client generieren .
1. Rufen Sie das zu konvertierende PDF-Dokument ab.
1. Konvertieren Sie das PDF-Dokument.
1. Speichern Sie die konvertierte Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Generate PDF Client**

Bevor Sie programmgesteuert einen PDF generieren -Vorgang durchführen können, müssen Sie einen PDF-Dienstclient für Generate erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `GeneratePdfServiceClient` -Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie eine `GeneratePDFServiceService` -Objekt.

**Abrufen des zu konvertierenden PDF-Dokuments**

Rufen Sie das PDF-Dokument ab, das in ein Nicht-Bildformat konvertiert werden soll.

**PDF-Dokument konvertieren**

Nachdem Sie den Dienstclient erstellt haben, können Sie den PDF-Exportvorgang aufrufen. Dieser Vorgang benötigt Informationen zum zu konvertierenden Dokument, einschließlich des Pfads zum Zieldokument.

**Speichern Sie die konvertierte Datei**

Speichern Sie die konvertierte Datei. Wenn Sie beispielsweise ein PDF-Dokument in eine RTF-Datei konvertieren, speichern Sie das konvertierte Dokument in eine RTF-Datei.

**Siehe auch**

[Konvertieren eines PDF-Dokuments in eine RTF-Datei mithilfe der Java-API](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-java-api)

[Konvertieren eines PDF-Dokuments in eine RTF-Datei mithilfe der Web-Dienst-API](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zum Generieren der PDF Service-API](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in eine RTF-Datei mithilfe der Java-API {#convert-a-pdf-document-to-a-rtf-file-using-the-java-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Generate PDF API (Java) in eine RTF-Datei:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-generatepdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF-Client generieren .

   Erstellen Sie eine `GeneratePdfServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das PDF-Dokument darstellt, das mithilfe seines Konstruktors konvertiert werden soll. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Konvertieren Sie das PDF-Dokument.

   Rufen Sie die `GeneratePdfServiceClient` -Objekt `exportPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das die zu konvertierende PDF-Datei darstellt.
   * A `java.lang.String` -Objekt, das den Namen der zu konvertierenden Datei enthält.
   * A `java.lang.String` -Objekt, das den Namen der Adobe PDF-Einstellungen enthält.
   * A `ConvertPDFFormatType` -Objekt, das den Zieldateityp für die Konvertierung angibt.
   * Ein optionales `com.adobe.idp.Document` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen.

   Die `exportPDF2` -Methode gibt eine `ExportPDFResult` -Objekt, das die konvertierte Datei enthält.

1. Konvertieren Sie das PDF-Dokument.

   Um die neu erstellte Datei abzurufen, führen Sie die folgenden Schritte aus:

   * Rufen Sie die `ExportPDFResult` -Objekt `getConvertedDocument` -Methode. Dadurch wird eine `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das neue Dokument zu extrahieren.

**Siehe auch**

[Zusammenfassung der Schritte](converting-file-formats-pdf.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren eines PDF-Dokuments in eine RTF-Datei mithilfe der Web-Dienst-API {#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Generate PDF API (Webdienst) in eine RTF-Datei:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Generate PDFf-Client.

   * Erstellen Sie eine `GeneratePDFServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `GeneratePDFServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Geben Sie jedoch `?blob=mtom`.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `GeneratePDFServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines konvertierten PDF-Dokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisung zu `MTOM` -Eigenschaft den Inhalt des Byte-Arrays.

1. Konvertieren Sie das PDF-Dokument.

   Rufen Sie die `GeneratePDFServiceServiceWse` -Objekt `ExportPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das die zu konvertierende PDF-Datei darstellt.
   * Eine Zeichenfolge, die den Pfadnamen der zu konvertierenden Datei enthält.
   * A `java.lang.String` -Objekt, das den Speicherort der Datei angibt.
   * Ein string -Objekt, das den Zieldateityp für die Konvertierung angibt. Geben Sie `RTF`.
   * Ein optionales `BLOB` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen.
   * Ein Ausgabeparameter vom Typ `BLOB` , der durch die `ExportPDF2` -Methode. Die `ExportPDF2` -Methode füllt dieses Objekt mit dem konvertierten Dokument. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

1. Speichern Sie die konvertierte Datei.

   * Rufen Sie das konvertierte RTF-Dokument ab, indem Sie die `BLOB` -Objekt `MTOM` in ein Byte-Array. Das Byte-Array stellt das konvertierte RTF-Dokument dar. Stellen Sie sicher, dass Sie die `BLOB` -Objekt, das als Ausgabeparameter für die `ExportPDF2` -Methode.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Speicherort der RTF-Datei darstellt.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine RTF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-file-formats-pdf.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Hinzufügen der Unterstützung für weitere native Dateiformate {#adding-support-for-additional-native-file-formats}

In diesem Abschnitt wird beschrieben, wie Sie Unterstützung für zusätzliche native Dateiformate hinzufügen. Es bietet einen Überblick über die Interaktionen zwischen dem Generate PDF-Dienst und den nativen Programmen, die dieser Dienst zum Konvertieren nativer Dateiformate in PDF verwendet.

In diesem Abschnitt wird auch Folgendes erläutert:

* Ändern der Antwort, die der Generate PDF-Dienst den nativen Applikationen bereitstellt, die dieses Produkt bereits verwendet, um native Dateiformate in PDF zu konvertieren
* Die Interaktionen zwischen dem Generate PDF-Dienst, der Generate PDF Service Application Monitor (AppMon)-Komponente und nativen Anwendungen wie Microsoft Word
* Die Rollen, die XML-Grammatiken in diesen Interaktionen spielen

### Komponenteninteraktionen {#component-interactions}

Der Generate PDF-Dienst konvertiert native Dateiformate, indem er die mit dem Dateiformat verknüpfte Anwendung aufruft und dann mit der Anwendung interagiert, um das Dokument mithilfe des Standarddruckers zu drucken. Der Standarddrucker muss als Adobe PDF-Drucker eingerichtet sein.

Diese Abbildung zeigt die Komponenten und Treiber, die mit nativer Anwendungsunterstützung verbunden sind. Außerdem werden die XML-Grammatiken erwähnt, die die Interaktionen beeinflussen.

Komponenteninteraktionen für die native Dateikonvertierung

Dieses Dokument verwendet den Begriff *native Anwendung* , um die Anwendung anzugeben, die zum Erstellen eines nativen Dateiformats wie Microsoft Word verwendet wird.

*AppMon* ist eine Unternehmenskomponente, die mit einer nativen Anwendung auf dieselbe Weise interagiert, wie ein Benutzer durch die von dieser Anwendung dargestellten Dialogfelder navigieren würde. Die XML-Grammatiken, die von AppMon verwendet werden, um eine Anwendung wie Microsoft Word anzuweisen, eine Datei zu öffnen und zu drucken, umfassen folgende sequenzielle Aufgaben:

1. Öffnen Sie die Datei, indem Sie Datei > Öffnen auswählen.
1. Sicherstellen, dass das Dialogfeld &quot;Öffnen&quot;angezeigt wird; falls nicht, Umgang mit dem Fehler
1. Geben Sie den Dateinamen im Feld Dateiname ein und klicken Sie dann auf die Schaltfläche Öffnen .
1. Sicherstellen, dass die Datei tatsächlich geöffnet wird
1. Öffnen Sie das Dialogfeld &quot;Drucken&quot;, indem Sie &quot;Datei&quot;> &quot;Drucken&quot;auswählen
1. Sicherstellen, dass das Dialogfeld &quot;Drucken&quot;angezeigt wird

AppMon verwendet standardmäßige Win32-APIs, um mit Drittanbieteranwendungen zu interagieren und Benutzeroberflächenereignisse wie Tastenanschläge und Mausklicks zu übertragen. Dies ist nützlich, um diese Anwendungen zu steuern und PDF-Dateien daraus zu erstellen.

Aufgrund einer Einschränkung mit diesen Win32-APIs kann AppMon diese Benutzeroberflächen-Ereignisse nicht an bestimmte Arten von Fenstern senden, wie z. B. unverankerte Menüleisten (in einigen Anwendungen wie TextPad enthalten) und bestimmte Dialogfelder, deren Inhalt nicht mit den Win32-APIs abgerufen werden kann.

Eine schwebende Menüleiste lässt sich leicht visuell erkennen. Es kann jedoch nicht möglich sein, die speziellen Dialogfeldtypen nur durch visuelle Überprüfung zu identifizieren. Sie benötigen eine Drittanbieteranwendung wie Microsoft Spy+ (Teil der Microsoft Visual C++-Entwicklungsumgebung) oder die entsprechende WinID (die kostenlos heruntergeladen werden kann von [https://www.dennisbabkin.com/php/download.php?what=WinID](https://www.dennisbabkin.com/php/download.php?what=WinID)), um ein Dialogfeld zu untersuchen, um festzustellen, ob AppMon mit Standard-Win32-APIs damit interagieren kann.

Wenn WinID in der Lage ist, Dialogfeldinhalte wie Text, Unterfenster, Fensterklassen-ID usw. zu extrahieren, kann AppMon dies ebenfalls tun.

In dieser Tabelle sind die Informationen aufgeführt, die beim Drucken nativer Dateiformate verwendet werden.

<table> 
 <thead> 
  <tr> 
   <th><p>Informationstyp</p></th> 
   <th><p>Beschreibung</p></th> 
   <th><p>Ändern/Erstellen von Einträgen für native Dateien </p></th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td><p>Administrative Einstellungen </p></td> 
   <td><p>Enthält PDF-Einstellungen, Sicherheitseinstellungen und Dateitypeinstellungen. </p><p>Dateitypeinstellungen verknüpfen Dateinamenerweiterungen mit den entsprechenden nativen Programmen. Dateitypeinstellungen geben auch native Anwendungseinstellungen an, die zum Drucken nativer Dateien verwendet werden. </p></td> 
   <td><p>Um die Einstellungen für eine bereits unterstützte native Anwendung zu ändern, legt der Systemadministrator die Dateitypeinstellungen in der Administration Console fest. </p><p>Um Unterstützung für ein neues natives Dateiformat hinzuzufügen, müssen Sie die Datei manuell bearbeiten. (Siehe <a href="converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format">Unterstützung für ein natives Dateiformat hinzufügen oder ändern</a>. </p></td> 
  </tr> 
  <tr> 
   <td><p>Script </p></td> 
   <td><p>Gibt Interaktionen zwischen dem Generate PDF-Dienst und einer nativen Anwendung an. Diese Interaktionen leiten das Programm normalerweise zum Drucken einer Datei an den Adobe PDF-Treiber weiter. </p><p>Das Skript enthält Anweisungen, die die native Anwendung anweisen, bestimmte Dialogfelder zu öffnen, und die bestimmte Antworten auf Felder und Schaltflächen in diesen Dialogfeldern bereitstellen. </p></td> 
   <td><p>Der Generate PDF-Dienst enthält Skriptdateien für alle unterstützten nativen Programme. Sie können diese Dateien mithilfe einer XML-Bearbeitungsanwendung ändern.</p><p>Um Unterstützung für eine neue native Anwendung hinzuzufügen, müssen Sie eine neue Skriptdatei erstellen. (Siehe <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für eine native Anwendung</a>. </p></td> 
  </tr> 
  <tr> 
   <td><p>Allgemeine Dialogfeldanweisungen </p></td> 
   <td><p>Gibt an, wie auf Dialogfelder reagiert werden soll, die für mehrere Anwendungen verwendet werden. Solche Dialogfelder werden von Betriebssystemen, Hilfsprogrammen (wie PDFMaker) und Treibern generiert. </p><p>Die Datei, die diese Informationen enthält, lautet "appmon.global.en_US.xml".</p></td> 
   <td><p>Ändern Sie diese Datei nicht. </p></td> 
  </tr> 
  <tr> 
   <td><p>Anwendungsspezifische Dialogfeldanweisungen</p></td> 
   <td><p>Gibt an, wie auf anwendungsspezifische Dialogfelder reagiert werden soll. </p><p>Die Datei, die diese Informationen enthält, ist appmon.<i>[appname]</i>.dialog.<i>[locale]</i>.xml (z. B. appmon.word.en_US.xml).</p></td> 
   <td><p>Ändern Sie diese Datei nicht. </p><p>Informationen zum Hinzufügen von Dialogfeldanweisungen für eine neue native Anwendung finden Sie unter <a href="converting-file-formats-pdf.md#creating_or_modifying_an_additional_dialog_xml_file_for_a_native_application">Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für eine native Anwendung</a>.</p></td> 
  </tr> 
  <tr> 
   <td><p>Zusätzliche anwendungsspezifische Dialogfeldanweisungen </p></td> 
   <td><p>Gibt Überschreibungen und Ergänzungen zu anwendungsspezifischen Dialogfeldanweisungen an. Der Abschnitt enthält ein Beispiel für solche Informationen. </p><p>Die Datei, die diese Informationen enthält, ist appmon.<i>[appname]</i>.additional.<i>[locale]</i>.xml. Ein Beispiel ist appmon.additional.en_US.xml.</p></td> 
   <td><p>Dateien dieses Typs können mit einer XML-Bearbeitungsanwendung erstellt und geändert werden. (Siehe <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für eine native Anwendung</a>. </p><p><strong>Wichtig</strong>: Sie müssen zusätzliche anwendungsspezifische Dialogfeldanweisungen für jede native Anwendung erstellen, die Ihr Server unterstützt. </p></td> 
  </tr> 
 </tbody> 
</table>

### Über XML-Dateien für Skripte und Dialogfelder {#about-the-script-and-dialog-xml-files}

Skript-XML-Dateien leiten den Generate PDF-Dienst an, um durch Anwendungsdialogfelder zu navigieren, so wie ein Benutzer durch die Anwendungsdialogfelder navigieren würde. Skript-XML-Dateien weisen den Generate PDF-Dienst auch an, auf Dialogfelder zu reagieren, indem sie beispielsweise Schaltflächen drücken, Kontrollkästchen aktivieren oder deaktivieren oder Menüelemente auswählen.

Im Gegensatz dazu reagieren XML-Dialogfelddateien einfach auf Dialogfelder mit den gleichen Aktionstypen, die in XML-Skript-Dateien verwendet werden.

#### Terminologie von Dialog- und Fensterelementen {#dialog-box-and-window-element-terminology}

In diesem Abschnitt und im nächsten Abschnitt wird je nach der beschriebenen Perspektive eine andere Terminologie für Dialogfelder und die darin enthaltenen Komponenten verwendet. Dialogfeldkomponenten sind Elemente wie Schaltflächen, Felder und Kombinationsfelder.

Wenn dieser Abschnitt und der nächste Abschnitt Dialogfelder und ihre Komponenten aus der Perspektive eines Benutzers beschreiben, werden Begriffe wie *Dialogfeld*, *button*, *field* und *Kombinationsfeld* verwendet werden.

Wenn dieser Abschnitt und der nächste Abschnitt Dialogfelder und ihre Komponenten aus der Perspektive ihrer internen Darstellung beschreiben, wird der Begriff *Fensterelement* verwendet. Die interne Darstellung von Fensterelementen ist eine Hierarchie, bei der jede Fensterelementinstanz durch Beschriftungen identifiziert wird. Die Fensterelementinstanz beschreibt auch ihre physischen Merkmale und ihr Verhalten.

Aus Sicht eines Benutzers zeigen die Dialogfelder und ihre Komponenten unterschiedliche Verhaltensweisen an, bei denen einige Dialogfeldelemente ausgeblendet werden, bis sie aktiviert werden. Aus der Sicht der internen Repräsentation gibt es kein solches Verhaltensproblem. Beispielsweise ähnelt die interne Darstellung eines Dialogfelds der der darin enthaltenen Komponenten, mit der Ausnahme, dass die Komponenten im Dialogfeld verschachtelt sind.

In diesem Abschnitt werden XML-Elemente beschrieben, die AppMon Anweisungen geben. Diese Elemente haben Namen wie die `dialog` -Element und `window` -Element. In diesem Dokument wird eine Schriftart mit Konstantschriftart verwendet, um XML-Elemente zu unterscheiden. Die `*dialog*` -Element gibt ein Dialogfeld an, das eine XML-Skriptdatei dazu führen kann, dass sie entweder absichtlich oder unbeabsichtigt angezeigt wird. Die `*window*` -Element ein Fensterelement (Dialogfeld oder die Komponenten eines Dialogfelds).

#### Hierarchie {#hierarchy}

Dieses Diagramm zeigt die Hierarchie des Skripts und der Dialog-XML. Eine XML-Skript-Datei entspricht dem Schema script.xsd , das (im XML-Sinne) das Schema window.xsd enthält. Gleichermaßen entspricht eine XML-Dialogfelddatei dem Schema dialogs.xsd , das auch das Schema window.xsd enthält.

![as_as_xml_hierarchy](assets/as_as_xml_hierarchy.png)

Hierarchie des Skripts und Dialogfeld-XML

#### XML-Skriptdateien {#script-xml-files}

A *Skript-XML-Datei* gibt eine Reihe von Schritten an, die die native Anwendung anweisen, zu bestimmten Fensterelementen zu navigieren und dann Antworten auf diese Elemente bereitzustellen. Die meisten Antworten sind Text oder Tastenanschläge, die der Eingabe entsprechen, die ein Benutzer für ein Feld, Kombinationsfeld oder eine Schaltfläche im entsprechenden Dialogfeld bereitstellt.

Der Generate PDF-Dienst unterstützt Skript-XML-Dateien, indem er eine native Anwendung anweist, eine native zu drucken. Skript-XML-Dateien können jedoch verwendet werden, um alle Aufgaben auszuführen, die ein Benutzer bei der Interaktion mit den Dialogfeldern der nativen Anwendung ausführen kann.

Die Schritte in einer XML-Skript-Datei werden in der richtigen Reihenfolge ausgeführt, ohne dass sich die Möglichkeit einer Verzweigung bietet. Der einzige unterstützte bedingte Test ist die Zeitüberschreitung/Wiederholung, wodurch ein Skript beendet wird, wenn ein Schritt innerhalb eines bestimmten Zeitraums und nach einer bestimmten Anzahl weiterer Versuche nicht erfolgreich abgeschlossen wurde.

Die Anweisungen in einem Schritt sind nicht nur sequenziell, sondern werden auch der Reihe nach ausgeführt. Sie müssen sicherstellen, dass die Schritte und Anweisungen die Reihenfolge widerspiegeln, in der ein Benutzer dieselben Schritte durchführt.

Jeder Schritt in einer XML-Skript-Datei identifiziert das Fensterelement, das angezeigt werden soll, wenn die Anweisungen des Schritts erfolgreich ausgeführt wurden. Wenn beim Ausführen eines Skriptschritts ein unerwartetes Dialogfeld angezeigt wird, durchsucht der Generate PDF-Dienst die XML-Dialogfelddateien, wie im nächsten Abschnitt beschrieben.

#### Dialogfeld-XML-Dateien {#dialog-xml-files}

Beim Ausführen nativer Anwendungen werden verschiedene Dialogfelder angezeigt, die unabhängig davon angezeigt werden, ob sich die nativen Anwendungen im sichtbaren oder unsichtbaren Modus befinden. Die Dialogfelder können vom Betriebssystem oder von der Anwendung selbst erstellt werden. Wenn native PDF-Anwendungen unter der Kontrolle des Generate-Dienstes ausgeführt werden, werden die Dialogfelder &quot;System&quot;und &quot;Native App&quot;in einem unsichtbaren Fenster angezeigt.

A *Dialogfeld-XML-Datei* gibt an, wie der Generate PDF-Dienst auf die Dialogfelder &quot;System&quot;oder &quot;Native App&quot;antwortet. Die XML-Dialogfelddateien ermöglichen es dem Generate PDF-Dienst, auf nicht erforderliche Dialogfelder zu reagieren, um den Konvertierungsprozess zu erleichtern.

Wenn das System oder die native Anwendung ein Dialogfeld anzeigt, das nicht von der derzeit ausgeführten Skript-XML-Datei verarbeitet wird, durchsucht der Generate PDF-Dienst die XML-Dialogfelddateien in dieser Reihenfolge und stoppt sie, wenn eine Übereinstimmung gefunden wird:

* appmon.*[appname]*.additional.*[locale]*.xml
* appmon.*[appname].[locale]*.xml (Ändern Sie diese Datei nicht.)
* appmon.global.*[locale]*.xml (Ändern Sie diese Datei nicht.)

Wenn der Generate PDF-Dienst eine Übereinstimmung für das Dialogfeld findet, wird er durch Senden des Tastenanschlags oder einer anderen für das Dialogfeld angegebenen Aktion beendet. Wenn in den Anweisungen für das Dialogfeld eine Abbruchmeldung angegeben wird, beendet der Generate PDF-Dienst den derzeit ausgeführten Auftrag und erzeugt eine Fehlermeldung. Eine solche Abbruchmeldung würde im `abortMessage` -Element in der XML-Skriptgrammatik.

Wenn der Generate PDF-Dienst auf ein Dialogfeld stößt, das in keiner der oben aufgeführten Dateien beschrieben wird, fügt der Generate PDF-Dienst die Beschriftung des Dialogfelds in den Protokolldateieintrag ein. Der derzeit ausgeführte Auftrag wird schließlich mit einer Zeitüberschreitung beendet. Sie können dann die Informationen in der Protokolldatei verwenden, um neue Anweisungen in der zusätzlichen XML-Dialogfelddatei für die native Anwendung zu erstellen.

### Unterstützung für ein natives Dateiformat hinzufügen oder ändern {#adding-or-modifying-support-for-a-native-file-format}

In diesem Abschnitt werden die Aufgaben beschrieben, die Sie ausführen müssen, um andere native Dateiformate zu unterstützen oder um die Unterstützung für ein bereits unterstütztes natives Dateiformat zu ändern.

Bevor Sie Unterstützung hinzufügen oder ändern können, müssen Sie die folgenden Aufgaben ausführen.

#### Auswahl eines Werkzeugs zum Identifizieren von Fensterelementen {#choosing-a-tool-for-identifying-window-elements}

In den XML-Dateien für Dialogfelder und Skripten müssen Sie das Fensterelement (Dialogfeld, Feld oder andere Dialogfeldkomponente) identifizieren, auf das Ihr Dialogfeld oder Skriptelement reagiert. Wenn beispielsweise ein Skript ein Menü für eine native Anwendung aufruft, muss das Skript das Fensterelement in diesem Menü identifizieren, auf das Tastenanschläge oder eine Aktion angewendet werden sollen.

Sie können ein Dialogfeld einfach anhand der Beschriftung identifizieren, die in der Titelleiste angezeigt wird. Sie müssen jedoch ein Tool wie Microsoft Spy++ verwenden, um Fensterelemente der unteren Ebene zu identifizieren. Die Fensterelemente der unteren Ebene können durch eine Vielzahl von Attributen identifiziert werden, die nicht offensichtlich sind. Darüber hinaus kann jedes native Programm sein Fensterelement anders identifizieren. Daher gibt es mehrere Möglichkeiten, ein Fensterelement zu identifizieren. Im Folgenden finden Sie die empfohlene Reihenfolge für die Berücksichtigung der Identifizierung von Fensterelementen:

1. Beschriftung selbst, wenn sie eindeutig ist
1. Control ID, die für ein bestimmtes Dialogfeld möglicherweise eindeutig ist oder nicht
1. Klassenname, der eindeutig sein kann oder nicht

Jedes dieser drei Attribute kann zur Identifizierung eines Fensters verwendet werden.

Wenn die Attribute eine Beschriftung nicht identifizieren, können Sie stattdessen ein Fensterelement identifizieren, indem Sie dessen Index in Bezug auf dessen übergeordnetes Element verwenden. Ein *index* gibt die Position des Fensterelements relativ zu den gleichrangigen Fensterelementen an. Häufig sind Indizes die einzige Möglichkeit, Kombinationsfelder zu identifizieren.

Beachten Sie diese Probleme:

* Microsoft Spy++ zeigt Untertitel mit einem kaufmännischen Und-Zeichen (&amp;) an, um den Hotkey der Beschriftung zu identifizieren. Beispielsweise zeigt Spy++ die Beschriftung für ein Druckdialogfeld als `Pri&nt`, was anzeigt, dass der Hotkey *n*. Beschriftungstitel in XML-Dateien für Skripte und Dialogfelder dürfen keine kaufmännischen Und-Zeichen enthalten.
* Einige Beschriftungen enthalten Zeilenumbrüche. Der Generate PDF-Dienst kann Zeilenumbrüche nicht identifizieren. Wenn eine Beschriftung einen Zeilenumbruch enthält, fügen Sie genügend Beschriftung hinzu, um sie von den anderen Menüelementen zu unterscheiden, und verwenden Sie dann reguläre Ausdrücke für den ausgelassenen Teil. Ein Beispiel ist ( `^Long caption title$`). (Siehe [Verwenden regulärer Ausdrücke in Beschriftungsattributen](converting-file-formats-pdf.md#using-regular-expressions-in-caption-attributes).
* Verwenden Sie Zeichenentitäten (auch als Escape-Sequenzen bezeichnet) für reservierte XML-Zeichen. Verwenden Sie beispielsweise `&` für Ampersands, `<` und `>` für Symbole kleiner als und größer als `&apos;` bei Apostrophen und `&quot;` für Anführungszeichen.

Wenn Sie mit Dialogfeld- oder Skript-XML-Dateien arbeiten möchten, sollten Sie die Anwendung Microsoft Spy++ installieren.

#### Dekomprimieren der Dialog- und Skriptdateien {#unpackaging-the-dialog-and-script-files}

Die Dialogfelder und Skriptdateien befinden sich in der Datei &quot;appmondata.jar&quot;. Bevor Sie eine dieser Dateien ändern oder neue Skript- oder Dialogfelddateien hinzufügen können, müssen Sie die Verpackung dieser JAR-Datei aufheben. Angenommen, Sie möchten Unterstützung für die Anwendung EditPlus hinzufügen. Sie erstellen zwei XML-Dateien mit den Namen &quot;appmon.editplus.script.en_US.xml&quot;und &quot;appmon.editplus.script.additional.en_US.xml&quot;. Diese XML-Skripte müssen zur Datei adobe-appmondata.jar an zwei Stellen hinzugefügt werden, wie unten angegeben:

* adobe-livecycle-native-jboss-x86_win32.ear > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar\com\adobe\appmon. Die Datei &quot;adobe-livecycle-native-jboss-x86_win32.ear&quot;befindet sich im Exportordner unter *[Installationsordner für AEM Forms]\*configurationManager. (Wenn AEM Forms auf einem anderen J2EE-Anwendungsserver bereitgestellt wird, ersetzen Sie die Datei &quot;adobe-livecycle-native-jboss-x86_win32.ear&quot;durch die EAR-Datei, die Ihrem J2EE-Anwendungsserver entspricht.)
* adobe-generatepdf-dsc.jar > adobe-appmondata.jar\com\adobe\appmon (die Datei adobe-appmondata.jar befindet sich in der Datei adobe-generatepdf-dsc.jar ). Die Datei &quot;adobe-generatepdf-dsc.jar&quot;befindet sich im *[Installationsordner für AEM Forms]*\deploy .

Nachdem Sie diese XML-Dateien zur Datei adobe-appmondata.jar hinzugefügt haben, müssen Sie die GeneratePDF-Komponente erneut bereitstellen. Führen Sie die folgenden Aufgaben aus, um der Datei &quot;adobe-appmondata.jar&quot;Dialog- und Skript-XML-Dateien hinzuzufügen:

1. Öffnen Sie mit einem Tool wie WinZip oder WinRAR die Datei adobe-livecycle-native-jboss-x86_win32.earfile > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar Datei.
1. Fügen Sie das Dialogfeld und die Skript-XML-Dateien zur Datei &quot;appmondata.jar&quot;hinzu oder ändern Sie vorhandene XML-Dateien in dieser Datei. (Siehe [Erstellen oder Ändern einer XML-Skript-Datei für eine native Anwendung](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)und [Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für eine native Anwendung](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application).
1. Öffnen Sie mit einem Tool wie WinZip oder WinRAR adobe-generatepdf-dsc.jar > adobe-appmondata.jar .
1. Fügen Sie das Dialogfeld und die Skript-XML-Dateien zur Datei &quot;appmondata.jar&quot;hinzu oder ändern Sie vorhandene XML-Dateien in dieser Datei. (Siehe [Erstellen oder Ändern einer XML-Skript-Datei für eine native Anwendung](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)und [Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für eine native Anwendung](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application). Nachdem Sie die XML-Dateien zur Datei &quot;adobe-appmondata.jar&quot;hinzugefügt haben, platzieren Sie die neue Datei &quot;adobe-appmondata.jar&quot;in die Datei &quot;adobe-generatepdf-dsc.jar&quot;.
1. Wenn Sie Unterstützung für ein zusätzliches natives Dateiformat hinzugefügt haben, erstellen Sie eine Systemumgebungsvariable, die den Pfad der Anwendung bereitstellt (siehe [Umgebungsvariable zum Suchen der nativen Anwendung erstellen](converting-file-formats-pdf.md#creating-an-environment-variable-to-locate-the-native-application).

**So stellen Sie die GeneratePDF-Komponente erneut bereit**

1. Melden Sie sich bei Workbench an.
1. Auswählen **Fenster** > **Ansichten anzeigen** > **Komponenten**. Durch diese Aktion wird die Ansicht &quot;Components&quot;zu Workbench hinzugefügt.
1. Klicken Sie mit der rechten Maustaste auf die GeneratePDF-Komponente und wählen Sie **Stopp-Komponente**.
1. Wenn die Komponente angehalten wurde, klicken Sie mit der rechten Maustaste und wählen Sie Komponente deinstallieren , um sie zu entfernen.
1. Klicken Sie mit der rechten Maustaste auf die **Komponenten** Symbol und wählen Sie **Komponente installieren**.
1. Suchen Sie die geänderte Datei &quot;adobe-generatepdf-dsc.jar&quot;und wählen Sie sie aus. Klicken Sie dann auf &quot;Öffnen&quot;. Beachten Sie, dass neben der GeneratePDF-Komponente ein rotes Quadrat angezeigt wird.
1. Erweitern Sie die Komponente GeneratePDF , wählen Sie Service Descriptors und klicken Sie dann mit der rechten Maustaste auf GeneratePDFService und wählen Sie Activate Service.
1. Geben Sie im angezeigten Konfigurationsdialogfeld die entsprechenden Konfigurationswerte ein. Wenn Sie diese Werte leer lassen, werden die Standardkonfigurationswerte verwendet.
1. Klicken Sie mit der rechten Maustaste auf GeneratePDF und wählen Sie &quot;Start Component&quot;.
1. Erweitern Sie Aktive Dienste . Neben dem Dienstnamen wird ein grüner Pfeil angezeigt, wenn er ausgeführt wird. Andernfalls befindet sich der Dienst im Status &quot;Angehalten&quot;.
1. Wenn der Dienst angehalten ist, klicken Sie mit der rechten Maustaste auf den Dienstnamen und wählen Sie &quot;Dienst starten&quot;.

### Erstellen oder Ändern einer XML-Skript-Datei für eine native Anwendung {#creating-or-modifying-a-script-xml-file-for-a-native-application}

Wenn Sie Dateien an eine neue native Anwendung weiterleiten möchten, müssen Sie eine XML-Skript-Datei für diese Anwendung erstellen. Wenn Sie ändern möchten, wie der Generate PDF-Dienst mit einer bereits unterstützten nativen Anwendung interagiert, müssen Sie das Skript für diese Anwendung ändern.

Das Skript enthält Anweisungen, die durch die Fensterelemente der nativen Anwendung navigieren und spezifische Antworten auf diese Elemente bereitstellen. Die Datei, die diese Informationen enthält, ist appmon.*[appname]*.script.*[locale]*.xml. Ein Beispiel ist appmon.notepad.script.en_US.xml.

#### Identifizieren der Schritte, die das Skript ausführen muss {#identifying-steps-the-script-must-execute}

Bestimmen Sie mithilfe des nativen Programms die Fensterelemente, die Sie navigieren müssen, und jede Antwort, die Sie zum Drucken des Dokuments ausführen müssen. Beachten Sie die Dialogfelder, die aus einer Antwort resultieren. Die Schritte ähneln den folgenden Schritten:

1. Wählen Sie „Datei“ > „Öffnen“.
1. Geben Sie den Pfad an und klicken Sie dann auf &quot;Öffnen&quot;.
1. Wählen Sie in der Menüleiste Datei > Drucken aus.
1. Geben Sie die für den Drucker erforderlichen Eigenschaften an.
1. Wählen Sie &quot;Drucken&quot;aus und warten Sie, bis das Dialogfeld &quot;Speichern unter&quot;angezeigt wird. Das Dialogfeld &quot;Speichern unter&quot;ist erforderlich, damit der Generate PDF-Dienst das Ziel für die PDF-Datei angeben kann.

#### Identifizieren der in Beschriftungsattributen angegebenen Dialogfelder {#identifying-the-dialogs-specified-in-caption-attributes}

Verwenden Sie Microsoft Spy++, um die Identitäten der Fensterelementeigenschaften im nativen Programm abzurufen. Sie müssen über diese Identitäten verfügen, um Skripte zu schreiben.

#### Verwenden regulärer Ausdrücke in Beschriftungsattributen {#using-regular-expressions-in-caption-attributes}

Sie können reguläre Ausdrücke in Beschriftungsspezifikationen verwenden. Der Generate PDF-Dienst verwendet die `java.util.regex.Matcher` -Klasse, um reguläre Ausdrücke zu unterstützen. Dieses Dienstprogramm unterstützt die regulären Ausdrücke, die unter `java.util.regex.Pattern`.

**Regulärer Ausdruck, der den Dateinamen unterstützt, dem im Editor-Banner Notepad vorangestellt wird**

```as3
 <!-- The regular expression ".*Notepad" means any number of non-terminating characters followed by Notepad. --> 
 <step> 
     <expectedWindow> 
         <window caption=".*Notepad"/> 
     </expectedWindow> 
 </step>
```

**Regulärer Ausdruck, der Druck von der Druckeinrichtung unterscheidet**

```as3
 <!-- This regular expression differentiates the Print dialog box from the Print Setup dialog box. The "^" specifies the beginning of the line, and the "$" specifies the end of the line. --> 
 <windowList> 
     <window controlID="0x01" caption="^Print$" action="press"/> 
 </windowList>
```

#### Sortieren von window- und windowList-Elementen {#ordering-the-window-and-windowlist-elements}

Sie müssen bestellen `window` und `windowList` -Elemente wie folgt:

* Wenn mehrere `window` -Elemente werden als untergeordnete Elemente in `windowList` oder `dialog` -Element, diese sortieren `window` -Elemente in absteigender Reihenfolge, mit den Längen der `caption` Namen, die die Position in der Reihenfolge angeben.
* Wenn mehrere `windowList` -Elemente in `window` -Element, diese sortieren `windowList` -Elemente in absteigender Reihenfolge, mit den Längen der `caption` -Attribute der ersten `indexes/`-Element, das die Position in der Reihenfolge angibt.

**Sortieren von Fensterelementen in einer Dialogfelddatei**

```as3
 <!-- The caption attribute in the following window element is 40 characters long. It is the longest caption in this example, so its parent window element appears before the others. --> 
 <window caption="Unexpected Failure in DebugActiveProcess"> 
     <…> 
 </window> 
  
 <!-- Caption length is 33 characters. --> 
 <window caption="Adobe Acrobat - License Agreement"> 
     <…> 
 </window> 
  
 <!-- Caption length is 33 characters. --> 
 <window caption="Microsoft Visual.*Runtime Library"> 
     <…> 
 </window> 
  
 <!-- The caption attribute in the following window element is 28 characters long. It is the shortest caption in this example, so its parent window element appears after the others. --> 
 <window caption="Adobe Acrobat - Registration"> 
     <…> 
 </window>
```

**Sortieren von Fensterelementen in einem windowList-Element**

```as3
 <!-- The caption attribute in the following indexes element is 56 characters long. It is the longest caption in this example, so its parent window element appears before the others. --> 
 <windowList> 
     <window caption="Can&apos;t exit design mode because.* cannot be created"/> 
     <window className="Button" caption="OK" action="press"/> 
 </windowList> 
 <windowList> 
     <window caption="Do you want to continue loading the project?"/> 
     <window className="Button" caption="No" action="press"/> 
 </windowList> 
 <windowList> 
     <window caption="The macros in this project are disabled"/> 
     <window className="Button" caption="OK" action="press"/> 
 </windowList>
```

### Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für eine native Anwendung {#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application}

Wenn Sie ein Skript für eine native Anwendung erstellen, die zuvor nicht unterstützt wurde, müssen Sie auch eine zusätzliche XML-Dialogfelddatei für diese Anwendung erstellen. Jede native Anwendung, die von AppMon verwendet wird, darf nur eine zusätzliche XML-Dialogfelddatei haben. Die zusätzliche XML-Datei des Dialogfelds ist erforderlich, auch wenn keine unangeforderten Dialogfelder erwartet werden. Das zusätzliche Dialogfeld muss mindestens ein `window` -Element, auch wenn dies `window` -Element ist lediglich ein Platzhalter.

>[!NOTE]
>
>In diesem Zusammenhang bedeutet der zusätzliche Begriff den Inhalt des Apfels.[applicationname].additional.[locale].xml-Datei. Eine solche Datei gibt Überschreibungen und Ergänzungen der XML-Datei des Dialogfelds an.

Sie können für folgende Zwecke auch die zusätzliche XML-Datei für das Dialogfeld für eine native Anwendung ändern:

* So überschreiben Sie die XML-Datei des Dialogfelds für eine Anwendung mit einer anderen Antwort
* So fügen Sie eine Antwort zu einem Dialogfeld hinzu, das nicht in der XML-Dialogfelddatei für diese Anwendung angesprochen ist

Der Dateiname, der eine zusätzliche dialogXML-Datei angibt, wird angezeigt.*[appname]*.additional.*[locale]*.xml. Ein Beispiel ist appmon.excel.additional.de_DE.xml.

Der Name der XML-Datei des zusätzlichen Dialogfelds muss das Format appmon verwenden.*[applicationname]*.additional.*[locale]*.xml, wobei *applicationname* muss genau mit dem Anwendungsnamen übereinstimmen, der in der XML-Konfigurationsdatei und im Skript verwendet wird.

>[!NOTE]
>
>Keine der generischen Anwendungen, die in der Konfigurationsdatei native2pdfconfig.xml angegeben sind, verfügt über eine primäre XML-Dialogfelddatei. Der Abschnitt [Unterstützung für ein natives Dateiformat hinzufügen oder ändern](converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format) beschreibt diese Spezifikationen.

Sie müssen bestellen `windowList` -Elemente, die in einer `window` -Element. (Siehe [Sortieren von window- und windowList-Elementen](converting-file-formats-pdf.md#ordering-the-window-and-windowlist-elements).

### XML-Datei des allgemeinen Dialogfelds ändern {#modifying-the-general-dialog-xml-file}

Sie können die allgemeine XML-Datei des Dialogfelds ändern, um auf vom System generierte Dialogfelder zu reagieren oder auf Dialogfelder zu reagieren, die für mehrere Anwendungen gelten.

#### Hinzufügen eines Dateitypeintrags in der XML-Konfigurationsdatei {#adding-a-filetype-entry-in-the-xml-configuration-file}

In diesem Verfahren wird beschrieben, wie Sie die Konfigurationsdatei des Generate PDF-Dienstes aktualisieren, um Dateitypen mit nativen Programmen zu verknüpfen. Um diese Konfigurationsdatei zu aktualisieren, müssen Sie die Konfigurationsdaten mithilfe von Administration Console in eine Datei exportieren. Der standardmäßige Dateiname für die Konfigurationsdaten lautet &quot;native2pdfconfig.xml&quot;.

**Aktualisieren der Konfigurationsdatei des Generate PDF-Dienstes**

1. Auswählen **Startseite** > **Dienste** > **Adobe PDF Generator** > **Konfigurationsdateien** und wählen Sie **Exportkonfiguration**.
1. Ändern Sie die `filetype-settings` -Element in der Datei native2pdfconfig.xml nach Bedarf.
1. Auswählen **Startseite** > **Dienste** > **Adobe PDF Generator** >**Konfigurationsdateien** und wählen Sie **Importkonfiguration**. Die Konfigurationsdaten werden in den Generate PDF-Dienst importiert, wobei die vorherigen Einstellungen ersetzt werden.

>[!NOTE]
>
>Der Name der Anwendung wird als Wert der `GenericApp` -Element `name` -Attribut. Dieser Wert muss genau mit dem entsprechenden Namen übereinstimmen, der im Skript angegeben ist, das Sie für diese Anwendung entwickeln. Ebenso wird die `GenericApp` -Element `displayName` sollte genau mit dem entsprechenden Skript übereinstimmen `expectedWindow` Fensterbeschriftung. Diese Gleichwertigkeit wird nach Auflösung von regulären Ausdrücken, die im `displayName` oder `caption` -Attribute.

In diesem Beispiel wurden die mit dem Generate PDF-Dienst bereitgestellten Standardkonfigurationsdaten geändert, um anzugeben, dass Notepad (nicht Microsoft Word) zur Verarbeitung von Dateien mit der Dateierweiterung .txt verwendet werden soll. Vor dieser Änderung wurde Microsoft Word als natives Programm angegeben, das solche Dateien verarbeiten soll.

**Änderungen für die Weiterleitung von Textdateien an Notepad (native2pdfconfig.xml)**

```as3
 <filetype-settings> 
  
 <!-- Some native app file types were omitted for brevity. --> 
 <!-- The following GenericApp element specifies Notepad as the native application that should be used to process files that have a txt file name extension. --> 
             <GenericApp 
                 extensions="txt" 
                 name="Notepad" displayName=".*Notepad"/> 
             <GenericApp  
                 extensions="wpd"  
                 name="WordPerfect" displayName="Corel WordPerfect"/> 
             <GenericApp extensions="pmd,pm6,p65,pm"  
                 name="PageMaker" displayName="Adobe PageMaker"/> 
             <GenericApp extensions="fm"  
                 name="FrameMaker" displayName="Adobe FrameMaker"/> 
             <GenericApp extensions="psd"  
                 name="Photoshop" displayName="Adobe Photoshop"/> 
         </settings> 
     </filetype-settings>
```

#### Umgebungsvariable zum Suchen der nativen Anwendung erstellen {#creating-an-environment-variable-to-locate-the-native-application}

Erstellen Sie eine Umgebungsvariable, die den Speicherort der ausführbaren Datei der nativen Anwendung angibt. Die Variable muss das Format *[applicationname]*_PATH, wobei *applicationname* muss genau mit dem Anwendungsnamen übereinstimmen, der in der XML-Konfigurationsdatei und im Skript verwendet wird und in dem der Pfad den Pfad zur ausführbaren Datei in doppelten Anführungszeichen enthält. Ein Beispiel für eine solche Umgebungsvariable ist `Photoshop_PATH`.

Nachdem Sie die neue Umgebungsvariable erstellt haben, müssen Sie den Server neu starten, auf dem der Generate PDF-Dienst bereitgestellt ist.

**Systemvariable in der Windows XP-Umgebung erstellen**

1. Auswählen **Control Panel > System**.
1. Klicken Sie im Dialogfeld &quot;Systemeigenschaften&quot;auf das **Erweitert** und klicken Sie auf **Umgebungsvariablen**.
1. Klicken Sie unter &quot;Systemvariablen&quot;im Dialogfeld &quot;Umgebungsvariablen&quot;auf **Neu**.
1. Im Dialogfeld &quot;Neue Systemvariable&quot;im **Variablenname** ein Feld, geben Sie einen Namen ein, der das Format verwendet *[applicationname]*_PATH.
1. Im **Variablenwert** Geben Sie den vollständigen Pfad und Dateinamen der ausführbaren Datei der Anwendung ein und klicken Sie auf **OK**. Geben Sie beispielsweise: `c:\windows\Notepad.exe`
1. Klicken Sie im Dialogfeld &quot;Umgebungsvariablen&quot;auf **OK**.

**Systemvariable über die Befehlszeile erstellen**

1. Geben Sie in einem Befehlszeilenfenster die Variablendefinition in folgendem Format ein:

   ```as3
            [applicationname]_PATH=[Full path name]
   ```

   Geben Sie beispielsweise: `NotePad_PATH=C:\WINDOWS\NOTEPAD.EXE`

1. Starten Sie eine neue Eingabeaufforderung, damit die Systemvariable wirksam wird.

#### XML-Dateien {#xml-files}

AEM Forms enthält XML-Beispieldateien, die dazu führen, dass der Generate PDF-Dienst Notepad zur Verarbeitung von Dateien mit der Dateinamenerweiterung .txt verwendet. Dieser Code ist in diesem Abschnitt enthalten. Darüber hinaus müssen Sie die anderen in diesem Abschnitt beschriebenen Änderungen vornehmen.

#### Zusätzliche XML-Dialogdatei {#additional-dialog-xml-file}

Dieses Beispiel enthält die zusätzlichen Dialogfelder für die Notepad-Anwendung. Diese Dialogfelder können zusätzlich zu den vom Generate PDF-Dienst angegebenen Dialogfeldern angezeigt werden.

**Editor-Dialogfelder (appmon.notepad.additional.de_DE.xml)**

```as3
 <dialogs app="Notepad" locale="en_US" version="7.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="dialogs.xsd"> 
     <window caption="Caption Title"> 
         <windowList> 
             <window className="Button" caption="OK" action="press"/> 
         </windowList> 
     </window> 
 </dialogs>
```

#### XML-Skriptdatei {#script-xml-file}

In diesem Beispiel wird angegeben, wie der Generate PDF-Dienst mit Notepad interagieren soll, um Dateien mithilfe des Adobe PDF-Druckers zu drucken.

**XML-Datei für Editor-Skript (appmon.notepad.script.en_US.xml)**

```as3
<?xml version="1.0" encoding="UTF-8" standalone="yes"?> 
<!-- 
* 
* ADOBE CONFIDENTIAL 
* ___________________ 
* Copyright 2004 - 2005 Adobe Systems Incorporated 
* All Rights Reserved. 
* 
* NOTICE:  All information contained herein is, and remains 
* the property of Adobe Systems Incorporated and its suppliers, 
* if any.  The intellectual and technical concepts contained 
* herein are proprietary to Adobe Systems Incorporated and its 
* suppliers and may be covered by U.S. and Foreign Patents, 
* patents in process, and are protected by trade secret or copyright law. 
* Dissemination of this information or reproduction of this material 
* is strictly forbidden unless prior written permission is obtained 
* from Adobe Systems Incorporated. 
*--> 
 
<!-- This file automates printing of text files via notepad to Adobe PDF printer. In order to see the complete hierarchy we recommend using the Microsoft Spy++ which details the properties of windows necessary to write scripts. In this sample there are total of eight steps--> 
 
<application name="Notepad" version="9.0" locale="en_US" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="scripts.xsd"> 
 
    <!-- In this step we wait for the application window to appear --> 
    <step> 
        <expectedWindow> 
            <window caption=".*Notepad"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the application window and send File->Open menu bar, menu item commands and the expectation is the windows Open dialog-->         
    <step> 
        <acquiredWindow> 
            <window caption=".*Notepad"> 
                <virtualInput> 
                    <menuBar> 
                        <selection> 
                            <name>File</name> 
                        </selection> 
                        <selection> 
                            <name>Open...</name> 
                        </selection> 
                    </menuBar> 
                </virtualInput> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Open"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the Open window and then select the 'Edit' widget and input the source path followed by clicking on the 'Open' button . The expectation of this 'action' is that the Open dialog will disappear --> 
    <step> 
        <acquiredWindow> 
            <window caption="Open"> 
                <windowList> 
                    <window className="ComboBoxEx32"> 
                        <windowList> 
                            <window className="ComboBox"> 
                                <windowList> 
                                <window className="Edit" action="inputSourcePath"/> 
                                </windowList> 
                            </window> 
                        </windowList> 
                    </window> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="Open" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Open" action="disappear"/> 
        </expectedWindow> 
        <pause value="30"/> 
    </step> 
     
    <!-- In this step, we acquire the application window and send File->Print menu bar, menu item commands and the expectation is the windows Print dialog--> 
    <step> 
        <acquiredWindow> 
            <window caption=".*Notepad"> 
                <virtualInput> 
                    <menuBar> 
                        <selection> 
                            <name>File</name> 
                        </selection> 
                        <selection> 
                            <name>Print...</name> 
                        </selection> 
                    </menuBar> 
                </virtualInput> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Print"> 
        </window> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the Print dialog and click on the 'Preferences' button and the expected window in this case is the dialog with the caption '"Printing Preferences' --> 
    <step> 
        <acquiredWindow> 
            <window caption="Print"> 
                <windowList> 
                    <window caption="General"> 
                        <windowList> 
                            <window className="Button" caption="Preferences" action="press"/> 
                        </windowList> 
                    </window> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Printing Preferences"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the dialog "Printing Preferences' and select the combo box which is the 10th child of window with caption '"Adobe PDF Settings' and select the first index. (Note: All indeces start with 0.) Besides this we uncheck the box which  has the caption '"View Adobe PDF results' and we click on the button OK. The expectation is that 'Printing Preferences' dialog disappears. --> 
    <step> 
        <acquiredWindow> 
            <window caption="Printing Preferences"> 
                <windowList> 
                    <window caption="Adobe PDF Settings"> 
                        <windowList> 
                            <window className="Button" caption="View Adobe PDF results" action="uncheck"/> 
                        </windowList> 
                        <windowList> 
                            <window className="Button" caption="Ask to Replace existing PDF file" action="uncheck"/> 
                        </windowList> 
                    </window> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="OK" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Printing Preferences" action="disappear"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the 'Print' dialog and click on the Print button. The expectation is that the dialog with caption 'Print' disappears. In this case we use the regular expression '^Print$' for specifying the caption given there could be multiple dialogs with caption that includes the word Print. --> 
    <step> 
        <acquiredWindow> 
            <window caption="Print"> 
                <windowList> 
                    <window caption="General"/> 
                    <window className="Button" caption="^Print$" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Print" action="disappear"/> 
        </expectedWindow> 
    </step> 
    <step> 
        <expectedWindow> 
            <window caption="Save PDF File As"/> 
        </expectedWindow> 
    </step> 
    <!-- Finally in this step, we acquire the dialog with caption "Save PDF File As" and in the Edit widget type the destination path for the output PDF file and click on the Save button. The expectation is that the dialog disappears--> 
    <step> 
        <acquiredWindow> 
            <window caption="Save PDF File As"> 
                <windowList> 
                    <window className="Edit" action="inputDestinationPath"/> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="Save" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Save PDF File As" action="disappear"/> 
        </expectedWindow> 
    </step> 
     
    <!-- We can always set a retry count or a maximum time for a step. In case we surpass these limitations, PDF Generator generates this abort message and terminates processing. --> 
    <abortMessage msg="15078"/> 
</application>
```
