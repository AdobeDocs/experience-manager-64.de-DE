---
title: Aktualisieren auf AEM 6.4
seo-title: Upgrading to AEM 6.4
description: Erfahren Sie mehr über die Grundlagen der Aktualisierung einer älteren AEM-Installation auf AEM 6.4.
seo-description: Learn about the basics of upgrading an older AEM installation to AEM 6.4.
uuid: aa878528-5161-4df3-9fed-cc779fb6bdbe
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 81ceb91d-039e-45f0-9b0c-b8233901dea8
targetaudience: target-audience upgrader
feature: Upgrading
exl-id: 791da16c-bf2c-47a9-86a4-0a601a1b017e
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 71%

---

# Aktualisieren auf AEM 6.4{#upgrading-to-aem}

In diesem Abschnitt wird das Aktualisieren einer AEM-Installation auf AEM 6.4 beschrieben:

* [Planung der Aktualisierung](/help/sites-deploying/upgrade-planning.md)
* [Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor ](/help/sites-deploying/pattern-detector.md)
* [Abwärtskompatibilität in AEM 6.4](/help/sites-deploying/backward-compatibility.md)
* [Aktualisierungsverfahren](/help/sites-deploying/upgrade-procedure.md)
* [Aktualisierung von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Wartungsaufgaben vor einer Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Durchführen einer In-Place-Aktualisierung](/help/sites-deploying/in-place-upgrade.md)
* [Prüfungen und Fehlerbehebung nach einer Aktualisierung](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Nachhaltige Aktualisierungen](/help/sites-deploying/sustainable-upgrades.md)
* [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md)
* [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md)

Für ein einfacheres Verständnis der in diesen Verfahren verwendeten AEM-Instanzen werden die folgenden Begriffe in diesen Artikeln verwendet:

* Bei der *Quell* instanz handelt es sich um die AEM-Instanz, von der aus die Aktualisierung durchgeführt wird.
* Bei der *Ziel* instanz handelt es sich um die Instanz, auf die die Aktualisierung durchgeführt wird.

>[!NOTE]
>
>Im Rahmen der Bemühungen zur Verbesserung der Zuverlässigkeit von Upgrades wurde AEM 6.4 einer umfassenden Repository-Umstrukturierung unterzogen. Weitere Informationen zur Anpassung an die neue Struktur finden Sie unter [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md)

## Was wurde geändert? {#what-has-changed}

Nachfolgend sind die wichtigsten Änderungen im Vergleich zu den letzten AEM-Versionen aufgeführt:

In AEM 6.0 wurde das neue Jackrabbit-Oak-Repository eingeführt. Persistenz-Manager wurden durch [Mikrokernel](/help/sites-deploying/recommended-deploys.md) ersetzt. Ab Version 6.1 wird CRX2 nicht mehr unterstützt. Ein Migrationstool mit der Bezeichnung CRX2OAK muss ausgeführt werden, um CRX2-Repositorys von 5.6.1-Instanzen zu migrieren. Weitere Informationen finden Sie unter [Verwenden des CRX2OAK-Migrationstools](/help/sites-deploying/using-crx2oak.md).

Wenn Assets Insights verwendet werden soll und Sie von einer Version aktualisieren, die älter als AEM 6.2 ist, müssen Assets migriert werden und IDs über ein JMX-Bean generiert werden. In internen Tests wurden 125.000 Assets in einer TarMK-Umgebung innerhalb einer Stunde migriert. Ihre Ergebnisse können jedoch möglicherweise abweichen.

Mit AEM 6.3 wurde ein neues Format für die `SegmentNodeStore`, die die Grundlage der TarMK-Implementierung bildet. Wenn Sie eine Version vor AEM 6.3 aktualisieren, muss bei der Aktualisierung eine Migration des Repositorys durchgeführt werden, während der das System nicht verfügbar ist.

Adobe Engineering schätzt, dass diese Ausfallzeit ca. 20 Minuten beträgt. Beachten Sie, dass keine Neuindizierung erforderlich ist. Darüber hinaus wurde eine neue Version des CRX2OAK-Tools für das neue Repository-Format veröffentlicht.

**Diese Migration ist nicht erforderlich, wenn Sie von AEM 6.3 auf AEM 6.4 aktualisieren.**

Die Wartungsaufgaben vor einer Aktualisierung wurden optimiert, um die Automatisierung zu unterstützen.

Die Befehlszeilenoptionen für die Verwendung des CRX2OAK-Tools wurden geändert, um diese automatisierungsfreundlich zu machen und mehr Aktualisierungspfade zu unterstützen.

Die Prüfungen nach einer Aktualisierung wurden ebenfalls automatisierungsfreundlich gestaltet.

Zu den regelmäßig durchzuführenden Routinewartungsaufgaben gehören jetzt die regelmäßige Revisionsbereinigung und die Bereinigung des Datenspeichers. Mit der Einführung von AEM 6.3 unterstützt und empfiehlt Adobe die Online-Revisionsbereinigung. Weitere Informationen zum Konfigurieren dieser Aufgaben finden Sie unter [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md).

Mit **AEM 6.4** wird der [Musterdetektor](/help/sites-deploying/pattern-detector.md) eingeführt, mit dem Sie bei der Planung der Aktualisierung die Komplexität der Aktualisierung ermitteln können. In 6.4 liegt der Fokus sehr auf der [Abwärtskompatibilität](/help/sites-deploying/backward-compatibility.md) der Funktionen. Außerdem wurden Best Practices für [nachhaltige Aktualisierungen](/help/sites-deploying/sustainable-upgrades.md) hinzugefügt.

Einzelheiten zu weiteren Änderungen in den neuen AEM-Versionen finden Sie in den vollständigen Versionshinweisen:

* [https://helpx.adobe.com/de/experience-manager/6-2/release-notes.html](https://helpx.adobe.com/de/experience-manager/6-2/release-notes.html)
* [https://helpx.adobe.com/de/experience-manager/6-3/release-notes.html](https://helpx.adobe.com/de/experience-manager/6-3/release-notes.html)
* [https://helpx.adobe.com/de/experience-manager/6-4/release-notes.html](https://helpx.adobe.com/de/experience-manager/6-4/release-notes.html)

## Überblick über die Aktualisierung {#upgrade-overview}

Die Aktualisierung von AEM ist ein mehrstufiger Prozess, der in manchen Fällen mehrere Monate dauert. Die nachfolgende Darstellung gibt einen Überblick über die Bestandteile eines Aktualisierungsprojekts und die entsprechenden Inhalte, die in dieser Dokumentation enthalten sind:

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## Flussdiagramm der Aktualisierung mit Aktualisierungsverbesserungen in 6.4 {#upgrade-overview-1}

Das folgende Diagramm zeigt den für die Aktualisierung empfohlenen Ablauf. Beachten Sie den Verweis auf die neu eingeführten Funktionen. Das Upgrade sollte mit der Mustererkennung beginnen (siehe [Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor](/help/sites-deploying/pattern-detector.md)), die es Ihnen ermöglichen soll, den Pfad zu bestimmen, den Sie für die Kompatibilität mit AEM 6.4 verwenden möchten, basierend auf den Mustern im generierten Bericht.

In Version 6.4 wurde der Fokus darauf gelegt, alle neuen Funktionen abwärtskompatibel zu halten. In Fällen, in denen jedoch noch einige Abwärtskompatibilitätsprobleme auftreten, können Sie mit dem Kompatibilitätsmodus die Entwicklung zeitweise verschieben, um Ihren benutzerdefinierten Code mit 6.4 kompatibel zu halten. Dieser Ansatz hilft Ihnen, Entwicklungsaufwand unmittelbar nach der Aktualisierung zu vermeiden (siehe [Abwärtskompatibilität in AEM 6.4](/help/sites-deploying/backward-compatibility.md)).

Schließlich wurden in Ihrem 6.4-Entwicklungszyklus Funktionen eingeführt, die unter &quot;Nachhaltige Aktualisierungen&quot;eingeführt wurden (siehe [Nachhaltige Aktualisierungen](/help/sites-deploying/sustainable-upgrades.md)) helfen Ihnen, Best Practices zu befolgen, um zukünftige Upgrades noch effizienter und nahtloser zu gestalten.

![6_4_upgrade_overviewFlussdiagramm-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)
