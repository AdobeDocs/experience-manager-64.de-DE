---
title: Arbeiten mit Protokollen
seo-title: Arbeiten mit Protokollen
description: Erfahren Sie, wie Sie anhand von Protokollen eine Fehlerbehebung für AEM durchführen können.
seo-description: Erfahren Sie, wie Sie anhand von Protokollen eine Fehlerbehebung für AEM durchführen können.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 93%

---


# Arbeiten mit Protokollen{#working-with-logs}

Dieser Abschnitt beinhaltet ausführliche Informationen zu den zur Fehlerbehebung verfügbaren Protokollen.

CRX zeichnet detaillierte Protokolle auf. Nach dem Entpacken und Aufrufen der Schnellstart-Funktion finden Sie Protokolle an den folgenden Speicherorten:

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Aktivieren der DEBUG-Protokollebene {#activating-the-debug-log-level}

Die standardmäßige Protokollebene ist INFO, DEBUG-Meldungen werden also nicht protokolliert.

Zum Aktivieren der DEBUG-Protokollebene stellen Sie mit dem CRX-Explorer die Eigenschaft

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

auf „debug“ ein. Lassen Sie die DEBUG-Protokollebene nicht länger als notwendig aktiviert, da hierdurch zahlreiche Protokolle generiert werden.

Eine Zeile in der Debugdatei beginnt gewöhnlich mit DEBUG, gefolgt von der Angabe der Protokollebene, der Aktion des Installationsprogramms und der Protokollmeldung. Beispiel:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

Die Protokollebenen lauten wie folgt:

| 0 | Schwerwiegender Fehler | Die Aktion ist fehlgeschlagen und das Installationsprogramm kann nicht fortgesetzt werden. |
|---|---|---|
| 1 | Fehler | Die Aktion ist fehlgeschlagen. Die Installation wird fortgesetzt, aber ein CRX-Teil wurde nicht ordnungsgemäß installiert und funktioniert daher nicht. |
| 2 | Warnung | Die Aktion war erfolgreich, stieß aber auf Probleme. CRX funktioniert ggf. nicht ordnungsgemäß. |
| 3 | Informationen | Die Aktion war erfolgreich. |

## Ausführliche Option „verbose“ zur Fehlerbehebung {#verbose-option-used-for-troubleshooting}

Beim Beginn von CRX können Sie die Option -v (verbose) wie folgt zur Befehlszeile hinzufügen: &quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

Verwenden Sie die ausführliche Option „verbose“ zur Fehlerbehebung, da damit einige der Schnellstart-Protokollausgaben in der Konsole angezeigt werden.
