---
title: Prüfungen und Fehlerbehebung nach einer Aktualisierung
seo-title: Post Upgrade Checks and Troubleshooting
description: Erfahren Sie, wie Sie Probleme beheben, die nach einer Aktualisierung auftreten können.
seo-description: Learn how to troubleshoot issues that might appear after an upgrade.
uuid: 3f83e8fc-1c45-4ef0-b8da-d29ff483d3d5
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: bc8c9aa2-f669-41f3-a526-6146ff5cf0cd
feature: Upgrading
exl-id: edd6e933-59ed-4d7e-8934-7e2ec485cfb9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1871'
ht-degree: 88%

---

# Prüfungen und Fehlerbehebung nach einer Aktualisierung{#post-upgrade-checks-and-troubleshooting}

## Prüfungen nach einer Aktualisierung {#post-upgrade-checks}

Nach einer [ersetzenden Aktualisierung](/help/sites-deploying/in-place-upgrade.md) sollten folgende Schritte durchgeführt werden, um die Aktualisierung abzuschließen. Es wird davon ausgegangen, dass AEM mit der 6.4-JAR-Datei gestartet und die aktualisierte Codebasis bereitgestellt wurde.

* [Überprüfen der Protokolle auf eine erfolgreiches Aktualisierung](#verify-logs-for-upgrade-success)

* [Überprüfen von OSGi-Bundles](#verify-osgi-bundles)

* [Überprüfen der Oak-Version](#verify-oak-version)

* [Überprüfen des Ordners „PreUpgradeBackup“](#inspect-preupgradebackup-folder)

* [Erstüberprüfung von Seiten](#initial-validation-of-pages)
* [Anwenden von AEM Service Packs](#apply-aem-service-packs)

* [Migrieren von AEM-Funktionen](#migrate-aem-features)

* [Überprüfen der Konfigurationen für die geplante Wartung](#verify-scheduled-maintenance-configurations)

* [Aktivieren von Replikationsagenten](#enable-replication-agents)

* [Aktivieren von benutzerdefinierten geplanten Aufträgen](#enable-custom-scheduled-jobs)

* [Durchführen des Testplans](#execute-test-plan)

### Überprüfen der Protokolle auf eine erfolgreiche Aktualisierung {#verify-logs-for-upgrade-success}

**upgrade.log**

Bisher mussten diverse Protokolldateien, Teile des Repositorys und das Launchpad sorgfältig überprüft werden, um den Status Ihrer Instanz nach einer Aktualisierung zu bestimmen. Durch das Generieren von Berichten nach einer Aktualisierung können defekte Aktualisierungen erkannt werden, bevor Instanzen zum Einsatz kommen.

Der primäre Zweck dieser Funktion besteht darin, den manuellen Interpretationsaufwand zu reduzieren oder eine komplexe Parsing-Logik für mehrere Endpunkte zu vermeiden, die erforderlich sind, um den Erfolg einer Aktualisierung zu qualifizieren. Ziel der Lösung ist es, eindeutige Informationen für externe Automatisierungssysteme bereitzustellen, damit diese auf den Erfolg oder das festgestellte Fehlschlagen einer Aktualisierung reagieren können.

Sie dient vor allem dazu, Folgendes sicherzustellen:

* Fehlgeschlagene Aktualisierungen, die vom Aktualisierungs-Framework erkannt werden, werden in einem einzigen Aktualisierungsbericht zusammengefasst.
* Der Bericht enthält Indikatoren über notwendige manuelle Eingriffe.

Um diesem Rechnung zu tragen, wurde das Verfahren für die Generierung von Protokollen in der Datei `upgrade.log` geändert.

Dies ist ein Beispielbericht für eine Aktualisierung ohne Fehler:

![148787443006](assets/1487887443006.png)

Dies ist ein Beispielbericht mit einem Bundle, das beim Aktualisierungsvorgang nicht installiert wurde:

![1487887532730](assets/1487887532730.png)

**error.log**

Die Datei „error.log“ sollte beim Start von AEM und danach anhand der JAR-Datei der Zielversion sorgfältig überprüft werden. Alle Warnungen und Fehler müssen dabei geprüft werden. Im Allgemeinen ist es am besten, am Anfang der Datei nach möglichen Problemen zu suchen. Fehler, die weiter unten im Protokoll aufgeführt werden, sind u. U. Nebeneffekte einer Grundursache, die sich am Dateianfang findet. Wenn wiederholte Fehler und Warnungen auftreten, finden Sie im nachfolgenden Abschnitt [Analysieren von Problemen bei der Aktualisierung](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-upgrade) weitere Informationen.

### Überprüfen von OSGi-Bundles {#verify-osgi-bundles}

Navigieren Sie zur OSGi-Konsole `/system/console/bundles` und überprüfen Sie, ob keine Bundles gestartet wurden. Wenn sich Pakete in einem installierten Zustand befinden, lesen Sie den Abschnitt `error.log` um das Problem zu ermitteln.

### Überprüfen der Oak-Version {#verify-oak-version}

Nach der Aktualisierung sollte ersichtlich sein, dass die Oak-Version auf Version **1.8.2** aktualisiert wurde. Um die Oak-Version zu überprüfen, navigieren Sie zur OSGi-Konsole und sehen Sie sich die Version an, die Oak-Bundles zugeordnet ist: Oak-Kern, Oak-Commons, Oak-Segment-Tar.

### Überprüfen des Ordners „PreUpgradeBackup“ {#inspect-preupgradebackup-folder}

Während des Upgrades versucht AEM, Anpassungen zu sichern und sie unter `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>`. Um diesen Ordner in CRXDE Lite anzuzeigen, müssen Sie [CRXDE Lite vorübergehend aktivieren](/help/sites-administering/enabling-crxde-lite.md).

Der Ordner mit dem Zeitstempel sollte die Eigenschaft `mergeStatus` mit dem Wert `COMPLETED` aufweisen. Der Ordner **to-process** sollte leer sein und der Knoten **overwritten** zeigt an, welche Knoten bei der Aktualisierung überschrieben wurden. Unter dem Knoten **leftovers** angezeigte Inhalte konnten bei der Aktualisierung nicht problemlos zusammengeführt werden. Wenn Ihre Implementierung von einem der untergeordneten Knoten abhängig ist (und nicht bereits von Ihrem aktualisierten Codepaket installiert wurde), muss eine manuelle Zusammenführung durchgeführt werden.

Deaktivieren Sie CRXDE Lite nach dieser Übung, wenn eine Staging- oder Produktionsumgebung verwendet wird.

### Erstüberprüfung von Seiten {#initial-validation-of-pages}

Führen Sie in AEM eine Erstüberprüfung mithilfe von mehreren Seiten durch. Wenn Sie eine Autorenumgebung aktualisieren, öffnen Sie die Startseite und die Begrüßungsseite ( `/aem/start.html`, `/libs/cq/core/content/welcome.html`). Öffnen Sie in Autoren- und Veröffentlichungsumgebungen einige Anwendungsseiten und prüfen Sie, ob diese richtig angezeigt werden. Wenn Probleme auftreten, finden Sie in der Datei `error.log` weitere Informationen zur Fehlerbehebung.

### Anwenden von AEM Service Packs {#apply-aem-service-packs}

Anwenden aller relevanten AEM 6.4 Service Packs, die veröffentlicht wurden.

### Migrieren von AEM-Funktionen {#migrate-aem-features}

Für eine Reihe von Funktionen in AEM sind nach einer Aktualisierung zusätzliche Schritte erforderlich. Eine vollständige Liste dieser Funktionen und die erforderlichen Schritte zum Migrieren derselben auf AEM 6.4 finden Sie auf der Seite [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md).

### Überprüfen der Konfigurationen für die geplante Wartung {#verify-scheduled-maintenance-configurations}

#### Aktivieren der Bereinigung des Datenspeichers {#enable-data-store-garbage-collection}

Wenn Sie einen Dateidatenspeicher verwenden, stellen Sie sicher, dass die Aufgabe „Data Store-Abfallsammlung“ aktiviert ist und zur Liste für die wöchentliche Wartung hinzugefügt wurde. Anweisungen werden beschrieben [here](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Die Aufgabe wird nicht für benutzerdefinierte S3-Datenspeicherinstallationen empfohlen oder wenn ein freigegebener Datenspeicher verwendet wird.

#### Aktivieren der Online-Revisionsbereinigung {#enable-online-revision-cleanup}

Wenn Sie MongoMK oder das neue TarMK-Segmentformat verwenden, stellen Sie sicher, dass die Aufgabe „Revisionsbereinigung“ aktiviert ist und zur Liste für die tägliche Wartung hinzugefügt wurde. Anweisungen hierzu finden Sie [hier](/help/sites-deploying/revision-cleanup.md).

### Durchführen des Testplans {#execute-test-plan}

Führen Sie einen detaillierten Testplan durch, wie unter [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) im Abschnitt **Testverfahren** beschrieben.

### Aktivieren von Replikationsagenten {#enable-replication-agents}

Wenn eine Veröffentlichungsumgebung vollständig aktualisiert und überprüft wurde, aktivieren Sie die Replikationsagenten in der Autorenumgebung. Vergewissern Sie sich, dass die Agenten eine Verbindung mit den jeweiligen Veröffentlichungsinstanzen herstellen können. Siehe [Aktualisierungsverfahren](/help/sites-deploying/upgrade-procedure.md) für weitere Details zur Reihenfolge der Ereignisse.

### Aktivieren von benutzerdefinierten geplanten Aufträgen {#enable-custom-scheduled-jobs}

Zu diesem Zeitpunkt können alle geplanten Aufträge, die Teil der Codebasis sind, aktiviert werden.

## Analysieren von Aktualisierungsproblemen {#analyzing-issues-with-upgrade}

In diesem Abschnitt sind einige Problemszenarien enthalten, die möglicherweise im Zuge der Aktualisierung auf AEM 6.4 auftreten.

Diese Szenarien sollen dabei helfen, die Grundursache der mit der Aktualisierung im Zusammenhang stehenden Probleme zu identifizieren. Ferner sollen sie dazu beitragen, projekt- oder produktspezifische Probleme zu ermitteln.

### Neuerstellen der Dynamic Media Cloud-Konfiguration nach der Aktualisierung {#dynamic-media-cloud-configuration}

Nach dem Upgrade von einer früheren Version auf AEM 6.4 ist die Dynamic Media Cloud-Konfiguration aus früheren Einstellungen unter Umständen nicht mehr über die TouchUI von AEM 6.4 verfügbar. Um dieses Problem zu beheben, verwenden Sie CRXDE Lite , um die vorherigen Einstellungen zu entfernen, und erstellen Sie dann eine neue Dynamic Media Cloud-Konfiguration. Siehe auch [Dynamic Media-Repository-Umstrukturierung in AEM 6.4](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md).

### Fehler bei der Repository-Migration  {#repository-migration-failing-}

Die Datenmigration von CRX2 auf OAK sollte für alle Szenarien mit Quellinstanzen auf Basis von CQ 5.4 durchführbar sein. Stellen Sie sicher, dass Sie die Aktualisierungsanweisungen in diesem Dokument genau befolgen. Dazu gehört auch, dass Sie die Datei `repository.xml` entsprechend vorbereiten und sicherstellen, dass keine benutzerdefinierte Authentifizierung über JAAS gestartet wurde und dass die Instanz vor dem Start der Migration auf Inkonsistenzen überprüft wurde.

Wenn bei der Migration weiterhin Fehler auftreten, können Sie die Grundursache bestimmen, indem Sie die Datei `upgrade.log` überprüfen. Wenn das Problem bislang unbekannt ist, melden Sie es dem Kundensupport.

### Aktualisierung wurde nicht ausgeführt {#the-upgrade-did-not-run}

Stellen Sie vor Beginn der vorbereitenden Schritte sicher, dass zuerst die **Quellinstanz** ausgeführt wird. Verwenden Sie hierzu den Java-Befehl „-jar aem-quickstart.jar“. Dieser Schritt ist notwendig, um zu gewährleisten, dass die Datei „quickstart.properties“ ordnungsgemäß generiert wird. Fehlt diese Datei, wird die Aktualisierung nicht durchgeführt. Alternativ dazu können Sie im Installationsordner der Quellinstanz unter `crx-quickstart/conf` prüfen, ob die Datei vorhanden ist. Darüber hinaus muss sie beim Starten von AEM für die Aktualisierung mit dem Java-Befehl „-jar aem-quickstart.jar“ ausgeführt werden. Beim Starten mit einem Startskript wird AEM nicht im Aktualisierungsmodus gestartet.

### Fehlerhafte Aktualisierung von Paketen und Bundles  {#packages-and-bundles-fail-to-update-}

Wenn Pakete während der Aktualisierung nicht installiert werden können, werden die darin enthaltenen Bundles ebenfalls nicht aktualisiert. Diese Kategorie von Problemen geht für gewöhnlich auf eine Fehlkonfiguration des Datenspeichers zurück. Sie werden auch als **ERROR**- und **WARN**-Meldungen in der Datei error.log angezeigt. Da in den meisten dieser Fälle die Standardanmeldung möglicherweise nicht funktioniert, können Sie CRXDE direkt verwenden, um die Konfigurationsprobleme zu untersuchen und zu finden.

### Einige AEM-Bundles wechseln nicht in den aktiven Status {#some-aem-bundles-are-not-switching-to-the-active-state}

Im Falle nicht startender Bundles sollten Sie diese auf nicht erfüllte Abhängigkeiten überprüfen.

Wenn dieses Problem auftritt, jedoch auf eine fehlerhafte Paketinstallation zurückzuführen ist, wodurch Bundles nicht aktualisiert werden, werden diese für die neue Version als inkompatibel angesehen. Weitere Informationen über die entsprechende Fehlerbehebung finden Sie oben unter **Fehlerhafte Aktualisierung von Paketen und Bundles**.

Es wird zudem empfohlen, die Bundle-Liste einer aktuellen AEM 6.4-Instanz mit der aktualisierten zu vergleichen, um nicht aktualisierte Bundles zu ermitteln. Dadurch kann der Bereich der zu suchenden Elemente in der Datei `error.log` eingegrenzt werden.

### Benutzerdefinierte Bundles wechseln nicht in den aktiven Status {#custom-bundles-not-switching-to-the-active-state}

Wenn Ihre benutzerdefinierten Bundles nicht in den aktiven Status wechseln, liegt dies höchstwahrscheinlich an Code, der die geänderte API nicht importiert. Dies führt oftmals zu nicht erfüllten Abhängigkeiten.

Eine gelöschte API sollte in einer der vorherigen Versionen als veraltet markiert werden. In diesem Hinweis zur veralteten Version finden Sie u. U. Anweisungen über eine direkte Migration Ihres Codes. Adobe ist bestrebt, nach Möglichkeit eine semantische Versionierung zu verwenden, sodass die Versionen Änderungen anzeigen können, die Probleme verursachen.

Es empfiehlt sich zudem, zu überprüfen, ob die Änderung, die das Problem verursacht hat, unbedingt nötig war, und sie zurückzusetzen, wenn dies nicht der Fall ist. Überprüfen Sie zudem, ob die Version des Paketexports unter Beachtung einer strengen semantischen Versionierung mehr als nötig erhöht wurde.

### Fehlerhafte Plattform-Benutzeroberfläche {#malfunctioning-platform-ui}

Im Falle bestimmter Benutzeroberflächenfunktionen, die nach der Aktualisierung nicht richtig funktionieren, sollten Sie zunächst eine Überprüfung auf benutzerdefinierte Überlagerungen der Oberfläche vornehmen. Möglicherweise haben sich einige Strukturen geändert und die Überlagerung muss u. U. aktualisiert werden oder ist veraltet.

Führen Sie anschließend eine Überprüfung auf JavaScript-Fehler durch, die möglicherweise auf benutzerdefinierte, hinzugefügte Erweiterungen zurückzuführen sind, welche mit Client-Bibliotheken verknüpft sind. Dies kann auch auf ein benutzerdefiniertes CSS zutreffen, das möglicherweise Probleme am AEM-Layout verursacht.

Führen Sie abschließend eine Überprüfung auf fehlerhafte Konfigurationen durch, die von JavaScript möglicherweise nicht verarbeitet werden können. Dies ist für gewöhnlich bei unsachgemäß deaktivierten Erweiterungen der Fall.

### Fehlerhafte benutzerdefinierte Komponenten, Vorlagen oder Benutzeroberflächenerweiterungen {#malfunctioning-custom-components-templates-or-ui-extensions}

In den meisten Fällen sind die Grundursachen für diese Probleme dieselben wie für nicht gestartete Bundles oder nicht installierte Pakete. Der einzige Unterschied besteht darin, dass die Probleme bei der ersten Verwendung der Komponenten auftreten.

Bei fehlerhaftem benutzerdefiniertem Code sollten Sie zunächst Feuerproben durchführen, um die Ursache zu identifizieren. Sobald Sie sie gefunden haben, sehen Sie sich die Empfehlungen in diesem [link] des Artikels, um Möglichkeiten zu ihrer Behebung zu finden.

### Fehlende Anpassungen unter usw. {#missing-customizations-under-etc}

`/apps` und `/libs` werden durch das Upgrade gut verarbeitet, jedoch unter `/etc` möglicherweise manuell von `/var/upgrade/PreUpgradeBackup` nach der Aktualisierung. Überprüfen Sie diesen Speicherort auf Inhalte, die manuell zusammengeführt werden müssen.

### Analysieren der Dateien „error.log“ und „upgrade.log“ {#analyzing-the-error-log-and-upgrade-log}

In den meisten Situationen müssen die Protokolle auf Fehler untersucht werden, um die Ursache eines Problems zu ermitteln. Im Falle von Aktualisierungen ist es jedoch ebenfalls erforderlich, Abhängigkeitsfehler zu überwachen, da alte Bundles möglicherweise nicht ordnungsgemäß aktualisiert werden.

Dafür sollten Sie alle Meldungen aus der Datei „error.log“ entfernen, die erwartungsgemäß nicht mit Ihrem Problem in Zusammenhang stehen. Dies ist mit einem Tool wie grep möglich, indem Sie Folgendes verwenden:

```shell
grep -v UnrelatedErrorString
```

Einige Fehlermeldungen sind möglicherweise nicht sofort selbsterklärend. In diesem Fall kann die Anzeige des Kontexts, in dem sie auftreten, verdeutlichen, wo der Fehler verursacht wurde. Sie können den Fehler mithilfe der folgenden Befehle trennen:

* `grep -B` zum Hinzufügen von Zeilen vor dem Fehler;

oder

* `grep -A` zum Hinzufügen von Zeilen nach.

In einigen Fällen können Fehler auch in WARN-Meldungen gefunden werden, da gültige Fälle vorliegen können, die zu diesem Status führen. Die Anwendung kann darüber hinaus nicht immer entscheiden, ob ein tatsächlicher Fehler vorliegt. Sie sollten diese Meldungen ebenfalls lesen.

### Kontaktaufnahme mit dem Adobe-Support {#contacting-adobe-support}

Wenn Sie die Empfehlungen auf dieser Seite befolgt haben und weiterhin Fehler auftreten, wenden Sie sich an den Adobe-Support. Um dem Supportmitarbeiter für Ihren Fall so viele Informationen wie möglich bereitzustellen, fügen Sie Ihrer Supportanfrage die Datei „upgrade.log“ für die Aktualisierung hinzu.
