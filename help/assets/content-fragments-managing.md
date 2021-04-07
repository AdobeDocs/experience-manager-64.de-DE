---
title: Verwalten von Inhaltsfragmenten
seo-title: Verwalten von Inhaltsfragmenten
description: Inhaltsfragmente werden als Assets gespeichert und daher hauptsächlich über die Assets-Konsole verwaltet.
seo-description: Inhaltsfragmente werden als Assets gespeichert und daher hauptsächlich über die Assets-Konsole verwaltet.
uuid: 0659cf03-b4e8-4b8b-bec7-0082f980115a
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: da8f968b-91cc-45a8-ae4b-757b4f840b8e
exl-id: b21ba7a1-6e6f-4b95-9336-b49f7e932af5
feature: Inhaltsfragmente
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '1511'
ht-degree: 97%

---

# Verwalten von Inhaltsfragmenten {#managing-content-fragments}

>[!CAUTION]
>
>Einige Inhaltsfragmentfunktionen erfordern die Anwendung von [AEM 6.4 Service Pack 2 (6.4.2.0) oder höher](/help/release-notes/sp-release-notes.md).

Inhaltsfragmente werden als **[!UICONTROL Assets]** gespeichert und daher hauptsächlich über die **[!UICONTROL Assets-Konsole]** verwaltet.

>[!NOTE]
>
>Inhaltsfragmente werden dann für erstellte Seiten verwendet. Weitere Informationen finden Sie unter [Seitenerstellung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md).

## Erstellen von Inhaltsfragmenten  {#creating-content-fragments}

### Erstellen von Inhaltsmodellen {#creating-a-content-model}

[Inhaltsfragmentmodelle](content-fragments-models.md) können vor dem Erstellen von Inhaltsfragmenten mit strukturiertem Inhalt aktiviert und erstellt werden.

>[!NOTE]
>
>Weitere Informationen zu für einfache Inhaltsfragmente verwendeten Vorlagen finden Sie unter [Entwickeln von Inhaltsfragmenten](/help/sites-developing/customizing-content-fragments.md).

### Erstellen eines Inhaltsfragments {#creating-a-content-fragment}

Die Methode zum Erstellen eines Inhaltsmodells ist (im Grunde genommen) bei einfachen und strukturierten Fragmenten gleich:

1. Navigieren Sie zum Ordner **[!UICONTROL Assets]**, in dem Sie das Fragment erstellen möchten.
1. Wählen Sie **[!UICONTROL Erstellen]** und danach **[!UICONTROL Inhaltsfragment]** aus, um den Assistenten zu öffnen.
1. Im ersten Schritt des Assistenten müssen Sie die Grundlage des neuen Fragments angeben.

   * Dabei kann es sich um Folgendes handeln:

      * [](/help/sites-developing/content-fragment-templates.md)Vorlage – beispielsweise **[!UICONTROL Einfaches Fragment]**
      * [Modell](content-fragments-models.md) – wird verwendet, um ein Fragment zu erstellen, für das strukturierte Inhalte erforderlich sind; beispielsweise das **Flughafen**-Modell
   * Es werden alle verfügbaren Vorlagen und Modelle angezeigt.

   Wählen Sie **[!UICONTROL Weiter]** aus, wenn Sie Ihre Auswahl getroffen haben.

   ![cfm-6420-15](assets/cfm-6420-15.png)

1. Geben Sie im Schritt **[!UICONTROL Eigenschaften]** Folgendes an:

   * **[!UICONTROL Allgemein]**

      * **[!UICONTROL Titel]**

         Der Titel des Fragments.

         Obligatorisch.

      * **[!UICONTROL Beschreibung]**
      * **[!UICONTROL Tags]**
   * **[!UICONTROL Erweitert]**

      * **[!UICONTROL Name]**

         Der Name, der für die URL verwendet wird.

         Obligatorisch. Wird automatisch aus dem Titel abgeleitet, kann jedoch aktualisiert werden.


1. Wählen Sie **[!UICONTROL Erstellen]** aus, um den Vorgang abzuschließen, und **[!UICONTROL öffnen]** Sie das Fragment zur Bearbeitung oder wechseln Sie über **[!UICONTROL Fertig]** wieder zur Konsole.

## Aktionen für ein Inhaltsfragment {#actions-for-a-content-fragment}

In der **[!UICONTROL Assets-Konsole]** können Sie eine Reihe von Aktionen für Ihre Inhaltsfragmente vornehmen, die Sie wie folgt erreichen:

* Über die Symbolleiste – nachdem Sie das Fragment ausgewählt haben, sind alle geeigneten Aktionen verfügbar.
* Als [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions) – ein Teil der Aktionen, die für die individuellen Fragmentkarten verfügbar sind.

![cfm-6420-17](assets/cfm-6420-17.png)

Wählen Sie das Fragment aus, um die Symbolleiste mit entsprechenden Aktionen anzuzeigen:

* **[!UICONTROL Download]**

   * Speichern Sie das Fragment als ZIP-Datei. Sie können festlegen, ob die betreffenden Elemente, Varianten und Metadaten enthalten sein sollen.

* **[!UICONTROL Erstellen]**
* **[!UICONTROL Checkout]**
* **[!UICONTROL Eigenschaften]**

   * Ermöglicht das Anzeigen bzw. Bearbeiten der Metadaten des Fragments.

* **[!UICONTROL Bearbeiten]**

   * Hier können Sie [das Fragment zum Bearbeiten des Inhalts](content-fragments-variations.md) zusammen mit seinen Elementen, Varianten, verknüpften Inhalten und Metadaten öffnen.

* **[!UICONTROL Tags verwalten]**
* **[!UICONTROL Zu Sammlung]**

   * Fügen Sie das Fragment einer Sammlung hinzu.
   * Dies können Sie auch erreichen, wenn Sie [eine Sammlung mit dem Fragment verknüpfen](content-fragments-assoc-content.md#adding-associated-content).

* **[!UICONTROL Kopieren/Einfügen]**
* **[!UICONTROL Verschieben]**
* **[!UICONTROL Quick Publish]**
* **[!UICONTROL Veröffentlichung verwalten]**
* **[!UICONTROL Löschen]**

>[!NOTE]
>
>Viele davon sind [Standardaktionen für Assets](managing-assets-touch-ui.md) und/oder die [Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de).

## Öffnen des Fragmenteditors {#opening-the-fragment-editor}

So öffnen Sie ein Fragment zur Bearbeitung:

>[!CAUTION]
>
>Um ein Inhaltsfragment zu bearbeiten, benötigen Sie [die entsprechenden Berechtigungen](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Wenden Sie sich an Ihren Systemadministrator, falls Probleme auftreten.

1. Navigieren Sie in der Konsole **[!UICONTROL Assets]** zum Speicherort des gewünschten Inhaltsfragments.
1. Öffnen Sie das Fragment zur Bearbeitung. Befolgen Sie dazu einen der folgenden Schritte:

   * Klicken/tippen Sie auf das Fragment oder den Fragment-Link (abhängig von der Konsolenansicht).
   * Wählen Sie das Fragment und anschließend in der Symbolleiste die Option **[!UICONTROL Bearbeiten]** aus.

   Der Fragmenteditor wird geöffnet:

   ![cfm-6420-18](assets/cfm-6420-18.png)

   >[!NOTE]
   >
   >1. Es wird eine Benachrichtigung angezeigt, wenn das Fragment bereits auf einer Inhaltsseite referenziert wird.
      >
      >
   2. Das seitliche Bedienfeld kann über das Symbol **[!UICONTROL Seitliches Bedienfeld ein/aus]** ein- oder ausgeblendet werden.


1. Navigieren Sie mit den Symbolen im seitlichen Bedienfeld durch die drei Modi:

   * Varianten: [Bearbeiten des Inhalts](#editing-the-content-of-your-fragment) und [Verwalten Ihrer Varianten](#creating-and-managing-variations-within-your-fragment)
   * [Anmerkungen](content-fragments-variations.md#annotating-a-content-fragment)
   * [Zugehörige Inhalte](#associating-content-with-your-fragment)
   * [Metadaten](#viewing-and-editing-the-metadata-properties-of-your-fragment)

   ![cfm-10](assets/cfm-10.png)

1. Wenn Sie Ihre Änderungen vorgenommen haben, verwenden Sie je nach Bedarf entweder **[!UICONTROL Speichern]** oder **[!UICONTROL Abbrechen]**.

   >[!NOTE]
   >
   >Sowohl **[!UICONTROL Speichern]** als auch **[!UICONTROL Abbrechen]** schließen den Editor – siehe [Speichern, Abbrechen und Versionen](#save-cancel-and-versions) für ausführliche Informationen zur Funktionsweise beider Optionen für Inhaltsfragmente.

## Speichern, Abbrechen und Versionen   {#save-cancel-and-versions}

>[!NOTE]
>
>Versionen können [über die Zeitleiste auch erstellt, verglichen und zurückgesetzt werden](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments).

Der Editor bietet zwei Optionen:

* **[!UICONTROL Speichern]**

   Die aktuellen Änderungen werden gespeichert und der Editor wird beendet.

   >[!CAUTION]
   >
   >Um ein Inhaltsfragment zu bearbeiten, benötigen Sie [die entsprechenden Berechtigungen](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Wenden Sie sich an Ihren Systemadministrator, falls Probleme auftreten.

   >[!NOTE]
   >
   >Es ist möglich, im Fragmenteditor zu bleiben und vor Auswahl von **[!UICONTROL Speichern]** eine Reihe von Änderungen vorzunehmen.

   >[!CAUTION]
   >
   >Die Option **[!UICONTROL Speichern]** speichert nicht nur einfach Ihre Änderungen, sondern aktualisiert auch alle Verweise und stellt sicher, dass der Dispatcher nach Bedarf geleert wird. Es kann einige Zeit dauern, bis diese Änderungen verarbeitet werden. Aus diesem Grund kann die Leistung eines umfassenden/komplexen/stark belasteten Systems beeinträchtigt werden.
   >
   >
   >Beachten Sie das, wenn Sie die Option **[!UICONTROL Speichern]** auswählen und den Fragmenteditor danach schnell erneut aufrufen, um weitere Änderungen vorzunehmen und zu speichern.

* **[!UICONTROL Abbrechen]**

   Der Editor wird beendet und die letzten Änderungen werden nicht gespeichert.

Beim Bearbeiten Ihres Inhaltsfragments erstellt AEM automatisch Versionen, damit ältere Inhalte wiederhergestellt werden können, falls Sie Ihre Änderungen über **[!UICONTROL Abbrechen]** verwerfen:

1. Wenn ein Inhaltsfragment zur Bearbeitung geöffnet ist, überprüft AEM, ob ein Cookie-basiertes Token vorliegt, das angibt, ob eine *Bearbeitungssitzung* vorhanden ist:

   1. Wird das entsprechende Token gefunden, gilt das Fragment als Teil der vorhandenen Bearbeitungssitzung.
   1. Wenn das Token *nicht* verfügbar ist und der Benutzer mit dem Bearbeiten von Inhalt beginnt, wird eine Version erstellt, und ein Token für diese neue Bearbeitungssitzung wird an den Client gesendet, wo er in einem Cookie gespeichert wird.

1. Während einer *aktiven* Bearbeitungssitzung wird der bearbeitete Inhalt automatisch alle 600 Sekunden gespeichert (Standardeinstellung).

   >[!NOTE]
   >
   >Das Intervall für das automatische Speichern kann mit dem Mechanismus `/conf` konfiguriert werden.
   >
   >Den Standardwert finden Sie unter:
   >
   >`/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

1. Wird **[!UICONTROL Abbrechen]** ausgewählt, um die Bearbeitung abzubrechen, wird die am Anfang der Bearbeitungssitzung erstellte Version wiederhergestellt und das Token wird zum Beenden der Bearbeitungssitzung entfernt.
1. Werden die Bearbeitungen über die Option **[!UICONTROL Speichern]** gespeichert, werden die aktualisierten Elemente/Varianten beibehalten und das Token wird zum Beenden der Bearbeitungssitzung entfernt.

## Bearbeiten des Inhalts Ihres Fragments {#editing-the-content-of-your-fragment}

Wenn Sie das Fragment geöffnet haben, können Sie die Registerkarte [Varianten](content-fragments-variations.md) verwenden, um Ihren Inhalt zu erstellen.

## Erstellen und Verwalten von Varianten innerhalb Ihres Fragments   {#creating-and-managing-variations-within-your-fragment}

Sobald Sie den primären Inhalt erstellt haben, können Sie [Varianten](content-fragments-variations.md) dieses Inhalts erstellen und verwalten.

## Verknüpfen von Inhalt mit Ihrem Fragment   {#associating-content-with-your-fragment}

Sie können auch Inhalt mit einem Fragment [verknüpfen](content-fragments-assoc-content.md). So entsteht eine Verbindung, mit der Assets (d. h. Bilder) für ein Fragment verwendet werden können (falls gewünscht), wenn sie zu einer Inhaltsseite hinzugefügt werden.

## Anzeigen und Bearbeiten von Metadaten (Eigenschaften) des Fragments   {#viewing-and-editing-the-metadata-properties-of-your-fragment}

Sie können die Eigenschaften eines Fragments über die Registerkarte [[!UICONTROL Metadaten]](content-fragments-metadata.md) anzeigen und bearbeiten.

## Zeitleiste für Inhaltsfragmente   {#timeline-for-content-fragments}

Neben den Standardoptionen enthält die [Zeitleiste](managing-assets-touch-ui.md#timeline) Informationen und Aktionen für Inhaltsfragmente.

* Anzeigen von Informationen zu Versionen, Kommentaren und Anmerkungen
* Aktionen für Versionen

   * **[[!UICONTROL Auf diese Version zurück]](#reverting-to-a-version)** (ein vorhandenes Fragment und eine bestimmte Version auswählen)
   * **[[!UICONTROL Mit aktueller Version vergleichen]](#comparing-fragment-versions)** (ein vorhandenes Fragment und eine bestimmte Version auswählen)
   * **[!UICONTROL Beschriftung]** und/oder **[!UICONTROL Kommentar]** hinzufügen (ein vorhandenes Fragment und eine bestimmte Version auswählen)
   * **[!UICONTROL Als Version speichern]** (ein vorhandenes Fragment und dann den Pfeil nach oben am unteren Rand der Zeitleiste auswählen)

* Aktionen für Anmerkungen

   * **[!UICONTROL Löschen]**

>[!NOTE]
>
>Kommentare sind:
>
>* Standardfunktionen für alle Assets
>* In der Zeitleiste erstellt worden
>* Mit dem Fragment-Asset verbunden

>
>
Anmerkungen (für Inhaltsfragmente) sind:
>
>* Im Fragmenteditor eingegeben worden
>* Spezifisch für ein ausgewähltes Textsegment innerhalb des Fragments


Beispiel:

![cfm-6420-19](assets/cfm-6420-19.png)

## Vergleichen von Fragment-Versionen {#comparing-fragment-versions}

Die Aktion **[!UICONTROL Mit aktueller Version vergleichen]** ist in der [[!UICONTROL Zeitleiste] verfügbar, sobald Sie eine bestimmte Version ausgewählt haben.](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments)

Folgendes wird geöffnet:

* die **[!UICONTROL aktuelle]** (neueste) Version (links)

* die ausgewählte Version **v&lt;*x.y*>** (rechts)

Sie werden nebeneinander angezeigt:

* Unterschiede werden hervorgehoben

   * Gelöschter Text: Rot
   * Eingefügter Text: Grün
   * Ersetzter Text: Blau

* Über das Vollbildsymbol können Sie jede Version separat öffnen. Wechseln Sie dann wieder zur parallelen Ansicht.
* Sie können die jeweilige Version **[!UICONTROL wiederherstellen]**.
* Über **[!UICONTROL Fertig]** kehren Sie zur Konsole zurück.

>[!NOTE]
>
>Sie können den Fragmentinhalt nicht bearbeiten, während Sie Fragmente vergleichen.

![cfm-6420-20](assets/cfm-6420-20.png)

## Wiederherstellen einer früheren Version {#reverting-to-a-version}

Sie können eine frühere Version wiederherstellen.

* Direkt über die [[!UICONTROL Zeitleiste]](content-fragments-managing.md#timeline-for-content-fragments).

   Wählen Sie die gewünschte Version und dann die Aktion **[!UICONTROL Auf diese Version zurück]** aus.

* Beim [Vergleichen einer Version mit der aktuellen Version](content-fragments-managing.md#comparing-fragment-versions) können Sie die ausgewählte Version **[!UICONTROL wiederherstellen]**.

## Veröffentlichen und Referenzieren von Fragmenten {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>Wenn das Fragment auf einem Modell basiert, sollten Sie sicherstellen, dass das [Modell veröffentlicht wurde](content-fragments-models.md#publishing-a-content-fragment-model).
>
>Wenn Sie Inhaltsfragmente veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

Inhaltsfragmente müssen veröffentlicht werden, um in der Veröffentlichungsumgebung genutzt werden zu können. Sie können folgendermaßen veröffentlicht werden:

* Nach der Erstellung in der Konsole **[!UICONTROL Assets]**.
* Wenn Sie [eine Seite veröffentlichen, in der das Fragment verwendet wird](/help/sites-authoring/content-fragments.md#publishing), wird das Fragment in den Seitenverweisen aufgeführt.

>[!CAUTION]
>
>Nachdem ein Fragment veröffentlicht und/oder referenziert wurde, zeigt AEM eine Warnmeldung an, wenn ein Autor das Fragment erneut zur Bearbeitung öffnet. Dies dient als Hinweis darauf, dass am Fragment vorgenommene Änderungen sich auch auf die referenzierten Seiten auswirken.

## Löschen von Fragmenten {#deleting-a-fragment}

So löschen Sie ein Fragment:

1. Navigieren Sie in der Konsole **[!UICONTROL Assets]** zum Speicherort des Inhaltsfragments.
1. Wählen Sie das Fragment aus.

   >[!NOTE]
   >
   >Die Aktion **[!UICONTROL Löschen]** ist nicht als Schnellzugriff verfügbar.

1. Wählen Sie **[!UICONTROL Löschen]** in der Symbolleiste aus.
1. Bestätigen Sie die **[!UICONTROL Löschaktion]**.

   >[!CAUTION]
   >
   >Wenn das Fragment bereits in einer Seite referenziert wird, werden Sie in einer Warnung zur Bestätigung des **[!UICONTROL erzwungenen Löschens]** aufgefordert. Das Fragment wird zusammen mit seiner Inhaltsfragmentkomponente aus allen Inhaltsseiten gelöscht.
