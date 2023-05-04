---
title: Protokolldateien
seo-title: Log files
description: Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers geschrieben, die mithilfe eines Texteditors geöffnet werden können.
seo-description: Events such as run-time or startup errors are recorded to the application server log files, which can be  opened using any text editor.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 27%

---

# Protokolldateien {#log-files}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers aufgenommen. Wenn bei der Bereitstellung auf dem Anwendungsserver Probleme auftreten, können Sie die Protokolldateien verwenden, um das Problem zu finden. Sie können die Protokolldateien mit einem beliebigen Texteditor öffnen.

(JBoss) Die folgenden Protokolldateien befinden sich im Verzeichnis `*[appserver root]*/server/*[server]*/log`:

* boot.log
* server.log.*[jjjj-mm-tt]*
* server.log

(WebLogic) Protokolldateien für Domänen befinden sich im Ordner *[appserverdomain]* Ordner und Serverprotokolldateien befinden sich im Ordner *[appserverdomain]/servers/[appserver name]/logs *directory:

* access.log
* *[appserver name]*.log
* *[appserver name]*.out.*[inkrementelle Zahl]*

(WebSphere) Die folgenden Protokolldateien befinden sich im *[Anwendungsserver-Stammordner]*/profiles/default/logs/*[appserver name]* directory:

* SystemErr.log
* SystemOut.log
* StartServer.log
