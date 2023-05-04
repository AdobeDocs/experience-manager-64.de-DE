---
title: Konfigurationseigenschaften für interaktive Kommunikation
seo-title: Interactive Communication configuration properties
description: Bearbeiten von Standardkonfigurationseigenschaften für interaktive Kommunikation
seo-description: Edit default configuration properties for Interactive Communications
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: Interactive Communication
exl-id: 2caf7242-8588-4fc9-9429-40e24416d6eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 48%

---

# Konfigurationseigenschaften für interaktive Kommunikation {#interactive-communications-configuration-properties}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Bearbeiten von Standardkonfigurationseigenschaften für interaktive Kommunikation

Interaktive Kommunikation enthält Eigenschaften, die nach der Installation des Pakets [AEM Forms Add-On](/help/forms/using/installing-configuring-aem-forms-osgi.md) automatisch konfiguriert werden. Autoren der interaktiven Kommunikation können diese Standardkonfigurationseigenschaften mit Hilfe der Seite **Konfiguration von Adobe Experience Manager Web Console** bearbeiten.

Öffnen Sie die Seite für die **Konfiguration von Adobe Experience Manager Web Console** unter der folgenden URL:

https://&lt;server>:&lt;port>/&lt;contextpath>/system/console/configMgr

Die Konfigurationseigenschaften umfassen Folgendes:

* [Konfiguration für Dokumentfragment](#document-fragments-configuration)
* [Korrespondenzkonfiguration erstellen](#create-correspondence-configuration)
* [Webkanal-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Webkanalthemen-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Konfiguration für Dokumentfragment {#document-fragments-configuration}

Tippen **Konfiguration von Dokumentfragmenten** auf **Konfiguration der Adobe Experience Manager-Web-Konsole** Seite, um die Konfigurationseigenschaften für Dokumentfragmente anzuzeigen.

<table> 
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Datenanzeigeformate</td> 
   <td>Gebietsschema-spezifisches Anzeigeformat für Felder, Variablen und Formulardatenmodellelemente, die beim Erstellen einer interaktiven Kommunikation für Druck- und Webkanäle verfügbar sind.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR und ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>Einzug</td> 
   <td>Die Breite einer Einzugseinheit, die auf Text in Listendokumentfragmenten angewendet wird.</td> 
   <td>12.7mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite der römischen Zahlen</td> 
   <td>Mindestbreite für das Aufzählungs- oder Zahlenfeld bei Verwendung von römischen Zahlen in Listendokumentfragmenten. </td> 
   <td>12.7mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite der Zahl</td> 
   <td>Mindestbreite für das Aufzählungs- oder Zahlenfeld bei nummerierten Listen, mit Ausnahme der römischen Zahlen in Listendokumentfragmenten.</td> 
   <td>8.0mm</td> 
   <td>Zahl</td> 
  </tr> 
 </tbody> 
</table>

## Erstellen der Korrespondenzkonfiguration {#create-correspondence-configuration}

Tippen Sie auf **Korrespondenz erstellen auf der Seite Konfiguration von Adobe Experience Manager Web Console** auf der Seite **Konfiguration von Adobe Experience Manager Web Console**, um die Konfigurationseigenschaften für Dokumentfragmente anzuzeigen.

| Eigenschaft | Beschreibung | Standard | Zulässige Werte |
|---|---|---|---|
| Gelösten Inhalt zur Bearbeitung anzeigen | Aktivieren Sie das Kontrollkästchen, um aufgelösten Inhalt (tatsächliche Werte anstelle von Platzhaltern) beim Bearbeiten des Textmoduls auf der Benutzeroberfläche für Agenten anzuzeigen. | Nicht ausgewählt | Nicht zutreffend |
| Anwenden von Wasserzeichen während der Vorschau | Aktivieren Sie das Kontrollkästchen, um das Wasserzeichen auf den Druckkanal der interaktiven Kommunikation im Vorschaumodus anzuwenden. | Nicht ausgewählt | Nicht zutreffend |

## Konfiguration des Web-Kanals für adaptive Formulare und interaktive Kommunikation {#adaptive-form-and-interactive-communication-web-channel-configuration}

Tippen Sie auf der Seite **Webkanal-Konfiguration für adaptive Formulare und interaktive Kommunikation** auf **Konfiguration von Adobe Experience Manager Web Console**, um die Konfigurationseigenschaften für den Webkanal für adaptive Formulare und interaktive Kommunikation anzuzeigen. In der folgenden Tabelle werden die Eigenschaften im Zusammenhang mit interaktiver Kommunikation beschrieben:

| Eigenschaft | Beschreibung | Standard | Zulässige Werte |
|---|---|---|---|
| Platzhalter anzeigen | Aktivieren Sie das Kontrollkästchen, um die Anzeige von Platzhaltern für Felder zu aktivieren, die in adaptiven Formularen und interaktiver Kommunikation enthalten sind. | ausgewählt | Nicht zutreffend |
| Maximale Cache-Einträge | Legen Sie die maximale Anzahl adaptiver Formulare und interaktiver Kommunikation fest, die mithilfe des Cache-Speichers abgerufen werden können. | 100 | Zahl |
| Dateinamen eindeutig machen | Aktivieren Sie das Kontrollkästchen, um eindeutige Namen für Dateien zu erhalten, die als Anhänge in Adaptive Forms und interaktive Kommunikation enthalten sind. | Nicht ausgewählt | Nicht zutreffend |

## Konfiguration der Web-Kanalthemen für adaptive Formulare und interaktive Kommunikation {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Tippen Sie auf der Seite **Konfiguration von Adobe Experience Manager Web Console** auf **Webkanalthemen-Konfiguration für adaptive Formulare und interaktive Kommunikation**, um die Konfigurationseigenschaften für die Webkanalthemen für adaptive Formulare und interaktive Kommunikation anzuzeigen.

<table> 
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Schriftlistenname</td> 
   <td>Liste der Schriftarten, die beim Erstellen der adaptiven Forms- und interaktiven Kommunikation verwendet werden können.</td> 
   <td><p>Georgien</p> <p>Buch Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Schwarz</p> <p>Auswirkungen</p> <p>Palatino-Linotyp</p> </td> 
   <td>Alle gültigen Adobe-Serverschriftarten</td> 
  </tr> 
 </tbody> 
</table>
