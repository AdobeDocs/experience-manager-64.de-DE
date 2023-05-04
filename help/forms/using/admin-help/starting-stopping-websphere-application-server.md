---
title: Starten und Anhalten des WebSphere-Anwendungs-Servers
seo-title: Starting and stopping WebSphere Application Server
description: In mehreren Verfahren müssen Sie die Instanz von WebSphere, in der Sie AEM Forms-Produkte bereitstellen möchten, stoppen oder starten. In diesem Dokument wird beschrieben, wie Sie WebSphere Application Server starten und beenden.
seo-description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
exl-id: 8e3bb77f-b187-42c8-a90e-fe0fee50dc34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 40%

---

# Starten und Anhalten des WebSphere-Anwendungs-Servers {#starting-and-stopping-websphere-application-server}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In mehreren Verfahren müssen Sie die Instanz von WebSphere, in der Sie AEM Forms-Produkte bereitstellen möchten, stoppen oder starten. Wenn Sie nicht sicher sind, ob der Anwendungsserver gestartet wurde, können Sie zunächst den Status von WebSphere Application Server anzeigen.

## Status von WebSphere Application Server anzeigen {#view-the-status-of-websphere-application-server}

1. Wechseln Sie an einer Eingabeaufforderung zum *[Anwendungsserver-Stammordner]* Ordner &quot;/bin&quot;.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `serverStatus.bat`*server_name*
   * (Linux, UNIX) ./ `serverStatus.sh`*server_name*

## WebSphere Application Server starten {#start-websphere-application-server}

1. Wechseln Sie an einer Eingabeaufforderung zum *[Anwendungsserver-Stammordner]* Ordner &quot;/bin&quot;.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `startServer.bat`*server_name*
   * (Linux, UNIX) ./ `startServer.sh`*server_name*

## WebSphere Application Server beenden {#stop-websphere-application-server}

1. Wechseln Sie an einer Eingabeaufforderung zum *[Anwendungsserver-Stammordner]* Ordner &quot;/bin&quot;.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `stopServer.bat`*server_name*
   * (Linux, UNIX) ./ `stopServer.sh`*server_name*
