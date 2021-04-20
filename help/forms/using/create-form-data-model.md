---
title: '"Schulung: Formulardatenmodell erstellen "'
seo-title: Formulardatenmodell erstellen - Schulung
description: Mit dem AEM Forms-Datenintegrationsmodul können Sie ein Formulardatenmodell aus unterschiedlichen Back-End-Datenquellen wie AEM-User-Profil, RESTful-Webservices, SOAP-basierten Webdiensten, OData-Diensten und relationalen Datenbanken erstellen. Erfahren Sie, wie Sie die MySQL-Datenbank als Datenquelle konfigurieren, ein Formulardatenmodell erstellen, konfigurieren und testen.
seo-description: Mit dem AEM Forms-Datenintegrationsmodul können Sie ein Formulardatenmodell aus unterschiedlichen Back-End-Datenquellen wie AEM-User-Profil, RESTful-Webservices, SOAP-basierten Webdiensten, OData-Diensten und relationalen Datenbanken erstellen. Erfahren Sie, wie Sie die MySQL-Datenbank als Datenquelle konfigurieren, ein Formulardatenmodell erstellen, konfigurieren und testen.
page-status-flag: de-activated
uuid: 81d40278-4df9-4b61-93ad-eae2fce0a35c
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 31e97723-d637-4a18-999d-36e00fbd031a
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 72%

---


# Schulung: Formulardatenmodell erstellen  {#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Diese Schulung ist ein Schritt in der Serie [Erstellen Sie Ihr erstes adaptives Formular](/help/forms/using/create-your-first-adaptive-form.md). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

## Über die Schulung {#about-the-tutorial}

Mit dem AEM Forms-Datenintegrationsmodul können Sie ein Formulardatenmodell aus unterschiedlichen Back-End-Datenquellen wie AEM-User-Profil, RESTful-Webservices, SOAP-basierten Webdiensten, OData-Diensten und relationalen Datenbanken erstellen. Sie können Datenmodellobjekte und -Dienste in einem Formulardatenmodell konfigurieren und einem adaptiven Formular zuordnen. Adaptive Formularfelder sind an Datenmodellobjekteigenschaften gebunden. Mit den Diensten können Sie das adaptive Formular vorab befüllen und gesendete Formulardaten zurück an das Datenmodellobjekt schreiben.

Weitere Informationen zum Formulardatenmodell und zur Formulardatenintegration finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

Diese Schulung führt Sie durch die Schritte zum Vorbereiten, Erstellen, Konfigurieren und Zuordnen eines Formulardatenmodells mit einem adaptiven Formular. Am Ende dieser Schulung können Sie Folgendes:

* [Konfigurieren der MySQL-Datenbank als Datenquelle](#config-database)
* [Erstellen eines Formulardatenmodells mit der MySQL-Datenbank](#create-fdm)
* [Konfigurieren eines Formulardatenmodells](#config-fdm)
* [Testen eines Formulardatenmodells](#test-fdm)

Das Formulardatenmodell sieht etwa wie folgt aus:

![form-data-model_l](assets/form-data-model_l.png)

**A.** Konfigurierte Datenquellen  **B.** Datenquellen-Schema  **C.** Verfügbare Dienste  **D.** Datenmodellobjekte  **E.** Konfigurierte Dienste

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* MySQL-Datenbank mit Beispieldaten wie im Abschnitt „Voraussetzungen“ von [Erstellen Sie Ihr erstes adaptives Formular ](/help/forms/using/create-your-first-adaptive-form.md) beschrieben
* OSGi-Bundle für den JDBC-Treiber für MySQL, wie unter [Bundling des JDBC-Datenbanktreibers](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver) beschrieben
* Adaptives Formular, wie im ersten Lernprogramm [Erstellen eines adaptiven Formulars](/help/forms/using/create-adaptive-form.md) beschrieben

## Schritt 1: Konfigurieren der MySQL-Datenbank als Datenquelle {#config-database}

Sie können verschiedene Arten von Datenquellen konfigurieren, um ein Formulardatenmodell zu erstellen. Für diese Schulung werden wir die MySQL-Datenbank, die Sie konfiguriert und mit Beispieldaten befüllt haben, konfigurieren. Informationen zu anderen unterstützten Datenquellen und deren Konfiguration finden Sie unter [AEM Forms-Datenintegration](/help/forms/using/data-integration.md).

Gehen Sie folgendermaßen vor, um Ihre MySQL-Datenbank zu konfigurieren:

1. Installieren Sie den JDBC-Treiber für die MySQL-Datenbank als OSGi-Bundle:

   1. Melden Sie sich bei der AEM Forms-Autoreninstanz als Administrator an und wechseln Sie zu den AEM-Webkonsolen-Paketen. Die Standard-URL lautet [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).

   1. Tippen Sie auf **Installieren/Aktualisieren**. Ein Dialogfeld **Pakete hochladen/installieren** wird angezeigt.

   1. Tippen Sie auf **Datei auswählen**, um das OSBi-Paket für den MySQL-JDBC-Treiber auszuwählen. Wählen Sie **Beginn-Bundle** und **Pakete aktualisieren** und tippen Sie auf **Installieren oder Aktualisieren**. Stellen Sie sicher, dass der JDBC-Treiber der Oracle Corporation für MySQL aktiv ist. Der Treiber wird installiert.

1. Konfigurieren der MySQL-Datenbank als Datenquelle:

   1. Wechseln zur AEM-Webkonsole unter [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
   1. Suchen Sie die Konfiguration **Apache Sling Connection Pooled DataSource**. Tippen Sie, um die Konfiguration im Bearbeitungsmodus zu öffnen.
   1. Geben Sie im Konfigurationsdialog die folgenden Details an:

      * **Datenquellenname:** Sie können einen beliebigen Namen angeben, beispielsweise **WeRetailMySQL**.
      * **Name der DataSource-Diensteigenschaft**: Geben Sie den Namen der Diensteigenschaft an, die den DataSource-Namen enthält. Er wird beim Registrieren der Datenquelleninstanz als OSGi-Dienst angegeben. Zum Beispiel: **datasource.name**.
      * **JDBC-Treiberklasse**: Geben Sie den Java-Klassennamen des JDBC-Treibers an. Geben Sie für die MySQL-Datenbank **com.mysql.jdbc.Driver** an.
      * **JDBC-Verbindungs-URI**: Geben Sie die Verbindungs-URL der Datenbank an. Für eine MySQL-Datenbank, die auf Port 3306 ausgeführt wird, und für Schema, das über Ethernet verfügt, lautet die URL: `jdbc:mysql://[server]:3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **Benutzername:** Benutzername der Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.
      * **Kennwort:** Kennwort für die Datenbank. Es ist erforderlich, den JDBC-Treiber zu aktivieren, um eine Verbindung mit der Datenbank herzustellen.
      * **Test on Borrow:** Aktivieren Sie die Option  **Test on** Borrowoption.
      * **Test on Return:** Aktivieren Sie die Option **Test on Return.**
      * **Validation Query:** Geben Sie eine SQL SELECT-Abfrage ein, damit Verbindungen aus dem Pool validiert werden. Die Abfrage muss mindestens eine Zeile zurückgeben. Beispiel: **Wählen Sie &amp;ast; von customerdetails**.
      * **Transaktions-Isolierung**: Setzen Sie den Wert auf **READ_COMMITTED**.

      Belassen Sie andere Eigenschaften mit den Standardwerten [und tippen Sie auf **Speichern**.](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html)
   Eine Konfiguration ähnlich der folgenden wird erstellt.

   ![relational-database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## Schritt 2: Erstellen eines Formulardatenmodells {#create-fdm}

AEM Forms bietet eine intuitive Benutzeroberfläche zum Erstellen eines Formulardatenmodells [aus konfigurierten Datenquellen. ](data-integration.md) Sie können mehrere Datenquellen in einem Formulardatenmodell verwenden. Für unseren Anwendungsfall verwenden wir die konfigurierte MySQL-Datenquelle.

Gehen Sie folgendermaßen vor, um ein Formulardatenmodell zu erstellen:

1. Navigieren Sie in AEM Autoreninstanz zu **Forms** > **Datenintegration** s.
1. Tippen Sie auf **Erstellen** > **Formulardatenmodell**.
1. Geben Sie im Dialogfeld „Formulardatenmodell erstellen“ einen **Namen** für das Formulardatenmodell ein. Zum Beispiel **customer-shipping-billing-details**. Tippen Sie auf **Weiter**.
1. Im Bildschirm „Datenquelle auswählen“ werden alle konfigurierten Datenquellen angezeigt. Wählen Sie **WeRetailMySQL**-Datenquelle und tippen Sie auf **Erstellen**.

   ![data-source-selection](assets/data-source-selection.png)

Das Formulardatenmodell **customer-shipping-billing-details** wird erstellt.

## Schritt 3: Konfigurieren eines Formulardatenmodells {#config-fdm}

Zum Konfigurieren eines Formulardatenmodells gehört Folgendes:

* Hinzufügen von Datenmodellobjekten und Diensten
* Konfigurieren von Lese- und Schreibdiensten für Datenmodellobjekte

Gehen Sie folgendermaßen vor, um das Formulardatenmodell zu konfigurieren:

1. Navigieren Sie auf dem AEM-Server zu **Formulare > Datenintegrationen**.  Die Standard-URL lautet [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. Das zuvor erstellte Formulardatenmodell **customer-shipping-billing-details** ist hier aufgeführt. Öffnen Sie es im Bearbeitungsmodus.

   Die ausgewählte Datenquelle **WeRetailMySQL** wird im Formulardatenmodell konfiguriert.

   ![default-fdm](assets/default-fdm.png)

1. Erweitern Sie den WeRailMySQL-Datenquellenbaum. Wählen Sie die folgenden Datenmodellobjekte und -dienste aus dem Schema **weretail** > **customerdetails** zum Formulardatenmodell aus:

   * **Datenmodellobjekte**:

      * id
      * name
      * shippingAddress
      * city
      * state
      * zipcode
   * **Dienste:**

      * get
      * Aktualisieren

   Tippen Sie auf **Ausgewählte hinzufügen**, um dem Formulardatenmodell ausgewählte Datenmodellobjekte und Dienste hinzuzufügen.

   ![weretail-Schema](assets/weretail-schema.png)

   >[!NOTE]
   >
   >Die standardmäßigen get-, update- und insert-Dienste für JDBC-Datenquellen werden standardmäßig mit dem Formulardatenmodell bereitgestellt.

1. Konfigurieren Sie Lese- und Schreibdienste für Datenmodellobjekte.

   1. Wählen Sie das Datenmodellobjekt **customerdetails** und tippen Sie auf **Eigenschaften bearbeiten**.
   1. Wählen Sie aus dem Dropdown-Menü „Lesedienst“ **get.** Das Argument **id**, das der Primärschlüssel im Datenmodellobjekt des „customerdetails“ ist, wird automatisch hinzugefügt. Tippen Sie auf ![aem_6_3_edit](assets/aem_6_3_edit.png) und konfigurieren Sie das Argument wie folgt.

      ![read-default](assets/read-default.png)

   1. Wählen Sie ebenfalls **update** als Schreibdienst. Das Objekt **customerdetails** wird automatisch als Argument hinzugefügt. Das Argument ist wie folgt konfiguriert.

      ![write-default](assets/write-default.png)

      Fügen Sie das Argument **id** hinzu und konfigurieren Sie es wie folgt.

      ![id-arg](assets/id-arg.png)

   1. Tippen Sie auf **Fertig**, um die Eigenschaften des Datenmodellobjekts zu speichern. Tippen Sie dann auf **Speichern**, um das Formulardatenmodell zu speichern.

      Die Dienste **get** und **update** werden als Standarddienste für das Datenmodellobjekt hinzugefügt.

      ![data-model-object](assets/data-model-object.png)

1. Wechseln Sie zur Registerkarte **Dienste** und konfigurieren Sie die Dienste **get** und **update**.

   1. Wählen Sie den Dienst **get** und tippen Sie auf **Eigenschaften bearbeiten**. Das Dialogfeld „Eigenschaften“ wird geöffnet.
   1. Geben Sie im Dialogfeld „Eigenschaften bearbeiten“ Folgendes an:

      * **Titel**: Geben Sie den Titel des Dienstes an. Beispiel: Lieferadresse abrufen.
      * **Beschreibung**: Geben Sie eine Beschreibung an, die das detaillierte Funktionieren des Dienstes enthält. Beispiel:

         Dieser Dienst ruft Versandadresse und andere Kundendetails aus der MySQL-Datenbank ab

      * **Ausgabemodellobjekt**: Wählen Sie ein Schema mit Kundendaten. Beispiel:

         customerdetail Schema
      * **Array zurückgeben**: Deaktivieren Sie die Option **Array zurückgeben**.
      * **Argumente**: Wählen Sie das Argument mit dem Namen **ID**.

      Tippen Sie auf **Fertig**. Der Dienst zum Abrufen von Kundendaten aus der MySQL-Datenbank ist konfiguriert.

      ![shiiping-address-retrieve](assets/shiiping-address-retrieval.png)

   1. Wählen Sie den Dienst **update** und tippen Sie auf **Eigenschaften bearbeiten**. Das Dialogfeld „Eigenschaften“ wird geöffnet.

   1. Geben Sie im Dialogfeld „Eigenschaften bearbeiten“ Folgendes an:

      * **Titel**: Geben Sie den Titel des Dienstes an. Beispiel: Lieferadresse aktualisieren.

      * **Beschreibung**: Geben Sie eine Beschreibung an, die das detaillierte Funktionieren des Dienstes enthält. Beispiel:

         Dieser Dienst aktualisiert die Lieferadresse und die zugehörigen Felder in der MySQL-Datenbank

      * **Eingabemodellobjekt**: Wählen Sie ein Schema mit Kundendaten. Beispiel:

         customerdetail Schema

      * **Ausgabetyp**: Wählen Sie **BOOLEAN**.
      * **Argumente**: Wählen Sie das Argument mit dem Namen **ID** und **customerdetails**.

      Tippen Sie auf **Fertig**. Der Dienst **update** zum Aktualisieren von Kundendetails in der MySQL-Datenbank ist konfiguriert.

      ![shiiping-address-update](assets/shiiping-address-update.png)



Das Datenmodellobjekt und die Dienste im Formulardatenmodell sind konfiguriert. Sie können nun das Formulardatenmodell testen.

## Schritt 4: Testen eines Formulardatenmodells  {#test-fdm}

Sie können das Datenmodellobjekt und die Datendienste testen, um sicherzustellen, dass das Formulardatenmodell ordnungsgemäß konfiguriert ist.

Führen Sie folgende Schritte aus, um den Test durchzuführen:

1. Wechseln Sie auf die Registerkarte **Modell**, wählen Sie das Datenmodellobjekt **customerdetails** und tippen Sie auf **Modellobjekt testen**.
1. Wählen Sie im Fenster **Modell/Dienst testen** **Modellobjekt lesen** aus der Dropdown-Liste **Modell/Dienst auswählen** auswählen.
1. Geben Sie im Abschnitt **customerdetails** einen Wert für das Argument **id** in der konfigurierten MySQL-Datenbank an und tippen Sie auf **Testen**.

   Die Kundendetails, die der angegebenen ID zugeordnet sind, werden abgerufen und im Abschnitt **Ausgabe** angezeigt, wie unten gezeigt.

   ![test-read-model](assets/test-read-model.png)

1. In ähnlicher Weise können Sie das Schreibmodellobjekt und die Dienste testen.

   Im folgenden Beispiel aktualisiert der Aktualisierungsdienst die Adressdetails für die ID 7102715 in der Datenbank erfolgreich.

   ![test-write-model](assets/test-write-model.png)

   Wenn Sie nun den Lesemodelldienst für die ID 7107215 erneut testen, werden die aktualisierten Kundendetails abgerufen und angezeigt (siehe unten).

   ![read-updated](assets/read-updated.png)

