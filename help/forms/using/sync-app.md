---
title: Synchronisieren der App
seo-title: Synchronizing the app
description: Synchronisieren Sie die AEM Forms-App auf Ihrem Mobilgerät mit dem AEM Forms-Server.
seo-description: Synchronize the AEM Forms app on your mobile device with the AEM Forms server.
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
exl-id: b5681fe5-69ba-4fc0-95e3-6ffdcdd95382
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 19%

---

# Synchronisieren der App {#synchronizing-the-app}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Synchronisieren der App {#synchronizing-the-app-1}

Die Formulare in Ihrer App werden vom AEM Forms-Server heruntergeladen. Die Formulare werden auf den Registerkarten Aufgaben und Forms heruntergeladen. Entwürfe, die aus Formularen erstellt wurden, werden auf die Registerkarte &quot;Entwürfe&quot;heruntergeladen und Entwürfe, die aus Aufgaben erstellt wurden, werden auf die Registerkarte &quot;Aufgaben&quot;heruntergeladen. Für ein eigenständiges Formular auf dem OSGi-Server werden Formulare und Entwürfe auf den Registerkarten &quot;Forms&quot;bzw. &quot;Entwurf&quot;heruntergeladen.

Wenn Sie ein Formular ausfüllen und senden, wird das Formular sofort auf den AEM Forms-Server hochgeladen, wenn die App online ist. Die Formulare werden beim Synchronisieren der App vom Server abgerufen. Die Entwürfe werden jedoch sofort mit dem Server synchronisiert, wenn die App online ist.

Wenn Sie mit dem AEM Forms-Server online sind, wird Ihre App standardmäßig alle 15 Minuten synchronisiert. Sie haben jedoch die Möglichkeit, die Synchronisierungshäufigkeit zu ändern. Alternativ können Sie die App jederzeit manuell synchronisieren.

**Manuelles Synchronisieren der App**

Tippen Sie in der rechten unteren Ecke des Startbildschirms auf das Synchronisierungsschaltfläche ![Mobile App synchronisieren](assets/sync-app.png).

**Ändern der Synchronisierungshäufigkeit**

1. Um zum Einstellungsbildschirm zu gelangen, tippen Sie auf die Menüschaltfläche in der linken oberen Ecke des Startbildschirms und dann auf **Einstellungen**.
1. Tippen Sie im Bildschirm &quot;Einstellungen&quot;auf die Registerkarte Allgemein .

   ![Einstellung der Synchronisierungsfrequenz im Fenster „Allgemeine Einstellungen“](assets/gen-settings-1.png)

1. Tippen Sie bei der Option Synchronisierungsfrequenz auf den Wert rechts neben Synchronisierungsfrequenz.
1. Wählen Sie in der Dropdown-Liste die neue Synchronisierungshäufigkeit aus.

### Technische Spezifikationen {#technical-specifications}

* Die Hauptlogik zum Senden der Offline-App-Daten an den AEM Forms-Server ist in runtime/offline/util/offline.js enthalten.
* In der .js sendet der Aufruf der Funktion &quot;processOfflineSubmittedSavedTasks(...)&quot;die gespeicherten/gesendeten Aufgaben an den Server. Außerdem werden alle Fehler oder Konflikte im Synchronisierungsprozess behandelt. Wenn die Übermittlung einer Aufgabe fehlschlägt, wird die Aufgabe auf der App als fehlgeschlagen markiert. Darüber hinaus bleibt die Aufgabe in Ihrem Postausgang.
* Die Funktionen syncSubmittedTask() und syncSavedTask() führen Vorgänge für einzelne Aufgaben durch.
* Der Aufruf der Funktion &quot;processOfflineSubmittedSavedTasks()&quot;wird von der Aufgabenlistenkomponente initiiert, nachdem ein Benutzer die Synchronisierung des Offline-Status mit dem Server oder eine automatische Synchronisierung durch den Hintergrund-Thread ausgewählt hat.
