---
title: Auflösen von Dateiabhängigkeiten
seo-title: Auflösen von Dateiabhängigkeiten
description: Abhängigkeiten von primären 3D-Modelldateien wie Texturmap-Dateien werden bei Möglichkeit automatisch aufgelöst. Dies ist möglich, weil AEM nahe gelegene Asset-Ordner nach Dateien mit den Namen durchsucht, die auch in den 3D-Dateien vorkommen.
seo-description: Abhängigkeiten von primären 3D-Modelldateien wie Texturmap-Dateien werden bei Möglichkeit automatisch aufgelöst. Dies ist möglich, weil AEM nahe gelegene Asset-Ordner nach Dateien mit den Namen durchsucht, die auch in den 3D-Dateien vorkommen.
uuid: b1b83cb7-b6e5-4417-9a53-b6d8bcf8d2e0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 14754023-e7c4-4dc5-a9d8-408b81861d95
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 61%

---


# Auflösen von Dateiabhängigkeiten{#resolving-file-dependencies}

Abhängigkeiten von primären 3D-Modelldateien wie Texturmap-Dateien werden bei Möglichkeit automatisch aufgelöst. Dies ist möglich, weil AEM nahe gelegene Asset-Ordner nach Dateien mit den Namen durchsucht, die auch in den 3D-Dateien vorkommen. Wenn eine oder mehrere Abhängigkeiten während der Verarbeitung der Vorschau &quot;Erstellen&quot;nicht aufgelöst werden können, zeigt die Elementkarte in der [!UICONTROL Card-Ansicht] die folgende rote Bannermeldung an:

![chlimage_1-189](assets/chlimage_1-189.png)

**So lösen Sie Dateiabhängigkeiten auf**:

1. Bewegen Sie den Mauszeiger in der Ansicht **[!UICONTROL Card]** über die Meldung **[!UICONTROL Ungelöste Abhängigkeiten]** auf der Karte und tippen Sie dann auf das Symbol zum Ausrufezeichen.

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. Tippen Sie auf der Seite „Metadateneigenschaften“ auf die Registerkarte **[!UICONTROL Abhängigkeiten]**.

   Die Dateien, die von AEM nicht automatisch aufgelöst werden konnten, werden in der Spalte „Ausgangspfad“ in Rot angezeigt.

1. Führen Sie einen oder mehrere der folgenden Schritte aus:

   * **[!UICONTROL Abhängigkeiten suchen und auswählen]**. (Bei dieser Option wird davon ausgegangen, dass Sie die Abhängigkeitsdateien bereits hochgeladen haben.)

      1. Tippen Sie auf das Symbol **[!UICONTROL Dateisuche]** links neben dem roten Pfad.
      1. Navigieren Sie auf der Seite **[!UICONTROL Inhalt auswählen]** zur fehlenden Datei und tippen Sie dann auf die Karte der Datei, um sie auszuwählen.
      1. Tippen Sie in der oberen linken Ecke der Seite **[!UICONTROL Inhalt auswählen]** auf **[!UICONTROL Schließen]** (X-Symbol), um zur Seite **[!UICONTROL Eigenschaften der Ansicht]** zurückzukehren.
   * **[!UICONTROL Abhängigkeiten hochladen]**. (Bei dieser Option wird davon ausgegangen, dass Sie die fehlenden Dateien noch nicht hochgeladen haben.)

      1. Beachten Sie die fehlenden Pfade und Dateinamen.
      1. Tippen Sie in der rechten oberen Ecke auf **[!UICONTROL Schließen]**.

   Nach dem Hochladen kehren Sie zur Seite **[!UICONTROL Eigenschaften der Ansicht > Abhängigkeiten]** zurück. Das neu hochgeladene Asset wird nun korrekt als referenziertes Asset aufgeführt.

   * **[!UICONTROL Abhängigkeiten ignorieren]**.

      Wenn keine fehlende Abhängigkeit mehr benötigt wird, geben Sie unter der Spalte **[!UICONTROL Verweisender Asset]** im Textfeld links neben der fehlenden Datei `n/a` ein, damit AEM 3D die Datei ignoriert.



1. Tippen Sie rechts oben auf der Seite **[!UICONTROL Eigenschaften von Ansichten]** auf **[!UICONTROL Speichern]**.
1. Tippen Sie auf **[!UICONTROL Schließen]****[!UICONTROL , um zur Kartenansicht zurückzukehren]**.

   Das Asset wird mit den neu aufgelösten Abhängigkeiten automatisch neu verarbeitet.

