---
title: Konvertieren von PDF in PostScript- und Bilddateien
seo-title: Converting PDF to Postscript andImage Files
description: Verwenden Sie den Convert PDF-Dienst, um PDF-Dokumente mithilfe der Java-API und der Web Service-API in PostScript und eine Reihe von Bildformaten (JPEG, JPEG 2000, PNG und TIFF) zu konvertieren.
seo-description: Use the Convert PDF service to convert PDF documents to PostScript and to a number of image formats (JPEG, JPEG 2000, PNG, and TIFF) using the Java API and Web Service API.
uuid: 07da0391-7180-4197-aaa6-ae753d753b84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: f8707752-2c83-461a-b83d-708754b0f3f6
role: Developer
exl-id: 4afed537-1694-4187-8968-608f49116c2e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2795'
ht-degree: 6%

---

# Konvertieren von PDF in PostScript- und Bilddateien {#converting-pdf-to-postscript-andimage-files}

**Über den Convert PDF-Dienst**

Der Convert PDF-Dienst konvertiert PDF-Dokumente in PostScript und eine Reihe von Bildformaten (JPEG, JPEG 2000, PNG und TIFF). Das Konvertieren eines PDF-Dokuments in PostScript ist nützlich für die unbeaufsichtigte serverbasierte Druckausgabe auf PostScript-Druckern. Das Konvertieren eines PDF-Dokuments in eine mehrseitige TIFF-Datei ist beim Archivieren von Dokumenten in Content Management-Systemen praktisch, die PDF-Dokumente nicht unterstützen.

Mithilfe des Convert PDF-Dienstes können Sie diese Aufgaben ausführen:

* Konvertieren von PDF-Dokumenten in PostScript – 
* Konvertieren Sie PDF-Dokumente in Bildformate.

   >[!NOTE]
   >
   >Weitere Informationen zum Convert PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PDF-Dokumenten in PostScript {#converting-pdf-documents-to-postscript}

Hier wird beschrieben, wie Sie mit der Convert PDF Service API (Java- und Webdienst) PDF-Dokumente programmgesteuert in PostScript-Dateien konvertieren können. Das PDF-Dokument, das in eine PostScript-Datei konvertiert wird, muss ein nicht interaktives PDF-Dokument sein. Wenn Sie also versuchen, ein interaktives PDF-Dokument in eine PostScript-Datei zu konvertieren, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um ein PDF-Dokument in eine PostScript-Datei zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Convert PDF-Dienst-Client.
1. Referenzieren Sie das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.
1. Festlegen von Konversions-Laufzeitoptionen.
1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.
1. Speichern Sie die PostScript-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Convert PDF-Clients**

Bevor Sie programmgesteuert einen Vorgang des Convert PDF-Dienstes ausführen können, müssen Sie einen Convert PDF-Dienst-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `ConvertPdfServiceClient` -Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie eine `ConvertPDFServiceService` -Objekt.

In diesem Abschnitt werden Webdienstfunktionen verwendet, die in AEM Forms eingeführt wurden. Um auf neue Funktionen zugreifen zu können, müssen Sie Ihr Proxy-Objekt mithilfe der `lc_version` -Attribut. (Siehe &quot;Zugriff auf neue Funktionen mithilfe von Webdiensten&quot;in [Aufrufen von AEM Forms mithilfe von Webdiensten](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).

**Referenzieren des PDF-Dokuments zur Konvertierung in eine PostScript-Datei**

Referenzieren Sie das PDF-Dokument, das Sie in eine PostScript-Datei konvertieren möchten. Wie bereits in diesem Thema erwähnt, muss das PDF-Dokument ein nicht interaktives PDF-Dokument sein. Wenn Sie versuchen, ein interaktives PDF-Dokument in eine PostScript-Datei zu konvertieren, wird eine Ausnahme ausgelöst.

**Laufzeitoptionen für Konversionen festlegen**

Beim Konvertieren eines PDF-Dokuments in eine PostScript-Datei können Sie Laufzeitoptionen definieren, die den erstellten PostScript-Typ angeben. Sie können beispielsweise eine PostScript-Datei der Stufe 3 definieren.

In der Regel spiegelt die generierte PostScript-Datei die Größe des PDF-Eingabedokuments wider. Wenn Sie die `ShrinkToFit` -Option (wodurch die Ausgabe der PostScript-PDF-Datei an die Seite angepasst wird), wird kein Unterschied zwischen dem Eingabedokument und der generierten PostScript--Datei angezeigt. Die `ShrinkToFit` wird nur wirksam, wenn Sie sich dafür entscheiden, auf einer kleineren Seitengröße als das PDF-Eingabedokument zu drucken. Um eine kleinere Seitengröße auszuwählen, definieren Sie die `PageSize` -Option. Darüber hinaus wird empfohlen, die Variable `RotateAndCenter` -Option `true` um die richtige PostScript-Ausgabe zu erhalten.

Wenn Sie die `ExpandToFit` -Option (die die Ausgabe der PostScript-Datei so erweitert, dass sie auf die Seite passt), wird sie nur wirksam, wenn Sie sich dafür entscheiden, auf eine größere Seitengröße als das PDF-Eingabedokument zu drucken. Um eine größere Seitengröße auszuwählen, definieren Sie die `PageSize` -Option. Darüber hinaus wird empfohlen, die Variable `RotateAndCenter` -Option `true` um die richtige PostScript-Ausgabe zu erhalten.

>[!NOTE]
>
>Informationen zu den Laufzeitwerten, die Sie festlegen können, finden Sie unter `ToPSOptionsSpec` Klassenreferenz in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Konvertieren des PDF-Dokuments in eine PostScript-Datei**

Nachdem Sie den Service-Client erstellt und Laufzeitoptionen festgelegt haben, können Sie den PostScript-Konvertierungsvorgang aufrufen. Dieser Vorgang benötigt Informationen zum zu konvertierenden Dokument, einschließlich der bevorzugten PostScript-Ebene für das Zieldokument.

**PostScript-Datei speichern**

Nachdem Sie das PDF-Dokument in PostScript konvertiert haben, können Sie die Ausgabe als PostScript-Datei speichern.

**Siehe auch**

[Konvertieren eines PDF-Dokuments in PS mithilfe der Java-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-java-api)

[Konvertieren eines PDF-Dokuments in PS mithilfe der Web Service-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF Service-API-Schnellstarts konvertieren](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in PS mithilfe der Java-API {#convert-a-pdf-document-to-ps-using-the-java-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF Service API (Java) in PostScript:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-convertpdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Convert PDF Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des zu konvertierenden PDF-Dokuments angibt.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, das das PDF-Dokument mithilfe der `com.adobe.idp.Document` -Konstruktor. Übergeben Sie die `java.io.FileInputStream` -Objekt, das das PDF-Dokument enthält.

1. Festlegen von Konversions-Laufzeitoptionen.

   * Erstellen Sie eine `ToPSOptionsSpec` -Objekt durch Aufrufen seines Konstruktors.
   * Festlegen von Laufzeitoptionen durch Aufrufen einer entsprechenden Methode, die zum `ToPSOptionsSpec` -Objekt. Um beispielsweise die erstellte PostScript-Ebene zu definieren, rufen Sie die `ToPSOptionsSpec` -Objekt `setPsLevel` -Methode und übergeben Sie eine `PSLevel` Auflistungswert, der die PostScript-Ebene angibt. Informationen zu allen Laufzeitwerten, die Sie festlegen können, finden Sie unter `ToPSOptionsSpec` Klassenreferenz in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.

   Rufen Sie die `ConvertPdfServiceClient`-Objekt `toPS2` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das PDF-Dokument darstellt, das in eine PostScript-Datei konvertiert werden soll.
   * A `ToPSOptionsSpec` -Objekt, das PostScript-Laufzeitoptionen angibt.

   Die `toPS2` -Methode gibt eine `Document` -Objekt, das das neue PostScript-Dokument enthält.

1. Speichern Sie die PostScript-Datei.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateinamenerweiterung .ps lautet.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `toPS2` -Methode).

**Siehe auch**

[Zusammenfassung der Schritte](converting-pdf-postscript-image-files.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Konvertieren eines PDF-Dokuments in PostScript mithilfe der Java-API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren eines PDF-Dokuments in PS mithilfe der Web Service-API {#convert-a-pdf-document-to-ps-using-the-web-service-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF Service-API (Webdienst) in PostScript:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Convert PDF Client.

   * Erstellen Sie eine `ConvertPdfServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `ConvertPdfServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Geben Sie jedoch `?blob=mtom`.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `ConvertPdfServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `ConvertPdfServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `ConvertPdfServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren Sie das PDF-Dokument, das in eine PostScript-Datei konvertiert werden soll.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines PDF-Dokuments verwendet, das in eine PostScript-Datei konvertiert wird.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des zu konvertierenden PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode und Übergabe des Byte-Arrays, der Startposition und der Stream-Länge zum Lesen.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Festlegen von Konversions-Laufzeitoptionen.

   * Erstellen Sie eine `ToPSOptionsSpec` -Objekt durch Aufrufen seines Konstruktors.
   * Festlegen von Laufzeitoptionen durch Zuweisen eines Werts zum `ToPSOptionsSpec` -Datenelement des -Objekts. Um beispielsweise die zu erstellende PostScript-Ebene zu definieren, weisen Sie eine `PSLevel` Auflistungswert zum `ToPSOptionsSpec` -Objekt `psLevel` Datenelement.

1. Konvertieren Sie das PDF-Dokument in eine PostScript-Datei.

   Rufen Sie die `GeneratePDFServiceService` -Objekt `toPS2` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das PDF-Dokument darstellt, das in eine PostScript-Datei konvertiert werden soll
   * A `ToPSOptionsSpec` -Objekt, das Laufzeitoptionen angibt

   Extrahieren Sie nach Abschluss der Konvertierung die Binärdaten, die das PostScript-Dokument darstellen, indem Sie auf dessen `BLOB` -Objekt `MTOM` -Eigenschaft. Dadurch wird ein Byte-Array zurückgegeben, das Sie in eine PostScript-Datei schreiben können.

1. Speichern Sie die PostScript-Datei.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort der PS-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `encryptPDFUsingPassword` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in die PostScript-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-pdf-postscript-image-files.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Konvertieren von PDF-Dokumenten in Bildformate {#converting-pdf-documents-to-image-formats}

Sie können den Convert PDF-Dienst verwenden, um PDF-Dokumente programmgesteuert in Bildformate zu konvertieren, darunter JPEG, JPEG 2000, TIFF und PNG. Durch Konvertieren eines PDF-Dokuments in eine Bilddatei können Sie das PDF-Dokument als Bilddatei verwenden. Sie können das Bild beispielsweise in einem Enterprise Content Management-System zur Speicherung platzieren.

Beim Konvertieren eines PDF-Dokuments in ein Bild erstellt der Convert PDF-Dienst ein eigenes Bild für jede-Seite im Dokument. Das heißt, wenn das Dokument 20 Seiten umfasst, erstellt der Convert PDF-Dienst 20 Bilddateien. Beim Konvertieren eines PDF-Dokuments in ein Bildformat können Sie für jede Seite innerhalb des PDF-Dokuments Einzelbilder erstellen oder für das gesamte PDF-Dokument eine Bilddatei erstellen.

>[!NOTE]
>
>Weitere Informationen zum Convert PDF-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Führen Sie die folgenden Schritte aus, um ein PDF-Dokument in einen der unterstützten Typen zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Convert PDF-Dienst-Client.
1. Rufen Sie das zu konvertierende PDF-Dokument ab.
1. Legen Sie Laufzeitoptionen fest.
1. Konvertieren Sie die PDF in ein Bild.
1. Rufen Sie die Bilddateien aus einer Sammlung ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Convert PDF-Clients**

Bevor Sie programmgesteuert einen Vorgang des Convert PDF-Dienstes ausführen können, müssen Sie einen Convert PDF-Dienst-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `ConvertPdfServiceClient` -Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie eine `ConvertPDFServiceService` -Objekt.

**Abrufen des zu konvertierenden PDF-Dokuments**

Sie müssen das PDF-Dokument abrufen, um es in ein Bild zu konvertieren. Sie können ein interaktives PDF-Dokument nicht in ein Bild konvertieren. Wenn Sie dies versuchen, wird eine Ausnahme ausgelöst. Um ein interaktives PDF-Dokument in eine Bilddatei zu konvertieren, müssen Sie das PDF-Dokument vor dem Konvertieren reduzieren. (Siehe [Reduzieren von PDF-Dokumenten](/help/forms/developing/creating-document-output-streams.md#flattening-pdf-documents).

**Laufzeitoptionen festlegen**

Sie müssen Laufzeitoptionen festlegen, z. B. das Bildformat und die Auflösungswerte. Informationen zu den Laufzeitwerten finden Sie unter `ToImageOptionsSpec` Klassenreferenz in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**PDF in ein Bild konvertieren**

Nachdem Sie den Service-Client erstellt und Laufzeitoptionen festgelegt haben, können Sie das PDF-Dokument in ein Bild konvertieren. Ein Sammlungsobjekt, das die Bilder enthält, wird zurückgegeben.

**Abrufen der Bilddateien aus einer Sammlung**

Sie können Bilddateien von einem Sammlungsobjekt abrufen, das der Convert PDF-Dienst zurückgibt. Jedes Element in der Sammlung ist ein `com.adobe.idp.Document` Instanz (oder `BLOB` -Instanz, wenn Sie Webdienste verwenden), die Sie als Bilddatei speichern können, z. B. als JPG-Datei.

Das Format der Bilddatei hängt von der `ImageConvertFormat` Laufzeitoption. Das heißt, wenn Sie die `ImageConvertFormat` Laufzeitoption zu `ImageConvertFormat.JPEG`, können Sie Bilddateien als JPG-Dateien speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF Service-API-Schnellstarts konvertieren](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in Bilddateien mithilfe der Java-API {#convert-a-pdf-document-to-image-files-using-the-java-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF Service API (Java) in ein Bildformat:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-convertpdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Convert PDF Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ConvertPdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das zu konvertierende PDF-Dokument mithilfe des Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `ToImageOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Rufen Sie nach Bedarf Methoden auf, die zu diesem Objekt gehören. Legen Sie beispielsweise den Bildtyp fest, indem Sie die `setImageConvertFormat` -Methode und Übergeben einer `ImageConvertFormat` enum -Wert, der den Formattyp angibt.

   >[!NOTE]
   >
   >Festlegen der `ImageConvertFormat` Der Auflistungswert ist obligatorisch.

1. Konvertieren Sie die PDF in ein Bild.

   Rufen Sie die `ConvertPdfServiceClient` -Objekt `toImage2` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das die zu konvertierende PDF-Datei darstellt.
   * A `com.adobe.livecycle.converpdfservice.client.ToImageOptionsSpec` -Objekt, das die verschiedenen Voreinstellungen zum Zielbildformat enthält.

   Die `toImage2` -Methode gibt eine `java.util.List` -Objekt, das Bilder enthält. Jedes Element in der Sammlung ist ein `com.adobe.idp.Document` -Instanz.

1. Rufen Sie die Bilddateien aus einer Sammlung ab.

   Iteration durch die `java.util.List` -Objekt, um zu bestimmen, ob Bilder vorhanden sind. Jedes Element ist eine `com.adobe.idp.Document` -Instanz. Speichern Sie das Bild, indem Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode und Übergeben einer `java.io.File` -Objekt.

**Siehe auch**

[Schnellstart (SOAP-Modus): Konvertieren eines PDF-Dokuments in JPEG-Dateien mithilfe der Java-API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

### Konvertieren eines PDF-Dokuments in Bilddateien mithilfe der Webdienst-API {#convert-a-pdf-document-to-image-files-using-the-web-service-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Convert PDF Service API (Webdienst) in ein Bildformat:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF-Client zum Konvertieren.

   * Erstellen Sie eine `ConvertPdfServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `ConvertPdfServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Geben Sie jedoch `?blob=mtom`.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `ConvertPdfServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `ConvertPdfServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `ConvertPdfServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Diese `BLOB` -Objekt wird zum Speichern des PDF-Formulars verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Formulars und den Modus zum Öffnen der Datei angibt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Bestimmen Sie die Größe des Byte-Arrays, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie ein Objekt `ToImageOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Rufen Sie nach Bedarf Methoden auf, die zu diesem Objekt gehören. Legen Sie beispielsweise den Bildtyp fest, indem Sie die `setImageConvertFormat` -Methode und Übergeben einer `ImageConvertFormat` Auflistungswert, der den Formattyp angibt.

   >[!NOTE]
   >
   >Festlegen der `ImageConvertFormat` Der Auflistungswert ist obligatorisch.

1. Konvertieren Sie die PDF in ein Bild.

   Rufen Sie die `ConvertPDFServiceService` -Objekt `toImage2` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das die zu konvertierende Datei darstellt
   * A `ToImageOptionsSpec` -Objekt, das die verschiedenen Voreinstellungen zum Zielbildformat enthält

   Die `toImage2` -Methode gibt eine `MyArrayOfBLOB` -Objekt, das die neu erstellten Bilddateien enthält.

1. Rufen Sie die Bilddateien aus einer Sammlung ab.

   * Bestimmen Sie die Anzahl der Elemente im `MyArrayOfBLOB` -Objekt durch Abrufen des Werts seiner `Count` -Feld. Jedes Element ist eine `BLOB` -Objekt, das das Bild enthält.
   * Iteration durch die `MyArrayOfBLOB` -Objekt und speichern Sie jede Bilddatei.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
