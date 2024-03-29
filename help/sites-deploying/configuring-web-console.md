---
title: Web-Konsole
seo-title: Web Console
description: Erfahren Sie, wie Sie die Web-Konsole in AEM verwenden.
seo-description: Learn how to use the web console in AEM.
uuid: 047274ff-4d7d-4c7d-95be-06f363beae2e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: f934eb02-1f84-44f2-9f14-3f17250c9a90
exl-id: e03d2075-1d65-4ab3-b1bb-0bae925824c6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 63%

---

# Web-Konsole{#web-console}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Web-Konsole in AEM basiert auf der [Apache Felix Web Management Console](https://felix.apache.org/documentation/subprojects/apache-felix-web-console.html). Apache Felix ist eine Community-Anstrengung zur Implementierung der OSGi R4-Dienstplattform, die das OSGi-Framework und Standarddienste umfasst.

>[!NOTE]
>
>In der Webkonsole beziehen sich alle Beschreibungen, in denen Standardeinstellungen erwähnt werden, auf die Sling-Standardeinstellungen.
>
>Für AEM gelten eigene Standardeinstellungen, sodass sich die festgelegten Standardeinstellungen möglicherweise von denen der Konsole unterscheiden.

Die Web-Konsole bietet eine Auswahl von Registerkarten zur Verwaltung der OSGi-Bundles, darunter:

* [Konfiguration](#configuration): wird zum Konfigurieren der OSGi-Bundles verwendet und ist daher der zugrunde liegende Mechanismus zum Konfigurieren AEM Systemparameter.
* [Bundles](#bundles): wird für die Installation von Bundles verwendet
* [Komponenten](#components): zur Steuerung des Status der für AEM erforderlichen Komponenten

Alle vorgenommenen Änderungen werden sofort auf das laufende System angewendet. Es ist kein Neustart erforderlich.

Der Zugriff auf die Konsole ist über `../system/console` möglich, z. B.:

`http://localhost:4502/system/console/components`

## Konfiguration {#configuration}

Die **Konfiguration** -Tab wird zur Konfiguration der OSGi-Bundles verwendet und ist daher der zugrunde liegende Mechanismus zur Konfiguration AEM Systemparameter.

>[!NOTE]
>
>Siehe [OSGi-Konfiguration mit der Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) für weitere Informationen.

Die **Konfiguration** auf die Registerkarte kann wie folgt zugegriffen werden:

* über das Dropdown-Menü:

   **OSGi >**

* Die URL; Beispiel:

   `http://localhost:4502/system/console/configMgr`

Eine Liste der Konfigurationen wird angezeigt:

![screen_shot_2012-02-15at52308pm-1](assets/screen_shot_2012-02-15at52308pm-1.png)

Es gibt zwei Arten von Konfigurationen, die in den Dropdown-Listen auf dem Bildschirm verfügbar sind:

* **Konfigurationen**

   Ermöglicht die Aktualisierung der vorhandenen Konfigurationen. Diese weisen eine persistente Identität (PID) auf und können entweder:

   * Standard und integraler Bestandteil der AEM; Diese sind erforderlich, wenn sie gelöscht werden, kehren die Werte zu den Standardeinstellungen zurück.
   * Instanzen, die aus Factory-Konfigurationen erstellt wurden; Diese Instanzen werden vom Benutzer erstellt. Durch Löschen wird die Instanz entfernt.

* **Werkskonfigurationen**

   Ermöglicht die Erstellung einer Instanz des erforderlichen Funktionsobjekts.

   Diesem Objekt wird eine Persistent Identity (PID) zugewiesen und es wird dann in der Dropdown-Liste „Konfigurationen“ aufgeführt.

Bei Auswahl eines Eintrags aus den Listen werden die Parameter für die Konfiguration angezeigt:

![chlimage_1-61](assets/chlimage_1-61.png)

Die Parameter können dann ggf. aktualisiert werden und Sie können unter folgenden Optionen wählen:

* **Speichern**

   Speichert die vorgenommenen Änderungen.

    Für eine Factory-Konfiguration wird hierdurch eine neue Instanz mit einer Persistent Identity erstellt. Die neue Instanz wird dann unter „Konfigurationen“ aufgelistet.

* **Zurücksetzen**

   Setzt die auf dem Bildschirm gezeigten Parameter auf die zuletzt gespeicherten zurück.

* **Löschen**

   Löscht die aktuelle Konfiguration. Bei einer Standardinstanz werden die Parameter auf die Standardeinstellungen zurückgesetzt. Wenn sie über eine Factory-Konfiguration erstellt wurde, wird die spezifische Instanz gelöscht.

* **Bindung aufheben**

   Hebt die Bindung zwischen der aktuellen Konfiguration und dem Bundle auf.

* **Abbrechen**

   Verwirft alle aktuellen Änderungen.

## Bundles {#bundles}

Die Registerkarte **Pakete** stellt den Mechanismus zum Installieren der für AEM erforderlichen OSGi-Pakete dar. Sie können mit einer der beiden folgenden Methoden auf die Registerkarte zugreifen:

* über das Dropdown-Menü:

   **OSGi >**

* Die URL; Beispiel:

   `http://localhost:4502/system/console/bundles`

Eine Liste mit Bundles wird angezeigt:

![screen_shot_2012-02-15at44740pm-1](assets/screen_shot_2012-02-15at44740pm-1.png)

Auf dieser Registerkarte stehen folgende Optionen zur Verfügung:

* **Installieren oder aktualisieren**

   Hiermit können Sie nach der Datei mit Ihrem Bundle **suchen** und festlegen, ob dieses sofort **gestartet** werden soll, und mit welcher **Startebene**.

* **Neu laden**

   Aktualisiert die angezeigte Liste.

* **Pakete aktualisieren**

   Diese Option prüft die Verweise aller Pakete und aktualisiert sie ggf.

    So werden möglicherweise nach einer Aktualisierung die alte und die neue Version aufgrund vorheriger Verweise weiter ausgeführt, Diese Option prüft und transferiert alle Verweise auf die neue Version, sodass die alte Version beendet werden kann.

* **Starten**

   Startet ein Bundle gemäß der angegebenen Startebene.

* **Anhalten**

   Stoppt das Bundle.

* **Deinstallieren**

   Deinstalliert das Bundle vom System.

* **Status anzeigen**

   Die Liste gibt den aktuellen Status des Bundles an. Klicken Sie auf den Namen eines bestimmten Bundles, um weitere Informationen anzuzeigen.

>[!NOTE]
>
>Nachher **Aktualisieren** Es wird empfohlen, eine **Aktualisieren von Paketen**.

## Komponenten {#components}

Auf der Registerkarte **Komponenten** können die verschiedenen Komponenten aktiviert und/oder deaktiviert werden. Sie können mit einer der beiden folgenden Methoden auf die Registerkarte zugreifen:

* über das Dropdown-Menü:

   **Main >**

* Die URL; Beispiel:

   `http://localhost:4502/system/console/components`

Eine Liste der Komponenten wird angezeigt. Eine Reihe von Symbolen steht zur Verfügung, mit denen Sie die Komponenten aktivieren, deaktivieren oder ggf. Konfigurationsdetails für eine bestimmte Komponente öffnen können.

![screen_shot_2012-02-15at52144pm-1](assets/screen_shot_2012-02-15at52144pm-1.png)

Klicken Sie auf den Namen einer bestimmten Komponente, um weitere Informationen zu deren Status anzuzeigen. Hier können Sie die Komponente auch aktivieren, deaktivieren oder neu laden.

![chlimage_1-62](assets/chlimage_1-62.png)

>[!NOTE]
>
>Das Aktivieren oder Deaktivieren einer Komponente gilt nur, bis AEM/CRX neu gestartet wird.
>
>Der Startstatus wird innerhalb des Komponentendeskriptors definiert, der während der Entwicklung generiert und zum Zeitpunkt der Bundleerstellung im Bundle gespeichert wird.
