---
title: Aufrufen von AEM Forms mithilfe von APIs
seo-title: Aufrufen von AEM Forms mithilfe von APIs
description: 'Adobe Experience Manager Forms ist eine J2EE-basierte Unternehmenssoftware, die aus Dienstleistungen besteht, die innerhalb einer gemeinsamen Infrastruktur betrieben werden. Erfahren Sie, wie Sie mithilfe von Clientanwendungen AEM Forms programmgesteuert mit einer Java-API, Webdiensten, Remoting und REST-API aufrufen. '
seo-description: Adobe Experience Manager Forms ist eine J2EE-basierte Unternehmenssoftware, die aus Dienstleistungen besteht, die innerhalb einer gemeinsamen Infrastruktur betrieben werden. Erfahren Sie, wie Sie mithilfe von Clientanwendungen AEM Forms programmgesteuert mit einer Java-API, Webdiensten, Remoting und REST-API aufrufen.
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
role: Developer
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Aufrufen von AEM Forms mithilfe von APIs {#invoking-aem-forms-using-apis}

Adobe Experience Manager Forms ist eine J2EE-basierte Unternehmenssoftware, die aus Dienstleistungen besteht, die innerhalb einer gemeinsamen Infrastruktur betrieben werden. Dienstvorgänge verbrauchen oder produzieren normalerweise Dokumente. Mit AEM Forms können Sie Arbeitsabläufe für Formulare mit elektronischen Formularen, Dokument-Sicherheit und Dokument-Generierung in einem integrierten und zusammenhängenden Satz von Diensten kombinieren. Auf diese Dienste kann von innen und außerhalb der Firewall zugegriffen werden.

Clientanwendungen können AEM Forms-Dienste programmgesteuert über eine Java-API, Webdienste, Remoting und REST aufrufen. Mit Administration Console können Sie einen Dienst so konfigurieren, dass ein Endpunkt offen gelegt wird, über den AEM Forms-Dienste programmgesteuert aufgerufen werden können. Standardmäßig sind die meisten Dienste vorkonfiguriert, um Remoting-, Java- und Webdienst-Endpunkte verfügbar zu machen.

Ihre Geschäftsanforderungen bestimmen, welche Aufrufmethode verwendet werden soll. Beispielsweise können Sie mit der Java-API AEM Forms-Funktionen in Ihre Java-Unternehmensanwendungen integrieren, z. B. Java Entity und Message Beans. Ebenso können Sie AEM Forms-Funktionen mithilfe von Webdiensten in .NET-Projekte (oder andere Umgebung, die mit Entwicklungs-Standards unterstützen) integrieren.

Dienste benötigen einen Service Container, ähnlich wie Enterprise JavaBeans™ (EJBs) einen J2EE-Container. AEM Forms umfasst nur eine Implementierung eines Service-Containers. Der Service Container ist für die Verwaltung der Lebensdauer eines Dienstes verantwortlich, einschließlich dessen Bereitstellung und der Sicherstellung, dass alle Anforderungen an den richtigen Dienst gesendet werden. Es verwaltet auch Dokumente, die ein Dienst nutzt oder produziert.

>[!NOTE]
>
>Die Programmierung mit AEM Formularen enthält keine Informationen zum Aufrufen von AEM Forms mit überwachten Ordnern oder per E-Mail.

