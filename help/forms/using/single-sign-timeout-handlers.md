---
title: Single Sign-On und Zeitüberschreitungshandler
seo-title: Single Sign On and timeout handlers
description: Gehen Sie wie folgt vor, um einen Sitzungs-Timeout-Wert für AEM Forms festzulegen.
seo-description: How-to set the session timeout value for AEM Forms workspace.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
exl-id: eb7afdd3-0901-4dfb-b23c-88c46b5a4fb5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 43%

---

# Single Sign-On und Zeitüberschreitungshandler {#single-sign-on-and-timeout-handlers}

AEM Forms Workspace ist SSO-fähig. Wenn sich ein Benutzer bei einer AEM Forms-Anwendung wie Forms Manager oder PDF Generator angemeldet hat und in derselben Browsersitzung auf AEM Forms Workspace zugreift, wird der Benutzer bei AEM Forms Workspace angemeldet und umgekehrt.

## Das Bearbeiten des Serverzeitlimits in AEM Forms bildet Arbeitsbereich {#handling-server-timeout-in-nbsp-aem-forms-workspace}

Sitzungs-Timeouts für einen Benutzer können in der Administration Console konfiguriert werden.

Um die Zeitüberschreitung festzulegen, melden Sie sich bei an `https://[server]:[port]/adminui`, navigieren Sie zu **Einstellungen > User Management > Konfiguration > Erweiterte Systemattribute konfigurieren** und nehmen Sie die gewünschten Einstellungen vor.

Die Zeitüberschreitung in AEM Forms Workspace wird wie folgt gehandhabt:

* Sitzungsdauer für einen Benutzer ist als Antwort auf `initialize` -Aufruf, der die Benutzersitzung initialisiert.
* Ein Popup-Fenster informiert den Benutzer 15 Sekunden im Voraus, dass die Sitzung gleich ablaufen wird.

In diesem Popup-Dialog:

* Klicken Sie auf „OK“, um die Benutzersitzung zu beenden.
* Klicken Sie auf „Abbrechen“, um die Benutzersitzung neu zu initialisieren.

>[!NOTE]
>
>Wenn keine Aktion ausgeführt wird, wird der Benutzer drei Sekunden vor Ablauf der Sitzung automatisch von AEM Forms Workspace abgemeldet.
