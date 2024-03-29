---
title: Schützen von Dokumenten im Auftrag eines anderen Benutzers
seo-title: Protect a document on behalf of another user
description: Erfahren Sie, wie Sie mit den APIs ein Dokument im Namen eines anderen Benutzers schützen können, ohne die Berechtigungen zum Bearbeiten des Dokuments zu erhalten.
seo-description: Learn how to use the APIs to protect a document on behalf of another user without attaining the permissions to edit the document.
uuid: 76f4b30b-6d0c-4cae-98b3-334efdbf27bb
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 7cb8140d-dd62-4659-8cc7-21361bd5d3f6
feature: Document Security
exl-id: 76f25e65-1bc3-4801-998c-40ff533393e2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 22%

---

# Schützen von Dokumenten im Auftrag eines anderen Benutzers {#protect-a-document-on-behalf-of-another-user}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Das AEM Forms Document Security Java SDK bietet APIs, mit denen ein Benutzerkonto ein Dokument im Namen eines anderen Benutzers schützen kann, ohne die Berechtigungen zum Bearbeiten des Dokuments zu erhalten. Sie können die APIs in einem Workflow-Prozess oder programmgesteuert als Dokumentdienst verwenden. Die neuen APIs sind:

* **protectDocumentUse** die ProtectDocument-API, um eine Richtlinie im Namen eines

   anderen Benutzerkontos auf ein Dokument anzuwenden. Die Berechtigungen des Benutzerkontos, das zur Anwendung der Richtlinie verwendet wird, bleiben auf den Schutz des Dokuments beschränkt. Es werden keine Rechte zum Öffnen und Anzeigen des Dokuments zugewiesen. RMSecureDocumentResult protectDocument(Document inDoc, String documentName, String policySetName, String policyName, RMLocale locale, boolean bExactMatchForNames)

* **createLicenseUse** die CreateLicense-API zum Erstellen einer Lizenz für eine Richtlinie im Namen eines anderen Benutzerkontos. PublishLicenseDTO createLicense(String policyId, String documentName, boolean logSecureDocEvent)
* **protectDocumentWithCoverPageUse** die ProtectDocumentWithCoverPage -API verwenden, um eine Richtlinie anzuwenden und im Namen eines anderen Benutzers einem Dokument eine Titelseite hinzuzufügen. Die Berechtigungen des Benutzerkontos, das zur Anwendung der Richtlinie verwendet wird, bleiben auf den Schutz des Dokuments beschränkt. Es erhält keine Rechte zum Öffnen und Anzeigen des Dokuments. RMSecureDocumentResult protectDocumentWithCoverPage(Document inDoc, String documentName, String policySetName, String policyName, Document coverDoc, boolean bExactMatchForNames)

## Verwenden der APIs zum Schützen eines Dokuments im Namen eines anderen Benutzers {#using-the-apis-to-protect-a-document-on-behalf-of-another-user}

Führen Sie die folgenden Schritte aus, um ein Dokument im Namen eines anderen Benutzers zu schützen, ohne die Berechtigungen zum Bearbeiten des Dokuments zu erhalten:

1. Erstellen Sie einen Richtliniensatz. Beispiel: PolicySet1.
1. Erstellen Sie eine Richtlinie im neu erstellten Richtliniensatz. Beispiel: Policy1 in PolicySet1.
1. Erstellen Sie einen Benutzer mit Rolle Rights Management-Endbenutzer . Beispiel: User1. Legen Sie die Berechtigungen zum Anzeigen von Dokumenten, die mit Policy1 geschützt wurden, für den neu erstellten Benutzer fest.
1. Erstellen Sie eine neue Rolle. Beispiel: Role1. Stellen Sie der neu erstellten Rolle die Berechtigung Dienstaufruf bereit. Erstellen Sie einen Benutzer mit der neu erstellten Rolle. Beispielsweise können Sie User2.Sie können Benutzer2 oder einen Administrator verwenden, um eine SDK-Verbindung zu erstellen und den protectDocument -Dienst aufzurufen.

   Jetzt können Sie den folgenden Beispielcode ausführen, um ein Dokument zu schützen, ohne dem Benutzer, der das Dokument schützt, Berechtigungen zum Bearbeiten des Dokuments zu erteilen:

   ```java
   import java.io.File;
   import java.io.FileInputStream;
   import java.io.FileNotFoundException;
   import java.io.FileOutputStream;
   import java.io.IOException;
   import java.io.InputStream;
   import java.util.Properties;
   
   import com.adobe.edc.common.dto.PublishLicenseDTO;
   import com.adobe.edc.sdk.SDKException;
   import com.adobe.idp.Document;
   import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
   import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
   import com.adobe.livecycle.rightsmanagement.RMSecureDocumentResult;
   import com.adobe.livecycle.rightsmanagement.client.DocumentManager;
   import com.adobe.livecycle.rightsmanagement.client.RightsManagementClient;
   import com.adobe.livecycle.rightsmanagement.client.RightsManagementClient2;
   
   public class PublishAsProtectAPI {
   
   private static final String unprotectedFileName = "C:\\unprotected.pdf";
   private static final String protectedFileName = "C:\\protect.pdf";
   private static final String coverFileName = "C:\\CoverPage.pdf";
   private static final String POLICY_ID = "2EF66008-5E2D-1034-9B06-00000A292C18"; 
   
   public static void main(String[] args) {
   
   try {
   
   Properties connectionProps = new Properties();
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT,"http://localhost:8080");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME,"administrator");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD,"password");
   
   // Create a ServiceClientFactory instance
   ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
   testProtectDocument(factory);
   testProtectDocumentWithCoverPage(factory);
   testProtectDocumentJavaPPL(factory);
   
   } 
   catch (Exception ex) {
   ex.printStackTrace(); }
   }
   
   private static void testProtectDocument(ServiceClientFactory factory) throws FileNotFoundException, SDKException {
   // Create a RightsManagementClient object
   RightsManagementClient rmClient = new RightsManagementClient(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient.getDocumentManager();
   //Reference a policy-protected PDF document from which to remove a policy
   FileInputStream is = new FileInputStream(unprotectedFileName);
   Document inPDF = new Document(is);
   long startTime = System.currentTimeMillis();
   //Remove a policy from the policy-protected PDF document
   RMSecureDocumentResult securePDF = documentManager.protectDocument(inPDF, "test", "newPolicySet", "latest", "DefaultDom", "administrator", null, true);
   System.out.println("Total Time taken for protectDocument = " + (System.currentTimeMillis() - startTime));
   //Save the unsecured PDF document
   File myFile = new File(protectedFileName);
   securePDF.getProtectedDoc().copyToFile(myFile);
   }
   
   private static void testProtectDocumentWithCoverPage(ServiceClientFactory factory) throws FileNotFoundException, SDKException {
   // Create a RightsManagementClient object
   RightsManagementClient rmClient = new RightsManagementClient(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient.getDocumentManager();
   //Reference a policy-protected PDF document from which to remove a policy
   FileInputStream is = new FileInputStream(unprotectedFileName);
   Document inPDF = new Document(is);
   FileInputStream coverIS = new FileInputStream(coverFileName);
   Document inCoverPDF = new Document(coverIS);
   long startTime = System.currentTimeMillis();
   //Remove a policy from the policy-protected PDF document
   RMSecureDocumentResult securePDF = documentManager.protectDocumentWithCoverPage(inPDF, "test", "newPolicySet", "latestPolicy", inCoverPDF, true);
   System.out.println("Total Time taken for Page0ProtectDocument = " + (System.currentTimeMillis() - startTime));
   //Save the unsecured PDF document
   File myFile = new File(protectedFileName);
   securePDF.getProtectedDoc().copyToFile(myFile);
   }
   
   private static PublishLicenseDTO testProtectDocumentJavaPPL (ServiceClientFactory factory) throws SDKException, FileNotFoundException, IOException {
   // Create a RightsManagementClient object
   RightsManagementClient2 rmClient2 = new RightsManagementClient2(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient2.getDocumentManager();
   long startTime = System.currentTimeMillis();
   PublishLicenseDTO license = documentManager.createLicense(POLICY_ID, "Out.pdf", true);
   System.out.println("Create License totalTime = " + (System.currentTimeMillis() - startTime));
   startTime = System.currentTimeMillis();
   // Reference a PDF document to which a policy is applied
   InputStream inputFileStream = new FileInputStream(unprotectedFileName);
   // Apply a policy to the PDF document
   InputStream protectPDF = rmClient2.getRightsManagementEncryptionService().protectDocument(inputFileStream, license);
   // Save the policy-protected PDF document
   File myFile = new File(protectedFileName);
   // write the inputStream to a FileOutputStream
   FileOutputStream outputStream = new FileOutputStream(myFile);
   int read = 0;
   byte[] bytes = new byte[1024];
   while ((read = protectPDF.read(bytes)) != -1) {
   outputStream.write(bytes, 0, read);
   }
   System.out.println("protectPDFDocument totalTime = " + (System.currentTimeMillis() - startTime));
   outputStream.close();
   inputFileStream.close();
   System.out.println("Document Protected Successfully");
   return license;
   }
   }
   ```
