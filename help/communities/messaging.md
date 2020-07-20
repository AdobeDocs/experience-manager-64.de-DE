---
title: Messaging konfigurieren
seo-title: Messaging konfigurieren
description: Communities-Messaging
seo-description: Communities-Messaging
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
translation-type: tm+mt
source-git-commit: 9fa89ca34843d41a5ab5711c1090fcc7a1077760
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 4%

---


# Messaging konfigurieren {#configuring-messaging}

## Übersicht {#overview}

Die Messaging-Funktion für AEM Communities ermöglicht es Besuchern mit angemeldeten Sites (Mitgliedern), Nachrichten an andere zu senden, auf die bei der Anmeldung auf der Site zugegriffen werden kann.

Die Messaging-Funktion wird für eine Community-Site aktiviert, indem während der Erstellung [](sites-console.md)einer Community-Site ein Kästchen markiert wird.

Auf dieser Seite finden Sie Informationen zur Standardkonfiguration und möglichen Anpassungen.

For additional information for developers, see [Messaging Essentials](essentials-messaging.md).

## Messaging-Dienst {#messaging-operations-service}

Der [AEM Communities Messaging Operations-Dienst](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifiziert den Endpunkt, der Messaging-bezogene Anfragen verarbeitet, die Ordner, die der Dienst zum Speichern von Nachrichten verwenden sollte, und wenn Meldungen Dateianhänge enthalten können, welche Dateitypen sind zulässig.

Für Community-Sites, die mit der [Communities Sites Console](sites-console.md)erstellt wurden, ist bereits eine Instanz des Dienstes vorhanden, wobei der Posteingang auf `/mail/community/inbox`festgelegt ist.

### Community Messaging-Dienst {#community-messaging-operations-service}

Wie unten gezeigt, existiert eine Konfiguration des Dienstes für Sites, die mit dem [Site-Erstellungsassistenten](sites-console.md)erstellt wurden. Die Konfiguration kann angezeigt oder bearbeitet werden, indem Sie auf das Stiftsymbol neben der Konfiguration klicken:

![chlimage_1-63](assets/chlimage_1-63.png)

### Neue Konfiguration {#new-configuration}

Um eine neue Konfiguration hinzuzufügen, klicken Sie auf das Plus-Symbol **+** neben dem Dienstnamen:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Zulassungsliste]**&quot;Nachrichtenfelder&quot;Gibt die Eigenschaften der Komponente &quot;Nachricht erstellen&quot;an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie in SRP gespeichert werden kann. Die Standardeinstellung sind zwei Einträge: 
*Betreff* und *Inhalt*.

* **[!UICONTROL Begrenzung]** der Größe des Meldungsfelds Die maximale Anzahl von Byte im Meldungsfeld jedes Benutzers. Der Standardwert ist 
*1073741824* (1 GB).

* **[!UICONTROL Begrenzung]** der Anzahl der Nachrichten Die Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 gibt an, dass eine unbegrenzte Anzahl von Nachrichten zulässig ist, sofern die Größe des Meldungsfelds begrenzt ist. Der Standardwert ist 
*10000* (10 k).

* **[!UICONTROL Benachrichtigen Sie den Versand bei]** aktivierter Option den Absender, wenn der Versand bei einigen Empfängern fehlschlägt. Der Standardwert ist 
*markiert*.

* **[!UICONTROL Versand-Absender-ID]** Name des Absenders, der in der Meldung über den Versand fehlgeschlagen angezeigt wird. Der Standardwert ist 
*failureNotifier*.

* **[!UICONTROL Fehlermeldungsvorlagenpfad]** Absoluter Pfad zum Fehlermeldungsvorlagenstamm des Versands. Der Standardwert ist 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]** Gibt an, wie oft eine Meldung erneut gesendet werden soll, die nicht zugestellt werden kann. Der Standardwert ist 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]** Anzahl der Sekunden, die zwischen Versuchen, eine Nachricht bei fehlgeschlagenem Senden erneut zu senden, gewartet werden soll. Der Standardwert ist *100 *(Sekunden).

* **[!UICONTROL Anzahl der Updatepool-Größe]** Anzahl der gleichzeitigen Threads, die für die Zähleraktualisierung verwendet werden. Der Standardwert ist 
*10*.

* **[!UICONTROL inbox.path.name]**(
*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den **`inbox`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**(
*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den **`senditems`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/sentitems* .

* **[!UICONTROL supportAttachments.name]** Wenn diese Option aktiviert ist, können Benutzer ihren Nachrichten Anlagen hinzufügen. Der Standardwert ist 
*markiert*.

* **[!UICONTROL batchSize.name]** Anzahl der Meldungen, die zusammen für einen Senden gesendet werden, wenn sie an eine große Gruppe von Empfängern gesendet werden. Der Standardwert ist 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]** Wenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Der Standardwert ist 
*104857600* (100 MB)

* **[!UICONTROL attachmentTypeBlocklist.name]** Eine Blockierungsliste von Dateierweiterungen mit dem Präfix
**.**&quot;, die vom System abgelehnt werden. Wenn sie nicht auf die Blockierungsliste gesetzt wird, ist die Erweiterung zulässig. Erweiterungen können mit den Symbolen &#39;**+**&#39; und &#39;**-**&#39; hinzugefügt oder entfernt werden. Default is *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Aktion erforderlich*)** Eine Zulassungsliste von Dateierweiterungen, das Gegenteil von der Blockierungsliste. Um alle Dateierweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zuzulassen, verwenden Sie das Symbol &#39;**-**&#39;, um den einzelnen leeren Eintrag zu entfernen.

* **[!UICONTROL serviceSelector.name]**(*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss in der OSGi-Konfiguration für die *Ausführungspfade* enthalten sein [ wie `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), `/bin/`und `/apps/``/services/`. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`** Wert für die `Message List and Compose Message components` (siehe [Nachrichtenfunktion](configure-messaging.md)) bereitgestellt. Die Standardeinstellung ist */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]** Verwenden 
**Nachrichtenfelder Zulassungsliste**.

>[!CAUTION]
>
>Jedes Mal, wenn eine `Messaging Operations Service` Konfiguration zur Bearbeitung geöffnet wird und sie entfernt `allowedAttachmentTypes.name` wurde, wird ein leerer Eintrag erneut hinzugefügt, damit die Eigenschaft konfiguriert werden kann. Ein einzelner leerer Eintrag deaktiviert Dateianlagen effektiv.
>
>Um alle Dateierweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zuzulassen, verwenden Sie das Symbol &#39;**-**&#39;, um (erneut) den einzelnen leeren Eintrag zu entfernen, bevor Sie auf **[!UICONTROL Speichern]** klicken.

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit zur Fehlerbehebung besteht darin, [Debugging-Meldungen im Protokoll zu aktivieren.](../../help/sites-administering/troubleshooting.md)

Siehe auch [Anmelder und Autoren für individuelle Services](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
