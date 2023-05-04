---
title: Konzept der Inhaltserstellung
seo-title: Concept of Authoring
description: Konzepte der Bearbeitung (Authoring) in AEM
seo-description: Concepts of authoring in AEM
uuid: 824c8b91-07c7-471b-b3aa-5a73d6d48414
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 72ee013a-7a60-41ee-9421-2846e4c6bc68
exl-id: 23e30de9-1a30-484a-b370-f9f0d45b4e41
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 62%

---

# Konzept der Bearbeitung und Veröffentlichung{#authoring}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM bietet Ihnen zwei Umgebungen:

* Autor
* Veröffentlichung

Diese interagieren und ermöglichen es Ihnen, Inhalte auf Ihrer Website verfügbar zu machen, damit Ihre Besucher sie lesen können.

Die Autorenumgebung bietet die Mechanismen zum Erstellen, Aktualisieren und Überprüfen dieses Inhalts, bevor er tatsächlich veröffentlicht wird:

* Ein Autor erstellt und überprüft den Inhalt (dabei kann es sich um verschiedene Inhaltstypen handeln, z. B. Seiten, Assets, Veröffentlichungen usw.),
* der zu einem späteren Zeitpunkt auf Ihrer Website veröffentlicht wird.

![chlimage_1-289](assets/chlimage_1-289.png)

In der Autorenumgebung werden die Funktionen von AEM in zwei Benutzeroberflächen bereitgestellt. In der Veröffentlichungsumgebung entwerfen Sie das Aussehen der Oberfläche, die Sie Ihren Benutzern zur Verfügung stellen.

## Autorenumgebung {#author-environment}

Der Autor arbeitet in der sogenannten **[Autorenumgebung](/help/sites-authoring/home.md)**. Diese bietet eine einfach zu verwendende Oberfläche (grafische Benutzeroberfläche (GUI oder UI)) zum Erstellen von Inhalt. Normalerweise befindet sich diese hinter der Firewall eines Unternehmens, die vollen Schutz bietet und eine Anmeldung des Autors mit einem Konto mit entsprechenden Zugriffsrechten erfordert.

>[!NOTE]
>
>Ihr Konto muss über die entsprechenden Zugriffsrechte verfügen, um Inhalte zu erstellen, zu bearbeiten oder zu veröffentlichen.

Je nachdem, wie Ihre Instanz und Ihre persönlichen Zugriffsrechte konfiguriert sind, können Sie viele Aufgaben an Ihrem Inhalt ausführen, darunter (unter anderem):

* Erstellen neuer Inhalte oder Bearbeiten vorhandener Inhalte auf einer Seite
* Verwenden vordefinierter Vorlagen zum Erstellen neuer Inhaltsseiten
* Erstellen, Bearbeiten und Verwalten von Assets und Sammlungen
* Erstellen, Bearbeiten und Verwalten von Veröffentlichungen
* Entwickeln von Kampagnen und damit zusammenhängenden Ressourcen
* Entwickeln und Verwalten von Community-Sites
* Verschieben, Kopieren oder Löschen von Inhaltsseiten, Assets usw.
* Veröffentlichen (oder Rückgängigmachen der Veröffentlichung) von Seiten, Assets usw.

Außerdem gibt es administrative Aufgaben, die Sie beim Verwalten des Inhalts unterstützen:

* Workflows für die Verwaltung von Änderungen, zum Beispiel: Erzwingen einer Überprüfung vor der Veröffentlichung
* Projekte zur Koordinierung einzelner Aufgaben

>[!NOTE]
>
>AEM [verabreicht](/help/sites-administering/home.md) (für die meisten Aufgaben) aus der Autorenumgebung.

## Veröffentlichungsumgebung {#publish-environment}

Wenn die Inhalte der AEM-Site fertig sind, werden sie in der **Veröffentlichungsumgebung** veröffentlicht. Hier werden die Seiten der Website in Übereinstimmung mit dem Aussehen der entworfenen Oberfläche der vorgesehenen Zielgruppe bereitgestellt.

Normalerweise befindet sich die Veröffentlichungsumgebung in der demilitarisierten Zone. mit anderen Worten, für das Internet verfügbar, aber nicht mehr unter dem vollen Schutz des internen Netzes.

Wenn die AEM Site ein [Community-Site](/help/communities/overview.md)oder enthält [Communities-Komponenten](/help/communities/author-communities.md), können angemeldete Site-Besucher (Mitglieder) mit Communities-Funktionen interagieren. Sie können beispielsweise in einem Forum posten, Kommentare abgeben oder anderen Mitgliedern folgen. Mitglieder erhalten möglicherweise die Berechtigung, Aktivitäten durchzuführen, die normalerweise nur in der Autorenumgebung verfügbar sind. Hierzu gehören unter anderem das Erstellen neuer Seiten (Community-Gruppen) oder Blog-Beiträge oder die Moderation der Beiträge anderer Mitglieder.

>[!NOTE]
>
>Leider gibt es manchmal Überschneidungen in der verwendeten Terminologie. Dies kann passieren mit:
>
>* **Veröffentlichen/Veröffentlichung rückgängig machen**
   >  Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihren Inhalt in Ihrer Veröffentlichungsumgebung verfügbar machen (oder dies rückgängig machen).
>
>* **Aktivieren/Deaktivieren**
   >  Diese Begriffe sind Synonyme für das Veröffentlichen/Rückgängigmachen der Veröffentlichung. Sie werden in der klassischen Benutzeroberfläche häufiger verwendet.
>
>* **Replizieren/Replikation**
   >  Dies sind technische Begriffe, die für die Verschiebung von Daten (z. B. Seiteninhalte, Dateien, Code, Benutzerkommentare) zwischen Umgebungen verwendet werden, z. B. beim Publishing oder beim Zurückreplizieren von Benutzerkommentaren.
>


## Dispatcher {#dispatcher}

Um eine optimale Nutzung der Website durch Ihre Besucher zu gewährleisten, führt der **[Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/user-guide.html) Lastenausgleiche und Caching durch.**
