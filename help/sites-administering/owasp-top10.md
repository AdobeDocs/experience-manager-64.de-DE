---
title: OWASP – Top 10
seo-title: OWASP Top 10
description: Erfahren Sie, wie AEM mit den 10 wichtigsten OWASP-Sicherheitsrisiken umgeht.
seo-description: Learn how AEM deals with the top 10 OWASP security risks.
uuid: a5a7e130-e15b-47ae-ba21-448f9ac76074
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: e5323ae8-bc37-4bc6-bca6-9763e18c8e76
exl-id: c29472c8-9a93-4cb1-9cb1-05fc155ba736
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 43%

---

# OWASP – Top 10{#owasp-top}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die [Webanwendungs-Sicherheitsprojekt öffnen](https://www.owasp.org) (OWASP) verwaltet eine Liste dessen, was sie als [Die 10 wichtigsten Sicherheitsrisiken für Webanwendungen](https://www.owasp.org/index.php/OWASP_Top_Ten_Project).

Diese sind unten aufgeführt, zusammen mit einer Erläuterung, wie CRX mit ihnen umgeht.

## 1. Injektion {#injection}

* SQL - Vorsichtshinweis: Die standardmäßige Repository-Einrichtung umfasst keine traditionelle Datenbank und erfordert auch keine solche. Alle Daten werden im Inhalts-Repository gespeichert. Der Zugriff ist auf authentifizierte Benutzer beschränkt und kann nur über die JCR-API erfolgen. SQL wird nur für Suchabfragen (SELECT) unterstützt. Darüber hinaus bietet SQL Unterstützung für Werte-Binding.
* LDAP - Eine LDAP-Injektion ist nicht möglich, da das Authentifizierungsmodul die Eingabe filtert und den Benutzerimport mithilfe der Bindungsmethode durchführt.
* BS - In der Anwendung wird keine Shell-Ausführung ausgeführt.

## 2. Cross-Site Scripting (XSS) {#cross-site-scripting-xss}

Die allgemeine Praxis zur Schadensbegrenzung besteht in der Codierung aller Ausgaben benutzergenerierter Inhalte mithilfe einer Server-seitigen XSS-Schutzbibliothek, die auf dem [OWASP Encoder](https://www.owasp.org/index.php/OWASP_Java_Encoder_Project) und [AntiSamy](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) basiert.

XSS hat sowohl bei den Tests als auch bei der Entwicklung eine hohe Priorität und alle festgestellten Probleme werden (in der Regel) umgehend behoben.

## 3. Fehler in Authentifizierung und Session Management {#broken-authentication-and-session-management}

AEM nutzt fundierte, bewährte Authentifizierungstechniken und greift hierzu auf [Apache Jackrabbit](https://jackrabbit.apache.org/) und [Apache Sling](https://sling.apache.org/) zurück. In AEM werden keine Browser-/HTTP-Sitzungen verwendet.

## 4. Unsichere direkte Objektreferenzen {#insecure-direct-object-references}

Der Zugriff auf Datenobjekte wird vom Repository vermittelt und daher durch rollenbasierte Zugriffskontrolle eingeschränkt.

## 5. Cross-Site Request Forgery (CSRF) {#cross-site-request-forgery-csrf}

Auf das Risiko der Cross-Site Request Forgery (CSRF) wird durch die automatische Einschleusung eines kryptografischen Tokens in alle Formulare und AJAX-Anforderungen sowie durch die Verifizierung dieses Tokens auf dem Server bei jedem POST eingegangen.

Darüber hinaus ist AEM mit einem Referrer-Header-basierten Filter ausgestattet, der so konfiguriert werden kann, dass er *nur* POST-Anforderungen von bestimmten Hosts (in einer Liste definiert) zulässt.

## 6. Sicherheitsfehler {#security-misconfiguration}

Es ist unmöglich zu garantieren, dass alle Software immer korrekt konfiguriert ist. Wir bemühen uns jedoch, möglichst viele Anleitungen zur Verfügung zu stellen und die Konfiguration so einfach wie möglich zu gestalten. AEM [Integrierte Sicherheits-Konsistenzprüfungen](/help/sites-administering/operations-dashboard.md) die Ihnen dabei helfen, die Sicherheitskonfiguration auf einen Blick zu verfolgen.

In der [Sicherheitsprüfliste](/help/sites-administering/security-checklist.md) finden Sie weitere Informationen, die Ihnen Schritt für Schritt Härtungsanweisungen bereitstellen.

## 7. Unsicherer kryptografischer Speicher {#insecure-cryptographic-storage}

Kennwörter werden als kryptografische Hashes im Benutzerknoten gespeichert. Standardmäßig sind diese Knoten nur vom Administrator und vom Benutzer selbst lesbar.

Sensible Daten wie Drittanbieter-Anmeldeinformationen werden in verschlüsselter Form mit einer FIPS 140-2-zertifizierten kryptografischen Bibliothek gespeichert.

## 8. Fehler beim Einschränken des URL-Zugriffs {#failure-to-restrict-url-access}

Das Repository ermöglicht die Einstellung von [feinabgestimmten Rechten (wie durch JCR angegeben)](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) für jeden Benutzer bzw. jede Gruppe unter jedem beliebigen Pfad über Zugriffssteuerungseinträge. Zugriffbeschränkungen werden durch das Repository durchgesetzt.

## 9. Unzureichende Transportschichtsicherheit {#insufficient-transport-layer-protection}

Dieses Risiko wird durch die Server-Konfiguration gemindert (z. B. nur HTTPS).

## 10. Ungeprüfte Um- und Weiterleitungen {#unvalidated-redirects-and-forwards}

Dieses Risiko wird durch die Beschränkung aller Umleitungen an benutzerseitig bereitgestellte Ziele auf interne Standorte gemindert.
