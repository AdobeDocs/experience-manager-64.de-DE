---
title: Senden einer Formularsendebestätigung per E-Mail
seo-title: Sending a form submission acknowledgement via email
description: Mit AEM Forms können Sie die E-Mail-Übermittlungsaktion konfigurieren, die eine Bestätigung an einen Benutzer beim Senden des Formulars sendet.
seo-description: AEM Forms allows you to configure the email submit action that sends an acknowledgement to a user on submitting the form.
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
exl-id: e850d2a5-cb5f-4bd4-81dd-57951923b6d3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 88%

---

# Senden einer Formularsendebestätigung per E-Mail {#sending-a-form-submission-acknowledgement-via-email}

## Senden der Daten adaptiver Formulare {#adaptive-form-data-submission}

Adaptive Formulare bieten mehrere standardmäßige [Übermittlungsaktionen](/help/forms/using/configuring-submit-actions.md)-Workflows, um die Formulardaten an verschiedene Endpunkte zu senden.

Beispiel: die **E-Mail-Aktion** Übermittlungsaktion sendet eine E-Mail bei erfolgreicher Übermittlung eines adaptiven Formulars. Sie kann auch so konfiguriert werden, dass die Formulardaten und die PDF-Datei in die E-Mail eingefügt werden.

In diesem Artikel werden die Schritte erläutert, mit denen die E-Mail-Aktion für ein adaptives Formular aktiviert wird, sowie die verschiedenen bereitgestellten Konfigurationen.

>[!NOTE]
>
>Sie können auch die **PDF-Aktion für E-Mail** das ausgefüllte Formular per E-Mail als PDF-Anlage zu senden. Die für diese Aktion verfügbaren Konfigurationsoptionen sind mit den Optionen identisch, die für die E-Mail-Aktion verfügbar sind. Die E-Mail-PDF-Aktion ist nur für XFA-basierte adaptive Formulare verfügbar.

## E-Mail-Aktion {#email-action}

Mit der E-Mail-Aktion kann ein Autor automatisch eine E-Mail an einen oder mehrere Empfänger senden, wenn das adaptive Formular erfolgreich gesendet wurde.

>[!NOTE]
>
>Um die E-Mail-Aktion verwenden zu können, müssen Sie dem AEM-E-Mail-Dienst konfigurieren, wie in [Konfigurieren des E-Mail-Diensts](/help/sites-administering/notification.md#configuring-the-mail-service) beschrieben.

### Aktivieren der E-Mail-Aktion in einem adaptiven Formular {#enabling-email-action-on-an-adaptive-form}

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.

1. Klicken Sie neben der Symbolleiste **Beginn eines adaptiven Formulars** auf **Bearbeiten**.

   Das Dialogfeld Komponente bearbeiten wird geöffnet.

   ![Dialogfeld „Komponente bearbeiten“ für ein adaptives Formular](assets/start_of_adp_form.png)

1. Wählen Sie die **Übermittlungsaktionen** Registerkarte und wählen Sie **E-Mail-Aktion** aus der Dropdown-Liste Übermittlungsaktion .

   Auf der Registerkarte werden die Optionen angezeigt, mit denen die E-Mail-Aktion für das aktuelle Formular konfiguriert werden.

   ![Registerkarte „Aktionen übermitteln“](assets/dialog.png)

1. Geben Sie gültige E-Mail-IDs in den Feldern „Mailto“, „CC“ und „BCC“ an.

   Geben Sie den Betreff und den Text der E-Mail in die entsprechenden Felder ein.

   Sie können auch variable Platzhalter in den Feldern angeben. In diesem Fall werden die Feldwerte verarbeitet, wenn das Formular erfolgreich von einem Endbenutzer gesendet wurde. Weitere Informationen finden Sie unter [Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Aktivieren Sie Anhänge einschließen, wenn das Formular Dateianhänge enthält und Sie diese Dateien in der E-Mail anhängen möchten.

   >[!NOTE]
   >
   >Wenn Sie die **E-Mail-PDF-Aktion** auswählen, müssen Sie die Option „Anlagen einschließen“ aktivieren.

1. Klicken Sie auf **OK**, um die Änderungen zu speichern.

### Verwenden der Feldnamen in adaptiven Formularen, um E-Mail-Inhalte dynamisch zu erstellen {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Die Feldnamen in einem adaptiven Formular werden als Platzhalter bezeichnet, die durch den Wert dieses Felds ersetzt werden, wenn ein Benutzer das Formular sendet.

In der Registerkarte „E-Mail-Aktion“ können Sie Platzhalter verwenden, die verarbeitet werden, wenn die Aktion ausgeführt wird. Das bedeutet, dass die Header der E-Mail (wie Mailto, CC, BCC, Betreff) erstellt werden, wenn der Benutzer das Formular sendet.

Um einen Platzhalter zu definieren, geben Sie `${<field name>}` in einem Feld auf der Registerkarte &quot;Aktionen übermitteln&quot;.

Beispiel: Wenn das Formular das Feld **E-Mail-Adresse** mit dem Namen `email_addr` zur Erfassung der E-Mail-ID eines Benutzers enthält, können Sie Folgendes im Feld „Mailto“, „CC“ oder „BCC“ angeben.

`${email_addr}`

Wenn ein Benutzer das Formular sendet, wird eine E-Mail an die E-Mail-Adresse gesendet, die in das Feld `email_addr` des Formulars eingegeben wurde.

>[!NOTE]
>
>Sie finden den Namen eines Felds im Dialogfeld **Bearbeiten** für das Feld.

Variable Platzhalter können auch in den Feldern **Betreff** und **E-Mail-Vorlage** verwendet werden.

Beispiel:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Felder in wiederholbaren Bereichen können nicht als variable Platzhalter verwendet werden.
