---
title: Konfigurieren der Überprüfungsmeldungen
seo-title: Configuring validation messages
description: Erfahren Sie, wie Sie angeben, wie Überprüfungsmeldungen angezeigt werden und wo sie sich im Verhältnis zum im Webbrowser zurückgegebenen Formular befinden.
seo-description: Learn how to specify how validation messages are displayed and their location relative to the form returned in the web browser.
uuid: f6bff4fa-f90f-4135-ae40-7ab3d3613122
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5f2f8129-e45e-4f3f-ae30-c09330d0e152
exl-id: 2016ac85-12a1-42cb-bc03-fced94947010
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 6%

---

# Konfigurieren der Überprüfungsmeldungen {#configuring-validation-messages}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Bei Formularen, die als HTML wiedergegeben werden, werden Fehler bei der Formularüberprüfung für den Benutzer angezeigt. Sie können die Anzeige von Validierungsmeldungen anpassen. Je nachdem, wo die Überprüfungsmeldungen angezeigt werden, können Sie auch die Position der Nachricht im Formular und die Größe des Rahmenrahmens steuern.

## Festlegen der Anzeige von Validierungsmeldungen {#specify-how-validation-messages-are-displayed}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Formulare&quot;.
1. Wählen Sie unter &quot;Überprüfungsausgabe&quot;in der Liste &quot;Berichte&quot;eine der folgenden Optionen aus:

   **Meldungsfeld:** So zeigen Sie Überprüfungsmeldungen in einem separaten Dialogfeld an.

   **Frame:** Zum Anzeigen von Überprüfungsmeldungen innerhalb eines Rahmens desselben Fensters.

   **Kein Frame:** So zeigen Sie Überprüfungsmeldungen im selben Fenster an. Dieser Wert ist der Standardwert.

   **Über API (mit Daten):** So geben Sie die Validierungsmeldungen über die API (mit Daten) zurück. Die Überprüfungsmeldungen werden nicht auf dem Bildschirm angezeigt.

   **Über API (mit Formular):** So geben Sie die Überprüfungsmeldungen über die API (mit dem Formular) zurück. Die Überprüfungsmeldungen werden nicht auf dem Bildschirm angezeigt.

   **Keine:** So zeigen Sie keine Überprüfungsmeldungen an.

1. Klicken Sie auf Speichern.

## Geben Sie den Speicherort der Überprüfungsmeldungen relativ zum im Webbrowser zurückgegebenen Formular an {#specify-the-location-of-validation-messages-relative-to-the-form-returned-in-the-web-browser}

Wenn &quot;Berichterstellung&quot;auf &quot;Frame&quot;oder &quot;Kein Frame&quot;festgelegt ist, können Sie den Speicherort der Überprüfungsmeldungen angeben.

1. Wählen Sie unter &quot;Überprüfungsausgabe&quot;in der Liste &quot;Position&quot;eine der folgenden Optionen aus:

   **Links:** Zum Anzeigen von Validierungsmeldungen auf der linken Seite des Webbrowsers.

   **Rechts:** Zum Anzeigen von Validierungsmeldungen auf der rechten Seite des Webbrowsers.

   **Oben**: So zeigen Sie Überprüfungsmeldungen oben im Webbrowser an. Dieser Wert ist der Standardwert.

   **Unten**: So zeigen Sie Überprüfungsmeldungen am unteren Rand des Webbrowsers an.

1. Klicken Sie auf Speichern.

## Festlegen der Rahmenrahmengröße {#specify-the-frame-border-size}

Wenn für die Berichterstellung &quot;Frame&quot;festgelegt ist, können Sie die Rahmenrahmengröße angeben.

1. Geben Sie unter &quot;Überprüfungsausgabe&quot;im Feld &quot;Rahmengröße&quot;die Größe des Rahmenrahmens in Pixel ein.

   Die Rahmengröße muss größer/gleich 0 sein. Der Standardwert ist 1.

1. Klicken Sie auf Speichern.
