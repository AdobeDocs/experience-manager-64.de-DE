---
title: Veraltete und entfernte Funktionen
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager 6.4.
exl-id: 2fe0dad7-fc78-4aac-afa3-79a278008453
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1344'
ht-degree: 24%

---

# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Für die Mitteilung der bevorstehenden Entfernung/Ersetzung AEM Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Obwohl diese Funktion nicht mehr unterstützt wird, sind die Funktionen weiterhin verfügbar, sie werden jedoch nicht weiter verbessert.
1. Die veralteten Funktionen werden frühestens in der folgenden Hauptversion entfernt. Das geplante Datum für die Entfernung wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In der folgenden Tabelle sind die Funktionen aufgeführt, die in AEM 6.4 als veraltet gekennzeichnet wurden. Im Allgemeinen werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zunächst als veraltet gekennzeichnet und es wird eine Alternative bereitgestellt.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und Pläne zur Änderung ihrer Implementierung zu erstellen, um die bereitgestellte Alternative nutzen zu können.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| Bereich | Funktion | Ersatz |
|---|---|---|
| Benutzeroberfläche | Adobe plant keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. AEM Version 6.4 enthält die klassische Benutzeroberfläche, und Kunden, die ein Upgrade von früheren Versionen durchführen, können diese weiterhin unverändert verwenden. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (Seiteneditor) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | Kunden wird empfohlen, zur Verwendung der neuen AEM-Benutzeroberfläche zu wechseln. |
| Komponenten | Adobe plant keine weiteren Verbesserungen an den unten aufgeführten Foundation-Komponenten. Die Foundation-Komponenten sind in AEM 6.4 enthalten und Kunden, die auf diese Version aktualisieren, können diese wie gehabt verwenden. Beachten Sie, dass Foundation-Komponenten weiterhin vollständig unterstützt werden, während sie nicht mehr unterstützt werden. <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/passwordreset </li> <li> foundation/components/account/requestvalidation </li> <li> foundation/components/adaptiveimage </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/breadcrumb </li> <li> foundation/components/form/creditcard </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | Kunden wird empfohlen, die Kernkomponenten für zukünftige Projekte zu verwenden. Vorhandene Sites müssen nicht geändert werden. |
| Komponenten | Adobe plant keine weiteren Verbesserungen an den unten aufgeführten Foundation-Komponenten. Die Foundation-Komponenten sind in AEM 6.4 enthalten und Kunden, die auf diese Version aktualisieren, können diese wie gehabt verwenden. Beachten Sie, dass Foundation-Komponenten weiterhin vollständig unterstützt werden, während sie nicht mehr unterstützt werden. <ul><li>foundation/components/timing</li></ul> | Adobe plant keine Ersatzlieferung. |
| Portal Director | Das Portal Director ist eine Reihe von Funktionen, die das Hosting AEM Inhalte über Portlet auf Drittanbieter-Servern ermöglichen. Adobe plant keine weiteren Verbesserungen an der Funktion Portal Director unter dem unten aufgeführten Speicherort. In AEM 6.4 ist das Portal Director enthalten, und Kunden, die ein Upgrade von früheren Versionen durchführen, können es weiterhin unverändert verwenden. Beachten Sie, dass Portal Direct auch weiterhin vollständig unterstützt wird, wenn es nicht mehr unterstützt wird. <ul><li>/libs/portal/director</li></ul> | Adobe plant keine Ersatzlieferung. |
| Portlet-Komponente | Portlet-Komponenten unter /foundation/components/portlet ermöglichen das Hosting von JSR-Portlets in AEM als Komponenten. Adobe plant keine weiteren Verbesserungen an der Portlet-Komponenten-Funktion. AEM 6.4 ist die Portlet-Komponente enthalten, und Kunden, die von früheren Versionen aktualisieren, können sie weiterhin wie bisher verwenden. Beachten Sie, dass die Portlet-Komponente weiterhin vollständig unterstützt wird, obwohl sie nicht mehr unterstützt wird. | Adobe plant keine Ersatzlieferung. |
| Formulare | Die Unterstützung für den Central Migration Bridge-Dienst von Adobe wurde eingestellt, da Adobe Central nicht mehr unterstützt wird. | Kein Ersatz vorhanden. |
| Formulare | Veraltete Verwendung von JSONObject in Query and OperationOptions. Die folgenden APIs werden nicht mehr unterstützt: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | Verwenden Sie die `IValueMap` API |
| Formulare | Veralteter Central Migration Bridge-Dienst. | Es wird kein Ersatz angeboten. |
| Assets | Die Asset-Abladung wird ab AEM 6.4 nicht mehr unterstützt. |  |
| Entwickler  | Lodash/Underscore-Client-Bibliothek Adobe plant keine weitere Pflege und Aktualisierung der Lodash/Underscore-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die nach wie vor Lodash/Underscore für ihren Code benötigen, diese Erweiterung zu ihrer Projekt-Code-Basis hinzuzufügen. |

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

In der folgenden Tabelle sind die Funktionen aufgeführt, die aus AEM 6.4 entfernt wurden. Frühere Versionen hatten diese Funktionen als veraltet gekennzeichnet.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integration mit [!DNL Experience Cloud] | Sie können Ihre Assets mit [!DNL Experience Cloud] synchronisieren, mithilfe einer Konfiguration über [!DNL Adobe I/O]. [!DNL Adobe Experience Cloud] hieß zuvor [!DNL Adobe Marketing Cloud]. | Bei Fragen wenden Sie sich an [Adobe-Kundensupport](https://experienceleague.adobe.com/?support-solution=General&amp;lang=de#support). |
| Analytics-Activity Map | Die Version der Activity Map, die in AEM enthalten ist. | Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden. Die [Von Adobe Analytics bereitgestelltes ActivityMap-Plugin](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=de) verwendet werden. |
| Components-Forms | Form Captcha (foundation/components/form/captcha) | Verwenden Sie stattdessen die Komponente Captcha nach Google . |
| Komponenten | Bildschirmpräsentation (foundation/components/slideshow) | Kein Ersatz vorhanden. |
| Komponenten | Flash (foundation/components/flash) | Kein Ersatz vorhanden. |
| Komponenten | Die Unterstützung für die Wiedergabe von SWF-Dateien in der Videokomponente wurde entfernt (foundation/components/video) | Verwenden Sie nicht-Flash-basierte Videoformate. |
| Komponenten | Produkttabelle (commerce/components/product_table) | Kein Ersatz vorhanden. |
| Aufgabenverwaltung | Aufgabenverwaltung der klassischen Benutzeroberfläche (/libs/cq/taskmanagement/content/taskmanager.html) | Veraltet seit 6.0. Verwenden Sie die neue Aufgabenverwaltung, die mit der Workflow-Benutzeroberfläche kombiniert wird. |
| Workflow | Benachrichtigungs-UI, die zwischen 5.6 und 6.2 verwendet wird (/libs/cq/workflow/content/notifications.html) | Workflow-Posteingang /aem/inbox |
| Formulare | Export PDF zum PDF/E-1-Format mithilfe von PDF Generator wurde entfernt. | PDF Generator unterstützt weiterhin den Export von PDF in die Formate PDF/A-1a/b, PDF/A-2a/b und PDF/A-3a/b. |
| Formulare | Die Unterstützung für Bilder in Dokumentfragmenten wurde entfernt. | Interaktive Kommunikation bietet die Möglichkeit, Bilder direkt in Druck- und Webkanälen zu verwenden. |
| Formulare | Nicht ersetzende Aktualisierung | Unterstützung für nicht ersetzende Aktualisierung ist nicht verfügbar |
| Formulare | Sidegrade für TarMK- zu DocumentMK-Migrationen | Sie können die Daten aus einem älteren System exportieren und dann in ein neu eingerichtetes System importieren. Detaillierte Anweisungen finden Sie in der Dokumentation zur Aktualisierung auf AEM Forms on JEE . |
| Formulare | AEM Forms on JEE 32-Bit-Installationsprogramm nicht verfügbar. | Adobe hat den Versand des 32-Bit-Installationsprogramms für AEM Forms on JEE eingestellt. Sie können das 64-Bit-Installationsprogramm weiterhin verwenden, um AEM Forms on JEE zu installieren. |
| Formulare | Die Unterstützung für die Verwendung von DAM-Bildern in der Dokumentfragment-Komponente wurde entfernt. | Sie können die Bild- und Diagrammkomponente im Druckkanal der interaktiven Kommunikation verwenden. Wenn Sie die Dokumentfragmentkomponente des adaptiven Dokuments in adaptiven Formularen verwenden, funktioniert sie nach der Aktualisierung auf AEM 6.4 Forms nicht mehr. |
| Formulare | Funktion &quot;Adaptive Dokumente&quot;entfernt | Sie können die interaktive Kommunikationsfunktion verwenden, um gedruckte und webbasierte Kommunikation zu erstellen. Wenn Sie adaptive Dokumente verwenden, installieren Sie das Kompatibilitätspaket, um vorhandene adaptive Dokumente weiterhin zu verwenden |
| Formulare | AEM Forms on JEE-spezifische Landingpage entfernt. | Die Landingpage von AEM Forms on JEE wird durch AEM Landingpage ersetzt (/aem/start.html). |
| Formulare | Unterstützung für standardmäßiges Captcha entfernt | Verwenden Sie den reCAPTCHA-Dienst von Google. |
| Formulare | Die Unterstützung für Flash-Felder in AEM Designer wurde entfernt. AEM Designer lässt die Bearbeitung von Flash-Feldern, die in einem Formular verwendet werden, nicht zu. | Sie können AEM Designer verwenden, der für eine frühere Version veröffentlicht wurde, um solche Formulare zu bearbeiten. |
| Communities | Unterstützung für die Captcha-Verifizierung wurde entfernt. | Verwenden Sie zur Überprüfung die benutzerdefinierte Captcha-Integration (z. B. reCAPTCHA von Google). |

## Vorankündigung für die nächste Version {#pre-announcement-for-next-release}

Die nachstehende Tabelle enthält eine Liste der Änderungen für die künftige Version, die nicht veraltet sind, sich aber auf Kunden auswirken können. Diese werden für Planungszwecke bereitgestellt.

| Bereich | Funktion | Ankündigung |
|---|---|---|
| Browser-Unterstützung | Microsoft Internet Explorer | AEM 6.4 ist die letzte Version, die Microsoft Internet Explorer 11 unterstützt. |
| Foundation | UI-Framework | Die Coral UI 2-Komponenten von Adobe werden 2019 nicht mehr unterstützt. AEM 6.4 basiert vollständig auf Coral UI 3 (eingeführt mit AEM 6.2). Adobe empfiehlt seinen Kunden und Partnern, die benutzerdefinierte Benutzeroberflächen mit Coral 2 erstellt haben, diese in Coral 3 umzuwandeln. Adobe bietet ein Tool zum Konvertieren von Coral 2-Dialogfeldern in Coral 3 - [Mehr dazu.](/help/sites-developing/modernization-tools.md) |
