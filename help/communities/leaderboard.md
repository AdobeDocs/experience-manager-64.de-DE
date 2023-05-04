---
title: Leaderboard-Grundlagen
seo-title: Leaderboard Essentials
description: Übersicht über Leaderboard-Funktionen
seo-description: Leaderboard feature overview
uuid: 815a6928-b147-496d-9751-13159ad1304d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7449f99e-77d7-4c0f-96d5-b67d5e1f124a
exl-id: 20c16e96-2ba8-4f2d-8cfa-8cd804e3441f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 10%

---

# Leaderboard-Grundlagen {#leaderboard-essentials}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Diese Seite enthält die wichtigsten Informationen für die Arbeit mit der Leaderboard-Funktion.

Bevor Sie die Leaderboard-Komponente auf einer Seite einfügen, müssen Sie [Communities-Scoring und -Abzeichen](implementing-scoring.md). Siehe auch [Grundlagen zu Scoring und Abzeichen](configure-scoring.md).

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/gamification/components/hbs/leaderboard</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.gamification.hbs.leaderboard</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/leaderboard.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/clientlibs/leaderboard.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Siehe <a href="enabling-leaderboard.md">Leaderboard-Funktion</a></td> 
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

### Dateibibliotheksfunktion {#file-library-function}

Eine Community-Site-Struktur mit [Leaderboard-Funktion](functions.md#leaderboard-function)enthält eine konfigurierte `leaderboard` -Komponente.
