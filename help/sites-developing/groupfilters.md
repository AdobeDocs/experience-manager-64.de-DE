---
title: Erstellen von Gerätegruppenfiltern
seo-title: Creating Device Group Filters
description: Erstellen Sie einen Gerätegruppenfilter, um eine Reihe von Gerätefunktionsanforderungen zu definieren
seo-description: Create a device group filter to define a set of device capability requirements
uuid: 8db98b98-f26d-4924-930a-a682cd7df866
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: mobile-web
content-type: reference
discoiquuid: 4c4a7bc4-3fb1-44c1-823f-d789790f5e06
legacypath: /content/docs/en/aem/6-0/develop/mobile/groupfilters
exl-id: abbbf606-aff2-44b4-b16e-ceb54997115f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 90%

---

# Erstellen von Gerätegruppenfiltern{#creating-device-group-filters}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md).

Erstellen Sie einen Gerätegruppenfilter, um eine Reihe von Gerätefunktionsanforderungen zu definieren. Erstellen Sie so viele Filter, wie Sie benötigen, um auf die erforderlichen Gruppen von Gerätefunktionen zu zielen.

Entwerfen Sie Ihre Filter so, dass Sie Kombinationen von ihnen verwenden können, um die Gruppen von Funktionen zu definieren. In der Regel gibt es eine Überlappung der Funktionen verschiedener Gerätegruppen. Daher könnten Sie einige Filter mit mehreren Gerätegruppendefinitionen verwenden.

Nachdem Sie einen Filter erstellt haben, können Sie ihn in der [Gruppenkonfiguration](/help/sites-developing/mobile.md#creating-a-device-group) verwenden.

## Die Filter-Java-Klasse {#the-filter-java-class}

Ein Gerätegruppenfilter ist eine OSGi-Komponente, die die Schnittstelle [com.day.cq.wcm.mobile.api.device.DeviceGroupFilter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/mobile/api/device/DeviceGroupFilter.html) implementiert. Bei der Bereitstellung stellt die Implementierungsklasse einen Filterservice bereit, der für Gerätegruppenkonfigurationen verfügbar ist.

Die in diesem Artikel beschriebene Lösung verwendet das Apache Felix Maven-SCR-Plug-in, um die Entwicklung von Komponenten und Diensten zu erleichtern. Daher verwendet die Beispiel-Java-Klasse die `@Component`und `@Service` Anmerkungen. Die Klasse hat die folgende Struktur:

```java
package com.adobe.example.myapp;

import java.util.Map;

import com.day.cq.wcm.mobile.api.device.DeviceGroup;
import com.day.cq.wcm.mobile.api.device.DeviceGroupFilter;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

@Component(metatype = false)
@Service 
public class myDeviceGroupFilter implements DeviceGroupFilter {
 
       public String getDescription() {
  return null;
 }

 public String getTitle() { 
  return null;
 }

 public boolean matches(DeviceGroup arg0, String arg1, Map arg2) { 
  return false;
 }

}
```

Sie müssen Code für die folgenden Methoden angeben:

* getDescription: Gibt die Filterbeschreibung zurück. Die Beschreibung wird im Konfigurationsdialogfeld „Gerätegruppe“ angezeigt.
* getTitle: Gibt den Namen des Filters zurück. Der Name wird angezeigt, wenn Sie Filter für die Gerätegruppe auswählen.
* matches: Legt fest, ob das Gerät über die erforderlichen Funktionen verfügt.

### Bereitstellung des Filternamens und der Beschreibung {#providing-the-filter-name-and-description}

Die `getTitle`- und `getDescription`-Methoden geben jeweils den Filternamen und die Beschreibung zurück. Der folgende Code zeigt die einfachste Implementierung:

```java
public String getDescription() {
    return "An example device group filter";
}

public String getTitle() { 
 return "myFilter";
}
```

Feste Programmierung des Namens und des Beschreibungtextes ist ausreichend für einsprachige Authoring-Umgebungen. Ziehen Sie in Betracht, die Strings für mehrsprachige Verwendung zu externalisieren oder das Ändern von Strings zu aktivieren, ohne den Quellcode erneut zu kompilieren.

### Bewertung gegen Filterkriterien {#evaluating-against-filter-criteria}

Die `matches`-Funktion gibt `true` zurück, wenn die Gerätefunktionen alle Filterkriterien erfüllen. Werten Sie die in den Methodenargumenten bereitgestellten Informationen aus, um festzustellen, ob das Gerät zur Gruppe gehört. Die folgenden Werte werden als Argumente bereitgestellt:

* Ein DeviceGroup-Objekt
* Der Name des Benutzeragenten
* Ein Map-Objekt, das die Gerätefunktionen enthält. Die Map-Schlüssel sind die Namen der WURFL™ -Funktionalität und die Werte sind die entsprechenden Werte aus der WURFL™ -Datenbank.

Die Schnittstelle[ com.day.cq.wcm.mobile.api.devicespecs.DeviceSpecsConstants](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/mobile/api/device/DeviceGroupFilter.html) enthält eine Teilmenge der WURFL™ -Fähigkeitsnamen in statischen Feldern. Verwenden Sie diese Feldkonstanten als Schlüssel beim Abrufen von Werten aus der Karte der Gerätefunktionen.

Zum Beispiel bestimmt das folgende Codebeispiel, ob das Gerät CSS unterstützt:

```xml
boolean cssSupport = true;
cssSupport = NumberUtils.toInt(capabilities.get(DeviceSpecsConstants.DSPEC_XHTML_SUPPORT_LEVEL)) > 1;
```

Die `org.apache.commons.lang.math` -Paket bietet die `NumberUtils` -Klasse.

>[!NOTE]
>
>Stellen Sie sicher, dass die WURFL™ -Datenbank, die für AEM bereitgestellt wird, die Funktionen enthält, die Sie als Filterkriterien verwenden. (Siehe [Geräteerkennung](/help/sites-developing/mobile.md#server-side-device-detection).)

### Beispielfilter für Bildschirmgröße {#example-filter-for-screen-size}

Die folgende Beispiel-Implementierung von DeviceGroupFilter bestimmt, ob die physische Größe des Geräts die Mindestanforderungen erfüllt. Dieser Filter soll der Touch-Gerätegruppe Granularität verleihen. Die Größe der Schaltflächen in der Anwendungsoberfläche sollte unabhängig von der physischen Bildschirmgröße gleich sein. Die Größe von anderen Elementen, z. B. Text, kann variieren. Der Filter ermöglicht die dynamische Auswahl eines bestimmten CSS, das die Größe der Benutzeroberflächenelemente steuert.

Dieser Filter wendet Größenkriterien auf die `physical_screen_height` und `physical_screen_width` WURFL™-Eigenschaftsnamen.

```java
package com.adobe.example.myapp;

import java.util.Map;

import com.day.cq.wcm.mobile.api.device.DeviceGroup;
import com.day.cq.wcm.mobile.api.device.DeviceGroupFilter;

import org.apache.commons.lang.math.NumberUtils;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

@Component(metatype = false)
@Service
@SuppressWarnings("unused")
public class ScreenSizeLarge implements DeviceGroupFilter {
    private int len=400;
    private int wid=200;
    public String getDescription() {

        return "Requires the physical size of the screen to have minimum dimensions " + len + "x" + wid+".";
    }

    public String getTitle() {
        return "Screen Size Large ("+len + "x" + wid+")";
    }

    public boolean matches(DeviceGroup deviceGroup, String userAgent,
            Map<String, String> deviceCapabilities) {

        boolean longEnough=true;
        boolean wideEnough=false;
        int dimension1=NumberUtils.toInt(deviceCapabilities.get("physical_screen_height"));
        int dimension2=NumberUtils.toInt(deviceCapabilities.get("physical_screen_width"));
        if(dimension1>dimension2){
            longEnough=dimension1>=len;
            wideEnough=dimension2>=wid;
        }else{
            longEnough=dimension2>=len;
            wideEnough=dimension1>=wid;
        }

        return longEnough && wideEnough;
    }
}
```

Der Stringwert, den die getTitle-Methode in der Dropdown-Liste der Gerätegruppeneigenschaften zurückgibt.

![filteraddtogroup](assets/filteraddtogroup.png)

Die Stringwerte, die die getTitle- und getDescription-Methoden zurückgeben, sind am unteren Rand der Zusammenfassungsseite der Gerätegruppe enthalten.

![filterdescription](assets/filterdescription.png)

### Die Maven POM-Datei {#the-maven-pom-file}

Der folgende POM-Code ist nützlich, wenn Sie Maven zum Erstellen Ihrer Anwendungen verwenden. Das POM verweist auf mehrere erforderliche Plug-ins und Abhängigkeiten.

**Plug-ins:**

* Apache Maven Compiler-Plug-in: Kompiliert Java-Klassen aus dem Quellcode
* Apache Felix Maven Bundle Plug-in: Erstellt das Bundle und das Manifest
* Apache Felix Maven SCR-Plug-in: Erstellt die Komponentendeskriptordatei und konfiguriert den Manifestheader der Servicekomponente

**Abhängigkeiten:**

* `cq-wcm-mobile-api-5.5.2.jar`: Stellt die Schnittstellen DeviceGroup und DeviceGroupFilter bereit.

* `org.apache.felix.scr.annotations.jar`: Stellt die Anmerkungen zu Komponenten und Diensten bereit.

Die DeviceGroup- und DeviceGroupFilter-Schnittstellen sind im Day Communique 5 WCM Mobile API-Bundle enthalten. Die Felix-Anmerkungen sind im Apache Felix Declarative Services-Bundle enthalten. Sie können diese JAR-Datei über das öffentliche Adobe-Repository beziehen.

Zum Zeitpunkt der Erstellung ist 5.5.2 die Version des WCM Mobile API-Bundles, das in der neuesten Version von AEM enthalten ist. Verwenden Sie die Adobe-Webkonsole ([http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles)), um sicherzustellen, dass es sich um die Paketversion handelt, die in Ihrer Umgebung bereitgestellt wird.

**POM:**(Ihr POM wird eine andere groupId und Version verwenden.)

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
        xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
      <modelVersion>4.0.0</modelVersion>
      <groupId>com.adobe.example.myapp</groupId>
      <artifactId>devicefilter</artifactId>
      <version>0.0.1-SNAPSHOT</version>
      <name>my app device filter</name>
      <url>https://dev.day.com/docs/en/cq/current.html</url>
  <packaging>bundle</packaging>
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
         <groupId>com.day.cq.wcm</groupId>
         <artifactId>cq-wcm-mobile-api</artifactId>
         <version>5.5.2</version>
         <scope>provided</scope>
     </dependency>
     <dependency>
        <groupId>org.apache.felix</groupId>
        <artifactId>org.apache.felix.scr.annotations</artifactId>
        <version>1.6.0</version>
        <scope>compile</scope>
    </dependency>
</dependencies>
</project>
```

Fügen Sie das Profil, das im Abschnitt [Abrufen des Inhaltspaket-Maven-Plugins](/help/sites-developing/vlt-mavenplugin.md) enthalten ist, zu Ihrer Maven-Einstellungsdatei hinzu, um das öffentliche Adobe-Repository zu verwenden.
