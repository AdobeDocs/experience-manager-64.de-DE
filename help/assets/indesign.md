---
title: Integrieren [!DNL Experience Manager] Assets mit Adobe InDesign Server
description: Informationen zur Integration [!DNL Experience Manager] Assets mit InDesign Server.
contentOwner: AG
feature: Publishing
role: Admin
exl-id: d80562f7-071c-460a-9c68-65f48d36fbd9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 52%

---

# Integration von Assets mit Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe Experience Manager Assets verwendet:

* Einen Proxy für den Lastenausgleich bei der Verarbeitung bestimmter Aufgaben. Ein Proxy ist eine [!DNL Experience Manager]-Instanz, die mit einem Proxy Worker kommuniziert, um eine bestimmte Aufgabe zu erfüllen, sowie mit anderen [!DNL Experience Manager]-Instanzen, um das Ergebnis bereitzustellen.
* Einen Proxy Worker zum Definieren und Verwalten einer bestimmten Aufgabe.

Diese können eine Vielzahl von Aufgaben abdecken; Beispielsweise die Verwendung einer Adobe InDesign Server zur Verarbeitung von Dateien.

Zum vollständigen Hochladen von Dateien in [!DNL Experience Manager] Assets, die Sie mit Adobe InDesign erstellt haben, wird ein Proxy verwendet. Hierbei wird ein Proxy Worker verwendet, um mit der Adobe InDesign Server zu kommunizieren, wobei [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) werden ausgeführt, um Metadaten zu extrahieren und verschiedene Ausgabeformate für [!DNL Experience Manager] Assets. Der Proxy Worker ermöglicht die bidirektionale Kommunikation zwischen dem InDesign Server und dem [!DNL Experience Manager] -Instanz(en) in einer Cloud-Konfiguration.

>[!NOTE]
>
>Adobe InDesign ist mit zwei Produkten ausgestattet:
>
>* [InDesign](https://www.adobe.com/de/products/indesign.html)\
   >  Damit können Sie Seiten-Layouts für den Druck bzw. die digitale Distribution entwerfen.
>
>* [InDesign Server](https://www.adobe.com/de/products/indesignserver.html)\
   >  Diese Engine ermöglicht die programmgesteuerte automatisierte Erstellung von Dokumenten, die auf denen basieren, die Sie mit InDesign entworfen haben. Die Engine fungiert als Dienst, der eine Schnittstelle seiner [ExtendScript](https://www.adobe.com/devnet/scripting.html)-Engine bereitstellt.\
   >  Die Skripte werden in ExtendScript geschrieben, das JavaScript ähnelt. Weitere Informationen zu Adobe InDesign-Skripten finden Sie unter [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
>


## So funktioniert die Extraktion {#how-the-extraction-works}

Die InDesign Server kann mit [!DNL Experience Manager] Assets, damit mit InDesign erstellte Dateien ( `.indd`) hochgeladen werden können, Ausgabedarstellungen generiert werden, *all* Medien, die extrahiert (z. B. Video) und als Assets gespeichert wurden:

>[!NOTE]
>
>Frühere Versionen von [!DNL Experience Manager] konnten XMP und die Miniaturansicht extrahieren, während jetzt alle Medien extrahiert werden können.

1. Hochladen Ihrer `.indd` Datei in [!DNL Experience Manager] Assets.
1. Ein Framework sendet Befehlsskripte via SOAP (Simple Object Access Protocol) an InDesign Server.


   Dieses Befehlsskript führt folgende Aktionen aus:

   * Rufen Sie die `.indd` -Datei.
   * Ausführen von InDesign Server-Befehlen:

      * Struktur, Text und alle Mediendateien werden extrahiert.
      * PDF- und JPG-Ausgabeformate werden generiert.
      * HTML- und IDML-Ausgabeformate werden generiert.
   * Posten Sie die resultierenden Dateien zurück in [!DNL Experience Manager] Assets.

   >[!NOTE]
   >
   >IDML ist ein XML-basiertes Format, das *alles* in der InDesign-Datei. Sie wird als komprimiertes Paket gespeichert, indem [Zip](https://www.techterms.com/definition/zip) Komprimierung.
   >
   >Siehe [Adobe InDesign-Austauschformate INX und IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) für weitere Informationen.

   >[!CAUTION]
   >
   >Wenn die InDesign Server nicht installiert oder nicht konfiguriert ist, können Sie dennoch eine `.indd` in [!DNL Experience Manager]. Die erzeugten Ausgabedarstellungen sind jedoch auf `png` und `jpeg`, können Sie nicht `html`, `idml` oder die Seitenausgabeformate.

1. Nach der Extraktion und Ausgabegenerierung:

   * Die Struktur wird auf einer `cq:Page` repliziert (Ausgabetyp).
   * Der extrahierte Text und die Dateien werden in [!DNL Experience Manager] Assets.
   * Alle Ausgabedarstellungen werden in [!DNL Experience Manager] Assets im Asset selbst.

## Integrieren von InDesign Server in [!DNL Experience Manager] {#integrating-the-indesign-server-with-aem}

So integrieren Sie die InDesign Server zur Verwendung mit [!DNL Experience Manager] Assets und nach der Konfiguration Ihres Proxys müssen Sie:

1. [Installieren Sie InDesign Server](#installing-the-indesign-server).
1. Falls erforderlich, [ [!DNL Experience Manager] konfigurieren Sie den Assets-Workflow](#configuring-the-aem-assets-workflow).

   Dies ist nur dann notwendig, wenn die Standardwerte für Ihre Instanz nicht geeignet sind.

1. Konfigurieren Sie einen [Proxy Worker für InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installieren von InDesign Server   {#installing-the-indesign-server}

So installieren und starten Sie die InDesign Server zur Verwendung mit [!DNL Experience Manager]:

1. Laden Sie Adobe InDesign Server herunter und installieren Sie ihn.

   >[!NOTE]
   >
   >InDesign Server (CS6 und höher).

1. Bei Bedarf können Sie die Konfiguration Ihrer InDesign Server-Instanz anpassen.

1. Starten Sie den Server über die Befehlszeile:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Dadurch wird der Server mit dem SOAP-Plug-in gestartet, das Port 8080 abhört. Alle Protokollmeldungen und Ausgaben werden direkt im Befehlsfenster angezeigt.

   >[!NOTE]
   >
   >Wenn Sie die Ausgabemeldungen in einer Datei speichern möchten, müssen Sie dazu eine Umleitung verwenden, z. B. unter Windows:
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Konfigurieren der [!DNL Experience Manager] Assets-Workflow {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager] Assets verfügt über einen vorkonfigurierten Workflow **DAM-Update-Asset**, der mehrere Prozessschritte speziell für das InDesign umfasst:

* [Extrahierung von Medien](#media-extraction)
* [Extrahierung von Seiten  ](#page-extraction)

Dieser Workflow wird mit Standardwerten konfiguriert, die für Ihr Setup in den verschiedenen Autoreninstanzen angepasst werden können. (Dies ist ein Standard-Workflow. Deshalb finden Sie weitere Information unter [Bearbeiten eines Workflows](/help/sites-developing/workflows-models.md#configuring-a-workflow-step).) Wenn Sie die Standardwerte (einschließlich SOAP-Port) verwenden, ist keine Konfiguration erforderlich.

Nach dem Setup laden Sie InDesign-Dateien in hoch [!DNL Experience Manager] Bei Assets (mit einer der üblichen Methoden) wird der für die Verarbeitung des Assets und Vorbereitung der verschiedenen Ausgabedarstellungen erforderliche Workflow Trigger. Testen Sie Ihre Konfiguration, indem Sie eine `.indd`[!DNL Experience Manager]-Datei in  Assets hochladen und auf diese Weise überprüfen, ob IDS verschiedene Ausgabeformate unter  erstellt. `<*your_asset*>.indd/Renditions`

#### Extrahierung von Medien {#media-extraction}

Dieser Schritt steuert die Extrahierung von Medien aus dem `.indd` -Datei.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Medien]** auf der Registerkarte **[!UICONTROL Argumente]** vornehmen.

![Argumente und Skriptpfade zum Extrahieren von Medien](assets/media_extraction_arguments_scripts.png)

Argumente und Skriptpfade zum Extrahieren von Medien

* **ExtendScript-Bibliothek**: Dies ist eine einfache HTTP-GET/POST-Methodenbibliothek, die von anderen Skripten benötigt wird.

* **Skripte erweitern**: Hier können Sie unterschiedliche Skriptkombinationen angeben. Wenn Ihre eigenen Skripte auf InDesign Server ausgeführt werden sollen, speichern Sie die Skripte unter `/apps/settings/dam/indesign/scripts`.

   Informationen zu InDesign-Skripten finden Sie unter [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>Ändern Sie nicht die ExtendScript-Bibliothek. Die Bibliothek bietet die HTTP-Funktionalität, die für die Kommunikation mit Sling erforderlich ist. Diese Einstellung gibt die Bibliothek an, die zur Verwendung an die Adobe InDesign Server gesendet werden soll.

Das Skript `ThumbnailExport.jsx`, das vom Workflow-Schritt „Extrahierung von Medien“ ausgeführt wird, generiert eine Miniaturansicht im JPG-Format. Diese Ausgabedarstellung wird vom Workflow-Schritt „Miniaturansichten verarbeiten“ dazu verwendet, die für [!DNL Experience Manager] erforderlichen statischen Ausgabedarstellungen zu rendern.

Sie können den Workflow-Schritt „Miniaturansichten verarbeiten“ so konfigurieren, dass statische Darstellungen in verschiedenen Größen generiert werden. Stellen Sie sicher, dass Sie die Standardwerte nicht entfernen, da sie von der [!DNL Experience Manager] Assets-Benutzeroberfläche. Schließlich entfernt der Workflow-Schritt Bildvorschau-Wiedergabe löschen die .jpg-Miniaturansicht, da sie nicht mehr benötigt wird.

#### Extrahierung von Seiten   {#page-extraction}

Dabei wird eine [!DNL Experience Manager]-Seite aus den extrahierten Elementen erstellt. Das Extrahieren von Daten aus einem Ausgabeformat (aktuell HTML oder IDML) erfolgt mithilfe eines Extrahierungs-Handlers. Diese Daten werden verwendet, um eine Seite mit PageBuilder zu erstellen.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Seiten]** auf der Registerkarte **Argumente** vornehmen.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Handler zur Seitenextrahierung**: Wählen Sie aus der Dropdown-Liste den Handler aus, den Sie verwenden möchten. Ein Extrahierungs-Handler arbeitet mit einem bestimmten Ausgabeformat, das mit einem entsprechenden `RenditionPicker` ausgewählt wird (siehe `ExtractionHandler`-API). Standardmäßig ist der IDML-Export-Extraktions-Handler verfügbar. Sie arbeitet auf der `IDML` Ausgabedarstellung, die im Schritt MediaExtract generiert wurde.

* **Seitenname**: Geben Sie den Namen an, den Sie der resultierenden Datei zuweisen möchten. Wenn Sie das Feld leer lassen, wird als Name „Seite“ gewählt (oder eine Ableitung, falls „Seite“ bereits vorhanden ist).

* **Seitentitel**: Geben Sie den Titel an, den Sie der resultierenden Datei zuweisen möchten.

* **Stammverzeichnis der Seite**: Der Pfad zum Stammverzeichnis der resultierenden Datei. Wenn Sie das Feld leer lassen, wird der Knoten mit den Ausgabeformaten des Assets verwendet.

* **Seitenvorlage**: Die zu verwendende Vorlage für das Generieren der resultierenden Seite.

* **Seiten-Design**: Das zu verwendende Seiten-Design für das Generieren der resultierenden Seite.

### Konfigurieren von Proxy Worker für InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Der Worker befindet sich in der Proxy-Instanz.

1. Erweitern Sie in der Tools-Konsole **[!UICONTROL Cloud Services-Konfigurationen]** im linken Bereich. Anschließend erweitern Sie den Eintrag **[!UICONTROL Cloud-Proxy-Konfiguration]**.

1. Doppelklicken Sie auf den **[!UICONTROL IDS-Worker]**, um ihn für die Konfiguration zu öffnen.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Konfigurationsdialogfeld zu öffnen und die erforderlichen Einstellungen vorzunehmen:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS-Pool**: Die SOAP-Endpunkte, die für die Kommunikation mit der InDesign Server verwendet werden sollen. Sie können Elemente nach Bedarf hinzufügen, entfernen und ordnen.

1. Klicken Sie zum Speichern auf **[!UICONTROL OK]**.

### Konfigurieren von Day CQ Link Externalizer  {#configuring-day-cq-link-externalizer}

Wenn die InDesign Server und [!DNL Experience Manager] sich auf verschiedenen Hosts befinden oder eine oder beide dieser Anwendungen nicht an Standardanschlüssen funktionieren, konfigurieren Sie **Day CQ Link Externalizer** , um den Hostnamen, Port und Inhaltspfad für die InDesign Server festzulegen.

1. Greifen Sie auf Configuration Manager über die URL `https://[AEM_server]:[port]/system/console/configMgr` zu.
1. Suchen Sie die Konfiguration **[!UICONTROL Day CQ Link Externalizer]**. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um sie zu öffnen.
1. Mithilfe der Einstellungen von Link Externalizer können Sie absolute URLs für die [!DNL Experience Manager] und für [!DNL InDesign Server]. Verwendung **[!UICONTROL Domänen]** -Feld zum Angeben des Hostnamens und des Kontextpfads für [!DNL Adobe InDesign Server]. Befolgen Sie die Anweisungen auf dem Bildschirm. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Externalizer-Einstellungen für Links](assets/link-externalizer-config.png)

### Aktivieren der parallelen Auftragsverarbeitung für InDesign Server {#enabling-parallel-job-processing-for-indesign-server}

Sie können jetzt die parallele Auftragsverarbeitung für IDS aktivieren.

Dazu müssen Sie zunächst die maximale Anzahl der parallelen Aufträge (`x`) festlegen, die ein InDesign Server verarbeiten kann:

* Auf einem einzigen Multiprozessorcomputer ist die maximale Anzahl von parallelen Aufträgen (x), die ein InDesign Server verarbeiten kann, eine weniger als die Anzahl der Prozessoren, die IDS ausführen.
* Wenn Sie IDS auf mehreren Computern ausführen, müssen Sie die Gesamtanzahl der verfügbaren Prozessoren (d. h. auf allen Computern) zählen und dann die Gesamtanzahl der Maschinen subtrahieren.

So konfigurieren Sie die Anzahl der parallelen IDS-Aufträge:

1. Öffnen Sie die Registerkarte **[!UICONTROL Konfigurationen]** der Felix-Konsole. Beispiel:    

   `http://localhost:4502/system/console/configMgr`

1. Wählen Sie die IDS-Verarbeitungsschlange unter:

   `Apache Sling Job Queue Configuration`

1. Satz:

   * **[!UICONTROL Typ]** - `Parallel`
   * **[!UICONTROL Maximal parallel ausführbare Aufträge]** –`<*x*>` (Berechnung siehe oben)

1. Speichern Sie diese Änderungen.
1. Um die Unterstützung für mehrere Sitzungen für Adobe CS6 und höher zu aktivieren, überprüfen Sie die `enable.multisession.name` Kontrollkästchen unter `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Erstellen Sie eine [Pool von &lt; `*x*>` IDS-Sekundäre durch Hinzufügen von SOAP-Endpunkten zur IDS Worker-Konfiguration](#configuring-the-proxy-worker-for-indesign-server).

   Wenn mehrere Computer mit InDesign Server arbeiten, fügen Sie SOAP-Endpunkte (Anzahl der Prozessoren pro Rechner -1) für jeden Computer hinzu.

   >[!NOTE]
   >
   >Wenn Sie mit einem Pool von Workern arbeiten, können Sie die Blockierungsliste von IDS-Workern aktivieren.
   >
   >Dazu aktivieren Sie das Kontrollkästchen „enable.retry.name“ unter der Konfiguration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`, die Wiederholungen von IDS-Aufträgen ermöglicht.
   >
   >Legen Sie in der Konfiguration `com.day.cq.dam.ids.impl.IDSPoolImpl.name` außerdem einen positiven Wert für den Parameter `max.errors.to.blacklist` fest, der die Anzahl der Auftragswiederholungen steuert, bevor ein IDS aus der Auftrags-Handler-Liste ausgeschlossen wird.
   >
   >Standardmäßig wird der IDS-Worker nach einer konfigurierbaren Zeit (`retry.interval.to.whitelist.name`) in Minuten erneut validiert. Wenn der Worker online gefunden wird, wird er aus der Blockierungsliste entfernt.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Unterstützung für Adobe InDesign Server 10.0 oder höher aktivieren {#enabling-support-for-indesign-server-or-higher}

Führen Sie für InDesign Server 10.0 oder höher die folgenden Schritte durch, um Unterstützung für Mehrfachsitzungen zu aktivieren.

1. Öffnen Sie Configuration Manager über Ihre [!DNL Assets] instance `https://[aem_server]:[port]/system/console/configMgr`.
1. Bearbeiten Sie die Konfiguration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Auswählen **[!UICONTROL ids.cc.enable]** und klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Verwenden Sie für die Integration von [!DNL InDesign Server] mit [!DNL Assets] einen Mehrkernprozessor, da die für die Integration notwendige Funktion „Sitzungsunterstützung“ auf Einzelkernsystemen nicht unterstützt wird.

## Experience Manager-Anmeldedaten konfigurieren {#configure-aem-credentials}

Sie können die standardmäßigen Administratorberechtigungen (Benutzername und Kennwort) für den Zugriff auf den InDesign-Server von Ihrem [!DNL Experience Manager] -Instanz ohne Unterbrechung der Integration mit dem Adobe InDesign-Server.

1. Wechseln zu `/etc/cloudservices/proxy.html`.
1. Geben Sie im Dialogfeld den neuen Benutzernamen und das neue Kennwort an.
1. Speichern Sie die Anmeldeinformationen.
