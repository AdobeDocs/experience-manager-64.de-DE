---
title: Konfigurieren von Datenquellen
seo-title: Konfigurieren von Datenquellen
description: Erfahren Sie, wie Sie verschiedene Arten von Datenquellen konfigurieren und das Erstellen von Formulardatenmodellen nutzen können.
seo-description: Erfahren Sie, wie Sie verschiedene Arten von Datenquellen konfigurieren und das Erstellen von Formulardatenmodellen nutzen können.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 65%

---


# Konfigurieren von Datenquellen {#configure-data-sources}

Erfahren Sie, wie Sie verschiedene Arten von Datenquellen konfigurieren und das Erstellen von Formulardatenmodellen nutzen können.

![](do-not-localize/data-integeration.png)

Mit der AEM Forms-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herzustellen. Die folgenden Datenquellen werden standardmäßig unterstützt. Es ist jedoch möglich, mit nur wenigen Anpassungen auch andere Datenquellen zu integrieren.

* Relationale Datenbanken: MySQL, Microsoft SQL Server, IBM DB2 und Oracle RDBMS
* AEM-Benutzerprofil 
* RESTful Webservices 
* SOAP-basierte Webservices
* OData-Dienstleistungen

Die Datenintegration unterstützt standardmäßig die Authentifizierungstypen OAuth2.0, Basic Authentication und API Key und ermöglicht die Implementierung der benutzerdefinierten Authentifizierung für den Zugriff auf Webdienste. RESTful-, SOAP-basierte und OData-Dienste werden in AEM-Cloud-Services, JDBC für relationale Datenbanken und der Connector für AEM-Profile dagegen in der AEM-Webkonsole konfiguriert.

## Konfigurieren relationaler Datenbanken {#configure-relational-database}

Sie können relationale Datenbanken mithilfe der AEM Web Console-Konfiguration konfigurieren. Gehen Sie folgendermaßen vor:

1. Gehen Sie zu AEM Webkonsole unter `https://[server]:[host]/system/console/configMgr`.
1. Suchen Sie die Konfiguration **[!UICONTROL Apache Sling Connection Pooled DataSource]**. Tippen Sie, um die Konfiguration im Bearbeitungsmodus zu öffnen.
1. Geben Sie im Konfigurationsdialogfeld die Details für die Datenbank an, die Sie konfigurieren möchten, z. B.:

   * Name der Datenquelle
   * Datenquellendienst-Eigenschaft, in der der Name der Datenquelle gespeichert wird
   * Java-Klassenname für den JDBC-Treiber
   * JDBC-Verbindungs-URI
   * Benutzername und Kennwort zum Herstellen der Verbindung zum JDBC-Treiber

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie vertrauliche Informationen wie Kennwörter verschlüsseln, bevor Sie die Datenquelle konfigurieren. Gehen Sie zum Verschlüsseln wie folgt vor:
   >
   >1. Rufen Sie `https://[server]:[port]/system/console/crypto` auf.
   >1. Geben Sie im Feld **[!UICONTROL Plain Text]** das Kennwort bzw. die zu verschlüsselnde Zeichenfolge ein und klicken Sie auf **[!UICONTROL Protect]**.

   >
   >Der verschlüsselte Text wird im Feld Geschützter Text angezeigt, das Sie in der Konfiguration angeben können.

1. Aktivieren Sie **[!UICONTROL Test on Borrow]** oder **[!UICONTROL Test on Return]**, um festzulegen, dass die Objekte vor der Entnahme oder bei der Rückgabe aus dem bzw. in den Pool validiert werden sollen.
1. Geben Sie eine SQL SELECT-Abfrage in das Feld **[!UICONTROL Validation Query]** ein, damit Verbindungen aus dem Pool validiert werden. Die Abfrage muss mindestens eine Zeile zurückgeben. Legen Sie die für Ihre Datenbank geeignete Option fest:

   * SELECT 1 (MySQL und MS SQL)
   * SELECT 1 from dual (Oracle)

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

## AEM-Benutzerprofil konfigurieren {#configure-aem-user-profile}

Sie können das AEM-Benutzerprofil mithilfe der User Profile Connector-Konfiguration in der AEM-Webkonsole konfigurieren. Gehen Sie folgendermaßen vor:

1. Gehen Sie zu AEM Webkonsole unter `https://[server]:[host]/system/console/configMgr`.
1. Suchen Sie nach **[!UICONTROL AEM Forms Data Integrations - User Profil Connector Configuration]** und tippen Sie auf , um die Konfiguration im Bearbeitungsmodus zu öffnen.
1. Im Dialogfeld für die Benutzerprofil-Connector-Konfiguration können Sie Benutzerprofileigenschaften hinzufügen, entfernen oder aktualisieren. Die angegebenen Eigenschaften sind zur Verwendung im Formulardatenmodell verfügbar. Verwenden Sie das folgende Format, um Benutzerprofileigenschaften festzulegen:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Beispiele:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >Die **&amp;ast;** im obigen Beispiel kennzeichnet alle Nodes unter dem Knoten `profile/empLocation/` im Profil AEM Benutzer in der CRXDE-Struktur. Das bedeutet, dass das Formulardatenmodell auf die `city`-Eigenschaft des Typs `string` zugreifen kann, die in einem beliebigen Knoten unter dem Knoten `profile/empLocation/` vorhanden ist. Die Knoten, die die angegebene Eigenschaft enthalten, müssen jedoch einer einheitlichen Struktur entsprechen.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

## Ordner für Cloud-Dienstkonfigurationen konfigurieren {#cloud-folder}

>[!NOTE]
>
>Zum Konfigurieren von Cloud-Diensten für RESTful-, SOAP- und OData-Dienste ist eine Konfiguration des Ordners für Cloud-Dienste erforderlich.

Alle Cloud-Dienstkonfigurationen in AEM werden im Ordner `/conf` im AEM Repository konsolidiert. Standardmäßig enthält der Ordner `conf` den Ordner `global`, in dem Sie Cloud-Dienst-Konfigurationen erstellen können. Sie müssen ihn jedoch manuell für Cloud-Konfigurationen aktivieren. Sie können auch zusätzliche Ordner in `conf` erstellen, um Cloud-Dienstkonfigurationen zu erstellen und zu organisieren.

Konfigurieren des Ordners für Cloud-Dienstkonfigurationen:

1. Gehen Sie zu **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
   * Weitere Informationen finden Sie in der Dokumentation zum Konfigurationsbrowser](/help/sites-administering/configurations.md).[
1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloud-Konfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud-Dienstkonfigurationen zu erstellen und zu konfigurieren.

   1. Wählen Sie im **[!UICONTROL Konfigurationsbrowser]** den Ordner `global`und tippen Sie auf **[!UICONTROL Eigenschaften]**.
   1. Aktivieren Sie im Dialogfeld **[!UICONTROL Konfigurationseigenschaften]** die Option **[!UICONTROL Cloud-Konfigurationen]**.
   1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Tippen Sie im **[!UICONTROL Konfigurationsbrowser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den Ordner zu erstellen, der für Cloud-Dienstkonfigurationen aktiviert ist.

## RESTful-Webdienste konfigurieren {#configure-restful-web-services}

RESTful-Webdienst kann mithilfe von [Swagger-Spezifikationen](https://swagger.io/specification/) im JSON- oder YAML-Format in einer Swagger-Definitionsdatei beschrieben werden. Um den RESTful-Webdienst in den AEM-Cloud-Services zu konfigurieren, müssen Sie entweder über die Swagger-Datei auf Ihrem System oder über die URL verfügen, unter der die Datei gehostet wird.

Gehen Sie wie folgt vor, um RESTful-Dienste zu konfigurieren:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud-Dienste > Datenquellen]**. Tippen Sie auf , um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud-Dienstkonfigurationen finden Sie unter [Ordner für Cloud-Dienstkonfigurationen konfigurieren](/help/forms/using/configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Create]**, um das Dialogfeld **[!UICONTROL Konfiguration der Datenquelle erstellen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Dienst]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]**, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie die folgenden Details für den RESTful-Dienst an:

   * Wählen Sie „URL“ oder „Datei“ aus der Swagger Source-Dropdownliste aus und geben Sie dementsprechend die URL zur Swagger-Definitionsdatei an oder laden Sie die Swagger-Datei aus Ihrem lokalen Dateisystem hoch.
   * Wählen Sie den Authentifizierungstyp aus — Keine, OAuth2.0, einfache Authentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung — , um auf den RESTful-Dienst zuzugreifen und dementsprechend Details zur Authentifizierung anzugeben.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den RESTful-Dienst zu erstellen.

## SOAP-Webdienste konfigurieren {#configure-soap-web-services}

SOAP-basierte Webdienste werden mithilfe von [WSDL-Spezifikationen (Web Services Description Language)](https://www.w3.org/TR/wsdl) beschrieben. Um den SOAP-basiertenWebdienst in den AEM-Cloud-Services zu konfigurieren, benötigen Sie die WSDL-URL für den Webdienst. Gehen Sie dann wie folgt vor:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud-Dienste > Datenquellen]**. Tippen Sie auf , um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud-Dienstkonfigurationen finden Sie unter [Ordner für Cloud-Dienstkonfigurationen konfigurieren](/help/forms/using/configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Create]**, um das Dialogfeld **[!UICONTROL Konfiguration der Datenquelle erstellen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL SOAP Web-Dienst]** aus der **[!UICONTROL Dropdown-Liste Service-Typ]**, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie Folgendes für den SOAP-Webdienst an:

   * WSDL-URL für den Webdienst.
   * Dienstendpunkt. Geben Sie in diesem Feld einen Wert ein, um den in WSDL erwähnten Dienstendpunkt zu überschreiben.
   * Wählen Sie den Authentifizierungstyp aus — Keine, OAuth2.0, einfache Authentifizierung, benutzerdefinierte Authentifizierung oder X509-Token — , um auf den SOAP-Dienst zuzugreifen und die Details zur Authentifizierung anzugeben.

      Wenn Sie als Authentifizierungstyp &quot;X509-Token&quot;auswählen, konfigurieren Sie das X509-Zertifikat. Weitere Informationen finden Sie unter [Zertifikate einrichten](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Geben Sie im Feld **[!UICONTROL Schlüsselalias]** den KeyStore-Alias für das X509-Zertifikat an. Geben Sie im Feld **[!UICONTROL Zeit bis zum Live]** die Zeit in Sekunden an, bis die Authentifizierungsanforderung gültig bleibt. Optional können Sie den Nachrichtentext oder die Zeitstempelüberschrift oder beides signieren.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den SOAP-Webdienst zu erstellen.

## OData-Dienste konfigurieren {#config-odata}

Ein OData-Dienst wird anhand seiner Dienststamm-URL identifiziert. Stellen Sie zum Konfigurieren eines OData-Dienstes in AEM-Cloud-Services sicher, dass Sie die Dienststamm-URL für den Service haben, und gehen Sie folgendermaßen vor:

>[!NOTE]
>
>Eine schrittweise Anleitung zum Konfigurieren von Microsoft Dynamics 365, online oder On-Premise, finden Sie unter [Microsoft Dynamics OData-Konfiguration ](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud-Dienste > Datenquellen]**. Tippen Sie auf , um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud-Dienstkonfigurationen finden Sie unter [Ordner für Cloud-Dienstkonfigurationen konfigurieren](/help/forms/using/configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Create]**, um das Dialogfeld **[!UICONTROL Konfiguration der Datenquelle erstellen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL OData-Dienst]** aus der **[!UICONTROL Dropdown-Liste Service-Typ]**, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie die folgenden Details für den OData-Dienst an:

   * Dienststamm-URL für den zu konfigurierenden OData-Dienst.
   * Wählen Sie den Authentifizierungstyp aus — Keine, OAuth2.0, einfache Authentifizierung oder benutzerdefinierte Authentifizierung — , um auf den OData-Dienst zuzugreifen und die Details zur Authentifizierung anzugeben.

   >[!NOTE]
   >
   >Sie müssen den OAuth 2.0-Authentifizierungstyp auswählen, um eine Verbindung mit Microsoft Dynamics-Diensten herzustellen, die den OData-Endpunkt als Dienststamm nutzen.

1. Tippen Sie auf **Create**, um die Cloud-Konfiguration für den ODData-Dienst zu erstellen.

## Nächste Schritte {#next-steps}

Sie haben die Datenquellen konfiguriert. Als Nächstes können Sie ein Formulardatenmodell erstellen oder, falls Sie bereits ein Formulardatenmodell ohne Datenquelle erstellt haben, können Sie es den soeben konfigurierten Datenquellen zuordnen. Weitere Informationen finden Sie unter [Formulardatenmodell erstellen](/help/forms/using/create-form-data-models.md).
