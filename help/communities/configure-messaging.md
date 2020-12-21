---
title: Messaging-Funktion
seo-title: Messaging-Funktion
description: Konfigurieren von Messaging-Komponenten
seo-description: Konfigurieren von Messaging-Komponenten
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 29%

---


# Messaging-Funktion {#messaging-feature}

Zusätzlich zu den öffentlich sichtbaren Interaktionen, die in Foren und Kommentaren auftreten, ermöglicht die Messaging-Funktion von AEM Communities es Community-Mitgliedern, privat miteinander zu interagieren.

Diese Funktion kann eingeschlossen werden, wenn eine [Community-Site](overview.md#communitiessites) erstellt wird.

Die Messaging-Funktion bietet Folgendes:

* Senden einer Nachricht an ein oder mehrere Community-Mitglieder
* Eine Nachricht an eine Community-Mitgliedsgruppe senden
* Eine Nachricht mit Anlagen senden
* Weiterleiten einer Nachricht
* Antwort auf eine Nachricht
* Eine Nachricht löschen
* Wiederherstellen einer gelöschten Meldung

Um die Messaging-Funktion zu aktivieren und zu ändern, besuchen Sie

* [Konfigurieren von ](messaging.md) Nachrichten für Administratoren
* [Messaging ](essentials-messaging.md) Essentials für Entwickler

>[!NOTE]
>
>Es wird nicht unterstützt, `Compose Message, Message, or Message List`-Komponenten (in `Communities`Komponentengruppe gefunden) zu einer Seite im Autorenbearbeitungsmodus hinzuzufügen.

## Konfigurieren von Messaging-Komponenten {#configuring-messaging-components}

Wenn Messaging für eine Community-Site aktiviert ist, ist es vollständig eingerichtet, ohne dass eine weitere Konfiguration erforderlich ist. Diese Informationen werden bereitgestellt, wenn die Standardkonfiguration geändert werden muss.

### Konfigurieren der Message-Liste (messagebox) {#configuring-message-list-messagebox}

Um die Liste der Nachrichten für **Inbox**-, **Gesendete Elemente**- und **Papierkorb**-Seiten der Nachrichtenfunktion zu ändern, öffnen Sie die Site im Bearbeitungsmodus [Autor](sites-console.md#authoring-site-content).

Wählen Sie im Modus `Preview` den Link **[!UICONTROL Nachrichten]**, um die Hauptseite der Nachrichten zu öffnen. Wählen Sie dann entweder **[!UICONTROL Posteingang, Gesendete Elemente oder Papierkorb]** aus, um die Liste für diese Nachricht zu konfigurieren.

Wählen Sie im Modus `Edit` die Komponente auf der Seite aus.

Um auf das Konfigurationsdialogfeld zugreifen zu können, müssen Sie die Vererbung abbrechen, indem Sie das Symbol `link`auswählen.

Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des Symbols `broken link` wiederhergestellt werden.

![chlimage_1-396](assets/chlimage_1-396.png)

Nach dem Abbrechen der Vererbung können Sie das Symbol `configure` auswählen, um das Konfigurationsdialogfeld zu öffnen.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Einfache Registerkarte {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Dienstauswahl]**
(*Erforderlich*) Legen Sie diesen Wert auf den Wert der Eigenschaft  `serviceSelector.name` aus dem  [AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service) fest.

* **[!UICONTROL Seite]**
 erstellen (*Erforderlich*) Die Seite, die geöffnet werden soll, wenn ein Mitglied auf die  `Reply` Schaltfläche klickt. Die Zielseite sollte das Formular **[!UICONTROL Nachricht erstellen]** enthalten.

* **[!UICONTROL Als Ressource antworten/anzeigen]** Ist diese Option aktiviert, verweisen die Antwort- und Ansichts-URL auf eine Ressource. Ist sie nicht aktiviert, werden Daten als Abfrageparameter in der URL übermittelt. 

* **[!UICONTROL Anzeigeform für Profil]** Das Profilformular zur Anzeige des Absenderprofils.

* **[!UICONTROL Papierkorb-Ordner]** Ist die Option aktiviert, zeigt diese Nachrichtenlisten-Komponente lediglich Nachrichten an, die als gelöscht markiert wurden (Papierkorb).

* **[!UICONTROL Ordnerpfade]**
(*Erforderlich*) Verweis auf die Werte, die für  `inbox.path.name` und  `sentitems.path.name` im  [AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service) festgelegt wurden. Bei der Konfiguration für ein `Inbox` fügen Sie einen Eintrag mit dem Wert `inbox.path.name` hinzu. Bei der Konfiguration für ein `Outbox` fügen Sie einen Eintrag mit dem Wert `sentitems.path.name` hinzu. Fügen Sie bei der Konfiguration für `Trash` zwei Einträge mit beiden Werten hinzu.

#### Display tab {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Schaltfläche &quot;Gelesen]**
markieren&quot;Wenn aktiviert, wird eine 
`Read`-Schaltfläche, mit der eine Nachricht als gelesen markiert werden kann.

* **[!UICONTROL Markieren Sie die ungelesene]**
SchaltflächeWenn aktiviert, wird eine 
`Mark Unread` -Schaltfläche, mit der eine Nachricht als gelesen markiert werden kann.

* **[!UICONTROL Schaltfläche]**
löschenWenn aktiviert, wird eine 
`Delete`-Schaltfläche, mit der eine Nachricht als gelesen markiert werden kann. Wird die Funktion zum Löschen Duplikat, wenn **`Message Options`** ebenfalls aktiviert ist.

* **[!UICONTROL Nachrichtenoptionen]**
Wenn aktiviert, wird angezeigt 
**`Reply`**,  **`Reply All`** und  **`Forward`**   **`Delete`** Schaltflächen, mit denen eine Nachricht erneut gesendet oder gelöscht werden kann. Wird die Funktion zum Löschen Duplikat, wenn **`Delete Button`** ebenfalls aktiviert ist.

* **[!UICONTROL Nachrichten pro Seite]** Die angegebene Zahl entspricht der maximalen Anzahl von Nachrichten, die bei einer Aufteilung in Seiten pro Seite angezeigt wird. Ist keine Anzahl festgelegt (leeres Feld), werden alle Nachrichten auf einer Seite angezeigt.

* **[!UICONTROL Zeitstempelmuster]** Stellen Sie für eine oder mehrere Sprachen Zeitstempelmuster bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

* **[!UICONTROL Display]**
UserChoose 
**`Sender`** oder  **`Recipients`** um festzulegen, ob der Absender oder die Empfänger angezeigt werden sollen.

### Konfigurieren der Nachricht erstellen {#configuring-compose-message}

Um die Konfiguration der Seite mit der Nachricht zum Erstellen zu ändern, öffnen Sie die Site im Bearbeitungsmodus [Autor](sites-console.md#authoring-site-content).

Wählen Sie im Modus `Preview`den Link **[!UICONTROL Nachrichten]** aus, um die Hauptseite der Nachrichten zu öffnen. Klicken Sie dann auf &quot;Neue Nachricht&quot;, um die Seite `Compose Message` zu öffnen.

Wählen Sie im Modus `Edit` die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.

Um auf das Konfigurationsdialogfeld zugreifen zu können, müssen Sie die Vererbung abbrechen, indem Sie das Symbol `link`auswählen.

Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des Symbols `broken link` wiederhergestellt werden.

![chlimage_1-400](assets/chlimage_1-400.png)

Nach dem Abbrechen der Vererbung können Sie das Symbol `configure` auswählen, um das Konfigurationsdialogfeld zu öffnen.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Einfache Registerkarte {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL URL-Weiterleitung]** Geben Sie die URL der Seite ein, die nach dem Versenden der Nachricht angezeigt werden soll. Beispiel: 
`../messaging.html`.

* **[!UICONTROL URL abbrechen]** Geben Sie die URL der Seite ein, die angezeigt werden soll, wenn der Sender das Verfassen einer Nachricht abbricht. Beispiel: 
`../messaging.html`.

* **[!UICONTROL Maximale Länge des Nachrichtenbetreffs]** Die maximal zulässige Anzahl der Zeichen im Feld „Betreff“. Beispiel: 500. Der Standardwert ist nicht begrenzt.

* **[!UICONTROL Maximale Länge des Nachrichtentextes]** Die maximal zulässige Anzahl der Zeichen im Feld „Inhalt“. Beispielsweise 10000. Der Standardwert ist nicht begrenzt.

* **[!UICONTROL Dienstauswahl]**
(*Erforderlich*) Legen Sie diesen Wert auf den Wert der Eigenschaft  **`serviceSelector.name`** aus dem  [AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service) fest.

#### Display tab {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Feld]**
für Betreff anzeigen Wenn aktiviert, zeigen Sie die 
`Subject` und aktivieren Sie das Hinzufügen eines Betreffs zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Subject]**
LabelGeben Sie den Text ein, der neben dem 
`Subject` field. Der Standardwert ist `Subject`.

* **[!UICONTROL Dateinamenfeld]**
anzeigen Wenn aktiviert, zeigen Sie die 
`Attachment` und aktivieren Sie das Hinzufügen von Dateianlagen zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Dateinamenbeschriftung anhängenGeben Sie den]**
Text ein, der neben dem 
`Attachment` Feld. Der Standardwert ist **`Attach File`**.

* **[!UICONTROL Inhaltsfeld anzeigen]**
Wenn aktiviert, zeigen Sie die 
`Content` und aktivieren Sie das Hinzufügen eines Nachrichtentextes. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Inhaltsbeschriftung]**
Geben Sie den Text ein, der neben dem 
`Content` Feld. Der Standardwert ist **`Body`**.

* **[!UICONTROL Mit Rich-Text-Editor]** Ist diese Option aktiviert, kann ein benutzerdefiniertes „Inhalt“-Textfeld verwendet werden, das über einen eigenen Rich-Text-Editor verfügt. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zeitstempelmuster]** Stellen Sie für eine oder mehrere Sprachen Zeitstempelmuster bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

