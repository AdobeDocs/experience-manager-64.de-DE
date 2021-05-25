---
title: Remoting-Endpunkte konfigurieren
seo-title: Remoting-Endpunkte konfigurieren
description: Erfahren Sie, wie Sie Remoting-Endpunkte konfigurieren.
seo-description: Erfahren Sie, wie Sie Remoting-Endpunkte konfigurieren.
uuid: 4d4f9274-dcae-4b9f-975a-575376c2f89c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: aab9d622-d76b-4100-9ca6-e5b86f543381
exl-id: d8e31f99-0558-4634-ae35-f4a09f34ad6d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 67%

---

# Remoting-Endpunkte konfigurieren {#configuring-remoting-endpoints}

Ein Remoting-Endpunkt aktiviert eine Anwendung, die mit Flex erstellt wurde, um den Dienst mithilfe von (für AEM Forms nicht mehr unterstützt) AEM Forms Remoting aufzurufen. Ein Remoting-Endpunkt wird automatisch für jeden aktivierten Dienst erstellt. Ein Flex-Ziel mit demselben Namen wie der Endpunkt wird erstellt und Flex-Clients können Remoteobjekte erstellen, die auf dieses Ziel verweisen, um Vorgänge für den entsprechenden Dienst aufzurufen.

## Remoting-Endpunkteinstellungen  {#remoting-endpoint-settings}

**Flex Client-Authentifizierungsmethode:** Bestimmt den Typ der Antwort, die der Server an den Client zurücksendet, wenn die Sicherheit des aufgerufenen Dienstes aktiviert ist, der aufgerufene Vorgang keine anonymen Aufrufe unterstützt und der Client keine oder ungültige Anmeldeinformationen übergibt.
