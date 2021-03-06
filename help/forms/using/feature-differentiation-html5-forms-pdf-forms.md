---
title: 'Funktionsunterschiede zwischen HTML5- und PDF-Formularen '
seo-title: Feature differentiation between HTML5 forms and PDF forms
description: In den HTML5-Formularen und in PDF-Formularen unterstützte Funktionen
seo-description: Feature supported in HTML5 forms and PDF forms
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
feature: Mobile Forms
exl-id: 2b82e68c-ec11-417d-a8e2-769da9b35140
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 94%

---

# Funktionsunterschiede zwischen HTML5- und PDF-Formularen {#feature-differentiation-between-html-forms-and-pdf-forms}

Die folgende Tabelle zeigt die Funktionsunterstützung für HTML5- und PDF-Formulare:

<table> 
 <tbody>
  <tr>
   <th>Funktion</th> 
   <th>HTML5-Formulare</th> 
   <th>PDF</th> 
  </tr>
  <tr>
   <td>Barcodes<br /> </td> 
   <td>Nicht verfügbar auf Benutzeroberflächenebene. </td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Unterschriftsfeld<br /> </td> 
   <td><strong>Digitale Signaturen</strong> Signaturen werden nicht unterstützt, aber ein neues<strong> Scribble-Signatur</strong>-Feld wurde für papierähnliche Signaturen hinzugefügt. Die Signatur kann im <strong>Scribble-Signatur</strong>-Feld auf dem Formular gesetzt werden. Die Signatur wird auf dem Formular als Bild gespeichert. Sie können den Geotagging-Informationen im <strong>Scribble-Signatur</strong>-Feld speichern.</td> 
   <td>Signaturfeld für<strong> digitale Signaturen</strong> verfügbar.</td> 
  </tr>
  <tr>
   <td>Datenzusammenführung</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Bilder</td> 
   <td>Das Daten-URI-Schema wird für die Darstellung von Bildern verwendet. Alle modernen Browser unterstützen dieses Schema, es gibt jedoch Unterschiede bei den Bildformaten, die die einzelnen Browser unterstützen.<br /> </td> 
   <td>Die Formate .gif, .png, .jpeg, .bmp und .tiff werden unterstützt.</td> 
  </tr>
  <tr>
   <td>Seitenumbruch<br /> </td> 
   <td><p>Ein HTML5-Formular ist in Bereiche und Felder unterteilt, damit es wie ein PDF-Formular wirkt. Die Seitengröße wird dynamisch berechnet. Wenn der gesamte Inhalt einer Seite in einem HTML5-Formular gelöscht oder als ausgeblendet markiert wird, wird die leere Seite ausgeblendet und es wird kein Leerraum zwischen den Seiten angezeigt, die der leeren Seite vorangehen und folgen.</p> <p>Wird einer Seite durch Datenzusammenführung oder Skripte Inhalt hinzugefügt, wird die Seite verlängert, damit der neu hinzukommende Inhalt Platz findet. Dem Formular werden keine neuen Seiten für den neuen Inhalt hinzugefügt. </p> <p><strong>Hinweis:</strong> Wenn der gesamte Inhalt einer Seite in einem HTML5-Formular gelöscht oder als ausgeblendet markiert wird, bleibt die leere Seite zwischen der ersten und zweiten, nicht jedoch zwischen den weiteren Seiten sichtbar.</p> </td> 
   <td>Paginierung in PDF hängt vom zusammengeführten Dateninhalt oder dem Benutzerinhalt ab. Abhängig davon wird die Seitenanzahl erhöht bzw. verringert.</td> 
  </tr>
  <tr>
   <td>Kopf- und Fußzeilen </td> 
   <td>Unterstützt. <br /> <br /> Da HTML5-Mobile Forms Seitenumbrüche nicht unterstützen, werden Kopf- und Fußzeilen nur einmal angezeigt. Sie können jedoch im Layout festlegen, dass sie an mehreren Stellen in der Mobile Forms-Vorschau angezeigt werden.<br /> </td> 
   <td>Unterstützt.</td> 
  </tr>
  <tr>
   <td>Benutzerdefinierte Widgets</td> 
   <td>Widgets können angepasst werden, um die Benutzererfahrung auf mobilen Geräten erweitern.<br /> </td> 
   <td>Alle Widgets werden gesperrt und kein benutzerdefiniertes Widget kann als Plug-In verwendet werden.<br /> </td> 
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

Befolgen Sie die Best Practices, um eine Formularvorlage für HTML5-Ausgabeformate zu aktivieren und sicherzustellen, dass das Verhalten und das Erscheinungsbild von HTML5-Formularen und XFA-basiertem PDF konsistent ist. Eine detaillierte Liste bewährter Verfahren finden Sie unter [Empfohlene Vorgehensweisen für den Entwurf eines HTML5-Formulars](/help/forms/using/best-practices-for-html5-forms.md).
