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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 63%

---

# Versionsbereinigung{#version-purging}

Bei einer Standardinstallation erstellt AEM eine neue Version einer Seite oder eines Knotens, wenn Sie eine Seite nach der Aktualisierung des Inhalts aktivieren.

>[!NOTE]
>
>Werden keine Änderungen am Inhalt vorgenommen, wird eine Meldung angezeigt, dass die Seite aktiviert wurde. Es wird jedoch keine neue Version erstellt.

Mit der Registerkarte **Versionierung** des Sidekicks können Sie auf Anforderung zusätzliche Versionen erstellen. Diese Versionen werden im Repository gespeichert und können bei Bedarf wiederhergestellt werden.

Diese Versionen werden nie bereinigt. Daher wächst die Größe des Repositorys im Laufe der Zeit an und muss verwaltet werden.

AEM stellt eine Reihe von Mechanismen zum Verwalten Ihres Repositorys zur Verfügung:

* die [Version Manager](#version-manager)

   Dies kann so konfiguriert werden, dass alte Versionen bei der Erstellung neuer Versionen bereinigt werden.

* die [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#version-purging) Tool

   Dies wird im Rahmen der Überwachung und Wartung Ihres Repositorys verwendet.

   Hiermit können Sie alte Versionen eines Knotens oder eine Hierarchie von Knoten entsprechend den folgenden Parametern entfernen:

   * Die maximale Anzahl der Versionen, die im Repository gespeichert werden sollen.

      Wird dieser Wert überschritten, wird die älteste Version entfernt.

   * Das Höchstalter einer im Repository gespeicherten Version.

      Wenn das Alter einer Version diesen Wert überschreitet, wird sie aus dem Repository gelöscht.

* die [Wartungsaufgabe für Versionsbereinigung](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). Sie können die Wartungsaufgabe zur Versionsbereinigung planen, um alte Versionen automatisch zu löschen. Dadurch wird die Notwendigkeit minimiert, die Tools zur Versionsbereinigung manuell zu verwenden.

>[!CAUTION]
>
>Um die Größe des Repositorys zu optimieren, sollten Sie die Aufgabe zur Versionsbereinigung regelmäßig ausführen. Die Aufgabe sollte außerhalb der Geschäftszeiten geplant werden, wenn der Netzwerkverkehr begrenzt ist.

## Versions-Manager {#version-manager}

Zusätzlich zum expliziten Löschen mit dem Bereinigungs-Tool kann der Versionsmanager so konfiguriert werden, dass alte Versionen bei der Erstellung von neuen Versionen entfernt werden.

Um den Versionsmanager entsprechend zu konfigurieren, erstellen Sie eine Konfiguration für:

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

   Die Mindestanzahl der Versionen, die unabhängig vom Alter beibehalten werden sollen. Wenn hier ein Wert kleiner 1 festgelegt ist, werden keine Versionen beibehalten.

>[!NOTE]
>
>Es wird nicht empfohlen, eine große Anzahl von Versionen im Repository zu halten. Achten Sie also bei der Konfiguration des Versions-Bereinigungsvorgangs darauf, nicht zu viele Versionen von der Bereinigung auszuschließen, da sonst die Größe des Repositorys nicht richtig optimiert wird. Wenn Sie aufgrund einer Geschäftsanforderung eine große Anzahl von Versionen aufbewahren, wenden Sie sich an den Support von Adobe, um alternative Möglichkeiten zur Optimierung der Repository-Größe zu finden.

### Kombinieren von Aufbewahrungsoptionen {#combining-retention-options}

Die Optionen, die festlegen, wie welche Versionen beibehalten werden sollen ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), kann je nach Ihren Anforderungen kombiniert werden.

Wenn Sie z. B. die Anzahl der Versionen, die maximal aufbewahrt werden, UND die älteste aufzubewahrende Version definieren:

* Einstellung:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* mit:

   * 10 Versionen, die in den letzten 60 Tagen erstellt wurden,
   * von denen 3 Versionen innerhalb der letzten 30 Tage erstellt wurden,

* bedeutet dies, dass:

   * die letzten 3 Versionen aufbewahrt werden.

Wenn Sie z. B. die maximale UND die minimale Anzahl von Versionen, die aufbewahrt werden, UND die älteste beizubehaltende Version definieren:

* Einstellung:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* mit:

   * 5 Versionen, die in den letzten 60 Tagen erstellt wurden

* bedeutet dies, dass:

   * 3 Versionen aufbewahrt werden.

## Tool „Versionen bereinigen“ {#purge-versions-tool}

Das Tool [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) dient zum Bereinigen der Versionen eines Knotens oder einer Hierarchie von Knoten in Ihrem Repository. Der Hauptzweck ist die Verkleinerung des Repositorys durch Löschen alter Knotenversionen.
