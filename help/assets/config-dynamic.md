---
title: Konfigurieren von Dynamic Media – Hybridmodus
seo-title: Konfigurieren von Dynamic Media – Hybridmodus
description: Erfahren Sie mehr über die Konfiguration von Dynamic Media – Hybridmodus.
seo-description: Erfahren Sie mehr über die Konfiguration von Dynamic Media – Hybridmodus.
uuid: de88f68f-4697-4ff0-8008-3ae6a4684a84
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 821eb27e-67c9-4589-9196-30dacb84fa59
exl-id: 1e122f97-ac37-44f5-a1cd-bf53ffda6f5b
feature: Konfiguration,Hybridmodus
role: Admin,User,Developer
source-git-commit: 9bd173e99c2bbedc77afb11b4c1eac423c62ef30
workflow-type: tm+mt
source-wordcount: '7796'
ht-degree: 56%

---

# Konfigurieren von Dynamic Media – Hybridmodus {#configuring-dynamic-media-hybrid-mode}

Dynamic Media - Hybrid muss aktiviert und für die Verwendung konfiguriert werden. Je nach Anwendungsfall verfügt Dynamic Media über mehrere [unterstützte Konfigurationen](#supported-dynamic-media-configurations).

>[!NOTE]
>
>Wenn Sie Dynamic Media im Scene7-Modus konfigurieren und ausführen möchten, finden Sie weitere Informationen unter [Konfigurieren von Dynamic Media – Scene7-Modus](config-dms7.md).
>
>Wenn Sie Dynamic Media im Hybridmodus konfigurieren und ausführen möchten, folgen Sie den Anweisungen auf dieser Seite.

Informieren Sie sich über die Verwendung von [Videos](video.md) in Dynamic Media.

Wenn Sie Adobe Experience Manager für unterschiedliche Umgebungen eingerichtet haben (z. B. je eine Instanz für die Entwicklung, das Staging und die Live-Produktion), müssen Sie Dynamic Media Cloud Services für jede Umgebung konfigurieren.

Falls Probleme mit Ihrer Dynamic Media-Konfiguration auftreten, sind die Protokolldateien für die dynamischen Medien ein wichtiger Ort, um Informationen zu erhalten. Sie werden automatisch installiert, wenn Sie Dynamic Media aktivieren:

* `s7access.log`
* `ImageServing.log`

Sie werden unter [Überwachung und Wartung Ihrer AEM-Instanz](/help/sites-deploying/monitoring-and-maintaining.md) dokumentiert.

Die hybride Veröffentlichung und Bereitstellung ist eine Kernfunktion der Erweiterung Dynamic Media für Adobe Experience Manager. Mit der Hybrid-Veröffentlichung können Sie Dynamic Media-Assets wie Bilder, Sets und Videos aus der Cloud und nicht aus den AEM Veröffentlichungsknoten bereitstellen.

Andere Inhalte, z. B. Dynamic Media-Viewer, Seiten von Websites und statischer Inhalt, werden weiterhin über die AEM-Veröffentlichungsknoten bereitgestellt.

Wenn Sie Dynamic Media-Kunde sind, müssen Sie Hybridlieferungen als Bereitstellungsmechanismus für alle Dynamic Media-Inhalte verwenden.

## Hybride Veröffentlichungsarchitektur für Videos {#hybrid-publishing-architecture-for-videos}

![chlimage_1-506](assets/chlimage_1-506.png)

## Hybride Veröffentlichungsarchitektur für Bilder {#hybrid-publishing-architecture-for-images}

![chlimage_1-507](assets/chlimage_1-507.png)

## Unterstützte Dynamic Media-Konfigurationen {#supported-dynamic-media-configurations}

In den folgenden Konfigurationsaufgaben werden die hier angegebenen Begriffe verwendet:

| **Begriff** | **Dynamic Media aktiviert** | **Beschreibung** |
|---|---|---|
| AEM Autorenknoten | Weißes Häkchen in einem grünen Kreis | Der Autorknoten, den Sie On-Premise oder über Managed Services bereitstellen. |
| Veröffentlichungsknoten AEM | Weißes X in einem roten Quadrat. | Der Veröffentlichungsknoten, den Sie On-Premise oder über Managed Services bereitstellen. |
| Veröffentlichungsknoten des Bilddienstes | Weißes Häkchen in einem grünen Kreis. | Der Veröffentlichungsknoten, den Sie in Rechenzentren ausführen, die von Adobe verwaltet werden. Bezieht sich auf die Bilddienst-URL. |

Sie können Dynamic Media nur für Bilder, nur für Video oder sowohl für Bilder als auch für Video implementieren. Die Schritte zum Konfigurieren von Dynamic Media für Ihr jeweiliges Szenario können Sie in der folgenden Tabelle ermitteln.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Szenario</strong></td> 
   <td><strong>Funktionsweise</strong></td> 
   <td><strong>Konfigurationsschritte</strong></td> 
  </tr> 
  <tr> 
   <td>NUR Bilder in Produktion bereitstellen</td> 
   <td>Bilder werden über Server in den weltweiten Datenzentren von Adobe bereitgestellt und dann per CDN zwischengespeichert, um eine skalierbare Leistung und globale Reichweite zu erzielen.</td> 
   <td> 
    <ol> 
     <li>Aktivieren Sie auf dem AEM-<strong>Autorknoten</strong> die Option für <a href="#enabling-dynamic-media">dynamische Medien</a>.</li> 
     <li>Konfigurieren Sie die Bildbearbeitung unter <a href="#configuring-dynamic-media-cloud-services">Dynamic Media Cloud Services</a>.</li> 
     <li><a href="#configuring-image-replication">Konfigurieren Sie die Bildreplikation</a>.</li> 
     <li><a href="#replicating-catalog-settings">Replizieren Sie Katalogeinstellungen</a>.</li> 
     <li><a href="#replicating-viewer-presets">Replizieren Sie Viewer-Vorgaben</a>.</li> 
     <li><a href="#using-default-asset-filters-for-replication">Verwenden Sie Asset-Standardfilter für die Replikation</a>.</li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">Konfigurieren Sie Dynamic Media-Bildserver-Einstellungen</a>.</li> 
     <li><a href="#delivering-assets">Stellen Sie Assets bereit</a>.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>NUR Bilder in der Phase vor der Produktion bereitstellen (Entwicklung, QE, Bühne etc.)</td> 
   <td>Bilder werden über den AEM-Veröffentlichungsknoten bereitgestellt. Da bei diesem Szenario nur minimaler Datenverkehr anfällt, müssen keine Bilder für das Datenzentrum von Adobe bereitgestellt werden. Ein weiterer Vorteil ist, dass Sie damit die Möglichkeit erhalten, vor Beginn der Produktion eine sichere Vorschau des Inhalts anzuzeigen</td> 
   <td> 
    <ol> 
     <li>Aktivieren Sie auf dem AEM-<strong>Autorknoten</strong> die Option für <a href="#enabling-dynamic-media">dynamische Medien</a>.</li> 
     <li>Aktivieren Sie auf AEM Knoten <strong>publish</strong> <a href="#enabling-dynamic-media">dynamische Medien</a>.</li> 
     <li><a href="#replicating-viewer-presets">Replizieren Sie Viewer-Vorgaben</a>.</li> 
     <li>Richten Sie <a href="#setting-up-asset-filters-for-imaging-in-non-production-deployments">Asset-Filter für nicht für die Produktion bestimmte Bilder</a> ein.</li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">Konfigurieren Sie Dynamic Media-Bildserver-Einstellungen.</a></li> 
     <li><a href="#delivering-assets">Stellen Sie Assets bereit.</a></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>NUR Videos in allen Umgebungen bereitstellen (Produktion, Entwicklung, QE, Bühne usw.)</td> 
   <td>Videos werden vom CDN für skalierbare Leistung und eine globale Reichweite bereitgestellt und zwischengespeichert. Das Video-Posterbild (Miniaturansicht des Videos, das vor der Initiierung der Wiedergabe angezeigt wird) wird von der AEM-Veröffentlichungsinstanz bereitgestellt.</td> 
   <td> 
    <ol> 
     <li>Aktivieren Sie auf dem AEM-<strong>Autorknoten</strong> die Option für <a href="#enabling-dynamic-media">dynamische Medien</a>.</li> 
     <li>Aktivieren Sie auf dem AEM-<strong>Veröffentlichungsknoten</strong> die Option für <a href="#enabling-dynamic-media">dynamische Medien</a> (über die Veröffentlichungsinstanz werden das Video-Posterbild und die Metadaten für die Videowiedergabe bereitgestellt).</li> 
     <li>Konfigurieren Sie Videos unter <a href="#configuring-dynamic-media-cloud-services">Dynamic Media Cloud Services</a>.</li> 
     <li><a href="#replicating-viewer-presets">Replizieren Sie Viewer-Vorgaben</a>.</li> 
     <li>Richten Sie <a href="#setting-up-asset-filters-for-video-only-deployments">Asset-Filter für Videos</a> ein.</li> 
     <li><a href="#delivering-assets">Stellen Sie Assets bereit.</a></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Bilder UND Videos in Produktion bereitstellen</td> 
   <td><p>Videos werden vom CDN für skalierbare Leistung und eine globale Reichweite bereitgestellt und zwischengespeichert. Bilder und Video-Posterbilder werden über Server in den weltweiten Datenzentren von Adobe bereitgestellt und dann per CDN zwischengespeichert, um eine skalierbare Leistung und globale Reichweite zu erzielen.</p> <p>Informationen zur Einrichtung für Bilder oder Videos in der Phase vor der Produktion finden Sie in den obigen Abschnitten. </p> </td> 
   <td> 
    <ol> 
     <li>Aktivieren Sie auf dem AEM-<strong>Autorknoten</strong> die Option für <a href="#enabling-dynamic-media">dynamische Medien</a>.</li> 
     <li>Konfigurieren Sie Videos unter <a href="#configuring-dynamic-media-cloud-services">Dynamic Media Cloud Services</a>.</li> 
     <li>Konfigurieren Sie die Bildbearbeitung unter <a href="#configuring-dynamic-media-cloud-services">Dynamic Media Cloud Services</a>.</li> 
     <li><a href="#configuring-image-replication">Konfigurieren Sie die Bildreplikation</a>.</li> 
     <li><a href="#replicating-catalog-settings">Replizieren Sie Katalogeinstellungen</a>.</li> 
     <li><a href="#replicating-viewer-presets">Replizieren Sie Viewer-Vorgaben</a>.</li> 
     <li><a href="#using-default-asset-filters-for-replication">Verwenden Sie Asset-Standardfilter für die Replikation.</a></li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">Konfigurieren Sie Dynamic Media-Bildserver-Einstellungen.</a></li> 
     <li><a href="#delivering-assets">Stellen Sie Assets bereit.</a></li> 
    </ol> </td> 
  </tr> 
 </tbody> 
</table>

## Aktivieren von Dynamic Media {#enabling-dynamic-media}

[Dynamic Media](https://www.adobe.com/de/solutions/web-experience-management/dynamic-media.html) ist standardmäßig deaktiviert. Um die Funktionen von Dynamic Media nutzen zu können, müssen Sie Dynamic Media im Ausführungsmodus **[!UICONTROL dynamicmedia]** aktivieren, wie Sie es beispielsweise im Ausführungsmodus **[!UICONTROL publish]** tun würden. Prüfen Sie vor dem Aktivieren die [technischen Anforderungen](/help/sites-deploying/technical-requirements.md#requirements-for-aem-dynamic-media-add-on).

>[!NOTE]
>
>Durch das Aktivieren von Dynamic Media per Ausführungsmodus wird die Funktionalität in AEM 6.1 und AEM 6.0 für die Teile ersetzt, für die Sie Dynamic Media aktiviert haben, indem das Flag **[!UICONTROL dynamicMediaEnabled]** auf **[!UICONTROL true]** festgelegt wird. Dieses Flag hat in AEM 6.2 und höher keine Funktion. Außerdem ist es nicht erforderlich, den Schnellstartvorgang neu zu starten, um Dynamic Media zu aktivieren.

Durch die Aktivierung von Dynamic Media sind die Dynamic Media-Funktionen in der Benutzeroberfläche verfügbar. Jedes hochgeladene Bild-Asset erhält ein `cqdam.pyramid.tiff`-Ausgabeformat, das für die schnelle Bereitstellung dynamischer Bilddarstellungen verwendet wird. Diese PTIFF-Dateien bieten erhebliche Vorteile, z. B.: 1) die Möglichkeit, nur ein einziges Übergeordnetes Bild zu verwalten und unendliche Ausgabeformate ohne zusätzlichen Speicher zu generieren und 2) die Möglichkeit, interaktive Visualisierungen wie Zoom, Schwenken, Drehen usw. zu verwenden.

Wenn Sie Dynamic Media Classic in AEM verwenden möchten, sollten Sie Dynamic Media nur aktivieren, wenn Sie ein [spezifisches Szenario](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media) verwenden. Dynamic Media ist deaktiviert, es sei denn, Sie aktivieren Dynamic Media über den Ausführungsmodus.

Zum Aktivieren von Dynamic Media müssen Sie den Ausführungsmodus für Dynamic Media entweder über die Befehlszeile oder den Schnellstart-Dateinamen aktivieren.

**So aktivieren Sie Dynamic Media**:

1. In der Befehlszeile haben Sie nach dem Starten des Schnellstartvorgangs die folgenden Möglichkeiten:

   * Fügen Sie beim Starten der JAR-Datei **[!UICONTROL -r dynamicmedia]** am Ende der Befehlszeile hinzu.

   ```shell
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -r dynamicmedia
   ```

   Wenn Sie in s7delivery veröffentlichen, müssen Sie auch die folgenden trustStore-Argumente einbeziehen:

   ```shell
   -Djavax.net.ssl.trustStore=<absoluteFilePath>/customerTrustStoreFileName>
   
    -Djavax.net.ssl.trustStorePassword=<passwordForTrustStoreFile>
   ```

1. Fordern Sie `http://localhost:4502/is/image` an und stellen Sie sicher, dass Image Server jetzt ausgeführt wird.

   >[!NOTE]
   >
   >Informationen zur Fehlerbehebung bei Problemen mit Dynamic Media finden Sie in den folgenden Protokollen im Ordner **[!UICONTROL crx-quickstart/logs/]** :
   >
   >* ImageServer-&lt;PortId>-&lt;JJJJ>&lt;MM>&lt;TT>.log - Das ImageServer-Protokoll stellt Statistiken und analytische Informationen bereit, die zur Analyse des Verhaltens des internen ImageServer-Prozesses verwendet werden.

      Beispiel eines Image Server-Protokolldateinamens: `ImageServer-57346-2019-07-25.log`
   * s7access-&lt;jjjj>&lt;mm>&lt;tt>.log - Das s7access-Protokoll zeichnet alle Anfragen auf, die über `/is/image` und `/is/content` an Dynamic Media gesendet werden.
   Diese Protokolle werden nur verwendet, wenn Dynamic Media aktiviert ist. Sie sind nicht im Paket **Download Full** enthalten, das von der Seite **[!UICONTROL system/console/status-Bundlelist]** generiert wird. Wenn Sie den Kundensupport aufrufen, wenn Sie ein Dynamic Media-Problem haben, hängen Sie beide Protokolle an das Problem an.

### Bei Installation von AEM über einen anderen Port oder Kontextpfad {#if-you-installed-aem-to-a-different-port-or-context-path}

Wenn Sie [AEM auf einem Anwendungsserver](/help/sites-deploying/application-server-install.md) bereitstellen und Dynamic Media aktiviert haben, müssen Sie die Domäne **self** im Externalizer konfigurieren. Andernfalls funktioniert die Generierung von Miniaturansichten für Dynamic Media Assets nicht richtig.

Falls Sie den Schnellstart für einen anderen Port oder Kontextpfad ausführen, müssen Sie die Domäne **self** ebenfalls ändern.

Wenn Dynamic Media aktiviert ist, werden die statischen Miniaturansicht-Wiedergabeformate für Bild-Assets mit Dynamic Media generiert. Damit die Generierung von Miniaturansichten für Dynamic Media richtig funktioniert, muss AEM eine URL-Anforderung an sich selbst senden und sowohl die Portnummer als auch den Kontextpfad kennen.

In AEM:

* Die Domäne **self** im [Externalizer](/help/sites-developing/externalizer.md) wird verwendet, um sowohl die Portnummer als auch den Kontextpfad abzurufen.
* Wenn keine **self**-Domäne konfiguriert ist, werden die Portnummer und der Kontextpfad vom Jetty-HTTP-Dienst abgerufen.

In einer AEM QuickStart-WAR-Bereitstellung können die Portnummer und der Kontextpfad nicht abgeleitet werden. Daher müssen Sie eine **self**-Domäne konfigurieren. Weitere Informationen zur Konfiguration der Domäne **self** finden Sie in der [Externalizer-Dokumentation](/help/sites-developing/externalizer.md).

>[!NOTE]
Bei einer [eigenständigen AEM Quickstart-Bereitstellung](/help/sites-deploying/deploy.md) muss die Domäne **self** im Allgemeinen nicht konfiguriert werden, weil die Portnummer und der Kontextpfad automatisch konfiguriert werden können. Sie müssen die Domäne **self** aber konfigurieren, wenn alle Netzwerkschnittstellen deaktiviert sind.

## Deaktivieren von Dynamic Media  {#disabling-dynamic-media}

Dynamic Media ist standardmäßig deaktiviert. Wenn Sie Dynamic Media aktiviert haben, kann es sein, dass Sie es zu einem späteren Zeitpunkt deaktivieren möchten.

Um Dynamic Media nach dem Aktivieren wieder zu deaktivieren, müssen Sie das Ausführungsmodus-Flag **[!UICONTROL -r dynamicmedia]** entfernen.

**Gehen Sie wie folgt vor, um Dynamic Media nach der Aktivierung zu deaktivieren**:

1. In der Befehlszeile haben Sie nach dem Starten des Schnellstartvorgangs die beiden folgenden Möglichkeiten:

   * Fügen Sie beim Starten der JAR-Datei nicht `-r dynamicmedia` zur Befehlszeile hinzu.

   ```shell
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar
   ```

1. Anfrage `http://localhost:4502/is/image`. Sie erhalten eine Nachricht, dass Dynamic Media deaktiviert wurde.

   >[!NOTE]
   Nachdem der Dynamic Media-Ausführungsmodus deaktiviert wurde, wird der Workflow-Schritt, der das Ausgabeformat `qdam.pyramid.tiff` generiert, automatisch übersprungen. Hierbei werden auch die Unterstützung der dynamischen Wiedergabeformate und andere Dynamic Media-Funktionen deaktiviert.
   Achtung: Wenn Sie den Dynamic Media-Ausführungsmodus nach der Konfiguration des AEM-Servers deaktivieren, sind alle mit diesem Ausführungsmodus hochgeladenen Elemente ungültig.

## (Optional) Migration von Dynamic Media-Vorgaben und -Konfigurationen von 6.3 auf 6.4 ohne Ausfallzeiten {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Wenn Sie ein Upgrade AEM Dynamic Media von 6.3 auf 6.4 durchführen - was jetzt die Möglichkeit bietet, keine Ausfallzeiten (auch &quot;Opt-in&quot;) zu erzielen -, müssen Sie den folgenden curl-Befehl ausführen, um Ihre Vorgaben und Konfigurationen in CRXDE Lite von `/etc` auf `/conf` zu migrieren.

**Hinweis**: Wenn Sie Ihre AEM-Instanz im Kompatibilitätsmodus ausführen (d. h., Sie haben die Kompatibilität installiert), müssen Sie diese Befehle nicht ausführen.

Um Ihre benutzerdefinierten Vorgaben und Konfigurationen von `/etc` auf `/conf` zu migrieren, führen Sie den folgenden Linux-curl-Befehl aus:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

Bei allen Upgrades, ob mit oder ohne Kompatibilitätspaket, können Sie mit dem folgenden Befehl die standardmäßigen Benutzer-Vorgaben kopieren:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## Konfigurieren der Bildreplikation {#configuring-image-replication}

Die Dynamic Media-Bildbereitstellung funktioniert durch die Veröffentlichung von Bild-Assets, einschließlich Videominiaturen, aus der AEM-Autoreninstanz und die Replikation dieser Assets auf den On-Demand-Replikationsdienst der Adobe (die Replikationsdienst-URL). Assets werden dann über den On-Demand-Bildbereitstellungsdienst (die Image Service-URL) bereitgestellt.

Führen Sie die folgenden Schritte aus:

1. [Einrichten der Authentifizierung](#setting-up-authentication).
1. [Konfigurieren Sie den Replikationsagenten](#configuring-the-replication-agent).

Der Replikationsagent veröffentlicht Dynamic Media-Assets wie Bilder, Videometadaten und Sets auf den von der Adobe gehosteten Bilddienst. Der Replikationsagent ist nicht standardmäßig aktiviert.

Nachdem Sie den Replikationsagenten konfiguriert haben, müssen Sie [überprüfen und testen, ob die Einrichtung erfolgreich war](#validating-the-replication-agent-for-dynamic-media). In diesem Abschnitt wird die Vorgehensweise beschrieben.

>[!NOTE]
Die standardmäßige Speicherbegrenzung für die PTIFF-Erstellung beträgt für alle Workflows 3 GB. Beispielsweise können Sie ein Bild verarbeiten, für das 3 GB Speicher erforderlich sind, während andere Workflows angehalten werden, oder Sie können zehn Bilder parallel verarbeiten, die jeweils 300 MB Speicher erfordern.
Die Speicherbegrenzung ist konfigurierbar und sollte zur Verfügbarkeit der Systemressourcen und zur Art und Weise der Verarbeitung von Bildinhalten passen. Falls Sie über viele sehr große Assets verfügen und im System ausreichend Speicher vorhanden ist, können Sie diese Begrenzung erhöhen, um sicherzustellen, dass die Bilder parallel verarbeitet werden.
Ein Bild, für das mehr Speicher als laut Begrenzung festgelegt erforderlich ist, wird abgelehnt.
Navigieren Sie zum Ändern der Speicherbegrenzung für die PTIFF-Erstellung zu **[!UICONTROL Tools > Vorgänge > Web-Konsole > Adobe CQ Scene7 PTiffManager]** und ändern Sie den Wert `maxMemory`.

### Einrichten der Authentifizierung {#setting-up-authentication}

Es ist erforderlich, dass Sie die Replikationsauthentifizierung für den Autor einrichten, um Bilder für den Dynamic Media-Service für die Bildbereitstellung zu replizieren. Rufen Sie dazu einen KeyStore ab, speichern Sie ihn dann unter dem Benutzer **[!UICONTROL dynamic-media-replication]** und konfigurieren Sie ihn. Der Administrator in Ihrem Unternehmen sollte während des Bereitstellungsprozesses eine Begrüßungs-E-Mail mit der KeyStore-Datei und den erforderlichen Anmeldeinformationen erhalten haben. Wenden Sie sich an die Kundenunterstützung, falls Sie diese Informationen nicht erhalten haben.

**Gehen Sie wie folgt vor, um die Authentifizierung einzurichten**:

1. Wenden Sie sich an die Kundenunterstützung, um Ihre KeyStore-Datei und das dazugehörige Kennwort zu erhalten (falls noch nicht vorhanden). Dies ist Teil des Bereitstellungsvorgangs und die Schlüssel werden Ihrem Konto zugeordnet.
1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Tools > Sicherheit > Benutzer]**.
1. Navigieren Sie auf der Seite Benutzerverwaltung zum Benutzer **[!UICONTROL dynamic-media-replication]** und tippen Sie dann zum Öffnen.

   ![dm-replication](assets/dm-replication.png)

1. Tippen Sie auf der Seite &quot;Benutzereinstellungen für dynamic-media-replication bearbeiten&quot;auf die Registerkarte **[!UICONTROL Keystore]** und tippen Sie dann auf **[!UICONTROL KeyStore erstellen]**.

   ![dm-replication-keystore](assets/dm-replication-keystore.png)

1. Geben Sie im Dialogfeld **[!UICONTROL Zugangskennwort für KeyStore festlegen]** ein Kennwort ein und bestätigen Sie es.

   >[!NOTE]
   Merken Sie sich das eingegebene Kennwort. Sie müssen sie erneut eingeben, wenn Sie den **[!UICONTROL Replikationsagenten]** später konfigurieren.

   ![chlimage_1-508](assets/chlimage_1-508.png)

1. Erweitern Sie auf der Seite **[!UICONTROL Benutzereinstellungen für dynamic-media-replication bearbeiten]** den Bereich **[!UICONTROL Privaten Schlüssel aus KeyStore-Datei hinzufügen]** und fügen Sie Folgendes ein (siehe folgende Abbildungen):

   * Geben Sie im Feld **[!UICONTROL Neuer Alias]** den Namen eines Alias ein, den Sie später in der Replikationskonfiguration verwenden werden. Beispiel: **replication**.
   * Tippen Sie auf **[!UICONTROL KeyStore-Datei]**. Navigieren Sie zur KeyStore-Datei, die Sie von Adobe, wählen Sie sie aus und tippen Sie auf **[!UICONTROL Öffnen]**.
   * Geben Sie im Feld **[!UICONTROL KeyStore File Password]** das Kennwort für die KeyStore-Datei ein. Dies ist _nicht_ das KeyStore-Kennwort, das Sie in Schritt 5 erstellt haben, aber die KeyStore-Adobe für das Dateikennwort ist in der Begrüßungs-E-Mail enthalten, die Sie während der Bereitstellung erhalten haben. Wenden Sie sich an die Kundenunterstützung von Adobe, um Ihre KeyStore-Datei und das dazugehörige Kennwort zu erhalten (falls noch nicht vorhanden).
   * Geben Sie im Feld **[!UICONTROL Kennwort für privaten Schlüssel]** das Kennwort für den privaten Schlüssel ein (dies kann dasselbe Kennwort für den privaten Schlüssel wie im vorherigen Schritt sein). Das Kennwort für den privaten Schlüssel ist in der Begrüßungs-E-Mail von Adobe enthalten, die während der Bereitstellung an Sie gesendet wird. Nehmen Sie Kontakt mit der Kundenunterstützung von Adobe auf, falls Sie kein Kennwort für den privaten Schlüssel erhalten haben.
   * Geben Sie im Feld **[!UICONTROL Alias für privaten Schlüssel]** den Alias für den privaten Schlüssel ein. Beispiel: `companyname-alias`. Der Alias für den privaten Schlüssel ist in der Begrüßungs-E-Mail von Adobe enthalten, die während der Bereitstellung an Sie gesendet wird. Nehmen Sie Kontakt mit der Kundenunterstützung von Adobe auf, falls Sie keinen Alias für den privaten Schlüssel erhalten haben.

   ![edit_settings_fordynamic-media-replication2](assets/edit_settings_fordynamic-media-replication2.png)

1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um Ihre Änderungen für diesen Benutzer zu speichern.

   Als Nächstes müssen Sie den [Replikationsagenten konfigurieren](#configuring-the-replication-agent).

### Konfigurieren des Replikationsagenten {#configuring-the-replication-agent}

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Tools >  Bereitstellung >  Replikation > Agenten für Autor]**.
1. Tippen Sie auf der Seite „Agenten für Autor“ auf **[!UICONTROL Hybride Bildreplikation für dynamische Medien (s7delivery)]**.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Tippen Sie auf die Registerkarte **[!UICONTROL Einstellungen]** und geben Sie dann Folgendes ein:

   * **[!UICONTROL Aktiviert]**: Aktivieren Sie dieses Kontrollkästchen, um den Replikationsagenten zu aktivieren.
   * **[!UICONTROL Region]**  - Auf die entsprechende Region eingestellt: Nordamerika, Europa oder Asien
   * **[!UICONTROL Mandantenkennung]**  - Dieser Wert ist der Name Ihres Unternehmens/Mandanten, das/der im Replikationsdienst veröffentlicht wird. Dieser Wert ist die Mandantenkennung, die die Adobe in der Begrüßungs-E-Mail bereitstellt, die Ihnen während der Bereitstellung gesendet wird. Wenden Sie sich an die Kundenunterstützung von Adobe, falls Sie diese E-Mail nicht erhalten haben.
   * **[!UICONTROL Key Store Alias]**  - Dieser Wert entspricht dem Wert &quot;New Alias&quot;, der beim Generieren des Schlüssels unter  [Einrichten der Authentifizierung](#setting-up-authentication) festgelegt wurde. z. B.  `replication`. (Siehe Schritt 7 unter [Einrichten der Authentifizierung](#setting-up-authentication).)
   * **[!UICONTROL Key Store Password]**  - Dies ist das KeyStore-Kennwort, das erstellt wurde, als Sie auf KeyStore  **[!UICONTROL erstellen tippen]**. Dieses Kennwort wird nicht von Adobe bereitgestellt. Siehe Schritt 5 von [Einrichten der Authentifizierung](#setting-up-authentication).

   In der folgenden Abbildung ist der Replikationsagent mit Beispieldaten dargestellt:

   ![chlimage_1-509](assets/chlimage_1-509.png)

1. Tippen Sie auf **[!UICONTROL OK]**.

### Validieren des Replikationsagenten für Dynamic Media {#validating-the-replication-agent-for-dynamic-media}

Gehen Sie wie folgt vor, um den Replikationsagenten auf dynamische Medien zu überprüfen:

Tippen Sie auf **[!UICONTROL Verbindung testen]**. Die Beispielausgabe lautet wie folgt:

```shell
11.03.2016 10:57:55 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
11.03.2016 10:57:55 - * Auth User: replication-receiver
11.03.2016 10:57:55 - * HTTP Version: 1.1
11.03.2016 10:57:55 - * Using OAuth 2.0 Authorization Grants
11.03.2016 10:57:55 - * OAuth 2.0 User: dynamic-media-replication
11.03.2016 10:57:55 - * OAuth 2.0 Token: '*****' initialized
11.03.2016 10:57:55 - Publishing: POST[https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=xfpuu-6613]
11.03.2016 10:57:55 - Publish response: OK[]
11.03.2016 10:57:55 - Transfer succeeded in 141 ms for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
-------------------------------------------------------------------------------------------------------------------------------
Replication test succeeded
```

>[!NOTE]
Sie können die Überprüfung auch durchführen, indem Sie einen der folgenden Schritte ausführen:
* Überprüfen Sie die Replikationsprotokolle, um sicherzustellen, dass das Asset repliziert wurde.
* Veröffentlichen Sie ein Bild. Tippen Sie auf das Bild und wählen Sie **[!UICONTROL Viewer]** im Dropdown-Menü aus. Wählen Sie eine Viewer-Vorgabe aus, tippen Sie auf **[!UICONTROL URL]** und kopieren Sie die URL und fügen Sie sie in den Browser ein, um zu überprüfen, ob das Bild angezeigt wird.


### Durchführen der Fehlerbehebung für die Authentifizierung {#troubleshooting-authentication}

Hier sind einige Probleme, die beim Einrichten der Authentifizierung auftreten können, und die dazugehörigen Lösungen angegeben. Achten Sie darauf, dass Sie die Replikation eingerichtet haben, bevor Sie diese Angaben prüfen.

#### Problem: HTTP-Statuscode 401 mit der Meldung „Authorization Required“ (Autorisierung erforderlich) {#problem-http-status-code-with-message-authorization-required}

Dieses Problem kann auftreten, wenn der KeyStore für den Benutzer `dynamic-media-replication` nicht eingerichtet wurde.

```shell
Replication test to s7delivery:https://s7bern.macromedia.com:8580/is-publish/
17.06.2016 18:54:43 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}
17.06.2016 18:54:43 - * Auth User: replication-receiver
17.06.2016 18:54:43 - * HTTP Version: 1.1
17.06.2016 18:54:43 - * Using OAuth 2.0 Authorization Grants
17.06.2016 18:54:43 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 18:54:43 - No OAuth token available. OAuth not initialized
17.06.2016 18:54:43 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 18:54:43 - Publishing: POST[https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough]
17.06.2016 18:54:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
17.06.2016 18:54:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309,
 userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
```

**Lösung**: Vergewissern Sie sich, dass  `KeyStore` der Ordner unter  **[!UICONTROL dynamic-media-replicationuser gespeichert]** wird und das richtige Kennwort enthält.

#### Problem: Schlüssel kann nicht entschlüsselt werden – Daten können nicht entschlüsselt werden {#problem-could-not-decrypt-key-could-not-decrypt-data}

```xml
Replication test to s7delivery:https://<localhost>:8580/is-publish/
17.06.2016 19:00:16 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}
17.06.2016 19:00:16 - * Auth User: replication-receiver
17.06.2016 19:00:16 - * HTTP Version: 1.1
17.06.2016 19:00:16 - * Using OAuth 2.0 Authorization Grants
17.06.2016 19:00:16 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 19:00:16 - No OAuth token available. OAuth not initialized
17.06.2016 19:00:16 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 19:00:16 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}. java.lang.SecurityException: java.security.UnrecoverableKeyException: Could not decrypt key: Could not decrypt data.
```

**Lösung**: Überprüfen Sie das Kennwort. Das im Replikationsagenten gespeicherte Kennwort entspricht nicht dem Kennwort, das zum Erstellen des KeyStore verwendet wurde.

#### Problem: InvalidAlgorithmParameterException {#problem-invalidalgorithmparameterexception}

Dieses Problem wird durch einen Konfigurationsfehler in Ihrer AEM-Autoreninstanz verursacht. Für den Java-Prozess des Autors wird nicht das richtige `javax.net.ssl.trustStore`-Element verwendet. Dieser Fehler ist im Replikationsprotokoll enthalten:

```shell
14.04.2016 09:37:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
14.04.2016 09:37:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
```

Oder im Fehlerprotokoll:

```shell
07.25.2019 12:00:59.893 *ERROR* [sling-threadpool-db2763bb-bc50-4bb5-bb64-10a09f432712-(apache-sling-job-thread-pool)-90-com_day_cq_replication_job_s7delivery(com/day/cq/replication/job/s7delivery)] com.day.cq.replication.Agent.s7delivery.queue Error during processing of replication.
 
java.io.IOException: Failed to execute request 'https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
        at com.scene7.is.catalog.service.publish.atomic.PublishingServiceHttp.executePost(PublishingServiceHttp.scala:195)
```

**Lösung**: Stellen Sie sicher, dass für den Java-Prozess in der AEM-Autoreninstanz die Systemeigenschaft  **-Djavax.net.ssl.trustStore=** auf einen gültigen Truststore festgelegt ist.

#### Problem: KeyStore ist entweder nicht eingerichtet oder nicht initialisiert {#problem-keystore-is-either-not-set-up-or-it-is-not-initialized}

Dieses Problem kann durch einen Hotfix oder ein Feature Pack verursacht werden, das den Knoten **[!UICONTROL dynamic-media-user]** oder **[!UICONTROL keystore]** überschreibt.

Beispiel für Replikationsprotokoll:

```shell
Replication test to s7delivery:https://replicate-na.assetsadobe.com/is-publish
02.08.2016 14:37:44 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}
02.08.2016 14:37:44 - * Auth User: replication-receiver
02.08.2016 14:37:44 - * HTTP Version: 1.1
02.08.2016 14:37:44 - * Using OAuth 2.0 Authorization Grants
02.08.2016 14:37:44 - * OAuth 2.0 User: dynamic-media-replication
02.08.2016 14:37:44 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}. com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised key store for user dynamic-media-replication
```

**Lösung**:

1. Navigieren Sie zur Seite **[!UICONTROL Benutzerverwaltung]** :

   `localhost:4502/libs/granite/security/content/useradmin.html`
1. Navigieren Sie auf der Seite **[!UICONTROL Benutzerverwaltung]** zum Benutzer **[!UICONTROL dynamic-media-replication]** und tippen Sie dann zum Öffnen.
1. Tippen Sie auf die Registerkarte **[!UICONTROL KeyStore]** . Wenn die Schaltfläche **[!UICONTROL KeyStore erstellen]** angezeigt wird, müssen Sie die Schritte zum [Einrichten der Authentifizierung](#setting-up-authentication) wiederholen.
1. Wenn Sie die Einrichtung **[!UICONTROL KeyStore]** erneut durchführen mussten, müssen Sie möglicherweise auch [den Replikationsagenten](config-dynamic.md#configuring-the-replication-agent) erneut konfigurieren.

   Konfigurieren Sie den s7delivery-Replikationsagenten neu.

   `localhost:4502/etc/replication/agents.author/s7delivery.html`

1. Tippen Sie auf **[!UICONTROL Verbindung testen]**, um zu überprüfen, ob die Konfiguration gültig ist.

#### Problem: Für den Veröffentlichungsagenten wird SSL anstelle von OAuth verwendet {#problem-publish-agent-is-using-ssl-instead-of-oauth}

Dieses Problem kann durch einen Hotfix, ein nicht korrekt installiertes Feature Pack oder Überschreiben der Einstellungen verursacht werden.

Beispiel für Replikationsprotokoll:

```shell
01.08.2016 18:42:59 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}
01.08.2016 18:42:59 - * Auth User: replication-receiver
01.08.2016 18:42:59 - * HTTP Version: 1.1
01.08.2016 18:42:59 - * Using Client Auth SSL alias - replication-receiver *
01.08.2016 18:42:59 - Publishing: POST[https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=altayerstaging]
01.08.2016 18:42:59 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
01.08.2016 18:42:59 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
```

**Lösung:**

1. Tippen Sie in AEM auf **[!UICONTROL Tools > Allgemein > CRXDE Lite]**.

   `localhost:4502/crx/de/index.jsp`

1. Navigieren Sie zum Knoten **[!UICONTROL s7delivery Replication Agent]** .

   `localhost:4502/crx/de/index.jsp#/etc/replication/agents.author/s7delivery/jcr:content`

1. Fügen Sie diese Einstellung dem Replikationsagenten hinzu (boolescher Wert mit der Einstellung **[!UICONTROL True]**):

   `enableOauth=true`

1. Tippen Sie in der oberen linken Ecke der Seite auf **[!UICONTROL Alle speichern]**.

### Konfiguration testen {#testing-your-configuration}

Adobe empfiehlt, für die Konfiguration einen umfassenden Test durchzuführen.

Achten Sie darauf, dass Sie vor Beginn dieses Tests Folgendes durchgeführt haben:

* Hinzufügen von Bildvorgaben.
* Konfigurieren Sie **Dynamic Media Configuration (Pre 6.3)** unter **[!UICONTROL Cloud Services]**. Die Bilddienst-URL ist für diesen Test nicht erforderlich.

Gehen Sie wie folgt vor, um die Konfiguration zu testen:

1. Laden Sie ein Bild-Asset hoch. (Tippen Sie in Assets auf **[!UICONTROL Erstellen > Dateien]** und wählen Sie die Datei aus.)
1. Warten Sie, bis der Workflow abgeschlossen ist.
1. Veröffentlichen Sie das Bild-Asset. (Wählen Sie das Asset aus und tippen Sie auf **[!UICONTROL Quick Publish]**.)
1. Navigieren Sie zu den Ausgabeformaten für dieses Bild, indem Sie das Bild öffnen und auf **[!UICONTROL Ausgabeformate]** tippen.

   ![chlimage_1-510](assets/chlimage_1-510.png)

1. Wählen Sie eine beliebige dynamische Wiedergabe aus.
1. Tippen Sie auf **[!UICONTROL URL]** , um die URL für dieses Asset abzurufen.
1. Navigieren Sie zur ausgewählten URL und überprüfen Sie, ob sich das Bild wie erwartet verhält.

Eine andere Möglichkeit zum Testen der Bereitstellung Ihrer Assets besteht darin, „req=exists“ an die URL anzufügen.

## Konfigurieren von Dynamic Media Cloud Services {#configuring-dynamic-media-cloud-services}

Der Dynamic Media Cloud Service bietet Unterstützung für Cloud-Services, z. B. hybride Veröffentlichung und Bereitstellung von Bildern und Videos, Videoanalyse und Videokodierung.

Im Rahmen der Konfiguration müssen Sie eine Registrierungs-ID, Videodienst-URL, Bilddienst-URL und Replikationsdienst-URL eingeben und die Authentifizierung einrichten. Sie sollten diese gesamten Informationen im Rahmen des Prozesses für die Kontobereitstellung erhalten haben. Wenn Sie diese Informationen nicht erhalten haben, wenden Sie sich an Ihren Adobe Experience Manager-Administrator oder an den technischen Support der Adobe, um die Informationen zu erhalten.

>[!NOTE]
Bevor Sie Dynamic Media-Cloud Services einrichten, stellen Sie sicher, dass Ihre Veröffentlichungsinstanz eingerichtet ist. Außerdem müssen Sie die Replikation eingerichtet haben, bevor Sie Dynamic Media-Cloud Services konfigurieren.

**So konfigurieren Sie Cloud-Services für Dynamic Media**:

1. Tippen Sie AEM auf das AEM Logo, um auf die globale Navigationskonsole zuzugreifen, und tippen Sie dann auf **[!UICONTROL Tools > Cloud Services > Dynamic Media-Konfiguration (vor 6.3)]**.
1. Wählen Sie auf der Seite **[!UICONTROL Dynamic Media Configuration Browser]** im linken Bereich **[!UICONTROL global]** und tippen Sie dann auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Dynamic Media-Konfiguration erstellen]** im Feld „Titel“ einen Titel ein.****
1. Wenn Sie Dynamic Media für Video konfigurieren,

   * Geben Sie im Feld **[!UICONTROL Registrierungs-ID]** Ihre Registrierungs-ID ein.
   * Geben Sie im Feld **[!UICONTROL Videodienst-URL]** die Videodienst-URL für das Dynamic Media Gateway ein.

1. Geben Sie beim Konfigurieren von Dynamic Media für die Bilddarstellung im Dialogfeld **[!UICONTROL Bilddienst-URL]** die Bilddienst-URL für das Dynamic Media Gateway ein.
1. Tippen Sie auf **[!UICONTROL Speichern]**, um zum Browser für die Dynamic Media-Konfiguration zurückzukehren.
1. Tippen Sie auf das AEM-Logo, um auf die Konsole für die globale Navigation zuzugreifen.

## Konfigurieren von Videoberichten {#configuring-video-reporting}

Sie können Videoberichte für mehrere Installationen von AEM im Hybridmodus von Dynamic Media konfigurieren.

**Verwendung:** Zum Zeitpunkt der Konfiguration der  **[!UICONTROL Dynamic Media-Konfiguration (vor 6.3)]** werden zahlreiche Funktionen gestartet, darunter auch Videoberichte. Die Konfiguration erstellt eine Report Suite in einem regionalen Analytics-Unternehmen Wenn Sie mehrere Autorknoten konfigurieren, erstellen Sie für jeden davon eine separate Report Suite. Das führt zu inkonsistenten Berichtsdaten in den einzelnen Installationen. Wenn jeder Autorknoten auf denselben Hybrid-Veröffentlichungsserver verweist, ändert die letzte Autorinstallation die Ziel-Report Suite für alle Videoberichte. Dieses Problem führt zur Überlastung des Analysesystems mit zu vielen Report Suites.

**Erste Schritte:** Konfigurieren Sie Videoberichte, indem Sie die folgenden drei Schritte ausführen.

1. Erstellen Sie ein Vorgabenpaket [!DNL Video Analytics], nachdem Sie **[!UICONTROL Dynamic Media Configuration (Pre 6.3)]** auf dem ersten Autorknoten konfiguriert haben. Diese Aufgabe ist wichtig, da sie einer neuen Konfiguration die weitere Verwendung derselben Report Suite ermöglicht.
1. Installieren Sie das Vorgabenpaket [!DNL Video Analytics] auf einem beliebigen ***neuen*** Autorenknoten ***bevor Sie*** die Dynamic Media-Konfiguration (vor 6.3) konfigurieren.

1. Überprüfen und debuggen Sie die Paketinstallation.

### Erstellen eines Vorgabenpakets [!DNL Video Analytics] nach dem Konfigurieren des ersten Autorknotens {#creating-a-video-analytics-preset-package-after-configuring-the-first-author-node}

Wenn Sie diese Aufgabe abgeschlossen haben, verfügen Sie über eine Paketdatei mit den Vorgaben [!DNL Video Analytics]. Diese Vorgaben enthalten eine Report Suite, den Tracking-Server, den Tracking-Namespace und die Marketing Cloud-Organisations-ID (falls verfügbar).

1. Falls noch nicht geschehen, konfigurieren Sie **[!UICONTROL Dynamic Media Configuration (Pre 6.3)]**.
1. (Optional) Zeigen Sie die **[!UICONTROL Report Suite-ID]** an und kopieren Sie sie (Sie müssen Zugriff auf JCR haben). Die **[!UICONTROL Report Suite-ID]** ist zwar nicht erforderlich, erleichtert aber die Validierung.
1. Erstellen Sie ein Paket mit **[!UICONTROL Package Manager]**.
1. Bearbeiten Sie das Paket, sodass es einen Filter enthält.

   In AEM: `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

1. Erstellen Sie das Paket.
1. Laden Sie das Vorgabenpaket [!DNL Video Analytics] herunter oder geben Sie es frei, damit es für nachfolgende neue Autorknoten freigegeben werden kann.

### Installieren des Vorgabenpakets [!DNL Video Analytics] , bevor Sie zusätzliche Autorknoten konfigurieren {#installing-the-video-analytics-preset-package-before-you-configure-additional-author-nodes}

Stellen Sie sicher, dass Sie diese Aufgabe _vor_ ausführen, dass Sie **[!UICONTROL Dynamic Media-Konfiguration (vor 6.3)]** konfigurieren. Andernfalls wird eine weitere nicht verwendete Report Suite erstellt. Darüber hinaus wird die Datenerfassung nicht optimiert, obwohl die Videoberichte korrekt ausgeführt werden.

Stellen Sie sicher, dass auf das Vorgabenpaket [!DNL Video Analytics] des ersten Autorknotens auf dem neuen Autorknoten zugegriffen werden kann.

1. Laden Sie das zuvor erstellte Vorgabenpaket [!DNL Video Analytics] in **[!UICONTROL Package Manager]** hoch.
1. Installieren Sie das Vorgabenpaket [!DNL Video Analytics] .
1. Konfigurieren Sie **[!UICONTROL Dynamic Media-Konfiguration (vor 6.3)]**.

### Überprüfen und Debuggen der Paketinstallation {#verifying-and-debugging-the-package-installation}

1. Führen Sie einen der folgenden Schritte aus, um die Paketinstallation zu überprüfen und bei Bedarf zu debuggen:

   * **Überprüfen Sie die  [!DNL Video Analytics] Vorgabe über**
JCRT, um die  [!DNL Video Analytics] Vorgabe über JCR zu überprüfen. Sie müssen Zugriff auf die  **[!UICONTROL CRXDE Lite]** haben.

      AEM - Navigieren Sie in **[!UICONTROL CRXDE Lite]** zu `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata  `.

      Sie lautet `http://localhost:4502/crx/de/index.jsp#/conf/global/settings/dam/dm/presets/analytics/jcr%3Acontent/userdata`

      Wenn Sie keinen Zugriff auf **[!UICONTROL CRXDE Lite]** im Autorknoten haben, können Sie die Vorgabe über den Veröffentlichungsserver überprüfen.

   * **Überprüfen der  [!DNL Video Analytics] Vorgabe über den Image-Server**

      Sie können die Vorgabe [!DNL Video Analytics] direkt validieren, indem Sie eine Image Server-Anforderung `req=userdata` stellen.

      Um beispielsweise die Vorgabe [!DNL Video Analytics] im Autorknoten anzuzeigen, können Sie die folgende Anfrage stellen:

      `http://localhost:4502/is/image/conf/global/settings/dam/dm/presets/analytics?req=userdata`

      Um die Vorgabe auf Veröffentlichungs-Servern zu überprüfen, können Sie eine ähnliche direkte Anfrage an den Veröffentlichungsserver richten. Die Antworten sind auf dem Autor- und Veröffentlichungsknoten identisch. Die Antwort sieht in etwa wie folgt aus:

      ```
      marketingCloudOrgId=0FC4E86B573F99CC7F000101
       reportSuite=aemaem6397618-2018-05-23
       trackingNamespace=aemvideodal
       trackingServer=aemvideodal.d2.sc.omtrdc.net
      ```

   * **Überprüfen Sie die  [!DNL Video Analytics] Vorgabe über das Tool für Videoberichte in AEM**

      Tippen Sie auf **[!UICONTROL Tools > Assets > Videoberichte]** `http://localhost:4502/mnt/overlay/dam/gui/content/s7dam/videoreports/videoreport.html`

      Wenn die folgende Fehlermeldung angezeigt wird, ist die Report Suite zwar verfügbar, aber nicht ausgefüllt. Dieser Fehler ist korrekt und erwünscht, wenn es sich um eine Neuinstallation handelt, bevor das System Daten erfasst hat.

      ![screen_shot_2018-05-23at52254pm](assets/screen_shot_2018-05-23at52254pm.png)
   Zum Generieren von Berichtsdaten müssen Sie ein Video hochladen und veröffentlichen. Verwenden Sie **[!UICONTROL URL kopieren]** und führen Sie das Video mindestens einmal aus.

   Beachten Sie, dass es bis zu 12 Stunden dauern kann, bevor die Berichtsdaten aus der Verwendung von Video-Viewer geladen werden.

   Wenn ein Fehler vorliegt und die Report Suite nicht ordnungsgemäß festlegt wurde, wird der folgende Warnhinweis angezeigt.

   ![screen_shot_2018-05-23at52612pm](assets/screen_shot_2018-05-23at52612pm.png)

   Dieser Fehler wird auch angezeigt, wenn Videoberichte ausgeführt werden, bevor Sie die Dienste **[!UICONTROL Dynamic Media-Konfiguration (vor 6.3)]** konfigurieren.

### Beheben von Problemen bei der Konfiguration von Videoberichten {#troubleshooting-the-video-reporting-configuration}

* Während der Installation treten manchmal Timeouts beim Analytics API Server auf. Bei der Installation wird 20-mal versucht, die Verbindung wiederherzustellen. Wenn diese Situation eintritt, zeichnet die Protokolldatei mehrere Fehler auf. Suchen Sie nach `SiteCatalystReportService`.
* Wenn Sie das Vorgabenpaket [!DNL Video Analytics] nicht zuerst installieren, kann dies zur Erstellung einer neuen Report Suite führen.
* Beim Aktualisieren von AEM 6.3 auf AEM 6.4 oder AEM 6.4.1 und anschließenden Konfigurieren von **[!UICONTROL Dynamic Media Configuration (Pre 6.3)]** wird weiterhin eine Report Suite erstellt. Dieses Problem ist bekannt und wird in AEM 6.4.2 behoben.

### Über die Vorgabe [!DNL Video Analytics] {#about-the-video-analytics-preset}

Die Vorgabe [!DNL Video Analytics] - manchmal auch als Analysevorgabe bezeichnet - wird in Dynamic Media neben den Viewer-Vorgaben gespeichert. Sie entspricht im Grunde der Viewer-Vorgabe, enthält jedoch Informationen zum Konfigurieren von AppMeasurement- und Video Heartbeat-Berichten.

Die Eigenschaften der Vorgabe lauten wie folgt:

* **[!UICONTROL reportSuite]**
* **[!UICONTROL trackingServer]**
* **[!UICONTROL trackingNamespace]**
* **[!UICONTROL marketingCloudOrgId]**  (in älteren AEM nicht vorhanden)

AEM 6.4 und neuere Versionen speichern diese Vorgabe unter `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

## Replizieren von Katalogeinstellungen {#replicating-catalog-settings}

Sie müssen Ihre eigenen Standardeinstellungen für den Katalog im Rahmen der Einrichtung per JCR veröffentlichen. Gehen Sie wie folgt vor, um die Katalogeinstellungen zu replizieren:

1. Führen Sie in einem Terminalfenster folgenden Befehl aus:

   `curl -u admin:admin localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

1. Navigieren Sie AEM unter **[!UICONTROL CRXDE Lite]** zum folgenden Speicherort (Administratorberechtigungen erforderlich):

   `https://<server>:<port>/crx/de/index.jsp#/conf/global/settings/dam/dm/imageserver/`

1. Tippen Sie auf die Registerkarte **[!UICONTROL Replikation]**.
1. Tippen Sie auf **[!UICONTROL Replizieren]**.

## Replizieren von Viewer-Vorgaben {#replicating-viewer-presets}

Um ein Asset mit einer Viewer-Vorgabe bereitzustellen, müssen Sie die Viewer-Vorgabe replizieren/veröffentlichen. (Alle Viewer-Vorgaben müssen aktiviert _und_ repliziert werden, um die URL oder den Einbettungscode für ein Asset zu erhalten.) Weitere Informationen finden Sie unter [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

>[!NOTE]
Standardmäßig zeigt das System eine Vielzahl von Ausgabeformaten an, wenn Sie **[!UICONTROL Ausgabeformate]** und eine Vielzahl von Viewer-Vorgaben auswählen, wenn Sie **[!UICONTROL Viewer]** in der Detailansicht des Assets auswählen. Sie können die angezeigte Anzahl erhöhen oder verringern. Siehe [Erhöhen der Anzahl angezeigter Bildvorgaben](/help/assets/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) oder [Erhöhen der Anzahl angezeigter Viewer-Vorgaben](/help/assets/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

## Filtern von Assets für die Replikation {#filtering-assets-for-replication}

In Nicht-Dynamic Media-Bereitstellungen replizieren Sie _alle_-Assets (sowohl Bilder als auch Videos) aus Ihrer AEM Autorenumgebung in den Veröffentlichungsknoten AEM. Dieser Workflow ist erforderlich, da die AEM Veröffentlichungsserver auch die Assets bereitstellen.

Da Assets jedoch in Dynamic Media-Implementierungen über die Cloud bereitgestellt werden, müssen diese Assets nicht auf Veröffentlichungsknoten repliziert AEM. Ein solcher &quot;hybrider Publishing&quot;-Workflow vermeidet zusätzliche Speicherkosten und längere Verarbeitungszeiten für die Replikation von Assets. Andere Inhalte, z. B. Dynamic Media-Anzeigeprogramme, Seiten von Websites und statischer Inhalt, werden weiterhin über die AEM-Veröffentlichungsknoten bereitgestellt.

Neben der Replikation der Assets werden auch die folgenden Nicht-Assets repliziert:

* Dynamic Media-Bereitstellungskonfiguration: `/conf/global/settings/dam/dm/imageserver/configuration/jcr:content/settings`
* Bildvorgaben: `/conf/global/settings/dam/dm/presets/macros`
* Viewer-Vorgaben: `/conf/global/settings/dam/dm/presets/viewer`

Mit den Filtern können Sie Assets von der Replikation auf dem AEM-Veröffentlichungsknoten _ausschließen_.

### Verwenden von Asset-Standardfiltern für die Replikation {#using-default-asset-filters-for-replication}

Wenn Sie Dynamic Media für 1) Bildbearbeitung in der Produktion _oder_ 2) verwenden, können Sie die Standardfilter verwenden, die wir im Ist-Zustand bereitstellen. Folgende Filter sind standardmäßig aktiviert:

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Filter</strong></td> 
   <td><strong>Mimetype</strong></td> 
   <td><strong>Ausgabedarstellungen</strong></td> 
  </tr> 
  <tr> 
   <td>Dynamic Media-Bildbereitstellung</td> 
   <td><p>filter-images</p> <p>filter-sets</p> <p> </p> </td> 
   <td><p>Beginnt mit <strong>image/</strong></p> <p>Enthält <strong>application/</strong> und endet mit <strong>set</strong>.</p> </td> 
   <td>Die standardmäßigen "filter-images"(für einzelne Bild-Assets, einschließlich interaktiver Bilder) und "filter-sets"(für Rotationssets, Bildsets, gemischte Mediensets und Karussellsets) werden: 
    <ul> 
     <li>Fügen Sie PTIFF-Bilder und Metadaten für die Replikation ein (alle Ausgabedarstellungen, die mit <strong>cqdam</strong> beginnen).</li> 
     <li>Das Originalbild und statische Bildausgabeformate werden von der Replikation ausgeschlossen.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media-Videobereitstellung</td> 
   <td>filter-video</td> 
   <td>Beginnt mit <strong>video/</strong></td> 
   <td>Das vordefinierte "filter-video"wird: 
    <ul> 
     <li>Schließen Sie Proxy-Videoausgabeformate, Videominiatur/Posterbild, Metadaten (sowohl bei übergeordneten Video- als auch Videoausgabeformaten) für die Replikation ein (Beliebige Wiedergabe, die mit <strong>cqdam</strong> beginnt).</li> 
     <li>Das Originalvideo und statische Miniaturwiedergaben werden von der Replikation ausgeschlossen.<br /> <br /> <strong>Hinweis:</strong> Die Proxy-Videoausgabedarstellungen enthalten keine Binärdateien, sondern sind nur Knoteneigenschaften. Dies hat daher keine Auswirkung auf die Repositorygröße des Herausgebers.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media Classic-Integration</td> 
   <td><p>filter-images</p> <p>filter-sets</p> <p>filter-video</p> </td> 
   <td><p>Beginnt mit <strong>image/</strong></p> <p>Enthält <strong>application/</strong> und endet mit <strong>set</strong>.</p> <p>Beginnt mit <strong>video/</strong></p> </td> 
   <td><p>Sie konfigurieren den Transport-URI so, dass er auf Ihren AEM Veröffentlichungsserver verweist, anstatt auf die Adobe Dynamic Media Cloud-Replikationsdienst-URL. Durch das Einrichten dieses Filters können Assets mit Dynamic Media Classic bereitgestellt werden, anstatt mit der AEM-Veröffentlichungsinstanz.</p> <p>Die vordefinierten "filter-images", "filter-sets"und "filter-video"werden:</p> 
    <ul> 
     <li>Fügen Sie PTIFF-Bilder, Proxy-Videoausgabeformate und Metadaten für die Replikation hinzu. Da diese Daten in JCR nicht vorhanden sind, werden keine Schritte ausgeführt (bei Durchführung der AEM/Dynamic Media Classic-Integration).</li> 
     <li>Das Originalbild, statische Bildwiedergaben, das Originalvideo und statische Miniaturwiedergaben werden aus der Replikation ausgeschlossen. Stattdessen werden von Dynamic Media Classic Bild- und Video-Assets bereitgestellt.</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
Filter gelten für MIME-Typen und können nicht pfadspezifisch sein.

### Einrichten von Asset-Filtern für reine Videobereitstellungen {#setting-up-asset-filters-for-video-only-deployments}

Wenn Sie Dynamic Media ausschließlich für Videos nutzen, können Sie mit diesen Schritten Asset-Filter für die Replikation einrichten:

1. Tippen Sie AEM auf das AEM Logo, um auf die globale Navigationskonsole zuzugreifen, und tippen Sie auf **[!UICONTROL Tools > Bereitstellung > Replikation > Agenten für Autor]**.
1. Tippen Sie auf der Seite „Agenten für Autor“ auf **[!UICONTROL Standardagent (Publish)]**.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Aktivieren Sie im Dialogfeld **[!UICONTROL Agenteneinstellungen]** auf der Registerkarte [!UICONTROL Einstellungen] die Option **[!UICONTROL Aktiviert]**, um den Agenten zu aktivieren.
1. Tippen Sie auf **[!UICONTROL OK]**.
1. Tippen Sie in AEM auf **[!UICONTROL Tools > Allgemein > CRXDE Lite]**.
1. Navigieren Sie in der Ordnerstruktur auf der linken Seite zu `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters` .
1. Suchen Sie nach [!UICONTROL filter-video], klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Kopieren]**.
1. Navigieren Sie in der Ordnerstruktur auf der linken Seite zu `/etc/replication/agents.author/publish` .
1. Suchen Sie nach [!UICONTROL jcr:content], klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Einfügen]**.

So wird für die AEM-Veröffentlichungsinstanz eingerichtet, dass das Video-Posterbild sowie die für die Wiedergabe erforderlichen Videometadaten bereitgestellt werden, während das Video selbst vom Dynamic Media Cloud Service bereitgestellt wird. Mit dem Filter werden auch das Originalvideo und statische Miniaturwiedergaben, die auf der Veröffentlichungsinstanz nicht benötigt werden, von der Replikation ausgeschlossen.

### Einrichten von Asset-Filtern für die Bildbearbeitung in Nicht-Produktions-Bereitstellungen {#setting-up-asset-filters-for-imaging-in-non-production-deployments}

Wenn Sie Dynamic Media für die Bilddarstellung in Bereitstellungen außerhalb der Produktion nutzen, können Sie mit diesen Schritten Asset-Filter für die Replikation einrichten:

1. Tippen Sie AEM auf das AEM Logo, um auf die globale Navigationskonsole zuzugreifen, und tippen Sie auf **[!UICONTROL Tools > Bereitstellung > Replikation > Agenten für Autor]**.
1. Tippen Sie auf der Seite „Agenten für Autor“ auf **[!UICONTROL Standardagent (Publish)]**.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Aktivieren Sie im Dialogfeld **[!UICONTROL Agenteneinstellungen]** auf der Registerkarte **[!UICONTROL Einstellungen]** die Option **[!UICONTROL Aktiviert]**, um den Agenten zu aktivieren.
1. Tippen Sie auf **[!UICONTROL OK]**.
1. Tippen Sie in AEM auf **[!UICONTROL Tools > Allgemein > CRXDE Lite]**.
1. Navigieren Sie in der Ordnerstruktur auf der linken Seite zu `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters` .

   ![image-2018-01-16-10-22-40-410](assets/image-2018-01-16-10-22-40-410.png)

1. Suchen Sie nach **[!UICONTROL filter-images]**, klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Kopieren]**.
1. Navigieren Sie in der Ordnerstruktur auf der linken Seite zu `/etc/replication/agents.author/publish` .
1. Suchen Sie **[!UICONTROL jcr:content]**, klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Erstellen > Knoten erstellen]** aus. Geben Sie den Namen `damRenditionFilters` des Typs `nt:unstructured` ein.
1. Suchen Sie [!UICONTROL `damRenditionFilters`], klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Einfügen]** aus.

Die AEM-Veröffentlichungsinstanz für die Bereitstellung der Bilder in Ihrer Umgebung, die nicht für die Produktion bestimmt ist, wird eingerichtet. Mit dem Filter werden auch das Originalbild und statische Wiedergaben, die auf der Veröffentlichungsinstanz nicht benötigt werden, von der Replikation ausgeschlossen.

>[!NOTE]
Wenn es für einen Autor viele verschiedene Filter gibt, muss jedem Agenten ein anderer Benutzer zugewiesen werden. Der Granite-Code erzwingt, dass pro Benutzer nur ein Filter angewendet wird. Deswegen sollten Sie für jeden eingerichteten Filter einen anderen Benutzer festlegen.
Wenn Sie mehr als einen Filter auf einem Server verwenden, z. B. einen Filter für die zu veröffentlichende Replikation und einen zweiten Filter für die s7delivery, müssen Sie sicherstellen, dass diesen beiden Filtern im Knoten **[!UICONTROL jcr:content]** eine andere **userId** zugewiesen ist. Sehen Sie sich das folgende Bild an:

![image-2018-01-16-10-26-28-465](assets/image-2018-01-16-10-26-28-465.png)

### Anpassen von Asset-Filtern für die Replikation {#customizing-asset-filters-for-replication}

Gehen Sie wie folgt vor, um Asset-Filter für die Replikation optional anzupassen:

1. Tippen Sie AEM auf das AEM Logo, um auf die globale Navigationskonsole zuzugreifen, und tippen Sie dann auf **[!UICONTROL Tools > Allgemein > CRXDE Lite]**.
1. Navigieren Sie in der linken Ordnerstruktur zu `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters` , um die Filter zu überprüfen.

   ![chlimage_1-511](assets/chlimage_1-511.png)

1. Zum Definieren des MIME-Typs für den Filter können Sie den MIME-Typ wie folgt ermitteln:

   Erweitern Sie in der linken Leiste **[!UICONTROL content > dam > &lt;`locate_your_asset` > jcr:content > metadata]** und suchen Sie dann in der Tabelle `dc:format`.

   Die folgende Grafik ist ein Beispiel für den Pfad eines Assets zu `dc:format`.

   ![chlimage_1-512](assets/chlimage_1-512.png)

   Beachten Sie, dass `dc:format` für das Asset `Fiji Red.jpg` `image/jpeg` ist.

   Damit dieser Filter für alle Bilder gilt, setzen Sie den Wert unabhängig vom Format auf `image/*`, wobei `*` ein regulärer Ausdruck ist, der auf alle Bilder eines beliebigen Formats angewendet wird.

   Damit der Filter nur auf Bilder vom Typ JPEG angewendet wird, geben Sie den Wert `image/jpeg` ein.

1. Definieren Sie, welche Ausgabedarstellungen Sie in die Replikation einbeziehen oder davon ausschließen möchten.

   Sie können die folgenden Zeichen verwenden, um einen Filtervorgang für die Replikation durchzuführen:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Zu verwendendes Zeichen</strong></td> 
   <td><strong>Filtern von Assets für die Replikation</strong></td> 
  </tr> 
  <tr> 
   <td>*</td> 
   <td>Platzhalterzeichen<br /> </td> 
  </tr> 
  <tr> 
   <td>+</td> 
   <td>Umfasst Assets für die Replikation.</td> 
  </tr> 
  <tr> 
   <td>-</td> 
   <td>Schließt Assets aus der Replikation aus.</td> 
  </tr> 
 </tbody> 
</table>

Navigieren Sie zu `content/dam/<locate_your_asset>/jcr:content/renditions`.

Die folgende Grafik ist ein Beispiel für die Wiedergabeformate eines Assets.

![chlimage_1-513](assets/chlimage_1-513.png)

Wenn Sie anhand des obigen Beispiels nur das PTIFF (Pyramid TIFF) replizieren möchten, geben Sie `+cqdam,*` ein, das alle Ausgabedarstellungen enthält, die mit `cqdam` beginnen. Im Beispiel ist diese Ausgabedarstellung `cqdam.pyramid.tiff`.

Wenn Sie nur das Original replizieren möchten, geben Sie `+original` ein.

## Konfigurieren von Dynamic Media-Bildserver-Einstellungen {#configuring-dynamic-media-image-server-settings}

Das Konfigurieren des Dynamic Media-Bildservers umfasst die Bearbeitung des Adobe CQ Scene7 ImageServer-Bundles und des Adobe CQ Scene7 PlatformServer-Bundles.

>[!NOTE]
Dynamic Media arbeitet standardmäßig [nach der Aktivierung](#enabling-dynamic-media). Sie können für Ihre Installation optional aber eine Feineinstellung verwenden, indem Sie den Dynamic Media-Bildserver so konfigurieren, dass er bestimmte Spezifikationen oder Anforderungen erfüllt.

**Voraussetzung**:  __ Stellen Sie vor dem Konfigurieren des Dynamic Media Image-Servers sicher, dass Ihre Windows-VM eine Installation der Microsoft Visual C++-Bibliotheken enthält. Diese Bibliotheken werden benötigt, um den Dynamic Media-Bildserver auszuführen. Sie können das [Microsoft Visual C++ 2010 Redistributable Package (x64) hier herunterladen](https://www.microsoft.com/de-de/download/details.aspx?id=26999).

**So konfigurieren Sie die Einstellungen für den Dynamic Media-Bildserver**:

1. Tippen Sie in der linken oberen Ecke von AEM auf **[!UICONTROL Adobe Experience Manager]** , um auf die globale Navigationskonsole zuzugreifen, und tippen Sie dann auf **[!UICONTROL Tools > Vorgänge > Web-Konsole]**.
1. Tippen Sie auf der Seite **[!UICONTROL Adobe Experience Manager Web Console Configuration]** auf **[!UICONTROL OSGi > Configuration]** , um alle Pakete aufzulisten, die derzeit in AEM ausgeführt werden.

   Die Dynamic Media-Bereitstellungsserver befinden sich unter den folgenden Namen in der Liste:

   * **[!UICONTROL Adobe CQ Scene7 ImageServer]**
   * **[!UICONTROL Adobe CQ Scene7 PlatformServer]**

1. Tippen Sie in der Liste der Bundles rechts neben **[!UICONTROL Adobe CQ Scene7 ImageServer]** auf das Symbol **[!UICONTROL Bearbeiten]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Adobe CQ Scene7 ImageServer]** die folgenden Konfigurationswerte fest:

   >[!NOTE]
   In den meisten Fällen ist keine Änderung der Standardwerte erforderlich. Wenn Sie jedoch die Standardwerte ändern, müssen Sie das Bundle neu starten, damit die Änderungen wirksam werden.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Eigenschaft</strong></td> 
   <td><strong>Standardwert</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>TcpPort.name</td> 
   <td><code><em>empty</em></code></td> 
   <td>Anschlussnummer für die Kommunikation mit dem ImageServer-Prozess. Der freie Port wird standardmäßig automatisch erkannt.</td> 
  </tr> 
  <tr> 
   <td>AllowRemoteAccess.name</td> 
   <td><code><em>empty</em></code></td> 
   <td><p>Der Remotezugriff auf den ImageServer-Prozess wird zugelassen bzw. nicht zugelassen. Wenn "false", überwacht der Bildserver nur localhost.</p> <p>In Externalizer-Standardeinstellungen, die auf den „localhost“ verweisen, muss die tatsächliche Domäne oder IP-Adresse der jeweiligen VM-Instanz angegeben werden. Der Grund dafür ist, dass der localhost möglicherweise auf das übergeordnete System der VM verweist.</p> <p>Domänen oder IP-Adressen für die VM müssen ggf. über einen Hostdateieintrag verfügen, damit die Auflösung selbst durchgeführt werden kann.</p> </td> 
  </tr> 
  <tr> 
   <td>MaxRenderRgnPixels</td> 
   <td>16 MPixel</td> 
   <td>Maximale Größe in Megapixeln, die gerendert werden.</td> 
  </tr> 
  <tr> 
   <td>MaxMessageSize</td> 
   <td>16 MB</td> 
   <td>Maximale Nachrichtengröße in MB, die bereitgestellt wird.</td> 
  </tr> 
  <tr> 
   <td>RandomAccessUrlTimeout</td> 
   <td>20</td> 
   <td>Timeout-Wert in Sekunden, wie lange der ImageServer darauf warten soll, dass JCR auf eine Kachelanforderung reagiert.</td> 
  </tr> 
  <tr> 
   <td>WorkerThreads</td> 
   <td>10</td> 
   <td>Anzahl von Workerthreads.</td> 
  </tr> 
 </tbody> 
</table>

1. Tippen Sie auf **[!UICONTROL Speichern]**.
1. Tippen Sie in der Liste der Bundles rechts neben **[!UICONTROL Adobe CQ Scene7 PlatformServer]** auf das Symbol **[!UICONTROL Bearbeiten]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Adobe CQ Scene7 Platform Server]** die folgenden Standardwertoptionen fest:

   >[!NOTE]
   Der Dynamic Media-Bildserver verwendet einen eigenen Datenträgercache für das Zwischenspeichern von Antworten. Der AEM-HTTP-Cache und der Dispatcher können nicht genutzt werden, um Antworten vom Dynamic Media-Bildserver zwischenzuspeichern.

   | **Eigenschaft** | **Standardwert** | **Beschreibung** |
   |---|---|---|
   | **[!UICONTROL Cache enabled]** | Aktiviert | Gibt an, ob der Cache für Antworten aktiviert ist.. |
   | **[!UICONTROL Cache roots]** | cache | Mindestens ein Pfad zu Ordnern des Caches für Antworten. Relative Pfade werden für den internen s7imaging-Bundle-Ordner aufgelöst. |
   | **[!UICONTROL Cache Max Size]** | 200000000 | Gibt die maximale Größe des Caches für Antworten in Byte an. |
   | **[!UICONTROL Cache Max Entries]** | 100000 | Maximale Anzahl der im Cache zulässigen Einträge. |

### Standardeinstellungen des Manifests {#default-manifest-settings}

Mit dem Standardmanifest können Sie die Standardwerte konfigurieren, die zum Generieren der Antworten für die Dynamic Media-Bereitstellung verwendet werden. Sie können die Qualität (JPEG-Qualität, Auflösung, Resampling-Modus), das Caching (Ablauf) optimieren und das Rendern von zu großen Bildern verhindern (defaultpix, defaultthumbpix, maxpix).

Der Speicherort der Standardmanifest-Konfiguration wird aus dem Standardwert für **[!UICONTROL Catalog root]** des **[!UICONTROL Adobe CQ Scene7 PlatformServer]**-Bundles übernommen. Standardmäßig befindet sich dieser Wert im folgenden Pfad unter **[!UICONTROL Tools > Allgemein > CRXDE Lite]**:

`/conf/global/settings/dam/dm/imageserver/`

![configimageservercrxdelite](assets/configimageservercrxdelite.png)

Sie können die Werte der Eigenschaften wie in der folgenden Tabelle beschrieben ändern, indem Sie neue Werte eingeben.

Wenn Sie alle Änderungen am Standardmanifest vorgenommen haben, tippen Sie oben links auf der Seite auf **[!UICONTROL Alle speichern]**.

Tippen Sie unbedingt auf die Registerkarte **[!UICONTROL Zugriffssteuerung]** (rechts neben der Registerkarte **[!UICONTROL Eigenschaften]**) und legen Sie dann die Zugriffssteuerungsberechtigungen für alle und Benutzer von dynamic-media-replication auf `jcr:read` fest.

![configeservercrxdeliteaccessControlList](assets/configimageservercrxdeliteaccesscontroltab.png)

Tabelle mit Manifesteinstellungen und deren Standardwerte:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Eigenschaft</strong></td> 
   <td><strong>Standardwert</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>bkgcolor</td> 
   <td>FFFFFF</td> 
   <td><p>Standard-Hintergrundfarbe. RGB-Wert, mit dem alle Bereiche des Antwortbildes gefüllt werden, die keine Bilddaten enthalten.</p> <p>Siehe auch <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html">BkgColor</a> in der Image-Serving-API.</p> </td> 
  </tr> 
  <tr> 
   <td>defaultpix</td> 
   <td>300,300</td> 
   <td><p>Standard-Ansichtsgröße. Der Server beschränkt die Größe der Antwortbilder auf diese Breite und Höhe, wenn bei der Anfrage die Größe nicht explizit durch die Werte wid=, hei= oder scl= festgelegt wird.</p> <p>Wird als zwei ganze Zahlen angegeben (0 oder höher), die durch ein Komma getrennt sind. Breite und Höhe in Pixel. Einer oder beide Werte können auf 0 festgelegt werden, um die Einschränkung aufzuheben. Gilt nicht für verschachtelte oder eingebettete Anforderungen.</p> <p>Siehe auch <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html">DefaultPix</a> in der Image-Serving-API.</p> <p>Normalerweise verwenden Sie aber eine Viewer-Vorgabe oder Bildvorgabe, um das Asset bereitzustellen. „defaultpix“ gilt nur für ein Asset, für das keine Viewer-Vorgabe oder Bildvorgabe verwendet wird.</p> </td> 
  </tr> 
  <tr> 
   <td>defaultthumbpix</td> 
   <td>100,100</td> 
   <td><p>Standardgröße für Miniaturansichten. Wird anstelle von „attribute::DefaultPix“ für Miniaturanforderungen (req=tmb) verwendet.</p> <p>Der Server beschränkt die Größe der Antwortbilder auf diese Breite und Höhe, wenn in einer Miniaturanforderung (req=tmb) die Anzeigegröße nicht explizit durch die Werte wid=, hei= oder scl= festgelegt wird.</p> <p>Wird als zwei ganze Zahlen angegeben (0 oder höher), die durch ein Komma getrennt sind. Breite und Höhe in Pixel. Einer oder beide Werte können auf 0 festgelegt werden, um die Einschränkung aufzuheben. </p> <p>Gilt nicht für verschachtelte oder eingebettete Anforderungen.</p> <p>Siehe auch <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html">DefaultThumbPix</a> in der Image-Serving-API. </p> </td> 
  </tr> 
  <tr> 
   <td>Ablauf</td> 
   <td>36000000</td> 
   <td><p>Standardeinstellung für Time-To-Live des Client-Caches. Bietet ein standardmäßiges Ablaufintervall für den Fall, dass ein bestimmter Katalogdatensatz keinen gültigen Wert für „catalog::Expiration“ (also den Ablauf des Katalogs) aufweist.</p> <p>Reelle Zahl, 0 oder höher. Anzahl von Millisekunden bis zum Ablauf seit der Generierung der Daten. Geben Sie „0“ an, wenn das Antwortbild immer sofort ablaufen soll. Hiermit wird das Client-Caching praktisch deaktiviert. Dieser Wert ist standardmäßig auf 10 Stunden festgelegt. Dies bedeutet, dass es bei der Veröffentlichung eines neuen Bildes zehn Stunden dauert, bis das alte Bild aus dem Cache des Benutzers entfernt wird. Wenden Sie sich an die Kundenunterstützung, wenn der Cache früher geleert werden soll.</p> <p>Siehe auch <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html">Expiration</a> in der Image-Serving-API.</p> </td> 
  </tr> 
  <tr> 
   <td>jpegquality</td> 
   <td>80</td> 
   <td><p>Standardattribute für JPEG-Verschlüsselung. Legt die Standardattribute von JPEG-Antwortbildern fest.</p> <p>Ganze Zahl und Flag, getrennt durch ein Komma. Der erste Wert liegt im Bereich 1 bis 100 und definiert die Qualität. Der zweite Wert kann „0“ für normales Verhalten oder „1“ sein, um anzugeben, dass das normalerweise von der JPEG-Kodierung genutzte RGB-Farbart-Downsampling deaktiviert werden soll.</p> <p>Siehe auch <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html">JpegQuality</a> in der Image-Serving-API.</p> </td> 
  </tr> 
  <tr> 
   <td>maxpix</td> 
   <td>2000,2000</td> 
   <td><p>Maximale Größe des Antwortbildes. Maximale Breite und Höhe des Antwortbildes, das an den Client zurückgegeben wird.</p> <p>Der Server gibt einen Fehler zurück, wenn eine Anfrage ein Antwortbild verursacht, dessen Breite oder Höhe größer als das Attribut::MaxPix ist.</p> <p>Siehe auch <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html">MaxPix</a> in der Image-Serving-API.</p> </td> 
  </tr> 
  <tr> 
   <td>resmode</td> 
   <td>SCHARF2</td> 
   <td><p>Standard-Resamplingmodus. Gibt die standardmäßigen Resampling- und Interpolationsattribute an, die für die Skalierung von Bilddaten verwendet werden sollen.</p> <p>Wird verwendet, wenn „resMode=“ in einer Anforderung nicht angegeben wird.</p> <p>Zulässige Werte sind BILIN, BICUB oder SHARP2.</p> <p>Enum. Festlegung für Interpolationsmodus: 2 für BILIN, 3 für BICUB oder 4 für SCHARF2. Verwenden Sie für die besten Ergebnisse die Zeichenfolge 2.</p> <p>Siehe auch <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html">ResMode</a> in der Image-Serving-API.</p> </td> 
  </tr> 
  <tr> 
   <td>resolution</td> 
   <td>72</td> 
   <td><p>Standardobjektauflösung. Bietet eine standardmäßige Objektauflösung, falls ein bestimmter Katalogdatensatz keinen gültigen Wert für „catalog::Resolution“ aufweist.</p> <p>Reelle Zahl, größer als 0. Wird normalerweise als Pixel pro Zoll ausgedrückt, aber es können auch andere Einheiten verwendet werden, z. B. Pixel pro Meter.</p> <p>Siehe auch <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-resolution.html">Resolution</a> in der Image-Serving-API.</p> </td> 
  </tr> 
  <tr> 
   <td>thumbnailtime</td> 
   <td>1 %,11 %,21 %,31 %,41 %,51 %,61 %,71 %,81 %,91 %</td> 
   <td>Diese Werte stellen einen Schnappschuss der Videowiedergabezeit dar und werden an <a href="https://encoding.com/">encoding.com</a> übergeben. Weitere Informationen finden Sie unter <a href="/help/assets/video.md#about-video-thumbnails">Informationen zu Videominiaturen</a>.</td> 
  </tr> 
 </tbody> 
</table>

## Konfigurieren des Farbmanagements für dynamische Medien {#configuring-dynamic-media-color-management}

Beim Farbmanagement für dynamische Medien können Sie die richtigen Assets für die Vorschauanzeige farbig markieren.

Bei der Farbkorrektur behalten übernommene Assets ihren Farbraum (RGB, CMYK, Grau) und das eingebettete Farbprofil im generierten Pyramid TIFF-Wiedergabeformat bei. Wenn Sie eine dynamische Wiedergabe anfordern, wird die Bildfarbe gemäß dem Zielfarbraum korrigiert. Sie konfigurieren das Wiedergabefarbprofil in JCR in den Veröffentlichungseinstellungen für dynamische Medien.

Für das Adobe-Farbmanagement werden ICC-Profile verwendet. Dieses Format wurde vom International Color Consortium (ICC) definiert.

Sie können das Farbmanagement für dynamische Medien und Bildvorgaben konfigurieren, indem Sie eine CMYK-, RGB- oder Graustufen-Wiedergabe verwenden. Siehe [Konfigurieren von Bildvorgaben](managing-image-presets.md).

Für erweiterte Anwendungsfälle kann der Modifikator **[!UICONTROL icc=]** für die manuelle Konfiguration verwendet werden, um explizit ein Wiedergabefarbprofil auszuwählen:

* **[!UICONTROL icc]**  -  [Profil der Ausgabefarben.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-icc.html)

* **[!UICONTROL iccEmbed]**  - Farbprofil  [einbetten.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-iccembed.html)

>[!NOTE]
Der Standardsatz mit Adobe-Farbprofilen ist nur verfügbar, wenn [Feature Pack 12445 von Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-12445) installiert ist. Alle Feature Packs und Service Packs sind unter [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar. Feature Pack 12445 enthält die Adobe-Farbprofile.

### Installieren von Feature Pack 12445 {#installing-feature-pack}

Sie müssen Feature Pack 12445 installieren, um die Funktionen für das Farbmanagement dynamischer Medien nutzen zu können.

**Gehen Sie wie folgt vor, um Feature Pack 12445 zu installieren**:

1. Navigieren Sie zu [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) und laden Sie `cq-6.3.0-featurepack-12445` herunter.

   Weitere Informationen zur Verwendung von Paketen in [!DNL Adobe Experience Manager] finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md) .

1. Installieren Sie das Feature Pack.

### Konfigurieren der Standardfarbprofile {#configuring-the-default-color-profiles}

Nach der Feature Pack-Installation müssen Sie die richtigen Standardfarbprofile konfigurieren, um die Farbkorrektur beim Anfordern von RGB- oder CMYK-Bilddaten zu ermöglichen.

**Gehen Sie wie folgt vor, um die Standardfarbprofile zu konfigurieren**:

1. Navigieren Sie unter **[!UICONTROL Tools > Allgemein > CRXDE Lite]** zu `/conf/global/settings/dam/dm/imageserver/configuration/settings` , das die standardmäßigen Adobe Color-Profile enthält.

   ![chlimage_1-514](assets/chlimage_1-514.png)

1. Fügen Sie eine Farbkorrektureigenschaft hinzu, indem Sie am unteren Rand der Registerkarte **[!UICONTROL Properties]** scrollen und manuell den Eigenschaftsnamen, den Typ und den Wert eingeben, die in den folgenden Tabellen beschrieben werden. Tippen Sie nach Eingabe der Werte auf **[!UICONTROL Hinzufügen]** und dann auf **[!UICONTROL Alle speichern]** , um Ihre Werte zu speichern.

   Die Farbkorrektureigenschaften werden in der Tabelle **[!UICONTROL Farbkorrektureigenschaften]** beschrieben. Werte, die Sie Farbkorrektureigenschaften zuweisen können, sind in der Tabelle **[!UICONTROL Farbprofil]** angegeben.

   Fügen Sie beispielsweise **[!UICONTROL Name]** `iccprofilecmyk` hinzu, wählen Sie **[!UICONTROL Typ]** `String` und fügen Sie `WebCoated` als **[!UICONTROL Wert]** hinzu. Tippen Sie auf **[!UICONTROL Hinzufügen]** und dann auf **[!UICONTROL Alle speichern]**, um Ihre Werte zu speichern.

   ![chlimage_1-515](assets/chlimage_1-515.png)

   **Tabelle „Farbkorrektureigenschaften“**

   <table> 
    <tbody> 
      <tr> 
      <td><strong>Eigenschaft</strong></td> 
      <td><strong>Typ</strong></td> 
      <td><strong>Default</strong></td> 
      <td><strong>Beschreibung</strong></td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html">iccprofilergb</a></td> 
      <td>Zeichenfolge</td> 
      <td>&lt;leer&gt;</td> 
      <td>Name des standardmäßigen RGB-Profils.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html">iccprofilecmyk</a></td> 
      <td>Zeichenfolge</td> 
      <td>&lt;leer&gt;</td> 
      <td>Name des standardmäßigen CMYK-Farbprofils.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html">iccprofilegray</a></td> 
      <td>Zeichenfolge</td> 
      <td>&lt;leer&gt;</td> 
      <td>Name des standardmäßigen grauen Farbprofils.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcrgb.html">iccprofilesrcrgb</a></td> 
      <td>Zeichenfolge</td> 
      <td>&lt;leer&gt;</td> 
      <td>Name des standardmäßigen RGB-Farbprofils, das für RGB-Bilder ohne eingebettetes Farbprofil verwendet wird</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrccmyk.html">iccprofilesrccmyk</a></td> 
      <td>Zeichenfolge</td> 
      <td>&lt;leer&gt;</td> 
      <td>Name des standardmäßigen CMYK-Farbprofils, das für CMYK-Bilder ohne eingebettetes Farbprofil verwendet wird.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcgray.html">iccprofilesrcgray</a></td> 
      <td>Zeichenfolge</td> 
      <td>&lt;leer&gt;</td> 
      <td>Name des standardmäßigen grauen Farbprofils, das für CMYK-Bilder ohne eingebettetes Farbprofil verwendet wird.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccblackpointcompensation.html">iccblackpointpayment</a></td> 
      <td>Boolesch</td> 
      <td>True</td> 
      <td>Gibt an, ob während der Farbkorrektur eine Schwarzpunktersatzkompensation vorgenommen werden soll. Adobe empfiehlt, diese Option zu aktivieren.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccdither.html">iccdither</a></td> 
      <td>Boolesch</td> 
      <td>False</td> 
      <td>Gibt an, ob während der Farbkorrektur Dithering durchgeführt werden soll.</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html">iccrenderintent</a></td> 
      <td>Zeichenfolge</td> 
      <td>relative</td> 
      <td><p>Gibt die Rendering-Absicht an. Zulässige Werte sind: <strong>wahrnehmungsorientiert, relativ, Sättigung, absolut. </strong><i></i>Adobe empfiehlt <strong>relativ</strong><i></i> als Standard.</p> </td> 
      </tr> 
    </tbody> 
    </table>

   >[!NOTE]
   Bei Eigenschaftsnamen wird die Groß-/Kleinschreibung berücksichtigt und es dürfen nur Kleinbuchstaben verwendet werden.

   **Tabelle „Farbprofile“**

   Die folgenden Farbprofile werden installiert:

   <table> 
    <tbody> 
      <tr> 
      <th><p>Name</p> </th> 
      <th><p>Farbraum</p> </th> 
      <th><p>Beschreibung</p> </th> 
      </tr> 
      <tr> 
      <td>AdobeRGB</td> 
      <td>RGB</td> 
      <td>Adobe RGB (1998)</td> 
      </tr> 
      <tr> 
      <td>AppleRGB</td> 
      <td>RGB</td> 
      <td>Apple RGB</td> 
      </tr> 
      <tr> 
      <td>CIERGB</td> 
      <td>RGB</td> 
      <td>CIE RGB</td> 
      </tr> 
      <tr> 
      <td>CoatedFogra27</td> 
      <td>CMYK</td> 
      <td>Überzogene FOGRA27 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>CoatedFogra39</td> 
      <td>CMYK</td> 
      <td>Überzogene FOGRA39 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>CoatedGraCol</td> 
      <td>CMYK</td> 
      <td>Coated GRACoL 2006 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>ColorMatchRGB</td> 
      <td>RGB</td> 
      <td>ColorMatch RGB</td> 
      </tr> 
      <tr> 
      <td>EuropeISOCoated</td> 
      <td>CMYK</td> 
      <td>Europe ISO Coated FOGRA27</td> 
      </tr> 
      <tr> 
      <td>EuroscaleCoated</td> 
      <td>CMYK</td> 
      <td>Euroscale Coated v2</td> 
      </tr> 
      <tr> 
      <td>EuroscaleUngestrichen</td> 
      <td>CMYK</td> 
      <td>Euroscale Unbeschichtv2</td> 
      </tr> 
      <tr> 
      <td>JapanColorCoated</td> 
      <td>CMYK</td> 
      <td>Japan Color 2001 Coated</td> 
      </tr> 
      <tr> 
      <td>JapanColorNewspaper</td> 
      <td>CMYK</td> 
      <td>Japan Color 2002 Newspaper</td> 
      </tr> 
      <tr> 
      <td>JapanColorUnxed</td> 
      <td>CMYK</td> 
      <td>Japan Color 2001 Ungestrichen</td> 
      </tr> 
      <tr> 
      <td>JapanColorWebCoated</td> 
      <td>CMYK</td> 
      <td>Japan Color 2003 Web Coated</td> 
      </tr> 
      <tr> 
      <td>JapanWebCoated</td> 
      <td>CMYK</td> 
      <td>Japan Web Coated (Ad)</td> 
      </tr> 
      <tr> 
      <td>NewsprintSNAP2007</td> 
      <td>CMYK</td> 
      <td>US Newsprint (SNAP 2007)</td> 
      </tr> 
      <tr> 
      <td>NTSC</td> 
      <td>RGB</td> 
      <td>NTSC (1953)</td> 
      </tr> 
      <tr> 
      <td>PAL</td> 
      <td>RGB</td> 
      <td>PAL/SECAM</td> 
      </tr> 
      <tr> 
      <td>ProFoto</td> 
      <td>RGB</td> 
      <td>ProFoto RGB</td> 
      </tr> 
      <tr> 
      <td>PS4Default</td> 
      <td>CMYK</td> 
      <td>Photoshop 4-Standard-CMYK</td> 
      </tr> 
      <tr> 
      <td>PS5Default</td> 
      <td>CMYK</td> 
      <td>Photoshop 5-Standard-CMYK</td> 
      </tr> 
      <tr> 
      <td>SheetfedCoated</td> 
      <td>CMYK</td> 
      <td>U.S. Sheetfed Coated v2</td> 
      </tr> 
      <tr> 
      <td>BlattmatteUngestrichen</td> 
      <td>CMYK</td> 
      <td>U.S. Sheetfed Unbeschichtete Version 2</td> 
      </tr> 
      <tr> 
      <td>SMPTE</td> 
      <td>RGB</td> 
      <td>SMPTE-C</td> 
      </tr> 
      <tr> 
      <td>sRGB</td> 
      <td>RGB</td> 
      <td>sRGB IEC61966-2.1</td> 
      </tr> 
      <tr> 
      <td>UngestrichenFogra29</td> 
      <td>CMYK</td> 
      <td>Unbeschichtetes FOGRA29 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>WebCoated</td> 
      <td>CMYK</td> 
      <td>U.S. Web Coated (SWOP) v2</td> 
      </tr> 
      <tr> 
      <td>WebCoatedFogra28</td> 
      <td>CMYK</td> 
      <td>Web Coated FOGRA28 (ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>WebCoatedGrade3</td> 
      <td>CMYK</td> 
      <td>Webbeschichteter SWOP 2006 Grad 3 Papier</td> 
      </tr> 
      <tr> 
      <td>WebCoatedGrade5</td> 
      <td>CMYK</td> 
      <td>Webbeschichtetes SWOP 2006 Grade 5 Papier</td> 
      </tr> 
      <tr> 
      <td>WebUngestrichen</td> 
      <td>CMYK</td> 
      <td>U.S. Web Unxed v2</td> 
      </tr> 
      <tr> 
      <td>WideGamutRGB</td> 
      <td>RGB</td> 
      <td>Wide Gamut RGB</td> 
      </tr> 
    </tbody> 
    </table>

1. Tippen Sie auf **[!UICONTROL Alle speichern]**.

Sie können beispielsweise **[!UICONTROL iccprofilergb]** auf `sRGB` und **[!UICONTROL iccprofilecmyk]** auf `WebCoated` setzen. Dies hat folgende Auswirkungen:

* Die Farbkorrektur für RGB- und CMYK-Bilder wird aktiviert.
* Für RGB-Bilder ohne Farbprofil wird angenommen, dass sie sich im Farbraum `sRGB` befinden.
* Für CMYK-Bilder ohne Farbprofil wird angenommen, dass sie sich im Farbraum `WebCoated` befinden.
* Für dynamische Ausgabedarstellungen, bei denen eine RGB-Ausgabe zurückgegeben wird, erfolgt dies im Farbraum `sRGB`.
* Für dynamische Ausgabedarstellungen, bei denen eine CMYK-Ausgabe zurückgegeben wird, erfolgt dies im Farbraum `WebCoated`.

## Bereitstellen von Assets {#delivering-assets}

Nachdem Sie alle oben genannten Aufgaben ausgeführt haben, werden aktivierte Dynamic Media-Assets vom Bild- oder Videodienst bereitgestellt. In AEM wird diese Funktion in einer **[!UICONTROL Bild-URL kopieren]**, **[!UICONTROL Viewer-URL kopieren]**, **[!UICONTROL Viewer-Code einbetten]** und im WCM angezeigt.

Siehe [Bereitstellen von Assets mit Dynamic Media](delivering-dynamic-media-assets.md).

<table> 
 <tbody> 
  <tr> 
   <td><strong>Aktion</strong></td> 
   <td><strong>Ergebnis</strong></td> 
  </tr> 
  <tr> 
   <td>Kopieren einer Bild-URL</td> 
   <td><p>Im Dialogfeld URL kopieren wird eine URL wie die folgende angezeigt (URL dient nur zur Veranschaulichung):</p> <p><code>https://IMAGESERVICEPUBLISHNODE/is/image/content/dam/path/to/Image.jpg?$preset$</code></p> <p>Hier verweist <code>IMAGESERVICEPUBLISHNODE</code> auf die Bilddienst-URL.</p> <p>Weitere Informationen finden Sie unter <a href="/help/assets/delivering-dynamic-media-assets.md">Bereitstellen von Assets mit Dynamic Media</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Kopieren einer Viewer-URL</td> 
   <td><p>Im Dialogfeld URL kopieren wird eine URL angezeigt, die der folgenden ähnelt (URL dient nur zur Veranschaulichung):</p> <p><code>https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/BasicZoomViewer.html?asset=/content/dam/path/to/Image.jpg&amp;config=/conf/global/settings/dam/dm/presets/viewer/Zoom_dark&amp;serverUrl=https://IMAGESERVICEPUBLISHNODE/is/image/&amp;contentRoot=%2F</code></p> <p>Hier verweist <code>PUBLISHNODE</code> auf den regulären Veröffentlichungsknoten von AEM und <code>IMAGESERVICEPUBLISHNODE</code> auf die Bilddienst-URL.</p> <p>Weitere Informationen finden Sie unter <a href="/help/assets/delivering-dynamic-media-assets.md">Bereitstellen von Assets mit Dynamic Media</a>.</p> </td> 
  </tr> 
  <tr> 
   <td>Kopieren von Einbettungscode eines Viewers</td> 
   <td><p>Im Dialogfeld Einbettungscode kopieren wird ein Code-Snippet ähnlich dem folgenden angezeigt (Codebeispiel dient nur zur Veranschaulichung):</p> <p><code class="code">&lt;style type="text/css"&gt;
       #s7basiczoom_div.s7basiczoomviewer{
       width:100%;
       height:auto;
       }
       &lt;/style&gt;
       &lt;script
       type="text/javascript" src="https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/js/BasicZoomViewer.js"&gt;&lt;/script&gt;
       &lt;div id="s7basiczoom_div"&gt;&lt;/div&gt;
       &lt;script type="text/javascript"&gt;
       var s7basiczoomviewer = new s7viewers.BasicZoomViewer({
       "containerId" : "s7basiczoom_div",
       "params" : {
       "serverurl" : "https://IMAGESERVICEPUBLISHNODE/is/image/",
       "contenturl" : "https://PUBLISHNODE/",
       "config" : "/conf/global/settings/dam/dm/presets/viewer/Zoom_dark",
       "asset" : "/content/dam/path/to/Image.jpg" }
       }).init();
       &lt;/script&gt;</code></p> <p>Hier verweist <code>PUBLISHNODE</code> auf den regulären Veröffentlichungsknoten von AEM und <code>IMAGESERVICEPUBLISHNODE</code> auf die Bilddienst-URL.</p> <p>Weitere Informationen finden Sie unter <a href="/help/assets/delivering-dynamic-media-assets.md">Bereitstellen von Assets mit Dynamic Media</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

### Komponenten von dynamischen Medien und interaktiven Medien für WCM {#wcm-dynamic-media-and-interactive-media-components}

Auf WCM-Seiten mit Verweisen auf Komponenten von dynamischen Medien und interaktiven Medien wird auf den Service für die Bereitstellung verwiesen.
