---
title: Formularausgabe konfigurieren
seo-title: Configuring form output
description: Erfahren Sie, wie Sie die Formularausgabe konfigurieren.
seo-description: Learn how to configure form output.
uuid: 70aad14e-c845-4ef3-a751-ad8860d5d505
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 17c9b69a-3c6f-47e3-a828-841bb90eba8b
exl-id: b19cae88-a549-41ba-b4a6-4b065a995296
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 100%

---

# Formularausgabe konfigurieren{#configuring-form-output}

## Den Typ der HTML-Ausgabe angeben, der an den Webbrowser zurückgegeben wird. {#specify-the-type-of-html-output-returned-to-the-web-browser}

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Wählen Sie unter „Formularausgabe“ in der Liste „Ausgabetyp“ eine der folgenden Optionen aus:

   **Voll-HTML**, um das Formular mit vollständigen HTML-Tags wiederzugeben (eine vollständige HTML-Seite). Dies ist der Standardwert.

   **Formularhauptteil:** Um das Formular zwischen `<BODY>`-Tags wiederzugeben (keine vollständige HTML-Seite).

1. Klicken Sie auf Speichern.

## Den Ort angeben, an dem PDF-Inhalt wiedergegeben wird. {#specify-the-location-where-pdf-content-is-rendered}

1. Wählen Sie unter „Formularausgabe“ in der Liste „Wiedergeben“ eine der folgenden Optionen aus:

   **Client**, um PDF-Formulare in Adobe Acrobat oder Adobe Reader wiederzugeben. Die clientseitige Wiedergabe verbessert die Leistung von AEM Forms und findet nur bei der PDFForm-Transformation Anwendung.

   **Server**, um PDF-Formulare auf dem Anwendungsserver wiederzugeben.

   **Autom.**, um das PDF-Formular an dem Ort wiederzugeben, der über den Konfigurationswert `dynamicRender` der XDP-Datei angegeben ist. Dies ist der Standardwert.

1. Klicken Sie auf Speichern.

## Aufrufe von benutzerdefinierten Skripten konfigurieren, bevor das Formular eingereicht wird {#configuring-invocation-of-custom-scripts-before-form-submit}

Führen Sie zum Aktivieren der Funktion folgende Schritte durch:

1. Melden Sie sich bei Administration Console an.
1. Gehen Sie zu **Dienste** > **Forms**.
1. Geben Sie den Ausgabetyp als Form Body an.
1. Speichern Sie die Einstellungen.
1. Deklarieren Sie eine JavaScript-Variable, __CUSTOM_SCRIPTS_VERSION, im Kopfteil des HTML-Codes und stellen Sie den Wert auf 1 ein.

   >[!NOTE]
   >
   >*Um die Funktion zu deaktivieren, können Sie die JavaScript-Variable entfernen oder ihren Wert auf 0 einstellen.*
