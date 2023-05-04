---
title: Verwenden von Metadaten in einer E-Mail-Benachrichtigung
seo-title: Use metadata in an email notification
description: Verwenden von Metadaten zum Ausfüllen von Informationen in einer E-Mail-Benachrichtigung im Arbeitsablauf für Formulare
seo-description: Use metadata to populate information in a forms workflow email notification
uuid: 17e018c9-6bf8-4042-bba9-4ebe449304ac
topic-tags: publish
discoiquuid: bdf13893-630a-43cd-aaeb-c7c16bf4f8a6
exl-id: 248c5adf-23e9-463f-9f29-869ae2426c22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 22%

---

# Verwenden von Metadaten in einer E-Mail-Benachrichtigung  {#use-metadata-in-an-email-notification}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Verwenden von Metadaten zum Ausfüllen von Informationen in einer E-Mail-Benachrichtigung im Arbeitsablauf für Formulare

Sie können den Schritt &quot;Aufgabe zuweisen&quot;verwenden, um einem Benutzer oder einer Gruppe Aufgaben zu erstellen und zuzuweisen. Wenn eine Aufgabe einem Benutzer oder einer Gruppe zugewiesen wird, wird eine E-Mail-Benachrichtigung an den definierten Benutzer oder an jedes Mitglied der definierten Gruppe gesendet. Eine typische [E-Mail-Benachrichtigung](/help/forms/using/use-custom-email-template-assign-task-step.md) enthält die Verknüpfung der zugewiesenen Aufgabe und Informationen zur Aufgabe.

Sie können Metadaten in einer E-Mail-Vorlage verwenden, um Informationen in einer E-Mail-Benachrichtigung dynamisch auszufüllen. Beispielsweise wird der Wert des Titels, der Beschreibung, des Fälligkeitsdatums, der Priorität, des Workflows und des letzten Datums in der folgenden E-Mail-Benachrichtigung dynamisch zur Laufzeit ausgewählt (wenn eine E-Mail-Benachrichtigung generiert wird).

![default-email-template](assets/default-email-template.png)

Metadaten werden in Schlüssel-Wert-Paaren gespeichert. Sie können den Schlüssel in der E-Mail-Vorlage angeben und der Schlüssel wird zur Laufzeit durch einen Wert ersetzt (wenn eine E-Mail-Benachrichtigung generiert wird). Im folgenden Codebeispiel ist beispielsweise „$ {workitem_title}“ ein Schlüssel. Sie wird zur Laufzeit durch den Wert &quot;Loan-Request&quot;ersetzt.

```xml
subject=Task Assigned - ${workitem_title}

message=<html><body>\n\
 <table>\n\
  <tbody>\n\
   <tr>\n\
    <td>\n\
      Sample Company\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <pre style="font-size: 13px; font-family: Helvetica, Arial, sans-serif;  font-weight: normal; color: #323232;"> Hello ${workitem_assignee},\n\
 The following task has been assigned to you:</pre>\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <table>\n\
      <tbody>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> TITLE</td>\n\
        <td>\n\
         <p>${workitem_title}</p>\n\
        </td>\n\
       </tr>\n\
                            <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> DESCRIPTION</td>\n\
        <td>\n\
         <p>${workitem_description}</p>\n\
        </td>\n\
       </tr>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> DUE DATE</td>\n\
        <td>\n\
         <p>${workitem_due_date}</p>\n\
        </td>\n\
       </tr>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> PRIORITY</td>\n\
        <td>\n\
         <p>${workitem_priority}</p>\n\
        </td>\n\
       </tr>\n\
       <tr>\n\
        <td> WORKFLOW</td>\n\
        <td>\n\
         <p>${workitem_workflow}</p>\n\
        </td>\n\
       </tr>\n\
      </tbody>\n\
     </table>\n\
    </td>\n\
   </tr>\n\
   <tr style = "text-align: center; vertical-align: middle;">\n\
    <td> \n\
     <a href="${workitem_url}" target="_blank" style="background-color: #1EBBBB; font-size: 18px; line-height: 25px; font-weight: bold; color: #FFFFFF; text-decoration: none; padding: 15px 15px 15px 15px;">Open Task</a>\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <p><span style="font-size: 12px; font-weight: normal; font-style: italic; color: #919191;">This is an automatically generated email. Please do not reply to this email.</span></p>\n\
    </td>\n\
   </tr>\n\
  </tbody>\n\
 </table>\n\
</body>\n\
</html>\n\
```

## Verwenden systemgenerierter Metadaten in einer E-Mail-Benachrichtigung {#using-system-generated-metadata-in-an-email-notification}

Eine AEM Forms-Anwendung bietet standardmäßig mehrere Metadatenvariablen (Schlüssel-Wert-Paare). Sie können diese Variablen in einer E-Mail-Vorlage verwenden. Der Wert der Variablen basiert auf der zugehörigen Formularanwendung. In der folgenden Tabelle sind alle standardmäßig verfügbaren Metadatenvariablen aufgeführt:

<table> 
 <tbody> 
  <tr> 
   <td>Schlüssel</td> 
   <td>Beschreibung</td> 
  </tr> 
  <tr> 
   <td>workitem_title</td> 
   <td>Titel der verknüpften Formularanwendung.</td> 
  </tr> 
  <tr> 
   <td>workitem_url</td> 
   <td>URL für den Zugriff auf die verknüpfte Formularanwendung.</td> 
  </tr> 
  <tr> 
   <td>workitem_description</td> 
   <td>Beschreibung der verknüpften Formularanwendung.</td> 
  </tr> 
  <tr> 
   <td>workitem_priority</td> 
   <td>Die für die verknüpfte Formularanwendung angegebene Priorität.</td> 
  </tr> 
  <tr> 
   <td>workitem_due_date</td> 
   <td>Letztes Datum für die Bearbeitung der zugehörigen Formularanwendung.</td> 
  </tr> 
  <tr> 
   <td>workitem_workflow</td> 
   <td>Name des mit der Formularanwendung verknüpften Workflows.</td> 
  </tr> 
  <tr> 
   <td>workitem_assign_timestamp</td> 
   <td>Datum und Uhrzeit der Zuweisung des Workflow-Elements zum aktuellen Bevollmächtigten.</td> 
  </tr> 
  <tr> 
   <td>workitem_assignee</td> 
   <td>Name des derzeitigen Bevollmächtigten.</td> 
  </tr> 
  <tr> 
   <td>host_prefix</td> 
   <td>URL des Autorenservers. Beispiel: https://10.41.42.66:4502<br /> </td> 
  </tr> 
  <tr> 
   <td>publish_prefix</td> 
   <td>URL des Veröffentlichungsservers. Beispiel: https://10.41.42.66:4503</td> 
  </tr> 
 </tbody> 
</table>

## Verwenden benutzerdefinierter Metadaten in einer E-Mail-Benachrichtigung {#using-custom-metadata-in-an-email-notification}

Sie können auch benutzerdefinierte Metadaten in einer E-Mail-Benachrichtigung verwenden. Benutzerdefinierte Metadaten enthalten Informationen zusätzlich zu systemgenerierten Metadaten. Beispielsweise Richtliniendetails, die aus einer Datenbank abgerufen werden. Sie können ein ECMAScript- oder OSGi-Bundle verwenden, um benutzerdefinierte Metadaten in crx-repository hinzuzufügen:

### Verwenden von ECMAScript zum Hinzufügen benutzerdefinierter Metadaten  {#use-ecmascript-to-add-custom-metadata}

[ECMAScript](https://de.wikipedia.org/wiki/ECMAScript) ist eine Skriptsprache. Sie wird für die Client-seitige Skripterstellung und Server-Anwendungen verwendet. Führen Sie die folgenden Schritte aus, um ECMAScript zum Hinzufügen benutzerdefinierter Metadaten für eine E-Mail-Vorlage zu verwenden:

1. Melden Sie sich mit einem Administratorkonto bei CRX DE an. Die URL lautet `https://[server]:[port]/crx/de/index.jsp`.

1. Navigieren Sie zu /apps/fd/dashboard/scripts/metadataScripts. Erstellen Sie eine Datei mit der Erweiterung .ecma. Beispiel: usermetadata.ecma

   Wenn der oben genannte Pfad nicht vorhanden ist, erstellen Sie ihn.

1. Fügen Sie der .ecma-Datei Code hinzu, der über die Logik zum Generieren benutzerdefinierter Metadaten in Schlüssel-Wert-Paaren verfügt. Beispielsweise generiert der folgende ECMAScript-Code benutzerdefinierte Metadaten für eine Versicherungspolice:

   ```
   function getUserMetaData()  {
       //Commented lines below provide an overview on how to set user metadata in map and return it.
       var HashMap = Packages.java.util.HashMap;
       var valuesMap = new HashMap();
       valuesMap.put("policyNumber", "2017568972695");
       valuesMap.put("policyHolder", "Adobe Systems");
   
       return valuesMap;
   }
   ```

1. Klicken Sie auf Alle speichern. Jetzt ist das Skript zur Auswahl in AEM Workflow-Modell verfügbar.

   ![assigntask-metadata](assets/assigntask-metadata.png)

1. (Optional) Geben Sie den Titel des Skripts an:

   Wenn Sie keinen Titel angeben, zeigt das Feld Benutzerdefinierte Metadaten den vollständigen Pfad der ECMAScript-Datei an. Führen Sie die folgenden Schritte aus, um einen aussagekräftigen Titel für das Skript festzulegen:

   1. Erweitern Sie den Skriptknoten, klicken Sie mit der rechten Maustaste auf den Knoten **[!UICONTROL jcr:content]** und dann auf **[!UICONTROL Mixins]**.
   1. Geben Sie mix:title im Dialogfeld &quot;Mixins bearbeiten&quot;ein und klicken Sie auf **+**.
   1. Fügen Sie eine Eigenschaft mit den folgenden Werten hinzu.

      | Name | jcr:title |
      |---|---|
      | Typ | Zeichenfolge |
      | Wert | Geben Sie den Titel des Skripts an. Beispielsweise benutzerdefinierte Metadaten für den Richtlinieninhaber. Der angegebene Wert wird im Schritt &quot;Aufgabe zuweisen&quot;angezeigt. |

### Verwenden eines OSGi-Bundles und einer Java-Schnittstelle zum Hinzufügen benutzerdefinierter Metadaten {#use-an-osgi-bundle-and-java-interface-to-add-custom-metadata}

Sie können die Java-Schnittstelle WorkitemUserMetadataService verwenden, um benutzerdefinierte Metadaten für E-Mail-Vorlagen hinzuzufügen. Sie können ein OSGi-Bundle erstellen, das die Java-Schnittstelle WorkitemUserMetadataService verwendet und auf dem AEM Forms-Server bereitstellt. Dadurch werden die Metadaten im Schritt &quot;Aufgabe zuweisen&quot;zur Auswahl bereitgestellt.

Um ein OSGi-Bundle mit Java-Schnittstelle zu erstellen, fügen Sie [AEM Forms Client SDK](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) jar und [Granite-JAR](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.workflow.api/1.0.2/) -Dateien als externe Abhängigkeiten zum OSGi-Bundle-Projekt. Sie können eine beliebige Java IDE verwenden, um ein OSGi-Bundle zu erstellen. Im folgenden Verfahren wird beschrieben, wie Sie mit Eclipse ein OSGi-Bundle erstellen:

1. Öffnen Sie Eclipse IDE. Navigieren Sie zu Datei > Neues Projekt.

1. Wählen Sie im Assistenten-Dialogfeld Maven-Projekt und klicken Sie auf Weiter.

1. Behalten Sie im neuen Maven-Projekt die Standardeinstellungen bei und klicken Sie auf Weiter. Wählen Sie einen Archetyp aus und klicken Sie auf Weiter . Beispiel: maven-archetype-quickstart. Geben Sie Group Id, Artifact ID, Version und Paket für das Projekt an und klicken Sie auf Beenden. Das Projekt wird erstellt.

1. Öffnen Sie die Datei &quot;pom.xml&quot;zur Bearbeitung und ersetzen Sie den gesamten Inhalt der Datei durch den folgenden Text:

   ```
   
   ```

1. Fügen Sie Quellcode hinzu, der die Java-Schnittstelle WorkitemUserMetadataService verwendet, um benutzerdefinierte Metadaten für E-Mail-Vorlagen hinzuzufügen. Unten finden Sie einen Beispielcode:

   ```java
   package com.aem.impl;
   
   import com.adobe.fd.workspace.service.external.WorkitemUserMetadataService;
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Properties;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   import org.osgi.framework.Constants;
   
   import java.util.HashMap;
   import java.util.Map;
   
   @Component
   @Service
   @Properties({
           @Property(name = Constants.SERVICE_DESCRIPTION, value = "A sample implementation of a user metadata service."),
           @Property(name = WorkitemUserMetadataService.SERVICE_PROPERTY_LABEL, value = "Default User Metadata Service")})
   
   public class WorkitemUserMetadataServiceImpl
     implements WorkitemUserMetadataService
   {
     public WorkitemUserMetadataServiceImpl() {}
   
     public Map<String, String> getUserMetadataMap()
     {
       HashMap<String, String> metadataMap = null;
       metadataMap = new HashMap();
       metadataMap.put("test_metadata", "tested-interface implementation");
       return metadataMap;
     }
   }
   ```

1. Öffnen Sie eine Eingabeaufforderung und navigieren Sie zum Ordner, der das OSGi-Bundle-Projekt enthält. Verwenden Sie den folgenden Befehl, um das OSGi-Bundle zu erstellen:

   `mvn clean install`

1. Laden Sie das Bundle auf einen AEM Forms-Server hoch. Sie können AEM Package Manager verwenden, um das Bundle auf den AEM Forms-Server zu importieren.

Nachdem das Bundle importiert wurde, können Sie die Metadaten im Schritt „Aufgabe zuweisen“ auswählen und als E-Mail-Vorlage verwenden.
