---
title: AEM 6.4 - Versionshinweise zur kumulativen Fehlerbehebung
description: Versionshinweise speziell für Adobe Experience Manager 6.4 Cumulative Fix Packs.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 3a8fefc8a580d41d327cf7acbf8e4b0440fea604
workflow-type: tm+mt
source-wordcount: '4432'
ht-degree: 11%

---


# AEM 6.4 Versionshinweise zu den insgesamt Fix Pack-Versionen {#aem-cumulative-fix-pack-release-notes}

## Versionshinweise {#release-information}

<!-- TBD: Update the SD URL. -->

| Produkte | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.4 |
| Typ | Cumulative Fix Pack |
| Datum  | 25. Februar 2021 |
| Voraussetzung | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| Download-URL | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) |

## Was ist in AEM 6.4.8.4 enthalten?{#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.4 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 mehrere interne und kundenspezifische Korrekturen enthält.

AEM 6.4.8.4 ist ein Cumulative Fix Pack (CFP), das von AEM 6.4 Service Pack 8 abhängig ist. Installieren Sie CFP nach der Installation von AEM 6.4 Service Pack 8.

In AEM 6.4.8.4 wird das integrierte Repository (Apache Jackrabbit Oak) auf Version 1.8.24 aktualisiert.

Weitere Informationen zu CFP und anderen Versionstypen finden Sie unter [AEM Definitionen für Versionshinweise aktualisieren](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html?lang=en)

In Adobe Experience Manager 6.4.8.4 wurden die folgenden Probleme behoben:

### Sites {#sites-6484}

* Nach der Installation von Experience Manager Service Pack 6.4.8.2 können die Benutzer keine Inhaltsfragmentmodelle bearbeiten, und es tritt der folgende Fehler auf:

   `Uncaught TypeError: Cannot read property 'debounce' of undefined` (NPR-35312)
* Wenn ein Benutzer auf die Schaltfläche zum Abmelden klickt, wird der Benutzer nicht aus Package Manager abgemeldet. (NPR-35161)
* Nach dem Upgrade von Experience Manager 6.4.x auf Experience Manager 6.4.8.3 können Benutzer eine Seite nicht über Veröffentlichung verwalten veröffentlichen. (CQ-4312511)
* Wenn Sie eine untergeordnete Blueprint-Seite wieder an den ursprünglichen Speicherort verschieben, wird die Konfiguration cq:liveSyncConfig nicht von einer untergeordneten Live Copy-Seite entfernt. (NPR-35900)
* Wenn Sie einen Entwurf verschieben, der Live-Kopien enthält, funktioniert nur der erste Schritt, dann schlägt er fehl und es wird keine Fehlermeldung angezeigt. (NPR-35899)


### [!DNL Assets] {#assets-6484}

* `IndexWriter.merge` verursacht  `OutOfMemoryError` Fehler, da intelligente Tagging-Funktionen große  `/oak:index/lucene` und  `/oak:index/ntBaseLucene` Indizes erstellen (NPR-35650).
* Benutzer können keine Assets einchecken, nachdem sie die unter [!DNL Adobe InDesign] bearbeitet haben, und erhalten einen Fehler wegen fehlender Berechtigungen (NPR-35340).
* Wenn nach dem Auflösen des Namenskonflikts eine neue Version eines vorhandenen Assets erstellt wird, werden die Metadaten des ursprünglichen Assets überschrieben (NPR-35939).
* Automatisch generierte Gruppen von privaten Ordnern werden beim Löschen des Ordners oder beim Aktualisieren des Ordners mit dem Optionssatz [!UICONTROL Beschränkungen für private Ordner entfernen] (NPR-35625) nicht beibehalten und nicht entfernt.

#### [!DNL Dynamic Media] {#dynamic-media}

* Der zeitweise auftretende ImageServer-Fehler verursacht 403 Antworten und einen anschließenden Fehler einiger Funktionen von [!DNL Experience Manager]. (CQ-4308565)

### Integrationen {#integrations-6484}

* Wenn Sie die Eigenschaften einer Seite nach einem Upgrade auf Experience Manager 6.4.8.3 öffnen, wird der Beginn für JavaScript-Fehler in der Konsole angezeigt (NPR-35649).

### Formulare {#forms-6484}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten  [!DNL Experience Manager] Cumulative Fix Pack-Veröffentlichungsdatum.

Informationen zu Sicherheitsaktualisierungen finden Sie unter [Seite mit Sicherheitsbulletins für Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## Hotfixes und Feature Packs, die in früheren Cumulative Fix Packs enthalten waren {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.3 {#experience-manager-6483}

AEM Cumulative Fix Pack 6.4.8.3 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 mehrere interne und kundenspezifische Korrekturen enthält.

AEM 6.4.8.3 ist ein Cumulative Fix Pack (CFP), das von AEM 6.4 Service Pack 8 abhängig ist. Installieren Sie CFP nach der Installation von AEM 6.4 Service Pack 8.

In AEM 6.4.8.3 wird das integrierte Repository (Apache Jackrabbit Oak) auf Version 1.8.23 aktualisiert.

Weitere Informationen zu CFP und anderen Versionstypen finden Sie unter [AEM Definitionen für Versionshinweise aktualisieren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

In Adobe Experience Manager 6.4.8.3 wurden die folgenden Probleme behoben:

#### Sites {#sites-6483}

* Wenn Sie den Text einer Variation eines Inhaltsfragments aktualisieren, wird der Inhalt des Fragments &quot;Übergeordnet content&quot;anstelle der Variation aktualisiert (NPR-35080).

* Wenn Sie einen numerischen Wert für die Eigenschaft mit der Beschriftung für den String-Typ einer Komponente festlegen, die Komponente löschen und die Rückgängig-Option verwenden, um sie wiederherzustellen, ändert sich der Typ der Eigenschaft label automatisch von String in Long (NPR-34738).

* Wenn Sie eine Datei-Upload-Komponente zu einem Multi-Field-Element hinzufügen, wird der Bildpfad im Komponentenknoten und nicht im Multi-Field-Knoten (NPR-34423) gespeichert.

* Im Assistenten &quot;Seite verschieben&quot;bleibt die nächste Schaltfläche aktiviert (NPR-34460), auch wenn kein Ziel ausgewählt ist.

* Wenn die übergeordnete Komponente die Eigenschaft `cq:isContainer` enthält, enthält die geerbte Komponente nicht automatisch die Eigenschaft (CQ-4308409).

* Wenn Sie die CSS-Minimierung mit der Funktion `calc()` verwenden, werden die Leerzeichen um das `+`-Zeichen entfernt (NPR-34991).

* Wenn Sie eine AEM-Instanz Beginn haben, werden die Komponenten `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` und `com.adobe.granite.maintenance.impl.TaskScheduler` nicht im Status `Active` (NPR-34952) angezeigt.

#### [!DNL Assets] {#assets-6483}

* Wenn Sie eine Version eines vorhandenen Assets erstellen, bleiben die Benutzeraktualisierungen zu Metadaten nicht erhalten, wenn ein Metadaten-Profil auf den Ordner angewendet wird (NPR-34833).
* Bei Verwendung von [!DNL Adobe Asset Link] mit [!DNL Adobe InDesign] enthalten die Suchergebnisse keine Ordner und Sammlungen, sondern nur Assets (NPR-34700).
* Wenn Sie ein Asset in einen Ordner ziehen, um es zu verschieben, zeigt die Benutzeroberfläche auch die Option [!UICONTROL In Leuchtkasten ] ablegen und [!UICONTROL In Sammlung ablegen] an. Auch wenn der Verschiebungsvorgang abgebrochen wird, zeigt die Benutzeroberfläche weiterhin die beiden letztgenannten Optionen an (NPR-34525).
* Wenn die Benutzeroberfläche &quot;Veröffentlichung verwalten&quot;geöffnet ist, ist die Option &quot;Veröffentlichen&quot;nicht verfügbar und bei Auswahl der Option &quot;Rückgängig&quot;ist die Seite &quot;Umfang&quot;leer (CQ-4302509).

##### [!DNL Dynamic Media] {#dynamic-media-6483}

* Wenn in den Bildvorgabeeinstellungen die Option [!UICONTROL JPG-Chrominanz-Downsampling aktivieren] in [!DNL Experience Manager] deaktiviert ist, wird die Änderung nicht mit [!DNL Dynamic Media] (NPR-34284) synchronisiert.
* Im [!UICONTROL Viewer-Vorgaben-Editor] ist bei der Bearbeitung der Vorgabe [!UICONTROL PanoramicImage/PanoramicImage_VR] in der Komponente `PanoramicView` die Modifikator-Beschriftung `PANORAMICVIEW_AUTOROTATE` nicht verfügbar (CQ-4302043).
* Beim Rückgängigmachen der Veröffentlichung eines Videos von [!DNL Experience Manager] wird die Veröffentlichung des adaptiven Videosets in konfigurierter Dynamic Media Classic nicht rückgängig gemacht. (CQ-4304405).

#### Plattform {#platform-6483}

* Das `emitUseStrict`-Flag wird der Funktion Google Closure Compiler (GCC) Processor `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl` hinzugefügt. Das Flag unterdrückt die Ausgabe der Anweisung `use strict` (NPR-34830).
* Ein `NullPointerException` wird beim Starten der täglichen oder wöchentlichen Wartungsarbeiten zurückgegeben (NPR-34702).
* Das [!DNL Apache Sling Health Check]-Tool wird nicht mehr unterstützt. Verwenden Sie stattdessen [Mustererkennung](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html), um Inhaltsverletzungen zu erkennen (NPR-33929).

#### Integrationen {#integrations-6483}

* Die Schaltfläche [!UICONTROL Erstellen] wird auf der Seite [!UICONTROL Audiencen] angezeigt, wenn Sie von einem Ordner zur Seite [!UICONTROL Audiencen] navigieren (NPR-35152).

#### Benutzeroberfläche {#ui-6483}

* Das Suchfeld [!UICONTROL Filter] auf der [!UICONTROL Omniture Search]-Benutzeroberfläche gibt auch Ergebnisse von anderen Orten als dem zurück, von denen aus die Suche ausgeführt wird (NPR-34877).
* Beim Schließen des Bereichs [!UICONTROL Filter] auf der [!UICONTROL Omniture Search]-Benutzeroberfläche wird die linke Leiste nicht auf [!UICONTROL Content] zurückgesetzt, was verhindert, dass das Bedienfeld [!UICONTROL Filter] erneut geöffnet wird (NPR-34483).
* Beim Zugriff auf die Seiteneigenschaften wird ein `NullPointerException` zurückgegeben (NPR-34509).

#### Communities {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* Alle Fälle ungleicher Terminologie im Produkt werden durch anerkannte Entsprechungen ersetzt (NPR-34506).

#### Commerce {#commerce-6483}

* Wenn eine Sammlung mehr als 15 Produkte enthält, zeigt die Sammlung nur die ersten 15 Produkte an (NPR-34494).

#### Formulare {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten  [!DNL Experience Manager] Cumulative Fix Pack-Veröffentlichungsdatum.

>[!NOTE]
>
>[!DNL Experience Manager] Das kumulative Fix Pack enthält keine Korrekturen für  [!DNL Experience Manager Forms]. Sie werden mithilfe eines separaten [!DNL Forms] Add-On-Pakets bereitgestellt. Zusätzlich wird ein kumulatives Installationsprogramm veröffentlicht, das Fehlerbehebungen für [!DNL Experience Manager Forms] auf JEE enthält. Weitere Informationen finden Sie unter [AEM Forms-Add-On-Paket installieren](#install-aem-forms-add-on-package) und [AEM Forms JEE-Installationsprogramm installieren](#install-aem-forms-jee-installer).

**Adaptive Formulare**

* Adaptive Formulare können nicht mit der klassischen Benutzeroberfläche bearbeitet werden, nachdem das [!DNL Experience Manager] Cumulative Fix Pack (NPR-35127) angewendet wurde.

* Fragmente benötigen wegen der Cache-Ungültigmachung (NPR-34655) längere Zeit, um sie in einem adaptiven Formular zu laden.

* Zugänglichkeit: Die Registerkartennavigation funktioniert nicht ordnungsgemäß für Bildschirmlesehilfen in adaptiven Formularen (NPR-34550).

**Korrespondenzverwaltung**

* Wenn Sie die Assets aus ES3 migrieren, enthalten die Assets zwei nicht bearbeitbare Standardbedingungen (NPR-34971).

**Foundation JEE**

* Migrieren Sie [!DNL AEM Forms]-Benutzer von Flash zu HTML (CQ-4304075).

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM Cumulative Fix Pack 6.4.8.2 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 einige interne und kundenspezifische Fehlerbehebungen enthält.

AEM 6.4.8.2 ist ein kumulatives Fix Pack (CFP), das von AEM 6.4 Service Pack 8 abhängig ist. Installieren Sie CFP nach der Installation von AEM 6.4 Service Pack 8.

In AEM 6.4.8.2 wird das integrierte Repository (Apache Jackrabbit Oak) auf Version 1.8.22 aktualisiert.

Weitere Informationen zu CFP und anderen Versionstypen finden Sie unter [AEM Definitionen für Versionshinweise aktualisieren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

In Adobe Experience Manager 6.4.8.2 wurden die folgenden Probleme behoben:

#### Sites {#sites-6482}

* Wenn `RolloutConfigManagerFactoryImpl` keine Rollout-Konfiguration laden kann, wird nicht versucht, die fehlenden Konfigurationen zu laden. Es gibt die zwischengespeicherten Konfigurationen (NPR-34091) zurück.
* In der Kernkomponente &quot;Text&quot;wird nach Verwendung der HTML-Quellbearbeitungsoption die Klasse aus dem Tag `em` entfernt (NPR-34080).
* Wenn Sie von Experience Manager 6.2 auf Experience Manager 6.5 aktualisieren, wird die Komponente Parsys der statischen Vorlagen nicht korrekt angezeigt. Die Höhe der Komponente Parsys ist auf 0 eingestellt und die darin enthaltenen Komponenten sind nicht sichtbar (NPR-34044).
* Die Beschriftungsinformationen der zulässigen Komponenten im Vorlageneditor (NPR-33908) werden nicht angezeigt.

   ![Fehlende Beschriftungen im Layout-Container](assets/33908_missing_labels.png)

* Benutzer können nach der vierten Ebene verschachtelter Komponenten (NPR-33873) keine Komponenten zu den Parsen hinzufügen oder bearbeiten.
* Wenn der ursprüngliche Inhalt einer bearbeitbaren Vorlage geändert und dann die Vorlage veröffentlicht wird, zeigen alle neuen Seiten, die mit dieser Vorlage erstellt wurden, das Veröffentlichungsdatum der Vorlage an, auch wenn die Seiten nicht veröffentlicht wurden (NPR-33822).
* Die Eigenschaften `cq:acLinks` und `cq:acUUID` für [!DNL Adobe Campaign] auf der Kopie werden beim Kopieren und Einfügen entfernt (NPR-33793).
* Auf der Registerkarte [!UICONTROL Live Usage] werden nur 49 Ergebnisse angezeigt. Es wird nicht die gesamte Nutzung der Komponente angezeigt (NPR-33710).
* Eine Webseite mit dem Zeichen `/` in der URL reagiert beim Authoring nicht mehr. Wenn beim Authoring eine Komponente hinzugefügt wird, erhöht sich die CPU-Auslastung und der Browser reagiert nicht mehr (NPR-33625).
* Im Inline-Bearbeitungsmodus unter [!DNL RTE] funktioniert das Ziehen eines Bildes nicht für Textkomponente (NPR-33579).
* Es ist möglich, eine Komponente in einer Blueprint-Seite mit demselben Namen wie der Seitenname zu erstellen. Während der Rollout wird eine solche Komponente durch Suffix `_msm_moved` umbenannt. Die Komponente wird jedoch an das Ende des [!UICONTROL Absatzsystems] (NPR-33534) verschoben.
* Beim Start der Promotion werden keine Seiten veröffentlicht, wenn die Eigenschaft [!UICONTROL einschließlich der Unterseiten] im ersten Inhaltsstamm (NPR-33533) nicht markiert ist.
* Die Umleitung auf die Seite [!DNL Experience Manager] mit Anker funktioniert in der Autoreninstanz nicht, da `PageRedirectServlets` die Abfrage nach einem URL-Fragment oder Anker (NPR-34287) setzt.
* `PageRedirectServlet` wird  `.html` nach der Sling-Zuordnung angehängt, was zu Link-Fehlern führt (NPR-34271).
* Sie können das [!DNL Live Copy] einer Seite aussetzen und die Vererbung wird, wie im Editor-Modus gesehen, unterbrochen. In den Seiteneigenschaften gibt das Symbol für Vererbung jedoch fälschlicherweise an, dass die Vererbung vorhanden ist und nicht beschädigt ist (NPR-34096).
* Problem mit der Anzeige der zulässigen Komponenten auf der Seite &quot;Vorlage bearbeiten&quot;(CQ-4297295).
* Nach der Aktualisierung von Chrome und Firefox funktionieren die Popupmenüs nicht wie erwartet. Beim Laden der Seiteneigenschaften wird das Bedienfeld nicht angezeigt, wenn Daten darin vorhanden sind (CQ-4292995).
* Mehrere Site-übergreifende Skriptinstanzen in [!DNL Experience Manager Sites]-Komponenten (NPR-33926).
* Benutzereingaben werden beim Senden von Informationen an den Client nicht ordnungsgemäß für verschiedene Komponenten kodiert (NPR-33696).
* Eine URL, die mit `childrenlist.html` endet, zeigt eine HTML-Seite anstelle einer 404-Antwort an. Solche URLs sind anfällig für Cross-Site-Scripting (NPR-33441).

#### Assets {#assets-6482}

* Die Extraktion von Text für die hochgeladenen PDF-Dateien funktioniert nicht und die Volltextsuche nach bestimmten Wörtern in einer PDF-Datei funktioniert nicht, um diese PDF-Datei abzurufen (NPR-34165).

   >[!NOTE]
   >Damit diese Fehlerbehebung funktioniert, müssen Sie die Adobe Experience Manager-Instanz nach der Installation von Service Pack 6.4.8.2 neu starten.

* Backslashes werden vor Sonderzeichen in Suchvorschlägen von Assets hinzugefügt, deren Name Sonderzeichen enthält (NPR-33833).

* Die benutzerdefinierten Filter, die als intelligente Sammlungen gespeichert werden, werden nicht korrekt auf Assets angewendet. Daher sind die Suchergebnisse nicht genau   (NPR-33725).

* Die Zeitleiste eines Assets in einem neu angeordneten Ordner zeigt an, dass das Asset verschoben wurde (NPR-33580).

* Das Rückgängigmachen der Veröffentlichung der Assets stapelweise von [!DNL Brand Portal] führt zum `Request-URI Too Long`-Fehler (NPR-34158).

* Wenn der Benutzer nach Auswahl eines Assets die Option [!UICONTROL Filter] auswählt (die Assets werden deaktiviert) und anschließend einen anderen Asset-Satz auswählt, der verschoben werden soll, werden die zuvor ausgewählten Assets ebenfalls an den neuen Speicherort verschoben (NPR-34018).

* Die Bildlaufleiste ist in der Ansicht der Liste nicht sichtbar, selbst wenn es zahlreiche Elemente gibt, die in die Seite passen (NPR-34156).

* Die Seite [!UICONTROL Veröffentlichung verwalten] für Assets ist beschädigt und die darin enthaltenen Optionen funktionieren nicht (CQ-4302509).

**Dynamic Media**

* Die Funktion &quot;Intelligentes Beschneiden&quot;schlägt fehl, wenn einem Profil mit mehreren Seitenverhältnissen (z. B. 11) (NPR-34083) ein Bild hinzugefügt wird.

* Änderungen an Bildvorgaben in [!UICONTROL Adobe Experience Manager] werden nicht mit Dynamic Media Classic synchronisiert (NPR-34284, CQ-4299713).

* Die Modifikatorbeschriftung [!UICONTROL PANORAMICVIEW_AUTOROTATE] fehlt auf der Registerkarte [!UICONTROL Verhalten] auf der Seite [!UICONTROL Viewer-Vorgabeneditor] (CQ-4302043).

#### Plattform {#platform-6482}

* Die Standardwerte für die Einstellungen **[!UICONTROL Connect Timeout]** und **[!UICONTROL Socket Timeout]** für die Standardagentenkonfiguration (publish) sind nicht angegeben (NPR-33708).
* Die Planung der Aufgabe zur Instandhaltung wird zu oft durch die Beginn der  beendet und die Aufgaben werden zu oft gestoppt (NPR-33520).
* Protokolle können nicht mit dem Diagnosetool auf einer aktualisierten Experience Manager-Instanz (NPR-34419) heruntergeladen werden.

#### Integrationen {#integrations-6482}

* Der Wert von `library_path` wird nicht berücksichtigt, wenn [!DNL Adobe Launch]-Bibliotheks-URL für Bibliotheken generiert wird, die von [!DNL Adobe Dynamic Tag Management] migriert wurden. Außerdem verwenden die migrierten Bibliotheken ein anderes Präfix als [!DNL Adobe Launch]-Bibliotheken. (NPR-34238).
* Die von einem Cloud-Dienst geerbten Eigenschaften bleiben beim Aktualisieren der Seiteneigenschaften nicht erhalten (NPR-33865).

#### Benutzeroberfläche {#ui-6482}

* Die Anzeige der Anzahl der ausgewählten Assets auf einer Suchseite ist nicht korrekt (NPR-33540).

#### Communities {#communities-6482}

* Die vorhandenen Benutzer einer Community-Gruppe, die über die Admin-Konsole hinzugefügt wurde, werden bei jeder Änderung in der Community-Gruppenkonsole (NPR-34312) aus der Liste entfernt.

#### Formulare {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] Das kumulative Fix Pack enthält keine Korrekturen für  [!DNL Experience Manager Forms]. Sie werden mithilfe eines separaten [!DNL Forms] Add-On-Pakets bereitgestellt. Zusätzlich wird ein kumulatives Installationsprogramm veröffentlicht, das Fehlerbehebungen für [!DNL Experience Manager Forms] auf JEE enthält. Weitere Informationen finden Sie unter [AEM Forms-Add-On-Paket installieren](#install-aem-forms-add-on-package) und [AEM Forms JEE-Installationsprogramm installieren](#install-aem-forms-jee-installer).

**Adaptive Formulare**

* Wenn ein adaptives Formularfragment fehlt, kann das adaptive Formular nicht gerendert werden (NPR-34303).

* In der Inhaltsbeschreibung für adaptive Formularfelder wird ein Absatz-HTML-Tag (NPR-34117) angezeigt.

* Wenn Sie einen Forms-Container auf einer [!DNL Experience Manager Sites]-Seite hinzufügen, zeigt die Seite die folgende Fehlermeldung an und erlaubt Ihnen nicht, neue Komponenten hinzuzufügen (NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Wenn Sie die Eigenschaft **[!UICONTROL Auf Server]** erneut überprüfen und mehrere Anlagen hochladen, schlägt das Senden des adaptiven Formulars fehl (NPR-33701).

* Wenn Sie die Optionen **[!UICONTROL Seitensprache verwenden]** und **[!UICONTROL Formular für die gesamte Breite der Optionen &quot;Seite]**&quot;in [!DNL Experience Manager Forms]-Komponente auf einer [!DNL Experience Manager Sites]-Seite auswählen, schlägt die Übersetzung der Seite fehl (NPR-33641).

* Wenn Sie ein analysefähiges adaptives Formular senden, das in eine [!DNL Experience Manager Sites]-Seite eingebettet ist, funktioniert die Analyse nicht korrekt (NPR-31359).

* Abhängigkeiten von [!DNL Lodash]- und [!DNL backbone]-Bibliotheken (NPR-33458) wurden entfernt.

* Die Übermittlungsaktion **[!UICONTROL An REST-Endpunkt senden]** funktioniert nicht für ein adaptives Formular (NPR-34513).

* Zugänglichkeit: Wenn Sie versuchen, ein adaptives Formular zu senden, ohne eine Anlage für ein Pflichtfeld hochzuladen, wird der Fokus nicht automatisch auf das Anlagenfeld verschoben (NPR-34511).

* Benutzereingaben werden für [!DNL Forms]-Komponenten nicht ordnungsgemäß kodiert, wenn Informationen an den Client gesendet werden (NPR-33611).

**Arbeitsablauf**

* [!DNL Experience Manager] Der Vorgang &quot;Workflow-Bereinigung&quot;schlägt fehl und zeigt die folgende Fehlermeldung an (NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Wenn Sie [!DNL Experience Manager] 6.4.8.1 installieren, wird die Liste [!UICONTROL Aufgaben] der Elemente nicht als Links angezeigt. Der Text für die Elemente [!UICONTROL Aufgaben] enthält HTML-Tags (NPR-34318).

**BackendIntegration**

* Formulardatenmodell kann nicht in einer AWS-gehosteten [!DNL Experience Manager Forms Linux]-Umgebung (NPR-33617) konfiguriert werden.

**Designer**

* Wenn [!DNL Acrobat DC] auf einem [!DNL Experience Manager] Forms-Server installiert ist, ist die Option **[!UICONTROL Formular verteilen]** in [!DNL Experience Manager Designer] Version 6.x (NPR-34325) nicht verfügbar.

**Document Security**

* Der Signaturvorgang mit HSM-basierten Zertifikaten kann nach der Installation von [!DNL Experience Manager] 6.4.8.0 (NPR-34309) nicht in einer PDF-Datei ausgeführt werden.

**Aktualisierung**

* Wenn Sie die [!DNL JBoss]-Version auf 7.0.9 für [!DNL Experience Manager Forms] mit Dokument Security in einer [!DNL Linux]-Umgebung aktualisieren, wird ein Fehler ausgegeben (CQ-4300546).

Informationen zu Sicherheitsaktualisierungen finden Sie unter [Seite mit Sicherheitsbulletins für Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 mehrere interne und kundenspezifische Fehlerbehebungen enthält.

AEM Cumulative Fix Pack 6.4.8.1 ist von AEM 6.4 Service Pack 8 abhängig. Daher müssen Sie das AEM Cumulative Fix Pack 6.4.8.1 Paket nach der Installation von AEM 6.4 Service Pack 8 installieren.

Einige der wichtigsten Highlights von AEM 6.4.8.1 sind:

* Der anonyme Zugriff auf CRXDE Lite ist nicht erlaubt, um die Sicherheit zu erhöhen. Stattdessen werden die Benutzer zum Anmeldebildschirm weitergeleitet. Siehe [Entwickeln mit CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* Die Paketfreigabe-Integration mit Adobe Experience Manager wurde entfernt.
* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.21 aktualisiert.

Weitere Informationen zu CFP und anderen Versionstypen finden Sie unter [AEM Definitionen für Versionshinweise aktualisieren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

In Adobe Experience Manager 6.4.8.1 wurden die folgenden Probleme behoben:

#### Sites {#sites-6481}

* Anonyme Benutzer können auf die Funktionen von CRX DE Lite zugreifen (NPR-33522).
* Wenn der Name einer lokalen Komponente in einer LiveCopy mit dem Namen einer Komponente im Entwurf identisch ist und die Komponente aus dem Blueprint herausgegeben wird, wird dem Namen der lokalen Komponente kein Begriff _msm_move hinzugefügt (NPR-33207).
* Die an die ursprüngliche Anforderung angehängten Parameter sind nicht in der Umleitungs-URL (NPR-33174) enthalten.
* Wenn die Option &quot;Coral.Select&quot;emptyOption=true setzt oder ein Standardelement mit Wert = &quot;&quot; enthält, tritt in der Datei dropdownshowhide.js ein Fehler auf: Nicht abgefangener TypeError: component.getValue ist keine Funktion (NPR-33163).
* Wenn eine Komponente eine andere Komponente als datenbasierte Ressource enthält, wird der Platzhalter für die Komponente des übergeordneten Containers durch den Platzhalter für die inneren Komponenten ersetzt (NPR-33119).
* Wenn Sie ein Inhaltsfragment auf einem Schema basieren und es einen obligatorischen Textbereich oder ein Pfadfeld enthält, kann das Inhaltsfragment nicht gespeichert werden (NPR-33007)
* Wenn Sie eine benutzerdefinierte Komponente mithilfe der vordefinierten Erlebnisfragmentkomponente erstellen und sie auf AEM Sites-Seiten verwenden, werden AEM keine Verweise (Verwendung) für die benutzerdefinierte Komponente (NPR-32852) angezeigt.
* Wenn eine AEM Sites-Seite Teil eines großen Inhaltssatzes mit mehreren Live-Kopien ist, kann die Vorschau des Seitenversionsverlaufs nicht geladen werden (NPR-32772).
* Wenn Sie einen Launch bewerben, wird das &quot;cq:LiveRelationship&quot;-Mixin zu jeder Komponente hinzugefügt, die im Launch hinzugefügt wird. Sie wirkt sich auf alle Starts aus, unabhängig davon, ob ein Startvorgang mit oder ohne Auswahl der Option —  Quellseitendaten übernehmen —  Option (NPR-32664).
* Beim Paginieren werden nicht alle Elemente (NPR-32605) in der Erlebnisfragmentauswahl geladen.
* Ein Start für eine AEM Sites-Seite kann nicht erstellt werden. Die Erstellung des Startvorgangs führt zu einem Fehler (NPR-32544).
* Veröffentlichung verwalten enthält keine referenzierten Assets in der Anforderung des Arbeitsablaufs für die Aktivierung (NPR-32463).
* Bei der Dispatcher-Statusprüfung wird in den Protokolldateien (NPR-33630) die Warnmeldung `Invalid cookie header` angezeigt.
* Die Salesforce-Integration ist anfällig für SSRF (NPR-32671).
* XSS in PreferencesServlet (NPR-33439) reflektiert.

#### Assets {#assets-6481}

* Die Anzahl der Vermögenswerte ändert sich nicht entsprechend der Änderung der Auswahl in der Ansicht der Liste (NPR-33285).

* Die Schaltfläche Weiter ist nicht aktiviert, wenn der übergeordnete Knoten ausgewählt (wobei ein einzelner untergeordneter Ordner sichtbar ist) und anschließend der untergeordnete Ordner ausgewählt wird (NPR-33284).

* Die Touch-Benutzeroberfläche kann nicht (mit Fehler) für Benutzer gerendert werden, die keinen Lesezugriff im Repository-Stammordner haben, wenn der DMS7- oder Hybrid-Modus aktiviert ist (NPR-33175).

* Die GB18030-Zeichen in Ordner- und Asset-Namen werden in den heruntergeladenen ZIP-Dateien leer (NPR-33150).

* Der Ordner &quot;Extra&quot;wird beim intelligenten Zuschneiden eines Assets erstellt, das sich in einem übergeordneten Ordner mit dem Zeichen `.` in seinem Namen befindet (NPR-32755).

* Verzögertes Laden wird nicht ausgelöst, und es werden nicht mehr als 100 Assets angezeigt, die ausgewählt werden, um die Aufgaben aus dem Benachrichtigungs-Posteingang zu überprüfen (NPR-32749).

* Die Linkseite zum Teilen der Sammlung ist aufgrund einer Änderung der Korallen-Info (NPR-32510) beschädigt.

* Die Verarbeitung von Assets während des Massen-Uploads wird blockiert (CQ-4293916).

* Anfälligkeit für SSRF in Experience Manager (NPR-33437).

#### Plattform {#platform-6481}

* Der Filter [!DNL Sling] wird nicht aufgerufen, wenn der `sling:match`-Map-Eintrag unter `/etc/maps` (NPR-33308) erstellt wird.
* Alle Spülmittel werden beim Deaktivieren einer Seite ausgelöst (NPR-32941).
* Wenn Sie die API `ScriptProcessor` verwenden, um eine JavaScript-Bibliothek zu verkleinern, zeigt die Protokolldatei eine Fehlermeldung an, dass der JavaScript-Code nicht dem strikten Modus entspricht. Die API bietet keine Option zum Aktivieren oder Deaktivieren des strikten Modus. (NPR-32746).
* Wenn eine SQL-Abfrage länger ausgeführt wird (z. B. 7 Stunden), reagiert AEM nicht mehr (NPR-33043).

#### Benutzeroberfläche {#ui-6481}

* Wenn Sie einen Pfad über ein Auswahldialogfeld suchen oder durchsuchen, werden im Auswahldialogfeld alle Inhalte des ausgewählten JCR-Knotens angezeigt, anstatt nur die Bilder anzuzeigen (NPR-32712).

#### Übersetzungsprojekte {#tranlation-6481}

* Ein `NullPointerException`-Fehler wird in den Protokollen zur Ausführung eines Übersetzungsauftrags (NPR-32220) angezeigt.

#### Integrationen {#integrations-6481}

* Site-übergreifende Skripterstellung für JSON (NPR-32745).

#### Communities {#communities-6481}

* Autoren werden nach dem Erstellen einer neuen Gruppe nicht zum Abschnitt [!UICONTROL Community-Gruppe] unter [!DNL Internet Explorer] 11 (NPR-33202) umgeleitet.
* Beim Zugriff auf die Seite [!UICONTROL Aktivität Stream] (NPR-33152) tritt ein Fehler auf.
* Wenn Sie eine [!DNL Communities]-Gruppe bearbeiten und das Miniaturbild ändern, wird das Gruppenminiaturbild nicht aktualisiert (NPR-32603).
* Beim Erstellen einer Version von Benachrichtigungen und Abonnements von User Generated Content (UGC) wird eine falsche ID der Quellseite gespeichert (CQ-4289703).
* Site-übergreifendes Skriptproblem (NPR-33212).

#### Workflow {#workflow-6481}

* Einige Komponenten werden nicht im Popup-Dialogfeld angezeigt, wenn ein Benutzer einen Workflow abgeschlossen hat, der den Schritt [!UICONTROL Dialogteilnehmer] (NPR-32989) enthält.

* Die Option [!UICONTROL Zeitschiene] in der linken Leiste dauert länger als erwartet (NPR-32850).

#### Formulare {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack enthält keine Korrekturen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [AEM Forms-Add-On-Paket installieren](#install-aem-forms-add-on-package) und [AEM Forms JEE-Installationsprogramm installieren](#install-aem-forms-jee-installer).

* Correspondence Management: Wenn ein Benutzer Inhalte aus einem [!DNL Word]-Dokument einfügt, behält das Textfragment keine Formatierung bei (NPR-33213).
* Adaptives Forms: Eine neue Zeile zu einer Zeichenfolge in einem Wörterbuch für adaptive Formulare fügt dem Wörterbuch `&#xa;`-Zeichen hinzu (NPR-33265).
* Adaptives Forms: Der Benutzer kann ein adaptives Formular nicht mit mehr als einer Anlage speichern (NPR-33214).
* Adaptives Forms: `AddInstance`- und `RemoveInstance`-Methoden für Instanz-Manager-Klasse fügen keine dynamische Anzahl von Instanzen für verzögerte Ladefragmente bei [!DNL Internet Explorer 11] (NPR-33201) hinzu.
* Adaptives Forms: Analytics, die auf einem adaptiven Formular aktiviert sind, das in eine [!DNL Sites]-Seite eingebettet ist, zeichnet keine Daten für die Ereignisse &quot;Senden&quot;und &quot;Abbrechen&quot;auf (NPR-31359).
* Adaptives Forms: Wenn ein Benutzer den Inhalt aus einem [!DNL Word]-Dokument in ein adaptives Formular einfügt und es sendet, enthält das gesendete adaptive Formular Unicode-Zeichen. Darüber hinaus schlägt die Konvertierung von PDF in PDF/A aufgrund von Unicode-Zeichen (NPR-33348) fehl.
* BackendIntegration: Formulardatenmodellanforderungen schlagen fehl, da der Aktualisierungstoken aufgrund eines inaktiven Status (NPR-33168) abläuft.
* Dokument-Dienste: Der Convert PDF-Dienst kann PDF-Dokumente nicht in PostScript konvertieren, da Gibson-Jars für [!DNL WebLogic] auf dem [!DNL Linux]-Server (NPR-33515, CQ-4292239) fehlen.
* Dokument-Dienste: Wenn ein Benutzer eine Textdatei in eine PDF-Datei konvertiert, werden japanische Zeichen nicht korrekt dargestellt (NPR-33239).
* XSS mit GuideSOMProviderServlet (NPR-32701) gespeichert.

## Installieren Sie 6.4.8.4 {#install}

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
>Für Kunden mit Feature Packs, die auf AEM 6.4 installiert sind. Optionale Funktionspakete, die von Adobe bereitgestellt werden, hängen von der Release-Version und den Service Packs ab. Wenn Sie ein Feature Pack installiert haben, wenden Sie sich bitte an das AEM Kundenservice-Team, um die Kompatibilität dieser Feature Packs mit diesem kumulativen Fix Pack für AEM 6.4 zu überprüfen.

* AEM 6.4.8.4 erfordert AEM 6.4.8.0. Ausführliche Anweisungen finden Sie in der [Aktualisierungsdokumentation](../sites-deploying/upgrade.md).
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.4.8.4 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Bevor Sie das kumulative Fix Pack installieren, stellen Sie sicher, dass Sie eine Momentaufnahme oder eine erneute Sicherung Ihrer AEM erhalten.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz gerade von einer früheren Version aktualisiert wurde). Dennoch wird dies allgemein empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!NOTE]
>
>Adobe rät davon ab, das AEM 6.4.8.4-Paket zu entfernen oder zu deinstallieren.

### Installieren Sie das kumulative Fix Pack {#install-cumulative-fix-pack}

Führen Sie die folgenden Schritte aus, um das Cumulative Fix Pack auf einer vorhandenen AEM 6.4.8.0-Instanz zu installieren:

1. Klicken Sie auf den Link [Software-Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip), um das Paket herunterzuladen.

1. Öffnen Sie [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.

1. Wählen Sie den Paketnamen und klicken Sie auf **[!UICONTROL Install]**.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird in einigen Fällen während der Installation von 6.4.8.4 frühzeitig beendet.**
>
>Es wird daher empfohlen, auf die Stabilisierung der Fehlerprotokolle zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles warten, bevor sichergestellt wird, dass die Installation erfolgreich ist. In der Regel trifft dies auf Safari zu, kann aber mitunter auch auf allen anderen Browsern der Fall sein.

### Automatische Installation {#auto-installation}

Es gibt zwei Möglichkeiten, AEM 6.4.8.4 automatisch in einer laufenden Instanz zu installieren:

A. Platzieren Sie das Paket in ..Ordner */crx-quickstart/install*, während der Server läuft. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](https://helpx.adobe.com/de/experience-manager/aem-previous-versions.html) - stellen Sie sicher, dass Sie `cmd=install&recursive=true` verwenden - damit das verschachtelte Paket installiert wird.

>[!NOTE]
>
>AEM 6.4.8.4 unterstützt keine Bootstrap-Installation.

### Bestätigen der Installation {#validate-install}

1. Auf der Seite „Produktinformationen“ (*/system/console/productinfo*) sollte nun unter „Installierte Produkte“ die aktualisierte Version „Adobe Experience Manager, Version 6.4.8.4“ angezeigt werden.
1. Alle OSGI-Bundles sind in der OSGI-Konsole entweder AKTIV oder FRAGMENT. (Verwenden Sie die Webkonsole: /system/console/bundles.)
1. Das OSGI-Bundle org.apache.jackrabbit.oak-core ist auf Version 1.8.17 oder höher (Web-Konsole verwenden: /system/console/bundles).

Informationen zum Bestimmen der zertifizierten Plattform für die Ausführung mit dieser Version von AEM Sites und Assets finden Sie unter [Technische Anforderungen](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Bei erfolgreicher Installation des Pakets wird eine Informationsmeldung angezeigt, die angibt, dass das Inhaltspaket erfolgreich installiert wurde, z. B. **&quot;Content Package AEM-6.4-Service-Pack-8 erfolgreich installiert wurde&quot;**.

### Dynamic Media-Viewer aktualisieren (5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.4 enthält eine neue Version von Dynamic Media-Viewern (5.10.1), mit der auf der Seite &quot;Bildvorgabe&quot;nach Duplikat gesucht werden kann. Dynamic Media-Kunden wird empfohlen, den folgenden Befehl auszuführen, um die standardmäßigen Viewer-Vorgaben in den aktuellen Zustand zu bringen.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

, der neue Viewer-Vorgaben in /conf kopieren wird.

### Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] veröffentlicht die Add-On-Pakete eine Woche nach dem geplanten  [!DNL Experience Manager] Cumulative Fix Pack-Veröffentlichungsdatum.

### Uber Jar {#uber-jar}

Die Uber-Jar für AEM 6.4.8.4 ist im [Maven Central-Repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.4/) verfügbar.

Um Uber Jar in einem Maven-Projekt zu verwenden, lesen Sie den Artikel [Wie Sie Uber jar](../sites-developing/ht-projects-maven.md) verwenden und fügen Sie die folgende Abhängigkeit in Ihr Projekt-POM ein:

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
>UberJar und andere zugehörige Artefakte stehen im Maven Central Repository anstelle der Adobe Public Maven Repository (repo.adobe.com) zur Verfügung. Die UberJar-Hauptdatei wird in `uber-jar-<version>.jar` umbenannt. Daher gibt es für das `dependency`-Tag kein `classifier`-Zeichen mit dem Wert `apis`.

## Entfernte/veraltete Funktionen {#removed-deprecated-features}

Dieser Abschnitt listet Funktionen und Fähigkeiten auf, die aus AEM 6.4 entfernt oder veraltet sind.

| Bereich | Funktion | Ersatz | Version |
|---|---|---|---|
| Assets | Tag-Aktion für Teilassets verwalten | Kein Ersatz vorhanden. | AEM 6.4.2.0 |
| Assets und Adobe Creative Cloud-Integration | [Die ](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) Freigabe von AEM an Creative Cloud-Ordner wurde in AEM 6.2 eingeführt, um kreativen Benutzern Zugriff auf Assets aus AEM zu gewähren. Eine neue Funktion der Creative Cloud-Anwendung, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus.  Adobe wird die Ordnerfreigabe nicht weiter verbessern. Während die Funktion in AEM enthalten ist, wird Kunden dringend empfohlen, den Ersatz zu verwenden. | Adobe Asset Link oder Desktop-App. Weitere Informationen finden Sie im Artikel zur [AEM Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Bekannte Probleme {#known-issues}

* Wenn Sie ein Upgrade von [!DNL Experience Manager] 6.4 auf [!DNL Experience Manager] 6.5 durchführen, wird der Status einiger Pakete möglicherweise nicht als `Active` angezeigt. Installieren Sie das neueste [!DNL Experience Manager] 6.5 Service Pack, um das Problem zu beheben.

Informationen zu den bekannten Problemen im AEM 6.4.8.0 Service Pack finden Sie unter [AEM 6.4.8.0 Service Pack - Versionshinweise](sp-release-notes.md).

## OSGi-Bundles und Inhaltspakete sind enthalten {#osgi-bundles-and-content-packages-included}

Die folgenden Dokumente Liste der OSGi-Pakete und Content Packages in AEM 6.4.8.4.

Liste der in AEM 6.4.8.4 enthaltenen OSGi-Bundles

[Datei laden](assets/6.4.8.4_osgi_bundles.txt)

Liste der in AEM 6.4.8.4 enthaltenen Inhaltspakete

[Datei laden](assets/6.4.8.4_content_packages.txt)

## Hilfreiche Ressourcen {#helpful-resources}

* [Versionshinweise zu AEM 6.4](../release-notes/release-notes.md)
* [AEM-Produktseite](https://www.adobe.com/solutions/web-experience-management.html)
* [Dokumentation zu AEM 6.4](https://helpx.adobe.com/de/support/experience-manager/6-4.html)
* Abonnieren Sie die Produktaktualisierungen mit der Priorität &quot;Adobe&quot;](https://www.adobe.com/subscription/priority-product-update.html)[

## Eingeschränkte Sites {#restricted-sites-new}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Kundensupport.](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
