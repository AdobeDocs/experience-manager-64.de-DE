---
title: Gefällt mir-Grundlagen
seo-title: Liking Essentials
description: Übersicht über Verknüpfungskomponenten
seo-description: Liking component overview
uuid: 89f16859-c901-4090-8e16-363b95c508de
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f176c42b-b16b-42c9-af22-4b6421de5a90
pagetitle: Liking Essentials
exl-id: 509d1fb4-a88d-4438-a618-ba063adb6fb9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 3%

---

# Gefällt mir-Grundlagen {#liking-essentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Komponente &quot;Gefällt mir&quot;, eine [tally](tally.md) subclass ist ein nützliches Tool, mit dem Mitglieder durch die Auswahl des Herzensymbols eine positive Meinung zu einem bestimmten Inhalt äußern können.

Es ist zulässig, mehrere Instanzen einer liken Komponente auf derselben Seite zu platzieren. Jede Instanz muss mit einer eindeutigen `tally name` -Eigenschaft.

Das anonyme Posten eines &quot;Gefällt mir&quot;-Klicks wird nicht unterstützt. Besucher der Site müssen sich registrieren und sich anmelden, um an &quot;Gefällt mir&quot;-Klicks teilnehmen zu können. Der angemeldete Besucher (Mitglied) kann sich jederzeit ein- und ausschalten.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>social/tally/components/hbs/liken</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td> 
   <td>Ja - Eigenschaften können bearbeitet werden in <i>Design </i>mode</td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td> cq.social.hbs.liking</td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td><p> /libs/social/tally/components/hbs/liking/liking.hbs<br /> /libs/social/tally/components/hbs/liking/activity-icon.hbs<br /> /libs/social/tally/components/hbs/liking/activity-title.hbs</p> </td> 
  </tr> 
  <tr> 
   <td><strong>CSS</strong></td> 
   <td> /libs/social/tally/components/hbs/liking/clientlibs/likingcomponent.css</td> 
  </tr> 
  <tr> 
   <td><strong>properties</strong></td> 
   <td><p>Siehe <a href="liking.md">Verwenden von "Gefällt mir"</a></p> </td> 
  </tr> 
 </tbody> 
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Tally-APIs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tally Endpoints](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Abstimmung (UGC) {#accessing-posted-voting-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.\
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities: Verwendung einer [gemeinsamer Speicher](working-with-srp.md) für UGC umfasst den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können ohne Warnung geändert werden**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung
* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - SRP-Anwendungsmethoden und -Beispiele
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Methoden von Dienstprogrammen zu aktuellen Methoden des SRP-Dienstprogramms
