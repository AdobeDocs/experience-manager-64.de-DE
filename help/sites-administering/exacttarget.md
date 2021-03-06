---
title: Integration mit ExactTarget
seo-title: Integrating with ExactTarget
description: Erfahren Sie, wie Sie AEM mit ExactTarget integrieren.
seo-description: Learn how to integrate AEM with ExactTarget.
uuid: dafa0a1a-2d1e-40fc-a729-f2ce7ebc7807
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: d1cff2bb-9fdf-49cb-a695-d437bba5653d
exl-id: 943e5199-271f-4015-a9f7-4d39c00deabe
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 77%

---

# Integration mit ExactTarget{#integrating-with-exacttarget}

Durch die Integration von AEM in Exact Target können Sie in AEM erstellten E-Mails verwalten und senden. Außerdem können Sie die Lead-Management-Funktionen von ExactTarget über AEM Formulare auf AEM Seiten verwenden.

Mit der Integration verfügen Sie über die folgenden Funktionen:

* die Möglichkeit, E-Mails in AEM zu erstellen und sie für ExactTarget für den Versand zu veröffentlichen
* die Möglichkeit, die Aktion für ein AEM-Formular festzulegen, einen ExactTarget-Abonnenten zu erstellen

Nach der Konfiguration von ExactTarget können Sie Newsletter oder E-Mails für ExactTarget veröffentlichen. Siehe [Veröffentlichen von Newslettern für einen E-Mail-Dienst](/help/sites-authoring/personalization.md).

## Erstellen einer ExactTarget-Konfiguration {#creating-an-exacttarget-configuration}

Sie können ExactTarget-Konfigurationen über Cloud-Services oder über die Tools hinzufügen. Beide Möglichkeiten werden in diesem Abschnitt beschrieben.

### Konfigurieren von ExactTarget über Cloud-Services {#configuring-exacttarget-via-cloudservices}

So erstellen Sie eine ExactTarget-Konfiguration über Cloud-Services:

1. Klicken Sie auf der Willkommensseite auf **Cloud-Services**. (Oder direkt auf unter `https://<hostname>:<port>/etc/cloudservices.html`.
1. Klicken **ExactTarget** und dann **Konfigurieren**. Das ExactTarget-Konfigurationsfenster wird geöffnet.

   ![chlimage_1-182](assets/chlimage_1-182.png)

1. Geben Sie einen Titel und optional einen Namen ein und klicken Sie auf **Erstellen**. Das Konfigurationsfenster &quot;ExactTarget-Einstellungen&quot;wird geöffnet.

   ![chlimage_1-31](assets/chlimage_1-31.jpeg)

1. Geben Sie den Benutzernamen und das Kennwort ein und wählen Sie einen API-Endpunkt aus (z. B. **https://webservice.exacttarget.com/Service.asmx**).
1. Klicken Sie auf **Mit ExactTarget verbinden.** Wenn die Verbindung erfolgreich hergestellt wurde, wird ein Dialogfeld mit dem entsprechenden Hinweis angezeigt. Klicken Sie auf **OK**, um das Fenster zu beenden.

   ![chlimage_1-32](assets/chlimage_1-32.jpeg)

1. Wählen Sie ein Konto aus, falls verfügbar. Das Konto ist für Enterprise 2.0-Kunden. Klicken Sie auf **OK**.

   ExactTarget wurde konfiguriert. Sie können die Konfiguration bearbeiten, indem Sie auf **Bearbeiten** klicken. Sie können ExactTarget aufrufen, indem Sie auf **Zu ExactTarget wechseln**.

1. AEM bietet jetzt eine Datenerweiterungsfunktion. Sie können ExactTarget-Datenerweiterungsspalten importieren. Klicken Sie zur Konfiguration auf das Pluszeichen (+), das neben der erfolgreich erstellten ExactTarget-Konfiguration angezeigt wird. Aus der Dropdown-Liste können Sie jede vorhandene Datenerweiterung auswählen. Weitere Informationen zur Konfiguration von Datenerweiterungen finden Sie in der [ExactTarget-Dokumentation](https://help.exacttarget.com/en/documentation/exacttarget/subscribers/data_extensions_and_data_relationships).

   Importierte Datenerweiterungsspalten können Sie später über die Komponente **Text und Personalisierung** nutzen.

   ![chlimage_1-33](assets/chlimage_1-33.jpeg)

### Konfigurieren von ExactTarget über die Tools {#configuring-exacttarget-via-tools}

So erstellen Sie eine ExactTarget-Konfiguration über die Tools:

1. Klicken Sie auf der Willkommensseite auf **Tools**. Oder navigieren Sie direkt dorthin, indem Sie `https://<hostname>:<port>/misadmin#/etc`.
1. Wählen Sie **Tools** > **Cloud Service-Konfigurationen** > **ExactTarget** aus.
1. Klicken **Neu** , um das Fenster &quot;Seite erstellen&quot;zu öffnen.

   ![chlimage_1-34](assets/chlimage_1-34.jpeg)

1. Geben Sie den **Titel** und optional den **Namen** ein und klicken Sie auf **Erstellen**.
1. Geben Sie die Konfigurationsinformationen ein, wie in Schritt 4 des vorherigen Verfahrens beschrieben. Befolgen Sie diesen Vorgang, um die Konfiguration von ExactTarget abzuschließen.

### Hinzufügen mehrerer Konfigurationen {#adding-multiple-configurations}

So fügen Sie mehrere Konfigurationen hinzu:

1. Klicken Sie auf der Willkommensseite auf **Cloud-Services** und dann auf **ExactTarget**. Klicken Sie auf **Konfigurationen anzeigen** -Schaltfläche, die angezeigt wird, wenn eine oder mehrere ExactTarget-Konfigurationen verfügbar sind. Alle verfügbaren Konfigurationen werden aufgeführt.
1. Klicken Sie auf das Pluszeichen (**+**) neben „Verfügbare Konfigurationen“. Das Fenster **Konfiguration erstellen** wird geöffnet. Führen Sie die Schritte des vorherigen Konfigurationsverfahrens aus, um eine neue Konfiguration zu erstellen.
