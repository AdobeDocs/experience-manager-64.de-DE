---
title: Assemblieren von PDF-Portfolios
seo-title: Assembling PDF Portfolios
description: Stellen Sie ein PDF-Portfolio zusammen, um verschiedene-Dokumente zu kombinieren, darunter Textdateien, Bilddateien und PDF-Dokumente. Sie können ein PDF-Portfolio mithilfe einer Java-API und einer Web Service-API zusammenstellen.
seo-description: Assemble a PDF portfolio to combine several documents of various types, including word file, image files, and PDF documents. You can assemble a PDF portfolio using a Java API and a Web Service API.
uuid: 1778c90b-9d26-466b-a7c7-401d737395e0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 023f0d9e-bfde-4879-a839-085fadffb48e
role: Developer
exl-id: 767d89bc-d243-46a1-a954-9977f4906566
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1814'
ht-degree: 3%

---

# Assemblieren von PDF-Portfolios {#assembling-pdf-portfolios}

Sie können ein PDF-Portfolio mit der Assembler-Java- und Webdienst-API zusammenstellen. Ein Portfolio kann mehrere Dokumente verschiedener Typen kombinieren, darunter Textdateien, Bilddateien (z. B. eine JPEG-Datei) und PDF-Dokumente. Das Layout des Portfolios kann auf verschiedene Stile wie die *Raster mit Vorschau*, die *Auf einem Bild* Layout oder gerade *Revolve*.

Die folgende Abbildung zeigt einen Screenshot eines Portfolios mit *Auf einem Bild* Stillayout.

![ap_ap_portfolio](assets/ap_ap_portfolio.png)

Das Erstellen eines PDF-Portfolios dient als papierlose Alternative zur Übergabe einer Dokumentensammlung. Mit AEM Forms können Sie Portfolios erstellen, indem Sie den Assembler-Dienst mit einem strukturierten DDX-Dokument aufrufen. Das folgende DDX-Dokument ist ein Beispiel für ein DDX-Dokument, das ein PDF-Portfolio erstellt.

```as3
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
     <PDF result="portfolio1.pdf"> 
         <Portfolio>   
             <Navigator source="myNavigator">   
                 <Resource name="navigator/image.xxx" source="myImage.png"/> 
             </Navigator> 
         </Portfolio> 
         <PackageFiles source="dog1"  > 
              <FieldData name="X">72</FieldData> 
             <FieldData name="Y">72</FieldData> 
             <File filename="saint_bernard.jpg" mimetype="image/jpeg"/> 
         </PackageFiles> 
         <PackageFiles source="dog2"  > 
             <FieldData name="X">120</FieldData> 
             <FieldData name="Y">216</FieldData> 
             <File filename="greyhound.pdf"/> 
         </PackageFiles>     
     </PDF> 
 </DDX>
```

Das DXX-Dokument muss eine `Portfolio` Tag mit verschachtelten `Navigator` -Tag. Beachten Sie das -Tag `<Resource name="navigator/image.xxx" source="myImage.png"/>` ist nur erforderlich, wenn `myNavigator` wird als onImage-Layout-Navigator zugewiesen: `AdobeOnImage.nav`. Mit diesem Tag kann der Assembler-Dienst das Bild auswählen, das als Portfoliohintergrund verwendet werden soll. Einschließen `PackageFiles` und `File` Tags zum Definieren des Dateinamens und MIME-Typs der gepackten Datei.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um ein PDF-Portfolio zu erstellen:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie die erforderlichen Dokumente.
1. Legen Sie Laufzeitoptionen fest.
1. Assemblieren des Portfolios.
1. Speichern Sie das assemblierte Portfolio.

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

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Portfolios muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss Folgendes enthalten: `Portfolio`, `Navigator` und `PackageFiles` -Elemente.

**Referenzieren der erforderlichen Dokumente**

Referenzieren Sie zum Zusammenführen eines PDF-Portfolios alle Dateien, die die zu assemblierenden Dokumente darstellen. Übergeben Sie beispielsweise alle im DDX-Dokument angegebenen Bilddateien an den Assembler-Dienst. Beachten Sie, dass diese Dateien im DDX-Dokument referenziert werden, das in diesem Abschnitt angegeben ist: *myImage.png* und *saint_bernard.jpg*.

Übergeben Sie beim Zusammenstellen eines PDF-Portfolios eine NAV-Datei (eine Navigatordatei) an den Assembler-Dienst. Die NAV-Datei, die Sie an den Assembler-Dienst übergeben, hängt davon ab, welcher PDF-Portfolio erstellt werden soll. Um beispielsweise eine *Auf einem Bild* übergeben Sie die Datei &quot;AdobeOnImage.nav&quot;. NAV-Dateien befinden sich im folgenden Ordner:

`<Install folder>\Acrobat 9.0\Acrobat\Navigators`

Kopieren Sie die NAV-Datei aus dem Installationsordner von Acrobat 9 (oder höher). Platzieren Sie die NAV-Datei an einem Speicherort, an dem Ihre Client-Anwendung darauf zugreifen kann. Alle Dateien werden in einem Map-Sammlungsobjekt an den Assembler-Dienst übergeben.

>[!NOTE]
>
>Die Schnellstarts, die mit Assembling-PDF-Portfolios verknüpft sind, verwenden AdobeOnImage.nav.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt.

**Assemblieren des Portfolios**

Um ein PDF-Portfolio zusammenzustellen, rufen Sie die `invokeDDX` Vorgang. Der Assembler-Dienst gibt das PDF-Portfolio in einem Sammlungsobjekt zurück.

**Speichern des assemblierten Portfolios**

Ein PDF-Portfolio wird innerhalb eines Sammlungsobjekts zurückgegeben. Durchlaufen Sie das Sammlungsobjekt und speichern Sie das PDF-Portfolio als PDF-Datei.

**Siehe auch**

[Assemblieren eines PDF-Portfolios mithilfe der Java-API](#assemble-a-pdf-portfolio-using-the-java-api)

[Assemblieren eines PDF-Portfolios mithilfe der Webdienst-API](#assemble-a-pdf-portfolio-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Assemblieren eines PDF-Portfolios mithilfe der Java-API {#assemble-a-pdf-portfolio-using-the-java-api}

Assemblieren eines PDF-Portfolios mithilfe der Assembler-Dienst-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie die erforderlichen Dokumente.

   * Erstellen Sie eine `java.util.Map` -Objekt, das zum Speichern von Eingabe-PDF-Dokumenten mithilfe eines `HashMap` -Konstruktor.
   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie den Speicherort der erforderlichen NAV-Datei (wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt und übergeben Sie die `java.io.FileInputStream` -Objekt, das die NAV-Datei enthält (wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
   * Fügen Sie dem `java.util.Map` -Objekt durch Aufrufen seiner `put` -Methode verwenden und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Quellelements übereinstimmen. (Wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).
      * A `com.adobe.idp.Document` -Objekt, das das PDF-Dokument enthält. (Wiederholen Sie diese Aufgabe für jede Datei, die zum Erstellen eines Portfolios erforderlich ist).

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `AssemblerOptionSpec` -Objekt `setFailOnError` -Methode und -übergabe `false`.

1. Assemblieren des Portfolios.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden erforderlichen Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das zu verwendende DDX-Dokument darstellt
   * A `java.util.Map` -Objekt, das die Dateien enthält, die zum Erstellen eines PDF-Portfolios erforderlich sind.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Auftragsprotokollebene

   Die `invokeDDX` -Methode gibt eine `com.adobe.livecycle.assembler.client.AssemblerResult` -Objekt, das das assemblierte PDF-Portfolio und alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das assemblierte Portfolio.

   Führen Sie die folgenden Schritte aus, um das PDF-Portfolio abzurufen:

   * Rufen Sie die `AssemblerResult` -Objekt `getDocuments` -Methode. Diese Methode gibt eine `java.util.Map` -Objekt.
   * Iteration durch die `java.util.Map` -Objekt, bis Sie das Ergebnis finden `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Portfolio zu extrahieren.

**Siehe auch**

[Schnellstart (SOAP-Modus): Assemblieren von PDF-Portfolios mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-portfolios-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblieren eines PDF-Portfolios mithilfe der Webdienst-API {#assemble-a-pdf-portfolio-using-the-web-service-api}

Assemblieren eines PDF-Portfolios mithilfe der Assembler-Dienst-API (Webdienst):

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
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Referenzieren Sie die erforderlichen Dokumente.

   * Erstellen Sie für jede Eingabedatei eine `BLOB` -Objekt durch Verwendung seines -Konstruktors. Die `BLOB` -Objekt wird zum Speichern der Eingabedatei verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort der Eingabedatei und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.
   * Erstellen Sie eine `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Kollektionsobjekt wird zum Speichern von Eingabedateien verwendet, die zum Erstellen eines PDF-Portfolios erforderlich sind.
   * Erstellen Sie für jede Eingabedatei eine `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Weisen Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` -Feld. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Elements übereinstimmen. (Führen Sie diese Aufgabe für jede Eingabedatei aus.)
   * Zuweisen der `BLOB` -Objekt, das die Eingabedatei im `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` -Feld. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)
   * Fügen Sie die `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt `Add` -Methode und übergeben Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. (Führen Sie diese Aufgabe für jedes PDF-Eingabedokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement einen Wert zuweisen, der zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` der `AssemblerOptionSpec` -Objekt `failOnError` Datenelement.

1. Assemblieren des Portfolios.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt
   * Die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt, das die erforderlichen Dateien enthält
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX` -Methode gibt eine `AssemblerResult` -Objekt, das die Ergebnisse des Auftrags sowie alle aufgetretenen Ausnahmen enthält.

1. Speichern Sie das assemblierte Portfolio.

   Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Portfolio abzurufen:

   * Zugriff auf `AssemblerResult` -Objekt `documents` -Feld, das ein `Map` -Objekt, das die resultierenden PDF-Dokumente enthält.
   * Iteration durch die `Map` -Objekt, um jedes Zieldokument abzurufen. Dann die `value` zu `BLOB`.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf dessen `BLOB` -Objekt `MTOM` -Eigenschaft. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine PDF-Datei schreiben können.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
