---
title: Starten und Beenden von WebSphere Application Server
seo-title: Starten und Beenden von WebSphere Application Server
description: In mehreren Verfahren müssen Sie die Instanz von WebSphere, auf der Sie AEM Forms-Produkte bereitstellen möchten, starten oder beenden. In diesem Dokument wird beschrieben, wie Sie WebSphere Application Server starten und anhalten.
seo-description: In mehreren Verfahren müssen Sie die Instanz von WebSphere, auf der Sie AEM Forms-Produkte bereitstellen möchten, starten oder beenden. In diesem Dokument wird beschrieben, wie Sie WebSphere Application Server starten und anhalten.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 79%

---


# Starten und Beenden von WebSphere Application Server {#starting-and-stopping-websphere-application-server}

In mehreren Verfahren müssen Sie die Instanz von WebSphere, auf der Sie AEM Forms-Produkte bereitstellen möchten, starten oder beenden. Wenn Sie nicht sicher sind, ob der Anwendungsserver gestartet wurde, können Sie zunächst den Status von WebSphere Application Server anzeigen.

## Status des WebSphere Application Server anzeigen {#view-the-status-of-websphere-application-server}

1. Wechseln Sie an einer Eingabeaufforderung zum Ordner *[Anwendungsserver-Stammordner]*/bin.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `serverStatus.bat`*Servername*
   * (Linux, UNIX) ./ `serverStatus.sh`*Servername*

## WebSphere Application Server starten {#start-websphere-application-server}

1. Wechseln Sie an einer Eingabeaufforderung zum Ordner *[Anwendungsserver-Stammordner]*/bin.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `startServer.bat`*Servername*
   * (Linux, UNIX) ./ `startServer.sh`*Servername*

## WebSphere Application Server beenden {#stop-websphere-application-server}

1. Wechseln Sie an einer Eingabeaufforderung zum Ordner *[Anwendungsserver-Stammordner]*/bin.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `stopServer.bat`*Servername*
   * (Linux, UNIX) ./ `stopServer.sh`*Servername*

