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
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 1%

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

* **[!UICONTROL Nachrichtenfelder Zulassungsliste]** Gibt die Eigenschaften der Komponente &quot;Nachricht erstellen&quot;an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie in SRP gespeichert werden kann. Die Standardeinstellung sind zwei Einträge: *Betreff* und *Inhalt*.
**[!UICONTROL Begrenzung]** der Größe des Meldungsfelds Die maximale Anzahl von Byte im Meldungsfeld jedes Benutzers. Der Standardwert ist *1073741824* (1 GB).**

* **[!UICONTROL Begrenzung]** der Anzahl der Nachrichten Die Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 gibt an, dass eine unbegrenzte Anzahl von Nachrichten zulässig ist, sofern die Größe des Meldungsfelds begrenzt ist. Der Standardwert ist *10000* (10 k).
**[!UICONTROL Benachrichtigen Sie den Versand bei]** aktivierter Option den Absender, wenn der Versand bei einigen Empfängern fehlschlägt. Default is *checked*.*

* **[!UICONTROL Versand-Absender-ID]** Name des Absenders, der in der Meldung über den Versand fehlgeschlagen angezeigt wird. Der Standardwert ist *failureNotifier*.
**[!UICONTROL Fehlermeldungsvorlagenpfad]** Absoluter Pfad zum Fehlermeldungsvorlagenstamm des Versands. Der Standardwert ist */etc/notification/messaging/default*.*

* **[!UICONTROL maxRetries.name]** Gibt an, wie oft eine Meldung erneut gesendet werden soll, die nicht zugestellt werden kann. Der Standardwert ist *3*.
**[!UICONTROL minWaitBetweenRetries.name]** Anzahl der Sekunden, die zwischen Versuchen, eine Nachricht erneut zu senden, bei fehlgeschlagenem Senden zu warten, gewartet werden soll. Der Standardwert ist *100 *(Sekunden).*

* **[!UICONTROL Anzahl der Updatepool-Größe]** Anzahl der gleichzeitigen Threads, die für die Zähleraktualisierung verwendet werden. Der Standardwert ist *10*.
**[!UICONTROL inbox.path.name]**(*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den **`inbox`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/inbox* .*

* **[!UICONTROL sentitems.path.name]**(*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den **`senditems`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/sentitems* .
**[!UICONTROL supportAttachments.name]** Wenn diese Option aktiviert ist, können Benutzer ihren Nachrichten Anlagen hinzufügen. Default is *checked*.*

* **[!UICONTROL batchSize.name]** Anzahl der Meldungen, die zusammen für einen Senden gesendet werden, wenn sie an eine große Gruppe von Empfängern gesendet werden. Der Standardwert ist *100*.
**[!UICONTROL maxTotalAttachmentSize.name]** Wenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Default is *104857600* (100 MB).*

* **[!UICONTROL attachmentTypeAllowlist.name]** Eine blockierungsliste von Dateierweiterungen, der &quot;**vorangestellt wird.**&quot;, die vom System abgelehnt werden. Wenn kein auf die Blockierungsliste gesetzt wird, ist die Erweiterung zulässig. Erweiterungen können mit den Symbolen &#39;**+**&#39; und &#39;**-**&#39; hinzugefügt oder entfernt werden. Default is *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

**(*Aktion erforderlich*)** Eine zulassungsliste von Dateierweiterungen im , das Gegenteil von der blockierungsliste. Wenn Sie alle Dateierweiterungen mit auf die Blockierungsliste gesetzt zulassen möchten, mit Ausnahme der Dateierweiterungen, verwenden Sie das Symbol &#39;**-**&#39;, um den einzelnen leeren Eintrag zu entfernen.

* **[!UICONTROL serviceSelector.name]**(*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss in der OSGi-Konfiguration für die *Ausführungspfade* enthalten sein [ wie `Apache Sling Servlet/Script Resolver and Error Handler`[#$tu39], `/bin/`und `/apps/``/services/`. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`** Wert für die `Message List and Compose Message components` (siehe [Nachrichtenfunktion](configure-messaging.md)) bereitgestellt. Die Standardeinstellung ist */bin/messaging* .


* 


* 


* 


* 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeAllowlist.name]**
A blocklist of file extensions, prefixed with &#39;
**.**&#39;, that will be rejected by the system. If not blocklisted, then the extension is allowed. Extensions may be added or removed using the &#39;**+**&#39; and &#39;**-**&#39; icons. Default is *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Action Required*)** An allowlist of file extensions, the opposite of the blocklist. To allow all file extensions, except for those blocklisted, use the &#39;**-**&#39; icon to remove the single empty entry.

* **[!UICONTROL serviceSelector.name]**
(*Required*) An absolute path (endpoint) through which the service is invoked (a virtual resource). The root of the path chosen must be one included in the *Execution Paths* configuration setting of OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`-ERR:REF-NOT-FOUND-, such as `/bin/`, `/apps/`, and `/services/`. To select this configuration for a site&#39;s messaging feature, this endpoint is provided as the **`Service selector`** value for the `Message List and Compose Message components` (see [Message Feature](configure-messaging.md)). The default is */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
Use 
**Message Fields Allowlist**.

>[!CAUTION]
>
>Each time a `Messaging Operations Service` configuration is opened for edit, if `allowedAttachmentTypes.name` had been removed, an empty entry is re-added to make the property configurable. A single empty entry effectively disables file attachments.
>
>To allow all file extensions, except for those blocklisted, use the &#39;**-**&#39; icon to (again) remove the single empty entry before clicking **[!UICONTROL Save]**.

## Troubleshooting {#troubleshooting}

One way to troubleshoot problems is to enable [debugging messages in the log.](../../help/sites-administering/troubleshooting.md)

See also [Loggers and Writers for Individual Services](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

The package to monitor is `com.adobe.cq.social.messaging`.
