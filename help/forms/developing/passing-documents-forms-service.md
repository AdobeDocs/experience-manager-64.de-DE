---
title: Übergeben von Dokumenten an den FormsService
seo-title: Passing Documents to the FormsService
description: Übergeben Sie ein com.adobe.idp.Document -Objekt, das den Formularentwurf enthält, an den Forms-Dienst. Der Forms-Dienst rendert den Formularentwurf im Objekt com.adobe.idp.Document .
seo-description: Pass a com.adobe.idp.Document object that contains the form design to the Forms service. The Forms service renders the form design located in the com.adobe.idp.Document object.
uuid: 841e97f3-ebb8-4340-81a9-b6db11f0ec82
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: e23de3c3-f8a0-459f-801e-a0942fb1c6aa
role: Developer
exl-id: fe19e9b3-d662-4df2-b372-5006b794cde8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1670'
ht-degree: 3%

---

# Übergeben von Dokumenten an den Forms-Dienst {#passing-documents-to-the-formsservice}

Der AEM Forms-Dienst rendert interaktive PDF forms an Client-Geräte, normalerweise Webbrowser, um Benutzerinformationen zu erfassen. Ein interaktives PDF-Formular basiert auf einem Formularentwurf, der normalerweise als XDP--Datei gespeichert und in Designer erstellt wird. Ab AEM Forms können Sie eine `com.adobe.idp.Document` -Objekt, das den Formularentwurf für den Forms-Dienst enthält. Der Forms-Dienst rendert dann den Formularentwurf im `com.adobe.idp.Document` -Objekt.

Der Vorteil der Übergabe eines `com.adobe.idp.Document` -Objekt für den Forms-Dienst ist, dass andere Dienstvorgänge eine `com.adobe.idp.Document` -Instanz. Das heißt, Sie können eine `com.adobe.idp.Document` -Instanz von einem anderen Dienstvorgang aus und rendern Sie ihn. Angenommen, eine XDP-Datei wird in einem Knoten von Content Services (veraltet) gespeichert, der `/Company Home/Form Designs`, wie in der folgenden Abbildung dargestellt.

Sie können Loan.xdp programmgesteuert aus Content Services (nicht mehr unterstützt) abrufen und die XDP-Datei in einer `com.adobe.idp.Document` -Objekt.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein Dokument aus Content Services (nicht mehr unterstützt) an den Forms-Dienst zu übergeben:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms- und ein Document Management Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus Content Services ab (nicht mehr unterstützt).
1. Rendern Sie das interaktive PDF-Formular.
1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Forms und ein Client-API-Objekt für Document Management erstellen**

Bevor Sie einen Forms-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie ein Forms Client-API-Objekt. Da mit diesem Workflow eine XDP-Datei aus Content Services (nicht mehr unterstützt) abgerufen wird, erstellen Sie ein Document Management-API-Objekt.

**Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)**

Rufen Sie die XDP-Datei aus Content Services (nicht mehr unterstützt) ab, indem Sie die Java- oder Webdienst-API verwenden. Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document` Instanz (oder `BLOB` -Instanz, wenn Sie Webdienste verwenden). Anschließend können Sie die `com.adobe.idp.Document` -Instanz auf den Forms-Dienst.

**Rendern eines interaktiven PDF-Formulars**

Übergeben Sie zum Rendern eines interaktiven Formulars die `com.adobe.idp.Document` -Instanz, die von Content Services (nicht mehr unterstützt) an den Forms-Dienst zurückgegeben wurde.

>[!NOTE]
>
>Sie können eine `com.adobe.idp.Document` , der den Formularentwurf für den Forms-Dienst enthält. Zwei neue Methoden namens `renderPDFForm2` und `renderHTMLForm2` akzeptieren `com.adobe.idp.Document` -Objekt, das einen Formularentwurf enthält.

**Ausführen einer Aktion mit dem Formulardatenstream**

Je nach Typ der Clientanwendung können Sie das Formular in einen Client-Webbrowser schreiben oder es als PDF-Datei speichern. Eine webbasierte Anwendung schreibt das Formular normalerweise in den Webbrowser. Eine Desktop-Applikation speichert das Formular jedoch normalerweise als PDF-Datei.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Übergeben von Dokumenten an den Forms-Dienst mithilfe der Java-API {#pass-documents-to-the-forms-service-using-the-java-api}

Übergeben Sie ein Dokument, das von Content Services (nicht mehr unterstützt) mithilfe der Forms-Dienst- und Content Services-API (nicht mehr unterstützt) erhalten wurde:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar und adobe-contentservices-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Forms und ein Client-API-Objekt für Document Management erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie eine `FormsServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)

   Rufen Sie die `DocumentManagementServiceClientImpl` -Objekt `retrieveContent` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher lautet `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.

   Die `retrieveContent` -Methode gibt eine `CRCResult` -Objekt, das die XDP-Datei enthält. Abrufen einer `com.adobe.idp.Document` -Instanz durch Aufrufen der `CRCResult` -Objekt `getDocument` -Methode.

1. Rendern eines interaktiven PDF-Formulars

   Rufen Sie die `FormsServiceClient` -Objekt `renderPDFForm2` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das den Formularentwurf enthält, der von Content Services abgerufen wurde (nicht mehr unterstützt).
   * A `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie einen leeren `com.adobe.idp.Document` -Objekt.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter und Sie können `null` , wenn Sie keine Laufzeitoptionen festlegen möchten.
   * A `URLSpec` -Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter und Sie können `null`.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dieser Wert ist ein optionaler Parameter und Sie können `null` , wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Ausführen einer Aktion mit dem Formulardatenstream

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `com.adobe.idp.Document` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` -Objekt `read` -Methode. Übergeben Sie das Byte-Array als Argument.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Übergeben von Dokumenten an den Forms-Dienst mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Übergeben von Dokumenten an den Forms-Dienst mithilfe der Webdienst-API {#pass-documents-to-the-forms-service-using-the-web-service-api}

Übergeben Sie ein Dokument, das von Content Services (nicht mehr unterstützt) mithilfe der Forms-Dienst- und Content Services-API (nicht mehr unterstützt) abgerufen wurde:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da diese Client-Anwendung zwei AEM Forms-Dienste aufruft, erstellen Sie zwei Dienstverweise. Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Forms-Dienst verknüpft ist: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Document Management-Dienst verknüpft ist: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Da die `BLOB` Datentyp für beide Dienstverweise verwendet wird, müssen Sie die `BLOB` Datentyp bei der Verwendung. Im entsprechenden Webdienst-Schnellstart werden alle `BLOB` -Instanzen sind vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen `localhost`* mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird. *

1. Forms und ein Client-API-Objekt für Document Management erstellen

   * Erstellen Sie eine `FormsServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `FormsServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/FormsService?WSDL`). Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `FormsServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `FormsServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `FormsServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für die `DocumentManagementServiceClient`* Service-Client. *

1. Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)

   Abrufen von Inhalten durch Aufrufen der `DocumentManagementServiceClient` -Objekt `retrieveContent` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher lautet `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.
   * Ein string -Ausgabeparameter, der den Wert des Durchsuchen-Links speichert.
   * A `BLOB` Ausgabeparameter, der den Inhalt speichert. Sie können diesen Ausgabeparameter verwenden, um den Inhalt abzurufen.
   * A `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` Ausgabeparameter, der Inhaltsattribute speichert.
   * A `CRCResult` Ausgabeparameter. Anstatt dieses Objekt zu verwenden, können Sie die `BLOB` Ausgabeparameter zum Abrufen des Inhalts.

1. Rendern eines interaktiven PDF-Formulars

   Rufen Sie die `FormsServiceClient` -Objekt `renderPDFForm2` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das den Formularentwurf enthält, der von Content Services abgerufen wurde (nicht mehr unterstützt).
   * A `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie einen leeren `BLOB` -Objekt.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dieser Wert ist ein optionaler Parameter und Sie können `null` , wenn Sie keine Laufzeitoptionen festlegen möchten.
   * A `URLSpec` -Objekt, das URI-Werte enthält. Dieser Wert ist ein optionaler Parameter und Sie können `null`.
   * A `Map` -Objekt, das Dateianlagen speichert. Dieser Wert ist ein optionaler Parameter und Sie können `null` , wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein long -Ausgabeparameter, der zum Speichern der Seitenzahl verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des Gebietsschemawerts verwendet wird.
   * A `FormsResult` Ausgabeparameter, der zum Speichern des interaktiven PDF-Formulars verwendet wird `.`

   Die `renderPDFForm2` -Methode gibt eine `FormsResult` -Objekt, das das interaktive PDF-Formular enthält.

1. Ausführen einer Aktion mit dem Formulardatenstream

   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, indem der Wert der `FormsResult` -Objekt `outputContent` -Feld.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort des interaktiven PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt, das aus dem `FormsResult` -Objekt. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
