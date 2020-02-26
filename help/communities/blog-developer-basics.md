---
title: Blog Essentials
seo-title: Blog Essentials
description: Blog-Übersicht
seo-description: Blog-Übersicht
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f

---


# Blog Essentials {#blog-essentials}

Ab AEM 6.1 Communities ist ein Blog eine Community-Aktivität. Blog-Artikel werden jetzt in der Veröffentlichungsumgebung veröffentlicht, wo zuvor Blog-Artikel nur in der Autorenumgebung erstellt und veröffentlicht werden konnten.

Blog-Artikel können jetzt von jedem Community-Mitglied erstellt werden, es sei denn, sie sind auf privilegierte Mitglieder beschränkt.

Diese Seite enthält die wesentlichen Informationen für die Arbeit mit der Blog-Funktion.

>[!NOTE]
>
>Die zugrunde liegende Infrastruktur der Blog-Funktion ist die Zeitschriftenfunktion.

## Grundlagen für clientseitige {#essentials-for-client-side}

Die Blog-Funktion besteht aus zwei Hauptkomponenten, die verfügbar sind, indem Sie die [Blog-Funktion](functions.md#blog-function) hinzufügen oder die Komponenten einer Seite im Autorenbearbeitungsmodus hinzufügen.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.stimmst<br /> cq.social.hbs.journal</td> 
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
   <td>siehe <a href="blog-feature.md">Blog-Funktion</a></td> 
  </tr>
 </tbody>
</table>

### Blog-Seitenleiste {#blog-sidebar}

| **resourceType** | social/Journal/components/hbs/sidebar |
|---|---|
| [**einschließbar **](scf.md#add-or-include-a-communities-component) | Nein |
| [**clientllibs **](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **properties** | siehe [Blog-Funktion](blog-feature.md) |

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Blog-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Blog-Endpunkte](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Blogfunktion {#blog-function}

Eine Community-Site-Struktur, die die [Bog-Funktion](functions.md#blog-function) enthält, verfügt über konfigurierte `Blog` und `Blog Sidebar` Komponenten. Die Blog-Funktion unterstützt die Identifizierung einer [privilegierten Benutzergruppe](users.md#privileged-members-group).

### Zugriff auf Blog-Einträge (UGC) {#accessing-blog-entries-ugc}

UGC sollte mit einer der Standardmethoden für Moderation moderiert werden.\
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Speichers](working-with-srp.md) für UGC Programmierungszugriff auf UGC, unabhängig von der gewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können ohne Warnung** geändert werden.

Siehe:

* [Übersicht über](srp.md) den Speicherressourcen-Provider - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Richtlinien zum Kodieren
* [SocialUtils Refactoring](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden

## Herausgeber {#primary-publisher}

Wenn es sich bei der Bereitstellung um eine Veröffentlichungsfarm handelt, müssen Sie einen primären Herausgeber identifizieren, der nach Artikeln sucht, deren Veröffentlichung geplant ist.

Weitere Informationen finden Sie unter [Primärherausgeber](deploy-communities.md#primary-publisher) .

## Rich Media zulassen {#allowing-rich-media}

Die AEM-Plattform blockiert Links von anderen Websites, um XSS-Angriffe zu verhindern, wie in

* [Schutz vor Cross-Site Scripting (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

Ab AEM 6.2 sind die zuvor manuell vorzunehmenden Änderungen in der standardmäßigen AntiSamy-Konfigurationsdatei enthalten.

Rich-Media-Daten werden durch Auswahl des `Embed Media from External Sites` Symbols in einen Blog-Artikel eingebettet:  ![chlimage_1-471](assets/chlimage_1-471.png)

