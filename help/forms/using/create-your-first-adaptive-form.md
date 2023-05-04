---
title: Erstellen Sie Ihr erstes adaptives Formular
seo-title: Create your first adaptive form
description: Lernen Sie, wie Sie Business-Class-, interaktive und Responsive-Formulare erstellen.
seo-description: Learn to create business class, interactive, and responsive forms.
page-status-flag: de-activated
uuid: 62f5222c-c787-46be-95fa-a701aa0e6115
topic-tags: introduction
discoiquuid: 4e247e70-c50a-4571-8ac1-fbbb07100262
feature: Adaptive Forms
exl-id: f634a73a-e720-4a38-a459-6ddbe4fdc565
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 37%

---

# Erstellen Sie Ihr erstes adaptives Formular {#do-not-publish-create-your-first-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Einführung {#introduction}

Suchen Sie einen mobilfreundlichen **Formularerfahrung** das die Einschreibung vereinfacht, die Interaktion erhöht und die Bearbeitungszeit verkürzt, **adaptive Formulare** ist perfekt für dich geeignet. Adaptive Formulare bieten ein mobiles, automatisierungs- und analysefreundliches Formularerlebnis. Sie können einfach Formulare erstellen, die responsiv und interaktiv sind, automatisierte Prozesse verwenden, um administrative und sich wiederholende Aufgaben zu reduzieren, und Datenanalysen verwenden, um die Erlebnisse, die Kunden mit Ihren Formularen haben, zu verbessern und zu personalisieren.

Dieses Tutorial bietet ein End-to-End-Framework zum Erstellen eines adaptiven Formulars. Das Tutorial ist in einen Anwendungsfall und mehrere Handbücher unterteilt. Jedes Handbuch hilft Ihnen dabei, neue Funktionen zu lernen und zum adaptiven Formular hinzuzufügen, das in diesem Tutorial erstellt wird. Sie haben nach jedem Handbuch ein funktionierendes adaptives Formular. Das Handbuch zum Erstellen eines adaptiven Formulars ist verfügbar. Nachfolgende Handbücher werden in Kürze verfügbar sein. Am Ende dieser Schulung können Sie Folgendes:

* Erstellen Sie ein adaptives Formular und ein Formulardatenmodell.
* Gestalten Sie Ihr adaptives Formular.
* Verwenden Sie den Regeleditor für adaptive Formulare, um Geschäftsregeln zu erstellen.
* Testen und veröffentlichen Sie ein adaptives Formular.

![create-daptive-form-workflow](assets/create-daptive-form-workflow.png)

Die Journey beginnt mit dem Erlernen des Anwendungsfalls:

Eine Website bietet eine Reihe von Produkten für verschiedene Kunden. Kunden durchsuchen das Portal, wählen die Produkte aus und bestellen sie. Jeder Kunde erstellt ein Konto und stellt Versand- und Rechnungsadressen bereit. Eine bestehende Kundin, Sara Rose, möchte ihre Versandadresse zur Website hinzufügen. Die Website bietet ein Online-Formular zum Hinzufügen und Aktualisieren von Versandadressen.

Die Website wird auf Adobe Experience Manager (AEM) ausgeführt und verwendet AEM Forms für die Datenerfassung und -verarbeitung. Das Formular zum Hinzufügen und Aktualisieren von Adressen ist ein adaptives Formular. Die Website speichert Kundendetails in einer Datenbank. Das Formular zum Hinzufügen und Aktualisieren von Adressen dient dazu, verfügbare Adressen abzurufen und anzuzeigen. Sie verwenden auch das adaptive Formular, um aktualisierte und neue Adressen zu akzeptieren.

### Voraussetzung {#prerequisite}

* Eine AEM Author-Instanz einrichten.
* Installieren Sie das [AEM Forms-Add-On](/help/forms/using/installing-configuring-aem-forms-osgi.md) auf der Author-Instanz.
* Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Die Beispiele in diesem Tutorial basieren auf der MySQL-Datenbank und verwenden den [MySQL JDBC-Datenbanktreiber von Oracle](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Richten Sie eine Datenbank mit Kundendaten mit den unten angezeigten Feldern ein. Eine Datenbank ist nicht erforderlich, um ein adaptives Formular zu erstellen. In diesem Tutorial wird eine Datenbank verwendet, um Formulardatenmodell und Persistenzfunktionen von AEM Forms anzuzeigen.

![adaptiveformdata](assets/adaptiveformdata.png)

## Schritt 1: Erstellen Sie ein adaptives Formular {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small_new](assets/03-create-adaptive-form-main-image_small_new.png)

Adaptive Formulare sind neue Generationen, ansprechend, responsiv, dynamisch und adaptiv. Mit adaptiven Formularen können Sie personalisierte und zielgerichtete Erlebnisse bereitstellen. AEM Forms bietet einen Drag &amp; Drop-WYSIWYG-Editor zum Erstellen adaptiver Formulare. Weitere Informationen zu adaptiven Formularen finden Sie unter [Einführung in das Authoring adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md).

Ziele:

* Erstellen eines adaptiven Formulars, mit dem ein Kunde eine Versandadresse hinzufügen kann
* Layout-Felder eines adaptiven Formulars zum Anzeigen und Akzeptieren von Informationen eines Kunden
* Erstellen Sie eine Sendeaktion zum Senden einer E-Mail mit Formularinhalt
* Anzeigen und Senden eines adaptiven Formulars in der Vorschau

[ ](create-adaptive-form.md)

## Schritt 2: Erstellen Sie ein Formulardatenmodell {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Ein Formulardatenmodell ermöglicht die Verbindung eines adaptiven Formulars mit unterschiedlichen Datenquellen. Zum Beispiel AEM Benutzerprofil, RESTful-Webdienste, SOAP-basierte Webdienste, OData-Dienste und relationale Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datendarstellungsschema von Geschäftsentitäten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einem adaptiven Formular verwenden, um Daten abzurufen, zu aktualisieren, zu löschen und zu verbundenen Datenquellen hinzuzufügen.

Ziele:

* Konfigurieren der Datenbankinstanz der Website (MySQL-Datenbank) als Datenquellen
* Erstellen des Formulardatenmodells mit der MySQL-Datenbank als Datenquelle
* Hinzufügen von Datenmodellobjekten zum Datenmodell
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten

[ ](create-form-data-model.md)

## Schritt 3: Wenden Sie Regeln auf adaptive Formularfelder an {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Adaptive Formulare stellen einen Editor zum Schreiben von Regeln für adaptive Formularobjekte bereit. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Dies hilft, die Genauigkeit zu gewährleisten, und beschleunigt das Ausfüllen der Formulare.

Ziele:

* Erstellen und Anwenden von Regeln auf adaptive Formularfelder
* Verwenden Sie Regeln zum Auslösen von Formulardatenmodelldiensten, um Daten in der Datenbank zu aktualisieren 

## Schritt 4: Gestalten Sie Ihr adaptives Formular {#step-style-your-adaptive-form}

![09-Style-your-adaptive-form_small](assets/09-Style-your-adaptive-form_small.png)

Adaptive Formulare bieten Designs und einen [Editor](/help/forms/using/themes.md), um Designs für die adaptiven Formulare zu erstellen. Ein Design enthält Stildetails für Komponenten und Bereiche und Sie können ein Design in verschiedenen Formularen wiederverwenden. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie das Design auf Ihr Formular anwenden, spiegelt der angegebene Stil die entsprechenden Komponenten des Formulars wider. Adaptive Formulare unterstützen auch die Inline-Formatierung für Formularstile.

Ziele:

* Anwenden eines Standarddesigns auf ein adaptives Formular
* Erstellen eines Designs für ein adaptives Formular mit dem Design-Editor
* Verwenden von Webfonts in einem benutzerdefinierten Design

[ ](style-your-adaptive-form.md)

## Schritt 5: Testen Sie Ihr adaptives Formular {#step-test-your-adaptive-form}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

Adaptive Formulare sind für die Interaktion mit Ihren Kunden von wesentlicher Bedeutung. Es ist wichtig, Ihre adaptiven Formulare bei jeder Änderung, die Sie daran vornehmen, zu testen. Das Testen jedes Felds eines Formulars ist mühsam. AEM Forms bietet ein SDK (Calvin SDK) zur Automatisierung des Testens adaptiver Formulare. Calvin ermöglicht es Ihnen das automatische Testen der adaptiven Formulare im Webbrowser.

Ziele:

* Installieren des Calvin SDK
* Erstellen von Test-Suites und Testfällen für das Formular &quot;Adresse ändern&quot;

Weitere Informationen zum SDK finden Sie unter [Verwenden automatisierter Tests mit AEM adaptiven Formular](/help/forms/using/calvin.md).

## Schritt 6: Veröffentlichen Sie Ihr adaptives Formular {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Sie können adaptive Formulare als eigenständiges Formular veröffentlichen (Einzelseitenanwendung), in AEM einschließen [Siteseite](/help/forms/using/embed-adaptive-form-aem-sites.md)oder auf einer AEM Site mit [Forms Portal](/help/forms/using/introduction-publishing-forms.md).

Ziele:

* Veröffentlichen des adaptiven Formulars als Einzelseitenanwendung
