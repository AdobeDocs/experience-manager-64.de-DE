---
title: Assemblieren mehrerer XDP-Fragmente
seo-title: Assembling Multiple XDP Fragments
description: Assemblieren mehrerer XDP-Fragmente in einem einzelnen XDP-Dokument mithilfe der Java-API und der Web Service-API.
seo-description: Assemble multiple XDP fragments into a single XDP document using the Java API and Web Service API.
uuid: 9e74e0e0-568d-4760-91a8-03dc1362d497
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 0ed1f69d-c212-4d47-a572-ae030f2983fc
role: Developer
exl-id: be9db93d-97e1-4d4e-8d07-1c58a4a1a44c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1887'
ht-degree: 3%

---

# Assemblieren mehrerer XDP-Fragmente {#assembling-multiple-xdp-fragments}

Sie können mehrere XDP-Fragmente in einem einzelnen XDP-Dokument zusammenführen. Betrachten Sie beispielsweise XDP-Fragmente, in denen jede XDP-Datei ein oder mehrere Teilformulare enthält, die zum Erstellen eines Konsistenzformulars verwendet werden. Die folgende Abbildung zeigt die Entwurfsansicht (stellt die Datei tuc018_template_flowed.xdp dar, die in der Datei *Assemblieren mehrerer XDP-Fragmente* Schnellstart):

![am_am_forma](assets/am_am_forma.png)

Die folgende Abbildung zeigt den Patientenabschnitt (stellt die Datei tuc018_contact.xdp dar, die in der Datei *Assemblieren mehrerer XDP-Fragmente* Schnellstart):

![am_am_formb](assets/am_am_formb.png)

Die folgende Abbildung zeigt den Abschnitt zur Patientengesundheit (stellt die Datei tuc018_patient.xdp dar, die in der Datei *Assemblieren mehrerer XDP-Fragmente* Schnellstart):

![am_am_formc](assets/am_am_formc.png)

Dieses Fragment enthält zwei Teilformulare mit dem Namen *subPatientPhysical* und *subPatientHealth*. Beide Unterformulare werden im DDX-Dokument referenziert, das an den Assembler-Dienst übergeben wird. Mithilfe des Assembler-Dienstes können Sie alle diese XDP-Fragmente zu einem einzelnen XDP-Dokument kombinieren, wie in der folgenden Abbildung dargestellt.

![am_am_formd](assets/am_am_formd.png)

Das folgende DDX-Dokument stellt mehrere XDP-Fragmente in einem XDP-Dokument zusammen.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
         <XDP result="tuc018result.xdp"> 
            <XDP source="tuc018_template_flowed.xdp"> 
             <XDPContent insertionPoint="ddx_fragment" source="tuc018_contact.xdp" fragment="subPatientContact" required="false"/> 
               <XDPContent insertionPoint="ddx_fragment" source="tuc018_patient.xdp" fragment="subPatientPhysical" required="false"/> 
               <XDPContent insertionPoint="ddx_fragment" source="tuc018_patient.xdp" fragment="subPatientHealth" required="false"/> 
            </XDP> 
         </XDP>         
 </DDX>
```

Das DDX-Dokument enthält eine XDP `result` -Tag, das den Namen des Ergebnisses angibt. In diesem Fall ist der Wert `tuc018result.xdp`. Dieser Wert wird in der Anwendungslogik referenziert, die zum Abrufen des XDP-Dokuments verwendet wird, nachdem der Assembler-Dienst das Ergebnis zurückgegeben hat. Betrachten Sie beispielsweise die folgende Java-Anwendungslogik, die zum Abrufen des assemblierten XDP-Dokuments verwendet wird (beachten Sie, dass der Wert fett ist):

```as3
 //Iterate through the map object to retrieve the result XDP document 
 for (Iterator i = allDocs.entrySet().iterator(); i.hasNext();) { 
     // Retrieve the Map object’s value 
     Map.Entry e = (Map.Entry)i.next(); 
                  
     //Get the key name as specified in the  
     //DDX document  
     String keyName = (String)e.getKey(); 
     if (keyName.equalsIgnoreCase("tuc018result.xdp")) 
                 {  
         Object o = e.getValue(); 
         outDoc = (Document)o; 
  
         //Save the result PDF file 
         File myOutFile = new File("C:\\AssemblerResultXDP.xdp");  
         outDoc.copyToFile(myOutFile); 
     } 
 }
```

Die `XDP source` -Tag gibt die XDP-Datei an, die ein vollständiges XDP-Dokument darstellt, das als Container zum Hinzufügen von XDP-Fragmenten oder als eines von mehreren Dokumenten verwendet werden kann, die in der richtigen Reihenfolge angehängt werden. In diesem Fall wird das XDP-Dokument nur als Container verwendet (die erste Illustration, die unter *Assemblieren mehrerer XDP-Fragmente*). Das heißt, die anderen XDP-Dateien werden im XDP-Container platziert.

Für jedes Teilformular können Sie eine `XDPContent` -Element (dieses Element ist optional). Beachten Sie im obigen Beispiel, dass es drei Teilformulare gibt: `subPatientContact`, `subPatientPhysical`und `subPatientHealth`. Beide `subPatientPhysical` Teilformular und `subPatientHealth` Teilformulare befinden sich in derselben XDP-Datei, tuc018_patient.xdp. Das Fragment-Element gibt den Namen des Teilformulars an, wie in Designer definiert.

>[!NOTE]
>
>Weitere Informationen zum Assembler-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zu einem DDX-Dokument finden Sie unter [Assembler-Dienst und DDX-Referenz](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um mehrere XDP-Fragmente zusammenzuführen:

1. Projektdateien einschließen.
1. Erstellen Sie einen PDF Assembler-Client.
1. Referenzieren Sie ein vorhandenes DDX-Dokument.
1. Referenzieren Sie die XDP-Dokumente.
1. Legen Sie Laufzeitoptionen fest.
1. Assemblieren Sie mehrere XDP-Dokumente.
1. Rufen Sie das assemblierte XDP-Dokument ab.

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

Zum Zusammenführen mehrerer XDP-Dokumente muss auf ein DDX-Dokument verwiesen werden. Dieses DDX-Dokument muss Folgendes enthalten: `XDP result`, `XDP source`und `XDPContent` -Elemente.

**Referenzieren der XDP-Dokumente**

Referenzieren Sie zum Zusammenführen mehrerer XDP-Dokumente alle XDP-Dateien, die zum Zusammenführen des XDP-Ergebnisdokuments verwendet werden. Stellen Sie sicher, dass der Name des Teilformulars im XDP-Dokument, auf das vom `source` -Attribut wird in der `fragment` -Attribut. Ein Teilformular wird in Designer definiert. Betrachten Sie beispielsweise die folgende XML.

```as3
 <XDPContent insertionPoint="ddx_fragment" source="tuc018_contact.xdp" fragment="subPatientContact" required="false"/>
```

Das Teilformular mit dem Namen *subPatientContact* muss sich in der XDP-Datei mit dem Namen *tuc018_contact.xdp*.

**Laufzeitoptionen festlegen**

Sie können Laufzeitoptionen festlegen, die das Verhalten des Assembler-Dienstes während der Ausführung eines Auftrags steuern. Sie können beispielsweise eine Option festlegen, mit der der Assembler-Dienst angewiesen wird, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt.

**Assemblieren mehrerer XDP-Dokumente**

Um mehrere XDP-Dateien zusammenzuführen, rufen Sie die `invokeDDX` Vorgang. Der Assembler-Dienst gibt das assemblierte XDP-Dokument innerhalb eines Sammlungsobjekts zurück.

**Abrufen des assemblierten XDP-Dokuments**

Ein assembliertes XDP-Dokument wird innerhalb eines Sammlungsobjekts zurückgegeben. Durchsuchen Sie das Sammlungsobjekt und speichern Sie das XDP-Dokument als XDP-Datei. Sie können das XDP-Dokument auch an einen anderen AEM Forms-Dienst, z. B. Output, übergeben.

**Siehe auch**

[Assemblieren mehrerer XDP-Fragmente mithilfe der Java-API](assembling-multiple-xdp-fragments.md#assemble-multiple-xdp-fragments-using-the-java-api)

[Assemblieren mehrerer XDP-Fragmente mithilfe der Webdienst-API](assembling-multiple-xdp-fragments.md#assemble-multiple-xdp-fragments-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmgesteuertes Zusammenstellen von PDF-Dokumenten](/help/forms/developing/programmatically-assembling-pdf-documents.md)

[Erstellen von PDF-Dokumenten mit Fragmenten](/help/forms/developing/creating-document-output-streams.md)

## Assemblieren mehrerer XDP-Fragmente mithilfe der Java-API {#assemble-multiple-xdp-fragments-using-the-java-api}

Assemblieren mehrerer XDP-Fragmente mithilfe der Assembler Service-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-assembler-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `AssemblerServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das DDX-Dokument darstellt, indem es seinen Konstruktor verwendet und einen string -Wert übergibt, der den Speicherort der DDX-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie die XDP-Dokumente.

   * Erstellen Sie eine `java.util.Map` -Objekt, das zum Speichern von XDP-Eingabedokumenten mithilfe eines `HashMap` -Konstruktor.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt und übergeben Sie die `java.io.FileInputStream` -Objekt, das die XDP-Eingabedatei enthält (wiederholen Sie diese Aufgabe für jede XDP-Datei).
   * Fügen Sie dem `java.util.Map` -Objekt durch Aufrufen seiner `put` -Methode verwenden und die folgenden Argumente übergeben:

      * Ein string -Wert, der den Schlüsselnamen darstellt. Dieser Wert muss mit dem Wert `source` Elementwert, der im DDX-Dokument angegeben ist (diese Aufgabe für jede XDP-Datei wiederholen).
      * A `com.adobe.idp.Document` -Objekt, das das XDP-Dokument enthält, das dem `source` -Element (diese Aufgabe für jede XDP-Datei wiederholen).

1. Legen Sie die Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie eine Methode aufrufen, die zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, rufen Sie die `AssemblerOptionSpec` -Objekt `setFailOnError` -Methode und -übergabe `false`.

1. Assemblieren Sie mehrere XDP-Dokumente.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden erforderlichen Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das zu verwendende DDX-Dokument darstellt
   * A `java.util.Map` -Objekt, das die XDP-Eingabedateien enthält
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -Objekt, das die Laufzeitoptionen angibt, einschließlich der Standardschrift und der Auftragsprotokollebene

   Die `invokeDDX` -Methode gibt eine `com.adobe.livecycle.assembler.client.AssemblerResult` -Objekt, das das assemblierte XDP-Dokument enthält.

1. Rufen Sie das assemblierte XDP-Dokument ab.

   Um das assemblierte XDP-Dokument abzurufen, führen Sie die folgenden Aktionen aus:

   * Rufen Sie die `AssemblerResult` -Objekt `getDocuments` -Methode. Diese Methode gibt eine `java.util.Map` -Objekt.
   * Iteration durch die `java.util.Map` -Objekt, bis Sie das Ergebnis finden `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Extrahieren des assemblierten XDP-Dokuments.

**Siehe auch**

[Assemblieren mehrerer XDP-Fragmente](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)

[Schnellstart (SOAP-Modus): Assemblieren mehrerer XDP-Fragmente mithilfe der Java-API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-multiple-xdp-fragments-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Assemblieren mehrerer XDP-Fragmente mithilfe der Webdienst-API {#assemble-multiple-xdp-fragments-using-the-web-service-api}

Assemblieren mehrerer XDP-Fragmente mithilfe der Assembler-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie beim Festlegen einer Dienstreferenz die folgende WSDL-Definition verwenden:

   ```as3
    http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen PDF Assembler-Client.

   * Erstellen Sie eine `AssemblerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `AssemblerServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt, z. B. `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `AssemblerServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie den Benutzernamen AEM Formulare dem `AssemblerServiceClient.ClientCredentials.UserName.UserName` -Feld.
      * Weisen Sie den entsprechenden Kennwortwert dem `AssemblerServiceClient.ClientCredentials.UserName.Password`-Feld.
      * Zuweisen der `HttpClientCredentialType.Basic` Konstantenwert zum `BasicHttpBindingSecurity.Transport.ClientCredentialType`-Feld.
      * Zuweisen der `BasicHttpSecurityMode.TransportCredentialOnly` Konstantenwert zum `BasicHttpBindingSecurity.Security.Mode`-Feld.

1. Referenzieren Sie ein vorhandenes DDX-Dokument.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des DDX-Dokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des DDX-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die Stream-Länge zum Lesen.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Referenzieren Sie die XDP-Dokumente.

   * Erstellen Sie für jede XDP-Eingabedatei eine `BLOB` -Objekt durch Verwendung seines -Konstruktors. Die `BLOB` -Objekt wird zum Speichern der Eingabedatei verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort der Eingabedatei und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die Stream-Länge zum Lesen.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Feld mit dem Inhalt des Byte-Arrays.
   * Erstellen Sie eine `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Dieses Collection-Objekt wird zum Speichern von Eingabedateien verwendet, die zum Erstellen eines assemblierten XDP-Dokuments erforderlich sind.
   * Erstellen Sie für jede Eingabedatei eine `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Weisen Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` -Feld. Dieser Wert muss mit dem Wert des im DDX-Dokument angegebenen Elements übereinstimmen. (Führen Sie diese Aufgabe für jede XDP-Eingabedatei aus.)
   * Zuweisen der `BLOB` -Objekt, das die Eingabedatei im `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` -Feld. (Führen Sie diese Aufgabe für jede XDP-Eingabedatei aus.)
   * Fügen Sie die `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. Rufen Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt `Add` -Methode und übergeben Sie die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt. (Führen Sie diese Aufgabe für jedes XDP-Eingabedokument aus.)

1. Legen Sie Laufzeitoptionen fest.

   * Erstellen Sie eine `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen mithilfe seines Konstruktors speichert.
   * Legen Sie Laufzeitoptionen fest, um Ihre Geschäftsanforderungen zu erfüllen, indem Sie einem Datenelement einen Wert zuweisen, der zum `AssemblerOptionSpec` -Objekt. Um beispielsweise den Assembler-Dienst anzuweisen, die Verarbeitung eines Auftrags fortzusetzen, wenn ein Fehler auftritt, weisen Sie `false` der `AssemblerOptionSpec` -Objekt `failOnError` Datenelement.

1. Assemblieren Sie mehrere XDP-Dokumente.

   Rufen Sie die `AssemblerServiceClient` -Objekt `invokeDDX` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das DDX-Dokument darstellt
   * Die `MyMapOf_xsd_string_To_xsd_anyType` -Objekt, das die erforderlichen Dateien enthält
   * Ein `AssemblerOptionSpec` -Objekt, das Laufzeitoptionen angibt

   Die `invokeDDX` -Methode gibt eine `AssemblerResult` -Objekt, das die Ergebnisse des Auftrags sowie alle aufgetretenen Ausnahmen enthält.

1. Rufen Sie das assemblierte XDP-Dokument ab.

   Um das neu erstellte XDP-Dokument abzurufen, führen Sie die folgenden Aktionen aus:

   * Zugriff auf `AssemblerResult` -Objekt `documents` -Feld, das ein `Map` -Objekt, das die resultierenden PDF-Dokumente enthält.
   * Iteration durch die `Map` -Objekt, um jedes Zieldokument abzurufen. Dann die `value` zu `BLOB`.
   * Extrahieren Sie die Binärdaten, die das PDF-Dokument darstellen, indem Sie auf dessen `BLOB` -Objekt `MTOM` -Eigenschaft. Dadurch wird ein Array von Bytes zurückgegeben, die Sie in eine XDP-Datei schreiben können.

**Siehe auch**

[Assemblieren mehrerer XDP-Fragmente](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
