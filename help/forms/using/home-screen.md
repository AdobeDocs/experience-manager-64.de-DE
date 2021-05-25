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
exl-id: b8f515fd-7ab7-4237-9a35-2840f708e856
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 83%

---

# Startbildschirm  {#home-screen}

Wenn Sie sich bei der AEM Forms-App anmelden, werden Sie zum Startbildschirm weitergeleitet.

## Standardstartbildschirm  {#default-home-screen}

Auf dem Startbildschirm werden standardmäßig alle Formulare einschließlich Startpunkte und Aufgaben (wenn der verknüpfte Server mit dem Arbeitsablauf für AEM Forms aktiviert ist) zusammen mit den zugehörigen Miniaturbildern angezeigt. Sie können die Miniaturen im AEM Forms-Server angeben.

In der folgenden Abbildung werden die wichtigsten Komponenten auf dem standardmäßigen Startbildschirm mit Anmerkungen erläutert.
![Startbildschirm ](assets/home-screen-1.png)
[der Forms-AppVergrößern](assets/home-screen-1-1.png)

1. **Menüschaltfläche**: Tippen Sie auf die  **** Schaltfläche &quot;Menubution&quot;, um zu Aufgaben, Forms, Postausgang und Einstellungen zu navigieren. Wenn Ihre AEM Forms-App mit einem AEM Forms JEE-Server verbunden ist, wird die Option „Aufgaben“ angezeigt. Die Option „Aufgaben“ speichert auch die Entwürfe, die aus Aufgaben in einem Prozess erstellt wurden. Beim AEM Forms OSGi-Server ist die Option „Aufgaben“ ausgeblendet. Im Postausgang werden die gespeicherten Formulare und Entwürfe vor der Synchronisierung mit dem Server abgelegt. Alle im Postausgang gespeicherten Formulare und Entwürfe werden auf den AEM Forms-Server hochgeladen, wenn die App [mit dem Server](/help/forms/using/sync-app.md) synchronisiert wird. Weitere Informationen zu den Einstellungen finden Sie unter [Aktualisieren allgemeiner Einstellungen](/help/forms/using/update-general-settings.md).
1. **Aufgabe oder Formular**: Tippen Sie auf die aufgeführte Aufgabe oder das Formular, mit denen Sie arbeiten möchten.
1. **Horizontale Auslassungspunkte**: gibt an, dass Aktionen für das Formular zur Verfügung stehen. Beim Tippen auf die Auslassungspunkte werden die Aktionen und Beschreibungen angezeigt, die vom Autor angegeben wurden. Die Option **Entwurf löschen** und **Umfassend** ist sichtbar, wenn Sie auf die Auslassungspunkte tippen.
1. **Aktualisieren-Symbol**: Tippen Sie auf dieses Symbol, um Ihre App mit dem AEM Forms-Server zu synchronisieren.

## Anpassen des Startbildschirms  {#customizing-the-home-screen}

![Allgemeine Einstellungen](assets/gen-settings.png)

Sie können den Standardstartbildschirm der App entweder über die Registerkarte **[Allgemeine Einstellungen](/help/forms/using/update-general-settings.md)** der App oder über die Registerkarte **Einstellungen** in HTML Workspace ändern.

Die Änderung an den Einstellungen des Startbildschirms der App hat Auswirkungen auf den Startbildschirm für den derzeit angemeldeten Benutzer oder den Benutzer am aktuellen Mobilgerät.

Die in HTML Workspace vorgenommene Änderung hingegen hat Auswirkungen für alle AEM Forms-App-Benutzer, die beim AEM Forms-Server angemeldet sind.
