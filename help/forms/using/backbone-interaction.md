---
title: Interaktion mit Backbone
seo-title: Backbone interaction
description: Grundlegende Informationen zur Verwendung von Backbone JavaScript-Modellen in AEM Forms Workspace.
seo-description: Conceptual information about use of Backbone JavaScript models in AEM Forms workspace.
uuid: c70da848-e514-42bc-a59b-44a7c00aa529
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: d363eec3-172b-413e-9743-ed51804ea1e9
exl-id: f726cb73-732c-4893-bdb5-10ddcf4a340a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 100%

---

# Interaktion mit Backbone {#backbone-interaction}

Backbone ist eine Bibliothek, die das Erstellen und Verfolgen von MVC-Architektur in Webanwendungen unterstützt. Die Grundidee von Backbone ist, Ihre Benutzeroberfläche in logischen Ansichten zu organisieren, unterstützt von Modellen, die bei Modelländerungen jeweils einzeln aktualisiert werden können, ohne dass die Seite neu gezeichnet werden muss. Weitere Informationen zu Backbone finden Sie unter [https://backbonejs.org](https://backbonejs.org/).

Einige Hauptkonzepte sind die folgenden:

**Backbone-Modell**: Enthält Daten und die meiste mit diesen Daten verknüpfte Logik.

**Backbone-Ansicht**: Wird verwendet, um den Status des jeweiligen Modells darzustellen. Eine Backbone-Ansicht verhält sich im Prinzip wie ein Controller, der Benutzeroberflächenereignisse wie Benutzerklicks oder Modellereignisse (wie Datenänderungen) erfasst und die Benutzeroberfläche entsprechend ändert.

**HTML-Vorlage**: Eine Wrapper-Vorlage mit Platzhaltern, die durch das Modell gefüllt werden.

**AEM Forms-Arbeitsbereich**: Enthält mehrere einzelne Komponenten. Jede Komponente:

* Stellt ein einzelnes logischen Element der Benutzeroberfläche dar.
* Kann eine Sammlung ähnlicher Komponenten sein.
* Erstellt aus Backbone-Modell, Backbone-Ansicht und HTML-Vorlage.
* Enthält Verweis zu einem Dienst.
* Enthält Verweis zu erforderlichen Dienstprogrammen.

Wenn eine Komponente initialisiert wurde, werden folgende Objekte erstellt:

* Eine neue Instanz des Backbone-Modells für die Komponente wird erstellt. Dienst wird ins Modell injiziert.
* Eine neue Instanz der Backbone-Ansicht wird erstellt.
* Instanz des entsprechenden Modells, HTML-Vorlage und Dienstprogramme werden in die Ansicht injiziert.

In der Backbone-Ansicht gibt es eine Ereigniszuordnung für die verschiedenen Ereignisse, die durch Benutzeroberflächeninteraktionen mit einem entsprechenden Handler auftreten können. Diese Zuordnung wird ausgelöst, wenn eine Komponente initialisiert wird.

Wenn eine Ansicht initialisiert wird, ruft die Ansicht das entsprechende Modell zum Datenabruf vom Server auf. Nachdem alle für eine Ansicht erforderlich Daten verfügbar sind, gibt die Ansicht die Daten in dem Format wieder, das in der HTML-Vorlage angegeben ist. Mehrere Ansichten können dasselbe Modell für die Kommunikation nutzen.

![](do-not-localize/aem_forms_workflow.png)

Ein Beispiel:

1. Benutzer klickt in der Aufgabenliste auf eine Aufgabenvorlage.
1. Aufgabenansicht erfasst den Klick und ruft Renderfunktion im Aufgabenmodell auf.
1. Das Task-Modell ruft daraufhin den Service auf, der ein gemeinsamer Punkt für die gesamte Kommunikation mit dem AEM Forms-Server ist.
1. Die Service-Klasse ruft den AEM Forms-REST-Endpunkt für die Render-Methode über Ajax auf.
1. Der Erfolgsrückruf für diesen Ajax-Aufruf wird im Aufgabenmodell definiert.
1. Aufgabenmodell erstellt ein Backbone-Ereignis als Benachrichtigung, dass der Renderaufruf abgeschlossen ist.
1. Eine andere Ansicht, die Aufgabendetailansicht, überwacht dieses Ereignis des Aufgabenmodells.
1. Aufgabendetailansicht ändert dann die Aufgabendetailvorlage, um die gerenderte Aufgabe (Formular, Details, Anlagen, Hinweise usw.) für den Benutzer anzuzeigen.
