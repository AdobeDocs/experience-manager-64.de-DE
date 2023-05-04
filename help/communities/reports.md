---
title: Berichtkonsole
seo-title: Reports Console
description: Erfahren Sie, wie Sie auf Berichte zugreifen können
seo-description: Learn how to access reports
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
role: Admin
exl-id: 766711ea-f3d3-49ab-8346-4e4477c261bd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 8%

---

# Berichtkonsole {#reports-console}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Für AEM Communities gibt es verschiedene Berichte, auf die über die Autorenumgebung auf verschiedene Weise zugegriffen werden kann.

Die verschiedenen Berichte sind im Allgemeinen:

* [Zuweisungsbericht](#assignments-report) - für [Aktivierungs-Community](overview.md#enablement-community)bietet einen Überblick über den Fortschritt der Lernenden bei ihrer Zuweisung, einschließlich eines zugehörigen Punkts bei der Implementierung des SCORM-Standards
* [Bericht &quot;Ansichten&quot;](#views-report) - bietet ein Diagramm mit den Inhalten von Community-Mitgliedern und Site-Besuchern für jede Community-Site.
* [Beitragsbericht](#posts-report) - bietet ein Diagramm mit verschiedenen Beiträgen von Community-Mitgliedern zu jeder Community-Site.

Wann [Adobe Analytics ist aktiviert](sites-console.md#analytics)enthalten, enthalten Berichte die Anzahl der Ansichten, Wiedergaben, Kommentare und Bewertungen für jede Aktivierungsressource im Laufe der Zeit.

Tabellarische Berichte können zur nachfolgenden Verarbeitung im CSV-Format exportiert werden.

## Reporting-Konsolen {#reporting-consoles}

### Berichte für Community-Sites {#reports-for-community-sites}

* Über die globale Navigation: **[!UICONTROL Navigation > Communities > Berichte]**
* Wählen Sie aus
   * **[!UICONTROL Zuweisungsbericht]**
      * Erstellen Sie einen Bericht für die ausgewählte Community-Site, den ausgewählten Benutzer oder die Gruppe und die Zuweisung
   * **[!UICONTROL Post-Bericht]**
      * Erstellen Sie einen Bericht für die ausgewählte Community-Site, den Inhaltstyp und den Zeitraum
   * **[!UICONTROL Ansichtsbericht]**
      * Erstellen Sie einen Bericht für die ausgewählte Community-Site, den Inhaltstyp und den Zeitraum
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Berichte für Aktivierungsressourcen und Lernpfade {#reports-for-enablement-resources-and-learning-paths}

* Über die globale Navigation: **[!UICONTROL Navigation > Communities > Ressourcen]**
* Vorhandene Aktivierungs-Community-Site auswählen
   * Auswählen **[!UICONTROL Bericht]** -Symbol zum Generieren von Berichten, die alle Aktivierungsressourcen abdecken
   * Aktivierungs-Lernpfad auswählen
   * Auswählen **[!UICONTROL Bericht]** Symbol zum Generieren von Berichten für
      * Die enthaltenen Aktivierungsressourcen
      * Den Lernpfaden zugewiesene Lernende
* Diese Berichte bieten Folgendes:
   * Tabellendaten, als CSV heruntergeladen
      * Identifizieren von Lernenden
      * Ihr Status
      * Ob zugewiesen oder über Katalog aufgerufen
      * Anzahl der abgegebenen Kommentare
      * Sternbewertung

Weitere Informationen finden Sie unter [Berichtabschnitt](resources.md#report) in der Ressourcenkonsole.

## Zuweisungsbericht {#assignments-report}

In der Konsole &quot;Zuweisungen&quot;können Berichte nach der Aktivierungs-Community-Site, Benutzern oder Gruppen und der Zuweisung gefiltert werden.

Der Bericht enthält Informationen über ihren Fortschritt sowie etwaige Kommentare oder Bewertungen.

![chlimage_1-157](assets/chlimage_1-157.png)

Wählen Sie die Kriterien für den Bericht aus:

* **[!UICONTROL Site]**
Auswahl einer Community-Site für die Aktivierung
* **[!UICONTROL Benutzer oder Gruppe]**
   * Wählen Sie Benutzer aus, um einen Bericht für einen Lernenden zu erstellen
   * Gruppe auswählen , um einen Bericht für eine Gruppe von Lernenden zu erstellen Der Tunneldienst greift in der Veröffentlichungsumgebung auf Mitglieder und Mitgliedergruppen zu
* **[!UICONTROL Zuweisung]**
Wählen Sie aus den den ausgewählten Lernenden zugewiesenen Aktivierungsressourcen aus.

Auswählen **[!UICONTROL Erzeugen]** , um den Bericht zu erstellen:

![chlimage_1-158](assets/chlimage_1-158.png)

## Ansichtsbericht {#views-report}

Mit der Konsole &quot;Ansichten&quot;können Berichte zu Seitenansichten von Community-Funktionen für einen bestimmten Zeitraum generiert werden.

![chlimage_1-159](assets/chlimage_1-159.png)

Wählen Sie die Kriterien für den Bericht aus:

* **[!UICONTROL Site]**
Community-Site auswählen
* **[!UICONTROL Content-Typ]**
Sie können Alle Inhalte auswählen oder eine der auf der Site vorhandenen Funktionen auswählen
* Zeitrahmen Wählen Sie einen der folgenden Optionen aus:
   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Auswählen **[!UICONTROL Erzeugen]** , um den Bericht zu erstellen:

![chlimage_1-160](assets/chlimage_1-160.png)

## Post-Bericht {#posts-report}

Die Konsole Beiträge ermöglicht die Erstellung von Berichten über die Anzahl der Beiträge zu Community-Funktionen für einen bestimmten Zeitraum.

![chlimage_1-161](assets/chlimage_1-161.png)

Wählen Sie die Kriterien für den Bericht aus:

* **[!UICONTROL Site]**
Community-Site auswählen
* **[!UICONTROL Content-Typ]**
Sie können Alle Inhalte auswählen oder eine der auf der Site vorhandenen Funktionen auswählen
* Zeitrahmen Wählen Sie einen der folgenden Optionen aus:
   * Letzte 7 Tage
   * Letzte 30 Tage
   * Letzte 90 Tage
   * Letztes Jahr

Auswählen **[!UICONTROL Erzeugen]** , um den Bericht zu erstellen:

![chlimage_1-162](assets/chlimage_1-162.png)

## Fehlerbehebung {#troubleshooting}

### Keine Community-Sites aufgeführt {#no-community-sites-listed}

Wenn keine Community-Sites aufgelistet sind, stellen Sie sicher, dass Adobe Analytics für eine Site aktiviert wurde. Stellen Sie bei der Auswahl von Berichten zu Zuweisungen sicher, dass sich die Zuweisungsfunktion in der Struktur der Community-Site befindet.
