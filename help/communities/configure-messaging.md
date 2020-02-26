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

---


# Messaging-Funktion {#messaging-feature}

Zusätzlich zu den öffentlich sichtbaren Interaktionen, die in Foren und Kommentaren auftreten, ermöglicht die Messaging-Funktion von AEM Communities Community es Community-Mitgliedern, privat miteinander zu interagieren.

This feature may be included when a [community site](overview.md#communitiessites) is created.

Die Messaging-Funktion bietet Folgendes:

* Senden einer Nachricht an ein oder mehrere Community-Mitglieder
* Eine Nachricht an eine Community-Mitgliedsgruppe senden
* Eine Nachricht mit Anlagen senden
* Weiterleiten einer Nachricht
* Antwort auf eine Nachricht
* Eine Nachricht löschen
* Wiederherstellen einer gelöschten Meldung

Um die Messaging-Funktion zu aktivieren und zu ändern, besuchen Sie

* [Messaging](messaging.md) für Administratoren konfigurieren
* [Messaging Essentials](essentials-messaging.md) für Entwickler

>[!NOTE]
>
>Es wird nicht unterstützt, `Compose Message, Message, or Message List` Komponenten (in der `Communities`Komponentengruppe) einer Seite im Bearbeitungsmodus des Autors hinzuzufügen.

## Messaging-Komponenten konfigurieren {#configuring-messaging-components}

Wenn Messaging für eine Community-Site aktiviert ist, ist es vollständig eingerichtet und es ist keine weitere Konfiguration erforderlich. Diese Informationen werden bereitgestellt, wenn die Standardkonfiguration geändert werden muss.

### Nachrichtenliste konfigurieren (messageBox) {#configuring-message-list-messagebox}

Um die Konfiguration der Liste der Nachrichten für **Posteingang**-, **Gesendete Elemente**- und **Papierkorb** -Seiten der Nachrichtenfunktion zu ändern, öffnen Sie die Site im [Autorenbearbeitungsmodus](sites-console.md#authoring-site-content).

Wählen Sie im `Preview` Modus den Link &quot; **[!UICONTROL Nachrichten]** &quot;, um die Haupt-Messaging-Seite zu öffnen. Wählen Sie dann entweder &quot; **[!UICONTROL Posteingang&quot;, &quot;Gesendete Elemente&quot;oder &quot;Papierkorb]** &quot;, um die Komponente für diese Nachrichtenliste zu konfigurieren.

Wählen Sie im `Edit` Modus die Komponente auf der Seite aus.

Um auf das Konfigurationsdialogfeld zugreifen zu können, müssen Sie die Vererbung abbrechen, indem Sie das `link`Symbol auswählen.

Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des `broken link` Symbols wiederhergestellt werden.

![chlimage_1-396](assets/chlimage_1-396.png)

Nach dem Abbrechen der Vererbung können Sie das Symbol auswählen, um das Konfigurationsdialogfeld zu öffnen. `configure` .

![chlimage_1-397](assets/chlimage_1-397.png)

#### Basic tab {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Dienstauswahl]**(*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft `serviceSelector.name` aus dem [AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service)fest.

* **[!UICONTROL Seite]** erstellen (*Erforderlich*) Die Seite, die geöffnet wird, wenn ein Mitglied auf die `Reply` Schaltfläche klickt. Die Zielseite sollte das Formular **[!UICONTROL Nachricht erstellen]** enthalten.

* **[!UICONTROL Als Ressource antworten/anzeigen]** Ist diese Option aktiviert, verweisen die Antwort- und Ansichts-URL auf eine Ressource. Ist sie nicht aktiviert, werden Daten als Abfrageparameter in der URL übermittelt. 

* **[!UICONTROL Anzeigeform für Profil]** Das Profilformular zur Anzeige des Absenderprofils.

* **[!UICONTROL Papierkorb-Ordner]** Ist die Option aktiviert, zeigt diese Nachrichtenlisten-Komponente lediglich Nachrichten an, die als gelöscht markiert wurden (Papierkorb).

* **[!UICONTROL Ordnerpfade]**(*Erforderlich*) Verweisen auf die Werte, die für `inbox.path.name` und `sentitems.path.name` im [AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service)festgelegt sind. Bei der Konfiguration für einen `Inbox`Eintrag fügen Sie einen Eintrag mit dem Wert `inbox.path.name`. Bei der Konfiguration für einen `Outbox`Eintrag fügen Sie einen Eintrag mit dem Wert `sentitems.path.name`. Fügen Sie beim Konfigurieren für `Trash`zwei Einträge mit beiden Werten hinzu.

#### Registerkarte anzeigen {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Markieren Sie die Leseschaltfläche]** Wenn diese aktiviert ist, wird eine `Read`Schaltfläche angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **[!UICONTROL &quot;Ungelesen markieren&quot;]** Wenn diese Option aktiviert ist, wird eine `Mark Unread` Schaltfläche angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **[!UICONTROL Schaltfläche]**&quot;Löschen&quot;Wenn diese Option aktiviert ist, wird eine `Delete`Schaltfläche angezeigt, mit der eine Nachricht als gelesen markiert werden kann. Will duplicate the delete functionality if **`Message Options`** is also checked.

* **[!UICONTROL Nachrichtenoptionen]** Wenn aktiviert, werden Schaltflächen **`Reply`**, **`Reply All`****`Forward`** **`Delete`** und Schaltflächen angezeigt, mit denen eine Nachricht erneut gesendet oder gelöscht werden kann. Will duplicate the delete functionality if **`Delete Button`** is also checked.

* **[!UICONTROL Nachrichten pro Seite]** Die angegebene Zahl entspricht der maximalen Anzahl von Nachrichten, die bei einer Aufteilung in Seiten pro Seite angezeigt wird. Ist keine Anzahl festgelegt (leeres Feld), werden alle Nachrichten auf einer Seite angezeigt.

* **[!UICONTROL Zeitstempelmuster]** Stellen Sie für eine oder mehrere Sprachen Zeitstempelmuster bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

* **[!UICONTROL Benutzer]** auswählen anzeigen **`Sender`** oder **`Recipients`** bestimmen, ob der Absender oder die Empfänger angezeigt werden sollen.

### Konfigurieren der Nachricht &quot;Erstellen&quot; {#configuring-compose-message}

Um die Konfiguration der Seite mit der Nachricht zum Erstellen zu ändern, öffnen Sie die Site im [Autorenbearbeitungsmodus](sites-console.md#authoring-site-content).

Wählen Sie im `Preview`Modus den Link &quot; **[!UICONTROL Nachrichten]** &quot;, um die Hauptnachrichtenseite zu öffnen. Klicken Sie dann auf &quot;Neue Nachricht&quot;, um die `Compose Message` Seite zu öffnen.

Wählen Sie im `Edit` Modus die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.

Um auf das Konfigurationsdialogfeld zugreifen zu können, müssen Sie die Vererbung abbrechen, indem Sie das `link`Symbol auswählen.

Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des `broken link` Symbols wiederhergestellt werden.

![chlimage_1-400](assets/chlimage_1-400.png)

Nach dem Abbrechen der Vererbung können Sie das Symbol auswählen, um das Konfigurationsdialogfeld zu öffnen. `configure` .

![chlimage_1-401](assets/chlimage_1-401.png)

#### Basic tab {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL URL-Weiterleitung]** Geben Sie die URL der Seite ein, die nach dem Versenden der Nachricht angezeigt werden soll. Beispiel, `../messaging.html`.

* **[!UICONTROL URL abbrechen]** Geben Sie die URL der Seite ein, die angezeigt werden soll, wenn der Sender das Verfassen einer Nachricht abbricht. Beispiel, `../messaging.html`.

* **[!UICONTROL Maximale Länge des Nachrichtenbetreffs]** Die maximal zulässige Anzahl der Zeichen im Feld „Betreff“. Beispiel: 500. Der Standardwert ist nicht begrenzt.

* **[!UICONTROL Maximale Länge des Nachrichtentextes]** Die maximal zulässige Anzahl der Zeichen im Feld „Inhalt“. Beispielsweise 10000. Der Standardwert ist nicht begrenzt.

* **[!UICONTROL Dienstauswahl]**(*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft **`serviceSelector.name`** aus dem [AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service)fest.

#### Registerkarte anzeigen {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL &quot;Betrefffeld]** anzeigen&quot; `Subject` Wenn aktiviert, zeigen Sie das Feld an und aktivieren Sie das Hinzufügen eines Betreffs zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Betreffbeschriftung]** Geben Sie den Text ein, der neben dem `Subject` Feld angezeigt werden soll. Der Standardwert ist `Subject`.

* **[!UICONTROL Dateifeld]** anhängen anzeigen Wenn aktiviert, zeigen Sie das Feld an und aktivieren Siedas Hinzufügen von Dateianlagen zur Nachricht. `Attachment` Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Dateibeschriftung]** anhängen Geben Sie den Text ein, der neben dem `Attachment` Feld angezeigt werden soll. Der Standardwert ist **`Attach File`**.

* **[!UICONTROL Inhaltsfeld]** anzeigen Wenn aktiviert, zeigen Sie das Feld an und aktivieren Sie das Hinzufügen eines Nachrichtentextes `Content` . Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Inhaltsbeschriftung]** Geben Sie den Text ein, der neben dem `Content` Feld angezeigt werden soll. Der Standardwert ist **`Body`**.

* **[!UICONTROL Mit Rich-Text-Editor]** Ist diese Option aktiviert, kann ein benutzerdefiniertes „Inhalt“-Textfeld verwendet werden, das über einen eigenen Rich-Text-Editor verfügt. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Zeitstempelmuster]** Stellen Sie für eine oder mehrere Sprachen Zeitstempelmuster bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

