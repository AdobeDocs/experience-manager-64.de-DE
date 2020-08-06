---
title: Anfragenanalyse-Skript
seo-title: Anfragenanalyse-Skript
description: Das Anfragenanalyse-Skript vereinfacht die Analyse der access.log-Dateien und erzeugt einen lesbaren Bericht für die spätere Verarbeitung.
seo-description: Das Anfragenanalyse-Skript vereinfacht die Analyse der access.log-Dateien und erzeugt einen lesbaren Bericht für die spätere Verarbeitung.
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
translation-type: tm+mt
source-git-commit: 5da706f22d96b0f5ed8e02febfd64e777d5ce59f
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 47%

---


# Anfragenanalyse-Skript{#request-analysis-script}

## Download {#download}

This script is made to ease the analysis of the `access.log` files producing a readable report for later processing.

[Datei laden](assets/analyse-access.sh)

## Beschreibung {#description}

This script is made to ease the analysis of the `access.log` files producing a readable report for later processing.

Es liefert die Gesamtzahl an Anfragen, einen Vergleich zwischen GET und POST, die Anfrageverteilung über einen Zeitraum hinweg usw.

Die Ausgabe erfolgt in der Markdown-Syntax, daher ist es einfacher, sie mit Werkzeugen wie Pandoc oder dem Anzeigen in einem Browser mit Plug-Ins wie dem Markdown-Viewer in PDFs zu konvertieren.

Er kann einen benutzerdefinierten Pfad analysieren, der in der Befehlszeile angegeben wird.

Ausgehend von dem Kommentar in der Datei, mit dem Sie erfahren, wie Sie sie ausführen:

Analyse CQ `access.log` extrapolating various informations and producing a Markdown output on `stdout`.

## Verwendung {#usage}

`./analyse-access.sh access.log.2013-&ast;`

Sie können zusätzliche benutzerdefinierte Pfade für die Analyse in der Befehlszeile angeben

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

Sie können die Ausgabe durch einfaches Piping speichern

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
