---
title: Aktionen und Funktionen formularorientierter AEM-Workflows in OSGi- und AEM Forms JEE-Workflows
seo-title: Actions and capabilities of Form-centric AEM Workflows on OSGi and AEM Forms JEE workflows
description: Erfahren Sie mehr über die Unterschiede bei Aktionen, die vom AEM Posteingang und HTML Workspace unterstützt werden, Unterschiede bei den Funktionen, die von formularorientierten AEM Workflows in OSGi- und AEM Forms JEE-Workflows unterstützt werden, sowie Unterschiede zwischen den Funktionen AEM Posteingang und AEM Forms-Apps.
seo-description: Learn more about the differences in actions supported by AEM Inbox and HTML Workspace, differences in capabilities supported by Form-centric AEM Workflows on OSGi and AEM Forms JEE Workflows, and differences between AEM Inbox and AEM Forms app features.
uuid: ce2a05fe-ba45-42ed-880e-fb1d6efc1d26
contentOwner: khsingh
topic-tags: publish
discoiquuid: 4c7ba430-25b2-4ba2-a5eb-4edaed0d599a
exl-id: 6172d936-9348-4f3f-a437-6465dd156f3b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 46%

---

# Aktionen und Funktionen formularorientierter AEM-Workflows in OSGi- und AEM Forms JEE-Workflows  {#actions-and-capabilities-of-form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## AEM Posteingang und HTML Workspace {#aem-inbox-and-html-workspace}

AEM Posteingang wird zum Ausführen und Überwachen von Forms-orientierten AEM-Workflows unter OSGi verwendet. Mit HTML Workspace können Sie AEM Forms JEE-Workflows ausführen und überwachen. In der folgenden Tabelle sind wichtige Aktionen aufgeführt, die im Posteingang für AEM Forms-orientierte AEM-Workflows in OSGi und in HTML Workspace für AEM Forms JEE-Workflows verfügbar sind.

<table> 
 <tbody>
  <tr>
   <td>Aktionen</td> 
   <td>AEM-Posteingang</td> 
   <td>HTML Workspace</td> 
  </tr>
  <tr>
   <td>Starten eines Prozesses, einer Aufgabe oder einer Formularanwendung<br /> </td> 
   <td>Unterstützt<br /> </td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Aufgaben übermitteln</td> 
   <td>Unterstützt<br /> </td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Zuweisen einer Aufgabe zu einer Gruppe</td> 
   <td>Unterstützt<br /> </td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Senden an mehrere Routen</td> 
   <td>Unterstützt<br /> </td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Verfolgen des Aufgabenverlaufs und der Aufgabenzusammenfassung</td> 
   <td>Unterstützt<br /> </td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>E-Mail-Benachrichtigungen</td> 
   <td>Unterstützt<br /> </td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Aufgaben neu zuweisen</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Anlagen auf Feldebene für adaptive Formulare</td> 
   <td>Unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Kalenderansicht</td> 
   <td>Unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Kommentare auf Aufgabenebene</td> 
   <td>Unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Warteschlangen (freigegebene persönliche Warteschlange, Aufgaben aus Warteschlange anfordern)</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Abwesenheitsbenachrichtigung</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Zuweisen einer Aufgabe zu mehreren Benutzern</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
 </tbody>
</table>

## Formularorientierte AEM Workflows in OSGi- und AEM Forms JEE-Workflows {#form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

Formularorientierte AEM Workflows in OSGi- und AEM Forms JEE-Workflows (AEM Forms on JEE Process Management) verfügen über unterschiedliche Funktionen. In der folgenden Tabelle sind wichtige Funktionen und die Unterstützung für die Funktionen formularzentrierter AEM-Workflows in OSGi- und AEM Forms on JEE-Workflows aufgeführt:

<table> 
 <tbody>
  <tr>
   <td>Funktionen</td> 
   <td>Formularorientierte AEM-Workflows in OSGi<br /> </td> 
   <td>AEM Forms JEE-Workflows</td> 
  </tr>
  <tr>
   <td>Adaptive Formulare</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Integration mit anderen AEM</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Freihändige Unterschrift</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Benutzerdefinierte E-Mail-Vorlagen</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Festlegen der Aufgabenpriorität</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Zeitüberschreitung für Aufgaben nach Fälligkeitsdatum</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Schleifen im Workflow</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Verantwortlichen dynamisch wählen </td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Verwenden benutzerdefinierter Metadaten</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>E-Signatur (Acrobat Sign)</td> 
   <td>Unterstützt <sup>[1]</sup></td> 
   <td>Unterstützt <sup>[5]</sup></td> 
  </tr>
  <tr>
   <td>Verwalten von Aufgaben und Formularanwendungen</td> 
   <td>Unterstützt <sup>[2]</sup><br /> </td> 
   <td>Unterstützt <sup>[2]</sup></td> 
  </tr>
  <tr>
   <td>Document Services</td> 
   <td>Unterstützt <sup>[3]</sup></td> 
   <td>Unterstützt <sup>[3]</sup></td> 
  </tr>
  <tr>
   <td>Rendern abgeschlossener Aufgaben als adaptives Formular oder PDF-Dokument</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt  [4]</td> 
  </tr>
  <tr>
   <td>Integration mit Correspondence Management</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Schaltfläche „Zurücksetzen“</td> 
   <td>Unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Workflow-Phasen</td> 
   <td>Unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Schreibgeschützte adaptive Formulare</td> 
   <td>Unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Ausblenden der Standardspeicherschaltfläche</td> 
   <td>Unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Detaillierte Kontrolle über den Abschnitt mit Workflow-Details</td> 
   <td>Unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>HTML5-Formulare, interaktive PDF-Formulare, Formularsatz<br /> </td> 
   <td>Nicht unterstützt<br /> </td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Prozessberichterstellung</td> 
   <td>Nicht unterstützt<br /> </td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Digitale Signatur</td> 
   <td>Unterstützt<br /> </td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Startpoint-Kategorien</td> 
   <td>Nicht unterstützt </td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Genehmigung mehrerer Aufgaben </td> 
   <td>Nicht unterstützt </td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Speichern eines Entwurfs unter benutzerdefiniertem Namen</td> 
   <td>Nicht unterstützt </td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Starten eines Prozesses mit vorhandenen Prozessdaten<br /> </td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Speichern eines Startpunkts als Entwurf</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Benutzeravatar</td> 
   <td>Unterstützt</td> 
   <td>Unterstützt </td> 
  </tr>
  <tr>
   <td>Manageransicht</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Vorlagen suchen</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt<br /> </td> 
  </tr>
  <tr>
   <td>Integration mit Anwendungen von Drittanbietern</td> 
   <td>Unterstützt <sup>[6]</sup></td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Anlagen auf Aufgabenebene für Workflow-Anwendung oder Startpunkt</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Erinnerungsemail</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Titel des Zeitlimits einer Aufgabe ändern</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>E-Mail für Aufgabenzuweisung und Aufgabenanfrage</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Senden einer E-Mail am Ende des Workflows</td> 
   <td>Unterstützt <sup>[7]</sup></td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Delegieren zwischen getrennten Gruppen</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Webdienst über einen Workflow aufrufen</td> 
   <td>Unterstützt <sup>[6]</sup></td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>XSLT Transform</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Gateways, NO WAIT</td> 
   <td>Unterstützt </td> 
   <td>Unterstützt  </td> 
  </tr>
  <tr>
   <td>ODER-Teilung und UND-Teilung</td> 
   <td>Nicht unterstützt</td> 
   <td>Unterstützt</td> 
  </tr>
  <tr>
   <td>Dynamische Aufgabenpriorität</td> 
   <td>Nicht unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
 </tbody>
</table>

1. Sie können formularorientierte AEM Workflows in OSGi verwenden, um ein bereits ausgefülltes adaptives Formular zu signieren. Formularorientierte AEM-Workflows in OSGi unterstützen das externe Signieren von Formularen. [Formularinternes Signieren](/help/forms/using/working-with-adobe-sign.md#create-in-form-signing-experience) wird nicht unterstützt.

1. Sie benötigen Zugriff auf AEM Posteingang, um AEM Forms OSGi AEM Workflows und HTML Workspace ausführen und überwachen zu können, um AEM Forms JEE-Workflows ausführen und überwachen zu können.
1. Programmeigene AEM Forms Document Services sind sowohl für formularorientierte AEM-Workflows in OSGi als auch für AEM Forms in JEE-Workflows verfügbar. AEM Workflow nutzt native Dokumenten-Services für formularzentrierte AEM-Workflows unter OSGi und für Workflows von AEM Forms auf JEE (Prozessverwaltung).
1. AEM Forms JEE-Workflows können nur ein adaptives Formular wiedergeben. Das Rendern eines adaptiven Formulars als PDF-Dokument wird nicht unterstützt.
1. AEM Forms JEE-Workflows verfügen nicht über einen separaten Schritt für Acrobat Sign. Sie benötigen ein für Acrobat Sign aktiviertes adaptives Formular für AEM Forms JEE-Workflows. Weitere Informationen finden Sie unter [Acrobat Sign-Dokumentation](/help/forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component).
1. Mit dem Schritt [Formulardatenmodell-Service aufrufen](/help/forms/using/aem-forms-workflow-step-reference.md#p-invoke-form-data-model-service-step-p) können Sie einen Webservice aufrufen und Daten aus einem Drittanbieterprogramm senden oder abrufen.
1. Sie können den Schritt [E-Mail senden](/help/forms/using/aem-forms-workflow-step-reference.md#send-email-step) verwenden, um E-Mails zu senden.

## Unterschiede zwischen den Funktionen von AEM Inbox und AEM Forms-App {#differences-between-aem-inbox-and-aem-forms-app-features}

Zwei der bekanntesten Möglichkeiten zum Starten eines formularbasierten Workflows sind der [AEM-Posteingang](/help/forms/using/manage-applications-inbox.md) und die Mobile App von AEM Forms. Die Funktionen von AEM Inbox und AEM Forms-App sind jedoch unterschiedlich. Der AEM-Posteingang funktioniert nur mit [formularzentrierten Workflows](/help/forms/using/aem-forms-workflow.md), während die Mobile App von AEM Forms sowohl mit formularzentrierten Workflows als auch mit der Prozessverwaltung funktioniert.

Die folgende Tabelle zeigt die Funktionen von AEM Inbox und der AEM Forms App:

<table> 
 <tbody>
  <tr>
   <td><p><strong>Aktionen</strong></p> </td> 
   <td><p><strong>AEM-Posteingang</strong></p> </td> 
   <td><p><strong>AEM Forms-App</strong></p> </td> 
  </tr>
  <tr>
   <td><p>Formularanwendung starten</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Unterstützt </p> </td> 
  </tr>
  <tr>
   <td><p>Aufgaben übermitteln</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Unterstützt </p> </td> 
  </tr>
  <tr>
   <td><p>Aufgaben delegieren</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr>
  <tr>
   <td><p>Verfolgen des Aufgabenverlaufs und der Aufgabenzusammenfassung</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr>
  <tr>
   <td><p>Anlagen auf Aufgabenebene hinzufügen</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Unterstützt </p> </td> 
  </tr>
  <tr>
   <td><p>Anlagen auf Aufgabenebene anzeigen</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Unterstützt </p> </td> 
  </tr>
  <tr>
   <td><p>Anlagen auf Feldebene hinzufügen</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Unterstützt </p> </td> 
  </tr>
  <tr>
   <td><p>Kalenderansicht anzeigen</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr>
  <tr>
   <td><p>Kommentare hinzufügen</p> </td> 
   <td><p>Unterstützt</p> </td> 
   <td><p>Unterstützt </p> </td> 
  </tr>
 </tbody>
</table>
