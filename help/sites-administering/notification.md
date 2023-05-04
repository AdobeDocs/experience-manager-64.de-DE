---
title: Konfigurieren von E-Mail-Benachrichtigungen
seo-title: Configuring Email Notification
description: Erfahren Sie, wie Sie E-Mail-Benachrichtigungen in AEM konfigurieren.
seo-description: Learn how to configure Email Notification in AEM.
uuid: 6cbdc312-860b-4a69-8bbe-2feb32204a27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6466d7b8-e308-43c5-acdc-dec15f796f64
exl-id: ea12035c-09b6-4197-ab23-c27fe71e7432
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1170'
ht-degree: 64%

---

# Konfigurieren von E-Mail-Benachrichtigungen{#configuring-email-notification}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM sendet E-Mail-Benachrichtigungen an Benutzer, die:

* Seitenereignisse wie Änderungen oder Replikationen abonniert haben. Im Abschnitt [Benachrichtigungs-Posteingang](/help/sites-classic-ui-authoring/author-env-inbox.md#subscribing-to-notifications) ist beschrieben, wie solche Ereignisse abonniert werden können.

* Forumsveranstaltungen abonniert haben.
* Führen Sie einen Schritt in einem Workflow aus. Die [Teilnehmer-Schritt](/help/sites-developing/workflows-step-ref.md#participant-step) -Abschnitt beschreibt den Trigger von E-Mail-Benachrichtigungen in einem Workflow.

Voraussetzungen:

* Für den/die Benutzer muss/müssen in seinem Profil eine gültige E-Mail-Adresse definiert sein.
* Der **Day CQ Mail Service** muss ordnungsgemäß konfiguriert sein.

Wenn ein Benutzer benachrichtigt wird, erhält er eine E-Mail in der Sprache, die in seinem Profil definiert ist. Jede Sprache verfügt über eine eigene Vorlage, die angepasst werden kann. Für neue Sprachen können neue E-Mail-Vorlagen hinzugefügt werden.

>[!NOTE]
>
>Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

## Konfigurieren des Mail-Dienstes {#configuring-the-mail-service}

Damit AEM E-Mails versenden können, muss die **Day CQ Mail Service** muss ordnungsgemäß konfiguriert sein. Sie können die Konfiguration in der Webkonsole anzeigen. Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

Es gelten die folgenden Beschränkungen:

* Der **SMTP-Server-Port** muss 25 oder höher sein.

* Der **SMTP-Server-Hostname** darf nicht leer sein.
* Die **„Von“-Adresse** darf nicht leer sein.

Zum Debuggen eines Problems mit dem **Day CQ Mail Service** können Sie die Protokolle des Dienstes betrachten:

`com.day.cq.mailer.DefaultMailService`

Die Konfiguration sieht in der Web-Konsole wie folgt aus:

![chlimage_1-276](assets/chlimage_1-276.png)

## Konfigurieren des E-Mail-Benachrichtigungskanals {#configuring-the-email-notification-channel}

Wenn Sie entweder Benachrichtigungen zu Seiten- oder Forenereignissen abonniert haben, ist die „Von“-E-Mail-Adresse standardmäßig auf `no-reply@acme.com` eingestellt. Sie können diesen Wert durch die Konfiguration des Diensts **Benachrichtigungs-E-Mail-Kanal** in der Web-Konsole ändern.

Fügen Sie zum Konfigurieren der „Von“-E-Mail-Adresse einen `sling:OsgiConfig`-Knoten zum Repository hinzu. Verwenden Sie das folgende Verfahren, um den Knoten direkt mithilfe von CRXDE Lite hinzuzufügen:

1. Fügen Sie in CRXDE Lite einen Ordner mit dem Namen `config` unter Ihrem Programmordner hinzu.
1. Fügen Sie im Konfigurationsordner einen Knoten mit folgendem Namen hinzu:

   `com.day.cq.wcm.notification.email.impl.EmailChannel` vom Typ `sling:OsgiConfig`

1. Fügen Sie eine `String`-Eigenschaft zum Knoten mit dem Namen `email.from` hinzu. Geben Sie als Wert die E-Mail-Adresse an, die Sie verwenden möchten.

1. Klicken Sie auf **Alle speichern**.

Gehen Sie wie folgt vor, um den Knoten in den Quellordnern des Inhaltspakets zu definieren:

1. Erstellen Sie in `jcr_root/apps/*app_name*/config folder` eine Datei mit dem Namen `com.day.cq.wcm.notification.email.impl.EmailChannel.xml`.

1. Fügen Sie die folgende XML für den Knoten hinzu:

   `<?xml version="1.0" encoding="UTF-8"?> <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig" email.from="name@server.com"/>`
1. Ersetzen Sie den Wert des Attributs `email.from` (`name@server.com`) durch Ihre E-Mail-Adresse.

1. Speichern Sie die Datei.

## Konfigurieren des Workflow-E-Mail-Benachrichtigungsdiensts {#configuring-the-workflow-email-notification-service}

Wenn Sie Workflow-E-Mail-Benachrichtigungen erhalten, werden sowohl die E-Mail-Adresse als auch das Host-URL-Präfix auf Standardwerte gesetzt. Sie können diese Werte ändern, indem Sie die **Day CQ Workflow Email Notification Service** in der Web-Konsole. Wenn Sie dies tun, wird empfohlen, die Änderung im Repository beizubehalten.

Die Standardkonfiguration sieht in der Web-Konsole wie folgt aus:

![chlimage_1-277](assets/chlimage_1-277.png)

### E-Mail-Vorlagen für Seitenbenachrichtigungen {#email-templates-for-page-notification}

E-Mail-Vorlagen für Seitenbenachrichtigungen finden Sie unten:

`/libs/settings/notification-templates/com.day.cq.wcm.core.page`

Die standardmäßige englische Vorlage (`en.txt`) wird wie folgt definiert:

```xml
subject=[CQ Page Event Notification]: Page Event

header=-------------------------------------------------------------------------------------\n \
Time: ${time}\n \
User: ${userFullName} (${userId})\n \
-------------------------------------------------------------------------------------\n\n

message=The following pages were affected by the event: \n \
 \n \
${modifications} \n \
 \n\n
footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Anpassen von E-Mail-Vorlagen für die Seitenbenachrichtigung {#customizing-email-templates-for-page-notification}

Die englische E-Mail-Vorlage für die Seitenbenachrichtigung können Sie wie folgt anpassen:

1. Öffnen Sie in CRXDE die Datei:

   `/libs/settings/notification-templates/com.day.cq.wcm.core.page/en.txt`

1. Ändern Sie die Datei nach Bedarf.
1. Speichern Sie die Änderungen.

Die Vorlage muss das folgende Format aufweisen:

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

Dabei kann &lt;text_x> ein Mix von statischem Text und dynamischen Zeichenfolgenvariablen sein. Die folgenden Variablen können innerhalb der E-Mail-Vorlage für Seitenbenachrichtigungen verwendet werden:

* `${time}`, Ereignisdatum und -uhrzeit

* `${userFullName}`, der vollständige Name des Benutzers, der das Ereignis ausgelöst hat

* `${userId}`, die ID des Benutzers, der das Ereignis ausgelöst hat
* `${modifications}`, beschreibt den Typ des Seitenereignisses und den Seitenpfad im folgenden Format:

   &lt;Seitenereignistyp> => &lt;Seitenpfad>

   Beispiel:

   PageModified => /content/geometrixx/en/products

### E-Mail-Vorlagen für Forumsbenachrichtigungen {#email-templates-for-forum-notification}

E-Mail-Vorlagen für Forumsbenachrichtigungen finden Sie unter:

`/etc/notification/email/default/com.day.cq.collab.forum`

Die standardmäßige englische Vorlage (`en.txt`) wird wie folgt definiert:

```xml
subject=[CQ Forum Notification]

header=-------------------------------------------------------------------------------------\n \
Time: Time: ${time}\n \
Forum Page Path: ${forum.path}\n \
-------------------------------------------------------------------------------------\n\n

message=Page: ${host.prefix}${forum.path}.html\n

footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Anpassen von E-Mail-Vorlagen für die Forumsbenachrichtigung {#customizing-email-templates-for-forum-notification}

Die englische E-Mail-Vorlage für die Forumsbenachrichtigung können Sie wie folgt anpassen:

1. Öffnen Sie in CRXDE die Datei:

   `/etc/notification/email/default/com.day.cq.collab.forum/en.txt`

1. Ändern Sie die Datei nach Bedarf.
1. Speichern Sie die Änderungen.

Die Vorlage muss das folgende Format aufweisen:

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

Dabei kann `<text_x>` ein Mix von statischem Text und dynamischen Zeichenfolgenvariablen sein.

Die folgenden Variablen können innerhalb der E-Mail-Vorlage für Forumsbenachrichtigungen verwendet werden:

* `${time}`, Ereignisdatum und -uhrzeit

* `${forum.path}`, der Pfad zur Forumsseite.

### E-Mail-Vorlagen für Workflow-Benachrichtigung {#email-templates-for-workflow-notification}

Die E-Mail-Vorlage für Workflow-Benachrichtigungen (Englisch) befindet sich unter:

`/libs/settings/workflow/notification/email/default/en.txt`

Sie wird wie folgt definiert:

```xml
subject=Workflow notification: ${event.EventType}

header=-------------------------------------------------------------------------------------\n \
Time: ${event.TimeStamp}\n \
Step: ${item.node.title}\n \
User: ${participant.name} (${participant.id})\n \
Workflow: ${model.title}\n \
-------------------------------------------------------------------------------------\n\n

message=Content: ${host.prefix}${payload.path.open}\n

footer=\n \
-------------------------------------------------------------------------------------\n \
View the overview in your ${host.prefix}/aem/inbox\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Anpassen von E-Mail-Vorlagen für die Workflow-Benachrichtigung {#customizing-email-templates-for-workflow-notification}

Die englische E-Mail-Vorlage für die Benachrichtigung über ein Workflow-Ereignis können Sie wie folgt anpassen:

1. Öffnen Sie in CRXDE die Datei:

   `/libs/settings/workflow/notification/email/default/en.txt`

1. Ändern Sie die Datei nach Bedarf.
1. Speichern Sie die Änderungen.

Die Vorlage muss das folgende Format aufweisen:

```
subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

>[!NOTE]
>
>Dabei kann `<text_x>` ein Mix von statischem Text und dynamischen Zeichenfolgenvariablen sein. Jede Zeile eines `<text_x>`-Elements muss mit einem umgekehrten Schrägstrich (`\`) enden, außer der letzten Instanz, wo das Fehlen des umgekehrten Schrägstrichs das Ende der `<text_x>`-Zeichenfolgenvariable anzeigt.
>
>Weitere Informationen zum Vorlagenformat werden von der Methode [javadocs der Properties.load()](https://docs.oracle.com/javase/8/docs/api/java/util/Properties.html#load-java.io.InputStream-)-Methode bereitgestellt.

Die Methode `${payload.path.open}` legt den Pfad zur Payload des Arbeitselements offen. Bei einer Seite in Sites würde `payload.path.open` dann `/bin/wcmcommand?cmd=open&path=…`ähneln, das den Server-Namen nicht enthält. Aus diesem Grund stellt die Vorlage diesem `${host.prefix}` voran.

Die folgenden Variablen können innerhalb der E-Mail-Vorlage verwendet werden:

* `${event.EventType}`, Ereignistyp
* `${event.TimeStamp}`, Datum und Uhrzeit des Ereignisses
* `${event.User}`, der Benutzer, der das Ereignis ausgelöst hat
* `${initiator.home}`, der Knotenpfad des Initiators

* `${initiator.name}`, der Name des Initiators

* `${initiator.email}`, die E-Mail-Adresse des Initiators
* `${item.id}`, die ID des Arbeitselements
* `${item.node.id}`, die ID des Knotens innerhalb des Workflow-Modells, das mit diesem Arbeitselement verknüpft ist
* `${item.node.title}`, der Titel des Arbeitselements
* `${participant.email}`, die E-Mail-Adresse des Teilnehmers
* `${participant.name}`, der Vorname des Teilnehmers
* `${participant.familyName}`, der Familienname des Teilnehmers
* `${participant.id}`, die ID des Teilnehmers
* `${participant.language}`, die Sprache des Teilnehmers
* `${instance.id}`, die ID des Workflows
* `${instance.state}`, der Status des Workflows
* `${model.title}`, der Titel des Workflow-Modells
* `${model.id}`, die ID des Workflow-Modells

* `${model.version}`, die Version des Workflow-Modells
* `${payload.data}`, die Payload

* `${payload.type}`, der Typ der Payload
* `${payload.path}`, der Pfad der Payload
* `${host.prefix}`, das Host-Präfix, z. B. http://localhost:4502

### Hinzufügen einer E-Mail-Vorlage für eine neue Sprache {#adding-an-email-template-for-a-new-language}

So fügen Sie eine Vorlage für eine neue Sprache hinzu:

1. Fügen Sie in CRXDE eine Datei `<language-code>.txt` hinzu unter:

   * `/libs/settings/notification-templates/com.day.cq.wcm.core.page`: für Seitenbenachrichtigungen
   * `/etc/notification/email/default/com.day.cq.collab.forum`: für Forumsbenachrichtigungen
   * `/libs/settings/workflow/notification/email/default`: für Workflow-Benachrichtigungen

1. Passen Sie die Datei an die Sprache an.
1. Speichern Sie die Änderungen.

>[!NOTE]
>
>Der `<language-code>`, der als Dateiname der E-Mail-Vorlage verwendet wird, muss ein von AEM anerkannter, aus zwei Kleinbuchstaben bestehender Sprach-Code sein. AEM nutzt die Sprach-Codes gemäß ISO-639-1.

## Konfigurieren von AEM Assets-E-Mail-Benachrichtigungen {#assetsconfig}

Wenn Sammlungen in AEM Assets freigegeben oder nicht freigegeben sind, können Benutzer E-Mail-Benachrichtigungen von AEM erhalten. Gehen Sie wie folgt vor, um E-Mail-Benachrichtigungen zu konfigurieren.

1. Konfigurieren Sie den E-Mail-Dienst, wie oben unter [Konfigurieren des Mail-Dienstes](/help/sites-administering/notification.md#configuring-the-mail-service).
1. Melden Sie sich in AEM als Admin an. Klicken Sie auf **Tools** > **Vorgänge** > **Web-Konsole**, um die Konfiguration der Web-Konsole zu öffnen.
1. Bearbeiten Sie das **Day CQ DAM-Ressourcensammlungs-Servlet**. Auswählen **Versand-E-Mail**. Klicken Sie auf **Speichern**.
