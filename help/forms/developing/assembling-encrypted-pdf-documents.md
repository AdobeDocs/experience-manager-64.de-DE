---
title: Assemblieren verschlüsselter PDF-Dokumente
seo-title: Assembling Encrypted PDF Documents
description: Stellen Sie mithilfe der Java-API und der Web Service-API verschlüsselte PDF-Dokumente zusammen.
seo-description: Assemble encrypted PDF documents using the Java API and Web Service API.
uuid: d0948ec9-ab67-4fe4-9062-1c4938460b43
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 6d75c7b1-9c0e-47f3-bdb1-61acf16b97f9
role: Developer
exl-id: fa543e13-f920-4b77-9762-36f115261e8c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1645'
ht-degree: 6%

---

# Assemblieren verschlüsselter PDF-Dokumente {#assembling-encrypted-pdf-documents}

Sie können ein PDF-Dokument mit einem Kennwort verschlüsseln, indem Sie den Assembler-Dienst verwenden. Nachdem ein PDF-Dokument mit einem Kennwort verschlüsselt wurde, muss ein Benutzer das Kennwort angeben, damit das Dokument in Adobe Reader oder Acrobat angezeigt werden kann. Zum Verschlüsseln eines PDF-Dokuments mit einem Kennwort muss das DDX-Dokument encryption-Elementwerte enthalten, die für die Verschlüsselung eines PDF-Dokuments erforderlich sind.

Angenommen, für diese Diskussion wird das folgende DDX-Dokument verwendet.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
        <PDF result="EncryptLoan.pdf" encryption="userProtect"> 
         <PDF source="inDoc" /> 
     </PDF> 
     <PasswordEncryptionProfile name="userProtect" compatibilityLevel="Acrobat7"> 
         <OpenPassword>AdobeOpen</OpenPassword> 
        </PasswordEncryptionProfile> 
 </DDX>
```

Beachten Sie in diesem DDX-Dokument, dass dem Quellattribut der Wert zugewiesen ist. `inDoc`. In Fällen, in denen nur ein Eingabedokument an den Assembler-Dienst übergeben und ein PDF-PDF-Dokument zurückgegeben wird, rufen Sie die `invokeOneDocument` -Vorgang, Wert zuweisen `inDoc` zum PDF-Quellattribut. Beim Aufrufen der `invokeOneDocument` den `inDoc` value ist ein vordefinierter Schlüssel, der im DDX-Dokument angegeben werden muss.

Wenn Sie dagegen zwei oder mehr Eingabedokumente an den Assembler-PDF-Dienst übergeben, können Sie die `invokeDDX` Vorgang. Weisen Sie in diesem Fall den Dateinamen des PDF-Eingabedokuments dem `source` -Attribut.

Der Encryption-Dienst muss nicht Teil Ihrer AEM Forms-Installation sein, um ein PDF-Dokument mit einem Kennwort zu verschlüsseln. Siehe [Verschlüsseln und Entschlüsseln von PDF-Dokumenten](/help/forms/developing/encrypting-decrypting-pdf-documents.md).

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um ein verschlüsseltes PDF-Dokument zusammenzustellen:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie ein unsicheres PDF-Dokument.
1. Legen Sie Laufzeitoptionen fest.
1. Verschlüsseln Sie das Dokument.
1. Speichern Sie das verschlüsselte PDF-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Assembler-Clients**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Zum Zusammenführen eines PDF-Dokuments muss auf ein DDX-Dokument verwiesen werden. Betrachten Sie beispielsweise das DDX-Dokument, das in diesem Abschnitt eingeführt wurde. Zum Verschlüsseln eines PDF-Dokuments muss das DDX-Dokument die `PasswordEncryptionProfile` -Element.

**Unsicheres PDF-Dokument referenzieren**

Ein nicht gesichertes PDF-Dokument muss referenziert und an den Assembler-Dienst übergeben werden, um es zu verschlüsseln. Wenn Sie auf ein bereits verschlüsseltes PDF-Dokument verweisen, wird eine Ausnahme ausgelöst.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie unter `AssemblerOptionSpec` Klassenreferenz in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Dokument verschlüsseln**

Nachdem Sie den Assembler-Dienst-Client erstellt haben, verweisen Sie auf das DDX-Dokument, das Verschlüsselungsinformationen enthält, auf ein ungesichertes PDF-Dokument verweisen und Laufzeitoptionen festlegen, können Sie die `invokeOneDocument` Vorgang. Da nur ein Eingabedokument an den Assembler-Dienst übergeben wird (und ein PDF zurückgegeben wird), können Sie die `invokeOneDocument` -Vorgang anstelle der `invokeDDX` Vorgang.

**Speichern Sie das verschlüsselte PDF-Dokument**

Wenn nur ein einzelnes PDF-Dokument an den Assembler-Dienst übergeben wird, gibt der Assembler-Dienst anstelle eines Collection-Objekts ein einzelnes Dokument zurück. Das heißt, beim Aufrufen der `invokeOneDocument` -Vorgang, wird ein einzelnes Dokument zurückgegeben. Da das in diesem Abschnitt referenzierte DDX-Dokument Verschlüsselungsinformationen enthält, gibt der Assembler-Dienst ein PDF-Dokument zurück, das mit einem Kennwort verschlüsselt ist.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Zusammenführen eines verschlüsselten PDF-Dokuments mithilfe der Java-API {#assemble-an-encrypted-pdf-document-using-the-java-api}

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie ein unsicheres PDF-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und den Speicherort eines ungesicherten PDF-Dokuments übergeben.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt und übergeben Sie die `java.io.FileInputStream` -Objekt, das das PDF-Dokument enthält. Diese `com.adobe.idp.Document` -Objekt wird an die `invokeOneDocument` -Methode.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `AssemblerOptionSpec` -Objekt `setFailOnError` -Methode und -übergabe `false`.

1. Verschlüsseln Sie das Dokument.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeOneDocument` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das DDX-Dokument darstellt. Stellen Sie sicher, dass dieses DDX-Dokument den Wert enthält. `inDoc` für das PDF-Quellelement.
   * A `com.adobe.idp.Document` -Objekt, das das ungesicherte PDF-Dokument enthält.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der standardmäßigen Schrift- und Auftragsprotokollebene.

   Die `invokeOneDocument` -Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt in die Datei ein. Stellen Sie sicher, dass Sie die `Document` -Objekt, das `invokeOneDocument` -Methode zurückgegeben.

**Siehe auch**

[Schnellstart (SOAP-Modus): Assemblieren eines verschlüsselten PDF-Dokuments mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-an-encrypted-pdf-document-using-the-java-api)

## Zusammenführen eines verschlüsselten PDF-Dokuments mithilfe der Webdienst-API {#assemble-an-encrypted-pdf-document-using-the-web-service-api}

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

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
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Referenzieren Sie ein unsicheres PDF-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des PDF-Eingabedokuments verwendet. Diese `BLOB` -Objekt wird an die `invokeOneDocument` als Argument.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des Eingabedokuments und den PDF-Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement einen Wert zuweisen, der zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` der `AssemblerOptionSpec` -Objekt `failOnError` Datenelement.

1. Verschlüsseln Sie das Dokument.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeOneDocument` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt
   * A `BLOB` -Objekt, das das ungesicherte PDF-Dokument darstellt
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeOneDocument` -Methode gibt eine `BLOB` -Objekt, das ein verschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den zu öffnenden Dateimodus darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt, das `invokeOneDocument` -Methode zurückgegeben. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
