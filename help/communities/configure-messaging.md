---
title: Messaging-Funktion
seo-title: Messaging Feature
description: Konfigurieren von Messaging-Komponenten
seo-description: Configuring Messaging components
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 29%

---

# Messaging-Funktion {#messaging-feature}

Zusätzlich zu den öffentlich sichtbaren Interaktionen in Foren und Kommentaren ermöglicht die Messaging-Funktion von AEM Communities es Community-Mitgliedern, privat miteinander zu interagieren.

Diese Funktion kann bei einer [Community-Site](overview.md#communitiessites) erstellt.

Die Messaging-Funktion bietet Folgendes:

* Nachricht an ein oder mehrere Community-Mitglieder senden
* Nachricht an eine Community-Mitgliedergruppe senden
* Nachricht mit Anhängen senden
* Weiterleiten einer Nachricht
* Auf eine Nachricht antworten
* Nachricht löschen
* Gelöschte Nachricht wiederherstellen

Um die Messaging-Funktion zu aktivieren und zu ändern, besuchen Sie

* [Messaging konfigurieren](messaging.md) für Administratoren
* [Grundlagen zu Messaging](essentials-messaging.md) für Entwickler

>[!NOTE]
>
>Das Hinzufügen von `Compose Message, Message, or Message List` Komponenten (gefunden in `Communities`Komponentengruppe) auf eine Seite im Bearbeitungsmodus &quot;Autor&quot;klicken.

## Konfigurieren von Messaging-Komponenten {#configuring-messaging-components}

Wenn Messaging für eine Community-Site aktiviert ist, ist es vollständig eingerichtet, ohne dass eine weitere Konfiguration erforderlich ist. Diese Informationen werden bereitgestellt, wenn die Standardkonfiguration geändert werden muss.

### Nachrichtenliste konfigurieren (messageBox) {#configuring-message-list-messagebox}

Um die Konfiguration der Nachrichtenliste für **Posteingang**, **Gesendete Elemente** und **Papierkorb** Seiten der Messaging-Funktion öffnen Sie die Site in [Bearbeitungsmodus des Autors](sites-console.md#authoring-site-content).

In `Preview` -Modus, wählen Sie die **[!UICONTROL Nachrichten]** -Link, um die Hauptseite der Nachrichten zu öffnen. Wählen Sie anschließend **[!UICONTROL Posteingang, gesendete Elemente oder Papierkorb]** um die Komponente für diese Nachrichtenliste zu konfigurieren.

In `Edit` -Modus wählen Sie die Komponente auf der Seite aus.

Um auf das Konfigurationsdialogfeld zugreifen zu können, muss die Vererbung durch Auswahl der `link`Symbol.

Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl der `broken link` Symbol.

![chlimage_1-396](assets/chlimage_1-396.png)

Sobald die Vererbung abgebrochen wurde, kann die `configure` -Symbol, um das Konfigurationsdialogfeld zu öffnen.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Registerkarte &quot;Allgemein&quot; {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Dienstauswahl]**
(*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft fest. `serviceSelector.name` von [AEM Communities Messaging-Dienst](messaging.md#messaging-operations-service).

* **[!UICONTROL Seite erstellen]**
(*Erforderlich*) Die Seite, die geöffnet werden soll, wenn ein Mitglied auf die `Reply` Schaltfläche. Die Zielseite sollte das Formular **[!UICONTROL Nachricht erstellen]** enthalten.

* **[!UICONTROL Als Ressource antworten/anzeigen]** Ist diese Option aktiviert, verweisen die Antwort- und Ansichts-URL auf eine Ressource. Ist sie nicht aktiviert, werden Daten als Abfrageparameter in der URL übermittelt. 

* **[!UICONTROL Anzeigeform für Profil]** Das Profilformular zur Anzeige des Absenderprofils.

* **[!UICONTROL Papierkorb-Ordner]** Ist die Option aktiviert, zeigt diese Nachrichtenlisten-Komponente lediglich Nachrichten an, die als gelöscht markiert wurden (Papierkorb).

* **[!UICONTROL Ordnerpfade]**
(*Erforderlich*) Referenzieren der für `inbox.path.name` und `sentitems.path.name` im [AEM Communities Messaging-Dienst](messaging.md#messaging-operations-service). Beim Konfigurieren von `Inbox`, fügen Sie einen Eintrag mit dem Wert von hinzu. `inbox.path.name`. Beim Konfigurieren von `Outbox`, fügen Sie einen Eintrag mit dem Wert von hinzu. `sentitems.path.name`. Wenn Sie `Trash`, fügen Sie zwei Einträge mit beiden Werten hinzu.

#### Registerkarte &quot;Anzeige&quot; {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Schaltfläche &quot;Lesen&quot;]**
Wenn diese Option aktiviert ist, zeigt eine 
`Read`-Schaltfläche, über die eine Nachricht als gelesen gekennzeichnet werden kann.

* **[!UICONTROL Schaltfläche &quot;Ungelesen markieren&quot;]**
Wenn diese Option aktiviert ist, zeigt eine 
`Mark Unread` -Schaltfläche, über die eine Nachricht als gelesen gekennzeichnet werden kann.

* **[!UICONTROL Schaltfläche &quot;Löschen&quot;]**
Wenn diese Option aktiviert ist, zeigt eine 
`Delete`-Schaltfläche, über die eine Nachricht als gelesen gekennzeichnet werden kann. Dupliziert die Löschfunktion, wenn **`Message Options`** ebenfalls aktiviert ist.

* **[!UICONTROL Nachrichtenoptionen]**
Wenn diese Option aktiviert ist, wird angezeigt. 
**`Reply`**, **`Reply All`**, **`Forward`** und **`Delete`** Schaltflächen zum erneuten Senden oder Löschen einer Nachricht. Dupliziert die Löschfunktion, wenn **`Delete Button`** ebenfalls aktiviert ist.

* **[!UICONTROL Nachrichten pro Seite]** Die angegebene Zahl entspricht der maximalen Anzahl von Nachrichten, die bei einer Aufteilung in Seiten pro Seite angezeigt wird. Ist keine Anzahl festgelegt (leeres Feld), werden alle Nachrichten auf einer Seite angezeigt.

* **[!UICONTROL Zeitstempelmuster]** Stellen Sie für eine oder mehrere Sprachen Zeitstempelmuster bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

* **[!UICONTROL Benutzer anzeigen]**
Wählen Sie entweder 
**`Sender`** oder **`Recipients`** um zu bestimmen, ob der Absender oder die Empfänger angezeigt werden sollen.

### Konfigurieren der Nachricht erstellen {#configuring-compose-message}

Um die Konfiguration der Seite mit der Nachricht zum Erstellen zu ändern, öffnen Sie die Site in [Bearbeitungsmodus des Autors](sites-console.md#authoring-site-content).

In `Preview`-Modus, wählen Sie die **[!UICONTROL Nachrichten]** -Link, um die Hauptseite der Nachrichten zu öffnen. Wählen Sie dann die Schaltfläche Neue Nachricht aus, um die `Compose Message` Seite..

In `Edit` -Modus wählen Sie die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.

Um auf das Konfigurationsdialogfeld zugreifen zu können, muss die Vererbung durch Auswahl der `link`Symbol.

Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl der `broken link` Symbol.

![chlimage_1-400](assets/chlimage_1-400.png)

Sobald die Vererbung abgebrochen wurde, kann die `configure` -Symbol, um das Konfigurationsdialogfeld zu öffnen.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Registerkarte &quot;Allgemein&quot; {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL URL-Weiterleitung]** Geben Sie die URL der Seite ein, die nach dem Versenden der Nachricht angezeigt werden soll. Beispiel: 
`../messaging.html`.

* **[!UICONTROL URL abbrechen]** Geben Sie die URL der Seite ein, die angezeigt werden soll, wenn der Sender das Verfassen einer Nachricht abbricht. Beispiel: 
`../messaging.html`.

* **[!UICONTROL Maximale Länge des Nachrichtenbetreffs]** Die maximal zulässige Anzahl der Zeichen im Feld „Betreff“. Beispiel: 500. Der Standardwert ist keine Begrenzung.

* **[!UICONTROL Maximale Länge des Nachrichtentextes]** Die maximal zulässige Anzahl der Zeichen im Feld „Inhalt“. Beispielsweise 10000. Der Standardwert ist keine Begrenzung.

* **[!UICONTROL Dienstauswahl]**
(*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft fest. **`serviceSelector.name`** von [AEM Communities Messaging-Dienst](messaging.md#messaging-operations-service).

#### Registerkarte &quot;Anzeige&quot; {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Feld anzeigen]**
Wenn diese Option aktiviert ist, zeigen Sie die 
`Subject` und aktivieren Sie die Option Betreff zur Nachricht hinzufügen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Betreffbezeichnung]**
Geben Sie den Text ein, der neben dem 
`Subject` field. Der Standardwert ist `Subject`.

* **[!UICONTROL Feld für Dateianhang anzeigen]**
Wenn diese Option aktiviert ist, zeigen Sie die 
`Attachment` und aktivieren Sie das Hinzufügen von Dateianlagen zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Dateinamen anhängen]**
Geben Sie den Text ein, der neben dem 
`Attachment` -Feld. Der Standardwert ist **`Attach File`**.

* **[!UICONTROL Inhaltsfeld anzeigen]**
Wenn diese Option aktiviert ist, zeigen Sie die 
`Content` und aktivieren Sie das Hinzufügen eines Nachrichtentextes. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Inhaltsbezeichnung]**
Geben Sie den Text ein, der neben dem 
`Content` -Feld. Der Standardwert ist **`Body`**.

* **[!UICONTROL Mit Rich-Text-Editor]** Ist diese Option aktiviert, kann ein benutzerdefiniertes „Inhalt“-Textfeld verwendet werden, das über einen eigenen Rich-Text-Editor verfügt. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zeitstempelmuster]** Stellen Sie für eine oder mehrere Sprachen Zeitstempelmuster bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.
