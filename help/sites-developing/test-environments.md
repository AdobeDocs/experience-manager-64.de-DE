---
title: Welche Testumgebungen sind erforderlich?
seo-title: Which Test Environments are needed?
description: Mehrere Umgebungen sollten als Teil von Tests betrachtet werden
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: c3c7c007-4814-4bd1-987e-534df4575a4a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 47%

---

# Welche Testumgebungen sind erforderlich?{#which-test-environments-will-be-needed}

Um zu bestimmen, welche Konfigurationen getestet werden sollen, sollten Sie Folgendes beachten:

**Entwicklung** - für Einheiten und bestimmte Integrationstests.

**Test** - Für die Mehrzahl der Tests.

**Live** - für Leistungs- und Belastungstests. Auch für Akzeptanztests mit dem Kunden.

Sie müssen auch entscheiden, welche Instanzen wo erforderlich sind (in der Regel mindestens eine für jede Teststufe):

**Autor** - Diese Instanz ermöglicht es Autoren, Inhalte einzugeben und zu veröffentlichen.

**Veröffentlichen** - Diese Instanz präsentiert die Website in ihrer veröffentlichten Form für den Zugriff durch Besucher.

Sollte in Verbindung mit dem Dispatcher getestet werden.

Als Letztes müssen Sie die verwendete Hardware berücksichtigen. Leistungstests sollten auf einem System ausgeführt werden, das möglichst ähnlich wie die endgültige Live-Umgebung konfiguriert ist. Daher wird empfohlen, den Projektstart wie folgt zu unterteilen:

**Soft Launch** - reduzierte Verfügbarkeit; die Zeit für Leistungstests, Optimierung und Optimierung unter realistischen Bedingungen in der Produktionsumgebung lässt.

**Hard Launch** - Vollständige Verfügbarkeit.
