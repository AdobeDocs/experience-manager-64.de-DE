---
title: Fehlerbehebung bei der Adobe Campaign-Integration
seo-title: Troubleshooting your Adobe Campaign Integration
description: Erfahren Sie, wie Sie Probleme mit der Adobe Campaign-Integration beheben können.
seo-description: Learn how to troubleshoot issues with the Adobe Campaign Integration.
uuid: 835ac2c3-ef2f-4963-9047-aeda3647b114
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b1d45f01-78de-423c-8f6b-5cb7067c3a2f
exl-id: f603b208-5f7b-4e5d-afa8-c3b249f67fb8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 41%

---

# Fehlerbehebung bei der Adobe Campaign-Integration{#troubleshooting-your-adobe-campaign-integration}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Diese Seite gilt für Campaign Classic.

Die folgenden Tipps zur Fehlerbehebung helfen bei der Lösung der häufigsten Probleme, die bei der Integration von AEM in Adobe Campaign auftreten können:

## Allgemeine Tipps zur Problembehebung {#general-troubleshooting-tips}

Bei beiden Integrationen können Sie prüfen, ob HTTP-Aufrufe gesendet werden (AEM > Adobe Campaign, Adobe Campaign > AEM):

* Wenn Integrationen fehlschlagen, stellen Sie sicher, dass diese Aufrufe am anderen Ende ankommen (um Firewall-/SSL-Probleme zu vermeiden).
* Für AEM Funktionen sehen Sie, dass JSON-Aufrufe über die AEM Autorenoberfläche angefordert werden. Diese sollten nicht zu einem HTTP-500-Fehler führen. Wenn HTTP-500-Fehler auftreten, überprüfen Sie die Datei `error.log`, um weitere Informationen zu erhalten.
* Die Anhebung der Debugging-Stufe für Kampagnenklassen in AEM hilft auch bei der Fehlerbehebung.

## Wenn die Verbindung fehlschlägt {#if-the-connection-fails}

Vergewissern Sie sich, dass Sie in Adobe Campaign den Operator **aemserver** konfiguriert haben.

## Wenn Bilder nicht in der Adobe Campaign-Konsole angezeigt werden {#if-images-do-not-appear-in-the-adobe-campaign-console}

Überprüfen Sie die HTML-Quelle und überprüfen Sie, ob Sie die URL vom Clientcomputer aus öffnen können. Wenn die URL „localhost:4503“ enthält, ändern Sie die Konfiguration des Day CQ Link Externalizer auf Ihrer Autoreninstanz so, dass er auf eine Veröffentlichungsinstanz verweist, die vom Adobe Campaign-Konsolen-Computer erreichbar ist.

Siehe [Konfigurieren des Externalizers](/help/sites-administering/campaignstandard.md#configuring-the-externalizer).

## Wenn keine Verbindung von AEM zu Adobe Campaign hergestellt werden kann {#if-you-cannot-connect-from-aem-to-adobe-campaign}

Suchen Sie in Adobe Campaign nach der folgenden Fehlermeldung:

`No datasource defined in the instance 'default'.`

`Make sure the DNS alias used to access the server is correct (for example, avoid hard-coded IP addresses). (iRc=16384)`

Zur Behebung dieses Problems ändern Sie Folgendes in **$CAMPAIGN_HOME/conf/config-&lt;Instanzname>.xml**:

`<dataStore hosts="*" lang="en_GB">`

## Falls im Adobe Campaign-Dialogfeld keine Daten angezeigt werden {#if-no-data-displays-in-the-adobe-campaign-dialog}

Überprüfen Sie in Adobe Campaign, dass nach der Port-Nummer kein Schrägstrich (/) steht.

![chlimage_1-149](assets/chlimage_1-149.png)

## Falls Sie eine Warnung zu Ihrer „setlocale“ erhalten {#if-you-get-a-warning-about-your-setlocale}

Wenn Sie den Apache-HTTPD-Service starten und die Fehlermeldung `"Warning: setlocale: LC_CTYPE cannot change locale"` angezeigt wird, stellen Sie sicher, dass Sie Ihr Eingabegebietsschema **de_DE.ISO-8859-15** auf Ihrem System installiert haben.

Mit `local -a` können Sie überprüfen, ob es installiert ist. Wenn es nicht installiert ist, können Sie einen Patch installieren **/usr/local/neolane/nl6/env.sh** und ändern Sie das Gebietsschema in ein installiertes.

## Wenn beim Kompilieren des Skripts &#39;get_nms_amcGetSeedMetaData_jssp&#39; ein Fehler auftritt {#if-you-get-an-error-while-compiling-script-get-nms-amcgetseedmetadata-jssp}

Wenn die folgende Fehlermeldung in der AEM-Protokolldatei angezeigt wird:

`com.day.cq.mcm.campaign.impl.CampaignConnectorImpl Internal Adobe Campaign error: response body is Error while compiling script 'get_nms_amcGetSeedMetaData_jssp' line 45: String.prototype.toJSON called on incompatible XML.`

Verwenden Sie die folgende Problemumgehung:

1. Datei öffnen **$CAMPAIGN_HOME/datakit/nms/fra/js/amcIntegration.js**
1. Ändern Sie Zeile 467 der Methode „amcGetSeedMetaData“.
1. Ändern Sie `label : [inclView.@label](mailto:inclView.@label)` in `label : String([inclView.@label](mailto:inclView.@label))`.

1. Speichern.
1. Starten Sie den Server neu.

## Wenn Adobe Campaign beim Klicken auf die Schaltfläche &quot;Synchronisieren&quot;einen Fehler anzeigt {#if-adobe-campaign-displays-an-error-when-clicking-the-synchronize-button}

Wenn nach dem Klicken auf die Schaltfläche **Synchronisieren** in Adobe Campaign Classic folgende Fehlermeldung ausgegeben wird:

`Error while executing the method ‘aemListContent' of service [nms:delivery](https://nmsdelivery/)`

Um dieses Problem zu beheben, stellen Sie sicher, dass die in den externen Konten konfigurierte AEM connection-url vom Computer aus erreichbar ist.

Ein Schalter aus **localhost** an eine IP-Adresse zu senden, wurde dieses Problem behoben.

## Wenn der Fehler &quot;XTK-Datum kann nicht analysiert werden&quot;angezeigt wird {#if-you-get-a-cannot-parse-xtk-date-time-undefined-error}

Nachdem Sie auf Synchronisieren geklickt haben, erhalten Sie eine Fehlermeldung, dass ein Skript auf den Seiten aufgetreten ist: Kann XTK-Datum+Uhrzeit nicht analysieren: kein gültiger XTK-Wert.

Dies geschieht, wenn in der AEM-Instanz noch veraltete Adobe Campaign-Informationen vorhanden sind. Lösen Sie dieses Problem, indem Sie alle Konfigurationen der Kampagnenintegration entfernen, die sich auf AEM befinden, und sie neu erstellen. Erstellen Sie dann eine neue Vorlage.

## Wenn eine Verbindung zu SSL einen Fehler beim Einrichten des Cloud Service anzeigt {#if-a-connection-to-ssl-displays-an-error-when-setting-up-the-cloud-service}

Wenn Folgendes in der Datei error.log von AEM angezeigt wird:

```xml
javax.net.ssl.SSLProtocolException: handshake alert:  unrecognized_name
at sun.security.ssl.ClientHandshaker.handshakeAlert(Unknown Source)
at sun.security.ssl.SSLSocketImpl.recvAlert(Unknown Source)
at sun.security.ssl.SSLSocketImpl.readRecord(Unknown Source)
at sun.security.ssl.SSLSocketImpl.performInitialHandshake(Unknown Source)
at sun.security.ssl.SSLSocketImpl.writeRecord(Unknown Source)
at sun.security.ssl.AppOutputStream.write(Unknown Source)
```

Bitte erstellen Sie ein Ticket beim Adobe Campaign-Supportteam.

## Wenn im Synchronisierungsdialogfeld &quot;http&quot;anstelle von erwarteten HTTPS-Links angezeigt wird {#if-you-see-http-instead-of-an-expected-https-links-in-the-synchronization-dialog}

Mit der folgenden Einrichtung:

* Gehostete Adobe Campaign mit HTTPS für die Kommunikation mit AEM Author
* Umgekehrter Proxy, der SSL beendet
* On-Premise-AEM-Autoreninstanz

Wenn Sie versuchen, Inhalte im Adobe Campaign-Versand zu synchronisieren, gibt AEM eine Liste von Newslettern zurück. Die URLs zu den Newslettern in der Liste sind jedoch HTTP-Adressen. Bei Auswahl eines der Elemente in der Liste tritt ein Fehler auf.

So lösen Sie dieses Problem:

* Der Dispatcher oder Reverse-Proxy muss konfiguriert werden, um das ursprüngliche Protokoll als Header zu übergeben.
* Der *Apache Felix HTTP-Service-SSL-Filter* in der OSGi-Konfiguration ([https://&lt;Host>:&lt;Port>/system/console/configMgr](http://localhost:4502/system/console/configMgr)) muss den jeweiligen Kopfzeileneinstellungen entsprechend konfiguriert werden. Siehe [https://felix.apache.org/documentation/subprojects/apache-felix-http-service.html#using-the-ssl-filter](https://felix.apache.org/documentation/subprojects/apache-felix-http-service.html#using-the-ssl-filter)

## Falls die selbst erstellte benutzerdefinierte Vorlage unter Seiteneigenschaften nicht ausgewählt werden kann {#if-the-custom-template-i-created-cannot-be-selected-in-page-properties}

Bei der Erstellung einer Mail-Vorlage für Adobe Campaign müssen Sie die Eigenschaft **acMapping** mit dem Wert **mapRecipient** im Knoten **jcr:content** der Vorlage einbeziehen. Andernfalls können Sie die Adobe Campaign-Vorlage nicht in den **Seiteneigenschaften** von AEM auswählen (Feld ist deaktiviert).

## Falls in den Protokollen der Fehler „com.day.cq.mcm.campaign.servlets.util.ParameterMapper“ auftritt {#if-you-get-the-error-com-day-cq-mcm-campaign-servlets-util-parametermapper-in-your-logs}

Bei der Verwendung Ihrer benutzerdefinierten Vorlage tritt in den Protokollen der Fehler „com.day.cq.mcm.campaign.servlets.util.ParameterMapper“ auf. In diesem Fall müssen Sie das Feature Pack 6576 von [Package Share](/help/sites-administering/package-manager.md#package-share) installieren. Dieses Problem tritt auf, wenn für die Eigenschaft acMapping ein anderer Wert als „recipient.firstName“ festgelegt ist und deshalb ein leerer Wert in Adobe Campaign Manager erstellt wird.
