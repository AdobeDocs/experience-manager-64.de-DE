---
title: Aktivität Stream Essentials
seo-title: Aktivität Stream Essentials
description: Liste der zuletzt durchgeführten Aktivitäten eines Mitglieds oder einer Liste der letzten Aktivitäten in einem einzigen Inhaltsthread
seo-description: Liste der zuletzt durchgeführten Aktivitäten eines Mitglieds oder einer Liste der letzten Aktivitäten in einem einzigen Inhaltsthread
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 2%

---


# Aktivität Stream Essentials {#activity-stream-essentials}

Die Aktivitäten eines in einem Community-Mitglied unterschriebenen Mitglieds, wie z.B. das Posten in einem Forum oder Blog, werden in einem Stream gesammelt, der durch die Konfiguration der Aktivität Streams-Komponente gefiltert und auf verschiedene Weise angezeigt werden kann.

Die Möglichkeit zu folgen, fügt weitere Aktivitäten hinzu, wenn Community-Mitglieder Beiträge von Interesse oder andere Community-Mitglieder folgen.

Alle [Community-Sites](overview.md#communitiessites) enthalten eine Benutzerseite für das Profil des angemeldeten Mitglieds, auf der die Mitgliederangaben auf dieselbe Weise angezeigt werden.

## Konzepte {#concepts}

Ein *Aktivitäten-Stream* ist die Liste der letzten Aktivitäten, die von einem Mitglied oder einer Liste der letzten Aktivitäten an einem einzigen Inhaltsthread, wie z. B. einem Forenthema oder einem Blog, durchgeführt wurden.

Ein Mitglied kann einem Aktivitäten-Stream folgen, indem es entweder einer anderen Einzelperson oder einem anderen Inhalt folgt.

Ein *News-Feed* ist eine Zusammenführung der Aktivität-Streams, die von einem Mitglied in einem Stream verfolgt werden.

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
   <td>Siehe <a href="activities.md">Aktivität Streams-Funktion</a></td> 
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Aktivität Streams API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [Aktivität Streams Listener API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Serverseitige Anpassungen](server-customize.md)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Eine Community-Site-Struktur, die die [Aktivität Stream-Funktion](functions.md#activity-stream-function)enthält, enthält eine konfigurierte `activity streams` Komponente.
