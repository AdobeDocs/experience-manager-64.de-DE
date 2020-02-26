---
title: ERSTELLEN SIE NICHT DAS erste adaptive Dokument
seo-title: ERSTELLEN SIE NICHT DAS erste adaptive Dokument
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# ERSTELLEN SIE NICHT DAS erste adaptive Dokument {#do-not-publish-create-your-first-adaptive-document}

## Nutzungsszenario {#use-case}

Wir Finance ist ein führendes Unternehmen im Bereich Finanzdienstleistungen, das umfassende und personalisierte Finanzlösungen anbietet, die den Anforderungen verschiedener Kundenprofile entsprechen.

Eine der Versicherungspolicen ihrer Kunden läuft ab, und sie senden ihr eine interaktive Erinnerung mit einem PDF-Dokument mit dem Verlängerungsangebot. Die Mitteilung enthält auch weitere Informationen, wie Loyalitätsbelohnungen und Preisnachlässe.

Das Portal wird auf Adobe AEM ausgeführt. Die Web- und Print-Willkommens-Kanalausgabe wird mithilfe der Mehrkanal-Funktionen des adaptiven Dokuments erstellt.

Am Ende des Lernprogramms haben Sie ein adaptives Dokument, das dem Folgenden ähnelt:
[ ad-1![ ](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf) ad-2[![](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)Das erste Tutorial für adaptive Dokumente wird in Schritte kategorisiert. Jeder Schritt ist ein vollständiger Artikel an sich.

<table> 
 <tbody>
  <tr>
   <th>Sie lernen</th> 
   <th>
    <ul> 
     <li>Erstellen eines adaptiven Dokuments und eines Formulardatenmodells.</li> 
     <li>Erstellen von Vorlagen und Designs für adaptive Dokumente.</li> 
     <li>Erstellen von Geschäftsregeln mit dem Regeleditor.<br /> </li> 
     <li>Publishing an adaptive document. <br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>Voraussetzung</td> 
   <td>
    <ul> 
     <li>Einrichten der AEM-Autoreninstanz </li> 
     <li>AEM Forms-Add-on installieren. Ausführliche Informationen finden Sie unter <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">Installieren und Konfigurieren von AEM Forms</a>.</li> 
     <li>Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Beispiele in der Übung basieren auf der MySQL-Datenbank und verwenden den Oracle MySQL JDBC-Datenbanktreiber. </li> 
     <li>Einrichten einer Datenbank mit Kundendaten. Eine Datenbank ist unverzichtbar, um ein adaptives Dokument zu erstellen. In diesem Lernprogramm wird eine Datenbank zur Demonstration der Formulardatenmodell- und Persistenzfunktionen von AEM Forms verwendet. </li> 
     <li>Erstellen/importieren und aktivieren Sie <a href="/help/forms/using/web-channel-print-channel.md">Vorlagen für Druck- und Webkanäle</a>.</li> 
     <li>Stellen Sie sicher, dass die <a href="/help/forms/using/document-fragments.md">Dokumentfragmente auf der Grundlage des FDM</a>vorhanden sind.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Schritt 1: Erstellen Sie ein Formulardatenmodell {#step-create-form-data-model}

Ein Formulardatenmodell ermöglicht die Verbindung eines adaptiven Dokuments mit unterschiedlichen Datenquellen. Zum Beispiel AEM-Benutzerprofil, RESTful-Webdienste, SOAP-basierte Webdienste, OData-Dienste und relationale Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datenrepräsentationsschema von Geschäftseinheiten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einem adaptiven Dokument verwenden, um Daten aus verbundenen Datenquellen abzurufen. For more information about form data model, see [AEM Forms Data Integration](/help/forms/using/data-integration.md).

Ziele:

* Datenbankinstanz (Microsoft Dynamics) als Datenquelle konfigurieren
* Formulardatenmodell mit Microsoft Dynamics als Datenquelle erstellen
* Hinzufügen von Datenmodellobjekten zum Datenmodell
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten

## Step 2: Create an adaptive document {#step-create-an-adaptive-document}

Customer Communications zentralisiert und verwaltet die Erstellung, Zusammenstellung und Bereitstellung sicherer, personalisierter und interaktiver Korrespondenz wie Geschäftskorrespondenz, Briefe, Dokumente, Aussagen, Vorteilsnotices, Vermögensverwaltungsprospekt, Marketing-Mails, Rechnungen und Begrüßungs-Kits.

Mithilfe adaptiver Dokumente können Sie Kundenmitteilungen erstellen, die ansprechend, reaktionsschnell, dynamisch und adaptiv sind. AEM Forms bietet einen Drag &amp; Drop-WYSIWYG-Editor zum Erstellen adaptiver Dokumente.

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

Ziele:

* Erstellen Sie die Druck- und Webausgabe eines adaptiven Dokuments basierend auf dem Formulardatenmodell.
* Layout-Felder eines adaptiven Formulars, um dem Kunden Informationen anzuzeigen
* Erstellen Sie Regeln, um Informationen vom Formulardatenmodell zum adaptiven Dokument abzurufen und anzuzeigen.

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## Schritt 3: Regeln auf Felder für adaptive Dokumente anwenden (nur Webkanal) {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

Das adaptive Dokument bietet einen Editor zum Schreiben von Regeln für adaptive Dokumentobjekte. Diese Regeln definieren Aktionen, die auf Dokumentobjekten basierend auf vorgegebenen Bedingungen und Benutzeraktionen im Dokument ausgelöst werden. Dadurch wird die Genauigkeit und Benutzerfreundlichkeit in der Webversion des adaptiven Dokuments gewährleistet. Weitere Informationen zu Regeln und Regeln-Editoren für adaptive Dokumente finden Sie unter [Regeleditor](/help/forms/using/rule-editor.md).

Ziele:

* Erstellen und Anwenden von Regeln auf die Webkanalfelder adaptiver Dokumente
* Verwenden Sie Regeln, um Dokumentdatenmodelldienste im Webkanal auszulösen

## Schritt 4: Formatieren des adaptiven Dokuments (nur Webkanal) {#step-style-the-adaptive-document-web-channel-only}

Adaptive Dokumente bieten einen Editor zum Erstellen von Designs für adaptive Dokumente und Inline-Stile. Ein Design enthält Stildetails für Komponenten und Bereiche und Sie können ein Design auf Webkanälen verschiedener Dokumente wiederverwenden. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie das Design auf Ihr Dokument anwenden, spiegelt der angegebene Stil die entsprechenden Komponenten des Dokuments wider. Weitere Informationen finden Sie unter [Designanpassung](/help/forms/using/themes.md).

Ziele:

* Design für den Webkanal des adaptiven Dokuments erstellen
* Anwenden des Designs auf den Webkanal des adaptiven Dokuments
* Erscheinungsbild des Webkanals des adaptiven Dokuments auf Mobilgeräten und Desktop überprüfen

## Schritt 5: Veröffentlichen des adaptiven Dokuments {#step-publish-the-adaptive-document}

Nachdem Sie das Erstellen des adaptiven Dokuments abgeschlossen haben, müssen Sie es veröffentlichen, damit es in Ihrer Veröffentlichungsinstanz verfügbar ist, in der die Agenten das adaptive Dokument verwenden können, um die darauf basierenden Kommunikationsinstanzen zu erstellen.

Zum Veröffentlichen des adaptiven Dokuments müssen die Dokumentautoren über die erforderlichen Berechtigungen verfügen.
