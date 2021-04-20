---
title: Auflösen von Dateiabhängigkeiten
seo-title: Auflösen von Dateiabhängigkeiten
description: Anleitung zur Auflösung von 3D-Dateiabhängigkeiten wie Texturmap-Dateien bei fehlgeschlagener automatischer Auflösung.
seo-description: Anleitung zur Auflösung von 3D-Dateiabhängigkeiten wie Texturmap-Dateien bei fehlgeschlagener automatischer Auflösung.
uuid: 49cefabf-147b-4a78-90f3-0f2d6a8e8cae
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 05b7410b-82a1-4267-ac07-2edbc29e9ee8
exl-id: 088d32a8-a47e-4ae6-a171-8d327d3dac64
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 49%

---

# Auflösen von Dateiabhängigkeiten {#resolving-file-dependencies}

Abhängigkeiten von primären 3D-Modelldateien wie Texturmap-Dateien werden bei Möglichkeit automatisch aufgelöst. Dies ist möglich, weil AEM nahe gelegene Asset-Ordner nach Dateien mit den Namen durchsucht, die auch in den 3D-Dateien vorkommen. Wenn eine oder mehrere Abhängigkeiten während der Verarbeitung der Vorschau &quot;Erstellen&quot;nicht aufgelöst werden können, zeigt die Elementkarte in der **[!UICONTROL Card-Ansicht]** die folgende rote Bannermeldung an:

![chlimage_1-124](assets/chlimage_1-124.png)

**So lösen Sie Dateiabhängigkeiten auf**:

1. Bewegen Sie den Mauszeiger in der Ansicht **[!UICONTROL Card]** über die Meldung **[!UICONTROL Ungelöste Abhängigkeiten]** auf der Karte und klicken Sie dann auf das Symbol **[!UICONTROL Ausrufezeichen]**.

   ![chlimage_1-125](assets/chlimage_1-125.png)

1. Tippen Sie auf der Seite **[!UICONTROL Metadateneigenschaften]** auf die Registerkarte **[!UICONTROL Abhängigkeiten]**.

   Die Dateien, die AEM nicht automatisch auflösen konnten, werden in der Spalte **[!UICONTROL Ursprüngliche Pfade]** in Rot aufgeführt.

1. Führen Sie einen oder mehrere der folgenden Schritte aus:

   * **Abhängigkeiten suchen und auswählen**. (Bei dieser Option wird davon ausgegangen, dass Sie die Abhängigkeitsdateien bereits hochgeladen haben.)

      1. Tippen Sie auf das Symbol **[!UICONTROL Dateisuche]** links neben dem roten Pfad.
      1. Navigieren Sie auf der Seite **[!UICONTROL Inhalt auswählen]** zur fehlenden Datei und tippen Sie dann auf die Karte der Datei, um sie auszuwählen.
      1. Tippen Sie in der oberen linken Ecke der Seite **[!UICONTROL Inhalt auswählen]** auf **[!UICONTROL Schließen]** (X-Symbol), um zur Seite **[!UICONTROL Eigenschaften der Ansicht]** zurückzukehren.
   * **Abhängigkeiten hochladen**. (Bei dieser Option wird davon ausgegangen, dass Sie die fehlenden Dateien noch nicht hochgeladen haben.)

      1. Beachten Sie die fehlenden Pfade und Dateinamen.
      1. Tippen Sie in der rechten oberen Ecke auf **[!UICONTROL Schließen]**.

   Nach dem Hochladen kehren Sie zur Seite **[!UICONTROL Eigenschaften der Ansicht > Abhängigkeiten]** zurück. Das neu hochgeladene Asset wird nun korrekt als referenziertes Asset aufgeführt.

   * **Abhängigkeiten ignorieren**.

      Wenn keine fehlende Abhängigkeit mehr benötigt wird, geben Sie unter der Spalte **[!UICONTROL Verweisender Asset]** im Textfeld links neben der fehlenden Datei `n/a` ein, damit AEM 3D die Datei ignoriert.



1. Tippen Sie rechts oben auf der Seite **[!UICONTROL Eigenschaften von Ansichten]** auf **[!UICONTROL Speichern]**.
1. Tippen Sie auf **[!UICONTROL Schließen]****[!UICONTROL , um zur Kartenansicht zurückzukehren]**.

   Das Asset wird mit den neu aufgelösten Abhängigkeiten automatisch neu verarbeitet.
