---
title: Aktivieren von AEM, um durch Document Security geschützte PDF-Dokumente zu durchsuchen
seo-title: Enable AEM to search document security protected PDF and Microsoft Office documents
description: Erfahren Sie, wie Sie die native AEM für die Volltextsuche in DRM-geschützten PDF-Dokumenten aktivieren.
seo-description: Learn how to enable native AEM search to perform full-text search on DRM protected PDF documents.
uuid: dba882f8-bad4-4122-a0df-03cf087afb23
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 7eebef08-83b9-4b56-90ec-35ab3b0c27e8
noindex: true
feature: Document Security
exl-id: dbf97dc1-cf05-4d45-859e-60ff01186e51
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 65%

---

# AEM aktivieren, um durch Document Security geschützte PDF-Dokumente zu durchsuchen{#enable-aem-to-search-document-security-protected-pdf-and-microsoft-office-documents}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe Experience Manager bietet eine Benutzeroberfläche zum Suchen und Auffinden verschiedener Assets, die in AEM gespeichert werden. Die programmeigene Suchfunktion kann AEM-Assets durchsuchen und nach   Textsuche in Dokumenten verschiedener gängiger Formate, wie z. B. Textdateien, Microsoft Office-Dokumenten und PDF-Dokumenten. Sie können dies auch erweitern und die native Suche aktivieren, um eine Volltextsuche in DRM-geschützten PDF- und Microsoft-Office-Dokumenten durchzuführen.

Führen Sie die folgenden Schritte aus, um die AEM zum Durchsuchen von durch Document Security geschützten PDF- und Microsoft Office-Dokumenten zu aktivieren:

## Bevor Sie beginnen {#before-you-start}

* Installieren und konfigurieren Sie AEM Forms Document Security.
* Fügen Sie das Paket „sun.util.calendar“ zur Zulassungsliste der **Deserialisierungs-Firewall-Konfiguration hinzu.** Die Konfiguration ist unter `https://[server]:[port]/system/console/configMgr` aufgeführt.
* Stellen Sie sicher, dass alle AEM-Pakete aktiv sind. Die Bundles sind unter `https://[server]:[port]/system/console/bundles` aufgeführt. Wenn alle Bundles nicht aktiv, warten Sie einige Minuten und überprüfen Sie den Status der Bundles.

## Herstellen einer sicheren Verbindung innerhalb des AEM Forms-Workflows (AEM Forms on JEE) {#establish-a-secure-connection-within-aem-forms-workflow-aem-forms-on-jee}

Eine sichere Verbindung ermöglicht einen nahtlosen Informationsfluss zwischen AEM Forms on JEE und den OSGi-Diensten, die auf demselben Server ausgeführt werden. Verwenden Sie eine der folgenden Methoden, um eine sichere Verbindung herzustellen:

* Konfigurieren des AEM Forms Client SDK Bundle mit AEM Forms on JEE-Administratorberechtigungen
* Konfigurieren von AEM Forms Client SDK Bundle mit gegenseitiger Authentifizierung 

### Konfigurieren des AEM Forms Client SDK Bundle mit Administratorberechtigungen für AEM Forms on JEE {#configure-aem-forms-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Öffnen Sie AEM Konfigurationsmanager und melden Sie sich als Administrator an. Die Standard-URL lautet https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Suchen und öffnen Sie das AEM Forms Client SDK Bundle. Geben Sie einen Wert für die folgenden Eigenschaften an:

   * **Server-URL:** Geben Sie die HTTP-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie AEM Forms auf JEE-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der Keystore-Datei von AEM Forms auf JEE> neu.
   * **Dienstname**: Fügen Sie den RightsManagementService zur Liste der angegebenen Dienste hinzu.
   * **Benutzername:** Geben Sie den Benutzernamen des AEM Forms on JEE-Kontos an, um Aufrufe vom AEM Forms on JEE-Server zu initiieren. Das angegebene Konto muss über Berechtigungen zum Aufrufen von Document Services auf dem AEM Forms on JEE-Server verfügen.
   * **Passwort**: Geben Sie das Kennwort des im Feld Benutzername erwähnten AEM Forms on JEE-Kontos an.

   Klicken Sie auf **Speichern**. AEM ist aktiviert, um durch Document Security geschützte PDF- und Microsoft Office-Dokumente zu durchsuchen.

### Konfigurieren von AEM Forms Client SDK Bundle mit gegenseitiger Authentifizierung  {#configure-aem-forms-client-sdk-bundle-using-mutual-authentication}

1. Aktivieren Sie die gegenseitige Authentifizierung für AEM Forms on JEE. Detaillierte Informationen finden Sie unter [CAC und gegenseitige Authentifizierung](https://helpx.adobe.com/de/livecycle/kb/cac-mutual-authentication.html).
1. Öffnen Sie AEM Konfigurationsmanager und melden Sie sich als Administrator an. Die Standard-URL lautet https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Suchen und öffnen Sie das AEM Forms Client SDK Bundle. Geben Sie einen Wert für die folgenden Eigenschaften an:

   * **Server-URL:** Geben Sie die HTTPS-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie AEM Forms auf JEE-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der Keystore-Datei von AEM Forms auf JEE> neu.
   * **2-Weg-SSL aktivieren**: Aktivieren Sie die Option für 2-Weg-SSL.
   * **KeyStore-Datei-URL**: Geben Sie die URL der KeyStore-Datei an.
   * **TrustStore-Datei-URL**: Geben Sie die URL für die TrustStore-Datei an.
   * **KeyStore-Kennwort**: Geben Sie das Kennwort für die KeyStore-Datei an.
   * **TrustStorePassword**: Geben Sie das Kennwort für die TrustStore-Datei an.
   * **Service-Name**: Fügen Sie den RightsManagementService zur Liste der angegebenen Services hinzu.

   Klicken Sie auf **Speichern**. AEM ist aktiviert, um durch Document Security geschützte PDF- und Microsoft Office-Dokumente zu durchsuchen

## Indexieren eines richtliniengeschützten Beispieldokuments für PDF oder Microsoft Office {#index-a-sample-policy-protected-pdf-or-microsoft-office-document}

1. Melden Sie sich bei AEM Assets als Administrator an.
1. Erstellen Sie einen Ordner in AEM Digital Asset Manager und laden Sie die durch Richtlinien geschützten PDF oder Microsoft Office-Dokumente in den neu erstellten Ordner hoch. Durchsuchen Sie nun die Inhalte der richtliniengeschützten Dokumente mit der AEM-Suche. Das Dokument muss zurückzugeben werden, das den gesuchten Text enthält, das Text enthält.
