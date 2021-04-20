---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites
audience: end-user
user-guide-title: AEM 6.4-Implementierungsanleitung
breadcrumb-title: Implementierungsanleitung
user-guide-description: Erfahren Sie mehr über die Installation, Bereitstellung und Architektur von Adobe Experience Manager 6.4, einschließlich der Adobe Managed Services-Cloud-Implementierung.
feature-set: Experience Manager Sites
feature: Deploying
role: Architect
translation-type: tm+mt
source-git-commit: ca18aa3d207aa9506d22286eaaabdd0991d8e4e7
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 93%

---


# AEM 6.4 Bereitstellen des Benutzerhandbuchs {#deploying}

+ [Bereitstellungshandbuch für Benutzer](home.md)
+ Einführung in die AEM-Plattform {#introduction}
   + [Einführung in die AEM-Plattform](platform.md)
   + [Technische Anforderungen](technical-requirements.md)
   + [Speicherelemente in AEM 6.4](storage-elements-in-aem-6.md)
   + [AEM mit MongoDB](aem-with-mongodb.md)
+ Bereitstellen von AEM {#deploying}
   + [Bereitstellen und Verwalten](deploy.md)
   + [Empfohlene Bereitstellungen](recommended-deploys.md)
   + [Anwendungsserver-Installation](application-server-install.md)
   + [Benutzerdefinierte Standalone-Installation](custom-standalone-install.md)
   + [Start und Stopp über die Befehlszeile](command-line-start-and-stop.md)
   + [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](data-store-config.md)
   + [Revisionsbereinigung](revision-cleanup.md)
   + [Ausführen von AEM mit der TarMK-Cold-Standby-Funktion](tarmk-cold-standby.md)
   + [RDBMS-Unterstützung in AEM 6.4](rdbms-support-in-aem.md)
   + [Oak-Abfragen und Indizierung](queries-and-indexing.md)
   + [Indizieren mit dem Oak-run JAR](indexing-via-the-oak-run-jar.md)
   + [Oak-run.jar – Indizierungsanwendungsfälle](oak-run-indexing-usecases.md)
   + [Fehlerbehebung bei Oak-Indizes](troubleshooting-oak-indexes.md)
   + [Aktivieren der aggregierten Sammlung von Nutzungsstatistiken](opt-in-aggregated-usage-statistics.md)
   + [Fehlerbehebung](troubleshooting.md)
+ Konfigurieren von AEM {#configuring}
   + [Grundlegende Konfigurationskonzepte](configuring.md)
   + [Protokollierung](configure-logging.md)
   + [Konfigurieren von OSGi](configuring-osgi.md)
   + [OSGi-Konfigurationseinstellungen](osgi-configuration-settings.md)
   + [Ausführungsmodi](configure-runmodes.md)
   + [Web-Konsole](web-console.md)
   + [Replikation](replication.md)
   + [Replizieren mit MSSL](mssl-replication.md)
   + [Fehlerbehebung bei Replikationsproblemen](troubleshoot-rep.md)
   + [Ablauf statischer Objekte](expiration-static-objects.md)
   + [Versionsbereinigung](version-purging.md)
   + [Überwachung und Wartung der AEM-Instanz](monitoring-and-maintaining.md)
   + [Abladen von Aufträgen](offloading.md)
   + [Single Sign-On](single-sign-on.md)
   + [Ressourcenzuordnung](resource-mapping.md)
   + [Aktivieren von HTTP über SSL](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/configuring/ssl-by-default.html)
   + [Konsistenz- und Ausnahmeprüfungen](consistency-check.md)
   + [Leistungsrichtlinien](performance-guidelines.md)
   + [Leistungsoptimierung](configuring-performance.md)
   + [Handbuch zur Leistung von Assets](assets-performance-sizing.md)
   + [Artikel mit Anleitungen für die Konfiguration](ht-deploy.md)
   + [Entfernen der Geometrixx-Websites](removing-the-geometrixx-sites.md)
   + [Web-Konsole konfigurieren](configuring-web-console.md)
+ Aktualisieren auf AEM 6.4 {#upgrading}
   + [Aktualisieren auf AEM 6.4](upgrade.md)
   + [Planung der Aktualisierung](upgrade-planning.md)
   + [Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor ](pattern-detector.md)
   + [Abwärtskompatibilität in AEM 6.4](backward-compatibility.md) 
   + [Aktualisierungsverfahren](upgrade-procedure.md)
   + [Verwenden der Offline-Neudezierung, um Ausfallzeiten während einer Aktualisierung zu reduzieren](upgrade-offline-reindexing.md)
   + [Durchführen einer In-Place-Aktualisierung](in-place-upgrade.md)
   + [Lazy-Content-Migration](lazy-content-migration.md)
   + [Verwendung des CRX2OAK-Migrationstools](using-crx2oak.md)
   + [Wartungsaufgaben vor einer Aktualisierung](pre-upgrade-maintenance-tasks.md)
   + [Prüfungen und Fehlerbehebung nach einer Aktualisierung](post-upgrade-checks-and-troubleshooting.md)
   + [Aktualisieren von benutzerdefinierten Suchformularen](upgrading-custom-search-forms.md)
   + [Nachhaltige Aktualisierungen](sustainable-upgrades.md) 
   + [Aktualisierung von Code und Anpassungen](upgrading-code-and-customizations.md)
   + [Schritte zur Aktualisierung von Installationen auf Anwendungsservern](app-server-upgrade.md)
   + [Liste der nach dem Upgrade deinstallierten veralteten Bundles](obsolete-bundles.md)
+ Repository-Neustrukturierung {#restructuring}
   + [Repository-Neustrukturierung in AEM 6.4](repository-restructuring.md)
   + [Repository-Neustrukturierung für alle Lösungen in AEM 6.4](all-repository-restructuring-in-aem-6-4.md)
   + [Repository-Neustrukturierung in AEM 6.4](sites-repository-restructuring-in-aem-6-4.md)
   + [Assets-Repository-Neustrukturierung in AEM 6.4](assets-repository-restructuring-in-aem-6-4.md)
   + [Dynamic Media: Repository-Neustrukturierung in AEM 6.4](dynamicmedia-repository-restructuring-in-aem-6-4.md)
   + [Forms-Repository-Neustrukturierung in AEM 6.4](forms-repository-restructuring-in-aem-6-4.md)
   + [E-Commerce-Repository-Neustrukturierung in AEM 6.4](ecommerce-repository-restructuring-in-aem-6-4.md)
   + [Repository-Neustrukturierung für AEM Communities in 6.4](communities-repository-restructuring-in-aem-6-4.md)
+ E-Commerce {#ecommerce}
   + [E-Commerce-Übersicht](ecommerce.md)
   + [SAP Commerce Cloud](sap-commerce-cloud.md)
   + [Salesforce Commerce Cloud](https://github.com/adobe/commerce-salesforce)
   + [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)
+ Best Practices {#practices}
   + [Best Practices für die Bereitstellung](best-practices.md)
   + [Leistungsübersicht](performance-tree.md)
   + [Best Practices für Leistungstests](best-practices-for-performance-testing.md) 
   + [Best Practices für Abfragen und Indizierung](best-practices-for-queries-and-indexing.md)
   + [Empfehlungen für Kunden zur Benutzeroberfläche](ui-recommendations.md)
   + [Leistung und Skalierbarkeit](performance.md)


<!--

To be removed:
[Quickstart for AEM Screens](setting-up-a-basic-project-screens.md)
[Device Control Center](device-control-center.md)
[repository-restructuring-in-aem64](repository-restructuring-in-aem64.md)
[Web Console] (configuring-web-console.md)
[Configuring and Deploying AEM Screens](configuring-screens-introduction.md)
[Kickstart Guide](kickstart-for-aem-screens.md)
/help/sites/deploying/using/performance-lp.md
/help/sites-deploying/do-not-delete-performance-guidelines-pdf.md
/help/sites-deploying/removing-the-geometrixx-sites.md
/help/sites-deploying/consistency-check.md

Redirects:
[(Enabling HTTP Over SSL)](config-ssl.md) redirect to /content/help/en/experience-manager/6-4/sites-administering/ssl-by-default
-->
