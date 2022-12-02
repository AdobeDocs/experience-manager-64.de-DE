---
title: E-Mail konfigurieren
seo-title: Configuring Email
description: E-Mail-Konfiguration für Communities
seo-description: Email configuration for Communities
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: Admin
exl-id: 0a0222e7-ca30-4603-94ad-582005b2de11
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 5%

---

# E-Mail konfigurieren {#configuring-email}

AEM Communities verwendet E-Mail für

* [Communities-Benachrichtigungen](notifications.md)
* [Communities-Abonnements](subscriptions.md)

Standardmäßig ist die E-Mail-Funktion nicht funktionsfähig, da sie die Spezifikation eines SMTP-Servers und SMTP-Benutzers erfordert.

>[!CAUTION]
>
>E-Mail für Benachrichtigungen und Abonnements darf nur auf der [primärer Herausgeber](deploy-communities.md#primary-publisher).

## Standard-E-Mail-Dienstkonfiguration {#default-mail-service-configuration}

Der Standard-E-Mail-Dienst ist sowohl für Benachrichtigungen als auch für Abonnements erforderlich.

* Im primären Herausgeber
* Mit Administratorrechten angemeldet
* Zugriff auf [Web-Konsole](../../help/sites-deploying/configuring-osgi.md)

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie die `Day CQ Mail Service`
* Bearbeiten-Symbol auswählen

Dies basiert auf der Dokumentation für [Konfigurieren von E-Mail-Benachrichtigungen](../../help/sites-administering/notification.md), jedoch mit einem Unterschied in diesem Feld `"From" address` is *not* erforderlich und sollte leer gelassen werden.

Beispiel: (nur zu Veranschaulichungszwecken mit Werten gefüllt):

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL Hostname des SMTP-Servers]**: *(erforderlich)* Der zu verwendende SMTP-Server.

* **[!UICONTROL SMTP-Server-Anschluss]** *(erforderlich)* Der SMTP-Server-Port muss 25 oder höher sein.

* **[!UICONTROL SMTP-Benutzer]**: *(erforderlich)* Der SMTP-Benutzer.

* **[!UICONTROL SMTP-Kennwort]**: *(erforderlich)* Das Kennwort des SMTP-Benutzers.

* **[!UICONTROL &quot;Von&quot;-Adresse]**: Leer lassen
* **[!UICONTROL SMTP SSL verwenden]**: Wenn diese Option aktiviert ist, wird sichere E-Mail gesendet. Stellen Sie sicher, dass der Port auf 465 oder wie für den SMTP-Server erforderlich eingestellt ist.
* **[!UICONTROL Debug-E-Mail]**: Ist diese Option aktiviert, wird die Protokollierung von SMTP-Serverinteraktionen aktiviert.

## AEM Communities-E-Mail-Konfiguration {#aem-communities-email-configuration}

Einmal [Standard-E-Mail-Dienst](#default-mail-service-configuration) konfiguriert ist, werden die beiden vorhandenen Instanzen der `AEM Communities Email Reply Configuration` Die in der Version enthaltene OSGi-Konfiguration wird funktionsfähig.

Nur die Instanz für Abonnements muss weiter konfiguriert werden, wenn E-Mail-Antworten zugelassen werden.

1. ` [email](#configuration-for-notifications)` Veröffentlichungsinstanz

   für Benachrichtigungen, die keine Antwort-E-Mail unterstützen und nicht geändert werden sollten

1. ` [subscriptions-email](#configuration-for-subscriptions)` Veröffentlichungsinstanz

   erfordert eine Konfiguration, um die Erstellung von Beiträgen aus einer Antwort-E-Mail vollständig zu aktivieren

So greifen Sie auf die Communities-E-Mail-Konfigurationsinstanzen zu:

* Im primären Herausgeber
* Mit Administratorrechten angemeldet
* Zugriff auf [Web-Konsole](../../help/sites-deploying/configuring-osgi.md)

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen `AEM Communities Email Reply Configuration`

![chlimage_1-99](assets/chlimage_1-99.png)

### Konfiguration für Benachrichtigungen {#configuration-for-notifications}

Die Instanz von `AEM Communities Email Reply Configuration` Die OSGi-Konfiguration mit der E-Mail &quot;Name&quot;ist für die Benachrichtigungsfunktion vorgesehen. Diese Funktion enthält keine E-Mail-Antwort.

Diese Konfiguration sollte nicht geändert werden.

* Suchen Sie die `AEM Communities Email Reply Configuration`
* Bearbeiten-Symbol auswählen
* Überprüfen Sie die **Name** is `email`

* Überprüfen **Beitrag aus Antwort-E-Mail erstellen** is `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### Konfiguration für Abonnements {#configuration-for-subscriptions}

Bei Communities-Abonnements ist es möglich, die Möglichkeit für ein Mitglied zu aktivieren oder zu deaktivieren, Inhalte zu posten, indem es auf eine E-Mail antwortet.

* Suchen Sie die `AEM Communities Email Reply Configuration`
* Bearbeiten-Symbol auswählen
* Überprüfen Sie die **Name** is `subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL Name]** : *(erforderlich)* `subscriptions-email`. Nicht bearbeiten.

* **[!UICONTROL Beitrag aus Antwort-E-Mail erstellen]**: Wenn diese Option aktiviert ist, kann der Empfänger der Abonnement-E-Mail Inhalte durch Senden einer Antwort posten. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL Getrackte ID zur Kopfzeile hinzufügen]**: Der Standardwert ist `Reply-To`.

* **[!UICONTROL Höchstlänge des Betreffs]**: Wenn die Tracker-ID zur Betreffzeile hinzugefügt wird, ist dies die maximale Länge des Betreffs, ausgenommen die verfolgte ID, nach der sie abgeschnitten wird. Beachten Sie, dass dies so klein wie möglich sein sollte, um zu verhindern, dass getrackte ID-Informationen verloren gehen. Der Standardwert ist 200.
* **[!UICONTROL E-Mail-Adresse &quot;Von&quot;]**: *(erforderlich)* Adresse, von der die Benachrichtigungs-E-Mail gesendet wird. Ist wahrscheinlich gleich **SMTP-Benutzer** festgelegt für [Standard-E-Mail-Dienst](#configuredefaultmailservice). Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Antwort an Trennzeichen]**: Wenn die Tracker-ID zur Kopfzeile Antwort hinzugefügt wird, wird dieses Trennzeichen verwendet. Der Standardwert ist `+` (Pluszeichen).

* **[!UICONTROL Tracker-ID-Präfix im Betreff]**: Wenn die Tracker-ID der Betreffzeile hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `post#`.

* **[!UICONTROL Tracker-ID-Präfix im Nachrichtentext]**: Wenn die Tracker-ID zum Nachrichtentext hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `Please do not remove this:`.

* **[!UICONTROL E-Mail als HTML]**: Wenn diese Option aktiviert ist, wird der Inhaltstyp der E-Mail als `"text/html;charset=utf-8"`. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Standardbenutzername]**: Dieser Name wird für Benutzer ohne Namen verwendet. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Vorlagen-Stammpfad]**: Die E-Mail wird mithilfe einer Vorlage erstellt, die in diesem Stammverzeichnis gespeichert ist. Der Standardwert ist `/etc/community/templates/subscriptions-email`.

## Abruf-Importtool konfigurieren {#configure-polling-importer}

Damit die E-Mail in das Repository geladen werden kann, muss ein Abruf-Importtool konfiguriert und die Eigenschaften im Repository manuell konfiguriert werden.

### Neuen Abruf-Importtool hinzufügen {#add-new-polling-importer}

* Im primären Herausgeber
* Mit Administratorrechten angemeldet
* Navigieren Sie zur Abruf-Importtool-Konsole. Beispiel: [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* Klicken Sie auf **[!UICONTROL Hinzufügen]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL Typ]**: *(erforderlich)* Nach unten zur Auswahl ziehen `POP3 (over SSL).`

* **[!UICONTROL URL]**: *(erforderlich)* Der ausgehende Mail-Server. Beispiel: `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL Import in Pfad]**&amp;ast;: *(erforderlich)* Legen Sie fest auf `/content/usergenerated/mailFolder/postEmails`
durch Navigation zum 
`postEmails`Ordner und wählen Sie **OK**

* **[!UICONTROL Aktualisierungsintervall in Sekunden]**: *(optional)* Der für den Standard-E-Mail-Dienst konfigurierte Mailserver weist möglicherweise Anforderungen in Bezug auf den Wert des Aktualisierungsintervalls auf. Gmail erfordert beispielsweise möglicherweise ein Intervall von `300`.

* **[!UICONTROL Anmelden]**: *(optional)*

* **[!UICONTROL Passwort]**: *(optional)*

* Wählen Sie **[!UICONTROL OK]** aus

### Anpassen des Protokolls für den neuen Abruf-Importtool {#adjust-protocol-for-new-polling-importer}

Sobald die neue Abruffunktion gespeichert wurde, müssen die Eigenschaften des E-Mail-Importtools für Abonnements weiter geändert werden, um das Protokoll von `POP3` nach `emailreply`

Verwenden [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Im primären Herausgeber
* Mit Administratorrechten angemeldet
* Navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importers/olling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* Wählen Sie die neu erstellte Konfiguration aus
* Ändern Sie die folgenden Eigenschaften

   * **feedType**: replace `pop3s` mit **`emailreply`**
   * **source**: Quellprotokoll ersetzen `pop3s://` mit **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

Die roten Dreiecke geben die geänderten Eigenschaften an. Achten Sie darauf, die Änderungen zu speichern:

* Klicken Sie auf **[!UICONTROL Alle speichern]**
