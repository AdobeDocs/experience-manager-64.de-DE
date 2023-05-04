---
title: Datenschutzbestimmungen – Einhaltung durch Adobe Experience Manager
seo-title: Adobe Experience Manager Readiness for Data Protection and Data Privacy Regulations; such as GDPR, CCPA, etc
description: Erfahren Sie mehr über die Unterstützung von Adobe Experience Manager für die verschiedenen Datenschutzbestimmungen, darunter die EU-Datenschutz-Grundverordnung (DSGVO), das kalifornische Verbraucherdatenschutzgesetz (CCPA) und die Einhaltung der Vorschriften bei der Implementierung eines neuen Projekts in AEM
seo-description: Learn about Adobe Experience Manager support for the various Data Protection and Data Privacy Regulations; including the EU General Data Protection Regulation (GDPR), the California Consumer Privacy Act and how to comply when implementing a new AEM project.
uuid: c443aa47-0766-4280-b0f2-b5b06534ffba
contentOwner: AEM Docs
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: grdp, introduction
discoiquuid: 93e71efe-c1c6-4d83-9b57-6c70f7bc0b80
exl-id: 46ad04b1-a660-4cdd-8649-5cdb00dbcae3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 76%

---

# Adobe Experience Manager – Einhaltung von Datenschutzbestimmungen {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um Ratschläge zu Datenschutzbestimmungen zu erhalten.

>[!NOTE]
>
>Weitere Informationen über die Reaktion von Adobe auf Datenschutzprobleme und was dies für Sie als Adobe-Kunde bedeutet, finden Sie im [Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy.html).

Adobe stellt Dokumentationen und Verfahren (sofern verfügbar auch unter Verwendung von APIs) bereit, die Datenschutz- und AEM-Administratoren für die Handhabung von datenbezogenen Anfragen verwenden können und die unsere Kunden dabei unterstützen, die Anforderungen dieser Verordnungen zu erfüllen. Mithilfe der beschriebenen Verfahren können DSGVO-bezogene Anfragen entweder manuell oder API-gestützt (sofern verfügbar) über ein externes Portal oder einen externen Service verarbeitet werden.

>[!CAUTION]
>
>Die hier dokumentierten Details sind auf Adobe Experience Manager beschränkt.
>
>Daten aus einem anderen Adobe-On-Demand-Service und alle damit verbundenen Datenschutzanfragen erfordern, dass für diesen Service Maßnahmen ergriffen werden.
>
>Weitere Informationen finden Sie unter [Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy.html).

## Einführung {#introduction}

Die Instanzen von Adobe Experience Manager und die darauf ausgeführten Anwendungen liegen in der Verantwortung unserer Kunden und werden von ihnen betrieben.

Daher sind Datenschutzbestimmungen wie die DSGVO, der CCPA und andere größtenteils Sache der Kunden.

In einer kurzen Einführung enthalten die Vorschriften für Datenschutz neue Regeln, denen die nachstehenden Rollen folgen müssen:

* Unternehmens-Entitäten (CCPA) und/oder Datenverantwortliche (DSGVO)

* Dienstleister (CCPA) und/oder Auftragsverarbeiter (DSGVO)

Die wichtigsten Bestimmungen dieser Verordnungen sind:

1. Erweiterte Definition personenbezogener Daten, um alle eindeutigen Kennungen einzuschließen; wie in direkt und indirekt identifizierbaren Daten.

2. Verschärfte Anforderungen an das Einverständnis.

3. Verstärkter Fokus auf Löschrechte (Datenlöschung).

4. Opt-out vom Verkauf von Daten.

Für Adobe Experience Manager gilt:

* Die Instanzen und die darauf ausgeführten Anwendungen liegen in der Verantwortung unserer Kunden und werden von ihnen betrieben.

   * Dies bedeutet effektiv, dass der Kunde die regulatorischen Rollen verwaltet, darunter Unternehmens-Entitäten und Dienstleister, Datenverantwortliche und Auftragsverarbeiter.

   * Der Adobe Experience Platform Privacy Service ist nicht Teil des Workflows für AEM, wie in der folgenden Abbildung dargestellt.

* AEM umfasst Dokumentationen und Verfahren für den Datenschutzadministrator und/oder AEM-Administrator des Kunden, die Datenschutzanfragen manuell oder über APIs (sofern verfügbar) zu bearbeiten.

* Es wurde kein neuer Service und keine neue Benutzeroberfläche hinzugefügt.

   * Stattdessen werden Verfahren und APIs für die Verwendung durch die Benutzeroberflächen/Portale von Kunden dokumentiert, die Datenschutzanfragen bearbeiten.

* AEM enthält keine vorkonfigurieren Tools zur Unterstützung des Workflows für Datenschutzanfragen.

   * Adobe stellt dem Datenschutzadministrator und/oder AEM Administrator des Kunden Dokumentationen und Verfahren zur Verfügung, mit denen er Anfragen im Zusammenhang mit den Datenschutzbestimmungen manuell bearbeiten kann.

Adobe bietet Verfahren für die Bearbeitung von Datenschutzanfragen im Zusammenhang mit Zugriff, Löschen und Opt-out für Adobe Experience Manager. In einigen Fällen sind APIs verfügbar, die von einem vom Kunden entwickelten Portal oder von Skripten aufgerufen werden können, um die Automatisierung zu unterstützen.

Die folgende Abbildung zeigt, wie ein Workflow für Datenschutzanfragen aussehen könnte (unter Verwendung von Adobe Experience Manager 6.5):

![Datenschutz](assets/data-protection-and-privacy-01.png)

## Befolgung der Vorschriften durch Adobe Experience Manager {#aem-and-regulatory-readiness}

In den folgenden Abschnitten finden Sie die Dokumentation zu Vorschriften für einzelne Produktbereiche von AEM.

## AEM Foundation {#aem-foundation}

Siehe [Umgang mit Datenschutzanfragen für die AEM Foundation](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

## AEM der Aktivierung der Sammlung von aggregierten Nutzungsstatistiken {#aem-opting-into-aggregate-usage-statistics-collection}

Siehe [Aggregierte Sammlung von Nutzungsstatistiken](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

## AEM Sites {#aem-sites}

Siehe [AEM Sites – Einhaltung von Datenschutzbestimmungen.](/help/sites-administering/gdpr-compliance-sites.md)

## AEM Commerce {#aem-commerce}

Siehe [AEM Commerce – Einhaltung von Datenschutzbestimmungen](/help/sites-administering/gdpr-compliance-commerce.md).

## AEM Mobile {#aem-mobile}

Siehe [AEM Mobile – Einhaltung von Datenschutzbestimmungen](/help/mobile/aem-mobile-gdpr-compliance.md).

## AEM-Integration mit Adobe Target und Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Diese Adobe Experience Manager-Integrationen verfügen über datenschutzfreundliche Dienste (z. B. DSGVO oder CCPA). In AEM werden keine personenbezogenen Daten von Adobe Target oder Adobe Analytics in Bezug auf die Integrationen gespeichert.
Weitere Informationen finden Sie unter:

* [Adobe Target – Datenschutzübersicht](https://experienceleague.adobe.com/docs/target/using/implement-target/before-implement/privacy/privacy.html?lang=de)

* [Adobe Analytics-Datenschutz-Workflow](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-workflow.html?lang=de)

## AEM Communities {#aem-communities}

AEM Communities gibt den betroffenen Personen das Recht auf ihre Datenübertragbarkeit, ihr Recht auf Zugriff und ihr Recht auf Vergessenwerden mittels [vordefinierte APIs](/help/communities/user-ugc-management-service.md). Diese APIs ermöglichen das Löschen und den Massenexport benutzergenerierter Inhalte sowie die Deaktivierung von Benutzerkonten, die über autorisierbare IDs identifiziert werden. Das permanente Löschen des Benutzerkontos ist jedoch durch das Löschen des Benutzerknotens in CRXDE Lite realisierbar, wodurch die Notwendigkeit eines einfachen Opt-out aus dem System abgedeckt wird.

Darüber hinaus bietet AEM Communities aufgrund der Massenmoderationskonsole, die es privilegierten Mitgliedern ermöglicht, Beiträge und Details der Benutzer zu finden und zu löschen, eingebauten Datenschutz. Die Mitgliederverwaltungskonsole ermöglicht die Beschränkung auf den Punkt, an dem ein Mitarbeiter verboten wird. Darüber hinaus werden die betroffenen Personen ermächtigt, die von ihnen erstellten Beiträge zu löschen.

## AEM Forms {#aem-forms}

AEM Forms umfasst Komponenten und Workflows, die Daten erfassen, verarbeiten und speichern, um Geschäftsprozesse zu koordinieren und digitale Transaktionen abzuschließen. Verschiedene Komponenten verwenden verschiedene Datenspeicher und ermöglichen auch die Integration in benutzerdefinierte Datenspeicher. In der folgenden Dokumentation werden Verfahren und Richtlinien für den Zugriff auf und die Verarbeitung von Benutzerdaten erläutert, um Datenschutzarbeitsabläufe (z. B. DSGVO oder CCPA) für eine Komponente zu unterstützen.

* [Formularportal](/help/forms/using/forms-portal-handling-user-data.md)
* [Korrespondenzverwaltung](/help/forms/using/correspondence-management-handling-user-data.md)
* [Integration mit Acrobat Sign](/help/forms/using/integration-adobe-sign-handling-user-data.md)
* [Forms-zentrierte Workflows auf OSGi](/help/forms/using/forms-workflow-osgi-handling-user-data.md)
* [Forms JEE-Workflows](/help/forms/using/forms-workflow-jee-handling-user-data.md) (Nur AEM Forms JEE)
* [Document Security](/help/forms/using/document-security-handling-user-data.md) (Nur AEM Forms JEE)
* [Benutzerverwaltung](/help/forms/using/user-management-handling-user-data.md) (Nur AEM Forms JEE)
