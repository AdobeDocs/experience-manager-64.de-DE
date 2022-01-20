---
title: Verwalten von Aufgaben in einer hierarchischen Struktur mithilfe der Manageransicht
seo-title: Managing tasks in an organizational hierarchy using Manager View
description: Wie Manager und Unternehmensleitungen auf die Aufgaben ihrer direkt oder indirekt unterstellten Mitarbeiter in der Registerkarte „Aufgaben“ in AEM Forms Workspace zugreifen und sie verwenden können.
seo-description: How managers and organization heads can access and work on the tasks of their direct and indirect reports in the To-do tab in AEM Forms workspace.
uuid: a44d5a64-c03a-4337-8577-b121e6202449
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c7cf28bf-2806-47bc-a803-8bc0e803fc4d
exl-id: 28877528-2f91-4ee0-b9d8-c7df364ed803
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 77%

---

# Verwalten von Aufgaben in einer hierarchischen Struktur mithilfe der Manageransicht {#managing-tasks-in-an-organizational-hierarchy-using-manager-view}

In AEM Forms Workspace können Manager jetzt auf die Aufgaben zugreifen, die Benutzern in ihren Hierarchien – direkt oder indirekt unterstellten Mitarbeitern – zugewiesen sind, und dafür verschiedene Aktionen ausführen. Die Aufgaben sind in AEM Forms Workspace auf der Registerkarte „Aufgaben“ verfügbar. Die folgenden Aktionen werden für die Aufgaben direkt unterstellter Mitarbeiter unterstützt:

**Weiterleiten** Leitet eine Aufgabe aus einem direkten Bericht an einen beliebigen Benutzer weiter.

**Anspruch** Fordert eine Aufgabe eines direkt unterstellten Mitarbeiters an.

**Anfordern und Öffnen** Fordert eine Aufgabe eines direkt unterstellten Mitarbeiters an und öffnet sie automatisch in der Aufgabenliste des Managers.

**Ablehnen** Lehnen Sie eine Aufgabe ab, die von einem anderen Benutzer an einen direkt unterstellten Mitarbeiter weitergeleitet wurde. Diese Option ist für die Aufgaben verfügbar, die von anderen Benutzern an einen direkt unterstellten Mitarbeiter weitergeleitet wurden.

AEM Forms beschränkt den Zugriff eines Benutzers auf die Aufgaben, für die der Benutzer die Zugriffskontrolle (ACL) hat. Durch diese Überprüfung wird sichergestellt, dass ein Benutzer nur die Aufgaben abrufen kann, für die er Zugriffsberechtigungen hat. Eine Organisation kann die Hierarchie mit Webdiensten von Drittanbietern definieren und die Definition von Managern und direkt unterstellten Mitarbeitern an ihren Bedarf anpassen.

1. Erstellen Sie ein DSC. Weitere Informationen finden Sie unter &quot;Entwickeln von Komponenten für AEM Forms&quot;in [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63) Handbuch.
1. Definieren Sie in dem DSC eine neue SPI für das Hierarchiemanagement, um direkt unterstellte Mitarbeiter und Hierarchie unter den AEM Forms-Benutzern zu definieren. Im Folgenden finden Sie ein Java™-Beispielcodefragment.

   ```as3
   public class MyHierarchyMgmtService 
   { 
        /*
       Input : Principal Oid for a livecycle user
       Output : Returns true when the user is either the service invoker OR his direct/indirect report.
       */
       boolean isInHierarchy(String principalOid) {
   
       }
   
       /* 
       Input : Principal Oid for a livecycle user
       Output : List of principal Oids for direct reports of the livecycle user
       A user may get direct reports only for himself OR his direct/indirect reports.
       So the API is functionally equivalent to - 
       isInHierarchy(principalOid) ? <return direct reports> : <return empty list>
       */
       List<String> getDirectReports(String principalOid) {
   
       }
   
       /* 
       Returns whether a livecycle user has direct reports or not.
       It's functionally equivalent to -
       getDirectReports(principalOid).size()>0
       */
       boolean isManager(String principalOid) {
   
       }  
   }
   ```

1. Erstellen Sie die Datei component.xml. Stellen Sie sicher, dass spec-id mit dem unten angegebenen Codefragment bereinstimmt. Im Folgenden finden Sie ein Beispielcodefragment, das Sie für Ihre Zwecke anpassen können.

   ```as3
   <component xmlns="https://adobe.com/idp/dsc/component/document"> 
       <component-id>com.adobe.sample.SampleDSC</component-id> 
       <version>1.1</version> 
       <supports-export>false</supports-export> 
         <descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class> 
         <services> 
           <service name="MyHierarchyMgmtService" title="My hierarchy management service" orchestrateable="false"> 
           <auto-deploy service-id="MyHierarchyMgmtService" category-id="Sample DSC" major-version="1" minor-version="0" /> 
           <description>Service for resolving hierarchy management.</description> 
            <specifications> 
            <specification spec-id="com.adobe.idp.taskmanager.dsc.enterprise.HierarchyManagementProvider"/> 
            </specifications> 
           <specification-version>1.0</specification-version> 
           <implementation-class>com.adobe.sample.hierarchymanagement.MyHierarchyMgmtService</implementation-class> 
           <request-processing-strategy>single_instance</request-processing-strategy> 
           <supported-connectors>default</supported-connectors> 
           <operation-config> 
               <operation-name>*</operation-name> 
               <transaction-type>Container</transaction-type> 
               <transaction-propagation>supports</transaction-propagation> 
               <!--transaction-timeout>3000</transaction-timeout--> 
           </operation-config> 
           <operations> 
               <operation anonymous-access="true" name="isInHierarchy" method="isInHierarchy"> 
                   <input-parameter name="principalOid" type="java.lang.String" /> 
                   <output-parameter name="result" type="java.lang.Boolean"/> 
               </operation> 
               <operation anonymous-access="true" name="getDirectReports" method="getDirectReports"> 
                   <input-parameter name="principalOid" type="java.lang.String" /> 
                   <output-parameter name="result" type="java.util.List"/> 
               </operation> 
               <operation anonymous-access="true" name="isManager" method="isManager"> 
                   <input-parameter name="principalOid" type="java.lang.String" /> 
                   <output-parameter name="result" type="java.lang.Boolean"/> 
               </operation> 
               </operations> 
               </service> 
         </services>
   </component>
   ```

1. Stellen Sie das DSC über Workbench bereit. Neu starten `ProcessManagementTeamTasksService` Dienst.
1. Möglicherweise müssen Sie den Browser aktualisieren oder sich für den Benutzer erneut abmelden/anmelden.

Der folgende Bildschirm veranschaulicht den Zugriff auf die Aufgaben direkt unterstellter Mitarbeiter und die verfügbaren Aktionen.

![cu_manager_view](assets/cu_manager_view.png)

Zugreifen auf Aufgaben direkt unterstellter Mitarbeiter und Ausführen von Aktionen für die Aufgaben
