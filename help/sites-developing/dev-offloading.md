---
title: Erstellen und Verarbeiten von Aufträgen für die Auslagerung
seo-title: Creating and Consuming Jobs for Offloading
description: Die Apache Sling Discovery-Funktion bietet eine Java-API, mit der Sie JobManager-Aufträge und JobConsumer-Dienste erstellen können, die sie nutzen
seo-description: The Apache Sling Discovery feature provides a Java API that enables you to create JobManager jobs and JobConsumer services that consume them
uuid: d6a5beb0-0618-4b61-9b52-570862eac920
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: e7b6b9ee-d807-4eb0-8e96-75ca1e66a4e4
exl-id: ec5253cd-7f1e-4408-9765-8aaa9a81095c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 56%

---

# Erstellen und Verarbeiten von Aufträgen für die Auslagerung{#creating-and-consuming-jobs-for-offloading}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Apache Sling Discovery-Funktion bietet eine Java-API, mit der Sie JobManager-Aufträge und JobConsumer-Dienste erstellen können, die sie nutzen.

Informationen zum Erstellen von Abladetopologien und Konfigurieren des Themenverbrauchs finden Sie unter [Abladen von Aufträgen](/help/sites-deploying/offloading.md).

## Verarbeiten von Auftrags-Payloads {#handling-job-payloads}

Das Abladungs-Framework definiert zwei Auftragseigenschaften zum Identifizieren der Auftrags-Payload. Die Abladungs-Replikationsagenten verwenden diese Eigenschaften, um die Ressourcen zu identifizieren, die auf die Instanzen in der Topologie repliziert werden sollen:

* `offloading.job.input.payload`: Eine kommagetrennte Liste von Inhaltspfaden. Der Inhalt wird auf der Instanz repliziert, die den Auftrag ausführt.
* `offloading.job.output.payload`: Eine kommagetrennte Liste von Inhaltspfaden. Wenn die Auftragsausführung abgeschlossen ist, wird die Auftrags-Payload unter diesen Pfaden auf der Instanz repliziert, die den Auftrag erstellt hat.

Verwenden Sie die Aufzählung `OffloadingJobProperties`, um auf die Eigenschaftsnamen zu verweisen:

* `OffloadingJobProperties.INPUT_PAYLOAD.propertyName()`
* `OffloadingJobProperties.OUTPUT_PAYLOAD.propetyName()`

Für Aufträge sind keine Payloads erforderlich. Eine Payload ist jedoch dann notwendig, wenn der Auftrag die Bearbeitung einer Ressource erfordert und er auf einen Computer abgeladen wird, der den Auftrag nicht erstellt hat.

## Erstellen von Aufträgen für die Abladung {#creating-jobs-for-offloading}

Erstellen Sie einen Client, der die Methode JobManager.addJob aufruft, um einen Auftrag zu erstellen, den ein automatisch ausgewählter JobConsumer-Dienst ausführt. Geben Sie die folgenden Informationen an, um den Auftrag zu erstellen:

* Thema: Das Auftragsthema.
* Name: (Optional)
* Eigenschaftenzuordnung: Ein `Map<String, Object>`-Objekt, das beliebig viele Eigenschaften enthält, z. B. die Pfade für die Eingabe-Payload und Ausgabe-Payload. Dieses Zuordnungsobjekt ist für das JobConsumer-Objekt verfügbar, das den Auftrag ausführt.

Der Dienst im folgenden Beispiel erstellt einen Auftrag für ein bestimmtes Thema und einen bestimmten Payload-Pfad.

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;

import java.util.HashMap;

import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;

import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.ResourceResolver;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class JobGeneratorImpl implements JobGenerator  {

 @Reference
 private JobManager jobManager;
 @Reference ResourceResolverFactory resolverFactory;

 public String createJob(String topic, String payload) throws Exception {
  Job offloadingJob;

  ResourceResolver resolver = resolverFactory.getResourceResolver(null);
  if(resolver.getResource(payload)!=null){

   HashMap<String, Object> jobprops = new HashMap<String, Object>();
   jobprops.put(OffloadingJobProperties.INPUT_PAYLOAD.propertyName(), payload);

   offloadingJob = jobManager.addJob(topic, null, jobprops);
  } else {
   throw new Exception("Payload for job cannot be found");
  }
  if (offloadingJob == null){
   throw new Exception ("Offloading job could not be created");
  }
  return offloadingJob.getId();
 }
}
```

Das Protokoll enthält die folgende Meldung, wenn „JobGeneratorImpl.createJob“ für das Thema `com/adobe/example/offloading` und die Payload `/content/geometrixx/de/services` aufgerufen wird:

```shell
10.06.2013 15:43:33.868 *INFO* [JobHandler: /etc/workflow/instances/2013-06-10/model_1554418768647484:/content/geometrixx/en/company] com.adobe.example.offloading.JobGeneratorImpl Received request to make job for topic com/adobe/example/offloading and payload /content/geometrixx/de/services
```

## Entwickeln von JobConsumer-Diensten {#developing-a-job-consumer}

Um Aufträge zu verarbeiten, entwickeln Sie einen OSGi-Dienst, der die Schnittstelle `org.apache.sling.event.jobs.consumer.JobConsumer` implementiert. Identifizieren Sie das zu verarbeitende Thema mithilfe der Eigenschaft `JobConsumer.PROPERTY_TOPICS`.

Die JobConsumer-Implementierung im folgenden Beispiel registriert das Thema `com/adobe/example/offloading`. Der JobConsumer-Dienst legt einfach den Wert für die Eigenschaft „Consumed“ des Payload-Inhaltknotens auf „true“ fest.

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;
import org.apache.sling.event.jobs.consumer.JobConsumer;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import javax.jcr.Session;
import javax.jcr.Node;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class MyJobConsumer implements JobConsumer {

 public static final String TOPIC = "com/adobe/example/offloading";

 @Property(value = TOPIC)
 static final String myTopic = JobConsumer.PROPERTY_TOPICS; 

 @Reference
 private ResourceResolverFactory resolverFactory;

 @Reference
 private JobManager jobManager;

 private final Logger log = LoggerFactory.getLogger(getClass());

 public JobResult process(Job job) {
  JobResult result = JobResult.FAILED;
  String topic = job.getTopic();
  log.info("Consuming job of topic: {}", topic);
  String payloadIn =  (String) job.getProperty(OffloadingJobProperties.INPUT_PAYLOAD.propertyName());
  String payloadOut =  (String) job.getProperty(OffloadingJobProperties.OUTPUT_PAYLOAD.propertyName());

  log.info("Job has Input Payload {} and Output Payload {}",payloadIn, payloadOut);

  ResourceResolver resolver = null;
  try {
   resolver = resolverFactory.getAdministrativeResourceResolver(null);
   Session session = resolver.adaptTo(Session.class);
   Node inNode = session.getNode(payloadIn);
   inNode.getNode(Node.JCR_CONTENT).setProperty("consumed",true);
   result = JobResult.OK;
  }catch (Exception e){
   log.info("ERROR -- JOB RESULT IS FAILURE " + e.getMessage());
   result = JobResult.FAILED;
  }
  log.info("Job OK for payload {}",payloadIn);
  return result;
 }
}
```

Die MyJobConsumer-Klasse generiert die folgenden Protokollmeldungen für die Eingabe-Payload /content/geometrixx/de/services:

```shell
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Consuming job of topic: com/adobe/example/offloading
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job has Input Payload /content/geometrixx/de/services and Output Payload /content/geometrixx/de/services
10.06.2013 16:02:40.884 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job OK for payload /content/geometrixx/de/services
```

Die Eigenschaft &quot;Consumed&quot;kann mithilfe von CRXDE Lite beobachtet werden:

![chlimage_1-25](assets/chlimage_1-25.png)

## Maven-Abhängigkeiten {#maven-dependencies}

Fügen Sie die folgenden Abhängigkeitsdefinitionen zu Ihrer Datei &quot;pom.xml&quot;hinzu, damit Maven die Klassen auflösen kann, die sich auf die Abladung beziehen.

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.event</artifactId>
   <version>3.1.5-R1485539</version>
   <scope>provided</scope> 
</dependency>
<dependency>
   <groupId>com.adobe.granite</groupId>
   <artifactId>com.adobe.granite.offloading.core</artifactId>
   <version>1.0.4</version>
   <scope>provided</scope>
</dependency>
```

Für die vorherigen Beispiele waren auch die folgenden Abhängigkeitsdefinitionen erforderlich:

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.api</artifactId>
   <version>2.4.3-R1488084</version>
   <scope>provided</scope>
</dependency>

<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
   <version>2.0.0</version>
   <scope>provided</scope>
</dependency>
```
