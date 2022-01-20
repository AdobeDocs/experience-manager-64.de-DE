---
title: Programmgesteuertes Zusammenstellen von PDF-Dokumenten
seo-title: Programmatically Assembling PDF Documents
description: Verwenden Sie die Assembler-Dienst-API, um mithilfe der Java-API und der Web Service-API mehrere PDF-Dokumente in einem PDF-Dokument zusammenzuführen.
seo-description: Use the Assembler service API to assemble multiple PDF documents into a single PDF document using the Java API and the Web Service API.
uuid: aa3f8f39-1fbc-48d0-82ff-6caaadf125fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: ebe8136b-2a79-4035-b9d5-aa70a5bbd4af
role: Developer
exl-id: be09271b-3004-4866-b43b-fb03c91305ec
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2110'
ht-degree: 2%

---

# Programmgesteuertes Zusammenstellen von PDF-Dokumenten {#programmatically-assembling-pdf-documents}

Sie können die Assembler-Dienst-API verwenden, um mehrere PDF-Dokumente in einem PDF-Dokument zusammenzuführen. Die folgende Abbildung zeigt, wie drei PDF-Dokumente in einem einzigen PDF-Dokument zusammengeführt werden.

![pa_pa_document_assembly](assets/pa_pa_document_assembly.png)

Zum Zusammenführen von zwei oder mehr PDF-Dokumenten in einem PDF-Dokument benötigen Sie ein DDX-Dokument. Ein DDX-Dokument beschreibt das PDF-Dokument, das der Assembler-Dienst erzeugt. Das heißt, das DDX-Dokument weist den Assembler-Dienst an, welche Aktionen ausgeführt werden sollen.

Angenommen, für diese Diskussion wird das folgende DDX-Dokument verwendet.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
     <PDF result="out.pdf"> 
         <PDF source="map.pdf" /> 
         <PDF source="directions.pdf" /> 
     </PDF> 
 </DDX>
```

Dieses DDX-Dokument führt zwei PDF-Dokumente mit dem Namen *map.pdf* und *instructions.pdf* in einem einzigen PDF-Dokument.

>[!NOTE]
>
>Informationen zum Anzeigen eines DDX-Dokuments, das ein PDF-Dokument zerlegt, finden Sie unter [Programmgesteuerte Demontage von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents).

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Überlegungen beim Aufrufen des Assembler-Dienstes mithilfe von Webdiensten {#considerations-when-invoking-assembler-service-using-web-services}

Wenn Sie beim Zusammenstellen großer Dokumente Kopf- und Fußzeilen hinzufügen, wird möglicherweise ein `OutOfMemory` -Fehler und die Dateien werden nicht zusammengestellt. Fügen Sie eine `DDXProcessorSetting` -Element zu Ihrem DDX-Dokument hinzufügen, wie im folgenden Beispiel gezeigt.

`<DDXProcessorSetting name="checkpoint" value="2000" />`

Sie können dieses Element als untergeordnetes Element der `DDX` -Element oder als untergeordnetes Element eines `PDF result` -Element. Der Standardwert für diese Einstellung ist 0 (null), wodurch der Checkpoint deaktiviert wird und sich das DDX so verhält, als ob sich die `DDXProcessorSetting` -Element nicht vorhanden ist. Wenn bei Ihnen ein `OutOfMemory` -Fehler verwenden, müssen Sie den Wert möglicherweise auf eine Ganzzahl festlegen, in der Regel zwischen 500 und 5000. Ein kleiner Checkpoint-Wert führt zu einem häufigeren Checkpoint.

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein einzelnes PDF-Dokument aus mehreren PDF-Dokumenten zusammenzuführen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzeingabedokumente für PDF.
1. Legen Sie Laufzeitoptionen fest.
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

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Dieses DDX-Dokument weist den Assembler-Dienst an, zwei PDF-Dokumente in einem PDF-Dokument zusammenzuführen.

**Referenzeingabe-PDF**

Referenzieren Sie PDF-Eingabedokumente, die Sie an den Assembler-Dienst übergeben möchten. Wenn Sie beispielsweise zwei Eingabedokumente mit dem Namen PDF übergeben möchten, müssen Sie die entsprechenden PDF--Dateien übergeben.

Sowohl die Datei &quot;map.pdf&quot;als auch die Datei &quot;richtung.pdf&quot;müssen in einem Kollektionsobjekt platziert werden. Der Name des Schlüssels muss mit dem Wert des PDF-Quellattributs im DDX-Dokument übereinstimmen. Es spielt keine Rolle, wie der Name der PDF-Datei lautet, wenn der Schlüssel und das Quellattribut im DDX-Dokument übereinstimmen.

>[!NOTE]
>
>Ein `*AssemblerResult*` -Objekt, das ein Collection-Objekt enthält, wird zurückgegeben, wenn Sie die `*invokeDDX*` Vorgang. Dieser Vorgang wird verwendet, wenn Sie zwei oder mehr PDF-Eingabedokumente an den Assembler-Dienst übergeben. Wenn Sie jedoch nur eine Eingabe-PDF an den Assembler-Dienst übergeben und nur ein Rückgabedokument erwarten, rufen Sie die `*invokeOneDocument*` Vorgang. Beim Aufrufen dieses Vorgangs wird ein einzelnes Dokument zurückgegeben. Informationen zur Verwendung dieses Vorgangs finden Sie unter [Assemblieren verschlüsselter PDF-Dokumente](/help/forms/developing/assembling-encrypted-pdf-documents.md#assembling-encrypted-pdf-documents).

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie unter `AssemblerOptionSpec` Klassenreferenz in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Zusammenführen der PDF-Eingabedokumente**

Nachdem Sie den Service-Client erstellt haben, auf eine DDX-Datei verweisen, ein Sammlungsobjekt erstellen, das Eingabedokumente speichert, und Laufzeitoptionen festlegen, können Sie den DDX-Vorgang aufrufen. Bei Verwendung des in diesem Abschnitt angegebenen DDX-Dokuments werden die Dateien &quot;map.pdf&quot;und &quot;direction.pdf&quot;zu einem PDF-Dokument zusammengeführt.

**Ergebnisse extrahieren**

Der Assembler-Dienst gibt einen `java.util.Map` -Objekt, das vom `AssemblerResult` -Objekt, das Vorgangsergebnisse enthält. Die zurückgegebene `java.util.Map` -Objekt enthält die resultierenden Dokumente und alle Ausnahmen.

Die folgende Tabelle fasst einige der Schlüsselwerte und Objekttypen zusammen, die in der zurückgegebenen `java.util.Map` -Objekt.

<table> 
 <thead> 
  <tr> 
   <th><p>Schlüsselwert</p></th> 
   <th><p>Objekttyp</p></th> 
   <th><p>Beschreibung</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p><code><i>documentName</i></code></p></td> 
   <td><p><code>com.adobe.idp.Document</code></p></td> 
   <td><p>Enthält die Zieldokumente, die in einem DDX-Ergebniselement angegeben sind</p></td> 
  </tr> 
  <tr> 
   <td><p><code><i>documentName</i></code></p></td> 
   <td><p><code>Exception</code></p></td> 
   <td><p>Enthält eine Ausnahme für das Dokument</p></td> 
  </tr> 
  <tr> 
   <td><p><code>OutputMapConstants.LOG_NAME</code></p></td> 
   <td><p><code>com.adobe.idp.Documen</code></p></td> 
   <td><p>Enthält das Auftragsprotokoll</p></td> 
  </tr> 
 </tbody> 
</table>

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuerte Demontage von PDF-Dokumenten](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## Zusammenführen von PDF-Dokumenten mit der Java-API {#assemble-pdf-documents-using-the-java-api}

Assemblieren eines PDF-Dokuments mithilfe der Assembler-Dienst-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzeingabedokumente für PDF.

   * Erstellen Sie eine `java.util.Map` -Objekt, das zum Speichern von Eingabe-PDF-Dokumenten mithilfe eines `HashMap` -Konstruktor.
   * Erstellen Sie für jedes PDF-Eingabedokument eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort des PDF-Eingabedokuments übergeben.
   * Erstellen Sie für jedes PDF-Eingabedokument eine `com.adobe.idp.Document` -Objekt und übergeben Sie die `java.io.FileInputStream` -Objekt, das das PDF-Dokument enthält.
   * Fügen Sie für jedes Eingabedokument einen Eintrag zum `java.util.Map` -Objekt durch Aufrufen seiner `put` -Methode verwenden und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen.
      * A `com.adobe.idp.Document` -Objekt (oder `java.util.List` -Objekt, das mehrere PDF-Dokumente angibt), das das Quelldokument enthält.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `AssemblerOptionSpec` -Objekt `setFailOnError` -Methode und -übergabe `false`.

1. Stellen Sie die PDF-Eingabedokumente zusammen.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden erforderlichen Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das zu verwendende DDX-Dokument darstellt
   * A `java.util.Map` -Objekt, das die zu assemblierenden PDF-Eingabedateien enthält
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich standardmäßiger Schrift- und Auftragsprotokollebene

   Die `invokeDDX` -Methode gibt eine `com.adobe.livecycle.assembler.client.AssemblerResult` -Objekt, das die Ergebnisse des Auftrags sowie alle aufgetretenen Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Rufen Sie die `AssemblerResult` -Objekt `getDocuments` -Methode. Dadurch wird eine `java.util.Map` -Objekt.
   * Iteration durch die `java.util.Map` -Objekt, bis Sie das Ergebnis finden `com.adobe.idp.Document` -Objekt. (Sie können das im DDX-Dokument angegebene PDF-Ergebniselement verwenden, um das Dokument abzurufen.)
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument zu extrahieren.

   >[!NOTE]
   >
   >Wenn `*LOG_LEVEL*` festgelegt wurde, um ein Protokoll zu erstellen, können Sie das Protokoll mithilfe der `*AssemblerResult*` -Objekt `*getJobLog*` -Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Assemblieren eines PDF-Dokuments mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Zusammenführen von PDF-Dokumenten mithilfe der Webdienst-API {#assemble-pdf-documents-using-the-web-service-api}

Zusammenführen von PDF-Dokumenten mithilfe der Assembler-Dienst-API (Webdienst):

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
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Referenzeingabedokumente für PDF.

   * Erstellen Sie für jedes PDF-Eingabedokument eine `BLOB` -Objekt durch Verwendung seines -Konstruktors. Die `BLOB` -Objekt wird zum Speichern des PDF-Eingabedokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des Eingabedokuments und den PDF-Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.
   * Erstellen Sie eine `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Sammlungsobjekt wird zum Speichern von PDF-Eingabedokumenten verwendet.
   * Erstellen Sie für jedes PDF-Eingabedokument eine `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt. Wenn beispielsweise zwei PDF-Eingabedokumente verwendet werden, erstellen Sie zwei `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekte.
   * Weisen Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` -Feld. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen PDF-Quellelements übereinstimmen. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Zuweisen der `BLOB` -Objekt, das das PDF-Dokument im `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` -Feld. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Fügen Sie die `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt `Add` -Methode und übergeben Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement einen Wert zuweisen, der zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` der `AssemblerOptionSpec` -Objekt `failOnError` Datenelement.

1. Stellen Sie die PDF-Eingabedokumente zusammen.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invoke` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt.
   * Die `mapItem` -Array, das die PDF-Eingabedokumente enthält. Die Schlüssel müssen mit den Namen der PDF-Quelldateien übereinstimmen, und ihre Werte müssen die `BLOB` Objekte, die diesen Dateien entsprechen.
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt.

   Die `invoke` -Methode gibt eine `AssemblerResult` -Objekt, das die Ergebnisse des Auftrags und eventuell aufgetretene Ausnahmen enthält.

1. Extrahieren Sie die Ergebnisse.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Zugriff auf `AssemblerResult` -Objekt `documents` -Feld, das ein `Map` -Objekt, das die PDF-Ergebnisdokumente enthält.
   * Iteration durch die `Map` -Objekt ein, bis Sie den Schlüssel finden, der dem Namen des Zieldokuments entspricht. Dann die `value` zu `BLOB`.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf dessen `BLOB` -Objekt `MTOM` -Eigenschaft. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

   >[!NOTE]
   >
   >Wenn `LOG_LEVEL` festgelegt wurde, um ein Protokoll zu erstellen, können Sie das Protokoll extrahieren, indem Sie den Wert der `AssemblerResult` -Objekt `jobLog` Datenelement.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
