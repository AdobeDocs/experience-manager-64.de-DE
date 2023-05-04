---
title: Verwalten von Workflows
seo-title: Administering Workflows
description: Erfahren Sie, wie Sie Workflows in AEM verwalten.
seo-description: Learn how to administer workflows in AEM.
uuid: d000a13c-97cb-4b1b-809e-6c3eb0d675e8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 4b09cd44-434e-4834-bc0d-c9c082a4ba5a
exl-id: e57b7a69-6e25-4066-ad7a-917969cebbe8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 29%

---

# Verwalten von Workflows{#administering-workflows}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Workflows ermöglichen die Automatisierung von Adobe Experience Manager (AEM)-Aktivitäten. Workflows:

* besteht aus einer Reihe von Schritten, die in einer bestimmten Reihenfolge ausgeführt werden.

   * Jeder Schritt führt eine bestimmte Aktivität aus. wie das Warten auf Benutzereingaben, das Aktivieren einer Seite oder das Senden einer E-Mail-Nachricht.

* Kann mit Assets im Repository, mit Benutzerkonten und mit AEM-Diensten interagieren.
* Können komplizierte Aktivitäten koordinieren, die jeden Aspekt von AEM umfassen.

Die von Ihrer Organisation eingerichteten Geschäftsprozesse können als Workflows dargestellt werden. Beispielsweise umfasst der Prozess der Veröffentlichung von Website-Inhalten in der Regel Schritte wie die Genehmigung und die Abnahme durch verschiedene Stakeholder. Diese Prozesse können als AEM Workflows implementiert und auf Inhaltsseiten und Assets angewendet werden.

* [Starten von Workflows](/help/sites-administering/workflows-starting.md)
* [Verwalten der Workflow-Instanzen](/help/sites-administering/workflows-administering.md)
* [Verwalten des Zugriffs auf Workflows](/help/sites-administering/workflows-managing.md)

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* Anwenden von und Teilnehmen an Workflows: [Arbeiten mit Workflows](/help/sites-authoring/workflows.md).
>* Das Erstellen von Workflow-Modellen und die Erweiterung der Workflow-Funktionalität: [Entwickeln und Erweitern von Workflows](/help/sites-developing/workflows.md).
>* Verbesserung der Leistung von Workflows, die umfangreiche Serverressourcen nutzen: [Gleichzeitige Workflow-Verarbeitung](/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing).
>


## Workflow-Modelle und -Instanzen {#workflow-models-and-instances}

[Workflow-Modelle](/help/sites-developing/workflows.md#model) in AEM sind die Darstellung und Implementierung von Geschäftsprozessen:

* Normalerweise werden sie auf Seiten oder Assets angewendet, um ein bestimmtes Ergebnis zu erzielen.
* Diese Seiten und/oder Assets werden als Workflow-Payload bezeichnet.
* Workflow-Modelle bestehen aus einer Reihe von Schritten zur Durchführung einer bestimmten Aufgabe.
* Die Payload wird bei der weiteren Ausführung des Workflows von Schritt zu Schritt übergeben.

Wenn ein Workflow-Modell gestartet (ausgeführt) wird, wird eine Workflow-Instanz erstellt. Ein Workflow-Modell kann mehrmals gestartet werden, wobei jedes Mal eine spezifische Workflow-Instanz generiert wird. Die vom Workflow-Modell definierten Schritte werden für jede Instanz ausgeführt.

>[!CAUTION]
>
>Die durchgeführten Schritte werden durch das Workflow-Modell definiert *zum Zeitpunkt der Instanzgenerierung*. Unter [Entwickeln von Workflows](/help/sites-developing/workflows.md#model) finden Sie weitere Details.

Workflow-Instanzen schreiten durch den folgenden Lebenszyklus voran:

1. Das Workflow-Modell wird gestartet und eine Workflow-Instanz wird erstellt und ausgeführt.

   1. Die Payload der Workflow-Instanz wird identifiziert, wenn das Modell gestartet wird.
   1. Die Instanz ist im Grunde eine Kopie des Modells (wie zum Zeitpunkt der Erstellung).
   1. AEM Autoren, Administratoren oder Dienste können Workflow-Modelle starten.

1. Der erste Schritt des Workflow-Modells wird ausgeführt.
1. Der Schritt ist abgeschlossen und die Workflow-Engine verwendet das Modell, um den nächsten auszuführenden Schritt zu bestimmen.
1. Die nachfolgenden Schritte im Workflow-Modell werden ausgeführt und abgeschlossen.
1. Wenn der letzte Schritt abgeschlossen ist, wird die Workflow-Instanz abgeschlossen und somit archiviert.

Viele nützliche Workflow-Modelle werden mit AEM bereitgestellt. Darüber hinaus können die Entwickler in Ihrem Unternehmen benutzerdefinierte Workflow-Modelle erstellen, die auf die spezifischen Anforderungen Ihrer Geschäftsprozesse zugeschnitten sind.

## Workflow-Schritte {#workflow-steps}

Wenn Workflow-Schritte ausgeführt werden, sind sie mit einer Workflow-Instanz verknüpft. Der Verlauf einer Workflow-Instanz enthält Informationen zu jedem Schritt, der für die Instanz ausgeführt wurde. Diese Informationen sind hilfreich, um Probleme zu untersuchen, die während der Ausführung auftreten.

Je nach Schritttyp führt ein Benutzer oder ein Dienst Workflow-Schritte aus:

* Wenn ein Benutzer einen Schritt ausführt, wird ihm ein Arbeitselement zugewiesen, das in seinem Posteingang platziert wird. Der Benutzer ist dafür verantwortlich, den Schritt manuell abzuschließen, damit die Workflow-Instanz fortgesetzt wird.
* Wenn ein Dienst einen Schritt ausführt, geht die Workflow-Instanz nach Abschluss automatisch zum nächsten Schritt über.

>[!NOTE]
>
>Wenn ein Fehler auftritt, sollte die Implementierung des Dienstes/Schritts das Verhalten für ein Fehlerszenario handhaben. Die Workflow-Engine selbst versucht den Auftrag erneut, protokolliert dann einen Fehler und stoppt die Instanz.

## Workflow-Status und -Aktionen {#workflow-status-and-actions}

Ein Workflow kann einen der folgenden Status aufweisen:

* **WIRD AUSGEFÜHRT**: Die Workflow-Instanz wird ausgeführt.
* **ABGESCHLOSSEN**: Die Workflow-Instanz wurde erfolgreich beendet.

* **AUSGESETZT**: Die Workflow-Instanz wurde ausgesetzt.
* **ABORTED**: Die Workflow-Instanz wurde beendet.
* **STÄNDIG**: Für die Weiterentwicklung der Workflow-Instanz muss ein Hintergrundauftrag ausgeführt werden, der Auftrag kann jedoch nicht im System gefunden werden. Diese Situation kann auftreten, wenn beim Ausführen des Workflows ein Fehler auftritt.

>[!NOTE]
>
>Wenn die Ausführung eines Prozessschritts zu einem Fehler führt, wird der Schritt im Posteingang der bzw. des Admins angezeigt und der Workflow-Status lautet **WIRD AUSGEFÜHRT**.

Je nach dem aktuellen Status können Sie Aktionen zur Ausführung von Workflow-Instanzen durchführen, wenn Sie beim normalen Fortschritt einer Workflow-Instanz eingreifen müssen:

* **Aussetzen**: Stoppt vorübergehend die Ausführung des Workflows. Das Aussetzen ist in Ausnahmefällen nützlich, wenn Sie nicht möchten, dass der Workflow fortgesetzt wird, z. B. zur Wartung. Durch Aussetzen wird der Workflow-Status auf Ausgesetzt geändert.
* **Fortsetzen**: Startet einen ausgesetzten Workflow an der Stelle der Ausführung neu, an der er unterbrochen wurde – und zwar mit derselben Konfiguration.
* **Beenden**: Beendet die Workflow-Ausführung und ändert den Status in **ABGEBROCHEN**. Eine abgebrochene Workflow-Instanz kann nicht neu gestartet werden.
