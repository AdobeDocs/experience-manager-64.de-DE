---
title: AEM zum Durchsuchen von durch Document Security geschützten PDF-Dokumenten aktivieren
seo-title: Enable AEM to search document security protected PDF documents
description: 'Erfahren Sie, wie Sie die native AEM-Suche aktivieren, um eine Volltextsuche in DRM-geschützten PDF-Dokumenten durchzuführen.  '
seo-description: Learn how to enable native AEM search to perform full-text search on DRM protected PDF documents.
uuid: c743cda3-252f-4c1f-8d94-e6d26d91dcd8
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 759068fa-dc1b-4cf5-bc7b-62b8c5464831
feature: Document Security
exl-id: c405c69b-3588-4701-8f36-1ea0680e056d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 92%

---

# AEM zum Durchsuchen von durch Document Security geschützten PDF-Dokumenten aktivieren {#enable-aem-to-search-document-security-protected-pdf-documents}

Mithilfe der AEM-Suche kann nach AEM-Assets gesucht werden und es kann eine Textsuche für verschiedene häufig verwendete Dokumentformate wie Textdateien, Microsoft Office-Dokumente und PDF-Dokumente durchgeführt werden. Sie können die native Suche erweitern, um die Volltextsuche in [PDF-Dokumenten durchzuführen, die mit AEM-Dokumentensicherheit geschützt sind](/help/forms/using/admin-help/document-security.md). Damit AEM die Volltextsuche in solchen Dokumenten durchführen kann, führen Sie die folgenden Schritte aus:

1. Erstellen Sie eine sichere Verknüpfung
1. Indizieren eines richtliniengeschützten Beispiel-PDF-Dokuments

## Voraussetzungen {#prerequisites}

* Wenn Sie AEM Forms on OSGi verwenden: 

   * Installieren Sie[ AEM Forms-Dokumentensicherheit ](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html)auf dem AEM Forms-Server.
   * Stellen Sie sicher, dass ein AEM-Formular auf dem JEE-Server läuft und die Dokumentensicherheit auf den entsprechenden AEM-Formularen auf dem JEE-Server installiert ist. Der AEM Forms on JEE-Server ist erforderlich, um das geschützte Dokument mit einem Index zu versehen. 

* Wenn Sie nur den AEM Forms on JEE-Server verwenden, ist das Indexpaket bereits installiert. 
* Stellen Sie sicher, dass alle Pakete aktiv sind. Wenn nicht alle Pakete aktiv sind, warten Sie, bis alle Pakete aktiv sind. 

   * Bei AEM Forms unter OSGi sind die Bundles unter `https://[server]:[port]/system/console/bundles`.
   * Für AEM Forms on JEE sind die Bundles unter `https://[server]:[port]/[context-path]/system/console/bundles`. Beispiel `http://localhost:8080/lc/system/console/bundles`.

* Fügen Sie die *sun.util.calendar* -Paket in die Zulassungsliste. So fügen Sie das Paket zur Zulassungsliste hinzu:

   1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://[server]:[port]/system/console/configMgr`.
   1. Suchen und öffnen Sie **Deserialisierungs-Firewallkonfiguration**. 
   1. Fügen Sie das sun.util.calendar-Paket zu den Positiv-Klassen oder dem Paketpräfixfeld hinzu und klicken Sie auf **Save**.

## Erstellen Sie eine sichere Verknüpfung zwischen AEM Forms JEE- und OSGi-Stapeln. {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

Sie können eine der folgenden Methoden verwenden, um die sichere Verbindung herzustellen:

* Konfigurieren des Adobe LiveCycle Client SDK Bundle mit AEM Forms on JEE-Administratorberechtigungen
* Konfigurieren von Adobe LiveCycle Client SDK Bundle mit gegenseitiger Authentifizierung

### Konfigurieren des Adobe LiveCycle Client SDK Bundle mit AEM Forms on JEE-Administratorberechtigungen {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://[server]:[port]/system/console/configMgr`.
1. Öffnen Sie das **Adobe LiveCycle Client SDK-Paket**. Geben Sie den Wert für die folgenden Felder an:

   * **Server-URL:** Geben Sie die HTTPS-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie den AEM-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der Forms on JEE-Keystore-Datei> neu.
   * **Dienstname**: Fügen Sie den RightsManagementService zur Liste der angegebenen Dienste hinzu.
   * **Benutzername:** Geben Sie den Benutzernamen des AEM Forms on JEE-Konto an, der verwendet werden soll, um Aufrufe von AEM-Server zu initiieren. Das angegebene Konto benötigt Berechtigungen zum Starten der Document Services auf dem AEM Forms on JEE-Server.
   * **Kennwort:** Geben Sie das Kennwort für das AEM Forms on JEE-Konto an, das im Feld „Benutzername“ erwähnt ist.

   Klicken Sie auf **Speichern**. AEM kann durch Document Security geschützte PDF-Dokumente durchsuchen.

### Konfigurieren von Adobe LiveCycle Client SDK Bundle mit gegenseitiger Authentifizierung {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. Aktivieren Sie die gegenseitige Authentifizierung für AEM Forms on JEE. Weitere Informationen finden Sie unter [CAC und gegenseitige Authentifizierung](https://helpx.adobe.com/de/livecycle/kb/cac-mutual-authentication.html).
1. Öffnen Sie die AEM Web-Konsole. Die URL lautet `https://[server]:[port]/system/console/configMgr`.
1. Öffnen Sie das **Adobe LiveCycle Client SDK-** Paket. Geben Sie Werte für die folgenden Eigenschaften an:

   * **Server-URL:** Geben Sie die HTTPS-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie den AEM-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der AEM Forms on JEE-Keystore-Datei> neu.
   * **2-Weg-SSL aktivieren**: Aktivieren Sie die Option für 2-Weg-SSL.
   * **KeyStore-Datei-URL**: Geben Sie die URL der KeyStore-Datei an.
   * **TrustStore-Datei-URL**: Geben Sie die URL für die TrustStore-Datei an.
   * **KeyStore-Kennwort**: Geben Sie das Kennwort für die KeyStore-Datei an.
   * **TrustStorePassword**: Geben Sie das Kennwort für die TrustStore-Datei an.
   * **Dienstname**: Fügen Sie den RightsManagementService zur Liste der angegebenen Dienste hinzu.

   Klicken Sie auf **Speichern**. AEM kann durch Document Security geschützte PDF-Dokumente durchsuchen.

## Indizieren eines richtliniengeschützten Beispiel-PDF-Dokuments {#index-a-sample-policy-protected-pdf-document}

1. Melden Sie sich bei AEM Assets als Administrator an.
1. Erstellen Sie einen Ordner in AEM Digital Asset Manager und laden Sie die durch Richtlinien geschützten PDF-Dokumente in den neu erstellten Ordner hoch.

   Jetzt können Sie richtliniengeschützte Dokumente mit der AEM-Suche durchsuchen.
