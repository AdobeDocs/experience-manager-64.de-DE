---
title: Dynamic Media-Repository-Umstrukturierung in AEM 6.4
seo-title: Dynamic Media repository restructuring in AEM 6.4
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zur neuen Repository-Struktur in AEM 6.4 für Dynamic Media zu migrieren.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Dynamic Media.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: Upgrading
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 68%

---

# Dynamic Media-Repository-Umstrukturierung in AEM 6.4{#dynamic-media-repository-restructuring-in-aem}

Wie im übergeordneten Element beschrieben [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md) -Seite verwenden, sollten Kunden, die auf AEM 6.4 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen zu bewerten, die sich auf die Dynamic Media-Lösung auswirken. Einige Änderungen erfordern einen Arbeitsaufwand während des Aktualisierungsprozesses auf AEM 6.4, während andere bis zu einer Aktualisierung auf 6.5 verschoben werden können.

**Vor der Aktualisierung auf 6.5**

* [Benutzerdefinierte Konfigurationen für die adaptive Video-Kodierung](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Cloud-Konfiguration für Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Cloud-Service-Konfiguration für Dynamic Media (DM Hybrid)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - YouTube-Cloud-Service-Konfiguration](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [Verschiedenes](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## Vor der Aktualisierung auf 6.5 {#prior-to-upgrade}

### Benutzerdefinierte Konfigurationen für die adaptive Videokodierung  {#custom-adaptive-video-encoding-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/dam/video/dynamicmedia</code></td> 
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td> 
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Sie können das folgende Migrationsskript ausführen, um zum neuen Speicherort zu migrieren:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Alternativ können Sie die Konfiguration in der AEM-Benutzeroberfläche bearbeiten, und die Änderungen werden am neuen Speicherort gespeichert.</p> </td> 
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr>
 </tbody>
</table>

### Cloud-Konfiguration für Dynamic Media (DMS7) {#dynamic-media-dms-cloud-configuration}

<table> 
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td> 
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Der Kunde kann an diesem Speicherort ein Migrationsskript ausführen:<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>Starten Sie das Dynamic Media-OSGi-Bundle neu.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend</td> 
  </tr>
 </tbody>
</table>

### Konfiguration des Dynamic Media-Cloud Service (DM Hybrid) {#cloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td> 
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Sie können das untenstehende Migrationsskript ausführen, damit eine Anpassung an das aktuelle Modell erfolgt:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media - YouTube-Cloud Service-Konfiguration  {#youtubecloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/cloudservices/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td> 
   <td><code>/libs/settings/dam/dm/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>1. Rückgängigmachen der Veröffentlichung aller Videos von YouTube<br /> 2. Erstellen Sie die YouTube-Konfiguration mithilfe der neuen Touch-optimierten Benutzeroberfläche (aus <code>/conf</code>), einschließlich des Kopierens aller Kanäle aus dem alten Speicherort<br /> 3. Veröffentlichen Sie alle Videos neu auf YouTube.</p> <p>Dieser Workflow führt zu neuen YouTube-URLs. Wenn Sie die Veröffentlichung nicht vor der Erstellung einer neuen YouTube-Konfiguration mit der Touch-optimierten Benutzeroberfläche aufheben, werden unter „Eigenschaften“ mehrere YouTube-URLs aufgelistet, da die neu erstellten Kanäle bei Gelegenheit erneut veröffentlicht werden. Dies bedeutet, dass Sie unbrauchbar gewordene URLs haben, die unter „Eigenschaften“ aufgelistet sind.</p> </td> 
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr>
 </tbody>
</table>

### Verschiedenes {#misc}

<table> 
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/dam/imageserver/macros</code></td> 
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td> 
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Der Kunde kann das untenstehende Migrationsskript ausführen.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Alternativ können Sie die Konfiguration in der AEM-Benutzeroberfläche bearbeiten, und die Änderungen werden am neuen Speicherort gespeichert.</p> </td> 
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend</td> 
  </tr>
 </tbody>
</table>

<table> 
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/dam/presets/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td> 
   <td><code>/libs/settings/dam/dm/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Der Kunde kann das untenstehende Migrationsskript ausführen.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend</td> 
  </tr>
 </tbody>
</table>
