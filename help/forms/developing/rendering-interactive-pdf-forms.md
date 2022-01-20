---
title: Rendern interaktiver PDF forms
seo-title: Rendering Interactive PDF Forms
description: Verwenden Sie den Forms-Dienst, um interaktive PDF forms auf Clientgeräten, normalerweise Webbrowsern, zu rendern, um Benutzerinformationen zu erfassen. Sie können den Forms-Dienst verwenden, um interaktive Formulare mithilfe der Java-API und der Web Service-API zu rendern.
seo-description: Use the Forms service to render interactive PDF forms to client devices, typically web browsers, to collect information from users. You can use Forms service to render interactive forms using the Java API and Web Service API.
uuid: df2a4dc8-f19e-49de-850f-85a204102631
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 3cb307ec-9b7b-4f03-b860-48553ccee746
role: Developer
exl-id: 0bca3af9-78df-44e6-96ef-62bda24d0025
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2473'
ht-degree: 0%

---

# Rendern interaktiver PDF forms {#rendering-interactive-pdf-forms}

Der Forms-Dienst rendert interaktive PDF forms an Client-Geräte, normalerweise Webbrowser, um Benutzerinformationen zu erfassen. Nachdem ein interaktives Formular wiedergegeben wurde, kann ein Benutzer Daten in Formularfelder eingeben und auf eine Senden-Schaltfläche im Formular klicken, um Informationen zurück an den Forms-Dienst zu senden. Adobe Reader oder Acrobat müssen auf dem Computer installiert sein, der den Client-Webbrowser hostet, damit ein interaktives PDF-Formular sichtbar ist.

>[!NOTE]
>
>Bevor Sie ein Formular mit dem Forms-Dienst wiedergeben können, erstellen Sie einen Formularentwurf. In der Regel wird ein Formularentwurf in Designer erstellt und als XDP-Datei gespeichert. Informationen zum Erstellen eines Formularentwurfs finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

**Beispiel für einen Kreditantrag**

Ein Beispiel für einen Kreditantrag wird eingeführt, um zu veranschaulichen, wie der Forms-Dienst interaktive Formulare verwendet, um Informationen von Benutzern zu erfassen. Mit dieser Anwendung kann ein Benutzer ein Formular mit Daten ausfüllen, die zur Sicherung eines Kredits erforderlich sind, und dann Daten an den Forms-Dienst senden. Das folgende Diagramm zeigt den Logikfluss des Kreditantrags.

![ri_ri_finsrv_loanapp_v1](assets/ri_ri_finsrv_loanapp_v1.png)

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
   <td><p>Die <code>GetLoanForm</code> Java Servlet wird von einer HTML-Seite aufgerufen. </p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>Die <code>GetLoanForm</code> Java Servlet verwendet die Client-API des Forms-Dienstes, um das Darlehensformular an den Client-Webbrowser zu rendern. (Siehe <a href="#render-an-interactive-pdf-form-using-the-java-api">Rendern eines interaktiven PDF-Formulars mit der Java-API</a>.</p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>Nachdem der Benutzer das Darlehensformular ausgefüllt und auf die Senden-Schaltfläche geklickt hat, werden die Daten an die <code>HandleData</code> Java-Servlet. (Siehe <i>"Darlehensformular"</i>.</p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>Die <code>HandleData</code> Java Servlet verwendet die Client-API des Forms-Dienstes, um die Formularübermittlung zu verarbeiten und Formulardaten abzurufen. Die Daten werden dann in einer Unternehmensdatenbank gespeichert. (Siehe <a href="/help/forms/developing/handling-submitted-forms.md#handling-submitted-forms">Umgang mit übermittelten Forms</a>.</p></td> 
  </tr> 
  <tr> 
   <td><p>5</p></td> 
   <td><p>Ein Bestätigungsformular wird an den Webbrowser zurückgegeben. Daten wie der Vor- und Nachname des Benutzers werden mit dem Formular zusammengeführt, bevor es wiedergegeben wird. (Siehe <a href="/help/forms/developing/prepopulating-forms-flowable-layouts.md">Vorausfüllen von Forms mit flexiblen Layouts</a>.</p></td> 
  </tr> 
 </tbody> 
</table>

**Darlehensformular**

Dieses interaktive Darlehensformular wird durch die `GetLoanForm` Java-Servlet.

![ri_ri_loanform](assets/ri_ri_loanform.png)

**Bestätigungsformular**

Dieses Formular wird durch die `HandleData` Java-Servlet.

![ri_ri_confirm](assets/ri_ri_confirm.png)

Die `HandleData` Java Servlet füllt dieses Formular vorab mit dem Vor- und Nachnamen des Benutzers sowie dem Betrag. Nachdem das Formular vorausgefüllt wurde, wird es an den Client-Webbrowser gesendet. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md))

**Java-Servlets**

Der Beispielkreditantrag ist ein Beispiel für eine Forms-Dienstanwendung, die als Java-Servlet vorhanden ist. Ein Java-Servlet ist ein Java-Programm, das auf einem J2EE-Anwendungsserver wie WebSphere ausgeführt wird und den Client-API-Code des Forms-Dienstes enthält.

Der folgende Code zeigt die Syntax eines Java-Servlets mit dem Namen GetLoanForm:

```as3
     public class GetLoanForm extends HttpServlet implements Servlet { 
         public void doGet(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
          
         } 
         public void doPost(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
              
             }
```

Normalerweise platzieren Sie den Client-API-Code des Forms-Dienstes nicht in einem Java-Servlet `doGet` oder `doPost` -Methode. Es ist eine bessere Programmierungspraxis, diesen Code innerhalb einer separaten Klasse zu platzieren und die -Klasse aus der `doPost` -Methode oder `doGet` -Methode) und rufen Sie die entsprechenden Methoden auf. Die Codebeispiele in diesem Abschnitt werden jedoch für die Codereihenfolge auf ein Minimum beschränkt und Codebeispiele werden im `doPost` -Methode.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

**Zusammenfassung der Schritte**

Um ein interaktives PDF-Formular wiederzugeben, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Geben Sie URI-Werte an.
1. Anhängen von Dateien an das Formular (optional).
1. Rendern Sie ein interaktives PDF-Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Dienst programmgesteuert ausführen können, müssen Sie ein Forms Client-API-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `FormsServiceClient` -Objekt. Wenn Sie die Forms-Webdienst-API verwenden, erstellen Sie eine `FormsService` -Objekt.

**URI-Werte angeben**

Sie können URI-Werte angeben, die der Forms-Dienst zum Rendern eines Formulars benötigt. Ein Formularentwurf, der als Teil einer Forms-Anwendung gespeichert wird, kann mithilfe des Inhaltsstamm-URI-Werts referenziert werden `repository:///`. Betrachten Sie beispielsweise den folgenden Formularentwurf mit dem Namen *Loan.xdp* innerhalb einer Forms-Anwendung mit dem Namen *FormsApplication*:

![ri_ri_formrepository](assets/ri_ri_formrepository.png)

Um auf diesen Formularentwurf zuzugreifen, geben Sie `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` als Formularname (der erste Parameter, der an die `renderPDFForm` Methode) und `repository:///` als Inhaltsstamm-URI-Wert.

>[!NOTE]
>
>Informationen zum Erstellen einer Forms-Anwendung mit Workbench finden Sie unter [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63).

Der Pfad zu einer Ressource in einer Forms-Anwendung lautet:

`Applications/Application-name/Application-version/Folder.../Filename`

Die folgenden Werte zeigen einige Beispiele für URI-Werte:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

Beim Rendern eines interaktiven Formulars können Sie URI-Werte definieren, z. B. die Ziel-URL, an die die Formulardaten gesendet werden. Die Ziel-URL kann auf eine der folgenden Arten definiert werden:

* Auf der Schaltfläche &quot;Senden&quot;beim Entwerfen des Formularentwurfs in Designer
* Verwendung der Client-API des Forms-Dienstes

Wenn die Ziel-URL im Formularentwurf definiert ist, darf sie nicht mit der Client-API des Forms-Dienstes überschrieben werden. Das heißt, durch Festlegen der Ziel-URL mithilfe der Forms-API wird die angegebene URL im Formularentwurf auf die URL zurückgesetzt, die mithilfe der API angegeben wurde. Wenn Sie das PDF-Formular an die im Formularentwurf angegebene Ziel-URL senden möchten, legen Sie die Ziel-URL programmgesteuert auf eine leere Zeichenfolge fest.

Wenn Sie ein Formular mit einer Senden-Schaltfläche und einer Berechnungsschaltfläche (mit einem entsprechenden Skript, das auf dem Server ausgeführt wird) haben, können Sie programmgesteuert die URL definieren, an die das Formular gesendet wird, um das Skript auszuführen. Verwenden Sie die Senden-Schaltfläche im Formularentwurf, um die URL anzugeben, an die die Formulardaten gesendet werden. (Siehe [Formulardaten berechnen](/help/forms/developing/calculating-form-data.md).

>[!NOTE]
>
>Anstatt einen URL-Wert anzugeben, um auf eine XDP-Datei zu verweisen, können Sie auch eine `com.adobe.idp.Document` -Instanz auf den Forms-Dienst. Die `com.adobe.idp.Document` -Instanz enthält einen Formularentwurf. (Siehe [Übergeben von Dokumenten an den Forms-Dienst](/help/forms/developing/passing-documents-forms-service.md).

**Anhängen von Dateien an das Formular**

Sie können Dateien an ein Formular anhängen. Wenn Sie ein PDF-Formular mit Dateianlagen rendern, können Benutzer die Dateianlagen in Acrobat mithilfe des Bereichs Dateianlagen abrufen. Sie können verschiedene Dateitypen an ein Formular anhängen, z. B. eine Textdatei, oder an eine Binärdatei, z. B. eine JPG-Datei.

>[!NOTE]
>
>Das Anhängen von Dateianlagen an ein Formular ist optional.

**Rendern eines interaktiven PDF-Formulars**

Verwenden Sie zum Wiedergeben eines Formulars einen Formularentwurf, der in Designer erstellt und als XDP- oder PDF-Datei gespeichert wurde. Außerdem können Sie ein Formular wiedergeben, das mit Acrobat erstellt und als PDF-Datei gespeichert wurde. Rufen Sie zum Rendern eines interaktiven PDF-Formulars die `FormsServiceClient` -Objekt `renderPDFForm` Methode oder `renderPDFForm2` -Methode.

Die `renderPDFForm` verwendet eine `URLSpec` -Objekt. Der Inhaltsstamm an die XDP-Datei wird mithilfe der `URLSpec` -Objekt `setContentRootURI` -Methode. Der Name des Formularentwurfs ( `formQuery`) wird als separater Parameterwert übergeben. Die beiden Werte werden verkettet, um den absoluten Verweis auf den Formularentwurf zu erhalten.

Die `renderPDFForm2` -Methode akzeptiert eine `com.adobe.idp.Document` -Instanz, die das zu rendernde XDP- oder PDF-Dokument enthält.

>[!NOTE]
>
>Die Laufzeitoption für getaggte PDF kann nicht festgelegt werden, wenn das Eingabedokument ein PDF-Dokument ist. Wenn es sich bei der Eingabedatei um eine XDP-Datei handelt, kann die getaggte PDF-Option festgelegt werden.

## Rendern eines interaktiven PDF-Formulars mit der Java-API {#render-an-interactive-pdf-form-using-the-java-api}

Rendern Sie ein interaktives PDF-Formular mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `FormsServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. URI-Werte angeben

   * Erstellen Sie eine `URLSpec` -Objekt, das URI-Werte mithilfe seines Konstruktors speichert.
   * Rufen Sie die `URLSpec` -Objekt `setApplicationWebRoot` -Methode verwenden und einen string -Wert übergeben, der den Webstamm der Anwendung darstellt.
   * Rufen Sie die `URLSpec` -Objekt `setContentRootURI` -Methode verwenden und einen string -Wert übergeben, der den Inhaltsstamm-URI-Wert angibt. Stellen Sie sicher, dass sich der Formularentwurf im Inhaltsstamm-URI befindet. Andernfalls gibt der Forms-Dienst eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository:///`.
   * Rufen Sie die `URLSpec` -Objekt `setTargetURL` -Methode verwenden und einen Zeichenfolgenwert übergeben, der den Ziel-URL-Wert angibt, an den die Formulardaten gesendet werden. Wenn Sie die Ziel-URL im Formularentwurf definieren, können Sie eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Anhängen von Dateien an das Formular

   * Erstellen Sie eine `java.util.HashMap` -Objekt zum Speichern von Dateianlagen mithilfe des -Konstruktors.
   * Rufen Sie die `java.util.HashMap` -Objekt `put` -Methode für jede Datei, die an das wiedergegebene Formular angehängt werden soll. Übergeben Sie die folgenden Werte an diese Methode:

      * Ein string -Wert, der den Namen des Dateianhangs angibt, einschließlich der Dateinamenerweiterung.
   * A `com.adobe.idp.Document` -Objekt, das die Dateianlage enthält.

   >[!NOTE]
   >
   >Wiederholen Sie diesen Schritt für jede Datei, die an das Formular angehängt werden soll. Dieser Schritt ist optional und Sie können `null`* , wenn Sie keine Dateianlagen senden möchten.*

1. Rendern eines interaktiven PDF-Formulars

   Rufen Sie die `FormsServiceClient` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie einen leeren `com.adobe.idp.Document` -Objekt.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Laufzeitoptionen festlegen möchten.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm` -Methode gibt eine `FormsResult` -Objekt, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Aufrufen der `FormsResult` object ‘s `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `com.adobe.idp.Document` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `com.adobe.idp.Document` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie eine `java.io.InputStream` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getInputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` -Objekt `read` -Methode verwenden und das Byte-Array als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

## Rendern eines interaktiven PDF-Formulars mit der Webdienst-API {#render-an-interactive-pdf-form-using-the-web-service-api}

Rendern Sie ein interaktives PDF-Formular mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie eine `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. URI-Werte angeben

   * Erstellen Sie eine `URLSpec` -Objekt, das URI-Werte mithilfe seines Konstruktors speichert.
   * Rufen Sie die `URLSpec` -Objekt `setApplicationWebRoot` -Methode verwenden und einen string -Wert übergeben, der den Webstamm der Anwendung darstellt.
   * Rufen Sie die `URLSpec` -Objekt `setContentRootURI` -Methode verwenden und einen string -Wert übergeben, der den Inhaltsstamm-URI-Wert angibt. Stellen Sie sicher, dass sich der Formularentwurf im Inhaltsstamm-URI befindet. Andernfalls gibt der Forms-Dienst eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository:///`.
   * Rufen Sie die `URLSpec` -Objekt `setTargetURL` -Methode verwenden und einen Zeichenfolgenwert übergeben, der den Ziel-URL-Wert angibt, an den die Formulardaten gesendet werden. Wenn Sie die Ziel-URL im Formularentwurf definieren, können Sie eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Anhängen von Dateien an das Formular

   * Erstellen Sie eine `java.util.HashMap` -Objekt zum Speichern von Dateianlagen mithilfe des -Konstruktors.
   * Rufen Sie die `java.util.HashMap` -Objekt `put` -Methode für jede Datei, die an das wiedergegebene Formular angehängt werden soll. Übergeben Sie die folgenden Werte an diese Methode:

      * Ein string -Wert, der den Namen des Dateianhangs angibt, einschließlich der Dateinamenerweiterung
   * A `BLOB` -Objekt, das den Dateianhang enthält

   >[!NOTE]
   >
   >Wiederholen Sie diesen Schritt für jede Datei, die an das Formular angehängt werden soll.

1. Rendern eines interaktiven PDF-Formulars

   Rufen Sie die `FormsService` -Objekt `renderPDFForm` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * A `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Laufzeitoptionen festlegen möchten.
   * A `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind.
   * A `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie `null` , wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode aufgefüllt wird. Damit wird das wiedergegebene PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode aufgefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm` -Methode füllt die `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das als letzter Argumentwert mit einem Formulardatenstream übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie eine `FormResult` -Objekt durch Abrufen des Werts der `com.adobe.idp.services.holders.FormsResultHolder` -Objekt `value` Datenelement.
   * Erstellen Sie eine `BLOB` -Objekt, das Formulardaten enthält, durch Aufrufen der `FormsResult` -Objekt `getOutputContent` -Methode.
   * Abrufen des Inhaltstyps der `BLOB` -Objekt durch Aufrufen seiner `getContentType` -Methode.
   * Legen Sie die `javax.servlet.http.HttpServletResponse` Inhaltstyp des Objekts durch Aufrufen seiner `setContentType` -Methode und Übergabe des Inhaltstyps der `BLOB` -Objekt.
   * Erstellen Sie eine `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Objekt `getOutputStream` -Methode.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `BLOB` -Objekt `getBinaryData` -Methode. Diese Aufgabe weist den Inhalt des `FormsResult` -Objekt zum Byte-Array hinzu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` -Objekt `write` -Methode zum Senden des Formulardaten-Streams an den Client-Webbrowser. Übergeben Sie das Byte-Array an die `write` -Methode.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.
