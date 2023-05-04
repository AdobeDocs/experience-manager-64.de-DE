---
title: Aktivieren von AEM zum Durchsuchen von durch Dokumentensicherheit geschützten PDF-Dokumenten
seo-title: Enable AEM to search document security protected PDF documents
description: Erfahren Sie, wie Sie die native AEM für die Volltextsuche in DRM-geschützten PDF-Dokumenten aktivieren.
seo-description: Learn how to enable native AEM search to perform full-text search on DRM protected PDF documents.
uuid: c743cda3-252f-4c1f-8d94-e6d26d91dcd8
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 759068fa-dc1b-4cf5-bc7b-62b8c5464831
feature: Document Security
exl-id: c405c69b-3588-4701-8f36-1ea0680e056d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 48%

---

# AEM zum Durchsuchen von durch Document Security geschützten PDF-Dokumenten aktivieren {#enable-aem-to-search-document-security-protected-pdf-documents}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Suche ist in der Lage, nach AEM Assets zu suchen und diese zu suchen und Textsuchen in verschiedenen häufig verwendeten Dokumentformaten wie Textdateien, Microsoft Office-Dokumenten und PDF-Dokumenten durchzuführen. Sie können die native Suche auch erweitern, um eine Volltextsuche für [PDF von Dokumenten mit AEM Document Security geschützt](/help/forms/using/admin-help/document-security.md). So aktivieren AEM Volltextsuchen für solche Dokumente:

1. Sichere Verbindung herstellen
1. Indexieren eines richtliniengeschützten Beispieldokuments für PDF

## Voraussetzungen {#prerequisites}

* Wenn Sie AEM Forms on OSGi verwenden: 

   * Installieren Sie[ AEM Forms-Dokumentensicherheit ](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html)auf dem AEM Forms-Server.
   * Stellen Sie sicher, dass ein AEM Forms auf dem JEE-Server läuft und die Dokumentensicherheit auf den entsprechenden AEM Forms auf dem JEE-Server installiert ist. Der AEM Forms on JEE-Server ist erforderlich, um das geschützte Dokument mit einem Index zu versehen. 

* Wenn Sie nur den AEM Forms on JEE-Server verwenden, ist das Indexpaket bereits installiert. 
* Stellen Sie sicher, dass alle Pakete aktiv sind. Wenn nicht alle Pakete aktiv sind, warten Sie, bis alle Pakete aktiv sind. 

   * Bei AEM Forms unter OSGi sind die Bundles unter `https://[server]:[port]/system/console/bundles`.
   * Für AEM Forms on JEE sind die Bundles unter `https://[server]:[port]/[context-path]/system/console/bundles`. Beispiel `http://localhost:8080/lc/system/console/bundles`.

* Fügen Sie das Paket *sun.util.calendar* zur Zulassungsliste hinzu. Um das Paket zur Zulassungsliste hinzuzufügen, führen Sie die folgenden Schritte aus:

   1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://[server]:[port]/system/console/configMgr`..
   1. Suchen und öffnen Sie **Deserialisierungs-Firewallkonfiguration**. 
   1. Fügen Sie das Paket sun.util.calendar zum Feld Whitelisted classes or package prefixes hinzu und klicken Sie auf **Speichern**.

## Sichere Verbindung zwischen AEM Forms JEE- und OSGi-Stapeln herstellen {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

Sie können eine der folgenden Methoden verwenden, um die sichere Verbindung herzustellen:

* Konfigurieren von Adobe LiveCycle Client SDK Bundle mit AEM Forms on JEE-Administratorberechtigungen
* Konfigurieren von Adobe LiveCycle Client SDK Bundle mit gegenseitiger Authentifizierung

### Konfigurieren von Adobe LiveCycle Client SDK Bundle mit AEM Forms on JEE-Administratorberechtigungen {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://[server]:[port]/system/console/configMgr`..
1. Suchen und öffnen Sie die **Adobe LiveCycle Client SDK Bundle**. Geben Sie Werte für die folgenden Felder an:

   * **Server-URL:** Geben Sie die HTTPS-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie den AEM-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der AEM Forms on JEE-Keystore-Datei> neu.
   * **Dienstname**: Fügen Sie den RightsManagementService zur Liste der angegebenen Dienste hinzu.
   * **Benutzername:** Geben Sie den Benutzernamen des AEM Forms on JEE-Konto an, der verwendet werden soll, um Aufrufe von AEM-Server zu initiieren. Das angegebene Konto muss über Berechtigungen zum Starten von Document Services auf dem AEM Forms on JEE-Server verfügen.
   * **Passwort**: Geben Sie das Kennwort des im Feld Benutzername erwähnten AEM Forms on JEE-Kontos an.

   Klicken Sie auf **Speichern**. AEM ist aktiviert, um durch Document Security geschützte PDF-Dokumente zu durchsuchen.

### Konfigurieren von Adobe LiveCycle Client SDK Bundle mit gegenseitiger Authentifizierung {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. Aktivieren Sie die gegenseitige Authentifizierung für AEM Forms on JEE. Detaillierte Informationen finden Sie unter [CAC und gegenseitige Authentifizierung](https://helpx.adobe.com/de/livecycle/kb/cac-mutual-authentication.html).
1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://[server]:[port]/system/console/configMgr`..
1. Suchen und öffnen Sie die **Adobe LiveCycle Client SDK** Bundle. Geben Sie einen Wert für die folgenden Eigenschaften an:

   * **Server-URL:** Geben Sie die HTTPS-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie den AEM-Server mit -Djavax.net.ssl.trustStore= neu.&lt;path of=&quot;&quot; aem=&quot;&quot; forms=&quot;&quot; on=&quot;&quot; jee=&quot;&quot; keystore=&quot;&quot; file=&quot;&quot;> Parameter.
   * **2-Weg-SSL aktivieren**: Aktiviert die Option für 2-Weg-SSL.
   * **KeyStore-Datei-URL**: Geben Sie die URL der KeyStore-Datei an.
   * **TrustStore-Datei-URL**: Geben Sie die URL für die TrustStore-Datei an.
   * **KeyStore-Kennwort**: Geben Sie das Kennwort für die KeyStore-Datei an.
   * **TrustStorePassword**: Geben Sie das Kennwort für die TrustStore-Datei an.
   * **Dienstname**: Fügt den RightsManagementService zur Liste der angegebenen Dienste hinzu.

   Klicken Sie auf **Speichern**. AEM ist aktiviert, um durch Document Security geschützte PDF-Dokumente zu durchsuchen

## Indexieren eines richtliniengeschützten Beispieldokuments für PDF {#index-a-sample-policy-protected-pdf-document}

1. Melden Sie sich bei AEM Assets als Administrator an.
1. Erstellen Sie einen Ordner in AEM Digital Asset Manager und laden Sie die richtliniengeschützten PDF-Dokumente in den neu erstellten Ordner hoch.

   Jetzt können Sie die richtliniengeschützten Dokumente mithilfe AEM Suche durchsuchen.
