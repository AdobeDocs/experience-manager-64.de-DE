---
title: Versionshinweise zum Smart Content Service
seo-title: Versionshinweise zum Smart Content Service
description: Überblick über den Smart Content Service und bekannte Probleme im Zusammenhang mit dem Dienst.
seo-description: Überblick über den Smart Content Service und bekannte Probleme im Zusammenhang mit dem Dienst.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 17%

---


# Versionshinweise zum Smart Content Service {#smart-content-service-release-notes}

Überblick über den Smart Content Service und bekannte Probleme im Zusammenhang mit dem Dienst.

Unternehmen verlangen, dass ihre digitalen Assets entsprechend der Taxonomie getaggt werden, mit der Mitarbeiter, Partner und Kunden auf digitale Assets verweisen und diese suchen. Im Vergleich zu generischen Tags lassen sich Elemente, die auf der Grundlage der Geschäftstaxonomie getaggt werden, leichter identifizieren und durch tagbasierte Suchen abrufen.

Der Smart Content Service nutzt Ihre geschäftliche Taxonomie von AEM Assets, um digitale Assets automatisch zu taggen, wodurch sichergestellt wird, dass die relevantesten Assets in Suchvorgängen angezeigt werden.

Sie müssen den Smart Content Service mit einem kuratierten Satz von AEM Assets und Tags ausbilden, um Ihre Geschäftstaxonomie zu erkennen. Nach der Schulung kann der Dienst diese Tags auf ähnliche Assets anwenden.

Der Smart Content Service basiert auf der Adobe Sensei-Plattform, mit der Sie den Bilderkennungsalgorithmus nach Ihrer Geschäftstaxonomie ausbilden können. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf ähnliche Assets anzuwenden.

## Wichtige Verbesserungen {#key-improvements}

Der Dienst für intelligente Inhalte umfasst die folgenden wichtigen Verbesserungen:

* Algorithmusoptimierungen zur weiteren Verbesserung der Modellgenauigkeit, zum Rückruf von Werten
* Unterstützung für das Zurücksetzen der Modellschulung für alle Tags auf Pächter-Ebene
* Unterstützung erweiterter Namensraum für intelligente Tags zur Konfliktvermeidung
* Neue Modellaustauschpolitik zur Vermeidung von Beeinträchtigungen durch Umschulungen
* Mandantenbasierte Überwachung zur Nutzung des Dienstes
* Fehlerbehebungen bei Clustering und Verbindung, die die Stabilität des Dienstes verbessern

## Behobene Probleme {#fixed-issues}

Die folgenden Probleme wurden in dieser Version behoben:

* Arbeitsprozesse für Tagging und Schulung Workflows beendet, wenn keine Verbindung zum MySQL-Server hergestellt werden kann. CQ-4242886

* Der Präzisionswert wird nicht richtig berechnet. CQ-4241797

* Falsche PR-Berechnung für Modell. CQ-4241381

* Im Schulungsarbeitsablauf fehlen Beispiel-Assets bei der Verarbeitung aus der Warteschlange CQ-4240901

* Verbesserte Genauigkeit beim Rückruf. CQ-4239895

* Modellaustauschrichtlinie. CQ-4239886

* Bilder für Herrenhemden sind mit dem Damenjacke-Tag versehen. CQ-4239650

* Schulungsbeispiele werden bei der Bereitstellung der Stufe verpasst. CQ-4239483

* Die Validierung des Ausbildungsauftrags sollte für eine Reihe von Assets erfolgen, die zur Fortbildung eingereicht werden. CQ-4238834

* Die Modellerstellung schlägt bei negativer Nachbildung fehl, selbst wenn für ein Tag minimale positive/negative Werte vorhanden sind. CQ-4240741

* Irreführende Einträge für negative Futtersuche in Trainerprotokollen. CQ-4240738

* Problem bei der Erstausbildung, wenn Tags, die zur Schulung eingereicht werden, zufällige Negative voneinander sind. CQ-4240118

* Verbessern Sie die Protokolle, um die Nutzung der Dienste pro Mandant zu überwachen. CQ-4239781

## Sprachen {#languages}

Der Smart Content Service ist für folgende Gebietsschemata verfügbar:

* Englisch
* Deutsch
* Französisch
* Spanisch
* Italienisch
* Portugiesisch
* Japanisch
* Vereinfachtes Chinesisch
* Koreanisch

## Links {#links}

* [Adobe Experience Manager-Produktseite unter adobe.com](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [Verbesserte Dokumentation zu intelligenten Tags](/help/assets/enhanced-smart-tags.md)

## Produktzugriff und Support (Websites mit Zugriffsbeschränkung) {#product-access-and-support-restricted-sites}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

* [Produktzugriff](https://login.marketing.adobe.com)
* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/).
* Produktupdates, Patches und Pakete für zusätzliche Funktionen bei der [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Kundenservice per Admin Console](https://adminconsole.adobe.com/). Weitere Informationen finden Sie unter [Neue Adobe - Kundendiensterfahrung](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
