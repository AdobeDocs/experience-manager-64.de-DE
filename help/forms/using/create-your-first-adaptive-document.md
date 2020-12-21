---
title: ERSTELLEN SIE NICHT DAS erste adaptive Dokument.
seo-title: ERSTELLEN SIE NICHT DAS erste adaptive Dokument.
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 15%

---


# NICHT VERÖFFENTLICHEN Erstellen Sie Ihr erstes adaptives Dokument {#do-not-publish-create-your-first-adaptive-document}

## Nutzungsszenario  {#use-case}

Wir Finance ist ein führendes Unternehmen im Bereich Finanzdienstleistungen, das umfassende und personalisierte Finanzlösungen für die Anforderungen verschiedener Profil Angebot.

Eine der Versicherungspolicen ihrer Kunden läuft ab, und sie senden ihr eine interaktive Erinnerung mit einem PDF-Dokument mit dem Verlängerungsangebot. Die Mitteilung enthält auch weitere Informationen, wie Loyalitätsbelohnungen und Angebote von Rabatten.

Das Portal wird auf AEM ausgeführt. Die Web- und Print-Begrüßungs-Kanal-Ausgabe wird mit den Multi-Kanal-Funktionen von Adaptive Dokument erstellt.

Am Ende des Lernprogramms haben Sie ein adaptives Dokument, das dem Folgenden ähnelt:
[ ![ad-1](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf)    [ ![ad-2](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)Das Erstellen des ersten Tutorials für adaptive Dokumente ist in Schritte kategorisiert. Jeder Schritt ist ein vollständiger Artikel an sich.

<table> 
 <tbody>
  <tr>
   <th>Sie lernen</th> 
   <th>
    <ul> 
     <li>Erstellen eines adaptiven Dokument- und Formulardatenmodells.</li> 
     <li>Erstellen von Vorlagen und Themen für adaptive Dokumente.</li> 
     <li>Verwenden des Regeleditors zum Erstellen von Geschäftsregeln.<br /> </li> 
     <li>Veröffentlichen eines adaptiven Dokuments. <br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>Voraussetzung</td> 
   <td>
    <ul> 
     <li>Einrichten AEM Autoreninstanz. </li> 
     <li>AEM Forms-Add-on installieren. Ausführliche Informationen finden Sie unter <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">AEM Forms</a> installieren und konfigurieren.</li> 
     <li>Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Beispiele in der Übung basieren auf der MySQL-Datenbank und verwenden den Oracle MySQL JDBC-Datenbanktreiber. </li> 
     <li>Einrichten einer Datenbank mit Kundendaten. Eine Datenbank ist unverzichtbar, um ein adaptives Dokument zu erstellen. In diesem Lernprogramm wird eine Datenbank zur Demonstration der Formulardatenmodell- und Persistenzfunktionen von AEM Forms verwendet. </li> 
     <li>Erstellen/importieren und aktivieren Sie <a href="/help/forms/using/web-channel-print-channel.md">Vorlagen für Druck- und Web-Kanal</a>.</li> 
     <li>Vergewissern Sie sich, dass die <a href="/help/forms/using/document-fragments.md">Dokument-Fragmente auf Grundlage des FDM</a> vorhanden sind.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Schritt 1: Erstellen Sie ein Formulardatenmodell {#step-create-form-data-model}

Ein Formulardatenmodell ermöglicht die Verbindung eines adaptiven Dokuments mit unterschiedlichen Datenquellen. Zum Beispiel AEM-Benutzerprofil, RESTful-Webdienste, SOAP-basierte Webdienste, OData-Dienste und relationale Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datenrepräsentationsschema von Geschäftseinheiten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einem adaptiven Dokument verwenden, um Daten aus verbundenen Datenquellen abzurufen. Weitere Informationen zum Formulardatenmodell finden Sie unter [AEM Forms Data Integration](/help/forms/using/data-integration.md).

Ziele:

* Datenbankinstanz (Microsoft Dynamics) als Datenquelle konfigurieren
* Formulardatenmodell mit Microsoft Dynamics als Datenquelle erstellen
* Hinzufügen von Datenmodellobjekten zum Datenmodell
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten

## Schritt 2: Erstellen eines adaptiven Dokuments {#step-create-an-adaptive-document}

Kundenkommunikation zentralisiert und verwaltet die Erstellung, Zusammenstellung und den Versand von sicheren, personalisierten und interaktiven Schriftstücken wie Geschäftskorrespondenz, Briefe, Dokumente, Aussagen, Benefiz, Vermögensverwaltungsprospekt, Marketing-Mails, Rechnungen und Begrüßungs-Kits.

Mithilfe von adaptiven Dokumenten können Sie Kundenkommunikation erstellen, die ansprechend, reaktionsfähig, dynamisch und adaptiv ist. AEM Forms bietet einen Drag &amp; Drop-WYSIWYG-Editor, um adaptive Dokumente zu erstellen.

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

Ziele:

* Erstellen Sie die Druck- und Webausgabe eines adaptiven Dokuments basierend auf dem Formulardatenmodell.
* Layout-Felder eines adaptiven Formulars, um dem Kunden Informationen anzuzeigen
* Erstellen Sie Regeln, um Informationen vom Formulardatenmodell zum adaptiven Dokument abzurufen und anzuzeigen.

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## Schritt 3: Anwenden von Regeln auf Felder mit adaptiven Dokumenten (nur Web-Kanal) {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

Adaptives Dokument bietet einen Editor zum Schreiben von Regeln für adaptive Dokument-Objekte. Diese Regeln definieren Aktionen, die auf Dokument-Objekten basierend auf vorgegebenen Bedingungen und Benutzeraktionen auf dem Dokument ausgelöst werden. Dadurch wird die Genauigkeit und Benutzerfreundlichkeit in der Webversion des adaptiven Dokuments gewährleistet. Weitere Informationen zu Regeln und Regeln-Editoren für adaptive Dokument finden Sie unter [Regeleditor](/help/forms/using/rule-editor.md).

Ziele:

* Erstellen und Anwenden von Regeln auf die Web-Kanal-Felder des adaptiven Dokuments
* Verwenden Sie Regeln, um Dokument-Datenmodelldienste im Web-Kanal auszulösen

## Schritt 4: Formatieren Sie das adaptive Dokument (nur Web-Kanal) {#step-style-the-adaptive-document-web-channel-only}

Adaptive Dokumente bieten einen Editor zum Erstellen von Themen für die adaptive Dokumente- und Inline-Formatierung. Ein Design enthält Stildetails für Komponenten und Bereiche und Sie können ein Design auf Web-Kanälen verschiedener Dokumente wiederverwenden. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie das Design auf Ihr Dokument anwenden, spiegelt der angegebene Stil die entsprechenden Komponenten Ihres Dokuments wider. Weitere Informationen finden Sie unter [Designanpassung](/help/forms/using/themes.md).

Ziele:

* Erstellen eines Designs für den Web-Kanal des adaptiven Dokuments
* Anwenden des Designs auf den Web-Kanal des adaptiven Dokuments
* Erscheinungsbild des adaptiven Dokument-Web-Kanals auf Mobilgeräten und Desktop überprüfen

## Schritt 5: Veröffentlichen des adaptiven Dokuments {#step-publish-the-adaptive-document}

Nachdem Sie das Erstellen des adaptiven Dokuments abgeschlossen haben, müssen Sie es veröffentlichen, damit es in Ihrer Veröffentlichungsinstanz verfügbar ist, in der die Agenten das adaptive Dokument verwenden können, um die darauf basierenden Kommunikationsinstanzen zu erstellen.

Um das adaptive Dokument zu veröffentlichen, müssen die Dokument-Autoren über die erforderlichen Berechtigungen verfügen.
