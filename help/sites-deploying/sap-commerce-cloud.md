---
title: SAP Commerce Cloud
seo-title: SAP Commerce Cloud
description: Erfahren Sie, wie Sie eCommerce mit SAP Commerce Cloud bereitstellen.
seo-description: Learn how to deploy eCommerce with SAP Commerce Cloud.
uuid: a16ae42b-9c33-4da8-a130-52b72a779ec7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 44dfa10f-497e-473f-95d4-8dccae7ebf8e
pagetitle: Deploying eCommerce with SAP Commerce Cloud
feature: Commerce Integration Framework
exl-id: 71d0a249-8ad1-416e-ad78-d651b413e5c3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 54%

---

# SAP Commerce Cloud{#sap-commerce-cloud}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Diese Seite enthält Links zur hybris-Website. Für bestimmte Seiten benötigen Sie ein Konto, um sich anzumelden.

## Bereitstellen von eCommerce mit SAP Commerce Cloud {#deploying-ecommerce-with-sap-commerce-cloud}

>[!NOTE]
>
>Zur Veranschaulichung der folgenden Bereitstellung wird dieser Demo-Katalog verwendet:
>
>`Geometrixx Outdoors Site English (US)`

Durch die Implementierung der [erforderlichen eCommerce-Pakete](#packages-needed-for-ecommerce-with-hybris) wird der volle Funktionsumfang des eCommerce-Frameworks zusammen mit einer Referenzimplementierung der eCommerce-Funktionen bereitgestellt, die im Rahmen einer Hybris-Implementierung (einschließlich Demo-Katalog) verfügbar sind.

Dies ist in der englischen (US) Version (`/content/geometrixx-outdoors/en_US`) der Geometrixx Outdoors-Website erhältlich:

* [Produktinformationen](#productinformationwithcolorvariants) (mit Farbvarianten sofern zutreffend)

* [Übersicht über den Warenkorbinhalt ](#shoppingcartcontentoverview)
* [Kundenregistrierung](#customersignup) und [Kundenanmeldung](#customersignin) 

* [Zugriff auf die Hybris-Verwaltungskonsole](#accesstothehybrismanagementconsole)

### Technische Anforderungen – Hybris-Server {#technical-requirements-hybris-server}

Die Hybris-Erweiterung des eCommerce-Integrations-Frameworks wurde aktualisiert und unterstützt jetzt Hybris 5 (standardmäßig), während die Rückwärtskompatibilität mit [Hybris 4](/help/sites-developing/sap-commerce-cloud.md#developing-for-hybris) ebenfalls gewährleistet ist.

>[!NOTE]
>
>* Unterstützt bis zu hybris 6.4 mit OCC-Version 2.
>* Sie benötigen Java 7 für den [Hybris 5-Server](https://www.hybris.com/de/architecture-technology).
>* Das hybris-Add-on, das [Telco Accelerator](https://www.hybris.com/de/products/telecommunication), wird von der AEM-Erweiterung nicht unterstützt.
>


### Für eCommerce mit Hybris benötigte Pakete {#packages-needed-for-ecommerce-with-hybris}

Zum Installieren der eCommerce-Funktion benötigen Sie Folgendes:

* Ihren Hybris-Server
* AEM eCommerce-Framework:

   * Dies ist Teil einer standardmäßigen AEM.

* AEM Geometrixx-Package:

   * `cq-geometrixx-all-pkg`

* AEM Hybris-Inhaltspakete:

   * `cq-hybris-content-6.3.2`
   * Hybris-spezifische API-Implementierung
   * `cq-geometrixx-hybris-content-6.3.2`
   * Eine Referenzimplementierung zur Veranschaulichung der Funktionsweise von Hybris (`geometrixx-outdoors/en_US`)

### Installation von eCommerce mit hybris {#installation-of-ecommerce-with-hybris}

Zur Installation einer vollständigen Konfiguration (unter Verwendung des Demonstrationskatalogs, Geometrixx Outdoors) sind folgende Schritte erforderlich:

1. [Installieren Sie AEM](/help/sites-deploying/deploy.md).
1. Installieren des Geometrixx all-Packages

   1. ` [cq-geometrixx-all-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq60/product/cq-geometrixx-all-pkg)`

1. Installieren Sie die Demo-Inhaltspakete mithilfe von [Package Manager](/help/sites-administering/package-manager.md):

   1. ` [cq-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-hybris-content)`
   1. ` [cq-geometrixx-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-geometrixx-hybris-content)`

1. [Herunterladen und Erstellen Ihres hybris-Servers](#download-and-build-your-hybris-server).
1. Erstellen Sie Ihren Katalog in Ihrer eCommerce-Engine:

   1. [Einrichten des Geometrixx Outdoor Store](#setup-the-geometrixx-outdoors-store).

1. [Autor](/help/sites-authoring/qg-page-authoring.md) alle zusätzlichen Seiten, die Sie in AEM benötigen.

>[!CAUTION]
>
>Die Verwendung des hybris-Servers erfordert eine separate hybris-Lizenz.

>[!NOTE]
>
>Für Entwickler ist auch eine [API-Dokumentation](/help/sites-developing/ecommerce.md#api-documentation) zum Herunterladen verfügbar.

### Herunterladen und Erstellen Ihres hybris-Servers {#download-and-build-your-hybris-server}

Die Schritte in diesem Verfahren werden den hybris-Server herunterladen und erstellen. Außerdem werden die ersten Konfigurationen vorgenommen, die für die Verbindungen zwischen hybris und cq erforderlich sind. Die Erweiterung kann dann mit den Standardeinstellungen verwendet werden.

>[!CAUTION]
>
>Hybris-Versionen vor 5.5.1 werden nicht unterstützt.

>[!NOTE]
>
>Dazu muss [Groovy](https://groovy-lang.org/) auf Ihrem System installiert sein.

1. Laden Sie die **Hybris Commerce Suite**-Distribution von der Hybris-Download-Website herunter.

   >[!CAUTION]
   >
   >Sie benötigen ein Konto (von hybris), um darauf zugreifen zu können.

1. Entpacken Sie die Verteilungsdatei an den erforderlichen Speicherort (siehe &lt;hybris-root-directory>).
1. Führen Sie in der Befehlszeile Folgendes aus:

   ```shell
   cd <hybris-root-directory>/bin/platform
   . ./setantenv.sh
   ant clean all 
   cd ../..
   ```

   >[!NOTE]
   >
   >Beim Ausführen:
   >
   >`ant clean all`
   >
   >Drücken Sie bei Bedarf `Return`.

1. Laden Sie die folgenden Dateien in den Stammordner Ihrer dekomprimierten Hybris-Distributionsdatei herunter:

   ```
       <hybris-root-directory>
   ```


[Datei abrufen](assets/setup.groovy)

   >[!NOTE]
   >
   >Verwenden Sie für Hybris 5.6.0 und höher folgende setup.groovy.

   5.6.0 und höher

[Datei abrufen](assets/setup-1.groovy)

1. Geben Sie in der Befehlszeile Folgendes ein, um:

   * die Konfiguration des Hybris-Servers zu aktualisieren (gemäß der Anforderung der Erweiterung); 
   * den Hybris-Server mit der geänderten Konfiguration einzurichten; 
   * Server starten

   ```shell
   groovy setup.groovy
   cd bin/platform
   ant clean all
   sh hybrisserver.sh
   ```

   >[!NOTE]
   >
   >Je nach System kann es mehrere Minuten dauern, bis einige dieser Schritte abgeschlossen sind.

1. Navigieren Sie in Ihrem Browser zum **hybris Administration Console** unter:

   [http://localhost:9002](http://localhost:9002)

1. Klicken Sie auf **Initialize** und bestätigen Sie dann die Initialisierung (da dadurch vorhandene Daten gelöscht werden).

   Der Fortschritt ist in der Konsole zu sehen und nach Fertigstellung wird `FINISHED` angezeigt.

   >[!NOTE]
   >
   >Abhängig von Ihrem System kann dies mehrere Minuten dauern.

### Einrichten des Geometrixx Outdoors Store {#setup-the-geometrixx-outdoors-store}

Mit diesem Verfahren wird das Demo-Geschäft Geometrixx Online hochgeladen und konfiguriert.

1. Starten Sie Ihre hybris-Instanz. Führen Sie in der Befehlszeile Folgendes aus:

   ```shell
   cd <hybris-root-directory>/bin/platform
   sh hybrisserver.sh
   ```

1. Navigieren Sie in Ihrem Browser zum **Hybris-Verwaltungskonsole** unter:

   [http://localhost:9002/hmc/hybris](http://localhost:9002/hmc/hybris)

1. Navigieren Sie in der Seitenleistennavigation zu **System** und **Instrumente**. Wählen Sie anschließend **Import** , um **Assistent: CSV-Import** Fenster.
1. Im **Konfiguration** Registerkarte, **Hochladen** die folgenden **Importdatei**:

[Datei abrufen](assets/geometrixx-outdoors-export.csv)

1. Definieren Sie **Locale Setting** folgendermaßen:

   `en_US - English (United States)`

1. Öffnen Sie die **Ressourcen** Registerkarte.
1. **Hochladen** die folgenden **Media-Zip**:

[Datei abrufen](assets/geometrixx-outdoors-images.zip)

1. Klicken Sie auf **Start**, um die angegebenen Dateien zu importieren. Auf der Registerkarte **Result** werden etwaige Protokolleinträge angezeigt.

1. Klicken Sie auf **Done**, um das Importfenster zu schließen.

1. Wählen Sie in der Sidebar **System**, dann **Tools** und schließlich **Import** aus. 

1. **Laden** Sie die folgende **Importdatei** hoch:

[Datei abrufen](assets/base-store.csv)

   Verwenden Sie für Hybris 5.7 Folgendes:

[Datei abrufen](assets/base-store-5_7.csv)

1. Definieren Sie **Locale Setting** folgendermaßen:

   `en_US - English (United States)`

1. Klicken Sie auf **Start**, um die angegebenen Dateien zu importieren. Auf der Registerkarte **Result** werden etwaige Protokolleinträge angezeigt.

1. Klicken Sie auf **Done**, um das Importfenster zu schließen.

1. Im Produkt-Cockpit können Sie sich jetzt die importierten Kataloge und Produkte ansehen:

   [http://localhost:9002/productcockpit](http://localhost:9002/productcockpit)
