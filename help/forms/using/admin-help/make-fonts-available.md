---
title: Bereitstellen von Schriften
seo-title: Make fonts available
description: Stellen Sie sicher, dass die in einem Formular verwendeten Schriftarten für die Verwendung auf dem J2EE-Anwendungsserver verfügbar sind, auf dem AEM Formulare gehostet werden.
seo-description: Ensure that the fonts used within a form are available for use on the J2EE application server hosting AEM forms.
uuid: 6588b4b6-f866-4253-91c8-3aa174340e8c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9f58a6c4-3190-49d4-800c-4a55dca7c296
exl-id: 33d63ec9-b100-48b4-b84d-a9de82c24f86
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 16%

---

# Bereitstellen von Schriften {#make-fonts-available}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Stellen Sie sicher, dass die in einem Formular verwendeten Schriftarten für die Verwendung auf dem J2EE-Anwendungsserver verfügbar sind, auf dem AEM Formulare gehostet werden. Betrachten Sie beispielsweise das folgende Szenario. Ein Formularentwickler fügt dem Schriftartenordner, den Designer verwendet, eine Schrift hinzu und erstellt ein Formular, das diese Schrift verwendet, auf einem separaten Computer. Damit der Output-Dienst die Schrift verwenden kann, legen Sie sie im Verzeichnis &quot;Kundenschriftarten&quot;ab. Wenn der Ordner für Kundenschriftarten nicht vorhanden ist, erstellen Sie einen Ordner auf dem J2EE-Anwendungsserver, der AEM Formulare hostet.

Weitere Informationen zu Schrifteinstellungen finden Sie unter [Allgemeine Einstellungen AEM Formulare konfigurieren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**Speicherort des Ordners für Kundenschriftarten angeben**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Core-Systemeinstellungen&quot;> &quot;Konfigurationen&quot;.
1. Geben Sie in das Feld Speicherort des Ordners für Systemschriftarten den Pfad zum Verzeichnis für Kundenschriftarten ein. Mehrere Ordner können hinzugefügt werden, indem sie durch ein Semikolon **;** voneinander getrennt werden.
1. Klicken Sie auf OK.
1. Starten Sie das System neu, auf dem AEM Formulare installiert sind.

>[!NOTE]
>
>Schriftarten werden aus dem Windows-Systemschriftarten-Cache ausgewählt und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.
