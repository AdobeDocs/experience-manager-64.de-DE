---
title: Formulardaten berechnen
seo-title: Calculating Form Data
description: Verwenden Sie den Forms-Dienst, um die Werte zu berechnen, die ein Benutzer in ein Formular eingibt, und die Ergebnisse anzuzeigen. Der Forms-Dienst berechnet die Werte mithilfe der Java-API und der Web Service-API.
seo-description: Use the Forms service to calculate values that a user enters into a form and display the results. Forms service calculates the values using the Java API and Web Service API.
uuid: ccd85bc7-8ccc-44d9-9424-dfc1f603e688
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: b4f57e42-60a6-407d-9764-15a11615827d
role: Developer
exl-id: 476b1c78-8332-4a79-93dc-a615ec58abbe
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1853'
ht-degree: 2%

---

# Formulardaten berechnen {#calculating-form-data}

Der Forms-Dienst kann die Werte berechnen, die ein Benutzer in ein Formular eingibt, und die Ergebnisse anzeigen. Zur Berechnung der Formulardaten müssen Sie zwei Aufgaben ausführen. Erstellen Sie zunächst ein Formularentwurfsskript, das Formulardaten berechnet. Ein Formularentwurf unterstützt drei Arten von Skripten. Ein Skripttyp wird auf dem Client ausgeführt, ein anderer auf dem Server und der dritte auf dem Server und auf dem Client. Der in diesem Thema beschriebene Skripttyp wird auf dem Server ausgeführt. Serverseitige Berechnungen werden für HTML-, PDF- und Formularhandbuchtransformationen (nicht mehr unterstützt) unterstützt.

Im Rahmen des Formularentwurfsprozesses können Sie Berechnungen und Skripten verwenden, um ein besseres Benutzererlebnis zu bieten. Berechnungen und Skripten können den meisten Formularfeldern und -objekten hinzugefügt werden. Sie müssen ein Formularentwurfsskript erstellen, um Berechnungsvorgänge für Daten durchzuführen, die ein Benutzer in ein interaktives Formular eingibt.

Der Benutzer gibt Werte in das Formular ein und klickt auf die Schaltfläche Berechnen , um die Ergebnisse anzuzeigen. Im folgenden Prozess wird eine Beispielanwendung beschrieben, mit der ein Benutzer Daten berechnen kann:

* Der Benutzer greift auf eine HTML-Seite mit dem Namen StartLoan.html zu, die als Startseite der Webanwendung fungiert. Diese Seite ruft ein Java-Servlet mit dem Namen `GetLoanForm`.
* Die `GetLoanForm` Servlet rendert ein Darlehensformular. Dieses Formular enthält ein Skript, interaktive Felder, eine Berechnungsschaltfläche und eine Senden-Schaltfläche.
* Der Benutzer gibt Werte in die Felder des Formulars ein und klickt auf die Schaltfläche Berechnen . Das Formular wird an die `CalculateData` Java-Servlet, wo das Skript ausgeführt wird. Das Formular wird mit den im Formular angezeigten Berechnungsergebnissen an den Benutzer zurückgesendet.
* Der Benutzer gibt die Werte weiter ein und berechnet sie, bis ein zufriedenstellendes Ergebnis angezeigt wird. Wenn der Benutzer zufrieden ist, klickt er auf die Schaltfläche Senden , um das Formular zu verarbeiten. Das Formular wird an ein anderes Java-Servlet mit dem Namen `ProcessForm` , der für das Abrufen der gesendeten Daten verantwortlich ist. (Siehe [Umgang mit übermittelten Forms](/help/forms/developing/rendering-forms.md#handling-submitted-forms).

Das folgende Diagramm zeigt den Logikfluss der Anwendung.

![cf_cf_finsrv_loancalcapp_v1](assets/cf_cf_finsrv_loancalcapp_v1.png)

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
   <td><p>Die <code>GetLoanForm</code> Java Servlet wird von der HTML-Startseite aus aufgerufen. </p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>Die <code>GetLoanForm</code> Java Servlet verwendet die Client-API des Forms-Dienstes, um das Darlehensformular an den Client-Webbrowser zu rendern. Der Unterschied zwischen der Wiedergabe eines Formulars, das ein für die Ausführung auf dem Server konfiguriertes Skript enthält, und der Wiedergabe eines Formulars, das kein Skript enthält, besteht darin, dass Sie den Zielspeicherort angeben müssen, der zum Ausführen des Skripts verwendet wird. Wenn kein Zielspeicherort angegeben ist, wird ein Skript, das für die Ausführung auf dem Server konfiguriert ist, nicht ausgeführt. Betrachten Sie beispielsweise die in diesem Abschnitt eingeführte Anwendung. Die <code>CalculateData</code> Java Servlet ist der Zielspeicherort, an dem das Skript ausgeführt wird.</p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>Der Benutzer gibt Daten in interaktive Felder ein und klickt auf die Schaltfläche Berechnen . Das Formular wird an die <code>CalculateData</code> Java-Servlet, wo das Skript ausgeführt wird. </p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>Das Formular wird im Webbrowser wiedergegeben, wobei die Berechnungsergebnisse im Formular angezeigt werden. </p></td> 
  </tr> 
  <tr> 
   <td><p>5</p></td> 
   <td><p>Der Benutzer klickt auf die Schaltfläche Senden , wenn die Werte zufriedenstellend sind. Das Formular wird an ein anderes Java-Servlet mit dem Namen <code>ProcessForm</code>.</p></td> 
  </tr> 
 </tbody> 
</table>

Normalerweise enthält ein Formular, das als PDF-Inhalt gesendet wird, Skripte, die auf dem Client ausgeführt werden. Serverseitige Berechnungen können jedoch auch ausgeführt werden. Eine Senden-Schaltfläche kann nicht zur Berechnung von Skripten verwendet werden. In diesem Fall werden keine Berechnungen ausgeführt, da der Forms-Dienst die Interaktion für abgeschlossen hält.

Um die Verwendung eines Formularentwurfsskripts zu veranschaulichen, wird in diesem Abschnitt ein einfaches interaktives Formular untersucht, das ein Skript enthält, das für die Ausführung auf dem Server konfiguriert ist. Das folgende Diagramm zeigt einen Formularentwurf mit einem Skript, das Werte hinzufügt, die ein Benutzer in die ersten beiden Felder eingibt, und das Ergebnis im dritten Feld anzeigt.

![cf_cf_caldata](assets/cf_cf_caldata.png)

**A.** Ein Feld namens NumericField1 **B.** Ein Feld mit dem Namen NumericField2 **C.** Ein Feld namens NumericField3

Die Syntax des Skripts in diesem Formularentwurf lautet wie folgt:

```as3
     NumericField3 = NumericField2 + NumericField1
```

In diesem Formularentwurf ist die Schaltfläche &quot;Berechnen&quot;eine Befehlsschaltfläche und das Skript befindet sich in der `Click` -Ereignis. Wenn ein Benutzer Werte in die ersten beiden Felder (NumericField1 und NumericField2) eingibt und auf die Schaltfläche Berechnen klickt, wird das Formular an den Forms-Dienst gesendet, wo das Skript ausgeführt wird. Der Forms-Dienst rendert das Formular auf das Clientgerät zurück, wobei die Berechnungsergebnisse im Feld NumericField3 angezeigt werden.

>[!NOTE]
>
>Informationen zum Erstellen eines Formularentwurfsskripts finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um Formulardaten zu berechnen, führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Rufen Sie ein Formular mit einem Berechnungsskript ab.
1. Schreiben Sie den Formulardaten-Stream zurück in den Client-Webbrowser

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Dienst programmgesteuert ausführen können, müssen Sie einen Forms-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `FormsServiceClient` -Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie eine `FormsServiceService` -Objekt.

**Abrufen eines Formulars mit einem Berechnungsskript**

Sie verwenden die Client-API des Forms-Dienstes, um eine Anwendungslogik zu erstellen, die ein Formular verarbeitet, das ein Skript enthält, das für die Ausführung auf dem Server konfiguriert ist. Der Prozess ähnelt der Verarbeitung eines gesendeten Formulars. (Siehe [Umgang mit übermittelten Forms](/help/forms/developing/handling-submitted-forms.md).

Überprüfen Sie, ob der mit dem gesendeten Formular verknüpfte Verarbeitungsstatus `1` `(Calculate)`, was bedeutet, dass der Forms-Dienst einen Berechnungsvorgang für die Formulardaten durchführt und die Ergebnisse an den Benutzer zurückgeschrieben werden müssen. In diesem Fall wird automatisch ein Skript ausgeführt, das für die Ausführung auf dem Server konfiguriert wurde.

**Schreiben Sie den Formulardaten-Stream zurück in den Client-Webbrowser**

Nachdem Sie überprüft haben, ob der mit einem gesendeten Formular verknüpfte Verarbeitungsstatus `1`müssen Sie die Ergebnisse zurück in den Client-Webbrowser schreiben. Wenn das Formular angezeigt wird, erscheint der berechnete Wert in den entsprechenden Feldern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

## Formulardaten mit der Java-API berechnen {#calculate-form-data-using-the-java-api}

Berechnen Sie die Formulardaten mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `FormsServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Abrufen eines Formulars mit einem Berechnungsskript

   * Um Formulardaten abzurufen, die ein Berechnungsskript enthalten, erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Verwendung seines Konstruktors und Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getInputStream` -Methode innerhalb des Konstruktors.
   * Rufen Sie die `FormsServiceClient` -Objekt `processFormSubmission` -Methode verwenden und die folgenden Werte übergeben:

      * Die `com.adobe.idp.Document` -Objekt, das die Formulardaten enthält.
      * Ein string -Wert, der Umgebungsvariablen einschließlich aller relevanten HTTP-Header angibt. Sie müssen den Inhaltstyp angeben, der verarbeitet werden soll, indem Sie einen oder mehrere Werte für die `CONTENT_TYPE` Umgebungsvariable. Um beispielsweise XML- und PDF-Daten zu verarbeiten, geben Sie den folgenden Zeichenfolgenwert für diesen Parameter an: `CONTENT_TYPE=application/xml&CONTENT_TYPE=application/pdf`
      * Ein string -Wert, der die `HTTP_USER_AGENT` Header-Wert; Beispiel: `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen speichert.

      Die `processFormSubmission` -Methode gibt eine `FormsResult` -Objekt, das die Ergebnisse der Formularübermittlung enthält.

   * Überprüfen Sie, ob der mit einem gesendeten Formular verknüpfte Verarbeitungsstatus `1` durch Aufrufen der `FormsResult` -Objekt `getAction` -Methode. Wenn diese Methode den Wert zurückgibt `1`, wurde die Berechnung durchgeführt und die Daten können in den Client-Webbrowser zurückgeschrieben werden.


1. Schreiben Sie den Formulardaten-Stream zurück in den Client-Webbrowser

   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Senden eines Formulardaten-Streams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` -Objekt `read` -Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formulardaten mithilfe der Webdienst-API berechnen {#calculate-form-data-using-the-web-service-api}

Berechnen Sie Formulardaten mithilfe der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie eine `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Abrufen eines Formulars mit einem Berechnungsskript

   * Um Formulardaten abzurufen, die in einem Java-Servlet veröffentlicht wurden, erstellen Sie eine `BLOB` -Objekt durch Verwendung seines -Konstruktors.
   * Erstellen Sie eine `java.io.InputStream` -Objekt mithilfe der `javax.servlet.http.HttpServletResponse` -Objekt `getInputStream` -Methode.
   * Erstellen Sie eine `java.io.ByteArrayOutputStream` -Objekt mithilfe des Konstruktors und Übergabe der Länge des `java.io.InputStream` -Objekt.
   * Den Inhalt der `java.io.InputStream` Objekt in `java.io.ByteArrayOutputStream` -Objekt.
   * Erstellen Sie ein Byte-Array durch Aufrufen der `java.io.ByteArrayOutputStream` -Objekt `toByteArray` -Methode.
   * Füllen Sie die `BLOB` -Objekt durch Aufrufen seiner `setBinaryData` -Methode verwenden und das Byte-Array als Argument übergeben.
   * Erstellen Sie ein Objekt `RenderOptionsSpec`, indem Sie den Konstruktor verwenden. Festlegen des Gebietsschemawerts durch Aufrufen der `RenderOptionsSpec` -Objekt `setLocale` -Methode verwenden und einen string -Wert übergeben, der den Gebietsschema-Wert angibt.
   * Rufen Sie die `FormsServiceClient` -Objekt `processFormSubmission` -Methode verwenden und die folgenden Werte übergeben:

      * Die `BLOB` -Objekt, das die Formulardaten enthält.
      * Ein string -Wert, der Umgebungsvariablen angibt, die alle relevanten HTTP-Header enthalten. Sie können beispielsweise den folgenden Zeichenfolgenwert angeben: `HTTP_REFERER=referrer&HTTP_CONNECTION=keep-alive&CONTENT_TYPE=application/xml`
      * Ein string -Wert, der die `HTTP_USER_AGENT` Header-Wert; Beispiel: `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * A `RenderOptionsSpec` -Objekt, das Laufzeitoptionen speichert. Für weitere Informationen, .
      * Ein leeres `BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode aufgefüllt wird.
      * Ein leeres `BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird.
      * Ein leeres `BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird.
      * Ein leeres `javax.xml.rpc.holders.ShortHolder` -Objekt, das von der -Methode aufgefüllt wird.
      * Ein leeres `MyArrayOf_xsd_anyTypeHolder` -Objekt, das von der -Methode aufgefüllt wird. Dieser Parameter wird zum Speichern von Dateianlagen verwendet, die zusammen mit dem Formular gesendet werden.
      * Ein leeres `FormsResultHolder` -Objekt, das von der -Methode mit dem gesendeten Formular gefüllt wird.

      Die `processFormSubmission` -Methode füllt die `FormsResultHolder` mit den Ergebnissen der Formularübermittlung. Die `processFormSubmission` -Methode gibt eine `FormsResult` -Objekt, das die Ergebnisse der Formularübermittlung enthält.

   * Überprüfen Sie, ob der mit einem gesendeten Formular verknüpfte Verarbeitungsstatus `1` durch Aufrufen der `FormsResult` -Objekt `getAction` -Methode. Wenn diese Methode den Wert zurückgibt `1`, wurde die Berechnung durchgeführt und die Daten können in den Client-Webbrowser zurückgeschrieben werden.


1. Schreiben Sie den Formulardaten-Stream zurück in den Client-Webbrowser

   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Senden eines Formulardaten-Streams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `BLOB` -Objekt `getBinaryData` -Methode. Diese Aufgabe weist den Inhalt des `FormsResult` -Objekt zum Byte-Array hinzu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
