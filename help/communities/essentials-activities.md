---
title: Aktivitäts-Stream-Grundlagen
seo-title: Aktivitäts-Stream-Grundlagen
description: Liste der zuletzt von einem Mitglied durchgeführten Aktivitäten oder einer Liste der zuletzt durchgeführten Aktivitäten in einem einzigen Inhaltsthread
seo-description: Liste der zuletzt von einem Mitglied durchgeführten Aktivitäten oder einer Liste der zuletzt durchgeführten Aktivitäten in einem einzigen Inhaltsthread
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f

---


# Aktivitäts-Stream-Grundlagen {#activity-stream-essentials}

Die Aktivitäten eines in einem Community-Mitglied unterschriebenen Mitglieds, wie das Posten in einem Forum oder Blog, werden in einem Stream gesammelt, der durch die Konfiguration der Aktivitätsstreams-Komponente auf verschiedene Weise gefiltert und angezeigt werden kann.

Die Möglichkeit zu folgen, fügt weitere Aktivitäten hinzu, wenn Community-Mitglieder Beiträge von Interesse oder andere Community-Mitglieder folgen.

Alle [Community-Sites](overview.md#communitiessites) enthalten eine Benutzerprofilseite für das angemeldete Mitglied, auf der die Mitgliederaktivitäten auf dieselbe Weise angezeigt werden.

## Konzepte {#concepts}

Ein *Aktivitätsstream* ist die Liste der kürzlich von einem Mitglied durchgeführten Aktivitäten oder eine Liste der zuletzt durchgeführten Aktivitäten in einem einzigen Inhaltsthread, z. B. einem Forenthema oder einem Blog.

Ein Mitglied kann einem Aktivitätsstream folgen, indem es entweder einer anderen Einzelperson oder einem anderen Inhalt folgt.

Ein *News-Feed* ist eine Zusammenführung der Aktivitätsströme, denen ein Mitglied gefolgt ist, in einem einzigen Stream.

Ein [Social Graph](essentials-socialgraph.md) erfasst die folgenden Beziehungen eines Mitglieds zum anderen.

## Grundlagen für clientseitige {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/activitystreams/components/hbs/activitystreams</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Siehe <a href="activities.md">Activity Streams-Funktion</a></td> 
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Activity Streams-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [Activity Stream-Listener-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Serverseitige Anpassungen](server-customize.md)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Eine Community-Site-Struktur, die die [Activity Stream-Funktion](functions.md#activity-stream-function)enthält, enthält eine konfigurierte `activity streams` Komponente.
