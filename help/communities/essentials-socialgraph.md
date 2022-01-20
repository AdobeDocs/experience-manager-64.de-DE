---
title: Grundlagen zum Social-Diagramm
seo-title: Social Graph Essentials
description: Folgt der Komponente und der folgenden Komponentenübersicht
seo-description: follow component and following component overview
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
exl-id: 55aa015e-e0e4-411e-8e28-75006ae3090b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 12%

---

# Grundlagen zum Social-Diagramm {#social-graph-essentials}

Die Fähigkeit eines Mitglieds der Gemeinschaft, [activities](essentials-activities.md) und werden durch zwei Komponenten festgelegt:

Die `follow`-Komponente muss mit einer anderen Ressource verknüpft sein. Diese Zuordnung ist bereits für bestehende Community-Mitglieder und -Funktionen in einer [Community-Site](overview.md#communitiessites).

Die `following`-Komponente listet die Mitglieder auf, die dem aktuellen Mitglied folgen oder dem aktuellen Mitglied folgen. Dieses Sozialdiagramm der Mitgliederbeziehungen untereinander ist Teil des Benutzerprofils, das für eine Community-Site bereitgestellt wird.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

### Folgende {#following}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/socialgraph/components/hbs/relations</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.socialgraph</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Siehe <a href="socialgraph.md">Social-Diagramm verwenden</a></td> 
  </tr>
  <tr>
   <td><strong> optional<br /> property</strong></td> 
   <td>
    <ul> 
     <li>Name: <strong><code>outgoing</code></strong></li> 
     <li>Typ: Boolean</li> 
     <li>Wert:<br /> 
      <ul> 
       <li><i>true </i>- die <code>following</code> -Komponente listet die Mitglieder auf, die das derzeit angemeldete Mitglied sind <code>follows</code></li> 
       <li><i>false </i>- die <code>following</code> -Komponente listet die Mitglieder auf, die <code>follow </code>das derzeit angemeldete Mitglied</li> 
      </ul> </li> 
    </ul> <p>Standardwert ist <i>true</i> wenn die -Eigenschaft fehlt. Derzeit ist es nicht möglich, diese Eigenschaft im Bearbeitungsdialogfeld im Autorenmodus festzulegen. Die Eigenschaft muss einer Instanz der <code>following </code>Knoten verwenden <a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>.</p> </td> 
  </tr>
 </tbody>
</table>

### Folgen {#follow}

| **resourceType** | social/socialgraph/components/hbs/following |
|---|---|
| [**einschließen**](scf.md#add-or-include-a-communities-component) | Nein |
| **templates** | /libs/social/socialgraph/components/hbs/following/following.hbs |
| **css** | /libs/social/socialgraph/components/hbs/following/clientlibs/following.css |

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Social Graph-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Social Graph-Endpunkte](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Serverseitige Anpassungen](server-customize.md)
