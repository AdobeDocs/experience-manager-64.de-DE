---
title: Arbeiten mit Startpunkten
seo-title: Working with Startpoints
description: Schritte zum Arbeiten mit einem AEM Forms-Prozess von Ihrem in Workbench definierten Mobilgerät aus.
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
exl-id: ef9352c7-c164-4cbf-8f18-5b97aa5f56be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 50%

---

# Arbeiten mit Startpunkten {#working-with-startpoints}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Ein Startpunkt ruft einen in der Workbench erstellten Prozess auf. Ein ist mit einem Formular verknüpft, über das der Prozess aufgerufen wird, wenn das Formular gesendet wird. Siehe [Schrittweise Anleitung zur Geometrixx Finance-Referenz-Website](/help/forms/using/finance-reference-site-walkthrough.md) um Prozesse zu verstehen.

>[!NOTE]
>
>Die Begriffe „Startpunkte“, „Startprozess“ und „Formular“ werden wechselweise verwendet, wenn von diesem Konzept die Rede ist.

Um einen Prozess aus der AEM Forms-Anwendung zu initiieren, müssen Sie einen Startpunkt des Typs **Arbeitsbereich** in Ihrem Prozess haben. Außerdem müssen Sie die **[!UICONTROL In Mobile Workspace sichtbar]** für den Startpunkt.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Starten eines in Workbench definierten Prozesses**

1. Um die in der AEM Forms-App verfügbaren Startpunkte anzuzeigen, navigieren Sie zu [Startbildschirm](/help/forms/using/home-screen.md).
1. Auf dem Bildschirm **[!UICONTROL Startseite]** wird standardmäßig die Liste **[!UICONTROL Alle Formulare]** angezeigt.

   Der Startpunkt ist mit einem Formular verknüpft. Tippen Sie in der Liste auf das mit dem Startpunkt verknüpfte Formular, um es zu öffnen.

   Das mit dem Startpunkt verknüpfte Formular wird geöffnet.

1. Geben Sie die Details in das Formular für den **[!UICONTROL Startpunkt]** ein.

   Sie können dieser Aufgabe mithilfe der Schaltfläche[ Anlage](/help/forms/using/add-attachments.md) Anmerkungen hinzufügen.

1. Nachdem Sie das Formular ausgefüllt haben, tippen Sie auf **Senden.**

Wenn die App offline ist, werden das Formular und die zugehörigen Daten im Ordner &quot;Outbox&quot;gespeichert.

Wenn die App online ist, wird die Aufgabe mit dem AEM Forms-Server synchronisiert und dem im Prozess angegebenen Benutzer zugewiesen.

Informationen zum Arbeiten mit der Aufgabe in der Aufgabenliste finden Sie unter [Öffnen einer Aufgabe](/help/forms/using/open-task.md).
