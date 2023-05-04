---
title: Single Sign-On und Zeitüberschreitungs-Handler
seo-title: Single Sign On and timeout handlers
description: So legen Sie den Wert für das Sitzungs-Timeout für AEM Forms Workspace fest.
seo-description: How-to set the session timeout value for AEM Forms workspace.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
exl-id: eb7afdd3-0901-4dfb-b23c-88c46b5a4fb5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 56%

---

# Single Sign-On und Zeitüberschreitungs-Handler {#single-sign-on-and-timeout-handlers}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM Forms Workspace ist SSO-aktiviert. Wenn sich ein Benutzer bei einer AEM Forms-Anwendung wie Forms Manager, der PDF Generator-Benutzeroberfläche oder AEM Forms-Arbeitsbereich angemeldet hat und in derselben Browsersitzung auf AEM Forms-Arbeitsbereich zugreift, wird der Benutzer bei AEM Forms-Arbeitsbereich angemeldet und umgekehrt.

## Umgang mit Server-Timeouts in AEM Forms Workspace {#handling-server-timeout-in-nbsp-aem-forms-workspace}

Sitzungs-Timeout für einen Benutzer kann in der Administration Console konfiguriert werden.

Um den Timeout festzulegen, melden Sie sich bei `https://[server]:[port]/adminui` an, navigieren zu **Einstellungen > Benutzerverwaltung > Konfiguration > Erweiterte Systemattribute konfigurieren** und nehmen die gewünschten Einstellungen vor.

In AEM Forms wird die Zeitüberschreitung im Arbeitsbereich wie folgt behandelt:

* Die Sitzungsdauer für einen Benutzer ist in der Antwort auf den Aufruf `initialize` verfügbar, der die Benutzersitzung initialisiert.
* Ein Popup-Dialogfeld benachrichtigt den Benutzer 15 Sekunden vor Ablauf der Sitzung über den bevorstehenden Ablauf der Sitzung.

In diesem Popup-Dialogfeld:

* Klicken Sie auf OK , um die Benutzersitzung zu beenden.
* Klicken Sie auf Abbrechen , um die Benutzersitzung erneut zu initialisieren.

>[!NOTE]
>
>Wird keine Aktion ausgeführt, wird der Benutzer drei Sekunden vor Ablauf der Sitzung automatisch vom AEM Forms-Arbeitsbereich abgemeldet.
