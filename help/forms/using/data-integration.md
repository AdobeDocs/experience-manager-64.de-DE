---
title: Datenintegration für AEM Forms
seo-title: AEM Forms Data Integration
description: Mit der Datenintegration können Sie AEM Forms mit unterschiedlichen Datenquellen integrieren und ein Formulardatenmodell erstellen, um adaptive Formulare und interaktive Kommunikation zu erstellen und zu verwenden.
seo-description: Data Integration lets you integrate AEM Forms with disparate data sources and create form data model to create and work with adaptive forms and interactive communications.
uuid: 58f65ae0-cf54-4249-92c7-64b557e30491
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: b6786321-6e8e-40e2-809b-d117991246c4
feature: Form Data Model
exl-id: 8cbd3fb0-3c87-433e-bfd7-0f93216a5de7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 37%

---

# Einführung in die AEM Forms-Datenintegration {#aem-forms-data-integration}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit der Datenintegration können Sie AEM Forms mit unterschiedlichen Datenquellen integrieren und ein Formulardatenmodell erstellen, um adaptive Formulare und interaktive Kommunikation zu erstellen und zu verwenden.

![](do-not-localize/data-integeration.png)

Unternehmensinfrastrukturen umfassen unterschiedliche Back-End-Systeme oder Datenquellen wie Datenbanken, Webservices, REST-Services, OData-Services und CRM-Lösungen. Zusammen bilden sie ein Informationssystem, das Daten für Unternehmensanwendungen zur Abwicklung des Tagesgeschäfts bereitstellt. Umgekehrt erfassen die Anwendungen Daten und senden sie zurück, um die Datenquellen zu aktualisieren.

AEM Forms-Anwendungen wie adaptive Formulare und interaktive Kommunikation erfordern die Integration mit Datenquellen, um Kundendaten beim Rendern von Formularen und Erstellen interaktiver Kommunikation abzurufen. Es gibt Anwendungsfälle, in denen Daten basierend auf Benutzereingaben in adaptiven Formularen aus Datenquellen abgerufen werden. Darüber hinaus können die gesendeten adaptiven Formulardaten zurückgeschrieben werden, um die entsprechenden Datenquellen zu aktualisieren.

Ein verteiltes, modulares System hat seine eigenen Vorteile, aber die Herausforderung besteht darin, Datenverknüpfungen über Datenquellen hinweg zu integrieren und zu erstellen. Datenintegration ist der Schlüssel zu einer funktionsfähigen und effizienten Unternehmensinfrastruktur mit unterschiedlichen Datenquellen, die für den Austausch von Geschäftsdaten mit Anwendungen verbunden sind.

## Übersicht über die Datenintegration {#data-integration-overview}

![aem-forms-data-integeration](assets/aem-forms-data-integeration.png)

Die Datenintegration von AEM Forms ermöglicht die Konfiguration und Verbindung verschiedener Datenquellen mit AEM Forms. In der intuitiven Benutzeroberfläche können Sie eine einheitliche Datendarstellung der Geschäftsbereiche und Services für sämtliche verbundenen Datenquellen erstellen. Diese einheitliche Darstellung wird als Formulardatenmodell bezeichnet. Es handelt sich um eine Erweiterung des JSON-Schemas. Die Entitäten in einem Formulardatenmodell werden als Datenmodellobjekte bezeichnet. Mit einem Formulardatenmodell können Sie:

* Zugreifen auf Datenmodellobjekte, Eigenschaften und Services aus verbundenen Datenquellen.
* Erstellen benutzerdefinierter Datenmodellobjekten und -eigenschaften.
* Erstellen von Verknüpfungen zwischen Datenmodellobjekten innerhalb und zwischen Datenquellen.
* Aufrufen von Services für Datenmodellobjekte zum Abfragen von Daten aus und Schreiben von Daten in Datenquellen.

Nachdem Sie ein Formulardatenmodell erstellt haben, können Sie es in verschiedenen Arbeitsabläufen für adaptive Formulare und interaktive Kommunikation verwenden, z. B.:

* Erstellen adaptiver Formulare und interaktiver Kommunikation basierend auf dem Formulardatenmodell
* Ausfüllen adaptiver Formulare und interaktiver Kommunikation aus konfigurierten Datenquellen 
* Aufrufen von Datenquellendiensten/-vorgängen mithilfe von Regeln für adaptive Formulare
* Schreiben gesendeter adaptiver Formulardaten in Datenquellen

## Erste Schritte mit der Datenintegration {#get-started-with-data-integration}

Der erste Schritt zur Implementierung der Datenintegration besteht darin, Datenquellen zu identifizieren und zu konfigurieren, die Informationen speichern, die Sie in Anwendungsfällen für adaptive Formulare und interaktive Kommunikation nutzen möchten. Als Nächstes erstellen Sie ein Formulardatenmodell, das Datenmodellobjekte, Eigenschaften und Dienste aus einer oder mehreren Datenquellen verwendet. Sie können adaptive Formulare und interaktive Kommunikation basierend auf einem Formulardatenmodell erstellen, bei dem adaptive Formularfelder oder Platzhalter in interaktiver Kommunikation an die entsprechenden Datenquelleneigenschaften gebunden sind.

Mit AEM Forms können Sie auch ein Formulardatenmodell erstellen, das unabhängig von Datenquellen ist, und Datenmodellobjekte und Eigenschaften im Formulardatenmodell später mit der Datenquelle verknüpfen oder verknüpfen. Dadurch werden alle Abhängigkeiten von Datenquellen entfernt, während Sie an einem Formulardatenmodell arbeiten.

Lesen Sie folgende Informationen für die ersten Schritte mit der Datenintegration, um sie zu verstehen und zu implementieren.

* [Konfigurieren von Datenquellen](/help/forms/using/configure-data-sources.md)
* [Erstellen des Formulardatenmodells](/help/forms/using/create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell](/help/forms/using/work-with-form-data-model.md)
* [Verwenden eines Formulardatenmodells](/help/forms/using/using-form-data-model.md)
