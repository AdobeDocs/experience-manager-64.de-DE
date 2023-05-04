---
title: Ideengrundlagen
seo-title: Ideation Essentials
description: Übersicht über die Ideen-Funktion
seo-description: Ideation feature overview
uuid: abaf03ee-8bf4-4241-96c3-474c95a30a88
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a9e4f2f0-d1ff-40c0-abcf-645e40586a84
exl-id: 7fb68293-c6e3-4793-b433-205bcfc23e20
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 9%

---

# Ideengrundlagen {#ideation-essentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Auf dieser Seite finden Sie die wichtigsten Informationen für die Arbeit mit der Ideenfunktion, die einem Forum ähnlich ist, jedoch mit der Möglichkeit, als Entwurf zu speichern und ein kollaboratives Gefühl zu entwickeln.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/ideation/components/hbs/ideation</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.stimating<br /> cq.social.hbs.liking<br /> cq.social.hbs.ideation</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/ideation.hbs<br /> /libs/social/ideation/components/hbs/ideation/ideationlists.hbs<br /> /libs/social/ideation/components/hbs/ideation/composer.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/clientlibs/ideation.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Siehe <a href="ideation-feature.md">Ideen-Funktion</a></td> 
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

### Ideen-Funktion {#ideation-function}

Eine Community-Site-Struktur mit [Ideenfunktion](functions.md#ideation-function)enthält eine konfigurierte `ideation` -Komponente.
