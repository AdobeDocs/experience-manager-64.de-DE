---
title: Aufrufen von AEM Forms mithilfe von APIs
seo-title: Aufrufen von AEM Forms mithilfe von APIs
description: 'Adobe Experience Manager Forms ist eine auf J2EE basierende Unternehmenssoftware, die aus Dienstleistungen besteht, die innerhalb einer gemeinsamen Infrastruktur betrieben werden. Erfahren Sie, wie Sie Clientanwendungen verwenden, um AEM Forms mithilfe einer Java-API, Webservices, Remoting und REST-API programmgesteuert aufzurufen. '
seo-description: Adobe Experience Manager Forms ist eine auf J2EE basierende Unternehmenssoftware, die aus Dienstleistungen besteht, die innerhalb einer gemeinsamen Infrastruktur betrieben werden. Erfahren Sie, wie Sie Clientanwendungen verwenden, um AEM Forms mithilfe einer Java-API, Webservices, Remoting und REST-API programmgesteuert aufzurufen.
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
role: Developer
exl-id: 6b60209f-aced-4698-97f1-b1a7782eef46
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Aufrufen von AEM Forms mithilfe von APIs {#invoking-aem-forms-using-apis}

Adobe Experience Manager Forms ist eine auf J2EE basierende Unternehmenssoftware, die aus Dienstleistungen besteht, die innerhalb einer gemeinsamen Infrastruktur betrieben werden. Dienstvorgänge nutzen oder produzieren normalerweise Dokumente. Mithilfe von AEM Forms können Sie den Arbeitsablauf für Formulare mit elektronischen Formularen, Document Security und der Dokumenterstellung in einem integrierten und kohärenten Satz von Diensten kombinieren. Der Zugriff auf diese Dienste erfolgt innerhalb und außerhalb der Firewall.

Clientanwendungen können AEM Forms-Dienste programmgesteuert über eine Java-API, Webdienste, Remoting und REST aufrufen. Mit Administration Console können Sie einen Dienst konfigurieren, um einen Endpunkt anzuzeigen, über den AEM Forms-Dienste programmgesteuert aufgerufen werden können. Standardmäßig sind die meisten Dienste so vorkonfiguriert, dass sie Remoting-, Java- und Webdienst-Endpunkte verfügbar machen.

Ihre Geschäftsanforderungen bestimmen, welche Aufrufmethode verwendet werden soll. Beispielsweise können Sie mit der Java-API AEM Forms-Funktionen in Ihre Java-Unternehmensanwendungen integrieren, z. B. Java-Entität und Message Beans. Ebenso können Sie AEM Forms-Funktionen mithilfe von Webdiensten in .NET-Projekte (oder andere Projekte, die mit Entwicklungsumgebungen entwickelt wurden, die Webdienststandards unterstützen) integrieren.

Dienste erfordern einen Dienstcontainer, ähnlich wie Enterprise JavaBeans™ (EJBs) einen J2EE-Container benötigen. AEM Forms umfasst nur eine Implementierung eines Dienstcontainers. Der Dienstcontainer ist für die Verwaltung der Lebensdauer eines Dienstes zuständig, einschließlich seiner Bereitstellung und der Sicherstellung, dass alle Anforderungen an den richtigen Dienst gesendet werden. Es verwaltet auch Dokumente, die ein Dienst nutzt oder produziert.

>[!NOTE]
>
>Das Programmieren mit AEM Formularen enthält keine Informationen zum Aufrufen von AEM Forms mithilfe von überwachten Ordnern oder E-Mails.
