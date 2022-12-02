---
title: Messaging konfigurieren
seo-title: Configuring Messaging
description: Communities-Messaging
seo-description: Communities messaging
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 4%

---

# Messaging konfigurieren {#configuring-messaging}

## Übersicht {#overview}

Die Messaging-Funktion für AEM Communities bietet angemeldeten Site-Besuchern (Mitgliedern) die Möglichkeit, Nachrichten miteinander zu senden, auf die bei der Anmeldung auf der Site zugegriffen werden kann.

Messaging wird für eine Community-Site aktiviert, indem Sie ein Kästchen bei [Community-Site-Erstellung](sites-console.md).

Auf dieser Seite finden Sie Informationen zur Standardkonfiguration und möglichen Anpassungen.

Weitere Informationen für Entwickler finden Sie unter [Grundlagen zu Messaging](essentials-messaging.md).

## Messaging Operations-Dienst {#messaging-operations-service}

Die [AEM Communities Messaging-Dienst](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifiziert den Endpunkt, der mit Messaging-bezogenen Anfragen verarbeitet, die Ordner, die der Dienst zum Speichern von Nachrichten verwenden soll, und wenn Nachrichten Dateianhänge enthalten können, welche Dateitypen sind zulässig.

Für Community-Sites, die mithilfe der [Communities Sites-Konsole](sites-console.md), eine Instanz des Dienstes bereits vorhanden ist, wobei der Posteingang auf `/mail/community/inbox`.

### Community Messaging-Dienst {#community-messaging-operations-service}

Wie unten gezeigt, existiert eine Konfiguration des Dienstes für Sites, die mit der [Assistent zur Site-Erstellung](sites-console.md). Die Konfiguration kann durch Auswahl des Stiftsymbols neben der Konfiguration angezeigt oder bearbeitet werden:

![chlimage_1-63](assets/chlimage_1-63.png)

### Neue Konfiguration {#new-configuration}

Um eine neue Konfiguration hinzuzufügen, wählen Sie das Pluszeichen &quot;**+**&#39; neben dem Namen des Dienstes:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Zulassungsliste der Nachrichtenfelder]**
Gibt die Eigenschaften der Komponente Nachricht erstellen an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie im SRP gespeichert werden kann. Der Standardwert ist zwei Einträge: 
*subject* und *content*.

* **[!UICONTROL Größenbeschränkung für Nachrichtenfelder]**
Die maximale Anzahl von Bytes im Nachrichtenfeld jedes Benutzers. Der Standardwert ist 
*1073741824* (1 GB).

* **[!UICONTROL Begrenzung der Nachrichtenanzahl]**
Die Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 zeigt an, dass eine unbegrenzte Anzahl von Nachrichten zulässig ist, sofern die Größe des Meldungsfelds begrenzt ist. Der Standardwert ist 
*10000* (10k).

* **[!UICONTROL Versandfehler benachrichtigen]**
Wenn diese Option aktiviert ist, benachrichtigen Sie den Absender, wenn der Nachrichtenversand bei einigen Empfängern fehlschlägt. Der Standardwert ist 
*markiert*.

* **[!UICONTROL Versandabsender-ID eines fehlgeschlagenen Versands]**
Name des Absenders, der in der Nachricht mit fehlgeschlagenen Sendungen angezeigt wird. Der Standardwert ist 
*failureNotifier*.

* **[!UICONTROL Pfad der Fehlermeldungsvorlage]**
Absoluter Pfad zum Stamm der fehlgeschlagenen Nachrichtenvorlage für den Versand. Der Standardwert ist 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]**
Gibt an, wie oft eine erneute Nachricht versucht werden soll, die nicht zugestellt werden kann. Der Standardwert ist 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**
Anzahl der Sekunden, die zwischen Versuchen gewartet werden soll, die Nachricht bei fehlgeschlagenem Versand erneut zu senden. Der Standardwert ist *100 * (Sekunden).

* **[!UICONTROL Anzahl der Aktualisierungspool-Größe]**
Anzahl der gleichzeitigen Threads, die für die Aktualisierung der Anzahl verwendet werden. Der Standardwert ist 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Erforderlich*) Der Pfad, relativ zum Knoten des Benutzers (/home/users/*Benutzername*), um für die **`inbox`** Ordner. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich ( &#39;/&#39;) enden. Der Standardwert ist */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**
(
*Erforderlich*) Der Pfad, relativ zum Knoten des Benutzers (/home/users/*Benutzername*), um für die **`senditems`** Ordner. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich ( &#39;/&#39;) enden. Der Standardwert ist */mail/sentitems* .

* **[!UICONTROL supportAttachments.name]**
Wenn diese Option aktiviert ist, können Benutzer ihren Nachrichten Anlagen hinzufügen. Der Standardwert ist 
*markiert*.

* **[!UICONTROL batchSize.name]**
Anzahl der Nachrichten, die im Batch-Vorgang an eine große Empfängergruppe gesendet werden. Der Standardwert ist 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]**
Wenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Der Standardwert ist 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.name]**
Eine Blockierungsliste von Dateierweiterungen mit dem Präfix &quot;
**möglich.**&#39;, das vom System abgelehnt wird. Wenn die Erweiterung nicht auf die Blockierungsliste gesetzt wird, ist sie zulässig. Erweiterungen können mit dem **+**&#39; und &#39;**-**&quot;. Der Standardwert ist *STANDARD*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Erforderliche Aktion*)** Eine Zulassungsliste von Dateierweiterungen, das Gegenteil von der Blockierungsliste. Um alle Dateierweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zu ermöglichen, verwenden Sie den **-**&quot;, um den einzelnen leeren Eintrag zu entfernen.

* **[!UICONTROL serviceSelector.name]**
(*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss einen im *Ausführungspfade* Konfigurationseinstellung der OSGi-Konfiguration [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), z. B. `/bin/`, `/apps/`und `/services/`. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`** Wert für `Message List and Compose Message components` (siehe [Nachrichtenfunktion](configure-messaging.md)). Der Standardwert ist */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
Verwendung 
**Zulassungsliste der Nachrichtenfelder**.

>[!CAUTION]
>
>Jedes Mal, wenn ein `Messaging Operations Service` -Konfiguration zur Bearbeitung geöffnet ist, wenn `allowedAttachmentTypes.name` entfernt wurde, wird ein leerer Eintrag erneut hinzugefügt, um die Eigenschaft konfigurierbar zu machen. Ein einzelner leerer Eintrag deaktiviert Dateianlagen effektiv.
>
>Um alle Dateierweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zu ermöglichen, verwenden Sie den **-**&quot;(erneut) Symbol, um den einzelnen leeren Eintrag zu entfernen, bevor Sie auf **[!UICONTROL Speichern]**.

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit, Probleme zu beheben, besteht darin, [Debugging von Meldungen im Protokoll.](../../help/sites-administering/troubleshooting.md)

Siehe auch [Logger und Writer für einzelne Dienste](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
