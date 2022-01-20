---
title: Konvertieren von Postscript in PDF-Dokumente
seo-title: Converting Postscript to PDF Documents
description: Verwenden Sie den Distiller-Dienst zum Konvertieren von PostScript®-, Encapsulated PostScript (EPS)- und PRN-Dateien, um PDF-Dateien über ein Netzwerk zu komprimieren, zuverlässig und sicherer zu machen. Der Distiller-Dienst konvertiert große Mengen von Druckdokumenten in elektronische Dokumente, z. B. Rechnungen und Aussagen mithilfe der Java-API und der Web Service-API.
seo-description: Use the Distiller service to convert PostScript®, Encapsulated PostScript (EPS), and PRN files to compact, reliable, and more secure PDF files over a network. The Distiller service converts large volumes of print documents to electronic documents, such as invoices and statements using the Java API and Web Service API.
uuid: 2143f406-1fdd-4551-a738-1a8388f8d478
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 06ad343a-f74d-41f5-b3c8-b85bb723ceeb
role: Developer
exl-id: 8bfbeef8-d211-4e87-8cd5-adccb21a6e05
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 7%

---

# Konvertieren von Postscript in PDF-Dokumente {#converting-postscript-to-pdf-documents}

## Über den Distiller-Dienst {#about-the-distiller-service}

Der Distiller®-Dienst konvertiert PostScript®-, Encapsulated PostScript (EPS)- und PRN-Dateien in kompakte, zuverlässige und sicherere PDF-Dateien über ein Netzwerk. Der Distiller-Dienst dient häufig zum Konvertieren großen Mengen gedruckter Dokumente in elektronische Dokumente, z. B. Rechnungen und Belege. Das Konvertieren von Dokumenten in PDF ermöglicht Unternehmen auch, ihren Kunden eine Papier- und eine elektronische Version eines Dokuments zu senden.

>[!NOTE]
>
>Weitere Informationen zum Distiller-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PostScript in PDF-Dokumente {#converting-postscript-to-pdf-documents-inner}

Hier wird beschrieben, wie Sie mit der Distiller Service API (Java- und Webdienst) PostScript- (PS), Encapsulated PostScript- (EPS) und PRN-Dateien programmgesteuert in PDF-Dokumente konvertieren können.

>[!NOTE]
>
>Weitere Informationen zum Distiller-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Um PostScript-Dateien in PDF-Dokumente zu konvertieren, muss eine der folgenden Dateien auf dem Server installiert sein, der als Host für AEM Forms dient: Acrobat 9 oder Microsoft Visual C++ 2005 Redistributable Package.

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um einen der unterstützten Typen in ein PDF-Dokument zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Distiller-Dienstclient.
1. Rufen Sie die zu konvertierende Datei ab.
1. Rufen Sie den PDF-Erstellungsvorgang auf.
1. Speichern Sie das PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Distiller-Dienstclients**

Bevor Sie einen Distiller-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Distiller-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `DistillerServiceClient` -Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie eine `DistillerServiceService` -Objekt.

**Zu konvertierende Datei abrufen**

Sie müssen die Datei abrufen, die Sie konvertieren möchten. Um beispielsweise eine PS-Datei in ein PDF-Dokument zu konvertieren, müssen Sie die PS-Datei abrufen.

**Aufrufen des PDF-Erstellungsvorgangs**

Nachdem Sie den Service-Client erstellt haben, können Sie den PDF-Erstellungsvorgang aufrufen. Dieser Vorgang benötigt Informationen zum zu konvertierenden Dokument, einschließlich des Pfads zum Zieldokument.

**PDF-Dokument speichern**

Sie können das PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Konvertieren einer PostScript-Datei in eine PDF mithilfe der Java-API](converting-postscript-pdf-documents.md#convert-a-postscript-file-to-pdf-using-the-java-api)

[Konvertieren einer PostScript-Datei in eine PDF mithilfe der Webdienst-API](converting-postscript-pdf-documents.md#converting-a-postscript-file-to-pdf-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Konvertieren einer PostScript-Datei in eine PDF mithilfe der Java-API {#convert-a-postscript-file-to-pdf-using-the-java-api}

Konvertieren Sie eine PostScript-Datei mithilfe der Distiller Service API (Java) in ein PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-tiller-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Distiller-Dienstclient.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `DistillerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Rufen Sie die zu konvertierende Datei ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das die zu konvertierende Datei mithilfe ihres Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort der Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Rufen Sie den PDF-Erstellungsvorgang auf.

   Rufen Sie die `DistillerServiceClient` -Objekt `createPDF` -Methode verwenden und die folgenden Werte übergeben:

   * Die `com.adobe.idp.Document` -Objekt, das die zu konvertierende PS-, EPS- oder PRN-Datei darstellt
   * A `java.lang.String` -Objekt, das den Namen der zu konvertierenden Datei enthält
   * A `java.lang.String` -Objekt, das den Namen der zu verwendenden Adobe PDF-Einstellungen enthält
   * A `java.lang.String` -Objekt, das den Namen der zu verwendenden Sicherheitseinstellungen enthält
   * Ein optionales `com.adobe.idp.Document` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen
   * Ein optionales `com.adobe.idp.Document` -Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen

   Die `createPDF` -Methode gibt eine `CreatePDFResult` -Objekt, das das neue PDF-Dokument und eine eventuell generierte Protokolldatei enthält. Die Protokolldatei enthält in der Regel Fehler- oder Warnmeldungen, die von der Konvertierungsanforderung generiert werden.

1. Speichern Sie das PDF-Dokument.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Rufen Sie die `CreatePDFResult` -Objekt `getCreatedDocument` -Methode. Dadurch wird eine `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument zu extrahieren.

   Um das Protokolldokument abzurufen, führen Sie die folgenden Schritte aus.

   * Rufen Sie die `CreatePDFResult` -Objekt `getLogDocument` -Methode. Dadurch wird eine `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das Protokolldokument zu extrahieren.


**Siehe auch**

[Zusammenfassung der Schritte](converting-postscript-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Konvertieren einer PostScript-Datei in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren einer PostScript-Datei in eine PDF mithilfe der Webdienst-API {#converting-a-postscript-file-to-pdf-using-the-web-service-api}

Konvertieren Sie eine PostScript-Datei mithilfe der Distiller Service-API (Webdienst) in ein PDF-Dokument:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/DistillerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Distiller-Dienstclient.

   * Erstellen Sie eine `DistillerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `DistillerServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DistillerService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `DistillerServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `DistillerServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DistillerServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie die zu konvertierende Datei ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Diese `BLOB` -Objekt wird verwendet, um die Datei zu speichern, die in ein PDF-Dokument konvertiert werden soll.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Rufen Sie den PDF-Erstellungsvorgang auf.

   Rufen Sie die `DistillerServiceService` -Objekt `CreatePDF2` -Methode verwenden und die folgenden erforderlichen Werte übergeben:

   * Die `BLOB` -Objekt, das die zu konvertierende PS-Datei darstellt
   * Eine Zeichenfolge, die den Pfadnamen der zu konvertierenden Datei enthält
   * Ein Zeichenfolgenobjekt, das die zu verwendenden Adobe PDF-Einstellungen enthält (z. B. `Standard`)
   * Ein string -Objekt, das die zu verwendenden Sicherheitseinstellungen enthält (z. B. `No Securit`y)
   * Ein optionales `BLOB` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen
   * Ein optionales `BLOB` -Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen
   * A `BLOB` Ausgabeparameter zum Speichern des PDF-Dokuments
   * A `BLOB` Ausgabeparameter zum Speichern des Protokolls

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort des signierten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt, das von der `CreatePDF2` -Methode (der Ausgabeparameter). Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-postscript-pdf-documents.md#summary-of-steps)

<!-- UNRESOLVED LINKS
[Quick Start (MTOM): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7f01.2)

[Quick Start (SwaRef): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7eff.2)
-->

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
