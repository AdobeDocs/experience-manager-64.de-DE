---
title: Welche Testumgebungen sind erforderlich?
seo-title: Which Test Environments are needed?
description: Bei Tests sollten mehrere Umgebungen berücksichtigt werden.
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: c3c7c007-4814-4bd1-987e-534df4575a4a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 67%

---

# Welche Testumgebungen sind erforderlich?{#which-test-environments-will-be-needed}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Beim Definieren der Konfigurationen für Tests sollten Sie Folgendes beachten:

**Entwicklung**: Für Komponententests und bestimmte Integrationstests.

**Test**: Für die Mehrzahl der Tests.

**Live**: Für abschließende Leistungs- und Belastungstests. Auch für Akzeptanztests mit dem Kunden.

Sie müssen auch entscheiden, welche Instanzen wo erforderlich sind (in der Regel mindestens eine für jede Teststufe):

**Author**: In dieser Instanz können Autoren Inhalte eingeben und veröffentlichen.

**Publish**: Diese Instanz stellt die Website in veröffentlichter Form dar, auf die Besucher zugreifen können.

Sollte in Verbindung mit dem Dispatcher getestet werden.

Schließlich muss die tatsächliche Hardware berücksichtigt werden - alle Leistungstests sollten auf einem System durchgeführt werden, das der Konfiguration der endgültigen Live-Umgebung so ähnlich wie möglich ist. Aus diesem Grund wird auch empfohlen, den Projekt-Launch in einen aufzuteilen:

**Soft Launch**: Reduzierte Verfügbarkeit, sodass Zeit für Leistungstests, Anpassungen und Optimierungen unter realistischen Bedingungen in der Produktionsumgebung bleibt.

**Hard Launch**: Vollständige Verfügbarkeit.
