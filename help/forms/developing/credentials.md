---
title: Arbeiten mit Anmeldeinformationen
seo-title: Working with Credentials
description: Importieren Sie Anmeldeinformationen mithilfe der Trust Manager-API und der Java-API in AEM Forms. Erfahren Sie außerdem, wie Sie Berechtigungen mithilfe der Trust Manager-API und der Java-API löschen.
seo-description: Import credentials into AEM Forms using the Trust Manager API and Java API. In addition, learn how to delete credentials using the Trust Manager API and Java API.
uuid: b794428f-49bf-4a91-bc5f-d855881f4f38
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: bc06d9bd-af6c-47b1-b46f-aab990ef5816
role: Developer
exl-id: 7dcfcee1-998e-41d8-badc-3106055e6ba7
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 12%

---

# Arbeiten mit Anmeldeinformationen {#working-with-credentials}

**Über den Berechtigungsdienst**

Eine Berechtigung enthält Informationen zu Ihrem privaten Schlüssel, der zum Signieren bzw. Identifizieren von Dokumenten benötigt wird. Ein Zertifikat enthält Informationen zum öffentlichen Schlüssel, den Sie für die Trust Store-Verwaltung konfigurieren. AEM Forms verwendet Zertifikate und Berechtigungen für verschiedene Zwecke:

* Acrobat Reader DC Extensions verwendet eine Berechtigung zur Aktivierung von Adobe Reader-Verwendungsrechten in PDF-Dokumenten. (Siehe [Anwenden von Nutzungsrechten auf PDF-Dokumente](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).
* Der Signature-Dienst greift beim Ausführen von Vorgängen wie dem digitalen Signieren von PDF-Dokumenten auf Zertifikate und Berechtigungen zu. (Siehe [Digitales Signieren von PDF-Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).

Sie können programmgesteuert mit dem Berechtigungsdienst über die Java-API von Trust Manager interagieren. Sie können die folgenden Aufgaben ausführen:

* [Importieren von Anmeldeinformationen mithilfe der Trust Manager-API](credentials.md#importing-credentials-by-using-the-trust-manager-api)
* [Löschen von Anmeldeinformationen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

>[!NOTE]
>
>Sie können Zertifikate auch über Administration Console importieren und löschen. (Siehe [Hilfe zur Administration.](https://www.adobe.com/go/learn_aemforms_admin_63))

## Importieren von Anmeldeinformationen mithilfe der Trust Manager-API {#importing-credentials-by-using-the-trust-manager-api}

Sie können eine Berechtigung programmgesteuert mit der Trust Manager-API in AEM Forms importieren. Sie können beispielsweise eine Berechtigung importieren, die zum Signieren eines PDF-Dokuments verwendet wird. (Siehe [Digitales Signieren von PDF-Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)).

Beim Importieren einer Berechtigung geben Sie einen Alias für die Berechtigung an. Der Alias wird verwendet, um einen Forms-Vorgang auszuführen, für den eine Berechtigung erforderlich ist. Nach dem Import kann eine Berechtigung in Administration Console angezeigt werden, wie in der folgenden Abbildung dargestellt. Beachten Sie, dass der Alias für die Berechtigung *Secure*.

![ww_ww_truststore](assets/ww_ww_truststore.png)

>[!NOTE]
>
>Sie können eine Berechtigung nicht mit Webdiensten in AEM Forms importieren.

### Zusammenfassung der Schritte {#summary-of-steps}

Um eine Berechtigung in AEM Forms zu importieren, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen Client für den Berechtigungsdienst.
1. Verweisen Sie auf die Berechtigung.
1. Führen Sie den Importvorgang durch.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-truststore-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Berechtigungsdienstclients**

Bevor Sie eine Berechtigung programmgesteuert in AEM Forms importieren können, erstellen Sie einen Berechtigungsdienstclient. Weitere Informationen finden Sie unter [Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Referenz: Berechtigung**

Referenzieren Sie eine Berechtigung, die Sie in AEM Forms importieren möchten. Der Schnellstart für diesen Abschnitt verweist auf eine P12-Datei im Dateisystem.

**Importvorgang durchführen**

Nachdem Sie auf die Berechtigung verwiesen haben, importieren Sie die Berechtigung in AEM Forms. Wenn die Berechtigung nicht erfolgreich importiert wurde, wird eine Ausnahme ausgelöst. Beim Importieren einer Berechtigung geben Sie einen Alias für die Berechtigung an.

**Siehe auch**

[Importieren von Anmeldeinformationen mit der Java-API](credentials.md#import-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Credential Service](/help/forms/developing/credential-service-java-api-quick.md#credential-service-java-api-quick-start-soap)

[Löschen von Anmeldeinformationen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

### Importieren von Anmeldeinformationen mit der Java-API {#import-credentials-using-the-java-api}

Importieren Sie eine Berechtigung mithilfe der Trust Manager-API (Java) in AEM Forms:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-truststore-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Berechtigungsdienstclients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `CredentialServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenz: Berechtigung

   * Erstellen Sie ein Objekt `java.io.FileInputStream`, indem Sie den Konstruktor verwenden. Übergeben Sie einen string -Wert, der den Speicherort der Berechtigung angibt.
   * Erstellen Sie eine `com.adobe.idp.Document` -Objekt, das die Berechtigung mithilfe der `com.adobe.idp.Document` -Konstruktor. Übergeben Sie die `java.io.FileInputStream` -Objekt, das die Berechtigung für den Konstruktor enthält.

1. Importvorgang durchführen

   * Erstellen Sie ein Zeichenfolgen-Array, das ein Element enthält. Wert zuweisen `truststore.usage.type.sign` zum Element hinzu.
   * Rufen Sie die `CredentialServiceClient` -Objekt `importCredential` -Methode verwenden und die folgenden Werte übergeben:

      * Ein string -Wert, der den Alias-Wert für die Berechtigung angibt.
      * Die `com.adobe.idp.Document` -Instanz, die die Berechtigung speichert.
      * Ein string -Wert, der das Kennwort angibt, das mit der Berechtigung verknüpft ist.
      * Das Zeichenfolgen-Array, das den Nutzungswert enthält. Sie können diesen Wert beispielsweise angeben `truststore.usage.type.sign`. Um eine Berechtigung für die Reader-Erweiterung zu importieren, geben Sie `truststore.usage.type.lcre`.

**Siehe auch**

[Importieren von Anmeldeinformationen mithilfe der Trust Manager-API](credentials.md#importing-credentials-by-using-the-trust-manager-api)

[Schnellstart (SOAP-Modus): Importieren von Anmeldeinformationen mit der Java-API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-importing-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Löschen von Anmeldeinformationen mithilfe der Trust Manager-API {#deleting-credentials-by-using-the-trust-manager-api}

Sie können eine Berechtigung programmgesteuert löschen, indem Sie die Trust Manager-API verwenden. Beim Löschen einer Berechtigung geben Sie einen Alias an, der der Berechtigung entspricht. Nach dem Löschen kann eine Berechtigung nicht mehr zum Ausführen eines Vorgangs verwendet werden.

>[!NOTE]
>
>Sie können eine Berechtigung nicht mithilfe von Webdiensten in AEM Forms löschen.

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um eine Berechtigung zu löschen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen Client für den Berechtigungsdienst.
1. Führen Sie den Löschvorgang durch.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-truststore-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Berechtigungsdienstclients**

Bevor Sie eine Berechtigung programmgesteuert löschen können, erstellen Sie einen Client des Data Integration Service. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind. Weitere Informationen finden Sie unter [Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Löschvorgang durchführen**

Um eine Berechtigung zu löschen, geben Sie den Alias an, der der Berechtigung entspricht. Wenn Sie einen Alias angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Importieren von Anmeldeinformationen mit der Java-API](credentials.md#import-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Importieren von Anmeldeinformationen mit der Java-API](credentials.md#import-credentials-using-the-java-api)

### Löschen von Anmeldeinformationen mithilfe der Java-API {#deleting-credentials-using-the-java-api}

Löschen Sie mithilfe der Trust Manager-API (Java) eine Berechtigung aus AEM Forms:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-truststore-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Berechtigungsdienstclients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `CredentialServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Löschvorgang durchführen

   Rufen Sie die `CredentialServiceClient` -Objekt `deleteCredential` -Methode und übergeben Sie einen string -Wert, der den Alias-Wert angibt.

**Siehe auch**

[Löschen von Anmeldeinformationen mithilfe der Trust Manager-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

[Schnellstart (SOAP-Modus): Löschen von Anmeldeinformationen mithilfe der Java-API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-deleting-credentials-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
