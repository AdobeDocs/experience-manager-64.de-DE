---
title: Sicherheit
seo-title: Security
description: Anwendungssicherheit beginnt während der Entwicklung
seo-description: Application Security starts during the development phase
uuid: efd5f3bc-da07-4fc8-a6ce-f1e6f5084c9e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: d2267663-6c1d-413c-9862-e82e21ae6906
exl-id: 22c48f8c-38df-4c9b-88cf-67f6ae46e7e1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 75%

---

# Sicherheit{#security}

Anwendungssicherheit beginnt während der Entwicklung. Adobe empfiehlt die folgenden Best Practices, um die Sicherheit zu verbessern.

## Verwenden Sie Sitzungsanfragen {#use-request-session}

Gemäß dem Grundsatz der geringsten Berechtigungen empfiehlt Adobe, dass jeder Repository-Zugriff über die mit der Benutzeranfrage verknüpfte Sitzung und eine ordnungsgemäße Zugriffskontrolle erfolgt.

## Schutz vor Cross-Site Scripting (XSS) {#protect-against-cross-site-scripting-xss}

Mit Cross-Site Scripting (XSS) können Angreifer Code in Webseiten einfügen, die von anderen Benutzern aufgerufen werden. Diese Sicherheitslücke kann von böswilligen Nutzern ausgenutzt werden, um die Zugriffssteuerung zu umgehen.

AEM filtert prinzipiell sämtliche vom Benutzer bereitgestellten Inhalte bei der Ausgabe. Bei Entwicklung und Tests hat das Vermeiden von XSS höchste Priorität.

Der XSS-Schutzmechanismus, der von AEM bereitgestellt wird, basiert auf der [AntiSamy Java Library](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) von [OWASP (Open Web Application Security Project). ](https://www.owasp.org/) Die standardmäßige AntiSamy-Konfiguration finden Sie unter

`/libs/cq/xssprotection/config.xml`

Es ist wichtig, dass Sie diese Konfiguration an Ihre eigenen Sicherheitsanforderungen anpassen, indem Sie die Konfigurationsdatei überlagern. Die offizielle [AntiSamy-Dokumentation](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) bietet alle notwendigen Informationen, um Ihre Sicherheitsanforderungen zu implementieren.

>[!NOTE]
>
>Wir empfehlen Ihnen dringend, immer mit der [von AEM bereitgestellten XSSAPI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/xss/XSSAPI.html) auf die XSS-Schutz-API zuzugreifen.

Außerdem eine Webanwendungs-Firewall, z. B. [mod_security für Apache](https://www.modsecurity.org)kann eine zuverlässige, zentrale Kontrolle über die Sicherheit der Bereitstellungsumgebung bieten und vor zuvor nicht erkannten Cross-Site-Scripting-Angriffen schützen.

## Zugriff auf Cloud-Service-Informationen {#access-to-cloud-service-information}

>[!NOTE]
>
>ACLs für die Cloud-Service-Information sowie die OSGi-Einstellungen, die zum Sichern Ihrer Instanz erforderlich sind, sind im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) automatisiert. Das bedeutet, dass Sie die Konfigurationsänderungen nicht manuell vornehmen müssen. Sie sollten sie dennoch überprüfen, bevor Sie Ihre Bereitstellung live schalten.

Wenn Sie [Ihre AEM-Instanz mit Adobe Marketing Cloud integrieren](/help/sites-administering/marketing-cloud.md), verwenden Sie [die Cloud-Service-Konfigurationen](/help/sites-developing/extending-cloud-config.md). Informationen über diese Konfigurationen sowie sämtliche erfassten Statistiken werden im Repository gespeichert. Wenn Sie diese Funktion verwenden, empfehlen wir Ihnen, zu überprüfen, ob die Standard-Sicherheitseinstellungen für diese Daten Ihren Anforderungen entsprechen.

Das webservicesupport-Modul schreibt Statistiken und Konfigurationsinformationen unter:

`/etc/cloudservices`

Mit den Standardberechtigungen:

* Autorenumgebung: `read` für `contributors`

* Veröffentlichungsumgebung: `read` für `everyone`

## Schützen Sie sich vor Cross-Site Request Forgery-Angriffen {#protect-against-cross-site-request-forgery-attacks}

Im [Sling Referrer Filter](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery)-Abschnitt der Sicherheits-Checkliste und in der [Dokumentation zum CSRF-Schutz-Framework](/help/sites-developing/csrf-protection.md) finden Sie ausführliche Informationen zu den Sicherheitsmechanismen, die AEM nutzt, um CSRF-Angriffe abzuwehren.
