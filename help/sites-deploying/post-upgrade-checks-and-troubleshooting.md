---
title: Prüfungen und Fehlerbehebung nach einem Upgrade
seo-title: Post Upgrade Checks and Troubleshooting
description: Erfahren Sie, wie Sie Probleme beheben, die nach einem Upgrade auftreten können.
seo-description: Learn how to troubleshoot issues that might appear after an upgrade.
uuid: 3f83e8fc-1c45-4ef0-b8da-d29ff483d3d5
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: bc8c9aa2-f669-41f3-a526-6146ff5cf0cd
feature: Upgrading
exl-id: edd6e933-59ed-4d7e-8934-7e2ec485cfb9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 75%

---

# Prüfungen und Fehlerbehebung nach einem Upgrade{#post-upgrade-checks-and-troubleshooting}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Prüfungen nach einem Upgrade {#post-upgrade-checks}

Nach einem [ersetzenden Upgrade](/help/sites-deploying/in-place-upgrade.md) sollten folgende Schritte durchgeführt werden, um das Upgrade abzuschließen. Es wird davon ausgegangen, dass AEM mit der 6.4-JAR-Datei gestartet wurde und dass die aktualisierte Codebasis bereitgestellt wurde.

* [Überprüfen der Protokolle auf ein erfolgreiches Upgrade](#verify-logs-for-upgrade-success)

* [Überprüfen von OSGi-Paketen](#verify-osgi-bundles)

* [Überprüfen der Oak-Version](#verify-oak-version)

* [Überprüfen des Ordners „PreUpgradeBackup“](#inspect-preupgradebackup-folder)

* [Erstüberprüfung von Seiten](#initial-validation-of-pages)
* [Anwenden von AEM Service Packs](#apply-aem-service-packs)

* [Migrieren von AEM-Funktionen](#migrate-aem-features)

* [Überprüfen der Konfigurationen für die geplante Wartung](#verify-scheduled-maintenance-configurations)

* [Aktivieren von Replikationsagenten](#enable-replication-agents)

* [Aktivieren von benutzerdefinierten geplanten Aufträgen](#enable-custom-scheduled-jobs)

* [Testplan ausführen](#execute-test-plan)

### Überprüfen der Protokolle auf ein erfolgreiches Upgrade {#verify-logs-for-upgrade-success}

**upgrade.log**

Bisher mussten diverse Protokolldateien, Teile des Repositorys und das Launchpad sorgfältig überprüft werden, um den Status Ihrer Instanz nach einem Upgrade zu bestimmen. Durch das Generieren von Berichten nach einer Aktualisierung können defekte Upgrades erkannt werden, bevor Instanzen zum Einsatz kommen.

Der primäre Zweck dieser Funktion besteht darin, den manuellen Interpretationsaufwand zu reduzieren oder eine komplexe Parsing-Logik für mehrere Endpunkte zu vermeiden, die erforderlich sind, um den Erfolg eines Upgrades zu qualifizieren. Die Lösung zielt darauf ab, für externe Automatisierungssysteme eindeutige Informationen bereitzustellen, damit diese auf den Erfolg oder das festgestellte Fehlschlagen einer Aktualisierung reagieren können.

Insbesondere wird Folgendes sichergestellt:

* Fehlgeschlagene Upgrades, die vom Upgrade-Framework erkannt werden, werden in einem einzigen Upgrade-Bericht zusammengefasst.
* Der Upgrade-Bericht enthält Indikatoren über notwendige manuelle Eingriffe.

Um diesem Rechnung zu tragen, wurde das Verfahren für die Generierung von Protokollen in der Datei `upgrade.log` geändert.

Dies ist ein Beispielbericht für ein Upgrade ohne Fehler:

![1487887443006](assets/1487887443006.png)

Dies ist ein Beispielbericht mit einem Paket, das beim Upgrade-Vorgang nicht installiert wurde:

![1487887532730](assets/1487887532730.png)

**error.log**

Die Datei „error.log“ sollte beim Start von AEM und danach anhand der JAR-Datei der Zielversion sorgfältig überprüft werden. Alle Warnungen und Fehler müssen dabei geprüft werden. Im Allgemeinen ist es am besten, am Anfang der Datei nach möglichen Problemen zu suchen. Fehler, die weiter unten im Protokoll aufgeführt werden, sind u. U. Nebeneffekte einer Grundursache, die sich am Dateianfang findet. Wenn wiederholte Fehler und Warnungen auftreten, finden Sie im nachfolgenden Abschnitt [Analysieren von Problemen beim Upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-upgrade) weitere Informationen.

### Überprüfen von OSGi-Paketen {#verify-osgi-bundles}

Navigieren Sie zur OSGi-Konsole unter `/system/console/bundles` und überprüfen Sie, ob irgendwelche Pakete nicht gestartet wurden. Wenn Pakete den Status „Installiert“ aufweisen, überprüfen Sie die Datei `error.log`, um die Grundursache zu bestimmen.

### Überprüfen der Oak-Version {#verify-oak-version}

Nach dem Upgrade sollte ersichtlich sein, dass die Oak-Version auf Version **1.8.2** aktualisiert wurde. Um die Oak-Version zu überprüfen, navigieren Sie zur OSGi-Konsole und suchen Sie nach der entsprechenden Version der Oak-Pakete: Oak Core, Oak Commons, Oak Segment-TAR.

### Überprüfen des Ordners „PreUpgradeBackup“ {#inspect-preupgradebackup-folder}

Während des Upgrades versucht AEM, die Anpassungen zu sichern und sie unter `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>` zu speichern. Um diesen Ordner in CRXDE Lite anzuzeigen, müssen Sie [CRXDE Lite vorübergehend aktivieren](/help/sites-administering/enabling-crxde-lite.md).

Der Ordner mit dem Zeitstempel sollte die Eigenschaft `mergeStatus` mit dem Wert `COMPLETED` aufweisen. Der Ordner **to-process** sollte leer sein und der Knoten **overwritten** zeigt an, welche Knoten beim Upgrade überschrieben wurden. Unter dem Knoten **leftovers** angezeigte Inhalte konnten beim Upgrade nicht problemlos zusammengeführt werden. Wenn Ihre Implementierung von einem der untergeordneten Knoten abhängig ist (und noch nicht von Ihrem aktualisierten Code-Paket installiert wurde), müssen sie manuell zusammengeführt werden.

Deaktivieren Sie die CRXDE Lite nach dieser Übung, wenn Sie sich in einer Staging- oder Produktionsumgebung befinden.

### Erstüberprüfung von Seiten {#initial-validation-of-pages}

Führen Sie in AEM eine Erstüberprüfung mithilfe von mehreren Seiten durch. Wenn eine Autorenumgebung ein Upgrade erhält, öffnen Sie die Startseite und die Begrüßungsseite (`/aem/start.html`, `/libs/cq/core/content/welcome.html`). Öffnen Sie in Autoren- und Veröffentlichungsumgebungen einige Anwendungsseiten und prüfen Sie, ob diese richtig angezeigt werden. Wenn Probleme auftreten, finden Sie in der Datei `error.log` weitere Informationen zur Fehlerbehebung.

### Anwenden von AEM Service Packs {#apply-aem-service-packs}

Wenden Sie alle relevanten AEM 6.4 Service Packs an, falls diese veröffentlicht wurden.

### Migrieren AEM Funktionen {#migrate-aem-features}

Für eine Reihe von Funktionen in AEM sind nach einem Upgrade zusätzliche Schritte erforderlich. Eine vollständige Liste dieser Funktionen und Schritte zur Migration in AEM 6.4 finden Sie im [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) Seite.

### Überprüfen der Konfigurationen für die geplante Wartung {#verify-scheduled-maintenance-configurations}

#### Datenspeicherbereinigung aktivieren {#enable-data-store-garbage-collection}

Wenn Sie einen Dateidatenspeicher verwenden, stellen Sie sicher, dass die Aufgabe „Data Store-Abfallsammlung“ aktiviert ist und zur Liste für die wöchentliche Wartung hinzugefügt wurde. Anweisungen hierzu finden Sie [hier](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Dies wird für benutzerdefinierte S3-Datenspeicherinstallationen oder bei Verwendung eines freigegebenen Datenspeichers nicht empfohlen.

#### Aktivieren der Online-Revisionsbereinigung {#enable-online-revision-cleanup}

Wenn Sie MongoMK oder das neue TarMK-Segmentformat verwenden, stellen Sie sicher, dass die Aufgabe „Revisionsbereinigung“ aktiviert ist und zur Liste für die tägliche Wartung hinzugefügt wurde. Anleitungen [here](/help/sites-deploying/revision-cleanup.md).

### Testplan ausführen {#execute-test-plan}

Ausführlichen Testplan gemäß Definition ausführen [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) unter **Testverfahren** Abschnitt.

### Aktivieren von Replikationsagenten {#enable-replication-agents}

Wenn eine Veröffentlichungsumgebung vollständig upgegradet und überprüft wurde, aktivieren Sie die Replikationsagenten in der Autorenumgebung. Vergewissern Sie sich, dass die Agenten eine Verbindung mit den jeweiligen Veröffentlichungsinstanzen herstellen können. Siehe [Aktualisierungsverfahren](/help/sites-deploying/upgrade-procedure.md) für weitere Details zur Reihenfolge der Ereignisse.

### Aktivieren von benutzerdefinierten geplanten Aufträgen {#enable-custom-scheduled-jobs}

Alle geplanten Aufträge, die Teil der Codebasis sind, können zu diesem Zeitpunkt aktiviert werden.

## Analysieren von Upgrade-Problemen {#analyzing-issues-with-upgrade}

In diesem Abschnitt sind einige Problemszenarien enthalten, die möglicherweise im Zuge des Upgrades auf AEM 6.4 auftreten.

Diese Szenarien sollen dabei helfen, die Grundursache der mit dem Upgrade im Zusammenhang stehenden Probleme zu identifizieren. Ferner sollen sie dazu beitragen, projekt- oder produktspezifische Probleme zu ermitteln.

### Neuerstellen der Dynamic Media Cloud-Konfiguration nach der Aktualisierung {#dynamic-media-cloud-configuration}

Nach dem Upgrade von einer früheren Version auf AEM 6.4 ist die Dynamic Media Cloud-Konfiguration aus früheren Einstellungen unter Umständen nicht mehr über die TouchUI von AEM 6.4 verfügbar. Um dieses Problem zu beheben, verwenden Sie CRXDE Lite , um die vorherigen Einstellungen zu entfernen, und erstellen Sie dann eine neue Dynamic Media Cloud-Konfiguration. Siehe auch [Dynamic Media-Repository-Umstrukturierung in AEM 6.4](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md).

### Repository-Migration fehlgeschlagen  {#repository-migration-failing-}

Die Datenmigration von CRX2 auf OAK sollte für alle Szenarien mit Quellinstanzen auf Basis von CQ 5.4 durchführbar sein. Stellen Sie sicher, dass Sie die Upgrade-Anweisungen in diesem Dokument genau befolgen. Dazu gehört auch, dass Sie die Datei `repository.xml` entsprechend vorbereiten und sicherstellen, dass keine benutzerdefinierte Authentifizierung über JAAS gestartet wurde und dass die Instanz vor dem Start der Migration auf Inkonsistenzen überprüft wurde.

Wenn bei der Migration weiterhin Fehler auftreten, können Sie die Grundursache bestimmen, indem Sie die Datei `upgrade.log` überprüfen. Wenn das Problem noch nicht bekannt ist, melden Sie es dem Support.

### Upgrade wurde nicht ausgeführt {#the-upgrade-did-not-run}

Stellen Sie vor Beginn der vorbereitenden Schritte sicher, dass zuerst die **Quellinstanz** ausgeführt wird. Verwenden Sie hierzu den Java-Befehl „-jar aem-quickstart.jar“. Dieser Schritt ist notwendig, um zu gewährleisten, dass die Datei „quickstart.properties“ ordnungsgemäß generiert wird. Fehlt diese Datei, wird das Upgrade nicht durchgeführt. Alternativ dazu können Sie im Installationsordner der Quellinstanz unter `crx-quickstart/conf` prüfen, ob die Datei vorhanden ist. Darüber hinaus muss sie beim Starten von AEM für das Upgrade mit dem Java-Befehl „-jar aem-quickstart.jar“ ausgeführt werden. Beim Starten mit einem Startskript wird AEM nicht im Upgrade-Modus gestartet.

### Fehlerhafte Aktualisierung von Paketen  {#packages-and-bundles-fail-to-update-}

Wenn Pakete während des Upgrades nicht installiert werden können, werden die darin enthaltenen Pakete ebenfalls nicht aktualisiert. Diese Kategorie von Problemen wird normalerweise durch eine Fehlkonfiguration des Datenspeichers verursacht. Sie werden auch als **FEHLER** und **WARN** Meldungen in der Datei error.log. Da in den meisten dieser Fälle die Standardanmeldung möglicherweise nicht funktioniert, können Sie CRXDE direkt verwenden, um die Konfigurationsprobleme zu untersuchen und zu finden.

### Einige AEM-Pakete wechseln nicht in den aktiven Status {#some-aem-bundles-are-not-switching-to-the-active-state}

Im Falle nicht startender Paketen sollten Sie diese auf nicht erfüllte Abhängigkeiten überprüfen.

Wenn dieses Problem auftritt, jedoch auf eine fehlerhafte Paketinstallation zurückzuführen ist, wodurch Pakete nicht aktualisiert werden, werden diese für die neue Version als inkompatibel angesehen. Weitere Informationen über die entsprechende Fehlerbehebung finden Sie oben unter **Fehlerhafte Aktualisierung von Pakete**.

Es wird zudem empfohlen, die Paket-Liste einer aktuellen AEM 6.4-Instanz mit der upgegradeten zu vergleichen, um nicht aktualisierte Pakete zu ermitteln. Dadurch kann der Bereich der zu suchenden Elemente in der Datei `error.log` eingegrenzt werden.

### Benutzerdefinierte Pakete wechseln nicht in den aktiven Status {#custom-bundles-not-switching-to-the-active-state}

Wenn Ihre benutzerdefinierten Pakete nicht in den aktiven Status wechseln, liegt dies höchstwahrscheinlich an Code, der die geänderte API nicht importiert. Dies führt meist zu nicht zufrieden stellenden Abhängigkeiten.

Eine gelöschte API sollte in einer der vorherigen Versionen als veraltet markiert werden. In diesem Hinweis zur veralteten Version finden Sie u. U. Anweisungen über eine direkte Migration Ihres Codes. Die Adobe zielt nach Möglichkeit auf die semantische Versionierung ab, sodass die Versionen auf brechende Änderungen hinweisen können.

Es empfiehlt sich zudem, zu überprüfen, ob die Änderung, die das Problem verursacht hat, unbedingt nötig war, und sie zurückzusetzen, wenn dies nicht der Fall ist. Überprüfen Sie außerdem, ob die Versionssteigerung des Package-Exports nach strikter semantischer Versionierung mehr als nötig erhöht wurde.

### Fehlerhafte Benutzeroberfläche der Plattform {#malfunctioning-platform-ui}

Im Falle bestimmter Benutzeroberflächenfunktionen, die nach dem Upgrade nicht richtig funktionieren, sollten Sie zunächst eine Überprüfung auf benutzerdefinierte Überlagerungen der Oberfläche vornehmen. Einige Strukturen haben sich möglicherweise geändert und die Überlagerung muss möglicherweise aktualisiert werden oder ist veraltet.

Führen Sie anschließend eine Überprüfung auf JavaScript-Fehler durch, die möglicherweise auf benutzerdefinierte, hinzugefügte Erweiterungen zurückzuführen sind, welche mit Client-Bibliotheken verknüpft sind. Dasselbe kann für benutzerdefiniertes CSS gelten, das möglicherweise Probleme beim AEM-Layout verursacht.

Führen Sie abschließend eine Überprüfung auf fehlerhafte Konfigurationen durch, die von JavaScript möglicherweise nicht verarbeitet werden können. Dies ist normalerweise bei falsch deaktivierten Erweiterungen der Fall.

### Fehlerhafte benutzerdefinierte Komponenten, Vorlagen oder Benutzeroberflächen-Erweiterungen {#malfunctioning-custom-components-templates-or-ui-extensions}

In den meisten Fällen sind die Grundursachen für diese Probleme dieselben wie für nicht gestartete oder nicht installierte Pakete. Der einzige Unterschied besteht darin, dass die Probleme bei der ersten Verwendung der Komponenten auftreten.

Bei fehlerhaftem benutzerdefiniertem Code sollten Sie zunächst Feuerproben durchführen, um die Ursache zu identifizieren. Anschließend sollten Sie in diesem Abschnitt [Link] des Artikels nach Empfehlungen suchen, wie das Problem behoben werden kann.

### Fehlende Anpassungen unter usw. {#missing-customizations-under-etc}

`/apps` und `/libs` werden bei einem Upgrade problemlos verarbeitet. Änderungen unter `/etc` müssen jedoch möglicherweise nach dem Upgrade manuell aus `/var/upgrade/PreUpgradeBackup` wiederhergestellt werden. Überprüfen Sie diesen Speicherort auf Inhalte, die manuell zusammengeführt werden müssen.

### Analysieren der Dateien „error.log“ und „upgrade.log“   {#analyzing-the-error-log-and-upgrade-log}

In den meisten Situationen müssen die Protokolle auf Fehler untersucht werden, um die Ursache eines Problems zu ermitteln. Im Falle von Upgrades ist es jedoch ebenfalls erforderlich, Abhängigkeitsfehler zu überwachen, da alte Pakete möglicherweise nicht ordnungsgemäß aktualisiert werden.

Dafür sollten Sie alle Meldungen aus der Datei „error.log“ entfernen, die erwartungsgemäß nicht mit Ihrem Problem in Zusammenhang stehen. Dies ist mit einem Tool wie grep möglich, indem Sie Folgendes verwenden:

```shell
grep -v UnrelatedErrorString
```

Einige Fehlermeldungen sind möglicherweise nicht sofort selbsterklärend. In diesem Fall kann die Anzeige des Kontexts, in dem sie auftreten, verdeutlichen, wo der Fehler verursacht wurde. Sie können den Fehler wie folgt trennen:

* `grep -B` für das Hinzufügen von Zeilen vor dem Fehler

oder

* `grep -A` für das Hinzufügen von Zeilen nach dem Fehler.

In einigen Fällen können Fehler auch in WARN-Meldungen gefunden werden, da gültige Fälle vorliegen können, die zu diesem Status führen. Die Anwendung kann darüber hinaus nicht immer entscheiden, ob ein tatsächlicher Fehler vorliegt. Stellen Sie sicher, dass Sie auch diese Nachrichten konsultieren.

### Kontaktaufnahme mit dem Adobe-Support {#contacting-adobe-support}

Wenn Sie die Empfehlungen auf dieser Seite befolgt haben und weiterhin Fehler auftreten, wenden Sie sich an den Adobe-Support. Um dem Supportmitarbeiter für Ihren Fall so viele Informationen wie möglich bereitzustellen, fügen Sie Ihrer Supportanfrage die Datei „upgrade.log“ für das Upgrade hinzu.
