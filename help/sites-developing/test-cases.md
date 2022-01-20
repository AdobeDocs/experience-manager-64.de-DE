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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 76%

---

# Definieren von Testfällen{#defining-your-test-cases}

Ihre Testfälle sollten auf Folgendem basieren:

**Anwendungsfälle**

* Diese definieren die erforderliche Funktionalität in Bezug auf die Interaktion zwischen Akteuren (Rollen, die bestimmte Aktionen auslösen) und dem System.
* Die Nutzungsszenarios sollten vom Kunden definiert werden.

**Detaillierte Anforderungsspezifikation**

* Alle Funktions- und Leistungsanforderungen sollten getestet werden.

Die Tests sollten eindeutig definieren:

* Voraussetzungen; diese umfassen möglicherweise bestimmte Systeme, Konfigurationen oder Testerfahrung.
* Schritte die zu befolgen sind; in angemessenen Details.
* Erwartete Ergebnisse.
* Klare Kriterien für Bestehen/Nichtbestehen.

Die Aussicht, Testfälle zu automatisieren, ist offensichtlich attraktiv, da dadurch repetititve Aufgaben eliminiert werden können.

## Manuelle und automatisierte Tests {#manual-versus-automated-tests}

Die Automatisierung von Testfällen ist jedoch eine erhebliche Investition, daher sollten bestimmte Aspekte berücksichtigt werden:

* Benötigen Zeit, Mühe und Erfahrung beim Einrichten und Konfigurieren.
* Wenn sie browserbasiert sind, besteht ein erhöhtes Risiko für Probleme, wenn Browser-Updates installiert werden; es bedarf weiterer Korrekturzeit.
* Nur tatsächlich praktikabel für große Projekte.
* Gut, wenn mehrere Versionen entweder zum Testen oder im langfristigen Freigabeplan generiert werden.

## Spezifische Aspekte testen {#testing-specific-aspects}

Beim Testen AEM einige spezifische Details von besonderem Interesse sind:

Autor- und Veröffentlichungsumgebung

Obwohl unter [Umgebungen](/help/sites-developing/the-basics.md#environments) Es ist angebracht, einen entscheidenden AEM in Bezug auf die Tests hervorzuheben.

Sie müssen AEM als zwei Anwendungen betrachten:

* die **Autor** Umgebung Diese Instanz ermöglicht es Autoren, Inhalte einzugeben und zu veröffentlichen.
Sie hat einen klein(er)en, vorhersehbaren Benutzerkreis, für den spezielle Funktionen und Leistung äußerst wichtig sind.
* die **Veröffentlichungsumgebung**
Diese Instanz stellt die Website in veröffentlichter Form dar, auf die Besucher zugreifen können.
Daraus ergibt sich meist ein größerer Benutzerkreis und das Traffic-Volumen ist nicht immer zu 100 % vorhersehbar. Leistung ist immer noch entscheidend - wenn auf Anfragen reagiert wird. Caching und Lastenausgleich müssen ebenfalls berücksichtigt werden.

Zwar handelt es sich um dieselbe Software, doch die Umgebungen:

* dienen verschiedenen Zwecken
* haben unterschiedliche Anforderungen hinsichtlich Funktionalität und Leistung
* sind unterschiedlich konfiguriert
* werden separat eingestellt
* haben jeweils einen eigenen Satz von Funktionstests

Mit anderen Worten, sie müssen separat und mit verschiedenen Testfällen getestet werden.

**Personalisierung**

Beim Testen der Personalisierung sollte jeder einzelne Anwendungsfall mit mehreren Benutzerkonten wiederholt werden, um das Verhalten nachzuweisen.

Caching muss auch auf korrektes Verhalten geprüft werden.

**Der Dispatcher**

Bei den meisten Projekte installieren Sie den Dispatcher für Caching und Lastenausgleich.

Das Testen ist schwierig (Caching tritt auf unterschiedlichen Ebenen und in verschiedenen Orten auf) und muss auf Blackboxbasis vorgenommen werden. Die zu prüfenden Hauptaspekte sind:

* **Genauigkeit**; stellen sicher, dass der Besucher der Website Inhaltsaktualisierungen sieht.
* **Kontinuität**; Stellen Sie sicher, dass die Website weiterhin verfügbar ist, wenn ein Server heruntergefahren wird.
* **Cluster** Cluster werden verwendet, um Folgendes bereitzustellen:
   * **Failover**
Wenn ein Server fehlschlägt, übernehmen andere Server im Cluster die Verarbeitung.
   * **Leistung**
Lastenausgleich mit vollständigem Failover erhöht die Leistung eines Clusters.

Wenn dies für ein Kundenprojekt verwendet wird, muss der Cluster getestet werden, um den korrekten Ablauf der Konfiguration zu bestätigen.

## Testen von Software von Drittanbietern {#testing-third-party-software}

Jede Software von Drittanbietern, die mit AEM verbunden ist, wird in den detaillierten Anforderungsspezifikationen referenziert.

Sämtliche erforderlichen Tests (abhängig vom definierten Umfang) müssen analysiert werden und als sauber getestet werden.
