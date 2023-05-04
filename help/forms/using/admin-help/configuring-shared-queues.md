---
title: Konfigurieren freigegebener Warteschlangen
seo-title: Configuring Shared Queues
description: Mit freigegebenen Warteschlangen können Sie Benutzerwarteschlangen effektiv konfigurieren und verwalten. Erfahren Sie, wie Sie freigegebene Warteschlangen konfigurieren.
seo-description: Shared Queues allow you to configure and manage user queues effectively. Learn how to configure shared queues.
uuid: 69ab611d-334b-40a5-bd2d-533d4cb25eda
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fc403a60-b635-4334-9bf8-2f3d2036b2f3
exl-id: 40890db3-240c-4021-967a-b6b3eb1d4b7c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 7%

---

# Konfigurieren freigegebener Warteschlangen{#configuring-shared-queues}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit freigegebenen Warteschlangen können Sie Benutzerwarteschlangen effektiv konfigurieren und verwalten. Eine Benutzerwarteschlange ist einfach alle einem Benutzer zugewiesenen Aufgaben, siehe [Aufgabenlisten](https://help.adobe.com/de_DE/livecycle/11.0/WorkspaceHelp/WS92d06802c76abadb-2b6ab502126beb6ba2f-7ffc.2.html) für weitere Informationen. Sie können Benutzerwarteschlangen entsprechend Ihren organisatorischen Anforderungen zuweisen, die Zuweisung aufheben und neu zuweisen. Sie können freigegebene Warteschlangen auf zwei Arten verwalten:

**Zugriff auf einen Benutzer verwalten**

Mit dieser Option können Sie den Zugriff auf eine ausgewählte Benutzerwarteschlange verwalten.

**Zugriff durch Benutzer verwalten**

Mit dieser Option können Sie freigegebene Warteschlangen verwalten, die einem ausgewählten Benutzer zugewiesen sind.

## Zugriff auf ausgewählte Benutzerwarteschlangen verwalten {#managing-access-to-a-selected-user-queue}

Mit der Funktion Zugriff auf einen Benutzer verwalten können Sie den Zugriff auf eine ausgewählte Benutzerwarteschlange verwalten. Sie können anderen Benutzern in Ihrer Organisation Zugriff auf eine ausgewählte Benutzerwarteschlange gewähren oder sperren. Zum Beispiel ist Kara Bowman nicht im Amt. Mithilfe der Funktion Zugriff auf einen Benutzer verwalten kann ihre Warteschlange für Akira Tanaka und John Jacobs freigegeben werden, um sie abzuschließen. Wenn Kara Bowman später ins Büro zurückkehrt, können Sie den Zugriff auf ihre Warteschlange von Akira Tanaka und John Jacobs widerrufen.

Nach der Freigabe können diese Aufgaben vom Benutzer mithilfe von Workspace mit Zugriff auf die Warteschlange abgeschlossen werden.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

### Zugriff auf eine ausgewählte Benutzerwarteschlange konfigurieren {#configuring-access-to-a-selected-user-queue}

1. Melden Sie sich mit einem Administratorkonto bei Administration Console an.
1. Auswählen **Dienste** > **Arbeitsablauf für Formulare** > **Freigegebene Warteschlange**.

1. Wählen Sie auf der Registerkarte Zugriff auf einen Benutzer verwalten den Benutzer aus, dessen Warteschlange Sie freigeben möchten. Das untere rechte Fenster zeigt die Liste der Benutzer an, die Zugriff auf die ausgewählte Benutzerwarteschlange haben.
1. Wählen Sie im unteren linken Bereich den Benutzer aus. Klicken Sie auf „Freigeben“.
1. Klicken Sie zum Abschluss auf Speichern .

### Zugriff auf ausgewählte Benutzerwarteschlangen sperren {#revoking-access-to-a-selected-user-queue}

1. Melden Sie sich mit einem Administratorkonto bei Administration Console an.
1. Auswählen **Dienste** > **Arbeitsablauf für Formulare** > **Freigegebene Warteschlange**.

1. Wählen Sie auf der Registerkarte Zugriff auf einen Benutzer verwalten den Benutzer aus, dessen Warteschlange Sie verwalten möchten.
1. Im unteren rechten Bereich wird die Liste der Benutzer mit Zugriff auf die ausgewählte Benutzerwarteschlange angezeigt. Wählen Sie den Benutzer aus und klicken Sie auf Sperren .
1. Klicken Sie zum Abschluss auf Speichern .

## Verwalten von Warteschlangen, die einem Benutzer zugewiesen sind {#managing-queues-assigned-to-a-user}

Mit der Funktion Zugriff von einem Benutzer verwalten können Sie Warteschlangen verwalten, die einem ausgewählten Benutzer zugewiesen sind. Sie können einem ausgewählten Benutzer einzeln Zugriff auf Benutzerwarteschlangen gewähren oder sperren. Sie möchten beispielsweise Kara Bowman Benutzerwarteschlangen für Akira Tanaka und John Jacobs zuweisen. Mithilfe der Funktion Zugriff von einem Benutzer verwalten können Sie nach Kara Bowman suchen und Zugriff auf Aufgaben gewähren, die Akira Tanaka und John Jacobs zugewiesen sind. Zu einem späteren Zeitpunkt können Sie den Zugriff von Kara Bowman auf diese Benutzerwarteschlangen widerrufen.

Nach der Zuweisung können diese Aufgaben vom Benutzer, der Workspace verwendet, ausgeführt werden.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

### Zugriff auf eine ausgewählte Benutzerwarteschlange gewähren {#granting-access-to-a-selected-user-queue}

1. Melden Sie sich mit einem Administratorkonto bei Administration Console an.
1. Auswählen **Dienste** > **Arbeitsablauf für Formulare** > **Freigegebene Warteschlange**.

1. Wählen Sie auf der Registerkarte Zugriff auf einen Benutzer verwalten den Benutzer aus, dessen Warteschlange Sie freigeben möchten. Das untere rechte Fenster zeigt die Liste der Benutzer an, die Zugriff auf die ausgewählte Benutzerwarteschlange haben.
1. Wählen Sie im unteren linken Bereich Benutzerwarteschlangen aus, die Sie für den ausgewählten Benutzer freigeben möchten. Klicken Sie auf „Freigeben“.
1. Klicken Sie zum Abschluss auf Speichern .

### Zugriff auf ausgewählte Benutzerwarteschlangen sperren {#revoking_access_to_a_selected_user_queue-1}

1. Melden Sie sich mit einem Administratorkonto bei Administration Console an.
1. Auswählen **Dienste** > **Arbeitsablauf für Formulare** > **Freigegebene Warteschlange**.

1. Wählen Sie auf der Registerkarte Zugriff von einem Benutzer verwalten den Benutzer aus, dessen Warteschlange Sie verwalten möchten.
1. Im unteren rechten Bereich wird die Liste der Benutzerwarteschlangen angezeigt, die dem ausgewählten Benutzer zugewiesen sind. Wählen Sie die Benutzerwarteschlange aus und klicken Sie auf &quot;Sperren&quot;.
1. Klicken Sie zum Abschluss auf Speichern .
