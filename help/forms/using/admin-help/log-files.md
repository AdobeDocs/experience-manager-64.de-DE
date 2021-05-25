---
title: Protokolldateien
seo-title: Protokolldateien
description: Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers geschrieben, die mithilfe eines Texteditors geöffnet werden können.
seo-description: Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers geschrieben, die mithilfe eines Texteditors geöffnet werden können.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 64%

---

# Protokolldateien {#log-files}

Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers geschrieben. Wenn bei der Bereitstellung auf dem Anwendungsserver Probleme auftreten, können Sie diese mithilfe der Protokolldateien ermitteln. Sie können die Protokolldateien in einem beliebigen Texteditor öffnen.

(JBoss) Die folgenden Protokolldateien befinden sich im Ordner `*[appserver root]*/server/*[server]*/log` :

* boot.log
* server.log.*[jjjj-mm-tt]*
* server.log

(WebLogic) Domänenprotokolldateien befinden sich im Ordner *[appserverdomain]* und Serverprotokolldateien befinden sich im Ordner *[appserverdomain]/servers/[appserver name]/logs *directory:

* access.log
* *[appserver name]*.log
* *[appserver name]*.out.*[inkrementelle Zahl]*

(WebSphere) Die folgenden Protokolldateien befinden sich im Ordner *[appserver root]*/profiles/default/logs/*[appserver name]* :

* SystemErr.log
* SystemOut.log
* StartServer.log
