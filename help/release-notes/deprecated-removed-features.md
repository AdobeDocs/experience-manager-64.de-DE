---
title: Veraltete und entfernte Funktionen
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager 6.4.
translation-type: tm+mt
source-git-commit: 5b00783e4471a6b142ab17a7bc4a647ab04aec5f
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 47%

---


# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Für die Bekanntgabe des bevorstehenden Entfernens/Ersetzens von AEM-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Die Funktionen sind zwar nicht mehr unterstützt, aber sie werden nicht weiter verbessert.
1. Das Entfernen veralteter Funktionen erfolgt frühestens mit Einführung der nächsten Hauptversion. Das geplante Datum für die Entfernung wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

Die folgende Tabelle zeigt Funktionen und Funktionen, die als nicht mehr unterstützt mit AEM 6.4 gekennzeichnet wurden. Im Allgemeinen werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zuerst auf &quot;Veraltet&quot;eingestellt, wobei eine Alternative bereitgestellt wird.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und Pläne zur Änderung ihrer Implementierung zu erstellen, um die bereitgestellte Alternative nutzen zu können.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| Bereich | Funktion | Ersatz |
|---|---|---|
| Benutzeroberfläche | Adobe plant keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. In AEM 6.4 ist die klassische Benutzeroberfläche integriert und Kunden, die ein Upgrade auf diese Version durchführen, können diese wie gehabt verwenden. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (Seiteneditor) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | Kunden wird empfohlen, auf die neue AEM-Benutzeroberfläche umzusteigen. |
| Komponenten  | Adobe plant keine weiteren Verbesserungen an den im Folgenden aufgeführten Foundation-Komponenten. AEM 6.4 enthält die Foundation-Komponenten, und Kunden, die von früheren Versionen aktualisieren, können diese weiterhin wie bisher verwenden. Beachten Sie, dass die Foundation-Komponenten zwar veraltet sind, aber weiterhin umfassend unterstützt werden. <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/passwordreset </li> <li> foundation/components/account/requestconfirmation </li> <li> foundation/components/adaptiveimage </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/breadcrumb </li> <li> foundation/components/form/creditcard </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | Kunden wird empfohlen, für künftige Projekte die Kernkomponenten zu verwenden. Bestehende Sites müssen nicht geändert werden. |
| Komponenten  | Adobe plant keine weiteren Verbesserungen an den im Folgenden aufgeführten Foundation-Komponenten. AEM 6.4 enthält die Foundation-Komponenten, und Kunden, die von früheren Versionen aktualisieren, können diese weiterhin wie bisher verwenden. Beachten Sie, dass die Foundation-Komponenten zwar veraltet sind, aber weiterhin umfassend unterstützt werden. <ul><li>foundation/components/timing</li></ul> | Adobe plant keine Ersatzlieferung. |
| Director | Das Portal Director ist eine Reihe von Funktionen, die das Hosting von AEM Inhalten über Portlet in Drittanbieterservern ermöglichen. Adobe plant keine weiteren Verbesserungen der Funktion &quot;Portal Director&quot;unter dem unten aufgeführten Speicherort. In AEM 6.4 ist das Portal Director enthalten, und Kunden, die ein Upgrade von früheren Versionen durchführen, können es weiterhin wie bisher verwenden. Beachten Sie, dass Portal Direct weiterhin vollständig unterstützt wird, während es nicht mehr unterstützt wird. <ul><li>/libs/portal/direktor</li></ul> | Adobe plant keine Ersatzlieferung. |
| Portlet-Komponente | Portlet Components unter /foundation/components/portlet ermöglicht das Hosting von JSR Portlets in AEM als Komponenten. Adobe plant keine weiteren Verbesserungen der Funktion Portlet Component. AEM 6.4 enthält die Portlet-Komponente, und Kunden, die ein Upgrade von früheren Versionen durchführen, können diese weiterhin verwenden. Beachten Sie, dass die Portlet-Komponente weiterhin vollständig unterstützt wird, während sie nicht mehr unterstützt wird. | Adobe plant keine Ersatzlieferung. |
| Formulare | Die Unterstützung für den Adobe Central Migration Bridge-Service wird eingestellt, da Adobe Central nicht länger unterstützt wird. | Kein Ersatz vorhanden. |
| Formulare | Veraltete Verwendung von JSONObject in Abfrage und OperationOptions. Die folgenden APIs werden nicht mehr unterstützt: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | Verwenden der `IValueMap`-API |
| Formulare | Veralteter Central Migration Bridge-Dienst. | Es wird kein Ersatz angeboten. |
| Assets | Das Assets-Offload wurde mit AEM 6.4 eingestellt. |  |
| Entwickler | Client-Bibliothek &quot;Lodash/Unterstrich&quot;. Adobe plant nicht, die Lodash/underscore-Client-Bibliothek, die im Lieferumfang enthalten ist, weiter zu pflegen und zu aktualisieren (Quickstart) | Adobe empfiehlt Kunden, die für ihren Code immer noch einen Lodash/Unterstrich benötigen, um ihn in ihre Projektcodebasis einzufügen. |

<!-- Original HTML table that came from helpx during migration.

<table> 
 <tbody>
  <tr>
   <td>Area</td> 
   <td>Feature</td> 
   <td>Replacement</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe does not plan to make further enhancements to the Classic UI. AEM 6.4 has the Classic UI included, and customers upgrading from earlier releases can keep using it as is. Note that Classic UI remains fully supported while being deprecated. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Page Editor)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Customers are advised to switch to use the new AEM UI.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordreset</li> 
     <li>foundation/components/account/requestconfirmation</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>foundation/components/assetsharepage</li> 
     <li>foundation/components/breadcrumb</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listchildren</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilefooter</li> 
     <li>foundation/components/mobileimage</li> 
     <li>foundation/components/mobilelist</li> 
     <li>foundation/components/mobilelogo</li> 
     <li>foundation/components/mobilereference</li> 
     <li>foundation/components/mobiletextimage</li> 
     <li>foundation/components/mobiletopnav</li> 
     <li>foundation/components/search</li> 
     <li>foundation/components/sitemap</li> 
     <li>foundation/components/table</li> 
     <li>foundation/components/toolbar</li> 
     <li>foundation/components/topnav</li> 
     <li>foundation/components/userinfo</li> 
    </ul> </td> 
   <td>Customers are advised to use the Core Components for future projects. Existing sites do not need to be changed.</td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portal Director</td> 
   <td><p>The Portal Director is a set of features, that enables the hosting of AEM content via Portlet in 3rd party servers.</p> <p>Adobe does not plan to make further enhancements to the Portal Director feature under the location listed below. AEM 6.4 has the Portal Director included, and customers upgrading from earlier releases can keep using it as is. Note that Portal Direct remains fully supported while being deprecated.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portlet Component</td> 
   <td><p>Portlet Components under /foundation/components/portlet enables the hosting of JSR Portlets in AEM as components.</p> <p>Adobe does not plan to make further enhancements to the Portlet Component feature. AEM 6.4 has the Portlet Component included, and customers upgrading from earlier releases can keep using it as is. Note that Portlet Component remains fully supported while being deprecated.</p> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Support for Adobe Central Migration Bridge service has been deprecated as Adobe Central product is no longer supported.</p> </td> 
   <td>No replacement </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Deprecated use of JSONObject in Query and OperationOptions. The following APIs are deprecated:
   <ul><li>setArguments(JSONObject arguments)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject arguments</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject arguments)</li></ul>
   </p> </td> 
   <td>Use the IValueMap API </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Deprecated Central Migration Bridge service</p> </td> 
   <td> No replacement </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>Assets Offloading has been deprecated starting with AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>
-->

## Entfernte Funktionen {#removed-features}

In der folgenden Tabelle werden Funktionen und Funktionen Liste, die aus AEM 6.4 entfernt wurden. In früheren Versionen wurden diese Funktionen als
nicht mehr unterstützt.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Analytics Activity Map | Die Version der Activity Map, die in AEM enthalten ist. | Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden. Das [Activity Map-Plugin, das von Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=de#activity-map) bereitgestellt wird, sollte jetzt verwendet werden. |
| Components-Forms | Captcha-Formularkomponente (foundation/components/form/captcha) | Verwenden Sie stattdessen reCAPTCHA von Google. |
| Komponenten  | Bildschirmpräsentation (foundation/components/slideshow) | Kein Ersatz |
| Komponenten  | Flash (foundation/components/flash) | Kein Ersatz |
| Komponenten  | Unterstützung für Wiedergabe von SWF-Dateien in der Videokomponente eingestellt (foundation/components/video) | Verwenden Sie Videoformate, die nicht auf Flash basieren. |
| Komponenten  | Produkttabelle (commerce/components/product_table) | Kein Ersatz |
| Aufgabenverwaltung | Aufgabenverwaltung der klassischen Benutzeroberfläche (/libs/cq/taskmanagement/content/taskmanager.html) | Veraltet seit Version 6.0. Verwenden Sie die neue, mit der Workflow-Benutzeroberfläche verbundene Aufgabenverwaltung. |
| Workflow | Benachrichtigungs-UI, die von Version 5.6 bis Version 6.2 verwendet wurde (/libs/cq/workflow/content/notifications.html) | Workflow-Posteingang /aem/inbox |
| Formulare | Die Funktion zum Exportieren von PDF in das PDF/E-1-Format mit PDF Generator wurde entfernt. | PDF Generator unterstützt weiterhin das Exportieren von PDF-Dateien in die Formate PDF/A-1a/b, PDF/A-2a/b und PDF/A-3a/b. |
| Formulare | Unterstützung für Bilder in Dokumentfragmenten wurde eingestellt. | Interaktive Kommunikation ermöglicht es, Bilder direkt in Print- und Web-Kanälen zu verwenden. |
| Formulare | Nicht ersetzende Aktualisierung | Unterstützung für eine nicht ersetzende Aktualisierung ist nicht verfügbar |
| Formulare | Sidegrade für TarMK zu DocumentMK-Migrationen | Sie können die Daten aus einem älteren System exportieren und dann in ein frisch eingerichtetes System importieren. Detaillierte Anweisungen finden Sie in den Dokumentation zu AEM Forms on JEE-Upgrades |
| Formulare | AEM Forms on JEE 32-Bit-Installationsprogramm nicht verfügbar. | Adobe hat den Versand von AEM Forms mit dem 32-Bit-Installationsprogramm für JEE eingestellt. Sie können AEM Forms unter JEE weiterhin mit dem 64-Bit-Installationsprogramm installieren. |
| Formulare | Die Unterstützung für die Verwendung von DAM-Bildern in der Dokument Fragment-Komponente wurde entfernt. | Sie können die Bild- und Diagrammkomponente im Kanal &quot;Drucken&quot;der interaktiven Kommunikation verwenden. Wenn Sie die Dokument-Fragmentkomponente des adaptiven Dokuments in adaptiven Formularen verwenden, funktioniert sie nach der Aktualisierung auf AEM 6.4 Forms nicht mehr. |
| Formulare | Die Funktion Adaptive Dokumente wurde entfernt | Mit der Funktion für interaktive Kommunikation können Sie gedruckte und webbasierte Kommunikation erstellen. Wenn Sie adaptive Dokumente verwenden, installieren Sie das Kompatibilitätspaket, um weiterhin vorhandene adaptive Dokumente zu verwenden |
| Formulare | AEM Forms on JEE-spezifische Landingpage wurde entfernt. | AEM Forms on JEE-Landingpage wird durch AEM Landingpage ersetzt (/aem/start.html) |
| Formulare | Die Unterstützung für Captcha-Standarddateien wurde entfernt | Verwenden Sie den reCAPTCHA-Dienst von Google. |
| Formulare | Die Unterstützung für Flash-Felder in AEM Designer wurde entfernt. AEM Designer lässt die Bearbeitung von Flash-Feldern in einem Formular nicht zu. | Sie können AEM Designer verwenden, der für eine frühere Version veröffentlicht wurde, um solche Formulare zu bearbeiten. |
| Communities | Die Unterstützung für die Captcha-Überprüfung wurde entfernt. | Verwenden Sie zur Verifizierung benutzerdefinierte Captcha-Integration (z. B. reCAPTCHA von Google). |

## Vorankündigung für die nächste Version {#pre-announcement-for-next-release}

Die nachstehende Tabelle enthält eine Liste der Änderungen für zukünftige Versionen, die nicht mehr unterstützt werden, sich aber auf Kunden auswirken können. Diese werden für Planungszwecke bereitgestellt.

| Bereich | Funktion | Mitteilung |
|---|---|---|
| Browserunterstützung | Microsoft Internet Explorer | AEM 6.4 ist die letzte Version, die Microsoft Internet Explorer 11 unterstützt. |
| Foundation | UI-Framework | Adobe stellt die Coral UI 2-Komponenten im Jahr 2019 ein. AEM 6.4 basiert vollständig auf Coral UI 3 (eingeführt mit AEM 6.2). Adobe empfiehlt seinen Kunden und Partnern, die benutzerdefinierte UIs mit Coral 2 erstellt haben, diese in Coral 3 umzuwandeln. Adobe Angebot ein Tool zum Konvertieren von Coral 2-Dialogen in Coral 3 - [Weitere Informationen.](/help/sites-developing/modernization-tools.md) |
