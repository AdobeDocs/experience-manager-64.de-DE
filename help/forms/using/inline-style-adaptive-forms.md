---
title: Inline-Stile für Komponenten adaptiver Formulare
seo-title: Inline CSS properties for adaptive form components
description: Sie können zwar benutzerdefinierte Stile auf ein adaptives Formular anwenden, Sie können aber auch Inline-CSS-Eigenschaften auf einzelne Komponenten eines adaptiven Formulars anwenden.
seo-description: While you can apply custom styles on an adaptive form, you can also apply inline CSS properties on individual components of an adaptive form.
uuid: ab948f02-3b41-4304-955b-6dd51d27088e
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 91a41bc1-3fa3-4467-b3f8-5570ba7757c0
feature: Adaptive Forms
exl-id: 8e7ba9d2-207f-419b-bcd5-74ba9b14ab92
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 37%

---

# Inline-Stile für Komponenten adaptiver Formulare {#inline-styling-of-adaptive-form-components}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können das Erscheinungsbild und den Stil eines adaptiven Formulars definieren, indem Sie Stile angeben, indem Sie [Design-Editor](/help/forms/using/themes.md). Außerdem können Sie Inline-CSS-Stile auf einzelne adaptive Formularkomponenten anwenden und die Änderungen sofort in der Vorschau anzeigen. Inline-Stile überschreiben die Formatierung, die im Design bereitgestellt wird.

## Verwenden von Inline-CSS-Eigenschaften {#apply-inline-css-properties}

So fügen Sie einer Komponente Inline-Stile hinzu:

1. Öffnen Sie das Formular im Formular-Editor und ändern Sie den Modus in den Formatierungsmodus. Um den Stilmodus zu aktivieren, tippen Sie in der Symbolleiste der Seite auf ](assets/canvas-drop-down.png)Arbeitsfläche-Dropdown![ > **Stil**.
1. Wählen Sie eine Komponente auf der Seite aus und tippen Sie auf die Schaltfläche „Bearbeiten“ ![Bearbeiten-Schaltfläche](assets/edit-button.png). Die Stileigenschaften werden in der Seitenleiste geöffnet.

   Sie können auch Komponenten aus der Formularhierarchie in der Seitenleiste auswählen. Die Hierarchie des Formulars ist als Formularobjekte in der Seitenleiste verfügbar.

   Sie können auch eine Komponente in der Seitenleiste auswählen. Im Modus Stil können Sie Komponenten sehen, die unter „Formularobjekte“ aufgeführt sind. Die Liste &quot;Formularobjekte&quot;in der Seitenleiste listet jedoch Komponenten wie Felder und Bereiche auf. Felder und Bedienfelder sind allgemeine Komponenten, die Komponenten wie Textfelder und Optionsfelder enthalten können.

   Wenn Sie eine Komponente aus der Seitenleiste auswählen, werden alle aufgelisteten Unterkomponenten und die Eigenschaften der ausgewählten Komponente angezeigt. Sie können eine bestimmte Unterkomponente auswählen und formatieren.

1. Klicken Sie auf eine Registerkarte in der Seitenleiste, um CSS-Eigenschaften anzugeben. Sie können Eigenschaften angeben, z. B.:

   * Abmessungen und Position (Anzeigeeinstellung, Auffüllung, Höhe, Breite, Ränder, Position, Z-Index, „Float“, „Clear“, Überlauf)
   * Text (Schriftfamilie, Stärke, Farbe, Größe, Zeilenhöhe und Ausrichtung)
   * Hintergrund (Bild und Verlauf, Hintergrundfarbe)
   * Rahmen (Breite, Stil, Farbe, Radius)
   * Effekte (Schatten, Deckkraft)
   * Erweitert (Ermöglicht das Schreiben benutzerdefinierten CSS für die Komponente)

1. Ebenso können Sie Stile auf andere Teile einer Komponente wie Widget, Beschriftung und Hilfe anwenden.
1. Tippen Sie auf **Fertig**, um die Änderungen zu bestätigen, oder auf **Abbrechen**, um die Änderungen zu verwerfen.

## Beispiel: Inline-Formatvorlagen für eine Feldkomponente {#example-inline-styles-for-a-field-component}

Die folgenden Bilder zeigen ein Textfeld, bevor und nachdem Inline-Stile darauf angewendet wurden.

![Textfeldkomponente vor der Anwendung von Inline-Formatierung](assets/no-style.png)

Textfeldkomponente vor dem Anwenden von Inline-Stil-Eigenschaften

Beachten Sie die Änderung des Textfeldstils, die in der folgenden Abbildung gezeigt wird, nachdem die folgenden CSS-Eigenschaften angewendet wurden.

<table> 
 <tbody> 
  <tr> 
   <td><p>Selektor</p> </td> 
   <td><p>CSS-Eigenschaft</p> </td> 
   <td><p>Wert</p> </td> 
   <td><p>Ergebnis</p> </td> 
  </tr> 
  <tr> 
   <td><p>Feld</p> </td> 
   <td><p>border</p> </td> 
   <td><p>Border width =2px</p> <p>Border style=Solid</p> <p>Rahmenfarbe=#1111</p> </td> 
   <td><p>Erstellt einen schwarzen, 2px breiten Rahmen um das Feld</p> </td> 
  </tr> 
  <tr> 
   <td><p>Textfeld</p> </td> 
   <td><p>background-color</p> </td> 
   <td><p>#6495ED</p> </td> 
   <td><p>Ändert die Hintergrundfarbe zu Kornblumenblau (#6495ED)</p> <p>Hinweis: Sie können einen Farbnamen oder seinen Hexadezimalcode im Wertefeld angeben.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Bezeichnung</p> </td> 
   <td><p>Dimensionen und Position &gt; Breite</p> </td> 
   <td><p>100 px</p> </td> 
   <td><p>Stellt die Breite für die Beschriftung auf 100 px ein</p> </td> 
  </tr> 
  <tr> 
   <td>Feld Hilfe Symbol</td> 
   <td>Text &gt; Schriftfarbe</td> 
   <td>#2ECC40</td> 
   <td>Ändert die Farbe des Gesichts des Hilfesymbols.</td> 
  </tr> 
  <tr> 
   <td><p>Lange Beschreibung</p> </td> 
   <td><p>text-align</p> </td> 
   <td><p>Zentriert</p> </td> 
   <td><p>Richtet die lange Beschreibung der Hilfe zentriert aus</p> </td> 
  </tr> 
 </tbody> 
</table>

![Textfelddesign nach der Anwendung von Inline-Formatierung](assets/applied-style.png)
**Abbildung:** *Textfeldkomponente nach dem Anwenden von Inline-Stileigenschaften*

Mit den oben beschriebenen Schritten können Sie andere Komponenten wie Bedienfelder, Senden-Schaltflächen und Optionsfelder auswählen und formatieren.

>[!NOTE]
>
>Designeigenschaften variieren je nach ausgewählter Komponente.
