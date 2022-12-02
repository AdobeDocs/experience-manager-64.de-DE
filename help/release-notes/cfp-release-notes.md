---
title: AEM 6.4 Versionshinweise zum Cumulative Fix Pack
description: Spezifische Versionshinweise für Adobe Experience Manager 6.4 Cumulative Fix Packs.
contentOwner: AK
mini-toc-levels: 1
exl-id: a63e77a3-da48-4072-bc75-c4c41a2f62a3
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '4681'
ht-degree: 37%

---

# AEM 6.4 Versionshinweise zum Cumulative Fix Pack {#aem-cumulative-fix-pack-release-notes}

## Versionshinweise {#release-information}

<!-- TBD: Update the SD URL. -->

| Produkte | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.4 |
| Typ | Cumulative Fix Pack |
| Datum | 25. Februar 2021 |
| Voraussetzung | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| Download-URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) |

## Was ist in AEM 6.4.8.4 enthalten? {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.4 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 mehrere interne und kundenspezifische Korrekturen enthält.

AEM 6.4.8.4 ist ein Cumulative Fix Pack (CFP), das von AEM 6.4 Service Pack 8 abhängig ist. Installieren Sie CFP nach der Installation von AEM 6.4 Service Pack 8.

Die wichtigsten Funktionen und Verbesserungen, die in [!DNL Adobe Experience Manager] 6.4.8.4 eingeführt wurden, sind:

* Möglichkeit, die [!DNL Experience Manager Forms] Registrierungsänderungen beim Ausführen einer PDFG-Konvertierung.

* Authentifizierung für SOAP-basierte Webdienste im Formulardatenmodell durch X-509-Zertifikat.

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.24 aktualisiert.

Informationen zu CFP und anderen Veröffentlichungstypen finden Sie unter [AEM Update der Versionsdefinitionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.4 bietet Fehlerbehebungen für die folgenden Probleme.

### Sites {#sites-6484}

* Nach der Installation von Experience Manager Service Pack 6.4.8.2 können Benutzer Inhaltsfragmentmodelle nicht bearbeiten. Der folgende Fehler tritt auf:

   `Uncaught TypeError: Cannot read property 'debounce' of undefined` (NPR-35312)
* Wenn ein Benutzer auf die Abmelde-Schaltfläche klickt, wird der Benutzer nicht von Package Manager abgemeldet. (NPR-35161)
* Nach dem Upgrade von Experience Manager 6.4.x auf Experience Manager 6.4.8.3 können Benutzer eine Seite nicht über Veröffentlichung verwalten veröffentlichen. (CQ-4312511)
* Wenn Sie eine untergeordnete Blueprint-Seite zurück an den ursprünglichen Speicherort verschieben, wird die Konfiguration cq:liveSyncConfig nicht von einer untergeordneten Live Copy-Seite entfernt. (NPR-35900)
* Wenn Sie einen Blueprint mit Live Copies hin und her verschieben, funktioniert nur der erste Schritt, dann schlägt er fehl und es wird keine Fehlermeldung angezeigt. (NPR-35899)


### [!DNL Assets] {#assets-6484}

* `IndexWriter.merge` verursacht `OutOfMemoryError` Fehler, da die Smart-Tagging-Funktion große `/oak:index/lucene` und `/oak:index/ntBaseLucene` Indizes (NPR-35650).
* Benutzende können keine Assets einchecken, nachdem sie diese in [!DNL Adobe InDesign] bearbeitet haben, und erhalten einen Fehler wegen fehlender Berechtigungen (NPR-35340).
* Wenn nach dem Auflösen des Namenskonflikts eine neue Version eines vorhandenen Assets erstellt wird, werden die Metadaten des ursprünglichen Assets überschrieben. (NPR-35939)
* Automatisch generierte private Ordner werden nicht beibehalten und nicht entfernt, wenn der Ordner gelöscht oder der Ordner mit der [!UICONTROL Entfernen von Einschränkungen für private Ordner] Optionssatz (NPR-35625).

#### [!DNL Dynamic Media] {#dynamic-media}

* Der zeitweise auftretende ImageServer-Fehler verursacht eine 403-Antwort für einige Funktionen von [!DNL Experience Manager]. (CQ-4308565)

### Integrationen {#integrations-6484}

* Wenn Sie die Eigenschaften einer Seite nach dem Upgrade auf Experience Manager 6.4.8.3 öffnen, treten in der Konsole JavaScript-Fehler auf (NPR-35649).

### Formulare {#forms-6484}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Cumulative Fix Packs.

**Korrespondenzverwaltung**

* Wenn Sie einen Brief bearbeiten, dauert das Laden der Module mit Bedingungen länger (NPR-35326).

* Beim Bearbeiten eines Briefs werden die Inhalte und Datenbindungen nicht auf der Benutzeroberfläche angezeigt (CQ-4312905).

**Document Services**

* PDF können nach der Aktualisierung nicht zusammengestellt werden [!DNL JAVA] nach [!DNL JDK1.8.0_261] (NPR-35761, NPR-35848).

**Foundation JEE**

* Beim Bearbeiten einer Aufgabenbenachrichtigung in [!DNL Forms] nicht speichern können (CQ-4315055).

**Behobene Probleme in AEMForms-6.4.0-0027**

* (Nur JEE) Kritische Sicherheitslücken (CVE-2021-44228 und CVE-2021-45046), die für Apache Log4j2 gemeldet wurden.

Informationen zu Sicherheitsaktualisierungen finden Sie auf der [Seite mit Sicherheitsbulletins für Experience Manager](https://helpx.adobe.com/de/security/products/experience-manager.html).

## Hotfixes und Feature Packs, die in früheren Cumulative Fix Packs enthalten waren {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.3 {#experience-manager-6483}

AEM Cumulative Fix Pack 6.4.8.3 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 mehrere interne und kundenspezifische Korrekturen enthält.

AEM 6.4.8.3 ist ein Cumulative Fix Pack (CFP), das von AEM 6.4 Service Pack 8 abhängig ist. Installieren Sie CFP nach der Installation von AEM 6.4 Service Pack 8.

In AEM 6.4.8.3 wird das integrierte Repository (Apache Jackrabbit Oak) auf Version 1.8.23 aktualisiert.

Informationen zu CFP und anderen Veröffentlichungstypen finden Sie unter [AEM Update der Versionsdefinitionen](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.3 bietet Fehlerbehebungen für die folgenden Probleme.

#### Sites {#sites-6483}

* Wenn Sie den Text einer Variante eines Inhaltsfragments aktualisieren, wird der Inhalt des Übergeordneten Inhaltsfragments anstelle der Variante aktualisiert (NPR-35080).

* Wenn Sie einen numerischen Wert für die Beschriftungseigenschaft des Typs Zeichenfolge einer Komponente festlegen, die Komponente löschen und die Rückgängig-Option verwenden, um sie wiederherzustellen, ändert sich der Typ der Beschriftungseigenschaft automatisch von String in Long (NPR-34738).

* Wenn Sie eine Datei-Upload-Komponente zu mehreren Feldern hinzufügen, wird der Bildpfad im Komponentenknoten statt im Knoten Multi-Field gespeichert (NPR-34423).

* Im Assistenten Seite verschieben bleibt die nächste Schaltfläche aktiviert, auch wenn kein Ziel ausgewählt ist (NPR-34460).

* Wenn die übergeordnete Komponente die `cq:isContainer` -Eigenschaft, enthält die geerbte Komponente nicht automatisch die Eigenschaft (CQ-4308409).

* Wenn Sie die CSS-Minimierung mit `calc()` -Funktion die Leerzeichen um die `+` -Zeichen werden entfernt (NPR-34991).

* Wenn Sie eine AEM Instanz starten, wird die `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` und `com.adobe.granite.maintenance.impl.TaskScheduler` Komponenten werden nicht in `Active` state (NPR-34952).

#### [!DNL Assets] {#assets-6483}

* Beim Erstellen einer Version eines vorhandenen Assets wird das Benutzer-Update auf Metadaten nicht beibehalten, wenn ein Metadatenprofil auf den Ordner angewendet wird (NPR-34833).
* Bei Verwendung von [!DNL Adobe Asset Link] mit [!DNL Adobe InDesign], enthalten die Suchergebnisse keine Ordner und Sammlungen, sondern nur Assets (NPR-34700).
* Wenn Sie ein Asset auf einen Ordner ziehen, um es zu verschieben, zeigt die Benutzeroberfläche auch die Optionen [!UICONTROL In Lightbox ablegen] und [!UICONTROL In Sammlung ablegen] an. Selbst wenn der Verschiebungsvorgang abgebrochen wird, zeigt die Benutzeroberfläche weiterhin die beiden letztgenannten Optionen an (NPR-34525).
* Wenn die Benutzeroberfläche Veröffentlichung verwalten geöffnet ist, ist die Veröffentlichungsoption nicht verfügbar und bei Auswahl der Option Veröffentlichung rückgängig machen ist die Seite mit dem Umfang leer (CQ-4302509).

##### [!DNL Dynamic Media] {#dynamic-media-6483}

* Wenn die Option in den Bildvorgabeneinstellungen [!UICONTROL JPG Chrominanz-Downsampling aktivieren] ist deaktiviert in [!DNL Experience Manager], synchronisiert die Änderung nicht mit [!DNL Dynamic Media] (NPR-34284).
* Im [!UICONTROL Viewer-Vorgabeneditor] ist beim Bearbeiten der [!UICONTROL PanoramicImage/PanoramicImage_VR]-Vorgaben in der `PanoramicView`-Komponente die `PANORAMICVIEW_AUTOROTATE`-Modifikatorbeschriftung nicht verfügbar (CQ-4302043).
* Rückgängigmachen der Veröffentlichung eines Videos aus [!DNL Experience Manager] Veröffentlichung des adaptiven Videosets in konfigurierter Dynamic Media Classic wird nicht rückgängig gemacht. (CQ-4304405).

#### Platform {#platform-6483}

* Die `emitUseStrict` Markierung wird der Funktion Google Closure Compiler (GCC) Processor hinzugefügt `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`. Das Flag unterdrückt die Ausgabe der `use strict` Anweisung (NPR-34830).
* A `NullPointerException` wird beim Start täglicher oder wöchentlicher Wartungsaufgaben zurückgegeben (NPR-34702).
* Die [!DNL Apache Sling Health Check] nicht mehr unterstützt. Verwenden Sie stattdessen [Musterdetektor](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html?lang=de) zur Erkennung von Inhaltsverletzungen (NPR-33929).

#### Integrationen {#integrations-6483}

* Die [!UICONTROL Erstellen] -Schaltfläche angezeigt [!UICONTROL Zielgruppen] Seite beim Navigieren von einem Ordner zum [!UICONTROL Zielgruppen] Seite (NPR-35152).

#### Benutzeroberfläche {#ui-6483}

* Die [!UICONTROL Filter] Suchbereich in [!UICONTROL Omnisearch] Die Benutzeroberfläche gibt auch Ergebnisse von anderen Orten zurück als von wo die Suche ausgeführt wird (NPR-34877).
* Beim Schließen der [!UICONTROL Filter] Bedienfeld auf [!UICONTROL Omnisearch] -Benutzeroberfläche wird die linke Leiste nicht auf [!UICONTROL Inhalt] Auswahl, die verhindert, dass die [!UICONTROL Filter] panel (NPR-34483).
* A `NullPointerException` wird beim Zugriff auf die Seiteneigenschaften zurückgegeben (NPR-34509).

#### Communities {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* Alle Fälle von ungerechter Terminologie im Produkt wurden durch akzeptable Äquivalente ersetzt (NPR-34506).

#### Commerce  {#commerce-6483}

* Wenn eine Kollektion mehr als 15 Produkte enthält, zeigt die Kollektion nur die ersten 15 Produkte an (NPR-34494).

#### Formulare {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Cumulative Fix Packs.

>[!NOTE]
>
>[!DNL Experience Manager] Das Cumulative Fix Pack enthält keine Korrekturen für [!DNL Experience Manager Forms]. Diese werden im Rahmen eines separaten Add-on-Pakets für [!DNL Forms] bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für [!DNL Experience Manager Forms] on JEE enthält. Weitere Informationen finden Sie unter [AEM Forms Add-On-Paket installieren](#install-aem-forms-add-on-package) und [Installieren des AEM Forms JEE-Installationsprogramms](#install-aem-forms-jee-installer).

**Adaptive Formulare**.

* Adaptive Formulare können nach dem Anwenden der [!DNL Experience Manager] Cumulative Fix Pack (NPR-35127).

* Das Laden von Fragmenten in einem adaptiven Formular dauert aufgrund der Cache-Invalidierung länger (NPR-34655).

* Barrierefreiheit: Die Registerkartennavigation funktioniert nicht ordnungsgemäß für Bildschirmlesehilfen in einem adaptiven Formular (NPR-34550).

**Korrespondenzverwaltung**

* Wenn Sie Assets aus ES3 migrieren, enthalten die Assets zwei nicht bearbeitbare Standardbedingungen (NPR-34971).

**Foundation JEE**

* Migrieren [!DNL AEM Forms] Benutzer von Flash zu HTML (CQ-4304075).

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM Cumulative Fix Pack 6.4.8.2 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 mehrere interne und kundenspezifische Korrekturen enthält.

AEM 6.4.8.2 ist ein Cumulative Fix Pack (CFP), das von AEM 6.4 Service Pack 8 abhängig ist. Installieren Sie CFP nach der Installation von AEM 6.4 Service Pack 8.

In AEM 6.4.8.2 wird das integrierte Repository (Apache Jackrabbit Oak) auf Version 1.8.22 aktualisiert.

Informationen zu CFP und anderen Veröffentlichungstypen finden Sie unter [AEM Update der Versionsdefinitionen](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.2 bietet Fehlerbehebungen für die folgenden Probleme.

#### Sites {#sites-6482}

* Wenn `RolloutConfigManagerFactoryImpl` keine Rollout-Konfiguration laden kann, wird nicht versucht, die fehlenden Konfigurationen zu laden. Stattdessen werden die zwischengespeicherten Konfigurationen zurückgegeben (NPR-34091).
* Nach Verwendung der Bearbeitungsoption „Quell-HTML-bearbeiten“ in der Text-Kernkomponente wird die Klasse aus dem `em`-Tag entfernt (NPR-34080).
* Wenn Sie von Experience Manager 6.2 auf Experience Manager 6.5 aktualisieren, wird die Parsys-Komponente statischer Vorlagen nicht korrekt angezeigt. Die Höhe der Parsys-Komponente ist auf 0 festgelegt und die darin enthaltenen Komponenten sind nicht sichtbar (NPR-34044).
* Die Beschriftungsinformationen der zulässigen Komponenten werden im Vorlageneditor nicht angezeigt (NPR-33908).

   ![Fehlende Beschriftungen im Layout-Container](assets/33908_missing_labels.png)

* Benutzer können nach der vierten Ebene verschachtelter Komponenten keine Komponenten zum parsys hinzufügen oder bearbeiten (NPR-33873).
* Wenn der anfängliche Inhalt einer bearbeitbaren Vorlage geändert und die Vorlage veröffentlicht wird, zeigen alle neuen Seiten, die mit dieser Vorlage erstellt wurden, das Veröffentlichungsdatum der Vorlage an, auch wenn die Seiten nicht veröffentlicht werden (NPR-33822).
* Die Eigenschaften `cq:acLinks` und `cq:acUUID` für [!DNL Adobe Campaign] auf der Kopie werden beim Kopieren und Einfügen entfernt (NPR-33793).
* Im [!UICONTROL Live-Nutzung] angezeigt, werden nur 49 Ergebnisse angezeigt. Es wird nicht die gesamte Verwendung für die Komponente angezeigt (NPR-33710).
* Eine Webseite mit `/` -Zeichen in der URL reagiert beim Authoring nicht mehr. Wenn beim Authoring eine Komponente hinzugefügt wird, erhöht sich die CPU-Auslastung und der Browser reagiert nicht mehr (NPR-33625).
* Im Inline-Bearbeitungsmodus in [!DNL RTE] funktioniert das Ziehen eines Bildes für die Textkomponente nicht (NPR-33579).
* Es ist möglich, in einer Blueprint-Seite eine Komponente mit demselben Namen wie die Seite zu erstellen. Während des Rollouts wird eine solche Komponente durch Nachfüllen umbenannt `_msm_moved`. Die Komponente wird jedoch an das Ende der [!UICONTROL Absatzsystem] (NPR-33534).
* Die Launch-Promotion veröffentlicht keine Seiten, wenn [!UICONTROL Unterseiten einschließen] -Eigenschaft nicht im ersten Inhaltsstamm überprüft (NPR-33533).
* Das Weiterleiten an eine [!DNL Experience Manager]-Seite mit Anker funktioniert in der Autoreninstanz nicht, da `PageRedirectServlets` eine Abfragezeichenfolge hinter einem URL-Fragment oder Anker einfügt (NPR-34287).
* `PageRedirectServlet` appends `.html` nach der Sling-Zuordnung, die zu Link-Fehlern führte (NPR-34271).
* Sie können die [!DNL Live Copy] einer Seite aufheben. Die Vererbung wird beschädigt, wie im Editor-Modus angezeigt. In den Seiteneigenschaften zeigt das Symbol für Vererbung jedoch fälschlicherweise an, dass die Vererbung vorhanden und nicht beschädigt ist (NPR-34096).
* Problem mit der Anzeige der zulässigen Komponenten auf der Seite Vorlage bearbeiten (CQ-4297295).
* Nach dem Upgrade von Chrome und Firefox funktionieren die Popup-Menüs nicht erwartungsgemäß. Beim Laden der Seiteneigenschaften wird das Bedienfeld nicht angezeigt, wenn darin Daten enthalten sind. (CQ-4292995)
* Mehrere Cross-Site-Scripting-Instanzen in [!DNL Experience Manager Sites]-Komponenten (NPR-33926).
* Benutzereingaben werden beim Senden von Informationen an den Client für verschiedene Komponenten nicht angemessen kodiert (NPR-33696).
* Eine URL, die auf `childrenlist.html` endet, zeigt anstelle einer „404-Seite“ eine HTML-Seite an. Solche URLs sind anfällig für Cross-Site-Scripting (NPR-33441).

#### Assets {#assets-6482}

* Die Textextraktion für die hochgeladenen PDF-Dateien funktioniert nicht und die Volltextsuche nach einigen in einer PDF-Datei kann diese PDF-Datei nicht abrufen (NPR-34165).

   >[!NOTE]
   >Damit diese Korrektur funktioniert, starten Sie die Adobe Experience Manager-Instanz nach der Installation des Service Packs 6.4.8.2 neu.

* In Suchvorschlägen für Assets, deren Name Sonderzeichen enthält, werden Backslashes vor Sonderzeichen hinzugefügt (NPR-33833).

* Die benutzerdefinierten Filter, die als Smart-Sammlungen gespeichert werden, werden nicht korrekt auf Assets angewendet. Daher sind die Suchergebnisse nicht korrekt (NPR-33725).

* Die Zeitleiste eines Assets in einem Ordner, der neu angeordnet wurde, zeigt an, dass das Asset verschoben wurde (NPR-33580).

* Rückgängigmachen der Veröffentlichung von Assets in Batches [!DNL Brand Portal] führt zu `Request-URI Too Long` Fehler (NPR-34158).

* In der Spaltenansicht, wenn der Benutzer [!UICONTROL Filter] nach Auswahl eines Sets von Assets (die Assets werden nicht ausgewählt) und dann einen anderen Satz von Assets zum Verschieben ausgewählt, werden die zuvor ausgewählten Assets ebenfalls an den neuen Speicherort verschoben (NPR-34018).

* Die Bildlaufleiste ist in der Listenansicht nicht sichtbar, selbst wenn zahlreiche Assets auf die Seite passen (NPR-34156).

* Die [!UICONTROL Veröffentlichung verwalten] -Seite für Assets ist fehlerhaft und die darin enthaltenen Optionen funktionieren nicht (CQ-4302509).

**Dynamic Media**

* Die Funktion für smartes Zuschneiden schlägt mit einem Fehler fehl, wenn einem Ordner mit mehreren Seitenverhältnissen (z. B. 11) ein Bildprofil hinzugefügt wird (NPR-34083).

* Änderungen an Bildvorgaben in [!UICONTROL Adobe Experience Manager] nicht mit Dynamic Media Classic synchronisieren (NPR-34284, CQ-4299713).

* Die [!UICONTROL PANORAMICVIEW_AUTOROTATE] -Modifikatorbeschriftung fehlt in der [!UICONTROL Verhalten] Registerkarte in [!UICONTROL Viewer-Vorgabeneditor] Seite (CQ-4302043).

#### Plattform {#platform-6482}

* Die Standardwerte für die Einstellungen **[!UICONTROL Verbindungs-Timeout]** und **[!UICONTROL Socket-Timeout]** für die Konfiguration des Standardagenten (Veröffentlichungsinstanz) sind nicht angegeben (NPR-33708).
* Der Planer für Wartungsaufgaben startet und beendet Wartungsaufgaben zu oft als konfiguriert (NPR-33520).
* Protokolle können nicht mit dem Diagnose-Tool auf eine aktualisierte Experience Manager-Instanz heruntergeladen werden (NPR-34419).

#### Integrationen {#integrations-6482}

* Der Wert von `library_path` wird bei der Generierung nicht berücksichtigt [!DNL Adobe Launch] Bibliotheks-URL für aus migrierte Bibliotheken [!DNL Adobe Dynamic Tag Management]. Außerdem verwenden die migrierten Bibliotheken ein anderes Präfix als [!DNL Adobe Launch] -Bibliotheken. (NPR-34238).
* Die von einem Cloud-Service geerbten Eigenschaften bleiben beim Aktualisieren der Seiteneigenschaften nicht erhalten (NPR-33865).

#### Benutzeroberfläche {#ui-6482}

* Die Anzeige der Anzahl ausgewählter Assets auf einer Suchseite ist falsch (NPR-33540).

#### Communities {#communities-6482}

* Vorhandene Benutzende einer Community-Gruppe, die über die Admin Console hinzugefügt wurden, werden bei jeder Änderung in der Community-Gruppenkonsole aus der Benutzerliste entfernt (NPR-34312).

#### Formulare {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] Das Cumulative Fix Pack enthält keine Korrekturen für [!DNL Experience Manager Forms]. Diese werden im Rahmen eines separaten Add-on-Pakets für [!DNL Forms] bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für [!DNL Experience Manager Forms] on JEE enthält. Weitere Informationen finden Sie unter [AEM Forms Add-On-Paket installieren](#install-aem-forms-add-on-package) und [Installieren des AEM Forms JEE-Installationsprogramms](#install-aem-forms-jee-installer).

**Adaptive Formulare**.

* Wenn ein adaptives Formularfragment fehlt, kann das adaptive Formular nicht gerendert werden (NPR-34303).

* In der Hilfebeschreibung für ein adaptives Formularfeld wird ein Absatz-HTML-Tag angezeigt (NPR-34117).

* Wenn Sie einen Forms-Container zu einem [!DNL Experience Manager Sites] -Seite, zeigt die Seite die folgende Fehlermeldung an und lässt das Hinzufügen neuer Komponenten nicht zu (NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Wenn Sie die **[!UICONTROL Auf dem Server erneut überprüfen]** -Eigenschaft und das Hochladen mehrerer Anlagen, kann das adaptive Formular nicht gesendet werden (NPR-33701).

* Wenn Sie die **[!UICONTROL Seitensprache verwenden]** und **[!UICONTROL Das Formular deckt die gesamte Breite der Seite ab]** Optionen in [!DNL Experience Manager Forms] -Komponente auf einer [!DNL Experience Manager Sites] -Seite nicht übersetzt werden kann (NPR-33641).

* Wenn Sie ein für Analysen aktiviertes adaptives Formular senden, das in ein [!DNL Experience Manager Sites] Seite, funktioniert Analytics nicht ordnungsgemäß (NPR-31359).

* Entfernte Abhängigkeiten von [!DNL Lodash] und [!DNL backbone] -Bibliotheken (NPR-33458).

* Die **[!UICONTROL An REST-Endpunkt übermitteln]** Sendeaktion funktioniert nicht für ein adaptives Formular (NPR-34513).

* Barrierefreiheit: Wenn Sie versuchen, ein adaptives Formular zu senden, ohne eine Anlage für ein Pflichtfeld hochzuladen, wird der Fokus nicht automatisch auf das Anlagenfeld verschoben (NPR-34511).

* Benutzereingaben werden für [!DNL Forms]-Komponenten beim Senden von Informationen an den Client nicht angemessen kodiert (NPR-33611).

**Workflow**

* Die Workflow-Bereinigung in [!DNL Experience Manager] schlägt fehl und zeigt die folgende Fehlermeldung an (NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Bei der Installation [!DNL Experience Manager] 6.4.8.1, die [!UICONTROL Aufgaben] Die Liste der Elemente wird nicht als Links angezeigt. Der Text für [!UICONTROL Aufgaben]-Elemente enthält HTML-Tags (NPR-34318).

**BackendIntegration**

* Formulardatenmodell kann nicht in einer gehosteten AWS konfiguriert werden [!DNL Experience Manager Forms Linux] Umgebung (NPR-33617).

**Designer**

* Wann [!DNL Acrobat DC] auf einer [!DNL Experience Manager] Forms-Server, der **[!UICONTROL Formular verteilen]** ist nicht verfügbar in [!DNL Experience Manager Designer] Version 6.x (NPR-34325).

**Document Security**

* Der Sign-Vorgang mit HSM-basierten Zertifikaten kann nach der Installation nicht in einer PDF-Datei ausgeführt werden [!DNL Experience Manager] 6.4.8.0 (NPR-34309).

**Aktualisierung**

* Wenn Sie die [!DNL JBoss] Version 7.0.9 für [!DNL Experience Manager Forms] mit Document Security in einer [!DNL Linux] -Umgebung einen Fehler verursacht (CQ-4300546).

Informationen zu Sicherheitsaktualisierungen finden Sie auf der [Seite mit Sicherheitsbulletins für Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 mehrere interne und kundenspezifische Korrekturen enthält.

AEM Cumulative Fix Pack 6.4.8.1 ist von AEM 6.4 Service Pack 8 abhängig. Daher müssen Sie das AEM Cumulative Fix Pack 6.4.8.1-Paket nach der Installation von AEM 6.4 Service Pack 8 installieren.

Zu den wichtigsten Highlights von AEM 6.4.8.1 gehören:

* Der anonyme Zugriff auf die CRXDE Lite ist zur Erhöhung der Sicherheit nicht zulässig. Stattdessen werden Benutzende zum Anmeldebildschirm weitergeleitet. Siehe [Entwicklung mit CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* Die Package Share-Integration mit Adobe Experience Manager wurde entfernt.
* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.21 aktualisiert.

Informationen zu CFP und anderen Veröffentlichungstypen finden Sie unter [AEM Update der Versionsdefinitionen](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.1 bietet Fehlerbehebungen für die folgenden Probleme.

#### Sites {#sites-6481}

* Anonyme Benutzer können auf CRX DE Lite-Funktionen zugreifen (NPR-33522).
* Wenn der Name einer lokalen Komponente in einer Live Copy mit dem Namen einer Komponente im Blueprint identisch ist und die Komponente aus dem Blueprint ausgerollt wird, wird der Begriff _msm_moved nicht zum Namen der lokalen Komponente hinzugefügt (NPR-33207).
* Die an die ursprüngliche Anfrage angehängten Parameter sind nicht in der Umleitungs-URL enthalten (NPR-33174).
* Wenn die Option Coral.Select den Wert emptyOption=true festlegt oder ein Standardelement mit dem Wert = &quot;&quot;enthält, tritt in der Datei dropdownshowhide.js ein Fehler auf: Uncaught TypeError: component.getValue ist keine Funktion (NPR-33163).
* Wenn eine Komponente eine andere Komponente als data-sly-resource enthält, wird der Platzhalter der übergeordneten Container-Komponente durch den Platzhalter für die inneren Komponenten ersetzt (NPR-33119).
* Wenn ein Inhaltsfragment auf einem Schema basiert und einen obligatorischen Textbereich oder ein Pfadfeld enthält, kann das Inhaltsfragment nicht gespeichert werden (NPR-33007)
* Wenn Sie eine benutzerdefinierte Komponente mit der vordefinierten Experience Fragment-Komponente erstellen und sie auf AEM Sites-Seiten verwenden, zeigt AEM keine Verweise (Verwendung) für die benutzerdefinierte Komponente an (NPR-32852).
* Wenn eine AEM Sites-Seite Teil eines großen Inhaltssatzes mit mehreren Live Copies ist, kann die Vorschau des Seitenversionsverlaufs nicht geladen werden. (NPR-32772)
* Wenn Sie einen Launch bewerben, wird das Mixin &quot;cq:LiveRelationship&quot;zu jeder im Launch hinzugefügten Komponente hinzugefügt. Er wirkt sich auf alle Launches aus, unabhängig davon, ob ein Launch mit oder ohne Auswahl der Option — Quellseiten-Live-Daten übernehmen — erstellt wird (NPR-32664).
* Beim Start der Paginierung lädt die Experience Fragments-Auswahl nicht alle Elemente (NPR-32605).
* Launch für eine AEM Sites-Seite kann nicht erstellt werden. Die Launch-Erstellung führt zu einem Fehler (NPR-32544).
* Veröffentlichung verwalten enthält keine referenzierten Assets im Aktivierungsanfrage-Workflow (NPR-32463).
* Die Dispatcher-Konsistenzprüfung zeigt in den Protokolldateien die Warnmeldung `Invalid cookie header` an (NPR-33630).
* Die Salesforce-Integration ist anfällig für SSRF (NPR-32671).
* XSS in PreferencesServlet (NPR-33439) dargestellt.

#### Assets {#assets-6481}

* Die Anzahl der Assets ändert sich nicht entsprechend der Änderung der Auswahl in der Listenansicht (NPR-33285).

* Die Schaltfläche Weiter ist nicht aktiviert, wenn der übergeordnete Knoten ausgewählt (wobei ein einzelner untergeordneter Ordner sichtbar ist) und anschließend der untergeordnete Ordner ausgewählt wird (NPR-33284).

* Die Touch-Benutzeroberfläche kann für Benutzer, die keinen Lesezugriff auf den Repository-Stammordner haben, nicht gerendert werden (mit Fehler), wenn der DMS7- oder Hybridmodus aktiviert ist (NPR-33175).

* Die GB18030-Zeichen, die in Ordnern und Asset-Namen vorkommen, werden in den heruntergeladenen ZIP-Dateien leer angezeigt (NPR-33150).

* Zusätzlicher Ordner wird beim smarten Zuschneiden eines Assets erstellt, das sich in einem übergeordneten Ordner mit Punkt befindet `.` in seinem Namen (NPR-32755).

* Das verzögerte Laden wird nicht ausgelöst und bei der Auswahl, die Aufgaben aus dem Benachrichtigungs-Posteingang zu überprüfen, werden nicht mehr als 100 Assets angezeigt. (NPR-32749)

* Die Linkseite für die Freigabe der Sammlung ist aufgrund von Änderungen in coral-info fehlerhaft (NPR-32510).

* Die Asset-Verarbeitung beim Massen-Upload wird blockiert (CQ-4293916).

* SSRF-Schwachstelle in Experience Manager (NPR-33437).

#### Plattform {#platform-6481}

* Der [!DNL Sling]-Filter wird nicht aufgerufen, wenn der Zuordnungseintrag `sling:match` unter `/etc/maps` erstellt wird (NPR-33308).
* Alle Flush-Agenten werden beim Deaktivieren einer Seite ausgelöst (NPR-32941).
* Wenn Sie `ScriptProcessor` API zum Minimieren einer JavaScript-Bibliothek anzeigen, zeigt die Protokolldatei eine Fehlermeldung an, die darauf hinweist, dass der JavaScript-Code nicht mit dem strikten Modus konform ist. Die API bietet keine Option zum Aktivieren oder Deaktivieren des strikten Modus. (NPR-32746).
* Wenn eine SQL-Abfrage länger ausgeführt wird, z. B. 7 Stunden, reagiert AEM nicht mehr (NPR-33043).

#### Benutzeroberfläche {#ui-6481}

* Wenn Sie einen Pfad mithilfe eines Auswahldialogfelds suchen oder durchsuchen, zeigt das Auswahldialogfeld alle Inhalte des ausgewählten JCR-Knotens an, anstatt nur die Bilder anzuzeigen (NPR-32712).

#### Übersetzungsprojekte {#tranlation-6481}

* Ein `NullPointerException`-Fehler tritt in den Protokollen beim Ausführen eines Übersetzungsauftrags auf (NPR-32220).

#### Integrationen {#integrations-6481}

* Cross-Site-Scripting für JSON (NPR-32745).

#### Communities {#communities-6481}

* Autoren werden nach dem Erstellen einer neuen Gruppe nicht zum Abschnitt [!UICONTROL Community-Gruppe] in [!DNL Internet Explorer] 11 weitergeleitet (NPR-33202).
* Beim Zugreifen auf die Seite [!UICONTROL Aktivitäts-Stream] tritt ein Fehler auf (NPR-33152).
* Beim Bearbeiten einer [!DNL Communities]-Gruppe und Ändern des Miniaturbilds wird das Miniaturbild der Gruppe nicht aktualisiert (NPR-32603).
* Beim Erstellen einer Version von Benachrichtigungen und Abonnements von nutzergenerierten Inhalten (User-Generated Content, UGC) wird eine falsche ID für die Quellseite gespeichert (, CQ-4289703).
* Problem mit Cross-Site-Scripting (NPR-33212).

#### Workflow {#workflow-6481}

* Einige Komponenten werden nicht im Dialogfeld angezeigt, das angezeigt wird, wenn ein Benutzer einen Workflow mit einer [!UICONTROL Schritt &quot;Dialogteilnehmer&quot;] (NPR-32989).

* Das Laden der Option [!UICONTROL Zeitleiste] in der linken Leiste dauert länger als erwartet (NPR-32850).

#### Formulare {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [AEM Forms Add-On-Paket installieren](#install-aem-forms-add-on-package) und [Installieren des AEM Forms JEE-Installationsprogramms](#install-aem-forms-jee-installer).

* Correspondence Management: Wenn ein Benutzer Inhalte aus einem [!DNL Word] -Dokument, behält das Textdokumentfragment keine Formatierung bei (NPR-33213).
* Adaptive Formulare: Durch eine neue Zeile in einer Zeichenfolge in einem Wörterbuch für adaptive Formulare werden die Zeichen `&#xa;` in das Wörterbuch eingefügt (NPR-33265).
* Adaptive Formulare: Benutzende können ein adaptives Formular nicht mit mehr als einem Anhang speichern (NPR-33214).
* Adaptive Forms: `AddInstance` und `RemoveInstance` Methoden für die Instanz-Manager-Klasse fügen keine dynamische Anzahl von Instanzen für verzögerte Ladefragmente hinzu in [!DNL Internet Explorer 11] (NPR-33201).
* Adaptive Forms: Analytics aktiviert für ein adaptives Formular, eingebettet in ein [!DNL Sites] -Seite keine Daten für die Ereignisse &quot;Senden&quot;und &quot;Abbrechen&quot;aufzeichnet (NPR-31359).
* Adaptive Forms: Wenn ein Benutzer den Inhalt aus einem [!DNL Word] Dokument in ein adaptives Formular übertragen und senden, enthält das gesendete adaptive Formular Unicode-Zeichen. Darüber hinaus schlägt die Konvertierung von PDF zu PDF/A aufgrund von Unicode-Zeichen fehl (NPR-33348).
* Backend-Integration: Formulardatenmodellanforderungen schlagen fehl, da das Aktualisierungs-Token aufgrund eines falschen inaktiven Status abläuft (NPR-33168).
* Document Services: Der PDF-Dienst kann PDF-Dokumente nicht in PostScript konvertieren, da Gibson-JARs für [!DNL WebLogic] auf [!DNL Linux] Server (NPR-33515, CQ-4292239).
* Document Services: Wenn ein Benutzer eine Textdatei in eine PDF konvertiert, werden japanische Zeichen nicht korrekt dargestellt (NPR-33239).
* XSS mit GuideSOMProviderServlet gespeichert (NPR-32701).

## Installieren von Version 6.4.8.4. {#install}

### Einrichtungsvoraussetzungen {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Für Kunden mit Feature Packs, die in AEM 6.4 installiert sind. Die von Adobe bereitgestellten optionalen Feature Packs hängen von der Release-Version und den Service Packs ab. Wenn Sie Feature Pack installiert haben, wenden Sie sich an das AEM Kundenunterstützungsteam, um die Kompatibilität dieser Feature Packs mit diesem kumulativen Fixpack für AEM 6.4 zu überprüfen.

* AEM 6.4.8.4 erfordert AEM 6.4.8.0. Bitte besuchen Sie [Upgrade-Dokumentation](../sites-deploying/upgrade.md) für detaillierte Anweisungen.
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.4.8.4 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Stellen Sie vor der Installation des Cumulative Fix Packs sicher, dass Sie einen Schnappschuss oder eine neue Sicherung Ihrer AEM-Instanz haben.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz gerade von einer früheren Version aktualisiert wurde). Dennoch wird dies allgemein empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!NOTE]
>
>Adobe rät davon ab, das AEM 6.4.8.4-Paket zu entfernen oder zu deinstallieren.

### Installieren Sie das kumulative Fix Pack {#install-cumulative-fix-pack}

Führen Sie die folgenden Schritte aus, um das Cumulative Fix Pack auf einer vorhandenen AEM 6.4.8.0-Instanz zu installieren:

1. Klicken Sie auf den Link [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip), um das Paket herunterzuladen.

1. Öffnen Sie [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.

1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird in einigen Fällen während der Installation von 6.4.8.4 frühzeitig beendet.**
>
>Es wird daher empfohlen, auf die Stabilisierung der Fehlerprotokolle zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles warten, bevor sichergestellt wird, dass die Installation erfolgreich ist. In der Regel trifft dies auf Safari zu, kann aber mitunter auch auf allen anderen Browsern der Fall sein.

### Automatische Installation {#auto-installation}

Es gibt zwei Möglichkeiten, AEM 6.4.8.4 automatisch in einer laufenden Instanz zu installieren:

A. Platzieren Sie das Paket in ..Ordner */crx-quickstart/install*, während der Server läuft. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](https://helpx.adobe.com/de/experience-manager/aem-previous-versions.html) - Stellen Sie sicher, dass Sie `cmd=install&recursive=true` - damit das verschachtelte Paket installiert wird.

>[!NOTE]
>
>AEM 6.4.8.4 unterstützt keine Bootstrap-Installation.

### Bestätigen der Installation {#validate-install}

1. Auf der Seite „Produktinformationen“ (*/system/console/productinfo*) sollte nun unter „Installierte Produkte“ die aktualisierte Versionszeichenfolge „Adobe Experience Manager, Version 6.4.8.4“ angezeigt werden.
1. Alle OSGI-Bundles sind in der OSGI-Konsole entweder AKTIV oder FRAGMENT. (Verwenden Sie die Web-Konsole: /system/console/bundles.)
1. Das OSGI-Bundle org.apache.jackrabbit.oak-core befindet sich auf Version 1.8.17 oder höher (Webkonsole verwenden: /system/console/bundles).

Informationen zur Ermittlung der zertifizierten Plattform für die Ausführung mit dieser Version von AEM Sites und Assets finden Sie unter [Technische Anforderungen](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Bei erfolgreicher Installation des Pakets wird eine Informationsmeldung angezeigt, die angibt, dass das Inhaltspaket erfolgreich installiert wurde, z. B. **&quot;Inhaltspaket AEM-6.4-Service-Pack-8 wurde erfolgreich installiert.&quot;**

### Aktualisieren von Dynamic Media-Viewern (5.10.1) {#update-dynamic-media-viewers}

AEM Version 6.4.8.4 enthält eine neue Version von Dynamic Media-Viewern (5.10.1), die die Überprüfung auf doppelte Namen auf der Seite Bildvorgabe ermöglicht. Dynamic Media-Kunden wird empfohlen, den folgenden Befehl auszuführen, um die standardmäßigen Viewer-Vorgaben in einen aktuellen Status zu versetzen.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

, wodurch neue Viewer-Vorgaben in den Speicherort /conf kopiert werden.

### Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten Veröffentlichungsdatum der [!DNL Experience Manager] Cumulative Fix Packs.

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in AEM Forms werden über ein separates Add-on-Paket bereitgestellt.

1. Stellen Sie sicher, dass Sie das AEM Cumulative Fix Pack installiert haben.
1. Laden Sie das entsprechende Formular-Add-On-Paket herunter, das unter [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de#forms-updates) für Ihr Betriebssystem.
1. Installieren Sie das Formular-Add-On-Paket wie unter [Installieren von Add-On-Paketen für AEM Formulare](https://experienceleague.adobe.com/docs/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installieren des AEM Forms JEE-Installationsprogramms {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in AEM Forms JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für AEM Forms JEE und zur Konfiguration nach der Bereitstellung finden Sie unter [AEM Forms JEE-Patch-Installationsprogramm](jee-patch-installer-64.md).

>[!NOTE]
>
>Nachdem Sie das kumulative Installationsprogramm für Experience Manager Forms on JEE installiert haben, installieren Sie das neueste Add-On-Paket für Forms, löschen Sie das Add-On-Paket für Forms aus dem Ordner `crx-repository\install` und starten Sie den Server neu.

### Uber Jar {#uber-jar}

Das Uber Jar für AEM 6.4.8.4 ist im Abschnitt [Maven Central Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.4/).

Informationen zur Verwendung von Uber Jar in einem Maven-Projekt finden Sie in [diesem Artikel](../sites-developing/ht-projects-maven.md). Beziehen Sie die folgenden Abhängigkeiten in Ihr Projekt-POM ein:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.4</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>UberJar und andere zugehörige Artefakte sind im Maven Central Repository anstelle des Adobe Public Maven-Repositorys (repo.adobe.com) verfügbar. Die UberJar-Hauptdatei wurde in `uber-jar-<version>.jar` umbenannt. Daher gibt es keine `classifier`, mit `apis` als Wert für die `dependency` -Tag.

## Entfernte/veraltete Funktionen {#removed-deprecated-features}

Dieser Abschnitt listet Funktionen und Fähigkeiten auf, die aus AEM 6.4 entfernt oder veraltet sind.

| Bereich | Funktion | Ersatz | Version |
|---|---|---|---|
| Assets | Tag-Aktion für Teil-Assets verwalten | Kein Ersatz vorhanden. | AEM 6.4.2.0 |
| Assets und Adobe Creative Cloud-Integration | [Die gemeinsame Nutzung von AEM-Ordnern in Creative Cloud](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) wurde in AEM 6.2 eingeführt, um Benutzern von Creative Cloud den Zugang zu den Assets von AEM zu ermöglichen. Eine neue Funktion des Creative Cloud-Programms, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus. Adobe wird die Ordnerfreigabe nicht weiter verbessern. Auch wenn die Funktion in AEM enthalten ist, wird den Kunden dringend empfohlen, den Ersatz zu verwenden. | Adobe Asset Link oder Desktop-Programm. Weitere Informationen finden Sie im Artikel zur [AEM Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Bekannte Probleme {#known-issues}

* Wenn Sie von [!DNL Experience Manager] 6.4 bis [!DNL Experience Manager] 6.5, zeigen einige Pakete möglicherweise ihren Status nicht als `Active`. Neueste Version installieren [!DNL Experience Manager] 6.5 Service Pack , um das Problem zu beheben.

Informationen zu den bekannten Problemen des AEM 6.4.8.0 Service Pack finden Sie unter [AEM 6.4.8.0 Service Pack - Versionshinweise](sp-release-notes.md).

## Enthaltene OSGi-Bundles und Inhaltspakete {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten sind die in AEM 6.4.8.4 enthaltenen OSGi-Pakete und Inhaltspakete aufgeführt.

Liste der in AEM 6.4.8.4 enthaltenen OSGi-Bundles

[Datei abrufen](assets/6.4.8.4_osgi_bundles.txt)

Liste der in AEM 6.4.8.4 enthaltenen Inhaltspakete

[Datei abrufen](assets/6.4.8.4_content_packages.txt)

## Hilfreiche Ressourcen {#helpful-resources}

* [AEM 6.4 – Versionshinweise](../release-notes/release-notes.md)
* [AEM-Produktseite](https://www.adobe.com/solutions/web-experience-management.html)
* [Dokumentation zu AEM 6.4](https://helpx.adobe.com/de/support/experience-manager/6-4.html)
* Abonnieren von [Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

## Eingeschränkte Sites {#restricted-sites-new}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Kundensupport.](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de)
