---
title: Adobe Classifications
seo-title: Adoben-Classifications
description: Erfahren Sie mehr über Adobe Classifications.
seo-description: Erfahren Sie mehr über Adobe Classifications.
uuid: 57fb59f4-da90-4fe7-a5b1-c3bd51159a16
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6787511a-2ce0-421a-bcfb-90d5f32ad35e
translation-type: tm+mt
source-git-commit: be46329cfe5c6fee28f616f2257e215df402e94d
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 71%

---


# Adobe Classifications{#adobe-classifications}

Adobe Classifications exportiert Classification-Daten planmäßig nach [Adobe Analytics](/help/sites-administering/adobeanalytics.md). Der Exporter ist eine Implementierung von **com.adobe.cq.scheduled.exporter.Exporter**.

So konfigurieren Sie diese Komponente:

1. Navigieren Sie über **Tools > Cloud-Services** zum Abschnitt **Adobe Analytics**.
1. Fügen Sie eine neue Konfiguration hinzu. Die Konfigurationsvorlage **Adobe Analytics-Klassifizierungen** wird unter der Konfiguration **Adobe Analytics-Framework** angezeigt. Geben Sie einen **Titel** und einen **Namen** nach Bedarf an:

   ![aa-25](assets/aa-25.png)

1. Klicken Sie auf **Erstellen**, um die Einstellungen zu konfigurieren.

   ![chlimage_1](assets/chlimage_1.png)

   Die Eigenschaften umfassen Folgendes:

   | **Feld** | **Beschreibung** |
   |---|---|
   | Aktiviert | Wählen Sie **Ja**, um die Adobe Classifications-Einstellungen zu aktivieren. |
   | Bei Konflikt überschreiben | Wählen Sie **Ja**, um Datenkollisionen zu überschreiben. Standardmäßig ist **Nein** eingestellt. |
   | Bearbeitete löschen | Ist **Ja** eingestellt, werden die verarbeiteten Knoten nach dem Export gelöscht. Der Standardwert lautet **False**. |
   | Beschreibung des Exportvorgangs | Geben Sie eine Beschreibung für den Adobe Classifications-Auftrag ein. |
   | Benachrichtigungs-E-Mail | Geben Sie eine E-Mail-Adresse für die Benachrichtigung zu Adoben-Classifications ein. |
   | Report Suite | Geben Sie die Report Suite ein, für die der Importauftrag ausgeführt werden soll. |
   | Datensatz | Geben Sie die Datensatz-Bezugs-ID ein, für die der Importauftrag ausgeführt werden soll. |
   | Transformator | Wählen Sie aus dem Dropdown-Menü eine Transformator-Implementierung aus. |
   | Datenquelle | Navigieren Sie zum Pfad für den Datencontainer. |
   | Zeitplan exportieren | Wählen Sie den Zeitplan für den Export aus. Die Standardeinstellung lautet alle 30 Minuten. |

1. Klicken Sie auf **OK**, um Ihre Einstellungen zu speichern.

## Ändern der Seitengröße {#modifying-page-size}

Datensätze werden seitenweise verarbeitet. Adobe Classifications erstellt standardmäßig Seiten mit einem Seitenformat von 1000.

Eine Adobe kann maximal 25000 Seiten umfassen, je nach Definition in den Klassifizierungen und kann von der Felix-Konsole aus geändert werden. Während des Exports sperrt Adobe Classifications den Quellknoten, um gleichzeitige Änderungen zu vermeiden. Der Knoten wird nach dem Export, bei einem Fehler oder beim Schließen der Sitzung wieder entsperrt.

So ändern Sie die Seitengröße:

1. Navigieren Sie zur OSGI-Konsole unter **https://&lt;host>:&lt;port>/system/console/configMgr** und wählen Sie **Adobe AEM Classifications Exporter**.

   ![aa-26](assets/aa-26.png)

1. Aktualisieren Sie die **Seitengröße für den Export** nach Bedarf und klicken Sie auf **Speichern**.

## SAINTDefaultTransformer  {#saintdefaulttransformer}

>[!NOTE]
>
>Adobe Classifications wurde früher als SAINT-Exporter bezeichnet.

Ein Exporter kann einen Transformator verwenden, um die Exportdaten in ein bestimmtes Format zu konvertieren. Für Adoben-Classifications wurde eine Subschnittstelle `SAINTTransformer<String[]>` bereitgestellt, die die Transformer-Schnittstelle implementiert. Diese Schnittstelle wird verwendet, um den Datentyp auf `String[]` zu beschränken, der von der SAINT-API verwendet wird, und um eine Marker-Schnittstelle zu haben, um solche Dienste zur Auswahl zu finden.

In der Standardimplementierung SAINTDefaultTransformer werden die untergeordneten Ressourcen der Exporteurquelle als Datensätze mit Eigenschaftsnamen als Schlüssel und Eigenschaftswerte als Werte behandelt. Die Spalte **Schlüssel** wird automatisch als erste Spalte hinzugefügt und enthält den Knotennamen. Benannte Eigenschaften (mit :) werden nicht berücksichtigt.

*Knotenstruktur:*

* id-classification `nt:unstructured`

   * 1 `nt:unstructured`

      * Produkt = ﻿﻿Mein Produktname (String)
      * Preis = 120,90 (String)
      * Größe = M (String)
      * Farbe = Schwarz (String)
      * Farbcode = 101 (String)

**SAINT-Kopfzeile und -Datensatz:**

| **Schlüssel** | **Produkt** | **Preis** | **Größe** | **Farbe** | **Farbe^Code** |
|---|---|---|---|---|---|
| 1 | Mein Produktname | 120,90 | M | black | 101 |

Die Eigenschaften umfassen Folgendes:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Eigenschaftspfad</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>transformer</td> 
   <td>Klassenname einer SAINTTransformer-Implementierung.</td> 
  </tr> 
  <tr> 
   <td>email</td> 
   <td>E-Mail-Adresse der Benachrichtigung.</td> 
  </tr> 
  <tr> 
   <td>reportsuites</td> 
   <td>Report Suite-IDs, für die der Importauftrag ausgeführt werden soll. </td> 
  </tr> 
  <tr> 
   <td>dataset</td> 
   <td>Datensatz-Bezugs-ID, für die der Importauftrag ausgeführt werden soll. </td> 
  </tr> 
  <tr> 
   <td>description</td> 
   <td>Auftragsbeschreibung <br /> </td> 
  </tr> 
  <tr> 
   <td>overwrite</td> 
   <td>Flag zum Überschreiben von Datenkollisionen. Der Standardwert lautet <strong>false</strong>.</td> 
  </tr> 
  <tr> 
   <td>checkdivisions</td> 
   <td>Flag zur Report Suites-Kompatibilitätsprüfung. Der Standardwert ist <strong>true</strong>.</td> 
  </tr> 
  <tr> 
   <td>deleteprocessed</td> 
   <td>Flag für die Löschung der verarbeiteten Knoten nach dem Export. Der Standardwert lautet <strong>false</strong>.</td> 
  </tr> 
 </tbody> 
</table>

## Automatisieren des Adobe Classifications-Exports  {#automating-adobe-classifications-export}

Sie können einen eigenen Workflow erstellen, damit bei jedem neuen Import der Workflow gestartet wird, um geeignete und korrekt strukturierte Daten in **/var/export/** zu erstellen und diese so in Adobe Classifications exportieren zu können.
