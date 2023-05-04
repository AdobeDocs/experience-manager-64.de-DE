---
title: Konfigurieren der Formularausgabe
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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 38%

---

# Konfigurieren der Formularausgabe{#configuring-form-output}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Geben Sie den Typ der an den Webbrowser zurückgegebenen HTML-Ausgabe an {#specify-the-type-of-html-output-returned-to-the-web-browser}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Formulare&quot;.
1. Wählen Sie unter &quot;Formularausgabe&quot;in der Liste &quot;Ausgabetyp&quot;eine der folgenden Optionen aus:

   **Vollständige HTML:** So rendern Sie das Formular mit vollständigen HTML-Tags (eine vollständige HTML-Seite). Dieser Wert ist der Standardwert.

   **Formularhauptteil:** Um das Formular zwischen `<BODY>`-Tags wiederzugeben (keine vollständige HTML-Seite).

1. Klicken Sie auf Speichern.

## Geben Sie den Speicherort an, an dem PDF-Inhalt gerendert wird {#specify-the-location-where-pdf-content-is-rendered}

1. Wählen Sie unter &quot;Formularausgabe&quot;in der Liste &quot;Rendern am&quot;eine der folgenden Optionen aus:

   **Client:** So rendern Sie PDF forms in Adobe Acrobat oder Adobe Reader. Die clientseitige Wiedergabe verbessert die Leistung von AEM Formularen und gilt nur für die PDFForm-Transformation.

   **Server:** So rendern Sie PDF forms auf dem Anwendungsserver.

   **Autom.**, um das PDF-Formular an dem Ort wiederzugeben, der über den Konfigurationswert `dynamicRender` der XDP-Datei angegeben ist. Dieser Wert ist der Standardwert.

1. Klicken Sie auf Speichern.

## Konfigurieren des Aufrufs von benutzerdefinierten Skripten vor dem Senden des Formulars {#configuring-invocation-of-custom-scripts-before-form-submit}

Führen Sie zum Aktivieren der Funktion folgende Schritte durch:

1. Melden Sie sich bei Administration Console an.
1. Navigieren Sie zu **Dienste** > **forms**.
1. Geben Sie den Ausgabetyp als Form Body an.
1. Speichern Sie die Einstellungen.
1. Deklarieren Sie eine JavaScript-Variable, __CUSTOM_SCRIPTS_VERSION, im Kopfteil des HTML-Codes und stellen Sie den Wert auf 1 ein.

   >[!NOTE]
   >
   >*Um die Funktion zu deaktivieren, können Sie die JavaScript-Variable entfernen oder ihren Wert auf 0 einstellen.*
