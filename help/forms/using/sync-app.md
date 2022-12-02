---
title: Synchronisieren der App
seo-title: Synchronizing the app
description: Synchronisieren Sie die AEM Forms-App auf Ihrem mobilen Gerät mit dem AEM Forms-Server.
seo-description: Synchronize the AEM Forms app on your mobile device with the AEM Forms server.
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
exl-id: b5681fe5-69ba-4fc0-95e3-6ffdcdd95382
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 100%

---

# Synchronisieren der App {#synchronizing-the-app}

## Synchronisieren der App {#synchronizing-the-app-1}

Die Formulare in Ihrer App werden vom AEM Forms-Server heruntergeladen. Die Formulare werden unter den Registerkarten „Aufgaben“ und „Formulare“ heruntergeladen. Die Entwürfe, die aus Formularen erstellt wurden, werden auf der Registerkarte „Entwürfe“ herunterladen und die Entwürfe, die aus Aufgaben erstellt wurden, werden auf der Registerkarte „Aufgaben“ heruntergeladen. Für ein eigenständiges Formular auf dem OSGi-Server werden Formulare und Entwürfe auf den Registerkarten „Formulare“ bzw. „Entwurf“ heruntergeladen.

Wenn Sie ein Formular ausfüllen und senden, wird das Formular sofort auf den AEM Forms-Server hochgeladen, wenn die App online ist. Beim Synchronisieren der App werden die Formulare vom Server abgerufen. Die Entwürfe werden jedoch sofort mit dem Server synchronisiert, wenn die App online ist.

Wenn Sie mit dem AEM Forms-Server online sind, wird Ihre App standardmäßig alle 15 Minuten synchronisiert. Sie haben jedoch die Möglichkeit, die Häufigkeit der Synchronisierung zu ändern. Und Sie können die App auch jederzeit manuell synchronisieren.

**Manuelles Synchronisieren der App**

Tippen Sie in der rechten unteren Ecke des Startbildschirms auf das Synchronisierungsschaltfläche ![Mobile App synchronisieren](assets/sync-app.png).

**Ändern der Synchronisierungsfrequenz**

1. Um den Einstellungsbildschirm aufzurufen, tippen Sie links oben auf dem Startbildschirm auf die Menüschaltfläche und dann auf **Einstellungen**.
1. Tippen Sie auf dem Bildschirm „Einstellungen“ auf die Registerkarte „General“.

   ![Einstellung der Synchronisierungsfrequenz im Fenster „Allgemeine Einstellungen“](assets/gen-settings-1.png)

1. Tippen Sie für die Option „Sync frequency“ auf den Wert rechts neben „Sync frequency“. 
1. Wählen Sie in der Dropdown-Liste die neue Synchronisierungshäufigkeit aus.

### Technische Spezifikationen {#technical-specifications}

* Die Hauptlogik zum Übertragen der Offline-Daten der App an den AEM Forms-Server ist in „runtime/offline/util/offline.js“ enthalten.
* In der .js sendet ein Aufruf der Funktion „processOfflineSubmittedSavedTasks(...)“ die gespeicherten bzw. übermittelten Aufgaben an den Server. Darüber hinaus werden Fehler bei der Synchronisierung behandelt. Wenn bei der Übermittlung einer Aufgabe ein Fehler auftritt, wird die Aufgabe in der App als fehlerhaft markiert. Darüber hinaus verbleibt die Aufgabe in der Outbox.
* Die Funktionen „syncSubmittedTask()“ und „syncSavedTask()“ führen Vorgänge für einzelne Aufgaben durch.
* Der Aufruf der Funktion „processOfflineSubmittedSavedTasks()“ wird durch die Aufgabenlistenkomponente ausgelöst, nachdem ein Benutzer die Synchronisierung des Offline-Status mit dem Server oder eine automatische Synchronisierung über den Hintergrund-Thread ausgewählt hat.
