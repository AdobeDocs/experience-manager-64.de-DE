---
title: Assets-Repository-Neustrukturierung in AEM 6.4
seo-title: Assets Repository Restructuring in AEM 6.4
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zur neuen Repository-Struktur in AEM 6.4 für Assets zu migrieren.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Assets.
uuid: 0e3d8163-6274-4d1b-91c7-32ca927fb83c
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 212930fc-3430-4a0a-842c-2fb613ef981f
feature: Upgrading
exl-id: 3d5bbf95-bd1e-453b-b487-517a56fe727f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 79%

---

# Assets-Repository-Neustrukturierung in AEM 6.4{#assets-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kundinnen und Kunden, die auf AEM 6.4 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Neustrukturierungen einzuschätzen, die sich auf AEM Assets auswirken. Einige Änderungen erfordern während des Aktualisierungsprozesses von AEM 6.4 Arbeitsaufwand, während andere bis zu einem Upgrade auf 6.5 verschoben werden können.

**Mit der Aktualisierung auf 6.4**

* [Verschiedenes](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#misc)

**Vor der Aktualisierung auf 6.5**

* [Vorlage für E-Mail-Benachrichtigung für Asset-/Sammlungsereignis](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#asset-collection-event-e-mail-notification-template)
* [Klassische Designs zur Asset-Freigabe](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#classic-asset-share-designs)
* [Vorlage für E-Mail-Benachrichtigung zum Asset-Download](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#download-asset-e-mail-notification-template)
* [Beispiel-DRM-Lizenzen](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#example-drm-licenses)

* [Vorlage für E-Mail-Benachrichtigung zu Link-Freigabe](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#link-share-e-mail-notification-template)
* [InDesign-Workflow-Skripts](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#indesign-workflow-scripts)
* [Konfigurationen für die Videotranskodierung](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#video-transcoding-configurations)
* [Verschiedenes](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/assets-repository-restructuring-in-aem-6-4.html#misc2)

## Mit der Aktualisierung auf 6.4 {#with-upgrade}

### Verschiedenes {#misc}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td>/etc/dam/jobs</td> 
  </tr> 
  <tr> 
   <td><strong>Neuer Speicherort</strong></td> 
   <td>/var/dam/jobs</td> 
  </tr> 
  <tr> 
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Wenn ein benutzerdefinierter Code von diesem Speicherort abhängig ist (d. h. der Code basiert explizit auf diesem Pfad), muss der Code aktualisiert werden, um den neuen Speicherort vor der Aktualisierung zu verwenden. Idealerweise werden Java-APIs verwendet, wenn verfügbar, um Abhängigkeiten von einem bestimmten Pfad im JCR zu reduzieren.</p> <p>Temporärer Speicherort, um die ZIP-Datei für das Herunterladen des Clients zu speichern. Eine Aktualisierung ist nicht notwendig, wenn der Client das Herunterladen des Assets anfordert. Es wird eine Datei am neuen Speicherort generiert.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend</td> 
  </tr> 
 </tbody> 
</table>

## Vor der Aktualisierung auf 6.5 {#prior-to-upgrade}

### Vorlage für E-Mail-Benachrichtigung für Asset-/Sammlungsereignis {#asset-collection-event-e-mail-notification-template}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/notification/email/default</code></td> 
  </tr> 
  <tr> 
   <td><strong>Neuer Speicherort</strong></td> 
   <td><p><code>/libs/settings/dam/notification</code></p> <p><code>/apps/settings/dam/notification</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Wenn die E-Mail-Vorlagen vom Kunden geändert wurden, führen Sie die folgenden Schritte aus, um sie an die neue Repository-Struktur anzupassen:</p> 
    <ol> 
     <li>Die E-Mail-Vorlage <code>/libs/settings/dam/notification</code> sollte von <strong><code>/etc/notification/email/default</code></strong> nach <strong><code>/apps/settings/notification/email/default</code></strong> kopiert werden. 
      <ol> 
       <li>Da sich das Ziel in <strong><code>/apps</code></strong> befindet, sollte diese Änderung in SCM erhalten bleiben.</li> 
      </ol> </li> 
     <li>Entfernen Sie den Ordner <strong><code>/etc/dam/notification/email/default</code></strong>, nachdem die darin enthaltenen E-Mail-Vorlagen verschoben wurden.<br /> 
      <ol> 
       <li>Wenn keine Aktualisierungen der E-Mail-Vorlage unter <strong> <code>/etc/notification/email/default</code></strong> vorgenommen wurden, kann der Ordner entfernt werden, da die ursprüngliche E-Mail-Vorlage als Bestandteil der AEM 6.4-Installation unter <strong><code>/libs/settings/notification/email/default</code></strong> vorhanden ist.</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Klassische Designs zur Asset-Freigabe {#classic-asset-share-designs}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/designs/assetshare</code></td> 
  </tr> 
  <tr> 
   <td><strong>Neuer Speicherort</strong></td> 
   <td><p><code>/libs/settings/wcm/designs/assetshare</code></p> <p><code>/apps/settings/wcm/designs/assetshare</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Für alle Entwürfe, die in SCM verwaltet werden und in die nicht während der Laufzeit von Design-Dialogfeldern geschrieben wird, führen Sie die folgenden Schritte aus, um das neueste Modell anzupassen:</p> 
    <ol> 
     <li>Kopieren Sie die Designs vom bisherigen Speicherort an den neuen Speicherort unter <code>/apps</code>.</li> 
     <li>Wandeln Sie die gesamten CSS-, JavaScript- und statischen Ressourcen im Design in eine <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client-Bibliothek</a> mit <code>allowProxy = true</code> um.</li> 
     <li>Aktualisieren Sie die Verweise auf den vorherigen Speicherort in der Eigenschaft <code>cq:designPath</code> über <strong>AEM &gt; Sites &gt; Seiten für benutzerdefinierte Site &gt; Seiteneigenschaften &gt; Erweitert &gt; Design</strong>.</li> 
     <li>Aktualisieren Sie alle Seiten, die auf den vorherigen Speicherort verweisen, sodass sie die neue Kategorie der Client-Bibliothek verwenden. Dies erfordert auf der Seite eine Aktualisierung des Implementierungs-Codes.</li> 
     <li>Aktualisieren Sie die Dispatcher-Regeln, um das Bedienen von Client-Bibliotheken über das Proxy-Servlet <code>/etc.clientlibs/</code> zuzulassen.</li> 
    </ol> <p>Für alle Designs, die nicht in SCM verwaltet werden und die zur Laufzeit über Design-Dialoge geändert werden, verschieben Sie keine bearbeitbaren Designs aus <code>/etc</code>.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Vorlage für E-Mail-Benachrichtigung zum Asset-Download {#download-asset-e-mail-notification-template}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/dam/workflow/notification/email/downloadasset</code></td> 
  </tr> 
  <tr> 
   <td><strong>Neuer Speicherort</strong></td> 
   <td><p><code>/libs/settings/dam/workflownotification/email/downloadasset</code></p> <p><code>/apps/settings/dam/workflownotification/email/downloadasset</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Wenn die E-Mail-Vorlagen (<strong>downloadasset</strong> oder<strong> transientworkflowcompleted</strong>) geändert wurden, befolgen Sie die nachstehenden Schritte, um sie an die neue Struktur anzupassen:</p> 
    <ol> 
     <li>Die aktualisierte E-Mail-Vorlage sollte aus <strong><code>/etc/dam/workflow/notification/email/downloadasset</code></strong> nach <strong><code>/apps/settings/dam/workflow/notification/email/downloadasset</code></strong> kopiert werden 
      <ol> 
       <li>Da sich das Ziel in <strong><code>/apps</code></strong> befindet, sollte diese Änderung in SCM erhalten bleiben.</li> 
      </ol> </li> 
     <li>Entfernen Sie den Ordner <code>/etc/dam/workflow/notification/email/downloadasset </code>, nachdem die darin enthaltenen E-Mail-Vorlagen verschoben wurden.<br /> 
      <ol> 
       <li>Wenn keine Aktualisierungen der E-Mail-Vorlage unter <strong> <code>/etc</code></strong> vorgenommen wurden, kann der Ordner entfernt werden, da die ursprüngliche E-Mail-Vorlage als Bestandteil der AEM 6.4-Installation unter <strong><code>/libs/settings/dam/workflownotification/email/downloadasset</code></strong> vorhanden ist.</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Anmerkungen</strong></td> 
   <td>Auch wenn <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> technisch für die Suche unterstützt wird (hat Vorrang vor /apps über das übliche Sling CAConfig-Lookup, aber kommt nach <code>/etc</code>), kann die Vorlage in <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> platziert werden. Dies wird jedoch nicht empfohlen, da es keine Laufzeitbenutzeroberfläche gibt, um die Bearbeitung der E-Mail-Vorlage zu erleichtern.</td> 
  </tr> 
 </tbody> 
</table>

### Beispiel-DRM-Lizenzen {#example-drm-licenses}

| **Vorheriger Speicherort** | `/etc/dam/drm/licenses/` |
|---|---|
| **Neuer Speicherort** | `/libs/settings/dam/drm` |
| **Leitfaden für die Neustrukturierung** | Nicht zutreffend |
| **Anmerkungen** | Nicht zutreffend |

### Vorlage für E-Mail-Benachrichtigung zu Link-Freigabe {#link-share-e-mail-notification-template}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/dam/adhocassetshare</code></td> 
  </tr> 
  <tr> 
   <td><strong>Neuer Speicherort</strong></td> 
   <td><p><code>/libs/settings/dam/adhocassetshare</code></p> <p><code>/apps/settings/dam/adhocassetshare</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Wenn die E-Mail-Vorlage vom Kunden geändert wurde, sollte sie anschließend an die neue Repository-Struktur angepasst werden:</p> 
    <ol> 
     <li>Die aktualisierte E-Mail-Vorlage sollte aus <strong><code>/etc/dam/adhocassetshare</code></strong> nach <strong><code>/apps/settings/dam/adhocassetshare</code></strong> kopiert werden 
      <ol> 
       <li>Da sich das Ziel in <strong><code>/apps</code></strong> befindet, sollte diese Änderung in SCM erhalten bleiben.</li> 
      </ol> </li> 
     <li>Entfernen Sie den Ordner <strong><code>/etc/dam/adhocassetshare</code></strong>, nachdem die darin enthaltenen E-Mail-Vorlagen verschoben wurden.<br /> 
      <ol> 
       <li>Wenn keine Aktualisierungen der E-Mail-Vorlage unter <strong> <code>/etc</code></strong> vorgenommen wurden, kann der Ordner entfernt werden, da die ursprüngliche E-Mail-Vorlage als Bestandteil der AEM 6.4-Installation unter <strong><code>/libs/settings/dam/adhocassetshare</code></strong> vorhanden ist.</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Anmerkungen</strong></td> 
   <td>Auch wenn <code>/conf/global/settings/dam/adhocassetshare</code> technisch für die Suche unterstützt wird (hat Vorrang vor <code>/apps</code> über das übliche Sling CAConfig-Lookup, aber kommt nach <code>/etc</code>), kann die Vorlage in <code>/conf/global/settings/dam/adhocassetshare</code> platziert werden. Dies wird jedoch nicht empfohlen, da es keine Laufzeitbenutzeroberfläche gibt, um die Bearbeitung der E-Mail-Vorlage zu erleichtern</td> 
  </tr> 
 </tbody> 
</table>

### InDesign-Workflow-Skripts {#indesign-workflow-scripts}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/dam/indesign/scripts</code></td> 
  </tr> 
  <tr> 
   <td><strong>Neuer Speicherort</strong></td> 
   <td><p><code>/libs/settings/dam/indesign</code></p> <p><code>/apps/settings/dam/indesign</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>So nehmen Sie eine Anpassung an eine neue Repository-Struktur vor:</p> 
    <ol> 
     <li>Kopieren Sie alle benutzerdefinierten oder geänderten Skripte aus <strong><code>/etc/dam/indesign/scripts</code></strong> nach <strong><code>/apps/settings/dam/indesign/scripts</code></strong><br />. 
      <ol> 
       <li>Kopieren Sie nur neue oder geänderte Skripte, da von AEM bereitgestellte unveränderte Skripte über <strong><code>/libs/settings</code></strong> in AEM 6.4 zur Verfügung stehen.</li> 
      </ol> </li> 
     <li>Suchen Sie alle Workflow-Modelle, die den Medienextraktionsprozess-WF-Schritt verwenden. 
      <ol> 
       <li>Aktualisieren Sie für jede Instanz des Workflow-Schrittes die Pfade in config, sodass sie auf die entsprechenden Skripte unter <strong> <code>/apps/settings/dam/indesign/scripts</code></strong> oder <strong><code>/libs/settings/dam/indesign/scripts</code></strong> verweisen.</li> 
      </ol> </li> 
     <li>Entfernen Sie <strong> <code>/etc/dam/indesign/scripts</code></strong> vollständig.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Anmerkungen</strong></td> 
   <td>Es ist empfehlenswert, benutzerdefinierte Skripte unter <code>/apps</code> zu speichern, dem vorgesehenen Speicherort für Code.</td> 
  </tr> 
 </tbody> 
</table>

### Konfigurationen für die Videotranskodierung {#video-transcoding-configurations}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/dam/video</code></td> 
  </tr> 
  <tr> 
   <td><strong>Neuer Speicherort</strong></td> 
   <td><p><code>/libs/settings/dam/video</code></p> <p><code>/apps/settings/dam/video</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Anpassungen auf Projektebene müssen ausgeschnitten und in die gleichgestellten Pfade <code>/apps</code> oder <code>/conf</code> eingefügt werden.</p> <p>So nehmen Sie eine Anpassung an die Repository-Struktur von AEM 6.4 vor:</p> 
    <ol> 
     <li>Kopieren Sie alle geänderten Videokonfigurationen aus <code>/etc/dam/video</code> nach <code>/apps/settings/dam/video</code></li> 
     <li>Remove <code>/etc/dam/video</code></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend</td> 
  </tr> 
 </tbody> 
</table>

### Konfigurationen von Viewer-Vorgaben {#viewer-preset-configurations}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><code>/etc/dam/presets/viewer</code></td> 
  </tr> 
  <tr> 
   <td><strong>Neuer Speicherort</strong></td> 
   <td><p><code>/libs/settings/dam/dm/presets/viewer</code></p> <p><code>/conf/global/settings/dam/dm/presets/viewer</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Für die vordefinierte Viewer-Vorgabe ist sie nur am neuen Speicherort verfügbar.</p> <p>Für die benutzerdefinierte Viewer-Vorgabe:</p> 
    <ul> 
     <li>Sie müssen ein Migrationsskript ausführen, um den Knoten von <code>/etc</code> nach <code>/conf</code> zu verschieben. Das Skript befindet sich unter <em>https://serveradresse:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em>.</li> 
     <li>Alternativ können Sie die Konfiguration bearbeiten und sie wird automatisch am neuen Speicherort gespeichert.</li> 
    </ul> <p>Beachten Sie, dass Sie ihren copyURL/embed-Code nicht anzupassen brauchen, um auf <code>/conf</code> zu verweisen. Die vorhandene Anforderung an <code>/etc</code> wird zum richtigen Inhalt aus <code>/conf</code> umgeleitet.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend</td> 
  </tr> 
 </tbody> 
</table>

### Verschiedenes {#misc2}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Vorheriger Speicherort</strong></td> 
   <td><p><code>/etc/clientlibs/foundation/asseteditor</code></p> <p><code>/etc/clientlibs/foundation/assetshare</code></p> <p><code>/etc/clientlibs/foundation/assetinsights</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Neuer Speicherort</strong></td> 
   <td><code>/libs/dam/clientlibs</code></td> 
  </tr> 
  <tr> 
   <td><strong>Leitfaden für die Neustrukturierung</strong></td> 
   <td><p>Passen Sie alle Verweise so an, dass sie auf die neuen Ressourcen unter <code>/libs</code> verweisen, indem Sie das Präfix <code>/etc.clientlibs/</code> zum Zulassen als Proxy-Präfix verwenden.</p> <p>Entfernen Sie abschließend die Ordner für die migrierten Client-Bibliotheken aus dem Verzeichnis <code>/etc/clientlibs/foundation/</code></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Anmerkungen</strong></td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr> 
 </tbody> 
</table>
