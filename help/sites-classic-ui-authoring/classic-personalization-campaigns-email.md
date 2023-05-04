---
title: E-Mail-Marketing
seo-title: E-mail Marketing
description: E-Mail-Marketing (z. B. Newsletter) ist ein wichtiger Bestandteil jeder Marketingkampagne, da Sie auf diese Weise Ihren Leads Inhalte zukommen lassen können. In AEM können Sie Newsletter aus vorhandenen AEM erstellen sowie neue, für die Newsletter spezifische Inhalte hinzufügen.
seo-description: E-mail marketing (for example, newsletters) are an important part of any marketing campaign as you use them to push content to your leads. In AEM, you can create newsletters from existing AEM content as well as add new content, specific to the newsletters.
uuid: 798e06cd-64dd-4a8d-8a7a-9a7ba80045f6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: eb72f934-4b0f-4a71-b2a2-3ddf78db8c3c
exl-id: 5e97f7bd-d668-423d-9f65-7dcc8fb1943a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1762'
ht-degree: 39%

---

# E-Mail-Marketing{#e-mail-marketing}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe plant keine weitere Verbesserung von offenen/nicht zugestellten E-Mails, die vom AEM SMTP-Dienst gesendet werden.\
>Die Empfehlung lautet, [Adobe Campaign und die AEM-Integration zu nutzen](/help/sites-administering/campaign.md).

E-Mail-Marketing (z. B. Newsletter) ist ein wichtiger Bestandteil jeder Marketingkampagne, da Sie auf diese Weise Ihren Leads Inhalte zukommen lassen können. In AEM können Sie Newsletter aus vorhandenen AEM erstellen sowie neue, für die Newsletter spezifische Inhalte hinzufügen.

Nach der Erstellung können Sie Newsletter entweder sofort oder zu einem anderen geplanten Zeitpunkt (mithilfe eines Workflows) an die jeweilige Benutzergruppe senden. Darüber hinaus können Benutzer Newsletter in dem Format abonnieren, das sie wählen.

Darüber hinaus können AEM die Newsletter-Funktion verwalten, einschließlich der Pflege von Themen, der Archivierung von Newslettern und der Anzeige von Newsletter-Statistiken.

>[!NOTE]
>
>In Geometrixx wird die Newsletter-Vorlage automatisch im E-Mail-Editor geöffnet. Sie können den E-Mail-Editor auch für andere Vorlagen verwenden, die Sie per E-Mail versenden möchten, z. B. Einladungen. Der E-Mail-Editor wird immer dann angezeigt, wenn eine Seite von **mcm/components/newsletter/page**.

In diesem Dokument werden die Grundlagen zum Erstellen von Newslettern in AEM beschrieben. Weitere Informationen zur Verwendung von E-Mail-Marketing finden Sie in den folgenden Dokumenten:

* [Erstellen einer effektiven Einstiegsseite für Newsletter](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-landingpage.md)
* [Verwalten von Abonnements](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-subscriptions.md)
* [Veröffentlichen von E-Mails bei E-Mail-Dienstanbietern](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-newsletters.md)
* [Nachverfolgen nicht zugestellter E-Mails](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-tracking-bounces.md)

>[!NOTE]
>
>Wenn Sie E-Mail-Anbieter aktualisieren, einen Testlauf durchführen oder einen Newsletter versenden, schlagen diese Vorgänge fehl, wenn der Newsletter nicht zuerst in der Veröffentlichungsinstanz veröffentlicht wird oder die Veröffentlichungsinstanz nicht verfügbar ist. Veröffentlichen Sie Ihren Newsletter und stellen Sie sicher, dass die Veröffentlichungsinstanz aktiv ist.

## Erstellen eines Newsletter-Erlebnisses {#creating-a-newsletter-experience}

>[!NOTE]
>
>E-Mail-Benachrichtigungen müssen über die OSGi-Konfiguration konfiguriert werden. Siehe [Konfigurieren der E-Mail-Benachrichtigung.](/help/sites-administering/notification.md)

1. Wählen Sie Ihre neue Kampagne im linken Bereich aus oder doppelklicken Sie im rechten Bereich darauf.

1. Wählen Sie die Listenansicht mithilfe des Symbols aus:

   ![](do-not-localize/mcm_icon_listview-1.png)

1. Klicken Sie auf **Neu...**

   Sie können die **Titel**, **Name** und Art des zu erstellenden Erlebnisses; in diesem Fall Newsletter.

   ![mcm_createnewsletter](assets/mcm_createnewsletter.png)

1. Klicken Sie auf **Erstellen**.

1. Ein neues Dialogfeld wird geöffnet. Hier können Sie Eigenschaften für den Newsletter eingeben.

   Das Feld **Standard-Empfängerliste** muss ausgefüllt werden, da es den Touchpoint für den Newsletter bildet (weitere Informationen zu Listen finden Sie unter [Arbeiten mit Listen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists)).

   ![mcm_newnewsletterdialog](assets/mcm_newnewsletterdialog.png)

   * **Absendername**

      Der Name, der als Absender des Newsletters angezeigt werden soll.

   * **Absenderadresse**

      Die E-Mail-Adresse, die als Absender des Newsletters angezeigt werden soll.

   * **Betreff**

      Der Betreff des Newsletters.

   * **Antwort an**

      Die E-Mail-Adresse, an die Antworten auf den gesendeten Newsletter gerichtet werden sollen.

   * **Beschreibung**

      Beschreibung des Newsletters.

   * **Einschaltzeit**

      Die Einschaltzeit für den Versand des Newsletters.

   * **Standard-Empfängerliste**

      Standardliste, die den Newsletter erhalten soll.
   Diese können zu einem späteren Zeitpunkt im Abschnitt **Eigenschaften...** angezeigt.

1. Klicken Sie zum Speichern auf **OK**.

## Hinzufügen von Inhalten zu Newslettern {#adding-content-to-newsletters}

Sie können Ihrem Newsletter wie bei jeder anderen AEM-Komponente Inhalt hinzufügen, darunter auch dynamischen Inhalt. In Geometrixx sind für die Vorlage Newsletter bestimmte Komponenten zum Hinzufügen und Ändern von Inhalt in Newslettern verfügbar.

1. Klicken Sie im MCM auf die Registerkarte **Kampagnen** und doppelklicken Sie dann auf den Newsletter, dem Sie Inhalt hinzufügen möchten oder dessen Inhalt Sie bearbeiten möchten. Der Newsletter wird geöffnet.

1. Wenn keine Komponenten sichtbar sind, gehen Sie zur Designansicht und aktivieren Sie die erforderlichen Komponenten (z. B. die Newsletter-Komponente), bevor Sie mit der Bearbeitung beginnen.
1. Geben Sie wie erforderlich neuen Text, neue Bilder oder andere Komponenten ein. Im Geometrixx-Beispiel stehen 4 Komponenten zur Verfügung: „Text“, „Bild“, „Überschrift“ und „2 Spalten“. Ihr Newsletter kann je nach Einrichtung mehr oder weniger Komponenten enthalten.

   >[!NOTE]
   >
   >Mithilfe von Variablen können Sie den Newsletter personalisieren. Im Geometrixx-Newsletter stehen in der Text-Komponente Variablen zur Verfügung. Die Werte für die Variablen werden aus den Informationen im Benutzerprofil übernommen.

   ![mcm_newsletter_content](assets/mcm_newsletter_content.png)

1. Wählen Sie die Variable aus der Liste aus und klicken Sie auf **Einfügen**, um die Variablen einzufügen. Variablen werden aus dem Profil gefüllt.

## Personalisieren von Newslettern {#personalizing-newsletters}

Sie können die Newsletter anpassen, indem Sie vordefinierte Variablen in die Text-Komponente des Geometrixx-Newsletters einfügen. Die Werte für die Variablen werden aus den Informationen im Benutzerprofil übernommen.

Sie können auch simulieren, wie ein Newsletter personalisiert wird, indem Sie den Client-Kontext verwenden und ein Profil laden.

So personalisieren Sie einen Newsletter und simulieren sein Aussehen:

1. Öffnen Sie im MCM den Newsletter, für den Sie Einstellungen anpassen möchten.

1. Öffnen Sie die Textkomponente, die Sie personalisieren möchten.

1. Platzieren Sie den Cursor an die Stelle, an der die Variable angezeigt werden soll, wählen Sie eine Variable aus der Dropdownliste aus und klicken Sie auf **Einfügen**. Führen Sie diese Schritte für so viele Variablen wie erforderlich aus und klicken Sie auf **OK**.

   ![mcm_newsletter_variables](assets/mcm_newsletter_variables.png)

1. Drücken Sie Strg+Alt+C, um ClientContext zu öffnen, und wählen Sie **Laden**, um zu simulieren, wie die Variable beim Versenden dargestellt wird. Wählen Sie den Benutzer aus der Liste aus, dessen Profil Sie laden möchten, und klicken Sie auf **OK**.

   Die Informationen aus dem von Ihnen geladenen Profil haben die Variablen gefüllt.

   ![mc_newsletter_testvariables](assets/mc_newsletter_testvariables.png)

## Testen von Newslettern in verschiedenen E-Mail-Clients {#testing-newsletters-in-different-e-mail-clients}

>[!NOTE]
>
>Prüfen Sie vor dem Versenden eines Newsletters die OSGi-Konfiguration für Day CQ Link Externalizer unter `http://localhost:4502/system/console/configMgr`.
>
>Der Wert des Parameters ist standardmäßig `localhost:4502` und der Vorgang kann nicht abgeschlossen werden, wenn der Port für die aktive Instanz geändert wird.

Schalten Sie zwischen allgemeinen E-Mail-Clients um, um eine Ansicht des Newsletters für Ihre Leads anzuzeigen. Standardmäßig wird Ihr Newsletter geöffnet, wobei keiner der ausgewählten E-Mail-Clients ausgewählt ist.

Derzeit können Sie Newsletter in den folgenden E-Mail-Clients anzeigen:

* Yahoo Mail
* Gmail
* Hotmail
* Thunderbird
* Microsoft Outlook 2007
* Apple Mail

Um zwischen Clients zu wechseln, klicken Sie auf das entsprechende Symbol, um den Newsletter in diesem E-Mail-Client anzuzeigen:

1. Öffnen Sie im MCM den Newsletter, für den Sie Einstellungen anpassen möchten.

1. Klicken Sie in der oberen Leiste auf einen E-Mail-Client, um zu sehen, wie der Newsletter in diesem Client aussehen würde.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Wiederholen Sie diesen Schritt für alle weiteren E-Mail-Clients, die Sie testen möchten.

   ![chlimage_1-168](assets/chlimage_1-168.png)

## Anpassen der Newsletter-Einstellungen {#customizing-newsletter-settings}

Obwohl nur autorisierte Benutzer einen Newsletter versenden können, sollten Sie Folgendes anpassen:

* Betreffzeile, damit Benutzer Ihre E-Mail öffnen und sicherstellen können, dass Ihr Newsletter nicht als Spam gekennzeichnet wird.
* Die Von-Adresse, z. B. noreply@geometrixx.com, damit Benutzer die E-Mail von einer bestimmten Adresse erhalten.

So passen Sie Newsletter-Einstellungen an:

1. Öffnen Sie im MCM den Newsletter, für den Sie Einstellungen anpassen möchten.

   ![mcm_newsletter_open](assets/mcm_newsletter_open.png)

1. Klicken Sie oben im Newsletter auf **Einstellungen**.

   ![mcm_newsletter_settings](assets/mcm_newsletter_settings.png)

   1. Geben Sie die **Von** E-Mail-Adresse
   1. Ändern Sie die **Betreff** der E-Mail, falls erforderlich.
   1. Wählen Sie eine **Standard-Empfängerliste** aus der Dropdown-Liste aus.
   1. Klicken Sie auf **OK**.

   Wenn Sie den Newsletter testen oder versenden, erhalten Empfänger E-Mails mit der angegebenen E-Mail-Adresse und dem angegebenen Betreff.

## Newsletter zum Testen von Flugzeugen {#flight-testing-newsletters}

Während Flugtests nicht obligatorisch sind, sollten Sie vor dem Versand eines Newsletters testen, ob der Newsletter wie gewünscht angezeigt wird.

Mithilfe von Flugtests können Sie Folgendes durchführen:

* Sehen Sie sich den Newsletter an unter [alle vorgesehenen Kunden](#testing-newsletters-in-different-e-mail-clients).
* Überprüfen Sie, ob der E-Mail-Server ordnungsgemäß eingerichtet ist.
* Ermitteln Sie, ob Ihre E-Mail als Spam eingestuft wird. (Stellen Sie sicher, dass Sie sich selbst in die Empfängerliste aufnehmen.)

>[!NOTE]
>
>Wenn Sie E-Mail-Anbieter aktualisieren, einen Testlauf durchführen oder einen Newsletter versenden, schlagen diese Vorgänge fehl, wenn der Newsletter nicht zuerst in der Veröffentlichungsinstanz veröffentlicht wird oder die Veröffentlichungsinstanz nicht verfügbar ist. Veröffentlichen Sie Ihren Newsletter und stellen Sie sicher, dass die Veröffentlichungsinstanz aktiv ist.

Newsletter zu Testflügen:

1. Öffnen Sie im MCM den Newsletter, den Sie testen und senden möchten.

1. Klicken Sie oben im Newsletter auf **Test** vor dem Versand testen.

   ![mcm_newsletter_testsettings](assets/mcm_newsletter_testsettings.png)

1. Geben Sie die Test-E-Mail-Adresse ein, an die der Newsletter geschickt werden soll und klicken Sie auf **Senden**. Wenn Sie das Profil ändern möchten, laden Sie ein anderes Profil in ClientContext. Drücken Sie dazu Strg+Alt+C und wählen Sie Laden und Laden eines Profils aus.

## Versenden von Newslettern {#sending-newsletters}

Sie können einen Newsletter entweder aus dem Newsletter selbst oder aus der Liste versenden. Beide Verfahren werden beschrieben.

>[!NOTE]
>
>Prüfen Sie vor dem Versenden eines Newsletters die OSGi-Konfiguration für Day CQ Link Externalizer unter `http://localhost:4502/system/console/configMgr`.
>
>Der Wert des Parameters ist standardmäßig `localhost:4502` und der Vorgang kann nicht abgeschlossen werden, wenn der Port für die aktive Instanz geändert wird.

>[!NOTE]
>
>Wenn Sie E-Mail-Anbieter aktualisieren, einen Testlauf durchführen oder einen Newsletter versenden, schlagen diese Vorgänge fehl, wenn der Newsletter nicht zuerst in der Veröffentlichungsinstanz veröffentlicht wird oder die Veröffentlichungsinstanz nicht verfügbar ist. Veröffentlichen Sie Ihren Newsletter und stellen Sie sicher, dass die Veröffentlichungsinstanz aktiv ist.

### Senden von Newslettern aus einer Kampagne {#sending-newsletters-from-a-campaign}

So senden Sie einen Newsletter aus der Kampagne heraus:

1. Öffnen Sie im MCM den Newsletter, den Sie versenden möchten.

   >[!NOTE]
   >
   >Stellen Sie vor dem Senden sicher, dass Sie den Betreff und die Absender-E-Mail-Adresse durch [Anpassen der Einstellungen](#customizing-newsletter-settings) personalisiert haben.
   >
   >Vor dem Versenden des Newsletters wird ein [Newsletter-Testlauf](#flight-testing-newsletters) empfohlen.

1. Klicken Sie oben im Newsletter auf **Senden**. Der Newsletter-Assistent wird geöffnet.

1. Wählen Sie in der Empfängerliste die Liste aus, die den Newsletter erhalten soll, und klicken Sie auf **Nächste**.

   ![mcm_newslettersend](assets/mcm_newslettersend.png)

1. Es wird eine Bestätigung angezeigt, dass die Einrichtung abgeschlossen wurde. Klicken **Senden** um den Newsletter zu versenden.

   ![mcm_newslettersendconfirm](assets/mcm_newslettersendconfirm.png)

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie einer der Empfänger sind, damit Sie sicherstellen können, dass der Newsletter empfangen wurde.

### Versenden von Newslettern aus einer Liste {#sending-newsletters-from-a-list}

So versenden Sie einen Newsletter aus einer Liste:

1. Klicken Sie im MCM auf **Listen** im linken Bereich.

   >[!NOTE]
   >
   >Stellen Sie vor dem Senden sicher, dass Sie den Betreff und die Absender-E-Mail-Adresse durch [Anpassen der Einstellungen](#customizing-newsletter-settings) personalisiert haben. Sie können einen Newsletter nicht testen, wenn Sie ihn aus der Liste versenden. Sie können [Flugprüfung](#flight-testing-newsletters) es, wenn Sie es aus dem Newsletter versenden.

1. Aktivieren Sie das Kontrollkästchen neben der Liste der Leads, an die Sie den Newsletter senden möchten.

1. Wählen Sie im Menü **Tools** die Option **Newsletter senden** aus. Das Fenster **Newsletter senden** wird geöffnet.

   ![mcm_newslettersendformlist](assets/mcm_newslettersendfromlist.png)

1. Wählen Sie im Feld **Newsletter** den Newsletter aus, den Sie senden möchten, und klicken Sie auf **Weiter**.

   ![mcm_newslettersenddialog](assets/mcm_newslettersenddialog.png)

1. Es wird eine Bestätigung angezeigt, dass die Einrichtung abgeschlossen wurde. Klicken **Senden** , um den ausgewählten Newsletter an die angegebene Liste von Leads zu senden.

   ![mcm_newslettersenddialog_validation](assets/mcm_newslettersenddialog_confirmation.png)

   Ihr Newsletter wird an die angegebenen Empfänger gesendet.

## Abonnieren eines Newsletters {#subscribing-to-a-newsletter}

In diesem Abschnitt wird beschrieben, wie Sie einen Newsletter abonnieren.

### Newsletter abonnieren {#subscribing-to-a-newsletter-1}

So abonnieren Sie einen Newsletter (unter Verwendung der Geometrixx-Website als Beispiel):

1. Klicken **Websites** und zum Geometrixx navigieren **Symbolleiste** und öffnen Sie sie.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Geben Sie in dem Feld **Registrieren** in dem Geometrixx-Newsletter Ihre E-Mail-Adresse ein und klicken Sie auf **Registrieren**. Sie haben jetzt den Newsletter abonniert.
