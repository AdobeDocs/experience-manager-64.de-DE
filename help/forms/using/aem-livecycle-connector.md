---
title: Verbinden von AEM Forms mit Adobe LiveCycle
seo-title: Connecting AEM Forms with Adobe LiveCycle
description: Mit AEM LiveCycle-Connector können Sie LiveCycle ES4 Document Services aus AEM Apps und Workflows starten.
seo-description: AEM LiveCycle connector allows you to start LiveCycle ES4 Document Services from within AEM apps and workflows.
uuid: 7dc9d5ec-7b19-4d93-936d-81ceb45dfffa
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 7e404b45-1302-4dd1-b3c9-3f47fedb5f94
role: Admin
exl-id: f40674c1-a1dd-41ef-8a19-82ece3103bcc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 25%

---

# Verbinden von AEM Forms mit Adobe LiveCycle {#connecting-aem-forms-with-adobe-livecycle}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe Experience Manager (AEM) LiveCycle-Connector ermöglicht den nahtlosen Aufruf von Adobe LiveCycle ES4 Document Services aus AEM Web-Apps und -Workflows. LiveCycle bietet ein Rich-Client-SDK, mit dem Clientanwendungen LiveCycle-Dienste mithilfe von Java-APIs starten können. AEM LiveCycle Connector vereinfacht die Verwendung dieser APIs in der OSGi-Umgebung.

## Verbinden des AEM-Servers mit Adobe LiveCycle {#connecting-aem-server-to-adobe-livecycle}

AEM LiveCycle Connector ist Teil des [AEM Forms-Add-On-Pakets](/help/forms/using/installing-configuring-aem-forms-osgi.md). Nachdem Sie das Add-On-Paket für AEM Forms installiert haben, führen Sie die folgenden Schritte aus, um Details des LiveCycle-Servers zur AEM Web Console hinzuzufügen.

1. Suchen Sie AEM Konfigurationsmanager der Web Console nach der Konfigurationskomponente des LiveCycle Client SDK für die Adobe.
1. Klicken Sie auf die Komponente, um die URL, den Benutzernamen und das Kennwort des Konfigurationsservers zu bearbeiten.
1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

Obwohl die Eigenschaften selbsterklärend sind, sind die wichtigsten wie folgt:

* **Server URL** – gibt die URL für den LiveCycle-Server an. Wenn Sie möchten, dass LiveCycle und AEM über HTTPS kommunizieren, starten Sie AEM mit der folgenden JVM

   ```
   argument 
    -Djavax.net.ssl.trustStore=<<em>path to LC keystore</em>>
   ```

   Option.

* **Benutzername** – gibt den Benutzernamen des Kontos an, das verwendet wird, um die Kommunikation zwischen AEM und LiveCycle herzustellen. Das Konto ist ein LiveCycle-Benutzerkonto, das zum Start von Document Services berechtigt ist.
* **Kennwort** – gibt das Kennwort an.
* **Dienstname** - Gibt die Dienste an, die mit den Benutzeranmeldeinformationen gestartet werden, die in den Feldern &quot;Benutzername&quot;und &quot;Kennwort&quot;angegeben sind. Standardmäßig werden beim Starten von LiveCycle-Diensten keine Anmeldeinformationen übergeben.

## Starten von Document Services {#starting-document-services}

Clientanwendungen können LiveCycle-Dienste programmgesteuert mit einer Java-API, Webdiensten, Remoting und REST starten. Für Java-Clients kann die Anwendung das LiveCycle SDK verwenden. Das LiveCycle SDK stellt eine Java-API zum Remote-Starten dieser Dienste bereit. Um beispielsweise ein Microsoft Word-Dokument in PDF zu konvertieren, startet der Client GeneratePDFService. Der Aufruf erfolgt durch folgende Schritte:

1. Erstellen Sie eine ServiceClientFactory-Instanz.
1. Jeder Dienst stellt eine Client-Klasse bereit. Um einen Dienst zu starten, erstellen Sie eine Client-Instanz des Dienstes.
1. Starten Sie den Dienst und verarbeiten Sie das Ergebnis.

AEM LiveCycle Connector vereinfacht den Fluss, indem diese Client-Instanzen als OSGi-Dienste verfügbar gemacht werden, auf die mit standardmäßigen OSGi-Mitteln zugegriffen werden kann. LiveCycle Connector umfasst die folgenden Funktionen:

* Clientinstanzen als OSGi-Dienst – Die als OSGI-Pakete gebündelten Clients sind im Abschnitt [Document Services-Liste](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p) aufgeführt. Jede Client-JAR-Datei registriert die Client-Instanz als OSGi-Dienst in der OSGi Service Registry.
* Weitergabe von Benutzerberechtigungen: Die für die Verbindung mit dem LiveCycle-Server erforderlichen Verbindungsdetails werden zentral verwaltet.
* ServiceClientFactory Service: Um die Prozesse zu starten, kann die Client-Anwendung auf die ServiceClientFactory-Instanz zugreifen.

### Starten über Dienstverweise aus der OSGi Service Registry {#starting-via-service-references-from-osgi-service-registry}

Um einen angezeigten Dienst aus AEM heraus zu starten, führen Sie die folgenden Schritte aus:

1. Bestimmen Sie Maven-Abhängigkeiten. Fügen Sie der erforderlichen Client-JAR-Datei in Ihrer maven pom.xml-Datei Abhängigkeiten hinzu. Fügen Sie mindestens &quot;dependency&quot;zu den JARs adobe-livecycle-client und adobe-usermanager-client hinzu.

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-livecycle-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-usermanager-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-cq-integration-api</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

   Um einen Dienst zu starten, fügen Sie die entsprechende Maven-Abhängigkeit für den Dienst hinzu. Eine Liste der Abhängigkeiten finden Sie unter [Document Service-Liste](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p). Fügen Sie beispielsweise zum Dienst für das Generieren von PDF-Dokumenten die folgende Abhängigkeit hinzu:

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-generatepdf-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

1. Rufen Sie die Dienstreferenz ab. Rufen Sie einen Handle für die Dienstinstanz ab. Wenn Sie eine Java-Klasse schreiben, können Sie die Deklarative Services-Anmerkungen verwenden.

   ```java
   import com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient;
   import com.adobe.livecycle.generatepdf.client.CreatePDFResult;
   import com.adobe.idp.Document;
   
   @Reference
   GeneratePdfServiceClient generatePDF;
   ...
   
   Resource r = resourceResolver.getResource("/path/tp/docx");
   Document sourceDoc = new Document(r.adaptTo(InputStream.class));
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

   Das obige Codefragment startet die createPDF-API von GeneratePdfServiceClient, um ein Dokument in PDF zu konvertieren. Sie können einen ähnlichen Aufruf in einer JSP mit dem folgenden Code durchführen. Der wesentliche Unterschied besteht darin, dass der folgende Code Sling ScriptHelper verwendet, um auf GeneratePdfServiceClient zuzugreifen.

   ```java
   <%@ page import="com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient" %>
   <%@ page import="com.adobe.livecycle.generatepdf.client.CreatePDFResult" %>
   <%@ page import="com.adobe.idp.Document" %>
   
   GeneratePdfServiceClient generatePDF = sling.getService(GeneratePdfServiceClient.class);
   Document sourceDoc = ...
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

### Starten über ServiceClientFactory {#starting-via-serviceclientfactory}

In einigen Fällen ist die ServiceClientFactory-Klasse erforderlich. Beispielsweise benötigen Sie ServiceClientFactory, um Prozesse aufzurufen.

```java
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider;
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 
@Reference
ServiceClientFactoryProvider scfProvider;
 
...
ServiceClientFactory scf = scfProvider.getDefaultServiceClientFactory();
...
```

## RunAs-Unterstützung {#runas-support}

Fast jeder Document Service in LiveCycle erfordert Authentifizierung. Sie können eine der folgenden Optionen verwenden, um diese Dienste zu starten, ohne explizite Anmeldedaten im Code anzugeben:

### Whitelist-Konfiguration {#allowlist-configuration}

Die LiveCycle Client SDK-Konfiguration enthält eine Einstellung zu Dienstnamen. Diese Konfiguration ist eine Liste von Diensten, für die die Aufruflogik standardmäßig Administratorberechtigungen verwendet. Wenn Sie beispielsweise DirectoryManager-Dienste (Teil der User Management-API) zu dieser Liste hinzufügen, kann jeder Client-Code den Dienst direkt verwenden und die Aufrufebene gibt die konfigurierten Anmeldeinformationen automatisch als Teil der an den LiveCycle-Server gesendeten Anfrage weiter.

### RunAsManager {#runasmanager}

Im Rahmen der Integration wird ein neuer RunAsManager-Dienst bereitgestellt. Damit können Sie programmatisch die Anmeldedaten steuern, die beim Aufruf des LiveCycle-Servers verwendet werden sollen.

```java
import com.adobe.livecycle.dsc.clientsdk.security.PasswordCredential;
import com.adobe.livecycle.dsc.clientsdk.security.PrivilegedAction;
import com.adobe.livecycle.dsc.clientsdk.security.RunAsManager;
import com.adobe.idp.dsc.registry.component.ComponentRegistry;
  
@Reference
private RunAsManager runAsManager;
  
List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
            public List<Component> run() {
                return componentRegistry.getComponents();
            }
        });
assertNotNull(components);
```

Wenn Sie andere Anmeldedaten übergeben möchten, können Sie die Überlastungsmethode verwenden, die eine PasswordCredential -Instanz akzeptiert.

```java
PasswordCredential credential = new PasswordCredential("administrator","password");
List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
    public List<Component> run() {
        return componentRegistry.getComponents();
    }
},credential);
```

### InvocationRequest-Eigenschaft {#invocationrequest-property}

Wenn Sie einen Prozess aufrufen oder die ServiceClientFactory-Klasse direkt verwenden und eine InvocationRequest erstellen, können Sie eine Eigenschaft angeben, um anzugeben, dass die Aufrufebene konfigurierte Anmeldeinformationen verwenden soll.

```java
import com.adobe.idp.dsc.InvocationResponse
import com.adobe.idp.dsc.InvocationRequest
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory
import com.adobe.livecycle.dsc.clientsdk.InvocationProperties
   
ServiceClientFactoryProvider scfp = sling.getService(ServiceClientFactoryProvider.class)
ServiceClientFactory serviceClientFactory = scfp.getDefaultServiceClientFactory()
InvocationRequest ir = serviceClientFactory.createInvocationRequest("sample/LetterSubmissionProcess", "invoke", new HashMap(), true);
  
//Here we are invoking the request with system user
ir.setProperty(InvocationProperties.INVOKER_TYPE,InvocationProperties.INVOKER_TYPE_SYSTEM)
   
InvocationResponse response = serviceClientFactory.getServiceClient().invoke(ir);
```

## Document Services-Liste {#document-services-list}

### Adobe LiveCycle Client SDK API-Bundle {#adobe-livecycle-client-sdk-api-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.idp.um.api.AuthenticationManager
* com.adobe.idp.um.api.DirectoryManager
* com.adobe.idp.um.api.AuthorizationManager
* com.adobe.idp.dsc.registry.service.ServiceRegistry
* com.adobe.idp.dsc.registry.component.ComponentRegistry

#### Maven-Abhängigkeiten {#maven-dependencies}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-client</artifactId>
  <version>11.0.0</version>
</dependency>
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-usermanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Client SDK Bundle {#adobe-livecycle-client-sdk-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.livecycle.dsc.clientsdk.security.RunAsManager
* com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider

#### Maven-Abhängigkeiten {#maven-dependencies-1}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-cq-integration-api</artifactId>
  <version>1.1.10</version>
</dependency>
```

### Adobe LiveCycle TaskManager Client Bundle {#adobe-livecycle-taskmanager-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.idp.taskmanager.dsc.client.task.TaskManager
* com.adobe.idp.taskmanager.dsc.client.TaskManagerQueryService
* com.adobe.idp.taskmanager.dsc.client.queuemanager.QueueManager
* com.adobe.idp.taskmanager.dsc.client.emailsettings.EmailSettingService
* com.adobe.idp.taskmanager.dsc.client.endpoint.TaskManagerEndpointClient
* com.adobe.idp.taskmanager.dsc.client.userlist.UserlistService

#### Maven-Abhängigkeiten {#maven-dependencies-2}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-taskmanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Workflow Client Bundle {#adobe-livecycle-workflow-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.idp.workflow.client.WorkflowServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-3}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-workflow-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle PDF Generator Client Bundle {#adobe-livecycle-pdf-generator-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-4}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-generatepdf-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Application Manager Client Bundle {#adobe-livecycle-application-manager-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.idp.applicationmanager.service.ApplicationManager
* com.adobe.livecycle.applicationmanager.client.ApplicationManager
* com.adobe.livecycle.design.service.DesigntimeService

#### Maven-Abhängigkeiten {#maven-dependencies-5}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-applicationmanager-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Assembler Client Bundle {#adobe-livecycle-assembler-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.assembler.client.AssemblerServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-6}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-assembler-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Form Data Integration Client Bundle {#adobe-livecycle-form-data-integration-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.formdataintegration.client.FormDataIntegrationClient

#### Maven-Abhängigkeiten {#maven-dependencies-7}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-formdataintegration-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Forms Client Bundle {#adobe-livecycle-forms-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.formsservice.client.FormsServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-8}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-forms-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Output Client Bundle {#adobe-livecycle-output-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.output.client.OutputClient

#### Maven-Abhängigkeiten {#maven-dependencies-9}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-output-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Reader Extensions Client Bundle {#adobe-livecycle-reader-extensions-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.readerextensions.client.ReaderExtensionsServiceClient

#### Maven-Abhängigkeiten {#maven-dependencies-10}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-reader-extensions-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Rights Manager Client Bundle {#adobe-livecycle-rights-manager-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.livecycle.rightsmanagement.client.DocumentManager
* com.adobe.livecycle.rightsmanagement.client.EventManager
* com.adobe.livecycle.rightsmanagement.client.ExternalUserManager
* com.adobe.livecycle.rightsmanagement.client.LicenseManager
* com.adobe.livecycle.rightsmanagement.client.WatermarkManager
* com.adobe.livecycle.rightsmanagement.client.PolicyManager
* com.adobe.livecycle.rightsmanagement.client.AbstractPolicyManager

#### Maven-Abhängigkeiten {#maven-dependencies-11}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-rightsmanagement-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Signatures Client Bundle {#adobe-livecycle-signatures-client-bundle}

Der folgende Dienst ist verfügbar:

* com.adobe.livecycle.signatures.client.SignatureServiceClientInterface

#### Maven-Abhängigkeiten {#maven-dependencies-12}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-signatures-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Truststore Client Bundle {#adobe-livecycle-truststore-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.truststore.dsc.TrustConfigurationService
* com.adobe.truststore.dsc.CRLService
* com.adobe.truststore.dsc.CredentialService
* com.adobe.truststore.dsc.CertificateService

#### Maven-Abhängigkeiten {#maven-dependencies-13}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-truststore-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Repository Client Bundle {#adobe-livecycle-repository-client-bundle}

Folgende Dienste sind verfügbar:

* com.adobe.repository.bindings.ResourceRepository
* com.adobe.repository.bindings.ResourceSynchronizer

#### Maven-Abhängigkeiten {#maven-dependencies-14}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-repository-client</artifactId>
  <version>11.0.0</version>
</dependency>
```
