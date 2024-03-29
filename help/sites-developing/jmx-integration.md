---
title: Integrieren von Diensten mit der JMX-Konsole
seo-title: Integrating Services with the JMX Console
description: Stellen Sie Dienstattribute und Vorgänge bereit, damit Verwaltungsaufgaben ausgeführt werden können, indem Sie MBeans erstellen und bereitstellen, um Dienste mit der JMX-Konsole zu verwalten.
seo-description: Expose service attributes and operations to enable administration tasks to be performed by creating and deploying MBeans to manage services using the JMX Console
uuid: 730a09b6-a110-4203-8de2-d4c46edc59f6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: df8cfde3-543d-4150-9822-9be763908bd7
exl-id: d56fa6ba-6ac7-4d4f-968b-075f4f13957c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1693'
ht-degree: 22%

---

# Integrieren von Diensten mit der JMX-Konsole{#integrating-services-with-the-jmx-console}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erstellen und stellen Sie MBeans für die Verwaltung von Diensten mithilfe der JMX-Konsole bereit. Zeigen Sie Dienstattribute und Vorgänge an, damit Verwaltungsaufgaben ausgeführt werden können.

Informationen zur Verwendung der JMX-Konsole finden Sie unter [Überwachen von Serverressourcen mit der JMX-Konsole](/help/sites-administering/jmx-console.md).

## Das JMX-Framework in Felix und CQ5 {#the-jmx-framework-in-felix-and-cq}

Auf der Apache Felix-Plattform stellen Sie MBeans als OSGi-Dienste bereit. Wenn ein MBean-Dienst in der OSGi-Dienst-Registrierung registriert wird, registriert das Aries JMX Whiteboard-Modul das MBean automatisch beim MBean-Server. Das MBean ist dann für die JMX-Konsole verfügbar, die die öffentlichen Attribute und Vorgänge veröffentlicht.

![jmxwhiteboard](assets/jmxwhiteboard.png)

## Erstellen von MBeans für CQ5 und CRX {#creating-mbeans-for-cq-and-crx}

MBeans, die Sie für die Verwaltung von CQ5- oder CRX-Ressourcen erstellen, basieren auf der Schnittstelle javax.management.DynamicMBean. Um sie zu erstellen, folgen Sie den üblichen Designmustern, die in der JMX-Spezifikation festgelegt sind:

* Erstellen Sie die Verwaltungsoberfläche, einschließlich der Methoden zum Abrufen, Festlegen und Definieren von Attributen und anderer Methoden zum Definieren von Vorgängen.
* Erstellen Sie die Implementierungsklasse. Die Klasse muss DynamicMBean implementieren oder eine Implementierungsklasse von DynamicMBean erweitern.
* Befolgen Sie die standardmäßige Namenskonvention, sodass der Name der Implementierungsklasse der Name der Schnittstelle mit dem MBean-Suffix ist.

Neben der Definition der Verwaltungsschnittstelle definiert die Schnittstelle auch die OSGi-Dienstschnittstelle. Die Implementierungsklasse implementiert den OSGi-Dienst.

### Verwenden von Anmerkungen zur Bereitstellung von MBean-Informationen {#using-annotations-to-provide-mbean-information}

Die [com.adobe.granite.jmx.annotation](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/jmx/annotation/package-summary.html) Das -Paket enthält mehrere Anmerkungen und Klassen, um der JMX-Konsole einfach MBean-Metadaten bereitzustellen. Verwenden Sie diese Anmerkungen und Klassen, anstatt Informationen direkt zum MBeanInfo-Objekt des MBean hinzuzufügen.

**Anmerkungen**

Fügen Sie Anmerkungen zur Verwaltungsoberfläche hinzu, um MBean-Metadaten anzugeben. Die Informationen werden in der JMX-Konsole für jede bereitgestellte Implementierungsklasse angezeigt. Die folgenden Anmerkungen sind verfügbar (vollständige Informationen finden Sie unter [com.adobe.granite.jmx.annotation JavaDocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/jmx/annotation/package-summary.html)):

* **Beschreibung:** Enthält eine Beschreibung der MBean-Klasse oder -Methode. Bei Verwendung in der Klassendeklaration wird die Beschreibung auf der JMX Console-Seite für das MBean angezeigt. Bei Verwendung in einer Methode wird die Beschreibung als Mauszeiger-Text für das entsprechende Attribut oder den entsprechenden Vorgang angezeigt.
* **Impact:** Die Auswirkung einer Methode. Gültige Parameterwerte sind die Felder, die von [javax.management.MBeanOperationInfo](https://docs.oracle.com/javase/1.5.0/docs/api/javax/management/MBeanOperationInfo.html) definiert werden.

* **Name:** Gibt den Namen an, der für einen Vorgangsparameter angezeigt werden soll. Verwenden Sie diese Anmerkung, um den tatsächlichen Namen des Methodenparameters zu überschreiben, der in der Benutzeroberfläche verwendet wird.
* **OpenTypeInfo:** Gibt die Klasse an, die für die Darstellung von zusammengesetzten Daten oder Tabellendaten in der JMX-Konsole verwendet werden soll. Für die Verwendung mit Open MBeans
* **TabularTypeInfo:** Wird verwendet, um die Klasse zu kommentieren, die zur Darstellung von Tabellendaten verwendet wird.

**Klassen**

Klassen werden zum Erstellen dynamischer MBeans bereitgestellt, die die Anmerkungen nutzen, die Sie zu ihren Schnittstellen hinzufügen:

* **AnnotatedStandardMBean:** Eine Unterklasse der Klasse javax.management.StandardMBean , die der JMX-Konsole automatisch die Anmerkungsmetadaten bereitstellt.
* **OpenAnnotatedStandardMBean:** eine Unterklasse der Klasse AnnotatedStandardMBean für die Erstellung von Open MBeans, die die OpenTypeInfo-Anmerkung nutzen.

### Entwickeln von MBeans {#developing-mbeans}

In der Regel spiegelt Ihr MBean den OSGi-Dienst wider, den Sie verwalten möchten. Auf der Felix-Plattform erstellen Sie das MBean wie auf anderen Java-Serverplattformen. Ein Hauptunterschied besteht darin, dass Sie mit Anmerkungen MBean-Informationen angeben können:

* Verwaltungsoberfläche: Definiert Attribute mithilfe von Getter-, Setter- und is-Methoden. Definiert Vorgänge mit anderen öffentlichen Methoden. Stellt mithilfe von Anmerkungen Metadaten für das BeanInfo-Objekt bereit.
* MBean-Klasse: Implementiert die Verwaltungsschnittstelle. Erweitert die Klasse AnnotatedStandardMBean , sodass sie die Anmerkungen auf der Benutzeroberfläche verarbeitet.

Das folgende Beispiel-MBean stellt Informationen zum CRX-Repository bereit. Die Schnittstelle verwendet die Anmerkung Beschreibung , um Informationen für die JMX-Konsole bereitzustellen.

#### Verwaltungsoberfläche {#management-interface}

```java
package com.adobe.example.myapp;

import com.adobe.granite.jmx.annotation.Description;

@Description("Example MBean that exposes repository properties.")
public interface ExampleMBean {

    @Description("The name of the repository.")
    String getRepositoryName();

    @Description("The vendor of the repository.")
    String   getRepositoryVendor();

    @Description("The URL of repository vendor.")
    String getVendorUrl();
}
```

Die Implementierungsklasse verwendet den SlingRepository-Dienst, um Informationen zum CRX-Repository abzurufen.

#### MBean-Implementierungsklasse {#mbean-implementation-class}

```java
package com.adobe.example.myapp;

import org.apache.felix.scr.annotations.*;
import org.apache.sling.jcr.api.SlingRepository;

import com.adobe.granite.jmx.annotation.AnnotatedStandardMBean;

import javax.management.*;

public class ExampleMBeanImpl extends AnnotatedStandardMBean implements ExampleMBean {

    @Reference(cardinality = ReferenceCardinality.OPTIONAL_UNARY)
    private SlingRepository repository;

    public ExampleMBeanImpl() throws NotCompliantMBeanException {
        super(ExampleMBean.class);
    }

    public String getRepositoryName() {
        return repository.getDescriptor("jcr.repository.name");
    }

    public String getRepositoryVendor() {
        return repository.getDescriptor("jcr.repository.vendor");
    }

    public String getVendorUrl() {
        return repository.getDescriptor("jcr.repository.vendor.url");
    }
}
```

Die folgende Abbildung zeigt die Seite für dieses MBean in der JMX-Konsole.

![jmxdescription](assets/jmxdescription.png)

### Registrieren von MBeans {#registering-mbeans}

Wenn Sie MBeans als OSGi-Dienst registrieren, werden sie automatisch beim MBean-Server registriert. Um ein MBean auf CQ5 zu installieren, schließen Sie es in ein Bundle ein und exportieren Sie den MBean-Dienst wie jeden anderen OSGi-Dienst.

Zusätzlich zu den OSGi-bezogenen Metadaten müssen Sie auch Metadaten angeben, die das Aries JMX Whiteboard-Modul für die Registrierung des MBean beim MBean-Server benötigt:

* **Name der DynamicMBean-Schnittstelle:** Deklarieren Sie, dass der MBean-Dienst die Schnittstelle `javax.management.DynamicMBea`n implementiert. Diese Deklaration informiert das Aries JMX Whiteboard-Modul darüber, dass es sich bei dem Dienst um einen MBean-Dienst handelt.

* **MBean-Domain und wichtige Eigenschaften:** Bei Felix geben Sie diese Daten als Eigenschaft des OSGi-Dienstes des MBean an. Dabei handelt es sich um dieselben Daten, die Sie für gewöhnlich dem MBean-Server in einem `javax.management.ObjectName`-Objekt bereitstellen.

Wenn Ihr MBean ein Spiegelbild eines einzelnen Dienstes ist, ist nur eine einzige Instanz des MBean-Dienstes erforderlich. Wenn Sie in diesem Fall das Felix SCR Maven-Plug-in verwenden, können Sie die Apache Felix Service Component Runtime (SCR)-Anmerkungen auf der MBean-Implementierungsklasse verwenden, um die JMX-bezogenen Metadaten anzugeben. Um mehrere MBean-Instanzen zu instanziieren, können Sie eine andere Klasse erstellen, die diese Registrierung des OSGi-Dienstes des MBean durchführt. In diesem Fall werden die JMX-bezogenen Metadaten zur Laufzeit generiert.

**Einzelnes MBean**

MBeans, für die Sie alle Attribute und Vorgänge zur Entwurfszeit definieren können, können mit SCR-Anmerkungen in der MBean-Implementierungsklasse bereitgestellt werden. Im folgenden Beispiel deklariert das Attribut `value` der Anmerkung `Service`, dass der Dienst die Schnittstelle `DynamicMBean` implementiert. Das Attribut `name` der Anmerkung `Property` legt die JMX-Domain und die wichtigsten Eigenschaften fest.

#### MBean-Implementierungsklasse mit SCR-Anmerkungen {#mbean-implementation-class-with-scr-annotations}

```java
package com.adobe.example.myapp;

import org.apache.felix.scr.annotations.*;
import org.apache.sling.jcr.api.SlingRepository;

import com.adobe.granite.jmx.annotation.AnnotatedStandardMBean;

import javax.management.*;

@Component(immediate = true)
@Property(name = "jmx.objectname", value="com.adobe.example:type=CRX")
@Service(value = DynamicMBean.class)
public class ExampleMBeanImpl extends AnnotatedStandardMBean implements ExampleMBean {

    @Reference(cardinality = ReferenceCardinality.OPTIONAL_UNARY)
    private SlingRepository repository;

    public ExampleMBeanImpl() throws NotCompliantMBeanException {
        super(ExampleMBean.class);
    }

    public String getRepositoryName() {
        return repository.getDescriptor("jcr.repository.name");
    }

    public String getRepositoryVendor() {
        return repository.getDescriptor("jcr.repository.vendor");
    }

    public String getVendorUrl() {
        return repository.getDescriptor("jcr.repository.vendor.url");
    }
}
```

**Mehrere MBean-Dienstinstanzen**

Um mehrere Instanzen eines verwalteten Dienstes zu verwalten, erstellen Sie mehrere Instanzen des entsprechenden MBean-Dienstes. Darüber hinaus sollten MBean-Dienstinstanzen erstellt oder entfernt werden, wenn verwaltete Dienste gestartet oder angehalten werden. Sie können eine MBean-Managerklasse erstellen, die MBean-Dienste zur Laufzeit initiiert und den Dienstlebenszyklus verwaltet.

Verwenden Sie BundleContext, um das MBean als OSGi-Dienst zu registrieren. Schließen Sie die JMX-bezogenen Informationen in das Dictionary-Objekt ein, das Sie als Argument der `BundleContext.registerService` -Methode.

Im folgenden Codebeispiel wird der ExampleMBean-Dienst programmgesteuert registriert. Das componentContext -Objekt ist ComponentContext, das Zugriff auf BundleContext bietet.

#### Codeausschnitt: Programmatische MBean-Dienstregistrierung {#code-snippet-programmatic-mbean-service-registration}

```java
Dictionary mbeanProps = new Hashtable();
mbeanProps.put("jmx.objectname", "com.adobe.example:type=CRX");
ExampleMBeanImpl mbean = new ExampleMBeanImpl();
ServiceRegistration serviceregistration = 
            componentContext.getBundleContext().registerService(DynamicMBean.class.getName(), mbean, mbeanProps);
```

Das Beispiel-MBean im nächsten Abschnitt enthält weitere Details.

Ein MBean-Service Manager ist nützlich, wenn Dienstkonfigurationen im Repository gespeichert werden. Der Manager kann Dienstinformationen abrufen und zum Konfigurieren und Erstellen des entsprechenden MBean verwenden. Die Manager-Klasse kann auch auf Repository-Änderungsereignisse warten und die MBean-Dienste entsprechend aktualisieren.

## Beispiel: Überwachen von Workflow-Modellen mit JMX {#example-monitoring-workflow-models-using-jmx}

Das MBean in diesem Beispiel enthält Informationen zu den CQ5-Workflow-Modellen, die im Repository gespeichert sind. Eine MBean-Manager-Klasse erstellt MBeans basierend auf Workflow-Modellen, die im Repository gespeichert sind, und registriert ihren OSGi-Dienst zur Laufzeit. Dieses Beispiel besteht aus einem einzelnen Bundle, das die folgenden Mitglieder enthält:

* WorkflowMBean: Die Verwaltungsschnittstelle.
* WorkflowMBeanImpl: Die MBean-Implementierungsklasse.
* WorkflowMBeanManager: Die Schnittstelle der MBean-Manager-Klasse.
* WorkflowMBeanManagerImpl: Die Implementierungsklasse des MBean-Managers.

>[!NOTE]
>
>Der Einfachheit halber führt der Code in diesem Beispiel keine Protokollierung durch oder reagiert nicht auf ausgelöste Ausnahmen.

WorkflowMBeanManagerImpl enthält eine Komponentenaktivierungsmethode. Wenn die Komponente aktiviert ist, führt die Methode die folgenden Aufgaben aus:

* Ruft einen BundleContext für das Bundle ab.
* Fragt das Repository ab, um die Pfade der vorhandenen Workflow-Modelle abzurufen.
* Sie erstellt MBeans für jedes Workflow-Modell.
* Registriert die MBeans bei der OSGi-Dienstregistrierung.

Die MBean-Metadaten werden in der JMX-Konsole mit der Domain com.adobe.example und dem workflow_model-Typ angezeigt. Als Eigenschaft ist der Pfad des Workflow-Modellkonfigurationsknotens angegeben.

![jmxworkflowmbean](assets/jmxworkflowmbean.png)

### Das Beispiel-MBean {#the-example-mbean}

Dieses Beispiel setzt eine MBean-Schnittstelle und -Implementierung voraus, die ein Abbild der Schnittstelle `com.day.cq.workflow.model.WorkflowModel` ist. Das MBean ist sehr einfach, sodass sich das Beispiel auf die Konfigurations- und Bereitstellungsaspekte des Designs konzentrieren kann. Das MBean stellt ein einzelnes Attribut bereit, den Modellnamen.

#### WorkflowMBean-Schnittstelle {#workflowmbean-interface}

```java
package com.adobe.example.myapp.api;

import com.adobe.granite.jmx.annotation.Description;

@Description("Example MBean that exposes Workflow model properties.")
public interface WorkflowMBean {
 
 @Description("The name of the Workflow model.")
 String getModelName();
}
```

#### WorkflowMBeanImpl {#workflowmbeanimpl}

```java
package com.adobe.example.myapp.impl;

import javax.management.NotCompliantMBeanException;

import com.day.cq.workflow.model.WorkflowModel;
import com.adobe.example.myapp.api.WorkflowMBean;
import com.adobe.granite.jmx.annotation.AnnotatedStandardMBean;

public class WorkflowMBeanImpl extends AnnotatedStandardMBean implements WorkflowMBean {

 WorkflowModel model; 
 
 protected WorkflowMBeanImpl(WorkflowModel inmodel)
   throws NotCompliantMBeanException {
  super(WorkflowMBean.class);
  model=inmodel;
 }

 public String getModelName() {
  return model.getTitle();
 }
}
```

### Der Beispiel-MBean-Manager {#the-example-mbean-manager}

Der WorkflowMBeanManager-Dienst enthält die Komponentenaktivierungsmethode, die WorkflowMBean-Dienste erstellt. Die Dienstimplementierung umfasst die folgenden Methoden:

* aktivieren: Die Komponentenaktivierung. Erstellt die JCR-Sitzung zum Lesen der WorkflowModel-Konfigurationsknoten. Der Stammknoten, unter dem Modellkonfigurationen gespeichert werden, wird in einem statischen Feld definiert. Der Name des Konfigurationsknotens wird auch in einem statischen Feld definiert. Diese Methode ruft andere Methoden auf, die die Knotenmodellpfade abrufen und die WorkflowMBeans des Modells erstellen.
* getModelIds: Durchsucht das Repository unter dem Stammknoten und ruft den Pfad jedes Modellknotens ab.
* makeMBean: Verwendet den Modellpfad, um ein WorkflowModel -Objekt zu erstellen, erstellt ein WorkflowMBean dafür und registriert seinen OSGi-Dienst.

>[!NOTE]
>
>Die WorkflowMBeanManager-Implementierung erstellt nur MBean-Dienste für Modellkonfigurationen, die bei Aktivierung der Komponente vorhanden sind. Eine stabilere Implementierung überwacht Repository-Ereignisse in Bezug auf neue Modellkonfigurationen und Änderungen oder Löschungen vorhandener Modellkonfigurationen. Wenn eine Änderung eintritt, kann der Manager den entsprechenden WorkflowMBean-Dienst erstellen, ändern oder entfernen.

#### WorkflowMBeanManager-Schnittstelle {#workflowmbeanmanager-interface}

```java
package com.adobe.example.myapp.api;

public interface WorkflowMBeanManager {

}
```

#### WorkflowMBeanManagerImpl {#workflowmbeanmanagerimpl}

```java
package com.adobe.example.myapp.impl;

import java.util.*;

import org.apache.felix.scr.annotations.*;

import javax.jcr.Session;
import javax.jcr.Node;
import javax.jcr.NodeIterator;
import javax.jcr.RepositoryException;
import javax.management.ObjectName;

import org.apache.sling.jcr.api.SlingRepository;
import org.osgi.framework.ServiceRegistration;
import org.osgi.service.component.ComponentContext;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.workflow.WorkflowService;
import com.day.cq.workflow.WorkflowSession;
import com.adobe.example.myapp.api.WorkflowMBean;
import com.adobe.example.myapp.api.WorkflowMBeanManager;

/**Instantiates and registers WorkflowMBean services */
@Component(immediate=true)
@Service(value=WorkflowMBeanManager.class)
public class WorkflowMBeanManagerImpl implements WorkflowMBeanManager {
 //The ComponentContext provides access to the BundleContext
 private ComponentContext componentContext;

 //Use the SlingRepository service to read model nodes
 @Reference
        private SlingRepository repository = null;

 //Use the WorkflowService service to create WorkflowModel objects
 @Reference
 private WorkflowService workflowservice = null;
 
  private Session session;

         //Details about model nodes
  private static final String MODEL_ROOT ="/etc/workflow/models"; 
  private static final String MODEL_NODE = "model";

  private Set<String> modelIds = new HashSet<String>();

        //Storage for ServiceRegistrations for MBean services
  private Collection<ServiceRegistration> mbeanRegistrations= new Vector<ServiceRegistration>(0,1);
 
 @Activate
        protected void activate(ComponentContext ctx) { 
             //Traverse the repository and load the model nodes
             try {
                   session = repository.loginAdministrative(null);
                   // load and store model node paths
                   if (session.nodeExists(MODEL_ROOT)) {
                          getModelIds(session.getNode(MODEL_ROOT));
                   }
                   //Create MBeans for each model
                   for(String modid: modelIds){
                    makeMBean(modid);
                    }
             }catch(Exception e){ }
          }

        /**
         * Add JMX domain and key properties to a collection 
         * Instantiate a WorkflowModel and its WorkflowMBeanImpl object
         * Register the MBean OSGi service 
         */
 private void makeMBean(String modelId) {
             // create MBean for the model
             try {
                 Dictionary<String, String> mbeanProps = new Hashtable<String, String>();
                 //These properties appear on the JMX Console home page
                 mbeanProps.put("jmx.objectname", "com.adobe.example:type=workflow_model,id=" + ObjectName.quote(modelId));
                 WorkflowSession wfsession = workflowservice.getWorkflowSession(session);
                 WorkflowMBeanImpl mbean = new WorkflowMBeanImpl(wfsession.getModel(modelId));

                ServiceRegistration serviceregistration = componentContext.getBundleContext().registerService(WorkflowMBean.class.getName(), mbean, mbeanProps);
                //Store the ServiceRegistration objects for deactivation
                mbeanRegistrations.add(serviceregistration);
             } catch (Throwable t) {}
         }

        /**
         * Traverses the repository branch below a given Node. Stores the path of each model node.
         */
 private void getModelIds(Node node) throws RepositoryException {
  try{
                     NodeIterator iter = node.getNodes();
                     while (iter.hasNext()) {
                           Node n = iter.nextNode();
                           //Look for "jcr:content" nodes
                           if (n.getName().equals("jcr:content")) {
                                //get the path of the model node and save it 
                                if(n.hasNode(MODEL_NODE)){
                                      modelIds.add(n.getNode(MODEL_NODE).getPath());
                                 }
                           } else{ 
                                   //Scan child nodes
                                   getModelIds(n);
                           }
                       }
  }catch(Exception e){ }
       }

        /**
         * Log out of the JCR session and unregister WorkflowMBean services
         */
        @Deactivate
        protected void deactivate() {
          session.logout();
          session=null;
          for(ServiceRegistration sr:mbeanRegistrations){
         sr.unregister();
          }
        }
}
```

### Die POM-Datei für das Beispiel-MBean {#the-pom-file-for-the-example-mbean}

Der Einfachheit halber können Sie den folgenden XML-Code in Ihre Projektdatei pom.xml kopieren, um das Komponenten-Bundle zu erstellen. Das POM verweist auf mehrere erforderliche Plug-ins und Abhängigkeiten.

**Plug-ins:**

* Apache Maven Compiler-Plug-in: Kompiliert Java-Klassen aus dem Quellcode.
* Apache Felix Maven Bundle-Plug-in: Erstellt das Bundle und das Manifest
* Apache Felix Maven SCR Plugin: Erstellt die Komponentendeskriptordatei und konfiguriert die Manifestkopfzeile der Dienstkomponente.

**Hinweis:** Zum Zeitpunkt des Schreibens ist das Maven-SCR-Plugin nicht mit dem m2e-Plugin für Eclipse kompatibel. (Siehe [Felix bug 3170](https://issues.apache.org/jira/browse/FELIX-3170). Um die Eclipse IDE zu verwenden, installieren Sie Maven und verwenden Sie die Befehlszeilenschnittstelle, um Builds durchzuführen.

#### Beispiel-POM-Datei {#example-pom-file}

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.2-SNAPSHOT</version>
  <name>mbean-simple</name>
  <url>www.adobe.com</url>
  <description>A simple MBean</description>
  <packaging>bundle</packaging>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>
    <build>
        <plugins>
        <plugin> 
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId> 
            <configuration> 
                <source>1.5</source> 
                <target>1.5</target> 
            </configuration> 
        </plugin>
            <plugin>
                <groupId>org.apache.felix</groupId>
                <artifactId>maven-scr-plugin</artifactId>
                <version>1.7.2</version>
                <executions>
                    <execution>
                        <id>generate-scr-scrdescriptor</id>
              <goals>
                 <goal>scr</goal>
              </goals>
            </execution>
         </executions>
            </plugin>
             <plugin> 
            <groupId>org.apache.felix</groupId> 
            <artifactId>maven-bundle-plugin</artifactId>
            <version>1.4.3</version> 
            <extensions>true</extensions> 
            <configuration> 
                <instructions> 
                    <Export-Package>com.adobe.example.myapp.*;version=${project.version}</Export-Package> 
                </instructions>
            </configuration> 
        </plugin>
        </plugins>
    </build>
    <dependencies>
        <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr.annotations</artifactId>
            <version>1.6.0</version>
            <scope>provided</scope>
        </dependency>
         <dependency>
            <groupId>org.apache.sling</groupId>
            <artifactId>org.apache.sling.api</artifactId>
            <version>2.0.8</version>
            <scope>provided</scope>
        </dependency>
         <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr</artifactId>
            <version>1.6.1-R1236132</version>
            <scope>provided</scope>
        </dependency>
        <dependency>
            <groupId>org.apache.sling</groupId>
            <artifactId>org.apache.sling.jcr.api</artifactId>
            <version>2.0.4</version>
        </dependency>
        <dependency>
            <groupId>com.adobe.granite</groupId>
            <artifactId>com.adobe.granite.jmx</artifactId>
            <version>0.1.6</version>
            <scope>provided</scope>
        </dependency>
        <dependency>
       <groupId>com.day.cq.wcm</groupId>
       <artifactId>cq-wcm-mobile-api</artifactId>
       <version>5.5.2</version>
       <scope>provided</scope>
      </dependency>
      <dependency>
       <groupId>com.day.cq.workflow</groupId>
       <artifactId>cq-workflow-api</artifactId>
       <version>5.5.0</version>
       <scope>provided</scope> 
      </dependency>
      <dependency>
       <groupId>javax.jcr</groupId>
       <artifactId>jcr</artifactId>
       <version>2.0</version>
       <scope>provided</scope>
      </dependency>
      <dependency>
                <groupId>org.slf4j</groupId>
  <artifactId>slf4j-api</artifactId>
  <version>1.6.4</version>
  <scope>provided</scope>
 </dependency>
    </dependencies>
</project>
```

Fügen Sie Ihrer Maven-Einstellungsdatei das folgende Profil hinzu, um das öffentliche Adobe-Repository zu verwenden.

#### Maven-Profil {#maven-profile}

```xml
<profile>
    <id>adobe-public</id>
    <activation>
         <activeByDefault>false</activeByDefault>
    </activation>
    <properties>
         <releaseRepository-Id>adobe-public-releases</releaseRepository-Id>
         <releaseRepository-Name>Adobe Public Releases</releaseRepository-Name>
         <releaseRepository-URL>https://repo.adobe.com/nexus/content/groups/public</releaseRepository-URL>
    </properties>
    <repositories>
         <repository>
             <id>adobe-public-releases</id>
             <name>Adobe Basel Public Repository</name>
             <url>https://repo.adobe.com/nexus/content/groups/public</url>
             <releases>
                 <enabled>true</enabled>
                 <updatePolicy>never</updatePolicy>
             </releases>
             <snapshots>
                 <enabled>false</enabled>
             </snapshots>
         </repository>
     </repositories>
     <pluginRepositories>
         <pluginRepository>
             <id>adobe-public-releases</id>
             <name>Adobe Basel Public Repository</name>
             <url>https://repo.adobe.com/nexus/content/groups/public</url>
             <releases>
                 <enabled>true</enabled>
                 <updatePolicy>never</updatePolicy>
             </releases>
             <snapshots>
                 <enabled>false</enabled>
             </snapshots>
         </pluginRepository>
     </pluginRepositories>
</profile>
```
