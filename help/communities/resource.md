---
title: Erstellen und Zuweisen von Aktivierungsressourcen
seo-title: Create and Assign Enablement Resources
description: Aktivierungsressourcen hinzufügen
seo-description: Add enablement resources
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
exl-id: 9f447a54-4512-41ab-b8d3-327e751eda58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 8%

---

# Erstellen und Zuweisen von Aktivierungsressourcen {#create-and-assign-enablement-resources}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Hinzufügen einer Aktivierungsressource {#add-an-enablement-resource}

So fügen Sie der neuen Community-Site eine Aktivierungsressource hinzu:

* In der Autoreninstanz
   * Beispiel: [http://localhost:4502/](http://localhost:4503/)
* Als Systemadministrator anmelden
* Wählen Sie in der globalen Navigation die Option **Communities > [Ressourcen](resources.md)**

   ![chlimage_1-199](assets/chlimage_1-199.png)
   ![chlimage_1-200](assets/chlimage_1-200.png)
* Wählen Sie die Community-Site aus, zu der Aktivierungsressourcen hinzugefügt werden.
   * Klicken Sie auf `Enablement Tutorial`
* Wählen Sie im Menü die Option ` Create`
* Auswählen **[!UICONTROL Ressource]**

![chlimage_1-201](assets/chlimage_1-201.png)

### Grundlegende Informationen {#basic-info}

Füllen Sie die grundlegenden Informationen für die Ressource aus:

* **[!UICONTROL Site-Name]**: auf den Namen der ausgewählten Community-Site festlegen: Tutorial zur Aktivierung
* **[!UICONTROL Resource Name&amp;ast;]**: Skiunterricht 1
* **[!UICONTROL Tags]**: Tutorial: Sport/Skifahren
* **[!UICONTROL Im Katalog anzeigen]**: on
* **[!UICONTROL Beschreibung]**: Schneeschlitten für Anfänger
* **[!UICONTROL Bild hinzufügen]**: Fügen Sie ein Bild hinzu, um die Ressource dem Mitglied in seiner Zuweisungsansicht darzustellen.
   ![chlimage_1-202](assets/chlimage_1-202.png)
* Wählen Sie **[!UICONTROL Weiter]** aus

### Inhalt hinzufügen {#add-content}

Es wird zwar so angezeigt, als ob mehrere Ressourcen ausgewählt sein könnten, aber nur eine ist zulässig.

Wählen Sie die `'+' icon`, um mit der Auswahl der Ressource zu beginnen, indem Sie die Quelle identifizieren.

![chlimage_1-203](assets/chlimage_1-203.png) ![chlimage_1-204](assets/chlimage_1-204.png)

Eine Ressource hochladen. Wenn eine Videoressource vorhanden ist, laden Sie entweder ein benutzerdefiniertes Bild hoch, das vor der Videowiedergabe angezeigt werden soll, oder lassen Sie zu, dass eine Miniaturansicht aus dem Video generiert wird (es kann einige Minuten dauern - es ist nicht erforderlich zu warten).

![chlimage_1-205](assets/chlimage_1-205.png)

* select **[!UICONTROL Nächste]**

### Einstellungen {#settings}

* **[!UICONTROL Social-Einstellungen]**
Behalten Sie die Standarderstellung für die Kommentierung und Bewertung von Aktivierungsressourcen durch die Lernenden bei.
* **[!UICONTROL Fälligkeitsdatum]**

   *(Optional)* Es kann ein Datum ausgewählt werden, bis zu dem die Zuweisung abgeschlossen werden soll.
* **[!UICONTROL Ressourcen-Autor]**

   *(Optional)* Leer lassen.
* **[!UICONTROL Resource Contact&amp;ast;]**

   *(Erforderlich)* Wählen Sie über das Pulldown-Menü ein Mitglied aus `Quinn Harper`.
* **[!UICONTROL Ressourcen-Experte]**

   *(Optional)* Leer lassen.
   **Hinweis**: Wenn Benutzer oder Gruppen nicht sichtbar sind, überprüfen Sie, ob sie zum `Community Enable Members` und *Gespeichert* in der Veröffentlichungsinstanz.
   ![chlimage_1-206](assets/chlimage_1-206.png)
* Wählen Sie **[!UICONTROL Weiter]** aus

### Zuweisungen {#assignments}

* **[!UICONTROL Zuweisende Stellen hinzufügen]**
Lassen Sie die Einstellung deaktiviert, da diese Aktivierungsressource einem Lernpfad hinzugefügt wird. Wenn ein Lernender der einzelnen Aktivierungsressource sowie einem learningPath mit der Aktivierungsressource zugewiesen wird, wird der Lernende der Aktivierungsressource zweimal zugewiesen.

![chlimage_1-207](assets/chlimage_1-207.png)

* Wählen Sie **[!UICONTROL Erstellen]** aus

![chlimage_1-208](assets/chlimage_1-208.png)

Die erfolgreiche Erstellung der Ressource kehrt zur Ressourcenkonsole zurück, wobei die neu erstellte Ressource ausgewählt ist. In dieser Konsole können Sie Inhalte veröffentlichen, Lernende hinzufügen und andere Einstellungen ändern.

Um eine neue Version der Aktivierungsressource hochzuladen, wird empfohlen, eine neue Ressource zu erstellen, dann die Registrierung für Mitglieder aus der alten Version aufzuheben und sie in der neuen Version zu registrieren.

### Ressource veröffentlichen {#publish-the-resource}

Damit die Teilnehmer die zugewiesenen Ressourcen sehen können, müssen sie veröffentlicht werden:

* Welt auswählen `Publish`icon

Die Aktivierung wird mit einer Erfolgsmeldung bestätigt:

![chlimage_1-209](assets/chlimage_1-209.png)

## Eine zweite Aktivierungsressource hinzufügen {#add-a-second-enablement-resource}

Wiederholen Sie die obigen Schritte, um eine zweite zugehörige Aktivierungsressource zu erstellen und zu veröffentlichen, aus der ein Lernpfad erstellt wird.

![chlimage_1-210](assets/chlimage_1-210.png)

**Veröffentlichen** die zweite Ressource.

Kehren Sie zur Liste des Tutorials zur Aktivierung der Ressourcen zurück.

*Hinweis: Wenn beide Ressourcen nicht sichtbar sind, aktualisieren Sie die Seite.*

![chlimage_1-211](assets/chlimage_1-211.png)

## Lernpfad hinzufügen {#add-a-learning-path}

Ein Lernpfad ist eine logische Gruppierung der Aktivierungsressourcen, die einen Kurs bilden.

* Wählen Sie in der Ressourcenkonsole die Option `+ Create`
* Auswählen **[!UICONTROL Lernpfad]**

![chlimage_1-212](assets/chlimage_1-212.png)

Fügen Sie die **[!UICONTROL Basisinformationen]**:

* **[!UICONTROL Lernpfad-Name]**: Skiunterricht
* **[!UICONTROL Tags]**: Tutorial: Skiing
* **[!UICONTROL Im Katalog anzeigen]**: Nicht aktivieren
* **[!UICONTROL Bild hochladen]** , um den Lernpfad in der Ressourcenkonsole darzustellen.

![chlimage_1-213](assets/chlimage_1-213.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

Überspringen Sie das nächste Bedienfeld, da es keine erforderlichen Lernpfade zum Hinzufügen gibt.

* Wählen Sie **[!UICONTROL Weiter]** aus

Im Bereich &quot;Ressourcen hinzufügen&quot;

* Auswählen `+ Add Resources` , um die 2 Skilesessourcen auszuwählen, die zum Lernpfad hinzugefügt werden sollen

   Hinweis: Nur **veröffentlicht** Ressourcen können ausgewählt werden.

>[!NOTE]
>
>Sie können nur die Ressourcen auswählen, die auf derselben Ebene wie der Lernpfad verfügbar sind. Beispielsweise sind für einen in einer Gruppe erstellten Lernpfad nur die Ressourcen auf Gruppenebene verfügbar. für einen Lernpfad, der auf einer Community-Site erstellt wurde, stehen die Ressourcen auf dieser Site zum Hinzufügen zum Lernpfad zur Verfügung.

* Klicken Sie auf **[!UICONTROL Übermitteln]**.

![chlimage_1-214](assets/chlimage_1-214.png) ![chlimage_1-215](assets/chlimage_1-215.png)

* Wählen Sie **[!UICONTROL Weiter]** aus

![chlimage_1-216](assets/chlimage_1-216.png)

* **[!UICONTROL Zuweisende Stellen hinzufügen]**
Wählen Sie über das Pulldown-Menü die 
`Community Ski Class` -Gruppe, der auch Mitglieder angehören sollten `Riley Taylor` und `Sidney Croft.`

* **[!UICONTROL Lernpfad Kontakt&amp;ast;]**

   *(Erforderlich)* Wählen Sie über das Pulldown-Menü ein Mitglied aus `Quinn Harper`.

* Wählen Sie **[!UICONTROL Erstellen]** aus

![chlimage_1-217](assets/chlimage_1-217.png)

Bei erfolgreicher Erstellung des Lernpfads wird die Konsole Ressourcen mit dem neu erstellten Lernpfad ausgewählt. In dieser Konsole können Sie Inhalte veröffentlichen, Lernende hinzufügen und andere Einstellungen ändern.

**Veröffentlichen** Lernpfad.
