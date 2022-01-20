---
title: DDX-Dokumente dynamisch erstellen
seo-title: Dynamically Creating DDX Documents
description: Erstellen Sie ein DDX-Dokument dynamisch mit der Java-API und der Web Service-API. Durch das dynamische Erstellen eines DDX-Dokuments können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden.
seo-description: Create a DDX document dynamically using the Java API and Web Service API. Dynamically creating a DDX document enables you to use values in the DDX document that are obtained during run-time.
uuid: b73e8069-6c9f-4517-a0ae-f3d503191d2d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 2ad227de-68a8-446f-8c4f-a33a6f95bec8
role: Developer
exl-id: 883b33c8-50b1-4df2-a762-02be67ce24f1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2149'
ht-degree: 4%

---

# DDX-Dokumente dynamisch erstellen {#dynamically-creating-ddx-documents}

Sie können ein DDX-Dokument dynamisch erstellen, das zum Ausführen eines Assembler-Vorgangs verwendet werden kann. Durch das dynamische Erstellen eines DDX-Dokuments können Sie Werte im DDX-Dokument verwenden, die während der Laufzeit abgerufen werden. Verwenden Sie zum dynamischen Erstellen eines DDX-Dokuments Klassen, die zur verwendeten Programmiersprache gehören. Wenn Sie beispielsweise Ihre Clientanwendung mit Java entwickeln, verwenden Sie Klassen, die zum `org.w3c.dom.*`Paket. Wenn Sie Microsoft .NET verwenden, verwenden Sie ebenfalls Klassen, die zum `System.Xml` Namespace.

Bevor Sie das DDX-Dokument an den Assembler-Dienst übergeben können, konvertieren Sie die XML aus einem `org.w3c.dom.Document` -Instanz zu einer `com.adobe.idp.Document` -Instanz. Wenn Sie Webdienste verwenden, konvertieren Sie die XML aus dem Datentyp, der zum Erstellen der XML verwendet wurde (z. B. `XmlDocument`) zu `BLOB` -Instanz.

Angenommen, das folgende DDX-Dokument wird dynamisch erstellt.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
      <PDFsFromBookmarks prefix="stmt"> 
     <PDF source="AssemblerResultPDF.pdf"/> 
 </PDFsFromBookmarks> 
 </DDX>
```

Dieses DDX-Dokument zerlegt ein PDF-Dokument. Es wird empfohlen, dass Sie mit dem Zerlegen von PDF-Dokumenten vertraut sind.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument mithilfe eines dynamisch erstellten DDX-Dokuments aufzuteilen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Erstellen Sie das DDX-Dokument.
1. Konvertieren Sie das DDX-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Lösen Sie das PDF-Dokument aus.
1. Speichern Sie die zerlegten PDF-Dokumente.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, erstellen Sie einen Assembler-Dienst-Client.

**DDX-Dokument erstellen**

Erstellen Sie ein DDX-Dokument mit der verwendeten Programmiersprache. Um ein DDX-Dokument zu erstellen, das ein PDF-Dokument aufteilt, stellen Sie sicher, dass es die `PDFsFromBookmarks` -Element. Konvertieren Sie den zum Erstellen des DDX-Dokuments verwendeten Datentyp in einen `com.adobe.idp.Document` -Instanz verwenden, wenn Sie die Java-API verwenden. Wenn Sie Webdienste verwenden, konvertieren Sie den Datentyp in eine `BLOB` -Instanz.

**Konvertieren des DDX-Dokuments**

Ein DDX-Dokument, das mithilfe von `org.w3c.dom` -Klassen in eine `com.adobe.idp.Document` -Objekt. Verwenden Sie Java XML Transformation-Klassen, um diese Aufgabe bei Verwendung der Java-API auszuführen. Wenn Sie Webdienste verwenden, konvertieren Sie das DDX-Dokument in ein `BLOB` -Objekt.

**Referenzieren eines zerlegbaren PDF-Dokuments**

Um ein PDF-Dokument zu zerlegen, verweisen Sie auf eine PDF-Datei, die das zu zerlegende PDF-Dokument darstellt. Wenn an den Assembler-Dienst übergeben wird, wird für jedes Lesezeichen der Stufe 1 im PDF ein separates Dokument zurückgegeben.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Zum Festlegen von Laufzeitoptionen verwenden Sie eine `AssemblerOptionSpec` -Objekt.

**Aufteilen des PDF-Dokuments**

Aufrufen des PDF-Dokuments durch `invokeDDX` Vorgang. Übergeben Sie das dynamisch erstellte DDX-Dokument. Der Assembler-Dienst gibt zerlegte PDF-Dokumente innerhalb eines Sammlungsobjekts zurück.

**Speichern Sie die zerlegten PDF-Dokumente**

Alle zerlegten PDF-Dokumente werden innerhalb eines Sammlungsobjekts zurückgegeben. Durchlaufen Sie das Sammlungsobjekt und speichern Sie jedes PDF-Dokument als PDF-Datei.

**Siehe auch**

[DDX-Dokument mithilfe der Java-API dynamisch erstellen](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-java-api)

[DDX-Dokument mithilfe der Webdienst-API dynamisch erstellen](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuerte Demontage von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## DDX-Dokument mithilfe der Java-API dynamisch erstellen {#dynamically-create-a-ddx-document-using-the-java-api}

Dynamisches Erstellen eines DDX-Dokuments und Aufteilen eines PDF-Dokuments mithilfe der Assembler Service-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Erstellen Sie das DDX-Dokument.

   * Java erstellen `DocumentBuilderFactory` -Objekt durch Aufruf der `DocumentBuilderFactory` class&quot; `newInstance` -Methode.
   * Java erstellen `DocumentBuilder` -Objekt durch Aufruf der `DocumentBuilderFactory` -Objekt `newDocumentBuilder` -Methode.
   * Rufen Sie die `DocumentBuilder` -Objekt `newDocument` -Methode zur Instanziierung einer `org.w3c.dom.Document` -Objekt.
   * Erstellen Sie das Stammelement des DDX-Dokuments, indem Sie die `org.w3c.dom.Document` -Objekt `createElement` -Methode. Diese Methode erstellt eine `Element` -Objekt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `setAttribute` -Methode. Hängen Sie das Element schließlich an das Kopfzeilenelement an, indem Sie die `appendChild` -Methode und übergeben Sie das untergeordnete Element-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:
      ` Element root = (Element)document.createElement("DDX");  root.setAttribute("xmlns","https://ns.adobe.com/DDX/1.0/");  document.appendChild(root);`

   * Erstellen Sie die `PDFsFromBookmarks` -Element durch Aufruf der `Document` -Objekt `createElement` -Methode. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie einen Wert für die `PDFsFromBookmarks` -Element durch Aufruf von `setAttribute` -Methode. Anhängen der `PDFsFromBookmarks` -Element zu `DDX` -Element durch Aufruf des DDX-Elements `appendChild` -Methode. Übergeben Sie die `PDFsFromBookmarks` element -Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element PDFsFromBookmarks = (Element)document.createElement("PDFsFromBookmarks");  PDFsFromBookmarks.setAttribute("prefix","stmt");  root.appendChild(PDFsFromBookmarks);`

   * Erstellen Sie eine `PDF` -Element durch Aufruf der `Document` -Objekt `createElement` -Methode. Übergeben Sie einen string -Wert, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie einen Wert für die `PDF` -Element durch Aufruf von `setAttribute` -Methode. Anhängen der `PDF` -Element zu `PDFsFromBookmarks` -Element durch Aufruf der `PDFsFromBookmarks` -Element `appendChild` -Methode. Übergeben Sie die `PDF` element -Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element PDF = (Element)document.createElement("PDF");  PDF.setAttribute("source","AssemblerResultPDF.pdf");  PDFsFromBookmarks.appendChild(PDF);`

1. Konvertieren Sie das DDX-Dokument.

   * Erstellen Sie eine `javax.xml.transform.Transformer` -Objekt durch Aufrufen der `javax.xml.transform.Transformer` Statische Objektform `newInstance` -Methode.
   * Erstellen Sie eine `Transformer` -Objekt durch Aufrufen der `TransformerFactory` -Objekt `newTransformer` -Methode.
   * Erstellen Sie ein Objekt `ByteArrayOutputStream`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein Objekt `javax.xml.transform.dom.DOMSource`, indem Sie den Konstruktor verwenden. Übergeben Sie die `org.w3c.dom.Document` -Objekt, das das DDX-Dokument darstellt.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource`-Objekt, indem Sie seinen Konstruktor verwenden und das `ByteArrayOutputStream`-Objekt übergeben.
   * Java ausfüllen `ByteArrayOutputStream` -Objekt durch Aufrufen der `javax.xml.transform.Transformer` -Objekt `transform` -Methode. Übergeben Sie die `javax.xml.transform.dom.DOMSource` und `javax.xml.transform.stream.StreamResult` Objekte.
   * Erstellen Sie ein Byte-Array und weisen Sie die Größe der `ByteArrayOutputStream` -Objekt zum Byte-Array hinzu.
   * Füllen Sie das Byte-Array, indem Sie die `ByteArrayOutputStream` -Objekt `toByteArray` -Methode.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, indem Sie seinen Konstruktor verwenden und das Byte-Array übergeben.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie eine `java.util.Map` -Objekt, das zum Speichern von Eingabe-PDF-Dokumenten mithilfe eines `HashMap` -Konstruktor.
   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort des PDF-Dokuments an die Disassemblierung übergeben.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt. Übergeben Sie die `java.io.FileInputStream` -Objekt, das das zu zerlegende PDF-Dokument enthält.
   * Fügen Sie dem `java.util.Map` -Objekt durch Aufrufen seiner `put` -Methode verwenden und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Im dynamisch erstellten DDX-Dokument lautet der Wert `AssemblerResultPDF.pdf`.
      * A `com.adobe.idp.Document` -Objekt, das das zu zerlegende PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `AssemblerOptionSpec` -Objekt `setFailOnError` -Methode und -übergabe `false`.

1. Lösen Sie das PDF-Dokument aus.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das dynamisch erstellte DDX-Dokument darstellt
   * A `java.util.Map` -Objekt, das das zu zerlegende PDF-Dokument enthält
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Auftragsprotokollebene

   Die `invokeDDX` -Methode gibt eine `com.adobe.livecycle.assembler.client.AssemblerResult` -Objekt, das die zerlegten PDF-Dokumente und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die zerlegten PDF-Dokumente abzurufen:

   * Rufen Sie die `AssemblerResult` -Objekt `getDocuments` -Methode. Diese Methode gibt eine `java.util.Map` -Objekt.
   * Iteration durch die `java.util.Map` -Objekt, bis Sie das Ergebnis finden `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Schnellstart (SOAP-Modus): DDX-Dokument mithilfe der Java-API dynamisch erstellen](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-dynamically-creating-a-ddx-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## DDX-Dokument mithilfe der Webdienst-API dynamisch erstellen {#dynamically-create-a-ddx-document-using-the-web-service-api}

Dynamisches Erstellen eines DDX-Dokuments und Aufteilen eines PDF-Dokuments mithilfe der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie eine `AssemblerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `AssemblerServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `AssemblerServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Erstellen Sie das DDX-Dokument.

   * Erstellen Sie ein Objekt `System.Xml.XmlElement`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie das Stammelement des DDX-Dokuments, indem Sie die `XmlElement` -Objekt `CreateElement` -Methode. Diese Methode erstellt eine `Element` -Objekt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `CreateElement` -Methode. Legen Sie einen Wert für das DDX-Element fest, indem Sie dessen `SetAttribute` -Methode. Hängen Sie abschließend das Element an das DDX-Dokument an, indem Sie die `XmlElement` -Objekt `AppendChild` -Methode. Übergeben Sie das DDX-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` System.Xml.XmlElement root = ddx.CreateElement("DDX");  root.SetAttribute("xmlns", "https://ns.adobe.com/DDX/1.0/");  ddx.AppendChild(root);`

   * Erstellen des DDX-Dokuments `PDFsFromBookmarks` -Element durch Aufruf der `XmlElement` -Objekt `CreateElement` -Methode. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `CreateElement` -Methode. Legen Sie anschließend einen Wert für das Element fest, indem Sie dessen `SetAttribute` -Methode. Anhängen der `PDFsFromBookmarks` -Element durch Aufruf der `DDX` -Element `AppendChild` -Methode. Übergeben Sie die `PDFsFromBookmarks` element -Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` XmlElement PDFsFromBookmarks = ddx.CreateElement("PDFsFromBookmarks");  PDFsFromBookmarks.SetAttribute("prefix", "stmt");  root.AppendChild(PDFsFromBookmarks);`

   * Erstellen des DDX-Dokuments `PDF` -Element durch Aufruf der `XmlElement` -Objekt `CreateElement` -Methode. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `CreateElement` -Methode. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `SetAttribute` -Methode. Anhängen der `PDF` -Element zu `PDFsFromBookmarks` -Element durch Aufruf der `PDFsFromBookmarks` -Element `AppendChild` -Methode. Übergeben Sie die `PDF` element -Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` XmlElement PDF = ddx.CreateElement("PDF");  PDF.SetAttribute("source", "AssemblerResultPDF.pdf");  PDFsFromBookmarks.AppendChild(PDF);`

1. Konvertieren Sie das DDX-Dokument.

   * Erstellen Sie ein Objekt `System.IO.MemoryStream`, indem Sie den Konstruktor verwenden.
   * Füllen Sie die `MemoryStream` -Objekt mit dem DDX-Dokument durch Verwendung der `XmlElement` -Objekt, das das DDX-Dokument darstellt. Rufen Sie die `XmlElement` -Objekt `Save` -Methode und übergeben Sie die `MemoryStream` -Objekt.
   * Erstellen Sie ein Byte-Array und fügen Sie es mit den Daten im `MemoryStream` -Objekt. Der folgende Code zeigt diese Anwendungslogik:

      ` int bufLen = Convert.ToInt32(stream.Length);  byte[] byteArray = new byte[bufLen];  stream.Position = 0;  int count = stream.Read(byteArray, 0, bufLen);`

   * Erstellen Sie eine `BLOB` -Objekt. Weisen Sie das Byte-Array dem `BLOB` -Objekt `MTOM` -Feld.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Diese `BLOB` -Objekt wird an die `invokeOneDocument` als Argument.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort des Eingabedokuments und den PDF-Dateimodus darstellt, in dem die geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft den Inhalt des Byte-Arrays.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement einen Wert zuweisen, der zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` der `AssemblerOptionSpec` -Objekt `failOnError` Datenelement.

1. Lösen Sie das PDF-Dokument aus.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das dynamisch erstellte DDX-Dokument darstellt
   * Die `mapItem` Array, das das PDF-Eingabedokument enthält
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX` -Methode gibt eine `AssemblerResult` -Objekt, das die Ergebnisse des Auftrags sowie alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die neu erstellten PDF-Dokumente abzurufen:

   * Zugriff auf `AssemblerResult` -Objekt `documents` -Feld, das ein `Map` -Objekt, das die zerlegten PDF-Dokumente enthält.
   * Iteration durch die `Map` -Objekt, um jedes Zieldokument abzurufen. Dann die `value` zu `BLOB`.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf dessen `BLOB` -Objekt `MTOM` -Eigenschaft. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
