---
title: Erstellen Sie Ihr erstes adaptives Formular
seo-title: Create your first adaptive form
description: 'Lernen Sie, wie Sie Business-Class-, interaktive und Responsive-Formulare erstellen. '
seo-description: Learn to create business class, interactive, and responsive forms.
page-status-flag: de-activated
uuid: 62f5222c-c787-46be-95fa-a701aa0e6115
topic-tags: introduction
discoiquuid: 4e247e70-c50a-4571-8ac1-fbbb07100262
feature: Adaptive Forms
exl-id: f634a73a-e720-4a38-a459-6ddbe4fdc565
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 94%

---

# Erstellen Sie Ihr erstes adaptives Formular {#do-not-publish-create-your-first-adaptive-form}

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Einführung {#introduction}

Sind Sie auf der Suche nach einer benutzerfreundlichen **Formularerfahrung**, die die Einschreibung vereinfacht, das Engagement erhöht und die Bearbeitungszeit verkürzt, dann passen **adaptive Formulare** perfekt für Sie. Adaptive Formulare bieten eine für Mobilgeräte, Automatisierung und Analysen geeignete Formularerfahrung. Sie können einfach Formulare erstellen, die responsiv und interaktiv sind, automatisierte Prozesse verwenden, um administrative und sich wiederholende Aufgaben zu reduzieren, und Datenanalysen verwenden, um die Erlebnisse, die Kunden mit Ihren Formularen haben, zu verbessern und zu personalisieren.

Diese Schulung bietet ein End-to-End-Framework zum Erstellen eines adaptiven Formulars. Die Schulung ist in einen Anwendungsfall und mehrere Leitfäden unterteilt. Jeder Leitfaden hilft Ihnen beim Erlernen und Hinzufügen neuer Funktionen zu dem adaptiven Formular, das in dieser Schulung erstellt wird. Sie haben nach jedem Leitfaden ein funktionierendes adaptives Formular. Der Leitfaden zum Erstellen eines adaptiven Formulars ist verfügbar. Weitere Leitfäden werden in Kürze verfügbar sein. Am Ende dieser Schulung können Sie Folgendes:

* Adaptive Formulare und ein Formulardatenmodell erstellen.
* Adaptive Formulare gestalten.
* Den Regel-Editor für adaptive Formulare zum Erstellen von Geschäftsregeln verwenden.
* Adaptive Formulare testen und veröffentlichen.

![create-daptive-form-workflow](assets/create-daptive-form-workflow.png)

Die Reise beginnt mit dem Erlernen des Anwendungsfalls:

Eine Website bietet eine Reihe von Produkten für verschiedene Kunden. Kunden durchsuchen das Portal, wählen und bestellen die Produkte. Jeder Kunde legt ein Konto an und stellt Versand- und Rechnungsadressen bereit. Eine bestehende Kundin, Sara Rose, möchte ihre Versandadresse auf der Website eintragen. Die Website bietet ein Online-Formular zum Hinzufügen und Aktualisieren von Versandadressen.

Die Website wird mit Adobe Experience Manager (AEM) ausgeführt und verwendet AEM Forms für die Erfassung und Verarbeitung von Daten. Das Formular zum Hinzufügen und Aktualisieren von Adressen ist ein adaptives Formular. Die Website speichert Kundendaten in einer Datenbank. Das Formular zum Hinzufügen und Aktualisieren von Adressen dient dazu, verfügbare Adressen abzurufen und anzuzeigen. Außerdem wird das adaptive Formular dazu verwendet, aktualisierte und neue Adressen zu akzeptieren.

### Voraussetzung {#prerequisite}

* Eine AEM Author-Instanz einrichten.
* Installieren Sie das [AEM Forms-Add-On](/help/forms/using/installing-configuring-aem-forms-osgi.md) auf der Author-Instanz.
* Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Die Beispiele in diesem Tutorial basieren auf der MySQL-Datenbank und verwenden den [MySQL JDBC-Datenbanktreiber von Oracle](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Richten Sie eine Datenbank mit Kundendaten in den unten gezeigten Feldern ein. Eine Datenbank ist nicht unbedingt notwendig zum Erstellen eines adaptiven Formulars. In diesem Lernprogramm wird eine Datenbank zur Demonstration der Formulardatenmodell- und Persistenzfunktionen von AEM Forms verwendet.

![adaptiveformdata](assets/adaptiveformdata.png)

## Schritt 1: Erstellen Sie ein adaptives Formular {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small_new](assets/03-create-adaptive-form-main-image_small_new.png)

Adaptive Formulare repräsentieren eine neue Generation: ansprechend, interaktiv, dynamisch und anpassungsfähig. Mit adaptiven Formularen können Sie personalisierte und zielgerichtete Erlebnisse bieten. AEM Forms bietet einen Drag &amp; Drop-WYSIWYG-Editor zum Erstellen von adaptiven Formularen. Weitere Informationen zu adaptiven Formularen finden Sie unter [Einführung in das Authoring adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md).

Ziele:

* Erstellen Sie ein adaptives Formular, mit dem ein Kunde eine Versandadresse hinzufügen kann
* Layout-Felder eines adaptiven Formulars zum Anzeigen und Akzeptieren von Informationen eines Kunden
* Erstellen Sie eine Sendeaktion zum Senden einer E-Mail mit Formularinhalt
* Anzeigen und Senden eines adaptiven Formulars in der Vorschau

[ ](create-adaptive-form.md)

## Schritt 2: Erstellen Sie ein Formulardatenmodell {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Ein Formulardatenmodell ermöglicht es, ein adaptives Formular mit unterschiedlichen Datenquellen zu verbinden. Zum Beispiel AEM-Benutzerprofil, RESTful-Webdienste, SOAP-basierte Webdienste, OData-Dienste und relationale Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datenrepräsentationsschema von Geschäftseinheiten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einem adaptiven Formular verwenden, um Daten von verbundenen Datenquellen abzurufen, zu aktualisieren, zu löschen und ihnen hinzuzufügen.

Ziele:

* Konfigurieren der Datenbankinstanz der Website (MySQL-Datenbank) als Datenquelle
* Erstellen des Formulardatenmodells mithilfe der MySQL-Datenbank als Datenquelle
* Hinzufügen von Datenmodellobjekten zum Datenmodell
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten

[ ](create-form-data-model.md)

## Schritt 3: Wenden Sie Regeln auf adaptive Formularfelder an {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Adaptive Formulare stellen einen Editor zum Schreiben von Regeln für adaptive Formularobjekte bereit. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Dies hilft, die Genauigkeit zu gewährleisten, und beschleunigt das Ausfüllen der Formulare.

Ziele:

* Erstellen und Anwenden von Regeln in adaptiven Formularfeldern
* Verwenden Sie Regeln zum Auslösen von Formulardatenmodelldiensten, um Daten in der Datenbank zu aktualisieren 

## Schritt 4: Gestalten Sie Ihr adaptives Formular {#step-style-your-adaptive-form}

![09-Style-your-adaptive-form_small](assets/09-Style-your-adaptive-form_small.png)

Adaptive Formulare bieten Designs und einen [Editor](/help/forms/using/themes.md), um Designs für die adaptiven Formulare zu erstellen. Ein Design umfasst Formatierungsdetails für Komponenten und Bereiche und Sie können ein Design in verschiedenen Formularen wiederverwenden. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie das Design auf ein Formular anwenden, wird der festgelegte Stil auf die entsprechenden Komponenten des Formulars angewendet. Adaptive Formulare unterstützen auch das Inline-Styling für Designs, die spezifisch für ein Formular sind.

Ziele:

* Wenden Sie ein Standarddesign auf ein adaptives Formular an
* Erstellen Sie mithilfe des Designeditors ein Design für das adaptive Formular
* Verwenden von Webfonts in einem benutzerdefinierten Design

[ ](style-your-adaptive-form.md)

## Schritt 5: Testen Sie Ihr adaptives Formular {#step-test-your-adaptive-form}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

Adaptive Formulare sind für die Interaktion mit Ihren Kunden von wesentlicher Bedeutung. Es ist wichtig, Ihre adaptiven Formulare bei jeder Änderung, die Sie daran vornehmen, zu testen. Das Testen jedes Felds eines Formulars ist mühsam. AEM Forms bietet ein SDK (Calvin SDK) zum automatischen Testen von adaptiven Formularen. Calvin ermöglicht es Ihnen das automatische Testen der adaptiven Formulare im Webbrowser.

Ziele:

* Installieren von Calvin SDK
* Erstellen einer Testsuite und von Testfällen für das Formular zum Ändern von Adressen

Weitere Informationen zum SDK finden Sie unter [Verwenden automatisierter Tests mit AEM adaptiven Formular](/help/forms/using/calvin.md).

## Schritt 6: Veröffentlichen Sie Ihr adaptives Formular {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Sie können adaptive Formulare als eigenständige Formulare (Einzelseitenanwendung) veröffentlichen, sie auf der AEM[-Sites-Seite](/help/forms/using/embed-adaptive-form-aem-sites.md) einbeziehen oder sie auf einer AEM-Site über das[ Forms Portal](/help/forms/using/introduction-publishing-forms.md) auflisten.

Ziele:

* Veröffentlichen des adaptiven Formulars als Einzelseitenanwendung 
