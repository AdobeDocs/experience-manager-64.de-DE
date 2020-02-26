---
title: Funktionsweise der Prozessberichterstellung
seo-title: Funktionsweise der Prozessberichterstellung
description: Beschreibung der Dienste, aus denen die AEM Forms on JEE Process Reporting-Berichterstellung und eine Einführung in die Benutzeroberfläche der Prozessberichterstellung gehören
seo-description: Beschreibung der Dienste, aus denen die AEM Forms on JEE Process Reporting-Berichterstellung und eine Einführung in die Benutzeroberfläche der Prozessberichterstellung gehören
uuid: 00a2dd6d-8a6f-4c7b-b03e-81cfd4bcf50d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: process-reporting
discoiquuid: 4afc68fc-6b39-4c31-95fa-2ef3111c57da
translation-type: tm+mt
source-git-commit: 9ce0d4c714d8ff55c64a884d90462bcd75629ae0

---


# Funktionsweise der Prozessberichterstellung {#how-process-reporting-works}

Prozessberichterstellung ist das Berichtsmodul von AEM Forms on JEE.

Mit der Prozessberichterstellung können Sie Berichte zu AEM Forms-Prozessen und -Aufgaben ausführen.

Die Prozessberichterstellung verwendet das eingebettete Process Reporting-Repository, um Formulardaten zu veröffentlichen. Diese Daten werden dann zum Ausführen von Berichten verwendet.

Process Reporting besteht aus den folgenden Modulen:

* [ProcessDataPublisher-Dienst](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatapublisher-service-br-p)
* [ProcessDataStorage-Dienst](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatastorageprovider-service-br-p)
* [OSGi-Dienst](/help/forms/using/process-reporting/process-reporting-architecture.md#p-osgi-service-br-p)
* [Abfragedaten-Servlet](/help/forms/using/process-reporting/process-reporting-architecture.md#p-querydataservlet-service-br-p)
* [Benutzeroberfläche &quot;Process Reporting&quot;](/help/forms/using/process-reporting/process-reporting-architecture.md#p-process-reporting-user-interface-br-p)

## Process Reporting-Architektur {#process-reporting-architecture-br}

![processreportingarchitecture](assets/processreportingarchitecture.png)

## Prozessberichtsmodule {#process-reporting-modules}

### ProcessDataPublisher-Dienst {#processdatapublisher-service-br}

Der ProcessDataPublisher-Server wird regelmäßig in der AEM Forms-Datenbank ausgeführt und extrahiert die Daten, die sich seit der letzten Ausführung des Dienstes geändert haben. Anschließend werden die Daten im Process Data Storage-Dienst veröffentlicht.

Weitere Informationen zum Konfigurieren des Dienstes finden Sie unter ProcessDataPublisher-Dienst [konfigurieren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-reportconfiguration-service-p).

### ProcessDataStorageProvider-Dienst {#processdatastorageprovider-service-br}

Der ProcessDataStorageProvider-Dienst empfängt Prozessdaten vom ProcessDataPublisher-Dienst und speichert die Daten im Process Reporting-Repository.

Weitere Informationen zum Konfigurieren des Dienstes finden Sie unter ProcessDataStorageProvider-Dienst [konfigurieren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-to-configure-the-process-reporting-repository-locations-p).

### OSGi-Dienst {#osgi-service-br}

Das QueryDataServlet verwendet diesen Dienst, um die Berichtsdaten aus dem Process Reporting-Repository abzurufen.

### QueryDataServlet-Dienst {#querydataservlet-service-br}

Der QueryDataServlet-Dienst akzeptiert Abfragen aus der Benutzeroberfläche &quot;Process Reporting&quot;.

Der Dienst verwendet dann OSGi-Dienste, um die relevanten Berichtsdaten abzurufen, die Daten zu verarbeiten und die Daten an die Benutzeroberfläche zurückzugeben.

### Benutzeroberfläche &quot;Process Reporting&quot; {#process-reporting-user-interface-br}

Die Benutzeroberfläche der Prozessberichterstellung ist eine webbrowser-basierte Oberfläche. Auf dieser Oberfläche können Sie Prozess- und Aufgabeninformationen anzeigen, die aus der AEM Forms-Datenbank veröffentlicht werden.

### QueryDataServlet-Dienst {#querydataservlet-service-br-1}

Der QueryDataServlet-Dienst akzeptiert Abfragen aus der Benutzeroberfläche &quot;Process Reporting&quot;.

Der Dienst verwendet dann OSGi-Dienste, um die relevanten Berichtsdaten abzurufen, die Daten zu verarbeiten und die Daten an die Benutzeroberfläche zurückzugeben.

### Benutzerspezifische Berichte {#custom-reports-br}

Sie können eigene benutzerspezifische Berichte erstellen und diese Berichte auf der Registerkarte &quot;Benutzerspezifische Berichte&quot;der Benutzeroberfläche &quot;Prozessberichterstellung&quot;anzeigen.

Die Schritte zum Erstellen eines benutzerspezifischen Berichts finden Sie unter So erstellen Sie einen benutzerspezifischen Bericht im Artikel [Benutzerspezifische Berichte in der Prozessberichterstellung](/help/forms/using/process-reporting/process-reporting-custom-reports.md).

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
