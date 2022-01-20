---
title: 'Erstellen von Document Output Streams '
seo-title: Creating Document Output Streams
description: Verwenden Sie den Output-Dienst zum Konvertieren von Dokumenten in die Beschriftungsformate PDF (einschließlich PDF/A-Dokumente), PostScript, Printer Control Language (PCL) und Zebra - ZPL, Intermec - IPL, Datamax - DPL und TecToshiba - TPCL.
seo-description: Use the Output service to convert documents as PDF (including PDF/A documents), PostScript, Printer Control Language (PCL), and Zebra - ZPL, Intermec - IPL, Datamax - DPL, and TecToshiba - TPCL label formats.
uuid: 80c28efa-35ce-4073-9ca6-2d93bcd67fdd
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: de527d50-991b-4ca3-a8ac-44d5cab988e9
role: Developer
exl-id: 31f60907-0b9c-43ac-bb9f-74eacf6976d7
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 5%

---

# Erstellen von Document Output Streams  {#creating-document-output-streams}

**Über den Output-Dienst**

Mit dem Output-Dienst können Sie Dokumente als PDF (einschließlich PDF/A-Dokumente), PostScript, Printer Control Language (PCL) und die folgenden Beschriftungsformate ausgeben:

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Mithilfe des Output-Dienstes können Sie XML-Formulardaten mit einem Formularentwurf zusammenführen und das Dokument an einen Netzwerkdrucker oder eine Datei ausgeben.

Es gibt zwei Möglichkeiten, einen Formularentwurf (eine XDP-Datei) an den Output-Dienst zu übergeben. Sie können entweder eine `com.adobe.idp.Document` -Instanz, die einen Formularentwurf für den Output-Dienst enthält. Sie können auch einen URI-Wert übergeben, der den Speicherort des Formularentwurfs angibt. Beide Wege werden in *Programmieren mit AEM Formularen*.

>[!NOTE]
>
>Der Output-Dienst unterstützt keine Acroform PDF-Dokumente, die anwendungsobjektspezifische Skripte enthalten. Acroform PDF-Dokumente, die anwendungsobjektspezifische Skripte enthalten, werden nicht gerendert.

Die folgenden Abschnitte zeigen, wie Sie einen Formularentwurf mithilfe eines URI-Werts an den Output-Dienst übergeben:

* [Erstellen von PDF-Dokumenten](creating-document-output-streams.md#creating-pdf-documents)
* [Erstellen von PDF/A-Dokumenten](creating-document-output-streams.md#creating-pdf-a-documents)

Die folgenden Abschnitte zeigen, wie Sie einen Formularentwurf in einem `com.adobe.idp.Document` instance:

* [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Erstellen von PDF-Dokumenten mit Fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

Bei der Entscheidung, welche Technik verwendet werden soll, sollten Sie den Formularentwurf von einem anderen AEM Forms-Dienst beziehen und dann in einem `com.adobe.idp.Document` -Instanz. Beide *Übergeben von Dokumenten an den Output-Dienst* und *Erstellen von PDF-Dokumenten mit Fragmenten* -Abschnitte zeigen, wie Sie einen Formularentwurf von einem anderen AEM Forms-Dienst erhalten. Im ersten Abschnitt wird der Formularentwurf aus Content Services (nicht mehr unterstützt) abgerufen. Der zweite Abschnitt ruft den Formularentwurf vom Assembler-Dienst ab.

Wenn Sie den Formularentwurf von einem festen Speicherort wie dem Dateisystem erhalten, können Sie beide Verfahren verwenden. Das heißt, Sie können den URI-Wert für eine XDP-Datei angeben oder eine `com.adobe.idp.Document` -Instanz.

Um beim Erstellen eines PDF-Dokuments einen URI-Wert zu übergeben, der den Speicherort des Formularentwurfs angibt, verwenden Sie die `generatePDFOutput` -Methode. Ebenso müssen Sie eine `com.adobe.idp.Document` -Instanz beim Erstellen eines PDF-Dokuments für den Output-Dienst verwenden Sie die `generatePDFOutput2` -Methode.

Wenn Sie einen Ausgabestream an einen Netzwerkdrucker senden, können Sie auch eine der beiden Methoden verwenden. So senden Sie einen Ausgabestream an einen Drucker, indem Sie eine `com.adobe.idp.Document` -Instanz, die einen Formularentwurf enthält, verwenden Sie die `sendToPrinter2`-Methode. Um einen Ausgabestream an einen Drucker zu senden, indem ein URI-Wert übergeben wird, verwenden Sie die `sendToPrinter`-Methode. Die *Senden von Druck-Streams an Drucker* -Abschnitt verwendet die `sendToPrinter` -Methode.

Sie können diese Aufgaben mithilfe des Output-Dienstes ausführen:

* [Erstellen von PDF-Dokumenten](creating-document-output-streams.md#creating-pdf-documents)
* [Erstellen von PDF/A-Dokumenten](creating-document-output-streams.md#creating-pdf-a-documents)
* [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Erstellen von PDF-Dokumenten mit Fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)
* [Drucken in Dateien](creating-document-output-streams.md#printing-to-files)
* [Senden von Druck-Streams an Drucker](creating-document-output-streams.md#sending-print-streams-to-printers)
* [Erstellen mehrerer Ausgabedateien](creating-document-output-streams.md#creating-multiple-output-files)
* [Erstellen von Suchregeln](creating-document-output-streams.md#creating-search-rules)
* [Reduzieren von PDF-Dokumenten](creating-document-output-streams.md#flattening-pdf-documents)

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Erstellen von PDF-Dokumenten {#creating-pdf-documents}

Sie können den Output-Dienst verwenden, um ein PDF-Dokument zu erstellen, das auf einem Formularentwurf und den von Ihnen bereitgestellten XML-Formulardaten basiert. Das vom Output-Dienst erstellte PDF-Dokument ist kein interaktives PDF-Dokument. Benutzer können keine Formulardaten eingeben oder ändern.

Wenn Sie ein PDF-Dokument für die Langzeitspeicherung erstellen möchten, wird empfohlen, ein PDF/A-Dokument zu erstellen. (Siehe [Erstellen von PDF/A-Dokumenten](creating-document-output-streams.md#creating-pdf-a-documents).

Verwenden Sie den Forms-Dienst, um ein interaktives PDF-Formular zu erstellen, mit dem Benutzer Daten eingeben können. (Siehe [Rendern interaktiver PDF forms](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms).

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument zu erstellen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Festlegen von PDF-Laufzeitoptionen.
1. Festlegen von Rendering-Laufzeitoptionen.
1. Erstellen Sie ein PDF-Dokument.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie eine `OutputServiceService` -Objekt.

**Referenzieren einer XML-Datenquelle**

Um Daten mit dem Formularentwurf zusammenzuführen, müssen Sie eine XML-Datenquelle referenzieren, die Daten enthält. Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

Beachten Sie das folgende Beispielformular für einen Kreditantrag.

![cp_cp_loanformdata](assets/cp_cp_loanformdata.png)

Um Daten in diesem Formularentwurf zusammenzuführen, müssen Sie eine XML-Datenquelle erstellen, die dem Formular entspricht. Die folgende XML-Datei stellt eine XDP-XML-Datenquelle dar, die dem Beispiel-Hypothekenantragsformular entspricht.

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

**Festlegen von PDF-Laufzeitoptionen**

Legen Sie die Datei-URI-Option beim Erstellen eines PDF-Dokuments fest. Diese Option gibt den Namen und Speicherort der PDF-Datei an, die der Output-Dienst generiert.

>[!NOTE]
>
>Anstatt die Laufzeitoption für den Datei-URI festzulegen, können Sie das PDF-Dokument programmgesteuert vom komplexen Datentyp abrufen, der vom Output-Dienst zurückgegeben wird. Durch Festlegen der Laufzeitoption für den Datei-URI müssen Sie jedoch keine Anwendungslogik erstellen, die das PDF-Dokument programmgesteuert abruft.

**Festlegen von Rendering-Laufzeitoptionen**

Beim Erstellen eines PDF-Dokuments können Sie Laufzeitoptionen für das Rendern festlegen. Obwohl diese Optionen nicht erforderlich sind (im Gegensatz zu erforderlichen PDF-Laufzeitoptionen), können Sie Aufgaben wie die Leistungsverbesserung des Output-Dienstes ausführen. Beispielsweise können Sie den Formularentwurf zwischenspeichern, den der Output-Dienst verwendet, um seine Leistung zu verbessern.

Wenn Sie ein getaggtes Acrobat-Formular als Eingabe verwenden, können Sie die Java- oder Webdienst-API des Output-Dienstes nicht verwenden, um die getaggte Einstellung zu deaktivieren. Wenn Sie versuchen, diese Option programmgesteuert auf `false`, ist das PDF-Ergebnisdokument weiterhin mit Tags versehen.

>[!NOTE]
>
>Wenn Sie keine Rendering-Laufzeitoptionen festlegen, werden Standardwerte verwendet. Informationen zum Rendern von Laufzeitoptionen finden Sie in der `RenderOptionsSpec` -Klassenreferenz. (Siehe [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

**PDF-Dokument generieren**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die Formulardaten enthält, und Laufzeitoptionen festgelegt haben, können Sie den Output-Dienst aufrufen, wodurch ein PDF-Dokument generiert wird.

Beim Generieren eines PDF-Dokuments geben Sie URI-Werte an, die vom Output-Dienst zum Erstellen eines PDF-Dokuments erforderlich sind. Ein Formularentwurf kann in Speicherorten wie dem Serverdateisystem oder im Rahmen einer AEM Forms-Anwendung gespeichert werden. Ein Formularentwurf (oder andere Ressourcen wie eine Bilddatei), der Teil einer Forms-Anwendung ist, kann mithilfe des Inhaltsstamm-URI-Werts referenziert werden `repository:///`. Betrachten Sie beispielsweise den folgenden Formularentwurf mit dem Namen *Loan.xdp* innerhalb einer Forms-Anwendung mit dem Namen *Anwendungen/FormsApplication*:

![cp_cp_formrepository](assets/cp_cp_formrepository.png)

Um auf die in der vorherigen Abbildung dargestellte Datei &quot;Loan.xdp&quot;zuzugreifen, geben Sie `repository:///Applications/FormsApplication/1.0/FormsFolder/` als dritten Parameter, der an die `OutputClient` -Objekt `generatePDFOutput` -Methode. Geben Sie den Namen des Formulars an (*Loan.xdp*) als zweiten Parameter, der an die `OutputClient` -Objekt `generatePDFOutput` -Methode.

Wenn die XDP-Datei Bilder (oder andere Ressourcen wie Fragmente) enthält, platzieren Sie die Ressourcen im selben Anwendungsordner wie die XDP-Datei. AEM Forms verwendet den Inhaltsstamm-URI als Basispfad, um Verweise auf Bilder aufzulösen. Wenn die Datei &quot;Loan.xdp&quot;beispielsweise ein Bild enthält, stellen Sie sicher, dass Sie das Bild in `Applications/FormsApplication/1.0/FormsFolder/`.

>[!NOTE]
>
>Sie können beim Aufrufen der `OutputClient` -Objekt `generatePDFOutput` oder `generatePrintedOutput` -Methoden.

>[!NOTE]
>
>Einen vollständigen Schnellstart zum Erstellen eines PDF-Dokuments durch Referenzieren einer XDP-Datei in einer Forms-Anwendung finden Sie unter [Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments basierend auf einer Anwendungs-XDP-Datei mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api).

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, gibt er verschiedene Datenelemente zurück, z. B. Status-XML-Daten, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Erstellen eines PDF-Dokuments mit der Java-API](creating-document-output-streams.md#create-a-pdf-document-using-the-java-api)

[Erstellen eines PDF-Dokuments mit der Webdienst-API](creating-document-output-streams.md#create-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen eines PDF-Dokuments mit der Java-API {#create-a-pdf-document-using-the-java-api}

Erstellen Sie ein PDF-Dokument mithilfe der Ausgabe-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des PDF-Dokuments mithilfe des Konstruktors verwendet wird, und einen string -Wert übergibt, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein Objekt `com.adobe.idp.Document`, indem Sie den Konstruktor verwenden. Übergeben Sie die `java.io.FileInputStream` -Objekt.

1. Festlegen von PDF-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Datei-URI fest, indem Sie die `PDFOutputOptionsSpec` -Objekt `setFileURI` -Methode. Übergeben Sie einen string -Wert, der den Speicherort der vom Output-Dienst generierten PDF-Datei angibt. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie die `RenderOptionsSpec` -Objekt `setCacheEnabled` und übergeben `true`.

   >[!NOTE]
   >
   >Sie können die PDF-Dokumentversion nicht mithilfe der `RenderOptionsSpec` -Objekt `setPdfVersion` -Methode, wenn das Eingabedokument ein Acrobat-Formular (ein in Acrobat erstelltes Formular) oder ein XFA-Dokument ist, das signiert oder zertifiziert ist. Das PDF-Ausgabedokument behält die Originalversion des PDF bei. Ebenso können Sie die getaggte Adobe PDF-Option nicht festlegen, indem Sie die `RenderOptionsSpec` -Objekt `setTaggedPDF`* -Methode, wenn das Eingabedokument ein Acrobat-Formular oder ein signiertes oder zertifiziertes XFA-Dokument ist. *

   >[!NOTE]
   >
   >Sie können die Option für linearisiertes PDF nicht mithilfe der `RenderOptionsSpec` -Objekt `setLinearizedPDF` -Methode, wenn das PDF-Eingabedokument zertifiziert oder digital signiert ist. (Siehe [Digitales Signieren von PDF-Dokumenten ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.*

1. Erstellen Sie ein PDF-Dokument.

   Erstellen Sie ein PDF-Dokument, indem Sie die `OutputClient` -Objekt `generatePDFOutput` -Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `com.adobe.idp.Document` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput` -Methode gibt eine `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

   >[!NOTE]
   >
   >Beim Generieren eines PDF-Dokuments durch Aufrufen der `generatePDFOutput` beachten Sie, dass Sie keine Daten mit einem XFA-PDF-Formular zusammenführen können, das signiert oder zertifiziert ist. (Siehe [Digitales Signieren und Zertifizieren von Dokumenten ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.*

   >[!NOTE]
   >
   >Die `OutputResult` -Objekt `getRecordLevelMetaDataList` Methodenzurückgaben `null`*.*

   >[!NOTE]
   >
   >Sie können auch ein PDF-Dokument erstellen, indem Sie die `OutputClient` -Objekt `generatePDFOutput2` -Methode. (Siehe [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.*

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Abrufen einer `com.adobe.idp.Document` -Objekt, das den Status der `generatePDFOutput` -Vorgang durch Aufrufen der `OutputResult` -Objekt `getStatusDoc` -Methode. Diese Methode gibt Status-XML-Daten zurück, die angeben, ob der Vorgang erfolgreich war.
   * Erstellen Sie eine `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das von der `getStatusDoc` -Methode).

   Obwohl der Output-Dienst das PDF-Dokument an den Speicherort schreibt, der durch das an das `PDFOutputOptionsSpec` -Objekt `setFileURI` -Methode verwenden, können Sie das PDF/A-Dokument programmgesteuert abrufen, indem Sie die `OutputResult` -Objekt `getGeneratedDoc` -Methode.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): Erstellen eines PDF-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen eines PDF-Dokuments mit der Webdienst-API {#create-a-pdf-document-using-the-web-service-api}

Erstellen Sie ein PDF-Dokument mithilfe der Output API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost`* mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird. *

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie eine `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `OutputServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `OutputServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern von XML-Daten verwendet, die mit dem PDF-Dokument zusammengeführt werden.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort der XML-Datei darstellt, die Formulardaten enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Festlegen von PDF-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Datei-URI fest, indem Sie einen Zeichenfolgenwert zuweisen, der den Speicherort der vom Output-Dienst generierten PDF-Datei angibt. `PDFOutputOptionsSpec` -Objekt `fileURI` Datenelement. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie den Wert zuweisen. `true` der `RenderOptionsSpec` -Objekt `cacheEnabled` Datenelement.

   >[!NOTE]
   >
   >Sie können die PDF-Dokumentversion nicht mithilfe der `RenderOptionsSpec` -Objekt `setPdfVersion` -Methode, wenn das Eingabedokument ein Acrobat-Formular (ein in Acrobat erstelltes Formular) oder ein XFA-Dokument ist, das signiert oder zertifiziert ist. Das PDF-Ausgabedokument behält die Originalversion des PDF bei. Ebenso können Sie die getaggte Adobe PDF-Option nicht festlegen, indem Sie die `RenderOptionsSpec` -Objekt `setTaggedPDF`* Methode, wenn das Eingabedokument ein Acrobat-Formular oder ein signiertes oder zertifiziertes XFA-Dokument ist.*

   >[!NOTE]
   >
   >Sie können die Option für linearisiertes PDF nicht mithilfe der `RenderOptionsSpec` -Objekt `linearizedPDF` -Element, wenn das PDF-Eingabedokument zertifiziert oder digital signiert ist. (Siehe [Digitales Signieren von PDF-Dokumenten ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.*

1. Erstellen Sie ein PDF-Dokument.

   Erstellen Sie ein PDF-Dokument, indem Sie die `OutputServiceService` -Objekt `generatePDFOutput`-Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `BLOB` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

   >[!NOTE]
   >
   >Beim Generieren eines PDF-Dokuments durch Aufrufen der `generatePDFOutput` beachten Sie, dass Sie keine Daten mit einem XFA-PDF-Formular zusammenführen können, das signiert oder zertifiziert ist. (Siehe [Digitales Signieren und Zertifizieren von Dokumenten ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.*

   >[!NOTE]
   >
   >Sie können auch ein PDF-Dokument erstellen, indem Sie die `OutputClient` -Objekt `generatePDFOutput2` -Methode. (Siehe [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.*

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `OutputServiceService` -Objekt `generatePDFOutput` -Methode (der achte Parameter). Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` `field`.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

   Siehe auch

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

   >[!NOTE]
   >
   >Die `OutputServiceService` -Objekt `generateOutput` -Methode veraltet ist.

## Erstellen von PDF/A-Dokumenten {#creating-pdf-a-documents}

Sie können den Output-Dienst verwenden, um ein PDF/A-Dokument zu erstellen. Da PDF/A ein Archivierungsformat für die langfristige Beibehaltung des Dokumentinhalts ist, werden alle Schriftarten eingebettet und die Datei unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Darüber hinaus enthält ein PDF/A-Dokument keine Audio- und Videoinhalte. Wie andere Output-Dienstaufgaben stellen Sie sowohl einen Formularentwurf als auch Daten bereit, die mit einem Formularentwurf zusammengeführt werden sollen, um ein PDF/A-Dokument zu erstellen.

Die PDF/A-1-Spezifikation besteht aus zwei Konformitätsstufen, nämlich a und b. Der wesentliche Unterschied zwischen den beiden besteht in der Unterstützung der logischen Struktur (Zugänglichkeit), die für die Konformitätsstufe b nicht erforderlich ist. Unabhängig von der Konformitätsstufe bestimmt PDF/A-1, dass alle Schriftarten in das generierte PDF/A-Dokument eingebettet sind.

Obwohl PDF/A der Standard für die Archivierung von PDF-Dokumenten ist, ist es nicht erforderlich, PDF/A für die Archivierung zu verwenden, wenn ein Standarddokument für die PDF Ihren Unternehmensanforderungen entspricht. Der PDF/A-Standard dient der Erstellung einer PDF-Datei, die über einen längeren Zeitraum gespeichert werden kann und die Anforderungen an die Dokumentenerhaltung erfüllt. Beispielsweise kann eine URL nicht in eine PDF/A eingebettet werden, da die URL im Laufe der Zeit ungültig werden kann.

Ihr Unternehmen muss seine eigenen Anforderungen, die Zeitdauer, in der Sie das Dokument aufbewahren möchten, Überlegungen zur Dateigröße und Ihre eigene Archivierungsstrategie beurteilen. Mit dem DocConverter-Dienst können Sie programmatisch feststellen, ob ein PDF-Dokument PDF/A-kompatibel ist. (Siehe [Programmatische Bestimmung der PDF/A-Kompatibilität](/help/forms/developing/pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).

Ein PDF/A-Dokument muss die im Formularentwurf angegebene Schriftart verwenden und Schriften können nicht ersetzt werden. Wenn daher eine Schriftart, die sich in einem PDF-Dokument befindet, auf dem Host-Betriebssystem (Betriebssystem) nicht verfügbar ist, tritt eine Ausnahme auf.

Wenn ein PDF/A-Dokument in Acrobat geöffnet wird, wird eine Meldung angezeigt, die bestätigt, dass es sich um ein PDF/A-Dokument handelt, wie in der folgenden Abbildung dargestellt.

![cp_cp_pdfamessage](assets/cp_cp_pdfamessage.png)

>[!NOTE]
>
>Die AIIM-Website verfügt über einen Abschnitt mit häufig gestellten Fragen zur PDF/A, auf den Sie unter [https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml](https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml).

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_64).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um ein PDF/A-Dokument zu erstellen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Festlegen von PDF/A-Laufzeitoptionen.
1. Festlegen von Rendering-Laufzeitoptionen.
1. Erstellen Sie ein PDF/A-Dokument.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein benutzerdefiniertes Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie eine `OutputServiceService` -Objekt.

**Referenzieren einer XML-Datenquelle**

Um Daten mit dem Formularentwurf zusammenzuführen, müssen Sie eine XML-Datenquelle referenzieren, die Daten enthält. Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

**Festlegen von PDF/A-Laufzeitoptionen**

Sie können die Option Datei-URI beim Erstellen eines PDF/A-Dokuments festlegen. Der URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient. Wenn Sie also C:\Adobe festlegen, wird die Datei in den Ordner auf dem Server geschrieben, nicht in den Client-Computer. Der URI gibt den Namen und Speicherort der PDF/A-Datei an, die der Output-Dienst generiert.

**Festlegen von Rendering-Laufzeitoptionen**

Beim Erstellen von PDF/A-Dokumenten können Sie Laufzeitoptionen für das Rendern festlegen. Zwei PDF/A-Optionen, die Sie festlegen können, sind die `PDFAConformance` und `PDFARevisionNumber` -Werte. Die `PDFAConformance` -Wert bezieht sich darauf, wie ein PDF-Dokument Anforderungen erfüllt, die angeben, wie langfristige elektronische Dokumente beibehalten werden. Gültige Werte für diese Option sind `A` und `B`. Informationen zur Konformität von Level a und B finden Sie in der ISO-Spezifikation PDF/A-1 mit dem Titel *ISO 19005-1 Dokumentenmanagement*.

Die `PDFARevisionNumber` -Wert bezieht sich auf die Revisionsnummer eines PDF/A-Dokuments. Informationen zur Revisionsnummer eines PDF/A-Dokuments finden Sie in der ISO-Spezifikation PDF/A-1 mit dem Titel *ISO 19005-1 Dokumentenmanagement*.

>[!NOTE]
>
>Sie können die getaggte Adobe PDF-Option nicht auf `false` beim Erstellen eines PDF/A 1A-Dokuments. PDF/A 1A ist immer ein getaggtes PDF-Dokument. Außerdem können Sie die getaggte Adobe PDF-Option nicht auf `true` beim Erstellen eines PDF/A 1B-Dokuments. PDF/A 1B ist immer ein PDF-Dokument ohne Tags.

**Erstellen eines PDF/A-Dokuments**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die Formulardaten enthält, und Laufzeitoptionen festgelegt haben, können Sie den Output-Dienst aufrufen, wodurch ein PDF/A-Dokument generiert wird.

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, gibt er verschiedene Datenelemente wie XML-Daten zurück, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Erstellen eines PDF/A-Dokuments mit der Java-API](creating-document-output-streams.md#create-a-pdf-a-document-using-the-java-api)

[Erstellen eines PDF/A-Dokuments mithilfe der Webdienst-API](creating-document-output-streams.md#create-a-pdf-a-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen eines PDF/A-Dokuments mit der Java-API {#create-a-pdf-a-document-using-the-java-api}

Erstellen Sie ein PDF/A-Dokument mithilfe der Ausgabe-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des PDF/A-Dokuments mithilfe seines Konstruktors verwendet wird, und einen string -Wert übergibt, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von PDF/A-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Datei-URI fest, indem Sie die `PDFOutputOptionsSpec` -Objekt `setFileURI` -Methode. Übergeben Sie einen string -Wert, der den Speicherort der vom Output-Dienst generierten PDF-Datei angibt. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die `PDFAConformance` -Wert durch Aufrufen der `RenderOptionsSpec` -Objekt `setPDFAConformance` -Methode und Übergeben einer `PDFAConformance` enum -Wert, der die Konformitätsstufe angibt. Um beispielsweise Konformitätsstufe A anzugeben, übergeben Sie `PDFAConformance.A`.
   * Legen Sie die `PDFARevisionNumber` -Wert durch Aufrufen der `RenderOptionsSpec` -Objekt `setPDFARevisionNumber` Methode und Übergabe `PDFARevisionNumber.Revision_1`.

   >[!NOTE]
   >
   >Die PDF-Version eines PDF/A-Dokuments ist 1.4, unabhängig davon, welchen Wert Sie für die `RenderOptionsSpec` -Objekt `setPdfVersion`*-Methode.*

1. Erstellen Sie ein PDF/A-Dokument.

   Erstellen Sie ein PDF/A-Dokument, indem Sie die `OutputClient` -Objekt `generatePDFOutput` -Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF/A-Dokument zu generieren, geben Sie `TransformationFormat.PDFA`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `com.adobe.idp.Document` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput` -Methode gibt eine `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

   >[!NOTE]
   >
   >Die `OutputResult` -Objekt `getRecordLevelMetaDataList` Methodenzurückgaben `null`*. *

   >[!NOTE]
   >
   >Sie können auch ein PDF/A-Dokument erstellen, indem Sie die `OutputClient` -Objekt `generatePDFOutput`2 Methode. (Siehe [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, das den Status der `generatePDFOutput` -Methode durch Aufrufen der `OutputResult` -Objekt `getStatusDoc` -Methode.
   * Erstellen Sie eine `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das von der `getStatusDoc` -Methode).

   >[!NOTE]
   >
   >Obwohl der Output-Dienst das PDF/A-Dokument an den Speicherort schreibt, der durch das an das `PDFOutputOptionsSpec` -Objekt `setFileURI` -Methode verwenden, können Sie das PDF/A-Dokument programmgesteuert abrufen, indem Sie die `OutputResult` -Objekt `getGeneratedDoc`* Methode.*

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Erstellen eines PDF/A-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-a-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Erstellen eines PDF/A-Dokuments mithilfe der Webdienst-API {#create-a-pdf-a-document-using-the-web-service-api}

Erstellen Sie ein PDF/A-Dokument mithilfe der Output API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost`* mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird. *

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie eine `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `OutputServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `OutputServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern von Daten verwendet, die mit dem PDF/A-Dokument zusammengeführt werden.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Festlegen von PDF/A-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Datei-URI fest, indem Sie einen Zeichenfolgenwert zuweisen, der den Speicherort der vom Output-Dienst generierten PDF-Datei angibt. `PDFOutputOptionsSpec` -Objekt `fileURI` Datenelement. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, nicht zum Clientcomputer

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die `PDFAConformance` Wert durch Zuweisung eines `PDFAConformance` enum -Wert auf `RenderOptionsSpec` -Objekt `PDFAConformance` Datenelement. Um beispielsweise Konformitätsstufe A anzugeben, weisen Sie `PDFAConformance.A` zu diesem Datenelement hinzu.
   * Legen Sie die `PDFARevisionNumber` Wert durch Zuweisung eines `PDFARevisionNumber` enum -Wert auf `RenderOptionsSpec` -Objekt `PDFARevisionNumber` Datenelement. Zuweisen `PDFARevisionNumber.Revision_1` zu diesem Datenelement hinzu.

   >[!NOTE]
   >
   >Die PDF-Version eines PDF/A-Dokuments ist 1.4, unabhängig vom angegebenen Wert.

1. Erstellen Sie ein PDF/A-Dokument.

   Erstellen Sie ein PDF-Dokument, indem Sie die `OutputServiceService` -Objekt `generatePDFOutput`-Methode verwenden und die folgenden Werte übergeben:

   * Ein Enumerationswert TransformationFormat . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDFA`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `BLOB` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)

   >[!NOTE]
   >
   >Sie können auch ein PDF/A-Dokument erstellen, indem Sie die `OutputClient` -Objekt `generatePDFOutput`2 Methode. (Siehe [Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `OutputServiceService` -Objekt `generatePDFOutput` -Methode (der achte Parameter). Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Übergeben von Dokumenten in Content Services (nicht mehr unterstützt) an den Output-Dienst {#passing-documents-located-in-content-services-deprecated-to-the-output-service}

Der Output-Dienst rendert ein nicht interaktives PDF-Formular, das auf einem Formularentwurf basiert, der normalerweise als XDP-gespeichert und in Designer erstellt wird. Sie können eine `com.adobe.idp.Document` -Objekt, das den Formularentwurf für den Output-Dienst enthält. Der Output-Dienst rendert dann den Formularentwurf im `com.adobe.idp.Document` -Objekt.

Der Vorteil der Übergabe eines `com.adobe.idp.Document` Objekt an den Output-Dienst ist, dass andere AEM Forms-Dienstvorgänge eine `com.adobe.idp.Document` -Instanz. Das heißt, Sie können eine `com.adobe.idp.Document` -Instanz von einem anderen Dienstvorgang aus und rendern Sie ihn. Angenommen, eine XDP-Datei wird in einem Knoten von Content Services (veraltet) gespeichert, der `/Company Home/Form Designs`, wie in der folgenden Abbildung dargestellt.

Sie können &quot;Loan.xdp&quot;programmgesteuert aus Content Services (nicht mehr unterstützt) abrufen und die XDP-Datei in einem `com.adobe.idp.Document` -Objekt.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Führen Sie die folgenden Aufgaben aus, um ein von Content Services (nicht mehr unterstützt) gespeichertes Dokument an den Output-Dienst zu übergeben:

1. Projektdateien einschließen.
1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus Content Services ab (nicht mehr unterstützt).
1. Rendern Sie das nicht interaktive PDF-Formular.
1. Führen Sie eine Aktion mit dem Datenstrom aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen einer Ausgabe und eines Document Management Client-API-Objekts**

Bevor Sie einen Output-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie ein Output Client-API-Objekt. Da mit diesem Workflow eine XDP-Datei aus Content Services (nicht mehr unterstützt) abgerufen wird, erstellen Sie ein Document Management-API-Objekt.

**Abrufen des Formularentwurfs aus Content Services (nicht mehr unterstützt)**

Rufen Sie die XDP-Datei aus Content Services (nicht mehr unterstützt) ab, indem Sie die Java- oder Webdienst-API verwenden. Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document` Instanz (oder `BLOB` -Instanz, wenn Sie Webdienste verwenden). Anschließend können Sie die `com.adobe.idp.Document` -Instanz zum Output-Dienst.

**Nicht interaktives PDF-Formular rendern**

Übergeben Sie zum Rendern eines nicht interaktiven Formulars die Variable `com.adobe.idp.Document` -Instanz, die von Content Services (nicht mehr unterstützt) an den Output-Dienst zurückgegeben wurde.

>[!NOTE]
>
>Zwei neue Methoden namens `generatePDFOutput2`und g `eneratePrintedOutput2`akzeptieren `com.adobe.idp.Document` -Objekt, das einen Formularentwurf enthält. Sie können auch eine `com.adobe.idp.Document`, der den Formularentwurf beim Senden eines Druckstreams an einen Netzwerkdrucker an den Output-Dienst enthält.

**Ausführen einer Aktion mit dem Formulardatenstream**

Sie können das nicht interaktive Formular als PDF-Datei speichern. Das Formular kann in Adobe Reader oder Acrobat angezeigt werden.

**Siehe auch**

[Übergeben von Dokumenten an den Output-Dienst mithilfe der Java-API](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-java-api)

[Übergeben von Dokumenten an den Output-Dienst mithilfe der Webdienst-API](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Erstellen von PDF-Dokumenten mit Fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

### Übergeben von Dokumenten an den Output-Dienst mithilfe der Java-API {#pass-documents-to-the-output-service-using-the-java-api}

Übergeben Sie ein Dokument, das von Content Services (nicht mehr unterstützt) mithilfe der Output-Dienst- und Content Services-API (nicht mehr unterstützt) abgerufen wurde:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar und adobe-contentservices-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den Formularentwurf aus Content Services ab (nicht mehr unterstützt).

   Rufen Sie die `DocumentManagementServiceClientImpl` -Objekt `retrieveContent` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher lautet `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.

   Die `retrieveContent` -Methode gibt eine `CRCResult` -Objekt, das die XDP-Datei enthält. Abrufen einer `com.adobe.idp.Document` -Instanz durch Aufrufen der `CRCResult` -Objekt `getDocument` -Methode.

1. Rendern Sie das nicht interaktive PDF-Formular.

   Rufen Sie die `OutputClient` -Objekt `generatePDFOutput2` -Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen wie Bilder befinden.
   * A `com.adobe.idp.Document` -Objekt, das den Formularentwurf darstellt (verwenden Sie die vom `CRCResult` -Objekt `getDocument` -Methode).
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `com.adobe.idp.Document` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput2` -Methode gibt eine `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

   * Abrufen einer `com.adobe.idp.Document` -Objekt, das das nicht interaktive Formular durch Aufrufen der `OutputResult` -Objekt `getGeneratedDoc` -Methode.
   * Erstellen Sie eine `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das von der `getGeneratedDoc` -Methode).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Übergeben von Dokumenten an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Schnellstart (SOAP-Modus): Übergeben von Dokumenten an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Übergeben von Dokumenten an den Output-Dienst mithilfe der Webdienst-API {#pass-documents-to-the-output-service-using-the-web-service-api}

Übergeben Sie ein Dokument, das von Content Services (nicht mehr unterstützt) mithilfe der Output-Dienst- und Content Services-API (nicht mehr unterstützt) abgerufen wurde (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da diese Client-Anwendung zwei AEM Forms-Dienste aufruft, erstellen Sie zwei Dienstverweise. Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Output-Dienst verknüpft ist: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Document Management-Dienst verknüpft ist: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Da die `BLOB` Datentyp für beide Dienstverweise verwendet wird, müssen Sie die `BLOB` Datentyp bei der Verwendung. Im entsprechenden Webdienst-Schnellstart werden alle `BLOB` -Instanzen sind vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen `localhost`* mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird. *

1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.

   * Erstellen Sie eine `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `OutputServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`). Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `OutputServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für die `DocumentManagementServiceClient`* Service-Client. *

1. Rufen Sie den Formularentwurf aus Content Services ab (nicht mehr unterstützt).

   Abrufen von Inhalten durch Aufrufen der `DocumentManagementServiceClient` -Objekt `retrieveContent` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Store angibt, in dem der Inhalt hinzugefügt wird. Der Standardspeicher lautet `SpacesStore`. Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der den vollständig qualifizierten Pfad des abzurufenden Inhalts angibt (z. B. `/Company Home/Form Designs/Loan.xdp`). Dieser Wert ist ein obligatorischer Parameter.
   * Ein string -Wert, der die Version angibt. Dieser Wert ist ein optionaler Parameter und Sie können eine leere Zeichenfolge übergeben. In diesem Fall wird die neueste Version abgerufen.
   * Ein string -Ausgabeparameter, der den Wert des Durchsuchen-Links speichert.
   * A `BLOB` Ausgabeparameter, der den Inhalt speichert. Sie können diesen Ausgabeparameter verwenden, um den Inhalt abzurufen.
   * A `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` Ausgabeparameter, der Inhaltsattribute speichert.
   * A `CRCResult` Ausgabeparameter. Anstatt dieses Objekt zu verwenden, können Sie die `BLOB` Ausgabeparameter zum Abrufen des Inhalts.

1. Rendern Sie das nicht interaktive PDF-Formular.

   Rufen Sie die `OutputServiceClient` -Objekt `generatePDFOutput2` -Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen wie Bilder befinden.
   * A `BLOB` -Objekt, das den Formularentwurf darstellt (verwenden Sie die `BLOB` -Instanz, die von Content Services (nicht mehr unterstützt) zurückgegeben wird.
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `BLOB` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ausgabe `BLOB` -Objekt, das von der `generatePDFOutput2` -Methode. Die `generatePDFOutput2` -Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ausgabe `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

   Die `generatePDFOutput2` -Methode gibt eine `BLOB` -Objekt, das das nicht interaktive PDF-Formular enthält.

1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort des interaktiven PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt, das aus dem `generatePDFOutput2` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Übergeben von Dokumenten im Repository an den Output-Dienst {#passing-documents-located-in-the-repository-to-the-output-service}

Der Output-Dienst rendert ein nicht interaktives PDF-Formular, das auf einem Formularentwurf basiert, der normalerweise als XDP-gespeichert und in Designer erstellt wird. Sie können eine `com.adobe.idp.Document` -Objekt, das den Formularentwurf für den Output-Dienst enthält. Der Output-Dienst rendert dann den Formularentwurf im `com.adobe.idp.Document` -Objekt.

Der Vorteil der Übergabe eines `com.adobe.idp.Document` Objekt an den Output-Dienst ist, dass andere AEM Forms-Dienstvorgänge eine `com.adobe.idp.Document` -Instanz. Das heißt, Sie können eine `com.adobe.idp.Document` -Instanz von einem anderen Dienstvorgang aus und rendern Sie ihn. Angenommen, eine XDP-Datei wird im AEM Forms-Repository gespeichert, wie in der folgenden Abbildung dargestellt.

![pd_pd_formrepository](assets/pd_pd_formrepository.png)

Die *FormsFolder* -Ordner ist ein benutzerdefinierter Speicherort im AEM Forms-Repository (dieser Speicherort ist ein Beispiel und ist standardmäßig nicht vorhanden). In diesem Beispiel befindet sich ein Formularentwurf namens &quot;Loan.xdp&quot;in diesem Ordner. Neben dem Formularentwurf können auch andere Formularkomponenten wie Bilder an dieser Stelle gespeichert werden. Der Pfad zu einer Ressource im AEM Forms-Repository lautet:

`Applications/Application-name/Application-version/Folder.../Filename`

Sie können &quot;Loan.xdp&quot;programmgesteuert aus dem AEM Forms-Repository abrufen und an den Output-Dienst in einem `com.adobe.idp.Document` -Objekt.

Sie können eine PDF basierend auf einer XDP-Datei im Repository auf zwei Arten erstellen. Sie können den XDP-Speicherort als Referenz übergeben oder Sie können die XDP programmgesteuert aus dem Repository abrufen und an den Output-Dienst in einer XDP-Datei übergeben.

[Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments basierend auf einer Anwendungs-XDP-Datei mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api) (zeigt, wie der Speicherort der XDP-Datei als Referenz übergeben wird).

[Schnellstart (EJB-Modus): Übergeben eines Dokuments im AEM Forms-Repository an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (zeigt, wie Sie die XDP-Datei programmgesteuert aus dem AEM Forms-Repository abrufen und an den Output-Dienst in einem `com.adobe.idp.Document` -Instanz). (In diesem Abschnitt wird beschrieben, wie Sie diese Aufgabe durchführen.)

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

Führen Sie die folgenden Aufgaben aus, um ein vom AEM Forms-Repository abgerufenes Dokument an den Output-Dienst zu übergeben:

1. Projektdateien einschließen.
1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.
1. Rufen Sie den Formularentwurf aus dem AEM Forms-Repository ab.
1. Rendern Sie das nicht interaktive PDF-Formular.
1. Führen Sie eine Aktion mit dem Datenstrom aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen einer Ausgabe und eines Document Management Client-API-Objekts**

Bevor Sie einen Output-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie ein Output Client-API-Objekt. Da mit diesem Workflow eine XDP-Datei aus Content Services (nicht mehr unterstützt) abgerufen wird, erstellen Sie ein Document Management-API-Objekt.

**Abrufen des Formularentwurfs aus dem AEM Forms-Repository**

Rufen Sie die XDP-Datei mithilfe der Repository-API aus dem AEM Forms-Repository ab. (Siehe [Lesen von Ressourcen](/help/forms/developing/aem-forms-repository.md#reading-resources).

Die XDP-Datei wird innerhalb einer `com.adobe.idp.Document` Instanz (oder `BLOB` -Instanz, wenn Sie Webdienste verwenden). Anschließend können Sie die `com.adobe.idp.Document` -Instanz des Output-Dienstes.

**Nicht interaktives PDF-Formular rendern**

Übergeben Sie zum Rendern eines nicht interaktiven Formulars die Variable `com.adobe.idp.Document` -Instanz, die mithilfe der AEM Forms Repository-API zurückgegeben wurde.

>[!NOTE]
>
>Zwei neue Methoden namens `generatePDFOutput2`und `generatePrintedOutput2`akzeptieren `com.adobe.idp.Document`-Objekt, das einen Formularentwurf enthält. Sie können auch eine `com.adobe.idp.Document` , der den Formularentwurf beim Senden eines Druckstreams an einen Netzwerkdrucker an den Output-Dienst enthält.

**Ausführen einer Aktion mit dem Formulardatenstream**

Sie können das nicht interaktive Formular als PDF-Datei speichern. Das Formular kann in Adobe Reader oder Acrobat angezeigt werden.

**Siehe auch**

[Übergeben von Dokumenten im Repository an den Output-Dienst mithilfe der Java-API](creating-document-output-streams.md#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

ResourceRepositoryClient

### Übergeben von Dokumenten im Repository an den Output-Dienst mithilfe der Java-API {#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api}

Übergeben Sie ein aus dem Repository abgerufenes Dokument mithilfe des Output-Dienstes und der Repository-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar und adobe-repository-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie eine Ausgabe und ein Document Management Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.
   * Erstellen Sie ein `DocumentManagementServiceClientImpl`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie den Formularentwurf aus dem AEM Forms-Repository ab.

   Rufen Sie die `ResourceRepositoryClient` -Objekt `readResourceContent` -Methode verwenden und einen string -Wert übergeben, der den URI-Speicherort an die XDP-Datei angibt. Beispiel: `/Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`. Dieser Wert ist ein Pflichtwert. Diese Methode gibt eine `com.adobe.idp.Document` -Instanz, die die XDP-Datei darstellt.

1. Rendern Sie das nicht interaktive PDF-Formular.

   Rufen Sie die `OutputClient` -Objekt `generatePDFOutput2` -Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen wie Bilder befinden. Beispiel: `repository:///Applications/FormsApplication/1.0/FormsFolder/`.
   * A `com.adobe.idp.Document` -Objekt, das den Formularentwurf darstellt (verwenden Sie die vom `ResourceRepositoryClient` -Objekt `readResourceContent` -Methode).
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `com.adobe.idp.Document` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput2` -Methode gibt eine `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

1. Führen Sie eine Aktion mit dem Formulardatenstream aus.

   * Abrufen einer `com.adobe.idp.Document` -Objekt, das das nicht interaktive Formular durch Aufrufen der `OutputResult` -Objekt `getGeneratedDoc` -Methode.
   * Erstellen Sie eine `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das von der `getGeneratedDoc` -Methode).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Übergeben eines Dokuments im AEM Forms-Repository an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Erstellen von PDF-Dokumenten mit Fragmenten {#creating-pdf-documents-using-fragments}

Sie können die Output- und Assembler-Dienste verwenden, um einen Ausgabestream zu erstellen, z. B. ein PDF-Dokument, das auf Fragmenten basiert. Der Assembler-Dienst stellt ein XDP-Dokument zusammen, das auf Fragmenten in mehreren XDP-Dateien basiert. Das assemblierte XDP-Dokument wird an den Output-Dienst übergeben, der ein PDF-Dokument erstellt. Obwohl dieser Workflow ein zu erstellendes PDF-Dokument anzeigt, kann der Output-Dienst für diesen Workflow andere Ausgabetypen wie ZPL generieren. Ein PDF-Dokument dient nur zu Diskussionszwecken.

Die folgende Abbildung zeigt diesen Workflow.

![cp_cp_outputassemblefragments](assets/cp_cp_outputassemblefragments.png)

Vor dem Lesen *Erstellen von PDF-Dokumenten mit Fragmenten* sollten Sie sich mit der Verwendung des Assembler-Dienstes zum Zusammenführen mehrerer XDP-Dokumente vertraut machen. (Siehe [Assemblieren mehrerer XDP-Fragmente](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments).

>[!NOTE]
>
>Sie können auch einen vom Assembler-Dienst zusammengestellten Formularentwurf an den Forms-Dienst anstelle des Output-Dienstes übergeben. Der Hauptunterschied zwischen dem Output-Dienst und dem Forms-Dienst besteht darin, dass der Forms-Dienst interaktive PDF-Dokumente generiert und der Output-Dienst nicht interaktive PDF-Dokumente erzeugt. Außerdem kann der Forms-Dienst keine druckerbasierten Ausgabestreams wie ZPL generieren.

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Um ein auf Fragmenten basierendes PDF-Dokument zu erstellen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output- und Assembler-Client-Objekt.
1. Verwenden Sie den Assembler-Dienst, um den Formularentwurf zu generieren.
1. Verwenden Sie den Output-Dienst, um das PDF-Dokument zu generieren.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Output- und Assembler-Client-Objekts**

Bevor Sie einen Output-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie ein Output Client-API-Objekt. Da dieser Workflow den Assembler-Dienst aufruft, um den Formularentwurf zu erstellen, erstellen Sie außerdem ein Assembler-Client-API-Objekt.

**Verwenden des Assembler-Dienstes zum Generieren des Formularentwurfs**

Verwenden Sie den Assembler-Dienst, um den Formularentwurf mithilfe von Fragmenten zu generieren. Der Assembler-Dienst gibt einen `com.adobe.idp.Document` -Instanz, die den Formularentwurf enthält.

**Verwenden des Output-Dienstes zum Generieren des PDF-Dokuments**

Sie können den Output-Dienst verwenden, um ein PDF-Dokument mit dem Formularentwurf zu generieren, den der Assembler-Dienst erstellt hat. Übergeben Sie die `com.adobe.idp.Document` -Instanz, die der Assembler-Dienst an den Output-Dienst zurückgegeben hat.

**PDF-Dokument als PDF-Datei speichern**

Nachdem der Output-Dienst ein PDF-Dokument generiert hat, können Sie es als PDF-Datei speichern.

**Siehe auch**

[Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-java-api)

[Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Webdienst-API](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Assemblieren mehrerer XDP-Fragmente](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments)

[Erstellen von PDF-Dokumenten](creating-document-output-streams.md#creating-pdf-documents)

### Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API {#create-a-pdf-document-based-on-fragments-using-the-java-api}

Erstellen Sie ein PDF-Dokument basierend auf Fragmenten mithilfe der Output Service-API und der Assembler-Dienst-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output- und Assembler-Client-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Verwenden Sie den Assembler-Dienst, um den Formularentwurf zu generieren.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden erforderlichen Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das zu verwendende DDX-Dokument darstellt.
   * A `java.util.Map` -Objekt, das die XDP-Eingabedateien enthält.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Auftragsprotokollebene.

   Die `invokeDDX` -Methode gibt eine `com.adobe.livecycle.assembler.client.AssemblerResult` -Objekt, das das assemblierte XDP-Dokument enthält. Um das assemblierte XDP-Dokument abzurufen, führen Sie die folgenden Aktionen aus:

   * Rufen Sie die `AssemblerResult` -Objekt `getDocuments` -Methode. Diese Methode gibt eine `java.util.Map` -Objekt.
   * Iteration durch die `java.util.Map` -Objekt, bis Sie das Ergebnis finden `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Extrahieren des assemblierten XDP-Dokuments.


1. Verwenden Sie den Output-Dienst, um das PDF-Dokument zu generieren.

   Rufen Sie die `OutputClient` -Objekt `generatePDFOutput2` -Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen (z. B. Bilder) befinden
   * A `com.adobe.idp.Document` -Objekt, das den Formularentwurf darstellt (verwenden Sie die vom Assembler-Dienst zurückgegebene Instanz)
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält
   * A `RenderOptionsSpec` Objekt, das Laufzeitoptionen zum Rendern enthält
   * Die `com.adobe.idp.Document` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen

   Die `generatePDFOutput2` -Methode gibt eine `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält

1. Speichern Sie das PDF-Dokument als PDF-Datei.

   * Abrufen einer `com.adobe.idp.Document` -Objekt, das das PDF-Dokument darstellt, indem das `OutputResult` -Objekt `getGeneratedDoc` -Methode.
   * Erstellen Sie eine `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt in die Datei ein. (Stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das `getGeneratedDoc` -Methode zurückgegeben.)

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Schnellstart (SOAP-Modus): Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Erstellen eines PDF-Dokuments basierend auf Fragmenten mithilfe der Webdienst-API {#create-a-pdf-document-based-on-fragments-using-the-web-service-api}

Erstellen Sie ein PDF-Dokument basierend auf Fragmenten mithilfe der Output Service-API und der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Output-Dienst verknüpft ist:

   ```as3
    http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1.
   ```

   Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Assembler-Dienst verknüpft ist:

   ```as3
    http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   Da die `BLOB` Datentyp für beide Dienstverweise verwendet wird, müssen Sie die `BLOB` Datentyp bei der Verwendung. Im entsprechenden Webdienst-Schnellstart werden alle `BLOB` -Instanzen sind vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen `localhost`* mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird. *

1. Erstellen Sie ein Output- und Assembler-Client-Objekt.

   * Erstellen Sie eine `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `OutputServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `OutputServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie den Benutzernamen AEM Formulare dem `OutputServiceClient.ClientCredentials.UserName.UserName`-Feld.
      * Weisen Sie den entsprechenden Kennwortwert dem `OutputServiceClient.ClientCredentials.UserName.Password`-Feld.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` der `BasicHttpBindingSecurity.Transport.ClientCredentialType`-Feld.
   * Zuweisen der `BasicHttpSecurityMode.TransportCredentialOnly` Konstantenwert zum `BasicHttpBindingSecurity.Security.Mode`-Feld.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für die `AssemblerServiceClient`* -Objekt. *

1. Verwenden Sie den Assembler-Dienst, um den Formularentwurf zu generieren.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt
   * Die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt, das die erforderlichen Dateien enthält
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX` -Methode gibt eine `AssemblerResult` -Objekt, das die Ergebnisse des Auftrags sowie alle aufgetretenen Ausnahmen enthält. Um das neu erstellte XDP-Dokument abzurufen, führen Sie die folgenden Aktionen aus:

   * Zugriff auf `AssemblerResult` -Objekt `documents` -Feld, das ein `Map` -Objekt, das die resultierenden PDF-Dokumente enthält.
   * Iteration durch die `Map` -Objekt, um den zusammengestellten Formularentwurf abzurufen. Schließen Sie die `value` zu `BLOB`. Weiterleiten `BLOB` -Instanz zum Output-Dienst.


1. Verwenden Sie den Output-Dienst, um das PDF-Dokument zu generieren.

   Rufen Sie die `OutputServiceClient` -Objekt `generatePDFOutput2` -Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die zusätzlichen Ressourcen (z. B. Bilder) befinden.
   * A `BLOB` -Objekt, das den Formularentwurf darstellt (verwenden Sie die `BLOB` -Instanz, die vom Assembler-Dienst zurückgegeben wird).
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `BLOB` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * Ausgabe `BLOB` -Objekt, das `generatePDFOutput2` -Methode gefüllt. Die `generatePDFOutput2` -Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ausgabe `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

   Die `generatePDFOutput2` -Methode gibt eine `BLOB` -Objekt, das das nicht interaktive PDF-Formular enthält.

1. Speichern Sie das PDF-Dokument als PDF-Datei.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort des interaktiven PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt, das aus dem `generatePDFOutput2` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Drucken in Dateien {#printing-to-files}

Mit dem Output-Dienst können Sie Streams wie PostScript, Printer Control Language (PCL) oder die folgenden Beschriftungsformate in eine Datei drucken:

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Mit dem Output-Dienst können Sie XML-Daten mit einem Formularentwurf zusammenführen und das Formular in eine Datei drucken. Die folgende Abbildung zeigt den Output-Dienst zum Erstellen von Laser- und Beschriftungsdateien.

>[!NOTE]
>
>Informationen zum Senden von Druckstreams an Drucker finden Sie unter [Senden von Druck-Streams an Drucker](creating-document-output-streams.md#sending-print-streams-to-printers).

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Führen Sie die folgenden Schritte aus, um in eine Datei zu drucken:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Legen Sie die zum Drucken in eine Datei erforderlichen Drucklaufzeitoptionen fest.
1. Drucken Sie den Druckdatenstrom in eine Datei.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird. (Siehe [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie eine `OutputServiceService` -Objekt.

**Referenzieren einer XML-Datenquelle**

Zum Drucken eines Dokuments, das Daten enthält, müssen Sie eine XML-Datenquelle referenzieren, die XML-Elemente für jedes Formularfeld enthält, das mit Daten gefüllt werden soll. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

**Festlegen der zum Drucken in einer Datei erforderlichen Drucklaufzeitoptionen**

Um in eine Datei zu drucken, müssen Sie die Laufzeitoption Datei-URI festlegen, indem Sie den Speicherort und den Namen der Datei angeben, in die der Output-Dienst druckt. So weisen Sie beispielsweise den Output-Dienst an, eine PostScript-Datei mit dem Namen *MortgageForm.ps* auf C:\Adobe, geben Sie C:\Adobe\MortgageForm.ps an.

>[!NOTE]
>
>Es gibt optionale Laufzeitoptionen, die Sie definieren können. Informationen zu allen Optionen, die Sie festlegen können, finden Sie unter `PrintedOutputOptionsSpec` Klassenreferenz in [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Druckdatenstrom in eine Datei drucken**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die Formulardaten enthält, und Drucklaufzeitoptionen festgelegt haben, können Sie den Output-Dienst aufrufen, wodurch eine Datei gedruckt wird.

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, werden verschiedene Datenelemente wie XML-Daten zurückgegeben, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Drucken in Dateien mithilfe der Java-API](creating-document-output-streams.md#print-to-files-using-the-java-api)

[Drucken in Dateien mithilfe der Webdienst-API](creating-document-output-streams.md#print-to-files-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Drucken in Dateien mithilfe der Java-API {#print-to-files-using-the-java-api}

Drucken Sie mit der Output API (Java) in eine Datei:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-output-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des Dokuments mithilfe seines Konstruktors verwendet wird, und einen string -Wert übergibt, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie die zum Drucken in eine Datei erforderlichen Drucklaufzeitoptionen fest.

   * Erstellen Sie ein Objekt `PrintedOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die Datei an, indem Sie die `setFileURI` -Methode verwenden und einen string -Wert übergeben, der den Namen und Speicherort der Datei darstellt. Wenn Sie beispielsweise möchten, dass der Output-Dienst in eine PostScript-Datei mit dem Namen &quot;MortgageForm.ps&quot;unter C:\Adobe druckt, geben Sie C:\\Adobe\MortgageForm.ps an.
   * Geben Sie die Anzahl der zu druckenden Kopien an, indem Sie die `PrintedOutputOptionsSpec` -Objekt `setCopies` -Methode verwenden und einen ganzzahligen Wert übergeben, der die Anzahl der Exemplare darstellt.

1. Drucken Sie den Druckdatenstrom in eine Datei.

   Drucken Sie in einer Datei, indem Sie die `OutputClient` -Objekt `generatePrintedOutput` -Methode verwenden und die folgenden Werte übergeben:

   * A `PrintFormat` Auflistungswert, der das zu erstellende Druckstream-Format angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Speicherort zugehöriger Begleitdateien wie Bilddateien angibt.
   * Ein string -Wert, der den Speicherort der zu verwendenden XDC-Datei angibt (Sie können `null` , wenn Sie die XDC-Datei angegeben haben, die verwendet werden soll, indem Sie die `PrintedOutputOptionsSpec` -Objekt).
   * Die `PrintedOutputOptionsSpec` -Objekt, das Laufzeitoptionen enthält, die zum Drucken in eine Datei erforderlich sind.
   * Die `com.adobe.idp.Document` -Objekt, das die XML-Datenquelle enthält, die Formulardaten enthält.

   Die `generatePrintedOutput` -Methode gibt eine `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

   >[!NOTE]
   >
   >Die `OutputResult` -Objekt `getRecordLevelMetaDataList` Methodenzurückgaben `null`*. *

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, das den Status der `generatePrintedOutput` -Methode durch Aufrufen der `OutputResult` -Objekt `getStatusDoc` -Methode `OutputResult` -Objekt wurde von der `generatePrintedOutput` -Methode).
   * Erstellen Sie eine `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das von der `getStatusDoc` -Methode).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Drucken in einer Datei mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-printing-to-a-file-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Drucken in Dateien mithilfe der Webdienst-API {#print-to-files-using-the-web-service-api}

Drucken Sie mit der Output API (Webdienst) in eine Datei:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost`* mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird. *

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie eine `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `OutputServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `OutputServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern von Formulardaten verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Speicherort der XML-Datei angibt, die Formulardaten enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `binaryData` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Legen Sie die zum Drucken in eine Datei erforderlichen Drucklaufzeitoptionen fest.

   * Erstellen Sie ein Objekt `PrintedOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die Datei an, indem Sie dem `PrintedOutputOptionsSpec` -Objekt `fileURI` Datenelement. Wenn der Output-Dienst beispielsweise in eine PostScript-Datei mit dem Namen *MortgageForm.ps* unter C:\Adobe, geben Sie C:\\Adobe\MortgageForm.ps an.
   * Geben Sie die Anzahl der zu druckenden Exemplare an, indem Sie einen ganzzahligen Wert zuweisen, der die Anzahl der Exemplare für die `PrintedOutputOptionsSpec` -Objekt `copies` Datenmitglieder.

1. Drucken Sie den Druckdatenstrom in eine Datei.

   Drucken Sie in einer Datei, indem Sie die `OutputServiceService` -Objekt `generatePrintedOutput` -Methode verwenden und die folgenden Werte übergeben:

   * A `PrintFormat` Auflistungswert, der das zu erstellende Druckstream-Format angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Speicherort zugehöriger Begleitdateien wie Bilddateien angibt.
   * Ein string -Wert, der den Speicherort der zu verwendenden XDC-Datei angibt (Sie können `null` , wenn Sie die XDC-Datei angegeben haben, die verwendet werden soll, indem Sie die `PrintedOutputOptionsSpec` -Objekt).
   * Die `PrintedOutputOptionsSpec` -Objekt, das zum Drucken in eine Datei erforderliche Drucklaufzeitoptionen enthält.
   * Die `BLOB` -Objekt, das die XML-Datenquelle enthält, die Formulardaten enthält.
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `OutputServiceService` -Objekt `generatePDFOutput` -Methode (der achte Parameter). Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Senden von Druck-Streams an Drucker {#sending-print-streams-to-printers}

Sie können den Output-Dienst verwenden, um Druckstreams wie PostScript, Printer Control Language (PCL) oder die folgenden Beschriftungsformate an Netzwerkdrucker zu senden:

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Mit dem Output-Dienst können Sie XML-Daten mit einem Formularentwurf zusammenführen und das Formular als Druckstream ausgeben. Sie können beispielsweise einen PostScript-Druckstream erstellen und an einen Netzwerkdrucker senden. Die folgende Abbildung zeigt den Output-Dienst, der Druckstreams an Netzwerkdrucker sendet.

>[!NOTE]
>
>Um zu demonstrieren, wie ein Druckstrom an einen Netzwerkdrucker gesendet wird, sendet dieser Abschnitt einen PostScript-Druckstrom mithilfe des SharedPrinter-Druckerprotokolls an einen Netzwerkdrucker.

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

So senden Sie einen Druckstream an einen Netzwerkdrucker:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Festlegen von Drucklaufzeitoptionen
1. Abrufen eines zu druckenden Dokuments.
1. Senden Sie das Dokument an einen Netzwerkdrucker.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, erstellen Sie ein Output-Dienst-Client-Objekt. Wenn Sie die Java-API verwenden, erstellen Sie eine `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie eine `OutputServiceClient` -Objekt.

**Referenzieren einer XML-Datenquelle**

Zum Drucken eines Dokuments, das Daten enthält, müssen Sie eine XML-Datenquelle referenzieren, die XML-Elemente für jedes Formularfeld enthält, das mit Daten gefüllt werden soll. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

**Festlegen von Drucklaufzeitoptionen**

Sie können die Laufzeitoptionen beim Senden eines Druckstreams an einen Drucker festlegen, einschließlich der folgenden Optionen:

* **Kopien**: Gibt die Anzahl der an den Drucker zu sendenden Kopien an. Der Standardwert ist 1.
* **Staple**: Eine XCI-Option wird festgelegt, wenn ein Hefter verwendet wird. Diese Option kann im Konfigurationsmodell durch das Heftelement angegeben werden und wird nur für PS- und PCL-Drucker verwendet.
* **OutputJog**: Eine XCI-Option wird festgelegt, wenn Ausgabeseiten gejoggt werden sollen (physisch in der Ausgabenablage verschoben). Diese Option ist nur für PS- und PCL-Drucker verfügbar.
* **OutputBin**: XCI-Wert, der verwendet wird, um dem Druckertreiber die Auswahl der entsprechenden Ausgabenablage zu ermöglichen.

>[!NOTE]
>
>Informationen zu allen Laufzeitoptionen, die Sie festlegen können, finden Sie unter `PrintedOutputOptionsSpec` -Klassenreferenz.

**Abrufen eines zu druckenden Dokuments**

Rufen Sie einen Druckstream ab, der an einen Drucker gesendet werden soll. Sie können beispielsweise eine PostScript-Datei abrufen und an einen Drucker senden.

Sie können eine PDF-Datei senden, wenn Ihr Drucker PDF unterstützt. Ein Problem beim Senden eines PDF-Dokuments an einen Drucker besteht jedoch darin, dass jeder Druckerhersteller über eine andere Implementierung des PDF-Interpreters verfügt. Das heißt, einige Druckereien verwenden die Adobe PDF-Interpretation, aber es hängt vom Drucker ab. Andere Drucker haben einen eigenen PDF-Interpreter. Daher können die Druckergebnisse variieren.

Eine weitere Einschränkung beim Senden eines PDF-Dokuments an einen Drucker besteht darin, dass es nur gedruckt wird. Es kann nicht auf Duplex, Papierfachauswahl und Stapeln zugreifen, außer durch Einstellungen am Drucker.

Um ein zu druckendes Dokument abzurufen, verwenden Sie die `generatePrintedOutput` -Methode. In der folgenden Tabelle sind die Inhaltstypen aufgeführt, die für einen bestimmten Druckstream festgelegt werden, wenn die `generatePrintedOutput` -Methode.

<table> 
 <thead> 
  <tr> 
   <th><p>Druckformat </p></th> 
   <th><p>Beschreibung</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>DPL </p></td> 
   <td><p>Erstellt einen standardmäßigen oder benutzerdefinierten xdc-Ausgabestream dpl203.xdc.</p></td> 
  </tr> 
  <tr> 
   <td><p>DPL300DPI </p></td> 
   <td><p>Erstellt einen DPL-Ausgabe-Stream mit 300 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>DPL406DPI </p></td> 
   <td><p>Erstellt einen DPL-Ausgabe-Stream mit 400 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>DPL600DPI </p></td> 
   <td><p>Erstellt einen DPL-Ausgabe-Stream mit 600 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>GenericColorPCL </p></td> 
   <td><p>Erstellt einen generischen Farb-PCL (5c)-Ausgabestream.</p></td> 
  </tr> 
  <tr> 
   <td><p>GenericPSLevel3 </p></td> 
   <td><p>Erstellt einen generischen PostScript Level 3-Ausgabestream.</p></td> 
  </tr> 
  <tr> 
   <td><p>IPL </p></td> 
   <td><p>Erstellt einen benutzerdefinierten IPL-Ausgabestream.</p></td> 
  </tr> 
  <tr> 
   <td><p>IPL 300 DPI </p></td> 
   <td><p>Erstellt einen IPL-Ausgabe-Stream mit 300 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>IPL 400 DPI </p></td> 
   <td><p>Erstellt einen IPL-Ausgabe-Stream mit 400 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>PCL </p></td> 
   <td><p>Erstellt einen generischen monochrome PCL (5e)-Ausgabestream.</p></td> 
  </tr> 
  <tr> 
   <td><p>PostScript </p></td> 
   <td><p>Erstellt einen generischen PostScript Level 2-Ausgabestream.</p></td> 
  </tr> 
  <tr> 
   <td><p>TPCL </p></td> 
   <td><p>Erstellt einen benutzerdefinierten TPCL-Ausgabestream.</p></td> 
  </tr> 
  <tr> 
   <td><p>TPCL305DPI </p></td> 
   <td><p>Erstellt einen TPCL 305-DPI-Ausgabestream.</p></td> 
  </tr> 
  <tr> 
   <td><p>TPCL600DPI </p></td> 
   <td><p>Erstellt einen TPCL-Ausgabe-Stream mit 600 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>ZPL </p></td> 
   <td><p>Erstellt einen ZPL-Ausgabe-Stream mit 203 DPI.</p></td> 
  </tr> 
  <tr> 
   <td><p>ZPL 300 DPI </p></td> 
   <td><p>Erstellt einen ZPL-Ausgabestream mit 300 DPI.</p></td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Sie können auch einen Druckstream an einen Drucker senden, indem Sie `generatePrintedOutput2` -Methode. Die Schnellstarts, die mit dem Abschnitt Senden von Druckstreams an Drucker verknüpft sind, verwenden jedoch die `generatePrintedOutput` -Methode.

**Senden Sie den Druckstrom an einen Netzwerkdrucker.**

Nachdem Sie ein zu druckendes Dokument abgerufen haben, können Sie den Output-Dienst aufrufen, wodurch ein Druckstream an einen Netzwerkdrucker gesendet wird. Damit der Output-Dienst den Drucker erfolgreich finden kann, müssen Sie sowohl den Druckserver als auch den Druckernamen angeben. Darüber hinaus müssen Sie auch das Druckprotokoll angeben.

>[!NOTE]
>
>Wenn PDFG auf dem Formularserver installiert ist und der Server unter Windows Server 2008 ausgeführt wird, können Sie die SharedPrinter-Eigenschaft nicht verwenden. Verwenden Sie in diesem Fall ein anderes Druckerprotokoll.

>[!NOTE]
>
>Wenn Sie einen Netzwerkdrucker verwenden und der Zugriffsmechanismus SharedPrinter lautet, müssen Sie den vollständigen Netzwerkpfad des Druckers angeben. Senden Sie einen Druckstrom mithilfe der Java-API an einen Netzwerkdrucker.

Senden Sie mithilfe der Output API (Java) einen Druckstream an einen Netzwerkdrucker:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-output-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Output Client-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren einer XML-Datenquelle

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des Dokuments mithilfe seines Konstruktors verwendet wird, und einen string -Wert übergibt, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Drucklaufzeitoptionen

   Erstellen Sie eine `PrintedOutputOptionsSpec` -Objekt, das Drucklaufzeitoptionen darstellt. Sie können beispielsweise die Anzahl der zu druckenden Kopien angeben, indem Sie die `PrintedOutputOptionsSpec` -Objekt `setCopies` -Methode.

   >[!NOTE]
   >
   >Sie können den Paginierungswert nicht mithilfe der Variablen `PrintedOutputOptionsSpec` -Objekt `setPagination` -Methode verwenden, wenn Sie einen ZPL-Druckstrom generieren. Ebenso können Sie die folgenden Optionen für einen ZPL-Druckstream nicht festlegen: OutputJog, PageOffset und Staple. Die `setPagination`* ist für die PostScript-Generierung nicht gültig. Sie gilt nur für die PCL-Generierung. *

1. Abrufen eines zu druckenden Dokuments

   * Abrufen eines zu druckenden Dokuments durch Aufrufen der `OutputClient` -Objekt `generatePrintedOutput` -Methode verwenden und die folgenden Werte übergeben:

      * A `PrintFormat` Auflistungswert, der den Druckstrom angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
      * Ein string-Wert, der den Namen des Formularentwurfs angibt.
      * Ein string -Wert, der den Speicherort zugehöriger Begleitdateien (z. B. Bilddateien) angibt.
      * Ein string -Wert, der den Speicherort der zu verwendenden XDC-Datei angibt.
      * Die `PrintedOutputOptionsSpec` -Objekt, das Laufzeitoptionen enthält, die zum Drucken in einer Datei erforderlich sind.
      * Die `com.adobe.idp.Document` -Objekt, das die XML-Datenquelle darstellt, die die mit dem Formularentwurf zusammenzuführenden Formulardaten enthält.

      Diese Methode gibt eine `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, das durch Aufrufen des `OutputResult` object ‘s `getGeneratedDoc` -Methode. Diese Methode gibt eine `com.adobe.idp.Document` -Objekt.


1. Senden Sie den Druckstrom an einen Netzwerkdrucker.

   Senden Sie den Druckstrom an einen Netzwerkdrucker, indem Sie die `OutputClient` -Objekt `sendToPrinter` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das den an den Drucker zu sendenden Druckstrom darstellt.
   * A `PrinterProtocol` enumeration -Wert, der das zu verwendende Druckerprotokoll angibt. Um beispielsweise das SharedPrinter-Protokoll anzugeben, übergeben Sie `PrinterProtocol.SharedPrinter`.
   * Ein string -Wert, der den Namen des Druckservers angibt. Wenn beispielsweise der Name des Druckservers PrintServer1 lautet, übergeben Sie `\\\PrintSever1`.
   * Ein string -Wert, der den Namen des Druckers angibt. Wenn beispielsweise der Name des Druckers Printer1 lautet, übergeben Sie `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >Die `sendToPrinter` wurde der AEM Forms-API in Version 8.2.1 hinzugefügt.

### Druckdatenstream mithilfe der Webdienst-API an einen Drucker senden {#send-a-print-stream-to-a-printer-using-the-web-service-api}

Senden Sie mithilfe der Output-API (Webdienst) einen Druckdatenstrom an einen Netzwerkdrucker:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost`* mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird. *

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie eine `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `OutputServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `OutputServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern von Formulardaten verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt, die Formulardaten enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Bestimmen Sie die Byte-Array-Länge, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Festlegen von Drucklaufzeitoptionen.

   Erstellen Sie ein Objekt `PrintedOutputOptionsSpec`, indem Sie den Konstruktor verwenden. Sie können beispielsweise die Anzahl der zu druckenden Exemplare angeben, indem Sie dem Wert `PrintedOutputOptionsSpec` -Objekt `copies` Datenelement.

   >[!NOTE]
   >
   >Sie können den Paginierungswert nicht mithilfe der Variablen `PrintedOutputOptionsSpec` -Objekt `pagination` Datenelement, wenn Sie einen ZPL-Druckstream generieren. Ebenso können Sie die folgenden Optionen für einen ZPL-Druckstream nicht festlegen: OutputJog, PageOffset und Staple. Die `pagination`* -Datenelement ist für die PostScript-Generierung nicht gültig. Sie gilt nur für die PCL-Generierung. *

1. Abrufen eines zu druckenden Dokuments.

   * Abrufen eines zu druckenden Dokuments durch Aufrufen der `OutputServiceService` -Objekt `generatePrintedOutput` -Methode verwenden und die folgenden Werte übergeben:

      * A `PrintFormat` Auflistungswert, der den Druckstrom angibt. Um beispielsweise einen PostScript-Druckstream zu erstellen, übergeben Sie `PrintFormat.PostScript`.
      * Ein string-Wert, der den Namen des Formularentwurfs angibt.
      * Ein string -Wert, der den Speicherort zugehöriger Begleitdateien (z. B. Bilddateien) angibt.
      * Ein string -Wert, der den Speicherort der zu verwendenden XDC-Datei angibt.
      * Die `PrintedOutputOptionsSpec` -Objekt, das Drucklaufzeitoptionen enthält, die beim Senden eines Druckstreams an einen Netzwerkdrucker verwendet werden.
      * Die `BLOB` -Objekt, das die XML-Datenquelle enthält, die Formulardaten enthält.
      * A `BLOB` -Objekt, das von der `generatePrintedOutput` -Methode. Die `generatePrintedOutput` -Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
      * A `BLOB` -Objekt, das von der `generatePrintedOutput` -Methode. Die `generatePrintedOutput` -Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
      * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Erstellen Sie eine `BLOB` -Objekt, das an den Drucker gesendet wird, indem der Wert des `OutputResult` object ‘s `generatedDoc` -Methode. Diese Methode gibt eine `BLOB` -Objekt, das PostScript-Daten enthält, die von der `generatePrintedOutput` -Methode.


1. Senden Sie den Druckstrom an einen Netzwerkdrucker.

   Senden Sie den Druckstrom an einen Netzwerkdrucker, indem Sie die `OutputClient` -Objekt `sendToPrinter` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das den an den Drucker zu sendenden Druckstrom darstellt.
   * A `PrinterProtocol` enumeration -Wert, der das zu verwendende Druckerprotokoll angibt. Um beispielsweise das SharedPrinter-Protokoll anzugeben, übergeben Sie `PrinterProtocol.SharedPrinter`.
   * A `bool` -Wert, der angibt, ob der vorherige Parameterwert verwendet werden soll. Übergeben des Werts `true`. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich.)
   * Ein string -Wert, der den Namen des Druckservers angibt. Wenn beispielsweise der Name des Druckservers PrintServer1 lautet, übergeben Sie `\\\PrintSever1`.
   * Ein string -Wert, der den Namen des Druckers angibt. Wenn beispielsweise der Name des Druckers Printer1 lautet, übergeben Sie `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >Die `sendToPrinter` wurde der AEM Forms-API in Version 8.2.1 hinzugefügt.

## Erstellen mehrerer Ausgabedateien {#creating-multiple-output-files}

Der Output-Dienst kann für jeden Datensatz in einer XML-Datenquelle oder in einer Datei, die alle Datensätze enthält, separate Dokumente erstellen (diese Funktion ist die Standardfunktion). Angenommen, zehn Datensätze befinden sich in einer XML-Datenquelle und Sie weisen den Output-Dienst an, mithilfe der Output-Dienst-API für jeden Datensatz separate PDF-Dokumente (oder andere Ausgabetypen) zu erstellen. Daher generiert der Output-Dienst zehn PDF-Dokumente. (Anstatt Dokumente zu erstellen, können Sie mehrere Druck-Streams an einen Drucker senden.)

Die folgende Abbildung zeigt auch den Output-Dienst, der eine XML-Datendatei verarbeitet, die mehrere Datensätze enthält. Nehmen Sie jedoch an, dass Sie den Output-Dienst anweisen, ein einzelnes PDF-Dokument zu erstellen, das alle Datensätze enthält. In diesem Fall generiert der Output-Dienst ein Dokument, das alle Datensätze enthält.

Die folgende Abbildung zeigt den Output-Dienst, der eine XML-Datendatei verarbeitet, die mehrere Datensätze enthält. Angenommen, Sie weisen den Output-Dienst an, für jeden Datensatz ein separates PDF-Dokument zu erstellen. In diesem Fall generiert der Output-Dienst für jeden Datensatz ein separates PDF-Dokument.

![cm_outputbatchmany](assets/cm_outputbatchmany.png)

Die folgenden XML-Daten zeigen ein Beispiel einer Datendatei, die drei Datensätze enthält.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <batch> 
 <LoanRecord> 
     <mortgageAmount>500000</mortgageAmount> 
     <lastName>Blue</lastName> 
     <firstName>Tony</firstName> 
     <SSN>555666777</SSN> 
     <PositionTitle>Product Manager</PositionTitle> 
     <Address>555 No Where Dr</Address> 
     <City>New York</City> 
     <StateProv>New York</StateProv> 
     <ZipCode>51256</ZipCode> 
     <Email>TBlue@NoMailServer.com</Email> 
     <PhoneNum>555-7418</PhoneNum> 
     <FaxNum>555-9981</FaxNum> 
     <Description>Buy a home</Description> 
 </LoanRecord> 
 <LoanRecord> 
     <mortgageAmount>300000</mortgageAmount> 
     <lastName>White</lastName> 
     <firstName>Sam</firstName> 
     <SSN>555666222</SSN> 
     <PositionTitle>Program Manager</PositionTitle> 
     <Address>557 No Where Dr</Address> 
     <City>New York</City> 
     <StateProv>New York</StateProv> 
     <ZipCode>51256</ZipCode> 
     <Email>SWhite@NoMailServer.com</Email> 
     <PhoneNum>555-7445</PhoneNum> 
     <FaxNum>555-9986</FaxNum> 
     <Description>Buy a home</Description> 
 </LoanRecord> 
 <LoanRecord> 
     <mortgageAmount>700000</mortgageAmount> 
     <lastName>Green</lastName> 
     <firstName>Steve</firstName> 
     <SSN>55566688</SSN> 
     <PositionTitle>Project Manager</PositionTitle> 
     <Address>445 No Where Dr</Address> 
     <City>New York</City> 
     <StateProv>New York</StateProv> 
     <ZipCode>51256</ZipCode> 
     <Email>SGreeb@NoMailServer.com</Email> 
     <PhoneNum>555-2211</PhoneNum> 
     <FaxNum>555-2221</FaxNum> 
     <Description>Buy a home</Description> 
 </LoanRecord> 
 </batch>
```

Beachten Sie, dass das XML-Element, das jeden Datensatz startet und beendet, `LoanRecord`. Dieses XML-Element wird durch die Anwendungslogik referenziert, die mehrere Dateien generiert.

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

So erstellen Sie mehrere PDF-Dateien basierend auf einer XML-Datenquelle:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Festlegen von PDF-Laufzeitoptionen.
1. Festlegen von Rendering-Laufzeitoptionen.
1. Generieren Sie mehrere PDF-Dateien.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie eine `OutputServiceService` -Objekt.

**Referenzieren einer XML-Datenquelle**

Referenzieren Sie eine XML-Datenquelle, die mehrere Datensätze enthält. Ein XML-Element muss verwendet werden, um die Datensätze zu trennen. In der Beispiel-XML-Datenquelle, die oben in diesem Abschnitt gezeigt wird, heißt beispielsweise das XML-Element, das Datensätze trennt `LoanRecord`.

Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Wenn alle XML-Elemente angegeben sind, muss die Reihenfolge, in der die XML-Elemente angezeigt werden, nicht eingehalten werden.

**Festlegen von PDF-Laufzeitoptionen**

Sie müssen die folgenden Laufzeitoptionen festlegen, damit der Output-Dienst erfolgreich mehrere Dateien basierend auf einer XML-Datenquelle erstellt:

* **Viele Dateien**: Gibt an, ob der Output-Dienst ein einzelnes Dokument oder mehrere Dokumente erstellt. Sie können &quot;true&quot;oder &quot;false&quot;angeben. Um ein separates Dokument für jeden Datensatz in der XML-Datenquelle zu erstellen, geben Sie &quot;true&quot;an.
* **Datei-URI**: Gibt den Speicherort der Dateien an, die der Output-Dienst generiert. Angenommen, Sie geben C:\\Adobe\forms\Loan.pdf an. In diesem Fall erstellt der Output-Dienst eine Datei mit dem Namen &quot;Loan.pdf&quot;und legt die Datei im Ordner &quot;C:\\Adobe\forms folder&quot;ab. Wenn mehrere Dateien vorliegen, lauten die Dateinamen &quot;Loan001.pdf&quot;, &quot;Loan0002.pdf&quot;, &quot;Loan003.pdf&quot;usw. Wenn Sie einen Dateispeicherort angeben, werden die Dateien auf dem Server und nicht auf dem Clientcomputer abgelegt.
* **Record Name**: Gibt den XML-Elementnamen in der Datenquelle an, der die Datensätze trennt. In der Beispiel-XML-Datenquelle, die oben in diesem Abschnitt gezeigt wird, wird beispielsweise das XML-Element, das Datensätze trennt, als `LoanRecord`. (Anstatt die Laufzeitoption &quot;Record Name&quot;festzulegen, können Sie die Datensatzebene festlegen, indem Sie ihr einen numerischen Wert zuweisen, der die Elementebene angibt, die Datensätze enthält. Sie können jedoch nur den Datensatznamen oder die Datensatzebene festlegen. Sie können nicht beide Werte festlegen.)

**Festlegen von Rendering-Laufzeitoptionen**

Sie können Laufzeitoptionen beim Rendern mehrerer Dateien festlegen. Obwohl diese Optionen nicht erforderlich sind (im Gegensatz zu erforderlichen Ausgabelaufzeitoptionen), können Sie Aufgaben wie die Verbesserung der Leistung des Output-Dienstes ausführen. Beispielsweise können Sie den Formularentwurf zwischenspeichern, den der Output-Dienst verwendet, um die Leistung zu verbessern.

Wenn der Output-Dienst Batch-Datensätze verarbeitet, liest er inkrementell Daten, die mehrere Datensätze enthalten. Das heißt, der Output-Dienst liest die Daten in den Speicher und gibt die Daten frei, während der Datensatz-Batch verarbeitet wird. Der Output-Dienst lädt Daten inkrementell, wenn eine von zwei Laufzeitoptionen festgelegt ist. Wenn Sie die Laufzeitoption &quot;Record Name&quot;festlegen, liest der Output-Dienst die Daten inkrementell. Wenn Sie die Laufzeitoption &quot;Record Level&quot;auf 2 oder höher setzen, liest der Output-Dienst die Daten auf inkrementelle Weise.

Sie können mithilfe der `PDFOutputOptionsSpec` oder `PrintedOutputOptionSpec` -Objekt `setLazyLoading` -Methode. Sie können den Wert übergeben `false` zu dieser Methode, die das inkrementelle Laden deaktiviert.

**Mehrere PDF-Dateien generieren**

Nachdem Sie eine gültige XML-Datenquelle referenziert haben, die mehrere Datensätze enthält und Laufzeitoptionen festgelegt hat, können Sie den Output-Dienst aufrufen, wodurch mehrere Dateien generiert werden. Wenn Sie mehrere Datensätze generieren, wird die `OutputResult` -Objekt `getGeneratedDoc` Methodenzurückgaben `null`.

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, werden XML-Daten zurückgegeben, die angeben, ob der Vorgang erfolgreich war. Die folgende XML-Datei wird vom Output-Dienst zurückgegeben. In diesem Fall generiert der Output-Dienst 42 Dokumente.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <printResult> 
 <status>0</status> 
 <requestId>4ad85f9e2</requestId> 
 <context/> 
 <messages> 
 <message>Printed all 42 records successfully.</message> 
 </messages> 
 <printSpec> 
 <input> 
 <validated>true</validated> 
 <dataFile recordIdField="" recordLevel="0" recordName="LoanRecord"/> 
 <sniffRules lookAhead="300"/> 
 <formDesign>Loan.xdp</formDesign> 
 <contentRoot>C:\Adobe</contentRoot> 
 <metadata-spec record="false"/> 
 </input> 
 <output> 
 <format>PDF</format> 
 <fileURI>C:\Adobe\forms\Loan.pdf</fileURI> 
 <optionString>cacheenabled=true&padebug=false&linearpdf=false&pdfarevisionnumber=1&pdfaconformance=A&taggedpdf=false&TransactionTimeOut=180</optionString> 
 <waitForResponse>true</waitForResponse> 
 <outputStream>multiple</outputStream> 
 </output> 
 </printSpec> 
 </printResult>
```

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen mehrerer PDF-Dateien mit der Java-API {#create-multiple-pdf-files-using-the-java-api}

Erstellen Sie mehrere PDF-Dateien mithilfe der Ausgabe-API (Java):

1. Projektdateien einschließen&quot;

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein. .

1. Erstellen eines Output Client-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren einer XML-Datenquelle

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die mehrere Datensätze enthält, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von PDF-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Viele Dateien fest, indem Sie die `PDFOutputOptionsSpec` -Objekt `setGenerateManyFiles` -Methode. Übergeben Sie beispielsweise den Wert `true` , um den Output-Dienst anzuweisen, für jeden Datensatz in der XML-Datenquelle eine separate PDF-Datei zu erstellen. (Wenn Sie `false`, generiert der Output-Dienst ein einzelnes PDF-Dokument, das alle Datensätze enthält).
   * Legen Sie die Option Datei-URI fest, indem Sie die `PDFOutputOptionsSpec` -Objekt `setFileUri` -Methode verwenden und einen string -Wert übergeben, der den Speicherort der Dateien angibt, die der Output-Dienst generiert. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.
   * Legen Sie die Option &quot;Record Name&quot;fest, indem Sie die `OutputOptionsSpec` -Objekt `setRecordName` -Methode verwenden und einen string -Wert übergeben, der den XML-Elementnamen in der Datenquelle angibt, der die Datensätze trennt. (Betrachten Sie beispielsweise die zuvor in diesem Abschnitt gezeigte XML-Datenquelle. Der Name des XML-Elements, das die Datensätze trennt, ist LoanRecord).

1. Festlegen von Rendering-Laufzeitoptionen

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie die `RenderOptionsSpec` -Objekt `setCacheEnabled` und das Übergeben einer `Boolean` Wert von `true`.

1. Mehrere PDF-Dateien generieren

   Generieren mehrerer PDF-Dateien durch Aufrufen der `OutputClient` -Objekt `generatePDFOutput` -Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` enum -Wert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `com.adobe.idp.Document` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.

   Die `generatePDFOutput` -Methode gibt eine `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

1. Ergebnisse des Vorgangs abrufen

   * Erstellen Sie eine `java.io.File` -Objekt, das eine XML-Datei darstellt, die die Ergebnisse der `generatePDFOutput` -Methode. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das von der `applyUsageRights` -Methode).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen mehrerer PDF-Dateien mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-multiple-pdf-files-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen mehrerer PDF-Dateien mithilfe der Webdienst-API {#create-multiple-pdf-files-using-the-web-service-api}

Erstellen Sie mehrere PDF-Dateien mithilfe der Output-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie eine `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `OutputServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `OutputServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern von Formulardaten verwendet, die mehrere Datensätze enthalten.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort der XML-Datei darstellt, die mehrere Datensätze enthält.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Festlegen von PDF-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Option Viele Dateien fest, indem Sie dem `OutputOptionsSpec` -Objekt `generateManyFiles` Datenelement. Weisen Sie beispielsweise den Wert zu `true` zu diesem Datenelement hinzu, um den Output-Dienst anzuweisen, eine separate PDF-Datei für jeden Datensatz in der XML-Datenquelle zu erstellen. (Wenn Sie `false` auf dieses Datenelement verweist, generiert der Output-Dienst eine PDF, die alle Datensätze enthält.
   * Legen Sie die Datei-URI-Option fest, indem Sie einen Zeichenfolgenwert zuweisen, der den Speicherort der vom Output-Dienst generierten Datei(en) angibt. `OutputOptionsSpec` -Objekt `fileURI` Datenelement. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.
   * Legen Sie die Option für den Datensatznamen fest, indem Sie einen string -Wert zuweisen, der den Namen des XML-Elements in der Datenquelle angibt, das die Datensätze zu der Variablen `OutputOptionsSpec` -Objekt `recordName` Datenelement.
   * Legen Sie die Kopieroption fest, indem Sie einen ganzzahligen Wert zuweisen, der die Anzahl der vom Output-Dienst generierten Kopien angibt. `OutputOptionsSpec` -Objekt `copies` Datenelement.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie den Wert zuweisen. `true` der `RenderOptionsSpec` -Objekt `cacheEnabled` Datenelement.

1. Generieren Sie mehrere PDF-Dateien.

   Erstellen mehrerer PDF-Dateien durch Aufrufen der `OutputServiceService` -Objekt `generatePDFOutput`-Methode verwenden und die folgenden Werte übergeben:

   * Ein Enum-Wert TransformationFormat . Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `BLOB` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben.
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit Ergebnisdaten.
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

1. Ergebnisse des Vorgangs abrufen

   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateinamenerweiterung .xml lautet.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `OutputServiceService` -Objekt `generatePDFOutput` -Methode (der achte Parameter). Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `binaryData` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Erstellen von Suchregeln {#creating-search-rules}

Sie können Suchregeln erstellen, die dazu führen, dass der Output-Dienst Eingabedaten prüft und verschiedene Formularentwürfe verwendet, die auf dem Dateninhalt basieren, um die Ausgabe zu generieren. Wenn beispielsweise der Text *Hypothek* sich in den Eingabedaten befindet, kann der Output-Dienst einen Formularentwurf namens Mortgage.xdp verwenden. Wenn der Text *Automobil* befindet sich in den Eingabedaten, kann der Output-Dienst einen Formularentwurf verwenden, der als &quot;AutomobileLoan.xdp&quot;gespeichert ist. Obwohl der Output-Dienst verschiedene Ausgabetypen generieren kann, geht dieser Abschnitt davon aus, dass der Output-Dienst eine PDF-Datei generiert. Das folgende Diagramm zeigt den Output-Dienst, der eine PDF-Datei durch Verarbeitung einer XML-Datendatei und Verwendung eines von vielen Formularentwürfen generiert.

Darüber hinaus kann der Output-Dienst Dokumentpakete generieren, in denen mehrere Datensätze im Datensatz bereitgestellt werden und jeder Datensatz mit einem Formularentwurf übereinstimmt und ein einzelnes Dokument aus mehreren Formularentwürfen generiert wird.

![cs_outputbatchmanyformdesigns2](assets/cs_outputbatchmanyformdesigns2.png)

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

So weisen Sie den Output-Dienst an, beim Generieren eines Dokuments Suchregeln zu verwenden:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Referenzieren einer XML-Datenquelle.
1. Definieren Sie Suchregeln.
1. Festlegen von PDF-Laufzeitoptionen.
1. Festlegen von Rendering-Laufzeitoptionen.
1. Erstellen Sie ein PDF-Dokument.
1. Rufen Sie die Ergebnisse des Vorgangs ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie adobe-utilities.jar und jbossall-client.jar durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird.

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen.

**Referenzieren einer XML-Datenquelle**

Für jedes Formularfeld, das mit Daten gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Es ist nicht erforderlich, die Reihenfolge der Anzeige der XML-Elemente einzuhalten, solange alle XML-Elemente angegeben sind.

**Suchregeln definieren**

Um Suchregeln zu definieren, definieren Sie ein oder mehrere Textmuster, nach denen der Output-Dienst in den Eingabedaten sucht. Für jedes von Ihnen definierte Textmuster geben Sie einen entsprechenden Formularentwurf an, der verwendet wird, wenn sich das Textmuster befindet. Wenn sich ein Textmuster befindet, verwendet der Output-Dienst den entsprechenden Formularentwurf, um die Ausgabe zu generieren. Ein Beispiel für ein Textmuster ist *Hypothek*.

>[!NOTE]
>
>Wenn sich keine Textmuster befinden, wird das Standardformular verwendet. Stellen Sie sicher, dass sich alle von Ihnen verwendeten Formularentwürfe im Inhaltsstamm befinden.

**Festlegen von PDF-Laufzeitoptionen**

Legen Sie die folgenden PDF-Laufzeitoptionen fest, damit der Output-Dienst erfolgreich ein PDF-Dokument erstellen kann, das auf mehreren Formularentwürfen basiert:

* **Datei-URI**: Gibt den Namen und Speicherort der PDF-Datei an, die der Output-Dienst generiert.
* **Regeln**: Gibt von Ihnen definierte Regeln an.
* **LookAHead**: Gibt die Anzahl der Bytes an, die vom Anfang der Eingabedatendatei verwendet werden sollen, um nach den definierten Textmustern zu suchen. Der Standardwert ist 500 Byte.

**Festlegen von Rendering-Laufzeitoptionen**

Sie können Laufzeitoptionen beim Erstellen von PDF-Dateien für das Rendering festlegen. Obwohl diese Optionen nicht erforderlich sind (im Gegensatz zu PDF-Laufzeitoptionen), können Sie Aufgaben wie die Leistungsverbesserung des Output-Dienstes ausführen. Beispielsweise können Sie den Formularentwurf zwischenspeichern, den der Output-Dienst verwendet, um die Leistung zu verbessern.

**PDF-Dokument generieren**

Nachdem Sie eine gültige XML-Datenquelle referenziert und Laufzeitoptionen festgelegt haben, können Sie den Output-Dienst aufrufen, um ein PDF-Dokument zu generieren. Wenn der Output-Dienst ein bestimmtes Textmuster in den Eingabedaten findet, verwendet er den entsprechenden Formularentwurf. Wenn kein Textmuster verwendet wird, verwendet der Output-Dienst den Standardformularentwurf.

**Ergebnisse des Vorgangs abrufen**

Nachdem der Output-Dienst einen Vorgang ausgeführt hat, werden XML-Daten zurückgegeben, die angeben, ob der Vorgang erfolgreich war.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Erstellen von Suchregeln mit der Java-API {#create-search-rules-using-the-java-api}

Erstellen Sie Suchregeln mithilfe der Ausgabe-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das die XML-Datenquelle darstellt, die zum Ausfüllen des PDF-Dokuments mithilfe des Konstruktors verwendet wird, und einen string -Wert übergibt, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Definieren Sie Suchregeln.

   * Erstellen Sie ein Objekt `Rule`, indem Sie den Konstruktor verwenden.
   * Definieren Sie ein Textmuster, indem Sie die `Rule` -Objekt `setPattern` -Methode verwenden und einen string -Wert übergeben, der ein Textmuster angibt.
   * Definieren Sie den entsprechenden Formularentwurf, indem Sie die `Rule` -Objekt `setForm` -Methode . Übergeben Sie einen string -Wert, der den Namen des Formularentwurfs angibt.

   >[!NOTE]
   >
   >Wiederholen Sie für jedes zu definierende Textmuster die vorherigen drei Unterschritte.

   * Erstellen Sie eine `java.util.List` Objekt mithilfe von `java.util.ArrayList` -Konstruktor.
   * Für jeden `Rule` -Objekt, das Sie erstellt haben, rufen Sie die `java.util.List` -Objekt `add` -Methode und übergeben Sie die `Rule` -Objekt.


1. Festlegen von PDF-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie den Namen und Speicherort der PDF-Datei an, die der Output-Dienst generiert, indem er die `PDFOutputOptionsSpec` -Objekt `setFileURI` -Methode. Übergeben Sie einen string -Wert, der den Speicherort der PDF-Datei angibt. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.
   * Legen Sie die Regeln fest, die Sie definiert haben, indem Sie die `PDFOutputOptionsSpec` -Objekt `setRules` -Methode. Übergeben Sie die `java.util.List` -Objekt, das `Rule` Objekte.
   * Legen Sie die Anzahl der Bytes fest, die auf die definierten Textmuster gescannt werden sollen, indem Sie die `PDFOutputOptionsSpec` -Objekt `setLookAhead` -Methode. Übergeben Sie einen ganzzahligen Wert, der die Anzahl der Bytes darstellt.

1. Festlegen von Rendering-Laufzeitoptionen.

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern Sie den Formularentwurf, um die Leistung des Output-Dienstes zu verbessern, indem Sie die `RenderOptionsSpec` -Objekt `setCacheEnabled` und übergeben `true`.

1. Erstellen Sie ein PDF-Dokument.

   Erstellen Sie ein PDF-Dokument, das auf mehreren Formularentwürfen basiert, indem Sie die `OutputClient` -Objekt `generatePDFOutput` -Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string -Wert, der den Namen des Standardformularentwurfs angibt. Das heißt, der Formularentwurf, der verwendet wird, wenn sich ein Textmuster nicht befindet.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich die Formularentwürfe befinden.
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `com.adobe.idp.Document` -Objekt, das die Formulardaten enthält, die vom Output-Dienst nach den definierten Textmustern durchsucht werden.

   Die `generatePDFOutput` -Methode gibt eine `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält.

1. Rufen Sie die Ergebnisse des Vorgangs ab.

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, das den Status der `generatePDFOutput` -Methode durch Aufrufen der `OutputResult` -Objekt `getStatusDoc` -Methode.
   * Erstellen Sie eine `java.io.File` -Objekt, das die Ergebnisse des Vorgangs enthält. Stellen Sie sicher, dass die Dateierweiterung .xml lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das von der `getStatusDoc` -Methode).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Erstellen von Suchregeln mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Schnellstart (SOAP-Modus): Erstellen von Suchregeln mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Erstellen von Suchregeln mithilfe der Webdienst-API {#create-search-rules-using-the-web-service-api}

Erstellen Sie Suchregeln mithilfe der Output-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie eine `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `OutputServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `OutputServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Referenzieren einer XML-Datenquelle.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern von Daten verwendet, die mit dem PDF-Dokument zusammengeführt werden.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.

1. Definieren Sie Suchregeln.

   * Erstellen Sie ein Objekt `Rule`, indem Sie den Konstruktor verwenden.
   * Definieren Sie ein Textmuster, indem Sie einen Zeichenfolgenwert zuweisen, der ein Textmuster für die `Rule` -Objekt `pattern` Datenelement.
   * Definieren Sie den entsprechenden Formularentwurf, indem Sie einen Zeichenfolgenwert zuweisen, der den Formularentwurf dem `Rule` -Objekt `form` Datenelement.

   >[!NOTE]
   >
   >Wiederholen Sie für jedes zu definierende Textmuster die vorherigen drei Unterschritte.

   * Erstellen Sie eine `MyArrayOf_xsd_anyType` -Objekt, das die Regeln speichert.
   * Zuweisen `Rule` -Objekt auf ein Element der `MyArrayOf_xsd_anyType` Array. Rufen Sie die `MyArrayOf_xsd_anyType` -Objekt `Add` -Methode für jeden `Rule` -Objekt.


1. Festlegen von PDF-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PDFOutputOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Datei-URI-Option fest, indem Sie einen Zeichenfolgenwert zuweisen, der den Speicherort der vom Output-Dienst generierten PDF-Datei angibt. `PDFOutputOptionsSpec` -Objekt `fileURI` Datenelement. Die Option Datei-URI ist relativ zum J2EE-Anwendungsserver, der als Host für AEM Forms dient, und nicht zum Clientcomputer.
   * Legen Sie die Kopieroption fest, indem Sie einen ganzzahligen Wert zuweisen, der die Anzahl der vom Output-Dienst generierten Kopien angibt. `PDFOutputOptionsSpec` -Objekt `copies` Datenelement.
   * Legen Sie die von Ihnen definierten Regeln fest, indem Sie die `MyArrayOf_xsd_anyType` -Objekt, das die Regeln im `PDFOutputOptionsSpec` -Objekt `rules` Datenelement.
   * Legen Sie die Anzahl der Bytes fest, die auf die definierten Textmuster gescannt werden sollen, indem Sie einen ganzzahligen Wert zuweisen, der die Anzahl der Bytes darstellt, die gescannt werden sollen. `PDFOutputOptionsSpec` -Objekt `lookAhead` Datenmethode.

1. Festlegen von Rendering-Laufzeitoptionen

   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden.
   * Zwischenspeichern des Formularentwurfs, um die Leistung des Output-Dienstes durch Zuweisen des Werts zu verbessern `true` der `RenderOptionsSpec` -Objekt `cacheEnabled` Datenelement.

   >[!NOTE]
   >
   >Sie können die PDF-Dokumentversion nicht mithilfe der `RenderOptionsSpec` -Objekt `pdfVersion` -Element, wenn das Eingabedokument ein Acrobat-Formular ist. Das PDF-Ausgabedokument behält die PDF-Version des Acrobat-Formulars bei. Ebenso können Sie die getaggte PDF-Option nicht mithilfe der `RenderOptionsSpec` -Objekt `taggedPDF` -Methode, wenn das Eingabedokument ein Acrobat-Formular ist.

   >[!NOTE]
   >
   >Sie können die Option für linearisiertes PDF nicht mithilfe der `RenderOptionsSpec` -Objekt `linearizedPDF` -Element, wenn das PDF-Eingabedokument zertifiziert oder digital signiert ist. Weitere Informationen finden Sie unter [Digitales Signieren von PDF-Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).

1. PDF-Dokument generieren

   Erstellen Sie ein PDF-Dokument, indem Sie die `OutputServiceService` -Objekt `generatePDFOutput`-Methode verwenden und die folgenden Werte übergeben:

   * A `TransformationFormat` Auflistungswert. Um ein PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * Ein string-Wert, der den Namen des Formularentwurfs angibt.
   * Ein string -Wert, der den Inhaltsstamm angibt, in dem sich der Formularentwurf befindet.
   * A `PDFOutputOptionsSpec` -Objekt, das PDF-Laufzeitoptionen enthält.
   * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen zum Rendern enthält.
   * Die `BLOB` -Objekt, das die XML-Datenquelle enthält, die Daten enthält, die mit dem Formularentwurf zusammengeführt werden sollen.
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit generierten Metadaten, die das Dokument beschreiben. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * A `BLOB` -Objekt, das von der `generatePDFOutput` -Methode. Die `generatePDFOutput` -Methode füllt dieses Objekt mit Ergebnisdaten. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).
   * Ein `OutputResult` -Objekt, das die Ergebnisse des Vorgangs enthält. (Dieser Parameterwert ist nur für den Webdienstaufruf erforderlich).

   >[!NOTE]
   >
   >Beim Generieren eines PDF-Dokuments durch Aufrufen der `generatePDFOutput` beachten Sie, dass Sie keine Daten mit einem XFA-PDF-Formular zusammenführen können, das signiert, zertifiziert oder Verwendungsrechte enthält. Weitere Informationen zu Verwendungsrechten finden Sie unter [Anwenden von Nutzungsrechten auf PDF-Dokumente](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).

1. Ergebnisse des Vorgangs abrufen

   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der einen XML-Dateispeicherort darstellt, der Ergebnisdaten enthält. Stellen Sie sicher, dass die Dateierweiterung XML ist.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `OutputServiceService` -Objekt `generatePDFOutput` -Methode (der achte Parameter). Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in die XML-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Reduzieren von PDF-Dokumenten {#flattening-pdf-documents}

Sie können den Output-Dienst verwenden, um ein interaktives PDF-Dokument in ein nicht interaktives PDF umzuwandeln. Mit einem interaktiven PDF-Dokument können Benutzer Daten in die PDF-Dokumentfelder eingeben oder ändern. Der Prozess der Umwandlung eines interaktiven PDF-Dokuments in ein nicht interaktives PDF-Dokument wird als *Abflachung*. Wenn ein PDF-Dokument reduziert wird, kann ein Benutzer die Daten in den Dokumentfeldern nicht ändern. Dies kann ein Grund dafür sein, PDF-Dokumente zu reduzieren.

Sie können die folgenden Arten von PDF-Dokumenten reduzieren:

* Interaktive XFA-PDF-Dokumente
* Acrobat Forms

Der Versuch, eine PDF zu reduzieren, bei der es sich um ein nicht interaktives PDF-Dokument handelt, verursacht eine Ausnahme.

>[!NOTE]
>
>Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-9}

So reduzieren Sie ein interaktives PDF-Dokument auf ein nicht interaktives PDF-Dokument:

1. Projektdateien einschließen.
1. Erstellen Sie ein Output Client -Objekt.
1. Rufen Sie ein interaktives PDF-Dokument ab.
1. Transformieren Sie das PDF-Dokument.
1. Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Wenn AEM Forms auf einem unterstützten J2EE-Anwendungsserver bereitgestellt wird, der nicht JBoss ist, müssen Sie die Dateien &quot;adobe-utilities.jar&quot;und &quot;jbossall-client.jar&quot;durch JAR-Dateien ersetzen, die spezifisch für den J2EE-Anwendungsserver sind, auf dem AEM Forms bereitgestellt wird. Informationen zum Speicherort aller AEM Forms-JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Output Client-Objekts**

Bevor Sie einen Output-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Output-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `OutputClient` -Objekt. Wenn Sie die Output-Webdienst-API verwenden, erstellen Sie eine `OutputServiceService` -Objekt.

**Abrufen eines interaktiven PDF-Dokuments**

Rufen Sie ein interaktives PDF-Dokument ab, das Sie in ein nicht interaktives PDF-Dokument umwandeln möchten. Der Versuch, ein nicht interaktives PDF-Dokument umzuwandeln, verursacht eine Ausnahme.

**PDF-Dokument transformieren**

Nachdem Sie ein interaktives PDF-Dokument abgerufen haben, können Sie es in ein nicht interaktives PDF-Dokument umwandeln. Der Output-Dienst gibt ein nicht interaktives PDF-Dokument zurück.

**Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei**

Sie können das nicht interaktive PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Reduzieren eines PDF-Dokuments mithilfe der Java-API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-java-api)

[Reduzieren eines PDF-Dokuments mithilfe der Webdienst-API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Reduzieren eines PDF-Dokuments mithilfe der Java-API {#flatten-a-pdf-document-using-the-java-api}

Reduzieren Sie ein interaktives PDF-Dokument mithilfe der Output API (Java) auf ein nicht interaktives PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-output-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `OutputClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Rufen Sie ein interaktives PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das zu transformierende interaktive PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort der interaktiven PDF-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Transformieren Sie das PDF-Dokument.

   Umwandeln des interaktiven PDF-Dokuments in ein nicht interaktives PDF-Dokument durch Aufrufen des `OutputServiceService` -Objekt `transformPDF` -Methode verwenden und die folgenden Werte übergeben:

   * Die `com.adobe.idp.Document` -Objekt, das das interaktive PDF-Dokument enthält.
   * A `TransformationFormat` enum -Wert. Um ein nicht interaktives PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * A `PDFARevisionNumber` enum -Wert, der die Revisionsnummer angibt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null`.
   * Ein string -Wert, der die Änderungsnummer und das Jahr darstellt, getrennt durch einen Doppelpunkt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null`.
   * A `PDFAConformance` enum -Wert, der die Konformitätsstufe PDF/A darstellt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null`.

   Die `transformPDF` -Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `transformPDF` -Methode).

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[Schnellstart (EJB-Modus): Transformieren eines PDF-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): Transformieren eines PDF-Dokuments mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Reduzieren eines PDF-Dokuments mithilfe der Webdienst-API {#flatten-a-pdf-document-using-the-web-service-api}

Reduzieren Sie ein interaktives PDF-Dokument mithilfe der Output API (Webdienst) auf ein nicht interaktives PDF-Dokument:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Output Client -Objekt.

   * Erstellen Sie eine `OutputServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `OutputServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/OutputService?blob=mtom`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` , um MTOM zu verwenden.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `OutputServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie ein interaktives PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des interaktiven PDF-Dokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des interaktiven PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Transformieren Sie das PDF-Dokument.

   Umwandeln des interaktiven PDF-Dokuments in ein nicht interaktives PDF-Dokument durch Aufrufen des `OutputClient` -Objekt `transformPDF` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das interaktive PDF-Dokument enthält.
   * A `TransformationFormat` Auflistungswert. Um ein nicht interaktives PDF-Dokument zu generieren, geben Sie `TransformationFormat.PDF`.
   * A `PDFARevisionNumber` enum -Wert, der die Revisionsnummer angibt.
   * Ein boolescher Wert, der angibt, ob die `PDFARevisionNumber` wird der enum -Wert verwendet. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `false`.
   * Ein string -Wert, der die Änderungsnummer und das Jahr darstellt, getrennt durch einen Doppelpunkt. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `null`.
   * A `PDFAConformance` enum -Wert, der die Konformitätsstufe PDF/A darstellt.
   * Boolescher Wert, der angibt, ob die `PDFAConformance` wird der enum -Wert verwendet. Da dieser Parameter für ein PDF/A-Dokument vorgesehen ist, können Sie `false`.

   Die `transformPDF` -Methode gibt eine `BLOB` -Objekt, das ein nicht interaktives PDF-Dokument enthält.

1. Speichern Sie das nicht interaktive PDF-Dokument als PDF-Datei.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des nicht interaktiven PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `transformPDF` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](creating-document-output-streams.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
