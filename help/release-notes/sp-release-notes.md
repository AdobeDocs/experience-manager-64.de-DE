---
title: Versionshinweise zum AEM 6.4 Service Pack
seo-title: Versionshinweise zum AEM 6.4 Service Pack
description: Spezifische Versionshinweise zu Adobe Experience Manager 6.4 Service Packs.
seo-description: Spezifische Versionshinweise zu Adobe Experience Manager 6.4 Service Packs.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
translation-type: tm+mt
source-git-commit: a2808c1861b6853b5e9505ad189f296f7ebd2572
workflow-type: tm+mt
source-wordcount: '21579'
ht-degree: 25%

---


# Versionshinweise zum AEM 6.4 Service Pack {#aem-service-pack-release-notes}

## Versionshinweise {#release-information}

| Produkte | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.0 |
| Typ | Service Pack-Version |
| Datum  | 05. März 2020 |
| Download-URL | AEM 6.4.8.0 auf [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## Was ist in AEM 6.4.8.0 enthalten?{#what-s-included-in-aem}

AEM 6.4.8.0 ist ein wichtiges Update, das neue Funktionen, von wichtigen Kunden angeforderte Erweiterungen sowie Leistung, Stabilität und Sicherheitsverbesserungen umfasst. Dieses Update wurde seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht.****

Es ist auch kumulativ, was bedeutet, dass 6.4.8.0 alle AEM 6.4 Service Packs umfasst, die vor ihm veröffentlicht wurden.

Zu den wichtigsten Merkmalen dieses Service Packs gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.20 aktualisiert.

* Die WCM-RTE-Funktion wird für japanische Websites unterstützt.

* Die Verarbeitung von Wortumbrüchen und Zeilenumbrüchen wird für japanische Websites unterstützt.

* Es wurde Unterstützung für die Verwendung der BUNSETSU-Methode hinzugefügt, um japanische Sprachsätze und -zeilen an geeigneten Positionen zu unterbrechen.

* Die CCR-Benutzeroberfläche für Correspondence Management unterstützt jetzt Dezimalwerte für das deutsche Gebietsschema.

* Die Integration von Formulardatenmodellen mit dem SOAP-Webdienst unterstützt jetzt Auswahlgruppen oder Attribute für Elemente.

* AEM Assets ist jetzt mit Brand Portal über [!DNL Adobe I/O] konfiguriert.

* Die in ContextHub enthaltene jQuery-Version wurde auf 3.2.1 aktualisiert.

## Liste der Änderungen {#list-of-changes}

### Sites {#sites}

* Wenn eine URL einer AEM Sites-Seite einen Doppelpunkt oder ein Prozentsymbol enthält, reagiert der zugrunde liegende Browser nicht mehr und die CPU-Zyklen zeigen eine Spitze (NPR-32368, NPR-31917).
* Wenn eine AEM Sites-Seite zur Bearbeitung geöffnet und eine Komponente kopiert wird, steht die Einfügeaktion für einige Platzhalter nicht zur Verfügung (NPR-32328).
* Der Arbeitsablauf für die Anforderung der Aktivierung umfasst keine referenzierten Assets (NPR-32304).
* Wenn ein Blueprint erstellt wird und die Anzahl der Datensätze mehr als 80 beträgt, werden nur die ersten 80 Datensätze angezeigt. Blueprint zeigt leere Zeilen für die übrigen Datensätze an (NPR-32058).
* Benutzer dürfen ein Inhaltsfragment speichern, ohne in den erforderlichen Feldern Informationen anzugeben (NPR-31988).
* Die automatische Navigation funktioniert nicht für Pfade, die in einer Core Experience Fragment-Komponente (NPR-31921) konfiguriert sind.
* Wenn Sie den Typ einer Tabellenzelle im Rich Text Editor (RTE) ändern, tritt der folgende Fehler auf:
   `Error: No common ancestor found, cannot continue` (NPR-31916).
* Wenn Inhalte innerhalb desselben Ordners verschoben werden, ist die Option zum Verschieben der Seite deaktiviert (NPR-31841).
* Unterstützung zur Unterteilung japanischer Sprachsätze mit der BUNSETSU-Methode und Umbruchlinien an der entsprechenden Position (NPR-31836) hinzugefügt.
* Wenn Sie einen Hyperlink im Rich Text Editor (RTE) bearbeiten, wird der neu ausgewählte Pfad nicht gespeichert (NPR-31659).
* Wenn Sie eine Multifield-Komponente löschen und den Löschvorgang rückgängig machen, wird die Komponente wiederhergestellt, die Daten werden jedoch nicht wiederhergestellt (NPR-31617).

### Assets {#assets}

* Ein Ordner ohne Namen wird in Dynamic Media Classic erstellt, während ein Asset in Experience Manager mit Dynamic Media Classic-Konfiguration (NPR-32440) von einem Ordner in einen anderen verschoben wird.

* Die Detailseite &quot;Assets&quot;von PDF-Dateien zeigt keine Aktionsschaltflächen in Experience Manager an, der im Dynamic Media Scene7-Modus ausgeführt wird (NPR-32316).

* Asset- und Videodarstellungen können nicht gelöscht werden (NPR-32213).

* Das Kalendersymbol für geplante Aktivierungen wird nicht in der Statusspalte (in der Classic UI der DAM-Asset-Auflistung) für Assets angezeigt, deren Aktivierung für ein späteres Datum und eine spätere Uhrzeit geplant ist (NPR-32198).

* Die Beziehung von Vermögenswerten wird überschrieben, wenn Vermögenswerte mit mehr als einem Vermögenswert unter Verwendung von Sonstige (NPR-32196) verbunden sind.

* Die Schaltfläche &quot;Speichern&quot;importiert kein Remote Set, wenn der Benutzer im Set-Editor im Dynamic Media Client keine Änderungen vorgenommen hat (NPR-32178).

* Die Erfassung von PSD-Assets verursacht CPU-Spitzen und nicht reagierende Experience Manager-Autoreninstanz (NPR-32165).

* Ausnahmefehler bei nicht bestimmtem Arbeitsspeicher, wenn eine große ZIP-Datei in Experience Manager DAM (NPR-32155) hochgeladen wird.

* Die URLs im Versionsverlauf werden auf der Eigenschaftenseite für Assets unter &quot;Verwiesen auf&quot;angezeigt (NPR-31889).

* Die Rückgängigmachung der Veröffentlichung im Markenportal auf der Seite &quot;Veröffentlichung verwalten&quot;schlägt bei Unterordnern eines veröffentlichten Ordners fehl (NPR-31835).

* Dynamic Media-Videokodierungen können nicht hochgeladen werden, wenn die Scene7 Cloud-Konfiguration in einem privaten Ordner `/conf` statt `/conf/global` (NPR-31779) abgelegt wird.

* Das Bild wird auf der Zeitleiste nicht angezeigt, nachdem Anmerkungen hinzugefügt wurden, auf einem Experience Manager, der im Dynamic Media Scene7-Ausführungsmodus ausgeführt wird (NPR-31754).

* ZIP-Datei, die von DAM heruntergeladen wurde, kann nicht mit WinZip (NPR-31745) geöffnet werden.

### Integrationen {#integrations-6480}

* Die Dropdown-Menüs **Firma** und **Berichte** Suite werden ausgeblendet, sobald **Berichte-Quelle** beim Konfigurieren von Adobe Analytics in Experience Manager Cloud-Diensten (NPR-31729) ausgewählt wurde.

* Adobe Campaign-Eigenschaften werden nicht bereinigt, wenn eine Sprachkopie eines mit einem Adobe Campaign verknüpften Newsletters erstellt wird, während eine Bereinigung erfolgt, wenn ein mit einem Adobe Campaign verknüpfter Newsletter kopiert oder eingefügt wird (NPR-32540).

* ReportSuitesServlet ist anfällig für SSRF (NPR-32161).

### Sling {#sling-6480}

* Nicht-deterministisches Schatten der Ressourcenbeobachtung funktioniert nicht (CQ-4286466).

### Projekte {#projects-6480}

* Schaltfläche &quot;Erstellen&quot;ist für den Benutzer nicht sichtbar, auch wenn der Benutzer berechtigt ist, ein Projekt im Unterordner zu erstellen (NPR-31831).

* Die Funktion zum Wechseln zwischen der Ansicht der Karte, der Ansicht der Liste und der Ansicht des Kalenders funktioniert nach Auswahl der Kalenderfunktion in der Ansicht der Projekte (NPR-31829) nicht.

### Übersetzung {#translation-6480}

* Bei der Erstellung von Übersetzungsprojekten für mehrere Sprachen wird das Projekt nur für einige der Sprachen statt für alle erstellt. Im Protokoll (NPR-32212) wird ein Fehler (Ressourcenauflöser ist bereits geschlossen) angezeigt.

### WCM-MSM {#wcm-msm-6480}

* Berechtigungsprobleme führen dazu, dass beim Verschieben von Seiten in einem Entwurf Fehler angezeigt werden (NPR-32610).

### WCM-Seiten-Editor {#wcm-page-editor-6480}

* Der Browser reagiert nicht mehr, wenn er versucht, einer Seite mit einem bestimmten URL-Format eine Komponente hinzuzufügen (NPR-32368, NPR-31917).

### WCM-Admin-Benutzeroberfläche {#wcm-admin-ui-6480}

* Veröffentlichung verwalten enthält keine referenzierten Assets in der Anforderung des Arbeitsablaufs für die Aktivierung (NPR-32304).

### Communities {#communities}

* Das Miniaturbild der Gruppe für Gruppen kann nicht aktualisiert werden (NPR-32603).

### Brand Portal {#brand-portal}

* Beim Rückgängigmachen der Veröffentlichung von Metadaten-Schemas in AEM Assets wird eine Fehlermeldung angezeigt, obwohl das Schema im Backend entfernt wurde (CQ-4286871).

### Foundation-Benutzeroberfläche {#foundations-ui-6480}

* Ungültige Zeichen werden in der URL angezeigt, die einer Schaltflächenkomponente hinzugefügt wird (NPR-32684).

### Formulare {#forms}

>[!NOTE]
>
>Das AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [AEM Forms-Add-On-Paket installieren](#install-aem-forms-add-on-package) und [AEM Forms JEE-Installationsprogramm installieren](#install-aem-forms-jee-installer).

* Designer: Wenn die Tagging-Option aktiviert ist, wird der Rand des Teilformulars in der generierten PDF-Ausgabe (NPR-32546, NPR-32322) ausgeblendet.

* Designer: Wenn eine Tabelle zusammengeführte Zellen enthält, schlägt der Barrierefreiheitstest für die Ausgabe-PDF-Datei fehl, die mithilfe des Output-Dienstes (NPR-32079) aus einem XDP-Formular konvertiert wurde.

* Dokument Security: Eine geschützte PDF-Datei kann nicht offline geöffnet werden, wenn die Option DisableGlobalOfflineSynchronizationData auf True (NPR-32080) eingestellt ist.

* Dokument Security: Probleme beim Öffnen einer geschützten PDF-Datei nach einem Upgrade von ES4 auf AEM 6.3 (NPR-32170).

* Dokument-Dienste: Beim Konvertieren einer PDF-Datei in ein PDF/A-Dokument mit der toPDFA-Konvertierungsmethode (NPR-32663) wird eine Fehlermeldung angezeigt.

* Dokument-Dienste: Beim Anwenden des Reader Extensions-Dienstes auf eine PDF-Datei (NPR-32639) wird eine Ausnahme angezeigt.

* Dokument-Dienste: Beim Zusammenstellen und Konvertieren von XDP-Dateien in PDF-Dateien wird eine Fehlermeldung angezeigt (NPR-31821).

* Analytics zeigt keine angemessenen Ergebnisse beim Senden oder Abbrechen von Formularen auf einer Siteseite (NPR-31359) an.

### In früheren Service Packs enthaltene Hotfixes und Feature Packs {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

AEM 6.4.7.0 ist ein wichtiges Update, das Funktionen für Leistung, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen umfasst, die seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht wurden.****

Es ist auch kumulativ, was bedeutet, dass 6.4.7.0 alle AEM 6.4 Service Packs vor der Veröffentlichung beinhaltet.

Einige der wichtigsten Highlights von AEM 6.4.7.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.17 aktualisiert.
* Unterstützung zum Festlegen der Version einer Siteseite beim Löschen hinzugefügt.
* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der Ansicht **DAM Liste** und in den Suchergebnissen für Assets in der Ansicht **Liste** (NPR-31311) hinzugefügt.
* Die Sortierung von Assets auf Grundlage der Spalte **Name** wurde in der Ansicht **Liste** zugelassen.
* Stapelgröße und Zeitüberschreitung für Arbeitsablaufschritte für Neu verarbeiten und Batch Upload können jetzt in der Benutzeroberfläche in Dynamic Media konfiguriert werden.
* Die Einstellung `pdfBrochure` wurde in der Scene7-Cloud-Konfiguration auf &quot;false&quot;gesetzt, um Speicher beim IPS zu speichern.

##### Assets {#assets-6470}

**Produktverbesserungen**

* Die Exportversion des API-Pakets `package com.day.cq.dam.handler.standard.msoffice`, die von `dam-handler` Bundle unterstützt wird, wird auf 6.0.0 aktualisiert (CQ-4279059).
Wenn Sie das Paket `com.day.cq.dam.handler.standard.msoffice` in Ihrer benutzerdefinierten Implementierung verwenden, wird empfohlen, das `dam-handler`-Bundle mit der neuesten uber-JAR zu kompilieren.

* Neue Spalte für das erstellte Datum, die sortierbar ist, wurde in der DAM Liste Ansicht und in den Asset-Suchergebnissen in der Liste Ansicht (NPR-31311) hinzugefügt.

* Die Sortierung nach der Spalte &quot;Name&quot;ist in der Ansicht &quot;Liste&quot;zulässig (NPR-31299).

**Fehlerkorrekturen**

* Metadaten für einige PDF-Dokumente werden beim Ändern des Titels (NPR-31575) nicht aktualisiert und im PDF-Format gespeichert.

* Assets mit dem Symbol &quot;+&quot;im Dateinamen können nicht gelöscht werden (NPR-30588).

* Die Eigenschaften von DAM-Ordnern zeigen nicht die hinzugefügten Benutzer oder Gruppen (die durch LDAP-Synchronisierung erstellt wurden) in geschlossenen Benutzergruppen (NPR-30555) an.

* Sonderzeichen, die in der Betreffzeile von E-Mail-Vorlagen auftreten, werden nicht richtig angezeigt (NPR-30547).

* Beim Verschieben von Assets aus einem Ordner in einen anderen im Dynamic Media Scene7-Runmode (NPR-31631) werden die Asset-Namen in Kleinbuchstaben geändert.

* Die Namen des Bildsatzes werden in Scene7 in Kleinbuchstaben geändert, wenn Bildsatz (oder Mediaset) erstellt und mit einer entsprechenden Benennungskonvention in DAM (NPR-31576) benannt wird.

* Der Dynamic Media Encode Video-Arbeitsablauf kann keine Miniaturansicht für das Video generieren, das vom Scene7 in den Dynamic Media Scene7-Ausführungsmodus migriert wird (NPR-31523).

* Interner Serverfehler wird beim Verwenden des Filters zur Suche nach Sets beobachtet, AEM unter Dynamic Media - Scene7-Runmode (NPR-31388) ausgeführt wird.

* Beim Bearbeiten eines Remote-Bildsatzes wird ein Fehler festgestellt, da sich das Bild im Ordner befindet, der dem Namen der Scene7-Firma entspricht (NPR-31347).

* Assets, die Referenzen enthalten, werden nicht veröffentlicht (DM) (NPR-31179).

* Der für den Modus „Dynamic Media Hybrid“ konfigurierte Wert zum Ablauf (Client-Cache-Zeit bis zum Livestream) wird nicht in die Umgebung für die Bereitstellung dynamischer Medien repliziert (NPR-31126) .

* Das Hochladen von AEM Dynamic Media - Scene7-Runmode zu Scene7 dauert zu lange. (NPR-30926)

* Nachdem Sie eine Seite mit Dynamic Media-Komponenten erstellt haben, während Sie die gleiche Komponente veröffentlichen, wird der Benutzer von der Autoreninstanz, die auf Dynamic Media - Scene7-Runmode ausgeführt wird, aufgefordert, die dmscene7-Konfiguration zu veröffentlichen (NPR-30880).

* Der Wert des Parameters &quot;asset&quot;im Viewer-Einbettungscode bleibt unverändert, nachdem die Werte in den Feldern &quot;Title after move&quot;und &quot;Name after move&quot;unter Dynamic Media - Scene7 (NPR-30745) geändert wurden.

* Die Suchergebnisseite der Touch-Benutzeroberfläche (über Omniture) scrollt automatisch nach oben und verliert die Bildlaufposition des Benutzers (NPR-31306).

* DAM Ereignis Purge löscht die neuesten (maxSavedActivities) Ereignis-Daten und speichert die zuvor erstellten Daten (NPR-30870).

* Asset-Titel und Namensänderung wurden nach dem Verschieben in einen Zielordner, in dem Trigger unendliches Scrollen durchführen, während sie ausgewählt wurden, nicht beibehalten (NPR-30647).

* Sammlungen werden aus der Ansicht entfernt, wenn Sie einen Filter in AEM Assets anwenden, der über Adobe Asset Link aufgerufen wird (CQ-4280534).

* Stapelgröße und Zeitüberschreitung für Arbeitsablaufschritte für &quot;Neu verarbeiten&quot;und &quot;Batch Upload&quot;sind nicht über die Benutzeroberfläche konfigurierbar und müssen in CRXDE eingestellt werden. Der Arbeitsablauf muss zweimal synchronisiert werden (CQ-4281254).

* Workflow-Schrittname für Batch-Uploads und einfachen Upload-Schritt ist in Scene7 identisch, was zu Verwirrung führt (CQ-4281176).

* Der Arbeitsablauf für die Neuverarbeitung in Scene7 wird angehalten, wenn einem Asset der Metadaten-Knoten fehlt (CQ-4281170).

* Der Schritt BatchUpload im Arbeitsablauf für die Neuverarbeitung funktioniert nicht für den Ordner mit dem Video-Asset (CQ-4280630).

* Für an DM gesendete PDF-Optionen ist &quot;extractKeywords&quot;standardmäßig auf &quot;true&quot;gesetzt (CQ-4280101).

* Null-Punkt-Ausnahme wird beim Ausführen des Scene7-Arbeitsablaufs für einen Ordner mit Nicht-DM-Assets beobachtet (CQ-4279555).

* Beim Umbenennen von Assets in AEM kann nicht mit Szene 7 synchronisiert werden, wenn in Scene 7 bereits ein Asset mit einem Duplikat-Namen vorhanden ist (CQ-4276763).

* Die Zip-Datei, die per E-Mail zum Herunterladen von Assets gesendet wird, kann nicht entpackt werden, wenn ein Benutzer mit der Berechtigung &quot;Lesen&quot;versucht, sie zu öffnen (CQ-4277925).

* Der Arbeitsablauf für die PPT-Wiedergabe kann keine Darstellungen der hochgeladenen PPT-Dateien generieren, da AEM 6.4 nicht auf com.adobe.granite.poi Version 2.0.28 (CQ-4279059) aktualisiert werden kann.

* PDF-Dateien werden nicht indiziert und der Inhalt in ist nicht durchsuchbar (CQ-4278916).

##### Sites {#sites-6470}

* Wenn Launches mit Promote only Modified pages und Promote Launches mit modifizierten Seiten durchgeführt werden, werden nur die geänderten Seiten beworben. Wenn die zu bewertende Liste korrekt ist, werden die nicht geänderten Seiten weiterhin am Ende der Liste angezeigt (NPR-31314).

* Wenn eine AEM Sites-Seite an einen anderen Speicherort verschoben wird, werden ihre Eigenschaften nicht entsprechend aktualisiert, um ihren neuen Speicherort widerzuspiegeln (NPR-31265).

* Bei einem neuen Blueprint werden nur die ersten 40 Datensätze angezeigt, wenn die Anzahl der Datensätze mehr als 40 beträgt. Blueprint zeigt leere Zeilen für die übrigen Datensätze an (NPR-31182).

* Bei einer großen Anzahl von LiveCopies dauert die Wiedergabe der Vorschau in der LiveCopy-Übersicht sehr lange (NPR-30945).

* Unterstützung zum Festlegen einer Version einer Seite beim Löschen hinzugefügt. Wenn die Versionsverwaltung für die gelöschte Seite deaktiviert ist, kann AEM Sites solche Seiten nicht wiederherstellen (NPR-30891).

* Wenn ein Benutzer japanische oder koreanische Zeichen in die Eigenschaft description eines Menüs einfügt, werden im Menü verzerrte Zeichen für japanischen und koreanischen Text angezeigt (NPR-31331).

* Wenn ein Benutzer sich auf Felder in der linken Schiene konzentriert und zum Einfügen von Inhalten einen Tastaturbefehl verwendet, wird der Inhalt der Zwischenablage des Seiteneditors anstelle des Inhalts eingefügt, der aus den Feldern der linken Schiene kopiert wurde (NPR-31169).

* Wenn ein Benutzer ein Inhaltsfragment bearbeitet, wird die bereits gelöschte Variante des Inhaltsfragments wiederhergestellt (NPR-31178).

* Die Abfrage der Inhaltsfragmentmodelle ist ineffizient. Es ist sehr langsam, wenn die Instanz viele Seiten hat und einen Fehler auslöst (NPR-30666).

* Beim Speichern des Inhaltsfragmentmodells wird die Uhrzeit im Datums- und Uhrzeitfeld auf 00:00 (NPR-30540) eingestellt.

##### Integrationen {#integrations-6470}

* Beim Konfigurieren von Adobe Launch wird ein Schrägstrich (/) in der Bibliotheks-URL (NPR-30700) vorangestellt.

* Die ContextHub-Leistung verschlechtert sich nach der Veröffentlichung (NPR-30884).

##### Sling {#sling-6470}

* Aktualisieren Sie die Bundle-Version des Webconsole-Sicherheitsanbieters auf 1.2.4, um die Abhängigkeit der starchpad starter API vom Webconsolesecurityprovider (NPR-30885) zu entfernen.

##### Plattform {#platform-6470}

* Aktualisierungen der Puffergrößenkonfiguration für den Jetty-basierten HTTP-Dienst werden nicht gespeichert (NPR-30925).

* QueryBuilder unterstützt jetzt orderby fn:name() in xpath-Abfragen (NPR-31322).

* Aktualisierung von Sling Distribution Ereignis Admin auf Version 1.1.4 zur Verbesserung der Qualität von Protokollen in einer Clusterlösung (NPR-29256).

##### Foundation-Benutzeroberfläche {#foundation-6470}

* Durch Bildlauf zum Ende der Ergebnisseite mit einer großen Anzahl von Suchergebnissen stürzt der Browser ab (NPR-31332).

* Beim Wechsel von der Card-Ansicht zur Liste-Ansicht auf einer Suchergebnisseite kommt es zu einer Verzögerung, bevor ein Bildlauf durchgeführt werden kann (NPR-31280).

##### Oak {#oak-6470}

* MS Office-Dateien mit den Dateierweiterungen .docx und .xlsx, die JPEG-Bilder enthalten, können mit dem Tika-Parser (NPR-31693) nicht analysiert werden.

##### Livefyre {#livefyre-6470}

* Die Livefyre-Integration mit AEM 6.4-Aktualisierung führt zu einer Null-Punkt-Ausnahme, wenn die Integration mit dem DITA-Plugin für synthetische Ressourcen erfolgt. Die Integration funktioniert jedoch, wenn Komponenten manuell hinzugefügt werden (FYR-11066).

##### Übersetzung {#translation-6470}

* Der Pfad zum Fragment &quot;Zielerlebnis&quot;wird beim Anzeigen einer Startseite nicht aktualisiert (NPR-30830).

##### Communities {#communities-6470}

* Die E-Mail-Funktion funktioniert in einigen Fällen nicht ordnungsgemäß, auch wenn E-Mail-Nachrichten in den Benachrichtigungseinstellungen aktiviert sind. Das System löst eine Ausnahme im NotificationsActivityStreamProvider (NPR-31521) aus.
* Da keine neuen Mitglieder erstellt werden können, wird im Bildschirm &quot;Create Member&quot;in AEM Autoreninstanz (NPR-30951) ein leerer Bildschirm angezeigt.
* Benutzer kann keinen Kommentar zu einem Blog in Internet Explorer 11 (NPR-30927) posten.
* Der Administrator einer eingeschränkten Gruppe ist nicht in der Lage, die Gruppenkarte Ansicht, kann keine Schnelllink-Vorgänge (Gruppen bearbeiten/Veröffentlichen/Löschen) in AEM Autoreninstanz (NPR-30810) durchführen.
* Bei der Erstellung einer neuen Site in AEM Autoreninstanz (NPR-28840) sind keine Informationen zu Mitgliedergruppen/Gruppen sichtbar.

##### Formulare {#forms-6470}

>[!NOTE]
>
>Das AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [AEM Forms-Add-On-Paket installieren](#install-aem-forms-add-on-package) und [AEM Forms JEE-Installationsprogramm installieren](#install-aem-forms-jee-installer).

**Forms-Add-on-Paket**

**Adaptive Formulare**

* Zeichenfolgen enthalten den Wörterbuchschlüssel beim Lokalisieren von adaptiven Formularen (NPR-31109).

* Die Kontrollkästchen und Dropdown-Listen in Forms führen keine Zugänglichkeitsprüfungen durch (NPR-31282).

**HTML5-Formulare**

* Beim Generieren einer HTML5-Vorschau eines XDP-Formulars tritt Flackern auf, während Instanzen eines Teilformulars hinzugefügt werden (NPR-30907).

**Dokument Services für OSGi**

* Beim Ausführen mehrerer Threads zum Zusammenstellen der Formulare mit der Methode com.adobe.fd.assembler.service.AssemblerService.invoke() wird eine Fehlermeldung angezeigt (NPR-31164).

* Die temporären Dateien, die vom Assembler Service erstellt wurden, werden nicht automatisch gelöscht und müssen AEM neu gestartet werden (NPR-30846).

* Das Anwenden von ReaderExtension-Rechten auf PDF-Dateien führt zu einer Fehlermeldung (NPR-30930).

**Arbeitsablauf**

* OSGi-Arbeitsablauf schlägt aufgrund der 100%igen CPU-Auslastung (NPR-31234) fehl.

**Forms JEE-Installationsprogramm**

**Document Services**

* Der Convert PDF-Dienst kann PDF-Dokumente nicht in PostScript konvertieren und zeigt eine Fehlermeldung an (NPR-31267).

* Die SOAP-Endpunktkonfiguration wird zurückgesetzt, nachdem ein Patch zur Behebung eines Fehlers bei HTML in PDF angewendet wurde (NPR-31309).

**PDFG Service**

* Die mit der Admin-Benutzeroberfläche (NPR-31273) heruntergeladene Adobe PDF-Einstellungsdatei kann nicht hochgeladen werden.

#### AEM 6.4.6.0 {#experience-manager-6460}

AEM 6.4.6.0 ist ein wichtiges Update, das Funktionen für Leistung, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen umfasst, die seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht wurden.****

Es ist auch kumulativ, was bedeutet, dass 6.4.6.0 alle AEM 6.4 Service Packs vor der Veröffentlichung beinhaltet.

Einige der wichtigsten Highlights von AEM 6.4.6.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.15 aktualisiert.
* Unterstützung für die Verfolgung von dynamischer UI-Zustände im Tracking-Ereignis in der Basis-API hinzugefügt.
* Unterstützung für Darstellungen zur Bildkernkomponente hinzugefügt.

**Assets**

* Asset Sharing-Link eines Ordners mit Leerzeichen und `&`-Zeichen im Namen zeigt leere graue Karten für einige Assets an. NPR-29934: Hotfix für CQ-4270187
* Der DAM-Workflow stürzt beim Erstellen von MP4-Assets für AEM ab. NPR-30031: Hotfix für CQ-4271352
* Problem bei der Verbindung mit Adobe Smart-Tag über DataPower. NPR-30026: Hotfix für CQ-4269457
* PDF kann nicht mit OmniSearch gefunden werden. NPR-30046: Hotfix für GRANITE-26290
* Von der ACP-API generierte Asset-Pfade in URL- und Ordner-Metadaten sind nicht URL-kodiert.  GRANITE-26198: Hotfix für CQ-4271814
* Die Funktion &quot;Aufgabe für Review erstellen&quot;funktioniert aufgrund nicht definierter Nutzlast nicht. NPR-30469: Hotfix CQ-4274263
* Die Möglichkeit, die Ansicht von der Ansicht der Karte zur Ansicht der Liste zu wechseln, und umgekehrt verschwindet, nachdem eine OmniSearch-Funktion in der Asset-Auswahl durchgeführt wurde. NPR-29852: Hotfix für CQ-4269369
* (Touch-Benutzeroberfläche) Während des Assistenten zum Verwalten der Veröffentlichung werden Assets nach dem Hinzufügen der Seiten zur Replikationswarteschlange hinzugefügt, sodass einige Assets nach einigen Sekunden angezeigt werden. NPR-29985: Hotfix für CQ-4270724
* Beim Sortieren der Suchanfrage nach Relevanz werden InDesign-Dokumente zusammen mit InDesign-Vorlagen zurückgegeben. Hotfix für CQ-4273864
* Wenn der Benutzer über eine E-Mail-ID in Großbuchstaben verfügt, können die Benutzer nicht für die zuvor ausgecheckten Assets einchecken. Hotfix für CQ-4276575
* Die Konfiguration von Dynamic Media-Cloud Services im `DMHybrid`-Modus führt dazu, dass in Analytics mehrere leere Report Suites erstellt werden, ohne dass eine Report Suite-ID auf AEM gespeichert wird, was zu einer Duplizierung der Report Suite führt. Hotfix für CQ-4276855
* Warndialog wird nicht angezeigt, wenn Sie auf der Seite &quot;Verwaltetes Tag&quot;eine Werbung machen. Hotfix für CQ-4252851
* Bei Verwendung des Karussells zur Verwaltung von Tags funktioniert die Navigationsschaltfläche nicht. Hotfix für CQ-4275499
* Die Funktion zum Verschieben von Assets per Massenverschiebung ist ungültig, sodass Assets nicht verschoben werden können. Hotfix für CQ-4272987

**Sites**

* `pageinfo.json` -Anforderungen sind extrem langsam und das Laden dauert zu lange. NPR-29709: Hotfix für CQ-4269560
* `onTime` oder  `offTime` Metadateneigenschaften, die auf Assets gespeichert wurden, nicht zurückgerufen werden, wenn der AEM neu gestartet wird. NPR-30413: Hotfix für CQ-4272784
* Aufgrund des fehlerhaften Verhaltens der ConfigPostProcessor-Klasse wird durch das Aussetzen der übergeordneten Seite cq entfernt: LiveRelationship-Mischungstyp von der untergeordneten Seite. NPR-30536, NPR-30510: Hotfix für CQ-4254113
* Site-übergreifende Skripterstellung (XSS) im Arbeitsablaufdialogfeld am Beginn auf der Bearbeitungsseite für Kampagnen. NPR-29747: Hotfix für CQ-4271067
* (Klassische Benutzeroberfläche) Die Workflow-Sperrstufe deaktiviert die Registerkarte &quot;Workflow&quot;, bis die Sperre losgelassen wird. NPR-30356: Hotfix für CQ-4237557
* (IE11) Beim Einfügen von HTML-Inhalten in eine Rich Text Editor-Komponente mit defaultPasteMode = reintext wird der HTML-Code mit der Formatierung eingefügt. Daher hat defaultPasteMode keine Auswirkungen. NPR-30045: Hotfix für GRANITE-26094
* (Klassische Benutzeroberfläche) Wenn die Site-Admin-Seite neu geladen wird, sind alle Dropdown-Elemente im Menü &quot;Neu&quot;deaktiviert. NPR-29980: Hotfix für CQ-4272044
* Es können keine Stile zum Text hinzugefügt oder vorhandene Stile, die für den Inhalt erstellt wurden, bearbeitet werden. NPR-29712: Hotfix für CQ-4266249
* (Klassische Benutzeroberfläche) Assets ohne dc: Der Wert title wird im Dialogfeld für Pfadfelder ohne Titel angezeigt. NPR-30166: Backport-Anfrage für CQ-88858
* cq: Listener funktioniert nicht mit verschachtelten Komponenten, auch nicht nach dem Hinzufügen der parsys-Komponente. NPR-30422: Hotfix für CQ-4274863
* ContextHub-Fehler während der AEM- und Campaign-Integration. NPR-30625: Hotfix für CQ-4250790
* Der Wert des Abfrageparameters „resourceType“ wird in den Wert eines HTML-Tag-Attributs kopiert, das in doppelte Anführungszeichen eingeschlossen ist. NPR-29832: Hotfix für CQ-4255365
* Eine Aktualisierung der Seite ist erforderlich, nachdem Komponenten kopiert und von einer Seite auf eine andere eingefügt wurden. NPR-29982: Hotfix für CQ-4256019
* Veröffentlichen/Veröffentlichung rückgängig machen aus einem Seitenalias wird nicht unterstützt und sollte entfernt werden. NPR-30062: Hotfix für CQ-4271249
* Ungeschlossene ResourceResolver-Warnung in ExperienceFragmentsReplicationListener, die im Laufe der Zeit zu Stabilitätsproblemen führt und AEM Instanzen neu starten muss. NPR-30416: Hotfix für CQ-4257521
* Durch Verschieben von Erlebnisfragmenten, auf die auf mehr als 150 Seiten verwiesen wird, wird fragmentPath auf den Seiten, auf die verwiesen wird, nicht verändert. NPR-30556: Hotfix für CQ-4274900
* Parsing-Fehler beim Öffnen eines Inhaltsfragments, das die Zeichen Dollar (`$`) und Klammer (`{`) nacheinander geöffnet hat. Hotfix für CQ-4270266
* Das VersionPreview-Servlet schlägt beim Versuch, eine Version eines Experience Fragment in der Timeline anzuzeigen, mit NullPointerException fehl. NPR-30074: Hotfix für CQ-4271881
* Inhaltsfragmente können nicht über die Eincheckfunktion gesperrt werden. NPR-29923: Hotfix für CQ-4258785
* Fehler bei der Signaturüberprüfung im SAML-Authentifizierungshandler. NPR-30379: Antrag auf Unterstützung für GRANITE-26567

**Replikation**

* JCR-Sitzung/Ressourcen-Resolver wird während der OAuth-Implementierung bei jeder Replikation an MAC/Brand Portal durchsickert. NPR-30000: Hotfix für Granite-26196

**Sling**

* Die Reihenfolge der betroffenen Kinder, die zuvor Überschneidungen und Bestellungen verwendet haben, verursacht IndexOutOfBoundException. NPR-30408: Hotfix für Sling-8296 &amp; Sling-7375
* InactiveBundlesHealthCheck liest die Konfiguration MissingPackagesHealthCheck, sobald die Konfigurationen InactiveBundlesHealthCheck gespeichert wurden. NPR-30084: Hotfix für CQ-4272644

**Commerce**

* Katalogvorlage kann nicht über die Site-Konsole ausgeführt werden. NPR-29829: Hotfix für CQ-4271461
* Das im Produkt verwendete Asset zeigt keinen Verweis auf das Produkt im Abschnitt &quot;Referenzen&quot;des Assets an. Der Asset-Pfad wird auch nicht aktualisiert, wenn das Asset verschoben wird. NPR-30542: Hotfix für CQ-4270247

**Plattform**

* Der für AEM standardmäßig verwendete E-Mail-Absender kann über TLS 1.2 keine E-Mails an einen Remote-SMTP-Server senden. NPR-30476: Hotfix für GRANITE-26605

**Communities**

* Beim Autor gelöschte Gruppen sind nicht mit allen Herausgebern synchronisiert. NPR-29987: Hotfix für CQ-4268738
* Gelöschte Benutzer, die aus dem Feld &quot;Community-Administratoren&quot;entfernt wurden, sind nicht mit der Gruppe &quot;Mitgliedschaft&quot;synchronisiert. NPR-30389: Hotfix für CQ-4274339
* Benutzer, die Teil der Administratorgruppe sind, haben keine QuickLinks für die Gruppe. NPR-30546: Hotfix für CQ-4275579
* Beim Aktualisieren einer neu erstellten und einer vorhandenen Community-Gruppe wird die Eigenschaft in jcr überschrieben: content-Knoten und ändert ihren Namen in den Titel der ersten Seite. NPR-30109: Hotfix für CQ-4273719
* Die Schnellsuche und Suche nach Ort und Adresse funktioniert nicht, wenn die Community so eingestellt ist, dass sie mit Database Datenspeicherung Resource Provider (DSRP) funktioniert. NPR-26737: Hotfix für CQ-4258493

**Übersetzung**

* Die automatische Ausführung der Übersetzung funktioniert nicht. NPR-30499: Hotfix für CQ-4276288
* Benutzer kann Sprachkopien auf dem Inhaltspfad erstellen, der auf schreibgeschützt beschränkt ist. NPR-29937: Hotfix für CQ-4270708
* Übersetzungsfehler - Nur einige wenige Komponenten werden mit maschineller Übersetzung übersetzt. NPR-30079: Hotfix für CQ-4273764

**Integration**

* Angepasster Content wird auf der Veröffentlichungsinstanz erst nach dem Neustart der Instanz korrekt angezeigt. NPR-30421: Hotfix für CQ-4273706

**Projekte**

* Die ThumbnailPath-Werte eines DAM-Ordners werden nicht aktualisiert und zeigen auch nach dem Löschen der Assets im Ordner noch die alten Miniaturansichten an. NPR-30424: Hotfix für CQ-4273667

**UI-Konsolen**

* Site-übergreifende Skripterstellung (XSS) in den Seiteneigenschaften von Sites auf der Registerkarte &quot;Miniaturansicht&quot;. NPR-30048: Hotfix für Granite-26200

**UI-Stiftung**

* Unterstützung für die Verfolgung von dynamischer UI-Zustände im Tracking-Ereignis in der Basis-API hinzugefügt. NPR-30742, GRANITE-26322: Hotfix für GRANITE-26036

**Formulare**

>[!NOTE]
>
>Das AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [AEM Forms-Add-On-Paket installieren](#install-aem-forms-add-on-package) und [AEM Forms JEE-Installationsprogramm installieren](#install-aem-forms-jee-installer).

**Forms-Add-on-Paket**

**Adaptive Formulare**

* Die leere .css-Datei benötigt mehr Zeit, um vom Herausgeber abzurufen, was zu Leistungsproblemen führt. NPR-30558: Hotfix für CQ-4274399
* Forms, die nach der Veröffentlichung geändert werden, werden beim Veröffentlichen der Site nicht erneut veröffentlicht. NPR-30411: Hotfix für CQ-4236566

**Forms - Backend-Integration**

* Beim Erstellen des Formulardatenmodells mit der Web Service Definition Language (WSDL) wird ein Fehler ausgegeben. NPR-30388: Hotfix für CQ-4272921

**Forms – Correspondence Management**

* Sonderzeichen wie Kleiner-als (&lt;), Größer-als (>) und kaufmännisches Und (&amp;) werden in der Agent-Benutzeroberfläche kodiert. NPR-30410: Hotfix für CQ-4273887
* Beim Auslösen eines Textfragments, das Datenwörterbuchwerte enthält, reagiert die Agent-Benutzeroberfläche nicht mehr. NPR-30098, NPR-30083: Hotfix für CQ-4272204
* Die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;(CCR-Benutzeroberfläche) schlägt gelegentlich mit der Fehlervariablen (Objekt) fehl. NPR-29983: Hotfix für CQ-4273874
* Das Neuladen von Briefentwürfen schlägt mit einer Ausnahme fehl, wenn die Beschreibung von Dokument-Fragmenten Sonderzeichen wie Kleiner-als-Zeichen (&lt;), Größer-als-Zeichen (>) und kaufmännisches Und-Zeichen (&amp;) in Eigenschaften enthält. NPR-29930: Hotfix für CQ-4252762

**HTML5-Formulare**

* Wird im Durchsuchen-Modus „NonVisual Desktop Access“ zum Lesen eines HTML5-Formulars verwendet, liest der Chrome-Browser vor jeder skalierbaren Vektorgrafik (SVG) im Formularentwurf das Wort „Grafik“. NPR-30450: Hotfix für CQ-4274732

**Forms JEE-Installationsprogramm**

**Forms – Foundation JEE**

* Beim Hinzufügen oder Bearbeiten einer Webdienst-Verbindung durch Aufrufen von Webdiensten aus AEM Forms Workbench wird ein Fehler ausgegeben: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30116: Hotfix für CQ-4273217

**Forms - Document Services**

* Fehler &quot;PDF/A-Beschriftung fehlt&quot;in Acrobat Preflight. NPR-30594: Hotfix für CQ-4276032
* Datenbindungen mit einem Zeichen in PDF führen dazu, dass Reader-Erweiterungen mit dem Fehler &quot;java.lang.StringIndexOutOfBoundsException: Zeichenfolgenindex außerhalb des Bereichs: 1&quot;. NPR-30128: Hotfix für CQ-4273878
* Wenn ein Ladetest für den HTML-zu-PDF-Dienst ausgeführt wird, schlägt er mit einem Fehler fehl und die Dateitypeinstellungen werden vom AEM Forms-Server entfernt. NPR-30085: Hotfix für CQ-4272631
* Beim Reduzieren einer PDF-Datei mit Adobe Acrobat 9.1 (XFA-Version 3.0) wird der Status des PDF-Formulars nicht beibehalten: Unsichtbare Elemente im Formular werden wieder auf einen sichtbaren Status zurückgesetzt. NPR-29978: Hotfix für CQ-4270888

**Forms - Document Security**

* Das Anwenden einer Unterschrift mit Zeitstempel schlägt mit folgender Meldung fehl: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Aufruffehler. NPR-30696, NPR-30537: Hotfix für CQ-4273778
* Configuration Manager fügt keine japanischen Zeichenfolgen für lokalisierte Tabellenspalten ein. NPR-30496: Hotfix für CQ-4274868

**PDFG-Dienst**

* Verbindungsfehler beim Versuch, Word-Dokument unter Windows Server 2016 in PDF zu konvertieren. NPR-30597: Hotfix für CQ-4275652
* Bei der Verwendung des &quot;HTML in PDF&quot;-Backend-Dienstes über die &quot;phantomjs&quot;-Bibliothek wurde eine Ausnahme verweigert. NPR-30456: Hotfix für CQ-4258077
* Der Dienst &quot;maxReuseCount&quot;für &quot;HTML in PDF&quot;wird in JBoss Management Console nicht angezeigt. NPR-30303, NPR-30135: Hotfix für CQ-4273763

#### AEM 6.4.5.0 {#experience-manager-6450}

AEM 6.4.5.0 ist ein wichtiges Update, das Funktionen für Leistung, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen umfasst, die seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht wurden.****

Es ist auch kumulativ, was bedeutet, dass 6.4.5.0 alle AEM 6.4 Service Packs vor der Veröffentlichung beinhaltet.

Einige der wichtigsten Highlights von AEM 6.4.5.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.13 aktualisiert.
* Socket-Timeout und Verbindungs-Timeout wurden in den Replizierungsagenten von Brand Portal hinzugefügt.
* Verbesserungen bei der Omniture-Suche: Die Paginierungsgrenze des Suchergebnisses wurde auf 100 Seiten erhöht.
* Die Komponente `AssetDownloadServlet` OSGi wurde in AEM Veröffentlichungsinstanzen standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Herunterladen von Assets von AEM](/help/assets/download-assets-from-aem.md).
* Multi-Site-Manager bietet jetzt Unterstützung für Assets. Weitere Informationen finden Sie unter [Assets mit MSM wiederverwenden für Assets](/help/assets/reuse-assets-using-msm.md).

**Assets**

* Assets mit einem Apostroph im Dateinamen werden nicht mit Dynamic Media synchronisiert. NPR-29538: Hotfix für CQ-4270592
* Die DAM DMGGateway-Schnittstelle bietet jetzt Unterstützung für S3-Multipart. NPR-29740: Hotfix für CQ-4226303
* Das Dialogfeld zum Herunterladen von Assets zeigt beim Herunterladen von Darstellungen für ein Video in Dynamic Media eine falsche Dateigröße an. NPR-29642: Hotfix für CQ-4246202
* Assets sind nicht mehr verwendbar, nachdem der Day CQ DAM Mime Type Service Text für m3u8 angewendet hat. NPR-29276: Hotfix für CQ-4264052
* Bei der Asset-Referenzanpassung kann die Sitzung nicht gespeichert werden, wenn eines der verschobenen/umbenannten Assets Teil der Sling-Ressourcen-Sammlungen ist. NPR-29143: Hotfix für /CQ-4252605
* Kann Assets nicht verfolgen oder suchen, indem die Metadatenwerte durchsucht werden. NPR-29141: Hotfix für CQ-4260215
* Wenn Sie den Suchfilter verwenden, um eine intelligente Sammlung zu speichern, wird der Fokus durch die Klickaktion im Bedienfeld nicht beibehalten. NPR-29000: Hotfix für CQ-4240323
* Wenn Sie einen Ordner verschieben, kann ein Ordner mit Groß- oder Kleinschreibung erstellt werden. NPR-28945: Hotfix für CQ-4265234
* Leere Ergebnisse werden in OmnitureSearch angezeigt, wenn der Sammlungsname über Leerzeichen verfügt. NPR-29001: Hotfix für CQ-4236729
* Wenn Sie eine Datei mit einigen nicht unterstützten Sonderzeichen wie dem kaufmännischen Und (&amp;) umbenennen, wird ein ungültiger Ordner erstellt. NPR-29196: Hotfix für CQ-4265037
* DAM Extract Archiv für die ZIP-Dateifunktionalität ist beschädigt. NPR-29187: Hotfix für CQ-4254421
* Der Metadaten-Import sollte den Import von Metadaten ohne Registrierung von Namensräumen ermöglichen. NPR-29425, NPR-28132: Hotfix für CQ-4269445
* Das Speichern von Metadatenänderungen funktioniert nicht bei Assets, deren Name ein Anführungszeichen enthält. NPR-29395: Hotfix für CQ-4254305
* DAM-Assets können nicht verschoben werden, wenn der Dateiname Leerzeichen enthält. NPR-29270: Hotfix für CQ-4266403
* ZIP-Archive, die mit dem Deflate64-Algorithmus komprimiert wurden, können nicht heruntergeladen werden. NPR-29225: Hotfix für CQ-4253995
* Asset-Miniaturansichten werden beim Öffnen eines Ordners mit Assets mit vielen Versionen langsam angezeigt. NPR-29833: Hotfix für CQ-4271629
* Die markierte Sammlung kann nicht eingegeben werden, wenn nach Auswahl der Sammlung die Eingabetaste gedrückt wird. NPR-29723: Hotfix für CQ-4261607
* Cross-Site Scripting (XSS) Angriff durch das eingeschränkte Warnfenster. NPR-29671: Hotfix für CQ-4270133
* Das Hinzufügen von Beziehungen zu Assets schlägt bei Benutzern ohne Löschberechtigung fehl. NPR-29640: Hotfix für CQ-4269196
* Wenn der Benutzer versucht, die Seite nach dem Hinzufügen des Asset-Titels auf der Eigenschaftenseite zu schließen, wird AEM die Eigenschaftsseite erneut geöffnet. NPR-29628: Hotfix für CQ-4264929
* Das Erstellen einer großen Anzahl von Beziehungen zu einem Asset führt zu einem Fehler. NPR-28779: Hotfix für CQ-4250708
* Die Asset-Erfassung erfolgt im Scene7 Connect-Ausführungsmodus langsam. NPR-28658: Hotfix für CQ-4263007
* Ein Fehler Nicht gefangen TypeError: Die Eigenschaft &#39;split&#39; von undefined kann nicht gelesen werden, wenn versucht wird, die Suchergebnisse Ansicht. NPR-28803: Hotfix für CQ-4248371
* Die Replizierung von AEM zum Markenportal ist über lange Zeit blockiert. NPR-28914: Hotfix für CQ-4254932
* Das Verschieben von Assets in DAM führt unter Scene7 nicht zu einem ähnlichen Schritt. NPR-28957: Hotfix für CQ-4264974
* Metadaten-Aktualisierungen werden nicht an IPS weitergeleitet, wenn das Metadatenfeld in AEM aktualisiert wird. NPR-28961: Hotfix für CQ-4255393
* VersioningTimelineEventProvider sollte die Stammversion zusammen mit dem Versionskommentar bereitstellen. Hotfix für GRANITE-26063
* Die Eingabe von Daten führt zur Codeausführung auf Serverseite. Hotfix für CQ-4270246
* Multi-Site-Manager bietet jetzt Unterstützung für Assets. Hotfix für CQ-4271453, CQ-4268621, CQ-4257491
* In der AEM-Oberfläche sollte ein zusätzlicher Eintrag für die aktuelle Version des Assets im Timeline-Verlauf angezeigt werden, der den neuesten Eincheckkommentar von Adobe Asset Link enthält. Hotfix für CQ-4262864
* Das Beispielvideo wird beim Erstellen oder Bearbeiten eines MixedMediaSet nicht geladen. Hotfix für CQ-4244889
* Wenn Sie die Berechtigungen zum Löschen von Inhalten auf der AEM deaktivieren, kann der Benutzer keine Inhalte im Markenportal veröffentlichen. Hotfix für CQ-4270426
* Abfragen begrenzen Probleme mit Asset-Berichten nach einem Upgrade auf AEM 6.4.3. NPR-28588: Hotfix für CQ-4262022, CQ-4260697
* Die Download-Funktion nutzt AEM Assets über assetdownload-Servlet, sodass anonyme Benutzer alle Assets herunterladen können. NPR-27315, Hotfix für CQ-4254732

**Sites**

* Der JCR-Beschwerde-Tag-Name sollte basierend auf dem Tag-Titel automatisch gefüllt werden. NPR-28990: Hotfix für CQ-4199411
* Die Schaltfläche &quot;Vererbung abbrechen&quot;ist in einigen Feldern, die in den Seiteneigenschaften hinzugefügt wurden, nicht sichtbar. NPR-29079: Hotfix für CQ-4265686
* Die Vorschau für die Aktualisierung sollte nicht versuchen, die Live-Kopie neu zu erstellen oder sie in der Liste für die Rollout-Seiten anzuzeigen. NPR-29151: Hotfix für CQ-4266213
* (Vorlagen-Editor) Regression der Stilrichtlinie im Strukturmodus. NPR-28981: Hotfix für CQ-4264400
* Verschachtelte Live-Kopien zeigen Einsendungen von Duplikaten während der Aktualisierung an. NPR-29300: Hotfix für CQ-4268664
* Beim Veröffentlichen einer Live Copy, die eine Design Importer-Komponente enthält, schlägt das Abrufen von Verweisen für die ausgewählte Seite fehl. NPR-28944: Hotfix für CQ-4265014
* Bei Verwendung von CoralUI für Multifield wird fileReferenceParameter auf Komponentenebene statt auf Multifield-Ebene abgelegt. NPR-29536: Hotfix für CQ-4266129
* Die Designreferenz wird beim Veröffentlichen nach dem Abbrechen der Vererbung im Design Importer nicht repliziert. NPR-29648, NPR-29721: Hotfix für CQ-4269270, CQ-4271087
* Das Pfadfeld im Rich-Text-Editor wird unabhängig vom Pfad, der für die Suche angegeben ist, am Stammpfad geöffnet. NPR-29483: Hotfix für CQ-4268997
* (IE11) Kopieren Sie HTML-Inhalt in eine RTE-Komponente mit defaultPasteMode = reintext fügt den Inhalt nicht als Nur-Text ein. NPR-29432, NPR-29171: Hotfix für GRANITE-24941
* Rechtschreibprüfung für Rich Text Editor funktioniert nicht mehr in anderen Sprachen. NPR-29506: Hotfix für CQ-4264990
* Site-übergreifende Skripterstellung (XSS) auf der Seite &quot;Kampagne&quot;. NPR-29614: Hotfix für CQ-4269322
* Die Minimierung des Rich-Text-Editors im Vollbildmodus im Quellbearbeitungsmodus führt zum Verlust von Inhalten. NPR-29574: Hotfix für CQ-4260584
* (Klassische Benutzeroberfläche) Die Navigation zur letzten Registerkarte ist nicht immer möglich, wenn eine große Anzahl von Tags vorhanden ist. NPR-29544: Hotfix für CQ-4264548
* (Klassische Benutzeroberfläche) Das Navigationsmenü für Admin Consolen wird ausgeblendet und die Seite wird nicht vollständig geladen. NPR-29571: Hotfix für CQ-4264585
* Beim Hinzufügen von Komponenten zur WCM-Seite wird eine Fehlerwarnung erzeugt, wenn die Minimierung in der Instanz aktiviert ist. NPR-29396: Hotfix für CQ-4266196
* Ein Problem mit der Vererbung von Style System-Knoten aus dem übergeordneten Element. NPR-29296: Hotfix für CQ-4266041
* Eine mithilfe von Timewarp wiederhergestellte Seite sollte zum Zeitpunkt der Versionierung auf das korrekte Bild verweisen.  NPR-29431: Hotfix für CQ-4262638
* Leere Seite mit Javascript-Fehlern im Editor nach der Installation der neuesten Snapshot-Version 6.4.5. NPR-29475: Hotfix für CQ-4266196
* Beim Hinzufügen einer Komponente zu einer Parsys wird die Eigenschaft der Liste der Designkomponente nicht berücksichtigt und in einen anderen Vorlagenknotennamen mit einer ähnlichen Parsys-Struktur aufgelöst. NPR-29509: Hotfix für CQ-4269044
* cq:dropTargets-Bereich deckt die gesamte Komponente statt der Bildgröße ab, wodurch das Targeting mit eingebetteten Komponenten schwierig wird. NPR-29738: Hotfix für CQ-4268912
* Die Bildkomponente ruft nach der Verwendung des ersetzenden Bildeditors nicht den Listener &quot;after edit&quot;auf. NPR-29616 Hotfix für CQ-4268065
* Problem beim Einrichten der Social-Veröffentlichung für Facebook. NPR-29212: Hotfix für CQ-4266630
* Beim Weiterleiten von Launches für geänderte Seiten werden Anpassungen sowohl im Quell- als auch im Launch-Zweig berücksichtigt. NPR-29308: Hotfix für CQ-4266746
* Die gerenderte Miniaturansicht im Inhaltsfragment zeigt eine interne Kalenderdarstellung für das Datums- und Uhrzeitfeld an. NPR-29531: Hotfix für CQ-4269362
* Es kann kein Tag per Massen zu Seiten mit verschiedenen Tags hinzugefügt werden. NPR-28729: Hotfix für CQ-4262922
* Das Symbol &quot;Geplante Aktivierung&quot;wird im Site-Administrator nicht angezeigt. NPR-28725: Hotfix für CQ-4263917

**Replikation**

* Sicherheitslücke bei der Offenlegung sensibler Informationen in der Replikationsagenten-Komponente. NPR-29612, NPR-24951: Hotfix für GRANITE-25070
* Vom Benutzer bereitgestellte Daten werden bei der Ausgabe in der Komponente cq/replication/components/agent nicht ausgegeben, was zu einer gespeicherten Cross-Site-Scripting- (XSS)-Schwachstelle führt. Hotfix für CQ-4266263

**Experience Fragments**

* Experience Fragments können nicht als Ziel exportiert werden, wenn die intelligente Bildkomponente verwendet wird. Hotfix für CQ-4269606

**Social - Berichte**

* AEM Community-Berichte werden AEM Autoreninstanz nicht angezeigt. Hotfix für CQ-4266294

**Plattform**

* Site-übergreifende Skripterstellung (XSS) im Paketmanager beim Installieren eines Pakets. NPR-29734, NPR-29713, NPR-29630: Hotfix für GRANITE-26161, GRANITE-
* Mehrere gespeicherte und reflektierte Cross-Site-Scripting (XSS) in der CRXDE Lite. NPR-29634: Hotfix für GRANITE-26049
* Die Anmeldungsfunktion für Package Share verwendet die Anforderung der GET und nicht die Anforderung der POST, wodurch das Kennwort auf der Registerkarte &quot;Netzwerk&quot;angezeigt wird. NPR-29631: Hotfix für GRANITE-26048

**Felix**

* Site-übergreifende Skripterstellung (XSS) in der Systemkonsole. Die Seite wird geladen, und das Pop-up wird angezeigt, wenn der Mauszeiger über das Textfeld bewegt wird. NPR-29853, NPR-29633: Hotfix für GRANITE-26188, GRANITE-26050

**Granite**

* Apache Sling Logging Logger Configuration filtert das injizierte Skript nicht.  NPR-29775: Hotfix für GRANITE-26051

**Communities**

* Beim Autor gelöschte Gruppen sollten aus den Veröffentlichungsinstanzen entfernt werden. NPR-28933: Hotfix für CQ-4264645
* App-Secret sollte mit einem Kennwortfeld geschützt werden, nicht in einfachem Text für Social-Verbindungs-Tools angezeigt werden. NPR-29728: Hotfix für CQ-4270480
* Besucher und Mitglieder ohne Moderatorberechtigungen können nicht genehmigte/ausstehende Beiträge sehen, indem sie die URL einfügen. NPR-29726: Hotfix für CQ-4271124, CQ-4271441
* Bei der Community-Benutzeranmeldung kommt es zu langsamen Reaktionszeiten von mitunter 40–50 Sekunden. NPR-29678: Hotfix für CQ-4269444

**Übersetzung**

* Benutzer ohne Zugriff auf Übersetzungsfunktionen bei der Navigation sollten nicht auf ihre Unterseiten zugreifen können. NPR-29644: Hotfix für CQ-4269979
* Benutzerberechtigungen, die nicht als Assistent beibehalten werden, ermöglichen die Erstellung der Übersetzungskopie an einem schreibgeschützten Speicherort. NPR-29375: Hotfix für CQ-4265877

**Benutzeroberfläche - Foundation**

* Die Paginierungsgrenze des Suchergebnisses wurde für die Ansicht der Karte auf 100 Seiten und für die Ansicht der Liste auf 200 Seiten erhöht. NPR-29332: Hotfix für GRANITE-24644
* Aufgrund des verzögerten Ladens von Tags wird auf der Sammlungsseite nichts angezeigt. NPR-29267: Hotfix für GRANITE-24902
* Die Änderung der Paginierungsgrenze auf 100 statt auf 40 Trigger bedeutet eine zusätzliche verzögerte Ladezeit ohne Seitenumbruchanforderung. NPR-29246: Hotfix für GRANITE-25027
* AEM Kennwortfeld für Granite wird nach der Verschlüsselung nicht ausgefüllt. NPR-29245: Hotfix für GRANITE-24908

**Integration**

* Beim Versuch, die AEM Startkonfiguration zu bearbeiten und zu speichern, wird eine Ausnahmemeldung angezeigt. NPR-29086: Hotfix für CQ-4266153
* Anmeldeversuche mit den BrightEdge-Anmeldeinformationen schlagen mit einem Verbindungsfehler fehl.  NPR-29167: Hotfix für CQ-4265872
* Das Kontrollkästchen &quot;Vererbt von&quot;, das auf der Stammebene in Cloud Service Configs angezeigt wird, sollte entfernt werden. NPR-27856: Hotfix für CQ-4259676

**Sling**

* HTTP-Verbindungstimeout wird nicht aus den Konfigurationen gelesen. NPR-29264: Hotfix für SLING-7902
* Durch das Schreibback des JCR-Installationsprogramms wird in der OSGi-Konfiguration ein ungültiges Format verwendet und die Bereitstellung blockiert. NPR-29027: Hotfix für CQ-4264694

**Projekte**

* Benutzer können den Projektarbeitsablauf nicht abschließen. NPR-29621: Hotfix für CQ-4258791
* Die Liste des Projektarbeitsablaufs zeigt leere Zeilen über 40 Workflows. NPR-28739: Hotfix für CQ-4264005
* Wenn Sie im Markenportal die Option &quot;Dynamische Darstellung&quot;wählen, wird eine leere ZIP-Datei heruntergeladen. NPR-29420: Hotfix für CQ-4268826
* Das Veröffentlichen von Assets in Brand Portal funktioniert nicht aus dem Ordner „/content/dam/mac“ der AEM-Autoreninstanz. NPR-29820: Hotfix für CQ-4271118
* Die Interpunktion im Namen verursacht Probleme mit der Veröffentlichungsschaltfläche. NPR-29573: Hotfix für CQ-4269317
* Asset-Sprachkopie kann nicht über das Referenzbedienfeld erstellt werden. Hotfix für CQ-4269535

**Arbeitsablauf**

* Die Aktualisierung von 6.4.2 auf 6.4.4 bricht das Kalenderwählfeld des Dialogteilnehmers. NPR-29727: Hotfix für CQ-4270423

**WCM - Admin-Benutzeroberfläche**

* Beim Öffnen der Registerkarte &quot;Berechtigungen&quot;in der Coral2-Implementierung werden die Schaltflächen nicht angezeigt. Hotfix für CQ-4269419

**WCM - MSM**

* Durch das Löschen eines untergeordneten Knotens in einer Live Copy sollte die LiveRelationship getrennt werden. Hotfix für CQ-4270395
* Nach einem Upgrade auf AEM 6.4.3 benötigt Multi-Site-Manager außergewöhnlich lange für den Rollout. Hotfix für CQ-4271410

**Schwachstelle**

* CSRF-Schutz-Framework funktioniert nicht mit AEM Foundation-Formularen. NPR-28612: Hotfix für GRANITE-22231

**WCM – Seiteneditor**

* Reflektiertes Cross-Site-Scripting (XSS) bei Verwendung einer ungültigen Auswahl. Hotfix für CQ-4270397

**Formulare**

Zu den wichtigsten Merkmalen von AEM 6.4.5.0 Forms gehören:

**Forms-Add-on-Paket**

**Adaptive Formulare**

* (Touch UI) Die Workflow-Option &quot;Beginn&quot;zeigt das Dialogfeld zur Konfiguration nicht an. NPR-29521: Hotfix für CQ-4269050

**Forms - Backend-Integration**

* Für die On-Premise-Integration von Microsoft Dynamics wurde Unterstützung für ADFS (Active Directory Federation Services) 3.0 ergänzt. NPR-30003, NPR-29484: Hotfix für CQ-4270586
* Der Vorfülldienst schlägt fehl, da die Umlaufzeit des AEM Forms-Datenintegrationsmoduls verlängert wurde. NPR-28997: Hotfix für CQ-4265988
* SOAP Webservice-Anforderung ist innerhalb von AEM Forms fehlerhaft. NPR-29013: Hotfix für CQ-4265443
* Beim Testen des SOAP-Dienstes wird keine Fehlermeldung angezeigt, wenn ein falscher Datumswert vorliegt. Hotfix für CQ-4265445

**Forms - Interaktive Kommunikation und Forms - Correspondence Management**

* Die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;(CCR-Benutzeroberfläche) kann eine Gleitkommazahl nicht verarbeiten.  NPR-29210: Hotfix für CQ-4254201
* Die auf einer Variablen eingestellte QuickInfo ist in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;(CCR-Benutzeroberfläche) nicht sichtbar. NPR-29739: Hotfix für CQ-4250533
* Es ist nicht möglich, in Briefen aus Omniture Search zu kopieren oder einzufügen. NPR-29808: Hotfix für CQ-4270783

**HTML5-Formulare**

* Wenn wir einen Leerzeichen innerhalb des Textes hinzufügen, ist es im Textfeld nicht möglich, bis zum Ende zu füllen. NPR-28844: Hotfix für CQ-4260239

**Forms JEE-Installationsprogramm**

**Forms – Foundation JEE**

* Die Webdienstkomponente in AEM Forms Workbench kann keinen Webdienst aufrufen, der eine bidirektionale SSL-Authentifizierung erfordert. NPR-29485: Hotfix für CQ-4246794
* AEM Forms JEE Configuration Manager funktioniert nicht mit mehreren NIC-Karten. NPR-29236: Hotfix für CQ-4268598
* AEM Startfehler von GemFire: java.lang.IllegalStateException: Es kann nur eine Verbindung mit AdminDistributedSystem hergestellt werden. NPR-29524: Hotfix für CQ-4266295
* NoClassDefFoundError, da die JAR-Version nicht übereinstimmt. NPR-28834: Hotfix für NPR-28834

**Forms - Dokument Services**

* Ungültige PDF/A-Datei wird mit dem isPDFA-Vorgang als gültiges PDF/A gemeldet. NPR-29076: Hotfix für CQ-4261541
* PDF-Konvertierung in PDF/A-1b mit Formularfeld hat kein Erscheinungsbild-Diktat. NPR-29534: Hotfix für CQ-4269618
* Die PDF/A-Konvertierung aus mit dem Output-Dienst erstellten PDF-Dateien wird nicht mit Acrobat DC validiert. NPR-29647: Hotfix für CQ-4270448
* Apache POI Bundle schlägt mit einer Ausnahme fehl. NPR-27861, NPR-28048: Hotfix für CQ-4245898, CQ-4244778

**Forms – Designer**

* Es wurde eine PDF/UA-Unterstützung zu XFA-Formularen (XML Forms Architecture) hinzugefügt, die mit Designer und dem Output Service generiert wurden. NPR-23022

**Forms – Workflow**

* Übermittlungen von Workspace schlagen mit Umlaut fehl. NPR-29087: Hotfix für CQ-4263172

**Enthaltene Feature Packs**

**Assets**

* Multi-Site-Manager bietet jetzt Unterstützung für Assets. Weitere Informationen finden Sie unter [Assets mit MSM wiederverwenden für Assets](/help/assets/reuse-assets-using-msm.md). NPR-26450: Hotfix für CQ-4259922

**OSGI-Bundles und Inhaltspakete sind enthalten**

Der folgende Text Dokumente die Liste von OSGI-Bundles und Inhaltspaketen, die in der CFP enthalten sind.

Liste der in AEM 6.4.5.0 enthaltenen OSGi-Bundles

[Datei laden](assets/6.4.5.0_bundles.txt)

Liste der in AEM 6.4.5.0 enthaltenen Inhaltspakete

[Datei laden](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

AEM 6.4.4.0 ist ein wichtiges Update, das Funktionen für Leistung, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen umfasst, die seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht wurden.****

Es ist auch kumulativ, was bedeutet, dass 6.4.4.0 alle AEM 6.4 Service Packs vor der Veröffentlichung beinhaltet.

Einige der wichtigsten Highlights von AEM 6.4.4.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.11 aktualisiert.
* Unterstützung für die Version des Cache-Dienstes hinzugefügt, um häufige HTTP-Anforderungen der Dienstversion zu vermeiden.
* Unterstützung für das Löschen von automatischen Tags hinzugefügt.
* Implementiert endlosen Bildlauf für den Katalogassistenten.
* Unterstützte Möglichkeit, Berechtigungen gemäß Community-Sites einzuschränken.
* Leistungsverbesserungen (Zwischenspeicherung, asynchrone Ausführung, Ausschluss-Liste) für Sling Granite Content Health Check.
* Schaltfläche zum Auswählen von Elementen zum Dialogfeld &quot;Seitenminiaturansicht&quot;hinzugefügt
* Neue Eigenschaft hinzugefügt, um die Positionierung von QuickInfo in Feldern zu ermöglichen.
* Verbesserte Unterstützung von ColorPicker im Multifield.
* Es wurde eine Prüfung hinzugefügt, um leere Werte für Zahleneingabe-Multifelder in den clientlibs des Inhaltsfragments zu ignorieren.
* Unterstützung für Microsoft Translator Text API Version 3 aktiviert.

**Assets**

* Migration der AKP- und Bestandsintegration zu AEM 6.4.4.0 NPR-27632
* Wenn Sie später einen leeren Asset-Ordner mit Unterordnern veröffentlichen, werden die Unterordner ausgeblendet. NPR-27558: Hotfix für CQ-4254701
* Die Hinzufügung der Eigenschaft &quot;Einzelne nicht namensgetrennte Zeichenfolge\[\]&quot;führt zu einer unvollständigen XMP. NPR-26805: Hotfix für CQ-4254142
* Nach dem Rastern der PDF-Eingabedatei fehlen in der Ausgabe Bilder. NPR-27929: Hotfix für CTG-4150481
* Der Assistent zum Verschieben von Assets zeigt eine falsche Anzahl der verweisenden Seiten für veröffentlichte Seiten an. NPR-27833: Hotfix für CQ-4258014
* AssetPicker sucht nur das erste Tag, um das Ergebnis beim Filtern mit Tags zu filtern. NPR-27778: Hotfix für CQ-4257705
* AEM OOTB PDF Handler bleibt bei der Verarbeitung von PDF mit Fremdzeichen hängen. NPR-28778: Hotfix für CQ-4254234
* Wenn eine CSV-Datei einen Wert hat, der durch Komma in einer einzelnen Spalte getrennt ist, AEM CSV-Editor nicht das Komma umgeht und es als separate Spalte behandelt. NPR-28801: Hotfix für CQ-4261694
* Problem mit dem Metadaten-Schema-Editor beim Auswählen von Daten mithilfe des Pfadbrowsers. NPR-28674: Hotfix für CQ-4263005
* Zu viele Assets werden in den Smart Content Service verarbeitet, was zu einer enormen Zeitspanne für den Abschluss des regelmäßigen Tagging-Prozesses führt. NPR-28640: Hotfix für CQ-4262661, CQ-4262644, CQ-4263234
* Desktop-Aktionen funktionieren nicht für Omniture-Suchergebnisse von `aem/start.html`-Seite. NPR-27242: Hotfix für CQ-4248176
* Die Assets-API lässt das Hochladen von Dateien mit einem Dateiformat von mehr als 2 GB nicht zu und führt zu einem Fehler beim Hochladen. NPR-27629: Hotfix für Granite-23590
* Beim ersten Versuch werden Metadaten nicht im heruntergeladenen Asset gespeichert, falls Dynamic Media auf der Instanz aktiviert ist. NPR-28233: Hotfix für CQ-4260759
* Der Dienst-Auflöser wird in der SiteCatalyst-Konfiguration nicht geschlossen. NPR-28015: Hotfix für CQ-4259397
* Das Verschieben von Assets in DAM führt unter Scene7 nicht zu einem ähnlichen Schritt (p2p-Konfiguration). NPR-28313: Hotfix für CQ-4261091

**Sites**

* (Klassische Benutzeroberfläche) Ein Bruchteil der Live-Kopien wird in der Rollout-Liste angezeigt. NPR-28598, NPR-28574: Hotfix für CQ-4263410
* LiveRelationshipManagerImpl gibt Ausnahmen aus, wenn cq:Übergeordnet leer oder ungültig ist. NPR-28590: Hotfix für CQ-4263115
* Der vordefinierte Arbeitsablauf &quot;Anforderung zum Löschen&quot;löscht die Seiten nicht ordnungsgemäß. NPR-28668: Hotfix für CQ-4263195
* Die Benutzeroberfläche für den Beziehungsstatus zeigt keine korrekten Jahres- oder Zeitstempelwerte für verwandte Korallendatepickerfelder an. NPR-28666: Hotfix für CQ-4263661
* Website-übergreifende Skripterstellung (XSS) in SuggestionHandler für 6.4. NPR-28693: Hotfix für CQ-4253821
* Der Befehl zum Verschieben des Ordners von siteadmin endet nicht mehr im Arbeitsspeicher und macht AEM nicht verfügbar. NPR-28346: Hotfix für CQ-4261398
* MSM LiveCopy-Rollout-Konfigurationen gehen nach der Aktualisierung verloren. NPR-28311: Hotfix für CQ-4258705
* Bildlauf nach 40 Musterkonfigurationen nicht möglich. NPR-27640: Hotfix für CQ-4239166
* Die Verwendung von SyntheticResource als Referenz löst eine Null-Zeiger-Ausnahme aus und blockiert das Verschieben der Seiten.  NPR-27576: Hotfix für CQ-4258262
* Das PushOnModify-Verfahren funktioniert bei einer aktualisierten Instanz von 6.1 auf 6.4 nicht. NPR-28108: Hotfix für CQ-4259833
* (Klassische Benutzeroberfläche) Die Schaltfläche &quot;Vererbung abbrechen&quot;fehlt und die Komponente kann auf einer Live Copy-Seite bearbeitet werden. NPR-28256: Hotfix für CQ-4260161
* OakState0001: Ungelöste Konflikte bei Rollout. NPR-27982: Hotfix für CQ-4259548
* Beim Kopieren/Einfügen einer Struktur, die SyntheticResource-Verweise enthält, endet der Prozess mit dem Fehler 500. NPR-27709: Hotfix für CQ-4259179
* Ausführung von Workflows kann nicht beendet werden, wenn Nutzlasten aktiviert werden. NPR-27672: Hotfix für CQ-4258520
* Rollout zeigt Duplikat-Rollout-Pfade nach der Aktualisierung von 6.1 auf 6.4 an. NPR-27845: Hotfix für CQ-4259487
* Integrieren Sie das Damm-Asset-Modell in die Komponente &quot;Seitenminiaturansicht&quot;. NPR-28131: Hotfix für CQ-108042
* (Klassische Benutzeroberfläche) Dialoge mit Tags-Widget können nicht geöffnet werden. NPR-28575: Hotfix für CQ-4262680
* Beim Hochladen von Dateien in mehreren Feldern wird kein Ablagebereich angezeigt. NPR-28676: Hotfix für CQ-4263516
* Fehler &quot;Ungültiger Rekursionsauswahlwert&quot;bei der Migration einer Komponente von AEM 6.0 auf AEM 6.2. NPR-28609: Hotfix für CQ-4241258
* Rich Text Editor im Dialog flackert, wenn das Popupfenster eines Plugins höher ist als der Textbereich, wodurch jedes weitere Authoring blockiert wird. NPR-27579: Hotfix für CQ-4257440
* (Classic UI) cq:action editannotate funktioniert nicht. NPR-28232: Hotfix für CQ-4257703
* Wenn Sie Tags aus dem Suchbereich für Assets des Tags-Filters des Seiteneditors entfernen, wird die Liste nicht ordnungsgemäß aktualisiert. NPR-27983: Hotfix für CQ-4245567
* Wenn die Werte für die Anzahl der Felder leer sind, führt das Klicken auf Speichern zu einer unendlichen Ladeaufforderung, ohne dass die Daten tatsächlich ausgefüllt werden.  NPR-28400, NPR-28393: Hotfix für CQ-4244058, CQ-4244349
* Mit der Berechtigung &quot;Nur lesen&quot;können Benutzer/Gruppen keine XF auswählen und haben keine Option zur Ansicht der XF- und der zugehörigen Seiteneigenschaften. NPR-28341: Hotfix für CQ-4260412
* Die JSON-Daten, die von der Zielgruppe empfangen werden, weisen eine Reihe von Escape-Zeichen auf, wodurch die Anwendungsseite umgebrochen wird. NPR-28318: Hotfix für CQ-4252043
* Komponenten können nach der Installation von AEM 6.4.3 nicht bearbeitet werden. NPR-28125: Hotfix für CQ-4261216
* Das Löschen aller Tags für ein Tag-Feld wird für ein strukturiertes Inhaltsfragment nicht beibehalten. NPR-28133: Hotfix für CQ-4247241
* Beim Bearbeiten einer Inhaltsfragment-Eigenschaft &quot;jcr:lastmodifiedby&quot;und &quot;jcr:lastchanged&quot;werden die Werte aktualisiert, ohne dass der Benutzer Änderungen vornimmt. NPR-27847: Hotfix für CQ-4257138
* Die Versionierung für Inhaltsfragmente bietet einen Vergleich der Verbesserungen für AEM 6.4. NPR-27764
* Wenn für /content/experience-fragments keine cq:allowedTemplates definiert sind und allowedPaths für die Experience Fragment-Vorlage verwendet werden, wird ein Fehler ausgegeben, wenn das Experience Fragment verschoben/kopiert wird. NPR-27487: Hotfix für CQ-4257489
* Schaltfläche &quot;Erstellen&quot;wird beim Aktualisieren für den neuen Benutzer angezeigt. NPR-27335: Hotfix für CQ-4255360
* Beim Versuch, eine veröffentlichte Seite zu verschieben, ist die Zählung &quot;Verweisende Seiten&quot;auf der ersten Seite des Assistenten &quot;Seite verschieben&quot;falsch. NPR-28111: Hotfix für CQ-4259663
* (Touch-Benutzeroberfläche) Die Leiste &quot;Referenzen&quot;zeigt keine eingehenden Links an. NPR-28529: Hotfix für CQ-4262306
* Komponenten und Seiteneigenschaften können nach der Installation von AEM 6.4.3 nicht bearbeitet werden. NPR-27998: Hotfix für CQ-4261216, CQ-4260441
* Migrieren Sie contexthub zu jquery 3. NPR-28397: Hotfix für GRANITE-19902

**Commerce**

* Katalog kann nicht ausgewählt werden, wenn sich ein Ordner mit mehr als 20 Katalogen befindet. NPR-27649: Hotfix für CQ-4258119
* Ansichten für Commerce-Assistenten und -Eigenschaften sind fehlerhaft, da header.referer fehlt. Hotfix für CQ-4261122

**Campaign - Targeting**

* com.day.cq.personalization.impl.TeaserResourceEventHandler wird in eine unendliche Schleife verschoben und führt bei Veröffentlichungsinstanzen zu Aktualisierungen der Knoten. Hotfix für CQ-4263096

**Replikation**

* Fehler beim Erstellen des Replikationsinhalts com.day.cq.replication.AccessDeniedException. NPR-28314: Hotfix für CQ-4261401
* Sitzungsleck, wenn die Benutzeragent-ID im Replizierungsagenten auf admin gesetzt ist. NPR-28220: Hotfix für CQ-4255517

**DAM - Creative Cloud**

* Unterstützen Sie die HTTP-API, um ähnliche Bilder aus AEM Assets zu finden. Hotfix für CQ-4254091
* Verbessern Sie die AKP-API, damit die Ergebnisse einer Abfrage auf die Mitglieder einer Sammlung beschränkt werden können. Hotfix für CQ-4258708

**DAM - Formate**

* Nach dem Auslösen des Metadaten-Exports wird die Seite auf eine 404-Seite umgeleitet. Hotfix für CQ-4262447

**DAM - Allgemeines**

* (Adobe Stock Integration) Das Serverfehlermodell wird mit einem Oauth-Fehler in der Datei &quot;error.log&quot;angezeigt. Hotfix für CQ-4260406
* Die Adobe Stock-Integration funktioniert nicht, wenn 6.4.4 auf 6.4.3 angewendet wird. Hotfix für CQ-4266009
* Der Link zum CF-Modell fehlt auch nach Anwendung des SP3-Patches. Hotfix für CQ-4259029

**Plattform**

* (Klassische Benutzeroberfläche) Die Bearbeitungsschaltfläche ist in der Komponente Basisbericht nach einem Upgrade auf 6.4.2 nicht verfügbar. NPR-28560: Hotfix für CQ-4262825
* Wenn Sie eine Abfrage verwenden, die property.operation=like und property.depth kombiniert, wird eine InvalidQueryException ausgelöst. NPR-28570: Hotfix für CQ-4262652
* Interner Serverfehler, wenn der neu hinzugefügte Sprachknoten aus dem überlagerten Sprachknoten entfernt wird. NPR-28661: Hotfix für CQ-4239194
* Null-Zeigerausnahme in stderr.log in sling-oak-1 thread auf zufälligen Beginn. NPR-28665: Hotfix für CQ-4237845

**Felix**

* webconsole.plugins.memoryusage führt bei der Aktualisierung zu einer Deaktivierung. NPR-27895: Hotfix für GRANITE-20715

**Granit**

* Sling Content Access Health Check führt eine lange übermäßige /libs Validierung für benutzerdefinierte Ressourcen-Auflösungspfad durch. NPR-28113: Hotfix für GRANITE-23529

**Verwaltung von Inhaltsfragmenten**

* Verbesserungen der Benutzerfreundlichkeit und Funktionsgleichheit mit Assets für Inhaltsfragmente. Hotfix für CQ-4253883

**Communities**

* Aktualisieren Sie die anfälligen Bootstrap-Bibliotheken auf 3.4 und die ckeditor-Bibliotheken auf 4.5.11. NPR-28490: Hotfix für CQ-4257511
* Durch den Abbruch der Bearbeitungsmodi wird die gelöschte Anlage nicht wiederhergestellt. NPR-27902: Hotfix für CQ-4255150
* Die Komposition im Namen der Box sollte nur für die privilegierten Mitglieder sichtbar sein. NPR-27900: Hotfix für CQ-4251235
* hinzufügen rep:cache in Ignorierbare Knoten bei AEM Communities User Sync Listener bei Veröffentlichungsinstanzen. NPR-27842: Hotfix für CQ-4247234
* Das Suchfeld zeigt Escape-Zeichen auf UI-Ebene an. NPR-27838: Hotfix für CQ-4259757
* Fehler beim Suchen nach Sonderzeichen wie (, +,? in Schnellsuche. NPR-28213: Hotfix für CQ-4260969
* Erstellen Sie eine &quot;Community-spezifische Administratorgruppe&quot;, damit die Benutzer die entsprechende Community-Site bearbeiten und erstellen können. NPR-27731
* Es wurde eine Logik zum Öffnen des Ereignisse über die Tastatur hinzugefügt. NPR-27726: Hotfix für CQ-4254026
* Aktivierung der Tastaturnavigation für AEM Communities-Komponenten bei der Veröffentlichung. NPR-27728: Hotfix für CQ-4254028
* Es wurde ein aria-label für die Ansicht von Listen und Karten hinzugefügt. NPR-27727: Hotfix für CQ-4254027
* Handhabung von Open Resource Resolver-Sitzungen in Social Communities NPR-27721: Hotfix für CQ-4258714

**Übersetzung**

* Unterstützung für Microsoft Translator Text API, Version 3. NPR-28366: Hotfix für CQ-4249755
* jcr:language &amp; cq:language werden nicht automatisch in der übersetzten Sprache aktualisiert. NPR-28338: Hotfix für CQ-4256046
* Cyclische Verweise verursachen StackOverflowError beim Erstellen einer Sprachkopie. NPR-27596: Hotfix für CQ-4255621
* In einem mehrsprachigen Übersetzungsprojekt werden durch Klicken auf Speichern und Schließen der Ergebnisse auf den nachfolgenden Seiten, die zum Projekt hinzugefügt werden, neue Projekte erstellt, anstatt neue Übersetzungsaufträge in einem vorhandenen Projekt zu erstellen. NPR-28219, NPR-28236: Hotfix für CQ-4261276, CQ-4260731
* Fehlerzeichenfolge zu lang, wenn Inhaltsfragment mit Bulkdaten hinzugefügt wird, aufgrund der Beschränkung der zulässigen Zeichenanzahl. NPR-28722: Hotfix für CQ-4262362

**Social**

* Kommentare, die auf der nächsten Seite veröffentlicht werden, werden bei jedem neuen Kommentar gelb hervorgehoben. Hotfix für CQ-4261359
* Kommentare können nicht mit der API im benutzerdefinierten Inhalt gelöscht werden. NPR-28075: Hotfix für CQ-4261135
* AbstractNotificationOperationService verursacht ClassCastException. Hotfix für CQ-4260456
* Entfernen des Verweises auf die SCORM-Cloud (Shareable Content Object Reference Model) im Player. Hotfix für CQ-4260779

**Benutzeroberfläche - Foundation**

* Die im HTML Client Library Manager integrierte Funktion &quot;Dateisystem Output Cache&quot;bricht die Funktion &quot;debugClientLibs&quot;für kompilierte Skripte wie LESS-Dateien. NPR-27249: Hotfix für Granite-23313
* Die Anzahl der Assets, die angezeigt werden, wenn der Debug-Modus aktiviert ist, ist immer 1 und es werden viele JS-Fehler in der Konsole des Browsers ausgegeben.  NPR-27575: Hotfix für GRANITE-23750
* Das Speichern und Schließen auf den Seiteneigenschaften kehrt nicht zur richtigen Seite in AEM WAR mit Tomcat zurück. NPR-27566: Hotfix für GRANITE-23671

**Integration**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` wird in eine unendliche Schleife verschoben und führt bei Veröffentlichungsinstanzen zu Aktualisierungen der Knoten. NPR-28561: Hotfix für CQ-4263096
* cq:actions werden für eine zielgerichtete Komponente nicht berücksichtigt. NPR-27616: Hotfix für CQ-4257497
* Die Absage der LiveCopy-Vererbung funktioniert auf zielgerichteten Containern nicht ordnungsgemäß. NPR-28129: Hotfix für CQ-4259813
* (Cloud Service Configs) Das Kontrollkästchen &quot;geerbt von&quot;auf der Stammebene sollte entfernt werden. NPR-27856: Hotfix für CQ-4259676

**Sling**

* Update auf Sling Models API 1.3.8, Impl 1.4.10. NPR-27636: Hotfix für GRANITE-23537

**OAK - Segmentbeständigkeit**

* SegmentBufferWriter wird nach OnRC nicht gerötet. NPR-27464

**Projekte**

* Das mehrsprachige Übersetzungsprojekt schafft nicht mehrere Sprachaufträge für Benutzer, die nicht zur Gruppe der Administratoren gehören. NPR-28508: Hotfix für CQ-4262023
* Das ProjectTaskListServlet löscht einen ResourceResolver, wenn getTaskRenderer während des Dienststarts aufgerufen wird. NPR-27590: Hotfix für CQ-4258011
* Wenn ein Ordner mehr Unterordner als das Seitenformat hat und die Reihenfolge nach Datum oder Größe bestimmt ist, verhindert ein Fehler, dass die erste Seite verschoben wird. NPR-28867: Hotfix für CQ-4265039
* Backport Cross-Site Scripting (XSS)-Fehlerbehebungen in DAM Viewern. NPR-28106: Hotfix für CQ-4253215
* Projektadministratoren können keine Seiten zum Übersetzungsprojekt hinzufügen, da der Link zum Hinzufügen neuer Seiten zum Übersetzungsprojekt nicht sichtbar ist. Hotfix für CQ-4266334

**Arbeitsablauf**

* Wenn wir das Dialogfeld &quot;Vollständige Arbeitselemente&quot;in der Workflow-Benachrichtigung öffnen, die ein Tag-Feld enthält, wird durch Klicken auf das Kreuz eine Tag-Eigenschaft hinzugefügt. NPR-28304: Hotfix für CQ-4261321
* Die Schaltfläche zum Umschalten der Benutzerauswahl im Dialogfeld &quot;Aufgabe neu zuweisen&quot;funktioniert nicht. NPR-28963: Hotfix für CQ-4264206

**Formulare**

Zu den wichtigsten Merkmalen von AEM 6.4.4.0 Forms gehören:

* Zusätzliche Unterstützung zum Aufzeichnen von Dokument-Sicherheits-APIs zum Signieren und Zertifizieren als Transaktionen.

**Forms-Add-on-Paket**

**Adobe Sign-Integration**

* AEM 6.4 Forms Client SDK enthält kein adobesign-recipent-Paket. NPR-27735: Hotfix für CQ-4259372

**Adaptive Formulare**

* Wenn ein adaptives Formular mit einer leeren Vorlage erstellt wird, können Kunden keine untergeordneten Bereiche in den Stammbereich des Formulars einfügen. NPR-28758: Hotfix für CQ-4264157
* Wenn der Wert der Komponente &quot;Jahr&quot;9999 beträgt, schlägt das Überprüfungsskript fehl. NPR-28580: Hotfix für CQ-4262620
* Wenn ein adaptives Formular mit einer leeren Vorlage erstellt wird, können Kunden keine untergeordneten Bedienfelder in den Stammbereich des Formulars einfügen. NPR-28758: Hotfix für CQ-4264157
* Es kann kein Wert zwischen den Feldern der verzögert geladenen Fragmente eines adaptiven Formulars festgelegt werden. NPR-27758: Hotfix für CQ-4259703
* Adaptives Formular verwendet keinen Rich-Text-Editor, lädt aber seine Bibliotheken.  NPR-27759: Hotfix für CQ-4259193
* Die Umleitung auf URL funktioniert nicht bei adaptiven Formularen, die in eine AEM Sites-Seite eingebettet sind. NPR-27620: Hotfix für CQ-4239287
* Es kann kein Wert zwischen den Feldern der verzögert geladenen Fragmente eines adaptiven Formulars festgelegt werden. NPR-28320: Hotfix für CQ-4262345
* Adaptives Formular verwendet keinen Rich-Text-Editor, lädt aber seine Bibliotheken.  NPR-28001: Hotfix für CQ-4259703, CQ-4259193
* Scribble-Signatur funktioniert nicht für AEM Forms-Apps, die unter Apple iOS 12.1 ausgeführt werden. NPR-28497: Hotfix für CQ-4261765
* Übermittlungsaktion unter Verwendung von &quot;Forms Workflow&quot;-Classic-Authoring-Problemen in 6.4. Hotfix für CQ-4252740
* Entfernen von Blockierungen und tmp-Datenspeicherung. NPR-28806: Hotfix für CQ-4264441

**Forms – Correspondence Management**

* Die Benutzeroberfläche des Agenten behält die Originalgröße des Bildes nicht bei. NPR-28800: Hotfix für CQ-4259767
* CCR/Agent-Benutzeroberfläche: Die Beschriftungen der Datumsfelder wurden auf der Registerkarte &quot;Daten&quot;verschoben. Hotfix für CQ-4255499

**Forms - Transaktions-Berichte**

* Es wurde Unterstützung hinzugefügt, um die Verwendung digitaler Signaturen oder die Zertifizierung eines Dokuments als abrechnungsfähige Transaktionen zu zählen. NPR-28495: Hotfix für CQ-4260236
* Digitale Signatur und Zertifizierung zur abrechnungsfähigen API hinzugefügt. Hotfix für CQ-4260236

**Forms Management**

Zusätzliche Unterstützung zum Ersetzen der Verwendung der Clientbibliothek mit Handlebars durch Unterstriche im Forms Manager-Assistenten zum Überprüfen des Beginns und zum Verschieben des Asset-Assistenten. NPR-27643: Hotfix für CQ-4246536.
Nach der Installation des Forms Management-Pakets in Release/640-Zweig bleibt ein Paket im installierten Zustand. Hotfix für CQ-4265410
Forms, das mit Anlagen in ihnen gesendet wurde, wird nicht im Workflow angezeigt, wenn die Übermittlungsaktion &quot;AEM Forms-Workflow aufrufen&quot;und &quot;Portal-Übermittlung aktivieren&quot;markiert ist. Hotfix für CQ-4263110

**Forms - Backend-Integration**

* Test von Pre-/Post-Präprozessoren und benutzerdefinierten Übermittlungen mit Client SDK, Hotfix für CQ-4238469 nicht möglich

**Forms JEE-Installationsprogramm**

**Forms - Sicherheit von Dokumenten**

* Bei Verwendung des Updaterichtliniendiensts tritt der Objektfehler nicht zwingend auf. NPR-28751: Hotfix für CQ-4252287
* Signature Build schlägt mit älterer Version von commons-pkg fehl. Hotfix für CQ-4265535

**Forms – Foundation JEE**

* Wenn AEM Forms auf IBM WebSphere installiert ist, schlägt das Erstellen eines auf SOAP basierenden Formulardatenmodells fehl. NPR-27923: Hotfix für CQ-4251134
* Das SRT-Tool von PDF Generator kann die installierte Version von Adobe Acrobat nicht erkennen. NPR-27971

**Forms – Designer**

* Einige JPEG-Bilder in einer XDP-Vorlage werden nicht korrekt dargestellt.  NPR-26702: Hotfix für LC-3917457

**Forms – Workflow**

* HTML5 Forms mit dem standardmäßigen Sendeprozess in an.lca funktioniert nicht mit JBoss 7. NPR-28675: Hotfix für CQ-4243928
* PDF forms können nicht in HTML Workspace gesendet werden. NPR-28058: Hotfix für CQ-4260373
* Kundendaten werden mit Invoke FDM Service Forms Workflow in Infoprotokollen gedruckt. Hotfix für CQ-4260385

**Enthaltene Feature Packs**

**Sites**

* Die Versionierung für Inhaltsfragmente vergleichen die Verbesserungen für AEM 6.4.  NPR-26760: FP für CQ-4248839
* Unterschiede bei Inhaltsfragmenten für AEM 6.4.  NPR-27866: FP für CQ-4248839
* Aktivierte Funktion in OSGI-Konfiguration **AEM Funktionsmarkierung zum Zurückziehen des Workflows**. Die Aktion zum Entfernen sollte die Workflow-Instanz beenden, nachdem das Flag festgelegt wurde. NPR-26451: Hotfix für CQ-4259090

**Plattform**

* Die erweiterte Facet-Extraktion von Abfrage Builder nutzt Oak API für 6.4. NPR-26674: FP für CQ-4230337

**OSGI-Bundles und Inhaltspakete sind enthalten**

Der folgende Text Dokumente die Liste von OSGI-Bundles und Inhaltspaketen, die in der CFP enthalten sind.

Liste der in AEM 6.4.4.0 enthaltenen OSGi-Bundles

[Datei laden](assets/bundles_6_4_4_0.txt)

Liste der in AEM 6.4.4.0 enthaltenen Inhaltspakete

[Datei laden](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

AEM 6.4.3.0 ist ein wichtiges Update, das Funktionen für Leistung, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen umfasst, die seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht wurden.

Es ist auch kumulativ, was bedeutet, dass 6.4.3.0 alle AEM 6.4 Service Packs vor der Veröffentlichung beinhaltet.

Einige der wichtigsten Highlights von AEM 6.4.3.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.9 aktualisiert.
* Unterstützung für die Eigenschaft allowedPaths in Vorlagen für adaptive Formulare hinzugefügt.
* Erweiterte panel-basierte Suche nach Assets in AEM
* Site-übergreifende Skripterstellungskorrekturen (XSS) auf der Anmeldeseite.
* Verbesserte UI-Instrumentierung.
* Verbesserte FormData-Verarbeitung.
* Verbesserte Handhabung der Elementbenennung in einem Multifield.
* Verbesserte Handhabung von Platzhalterelementen (Ansicht der Karten und der Liste) während der Auswahl.
* Adobe IMS-Authentifizierung und Admin Console-Unterstützung für Managed Services hinzugefügt.

**Assets**

* Der DAM-Arbeitsablauf zum Aktualisieren von Assets extrahiert keine Verweise aus INDD-Dateien, wenn die Option IDS-Entschlüsselung aktiviert ist. NPR-26243; Hotfix für CQ-4250933
* Die Erfolgsmeldung wird nicht angezeigt, wenn Assets mit dem Assets Bulk Editor veröffentlicht werden. NPR-26252; Hotfix für CQ-4251688.
* Wenn Sie sich ein Asset aus einem Suchergebnis angesehen haben und auf die Schaltfläche &quot;Zurück&quot;im Browser klicken, wird die Fehlermeldung &quot;Fehlerhafte Anforderung&quot;mit 400 Fehlercode angezeigt. NPR 26578; Hotfix für CQ-4253741
* In den Asset-Metadaten wird nach der Installation eines Service Packs ein Fehler wegen eines ungültigen Namensraums angezeigt. NPR-22341; Quickfix für CQ-4237202
* Die Option zum Neuanordnen von Ordnern und Inhaltsfragmenten in der Ansicht &quot;Liste&quot;wird für die entsprechenden Ordner nicht angezeigt. NPR-27153; Hotfix für CQ-4255873
* Benutzer können einer neuen Sammlung keine Assets hinzufügen, da eine Fehlermeldung mit einem fehlerhaften Bild im Popup-Dialogfeld &quot;Fehler&quot;angezeigt wird. NPR-22431; Hotfix für CQ-4237086
* Die Dropdown-Liste „Kaskadieren“ wird in dynamischen Dropdown-Listen nicht unterstützt. NPR-27043; Hotfix für CQ-4252564
* Wenn Benutzer in der DMS7-Cloud-Konfiguration einen nicht standardmäßigen Wert für den Stammordner für Firmen festlegen, funktioniert die Viewer-Vorgabe nicht wie erwartet. NPR-26360; Hotfix für CQ-4249505
* Asset Berichte schlägt bei Instanzen mit einer sehr großen Anzahl von Assets fehl. NPR-27278; Hotfix für CQ-4256748
* Unterordner übernehmen nicht das SmartCrop-Image-Profil des übergeordneten Ordners. NPR-27197; Hotfix für CQ-4256273
* Wenn die Dynamic Media-Integration aktiviert ist, werden einige Metadateneigenschaften von Assets geändert. Die Attribute für Breite, Höhe und Position werden nicht angezeigt. NPR-27203; Hotfix für CQ-4256258
* Dynamic Media verwendet den konfigurierten Proxy nicht für einige Assets. NPR-25211; Hotfix für CQ-4244871
* Metadaten-Editor-Seite enthält Null-Zeigerausnahme für ungültigen Elementparameter. NPR-26169; Hotfix für CQ-4241368.
* Wenn für eine Dropdown-Liste eine Auswahlregel und eine erforderliche Regel angewendet wurden, kann die erforderliche Regel im Metadateneditor nicht erfüllt werden. NPR-27479; Hotfix von CQ-4251428

**Sites**

* Ein Benutzer kann die Rich-Text-Editor-Funktionen im eingebetteten Vollbildmodus mithilfe von Inhaltsrichtlinien steuern, kann jedoch die Rich-Text-Editor-Funktionen im Dialogfeld bearbeiten nicht mit Inhaltsrichtlinien steuern. NPR-26750: Hotfix für CQ-4241130
* Rich-Text-Editor wird nicht mehr verwendbar, wenn von Vollbild zu schwebendem Dialog gewechselt wird. Die schwebende Ansicht enthält zwei Rich-Text-Editoren. NPR-25589: Hotfix für CQ-4206008
* Wenn die Eingabetaste (Eingabetaste) in einem Textfeld gedrückt wird, wechselt der Rich-Text-Editor in den Vollbildmodus. NPR-26204: Hotfix für CQ-4245893
* Liste-Plugin des Rich-Text-Editors ist automatisch deaktiviert und lässt keine Änderungen zu. NPR-26507: Hotfix für CQ-4239387
* Wenn dem Fenster des Rich-Text-Editors ein Sonderzeichen hinzugefügt wird, wird der Bildlauf des Fensters nach oben durchgeführt. NPR-26435: Hotfix für CQ-4249869
* Fragen zum Zwischenspeichern in segment.js in Client Context bzw. Nicht-Zwischenspeichern. NPR-26622: Hotfix für CQ-4253486
* Wenn eine untergeordnete Regel von der Autoreninstanz zur Veröffentlichungsinstanz aktiviert wird, funktioniert die Veröffentlichungsinstanz nicht mehr. NPR-26601: Hotfix für CQ-4253588
* Wenn der Rich-Text-Editor mit mehreren Feldern kombiniert wird, lautet der Fehler „Uncaught TypeError: fieldAPI.getName ist keine Funktion beim Fehler foundation.js“. NPR-27146: Hotfix für CQ-4253155
* Die Salesforce-Integration kann die Proxykonfiguration nicht verwenden. NPR-27244: Hotfix für CQ-4245300
* Wenn Sie eine Seite für die Aktivierung mit der Option &quot;Veröffentlichung verwalten&quot;für ein späteres Datum planen und zur Ansicht der Liste wechseln, fehlt das Kalendersymbol. NPR-26974: Hotfix für CQ-4239206
* Benutzer können die Berechtigungen für geschlossene Benutzergruppen in den Seiteneigenschaften nicht bearbeiten. NPR-27138: Hotfix für CQ-4256089
Tags können nicht über Tagging bearbeitet werden. NPR-26957: Hotfix für CQ-4254858
* Beim Verschieben eines Tags, auf das von einem strukturierten Inhaltsfragmentmodell verwiesen wird, werden die vorhandenen Verweise auf das Tag in einem Inhaltsfragment nicht aktualisiert. Dies geschieht im Bearbeitungsbildschirm des Inhaltsfragmentmodells. NPR-26776: Hotfix für CQ-4251805
* Wenn Sie einen Start mit mehreren Seiten erstellen und bewerben, werden für jede Seite mehrere Versionen erstellt. NPR-26917: Hotfix für CQ-4254663
* AEM siteadmin behandelt keine in die Adressleiste des Browsers eingegebenen Pfade. NPR-26780: Hotfix für CQ-4254097
* Wenn eine Seite ohne Umbenennung an einen neuen Speicherort verschoben wird, geht der Versionsverlauf der Seite verloren. NPR-26706: Hotfix für CQ-4254025
* URLs im Erlebnisfragment-Admin-Editor lassen keine Überlagerungen zu. NPR-26319: Hotfix für CQ-4252156
* Wenn eine Seite mit einer Vorlage erstellt und veröffentlicht wird, die ein leeres Erlebnisfragment enthält, schlägt das Öffnen der Seite fehl, und es tritt ein DefaultSlingScript-Fehler auf. NPR-26305: Hotfix für CQ-4252460
* Wird die datenbasierte Verwendung mit Klassen mit identischem Namen verwendet, wird nicht-kompatibler Code erzeugt. NPR-27282: Hotfix für Sling-7581
* Nach der Aktualisierung der SP-Installation verfügen die Sites über eine leere Blueprint-Rollout-Konfiguration. NPR-27609: Hotfix für CQ-4257078

**DAM - Markenportal**

* Tag-Vorhersagen werden nicht veröffentlicht, wenn das Metadaten-Schema-Formular im Markenportal veröffentlicht wird. Hotfix für CQ-4256218
* Wenn ein Ordner der dritten Ebene von AEM in das Markenportal veröffentlicht wird, ohne die übergeordneten Ordner zu veröffentlichen, ändert sich der Ordnername. Hotfix für CQ-4255423
* Die Pfadbrowservorhersage wird wie erwartet von AEM Assets bis Markenportal veröffentlicht. Der veröffentlichte Pfad bei BP bleibt jedoch /content/dam, der aktualisiert werden muss. Hotfix für CQ-4256240

**DAM - Creative Cloud**

* Das Symbol &quot;Assets durchsuchen&quot;fehlt in der AEM Hauptnavigation. Hotfix für CQ-4254343

**DAM - DM Client**

* Nachdem Sie Videos in einen mit dem AVS Video Processing Profil verknüpften Ordner aufgenommen haben, wird das Browserfenster immer wieder aktualisiert. Hotfix für CQ-4253563
* Die YouTube-Veröffentlichung schlägt fehl, wenn ein Ad-hoc-Tag mit Großbuchstaben verwendet wird. Hotfix für CQ-4252477
* Wenn eine Anmerkung in einem Asset wie PDF erstellt wird, Beginn die Benutzeroberfläche eine Endlosschleife zur Aktualisierung der Seite. NPR-27052: Hotfix für CQ-4255396

**DAM - DM-Dienste**

* Dynamic Media verwendet den konfigurierten Proxy nicht für einige Assets. NPR-10727; Hotfix für CQ-4244871

**Plattform**

* Leistungsprobleme mit org.apache.sling.i18n. NPR-26812: Hotfix für SLING-7543
* Die Knoteneigenschaften können nicht angezeigt werden, wenn die Eingabe-XML formatiert und bereitgestellt ist. NPR-26198: Hotfix für CQ-4250448
* IndexOutOfBoundsException in ResourceProviderTracker. NPR-26968: Hotfix für GRANITE-23310
* Die JMX-Konsole sammelt zahlreiche Admin-Sitzungen und eine neue Sitzung wird alle 5 Minuten geöffnet. NPR-26958: Hotfix für CQ-4251090
* Nach dem Upgrade von 6.2 auf 6.4 zeigt die Protokolldatei die Stapelablaufverfolgung für den nicht geschlossenen Ressourcenauflöser com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck an. NPR-26176: Hotfix für Granite-21734
* Wenn ein standardmäßiger Dispatcher-Flush-Agent für die Aktualisierung von Aliasnamen konfiguriert ist, schlägt der Vorgang mit einem StackOverflowError fehl. NPR-26373: Hotfix für CQ-4242928
* Die Replikation verwendet abgelaufenes OAuth-Token, bis es fehlschlägt. NPR-25894
* Eingeschränkte Seite (Seite &quot;Geschlossene Benutzergruppe&quot;) mit Sling: alias leitet den Benutzer nicht zur Anmeldeseite um. NPR-25715: Hotfix für Granite=22263
* Beim Veröffentlichen von Tags wird keine Aktivität auf der Benutzeroberfläche angezeigt. Hotfix für CQ-4255961
* Tags in der klassischen Benutzeroberfläche können nicht bearbeitet werden. Hotfix für CQ-4258697
* Aktualisierung von org.apache.felix.http.bridge auf Version 4.0.4. NPR-27038: Rückanschluss für Granit - 23334
* Die Aktivitätsprotokolle von Package Manager sollten in einer separaten Protokolldatei extrahiert werden. NPR-27323: Hotfix für Granite-14866
* Paketvalidator meldet keine Überlagerungen in CFP. NPR-27119: Hotfix für GRANITE-22825

**Projekte**

* Die AKP-API behandelt Paging mit untergeordneten Unterordnern nicht ordnungsgemäß. NPR-27617: Hotfix für CQ-4258639

**OAK**

* Anmeldung beim Repository nach der Installation von AEM 6.4 Service Pack 2 nicht möglich. NPR-27171: Hotfix für Granite-23317

**Replikation**

* Das Audit-Protokoll bleibt mit aktiven Sitzungen offen, die mit ca. 750 pro Tag stetig zunehmen. NPR-27062: Hotfix für CQ-4241350

**Communities**

* Forumsbeiträge und -antworten werden über der zweiten Seite hinzugefügt. Bei Aktualisierung wird der Beitrag an die richtige Position auf der ersten Seite verschoben. NPR-27342: Hotfix für CQ-4247338
* Links zu allen Ressourcen legen den Kontextpfad (/aempublish) nach dem Bildlauf ab. NPR-26982: Hotfix für CQ-4254345
* Hinzugefügte Gruppen sind in der Dropdown-Liste &quot;Community-Manager&quot;, &quot;Community-Moderatoren&quot;und &quot;Berechtigte Mitglieder&quot;beim Bearbeiten einer veröffentlichten Site nicht sichtbar. NPR-27190: Hotfix für CQ-4258574
* Nur 10 Gruppen werden auf der Seite &quot;Ressourcen für die Aktivierung&quot;aufgelistet, selbst wenn die Paginierung für die Gruppenaufstellung aktiviert ist. NPR-26934: Hotfix für CQ-4252985
* Die Option zum Aktivieren/Deaktivieren der Suche für die Komponente Geplanter Beitrag im Protokoll ist in ConfigMgr verfügbar und der SearchScheduledPosts-Auftrag wurde optimiert. NPR-26923: Hotfix für CQ-4250463
* Die Suche nach Suchbegriffen in der Adresse funktioniert nicht auf der Kalenderkomponentenseite, wenn AEM Community so eingestellt ist, dass sie mit DSRP funktioniert. NPR-26737: Hotfix für CQ-4258493
* Direkter Link zum Kommentar anstelle des Hauptbeitrags in den Details eines Kommentars für Moderations-UI- und Aktivierungsressourcen implementiert. NPR-26704: Hotfix für CQ-4251381
* Inhalte, die über eine Mehrfachauswahl in der Moderationskonsole moderiert wurden, werden im Aktivität-Stream nicht angezeigt. NPR-26695: Hotfix für CQ-4253244
* Die Suche mit Vorname und Nachname im Feld Communities Messaging gibt nicht das erwartete Ergebnis zurück. NPR-26385: Hotfix für CQ-4248673
* Fehler beim Hochladen eines anderen Anhangs als Bild (z. B. .pdf) im Forum. NPR-27360: Hotfix für CQ-4257753
* Wenn Authoring-Veröffentlichung mit MySQL DSRP eingestellt ist, funktioniert ein Forumsbeitrag nicht, wenn die Funktion &quot;Autoren veröffentlichen&quot;deaktiviert ist. NPR-26125; Hotfix für CQ-4251520
* Sammlungskomponenten (Foren, Blogs, Kalender, Ideation, QnA) verfügen jetzt über eine Eigenschaft im Komponentendialogfeld, um &quot;UGC im Bearbeitungsmodus des Autors blockieren&quot;zu aktivieren/deaktivieren, um das Laden von UGC im WCM-Bearbeitungsmodus zu erlauben/zu verweigern. NPR-26978: Hotfix für CQ-4248161
* Tags Die Suche funktioniert nicht bei lokalisierten Suchbegriffen. NPR-26171: Hotfix für CQ-4249926
* Über die Schaltfläche &quot;Zurück&quot;wird eine Seite in der Forumssuche übersprungen. NPR-26950: Hotfix für CQ-4254804
* AEM Instanz, die auf dem standardmäßigen HTTP-Anschluss (80) ausgeführt wird, kann nicht die Datei imsmanifest.xml erreichen. NPR-27173: Hotfix für CQ-4252211
* Wenn AEM Communities mit DSRP eingestellt ist, funktioniert das Entfernen der Markierung als Antwort für QnA nicht. NPR-26247: Hotfix für CQ-4252232
* Adobe Datenspeicherung kann nicht aufgerufen werden: 414 error - Lange GET-URI, die beobachtet wird, wenn Benutzer /content/community-components/en/search.html suchen und das Autorenfeld als einen der Filter für diesen Suchbegriff auswählen. NPR-26643: Hotfix für CQ-4251303
* Der Dropdown-Wert für DataCenterURL in der ASRP-Konfiguration wird von Dallas in Virginia geändert (für VA6). NPR-26936: Hotfix für CQ-4254434
* Sonderzeichen in der Forumssuche geben Fehler oder keine Ergebnisse zurück. NPR-26930: Hotfix für CQ-4247744
* Die für &quot;Anzahl der Ergebnisse&quot;in der Forumssuche angezeigte Zahl verwendet ein falsches Trennzeichen für englische und deutsche Gebietsschemata. NPR-27050: Hotfix für CQ-4248939
* Ungelesene Benachrichtigungen steigen nicht über 21 hinaus. NPR-26946, NPR-27480: Hotfix für CQ-4252829, CQ-4256939
* Durch die Paginierung im Kommentarbereich einer beliebigen Komponente wird der Seiteninhalt beim Erreichen einer Seite durch Paginierung angezeigt. NPR-27032: Hotfix für CQ-4251228
* Der Community-Site-Ordner kann nicht auf dem Miniaturbild angeklickt werden, wenn er von der Admin-Konsole in der AEM Author-Instanz angezeigt wird. NPR-26986: Hotfix für CQ-4254036
* Mit der Option &quot;Alle lesen markieren&quot;werden nur die ersten 10 Benachrichtigungen als gelesen markiert und andere bleiben bis zur Aktualisierung der Seite ungelesen. NPR-27037: Hotfix für CQ-4254058
* Aus Ideationsgründen wird keine Paginierung ausgelöst, und die Liste von Themen (oder Antworten) wird länger, es sei denn, sie werden neu geladen. NPR-26193: Hotfix für CQ-4252104
* Die Aktivitäten anderer Benutzer wurden gelöscht und beim Anmelden mit Moderatorberechtigungen und beim Hinzufügen von &quot;#social-Aktivitäten&quot;oder &quot;#tabs-2&quot;am Ende der Profil-URL des Moderators sichtbar. Hotfix für CQ-4251355
* Alle zugewiesenen Tags können nicht aus einem Blog-Artikel entfernt werden. NPR-26851: Hotfix für CQ-4253359
* Beziehungen zu UGC werden beim Löschen des UGC nicht gelöscht. NPR-27630: Hotfix für CQ-4258706
* Link für Antworten funktioniert nicht bei Zeilenklick auf Forumantworten. NPR-27623: Hotfix für CQ-4256138
* Die Beschränkung für das Benutzerabonnement liegt bei 1000. NPR-27614: Hotfix für CQ-4254689
* Das Bearbeiten einer Site und das Bearbeiten von Rollen in den Rolleneinstellungen führen zu einer Null-Zeiger-Ausnahme. NPR-27377; Hotfix für CQ-4255909

**Übersetzung**

* Translation Vorschau funktioniert nicht mit dem Musterinhalt &quot;we.retail&quot;. NPR-26727: Hotfix für CQ-4241179

**Benutzeroberfläche - Foundation**

* Beim Versuch, Konfigurationen nach einem Upgrade auf AEM 6.4 herunterzuladen, wird eine NullPointerException zurückgegeben. NPR-27310: Hotfix für Granite-23573
* Proaktiver Backport für Fehlerbehebungen &quot;granite.platform.login&quot;. NPR-26941
* Proaktiver Backport für granite.ui.content-Korrekturen. NPR-26294
* Die Komponente Zahlenfeld überprüft keine negativen Zahlen in Internet Explorer 11. NPR-26701
* Proaktiver Backport für granite.ui.coralui3-Korrekturen. NPR-26662
* Proaktiver Backport für granite.ui.coralui3-eon-Korrekturen. NPR-26666
* Proaktiver Backport für Fehlerbehebungen granite.ui.foundation.components. NPR-27313
* Proaktiver Backport für granite.ui.commons-Fehlerbehebungen. NPR-26753
* Proaktive Unterstützung von Foundation UI Backports. NPR-26248

**Integration**

* Änderungen in AEM Erlebnissen, die über die Targeting-Engine erstellt wurden, werden nicht veröffentlicht. NPR-24869: Hotfix für CQ-4247832
* Es können nicht mehrere Aktivitäten und Erlebnisse erstellt werden, wenn deren Namen japanische Zeichen enthalten. NPR-27271: Hotfix für CQ-4256857
* Aktualisierung des Start-API-Endpunkts. NPR-26790: Hotfix für CQ-4254380
* (Personalisierung) BrandsRetriever führt den gesamten Baum. NPR-27060: Hotfix für CQ-4255790

**WCM - Admin-Benutzeroberfläche**

* HTTP-Test zum Veröffentlichen/Rückgängigmachen der Veröffentlichung einer Seite mit Verweisen und einem UI-Test für Live Copy hinzugefügt. Hotfix für CQ-4256894

**WCM – Seiteneditor**

* Die Bearbeitungssymbolleiste wird bei der ersten Bearbeitung für Komponenten deaktiviert. Hotfix für CQ-4253270

**Formulare**

Zu den wichtigsten Merkmalen von AEM 6.4.3.0 Forms gehören:

* Unterstützung für ein Array/eine Liste von Objekten mit der dynamischen Entitätsersetzung aktiviert.
* FIPS-Kompatibilität für Reader Extended-Arbeitsablauf in Digital Signature, Reader Extensions, CryptoProvider und TrustStore aktiviert.
* Unterstützung für PDF/UA zu XFA-Formularen hinzugefügt, die mit Designer oder dem Output-Dienst generiert wurden.
* Unterstützung für die Eigenschaft allowedPaths in Vorlagen für adaptive Formulare aktiviert.
* JBoss 7.1.4-Unterstützung für AEM Forms 6.4 hinzugefügt.

**Forms-Add-on-Paket**

**Backend-Integration**

* Zuordnungen von Formulardatenmodellen können nicht basierend auf dynamischen Entitäten in der SOAP-Antwort gefüllt werden. NPR-26428: Hotfix für CQ-4250639
* Der Wert für _elementNamespace im Formulardatenmodell, zusätzliche Daten, die mithilfe der Test-UI eingegeben wurden, werden in der SOAP-Anforderung nicht korrekt wiedergegeben. Hotfix für CQ-4255373
* Eine Beschränkung der Eigenschaft &quot;null&quot;wird mit einem Standardwert initialisiert und kann nicht mit FDM synchronisiert werden. Hotfix für CQ-4253873
* Der Standardwert für die Eigenschaft null ist für die Datenquelle OData nicht auf True festgelegt. Hotfix für CQ-4253870

**Adaptive Formulare**

* Sites und Formulareditor können nicht geladen werden. NPR-26977; Hotfix für CQ-4249170
* Probleme beim Hinzufügen einer Anlage zu einem adaptiven Formular mithilfe der Tastatur. NPR-25913; Hotfix für CQ-4249456

**Forms – Interaktive Kommunikation**

* Bedienfelder, die mit der Option Hinzufügen untergeordneten Bedienfelds in der Inhaltsstruktur im Web-Kanal der interaktiven Kommunikation und in adaptiven Formularen hinzugefügt wurden, können nicht verschoben werden. Hotfix für CQ-4253915
* Die Tabellennamen werden anstelle des Titels der FDM-Zuordnung im Bereich &quot;Datenquellen&quot;des Kanals &quot;Drucken&quot;angezeigt. Hotfix für CQ-4253669
* Die Funktion isUseXFABullets() ist in der PrintChannelRenderOptions-Klasse nicht deaktiviert und ist im Client-SDK verfügbar. Hotfix für CQ-4246583, CQ-4252700

**Korrespondenzverwaltung**

* Javadocs für 6.4 enthält nicht com.adobe.dbforms.* -Paket und die entsprechenden Klassen. Hotfix für CQ-4253200
* Die CCR-Benutzeroberfläche zeigt einen standardmäßigen Junk-Wert für das Datumsfeld an, falls keine Eingabe aus der XML der Testdaten erfolgt. Hotfix für CQ-4252041
* Wenn ein Brief ein Liste-Modul enthält, geht beim Generieren von PDF-Dateien aus dem Brief der Abstand zwischen Aufzählungszeichen und Text verloren. Hotfix für CQ-4250588

**Forms Manager**

* Unterstützung für die Eigenschaft allowedPaths in Vorlagen für adaptive Formulare aktiviert. NPR-26598: Hotfix für CQ-4255892

**Forms – Workflow**

* Wenn beim Ausführen des Forms-Workflows Klammern im Namen der Aufgabe enthalten sind, wird eine Ausnahme in den Protokollen angezeigt. Hotfix für CQ-4256626
* Suchvorlage kann nicht in AEM Forms Workspace geöffnet werden. Hotfix für CQ-4255651

**Mobile Forms**

* Die Ausstiegsbenachrichtigung wird beim Beenden des Datumsfelds in AEM Forms nicht angezeigt, das in Internet Explorer oder Chrome als HTML wiedergegeben wird. NPR-26483: Hotfix für CQ-4239352
* Daten, die bei Beginn der Verarbeitung in der XML enthalten sind, führen dazu, dass die Formulare einen Validierungsfehler auslösen, wenn der Benutzer versucht, das Formular zu verlassen. NPR-26787: Hotfix für CQ-4251211

**Forms JEE-Installationsprogramm**

**PDF Generator-Dienst**

* Die Einstellungen für &quot;Standards Berichte&quot;und &quot;Kompatibilität&quot;für PDF Generator können nicht angezeigt werden. NPR-26715: Hotfix für CQ-4253384
* Die Binärdatei &quot;convertpdf&quot;fehlt im AIX Forms Add-On-Paket, was beim Aufrufen des PDFA-Dienstes zu Fehlern führt. Hotfix für CQ-4257873
* Der Papiererfassungsdienst stürzt bei der Verarbeitung von TIFF-Dateien ab. NPR-28079: Hotfix für CQ-4240649

**Dokument Services**

* hinzufügen FIPS-Kompatibilität für den RE-Arbeitsablauf in Digital Signature, Reader Extensions, CryptoProvider und TrustStore. NPR-27495: Hotfix für CQ-4257572
* Die Konvertierung schlägt fehl, wenn AssemblerService.toPDFA-Dienst in einer Schleife ausgeführt wird. NPR-26354: Hotfix für CQ-4248656
* Die PDF-Kompatibilität kann nicht ordnungsgemäß anhand der PDF/A-1b-Standards überprüft werden. NPR-26286: Hotfix für CQ-4227539
* Probleme mit ungenügendem Arbeitsspeicher bei der Aktualisierung von AEM Forms von 6.1 SP2 CFP5 auf CFP13. NPR-26285: Hotfix für CQ-4244379
* Die PDF-Kompatibilität kann nicht ordnungsgemäß anhand von PDF/A-Standards überprüft werden. NPR-26272: Hotfix für CQ-4248823

**Forms – Foundation JEE**

* JBoss 7.1.4-Unterstützung für AEM Forms 6.4 hinzugefügt. NPR-27331; Hotfix für CQ-4255601

**Enthaltene Feature Packs**

* Unterstützung für ein Array/eine Liste von Objekten mit der dynamischen Entitätsersetzung aktiviert. NPR-26590: Hotfix für CQ-4254655

**OSGI-Pakete und Inhaltspakete enthalten**

Liste der in AEM 6.4.3.0 enthaltenen OSGi-Bundles

[Datei laden](assets/6.4.3.0_bundles.txt)

Liste der in AEM 6.4.3.0 enthaltenen Inhaltspakete

[Datei laden](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

AEM 6.4.2.0 ist ein wichtiges Update, das Funktionen für Leistung, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen umfasst, die seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht wurden.****
Es ist auch kumulativ, was bedeutet, dass 6.4.2.0 alle AEM 6.4 Service Packs vor der Veröffentlichung beinhaltet.

Einige der wichtigsten Highlights von AEM 6.4.2.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.7 aktualisiert.
* Neue Unterstützung für HTML-Vorlagensprache (HTL) Spezification 1.4-Funktionen
* Unterstützung für MongoDB Enterprise 3.6 hinzugefügt.
* Der Seiten-Editor für Sites unterstützt jetzt die kontextbezogene Bearbeitung und Komposition mit clientseitigen Komponenten, die in React oder Angular in Kombination mit <a href="../sites-developing/spa-walkthrough.md">AEM SPA Editor JS SDK</a> erstellt wurden.
* Verbesserungen bei Inhaltsfragmenten: Die Funktion zum Kommentieren in Textfeldern wurde hinzugefügt. Außerdem können Versionen nebeneinander verglichen werden.
* Die [Integration mit Adobe Stock](/help/assets/aem-assets-adobe-stock.md) wurde hinzugefügt, damit die Benutzer Adobe Stock-Assets direkt über AEM Benutzeroberfläche suchen, Vorschau, speichern und lizenzieren können. Weitere Informationen finden Sie unter [Verwenden von Adobe Stock-Assets mit AEM Assets](https://docs.adobe.com/content/help/de-DE/experience-manager-learn/assets/creative-workflows/adobe-stock.html).
* Assets unterstützen jetzt das dynamische bedingte Metasystem und die Möglichkeit, ein Metadaten-Schema für Asset-Ordner festzulegen.
* Es wurde eine Konfiguration in jeder Komponente hinzugefügt, um die Funktion zum Erstellen/Aktualisieren von Ordnerminiaturen zu aktivieren/deaktivieren.
* Verbesserungen am Bildeditor beim Erstellen von Seiten.
* Regressionskorrektur in Communities für Ereignisse, die nicht ordnungsgemäß verarbeitet werden, wenn eine Antwort gelöscht wird.
* Die maximale Suchergebnisgrenze für Solr wurde auf MAX_INT-10000 überarbeitet.
* Der Auftrag zum Transaktionsflush wird nur beim ersten Aufruf von storeTransaction gestartet.
* Die Schaltfläche &quot;Alle auswählen&quot;ist jetzt in der Ansicht &quot;Ansicht der Karte&quot;und &quot;Spalte&quot;verfügbar.
* Verbesserungen der Barrierefreiheit in CoralUI.
* Verbesserte Handhabung von Coral.Keys.
* Aktualisierung von &quot;Moment.js&quot;auf 2.2.2
* jquery auf 1.12.1 aktualisiert
* Vorgestellte Foundation-Workflow-Statuskomponente.
* GCC auf die neueste Version aktualisiert.
* Verschieben Sie SAML in die neue externe IDP-Synchronisierung.

**Assets**

* Die Generierung von Teilassets für die pptx-Datei enthält keine Bilder und Miniaturansichten. NPR-24286: Hotfix für CQ-4217986
* migrateAllAssets - Hinzufügen Unterstützung für die Stapelverarbeitung und Verbesserung der AEM Methode, die alte Assets mit UUID ergänzt. NPR-24861: Hotfix für CQ-4242863 und CQ-4247874
* Leistungsproblem bei der Erstellung von Miniaturbildern. NPR-24693: Hotfix für CQ-4246960
* (Touch-Benutzeroberfläche) Die Komponente &quot;options Predicate&quot;bleibt leer, wenn sie der Seite &quot;Asset Share-Herausgeber&quot;hinzugefügt wird. NPR-24643: Hotfix für CQ-4245295
* (Workflow) Smart-Tag-Assets werden nicht über die Proxykonfiguration verarbeitet. NPR-25840: Hotfix für CQ-4248202
* (Omniture Search) Wenn Sie filetype:image aus den Suchkriterien entfernen, wird der Bildtyp nicht entfernt. NPR-25232: Hotfix für CQ-4248280
* Beim Versuch, eine Datei in einen anderen Ordner zu verschieben, werden keine Ordner mit Apostroph in ihrem Namen angezeigt. NPR-25125: Hotfix für CQ-4248660
* Der Schieberegler auf der Seite &quot;Unterasset&quot;funktioniert nicht ordnungsgemäß, wenn die Spracheinstellung auf &quot;Sonstige&quot;eingestellt ist. NPR-25274: Hotfix für CQ-4248489
* Problem beim Exportieren der CSV-Datei für Metadaten, wenn diese auf Computern mit europäischem Zahlenformat geöffnet wird. NPR-26009: Hotfix für CQ-4250677
* Schaltfläche &quot;Erstellen&quot;ist bei der Auswahl des Asset-Ordners ohne Berechtigung zum Löschen nicht verfügbar. NPR-25788: Hotfix für CQ-4250140
* (Backport) Barrierefreiheitsverbesserungen: Duplikat-ID: id-Attributwert muss eindeutig sein, Beschriftung: Formularelemente müssen über Beschriftungen und Linknamen verfügen: Links müssen einen erkennbaren Text enthalten. NPR-24252: Hotfix für CQ-4250905, CQ-4250906, CQ-4250907
* Das Hochladen einer CSV-Datei mit Feldern, die durch &quot;,&quot;getrennt sind, schlägt in europäischen Ländern fehl. NPR-25549: Hotfix für CQ-4249931
* (Markenportal) Subassets einer mehrseitigen PDF-Datei werden nicht veröffentlicht, wenn ein Asset veröffentlicht wird. NPR-25991: Hotfix für CQ-4245162
* Veröffentlichen Sie spätere Funktionen für die Replizierung von AEM in Brand Portal. NPR-25911: Hotfix für CQ-109139
* Das Veröffentlichen und Rückgängigmachen der Veröffentlichung der privaten Sammlung durch Benutzer, die keine Administratoren sind, führt zu einem NPE. NPR-25906: Hotfix für CQ-4250594
* Deaktivieren Sie die Veröffentlichung von Inhaltsfragmenten und Forms-Schemas im Markenportal. NPR-24176, NPR-26004: Hotfix für CQ-4251592, CQ-4252026
* (Dynamic Media) Aktualisierung von DM-Viewern auf Version 5.10.1, die die Suche nach Duplikat auf der Seite &quot;Bildvorgabe&quot;ermöglicht. Weitere Informationen finden Sie unter Aktualisieren von Dynamic Media Viewern (5.10.1). NPR-24403: Hotfix für CQ-4247554
* JavaScript-Fehler in der Browser-Konsole in der Ansicht Spalte bei Auswahl eines Assets oder Ordners. NPR-25939: Hotfix für CQ-4250228
* (Ansicht der Spalten) Aufgaben können nicht identifiziert werden, da die Schlüsseldatei als leerer weißer Eintrag angezeigt wird. NPR-25903: Hotfix für CQ-4246307

**Sites**

* Die Abfrage von datasource.jsp auf AEM 6.2 unterscheidet sich von AEM 6.4. NPR-24968: Hotfix für CQ-4244235
* (Klassische Benutzeroberfläche) Seiten können keine Tags hinzugefügt werden. NPR-25255, NPR-25612: Hotfix für CQ-4249615
* Sprachspezifikation für HTML-Vorlagen 1.4 Funktionen, die auf AEM 6.4.2.0 NPR-24585 zurückportiert sind
* Falsche Vererbung bei einer lokalen Komponente nach dem Kopieren einer Live Copy-Seite. NPR-25920: Hotfix für CQ-4236737, CQ-4248957
* Die EIN-/AUS-Zeit wird in crx/de gespeichert, ruft jedoch nicht dasselbe in der UI-Konsole der Seiteneigenschaften ab. NPR-25154: Hotfix für CQ-4243431
* Stile Systemumbrüche die anfänglichen Eigenschaftenwerte des Dialogfelds. NPR-25648: Hotfix für CQ-4250073
* Beim Definieren einer Eigenschaft cq:tagName in einem Knoten cq:htmlTag wird der Tag-Name nicht berücksichtigt, wenn die Komponente über JSP eingeschlossen wird. NPR-24154: Hotfix für CQ-4244120
* Bei verschachtelten parsys-Komponenten wird immer der erste (mit dem am wenigsten verschachtelten Pfad) passende Entwurf aus mehreren verfügbaren Komponenten angewendet. Weitere Informationen finden Sie unter [Designpfad-Auflösung](https://docs.adobe.com/content/help/en/experience-manager-64/developing/platform/templates/page-templates-static.html). NPR-24973: Hotfix für CQ-4246276
* Beim Einfügen von Text in eine RTE-Komponente wird ein Popup-Dialogfeld angezeigt, das jedoch nicht ordnungsgemäß wiedergegeben wird. NPR-24895: Hotfix für CQ-4245901
* (RTE) Leistungsprobleme mit obligatorischer Feldanzeige. NPR-24894: Hotfix für CQ-4241895
* (Seitenkomponente) Wenn Sie eine Komponente zu Parsys hinzufügen, wird sie von rechts abgeschnitten und die Rahmenbreite des Geräts wird gelöscht. NPR-25536: Hotfix für CQ-4238224
* Der Plaintext-Editor sendet nicht zugeschnittene Daten und fügt zusätzliche Leerzeichen hinzu. NPR-25312: Hotfix für CQ-4249006
* Beim Öffnen der Komponente im Inlide-Modus sind zuvor geladene Plugins beim zweiten Mal nicht sichtbar. NPR-24610: Hotfix für CQ-4236850
* Beim Laden einer XF-Datei in der Editor-Ansicht per Kopieren/Einfügen wird die Übergeordnet-Variante nicht automatisch geladen. NPR-24841: Hotfix für CQ-4248037
* Falsche HTML-Struktur in siteadmin/damadmin bricht IE11. NPR-24686: Hotfix für CQ-4246363, CQ-4248402
* (Assistent zum Verwalten von Veröffentlichungen) Der Kalender für das Datum der Aktivierung im Schritt &quot;Optionen&quot;wird nach einigen Aktionen im Schritt &quot;Umfang&quot;nicht geöffnet. NPR-25681: Hotfix für CQ-4250205
* Die klassische Benutzeroberfläche funktioniert aufgrund der veralteten Version nicht, um CUG zu bearbeiten. NPR-25075: Hotfix für 4241823
* Option nicht verfügbar erstellen, um Erlebnisfragmente zu erstellen. NPR-26053: Hotfix für CQ-4249923
* XF-Variation wird daher zweimal aktiviert, wodurch Duplikat-IDs für dasselbe Element generiert werden. NPR-24179: Hotfix für CQ-4245093
* Foundation-Tabelle ist anfällig für Stored Cross Site Scripting. NPR-25185: Hotfix für CQ-4240760
* Fehler &quot;Ungültiger Rekursionsauswahlwert&quot;bei der Migration einer Komponente von AEM 6.2.1.13 auf AEM 6.4. NPR-24146

**WCM – Seiteneditor**

* Mehrere gestapelte Parsys aufgrund langwieriger Abfragen (über 6) verlangsamen AEM. Hotfix für CQ-4240247
* JS-Fehler beim Hinzufügen von leerem cq:tagName im cq:htmlTag-Knoten. Hotfix für CQ-4251852
* Aktualisieren Sie EditableActions auf Grundlage der columnClassNames-Umlagerung. Hotfix für CQ-4250781
* Bieten Sie Ressourcen- und Modellpfade mit einer einzelnen Eigenschaft und einem einzigen Attribut an. Hotfix für CQ-4251255
* Zurücksetzen von Änderungen an der export.json-API Hotfix für CQ-4251854
* (Bearbeitbare SPA) Release-Kandidat für 1.0.0. Hotfix für CQ-4251991
* Die Bearbeitungssymbolleiste wird bei der Bearbeitung einer Komponente für andere Komponenten deaktiviert. Hotfix für CQ-4253270

**Integration**

* Die Felder &quot;Bibliothek&quot;und &quot;URL herunterladen&quot;sollten bearbeitet werden können. NPR-24804: Hotfix für CQ-4246864
* Problem mit mehreren DTM-Konfigurationen. NPR-24685: Hotfix für CQ-4247293
* Unterstützung für die asynchrone Bereitstellung für gehostete Clientbibliotheken hinzugefügt. NPR-25716: Hotfix für CQ-4245745
* Die Zielkomponente mit fehlendem Angebot rendert die gesamte Seite und anstelle einer leeren Zielkomponente wird eine weitere vollständige Darstellung der Seite hinzugefügt. NPR-25273: Hotfix für CQ-4248003
* Die Target-Engine (mbox.js, at.js) verwendet keine verwalteten URLs, und sie verwendet URLs mit Doppelpunkten, die bei bestimmten Bereitstellungen fehlschlagen können. NPR-25339: Hotfix für CQ-4237854
* (Launch)LibraryDownloadProcess speichert den falschen libraryUri-Wert. NPR-25330: Hotfix für CQ-4250006

**Plattform**

* Wiederverwendungs-Schleife | NPE während der Durchführung der BinaryTextExtract-Aktualisierung von 6.3 auf 6.4. Hotfix für Granit - 21677
* Grenzüberschreitende Außerkraftsetzung des internen markierten Pfads /libs/cq/cloudserviceconfigs/templates/configpage/jcr:content - Problem beim Ausführen des Musterdetektors. NPR-25036: Hotfix für CQ-4248597
* Protokolleinträge, die aufgrund von NPE in LogEntryImpl nicht geschrieben wurden. NPR-25627: Hotfix für Granite-22383
* Die Replizierung des Löschvorgangs-Ereignisses überprüft keine Rechte. NPR-25679: Hotfix für CQ-4241234
* STARTTLS-Unterstützung in &quot;Day CQ Mail Service&quot; hinzugefügt. NPR-25611: Hotfix für CQ-4249924
* Proaktiver Backport für granite.platform.login Korrekturen zur Verbesserung der Barrierefreiheit. NPR-25176: Hotfix für Granit 21746 und Granite-21309
* (AEM 6.4) Fehler beim Erstellen und Neuinstallieren des Pakets. NPR-25173: Hotfix für CQ-4247939
* Die standardmäßige MERGE_PRESERVE aclHandling wurde entfernt. NPR-24593: Hotfix für Granite-21889
* Content-Type wird nicht vorgeschlagen und fehlt in der Antwort, nachdem ContentDispositionFilter zweimal angewendet wurde. NPR-24175: Hotfix für Sling-7525
* Package Manager-Status nach der Aktualisierung auf AEM 6.4-Verzweigung falsch. NPR-24551: Hotfix für Granite-21750
* AMS-Instanz - Analyse für Fehlerprotokolle Hotfix für CQ-4249567

**Sicherheit**

* SAML meldet sich erneut auf die Abmeldeseite mit Okta IDP an. NPR-25523: Hotfix für GRANITE-22364
* IMS-Authentifizierung über OAK externe IDP OAuth Provider-Konfigurationen deaktiviert den in AEM erstellten Benutzer. NPR-25301: Hotfix für Granite-22363

**MAC - Test- und Target-Integration**

* (Targeting) Textkomponentenfehler während des Targeting. Hotfix für CQ-4233343

**Communities**

* (Dateibibliothek) Das Herunterladen von Assets mit Leerzeichen verursacht Formatprobleme. NPR-24260: Hotfix für CQ-4245159
* Fehlerbehebungen bei mehreren Adobe Social-Problemen. NPR-24247: Hotfix für CQ-4245054, CQ-4245120, CQ-4245296
* Der unbegrenzte Bildlauf für Mitglieder und Gruppen-Konsole schlägt fehl, wenn die Autor-Veröffentlichung auf unterschiedlichen Kontextpfaden ausgeführt wird. NPR-24437: Hotfix für CQ-4246013
* Der Beitrag kehrt nicht zum Status &quot;Nicht beantwortet&quot;zurück, selbst wenn er aus dem Status &quot;Antworten&quot;entfernt wird, und das Ergebnis wird nicht verringert. NPR-24419: Hotfix für CQ-4245797, CQ-4245932
* Ereignis, die mit Kalenderfunktionen in Communities hinzugefügt wurden, geben falsche Werte aus. NPR-24883: Hotfix für CQ-4244056
* (Community-Forum) Probleme mit dem Verhalten von Seitenumbrüchen und Seitenladevorgang. NPR-24880: Hotfix für CQ-4246109
* (Chrome) Zeitzonenkonvertierungen schlagen auf Communities-Ereignissen fehl. NPR-24881: Hotfix für CQ-4247115
* Eingebettetes Objekt kann nicht in E-Mail gerendert werden. NPR-24999: Hotfix für CQ-4248022
* Zusätzlich zur UGC-Erstellung sollte eine Automatisierungssequenz bei UGC-Aktualisierungen ausgeführt werden. NPR-25892: Hotfix für CQ-4251399
* Reaktionsgeschwindigkeit im modalen Dialog auf Gruppen. NPR-25623: Hotfix für CQ-4248805
* Beim Löschen von Inhalten wird eine Ausnahme ausgelöst. NPR-25869: Hotfix für CQ-4248908
* Paginierte Links zu Threads mit vielen Beiträgen funktionieren nicht bei Benachrichtigungen. NPR-25678: Hotfix für CQ-4243038
* Zeitwerte in Suchergebnissen zeigen die Serverzeit anstelle der Zeitzone des Clients an. NPR-25594: Hotfix für CQ-4248986
* (Forumkommentare) Die Schaltfläche &quot;Zurück zum Browser&quot;funktioniert nicht wie erwartet. NPR-25205: Hotfix für CQ-4248573
* (Suchergebnisse) Die Schaltfläche &quot;Zurück zum Browser&quot;funktioniert nicht wie erwartet. NPR-25214: Hotfix für CQ-4248574
* Null wird zurückgegeben, wenn die Komponente communitygroupList überlagert wird. NPR-25228: Hotfix für CQ-4248523
* (Communities Calendar) ClassCastException wird beim Speichern des Ereignisses mit dem neuen Deckblattbild generiert. NPR-25167: Hotfix für CQ-4248662
* (Communities) Nachrichten werden abgeschnitten. NPR-25326
* (AEM Publish) Die Scorm-Ressource schlägt mit dem Kontextpfad fehl und zeigt einen leeren Bildschirm an. NPR-26155: Hotfix für CQ-4251942
* (MSRP) Der neu erstellte Kalender wird teilweise gespeichert, indem NPE im Fehlerprotokoll ausgegeben wird. NPR-26071: Hotfix für CQ-4250531
* Die Paginierung von Forum/Thema wird nur aktualisiert, wenn die Seite aktualisiert wird. NPR-26070, NPR-25965: Hotfix für CQ-4249509
* (Frage-und-Antwort-Forum) Beim Öffnen eines direkten Links zu einem Kommentar kann nicht zur vorherigen Seite navigiert werden. NPR-26069: Hotfix für CQ-4251699
* Bild in Gruppe erstellen kann nicht auf Mobilgeräten hochgeladen werden. NPR-26172: Hotfix für CQ-4251703
* (Messaging) Bei Verwendung von DSRP wird der Name des Empfängers immer als &quot;Unbekannt&quot;angezeigt. NPR-26056: Hotfix für CQ-4251397
* Die Statusbeschriftung zum Abschluss der Aktivierungs-Scorm-Ressource wird in der Benutzeroberfläche leer angezeigt. NPR-26034: Hotfix für CQ-4249994
* Beim Erstellen einer neuen Community-Gruppe wird eine Duplikat Community-Gruppe auf einem aktiven/aktiven MongoMK-Cluster erstellt. NPR-26032: Hotfix für CQ-4245884
* (Autor) Der Assistent zum Erstellen von Gruppen dauert zu lange, bis eine Gruppe im Assistenten geladen bzw. erstellt wird. NPR-26031: Hotfix für CQ-4244966
* Parsys werden beim Hinzufügen einer include-Anweisung im hbs-Skript ausgeblendet. NPR-25908: Hotfix für CQ-4250489
* Wenn Sie „Priviligierte Mitglieder zulassen“ aktivieren, sollten die privilegierten Mitglieder nur Inhalte für Benutzer erstellen können, die Mitglieder der Community sind. NPR-25877: Hotfix für CQ-4248450
* Deep-Links zur Aktivierung gesperrt. NPR-25966: Hotfix für CQ-4251478
* Die Forumpaginierung wird beim Entfernen der Antworten nicht dynamisch aktualisiert. NPR-25970: Hotfix für CQ-4248975, CQ-4252843
* Bei verschachtelten Ereignissen funktioniert die automatische Bildlaufleiste und -hervorhebung nicht. NPR-25958: Hotfix für CQ-4251471
* (DSRP) Die Direct/Deep Link-Leistung verschlechtert sich bei hohen Mengen von benutzergenerierten Inhalten. NPR-25957: Hotfix für CQ-4251470
* Die Eigenschaften von Allow Privileged Members and Privileged members können nicht geändert werden. NPR-26014: Hotfix für CQ-4244592
* Als gelesen markieren setzt die Benachrichtigungsmarken für alle Community-Seiten zurück. NPR-25931: Hotfix für CQ-4248612
* Bearbeiten von ITs bei DSRP fehlschlagen. NPR-25929: Hotfix für CQ-4251382
* E-Mail-ITs fehlschlagen aufgrund von NPE beim Erstellen von E-Mail-Vorlagen. NPR-26039: Hotfix für CQ-4250962
* Foren-Thread-Probleme beim Einbetten von Bildern mit sehr hoher Auflösung. NPR-26037: Hotfix für CQ-4244453, CQ-4253099
* Die Zeit zeigt Switches an, wenn die Zeitzone des Servers von der Zeitzone des Benutzers abweicht. NPR-26036: Hotfix für CQ-4248751
* Das Anhängen einer Datei mit demselben Namen an einen Forumsbeitrag führt zu einem Serverfehler. NPR-24172: Hotfix für CQ-4244367
* Fehlerbehebungen bei der Backport-Leistung: Seitennummerierung bei Autor und Veröffentlichung, Gruppensuche bei Autor, Vermeidung der Serialisierung von Antworten für Protokoll, Kalender und Idee sowie verzögertes Laden für die Gruppenmitgliedschaft (Einladen/Entladen) für jede Gruppe während der Anzeige der Gruppenlistenseite. NPR-24538: Hotfix für CQ-4246515
* Aktivierungsressourcen sind beim Autor nicht sichtbar. Hotfix für CQ-4252618
* Benachrichtigungen werden von Unbekannte Nutzer nicht für Thread generiert. Hotfix für CQ-4245132
* Die Gruppensuche wird in der linken Leiste nicht angezeigt. Hotfix für CQ-4252621
* (Autor) Paginierung funktioniert nicht in der Gruppenkonsole. Hotfix für CQ-4242786
* jQuery UI-Aktualisierung. Hotfix für CQ-4248894
* Aktualisieren Sie auf die neueste Version von SCORM 2017.1. NPR-25675: Hotfix für CQ-4240671
* Die Felder &quot;Im Namen erstellen&quot;sind für Benutzer ohne Community sichtbar. NPR-25331: Hotfix für CQ-4247858
* Der Beitrag ist auch nach dem Löschen auf der Benutzeroberfläche weiterhin sichtbar und gibt in der Konsole einen Fehler aus. NPR-26290: Hotfix für CQ-4252803
* (Site-Einstellungen) Kann Änderungen speichern, die an Rollen vorgenommen wurden. NPR-26274: Hotfix für CQ-4252187
* (Sicherheitslücke) Kontoübergabe aufgrund einer Fehlkonfiguration des JSON-Webtokens. NPR-26458: Hotfix für CQ-4253314
* Die Paginierung wird nach Entfernen der Antworten nicht zurückgesetzt. NPR-26326: Hotfix für CQ-4252997
* Das Anlagenbild wird während der Bearbeitung nicht in Entwürfen angezeigt. Hotfix für CQ-4253360
* Die Seite wird beim Anhängen der Anlage an die relationale Datenbank (DSRP) nicht aktualisiert. Hotfix für CQ-4253084
* Gruppen funktionieren nicht innerhalb der Ressourcen der Website für die Aktivierung. Hotfix für CQ-4252975
* Voraussetzungen Lernpfade werden in der Aktivierung nicht beibehalten. Hotfix für CQ-4252948

**Arbeitsablauf**

* Die Benutzeroberfläche des Workflow-Starters zeigt keine vorherigen 41 Startkonfigurationen an und Trigger einen JavaScript-Fehler in der Konsole. NPR-25028: Hotfix für CQ-4247604
* Wenn Sie einen alten Workflow bearbeiten, ohne dessen Starter zu bearbeiten, werden mehrere Workflows für jeden Workflow erstellt, der einen Schritt zum Aktivieren der Seite/des Assets enthält. NPR-25870: Hotfix für CQ-4250896
* Falscher Link in der Workflow-Nutzlast, wenn die Seite über einen Metadaten-Knoten verfügt. NPR-25916: Hotfix für CQ-4250733

**Übersetzung**

* Es wurde behoben, dass beim Importieren eines übersetzten Projekts zwei Anforderungen an die gleichzeitige POST gestellt wurden, wodurch ein Fehler auftrat. NPR-24889: Hotfix für CQ-4247638
* Es wurde behoben, dass beim Erstellen eines Übersetzungsprojekts für mehrere Sprachen alle Seiten für dieselbe Sprache demselben Auftrag hinzugefügt werden. NPR-25091: Hotfix für CQ-4246112
* Es wurde behoben, dass in einigen Fällen Übersetzungsaufträge nur auf die 40 Seiten der obersten Ebene Liste wurden. NPR-25974: Hotfix für CQ-4248661
* DataPicker-Komponente (Coral2), die das Jahr nicht ändert. NPR-24466: Hotfix für Granite-21893

**Benutzeroberfläche - Foundation**

* Proaktive Unterstützung von Foundation UI Backports. NPR-24344, NPR-24345, NPR-25176, NPR-25095, NPR-24332, NPR-25653, NPR-25932, NPR-2599 35, NPR-25976
* (Design Importer) Beim Importieren einer Seite wird die Datei &quot;js,css&quot;nicht importiert. NPR-25203: Hotfix für Granite-22236
* Proaktive Unterstützung der Foundation-Benutzeroberfläche zur Verbesserung der Stabilität des Produkts. NPR-24334

**MAC - Test- und Target-Integration**

* Die zweite Seite des Personalisierungsassistenten (gestartet durch &quot;Beginn-Targeting&quot;) ist leer und löst Konsolenfehler aus. Hotfix für CQ-4253277

**Erlebnisfragmente**

* Integration von Erlebnisfragmenten/Zielgruppen in AEM 6.4.2.0. Hotfix für CQ-4248653

**Verwaltung von Inhaltsfragmenten**

* Inhaltsfragmente - Anmerkungen und Vergleich von Inhaltsfragmentversionen. Hotfix für CQ-4247148

**DAM - Allgemeines**

* Der Filter &quot;Ausgecheckt von&quot;funktioniert nicht ordnungsgemäß in der Suche. Hotfix für CQ-4247070
* Beim Ausführen des Arbeitsablaufs für die Asset-Aktualisierung werden die Asset-Sprachkopie und die dazugehörige Miniaturansicht leer. Hotfix für CQ-4250641
* Duplikat-ID: Der Wert des id-Attributs muss eindeutig sein. Hotfix für CQ-4250905
* Beschriftung: Formularelemente müssen Beschriftungen haben. Hotfix für CQ-4250906
* Linkname: Links müssen einen erkennbaren Text enthalten. Hotfix für CQ-4250907
* Migration von JMX- und ServiceUserMapping zu Metadaten für den Anschlussordner. Hotfix für CQ-4252947
* WebdriverIO Tests, die nicht in Release/640 von CQ/dam ausgeführt werden. Hotfix für CQ-4252749
* Links zu verschobenen Assets werden nicht umgestaltet, wenn der Link veröffentlicht wird. Hotfix für CQ-4245756

**DAM - Viewer**

* Zeitweiliger Fehler beim Laden von Videos mit neuen Viewern 5.10.1. Hotfix für CQ-4250562

**DAM-Markenportal**

* Das Rückgängigmachen der Veröffentlichung der Sammlung im Markenportal schlägt fehl. Hotfix für CQ-4245990
* Die Veröffentlichung von Bildvorgaben aus dem Markenportal kann nicht rückgängig gemacht werden. Hotfix für CQ-4246140
* Teilassets einer mehrseitigen PDF-Datei werden nicht veröffentlicht, wenn ein Asset veröffentlicht wird. Hotfix für CQ-4245162

**DAM - DMClient**

* Beim Veröffentlichen eines Video-Assets auf YouTube enthalten die Tags, die zu YouTube führen, den vollständigen Pfad des Tags. Hotfix für CQ-4245549
* (Opt-out- und Opt-in-Upgrades) Problem bei der Viewer-CSS-Umleitung. Hotfix für CQ-4247854
* Viewer-Vorgabe kann nicht als Nicht-Mitglied der Gruppe &quot;Administratoren&quot;erstellt/bearbeitet werden. Hotfix für CQ-4247618
* (6.4.1.0) Durch Hinzufügen mehrerer Videos in mehreren Parsen wird der Videoplayer beschädigt. Hotfix für CQ-4248517
* Durch Umbenennen und Verschieben von Assets innerhalb eines Bildsatzes wird die Bearbeitung unmöglich. Hotfix für CQ-4248434
* Wenn Sie große Videos auf YouTube veröffentlichen, werden Zeitüberschreitungsmeldungen ausgegeben. Hotfix für CQ-4237831
* (Liste-Ansicht) Die Benutzeroberfläche des Asset-Pickers/Selektors wird grau und für den Benutzer deaktiviert. Hotfix für CQ-4237817
* (Vertikaler Zoom) CSS wird mit einem 404-Fehler nicht geladen. Hotfix für CQ-4236508
* Der Versuch, ein Asset mit Prozentzeichen (%) im Asset-Namen herunterzuladen, führt zu einem leeren Archiv. Hotfix für CQ-4250558
* (Ansicht der Karte) Bei der Verwendung von &quot;Kopieren&quot;und &quot;Einfügen&quot;in einem Video-Asset wird kein Verarbeitungsindikator angezeigt. Hotfix für CQ-4249037
* (Aktualisierung von 6.3.2 auf 6.4) Bildvorgaben vor der Aktualisierung werden auf der Seite &quot;Darstellungen&quot;als &quot;unveröffentlicht&quot;angezeigt, geben aber bei Auswahl nicht die URL-Schaltfläche aus. Hotfix für CQ-4240406
* Technische Schulden/geringfügige Verbesserungen. Hotfix für CQ-4240648
* In der Asset-Auswahl (oder Asset-Auswahl) werden nicht alle Assets aus den verfügbaren Ordnern angezeigt. Hotfix für CQ-4218414
* Bildvorgabe ohne Höhe zeigt Bilder mit falscher Größe an. Hotfix für CQ-4246546
* (Multi-Page Assets) Die Benutzeroberfläche wird beim Klicken auf Anmerkungen umgebrochen. Hotfix für CQ-4251434
* Bei einem Upgrade von 6.3 auf 6.4 und höher auf die Analytics-Vorgabe wird eine neue Report Suite- und Analytics-Vorgabe erstellt, bei der die Daten älterer Berichte verloren gehen. Hotfix für CQ-4244529
* (Veröffentlichungsassistent verwalten) Die Liste der Assets scheint beim Veröffentlichen oder Rückgängigmachen der Veröffentlichung leer zu sein. Hotfix für CQ-4251881
* Bei der Auswahl von Viewern nach der Anzeige der Set-Member können AVS-Videos nicht wiedergegeben werden. Hotfix für CQ-4205308
* Vorab aktualisierte Video-Verarbeitungsvorgaben dürfen weder eine neue Video-Kodierungsvorgabe hinzugefügt noch die vorhandenen Kodierungsvorgaben bearbeitet werden. Hotfix für CQ-4240407
* Bildvorgaben werden nicht auf heruntergeladene dynamische Darstellungen angewendet. Hotfix für CQ-4249862
* Die Schaltfläche &quot;Alles auswählen&quot;funktioniert auf der Listenseite &quot;Viewer-Vorgaben&quot;nicht ordnungsgemäß. Hotfix für CQ-4252462
* Video-Profile: Schaltfläche &quot;Alle auswählen&quot;funktioniert nicht. Hotfix für CQ-4253076, CQ-4251447
* SP2 Validierung Pass - Rauch Pass. Hotfix für CQ-4251639

**DAM - DMServices**

* Dynamic Media-Darstellungen konnten nicht für die EPS-Datei generiert werden. Hotfix für CQ-4243688

**Granit**

* Typo im Bundle SymbolicName führt zum Duplikat-Bundle. Hotfix für Granite-22155
* CUGConconfiguration kann CugExclude möglicherweise nicht abrufen. Hotfix für Granite-21109
* Beim Neustart von Adobe Granite Workflow Core werden die Workflow-Schritte von der Mitte aus erneut ausgeführt, sodass unnötige Workflows entstehen. NPR-25057: Hotfix für Granite-22218
* JcrResourceBundle unterstützt nicht ordnungsgemäß mehrere Basisnamen. NPR-25245: Hotfix für Granite-22317
* Bei der Installation von Inhaltspaketen werden die ACLs nach Prinzipal gruppiert, wodurch das Berechtigungsmodell gebrochen wird. NPR-24583: Hotfix für Granite-21591
* Aktualisieren Sie Jetty auf 9.4.11, um Schwachstellen zu beheben. NPR-25030: Hotfix für Granite-22120

**Formulare**

Zu den wichtigsten Merkmalen von AEM 6.4.2.0 Forms gehören:

* Neue Eigenschaft für Warteschlangen hinzugefügt, die aktualisiert werden soll, ohne den Browser zu aktualisieren.
* Zusätzliche Funktion für den Benutzer, dieselbe WSDL-Datei für mehrere Dienste zu verwenden.
* Das nicht unterstützte Zeitstempelmuster wurde aus der Dropdown-Liste &quot;Datumsauswahl&quot;entfernt.
* Unterstützung für die Ausführung von xfaf und pdf in OSGI hinzugefügt.
* Unterstützung für die Verwendung der Funktion [Transaktionsberichte](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) bei lokalen Bereitstellungen hinzugefügt.
* Es wurde Code hinzugefügt, um die untergeordnete var im Bedingungsregel-Editor nicht anzuzeigen.

**Forms-Add-on-Paket**

**Transaction Berichte**

* Aktualisieren Sie die Configuration von Transaction Berichte mit der Wichtigkeit der auf einem Publish-Server konfigurierten Rückwärtsreplikation. NPR-26050: Hotfix für CQ-4246650
* Verzögerte Initialisierung des Periodic Flush-Auftrags. NPR-25968: Hotfix für CQ-4245024
* Die Transaktionsaufzeichnung schlägt mit Null-Zeiger-Ausnahme fehl. Hotfix für CQ-4247302

**Forms – Workflow**

* (HTML Workspace) Wenn ein Benutzer eine Aufgabe beansprucht, wird die Anzahl der Warteschlangen für den betreffenden Benutzer aktualisiert, nicht jedoch für andere Benutzer, es sei denn, die Seite wird aktualisiert. Dieses Problem wurde durch eine neue Eigenschaft behoben. Informationen zum Konfigurieren dieser neuen Eigenschaft für Ihre AEM Instanz finden Sie in den Konfigurationseinstellungen. NPR-24536: Hotfix für CQ-4233665
* Großes Formular kann nicht in die AEM Forms App auf 6.4 geladen werden. NPR-24463: Hotfix für CQ-4245091
* Problem in der Mobile Workspace-App, wenn versucht wird, die freigegebene Aufgabe Ansicht. NPR-25177: Hotfix für CQ-4248733
* Inkonsistentes Überprüfungsverhalten zwischen Web und APK. NPR-25670: Hotfix für CQ-4248178
* Wenn ein Aufruf an einen Webdienst erfolgt und ein HTML5-Formular im Client geöffnet wird, schlägt er fehl und eine Fehlermeldung wird zurückgegeben. NPR-26048: Hotfix für CQ-4244716
* Problem beim Aufrufen des Dienstes in AEM Forms Windows App 6.3. NPR-26468: Hotfix für CQ-4252341

**Forms**

* (Formularsatz) Validierungsfehler bei SSN- und Mobile-Feldern bei der Vorschau. NPR-24458: Hotfix für CQ-4244983
* Daten werden nicht angezeigt, wenn mehrzeilige Felder in der HTML-Vorschau vorausgefüllt sind. NPR-24549: Hotfix für CQ-4244212
* Daten gehen verloren, wenn das Skript in einem mehrzeiligen Feld ausgewertet wird. NPR-25333, Hotfix für CQ-4249610

**Forms - Interaktive Kommunikation und Correspondence Management**

* Die Synchronisierung schlägt auf der IC mit Basic Template und Reference IC Print Template fehl. NPR-24912
* (CCR) Validatoren funktionieren nicht für Felder/Variablen. Hotfix für CQ-4245047
* Das Symbol &quot;Datenmodellobjekt&quot;wird in der Symbolleiste &quot;Textbearbeitung&quot;gelegentlich ausgeblendet. Hotfix für CQ-4245122
* Ausnahmeprotokolle werden auf kopierter IC angezeigt, wenn die ursprüngliche IC gelöscht wird. Hotfix für CQ-4249378
* In der Briefdarstellung wird die Bedingung nicht als &quot;true&quot;ausgewertet, selbst wenn die Daten korrekt sind. Hotfix für CQ-4245944
* Automatisch generierte Komponenten werden bei Auswahl aus der Inhaltsstruktur nicht hervorgehoben. Hotfix für CQ-4246178
* Probleme beim Öffnen des Web Kanal-Vorlageneditors. Hotfix für CQ-4248182
* Die Reihenfolge der hinzugefügten Elemente kann nicht geändert werden, da die Pfeile nach oben bzw. unten deaktiviert bleiben. Hotfix für CQ-4252042
* Eigenschaften des Bedingungsmoduls können nicht aktualisiert werden. Hotfix für CQ-4247909
* Die UX des Dialogfelds &quot;Vererbung abbrechen&quot;, wenn der Benutzer ein Objekt im Web Kanal neu anordnet, muss verbessert werden. Hotfix für CQ-4241076
* Daten im Brief, die den in XDP definierten Bindungen entsprechen, werden bei der Verwendung der URL des Direktbriefs nicht ausgefüllt. Hotfix für CQ-4245833
* (Zwischenspeicherungsproblem) Die Synchronisierung von Web-Kanal spiegelt keine Änderungen wider, die an Layout-Fragmenten, Textfragmenten des Kanals, vorgenommen wurden. Hotfix für CQ-4251460
* Layout-Fragmente und DD-Eigenschaften können nicht aktualisiert werden. Hotfix für CQ-4247830
* (CCR) Das Neuladen des Entwurfs schlägt aufgrund der XML-Analyse fehl. Hotfix für CQ-4250950
* (IC-Editor) Die Schaltfläche &quot;Fragment bearbeiten&quot;sollte leichter zu finden sein. Hotfix für CQ-4244694
* (XDP) Beim Hinzufügen eines Layout-Fragments zum neu erstellten Teilformular wird ein leerer Bildschirm angezeigt. Hotfix für CQ-4248810
* DocumentFragment-Übergeordnet-DeployWithServerSideTests-Testfehler. Hotfix für CQ-4245496
* Im Bedingungsmodul duplizierte Variableninstanz. Hotfix für CQ-4252128
* Die PDF-Vorschauen-URL zeigt beim Veröffentlichen keinen Transaktions-Berichte an. Hotfix für CQ-4246158
* IC Sync verwandte Probleme mit der Synchronisierung von Print Kanal mit Web Kanal. Hotfix für CQ-4251505
* EXM-Code-Bereinigung: Entfernen Sie LocalFunctionMapper. Hotfix für CQ-4243265
* Korrigieren des Ressourcentyps von TableHeader der webChannel-Tabellenkomponente von IC. Hotfix für CQ-4251821
* (IC Editor) Probleme mit der Benutzerfreundlichkeit. Hotfix für CQ-4241081
* Das Teilformular &quot;Kanal drucken&quot;zeigt keine Funktion zum Einfügen an. Hotfix für CQ-4252994
* Die Synchronisierung der Änderungen schlägt fehl, nachdem der FDM-Knoten oder der Platzhalter für die Variable entfernt wurde. Hotfix für CQ-4253178
* (Vorlagen-Editor) Die Basisvorlage zeigt zusätzliche Drag-Drop-Bereiche für Kopf- und Fußzeilen und flackert beim Öffnen des Web-Kanals. Hotfix für CQ-4253323
* Automatisch generierte Komponenten werden bei der Auswahl aus der Inhaltsstruktur nicht hervorgehoben. Hotfix für CQ-4246178

**Dokument Services**

* (Form Service) OSGI hat keine Unterstützung für XFAF. NPR-25181, Hotfix für CQ-4251313
* Die Zeichen in der Überschrift der assemblierten PDF-Datei werden langsam beschädigt. NPR-25113: Hotfix für CQ-4244682

**Adaptive Formulare**

* Übermittlungsaktion als &quot;Mail senden&quot;gibt eine Ausnahme aus, wenn die CC/BC-Felder leer sind. NPR-25019: Hotfix für CQ-4243039
* Die OOTB AEM Formularkomponente kann aufgrund der ineffizienten Abfrage nicht verwendet werden. NPR-25065: Hotfix für CQ-4247256
* Entfernen Sie sling:orderBefore von den Dialogknoten guideImageChoiceComponent. Hotfix für CQ-4245013
* (Datumsauswahl) Das Bearbeitungsmuster unterstützt nicht zwei Typen von Zeitstempelmustern. Hotfix für CQ-4237982
* Übermittlungsaktion mit Problemen beim Authoring in Forms Workflow Classic. Hotfix für CQ-4236981
* (Web Kanal) Das IC-Diagramm sollte die Eigenschaft colspan aus dem AF-Diagramm übernehmen. Hotfix für CQ-4252143

**Backend-Integration**

* (SOAP-Anforderungen) Große Dezimalstellen (mehr als 6 Stellen) werden in exponentieller Notation dargestellt, was zu einem Validierungsfehler führt. NPR-25283: Hotfix für CQ-4248100
* Falsche Validierung optionaler Parameter, die in komplexen Typen definiert wurden. NPR-25070: Hotfix für CQ-4247107
* Zusätzliche Funktion für den Benutzer, dieselbe WSDL-Datei für mehrere Dienste zu verwenden. NPR-24604, Hotfix für CQ-4247756
* FDM mischt die Reihenfolge der Parameter in seinen SOAP-Aufrufen. NPR-25069, Hotfix für CQ-4247180
* FDM führt Entitäten (in Liste/Array) in einer SOAP-Anforderung zusammen. NPR-25284: Hotfix für CQ-4248375

**Forms JEE-Installationsprogramm**

**PDFG-Dienst**

* Die Funktion zum Erstellen/Ändern von Sicherheitseinstellungen funktioniert nicht. NPR-24769: Hotfix für CQ-4246927
* Optimizen PDF durch selektives Aufheben der Einbettung von Schriftarten über einen einzelnen API-Aufruf. NPR-23287

**Dokument Services**

* Der Output-Dienst stellt nicht die korrekten Tags für den Reader der Ein-/Ausgabehilfe bereit. NPR-24438, NPR-24439, NPR-24440, NPR-24441: Hotfix für CQ-4243849, CQ-4243845, CQ-4243852, CQ-4243853

**Document Security**

* Problem mit der Richtlinienerstellung unter Verwendung von Dokument Security. NPR-25586, NPR-25547: Hotfix für CQ-4247086

**Forms – Foundation JEE**

* Prozesse, die zeitweise als Systemkontextkonto ausgeführt werden. NPR-25289, NPR-25313: Hotfix für CQ-4249331
* AEM Forms JEE wurde von der Sicherheitswarnung für Apache Struts und Jackson beeinflusst. NPR-25628: Hotfix für CQ-4242891
* Der Punktprozess für E-Mail-Beginn funktioniert nicht. NPR-25253: Hotfix für CQ-4248518

**Enthaltene Feature Packs**

**Assets**

* Die [Integration mit Adobe Stock](/help/assets/aem-assets-adobe-stock.md) wurde hinzugefügt, damit Benutzer Adobe Stock-Assets direkt über AEM Benutzeroberfläche suchen, Vorschau, speichern und lizenzieren können. Weitere Informationen finden Sie unter [Verwenden von Adobe Stock-Assets mit AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html). NPR-15779: Hotfix für CQ-30857
* Unterstützung für dynamisches bedingtes Metaschema hinzugefügt. Weitere Informationen finden Sie unter [Kaskadieren von Metadaten](/help/assets/cascading-metadata.md). NPR-25189: Hotfix für CQ-4237413
* Option &quot;Asset-Download&quot;für Inhaltsfragmente aktiviert. Weitere Informationen finden Sie unter [Asset-Berichte](/help/assets/asset-reports.md). NPR-25186: Hotfix für CQ-4237410
* Möglichkeit zum Festlegen eines Metadaten-Schemas für Asset-Ordner. Weitere Informationen finden Sie unter [Ordnermetadaten-Schema](/help/assets/folder-metadata-schema.md) und beziehen Sie sich auf den [Konfigurationseinstellungen](#configuration-settings-required-for-npr) Beitrag AEM 6.4.2.0-Installation. NPR-21268: Hotfix für CQ-4221574

**Sites**

* Erlauben Sie die Bearbeitung eines Inhaltsfragments ohne Löschberechtigungen. Weitere Informationen finden Sie unter [Anpassen und Erweitern von Inhaltsfragmenten](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-delete.html). NPR-25793: Hotfix für CQ-4248750
* Inhaltsfragmente können jetzt kommentiert werden. Weitere Informationen finden Sie unter [Variations-Authoring-Fragmente](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-variations.html#annotating-a-content-fragment). NPR-25188: Hotfix für CQ-4235336
* Version: Vergleichen Sie Inhaltsfragmente nebeneinander. Weitere Informationen finden Sie unter [Verwalten von Inhaltsfragmenten](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-managing.html#comparing-fragment-versions). NPR-25187: Hotfix für CQ-4237412
* Verbesserungen im Bildeditor, die auf AEM 6.4.2.0 zurückportiert wurden. Weitere Informationen finden Sie unter [Bildeditor](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24467

**OSGI-Pakete und Inhaltspakete enthalten**

Liste der in AEM 6.4.2.0 enthaltenen OSGi-Bundles

[Datei laden](assets/6.4.2.0_bundle-list.txt)

Liste der in AEM 6.4.2.0 enthaltenen Inhaltspakete

[Datei laden](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

AEM 6.4.1.0 ist ein wichtiges Update, das Funktionen für Leistung, Stabilität, Sicherheit und wichtige Fehlerbehebungen und Erweiterungen umfasst, die seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht wurden.

AEM 6.4.1.0 kann auf AEM 6.4 GA installiert werden. Zu den wichtigsten Merkmalen des Service Packs gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.3 aktualisiert.
* Verbesserte intelligente Tags.
* Fehlerbehebungen in der Design-Auswahl, Tag-Auswahl (ändern Sie die Quell-VM und Zielgruppe-VM in Auto)
* Unterstützung für typeHint zum Speichern von Werten als Zeichenfolge hinzugefügt.
* Unterstützung für SMTP über TLS in Mail Service hinzugefügt.
* Proxy-Handling-Korrektur für HTTP-Forwarder in DMS7.
* Aktualisieren Sie auf /etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js Version 1.3.
* Fehlerbehebungen in DMHybrid Opt-OUT- und Opt-IN-Paketen.
* Korrekturen beim intelligenten Zuschneiden.
* OOTB-Konfigurationswerte wurden an den neuen Speicherort migriert ( von /etc zu /conf).
* Es wurden Profil für Farben zu den Kundeneinstellungen auf Versand-Servern hinzugefügt.
* Migration der Image-Server-Einstellungen von /etc —&amp;gt; /conf.
* Quellinhalt-Fragment zur Übersetzung hinzugefügt.
* ARIA-Unterstützung für Print und PrintDialog hinzugefügt.
* ARIA-Unterstützung zur E-Mail-Validierung hinzugefügt.
* Proaktive Backport für Fehlerbehebungen &quot;platform.clientlibs&quot;.
* Vermeidung der automatischen Ausführung von Skripten, wenn keine Eingabe für den expliziten dataType erfolgt (löst CVE-2015-9251 auf).

**Assets**

* Beim erneuten Öffnen der Seite mit den Asset-Eigenschaften wird der Dropdown-Wert für &quot;Kaskade&quot;leer angezeigt. NPR-23042: Hotfix für CQ-4238761
* Freigegebene Links auf der Seite &quot;mylinkshare&quot;und Links zur Seite sind für Benutzer ohne Administratorrechte NPR-23044 nicht verfügbar: Hotfix für CQ-4239004
* Um eine Null-Zeiger-Ausnahme im DAM Asset Update-Arbeitsablauf in 6.4.0 zu verhindern. NPR-24134: Hotfix für CQ-4244972
* Auf der veröffentlichten WCM-Seite werden Platzhaltersymbole für Hotspot angezeigt. CSS-Dateien fehlen mit 403-Fehler für OOTB-Viewer. NPR-23041: Hotfix für CQ-4233716
* (Detail-Ansicht) Die Funktion &quot;Weiter/Zurück&quot;hinterlässt eine DIV-Überlagerung im Bereich &quot;Vorschau für dynamische Darstellung&quot;, die den Zugriff auf den Viewer blockiert. NPR-23043: Hotfix für CQ-4238499
* Die CMYK-Bilddarstellung weist eine falsche Sättigung auf. NPR-23048: Hotfix für CQ-4235470
* XMP Metadaten-Extraktion von Scene7ListInfoProvider ist ressourcenintensiv. NPR-23754
* (dam-Versand) HTTP-Forwarder respektiert keine HTTP-Proxy-Einstellungen. NPR-24002: Hotfix für CQ-4244140

**Sites**

* Wenn wir die Seite umbenennen, während wir sie verschieben, ist die Bewegung der Seite erfolgreich, aber die Funktion zum Umbenennen funktioniert nicht. NPR-22923: Hotfix für CQ-4235907
* Fehler beim Veröffentlichen einer Live Copy-Seite, die auf eine Importer-Seite in Adobe Campaignen verweist. NPR-23053: Hotfix für CQ-4237164
* &quot;Verschieben/Umbenennen&quot;in der klassischen Benutzeroberfläche schlägt fehl und die Fehlermeldung &quot;Fehler beim Verschieben der Seite&quot;wird nicht umbenannt. NPR-23051: Hotfix für CQ-4235907
* Beim Wechsel von der Ansicht Spalteninhalt zur Ansicht Liste wird eine leere Seite und Trigger eine Null-Zeiger-Ausnahme für Seiten mit OffTime- und OnTime-Einstellung als leer gerendert. NPR-22968, NPR-23052: Hotfix für CQ-4238940

**Commerce**

* Fehlerbehebung beim Test von Kern-Hobbes (CQ/Commerce-Modul). Hotfix für CQ-4253494

**Schwachstelle**

* Die Salesforce-Integration ist anfällig für Server-seitige Anforderungsfälschung (SSRF, Server Side Request Forgery). NPR-24289: Hotfix für CQ-4245277
* Serverseitige Anforderungsfälschung (SSRF) und Cross-Site Scripting (XSS) in ReportingServicesProxyServlet. NPR-24657: Hotfix für CQ-4246880
* Site-übergreifende Skripterstellung (XSS): In Commerce Createcatalogwizard.html/content. NPR-24642: Hotfix für CQ-4237017
* Site-übergreifende Skripterstellung (XSS) in den Verknüpfungen zum Admin-UI-Projekt. NPR-23272: Hotfix für CQ-4241795

**WCM - Foundation-Komponenten**

* Das Öffnen der Designauswahl führt zu einer Null-Zeiger-Ausnahme. NPR-23047: Hotfix für CQ-4238736

**Benutzeroberfläche**

* (Coral3 Datepicker) Hinzufügen Unterstützung von typeHint zum Speichern von Werten als &quot;String&quot;. NPR-23398: Hotfix für Granite-21194
* Internationalisierungsübersetzungen funktionieren nicht auf der Sprachebene. NPR-22967, NPR-23046: Hotfix für Granite-21111
* Proaktiver Backport für granite.ui.commons-Fehlerbehebungen. NPR-23537
* Proaktiver Backport für granite.ui.content-Korrekturen. NPR-23535
* Proaktiver Backport für granite.ui.coralui-Korrekturen. NPR-23538
* Es können nicht mehrere Benutzer gleichzeitig aus der Gruppe entfernt werden. NPR-23846
* (OMEGA) Bericht &quot;Funktion&quot;nur auf Englisch. NPR-23989: Hotfix für Granite-21231
* (Design Importer) Beim Importieren einer Seite werden die CSS-Dateien &quot;js&quot;und &quot;css&quot;nicht importiert. NPR-25203: Hotfix für Granite-22236

**Integration**

* Ungeschlossener ResourceResolver in com.day.cq.analytics.sitecatalyst. NPR-22340: Hotfix für CQ-4236515
* TargetContentImpl verlangsamt AEM bei langwierigen Abfragen. NPR-22359: Hotfix für CQ-4236907
* Die Target-Engine (mbox.js, at.js) verwendet keine verwalteten URLs, und sie verwendet URLs mit Doppelpunkten, die bei bestimmten Bereitstellungen fehlschlagen können. NPR-22434: Hotfix für CQ-4237854
* Im Target-Modus können Autoren eine aus der Blueprint geerbte Komponente ändern, ohne die Vererbung abzubrechen. NPR-22865: Hotfix für CQ-4237907
* (Personalisierung) Symbole werden beim Wechsel zur Ansicht der Karte deformiert. NPR-23373, NPR-23374: Hotfix für CQ-4240018, CQ-4240019
* (Personalisierung) Audience Console zeigt keine nt:folder-Typen an. NPR-23375: Hotfix für CQ-4242293
* Wenn eine Komponente auf eine Veröffentlichungsinstanz ausgerichtet ist, wird das Flackern angezeigt, das das Standarderlebnis vor der Zielinstanz anzeigt. NPR-23415: Hotfix für CQ-4242038
* (Adobe IMS Console) Die Konfiguration des AccessTokenProvider OSGi-Dienstes wird nach dem Löschen erneut angezeigt. NPR-23520: Hotfix für CQ-4208250
* Die Replikation der Konfigurationsreferenzen mit der Zwischenordnerstruktur schlägt fehl. NPR-23485: Hotfix für CQ-4242751
* (Personalisierung) clientlib blockiert durch das Proxy-Servlet. NPR-23521: Hotfix für CQ-4240995
* (Adobe IMS Console) Registrierte Cloud-Lösungen werden im Konfigurationsassistenten nicht aufgenommen. NPR-23977: Hotfix für CQ-4244549
* Endlose Schleife beim Laden zielgerichteter Inhalte auf Seiten ohne HTML-Erweiterung. NPR-23522: Hotfix für CQ-4223600
* Aktivierung schlägt bei einer Seite mit Verweisen auf die Konfiguration des dynamischen Tag-Managements fehl. NPR-23485: Hotfix für CQ-4242751

**Plattform**

* (Klassische Benutzeroberfläche)(Touch-Benutzeroberfläche) Die Tag-Auswahl wird nicht angezeigt und gibt beim Versuch, über eine im Schema &quot;Asset-Suche&quot;vorhergesagte Tags nach Tags zu suchen, eine Ausnahme aus. NPR-23049: Hotfix für CQ-4239371
* (Klassische Benutzeroberfläche) Komponenten, die xtype=tags verwenden, geben null zurück und können nicht aus der eth-Liste von Tags ausgewählt werden. NPR-23050: Hotfix für CQ-4239937
* (Branding) In den Anmeldungsdialogfeldern wird Adobe Marketing Cloud anstelle von Adobe Experience Cloud erwähnt. NPR-23210: Hotfix für CQ-4237799
* Die Filteroption macht AEM nach der Aktualisierung von 6.3 auf 6.4 langsam. NPR-23260: Hotfix für CQ-4239847 (zu prüfen)
* Proaktiver Backport für Fehlerbehebungen &quot;granite.omnisearch.core&quot;. NPR-23536
* Proaktive Backport für Fehlerbehebungen &quot;platform.clientlibs&quot;. NPR-23569
* Cloud Service-Config-Vererbung ist beim Bearbeiten anderer Seiteneigenschaften fehlgeschlagen. NPR-23216: Hotfix für CQ-4239782
* STARTTLS-Unterstützung im Day CQ Mail Service aktiviert. NPR-23941: Hotfix für CQ-4240397

**Projekte**

* (Inhaltsfragment) Die Sprachkopie für eingebettete Assets wird nicht erstellt, während der englische Asset der Übersetzung hinzugefügt wird. Hotfix für CQ-4243477
* Das msft config-Dropdown zeigt config von /libs(6.4-Konfigurationen) anstelle von /etc(6.3-Konfigurationen) im Legacy-Modus an. Hotfix für CQ-4243475
* Automatische Förderung und Löschung von Übersetzungsstarts in Übersetzungsprojekten. Hotfix für CQ-4243474
* Inhaltsfragment in Sites, die nicht übersetzt werden. Hotfix für CQ-4243482, CQ-4243483, CQ-4245687
* Serverfehler beim Öffnen des Suchfilters für Übersetzungsaufträge. Hotfix für CQ-4236813
* Die Dropdown-Liste &quot;Berechtigungskonfiguration&quot;ist leer, auch wenn tif innerhalb von /conf/we-retail vorhanden ist. Hotfix für CQ-4236315
* Projekt-KPI öffnen: Leistungsbeeinträchtigung, wenn mehr Projekte erstellt werden. NPR-23840: Hotfix für CQ-4238392
* Workflow Starter kann den TypeHint-Wert von String nicht akzeptieren. NPR-23863: Hotfix für CQ-4238356

**Communities**

* Sicherheitslücken in Version 1.0 von Handlebars. NPR-23636: Hotfix für CQ-4243055
* Massengenehmigung für gekennzeichnete Nachrichten funktioniert nicht. NPR-23867: Hotfix für CQ-4243962
* Der Standardwert wird bei der Sortierschaltfläche in der Forumkomponente nicht angezeigt. NPR-23882: Hotfix für CQ-4243375
* Probleme mit dem Versand von Nachrichten von Community-Sites zu Gruppen. NPR-23935

**Arbeitsablauf**

* Der Day CQ Workflow E-Mail-Benachrichtigungsdienst Trigger eine E-Mail pro Mongo-Knoten für WorkflowComplete- und WorkflowAborted-Benachrichtigungen. NPR-22515: Hotfix für CQ-4238172
* Beim Ausführen des Arbeitsablaufs für DAM-Update-Assets wird eine NullPointerException ausgelöst. NPR-23010: Hotfix für Granite-21096
* Im Schritt Workflow-Prozess werden keine Skripten aus /etc/workflow/scripts angezeigt. NPR-23263: Hotfix für Granite-20775
* Workflow Dynamic Participant Step zeigt keine Skripten aus /apps/workflow/scripts an. NPR-23464: Hotfix für Granite-21276
* Workflow kann nach einmaliger Bearbeitung nicht mehr bearbeitet werden. NPR-23742: Hotfix für CQ-4238526
* (Klassische Benutzeroberfläche) Beim Bearbeiten der Workflow-Starter werden die Bedingungen ausgeblendet, sodass die Workflows ohne Bedingungen gestartet werden. NPR-23835: Hotfix für CQ-4239153
* Projekt-Posteingang: Beim Wechsel zur Kalenderinhalt-Ansicht werden die wichtigsten Inbox-Inhalte angezeigt. NPR-23947: Hotfix für CQ-4241236
* Die Payload-Details müssen im Bundle bereitgestellt werden, damit die HTL-Komponente den Wert in der Ansicht &quot;Liste&quot;anzeigen kann. NPR-23948: Hotfix für CQ-4240953
* Dialogfelddaten können nicht im Schritt &quot;Dialogbereitschaft&quot;gespeichert werden. NPR-23965: Hotfix für CQ-4234123
* (Touch UI) Beim Speichern eines Workflow-Modells ändert sich die Schaltfläche &quot;Synchronisieren&quot;in &quot;Synchronisiert&quot;, was zu einem Rechtschreibfehler führt. Hotfix für CQ-4244843
* Projekt-Posteingang: Beim Wechsel zur Kalenderinhalt-Ansicht werden die wichtigsten Inbox-Inhalte angezeigt. Hotfix für CQ-4244436
* Dialoge können nicht im Schritt &quot;Dialogteilnehmer&quot;ausgewählt werden. Hotfix für CQ-4244532
* Proaktiver Backport für Fehlerbehebungen &quot;granite.omnisearch.core&quot;. NPR-23536
* Problem in Mobile Workspace App 6.4 mit freigegebener Aufgabe. NPR-26383

**WCM - Übersetzung**

* (Referenz-Panel) Übersetzungsaufträge werden während der Projekterstellung nicht ausgeführt. Hotfix für CQ-4245327

**WCM - MSM**

* (MSM) Verbesserte Rollout-Leistung. Hotfix für CQ-4231488
* (MSM) Zeitlücke beim Ereignis-Listening zwischen tatsächlich stattfindendem Ereignis und dem Umgang mit Ereignissen. Hotfix für CQ-4227766

**Screens**

* Die Bildschirmseite schlägt fehl, weil Abhängigkeiten für screen-core-pkg:1.4.42 fehlerhaft sind. Hotfix für CQ-4245918

**Projekte - Übersetzung**

* (Inhaltsfragment) Die Sprachkopie für eingebettete Assets wird nicht erstellt, während der englische Asset der Übersetzung hinzugefügt wird. Hotfix für CQ-4243477
* Das msft config-Dropdown zeigt config von /libs(6.4 configs)anstelle von /etc(6.3 configs) im Legacy-Modus an. Hotfix für CQ-4243475
* Automatische Förderung und Löschung von Übersetzungsstarts in Übersetzungsprojekten. Hotfix für CQ-4243474
* Inhaltsfragment in Sites, die nicht übersetzt werden. Hotfix für CQ-4243482, CQ-4243483, CQ-4245687
* Serverfehler beim Öffnen des Suchfilters für Übersetzungsaufträge. Hotfix für CQ-4236813
* Die Dropdown-Liste &quot;Berechtigungskonfiguration&quot;ist leer, auch wenn tif innerhalb von /conf/we-retail vorhanden ist. Hotfix für CQ-4236315

**Verwaltung von Inhaltsfragmenten**

* Beim Löschen einer Komponente werden Protokolle mit Stapelspuren gefüllt. Hotfix für CQ-4242315

**DAM - Allgemeines**

* Beim Schließen der Detail-Ansicht eines Assets wird die falsche Suchergebnisseite angezeigt. Hotfix für CQ-4240960
* (Camera Raw) Die Bildanpassungsoption fehlt. Hotfix für CQ-4246121
* IndexOutOfBoundsException: OOTB Asset Modification-Bericht. Hotfix für CQ-4239744
* Entfernen Sie das Konfidenzergebnis aus der CSV-Datei des Berichts. Hotfix für CQ-4241491
* Link Share-E-Mail-Versand für Absender, die nicht &quot;admin&quot;sind, beschädigt. Hotfix für CQ-4240357
* Beheben von IT-Fehlern Hotfix für CQ-4249891

**DAM - Markenportal**

* Asset-Eigenschaften Liste nur 3 Eigenschaften auf der ersten Registerkarte, Rest alle Registerkarten aussehen leer. Hotfix für CQ-4242503
* Vorhersagen zu Dateityp und Dateigröße sind im veröffentlichten Suchformular nicht verfügbar. Hotfix für CQ-4242026
* Die Suche im Verzeichnis-Predicate sollte herausgefiltert werden/nicht in den Filtern angezeigt werden. Hotfix für CQ-4241386
* Die Standardsuche von sollte nach dem Rückgängigmachen der Veröffentlichung vorhanden sein. Hotfix für CQ-4241383, CQ-4241113
* Die Geste &quot;In Markenportal veröffentlichen&quot;funktioniert nicht für Bildvorgaben. Hotfix für CQ-4241074
* Die Veröffentlichung im Markenportal funktioniert nicht für Sammlungen. Hotfix für CQ-4241122, CQ-4246558

**DAM - DM-Client**

* Bei einem Upgrade auf 6.4 werden zuvor erstellte Profil zur Videokodierung entfernt. Hotfix für CQ-4244067
* Das Alt-Text-Attribut ist in der Dynamic Media-Komponente beschädigt. Hotfix für CQ-4244081
* (DMS7) Die Bearbeitung von Remote-Sets in AEM wird in Scene7 nicht überschrieben. Hotfix für CQ-4243430
* Verification of 6.4 SP1 build on DM Hybrid. Hotfix für CQ-4244623
* (DMS7-UA) Wenn Sie für ein veröffentlichtes Video-Asset auf die Schaltfläche &quot;Einbetten&quot;klicken, wird nichts angezeigt. Das Dialogfeld &quot;Einbetten&quot;wird voraussichtlich mit HTML-Code angezeigt. Hotfix für CQ-4245237
* (DM Hybrid) Beim Kopieren der URL für veröffentlichte Video-Assets oder gemischte Mediensets wird im URL-Dialogfeld &quot;`[object Object]`&quot;angezeigt. Hotfix für CQ-4245236, CQ-4245451
* (DMHybrid) Die Seite &quot;Details&quot;der Ansicht enthält nicht die Vorschau der Videoasset-Anzeige und gibt eine Fehlermeldung an die Konsole aus. Hotfix für CQ-4244320
* Automatische S7-Kodierung von We.Retail-Inhalten. Hotfix für CQ-4242253
* Vorab aktualisierte Video-Verarbeitungsvorgaben dürfen weder eine neue Video-Kodierungsvorgabe hinzugefügt noch die vorhandenen Kodierungsvorgaben bearbeitet werden. Hotfix für CQ-4240407
* Bildvorgaben vor der Aktualisierung werden auf der Seite &quot;Darstellungen&quot;als &quot;unveröffentlicht&quot;angezeigt und geben keine URL ab. Hotfix für CQ-4240406
* (CSS) Assets werden angezeigt - aber die verwendeten Viewer sind Standard und nicht die OOTB-Viewer. Hotfix für CQ-4239839
* Deaktivierte Aufräumschritte hängen manuelle Ausführung und Verwendung von privaten Korallenklassen. Hotfix für CQ-4239729
* Der Bild-Viewer erzeugt einen Fehler und zeigt nicht die richtige intelligente Beschneidung an. Hotfix für CQ-4237564
* Die ältere Vorgabe unter /etc scheint beschädigt zu sein und beim Speichern nicht an den Speicherort unter /conf migriert zu werden. Hotfix für CQ-4237416
* Regression in OOB VideoViewer 5.8.x - der Viewer erweitert iframe auf die rechte Seite, wodurch das Seitenlayout beschädigt wird. Hotfix für CQ-4235465
* (DMS7) URL und Schaltflächen zum Einbetten für Smart-Zuschneiden sind für Bilder aktiv, die noch nicht veröffentlicht wurden. Hotfix für CQ-4233696
* (DMHybrid) Funktion zum vorherigen Beschneiden/Drehen wiederherstellen. Hotfix für CQ-4239489
* Beim Anzeigen einer Videovorschau in der Ansicht der Karte wird die Wiedergabeschaltfläche nicht umgeschaltet, um anzuhalten. Hotfix für CQ-4238592
* Beim Durchführen einer Teilnahme-Aktualisierung wird die YouTube-Konfiguration nicht von ihrem alten Speicherort an den neuen Speicherort verschoben/kopiert. Hotfix für CQ-4238590
* DropZwei OTB-AVS-Videoverarbeitung-Profil werden unter Ordnereigenschaften aufgelistet und nur eines enthält definierte Kodierungen. Hotfix für CQ-4238096
* (DMS7) Smart Crop: Detail-Ansicht: Die URL-Schaltfläche heißt Schaltfläche &quot;Kopieren&quot;für Darstellungen. Hotfix für CQ-4237804
* Die Seite zur Auflistung der Viewer-Vorgaben bleibt auch nach dem Ausführen der Curl-Befehle leer. Hotfix für CQ-4243246
* Deaktivierte Aufräumschritte hängen manuelle Ausführung und Verwendung von privaten Korallenklassen. Hotfix für CQ-4239729
* Videoberichtdetails zeigen kein Video-Asset an. Hotfix für CQ-4246208

**DAM - DMServices**

* (DMS7) Cloud-Konfiguration: Neue Inhalte können nach der Aktualisierung auf SP1 nicht mit Scene7 synchronisiert werden. Hotfix für CQ-4244437
* (DMHybrid) Farbeinstellungen und Katalogeinstellungen werden nicht in einem debug_info=catalog-Aufruf registriert. Hotfix für CQ-4242346
* hinzufügen Sie die Profil auf den Kundeneinstellungen auf den Versand-Servern farblich an. Hotfix für CQ-4241818, CQ-4241819
* (DMHybrid) Nach 6.3 &amp;gt; 6.4-Aktualisierung, Katalogeinstellungen werden auf den falschen Knoten verschoben. Hotfix für CQ-4239974, CQ-4239975
* (DMHybrid) Push-ViewerPresets-Skript erstellt nicht die Knoten, die zum Ändern der Katalogeinstellungen erforderlich sind. Hotfix für CQ-4240076
* Wenn Sie die Dropdownliste &quot;Format&quot;verwenden und entweder PNG- oder JPG-Formate auswählen, wird die heruntergeladene Datei als übersättigt und dunkler als das ursprüngliche Asset angezeigt. Hotfix für CQ-4240073
* (DMS7) Entfernen Sie die MIME-Typzuordnung: image_x-eps. Hotfix für CQ-4240394
* (DMS7) Upload-Parameter für den Hintergrund des Aussparens übergeben nicht die Datei &quot;ipsApiService.log&quot;und funktionieren daher nicht. Hotfix für CQ-4240686
* Beim Aktualisieren von Bildverarbeitungs-Profilen, die in einer Instanz von 6.3 auf 6.4 erstellt wurden, wird die Eigenschaft &quot;Beschneidungstyp&quot;umgangen. Hotfix für CQ-4237739
* (Dynamic Media) Das regelmäßige Hochladen von Assets außerhalb des Ordners &quot;smartcut&quot;schlägt fehl. Hotfix für CQ-4237670
* Passen Sie den Fallback-Code für das Profil &quot;Adaptive Videokodierung&quot;an &quot;Adaptive_Video_Encoding&quot;an. Hotfix für CQ-4237666
* EmbedXMP-Daten werden für den Ptiff-Generierungsprozess immer auf „aktiv“ gesetzt. Hotfix für CQ-4234498
* Die CMYK-Bilddarstellung weist eine falsche Sättigung auf. Hotfix für CQ-4235470
* Image-Server-Einstellungen werden nicht auf Versand repliziert, während die Replizierungsprotokolle sie als erfolgreich markieren. Hotfix für CQ-4239480, CQ-4239046
* (DMS7) Sätze können nicht mit alten/neuen Verweisen auf die Cloud-Konfiguration erstellt werden. Hotfix für CQ-4238078
* Der Arbeitsablaufschritt von Scene7 liest nur Scene7 im Namen und in der Beschreibung, aber nicht den Workflow-Schritt im DAM-Aktualisierungsarbeitsablauf. Hotfix für CQ-4237865

**DAM - Intelligente Tags**

* Vorgestellt [Erweiterte Smart Tags](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951

**Formulare**

AEM Forms-Fehlerbehebungen werden über Add-on-Pakete und andere mit der Version gelieferte Patch-Installationsprogramme bereitgestellt. Weitere Informationen finden Sie unter AEM Forms-Versionen.

Die wichtigsten Highlights für AEM Forms sind:

* AEM Forms stellt die Funktion [Transaktionsberichte](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) vor, um Transaktionen wie gesendete Formulare, verarbeitete Dokumente und gerenderte Dokumente in Ihrer AEM Forms-Bereitstellung zu verfolgen und zu zählen. Es bietet Einblicke in die Produktnutzung und hilft Geschäftsbenutzern, digitale Verarbeitungsvolumina zu verstehen.
* PDF/UA-Unterstützung für XML-Formulare aktiviert.
* allowProxy = true für clientlib **aemfd.ccm.Kanal.contentpage** hinzugefügt
* Der Code wurde aktualisiert, um eine erweiterte Titelsuche mit &quot;enthält&quot;statt mit &quot;gleich&quot;zu ermöglichen.
* Aktualisieren Sie auf die neue Version von Node Package Manager (NPM) auf dem Continuous Integration Machine.

**Forms-Add-on-Paket**

**Backend-Integration**

* Ein Fehler wird generiert, wenn einem optionalen Feld null als Wert zugewiesen wird. NPR-24397
* Der WSDL-Aufruf schlägt fehl, wenn das Element einen anderen Namensraum als den globalen Namensraum hat. NPR-24281
* (FDM WSDL) DermisException: Ausgenommene Daten zur Liste im Falle eines Eigenschaftstyp-Arrays. NPR-24265
* (FDM WSDL) DermisException: java.lang.Exception: createSOAPParam: Ungültige Parameter. NPR-24264
* (FDM Client SDK) Tests von Pre-/Post-Vorprozessor- und benutzerdefinierten Übermittlungsaktionen können nicht durchgeführt werden. Hotfix für CQ-4238469
* Fehlerbehebungen bei Javadoc-Problemen in Dermis. Hotfix für CQ-4244250
* Verbesserte Eingabe in WSDL (Web Services Description Language). Hotfix für CQ-4244133
* Grundlegende Authentifizierungstests für WSDL führen zu unterschiedlichen Fehlern für dieselbe Konfiguration in AEM 6.3 und AEM 6.4. Hotfix für CQ-4244132
* Anfrage zur Einbeziehung von ValueUtil in client-sdk und javadocs. Hotfix für CQ-4242803
* (FDM Cloud-Konfiguration) SOAP-basierte Authentifizierung kann nicht aus der Cloud-Konfiguration konfiguriert werden. Hotfix für CQ-4238462
* Dermis - Hinzufügen Pakete in Javadocs fehlen. Hotfix für CQ-4242815
* WSDLInvokerParams wird in Forms Hinzufügen-On Client SDK aufgenommen. NPR-23381: Hotfix für CQ-4240233

**Adaptive Formulare**

* Dokument (IC)-Darstellung sollte als Transaktion mit dem Transaktionsaufzeichnungsdienst protokolliert werden. Hotfix für CQ-4245333
* Beim Ausführen von UAT5 fehlt in der im Prüfstadium erstellten PDF ein Eintrag. Hotfix für CQ-4243184
* Testen Sie die Groß-/Kleinschreibung für guideContext. Hotfix für CQ-4242924
* Beim Ausführen von UAT3 auf dem neuesten aktualisierten Server fehlt das Feld Testversand-Typ. Hotfix für CQ-4243120
* Auf dem aktualisierten Server fehlen im gesendeten Formular die Werte &quot;Bundesland/-staat/-region&quot;und &quot;Land&quot;, die auf dem Server vor der Aktualisierung vorhanden waren. Hotfix für CQ-4241444
* (ExpressionEditor) Fehler beim Navigieren zur Phase Überprüfen während der Formularübermittlung. Hotfix für CQ-4241384
* Werte fehlen im Überprüfungsstadium auf dem Server vor der Aktualisierung und dem aktualisierten Server für das gesendete Formular. Hotfix für CQ-4241896
* Die Schaltfläche zum Beenden und Speichern am unteren Rand der Seite funktioniert nicht. Hotfix für CQ-4240112
* Die Kontaktnummer fehlt im aktualisierten Setup. Hotfix für CQ-4239870
* Unter &quot;`ACTION TAKEN`&quot;auf der Registerkarte &quot;Dispute Type&quot;, &quot;Additional Dokumente to support my claim&quot;enthält das Feld Testversand Type Saved&quot;. Hotfix für CQ-4239873
* Fehler &quot;Fehler in getDataAPI&quot;im &quot;verifyPdf&quot;-Stadium. Hotfix für CQ-4239865
* Fehler in Migrationsprotokollen für Autor- und Veröffentlichungsinstanz. Hotfix für CQ-4239365
* Fehler in Migrationsprotokollen für Autor- und Veröffentlichungsinstanz. Hotfix für CQ-4239635
* Deserialisierungsfehler wie &quot;Deserialisierung für die Klasse sun.util.calendar.ZoneInfo&quot;in Fehlerprotokollen nach der Übermittlung eines adaptiven Formulars. Hotfix für CQ-4240419
* Das Statusfeld wird nicht in der Mobile Forms-Darstellung ausgefüllt. Hotfix für CQ-4240597
* Entfernen Sie die Referenzverwendung von Komponenten in Vorlagen aus der Liste gegen Muster. Hotfix für CQ-4239217
* HTML5 Numeric Box set as a Float or Decimal gibt in verschiedenen Browsern unterschiedliche Prüfergebnisse. NPR-23528: Hotfix für CQ-4244097
* (Bild-Upload) Bild wird nicht in der DOR-Vorschau angezeigt. Hotfix für CQ-4243178
* Der JEE-Server gibt beim Senden des adaptiven Formulars mit &quot;E-Mail-PDF&quot;und &quot;Anlagen einschließen&quot;einen Fehler aus. Hotfix für CQ-4239894
* Das Diagramm wird zur Laufzeit nicht mit Tabelle/Bedienfeld dargestellt. Hotfix für CQ-4240010
* Die Übermittlung des adaptiven Formulars funktioniert nicht und es werden keine Änderungen bei der Transaktionszählung aufgrund eines Fehlers bei der Übermittlung vorgenommen. Hotfix für CQ-4246125
* (Bildauswahl) Dokument der Datensatzoptionen ist nicht sichtbar. Hotfix für CQ-4236976
* Die Benutzeroberfläche des Vorlageneditors ist nicht stabil. Hotfix für CQ-4241497
* AFs werden nicht über die Registerkarte &quot;Assets&quot;des Seitenbedienfelds angezeigt, während die Option &quot;Durchsuchen&quot;für AEM Dialogfeld für die Eigenschaft der Formularkomponente angezeigt wird. Hotfix für CQ-4236751
* Die für die Formularkonvertierung generierte Workflow-ID sollte im erstellten adaptiven Formular verfügbar sein. Hotfix für CQ-4240014
* Vorlage zum Erstellen einer Seite in Sites bei Direct Upgrade kann nicht ausgewählt werden: LiveCycle auf 6.4-Server. Hotfix für CQ-4241300

**Assembler-Dienst**

* Transaktionsprotokolliereinrichtung in Assembler Services. Hotfix für CQ-4245018, CQ-4245017, CQ-4245016.
* Die Transaktion wird nicht gemeldet, wenn die PDF/A-Konvertierung mit DDX erfolgt. Hotfix für CQ-4246039

**Forms Manager**

* FM-Schaltflächen-Liste ERSTELLEN, um alphabetisch sortiert zu werden. Hotfix für CQ-4242307

**Form Portal**

* Entwürfe, die auf dem Server vor der Aktualisierung gespeichert wurden, werden auf dem aktualisierten Server nicht korrekt geöffnet. Hotfix für CQ-4243303
* Version auf 7.1 für das adobe-formsmanager-core-Modul aktualisieren. Hotfix für CQ-4245753
* Entwürfe, die auf dem Server vor der Aktualisierung gespeichert wurden, werden auf dem aktualisierten Server nicht korrekt geöffnet. Hotfix für CQ-4243303
* Anlagenszenarien funktionieren beim Ersetzen/Hinzufügen/Entfernen von Anlagen in einer neuen Instanz/in derselben Entwurfsinstanz nicht mehr. Hotfix für CQ-4243165
* Die Anzahl der bei der Abfrage der Datenbank abgerufenen Entwürfe ist mehr als die Anzahl der im Portal vorhandenen Entwürfe. Hotfix für CQ-4241489
* Forms, das auf einem Server vor der Aktualisierung gesendet wurde, ist auf dem aktualisierten Server nicht vorhanden. Hotfix für CQ-4241490
* Das in der Benutzeroberfläche auf der Registerkarte &quot;Übermittlungen&quot;angezeigte Formular befindet sich trotz erfolgreicher Übermittlungsmeldung im Status &quot;Nicht übermittelt&quot;. Hotfix für CQ-4241487
* Der guideContext sollte durch Deep Copy der Felder gebildet werden, da guideContext customPropertyMap enthält, die selbst ein Objekt ist. Hotfix für CQ-4240126
* Fehler beim Versuch, ein Formular zu speichern. Hotfix für CQ-4240763
* Der Eintrag für gespeicherte und gesendete Formulare wird in crx/de ausgefüllt, obwohl die DB-Konfiguration in Forms Portal Draft and Submission Configuration angegeben wurde. Hotfix für CQ-4240726
* (Search &amp; Lister) Der feste Wert für erweiterte Suchbegriffe sollte &quot;enthalten&quot;und nicht &quot;gleich&quot;funktionieren. Hotfix für CQ-4245499

**Forms**

* Das Datumsfeld überschneidet sich in Mobile Forms. Hotfix für CQ-4242256
* Die Formularübermittlung für Mobile Forms sollte als Transaktion mit dem Transaktionsaufzeichnungsdienst protokolliert werden. Hotfix für CQ-4246166
* Die Formularübermittlung in FormSet sollte als Transaktion mit dem Transaktionsaufzeichnungsdienst protokolliert werden. Hotfix für CQ-4246165

**AEM Forms-App**

* (Windows-App) Das Formular kann nicht wiedergegeben werden. Hotfix für CQ-4238005

**Workflow OSGI**

* Transaktionsprotokolliereinrichtung in der Aufgabe Workflow-Zuweisung. Hotfix für CQ-4244440
* (FDM-Schritt) Werte aus Workflow-Metadaten können nicht verwendet werden, wenn ein Zuweisungsschritt zwischen dem Prozessschritt und dem FDM-Schritt eingefügt wird. Hotfix für CQ-4241472
* Die Delegation der Zuweisung von Aufgabe funktioniert nicht in Forms Integration in OSGI Workflows. NPR-23709: Hotfix für CQ-4243700
* (Workflow-Modell-Editor) Einige Workflow-Modelle können nicht über den ClassicUI WF-Modelleditor bearbeitet werden. Hotfix für CQ-4241151

**MultiChannel-Dokument**

* Das Datumsfeld in der Vorlage überschneidet sich mit dem Teilformular im IC-Authoring. Hotfix für CQ-4240110
* Der Header sollte nicht gelöscht oder im IC Web Kanal Authoring nach oben und unten verschoben werden dürfen. Hotfix für CQ-4243358
* (IC Editor) Die Standardzeilen für Tabellenkomponenten werden auf 1 gesetzt. Hotfix für CQ-4244848
* Zielgruppen-Bereich, damit er auch dann sichtbar bleibt, wenn der Inhalt gezogen und abgelegt wurde. Hotfix für CQ-4244534
* Web Kanal erkennt keinen Tabulatorraum in Text Dokument Fragments. Hotfix für CQ-4244481
* (Print Kanal) Die Darstellung des Dokuments (IC) sollte als Transaktion mit dem Transaktionsaufzeichnungsdienst protokolliert werden. Hotfix für CQ-4245335
* (Web Kanal) Die Darstellung des Dokuments (IC) sollte als Transaktion mit dem Transaktionsaufzeichnungsdienst protokolliert werden. Hotfix für CQ-4245334
* Die Suche nach dem Dokument-Container oder der Datenmodellbaum muss mit der Suche nach dem Asset-Filter vereinheitlicht werden. Hotfix für CQ-4242305
* (Dokument Fragment) Die Einzug-Eigenschaft zieht den Text um, wie viel Einheiten nicht verstanden werden können. Hotfix für CQ-4241082, CQ-4240643
* (IC-Editor) Das Symbol &quot;Fragment bearbeiten&quot;auf der Kachel des Dokument-Fragments, die unter der Registerkarte &quot;Assets&quot;aufgeführt ist, ist nicht einfach zu erkennen und zu verstehen. Hotfix für CQ-4241047
* Anonymen Zugriff auf die IC Anonymous-Client-Bibliothek zulassen, auf die nicht zugegriffen werden kann. Hotfix für CQ-4245588
* (Web-Kanal) Daten werden in keiner der Tabellen in der Web-Vorschau aufgelöst und als leer angezeigt. Hotfix für CQ-4244476
* Tabellenüberschriften werden bei der automatischen Generierung als Variablen im Web Kanal angezeigt. Hotfix für CQ-4244242
* (IC-Editor) Die Inhaltsgröße eines in einer IC verwendeten Dokument-Fragments sollte automatisch an die Zielgruppe angepasst werden. Hotfix für CQ-4244094
* Der im mittleren oberen Bereich angezeigte Kanal muss entweder für den IC-Titel für WEB/PRINT konsistent sein. Hotfix für CQ-4242498
* Texteditor Das Datenobjektbedienfeld sollte nur Entitäten der obersten Ebene Liste, Hotfix für CQ-4244121
* Beim Hinzufügen einer neuen Komponente im Editor wird kein Standardname zugewiesen. Hotfix für CQ-4244691
* Hinzufügen der Colspan-Konfiguration in allen Web-Kanal-Komponenten. Hotfix für CQ-4244946
* Die Eigenschaft &quot;Tabellenbreite des Layout-Fragments&quot;wird im Kanal &quot;Brief&quot;oder &quot;Drucken der Kundenkommunikation&quot;nicht zurückgesetzt und berücksichtigt. Hotfix für CQ-4241574

**Korrespondenzverwaltung**

* Beschriftungen, die aus der Briefvorlage entfernt wurden, nachdem ein Textelement bearbeitet wurde, das Platzhalter enthält. NPR-24196
* Wenn die XDP-Datei hochgeladen und als Layout für Briefvorlagen verwendet wird, können die Vorlagen nicht Vorschau oder bearbeitet werden. NPR-24143: Hotfix für CQ-4244407
* Die Zuweisungsauswahl ist im Fragment &quot;Liste&quot;standardmäßig ausgewählt. Hotfix für CQ-4240097
* Bedingungseditor - Die Auswertung mehrerer Ergebnisse sollte standardmäßig aktiviert sein. Hotfix für CQ-4240096
* Wenn das Bild aus der Liste gelöscht wird, wird es weiterhin in der Vorschau angezeigt. Hotfix für CQ-4239909
* Der Regelsatz im Bedingungsmodul wird für alle Module als &quot;Standard&quot;festgelegt. Hotfix für CQ-4239878
* Die Erstellung des Datenwörterbuchs schlägt mit dem Fehler &quot;Unbekannte JCR-Ausnahme&quot;fehl. Hotfix für CQ-4244122
* Lücken in 6.3 Content JavaDocs. Hotfix für CQ-4213586

**Forms JEE-Installationsprogramm**

**Core**

* (HTML Workspace) Für Anwendungen mit Klammern-Symbol im Namen fehlen Verfolgungsdetails. NPR-23402

**PDFG-Dienst**

* Transaktionsprotokolliereinrichtung bei PDFG-Diensten. Hotfix für CQ-4244951, CQ-4244586
* Reduzierung von PDFs durch selektives Aufheben der Einbettung von Schriftarten über einen einzelnen API-Aufruf. NPR-23287
* Aktualisierungsfehler bei PDFG-Konfigurationen bei AEM Aktualisierung. Hotfix für CQ-4241176
* Transaktionsprotokolliereinrichtung im PDFUtility Service. Hotfix für CQ-4245014

**Prozessverwaltung**

* (HTML Workspace) Prozessstartpunkte werden nicht in alphanumerischer Reihenfolge sortiert. Hotfix für CQ-4239629
* (HTML Workspace) Bereiten Sie den Datenaufruf vor, der zweimal auftaucht, wenn der Entwurf zum ersten Mal geöffnet wird. Hotfix für CQ-4243280
* (HTML Workspace) Der Prozess &quot;Vorbereiten von Daten&quot;wird beim Schließen eines Formulars ausgelöst. Hotfix für CQ-4239456
* Der Arbeitsbereich hängt beim Durchlaufen zwischen zwei Aufgaben. Hotfix für CQ-4237125

**Workbench**

* Der Vorgang zum Verwalten des Action Profil Prepare-Datenprozesses schlägt fehl, wenn die standardmäßige Renderprozesskonfiguration auf HTML eingestellt ist. Hotfix für CQ-4244292

**Forms Designer**

* Fügt XML-Formularen, die über Designer und den Output Service generiert wurden, PDF/UA-Unterstützung hinzu. NPR-23022
* Inline-Hyperlinks, die in Designer definiert sind, werden weder mit Tags versehen, noch haben sie alternativen Text, wenn sie als PDF in Designer gespeichert werden. NPR-23023

**Enthaltene Feature Packs**

**Assets**

* Die Funktion für erweiterte intelligente Tags wurde hinzugefügt. Weitere Informationen finden Sie unter [Erweiterte Smart-Tags](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951: Hotfix für CQ-4234883
* Einführung in AEM Assets-Verweise in InDesign. Weitere Informationen finden Sie unter [AEM Assets-Verweise in InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**Sites**

* (Seiten-Authoring) Verbesserungen am Bildeditor. Weitere Informationen finden Sie unter [Bildeditor](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24267: Hotfix für CQ-4245502

**OSGI-Bundles und Inhaltspakete sind enthalten**

Der folgende Text Dokumente die Liste von OSGI-Bundles und Inhaltspaketen, die in der CFP enthalten sind.

Liste der in AEM 6.4.1.0 enthaltenen OSGi-Bundles

[Datei laden](assets/6_4_1_0_bundle-list.txt)

Liste der in AEM 6.4.1.0 enthaltenen Inhaltspakete

[Datei laden](assets/6_4_1_0_content-package-list.txt)

### Installieren Sie 6.4.8.0 {#install}

#### Einrichtungsvoraussetzungen {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Für Kunden mit Feature Packs, die in AEM 6.4 installiert sind: Optionale Feature Packs, die von Adobe bereitgestellt werden, weisen Abhängigkeiten von der Release-Version und dem Service Pack auf. Wenn Sie ein Feature Pack installiert haben, wenden Sie sich an das AEM-Kundendienstteam, um die Kompatibilität dieses Feature Packs mit diesem Service Pack für AEM 6.4 zu bestätigen.

* AEM 6.4.8.0 erfordert AEM 6.4. Weitere Informationen finden Sie unter [Upgrade-Dokumentation](../sites-deploying/upgrade.md).
* Der Service Pack-Download steht unter [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) zum Download bereit.
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.4.8.0 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Erstellen Sie eine Momentaufnahme oder ein neues Backup Ihrer AEM-Instanz, bevor Sie das Service Pack installieren.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz gerade von einer früheren Version aktualisiert wurde). Dennoch wird dies allgemein empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!NOTE]
>
>Adobe rät davon ab, das AEM 6.4.8.0-Paket zu entfernen oder zu deinstallieren.

### Installieren Sie das Service Pack über Package Manager {#install-the-service-pack-via-package-share}

Führen Sie folgende Schritte aus, um das Service Pack in einer vorhandenen AEM 6.4-Instanz zu installieren:

1. Laden Sie das Paket von der Softwareverteilung herunter.

1. Melden Sie sich in AEM bei Package Manager an und fügen Sie das heruntergeladene AEM 6.4.8.0-Paket hinzu. Wählen Sie das hochgeladene Paket aus und klicken Sie auf **[!UICONTROL Install]**.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird in einigen Fällen während der Installation von 6.4.8.0 frühzeitig beendet.**
>
>Es wird daher empfohlen, auf die Stabilisierung der Fehlerprotokolle zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles warten, bevor sichergestellt wird, dass die Installation erfolgreich ist. In der Regel trifft dies auf Safari zu, kann aber mitunter auch auf allen anderen Browsern der Fall sein.

### Automatische Installation  {#auto-installation}

Es gibt zwei Möglichkeiten, AEM 6.4.8.0 automatisch in einer laufenden Instanz zu installieren:

A. Platzieren Sie das Paket in ..Ordner */crx-quickstart/install*, während der Server läuft. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](https://helpx.adobe.com/de/experience-manager/aem-previous-versions.html) - stellen Sie sicher, dass Sie `cmd=install&recursive=true` verwenden - damit das verschachtelte Paket installiert wird.

>[!NOTE]
>
>AEM 6.4.8.0 unterstützt keine Bootstrap-Installation.

### Bestätigen der Installation {#validate-install}

1. Auf der Seite &quot;Produktinformationen&quot;(*/system/console/production *) sollte nun die aktualisierte Versionszeichenfolge &quot;Adobe Experience Manager, Version 6.4.8.0&quot;unter &quot;Installierte Produkte&quot;angezeigt werden.
1. Alle OSGI-Bundles sind in der OSGI-Konsole entweder AKTIV oder FRAGMENT. (Verwenden Sie die Webkonsole: /system/console/bundles.)
1. Das OSGI-Bundle org.apache.jackrabbit.oak-core ist auf Version 1.8.17 oder höher (Web-Konsole verwenden: /system/console/bundles).

Informationen zum Bestimmen der zertifizierten Plattform für die Ausführung mit dieser Version von AEM Sites und Assets finden Sie unter [Technische Anforderungen](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Bei erfolgreicher Installation des Pakets wird eine >Informationsmeldung angezeigt, die angibt, dass das Paket content >erfolgreich installiert wurde, z. B. **&quot;Content Package AEM-6.4-Service-Pack-7 erfolgreich installiert wurde&quot;**.

### Dynamic Media-Viewer aktualisieren (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM 6.4.8.0 enthält eine neue Version von Dynamic Media-Viewern (5.10.1), mit der auf der Seite "Bildvorgabe"nach Duplikat gesucht werden kann. Dynamic Media-Kunden wird empfohlen, den folgenden Befehl auszuführen, um die standardmäßigen Viewer-Vorgaben in den aktuellen Zustand zu bringen.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

, der neue Viewer-Vorgaben in /conf kopieren wird.

### Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

#### Installieren des AEM Forms-Add-ons {#installaemformsaddon}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in AEM Forms werden über ein separates Add-on-Paket bereitgestellt.

>[!NOTE]
>
>AEM 6.4.8.0 enthält eine neue Version des [AEM Forms-Kompatibilitätspakets](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/compatpack/AEM-FORMS-6.4.7.0-COMPAT). Wenn Sie eine ältere Version von AEM Forms Compatibility Package verwenden und auf AEM 6.4.8.0 aktualisieren, installieren Sie die neueste Version des AEM Forms-Kompatibilitätspakets nach der Installation des Forms Hinzufügen-On-Pakets.

1. Stellen Sie sicher, dass Sie das AEM Service Pack installiert haben.
1. Laden Sie das entsprechende Add-On-Paket für Formulare herunter, das unter [AEM Forms-Versionen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) für Ihr Betriebssystem aufgelistet ist.
1. Installieren Sie das Add-On-Paket für Formulare, wie unter [Installieren von Add-On-Paketen für AEM Formulare](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package) beschrieben.

### Installieren des AEM Forms JEE-Installationsprogramms {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in AEM Forms JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für AEM Forms JEE und zur Konfiguration nach der Bereitstellung finden Sie unter [AEM Forms JEE-Patch-Installationsprogramm 0015](https://helpx.adobe.com/de/aem-forms/quick-fixes/6-4/jee-patch-0015.html).

#### Für NPR-21268 erforderliche Konfigurationseinstellungen {#configuration-settings-required-for-npr}

Wenn Sie die klassische (alte) Benutzeroberfläche verwenden und Metadatenvorlagen verwendet haben, führen Sie die Schritte aus, um das JMX-Skript auszuführen, um diese beizubehalten -

1. Wechseln Sie zu /system/console/jmx.
1. Klicken Sie auf &quot;Metadatenvorlagen migrieren&quot;.
1. Klicken Sie auf &quot;migrateMetadataTemplatesAtPath&quot;und geben Sie den Ordnerpfad ein, unter dem die Metadatenvorlagen erhalten bleiben sollen.

#### Für NPR-24536 erforderliche Konfigurationseinstellungen {#configuration-settings-required-for-npr-1}

Die Anzahl freigegebener Warteschlangen wird für andere Benutzer nicht standardmäßig aktualisiert, wenn ein Benutzer eine Aufgabe beantragt. Dafür haben wir eine neue Eigenschaft eingeführt. Gehen Sie wie folgt vor, um diese Eigenschaft in Ihrer AEM zu konfigurieren:

1. Gehen Sie zu Admin-Benutzeroberfläche -> Dienste -> Arbeitsbereich -> Globale Verwaltung.
1. Globale Einstellungen exportieren.
1. Fügen Sie in der heruntergeladenen XML-Datei den Tag &lt;client_tasksPollingInterval>10&lt;/client_tasksPollingInterval> hier ist 10 der Beispielwert in Sekunden. Sie können sie entsprechend ändern.
1. Speichern Sie die Datei.
1. Gehen Sie zurück zur Admin-Benutzeroberfläche -> Dienste -> Arbeitsbereich -> Globale Verwaltung.
1. Importieren Sie die XML-Datei im Abschnitt &quot;Globale Einstellungen importieren&quot;.
1. Sie können sich jetzt vom System abmelden und sich erneut anmelden.
1. Die Anzahl der Beginn für freigegebene Warteschlangen, die für andere Benutzer im Arbeitsbereich aktualisiert werden.
1. Um die Abfrage zu deaktivieren, ändern Sie den Wert in 0 und importieren Sie die XML-Datei erneut.

### Uber Jar {#uber-jar}

Die Uber-Jar für AEM 6.4.8.0 ist im [Adobe Public Maven Repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/) verfügbar.

Um Uber Jar in einem Maven-Projekt zu verwenden, lesen Sie den Artikel [Wie Sie Uber jar](../sites-developing/ht-projects-maven.md) verwenden und fügen Sie die folgende Abhängigkeit in Ihr Projekt-POM ein:

```shell
<dependency>
      <code>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

### Entfernte/veraltete Funktionen {#removed-deprecated-features}

Dieser Abschnitt listet Funktionen und Fähigkeiten auf, die aus AEM 6.4 entfernt oder veraltet sind.

| Bereich | Funktion | Ersatz | Version |
|---|---|---|---|
| Assets | Tag-Aktion für Teilassets verwalten | Kein Ersatz vorhanden. | AEM 6.4.2.0 |
| Assets und Adobe Creative Cloud-Integration | [Die ](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) Freigabe von AEM an Creative Cloud-Ordner wurde in AEM 6.2 eingeführt, um kreativen Benutzern Zugriff auf Assets aus AEM zu gewähren. Eine neue Funktion der Creative Cloud-Anwendung, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus.  Adobe wird die Ordnerfreigabe nicht weiter verbessern. Während die Funktion in AEM enthalten ist, wird Kunden dringend empfohlen, den Ersatz zu verwenden. | Adobe Asset Link oder Desktop-App. Weitere Informationen finden Sie im Artikel zur [AEM Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

### Bekannte Probleme {#known-issues}

* Die folgenden Fehler und Warnungen werden möglicherweise während der Installation angezeigt:

   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Timeout wartet auf reg change, um unregistered abzuschließen.
   * `com.adobe.granite.maintenance.impl.TaskScheduler` Keine Wartungsfenster unter granite/operations/maintenance gefunden
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`: Die unbindAmendment-Methode hat eine Ausnahme ausgelöst (java.lang.IllegalStateException: Dienst ist bereits nicht registriert).
Diese Fehler erfordern keine Aktion, da sie Ihre AEM nicht beeinflussen.

### Behobene Probleme {#resolved-issues}

**AEM 6.4.4.0**

* Beim Importieren/Exportieren von Metadaten wird kein Ressourcenfehler festgestellt. CQ-4253263
* Bildkomponenten und Seiteneigenschaften können nach Anwendung von 6.4.3.0 über 6.4.2.0 nicht bearbeitet werden. CQ-4260316 &amp; CQ-4260441
So umgehen Sie dieses Problem:
   * Zu Package Manager wechseln
   * Installieren Sie das Paket &quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot; neu.
   * Kompilieren Sie alle JSPs `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` ODER starten Sie die Instanz neu.

### OSGi-Bundles und Inhaltspakete sind enthalten {#osgi-bundles-and-content-packages-included}

Die folgenden Dokumente Liste der OSGi-Pakete und Content Packages in AEM 6.4.8.0.

Liste der in AEM 6.4.8.0 enthaltenen OSGi-Bundles

[Datei laden](assets/6.4.8.0_osgi_bundles.txt)

Liste der in AEM 6.4.8.0 enthaltenen Inhaltspakete

[Datei laden](assets/6.4.8.0_content_packages.txt)

### Hilfreiche Ressourcen {#helpful-resources}

* [Versionshinweise zu AEM 6.4](../release-notes/release-notes.md)
* [AEM-Produktseite](https://www.adobe.com/solutions/web-experience-management.html)
* [Dokumentation zu AEM 6.4](https://helpx.adobe.com/de/support/experience-manager/6-4.html)
* Abonnieren Sie die Produktaktualisierungen mit der Priorität &quot;Adobe&quot;](https://www.adobe.com/subscription/priority-product-update.html)[

### Eingeschränkte Sites {#restricted-sites-new}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/).
* Produktupdates, Patches und Pakete für zusätzliche Funktionen bei [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Kundenservice per Admin Console](https://adminconsole.adobe.com/). Weitere Informationen finden Sie unter [Erlebnis des Kundensupports für neue Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
