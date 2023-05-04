---
title: Best Practices für die Bereitstellung
seo-title: Deploying Best Practices
description: Bereitstellen und Verwalten von Best Practices.
seo-description: Deploying and maintaining best practices.
uuid: 4546ed2c-43d5-40f3-874f-567b324e78c2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 4b5c0677-c630-4fae-867e-4f4583ac8507
exl-id: 0c8fefb5-6fa0-4fab-a890-9f5ae7508459
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 86%

---

# Best Practices für die Bereitstellung{#deploying-best-practices}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In den Best Practices für die Bereitstellung wird beschrieben, wie AEM am effizientesten und wirkungsvollsten bereitgestellt und gewartet wird. Diese wachsende Themenliste umfasst verschiedene Bereiche in AEM.

Für die folgenden Bereiche ist Dokumentation zu Best Practices und Empfehlungen für die Bereitstellung und Wartung verfügbar:

* [OAK](#oak)
* [Communities](#communities)
* [Benutzeroberfläche](#ui)
* [Leistung](#performance)

Informationen zu Best Practices zur Verwaltung, Entwicklung oder Inhaltserstellung finden Sie in den folgenden Abschnitten:

* [Best Practices für die Verwaltung](/help/sites-administering/administer-best-practices.md)
* [Best Practices für die Entwicklung](/help/sites-developing/best-practices.md)
* [Best Practices für die Inhaltserstellung](/help/sites-authoring/best-practices.md)

Spezifische Dokumente werden in den folgenden Tabellen beschrieben und mit ihnen verknüpft.

## OAK {#oak}

[Oak](/help/sites-deploying/platform.md) ist ein leistungsstarkes skalierbares, hierarchisches Inhalts-Repository und bildet die Basis von AEM.

<table> 
 <tbody>
  <tr>
   <td><p>Skalierbarkeit, Leistung und Notfallwiederherstellung</p> </td> 
   <td><a href="/help/sites-deploying/performance.md">Leistung und Skalierbarkeit</a></td> 
   <td>Ein Whitepaper über die technischen Funktionen für Agilität, Leistung und Notfallwiederherstellung</td> 
  </tr>
  <tr>
   <td>Empfohlene OAK-Implementierungen</td> 
   <td><a href="/help/sites-deploying/recommended-deploys.md">Empfohlene Implementierungen</a></td> 
   <td>Beschreibt Implementierungsszenarien</td> 
  </tr>
  <tr>
   <td>Mongo-Topologie</td> 
   <td><a href="/help/sites-deploying/recommended-deploys.md">Best Practices für die Mongo-Topologie</a></td> 
   <td>Beschreibt die Mongo-Topologie – wann welche Topologie verwendet werden soll.</td> 
  </tr>
  <tr>
   <td>Datenspeicheroptionen</td> 
   <td><a href="/help/sites-deploying/data-store-config.md">Konfigurieren von Knoten und Datenspeichern</a></td> 
   <td>In diesem Dokument werden Best Practices zum Speichern von Binärdaten und Inhaltsknoten erläutert. Enthält Informationen zum Datenspeicher Amazon S3.</td> 
  </tr>
  <tr>
   <td>Suchen in OAK</td> 
   <td><a href="/help/sites-deploying/best-practices-for-queries-and-indexing.md">Best Practices für Abfragen und Indizierung</a><br /> </td> 
   <td>Beschreibt Best Practices für die Indizierung von Inhalten.</td> 
  </tr>
 </tbody>
</table>

## Communities {#communities}

AEM Communities vereinfacht die Erstellung und Verwaltung von On-Premise-Communities. Informationen zu Best Practices für AEM Communities finden Sie hier:

[Community-Inhaltsspeicher](/help/communities/working-with-srp.md): Erläutert die neue Funktion des gemeinsamen Speichers für benutzergenerierte Inhalte (UGC) und Überlegungen zur Auswahl der zugrunde liegenden [Topologie](/help/communities/topologies.md).

[Empfohlene Implementierungen für Communities](/help/sites-deploying/recommended-deploys.md#considerations-for-aem-communities) – Beschreibt die empfohlenen Implementierungen für Communities. |

## Benutzeroberfläche {#ui}

Best Practices für die Benutzeroberfläche werden hier beschrieben: 

[Empfehlungen für Kunden zur Benutzeroberfläche](/help/sites-deploying/ui-recommendations.md)

AEM verfügt derzeit über zwei Benutzeroberflächen: die klassische und die Touch-optimierte Benutzeroberfläche in derselben Version. Daher müssen sich Kunden während der Projektimplementierung für die Nutzung der einen oder anderen entscheiden. Dieses Dokument soll bei der Entscheidungsfindung behilflich sein.

## Leistung {#performance}

Best Practices zur Leistung sind hier aufgeführt:

<table> 
 <tbody>
  <tr>
   <td>Best Practices zur Qualitätssicherung</td> 
   <td><a href="/help/sites-deploying/configuring-performance.md#best-practices-for-quality-assurance">Best Practices zur Qualitätssicherung</a></td> 
   <td>Ein einheitlicher Überblick über die Probleme bei der Definition eines Testkonzepts speziell für Leistungstests in der <em>Veröffentlichungsumgebung</em>. Dies ist vor allem für QA-Beauftragte, Projektleitende und Systemadmins von Interesse.</td> 
  </tr>
  <tr>
   <td>Verwenden des Dispatchers mit einem CDN </td> 
   <td><a href="https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher.html#using-dispatcher-with-a-cdn">Verwenden des Dispatchers mit einem CDN</a></td> 
   <td>Ein CDN (Content Delivery Network) wie Akamai Edge Delivery oder Amazon Cloud Front stellt Inhalte von einem Speicherort in der Nähe des Endbenutzers bereit.</td> 
  </tr>
  <tr>
   <td>Leistungsoptimierung</td> 
   <td><a href="/help/sites-deploying/configuring-performance.md">Leistungsoptimierung</a></td> 
   <td>Ein wichtiger Faktor ist die Zeit, die Ihre Website benötigt, um auf Anforderungen durch Besucher zu reagieren.</td> 
  </tr>
  <tr>
   <td>Leistungstests</td> 
   <td><a href="/help/sites-deploying/best-practices-for-performance-testing.md">Best Practices für Leistungstests</a></td> 
   <td>Beschreibt Best Practices für die Durchführung von Leistungstests bei der AEM-Bereitstellung<br />  </td> 
  </tr>
 </tbody>
</table>
