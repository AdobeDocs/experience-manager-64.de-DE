---
title: Datenintegration für AEM Forms
seo-title: Datenintegration für AEM Forms
description: Mit der Datenintegration können Sie AEM Forms mit unterschiedlichen Datenquellen integrieren und ein Formulardatenmodell zum Erstellen und Arbeiten mit adaptiven Formularen und interaktiver Kommunikation erstellen.
seo-description: Mit der Datenintegration können Sie AEM Forms mit unterschiedlichen Datenquellen integrieren und ein Formulardatenmodell zum Erstellen und Arbeiten mit adaptiven Formularen und interaktiver Kommunikation erstellen.
uuid: 58f65ae0-cf54-4249-92c7-64b557e30491
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: b6786321-6e8e-40e2-809b-d117991246c4
feature: Formulardatenmodell
exl-id: 8cbd3fb0-3c87-433e-bfd7-0f93216a5de7
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 96%

---

# Einführung in die AEM Forms-Datenintegration {#aem-forms-data-integration}

Mit der Datenintegration können Sie AEM Forms mit unterschiedlichen Datenquellen integrieren und ein Formulardatenmodell zum Erstellen und Arbeiten mit adaptiven Formularen und interaktiver Kommunikation erstellen.

![](do-not-localize/data-integeration.png)

Unternehmensinfrastrukturen umfassen unterschiedliche Back-End-Systeme oder Datenquellen wie Datenbanken, Web-Services, REST-Services, OData-Services und CRM-Lösungen. Zusammen bilden sie ein Informationssystem, das Daten für Unternehmensanwendungen zur Abwicklung des Tagesgeschäfts bereitstellt. Umgekehrt erfassen die Anwendungen Daten und senden sie zurück, um die Datenquellen zu aktualisieren.

AEM Forms-Anwendungen wie adaptive Formulare benötigen Integration mit Datenquellen, damit Kundendaten abgerufen, Formulare ausgegeben und interaktive Kommunikation erstellt werden kann. Es gibt Anwendungsfälle, bei denen Daten basierend auf Benutzereingaben in adaptiven Formularen aus Datenquellen abgerufen werden. Zusätzlich können die übermittelten Daten im adaptiven Formular zurückgeschrieben werden, um die jeweiligen Datenquellen zu aktualisieren.

Verteilte, modulare Systeme bieten ihre Vorteile, die Herausforderung besteht jedoch darin, Datenverknüpfungen datenquellenübergreifend zu integrieren und zu erstellen. Datenintegration ist der Schlüssel zu einer funktionsfähigen und effizienten Unternehmensinfrastruktur mit unterschiedlichen Datenquellen, die für den Austausch von Geschäftsdaten mit Anwendungen verbunden sind.

## Übersicht über die Datenintegration  {#data-integration-overview}

![aem-forms-data-integration](assets/aem-forms-data-integeration.png)

AEM Forms-Datenintegration ermöglicht die Konfiguration und Verbindung verschiedener Datenquellen mit AEM Forms. In der intuitiven Benutzeroberfläche können Sie eine einheitliche Darstellung der Geschäftsbereiche und Dienste für sämtliche verbundenen Datenquellen erstellen. Diese einheitliche Darstellung wird als Formulardatenmodell bezeichnet. Es handelt sich um eine Erweiterung des JSON-Schemas. Die Entitäten in einem Formulardatenmodell werden als Datenmodellobjekte bezeichnet. Ein Formulardatenmodell gibt Ihnen folgende Möglichkeiten:

* Zugreifen auf Datenmodellobjekte, Eigenschaften und Dienste aus verbundenen Datenquellen.
* Erstellen Sie benutzerdefinierte Datenmodellobjekte und -eigenschaften
* Erstellen Sie Verknüpfungen zwischen Datenmodellobjekten innerhalb und über Datenquellen hinweg.
* Aufrufen von Diensten für Datenmodellobjekte zum Abfragen von Daten aus und Schreiben von Daten in Datenquellen.

Nachdem Sie ein Formulardatenmodell erstellt haben, können Sie es in verschiedenen Workflows für adaptive Formulare und interaktive Kommunikation verwenden, zum Beispiel:

* Erstellen adaptiver Formulare und interaktiver Kommunikation basierend auf dem Formulardatenmodell
* Vorausfüllen adaptiver Formulare und interaktiver Kommunikation aus konfigurierten Datenquellen
* Aufrufen von Datenquellendiensten/-vorgängen mit Regeln für adaptive Formulare
* Übermittelte Formulardaten in Datenquellen schreiben

## Erste Schritte mit Datenintegration  {#get-started-with-data-integration}

Der erste Schritt zur Implementierung der Datenintegration besteht darin, Datenquellen, die Informationen speichern, die Sie in Anwendungsfällen für adaptive Formulare und interaktive Kommunikation verwenden möchten, zu identifizieren und zu konfigurieren. Als Nächstes erstellen Sie ein Formulardatenmodell, das Datenmodellobjekt, Eigenschaften und Dienste aus einer oder mehreren Datenquellen verwendet. Sie können adaptive Formulare und interaktive Kommunikation basierend auf einem Formulardatenmodell erstellen, bei dem adaptive Formularfelder oder Platzhalter in interaktiver Kommunikation an die jeweiligen Datenquelleneigenschaften gebunden sind.

Mit AEM Forms können Sie auch ein Formulardatenmodell erstellen, das unabhängig von Datenquellen ist, und Datenmodellobjekte und -eigenschaften im Formulardatenmodell später mit Datenquellen verknüpfen. Dadurch werden alle Abhängigkeiten von Datenquellen beseitigt, während Sie an einem Formulardatenmodell arbeiten.

Überprüfen Sie Folgendes, um die Datenintegration zu starten, zu verstehen und zu implementieren.

* [Konfigurieren von Datenquellen](/help/forms/using/configure-data-sources.md)
* [Formulardatenmodell erstellen](/help/forms/using/create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell](/help/forms/using/work-with-form-data-model.md)
* [Verwenden eines Formulardatenmodells](/help/forms/using/using-form-data-model.md)
