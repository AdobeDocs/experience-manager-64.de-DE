---
title: Grundlagen der Zuweisung
seo-title: Grundlagen der Zuweisung
description: Übersicht über Zuweisungsfunktionen für Communities
seo-description: Übersicht über Zuweisungsfunktionen für Communities
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 14%

---


# Zuweisungen Essentials {#assignments-essentials}

Auf dieser Seite finden Sie die wesentlichen Informationen zum Arbeiten mit der Zuweisungsfunktion von [Aktivierungs-Community](overview.md#enablement-community)-Sites.

Die Funktion &quot;Zuweisungen&quot;ermöglicht die Zuweisung von Ressourcen und Lernpfaden zu Mitgliedern von Communities, die eine Aktivierung ermöglichen.

## Grundlagen für clientseitige {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/enable/components/hbs/myassign</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td> 
   <td>Nein</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enable.hbs.breadcrumbs<br /> cq.social.enable.hbs.myassign<br /> cq.social.enable.hbs.resource<br /> cq.social.enable.hbs.learn.path</td> 
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

### Abschluss- und Erfolgsstatus {#completion-and-success-status}

Der Status &quot;Abschluss&quot;und &quot;Erfolg&quot;werden in Berichten sowie in Statusbannern für Zuweisungen verwendet.

Abschlussstatus:

* Nicht zugewiesen
* Nicht gestartet (neu)
* Wird ausgeführt
* Fertig stellen

Erfolgsstatus:

* Unknown
* Bestanden
* Fehler

Die einzigen möglichen Kombinationen aus Abschluss und Erfolgsstatus sind:

| **Abschluss** | **Success** |
|---|---|
| Nicht gestartet | unbekannt |
| Wird ausgeführt | unbekannt |
| Fertig stellen | Bestanden |
| Fertig stellen | Fehler |

## Grundlagen für serverseitige {#essentials-for-server-side}

### Zuweisungsfunktion {#assignments-function}

Eine Community-Site-Struktur, die die Funktion [Zuweisungen](functions.md#assignments-function) enthält, enthält eine konfigurierte Komponente ` [assignments](assignments.md)`.

### Referenz-APIs {#reference-apis}

* [Aktivierungs-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [Berichte-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [Berichte Analytics-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)