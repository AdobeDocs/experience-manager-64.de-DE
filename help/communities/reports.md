---
title: Berichte-Konsole
seo-title: Berichte-Konsole
description: Erfahren Sie, wie Sie auf Berichte zugreifen können
seo-description: Erfahren Sie, wie Sie auf Berichte zugreifen können
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 8%

---


# Berichte-Konsole {#reports-console}

## Überblick {#overview}

Für AEM Communities gibt es verschiedene Berichte, auf die von der Autorendatei aus auf verschiedene Weise zugegriffen werden kann.

Die verschiedenen Berichte sind im Allgemeinen:

* [Bericht](#assignments-report)  &quot;Zuweisungen&quot;- für eine  [Community](overview.md#enablement-community), die Informationen über den Fortschritt der Lernenden bei ihren Zuweisungen enthält, einschließlich eines zugehörigen Ergebnisses bei der Implementierung des SCORM-Standards
* [Ansichten-Bericht](#views-report)  - enthält eine Übersicht über die Ansichten von Inhalten von Community-Mitgliedern und Site-Besuchern für jede Community-Site
* [Bericht](#posts-report)  &quot;Beiträge&quot;- enthält ein Diagramm der verschiedenen Arten von Beiträgen von Mitgliedern der Community zu jeder Community-Site.

Wenn [Adobe Analytics aktiviert ist](sites-console.md#analytics), enthalten Berichte die Anzahl der Ansichten, Wiedergaben, Kommentare und Bewertungen für jede Aktivierungsressource im Zeitverlauf.

Tabuläre Berichte können zur anschließenden Verarbeitung im .csv-Format exportiert werden.

## Berichte-Konsolen {#reporting-consoles}

### Berichte für Community-Sites {#reports-for-community-sites}

* Aus globaler Navigation: **[!UICONTROL Navigation > Communities > Berichte]**
* Wählen Sie aus
   * **[!UICONTROL Zuweisungsbericht]**
      * Bericht für ausgewählte Community-Site, Benutzer oder -Gruppe und Zuweisen erstellen
   * **[!UICONTROL Post-Bericht]**
      * Bericht für ausgewählte Community-Site, Inhaltstyp und Zeitraum erstellen
   * **[!UICONTROL Ansichtsbericht]**
      * Bericht für ausgewählte Community-Site, Inhaltstyp und Zeitraum erstellen
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Berichte zu Aktivierungsressourcen und Lernpfaden {#reports-for-enablement-resources-and-learning-paths}

* Aus globaler Navigation: **[!UICONTROL Navigation > Communities > Ressourcen]**
* Eine vorhandene Community-Site für die Aktivierung auswählen
   * Klicken Sie auf das Symbol **[!UICONTROL Bericht]**, um Berichte zu erstellen, die alle Aktivierungsressourcen abdecken.
   * Auswählen eines Lernpfads für die Aktivierung
   * Klicken Sie auf das Symbol **[!UICONTROL Bericht]**, um Berichte für
      * Die enthaltenen Aktivierungsressourcen
      * Dem Lernpfad zugewiesene Lernende
* Diese Berichte bieten:
   * Tabellendaten als CSV herunterladen
      * Identifizieren des Lernenden
      * ihr Status
      * Ob zugewiesen oder über Katalog aufgerufen
      * Anzahl der Kommentare
      * Sternbewertung

Weitere Informationen finden Sie im Abschnitt [Berichte](resources.md#report) der Ressourcenkonsole.

## Zuweisungsbericht {#assignments-report}

Die Konsole &quot;Zuweisungen&quot;ermöglicht das Filtern von Berichten nach der Aktivierung der Community-Site, Benutzern oder Gruppen und der Zuweisung.

Der Bericht enthält Informationen über ihre Fortschritte sowie Kommentare und Bewertungen.

![chlimage_1-157](assets/chlimage_1-157.png)

Wählen Sie die Kriterien für den Bericht aus:

* ****
SiteWählen Sie eine Community-Site für die Aktivierung aus
* **[!UICONTROL Benutzer oder Gruppe]**
   * Benutzer auswählen, um einen Bericht für einen Lernenden zu erstellen
   * Gruppe auswählen, um einen Bericht für eine Gruppe Lernender zu erstellen
Der Tunneldienst greift über die Umgebung zur Veröffentlichung auf Mitglieder und Mitgliedergruppen zu
* **[!UICONTROL Zuweisung]**
Wählen Sie aus den den ausgewählten Lernenden zugewiesenen Ressourcen aus

Wählen Sie **[!UICONTROL Generate]**, um den Bericht zu erstellen:

![chlimage_1-158](assets/chlimage_1-158.png)

## Ansichtsbericht {#views-report}

Die Konsole &quot;Ansichten&quot;ermöglicht die Erstellung von Berichten auf Ansichten durch Community-Funktionen für einen bestimmten Zeitraum.

![chlimage_1-159](assets/chlimage_1-159.png)

Wählen Sie die Kriterien für den Bericht aus:

* ****
SiteWählen Sie eine Community-Site
* **[!UICONTROL Content]**
Typekann &quot;Alle Inhalte&quot;auswählen oder eine der Funktionen auf der Site auswählen
* Zeitrahmen
Wählen Sie eine der folgenden Optionen:
   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **[!UICONTROL Generate]**, um den Bericht zu erstellen:

![chlimage_1-160](assets/chlimage_1-160.png)

## Post-Bericht {#posts-report}

In der Konsole &quot;Beiträge&quot;können Berichte für die Anzahl der Beiträge zu Community-Funktionen für einen bestimmten Zeitraum generiert werden.

![chlimage_1-161](assets/chlimage_1-161.png)

Wählen Sie die Kriterien für den Bericht aus:

* ****
SiteWählen Sie eine Community-Site
* **[!UICONTROL Content]**
Typekann &quot;Alle Inhalte&quot;auswählen oder eine der Funktionen auf der Site auswählen
* Zeitrahmen
Wählen Sie eine der folgenden Optionen:
   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Wählen Sie **[!UICONTROL Generate]**, um den Bericht zu erstellen:

![chlimage_1-162](assets/chlimage_1-162.png)

## Fehlerbehebung {#troubleshooting}

### Keine Community-Sites aufgelistet {#no-community-sites-listed}

Wenn keine Community-Sites aufgelistet sind, stellen Sie sicher, dass Adobe Analytics für eine Site aktiviert wurde. Wenn Sie Berichte zu Zuweisungen auswählen, stellen Sie sicher, dass sich die Zuweisungsfunktion in der Struktur der Community-Site befindet.
