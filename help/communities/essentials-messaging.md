---
title: Grundlagen zu Messaging
seo-title: Grundlagen zu Messaging
description: Übersicht über Messaging-Komponenten
seo-description: Übersicht über Messaging-Komponenten
uuid: 53711f4d-6bbc-4be9-aefe-4e75a81cd67f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eb8fd2b3-0a31-425e-b0f1-38f09e1106df
exl-id: c6ad3c2b-8776-4ec4-99da-ab73ecc61153
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 5%

---

# Messaging Essentials {#messaging-essentials}

Auf dieser Seite werden die Details zum Arbeiten mit der Messaging-Komponente beschrieben, um eine Messaging-Funktion auf einer Website einzubinden.

## Grundlagen für Client-seitige {#essentials-for-client-side}

**Nachricht erstellen**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/composemessage</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td> 
  </tr> 
  <tr> 
   <td><strong>properties</strong></td> 
   <td>Siehe <a href="configure-messaging.md">Konfigurieren von Messaging</a></td> 
  </tr> 
  <tr> 
   <td><strong>Admin-Konfiguration</strong></td> 
   <td><a href="messaging.md">Messaging konfigurieren</a></td> 
  </tr> 
 </tbody> 
</table>

**Nachrichtenliste**  (für Posteingang, Gesendet und Papierkorb)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/messagebox</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td> 
  </tr> 
  <tr> 
   <td><strong>properties</strong></td> 
   <td>Siehe <a href="configure-messaging.md">Konfigurieren von Messaging</a></td> 
  </tr> 
  <tr> 
   <td><strong>Admin-Konfiguration</strong></td> 
   <td><a href="messaging.md">Messaging konfigurieren</a></td> 
  </tr> 
 </tbody> 
</table>

Siehe auch [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Messaging konfigurieren](configure-messaging.md)

* [Messaging-Client-](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) APIs für SCF-Komponenten

* [Messaging-](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) APIs für den Dienst

* [Messaging-Endpunkte](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

>[!CAUTION]
>
>Der String-Parameter darf für die folgenden MessageBuilder-Methoden *keinen Schrägstrich &quot;/&quot;enthalten:
>
>* `setInboxPath`()
>* `setSentItemsPath`()

>
>
Beispiel:
>
>
```
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```

### Community-Site {#community-site}

Eine Community-Site-Struktur, die mithilfe des Assistenten erstellt wird, enthält die Messaging-Funktion, falls ausgewählt. Siehe `User Management` Einstellungen von [Community-Sites-Konsole](sites-console.md#user-management).

### Beispielcode: Nachricht erhalten Benachrichtigung {#sample-code-message-received-notification}

Die Funktion Social Messaging löst Ereignisse für Vorgänge aus, z. B. `send`, `marking read`, `marking delete`. Diese Ereignisse können erfasst und Aktionen für die im Ereignis enthaltenen Daten durchgeführt werden.

Das folgende Beispiel zeigt einen Ereignis-Handler, der auf das `message sent`-Ereignis wartet und mit `Day CQ Mail Service` eine E-Mail an alle Nachrichtenempfänger sendet.

Zum Testen des serverseitigen Beispielskripts benötigen Sie eine Entwicklungsumgebung und die Möglichkeit, ein OSGi-Bundle zu erstellen.

1. Melden Sie sich als Administrator bei ` [CRXDE|Lite](http://localhost:4502/crx/de)` an.
1. Erstellen Sie eine `bundle node`in `/apps/engage/install` mit beliebigen Namen, z. B.

   * **[!UICONTROL Symbolischer Name]**: com.engage.media.social.messaging.MessagingNotification
   * **[!UICONTROL Name]**: Erste Schritte - Tutorial-Nachrichten-Benachrichtigung
   * **[!UICONTROL Beschreibung]**: einen Beispieldienst zum Senden einer E-Mail-Benachrichtigung an Benutzer beim Empfang einer Nachricht
   * **[!UICONTROL Paket]**: `com.engage.media.social.messaging.notification`

1. Navigieren Sie zu `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`

   1. Löschen Sie die automatisch erstellte Klasse `Activator.java` .
   1. Klasse erstellen `MessageEventHandler.java`
   1. Kopieren/fügen Sie den unten stehenden Code in `MessageEventHandler.java` ein.

1. Klicken Sie auf **[!UICONTROL Alle speichern]**
1. Navigieren Sie zu `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` und fügen Sie alle Importanweisungen hinzu, wie im Code `MessageEventHandler.java` geschrieben.
1. Erstellen Sie das Bundle
1. Stellen Sie sicher, dass der OSGi-Dienst `Day CQ Mail Service`konfiguriert ist.
1. Melden Sie sich als ein Demobenutzer an und senden Sie eine E-Mail an einen anderen
1. Der Empfänger sollte eine E-Mail bezüglich einer neuen Nachricht erhalten

#### MessageEventHandler.java {#messageeventhandler-java}

```java
package com.engage.media.social.messaging.notification;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.Resource;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.apache.commons.mail.HtmlEmail;
import java.util.List;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import com.adobe.cq.social.messaging.api.Message;
import com.adobe.cq.social.messaging.api.MessagingEvent;
import com.day.cq.mailer.MessageGatewayService;
import com.day.cq.mailer.MessageGateway;

@Component(immediate=true)
@Service(EventHandler.class)
@Properties({
        @Property(name = "event.topics", value = "com/adobe/cq/social/message")
})
public class MessagingEventHandler implements EventHandler {
    private Logger logger = LoggerFactory.getLogger(MessagingEventHandler.class);

    @Reference
    ResourceResolverFactory resourceResolverFactory;

    @Reference
    private MessageGatewayService messageGatewayService;

    ResourceResolver resourceResolver=null;
    MessageGateway messageGateway=null;

    public void sendMail(String from, String to,String subject, String content){
        Email email = new SimpleEmail();
        messageGateway = messageGatewayService.getGateway(SimpleEmail.class);
        try {
         email.addTo(to);
            email.addReplyTo(from);
            email.setFrom(from);
            email.setMsg(content);
            email.setSubject(subject);
         messageGateway.send(email);
        } catch(EmailException ex) {
            logger.error("MessageNotificaiton : Error sending email : "+ex.getMessage());
        }
        logger.info("**** MessageNotification **** Mail sent to " + to);
    }

    public void handleEvent(Event event) {
        //Get Message Path and originator User's ID from event
        String messagePath = (String) event.getProperty("path");
        String senderId = (String) event.getProperty("userId");
        MessagingEvent.MessagingActions action = (MessagingEvent.MessagingActions) event.getProperty("action");
        try{
            if(MessagingEvent.MessagingActions.MessageSent.equals(action)){
                resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);

                //Read message
                Resource resource = resourceResolver.getResource(messagePath);
                Message msg = resource.adaptTo(Message.class);

                //Get list of recipient Ids from message
                //For Getting Started Tutorial, Id is same as email. If that is not the case in your site, 
                //an additional step is needed to retrieve the email for the Id
                List<String> reclist = msg.getRecipientIdList();
                for(int i=0;i<reclist.size();i++){
                    //Send Email using Mailing Service
                    sendMail("admin@cqadmin.qqq",reclist.get(i),"New message on Getting Started Tutorial", "Hi\nYou have received a new message from  " +  senderId + ". To read it, sign in to Getting Started Tutorial.\n\n-Engage Admin");
                }
            }
        } catch(Exception ex){
            logger.error("Error getting message info : " + ex.getMessage());
        } finally {
            resourceResolver.close();
        }

    }
}
```
