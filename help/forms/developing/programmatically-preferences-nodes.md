---
title: Programmgesteuerte Verwaltung der PreferencesNodes
seo-title: Programmatically managing the PreferencesNodes
description: Verwenden Sie die Preferences Manager Service-API (Java), um die Voreinstellungsknoten programmgesteuert zu verwalten.
seo-description: Use the Preferences Manager Service API (Java) to programmatically manage the Preferences Nodes.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
exl-id: d580b32c-a344-4a8c-bd61-0949da76d981
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 89%

---

# Programmgesteuerte Verwaltung der Voreinstellungsknoten {#programmatically-managing-the-preferencesnodes}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Artikel wird beschrieben, wie Sie die Preferences Manager Service-API (Java) verwenden können, um die Voreinstellungsknoten programmgesteuert zu verwalten.

Sie können die Konfigurationseinstellungen über die Administrator-Benutzeroberfläche manuell ändern. Um die Optionen zu ändern, navigieren Sie zu `Home>Settings>User Management> Configuration>Manual Configuration`. Wenn Sie `config.xml` importieren, nachdem Sie die Änderungen vorgenommen haben, werden Sie feststellen, dass alle Änderungen mit Ausnahme der Änderungen am Knoten `/Adobe/Adobe Experience Manager Forms/Config/UM persist` verloren gegangen sind. Die Vorschau von Import und Export für User Management unterstützt nicht das Ändern von Konfigurationseinstellungen für andere Komponenten. Diese Änderungen können jetzt mithilfe der `PreferencesManagerServiceClient`-APIs vorgenommen werden.

**Zusammenfassung der Schritte** Um die Voreinstellungsknoten programmgesteuert zu verwalten, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen eines PreferencesManagerService-Clients
1. Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PreferencesManagerService-Clients**

Bevor Sie einen PreferencesManagerService-Vorgang für das User Management programmgesteuert durchführen können, müssen Sie einen PreferencesManagerService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein PreferencesManagerServiceClient-Objekt erstellt wird.

**Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge**

Nachdem Sie den Service-Client erstellt haben, können Sie dann die Voreinstellungs-Manager-Vorgänge aufrufen. Mit dem Service-Client können Sie Berechtigungen lesen und festlegen.
