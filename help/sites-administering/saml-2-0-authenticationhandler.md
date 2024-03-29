---
title: SAML 2.0-Authentifizierungs-Handler
seo-title: SAML 2.0 Authentication Handler
description: Erfahren Sie mehr über den SAML 2.0 Authentication Handler in AEM.
seo-description: Learn about the SAML 2.0 Authentication Handler in AEM.
uuid: 51f97315-350a-42a4-af2c-2de87307c6ad
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 6ed09b5d-5089-43d2-b9d5-e7db57be5c02
exl-id: 4868daad-0f3e-48cb-9b20-08dee270e74e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 71%

---

# SAML 2.0-Authentifizierungs-Handler {#saml-authentication-handler}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM umfasst einen [SAML](http://saml.xml.org/saml-specifications)-Authentifizierungs-Handler. Dieser Handler unterstützt das [SAML](http://saml.xml.org/saml-specifications) 2.0-Authentifizierungsanforderungsprotokoll (Web-SSO-Profil), das die `HTTP POST`-Bindung verwendet.

Es unterstützt:

* Signieren und Verschlüsselung von Nachrichten
* Automatische Erstellung von Benutzern
* Synchronisieren von Gruppen mit vorhandenen Gruppen in AEM
* Durch Dienstleister und Identitätsanbieter eingeleitete Authentifizierung

Dieser Handler speichert die verschlüsselte SAML-Antwortnachricht im Benutzerknoten (`usernode/samlResponse`), um die Kommunikation mit Dienstleistern von Drittanbietern zu erleichtern.

>[!NOTE]
>
>[Hier](https://helpx.adobe.com/experience-manager/kb/simple-saml-demo.html) finden Sie eine Demonstration zur Integration von AEM und SAML.
>
>Um einen End-to-End-Community-Artikel zu lesen, klicken Sie auf: [Integration von SAML in Adobe Experience Manager](https://helpx.adobe.com/de/experience-manager/using/aem63_saml.html).

## Konfigurieren des SAML 2.0-Authentifizierungs-Handlers {#configuring-the-saml-authentication-handler}

Die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) bietet Zugriff auf die [SAML](http://saml.xml.org/saml-specifications) 2.0-Authentifizierungs-Handler-Konfiguration namens **Adobe Granite SAML 2.0 Authentication Handler**. Die folgenden Eigenschaften können festgelegt werden.

>[!NOTE]
>
>Der SAML 2.0 Authentication Handler ist standardmäßig deaktiviert. Sie müssen mindestens eine der folgenden Eigenschaften festlegen, um den Handler zu aktivieren:
>
>* POST-URL des Identitätsanbieters
>* Die Entitäts-ID des Dienstanbieters.
>


>[!NOTE]
>
>SAML-Zusicherungen werden signiert und können optional verschlüsselt werden. Damit dies funktioniert, müssen Sie zumindest das öffentliche Zertifikat des Identitätsanbieters im TrustStore angeben. Weitere Informationen finden Sie im Abschnitt [Hinzufügen des Identitätsanbieterzertifikats zum TrustStore](/help/sites-administering/saml-2-0-authenticationhandler.md#add-the-idp-certificate-to-the-aem-truststore).

**Pfad** Repository-Pfad, für den dieser Authentifizierungs-Handler von Sling verwendet werden soll. Wenn dieser leer ist, wird der Authentifizierungs-Handler deaktiviert.

**Service-Rangfolge** Position in der Rangfolge der OSGi-Framework-Services. Gibt an, mit welcher Priorität dieser Service aufgerufen wird. Dies ist ein ganzzahliger Wert, wobei höhere Werte Vorrang haben.

**IDP-Zertifikatalias** Das Alias des IDP-Zertifikats im globalen TrustStore. Wenn diese Eigenschaft nicht angegeben wird, ist der Authentifizierungs-Handler deaktiviert. Weitere Informationen zum Einrichten finden Sie im Kapitel &quot;Hinzufügen des IdP-Zertifikats zum AEM TrustStore&quot;.

**Identitätsanbieter-URL** Die URL des IDP, an die die SAML-Authentifizierungsanforderung gesendet werden soll. Wenn diese Eigenschaft nicht angegeben wird, ist der Authentifizierungs-Handler deaktiviert.

>[!CAUTION]
>
>Der Hostname des Identitätsanbieters muss der OSGi-Konfiguration **Apache Sling Referrer Filter** hinzugefügt werden. Weitere Informationen finden Sie im Abschnitt [Web-Konsole](/help/sites-deploying/configuring-osgi.md).

**Entitäts-ID des Dienstleisters** ID, die diesen Dienstleister eindeutig beim Identitätsanbieter identifiziert. Wenn diese Eigenschaft nicht angegeben wird, ist der Authentifizierungs-Handler deaktiviert.

**Standardweiterleitung** Der Standardort, an den nach einer erfolgreichen Authentifizierung weitergeleitet wird.

>[!NOTE]
>
>Dieser Ort wird nur verwendet, wenn das Cookie `request-path` nicht festgelegt ist. Wenn Sie eine Seite unterhalb des konfigurierten Pfads ohne gültiges Anmelde-Token anfordern, wird der angeforderte Pfad in einem Cookie gespeichert\
>und der Browser wird nach erfolgreicher Authentifizierung erneut an diesen Ort weitergeleitet.

**Benutzer-ID-Attribut** Der Name des Attributs, das die Benutzer-ID enthält, die zur Authentifizierung und Erstellung des Benutzers im CRX-Repository verwendet wird.

>[!NOTE]
>
>Die Benutzer-ID wird nicht aus dem Knoten `saml:Subject` der SAML-Assertion abgerufen, sondern aus diesem `saml:Attribute`.

**Verschlüsselung verwenden** Gibt an, ob dieser Authentifizierungs-Handler verschlüsselte SAML-Assertionen erwartet.

**CRX-Benutzer automatisch erstellen** Gibt an, ob nicht vorhandene Benutzer nach erfolgreicher Authentifizierung automatisch im Repository erstellt werden sollen.

>[!CAUTION]
>
>Falls die automatische Erstellung von CRX-Benutzern deaktiviert ist, müssen die Benutzer manuell erstellt werden.

**Zu Gruppen hinzufügen** Gibt an, ob Benutzer nach erfolgreicher Authentifizierung automatisch zu CRX-Gruppen hinzugefügt werden sollen.

**Gruppenmitgliedschaft** Der Name des „saml:Attribute“, das eine Liste von CRX-Gruppen enthält, denen dieser Benutzer hinzugefügt werden muss.

## Hinzufügen des IdP-Zertifikats zum AEM TrustStore {#add-the-idp-certificate-to-the-aem-truststore}

SAML-Zusicherungen werden signiert und können optional verschlüsselt werden. Damit dies funktioniert, müssen Sie mindestens das öffentliche Zertifikat des IdP im Repository angeben. Gehen Sie dazu folgendermaßen vor:

1. Wechseln Sie zu *http:/Server-Adresse:Serverport/libs/granite/security/content/truststore.html*.
1. Klicken Sie auf **[!UICONTROL TrustStore-Link erstellen]**.
1. Geben Sie das Kennwort für den TrustStore ein und drücken Sie die **[!UICONTROL Speichern]**.
1. Klicken Sie auf **[!UICONTROL TrustStore verwalten]**.
1. Laden Sie das IdP-Zertifikat hoch.
1. Notieren Sie sich das Zertifikat Alias. Der Alias lautet **[!UICONTROL admin#1436172864930]** im Beispiel unten.

   ![chlimage_1-372](assets/chlimage_1-372.png)

## Hinzufügen des Schlüssels und der Zertifikatkette des Dienstleisters zum AEM-Schlüsselspeicher {#add-the-service-provider-key-and-certificate-chain-to-the-aem-keystore}

>[!NOTE]
>
>Die folgenden Schritte sind obligatorisch. Andernfalls wird die folgende Ausnahme ausgelöst: `com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised system trust store`

1. Wechseln Sie zu [http://localhost:4502/libs/granite/security/content/useradmin.html](http://localhost:4502/libs/granite/security/content/useradmin.html).
1. Bearbeiten Sie den Benutzer `authentication-service`.
1. Erstellen Sie einen KeyStore, indem Sie unter **Kontoeinstellungen** auf **KeyStore erstellen** klicken.

>[!NOTE]
>
>Die folgenden Schritte sind nur erforderlich, wenn der Handler in der Lage sein muss, Nachrichten zu signieren oder zu verschlüsseln.

1. Laden Sie die Datei mit dem privaten Schlüssel hoch, indem Sie auf **Datei mit privatem Schlüssel auswählen** klicken. Der Schlüssel muss das Format „PKCS#8“ haben und die DER-Verschlüsselung aufweisen.
1. Laden Sie die Zertifikatdatei hoch, indem Sie auf **Zertifikatkettendateien auswählen**.
1. Weisen Sie wie unten gezeigt einen Alias zu:

   ![chlimage_1-373](assets/chlimage_1-373.png)

## Konfigurieren eines Loggers für SAML {#configure-a-logger-for-saml}

Sie können einen Logger einrichten, um Probleme zu beheben, die sich aus der falschen Konfiguration von SAML ergeben könnten. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie zur Web-Konsole unter *http://localhost:4502/system/console/configMgr*.
1. Suchen Sie nach dem Eintrag **Apache Sling Logging-Logger-Konfiguration** und klicken Sie darauf.
1. Erstellen Sie eine Protokollfunktion mit der folgenden Konfiguration:

   * **Protokollebene:** Debuggen
   * **Protokolldatei:** logs/saml.log
   * **Logger:** com.adobe.granite.auth.saml
