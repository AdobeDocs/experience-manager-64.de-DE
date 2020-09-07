---
title: AEM 6.4 - Versionshinweise zu allen Fix-Paketen
description: Versionshinweise speziell für Adobe Experience Manager 6.4 Cumulative Fix Packs.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: d3721590e3c2dfd2b048f1b5964915a343f95f6d
workflow-type: tm+mt
source-wordcount: '3364'
ht-degree: 16%

---


# AEM 6.4 - Versionshinweise zur kumulativen Fehlerbehebung {#aem-cumulative-fix-pack-release-notes}

## Versionshinweise {#release-information}

| Produkte | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.2 |
| Typ | Cumulative Fix Pack |
| Datum            | 03. September 2020 |
| Voraussetzung | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| Download-URL | AEM 6.4.8.2 zur [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-2.0.zip) |

## Was ist in AEM 6.4.8.2 enthalten?{#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.2 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 einige interne und kundenspezifische Fehlerbehebungen enthält.

AEM 6.4.8.2 ist ein kumulatives Fix Pack (CFP), das von AEM 6.4 Service Pack 8 abhängig ist. Installieren Sie CFP nach der Installation von AEM 6.4 Service Pack 8.

In AEM 6.4.8.2 wird das integrierte Repository (Apache Jackrabbit Oak) auf Version 1.8.22 aktualisiert.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

In Adobe Experience Manager 6.4.8.2 wurden die folgenden Probleme behoben:

### Sites {#sites-6482}

* Wenn das `RolloutConfigManagerFactoryImpl` Programm keine Rollout-Konfiguration laden kann, wird nicht versucht, die fehlenden Konfigurationen zu laden. Es gibt die zwischengespeicherten Konfigurationen (NPR-34091) zurück.
* In der Kernkomponente &quot;Text&quot;wird nach Verwendung der HTML-Quellbearbeitungsoption die Klasse aus dem `em` -Tag entfernt (NPR-34080).
* Wenn Sie von Experience Manager 6.2 auf Experience Manager 6.5 aktualisieren, wird die Komponente Parsys der statischen Vorlagen nicht korrekt angezeigt. Die Höhe der Komponente Parsys ist auf 0 eingestellt und die darin enthaltenen Komponenten sind nicht sichtbar (NPR-34044).
* Die Beschriftungsinformationen der zulässigen Komponenten im Vorlageneditor (NPR-33908) werden nicht angezeigt.

   ![Fehlende Beschriftungen im Layout-Container](assets/33908_missing_labels.png)

* Benutzer können nach der vierten Ebene verschachtelter Komponenten (NPR-33873) keine Komponenten zu den Parsen hinzufügen oder bearbeiten.
* Wenn der ursprüngliche Inhalt einer bearbeitbaren Vorlage geändert und dann die Vorlage veröffentlicht wird, zeigen alle neuen Seiten, die mit dieser Vorlage erstellt wurden, das Veröffentlichungsdatum der Vorlage an, auch wenn die Seiten nicht veröffentlicht wurden (NPR-33822).
* Die `cq:acLinks` und `cq:acUUID` Eigenschaften für [!DNL Adobe Campaign] die Kopie werden beim Kopieren und Einfügen entfernt (NPR-33793).
* Auf der Registerkarte &quot; [!UICONTROL Live-Gebrauch] &quot;werden nur 49 Ergebnisse angezeigt. Es wird nicht die gesamte Nutzung der Komponente angezeigt (NPR-33710).
* Eine Webseite mit `/` Zeichen in der URL reagiert beim Authoring nicht mehr. Wenn beim Authoring eine Komponente hinzugefügt wird, erhöht sich die CPU-Auslastung und der Browser reagiert nicht mehr (NPR-33625).
* Im Inline-Bearbeitungsmodus in [!DNL RTE]funktioniert das Ziehen eines Bildes nicht für Textkomponente (NPR-33579).
* Es ist möglich, eine Komponente in einer Blueprint-Seite mit demselben Namen wie der Seitenname zu erstellen. Während der Aktualisierung wird eine solche Komponente durch Suffix umbenannt `_msm_moved`. Die Komponente wird jedoch an das Ende des [!UICONTROL Absatzsystems] (NPR-33534) verschoben.
* Beim Start der Promotion werden keine Seiten veröffentlicht, wenn die [!UICONTROL Eigenschaft &quot;Unterseiten] einschließen&quot;im ersten Inhaltsstamm nicht markiert ist (NPR-33533).
* Die Umleitung auf die [!DNL Experience Manager] Seite mit Anker funktioniert nicht in der Autoreninstanz, da die Abfrage nach einem URL-Fragment oder einem Anker `PageRedirectServlets` (NPR-34287) als Zeichenfolge eingefügt wird.
* `PageRedirectServlet` wird `.html` nach der Sling-Zuordnung angehängt, was zu Link-Fehlern führt (NPR-34271).
* Sie können den [!DNL Live Copy] Status einer Seite aussetzen und die Vererbung wird, wie im Editor-Modus angezeigt, unterbrochen. In den Seiteneigenschaften gibt das Symbol für Vererbung jedoch fälschlicherweise an, dass die Vererbung vorhanden ist und nicht beschädigt ist (NPR-34096).
* Problem mit der Anzeige der zulässigen Komponenten auf der Seite &quot;Vorlage bearbeiten&quot;(CQ-4297295).
* Nach der Aktualisierung von Chrome und Firefox funktionieren die Popupmenüs nicht wie erwartet. Beim Laden der Seiteneigenschaften wird das Bedienfeld nicht angezeigt, wenn Daten darin vorhanden sind (CQ-4292995).

### Assets {#assets-6482}

* Die Extraktion von Text für die hochgeladenen PDF-Dateien funktioniert nicht und die Volltextsuche nach bestimmten Wörtern in einer PDF-Datei funktioniert nicht, um diese PDF-Datei abzurufen (NPR-34165).

   >[!NOTE]
   >Damit diese Fehlerbehebung funktioniert, müssen Sie die Adobe Experience Manager-Instanz nach der Installation von Service Pack 6.4.8.2 neu starten.

* Backslashes werden vor Sonderzeichen in Suchvorschlägen von Assets hinzugefügt, deren Name Sonderzeichen enthält (NPR-33833).

* Die benutzerdefinierten Filter, die als intelligente Sammlungen gespeichert werden, werden nicht korrekt auf Assets angewendet. Daher sind die Suchergebnisse nicht korrekt (NPR-33725).

* Die Zeitleiste eines Assets in einem neu angeordneten Ordner zeigt an, dass das Asset verschoben wurde (NPR-33580).

* Das Rückgängigmachen der Veröffentlichung der Assets als Massendatei [!DNL Brand Portal] führt zu einem `Request-URI Too Long` Fehler (NPR-34158).

* Wenn der Benutzer nach Auswahl eines Assets die Option [!UICONTROL Filter] auswählt (die Assets werden deaktiviert) und anschließend einen anderen Asset-Satz auswählt, der verschoben werden soll, werden die zuvor ausgewählten Assets ebenfalls an den neuen Speicherort verschoben (NPR-34018).

* Die Bildlaufleiste ist in der Ansicht der Liste nicht sichtbar, selbst wenn es zahlreiche Elemente gibt, die in die Seite passen (NPR-34156).

* Die Seite &quot;Veröffentlichung  verwalten&quot;für Assets ist beschädigt und die darin enthaltenen Optionen funktionieren nicht (CQ-4302509).

**Dynamic Media**

* Die Funktion &quot;Intelligentes Beschneiden&quot;schlägt fehl, wenn einem Profil mit mehreren Seitenverhältnissen (z. B. 11) (NPR-34083) ein Bild hinzugefügt wird.

* Änderungen an Bildvorgaben in [!UICONTROL Adobe Experience Manager] werden nicht mit dem Scene7 Publishing System (NPR-34284, CQ-4299713) synchronisiert.

* Die [!UICONTROL Modifikatorbeschriftung &quot;PANORAMICVIEW_AUTOROTATE] &quot;fehlt auf der Registerkarte &quot; [!UICONTROL Verhalten] &quot;auf der Seite &quot; [!UICONTROL Viewer-Vorgabeneditor] &quot;(CQ-4302043).

### Plattform {#platform-6482}

* Die Standardwerte für die **[!UICONTROL Einstellungen &quot;Zeitlimit]** für Verbindung&quot;und &quot; **[!UICONTROL Socket-Zeitlimit]** &quot;für die Konfiguration des Standardagenten (Veröffentlichungsagenten) sind nicht angegeben (NPR-33708).
* Die Planung der Aufgabe zur Instandhaltung wird zu oft durch die Beginn der  beendet und die Aufgaben werden zu oft gestoppt (NPR-33520).
* Protokolle können nicht mit dem Diagnosetool auf einer aktualisierten Experience Manager-Instanz (NPR-34419) heruntergeladen werden.

### Integrationen {#integrations-6482}

* Der Wert von `library_path` wird beim Generieren der [!DNL Adobe Launch] Bibliotheks-URL für Bibliotheken, aus denen migriert wurde, nicht berücksichtigt [!DNL Adobe Dynamic Tag Management]. Außerdem verwenden die migrierten Bibliotheken ein anderes Präfix als [!DNL Adobe Launch] Bibliotheken. (NPR-34238).
* Die von einem Cloud-Dienst geerbten Eigenschaften bleiben beim Aktualisieren der Seiteneigenschaften nicht erhalten (NPR-33865).

### Benutzeroberfläche {#ui-6482}

* Die Anzeige der Anzahl der ausgewählten Assets auf einer Suchseite ist nicht korrekt (NPR-33540).

### Communities {#communities-6482}

* Die vorhandenen Benutzer einer Community-Gruppe, die über die Admin-Konsole hinzugefügt wurde, werden bei jeder Änderung in der Community-Gruppenkonsole (NPR-34312) aus der Liste entfernt.

### Formulare {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] Das kumulative Fix Pack enthält keine Korrekturen für [!DNL Experience Manager Forms]. They are delivered using a separate [!DNL Forms] add-on package. In addition, a cumulative installer is released that includes fixes for [!DNL Experience Manager Forms] on JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

**Adaptive Formulare**

* Wenn ein adaptives Formularfragment fehlt, kann das adaptive Formular nicht gerendert werden (NPR-34303).

* In der Inhaltsbeschreibung für adaptive Formularfelder wird ein Absatz-HTML-Tag (NPR-34117) angezeigt.

* Wenn Sie einen Forms-Container auf einer [!DNL Experience Manager Sites] Seite hinzufügen, wird die folgende Fehlermeldung angezeigt und Sie können keine neuen Komponenten hinzufügen (NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Wenn Sie die Eigenschaft &quot; **[!UICONTROL Auf Server]** überprüfen&quot;auswählen und mehrere Anlagen hochladen, kann das adaptive Formular nicht gesendet werden (NPR-33701).

* Wenn Sie die **[!UICONTROL Option &quot;Seitensprache]** verwenden&quot;auswählen und das **[!UICONTROL Formular die gesamte Breite der Seitenoptionen]** in der [!DNL Experience Manager Forms] Komponente auf einer [!DNL Experience Manager Sites] Seite abdeckt, schlägt die Übersetzung der Seite fehl (NPR-33641).

* Wenn Sie ein analysefähiges adaptives Formular senden, das in eine [!DNL Experience Manager Sites] Seite eingebettet ist, funktioniert die Analyse nicht korrekt (NPR-31359).

* Abhängigkeiten von [!DNL Lodash] und [!DNL backbone] Bibliotheken entfernt (NPR-33458).

* Die Übermittlungsaktion **[!UICONTROL An REST-Endpunkt]** übermitteln funktioniert nicht für ein adaptives Formular (NPR-34513).

* Zugänglichkeit: Wenn Sie versuchen, ein adaptives Formular zu senden, ohne eine Anlage für ein Pflichtfeld hochzuladen, wird der Fokus nicht automatisch auf das Anlagenfeld verschoben (NPR-34511).

**Arbeitsablauf**

* [!DNL Experience Manager] Der Vorgang &quot;Workflow-Bereinigung&quot;schlägt fehl und zeigt die folgende Fehlermeldung an (NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Bei der Installation von [!DNL Experience Manager] 6.4.8.1 wird die [!UICONTROL Aufgaben] -Liste von Elementen nicht als Links angezeigt. Der Text für die [!UICONTROL Aufgaben] -Elemente enthält HTML-Tags (NPR-34318).

**BackendIntegration**

* Formulardatenmodell kann nicht in einer gehosteten AWS- [!DNL Experience Manager Forms Linux] Umgebung (NPR-33617) konfiguriert werden.

**Designer**

* Wenn auf einem [!DNL Acrobat DC] Forms-Server installiert [!DNL Experience Manager] ist, ist die Option &quot;Formular **[!UICONTROL verteilen]** &quot;in [!DNL Experience Manager Designer] Version 6.x (NPR-34325) nicht verfügbar.

**Document Security**

* Der Signaturvorgang mit HSM-basierten Zertifikaten in einer PDF-Datei kann nach der Installation von [!DNL Experience Manager] 6.4.8.0 (NPR-34309) nicht ausgeführt werden.

**Aktualisierung**

* Wenn Sie die [!DNL JBoss] Version auf 7.0.9 für [!DNL Experience Manager Forms] mit Dokument Security in einer [!DNL Linux] Umgebung aktualisieren, wird ein Fehler ausgegeben (CQ-4300546).

Informationen zu Sicherheitsaktualisierungen finden Sie auf der Seite [zu Sicherheitsbulletins für](https://helpx.adobe.com/security/products/experience-manager.html)Experience Manager.

## Hotfixes und Feature Packs, die in früheren Cumulative Fix Packs enthalten waren {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 einige interne und kundenspezifische Fehlerbehebungen enthält.

AEM Cumulative Fix Pack 6.4.8.1 ist von AEM 6.4 Service Pack 8 abhängig. Daher müssen Sie das AEM Cumulative Fix Pack 6.4.8.1 Paket nach der Installation von AEM 6.4 Service Pack 8 installieren.

Einige der wichtigsten Highlights von AEM 6.4.8.1 sind:

* Der anonyme Zugriff auf CRXDE Lite ist nicht erlaubt, um die Sicherheit zu erhöhen. Stattdessen werden die Benutzer zum Anmeldebildschirm weitergeleitet. See [developing with CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* Die Paketfreigabe-Integration mit Adobe Experience Manager wurde entfernt.
* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.21 aktualisiert.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

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
* Dispatcher Health Check zeigt eine `Invalid cookie header` Warnmeldung in den Protokolldateien an (NPR-33630).
* Die Salesforce-Integration ist anfällig für SSRF (NPR-32671).
* XSS in PreferencesServlet (NPR-33439) reflektiert.

#### Assets {#assets-6481}

* Die Anzahl der Vermögenswerte ändert sich nicht entsprechend der Änderung der Auswahl in der Ansicht der Liste (NPR-33285).

* Die Schaltfläche Weiter ist nicht aktiviert, wenn der übergeordnete Knoten ausgewählt (wobei ein einzelner untergeordneter Ordner sichtbar ist) und anschließend der untergeordnete Ordner ausgewählt wird (NPR-33284).

* Die Touch-Benutzeroberfläche kann nicht (mit Fehler) für Benutzer gerendert werden, die keinen Lesezugriff im Repository-Stammordner haben, wenn der DMS7- oder Hybrid-Modus aktiviert ist (NPR-33175).

* Die GB18030-Zeichen in Ordner- und Asset-Namen werden in den heruntergeladenen ZIP-Dateien leer (NPR-33150).

* Der Ordner &quot;Extra&quot;wird beim intelligenten Zuschneiden eines Assets erstellt, das sich in einem übergeordneten Ordner mit Punkt- `.` Zeichen im Namen befindet (NPR-32755).

* Verzögertes Laden wird nicht ausgelöst, und es werden nicht mehr als 100 Assets angezeigt, die ausgewählt werden, um die Aufgaben aus dem Benachrichtigungs-Posteingang zu überprüfen (NPR-32749).

* Die Linkseite zum Teilen der Sammlung ist aufgrund einer Änderung der Korallen-Info (NPR-32510) beschädigt.

* Die Verarbeitung von Assets während des Massen-Uploads wird blockiert (CQ-4293916).

* Anfälligkeit für SSRF in Experience Manager (NPR-33437).

#### Plattform {#platform-6481}

* Der [!DNL Sling] Filter wird nicht aufgerufen, wenn der `sling:match` Karteneintrag unter `/etc/maps` (NPR-33308) erstellt wird.
* Alle Spülmittel werden beim Deaktivieren einer Seite ausgelöst (NPR-32941).
* Wenn Sie die `ScriptProcessor` API zum Minimieren einer JavaScript-Bibliothek verwenden, wird in der Protokolldatei eine Fehlermeldung angezeigt, die darauf hinweist, dass der JavaScript-Code nicht dem strikten Modus entspricht. Die API bietet keine Option zum Aktivieren oder Deaktivieren des strikten Modus. (NPR-32746).
* Wenn eine SQL-Abfrage länger ausgeführt wird (z. B. 7 Stunden), reagiert AEM nicht mehr (NPR-33043).

#### Benutzeroberfläche {#ui-6481}

* Wenn Sie einen Pfad über ein Auswahldialogfeld suchen oder durchsuchen, werden im Auswahldialogfeld alle Inhalte des ausgewählten JCR-Knotens angezeigt, anstatt nur die Bilder anzuzeigen (NPR-32712).

#### Übersetzungsprojekte {#tranlation-6481}

* Ein `NullPointerException` Fehler wird in den Protokollen zur Ausführung eines Übersetzungsauftrags (NPR-32220) angezeigt.

#### Integrationen {#integrations-6481}

* Site-übergreifende Skripterstellung für JSON (NPR-32745).

#### Communities {#communities-6481}

* Autoren werden nach der Erstellung einer neuen Gruppe nicht in den Abschnitt [!UICONTROL Community Group] unter [!DNL Internet Explorer] 11 (NPR-33202) umgeleitet.
* Beim Zugriff auf die [!UICONTROL Aktivität Stream] -Seite (NPR-33152) tritt ein Fehler auf.
* Durch Bearbeiten einer [!DNL Communities] Gruppe und Ändern der Miniaturansicht wird das Gruppenminiaturbild nicht aktualisiert (NPR-32603).
* Beim Erstellen einer Version von Benachrichtigungen und Abonnements von User Generated Content (UGC) wird eine falsche ID der Quellseite gespeichert (CQ-4289703).
* Site-übergreifendes Skriptproblem (NPR-33212).

#### Workflow {#workflow-6481}

* Einige Komponenten werden nicht im Popup-Dialogfeld angezeigt, wenn ein Benutzer einen Workflow abgeschlossen hat, der einen Schritt [!UICONTROL zum] Dialogteilnehmer enthält (NPR-32989).

* Die [!UICONTROL Option &quot;Zeitschiene] &quot;in der linken Leiste dauert länger als erwartet (NPR-32850).

#### Formulare {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack enthält keine Korrekturen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* Correspondence Management: Wenn ein Benutzer Inhalte aus einem [!DNL Word] Dokument einfügt, behält das Textfragment keine Formatierung bei (NPR-33213).
* Adaptives Forms: Eine neue Zeile zu einer Zeichenfolge in einem Wörterbuch für adaptive Formulare fügt dem Wörterbuch Zeichen hinzu (NPR-33265). `&#xa;`
* Adaptives Forms: Der Benutzer kann ein adaptives Formular nicht mit mehr als einer Anlage speichern (NPR-33214).
* Adaptives Forms: `AddInstance` und `RemoveInstance` Methoden für die Instanz Manager-Klasse fügen keine dynamische Anzahl von Instanzen für verzögerte Ladefragmente hinzu [!DNL Internet Explorer 11] (NPR-33201).
* Adaptives Forms: Analytics, das auf einem adaptiven Formular aktiviert ist, das in eine [!DNL Sites] Seite eingebettet ist, zeichnet keine Daten für die Ereignisse &quot;Senden&quot;und &quot;Abbrechen&quot;auf (NPR-31359).
* Adaptives Forms: Wenn ein Benutzer den Inhalt aus einem [!DNL Word] Dokument in ein adaptives Formular einfügt und es sendet, enthält das gesendete adaptive Formular Unicode-Zeichen. Darüber hinaus schlägt die Konvertierung von PDF in PDF/A aufgrund von Unicode-Zeichen (NPR-33348) fehl.
* BackendIntegration: Formulardatenmodellanforderungen schlagen fehl, da der Aktualisierungstoken aufgrund eines inaktiven Status (NPR-33168) abläuft.
* Dokument-Dienste: Der Convert PDF-Dienst kann PDF-Dokumente nicht in PostScript konvertieren, da Gibson-JARs für [!DNL WebLogic] den [!DNL Linux] Server fehlen (NPR-33515, CQ-4292239).
* Dokument-Dienste: Wenn ein Benutzer eine Textdatei in eine PDF-Datei konvertiert, werden japanische Zeichen nicht korrekt dargestellt (NPR-33239).
* XSS mit GuideSOMProviderServlet (NPR-32701) gespeichert.

## Install 6.4.8.2 {#install}

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

* AEM 6.4.8.2 requires AEM 6.4.8.0. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.4.8.2 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Bevor Sie das kumulative Fix Pack installieren, stellen Sie sicher, dass Sie eine Momentaufnahme oder eine erneute Sicherung Ihrer AEM erhalten.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz gerade von einer früheren Version aktualisiert wurde). Dennoch wird dies allgemein empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!NOTE]
>
>Adobe rät davon ab, das AEM 6.4.8.2-Paket zu entfernen oder zu deinstallieren.

### Installieren des kumulativen Fix Packs {#install-cumulative-fix-pack}

Führen Sie die folgenden Schritte aus, um das Cumulative Fix Pack auf einer vorhandenen AEM 6.4.8.0-Instanz zu installieren:

1. Klicken Sie auf den Link [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-2.0.zip) , um das Paket herunterzuladen.

1. Open [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) and click **[!UICONTROL Upload Package]** to upload the package.

1. Select the package name and click **[!UICONTROL Install]**.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird in einigen Fällen während der Installation von 6.4.8.2 frühzeitig beendet.**
>
>Es wird daher empfohlen, auf die Stabilisierung der Fehlerprotokolle zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles warten, bevor sichergestellt wird, dass die Installation erfolgreich ist. In der Regel trifft dies auf Safari zu, kann aber mitunter auch auf allen anderen Browsern der Fall sein.

### Automatische Installation {#auto-installation}

Es gibt zwei Möglichkeiten, AEM 6.4.8.2 automatisch in einer laufenden Instanz zu installieren:

A. Platzieren Sie das Paket in ..Ordner */crx-quickstart/install*, während der Server läuft. Das Paket wird automatisch installiert.

B. Use the [HTTP API from Package Manager](https://helpx.adobe.com/de/experience-manager/aem-previous-versions.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>AEM 6.4.8.2 unterstützt keine Bootstrap-Installation.

### Bestätigen der Installation {#validate-install}

1. Auf der Seite „Produktinformationen“ (*/system/console/productinfo*) sollte nun unter „Installierte Produkte“ die aktualisierte Version „Adobe Experience Manager, Version 6.4.8.2“ angezeigt werden.
1. Alle OSGI-Bundles sind in der OSGI-Konsole entweder AKTIV oder FRAGMENT. (Verwenden Sie die Webkonsole: /system/console/bundles.)
1. Das OSGI-Bundle org.apache.jackrabbit.oak-core ist auf Version 1.8.17 oder höher (Web-Konsole verwenden: /system/console/bundles).

To determine the certified platform for running with this release of AEM Sites and Assets, see [Technical Requirements](../sites-deploying/technical-requirements.md).

>[!NOTE]
>On successful installation of the package, an informational message appears indicating that the content package has installed successfully, such as **&quot;Content Package AEM-6.4-Service-Pack-8 installed successfully.&quot;**

### Aktualisieren von Viewern für dynamische Medien (5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.2 enthält eine neue Version von Dynamic Media Viewern (5.10.1), die die Suche nach Duplikat auf der Seite &quot;Bildvorgabe&quot;ermöglicht. Kunden mit dynamischen Medien wird empfohlen, den folgenden Befehl auszuführen, um die standardmäßigen Viewer-Vorgaben in den aktuellen Zustand zu bringen.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

, der neue Viewer-Vorgaben in /conf kopieren wird.

### Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in AEM Forms werden über ein separates Add-on-Paket bereitgestellt.

1. Stellen Sie sicher, dass Sie das AEM Cumulative Fix Pack installiert haben.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installieren des AEM Forms JEE-Installationsprogramms {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in AEM Forms JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für AEM Forms JEE und zur Konfiguration nach der Bereitstellung finden Sie unter [AEM Forms JEE-Patch-Installationsprogramm 0019](jee-patch-installer-64.md).

### Uber Jar {#uber-jar}

The Uber Jar for AEM 6.4.8.2 is available in the [Adobe Public Maven repository](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.2/uber-jar-6.4.8.2.jar).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.2</version>  
      <scope>provided</scope>
</dependency>
```

## Entfernte/veraltete Funktionen {#removed-deprecated-features}

Dieser Abschnitt listet Funktionen und Fähigkeiten auf, die aus AEM 6.4 entfernt oder veraltet sind.

| Bereich | Funktion | Ersatz | Version |
|---|---|---|---|
| Assets | Tag-Aktion für Teilassets verwalten | Kein Ersatz vorhanden. | AEM 6.4.2.0 |
| Assets und Adobe Creative Cloud-Integration | [Die Freigabe](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) von Creative Cloud-Ordnern wurde in AEM 6.2 eingeführt, um kreativen Benutzern Zugriff auf Assets aus AEM zu gewähren. Eine neue Funktion der Creative Cloud-Anwendung, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus.  Adobe wird die Ordnerfreigabe nicht weiter verbessern. Während die Funktion in AEM enthalten ist, wird Kunden dringend empfohlen, den Ersatz zu verwenden. | Adobe Asset Link oder Desktop-App. Weitere Informationen finden Sie im Artikel zur [AEM Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Bekannte Probleme {#known-issues}

* Wenn Sie ein Upgrade von Experience Manager 6.4.8.2 auf Experience Manager 6.5 durchführen, werden einige Pakete möglicherweise nicht als `Active`angezeigt. Installieren Sie das neueste Experience Manager 6.5 Service Pack 6, um das Problem zu beheben.

Informationen zu den bekannten Problemen im AEM 6.4.8.0 Service Pack finden Sie unter [AEM 6.4.8.0 Service Pack - Versionshinweise](sp-release-notes.md).

## OSGi-Bundles und Inhaltspakete sind enthalten {#osgi-bundles-and-content-packages-included}

Die folgenden Dokumente Liste der OSGi-Pakete und Content Packages in AEM 6.4.8.2.

Liste der in AEM 6.4.8.2 enthaltenen OSGi-Bundles

[Datei laden](assets/6.4.8.2_osgi_bundles.txt)

Liste der in AEM 6.4.8.2 enthaltenen Inhaltspakete

[Datei laden](assets/6.4.8.2_content_packages.txt)

## Hilfreiche Ressourcen {#helpful-resources}

* [Versionshinweise zu AEM 6.4](../release-notes/release-notes.md)
* [AEM-Produktseite](https://www.adobe.com/solutions/web-experience-management.html)
* [Dokumentation zu AEM 6.4](https://helpx.adobe.com/de/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

## Eingeschränkte Sites {#restricted-sites-new}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Kundensupport.](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
