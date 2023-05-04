---
title: Übersicht über die neuen Funktionen | AEM 6.4 Forms
seo-title: New features summary | AEM 6.4 Forms
description: Zusammenfassung der neuen Funktionen und Verbesserungen in AEM 6.4 Forms.
seo-description: Summary of new features and enhancements in AEM 6.4 Forms.
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
exl-id: 21b8ed83-9c0c-41ee-9fbb-56ccebaee132
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2038'
ht-degree: 8%

---

# Übersicht über die neuen Funktionen | AEM 6.4 Forms {#new-features-summary-aem-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Zusammenfassung der neuen Funktionen und Verbesserungen in AEM 6.4 Forms.

AEM Forms umfasst verschiedene neue Funktionen und Verbesserungen, die die Erstellung, Verwaltung und Benutzererfahrung adaptiver Formulare und interaktiver Kommunikation weiter optimieren.

Lesen Sie für eine schnelle Einführung in neue Funktionen und Verbesserungen weiter. In der Dokumentation finden Sie Ressourcen mit Details. Siehe auch AEM 6.4 Forms [Versionshinweise](/help/release-notes/forms.md). Die vollständige AEM 6.4 Forms-Dokumentation finden Sie unter [Handbuch zu AEM 6.4 Forms](/help/forms/home.md).

## Interaktive Kommunikation {#interactive-communications}

![Correspondence Management](assets/correspondence-management.png)

Interaktive Kommunikation zentralisiert und verwaltet die Erstellung, Zusammenstellung und Bereitstellung sicherer, personalisierter und interaktiver Schriftstücke, wie z. B. Geschäftskorrespondenz, Briefe, Dokumente, Aussagen, Sozialleistungen, Vermögensverwaltungsprospekte, Marketing-Mails, Rechnungen und Willkommenskits.

Interaktive Kommunikation nutzt dieselbe zugrunde liegende Technologie, Prozesse und Komponenten wie adaptive Formulare, um interaktive mehrkanalige Kommunikation zu erstellen, ähnlich wie interaktive adaptive Formulare.

Interaktive Kommunikation bietet erhebliche Vorteile:

* Bietet OOTB-Integration mit dem Formulardatenmodell, um einfachen und optimierten Zugriff auf Back-End-Datenbanken und andere CRM-Systeme wie MS Dynamics zu ermöglichen
* Bietet eine integrierte Authoring-Oberfläche für Druck- und Webkanäle
* Bietet eine Drag &amp; Drop-basierte Authoring-Oberfläche, die dem adaptiven Forms-Authoring ähnelt und sowohl für Druck- als auch Webkanäle verwendet wird.

Interaktive Kommunikation ist der standardmäßige und empfohlene Ansatz zur Erstellung von Kundenkommunikation. Um die Briefe in AEM 6.3 Forms und AEM 6.2 Forms weiterhin verwenden zu können, müssen Sie ein Kompatibilitätspaket installieren.

### Erstellung interaktiver Kommunikation mit mehreren Kanälen {#multi-channel-interactive-communication-authoring}

Mithilfe der interaktiven Kommunikation können Sie Druck- und Webdokumente in einem einzigen Dokumenteditor erstellen und bearbeiten. Durch Verwendung derselben Dokumentfragmente zur Erstellung von Ausgabedarstellungen beider Kanäle können Sie doppelte Arbeit vermeiden.
![printweb_2](assets/printweb_2.png)

Weitere Informationen finden Sie unter [Interaktive Kommunikation - Überblick](/help/forms/using/interactive-communications-overview.md).

### WYSIWYG Document Editor {#wysiwyg-document-editor}

Der Drag &amp; Drop-Dokumenteditor von WYSIWYG ist geschäftsfreundlich. Die intuitive Benutzeroberfläche, Drag &amp; Drop-Funktionen, Standardkomponenten, Datenmodelle und das integrierte Repository für Assets erleichtern das schnelle und einfache Authoring interaktiver Kommunikation.

Um eine interaktive Kommunikation zu erstellen oder eine vorhandene zu bearbeiten, können Geschäftsbenutzer die folgenden Bausteine verwenden: Kanäle, Inhalt, Eigenschaften, Assets, Komponenten und Datenquellen.

![Drag-n-Drop-lf](assets/drag-n-drop-lf.png)

Weitere Informationen finden Sie unter [Einführung in die Bearbeitung der interaktiven Kommunikation](/help/forms/using/introduction-interactive-communication-authoring.md).

### Automatische Generierung einer Webversion aus Druckinhalten in interaktiver Kommunikation {#auto-generate-web-version-from-print-content-in-interactive-communication}

Autoren können Webdokumentinhalte automatisch aus Druckdokumenten generieren, um sowohl Druck- als auch Webdokumente im selben Editor zu erstellen, in der Vorschau anzuzeigen und zu bearbeiten. Autoren der interaktiven Kommunikation können nur einmal erstellen und in allen Kanälen veröffentlichen. Autoren der interaktiven Kommunikation können dieselben Dokumentfragmente im Druck- und Webkanal verwenden, um doppelten Aufwand zu vermeiden.

Weitere Informationen finden Sie unter [Druckkanal und Webkanal](/help/forms/using/web-channel-print-channel.md).

### Verwenden Sie Designs, um den Webkanal der interaktiven Kommunikation zu gestalten {#use-themes-to-style-web-channel-of-interactive-communication}

Interaktive Kommunikation unterstützt Designs. Sie können Designs erstellen und sie auf Ihre interaktive Kommunikation anwenden. Ein Design enthält Stildetails für Komponenten und Bereiche. Sie können ein Design für verschiedene interaktive Kommunikation wiederverwenden, um ihnen ein einheitliches und konsistentes Erscheinungsbild und Branding zu verleihen.

AEM Forms enthält ein vordefiniertes Design für interaktive Kommunikation. Mithilfe eines Designs können Sie auch anpassen, wie eine interaktive Kommunikation auf einem Gerät aussieht.

Weitere Informationen finden Sie unter [Designs in AEM Forms](/help/forms/using/themes.md).

### Erweiterte Benutzeroberfläche für Agenten {#enhanced-agent-interface}

Die Benutzeroberfläche für Agenten unterstützt jetzt die Druck- und Webvorschau der interaktiven Kommunikation. Über dieselbe Benutzeroberfläche für Agenten können Sie den Druckkanal bearbeiten und den Webkanal Ihrer interaktiven mehrkanaligen Kommunikation in der Vorschau anzeigen. Felder, Variablen, FDM-Elemente und Dokumentfragmente im Druckkanal können so konfiguriert werden, dass sie vom Agenten in der Benutzeroberfläche für Agenten geändert werden. Mit der Unterstützung des Formulardatenmodells können Sie eine Vorschau mit vorausgefüllten Musterdaten generieren.

Weitere Informationen finden Sie unter [Vorbereiten und Senden der interaktiven Kommunikation über die Benutzeroberfläche für Agenten](/help/forms/using/prepare-send-interactive-communication.md).

### Präsentieren von Informationen in Diagrammen {#present-information-in-charts}

Interaktive Kommunikation unterstützt Diagramme im Web und im Druckkanal für eine bessere Kommunikation. Mithilfe von Diagrammen wie Torten, Donut, Balken und Spalten können Sie große Mengen von Informationen zusammenfassen und visuell darstellen, um eine einfache Interpretation und Analyse zu ermöglichen.

![chart-2](assets/chart-2.png) ![Diagramm](assets/chart.png)

Weitere Informationen finden Sie unter [Verwenden von Diagrammen mit interaktiver Kommunikation](/help/forms/using/chart-component-interactive-communications.md).

### Vordefinierte Data Connectors zum Vorbefüllen von Dokumenten {#out-of-the-box-data-connectors-to-prefill-documents}

Interaktive Kommunikation bietet Datenintegration mit Business Tools, um eine Verbindung mit mehreren Unternehmenssystemen herzustellen, einschließlich CRM-Systemen, und Daten in Dokumente zu personalisieren.

![fdm_ad](assets/fdm_ad.png)

Weitere Informationen finden Sie unter [Verwenden eines Formulardatenmodells](/help/forms/using/using-form-data-model.md).

### Verbesserter Dokumentfragmenteditor {#enhanced-document-fragment-editor}

Sie können jetzt FDM-Elemente und Regeln in Dokumentfragmenten der interaktiven Kommunikation verwenden.

* Unterstützung für Formulardatenmodellelemente
* Ein- oder Ausblenden von Assets/Textfragmenten mithilfe von Regeln
* Wert eines Elements/einer Variablen überprüfen
* Funktionen ausführen, um den Wert eines mathematischen Ausdrucks zu berechnen

Weitere Informationen finden Sie unter:

* [Texte in interaktiver Kommunikation](/help/forms/using/texts-interactive-communications.md)
* [Bedingungen in interaktiven Kommunikationen](/help/forms/using/conditions-interactive-communications.md)

### Kompatibilitätspaket für vorhandene Assets {#compatibility-package-for-existing-assets}

Standardmäßig werden Brief-Assets aus früheren Versionen von AEM Forms in dieser Version nicht unterstützt. Wenn Sie die Briefe aus AEM 6.3 Forms und AEM 6.2 Forms weiterhin verwenden möchten, müssen Sie das Kompatibilitätspaket installieren.

## -Datenintegration {#data-integration}

![](do-not-localize/data-integeration-1.png)

[AEM Forms-Datenintegration](/help/forms/using/data-integration.md) ermöglicht die Konfiguration unterschiedlicher Datenquellen; wie Datenbanken, RESTful- oder SOAP-basierte Webdienste und OData-Dienste; , um ein Formulardatenmodell zu erstellen, mit dem Sie Daten binden, vorab ausfüllen und Dienste in adaptiven Formularen und Dokumenten aufrufen können.

In dieser Version gibt es mehrere neue Funktionen und Verbesserungen bei der Datenintegration.

### Formulardatenmodell ohne Datenquelle erstellen {#create-form-data-model-without-data-source}

Geschäftsbenutzer und Formularverfasser können jetzt ein Formulardatenmodell mit seinen Entitäten und Eigenschaften erstellen, ohne eine Datenquelle zu konfigurieren. Außerdem können sie zum Erstellen adaptiver Formulare und Dokumente verwendet werden. Sie können das Formulardatenmodell später an Datenquellen binden. Sie beseitigt Abhängigkeiten von Datenquellen zum Erstellen von Formularen und Dokumenten mithilfe des Formulardatenmodells.

Ebenso können Sie Entitäten und untergeordnete Eigenschaften in einem vorhandenen Formulardatenmodell erstellen und sie später an entsprechende Entitäten und Eigenschaften in einer Datenquelle binden.

Weitere Informationen finden Sie unter [Erstellen des Formulardatenmodells](/help/forms/using/create-form-data-models.md).

### Erstellen berechneter Eigenschaften {#create-computed-properties}

Forms-Autoren und -Entwickler können berechnete Eigenschaften im Formulardatenmodell erstellen. Sie ermöglichen es Ihnen, einen Wert für die Eigenschaft zu berechnen, indem Sie Regeln oder Logiken für Daten erstellen, die in konfigurierten Datenquellen verfügbar sind. Eine Regel ist ein Ausdruck, der ausgewertet wird, wenn sich die Daten im Formulardatenmodell laden oder die Werte der Eigenschaften im Ausdruck ändern. Beispielsweise berechnet eine berechnete Eigenschaft mit der Bezeichnung &quot;Installments&quot;den monatlichen Betrag, der für einen Kredit zu zahlen ist, basierend auf dem in der Datenquelle angegebenen Zinssatz und dem Darlehensbetrag und der Laufzeit, die vom Benutzer im Formular angegeben wurden.

Eine berechnete Eigenschaft befindet sich lokal in einem Formulardatenmodell und ist nicht in einer Datenquelle vorhanden. Sie können berechnete Eigenschaften in adaptiven Formularen und interaktiver Kommunikation verwenden.

Weitere Informationen finden Sie unter [Arbeiten mit einem Formulardatenmodell](/help/forms/using/work-with-form-data-model.md).

### Vorschau von Formularen und Dokumenten mit Musterdaten {#preview-forms-and-documents-with-sample-data}

Mit dem Formulardatenmodell können Sie Beispieldaten für Eigenschaften aller Entitäten in einem Formulardatenmodell generieren. Die generierten Daten entsprechen den für die Eigenschaften konfigurierten Datentypen. Wenn Sie eine Vorschau eines adaptiven Formulars oder Dokuments anzeigen, das mit dem Formulardatenmodell verknüpft ist, wird es mit vorausgefüllten Beispieldaten wiedergegeben.

Die Beispieldaten sind eine Reihe zufälliger Werte, die sich jedes Mal ändern, wenn Sie sie generieren. Sie können jedoch die Beispieldaten bearbeiten und speichern, die auch dann beibehalten werden, wenn Sie sie neu generieren. Wenn Sie beispielsweise die Beispieldaten für die Eigenschaften &quot;Vorname&quot;und &quot;Nachname&quot;bearbeiten und speichern und später eine weitere Eigenschaft oder Entität zum Formulardatenmodell hinzufügen und die Beispieldaten neu generieren, zeigen die Eigenschaften &quot;Vorname&quot;und &quot;Nachname&quot;die gespeicherten Werte an, während die Werte für andere Eigenschaften neu generiert werden.

Weitere Informationen finden Sie unter [Formulardatenmodell verwenden](/help/forms/using/using-form-data-model.md).

### Datenquellendefinitionen aktualisieren {#refresh-data-source-definitions}

Jegliche Aktualisierung von Datenquellenentitäten oder -eigenschaften wird nicht automatisch in den zugehörigen Formulardatenmodellen widergespiegelt. Der Editor für Formulardatenmodelle bietet jetzt Funktionen ![refresh_forms_di](assets/refresh_forms_di.png) (Datenquellendefinitionen aktualisieren), die den Server-Cache ungültig machen und aktualisiertes Schema aus der Datenquelle abrufen, um es sofort im Formulardatenmodell widerzuspiegeln.

### Konfigurieren von Datenquellen über die Touch-Benutzeroberfläche {#configure-data-sources-using-touch-user-interface}

Mit dieser Version ist die Cloud-Services-Konfiguration für Datenquellen in der Touch-Benutzeroberfläche verfügbar. Außerdem wurde der Speicherort für die Konfiguration von Cloud-Services in **[!UICONTROL Tools > Cloud Services > Data Sources]**. Siehe [Datenquellen konfigurieren](/help/forms/using/configure-data-sources.md).

## Adaptive Formulare {#adaptive-forms}

![simplification-of-authoring-forms-and-documents_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### Verbessern der Leistung adaptiver Formulare mit verbessertem verzögertem Laden {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}

Die Funktion für verzögertes Laden in adaptiven Formularen verzögert die Initialisierung von Formularfragmenten, bis sie benötigt werden. Dadurch wird die Leistung großer Formulare verbessert, indem die zum Rendern eines Formulars erforderliche Zeit minimiert wird, was zu einem besseren Benutzererlebnis führt.

In dieser Version wurden mehrere Verbesserungen an der Funktion für verzögertes Laden vorgenommen:

* Dateianlagen und Komponenten für Nutzungsbedingungen werden in Formularfragmenten mit aktiviertem verzögertem Laden unterstützt.
* Adaptive Formularfragmente mit aktiviertem verzögertem Laden werden in wiederholbaren Bereichen unterstützt.
* Adaptive Formulare mit aktivierten Fragmenten für verzögertes Laden werden in der AEM Forms-App unterstützt.

## Forms-zentrierte AEM {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

Mit Forms-zentrierten AEM können Sie schnell Workflows für verschiedene Aufgaben auf dem OSGi-Stapel erstellen und bereitstellen. Sie müssen nicht mehr die auf dem JEE-Stapel verfügbaren Process Management-Funktionen installieren, um die Bereitstellung zu vereinfachen und die Kosten für Anwendungsserver und Infrastruktur zu senken. Weitere Informationen finden Sie unter [Forms-orientierte Workflows in OSGi](/help/forms/using/aem-forms-workflow.md).

Im Folgenden werden die Verbesserungen bei Forms-zentrierten AEM-Workflows beschrieben: ・

* Der Workflow-Modell-Editor ist in der Touch-Benutzeroberfläche verfügbar. Dies hilft Ihnen, den Zeitaufwand für die Erstellung formularzentrierter AEM-Workflows zu reduzieren.
* Workflow-Schritt zum Senden von E-Mails. Beispielsweise können Sie den E-Mail-Schritt verwenden, um nach Abschluss eines Workflows ein Datensatzdokument zu senden.
* Workflow-Schritt zur Verwendung von Formulardatenmodelldiensten in einem Workflow-Modell. Mit diesem Schritt können Sie Datenintegrationsdienste aufrufen, ohne benutzerdefinierten Code zu schreiben. Sie können beispielsweise einen GET-Dienst aufrufen, um Mitarbeiterdetails aus einem Datenbankarchiv abzurufen, ohne benutzerdefinierten Code zu schreiben.

## AEM Forms-App {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

Mit der AEM Forms-App können Außendienstmitarbeiter ihre Mobilgeräte mit einem AEM Forms-Server synchronisieren und Formulare bearbeiten. Die Anwendung funktioniert nahtlos, wenn das Gerät offline ist, indem Daten lokal auf dem Gerät gespeichert und mit dem Server synchronisiert werden, wenn das Gerät wieder online ist. Weitere Informationen finden Sie unter [AEM Forms-App](/help/forms/using/aem-forms-app.md).

Die folgenden Verbesserungen wurden in der AEM Forms-App vorgenommen:

* Adaptive Formulare mit aktivierten Fragmenten für verzögertes Laden werden in der AEM Forms-App unterstützt.
* Adaptive Formulare mit Formulardatenmodell werden in der AEM Forms-App unterstützt.

## Dokumente – Sicherheit {#document-security}

![aem-forms-document-security-](assets/aem-forms-document-security-.png)

Mit Document Security können Sie alle Informationen, die Sie in einem unterstützten Format gespeichert haben, sicher verteilen. Document Security stellt sicher, dass nur autorisierte Benutzer Ihre Dokumente verwenden können. Im Folgenden finden Sie die wichtigsten Änderungen an Document Security:

* Document Security bietet eine [Portable Protection Library (PPL)](/help/forms/using/document-security-offerings.md) , um ein Dokument lokal zu schützen, ohne es an den AEM Forms-Server zu senden. Nur Sicherheitsberechtigungen und Richtliniendetails werden über das Netzwerk zum AEM Forms-Server übertragen. AEM 6.4 Forms hat die Portable Protection Library (PPL) im OSGi-Bundle-Format eingeführt. Jetzt können Sie die PPL-Bibliothek direkt auf einem AEM Forms-Server installieren und die Funktionen von AEM und PPL gemeinsam nutzen.
* Die C++ SDK- und C++ PPL-Bibliothek von Document Security kann mit Microsoft Visual Studio 2013 kompiliert werden. Die zuvor unterstützte Version war Microsoft Visual Studio 2010.

## Unterstützte Plattformen {#supported-platforms}

AEM Forms kann mit einer beliebigen Kombination von unterstützten Betriebssystemen, Anwendungsservern, Datenbanken, Datenbanktreibern, JDK-, LDAP-Servern und E-Mail-Servern eingerichtet werden. Im Folgenden sind die wichtigsten Änderungen bei den unterstützten Plattformen aufgeführt:

<table> 
 <tbody> 
  <tr> 
   <td>Komponente</td> 
   <td>Unterstützung hinzugefügt</td> 
   <td>Support entfernt</td> 
  </tr> 
  <tr> 
   <td>Betriebssysteme</td> 
   <td> 
    <ul> 
     <li>Microsoft Windows Server 2016</li> 
     <li>Oracle Linux 7 Update 3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM AIX 7.2 <sup>[1]</sup><br /> </li> 
     <li>Solaris 11 <sup>[1]</sup></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Anwendungsserver<br /> </td> 
   <td> 
    <ul> 
     <li>Red Hat JBoss EAP 7</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM Weblogic 12.1.3</li> 
     <li>IBM WebSphere 8.5.5</li> 
     <li>Red Hat JBoss EAP 6</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Datenbanken</td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2016</li> 
     <li>MySQL 5.7.19 und höher</li> 
     <li>IBM DB2 11.1</li> 
     <li>Oracle Multitenant-Architektur</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2012<br /> </li> 
     <li>Microsoft SQL Server 2014</li> 
     <li>MySQL 5.5</li> 
     <li>IBM DB2 10.5<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>LDAP-Server</td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2016</li> 
     <li>IBM Tivoli Directory Server 6.4</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2008</li> 
     <li>IBM Tivoli Directory Server 6.3</li> 
     <li>Oracle Directory Server Enterprise Edition 7.0</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>E-Mail-Server</td> 
   <td> 
    <ul> 
     <li>Microsoft Office 365</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Novell Groupway 7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Connectoren</td> 
   <td> 
    <ul> 
     <li>Connector für Microsoft Sharepoint 2016</li> 
     <li>Connector für EMC Documentum 7.3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Connector für Microsoft Sharepoint 2007</li> 
     <li>Connector für Microsoft Sharepoint 2010</li> 
     <li>Connector für IBM Filenet 5.0</li> 
     <li>Connector für EMC Documentum 6.7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Browser</td> 
   <td> 
    <ul> 
     <li>Apple Safari 11.x auf macOS</li> 
     <li>Apple Safari 11.x auf iOS</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Blackberry-Browser für Blackberry Z30- und Q10-Geräte</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>AEM Forms-App<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4 oder höher</li> 
     <li>Apple iOS 10 oder höher</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. AIX- und Solaris-Betriebssysteme sind nur für Upgrade-Kunden verfügbar.
