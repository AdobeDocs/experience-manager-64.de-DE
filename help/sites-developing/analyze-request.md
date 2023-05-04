---
title: Anfragenanalyse-Skript
seo-title: Request Analysis Script
description: Das Skript zur Anforderungsanalyse erleichtert die Analyse der access.log-Dateien, die einen lesbaren Bericht zur späteren Verarbeitung erzeugen
seo-description: The request analysis script is made to ease the analysis of the access.log files producing a readable report for later processing
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
exl-id: 8582bbca-c11a-4880-88ba-da22e0301dba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 76%

---

# Anfragenanalyse-Skript{#request-analysis-script}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Download {#download}

Dieses Skript vereinfacht die Analyse der `access.log`-Dateien und erzeugt einen lesbaren Bericht für die spätere Verarbeitung.

[Datei laden](assets/analyse-access.sh)

## Beschreibung {#description}

Dieses Skript vereinfacht die Analyse der `access.log`-Dateien und erzeugt einen lesbaren Bericht für die spätere Verarbeitung.

Es liefert die Gesamtzahl der Anfragen, einen Vergleich zwischen GET und POST, die Anfrageverteilung über einen Zeitraum hinweg usw.

Die Ausgabe erfolgt in Markdown-Syntax. Somit lässt sie sich einfacher mit Tools wie Pandoc in PDF-Dateien umwandeln oder mit einem Plug-in wie Markdown Viewer in einem Browser anzeigen.

Das Skript kann auch einen benutzerdefinierten Pfad analysieren, der in der Befehlszeile angegeben wird.

Im Kommentar in der Datei finden Sie Angaben zur Ausführung:

Analysieren Sie die Datei `access.log` von CQ. Dabei werden verschiedene Daten extrapoliert und eine Markdown-Ausgabe wird auf `stdout` erstellt.

## Nutzung {#usage}

`./analyse-access.sh access.log.2013-&ast;`

Sie können zusätzliche benutzerdefinierte Pfade für die Analyse in der Befehlszeile angeben

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

Sie können die Ausgabe durch einfaches Piping speichern

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
