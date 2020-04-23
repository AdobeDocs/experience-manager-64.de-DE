---
title: Funktionsweise von Process Berichte
seo-title: Funktionsweise von Process Berichte
description: Beschreibung der Dienste, aus denen der AEM Forms on JEE Process Berichte besteht, und eine Einführung in die Benutzeroberfläche von Process Berichte
seo-description: Beschreibung der Dienste, aus denen der AEM Forms on JEE Process Berichte besteht, und eine Einführung in die Benutzeroberfläche von Process Berichte
uuid: 00a2dd6d-8a6f-4c7b-b03e-81cfd4bcf50d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: process-reporting
discoiquuid: 4afc68fc-6b39-4c31-95fa-2ef3111c57da
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f

---


# Funktionsweise von Process Berichte {#how-process-reporting-works}

Process Berichte ist das Berichte-Modul von AEM Forms on JEE.

Mit Process Berichte können Sie Berichte zu AEM Forms-Prozessen und -Aufgaben ausführen.

Process Berichte verwendet das eingebettete Process Berichte-Repository, um Formulardaten zu veröffentlichen. Diese Daten werden dann zum Ausführen von Berichten verwendet.

Process Berichte umfasst die folgenden Module:

* [ProcessDataPublisher-Dienst](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatapublisher-service-br-p)
* [ProcessDataStorage-Dienst](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatastorageprovider-service-br-p)
* [OSGi-Dienst](/help/forms/using/process-reporting/process-reporting-architecture.md#p-osgi-service-br-p)
* [Abfrage Data Servlet](/help/forms/using/process-reporting/process-reporting-architecture.md#p-querydataservlet-service-br-p)
* [Benutzeroberfläche von Process Berichte](/help/forms/using/process-reporting/process-reporting-architecture.md#p-process-reporting-user-interface-br-p)

## Process Berichte-Architektur {#process-reporting-architecture-br}

![processreportingarchitecture](assets/processreportingarchitecture.png)

## Process Berichte-Module {#process-reporting-modules}

### ProcessDataPublisher-Dienst {#processdatapublisher-service-br}

Der ProcessDataPublisher-Server wird regelmäßig in der AEM Forms-Datenbank ausgeführt und extrahiert die Daten, die sich seit der letzten Ausführung des Dienstes geändert haben. Anschließend werden die Daten im Process Data Datenspeicherung-Dienst veröffentlicht.

Weitere Informationen zum Konfigurieren des Dienstes finden Sie unter ProcessDataPublisher-Dienst [konfigurieren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-reportconfiguration-service-p).

### ProcessDataStorageProvider-Dienst {#processdatastorageprovider-service-br}

Der ProcessDataStorageProvider-Dienst empfängt Prozessdaten vom ProcessDataPublisher-Dienst und speichert die Daten im Process Berichte-Repository.

Weitere Informationen zum Konfigurieren des Dienstes finden Sie unter ProcessDataStorageProvider-Dienst [konfigurieren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-to-configure-the-process-reporting-repository-locations-p).

### OSGi-Dienst {#osgi-service-br}

Das QueryDataServlet verwendet diesen Dienst, um die Berichte-Daten aus dem Process Berichte-Repository abzurufen.

### QueryDataServlet-Dienst {#querydataservlet-service-br}

Der QueryDataServlet-Dienst akzeptiert Abfragen aus der Process Berichte-Benutzeroberfläche.

Der Dienst nutzt dann OSGi-Dienste, um die relevanten Daten des Berichte abzurufen, die Daten zu verarbeiten und die Daten an die Benutzeroberfläche zurückzugeben.

### Benutzeroberfläche von Process Berichte {#process-reporting-user-interface-br}

Die Benutzeroberfläche von Process Berichte ist eine webbrowser-basierte Benutzeroberfläche. Sie verwenden diese Schnittstelle zur Ansicht von Informationen zur Verarbeitung und Aufgabe, die aus der AEM Forms-Datenbank veröffentlicht werden.

### QueryDataServlet-Dienst {#querydataservlet-service-br-1}

Der QueryDataServlet-Dienst akzeptiert Abfragen aus der Process Berichte-Benutzeroberfläche.

Der Dienst nutzt dann OSGi-Dienste, um die relevanten Daten des Berichte abzurufen, die Daten zu verarbeiten und die Daten an die Benutzeroberfläche zurückzugeben.

### Benutzerspezifische Berichte {#custom-reports-br}

Sie können eigene benutzerspezifische Berichte erstellen und diese Berichte auf der Registerkarte &quot;Benutzerspezifische Berichte&quot;der Benutzeroberfläche von Process Berichte anzeigen.

Anweisungen zum Erstellen eines benutzerspezifischen Berichts finden Sie unter So erstellen Sie einen benutzerspezifischen Bericht im Artikel [Benutzerspezifische Berichte in Process Berichte](/help/forms/using/process-reporting/process-reporting-custom-reports.md).

