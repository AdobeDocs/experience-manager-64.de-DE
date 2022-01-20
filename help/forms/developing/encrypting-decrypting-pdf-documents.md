---
title: Verschlüsseln und Entschlüsseln von PDF-Dokumenten
seo-title: Encrypting and Decrypting PDF Documents
description: Verwenden Sie den Encryption-Dienst zum Verschlüsseln und Entschlüsseln von Dokumenten. Zu den Aufgaben des Encryption-Dienstes gehören das Verschlüsseln eines PDF-Dokuments mit einem Kennwort, das Verschlüsseln eines PDF-Dokuments mit einem Zertifikat, das Entfernen der kennwortbasierten Verschlüsselung von einem PDF-Dokument, das Entfernen der zertifikatbasierten Verschlüsselung von einem PDF-Dokument, das Entsperren des PDF-Dokuments, sodass andere Dienstvorgänge ausgeführt werden können, und das Ermitteln des Verschlüsselungstyps eines gesicherten PDF-Dokuments.
seo-description: Use the Encryption service to encrypt and decrypt documents. The Encryption service tasks include encrypting a PDF document with a password, encrypting a PDF document with a certificate, removing password-based encryption from a PDF document, removing certificate-based encryption from a PDF document, unlocking the PDF document so that other service operations can be performed, and determining the encryption type of a secured PDF document.
uuid: 4e4e2716-c21f-4bfe-ae7a-7e91442414ef
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 5e4bda3a-5648-4c0f-b2f8-bdbebb88f537
role: Developer
exl-id: 670d9680-6125-4a48-82ef-78f1630d780f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '8175'
ht-degree: 8%

---

# Verschlüsseln und Entschlüsseln von PDF-Dokumenten {#encrypting-and-decrypting-pdf-documents}

**Über den Encryption-Dienst**

Mit dem Encryption-Dienst können Sie Dokumente verschlüsseln und entschlüsseln. Wird ein Dokument verschlüsselt, ist sein Inhalt nicht mehr lesbar. Ein autorisierter Benutzer kann das Dokument entschlüsseln, um Zugriff auf den Inhalt zu erhalten. Wenn ein PDF-Dokument mit einem Kennwort verschlüsselt wird, muss der Benutzer das Kennwort zum Öffnen angeben, damit das Dokument in Adobe Reader oder Adobe angezeigt werden kann. Ähnlich muss der Benutzer, wenn ein PDF-Dokument mit einem Zertifikat verschlüsselt ist, das PDF-Dokument mithilfe des öffentlichen Schlüssels entschlüsseln, der dem Zertifikat (privater Schlüssel) entspricht, das zum Verschlüsseln des PDF-Dokuments verwendet wurde.

Sie können diese Aufgaben mithilfe des Encryption-Dienstes ausführen:

* Verschlüsseln Sie ein PDF-Dokument mit einem Kennwort. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).
* Verschlüsseln Sie ein PDF-Dokument mit einem Zertifikat. (Siehe [Verschlüsseln von PDF-Dokumenten mit Zertifikaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).
* Entfernen Sie die kennwortbasierte Verschlüsselung von einem PDF-Dokument. (Siehe [Entfernen der Kennwortverschlüsselung](encrypting-decrypting-pdf-documents.md#removing-password-encryption).
* Entfernen Sie die zertifikatbasierte Verschlüsselung von einem PDF-Dokument. (Siehe [Zertifikatbasierte Verschlüsselung entfernen](encrypting-decrypting-pdf-documents.md#removing-certificate-based-encryption).
* Entsperren Sie das PDF-Dokument, damit andere Dienstvorgänge ausgeführt werden können. Nachdem beispielsweise ein kennwortverschlüsseltes PDF-Dokument entsperrt wurde, können Sie eine digitale Signatur darauf anwenden. (Siehe [Entsperren verschlüsselter PDF-Dokumente](encrypting-decrypting-pdf-documents.md#unlocking-encrypted-pdf-documents).
* Bestimmen Sie den Verschlüsselungstyp eines gesicherten PDF-Dokuments. (Siehe [Bestimmen des Verschlüsselungstyps](encrypting-decrypting-pdf-documents.md#determining-encryption-type).

   >[!NOTE]
   >
   >Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Verschlüsseln von PDF-Dokumenten mit einem Kennwort {#encrypting-pdf-documents-with-a-password}

Nachdem ein PDF-Dokument mit einem Kennwort verschlüsselt wurde, muss ein Benutzer das Kennwort angeben, damit das Dokument in Adobe Reader oder Acrobat geöffnet werden kann. Außerdem muss ein kennwortverschlüsseltes PDF-Dokument entsperrt werden, bevor ein anderer AEM Forms-Vorgang wie das digitale Signieren des PDF-Dokuments für das Dokument ausgeführt werden kann.

>[!NOTE]
>
>Wenn Sie ein verschlüsseltes PDF-Dokument in das AEM Forms-Repository hochladen, kann es das PDF-Dokument nicht entschlüsseln und den XDP-Inhalt extrahieren. Es wird empfohlen, ein Dokument nicht vor dem Hochladen in das AEM Forms-Repository zu verschlüsseln. (Siehe [Schreiben von Ressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein PDF-Dokument mit einem Kennwort zu verschlüsseln, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Encryption Client-API-Objekt.
1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.
1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.
1. Fügen Sie das Kennwort hinzu.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Client-API-Objekts**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen.

**PDF-Dokument zum Verschlüsseln abrufen**

Sie müssen ein unverschlüsseltes PDF-Dokument abrufen, um das Dokument mit einem Kennwort zu verschlüsseln. Wenn Sie versuchen, ein bereits verschlüsseltes PDF-Dokument zu schützen, wird eine Ausnahme verursacht.

**Laufzeitoptionen für Verschlüsselung festlegen**

Um ein PDF-Dokument mit einem Kennwort zu verschlüsseln, geben Sie vier Werte an, darunter zwei Kennwortwerte. Der erste Kennwortwert wird zum Verschlüsseln des PDF-Dokuments verwendet und muss beim Öffnen des PDF-Dokuments angegeben werden. Der zweite Kennwortwert mit dem Namen &quot;Übergeordneter Kennwortwert&quot;wird zum Entfernen der Verschlüsselung vom PDF-Dokument verwendet. Bei Kennwortwerten wird zwischen Groß- und Kleinschreibung unterschieden. Diese beiden Kennwortwerte dürfen nicht dieselben Werte sein.

Sie müssen die zu verschlüsselnden PDF-Dokumentressourcen angeben. Sie können das gesamte PDF-Dokument verschlüsseln, alles außer den Metadaten des Dokuments oder nur die Anlagen des Dokuments. Wenn Sie nur die Anlagen des Dokuments verschlüsseln, wird ein Benutzer beim Versuch, auf die Dateianlagen zuzugreifen, nach einem Kennwort aufgefordert.

Beim Verschlüsseln eines PDF-Dokuments können Sie Berechtigungen angeben, die mit dem gesicherten Dokument verknüpft sind. Durch Festlegen von Berechtigungen können Sie steuern, welche Aktionen ein Benutzer ausführen darf, der ein kennwortverschlüsseltes PDF-Dokument öffnet. Zum erfolgreichen Extrahieren von Formulardaten müssen Sie beispielsweise die folgenden Berechtigungen festlegen:

* PASSWORD_EDIT_ADD
* PASSWORD_EDIT_MODIFY

>[!NOTE]
>
>Berechtigungen werden als `PasswordEncryptionPermission` Auflistungswerte.

**Passwort hinzufügen**

Nachdem Sie ein ungesichertes PDF-Dokument abgerufen und die Verschlüsselungs-Laufzeitwerte festgelegt haben, können Sie dem PDF-Dokument ein Kennwort hinzufügen.

**Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei**

Sie können das kennwortverschlüsselte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Verschlüsseln eines PDF-Dokuments mit der Java-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-using-the-java-api)

[Verschlüsseln eines PDF-Dokuments mit der Webdienst-API](encrypting-decrypting-pdf-documents.md#encrypting-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit Zertifikaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates)

### Verschlüsseln eines PDF-Dokuments mit der Java-API {#encrypt-a-pdf-document-using-the-java-api}

Verschlüsseln Sie ein PDF-Dokument mit einem Kennwort mithilfe der Verschlüsselungs-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie eine Verschlüsselungs-Client-API.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `EncryptionServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das zu verschlüsselende PDF-Dokument mithilfe des Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie eine `PasswordEncryptionOptionSpec` -Objekt durch Aufrufen seines Konstruktors.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie die `PasswordEncryptionOptionSpec` -Objekt `setEncryptOption` -Methode und Übergeben einer `PasswordEncryptionOption` enumeration -Wert, der die zu verschlüsselnden Dokumentressourcen angibt. Um beispielsweise das gesamte PDF-Dokument einschließlich der Metadaten und Anlagen zu verschlüsseln, geben Sie `PasswordEncryptionOption.ALL`.
   * Erstellen Sie eine `java.util.List` -Objekt, das die Verschlüsselungsberechtigungen mithilfe des `ArrayList` -Konstruktor.
   * Festlegen einer Berechtigung durch Aufrufen der `java.util.List` object ‘s `add` -Methode verwenden und einen Auflistungswert übergeben, der der festzulegenden Berechtigung entspricht. Um beispielsweise die Berechtigung festzulegen, mit der ein Benutzer Daten im PDF-Dokument kopieren kann, geben Sie `PasswordEncryptionPermission.PASSWORD_EDIT_COPY`. (Wiederholen Sie diesen Schritt für jede festzulegende Berechtigung.)
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie die `PasswordEncryptionOptionSpec` -Objekt `setCompatability` -Methode und Übergabe eines Auflistungswerts, der die Acrobat-Kompatibilitätsstufe angibt. Sie können beispielsweise `PasswordEncryptionCompatability.ACRO_7`.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer das verschlüsselte PDF-Dokument durch Aufrufen der `PasswordEncryptionOptionSpec` -Objekt `setDocumentOpenPassword` -Methode verwenden und einen string -Wert übergeben, der das offene Kennwort darstellt.
   * Geben Sie den Übergeordneten Kennwortwert an, mit dem ein Benutzer die Verschlüsselung aus dem PDF-Dokument entfernen kann, indem er die `PasswordEncryptionOptionSpec` -Objekt `setPermissionPassword` -Methode verwenden und einen string -Wert übergeben, der das Übergeordnete Kennwort darstellt.

1. Fügen Sie das Kennwort hinzu.

   Verschlüsseln Sie das PDF-Dokument, indem Sie die `EncryptionServiceClient` -Objekt `encryptPDFUsingPassword` -Methode verwenden und die folgenden Werte übergeben:

   * Die `com.adobe.idp.Document` -Objekt, das das PDF-Dokument enthält, das mit dem Kennwort verschlüsselt werden soll.
   * Die `PasswordEncryptionOptionSpec` -Objekt, das Verschlüsselungslaufzeitoptionen enthält.

   Die `encryptPDFUsingPassword` -Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt in die Datei ein. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `encryptPDFUsingPassword`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mit der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verschlüsseln eines PDF-Dokuments mit der Webdienst-API {#encrypting-a-pdf-document-using-the-web-service-api}

Verschlüsseln Sie ein PDF-Dokument mit einem Kennwort mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Encryption Client-API-Objekt.

   * Erstellen Sie eine `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `EncryptionServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `EncryptionServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird verwendet, um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu speichern.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` -Objekt, indem der Inhalt des Byte-Arrays dem `BLOB` -Objekt `MTOM` Datenelement.

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein Objekt `PasswordEncryptionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie eine `PasswordEncryptionOption` Auflistungswert zum `PasswordEncryptionOptionSpec` -Objekt `encryptOption` Datenelement. Um die gesamte PDF zu verschlüsseln, einschließlich Metadaten und Anlagen, weisen Sie `PasswordEncryptionOption.ALL` zu diesem Datenelement hinzu.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie eine `PasswordEncryptionCompatability` Auflistungswert zum `PasswordEncryptionOptionSpec` -Objekt `compatability` Datenelement. Weisen Sie beispielsweise `PasswordEncryptionCompatability.ACRO_7` zu diesem Datenelement hinzu.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer das verschlüsselte PDF-Dokument öffnen kann, indem Sie dem `PasswordEncryptionOptionSpec` -Objekt `documentOpenPassword` Datenelement.
   * Geben Sie den Kennwortwert an, mit dem ein Benutzer die Verschlüsselung aus dem PDF-Dokument entfernen kann, indem Sie dem `PasswordEncryptionOptionSpec` -Objekt `permissionPassword` Datenelement.

1. Fügen Sie das Kennwort hinzu.

   Verschlüsseln Sie das PDF-Dokument, indem Sie die `EncryptionServiceClient` -Objekt `encryptPDFUsingPassword` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das das PDF-Dokument enthält, das mit dem Kennwort verschlüsselt werden soll.
   * Die `PasswordEncryptionOptionSpec` -Objekt, das Verschlüsselungslaufzeitoptionen enthält.

   Die `encryptPDFUsingPassword` -Methode gibt eine `BLOB` -Objekt, das ein kennwortverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `encryptPDFUsingPassword` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Verschlüsseln von PDF-Dokumenten mit Zertifikaten {#encrypting-pdf-documents-with-certificates}

Zertifikatbasierte Verschlüsselung ermöglicht die Verschlüsselung eines Dokuments für bestimmte Empfänger mithilfe von Technologien mit öffentlichem Schlüssel. Verschiedene Empfänger können unterschiedliche Berechtigungen für das Dokument erhalten. Viele Aspekte der Verschlüsselung werden durch die Technologie öffentlicher Schlüssel möglich gemacht. Ein Algorithmus wird verwendet, um zwei große Zahlen zu generieren, die als *keys*, die die folgenden Eigenschaften aufweisen:

* Ein Schlüssel wird zum Verschlüsseln eines Satzes von Daten verwendet. Danach kann nur der andere Schlüssel zum Entschlüsseln der Daten verwendet werden.
* Es ist unmöglich, einen Schlüssel vom anderen zu unterscheiden.

Einer der Schlüssel dient als privater Schlüssel des Benutzers. Wichtig ist, dass nur der Benutzer Zugriff auf diesen Schlüssel hat. Der andere Schlüssel ist der öffentliche Schlüssel des Benutzers, der für andere freigegeben werden kann.

Ein Zertifikat mit öffentlichem Schlüssel enthält den öffentlichen Schlüssel eines Benutzers und Identifizierungsinformationen. Das X.509-Format dient zum Speichern von Zertifikaten. Zertifikate werden meist von einer Zertifizierungsstelle ausgestellt und digital signiert, bei der es sich um eine anerkannte Instanz handelt, die ein Maß an Vertrauen in die Gültigkeit des Zertifikats ermöglicht. Zertifikate haben ein Ablaufdatum, nach dem sie nicht mehr gültig sind. Darüber hinaus liefern Zertifikatsperrlisten Informationen zu Zertifikaten, die vor ihrem Ablaufdatum gesperrt wurden. Zertifikatsperrlisten werden regelmäßig von Zertifizierungsstellen veröffentlicht. Der Sperrstatus eines Zertifikats kann auch mittels des Online-Zertifikatstatusprotokolls (Online Certificate Status Protocol, OCSP) über das Netzwerk abgerufen werden.

>[!NOTE]
>
>Wenn Sie ein verschlüsseltes PDF-Dokument in das AEM Forms-Repository hochladen, kann es das PDF-Dokument nicht entschlüsseln und den XDP-Inhalt extrahieren. Es wird empfohlen, ein Dokument nicht vor dem Hochladen in das AEM Forms-Repository zu verschlüsseln. (Siehe [Schreiben von Ressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument mit einem Zertifikat verschlüsseln können, müssen Sie sicherstellen, dass Sie das Zertifikat zu AEM Forms hinzufügen. Ein Zertifikat wird über Administration Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Importieren von Anmeldeinformationen mithilfe der Trust Manager-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um ein PDF-Dokument mit einem Zertifikat zu verschlüsseln, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Encryption Client-API-Objekt.
1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.
1. Referenzieren Sie das Zertifikat.
1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.
1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.
1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Client-API-Objekts**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service-API verwenden, erstellen Sie eine `EncrytionServiceClient` -Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie eine `EncryptionServiceService` -Objekt.

**PDF-Dokument zum Verschlüsseln abrufen**

Sie müssen zum Verschlüsseln ein unverschlüsseltes PDF-Dokument abrufen. Wenn Sie versuchen, ein bereits verschlüsseltes PDF-Dokument zu sichern, wird eine Ausnahme ausgelöst.

**Referenzieren des Zertifikats**

Um ein PDF-Dokument mit einem Zertifikat zu verschlüsseln, verweisen Sie auf ein Zertifikat, das zum Verschlüsseln eines PDF-Dokuments verwendet wird. Das Zertifikat ist eine .cer-Datei, eine .crt-Datei oder eine .pem-Datei. Eine PKCS#12-Datei wird verwendet, um private Schlüssel mit entsprechenden Zertifikaten zu speichern.

Geben Sie beim Verschlüsseln eines PDF-Dokuments mit einem Zertifikat die Berechtigungen an, die mit dem gesicherten Dokument verknüpft sind. Durch Festlegen von Berechtigungen können Sie steuern, welche Aktionen ein Benutzer ausführen kann, der ein zertifikatverschlüsseltes PDF-Dokument öffnet.

**Laufzeitoptionen für Verschlüsselung festlegen**

Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an. Sie können das gesamte PDF-Dokument verschlüsseln, alles außer den Metadaten des Dokuments oder nur die Anlagen des Dokuments.

**Zertifikatverschlüsseltes PDF-Dokument erstellen**

Nachdem Sie ein ungesichertes PDF-Dokument abgerufen, auf das Zertifikat verwiesen und Laufzeitoptionen festgelegt haben, können Sie ein zertifikatverschlüsseltes PDF-Dokument erstellen. Nachdem das PDF-Dokument verschlüsselt wurde, benötigen Sie den entsprechenden öffentlichen Schlüssel zum Entschlüsseln.

**Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei**

Sie können das verschlüsselte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-java-api)

[Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Webdienst-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API {#encrypt-a-pdf-document-with-a-certificate-using-the-java-api}

Verschlüsseln Sie ein PDF-Dokument mit einem Zertifikat mithilfe der Verschlüsselungs-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Encryption Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `EncryptionServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das zu verschlüsselende PDF-Dokument mithilfe des Konstruktors darstellt und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Referenzieren Sie das Zertifikat.

   * Erstellen Sie eine `java.util.List` -Objekt, das Berechtigungsinformationen mithilfe des zugehörigen Konstruktors speichert.
   * Geben Sie die mit dem verschlüsselten Dokument verknüpfte Berechtigung an, indem Sie die `java.util.List` -Objekt `add` -Methode und Übergeben einer `CertificateEncryptionPermissions` enumeration -Wert, der die Berechtigungen darstellt, die dem Benutzer gewährt werden, der das gesicherte PDF-Dokument öffnet. Um beispielsweise alle Berechtigungen anzugeben, übergeben Sie `CertificateEncryptionPermissions.PKI_ALL_PERM`.
   * Erstellen Sie ein Objekt `Recipient`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das Zertifikat darstellt, das zum Verschlüsseln des PDF-Dokuments verwendet wird, indem der zugehörige Konstruktor verwendet und ein string -Wert übergeben wird, der den Speicherort des Zertifikats angibt.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt durch Verwendung seines Konstruktors und Übergabe des `java.io.FileInputStream` -Objekt, das das Zertifikat darstellt.
   * Rufen Sie die `Recipient` -Objekt `setX509Cert` -Methode und übergeben Sie die `com.adobe.idp.Document` -Objekt, das das Zertifikat enthält. (Darüber hinaus wird die `Recipient`-Objekt kann einen Truststore-Zertifikatalias oder eine LDAP-URL als Zertifikatquelle haben.)
   * Erstellen Sie eine `CertificateEncryptionIdentity` -Objekt, das Berechtigungen und Zertifikatinformationen mithilfe des zugehörigen Konstruktors speichert.
   * Rufen Sie die `CertificateEncryptionIdentity` -Objekt `setPerms` -Methode und übergeben Sie die `java.util.List` -Objekt, das Berechtigungsinformationen speichert.
   * Rufen Sie die `CertificateEncryptionIdentity` -Objekt `setRecipient` -Methode und übergeben Sie die `Recipient` -Objekt, das Zertifikatinformationen speichert.
   * Erstellen Sie eine `java.util.List` -Objekt, das Zertifikatinformationen mithilfe seines Konstruktors speichert.
   * Rufen Sie die `java.util.List` -Methode zum Hinzufügen des -Objekts verwenden und die `CertificateEncryptionIdentity` -Objekt. (Diese `java.util.List` -Objekt wird als Parameter an die `encryptPDFUsingCertificates` -Methode.)

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie eine `CertificateEncryptionOptionSpec` -Objekt durch Aufrufen seines Konstruktors.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie die `CertificateEncryptionOptionSpec` -Objekt `setOption` -Methode und Übergeben einer `CertificateEncryptionOption` enumeration -Wert, der die zu verschlüsselnden Dokumentressourcen angibt. Um beispielsweise das gesamte PDF-Dokument einschließlich der Metadaten und Anlagen zu verschlüsseln, geben Sie `CertificateEncryptionOption.ALL`.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie die `CertificateEncryptionOptionSpec` -Objekt `setCompat` -Methode und Übergeben einer `CertificateEncryptionCompatibility` Auflistungswert, der die Acrobat-Kompatibilitätsstufe angibt. Sie können beispielsweise `CertificateEncryptionCompatibility.ACRO_7`.

1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.

   Verschlüsseln Sie das PDF-Dokument mit einem Zertifikat, indem Sie die `EncryptionServiceClient` -Objekt `encryptPDFUsingCertificates` -Methode verwenden und die folgenden Werte übergeben:

   * Die `com.adobe.idp.Document` -Objekt, das das zu verschlüsselende PDF-Dokument enthält.
   * Die `java.util.List` -Objekt, das Zertifikatinformationen speichert.
   * Die `CertificateEncryptionOptionSpec` -Objekt, das Verschlüsselungslaufzeitoptionen enthält.

   Die `encryptPDFUsingCertificates` -Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein zertifikatverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt in die Datei ein. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `encryptPDFUsingCertificates`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verschlüsseln eines PDF-Dokuments mit einem Zertifikat mithilfe der Webdienst-API {#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api}

Verschlüsseln Sie ein PDF-Dokument mit einem Zertifikat mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Encryption Client-API-Objekt.

   * Erstellen Sie eine `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `EncryptionServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `EncryptionServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie ein PDF-Dokument zum Verschlüsseln ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines mit einem PDF-Zertifikat verschlüsselten Dokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu verschlüsselnden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` Objekt durch Zuweisen seiner `MTOM` -Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Referenzieren Sie das Zertifikat.

   * Erstellen Sie ein Objekt `Recipient`, indem Sie den Konstruktor verwenden. Dieses Objekt speichert Zertifikatinformationen.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Diese `BLOB` -Objekt speichert das Zertifikat, das das PDF-Dokument verschlüsselt.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des Zertifikats und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` -Objekt, indem der Inhalt des Byte-Arrays dem `BLOB` -Objekt `MTOM` Datenelement.
   * Zuweisen der `BLOB` -Objekt, das das Zertifikat im `Recipient` -Objekt `x509Cert` Datenelement.
   * Erstellen Sie eine `CertificateEncryptionIdentity` -Objekt, das Zertifikatinformationen mithilfe seines Konstruktors speichert.
   * Zuweisen der `Recipient` -Objekt, das das Zertifikat im `CertificateEncryptionIdentity`-Datenelement des -Objekts.
   * Erstellen Sie eine `Object` -Array und weisen Sie die `CertificateEncryptionIdentity` -Objekt zum ersten Element des `Object` Array. Diese `Object` Array wird als Parameter an die `encryptPDFUsingCertificates` -Methode.

1. Legen Sie die Laufzeitoptionen der Verschlüsselung fest.

   * Erstellen Sie ein Objekt `CertificateEncryptionOptionSpec`, indem Sie den Konstruktor verwenden.
   * Geben Sie die zu verschlüsselnden PDF-Dokumentressourcen an, indem Sie eine `CertificateEncryptionOption` Auflistungswert zum `CertificateEncryptionOptionSpec` -Objekt `option` Datenelement. Um das gesamte PDF-Dokument einschließlich der Metadaten und Anlagen zu verschlüsseln, weisen Sie `CertificateEncryptionOption.ALL` zu diesem Datenelement hinzu.
   * Geben Sie die Acrobat-Kompatibilitätsoption an, indem Sie eine `CertificateEncryptionCompatibility` Auflistungswert zum `CertificateEncryptionOptionSpec` -Objekt `compat` Datenelement. Weisen Sie beispielsweise `CertificateEncryptionCompatibility.ACRO_7` zu diesem Datenelement hinzu.

1. Erstellen Sie ein zertifikatverschlüsseltes PDF-Dokument.

   Verschlüsseln Sie das PDF-Dokument mit einem Zertifikat, indem Sie die `EncryptionServiceService` -Objekt `encryptPDFUsingCertificates` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das das zu verschlüsselende PDF-Dokument enthält.
   * Die `Object` -Array, das Zertifikatinformationen speichert.
   * Die `CertificateEncryptionOptionSpec` -Objekt, das Verschlüsselungslaufzeitoptionen enthält.

   Die `encryptPDFUsingCertificates` -Methode gibt eine `BLOB` -Objekt, das ein zertifikatverschlüsseltes PDF-Dokument enthält.

1. Speichern Sie das verschlüsselte PDF-Dokument als PDF-Datei.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des gesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt der `BLOB` -Objekt, das von der `encryptPDFUsingCertificates` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `binaryData` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Zertifikatbasierte Verschlüsselung entfernen {#removing-certificate-based-encryption}

Zertifikatbasierte Verschlüsselung kann aus einem PDF-Dokument entfernt werden, damit Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können. Um die Verschlüsselung von einem PDF-Dokument zu entfernen, das mit einem Zertifikat verschlüsselt ist, muss auf einen öffentlichen Schlüssel verwiesen werden. Nachdem die Verschlüsselung aus einem PDF-Dokument entfernt wurde, ist sie nicht mehr sicher.

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Führen Sie die folgenden Schritte aus, um die zertifikatbasierte Verschlüsselung von einem PDF-Dokument zu entfernen:

1. Projektdateien einschließen.
1. Erstellen Sie einen Verschlüsselungsdienst-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Entfernen Sie die Verschlüsselung.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Service-Clients**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service-API verwenden, erstellen Sie eine `EncrytionServiceClient` -Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie eine `EncryptionServiceService` -Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um die zertifikatbasierte Verschlüsselung zu entfernen. Wenn Sie versuchen, die Verschlüsselung von einem nicht verschlüsselten PDF-Dokument zu entfernen, wird eine Ausnahme ausgelöst. Wenn Sie versuchen, die zertifikatbasierte Verschlüsselung aus einem kennwortverschlüsselten Dokument zu entfernen, wird eine Ausnahme ausgelöst.

**Verschlüsselung entfernen**

Zum Entfernen der zertifikatbasierten Verschlüsselung von einem verschlüsselten PDF-Dokument benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch den privaten Schlüssel, der dem Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wurde. Der Aliaswert des privaten Schlüssels wird beim Entfernen der zertifikatbasierten Verschlüsselung von einem verschlüsselten PDF-Dokument angegeben. Informationen zum öffentlichen Schlüssel finden Sie unter [Verschlüsseln von PDF-Dokumenten mit Zertifikaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).

>[!NOTE]
>
>Ein privater Schlüssel wird im AEM Forms Trust Store gespeichert. Wenn dort ein Zertifikat platziert wird, wird ein Alias-Wert angegeben.

**PDF-Dokument speichern**

Nachdem die zertifikatbasierte Verschlüsselung aus einem verschlüsselten PDF-Dokument entfernt wurde, können Sie das PDF-Dokument als PDF-Datei speichern. Benutzer können das PDF-Dokument in Adobe Reader oder Acrobat öffnen.

**Siehe auch**

[Zertifikatbasierte Verschlüsselung mit der Java-API entfernen](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-java-api)

[Zertifikatbasierte Verschlüsselung mithilfe der Webdienst-API entfernen](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Zertifikatbasierte Verschlüsselung mit der Java-API entfernen {#remove-certificate-based-encryption-using-the-java-api}

Entfernen Sie die zertifikatbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Java) aus einem PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `EncryptionServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das verschlüsselte PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des verschlüsselten PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie die Verschlüsselung.

   Entfernen Sie die zertifikatbasierte Verschlüsselung vom PDF-Dokument, indem Sie die `EncryptionServiceClient` -Objekt `removePDFCertificateSecurity` -Methode verwenden und die folgenden Werte übergeben:

   * Die `com.adobe.idp.Document` -Objekt, das das verschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Aliasnamen des privaten Schlüssels angibt, der dem zum Verschlüsseln des PDF-Dokuments verwendeten Schlüssel entspricht.

   Die `removePDFCertificateSecurity` -Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt in die Datei ein. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `removePDFCredentialSecurity`-Methode zurückgegeben wurde.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Zertifikatbasierte Verschlüsselung mithilfe der Java-API entfernen](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Zertifikatbasierte Verschlüsselung mithilfe der Webdienst-API entfernen {#remove-certificate-based-encryption-using-the-web-service-api}

Entfernen Sie die zertifikatbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie eine `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `EncryptionServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `EncryptionServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern des verschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` -Objekt, indem der Inhalt des Byte-Arrays dem `BLOB` -Objekt `MTOM` Datenelement.

1. Entfernen Sie die Verschlüsselung.

   Rufen Sie die `EncryptionServiceClient` -Objekt `removePDFCertificateSecurity` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das Datei-Stream-Daten enthält, die ein verschlüsseltes PDF-Dokument darstellen.
   * Ein string -Wert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wird.

   Die `removePDFCredentialSecurity` -Methode gibt eine `BLOB` -Objekt, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt, das von der `removePDFPasswordSecurity` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen der Kennwortverschlüsselung {#removing-password-encryption}

Die kennwortbasierte Verschlüsselung kann aus einem PDF-Dokument entfernt werden, sodass Benutzer das PDF-Dokument in Adobe Reader oder Acrobat öffnen können, ohne ein Kennwort angeben zu müssen. Nachdem die kennwortbasierte Verschlüsselung aus einem PDF-Dokument entfernt wurde, ist das Dokument nicht mehr geschützt.

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So entfernen Sie die kennwortbasierte Verschlüsselung von einem PDF-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie einen Verschlüsselungsdienst-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Entfernen Sie das Kennwort.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Service-Clients**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service-API verwenden, erstellen Sie eine `EncrytionServiceClient` -Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie eine `EncryptionServiceService` -Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um kennwortbasierte Verschlüsselung zu entfernen. Wenn Sie versuchen, die Verschlüsselung von einem nicht verschlüsselten PDF-Dokument zu entfernen, wird eine Ausnahme ausgelöst.

**Kennwort entfernen**

Zum Entfernen der kennwortbasierten Verschlüsselung von einem verschlüsselten PDF-Dokument benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch einen Übergeordneten Kennwortwert, der zum Entfernen der Verschlüsselung vom PDF-Dokument verwendet wird. Das Kennwort zum Öffnen eines kennwortverschlüsselten PDF-Dokuments kann nicht zum Entfernen der Verschlüsselung verwendet werden. Ein Übergeordnetes Kennwort wird angegeben, wenn das PDF-Dokument mit einem Kennwort verschlüsselt wird. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).

**PDF-Dokument speichern**

Nachdem der Encryption-Dienst die kennwortbasierte Verschlüsselung von einem PDF-Dokument entfernt hat, können Sie das PDF-Dokument als PDF-Datei speichern. Benutzer können das PDF-Dokument in Adobe Reader oder Acrobat öffnen, ohne ein Kennwort anzugeben.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Kennwortbasierte Verschlüsselung mit der Java-API entfernen {#remove-password-based-encryption-using-the-java-api}

Entfernen Sie mithilfe der Verschlüsselungs-API (Java) die kennwortbasierte Verschlüsselung von einem PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-encryption-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `EncryptionServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das verschlüsselte PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie das Kennwort.

   Entfernen Sie die kennwortbasierte Verschlüsselung vom PDF-Dokument, indem Sie die `EncryptionServiceClient` -Objekt `removePDFPasswordSecurity` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das verschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Übergeordneten Kennwortwert angibt, der zum Entfernen der Verschlüsselung vom PDF-Dokument verwendet wird.

   Die `removePDFPasswordSecurity` -Methode gibt eine `com.adobe.idp.Document` -Objekt, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie eine `java.io.File` -Objekt ein und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt in die Datei ein. Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `removePDFPasswordSecurity`-Methode zurückgegeben wurde.

**Siehe auch**

[Schnellstart (SOAP-Modus): Kennwortbasierte Verschlüsselung mithilfe der Java-API entfernen](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api)

### Kennwortbasierte Verschlüsselung mithilfe der Webdienst-API entfernen {#remove-password-based-encryption-using-the-web-service-api}

Entfernen Sie die kennwortbasierte Verschlüsselung mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie eine `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `EncryptionServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `EncryptionServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird zum Speichern eines kennwortverschlüsselten PDF-Dokuments verwendet.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` -Objekt, indem der Inhalt des Byte-Arrays dem `BLOB` -Objekt `MTOM` Datenelement.

1. Entfernen Sie das Kennwort.

   Rufen Sie die `EncryptionServiceService` -Objekt `removePDFPasswordSecurity` -Methode verwenden und die folgenden Werte übergeben:

   * Die `BLOB` -Objekt, das Datei-Stream-Daten enthält, die ein verschlüsseltes PDF-Dokument darstellen.
   * Ein string -Wert, der den Kennwortwert angibt, der zum Entfernen der Verschlüsselung vom PDF-Dokument verwendet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben.

   Die `removePDFPasswordSecurity` -Methode gibt eine `BLOB` -Objekt, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie eine `System.IO.FileStream` -Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekt, das von der `removePDFPasswordSecurity` -Methode. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie eine `System.IO.BinaryWriter` -Objekt durch Aufrufen des Konstruktors und Übergeben des `System.IO.FileStream` -Objekt.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entsperren verschlüsselter PDF-Dokumente {#unlocking-encrypted-pdf-documents}

Ein kennwortverschlüsseltes oder zertifikatverschlüsseltes PDF-Dokument muss entsperrt werden, bevor ein anderer AEM Forms-Vorgang ausgeführt werden kann. Wenn Sie versuchen, einen Vorgang für ein verschlüsseltes PDF-Dokument auszuführen, generieren Sie eine Ausnahme. Nachdem Sie ein verschlüsseltes PDF-Dokument entsperrt haben, können Sie einen oder mehrere Vorgänge darauf ausführen. Diese Vorgänge können zu anderen Diensten gehören, z. B. zum Acrobat Reader DC Extensions-Dienst.

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

So entsperren Sie ein verschlüsseltes PDF-Dokument:

1. Projektdateien einschließen.
1. Erstellen Sie einen Verschlüsselungsdienst-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Entsperren Sie das Dokument.
1. Führen Sie einen AEM Forms-Vorgang aus.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Erstellen eines Verschlüsselungs-Service-Clients**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service-API verwenden, erstellen Sie eine `EncrytionServiceClient` -Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie eine `EncryptionServiceService` -Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein verschlüsseltes PDF-Dokument abrufen, um es zu entsperren. Wenn Sie versuchen, ein nicht verschlüsseltes PDF-Dokument zu entsperren, wird eine Ausnahme ausgelöst.

**Entsperren des Dokuments**

Zum Entsperren eines kennwortverschlüsselten PDF-Dokuments benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch einen Kennwortwert, der zum Öffnen eines kennwortverschlüsselten PDF-Dokuments verwendet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben. (Siehe [Verschlüsseln von PDF-Dokumenten mit einem Kennwort](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).

Zum Entsperren eines zertifikatverschlüsselten PDF-Dokuments benötigen Sie sowohl ein verschlüsseltes PDF-Dokument als auch den Aliaswert des öffentlichen Schlüssels, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wurde.

**Durchführen eines AEM Forms-Vorgangs**

Nachdem ein verschlüsseltes PDF-Dokument entsperrt wurde, können Sie einen weiteren Dienstvorgang durchführen, z. B. Verwendungsrechte darauf anwenden. Dieser Vorgang gehört zum Acrobat Reader DC Extensions-Dienst.

**Siehe auch**

[Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-java-api)

[Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Webdienst-API.](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API {#unlock-an-encrypted-pdf-document-using-the-java-api}

Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Verschlüsselungs-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `EncryptionServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das verschlüsselte PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des verschlüsselten PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entsperren Sie das Dokument.

   Entsperren Sie ein verschlüsseltes PDF-Dokument, indem Sie die `EncryptionServiceClient` -Objekt `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` -Methode.

   Um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die `unlockPDFUsingPassword` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das kennwortverschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Kennwortwert angibt, der zum Öffnen eines kennwortverschlüsselten PDF-Dokuments verwendet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben.

   Um ein mit einem Zertifikat verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die `unlockPDFUsingCredential` -Methode verwenden und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` -Objekt, das das zertifikatverschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem zum Verschlüsseln des PDF-Dokuments verwendeten privaten Schlüssel entspricht.

   Die `unlockPDFUsingPassword` und `unlockPDFUsingCredential` Methoden, die beide eine `com.adobe.idp.Document` -Objekt, das Sie zur Ausführung eines Vorgangs an eine andere AEM Forms Java-Methode übergeben.

1. Führen Sie einen AEM Forms-Vorgang aus.

   Führen Sie einen AEM Forms-Vorgang für das entsperrte PDF-Dokument aus, um Ihre Geschäftsanforderungen zu erfüllen. Wenn Sie beispielsweise Verwendungsrechte auf ein entsperrtes PDF-Dokument anwenden möchten, übergeben Sie die `com.adobe.idp.Document` -Objekt, das von der `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` -Methoden `ReaderExtensionsServiceClient` -Objekt `applyUsageRights` -Methode.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Entsperren eines verschlüsselten PDF-Dokuments mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api) (SOAP-Modus)

[Anwenden von Nutzungsrechten auf PDF-Dokumente](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Webdienst-API. {#unlock-an-encrypted-pdf-document-using-the-web-service-api}

Entsperren Sie ein verschlüsseltes PDF-Dokument mithilfe der Verschlüsselungs-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Verschlüsselungsdienst-Client.

   * Erstellen Sie eine `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `EncryptionServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `EncryptionServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie ein verschlüsseltes PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` -Objekt, indem der Inhalt des Byte-Arrays dem `BLOB` -Objekt `MTOM` Datenelement.

1. Entsperren Sie das Dokument.

   Entsperren Sie ein verschlüsseltes PDF-Dokument, indem Sie die `EncryptionServiceClient` -Objekt `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` -Methode.

   Um ein mit einem Kennwort verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die `unlockPDFUsingPassword` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das kennwortverschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Kennwortwert angibt, der zum Öffnen eines kennwortverschlüsselten PDF-Dokuments verwendet wird. Dieser Wert wird beim Verschlüsseln des PDF-Dokuments mit einem Kennwort angegeben.

   Um ein mit einem Zertifikat verschlüsseltes PDF-Dokument zu entsperren, rufen Sie die `unlockPDFUsingCredential` -Methode verwenden und die folgenden Werte übergeben:

   * A `BLOB` -Objekt, das das zertifikatverschlüsselte PDF-Dokument enthält.
   * Ein string -Wert, der den Aliasnamen des öffentlichen Schlüssels angibt, der dem privaten Schlüssel entspricht, der zum Verschlüsseln des PDF-Dokuments verwendet wird.

   Die `unlockPDFUsingPassword` und `unlockPDFUsingCredential` Methoden, die beide eine `com.adobe.idp.Document` -Objekt, das Sie zur Ausführung eines Vorgangs an eine andere AEM Forms-Methode übergeben.

1. Führen Sie einen AEM Forms-Vorgang aus.

   Führen Sie einen AEM Forms-Vorgang für das entsperrte PDF-Dokument aus, um Ihre Geschäftsanforderungen zu erfüllen. Wenn Sie beispielsweise Verwendungsrechte auf das entsperrte PDF-Dokument anwenden möchten, übergeben Sie die `BLOB` -Objekt, das von der `unlockPDFUsingPassword` oder `unlockPDFUsingCredential` -Methoden `ReaderExtensionsServiceClient` -Objekt `applyUsageRights` -Methode.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Bestimmen des Verschlüsselungstyps {#determining-encryption-type}

Sie können den Verschlüsselungstyp, der ein PDF-Dokument schützt, programmgesteuert mithilfe der Java Encryption Service-API oder der Web Service Encryption Service-API bestimmen. Manchmal ist es erforderlich, dynamisch zu bestimmen, ob ein PDF-Dokument verschlüsselt ist, und gegebenenfalls den Verschlüsselungstyp. Sie können beispielsweise bestimmen, ob ein PDF-Dokument mit kennwortbasierter Verschlüsselung oder einer Rights Management-Richtlinie geschützt ist.

Ein PDF-Dokument kann durch die folgenden Verschlüsselungstypen geschützt werden:

* Kennwortbasierte Verschlüsselung
* Zertifikatbasierte Verschlüsselung
* Eine Richtlinie, die vom Rights Management-Dienst erstellt wird
* Ein anderer Verschlüsselungstyp

>[!NOTE]
>
>Weitere Informationen zum Encryption-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

So bestimmen Sie den Verschlüsselungstyp, der ein PDF-Dokument schützt:

1. Projektdateien einschließen.
1. Erstellen Sie einen Verschlüsselungsdienst-Client.
1. Rufen Sie das verschlüsselte PDF-Dokument ab.
1. Bestimmen Sie den Verschlüsselungstyp.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

**Dienstclient erstellen**

Um programmgesteuert einen Encryption-Dienstvorgang durchzuführen, müssen Sie einen Encryption-Dienstclient erstellen. Wenn Sie die Java Encryption Service-API verwenden, erstellen Sie eine `EncrytionServiceClient` -Objekt. Wenn Sie die Webdienst-Verschlüsselungs-Service-API verwenden, erstellen Sie eine `EncryptionServiceService` -Objekt.

**Verschlüsseltes PDF-Dokument abrufen**

Sie müssen ein PDF-Dokument abrufen, um die Art der Verschlüsselung zu bestimmen, die sie schützt.

**Ermitteln des Verschlüsselungstyps**

Sie können die Art der Verschlüsselung bestimmen, die ein PDF-Dokument schützt. Wenn das PDF-Dokument nicht geschützt ist, werden Sie vom Encryption-Dienst darüber informiert, dass das PDF-Dokument nicht gesichert ist.

**Siehe auch**

[Ermitteln des Verschlüsselungstyps mithilfe der Java-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-java-api)

[Ermitteln des Verschlüsselungstyps mithilfe der Webdienst-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Verschlüsselungsdienst](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Schützen von Dokumenten mit Richtlinien](/help/forms/developing/protecting-documents-policies.md#protecting-documents-with-policies)

### Ermitteln des Verschlüsselungstyps mithilfe der Java-API {#determine-the-encryption-type-using-the-java-api}

Bestimmen Sie mithilfe der Verschlüsselungs-API (Java) den Verschlüsselungstyp, der ein PDF-Dokument schützt:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-encryption-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Service-Client.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie eine `EncryptionServiceClient` -Objekt durch Verwendung seines Konstruktors und Übergabe des `ServiceClientFactory` -Objekt.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie eine `java.io.FileInputStream` -Objekt, das das PDF-Dokument darstellt, indem es seinen Konstruktor verwendet und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Bestimmen Sie den Verschlüsselungstyp.

   * Bestimmen Sie den Verschlüsselungstyp, indem Sie die `EncryptionServiceClient` -Objekt `getPDFEncryption` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das PDF-Dokument enthält. Diese Methode gibt eine `EncryptionTypeResult` -Objekt.
   * Rufen Sie die `EncryptionTypeResult` -Objekt `getEncryptionType` -Methode. Diese Methode gibt eine `EncryptionType` enum -Wert, der den Verschlüsselungstyp angibt. Wenn das PDF-Dokument beispielsweise mit kennwortbasierter Verschlüsselung geschützt ist, gibt diese Methode `EncryptionType.PASSWORD`.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Bestimmen des Verschlüsselungstyps mithilfe der Java-API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-determining-encryption-type-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ermitteln des Verschlüsselungstyps mithilfe der Webdienst-API {#determine-the-encryption-type-using-the-web-service-api}

Bestimmen Sie mithilfe der Verschlüsselungs-API (Webdienst) den Typ der Verschlüsselung, die ein PDF-Dokument schützt:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Service-Client.

   * Erstellen Sie eine `EncryptionServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie eine `EncryptionServiceClient.Endpoint.Address` -Objekt mithilfe der `System.ServiceModel.EndpointAddress` -Konstruktor. Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/EncryptionService?WSDL`. Sie müssen die `lc_version` -Attribut. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie eine `System.ServiceModel.BasicHttpBinding` -Objekt durch Abrufen des Werts der `EncryptionServiceClient.Endpoint.Binding` -Feld. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den Benutzernamen AEM Formulare zu `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Konstantenwert zuweisen `HttpClientCredentialType.Basic` zum Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Konstantenwert zuweisen `BasicHttpSecurityMode.TransportCredentialOnly` zum Feld `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie das verschlüsselte PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie eine `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des verschlüsselten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream` -Objekt. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie die `BLOB` -Objekt, indem der Inhalt des Byte-Arrays dem `BLOB` -Objekt `MTOM` Datenelement.

1. Bestimmen Sie den Verschlüsselungstyp.

   * Rufen Sie die `EncryptionServiceClient` -Objekt `getPDFEncryption` -Methode und übergeben Sie die `BLOB` -Objekt, das das PDF-Dokument enthält. Diese Methode gibt eine `EncryptionTypeResult` -Objekt.
   * Den Wert der `EncryptionTypeResult` -Objekt `encryptionType` Datenmethode. Wenn das PDF-Dokument beispielsweise mit kennwortbasierter Verschlüsselung geschützt ist, lautet der Wert dieses Datenelements `EncryptionType.PASSWORD`.

**Siehe auch**

[Zusammenfassung der Schritte](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
