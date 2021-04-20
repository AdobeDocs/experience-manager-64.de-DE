---
title: Versionsbereinigung
seo-title: Versionsbereinigung
description: In diesem Artikel werden die verfügbaren Optionen für die Versionsbereinigung beschrieben.
seo-description: In diesem Artikel werden die verfügbaren Optionen für die Versionsbereinigung beschrieben.
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
feature: Configuring
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 64%

---


# Versionsbereinigung{#version-purging}

Bei einer Standardinstallation erstellt AEM eine neue Version einer Seite oder eines Knotens, wenn Sie eine Seite nach der Aktualisierung des Inhalts aktivieren.

>[!NOTE]
>
>Werden keine Änderungen am Inhalt vorgenommen, wird eine Meldung angezeigt, dass die Seite aktiviert wurde. Es wird jedoch keine neue Version erstellt.

Mit der Registerkarte **Versionierung** des Sidekicks können Sie auf Anforderung zusätzliche Versionen erstellen. Diese Versionen werden im Repository gespeichert und können bei Bedarf wiederhergestellt werden.

Diese Versionen werden nie bereinigt. Daher wächst die Größe des Repositorys im Laufe der Zeit an und muss verwaltet werden.

AEM stellt eine Reihe von Mechanismen zum Verwalten Ihres Repositorys zur Verfügung:

* [Version Manager](#version-manager)

   Dies kann so konfiguriert werden, dass alte Versionen beim Erstellen neuer Versionen bereinigt werden.

* Tool [Versionen entfernen](/help/sites-deploying/monitoring-and-maintaining.md#version-purging)

   Dies wird zur Überwachung und Wartung Ihres Repositorys verwendet.

   Hiermit können Sie alte Versionen eines Knotens oder eine Hierarchie von Knoten entsprechend den folgenden Parametern entfernen:

   * Die maximale Anzahl der Versionen, die im Repository gespeichert werden sollen.

      Wird dieser Wert überschritten, wird die älteste Version entfernt.

   * Das Höchstalter einer im Repository gespeicherten Version.

      Wenn das Alter einer Version diesen Wert überschreitet, wird sie aus dem Repository gelöscht.

* die [Aufgabe Versionsbereinigung (Maintenance)](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). Sie können die Wartungsaufgabe zur Versionsbereinigung planen, um alte Versionen automatisch zu löschen. Dadurch wird die manuelle Verwendung der Werkzeuge zum Bereinigen der Version minimiert.

>[!CAUTION]
>
>Um die Größe des Repositorys zu optimieren, sollten Sie die Aufgabe zur Versionsbereinigung regelmäßig ausführen. Die Aufgabe sollte außerhalb der Geschäftszeiten geplant werden, wenn der Netzwerkverkehr begrenzt ist.

## Versions-Manager {#version-manager}

Zusätzlich zum expliziten Löschen mit dem Bereinigungs-Tool kann der Versionsmanager so konfiguriert werden, dass alte Versionen bei der Erstellung von neuen Versionen entfernt werden.

Um den Versionsmanager entsprechend zu konfigurieren, erstellen Sie eine Konfiguration für:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Die folgenden Optionen sind verfügbar:

* `versionmanager.createVersionOnActivation` (Boolescher Wert, Standard: true)

   ob beim Aktivieren von Seiten eine Version erstellt werden soll.

   Eine Version wird erst erstellt, wenn der Replizierungsagenten so konfiguriert ist, dass die Erstellung von Versionen unterdrückt wird, was vom Version Manager berücksichtigt wird

   Eine Version wird nur erstellt, wenn die Aktivierung auf Pfaden erfolgt, die in versionmanager.ivPaths enthalten sind (siehe unten).

* `versionmanager.ivPaths` (Zeichenfolge[], Standard: {&quot;/&quot;})

   Pfade, auf denen Versionen implizit auf der Aktivierung erstellt werden, wenn versionmanager.createVersionOnActivation true ist.

* `versionmanager.purgingEnabled` (Boolescher Wert, Standard: false)

   ob das Bereinigen aktiviert werden soll, wenn neue Versionen erstellt werden

* `versionmanager.purgePaths` (Zeichenfolge[], Standard: {&quot;/content&quot;})

   auf welchen Pfaden Versionen bereinigt werden, wenn neue Versionen erstellt werden.

* `versionmanager.maxAgeDays` (int, Standard: 30)

   Bei der Bereinigung werden alle älteren Versionen entfernt. Wenn dieser Wert kleiner als 1 ist, wird das Bereinigen nicht basierend auf dem Alter der Version durchgeführt

* `versionmanager.maxNumberVersions` (int, Standard 5)

   Bei der Bereinigung werden alle älteren Versionen als die n. neueste Version entfernt. Wenn dieser Wert kleiner als 1 ist, wird das Bereinigen nicht basierend auf der Anzahl der Versionen durchgeführt

* `versionmanager.minNumberVersions` (int, Standard 0)

   Die Mindestanzahl der Versionen, die unabhängig vom Alter beibehalten werden sollen. Wenn hier ein Wert kleiner 1 festgelegt ist, werden keine Versionen beibehalten.

>[!NOTE]
>
>Es wird nicht empfohlen, eine große Anzahl von Versionen im Repository zu halten. Achten Sie also bei der Konfiguration des Versions-Bereinigungsvorgangs darauf, nicht zu viele Versionen von der Bereinigung auszuschließen, da sonst die Größe des Repositorys nicht richtig optimiert wird. Wenn Sie aufgrund einer Geschäftsanforderung eine große Anzahl von Versionen behalten, wenden Sie sich bitte an den Support der Adobe, um alternative Möglichkeiten zur Optimierung der Repository-Größe zu finden.

### Kombinieren von Aufbewahrungsoptionen {#combining-retention-options}

Die Optionen, mit denen festgelegt wird, welche Versionen beibehalten werden sollen ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), können je nach Ihren Anforderungen kombiniert werden.

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

## Tool „Versionen bereinigen“{#purge-versions-tool}

Das Tool [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) dient zum Bereinigen der Versionen eines Knotens oder einer Hierarchie von Knoten in Ihrem Repository. Der Hauptzweck ist die Verkleinerung des Repositorys durch Löschen alter Knotenversionen.
