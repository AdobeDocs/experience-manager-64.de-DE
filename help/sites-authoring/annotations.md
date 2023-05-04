---
title: Anmerkungen beim Bearbeiten einer Seite
seo-title: Annotations when Editing a Page
description: Viele Komponenten, die direkt zur Handhabung von Inhalten verwendet werden, ermöglichen das Hinzufügen von Anmerkungen.
seo-description: Many components directly related to content allow you to add an annotation
uuid: 157be55c-8ab8-472e-be32-0dcc02bfa41d
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: aa89326a-ad33-4b0b-8d09-c68c5a5c790a
exl-id: 65e534ec-7f73-4333-b225-7adf082f66d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 57%

---

# Anmerkungen beim Bearbeiten einer Seite{#annotations-when-editing-a-page}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Oft muss das Hinzufügen von Inhalten zu den Seiten Ihrer Website vor der tatsächlichen Veröffentlichung besprochen werden. Um dies zu unterstützen, können Sie mit vielen Komponenten, die sich direkt auf Inhalte beziehen (im Gegensatz zum Layout), Anmerkungen hinzufügen.

Bei einer Anmerkung wird eine farbige Markierung/Haftnotiz auf der Seite platziert. Mit einer Anmerkung können Sie (oder andere Benutzer) Kommentare und/oder Fragen für andere Autoren/Prüfer hinterlassen.

>[!NOTE]
>
>Die Definition einer einzelnen Komponente bestimmt, ob Anmerkungen in Instanzen dieser Komponente möglich sind oder nicht.

>[!NOTE]
>
>In der klassischen Benutzeroberfläche erstellte Anmerkungen werden in der Touch-optimierten Benutzeroberfläche angezeigt. Zeichnungen sind jedoch benutzeroberflächenspezifisch und werden nur in der Benutzeroberfläche angezeigt, in der sie erstellt wurden.

>[!CAUTION]
>
>Durch Löschen einer Ressource (z. B. eines Absatzes) werden alle Anmerkungen und Zeichnungen gelöscht, die mit dieser Ressource verbunden sind (unabhängig von ihrer Position auf der Seite als Ganzes).

>[!NOTE]
>
>Je nach Ihren Anforderungen können Sie auch einen Workflow erstellen, damit Benachrichtigungen gesendet werden, wenn Anmerkungen hinzugefügt, aktualisiert oder gelöscht werden.

## Anmerkungen {#annotations}

Zum Erstellen und Ansehen von Anmerkungen wird ein spezieller [Modus](/help/sites-authoring/author-environment-tools.md#page-modes) verwendet.

>[!NOTE]
>
>Beachten Sie, dass Sie auch mithilfe von [Kommentaren](/help/sites-authoring/basic-handling.md#timeline) Feedback zu einer Seite geben können.

>[!NOTE]
>
>Sie können Anmerkungen zu einer Vielzahl von Ressourcen anfügen: 
>
>* [Anmerkungen zu Assets](/help/assets/managing-assets-touch-ui.md#annotating)
>* [Kommentieren von Video-Assets](/help/assets/managing-video-assets.md#annotating-video-assets)
>


### Hinzufügen von Anmerkungen zu Komponenten {#annotating-a-component}

Im Anmerkungsmodus können Sie Anmerkungen für Ihren Inhalt erstellen, bearbeiten, verschieben oder löschen:

1. Sie können den Anmerkungsmodus über das Symbol in der Symbolleiste (oben rechts) aufrufen, wenn Sie eine Seite bearbeiten:

   ![](do-not-localize/screen_shot_2018-03-22at110414.png)

   Sie können nun vorhandene Anmerkungen anzeigen.

   >[!NOTE]
   >
   >Um den Anmerkungsmodus zu beenden, tippen/klicken Sie rechts oben in der Symbolleiste auf das Symbol Anmerken (x-Symbol).

1. Klicken/tippen Sie auf das Symbol „Anmerkung hinzufügen“ (Plussymbol links in der Symbolleiste), um mit dem Hinzufügen von Anmerkungen zu beginnen.

   >[!NOTE]
   >
   >Um das Hinzufügen von Anmerkungen zu beenden (und zur Anzeige zurückzukehren), tippen/klicken Sie links in der oberen Symbolleiste auf das Symbol Abbrechen (x-Symbol in einem weißen Kreis).

1. Klicken/tippen Sie auf die gewünschte Komponente (Komponenten, die kommentiert werden können, werden mit einem blauen Rahmen markiert), um die Anmerkung hinzuzufügen und das Dialogfeld zu öffnen:

   ![screen_shot_2018-03-22at110606](assets/screen_shot_2018-03-22at110606.png)

   Hier können Sie das entsprechende Feld und/oder Symbol verwenden, um:

   * Geben Sie den Anmerkungstext ein.
   * Eine Zeichnung (Linien und Formen) erstellen, um den Bereich der Komponente hervorzuheben.

      Der Mauszeiger ändert sich in ein Fadenkreuz, wenn Sie eine Zeichnung erstellen. Sie können mehrere separate Linien zeichnen. Die Zeichnungslinie hat dieselbe Farbe wie die Anmerkung und kann ein Pfeil, ein Kreis oder ein Oval sein.
   ![](do-not-localize/screen_shot_2018-03-22at110640.png)

   * Farbe wählen/ändern:

   ![](do-not-localize/chlimage_1-19.png)

   * Die Anmerkung löschen.

   ![](do-not-localize/screen_shot_2018-03-22at110647.png)

1. Sie können das Dialogfeld für die Anmerkungen schließen, indem Sie außerhalb des Dialogfelds. Eine abgeschnittene Ansicht (das erste Wort) der Anmerkung wird zusammen mit allen Zeichnungen angezeigt:

   ![screen_shot_2018-03-22at110850](assets/screen_shot_2018-03-22at110850.png)

1. Wenn Sie mit dem Bearbeiten einer bestimmten Anmerkung fertig sind, können Sie Folgendes tun:

   * Klicken/tippen Sie auf die Textmarkierung, um die Anmerkung zu öffnen. Nach dem Öffnen können Sie den Volltext anzeigen, Änderungen vornehmen oder die Anmerkung löschen.

      * Zeichnungen können nicht unabhängig von der Anmerkung gelöscht werden.
   * Positionieren Sie die Textmarkierung neu.
   * Klicken/tippen Sie auf eine Zeichnung, um diese Zeichnung auszuwählen und sie auf die gewünschte Position zu ziehen.
   * Verschieben oder Kopieren einer Komponente

      * Alle zugehörigen Anmerkungen und deren Zeichnungen werden ebenfalls verschoben oder kopiert und ihre Position in Bezug auf den Absatz bleibt unverändert.


1. Um den Anmerkungsmodus zu beenden und zum zuvor verwendeten Modus zurückzukehren, tippen/klicken Sie auf das Symbol Anmerken (x-Symbol) rechts oben in der Symbolleiste.

>[!NOTE]
>Anmerkungen können nicht zu einer Seite hinzugefügt werden, die von einem anderen Benutzer gesperrt wurde.

### Kennzeichnung von Anmerkungen {#annotation-indicator}

Anmerkungen werden nicht im Bearbeitungsmodus angezeigt, doch die Kennzeichnung oben rechts in der Symbolleiste gibt an, wie viele Anmerkungen auf der aktuellen Seite vorhanden sind. Die Kennzeichnung ersetzt das standardmäßige Anmerkungssymbol, dient jedoch ebenfalls als schneller Link, mit dem Sie den Anmerkungsmodus aktivieren/deaktivieren können:

![chlimage_1-242](assets/chlimage_1-242.png)
