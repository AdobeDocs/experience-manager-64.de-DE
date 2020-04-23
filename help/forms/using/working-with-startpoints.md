---
title: Arbeiten mit Startpunkten
seo-title: Arbeiten mit Startpunkten
description: Schritte zum Arbeiten mit einem AEM Forms-Prozess von Ihrem in Workbench definierten Mobilgerät aus.
seo-description: Schritte zum Arbeiten mit einem AEM Forms-Prozess von Ihrem in Workbench definierten Mobilgerät aus.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f

---


# Arbeiten mit Startpunkten {#working-with-startpoints}

Ein Startpunkt ruft einen in der Workbench erstellten Prozess auf. Ein ist mit einem Formular verknüpft, über das der Prozess aufgerufen wird, wenn das Formular gesendet wird. Genauere Informationen zu Prozessen finden Sie unter [Schrittweise Anleitung für die Geometrixx Finance-Referenz-Website](/help/forms/using/finance-reference-site-walkthrough.md).

>[!NOTE]
>
>Die Begriffe „Startpunkte“, „Startprozess“ und „Formular“ werden wechselweise verwendet, wenn von diesem Konzept die Rede ist.

To initiate a process from the AEM Forms app, you need to have a startpoint of type **Workspace** in your process. Außerdem müssen Sie für den Startpunkt die Option **[!UICONTROL Visible in Mobile Workspace]** auswählen.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Starten eines in Workbench definierten Prozesses**

1. Um die in der AEM Forms-App verfügbaren Startpunkte anzuzeigen, gehen Sie zum [Startbildschirm](/help/forms/using/home-screen.md).
1. On the **[!UICONTROL Home]** screen, by default, the **[!UICONTROL All Forms]** list is displayed.

   Der Startpunkt ist mit einem Formular verknüpft. Tippen Sie auf das mit dem Startpunkt verknüpfte Formular in der Liste, um es zu öffnen.

   Das mit dem Startpunkt verknüpfte Formular wird geöffnet.

1. Geben Sie die Details in das Formular für den **[!UICONTROL Startpunkt]** ein.

   Sie können dieser Aufgabe mithilfe der Schaltfläche[ Anlage](/help/forms/using/add-attachments.md) Anmerkungen hinzufügen.

1. Nachdem Sie das Formular ausgefüllt haben, tippen Sie auf **Senden.**

Wenn die App offline ist, werden das Formular und die Daten im Ordner „Outbox“ gespeichert.

Wenn die App online ist, wird die Aufgabe mit dem AEM Forms-Server synchronisiert und dem im Prozess angegebenen Benutzer zugewiesen.

Informationen zum Bearbeiten der Aufgabe in Ihrer Aufgabenliste finden Sie unter [Öffnen einer Aufgabe](/help/forms/using/open-task.md).
