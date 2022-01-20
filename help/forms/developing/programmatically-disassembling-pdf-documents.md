---
title: Programmgesteuerte Demontage von PDF-Dokumenten
seo-title: Programmatically Disassembling PDF Documents
description: Verwenden Sie den Assembler-Dienst, um ein einzelnes PDF-Dokument mithilfe der Java-API und der Web Service-API in mehrere PDF-Dokumente aufzuteilen.
seo-description: Use the Assembler service to disassemble a single PDF document into multiple PDF documents using the Java API and the Web Service API.
uuid: d71cc044-e948-4b7a-b598-b041723b69e9
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 8e38a597-5d22-4d83-95fe-4494fb04e4a3
role: Developer
exl-id: 3f757392-96a0-4f20-91d0-7fbccb1bf171
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 3%

---

# Programmgesteuerte Demontage von PDF-Dokumenten {#programmatically-disassembling-pdf-documents}

Sie können ein PDF-Dokument aufteilen, indem Sie es an den Assembler-Dienst übergeben. In der Regel ist diese Aufgabe nützlich, wenn das PDF-Dokument ursprünglich aus vielen Einzeldokumenten erstellt wurde, z. B. aus einer Sammlung von Anweisungen. In der folgenden Abbildung ist DocA in mehrere Zieldokumente unterteilt, wobei das Lesezeichen der ersten Ebene auf einer Seite den Beginn eines neuen Zieldokuments angibt.

![pd_pd_pdfsfrombookmarks](assets/pd_pd_pdfsfrombookmarks.png)

Stellen Sie zum Aufteilen eines PDF-Dokuments sicher, dass die `PDFsFromBookmarks` -Element befindet sich im DDX-Dokument. Die `PDFsFromBookmarks` -Element ist ein resultierendes Element und kann nur ein untergeordnetes Element der `DDX` -Element. Es gibt keine `result` -Attribut, da dadurch mehrere Dokumente generiert werden können.

Die `PDFsFromBookmarks` -Element bewirkt, dass für jedes Lesezeichen der Stufe 1 im Quelldokument ein einzelnes Dokument generiert wird.

Angenommen, für diese Diskussion wird das folgende DDX-Dokument verwendet.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
      <PDFsFromBookmarks prefix="stmt"> 
     <PDF source="AssemblerResultPDF.pdf"/> 
 </PDFsFromBookmarks> 
 </DDX>
```

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mithilfe des Assembler-Dienstes vertraut machen. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).

>[!NOTE]
>
>Wenn Sie ein einzelnes PDF-Dokument an den Assembler-Dienst übergeben und ein einzelnes Dokument zurückerhalten, können Sie die `invokeOneDocument` Vorgang. Verwenden Sie jedoch zum Aufteilen eines PDF-Dokuments die `invokeDDX` -Vorgang, da zwar ein Eingabedokument an den Assembler-Dienst übergeben wird, der Assembler-Dienst jedoch ein Sammlungsobjekt zurückgibt, das ein oder mehrere PDF-Dokumente enthält.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie zum Aufteilen eines PDF-Dokuments die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.
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

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie adobe-utilities.jar und jbossall-client.jar durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Um ein PDF-Dokument aufzuteilen, muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss Folgendes enthalten: `PDFsFromBookmarks` -Element.

**Referenzieren eines zerlegbaren PDF-Dokuments**

Um ein PDF-Dokument zu zerlegen, verweisen Sie auf eine PDF-Datei, die das zu zerlegende PDF-Dokument darstellt. Wenn an den Assembler-Dienst übergeben wird, wird für jedes Lesezeichen der Stufe 1 im PDF ein separates Dokument zurückgegeben.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt.

**Aufteilen des PDF-Dokuments**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, auf das DDX-Dokument verweisen, auf ein zu zerlegendes PDF-Dokument verweisen und Laufzeitoptionen festlegen, können Sie ein PDF-Dokument auflösen, indem Sie die `invokeDDX` -Methode. Sofern das DDX-Dokument Anweisungen zum Aufteilen des PDF-Dokuments enthält, gibt der Assembler-Dienst disassemblierte PDF-Dokumente innerhalb eines Sammlungsobjekts zurück.

**Speichern Sie die zerlegten PDF-Dokumente**

Alle zerlegten PDF-Dokumente werden innerhalb eines Sammlungsobjekts zurückgegeben. Durchlaufen Sie das Sammlungsobjekt und speichern Sie jedes PDF-Dokument als PDF-Datei.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Aufteilen eines PDF-Dokuments mithilfe der Java-API {#disassemble-a-pdf-document-using-the-java-api}

Aufteilen eines PDF-Dokuments mithilfe der Assembler Service-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie eine `java.util.Map` -Objekt, das zum Speichern von Eingabe-PDF-Dokumenten mithilfe eines `HashMap` -Konstruktor.
   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort des PDF-Dokuments an die Disassemblierung übergeben.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt und übergeben Sie die `java.io.FileInputStream` -Objekt, das das zu zerlegende PDF-Dokument enthält.
   * Fügen Sie dem `java.util.Map` -Objekt durch Aufrufen seiner `put` -Methode verwenden und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * A `com.adobe.idp.Document` -Objekt, das das zu zerlegende PDF-Dokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `AssemblerOptionSpec` -Objekt `setFailOnError` -Methode und -übergabe `false`.

1. Lösen Sie das PDF-Dokument aus.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden erforderlichen Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das zu verwendende DDX-Dokument darstellt
   * A `java.util.Map` -Objekt, das das zu zerlegende PDF-Dokument enthält
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Auftragsprotokollebene

   Die `invokeDDX` -Methode gibt eine `com.adobe.livecycle.assembler.client.AssemblerResult` -Objekt, das die zerlegten PDF-Dokumente und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die zerlegten PDF-Dokumente abzurufen:

   * Rufen Sie die `AssemblerResult` -Objekt `getDocuments` -Methode. Dadurch wird eine `java.util.Map` -Objekt.
   * Iteration durch die `java.util.Map` -Objekt, bis Sie das Ergebnis finden `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Programmgesteuerte Demontage von PDF-Dokumenten](#programmatically-disassembling-pdf-documents)

[Schnellstart (SOAP-Modus): Aufheben eines PDF-Dokuments mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-disassembling-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Aufteilen eines PDF-Dokuments mithilfe der Webdienst-API {#disassemble-a-pdf-document-using-the-web-service-api}

Aufteilen eines PDF-Dokuments mithilfe der Assembler-Dienst-API (Webdienst):

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

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert für den Dateispeicherort des DDX-Dokuments und den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Referenzieren Sie ein zu zerlegendes PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Diese `BLOB` -Objekt wird an die `invokeOneDocument` als Argument.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des Eingabedokuments und den PDF-Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` den Inhalt des Byte-Arrays.
   * Erstellen Sie eine `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Kollektionsobjekt wird verwendet, um die zu zerlegende PDF zu speichern.
   * Erstellen Sie eine `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Weisen Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` -Feld. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
   * Zuweisen der `BLOB` -Objekt, das das PDF-Dokument im `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` -Feld.
   * Fügen Sie die `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` object&quot; `Add` -Methode und übergeben Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement einen Wert zuweisen, der zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` der `AssemblerOptionSpec` -Objekt `failOnError` -Feld.

1. Lösen Sie das PDF-Dokument aus.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt, das das PDF-Dokument disassembliert
   * Die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt, das das zu zerlegende PDF-Dokument enthält
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX` -Methode gibt eine `AssemblerResult` -Objekt, das die Auftragsergebnisse und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie die zerlegten PDF-Dokumente.

   Führen Sie die folgenden Schritte aus, um die neu erstellten PDF-Dokumente abzurufen:

   * Zugriff auf `AssemblerResult` -Objekt `documents` -Feld, das ein `Map` -Objekt, das die zerlegten PDF-Dokumente enthält.
   * Iteration durch die `Map` -Objekt, um jedes Zieldokument abzurufen. Dann die `value` zu `BLOB`.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf dessen `BLOB` -Objekt `MTOM` -Eigenschaft. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[Programmgesteuerte Demontage von PDF-Dokumenten](#programmatically-disassembling-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
