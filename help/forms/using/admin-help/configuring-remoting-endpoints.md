---
title: Konfigurieren der Remoting-Endpunkte
seo-title: Configuring Remoting endpoints
description: Erfahren Sie, wie Sie Remoting-Endpunkte konfigurieren.
seo-description: Learn how to configure remoting endpoints.
uuid: 4d4f9274-dcae-4b9f-975a-575376c2f89c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: aab9d622-d76b-4100-9ca6-e5b86f543381
exl-id: d8e31f99-0558-4634-ae35-f4a09f34ad6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 37%

---

# Konfigurieren der Remoting-Endpunkte {#configuring-remoting-endpoints}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Ein Remoting-Endpunkt ermöglicht es einer mit Flex erstellten Anwendung, den Dienst mithilfe von (für AEM Formulare nicht mehr unterstützt) AEM Forms Remoting aufzurufen. Für jeden aktivierten Dienst wird automatisch ein Remoting-Endpunkt erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt. Flex-Clients können Remote-Objekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Dienst aufzurufen.

## Remoting-Endpunkteinstellungen {#remoting-endpoint-settings}

**Flex-Client-Authentifizierungsmethode**: Bestimmt den Typ der Antwort, die der Server zum Client zurücksendet, wenn die Sicherheit für den aufgerufenen Service aktiviert ist, der Vorgang keine anonymen Aufrufe unterstützt und der Client keine oder ungültige Anmeldeinformationen übergibt.
