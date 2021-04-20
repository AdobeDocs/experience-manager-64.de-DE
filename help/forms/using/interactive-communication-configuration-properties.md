---
title: Konfigurationseigenschaften für interaktive Kommunikation
seo-title: Konfigurationseigenschaften für interaktive Kommunikation
description: Bearbeiten Sie die Standardkonfigurationseigenschaften für interaktive Kommunikation
seo-description: Bearbeiten Sie die Standardkonfigurationseigenschaften für interaktive Kommunikation
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: Interactive Communication
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 70%

---


# Konfigurationseigenschaften für interaktive Kommunikation {#interactive-communications-configuration-properties}

Bearbeiten Sie die Standardkonfigurationseigenschaften für interaktive Kommunikation

Interaktive Kommunikation enthält Eigenschaften, die nach der Installation des Pakets [AEM Forms Add-On](/help/forms/using/installing-configuring-aem-forms-osgi.md) automatisch konfiguriert werden. Autoren der interaktiven Kommunikation können diese Standardkonfigurationseigenschaften mit Hilfe der Seite **Konfiguration von Adobe Experience Manager Web Console** bearbeiten.

Öffnen Sie die Seite **Adobe Experience Manager Web Console Configuration** unter Verwendung der folgenden URL:

https://&lt;server>:&lt;port>/&lt;contextPath>/system/console/configMgr

Die Konfigurationseigenschaften umfassen Folgendes:

* [Konfiguration für Dokumentfragment](#document-fragments-configuration)
* [Korrespondenzkonfiguration erstellen](#create-correspondence-configuration)
* [Webkanal-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Webkanalthemen-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Konfiguration für Dokumentfragment {#document-fragments-configuration}

Tippen Sie auf der Seite **Adobe Experience Manager Web Console Configuration** auf **, um die Konfigurationseigenschaften für Dokument-Fragmente Ansicht.**

<table> 
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Default</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Datenanzeigeformate</td> 
   <td>Gebietsschemaspezifisches Anzeigeformat für Felder, Variablen und Formulardatenmodellelemente, das beim Erstellen einer interaktiven Kommunikation für Print- und Web-Kanal verfügbar ist.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR und ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>Einzug</td> 
   <td>Die Breite der einzelnen Einzugseinheit, die auf den Text in Listendokumentfragmenten angewendet wird.</td> 
   <td>12.7mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite von römischen Zahlen</td> 
   <td>Mindestbreite für das Aufzählungsfeld oder Zahlenfeld, wenn römische Zahlen in Listendokumentfragmenten verwendet werden. </td> 
   <td>12.7 mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite von Nummer</td> 
   <td>Mindestbreite für das Aufzählungsfeld oder Zahlenfeld, wenn römische Zahlen in Listendokumentfragmenten verwendet werden.</td> 
   <td>8.0mm</td> 
   <td>Number-Wert</td> 
  </tr> 
 </tbody> 
</table>

## Korrespondenzkonfiguration erstellen  {#create-correspondence-configuration}

Tippen Sie auf der Seite **Adobe Experience Manager Web Console Configuration** auf Korrespondenzkonfiguration erstellen **, um die Konfigurationseigenschaften für die Agent-Benutzeroberfläche Ansicht.**

| Eigenschaft | Beschreibung | Standard | Zulässige Werte |
|---|---|---|---|
| Gelösten Inhalt zur Bearbeitung anzeigen | Aktivieren Sie das Kontrollkästchen, um aufgelösten Inhalt (tatsächliche Werte anstelle von Platzhaltern) anzuzeigen, während Sie Textmodule auf der Agentenbenutzeroberfläche bearbeiten. | Nicht ausgewählt | Nicht zutreffend |
| Wasserzeichen während der Vorschau anwenden | Aktivieren Sie das Kontrollkästchen, um ein Wasserzeichen auf den Druckkanal der interaktiven Kommunikation im Vorschaumodus anzuwenden. | Nicht ausgewählt | Nicht zutreffend |

## Webkanal-Konfiguration für adaptive Formulare und interaktive Kommunikation  {#adaptive-form-and-interactive-communication-web-channel-configuration}

Tippen Sie auf der Seite **Adobe Experience Manager Web-Konsolenkonfiguration** auf **, um die Konfigurationseigenschaften für den Web-Kanal Adaptive Forms und Interactive Communications Ansicht.** Die folgende Tabelle beschreibt die Eigenschaften, die sich auf die interaktive Kommunikation bezieht:

| Eigenschaft | Beschreibung | Standard | Zulässige Werte |
|---|---|---|---|
| Platzhalter anzeigen | Aktivieren Sie das Kontrollkästchen, um die Anzeige von Platzhaltern für Felder zu aktivieren, die in adaptiven Formularen und in interaktiver Kommunikation enthalten sind. | Ausgewählt | Nicht zutreffend |
| Maximale Cache-Einträge | Legen Sie die maximale Anzahl an adaptiven Formularen und interaktiver Kommunikation fest, die mithilfe des Cache-Speichers abgerufen werden können. | 100 | Zahl |
| Dateinamen als eindeutig festlegen | Aktivieren Sie das Kontrollkästchen, um eindeutige Namen für Dateien zu erhalten, die als Anhänge in adaptiven Formularen und interaktiver Kommunikation enthalten sind. | Nicht ausgewählt | Nicht zutreffend |

## Webkanalthemen-Konfiguration für adaptive Formulare und interaktive Kommunikation  {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Tippen Sie auf der Seite **Adobe Experience Manager Web-Konsolenkonfiguration** auf **Kanal-Konfiguration für adaptive Formulare und interaktive Kommunikation**, um die Konfigurationseigenschaften für Themen des adaptiven Forms und des interaktiven Kommunikations-Web-Kanals Ansicht.

<table> 
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Name der Schriftartliste</td> 
   <td>Liste der Schriftarten, die beim Erstellen von adaptiven Formularen und interaktiver Kommunikation verwendet werden können.</td> 
   <td><p>Georgia</p> <p>Buch Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Schwarz</p> <p>Auswirkungen</p> <p>Palatino-Linotyp</p> </td> 
   <td>Alle gültigen Adobe-Server-Schriftarten</td> 
  </tr> 
 </tbody> 
</table>

