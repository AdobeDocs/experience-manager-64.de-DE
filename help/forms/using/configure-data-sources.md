---
title: Konfigurieren von Datenquellen
seo-title: Configure data sources
description: Erfahren Sie, wie Sie verschiedene Arten von Datenquellen konfigurieren und nutzen können, um Formulardatenmodelle zu erstellen.
seo-description: Learn how to configure different types of data sources and leverage to create form data models.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
feature: Form Data Model
exl-id: a8f200ac-cf9f-47b7-9856-e62aa8b229eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 69%

---

# Konfigurieren von Datenquellen {#configure-data-sources}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erfahren Sie, wie Sie verschiedene Arten von Datenquellen konfigurieren und nutzen können, um Formulardatenmodelle zu erstellen.

![](do-not-localize/data-integeration.png)

Mit der AEM Forms-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herzustellen. Die folgenden Datenquellen werden standardmäßig unterstützt. Es ist jedoch möglich, mit nur wenigen Anpassungen auch andere Datenquellen zu integrieren.

* Relationale Datenbanken: MySQL, Microsoft SQL Server, IBM DB2 und Oracle RDBMS
* AEM-Benutzerprofil 
* RESTful-Webservices
* SOAP-basierte Webservices
* OData-Services

Die Datenintegration unterstützt standardmäßig die Authentifizierungstypen OAuth2.0, Standardauthentifizierung sowie API-Schlüssel und ermöglicht die Implementierung benutzerdefinierter Authentifizierung für den Zugriff auf Webservices. RESTful-, SOAP-basierte und OData-Dienste werden in AEM-Cloud-Services, JDBC für relationale Datenbanken und der Connector für AEM-Profile dagegen in der AEM-Webkonsole konfiguriert.

## Konfigurieren relationaler Datenbanken {#configure-relational-database}

Sie können relationale Datenbanken mithilfe AEM Konfiguration der Web-Konsole konfigurieren. Gehen Sie folgendermaßen vor:

1. Wechseln Sie zur AEM-Web-Konsole unter `https://[server]:[host]/system/console/configMgr`.
1. Suchen nach **[!UICONTROL Apache Sling Connection Pooled DataSource]** Konfiguration. Tippen Sie, um die Konfiguration im Bearbeitungsmodus zu öffnen.
1. Geben Sie im Konfigurationsdialogfeld die Details für die Datenbank an, die Sie konfigurieren möchten, z. B.:

   * Name der Datenquelle
   * Datenquellendienst-Eigenschaft, die den Namen der Datenquelle speichert
   * Java-Klassenname für den JDBC-Treiber
   * JDBC-Verbindungs-URI
   * Benutzername und Kennwort zum Herstellen der Verbindung mit dem JDBC-Treiber

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie vertrauliche Informationen wie Passwörter verschlüsseln, bevor Sie die Datenquelle konfigurieren. Verschlüsseln:
   >
   >1. Rufen Sie `https://[server]:[port]/system/console/crypto` auf.
   >1. Im **[!UICONTROL Nur Text]** ein, geben Sie das Kennwort oder eine beliebige Zeichenfolge zum Verschlüsseln an und klicken Sie auf **[!UICONTROL Protect]**.

   >
   >Der verschlüsselte Text wird im Feld „Protected Text“ angezeigt, das Sie in der Konfiguration angeben können.

1. Aktivieren **[!UICONTROL Borgentest]** oder **[!UICONTROL Rücksendungstest]** , um anzugeben, dass die Objekte validiert werden, bevor sie geliehen oder von bzw. an den Pool zurückgegeben werden.
1. Geben Sie eine SQL SELECT-Abfrage im **[!UICONTROL Überprüfungsabfrage]** -Feld, um Verbindungen aus dem Pool zu überprüfen. Die Abfrage muss mindestens eine Zeile zurückgeben. Legen Sie je nach Datenbank eine der folgenden Optionen fest:

   * SELECT 1 (MySQL und MS SQL)
   * SELECT 1 from dual (Oracle)

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

## AEM-Benutzerprofil konfigurieren {#configure-aem-user-profile}

Sie können AEM Benutzerprofil mithilfe der Benutzerprofil-Connector-Konfiguration in AEM Web-Konsole konfigurieren. Gehen Sie folgendermaßen vor:

1. Wechseln Sie zur AEM-Web-Konsole unter `https://[server]:[host]/system/console/configMgr`.
1. Suchen Sie nach **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** und tippen Sie darauf, um die Konfiguration im Bearbeitungsmodus zu öffnen.
1. Im Dialogfeld für die Benutzerprofil-Connector-Konfiguration können Sie Benutzerprofileigenschaften hinzufügen, entfernen oder aktualisieren. Die angegebenen Eigenschaften sind für die Verwendung im Formulardatenmodell verfügbar. Verwenden Sie das folgende Format, um Benutzerprofileigenschaften festzulegen:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Beispiele:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >Die **&amp;ast;** im obigen Beispiel bedeutet, dass alle Knoten unter `profile/empLocation/` Knoten in AEM Benutzerprofil in der CRXDE-Struktur. Das bedeutet, dass das Formulardatenmodell auf die Eigenschaft `city` des Typs `string` in jedem Knoten unter dem `profile/empLocation/`-Knoten zugreifen kann. Die Knoten, die die angegebene Eigenschaft enthalten, müssen jedoch einer einheitlichen Struktur entsprechen.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

## Einstellen des Ordners für Cloud-Service-Konfigurationen {#cloud-folder}

>[!NOTE]
>
>Die Konfiguration des Cloud Services-Ordners ist erforderlich, um Cloud Services für RESTful-, SOAP- und OData-Services zu konfigurieren.

Alle Cloud-Service-Konfigurationen in AEM werden im Ordner `/conf` im AEM-Repository zusammengefasst. Standardmäßig enthält der Ordner `conf` den Ordner `global`, in dem Sie Cloud Service-Konfigurationen erstellen können. Sie müssen ihn jedoch manuell für Cloud-Konfigurationen aktivieren. Sie können auch zusätzliche Ordner in `conf` erstellen, um Cloud Service-Konfigurationen zu erstellen und zu organisieren.

Konfigurieren des Ordners für Cloud Service-Konfigurationen:

1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurations-Browser.](/help/sites-administering/configurations.md)
1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloud-Konfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud Service-Konfigurationen zu erstellen und zu konfigurieren.

   1. Wählen Sie im **[!UICONTROL Konfigurationsbrowser]** den Ordner `global` aus und tippen Sie auf **[!UICONTROL Eigenschaften]**.
   1. Im **[!UICONTROL Konfigurationseigenschaften]** dialog, aktivieren **[!UICONTROL Cloud-Konfigurationen]**.
   1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Tippen Sie im **[!UICONTROL Konfigurationsbrowser]** auf **[!UICONTROL Erstellen]**.
1. Im **[!UICONTROL Konfiguration erstellen]** Dialogfeld, geben Sie einen Titel für den Ordner an und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den für Cloud Service-Konfigurationen aktivierten Ordner zu erstellen.

## Konfigurieren von RESTful-Webservices {#configure-restful-web-services}

Der RESTful-Webservice kann mithilfe von [Swagger-Spezifikationen](https://swagger.io/specification/) im JSON- oder YAML-Format in einer -Definitionsdatei beschrieben werden. Um den RESTful-Webdienst in AEM Cloud Services zu konfigurieren, stellen Sie sicher, dass sich die Swagger-Datei auf Ihrem Dateisystem oder die URL befindet, unter der die Datei gehostet wird.

Gehen Sie wie folgt vor, um RESTful-Services zu konfigurieren:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](/help/forms/using/configure-data-sources.md#cloud-folder).

1. Tippen **[!UICONTROL Erstellen]** , um **[!UICONTROL Dialogfeld &quot;Datenquellenkonfiguration erstellen&quot;]**. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Service]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den RESTful-Service an:

   * Wählen Sie URL oder Datei aus der Dropdown-Liste Swagger-Quelle aus und geben Sie dementsprechend die Swagger-URL in die Swagger-Definitionsdatei ein oder laden Sie die Swagger-Datei aus Ihrem lokalen Dateisystem hoch.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0, Standardauthentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung – für den Zugriff auf den RESTful-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den RESTful-Service zu erstellen.

## SOAP-Webservices konfigurieren {#configure-soap-web-services}

SOAP-basierte Webservices werden mithilfe von [WSDL-Spezifikationen (Web Services Description Language)](https://www.w3.org/TR/wsdl) beschrieben. Um den SOAP-basierten Web-dienst in den AEM-Cloud-Services zu konfigurieren, benötigen Sie die WSDL-URL für den Webdienst. Gehen Sie dann wie folgt vor:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](/help/forms/using/configure-data-sources.md#cloud-folder).

1. Tippen **[!UICONTROL Erstellen]** , um **[!UICONTROL Dialogfeld &quot;Datenquellenkonfiguration erstellen&quot;]**. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL SOAP-Webservice]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie Folgendes für den SOAP-Webservice an:

   * WSDL-URL für den Webservice.
   * Service-Endpunkt. Geben Sie in diesem Feld einen Wert ein, um den in WSDL erwähnten Service-Endpunkt zu überschreiben.
   * Wählen Sie den Authentifizierungstyp - Keine, OAuth2.0, Standardauthentifizierung, Benutzerdefinierte Authentifizierung oder X509-Token - für den Zugriff auf den SOAP-Dienst aus und geben Sie dementsprechend die Details für die Authentifizierung an.

      Wenn Sie X509-Token als Authentifizierungstyp verwenden, konfigurieren Sie das X509-Zertifikat. Weitere Informationen finden Sie unter [Einrichten von Zertifikaten](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Geben Sie im Feld **[!UICONTROL Schlüssel-Alias]** den KeyStore-Alias für das X509-Zertifikat an. Geben Sie im Feld **[!UICONTROL Gültigkeitsdauer]** die Zeit in Sekunden an, während der die Authentifizierungsanfrage gültig bleibt. Optional können Sie den Nachrichtentext oder die Kopfzeile des Zeitstempels oder beides signieren.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den SOAP-Webservice zu erstellen.

## Konfigurieren von OData-Services {#config-odata}

Ein OData-Service wird anhand seiner Service-Stamm-URL identifiziert. Um einen OData-Dienst in AEM-Cloud-Services zu konfigurieren, stellen Sie sicher, dass Sie über eine Dienststamm-URL für den Dienst verfügen, und führen Sie die folgenden Schritte aus:

>[!NOTE]
>
>Eine schrittweise Anleitung zum Konfigurieren von Microsoft Dynamics 365, online oder On-Premise, finden Sie unter [Microsoft Dynamics OData-Konfiguration](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Datenquellen]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](/help/forms/using/configure-data-sources.md#cloud-folder).

1. Tippen **[!UICONTROL Erstellen]** , um **[!UICONTROL Dialogfeld &quot;Datenquellenkonfiguration erstellen&quot;]**. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL OData-Service]** aus der **[!UICONTROL Dropdown-Liste „Service-Typ“]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den OData-Service an:

   * Service-Stamm-URL für den zu konfigurierenden OData-Service.
   * Wählen Sie den Authentifizierungstyp – Keine, OAuth2.0, Standardauthentifizierung oder benutzerdefinierte Authentifizierung – für den Zugriff auf den OData-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   >[!NOTE]
   >
   >Sie müssen den OAuth 2.0-Authentifizierungstyp auswählen, um eine Verbindung mit Microsoft Dynamics-Diensten herzustellen, die den OData-Endpunkt als Dienststamm nutzen.

1. Tippen Sie auf **Erstellen**, um die Cloud-Konfiguration für den OData-Service zu erstellen.

## Nächste Schritte {#next-steps}

Sie haben die Datenquellen konfiguriert. Als Nächstes können Sie ein Formulardatenmodell erstellen oder wenn Sie bereits ein Formulardatenmodell ohne Datenquelle erstellt haben, können Sie es mit den soeben konfigurierten Datenquellen verknüpfen. Weitere Informationen finden Sie unter [Erstellen eines Formulardatenmodells](/help/forms/using/create-form-data-models.md).
