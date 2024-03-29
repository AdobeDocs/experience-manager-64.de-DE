---
title: Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor
seo-title: Assessing the Upgrade Complexity with the Pattern Detector
description: Erfahren Sie, wie Sie mit dem Musterdetektor die Komplexität Ihres Upgrades bewerten können.
seo-description: Learn how to use the Pattern Detector to assess the complexity of your upgrade.
uuid: 4fcfdb16-3183-442a-aa5b-5f9c4fb7e091
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 8cdcfd3a-7003-4cce-97f4-da7a1a887d1b
feature: Upgrading
exl-id: 375e202c-21d4-41f1-a2d5-592ac95c8f25
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 37%

---

# Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor {#assessing-the-upgrade-complexity-with-the-pattern-detector}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Überblick {#overview}

Mit dieser Funktion können Sie vorhandene AEM-Instanzen auf ihre Aktualisierbarkeit überprüfen, indem Sie Muster erkennen, die verwendet werden und Folgendes tun:

1. gegen bestimmte Regeln verstoßen und Bereiche betreffen, die durch das Upgrade überschrieben werden
1. Verwenden Sie eine AEM 6.x-Funktion oder eine API, die in AEM 6.4 nicht abwärtskompatibel ist und nach der Aktualisierung möglicherweise beschädigt werden kann.

Dies könnte als Bewertung der Entwicklungsbemühungen dienen, die mit der Aktualisierung auf AEM 6.4 verbunden sind.

## Einrichtung {#how-to-set-up}

Der Musterdetektor wird als separates [Paket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/compatpack/pd-all-aem65) veröffentlicht, das mit allen Quell-AEM-Versionen von 6.1 bis 6.5 funktioniert, die auf AEM 6.5 aktualisiert werden sollen. Sie kann mithilfe der [Package Manager](https://helpx.adobe.com/de/experience-manager/6-5/sites/administering/using/package-manager.html).

## Verwendung {#how-to-use}

>[!NOTE]
>
>Der Musterdetektor kann in jeder beliebigen Umgebung, einschließlich lokaler Entwicklungsinstanzen, ausgeführt werden. Um jedoch
>
>* die Erkennungsrate erhöhen
>* vermeiden Sie jede Verlangsamung bei geschäftskritischen Instanzen.\
   >Gleichzeitig wird die Ausführung in **Staging-Umgebungen** empfohlen, die hinsichtlich Benutzerapplikationen, Inhalt und Konfigurationen den Produktionsumgebungen möglichst stark ähneln.


Sie haben verschiedene Möglichkeiten, das Ergebnis des Musterdetektors zu prüfen: 

* **Über die Felix Inventory-Konsole:** 

1. Navigieren Sie zur AEM Web-Konsole, indem Sie zu: https://<i></i>serveraddress:serverport/system/console/configMgr
1. Wählen Sie **Status - Musterdetektor** aus, wie im Bild unten dargestellt:

   ![screen-shot-2018-2-5pattern-detektor](assets/screenshot-2018-2-5pattern-detector.png)

* **Über eine auf reaktivem Text basierende oder die reguläre JSON-Schnittstelle** 

* **Über die Oberfläche für reaktive JSON-Zeilen**, das in jeder Zeile ein separates JSON-Dokument generiert.

Beide Methoden werden im Folgenden beschrieben:

## Reaktive Schnittstelle {#reactive-interface}

Die reaktive Oberfläche ermöglicht die Verarbeitung des Verstoßberichts, sobald ein Verdacht festgestellt wird.

Die Ausgabe ist derzeit unter 2 URLs verfügbar:

1. Nur-Text-Schnittstelle 
1. JSON-Benutzeroberfläche

## Umgang mit der Textschnittstelle {#handling-the-plain-text-interface}

Die Informationen in der Ausgabe werden als eine Reihe von Ereigniseinträgen formatiert. Es gibt zwei Kanäle - einen für Veröffentlichungsverletzungen und einen für die Veröffentlichung des aktuellen Fortschritts.

Sie können mithilfe der folgenden Befehle abgerufen werden:

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep SUSPICION
```

Die Ausgabe sieht wie folgt aus:

```
2018-02-13T14:18:32.071+01:00 [SUSPICION] The pattern=ECU/extraneous.content.usage was found by detector=ContentAccessDetector with id=a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f message="Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid". More info at=https://www.adobe.com/go/aem6_EC
```

Der Fortschritt kann mit dem Befehl `grep` gefiltert werden:

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep PROGRESS
```

Dies führt zur folgenden Ausgabe:

```
2018-02-13T14:19:26.909+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.4), analysed=45780/16 MB items, found=0 suspicions so far in period=PT5.005S (throughput=34667 items/sec)
2018-02-13T14:19:31.904+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.4), analysed=106050/39 MB items, found=0 suspicions so far in period=PT10S (throughput=23378 items/sec)
2018-02-13T14:19:35.685+01:00 [PROGRESS] Finished in period=PT13.782
```

## Umgang mit der JSON-Oberfläche {#handling-the-json-interface}

Auf ähnliche Weise kann JSON mit der [jq-Tool](https://stedolan.github.io/jq/) sobald sie veröffentlicht wurde.

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == true)'
```

Mit der Ausgabe:

```
{
  "timestamp": "2018-02-13T14:20:18.894+01:00",
  "suspicion": true,
  "pattern": {
    "code": "ECU",
    "type": "extraneous.content.usage",
    "detective": "ContentAccessDetector",
    "moreInfo": "https://www.adobe.com/go/aem6_ECU"
  },
  "item": {
    "id": "a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f",
    "message": "Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid"
  }
}
```

Der Fortschritt wird alle 5 Sekunden gemeldet und kann abgerufen werden, indem andere Nachrichten ausgeschlossen werden, die als verdächtig markiert sind:

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == false)'
```

Mit der Ausgabe:

```
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:17.279+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.4"
    ]
  },
  "state": {
    "itemsAnalysed": 57209,
    "itemsAnalysedSize": "26 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT5.003S",
    "elapsedTimeMilliseconds": 5003,
    "itemsPerSecond": 36965
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:22.276+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.4"
    ]
  },
  "state": {
    "itemsAnalysed": 113194,
    "itemsAnalysedSize": "46 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT10S",
    "elapsedTimeMilliseconds": 10000,
    "itemsPerSecond": 24092
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:25.762+01:00",
  "type": "FINISHED",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.4"
    ]
  },
  "state": {
    "itemsAnalysed": 140744,
    "itemsAnalysedSize": "63 MB",
    "suspicionsFound": 1
  },
  "progress": {
    "elapsedTime": "PT13.486S",
    "elapsedTimeMilliseconds": 13486,
    "itemsPerSecond": 19907
  }
}
{
  "suspicion": false,
  "type": "SUMMARY",
  "suspicionsFound": 1,
  "totalTime": "PT13.487S"
}
```

>[!NOTE]
>
>Es empfiehlt sich, die gesamte Ausgabe aus Curl in der Datei zu speichern und diese dann über `jq` oder `grep` zu verarbeiten, um einen Informationstyp zu filtern.

## Erkennungsbereich {#scope}

Der Musterdetektor ermöglicht derzeit die Überprüfung von:

* Die Exporte und Importe von OSGi-Bundles stimmen nicht überein
* Überschreibungen von Sling-Ressourcentypen und -Supertypen (mit Inhaltsüberlagerungen für Suchpfade)
* Definitionen der Oak-Indizes (Kompatibilität)
* VLT-Pakete (Überverwendung)
* rep:User nodes-Kompatibilität (im Kontext der OAuth-Konfiguration)
