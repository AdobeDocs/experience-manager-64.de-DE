---
title: Senden einer Formularsendebestätigung per E-Mail
seo-title: Sending a form submission acknowledgement via email
description: Mit AEM Forms können Sie die E-Mail-Sendeaktion konfigurieren, die eine Bestätigung an einen Benutzer beim Senden des Formulars sendet.
seo-description: AEM Forms allows you to configure the email submit action that sends an acknowledgement to a user on submitting the form.
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
exl-id: e850d2a5-cb5f-4bd4-81dd-57951923b6d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 22%

---

# Senden einer Formularsendebestätigung per E-Mail {#sending-a-form-submission-acknowledgement-via-email}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Datenübermittlung für adaptive Formulare {#adaptive-form-data-submission}

Adaptive Formulare bieten mehrere vordefinierte [Sendeaktionen](/help/forms/using/configuring-submit-actions.md) Workflows zum Senden der Formulardaten an verschiedene Endpunkte.

Beispiel: die **E-Mail-Aktion** Übermittlungsaktion sendet eine E-Mail bei erfolgreicher Übermittlung eines adaptiven Formulars. Sie kann auch so konfiguriert werden, dass die Formulardaten und die PDF-Datei in die E-Mail eingefügt werden.

In diesem Artikel werden die Schritte zum Aktivieren der E-Mail-Aktion für ein adaptives Formular und die verschiedenen bereitgestellten Konfigurationen beschrieben.

>[!NOTE]
>
>Sie können auch die **PDF-Aktion für E-Mail** das ausgefüllte Formular per E-Mail als PDF-Anlage zu senden. Die für diese Aktion verfügbaren Konfigurationsoptionen sind mit den für die E-Mail-Aktion verfügbaren Optionen identisch. Die E-Mail-PDF-Aktion ist nur für XFA-basierte adaptive Formulare verfügbar.

## E-Mail-Aktion {#email-action}

Mit der E-Mail-Aktion kann ein Autor bei erfolgreicher Übermittlung eines adaptiven Formulars automatisch eine E-Mail an einen oder mehrere Empfänger senden.

>[!NOTE]
>
>Um die E-Mail-Aktion zu verwenden, müssen Sie den AEM-E-Mail-Dienst konfigurieren, wie unter [E-Mail-Dienst konfigurieren](/help/sites-administering/notification.md#configuring-the-mail-service).

### Aktivieren der E-Mail-Aktion in einem adaptiven Formular {#enabling-email-action-on-an-adaptive-form}

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.

1. Klicken **Bearbeiten** neben dem **Beginn eines adaptiven Formulars** Symbolleiste.

   Das Dialogfeld Komponente bearbeiten wird geöffnet.

   ![Dialogfeld &quot;Komponente bearbeiten&quot;für ein adaptives Formular](assets/start_of_adp_form.png)

1. Wählen Sie die **Übermittlungsaktionen** Registerkarte und wählen Sie **E-Mail-Aktion** aus der Dropdown-Liste Übermittlungsaktion .

   Auf der Registerkarte werden die Optionen zum Konfigurieren der E-Mail-Aktion für das aktuelle Formular angezeigt.

   ![Registerkarte &quot;Übermittlungsaktionen&quot;](assets/dialog.png)

1. Geben Sie gültige E-Mail-IDs in die Felder Mailto, CC und BCC ein.

   Geben Sie den Betreff und den Text der E-Mail in die Felder Betreff und E-Mail-Vorlage ein.

   Sie können auch variable Platzhalter in den Feldern angeben. In diesem Fall werden die Werte der Felder verarbeitet, wenn das Formular erfolgreich von einem Endbenutzer gesendet wurde. Weitere Informationen finden Sie unter [Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Aktivieren Sie Anhänge einschließen, wenn das Formular Dateianhänge enthält und Sie diese Dateien in der E-Mail anhängen möchten.

   >[!NOTE]
   >
   >Wenn Sie die **PDF-Aktion für E-Mail** müssen Sie die Option Anlagen einschließen auswählen.

1. Klicken Sie auf **OK**, um die Änderungen zu speichern.

### Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Die Feldnamen in einem adaptiven Formular werden als Platzhalter bezeichnet, die durch den Wert dieses Felds ersetzt werden, nachdem ein Benutzer das Formular gesendet hat.

Auf der Registerkarte E-Mail-Aktion können Sie Platzhalter verwenden, die verarbeitet werden, wenn die Aktion ausgeführt wird. Dies bedeutet, dass die Header der E-Mail (wie Mailto, CC, BCC, Betreff) generiert werden, wenn der Benutzer das Formular sendet.

Um einen Platzhalter zu definieren, geben Sie `${<field name>}` in einem Feld auf der Registerkarte &quot;Aktionen übermitteln&quot;.

Wenn das Formular beispielsweise die Variable **Email-Adresse** Feld, benannt `email_addr`Um die E-Mail-ID eines Benutzers zu erfassen, können Sie Folgendes in die Felder Mailto, CC oder BCC eingeben.

`${email_addr}`

Wenn ein Benutzer das Formular sendet, wird eine E-Mail an die E-Mail-Adresse gesendet, die in das Feld `email_addr` des Formulars eingegeben wurde.

>[!NOTE]
>
>Sie finden den Namen eines Felds im Dialogfeld **Bearbeiten** für das Feld.

Variablenplatzhalter können auch im **Betreff** und **E-Mail-Vorlage** -Felder.

Beispiel:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Felder in wiederholbaren Bereichen können nicht als variable Platzhalter verwendet werden.
