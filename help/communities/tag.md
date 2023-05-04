---
title: Tag-Grundlagen
seo-title: Tag Essentials
description: Tag-Übersicht
seo-description: Tag overview
uuid: a5d52319-f821-4608-b0ab-abc8a1374343
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d355a3ee-c8a8-4a07-8d28-d1a99bda315c
exl-id: 863ee5e3-daa7-4f7d-8897-291d367cf29d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 6%

---

# Tag-Grundlagen {#tag-essentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn AEM Communities-Komponenten mit aktiviertem Tagging konfiguriert sind, können Community-Mitglieder den Inhalt taggen, den sie in der Veröffentlichungsumgebung posten.

Die zugrunde liegende Infrastruktur für Tags, die in der Veröffentlichungsumgebung angewendet werden, entspricht der für Tags, die in der Autorenumgebung auf Inhalte angewendet werden, wie z. B. Seiten und Assets:

* Siehe [Verwalten von Tags](../../help/sites-administering/tags.md) und [Tagging benutzergenerierter Inhalte](tag-ugc.md) (UGC) für Informationen zum Erstellen und Verwalten von Tags.

* Siehe [Tagging für Entwickler](../../help/sites-developing/tags.md) für Informationen über [Tagging-Framework](../../help/sites-developing/framework.md) sowie die Aufnahme und Erweiterung von Tags in [benutzerdefinierte Anwendungen](../../help/sites-developing/building.md).

* Siehe [Verwenden der Social Tag Cloud](tagcloud.md) für Informationen für Autoren zum Hinzufügen einer `social tag cloud` -Komponente auf eine Seite klicken, um die auf UGC angewandten Tags in der Veröffentlichungsumgebung hervorzuheben.

* Siehe [Tagging von Aktivierungsressourcen](tag-resources.md) für Informationen zum Tagging von Ressourcen für Kataloge.

Das Tagging von benutzergenerierten Inhalten kann beim Konfigurieren eines [Community-Site](sites-console.md#tagging) oder einer der folgenden Funktionen:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Dateibibliothek](file-library.md)
* [Forum](forum.md)
* [Fragen und Antworten](working-with-qna.md)

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

### Social Tag-Cloud {#social-tag-cloud}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/commons/components/hbs/tagcloud</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.tagcloud</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/commons/components/hbs/tagcloud/tagcloud.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/commons/components/hbs/tagcloud/clientlibs/tagcloud.css</td> 
  </tr>
  <tr>
   <td><strong>properties</strong></td> 
   <td>Siehe <a href="tagcloud.md">Verwenden der Social Tag Cloud</a></td> 
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Social Tag Cloud-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [Social Tag Manager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

## Tag-Suche {#tag-searching}

Als [Feature Pack 1](deploy-communities.md#latestfeaturepack) (FP1) wird die Tag-Suche mithilfe von [Tag-Titel](../../help/sites-developing/framework.md#tag-characteristics).

Vor FP1 wurde die Suche mithilfe von [Tag-IDs](../../help/sites-developing/framework.md#tagid).
