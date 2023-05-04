---
title: Definieren von Testfällen
seo-title: Defining your Test Cases
description: Ihre Testfälle sollten auf den Anwendungsfällen und der detaillierten Anforderungsspezifikation basieren
seo-description: Your test cases should be based upon the use cases and the detailed requirements specification
uuid: 82dff825-da58-49a2-bf35-f5bb905e523d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 87a1f27a-765e-4882-9c06-5909e1610e1d
exl-id: ad529be3-9d31-492f-943f-ef3e99e13586
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 29%

---

# Definieren von Testfällen{#defining-your-test-cases}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Ihre Testfälle sollten auf Folgendem basieren:

**Anwendungsfälle**

* Diese definieren die erforderliche Funktionalität in Bezug auf die Interaktion zwischen Akteuren (Rollen, die bestimmte Aktionen auslösen) und dem System.
* Die Anwendungsfälle sollten vom Kunden definiert werden.

**Detaillierte Anforderungsspezifikation**

* Alle funktionalen und leistungsbezogenen Anforderungen sollten getestet werden.

Die Tests sollten klar definieren:

* Voraussetzungen; Diese können bestimmte Systeme, Konfigurationen oder Tester-Erlebnisse abdecken.
* Schritte, die zu befolgen sind; auf einer geeigneten Detailebene.
* Erwartete Ergebnisse.
* Klare Kriterien für Bestehen oder Fehlschlagen.

Die Möglichkeit der Automatisierung von Testfällen ist offensichtlich attraktiv, da sie sich wiederholende Aufgaben eliminieren kann.

## Vergleich von manuellen und automatisierten Tests {#manual-versus-automated-tests}

Die Automatisierung von Testfällen ist jedoch eine wichtige Investition, daher sollten bestimmte Aspekte berücksichtigt werden:

* Sie benötigen Zeit, Mühe und Erfahrung zum Einrichten und Konfigurieren.
* Wenn Browser-basiert sind, besteht ein erhöhtes Risiko von Problemen bei der Installation von Browseraktualisierungen. weitere Korrekturzeit erforderlich machen.
* Nur wirklich machbar für große Projekte.
* Gut, wenn mehrere Versionen entweder zum Testen oder im langfristigen Release-Plan generiert werden.

## Testen von spezifischen Aspekten {#testing-specific-aspects}

Beim Testen von AEM sind einige spezifische Details von besonderem Interesse:

Autor- und Veröffentlichungsumgebung

Auch wenn dies unter [Umgebungen](/help/sites-developing/the-basics.md#environments) erläutert wird, lohnt es sich, einen entscheidenden Faktor von AEM in Bezug auf Tests noch einmal hervorzuheben.

Sie müssen AEM als zwei Anwendungen betrachten:

* die **Autorenumgebung**
Diese Instanz ermöglicht es Autoren, Inhalte einzugeben und zu veröffentlichen.
Dies umfasst einen kleinen (er), vorhersehbaren Satz von Benutzern, für die spezifische Funktionalität und Leistung von entscheidender Bedeutung sind.
* die **Veröffentlichen** Umgebung Diese Instanz präsentiert die Website in ihrer veröffentlichten Form für den Zugriff durch Besucher.
Dies umfasst normalerweise eine größere Gruppe von Benutzern, bei denen das Traffic-Volumen nicht immer zu 100 % vorhersehbar ist. Leistung ist immer noch entscheidend - wenn auf Anfragen reagiert wird. Zwischenspeicherung und Lastenausgleich müssen ebenfalls berücksichtigt werden.

Obwohl dieselbe Software als solche:

* unterschiedliche Zwecke nutzen
* hinsichtlich Funktionalität und Leistung unterschiedliche Anforderungen haben
* unterschiedlich konfiguriert sind
* separat eingestellt werden
* verfügt jeweils über einen eigenen Satz von Abnahmeprüfungen

Mit anderen Worten, sie müssen getrennt und mit verschiedenen Testfällen getestet werden.

**Personalisierung**

Beim Testen der Personalisierung sollte jeder einzelne Anwendungsfall mit mehreren Benutzerkonten wiederholt werden, um das Verhalten zu überprüfen.

Die Zwischenspeicherung muss auch auf korrektes Verhalten überprüft werden.

**Der Dispatcher**

Bei den meisten Projekten wird der Dispatcher für die Zwischenspeicherung und den Lastenausgleich installiert.

Das Testen ist schwierig (Zwischenspeicherung erfolgt auf verschiedenen Ebenen und an verschiedenen Orten) und muss auf Blackbox-Basis durchgeführt werden. Die wichtigsten Aspekte, auf die getestet werden muss:

* **Genauigkeit**; stellen sicher, dass der Besucher der Website Inhaltsaktualisierungen sieht.
* **Kontinuität**; Stellen Sie sicher, dass die Website weiterhin verfügbar ist, wenn ein Server heruntergefahren wird.
* **Cluster**
Cluster werden verwendet, um Folgendes bereitzustellen:
   * **Failover**
Wenn ein Server ausfällt, übernehmen andere Server im Cluster die Verarbeitung.
   * **Leistung**
Lastenausgleich mit vollständigem Failover erhöht die Leistung eines Clusters.

Wenn dies für ein Kundenprojekt verwendet wird, muss der Cluster getestet werden, um den korrekten Ablauf der Konfiguration zu bestätigen.

## Testen von Software von Drittanbietern {#testing-third-party-software}

Jede Software von Drittanbietern, die mit AEM verbunden ist, wird in den detaillierten Anforderungsspezifikationen aufgeführt.

Sämtliche erforderlichen Tests (abhängig vom definierten Umfang) müssen analysiert werden und als sauber getestet werden.
