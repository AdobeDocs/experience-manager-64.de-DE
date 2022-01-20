---
title: Test- und Tracking-Tools
seo-title: Testing and Tracking Tools
description: AEM bietet ein Framework für das Testen von Komponentenbenutzeroberflächen und einen Mechanismus zum Testen und Debuggen von Komponenten.
seo-description: AEM provides a framework for testing component UI and a mechanism for testing and debugging components
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
exl-id: 9387cdb4-f8de-4229-90d1-59218ac17561
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 93%

---

# Test- und Tracking-Tools{#testing-and-tracking-tools}

## Testen {#testing}

AEM bietet:

* [ein Framework für das Testen von Komponentenbenutzeroberflächen](/help/sites-developing/hobbes.md).
* [einen Mechanismus zum Testen und Debuggen von Komponenten](/help/sites-developing/developer-mode.md).

Im Folgenden werden zwei Open-Source-Test-Tools vorgestellt:

**Selenium**

Selenium wird für Funktionstests im Browser mit einem Benutzer pro Aktivität verwendet. Das Tool zeichnet Prüfungsschritte (Klicks) entweder als HTML-Tabellen oder Java-Klassen auf.

Weitere Informationen finden Sie unter [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

JMeter wird für das Tracking von Anfragen verwendet und kann für die Automatisierung von Funktions-, Leistungs- und Belastungstests verwendet werden.

Weitere Informationen finden Sie unter [http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/).

Außerdem sind viele proprietäre Tools für die Automatisierung von Tests und die Verwaltung von Testplänen verfügbar.

## Tracking {#tracking}

Die folgenden Tools stehen zur Verfügung. Eine wichtige Angelegenheit ist jedoch in allen Fällen die Verfügbarkeit der Daten für alle Mitglieder des Projektteams, also Partner und Kunde.

**Bugzilla**

Ein Bug-Tracking-System, das für Ihre eigenen Anforderungen konfiguriert werden kann.

**Tabellen**

Tabellen sind zwar nicht als Bugtracker gedacht, werden aber oft als solche missbraucht, da sie leicht verständlich sind und viele Benutzer Erfahrung mit ihrer Verwendung haben.

Wenn Tabellen als Bugtracker verwendet werden, dann:

* sollten sie einfach gehalten werden.
* sollte die Anzahl der einzelnen Tabellen möglichst gering gehalten werden.
* müssen sie regelmäßig aktualisiert werden.
* sollte nur eine Master-Kopie gepflegt werden, deren Speicherort allen bekannt ist.
* sollten sie allen Projektmitgliedern zugänglich sein.
* dürfen, falls Sicherheit ein Anliegen (oft in großen Unternehmen) und gemeinsamer Zugriff nicht möglich ist, Kopien verteilt werden, solange alle verstehen, dass es sich um Kopien handelt, die nicht aktualisiert werden können.

Auch für das Tracking von Bugs und Funktionsanforderungen sind proprietäre Tools vorhanden.
