---
title: Verwendungsrechte zuweisen
seo-title: Assigning Usage Rights
description: Verwenden Sie die Java Client-API und die Web Service-API der Acrobat Reader DC Extensions, um Verwendungsrechte auf PDF-Dokumente anzuwenden und daraus zu entfernen.
seo-description: Use the Acrobat Reader DC extensions Java Client API and Web Service API to apply and remove usage rights from PDF documents.
uuid: 8c2020df-ea3c-49fa-916f-38a458f40d2b
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9e8db506-9ace-4e1f-8a7b-c4e9b15dde7e
role: Developer
exl-id: c7805d8a-eb6a-4908-9662-936920ffa67a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '3912'
ht-degree: 6%

---

# Verwendungsrechte zuweisen {#assigning-usage-rights}

## Informationen zum Acrobat Reader DC Extensions-Dienst {#about-the-acrobat-reader-dc-extensions-service}

Der Acrobat Reader DC Extensions-Dienst ermöglicht Ihrem Unternehmen das einfache Freigeben interaktiver PDF-Dokumente durch Erweiterung der Funktionalität von Adobe Reader. Der Acrobat Reader DC Extensions-Dienst unterstützt alle PDF-Dokumente bis einschließlich PDF 1.7 vollständig. Er funktioniert mit Adobe Reader 7.0 und höher. Der Dienst fügt einem PDF-Dokument Verwendungsrechte hinzu und aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument mit Adobe Reader geöffnet wird. Drittanbieterbenutzer benötigen keine zusätzliche Software oder Plug-ins, um mit den Dokumenten mit aktivierten Berechtigungen arbeiten zu können.

Sie können diese Aufgaben mithilfe des Acrobat Reader DC Extensions-Dienstes ausführen:

* Verwendungsrechte auf PDF-Dokumente anwenden Weitere Informationen finden Sie unter [Anwenden von Nutzungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).
* Entfernen Sie Verwendungsrechte aus PDF-Dokumenten. Weitere Informationen finden Sie unter [Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).
* Abrufen von Anmeldeinformationen. Weitere Informationen finden Sie unter [Abrufen von Anmeldeinformationen](assigning-usage-rights.md#retrieving-credential-information).

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Anwenden von Nutzungsrechten auf PDF-Dokumente {#applying-usage-rights-to-pdf-documents}

Mit der Java Client-API und dem Webdienst von Acrobat Reader DC Extensions können Sie Verwendungsrechte auf PDF-Dokumente anwenden. Verwendungsrechte gelten für Funktionen, die standardmäßig in Acrobat, nicht jedoch in Adobe Reader zur Verfügung stehen, wie etwa die Möglichkeit, Kommentare zu einem Formular hinzuzufügen oder Formularfelder auszufüllen und das Formular zu speichern. PDF-Dokumente, auf die Verwendungsrechte angewandt wurden, werden als Dokumente mit aktivierten Verwendungsrechten bezeichnet. Benutzer, die ein Dokument mit aktivierten Verwendungsrechten in Adobe Reader öffnen, können Vorgänge durchführen, die für dieses spezifische Dokument aktiviert sind.

>[!NOTE]
>
>Beim Anwenden von Verwendungsrechten auf PDF-Dokumente mithilfe des `applyUsageRights` -Methode, die Teil der Java-API ist, können Sie die `isModeFinal` Parameter der `ReaderExtensionsOptionSpec` Objekt zu `false`. Dadurch wird der Zähler für verarbeitete Formulare nicht aktualisiert und die Leistung verbessert. Wenn Sie sich nicht darum kümmern, den Zähler für verarbeitete Formulare zu aktualisieren, sollten Sie die Variable `isModeFinal` Parameter auf `false`.

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So wenden Sie Verwendungsrechte auf ein PDF-Dokument an:

1. Projektdateien einschließen.
1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.
1. Rufen Sie ein PDF-Dokument ab.
1. Geben Sie die anzuwendenden Verwendungsrechte an.
1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.
1. Speichern Sie das PDF-Dokument mit aktivierten Berechtigungen.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Acrobat Reader DC Extensions-Client-Objekts**

Um programmgesteuert einen Acrobat Reader DC Extensions-Dienstvorgang durchzuführen, müssen Sie ein Client-Objekt des Acrobat Reader DC Extensions-Dienstes erstellen. Wenn Sie die Java-API für Acrobat Reader DC Extensions verwenden, erstellen Sie eine `ReaderExtensionsServiceClient` -Objekt. Wenn Sie die Acrobat Reader DC Extensions-Webdienst-API verwenden, erstellen Sie eine `ReaderExtensionsServiceService` -Objekt.

**Abrufen eines PDF-Dokuments**

Sie müssen ein PDF-Dokument abrufen, um Verwendungsrechte anwenden zu können. Berechtigungsaktivierte PDF-Dokumente enthalten ein Wörterbuch zu Verwendungsrechten. Wenn Adobe Reader ein Dokument öffnet, das ein solches Wörterbuch enthält, werden nur die im Wörterbuch für dieses Dokument angegebenen Verwendungsrechte aktiviert. Wenn das Dokument kein Wörterbuch für Verwendungsrechte enthält, erstellt der Acrobat Reader DC Extensions-Dienst eines. Wenn er bereits ein Wörterbuch enthält, überschreibt der Acrobat Reader DC Extensions-Dienst vorhandene Verwendungsrechte mit den von Ihnen angegebenen. Das Wörterbuch gibt an, welche Verwendungsrechte aktiviert sind. Wenn ein Benutzer das Dokument in Adobe Reader öffnet, sind nur die im Wörterbuch angegebenen Verwendungsrechte zulässig.

**Verwendungsrechte festlegen**

Die Verwendungsrechte, die Sie festlegen können, werden durch eine von Adobe Systems Incorporated erworbene Berechtigung bestimmt. Berechtigungen bieten normalerweise die Berechtigung zum Festlegen einer Gruppe verwandter Verwendungsrechte, z. B. für interaktive Formulare. Jede Berechtigung bietet das Recht, eine bestimmte Anzahl von PDF-Dokumenten mit aktivierten Berechtigungen zu erstellen. Eine Testberechtigung gibt die Möglichkeit, eine unbegrenzte Anzahl von Entwürfen von Dokumenten zu erstellen.

>[!NOTE]
>
>Wenn Sie versuchen, ein Nutzungsrecht zuzuweisen, das von Ihrer Berechtigung nicht zulässig ist, verursachen Sie eine Ausnahme.

**Verwendungsrechte auf das PDF-Dokument anwenden**

Um Verwendungsrechte auf ein PDF-Dokument anzuwenden, verweisen Sie auf den Alias der Berechtigung, die Sie zum Anwenden von Verwendungsrechten verwenden (eine Berechtigung wird normalerweise während der Installation von AEM Forms installiert). Außerdem müssen Sie das PDF-Dokument angeben, auf das die Verwendungsrechte angewendet werden. Informationen zum Konfigurieren einer Berechtigung finden Sie im Handbuch zum Installieren und Bereitstellen für Ihren Anwendungsserver.

**Das PDF-Dokument mit aktivierten Berechtigungen speichern**

Nachdem der Acrobat Reader DC Extensions-Dienst Verwendungsrechte auf ein PDF-Dokument angewendet hat, können Sie das PDF-Dokument mit aktivierten Berechtigungen als PDF-Datei speichern.

**Siehe auch**

[Verwendungsrechte mithilfe der Java-API anwenden](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Nutzungsrechte mithilfe der Web-Service-API anwenden](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Acrobat Reader DC Extensions-Dienst-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Verwendungsrechte mithilfe der Java-API anwenden {#apply-usage-rights-using-the-java-api}

Wenden Sie mithilfe der Acrobat Reader DC Extensions-API (Java) Verwendungsrechte auf ein PDF-Dokument an:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-reader-extensions-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `ReaderExtensionsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Geben Sie die anzuwendenden Verwendungsrechte an.

   * Erstellen Sie eine `UsageRights` -Objekt, das mithilfe seines Konstruktors Verwendungsrechte darstellt.
   * Rufen Sie für jedes Verwendungsrecht eine entsprechende Methode auf, die zum `UsageRights` -Objekt. Fügen Sie beispielsweise die `enableFormFillIn` Nutzungsrecht, Aufrufen Sie die `UsageRights` -Objekt `enableFormFillIn` -Methode und -übergabe `true`. (Wiederholen Sie diesen Schritt für jedes Verwendungsrecht, das angewendet werden soll.)

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein Objekt `ReaderExtensionsOptionSpec`, indem Sie den Konstruktor verwenden. Dieses Objekt enthält Laufzeitoptionen, die für den Acrobat Reader DC Extensions-Dienst erforderlich sind. Beim Aufrufen dieses Konstruktors müssen Sie die folgenden Werte angeben:

      * Die `UsageRights` -Objekt, das die Verwendungsrechte enthält, die auf das Dokument angewendet werden sollen.
      * Ein string -Wert, der eine Meldung angibt, die einem Benutzer angezeigt wird, wenn das PDF-Dokument mit aktivierten Berechtigungen in Adobe Reader 7.x geöffnet wird. Diese Meldung wird in Adobe Reader 8.0 nicht angezeigt.
   * Wenden Sie Verwendungsrechte auf das PDF-Dokument an, indem Sie die `ReaderExtensionsServiceClient` -Objekt `applyUsageRights` -Methode verwenden und die folgenden Werte übergeben:

      * Die `com.adobe.idp.Document` -Objekt, das das PDF-Dokument enthält, auf das die Verwendungsrechte angewendet werden.
      * Ein string -Wert, der den Alias der Berechtigung angibt, mit dem Sie Verwendungsrechte anwenden können.
      * Ein string -Wert, der den entsprechenden Kennwortwert angibt. (Derzeit wird dieser Parameter ignoriert. Sie können `null`.
   * Die `ReaderExtensionsOptionSpec` -Objekt, das Laufzeitoptionen enthält.

   Die `applyUsageRights` -Methode gibt eine `com.adobe.idp.Document` -Objekt, das das PDF-Dokument mit aktivierten Berechtigungen enthält.

1. Speichern Sie das PDF-Dokument mit aktivierten Berechtigungen.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `com.adobe.idp.Document` -Objekt, das von der `applyUsageRights` -Methode).

**Siehe auch**

[Anwenden von Nutzungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Schnellstart (SOAP-Modus): Anwenden von Nutzungsrechten mithilfe der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Nutzungsrechte mithilfe der Web-Service-API anwenden {#apply-usage-rights-using-the-web-service-api}

Wenden Sie mithilfe der Acrobat Reader DC Extensions-API (Webdienst) Verwendungsrechte auf ein PDF-Dokument an:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   * Erstellen Sie eine `ReaderExtensionsServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `ReaderExtensionsServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Stellen Sie sicher, dass Sie `?blob=mtom`.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `ReaderExtensionsServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines PDF-Dokuments verwendet, auf das Verwendungsrechte angewendet werden.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Geben Sie die anzuwendenden Verwendungsrechte an.

   * Erstellen Sie eine `UsageRights` -Objekt, das mithilfe seines Konstruktors Verwendungsrechte darstellt.
   * Weisen Sie jedem Verwendungsrecht den Wert zu `true` dem entsprechenden Datenelement, das zu der `UsageRights` -Objekt. Fügen Sie beispielsweise die `enableFormFillIn` Verwendungsrecht zuweisen `true` der `UsageRights` -Objekt `enableFormFillIn` Datenelement. (Wiederholen Sie diesen Schritt für jedes Verwendungsrecht, das angewendet werden soll.)

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie ein Objekt `ReaderExtensionsOptionSpec`, indem Sie den Konstruktor verwenden. Dieses Objekt enthält Laufzeitoptionen, die für den Acrobat Reader DC Extensions-Dienst erforderlich sind.
   * Zuweisen der `UsageRights` -Objekt `ReaderExtensionsOptionSpec` -Objekt `usageRights` Datenelement.
   * Weisen Sie einen Zeichenfolgenwert zu, der die Meldung angibt, die ein Benutzer sieht, wenn das PDF-Dokument mit aktivierten Berechtigungen in Adobe Reader geöffnet wird, dem `ReaderExtensionsOptionSpec` -Objekt `message` Datenelement.
   * Wenden Sie Verwendungsrechte auf das PDF-Dokument an, indem Sie die `ReaderExtensionsServiceClient` -Objekt `applyUsageRights` -Methode verwenden und die folgenden Werte übergeben:

      * Die `BLOB` -Objekt, das das PDF-Dokument enthält, auf das die Verwendungsrechte angewendet werden.
      * Ein string -Wert, der den Alias der Berechtigung angibt, mit dem Sie Verwendungsrechte anwenden können.
      * Ein string -Wert, der den entsprechenden Kennwortwert angibt. (Derzeit wird dieser Parameter ignoriert. Sie können `null`.
   * Die `ReaderExtensionsOptionSpec` -Objekt, das Laufzeitoptionen enthält.

   Die `applyUsageRights` -Methode gibt eine `BLOB` -Objekt, das das PDF-Dokument mit aktivierten Berechtigungen enthält.

1. Speichern Sie das PDF-Dokument mit aktivierten Berechtigungen.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen seines Konstruktors. Übergeben Sie einen string -Wert, der den Dateispeicherort des PDF-Dokuments mit aktivierten Berechtigungen darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `applyUsageRights` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Anwenden von Nutzungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen von Verwendungsrechten aus PDF-Dokumenten {#removing-usage-rights-from-pdf-documents}

Sie können Verwendungsrechte aus einem Dokument mit aktivierten Benutzerrechten entfernen. Das Entfernen von Verwendungsrechten aus einem PDF-Dokument mit aktivierten Benutzerrechten ist auch erforderlich, um andere AEM Forms-Vorgänge darauf auszuführen. Sie müssen beispielsweise ein PDF-Dokument digital signieren (bzw. zertifizieren), bevor Sie Verwendungsrechte festlegen. Wenn Sie daher Vorgänge für ein Dokument mit aktivierten Benutzerrechten durchführen möchten, müssen Sie die Verwendungsrechte aus dem PDF-Dokument entfernen, die anderen Vorgänge ausführen, z. B. das Dokument digital signieren, und dann erneut Verwendungsrechte auf das Dokument anwenden.

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So entfernen Sie Verwendungsrechte aus einem PDF-Dokument mit aktivierten Benutzerrechten:

1. Projektdateien einschließen.
1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.
1. Rufen Sie ein PDF-Dokument mit aktivierten Benutzerrechten ab.
1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.
1. Speichern Sie das PDF-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Acrobat Reader DC Extensions-Client-Objekts**

Bevor Sie einen Acrobat Reader DC Extensions-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Acrobat Reader DC Extensions-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `ReaderExtensionsServiceClient` -Objekt. Wenn Sie die Acrobat Reader DC Extensions-Webdienst-API verwenden, erstellen Sie eine `ReaderExtensionsServiceService` -Objekt.

**Abrufen eines PDF-Dokuments mit aktivierten Berechtigungen**

Rufen Sie ein PDF-Dokument mit aktivierten Benutzerrechten ab, um Verwendungsrechte zu entfernen.

**Entfernen von Verwendungsrechten aus dem PDF-Dokument**

Nachdem Sie ein PDF-Dokument mit aktivierten Benutzerrechten abgerufen haben, können Sie Verwendungsrechte entfernen. Nachdem Sie Verwendungsrechte entfernt haben, verfügt das PDF-Dokument über keine zusätzlichen Funktionen, während es in Adobe Reader angezeigt wird.

**PDF-Dokument speichern**

Sie können das PDF-Dokument, das keine Verwendungsrechte mehr enthält, als PDF-Datei speichern. Nach dem Speichern als PDF-Datei kann das PDF-Dokument in Adobe Reader oder Acrobat angezeigt werden.

**Siehe auch**

[Nutzungsrechte mit der Java-API entfernen](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Entfernen von Nutzungsrechten mithilfe der Webdienst-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Acrobat Reader DC Extensions-Dienst-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Anwenden von Nutzungsrechten auf PDF-Dokumente](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Nutzungsrechte mit der Java-API entfernen {#remove-usage-rights-using-the-java-api}

Entfernen Sie mithilfe der Acrobat Reader DC Extensions-API (Java) Verwendungsrechte aus einem PDF-Dokument mit aktivierten Rechten:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-reader-extensions-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   Erstellen Sie eine `ReaderExtensionsServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das PDF-Dokument mit aktivierten Rechten darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   Entfernen Sie Verwendungsrechte aus dem PDF-Dokument, indem Sie die `ReaderExtensionsServiceClient` -Objekt `removeUsageRights` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein PDF-Dokument ohne Verwendungsrechte enthält.

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateierweiterung .PDF lautet.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `removeUsageRights` -Methode).

**Siehe auch**

[Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Schnellstart (SOAP-Modus): Entfernen von Verwendungsrechten aus einem PDF-Dokument mithilfe der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entfernen von Nutzungsrechten mithilfe der Webdienst-API {#remove-usage-rights-using-the-web-service-api}

Entfernen Sie mithilfe der Acrobat Reader DC Extensions-API (Webdienst) Verwendungsrechte aus einem PDF-Dokument mit aktivierten Berechtigungen:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   * Erstellen Sie eine `ReaderExtensionsServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `ReaderExtensionsServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Stellen Sie sicher, dass Sie `?blob=mtom`.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `ReaderExtensionsServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des PDF-Dokuments mit aktivierten Benutzerrechten verwendet, aus dem Verwendungsrechte entfernt werden.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   Entfernen Sie Verwendungsrechte aus dem PDF-Dokument, indem Sie die `ReaderExtensionsServiceClient` -Objekt `removeUsageRights` -Methode und Übergabe der `BLOB` -Objekt, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt eine `BLOB` -Objekt, das ein PDF-Dokument ohne Verwendungsrechte enthält.

1. Wenden Sie Verwendungsrechte auf das PDF-Dokument an.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Speicherort der PDF-Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `removeUsageRights` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.

**Siehe auch**

[Entfernen von Verwendungsrechten aus PDF-Dokumenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Abrufen von Anmeldeinformationen {#retrieving-credential-information}

Sie können Informationen zu den Anmeldedaten abrufen, die zum Anwenden von Verwendungsrechten auf ein PDF-Dokument mit aktivierten Benutzerrechten verwendet wurden. Durch Abrufen von Informationen zu einer Berechtigung können Sie Informationen wie das Datum abrufen, nach dem das Zertifikat nicht mehr gültig ist.

>[!NOTE]
>
>Weitere Informationen zum Acrobat Reader DC Extensions-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um Informationen zu den Anmeldedaten abzurufen, die zum Anwenden von Verwendungsrechten auf ein PDF-Dokument verwendet wurden, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.
1. Rufen Sie ein PDF-Dokument mit aktivierten Benutzerrechten ab.
1. Rufen Sie Informationen über die Berechtigung ab.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Acrobat Reader DC Extensions-Client-Objekts**

Bevor Sie einen Acrobat Reader DC Extensions-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Acrobat Reader DC Extensions-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie eine `ReaderExtensionsServiceClient` -Objekt. Wenn Sie die Acrobat Reader DC Extensions-Webdienst-API verwenden, erstellen Sie eine `ReaderExtensionsServiceService` -Objekt.

**Abrufen eines PDF-Dokuments mit aktivierten Berechtigungen**

Sie müssen ein PDF-Dokument mit aktivierten Benutzerrechten abrufen, um Informationen über die Berechtigung abrufen zu können. Sie können auch Informationen zu einer Berechtigung abrufen, indem Sie ihren Alias angeben. Wenn Sie jedoch Informationen zu einer Berechtigung abrufen möchten, die zum Anwenden von Verwendungsrechten auf ein bestimmtes PDF-Dokument mit aktivierten Rechten verwendet wurde, müssen Sie das Dokument abrufen.

**Informationen zur Berechtigung abrufen**

Nachdem Sie ein PDF-Dokument mit aktivierten Benutzerrechten abgerufen haben, können Sie Informationen zu den Anmeldedaten abrufen, mit denen Verwendungsrechte angewendet wurden. Sie können die folgenden Informationen über die Berechtigung abrufen:

* Die Meldung, die in Adobe Reader angezeigt wird, wenn das PDF-Dokument mit aktivierten Berechtigungen geöffnet wird.
* Das Datum, nach dem die Berechtigung nicht mehr gültig ist.
* Das Datum, vor dem die Berechtigung nicht gültig ist.
* Die Verwendungsrechte, die für dieses PDF-Dokument mit aktivierten Benutzerrechten festgelegt wurden.
* Die Häufigkeit, mit der die Berechtigung verwendet wurde.

**Siehe auch**

[Nutzungsrechte mit der Java-API entfernen](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Entfernen von Nutzungsrechten mithilfe der Webdienst-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Acrobat Reader DC Extensions-Dienst-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Abrufen von Anmeldeinformationen mithilfe der Java-API {#retrieve-credential-information-using-the-java-api}

Abrufen von Anmeldeinformationen mithilfe der Acrobat Reader DC Extensions-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-reader-extensions-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   Erstellen Sie eine `ReaderExtensionsServiceClient` -Objekt mithilfe des -Konstruktors und Übergeben eines `ServiceClientFactory` -Objekt, das Verbindungseigenschaften enthält.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das PDF-Dokument mit aktivierten Rechten darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments mit aktivierten Rechten angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   * Rufen Sie Informationen zu den Berechtigungen ab, die zum Anwenden von Verwendungsrechten auf das PDF-Dokument verwendet werden, indem Sie die `ReaderExtensionsServiceClient` -Objekt `getDocumentUsageRights` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt eine `GetUsageRightsResult` -Objekt, das Anmeldeinformationen enthält.
   * Rufen Sie das Datum ab, nach dem die Berechtigung nicht mehr gültig ist, indem Sie die `GetUsageRightsResult` -Objekt `getNotAfter` -Methode. Diese Methode gibt eine `java.util.Date` -Objekt, das das Datum darstellt, nach dem die Berechtigung nicht mehr gültig ist.
   * Rufen Sie die Meldung ab, die in Adobe Reader angezeigt wird, wenn das PDF-Dokument mit aktivierten Berechtigungen geöffnet wird, indem Sie die `GetUsageRightsResult` -Objekt `getMessage` -Methode. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Nachricht darstellt.

**Siehe auch**

[Abrufen von Anmeldeinformationen](assigning-usage-rights.md#retrieving-credential-information)

[Schnellstart (SOAP-Modus): Abrufen von Anmeldeinformationen mithilfe der Java-API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von Anmeldeinformationen mithilfe der Webdienst-API {#retrieve-credential-information-using-the-web-service-api}

Abrufen von Anmeldeinformationen mithilfe der Acrobat Reader DC Extensions-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Client-Objekt für Acrobat Reader DC Extensions.

   * Erstellen Sie eine `ReaderExtensionsServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `ReaderExtensionsServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Stellen Sie sicher, dass Sie `?blob=mtom`.
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `ReaderExtensionsServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines PDF-Dokuments mit aktivierten Rechten verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des PDF-Dokuments mit aktivierten Berechtigungen und den Ausführungsmodus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Entfernen Sie Verwendungsrechte aus dem PDF-Dokument.

   * Rufen Sie Informationen zu den Berechtigungen ab, die zum Anwenden von Verwendungsrechten auf das PDF-Dokument verwendet werden, indem Sie die `ReaderExtensionsServiceClient` -Objekt `getDocumentUsageRights` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das PDF-Dokument mit aktivierten Berechtigungen enthält. Diese Methode gibt eine `GetUsageRightsResult` -Objekt, das Anmeldeinformationen enthält.
   * Rufen Sie das Datum ab, nach dem die Berechtigung nicht mehr gültig ist, indem Sie den Wert der `GetUsageRightsResult` -Objekt `notAfter` Datenelement. Der Datentyp dieses Datenelements lautet `System.DateTime`.
   * Rufen Sie die Meldung ab, die angezeigt wird, wenn das PDF-Dokument mit aktivierten Berechtigungen in Adobe Reader geöffnet wird, indem Sie den Wert der `GetUsageRightsResult` -Objekt `message` Datenelement. Der Datentyp dieses Datenelements ist eine Zeichenfolge.
   * Rufen Sie die Anzahl der verwendeten Anmeldedaten ab, indem Sie den Wert der `GetUsageRightsResult` -Objekt `useCount` Datenelement. Der Datentyp dieses Datenelements ist eine Ganzzahl.

**Siehe auch**

[Abrufen von Anmeldeinformationen](assigning-usage-rights.md#retrieving-credential-information)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
