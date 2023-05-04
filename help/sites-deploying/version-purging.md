---
title: Versionsbereinigung
seo-title: Version Purging
description: In diesem Artikel werden die verfügbaren Optionen für die Versionsbereinigung beschrieben.
seo-description: This article describes the available options for version purging.
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
feature: Configuring
exl-id: 357d5f23-3e75-44e3-905f-4efe960858bf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 32%

---

# Versionsbereinigung{#version-purging}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In einer Standardinstallation erstellt AEM eine neue Version einer Seite oder eines Knotens, wenn Sie eine Seite nach der Aktualisierung des Inhalts aktivieren.

>[!NOTE]
>
>Wenn keine Inhaltsänderungen vorgenommen werden, wird die Meldung angezeigt, dass die Seite aktiviert wurde, aber keine neue Version erstellt wird

Mit der Registerkarte **Versionierung** des Sidekicks können Sie auf Anforderung zusätzliche Versionen erstellen. Diese Versionen werden im Repository gespeichert und können bei Bedarf wiederhergestellt werden.

Diese Versionen werden nie gelöscht, sodass die Repository-Größe mit der Zeit zunimmt und daher verwaltet werden muss.

AEM wird mit verschiedenen Mechanismen geliefert, mit denen Sie Ihr Repository verwalten können:

* die [Version Manager](#version-manager)

   Dies kann so konfiguriert werden, dass alte Versionen bei der Erstellung neuer Versionen bereinigt werden.

* die [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#version-purging) Tool

   Dies wird im Rahmen der Überwachung und Wartung Ihres Repositorys verwendet.

   Hiermit können Sie alte Versionen eines Knotens oder eine Hierarchie von Knoten entsprechend den folgenden Parametern entfernen:

   * Die maximale Anzahl der Versionen, die im Repository gespeichert werden sollen.

      Wird dieser Wert überschritten, wird die älteste Version entfernt.

   * Das Höchstalter einer im Repository gespeicherten Version.

      Wenn das Alter einer Version diesen Wert überschreitet, wird sie aus dem Repository gelöscht.

* [Wartungsaufgabe zur Versionsbereinigung](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). Sie können die Wartungsaufgabe zur Versionsbereinigung planen, um alte Versionen automatisch zu löschen. Das verringert die Notwendigkeit, die Tools zur Versionsbereinigung manuell zu verwenden.

>[!CAUTION]
>
>Um die Größe des Repositorys zu optimieren, sollten Sie die Aufgabe zur Versionsbereinigung regelmäßig ausführen. Die Aufgabe sollte außerhalb der Geschäftszeiten geplant werden, wenn nur ein begrenzter Traffic verfügbar ist.

## Version Manager {#version-manager}

Zusätzlich zur expliziten Bereinigung mithilfe des Bereinigungs-Tools kann der Versionsmanager so konfiguriert werden, dass alte Versionen bei der Erstellung neuer Versionen bereinigt werden.

Um den Versions-Manager entsprechend zu konfigurieren, erstellen Sie eine Konfiguration für:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Die folgenden Optionen sind verfügbar:

* `versionmanager.createVersionOnActivation` (Boolesch, Standard: true)

   ob eine Version erstellt werden soll, wenn Seiten aktiviert werden.

   Es wird eine Version erstellt, es sei denn, der Replikationsagent ist so konfiguriert, dass die Erstellung von Versionen unterdrückt wird, was vom Versionsmanager berücksichtigt wird

   Eine Version wird nur erstellt, wenn die Aktivierung auf Pfaden erfolgt, die in versionmanager.ivPaths enthalten sind (siehe unten).

* `versionmanager.ivPaths` (String[], Standard: {&quot;/&quot;})

   Pfade, auf denen Versionen implizit bei Aktivierung erstellt werden, wenn versionmanager.createVersionOnActivation &quot;true&quot;ist.

* `versionmanager.purgingEnabled` (Boolesch, Standard: false)

   Ob die Bereinigung bei der Erstellung neuer Versionen aktiviert werden soll

* `versionmanager.purgePaths` (String[], Standard: {&quot;/content&quot;})

   auf welchen Pfaden Versionen gelöscht werden sollen, wenn neue Versionen erstellt werden.

* `versionmanager.maxAgeDays` (int, Standard: 30)

   Bei der Bereinigung werden alle Versionen entfernt, die älter als dieser Wert sind. Wenn dieser Wert kleiner als 1 ist, wird die Bereinigung nicht basierend auf dem Alter der Version durchgeführt

* `versionmanager.maxNumberVersions` (int, Standard 5)

   Bei der Bereinigung werden alle Versionen entfernt, die älter als die n. neueste Version sind. Wenn dieser Wert kleiner als 1 ist, wird die Bereinigung nicht basierend auf der Anzahl der Versionen durchgeführt

* `versionmanager.minNumberVersions` (int, Standard 0)

   Die Mindestanzahl der Versionen, die unabhängig vom Alter beibehalten werden sollen. Wenn dieser Wert auf einen Wert kleiner als 1 gesetzt ist, wird keine Mindestanzahl von Versionen beibehalten.

>[!NOTE]
>
>Es wird nicht empfohlen, eine große Anzahl von Versionen im Repository zu halten. Achten Sie also bei der Konfiguration des Versions-Bereinigungsvorgangs darauf, nicht zu viele Versionen von der Bereinigung auszuschließen, da sonst die Größe des Repositorys nicht richtig optimiert wird. Wenn Sie aufgrund einer Geschäftsanforderung eine große Anzahl von Versionen aufbewahren, wenden Sie sich an den Support von Adobe, um alternative Möglichkeiten zur Optimierung der Repository-Größe zu finden.

### Kombinieren von Aufbewahrungsoptionen {#combining-retention-options}

Die Optionen, mit denen definiert wird, welche Versionen aufbewahrt werden sollen (`maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), können gemäß Ihren Anforderungen kombiniert werden.

Beispielsweise bei der Definition der maximalen Anzahl von Versionen, die beibehalten werden sollen, UND der ältesten Version, die beibehalten werden soll:

* Einstellung:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* Mit:

   * 10 Versionen, die in den letzten 60 Tagen erstellt wurden
   * 3 dieser Versionen, die innerhalb der letzten 30 Tage erstellt wurden

* bedeutet Folgendes:

   * Die letzten drei Versionen werden beibehalten

Beispielsweise bei der Definition der maximalen UND minimalen Anzahl von Versionen, die beibehalten werden sollen, UND der ältesten Version, die beibehalten werden soll:

* Einstellung:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Mit:

   * 5 Versionen vor 60 Tagen

* bedeutet Folgendes:

   * 3 Versionen werden beibehalten

## Versionsbereinigungs-Tool {#purge-versions-tool}

Das Tool [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) dient zum Bereinigen der Versionen eines Knotens oder einer Hierarchie von Knoten in Ihrem Repository. Ihr Hauptzweck besteht darin, Ihnen zu helfen, die Größe Ihres Repositorys zu reduzieren, indem Sie alte Versionen Ihrer Knoten entfernen.
