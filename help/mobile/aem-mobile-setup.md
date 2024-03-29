---
title: AEM Mobile-Einrichtung
seo-title: AEM Mobile SetUp
description: Auf dieser Seite erfahren Sie, wie Sie AEM Mobile einrichten und damit Benutzer Inhalte in AEM erstellen und verwalten können. Auf dieser Seite finden Sie Informationen zur Integration der AEM-Instanz mit dem Cloud-basierten AEM Mobile On-demand Services-Konto und den entsprechenden Projekten.
seo-description: Follow this page for setting up AEM Mobile and thus allowing the user to create and manage the content within AEM. This page provides information on integrating the AEM instance with the cloud-based AEM Mobile On-Demand Services account and project(s).
uuid: 03bf5b56-7750-4f76-b079-43761367655a
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-on-demand-services-app
discoiquuid: 393cf504-917e-4bf6-9a8b-b7a5bd862c65
exl-id: 8f608465-7d0d-48d2-8105-ee2d4ceb727a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 5%

---

# AEM Mobile-Einrichtung{#aem-mobile-setup}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>Bestandskunden von AEM Mobile Apps, die von AEM 6.2 oder 6.3 auf AEM 6.4 migrieren, können weiterhin AEM Mobile-Apps verwenden, indem sie eine [Package aus PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/compatpack/aem-mobile-package). Neue Installationen von AEM 6.4 unterstützen jedoch nicht die Funktionalität von AEM Mobile Apps.

Um AEM zur Erstellung von Inhalten für AEM Mobile-Apps zu verwenden, müssen Sie die AEM-Instanz in das Cloud-basierte AEM Mobile On-demand Services-Konto und die -Projekte integrieren.

Führen Sie die folgenden Schritte aus, um AEM Mobile einzurichten und es dem Benutzer zu ermöglichen, Inhalte in AEM zu erstellen und zu verwalten.

## AEM Mobile-Bereitstellung {#aem-mobile-provisioning}

Gehen Sie wie folgt vor, um AEM Mobile einzurichten:

* **API-Schlüssel anfordern**: Für den Zugriff auf die On-Demand Services API müssen Sie einen API-Schlüssel anfordern. Um den API-Schlüssel anzufordern, führen Sie die [PDF-Formular](https://helpx.adobe.com/digital-publishing-solution/help/integrating-dps.html). Senden Sie das ausgefüllte Formular an den Adobe Developer-Support: [wwds@adobe.com](mailto:wwds@adobe.com)

* **Generieren der Geräte-ID und des Geräte-Tokens**: Nachdem Sie Ihren API-Schlüssel erhalten haben, können Sie die Geräte-ID und das Geräte-Token generieren. Gehen Sie zu aex.aemmobile.adobe.com und führen Sie folgende Schritte aus:

   * API-Schlüssel angeben
   * Melden Sie sich mit einer Adobe ID an, die Sie einem AEM Mobile-Projekt mit den folgenden Berechtigungen hinzugefügt haben (siehe die folgenden Schritte zum Erstellen eines Projekts)

      * Administration > Projekte und Benutzer verwalten
      * Inhalt > Inhalt hinzufügen und bearbeiten, Inhalt löschen, Inhalt anzeigen, Inhalt veröffentlichen

Wenn alle Bedingungen erfüllt sind, werden eine Geräte-ID und ein Geräte-Token generiert.

>[!NOTE]
>
>Der benötigten Adobe ID sollte Zugriff auf ein AEM Mobile-Projekt gewährt werden. Siehe [Kontoverwaltung für AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) in der Onlinehilfe.

## Erstellen von Projekten für AEM Mobile {#creating-projects-for-aem-mobile}

Wenn Sie ein Projekt erstellen, legen Sie Einstellungen für jede Plattform fest, die Sie als Ziel auswählen: iOS, Android, Windows und Desktop Web Viewer. Viele der von Ihnen angegebenen Projekteinstellungen beeinflussen das Verhalten der App.

Zum Erstellen eines Projekts müssen Sie sich über eine Adobe ID mit Übergeordneter Administratorrolle beim On-Demand Services-Portal anmelden. Die Bearbeitung eines Projekts erfordert entweder eine Übergeordnete Administrator-Rolle oder eine Benutzerrolle mit einer **Projekte und Benutzer verwalten** Berechtigung.

>[!NOTE]
>
>Um mehr über das Erstellen von Projekten in AEM Mobile zu erfahren, klicken Sie auf [here](https://helpx.adobe.com/digital-publishing-solution/help/creating-projects.html).

## Konfigurieren eines AEM Mobile Connectors {#configuring-an-aem-mobile-connector}

AEM Einrichtung umfasst die folgenden Schritte zur Connector-Konfiguration. Sobald die Konfiguration des AEM Mobile-Connectors abgeschlossen ist, kann der Benutzer Benutzergruppen und Berechtigungen einrichten.

Der AEM Mobile On-Demand-Connector wird verwendet, um AEM Mobile-verwaltete Inhalte mit den On-Demand-Diensten von Adobe Experience Manager Mobile zu verbinden. Auf diese Weise können Inhaltsautoren mithilfe der Tools von AEM Material für mobile Anwendungen erstellen und verwalten und gleichzeitig die On-Demand-Dienste von AEM Mobile zur einfachen Verteilung mobiler Inhalte nutzen.

>[!NOTE]
>
>Dies ist ein einmaliger Schritt zum Einrichten der AEM-Instanz.

### Konfigurieren des AEM Mobile On-demand Services-Clients {#configuring-aem-mobile-on-demand-services-client}

Sie müssen die Konfigurationsschritte ausführen, damit die AEM Mobile-Integrationen ordnungsgemäß funktionieren.

1. Navigieren Sie zur OSGi-Dienstkonfiguration .

   1. AEM > Tools > Vorgänge > Web-Konsole
   1. Scrollen oder Suchen Sie nach ***Experience Manager Mobile On-Demand Services Client (war Adobe Digital Publishing Solution Client)***

1. Bearbeiten ***Experience Manager Mobile On-Demand Services Client***

   1. **(Obligatorisch)** Füllen Sie die erforderlichen Felder aus:

      1. Client-ID.
      1. Client-Geheimnis.
   1. **(Optional)** Bearbeiten Sie vorhandene Werte.


1. Speichern Sie die Änderungen.
1. Im Folgenden finden Sie eine Beispielkonfiguration:

![chlimage_1-53](assets/chlimage_1-53.png)

### Konfigurieren von AEM Mobile On-demand Services Cloud Service {#configuring-aem-mobile-on-demand-services-cloudservice}

1. Zu Cloud Services wechseln

   1. AEM > Tools > Bereitstellung > [CloudServices](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html). Scrollen oder Suchen Sie nach ***Adobe Experience Manager Mobile On-Demand-Dienste***

1. Auswählen ***Jetzt konfigurieren*** oder ***Konfigurationen anzeigen*** und wählen Sie das Symbol Neue Konfiguration hinzufügen aus.

1. Neue Konfiguration erstellen

   1. Geben Sie einen Titel und einen Namen ein
   1. Geräte-ID eingeben
   1. Geräte-Token eingeben
   1. Auswählen ***Testgerätekonfiguration*** zur Validierung der eingegebenen Werte
   1. Select Ok

## Hinzufügen von AEM Mobile-Benutzerrollen und Zuweisen von Berechtigungen {#adding-aem-mobile-user-roles-and-assigning-permissions}

Nachdem Sie ein Projekt erstellt haben, sollten Sie Rollen erstellen und Benutzern Zugriff gewähren. Nur Übergeordnete Administratoren können Rollen erstellen und bearbeiten. Wenn Sie eine Rolle erstellen, aktivieren Sie die Funktionen (oder Berechtigungen) für die Benutzer, denen diese Berechtigungen zugewiesen sind. Sie können beispielsweise eine Rolle erstellen, die Berechtigungen zum Erstellen von Apps enthält, und eine andere Rolle, die Berechtigungen zum Erstellen und Veröffentlichen von Inhalten enthält.

Bei der Entwicklung von AEM Mobile-Apps gibt es drei verschiedene Rollen:

* Administrator
* Entwickler
* Autor

Weitere Informationen zum Erstellen von Rollen mit unterschiedlichen Berechtigungen wie zum Erstellen von Apps oder zum Erstellen und Veröffentlichen von Inhalten finden Sie unter [Erstellen von Benutzerrollen und Gewähren von Zugriff](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) in der AEM Mobile-Hilfe.

>[!NOTE]
>
>Die Verwaltung von App-Inhalten erfordert kollektive Anstrengungen von Entwicklern, Inhaltsautoren und Administratoren. Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden. Schließlich veröffentlichen Administratoren strategisch den aktualisierten App-Inhalt. Durch das Einrichten von AEM Gruppen und Berechtigungen werden deren Rollen im App-Dashboard oder im Control Center definiert.
>
>Weitere Informationen zum AEM Mobile Dashboard erhalten Sie durch Klick auf [here](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

Nachdem Sie die Rollen mit unterschiedlichen Berechtigungen erstellt haben, z. B. zum Erstellen von Apps oder zum Erstellen und Veröffentlichen von Inhalten, lesen Sie [**Konfigurieren von Benutzern und Benutzergruppen**](/help/mobile/aem-mobile-configure-users.md) um Ihre Benutzer und Gruppen so zu konfigurieren, dass sie die Erstellung und Verwaltung Ihrer mobilen Apps unterstützen.

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den beiden anderen Rollen und Zuständigkeiten beim Erstellen einer AEM Mobile On-demand Services App finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md)
* [Inhaltserstellung AEM AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md)

>[!NOTE]
>
>Informationen zur Vorschau der App-Inhalte, einschließlich Durchsuchen von Seiten und Artikeln, finden Sie unter [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md).
