---
title: Arbeiten mit Seitenversionen
seo-title: Working with Page Versions
description: Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten.
seo-description: Versioning creates a "snapshot" of a page at a specific point in time.
uuid: b8412922-3dd5-44e3-a7fa-3e357c89a4ff
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: ba74d3fb-063d-4bd6-a551-8e71ad6559e3
exl-id: 407287cf-8096-40ee-971c-006d876ba4e4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1362'
ht-degree: 98%

---

# Arbeiten mit Seitenversionen{#working-with-page-versions}

Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten. Bei der Versionierung sind die folgenden Aktionen verfügbar:

* Erstellen einer Version einer Seite
* Wiederherstellen einer früheren Seitenversion, um z. B. eine Änderung rückgängig zu machen
* Vergleichen der aktuellen Version einer Seite mit einer früheren Version, wobei die Unterschiede in Text und Bildern hervorgehoben sind

## Erstellen einer neuen Version   {#creating-a-new-version}

So erstellen Sie die neue Version einer Seite:

1. Öffnen Sie im Browser die Seite, für die eine neue Version erstellt werden soll.
1. Wählen Sie im Sidekick die Registerkarte **Versionierung** und dann die Unter-Registerkarte **Version erstellen**.

   ![screen_shot_2012-02-14at40259pm](assets/screen_shot_2012-02-14at40259pm.png)

1. Geben Sie einen **Kommentar** ein (optional).
1. Um eine Bezeichnung für die Version anzugeben (optional), klicken Sie auf die Schaltfläche **Mehr >>** und geben Sie unter **Bezeichnung** einen Namen für die Version ein. Wird keine Bezeichnung festgelegt, wird die Version automatisch nummeriert.
1. Klicken Sie auf **Version erstellen**. Auf der Seite wird eine grau hinterlegte Nachricht eingeblendet, z. B.:

   Version 1.2 erstellt für: Hemden.

>[!NOTE]
>
>Eine Version wird automatisch bei Aktivierung einer Seite erstellt.

## Wiederherstellen einer Seitenversion über den Sidekick {#restoring-a-page-version-from-sidekick}

So stellen Sie die frühere Version einer Seite wieder her:

1. Öffnen Sie die Seite, für die Sie eine frühere Version wiederherstellen möchten.
1. Wählen Sie im Sidekick die Registerkarte **Versionierung** und dann die Unter-Registerkarte **Version wiederherstellen** aus.

   ![screen_shot_2012-02-14at42949pm](assets/screen_shot_2012-02-14at42949pm.png)

1. Wählen Sie die Version aus, die Sie wiederherstellen möchten, und wählen Sie **Wiederherstellen** aus.

## Wiederherstellen einer Seitenversion über die Konsole {#restoring-a-page-version-from-the-console}

Sie können diese Methode verwenden, um eine Seitenversion wiederherzustellen. Sie können sie außerdem verwenden, um Seiten wiederherzustellen, die gelöscht wurden.

1. Navigieren Sie in der Konsole **Websites** zu der wiederherzustellenden Seite und wählen Sie diese aus.
1. Wählen Sie im oberen Menü die Optionen **Tools** und dann **Wiederherstellen** aus:

   ![screen_shot_2012-02-08at41326pm](assets/screen_shot_2012-02-08at41326pm.png)

1. Auswählen von &quot;Version wiederherstellen&quot;...** listet Versionen von Dokumenten im aktuellen Ordner auf. Selbst wenn eine Seite gelöscht wurde, wird die letzte Version aufgelistet:

   ![screen_shot_2012-02-08at45743pm](assets/screen_shot_2012-02-08at45743pm.png)

1. Wählen Sie die Version, die Sie wiederherstellen möchten, und wählen Sie **Wiederherstellen**. AEM stellt die Version(en) bzw. den Baum/die Bäume wieder her, die Sie ausgewählt haben.

### Wiederherstellen einer Baumstruktur über die Konsole {#restoring-a-tree-from-the-console}

Sie können diese Methode verwenden, um eine Seitenversion wiederherzustellen. Sie können sie außerdem verwenden, um Seiten wiederherzustellen, die gelöscht wurden.

1. Navigieren Sie in der Konsole **Websites** zu dem wiederherzustellenden Ordner und wählen Sie ihn aus.
1. Wählen Sie im oberen Menü die Optionen **Tools** und dann **Wiederherstellen** aus:
1. Wenn Sie **Baum wiederherstellen...** auswählen, wird ein Dialogfeld geöffnet, in dem Sie den wiederherzustellenden Baum auswählen können:

   ![screen_shot_2012-02-08at45743pm-1](assets/screen_shot_2012-02-08at45743pm-1.png)

1. Klicken Sie auf **Wiederherstellen**. AEM stellt den ausgewählten Baum wieder her.

## Vergleichen mit einer früheren Version {#comparing-with-a-previous-version}

So vergleichen Sie die aktuelle Version einer Seite mit einer früheren Version:

1. Öffnen Sie im Browser die Seite, die mit einer früheren Version verglichen werden soll.
1. Wählen Sie im Sidekick die Registerkarte **Versionierung** und dann die Unterregisterkarte **Version wiederherstellen** aus.

   ![screen_shot_2012-02-14at42949pm-1](assets/screen_shot_2012-02-14at42949pm-1.png)

1. Markieren Sie die Version, die Sie vergleichen möchten, und klicken Sie auf die Schaltfläche **Differenz**.
1. Die Unterschiede zwischen der aktuellen Version und der ausgewählten Version werden wie folgt dargestellt:

   * Gelöschter Text wird rot und durchgestrichen angezeigt.
   * Hinzugefügter Text wird grün und hervorgehoben angezeigt.
   * Bilder, die hinzugefügt oder gelöscht wurden, werden grün umrahmt angezeigt.

   ![chlimage_1-105](assets/chlimage_1-105.png)

1. Wählen Sie im Sidekick die Unter-Registerkarte **Version wiederherstellen** aus und klicken Sie auf **&lt;&lt;Zurück**, um die aktuelle Version anzuzeigen.

## Timewarp {#timewarp}

Timewarp ist eine Funktion, die den ***Veröffentlichungsstatus*** einer Seite zu einer bestimmten Zeit in der Vergangenheit simuliert.

Ziel ist es, Ihnen die Nachverfolgung der veröffentlichten Website zu einem bestimmten Zeitpunkt zu ermöglichen. Hierbei werden die Seitenaktivierungen verwendet, um den Status der Veröffentlichungsumgebung zu ermitteln.

Gehen Sie hierfür wie folgt vor:

* Das System sucht die Seitenversion, die zum gewählten Zeitpunkt aktiv war.
* Dies bedeutet, dass die angezeigte Version *vor* dem in Timewarp ausgewählten Zeitpunkt erstellt/aktiviert wurde.
* Wenn Sie zu einer inzwischen gelöschten Seite navigieren, wird diese ebenfalls wiedergegeben, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.
* Wenn keine veröffentlichte Version gefunden wird, kehrt Timewarp zum aktuellen Status der Seite in der Autorenumgebung zurück (dadurch wird eine Fehler/404-Seite vermieden, die dazu führen würde, dass Sie nicht weiterbrowsen können).

>[!NOTE]
>
>Wenn Versionen aus dem Repository entfernt wurden, kann Timewarp die korrekte Ansicht nicht anzeigen. Außerdem unterscheidet sich die Ansicht von der ursprünglichen Ansicht, wenn Elemente (Code, CSS, Bilder usw.) für die Anzeige der Website geändert wurden, da diese Elemente nicht im Repository versioniert werden.

### Verwenden des Timewarp-Kalenders {#using-the-timewarp-calendar}

Timewarp ist im Sidekick verfügbar.

Die Kalenderversion wird verwendet, wenn Sie einen bestimmten Tag anzeigen möchten.

1. Öffnen Sie die Registerkarte **Versionierung** und klicken Sie auf **Timewarp** (unten im Sidekick). Das folgende Dialogfeld wird angezeigt.

   ![chlimage_1-106](assets/chlimage_1-106.png)

1. Legen Sie über die Datum- und Uhrzeitauswahl das gewünschte Datum und die gewünschte Uhrzeit fest und klicken Sie auf **Los**.

   Timewarp zeigt die Seite in dem Status, in dem sie vor/an dem gewählten Datum veröffentlicht war.

   >[!NOTE]
   >
   >Timewarp funktioniert nur dann vollständig, wenn Sie die Seite zuvor veröffentlicht haben. Andernfalls zeigt Timewarp die aktuelle Seite in der Autorenumgebung an.

   >[!NOTE]
   >
   >Wenn Sie zu einer inzwischen aus dem Repository gelöschten Seite navigieren, wird diese ebenfalls korrekt wiedergegeben, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.

   >[!NOTE]
   >
   >Sie können die alte Version der Seite nicht bearbeiten. Sie kann nur angezeigt werden. Wenn Sie die ältere Version wiederherstellen möchten, müssen Sie dies über [Wiederherstellen](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#restoring-a-page-version-from-sidekick) manuell ausführen.

1. Wenn Sie die Seite wieder verlassen möchten, klicken Sie auf eine der folgenden Optionen:

   * Mit **Timewarp beenden** verlassen Sie Timewarp und kehren zur aktuellen Autorenseite zurück.
   * Mit [Zeitleiste anzeigen](#using-the-timewarp-timeline) zeigen Sie die Zeitleiste an.

   ![chlimage_1-107](assets/chlimage_1-107.png)

### Verwenden der Timewarp-Zeitleiste {#using-the-timewarp-timeline}

Die Zeitleistenversion wird verwendet, wenn Sie eine Übersicht über die Veröffentlichungsaktivitäten auf der Seite anzeigen möchten.

Wenn Sie die Zeitleiste im Dokument anzeigen möchten:

1. Sie können die Zeitleiste wie folgt anzeigen:

   1. Öffnen Sie die Registerkarte **Versionierung** und klicken Sie auf **Timewarp** (unten im Sidekick).
   1. Verwenden Sie das Sidekick-Dialogfeld, das nach [der Verwendung des Timewarp-Kalenders angezeigt wird](#using-the-timewarp-calendar).

1. Klicken Sie auf **Zeitleiste anzeigen**, die Zeitleiste des Dokuments wird angezeigt. Beispiel:

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. Wählen Sie (durch Gedrückthalten und Ziehen) die Zeitleiste aus und verschieben Sie sie, um sich durch die Zeitleiste des Dokuments zu bewegen.

   * Jede Linie steht für eine veröffentlichte Version.

      Wenn eine Seite aktiviert wird, beginnt eine neue Linie. Jedes Mal, wenn das Dokument bearbeitet wird, wird eine neue Farbe angezeigt.

      Im Beispiel unten zeigt die rote Linie an, dass die Seite während des Zeitraums der ursprünglichen grünen Version bearbeitet wurde, und die gelbe Linie zeigt an, dass die Seite während der roten Version bearbeitet wurde usw.
   ![chlimage_1-109](assets/chlimage_1-109.png)

1. Klicken Sie auf:

   1. **Los**, um den Inhalt der veröffentlichten Seite zum ausgewählten Zeitpunkt anzuzeigen.
   1. Wenn der Inhalt angezeigt wird, verwenden Sie **Timewarp beenden**, um Timewarp zu verlassen und zur aktuellen Autorenseite zurückzukehren.

### Timewarp-Beschränkungen

Timewarp versucht, eine Seite zu einem bestimmten Zeitpunkt zu reproduzieren. Aufgrund der Komplexität der kontinuierlichen Bearbeitung von Inhalten in AEM ist dies jedoch nicht immer möglich. Diese Einschränkungen sollten bei der Verwendung von Timewarp beachtet werden.

* **Timewarp funktioniert auf veröffentlichten Seiten**: Timewarp funktioniert nur dann vollständig, wenn Sie die Seite bereits veröffentlicht haben. Andernfalls zeigt Timewarp die aktuelle Seite in der Autorenumgebung.
* **Timewarp verwendet Seitenversionen**: Wenn Sie zu einer inzwischen aus dem Repository gelöschten Seite navigieren, wird diese ebenfalls korrekt wiedergegeben, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.
* **Entfernte Versionen wirken sich auf Timewarp**: Wenn Versionen aus dem Repository entfernt wurden, kann Timewarp die korrekte Ansicht nicht anzeigen.
* **Timewarp ist schreibgeschützt**: Sie können die alte Version der Seite nicht bearbeiten. Sie kann nur angezeigt werden. Wenn Sie die ältere Version wiederherstellen möchten, müssen Sie dies über Wiederherstellen manuell ausführen.
* **Timewarp basiert nur auf dem Seiteninhalt**: Die Ansicht unterscheidet sich von der ursprünglichen Ansicht, wenn Elemente (Code, CSS, Assets/Bilder usw.) für die Anzeige der Website geändert wurden, da diese Elemente nicht im Repository versioniert werden.

>[!CAUTION]
>
>Timewarp wurde als Tool entwickelt, das Autoren beim Verstehen und Erstellen ihres Inhalts unterstützen kann. Es ist nicht als Prüfprotokoll oder zu rechtlichen Zwecken gedacht.
