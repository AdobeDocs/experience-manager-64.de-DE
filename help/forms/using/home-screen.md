---
title: Startbildschirm
seo-title: Home screen
description: Beschreibung der Komponenten des Startbildschirms der AEM Forms-App
seo-description: Description of the components of the AEM Forms app Home screen
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
exl-id: b8f515fd-7ab7-4237-9a35-2840f708e856
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 26%

---

# Startbildschirm {#home-screen}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Sie sich bei der AEM Forms-App anmelden, werden Sie zum Startbildschirm weitergeleitet.

## Standardstartbildschirm {#default-home-screen}

Standardmäßig werden auf dem Startbildschirm alle Formulare einschließlich Startpunkten und Aufgaben (wenn der verbundene Server AEM Forms Workflow aktiviert ist) zusammen mit den zugehörigen Miniaturansichten angezeigt. Sie können die Miniaturansichten auf dem AEM Forms-Server angeben.

In der folgenden Abbildung werden die wichtigsten Komponenten auf dem standardmäßigen Startbildschirm mit Anmerkungen erläutert.
![Startbildschirm der Forms-App](assets/home-screen-1.png)
[Klicken Sie zum Vergrößern auf](assets/home-screen-1-1.png)

1. **Menüschaltfläche**: Tippen Sie auf die Schaltfläche **Menü**, um zu Aufgaben, Formularen, Posteingang und Einstellungen zu navigieren. Wenn Ihre AEM Forms-App mit einem AEM Forms JEE-Server verbunden ist, wird die Option &quot;Aufgaben&quot;angezeigt. Die Option Aufgaben speichert auch die Entwürfe, die aus Aufgaben in einem Prozess erstellt wurden. Bei AEM Forms OSGi-Servern ist die Option &quot;Aufgaben&quot;ausgeblendet. Der Postausgang speichert die gespeicherten Formulare und Entwürfe, bevor sie mit dem Server synchronisiert werden. Alle gespeicherten Formulare und Entwürfe werden im Postausgang gespeichert und auf den AEM Forms-Server hochgeladen, wenn die App [mit dem Server synchronisiert wird. ](/help/forms/using/sync-app.md) Weitere Informationen zu den Einstellungen finden Sie unter [Aktualisieren allgemeiner Einstellungen](/help/forms/using/update-general-settings.md).
1. **Aufgabe oder Formular**: Tippen Sie auf die aufgelistete Aufgabe oder das Formular, mit der Sie arbeiten möchten.
1. **Horizontale Ellipse**: Gibt an, dass Aktionen für das Formular verfügbar sind. Durch Tippen auf die Auslassungspunkte werden die Aktionen und Beschreibungen angezeigt, die der Autor bereitgestellt hat. Die Optionen **Entwurf löschen** und **Abgeschlossen** sind nur sichtbar, wenn Sie auf die Auslassungspunkte tippen.
1. **Aktualisierungssymbol**: Tippen Sie auf das Aktualisierungssymbol, um Ihre App mit dem AEM Forms-Server zu synchronisieren.

## Anpassen des Startbildschirms {#customizing-the-home-screen}

![Allgemeine Einstellungen](assets/gen-settings.png)

Sie können den Standardstartbildschirm der App entweder über die Registerkarte **[Allgemeine Einstellungen](/help/forms/using/update-general-settings.md)** der App oder über die Registerkarte **Einstellungen** in HTML Workspace ändern.

Die Änderung an der Einstellung des Startbildschirms in der App wirkt sich auf den Startbildschirm für den aktuellen angemeldeten Benutzer oder den Benutzer auf dem aktuellen Mobilgerät aus.

Die in HTML Workspace vorgenommene Änderung wirkt sich jedoch auf alle AEM Forms-App-Benutzer aus, die beim AEM Forms-Server angemeldet sind.
