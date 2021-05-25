---
title: Blog-Grundlagen
seo-title: Blog-Grundlagen
description: Blog-Übersicht
seo-description: Blog-Übersicht
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
exl-id: 8cff0b7b-c120-462f-8fce-13822073eabb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 4%

---

# Blog-Grundlagen {#blog-essentials}

Ab AEM 6.1 Communities ist ein Blog eine Community-Aktivität. Blogartikel werden jetzt aus der Veröffentlichungsumgebung gepostet, wo zuvor Blogartikel nur in der Autorenumgebung erstellt und veröffentlicht werden konnten.

Blog-Artikel können jetzt von jedem Community-Mitglied erstellt werden, es sei denn, sie sind auf privilegierte Mitglieder beschränkt.

Diese Seite enthält die wesentlichen Informationen für die Arbeit mit der Blog-Funktion.

>[!NOTE]
>
>Die zugrunde liegende Infrastruktur der Blog-Funktion ist die Journalfunktion.

## Grundlagen für Client-seitige {#essentials-for-client-side}

Die Blog-Funktion besteht aus zwei Hauptkomponenten, die verfügbar sind, indem die [Blog-Funktion](functions.md#blog-function) hinzugefügt oder die Komponenten einer Seite im Bearbeitungsmodus für Autoren hinzugefügt werden.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.stimating<br /> cq.social.hbs.journal</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Siehe <a href="blog-feature.md">Blog-Funktion</a></td> 
  </tr>
 </tbody>
</table>

### Blog-Seitenleiste {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**einschließen**](scf.md#add-or-include-a-communities-component) | Nein |
| [**clientllibs**](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **Eigenschaften** | Siehe [Blog-Funktion](blog-feature.md) |

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Blog-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Blog-Endpunkte](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Blogfunktion {#blog-function}

Eine Community-Site-Struktur, die die [Bog-Funktion](functions.md#blog-function) enthält, hat die Komponenten `Blog` und `Blog Sidebar` konfiguriert. Die Blog-Funktion unterstützt die Identifizierung einer [berechtigten Mitgliederbenutzergruppe](users.md#privileged-members-group).

### Zugreifen auf Blogeinträge (UGC) {#accessing-blog-entries-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.\
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für UGC den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können sich ohne Warnung** ändern.

Siehe:

* [Übersicht über den Speicher Resource Provider](srp.md)  - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](srp-and-ugc.md)  - SRP-Dienstprogrammmethoden und Beispiele
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md)  - Codierungsrichtlinien
* [SocialUtils-Refaktorierung](socialutils.md)  - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden

## Primärer Herausgeber {#primary-publisher}

Wenn es sich bei der Bereitstellung um eine Veröffentlichungsfarm handelt, müssen Sie einen primären Herausgeber identifizieren, der nach Artikeln fragt, deren Veröffentlichung geplant ist.

Weitere Informationen finden Sie unter [Primär Publisher](deploy-communities.md#primary-publisher) .

## Zulassen von Rich Media {#allowing-rich-media}

Die AEM Plattform blockiert Links von anderen Websites, um XSS-Angriffe zu verhindern, wie unter

* [Schutz vor Cross-Site Scripting (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

Ab AEM 6.2 sind die zuvor manuell vorzunehmenden Änderungen in der standardmäßigen AntiSamy-Konfigurationsdatei enthalten.

Rich-Media wird in einen Blog-Artikel eingebettet, indem Sie das Symbol `Embed Media from External Sites` auswählen:  ![chlimage_1-471](assets/chlimage_1-471.png)
