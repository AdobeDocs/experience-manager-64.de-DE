---
title: Arbeiten mit Seitenversionen
seo-title: Working with Page Versions
description: Erstellen, Vergleichen und Wiederherstellen von Versionen einer Seite
seo-description: Create, compare, and restore versions of a page
uuid: b0328431-c2cf-48f4-b358-261238338241
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: fa331c03-5587-452d-ab96-ac2926ae0da3
exl-id: 2df7c08f-db17-4666-ba39-e81cc2e656d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 65%

---

# Arbeiten mit Seitenversionen{#working-with-page-versions}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten. Bei der Versionierung können Sie die folgenden Aktionen durchführen:

* Erstellen Sie eine Version einer Seite.
* Stellen Sie eine Seite auf eine frühere Version zurück, um eine Änderung rückgängig zu machen, die Sie beispielsweise an einer Seite vorgenommen haben.
* Vergleichen Sie die aktuelle Version einer Seite mit einer früheren Version mit Unterschieden in Text und Bildern, die hervorgehoben sind.

## Erstellen einer neuen Version   {#creating-a-new-version}

Sie können eine Version Ihrer Ressource folgendermaßen erstellen:

* über die [Zeitleiste](#creating-a-new-version-timeline)
* die [Erstellen](#creating-a-new-version-create-with-a-selected-resource) Option (wenn eine Ressource ausgewählt ist)

### Erstellen einer neuen Version – Zeitleiste {#creating-a-new-version-timeline}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die Spalte **Zeitleiste**.
1. Klicken/tippen Sie auf den Pfeil neben dem Kommentarfeld, um die Optionen anzuzeigen:

   ![screen_shot_2018-03-21at155035](assets/screen_shot_2018-03-21at155035.png)

1. Auswählen **Als Version speichern**.
1. Geben Sie eine **Beschriftung** an und ggf. einen **Kommentar** ein.

   ![chlimage_1-398](assets/chlimage_1-398.png)

1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

   Die Informationen in der Zeitleiste werden entsprechend der neuen Version aktualisiert.

### Erstellen einer neuen Version – Erstellen mit einer ausgewählten Ressource {#creating-a-new-version-create-with-a-selected-resource}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Wählen Sie die **Erstellen** in der Symbolleiste.
1. Das Dialogfeld wird geöffnet. Sie können eine **Beschriftung** angeben und ggf. einen **Kommentar** eingeben:

   ![screen_shot_2012-02-15at105050am](assets/screen_shot_2012-02-15at105050am.png)

1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

   Die Informationen in der Zeitleiste werden entsprechend der neuen Version aktualisiert.

## Wiederherstellen einer früheren Seitenversion {#reverting-to-a-page-version}

Nachdem eine Version erstellt wurde, können Sie diese Version bei Bedarf wiederherstellen.

>[!NOTE]
>
>Wenn eine Seite wiederhergestellt wird, gehört die erstellte Version zu einem neuen Zweig.
>
>Beispiel:
>
>* Erstellen Sie Versionen einer beliebigen Seite.
>* Die anfänglichen Etiketten und Versionsknotennamen lauten 1.0, 1.1, 1.2 usw.
>* die erste Version wiederherstellen; d. h. 1.0.
>* Erstellen Sie erneut neue Versionen.
>* Die erzeugten Beschriftungen und Knotennamen lauten jetzt 1.0.0, 1.0.1, 1.0.2 usw.
>


So stellen Sie eine frühere Version wieder her:

1. Navigieren Sie zu der Seite, für die Sie eine frühere Version wiederherstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus. Die Seitenversionen für die ausgewählte Seite werden aufgelistet.
1. Wählen Sie die Version, die Sie wiederherstellen möchten. Die möglichen Optionen werden angezeigt:

   ![screen_shot_2018-03-21at155246](assets/screen_shot_2018-03-21at155246.png)

1. Wählen Sie **Auf diese Version zurück**. Die ausgewählte Version wird wiederhergestellt und die Informationen in der Zeitleiste werden aktualisiert.

## Vorschau einer Version   {#previewing-a-version}

Sie können eine Vorschau einer bestimmten Version anzeigen:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgeführt. Wählen Sie die Version aus, die Sie in der Vorschau anzeigen möchten:

   ![screen_shot_2018-03-21at155330](assets/screen_shot_2018-03-21at155330.png)

1. Wählen Sie **Vorschau**. Die Seite wird in einer neuen Registerkarte angezeigt.

   >[!CAUTION]
   >
   >Wenn eine Seite verschoben wurde, können Sie keine Vorschau mehr für Versionen anzeigen, die vor dem Verschieben vorgenommen wurden.
   >
   >Wenn Probleme bei der Vorschau auftreten, überprüfen Sie in der [Zeitleiste](/help/sites-authoring/basic-handling.md#timeline) der Seite, ob die Seite verschoben wurde.

## Vergleichen einer Version mit der aktuellen Seite {#comparing-a-version-with-current-page}

So vergleichen Sie eine frühere Version mit der aktuellen Seite:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgeführt. Wählen Sie die Version aus, die Sie vergleichen möchten:

   ![screen_shot_2018-03-21at155330](assets/screen_shot_2018-03-21at155330.png)

1. Auswählen **Mit aktueller Version vergleichen**. Die [Seitenvergleich](/help/sites-authoring/page-diff.md) öffnet und zeigt die Unterschiede an.

## Timewarp {#timewarp}

Timewarp ist eine Funktion, die den *Veröffentlichungsstatus* einer Seite zu einer bestimmten Zeit in der Vergangenheit simuliert.

Ziel ist es, Ihnen die Nachverfolgung der veröffentlichten Website zu einem bestimmten Zeitpunkt zu ermöglichen. Hierbei werden die Seitenversionen verwendet, um den Status der Veröffentlichungsumgebung zu ermitteln.

Gehen Sie hierfür wie folgt vor:

* Das System sucht nach der Seitenversion, die zum ausgewählten Zeitpunkt aktiv war.
* Dies bedeutet, dass die angezeigte Version erstellt/aktiviert wurde *before* den in Timewarp ausgewählten Zeitpunkt.
* Wenn Sie zu einer Seite navigieren, die gelöscht wurde, wird dies ebenfalls gerendert - solange die alten Versionen der Seite noch im Repository verfügbar sind.
* Wenn keine veröffentlichte Version gefunden wird, kehrt Timewarp zum aktuellen Status der Seite in der Autorenumgebung zurück (dadurch wird eine Fehler-/404-Seite vermieden, die dazu führen würde, dass Sie nicht weiter browsen können).

### Verwenden von Timewarp {#using-timewarp}

Timewarp ist eine [mode](/help/sites-authoring/author-environment-tools.md#page-modes) des Seiteneditors. Um es zu starten, wechseln Sie es einfach wie jeder andere Modus.

1. Starten Sie den Editor für die Seite, auf der Sie Timewarp starten möchten, und wählen Sie dann **Timewarp** in der Modusauswahl.

   ![screen_shot_2018-03-21at155416](assets/screen_shot_2018-03-21at155416.png)

1. Legen Sie im Dialogfeld ein Datum und eine Uhrzeit fest und tippen/klicken Sie auf **Datum einstellen**. Wenn Sie keine Zeit auswählen, wird die aktuelle Zeit standardmäßig eingestellt.

   ![screen_shot_2018-03-21at155513](assets/screen_shot_2018-03-21at155513.png)

1. Die Seite wird basierend auf dem festgelegten Datum angezeigt. Der Timewarp-Modus wird über die blaue Statusleiste am oberen Rand des Fensters angezeigt. Verwenden Sie die Links in der Statusleiste, um ein neues Zieldatum auszuwählen oder den Timewarp-Modus zu beenden.

   ![screen_shot_2018-03-21at155544](assets/screen_shot_2018-03-21at155544.png)

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
