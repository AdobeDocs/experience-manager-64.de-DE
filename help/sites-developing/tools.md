---
title: Test- und Tracking-Tools
seo-title: Testing and Tracking Tools
description: AEM bietet ein Framework zum Testen der Komponentenbenutzeroberfläche und einen Mechanismus zum Testen und Debuggen von Komponenten
seo-description: AEM provides a framework for testing component UI and a mechanism for testing and debugging components
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
exl-id: 9387cdb4-f8de-4229-90d1-59218ac17561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 22%

---

# Test- und Tracking-Tools{#testing-and-tracking-tools}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Testen {#testing}

AEM bietet:

* [ein Framework für das Testen von Komponentenbenutzeroberflächen](/help/sites-developing/hobbes.md).
* [einen Mechanismus zum Testen und Debuggen von Komponenten](/help/sites-developing/developer-mode.md).

Im Folgenden finden Sie zwei Open Source-Testtools:

**Selenium**

Selenium wird für Funktionstests in einem Browser mit einem Benutzer pro Aktivität verwendet. Testschritte (Klicks) werden entweder als HTML-Tabellen oder als Java-Klassen aufgezeichnet.

Weitere Informationen finden Sie unter [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

JMeter wird zur Nachverfolgung von Anforderungen verwendet und kann für Funktions-, Leistungs- und Stresstests verwendet werden.

Weitere Informationen finden Sie unter [http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/).

Es gibt auch viele proprietäre Tools für die Automatisierung von Tests und die Verwaltung von Testplänen.

## Tracking {#tracking}

Die folgenden Tools sind einfach verfügbar. Ein zentrales Problem ist jedoch in allen Fällen die Verfügbarkeit der Daten für alle Mitglieder des Projektteams - Partner und Kunde.

**Bugzilla**

Ein Bug-Tracking-System, das für Ihre eigenen Anforderungen konfiguriert werden kann.

**Tabellen**

Tabellen sind zwar nicht als Bugtracker gedacht, werden aber oft als solche miss braucht, da sie leicht verständlich sind und viele Benutzer Erfahrung mit ihrer Verwendung haben.

Wenn diese zum Tracking verwendet werden, dann:

* sie sollten einfach gehalten werden.
* die Anzahl der einzelnen Tabellen sollte auf ein Minimum beschränkt werden.
* sie müssen regelmäßig aktualisiert werden.
* Es sollte nur eine Übergeordnete Kopie aufbewahrt werden und jeder sollte wissen, wo die Übergeordnete Kopie ist.
* sie sollten für alle Projektmitglieder zugänglich sein.
* Wenn die Sicherheit ein Problem ist (häufig bei großen Unternehmen auftritt) und ein gemeinsamer Zugriff nicht möglich ist, können Kopien verteilt werden, sofern alle verstehen, dass es sich um Kopien handelt, die nicht aktualisiert werden können.

Auch für das Tracking von Bugs und Funktionsanforderungen sind proprietäre Tools vorhanden.
