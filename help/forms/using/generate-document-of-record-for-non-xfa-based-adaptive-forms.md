---
title: Generierung eines Datensatzdokuments für adaptive Formulare
seo-title: Generate Document of Record for adaptive forms
description: Sie erfahren in diesem Artikel, wie Sie eine Vorlage für ein Datensatzdokument (DoR, Document of Record) für adaptive Formulare erstellen können.
seo-description: Explains how you can generate a template for a document of record (DoR) for adaptive forms.
uuid: 6c0664a4-a2eb-4ec5-bad0-cf4e2f4fe83d
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 1e533a8c-f200-40ca-b170-0e9abee8513e
noindex: true
feature: Adaptive Forms
exl-id: 2e7944e5-976e-49d2-a8d2-76c5868a92a2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2758'
ht-degree: 97%

---

# Generierung eines Datensatzdokuments für adaptive Formulare {#generate-document-of-record-for-adaptive-forms}

## Überblick {#overview}

Nachdem Ihre Kunden ein Formular gesendet haben, möchten sie im Allgemeinen einen Beleg (in gedruckter Form oder im Dokumentformat) über die eingegebenen Informationen behalten, um später darauf Bezug nehmen zu können. Dies wird als Datensatzdokument bezeichnet.

Sie erfahren in diesem Artikel, wie Sie ein Datensatzdokument für adaptive Formulare erstellen können.

>[!NOTE]
>
>Die automatische Generierung von Datensatzdokumenten wird für XFA-basierte adaptive Formulare nicht unterstützt. Sie können jedoch XDP verwenden, um das adaptive Formular als Datensatzdokument zu erstellen.

## Typen adaptiver Formulare und ihre Datensatzdokumente {#adaptive-form-types-and-their-documents-of-record}

Beim Erstellen eines adaptiven Formulars können Sie ein Formularmodell auswählen. Ihre Optionen sind:

* [Formularvorlagen](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p)

   Hier können Sie eine XFA-Vorlage für Ihr adaptives Formular auswählen. Wenn Sie eine XFA-Vorlage auswählen, können Sie die dazugehörige XDP-Datei als Datensatzdokument verwenden (siehe oben). 

* [XML-Schema](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-xml-or-json-schema-p)

   Ermöglicht die Auswahl einer XML-Schemadefinition für das adaptive Formular. Wenn Sie ein XML-Schema für Ihr adaptives Formular auswählen, können Sie Folgendes tun:

   * XFA-Vorlage für Datensatzdokument verknüpfen. Vergewissern Sie sich, dass die verknüpfte XFA-Vorlage dasselbe XML-Schema verwendet wie Ihr adaptives Formular.
   * Datensatzdokument automatisch generieren

* Ohne

   Ermöglicht die Erstellung eines adaptiven Formulars ohne Formularmodell. Das Datensatzdokument für Ihr adaptives Formular wird automatisch generiert.

Wenn Sie ein Formularmodell auswählen, konfigurieren Sie das Datensatzdokument mithilfe der Optionen, die unter „Konfiguration von Dokument aus Datensatzvorlage“ verfügbar sind. Weitere Informationen dazu finden Sie unter [Konfiguration der Datensatzdokument-Vorlage](#document-of-record-template-configuration).

## Automatisch generiertes Datensatzdokument {#automatically-generated-document-of-record}

Dank Datensatzdokument erhalten Ihre Kunden eine Kopie des übermittelten Formulars zum Ausdrucken. Wenn Sie automatisch ein Datensatzdokument generieren, wird jedes Mal das Datensatzdokument sofort aktualisiert, wenn Sie das Formular ändern. Beispiel: Sie entfernen für Kunden, die als ihr Land die USA angeben, das Feld „Alter“. Wenn diese Kunden ein Datensatzdokument erstellen, ist das Altersfeld im Datensatzdokument nicht sichtbar.

 Ein automatisch generiertes Datensatzdokument bietet folgende Vorteile:

* Es kümmert sich um die Datenbindung.
* Dadurch werden automatisch Felder ausgeblendet, die im Datensatzdokument zum Zeitpunkt des Sendens entsprechend markiert sind. Zusätzlicher Aufwand ist nicht erforderlich.
* Dies spart Zeit für die Entwicklung der Datensatzdokument-Vorlage.
* Außerdem können Sie auch verschiedene Formatierungsstile und Erscheinungsbilder ausprobieren, indem Sie unterschiedliche Basisvorlagen verwenden und dann das beste Design für Ihr Datensatzdokument auswählen. Stil und Erscheinungsbild sind optional. Wenn Sie sich auf keinen Stil festlegen, werden Systemstile als Standard festgelegt.
* Es stellt sicher, dass eine Änderung im Formular sofort im Datensatzdokument umgesetzt wird.

## Komponenten für die automatische Generierung eines Datensatzdokuments {#components-to-automatically-generate-a-document-of-record}

Sie benötigen die folgenden Komponenten, um ein Datensatzdokument für adaptive Formulare zu generieren:

**Adaptives Formular** Das adaptive Formular, für das Sie ein Datensatzdokument generieren möchten.

**Basisvorlage (empfohlen)** Das ist eine in AEM Designer erstellte XFA-Vorlage (XDP-Datei). Eine Basisvorlage wird verwendet, um die Stile und Branding-Informationen für die Datensatzdokument-Vorlage festzulegen.

Siehe [Basisvorlage eines Datensatzdokuments](#base-template-of-a-dor)

>[!NOTE]
>
>Die Basisvorlage eines Datensatzdokuments wird auch als Metavorlage des Datensatzdokuments bezeichnet.

**Datensatzdokument-Vorlage** Eine aus einem adaptiven Formular generierte XFA-Vorlage (XDP-Datei).

Weitere Informationen dazu finden Sie unter [Konfiguration der Datensatzdokument-Vorlage](#document-of-record-template-configuration).

**Formulardaten** Informationen, die von einem Benutzer in das adaptive Formular eingetragen werden. Sie werden mit der Datensatzdokument-Vorlage zusammengeführt, um das Datensatzdokument zu generieren.

## Zuordnen von adaptiven Formularelementen {#mapping-of-adaptive-form-elements}

Die folgenden Abschnitte beschreiben, wie adaptive Formularelemente im Datensatzdokument angezeigt werden.

### Felder {#fields}

<table> 
 <tbody> 
  <tr> 
   <th>Komponente des adaptiven Formulars</th> 
   <th>Zugehörige XFA-Komponente</th> 
   <th>Standardmäßig in der Datensatzdokument-Vorlage enthalten?</th> 
   <th>Anmerkungen</th> 
  </tr> 
  <tr> 
   <td>Schaltfläche</td> 
   <td>Schaltfläche</td> 
   <td>Nein</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Kontrollkästchen</td> 
   <td>Kontrollkästchen</td> 
   <td>Ja</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Datumsauswahl</td> 
   <td>Datum-/Uhrzeitfeld</td> 
   <td>Ja</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Dropdown-Liste</td> 
   <td>Dropdown-Liste</td> 
   <td>Ja</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Freihändige Unterschrift</td> 
   <td>Freihändige Unterschrift</td> 
   <td>Ja</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Numerisches Feld</td> 
   <td>Numerisches Feld</td> 
   <td>Ja</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Kennwortfeld</td> 
   <td>Kennwortfeld</td> 
   <td>Nein</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Optionsfeld</td> 
   <td>Optionsfeld</td> 
   <td>Ja</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Textfeld</td> 
   <td>Textfeld</td> 
   <td>Ja</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Schaltfläche „Zurücksetzen“</td> 
   <td>Schaltfläche „Zurücksetzen“</td> 
   <td>Nein</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Schaltfläche „Senden“</td> 
   <td><p>Schaltfläche „E-Mail senden“</p> <p>Schaltfläche „HTTP senden“</p> </td> 
   <td>Nein</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Allgemeine Geschäftsbedingungen</td> 
   <td> </td> 
   <td>Ja</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Dateianhang</td> 
   <td> </td> 
   <td>Nein</td> 
   <td>In Datensatzdokument-Vorlage nicht verfügbar. In Datensatzdokument-Vorlage nur über Anlagen verfügbar.</td> 
  </tr> 
 </tbody> 
</table>

### Container {#containers}

<table> 
 <tbody> 
  <tr> 
   <th>Komponente des adaptiven Formulars</th> 
   <th>Zugehörige XFA-Komponente</th> 
   <th>Anmerkungen</th> 
  </tr> 
  <tr> 
   <td>Bereich<br /> </td> 
   <td>Teilformular<br /> </td> 
   <td>Wiederholbare Bereichs-Maps, zugeordnet zu wiederholbarem Teilformular.</td> 
  </tr> 
 </tbody> 
</table>

### Statische Komponenten {#static-components}

| Komponente des adaptiven Formulars | Zugehörige XFA-Komponente | Anmerkungen |
|---|---|---|
| Bild | Bild | Die Komponenten TextDraw und Image (egal ob gebunden oder nicht) werden immer im Datensatzdokument eines XSD-basierten adaptiven Formulars angezeigt, es sei denn, sie werden mithilfe der Datensatzdokument-Einstellungen ausgeschlossen. |
| Text | Text |

>[!NOTE]
>
>In der klassischen Benutzeroberfläche sind verschiedene Registerkarten zum Bearbeiten der Feldeigenschaften vorhanden.

### Tabellen {#tables}

Die Tabellenkomponenten adaptiver Formulare, wie Kopf- und Fußzeile sowie Zeilen sind den entsprechenden XFA-Komponenten zugeordnet. Sie können wiederholbare Bereiche Tabellen im Datensatzdokument zuordnen.

## Basisvorlage eines Datensatzdokuments {#base-template-of-a-document-of-record}

Die Basisvorlage beinhaltet Informationen zu Stil und Erscheinungsbild des Datensatzdokuments. Es bietet Ihnen die Möglichkeit, das Standarderscheinungsbild des automatisch generierten Datensatzdokuments anzupassen. Beispiel: Sie möchten das Logo Ihres Unternehmens in der Kopfzeile und die Copyright-Informationen in der Fußzeile des Datensatzdokuments einfügen. Die Masterseite der Basisvorlage wird als Masterseite für die Datensatzdokument-Vorlage verwendet. Die Masterseite kann Informationen wie Kopfzeile, Fußzeile und Seitenzahl enthalten, die Sie auf das Datensatzdokument anwenden können. Sie können solche Informationen mithilfe der Basisvorlage für die automatische Erstellung des Datensatzdokuments auf das Datensatzdokument anwenden. Die Verwendung der Basisvorlage ermöglicht es Ihnen, die Standardeinstellungen von Feldern zu ändern.

Bitte folgen Sie bei der Entwicklung Ihrer Basisvorlage den [Konventionen für Basisvorlagen](#base-template-conventions).

## Konventionen für Basisvorlagen {#base-template-conventions}

Eine Basisvorlage wird verwendet, um Kopf- und Fußzeile, Stil und Erscheinungsbild eines Datensatzdokuments zu definieren. Die Kopf- und die Fußzeile können Informationen wie Firmenlogo und Copyright-Vermerk enthalten. Die erste Masterseite in der Basisvorlage wird als Masterseite für das Datensatzdokument kopiert und verwendet. Sie enthält Kopfzeile, Fußzeile und Seitenanzahl oder auch andere Informationen, die im Datensatzdokument auf allen Seiten angezeigt werden sollen. Wenn Sie eine Basisvorlage verwenden, die nicht den Konventionen für Basisvorlagen entspricht, wird die erste Masterseite aus der Basisvorlage dennoch in der Datensatzdokument-Vorlage verwendet. Es wird dringend empfohlen, dass Sie Ihre Basisvorlage gemäß den Konventionen entwerfen und sie für die automatische Erstellung von Datensatzdokumenten verwenden.

**Konventionen für Musterseiten**

* In der Basisvorlage sollten Sie das Stamm-Unterformular mit `AF_METATEMPLATE` und die Musterseite mit `AF_MASTERPAGE` benennen.

* Die Musterseite mit dem Namen `AF_MASTERPAGE`, die sich unterhalb des Stamm-Unterformulars `AF_METATEMPLATE` befindet, hat beim Extrahieren von Kopfzeilen-, Fußzeilen- und Stilinformationen Vorrang.

* Wenn `AF_MASTERPAGE` fehlt, wird die erste Musterseite in der Basisvorlage verwendet.

**Stilkonventionen für Felder**

* Wenn Sie einen Stil auf die Felder im Datensatzdokument anwenden, stellt die Basisvorlage die Felder im Teilformular `AF_FIELDSSUBFORM` bereit, das sich unter dem Stammteilformular `AF_METATEMPLATE` befindet.

* Die Eigenschaften dieser Felder werden auf die Felder im Datensatzdokument angewendet. Benennungen für diese Felder sollten der Form `AF_<name of field in all caps>_XFO` folgen. So sollte beispielsweise der Feldname für ein Kontrollkästchen `AF_CHECKBOX_XFO` lauten.

Gehen Sie wie folgt vor, um eine Basisvorlage in AEM Designer zu erstellen:

1. Klicken Sie auf **Datei > Neu**.
1. Wählen Sie die Option **Auf Basis einer Vorlage** aus.

1. Wählen Sie die Kategorie **Formulare – Aufzuzeichnendes Dokument**.
1. Wählen Sie „**DoR-Basisvorlage**“.
1. Klicken Sie auf **Weiter** und geben Sie die erforderlichen Informationen ein.

1. (Optional) Ändern Sie den Stil und das Erscheinungsbild von Feldern, die Sie auf die Felder im Datensatzdokument anwenden möchten.
1. Speichern Sie das Formular.

Sie können das gespeicherte Formular jetzt als Basisvorlage für das Datensatzdokument verwenden.\
Ändern oder entfernen Sie keine Skripte, die in der Basisvorlage vorhanden sind.

**Ändern der Basisvorlage**

* Wenn Sie auf Felder in der Basisvorlage keinen Stil anwenden, wird empfohlen, diese Felder aus der Basisvorlage zu entfernen, damit alle Aktualisierungen der Basisvorlage automatisch übernommen werden.
* Während des Änderns der Basisvorlage dürfen Sie keine Skripte entfernen, hinzufügen oder ändern.

>[!NOTE]
>
>Entwickeln Sie die Basisvorlage gemäß den Konventionen und folgen Sie dabei genau den oben beschriebenen Schritten.

## Konfiguration von Vorlagen für Datensatzdokumente {#document-of-record-template-configuration}

Konfigurieren Sie die Datensatzdokument-Vorlage Ihres Formulars, damit Ihre Kunden eine benutzerfreundliche Kopie des gesendeten Formulars zum Drucken herunterladen können. Als Datensatzdokument-Vorlage dient eine XDP-Datei. Das vom Kunden heruntergeladene Datensatzdokument ist entsprechend dem Layout formatiert, das in der XDP-Datei festgelegt ist.

Führen Sie die folgenden Schritte aus, um ein Datensatzdokument für adaptive Formulare zu konfigurieren:

1. Klicken Sie in der AEM-Autor-Instanz auf **Formulare > Formulare und Dokumente**.
1. Wählen Sie ein Formular aus und klicken Sie auf **Eigenschaften anzeigen**.
1. Klicken Sie im Fenster „Eigenschaften“ auf **Formularmodell**.

   Sie können ein Formularmodell auch bei der Erstellung eines Formulars auswählen.

   >[!NOTE]
   >
   >Achten Sie auf der Registerkarte „Formularmodell“ darauf, dass Sie **Schema** oder **Ohne** aus dem Dropdown-Menü **Auswählen** auswählen. **[!UICONTROL Das Datensatzdokument wird nicht für XFA-basierte oder adaptive Formulare mit einer Formularvorlage als Formularmodell unterstützt.]**

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Abschnitt „Konfiguration der Datensatzdokument-Vorlage“ eine der folgenden Optionen aus.

   **Keine** Wählen Sie diese Option aus, wenn Sie kein Datensatzdokument für das Formular konfigurieren möchten.

   **Formularvorlage als Dokument einer Datensatzvorlage verknüpfen** Wählen Sie diese Option, wenn Sie eine XDP-Datei haben, die Sie als Vorlage für das Datensatzdokument verwenden möchten. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.

   Die ausgewählte XDP-Datei wird mit dem adaptiven Formular verknüpft.

   **Datensatzdokument generieren** Wählen Sie diese Option aus, um eine XDP-Datei als Basisvorlage zum Definieren von Stil und Erscheinungsbild des Datensatzdokuments zu verwenden. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.

   **[!UICONTROL Wählen Sie diese Option, um eine XDP-Datei als Basisvorlage zum Definieren von Stil und Erscheinungsbild des Datensatzdokuments zu verwenden. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.]**

   **Forms-Vorlage als Basisvorlage auswählen, um Datensatzdokument zu generieren** Wählen Sie diese Option aus, um eine XDP-Datei als Basisvorlage zum Definieren von Stil und Erscheinungsbild des Datensatzdokuments zu verwenden. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.

   >[!NOTE]
   >
   >Stellen Sie in folgenden Fällen sicher, dass das Schema, das für die Erstellung von adaptivem Formular und Schema (Datenschema) des XFA-Formulars verwendet wird, gleich sind:
   >
   >* Ihr adaptives Formular ist Schema-basiert
   >* Sie verwenden die Datensatzdokument-Option „**Formularvorlage als Dokument aus Datensatzvorlage zuordnen**“.


1. Klicken Sie auf **Fertig**.

## Anpassen der Branding-Informationen im Datensatzdokument {#customize-the-branding-information-in-document-of-record}

Beim Generieren eines Datensatzdokuments können Sie auf der Registerkarte „Datensatzdokument“ Branding-Informationen für das Datensatzdokument ändern. Die Registerkarte „Datensatzdokument“ enthält Optionen für Logos, Aussehen, Layout, Kopf- und Fußzeile, zum Anpassen des Haftungsausschlusses sowie eine Optionen zum Entscheiden, ob Sie deaktivierte Kontrollkästchen und Optionsfeldern berücksichtigen möchten.

Für die Lokalisierung der Branding-Informationen, die Sie auf der Registerkarte für das Datensatzdokument eingeben, müssen Sie sicherstellen, dass das Gebietsschema des Browsers richtig eingestellt ist. Um die Branding-Informationen im Datensatzdokument anzupassen, gehen Sie wie folgt vor:

1. Wählen Sie einen Bereich (Stammbereich) im Datensatzdokument aus und tippen Sie dann auf ![Konfigurieren](assets/configure.png).
1. Tippen Sie auf ![dortab](assets/dortab.png). Die Registerkarte „Datensatzdokument“ wird angezeigt.
1. Wählen Sie entweder die Standardvorlage oder eine benutzerdefinierte Vorlage für das Rendern von Datensatzdokumenten aus. Wenn Sie die Standardvorlage auswählen, wird eine Miniaturvorschau des Datensatzdokuments in der Dropdown-Liste für Vorlagen angezeigt.

   ![brandingtemplate](assets/brandingtemplate.png)

   Wenn Sie eine benutzerdefinierte Vorlage auswählen, navigieren zu einer XDP auf Ihrem AEM Forms-Server und wählen sie aus. Wenn Sie eine Vorlage verwenden möchten, die sich noch nicht auf Ihrem AEM Forms-Server befindet, müssen Sie die XDP zuerst auf Ihren AEM-Server hochladen.

1. Abhängig davon, ob Sie eine Standard- oder eine benutzerdefinierte Vorlage wählen, werden einige oder alle der folgenden Eigenschaften auf der Registerkarte „Datensatzdokument“ angezeigt. Legen Sie die folgenden entsprechend fest:

   * **Logo-Bild:** Sie können entweder das Logo-Bild des adaptiven Formulars verwenden, eines in DAM auswählen oder eines von Ihrem Computer hochladen.
   * **Formulartitel**
   * **Kopfzeilentext**
   * **Haftungsausschluss-Bezeichnung**
   * **Haftungsausschluss**
   * **Text des Haftungsausschlusses**
   * **Akzentfarbe:** Die Farbe, in der Kopfzeilentext und Trennlinien im PDF des aufzuzeichnenden Dokuments dargestellt werden.
   * **Schriftfamilie:** Schriftfamilie des Textes im Datensatzdokument-PDF. 
   * **Für Kontrollkästchen und Optionsschaltflächenkomponenten nur ausgewählte Werte einblenden**
   * **Trennzeichen für mehrere ausgewählte Werte**
   * **Formularobjekte, die nicht mit dem Datenmodell verbunden sind, einschließen**
   * **Ausgeblendete Felder vom Datensatzdokument ausschließen**
   * **Beschreibung von Bereichen ausblenden**

   >[!NOTE]
   >
   >Wenn Sie eine Vorlage für ein adaptives Formular mit einem Designer-Version vor 6.3 verwenden, müssen Sie sicherstellen, dass im Root-Unterformular der Vorlage für das adaptive Formular folgendes vorhanden ist, damit Akzentfarbe und Schriftfamilie funktionieren:

   ```xml
   <proto>
   <font typeface="Arial"/>
   <fill>
   <color value="4,166,203"/>
   </fill>
   <edge>
   <color value="4,166,203"/>
   </edge>
   </proto>
   ```

1. Tippen Sie auf „Fertig“, um die Branding-Änderungen zu speichern.

## Tabellen- und Spalten-Layouts für Bereiche im Datensatzdokument {#table-and-column-layouts-for-panels-in-document-of-record}

Ihr adaptives Formular ist möglicherweise sehr lange und umfasst mehrere Formularfelder. Sie möchten eventuell das Datensatzdokument nicht als exakte Kopie des adaptiven Formulars speichern. Im Editor für adaptive Formulare können Sie jetzt das Tabellen- oder Spaltenlayout zum Speichern eines oder mehrerer Bereiche des adaptiven Formulars im Datensatzdokument auswählen.

Bevor Sie ein Datensatzdokument generieren, wählen Sie in den Einstellungen für den betreffenden Bereich unter „Layout für Dokument aus Datensatz“ entweder „Tabelle“ oder „Spalte“ aus. Die Felder im Bereich werden im Datensatzdokument entsprechend angeordnet.

![Felder in einem Bedienfeld, im Datensatzdokument im Tabellenlayout angeordnet](assets/dortablelayout.png)

Felder in einem Bedienfeld, im Datensatzdokument im Tabellenlayout angeordnet

![Felder in einem Bedienfeld, im Datensatzdokument im Spaltenlayout angeordnet](assets/dorcolumnlayout.png)

Felder in einem Bedienfeld, im Datensatzdokument im Spaltenlayout angeordnet

## Einstellungen für Datensatzdokumente {#document-of-record-settings}

Über die Datensatzdokument-Einstellungen können Sie Optionen festlegen, die Sie in das Datensatzdokument aufnehmen möchten. Beispiel: Eine Bank akzeptiert in einem Formular Name, Alter, Sozialversicherungsnummer und Telefonnummer. Das Formular generiert eine Bankkontonummer und Details zur Filiale. Sie können festlegen, dass nur Name, Sozialversicherungsnummer, Bankkonto und Filialendetails im Datensatzdokument angezeigt werden.

Die Datensatzdokument-Einstellungen einer Komponente sind unter den Eigenschaften verfügbar. Um auf die Eigenschaften einer Komponente zuzugreifen, wählen Sie die Komponente aus und klicken Sie auf ![cmppr](assets/cmppr.png) in der Überlagerung. Die Eigenschaften werden in der Seitenleiste mit den folgenden Einstellungen angezeigt.

**Einstellungen auf Feldebene**

* **Aus Datensatzdokument ausschließen**: Wird diese Eigenschaft aktiviert, erscheint das Feld im Datensatzdokument nicht. Dies ist eine skriptfähige Eigenschaft namens `excludeFromDoR`. Ihr Verhalten ist von der auf Formularebene befindlichen Eigenschaft **Felder aus DoR ausschließen, wenn sie ausgeblendet sind** abhängig.

* **Bereich als Tabelle anzeigen:** Durch die Aktivierung dieser Eigenschaft wird der Bereich im Datensatzdokument als Tabelle angezeigt, wenn er weniger als 6 Felder enthält. Gilt nur für den Bereich.
* **Titel aus Datensatzdokument ausschließen:** Wird diese Eigenschaft aktiviert, erscheint der Titel des Bereichs bzw. der Tabelle im Datensatzdokument nicht. Gilt nur für Bereiche und Tabellen.
* **Beschreibung aus Datensatzdokument ausschließen:** Wird diese Eigenschaft aktiviert, erscheint die Beschreibung des Bereichs bzw. der Tabelle im Datensatzdokument nicht. Gilt nur für Bereiche und Tabellen.

**Einstellungen auf Formularebene**

* **Ungebundene Felder in DoR einbeziehen:** Durch Festlegen dieser Eigenschaft werden ungebundenen Felder aus dem Schema-basierten adaptiven Formular im Datensatzdokument berücksichtigt. Diese Option ist standardmäßig aktiviert.
* **Felder aus Datensatzdokument ausschließen, wenn sie ausgeblendet sind**: Wenn aktiviert, wird das Verhalten der auf Feldebene befindlichen Eigenschaft „Aus Datensatzdokument ausschließen“ überschrieben, wenn sie nicht den Wert „true“ hat. Wenn Felder zum Zeitpunkt der Formularübermittlung ausgeblendet sind, werden sie vom Datensatzdokument ausgeschlossen, wenn die Eigenschaft den Wert „true“ hat, vorausgesetzt, die Eigenschaft „Aus Datensatzdokument ausschließen“ ist nicht festgelegt.

## Wichtige Aspekte beim Arbeiten mit einem Datensatzdokument {#key-considerations-when-working-with-document-of-record}

Beachten Sie die folgenden Hinweise und Einschränkungen beim Arbeiten mit einem Datensatzdokument für adaptive Formulare.

* Datensatzdokument-Vorlagen unterstützen keinen Rich-Text. Rich-Text im statischen adaptiven Formular oder bei den vom Endbenutzer ausgefüllten Informationen wird daher im Datensatzdokument als Nur-Text angezeigt.
* Dokumentfragmente in einem adaptiven Formular werden im Datensatzdokument nicht angezeigt. Adaptive Formularfragmente werden jedoch nicht unterstützt.
* Das Datensatzdokument wird nur zum Drucken verwendet.
* Die Inhaltsbindung in Datensatzdokumenten, die für XML-Schema-Basierte adaptive Formulare generiert werden, wird nicht unterstützt.
* Die Inhaltsbindung in Datensatzdokumenten, die für XML-Schema-Basierte adaptive Formulare generiert werden, wird nicht unterstützt.
* Lokalisierte Versionen des DoR werden nach Wunsch für ein Gebietsschema erstellt, wenn der Benutzer das Rendern des DoR anfordert. Die Lokalisierung von DoR tritt zusammen mit der Lokalisierung des adaptiven Formulars auf. Siehe [Verwenden von AEM-Übersetzungs-Arbeitsablauf zum Lokalisieren von adaptiven Formularen und Datensatzdokumenten](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).
