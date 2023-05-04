---
title: Konfigurieren des Connectors für IBM Content Manager
seo-title: Configuring Connector for IBM Content Manager
description: Konfigurieren Sie den Connector für IBM Content Manager, um die Kommunikation zwischen AEM Forms und IBM Content Manager zu aktivieren.
seo-description: Configure the Connector for IBM Content Manager to enable communication between AEM forms and IBM Content Manager.
uuid: 3d55169d-93e3-4d4e-b18b-2a3394e1de3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3094b178-3b1a-46b3-8fbd-c20388afa3a7
exl-id: 8c65531e-f4f0-4cc4-b328-eaefb5662cf1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 11%

---

# Konfigurieren des Connectors für IBM Content Manager{#configuring-connector-for-ibm-content-manager}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Connector für IBM Content Manager ermöglicht die Kommunikation zwischen AEM Forms und IBM Content Manager. Weitere Hintergrundinformationen finden Sie unter &quot;Connectors for ECM&quot;in [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

## Verbindung mit IBM Content Manager konfigurieren {#configure-the-ibm-content-manager-connection}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für IBM Content Manager&quot;.
1. Geben Sie in das Feld &quot;Datastore Name&quot;den Namen des IBM Content Manager-Datenspeichers ein, mit dem Sie eine Verbindung herstellen möchten. Wenn es sich um eine lokale Datenbank handelt, geben Sie den Namen der Datenbank ein. Wenn es sich um eine Remote-Datenbank handelt, geben Sie deren Aliasnamen ein.
1. Geben Sie in das Feld &quot;Benutzername&quot;die Benutzer-ID eines Benutzers ein, der eine Verbindung zum IBM Content Manager-Datenspeicher herstellen soll.
1. Geben Sie in das Feld &quot;Kennwort&quot;das Kennwort des Benutzers ein.
1. (Optional) Geben Sie im Feld &quot;Alias-Verbindungszeichenfolge&quot;zusätzliche Verbindungsargumente ein. In den meisten Fällen sollte dieses Feld leer sein. Weitere Informationen finden Sie in der IBM-Dokumentation.
1. Klicken Sie auf Speichern.

## Validierung der Diensteinstellungen {#validation-of-service-settings}

Wenn Sie einen falschen Alias, Benutzernamen oder Kennwort für den Datenspeicher eingeben, erhalten Sie je nachdem, ob der Content Repository Connector für IBM Content Manager-Dienst derzeit ausgeführt wird, die folgenden Ergebnisse:

* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen angehalten wird, wird kein Fehler angezeigt. Wenn Sie den Dienst jedoch das nächste Mal starten, wird eine Ausnahme ausgelöst und der Dienst wird nicht gestartet.
* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet wird, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.
