---
title: Versionshinweise zu Smart Content Service
seo-title: Versionshinweise zu Smart Content Service
description: Überblick über den Smart Content Service und bekannte Probleme rund um den Service.
seo-description: Überblick über den Smart Content Service und bekannte Probleme rund um den Service.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
exl-id: 6e7ac9d2-7181-48bb-82c4-61a90e594ff5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 17%

---

# Versionshinweise zu Smart Content Service {#smart-content-service-release-notes}

Überblick über den Smart Content Service und bekannte Probleme rund um den Service.

Unternehmen verlangen, dass ihre digitalen Assets basierend auf der Taxonomie getaggt werden, mit der Mitarbeiter, Partner und Kunden digitale Assets referenzieren und suchen. Im Vergleich zu generischen Tags werden Assets, die basierend auf der Unternehmenstaxonomie getaggt werden, durch Tag-basierte Suchen leichter identifiziert und abgerufen.

Der Smart Content Service verwendet Ihre Unternehmenstaxonomie von AEM Assets, um digitale Assets automatisch mit Tags zu versehen. Dadurch wird sichergestellt, dass die relevantesten Assets bei Suchvorgängen angezeigt werden.

Sie müssen den Smart Content Service mit einem kuratierten Satz von AEM Assets und Tags trainieren, um Ihre Unternehmenstaxonomie zu erkennen. Nach der Schulung kann der Dienst diese Tags auf einen ähnlichen Satz von Assets anwenden.

Der Smart Content Service basiert auf der Adobe Sensei-Plattform, mit der Sie den Bilderkennungsalgorithmus auf Ihre Unternehmenstaxonomie trainieren können. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf ähnliche Assets anzuwenden.

## Wichtige Verbesserungen {#key-improvements}

Der Smart Content Service umfasst die folgenden wichtigen Verbesserungen:

* Algorithmusoptimierungen zur weiteren Verbesserung der Modellgenauigkeit und zum Rückruf von Werten
* Unterstützung für das Zurücksetzen der Modellschulung für alle Tags auf Mandantenebene
* Unterstützung für optimierte Smart-Tags-Namespaces zur Vermeidung von Konflikten
* Neue Modell-Ersatzrichtlinie zur Vermeidung von Beeinträchtigungen durch Umschulung
* Mandantenweises Monitoring für die Dienstverwendung
* Fehlerbehebungen für Probleme im Zusammenhang mit Clustering und Verbindung, die die Stabilität des Dienstes verbessern

## Behobene Probleme {#fixed-issues}

Die folgenden Probleme wurden in dieser Version behoben:

* Arbeitsprozesse für Tagging- und Trainings-Workflows werden beendet, wenn keine Verbindung zum MySQL-Server hergestellt werden kann. CQ-4242886

* Präzisionsverzerrungen werden nicht richtig berechnet. CQ-4241797

* Falsche PR-Berechnung für Modell. CQ-4241381

* Beim Trainings-Workflow werden Beispiel-Assets bei der Verarbeitung aus der Warteschlange CQ-4240901 nicht berücksichtigt

* Verbesserte Genauigkeit beim Rückruf. CQ-4239895

* Modell-Ersatzrichtlinie. CQ-4239886

* Bilder für Herrenhemden sind mit dem Damenjacke-Tag versehen. CQ-4239650

* Schulungsbeispiele werden bei der Staging-Implementierung verpasst. CQ-4239483

* Die Validierung im Trainings-Auftrag sollte für eine Reihe von Assets erfolgen, die für die Schulung eingereicht werden. CQ-4238834

* Die Modellerstellung schlägt für die negative Nachbildung fehl, selbst wenn für ein Tag minimale positive/negative Werte vorhanden sind. CQ-4240741

* Irreführende Einträge für negative Futtermittel in Trainer-Logs. CQ-4240738

* Problem bei der Erstausbildung, wenn zur Schulung eingereichte Tags zufällige Negative voneinander sind. CQ-4240118

* Verbessern Sie die Protokolle zur Überwachung der Dienstnutzung pro Mandant. CQ-4239781

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
* [Verbesserte Dokumentation zu Smart-Tags](/help/assets/enhanced-smart-tags.md)

## Produktzugriff und Support (Websites mit Zugriffsbeschränkung) {#product-access-and-support-restricted-sites}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

* [Produktzugriff](https://login.marketing.adobe.com)
* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/).
* Produktaktualisierungen, Patches und Pakete für zusätzliche Funktionen auf [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Kundensupport über Admin Console](https://adminconsole.adobe.com/). Weitere Informationen finden Sie unter [Neues Kundenunterstützungs-Erlebnis für Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
