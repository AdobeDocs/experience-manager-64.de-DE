---
title: Arbeiten mit Protokollen
seo-title: Working with Logs
description: Erfahren Sie, wie Sie AEM beheben können, indem Sie mit Protokollen arbeiten.
seo-description: Learn how to troubleshoot AEM by working with logs.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
exl-id: 201e2b57-17c0-4454-9b0e-026e2c95ac63
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 67%

---

# Arbeiten mit Protokollen{#working-with-logs}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Dieser Abschnitt enthält detaillierte Informationen zu den verfügbaren Protokollen, die Ihnen bei der Fehlerbehebung helfen.

CRX zeichnet detaillierte Protokolle auf. Nachdem Sie Quickstart entpackt und gestartet haben, finden Sie Protokolle an den folgenden Speicherorten:

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Aktivieren der DEBUG-Protokollebene {#activating-the-debug-log-level}

Die standardmäßige Protokollebene ist INFO, DEBUG-Meldungen werden also nicht protokolliert.

Um die DEBUG-Protokollebene zu aktivieren, verwenden Sie den CRX-Explorer, um die

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

Beim Starten von CRX können Sie der Befehlszeile die Option „- v“ (verbose, ausführlich) hinzufügen. Beispiel: &quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

Verwenden Sie die ausführliche Option „verbose“ zur Fehlerbehebung, da damit einige der Schnellstart-Protokollausgaben in der Konsole angezeigt werden.
