---
title: Wählen Sie dynamisch einen Benutzer oder eine Gruppe für AEM Forms-zentrierte Workflow-Schritte aus.
seo-title: Dynamically select a user or group for AEM Forms-centric workflow steps
description: Erfahren Sie, wie Sie zur Laufzeit einen Benutzer oder eine Gruppe für einen AEM Forms-Arbeitsablauf auswählen.
seo-description: Learn how to select a user or group for an AEM Forms workflow at the runtime.
uuid: 19dcbda4-61af-40b3-b10b-68a341373410
content-type: troubleshooting
topic-tags: publish
discoiquuid: e6c9f3bb-8f20-4889-86f4-d30578fb1c51
exl-id: c63e6e5c-c4c9-45b8-8401-87ee37a30c97
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 40%

---

# Dynamische Auswahl eines Benutzers order einer Gruppe für AEM Forms-zentrierte Workflow-Schritte {#dynamically-select-a-user-or-group-for-aem-forms-centric-workflow-steps}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erfahren Sie, wie Sie zur Laufzeit einen Benutzer oder eine Gruppe für einen AEM Forms-Arbeitsablauf auswählen.

In großen Unternehmen müssen Benutzer für einen Prozess dynamisch ausgewählt werden. Wählen Sie beispielsweise einen Feldagenten aus, um einen Kunden basierend auf der Nähe des Agenten zum Kunden zu bedienen. In einem solchen Szenario wird der Agent dynamisch ausgewählt.

Zuweisen von Aufgaben und Acrobat Sign-Schritten von [Forms-orientierte Workflows in OSGi](/help/forms/using/aem-forms-workflow.md) bietet Optionen zur dynamischen Auswahl eines Benutzers. Sie können ECMAScript oder OSGi-Bundles verwenden, um einen Verantwortlichen für den Schritt „Aufgabe zuweisen“ oder Unterzeichner für den Schritt „Dokument signieren“ dynamisch auszuwählen.

## Verwenden von ECMAScript zur dynamischen Auswahl eines Benutzers oder einer Gruppe {#use-ecmascript-to-dynamically-select-a-user-or-group}

ECMAScript ist eine Skriptsprache. Sie wird für die Client-seitige Skripterstellung und Server-Anwendungen verwendet. Führen Sie die folgenden Schritte aus, um einen Benutzer oder eine Gruppe mit ECMAScript dynamisch auszuwählen:

1. Öffnen Sie CRXDE Lite. Die URL lautet `https://[server]:[port]/crx/de/index.jsp`.
1. Erstellen Sie eine Datei mit der Erweiterung .ecma unter folgendem Pfad. Wenn der Pfad (Knotenstruktur) nicht vorhanden ist, erstellen Sie ihn:

   * (Pfad für Schritt „Aufgabe zuweisen“) `/apps/fd/dashboard/scripts/participantChooser`
   * (Pfad für Signaturschritt) `/apps/fd/workflow/scripts/adobesign`

1. Fügen Sie der .ecma-Datei ECMAScript hinzu, das die Logik zur dynamischen Auswahl eines Benutzers hat. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   Beispielskripte finden Sie unter [Beispiele für ECMAScripts zur dynamischen Auswahl eines Benutzers oder einer Gruppe](/help/forms/using/dynamically-select-a-user-or-group-for-aem-workflow.md#sample-ecmascripts-to-dynamically-choose-a-user-or-a-group).

1. Fügen Sie den Anzeigenamen des Skripts hinzu. Dieser Name wird in den Workflow-Schritten angezeigt. Eingeben des Namens:

   1. Erweitern Sie den Skriptknoten, klicken Sie mit der rechten Maustaste auf den Knoten **[!UICONTROL jcr:content]** und dann auf **[!UICONTROL Mixins]**.
   1. Fügen Sie die Eigenschaft `mix:title` im Dialogfeld „Mixins bearbeiten“ hinzu und klicken Sie auf **OK**.
   1. Fügen Sie folgende Eigenschaft zum Knoten „jcr:content“ des Skripts hinzu:

      | Name | Typ | Wert |
      |--- |--- |--- |
      | jcr:title | Zeichenfolge | Geben Sie den Namen des Skripts an. Wählen Sie beispielsweise den nächsten Feldagenten aus. Dieser Name wird in den Schritten &quot;Aufgabe zuweisen&quot;und &quot;Dokument unterschreiben&quot;angezeigt. |

   1. Klicken Sie auf **Alle speichern**. Das Skript ist nun zur Auswahl in den Komponenten des AEM-Workflows verfügbar.

      ![script](assets/script.png)

### Beispiele für ECMAScripts zum dynamischen Auswählen eines Benutzers oder einer Gruppe {#sample-ecmascripts-to-dynamically-choose-a-user-or-a-group}

Im folgenden Beispiel wählt ECMAScript dynamisch einen Verantwortlichen für den Schritt &quot;Aufgabe zuweisen&quot;aus. In diesem Skript wird ein Benutzer basierend auf dem Pfad der Payload ausgewählt. Bevor Sie dieses Skript verwenden, stellen Sie sicher, dass alle im Skript erwähnten Benutzer in AEM vorhanden sind. Wenn die im Skript genannten Benutzer nicht in AEM vorhanden sind, kann der zugehörige Prozess fehlschlagen.

```
function getParticipant() {

var workflowData = graniteWorkItem.getWorkflowData();

if (workflowData.getPayloadType() == "JCR_PATH") { 

var path = workflowData.getPayload().toString(); 
     if (path.indexOf("/content/geometrixx/en") == 0) {
    return "user1";
    } 
   else {
              return "user2";
            }
}
}
```

Im folgenden Beispiel wählt ECMAScript dynamisch einen Verantwortlichen für den Acrobat Sign-Schritt aus. Bevor Sie das unten stehende Skript verwenden, stellen Sie sicher, dass die im Skript erwähnten Benutzerinformationen (E-Mail-Adressen und Telefonnummern) korrekt sind. Wenn die im Skript erwähnten Benutzerinformationen falsch sind, kann der zugehörige Prozess fehlschlagen.

>[!NOTE]
>
>Bei Verwendung von ECMAScript für Acrobat Sign muss sich das Skript im crx-Repository unter /apps/fd/workflow/scripts/adobesign/ befinden und sollte über eine Funktion namens getAdobeSignRecipients verfügen, um eine Benutzerliste zurückzugeben.

```
function getAdobeSignRecipients() {

    var recipientSetInfos = new Packages.java.util.ArrayList();

    var recipientInfoSet = new com.adobe.aem.adobesign.recipient.RecipientSetInfo();
    var recipientInfoList = new Packages.java.util.ArrayList();
    var recipientInfo = new com.adobe.aem.adobesign.recipient.RecipientInfo();

    var email;
    var recipientAuthenticationMethod = com.adobe.aem.adobesign.recipient.RecipientAuthenticationMethod.PHONE;  
    //var recipientAuthenticationMethod = com.adobe.aem.adobesign.recipient.RecipientAuthenticationMethod.NONE;
    var securityOptions = null;

    var phoneNumber = "123456789";
    var countryCode = "+1";
    var recipientPhoneInfo = new Array();
    recipientPhoneInfo.push(new com.adobe.aem.adobesign.recipient.RecipientPhoneInfo(phoneNumber, countryCode));

     securityOptions = new com.adobe.aem.adobesign.recipient.RecipientSecurityOption(recipientAuthenticationMethod, recipientPhoneInfo , null);
    
    email = "example@example.com";
    
    recipientInfo.setEmail(email);
    recipientInfo.setSecurityOptions(securityOptions);
    
    recipientInfoList.add(recipientInfo);
    recipientInfoSet.setMemberInfos(recipientInfoList);
    recipientSetInfos.add(recipientInfoSet);

    return recipientSetInfos;

}
```

## Verwenden der Java-Schnittstelle zum dynamischen Auswählen eines Benutzers oder eine Gruppe {#use-java-interface-to-dynamically-choose-a-user-or-group}

Sie können die [RecipientInfoSpecifier](https://helpx.adobe.com/de/experience-manager/6-4/forms/javadocs/com/adobe/fd/workflow/adobesign/api/RecipientInfoSpecifier.html) Java-Schnittstelle zur dynamischen Auswahl eines Benutzers oder einer Gruppe für die Schritte &quot;Acrobat Sign&quot;und &quot;Aufgabe zuweisen&quot;. Sie können ein OSGi-Bundle erstellen, das die Java-Schnittstelle [RecipientInfoSpecifier](https://helpx.adobe.com/de/experience-manager/6-4/forms/javadocs/com/adobe/fd/workflow/adobesign/api/RecipientInfoSpecifier.html) verwendet, und es auf dem AEM Forms-Server bereitstellen. Dadurch wird die Option zur Auswahl in den Komponenten &quot;Aufgabe zuweisen&quot;und &quot;Acrobat Sign&quot;AEM Workflows verfügbar.

Sie benötigen die Dateien [AEM Forms Client SDK](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html)-JAR und [granite-JAR](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.workflow.api/1.0.2/), um die unten aufgeführten Codebeispiele zu kompilieren. Fügen Sie diese JAR-Dateien als externe Abhängigkeiten zum OSGi-Bundle-Projekt hinzu. Sie können eine beliebige Java IDE verwenden, um ein OSGi-Bundle zu erstellen. Im folgenden Verfahren wird beschrieben, wie Sie mit Eclipse ein OSGi-Bundle erstellen:

1. Öffnen Sie Eclipse IDE. Navigieren Sie zu **[!UICONTROL Datei]** > **[!UICONTROL Neues Projekt]**.
1. Wählen Sie im Bildschirm &quot;Assistenten auswählen&quot;die Option **[!UICONTROL Maven-Projekt]** und klicken Sie auf **[!UICONTROL Nächste]**.
1. Behalten Sie im neuen Maven-Projekt die Standardeinstellungen bei und klicken Sie auf **[!UICONTROL Nächste]**. Wählen Sie einen Archetyp aus und klicken Sie auf **[!UICONTROL Nächste]**. Beispiel: maven-archetype-quickstart. Geben Sie **[!UICONTROL Group Id]**, **[!UICONTROL Artifact ID]**, **[!UICONTROL Version]** und **[!UICONTROL Paket]** für das Projekt an und klicken Sie auf **[!UICONTROL Beenden]**. Das Projekt wird erstellt.
1. Öffnen Sie die Datei &quot;pom.xml&quot;zur Bearbeitung und ersetzen Sie den gesamten Inhalt der Datei durch den folgenden Text:

   ```xml
   <project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
       <modelVersion>4.0.0</modelVersion>
   
       <groupId>getAgent</groupId>
       <artifactId>assignToAgent</artifactId>
       <version>1.0</version>
       <packaging>bundle</packaging><!-- packaging type bundle is must -->
   
       <name>assignToAgent</name>
       <url>https://maven.apache.org</url>
       <repositories>
           <repository>
               <id>adobe</id>
               <name>Adobe Public Repository</name>
               <url>https://repo.adobe.com/nexus/content/groups/public/</url>
               <layout>default</layout>
           </repository>
       </repositories>
       <pluginRepositories>
           <pluginRepository>
               <id>adobe</id>
               <name>Adobe Public Repository</name>
               <url>https://repo.adobe.com/nexus/content/groups/public/</url>
               <layout>default</layout>
           </pluginRepository>
       </pluginRepositories>
   
       <dependencies>
           <dependency>
               <groupId>com.adobe.aemfd</groupId>
               <artifactId>aemfd-client-sdk</artifactId>
               <version>5.1.100</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.granite</groupId>
               <artifactId>com.adobe.granite.workflow.api</artifactId>
               <version>1.0.0</version>
           </dependency>
   
           <dependency>
               <groupId>org.osgi</groupId>
               <artifactId>org.osgi.core</artifactId>
               <version>4.2.0</version>
               <scope>provided</scope>
           </dependency>
   
           <dependency>
               <groupId>org.apache.felix</groupId>
               <artifactId>org.apache.felix.scr.annotations</artifactId>
               <version>1.7.0</version>
   
           </dependency>
   
           <dependency>
               <groupId>org.apache.sling</groupId>
               <artifactId>org.apache.sling.api</artifactId>
               <version>2.2.0</version>
   
           </dependency>
   
       </dependencies>
   
       <!-- ====================================================================== -->
       <!-- B U I L D D E F I N I T I O N -->
       <!-- ====================================================================== -->
       <build>
           <plugins>
   
               <plugin>
                   <groupId>org.apache.felix</groupId>
                   <artifactId>maven-bundle-plugin</artifactId>
                   <extensions>true</extensions>
                   <configuration>
                       <instructions>
                           <Bundle-SymbolicName>com.aem.assigntoAgent-bundle</Bundle-SymbolicName>
                       </instructions>
                   </configuration>
               </plugin>
   
               <plugin>
                   <groupId>org.apache.felix</groupId>
                   <artifactId>maven-scr-plugin</artifactId>
                   <version>1.9.0</version>
                   <executions>
                       <execution>
                           <id>generate-scr-descriptor</id>
                           <goals>
                               <goal>scr</goal>
                           </goals>
                       </execution>
                   </executions>
               </plugin>
           </plugins>
       </build>
   
   </project>
   ```

1. Fügen Sie Quell-Code hinzu, der die Java-Schnittstelle [RecipientInfoSpecifier](https://helpx.adobe.com/de/experience-manager/6-4/forms/javadocs/com/adobe/fd/workflow/adobesign/api/RecipientInfoSpecifier.html) verwendet, um einen Benutzer oder eine Gruppe für den Schritt „Aufgabe zuweisen“ dynamisch zuzuweisen. Unter [Beispiel für die dynamische Auswahl eines Benutzers oder einer Gruppe mithilfe einer Java-Schnittstelle](#-sample-scripts-for) finden Sie einen Beispiel-Code.
1. Öffnen Sie eine Eingabeaufforderung und navigieren Sie zum Ordner, der das OSGi-Bundle-Projekt enthält. Verwenden Sie den folgenden Befehl, um das OSGi-Bundle zu erstellen:

   `mvn clean install`

1. Laden Sie das Bundle auf einen AEM Forms-Server hoch. Sie können AEM Package Manager verwenden, um das Bundle auf den AEM Forms-Server zu importieren.

Nachdem das Bundle importiert wurde, wird die Option zur Auswahl der Java-Schnittstelle für die dynamische Auswahl eines Benutzers oder einer Gruppe in für die Schritte Acrobat Sign und Assign Task verfügbar.

### Beispiele für Java-Code zum dynamischen Auswählen eines Benutzers oder einer Gruppe {#sample-java-code-to-dynamically-choose-a-user-or-a-group}

Im folgenden Beispielcode wird dynamisch ein Verantwortlicher für den Acrobat Sign-Schritt ausgewählt. Sie verwenden den Code in einem OSGi-Bundle. Bevor Sie den unten aufgeführten Code verwenden, stellen Sie sicher, dass die im Code erwähnten Benutzerinformationen (E-Mail-Adressen und Telefonnummern) korrekt sind. Wenn die im Code erwähnten Benutzerinformationen falsch sind, kann der zugehörige Prozess fehlschlagen.

```java
/*************************************************************************

 *
 * ADOBE CONFIDENTIAL
 * __________________
 *
 * Copyright 2016 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
 
package com.aem.impl;

import java.util.ArrayList;
import java.util.List;

import com.adobe.aem.adobesign.recipient.RecipientAuthenticationMethod;
import com.adobe.aem.adobesign.recipient.RecipientInfo;
import com.adobe.aem.adobesign.recipient.RecipientPhoneInfo;
import com.adobe.aem.adobesign.recipient.RecipientSecurityOption;
import com.adobe.aem.adobesign.recipient.RecipientSetInfo;
import com.adobe.fd.workflow.adobesign.api.RecipientInfoSpecifier;
import com.adobe.granite.workflow.WorkflowException;
import com.adobe.granite.workflow.WorkflowSession;
import com.adobe.granite.workflow.exec.WorkItem;
import com.adobe.granite.workflow.metadata.MetaDataMap;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

/**
 * <code>DummyRecipientInfoSpecifier implementation. A sample code to write implementation of RecipientInfoSpecifier to choose recipients/code>...
 */
@Service

@Component(metatype = false)
public class DummyRecipientChoser implements RecipientInfoSpecifier {
    public List<RecipientSetInfo> getAdobeSignRecipients(WorkItem workItem, WorkflowSession workflowSession, MetaDataMap args) throws WorkflowException {

        List<RecipientSetInfo> recipientSetInfos = new ArrayList<RecipientSetInfo>();

                //First Recipient

                RecipientSetInfo recipientInfoSet1 = new RecipientSetInfo();
                List<RecipientInfo> recipientInfoList = new ArrayList<RecipientInfo>();
                RecipientInfo recipientInfo1 = new RecipientInfo();//Member to first recipient

                String email;

                RecipientAuthenticationMethod recipientAuthenticationMethod = RecipientAuthenticationMethod.WEB_IDENTITY;
                RecipientSecurityOption securityOptions = null;

                String phoneNumber = "123456789";
                String countryCode = "+1";
                RecipientPhoneInfo[] recipientPhoneInfo = new RecipientPhoneInfo[1];  //if multiple phone numbers, size>1
                recipientPhoneInfo[0] = new RecipientPhoneInfo(phoneNumber, countryCode);
                securityOptions = new RecipientSecurityOption(recipientAuthenticationMethod, recipientPhoneInfo , null);
                 
                email = "example@example.com";

                recipientInfo1.setEmail(email);
                recipientInfo1.setSecurityOptions(securityOptions);

                recipientInfoList.add(recipientInfo1);  //Add member

                recipientInfoSet1.setMemberInfos(recipientInfoList);

                //Second Recipient

                RecipientSetInfo recipientInfoSet2 = new RecipientSetInfo();
                List<RecipientInfo> recipientInfoList2 = new ArrayList<RecipientInfo>();

                recipientAuthenticationMethod = RecipientAuthenticationMethod.PHONE;
                securityOptions = null;
                 
                phoneNumber = "987654321";//"0123456789";

                countryCode = "+1";
                RecipientPhoneInfo[] recipientPhoneInfo_1 = new RecipientPhoneInfo[1];
                recipientPhoneInfo_1[0] = new RecipientPhoneInfo(phoneNumber, countryCode);
                securityOptions = new RecipientSecurityOption(recipientAuthenticationMethod, recipientPhoneInfo_1 , null);
                 
                email = "example2@example.com";//"dummymail2@domain.com";

                RecipientInfo recipientInfo2  = new RecipientInfo();
                recipientInfo2.setEmail(email);
                recipientInfo2.setSecurityOptions(securityOptions);

                recipientInfoList2.add(recipientInfo2);  //Add member

                recipientInfoSet2.setMemberInfos(recipientInfoList2);

                //*********************************

                recipientSetInfos.add(recipientInfoSet1); 
                recipientSetInfos.add(recipientInfoSet2);

        return recipientSetInfos;

    }

}
```
