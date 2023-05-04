---
title: Versionshinweise zum AEM 6.4 Service Pack
seo-title: AEM 6.4 Service Pack Release Notes
description: Spezifische Versionshinweise für Adobe Experience Manager 6.4 Service Packs.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Service Packs.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
exl-id: d0da9390-2167-47ee-82fd-8c81d8d68a3e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '21553'
ht-degree: 25%

---

# Versionshinweise zum AEM 6.4 Service Pack {#aem-service-pack-release-notes}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Versionshinweise {#release-information}

| Produkte | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.0 |
| Typ | Service Pack-Version |
| Datum | 5. März 2020 |
| Download-URL | AEM 6.4.8.0 on [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## Was ist in AEM 6.4.8.0 enthalten? {#what-s-included-in-aem}

AEM 6.4.8.0 ist ein wichtiges Update, das neue Funktionen, wichtige von Kunden angeforderte Verbesserungen der Leistung, Stabilität und Sicherheit sowie Verbesserungen enthält, die seit der allgemeinen Verfügbarkeit von AEM 6.4 in veröffentlicht wurden. **April 2018.**

Es ist auch kumulativ, was bedeutet, dass 6.4.8.0 alle AEM 6.4 Service Packs enthält, die zuvor veröffentlicht wurden.

Die wichtigsten Highlights dieser Service Pack-Version sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.20 aktualisiert.

* Die Wortumbruchfunktion wird für japanische Websites in WCM-RTE unterstützt.

* Die Verarbeitung von Zeilenumbrüchen und Zeilenumbrüchen wird für japanische Websites unterstützt.

* Die Verwendung der BUNSETSU-Methode wird nun unterstützt, um japanische Sprachsätze und -zeilen an geeigneten Positionen zu unterbrechen.

* Die CCR-Benutzeroberfläche für Correspondence Management unterstützt jetzt Dezimalwerte für das deutsche Gebietsschema.

* Die Integration des Formulardatenmodells mit dem SOAP-Webdienst unterstützt jetzt Auswahlgruppen oder Attribute zu Elementen.

* AEM Assets wird jetzt mit Brand Portal konfiguriert über [!DNL Adobe I/O].

* Aktualisierung der in ContextHub enthaltenen jQuery-Version auf 3.2.1.

## Liste der Änderungen {#list-of-changes}

### Sites {#sites}

* Wenn eine URL einer AEM Sites-Seite einen Doppelpunkt oder ein Prozentsymbol enthält, reagiert der zugrunde liegende Browser nicht mehr und die CPU-Zyklen zeigen eine Spitze (NPR-32368, NPR-31917).
* Wenn eine AEM Sites-Seite zur Bearbeitung geöffnet und eine Komponente kopiert wird, bleibt die Einfügeaktion für einige Platzhalter nicht verfügbar (NPR-32328).
* Der Aktivierungsanfrage-Workflow umfasst keine referenzierten Assets (NPR-32304).
* Wenn bei der Erstellung eines Blueprints die Anzahl der Datensätze 80 übersteigt, werden nur die 80 ersten Datensätze angezeigt. Der Blueprint zeigt für den Rest der Datensätze leere Zeilen an (NPR-32058).
* Benutzende dürfen ein Inhaltsfragment speichern, ohne Informationen in den erforderlichen Feldern bereitzustellen (NPR-31988).
* Die automatische Navigation funktioniert nicht für Pfade, die in einer Experience Fragment-Kernkomponente konfiguriert sind (NPR-31921).
* Wenn Sie den Typ einer Tabellenzelle im Rich-Text-Editor (RTE) ändern, tritt der folgende Fehler auf:
   `Error: No common ancestor found, cannot continue` (NPR-31916).
* Wenn Inhalt innerhalb desselben Ordners verschoben wird, ist die Option zum Verschieben der Seite deaktiviert (NPR-31841).
* Unterstützung für die Aufteilung japanischer Sprachsätze mithilfe der BUNSETSU-Methode und der Umbruchlinien an der entsprechenden Position hinzugefügt (NPR-31836).
* Wenn Sie einen Hyperlink im Rich-Text-Editor (RTE) bearbeiten, wird der neu ausgewählte Pfad nicht gespeichert (NPR-31659).
* Wenn Sie eine Multifield-Komponente löschen und den Löschvorgang rückgängig machen, wird die Komponente wiederhergestellt, die Daten werden jedoch nicht wiederhergestellt (NPR-31617).

### Assets {#assets}

* Ein Ordner ohne Namen wird in Dynamic Media Classic erstellt, während ein Asset in Experience Manager mit Dynamic Media Classic-Konfiguration von einem Ordner in einen anderen verschoben wird (NPR-32440).

* Die Asset-Detailseite von PDF-Dateien zeigt keine Aktionsschaltflächen im Experience Manager, der im Dynamic Media Scene7-Modus ausgeführt wird (NPR-32316).

* Asset- und Videoausgabeformate können nicht gelöscht werden (NPR-32213).

* Das Kalendersymbol für geplante Aktivierung wird nicht in der Spalte „Status“ (in der klassischen Benutzeroberfläche der DAM-Asset-Auflistung) für Assets angezeigt, deren Aktivierung für ein späteres Datum und eine spätere Uhrzeit geplant ist (NPR-32198).

* Die Beziehung von Assets wird überschrieben, wenn Assets mit mehreren Assets verbunden sind, die &quot;Sonstige&quot;verwenden (NPR-32196).

* Die Schaltfläche &quot;Speichern&quot;importiert kein Remote Set, wenn der Benutzer im Set-Editor im Dynamic Media Client keine Änderungen vorgenommen hat (NPR-32178).

* Die PSD-Asset-Erfassung verursacht CPU-Spitze und nicht responsive Experience Manager-Autoreninstanz (NPR-32165).

* Ausnahmefehler wegen ungenügenden Speicherplatzes, der beim Hochladen einer großen ZIP-Datei in Experience Manager DAM auftritt (NPR-32155).

* Versionsverlauf-URLs werden auf der Asset-Eigenschaftsseite unter „Referenziert von“ angezeigt (NPR-31889).

* Das Rückgängigmachen der Veröffentlichung in Brand Portal auf der Seite Veröffentlichung verwalten schlägt bei Unterordnern eines veröffentlichten Ordners fehl (NPR-31835).

* Dynamic Media-Videokodierungen können nicht hochgeladen werden, wenn die Scene7 Cloud-Konfiguration in einem privaten Ordner platziert wird `/conf` anstelle von `/conf/global` (NPR-31779).

* Das Bild wird auf der Timeline nach dem Hinzufügen von Anmerkungen nicht angezeigt, wenn auf einem Experience Manager im Dynamic Media Scene7-Ausführungsmodus ausgeführt wird (NPR-31754).

* Die vom DAM-System heruntergeladene ZIP-Datei kann nicht mit WinZip geöffnet werden (NPR-31745).

### Integrationen {#integrations-6480}

* Die **Firma** und **Berichterstellung** Dropdown-Menüs der Suite werden einmal ausgeblendet **Berichtsquelle** wird beim Konfigurieren von Adobe Analytics in Experience Manager Cloud Services ausgewählt (NPR-31729).

* Adobe Campaign-Eigenschaften werden nicht bereinigt, wenn eine Sprachkopie eines mit Adobe Campaign verknüpften Newsletters erstellt wird, während die Bereinigung erfolgt, wenn ein mit einer Adobe Campaign verknüpfter Newsletter kopiert oder eingefügt wird (NPR-32540).

* ReportSuitesServlet ist anfällig für SSRF (NPR-32161).

### Sling {#sling-6480}

* Nicht deterministisches Schatten der Ressourcenüberwachung funktioniert nicht (CQ-4286466).

### Projekte {#projects-6480}

* Die Schaltfläche &quot;Erstellen&quot;ist für den Benutzer nicht sichtbar, selbst wenn der Benutzer über die Berechtigung zum Erstellen eines Projekts im Unterordner verfügt (NPR-31831).

* Die Funktion zum Wechseln zwischen Karten-, Listen- und Kalenderansicht funktioniert nach der Auswahl der Kalenderansicht in Projekten nicht. (NPR-31829)

### Übersetzung {#translation-6480}

* Die Erstellung von Übersetzungsprojekten für mehrere Sprachen generiert das Projekt nur für einige der Sprachen anstelle von &quot;all&quot;. Im Protokoll wird ein Fehler (Resource Resolver ist bereits geschlossen) beobachtet (NPR-32212).

### WCM-MSM {#wcm-msm-6480}

* Berechtigungsprobleme führen dazu, dass beim Verschieben von Seiten innerhalb eines Blueprints Fehler angezeigt werden (NPR-32610).

### WCM-Seiten-Editor {#wcm-page-editor-6480}

* Der Browser reagiert nicht mehr, wenn er versucht, einer Seite mit einem bestimmten URL-Format eine Komponente hinzuzufügen (NPR-32368, NPR-31917).

### WCM-Admin-Benutzeroberfläche {#wcm-admin-ui-6480}

* Veröffentlichung verwalten enthält keine referenzierten Assets im Aktivierungsanfrage-Workflow (NPR-32304).

### Communities {#communities}

* Das Gruppenminiaturbild für Gruppen kann nicht aktualisiert werden (NPR-32603).

### Brand Portal {#brand-portal}

* Beim Rückgängigmachen der Veröffentlichung des Metadatenschemas in AEM Assets wird eine Fehlermeldung angezeigt, obwohl das Schema im Backend entfernt wurde. (CQ-4286871)

### Foundation-Benutzeroberfläche {#foundations-ui-6480}

* Ungültige Zeichen werden in der URL angezeigt, die einer Schaltflächenkomponente hinzugefügt wurde (NPR-32684).

### Formulare {#forms}

>[!NOTE]
>
>AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [AEM Forms Add-On-Paket installieren](#install-aem-forms-add-on-package) und [Installieren des AEM Forms JEE-Installationsprogramms](#install-aem-forms-jee-installer).

* Designer: Wenn die Tagging-Option aktiviert ist, verschwindet der Teilformularrahmen in der generierten PDF-Ausgabe (NPR-32546, NPR-32322).

* Designer: Wenn eine Tabelle zusammengeführte Zellen enthält, schlägt der Barrierefreiheitstest für die Ausgabe-PDF-Datei fehl, die mithilfe des Ausgabe-Service aus einem XDP-Formular konvertiert wurde (NPR-32079).

* Document Security: Eine geschützte PDF-Datei kann nicht offline geöffnet werden, wenn die Option „DisableGlobalOfflineSynchronizationData“ auf „True“ eingestellt ist (NPR-32080).

* Document Security: Probleme beim Öffnen einer geschützten PDF-Datei nach der Aktualisierung von ES4 auf AEM 6.3 (NPR-32170).

* Document Services: Beim Versuch, eine PDF-Datei mithilfe der toPDFA-Konvertierungsmethode in ein PDF/A-Dokument zu konvertieren, wird eine Fehlermeldung angezeigt. (NPR-32663)

* Document Services: Beim Anwenden des Reader Extensions-Dienstes auf eine PDF-Datei wird eine Ausnahme angezeigt (NPR-32639).

* Document Services: Beim Zusammenstellen und Konvertieren von XDP-Dateien in PDF-Dateien wird eine Fehlermeldung angezeigt (NPR-31821).

* Analytics zeigt keine geeigneten Ergebnisse beim Senden oder Abbrechen von Formularen auf einer Sites-Seite an (NPR-31359).

### In früheren Service Packs enthaltene Hotfixes und Feature Packs {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

AEM 6.4.7.0 ist ein wichtiges Update, das Verbesserungen der Leistung, Stabilität und Sicherheit sowie wichtige Fehlerbehebungen und Verbesserungen enthält, die seit der allgemeinen Verfügbarkeit von AEM 6.4 in veröffentlicht wurden. **April 2018.**

Es ist auch kumulativ, was bedeutet, dass 6.4.7.0 alle AEM 6.4 Service Packs umfasst, die zuvor veröffentlicht wurden.

Einige der wichtigsten Highlights von AEM 6.4.7.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.17 aktualisiert.
* Unterstützung zum Festlegen der Version einer Sites-Seite beim Löschen hinzugefügt.
* Eine neue Spalte für das sortierbare Erstellungsdatum wurde hinzugefügt in **DAM-Liste** Anzeigen und in Asset-Suchergebnissen in **Liste** Ansicht (NPR-31311).
* Asset-Sortierung basierend auf **Name** -Spalte ist in **Liste** anzeigen.
* Stapelgröße und Zeitüberschreitung bei Workflow-Schritten für die Neuverarbeitung und den Batch-Upload können jetzt über die Benutzeroberfläche in Dynamic Media konfiguriert werden.
* Die `pdfBrochure` wurde in der Scene 7-Cloud-Konfiguration auf false gesetzt, um Speicher in IPS zu speichern.

##### Assets {#assets-6470}

**Produktverbesserungen**

* Die Exportversion des API-Pakets `package com.day.cq.dam.handler.standard.msoffice` unterstützt von `dam-handler` Das Bundle wurde auf 6.0.0 aktualisiert (CQ-4279059).
Wenn Sie das Paket verwenden `com.day.cq.dam.handler.standard.msoffice` In Ihrer benutzerdefinierten Implementierung wird empfohlen, die `dam-handler` Bundle mit der neuesten uber jar.

* In der DAM-Listenansicht und den Asset-Suchergebnissen in der Listenansicht wurde eine neue Spalte für das sortierbare Erstellungsdatum hinzugefügt. (NPR-31311)

* Die Sortierung von Assets basierend auf der Spalte &quot;Name&quot;wurde in der Listenansicht zugelassen (NPR-31299).

**Fehlerkorrekturen**

* Metadaten für einige PDF-Dokumente werden beim Ändern des Titels nicht aktualisiert und auf der PDF gespeichert (NPR-31575).

* Assets mit dem Symbol &quot;+&quot;im Dateinamen können nicht gelöscht werden. (NPR-30588)

* In den DAM-Ordnereigenschaften werden die hinzugefügten (durch LDAP-Synchronisierung erstellten) Benutzer oder Gruppen in geschlossenen Benutzergruppen nicht angezeigt (NPR-30555).

* Sonderzeichen, die in der Betreffzeile von E-Mail-Vorlagen auftreten, werden nicht richtig angezeigt (NPR-30547).

* Asset-Namen werden beim Verschieben von Assets von einem Ordner in einen anderen im Dynamic Media Scene 7-Ausführungsmodus AEM in Kleinbuchstaben geändert (NPR-31631).

* Die Namen des Bildsets werden in Scene7 in Kleinbuchstaben geändert, wenn Bildset (oder Mediaset) erstellt und mit der entsprechenden Namenskonvention in DAM benannt wird (NPR-31576).

* Der Workflow für die Dynamic Media-Videokodierung kann keine Miniaturansichten für das Video generieren, das vom Scene7- in den Scene7-Ausführungsmodus migriert wird (NPR-31523).

* Interner Serverfehler wird beobachtet, wenn der Filter zum Suchen nach Sets verwendet wird, AEM im Dynamic Media Scene7-Ausführungsmodus ausgeführt wird (NPR-31388).

* Beim Bearbeiten eines Remote-Bildsets tritt ein Fehler für ein Bild auf, das sich in einem Ordner mit demselben Namen wie der Scene7-Unternehmensname befindet (NPR-31347).

* Assets, die Verweise enthalten, werden nicht veröffentlicht (DM) (NPR-31179).

* Der für den Modus „Dynamic Media Hybrid“ konfigurierte Wert zum Ablauf (Client-Cache-Zeit bis zum Livestream) wird nicht in die Umgebung für die Bereitstellung von Dynamic Media repliziert (NPR-31126).

* Uploads von AEM Dynamic Media - Scene7-Ausführungsmodus in Scene7 dauern zu lange, bis sie abgeschlossen sind (NPR-30926).

* Nachdem Sie eine Seite mit Dynamic Media-Komponente erstellt haben, während Sie dieselbe veröffentlicht haben, wird der Benutzer von der Autoreninstanz, die im Dynamic Media Scene7-Ausführungsmodus ausgeführt wird, aufgefordert, die dmscene7-Konfiguration zu veröffentlichen (NPR-30880).

* Der Wert des Parameters &quot;Asset&quot;im Viewer-Einbettungscode bleibt unverändert, nachdem die Werte in den Feldern &quot;Titel nach Verschiebung&quot;und &quot;Name nach Verschiebung&quot;in Dynamic Media - Scene 7 geändert wurden (NPR-30745).

* Die Ergebnisseite für die Touch-optimierte Suche (über Omnisearch) scrollt automatisch nach oben und verliert die Bildlaufposition der Benutzenden (NPR-31306).

* Die DAM-Ereignisbereinigung löscht die neuesten Ereignisdaten (maxSavedActivities) und enthält die zuvor erstellten Daten (NPR-30870).

* Asset-Titel und Namensänderung werden nach dem Verschieben in einen Zielordner, den Trigger unbegrenzt scrollen, während sie ihn auswählen, nicht beibehalten (NPR-30647).

* Sammlungen werden aus der Ansicht entfernt, wenn Sie einen beliebigen Filter in AEM Assets anwenden, auf den über Adobe Asset Link zugegriffen wird (CQ-4280534).

* Die Stapelgröße und der Zeitüberschreitungswert für Workflow-Schritte für die Neuverarbeitung und den Batch-Upload können nicht über die Benutzeroberfläche konfiguriert werden und müssen in CRXDE festgelegt werden. Der Workflow muss zweimal synchronisiert werden (CQ-4281254).

* Workflow-Schrittname für Batch-Upload und einfachen Upload-Schritt ist in Scene7 identisch, was zu Verwirrung führt (CQ-4281176).

* Neuverarbeitungs-Workflow in Scene7 wird blockiert, wenn einem Asset ein Metadatenknoten fehlt (CQ-4281170).

* Der Schritt &quot;BatchUpload&quot;im Neuverarbeitungs-Workflow funktioniert nicht für den Ordner mit dem Video-Asset (CQ-4280630).

* Für PDF-Optionen, die an DM gesendet werden, ist extractKeywords standardmäßig auf &quot;true&quot;gesetzt (CQ-4280101).

* Nullpunkt-Ausnahme wird beim Ausführen des Scene7-Neuverarbeitungs-Workflows für einen Ordner beobachtet, der Nicht-DM-Assets enthält. (CQ-4279555)

* Das Umbenennen von Assets in AEM kann nicht mit Szene 7 synchronisiert werden, wenn ein Asset mit einem doppelten Namen bereits in Scene 7 vorhanden ist (CQ-4276763).

* Die per E-Mail zum Herunterladen von Assets gesendete ZIP-Datei kann nicht entpackt werden, wenn ein Benutzer mit Leseberechtigungen versucht, sie zu öffnen (CQ-4277925).

* Der Arbeitsablauf für die PPT-Ausgabe kann keine Ausgabeformate der hochgeladenen PPT-Dateien generieren, da AEM 6.4 nicht auf com.adobe.granite.poi Version 2.0.28 aktualisiert werden kann (CQ-4279059).

* PDF-Dateien werden nicht indiziert und ihr Inhalt in ist nicht durchsuchbar (CQ-4278916).

##### Sites {#sites-6470}

* Wenn Launches mit &quot;Nur geänderte Seiten bewerben&quot;und &quot;Launches bewerben mit geänderten Seiten&quot;beworben werden, werden nur die geänderten Seiten beworben. Wenn die zu bewertende Liste korrekt ist, werden die nicht geänderten Seiten weiterhin am Ende der Liste angezeigt (NPR-31314).

* Wenn eine AEM Sites-Seite an einen anderen Speicherort verschoben wird, werden ihre Eigenschaften nicht entsprechend aktualisiert, um ihren neuen Speicherort widerzuspiegeln (NPR-31265).

* Bei einem neuen Blueprint werden bei mehr als 40 Datensätzen nur die ersten 40 Datensätze angezeigt. Der Blueprint zeigt für den Rest der Datensätze leere Zeilen an (NPR-31182).

* Wenn die Anzahl der LiveCopies groß ist, dauert die Wiedergabe der Vorschau in der LiveCopy-Übersicht lange (NPR-30945).

* Unterstützung zum Festlegen einer Seitenversion beim Löschen hinzugefügt. Wenn die Versionierung für die gelöschte Seite deaktiviert ist, kann AEM Sites solche Seiten nicht wiederherstellen (NPR-30891).

* Wenn Benutzende japanische oder koreanische Zeichen in die Beschreibungseigenschaft eines Menüs einfügen, zeigt das Menü verzerrte Zeichen für Text in japanischer und koreanischer Sprache an (NPR-31331).

* Wenn Benutzende den Fokus auf Felder in der linken Schiene legen und zum Einfügen von Inhalten einen Tastaturbefehl verwenden, wird der Inhalt der Zwischenablage des Seiteneditors anstelle des Inhalts eingefügt, der aus den Feldern der linken Schiene kopiert wurde (NPR-31169).

* Wenn ein Benutzer ein Inhaltsfragment bearbeitet, wird die bereits gelöschte Variante des Inhaltsfragments wiederhergestellt (NPR-31178).

* Die Abfrage von Inhaltsfragmentmodellen ist ineffizient. Es ist sehr langsam, wenn die Instanz viele Seiten hat und zu einem Fehler führt (NPR-30666).

* Beim Speichern des Inhaltsfragmentmodells wird die Zeit im Datums- und Uhrzeitfeld auf 00:00 Uhr festgelegt (NPR-30540).

##### Integrationen {#integrations-6470}

* Beim Konfigurieren von Adobe Launch wird ein Schrägstrich (/) in der Bibliotheks-URL vorangestellt (NPR-30700).

* Die ContextHub-Leistung verschlechtert sich nach der Veröffentlichung (NPR-30884).

##### Sling {#sling-6470}

* Aktualisieren Sie die Webconsole Security Provider Bundle-Version auf 1.2.4, um die Abhängigkeit der Launchpad-Starter-API vom Webconsolesecurityprovider zu entfernen (NPR-30885).

##### Platform {#platform-6470}

* Aktualisierungen der Puffergrößenkonfiguration für den Jetty-basierten HTTP-Service werden nicht gespeichert (NPR-30925).

* QueryBuilder unterstützt jetzt orderby fn:name() in xpath-Abfragen (NPR-31322).

* Aktualisierung des verteilten Sling-Ereignisadmins auf Version 1.1.4, um die Qualität der Protokolle in einer Clusterumgebung zu verbessern (NPR-29256).

##### Foundation-Benutzeroberfläche {#foundation-6470}

* Wenn Sie mit einer großen Anzahl von Suchergebnissen zum Ende der Ergebnisseite scrollen, kommt es zum Absturz des Browsers. (NPR-31332)

* Beim Wechseln von der Kartenansicht zur Listenansicht auf einer Suchergebnisseite kommt es zu einer Verzögerung, bevor ein Bildlauf auf der Seite möglich ist. (NPR-31280)

##### Oak {#oak-6470}

* MS Office-Dateien mit Dateierweiterungen .docx und .xlsx, die JPEG-Bilder enthalten, können mit dem Tika-Parser nicht analysiert werden (NPR-31693).

##### Livefyre {#livefyre-6470}

* Die Livefyre-Integration in AEM 6.4-Upgrade führt zu einer Nullpunkt-Ausnahme, wenn die Integration mit dem DITA-Plug-in für synthetische Ressourcen erfolgt. Die Integration funktioniert jedoch, wenn Komponenten manuell hinzugefügt werden (FYR-11066).

##### Übersetzung {#translation-6470}

* Der Pfad zum Zielerlebnisfragment wird beim Anzeigen einer Launch-Seite nicht aktualisiert (NPR-30830).

##### Communities {#communities-6470}

* E-Mail-Funktionalität funktioniert in einigen Fällen nicht ordnungsgemäß, auch wenn E-Mail-Messaging in den Benachrichtigungseinstellungen aktiviert ist. Das System löst im NotificationsActivityStreamProvider (NPR-31521) eine Ausnahme aus.
* Es ist nicht möglich, neue Mitglieder zu erstellen. Auf dem Bildschirm Mitglied erstellen in AEM Autoreninstanz wird ein leerer Bildschirm angezeigt (NPR-30951).
* Benutzer können keinen Kommentar zu einem Blog in Internet Explorer 11 (NPR-30927) posten.
* Der Administrator einer eingeschränkten Gruppe kann die Gruppenkarte nicht anzeigen und kann keine Schnelllink-Vorgänge (Gruppen bearbeiten/veröffentlichen/löschen) in AEM Autoreninstanz durchführen (NPR-30810).
* Informationen zu Mitgliedergruppen/Gruppen sind beim Erstellen einer neuen Site in AEM Autoreninstanz nicht sichtbar (NPR-28840).

##### Formulare {#forms-6470}

>[!NOTE]
>
>AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [AEM Forms Add-On-Paket installieren](#install-aem-forms-add-on-package) und [Installieren des AEM Forms JEE-Installationsprogramms](#install-aem-forms-jee-installer).

**Forms-Add-on-Paket**

**Adaptive Formulare**.

* Beim Lokalisieren von adaptiven Formularen enthalten Zeichenfolgen den Wörterbuchschlüssel (NPR-31109).

* Die Kontrollkästchen und Dropdown-Listen in Forms schlagen Barrierefreiheitsprüfungen fehl (NPR-31282).

**HTML5-Formulare**

* Beim Generieren einer HTML5-Vorschau eines XDP-Formulars tritt Flackern auf, während Instanzen eines Teilformulars hinzugefügt werden (NPR-30907).

**Document Services für OSGi**

* Wenn Sie mehrere gleichzeitige Threads zum Zusammenstellen der Formulare mit der Methode com.adobe.fd.assembler.service.AssemblerService.invoke() ausführen, wird eine Fehlermeldung angezeigt (NPR-31164).

* Die temporären Dateien, die von Assembler Service erstellt wurden, werden nicht automatisch gelöscht und müssen AEM neu gestartet werden. (NPR-30846)

* Das Anwenden von ReaderExtension-Rechten auf PDF führt zu einer Fehlermeldung (NPR-30930).

**Arbeitsablauf**

* Der OSGi-Workflow schlägt aufgrund von 100%iger CPU-Auslastung fehl (NPR-31234).

**Forms JEE-Installationsprogramm**

**Document Services**

* Der Convert PDF Service kann keine PDF-Dokumente in PostScript konvertieren und zeigt eine Fehlermeldung an (NPR-31267).

* Die SOAP-Endpunktkonfiguration wird zurückgesetzt, nachdem ein Patch angewendet wurde, um den HTML auf PDF-Fehler zu beheben (NPR-31309).

**PDFG Service**

* Die mit der Administrator-Benutzeroberfläche heruntergeladene Adobe PDF-Einstellungsdatei kann nicht hochgeladen werden (NPR-31273).

#### AEM 6.4.6.0 {#experience-manager-6460}

AEM 6.4.6.0 ist ein wichtiges Update, das Verbesserungen der Leistung, Stabilität und Sicherheit sowie wichtige Fehlerbehebungen und Verbesserungen enthält, die seit der allgemeinen Verfügbarkeit von AEM 6.4 in veröffentlicht wurden. **April 2018.**

Es ist auch kumulativ, was bedeutet, dass 6.4.6.0 alle AEM 6.4 Service Packs enthält, die zuvor veröffentlicht wurden.

Einige der wichtigsten Highlights von AEM 6.4.6.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.15 aktualisiert.
* Unterstützung für das Tracking von Status der dynamischen Benutzeroberfläche im Tracking-Ereignis in der Foundation-API hinzugefügt.
* Zusätzliche Unterstützung für Ausgabedarstellungen zur Bild-Core-Komponente.

**Assets**

* Asset-Freigabe-Link eines Ordners mit Leerzeichen und `&` -Zeichen im Namen zeigt leere graue Karten für einige Assets an. NPR-29934: Hotfix für CQ-4270187
* DAM-Workflow stürzt beim Erstellen von MP4-Assets für AEM ab. NPR-30031: Hotfix für CQ-4271352
* Problem bei der Verbindung mit Adobe Smart-Tag über DataPower. NPR-30026: Hotfix für CQ-4269457
* PDF kann nicht mit OmniSearch gefunden werden. NPR-30046: Hotfix für GRANITE-26290
* Asset-Pfade in URLs und Ordner-Metadaten, die von der AKP-API generiert wurden, sind nicht URL-kodiert.  GRANITE-26198: Hotfix für CQ-4271814
* Die Funktion &quot;Prüfungsaufgabe erstellen&quot;funktioniert aufgrund einer nicht definierten Payload nicht. NPR-30469: Hotfix CQ-4274263
* Die Möglichkeit, die Ansicht von der Kartenansicht zur Listenansicht zu wechseln, verschwindet nach einer OmniSearch-Funktion in der Asset-Auswahl. NPR-29852: Hotfix für CQ-4269369
* (Touch-optimierte Benutzeroberfläche) Während des Assistenten zum Verwalten der Veröffentlichung werden Assets zur Replikationswarteschlange hinzugefügt, nachdem die Seiten hinzugefügt wurden. Dadurch werden einige der Assets nach einigen Sekunden angezeigt. NPR-29985: Hotfix für CQ-4270724
* Bei der Sortierung der Suchabfrage nach Relevanz werden InDesign-Dokumente zusammen mit InDesign-Vorlagen zurückgegeben. Hotfix für CQ-4273864
* Wenn der Benutzer über eine E-Mail-ID in Großbuchstaben verfügt, können die Benutzer nicht für die zuvor ausgecheckten Assets einchecken. Hotfix für CQ-4276575
* Konfigurieren von Dynamic Media Cloud Services in `DMHybrid` führt dazu, dass mehrere leere Report Suites in Analytics erstellt werden, ohne dass in AEM eine Report Suite-ID gespeichert ist, was zu einer Duplizierung der Report Suite führt. Hotfix für CQ-4276855
* Das Warndialogfeld wird beim Bewerben auf der Seite &quot;Verwaltetes Tag&quot;nicht angezeigt. Hotfix für CQ-4252851
* Bei Verwendung des Karussells zur Verwaltung von Tags funktioniert die Navigationsschaltfläche nicht. Hotfix für CQ-4275499
* Die Funktion zum Verschieben von Assets per Massenvorgang ist fehlerhaft, was dazu führt, dass Assets nicht verschoben werden. Hotfix für CQ-4272987

**Sites**

* `pageinfo.json` -Anfragen sind extrem langsam und das Laden dauert zu lange. NPR-29709: Hotfix für CQ-4269560
* `onTime` oder `offTime` Auf Assets gespeicherte Metadateneigenschaften werden nicht zurückgerufen, wenn der AEM neu gestartet wird. NPR-30413: Hotfix für CQ-4272784
* Aufgrund des falschen Verhaltens der ConfigPostProcessor-Klasse wird durch das Aussetzen der übergeordneten Seite cq entfernt: LiveRelationship-Mischungstyp von der untergeordneten Seite. NPR-30536, NPR-30510: Hotfix für CQ-4254113
* Site-übergreifende Skripterstellung (XSS) im Dialogfeld &quot;Workflow starten&quot;auf der Kampagnenbearbeitungsseite. NPR-29747: Hotfix für CQ-4271067
* (Klassische Benutzeroberfläche) Die Workflow-Sperrphase deaktiviert die Workflow-Registerkarte, bis die Sperre aufgehoben wird. NPR-30356: Hotfix für CQ-4237557
* (IE11) Beim Einfügen von HTML-Inhalt in eine Rich-Text-Editor-Komponente mit defaultPasteMode = plaintext wird der HTML mit der Formatierung eingefügt. Daher hat defaultPasteMode keine Auswirkung. NPR-30045: Hotfix für GRANITE-26094
* (Klassische Benutzeroberfläche) Wenn die Site-Admin-Seite neu geladen wird, sind alle Dropdown-Elemente im Menü &quot;Neu&quot;deaktiviert. NPR-29980: Hotfix für CQ-4272044
* Es können keine Stile zum Text hinzugefügt oder vorhandene Stile, die für den Inhalt erstellt wurden, bearbeitet werden. NPR-29712: Hotfix für CQ-4266249
* (Klassische Benutzeroberfläche) Assets ohne dc: Der Titelwert wird ohne Titel im Dialogfeldbrowser für Pfadfelder aufgeführt. NPR-30166: Backport-Anfrage für CQ-88858
* cq: Listener funktioniert nicht mit verschachtelten Komponenten, selbst wenn die parsys-Komponente hinzugefügt wurde. NPR-30422: Hotfix für CQ-4274863
* ContextHub-Fehler während der AEM- und Campaign-Integration. NPR-30625: Hotfix für CQ-4250790
* Der Wert des Abfrageparameters „resourceType“ wird in den Wert eines HTML-Tag-Attributs kopiert, das in doppelte Anführungszeichen eingeschlossen ist. NPR-29832: Hotfix für CQ-4255365
* Eine Seitenaktualisierung ist erforderlich, nachdem Komponenten kopiert und von einer Seite auf eine andere eingefügt wurden. NPR-29982: Hotfix für CQ-4256019
* Das Veröffentlichen/Rückgängigmachen der Veröffentlichung in einem Seitenalias wird nicht unterstützt und sollte entfernt werden. NPR-30062: Hotfix für CQ-4271249
* Nicht geschlossene ResourceResolver-Warnmeldung in ExperienceFragmentsReplicationListener, die im Laufe der Zeit zu Stabilitätsproblemen führt und AEM Instanzen neu starten muss. NPR-30416: Hotfix für CQ-4257521
* Beim Verschieben von Experience Fragments, auf die auf mehr als 150 Seiten verwiesen wird, wird der fragmentPath auf den Seiten, auf die sie verwiesen werden, nicht geändert. NPR-30556: Hotfix für CQ-4274900
* Parsing-Fehler beim Öffnen eines Inhaltsfragments, das die Zeichen Dollar (`$`) und offene Klammer (`{`) einen nach dem anderen. Hotfix für CQ-4270266
* Das VersionPreviewServlet schlägt in NullPointerException fehl, wenn versucht wird, eine Version eines Experience Fragment in der Timeline anzuzeigen. NPR-30074: Hotfix für CQ-4271881
* Inhaltsfragmente können nicht über die Funktion &quot;Einchecken&quot;gesperrt werden. NPR-29923: Hotfix für CQ-4258785
* Fehler bei der Signaturüberprüfung im SAML-Authentifizierungs-Handler. NPR-30379: Backport-Anfrage für GRANITE-26567

**Replikation**

* JCR-Sitzung/Resource Resolver wird bei jeder Replikation nach MAC/Brand Portal während der OAuth-Implementierung durchsickert. NPR-30000: Hotfix für Granite-26196

**Sling**

* Die Reihenfolge der betroffenen untergeordneten Elemente, die Überlagerungen und Reihenfolge vor verwenden, verursacht IndexOutOfBoundException. NPR-30408: Hotfix für Sling-8296 und Sling-7375
* InactiveBundlesHealthCheck liest die Konfiguration MissingPackagesHealthCheck , sobald die Konfigurationen InactiveBundlesHealthCheck gespeichert wurden. NPR-30084: Hotfix für CQ-4272644

**Commerce**

* Der Katalog-Blueprint kann nicht über die Sites-Konsole ausgeführt werden. NPR-29829: Hotfix für CQ-4271461
* Das im Produkt verwendete Asset zeigt weder im Abschnitt &quot;Verweise&quot;des Assets einen Verweis auf das Produkt an, noch wird der Asset-Pfad aktualisiert, wenn das Asset verschoben wird. NPR-30542: Hotfix für CQ-4270247

**Plattform**

* AEM Standard Mail Sender kann über TLS v1.2 keine E-Mails an einen Remote-SMTP-Server senden. NPR-30476: Hotfix für GRANITE-26605

**Communities**

* Auf der Autoreninstanz gelöschte Gruppen sind nicht mit allen Herausgebern synchronisiert. NPR-29987: Hotfix für CQ-4268738
* Gelöschte Benutzer, die aus dem Feld &quot;Community-Administratoren&quot;entfernt wurden, stehen nicht mit der Gruppe Mitgliedschaft in synchron. NPR-30389: Hotfix für CQ-4274339
* Benutzer, die Teil der Administratorgruppe sind, haben keine Schnelllinks für die Gruppe. NPR-30546: Hotfix für CQ-4275579
* Wenn Sie eine neu erstellte und vorhandene Community-Gruppe aktualisieren, wird die Eigenschaft in jcr überschrieben: Inhaltsknoten und ändert ihren Namen in den Titel der ersten Seite. NPR-30109: Hotfix für CQ-4273719
* Die Schnellsuche und Suche nach Ort und Adresse funktioniert nicht, wenn die Community so eingerichtet ist, dass sie mit dem Datenbankspeicherressourcenanbieter (DSRP) funktioniert. NPR-26737: Hotfix für CQ-4258493

**Übersetzung**

* Die automatische Ausführung der Übersetzung funktioniert nicht. NPR-30499: Hotfix für CQ-4276288
* Der Benutzer kann Sprachkopien für den Inhaltspfad erstellen, die auf schreibgeschützt beschränkt sind. NPR-29937: Hotfix für CQ-4270708
* Übersetzungsfehler - Nur einige wenige Komponenten werden mit maschineller Übersetzung übersetzt. NPR-30079: Hotfix für CQ-4273764

**Integration**

* Der angepasste Inhalt wird auf der Veröffentlichungsinstanz erst nach dem Neustart der Instanz korrekt angezeigt. NPR-30421: Hotfix für CQ-4273706

**Projekte**

* Die dam:folderThumbnailPaths-Ordners werden nicht aktualisiert und zeigen auch nach dem Löschen der Assets im Ordner noch die alten Miniaturansichten an. NPR-30424: Hotfix für CQ-4273667

**UI-Konsolen**

* Site-übergreifende Skripterstellung (XSS) in den Seiteneigenschaften von Sites auf der Registerkarte &quot;Miniatur&quot;. NPR-30048: Hotfix für Granite-26200

**UI-Foundation**

* Unterstützung für das Tracking von Status der dynamischen Benutzeroberfläche im Tracking-Ereignis in der Foundation-API hinzugefügt. NPR-30742, GRANITE-26322: Hotfix für GRANITE-26036

**Formulare**

>[!NOTE]
>
>AEM Service Pack enthält keine Fehlerbehebungen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. Weitere Informationen finden Sie unter [AEM Forms Add-On-Paket installieren](#install-aem-forms-add-on-package) und [Installieren des AEM Forms JEE-Installationsprogramms](#install-aem-forms-jee-installer).

**Forms-Add-on-Paket**

**Adaptive Formulare**.

* Eine leere .css-Datei benötigt mehr Zeit, um vom Herausgeber abzurufen, was zu Leistungsproblemen führt. NPR-30558: Hotfix für CQ-4274399
* Forms, die nach der Veröffentlichung geändert werden, werden beim Veröffentlichen der Site nicht erneut veröffentlicht. NPR-30411: Hotfix für CQ-4236566

**Forms - Backend-Integration**

* Beim Erstellen des Formulardatenmodells mit der Web Service Definition Language (WSDL) wird ein Fehler ausgegeben. NPR-30388: Hotfix für CQ-4272921

**Forms – Korrespondenz-Management**

* Sonderzeichen wie Kleiner-als (&lt;), Größer-als (>) und kaufmännische Und-Zeichen (&amp;) werden in der Benutzeroberfläche für Agenten kodiert. NPR-30410: Hotfix für CQ-4273887
* Beim Auslösen eines Textfragments, das Datenwörterbuchwerte enthält, reagiert die Benutzeroberfläche des Agenten nicht mehr. NPR-30098, NPR-30083: Hotfix für CQ-4272204
* Die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;(CCR-Benutzeroberfläche) schlägt gelegentlich mit der Fehlervariablen (Objektobjekt) fehl. NPR-29983: Hotfix für CQ-4273874
* Das Neuladen von Briefentwürfen schlägt mit einer Ausnahme fehl, wenn die Beschreibung von Dokumentfragmenten Sonderzeichen wie Kleiner-als (&lt;), Größer-als (>) und Und-Zeichen (&amp;) in Eigenschaften enthält. NPR-29930: Hotfix für CQ-4252762

**HTML5-Formulare**

* Wird im Durchsuchen-Modus „NonVisual Desktop Access“ zum Lesen eines HTML5-Formulars verwendet, liest der Chrome-Browser vor jeder skalierbaren Vektorgrafik (SVG) im Formularentwurf das Wort „Grafik“. NPR-30450: Hotfix für CQ-4274732

**Forms JEE-Installationsprogramm**

**Forms – Foundation JEE**

* Beim Hinzufügen oder Bearbeiten einer Webdienstverbindung durch Aufrufen von Webdiensten aus AEM Forms Workbench wird ein Fehler ausgegeben: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30116: Hotfix für CQ-4273217

**Forms - Dokumenten-Services**

* PDF/A label missing error in Acrobat preflight. NPR-30594: Hotfix für CQ-4276032
* Datenbindungen mit nur einem Zeichen in PDF führen dazu, dass Reader-Erweiterungen mit dem Fehler &quot;java.lang.StringIndexOutOfBoundsException: Zeichenfolgenindex außerhalb des Bereichs: 1&quot;. NPR-30128: Hotfix für CQ-4273878
* Wenn ein Ladetest für den HTML-zu-PDF-Service ausgeführt wird, schlägt er mit einem Fehler fehl und die Dateitypeinstellungen werden vom AEM Forms-Server entfernt. NPR-30085: Hotfix für CQ-4272631
* Beim Reduzieren einer PDF mit Adobe Acrobat 9.1 (XFA-Version 3.0) wird der PDF-Formularstatus nicht beibehalten: Unsichtbare Elemente im Formular werden wieder auf einen sichtbaren Status zurückgesetzt. NPR-29978: Hotfix für CQ-4270888

**Forms – Dokumentsicherheit**

* Das Anwenden einer Unterschrift mit Zeitstempel schlägt mit folgender Meldung fehl: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Aufruffehler. NPR-30696, NPR-30537: Hotfix für CQ-4273778
* Configuration Manager fügt keine japanischen Zeichenfolgen für lokalisierte Tabellenspalten ein. NPR-30496: Hotfix für CQ-4274868

**PDFG Service**

* Verbindungsfehler beim Versuch, das Word-Dokument unter Windows Server 2016 in PDF zu konvertieren. NPR-30597: Hotfix für CQ-4275652
* Berechtigung verweigert Ausnahme bei der Verwendung des HTML zum PDF-Backend-Service über die &quot;phantomjs&quot;-Bibliothek. NPR-30456: Hotfix für CQ-4258077
* maxReuseCount für HTML zum PDF-Dienst wird in JBoss Management Console nicht angezeigt. NPR-30303, NPR-30135: Hotfix für CQ-4273763

#### AEM 6.4.5.0 {#experience-manager-6450}

AEM 6.4.5.0 ist ein wichtiges Update, das Verbesserungen der Leistung, Stabilität und Sicherheit sowie wichtige Fehlerbehebungen und Verbesserungen enthält, die seit der allgemeinen Verfügbarkeit von AEM 6.4 in veröffentlicht wurden. **April 2018.**

Es ist auch kumulativ, was bedeutet, dass 6.4.5.0 alle AEM 6.4 Service Packs umfasst, die zuvor veröffentlicht wurden.

Einige der wichtigsten Highlights von AEM 6.4.5.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.13 aktualisiert.
* Socket-Timeout und Verbindungs-Timeout in Brand Portal-Replikationsagenten hinzugefügt.
* Omnisearch-Verbesserungen - Die Paginierungsgrenze des Suchergebnisses wurde auf 100 Seiten erhöht.
* Behinderte `AssetDownloadServlet` OSGi-Komponente standardmäßig in AEM Veröffentlichungsinstanzen. Weitere Informationen finden Sie unter [Herunterladen von Assets von AEM](/help/assets/download-assets-from-aem.md).
* Unterstützung für Multi-Site-Manager für Assets wurde aktiviert. Weitere Informationen finden Sie unter [Wiederverwenden von Assets mit MSM für Assets](/help/assets/reuse-assets-using-msm.md).

**Assets**

* Assets mit einem Apostroph im Dateinamen werden nicht mit Dynamic Media synchronisiert. NPR-29538: Hotfix für CQ-4270592
* Die DAM DMGateway-Schnittstelle bietet jetzt Unterstützung für S3 Multipart. NPR-29740: Hotfix für CQ-4226303
* Das Dialogfeld zum Herunterladen von Assets zeigt beim Herunterladen von Ausgabeformaten für ein Video in Dynamic Media eine falsche Dateigröße an. NPR-29642: Hotfix für CQ-4246202
* Assets sind nicht mehr verwendbar, nachdem Day CQ DAM Mime Type Service Text für m3u8 anwendet. NPR-29276: Hotfix für CQ-4264052
* Bei der Asset-Referenzanpassung kann die Sitzung nicht gespeichert werden, wenn eines der verschobenen/umbenannten Assets Teil von Sling-Ressourcensammlungen ist. NPR-29143: Hotfix für /CQ-4252605
* Assets können nicht durch Suchen nach den Metadatenwerten verfolgt oder gefunden werden. NPR-29141: Hotfix für CQ-4260215
* Wenn Sie den Suchfilter zum Speichern einer Smart-Sammlung verwenden, wird der Fokus durch die Klickaktion im Bereich nicht beibehalten. NPR-29000: Hotfix für CQ-4240323
* Durch Verschieben eines Ordners können Sie einen Ordner mit Namen in Groß- oder Kleinschreibung erstellen. NPR-28945: Hotfix für CQ-4265234
* Leere Ergebnisse werden in Omnisearch angezeigt, wenn der Sammlungsname über Leerzeichen verfügt. NPR-29001: Hotfix für CQ-4236729
* Beim Umbenennen einer Datei mit einigen nicht unterstützten Sonderzeichen wie dem kaufmännischen Und-Zeichen (&amp;) wird ein ungültiger Ordner erstellt. NPR-29196: Hotfix für CQ-4265037
* DAM Extract Archive for zip file-Funktionalität ist fehlerhaft. NPR-29187: Hotfix für CQ-4254421
* Der Metadatenimport sollte den Import von Metadaten ermöglichen, ohne Namespaces zu registrieren. NPR-29425, NPR-28132: Hotfix für CQ-4269445
* Das Speichern von Metadatenänderungen funktioniert nicht für Assets, deren Name ein Anführungszeichen enthält. NPR-29395: Hotfix für CQ-4254305
* DAM-Assets können nicht verschoben werden, wenn der Dateiname Leerzeichen enthält. NPR-29270: Hotfix für CQ-4266403
* ZIP-Archive, die mit dem Deflate64-Algorithmus komprimiert wurden, können nicht heruntergeladen werden. NPR-29225: Hotfix für CQ-4253995
* Asset-Miniaturansichten werden beim Öffnen eines Ordners mit Assets mit vielen Versionen langsam angezeigt. NPR-29833: Hotfix für CQ-4271629
* Die markierte Sammlung kann nicht eingegeben werden, wenn nach Auswahl der Sammlung die Eingabetaste gedrückt wird. NPR-29723: Hotfix für CQ-4261607
* Cross-Site Scripting (XSS)-Angriffe über das eingeschränkte Warnhinweisfenster. NPR-29671: Hotfix für CQ-4270133
* Das Hinzufügen von Beziehungen zu Assets schlägt für Benutzer ohne Löschberechtigungen fehl. NPR-29640: Hotfix für CQ-4269196
* Wenn der Benutzer nach dem Hinzufügen des Asset-Titels auf der Eigenschaftenseite versucht, die Seite zu schließen, AEM die Eigenschaftenseite erneut geöffnet. NPR-29628: Hotfix für CQ-4264929
* Das Erstellen einer großen Anzahl von Relationen zu Assets führt zu einem Fehler. NPR-28779: Hotfix für CQ-4250708
* Die Asset-Erfassung ist im Scene7 Connect-Ausführungsmodus langsam. NPR-28658: Hotfix für CQ-4263007
* Ein Fehler Uncaught TypeError: Die Eigenschaft &#39;split&#39; von undefined kann nicht gelesen werden, wenn versucht wird, die Suchergebnisse anzuzeigen. NPR-28803: Hotfix für CQ-4248371
* Die Replikation von AEM nach Brand Portal ist über lange Zeit blockiert. NPR-28914: Hotfix für CQ-4254932
* Das Verschieben von Assets in DAM führt nicht zu einem ähnlichen Schritt in Scene7. NPR-28957: Hotfix für CQ-4264974
* Metadatenaktualisierungen werden nicht an IPS übergeben, wenn das Metadatenfeld in AEM aktualisiert wird. NPR-28961: Hotfix für CQ-4255393
* VersioningTimelineEventProvider sollte die Stammversion zusammen mit dem Versionskommentar bereitstellen. Hotfix für GRANITE-26063
* Die Eingabe von Daten führt zur Code-Ausführung auf der Server-Seite. Hotfix für CQ-4270246
* Unterstützung für Multi-Site-Manager für Assets wurde aktiviert. Hotfix für CQ-4271453, CQ-4268621, CQ-4257491
* AEM Benutzeroberfläche sollte einen zusätzlichen Eintrag für die aktuelle Version des Assets im Timeline-Verlauf anzeigen, in dem der neueste Eincheckkommentar von Adobe Asset Link angezeigt wird. Hotfix für CQ-4262864
* Das Beispielvideo wird beim Erstellen oder Bearbeiten eines MixedMediaSet nicht geladen. Hotfix für CQ-4244889
* Wenn Sie die Berechtigungen zum Löschen von Inhalten auf der AEM deaktivieren, kann der Benutzer keine Inhalte in Brand Portal veröffentlichen. Hotfix für CQ-4270426
* Probleme mit der Abfragebegrenzung bei Asset-Berichten nach der Aktualisierung auf AEM 6.4.3. NPR-28588: Hotfix für CQ-4262022, CQ-4260697
* Die Download-Funktion nutzt AEM Assets über das assetdownload-Servlet, sodass anonyme Benutzer alle Assets herunterladen können. NPR-27315, Hotfix für CQ-4254732

**Sites**

* Der JCR-Beschwerderetikettname sollte basierend auf dem Tag-Titel automatisch ausgefüllt werden. NPR-28990: Hotfix für CQ-4199411
* Die Schaltfläche Vererbung abbrechen ist in einigen Feldern, die in den Seiteneigenschaften hinzugefügt wurden, nicht sichtbar. NPR-29079: Hotfix für CQ-4265686
* Die Aktion &quot;Rollout-Vorschau&quot;sollte nicht versuchen, die Live Copy neu zu erstellen oder sie in der Liste der Rollout-Seiten anzuzeigen. NPR-29151: Hotfix für CQ-4266213
* (Vorlagen-Editor) Regression der Stilrichtlinie im Strukturmodus. NPR-28981: Hotfix für CQ-4264400
* Verschachtelte Live Copies zeigen doppelte Einträge während des Rollouts an. NPR-29300: Hotfix für CQ-4268664
* Das Veröffentlichen einer Live Copy einer Live Copy, die eine Design Importer-Komponente enthält, schlägt mit Fehlgeschlagener Abrufen von Verweisen für die ausgewählte Seite fehl. NPR-28944: Hotfix für CQ-4265014
* Bei Verwendung von CoralUI für Multifield wird fileReferenceParameter auf Komponentenebene statt auf Multifield-Ebene abgelegt. NPR-29536: Hotfix für CQ-4266129
* Die Designreferenz wird nach dem Abbrechen der Vererbung im Design Importer nicht bei der Veröffentlichung repliziert. NPR-29648, NPR-29721: Hotfix für CQ-4269270, CQ-4271087
* Das Pfadfeld im Rich-Text-Editor wird unabhängig vom Pfad, der für die Suche angegeben ist, im Stammpfad geöffnet. NPR-29483: Hotfix für CQ-4268997
* (IE11) Kopieren Sie den HTML-Inhalt in eine RTE-Komponente mit defaultPasteMode = plaintext fügt den Inhalt nicht als Text ein. NPR-29432, NPR-29171: Hotfix für GRANITE-24941
* Die Rechtschreibprüfung des Rich-Text-Editors funktioniert nicht mehr in anderen Sprachen. NPR-29506: Hotfix für CQ-4264990
* Site-übergreifende Skripterstellung (XSS) auf der Kampagnenseite. NPR-29614: Hotfix für CQ-4269322
* Die Minimierung des Rich-Text-Editors im Vollbildmodus im Quellbearbeitungsmodus führt zum Verlust von Inhalten. NPR-29574: Hotfix für CQ-4260584
* (Klassische Benutzeroberfläche) Die Navigation zur letzten Registerkarte ist nicht immer möglich, wenn eine große Anzahl von Tags vorhanden ist. NPR-29544: Hotfix für CQ-4264548
* (Klassische Benutzeroberfläche) Das Navigationsmenü der Admin Console wird nicht mehr angezeigt und die Seite wird nicht vollständig geladen. NPR-29571: Hotfix für CQ-4264585
* Beim Hinzufügen von Komponenten zur WCM-Seite wird eine Fehlerwarnung erzeugt, wenn die Minimierung in der Instanz aktiviert ist. NPR-29396: Hotfix für CQ-4266196
* Ein Problem mit der Vererbung von Stilsystemknoten vom übergeordneten Element. NPR-29296: Hotfix für CQ-4266041
* Die mit Timewarp wiederhergestellte Seite sollte sich auf das richtige Bild zum Zeitpunkt der Versionierung beziehen.  NPR-29431: Hotfix für CQ-4262638
* Leere Seite mit JavaScript-Fehlern im Editor nach der Installation der neuesten Snapshot-Version 6.4.5. NPR-29475: Hotfix für CQ-4266196
* Beim Hinzufügen einer Komponente zu einem parsys wird die Listeneigenschaft der Designkomponenten nicht berücksichtigt und in einen anderen Vorlagenknoten mit einer ähnlichen parsys-Struktur aufgelöst. NPR-29509: Hotfix für CQ-4269044
* cq:dropTargets -Bereich deckt die gesamte Komponente und nicht die Bildgröße ab, wodurch das Targeting mit eingebetteten Komponenten erschwert wird. NPR-29738: Hotfix für CQ-4268912
* Die Bildkomponente ruft den Listener &quot;afteredit&quot;nicht auf, nachdem der Bildeditor für die Bearbeitung im Kontext verwendet wurde. NPR-29616 Hotfix für CQ-4268065
* Ein Problem bei der Einrichtung der Social-Media-Veröffentlichung für Facebook. NPR-29212: Hotfix für CQ-4266630
* Beim Weiterleiten von Launches für geänderte Seiten werden Anpassungen sowohl im Quell- als auch im Launch-Zweig berücksichtigt. NPR-29308: Hotfix für CQ-4266746
* Die gerenderte Miniaturansicht im Inhaltsfragment zeigt eine interne Kalenderdarstellung für das Datums- und Uhrzeitfeld an. NPR-29531: Hotfix für CQ-4269362
* Das Hinzufügen eines Tags in Stapeln kann nicht zu Seiten mit vorhandenen verschiedenen Tags durchgeführt werden. NPR-28729: Hotfix für CQ-4262922
* Das Symbol Geplante Aktivierung wird nicht im Site-Administrator angezeigt. NPR-28725: Hotfix für CQ-4263917

**Replikation**

* Sicherheitslücke bei der Offenlegung vertraulicher Informationen in der Replikationsagenten-Komponente. NPR-29612, NPR-24951: Hotfix für GRANITE-25070
* Vom Benutzer bereitgestellte Daten werden bei der Ausgabe in der Komponente cq/replication/components/agent nicht maskiert, was zu einer Sicherheitslücke beim gespeicherten Cross-Site-Scripting (XSS) führt. Hotfix für CQ-4266263

**Experience Fragments**

* Experience Fragments können nicht als Ziel exportiert werden, wenn die intelligente Bildkomponente verwendet wird. Hotfix für CQ-4269606

**Social - Reporting**

* AEM Community-Berichte werden nicht in AEM Autoreninstanz angezeigt. Hotfix für CQ-4266294

**Plattform**

* Site-übergreifende Skripterstellung (XSS) im Paketmanager bei der Installation eines Pakets. NPR-29734, NPR-29713, NPR-29630: Hotfix für GRANITE-26161, GRANITE-
* Mehrere gespeicherte und reflektierte Cross-Site-Scripting (XSS) in CRXDE Lite. NPR-29634: Hotfix für GRANITE-26049
* Die Anmeldefunktion für Package Share verwendet die GET-Anfrage anstelle der POST-Anfrage, wodurch das Kennwort auf der Registerkarte &quot;Netzwerk&quot;angezeigt wird. NPR-29631: Hotfix für GRANITE-26048

**Felix**

* Site-übergreifende Skripterstellung (XSS) in der Systemkonsole. Die Seite wird geladen und das Popup-Fenster wird angezeigt, wenn der Mauszeiger über das Textfeld bewegt wird. NPR-29853, NPR-29633: Hotfix für GRANITE-26188, GRANITE-26050

**Granite**

* Apache Sling Logging Logger Configuration filtert das eingefügte Skript nicht.  NPR-29775: Hotfix für GRANITE-26051

**Communities**

* Auf der Autoreninstanz gelöschte Gruppen sollten aus den Veröffentlichungsinstanzen entfernt werden. NPR-28933: Hotfix für CQ-4264645
* Das App-Geheimnis sollte durch ein Kennwortfeld geschützt werden, das nicht im Klartext für Social-Verbindungs-Tools angezeigt werden soll. NPR-29728: Hotfix für CQ-4270480
* Besucher und Mitglieder ohne Moderatorberechtigungen können nicht genehmigte/ausstehende Beiträge sehen, indem sie die URL einfügen. NPR-29726: Hotfix für CQ-4271124, CQ-4271441
* Bei der Community-Benutzeranmeldung kommt es zu langsamen Reaktionszeiten von mitunter 40–50 Sekunden. NPR-29678: Hotfix für CQ-4269444

**Übersetzung**

* Benutzer ohne Übersetzungsfunktion sollten nicht auf die Unterseiten zugreifen können. NPR-29644: Hotfix für CQ-4269979
* Benutzerberechtigungen, die nicht als Assistent unterstützt werden, ermöglichen die Erstellung der Übersetzungskopie an einem schreibgeschützten Speicherort. NPR-29375: Hotfix für CQ-4265877

**Benutzeroberfläche - Foundation**

* Die Paginierungsgrenze des Suchergebnisses wurde für die Kartenansicht auf 100 Seiten und für die Listenansicht auf 200 Seiten erhöht. NPR-29332: Hotfix für GRANITE-24644
* Aufgrund des verzögerten Ladens von Tags wird auf der Sammlungsseite nichts angezeigt. NPR-29267: Hotfix für GRANITE-24902
* Die Änderung der Paginierungsgrenze auf 100 anstelle von 40 Triggern führt zu einer zusätzlichen verzögerten Ladezeit ohne Paginierungsanfrage. NPR-29246: Hotfix für GRANITE-25027
* AEM granite password -Feld wird nach der Verschlüsselung nicht ausgefüllt. NPR-29245: Hotfix für GRANITE-24908

**Integration**

* Beim Versuch, die AEM Launch-Konfiguration zu bearbeiten und zu speichern, wird eine Ausnahmemeldung angezeigt. NPR-29086: Hotfix für CQ-4266153
* Anmeldeversuche mit den BrightEdge-Anmeldeinformationen schlagen mit einem Verbindungsfehler fehl.  NPR-29167: Hotfix für CQ-4265872
* Das Kontrollkästchen &quot;Vererbt von&quot;, das auf der Stammebene in Cloud Service-Konfigurationen angezeigt wird, sollte entfernt werden. NPR-27856: Hotfix für CQ-4259676

**Sling**

* Das HTTP-Verbindungs-Timeout wird nicht aus den Konfigurationen gelesen. NPR-29264: Hotfix für SLING-7902
* Das Writeback des JCR-Installationsprogramms bewirkt, dass die OSGi-Konfiguration ein ungültiges Format verwendet und die Neubereitstellung blockiert. NPR-29027: Hotfix für CQ-4264694

**Projekte**

* Benutzer können den Projekt-Workflow nicht abschließen. NPR-29621: Hotfix für CQ-4258791
* Die Liste Projekt-Workflow zeigt leere Zeilen über 40 Workflows hinaus an. NPR-28739: Hotfix für CQ-4264005
* Wenn Sie in Brand Portal die Option &quot;Dynamisches Ausgabeformat&quot;auswählen, wird eine leere ZIP-Datei heruntergeladen. NPR-29420: Hotfix für CQ-4268826
* Die Veröffentlichung von Assets aus dem Ordner &quot;AEM Author /content/dam/mac&quot;in Brand Portal funktioniert nicht. NPR-29820: Hotfix für CQ-4271118
* Die Zeichensetzung im Namen verursacht Probleme mit der Veröffentlichungsschaltfläche. NPR-29573: Hotfix für CQ-4269317
* Asset-Sprachkopie kann nicht über das Referenzbedienfeld erstellt werden. Hotfix für CQ-4269535

**Arbeitsablauf**

* Ein Upgrade von 6.4.2 auf 6.4.4 bricht das Kalenderauswahlfeld des Dialogteilnehmers ab. NPR-29727: Hotfix für CQ-4270423

**WCM - Administrator-Benutzeroberfläche**

* Beim Öffnen der Registerkarte &quot;Berechtigungen&quot;in der Coral2-Implementierung werden die Schaltflächen nicht angezeigt. Hotfix für CQ-4269419

**WCM - MSM**

* Durch das Löschen eines untergeordneten Knotens in einer Live Copy sollte die LiveRelationship getrennt werden. Hotfix für CQ-4270395
* Bei einem Upgrade auf AEM 6.4.3 dauert die Einführung von Multi-Site Manager lange. Hotfix für CQ-4271410

**Schwachstelle**

* CSRF-Schutz-Framework funktioniert nicht mit AEM Foundation-Formularen. NPR-28612: Hotfix für GRANITE-22231

**WCM-Seiteneditor**

* Reflektiertes Cross-Site-Scripting (XSS) bei Verwendung einer ungültigen Auswahl. Hotfix für CQ-4270397

**Formulare**

Die wichtigsten Highlights von AEM 6.4.5.0 sind:

**Forms-Add-on-Paket**

**Adaptive Formulare**.

* (Touch-optimierte Benutzeroberfläche) Die Option Workflow starten wird im Dialogfeld zur Konfiguration nicht angezeigt. NPR-29521: Hotfix für CQ-4269050

**Forms - Backend-Integration**

* Für die On-Premise-Integration von Microsoft Dynamics wurde Unterstützung für ADFS (Active Directory Federation Services) 3.0 ergänzt. NPR-30003, NPR-29484: Hotfix für CQ-4270586
* Der Vorbefüllungs-Dienst schlägt aufgrund der längeren Bearbeitungszeit des AEM Forms-Datenintegrationsmoduls fehl. NPR-28997: Hotfix für CQ-4265988
* Die SOAP-Webservice-Anforderung ist in AEM Forms fehlerhaft. NPR-29013: Hotfix für CQ-4265443
* Beim Testen des SOAP-Dienstes wird keine Fehlermeldung angezeigt, wenn ein falscher Datumswert vorliegt. Hotfix für CQ-4265445

**Forms - Interaktive Kommunikation und Forms - Correspondence Management**

* Die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;(CCR-Benutzeroberfläche) kann eine Gleitkommazahl nicht verarbeiten.  NPR-29210: Hotfix für CQ-4254201
* Die QuickInfo, die auf einer Variablen festgelegt ist, ist nicht in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;(CCR-Benutzeroberfläche) sichtbar. NPR-29739: Hotfix für CQ-4250533
* Es ist nicht möglich, aus Omnisearch in Briefen zu kopieren oder einzufügen. NPR-29808: Hotfix für CQ-4270783

**HTML5-Formulare**

* Wenn wir innerhalb des Textes ein Leerzeichen hinzufügen, kann das Textfeld nicht bis zum Ende gefüllt werden. NPR-28844: Hotfix für CQ-4260239

**Forms JEE-Installationsprogramm**

**Forms – Foundation JEE**

* Die Webdienstkomponente in AEM Forms Workbench kann einen Webdienst nicht aufrufen, was eine bidirektionale SSL-Authentifizierung erfordert. NPR-29485: Hotfix für CQ-4246794
* AEM Forms JEE Configuration Manager funktioniert nicht mit mehreren NIC-Karten. NPR-29236: Hotfix für CQ-4268598
* AEM Startfehler von GemFire: java.lang.IllegalStateException: Es kann nur eine Verbindung mit dem AdminDistributedSystem hergestellt werden. NPR-29524: Hotfix für CQ-4266295
* NoClassDefFoundError aufgrund von nicht übereinstimmenden JAR-Versionen. NPR-28834: Hotfix für NPR-28834

**Forms - Dokumenten-Services**

* Eine ungültige PDF/A-Datei wird mit dem isPDFA-Vorgang als gültige PDF/A gemeldet. NPR-29076: Hotfix für CQ-4261541
* Die Konvertierung einer PDF- in eine PDF/A-1b-Datei schlägt aufgrund eines im Formularfeld nicht vorhandenen Erscheinungsbild-Wörterbuchs fehl. NPR-29534: Hotfix für CQ-4269618
* PDF/A-Konvertierung von PDF, die mit dem Output-Dienst erstellt wurde, lässt die Validierung nicht mit Acrobat DC bestehen. NPR-29647: Hotfix für CQ-4270448
* Das Apache POI-Bundle schlägt mit einer Ausnahme fehl. NPR-27861, NPR-28048: Hotfix für CQ-4245898, CQ-4244778

**Forms – Designer**

* Zusätzliche PDF/UA-Unterstützung für XFA-Formulare (XML Forms Architecture), die mit Designer und Output Service generiert wurden. NPR-23022

**Forms – Workflow**

* Übermittlungen aus Workspace schlagen mit Umlaut fehl. NPR-29087: Hotfix für CQ-4263172

**Enthaltene Feature Packs**

**Assets**

* Unterstützung für Multi-Site-Manager für Assets wurde aktiviert. Weitere Informationen finden Sie unter [Wiederverwenden von Assets mit MSM für Assets](/help/assets/reuse-assets-using-msm.md). NPR-26450: Hotfix für CQ-4259922

**Enthaltene OSGI-Bundles und Inhaltspakete**

Im folgenden Text wird die Liste der im CFP enthaltenen OSGI-Bundles und Inhaltspakete dokumentiert.

Liste der in AEM 6.4.5.0 enthaltenen OSGi-Bundles

[Datei abrufen](assets/6.4.5.0_bundles.txt)

Liste der in AEM 6.4.5.0 enthaltenen Inhaltspakete

[Datei abrufen](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

AEM 6.4.4.0 ist ein wichtiges Update, das Verbesserungen der Leistung, Stabilität und Sicherheit sowie wichtige Fehlerbehebungen und Verbesserungen enthält, die seit der allgemeinen Verfügbarkeit von AEM 6.4 in veröffentlicht wurden. **April 2018.**

Es ist auch kumulativ, was bedeutet, dass 6.4.4.0 alle AEM 6.4 Service Packs umfasst, die zuvor veröffentlicht wurden.

Einige der wichtigsten Highlights von AEM 6.4.4.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.11 aktualisiert.
* Unterstützung für die Zwischenspeicherung der Dienstversion hinzugefügt, um häufige HTTP-Anfragen zur Dienstversion zu vermeiden.
* Unterstützung für das Löschen von automatischen Tags hinzugefügt.
* Es wurde ein endloses Scrollen für den Katalog-Assistenten implementiert.
* Unterstützte Möglichkeit, Berechtigungen gemäß Community-Sites zu beschränken.
* Leistungsverbesserungen (Caching, asynchrone Ausführung, Ausschlussliste) für die Sling Granite Content Health Check.
* Asset-Picker-Schaltfläche zum Dialogfeld &quot;Seitenminiaturansichten&quot;hinzugefügt.
* Neue Eigenschaft hinzugefügt, um die Positionierung von QuickInfos in Feldern zu ermöglichen.
* Verbesserte Unterstützung von ColorPicker im Multifield.
* Es wurde ein Häkchen hinzugefügt, mit dem leere Werte für Zahleneingaben in mehreren Feldern in den Clientlibs von Inhaltsfragmenten ignoriert werden.
* Unterstützung für Microsoft Translator Text API v3 aktiviert.

**Assets**

* Migration der AKP- und Lagerintegration zu AEM 6.4.4.0 NPR-27632
* Wenn Sie später leeren Asset-Ordner mit Unterordnern veröffentlichen, werden die Unterordner ausgeblendet. NPR-27558: Hotfix für CQ-4254701
* Das Hinzufügen der Eigenschaft &quot;Single non-namespaced String\[\]&quot;führt zu unvollständigem XMP Writeback. NPR-26805: Hotfix für CQ-4254142
* Nach dem Rastern der PDF-Eingabedatei fehlen in der erzeugten Ausgabe Bilder. NPR-27929: Hotfix für CTG-4150481
* Der Assistent zum Verschieben von Assets zeigt eine falsche Anzahl von verweisenden Seiten für veröffentlichte Seiten an. NPR-27833: Hotfix für CQ-4258014
* AssetPicker sucht nur das erste Tag, um das Ergebnis beim Filtern mit Tags zu filtern. NPR-27778: Hotfix für CQ-4257705
* AEM OOTB-PDF-Handler bleibt bei der Verarbeitung von PDF mit Fremdzeichen hängen. NPR-28778: Hotfix für CQ-4254234
* Wenn eine CSV-Datei einen Wert enthält, der durch Kommas in einer einzelnen Spalte getrennt ist, AEM CSV-Editor das Komma nicht maskiert und es als separate Spalte behandelt. NPR-28801: Hotfix für CQ-4261694
* Problem mit dem Metadatenschema-Editor bei Verwendung des Pfadbrowsers zur Auswahl von Daten. NPR-28674: Hotfix für CQ-4263005
* Zu viele Assets werden in den Smart Content Service verarbeitet, was zu einer enormen Zeitspanne für den Abschluss des periodischen Tagging-Prozesses führt. NPR-28640: Hotfix für CQ-4262661, CQ-4262644, CQ-4263234
* Desktop-Aktionen funktionieren nicht für Omnisearch-Ergebnisse von `aem/start.html` Seite. NPR-27242: Hotfix für CQ-4248176
* Die Assets-API lässt das Hochladen von Dateien mit mehr als 2 GB nicht zu, wodurch das Hochladen fehlschlägt. NPR-27629: Hotfix für Granite-23590
* Metadaten werden beim ersten Versuch nicht im heruntergeladenen Asset gespeichert, falls Dynamic Media in der Instanz aktiviert ist. NPR-28233: Hotfix für CQ-4260759
* Der Service Resolver wird in der SiteCatalyst-Konfiguration nicht geschlossen. NPR-28015: Hotfix für CQ-4259397
* Das Verschieben von Assets in DAM führt nicht zu einer ähnlichen Verschiebung in Scene7 (p2p-Konfiguration). NPR-28313: Hotfix für CQ-4261091

**Sites**

* (Klassische Benutzeroberfläche) Ein Bruchteil der Live Copies wird in der Rollout-Liste angezeigt. NPR-28598, NPR-28574: Hotfix für CQ-4263410
* LiveRelationshipManagerImpl gibt Ausnahmen aus, wenn cq:Übergeordnet leer oder ungültig ist. NPR-28590: Hotfix für CQ-4263115
* Der vordefinierte Workflow &quot;Löschanfrage&quot;löscht die Seiten nicht ordnungsgemäß. NPR-28668: Hotfix für CQ-4263195
* Die Benutzeroberfläche für den Beziehungsstatus zeigt keine korrekten Jahres- oder Zeitstempelwerte für verwandte Koral-Datepicker-Felder an. NPR-28666: Hotfix für CQ-4263661
* Cross-Site-Scripting (XSS) in SuggestionHandler für 6.4. NPR-28693: Hotfix für CQ-4253821
* Der Ordner von siteadmin wird nicht mehr genügend Arbeitsspeicher zur Verfügung gestellt und AEM nicht verfügbar. NPR-28346: Hotfix für CQ-4261398
* MSM LiveCopy Rollout-Konfigurationen gehen nach der Aktualisierung verloren. NPR-28311: Hotfix für CQ-4258705
* Es kann nicht über 40 Blueprint-Konfigurationen hinaus gescrollt werden. NPR-27640: Hotfix für CQ-4239166
* Die Verwendung von SyntheticResource als Referenz löst eine Nullzeiger-Ausnahme aus und blockiert das Verschieben der Seiten.  NPR-27576: Hotfix für CQ-4258262
* Die PushOnModify-Instanz, die auf 6.1 auf 6.4 aktualisiert wurde, funktioniert nicht beim Löschen. NPR-28108: Hotfix für CQ-4259833
* (Klassische Benutzeroberfläche) Die Schaltfläche Vererbung abbrechen fehlt und die Komponente kann auf einer Live Copy-Seite bearbeitet werden. NPR-28256: Hotfix für CQ-4260161
* OakState0001: Ungelöste Konflikte bei Rollout. NPR-27982: Hotfix für CQ-4259548
* Beim Kopieren/Einfügen einer Struktur, die SyntheticResource-Verweise enthält, endet der Prozess mit dem Fehler 500. NPR-27709: Hotfix für CQ-4259179
* Laufende Workflows können nicht beendet werden, wenn Payloads aktiviert sind. NPR-27672: Hotfix für CQ-4258520
* Rollout zeigt doppelte Rollout-Pfade nach einem Upgrade von 6.1 auf 6.4 an. NPR-27845: Hotfix für CQ-4259487
* Integrieren Sie das dam assetpicker-Modal in die Komponente &quot;Seitenminiaturansichten&quot;. NPR-28131: Hotfix für CQ-108042
* (Klassische Benutzeroberfläche) Dialogfelder mit dem Tag-Widget können nicht geöffnet werden. NPR-28575: Hotfix für CQ-4262680
* Beim Hochladen von Multifield-Dateien wird keine Dropzone angezeigt. NPR-28676: Hotfix für CQ-4263516
* Fehler „Invalid Recursion Selector Value“ bei der Migration einer Komponente von AEM 6.0 auf AEM 6.2. NPR-28609: Hotfix für CQ-4241258
* Der Rich-Text-Editor im Dialogfeld flackert, wenn das Popup-Fenster eines Plug-ins höher ist als der Textbereich, sodass jede weitere Bearbeitung blockiert wird. NPR-27579: Hotfix für CQ-4257440
* (Klassische Benutzeroberfläche) Die Bearbeitung cq:action funktioniert nicht. NPR-28232: Hotfix für CQ-4257703
* Wenn Sie Tags aus dem Bereich für die Asset-Suche des Tags entfernen, wird die Liste nicht ordnungsgemäß aktualisiert. NPR-27983: Hotfix für CQ-4245567
* Wenn die Zahlenwerte für mehrere Felder leer sind, führt das Klicken auf Speichern zu einer endlosen Ladeaufforderung, ohne dass der Vorgang tatsächlich abgeschlossen wird.  NPR-28400, NPR-28393: Hotfix für CQ-4244058, CQ-4244349
* Mit nur Leseberechtigung können Benutzer/Gruppen keine XF auswählen und haben keine Option, die XF und die zugehörigen Seiteneigenschaften anzuzeigen. NPR-28341: Hotfix für CQ-4260412
* Die von Target empfangenen JSON-Daten weisen eine Reihe von Escape-Zeichen auf, die dazu führen, dass die Anwendungsseite beschädigt wird. NPR-28318: Hotfix für CQ-4252043
* Nach der Installation von AEM 6.4.3 kann keine Komponente bearbeitet werden. NPR-28125: Hotfix für CQ-4261216
* Das Löschen aller Tags für ein Tag-Feld wird für ein strukturiertes Inhaltsfragment nicht beibehalten. NPR-28133: Hotfix für CQ-4247241
* Beim Bearbeiten der Eigenschaften &quot;jcr:lastmodifiedby&quot;und &quot;jcr:lastmodified&quot;werden die Werte aktualisiert, ohne dass der Benutzer Änderungen vornimmt. NPR-27847: Hotfix für CQ-4257138
* Die Versionierung von Inhaltsfragmenten vergleicht verschiedene Verbesserungen für AEM 6.4. NPR-27764
* Wenn für /content/experience-fragments keine cq:allowedTemplates definiert sind und allowedPaths auf der Experience Fragment-Vorlage verwendet wird, wird beim Verschieben/Kopieren des Experience Fragment ein Fehler ausgegeben. NPR-27487: Hotfix für CQ-4257489
* Die Schaltfläche Erstellen wird bei der Aktualisierung für den neuen Benutzer angezeigt. NPR-27335: Hotfix für CQ-4255360
* Beim Versuch, eine veröffentlichte Seite zu verschieben, ist die Anzahl der &quot;Verweisenden Seiten&quot;, die auf der ersten Seite des Assistenten &quot;Seite verschieben&quot;angezeigt wird, falsch. NPR-28111: Hotfix für CQ-4259663
* (Touch-Benutzeroberfläche) Die Leiste &quot;Verweise&quot;zeigt keine eingehenden Links an. NPR-28529: Hotfix für CQ-4262306
* Es ist nicht möglich, Komponenten und Seiteneigenschaften nach der Installation von AEM 6.4.3 zu bearbeiten. NPR-27998: Hotfix für CQ-4261216, CQ-4260441
* Migrieren von ContextHub zu jquery 3. NPR-28397: Hotfix für GRANITE-19902

**Commerce**

* Der Katalog kann nicht ausgewählt werden, wenn ein Ordner mehr als 20 Kataloge enthält. NPR-27649: Hotfix für CQ-4258119
* Commerce-Assistenten und Eigenschaftenansichten sind fehlerhaft, da header.referer fehlt. Hotfix für CQ-4261122

**Campaign - Targeting**

* com.day.cq.personalization.impl.TeaserResourceEventHandler wird in eine Endlosschleife versetzt und führt zu Aktualisierungen der Knoten in Veröffentlichungsinstanzen. Hotfix für CQ-4263096

**Replikation**

* Fehler beim Erstellen des Replikationsinhalts com.day.cq.replication.AccessDeniedException. NPR-28314: Hotfix für CQ-4261401
* Sitzungsleck, wenn die Benutzeragent-ID im Replikationsagenten auf &quot;admin&quot;festgelegt ist. NPR-28220: Hotfix für CQ-4255517

**DAM - Creative Cloud**

* Backport-HTTP-API, um ähnliche Bilder aus AEM Assets zu finden. Hotfix für CQ-4254091
* Die AKP-API soll dahingehend erweitert werden, dass die Ergebnisse einer Abfrage auf die Mitglieder einer Kollektion beschränkt werden können. Hotfix für CQ-4258708

**DAM - Formate**

* Nachdem der Metadatenexport ausgelöst wurde, wird die Seite auf eine 404-Seite umgeleitet. Hotfix für CQ-4262447

**DAM - Allgemeines**

* (Adobe Stock Integration) Das Server-Fehlermodal wird mit einem Oauth-Fehler in der Datei error.log angezeigt. Hotfix für CQ-4260406
* Die Adobe Stock-Integration funktioniert nicht, wenn 6.4.4 auf 6.4.3 angewendet wird. Hotfix für CQ-4266009
* Der Link zum CF-Modell fehlt auch nach dem Anwenden des SP3-Patches. Hotfix für CQ-4259029

**Plattform**

* (Klassische Benutzeroberfläche) Die Bearbeitungsschaltfläche ist in der Basisprogrammkomponente nach der Aktualisierung auf 6.4.2 nicht verfügbar. NPR-28560: Hotfix für CQ-4262825
* Wenn Sie eine Abfrage verwenden, die property.operation=like und property.depth kombiniert, führt dies zu einer InvalidQueryException. NPR-28570: Hotfix für CQ-4262652
* Interner Server-Fehler, wenn der neu hinzugefügte Sprachknoten aus dem überlagerten Sprachknoten entfernt wird. NPR-28661: Hotfix für CQ-4239194
* Nullzeiger-Ausnahme in stderr.log im sling-oak-1-Thread bei Zufallsstarts. NPR-28665: Hotfix für CQ-4237845

**Felix**

* webconsole.plugins.memoryusage verursacht einen Deadlock bei der Aktualisierung. NPR-27895: Hotfix für GRANITE-20715

**Granite**

* Die Konsistenzprüfung des Sling-Inhaltszugriffs führt eine lange übermäßige /libs-Überprüfung für den Suchpfad des benutzerdefinierten Ressourcenauflösers durch. NPR-28113: Hotfix für GRANITE-23529

**Inhaltsfragmentverwaltung**

* Verbesserungen der Benutzerfreundlichkeit und Funktionsparität mit Assets für Inhaltsfragmente. Hotfix für CQ-4253883

**Communities**

* Aktualisieren Sie anfällige Bootstrap auf 3.4 und ckeditor-Bibliotheken auf 4.5.11. NPR-28490: Hotfix für CQ-4257511
* Durch Abbruch der Bearbeitungsmodi wird die gelöschte Anlage nicht wiederhergestellt. NPR-27902: Hotfix für CQ-4255150
* Die Komposition im Namen der Box sollte nur für die berechtigten Mitglieder sichtbar sein. NPR-27900: Hotfix für CQ-4251235
* Fügen Sie rep:cache zu Ignorable Nodes in AEM Communities User Sync Listener auf Veröffentlichungsinstanzen hinzu. NPR-27842: Hotfix für CQ-4247234
* Das Suchfeld zeigt Escape-Zeichen auf Benutzeroberflächen-Ebene an. NPR-27838: Hotfix für CQ-4259757
* Fehler wird bei der Suche nach Sonderzeichen wie ( , +,? in der Schnellsuche. NPR-28213: Hotfix für CQ-4260969
* Erstellen Sie eine &quot;Community-spezifische Administratorengruppe&quot;, damit die Benutzer die relevante Community-Site bearbeiten und erstellen können. NPR-27731
* Es wurde eine Logik für das Tastaturereignis zum Öffnen des Videos hinzugefügt. NPR-27726: Hotfix für CQ-4254026
* Aktivierung der Tastaturnavigation für AEM Communities-Komponenten bei der Veröffentlichung. NPR-27728: Hotfix für CQ-4254028
* Es wurde eine aria-Beschriftung für die Listen- und Kartenansichtsschaltfläche hinzugefügt. NPR-27727: Hotfix für CQ-4254027
* Umgang mit Open-Resource-Resolver-Sitzungen in Social - Communities NPR-27721: Hotfix für CQ-4258714

**Übersetzung**

* Unterstützen Sie die Microsoft Translator Text API v3. NPR-28366: Hotfix für CQ-4249755
* jcr:language &amp; cq:language werden nicht automatisch in der übersetzten Sprache aktualisiert. NPR-28338: Hotfix für CQ-4256046
* Zyklische Verweise verursachen StackOverflowError beim Erstellen einer Sprachkopie. NPR-27596: Hotfix für CQ-4255621
* In einem mehrsprachigen Übersetzungsprojekt führt das Klicken auf Speichern und Schließen zu nachfolgenden Seiten, die zum Projekt hinzugefügt werden, dazu, dass neue Projekte erstellt werden, anstatt neue Übersetzungsaufträge in einem vorhandenen Projekt zu erstellen. NPR-28219, NPR-28236: Hotfix für CQ-4261276, CQ-4260731
* Fehlerzeichenfolge beim Hinzufügen von Inhaltsfragmenten mit Massendaten aufgrund der Beschränkung der zulässigen Zeichenanzahl zu lang. NPR-28722: Hotfix für CQ-4262362

**Sozial**

* Kommentare, die auf die nächste Seite gepostet werden, werden bei jedem neuen Kommentar gelb hervorgehoben. Hotfix für CQ-4261359
* Kommentare können nicht mit der API im benutzerdefinierten Inhalt gelöscht werden. NPR-28075: Hotfix für CQ-4261135
* AbstractNotificationOperationService verursacht ClassCastException. Hotfix für CQ-4260456
* Entfernen des Verweises auf die SCORM-Cloud (Shareable Content Object Reference Model) im Player. Hotfix für CQ-4260779

**Benutzeroberfläche - Foundation**

* Die im HTML Client Library Manager integrierte Funktion &quot;Dateisystem-Output-Cache&quot;bricht die Funktion &quot;debugClientLibs&quot;für kompilierte Skripte wie LESS-Dateien ab. NPR-27249: Hotfix für Granite-23313
* Die Anzahl der Assets, die bei Aktivierung des Debug-Modus angezeigt werden, ist immer 1 und viele JS-Fehler werden in der Konsole des Browsers ausgegeben.  NPR-27575: Hotfix für GRANITE-23750
* Das Speichern und Schließen in den Seiteneigenschaften kehrt nicht zur richtigen Seite in AEM WAR mit Tomcat zurück. NPR-27566: Hotfix für GRANITE-23671

**Integration**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` wird in eine unendliche Schleife verschoben und führt bei Veröffentlichungsinstanzen zu Aktualisierungen der Knoten. NPR-28561: Hotfix für CQ-4263096
* Die cq  :actions werden für eine zielgerichtete Komponente nicht berücksichtigt. NPR-27616: Hotfix für CQ-4257497
* Die Aufhebung der LiveCopy-Vererbung funktioniert für zielgerichtete Container nicht ordnungsgemäß. NPR-28129: Hotfix für CQ-4259813
* (Cloud Service Config) Das Kontrollkästchen „geerbt von“ auf der Stammebene sollte entfernt werden. NPR-27856: Hotfix für CQ-4259676

**Sling**

* Aktualisierung auf Sling-Modelle API 1.3.8, Impl 1.4.10. NPR-27636: Hotfix für GRANITE-23537

**OAK - Segmentpersistenz**

* SegmentBufferWriter wird nach OnRC nicht geleert. NPR-27464

**Projekte**

* Das mehrsprachige Übersetzungsprojekt erstellt nicht mehrere Sprachaufträge für Benutzer, die nicht zur Administratorgruppe gehören. NPR-28508: Hotfix für CQ-4262023
* Das ProjectTaskListServlet verlässt einen ResourceResolver, wenn getTaskRenderers während des Dienststarts aufgerufen wird. NPR-27590: Hotfix für CQ-4258011
* Wenn ein Verzeichnis mehr Unterverzeichnisse enthält, als die Seitengröße und die Reihenfolge nach Datum oder Größe beträgt, verhindert ein Fehler, dass über die erste Seite hinaus navigiert wird. NPR-28867: Hotfix für CQ-4265039
* Backport Cross-Site Scripting (XSS)-Fehlerbehebungen in DAM-Viewern. NPR-28106: Hotfix für CQ-4253215
* Es ist nicht möglich, Seiten von Projekt-Administratoren zum Übersetzungsprojekt hinzuzufügen, da der Link zum Hinzufügen neuer Seiten zum Übersetzungsprojekt nicht sichtbar ist. Hotfix für CQ-4266334

**Arbeitsablauf**

* Wenn wir das Dialogfeld &quot;Abgeschlossenes Arbeitselement&quot;in der Workflow-Benachrichtigung öffnen, die über ein Tag-Feld verfügt, wird durch Klicken auf das Kreuz eine Tag-Eigenschaft hinzugefügt. NPR-28304: Hotfix für CQ-4261321
* Schaltfläche zum Umschalten der Benutzerauswahl im Dialogfeld &quot;Aufgabe neu zuweisen&quot;funktioniert nicht. NPR-28963: Hotfix für CQ-4264206

**Formulare**

Die wichtigsten Highlights von AEM 6.4.4.0 sind:

* Unterstützung zum Aufzeichnen von Document Security-APIs zum Signieren und Zertifizieren als Transaktionen hinzugefügt.

**Forms-Add-on-Paket**

**Acrobat Sign-Integration**

* AEM 6.4 Forms Client SDK enthält kein adobesign-recipent -Paket. NPR-27735: Hotfix für CQ-4259372

**Adaptive Formulare**.

* Wenn ein adaptives Formular mit einer leeren Vorlage erstellt wird, können Kunden keine untergeordneten Bedienfelder zum Stammbereich des Formulars erstellen. NPR-28758: Hotfix für CQ-4264157
* Wenn der Wert des Jahres-Felds der Datumskomponente 999 beträgt, schlägt das Überprüfungsskript fehl. NPR-28580: Hotfix für CQ-4262620
* Wenn ein adaptives Formular mit einer leeren Vorlage erstellt wird, können Kunden keine untergeordneten Bedienfelder zum Stammbereich des Formulars erstellen. NPR-28758: Hotfix für CQ-4264157
* Der Wert kann nicht zwischen den Feldern von verzögert geladenen Fragmenten eines adaptiven Formulars festgelegt werden. NPR-27758: Hotfix für CQ-4259703
* Das adaptive Formular verwendet nicht den Rich-Text-Editor, lädt aber seine Bibliotheken.  NPR-27759: Hotfix für CQ-4259193
* Die Umleitung auf URL funktioniert nicht für adaptive Formulare, die in eine AEM Sites-Seite eingebettet sind. NPR-27620: Hotfix für CQ-4239287
* Der Wert kann nicht zwischen den Feldern von verzögert geladenen Fragmenten eines adaptiven Formulars festgelegt werden. NPR-28320: Hotfix für CQ-4262345
* Das adaptive Formular verwendet nicht den Rich-Text-Editor, lädt aber seine Bibliotheken.  NPR-28001: Hotfix für CQ-4259703, CQ-4259193
* Scribble-Signatur funktioniert nicht für AEM Forms App, die auf Apple iOS 12.1 ausgeführt wird. NPR-28497: Hotfix für CQ-4261765
* Übermittlungsaktion mit Problemen beim klassischen Authoring mit &quot;Forms Workflow&quot;in 6.4. Hotfix für CQ-4252740
* Fehlerhandler und Entfernung des TMP-Speichers. NPR-28806: Hotfix für CQ-4264441

**Forms – Korrespondenz-Management**

* Die Benutzeroberfläche für Agenten kann die Originalgröße des Bildes nicht beibehalten. NPR-28800: Hotfix für CQ-4259767
* CCR/Agent-Benutzeroberfläche: Die Beschriftungen der Datumsfelder wurden im Tab Daten verschoben. Hotfix für CQ-4255499

**Forms - Transaktionsberichte**

* Zusätzliche Unterstützung für die Zählung digitaler Signaturen oder das Zertifizieren eines Dokuments als abrechnungsfähige Transaktionen. NPR-28495: Hotfix für CQ-4260236
* Digitale Signatur und Zertifizierung zur Abrechnungsfähigen API hinzugefügt. Hotfix für CQ-4260236

**Forms – Verwaltung**

Es wurde Unterstützung hinzugefügt, um die Verwendung der Handlebars-Client-Bibliothek durch Unterstriche im Beginnüberprüfungs-Assistenten von Forms Manager zu ersetzen und den Asset-Assistenten zu verschieben. NPR-27643: Hotfix für CQ-4246536.
Nach der Installation des Forms Management-Pakets in der Verzweigung Release/640 bleibt ein Bundle im installierten Status. Hotfix für CQ-4265410 Forms, der mit Anhängen in ihnen gesendet wurde, wird nicht im Workflow angezeigt, wenn die Sendeaktion &quot;AEM Forms-Workflow aufrufen&quot;und die Portalübermittlung aktivieren aktiviert ist. Hotfix für CQ-4263110

**Forms - Backend-Integration**

* Testen des Pre/Post-Präprozessors und der benutzerdefinierten Übermittlung mit Client SDK, Hotfix für CQ-4238469 kann nicht durchgeführt werden.

**Forms JEE-Installationsprogramm**

**Forms – Dokumentsicherheit**

* Bei Verwendung des UpdatePolicy-Diensts tritt der Fehler &quot;Objekt kann nicht erzwungen werden&quot;auf. NPR-28751: Hotfix für CQ-4252287
* Signature Build schlägt mit einer älteren Version von commons-pkg fehl. Hotfix für CQ-4265535

**Forms – Foundation JEE**

* Wenn AEM Forms in IBM WebSphere integriert ist, schlägt das Erstellen eines SOAP-basierten Formulardatenmodells fehl. NPR-27923: Hotfix für CQ-4251134
* Das SRT-Tool von PDF Generator kann die installierte Version von Adobe Acrobat nicht erkennen. NPR-27971

**Forms – Designer**

* Einige JPEG-Bilder in einer XDP-Vorlage werden nicht ordnungsgemäß dargestellt.  NPR-26702: Hotfix für LC-3917457

**Forms – Workflow**

* HTML5 Forms mit dem standardmäßigen Sendeprozess in an.lca funktioniert nicht auf JBoss 7. NPR-28675: Hotfix für CQ-4243928
* PDF forms können nicht in HTML Workspace gesendet werden. NPR-28058: Hotfix für CQ-4260373
* Kundendaten werden mithilfe des Forms Workflows &quot;Invoke FDM Service&quot;in Informationsprotokollen gedruckt. Hotfix für CQ-4260385

**Enthaltene Feature Packs**

**Sites**

* Die Versionierung von Inhaltsfragmenten vergleicht die Unterschiede für AEM 6.4. NPR-26760: FP für CQ-4248839
* Verbesserungen der Variantendifferenz von Inhaltsfragmenten für AEM 6.4. NPR-27866: FP für CQ-4248839
* Aktivierte Funktion in OSGi-Konfiguration **AEM Funktionskennzeichnung beim Zurückziehen eines Workflows**. Durch die Aktion zum Zurückziehen sollte die Workflow-Instanz beendet werden, nachdem das Flag gesetzt wurde. NPR-26451: Hotfix für CQ-4259090

**Plattform**

* Die erweiterte Facet-Extraktion von Query Builder nutzt die Oak-API für 6.4. NPR-26674: FP für CQ-4230337

**Enthaltene OSGI-Bundles und Inhaltspakete**

Im folgenden Text wird die Liste der im CFP enthaltenen OSGI-Bundles und Inhaltspakete dokumentiert.

Liste der in AEM 6.4.4.0 enthaltenen OSGi-Bundles

[Datei abrufen](assets/bundles_6_4_4_0.txt)

Liste der in AEM 6.4.4.0 enthaltenen Inhaltspakete

[Datei abrufen](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

AEM 6.4.3.0 ist ein wichtiges Update, das Verbesserungen der Leistung, Stabilität und Sicherheit sowie wichtige Fehlerbehebungen und Verbesserungen für Kunden enthält, die seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht wurden.

Es ist auch kumulativ, was bedeutet, dass 6.4.3.0 alle AEM 6.4 Service Packs umfasst, die zuvor veröffentlicht wurden.

Einige der wichtigsten Highlights von AEM 6.4.3.0 sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.9 aktualisiert.
* Unterstützung für die Eigenschaft allowedPaths in Vorlagen für adaptive Formulare hinzugefügt.
* Erweiterte bereichsbasierte Suche nach Assets in AEM
* Site-übergreifende Skripterstellungskorrekturen (XSS) auf der Anmeldeseite.
* Verbesserte UI-Instrumentierung.
* Verbesserungen bei der Verarbeitung von FormData.
* Die Handhabung der Elementbenennung in einem Multifield wurde verbessert.
* Verbesserte Handhabung von Platzhalterelementen (Karten- und Listenansicht) während der Auswahl.
* Adobe IMS-Authentifizierung und Admin Console-Unterstützung für Managed Services hinzugefügt.

**Assets**

* Der Workflow &quot;DAM-Update-Asset&quot;extrahiert keine Verweise aus INDD-Dateien, wenn die Option IDS-Entschlüsselung aktiviert ist. NPR-26243; Hotfix für CQ-4250933
* Die Erfolgsmeldung wird nicht angezeigt, wenn Assets mit dem Asset-Bulk Editor veröffentlicht werden. NPR-26252; Hotfix für CQ-4251688.
* Wenn Sie ein Asset aus einem Suchergebnis betrachtet haben und im Browser auf die Schaltfläche &quot;Zurück&quot;klicken, wird die Fehlermeldung &quot;Ungültige Anfrage&quot;mit dem Fehlercode 400 angezeigt. NPR 26578; Hotfix für CQ-4253741
* Die Asset-Metadaten zeigen einen ungültigen Namespace-Fehler nach der Installation eines Service Packs. NPR-22341; Quickfix für CQ-4237202
* Die Option zum Neuanordnen von Ordnern und Inhaltsfragmenten in der Listenansicht wird nicht für die entsprechenden Ordner angezeigt. NPR-27153; Hotfix für CQ-4255873
* Benutzer können keine Assets zu einer neuen Sammlung hinzufügen, da dies zu einer Fehlermeldung mit einem fehlerhaften Bild im FehlerPopup-Dialogfeld führt. NPR-22431; Hotfix für CQ-4237086
* Die Dropdown-Liste „Kaskadieren“ wird in dynamischen Dropdown-Listen nicht unterstützt. NPR-27043; Hotfix für CQ-4252564
* Wenn Benutzer in der DMS7-Cloud-Konfiguration einen nicht standardmäßigen Wert für den &quot;Firmen-Stammordner&quot;festlegen, funktioniert die Viewer-Vorgabe nicht wie erwartet. NPR-26360; Hotfix für CQ-4249505
* Die Asset-Berichterstellung schlägt bei Instanzen mit einer sehr großen Anzahl von Assets fehl. NPR-27278; Hotfix für CQ-4256748
* Unterordner übernehmen nicht das Bildprofil SmartCrop des übergeordneten Ordners. NPR-27197; Hotfix für CQ-4256273
* Wenn die Dynamic Media-Integration aktiviert ist, werden einige Metadateneigenschaften von Assets geändert. Die Attribute Breite, Höhe und Position werden nicht angezeigt. NPR-27203 Hotfix für CQ-4256258
* Dynamic Media verwendet den konfigurierten Proxy für einige Asset-Typen nicht. NPR-25211; Hotfix für CQ-4244871
* Die Seite Metadaten-Editor enthält eine Nullzeiger-Ausnahme für ungültige Elementparameter. NPR-26169; Hotfix für CQ-4241368.
* Wenn auf eine Dropdown-Liste eine Auswahlregel angewendet und eine erforderliche Regel angewendet wird, kann die erforderliche Regel im Metadateneditor nicht erfüllt werden. NPR-27479; Hotfix von CQ-4251428

**Sites**

* Ein Benutzer kann die Rich-Text-Editor-Funktionen mithilfe von Content-Richtlinien im Inline-Vollbildmodus steuern, aber die Rich-Text-Editor-Funktionen im Dialogfeld &quot;Bearbeiten&quot;können nicht mit Inhaltsrichtlinien gesteuert werden. NPR-26750: Hotfix für CQ-4241130
* Der Rich-Text-Editor wird beim Wechsel vom Vollbildmodus zum unverankerten Dialogfeld nicht mehr verwendet. Die schwebende Ansicht enthält zwei Rich-Text-Editoren. NPR-25589: Hotfix für CQ-4206008
* Wenn die Eingabetaste (Eingabetaste) in ein Textfeld gedrückt wird, wechselt der Rich-Text-Editor in den Vollbildmodus. NPR-26204: Hotfix für CQ-4245893
* Das Listen-Plug-in des Rich-Text-Editors ist automatisch deaktiviert und lässt keine Änderungen zu. NPR-26507: Hotfix für CQ-4239387
* Wenn dem Rich-Text-Editor-Fenster ein Sonderzeichen hinzugefügt wird, wird das Fenster nach oben gescrollt. NPR-26435: Hotfix für CQ-4249869
* Fragen zum Zwischenspeichern in segment.js in Client Context bzw. Nicht-Zwischenspeichern. NPR-26622: Hotfix für CQ-4253486
* Wenn eine untergeordnete Regel von der Autoreninstanz in die Veröffentlichungsinstanz aktiviert wird, funktioniert die Veröffentlichungsinstanz nicht mehr. NPR-26601: Hotfix für CQ-4253588
* Wenn der Rich-Text-Editor mit mehreren Feldern kombiniert wird, lautet der Fehler „Uncaught TypeError: fieldAPI.getName ist keine Funktion beim Fehler foundation.js“. NPR-27146: Hotfix für CQ-4253155
* Die Salesforce-Integration kann die Proxy-Konfiguration nicht verwenden. NPR-27244: Hotfix für CQ-4245300
* Wenn Sie eine Seite für die Aktivierung mit der Option Veröffentlichung verwalten für ein späteres Datum planen und zur Listenansicht wechseln, fehlt das Kalendersymbol. NPR-26974: Hotfix für CQ-4239206
* Benutzer können in den Seiteneigenschaften keine Berechtigungen für geschlossene Benutzergruppen bearbeiten. NPR-27138: Hotfix für CQ-4256089 Tags können nicht über Tagging bearbeitet werden. NPR-26957: Hotfix für CQ-4254858
* Wenn ein von einem strukturierten Inhaltsfragmentmodell referenziertes Tag verschoben wird, werden die vorhandenen Verweise auf das Tag in einem Inhaltsfragment nicht aktualisiert. Dies geschieht im Bearbeitungsbildschirm des Inhaltsfragmentmodells. NPR-26776: Hotfix für CQ-4251805
* Wenn Sie einen Launch mit mehreren Seiten erstellen und bewerben, werden für jede Seite mehrere Versionen erstellt. NPR-26917: Hotfix für CQ-4254663
* AEM siteadmin behandelt keine Pfade, die in die Adressleiste des Browsers eingegeben werden. NPR-26780: Hotfix für CQ-4254097
* Wenn eine Seite an einen neuen Speicherort verschoben wird, ohne sie umzubenennen, geht der Versionsverlauf der Seite verloren. NPR-26706: Hotfix für CQ-4254025
* URLs im Experience Fragment-Admin-Editor lassen keine Überlagerungen zu. NPR-26319: Hotfix für CQ-4252156
* Wenn eine Seite mit einer Vorlage erstellt und mit einem leeren Experience Fragment veröffentlicht wird, kann die Seite nicht geöffnet werden und es tritt ein DefaultSlingScript-Fehler auf. NPR-26305: Hotfix für CQ-4252460
* Wenn data-sly-use mit Klassen mit identischem Namen verwendet wird, wird nicht obligatorischer Code erzeugt. NPR-27282: Hotfix für Sling-7581
* Nach der Aktualisierung der SP-Installation verfügen die Sites über eine leere Blueprint-Rollout-Konfiguration. NPR-27609: Hotfix für CQ-4257078

**DAM - Brand Portal**

* Tag-Eigenschaften werden nicht veröffentlicht, wenn das Metadatenschema-Formular in Brand Portal veröffentlicht wird. Hotfix für CQ-4256218
* Wenn ein Ordner der dritten Ebene von AEM in Brand Portal veröffentlicht wird, ohne die übergeordneten Ordner zu veröffentlichen, ändert sich der Ordnername. Hotfix für CQ-4255423
* Das Pfad-Browser-Prädikat wird wie erwartet von AEM Assets in Brand Portal veröffentlicht. Der veröffentlichte Pfad bei BP bleibt jedoch /content/dam, der aktualisiert werden muss. Hotfix für CQ-4256240

**DAM - Creative Cloud**

* Das Symbol &quot;Adobe Assets durchsuchen&quot;fehlt im AEM Hauptnavigationsmenü. Hotfix für CQ-4254343

**DAM - DM Client**

* Nach der Aufnahme von Videos in einen Ordner, der mit dem AVS-Videoverarbeitungsprofil verknüpft ist, wird das Browserfenster immer wieder aktualisiert. Hotfix für CQ-4253563
* YouTube Publish schlägt fehl, wenn ein Ad Hoc-Tag verwendet wird, das Großbuchstaben enthält. Hotfix für CQ-4252477
* Wenn eine Anmerkung in einem Asset wie PDF erstellt wird, startet die Benutzeroberfläche eine Endlosschleife für die Seitenaktualisierung. NPR-27052: Hotfix für CQ-4255396

**DAM - DM Services**

* Dynamic Media verwendet den konfigurierten Proxy für einige Asset-Typen nicht. NPR-10727; Hotfix für CQ-4244871

**Plattform**

* Leistungsprobleme mit org.apache.sling.i18n. NPR-26812: Hotfix für SLING-7543
* Die Knoteneigenschaften können nicht angezeigt werden, wenn die Eingabe-XML formatiert und bereitgestellt ist. NPR-26198: Hotfix für CQ-4250448
* IndexOutOfBoundsException in ResourceProviderTracker. NPR-26968: Hotfix für GRANITE-23310
* Die JMX-Konsole fasst zahlreiche Admin-Sitzungen zusammen und alle 5 Minuten wird eine neue Sitzung geöffnet. NPR-26958: Hotfix für CQ-4251090
* Nach der Aktualisierung von 6.2 auf 6.4 zeigt die Protokolldatei die Stapelablaufverfolgung für nicht geschlossene Ressourcen-Resolver com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck an. NPR-26176: Hotfix für Granite-21734
* Wenn ein vordefinierter Dispatcher-Flush-Agent zum Aktualisieren von Aliasen konfiguriert ist, schlägt der Vorgang mit einem StackOverflowError fehl. NPR-26373: Hotfix für CQ-4242928
* Die Replikation verwendet das abgelaufene OAuth-Token, bis es fehlschlägt. NPR-25894
* Eingeschränkte Seite (Seite &quot;Geschlossene Benutzergruppe&quot;) mit Sling: alias leitet den Benutzer nicht zur Anmeldeseite weiter. NPR-25715: Hotfix für Granite=22263
* Beim Veröffentlichen von Tags wird keine Aktivität auf der Benutzeroberfläche angezeigt. Hotfix für CQ-4255961
* Tags können in der klassischen Benutzeroberfläche nicht bearbeitet werden. Hotfix für CQ-4258697
* Aktualisierung von org.apache.felix.http.bridge auf Version 4.0.4. NPR-27038: Backport für Granite - 23334
* Die Aktivitätsprotokolle von Package Manager sollten in einer separaten Protokolldatei extrahiert werden. NPR-27323: Hotfix für Granite-14866
* Der Paketvalidator meldet keine Überlagerungen in CFP. NPR-27119: Hotfix für GRANITE-22825

**Projekte**

* Die AKP-API behandelt Paging nur mit untergeordneten Unterordnern falsch. NPR-27617: Hotfix für CQ-4258639

**OAK**

* Anmeldung beim Repository nach der Installation von AEM 6.4 Service Pack 2 nicht möglich. NPR-27171: Hotfix für Granite-23317

**Replikation**

* Auditprotokoll bleibt offen mit aktiven Sitzungen, die mit rund 750 pro Tag kontinuierlich zunehmen. NPR-27062: Hotfix für CQ-4241350

**Communities**

* Forumsbeiträge und -antworten werden über der zweiten Seite hinzugefügt. Bei Aktualisierung wird der Beitrag an die richtige Position auf der ersten Seite verschoben. NPR-27342: Hotfix für CQ-4247338
* Links zu allen Ressourcen legen den Kontextpfad (/aempublish) nach dem Scrollen ab. NPR-26982: Hotfix für CQ-4254345
* Hinzugefügte Gruppen sind in der Dropdown-Liste Community-Manager, Community-Moderatoren und privilegierte Mitglieder beim Bearbeiten einer veröffentlichten Site nicht sichtbar. NPR-27190: Hotfix für CQ-4258574
* Auf der Seite mit den Aktivierungsressourcen werden nur 10 Gruppen aufgelistet, selbst wenn die Paginierung für die Gruppenauflistung aktiviert ist. NPR-26934: Hotfix für CQ-4252985
* Die Option zum Aktivieren/Deaktivieren der Suche für geplante Beiträge in der Journalkomponente wird in ConfigMgr bereitgestellt und der Auftrag SearchScheduledPosts ist optimiert. NPR-26923: Hotfix für CQ-4250463
* Die Suche nach Keywords in Adressen funktioniert auf der Kalenderkomponentenseite nicht, wenn AEM Community für die Verwendung mit DSRP eingerichtet ist. NPR-26737: Hotfix für CQ-4258493
* Es wurde ein direkter Link zum Kommentar anstelle des Hauptbeitrags in den Details eines Kommentars für die Moderations-Benutzeroberfläche und die Aktivierungsressourcen implementiert. NPR-26704: Hotfix für CQ-4251381
* Inhalte, die über eine Mehrfachauswahl in der Moderationskonsole moderiert wurden, werden nicht im Aktivitäts-Stream angezeigt. NPR-26695: Hotfix für CQ-4253244
* Die Suche mit Vorname und Nachname im Feld &quot;An&quot;von Communities-Nachrichten gibt nicht das erwartete Ergebnis zurück. NPR-26385: Hotfix für CQ-4248673
* Fehler beim Hochladen eines anderen Anhangs als Bild (z. B. .pdf) im Forum. NPR-27360: Hotfix für CQ-4257753
* Wenn Author-Publish mit MySQL DSRP festgelegt ist, funktioniert ein Forumbeitrag nicht, wenn er depoliert oder die Funktion deaktiviert wird. NPR-26125; Hotfix für CQ-4251520
* Sammlungskomponenten (Foren, Blogs, Kalender, Ideen, Fragen und Antworten) verfügen jetzt über eine Eigenschaft im Komponentendialogfeld, um &quot;Block UGC in Author Edit Mode&quot;zu aktivieren/deaktivieren, um das Laden von benutzergenerierten Inhalten im WCM-Bearbeitungsmodus zu ermöglichen/zu verweigern. NPR-26978: Hotfix für CQ-4248161
* Tags Die Suche funktioniert nicht für lokalisierte Suchbegriffe. NPR-26171: Hotfix für CQ-4249926
* Schaltfläche &quot;Zurück&quot;überspringt eine Seite in der Forumsuche. NPR-26950: Hotfix für CQ-4254804
* AEM Instanz, die auf dem standardmäßigen Http-Port (80) ausgeführt wird, kann die imsmanifest.xml nicht erreichen. NPR-27173: Hotfix für CQ-4252211
* Wenn AEM Communities mit DSRP eingerichtet ist, funktioniert das Entfernen der Kommentarzeichen als Antwort für Fragen und Antworten nicht. NPR-26247: Hotfix für CQ-4252232
* Adobe Storage kann nicht aufgerufen werden: 414-Fehler - Lange GET-URI, die beobachtet wird, wenn Benutzer /content/community-components/en/search.html suchen und das Autorenfeld als einen der Filter für diesen Suchbegriff auswählen. NPR-26643: Hotfix für CQ-4251303
* Der Dropdown-Wert für DataCenterURL in der ASRP-Konfiguration wird von Dallas in Virginia geändert (für VA6). NPR-26936: Hotfix für CQ-4254434
* Sonderzeichen in der Forumsuche geben Fehler oder keine Ergebnisse zurück. NPR-26930: Hotfix für CQ-4247744
* Die für &quot;Anzahl der Ergebnisse&quot;in der Forumsuche angezeigte Zahl verwendet ein falsches Trennzeichen für englische und deutsche Gebietsschemata. NPR-27050: Hotfix für CQ-4248939
* Ungelesene Benachrichtigungen steigen nicht über 21 hinaus. NPR-26946, NPR-27480: Hotfix für CQ-4252829, CQ-4256939
* Durch die Paginierung im Abschnitt &quot;Kommentare&quot;einer beliebigen Komponente scrollen Benutzer nach oben, um den Seiteninhalt zu sehen, wenn sie durch Paginierung zu einer Seite gelangen. NPR-27032: Hotfix für CQ-4251228
* Der Community-Site-Ordner kann nicht auf einem Miniaturbild angeklickt werden, wenn er von der Admin Console in der AEM-Autoreninstanz angezeigt wird. NPR-26986: Hotfix für CQ-4254036
* Die Option &quot;Alle Lesezeichen markieren&quot;kennzeichnet nur die ersten 10 Benachrichtigungen als gelesen und andere bleiben bis zur Aktualisierung einer Seite ungelesen. NPR-27037: Hotfix für CQ-4254058
* Die Paginierung wird nicht für &quot;Ideation&quot;ausgelöst und die Liste der Themen (oder Antworten) wird länger, es sei denn, sie werden neu geladen. NPR-26193: Hotfix für CQ-4252104
* Aktivitäten anderer Benutzer wurden gelöscht und UGC wurde beim Anmelden mit Moderatoranmeldeinformationen angezeigt. Am Ende der Profil-URL des Moderators wurde &quot;#social-activities&quot;oder &quot;#tabs-2&quot;hinzugefügt. Hotfix für CQ-4251355
* Alle zugewiesenen Tags können nicht aus einem Blogartikel entfernt werden. NPR-26851: Hotfix für CQ-4253359
* Beziehungen zu UGC werden beim Löschen der benutzergenerierten Inhalte nicht gelöscht. NPR-27630: Hotfix für CQ-4258706
* Link für Antworten funktioniert nicht bei Zeilenklicks auf Forumantworten. NPR-27623: Hotfix für CQ-4256138
* Die Beschränkung für das Benutzerabonnement liegt bei 1000. NPR-27614: Hotfix für CQ-4254689
* Wenn Sie eine Site bearbeiten und Rollen in den Rolleneinstellungen bearbeiten, wird eine Nullzeiger-Ausnahme ausgegeben. NPR-27377; Hotfix für CQ-4255909

**Übersetzung**

* Die Übersetzungsvorschau funktioniert nicht mit dem Beispielinhalt &quot;we.retail&quot;. NPR-26727: Hotfix für CQ-4241179

**Benutzeroberfläche - Foundation**

* Beim Versuch, Konfigurationen nach einem Upgrade auf AEM 6.4 herunterzuladen, wird eine NullPointerException zurückgegeben. NPR-27310: Hotfix für Granite-23573
* Proaktiver Backport für Fehlerbehebungen &quot;granite.platform.login&quot;. NPR-26941
* Proaktiver Backport für granite.ui.content-Korrekturen. NPR-26294
* Die Zahlenfeldkomponente überprüft keine negativen Zahlen in Internet Explorer 11. NPR-26701
* Proaktiver Backport für granite.ui.coralui3-Korrekturen. NPR-26662
* Proaktiver Backport für Fehlerbehebungen granite.ui.coralui3-eon. NPR-26666
* Proaktiver Backport für Fehlerbehebungen granite.ui.foundation.components. NPR-27313
* Proaktiver Backport für granite.ui.commons-Korrekturen. NPR-26753
* Proaktive Unterstützung von Foundation UI Backports. NPR-26248

**Integration**

* Änderungen an AEM Erlebnissen, die über die Targeting-Engine erstellt wurden, werden nicht veröffentlicht. NPR-24869: Hotfix für CQ-4247832
* Es können nicht mehrere Aktivitäten und Erlebnisse erstellt werden, wenn deren Namen japanische Zeichen enthalten. NPR-27271: Hotfix für CQ-4256857
* Aktualisieren Sie den Launch-API-Endpunkt. NPR-26790: Hotfix für CQ-4254380
* (Personalisierung) BrandsRetriever führt den gesamten Baum durch. NPR-27060: Hotfix für CQ-4255790

**WCM - Administrator-Benutzeroberfläche**

* HTTP-Test zum Veröffentlichen/Rückgängigmachen der Veröffentlichung einer Seite mit Verweisen und einem UI-Test für Live Copy hinzugefügt. Hotfix für CQ-4256894

**WCM-Seiteneditor**

* Die Bearbeitungssymbolleiste wird bei der ersten Bearbeitung für Komponenten deaktiviert. Hotfix für CQ-4253270

**Formulare**

Die wichtigsten Highlights von AEM 6.4.3.0 sind:

* Unterstützung für ein Array/eine Liste von Objekten mit dynamischer Entitätsersetzung aktiviert.
* FIPS-Konformität für Reader Extended Workflow in Digital Signature, Reader Extensions, CryptoProvider und TrustStore aktiviert.
* Zusätzliche PDF/UA-Unterstützung für XFA-Formulare, die mit Designer oder dem Output-Dienst generiert wurden.
* Unterstützung für die Eigenschaft allowedPaths in Vorlagen für adaptive Formulare aktiviert.
* Unterstützung von JBoss 7.1.4 für AEM Forms 6.4 hinzugefügt.

**Forms-Add-on-Paket**

**Backend-Integration**

* Zuordnungen von Formulardatenmodellen können nicht basierend auf dynamischen Entitäten in der SOAP-Antwort aufgefüllt werden. NPR-26428: Hotfix für CQ-4250639
* Der Wert für _elementNamespace im Formulardatenmodell für zusätzliche Daten, die über die Test-Benutzeroberfläche eingegeben wurden, wird nicht korrekt in der SOAP-Anforderung widergespiegelt. Hotfix für CQ-4255373
* Eine nullable Eigenschaftsbeschränkung wird mit einem Standardwert initialisiert und kann nicht mit FDM synchronisiert werden. Hotfix für CQ-4253873
* Der Standardwert für die Eigenschaft nullable ist für die OData-Datenquelle nicht auf True festgelegt. Hotfix für CQ-4253870

**Adaptive Formulare**.

* Sites und Formular-Editor können nicht geladen werden. NPR-26977; Hotfix für CQ-4249170
* Probleme beim Hinzufügen einer Anlage zu einem adaptiven Formular mithilfe der Tastatur. NPR-25913; Hotfix für CQ-4249456

**Forms – Interaktive Kommunikation**

* Es ist nicht möglich, ein Bedienfeld zu verschieben, das mit der Option Untergeordnetes Bedienfeld hinzufügen in der Inhaltsstruktur im Webkanal der interaktiven Kommunikation und in adaptiven Formularen hinzugefügt wurde. Hotfix für CQ-4253915
* Im Data Sources-Abschnitt des Druckkanals werden anstelle des Titels der FDM-Zuordnung Tabellennamen angezeigt. Hotfix für CQ-4253669
* Die Funktion isUseXFABullets() ist in der Klasse PrintChannelRenderOptions nicht deaktiviert und ist im Client SDK verfügbar. Hotfix für CQ-4246583, CQ-4252700

**Korrespondenzverwaltung**

* Javadocs für 6.4 enthalten nicht die com.adobe.dbforms.* -Paket und die entsprechenden Klassen. Hotfix für CQ-4253200
* Die CCR-Benutzeroberfläche zeigt einen standardmäßigen Junk-Wert für das Datumsfeld an, falls keine Eingabe aus der XML-Datei mit den Testdaten erfolgt. Hotfix für CQ-4252041
* Wenn ein Brief ein Listenmodul enthält, geht beim Generieren von PDF aus dem Brief der Abstand zwischen Aufzählungszeichen und Text verloren. Hotfix für CQ-4250588

**Forms Manager**

* Unterstützung für die Eigenschaft allowedPaths in Vorlagen für adaptive Formulare aktiviert. NPR-26598: Hotfix für CQ-4255892

**Forms – Workflow**

* Wenn beim Ausführen des Forms-Workflows im Aufgabennamen Klammern enthalten sind, wird in den Protokollen eine Ausnahme angezeigt. Hotfix für CQ-4256626
* Eine Suchvorlage kann nicht in AEM Forms Workspace geöffnet werden. Hotfix für CQ-4255651

**Mobile Forms**

* Die Ausstiegsbenachrichtigung wird beim Verlassen des Datumsfelds in AEM Forms nicht angezeigt, das in Internet Explorer oder Chrome als HTML gerendert wurde. NPR-26483: Hotfix für CQ-4239352
* Die in der XML-Datei enthaltenen Daten bei Beginn der Verarbeitung führen dazu, dass die Formulare einen Validierungsfehler auslösen, wenn der Benutzer versucht, das Formular zu verlassen. NPR-26787: Hotfix für CQ-4251211

**Forms JEE-Installationsprogramm**

**PDF Generator-Dienst**

* Die Standardberichterstellungs- und Compliance-Einstellungen für PDF Generator können nicht angezeigt werden. NPR-26715: Hotfix für CQ-4253384
* Die Binärdatei &quot;convertpdf&quot;fehlt im AIX Forms Add-On-Paket, was beim Aufrufen des PDFA-Dienstes zu einem Fehler führt. Hotfix für CQ-4257873
* Der Papiererfassungsdienst stürzt bei der Verarbeitung von TIFF-Dateien ab. NPR-28079: Hotfix für CQ-4240649

**Document Services**

* Fügen Sie die FIPS-Kompatibilität für den RE-Workflow in Digital Signature, Reader Extensions, CryptoProvider und TrustStore hinzu. NPR-27495: Hotfix für CQ-4257572
* Die Konvertierung schlägt beim Ausführen des AssemblerService.toPDFA-Dienstes in einer Schleife fehl. NPR-26354: Hotfix für CQ-4248656
* Die PDF-Konformität kann nicht ordnungsgemäß anhand von PDF/A-1b-Standards überprüft werden. NPR-26286: Hotfix für CQ-4227539
* Probleme mit ungenügendem Arbeitsspeicher bei der Aktualisierung von AEM Forms von 6.1 SP2 CFP5 auf CFP13. NPR-26285: Hotfix für CQ-4244379
* Die PDF-Konformität kann nicht ordnungsgemäß anhand von PDF/A-Standards überprüft werden. NPR-26272: Hotfix für CQ-4248823

**Forms – Foundation JEE**

* JBoss 7.1.4-Unterstützung für AEM Forms 6.4 hinzugefügt. NPR-27331; Hotfix für CQ-4255601

**Enthaltene Feature Packs**

* Unterstützung für ein Array/eine Liste von Objekten mit dynamischer Entitätsersetzung aktiviert. NPR-26590: Hotfix für CQ-4254655

**OSGi-Pakete und enthaltene Inhaltspakete**

Liste der in AEM 6.4.3.0 enthaltenen OSGi-Bundles

[Datei abrufen](assets/6.4.3.0_bundles.txt)

Liste der in AEM 6.4.3.0 enthaltenen Inhaltspakete

[Datei abrufen](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

AEM 6.4.2.0 ist ein wichtiges Update, das Verbesserungen der Leistung, Stabilität und Sicherheit sowie wichtige Fehlerbehebungen und Verbesserungen enthält, die seit der allgemeinen Verfügbarkeit von AEM 6.4 in veröffentlicht wurden. **April 2018.**
Es ist auch kumulativ, was bedeutet, dass 6.4.2.0 alle AEM 6.4 Service Packs umfasst, die zuvor veröffentlicht wurden.

Zu den wichtigsten Highlights von AEM 6.4.2.0 gehören:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.7 aktualisiert.
* Unterstützung für Funktionen der HTML-Vorlagensprache (HTL) Specification 1.4 hinzugefügt
* Unterstützung für MongoDB Enterprise 3.6 hinzugefügt.
* Der Sites-Seiten-Editor unterstützt jetzt die kontextbezogene Bearbeitung und Komposition mit Client-seitigen Komponenten, die in React oder Angular in Kombination mit <a href="../sites-developing/spa-walkthrough.md">AEM SPA Editor JS SDK</a>.
* Verbesserungen bei Inhaltsfragmenten: Es wurde die Möglichkeit hinzugefügt, Anmerkungen in Textfeldern hinzuzufügen und Versionen nebeneinander zu vergleichen.
* Hinzugefügt [Integration mit Adobe Stock](/help/assets/aem-assets-adobe-stock.md) damit die Benutzer Adobe Stock-Assets direkt über AEM Benutzeroberfläche suchen, in der Vorschau anzeigen, speichern und lizenzieren können. Weitere Informationen finden Sie unter [Verwenden von Adobe Stock-Assets mit AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html?lang=de).
* Assets unterstützen jetzt das dynamische bedingte Metaschema und die Möglichkeit, ein Metadatenschema für Asset-Ordner festzulegen.
* Es wurde eine Konfiguration in jeder Komponente hinzugefügt, um die Funktion zum Erstellen/Aktualisieren von Ordnerminiaturbildern zu aktivieren/deaktivieren.
* Verbesserungen für den Bildeditor bei der Seitenbearbeitung.
* Korrektur einer Regression in Communities für das nicht ordnungsgemäß verarbeitete Scoring-Ereignis, falls ausgewählte Antworten gelöscht werden.
* Die maximale Suchergebnisbegrenzung für Solr wurde auf MAX_INT-10000 überarbeitet.
* Der Vorgang &quot;Transaction Flush&quot;wird nur beim ersten Aufruf von storeTransaction gestartet.
* Die Schaltfläche &quot;Alle auswählen&quot;ist jetzt in der Karten- und Spaltenansicht verfügbar.
* Verbesserungen der Barrierefreiheit in CoralUI.
* Verbesserte Handhabung von Coral.Keys.
* &quot;moment.js&quot;wurde auf Version 2.22.2 aktualisiert.
* jquery wurde auf Version 1.12.1 aktualisiert.
* Die Foundation-Workflow-Status-Komponente wurde eingeführt.
* GCC wurde auf die neueste Version aktualisiert.
* Verschieben Sie SAML in die neue externe IDP-Synchronisierung.

**Assets**

* Die Erstellung von Unter-Assets für die PPTX-Datei enthält keine Bilder und Miniaturansichten. NPR-24286: Hotfix für CQ-4217986
* migrateAllAssets - Fügen Sie Unterstützung für die Stapelverarbeitung hinzu und verbessern Sie AEM -Methode, die alte Assets mit UUID ergänzt. NPR-24861: Hotfix für CQ-4242863 und CQ-4247874
* Leistungsproblem bei der Erstellung von Miniaturansichten. NPR-24693: Hotfix für CQ-4246960
* (Touch-optimierte Benutzeroberfläche) Die Komponente &quot;Options-Eigenschaft&quot;bleibt leer, wenn sie zur Asset Share-Publisher-Seite hinzugefügt wird. NPR-24643: Hotfix für CQ-4245295
* (Workflow) Smart-Tag-Assets werden nicht über die Proxy-Konfiguration verarbeitet. NPR-25840: Hotfix für CQ-4248202
* (Omnisearch) Wenn Sie filetype:image aus Suchkriterien entfernen, wird der Bildtyp nicht entfernt. NPR-25232: Hotfix für CQ-4248280
* Beim Versuch, eine Datei in einen anderen Ordner zu verschieben, werden keine Ordner mit Apostroph in ihrem Namen angezeigt. NPR-25125: Hotfix für CQ-4248660
* Der Regler auf der Seite &quot;Unter-Asset&quot;funktioniert nicht ordnungsgemäß, wenn die Sprachvoreinstellung auf &quot;Englisch&quot;eingestellt ist. NPR-25274: Hotfix für CQ-4248489
* Problem mit Metadaten-Export-CSV-Datei beim Öffnen auf Computern mit europäischem Zahlenformat. NPR-26009: Hotfix für CQ-4250677
* Schaltfläche &quot;Erstellen&quot;ist bei der Auswahl von Asset-Ordnern ohne Berechtigung zum &quot;Löschen&quot;nicht verfügbar. NPR-25788: Hotfix für CQ-4250140
* (Backport) Barrierefreiheitsverbesserungen: Duplicate-id: id-Attributwert muss eindeutig sein, Titel: Formularelemente müssen über Beschriftungen und Link-Name verfügen: Links müssen einen erkennbaren Text enthalten. NPR-24252: Hotfix für CQ-4250905, CQ-4250906, CQ-4250907
* Das Hochladen einer CSV-Datei mit Feldern, die durch &quot;,&quot;getrennt sind, schlägt für europäische Länder fehl. NPR-25549: Hotfix für CQ-4249931
* (Brand Portal) Unter-Assets einer mehrseitigen PDF-Datei werden nicht veröffentlicht, wenn ein Asset veröffentlicht wird. NPR-25991: Hotfix für CQ-4245162
* Veröffentlichen Sie spätere Funktionen für die AEM in der Brand Portal-Replikation. NPR-25911: Hotfix für CQ-109139
* Das Veröffentlichen und Rückgängigmachen der Veröffentlichung der privaten Sammlung durch Benutzer ohne Administratorrechte führt zu einem NPE. NPR-25906: Hotfix für CQ-4250594
* Deaktivieren Sie die Veröffentlichung von Inhaltsfragmenten und Formularschemata in Brand Portal. NPR-24176, NPR-26004: Hotfix für CQ-4251592, CQ-4252026
* (Dynamic Media) DM-Viewer wurden auf Version 5.10.1 aktualisiert, mit der auf der Seite &quot;Bildvorgabe&quot;die Suche nach doppelten Namen aktiviert wird. Siehe Aktualisieren von Dynamic Media-Viewern (5.10.1). NPR-24403: Hotfix für CQ-4247554
* JavaScript-Fehler in der Browser-Konsole in der Spaltenansicht bei der Auswahl eines Assets oder Ordners. NPR-25939: Hotfix für CQ-4250228
* (Spaltenansicht) Aufgaben können nicht identifiziert werden, da die Schlüsseldatei als leerer weißer Eintrag angezeigt wird. NPR-25903: Hotfix für CQ-4246307

**Sites**

* Die Abfrage von datasource.jsp in AEM 6.2 unterscheidet sich von AEM 6.4. NPR-24968: Hotfix für CQ-4244235
* (Klassische Benutzeroberfläche) Seiten können keine Tags hinzugefügt werden. NPR-25255, NPR-25612: Hotfix für CQ-4249615
* HTML Template Language Specification 1.4 verfügt über rückportierte Funktionen AEM 6.4.2.0 NPR-24585
* Falsche Vererbung bei einer lokalen Komponente nach dem Kopieren einer Live Copy-Seite. NPR-25920: Hotfix für CQ-4236737, CQ-4248957
* Die Einschalt-/Ausschaltzeit wird in crx/de gespeichert, ruft jedoch nicht dasselbe in der UI-Konsole für Seiteneigenschaften ab. NPR-25154: Hotfix für CQ-4243431
* Stile Das System unterbricht die ursprünglichen Eigenschaftswerte des Dialogfelds. NPR-25648: Hotfix für CQ-4250073
* Beim Definieren einer Eigenschaft cq:tagName in einem Knoten cq:htmlTag wird der Tag-Name nicht berücksichtigt, wenn die Komponente über JSP eingeschlossen ist. NPR-24154: Hotfix für CQ-4244120
* Bei verschachtelten parsys-Komponenten wird immer das erste (mit dem am wenigsten verschachtelten Pfad) passende Design aus mehreren verfügbaren Komponenten angewendet. Weitere Informationen finden Sie unter [Auflösung des Design-Pfads](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/templates/page-templates-static.html). NPR-24973: Hotfix für CQ-4246276
* Beim Einfügen von Text in eine RTE-Komponente wird ein Popup-Dialogfeld angezeigt, aber nicht ordnungsgemäß gerendert. NPR-24895: Hotfix für CQ-4245901
* (RTE) Leistungsprobleme mit obligatorischem Feldindikator. NPR-24894: Hotfix für CQ-4241895
* (Seitenkomponente) Wenn Sie eine Komponente zu Parsys hinzufügen, wird sie von rechts abgeschnitten und die Breite des Geräterahmens wird entfernt. NPR-25536: Hotfix für CQ-4238224
* Der Plaintext-Editor sendet nicht zugeschnittene Daten und fügt zusätzliche Leerzeichen hinzu. NPR-25312: Hotfix für CQ-4249006
* Beim Öffnen der Komponente im eingebetteten Modus sind zuvor geladene Plug-ins nicht beim zweiten Mal sichtbar. NPR-24610: Hotfix für CQ-4236850
* Das Laden einer XF-Datei in der Editor-Ansicht durch Kopieren/Einfügen lädt die Übergeordnete Variante nicht automatisch. NPR-24841: Hotfix für CQ-4248037
* Eine falsche HTML-Struktur in siteadmin / damadmin bricht IE11. NPR-24686: Hotfix für CQ-4246363, CQ-4248402
* (Veröffentlichungsassistent verwalten) Der Kalender für das Aktivierungsdatum im Schritt Optionen wird nach einigen Aktionen im Schritt Umfang nicht geöffnet. NPR-25681: Hotfix für CQ-4250205
* Die klassische Benutzeroberfläche funktioniert aufgrund der veralteten Version nicht, um CUG zu bearbeiten. NPR-25075: Hotfix für 4241823
* Option nicht verfügbar erstellen, um Experience Fragments zu erstellen. NPR-26053: Hotfix für CQ-4249923
* XF-Varianten werden daher zweimal aktiviert, wodurch doppelte IDs für dasselbe Element generiert werden. NPR-24179: Hotfix für CQ-4245093
* Foundation-Tabelle ist anfällig für Stored Cross Site Scripting. NPR-25185: Hotfix für CQ-4240760
* Fehler &quot;Ungültiger Wert für Rekursionsauswahl&quot;bei der Migration einer Komponente von AEM 6.2.1.13 auf AEM 6.4. NPR-24146

**WCM-Seiteneditor**

* Mehrere gestapelte Parsys aufgrund langwieriger Abfragen (über 6) verlangsamen AEM. Hotfix für CQ-4240247
* JS-Fehler beim Hinzufügen von leerem cq:tagName im Knoten cq:htmlTag . Hotfix für CQ-4251852
* Aktualisieren Sie die bearbeitbaren Aktionen basierend auf der columnClassNames -Umlagerung. Hotfix für CQ-4250781
* Zeigen Sie Ressourcen- und Modellpfade mit einer einzelnen Eigenschaft und einem einzelnen Attribut an. Hotfix für CQ-4251255
* Wiederherstellen von Änderungen durch die API export.json . Hotfix für CQ-4251854
* (Bearbeitbare SPA) Release-Kandidat für 1.0.0. Hotfix für CQ-4251991
* Die Bearbeitungssymbolleiste wird bei der Bearbeitung einer Komponente für andere Komponenten deaktiviert. Hotfix für CQ-4253270

**Integration**

* Die Felder Bibliothek und Download-URL sollten bearbeitbar sein. NPR-24804: Hotfix für CQ-4246864
* Problem mit mehreren DTM-Konfigurationen. NPR-24685: Hotfix für CQ-4247293
* Unterstützung für die asynchrone Bereitstellung für gehostete Client-Bibliotheken hinzugefügt. NPR-25716: Hotfix für CQ-4245745
* Die Targeting-Komponente mit fehlendem entsprechendes Angebot rendert die gesamte Seite und anstelle einer leeren Targeting-Komponente wird eine weitere vollständige Ausgabedarstellung der Seite hinzugefügt. NPR-25273: Hotfix für CQ-4248003
* Die Target-Engine (mbox.js, at.js) verwendet keine verwalteten URLs, und sie verwendet URLs mit Doppelpunkten, die bei bestimmten Bereitstellungen fehlschlagen können. NPR-25339: Hotfix für CQ-4237854
* (Launch)LibraryDownloadProcess speichert den falschen libraryUri-Wert. NPR-25330: Hotfix für CQ-4250006

**Plattform**

* Neuindizierungsschleife | NPE beim Ausführen der BinaryTextExtraction während der ersetzenden Aktualisierung von 6.3 auf 6.4. Hotfix für Granite - 21677
* Grenzüberschreitende Überschreibung des internen markierten Pfads /libs/cq/cloudserviceconfigs/templates/configpage/jcr:content - Problem beim Ausführen des Musterdetektors. NPR-25036: Hotfix für CQ-4248597
* Protokolleinträge, die aufgrund von NPE in LogEntryImpl nicht geschrieben wurden. NPR-25627: Hotfix für Granite-22383
* Die Replikation des Löschereignisses überprüft nicht auf Berechtigungen. NPR-25679: Hotfix für CQ-4241234
* STARTTLS-Unterstützung in &quot;Day CQ Mail Service&quot;hinzugefügt. NPR-25611: Hotfix für CQ-4249924
* Proaktiver Backport für granite.platform.login Korrekturen zur Verbesserung der Barrierefreiheit. NPR-25176: Hotfix für Granite 21746 und Granite-21309
* (AEM 6.4) Fehler beim Neuerstellen und Neuinstallieren des Pakets. NPR-25173: Hotfix für CQ-4247939
* Die standardmäßige MERGE_PRESERVE aclHandling wurde entfernt. NPR-24593: Hotfix für Granite-21889
* Content-Type wird nicht vorgeschlagen und fehlt in der Antwort, nachdem ContentDispositionFilter zweimal angewendet wurde. NPR-24175: Hotfix für Sling-7525
* Der Package Manager-Status ist nach der Aktualisierung auf die AEM 6.4-Verzweigung falsch. NPR-24551: Hotfix für Granite-21750
* AMS-Instanz - Fehlerprotokollanalyse. Hotfix für CQ-4249567

**Sicherheit**

* SAML meldet sich erneut mit Okta IDP auf die Abmeldeseite an. NPR-25523: Hotfix für GRANITE-22364
* Die IMS-Authentifizierung über externe OAK-IDP-OAuth-Provider-Konfigurationen deaktiviert den in AEM erstellten Benutzer. NPR-25301: Hotfix für Granite-22363

**MAC - Test&amp;Target-Integration**

* (Targeting) Fehler der Textkomponente während des Targeting. Hotfix für CQ-4233343

**Communities**

* (Dateibibliothek) Das Herunterladen von Assets mit Leerzeichen aus verursacht Formatprobleme. NPR-24260: Hotfix für CQ-4245159
* Fehlerbehebungen bei mehreren Adobe Social-Problemen. NPR-24247: Hotfix für CQ-4245054, CQ-4245120, CQ-4245296
* Der unbegrenzte Bildlauf für Mitglieder und Gruppen-Konsole schlägt fehl, falls die Autorenveröffentlichung auf unterschiedlichen Kontextpfaden ausgeführt wird. NPR-24437: Hotfix für CQ-4246013
* Der Beitrag kehrt nicht zum Status &quot;Nicht beantwortet&quot;zurück, selbst wenn er aus dem Status &quot;Antworten&quot;entfernt wird, und der Punktstand nimmt nicht ab. NPR-24419: Hotfix für CQ-4245797, CQ-4245932
* Ereignisse, die mit Kalenderfunktionen in Communities hinzugefügt werden, geben falsche Werte aus. NPR-24883: Hotfix für CQ-4244056
* (Community-Forum) Probleme mit dem Seitenladeverhalten und dem Seitenladeverhalten. NPR-24880: Hotfix für CQ-4246109
* (Chrome) Zeitzonenkonversionen schlagen bei Communities-Ereignissen fehl. NPR-24881: Hotfix für CQ-4247115
* Eingebettetes Objekt kann nicht in E-Mail gerendert werden. NPR-24999: Hotfix für CQ-4248022
* Zusätzlich zur UGC-Erstellung sollte die Automatisierungssequenz bei der UGC-Aktualisierung ausgeführt werden. NPR-25892: Hotfix für CQ-4251399
* Reaktionsschnelles modales Dialogfeld für Gruppen. NPR-25623: Hotfix für CQ-4248805
* Solr-Ausnahme wird beim Löschen von Inhalten ausgelöst. NPR-25869: Hotfix für CQ-4248908
* Paginierte Links zu Threads mit vielen Beiträgen funktionieren nicht bei Benachrichtigungen. NPR-25678: Hotfix für CQ-4243038
* Zeitwerte in Suchergebnissen zeigen die Serverzeit anstelle der Zeitzone des Kunden an. NPR-25594: Hotfix für CQ-4248986
* (Forumkommentare) Die Schaltfläche &quot;Browser-Zurück&quot;funktioniert nicht erwartungsgemäß. NPR-25205: Hotfix für CQ-4248573
* (Suchergebnisse) Die Schaltfläche &quot;Browser-Zurück&quot;funktioniert nicht erwartungsgemäß. NPR-25214: Hotfix für CQ-4248574
* Beim Überlagern der Komponente &quot;communityGroupMemberList&quot;wird null zurückgegeben. NPR-25228: Hotfix für CQ-4248523
* (Communities Calendar) ClassCastException wird beim Speichern des Ereignisses mit dem neuen Titelbild generiert. NPR-25167: Hotfix für CQ-4248662
* (Communities) Nachrichten werden abgeschnitten. NPR-25326
* (AEM Publish) Die Scorm-Ressource schlägt mit dem Kontextpfad fehl und zeigt einen leeren Bildschirm an. NPR-26155: Hotfix für CQ-4251942
* (MSRP) Der neu erstellte Kalender wird teilweise gespeichert, indem NPE im Fehlerprotokoll ausgegeben wird. NPR-26071: Hotfix für CQ-4250531
* Die Paginierung von Forum/Themen wird nur aktualisiert, wenn die Seite aktualisiert wird. NPR-26070, NPR-25965: Hotfix für CQ-4249509
* (Frage und Antwort-Forum) Beim Öffnen eines direkten Links zu einem Kommentar kann nicht zur vorherigen Seite navigiert werden. NPR-26069: Hotfix für CQ-4251699
* Das Hochladen von Bildern in Gruppe erstellen funktioniert nicht auf Mobilgeräten. NPR-26172: Hotfix für CQ-4251703
* (Messaging) Bei Verwendung von DSRP wird der Name des Nachrichtenempfängers immer als &quot;Unbekannt&quot;angezeigt. NPR-26056: Hotfix für CQ-4251397
* Die Statusbeschriftung zum Abschluss der Aktivierungs-Scorm-Ressource wird in der Benutzeroberfläche leer angezeigt. NPR-26034: Hotfix für CQ-4249994
* Beim Erstellen einer neuen Community-Gruppe wird eine doppelte Community-Gruppe auf einem aktiven/aktiven mongoMK-Cluster erstellt. NPR-26032: Hotfix für CQ-4245884
* (Autor) Der Assistent zum Erstellen von Gruppen dauert zu lange, um eine Gruppe im Assistenten zu laden/zu erstellen. NPR-26031: Hotfix für CQ-4244966
* Parsys verschwindet beim Hinzufügen einer Include-Anweisung im hbs-Skript. NPR-25908: Hotfix für CQ-4250489
* Wenn Sie „Privilegierte Mitglieder zulassen“ aktivieren, sollten die privilegierten Mitglieder nur Inhalte für Benutzer erstellen können, die Mitglieder der Community sind. NPR-25877: Hotfix für CQ-4248450
* Deeplinks sind zur Aktivierung gesperrt. NPR-25966: Hotfix für CQ-4251478
* Die Paginierung des Forums wird beim Entfernen von Antworten nicht dynamisch aktualisiert. NPR-25970: Hotfix für CQ-4248975, CQ-4252843
* Bei verschachtelten Kommentaren funktioniert der automatische Bildlauf und die Hervorhebung nicht bei Kalender- und Filelib-Ereignissen. NPR-25958: Hotfix für CQ-4251471
* (DSRP) Die Direkt-/Deep-Link-Leistung verschlechtert sich bei hohen Mengen benutzergenerierter Inhalte. NPR-25957: Hotfix für CQ-4251470
* Die Eigenschaften von Allow Privileged Members und Privileged members können nicht geändert werden. NPR-26014: Hotfix für CQ-4244592
* Alle markieren: Durch das Zurücksetzen der Benachrichtigungszähler für alle Community-Seiten werden die Benachrichtigungen zurückgesetzt. NPR-25931: Hotfix für CQ-4248612
* Bearbeiten von ITs schlägt bei DSRP fehl. NPR-25929: Hotfix für CQ-4251382
* E-Mail-ITs schlagen aufgrund von NPE beim Erstellen von E-Mail-Vorlagen fehl. NPR-26039: Hotfix für CQ-4250962
* Foren-Thread-Probleme beim Einbetten von Bildern mit sehr hoher Auflösung. NPR-26037: Hotfix für CQ-4244453, CQ-4253099
* Die Zeit zeigt Switches an, wenn sich die Zeitzone des Servers von der Zeitzone des Benutzers unterscheidet. NPR-26036: Hotfix für CQ-4248751
* Wenn eine Datei mit demselben Namen zweimal an einen Forumsbeitrag angehängt wird, tritt ein Serverfehler auf. NPR-24172: Hotfix für CQ-4244367
* Fehlerkorrekturen für die Backport-Leistung - Gruppenseitenierung bei Autor und Veröffentlichung, Gruppensuche bei Autor, Vermeidung der Serialisierung von Antworten für Journal, Kalender und Ideen sowie verzögertes Laden für die Gruppenmitgliedschaft (Einladen/Aufheben der Einladung) für jede Gruppe beim Anzeigen der Gruppenauflistungsseite. NPR-24538: Hotfix für CQ-4246515
* Aktivierungsressourcen sind in der Autoreninstanz nicht sichtbar. Hotfix für CQ-4252618
* Benachrichtigungen werden nicht für Threads von unbekannten Benutzern generiert. Hotfix für CQ-4245132
* Die Gruppensuche wird nicht in der linken Leiste angezeigt. Hotfix für CQ-4252621
* (Autor) Die Paginierung funktioniert nicht für die Gruppenkonsole. Hotfix für CQ-4242786
* Aktualisierung der jQuery-Benutzeroberfläche. Hotfix für CQ-4248894
* Aktualisieren Sie auf die neueste Version von SCORM 2017.1. NPR-25675: Hotfix für CQ-4240671
* Die Felder &quot;Im Namen erstellen&quot;sind für Benutzer ohne Community-Berechtigung sichtbar. NPR-25331: Hotfix für CQ-4247858
* Der Beitrag ist auch nach dem Löschen auf der Benutzeroberfläche weiterhin sichtbar und gibt in der Konsole einen Fehler aus. NPR-26290: Hotfix für CQ-4252803
* (Site-Einstellungen) Können Änderungen speichern, die an Rollen vorgenommen wurden. NPR-26274: Hotfix für CQ-4252187
* (Sicherheitslücke) Kontoübernahme aufgrund einer JSON Web Token-Fehlkonfiguration. NPR-26458: Hotfix für CQ-4253314
* Die Paginierung wird beim Entfernen von Antworten nicht zurückgesetzt. NPR-26326: Hotfix für CQ-4252997
* Das Anlagenbild wird während der Bearbeitung nicht in Entwürfen angezeigt. Hotfix für CQ-4253360
* Die Seite wird beim Anhängen des Anhangs an die relationale Datenbank (DSRP) nicht aktualisiert. Hotfix für CQ-4253084
* Gruppen funktionieren nicht innerhalb der Website-Ressource &quot;Aktivierung&quot;. Hotfix für CQ-4252975
* Voraussetzungen Lernpfade werden in Aktivierung nicht beibehalten. Hotfix für CQ-4252948

**Arbeitsablauf**

* In der Benutzeroberfläche des Workflow-Starters wird über 41 Starter-Konfigurationen hinaus kein JavaScript-Fehler in der Konsole angezeigt. NPR-25028: Hotfix für CQ-4247604
* Wenn Sie einen alten Workflow bearbeiten, ohne seinen Starter zu bearbeiten, werden mehrere Workflows für jeden Workflow erstellt, der einen Schritt Seite/Asset aktivieren enthält. NPR-25870: Hotfix für CQ-4250896
* Falscher Link in der Workflow-Payload, wenn die Seite über einen Metadatenknoten verfügt. NPR-25916: Hotfix für CQ-4250733

**Übersetzung**

* Fehlerkorrektur - Beim Import eines übersetzten Projekts werden nun zwei Anforderungen zur gleichzeitigen POST ausgeführt, was zu Fehlern führt. NPR-24889: Hotfix für CQ-4247638
* Es wurde behoben, dass beim Erstellen eines Übersetzungsprojekts für mehrere Sprachen alle Seiten für dieselbe Sprache zum selben Auftrag hinzugefügt werden. NPR-25091: Hotfix für CQ-4246112
* Es wurde behoben, dass in einigen Fällen Übersetzungsaufträge nur die 40 oberen Seiten auflisten. NPR-25974: Hotfix für CQ-4248661
* DataPicker-Komponente (Coral2) ändert das Jahr nicht. NPR-24466: Hotfix für Granite-21893

**Benutzeroberfläche - Foundation**

* Proaktive Unterstützung von Foundation UI Backports. NPR-24344, NPR-24345, NPR-25176, NPR-25095, NPR-24332, NPR-25653, NPR-25932, NPR-259 35, NPR-25976
* (Design Importer) Beim Importieren einer Seite wird die js,css-Datei nicht importiert. NPR-25203: Hotfix für Granite-22236
* Proaktive Foundation-UI-Backports zur Verbesserung der Stabilität des Produkts. NPR-24334

**MAC - Test&amp;Target-Integration**

* Die zweite Seite von PersonalizationWizard ( gestartet durch &quot;Targeting starten&quot;) ist leer und gibt Konsolenfehler aus. Hotfix für CQ-4253277

**Experience Fragments**

* Integration von Experience Fragments/Target in AEM 6.4.2.0. Hotfix für CQ-4248653

**Inhaltsfragmentverwaltung**

* Inhaltsfragmentanmerkungen und paralleler Vergleich von Inhaltsfragmentversionen. Hotfix für CQ-4247148

**DAM - Allgemeines**

* Der Filter &quot;Ausgecheckt von&quot;funktioniert bei der Suche nicht ordnungsgemäß. Hotfix für CQ-4247070
* Beim Ausführen des Workflows für die Asset-Aktualisierung werden die Sprachkopie des Assets und die zugehörige Miniaturansicht leer. Hotfix für CQ-4250641
* Duplicate-id: Der Wert des id-Attributs muss eindeutig sein. Hotfix für CQ-4250905
* Titel: Formularelemente müssen über Beschriftungen verfügen. Hotfix für CQ-4250906
* Link-Name: Links müssen einen erkennbaren Text enthalten. Hotfix für CQ-4250907
* Migration der Portordner-Metadatenvorlage JMX und ServiceUserMapping. Hotfix für CQ-4252947
* WebdriverIO Tests, die in der Verzweigung &quot;Version/640&quot;von CQ/dam nicht ausgeführt werden. Hotfix für CQ-4252749
* Links zu verschobenen Assets werden nicht umstrukturiert, wenn der Link veröffentlicht wird. Hotfix für CQ-4245756

**DAM - Viewer**

* Intermittierter Fehler beim Laden von Videos mit neuen Viewern 5.10.1. Hotfix für CQ-4250562

**DAM-Brand Portal**

* Das Rückgängigmachen der Veröffentlichung von Sammlungen in Brand Portal schlägt mit einem Fehler fehl. Hotfix für CQ-4245990
* Die Veröffentlichung von Bildvorgaben in Brand Portal kann nicht rückgängig gemacht werden. Hotfix für CQ-4246140
* Teil-Assets einer mehrseitigen PDF-Datei werden nicht veröffentlicht, wenn ein Asset veröffentlicht wird. Hotfix für CQ-4245162

**DAM - DMClient**

* Beim Veröffentlichen eines Video-Assets in YouTube enthalten die Tags, die zu YouTube führen, den vollständigen Pfad des Tags. Hotfix für CQ-4245549
* (Opt-out- und Opt-in-Upgrades) Problem mit der Viewer-CSS-Umleitung. Hotfix für CQ-4247854
* Viewer-Vorgaben können nicht als Nicht-Mitglied der Gruppe &quot;Administratoren&quot;erstellt/bearbeitet werden. Hotfix für CQ-4247618
* (6.4.1.0) Das Hinzufügen mehrerer Videos in mehreren Parsys unterbricht den Videoplayer. Hotfix für CQ-4248517
* Das Umbenennen und Verschieben von Assets in einem Bildset macht die Bearbeitung unmöglich. Hotfix für CQ-4248434
* Durch Veröffentlichen großer Videos in YouTube werden Zeitüberschreitungsmeldungen ausgegeben. Hotfix für CQ-4237831
* (Listenansicht) Die Benutzeroberfläche der Asset-Auswahl/-Auswahl ändert sich in Graustufen und ist für den Benutzer deaktiviert. Hotfix für CQ-4237817
* (Vertikaler Zoom) CSS wird mit einem 404-Fehler nicht geladen. Hotfix für CQ-4236508
* Der Versuch, ein Asset mit Prozentzeichen (%) im Asset-Namen herunterzuladen, führt zu einem leeren Archiv. Hotfix für CQ-4250558
* (Kartenansicht) Bei Verwendung von &quot;Kopieren und Einfügen&quot;in einem Video-Asset wird keine Verarbeitungsanzeige angezeigt. Hotfix für CQ-4249037
* (Aktualisierung von 6.3.2 auf 6.4) Bildvorgaben vor der Aktualisierung werden auf der Seite Ausgabedarstellungen als &quot;Veröffentlichung rückgängig gemacht&quot;angezeigt, geben aber bei Auswahl keine Schaltfläche mit URL-Adresse zurück. Hotfix für CQ-4240406
* Technische Schulden/geringfügige Verbesserungen. Hotfix für CQ-4240648
* Die Asset-Auswahl (oder Asset-Auswahl) zeigt nicht alle Assets aus den verfügbaren Ordnern an. Hotfix für CQ-4218414
* Bildvorgabe ohne Höhe zeigt Bilder mit falscher Größe an. Hotfix für CQ-4246546
* Die Benutzeroberfläche (Multi-Page Assets) bricht beim Klicken auf Anmerkungen ab. Hotfix für CQ-4251434
* Bei der Aktualisierung von 6.3 auf 6.4 und höher auf die Analytics-Vorgabe wird eine neue Report Suite- und Analysevorgabe erstellt, durch die die älteren Berichtsdaten des Benutzers verloren gehen. Hotfix für CQ-4244529
* (Assistent zum Verwalten von Veröffentlichungen) Die Liste der Assets scheint beim Veröffentlichen oder Rückgängigmachen der Veröffentlichung leer zu sein. Hotfix für CQ-4251881
* Bei der Auswahl von Viewern nach der Anzeige der Set-Mitglieder schlagen AVS-Videos fehl. Hotfix für CQ-4205308
* Für Vorab-Upgrade-Videoverarbeitungsvorgaben kann weder eine neue Videokodierungsvorgabe hinzugefügt noch die vorhandenen Kodierungsvorgaben bearbeitet werden. Hotfix für CQ-4240407
* Bildvorgaben werden nicht auf heruntergeladene dynamische Ausgabeformate angewendet. Hotfix für CQ-4249862
* Die Schaltfläche &quot;Alle auswählen&quot;funktioniert auf der Listenseite &quot;Viewer-Vorgabe&quot;nicht ordnungsgemäß. Hotfix für CQ-4252462
* Videoprofile: Schaltfläche &quot;Alle auswählen&quot;funktioniert nicht. Hotfix für CQ-4253076, CQ-4251447
* SP2 Validation Pass - Smoke Pass. Hotfix für CQ-4251639

**DAM - DMServices**

* Dynamic Media-Ausgabeformate konnten nicht für die EPS-Datei generiert werden. Hotfix für CQ-4243688

**Granite**

* Typo im Bundle SymbolicName führt zu doppeltem Bundle. Hotfix für Granite - 22155
* CUGConfiguration übernimmt CugExclude möglicherweise nicht. Hotfix für Granite - 21109
* Beim Neustart von Adobe Granite Workflow Core werden die Workflow-Schritte von der Mitte aus erneut ausgeführt, sodass unnötige Workflows erstellt werden. NPR-25057: Hotfix für Granite-22218
* JcrResourceBundle unterstützt nicht ordnungsgemäß mehrere Basisnamen. NPR-25245: Hotfix für Granite-22317
* Bei der Installation von Inhaltspaketen werden die ACLs nach Prinzipal gruppiert, sodass das Berechtigungsmodell verletzt wird. NPR-24583: Hotfix für Granite-21591
* Aktualisieren Sie Jetty auf 9.4.11, um Schwachstellen zu beheben. NPR-25030: Hotfix für Granite-22120

**Formulare**

Die wichtigsten Highlights von AEM 6.4.2.0 sind:

* Es wurde eine neue Eigenschaft für Warteschlangen hinzugefügt, die aktualisiert werden soll, ohne den Browser zu aktualisieren.
* Benutzer können nun dieselbe WSDL-Datei für mehrere Dienste verwenden.
* Das nicht unterstützte Zeitstempelmuster wurde aus der Dropdown-Liste &quot;datepicker&quot;entfernt.
* Unterstützung für das Erstellen von xfaf- und pdf-Dateien in OSGI hinzugefügt.
* Unterstützung für die Verwendung der [Transaktionsberichterstellung](https://experienceleague.adobe.com/docs/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) bei lokalen Implementierungen.
* Es wurde Code hinzugefügt, der verhindert, dass untergeordnete Vars im Bedingungsregel-Editor angezeigt werden.

**Forms-Add-on-Paket**

**Transaktionsberichte**

* Aktualisieren Sie die Konfiguration der Transaktionsberichte mit der Wichtigkeit der auf einem Veröffentlichungsserver konfigurierten Rückwärtsreplikation. NPR-26050: Hotfix für CQ-4246650
* Verzögerte Initialisierung des periodischen Flush-Auftrags. NPR-25968: Hotfix für CQ-4245024
* Die Transaktionsaufzeichnung schlägt mit der Nullzeiger-Ausnahme fehl. Hotfix für CQ-4247302

**Forms – Workflow**

* (HTML Workspace) Wenn ein Benutzer eine Aufgabe beansprucht, wird die Anzahl der Warteschlangen für den betreffenden Benutzer aktualisiert, nicht jedoch für andere Benutzer, es sei denn, die Seite wird aktualisiert. Dieses Problem wurde durch eine neue Eigenschaft behoben. Informationen zum Konfigurieren dieser neuen Eigenschaft für Ihre AEM-Instanz finden Sie in den Konfigurationseinstellungen. NPR-24536: Hotfix für CQ-4233665
* Große Formulare können nicht in die AEM Forms App unter 6.4 geladen werden. NPR-24463: Hotfix für CQ-4245091
* Problem in der Mobile Workspace-App beim Versuch, die freigegebene Aufgabe anzuzeigen. NPR-25177: Hotfix für CQ-4248733
* Inkonsistentes Validierungsverhalten zwischen Web und APK. NPR-25670: Hotfix für CQ-4248178
* Wenn ein Webdienst aufgerufen wird und ein HTML5-Formular im Client geöffnet wird, schlägt dies fehl und es wird eine Fehlermeldung zurückgegeben. NPR-26048: Hotfix für CQ-4244716
* Problem beim Aufrufen des Dienstes in AEM Forms Windows App 6.3. NPR-26468: Hotfix für CQ-4252341

**Mobile Forms**

* (Formularsatz) Validierungsproblem bei SSN- und mobilen Feldern bei der Vorschau. NPR-24458: Hotfix für CQ-4244983
* In der HTML-Vorschau werden keine Daten angezeigt, wenn mehrzeilige Felder vorausgefüllt sind. NPR-24549: Hotfix für CQ-4244212
* Daten gehen verloren, wenn das Skript in einem mehrzeiligen Feld ausgewertet wird. NPR-25333, Hotfix für CQ-4249610

**Forms - Interaktive Kommunikation und Correspondence Management**

* Die Synchronisierung schlägt auf IC mit der grundlegenden Vorlage und der Referenz-IC-Druckvorlage fehl. NPR-24912
* (CCR) Validatoren funktionieren nicht für Felder/Variablen. Hotfix für CQ-4245047
* Das Symbol Datenmodellobjekt wird gelegentlich in der Symbolleiste &quot;Textbearbeitung&quot;ausgeblendet. Hotfix für CQ-4245122
* Ausnahmeprotokolle werden auf der kopierten IC angezeigt, wenn die ursprüngliche IC gelöscht wird. Hotfix für CQ-4249378
* In der Briefausgabe wird die Bedingung nicht als &quot;true&quot;ausgewertet, selbst wenn die Daten korrekt sind. Hotfix für CQ-4245944
* Automatisch generierte Komponenten werden bei Auswahl aus der Inhaltsstruktur nicht hervorgehoben. Hotfix für CQ-4246178
* Probleme beim Öffnen des Webkanal-Vorlageneditors. Hotfix für CQ-4248182
* Die Reihenfolge der hinzugefügten Assets kann nicht geändert werden, da die Pfeile nach oben/unten deaktiviert bleiben. Hotfix für CQ-4252042
* Eigenschaften des Bedingungsmoduls können nicht aktualisiert werden. Hotfix für CQ-4247909
* Das UX des Dialogfelds &quot;Vererbung abbrechen&quot;, wenn der Benutzer ein Objekt im Webkanal neu anordnet, muss verbessert werden. Hotfix für CQ-4241076
* Daten im Brief, die den in XDP definierten Bindungen entsprechen, werden bei Verwendung der direkten Brief-URL nicht aufgefüllt. Hotfix für CQ-4245833
* (Caching-Problem) Die Synchronisierung des Webkanals spiegelt keine Änderungen an Layout-Fragmenten, Textfragment des Druckkanals wider. Hotfix für CQ-4251460
* Layout-Fragmente und DD-Eigenschaften können nicht aktualisiert werden. Hotfix für CQ-4247830
* (CCR) Das Neuladen von Entwürfen schlägt aufgrund der XML-Analyse fehl. Hotfix für CQ-4250950
* (IC Editor) Die Schaltfläche &quot;Fragment bearbeiten&quot;sollte besser auffindbar sein. Hotfix für CQ-4244694
* (XDP) Beim Hinzufügen eines Layout-Fragments zum neu erstellten Teilformular wird ein leerer Bildschirm angezeigt. Hotfix für CQ-4248810
* Testfehler &quot;DocumentFragment-Übergeordnet-DeployWithServerSideTests&quot;. Hotfix für CQ-4245496
* Instanz der Textmodulvariablen, die im Bedingungsmodul dupliziert wird. Hotfix für CQ-4252128
* Die PDF-Vorschau-URL zeigt keine Transaktionsberichte bei der Veröffentlichung an. Hotfix für CQ-4246158
* Probleme mit der IC-Synchronisierung bei der Synchronisierung von Druckkanälen mit Webkanälen. Hotfix für CQ-4251505
* EXM-Code-Bereinigung: Entfernen Sie LocalFunctionMapper. Hotfix für CQ-4243265
* Korrigieren des Ressourcentyps von TableHeader der WebChannel-Tabellenkomponente von IC. Hotfix für CQ-4251821
* (IC Editor) Probleme mit der Benutzerfreundlichkeit. Hotfix für CQ-4241081
* Das Teilformular &quot;Druckkanal&quot;weist keine Einfügefunktion auf. Hotfix für CQ-4252994
* Die Synchronisierung von Änderungen beibehalten schlägt nach dem Entfernen des FDM-Knotens oder Variablenplatzhalters fehl. Hotfix für CQ-4253178
* (Vorlagen-Editor) Eine einfache Vorlage zeigt zusätzliche Drag-Drop-Bereiche für Kopf- und Fußzeilen und das Flackern des Bildschirms beim Öffnen des Webkanals an. Hotfix für CQ-4253323
* Automatisch generierte Komponenten werden bei der Auswahl aus der Inhaltsstruktur nicht hervorgehoben. Hotfix für CQ-4246178

**Document Services**

* (Form Service) OSGI bietet keine Unterstützung für XFAF. NPR-25181, Hotfix für CQ-4251313
* Die Zeichen in der Überschrift der assemblierten PDF-Datei werden bald unleserlich. NPR-25113: Hotfix für CQ-4244682

**Adaptive Formulare**.

* &quot;Übermittlungsaktion&quot;als &quot;Senden-Mail&quot;gibt eine Ausnahme aus, wobei CC/BC-Felder leer sind. NPR-25019: Hotfix für CQ-4243039
* Die OOTB-AEM Formular-Komponente kann aufgrund ineffizienter Abfragen nicht verwendet werden. NPR-25065: Hotfix für CQ-4247256
* Entfernen Sie sling:orderBefore aus Dialogknoten von guideImageChoiceComponent. Hotfix für CQ-4245013
* (Datumsauswahl) Das Bearbeitungsmuster unterstützt nicht zwei Arten von Zeitstempelmustern. Hotfix für CQ-4237982
* Übermittlungsaktion mit &quot;Forms Workflow&quot;Classic-Authoring-Problemen. Hotfix für CQ-4236981
* (Webkanal) Das IC-Diagramm sollte die Eigenschaft colspan aus dem AF-Diagramm übernehmen. Hotfix für CQ-4252143

**Backend-Integration**

* (SOAP-Anforderungen) Große Dezimalstellen (mehr als 6 Stellen) werden in exponentieller Notation dargestellt, was zu einem Validierungsfehler führt. NPR-25283: Hotfix für CQ-4248100
* Falsche Validierung von optionalen Parametern, die in komplexen Typen definiert sind. NPR-25070: Hotfix für CQ-4247107
* Benutzer können nun dieselbe WSDL-Datei für mehrere Dienste verwenden. NPR-24604, Hotfix für CQ-4247756
* FDM mischt die Reihenfolge der Parameter in seinen SOAP-Aufrufen. NPR-25069, Hotfix für CQ-4247180
* FDM führt Entitäten (in Liste/Array) in der SOAP-Anforderung zusammen. NPR-25284: Hotfix für CQ-4248375

**Forms JEE-Installationsprogramm**

**PDFG Service**

* Die Funktion zum Erstellen/Ändern von Sicherheitseinstellungen funktioniert nicht. NPR-24769: Hotfix für CQ-4246927
* Optimizen PDF durch selektives Aufheben der Einbettung von Schriftarten über einen einzigen API-Aufruf. NPR-23287

**Document Services**

* Der Output-Dienst stellt nicht die richtigen Tags für Barrierefreiheit-Reader bereit. NPR-24438, NPR-24439, NPR-24440, NPR-24441: Hotfix für CQ-4243849, CQ-4243845, CQ-4243852, CQ-4243853

**Document Security**

* Problem mit der Richtlinienerstellung mit Document Security. NPR-25586, NPR-25547: Hotfix für CQ-4247086

**Forms – Foundation JEE**

* Prozesse, die zeitweise als Systemkontextkonto ausgeführt werden. NPR-25289, NPR-25313: Hotfix für CQ-4249331
* AEM Forms JEE wurde von der Sicherheitswarnung zur Datenbindung von Apache Struts und Jackson beeinflusst. NPR-25628: Hotfix für CQ-4242891
* Der Prozess für E-Mail-Startpunkte funktioniert nicht. NPR-25253: Hotfix für CQ-4248518

**Enthaltene Feature Packs**

**Assets**

* Hinzugefügt [Integration mit Adobe Stock](/help/assets/aem-assets-adobe-stock.md) damit Benutzer Adobe Stock-Assets direkt über AEM Benutzeroberfläche suchen, in der Vorschau anzeigen, speichern und lizenzieren können. Weitere Informationen finden Sie unter [Verwenden von Adobe Stock-Assets mit AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html?lang=de). NPR-15779: Hotfix für CQ-30857
* Unterstützung für dynamisches bedingtes Metaschema hinzugefügt. Weitere Informationen finden Sie unter [Kaskadierende Metadaten](/help/assets/cascading-metadata.md). NPR-25189: Hotfix für CQ-4237413
* Die Option &quot;Asset-Download&quot;für Inhaltsfragmente wurde aktiviert. Weitere Informationen finden Sie unter [Asset-Berichte](/help/assets/asset-reports.md). NPR-25186: Hotfix für CQ-4237410
* Möglichkeit zum Festlegen eines Metadatenschemas für Asset-Ordner. Weitere Informationen finden Sie unter [Ordner-Metadatenschema](/help/assets/folder-metadata-schema.md) und referenzieren sie [Konfigurationseinstellungen](#configuration-settings-required-for-npr) Post-AEM 6.4.2.0-Installation. NPR-21268: Hotfix für CQ-4221574

**Sites**

* Erlauben Sie die Bearbeitung eines Inhaltsfragments ohne Löschberechtigungen. Weitere Informationen finden Sie unter [Anpassen und Erweitern von Inhaltsfragmenten](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments-delete.html). NPR-25793: Hotfix für CQ-4248750
* Die Funktion zum Kommentieren von Inhaltsfragmenten wurde hinzugefügt. Weitere Informationen finden Sie unter [Varianten-Authoring-Fragmente](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments-variations.html#annotating-a-content-fragment). NPR-25188: Hotfix für CQ-4235336
* Versionierung: Vergleichen Sie Inhaltsfragmente nebeneinander. Weitere Informationen finden Sie unter [Verwalten von Inhaltsfragmenten](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments-managing.html#comparing-fragment-versions). NPR-25187: Hotfix für CQ-4237412
* Verbesserungen am Bildeditor, rückportiert auf AEM 6.4.2.0. Weitere Informationen finden Sie unter [Bildeditor](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/image-editor.html). NPR-24467

**OSGi-Pakete und enthaltene Inhaltspakete**

Liste der in AEM 6.4.2.0 enthaltenen OSGi-Bundles

[Datei abrufen](assets/6.4.2.0_bundle-list.txt)

Liste der in AEM 6.4.2.0 enthaltenen Inhaltspakete

[Datei abrufen](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

AEM 6.4.1.0 ist ein wichtiges Update, das Verbesserungen der Leistung, Stabilität und Sicherheit sowie wichtige Fehlerbehebungen und Verbesserungen für Kunden enthält, die seit der allgemeinen Verfügbarkeit von AEM 6.4 im April 2018 veröffentlicht wurden.

AEM 6.4.1.0 kann auf AEM 6.4 GA installiert werden. Einige der wichtigsten Highlights des Service Packs sind:

* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.3 aktualisiert.
* Es wurden optimierte Smart-Tags eingeführt.
* Fehlerbehebungen in der Design-Auswahl, Tag-Auswahl (ändern Sie die Quell-VM und Ziel-VM in auto.)
* Unterstützung für TypeHint zum Speichern von Werten als Zeichenfolge hinzugefügt.
* Unterstützung für SMTP über TLS in Mail Service hinzugefügt.
* Korrektur zur Proxy-Handhabung für die HTTP-Weiterleitung in DMS7.
* Aktualisierung auf /etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js Version 1.3.
* Fehlerbehebungen in DMHybrid Opt-out- und Opt-IN-Paketen.
* Fehlerbehebungen beim smarten Zuschneiden.
* Die OOTB-Konfigurationswerte wurden an den neuen Speicherort migriert ( von /etc zu /conf).
* Den Kundeneinstellungen auf Versandservern wurden Farbprofile hinzugefügt.
* Migration der Image-Server-Einstellungen aus /etc —&amp;gt; /conf.
* Quellinhaltsfragment zur Übersetzung hinzugefügt.
* ARIA-Unterstützung für Print und PrintDialog hinzugefügt.
* Unterstützung für E-Mail-Validierungs-ARIA hinzugefügt.
* Proaktiver Backport für Fehlerbehebungen &quot;platform.clientlibs&quot;.
* Vermeidung der automatischen Ausführung von Skripten, wenn keine Eingabe für den expliziten dataType vorhanden ist (löst CVE-2015-9251 auf).

**Assets**

* Beim erneuten Öffnen der Asset-Eigenschaftenseite wird ein leerer Dropdown-Wert für kaskadierende Elemente angezeigt. NPR-23042: Hotfix für CQ-4238761
* Freigegebene Links auf der Seite &quot;mylinkshare&quot;und Links zur Seite stehen Benutzern ohne Administratorrechte nicht zur Verfügung NPR-23044: Hotfix für CQ-4239004
* Um eine Nullzeiger-Ausnahme im Workflow &quot;DAM-Asset-Update&quot;in 6.4.0 zu verhindern. NPR-24134: Hotfix für CQ-4244972
* Die veröffentlichte WCM-Seite zeigt Platzhaltersymbole für Hotspots, fehlende CSS-Dateien mit 403-Fehler für OOTB-Viewer. NPR-23041: Hotfix für CQ-4233716
* (Detailansicht) Die Funktion &quot;Nächste/Zurück-Navigation&quot;hinterlässt eine DIV-Überlagerung im Vorschaubereich für dynamische Ausgabedarstellungen, die den Zugriff auf den Viewer blockiert. NPR-23043: Hotfix für CQ-4238499
* Die CMYK-Bildausgabe weist eine falsche Sättigung auf. NPR-23048: Hotfix für CQ-4235470
* XMP Metadatenextraktion durch Scene7ListInfoProvider ist ressourcenintensiv. NPR-23754
* (dam-delivery) Die HTTP-Weiterleitung entspricht nicht den HTTP-Proxy-Einstellungen. NPR-24002: Hotfix für CQ-4244140

**Sites**

* Wenn wir die Seite umbenennen, während wir verschieben, ist das Verschieben der Seite erfolgreich, aber die Umbenennungsfunktion funktioniert nicht. NPR-22923: Hotfix für CQ-4235907
* Fehler beim Veröffentlichen einer Live Copy-Seite, die auf eine Importer-Seite in Adobe Campaign verweist. NPR-23053: Hotfix für CQ-4237164
* Das Verschieben/Umbenennen in der klassischen Benutzeroberfläche schlägt mit dem Fehler &quot;Beim Verschieben der Seite ist ein Fehler aufgetreten&quot;fehl und es wird nicht umbenannt. NPR-23051: Hotfix für CQ-4235907
* Beim Wechseln von Inhalt aus der Spaltenansicht in die Listenansicht wird eine leere Seite gerendert und für Seiten mit OffTime und OnTime wird eine Nullzeiger-Ausnahme Trigger. NPR-22968, NPR-23052: Hotfix für CQ-4238940

**Commerce**

* Fehlerbehebung beim Testfall mit Hobbes-Kernkomponenten (CQ/Commerce-Modul). Hotfix für CQ-4253494

**Schwachstelle**

* Die Salesforce-Integration ist anfällig für Server-seitige Anforderungsfälschung (SSRF, Server Side Request Forgery). NPR-24289: Hotfix für CQ-4245277
* Server Side Request Forgery (SSRF) und Cross-Site Scripting (XSS) in ReportingServicesProxyServlet. NPR-24657: Hotfix für CQ-4246880
* Site-übergreifendes Scripting (XSS): Wird in Commerce createcatalogwizard.html/content dargestellt. NPR-24642: Hotfix für CQ-4237017
* Cross-Site-Scripting (XSS) in Verknüpfungen zum Admin-UI-Projekt. NPR-23272: Hotfix für CQ-4241795

**WCM - Foundation-Komponenten**

* Das Öffnen der Design-Auswahl führt zu einer Nullzeiger-Ausnahme. NPR-23047: Hotfix für CQ-4238736

**Benutzeroberfläche**

* (Coral3 Datepicker) Fügen Sie Unterstützung für typeHint hinzu, um Werte als &quot;Zeichenfolge&quot;zu speichern. NPR-23398: Hotfix für Granite-21194
* Internationalisierungs-Übersetzung funktioniert nicht auf sprachlicher Ebene. NPR-22967, NPR-23046: Hotfix für Granite-21111
* Proaktiver Backport für granite.ui.commons-Korrekturen. NPR-23537
* Proaktiver Backport für granite.ui.content-Korrekturen. NPR-23535
* Proaktiver Backport für granite.ui.coralui-Korrekturen. NPR-23538
* Es können nicht mehrere Benutzer gleichzeitig aus der Gruppe entfernt werden. NPR-23846
* (OMEGA) Bericht &quot;Funktion&quot;nur auf Englisch. NPR-23989: Hotfix für Granite-21231
* (Design Importer) Beim Importieren einer Seite wird die js, css nicht importiert. NPR-25203: Hotfix für Granite-22236

**Integration**

* Ungeschlossener ResourceResolver in com.day.cq.analytics.sitecatalyst. NPR-22340: Hotfix für CQ-4236515
* TargetContentImpl verlangsamt AEM bei langwierigen Abfragen. NPR-22359: Hotfix für CQ-4236907
* Die Target-Engine (mbox.js, at.js) verwendet keine verwalteten URLs, und sie verwendet URLs mit Doppelpunkten, die bei bestimmten Bereitstellungen fehlschlagen können. NPR-22434: Hotfix für CQ-4237854
* Im Target-Modus können Autoren eine aus der Blueprint geerbte Komponente ändern, ohne die Vererbung abzubrechen. NPR-22865: Hotfix für CQ-4237907
* (Personalisierung) Beim Wechseln zur Kartenansicht werden Symbole angezeigt. NPR-23373, NPR-23374: Hotfix für CQ-4240018, CQ-4240019
* (Personalisierung) Die Zielgruppenkonsole zeigt keine nt:folder-Typen an. NPR-23375: Hotfix für CQ-4242293
* Wenn eine Komponente auf eine Veröffentlichungsinstanz ausgerichtet ist, erscheint ein Flackern, das das Standarderlebnis vor dem zielgerichteten anzeigt. NPR-23415: Hotfix für CQ-4242038
* (Adobe IMS-Konsole) Die OSGi-Dienstkonfiguration AccessTokenProvider wird nach dem Löschen erneut angezeigt. NPR-23520: Hotfix für CQ-4208250
* Die Replikation der Konfigurationsreferenzen mit der Zwischenordnerstruktur schlägt fehl. NPR-23485: Hotfix für CQ-4242751
* clientlib (Personalisierung), die vom Proxy-Servlet blockiert wird. NPR-23521: Hotfix für CQ-4240995
* (Adobe IMS-Konsole) Registrierte Cloud-Lösungen werden nicht im Konfigurationsassistenten abgerufen. NPR-23977: Hotfix für CQ-4244549
* Endlosschleife beim Laden zielgerichteter Inhalte auf Seiten ohne HTML-Erweiterung. NPR-23522: Hotfix für CQ-4223600
* Die Aktivierung schlägt für eine Seite mit vererbten Dynamic Tag Management-Konfigurationsverweisen fehl. NPR-23485: Hotfix für CQ-4242751

**Plattform**

* (Klassische Benutzeroberfläche) (Touch-Benutzeroberfläche) Die Tag-Auswahl wird nicht angezeigt und gibt eine Ausnahme aus, wenn versucht wird, über ein Tag-Prädikat im Asset-Suchschema nach Tags zu suchen. NPR-23049: Hotfix für CQ-4239371
* (Klassische Benutzeroberfläche) Komponenten, die xtype=tags verwenden, geben null zurück und können nicht aus der eth-Liste der Tags ausgewählt werden. NPR-23050: Hotfix für CQ-4239937
* (Branding) Im Dialogfeld &quot;Opt-in&quot;wird Adobe Marketing Cloud anstelle von Adobe Experience Cloud erwähnt. NPR-23210: Hotfix für CQ-4237799
* Die Filteroption verlangsamt AEM nach der Aktualisierung von 6.3 auf 6.4. NPR-23260: Hotfix für CQ-4239847 (zu überprüfen)
* Proaktiver Backport für Fehlerbehebungen granite.omnisearch.core. NPR-23536
* Proaktiver Backport für Fehlerbehebungen &quot;platform.clientlibs&quot;. NPR-23569
* Die Vererbung der Cloud Service-Konfiguration wurde beim Bearbeiten anderer Seiteneigenschaften unterbrochen. NPR-23216: Hotfix für CQ-4239782
* STARTTLS-Unterstützung in Day CQ Mail Service aktiviert. NPR-23941: Hotfix für CQ-4240397

**Projekte**

* (Inhaltsfragment) Die Sprachkopie für eingebettete Assets wird nicht erstellt, während englisches Asset zur Übersetzung hinzugefügt wird. Hotfix für CQ-4243477
* Das Dropdown-Menü msft config zeigt die Konfiguration von /libs(6.4-Konfigurationen) anstelle von /etc(6.3-Konfigurationen) im alten Modus an. Hotfix für CQ-4243475
* Automatische Weiterleitung und Löschung von Übersetzungsstarts in Übersetzungsprojekten Hotfix für CQ-4243474
* Inhaltsfragment innerhalb von Sites wird nicht übersetzt. Hotfix für CQ-4243482, CQ-4243483, CQ-4245687
* Serverfehler beim Öffnen des Suchfilters für Übersetzungsaufträge. Hotfix für CQ-4236813
* Das Dropdown-Menü für die Konfiguration von Berechtigungen ist leer, selbst wenn tif in /conf/we-retail vorhanden ist. Hotfix für CQ-4236315
* Projekt-KPI öffnen: Leistungsbeeinträchtigung, da mehr Projekte erstellt werden. NPR-23840: Hotfix für CQ-4238392
* Workflow Starter kann den TypeHint-Wert „Zeichenfolge“ nicht akzeptieren. NPR-23863: Hotfix für CQ-4238356

**Communities**

* Sicherheitslücken in Version 1.0 von Handlebars. NPR-23636: Hotfix für CQ-4243055
* Massenzulassen von gekennzeichneten Nachrichten funktioniert nicht. NPR-23867: Hotfix für CQ-4243962
* Der Standardwert wird bei der Sortierungsschaltfläche in der Forumkomponente nicht angezeigt. NPR-23882: Hotfix für CQ-4243375
* Probleme beim Nachrichtenversand von Community-Sites an Gruppen. NPR-23935

**Arbeitsablauf**

* Der E-Mail-Benachrichtigungs-Service des Day CQ-Workflows löst eine E-Mail pro Mongo-Knoten für WorkflowCompleted- und WorkflowAborted-Benachrichtigungen aus. NPR-22515: Hotfix für CQ-4238172
* Beim Ausführen des Workflows für das DAM-Update-Asset wird eine NullPointerException ausgelöst. NPR-23010: Hotfix für Granite-21096
* Workflow-Prozessschritt zeigt keine Skripte aus /etc/workflow/scripts an. NPR-23263: Hotfix für Granite-20775
* Workflow Dynamic Participant Step zeigt keine Skripte aus /apps/workflow/scripts an. NPR-23464: Hotfix für Granite-21276
* Workflow kann nach der einmaligen Bearbeitung nicht mehr bearbeitet werden. NPR-23742: Hotfix für CQ-4238526
* (Klassische Benutzeroberfläche) Beim Bearbeiten der Workflow-Starter verschwinden die Bedingungen, die dazu führen, dass die Workflows ohne Bedingungen gestartet werden. NPR-23835: Hotfix für CQ-4239153
* Projekt-Posteingang: Beim Wechseln zur Kalenderansicht wird der Hauptinbox-Inhalt angezeigt. NPR-23947: Hotfix für CQ-4241236
* Sie müssen Payload-Details im Bundle verfügbar machen, damit die HTL-Komponente den Wert in der Listenansicht anzeigen kann. NPR-23948: Hotfix für CQ-4240953
* Dialogfelddaten können nicht im Dialogfeld Teilnehmer-Schritt gespeichert werden. NPR-23965: Hotfix für CQ-4234123
* (Touch-Benutzeroberfläche) Beim Speichern eines Workflow-Modells ändert sich die Schaltfläche &quot;Synchronisieren&quot;in &quot;Synchronisiert&quot;, was zu einem Rechtschreibfehler führt. Hotfix für CQ-4244843
* Projekt-Posteingang: Beim Wechseln zur Kalenderansicht wird der Hauptinbox-Inhalt angezeigt. Hotfix für CQ-4244436
* Dialogfelder können im Schritt &quot;Teilnehmer&quot;nicht ausgewählt werden. Hotfix für CQ-4244532
* Proaktiver Backport für Fehlerbehebungen granite.omnisearch.core. NPR-23536
* Problem in Mobile Workspace App 6.4 mit freigegebener Aufgabe. NPR-26383

**WCM - Übersetzung**

* (Referenzbereich) Übersetzungsaufträge werden während der Projekterstellung nicht ausgeführt. Hotfix für CQ-4245327

**WCM - MSM**

* (MSM) Verbesserung der Rollout-Leistung. Hotfix für CQ-4231488
* (MSM) Zeitlücke beim Ereignis-Listening zwischen dem tatsächlichen Ereignis und der Ereignisverarbeitung. Hotfix für CQ-4227766

**Screens**

* Die Bildschirmseite schlägt aufgrund fehlender Abhängigkeiten für screens-core-pkg:1.4.42 mit einem Fehler fehl. Hotfix für CQ-4245918

**Projekte - Übersetzung**

* (Inhaltsfragment) Die Sprachkopie für eingebettete Assets wird nicht erstellt, während englisches Asset zur Übersetzung hinzugefügt wird. Hotfix für CQ-4243477
* Das Dropdown-Menü msft config zeigt die Konfiguration von /libs(6.4 configs)anstelle von /etc(6.3 configs) im alten Modus an. Hotfix für CQ-4243475
* Automatische Weiterleitung und Löschung von Übersetzungsstarts in Übersetzungsprojekten Hotfix für CQ-4243474
* Inhaltsfragment innerhalb von Sites wird nicht übersetzt. Hotfix für CQ-4243482, CQ-4243483, CQ-4245687
* Serverfehler beim Öffnen des Suchfilters für Übersetzungsaufträge. Hotfix für CQ-4236813
* Das Dropdown-Menü für die Konfiguration von Berechtigungen ist leer, selbst wenn tif in /conf/we-retail vorhanden ist. Hotfix für CQ-4236315

**Inhaltsfragmentverwaltung**

* Beim Löschen einer Komponente werden Protokolle mit Stacktraces gefüllt. Hotfix für CQ-4242315

**DAM - Allgemeines**

* Wenn Sie die Detailansicht eines Assets schließen, wird wieder die falsche Suchergebnisseite angezeigt. Hotfix für CQ-4240960
* (Camera Raw) Die Bildanpassungsoption fehlt. Hotfix für CQ-4246121
* IndexOutOfBoundsException: OOTB Asset Modification-Bericht. Hotfix für CQ-4239744
* Entfernen Sie die Konfidenzbewertung aus der CSV-Datei des Berichts. Hotfix für CQ-4241491
* E-Mail-Versand der Linkfreigabe für Absender ohne Administratorrechte unterbrochen. Hotfix für CQ-4240357
* Behebung von IT-Fehlern. Hotfix für CQ-4249891

**DAM - Brand Portal**

* In den Asset-Eigenschaften werden nur drei Eigenschaften auf der ersten Registerkarte aufgelistet. Alle Registerkarten sind leer. Hotfix für CQ-4242503
* Dateityp und Dateigrößeneigenschaften sind im veröffentlichten Suchformular nicht verfügbar. Hotfix für CQ-4242026
* Die Suche in der Ordnereigenschaft sollte herausgefiltert oder in Suchfiltern nicht angezeigt werden. Hotfix für CQ-4241386
* Die Standardsuche aus sollte nach dem Rückgängigmachen der Veröffentlichung vorhanden sein. Hotfix für CQ-4241383, CQ-4241113
* Die Geste &quot;In Brand Portal veröffentlichen&quot;funktioniert nicht für Bildvorgaben. Hotfix für CQ-4241074
* Die Veröffentlichung in Brand Portal funktioniert nicht für Sammlungen. Hotfix für CQ-4241122, CQ-4246558

**DAM - DM Client**

* Durch die Aktualisierung auf 6.4 werden zuvor erstellte Videokodierungsprofile entfernt. Hotfix für CQ-4244067
* Das Attribut ALT-Text ist in der Dynamic Media-Komponente fehlerhaft. Hotfix für CQ-4244081
* (DMS7) Die Bearbeitung von Remote-Sets in AEM wird in Scene7 nicht überschrieben. Hotfix für CQ-4243430
* Überprüfung des 6.4 SP1-Builds auf DM Hybrid. Hotfix für CQ-4244623
* (DMS7-UA) Wenn Sie für ein veröffentlichtes Video-Asset auf die Schaltfläche &quot;Einbetten&quot;klicken, wird nichts angezeigt. Das Dialogfeld &quot;Einbetten&quot;wird voraussichtlich mit HTML-Code angezeigt. Hotfix für CQ-4245237
* (DM Hybrid) URL für veröffentlichte Video-Assets oder Sets für gemischte Medien erhält &quot;`[object Object]`&quot; im Dialogfeld &quot;URL&quot;. Hotfix für CQ-4245236, CQ-4245451
* (DMHybrid) Die Detailansicht-Seite des Videos enthält nicht die Vorschau der Video-Asset-Anzeige und gibt eine Fehlermeldung an die Konsole aus. Hotfix für CQ-4244320
* Automatische S7-Kodierung von We.Retail-Inhalten. Hotfix für CQ-4242253
* Für Vorab-Upgrade-Videoverarbeitungsvorgaben kann weder eine neue Videokodierungsvorgabe hinzugefügt noch die vorhandenen Kodierungsvorgaben bearbeitet werden. Hotfix für CQ-4240407
* Bildvorgaben vor der Aktualisierung werden als auf der Seite Ausgabedarstellungen unveröffentlicht angezeigt und geben keine URL zurück. Hotfix für CQ-4240406
* (CSS) Assets werden angezeigt - aber die verwendeten Viewer sind standardmäßig und nicht die OOTB-Viewer. Hotfix für CQ-4239839
* Der Bereinigungsschritt ist deaktiviert und führt manuell durch und wird von privaten Korallenklassen verwendet. Hotfix für CQ-4239729
* Der Bild-Viewer erzeugt einen Fehler und zeigt die richtige smarte Zuschneidung nicht an. Hotfix für CQ-4237564
* Die veraltete Voreinstellung unter /etc scheint beschädigt zu sein und beim Speichern nicht an den Speicherort unter /conf migriert zu werden. Hotfix für CQ-4237416
* Regression in OOB VideoViewer 5.8.x - der Viewer erweitert iframe auf die rechte Seite, wodurch das Seitenlayout beschädigt wird. Hotfix für CQ-4235465
* (DMS7) URL und Schaltflächen für die Einbettung von Ausgabedarstellungen für Smartes Zuschneiden sind für Bilder aktiv, die noch nicht veröffentlicht wurden. Hotfix für CQ-4233696
* (DMHybrid) Funktion zum vorherigen Zuschneiden/Drehen wiederherstellen. Hotfix für CQ-4239489
* Bei der Vorschau eines Videos in der Kartenansicht wird die Wiedergabeschaltfläche nicht umgeschaltet, um anzuhalten. Hotfix für CQ-4238592
* Bei einer Opt-in-Aktualisierung wird die YouTube-Konfiguration nicht von ihrem alten Speicherort an den neuen Speicherort verschoben/kopiert. Hotfix für CQ-4238590
* DropZwei OOTB AVS Video Processing Profiles werden unter Ordnereigenschaften aufgelistet und nur eines enthält definierte Kodierungen. Hotfix für CQ-4238096
* (DMS7) Smartes Zuschneiden: Detailansicht: Die Schaltfläche URL ist für Ausgabedarstellungen als Schaltfläche Kopieren gekennzeichnet. Hotfix für CQ-4237804
* Die Listenseite für Viewer-Vorgaben bleibt auch nach der Ausführung der curl-Befehle leer. Hotfix für CQ-4243246
* Der Bereinigungsschritt ist deaktiviert und führt manuelle Ausführung und Verwendung privater Korallenklassen durch. Hotfix für CQ-4239729
* Auf der Seite &quot;Videoberichtsdetails&quot;werden keine Video-Assets angezeigt. Hotfix für CQ-4246208

**DAM - DMServices**

* (DMS7) Cloud-Konfiguration: Neue Inhalte können nach der Aktualisierung auf SP1 nicht mit Scene7 synchronisiert werden. Hotfix für CQ-4244437
* (DMHybrid) Farbprofile und Katalogeinstellungen werden nicht in einem &quot;debug_info=catalog&quot;-Aufruf registriert. Hotfix für CQ-4242346
* Fügen Sie den Kundeneinstellungen auf den Versandservern Farbprofile hinzu. Hotfix für CQ-4241818, CQ-4241819
* (DMHybrid) Nach 6.3 &amp;gt; Aktualisierung auf 6.4, Katalogeinstellungen werden in den falschen Knoten verschoben. Hotfix für CQ-4239974, CQ-4239975
* (DMHybrid) pushviewerpresets script erstellt nicht die Knoten, die zum Ändern der Katalogeinstellungen erforderlich sind. Hotfix für CQ-4240076
* Wenn Sie die Dropdown-Auswahl &quot;Format&quot;verwenden und entweder das PNG- oder das JPG-Format auswählen, wird die heruntergeladene Datei als übersättigt und dunkler als das Original-Asset angezeigt. Hotfix für CQ-4240073
* (DMS7) Entfernen Sie die MIME-Typ-Zuordnung: image_x-eps. Hotfix für CQ-4240394
* (DMS7) Upload-Parameter für den Knock-out-Hintergrund werden nicht über die Datei &quot;ipsApiService.log&quot;übergeben und funktionieren daher nicht. Hotfix für CQ-4240686
* Das Aktualisieren von Bildverarbeitungsprofilen, die in einer Instanz von 6.3 auf 6.4 erstellt wurden, unterbricht die Eigenschaft &quot;Zuschnitttyp&quot;. Hotfix für CQ-4237739
* (Dynamic Media) Das regelmäßige Hochladen von Assets außerhalb des smartcrop -Ordners schlägt fehl. Hotfix für CQ-4237670
* Passen Sie den Profil-Fallback-Code für den Profilnamen &quot;Adaptive Videokodierung&quot;an &quot;Adaptive_Video_Encoding&quot;. Hotfix für CQ-4237666
* EmbedXMP-Daten werden für den Ptiff-Generierungsprozess immer auf „aktiv“ gesetzt. Hotfix für CQ-4234498
* Die CMYK-Bildausgabe weist eine falsche Sättigung auf. Hotfix für CQ-4235470
* Image-Server-Einstellungen werden nicht an die Bereitstellung repliziert, während die Replikationsprotokolle sie als erfolgreich kennzeichnen. Hotfix für CQ-4239480, CQ-4239046
* (DMS7) Sets können nicht mit alten/neuen Verweisen auf die Cloud-Konfiguration erstellt werden. Hotfix für CQ-4238078
* Der Workflow-Schritt von Scene7 liest nur Scene7 im Namen und in der Beschreibung, aber nicht den Workflow-Schritt im Workflow &quot;DAM-Update&quot;. Hotfix für CQ-4237865

**DAM - Smart-Tags**

* Neu [Verbesserte Smart-Tags](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951

**Formulare**

AEM Forms-Fehlerbehebungen werden über Add-on-Pakete und andere mit der Version gelieferte Patch-Installationsprogramme bereitgestellt. Weitere Informationen finden Sie unter den AEM Forms-Versionen.

Die wichtigsten Highlights für AEM Forms sind:

* Einführung in AEM Forms [Transaktionsberichterstellung](https://experienceleague.adobe.com/docs/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) , um Transaktionen wie gesendete Formulare, verarbeitete Dokumente und gerenderte Dokumente in Ihrer AEM Forms-Bereitstellung zu verfolgen und die Anzahl der Transaktionen zu halten. Es bietet Einblicke in die Produktnutzung und hilft Geschäftsbenutzern, digitale Verarbeitungsvolumen zu verstehen.
* PDF/UA-Unterstützung für XML-Formulare aktiviert.
* allowProxy = true für Clientlib hinzugefügt **aemfd.ccm.channel.contentpage**
* Der Code wurde aktualisiert, um die erweiterte Titelsuche mit &quot;enthält&quot;statt mit &quot;gleich&quot;durchzuführen.
* Aktualisierung auf die neue Version von Node Package Manager (NPM) auf dem Computer für die kontinuierliche Integration.

**Forms-Add-on-Paket**

**Backend-Integration**

* Wenn einem optionalen Feld null als Wert angegeben wird, wird ein Fehler generiert. NPR-24397
* Der WSDL-Aufruf schlägt fehl, wenn das Element einen anderen Namespace als den globalen Namespace hat. NPR-24281
* (FDM WSDL) Getting DermisException: Ausgenommene Listendaten bei einem Eigenschaftstyp-Array. NPR-24265
* (FDM WSDL) Getting DermisException: java.lang.Exception: createSOAPParam: Ungültige Parameter. NPR-24264
* (FDM Client SDK) Tests von Pre-/Post-Präprozessor- und benutzerdefinierten Übermittlungsaktionen können nicht durchgeführt werden. Hotfix für CQ-4238469
* Fehlerbehebungen bei Javadoc-Problemen in Dermis. Hotfix für CQ-4244250
* Verbesserte Eingabe in WSDL (Web Services Description Language). Hotfix für CQ-4244133
* Grundlegende Authentifizierungstests für WSDL führen zu unterschiedlichen Fehlern für dieselbe Konfiguration in AEM 6.3 und AEM 6.4. Hotfix für CQ-4244132
* Anfrage zur Einbeziehung von ValueUtil in client-sdk und javadocs. Hotfix für CQ-4242803
* (FDM Cloud-Konfiguration) SOAP-basierte Authentifizierung kann nicht über die Cloud-Konfiguration konfiguriert werden. Hotfix für CQ-4238462
* Dermis - Fügen Sie fehlende Pakete in Javadocs hinzu. Hotfix für CQ-4242815
* WSDLInvokerParams wird in das Forms Add-On-Client-SDK aufgenommen. NPR-23381: Hotfix für CQ-4240233

**Adaptive Formulare**.

* Die Ausgabe des Dokuments (IC) sollte als Transaktion mit dem Transaktionsaufzeichnungsdienst protokolliert werden. Hotfix für CQ-4245333
* Beim Ausführen von UAT5 fehlt in der im Überprüfungsstadium erstellten PDF ein Eintrag. Hotfix für CQ-4243184
* Testfall für eine Tiefkopie von guideContext. Hotfix für CQ-4242924
* Das Feld Testversand fehlt beim Ausführen von UAT3 auf dem neuesten aktualisierten Server. Hotfix für CQ-4243120
* Auf einem aktualisierten Server fehlen im gesendeten Formular die Werte Bundesland/Region und Land , die auf dem Server vor der Aktualisierung vorhanden waren. Hotfix für CQ-4241444
* (ExpressionEditor) Fehler beim Navigieren zum Schritt Überprüfen während der Formularübermittlung. Hotfix für CQ-4241384
* Werte fehlen in der Überprüfungsphase auf dem Server vor der Aktualisierung und dem aktualisierten Server für das gesendete Formular. Hotfix für CQ-4241896
* Die Schaltfläche zum Beenden und Speichern am unteren Seitenrand funktioniert nicht. Hotfix für CQ-4240112
* Kontaktnummer fehlt bei der aktualisierten Einrichtung. Hotfix für CQ-4239870
* under `ACTION TAKEN` im Tab Streitfall &quot;Zusätzliche Dokumente zur Unterstützung meiner Behauptung&quot;das zusätzliche Feld Testversand Typ gespeichert &quot;darin. Hotfix für CQ-4239873
* &quot;Fehler in getDataAPI&quot;-Fehler im &quot;verifyPdf&quot;-Schritt. Hotfix für CQ-4239865
* Fehler in Migrationsprotokollen für Autoren- und Veröffentlichungsinstanz. Hotfix für CQ-4239365
* Fehler in Migrationsprotokollen für Autoren- und Veröffentlichungsinstanz. Hotfix für CQ-4239635
* Deserialisierungsfehler wie &quot;Deserialisierung für die Klasse sun.util.calendar.ZoneInfo&quot;in Fehlerprotokollen nach der Übermittlung eines adaptiven Formulars. Hotfix für CQ-4240419
* Das Statusfeld wird nicht in der mobilen Formularwiedergabe ausgefüllt. Hotfix für CQ-4240597
* Entfernen Sie die Referenzverwendung von Komponenten in Vorlagen aus der Liste der Anti-Muster. Hotfix für CQ-4239217
* HTML5 Ein numerisches Feld, das als Float- oder Dezimalfeld eingestellt ist, liefert unterschiedliche Validierungsergebnisse in verschiedenen Browsern. NPR-23528: Hotfix für CQ-4244097
* (Bild-Upload) Bild wird nicht in der DOR-Vorschau angezeigt. Hotfix für CQ-4243178
* Der JEE-Server gibt beim Versuch, das adaptive Formular mit &quot;E-Mail-PDF&quot;und &quot;Anlagen einschließen&quot;zu senden, einen Fehler aus. Hotfix für CQ-4239894
* Das Diagramm wird zur Laufzeit nicht mit Tabelle/Bedienfeld gezeichnet. Hotfix für CQ-4240010
* Die Übermittlung des adaptiven Formulars funktioniert nicht und die Transaktionsanzahl ändert sich aufgrund der fehlgeschlagenen Übermittlung nicht. Hotfix für CQ-4246125
* (Bildauswahl) Datensatzdokument-Optionen sind nicht sichtbar. Hotfix für CQ-4236976
* Die Benutzeroberfläche des Vorlageneditors ist nicht stabil. Hotfix für CQ-4241497
* AFs werden nicht über die Registerkarte &quot;Assets&quot;des Seitenbereichs angezeigt, während über die Option &quot;Durchsuchen&quot;für AEM Dialogfeld mit den Eigenschaften der Formularkomponente angezeigt wird. Hotfix für CQ-4236751
* Die für die Formularkonvertierung generierte Workflow-ID sollte im generierten adaptiven Formular verfügbar sein. Hotfix für CQ-4240014
* Vorlage kann nicht ausgewählt werden, um eine Seite in Sites bei direkter Aktualisierung zu erstellen: LiveCycle auf den 6.4-Server. Hotfix für CQ-4241300

**Assembler-Service**

* Transaktionsprotokollierung in Assembler-Diensten. Hotfix für CQ-4245018, CQ-4245017, CQ-4245016.
* Die Transaktion wird nicht gemeldet, wenn die PDF/A-Konversion mit DDX durchgeführt wird. Hotfix für CQ-4246039

**Forms Manager**

* FM-Schaltflächenliste ERSTELLEN , um alphabetisch sortiert zu werden. Hotfix für CQ-4242307

**Form Portal**

* Auf dem Server vor der Aktualisierung gespeicherte Entwürfe werden auf dem aktualisierten Server nicht korrekt geöffnet. Hotfix für CQ-4243303
* Aktualisierung der Version auf 7.1 für das adobe-formsmanager-core-modul. Hotfix für CQ-4245753
* Auf dem Server vor der Aktualisierung gespeicherte Entwürfe werden auf dem aktualisierten Server nicht korrekt geöffnet. Hotfix für CQ-4243303
* Anlagenszenarien schlagen beim Ersetzen/Hinzufügen/Entfernen von Anlagen in einer neuen Instanz/derselben Instanz des Entwurfs fehl. Hotfix für CQ-4243165
* Die Anzahl der durch Abfrage der Datenbank abgerufenen Entwürfe übersteigt die Anzahl der im Portal vorhandenen Entwürfe. Hotfix für CQ-4241489
* Auf dem Server vor der Aktualisierung gesendete Forms sind nicht auf dem aktualisierten Server vorhanden. Hotfix für CQ-4241490
* Das in der Benutzeroberfläche auf der Registerkarte &quot;Übermittlungen&quot;angezeigte Formular befindet sich trotz erfolgreicher Übermittlungsmeldung im Status &quot;Nicht gesendet&quot;. Hotfix für CQ-4241487
* Der guideContext sollte durch Deep-Copy der Felder gebildet werden, da guideContext customPropertyMap enthält, die selbst ein Objekt ist. Hotfix für CQ-4240126
* Fehler beim Speichern eines Formulars. Hotfix für CQ-4240763
* Der Eintrag für gespeicherte und gesendete Formulare wird in crx/de ausgefüllt, obwohl die DB-Konfiguration in der Forms Portal-Konfiguration für Entwurf und Übermittlung angegeben ist. Hotfix für CQ-4240726
* (Search &amp; Lister) Der feste Wert für den erweiterten Suchtitel sollte &quot;enthalten&quot;und nicht &quot;gleich&quot;verwenden. Hotfix für CQ-4245499

**Mobile Forms**

* Das Datumsfeld überschneidet sich in Mobile Forms. Hotfix für CQ-4242256
* Die Formularübermittlung für Mobile Forms sollte als Transaktion mit dem Transaktionsaufzeichnungsdienst protokolliert werden. Hotfix für CQ-4246166
* Die Übermittlung von Formularen in FormSet sollte als Transaktion mit dem Transaktionsaufzeichnungsdienst protokolliert werden. Hotfix für CQ-4246165

**AEM Forms-App**

* (Windows App) Das Formular kann nicht wiedergegeben werden. Hotfix für CQ-4238005

**Workflow-OSGi**

* Transaktionsprotokollierung in Workflow-Zuweisungsaufgabe. Hotfix für CQ-4244440
* (FDM-Schritt) Werte aus Workflow-Metadaten können nicht verwendet werden, wenn zwischen dem Prozessschritt und dem FDM-Schritt ein Schritt &quot;Aufgabe zuweisen&quot;eingefügt wird. Hotfix für CQ-4241472
* Die Zuweisung von Zuweisungsaufgaben funktioniert nicht in der Forms-Integration in OSGi-Workflows. NPR-23709: Hotfix für CQ-4243700
* (Workflow-Modell-Editor) Einige Workflow-Modelle können nicht über den WF-Modell-Editor der klassischen Benutzeroberfläche bearbeitet werden. Hotfix für CQ-4241151

**MultiChannel-Dokument**

* Das Datumsfeld in der Vorlage überschneidet sich mit dem Teilformular in der IC-Bearbeitung. Hotfix für CQ-4240110
* Die Kopfzeile darf nicht gelöscht oder in der IC-Webkanal-Bearbeitung nach oben und unten verschoben werden. Hotfix für CQ-4243358
* (IC Editor) Standardzeilen, die für Tabellenkomponenten auf 1 gesetzt werden. Hotfix für CQ-4244848
* Zielbereich bleibt sichtbar, auch wenn der Inhalt per Drag-and-Drop hierher gezogen und abgelegt wurde. Hotfix für CQ-4244534
* Der Webkanal erkennt keinen Tabulatorraum in Textdokumentfragmenten. Hotfix für CQ-4244481
* (Print Channel) Document (IC) rendition sollte als Transaktion mit Transaction Recording Service protokolliert werden. Hotfix für CQ-4245335
* (Webkanal) Die Ausgabe des Dokuments (IC) sollte als Transaktion mit dem Transaktionsaufzeichnungsdienst protokolliert werden. Hotfix für CQ-4245334
* Die Suche nach Dokumentcontainer oder die Suche nach Datenmodellstruktur muss mit der Asset-Filtersuche vereinheitlicht werden. Hotfix für CQ-4242305
* (Dokumentfragment) Die Einzugseigenschaft rückt den Text nach der Anzahl der Einheiten ein, die nicht verstanden werden können. Hotfix für CQ-4241082, CQ-4240643
* (IC Editor) Das Symbol &quot;Fragment bearbeiten&quot;auf der Kachel des Dokumentfragments, die auf der Registerkarte &quot;Assets&quot;aufgelistet ist, ist nicht einfach zu finden und zu verstehen. Hotfix für CQ-4241047
* Anonymen Zugriff auf die anonyme IC-Client-Bibliothek zulassen, auf die nicht zugegriffen werden kann. Hotfix für CQ-4245588
* (Webkanal) Daten werden in keiner der Tabellen in der Webvorschau aufgelöst und als leer angezeigt. Hotfix für CQ-4244476
* Tabellenüberschriften werden bei der automatischen Generierung als Variablen im Webkanal angezeigt. Hotfix für CQ-4244242
* (IC-Editor) Der Inhalt eines in einem IC verwendeten Dokumentfragments sollte automatisch neu skaliert werden, um die Breite des Zielbereichs anzupassen. Hotfix für CQ-4244094
* Der Kanalname, der in der Mitte angezeigt wird, muss entweder für den IC-Titel für WEB/PRINT konsistent sein. Hotfix für CQ-4242498
* Texteditor Datenobjektbereich sollte nur Entitäten der obersten Ebene auflisten, Hotfix für CQ-4244121
* Beim Hinzufügen einer neuen Komponente im Editor wird kein Standardname zugewiesen. Hotfix für CQ-4244691
* Hinzufügen der Colspan-Konfiguration in allen Webkanal-Komponenten. Hotfix für CQ-4244946
* Die Eigenschaft &quot;Tabellenbreite des Layoutfragments&quot;wird nicht zurückgesetzt und im Druckkanal für Brief- oder Kundenkommunikation berücksichtigt. Hotfix für CQ-4241574

**Korrespondenzverwaltung**

* Beschriftungen, die aus der Briefvorlage entfernt wurden, nachdem ein Text-Asset bearbeitet wurde, das Platzhalter enthält. NPR-24196
* Die XDP-Datei kann die Vorlagen nicht in der Vorschau anzeigen oder bearbeiten, wenn sie hochgeladen und als Layout für Briefvorlagen verwendet wird. NPR-24143: Hotfix für CQ-4244407
* Die Zuweisungsauswahl ist im Listenfragment standardmäßig ausgewählt. Hotfix für CQ-4240097
* Bedingungseditor - Die Auswertung mehrerer Ergebnisse sollte standardmäßig aktiviert sein. Hotfix für CQ-4240096
* Das aus der Liste gelöschte Bild zeigt weiterhin das Bild in der Vorschau an. Hotfix für CQ-4239909
* Der Regelsatz für das Bedingungsmodul wird für alle Module als &quot;Standard&quot;festgelegt. Hotfix für CQ-4239878
* Die Erstellung eines Datenwörterbuchs schlägt mit dem Fehler &quot;Unbekannte JCR-Ausnahme&quot;fehl. Hotfix für CQ-4244122
* Lücken in 6.3 Content JavaDocs. Hotfix für CQ-4213586

**Forms JEE-Installationsprogramm**

**Core**

* (HTML Workspace) Tracking-Details fehlen für Anwendungen mit Klammern-Symbol im Namen. NPR-23402

**PDFG Service**

* Transaktionsprotokollierung in PDFG-Diensten. Hotfix für CQ-4244951, CQ-4244586
* Verringerung der PDF durch selektives Aufheben der Einbettung von Schriftarten über einen einzigen API-Aufruf. NPR-23287
* Problem bei PDFG-Konfigurationen beim Aktualisieren AEM. Hotfix für CQ-4241176
* Transaktionsprotokollierung im PDFUtility-Dienst. Hotfix für CQ-4245014

**Prozessverwaltung**

* (HTML-Arbeitsbereich) Prozess-Startpunkte sind nicht in alphanumerischer Reihenfolge sortiert. Hotfix für CQ-4239629
* (HTML Workspace) Bereiten Sie den Datenaufruf vor, der zweimal angezeigt wird, wenn der Entwurf zum ersten Mal geöffnet wird. Hotfix für CQ-4243280
* (HTML Workspace) Der Prepare Data-Prozess wird beim Schließen eines Formulars ausgelöst. Hotfix für CQ-4239456
* Der Arbeitsbereich hängt, wenn er zwischen zwei Aufgaben durchlaufen wird. Hotfix für CQ-4237125

**Workbench**

* Der Datenprozess &quot;Aktionsprofil verwalten&quot;schlägt fehl, wenn die standardmäßige Renderprozesskonfiguration auf HTML festgelegt ist. Hotfix für CQ-4244292

**Forms Designer**

* Fügt XML-Formularen, die über Designer und den Output Service generiert wurden, PDF/UA-Unterstützung hinzu. NPR-23022
* Inline-Hyperlinks, die in Designer definiert sind, werden weder mit Tags versehen, noch haben sie alternativen Text, wenn sie als PDF in Designer gespeichert werden. NPR-23023

**Enthaltene Feature Packs**

**Assets**

* Die Funktion für optimierte Smart-Tags wurde hinzugefügt. Weitere Informationen finden Sie unter [Verbesserte Smart-Tags](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951: Hotfix für CQ-4234883
* Einführung von AEM Assets-Referenzen in InDesign. Weitere Informationen finden Sie unter [AEM Assets-Referenzen in InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**Sites**

* (Seitenbearbeitung) Verbesserungen des Bildeditors. Weitere Informationen finden Sie unter [Bildeditor](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/image-editor.html). NPR-24267: Hotfix für CQ-4245502

**Enthaltene OSGI-Bundles und Inhaltspakete**

Im folgenden Text wird die Liste der im CFP enthaltenen OSGI-Bundles und Inhaltspakete dokumentiert.

Liste der in AEM 6.4.1.0 enthaltenen OSGi-Bundles

[Datei abrufen](assets/6_4_1_0_bundle-list.txt)

Liste der in AEM 6.4.1.0 enthaltenen Inhaltspakete

[Datei abrufen](assets/6_4_1_0_content-package-list.txt)

### Installieren von Version 6.4.8.0. {#install}

#### Einrichtungsanforderungen {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Für Kunden mit Feature Packs, die in AEM 6.4 installiert sind. Optionale Feature Packs, die von Adobe bereitgestellt werden, haben Abhängigkeiten von der Release-Version und dem Service Pack. Wenn Sie Feature Pack installiert haben, wenden Sie sich an das AEM Kundenunterstützungsteam, um die Kompatibilität dieser Feature Packs mit diesem Service Pack für AEM 6.4 zu überprüfen.

* AEM 6.4.8.0 erfordert AEM 6.4. Weitere Informationen finden Sie unter [Upgrade-Dokumentation](../sites-deploying/upgrade.md).
* Der Service Pack-Download ist verfügbar unter [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) herunterladen.
* Installieren Sie bei einer Bereitstellung mit MongoDB und mehreren Instanzen AEM 6.4.8.0 auf einer der Autoreninstanzen mit Package Manager.
* Stellen Sie vor der Installation des Service Packs sicher, dass Sie eine Momentaufnahme oder eine neue Sicherung Ihrer AEM-Instanz haben.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz gerade von einer früheren Version aktualisiert wurde), es wird jedoch im Allgemeinen empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wird.

>[!NOTE]
>
>Adobe rät davon ab, das AEM 6.4.8.0-Paket zu entfernen oder zu deinstallieren.

### Installieren des Service Packs über Package Manager {#install-the-service-pack-via-package-share}

Führen Sie die folgenden Schritte aus, um das Service Pack auf einer vorhandenen AEM 6.4-Instanz zu installieren:

1. Laden Sie das Paket von Software Distribution herunter.

1. Melden Sie sich in AEM bei Package Manager an und fügen Sie das heruntergeladene Paket AEM 6.4.8.0 hinzu. Wählen Sie das hochgeladene Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird manchmal während der Installation von 6.4.8.0 nicht rechtzeitig beendet.**
>
>Daher wird empfohlen, auf die Stabilisierung von Fehlerprotokollen zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles warten, bevor sichergestellt wird, dass die Installationen erfolgreich sind. Dies geschieht in der Regel in Safari, kann jedoch gelegentlich in jedem Browser auftreten.

### Automatische Installation {#auto-installation}

Es gibt zwei Möglichkeiten, AEM 6.4.8.0 automatisch in einer laufenden Instanz zu installieren:

A. Platzieren Sie das Paket in ..*/crx-quickstart/install* Ordner, während der Server ausgeführt wird. Das Paket wird automatisch installiert.

B. Verwenden Sie die [HTTP-API von Package Manager](/help/sites-administering/package-manager.md) - Stellen Sie sicher, dass Sie `cmd=install&recursive=true` - damit das verschachtelte Paket installiert wird.

>[!NOTE]
>
>AEM 6.4.8.0 unterstützt keine Installation von Bootstraps.

### Bestätigen der Installation {#validate-install}

1. Auf der Seite &quot;Produktinformationen&quot;(*/system/console/productinfo *) sollte jetzt die aktualisierte Versionszeichenfolge &quot;Adobe Experience Manager, Version 6.4.8.0&quot;unter &quot;Installierte Produkte&quot;angezeigt werden.
1. Alle OSGI-Bundles sind in der OSGI-Konsole entweder AKTIV oder FRAGMENT. (Verwenden Sie die Web-Konsole: /system/console/bundles.)
1. Das OSGI-Bundle org.apache.jackrabbit.oak-core befindet sich auf Version 1.8.17 oder höher (Webkonsole verwenden: /system/console/bundles).

Informationen zur Ermittlung der zertifizierten Plattform für die Ausführung mit dieser Version von AEM Sites und Assets finden Sie unter [Technische Anforderungen](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Bei erfolgreicher Installation des Pakets erscheint eine Meldung, die angibt, dass der Inhalt > Paket erfolgreich installiert wurde, z. B. **&quot;Inhaltspaket AEM-6.4-Service-Pack-7 wurde erfolgreich installiert.&quot;**

### Aktualisieren von Dynamic Media-Viewern (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM Version 6.4.8.0 enthält eine neue Version von Dynamic Media-Viewern (5.10.1), die die Überprüfung auf doppelte Namen auf der Seite Bildvorgabe ermöglicht. Dynamic Media-Kunden wird empfohlen, den folgenden Befehl auszuführen, um die standardmäßigen Viewer-Vorgaben in einen aktuellen Status zu versetzen.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

, wodurch neue Viewer-Vorgaben in den Speicherort /conf kopiert werden.

### Installieren des Add-On-Pakets AEM Formulare {#install-aem-forms-add-on-package}

#### AEM Forms-Add-on installieren {#installaemformsaddon}

>[!NOTE]
>
>Überspringen Sie diese Option, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in AEM Forms werden über ein separates Add-On-Paket bereitgestellt.

>[!NOTE]
>
>AEM 6.4.8.0 enthält eine neue Version von [AEM Forms-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de). Wenn Sie eine ältere Version des AEM Forms-Kompatibilitätspakets verwenden und auf AEM 6.4.8.0 aktualisieren, installieren Sie nach der Installation des Forms Add-On-Pakets die neueste Version des AEM Forms-Kompatibilitätspakets.

1. Stellen Sie sicher, dass Sie das AEM Service Pack installiert haben.
1. Laden Sie das entsprechende Formular-Add-On-Paket herunter, das unter [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) für Ihr Betriebssystem.
1. Installieren Sie das Formular-Add-On-Paket wie unter [Installieren von Add-On-Paketen für AEM Formulare](https://experienceleague.adobe.com/docs/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installieren des AEM Forms JEE-Installationsprogramms {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in AEM Forms JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für AEM Forms JEE und zur Konfiguration nach der Bereitstellung finden Sie unter [AEM Forms JEE Patch Installer 2015](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0015.html).

#### Für NPR-21268 erforderliche Konfigurationseinstellungen {#configuration-settings-required-for-npr}

Wenn Sie die klassische (alte) Benutzeroberfläche verwenden und damit Metadatenvorlagen erstellt haben, führen Sie die Schritte aus, um das JMX-Skript auszuführen und beizubehalten -

1. Wechseln Sie zu /system/console/jmx.
1. Klicken Sie auf &quot;Metadatenvorlagen migrieren&quot;.
1. Klicken Sie auf &quot;migrateMetadataTemplatesAtPath&quot;und geben Sie den Ordnerpfad ein, unter dem die Metadatenvorlagen beibehalten werden sollen.

#### Für NPR-24536 erforderliche Konfigurationseinstellungen {#configuration-settings-required-for-npr-1}

Die Anzahl der freigegebenen Warteschlangen wird für andere Benutzer standardmäßig nicht aktualisiert, wenn ein Benutzer eine Aufgabe beansprucht. Dafür wurde eine neue Eigenschaft eingeführt. Führen Sie die folgenden Schritte aus, um diese Eigenschaft in Ihrer AEM-Instanz zu konfigurieren:

1. Gehen Sie zu „Administrator-Benutzeroberfläche“ > „Services“ > „Arbeitsbereich“ > „Globale Verwaltung“.
1. Globale Einstellungen exportieren.
1. Fügen Sie in der heruntergeladenen XML-Datei das Tag hinzu &lt;client_taskspollinginterval>10&lt;/client_taskspollinginterval> Hier ist 10 der Beispielwert in Sekunden. Sie können ihn entsprechend ändern.
1. Speichern Sie die Datei.
1. Gehen Sie zurück zu „Administrator-Benutzeroberfläche“ > „Services“ > „Arbeitsbereich“ > „Globale Verwaltung“.
1. Importieren Sie die XML-Datei im Abschnitt „Globale Einstellungen importieren“.
1. Sie können sich jetzt vom System abmelden und erneut anmelden.
1. Die Anzahl der freigegebenen Warteschlangen wird für andere Benutzer im Workspace aktualisiert.
1. Um die Abfrage zu deaktivieren, ändern Sie den Wert in 0 und importieren Sie die XML-Datei erneut.

### Uber Jar {#uber-jar}

Das Uber Jar für AEM 6.4.8.0 ist im [Öffentliches Maven-Repository der Adobe](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/).

Informationen zur Verwendung von Uber Jar in einem Maven-Projekt finden Sie in [diesem Artikel](../sites-developing/ht-projects-maven.md). Beziehen Sie die folgenden Abhängigkeiten in Ihr Projekt-POM ein:

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
| Assets | Tag-Aktion für Teil-Assets verwalten | Kein Ersatz | AEM 6.4.2.0 |
| Integration von Assets und Adobe Creative Cloud | [Die gemeinsame Nutzung von AEM-Ordnern in Creative Cloud](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) wurde in AEM 6.2 eingeführt, um Benutzern von Creative Cloud den Zugang zu den Assets von AEM zu ermöglichen. Eine neue Funktion des Creative Cloud-Programms, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus. Adobe wird die Ordnerfreigabe nicht weiter verbessern. Auch wenn die Funktion in AEM enthalten ist, wird den Kunden dringend empfohlen, den Ersatz zu verwenden. | Adobe Asset Link oder Desktop-Programm. Weitere Informationen finden Sie unter [AEM Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md) Artikel. | AEM 6.4.4.0 |

### Bekannte Probleme {#known-issues}

* Die folgenden Fehler und Warnungen können während der Installation angezeigt werden:

   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Zeitüberschreitung beim Warten darauf, dass die Registrierung geändert wird, um das Aufheben der Registrierung abzuschließen.
   * `com.adobe.granite.maintenance.impl.TaskScheduler` Keine Wartungsfenster unter granite/operations/maintenance gefunden
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`: Die unbindAmendment-Methode hat eine Ausnahme ausgelöst (java.lang.IllegalStateException: Dienst wurde bereits abgemeldet).
Diese Fehler erfordern keine Aktion, da sie sich nicht auf Ihre AEM-Instanz auswirken.

### Gelöste Probleme {#resolved-issues}

**AEM 6.4.4.0**

* Beim Importieren/Exportieren von Metadaten wird kein Ressourcenfehler festgestellt. CQ-4253263
* Es ist nicht möglich, Bildkomponenten und Seiteneigenschaften zu bearbeiten, nachdem 6.4.3.0 auf 6.4.2.0 angewendet wurde. CQ-4260316 und CQ-4260441 Um dieses Problem zu umgehen:
   * Wechseln Sie zu Package Manager .
   * Installieren Sie das Paket &quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot; neu.
   * Neukompilieren aller JSPs `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` ODER starten Sie die Instanz neu.

### Enthaltene OSGi-Bundles und Inhaltspakete {#osgi-bundles-and-content-packages-included}

In den folgenden Textdokumenten sind die in AEM 6.4.8.0 enthaltenen OSGi-Pakete und Inhaltspakete aufgeführt.

Liste der in AEM 6.4.8.0 enthaltenen OSGi-Bundles

[Datei abrufen](assets/6.4.8.0_osgi_bundles.txt)

Liste der in AEM 6.4.8.0 enthaltenen Inhaltspakete

[Datei abrufen](assets/6.4.8.0_content_packages.txt)

### Hilfreiche Ressourcen {#helpful-resources}

* [AEM 6.4 – Versionshinweise](../release-notes/release-notes.md)
* [AEM-Produktseite](https://www.adobe.com/solutions/web-experience-management.html)
* [Dokumentation zu AEM 6.4](https://helpx.adobe.com/de/support/experience-manager/6-4.html)
* Abonnieren von [Adobe-Prioritäts-Produkt-Updates](https://www.adobe.com/subscription/priority-product-update.html)

### Eingeschränkte Sites {#restricted-sites-new}

Diese Sites sind nur für Kundinnen und Kunden verfügbar. Wenn Sie ein Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Kundenbetreuer für Adoben.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/).
* Produktaktualisierungen, Patches und Pakete für zusätzliche Funktionen in der [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Kunden-Support über die Admin Console](https://adminconsole.adobe.com/). Weitere Informationen finden Sie unter [Neues Adobe-Kunden-Supporterlebnis](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).
