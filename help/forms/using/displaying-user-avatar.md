---
title: Anzeigen des Benutzeravatars
seo-title: Displaying the user avatar
description: So passen Sie den AEM Forms-Arbeitsbereich an, um das Bild eines angemeldeten Benutzers anzuzeigen.
seo-description: How to customize the AEM Forms workspace to display the image of a logged-in user.
uuid: 2961dc93-f0d0-4842-80f1-3c239a20e348
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: aec03ea5-17a6-4775-92cb-2ad361895fdf
exl-id: 2bc70cd6-1ea6-4594-9b42-ab3d3000a0c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 56%

---

# Anzeigen des Benutzeravatars {#displaying-the-user-avatar}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Avatar des angemeldeten Benutzers wird in der oberen rechten Ecke von AEM Forms Workspace angezeigt. Außerdem werden die Avatare der direkt unterstellten Mitarbeiter in der hierarchischen Struktur in der Manageransicht angezeigt. Sie können AEM Forms Workspace so konfigurieren, dass die Benutzerbilder aus Ihrer Datenbank, z. B. vom LDAP-Server, abgerufen werden.

>[!NOTE]
>
>Für Benutzerbilder wird nur das Seitenverhältnis 1:1 unterstützt.

1. Erstellen Sie ein DSC mithilfe der Informationen, die im nächsten Schritt angegeben werden. Weitere Informationen erhalten Sie unter „Entwickeln von Komponenten für AEM Forms“ im Handbuch [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).
1. Definieren Sie im DSC eine neue SPI, die mithilfe der Methoden getCurrentUserImageUrl und getUserImageUrl eine Bild-URL für einen AEM Forms-Benutzer abruft. Im Folgenden finden Sie ein Beispiel für ein Java™-Codefragment:

   ```as3
   public class DemoUserImageURLProviderService { 
     public String getCurrentUserImageUrl() 
     { 
        // return the URL for profile Image of logged in user 
     } 
     public String getUserImageUrl(String principalOid) 
     { 
         // return the URL for profile Image for user represented by this principal Oid 
      } 
   }
   ```

1. Erstellen Sie eine Datei &quot;component.xml&quot;. Stellen Sie sicher, dass spec-id wie im Code-Snippet unten gezeigt ist.

   Das folgende Codefragment ist ein Beispiel. Passen Sie es an Ihre spezifischen Anforderungen an.

   ```as3
   <component xmlns="https://adobe.com/idp/dsc/component/document"> 
       <component-id>com.adobe.sample.DemoUsersComponent</component-id> 
       <version>1.1</version> 
       <supports-export>false</supports-export> 
       <descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class> 
       <services> 
           <service name="DemoUserImageURLProviderService" title="Demo User ImageURL provider service" orchestrateable="false"> 
           <auto-deploy service-id="DemoUserImageURLProviderService" category-id="Demo Users Component DSC" major-version="1" minor-version="0" /> 
           <description>Service for resolving user image url.</description> 
            <specifications> 
            <specification spec-id="com.adobe.idp.taskmanager.dsc.enterprise.UserImageUrlProvider"/> 
            </specifications> 
           <specification-version>1.0</specification-version> 
           <implementation-class>com.adobe.sample.demousers.DemoUserImageURLProviderService</implementation-class> 
           <request-processing-strategy>single_instance</request-processing-strategy> 
           <supported-connectors>default</supported-connectors> 
           <operation-config> 
               <operation-name>*</operation-name> 
               <transaction-type>Container</transaction-type> 
               <transaction-propagation>supports</transaction-propagation> 
               <!--transaction-timeout>3000</transaction-timeout--> 
           </operation-config> 
           <operations> 
               <operation anonymous-access="false" name="getCurrentUserImageUrl" method="getCurrentUserImageUrl"> 
                   <output-parameter name="result" type="java.lang.String"/> 
               </operation> 
               <operation anonymous-access="false" name="getUserImageUrl" 
   method="getUserImageUrl"> 
               <input-parameter name="principalOid" type="java.lang.String"/> 
               <output-parameter name="result" type="java.lang.String"/> 
               </operation> 
           </operations> 
           </service> 
       </services>
   </component>
   ```

1. Stellen Sie DSC über Workbench bereit. Starten Sie den Service `ProcessManagementClientSessionService` neu.
1. Möglicherweise müssen Sie den Browser aktualisieren oder sich für den Benutzer erneut abmelden/anmelden.
