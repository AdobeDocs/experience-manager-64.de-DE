---
title: Grundlagen der quantitativen Lockerung
seo-title: QnA Essentials
description: Forumsfunktion für Fragen und Antworten
seo-description: Questions and answers forum feature
uuid: c718a8e3-b3bd-4db9-8c0f-6dd973d40583
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ceace3aa-78a5-485e-b519-630479e087d8
exl-id: 99f8afda-1771-471b-bd0c-99960a453bc9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 4%

---

# Grundlagen der quantitativen Lockerung {#qna-essentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Diese Seite enthält die wichtigsten Informationen für die Arbeit mit der Forumsfunktion Fragen und Antworten (QnA).

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> resourceType</td> 
   <td>social/qna/components/hbs/qnaforum</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">einschließen</a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md">clientllibs</a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.stimating<br /> cq.social.hbs.qna</td> 
  </tr>
  <tr>
   <td> templates</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td> 
  </tr>
  <tr>
   <td> css</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td> 
  </tr>
  <tr>
   <td> properties</td> 
   <td>Siehe <a href="working-with-qna.md">Funktion "Fragen und Antworten"</a></td> 
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [QnA-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [QnA-Endpunkte](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Fragen/Antworten-Funktion {#qna-function}

Eine Community-Site-Struktur mit [QnA-Funktion](functions.md#qna-function) verfügt über eine konfigurierte `QnA` sowie Einstellungen, die sich auf die Moderation und das Tagging auswirken. Die Funktion &quot;Fragen und Antworten&quot;unterstützt die Identifizierung einer [Berechtigte Mitgliederbenutzergruppe](users.md#privileged-members-group).

### Zugreifen auf QnA-Forumbeiträge (UGC) {#accessing-qna-forum-posts-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.\
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities: Verwendung einer [gemeinsamer Speicher](working-with-srp.md) für UGC umfasst den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können ohne Warnung geändert werden**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung
* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - SRP-Anwendungsmethoden und -Beispiele
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Methoden von Dienstprogrammen zu aktuellen Methoden des SRP-Dienstprogramms
