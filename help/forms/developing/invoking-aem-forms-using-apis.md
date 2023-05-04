---
title: Aufrufen von AEM Forms mithilfe von APIs
seo-title: Invoking AEM Forms using APIs
description: Adobe Experience Manager Forms ist eine auf J2EE basierende Unternehmenssoftware, die aus Diensten besteht, die innerhalb einer gemeinsamen Infrastruktur betrieben werden. Erfahren Sie, wie Sie Clientanwendungen verwenden, um AEM Forms mithilfe einer Java-API, Webservices, Remoting und REST-API programmgesteuert aufzurufen.
seo-description: Adobe Experience Manager Forms is J2EE-based enterprise software that consists of services that operate within a shared infrastructure. Learn how to use client applications to invoke AEM Forms programmatically using a Java API, web services, Remoting, and REST API.
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
role: Developer
exl-id: 6b60209f-aced-4698-97f1-b1a7782eef46
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 85%

---

# Aufrufen von AEM Forms mithilfe von APIs {#invoking-aem-forms-using-apis}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe Experience Manager Forms ist eine auf J2EE basierende Unternehmenssoftware, die aus Diensten besteht, die innerhalb einer gemeinsamen Infrastruktur betrieben werden. Dienstvorgänge nutzen oder produzieren normalerweise Dokumente. Mithilfe von AEM Forms können Sie den Workflow für Formulare mit elektronischen Formularen, Dokumentensicherheit und der Dokumenterstellung in einem integrierten und kohärenten Satz von Diensten kombinieren. Der Zugriff auf diese Dienste kann von innerhalb und außerhalb der Firewall erfolgen.

Clientanwendungen können AEM Forms-Dienste programmgesteuert über eine Java-API, Webdienste, Remoting und REST aufrufen. Über die Administrationskonsole können Sie einen Dienst so konfigurieren, dass ein Endpunkt bereitgestellt wird, über den AEM Forms-Dienste programmgesteuert aufgerufen werden können. Standardmäßig sind die meisten Dienste so vorkonfiguriert, dass sie Remoting-, Java- und Webdienst-Endpunkte bereitstellen.

Ihre Geschäftsanforderungen bestimmen, welche Aufrufmethode verwendet werden soll. Beispielsweise können Sie mit der Java-API AEM Forms-Funktionen in Ihre Java-Unternehmensanwendungen integrieren, z. B. Java-Entität und Message Beans. Ebenso können Sie AEM Forms-Funktionen mithilfe von Webdiensten in .NET-Projekte (oder andere Projekte, die mit Entwicklungsumgebungen entwickelt wurden, die Webdienststandards unterstützen) integrieren.

Für die Ausführung von Diensten ist ein Dienstcontainer erforderlich, ähnlich wie Enterprise JavaBeans™ (EJBs) einen J2EE-Container benötigen. AEM Forms umfasst nur eine Implementierung eines Dienstcontainers. Der Dienstcontainer ist für die Verwaltung der Lebensdauer eines Dienstes zuständig, einschließlich seiner Bereitstellung und der Sicherstellung, dass alle Anforderungen an den richtigen Dienst gesendet werden. Er verwaltet auch Dokumente, die ein Dienst nutzt oder produziert.

>[!NOTE]
>
>„Programmieren mit AEM Forms“ enthält keine Informationen zum Aufrufen von AEM Forms mithilfe von überwachten Ordnern oder E-Mails.
