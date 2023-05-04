---
title: Wählen eines Persistenztyps für eine AEM Forms-Installation
seo-title: Choosing a persistence type for an AEM Forms installation
description: Wählen Sie einen Persistenztyp mit Bedacht aus. Dies hilft Ihnen beim Aufbau einer effizienten und skalierbaren AEM Forms-Umgebung.
seo-description: Choose a persistence type wisely. It helps you build an efficient and scale able AEM Forms environment.
uuid: 1c692502-5039-4757-9358-1772772b3904
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: a972fb35-38a7-4b83-99bd-6a6dddf8043b
role: Admin
exl-id: ef486673-30fe-410a-83cf-c55be6064ce4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 26%

---

# Wählen eines Persistenztyps für eine AEM Forms-Installation {#choosing-a-persistence-type-for-an-aem-forms-installation}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wählen Sie einen Persistenztyp mit Bedacht aus. Dies hilft Ihnen beim Aufbau einer effizienten und skalierbaren AEM Forms-Umgebung.

Persistenz ist die Methode zum Speichern von Inhalten auf den physischen Speichern. Sie definiert die tatsächliche Datenstruktur und den Speichermechanismus für die Daten. MicroKernels fungieren in AEM Forms als Persistenzmanager. AEM Forms unterstützt Persistenz (MicroKernals) des Typs TarMK, MongoMK und RDBMK. Sie können je nach Zweck und Bereitstellungstyp (Einzelserver, Farm oder Cluster) einer AEM Forms-Instanz einen Persistenztyp für AEM Forms auswählen.

>[!NOTE]
>
>LiveCycle ES4 SP1 verwendet TarPM-Persistenz zum Speichern von Inhalten.

In der folgenden Tabelle werden alle unterstützten Persistenztypen zusammen mit verschiedenen Parametern aufgeführt, um Ihnen die Auswahl eines Persistenztyps für Ihre Umgebung zu erleichtern:

<table> 
 <tbody>
  <tr>
   <th><strong>Installationstyp/Kosten</strong></th> 
   <th><strong>TarMK</strong></th> 
   <th><strong>MongoMk</strong></th> 
   <th><strong>RDBMK</strong></th> 
  </tr>
  <tr>
   <th><strong>Eigenständige Einrichtung</strong></th> 
   <td>Unterstützt<br /> </td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <th><strong>Cluster-Einrichtung</strong></th> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <th><strong>Lizenzkosten</strong></th> 
   <td>Im Lieferumfang von AEM enthalten </td> 
   <td>Separate Lizenz erforderlich</td> 
   <td>Separate Lizenz erforderlich</td> 
  </tr>
 </tbody>
</table>

TarMK ist für Leistung konzipiert, während MongoMK und RDBMK für Skalierbarkeit ausgelegt sind. Adobe empfiehlt TarMK als Standardpersistenztechnologie für alle AEM Forms-Bereitstellungsszenarien für die Autoren- und Veröffentlichungsinstanz, außer in Fällen, die im Abschnitt [Mongo auswählt oder ein relationale Datenbank-Microkernel über TarMK](#p-choosing-mongo-or-a-relational-database-microkernel-over-tarmk-p) erläutert werden.

Eine Liste der unterstützten Microkernel finden Sie unter [Technische Anforderungen für AEM Forms unter OSGi](/help/sites-deploying/technical-requirements.md) oder [Von AEM Forms on JEE unterstützte Plattformkombinationen](/help/forms/using/aem-forms-jee-supported-platforms.md) Artikel.

## Mongo oder ein relationaler Datenbank-Microkernel über TarMK auswählen {#choosing-mongo-or-a-relational-database-microkernel-over-tarmk}

Eine skalierbare (geclusterte) AEM Forms-Umgebung ist ein Satz von zwei oder mehr horizontal konfigurierten aktiven Autoreninstanzen. Sie können festlegen, dass mehr als eine Autoreninstanz ausgeführt werden soll, wenn ein einzelner Server, der alle gleichzeitigen Authoring-Aktivitäten unterstützt, nicht mehr tragbar ist.

Für eine skalierbare (geclusterte) AEM Forms on JEE-Umgebung werden nur der Persistenztyp MongoMK und RDBMK unterstützt. Die Anzahl der Server oder die Größe der skalierbaren Umgebung variiert je nach Installation. Eine Liste der Überlegungen und Beispiele finden Sie unter [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md) und [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md) Artikel. Sie können sich auch an den AEM Forms-Support wenden, um detaillierte Informationen zur Kapazitätsplanung für AEM Forms mit RDBMK und TarMK zu erhalten.
