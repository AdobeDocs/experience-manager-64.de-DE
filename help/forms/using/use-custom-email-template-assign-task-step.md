---
title: Verwenden von benutzerdefinierten E-Mail-Vorlagen im Schritt „Aufgabe zuweisen“
seo-title: Use custom email templates in an Assign Task step
description: Benutzerdefinierte E-Mail-Vorlagen für E-Mail-Benachrichtigungen beim Arbeitsablauf für Formulare
seo-description: Custom email templates for forms workflow email notifications
uuid: bc2af94d-d4ad-417e-b3d2-bcfffc1b306d
topic-tags: publish
discoiquuid: c447fc39-c0f3-4932-ac6c-465d1fb83f8c
exl-id: 5af73823-2c32-41b3-9ab8-a7ad9fd9532f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 38%

---

# Benutzerdefinierte E-Mail-Vorlagen im Schritt „Aufgabe zuweisen“ verwenden {#use-custom-email-templates-in-an-assign-task-step}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Benutzerdefinierte E-Mail-Vorlagen für E-Mail-Benachrichtigungen beim Arbeitsablauf für Formulare

Sie können den Schritt &quot;Aufgabe zuweisen&quot;verwenden, um einem Benutzer oder einer Gruppe Aufgaben zu erstellen und zuzuweisen. Wenn eine Aufgabe einem Benutzer oder einer Gruppe zugewiesen wird, wird eine E-Mail-Benachrichtigung an den definierten Benutzer oder an jedes Mitglied der definierten Gruppe gesendet. Eine typische E-Mail-Benachrichtigung enthält einen Link zur zugewiesenen Aufgabe und Informationen zur Aufgabe. Die folgende Abbildung zeigt eine Beispiel-E-Mail-Benachrichtigung:

![E-Mail-Benachrichtigung mit vorgegebener Vorlage](do-not-localize/default-email-template.png)

Sie können das Erscheinungsbild anpassen und benutzerdefinierte Metadaten in einer E-Mail-Benachrichtigung verwenden. AEM Forms stellt eine vordefinierte Vorlage für E-Mail-Benachrichtigungen bereit. Sie können die vordefinierte Vorlage anpassen oder eine neue Vorlage von Grund auf neu erstellen.

Vorlagen für E-Mail-Benachrichtigungen basieren auf [HTML-E-Mail](https://en.wikipedia.org/wiki/HTML_email). Diese E-Mails passen sich an unterschiedliche E-Mail-Clients und Bildschirmgrößen an. Darüber hinaus wird der Stil der E-Mail in der Vorlage definiert.

Die folgende Abbildung zeigt eine angepasste E-Mail-Benachrichtigung:

![E-Mail-Benachrichtigung mit benutzerdefinierter Vorlage](do-not-localize/customized-email.png)

## Vorhandene Vorlage anpassen {#customize-the-existing-template}

Standardmäßig stellt AEM Forms eine Vorlage für E-Mail-Benachrichtigungen bereit. Die Vorlage enthält eine Titelbeschreibung, ein Fälligkeitsdatum, eine Priorität, den Namen des Workflows und den Link der zugewiesenen Aufgabe. Sie können die Vorlage anpassen, um das Erscheinungsbild zu ändern. Führen Sie die folgenden Schritte aus, um die Vorlage anzupassen:

1. Melden Sie sich mit einem Administratorkonto bei CRXDE an.

1. Navigieren Sie zu /libs/fd/dashboard/templates/email.

1. Öffnen Sie die Datei „htmlEmailTemplate.txt“. Sie enthält die Standardvorlage.

1. Ersetzen Sie den Inhalt der Datei „htmlEmailTemplate.txt“ durch benutzerdefinierten Inhalt.

   Eine E-Mail-Benachrichtigungsvorlage ist eine [HTML-E-Mail](https://en.wikipedia.org/wiki/HTML_email). Sie können den vorhandenen HTML-Code durch Ihren benutzerdefinierten Code ersetzen, um das Aussehen der Vorlage zu ändern.

1. Speichern Sie die Datei. Damit ist die benutzerdefinierte Vorlage einsatzbereit.

## E-Mail-Vorlage erstellen {#create-an-email-template}

Standardmäßig stellt AEM Forms eine Vorlage für E-Mail-Benachrichtigungen bereit. Die Vorlage enthält eine Titelbeschreibung, ein Fälligkeitsdatum, eine Priorität, den Namen des Workflows und den Link der zugewiesenen Aufgabe. Sie können auch eine benutzerdefinierte E-Mail-Vorlage (Ihre eigene Vorlage) für die Schritte zum Zuweisen von Aufgaben hinzufügen. Führen Sie die folgenden Schritte aus, um eine benutzerdefinierte E-Mail-Vorlage hinzuzufügen:

1. Melden Sie sich mit einem Administratorkonto bei CRXDE an.

1. Navigieren Sie zu /libs/fd/dashboard/templates/email.

1. Erstellen Sie eine TXT-Datei. Dies könnte beispielsweise „EmailOnTaskAssign.txt“ sein.

1. Fügen Sie der Datei benutzerdefinierten HTML-Code hinzu.

   Eine E-Mail-Benachrichtigungsvorlage ist eine [HTML-E-Mail](https://en.wikipedia.org/wiki/HTML_email). Sie können der Datei benutzerdefinierten HTML-Code hinzufügen, um eine neue Vorlage zu erstellen. 

1. Speichern Sie die Datei. Damit ist die Vorlage zur Verwendung im Schritt „Aufgabe zuweisen“ bereit.

## E-Mail-Vorlage in einem Schritt &quot;Aufgabe zuweisen&quot;verwenden {#use-an-email-template-in-an-assign-task-step}

Standardmäßig ist der Schritt Aufgabe zuweisen für die Verwendung der Standardvorlage htmlEmailTemplate.txt konfiguriert. Sie können eine benutzerdefinierte Vorlage verwenden. So ändern Sie die Vorlage:

1. Öffnen Sie die **[!UICONTROL Aufgabe zuweisen]** Schritt.

1. Navigieren Sie zu **[!UICONTROL Assignee > HTML Email Template]**.

1. Wählen Sie die neu erstellte HTML-E-Mail-Vorlage aus. 

1. Klicken Sie auf **[!UICONTROL OK]**. Die Vorlage wird geändert.

Eine E-Mail-Benachrichtigung verwendet auch [Metadaten](/help/forms/using/use-metadata-in-email-notifications.md). Beispielsweise Fälligkeitsdatum, Priorität, Workflow-Name und mehr. Sie können die Vorlage auch so konfigurieren, dass [benutzerdefinierte Metadaten](/help/forms/using/use-metadata-in-email-notifications.md#using-custom-metadata-in-an-email-notification) verwendet werden.
