---
title: Integrieren in Dynamic Media Classic
description: Erfahren Sie, wie Sie AEM in Dynamic Media Classic integrieren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
exl-id: 0bfb05b8-7d10-4984-9e89-f1af88938c03
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '5492'
ht-degree: 72%

---

# Integrieren in Dynamic Media Classic {#integrating-with-dynamic-media-classic-scene}

Adobe Dynamic Media Classic ist eine gehostete Lösung für die Verwaltung, Optimierung, Veröffentlichung und Bereitstellung von Rich-Media-Assets für Web-, Mobil-, E-Mail- und Internet-verbundene Anzeigen und Ausdrucke.

Um Dynamic Media Classic zu verwenden, müssen Sie die Cloud-Konfiguration so konfigurieren, dass Dynamic Media Classic und Adobe Experience Manager Assets miteinander interagieren können. In diesem Dokument wird die Konfiguration von Experience Manager und Dynamic Media Classic beschrieben.

Informationen zur Verwendung aller Dynamic Media Classic-Komponenten auf einer Seite und zum Arbeiten mit Videos finden Sie unter [Verwenden von Dynamic Media Classic](../assets/scene7.md).

>[!NOTE]
>
>* Die DHTML-Viewer-Plattform von Dynamic Media Classic wurde offiziell am 31. Januar 2014 eingestellt. Weitere Informationen finden Sie in den [FAQ zur Einstellung von DHTML-Viewer](../sites-administering/dhtml-viewer-endoflifefaqs.md).
>* Bevor Sie Dynamic Media Classic für die Verwendung mit Experience Manager konfigurieren, lesen Sie [Best Practices](#best-practices-for-integrating-scene-with-aem) zur Integration von Dynamic Media Classic mit Experience Manager.
>* Wenn Sie Dynamic Media Classic mit einer benutzerdefinierten Proxy-Konfiguration verwenden, konfigurieren Sie beide HTTP-Client-Proxy-Konfigurationen, da einige Funktionen von Experience Manager die 3.x-APIs und andere die 4.x-APIs verwenden. 3.x wird mit [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) konfiguriert und 4.x wird mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) konfiguriert.
>


## Integration von Experience Manager/Dynamic Media Classic im Vergleich zu Dynamic Media {#aem-scene-integration-versus-dynamic-media}

Experience Manager-Benutzer haben die Wahl zwischen zwei Lösungen für die Arbeit mit Dynamic Media:

* Verwenden Ihrer integrierten Instanz von Experience Manager mit *Dynamic Media Classic*.
* Verwenden *Dynamic Media* die in den Experience Manager integriert ist.

Verwenden Sie die folgenden Kriterien, um zu bestimmen, welche Lösung für Sie am besten geeignet ist:

* Wenn Sie **vorhandene** Dynamic Media Classic-Kunde, dessen Rich-Media-Assets zur Veröffentlichung und Bereitstellung in Dynamic Media Classic gespeichert sind. Sie möchten diese Assets jedoch in das Sites-Authoring (WCM) und/oder Experience Manager Assets zur Verwaltung integrieren und dann die [Experience Manager/Dynamic Media Classic-Punkt-zu-Punkt-Integration](#aem-scene-point-to-point-integration) in diesem Dokument beschrieben.

* Wenn Sie Experience Manager-**Neukunde** sind und Rich-Media-Bereitstellung benötigen, wählen Sie die [Dynamic Media-Option](#aem-dynamic-media) aus. Diese Option ist am sinnvollsten, wenn Sie über kein vorhandenes S7-Konto verfügen und wenn Sie nicht über viele im System gespeicherte Assets verfügen.

* Verwenden Sie in bestimmten Fällen beide Lösungen. Das [Szenario einer Doppelnutzung](/help/sites-administering/scene7.md#dual-use-scenario) beschreibt dieses Szenario.

### Punkt-zu-Punkt-Integration von Experience Manager/Dynamic Media Classic {#aem-scene-point-to-point-integration}

Wenn Sie in dieser Lösung mit Assets arbeiten, nutzen Sie eine der folgenden Vorgehensweisen:

* Laden Sie Assets direkt in Dynamic Media Classic hoch und greifen Sie anschließend über den **Dynamic Media Classic**-Inhaltsbrowser für die Seitenbearbeitung darauf zu.
* Laden Sie sie in Experience Manager Assets hoch und aktivieren Sie dann die automatische Veröffentlichung in Dynamic Media Classic. Der Zugriff erfolgt über den **Assets**-Inhaltsbrowser für die Seitenbearbeitung.

Die von Ihnen für diese Integration verwendeten Komponenten befinden sich im Komponentenbereich **Dynamic Media Classic** im [Designmodus.](/help/sites-authoring/author-environment-tools.md#page-modes)

### Experience Manager Dynamic Media {#aem-dynamic-media}

Experience Manager Dynamic Media ist die Vereinigung von Dynamic Media Classic-Funktionen direkt innerhalb der Experience Manager Platform.

Wenn Sie innerhalb dieser Lösung mit Assets arbeiten, befolgen Sie diesen Workflow:

1. Laden Sie Assets mit einzelnen Bildern und Videos direkt in Experience Manager hoch.
1. Kodieren Sie Videos direkt in Experience Manager.
1. Erstellen Sie bildbasierte Sets direkt in Experience Manager.
1. Fügen Sie Bildern und Videos bei Bedarf interaktive Elemente hinzu.

Die von Ihnen für Dynamic Media verwendeten Komponenten befinden sich im Komponentenbereich **[!UICONTROL Dynamic Media]** im [Designmodus](/help/sites-authoring/author-environment-tools.md#page-modes). Sie umfassen Folgendes:

* **[!UICONTROL Dynamic Media]** – Die Komponente **[!UICONTROL Dynamic Media]** ist intelligent. In Abhängigkeit davon, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bildsets sowie Rotationssets, Sets für gemischte Medien und Videos. Zudem ist der Viewer dynamisch. Die Anzeigegröße ändert sich demnach automatisch auf Grundlage der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

* **[!UICONTROL Interaktive Medien]** - die **[!UICONTROL Interaktive Medien]** -Komponente ist für Karussellbanner, interaktive Bilder und interaktive Videos gedacht, die interaktiv sind, z. B. Hotspots oder Imagemaps. Diese Komponente ist intelligent. Je nachdem, ob Sie ein Bild oder ein Video hinzufügen, haben Sie verschiedene Optionen. Darüber hinaus ist der Viewer responsiv. Das heißt, die Größe des Bildschirms ändert sich automatisch entsprechend der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

### Szenario einer Doppelnutzung {#dual-use-scenario}

Standardmäßig können Sie die Dynamic Media- und Dynamic Media Classic-Integrationsfunktionen von Experience Manager gleichzeitig nutzen. Die folgende Tabelle mit Anwendungsfällen beschreibt, wo Sie bestimmte Bereiche ein- und ausschalten können.

So verwenden Sie Dynamic Media und Dynamic Media Classic gleichzeitig:

1. Konfigurieren Sie [Dynamic Media Classic](#creating-a-cloud-configuration-for-scene) in Cloud-Services.
1. Befolgen Sie die Anleitungen, die auf Ihren jeweiligen Anwendungsfall zutreffen:

   <table> 
    <tbody> 
    <tr> 
    <td> </td> 
    <td> </td> 
    <td><strong>Dynamic Media</strong></td> 
    <td> </td> 
    <td><strong>Dynamic Media Classic-Integration</strong></td> 
    <td> </td> 
    </tr> 
    <tr> 
    <td><strong>Voraussetzung</strong></td> 
    <td><strong>Anwendungsfall-Workflow</strong></td> 
    <td><strong>Bildbearbeitung/Video</strong></td> 
    <td><strong>Dynamic Media-Komponente</strong></td> 
    <td><strong>S7-Inhaltsbrowser und -Komponenten</strong></td> 
    <td><strong>Automatisches Hochladen von Assets in S7</strong></td> 
    </tr> 
    <tr> 
    <td>Neu bei Sites und Dynamic Media</td> 
    <td>Laden Sie Assets in Experience Manager hoch und verwenden Sie die Experience Manager Dynamic Media-Komponente zum Erstellen von Assets auf Sites-Seiten.</td> 
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td> 
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td> 
    <td>Aus</td> 
    <td>Aus</td> 
    </tr> 
    <tr> 
    <td>Im Einzelhandel und neu bei Sites und Dynamic Media</td> 
    <td>Laden Sie NICHT produktbezogene Assets zur Verwaltung und Bereitstellung in Experience Manager hoch. Laden Sie PRODUKT-Assets in Dynamic Media Classic hoch und verwenden Sie den Dynamic Media Classic-Inhaltsbrowser in Experience Manager und die Komponente, um Produktdetailseiten auf Sites zu erstellen.</td> 
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td> 
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td> 
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td> 
    <td>Aus</td> 
    </tr> 
    <tr> 
    <td>Neu bei Assets und Dynamic Media</td> 
    <td>Laden Sie Assets in Experience Manager Assets hoch und verwenden die veröffentlichte URL/den Einbettungs-Code aus Dynamic Media.</td> 
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td> 
    <td>Aus</td> 
    <td>Aus</td> 
    <td>Aus</td> 
    </tr> 
    <tr> 
    <td>Neu bei Dynamic Media und Vorlagen</td> 
    <td>Verwenden Sie Dynamic Media für Bildbearbeitung und Videos. Erstellen Sie Bildvorlagen in Dynamic Media Classic und verwenden Sie den Content Finder von Dynamic Media Classic, um Vorlagen in Sites-Seiten aufzunehmen.</td> 
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td> 
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td> 
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td> 
    <td>Aus</td> 
    </tr> 
    <tr> 
    <td>Bestehender Dynamic Media Classic-Kunde und neu bei Sites</td> 
    <td>Laden Sie Assets in Dynamic Media Classic hoch und verwenden Sie den Experience Manager Dynamic Media Classic-Inhaltsbrowser, um Assets auf Sites-Seiten zu suchen und zu erstellen.</td> 
    <td>Aus</td> 
    <td>Aus</td> 
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td> 
    <td>Aus</td> 
    </tr> 
    <tr> 
    <td>Bestehender Dynamic Media Classic-Kunde und neu bei Sites und Assets</td> 
    <td>Laden Sie Assets in DAM hoch und führen Sie eine automatische Veröffentlichung in Dynamic Media Classic zur Bereitstellung durch. Verwenden Sie den Experience Manager Dynamic Media Classic-Inhaltsbrowser, um Assets auf Sites-Seiten zu suchen und zu erstellen.</td> 
    <td>Aus</td> 
    <td>Aus</td> 
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td> 
    <td><p><a href="#configuringautouploadingfromaemassets">Ein</a></p> <p>(Siehe Schritt 4)</p> </td> 
    </tr> 
    <tr> 
    <td>Bestehender Dynamic Media Classic-Kunde und neu bei Assets</td> 
    <td><p>Laden Sie Assets in Experience Manager hoch und verwenden Sie Dynamic Media, um Ausgabedarstellungen zum Herunterladen/Freigeben zu generieren. Experience Manager Assets wird automatisch zur Bereitstellung in Dynamic Media Classic veröffentlicht.</p> <p><strong>Wichtig:</strong> Informiert die doppelte Verarbeitung und die in Experience Manager generierten Ausgabedarstellungen werden nicht mit Dynamic Media Classic synchronisiert</p> </td> 
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td> 
    <td>Aus</td> 
    <td>Aus</td> 
    <td><p><a href="#configuringautouploadingfromaemassets">Ein</a></p> <p>(Siehe Schritt 4)</p> </td> 
    </tr> 
    </tbody> 
    </table>

1. (Optional, siehe die Tabelle mit den Anwendungsfällen) – Richten Sie die [Dynamic Media-Cloud-Konfiguration](/help/assets/config-dynamic.md) ein und [aktivieren Sie den Dynamic Media-Server](/help/assets/config-dynamic.md).
1. (Optional) (siehe Tabelle mit Nutzungsszenarios) - Wenn Sie die Option Automatisches Hochladen von Assets in Dynamic Media Classic aktivieren, müssen Sie Folgendes hinzufügen:

   1. Richten Sie das automatische Hochladen in Dynamic Media Classic ein.
   1. Fügen Sie den Schritt **Dynamic Media Classic-Upload** nach allen Dynamic Media-Workflow-Schritten *am Ende des Workflows* **DAM-Update-Asset** hinzu ( `https://<server>:<host>/cf#/etc/workflow/models/dam/update_asset.html)`.
   1. (Optional) Schränken Sie den Dynamic Media Classic-Asset-Upload nach MIME-Typen in [https://&lt;Server>:&lt;Port>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl) ein. Asset-MIME-Typen, die nicht in dieser Liste enthalten sind, werden nicht auf den Dynamic Media Classic-Server hochgeladen.
   1. (Optional) Richten Sie Videos in der Dynamic Media Classic-Konfiguration ein. Sie können die Videokodierung für Dynamic Media und/oder Dynamic Media Classic aktivieren. Dynamische Ausgabedarstellungen werden für die Vorschau und Wiedergabe lokal in der Experience Manager-Instanz verwendet, während Ausgabedarstellungen von Dynamic Media Classic-Videos auf Dynamic Media Classic-Servern generiert und gespeichert werden. Wenden Sie bei der Einrichtung der Videokodierungs-Services für Dynamic Media und Dynamic Media Classic ein [Videoverarbeitungsprofil](/help/assets/video-profiles.md) auf den Dynamic Media Classic-Asset-Ordner an.
   1. (Optional) [Konfigurieren Sie eine sichere Vorschau in Dynamic Media Classic](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene).

#### Beschränkungen {#limitations}

Wenn sowohl Dynamic Media Classic als auch Dynamic Media aktiviert sind, gelten die folgenden Beschränkungen:

* Das manuelle Hochladen in Dynamic Media Classic durch Auswählen eines Assets und Ziehen des Assets in eine Dynamic Media Classic-Komponente auf einer Experience Manager-Seite funktioniert nicht.
* Obwohl synchronisierte Assets in Experience Manager und Dynamic Media Classic automatisch in Dynamic Media Classic aktualisiert werden, wenn das Asset in Assets bearbeitet wird, wird kein neuer Upload durch eine Rollback-Aktion ausgelöst. Daher erhält Dynamic Media Classic unmittelbar nach einem Rollback nicht die neueste Version. Als Ausweichlösung eignet sich die erneute Bearbeitung, sobald das Rollback abgeschlossen ist.
* Wenn Sie Dynamic Media für einen Anwendungsfall und Dynamic Media Classic-Integration für einen anderen verwenden müssen, damit Dynamic Media-Assets nicht mit dem Dynamic Media Classic-System interagieren, wenden Sie die Dynamic Media Classic-Konfiguration nicht auf den Ordner Dynamic Media an. Wenden Sie die Dynamic Media-Konfiguration (Verarbeitungsprofil) auch nicht auf einen Dynamic Media Classic-Ordner an.

## Best Practices für die Integration von Dynamic Media Classic mit Experience Manager {#best-practices-for-integrating-scene-with-aem}

Bei der Integration von Dynamic Media Classic mit Experience Manager sind in den folgenden Bereichen einige wichtige Best Practices zu beachten:

* Testen der Integration
* Hochladen von Assets direkt aus Dynamic Media Classic, empfohlen für bestimmte Szenarien

Siehe [Bekannte Einschränkungen](#known-limitations-and-design-implications).

### Testen der Integration {#test-driving-your-integration}

Adobe empfiehlt das Testen der Integration, indem Sie den Stammordner nur auf einen Unterordner verweisen lassen statt auf ein ganzes Unternehmen.

>[!CAUTION]
>
>Beim Importieren von Assets aus einem bestehenden Dynamic Media Classic-Unternehmenskonto kann es lange dauern, bis sie in Experience Manager angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic angeben, in dem nicht zu viele Assets vorhanden sind (im Stammordner sind zum Beispiel häufig zu viele Assets enthalten, sodass Ihr System abstürzen kann).

### Hochladen von Assets aus Experience Manager Assets oder Dynamic Media Classic {#uploading-assets-from-aem-assets-versus-from-scene}

Sie können Assets entweder mithilfe der Assets-Funktion (Digital Asset Management) oder durch direkten Zugriff auf Dynamic Media Classic über den Dynamic Media Classic-Inhaltsbrowser in Experience Manager hochladen. Wie Sie vorgehen, hängt von den folgenden Faktoren ab:

* Dynamic Media Classic-Asset-Typen, die Experience Manager Assets noch nicht unterstützt, müssen über den Dynamic Media Classic-Inhaltsbrowser direkt von Dynamic Media Classic auf einer Experience Manager-Website hinzugefügt werden. Ein Beispiel sind Bildvorlagen.
* Bei Asset-Typen, die sowohl von Experience Manager Assets als auch von Dynamic Media Classic unterstützt werden, hängt die Entscheidung über die Art des Uploads von Folgendem ab:

   * Wo befinden sich die Assets heute
   * Wie wichtig ihre Verwaltung in einem gemeinsamen Repository ist

Wenn sich die Assets bereits in Dynamic Media Classic befinden und ihre Verwaltung in einem gemeinsamen Repository nicht wichtig ist, ist der Export in Experience Manager Assets nur zur erneuten Synchronisierung mit Dynamic Media Classic für die Bereitstellung ein unnötiger Umweg. Andernfalls wird empfohlen, Assets in einem einzigen Repository zu speichern und nur für die Bereitstellung mit Dynamic Media Classic zu synchronisieren.

## Dynamic Media Classic-Integration konfigurieren {#configuring-scene-integration}

Sie können Experience Manager so konfigurieren, dass Assets in Dynamic Media Classic hochgeladen werden. Assets von einem CQ-Zielordner können (automatisch oder manuell) von Experience Manager in ein Dynamic Media Classic-Unternehmenskonto hochgeladen werden.

>[!NOTE]
>
>Adobe empfiehlt Ihnen die ausschließliche Verwendung des vorgesehenen Zielordners für den Import von Dynamic Media Classic-Assets. Digitale Assets, die sich außerhalb des Zielordners befinden, können nur in Dynamic Media Classic-Komponenten auf Seiten verwendet werden, auf denen die Dynamic Media Classic-Konfiguration aktiviert wurde. Darüber hinaus werden sie in einem bedarfsabhängigen Ordner in Dynamic Media Classic abgelegt. Der bedarfsabhängige Ordner wird nicht mit Experience Manager synchronisiert (Assets sind jedoch im Dynamic Media Classic-Inhaltsbrowser auffindbar).

Um Dynamic Media Classic für die Integration mit Experience Manager zu konfigurieren, müssen Sie die folgenden Schritte ausführen:

1. [Legen Sie eine Cloud-Konfiguration fest](#creating-a-cloud-configuration-for-scene). Dadurch wird die Zuordnung zwischen einem Dynamic Media Classic-Ordner und einem Assets-Ordner festlegt. Führen Sie diesen Schritt auch dann aus, wenn Sie nur eine unidirektionale Synchronisation (von Experience Manager Assets zu Dynamic Media Classic) wünschen.
1. [Aktivieren Sie den **Adobe CQ s7dam DAM Listener**](#enabling-the-adobe-cq-scene-dam-listener). Verwenden Sie dazu die [!UICONTROL OSGi]-Konsole.
1. Wenn Sie möchten, dass Experience Manager-Assets automatisch in Dynamic Media Classic hochgeladen werden, aktivieren Sie die Option und fügen Sie Dynamic Media Classic zum Workflow für DAM-Update-Assets hinzu. Außerdem können Sie manuell Assets hochladen.
1. Fügen Sie Dynamic Media Classic-Komponenten zum Sidekick hinzu. Auf diese Weise können Benutzer Dynamic Media Classic-Komponenten auf ihren Experience Manager-Seiten verwenden.
1. [Ordnen Sie die Konfiguration der Seite im Experience Manager zu](#enabling-scene-for-wcm). Dieser Schritt ist erforderlich, um alle Videovorgaben anzuzeigen, die Sie in Dynamic Media Classic erstellt haben. Er ist auch erforderlich, wenn Sie eine Veröffentlichung eines Assets von außerhalb des CQ-Zielordners in Dynamic Media Classic vornehmen müssen.

In diesem Abschnitt wird die Durchführung all dieser Schritte behandelt und es werden wichtige Beschränkungen aufgeführt.

### Funktionsweise der Synchronisierung zwischen Dynamic Media Classic und Experience Manager Assets {#how-synchronization-between-scene-and-aem-assets-works}

Beim Einrichten der Synchronisierung von Experience Manager Assets und Dynamic Media Classic müssen Sie Folgendes verstehen:

#### Hochladen von Experience Manager Assets in Dynamic Media Classic {#uploading-to-scene-from-aem-assets}

* Es gibt einen speziellen Synchronisierungsordner in Experience Manager für Dynamic Media Classic-Uploads.
* Uploads auf Dynamic Media Classic können automatisiert werden, wenn die digitalen Assets im vorgesehenen Synchronisierungsordner platziert werden.
* Die Ordner- und Unterordnerstruktur in Experience Manager wird in Dynamic Media Classic repliziert.

>[!NOTE]
>
>Experience Manager bettet alle Metadaten als XMP ein, bevor sie in Dynamic Media Classic hochgeladen werden, sodass alle Eigenschaften auf dem Metadatenknoten in Dynamic Media Classic als XMP verfügbar sind.

#### Bekannte Beschränkungen und Auswirkungen auf das Design {#known-limitations-and-design-implications}

Bei der Synchronisierung zwischen Experience Manager Assets und Dynamic Media Classic gibt es derzeit die folgenden Beschränkungen/Auswirkungen auf das Design:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Beschränkung/Auswirkung auf das Design</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>Ein spezieller Synchronisierungsordner (Ziel)</td> 
   <td>Für Dynamic Media Classic-Uploads darf pro Unternehmen nur ein spezieller Ordner in Experience Manager vorhanden sein. Sie können mehrere Konfigurationen erstellen, wenn Sie Zugriff auf mehr als ein Unternehmenskonto in Dynamic Media Classic benötigen.</td> 
  </tr> 
  <tr> 
   <td>Ordnerstruktur</td> 
   <td>Wenn Sie einen synchronisierten Ordner mit Assets löschen, werden alle Remote-Assets von Dynamic Media Classic gelöscht, der Ordner bleibt jedoch erhalten.</td> 
  </tr> 
  <tr> 
   <td>Ad-hoc-Ordner</td> 
   <td>Assets, die sich außerhalb des Zielordners befinden und manuell in Dynamic Media Classic im WCM hochgeladen werden, werden automatisch in einem separaten Ad-hoc-Ordner in Dynamic Media Classic abgelegt. Sie konfigurieren diese Funktion in der Cloud-Konfiguration in Experience Manager.</td> 
  </tr> 
  <tr> 
   <td>Gemischte Medien</td> 
   <td>Gemischte Mediensets werden in Experience Manager angezeigt, obwohl sie in Experience Manager nicht unterstützt werden.</td> 
  </tr> 
  <tr> 
   <td>PDFs</td> 
   <td>Generierte PDF-Dateien aus E-Katalogen in Dynamic Media Classic werden in den CQ-Zielordner importiert.</td> 
  </tr> 
  <tr> 
   <td>Aktualisierung der Benutzeroberfläche</td> 
   <td>Stellen Sie bei der Synchronisierung zwischen Experience Manager und Dynamic Media Classic sicher, dass Sie die Benutzeroberfläche aktualisieren, um Änderungen anzuzeigen. </td> 
  </tr> 
  <tr> 
   <td>Videominiaturansichten</td> 
   <td>Wenn Sie ein Video zur Kodierung über Dynamic Media Classic in Experience Manager Assets hochladen, kann es je nach Videoverarbeitungszeit einige Zeit dauern, bis die Videominiaturansichten und kodierten Videos in Experience Manager Assets verfügbar sind.</td> 
  </tr> 
  <tr> 
   <td>Zielunterordner</td> 
   <td><p>Wenn Sie Unterordner im Zielordner verwenden, verwenden Sie entweder eindeutige Namen für jedes Asset (unabhängig vom Speicherort) oder konfigurieren Sie Dynamic Media Classic (im Bereich "Einrichtung") so, dass Assets unabhängig vom Speicherort nicht überschrieben werden.</p> <p>Andernfalls werden Assets hochgeladen, die denselben Namen haben wie Assets, die in einen Dynamic Media Classic-Zielunterordner hochgeladen werden. Das Asset mit dem gleichen Namen im Zielordner wird jedoch gelöscht. </p> </td> 
  </tr> 
 </tbody> 
</table>

### Konfigurieren von Dynamic Media Classic-Servern {#configuring-scene-servers}

Wenn Sie Experience Manager hinter einem Proxy ausführen oder über spezielle Firewall-Einstellungen verfügen, müssen Sie die Hosts der verschiedenen Regionen explizit aktivieren. Server werden im Hinblick auf Inhalte in `/etc/cloudservices/scene7/endpoints` verwaltet und können bei Bedarf angepasst werden. Tippen Sie auf eine URL und bearbeiten Sie sie, um sie bei Bedarf zu ändern. In früheren Versionen von Experience Manager waren diese Werte hartkodiert.

Wenn Sie zu `/etc/cloudservices/scene7/endpoints.html`angezeigt, sehen Sie die aufgeführten Server (und können sie durch Klicken auf die URL bearbeiten):

![chlimage_1-296](assets/chlimage_1-296.png)

### Erstellen einer Cloud-Konfiguration für Dynamic Media Classic {#creating-a-cloud-configuration-for-scene}

Eine Cloud-Konfiguration definiert die Zuordnung zwischen einem Dynamic Media Classic-Ordner und einem Experience Manager Assets-Ordner. Sie muss für die Synchronisierung von Experience Manager Assets mit Dynamic Media Classic konfiguriert werden. Unter „Funktionsweise der Synchronisierung“ finden Sie weitere Informationen.

>[!CAUTION]
>
>Beim Importieren von Assets aus einem bestehenden Dynamic Media Classic-Unternehmenskonto kann es lange dauern, bis sie in Experience Manager angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic angeben, der nicht zu viele Assets enthält. Beispielsweise enthält der Stammordner häufig zu viele Assets.
>
>Wenn Sie die Integration testen möchten, verweisen Sie den Stammordner nur auf einen Unterordner und nicht auf das gesamte Unternehmen.

>[!NOTE]
>
>Sie können mehrere Konfigurationen verwenden: Eine Cloud-Konfiguration steht für einen Benutzer in einem Dynamic Media Classic-Unternehmen. Wenn Sie auf andere Dynamic Media Classic-Unternehmen oder -Benutzer zugreifen möchten, erstellen Sie mehrere Konfigurationen.

So konfigurieren Sie Experience Manager, um Assets in Dynamic Media Classic veröffentlichen zu können:

1. Tippen Sie auf das Symbol Experience Manager und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]** , um auf Adobe Dynamic Media Classic zuzugreifen.

1. Tippen **[!UICONTROL Jetzt konfigurieren]**.

   ![chlimage_1-297](assets/chlimage_1-297.png)

1. Geben Sie im Feld **[!UICONTROL Titel]** und optional im Feld **[!UICONTROL Name]** die entsprechenden Informationen ein. Tippen Sie auf **[!UICONTROL Erstellen]**.

   >[!NOTE]
   >
   >Beim Erstellen weiterer Konfigurationen wird das Feld **[!UICONTROL Übergeordnete Konfiguration]** angezeigt.
   >
   >Ändern Sie **nicht** die übergeordnete Konfiguration. Das Ändern der übergeordneten Konfiguration kann zum Scheitern der Integration führen.

1. Geben Sie die E-Mail-Adresse, das Kennwort und die Region Ihres Dynamic Media Classic-Kontos ein und tippen Sie auf **[!UICONTROL Verbindung zu Dynamic Media Classic herstellen]**. Sie sind nun mit dem Dynamic Media Classic-Server verbunden und das Dialogfeld wird mit weiteren Optionen erweitert.

1. Geben Sie den **[!UICONTROL Unternehmensnamen]** und das **[!UICONTROL Stammverzeichnis]** ein. Diese Informationen sind der veröffentlichte Server-Name zusammen mit einem beliebigen Pfad, den Sie angeben möchten. Wenn Sie den veröffentlichten Server-Namen nicht kennen, navigieren Sie in Dynamic Media Classic zu **[!UICONTROL Einstellungen > Anwendungseinstellungen]**.

   >[!NOTE]
   >
   >Das Dynamic Media Classic-Stammverzeichnis ist der Dynamic Media Classic-Ordner, mit dem Experience Manager eine Verbindung herstellt. Es kann auf einen spezifischen Ordner eingegrenzt werden.

   >[!CAUTION]
   >
   >Je nach Größe des Dynamic Media Classic-Ordners kann der Import eines Stammordners viel Zeit in Anspruch nehmen. Darüber hinaus können Dynamic Media Classic-Daten den Experience Manager-Speicher überschreiten. Stellen Sie sicher, dass Sie in den richtigen Ordner importieren. Der Import einer zu großen Menge von Daten kann zur Unterbrechung Ihres Systems führen.

   ![chlimage_1-298](assets/chlimage_1-298.png)

1. Klicken Sie auf **[!UICONTROL OK]**. Experience Manager speichert Ihre Konfiguration.

>[!NOTE]
>
>Wenn Sie eine erneute Verbindung herstellen:
>
>* Beim erneuten Herstellen einer Verbindung mit Dynamic Media Classic beim Veröffentlichen funktioniert das Zurücksetzen des Kennworts beim Veröffentlichen oder erneuten Verbinden nicht (kein Problem in der Autoreninstanz).
>* Wenn Sie Werte ändern, wie zum Beispiel Region und Unternehmensname, müssen Sie erneut eine Verbindung mit Dynamic Media Classic herstellen. Wenn Konfigurationsoptionen geändert, aber nicht gespeichert wurden, zeigt Experience Manager fälschlicherweise nach wie vor an, dass die Konfiguration gültig ist. Achten Sie darauf, erneut eine Verbindung herzustellen.
>


### Aktivieren des Adobe CQ Dynamic Media Classic DAM-Listeners {#enabling-the-adobe-cq-scene-dam-listener}

Aktivieren Sie den DAM-Listener für Adobe CQ Dynamic Media Classic, der standardmäßig deaktiviert ist.

So aktivieren Sie den DAM-Listener für Adobe CQ Dynamic Media Classic:

1. Tippen Sie auf [!UICONTROL Instrumente] Symbol und navigieren Sie dann zu **[!UICONTROL Vorgänge > Web-Konsole]**. Die Web-Konsole wird geöffnet.
1. Navigieren Sie zu **[!UICONTROL Adobe CQ Dynamic Media Classic DAM Listener]** und wählen Sie die **[!UICONTROL Aktiviert]** aktivieren.

   ![chlimage_1-299](assets/chlimage_1-299.png)

1. Tippen Sie auf **[!UICONTROL Speichern]**.

### Hinzufügen eines konfigurierbaren Timeouts zum Dynamic Media Classic-Upload-Workflow {#adding-configurable-timeout-to-scene-upload-workflow}

Wenn eine Experience Manager-Instanz so konfiguriert wird, dass die Videokodierung von Dynamic Media Classic verarbeitet wird, gibt es standardmäßig ein 35-minütiges Timeout zu jedem Upload-Auftrag. Um Videokodierungsaufträge mit potenziell längerer Dauer zu ermöglichen, können Sie diese Einstellung konfigurieren:

1. Navigieren Sie zu **http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl**.

   ![chlimage_1-300](assets/chlimage_1-300.png)

1. Ändern Sie die Zahl wie gewünscht im Feld **[!UICONTROL Zeitüberschreitung bei aktiven Aufträgen]**. Jede positive Zahl wird binnen Sekunden mit der Maßeinheit akzeptiert. Standardmäßig ist diese Zahl auf 2100 festgelegt.

   >[!NOTE]
   >
   >Best Practice: Bei den meisten Assets dauert das Übernehmen höchstens einige Minuten (beispielsweise bei Bildern). Erhöhen Sie in bestimmten Fällen, z. B. bei größeren Videos, den Timeout-Wert auf 7200 Sekunden (zwei Stunden), um eine lange Verarbeitungszeit zu ermöglichen. Andernfalls wird dieser Dynamic Media Classic-Upload-Auftrag als **[!UICONTROL UploadFailed]** in den JCR-Metadaten.

1. Tippen Sie auf **[!UICONTROL Speichern]**.

### Autouploading von Experience Manager Assets {#autouploading-from-aem-assets}

Ab Experience Manager 6.3.2 ist Experience Manager Assets jetzt für Sie konfiguriert, sodass alle digitalen Assets, die Sie in den Digital Asset Manager hochladen, automatisch in Dynamic Media Classic aktualisiert werden, wenn sich die Assets in einem CQ-Zielordner befinden.

Wenn ein Asset zu Experience Manager Assets hinzugefügt wird, wird es automatisch hochgeladen und in Dynamic Media Classic veröffentlicht.

>[!NOTE]
>
>Die maximale Dateigröße für das automatische Hochladen von Experience Manager Assets in Dynamic Media Classic beträgt 500 MB.

So konfigurieren Sie die automatische Ladevorgänge von Experience Manager Assets:

1. Tippen Sie auf das Symbol Experience Manager und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]** Tippen Sie dann unter der Überschrift &quot;Dynamic Media&quot;unter &quot;Verfügbare Konfigurationen&quot;auf **[!UICONTROL dms7 (Dynamic Media]**)
1. Tippen Sie auf **[!UICONTROL Erweitert]** auswählen, wählen Sie die **[!UICONTROL Automatisches Hochladen aktivieren]** Kontrollkästchen aktivieren und dann auf **[!UICONTROL OK]**. Jetzt müssen Sie den DAM-Asset-Workflow so konfigurieren, dass er das Hochladen in Dynamic Media Classic umfasst.

   >[!NOTE]
   >
   >Unter [Konfigurieren des Status (veröffentlicht/unveröffentlicht) der auf Dynamic Media Classic gepushten Assets](#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) erhalten Sie Informationen zum Pushen von Assets auf Dynamic Media Classic im unveröffentlichten Status.

   ![screen_shot_2018-03-15at52501pm](assets/screen_shot_2018-03-15at52501pm.jpg)

1. Navigieren Sie zurück zur Begrüßungsseite des Experience Managers und tippen Sie auf **[!UICONTROL Workflows]**. Doppelklicken Sie auf den Workflow **DAM-Update-Asset**, um ihn zu öffnen.
1. Navigieren Sie im Sidekick zu den **[!UICONTROL Workflow]**-Komponenten und wählen Sie **[!UICONTROL Dynamic Media Classic]** aus. Ziehen **[!UICONTROL Dynamic Media Classic]** zum Workflow hinzu und tippen Sie auf **[!UICONTROL Speichern]**. Assets, die im Zielordner zu Experience Manager Assets hinzugefügt werden, werden automatisch in Dynamic Media Classic hochgeladen.

   ![chlimage_1-301](assets/chlimage_1-301.png)

   >[!NOTE]
   >
   >* Beim Hinzufügen von Assets nach der Automatisierung werden diese nicht in Dynamic Media Classic hochgeladen, wenn sie sich nicht im CQ-Zielordner befinden.
   >* Experience Manager bettet alle Metadaten als XMP ein, bevor sie in Dynamic Media Classic hochgeladen werden, sodass alle Eigenschaften auf dem Metadatenknoten in Dynamic Media Classic als XMP verfügbar sind.


### Konfigurieren des Status (veröffentlicht/unveröffentlicht) der an Dynamic Media Classic gepushten Assets {#configuring-the-state-published-unpublished-of-assets-pushed-to-scene}

Wenn Sie Assets von Experience Manager Assets auf Dynamic Media Classic pushen, können Sie sie entweder automatisch veröffentlichen (Standardverhalten) oder im unveröffentlichten Status auf Dynamic Media Classic pushen.

Es ist möglich, dass Sie Assets nicht sofort in Dynamic Media Classic veröffentlichen möchten, wenn Sie sie vor der Live-Schaltung in einer Staging-Umgebung testen möchten. Sie können Experience Manager mit der sicheren Testumgebung von Dynamic Media Classic verwenden, um Assets direkt aus Assets in einem unveröffentlichten Status auf Dynamic Media Classic zu pushen.

Dynamic Media Classic-Assets bleiben über eine sichere Vorschau verfügbar. Nur wenn Assets in Experience Manager veröffentlicht werden, werden die Dynamic Media Classic-Assets auch in der Produktion live geschaltet.

Wenn Sie Assets sofort nach dem Pushen auf Dynamic Media Classic veröffentlichen möchten, müssen Sie keine Optionen konfigurieren. Dies ist das Standardverhalten.

Wenn Sie jedoch nicht möchten, dass Assets, die auf Dynamic Media Classic gepusht werden, automatisch veröffentlicht werden, wird in diesem Abschnitt beschrieben, wie Sie Experience Manager und Dynamic Media Classic so konfigurieren, dass diese Funktion ausgeführt wird.

#### Voraussetzungen für das Pushen von unveröffentlichten Assets auf Dynamic Media Classic {#prerequisites-to-push-assets-to-scene-unpublished}

Bevor Sie Assets auf Dynamic Media Classic pushen können, ohne sie zu veröffentlichen, müssen Sie Folgendes einrichten:

1. [Verwenden Sie die Admin Console, um einen Support-Fall zu erstellen.](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Stellen Sie in Ihrem Support-Fall sicher, dass die sichere Vorschau für Ihr Dynamic Media Classic-Konto aktiviert ist.
1. Folgen Sie den Anweisungen unter [Einrichten einer sicheren Vorschau für Ihr Dynamic Media Classic-Konto.](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html#upload-publish)

Diese Schritte sind die gleichen, die Sie ausführen würden, um ein sicheres Test-Setup in Dynamic Media Classic zu erstellen.

>[!NOTE]
>
>Wenn Ihre Installationsumgebung ein UNIX®-64-Bit-Betriebssystem ist, finden Sie weitere Konfigurationsoptionen, die Sie festlegen müssen, unter [https://helpx.adobe.com/de/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html](https://helpx.adobe.com/de/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

#### Bekannte Beschränkungen für das Pushen von Assets im nicht veröffentlichten Status  {#known-limitations-for-pushing-assets-in-unpublished-state}

Beachten Sie die folgenden Beschränkungen, wenn Sie diese Funktion verwenden:

* Die Versionskontrolle wird nicht unterstützt.
* Wenn ein Asset bereits in Experience Manager veröffentlicht ist und eine Folgeversion erstellt wurde, wird diese neue Version sofort veröffentlicht und tatsächlich in der Produktion eingesetzt. Die Veröffentlichung zusammen mit der Aktivierung funktioniert nur bei der ersten Veröffentlichung eines Assets.

>[!NOTE]
>
>Wenn Sie Assets sofort veröffentlichen möchten, empfiehlt es sich, die Option **[!UICONTROL Sichere Vorschau aktivieren]** auf **[!UICONTROL Sofort]** eingestellt zu lassen und die Funktion **[!UICONTROL Automatisches Hochladen aktivieren]** zu verwenden.

### Festlegen des Status von Assets, die an Dynamic Media Classic gesendet werden, als unveröffentlicht {#setting-the-state-of-assets-pushed-to-scene-as-unpublished}

>[!NOTE]
>
>Wenn ein Benutzer das Asset in Experience Manager veröffentlicht, wird automatisch das S7-Asset in der Produktion/im Live-Asset aktiviert (das Asset befindet sich dann nicht mehr in der sicheren Vorschau/im unveröffentlichten Status).

So legen Sie den Status der auf Dynamic Media Classic gepushten Assets auf „unveröffentlicht“ fest:

1. Tippen Sie auf das Symbol Experience Manager und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]** Tippen Sie auf **[!UICONTROL Dynamic Media Classic]** und wählen Sie Ihre Konfiguration in Dynamic Media Classic aus.
1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert.]** Wählen Sie im Dropdown-Menü **[!UICONTROL Sichere Ansicht aktivieren]** die Option **[!UICONTROL Bei AEM-Veröffentlichung/-Aktivierung]** aus, um Assets ohne Veröffentlichung auf Dynamic Media Classic zu pushen. (Standardmäßig ist dieser Wert auf **[!UICONTROL Sofort]** eingestellt, sodass Dynamic Media Classic-Assets sofort veröffentlicht werden.)

   In der [Dynamic Media Classic-Dokumentation](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html#upload-publish) finden Sie weitere Informationen zum Testen von Assets vor ihrer Veröffentlichung.

   ![chlimage_1-302](assets/chlimage_1-302.png)

1. Tippen Sie auf **[!UICONTROL OK]**.

Die Aktivierung der sicheren Ansicht bedeutet, dass Ihre Assets unveröffentlicht auf den sicheren Vorschauserver gepusht werden.

Um herauszufinden, ob Sichere Vorschau aktiviert ist, navigieren Sie auf einer Seite in Experience Manager zu einer Dynamic Media Classic-Komponente. Tippen Sie auf **[!UICONTROL Bearbeiten]**. Der sichere Vorschauserver ist in der URL des Assets aufgeführt. Nach der Veröffentlichung in Experience Manager wird die Server-Domain im Dateiverweis von der Vorschau-URL in die Produktions-URL aktualisiert.

### Aktivieren von Dynamic Media Classic für WCM {#enabling-scene-for-wcm}

Die Aktivierung von Dynamic Media Classic für WCM ist aus zwei Gründen erforderlich:

* Sie aktiviert die Dropdown-Liste der universellen Videoprofile für die Seitenbearbeitung. Ohne diese Liste ist die Dropdown-Liste **[!UICONTROL Universelle Videovorgabe]** leer und kann nicht festgelegt werden.
* Falls sich ein digitales Asset nicht im Zielordner befindet, können Sie das Asset in Dynamic Media Classic hochladen, wenn Sie Dynamic Media Classic für diese Seite in den Seiteneigenschaften aktivieren. Ziehen Sie das Asset dann auf eine Dynamic Media Classic-Komponente. Es gelten die normalen Vererbungsregeln (die untergeordneten Seiten übernehmen also die Konfiguration von der übergeordneten Seite).

Beim Aktivieren von Dynamic Media Classic für WCM gelten wie bei anderen Konfigurationen Vererbungsregeln. Sie können Dynamic Media Classic für WCM entweder in der Touch-optimierten oder in der klassischen Benutzeroberfläche aktivieren.

#### Aktivieren von Dynamic Media Classic für WCM in der Touch-optimierten Benutzeroberfläche {#enabling-scene-for-wcm-in-the-touch-optimized-user-interface}

So aktivieren Sie Dynamic Media Classic für WCM in der Touch-optimierten Benutzeroberfläche:

1. Tippen Sie auf das Symbol Experience Manager und navigieren Sie zu **[!UICONTROL Sites]** und dann die Stammseite Ihrer Website (nicht sprachspezifisch).

1. Wählen Sie in der Symbolleiste die [!UICONTROL settings] Symbol und tippen Sie auf **[!UICONTROL Eigenschaften öffnen]**.

1. Tippen **[!UICONTROL Cloud Services]** und tippen **[!UICONTROL Konfiguration hinzufügen]** und wählen Sie **[!UICONTROL Dynamic Media Classic]**.
1. Im **[!UICONTROL Adobe Dynamic Media Classic]** Dropdownliste, wählen Sie die gewünschte Konfiguration aus und tippen Sie auf **[!UICONTROL OK]**.

   ![chlimage_1-303](assets/chlimage_1-303.png)

   Videovorgaben aus dieser Dynamic Media Classic-Konfiguration stehen für die Verwendung in Experience Manager mit der Dynamic Media Classic-Videokomponente auf dieser Seite und auf untergeordneten Seiten zur Verfügung.

#### Aktivieren von Dynamic Media Classic für WCM in der klassischen Benutzeroberfläche {#enabling-scene-for-wcm-in-the-classic-user-interface}

So aktivieren Sie Dynamic Media Classic für WCM in der klassischen Benutzeroberfläche:

1. Tippen Sie in Experience Manager auf **[!UICONTROL Websites]** und navigieren Sie zur Stammseite Ihrer Website (nicht sprachspezifisch).

1. Tippen Sie im Sidekick auf die **[!UICONTROL Seite]** Symbol und tippen Sie auf **[!UICONTROL Seiteneigenschaften]**.

1. Tippen **[!UICONTROL Cloud Services > Dienste hinzufügen > Dynamic Media Classic]**.
1. Im **[!UICONTROL Adobe Dynamic Media Classic]** Dropdownliste, wählen Sie die gewünschte Konfiguration aus und tippen Sie auf **[!UICONTROL OK]**.

   Videovorgaben aus dieser Dynamic Media Classic-Konfiguration stehen für die Verwendung in Experience Manager mit der Dynamic Media Classic-Videokomponente auf dieser Seite und auf untergeordneten Seiten zur Verfügung.

### Konfigurieren einer Standardkonfiguration {#configuring-a-default-configuration}

Wenn Sie mehrere Dynamic Media Classic-Konfigurationen haben, können Sie eine davon als Standard für den Dynamic Media Classic-Inhaltsbrowser festlegen.

Es kann immer nur eine Dynamic Media Classic-Konfiguration als Standard markiert werden. Die Standardkonfiguration umfasst die Unternehmens-Assets, die standardmäßig im Dynamic Media Classic-Inhaltsbrowser angezeigt werden.

Sie können die Standardkonfiguration wie folgt konfigurieren:

1. Tippen Sie auf das Symbol Experience Manager und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]** Tippen Sie auf **[!UICONTROL Dynamic Media Classic]** und wählen Sie Ihre Konfiguration in Dynamic Media Classic aus.
1. Um die Konfiguration zu öffnen, tippen Sie auf **[!UICONTROL Bearbeiten]**.

1. Aktivieren Sie auf der Registerkarte **[!UICONTROL Allgemein]** das Kontrollkästchen **[!UICONTROL Standardkonfiguration]**, um sie als Standardunternehmen und Stammverzeichnis festzulegen, die dann im Dynamic Media Classic-Inhaltsbrowser angezeigt werden.

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!NOTE]
   >
   >Wenn es nur eine Konfiguration gibt, hat die Auswahl des Kontrollkästchens **[!UICONTROL Standardkonfiguration]** keinerlei Wirkung.

### Konfigurieren des Ad-hoc-Ordners {#configuring-the-ad-hoc-folder}

Sie können den Ordner konfigurieren, in den Assets in Dynamic Media Classic hochgeladen werden, wenn sich das Asset nicht im CQ-Zielordner befindet. Siehe „Veröffentlichen von Assets von außerhalb des CQ-Zielordners“.

Sie können den Ad-hoc-Ordner wie folgt konfigurieren:

1. Tippen Sie auf das Symbol Experience Manager und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]** Tippen Sie auf **[!UICONTROL Dynamic Media Classic]** und wählen Sie Ihre Konfiguration in Dynamic Media Classic aus.
1. Um die Konfiguration zu öffnen, tippen Sie auf **[!UICONTROL Bearbeiten]**.

1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert.]** Im Feld **[!UICONTROL Ad-hoc-Ordner]** können Sie den **Ad-hoc**-Ordner verändern. Standardmäßig handelt es sich um **Firmenname/CQ5_adhoc**.

   ![chlimage_1-305](assets/chlimage_1-305.png)

### Konfigurieren der universellen Vorgaben {#configuring-universal-presets}

Informationen zur Konfiguration der universellen Vorgaben für die Videokomponente finden Sie unter [Video](/help/assets/s7-video.md).

## Unterstützung von MIME-typbasierten Assets/Dynamic Media Classic-Upload-Auftragsparametern {#enabling-mime-type-based-assets-scene-upload-job-parameter-support}

Sie können konfigurierbare Auftragsparameter für Dynamic Media Classic-Uploads aktivieren, die durch die Synchronisierung von Digital Asset Manager-/Dynamic Media Classic-Assets ausgelöst werden.

Insbesondere konfigurieren Sie hier das vom MIME-Typ akzeptierte Dateiformat im Bereich „OSGi“ (Open Service Gateway initiative) des Bedienfelds für die Konfiguration der Experience Manager-Web-Konsole. Dann können Sie die einzelnen Upload-Auftragsparameter konfigurieren, die für jeden MIME-Typ im JCR (Java™ Content Repository) verwendet werden.

**So aktivieren Sie MIME-typbasierte Assets:**

1. Tippen Sie auf das Symbol Experience Manager und navigieren Sie zu **[!UICONTROL Tools > Vorgänge > Web-Konsole]**.
1. Im Konfigurationsbereich der Adobe Experience Manager Web Console finden Sie im **[!UICONTROL OSGi]** Menü, tippen **[!UICONTROL Konfiguration]**.
1. Suchen Sie in der Spalte &quot;Name&quot;nach und tippen Sie auf **[!UICONTROL Adobe CQ Dynamic Media Classic Asset MIME type Service]** , um die Konfiguration zu bearbeiten.
1. Tippen Sie im Bereich MIME-Typ-Zuordnung auf ein beliebiges Pluszeichen (+), um einen MIME-Typ hinzuzufügen.

   Siehe [Unterstützte MIME-Typen](/help/assets/assets-formats.md#supported-mime-types).

1. Geben Sie im Textfeld den neuen Namen des MIME-Typs ein.

   Sie können beispielsweise `<file_extension>=<mime_type>` wie in `EPS=application/postscript` oder `PSD=image/vnd.adobe.photoshop` eingeben.

1. Tippen Sie in der rechten unteren Ecke des Konfigurationsfensters auf **[!UICONTROL Speichern]**.
1. Kehren Sie zu Experience Manager zurück und tippen Sie in der linken Leiste auf CRXDE Lite.
1. Navigieren Sie auf der Seite „CRXDE Lite“ in der linken Leiste zu `/etc/cloudservices/scene7/<environment>` (und ersetzen Sie `<environment>` durch den tatsächlichen Namen).
1. Erweitern Sie `<environment>` (und ersetzen Sie `<environment>` durch den tatsächlichen Namen), um den Knoten `mimeTypes` anzuzeigen.
1. Tippen Sie auf den soeben hinzugefügten mimeType .

   Beispiel: `mimeTypes > application_postscript` oder `mimeTypes > image_vnd.adobe.photoshop`

1. Tippen Sie rechts auf der Seite &quot;CRXDE Lite&quot;auf die **[!UICONTROL Eigenschaften]** Registerkarte.
1. Geben Sie einen Auftragsparameter für einen Dynamic Media Classic-Upload im Wertfeld **[!UICONTROL jobParam]** an.

   Beispiel: `psprocess="rasterize"&psresolution=120`. 

   Informationen zu weiteren Upload-Auftragsparametern, die Sie verwenden können, finden Sie in der [Adobe Dynamic Media Classic Image Production System-API](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-overview.html?lang=de).

   >[!NOTE]
   >
   >Wenn Sie PSD-Dateien hochladen und als Vorlagen mit Ebenenextraktionen verarbeiten möchten, geben Sie Folgendes im Wertfeld **[!UICONTROL jobParam]** ein:
   >
   >`process=MaintainLayers&layerNaming=AppendName&createTemplate=true`
   >
   >Achten Sie darauf, dass Ihre PSD-Datei über „Ebenen“ verfügt. Wenn es sich ausschließlich um ein Bild oder um ein Bild mit Maske handelt, wird es nur als Bild verarbeitet, da keine Ebenen zur Verarbeitung vorhanden sind.

1. Tippen Sie oben links auf der Seite &quot;CRXDE Lite&quot;auf **[!UICONTROL Alle speichern]**.

## Fehlerbehebung bei der Integration von Dynamic Media Classic und Experience Managern {#troubleshooting-scene-and-aem-integration}

Wenn Sie Probleme bei der Integration von Experience Manager mit Dynamic Media Classic haben, finden Sie in den folgenden Lösungsszenarien weitere Informationen.

**Wenn die Veröffentlichung digitaler Assets in Dynamic Media Classic fehlschlägt:**

* Überprüfen Sie, ob sich das Asset, das Sie hochladen möchten, im **[!UICONTROL CQ-Ziel]** Ordner (Sie geben diesen Ordner in der Dynamic Media Classic-Cloud-Konfiguration an).
* Ist dies nicht der Fall, müssen Sie die Cloud-Konfiguration in **[!UICONTROL Seiteneigenschaften]** für diese Seite, um das Hochladen in die **[!UICONTROL CQ-Adhoc]** Ordner.

* Überprüfen Sie die Protokolle auf etwaige Informationen.

**Wenn Ihre Videovorgaben nicht angezeigt werden:**

* Stellen Sie sicher, dass Sie die Cloud-Konfiguration dieser Seite durch die **[!UICONTROL Seiteneigenschaften]** konfiguriert haben. Videovorgaben sind in der Dynamic Media Classic-Videokomponente verfügbar.

**Wenn Ihre Video-Assets nicht in Experience Manager wiedergegeben werden:**

* Stellen Sie sicher, dass Sie die richtige Videokomponente verwendet haben. Die Dynamic Media Classic-Videokomponente unterscheidet sich von der Foundation-Videokomponente. Siehe [Foundation-Videokomponente im Vergleich zur Dynamic Media Classic-Videokomponente](/help/assets/s7-video.md).

**Wenn neue oder geänderte Assets in Experience Manager nicht automatisch in Dynamic Media Classic hochgeladen werden:**

* Stellen Sie sicher, dass sich die Assets im CQ-Zielordner befinden. Nur Assets, die sich im CQ-Zielordner befinden, werden automatisch aktualisiert (vorausgesetzt, Sie haben Experience Manager Assets für das automatische Hochladen von Assets konfiguriert).
* Stellen Sie sicher, dass Sie die Cloud-Services-Konfiguration konfiguriert haben, um das automatische Hochladen zu aktivieren, und dass Sie den DAM-Asset-Workflow aktualisiert und gespeichert haben, sodass er das Hochladen in Dynamic Media Classic umfasst.
* Stellen Sie beim Hochladen eines Bildes in einen Unterordner des Dynamic Media Classic-Zielordners sicher, dass Sie eine der folgenden Aktionen ausführen:

   * Stellen Sie sicher, dass die Namen aller Assets unabhängig von ihrem Speicherort eindeutig sind. Andernfalls wird das Asset im Hauptzielordner gelöscht und es verbleibt nur das Asset im Unterordner.
   * Ändern Sie, wie Dynamic Media Classic Assets im Bereich „Einstellungen“ des Dynamic Media Classic-Kontos überschreibt. Legen Sie nicht fest, dass Dynamic Media Classic Assets unabhängig vom Speicherort überschreibt, wenn Sie Assets mit dem gleichen Namen in Unterordnern verwenden.

**Wenn Ihre gelöschten Assets oder Ordner nicht zwischen Dynamic Media Classic und Experience Manager synchronisiert werden:**

* In Experience Manager Assets gelöschte Assets und Ordner werden weiterhin im synchronisierten Ordner in Dynamic Media Classic angezeigt. Löschen Sie sie manuell.

**Wenn der Video-Upload fehlschlägt**

* Wenn Ihr Video-Upload fehlschlägt und Sie Experience Manager verwenden, um Videos über die Dynamic Media Classic-Integration zu kodieren, lesen Sie [Hinzufügen eines konfigurierbaren Timeouts zum Dynamic Media Classic-Upload-Workflow](#adding-configurable-timeout-to-scene-upload-workflow).

>[!CAUTION]
>
>Beim Importieren von Assets aus einem bestehenden Dynamic Media Classic-Unternehmenskonto kann es lange dauern, bis sie in Experience Manager angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic angeben, der nicht über zu viele Assets verfügt (z. B. hat der Stammordner häufig zu viele Assets).
>
>Wenn Sie die Integration testen möchten, verweisen Sie den Stammordner nur auf einen Unterordner und nicht auf das gesamte Unternehmen.
