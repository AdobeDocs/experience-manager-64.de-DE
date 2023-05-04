---
title: Adaptives Formular formatieren
seo-title: Style your adaptive form
description: Erfahren Sie, wie Sie ein benutzerdefiniertes Design erstellen, individuelle Komponenten formatieren und Webfonts in einem Design verwenden
seo-description: Learn to create a custom theme, style individual components, and use web fonts in a theme
page-status-flag: de-activated
uuid: ffb2cc22-baaf-4525-a2e3-29f39271c670
topic-tags: introduction
discoiquuid: 655303a4-99bb-4ba3-9d50-a178f5edcf85
feature: Adaptive Forms
exl-id: 0ccf43eb-f0c6-4204-8325-f891caa8f5af
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2085'
ht-degree: 56%

---

# Adaptives Formular formatieren {#do-not-publish-style-your-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Erfahren Sie, wie Sie ein benutzerdefiniertes Design erstellen, individuelle Komponenten formatieren und Webfonts in einem Design verwenden

![](do-not-localize/08-style_your_adaptiveformmain.png)

Dieses Tutorial ist ein Schritt im [Erstellen Ihres ersten adaptiven Formulars](create-your-first-adaptive-form.md) Reihe. Es wird empfohlen, der Reihe in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, auszuführen und zu demonstrieren.

## Über das Tutorial  {#about-the-tutorial}

Sie können Designs verwenden, um ein adaptives Formular mit einem eindeutigen Erscheinungsbild und Stil zu versehen. Sie können Standarddesigns anwenden, die mit dem adaptiven Formulareditor bereitgestellt werden, oder eigene benutzerdefinierte Designs erstellen. AEM Forms stellt eine [Design-Editor](themes.md) um benutzerdefinierte Designs zu erstellen. Ein einzelnes Design kann für dasselbe adaptive Formular, das auf einem Mobilgerät, Tablet oder Desktop geöffnet wird, ein anderes Erscheinungsbild bieten. Frühere Kenntnisse über CSS oder LESS sind nicht erforderlich, um den Design-Editor zu verwenden, sind jedoch wünschenswert.

Am Ende des Tutorials lernen Sie Folgendes:

* Anwenden eines Standarddesigns auf ein adaptives Formular
* Erstellen eines Designs für ein adaptives Formular mit dem Design-Editor
* Gestalten einzelner Komponenten
* Bonusabschnitt: Verwenden von Webfonts in einem benutzerdefinierten Design

Das Formular sieht nach Abschluss des Tutorials wie folgt aus:

![Formular mit einem benutzerdefinierten Thema](assets/styled-adaptive-form.png)

## Bevor Sie beginnen {#before-you-start}

Laden Sie die unten aufgeführten Header- und Logo-Bilder auf Ihren lokalen Computer herunter. Die Kopfzeile des adaptiven Formulars `shipping-address-add-update-form` verwendet die kopfzeilenartigen und Logo-Bilder. Das kopfzeilenartige Bild erscheint auf der rechten Seite der Kopfzeile.

[Datei abrufen](assets/header-style.png)

[Datei abrufen](assets/logo-1.png)

## Schritt 1: Anwenden eines Designs auf Ihr adaptives Formular {#step-apply-a-theme-to-your-adaptive-form}

Der Editor für adaptive Formulare bietet mehrere vordefinierte Designs. Wenn Sie planen, keinen benutzerdefinierten Stil für Ihr adaptives Formular zu verwenden, können Sie Ihre adaptiven Formulare auch mit einem vordefinierten Design veröffentlichen. Designs sind unabhängig von adaptiven Formularen. Sie können dasselbe Design auf mehrere adaptive Formulare anwenden. So wenden Sie ein Design auf ein adaptives Formular an:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.

   [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

1. Offene Eigenschaften von **Container für adaptive Formulare**. Navigieren Sie im Eigenschaftenbrowser zu **Allgemein** > **Adaptives Formulardesign**. Das Feld **Adaptives Formulardesign** listet alle vordefinierten und benutzerdefinierten Designs auf. Standardmäßig wird das Canvas-Design angewendet.
1. Wählen Sie ein Design aus dem **Adaptives Formulardesign** -Feld. Beispiel: **Umfragedesign**. Tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um das ausgewählte Design anzuwenden.

![Adaptives Formular mit dem Standarddesign](assets/default-adaptive-form.png)

**Abbildung:** *Adaptives Formular mit dem Standard-Design*

![Adaptives Formular mit dem Umfragedesign](assets/adaptive-form-with-survey-theme.png)

**Abbildung:** *Adaptives Formular mit dem Umfragedesign*

## Schritt 2: Aktualisieren des adaptiven Formulars {#step-update-your-adaptive-form}

Das oben angezeigte Design erfordert Änderungen am Platzhaltertext und -logo des vorhandenen adaptiven Formulars. Führen Sie die folgenden Schritte aus, um die erforderlichen Änderungen vorzunehmen:

1. Ändern Sie das vorhandene Logo und den Text der Kopfzeile. So entfernen Sie das Logo:

   1. Öffnen Sie das Formular im Formular-Editor.

      [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

   1. Tippen Sie auf das Logo-Bild in der Komponente Kopfzeile und anschließend auf ![cmppr](assets/cmppr.png) Eigenschaften. Tippen Sie in der Eigenschaft Bild auf „X“, um das vorhandene Logo-Bild zu entfernen.
   1. Tippen Sie auf Hochladen, wählen Sie „logo.png“ aus und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Änderungen zu speichern. Das Bild wurde im Abschnitt [Bevor Sie beginnen](/help/forms/using/style-your-adaptive-form.md#before-you-start) heruntergeladen.
   1. Tippen auf Kopfzeilentext, `We.Retail`, und anschließend auf ![aem_6_3_edit](assets/aem_6_3_edit.png) **Bearbeiten**. Ändern des Kopfzeilentextes in `we retail`. Anwenden der Fettformatierung nur auf `we`in `we retail`.

   ![we-retail-logo-text](assets/we-retail-logo-text.png)

1. Entfernen Sie Titel und fügen Sie Platzhaltertext hinzu:

   1. Tippen Sie auf das Feld „Kunden-ID“ und anschließend auf ![cmppr](assets/cmppr.png) „Eigenschaften“.
   1. Kopieren Sie den Inhalt des Felds **Titel** in das Feld **Platzhaltertext**.
   1. Löschen Sie den Inhalt des Felds **Titel** und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
   1. Wiederholen Sie die vorherigen drei Schritte für alle Textfelder, das numerische Feld und das E-Mail-Feld im Formular.

   ![updated-adaptive-form](assets/updated-adaptive-form.png)

## Schritt 3: Erstellen eines benutzerdefinierten Designs für Ihr adaptives Formular {#step-create-a-custom-theme-for-your-adaptive-form}

Sie können [Design-Editor](/help/forms/using/themes.md) um benutzerdefinierte Designs zu erstellen. Der Design-Editor ist ein allmächtiger WYSIWYG-Editor. Es ist eine visuelle Methode, CSS auf verschiedene Komponenten eines adaptiven Formulars anzuwenden. Es bietet feinere Steuerelemente zum Stilen von Komponenten und Bedienfeldern eines adaptiven Formulars.

Ein Design ist eine separate Entität wie adaptive Formulare. Sie enthält Stile (CSS) für die Komponenten und Bedienfelder eines adaptiven Formulars. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, wird der angegebene Stil auf die entsprechenden Komponenten eines adaptiven Formulars angewendet.

In diesem Tutorial gestalten Sie Kopf- und Fußzeilen, Text- und numerische Komponenten, Anlagenkomponenten und Schaltflächen. Beginnen wir mit dem Erstellen eines Designs: 

### Erstellen von Designs {#create-a-theme}

1. Melden Sie sich bei der AEM-Autoreninstanz an und navigieren Sie zu **Adobe Experience Manager** > **Formulare** > **Designs**. Die Standard-URL lautet [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes).
1. Tippen Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Design]**. Die Seite Design erstellen mit den Feldern zum Erstellen eines Designs wird angezeigt. Die Felder „Titel“ und „Name“ sind obligatorisch.

   * **Titel:** Geben Sie einen Titel für das Design an. Zum Beispiel: **Globales Design.** Der Titel hilft Ihnen, das Design in der Liste der Designs zu identifizieren.
   * **Name**: Geben Sie den Namen des Designs an. Beispiel: **Globales Thema.** Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Alle ungültigen Eingaben werden durch Bindestriche ersetzt.

1. Tippen Sie auf **Erstellen**. Ein Design wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt. Tippen Sie auf **Öffnen**, um das neu erstellte Design in einer neuen Registerkarte zu öffnen. Design wird im Design-Editor geöffnet. Für die Formatierung verwendet der Design-Editor ein vordefiniertes adaptives Formular, das im Lieferumfang von AEM Forms enthalten ist.

   Informationen zur Verwendung der Benutzeroberfläche des Design-Editors finden Sie unter [Informationen zum Design-Editor](/help/forms/using/themes.md#aboutthethemeeditor).

1. Tippen Sie auf **Designoptionen** ![theme-options](assets/theme-options.png) > **Konfigurieren**. Wählen Sie im Feld **Vorschauformular** das adaptive Formular **shipping-address-add-update-form** und tippen Sie zunächst auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), dann auf **Speichern**. Jetzt ist der Design-Editor konfiguriert, um Ihr eigenes adaptives Formular anstelle des adaptiven Standardformulars zu benutzen. Tippen Sie auf **Abbrechen**, um zum Design-Editor zurückzukehren.

   ![custom-theme](assets/custom-theme.png)

   **Abbildung:** *Design-Editor mit dem adaptiven Formular „shipping-address-add-update-form“*

   ![create-a-theme](assets/create-a-theme.png)

   **Abbildung:** *Adaptives Formular mit dem Standardformular*

### Stilkopfzeile und -fußzeile {#style-header-and-footer}

Kopf- und Fußzeile bieten ein konsistentes und unverwechselbares Erscheinungsbild für ein adaptives Formular. Im Allgemeinen enthält die Kopfzeile das Logo und den Namen der Organisation, die Fußzeile enthält Copyright-Informationen und diese bleiben in mehreren Formularen einer Organisation identisch. So gestalten Sie Kopf- und Fußzeile des adaptiven Formulars shipping-address-add-update-form :

1. Navigieren Sie zum **Kopfzeile** > **Text** im Bedienfeld Selektoren . Das Bedienfeld Selektoren befindet sich auf der linken Seite des Design-Editors. Wenn das Bedienfeld nicht sichtbar ist, tippen Sie auf ![Seitliches Bedienfeld ein/aus](assets/toggle-side-panel.png) Seitliches Bedienfeld ein/aus.

1. Legen Sie die folgenden Eigenschaften im Akkordeon **Text** fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschaft | Wert |
   |---|---|
   | Schriftfamilie | Arial |
   | Schriftfarbe | FFFFFF |
   | Schriftgrad | 54 px |

1. Tippen Sie zunächst auf das Kopfzeilen-Widget und dann auf **Kopfzeile**. Die Optionen zum Formatieren des Kopfzeilen-Widgets werden auf der linken Seite angezeigt. Erweitern Sie das Akkordeon **Abmessungen und Position**, legen Sie für die **Höhe** `120px` fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Erweitern Sie das Akkordeon Hintergrund des Kopfzeilen-Widgets und legen Sie für die **Hintergrundfarbe** `F6921E.` fest.

   Bewegen Sie den Mauszeiger über **Bild und Verlauf** > **+ Hinzufügen** und tippen Sie auf **Bild**. Legen Sie die folgenden Eigenschaften fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschaft | Wert |
   |---|---|
   | image | Laden Sie die Datei header-style.png hoch. Das Bild wurde im Abschnitt [Bevor Sie beginnen](/help/forms/using/style-your-adaptive-form.md#before-you-start) heruntergeladen. |
   | Position | Rechts unten |
   | Anordnung | Keine Wiederholung |

1. Tippen Sie im Design-Editor auf das Logo in der Kopfzeile und tippen Sie auf **Kopfzeilen-Logo**. Erweitern Sie das Akkordeon „Abmessungen und Position“, legen Sie die folgenden Eigenschaften fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

<table> 
 <tbody> 
  <tr> 
   <td>Rand</td> 
   <td>Wert</td> 
  </tr> 
  <tr> 
   <td>Rand</td> 
   <td> 
    <ul> 
     <li>Oben: 1,5rem</li> 
     <li>Unten: -35px</li> 
     <li>Links: 1rem<strong><br /> </strong></li> 
    </ul> <p><strong>Tipp:</strong> Tippen Sie auf das Link-Symbol<img src="assets/link.png">, um einen anderen Wert für jedes Feld zur Verfügung zu stellen.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Höhe</td> 
   <td>4.75rem</td> 
  </tr> 
 </tbody> 
</table>

1. Tippen Sie auf das Fußzeilen-Widget und tippen Sie auf **Fußzeile**. Erweitern Sie das Akkordeon **Hintergrund**, legen Sie für die **Hintergrundfarbe** `F6921E` fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

### Formatieren Sie die Datenerfassungskomponente und wenden Sie einen Hintergrund auf das adaptive Formular an {#style-the-data-capture-component-and-apply-a-background-to-the-adaptive-form}

Sie können mehrere Komponenten in einem adaptiven Formular verwenden, um Daten zu erfassen. Beispiel: Textfeld und numerisches Feld. Sie können für alle Datenerfassungskomponenten einen identischen Stil bereitstellen oder jeder Komponente einen eigenen Stil zuweisen. In diesem Lernprogramm wird ein identischer Stil auf numerische Felder (Kunden-ID, Postleitzahl) und Textfelder (Kunden-ID, Name, Lieferadresse, Status, E-Mail) angewendet. So gestalten Sie die Datenerfassungskomponenten:

1. Tippen Sie zunächst auf das Feld Kunden-ID und dann auf die Option **Feld-Widget**. Legen Sie die folgenden Eigenschaften fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

<table> 
 <tbody> 
  <tr> 
   <td>Akkordeon</td> 
   <td>Eigenschaft</td> 
   <td>Wert</td> 
  </tr> 
  <tr> 
   <td>Rahmen</td> 
   <td>Rahmenfarbe (Hex-RGB)</td> 
   <td>A7A9AC</td> 
  </tr> 
  <tr> 
   <td>Rahmen</td> 
   <td>Rahmenradius </td> 
   <td> 
    <ul> 
     <li>Oben: 7px<br /> </li> 
     <li>Rechts: 7px<br /> </li> 
     <li>Unten: 7px<br /> </li> 
     <li>Links: 7px<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Schriftfamilie</td> 
   <td>Arial</td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Schriftfarbe</td> 
   <td>939598<br /> </td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Schriftgrad</td> 
   <td>18 px</td> 
  </tr> 
  <tr> 
   <td>Dimensionen und Position</td> 
   <td>Breite</td> 
   <td>60%</td> 
  </tr> 
  <tr> 
   <td>Dimensionen und Position</td> 
   <td>Rand</td> 
   <td> 
    <ul> 
     <li>Links: 10rem</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

1. Tippen Sie zunächst auf den leeren Bereich über dem Feld Kunden-ID und dann auf **Responsive Bereichscontainer**. Legen Sie den **Hintergrund** > **Hintergrundfarbe** auf F1F2F2 fest. Tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   ![](do-not-localize/responsive-panel-container.png)

### Gestalten Sie die Schaltflächen {#style-the-buttons}

Sie können ein benutzerdefiniertes Design verwenden, um allen Schaltflächen des adaptiven Formulars einen identischen Stil zuzuweisen, bzw. einen [Inline-Stil](/help/forms/using/inline-style-adaptive-forms.md), um einen Stil einer bestimmten Schaltfläche zuzuweisen. So gestalten Sie die Schaltflächen:

1. Tippen Sie auf **Senden** und dann auf **Option**. Legen Sie die folgenden Eigenschaften fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

<table> 
 <tbody> 
  <tr> 
   <td>Akkordeon</td> 
   <td>Eigenschaft</td> 
   <td>Wert</td> 
  </tr> 
  <tr> 
   <td>Hintergrund</td> 
   <td>Hintergrundfarbe</td> 
   <td>F6921E</td> 
  </tr> 
  <tr> 
   <td>Rahmen<br /> </td> 
   <td>Rahmenfarbe (Hex-RGB)</td> 
   <td>F6921E</td> 
  </tr> 
  <tr> 
   <td>Rahmen</td> 
   <td>Rahmenradius </td> 
   <td> 
    <ul> 
     <li>Oben: 7px<br /> </li> 
     <li>Rechts: 7px<br /> </li> 
     <li>Unten: 7px<br /> </li> 
     <li>Links: 7px</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Text<br /> </td> 
   <td>Schriftfamilie</td> 
   <td>Arial</td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Schriftfarbe</td> 
   <td>FFFFFF</td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Schriftgrad</td> 
   <td>18 px</td> 
  </tr> 
 </tbody> 
</table>

1. [Anwenden des benutzerdefinierten Designs](/help/forms/using/style-your-adaptive-form.md#step-apply-a-theme-to-your-adaptive-form), Globales Design in Ihr adaptives Formular. Wenn der Stil das adaptive Formular nicht widerspiegelt, bereinigen Sie den Browser-Cache und versuchen Sie es erneut. 

   ![style-data-collection-components](assets/style-data-capture-components.png)

## Schritt 4: Gestalten einzelner Komponenten {#step-style-individual-components}

Einige Stile gelten nur für eine bestimmte Komponente. Diese Komponenten sind im Editor für adaptive Formulare formatiert.

1. Öffnen Sie Ihr adaptives Formular zum Bearbeiten. [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)
1. Wählen Sie in der oberen Leiste die Option **Stil**.

   ![style-option](assets/style-option.png)

1. Tippen Sie auf die Schaltfläche **Anhängen** und dann auf das Symbol ![aem_6_3_edit](assets/aem_6_3_edit.png). Stellen Sie die folgenden Eigenschaften im Akkordeon **Abmessungen und Position** ein:

   | Eigenschaft | Wert |
   |---|---|
   | Gleitkomma | Linksbündig |
   | Breite | 10% |

1. Tippen Sie auf die Option **Von Behörden anerkannter Adressnachweis** und dann auf das Symbol ![aem_6_3_edit](assets/aem_6_3_edit.png). Legen Sie die folgenden Eigenschaften fest:

<table> 
 <tbody> 
  <tr> 
   <td>Akkordeon</td> 
   <td>Eigenschaft</td> 
   <td>Wert</td> 
  </tr> 
  <tr> 
   <td>Abmessungen und Position</td> 
   <td>Gleitkomma</td> 
   <td>Linksbündig</td> 
  </tr> 
  <tr> 
   <td>Abmessungen und Position</td> 
   <td>Breite</td> 
   <td>73%</td> 
  </tr> 
  <tr> 
   <td>Abmessungen und Position</td> 
   <td>Auffüllung</td> 
   <td> 
    <ul> 
     <li>Links: 10px</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Abmessungen und Position</td> 
   <td>Höhe</td> 
   <td>40 px</td> 
  </tr> 
  <tr> 
   <td>Abmessungen und Position<br /> </td> 
   <td>Rand</td> 
   <td><br /> 
    <ul> 
     <li>Rechts: 2rem</li> 
     <li>Links: 10rem </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Hintergrund</td> 
   <td>Hintergrundfarbe</td> 
   <td>FFFFFF</td> 
  </tr> 
  <tr> 
   <td>Rahmen</td> 
   <td>Rahmenbreite</td> 
   <td>1 px</td> 
  </tr> 
  <tr> 
   <td>Rahmen</td> 
   <td>Rahmenstil</td> 
   <td>Durchgehend</td> 
  </tr> 
  <tr> 
   <td>Rahmen</td> 
   <td>Rahmenfarbe (Hex-RGB)</td> 
   <td>A7A9AC</td> 
  </tr> 
  <tr> 
   <td>Rahmen</td> 
   <td>Rahmenradius</td> 
   <td>7 px</td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Schriftfamilie</td> 
   <td>Arial</td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Schriftfarbe</td> 
   <td>BCBEC0</td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Schriftgrad</td> 
   <td>18 px</td> 
  </tr> 
  <tr> 
   <td>Text</td> 
   <td>Zeilenhöhe</td> 
   <td>2</td> 
  </tr> 
 </tbody> 
</table>

1. Tippen Sie auf die Schaltfläche **Senden** und dann auf das Symbol ![aem_6_3_edit](assets/aem_6_3_edit.png). Legen Sie die folgenden Eigenschaften fest:

<table> 
 <tbody> 
  <tr> 
   <td>Akkordeon</td> 
   <td>Eigenschaft</td> 
   <td>Wert</td> 
  </tr> 
  <tr> 
   <td>Dimensionen und Position</td> 
   <td>Gleitkomma</td> 
   <td>Rechtsbündig</td> 
  </tr> 
  <tr> 
   <td>Dimensionen und Position</td> 
   <td>Rand</td> 
   <td> 
    <ul> 
     <li>Oben: 5rem</li> 
     <li>Rechts: 14rem</li> 
     <li>Unten: 20 px</li> 
     <li>Links: 20 px<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Hintergrund</td> 
   <td>Hintergrundfarbe</td> 
   <td>F6921E</td> 
  </tr> 
  <tr> 
   <td>Rahmen</td> 
   <td>Rahmenfarbe (Hex-RGB)</td> 
   <td>F6921E</td> 
  </tr> 
 </tbody> 
</table>

![styled-adaptive-form-1](assets/styled-adaptive-form-1.png)

## Schritt 5: Bonusabschnitt: Verwenden von Webfonts in einem benutzerdefinierten Design {#step-bonus-section-using-web-fonts-in-a-custom-theme}

Sie können verschiedene Schriftarten verwenden, um ein adaptives Formular zu entwerfen. Auf allen Geräten, auf denen das adaptive Formular angezeigt wird, sind die Schriftarten zum Entwerfen des adaptiven Formulars möglicherweise nicht vorhanden. Sie können einen Webfont-Dienst verwenden, um erforderliche Schriftarten auf dem Zielgerät bereitzustellen.

Adobe Typekit ist ein Webfonts-Dienst. Sie können den Dienst mit adaptiven Formularen konfigurieren und verwenden. So verwenden Sie Adobe Typekit in einem adaptiven Formular:

>[!NOTE]
>
>![typekit-to-adobe-fonts](assets/typekit-to-adobe-fonts.png) Typekit wird jetzt als Adobe Fonts bezeichnet und ist in Creative Cloud- und anderen Abonnements enthalten. [Weitere Informationen](https://fonts.adobe.com/)

1. Erstellen Sie eine [Adobe Typekit](https://typekit.com/) , erstellen Sie ein Kit, fügen Sie dem Kit die Schriftart Myriad Pro hinzu, veröffentlichen Sie das Kit und erhalten Sie die Kit-ID. Es ist erforderlich, Adobe Typekit-Schriftarten (Webfonts) in einem adaptiven Formular zu verwenden.
1. Navigieren Sie auf dem AEM Forms-Server zu ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **Adobe Experience Manager** > **Instrumente** ![Hammer](assets/hammer.png) > **Implementierung** > **Cloud Services**. Navigieren Sie auf der Seite &quot;Cloud Services&quot;zu **Drittanbieterdienste** > **Typekit** und klicken Sie auf **Konfigurieren** Jetzt unter &quot;Typekit&quot;. Wenn bereits eine Konfiguration verfügbar ist, klicken Sie auf die Schaltfläche + , um eine neue Instanz zu erstellen.

   Geben Sie im Dialogfeld „Konfiguration erstellen“ einen **Titel** für die Konfiguration an und klicken Sie auf **Erstellen**. Daraufhin werden Sie zur Seite „Konfiguration“ geleitet. Geben Sie im Dialogfeld Komponente bearbeiten, das angezeigt wird, Ihre **Kit-ID** ein und klicken Sie auf **OK**.

1. Konfigurieren Sie Ihr Design für die Verwendung der TypeKit-Konfiguration. Öffnen Sie in der Autorinstanz ein Design im Design-Editor **Globales Design**. Navigieren Sie im Design-Editor zu Themenoptionen![ Themenoptionen](assets/theme-options.png) > Konfigurieren. In **Typekit-Konfiguration** ein, wählen Sie das Kit aus und klicken Sie auf **Speichern**.

   Die Schriftarten, die dem Typekit hinzugefügt wurden, können im Abschnitt **Text** Akkordeon aller Komponenten.
