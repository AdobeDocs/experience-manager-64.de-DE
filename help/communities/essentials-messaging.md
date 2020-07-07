---
title: Messaging Essentials
seo-title: Messaging Essentials
description: Übersicht über die Messaging-Komponente
seo-description: Übersicht über die Messaging-Komponente
uuid: 53711f4d-6bbc-4be9-aefe-4e75a81cd67f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eb8fd2b3-0a31-425e-b0f1-38f09e1106df
translation-type: tm+mt
source-git-commit: 98fae2d51d73bda946f3c398e9276fe4d5a8a0fe
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 5%

---


# Messaging Essentials {#messaging-essentials}

Auf dieser Seite werden die Details zum Arbeiten mit der Messaging-Komponente Dokumente, um eine Messaging-Funktion auf einer Website einzuschließen.

## Grundlagen für clientseitige {#essentials-for-client-side}

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
   <td>siehe <a href="configure-messaging.md">Konfigurieren von Messaging</a></td> 
  </tr> 
  <tr> 
   <td><strong>Admin-Konfiguration</strong></td> 
   <td><a href="messaging.md">Messaging konfigurieren</a></td> 
  </tr> 
 </tbody> 
</table>

**Liste** der Nachricht (für &quot;Posteingang&quot;, &quot;Gesendet&quot;und &quot;Papierkorb&quot;)

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

Siehe auch [clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Messaging konfigurieren](configure-messaging.md)

* [Messaging-Client-APIs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) für SCF-Komponenten

* [Messaging-APIs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) für den Dienst

* [Messaging-Endpunkte](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

>[!CAUTION]
>
>Der String-Parameter darf für die folgenden MessageBuilder-Methoden *keinen *folgenden Schrägstrich (/) enthalten:
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

Eine Community-Site-Struktur, die mithilfe des Assistenten erstellt wurde, enthält bei Auswahl die Messaging-Funktion. Siehe `User Management` Einstellungen der [Community-Sites-Konsole](sites-console.md#user-management).

### Beispielcode: Benachrichtigung erhalten {#sample-code-message-received-notification}

Die Social Messaging-Funktion gibt Ereignis für Vorgänge aus, z. B. `send``marking read`, `marking delete`. Diese Ereignis können abgefangen und anhand der im Ereignis enthaltenen Daten ausgeführt werden.

Das folgende Beispiel zeigt einen Ereignis-Handler, der auf das `message sent` Ereignis überwacht und eine E-Mail an alle Empfänger mit der `Day CQ Mail Service`Funktion sendet.

Zum Testen des serverseitigen Beispielskripts benötigen Sie eine Entwicklungs-Umgebung und die Möglichkeit, ein OSGi-Bundle zu erstellen.

1. Login as an administrator to ` [CRXDE|Lite](http://localhost:4502/crx/de)`
1. Erstellen Sie ein `bundle node`in `/apps/engage/install` mit beliebigen Namen, z. B.

   * **[!UICONTROL Symbolischer Name]**: com.engagement.media.social.messaging.MessagingNotification
   * **[!UICONTROL Name]**: Erste Schritte - Benachrichtigung über Tutorialmeldungen
   * **[!UICONTROL Beschreibung]**: ein Beispieldienst zum Senden einer E-Mail-Benachrichtigung an Benutzer, die eine Nachricht erhalten
   * **[!UICONTROL Paket]**: `com.engage.media.social.messaging.notification`

1. Navigieren Sie zu `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`

   1. Löschen Sie die automatisch erstellte `Activator.java` Klasse
   1. Create-Klasse `MessageEventHandler.java`
   1. Kopieren/fügen Sie den unten stehenden Code in `MessageEventHandler.java`

1. Klicken Sie auf **[!UICONTROL Alle speichern]**
1. Navigieren Sie zu allen Importanweisungen `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` und fügen Sie sie hinzu, wie im `MessageEventHandler.java` Code geschrieben.
1. Erstellen Sie das Bundle
1. Stellen Sie sicher, dass der `Day CQ Mail Service`OSGi-Dienst konfiguriert ist.
1. Melden Sie sich als ein Demo-Benutzer an und senden Sie eine E-Mail an einen anderen
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

