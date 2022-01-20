---
title: Validieren von DDX-Dokumenten
seo-title: Validating DDX Documents
description: Validieren Sie ein DDX-Dokument programmgesteuert mithilfe der Java-API und der Web Service-API.
seo-description: Validate a DDX document programmatically using the Java API and the Web Service API.
uuid: da668170-d2e9-4fff-aef5-432a856bd0bd
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 693859b0-a0c3-43f1-95c0-be48a90d7d8d
role: Developer
exl-id: 5be91b23-355b-4e50-b1f5-afed248bc8b5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1512'
ht-degree: 3%

---

# Validieren von DDX-Dokumenten {#validating-ddx-documents}

Sie können ein DDX-Dokument programmgesteuert validieren, das vom Assembler-Dienst verwendet wird. Mit der Assembler-Dienst-API können Sie also feststellen, ob ein DDX-Dokument gültig ist. Wenn Sie beispielsweise von einer früheren AEM Forms-Version aktualisiert haben und sicherstellen möchten, dass Ihr DDX-Dokument gültig ist, können Sie es mithilfe der Assembler-Dienst-API überprüfen.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein DDX-Dokument zu validieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.
1. Führen Sie die Überprüfung durch.
1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem anderen unterstützten J2EE-Anwendungsserver als JBoss bereitgestellt wird, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die für den J2EE-Anwendungsserver spezifisch sind, auf dem AEM Forms bereitgestellt wird.

**PDF Assembler-Client erstellen**

Bevor Sie einen Assembler-Vorgang programmgesteuert ausführen können, müssen Sie einen Assembler-Dienst-Client erstellen.

**Vorhandenes DDX-Dokument referenzieren**

Um ein DDX-Dokument zu validieren, müssen Sie auf ein vorhandenes DDX-Dokument verweisen.

**Festlegen von Laufzeitoptionen zum Überprüfen des DDX-Dokuments**

Beim Validieren eines DDX-Dokuments müssen Sie bestimmte Laufzeitoptionen festlegen, die den Assembler-Dienst anweisen, das DDX-Dokument zu validieren, anstatt es auszuführen. Außerdem können Sie die Menge an Informationen erhöhen, die der Assembler-Dienst in die Protokolldatei schreibt.

**Validierung durchführen**

Nachdem Sie den Assembler-Dienst-Client erstellt, auf das DDX-Dokument verwiesen und Laufzeitoptionen festgelegt haben, können Sie die `invokeDDX` -Vorgang zum Überprüfen des DDX-Dokuments. Bei der Validierung des DDX-Dokuments können Sie `null` als map -Parameter (dieser Parameter speichert normalerweise PDF-Dokumente, die der Assembler benötigt, um die im DDX-Dokument angegebenen Vorgänge auszuführen).

Wenn die Validierung fehlschlägt, wird eine Ausnahme ausgelöst und die Protokolldatei enthält Details, die erklären, warum das DDX-Dokument ungültig ist, können Sie von der `OperationException` -Instanz. Nach der grundlegenden XML-Analyse und Schemakonferenz wird die Validierung anhand der DDX-Spezifikation durchgeführt. Alle im DDX-Dokument enthaltenen Fehler werden im Protokoll angegeben.

**Die Prüfergebnisse in einer Protokolldatei speichern**

Der Assembler-Dienst gibt die Überprüfungsergebnisse zurück, die Sie in eine XML-Protokolldatei schreiben können. Die Detailtiefe, die der Assembler-Dienst in die Protokolldatei schreibt, hängt von der von Ihnen festgelegten Laufzeitoption ab.

**Siehe auch**

[Überprüfen eines DDX-Dokuments mit der Java-API](#validate-a-ddx-document-using-the-java-api)

[Validieren eines DDX-Dokuments mithilfe der Webdienst-API](#validate-a-ddx-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Überprüfen eines DDX-Dokuments mit der Java-API {#validate-a-ddx-document-using-the-java-api}

Validieren Sie ein DDX-Dokument mithilfe der Assembler Service-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, mit der der Assembler-Dienst angewiesen wird, das DDX-Dokument zu validieren, indem er die `AssemblerOptionSpec` setValidateOnly -Methode des Objekts und Übergeben `true`.
   * Legen Sie die Menge an Informationen fest, die der Assembler-Dienst in die Protokolldatei schreibt, indem er die `AssemblerOptionSpec` -Objekt `getLogLevel` -Methode verwenden und einen Zeichenfolgenwert übergeben, erfüllt Ihre Anforderungen. Beim Validieren eines DDX-Dokuments möchten Sie weitere Informationen in die Protokolldatei schreiben, die den Validierungsprozess unterstützen. Daher können Sie den Wert `FINE` oder `FINER`.

1. Führen Sie die Überprüfung durch.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für das java.io.Map -Objekt, das normalerweise PDF-Dokumente speichert.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt.

   Die `invokeDDX` -Methode gibt eine `AssemblerResult` -Objekt, das Informationen enthält, die angeben, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die `AssemblerResult` -Objekt `getJobLog` -Methode. Diese Methode gibt eine `com.adobe.idp.Document` -Instanz, die Validierungsinformationen enthält.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt in die Datei ein.

   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird ein `OperationException` geworfen wird. Innerhalb der catch-Anweisung können Sie die `OperationException` -Objekt `getJobLog` -Methode.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[Schnellstart (SOAP-Modus): Validieren von DDX-Dokumenten mit der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api) (SOAP-Modus)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Validieren eines DDX-Dokuments mithilfe der Webdienst-API {#validate-a-ddx-document-using-the-web-service-api}

Validieren Sie ein DDX-Dokument mithilfe der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie localhost durch die IP-Adresse des Formularservers.

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
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Legen Sie Laufzeitoptionen fest, um das DDX-Dokument zu validieren.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie die Laufzeitoption fest, die den Assembler-Dienst anweist, das DDX-Dokument zu validieren, indem der Wert true dem Wert `AssemblerOptionSpec` -Objekt `validateOnly` Datenelement.
   * Legen Sie die Menge an Informationen fest, die der Assembler-Dienst in die Protokolldatei schreibt, indem Sie dem `AssemblerOptionSpec` -Objekt `logLevel` Datenelement. -Methode Beim Validieren eines DDX-Dokuments möchten Sie weitere Informationen in die Protokolldatei schreiben, die den Validierungsprozess unterstützen. Daher können Sie den Wert `FINE` oder `FINER`. Informationen zu den Laufzeitoptionen, die Sie festlegen können, finden Sie unter `AssemblerOptionSpec` Klassenreferenz in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Führen Sie die Überprüfung durch.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt.
   * Der Wert `null` für `Map` -Objekt, das normalerweise PDF-Dokumente speichert.
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt.

   Die `invokeDDX` -Methode gibt eine `AssemblerResult` -Objekt, das Informationen enthält, die angeben, ob das DDX-Dokument gültig ist.

1. Speichern Sie die Validierungsergebnisse in einer Protokolldatei.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort der Protokolldatei und den Modus zum Öffnen der Datei darstellt. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie eine `BLOB` -Objekt, das Protokollinformationen speichert, indem der Wert des `AssemblerResult` -Objekt `jobLog` Datenelement.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

   >[!NOTE]
   >
   >Wenn das DDX-Dokument ungültig ist, wird ein `OperationException` geworfen wird. Innerhalb der catch-Anweisung können Sie den Wert der `OperationException` -Objekt `jobLog` Mitglied.

**Siehe auch**

[Validieren von DDX-Dokumenten](#validating-ddx-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
