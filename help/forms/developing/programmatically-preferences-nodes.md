---
title: Programmgesteuerte Verwaltung der PreferencesNodes
seo-title: Programmatically managing the PreferencesNodes
description: Verwenden Sie die Voreinstellungs-Manager-Dienst-API (Java), um die Voreinstellungsknoten programmgesteuert zu verwalten.
seo-description: Use the Preferences Manager Service API (Java) to programmatically manage the Preferences Nodes.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
exl-id: d580b32c-a344-4a8c-bd61-0949da76d981
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Programmgesteuerte Verwaltung der Voreinstellungsknoten {#programmatically-managing-the-preferencesnodes}

In diesem Thema wird beschrieben, wie Sie die Voreinstellungs-Manager-Dienst-API (Java) verwenden können, um die Voreinstellungsknoten programmgesteuert zu verwalten.

Sie können die Konfigurationseinstellungen über die Administrator-Benutzeroberfläche manuell ändern. Um die Optionen zu ändern, navigieren Sie zu `Home>Settings>User Management> Configuration>Manual Configuration`. Import `config.xml` Nachdem Sie die Änderungen vorgenommen haben, würden Sie feststellen, dass alle Änderungen außer den am Knoten vorgenommenen Änderungen `/Adobe/Adobe Experience Manager Forms/Config/UM persist` verloren. Die Vorschau von User Management Import und Export unterstützt keine Änderung der Konfigurationseinstellungen für andere Komponenten. Diese Änderungen können nun mithilfe von `PreferencesManagerServiceClient` APIs.

**Zusammenfassung der Schritte** Um die Voreinstellungsknoten programmgesteuert zu verwalten, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen eines PreferencesManagerService-Clients
1. Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PreferencesManagerService-Clients**

Bevor Sie einen User Management PreferencesManagerService-Vorgang programmgesteuert ausführen können, müssen Sie einen PreferencesManagerService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein PreferencesManagerServiceClient -Objekt erstellt wird.

**Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge**

Nachdem Sie den Service-Client erstellt haben, können Sie dann die Voreinstellungs-Manager-Vorgänge aufrufen. Mit dem Dienst-Client können Sie Berechtigungen lesen und festlegen.
