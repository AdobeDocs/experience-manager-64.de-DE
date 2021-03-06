---
title: Content-Disposition-Filter
seo-title: Content Disposition Filter
description: Erfahren Sie, wie Sie mit dem Content Disposition Filter XSS-Angriffe verhindern können.
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
source-git-commit: 8cc85728be93d58e3aaee69c96f59ee98d5484a1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 34%

---

# Content-Disposition-Filter {#content-disposition-filter}

Der Content-Disposition-Filter ist eine Sicherheitsfunktion zum Schutz vor XSS-Angriffen auf SVG-Dateien.

Nach der Installation blockiert der Filter den Zugriff auf alle Assets. Sie konnten beispielsweise eine PDF nicht online anzeigen. In diesem Abschnitt wird beschrieben, wie Sie den Filter Ihren Anforderungen entsprechend konfigurieren.

## Konfigurieren des Content-Disposition-Filters {#configure-content-disposition-filter}

Sie können die [Apache Sling Content Disposition Filter in GitHub.](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

Die Optionen für den Content-Disposition-Filter bieten die folgenden Funktionen:

* **Content Disposition Paths:** eine Liste von Pfaden, auf die der Filter angewendet wird, gefolgt von einer Liste von MIME-Typen, die für diesen Pfad ausgeschlossen werden sollen. Dieser Pfad muss ein absoluter Pfad sein und kann einen Platzhalter (`*`), um jeden Ressourcenpfad mit dem angegebenen Pfadpräfix abzugleichen. Beispiel: `/content/*:image/jpeg,image/svg+xml` wendet den Filter auf jeden Knoten in `/content` außer JPG- und SVG-Bilder

* **Ausgeschlossene Ressourcenpfade:** eine Liste der ausgeschlossenen Ressourcen enthält, muss jeder Ressourcenpfad als absoluter und vollständig qualifizierter Pfad angegeben werden. Präfixabgleiche/Platzhalter werden nicht unterstützt.

* **Aktivieren Sie für alle Ressourcenpfade:** Dieses Flag steuert, ob dieser Filter für alle Pfade aktiviert werden soll, mit Ausnahme der durch Ausgeschlossene Ressourcenpfade definierten ausgeschlossenen Pfade. Ist diese Option auf „true“ festgelegt, werden die Content-Disposition-Pfade ignoriert. Unabhängig von der Konfiguration werden nur Ressourcenpfade behandelt, die eine Eigenschaft mit dem Namen `jcr:data` oder
   `jcr:content jcr:data`.
