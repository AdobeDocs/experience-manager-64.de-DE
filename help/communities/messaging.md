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
role: Administrator
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 4%

---

# Messaging konfigurieren {#configuring-messaging}

## Überblick {#overview}

Die Messaging-Funktion für AEM Communities bietet angemeldeten Site-Besuchern (Mitgliedern) die Möglichkeit, Nachrichten miteinander zu senden, auf die bei der Anmeldung auf der Site zugegriffen werden kann.

Das Messaging für eine Community-Site wird aktiviert, indem während der [Community-Site-Erstellung](sites-console.md) ein Kontrollkästchen aktiviert wird.

Auf dieser Seite finden Sie Informationen zur Standardkonfiguration und möglichen Anpassungen.

Weitere Informationen für Entwickler finden Sie unter [Messaging Essentials](essentials-messaging.md).

## Messaging Operations Service {#messaging-operations-service}

Der [AEM Communities Messaging Operations-Dienst](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifiziert den Endpunkt, der Messaging-bezogene Anfragen verarbeitet, die Ordner, die der Dienst zum Speichern von Nachrichten verwenden soll, und wenn Nachrichten Dateianhänge enthalten können, welche Dateitypen sind zulässig.

Für Community-Sites, die mit der [Communities Sites-Konsole](sites-console.md) erstellt wurden, ist bereits eine Instanz des Dienstes vorhanden, wobei der Posteingang auf `/mail/community/inbox` gesetzt ist.

### Community Messaging Operations Service {#community-messaging-operations-service}

Wie unten gezeigt, existiert eine Konfiguration des Dienstes für Sites, die mit dem [Website-Erstellungsassistenten](sites-console.md) erstellt wurden. Die Konfiguration kann durch Auswahl des Stiftsymbols neben der Konfiguration angezeigt oder bearbeitet werden:

![chlimage_1-63](assets/chlimage_1-63.png)

### Neue Konfiguration {#new-configuration}

Um eine neue Konfiguration hinzuzufügen, klicken Sie auf das Pluszeichen &quot;**+**&quot;neben dem Namen des Dienstes:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Nachrichtenfelder]**
AllowlistGibt die Eigenschaften der Komponente Nachricht erstellen an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie im SRP gespeichert werden kann. Der Standardwert ist zwei Einträge: 
** Betreff und  *Inhalt*.

* **[!UICONTROL Maximale Größe des Nachrichtenfelds]**
Die maximale Anzahl von Bytes im Nachrichtenfeld jedes Benutzers. Der Standardwert ist 
*1073741824*  (1 GB).

* **[!UICONTROL Begrenzung]**
der Nachrichtenanzahl: Die Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 zeigt an, dass eine unbegrenzte Anzahl von Nachrichten zulässig ist, sofern die Größe des Meldungsfelds begrenzt ist. Der Standardwert ist 
*10000*  (10 k).

* **[!UICONTROL Benachrichtigung bezüglich]**
fehlgeschlagener SendungenIst diese Option aktiviert, benachrichtigen Sie den Absender, wenn bei einigen Empfängern die Zustellung fehlschlägt. Der Standardwert ist 
*markiert*.

* **[!UICONTROL Fehler beim Versand]**
Absender-IDName des Absenders, der in der Nachricht mit fehlgeschlagenen Sendungen angezeigt wird. Der Standardwert ist 
*failureNotifier*.

* **[!UICONTROL Pfad]**
der Fehlermeldungsvorlage Absoluter Pfad zum Stamm der fehlgeschlagenen Nachrichtenvorlage für den Versand. Der Standardwert ist 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.]**
nameGibt an, wie oft eine erneute Nachricht versucht werden soll, die nicht zugestellt werden kann. Der Standardwert ist 
*3*.

* **[!UICONTROL minWaitBetweenRetries.]**
nameAnzahl der Sekunden, die zwischen Versuchen gewartet werden sollen, die Nachricht bei fehlgeschlagenem Versand erneut zu senden. Der Standardwert ist *100 * (Sekunden).

* **[!UICONTROL Anzahl der aktualisierten Poolgröße]**
Anzahl der gleichzeitigen Threads, die für die Aktualisierung der Anzahl verwendet werden. Der Standardwert ist 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Erforderlich*) Der Pfad, der relativ zum Knoten des Benutzers (/home/users/*username*) für den  **`inbox`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich ( &#39;/&#39;) enden. Der Standardwert ist */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**
(
*Erforderlich*) Der Pfad, der relativ zum Knoten des Benutzers (/home/users/*username*) für den  **`senditems`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich ( &#39;/&#39;) enden. Der Standardwert ist */mail/sentitems* .

* **[!UICONTROL supportAttachments.]**
nameIst diese Option aktiviert, können Benutzer ihren Nachrichten Anlagen hinzufügen. Der Standardwert ist 
*markiert*.

* **[!UICONTROL batchSize.]**
nameAnzahl der Nachrichten, die im Batch-Vorgang für einen Versand an eine große Empfängergruppe gesendet werden. Der Standardwert ist 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.]**
nameWenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Der Standardwert ist 
*104857600*  (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.]**
nameEine Blockierungsliste von Dateierweiterungen mit dem Präfix &quot;
**.**&#39;, das vom System abgelehnt wird. Wenn die Erweiterung nicht auf die Blockierungsliste gesetzt wird, ist sie zulässig. Erweiterungen können mit den Symbolen &#39;**+**&#39; und &#39;**-**&#39; hinzugefügt oder entfernt werden. Der Standardwert ist *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Aktion erforderlich*)** Eine Zulassungsliste von Dateierweiterungen, das Gegenteil von der Blockierungsliste. Um alle Dateierweiterungen zuzulassen, mit Ausnahme der auf die Blockierungsliste gesetzt, verwenden Sie das Symbol &quot;**-**&quot;, um den einzelnen leeren Eintrag zu entfernen.

* **[!UICONTROL serviceSelector.name]**
 (*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss in der Konfigurationseinstellung *Ausführungspfade* der OSGi-Konfiguration [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver) enthalten sein, z. B. `/bin/`, `/apps/` und `/services/`. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`**-Wert für `Message List and Compose Message components` bereitgestellt (siehe [Nachrichtenfunktion](configure-messaging.md)). Die Standardeinstellung ist */bin/messaging* .

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**Nachrichtenfelder - Zulassungsliste**.

>[!CAUTION]
>
>Jedes Mal, wenn eine `Messaging Operations Service`-Konfiguration zur Bearbeitung geöffnet wird und `allowedAttachmentTypes.name` entfernt wurde, wird ein leerer Eintrag erneut hinzugefügt, um die Eigenschaft konfigurierbar zu machen. Ein einzelner leerer Eintrag deaktiviert Dateianlagen effektiv.
>
>Um alle Dateierweiterungen zuzulassen, mit Ausnahme der auf die Blockierungsliste gesetzt, verwenden Sie das Symbol &quot;**-**&quot;, um (erneut) den einzelnen leeren Eintrag zu entfernen, bevor Sie auf **[!UICONTROL Speichern]** klicken.

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit, Probleme zu beheben, besteht darin, [Debugging-Meldungen im Protokoll zu aktivieren.](../../help/sites-administering/troubleshooting.md)

Siehe auch [Logger und Writer für einzelne Dienste](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
