---
title: Überprüfen eines DDX-Dokuments mithilfe der Webdienst-API
seo-title: Validate a DDX document using theweb service API
description: Verwenden Sie die Assembler-Dienst-API zum Überprüfen eines DDX-Dokuments.
seo-description: Use the Assembler Service API to validate a DDX document.
uuid: f6125746-6138-4e46-a1c4-fb24fd7399c5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a6fe91ab-3aa0-4b3d-87c0-6cf69a2c4cc4
role: Developer
exl-id: da303186-8f36-4fc8-a2db-b38a0b200c39
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 2%

---

# Validieren eines DDX-Dokuments mithilfe der Webdienst-API {#validate-a-ddx-document-using-theweb-service-api}

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

[Validieren von DDX-Dokumenten](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
