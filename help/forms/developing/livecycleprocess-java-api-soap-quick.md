---
title: Java API-Schnellstart (SOAP) für LiveCycleProcess
seo-title: LiveCycleProcess Java API(SOAP)Quick Start
description: Verwenden Sie den Schnellstart der LiveCycleProcess-Java-API (SOAP), um nach Prozessinstanzen zu suchen, Prozessinstanzen auszusetzen, ausgesetzte Prozessinstanzen zu starten, Prozessinstanzen zu beenden, Prozessdaten zu bereinigen und den Status eines Vorgangs abzurufen.
seo-description: Use the LiveCycleProcess Java API (SOAP) Quick Start to search for process instances, suspend process instances, start suspended process instances, terminate process instances, purge process data, and retrieve the status of a job.
uuid: ad14fb50-8dd5-44e0-9e48-f0f0334e04d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 9c17fa2d-0337-4204-822e-dcdafebf0e4d
role: Developer
exl-id: ee8f5f16-218a-41eb-be42-fda4537b2b4e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 93%

---

# Schnellstart für die LiveCycleProcess-Java-API (SOAP) {#livecycleprocess-java-api-soap-quick-start}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Schnellstart für die Java-API (SOAP) ist für Prozesse verfügbar. Eine *Prozessinstanz* ist ein Auftreten eines bestimmten Prozesses, der von einer Aufrufmethode wie der Aufruf-API oder aus dem Arbeitsbereich heraus gestartet wurde.

[Schnellstart (SOAP-Modus): Suchen nach Prozessinstanzen unter Verwendung der Java-API](livecycleprocess-java-api-soap-quick.md#quick-start-soap-mode-searching-for-process-instances-using-the-java-api)

[Schnellstart (SOAP-Modus): Aussetzen von Prozessinstanzen unter Verwendung der Java-API](livecycleprocess-java-api-soap-quick.md#quick-start-soap-mode-suspending-process-instances-using-the-java-api)

[Schnellstart (SOAP-Modus): Starten von ausgesetzten Prozessinstanzen unter Verwendung der Java-API](livecycleprocess-java-api-soap-quick.md#quick-start-soap-mode-starting-suspended-process-instances-using-the-java-api)

[Schnellstart (SOAP-Modus): Beenden von Prozessinstanzen unter Verwendung der Java-API](livecycleprocess-java-api-soap-quick.md#quick-start-soap-mode-terminating-process-instances-using-the-java-api)

[Schnellstart (SOAP-Modus): Bereinigen von Prozessdaten unter Verwendung der Java-API](livecycleprocess-java-api-soap-quick.md#quick-start-soap-mode-purging-process-data-using-the-java-api)

[Schnellstart (SOAP-Modus): Abrufen des Status eines Auftrags unter Verwendung der Java-API](livecycleprocess-java-api-soap-quick.md#quick-start-soap-mode-retrieving-the-status-of-a-job-using-the-java-api)

AEM Forms-Vorgänge können mit der stark typisierten AEM Forms-API durchgeführt werden und der Verbindungsmodus sollte auf SOAP eingestellt werden.

>[!NOTE]
>
>Schnellstarts, die unter „Programmieren mit AEM Forms“ zu finden sind, basieren auf Forms. Wenn Sie ein anderes Betriebssystem wie Unix verwenden, ersetzen Sie Windows-spezifische Pfade durch Pfade, die vom jeweiligen Betriebssystem unterstützt werden. Wenn Sie einen anderen J2EE-Anwendungsserver verwenden, stellen Sie sicher, dass Sie gültige Verbindungseigenschaften angeben. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

## Schnellstart (SOAP-Modus): Suchen nach Prozessinstanzen unter Verwendung der Java-API {#quick-start-soap-mode-searching-for-process-instances-using-the-java-api}

Im folgenden Java-Code-Beispiel wird nach Prozessinstanzen gesucht, die auf dem Prozess *Hypothekendarlehen – vorkonfiguriert* beruhen.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP  mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
     * 20. adobe-workflow-client-sdk.jar 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.taskmanager.dsc.client.TaskManagerClientFactory; 
 import com.adobe.idp.taskmanager.dsc.client.TaskManagerQueryService; 
 import com.adobe.idp.taskmanager.dsc.client.query.ProcessInstanceRow; 
 import com.adobe.idp.taskmanager.dsc.client.query.ProcessSearchFilter; 
 import com.adobe.idp.workflow.client.ProcessManager; 
  
 /** 
     * This Java Quick Start searches for all completed processes that are based on the application 
     * and tracks the time at which the processes where completed.   
     * 
     */ 
 public class SearchingProcesses { 
      
     public static void main(String[] args) { 
         try{ 
          
             //Set connection properties required to invoke AEM Forms 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
             TaskManagerQueryService queryProcess = TaskManagerClientFactory.getQueryManager(myFactory); 
              
             ProcessSearchFilter processFilter = new ProcessSearchFilter();  
             processFilter.setServiceName("MortgageLoan - Prebuilt"); 
              
             List allProcesses = queryProcess.processSearch(processFilter); 
                              
             //Create an Iterator object and iterate through 
 //             the List object 
            Iterator iter = allProcesses.iterator(); 
            int i = 0 ; 
            long processId=0 ;  
            while (iter.hasNext()) { 
                ProcessInstanceRow processInstance = (ProcessInstanceRow)iter.next(); 
          
           if (processInstance.getProcessInstanceStatus() == ProcessInstanceRow.STATUS_RUNNING){ 
              
             //Display the process d 
             processId = processInstance.getProcessInstanceId();   
             System.out.println("The process identifier is " +processId); 
           } 
               
             i++; 
            } 
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
      
      
      
  
 } 
 
```

## Schnellstart (SOAP-Modus): Aussetzen von Prozessinstanzen unter Verwendung der Java-API {#quick-start-soap-mode-suspending-process-instances-using-the-java-api}

Im folgenden Java-Code-Beispiel wird eine Prozessinstanz ausgesetzt. Um eine Prozessinstanz erfolgreich aussetzen zu können, benötigen Sie die Prozessaufruf-Kennung, die beim Aufrufen eines langlaufenden Prozesses mithilfe der Aufruf-API abgerufen werden kann.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
     * 20. adobe-workflow-client-sdk.jar 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.um.api.infomodel.PrincipalSearchFilter; 
 import com.adobe.idp.workflow.client.ProcessManager; 
  
  
 public class SuspendProcesses { 
  
      
     public static void main(String[] args) { 
          try{ 
              
                  //Set connection properties required to invoke AEM Forms 
                 Properties connectionProps = new Properties(); 
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue"); 
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                  
                   //Create a ServiceClientFactory object 
                    ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
                    //Create a ProcessManager object 
                    ProcessManager myProcessManager = new ProcessManager(myFactory); 
                    myProcessManager.suspendProcess("1");    
              } 
                catch(Exception e) 
                 { 
                       e.printStackTrace(); 
                } 
  
  
  
     } 
  
 } 
  
 
```

## Schnellstart (SOAP-Modus): Starten von ausgesetzten Prozessinstanzen unter Verwendung der Java-API {#quick-start-soap-mode-starting-suspended-process-instances-using-the-java-api}

Im folgenden Java-Code-Beispiel wird eine ausgesetzte Prozessinstanz gestartet.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
     * 20. adobe-workflow-client-sdk.jar 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
  
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.workflow.client.ProcessManager; 
  
 public class StartProcess { 
      
     public static void main(String[] args) { 
         try{ 
          
             //Set connection properties required to invoke AEM Forms 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a ProcessManager object 
             ProcessManager myProcessManager = new ProcessManager(myFactory); 
              
             //Start a suspended process instance         
              myProcessManager.unSuspendProcess("5fae07190a242fb1010b2229ccad8a7e");      
             } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## Schnellstart (SOAP-Modus): Beenden von Prozessinstanzen unter Verwendung der Java-API {#quick-start-soap-mode-terminating-process-instances-using-the-java-api}

Im folgenden Java-Code-Beispiel wird eine Prozessinstanz mit dem Kennungswert 756c22860a242fb101ec7a5bc0977fd6 beendet.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
     * 20. adobe-workflow-client-sdk.jar 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
  
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.workflow.client.ProcessManager; 
  
 public class TerminatingProcesses { 
      
     public static void main(String[] args) { 
         try{ 
          
             //Set connection properties required to invoke AEM Forms 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a ProcessManager object 
             ProcessManager myProcessManager = new ProcessManager(myFactory); 
              
              
             myProcessManager.terminateProcess("sd"); 
             //Terminate a process instance         
         //       myProcessManager.terminateProcess("756c22860a242fb101ec7a5bc0977fd6");      
             } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## Schnellstart (SOAP-Modus): Bereinigen von Prozessdaten unter Verwendung der Java-API {#quick-start-soap-mode-purging-process-data-using-the-java-api}

Der folgende Java-Code löscht Daten aus einem Prozess mit dem Namen *SecureDocument*. Es wird ein Filter verwendet, der angibt, Daten für die Prozessinstanzen zu bereinigen, in denen die Prozessvariable namens *inValue* größer als 200 ist.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
  
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.workflow.client.ProcessManager; 
 import com.adobe.idp.workflow.dsc.type.*; 
  
 public class PurgeProcess 
 { 
      public static void main(String[] args)  
        { 
           try 
            { 
              //Set connection properties required to invoke AEM Forms                                                                                                                        
              Properties connectionProps = new Properties(); 
              connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
              connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
              connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
              connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
  
              //Create a ServiceClientFactory instance 
              ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
      
            //Create a ProcessManager object 
           ProcessManager myProcessManager = new ProcessManager(myFactory); 
  
           //Prepare parameters to use in the purge operation 
              long age = 10;  // in seconds 
              boolean includeChildren = false;// don't include children by default 
              int status = 3;   // both completed and terminated by default 
              short minor = 0; 
              short major = 1;  
      
             //Create the conditionFilter object to filter 
             //out unwanted instances of the process 
             ConditionFilter filter = new ConditionFilter("inValue", ConditionEnum.GREATER_THAN, "200"); 
      
             //Delete process instances that contain a process  
             //variable named inValue whose value 
             //is greater than 200 
             myProcessManager.purgeProcess( 
               "SecureDocument", 
               major,  
               minor,  
               status,  
               age, 
               filter, 
               includeChildren); 
       } 
     catch (Exception e)  
             { 
               e.printStackTrace(); 
              } 
         } 
 } 
 
```

## Schnellstart (SOAP-Modus): Abrufen des Status eines Auftrags unter Verwendung der Java-API {#quick-start-soap-mode-retrieving-the-status-of-a-job-using-the-java-api}

Im folgenden Codebeispiel wird der Status von 10 AEM Forms-Vorgängen abgerufen.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-encryption-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
  
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.jobmanager.client.JobManager; 
 import com.adobe.idp.jobmanager.common.JobInstance; 
 import com.adobe.idp.jobmanager.common.JobInstanceFilter; 
  
  
 public class SearchForJobs { 
  
     public static void main(String[] args) { 
          
     //This function will upload a ceritificate to AEM Forms trust store 
       try{ 
          
         //Set connection properties required to invoke AEM Forms                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
         JobManager jobManager= new JobManager(myFactory); 
          
         //Specify filter criteria 
         JobInstanceFilter jobFilter = new JobInstanceFilter();  
         jobFilter.setMaxObjects(10); 
                                  
         //Retrieve the first 10 jobs 
         List<JobInstance> allJobs = jobManager.getJobInstances(jobFilter); 
          
         //Create an Iterator object and iterate through  
         //the List object 
         Iterator iter = allJobs.iterator();  
         int i = 0 ;  
         while (iter.hasNext()) {  
             JobInstance JobInstance = (JobInstance)iter.next();  
             System.out.println("The status of the job is " +JobInstance.getStatus() +". The identifier value of the job is " +JobInstance.getId()+ ". The service on which the job is based is " +JobInstance.getServiceName()); 
             i++;  
         } 
      
       }catch (Exception e) { 
              e.printStackTrace(); 
             }         
      
     } 
 } 
  
 
```
