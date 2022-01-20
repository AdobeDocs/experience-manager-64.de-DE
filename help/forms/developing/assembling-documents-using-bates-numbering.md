---
title: Assemblieren von Dokumenten mit Bates-Nummerierung
seo-title: Assembling Documents Using Bates Numbering
description: 'Verwenden Sie die Bates-Nummerierung, um PDF-Dokumente mithilfe der Java- und Web Service-API zusammenzustellen. '
seo-description: Use Bates numbering to assemble PDF documents using the Java and Web Service API.
uuid: 28d5faeb-6915-41a2-b6a0-78d255df024f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 77e9b895-1313-4a5b-a2d5-cdb65bdc1966
role: Developer
exl-id: 902fc62b-262e-4eb4-b580-dbfbf4344fa6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1908'
ht-degree: 5%

---

# Assemblieren von Dokumenten mit Bates-Nummerierung {#assembling-documents-using-bates-numbering}

Mithilfe der Bates-Nummerierung können Sie PDF-Dokumente zusammenstellen, die eindeutige Seitenkennungen enthalten. *Bates-Nummerierung* ist eine Methode zur Anwendung von eindeutigen Identifikatoren auf einen Stapel verwandter Dokumente. Jede Seite im Dokument (oder in einer Gruppe von Dokumenten) erhält eine Bates-Nummer, mit der die Seite eindeutig identifiziert wird. Beispielsweise Produktionsdokumente, die Materialaufstellungsinformationen enthalten und der Herstellung einer Baugruppe zugeordnet sind, können einen Bezeichner enthalten. Eine Bates-Nummer enthält einen sequenziell erhöhten numerischen Wert sowie ein optionales Präfix und Suffix. Das Präfix + numerisch + Suffix wird als *Bates-Muster*.

Die folgende Illustration zeigt ein PDF-Dokument, das einen eindeutigen Bezeichner enthält, der sich in der Kopfzeile des Dokuments befindet.

![au_au_batesnumber](assets/au_au_batesnumber.png)

Für diese Diskussion wird die eindeutige Seitenkennung in der Kopfzeile eines Dokuments platziert. Angenommen, das folgende DDX-Dokument wird verwendet.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
        <PDF result="out.pdf"> 
        <Header> 
         <Center> 
             <StyledText> 
                 <p font-size="20pt"><BatesNumber/></p> 
             </StyledText> 
         </Center> 
     </Header> 
           <PDF source="map.pdf" /> 
          <PDF source="directions.pdf" /> 
          </PDF> 
 </DDX>
```

Dieses DDX-Dokument führt zwei PDF-Dokumente mit dem Namen *map.pdf* und* instructions.pdf* in einem einzigen PDF-Dokument. Das PDF-Zieldokument enthält eine Kopfzeile, die aus einer eindeutigen Seitenkennung besteht. Das Dokument in der obigen Abbildung zeigt beispielsweise 000016.

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden die Konzepte nicht erläutert, z. B. das Erstellen eines Kollektionsobjekts, das Eingabedokumente enthält, oder das Extrahieren der Ergebnisse aus dem zurückgegebenen Kollektionsobjekt. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument mit einer eindeutigen Seitenkennung (Bates-Nummerierung) zusammenzuführen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzeingabedokumente für PDF.
1. Legen Sie den Anfangswert der Bates-Nummer fest.
1. Stellen Sie die PDF-Eingabedokumente zusammen.
1. Extrahieren Sie die Ergebnisse.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Um ein PDF-Dokument mit eindeutigen Seitenkennungen zusammenzustellen, muss das DDX-Dokument die `BatesNumber` -Element.

**Referenzeingabe-PDF**

Eingabedokumente müssen referenziert werden, um ein PDF-PDF-Dokument zusammenzustellen. Beispielsweise müssen die Dokumente &quot;map.pdf&quot;und &quot;guides.pdf&quot;referenziert werden, um diese PDF-Dokumente in einem einzigen PDF-Dokument zusammenzuführen.

**Festlegen des anfänglichen Bates-Zahlenwerts**

Sie können den Anfangswert der Bates-Nummer festlegen, um Ihre Geschäftsanforderungen zu erfüllen. Angenommen, der Ausgangswert muss auf 000100 gesetzt werden. Wenn Sie den Anfangswert nicht festlegen, lautet der Wert der ersten Seite 00000.

**Zusammenführen der PDF-Eingabedokumente**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, verweisen Sie auf das DDX-Dokument, das `BatesNumber` -Elementinformationen, Referenzierung eines PDF-Eingabedokuments und Festlegen von Laufzeitoptionen können Sie die `invokeDDX` -Vorgang, der dazu führt, dass der Assembler-Dienst ein PDF-Dokument zusammenstellt, das eindeutige Seitenkennungen enthält.

**Ergebnisse extrahieren**

Der Assembler-Dienst gibt ein Collection-Objekt zurück, das die Auftragsergebnisse enthält. Sie können das PDF-Zieldokument und alle ausgelösten Ausnahmen extrahieren. In diesem Fall befindet sich ein verschlüsseltes PDF-Dokument im Sammlungsobjekt.

>[!NOTE]
>
>Ein Collection-Objekt wird zurückgegeben, wenn Sie die `invokeDDX` Vorgang. Dieser Vorgang wird verwendet, wenn zwei oder mehr PDF-Eingabedokumente an den Assembler-Dienst übergeben werden. Wenn Sie jedoch nur ein Eingabedokument an den Assembler-PDF-Dienst übergeben, sollten Sie die `invokeOneDocument` Vorgang. Informationen zur Verwendung dieses Vorgangs finden Sie unter [Assemblieren verschlüsselter PDF-Dokumente](/help/forms/developing/assembling-encrypted-pdf-documents.md).

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Assemblieren von Dokumenten mit Bates-Nummerierung mithilfe der Java-API {#assemble-documents-with-bates-numbering-using-the-java-api}

Stellen Sie mithilfe der Assembler-Dienst-API (Java) ein PDF-Dokument zusammen, das eindeutige Seitenkennungen (Bates-Nummerierung) verwendet:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzeingabedokumente für PDF.

   * Erstellen Sie eine `java.util.Map` -Objekt zum Speichern von Eingabe-PDF-Dokumenten mithilfe von `HashMap` -Konstruktor.
   * Erstellen Sie für jedes PDF-Eingabedokument eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort des PDF-Eingabedokuments übergeben. Übergeben Sie in diesem Fall den Speicherort eines ungesicherten PDF-Dokuments.
   * Erstellen Sie für jedes PDF-Eingabedokument eine `com.adobe.idp.Document` -Objekt und übergeben Sie die `java.io.FileInputStream` -Objekt, das das PDF-Dokument enthält.
   * Fügen Sie dem `java.util.Map` -Objekt durch Aufrufen seiner `put` -Methode verwenden und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. Beispielsweise lautet der Name der im DDX-Dokument angegebenen PDF-Quelldatei, der in diesen Abschnitt eingefügt wird, Loan.pdf.
      * A `com.adobe.idp.Document` -Objekt, das das ungesicherte PDF-Dokument enthält.

1. Legen Sie den Anfangswert der Bates-Nummer fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie die Anfangszahl der Bates fest, indem Sie die `AssemblerOptionSpec` -Objekt `setFirstBatesNumber` und übergeben einen numerischen Wert, der den Anfangswert angibt.

1. Stellen Sie die PDF-Eingabedokumente zusammen.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden erforderlichen Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das DDX-Dokument darstellt.
   * A `java.util.Map` -Objekt, das die ungesicherte Eingabedatei enthält.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der standardmäßigen Schrift- und Auftragsprotokollebene.

   Die `invokeDDX` -Methode gibt eine `com.adobe.livecycle.assembler.client.AssemblerResult` -Objekt, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Extrahieren Sie die Ergebnisse.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Rufen Sie die `AssemblerResult` -Objekt `getDocuments` -Methode. Diese Aktion gibt eine `java.util.Map` -Objekt.
   * Iteration durch die `java.util.Map` -Objekt, bis Sie die `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument zu extrahieren.

**Siehe auch**

[Schnellstart (SOAP-Modus): Assemblieren eines PDF-Dokuments mit Bates-Nummerierung mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-with-bates-numbering-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblieren von Dokumenten mit Bates-Nummerierung mithilfe der Webdienst-API {#assemble-documents-with-bates-numbering-using-the-web-service-api}

Stellen Sie mithilfe der Assembler-Dienst-API (Webdienst) ein PDF-Dokument zusammen, das eindeutige Seitenkennungen (Bates-Nummerierung) verwendet:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

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
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Referenzeingabedokumente für PDF.

   * Erstellen Sie für jedes PDF-Eingabedokument eine `BLOB` -Objekt durch Verwendung seines -Konstruktors. Die `BLOB` -Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort des Eingabedokuments und den PDF-Dateimodus darstellt, in dem die geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.
   * Erstellen Sie eine `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Sammlungsobjekt wird zum Speichern der PDF-Eingabedokumente verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument eine `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt. Wenn beispielsweise zwei PDF-Eingabedokumente verwendet werden, erstellen Sie zwei `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekte.
   * Weisen Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` -Feld. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Zuweisen der `BLOB` -Objekt, das das PDF-Dokument im `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` -Feld. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Fügen Sie die `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt `Add` -Methode und übergeben Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie den Anfangswert der Bates-Nummer fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie die Anfangszahl der Bates fest, indem Sie dem `firstBatesNumber` Datenelement, das zu der `AssemblerOptionSpec` -Objekt.

1. Stellen Sie die PDF-Eingabedokumente zusammen.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invoke` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt.
   * Die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt, das die PDF-Eingabedokumente enthält. Die Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und ihre Werte müssen die `BLOB` -Objekte, die diesen Dateien entsprechen.
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt.

   Die `invoke` -Methode gibt eine `AssemblerResult` -Objekt, das die Ergebnisse des Auftrags sowie alle aufgetretenen Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Zugriff auf `AssemblerResult` -Objekt `documents` -Feld, das ein `Map` -Objekt, das die PDF-Ergebnisdokumente enthält.
   * Iteration durch die `Map` -Objekt ein, bis Sie den Schlüssel finden, der dem Namen des Zieldokuments entspricht. Dann die `value` zu `BLOB`.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf dessen `BLOB` -Objekt `MTOM` -Eigenschaft. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
