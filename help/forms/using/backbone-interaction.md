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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 34%

---

# Interaktion mit Backbone {#backbone-interaction}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Backbone ist eine Bibliothek, die beim Erstellen und Befolgen der MVC-Architektur in Webanwendungen hilft. Die Grundidee von Backbone besteht darin, Ihre Oberfläche in logischen Ansichten zu organisieren, die von Modellen gestützt werden, von denen jedes unabhängig aktualisiert werden kann, wenn sich das Modell ändert, ohne dass die Seite neu gezeichnet werden muss. Weitere Informationen zu Backbone finden Sie unter [https://backbonejs.org](https://backbonejs.org/).

Einige Hauptkonzepte sind die folgenden:

**Backbone-Modell**: Enthält Daten und die meiste mit diesen Daten verknüpfte Logik.

**Backbone-Ansicht**: Wird verwendet, um den Status des jeweiligen Modells darzustellen. Eine Backbone-Ansicht verhält sich im Prinzip wie ein Controller, der Benutzeroberflächenereignisse wie Benutzerklicks oder Modellereignisse (wie Datenänderungen) erfasst und die Benutzeroberfläche entsprechend ändert.

**HTML-Vorlage**: Eine Wrapper-Vorlage mit Platzhaltern, die durch das Modell gefüllt werden.

**AEM Forms-Arbeitsbereich**: Enthält mehrere einzelne Komponenten. Jede Komponente:

* Stellt ein einzelnes logisches Benutzeroberflächenelement dar.
* Kann eine Sammlung ähnlicher Komponenten sein.
* Aus Backbone-Modell, Backbone-Ansicht und HTML-Vorlage.
* Enthält Verweis auf einen Dienst.
* Enthält Verweis auf erforderliche Dienstprogramme.

Wenn eine Komponente initialisiert wird, werden die folgenden Objekte erstellt:

* Eine neue Instanz des Backbone-Modells für die Komponente wird erstellt. Der Dienst wird in das Modell eingefügt.
* Eine neue Instanz der Backbone-Ansicht wird erstellt.
* Instanz des entsprechenden Modells, HTML-Vorlage und Dienstprogramme werden in die Ansicht eingefügt.

In der Backbone-Ansicht gibt es eine Ereigniszuordnung, die die verschiedenen Ereignisse zuordnet, die aufgrund von Benutzeroberflächeninteraktionen mit einem entsprechenden Handler auftreten können. Diese Zuordnung wird initialisiert, sobald eine Komponente initialisiert wurde.

Wenn eine Ansicht initialisiert wird, ruft die Ansicht das entsprechende Modell auf, um Daten vom Server abzurufen. Nachdem alle für eine Ansicht erforderlich Daten verfügbar sind, gibt die Ansicht die Daten in dem Format wieder, das in der HTML-Vorlage angegeben ist. Mehrere Ansichten können dasselbe Modell für die Kommunikation nutzen.

![](do-not-localize/aem_forms_workflow.png)

Beispiel:

1. Der Benutzer klickt auf eine Aufgabenvorlage in der Aufgabenliste.
1. Die Aufgabenansicht überwacht den Klick und ruft die Renderfunktion im Aufgabenmodell auf.
1. Das Task-Modell ruft daraufhin den Service auf, der ein gemeinsamer Punkt für die gesamte Kommunikation mit dem AEM Forms-Server ist.
1. Die Service-Klasse ruft den AEM Forms-REST-Endpunkt für die Render-Methode über Ajax auf.
1. Der Rückruf &quot;success&quot;für diesen Ajax-Aufruf wird im Aufgabenmodell definiert.
1. Das Aufgabenmodell löst ein Backbone-Ereignis als Benachrichtigung aus, dass der Renderaufruf abgeschlossen ist.
1. Eine andere Ansicht, die Aufgabendetailansicht, überwacht dieses Ereignis aus dem Aufgabenmodell.
1. Aufgabendetailansicht ändert dann die Aufgabendetailvorlage, um die gerenderte Aufgabe (Formular, Details, Anhänge, Notizen usw.) für den Benutzer anzuzeigen.
