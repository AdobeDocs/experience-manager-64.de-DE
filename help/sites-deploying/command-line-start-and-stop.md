---
title: Start und Stopp über die Befehlszeile
seo-title: Command Line Start and Stop
description: Erfahren Sie, wie Sie AEM über die Befehlszeile starten und beenden.
seo-description: Learn how to start and stop AEM from the command line.
uuid: 585f071c-2286-4a2c-af07-404bf298cba8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 9333ff84-f624-4cfa-a9e4-c5e3882171ff
exl-id: 9d2682c2-6360-402e-a020-0021f5051a2d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 49%

---

# Start und Stopp über die Befehlszeile{#command-line-start-and-stop}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Starten von Adobe Experience Manager über die Befehlszeile {#starting-adobe-experience-manager-from-the-command-line}

Das Skript `start` befindet sich im Verzeichnis *&lt;cq-installation>/bin*. Sowohl die Unix- als auch die Windows-Version wird bereitgestellt. Das Skript startet die in *&lt;cq-installation>* Verzeichnis.

Diese beiden Versionen unterstützen eine Liste von Umgebungsvariablen, die zum Starten und Optimieren der AEM-Instanz verwendet werden können.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Umgebungsvariable </strong></td> 
   <td><strong>Beschreibung </strong></td> 
  </tr> 
  <tr> 
   <td>CQ_PORT</td> 
   <td>Für „stop“- und „status“-Skripts verwendeter TCP-Port<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_HOST</td> 
   <td>Hostname<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_INTERFACE</td> 
   <td>Schnittstelle, an der dieser Server lauschen sollte<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_RUNMODE</td> 
   <td>Durch Komma(s) getrennte Ausführungsmodi<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_JARFILE</td> 
   <td>Name der JAR-Datei<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_USE_JAAS</td> 
   <td>Verwendung von JAAS (wenn „true“ vorliegt)<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_JAAS_CONFIG</td> 
   <td>Pfad der JAAS-Konfiguration<br /> </td> 
  </tr> 
  <tr> 
   <td>CQ_JVM_OPTS</td> 
   <td>JVM-Standardoptionen<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!CAUTION]
>
>Beachten Sie, dass einige Ausführungsmodi, darunter Autoren- und Veröffentlichungsmodus, vor dem ersten Start der AEM festgelegt werden müssen und danach nicht mehr geändert werden können. Bevor Sie eine AEM-Instanz einrichten, die in der Produktion verwendet werden soll, lesen Sie bitte den Abschnitt [Dokumentation zu Ausführungsmodi](/help/sites-deploying/configure-runmodes.md) für Details.

### Skriptbeispiel für Windows-Plattform start.bat {#windows-platform-start-bat-script-example}

```shell
SET CQ_PORT=1234 & ./start.bat
```

### Beispiel eines Unix-Plattform-Startskripts {#unix-platform-start-script-example}

```shell
CQ_PORT=1234 ./start
```

>[!NOTE]
>
>Über das Skript „start“ wird der im Ordner *the &lt;cq-installation>/app* installierte AEM-Schnellstart gestartet.

## Beenden von Adobe Experience Manager {#stopping-adobe-experience-manager}

Um AEM zu beenden, führen Sie einen der folgenden Schritte aus:

* Je nach verwendeter Plattform:

   * Drücken Sie **Strg + C**, um den Server herunterzufahren, wenn Sie AEM über ein Skript oder die Befehlszeile gestartet haben.
   * Wenn Sie das Skript start unter UNIX verwendet haben, müssen Sie das Skript stop verwenden, um AEM anzuhalten.

* Wenn Sie AEM durch Doppelklicken auf die JAR-Datei gestartet haben, klicken Sie auf die **on** Schaltfläche im Startfenster (die Schaltfläche ändert sich in **Aus**), um den Server herunterzufahren.

   ![chlimage_1-63](assets/chlimage_1-63.png)

## Adobe Experience Manager über die Befehlszeile anhalten {#stopping-adobe-experience-manager-from-the-command-line}

Das Skript `stop` befindet sich im Verzeichnis *&lt;cq-installation>/bin*. Sowohl die Unix- als auch die Windows-Version wird bereitgestellt. Das Skript hält die im Verzeichnis *&lt;cq-installation>* installierte aktive Instanz an.

### Beispiel für ein Unix-Plattform-Stopp-Skript {#unix-platform-stop-script-example}

```shell
./stop
```

### Skriptbeispiel für das Windows-Plattform-stop.bat {#windows-platform-stop-bat-script-example}

```shell
./stop.bat
```

Wenn Sie das Repository nur vorkonfigurieren möchten (ohne es neu zu lokalisieren), müssen Sie nur Folgendes tun:

* `repository.xml` am erforderlichen Speicherort extrahieren

* `repository.xml` nach Bedarf aktualisieren

* `bootstrap.properties` erstellen und `repository.config` definieren

Zur Erinnerung: Führen Sie diese Aktionen vor der tatsächlichen Installation aus.
