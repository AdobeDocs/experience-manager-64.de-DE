---
title: OSGi-Ereignisse für Communities-Komponenten
seo-title: OSGi Events for Communities Components
description: OSGi-Ereignisse werden gesendet, die asynchrone Listener als Trigger verwenden können
seo-description: OSGi events are sent that can trigger asynchronous listeners
uuid: 317e2add-689d-4c99-ae38-0703b6649cb7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 25b7ac08-6cdc-4dd5-a756-d6169b86f9ab
exl-id: 3f7d1b95-729a-4c55-af96-efdb9617d333
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 6%

---

# OSGi-Ereignisse für Communities-Komponenten {#osgi-events-for-communities-components}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Wenn Mitglieder mit Communities-Funktionen interagieren, werden OSGi-Ereignisse gesendet, die asynchrone Listener wie Benachrichtigungen oder Gamification (Scoring und Badging) in Trigger setzen können.

Die [SocialEvent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) -Instanz zeichnet die Ereignisse als `actions`die für `topic`. Das SocialEvent enthält eine Methode zum Zurückgeben einer `verb`mit der Aktion verknüpft ist. Es gibt eine *n-1* Beziehung `actions`und `verbs`.

Die folgenden Tabellen beschreiben für die in der Version bereitgestellten Communities-Komponenten die `verbs`für jeden `topic`verfügbar.

## Themen und Verben {#topics-and-verbs}

[Kalenderkomponente](calendar-basics-for-developers.md)
SocialEvent `topic`= com/adobe/cq/social/calendar

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt ein Kalenderereignis |
| HINZUFÜGEN | Mitgliederkommentare für ein Kalenderereignis |
| AKTUALISIEREN | Kalenderereignis oder -kommentar eines Mitglieds wird bearbeitet |
| LÖSCHEN | Kalenderereignis oder -kommentar eines Mitglieds wird gelöscht |

[Kommentarkomponente](essentials-comments.md)
SocialEvent `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Kommentar |
| HINZUFÜGEN | Mitglied antwortet auf Kommentar |
| AKTUALISIEREN | Der Kommentar des Mitglieds wird bearbeitet |
| LÖSCHEN | Kommentar des Mitglieds wird gelöscht |

[Dateibibliothekskomponente](essentials-file-library.md)
SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Ordner |
| ANHÄNGEN | Mitglied lädt eine Datei hoch |
| AKTUALISIEREN | Mitglied aktualisiert Ordner oder Dateien |
| LÖSCHEN | Mitglied löscht Ordner oder Dateien |

[Forumkomponente](essentials-forum.md)
SocialEvent `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Forumthema |
| HINZUFÜGEN | Mitgliederantworten zum Forumthema |
| AKTUALISIEREN | Forenthema oder Antwort des Mitglieds wird bearbeitet |
| LÖSCHEN | Forenthema oder Antwort des Mitglieds wurde gelöscht |

[Journalkomponente](blog-developer-basics.md)
SocialEvent `topic`= com/adobe/cq/social/journal

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Blogartikel |
| HINZUFÜGEN | Kommentare zu Mitgliedern in einem Blogartikel |
| AKTUALISIEREN | Blogartikel oder Kommentar eines Mitglieds wird bearbeitet |
| LÖSCHEN | Blogartikel oder Kommentar eines Mitglieds wird gelöscht |

[QnA-Komponente](qna-essentials.md)
SocialEvent `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt eine Frage zur Frage der Fragen |
| HINZUFÜGEN | Mitglied erstellt eine Antwort auf Fragen und Antworten |
| AKTUALISIEREN | Frage oder Antwort des Mitglieds wird bearbeitet |
| SELECT | Antwort des Mitglieds ist ausgewählt |
| UNSELECT | Die Antwort des Mitglieds ist deaktiviert. |
| LÖSCHEN | Frage oder Antwort des Mitglieds wird gelöscht |

[Überprüfungskomponente](reviews-basics.md)
SocialEvent `topic`= com/adobe/cq/social/review

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Überprüfung |
| AKTUALISIEREN | Die Überprüfung des Mitglieds wird bearbeitet |
| LÖSCHEN | Überprüfung durch das Mitglied wird gestrichen |

[Bewertungskomponente](rating-basics.md)
SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschreibung** |
|---|---|
| RATE HINZUFÜGEN | Der Inhalt des Mitglieds wurde bewertet. |
| RATE ENTFERNEN | der Inhalt des Mitglieds wurde heruntergestuft |

[Abstimmungskomponente](essentials-voting.md)
SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschreibung** |
|---|---|
| ABSTIMMUNG HINZUFÜGEN | Der Inhalt des Mitglieds wurde abgestimmt |
| ABSTIMMUNG ENTFERNEN | Der Inhalt des Mitglieds wurde abgelehnt |

**Moderationsfähige Komponenten**
SocialEvent `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschreibung** |
|---|---|
| ABLEHNEN | Inhalt des Mitglieds wird verweigert |
| FLAG-AS-INAPPROPRIATE | Inhalt des Mitglieds wird gekennzeichnet |
| UNFLAG-AS-INAPPROPRIATE | Inhalt des Mitglieds ist unmarkiert |
| AKZEPT | Der Inhalt des Mitglieds wird vom Moderator genehmigt |
| SCHLIESSEN | Mitglied schließt Kommentar zu Bearbeitungen und Antworten |
| ÖFFNEN | Mitglied öffnet Kommentar erneut |

## Ereignisse für benutzerdefinierte Komponenten {#events-for-custom-components}

Bei einer benutzerdefinierten Komponente muss die [Abstrakte SocialEvent-Klasse](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) muss erweitert werden, um die Ereignisse der Komponente als `actions`die für `topic`.

Das benutzerspezifische Ereignis überschreibt die -Methode `getVerb()` , damit `verb`wird für jeden `action`. Die `verb` für eine Aktion zurückgegeben wird, kann eine häufig verwendete Aktion sein (z. B. `POST`) oder einer für die Komponente spezialisierten Komponente (z. B. `ADD RATING`). Es gibt eine *n-1* Beziehung `actions`und `verbs`.

>[!NOTE]
>
>Stellen Sie sicher, dass eine benutzerdefinierte Erweiterung mit einem niedrigeren Rang registriert ist als jede vorhandene Implementierung im Produkt.

### Pseudo-Code für benutzerspezifisches Komponentenereignis {#pseudo-code-for-custom-component-event}

[org.osgi.service.event.Event](https://osgi.org/javadoc/r4v41/org/osgi/service/event/Event.html);\
[com.adobe.cq.social.scf.core.SocialEvent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html);\
[com.adobe.granite.activitystreams.ObjectTypes](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ObjectTypes.html);\
[com.adobe.granite.activitystreams.verbs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/Verbs.html);

```java
package com.mycompany.recipe;

import org.osgi.service.event.Event;
import com.adobe.cq.social.scf.core.SocialEvent;
import com.adobe.granite.activitystreams.ObjectTypes;
import com.adobe.granite.activitystreams.Verbs;

/* 
 * The Recipe type, passed to RecipeEvent(), would be a custom Recipe class 
 * that extends either 
 * com.adobe.cq.social.scf.SocialComponent 
 * or
 * com.adobe.cq.social.scf.SocialCollectionComponent
 * See https://docs.adobe.com/docs/en/aem/6-2/develop/communities/scf/server-customize.html
 */

/**
 * Defines events that are triggered on a custom component, "Recipe".
 */
public class RecipeEvent extends SocialEvent<RecipeEvent.RecipeActions> {

    private static final long serialVersionUID = 1L;
    protected static final String PARENT_PATH = "PARENT_PATH";

    /**
     * The event topic suffix for Recipe events
     */
    public static final String RECIPE_TOPIC = "recipe";

    /**
     * @param recipe - the recipe resource on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final Recipe recipe, final String userId, final RecipeEvent.RecipeActions action) {
        String recipePath = recipe.getResource().getPath();
        String parentPath = (recipe.getParentComponent() != null) ? 
                             recipe.getParentComponent().getResource().getPath() : 
                             recipe.getSourceComponentId();
        this(recipePath, userId, parentPath, action);
    }

    /**
     * @param recipePath - the path to the recipe resource (jcr node) on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param parentPath - the path to the parent node of the recipe resource
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final String recipePath, final String userId, final String parentPath) {
        super(RECIPE_TOPIC, recipePath, userId, action, 
              new BaseEventObject(recipePath, ObjectTypes.ARTICLE), 
              new BaseEventObject(parentPath, ObjectTypes.COLLECTION),
              new HashMap<String, Object>(1) {
            private static final long serialVersionUID = 1L;
            {
                if (parentPath != null) {
                    this.put(PARENT_PATH, parentPath);
                }

            }
        });
    }

    private RecipeEvent (final Event event) {
      super(event);
    }

    /**
     * List of available recipe actions that can trigger a recipe event.
     */
    public static enum RecipeActions implements SocialEvent.SocialActions {
        RecipeAdded, 
        RecipeModified, 
        RecipeDeleted;

        @Override
        public String getVerb() {
            switch (this) {
                case RecipeAdded:
                    return Verbs.POST;
                case RecipeModified:
                    return Verbs.UPDATE;
                case RecipeDeleted:
                    return Verbs.DELETE;
                default:
                    throw new IllegalArgumentException("Unsupported action");
            }
        }
    }

}
```

## Beispiel für EventListener zum Filtern von Aktivitäts-Stream-Daten {#sample-eventlistener-to-filter-activity-stream-data}

Es ist möglich, Ereignisse zu überwachen, um zu ändern, was im Aktivitäts-Stream angezeigt wird.

Im folgenden Pseudo-Codebeispiel werden DELETE-Ereignisse für Kommentar-Komponenten aus dem Aktivitäts-Stream entfernt.

### Pseudocode für EventListener {#pseudo-code-for-eventlistener}

Erfordert [neueste Feature Pack](deploy-communities.md#latestfeaturepack).

```java
package my.company.comments;

import java.util.Collections;
import java.util.Map;

import org.apache.commons.lang.StringUtils;
import org.apache.felix.scr.annotations.Activate;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Modified;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.commons.osgi.PropertiesUtil;
import org.osgi.service.component.ComponentContext;

import com.adobe.cq.social.activitystreams.listener.api.ActivityStreamProviderExtension;
import com.adobe.cq.social.commons.events.CommentEvent.CommentActions;
import com.adobe.cq.social.scf.core.SocialEvent;

@Service
@Component(metatype = true, label = "My Comment Delete Event Filter",
        description = "Prevents comment DELETE events from showing up in activity streams")
public class CommentDeleteEventActivityFilter implements ActivityStreamProviderExtension {

    @Property(name = "ranking", intValue = 10)
    protected int ranking;

    @Activate
    public void activate(final ComponentContext ctx) {
        ranking = PropertiesUtil.toInteger(ctx.getProperties().get("ranking"), 10);
    }

    @Modified
    public void update(final Map<String, Object> props) {
        ranking = PropertiesUtil.toInteger(props.get("ranking"), 10);
    }

    @Override
    public boolean evaluate(final SocialEvent<?> evt, final Resource resource) {
        if (evt.getAction() != null && evt.getAction() instanceof SocialEvent.SocialActions) {
            final SocialEvent.SocialActions action = evt.getAction();
            if (StringUtils.equals(action.getVerb(), CommentActions.DELETED.getVerb())) {
                return false;
            }
        }
        return true;
    }

    @Override
    public Map<String, ? extends Object> getActivityProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public Map<String, ? extends Object> getActorProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String getName() {
        return "My Comment Delete Event Filter";
    }

    @Override
    public Map<String, ? extends Object> getObjectProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    /* Ensure a custom extension is registered with a ranking lower than any existing implementation in the product. */
    @Override
    public int getRanking() {
        return this.ranking;
    }

    @Override
    public Map<String, ? extends Object> getTargetProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String[] getStreamProviderPid() {
        return new String[]{"*"};
    }

}
```
