---
title: Sicherheit
seo-title: Security
description: Anwendungssicherheit beginnt in der Entwicklungsphase
seo-description: Application Security starts during the development phase
exl-id: 22c48f8c-38df-4c9b-88cf-67f6ae46e7e1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 55%

---

# Sicherheit{#security}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Anwendungssicherheit beginnt in der Entwicklungsphase. Adobe empfiehlt die Anwendung der folgenden Best Practices für die Sicherheit.

## Anforderungssitzung verwenden {#use-request-session}

Gemäß dem Prinzip der geringsten Rechte empfiehlt Adobe, dass jeder Zugriff auf das Repository über die an die Benutzeranfrage gebundene Sitzung und eine angemessene Zugriffskontrolle erfolgt.

## Protect gegen Cross-Site Scripting (XSS) {#protect-against-cross-site-scripting-xss}

Cross-Site Scripting (XSS) ermöglicht es Angreifern, Code in Webseiten einzufügen, die von anderen Benutzern angesehen werden. Diese Sicherheitslücke kann von böswilligen Webbenutzern ausgenutzt werden, um Zugriffskontrollen zu umgehen.

AEM filtert prinzipiell sämtliche vom Benutzer bereitgestellten Inhalte bei der Ausgabe. Die Prävention von XSS hat sowohl bei der Entwicklung als auch beim Testen höchste Priorität.

Der XSS-Schutzmechanismus, der von AEM bereitgestellt wird, basiert auf der [AntiSamy Java Library](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) von [OWASP (Open Web Application Security Project). ](https://www.owasp.org/) Die standardmäßige AntiSamy-Konfiguration finden Sie unter

`/libs/cq/xssprotection/config.xml`

Es ist wichtig, dass Sie diese Konfiguration an Ihre eigenen Sicherheitsanforderungen anpassen, indem Sie die Konfigurationsdatei überlagern. Die offizielle [AntiSamy-Dokumentation](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) bietet alle notwendigen Informationen, um Ihre Sicherheitsanforderungen zu implementieren.

>[!NOTE]
>
>Wir empfehlen Ihnen dringend, immer mit der [von AEM bereitgestellten XSSAPI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/xss/XSSAPI.html) auf die XSS-Schutz-API zuzugreifen.

Zusätzlich kann eine Firewall in der Web-Anwendung wie [mod_security für Apache](https://www.modsecurity.org) die Sicherheit der Bereitstellungsumgebung zuverlässig und zentral steuern und diese vor bisher unerkannten Cross-Site-Scripting-Angriffen schützen.

## Zugang zu Cloud Service-Informationen {#access-to-cloud-service-information}

>[!NOTE]
>
>ACLs für die Cloud Service-Informationen sowie die OSGi-Einstellungen, die zum Schützen Ihrer Instanz erforderlich sind, werden im Rahmen der [Produktionsbereiter Modus](/help/sites-administering/production-ready.md). Das bedeutet, dass Sie die Konfigurationsänderungen nicht manuell vornehmen müssen. Sie sollten sie dennoch überprüfen, bevor Sie Ihre Bereitstellung live schalten.

Wenn Sie [Integrieren Ihrer AEM-Instanz mit Adobe Marketing Cloud](/help/sites-administering/marketing-cloud.md) Sie verwenden [Cloud Service-Konfigurationen](/help/sites-developing/extending-cloud-config.md). Informationen zu diesen Konfigurationen sowie alle erfassten Statistiken werden im Repository gespeichert. Wenn Sie diese Funktion verwenden, sollten Sie überprüfen, ob die Standardsicherheit für diese Informationen Ihren Anforderungen entspricht.

Das webservicesupport-Modul schreibt Statistiken und Konfigurationsinformationen unter:

`/etc/cloudservices`

Mit den Standardberechtigungen:

* Autorenumgebung: `read` für `contributors`

* Veröffentlichungsumgebung: `read` für `everyone`

## Schützen Sie sich vor Cross-Site Request Forgery-Angriffen {#protect-against-cross-site-request-forgery-attacks}

Weitere Informationen zu den Sicherheitsmechanismen, die AEM zur Abschwächung von CSRF-Angriffen einsetzt, finden Sie im Abschnitt [Sling Referrer Filter](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) der Sicherheits-Checkliste und in der [Dokumentation zum CSRF Protection Framework](/help/sites-developing/csrf-protection.md).
