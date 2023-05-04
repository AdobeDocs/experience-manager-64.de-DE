---
title: Starten und Anhalten von Diensten
seo-title: Starting and stopping services
description: Erfahren Sie, wie Sie die Dienste starten und stoppen, die mit AEM Forms-Modulen und dem Anwendungsserver und der Datenbank verknüpft sind.
seo-description: Learn how to start and stop services associated with AEM Forms modules and the application server and database.
uuid: 8c831cb2-4165-4118-8a09-764cec4e5e05
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b93060bd-c6e1-40d2-8acd-ccafb8ed56da
exl-id: 6e0607d6-171c-4119-95a1-373b30fb63c1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 27%

---

# Starten und Anhalten von Diensten {#starting-and-stopping-services}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Es gibt zwei Arten von Diensten, die Teil AEM Formularen sind:

* Dienste, die den AEM forms-Anwendungsserver und die Datenbank steuern.
* Dienste, die AEM Formularmodule steuern

## Dienste starten oder beenden, die mit AEM Formularmodulen verknüpft sind {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM Formularmodule (z. B. Forms, Rights Management, Output) fungieren als Dienste. Manchmal müssen Sie die Dienste für diese AEM Formularmodule anhalten oder starten. Beispielsweise müssen Sie einen AEM Forms-Dienst beenden und neu starten, nachdem Sie eine Einstellung für den Dienst geändert haben.

1. Klicken Sie in der Administration-Console auf **Services** > **Programme und Services** > **Service-Verwaltung**.
1. Aktivieren Sie auf der Seite &quot;Dienstverwaltung&quot;das Kontrollkästchen neben dem Dienst, der angehalten oder gestartet werden soll, und klicken Sie auf &quot;Beenden&quot;oder &quot;Starten&quot;.

## Dienste für den Anwendungsserver und die Datenbank starten oder beenden {#start-or-stop-services-for-the-application-server-and-database}

Eine vollständige Implementierung AEM Formulars umfasst einen Anwendungsserver und Datenbankdienste:

* *`[application server]`* für AEM Forms
* *`[database]`* für AEM Forms

Unter Windows sind diese Services über **Verwaltung** > **Dienste** zugänglich. Wenn Sie beispielsweise AEM Formulare mithilfe der Turnkey-Methode auf JBoss installiert haben, sind die folgenden Dienste auf Ihrem System verfügbar:

* JBoss für Adobe Experience Manager forms
* MySQL für Adobe Experience Manager forms

Starten oder stoppen Sie diese Dienste, indem Sie sie in der Liste im Bedienfeld Dienste auswählen und dann auf die entsprechende Aktionsschaltfläche im Bedienfeld klicken.

Unter UNIX® oder Linux geben Sie folgenden Text an einer Befehlszeile ein, wobei *`[service name]`* der Name des zu überprüfenden Services ist:

```as3
     ps -A | grep [service name]
```
