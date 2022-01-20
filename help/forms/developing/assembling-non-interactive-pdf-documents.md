---
title: Assemblieren nicht interaktiver PDF-Dokumente
seo-title: Assembling Non-Interactive PDF Documents
description: Verwenden Sie ein nicht interaktives PDF-Formular als Eingabe, um ein nicht interaktives PDF-Dokument mithilfe der Java-API und der Web Service-API zusammenzustellen.
seo-description: Use a non-interactive PDF form as input to assemble a non-interactive PDF document using the Java API and Web Service API.
uuid: 0c7adeb4-9a3a-4ec5-ba33-c3642928d4ea
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 8a75c201-bd88-4809-be08-69de94656489
role: Developer
exl-id: d4e40d68-781d-4fc8-8557-bf36462ca1d9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1775'
ht-degree: 2%

---

# Assemblieren nicht interaktiver PDF-Dokumente {#assembling-non-interactive-pdf-documents}

Sie können ein nicht interaktives PDF-Dokument zusammenstellen, wenn Sie ein interaktives PDF-Formular als Eingabe verwenden. Angenommen, Sie verfügen über ein Formular, mit dem Benutzer Daten in die Felder eingeben können. Sie können dieses Formular an den Assembler-Dienst übergeben, was dazu führt, dass der Assembler-Dienst ein PDF-Dokument zurückgibt, das die Eingabe von Daten durch Benutzer verhindert. Dieses Dokument ist ein nicht interaktives PDF-Formular. Die folgende Abbildung zeigt beispielsweise einen Hypothekenantrag, der ein interaktives Formular darstellt.

Angenommen, für diese Diskussion wird das folgende DDX-Dokument verwendet.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
      <PDF result="out.pdf"> 
        <PDF source="inDoc"/> 
        <NoXFA/> 
      </PDF> 
 </DDX>
```

Beachten Sie in diesem DDX-Dokument, dass dem Quellattribut der Wert zugewiesen ist. `inDoc`. In Fällen, in denen nur ein Eingabedokument an den Assembler-Dienst übergeben und ein PDF-PDF-Dokument zurückgegeben wird, rufen Sie die `invokeOneDocument` -Vorgang, Wert zuweisen `inDoc` zum PDF-Quellattribut. Beim Aufrufen der `invokeOneDocument` den `inDoc` value ist ein vordefinierter Schlüssel, der im DDX-Dokument angegeben werden muss.

Wenn Sie dagegen zwei oder mehr Eingabedokumente an den Assembler-PDF-Dienst übergeben, können Sie die `invokeDDX` Vorgang. Weisen Sie in diesem Fall den Dateinamen des PDF-Eingabedokuments dem `source` -Attribut.

Dieses DDX-Dokument enthält die `NoXFA` -Element, das den Assembler-Dienst anweist, ein nicht interaktives PDF-Dokument zurückzugeben.

Der Assembler-Dienst kann nicht interaktive PDF-Dokumente zusammenstellen, ohne dass der Output-Dienst Teil Ihrer AEM Forms-Installation ist, wenn das Eingabedokument auf einem Acrobat-Formular oder einem statischen XFA-Formular basiert. Wenn das Eingabedokument jedoch ein dynamisches XFA-PDF-Formular ist, muss der Output-Dienst Teil Ihrer AEM Forms-Installation sein. Wenn der Output-Dienst nicht Teil Ihrer AEM Forms-Installation ist, wenn ein dynamisches XFA-Formular assembliert wird, wird eine Ausnahme ausgelöst. Siehe [Erstellen von Document Output Streams](/help/forms/developing/creating-document-output-streams.md).

>[!NOTE]
>
>Bevor Sie diesen Abschnitt lesen, sollten Sie sich mit dem Zusammenstellen von PDF-Dokumenten mit dem Assembler-Dienst vertraut machen. In diesem Abschnitt werden keine Konzepte besprochen, wie das Erstellen eines Kollektionsobjekts mit Eingabedokumenten oder das Extrahieren der Ergebnisse aus dem zurückgegebenen Kollektionsobjekt. (Siehe [Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md).

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie zum Zusammenführen eines nicht interaktiven PDF-Dokuments die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein interaktives PDF-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Stellen Sie das PDF-Dokument zusammen.
1. Speichern Sie das nicht interaktive PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss Folgendes enthalten: `NoXFA` -Element, das den Assembler-Dienst anweist, ein nicht interaktives PDF-Dokument zurückzugeben.

**Referenzieren eines interaktiven PDF-Dokuments**

Ein interaktives PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um ein nicht interaktives PDF-Dokument wiederherzustellen.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt.

**Zusammenführen des PDF-Dokuments**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, auf das DDX-Dokument verweisen, auf ein interaktives PDF-Dokument verweisen und Laufzeitoptionen festlegen, können Sie die `invokeOneDocument` Vorgang. Da nur ein Eingabedokument an den Assembler-Dienst übergeben und ein einziges PDF zurückgegeben wird, können Sie die `invokeOneDocument` im Gegensatz zum `invokeDDX` Vorgang.

**Speichern Sie das nicht interaktive PDF-Dokument**

Wenn nur ein einzelnes PDF-Dokument an den Assembler-Dienst übergeben wird, gibt der Assembler-Dienst anstelle eines Collection-Objekts ein einzelnes Dokument zurück. Das heißt, beim Aufrufen der `invokeOneDocument` -Vorgang, wird ein einzelnes Dokument zurückgegeben. Da das in diesem Abschnitt referenzierte DDX-Dokument Anweisungen zum Erstellen eines nicht interaktiven PDF-Dokuments enthält, gibt der Assembler-Dienst ein nicht interaktives PDF-Dokument zurück, das als PDF-Datei gespeichert werden kann.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenführen eines nicht interaktiven PDF-Dokuments mithilfe der Java-API {#assemble-a-non-interactive-pdf-document-using-the-java-api}

Assemblieren eines nicht interaktiven PDF-Dokuments mithilfe der Assembler-Dienst-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein interaktives PDF-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort eines interaktiven PDF-Dokuments übergeben.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt und übergeben Sie die `java.io.FileInputStream` -Objekt, das das PDF-Dokument enthält. Diese `com.adobe.idp.Document` -Objekt wird an die `invokeOneDocument` -Methode.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `AssemblerOptionSpec` -Objekt `setFailOnError` -Methode und -übergabe `false`.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeOneDocument` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das DDX-Dokument darstellt. Stellen Sie sicher, dass dieses DDX-Dokument den Wert enthält. `inDoc` für das PDF-Quellelement.
   * A `com.adobe.idp.Document` -Objekt, das das interaktive PDF-Dokument enthält.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der standardmäßigen Schrift- und Auftragsprotokollebene.

   Die `invokeOneDocument` -Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt in die Datei ein. Stellen Sie sicher, dass Sie die `Document` -Objekt, das `invokeOneDocument` -Methode zurückgegeben.

* &quot;Schnellstart (SOAP-Modus): Assemblieren eines nicht interaktiven PDF-Dokuments mit der Java-API&quot;

## Zusammenführen eines nicht interaktiven PDF-Dokuments mithilfe der Webdienst-API {#assemble-a-non-interactive-pdf-document-using-the-web-service-api}

Assemblieren eines nicht interaktiven PDF-Dokuments mithilfe der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Assembler-Client.

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

1. Referenzieren Sie ein interaktives PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Diese `BLOB` -Objekt wird an die `invokeOneDocument` als Argument.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des Eingabedokuments und den PDF-Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement einen Wert zuweisen, der zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` der `AssemblerOptionSpec` -Objekt `failOnError` Datenelement.

1. Stellen Sie das PDF-Dokument zusammen.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeOneDocument` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt
   * A `BLOB` -Objekt, das das interaktive PDF-Dokument darstellt
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeOneDocument` -Methode gibt eine `BLOB` -Objekt, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des nicht interaktiven PDF-Dokuments und den zu öffnenden Dateimodus darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt, das `invokeOneDocument` -Methode zurückgegeben. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

* &quot;Schnellstart (MTOM): Assemblieren eines nicht interaktiven PDF-Dokuments mithilfe der Webdienst-API&quot;.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
