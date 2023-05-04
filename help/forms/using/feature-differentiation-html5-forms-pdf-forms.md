---
title: Funktionsunterschiede zwischen HTML5- und PDF-Formularen
seo-title: Feature differentiation between HTML5 forms and PDF forms
description: In HTML5-Formularen und PDF forms unterstützte Funktionen
seo-description: Feature supported in HTML5 forms and PDF forms
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
feature: Mobile Forms
exl-id: 2b82e68c-ec11-417d-a8e2-769da9b35140
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 36%

---

# Funktionsunterschiede zwischen HTML5- und PDF-Formularen {#feature-differentiation-between-html-forms-and-pdf-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die folgende Tabelle zeigt die Funktionsunterstützung für HTML5-Formulare und PDF forms:

<table> 
 <tbody>
  <tr>
   <th>Funktion</th> 
   <th>HTML5-Formulare</th> 
   <th>PDF</th> 
  </tr>
  <tr>
   <td>Barcodes<br /> </td> 
   <td>Nicht auf Benutzeroberflächenebene verfügbar. </td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Signaturfeld<br /> </td> 
   <td><strong>Digitale Signaturen</strong> werden nicht unterstützt, aber ein neuer <strong>Scribble-Signatur</strong> für papierähnliche Signaturen hinzugefügt. Sie können ihre Signatur mithilfe des <strong>Scribble-Signatur</strong> -Feld. Die Signatur wird im Formular als Bild gespeichert. Sie können Geolocation-Informationen im Abschnitt <strong>Scribble-Signatur</strong> -Feld.</td> 
   <td>Signaturfeld verfügbar für <strong>Digitale Signaturen</strong>.</td> 
  </tr>
  <tr>
   <td>Datenzusammenführung</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Bilder</td> 
   <td>Das Daten-URI-Schema wird zum Anzeigen von Bildern verwendet. Alle modernen Versionen von Browsern unterstützen dieses Schema, es gibt jedoch Unterschiede in der Bandbreite der Bildformate, die von jedem Browser unterstützt werden.<br /> </td> 
   <td>Die Formate .gif, .png, .jpeg, .bmp und .tiff werden unterstützt.</td> 
  </tr>
  <tr>
   <td>Seitenumbruch<br /> </td> 
   <td><p>Ein HTML5-Formular ist in Bereiche und Felder unterteilt, um ihm ein ähnliches Aussehen wie PDF forms zu verleihen. Die Seitengröße wird dynamisch berechnet. Wenn der gesamte Seiteninhalt in einem HTML5-Formular gelöscht oder als ausgeblendet markiert wird, wird die leere Seite ausgeblendet und zwischen den5-Seiten wird kein leerer Leerraum (Leerraum) angezeigt.</p> <p>Wenn Datenzusammenführung oder Skripte Inhalte zu einer Seite hinzufügen, wird die Länge der Seite erweitert, um den neu hinzugefügten Inhalt aufzunehmen. Dem Formular werden keine neuen Seiten hinzugefügt, um den neu hinzugefügten Inhalt aufzunehmen. </p> <p><strong>Hinweis:</strong> Wenn der gesamte Inhalt einer Seite in einem HTML5-Formular gelöscht oder als ausgeblendet markiert wird, bleibt die leere Seite zwischen der ersten und zweiten, nicht jedoch zwischen den weiteren Seiten sichtbar.</p> </td> 
   <td>Paginierung in PDF hängt vom zusammengeführten Dateninhalt oder dem Benutzerinhalt ab. Abhängig davon wird die Seitenanzahl erhöht bzw. verringert.</td> 
  </tr>
  <tr>
   <td>Kopf- und Fußzeilen </td> 
   <td>Unterstützt. <br /> <br /> Da HTML5-Mobile Forms Seitenumbrüche nicht unterstützen, werden Kopf- und Fußzeilen nur einmal angezeigt. Sie können sie jedoch im Layout so einrichten, dass sie an mehreren Stellen in der Mobile Forms-Vorschau angezeigt werden.<br /> </td> 
   <td>Unterstützt.</td> 
  </tr>
  <tr>
   <td>Benutzerdefinierte Widgets</td> 
   <td>Widgets können angepasst werden, um das Benutzererlebnis auf Mobilgeräten zu verbessern.<br /> </td> 
   <td>Alle Widgets sind gesperrt und kein benutzerdefiniertes Widget kann als Plug-in verwendet werden.<br /> </td> 
  </tr>
  <tr>
   <td>XFA-Skript-API</td> 
   <td>Unterstützt die am häufigsten verwendeten XFA-Skriptkonstrukte. Eine detaillierte Liste der unterstützten Konstrukte finden Sie unter <a href="/help/forms/using/scripting-support.md">Unterstützung der Skripterstellung</a>.</td> 
   <td>Unterstützt alle XFA-Skriptkonstrukte.</td> 
  </tr>
  <tr>
   <td>Acrobat-Skript-APIs </td> 
   <td>HTML5-Formulare unterstützen die am häufigsten verwendeten APIs. Weitere Informationen finden Sie unter <a href="/help/forms/using/scripting-support.md">Unterstützung für Skripterstellung</a>.</td> 
   <td>Wenn die PDF-Datei in Acrobat oder Reader geöffnet ist, unterstützt sie auch alle Skript-APIs, die Acrobat bereitstellt.</td> 
  </tr>
  <tr>
   <td>Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung </td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
 </tbody>
</table>

Befolgen Sie die Best Practices, um eine Formularvorlage für HTML5-Ausgabeformate zu aktivieren und sicherzustellen, dass das Verhalten und das Erscheinungsbild von HTML5-Formularen und XFA-basiertem PDF konsistent ist. Eine detaillierte Liste der Best Practices finden Sie unter [Best Practices zum Entwerfen eines HTML5-Formulars.](/help/forms/using/best-practices-for-html5-forms.md)
