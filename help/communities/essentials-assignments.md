---
title: Zuweisungsgrundlagen
seo-title: Assignments Essentials
description: Übersicht über Zuweisungsfunktionen für Aktivierungs-Communities
seo-description: Assignments feature overview for enablement communities
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
exl-id: 310d9086-36b6-42ea-835f-c77d75e880cb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 14%

---

# Zuweisungsgrundlagen {#assignments-essentials}

Auf dieser Seite finden Sie die wichtigsten Informationen zum Arbeiten mit der Zuweisungsfunktion von [Aktivierungs-Community](overview.md#enablement-community) Sites.

Die Zuweisungsfunktion ist die Möglichkeit, Aktivierungsressourcen und Lernpfade Mitgliedern von Aktivierungsgemeinschaften zuzuweisen.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/enable/components/hbs/myassigned</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learning.path</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Siehe <a href="assignments.md">Zuweisungsfunktion</a></td> 
  </tr>
 </tbody>
</table>

### Abschluss und Erfolgsstatus {#completion-and-success-status}

&quot;Abschluss&quot;und &quot;Erfolgsstatus&quot;werden in Berichten sowie in Statusbannern für Zuweisungen verwendet.

Abschlussstatus:

* Nicht zugewiesen
* Nicht gestartet (neu)
* Wird ausgeführt
* Umfassend

Erfolgsstatus:

* Unknown
* Bestanden
* Fehler

Die einzigen möglichen Kombinationen aus Abschluss und Erfolgsstatus sind:

| **Abschluss** | **Success** |
|---|---|
| Nicht gestartet | unbekannt |
| Wird ausgeführt | unbekannt |
| Umfassend | Bestanden |
| Umfassend | Fehler |

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

### Zuweisungsfunktion {#assignments-function}

Eine Community-Site-Struktur mit [Zuweisungsfunktion](functions.md#assignments-function)enthält eine konfigurierte ` [assignments](assignments.md)` -Komponente.

### Referenz-APIs {#reference-apis}

* [Aktivierungs-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [Reporting-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [Reporting-Analytics-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
