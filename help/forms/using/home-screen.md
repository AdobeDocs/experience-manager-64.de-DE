---
title: Startbildschirm
seo-title: Startbildschirm
description: Beschreibung der Komponenten des Startbildschirms in der AEM Forms-App
seo-description: Beschreibung der Komponenten des Startbildschirms in der AEM Forms-App
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
translation-type: tm+mt
source-git-commit: 79dcf6816e1156604c0c9279b727ea436ad1826a
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 83%

---


# Startbildschirm {#home-screen}

Wenn Sie sich bei der AEM Forms-App anmelden, werden Sie zum Startbildschirm weitergeleitet.

## Standardstartbildschirm {#default-home-screen}

Auf dem Startbildschirm werden standardmäßig alle Formulare einschließlich Startpunkte und Aufgaben (wenn der verknüpfte Server mit dem Arbeitsablauf für AEM Forms aktiviert ist) zusammen mit den zugehörigen Miniaturbildern angezeigt. Sie können die Miniaturen im AEM Forms-Server angeben.

In der folgenden Abbildung werden die wichtigsten Komponenten auf dem standardmäßigen Startbildschirm mit Anmerkungen erläutert.
![Startbildschirm](assets/home-screen-1.png)der Forms-App[Zum Vergrößern klicken](assets/home-screen-1-1.png)

1. **Menüschaltfläche**: Tippen Sie auf die **Menüschaltfläche** , um zu Aufgaben, Formularen, Postausgang und Einstellungen zu navigieren. Wenn Ihre AEM Forms-App mit einem AEM Forms JEE-Server verbunden ist, wird die Option „Aufgaben“ angezeigt. Die Option „Aufgaben“ speichert auch die Entwürfe, die aus Aufgaben in einem Prozess erstellt wurden. Beim AEM Forms OSGi-Server ist die Option „Aufgaben“ ausgeblendet. Im Postausgang werden die gespeicherten Formulare und Entwürfe vor der Synchronisierung mit dem Server abgelegt. All saved forms and drafts in the Outbox are uploaded to the AEM Forms server when the app is [synchronized with the server](/help/forms/using/sync-app.md). Weitere Informationen zu den Einstellungen finden Sie unter [Aktualisieren allgemeiner Einstellungen](/help/forms/using/update-general-settings.md).
1. **Aufgabe oder Formular**: Tippen Sie auf die aufgeführte Aufgabe oder das Formular, mit denen Sie arbeiten möchten.
1. **Horizontale Auslassungspunkte**: gibt an, dass Aktionen für das Formular zur Verfügung stehen. Beim Tippen auf die Auslassungspunkte werden die Aktionen und Beschreibungen angezeigt, die vom Autor angegeben wurden. The **Delete Draft** and **Complete** option is visible when you tap the ellipsis.
1. **Aktualisieren-Symbol**: Tippen Sie auf dieses Symbol, um Ihre App mit dem AEM Forms-Server zu synchronisieren.

## Anpassen des Startbildschirms {#customizing-the-home-screen}

![Allgemeine Einstellungen](assets/gen-settings.png)

Sie können den Standardstartbildschirm der App entweder über die Registerkarte **[Allgemeine Einstellungen](/help/forms/using/update-general-settings.md)**der App oder über die Registerkarte **Einstellungen**in HTML Workspace ändern.

Die Änderung an den Einstellungen des Startbildschirms der App hat Auswirkungen auf den Startbildschirm für den derzeit angemeldeten Benutzer oder den Benutzer am aktuellen Mobilgerät.

Die in HTML Workspace vorgenommene Änderung hingegen hat Auswirkungen für alle AEM Forms-App-Benutzer, die beim AEM Forms-Server angemeldet sind.

