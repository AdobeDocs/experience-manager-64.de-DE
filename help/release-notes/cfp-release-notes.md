---
title: Versionshinweise zu AEM 6.4 Cumulative Fix Pack
description: Spezifische Versionshinweise zu Adobe Experience Manager 6.4 Cumulative Fix Packs.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 2aa3037b63f745d158eb87c5156808237277990d
workflow-type: tm+mt
source-wordcount: '2142'
ht-degree: 25%

---


# Versionshinweise zu AEM 6.4 Cumulative Fix Pack {#aem-cumulative-fix-pack-release-notes}

## Versionshinweise {#release-information}

| Produkte | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.1 |
| Typ | Cumulative Fix Pack |
| Datum       | 04. Juni 2020 |
| Voraussetzung | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| Download-URL | AEM 6.4.8.1 für [Paketfreigabe](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/cumulativefixpack/AEM-CFP-6.4.8.1), [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fcumulativefixpack%2Faem-6.4.8-cfp-1.0.zip) |

## Was ist in AEM 6.4.8.1 enthalten?{#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.1 ist ein wichtiges Update, das seit der allgemeinen Verfügbarkeit von AEM 6.4 Service Pack 8 (6.4.8.0) im März 2020 mehrere interne und kundenspezifische Fehlerbehebungen enthält.

AEM Cumulative Fix Pack 6.4.8.1 ist von AEM 6.4 Service Pack 8 abhängig. Daher müssen Sie das AEM Cumulative Fix Pack 6.4.8.1-Paket nach der Installation von AEM 6.4 Service Pack 8 installieren.

Einige der wichtigsten Highlights von AEM 6.4.8.1 sind:

* Die Paketfreigabe-Integration mit Adobe Experience Manager wurde entfernt.
* Das integrierte Repository (Apache Jackrabbit Oak) wird auf Version 1.8.21 aktualisiert.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

## Liste der Änderungen      {#list-of-changes}

Adobe Experience Manager 6.4.8.1 enthält Korrekturen an den folgenden Problemen.

### Sites {#sites-6481}

* Wenn der Name einer lokalen Komponente in einer LiveCopy mit dem Namen einer Komponente im Entwurf identisch ist und die Komponente aus dem Blueprint herausgegeben wird, wird dem Namen der lokalen Komponente kein Begriff _msm_move hinzugefügt (NPR-33207).
* Die an die ursprüngliche Anforderung angehängten Parameter sind nicht in der Umleitungs-URL (NPR-33174) enthalten.
* Wenn die Option &quot;Coral.Select&quot;emptyOption=true setzt oder ein Standardelement mit Wert = &quot;&quot; enthält, tritt in der Datei dropdownshowhide.js ein Fehler auf: Nicht abgefangener TypeError: component.getValue ist keine Funktion (NPR-33163).
* Wenn eine Komponente eine andere Komponente als datenbasierte Ressource enthält, wird der Platzhalter für die Komponente des übergeordneten Containers durch den Platzhalter für die inneren Komponenten ersetzt (NPR-33119).
* Wenn Sie ein Inhaltsfragment auf einem Schema basieren und es einen obligatorischen Textbereich oder ein Pfadfeld enthält, kann das Inhaltsfragment nicht gespeichert werden (NPR-33007)
* Wenn Sie eine benutzerdefinierte Komponente mithilfe der vordefinierten Erlebnisfragmentkomponente erstellen und sie auf den AEM-Siteseiten verwenden, zeigt AEM keine Verweise (Nutzung) für die benutzerdefinierte Komponente (NPR-32852) an.
* Wenn eine AEM-Siteseite Teil eines großen Inhaltssatzes mit mehreren Live-Kopien ist, kann die Vorschau des Seitenversionsverlaufs nicht geladen werden (NPR-32772).
* Wenn Sie einen Launch bewerben, wird das &quot;cq:LiveRelationship&quot;-Mixin zu jeder Komponente hinzugefügt, die im Launch hinzugefügt wird. Sie wirkt sich auf alle Starts aus, unabhängig davon, ob ein Startvorgang mit oder ohne Auswahl der Option —  Quellseitendaten übernehmen —  Option (NPR-32664).
* Beim Paginieren werden nicht alle Elemente (NPR-32605) in der Erlebnisfragmentauswahl geladen.
* Ein Start für eine AEM-Siteseite kann nicht erstellt werden. Die Erstellung des Startvorgangs führt zu einem Fehler (NPR-32544).
* Veröffentlichung verwalten enthält keine referenzierten Assets in der Anforderung des Arbeitsablaufs für die Aktivierung (NPR-32463).
* Dispatcher Health Check zeigt eine `Invalid cookie header` Warnmeldung in den Protokolldateien an (NPR-33630).

### Assets {#assets-6481}

* Die Anzahl der Vermögenswerte ändert sich nicht entsprechend der Änderung der Auswahl in der Ansicht der Liste (NPR-33285).

* Die Schaltfläche Weiter ist nicht aktiviert, wenn der übergeordnete Knoten ausgewählt (wobei ein einzelner untergeordneter Ordner sichtbar ist) und anschließend der untergeordnete Ordner ausgewählt wird (NPR-33284).

* Die Touch-Benutzeroberfläche kann nicht (mit Fehler) für Benutzer gerendert werden, die keinen Lesezugriff im Repository-Stammordner haben, wenn der DMS7- oder Hybrid-Modus aktiviert ist (NPR-33175).

* Die GB18030-Zeichen in Ordner- und Asset-Namen werden in den heruntergeladenen ZIP-Dateien leer (NPR-33150).

* Der Ordner &quot;Extra&quot;wird beim intelligenten Zuschneiden eines Assets erstellt, das sich in einem übergeordneten Ordner mit Punkt- `.` Zeichen im Namen befindet (NPR-32755).

* Verzögertes Laden wird nicht ausgelöst, und es werden nicht mehr als 100 Assets angezeigt, die ausgewählt werden, um die Aufgaben aus dem Benachrichtigungs-Posteingang zu überprüfen (NPR-32749).

* Die Linkseite zum Teilen der Sammlung ist aufgrund einer Änderung der Korallen-Info (NPR-32510) beschädigt.

* Die Verarbeitung von Assets während des Massen-Uploads wird blockiert (CQ-4293916).

### Plattform {#platform-6481}

* Der [!DNL Sling] Filter wird nicht aufgerufen, wenn der `sling:match` Karteneintrag unter `/etc/maps` (NPR-33308) erstellt wird.
* Alle Spülmittel werden beim Deaktivieren einer Seite ausgelöst (NPR-32941).
* Wenn Sie die `ScriptProcessor` API zum Minimieren einer JavaScript-Bibliothek verwenden, wird in der Protokolldatei eine Fehlermeldung angezeigt, die darauf hinweist, dass der JavaScript-Code nicht dem strikten Modus entspricht. Die API bietet keine Option zum Aktivieren oder Deaktivieren des strikten Modus. (NPR-32746).
* Wenn eine SQL-Abfrage länger ausgeführt wird (z. B. 7 Stunden), reagiert AEM nicht mehr (NPR-33043).

### Benutzeroberfläche {#ui-6481}

* Wenn Sie einen Pfad über ein Auswahldialogfeld suchen oder durchsuchen, werden im Auswahldialogfeld alle Inhalte des ausgewählten JCR-Knotens angezeigt, anstatt nur die Bilder anzuzeigen (NPR-32712).

### Übersetzungsprojekte {#tranlation-6481}

* Ein `NullPointerException` Fehler wird in den Protokollen zur Ausführung eines Übersetzungsauftrags (NPR-32220) angezeigt.

### Communities {#communities-6481}

* Autoren werden nach der Erstellung einer neuen Gruppe nicht in den Abschnitt [!UICONTROL Community Group] unter [!DNL Internet Explorer] 11 (NPR-33202) umgeleitet.
* Beim Zugriff auf die [!UICONTROL Aktivität Stream] -Seite (NPR-33152) tritt ein Fehler auf.
* Durch Bearbeiten einer [!DNL Communities] Gruppe und Ändern der Miniaturansicht wird das Gruppenminiaturbild nicht aktualisiert (NPR-32603).
* Beim Erstellen einer Version von Benachrichtigungen und Abonnements von User Generated Content (UGC) wird eine falsche ID der Quellseite gespeichert (CQ-4289703).

### Workflow {#workflow-6481}

* Einige Komponenten werden nicht im Popup-Dialogfeld angezeigt, wenn ein Benutzer einen Workflow abgeschlossen hat, der einen Schritt [!UICONTROL zum] Dialogteilnehmer enthält (NPR-32989).

* Die [!UICONTROL Option &quot;Zeitschiene] &quot;in der linken Leiste dauert länger als erwartet (NPR-32850).

### Forms {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack enthält keine Korrekturen für AEM Forms. Diese werden im Rahmen eines separaten Add-on-Pakets für Forms bereitgestellt. Außerdem wird ein kumulatives Installationsprogramm herausgegeben, das Fehlerbehebungen für AEM Forms JEE enthält. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* Correspondence Management: Wenn ein Benutzer Inhalte aus einem [!DNL Word] Dokument einfügt, behält das Textfragment keine Formatierung bei (NPR-33213).
* Adaptive Formulare: Eine neue Zeile zu einer Zeichenfolge in einem Wörterbuch für adaptive Formulare fügt dem Wörterbuch Zeichen hinzu (NPR-33265). `&#xa;`
* Adaptive Formulare: Der Benutzer kann ein adaptives Formular nicht mit mehr als einer Anlage speichern (NPR-33214).
* Adaptive Formulare: `AddInstance` und `RemoveInstance` Methoden für die Instanz Manager-Klasse fügen keine dynamische Anzahl von Instanzen für verzögerte Ladefragmente hinzu [!DNL Internet Explorer 11] (NPR-33201).
* Adaptive Formulare: Analytics, das auf einem adaptiven Formular aktiviert ist, das in eine [!DNL Sites] Seite eingebettet ist, zeichnet keine Daten für die Ereignisse &quot;Senden&quot;und &quot;Abbrechen&quot;auf (NPR-31359).
* Adaptive Formulare: Wenn ein Benutzer den Inhalt aus einem [!DNL Word] Dokument in ein adaptives Formular einfügt und es sendet, enthält das gesendete adaptive Formular Unicode-Zeichen. Darüber hinaus schlägt die Konvertierung von PDF in PDF/A aufgrund von Unicode-Zeichen (NPR-33348) fehl.
* BackendIntegration: Formulardatenmodellanforderungen schlagen fehl, da der Aktualisierungstoken aufgrund eines inaktiven Status (NPR-33168) abläuft.
* Dokument-Dienste: Der Convert PDF-Dienst kann PDF-Dokumente nicht in PostScript konvertieren, da Gibson-JARs für [!DNL WebLogic] den [!DNL Linux] Server fehlen (NPR-33515, CQ-4292239).
* Dokument-Dienste: Wenn ein Benutzer eine Textdatei in eine PDF-Datei konvertiert, werden japanische Zeichen nicht korrekt dargestellt (NPR-33239).

## Install 6.4.8.1 {#install}

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
>Für Kunden mit Feature Packs, die auf AEM 6.4 installiert sind. Die von Adobe bereitgestellten optionalen Funktionspakete hängen von der Release-Version und den Service Packs ab. Wenn Sie ein Feature Pack installiert haben, wenden Sie sich an den AEM-Kundendienst, um die Kompatibilität dieser Feature Packs mit diesem kumulativen Fix Pack für AEM 6.4 zu überprüfen.

* AEM 6.4.8.1 requires AEM 6.4.8.0. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* Installieren Sie bei einer Implementierung mit MongoDB und mehreren Instanzen AEM 6.4.8.1 mithilfe von Package Manager auf einer der Autoreninstanzen.
* Bevor Sie das kumulative Fix Pack installieren, stellen Sie sicher, dass Sie über einen Schnappschuss oder eine neue Sicherung Ihrer AEM-Instanz verfügen.
* Starten Sie die Instanz vor der Installation neu. Dies ist zwar nur dann erforderlich, wenn sich die Instanz noch im Aktualisierungsmodus befindet (und dies ist der Fall, wenn die Instanz gerade von einer früheren Version aktualisiert wurde). Dennoch wird dies allgemein empfohlen, wenn die Instanz über einen längeren Zeitraum ausgeführt wurde.

>[!NOTE]
>
>Adobe rät davon ab, das AEM 6.4.8.1-Paket zu entfernen oder zu deinstallieren.

### Installieren des kumulativen Fix Packs {#install-cumulative-fix-pack}

Führen Sie die folgenden Schritte aus, um das Cumulative Fix Pack auf einer vorhandenen AEM 6.4.8.0-Instanz zu installieren:

1. Klicken Sie auf den Link [Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/cumulativefixpack/AEM-CFP-6.4.8.1) oder [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-1.0.zip) , um das Paket herunterzuladen.

1. Öffnen Sie [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) und klicken Sie auf Paket **hochladen** , um das Paket hochzuladen.

1. Wählen Sie den Paketnamen und klicken Sie auf **Installieren**.

>[!NOTE]
>
>**Das Dialogfeld auf der Benutzeroberfläche von Package Manager wird in einigen Fällen während der Installation von 6.4.8.1 frühzeitig beendet.**
>
>Es wird daher empfohlen, auf die Stabilisierung der Fehlerprotokolle zu warten, bevor auf die Instanz zugegriffen wird. Der Benutzer muss auf bestimmte Protokolle im Zusammenhang mit der Deinstallation des Updater-Bundles warten, bevor sichergestellt wird, dass die Installation erfolgreich ist. In der Regel trifft dies auf Safari zu, kann aber mitunter auch auf allen anderen Browsern der Fall sein.

### Automatische Installation {#auto-installation}

Es gibt zwei Möglichkeiten, AEM 6.4.8.1 automatisch in einer laufenden Instanz zu installieren:

A. Platzieren Sie das Paket in ..Ordner */crx-quickstart/install*, während der Server läuft. Das Paket wird automatisch installiert.

B. Use the [HTTP API from Package Manager](https://helpx.adobe.com/de/experience-manager/aem-previous-versions.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>AEM 6.4.8.1 unterstützt keine Bootstrap-Installation.

### Bestätigen der Installation {#validate-install}

1. Auf der Seite &quot;Produktinformationen&quot;(*/system/console/production *) sollte nun die aktualisierte Versionszeichenfolge &quot;Adobe Experience Manager, Version 6.4.8.1&quot;unter &quot;Installierte Produkte&quot;angezeigt werden.
1. Alle OSGI-Bundles sind in der OSGI-Konsole entweder AKTIV oder FRAGMENT. (Verwenden Sie die Webkonsole: /system/console/bundles.)
1. Das OSGI-Bundle org.apache.jackrabbit.oak-core ist auf Version 1.8.17 oder höher (Web-Konsole verwenden: /system/console/bundles).

To determine the certified platform for running with this release of AEM Sites and Assets, see [Technical Requirements](../sites-deploying/technical-requirements.md).

>[!NHinweis]
>On successful installation of the package, an >informational message appears indicating that the content >package has installed successfully,  such as **&quot;Content Package AEM-6.4-Service-Pack-7 installed successfully.&quot;**

### Aktualisieren von Viewern für dynamische Medien (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM 6.4.8.1 enthält eine neue Version von Dynamic Media Viewern (5.10.1), mit der auf der Seite "Bildvorgabe"nach Duplikat gesucht werden kann. Kunden mit dynamischen Medien wird empfohlen, den folgenden Befehl auszuführen, um die standardmäßigen Viewer-Vorgaben in den aktuellen Zustand zu bringen.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

, der neue Viewer-Vorgaben in /conf kopieren wird.

### Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms nicht verwenden. Fehlerbehebungen in AEM Forms werden über ein separates Add-on-Paket bereitgestellt.

1. Stellen Sie sicher, dass Sie das AEM Cumulative Fix Pack installiert haben.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://helpx.adobe.com/experience-manager/6-4/forms/using/installing-configuring-aem-forms-osgi.html#InstallAEMFormsaddonpackage).

### Installieren des AEM Forms JEE-Installationsprogramms {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Überspringen Sie diesen Schritt, wenn Sie AEM Forms JEE nicht verwenden. Fehlerbehebungen in AEM Forms JEE werden über ein separates Installationsprogramm bereitgestellt.

Informationen zum Installieren des kumulativen Installationsprogramms für AEM Forms JEE und zur Konfiguration nach der Bereitstellung finden Sie unter [AEM Forms JEE-Patch-Installationsprogramm 0016](https://helpx.adobe.com/de/aem-forms/quick-fixes/6-4/jee-patch-0016.html).

### Uber Jar {#uber-jar}

The Uber Jar for AEM 6.4.8.1 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8.1/).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.1</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Entfernte/veraltete Funktionen {#removed-deprecated-features}

Dieser Abschnitt listet Funktionen und Fähigkeiten auf, die aus AEM 6.4 entfernt oder veraltet sind.

| Bereich | Funktion | Ersatz | Version |
|---|---|---|---|
| Assets | Tag-Aktion für Teilassets verwalten | Kein Ersatz vorhanden. | AEM 6.4.2.0 |
| Assets und Adobe Creative Cloud-Integration | [Die gemeinsame Nutzung](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/creative-cloud.html) von AEM in Creative Cloud-Ordnern wurde in AEM 6.2 eingeführt, um kreativen Benutzern Zugriff auf Assets aus AEM zu geben. Eine neue Funktion der Creative Cloud-Anwendung, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus.  Adobe wird die Ordnerfreigabe nicht weiter verbessern. Während die Funktion in AEM enthalten ist, empfehlen Kunden dringend, den Ersatz zu verwenden. | Adobe Asset Link oder Desktop-App. Weitere Informationen finden Sie im Artikel zur [AEM Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Bekannte Probleme {#known-issues}

* Die Aktualisierung von [!DNL chrome] Version 83 verursacht ein Problem beim Erstellen von Paketen. Verwenden Sie andere verfügbare Browser, z. B. [!DNL Internet Explorer] und [!DNL Firefox]andere Installationsoptionen für AEM-Standardpakete, um das Problem zu beheben.

* Es kann keine E-Mail mit dem AEM-Standard-E-Mail-Sender an den Remote-SMTP-Server gesendet werden, da nur die Kommunikation mit TLS v1.2 möglich ist. Entfernen Sie das Bundle `javax.mail:mail:1.5.0-b01` aus `system/console` und aktualisieren Sie die Bundles, um das Problem zu beheben.

Informationen zu bekannten Problemen mit AEM 6.4.8.0 Service Pack finden Sie unter [AEM 6.4.8.0 Service Pack - Versionshinweise](sp-release-notes.md).

## OSGi-Bundles und Inhaltspakete sind enthalten {#osgi-bundles-and-content-packages-included}

Die folgenden Dokumente Liste der OSGi-Pakete und Inhaltspakete in AEM 6.4.8.1.

Liste der in AEM 6.4.8.1 enthaltenen OSGi-Bundles

[Datei laden](assets/6.4.8.1_osgi_bundles.txt)

Liste der in AEM 6.4.8.1 enthaltenen Inhaltspakete

[Datei laden](assets/6.4.8.1_content_packages.txt)

## Hilfreiche Ressourcen {#helpful-resources}

* [Versionshinweise zu AEM 6.4](../release-notes/release-notes.md)
* [AEM-Produktseite](https://www.adobe.com/solutions/web-experience-management.html)
* [Dokumentation zu AEM 6.4](https://helpx.adobe.com/de/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

## Eingeschränkte Sites {#restricted-sites-new}

Diese Sites sind nur für Kunden verfügbar. Wenn Sie Kunde sind und Zugriff benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

* [Produktdownload unter licensing.adobe.com](https://licensing.adobe.com/)
* [Wenden Sie sich an den Kundensupport.](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
