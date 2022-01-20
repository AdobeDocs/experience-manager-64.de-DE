---
title: Importieren und Exportieren von Daten
seo-title: Importing and Exporting Data
description: Verwenden Sie den Formulardatenintegrationsdienst, um Daten in ein PDF-Formular zu importieren und mithilfe der Java-API und der Web Service-API Daten aus einem PDF-Formular zu exportieren.
seo-description: Use the Form Data Integration service to import data into a PDF form and export data from a PDF form using the Java API and Web Service API.
uuid: 94ccb6f2-6e5f-43ea-a954-9a4402871a17
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 2e783745-c986-45ba-8e65-7437d114ca38
role: Developer
exl-id: e9d10d35-6a8d-497d-83f7-67ee6c22baed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2764'
ht-degree: 6%

---

# Importieren und Exportieren von Daten {#importing-and-exporting-data}

## Über den Formulardatenintegrationsdienst {#about-the-form-data-integration-service}

Der Formulardatenintegrationsdienst kann Daten in ein PDF-Formular importieren und aus einem PDF-Formular exportieren. Die Ein- und Ausfuhrvorgänge unterstützen zwei Arten von PDF forms:

* Ein (in Acrobat erstelltes) Acrobat-Formular ist ein PDF-Dokument mit Formularfeldern.
* Ein in Designer erstelltes Adobe XML-Formular ist ein PDF-Dokument, das der XML Adobe Forms Architecture (XFA) entspricht.

Je nach PDF-Formulartyp können Formulardaten in einem der folgenden Formate vorhanden sein:

* Als XFDF-Datei, die eine XML-Version des Acrobat-Formulardatenformats darstellt.
* Als XDP-Datei, die eine XML-Datei mit Formularfelddefinitionen darstellt. Diese kann auch Formularfelddaten und eine eingebettete PDF-Datei enthalten. Eine von Designer generierte XDP-Datei kann nur verwendet werden, wenn sie ein eingebettetes base-64-kodiertes PDF-Dokument enthält.

Sie können diese Aufgaben mit dem Formulardatenintegrationsdienst ausführen:

* Importieren Sie Daten in PDF forms. Weitere Informationen finden Sie unter [Importieren von Formulardaten](importing-exporting-data.md#importing-form-data).
* Exportieren Sie Daten aus PDF forms. Weitere Informationen finden Sie unter [Exportieren von Formulardaten](importing-exporting-data.md#exporting-form-data).

>[!NOTE]
>
>Weitere Informationen zum Formulardatenintegrationsdienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Importieren von Formulardaten {#importing-form-data}

Sie können Formulardaten mit dem Formulardatenintegrationsdienst in interaktive PDF forms importieren. Ein interaktives PDF-Formular ist ein PDF-Dokument, das ein oder mehrere Felder zum Erfassen von Benutzerinformationen oder zum Anzeigen benutzerdefinierter Informationen enthält. Der Formulardatenintegrationsdienst unterstützt keine Formularberechnungen, Validierungen oder Skripten.

Um Daten in ein in Designer erstelltes Formular zu importieren, müssen Sie eine gültige XDP-XML-Datenquelle referenzieren. Betrachten Sie das folgende Beispielformular für einen Hypothekenantrag.

![ie_ie_loanformdata](assets/ie_ie_loanformdata.png)

Um Datenwerte in dieses Formular zu importieren, müssen Sie über eine gültige XDP XML-Datenquelle verfügen, die dem Formular entspricht. Sie können keine beliebige XML-Datenquelle verwenden, um Daten mithilfe des Formulardatenintegrationsdienstes in ein Formular zu importieren. Der Unterschied zwischen einer beliebigen XML-Datenquelle und einer XDP-XML-Datenquelle besteht darin, dass eine XDP-Datenquelle der XML Forms Architecture (XFA) entspricht. Die folgende XML-Datei stellt eine XDP-XML-Datenquelle dar, die dem Beispiel-Hypothekenantragsformular entspricht.

```as3
 <?xml version="1.0" encoding="UTF-8" ?>  
 - <xfa:datasets xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"> 
 - <xfa:data> 
 - <data> 
     - <Layer> 
         <closeDate>1/26/2007</closeDate>  
         <lastName>Johnson</lastName>  
         <firstName>Jerry</firstName>  
         <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>  
         <city>New York</city>  
         <zipCode>00501</zipCode>  
         <state>NY</state>  
         <dateBirth>26/08/1973</dateBirth>  
         <middleInitials>D</middleInitials>  
         <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>  
         <phoneNumber>5555550000</phoneNumber>  
     </Layer> 
     - <Mortgage> 
         <mortgageAmount>295000.00</mortgageAmount>  
         <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>  
         <purchasePrice>300000</purchasePrice>  
         <downPayment>5000</downPayment>  
         <term>25</term>  
         <interestRate>5.00</interestRate>  
     </Mortgage> 
 </data> 
 </xfa:data> 
 </xfa:datasets>
```

>[!NOTE]
>
>Weitere Informationen zum Formulardatenintegrationsdienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So importieren Sie Formulardaten in ein PDF-Formular:

1. Projektdateien einschließen.
1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.
1. Referenzieren Sie ein PDF-Formular.
1. Referenzieren einer XML-Datenquelle.
1. Importieren Sie Daten in das PDF-Formular.
1. Speichern Sie das PDF-Formular als PDF-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Client für den Formulardatenintegrationsdienst**

Bevor Sie Daten programmgesteuert in eine PDF Form Client API importieren können, müssen Sie einen Client für den Datenintegrationsdienst erstellen. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind. Weitere Informationen finden Sie unter [Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenzieren eines PDF-Formulars**

Um Daten in ein PDF-Formular zu importieren, müssen Sie entweder auf ein in Designer erstelltes XML-Formular oder auf ein in Acrobat erstelltes Acrobat-Formular verweisen.

**Referenzieren einer XML-Datenquelle**

Um Formulardaten zu importieren, müssen Sie auf eine gültige Datenquelle verweisen. Um Daten in ein in Designer erstelltes XFA XML-Formular zu importieren, müssen Sie eine XDP XML-Datenquelle verwenden. Wenn Sie auf ein Acrobat-Formular verweisen, müssen Sie eine XFDF-Datenquelle verwenden. Für jedes Feld, in das Sie Daten importieren möchten, muss ein Wert angegeben werden. Wenn ein Element in der XML-Datenquelle keinem Feld im Formular entspricht, wird das Element ignoriert.

**Daten in das PDF-Formular importieren**

Nachdem Sie ein PDF-Formular und eine gültige XML-Datenquelle referenziert haben, können Sie die Daten in das PDF-Formular importieren.

**Speichern Sie das PDF-Formular als PDF-Datei**

Nachdem Sie Daten in ein Formular importiert haben, können Sie das Formular als PDF-Datei speichern. Nach dem Speichern als PDF-Datei kann ein Benutzer das Formular in Adobe Reader oder Acrobat öffnen und das Formular mit den importierten Daten anzeigen.

**Siehe auch**

[Importieren von Formulardaten mit der Java-API](importing-exporting-data.md#import-form-data-using-the-java-api)

[Importieren von Formulardaten mit der Webdienst-API](importing-exporting-data.md#import-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für den Formulardatenintegrationsdienst](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Exportieren von Formulardaten](importing-exporting-data.md#exporting-form-data)

### Importieren von Formulardaten mit der Java-API {#import-form-data-using-the-java-api}

Importieren Sie Formulardaten mit der Form Data Integration API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-formdataintegration-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein PDF-Formular.

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Formulars angibt.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, das das PDF-Formular mithilfe der `com.adobe.idp.Document` -Konstruktor. Übergeben Sie die `java.io.FileInputStream` -Objekt, das das PDF-Formular für den Konstruktor enthält.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort der XML-Datei angibt, die Daten enthält, die in das Formular importiert werden sollen.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, das Formulardaten mithilfe der `com.adobe.idp.Document` -Konstruktor. Übergeben Sie die `java.io.FileInputStream` -Objekt, das Formulardaten für den Konstruktor enthält.

1. Importieren Sie Daten in das PDF-Formular.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `FormDataIntegrationClient` -Objekt `importData` -Methode verwenden und die folgenden Werte übergeben:

   * Die `com.adobe.idp.Document` -Objekt, das das PDF-Formular speichert.
   * Die `com.adobe.idp.Document` -Objekt, das Formulardaten speichert.

   Die `importData` -Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein PDF-Formular speichert, das die Daten in der XML-Datenquelle enthält.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateierweiterung &quot;.PDF&quot;lautet.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `importData` -Methode).

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Importieren von Formulardaten mit der Java-API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importieren von Formulardaten mit der Webdienst-API {#import-form-data-using-the-web-service-api}

Importieren Sie Formulardaten mithilfe der Form Data Integration API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.

   * Erstellen Sie eine `FormDataIntegrationClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `FormDataIntegrationClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `FormDataIntegrationClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `FormDataIntegrationClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `FormDataIntegrationClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren Sie ein PDF-Formular.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Diese `BLOB` -Objekt wird zum Speichern des PDF-Formulars verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Formulars und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Diese `BLOB` -Objekt wird verwendet, um die in das Formular importierten Daten zu speichern.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt, die zu importierende Daten enthält, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Importieren Sie Daten in das PDF-Formular.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `FormDataIntegrationClient` -Objekt `importData` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das das PDF-Formular speichert.
   * Die `BLOB` -Objekt, das Formulardaten speichert.

   Die `importData` -Methode gibt eine `BLOB` -Objekt, das ein PDF-Formular speichert, das die Daten in der XML-Datenquelle enthält.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort der PDF-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `importData` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Exportieren von Formulardaten {#exporting-form-data}

Sie können Formulardaten aus einem interaktiven PDF-Formular mithilfe des Formulardatenintegrationsdienstes exportieren. Das Format der exportierten Daten hängt vom Formulartyp ab. Wenn der Formulartyp ein in Acrobat erstelltes Acrobat-Formular ist, sind die exportierten Daten XFDF. Wenn der Formulartyp ein XML-Formular ist, das in Designer erstellt wurde, sind die exportierten Daten XDP.

>[!NOTE]
>
>Weitere Informationen zum Formulardatenintegrationsdienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So exportieren Sie Formulardaten aus einem PDF-Formular:

1. Projektdateien einschließen
1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.
1. Referenzieren Sie ein PDF-Formular.
1. Exportieren Sie Daten aus dem PDF-Formular.
1. Speichern Sie die exportierten Daten als XML-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Client für den Formulardatenintegrationsdienst**

Bevor Sie Daten programmgesteuert in eine PDF formClient-API importieren können, müssen Sie einen Client für den Datenintegrationsdienst erstellen. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind. Für Informationen: [Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenzieren eines PDF-Formulars**

Um Daten aus einem PDF-Formular zu exportieren, müssen Sie auf ein in Designer oder Acrobat erstelltes PDF-Formular verweisen, das Formulardaten enthält. Wenn Sie versuchen, Daten aus einem leeren PDF-Formular zu exportieren, erhalten Sie ein leeres XML-Schema.

**Daten aus dem PDF-Formular exportieren**

Nachdem Sie auf ein PDF-Formular mit Formulardaten verwiesen haben, können Sie die Daten aus dem Formular exportieren. Die Daten werden in ein XML-Schema exportiert, das auf dem Formular basiert.

**Speichern Sie die Formulardaten als XML-Datei**

Nach dem Export von Formulardaten können Sie die Daten als XML-Datei speichern. Nach dem Speichern als XML-Datei können Sie die XML-Datei in einem XML-Viewer öffnen, um die Formulardaten anzuzeigen.

**Siehe auch**

[Exportieren von Formulardaten mit der Java-API](importing-exporting-data.md#export-form-data-using-the-java-api)

[Exportieren von Formulardaten mit der Webdienst-API](importing-exporting-data.md#export-form-data-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für den Formulardatenintegrationsdienst](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Importieren von Formulardaten](importing-exporting-data.md#importing-form-data)

### Exportieren von Formulardaten mit der Java-API {#export-form-data-using-the-java-api}

Exportieren Sie Formulardaten mithilfe der Form Data Integration API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-formdataintegration-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormDataIntegrationClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren Sie ein PDF-Formular.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des zu exportierenden PDF-Formulars angibt.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, das das PDF-Formular mithilfe der `com.adobe.idp.Document` -Konstruktor. Übergeben Sie die `java.io.FileInputStream` -Objekt, das das PDF-Formular für den Konstruktor enthält.

1. Exportieren Sie Daten aus dem PDF-Formular.

   Exportieren von Formulardaten durch Aufrufen der `FormDataIntegrationClient` -Objekt `exportData` -Methode und übergeben Sie die `com.adobe.idp.Document` -Objekt, das das PDF-Formular speichert. Diese Methode gibt eine `com.adobe.idp.Document` -Objekt, das Formulardaten als XML-Schema speichert.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `exportData` -Methode).

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Exportieren von Formulardaten mit der Java-API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportieren von Formulardaten mit der Webdienst-API {#export-form-data-using-the-web-service-api}

Exportieren Sie Formulardaten mithilfe der Form Data Integration API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   * Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Client für den Formulardatenintegrationsdienst.

   * Erstellen Sie eine `FormDataIntegrationClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `FormDataIntegrationClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `FormDataIntegrationClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `FormDataIntegrationClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `FormDataIntegrationClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren Sie ein PDF-Formular.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Diese `BLOB` -Objekt wird verwendet, um das PDF-Formular zu speichern, aus dem Daten exportiert werden.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Formulars und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Exportieren Sie Daten aus dem PDF-Formular.

   Importieren Sie Daten in das PDF-Formular, indem Sie die `FormDataIntegrationClient` -Objekt `exportData` -Methode und übergeben Sie die `BLOB` -Objekt, das das PDF-Formular speichert. Diese Methode gibt eine `BLOB` -Objekt, das Formulardaten als XML-Schema speichert.

1. Speichern Sie das PDF-Formular als PDF-Datei.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines string-Werts, der den Speicherort der XML-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `exportData` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine XML-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](importing-exporting-data.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
