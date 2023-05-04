---
title: Anpassen von Fehlermeldungen für HTML5-Formulare
seo-title: Customizing error messages for HTML5 forms
description: Erfahren Sie, wie Sie die Anzeige von Fehlermeldungen für HTML5-Formulare anpassen können, einschließlich der Änderung ihrer Position und ihres Erscheinungsbilds.
seo-description: Learn how to customize the display of error messages for HTML5 forms including how to change their position and appearance.
uuid: 6f48b64e-858f-4323-ad50-88e25f3c2e3d
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 44e49789-9075-41b3-bce8-03e8efce2d5a
feature: Mobile Forms
exl-id: e8a53976-e9bd-459d-92f5-88527c72428b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 60%

---

# Anpassen von Fehlermeldungen für HTML5-Formulare {#customizing-error-messages-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In den HTML5-Formularen haben die Fehlermeldungen und Warnungen standardmäßig eine feste Position und ein festgelegtes Erscheinungsbild (Schriftart und Farbe). Der Fehler wird nur für ein ausgewähltes Feld angezeigt und es wird nur ein Fehler angezeigt.

Der Artikel stellt die Schritte bereit, um HTML5-Fehlermeldung anzupassen um,

* dass das Erscheinungsbild und die Position der Fehlermeldungen geändert werden. Die Fehlermeldung können oberhalb, unterhalb oder an der rechten Seite eines Felds angezeigt werden.
* Anzeigen von Fehlermeldungen für mehrere Felder jederzeit.
* Anzeigen der Fehlermeldung unabhängig davon, ob ein Feld ausgewählt ist oder nicht.

## Anpassen von Fehlermeldungen  {#customizing-error-messages-nbsp}

Laden Sie vor dem Anpassen der Fehlermeldungen das angehängte Paket herunter und extrahieren Sie es (CustomErrorManager-1.0-SNAPSHOT.zip).

Öffnen Sie nach dem Extrahieren des Pakets den Ordner CustomErrorManager-1.0-SNAPSHOT . Sie enthält die Ordner jcr_root und META-INF. Diese Ordner enthalten die CSS- und JS-Dateien, die zum Anpassen der Fehlermeldung erforderlich sind.

[Datei laden](assets/customerrormanager-1.0-snapshot.zip)

### Anpassen der Position der Fehlermeldungen  {#customizing-the-position-of-error-messages-nbsp}

Um die Position der Fehlermeldung anzupassen, fügen Sie &lt;div> Tag für jedes Fehler- und Warnfeld, positionieren Sie die &lt;div> -Tag auf der linken oder rechten Seite platzieren und CSS-Stile auf die &lt;div> -Tag. Ausführliche Anweisungen finden Sie im unten aufgeführten Verfahren:

1. Navigieren Sie zum Ordner `CustomErrorManager-1.0-SNAPSHOT` und öffnen Sie den Ordner `etc\clientlibs\mf-custom-error-manager\CustomErrorManager\javascript`.
1. Öffnen Sie die Datei `customErrorManager.js` zum Bearbeiten. Die `markError`-Funktion in der Datei akzeptiert folgende Parameter:

   |  |  |
   |---|---|
   | jqWidget | jqWidget ist das Handle für Widget. |
   | msg | enthält die Fehlermeldung |
   | Typ | gibt an, ob es sich um einen Fehler oder eine Warnung handelt |

1. Bei der vordefinierten Implementierung werden rechts im Feld Fehlermeldungen angezeigt. Verwenden Sie folgenden Code, um Fehlermeldungen oben anzuzeigen.

   ```
   markError: function (jqWidget, msg, type) {
               var element = jqWidget.element,                                //Gives the div containing widget
                   pos = $(element).offset(),                          //Calculates the position of the div in the view port
                                                                   msgHeight = xfalib.view.util.TextMetrics.measureExtent(msg).height + 5;  //Calculating the height of the Error Message
                   styles = {};
                   styles.left = pos.left + "px";         // Assign the desired left position using pos.left. Here it is calculated for exact left of the field 
                   styles.top = pos.top - msgHeight + "px";  // Assign the desired top position using pos.top. Here it is calculated for top of the field 
               if (type != "warning") {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the warning div if it is not present already
                       jqWidget.errorDiv=$("<div id='customError'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the warning div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               } else {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the error div if it is not present already
                       jqWidget.errorDiv=$("<div id='customWarning'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the error div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               }
   
           },
   ```

1. Speichern und schließen Sie die Datei.
1. Navigieren Sie zum Ordner `CustomErrorManager-1.0-SNAPSHOT` und erstellen Sie ein Archiv der Ordner jcr_root und META-INF. Benennen Sie das Archiv in CustomErrorManager-1.0-SNAPSHOT.zip um.
1. Verwenden Sie den Package Manager, um das Paket herunterzuladen und zu installieren.

## Anzeigen von Fehlermeldungen für mehrere Felder  {#display-error-messages-for-multiple-fields-nbsp}

Verwenden Sie das angehängte Paket, um Fehlermeldungen für alle Felder gleichzeitig anzuzeigen. Verwenden Sie zum Anzeigen einer einzelnen Fehlermeldung das Standardprofil.

### Anpassen der Darstellung von Fehlermeldungen  {#customizing-the-appearance-of-error-messages-nbsp}

1. Navigieren Sie zum Ordner etc\clientlibs\mf-custom-error-manager\CustomErrorManager\css.

1. Öffnen Sie die Datei sample.css zur Bearbeitung. Die CSS-Datei enthält 2 IDs: #customError, #customWarning. Sie können diese IDs verwenden, um verschiedene Eigenschaften wie Farbe, Schriftgröße usw. zu ändern.

    Verwenden Sie den folgenden Code, um Schriftgröße und Farbe der Fehler-/Warnmeldungen zu ändern.

   ```
   #customError {
   color: #0000FF; // it changes the color of Error Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 24px;  // it changes the font size of Error Message
   z-index:5;
   }
   
   #customWarning {
   color: #00FF00;  // it changes the color of Warning Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 18px;   // it changes the font size of Warning Message
   z-index:5;
   }
   
   Save the changes.
   ```

1. Speichern und schließen Sie die Datei.
1. Navigieren Sie zum Ordner CustomErrorManager-1.0-SNAPSHOT und erstellen Sie ein Archiv der Ordner jcr_root und META-INF. Benennen Sie das Archiv in CustomErrorManager-1.0-SNAPSHOT.zip um.
1. Verwenden Sie den Package Manager, um das Paket herunterzuladen und zu installieren.

## Rendern Sie das Formular mit dem neuen Profil.  {#render-the-form-with-the-new-profile-nbsp}

Standardmäßig verwenden HTML5-Formulare ein Standardprofil: https://&lt;server>/content/xfaforms/profiles/default.html?contentRoot=&lt;xdp location>&amp;template=&lt;name of the xdp>

Rendern Sie zum Anzeigen eines Formulars mit den angepassten Fehlermeldungen das Formular mit dem Fehlerprofil: http://&lt;server>/content/xfaforms/profiles/error.html?contentRoot=&lt;xdp location>&amp;template=&lt;name of the xdp>

>[!NOTE]
>
>Mit dem angehängten Paket wird das Fehlerprofil installiert.
