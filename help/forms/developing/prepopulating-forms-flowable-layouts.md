---
title: Vorausfüllen von Forms mit flexiblen Layouts
seo-title: Prepopulating Forms with Flowable Layouts
description: Füllen Sie Formulare mit flexiblem Layout im Voraus aus, um mithilfe der Java-API und der Web Service-API Daten für Benutzer in einem wiedergegebenen Formular anzuzeigen.
seo-description: Prepopulate forms with flowable layout to display data to users within a rendered form using the Java API and the Web Service API.
uuid: 93ccb496-e1c2-4b79-8e89-7a2abfce1537
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 30a12fc6-07b8-4c7c-b9e2-caa2bec0ac48
role: Developer
exl-id: 92bc6878-6963-442a-8441-fba42e89c859
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '3505'
ht-degree: 4%

---

# Vorausfüllen von Forms mit flexiblen Layouts {#prepopulating-forms-with-flowable-layouts1}

## Vorausfüllen von Forms mit flexiblen Layouts {#prepopulating-forms-with-flowable-layouts2}

Beim Vorausfüllen von Formularen werden Daten für Benutzer in einem wiedergegebenen Formular angezeigt. Angenommen, ein Benutzer meldet sich auf einer Website mit einem Benutzernamen und einem Kennwort an. Bei erfolgreicher Authentifizierung fragt die Client-Anwendung eine Datenbank nach Benutzerinformationen ab. Die Daten werden mit dem Formular zusammengeführt und das Formular wird dann für den Benutzer wiedergegeben. Dadurch kann der Benutzer personalisierte Daten im Formular anzeigen.

Das Vorausfüllen eines Formulars hat die folgenden Vorteile:

* Ermöglicht dem Benutzer das Anzeigen benutzerdefinierter Daten in einem Formular.
* Verringert den Tippaufwand, den der Benutzer beim Ausfüllen eines Formulars hat.
* Stellt die Datenintegrität sicher, indem gesteuert wird, wo die Daten platziert werden.

Die folgenden beiden XML-Datenquellen können ein Formular im Voraus ausfüllen:

* Eine XDP-Datenquelle, die der XFA-Syntax entspricht (oder XFDF-Daten, um ein mit Acrobat erstelltes Formular im Voraus auszufüllen).
* Eine beliebige XML-Datenquelle, die Name/Wert-Paare enthält, die mit den Feldnamen des Formulars übereinstimmen (die Beispiele in diesem Abschnitt verwenden eine beliebige XML-Datenquelle).

Für jedes Formularfeld, das vorausgefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Es ist nicht erforderlich, die Reihenfolge der Anzeige der XML-Elemente einzuhalten, solange alle XML-Elemente angegeben sind.

Wenn Sie ein Formular vorab ausfüllen, das bereits Daten enthält, müssen Sie die Daten angeben, die bereits in der XML-Datenquelle angezeigt werden. Angenommen, ein Formular mit 10 Feldern enthält Daten in vier Feldern. Nehmen wir als Nächstes an, dass Sie die restlichen sechs Felder im Voraus ausfüllen möchten. In diesem Fall müssen Sie 10 XML-Elemente in der XML-Datenquelle angeben, die zum Vorausfüllen des Formulars verwendet wird. Wenn Sie nur sechs Elemente angeben, sind die ursprünglichen vier Felder leer.

Sie können beispielsweise ein Formular wie das Beispielbestätigungsformular im Voraus ausfüllen. (Siehe &quot;Bestätigungsformular&quot;in [Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md).

Um das Beispielbestätigungsformular im Voraus auszufüllen, müssen Sie eine XML-Datenquelle erstellen, die drei XML-Elemente enthält, die den drei Feldern im Formular entsprechen. Dieses Formular enthält die folgenden drei Felder: `FirstName`, `LastName`und `Amount`. Der erste Schritt besteht darin, eine XML-Datenquelle zu erstellen, die XML-Elemente enthält, die mit den Feldern im Formularentwurf übereinstimmen. Der nächste Schritt besteht darin, den XML-Elementen Datenwerte zuzuweisen, wie im folgenden XML-Code dargestellt.

```as3
     <Untitled> 
         <FirstName>Jerry</FirstName> 
         <LastName>Johnson</LastName> 
         <Amount>250000</Amount> 
     </Untitled>
```

Nachdem Sie das Bestätigungsformular mit dieser XML-Datenquelle ausgefüllt und dann das Formular wiedergegeben haben, werden die den XML-Elementen zugewiesenen Datenwerte angezeigt, wie im folgenden Diagramm dargestellt.

![pf_pf_validationXML3](assets/pf_pf_confirmxml3.png)

### Vorausfüllen von Formularen mit flexiblen Layouts {#prepopulating_forms_with_flowable_layouts-1}

Forms mit flexiblen Layouts ist nützlich, um Benutzern eine unbestimmte Datenmenge anzuzeigen. Da sich das Layout des Formulars automatisch an die Datenmenge anpasst, die zusammengeführt wird, müssen Sie für das Formular kein festes Layout oder keine feste Seitenanzahl vorab festlegen, wie es für ein Formular mit festem Layout erforderlich ist.

Ein Formular wird in der Regel mit Daten gefüllt, die während der Laufzeit abgerufen werden. Daher können Sie ein Formular im Voraus ausfüllen, indem Sie eine XML-Datenquelle im Arbeitsspeicher erstellen und die Daten direkt in die XML-Datenquelle im Arbeitsspeicher platzieren.

Stellen Sie sich eine webbasierte Anwendung vor, z. B. einen Online-Store. Nachdem ein Online-Käufer den Kauf von Artikeln abgeschlossen hat, werden alle gekauften Artikel in eine XML-Datenquelle im Arbeitsspeicher eingefügt, die zum Vorausfüllen eines Formulars verwendet wird. Das folgende Diagramm zeigt diesen Vorgang, der in der Tabelle nach dem Diagramm erläutert wird.

![pf_pf_finsrv_webapp_v1](assets/pf_pf_finsrv_webapp_v1.png)

Die folgende Tabelle beschreibt die Schritte in diesem Diagramm.

<table> 
 <thead> 
  <tr> 
   <th><p>Schritt</p></th> 
   <th><p>Beschreibung</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>1</p></td> 
   <td><p>Ein Benutzer kauft Artikel aus einem webbasierten Online-Store. </p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>Nachdem der Benutzer den Kauf abgeschlossen hat und auf die Senden -Schaltfläche klickt, wird eine XML-Datenquelle im Arbeitsspeicher erstellt. Die gekauften Elemente und Benutzerinformationen werden in die XML-Datenquelle des Arbeitsspeichers eingefügt. </p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>Die XML-Datenquelle dient zum Vorausfüllen eines Bestellformulars (ein Beispiel für dieses Formular finden Sie in dieser Tabelle). </p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>Das Bestellformular wird im Client-Webbrowser wiedergegeben. </p></td> 
  </tr> 
 </tbody> 
</table>

Das folgende Diagramm zeigt ein Beispiel für ein Bestellformular. Die Informationen in der Tabelle können an die Anzahl der Datensätze in den XML-Daten angepasst werden.

![pf_pf_poform](assets/pf_pf_poform.png)

>[!NOTE]
>
>Ein Formular kann mit Daten aus anderen Quellen wie z. B. einer Unternehmensdatenbank oder externen Anwendungen vorausgefüllt werden.

### Überlegungen zum Formularentwurf {#form-design-considerations}

Forms mit flexiblen Layouts basieren auf Formularentwürfen, die in Designer erstellt werden. Ein Formularentwurf gibt einen Satz von Layout-, Darstellungs- und Datenerfassungsregeln an, einschließlich der Berechnung von Werten basierend auf der Benutzereingabe. Die Regeln werden angewendet, wenn Daten in ein Formular eingegeben werden. Felder, die einem Formular hinzugefügt werden, sind Teilformulare, die sich im Formularentwurf befinden. Im Bestellformular, das im vorherigen Diagramm dargestellt wird, ist jede Zeile beispielsweise ein Teilformular. Informationen zum Erstellen eines Formularentwurfs mit Teilformularen finden Sie unter [Bestellformular mit flexiblem Layout erstellen](https://www.adobe.com/go/learn_aemforms_qs_poformflowable_9).

### Grundlagen zu Datenuntergruppen {#understanding-data-subgroups}

Eine XML-Datenquelle dient zum Vorausfüllen von Formularen mit festen Layouts und flexiblen Layouts. Der Unterschied besteht jedoch darin, dass eine XML-Datenquelle, die ein Formular mit flexiblem Layout im Voraus ausfüllt, sich wiederholende XML-Elemente enthält, die zum Vorausfüllen von Teilformularen verwendet werden, die innerhalb des Formulars wiederholt werden. Diese sich wiederholenden XML-Elemente werden als Datenuntergruppen bezeichnet.

Eine XML-Datenquelle, mit der das im vorherigen Diagramm dargestellte Bestellformular im Voraus ausgefüllt wird, enthält vier sich wiederholende Datenuntergruppen. Jede Datenuntergruppe entspricht einem gekauften Artikel. Die gekauften Artikel sind ein Monitor, eine Schreibtischleuchte, ein Telefon und ein Adressbuch.

Die folgende XML-Datenquelle dient zum Vorausfüllen des Bestellformulars.

```as3
     <header>  
         <!-- XML elements used to prepopulate non-repeating fields such as address 
         <!and city  
         <txtPONum>8745236985</txtPONum>  
         <dtmDate>2004-02-08</dtmDate>  
         <txtOrderedByCompanyName>Any Company Name</txtOrderedByCompanyName>  
         <txtOrderedByAddress>555, Any Blvd.</txtOrderedByAddress>  
         <txtOrderedByCity>Any City</txtOrderedByCity>  
         <txtOrderedByStateProv>ST</txtOrderedByStateProv>  
         <txtOrderedByZipCode>12345</txtOrderedByZipCode>  
         <txtOrderedByCountry>Any Country</txtOrderedByCountry>  
         <txtOrderedByPhone>(123) 456-7890</txtOrderedByPhone>  
         <txtOrderedByFax>(123) 456-7899</txtOrderedByFax>  
         <txtOrderedByContactName>Contact Name</txtOrderedByContactName>  
         <txtDeliverToCompanyName>Any Company Name</txtDeliverToCompanyName>  
         <txtDeliverToAddress>7895, Any Street</txtDeliverToAddress>  
         <txtDeliverToCity>Any City</txtDeliverToCity>  
         <txtDeliverToStateProv>ST</txtDeliverToStateProv>  
         <txtDeliverToZipCode>12346</txtDeliverToZipCode>  
         <txtDeliverToCountry>Any Country</txtDeliverToCountry>  
         <txtDeliverToPhone>(123) 456-7891</txtDeliverToPhone>  
         <txtDeliverToFax>(123) 456-7899</txtDeliverToFax>  
         <txtDeliverToContactName>Contact Name</txtDeliverToContactName>  
     </header>  
     <detail>  
         <!-- A data subgroup that contains information about the monitor> 
         <txtPartNum>00010-100</txtPartNum>  
         <txtDescription>Monitor</txtDescription>  
         <numQty>1</numQty>  
         <numUnitPrice>350.00</numUnitPrice>  
     </detail>  
     <detail>  
         <!-- A data subgroup that contains information about the desk lamp> 
         <txtPartNum>00010-200</txtPartNum>  
         <txtDescription>Desk lamps</txtDescription>  
         <numQty>3</numQty>  
         <numUnitPrice>55.00</numUnitPrice>  
     </detail>  
     <detail> 
         <!-- A data subgroup that contains information about the Phone> 
             <txtPartNum>00025-275</txtPartNum>  
             <txtDescription>Phone</txtDescription>  
             <numQty>5</numQty>  
             <numUnitPrice>85.00</numUnitPrice>  
     </detail>  
     <detail> 
         <!-- A data subgroup that contains information about the address book> 
         <txtPartNum>00300-896</txtPartNum>  
         <txtDescription>Address book</txtDescription>  
         <numQty>2</numQty>  
         <numUnitPrice>15.00</numUnitPrice>  
     </detail>
```

Beachten Sie, dass jede Datenuntergruppe vier XML-Elemente enthält, die diesen Informationen entsprechen:

* Artikelteilnummer
* Beschreibung der Elemente
* Artikelmenge
* Stückpreis

Der Name des übergeordneten XML-Elements einer Datenuntergruppe muss mit dem Namen des Teilformulars übereinstimmen, das sich im Formularentwurf befindet. Beachten Sie beispielsweise im vorherigen Diagramm, dass der Name des übergeordneten XML-Elements der Datenuntergruppe lautet `detail`. Dies entspricht dem Namen des Teilformulars, das sich im Formularentwurf befindet, auf dem das Bestellformular basiert. Wenn der Name des übergeordneten XML-Elements der Datenuntergruppe und des Teilformulars nicht übereinstimmen, wird kein serverseitiges Formular vorausgefüllt.

Jede Datenuntergruppe muss XML-Elemente enthalten, die mit den Feldnamen im Teilformular übereinstimmen. Die `detail` Das Teilformular im Formularentwurf enthält die folgenden Felder:

* txtPartNum
* txtDescription
* numQty
* numUnitPrice

>[!NOTE]
>
>Wenn Sie versuchen, ein Formular mit einer Datenquelle zu füllen, die sich wiederholende XML-Elemente enthält, und legen Sie die `RenderAtClient` -Option `No`, wird nur der erste Datensatz mit dem Formular zusammengeführt. Um sicherzustellen, dass alle Datensätze mit dem Formular zusammengeführt werden, legen Sie die `RenderAtClient` nach `Yes`. Informationen zum `RenderAtClient` , siehe [Rendern von Forms auf dem Client](/help/forms/developing/rendering-forms-client.md).

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein Formular mit flexiblem Layout im Voraus auszufüllen:

1. Projektdateien einschließen.
1. Erstellen Sie eine speicherinterne XML-Datenquelle.
1. Konvertieren Sie die XML-Datenquelle.
1. Wiedergabe eines vorausgefüllten Formulars.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen einer speicherinternen XML-Datenquelle**

Sie können `org.w3c.dom` Klassen verwenden, um eine XML-Datenquelle im Arbeitsspeicher zu erstellen, um ein Formular mit flexiblem Layout im Voraus auszufüllen. Sie müssen Daten in eine XML-Datenquelle platzieren, die dem Formular entspricht. Informationen zur Beziehung zwischen einem Formular mit flexiblem Layout und der XML-Datenquelle finden Sie unter [Grundlagen zu Datenuntergruppen](#understanding-data-subgroups).

**Konvertieren der XML-Datenquelle**

Eine XML-Datenquelle im Arbeitsspeicher, die mithilfe von `org.w3c.dom` -Klassen in eine `com.adobe.idp.Document` -Objekt, bevor es zum Vorausfüllen eines Formulars verwendet werden kann. Eine XML-Datenquelle im Arbeitsspeicher kann mithilfe von Java XML Transformation-Klassen konvertiert werden.

>[!NOTE]
>
>Wenn Sie die WSDL des Forms-Dienstes zum Vorausfüllen eines Formulars verwenden, müssen Sie eine `org.w3c.dom.Document` Objekt in ein `BLOB` -Objekt.

**Vorausgefülltes Formular wiedergeben**

Sie rendern ein vorausgefülltes Formular wie ein anderes. Der einzige Unterschied besteht darin, dass Sie die `com.adobe.idp.Document` -Objekt, das die XML-Datenquelle enthält, um das Formular im Voraus auszufüllen.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

### Vorausfüllen von Formularen mit der Java-API {#prepopulating-forms-using-the-java-api}

So füllen Sie ein Formular mit einem flexiblen Layout mithilfe der Forms API (Java) im Voraus aus:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Erstellen einer speicherinternen XML-Datenquelle

   * Java erstellen `DocumentBuilderFactory` -Objekt durch Aufruf der `DocumentBuilderFactory` class&quot; `newInstance` -Methode.
   * Java erstellen `DocumentBuilder` -Objekt durch Aufruf der `DocumentBuilderFactory` -Objekt `newDocumentBuilder` -Methode.
   * Rufen Sie die `DocumentBuilder` -Objekt `newDocument` -Methode zur Instanziierung einer `org.w3c.dom.Document` -Objekt.
   * Erstellen Sie das Stammelement der XML-Datenquelle, indem Sie die `org.w3c.dom.Document` -Objekt `createElement` -Methode. Dadurch wird eine `Element` -Objekt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Stammelement an das Dokument an, indem Sie die `Document` -Objekt `appendChild` und übergeben Sie das Stamdelement-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element root = (Element)document.createElement("transaction");  document.appendChild(root);`

   * Erstellen Sie das Kopfzeilenelement der XML-Datenquelle, indem Sie die `Document` -Objekt `createElement` -Methode. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Kopfzeilenelement an das Stammelement an, indem Sie die `root` -Objekt `appendChild` -Methode und übergeben Sie das Überschriftenelementobjekt als Argument. Die XML-Elemente, die an das Header-Element angehängt werden, entsprechen dem statischen Teil des Formulars. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element header = (Element)document.createElement("header");  root.appendChild(header);`

   * Erstellen Sie ein untergeordnetes Element, das zum Kopfzeilenelement gehört, indem Sie die `Document` -Objekt `createElement` und übergeben einen Zeichenfolgenwert, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `appendChild` und übergeben Sie die `Document` -Objekt `createTextNode` -Methode als Argument verwenden. Geben Sie einen Zeichenfolgenwert an, der als Wert des untergeordneten Elements angezeigt wird. Hängen Sie abschließend das untergeordnete Element an das Kopfzeilenelement an, indem Sie die `appendChild` -Methode und übergeben Sie das untergeordnete Element-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element poNum= (Element)document.createElement("txtPONum");  poNum.appendChild(document.createTextNode("8745236985"));  header.appendChild(LastName);`


   * Fügen Sie alle verbleibenden Elemente zum Kopfzeilenelement hinzu, indem Sie den letzten Unterschritt für jedes Feld wiederholen, das im statischen Teil des Formulars erscheint (im XML-Datenquellendiagramm werden diese Felder in Abschnitt A angezeigt. (Siehe [Grundlagen zu Datenuntergruppen](#understanding-data-subgroups).
   * Erstellen Sie das Detailelement der XML-Datenquelle, indem Sie die `Document` -Objekt `createElement` -Methode. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Detailelement an das Stammelement an, indem Sie die `root` -Objekt `appendChild` -Methode und übergeben Sie das Element &quot;detail&quot;als Argument. Die XML-Elemente, die an das Detailelement angehängt werden, entsprechen dem dynamischen Teil des Formulars. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element detail = (Element)document.createElement("detail");  root.appendChild(detail);`

   * Erstellen Sie ein untergeordnetes Element, das zum Detailelement gehört, indem Sie die `Document` -Objekt `createElement` und übergeben einen Zeichenfolgenwert, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `appendChild` und übergeben Sie die `Document` -Objekt `createTextNode` -Methode als Argument verwenden. Geben Sie einen Zeichenfolgenwert an, der als Wert des untergeordneten Elements angezeigt wird. Hängen Sie abschließend das untergeordnete Element an das Detailelement an, indem Sie die `appendChild` -Methode und übergeben Sie das untergeordnete Element-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element txtPartNum = (Element)document.createElement("txtPartNum");  txtPartNum.appendChild(document.createTextNode("00010-100"));  detail.appendChild(txtPartNum);`

   * Wiederholen Sie den letzten Unterschritt für alle XML-Elemente, die an das Detailelement angehängt werden sollen. Um die XML-Datenquelle, die zum Ausfüllen des Bestellformulars verwendet wird, ordnungsgemäß zu erstellen, müssen Sie die folgenden XML-Elemente an das Detailelement anhängen: `txtDescription`, `numQty`und `numUnitPrice`.
   * Wiederholen Sie die letzten beiden Unterschritte für alle Datenelemente, die zum Vorausfüllen des Formulars verwendet werden.

1. Konvertieren der XML-Datenquelle

   * Erstellen Sie eine `javax.xml.transform.Transformer` -Objekt durch Aufrufen der `javax.xml.transform.Transformer` Statische Objektform `newInstance` -Methode.
   * Erstellen Sie eine `Transformer` -Objekt durch Aufrufen der `TransformerFactory` -Objekt `newTransformer` -Methode.
   * Erstellen Sie ein Objekt `ByteArrayOutputStream`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie eine `javax.xml.transform.dom.DOMSource` -Objekt durch Verwendung seines Konstruktors und Übergabe des `org.w3c.dom.Document` -Objekt, das in Schritt 1 erstellt wurde.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource`-Objekt, indem Sie seinen Konstruktor verwenden und das `ByteArrayOutputStream`-Objekt übergeben.
   * Java ausfüllen `ByteArrayOutputStream` -Objekt durch Aufrufen der `javax.xml.transform.Transformer` -Objekt `transform` -Methode und Übergabe der `javax.xml.transform.dom.DOMSource` und `javax.xml.transform.stream.StreamResult` Objekte.
   * Erstellen Sie ein Byte-Array und weisen Sie die Größe der `ByteArrayOutputStream` -Objekt zum Byte-Array hinzu.
   * Füllen Sie das Byte-Array, indem Sie die `ByteArrayOutputStream` -Objekt `toByteArray` -Methode.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, indem Sie seinen Konstruktor verwenden und das Byte-Array übergeben.

1. Vorausgefülltes Formular wiedergeben

   Rufen Sie die `FormsServiceClient` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * A `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das in den Schritten 1 und 2 erstellt wurde.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Senden eines Formulardaten-Streams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array, das mit dem Formulardatenstream gefüllt wird, indem Sie die `InputStream` -Objekt `read` -Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.


**Siehe auch**

[Schnellstart (SOAP-Modus): Vorausfüllen von Forms mit flexiblen Layouts mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Vorausfüllen von Formularen mit der Webdienst-API {#prepopulating-forms-using-the-web-service-api}

So füllen Sie ein Formular mit einem flexiblen Layout mithilfe der Forms-API (Webdienst) im Voraus aus:

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden. (Siehe [Erstellen von Java-Proxy-Klassen mit Apache Axis](/help/forms/developing/invoking-aem-forms-using-web.md#creating-java-proxy-classes-using-apache-axis).
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen einer speicherinternen XML-Datenquelle

   * Java erstellen `DocumentBuilderFactory` -Objekt durch Aufruf der `DocumentBuilderFactory` class&quot; `newInstance` -Methode.
   * Java erstellen `DocumentBuilder` -Objekt durch Aufruf der `DocumentBuilderFactory` -Objekt `newDocumentBuilder` -Methode.
   * Rufen Sie die `DocumentBuilder` -Objekt `newDocument` -Methode zur Instanziierung einer `org.w3c.dom.Document` -Objekt.
   * Erstellen Sie das Stammelement der XML-Datenquelle, indem Sie die `org.w3c.dom.Document` -Objekt `createElement` -Methode. Dadurch wird eine `Element` -Objekt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Stammelement an das Dokument an, indem Sie die `Document` -Objekt `appendChild` und übergeben Sie das Stamdelement-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element root = (Element)document.createElement("transaction");  document.appendChild(root);`

   * Erstellen Sie das Kopfzeilenelement der XML-Datenquelle, indem Sie die `Document` -Objekt `createElement` -Methode. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Kopfzeilenelement an das Stammelement an, indem Sie die `root` -Objekt `appendChild` -Methode und übergeben Sie das Überschriftenelementobjekt als Argument. Die XML-Elemente, die an das Header-Element angehängt werden, entsprechen dem statischen Teil des Formulars. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element header = (Element)document.createElement("header");  root.appendChild(header);`

   * Erstellen Sie ein untergeordnetes Element, das zum Kopfzeilenelement gehört, indem Sie die `Document` -Objekt `createElement` und übergeben einen Zeichenfolgenwert, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `appendChild` und übergeben Sie die `Document` -Objekt `createTextNode` -Methode als Argument verwenden. Geben Sie einen Zeichenfolgenwert an, der als Wert des untergeordneten Elements angezeigt wird. Hängen Sie abschließend das untergeordnete Element an das Kopfzeilenelement an, indem Sie die `appendChild` -Methode und übergeben Sie das untergeordnete Element-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element poNum= (Element)document.createElement("txtPONum");  poNum.appendChild(document.createTextNode("8745236985"));  header.appendChild(LastName);`

   * Fügen Sie alle verbleibenden Elemente zum Kopfzeilenelement hinzu, indem Sie den letzten Unterschritt für jedes Feld wiederholen, das im statischen Teil des Formulars erscheint (im XML-Datenquellendiagramm werden diese Felder in Abschnitt A angezeigt. (Siehe [Grundlagen zu Datenuntergruppen](#understanding-data-subgroups).
   * Erstellen Sie das Detailelement der XML-Datenquelle, indem Sie die `Document` -Objekt `createElement` -Methode. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` -Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Detailelement an das Stammelement an, indem Sie die `root` -Objekt `appendChild` -Methode und übergeben Sie das Element &quot;detail&quot;als Argument. Die XML-Elemente, die an das Detailelement angehängt werden, entsprechen dem dynamischen Teil des Formulars. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element detail = (Element)document.createElement("detail");  root.appendChild(detail);`

   * Erstellen Sie ein untergeordnetes Element, das zum Detailelement gehört, indem Sie die `Document` -Objekt `createElement` und übergeben einen Zeichenfolgenwert, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `appendChild` und übergeben Sie die `Document` -Objekt `createTextNode` -Methode als Argument verwenden. Geben Sie einen Zeichenfolgenwert an, der als Wert des untergeordneten Elements angezeigt wird. Hängen Sie abschließend das untergeordnete Element an das Detailelement an, indem Sie die `appendChild` -Methode und übergeben Sie das untergeordnete Element-Objekt als Argument. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element txtPartNum = (Element)document.createElement("txtPartNum");  txtPartNum.appendChild(document.createTextNode("00010-100"));  detail.appendChild(txtPartNum);`

   * Wiederholen Sie den letzten Unterschritt für alle XML-Elemente, die an das Detailelement angehängt werden sollen. Um die XML-Datenquelle, die zum Ausfüllen des Bestellformulars verwendet wird, ordnungsgemäß zu erstellen, müssen Sie die folgenden XML-Elemente an das Detailelement anhängen: `txtDescription`, `numQty`und `numUnitPrice`.
   * Wiederholen Sie die letzten beiden Unterschritte für alle Datenelemente, die zum Vorausfüllen des Formulars verwendet werden.

1. Konvertieren der XML-Datenquelle

   * Erstellen Sie eine `javax.xml.transform.Transformer` -Objekt durch Aufrufen der `javax.xml.transform.Transformer` Statische Objektform `newInstance` -Methode.
   * Erstellen Sie eine `Transformer` -Objekt durch Aufrufen der `TransformerFactory` -Objekt `newTransformer` -Methode.
   * Erstellen Sie ein Objekt `ByteArrayOutputStream`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie eine `javax.xml.transform.dom.DOMSource` -Objekt durch Verwendung seines Konstruktors und Übergabe des `org.w3c.dom.Document` -Objekt, das in Schritt 1 erstellt wurde.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource`-Objekt, indem Sie seinen Konstruktor verwenden und das `ByteArrayOutputStream`-Objekt übergeben.
   * Java ausfüllen `ByteArrayOutputStream` -Objekt durch Aufrufen der `javax.xml.transform.Transformer` -Objekt `transform` -Methode und Übergabe der `javax.xml.transform.dom.DOMSource` und `javax.xml.transform.stream.StreamResult` Objekte.
   * Erstellen Sie ein Byte-Array und weisen Sie die Größe der `ByteArrayOutputStream` -Objekt zum Byte-Array hinzu.
   * Füllen Sie das Byte-Array, indem Sie die `ByteArrayOutputStream` -Objekt `toByteArray` -Methode.
   * Erstellen Sie eine `BLOB` -Objekt mithilfe des -Konstruktors und Aufrufen der zugehörigen `setBinaryData` -Methode verwenden und das Byte-Array übergeben.

1. Vorausgefülltes Formular wiedergeben

   Rufen Sie die `FormsService` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * A `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Stellen Sie sicher, dass Sie die `BLOB` -Objekt, das in den Schritten 1 und 2 erstellt wurde.
   * A `PDFFormRenderSpecc` -Objekt, das Laufzeitoptionen speichert. Weitere Informationen finden Sie unter [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird. Damit wird das wiedergegebene PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular).
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert den Gebietsschemawert).
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm` -Methode füllt die `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das als letzter Argumentwert mit einem Formulardatenstream übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

   * Erstellen Sie eine `FormResult` -Objekt durch Abrufen des Werts der `com.adobe.idp.services.holders.FormsResultHolder` -Objekt `value` Datenelement.
   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `BLOB` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `BLOB` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `BLOB` -Objekt `getBinaryData` -Methode. Diese Aufgabe weist den Inhalt des `FormsResult` -Objekt zum Byte-Array hinzu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

   >[!NOTE]
   >
   >Die `renderPDFForm` -Methode füllt die `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das als letzter Argumentwert mit einem Formulardatenstream übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
