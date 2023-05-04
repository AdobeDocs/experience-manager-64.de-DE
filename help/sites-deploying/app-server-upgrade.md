---
title: Schritte zur Aktualisierung von Installationen auf Anwendungs-Servern
seo-title: Upgrade Steps for Application Server Installations
description: Erfahren Sie, wie Sie Instanzen von AEM aktualisieren, die über Anwendungsserver bereitgestellt werden.
seo-description: Learn how to upgrade instances of AEM that are deployed via Application Servers.
uuid: df3fa715-af4b-4c81-b2c5-130fbc82f395
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: c427c8b6-eb94-45fa-908f-c3d5a337427d
feature: Upgrading
exl-id: 1c72093e-82c8-49ad-bd3c-d61904aaab28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 36%

---

# Schritte zur Aktualisierung von Installationen auf Anwendungs-Servern{#upgrade-steps-for-application-server-installations}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Abschnitt wird das Verfahren beschrieben, das befolgt werden muss, um AEM für Anwendungsserverinstallationen zu aktualisieren.

Alle Beispiele in diesem Verfahren verwenden JBoss als Anwendungsserver und implizieren, dass Sie bereits über eine funktionierende Version von AEM verfügen. In dieser Anleitung wird die Aktualisierung von **AEM 5.6 auf 6.3** beschrieben.

1. Starten Sie zunächst JBoss. In den meisten Fällen können Sie dies tun, indem Sie die `standalone.sh` Startskript, indem Sie diesen Befehl über das Terminal ausführen:

   ```shell
   jboss-install-folder/bin/standalone.sh
   ```

1. Wenn AEM 5.6 bereits bereitgestellt ist, überprüfen Sie, ob die Bundles ordnungsgemäß funktionieren, indem Sie Folgendes ausführen:

   ```shell
   wget https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Heben Sie anschließend die Bereitstellung AEM 5.6 auf:

   ```shell
   rm jboss-install-folder/standalone/deployments/cq.war
   ```

1. Beenden Sie JBoss.

1. Migrieren Sie das Repository nun mithilfe des crx2oak-Migrations-Tools:

   ```shell
   java -jar crx2oak.jar crx-quickstart/repository/ crx-quickstart/oak-repository
   ```

   >[!NOTE]
   >
   >In diesem Beispiel ist oak-repository der temporäre Ordner, in dem sich das neu konvertierte Repository befindet. Bevor Sie diesen Schritt durchführen, stellen Sie sicher, dass Sie über die neueste crx2oak.jar-Version verfügen.

1. Löschen Sie die erforderlichen Eigenschaften in der Datei sling.properties folgendermaßen:

   1. Öffnen Sie die unter `crx-quickstart/launchpad/sling.properties` gespeicherte Datei.
   1. Entfernen Sie die folgenden Eigenschaften und speichern Sie die Datei:

      1. `sling.installer.dir`
      1. `felix.cm.dir`
      1. `granite.product.version`
      1. `org.osgi.framework.system.packages`
      1. `osgi-core-packages`
      1. `osgi-compendium-services`
      1. `jre-*`
      1. `sling.run.mode.install.options`

1. Entfernen Sie nicht mehr benötigte Dateien und Ordner. Die Elemente, die Sie speziell entfernen müssen, sind:

   * Die **launchpad/startup-Ordner**. Sie können ihn löschen, indem Sie am Terminal den folgenden Befehl ausführen: `rm -rf crx-quickstart/launchpad/startup`
   * Die Datei **base.jar**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`
   * Die Datei **BootstrapCommandFile_timestamp.txt**: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

1. Kopieren Sie den neu migrierten Segmentspeicher an den richtigen Speicherort:

   ```shell
   mv crx-quickstart/oak-repository/segmentstore crx-quickstart/repository/segmentstore
   ```

1. Kopieren Sie auch den Datenspeicher:

   ```shell
   mv crx-quickstart/repository/repository/datastore crx-quickstart/repository/datastore
   ```

1. Als Nächstes müssen Sie den Ordner erstellen, der die OSGi-Konfigurationen enthält, die mit der neuen aktualisierten Instanz verwendet werden. Genauer gesagt muss ein Ordner mit dem Namen install unter erstellt werden. **crx-quickstart**.

1. Erstellen Sie nun den Knotenspeicher und den Datenspeicher, der mit AEM 6.3 verwendet werden soll. Erstellen Sie dazu zwei Dateien mit den folgenden Namen unter **crx-quickstart\install**:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`

   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Diese beiden Dateien konfigurieren AEM so, dass ein TarMK-Knotenspeicher und ein Dateidatenspeicher verwendet werden.

1. Bearbeiten Sie die Konfigurationsdateien, damit sie einsatzbereit sind. Im Einzelnen:

   * Fügen Sie die folgende Zeile zu **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**:

      `customBlobStore=true`

   * Fügen Sie dann die folgenden Zeilen zu **org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**:

      ```
      path=./crx-quickstart/repository/datastore
       minRecordLength=4096
      ```

1. Entfernen Sie den crx2-Ausführungsmodus, indem Sie Folgendes ausführen:

   ```shell
   find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \
   ```

1. Ändern Sie nun die Ausführungsmodi in der WAR-Datei für AEM 6.3. Erstellen Sie dafür zunächst einen temporären Ordner, in dem die WAR-Datei für AEM 6.3 gespeichert wird. Der Name des Ordners in diesem Beispiel lautet **temp**. Extrahieren Sie nach dem Kopieren der WAR-Datei deren Inhalte im temporären Ordner:

   ```shell
   jar xvf aem-quickstart-6.3.0.war
   ```

1. Wechseln Sie nach dem Extrahieren der Inhalte zum Ordner **WEB-INF** und bearbeiten Sie die Datei , um die Ausführungsmodi zu ändern. `web.xml` Suchen Sie nach der Zeichenfolge `sling.run.modes`, um ihre Position in der XML-Datei zu bestimmen. Wenn Sie sie gefunden haben, ändern Sie die Ausführungsmodi in der nächsten Code-Zeile, die standardmäßig auf author gesetzt ist:

   ```shell
   <param-value >author</param-value>
   ```

1. Ändern Sie den obigen Autorenwert und legen Sie die Ausführungsmodi auf Folgendes fest: author,crx3,crx3tar Der endgültige Codeblock sollte wie folgt aussehen:

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. Erstellen Sie die JAR-Datei erneut mit den geänderten Inhalten:

   ```shell
   jar cvf aem62.war
   ```

1. Stellen Sie schließlich die neue WAR-Datei bereit:

   ```shell
   cp temp/aem62.war jboss-install-folder/standalone/deployments/aem61.war
   ```
