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
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 4%

---


# Konfigurieren von Messaging {#configuring-messaging}

## Überblick {#overview}

Die Messaging-Funktion für AEM Communities ermöglicht es Besuchern (Teilnehmern) mit angemeldeten Sites, Nachrichten an andere zu senden, auf die bei der Anmeldung auf der Site zugegriffen werden kann.

Die Messaging-Funktion ist für eine Community-Site aktiviert, indem Sie bei [Community-Site-Erstellung](sites-console.md) ein Kontrollkästchen aktivieren.

Auf dieser Seite finden Sie Informationen zur Standardkonfiguration und möglichen Anpassungen.

Weitere Informationen für Entwickler finden Sie unter [Messaging Essentials](essentials-messaging.md).

## Messaging Operations Service {#messaging-operations-service}

Der [AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifiziert den Endpunkt, der Messaging-bezogene Anfragen verarbeitet, die Ordner, die der Dienst zum Speichern von Nachrichten verwenden sollte, und wenn Meldungen Dateianhänge enthalten können, welche Dateitypen sind zulässig.

Für Community-Sites, die mit der Konsole [Communities Sites](sites-console.md) erstellt wurden, ist bereits eine Instanz des Dienstes vorhanden, wobei der Posteingang auf `/mail/community/inbox` eingestellt ist.

### Community Messaging Operations Service {#community-messaging-operations-service}

Wie unten gezeigt, existiert eine Konfiguration des Dienstes für Sites, die mit dem [Assistenten zum Erstellen der Site](sites-console.md) erstellt wurden. Die Konfiguration kann angezeigt oder bearbeitet werden, indem Sie auf das Stiftsymbol neben der Konfiguration klicken:

![chlimage_1-63](assets/chlimage_1-63.png)

### Neue Konfiguration {#new-configuration}

Um eine neue Konfiguration hinzuzufügen, wählen Sie neben dem Namen des Dienstes das Pluszeichen &quot;**+**&quot;aus:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Nachrichtenfelder]**
AllowlistGibt die Eigenschaften der Komponente &quot;Nachricht erstellen&quot;an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie in SRP gespeichert werden kann. Die Standardeinstellung sind zwei Einträge: 
** Subjekt und  *Inhalt*.

* **[!UICONTROL Begrenzung der]**
Größe des MeldungsfeldsDie maximale Anzahl von Byte im Meldungsfeld jedes Benutzers. Der Standardwert ist 
*1073741824* (1 GB).

* **[!UICONTROL Begrenzung der]**
Anzahl der NachrichtenDie Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 gibt an, dass eine unbegrenzte Anzahl von Nachrichten zulässig ist, sofern die Größe des Meldungsfelds begrenzt ist. Der Standardwert ist 
*10000* (10 k).

* **[!UICONTROL Benachrichtigen Sie Versand]**
failureWenn aktiviert, benachrichtigen Sie den Absender, wenn der Versand der Nachricht bei einigen Empfängern fehlschlägt. Der Standardwert ist 
*markiert*.

* **[!UICONTROL Fehler beim Absender]**
des Versands idName des Absenders, der in der Meldung über den Versand mit Fehler angezeigt wird. Der Standardwert ist 
*failureNotifier*.

* **[!UICONTROL Fehlermeldungsvorlage]**
pathAbsoluter Pfad zum Fehlermeldungsvorlagenstamm des Versands. Der Standardwert ist 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.]**
nameGibt an, wie oft eine Meldung erneut gesendet werden soll, die nicht zugestellt werden kann. Der Standardwert ist 
*3*.

* **[!UICONTROL minWaitBetweenRetries.]**
nameAnzahl der Sekunden, die zwischen Versuchen, eine Nachricht erneut zu senden, bei fehlgeschlagenem Senden zu warten, gewartet werden. Der Standardwert ist *100 *(Sekunden).

* **[!UICONTROL Anzahl der aktualisierten Poolgröße]**
Anzahl der gleichzeitigen Threads, die für die Zähleraktualisierung verwendet werden. Der Standardwert ist 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den  **`inbox`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**
(
*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den  **`senditems`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/sentitems* .

* **[!UICONTROL supportAttachments.]**
nameWenn diese Option aktiviert ist, können Benutzer ihren Nachrichten Anlagen hinzufügen. Der Standardwert ist 
*markiert*.

* **[!UICONTROL batchSize.]**
nameAnzahl der Meldungen, die zusammen für einen Senden gesendet werden, wenn sie an eine große Gruppe von Empfängern gesendet werden. Der Standardwert ist 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.]**
nameWenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Der Standardwert ist 
*104857600* (100 MB)

* **[!UICONTROL attachmentTypeBlocklist.]**
nameEine Blockierungsliste von Dateierweiterungen, mit dem Präfix
**.**&quot;, die vom System abgelehnt werden. Wenn sie nicht auf die Blockierungsliste gesetzt wird, ist die Erweiterung zulässig. Erweiterungen können mit den Symbolen &quot;**+**&quot;und &quot;**-**&quot;hinzugefügt oder entfernt werden. Der Standardwert ist *STANDARD*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Aktion erforderlich*)** Eine Zulassungsliste von Dateierweiterungen, das Gegenteil der Blockierungsliste. Um alle Dateierweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zuzulassen, verwenden Sie das Symbol &quot;**-**&quot;, um den einzelnen leeren Eintrag zu entfernen.

* **[!UICONTROL serviceSelector.name]**
(*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss in der Konfigurationseinstellung *Ausführungspfade* von OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), wie `/bin/`, `/apps/` und `/services/` enthalten sein. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`**-Wert für `Message List and Compose Message components` bereitgestellt (siehe [Nachrichtenfunktion](configure-messaging.md)). Die Standardeinstellung ist */bin/messaging* .

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**Nachrichtenfelder Zulassungsliste**.

>[!CAUTION]
>
>Jedes Mal, wenn eine `Messaging Operations Service`-Konfiguration zur Bearbeitung geöffnet wird und `allowedAttachmentTypes.name` entfernt wurde, wird ein leerer Eintrag erneut hinzugefügt, um die Eigenschaft konfigurierbar zu machen. Ein einzelner leerer Eintrag deaktiviert Dateianlagen effektiv.
>
>Um alle Dateierweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zuzulassen, verwenden Sie das Symbol &quot;**-**&quot;, um (erneut) den einzelnen leeren Eintrag zu entfernen, bevor Sie auf **[!UICONTROL Speichern]** klicken.

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit zur Fehlerbehebung besteht darin, [Debugging-Meldungen im Protokoll zu aktivieren.](../../help/sites-administering/troubleshooting.md)

Siehe auch [Anmelder und Autoren für individuelle Dienste](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
