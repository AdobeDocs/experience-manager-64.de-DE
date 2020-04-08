---
title: Veraltete und entfernte Funktionen
seo-title: Veraltete und entfernte Funktionen
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager 6.4.
seo-description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager 6.4.
uuid: 2619039b-72b4-4c6c-a813-90eed622b423
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 15819d42-4897-40fa-a013-e019d1580fa2
translation-type: tm+mt
source-git-commit: 3316dbc8ef268be2b305d22da9003ae40414b4e1

---


# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe bewertet die Produktfunktionen ständig, um ältere Funktionen mit der Zeit neu zu erfinden oder durch modernere Alternativen zu ersetzen, um den Gesamtwert der Kunden zu verbessern, wobei stets die Abwärtskompatibilität zu berücksichtigen ist.

Für die Bekanntgabe des bevorstehenden Entfernens/Ersetzens von AEM-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Die Funktion bleibt aber trotzdem weiterhin verfügbar, wird jedoch nicht weiter verbessert.
1. Das Entfernen veralteter Funktionen erfolgt frühestens mit Einführung der nächsten Hauptversion. Das geplante Datum für die Entfernung wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden die Funktionen aufgelistet, die in AEM 6.4 als veraltet gekennzeichnet wurden. Im Allgemeinen werden Funktionen, deren Entfernung in einer zukünftigen Version geplant ist, zunächst als veraltet gekennzeichnet und es wird eine Alternative bereitgestellt.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Bereitstellung nutzen, und Pläne zur Änderungen ihrer Implementierung zu erstellen, um die bereitgestellte Alternative nutzen zu können.

<table> 
 <tbody>
  <tr>
   <td>Bereich</td> 
   <td>Funktion</td> 
   <td>Ersatz</td> 
  </tr>
  <tr>
   <td>Benutzeroberfläche</td> 
   <td><p>Adobe plant keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. In AEM 6.4 ist die klassische Benutzeroberfläche integriert und Kunden, die ein Upgrade auf diese Version durchführen, können diese wie gehabt verwenden. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Seiten-Editor)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Kunden wird empfohlen, auf die neue AEM-Benutzeroberfläche umzusteigen.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Komponenten</td> 
   <td><p>Adobe plant keine weiteren Verbesserungen an den im Folgenden aufgeführten Foundation-Komponenten. In AEM 6.4 sind die Foundation-Komponenten enthalten, und Kunden, die von früheren Versionen aktualisieren, können diese weiterhin wie bisher verwenden. Beachten Sie, dass die Foundation-Komponenten zwar veraltet sind, aber weiterhin umfassend unterstützt werden. </p> 
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
   <td>Kunden wird empfohlen, für künftige Projekte die Kernkomponenten zu verwenden. Bestehende Sites müssen nicht geändert werden.</td> 
  </tr>
  <tr>
   <td>Komponenten</td> 
   <td><p>Adobe plant keine weiteren Verbesserungen an den im Folgenden aufgeführten Foundation-Komponenten. In AEM 6.4 sind die Foundation-Komponenten enthalten, und Kunden, die von früheren Versionen aktualisieren, können diese weiterhin wie bisher verwenden. Beachten Sie, dass die Foundation-Komponenten zwar veraltet sind, aber weiterhin umfassend unterstützt werden.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>Beim Schreiben ist es nicht geplant, einen Ersatz zu liefern.</td> 
  </tr>
  <tr>
   <td>Portal-Direktor</td> 
   <td><p>Der Portal-Direktor ist eine Reihe von Funktionen, die das Hosting von AEM-Inhalten über das Portlet in Drittanbieter-Servern ermöglichen.</p> <p>Adobe plant keine weiteren Verbesserungen an der Funktion "Portal-Direktor"unter dem unten aufgeführten Speicherort. In AEM 6.4 ist der Portal-Director enthalten, und Kunden, die ein Upgrade von früheren Versionen durchführen, können das Programm weiterhin wie bisher verwenden. Beachten Sie, dass Portal Direct weiterhin vollständig unterstützt wird, während es nicht mehr unterstützt wird.</p> 
    <ul> 
     <li>/libs/portal/direktor</li> 
    </ul> </td> 
   <td>Beim Schreiben ist es nicht geplant, einen Ersatz zu liefern.</td> 
  </tr>
  <tr>
   <td>Portlet-Komponente</td> 
   <td><p>Portlet Components unter /foundation/components/portlet ermöglicht das Hosting von JSR Portlets in AEM als Komponenten.</p> <p>Adobe plant keine weiteren Verbesserungen an der Funktion "Portlet-Komponenten". In AEM 6.4 ist die Portlet-Komponente enthalten, und Kunden, die ein Upgrade von früheren Versionen durchführen, können diese weiterhin verwenden. Beachten Sie, dass die Portlet-Komponente weiterhin vollständig unterstützt wird, während sie nicht mehr unterstützt wird.</p> </td> 
   <td>Beim Schreiben ist es nicht geplant, einen Ersatz zu liefern.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Die Unterstützung für den Adobe Central Migration Bridge-Service wird eingestellt, da Adobe Central nicht länger unterstützt wird.</p> </td> 
   <td>Kein Ersatz vorhanden. </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Veraltete Verwendung von JSONObject in Abfrage und OperationOptions. Die folgenden APIs werden nicht mehr unterstützt:
   <ul><li>setArguments(JSONObject-Argumente)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject-Argumente</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject-Argumente)</li></ul>
   </p> </td> 
   <td>IValueMap-API verwenden </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>Das Assets-Abladen wurde ab AEM 6.4 nicht mehr unterstützt.</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen Liste, die aus AEM 6.4 entfernt wurden. Frühere Versionen hatten diese Funktionen als veraltet markiert.

<table> 
 <tbody>
  <tr>
   <td><strong>Bereich</strong></td> 
   <td><strong>Funktion</strong></td> 
   <td><strong>Ersatz</strong></td> 
  </tr>
  <tr>
   <td>Analytics-Aktivität-Map</td> 
   <td>Die Version der Aktivität Map, die in AEM enthalten ist.</td> 
   <td>Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden.<br><br>Das <a href="https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html">Activity Map-Plugin, das von Adobe Analytics</a> bereitgestellt wird, sollte jetzt verwendet werden.</td> 
  </tr>
  <tr>
   <td>Komponenten</td> 
   <td>Captcha-Formularkomponente<br /> (foundation/components/form/captcha)</td> 
   <td>Verwenden Sie stattdessen reCAPTCHA von Google.</td> 
  </tr>
  <tr>
   <td>Komponenten</td> 
   <td>Bildschirmpräsentation<br /> (foundation/components/slideshow)</td> 
   <td>Kein Ersatz</td> 
  </tr>
  <tr>
   <td>Komponenten</td> 
   <td>Flash<br /> (foundation/components/flash)</td> 
   <td>Kein Ersatz</td> 
  </tr>
  <tr>
   <td>Komponenten</td> 
   <td>Unterstützung für Wiedergabe von SWF-Dateien in der Videokomponente eingestellt<br /> (foundation/components/video)</td> 
   <td>Verwenden Sie Videoformate, die nicht auf Flash basieren.</td> 
  </tr>
  <tr>
   <td>Komponenten</td> 
   <td>Produkttabelle<br /> (commerce/components/product_table)</td> 
   <td>Kein Ersatz</td> 
  </tr>
  <tr>
   <td>Aufgabenverwaltung</td> 
   <td>Aufgabenverwaltung der klassischen Benutzeroberfläche<br /> (/libs/cq/taskmanagement/content/taskmanager.html)</td> 
   <td>Veraltet seit Version 6.0. Verwenden Sie die neue, mit der Workflow-Benutzeroberfläche verbundene Aufgabenverwaltung.</td> 
  </tr>
  <tr>
   <td>Workflow</td> 
   <td>Benachrichtigungs-UI, die von Version 5.6 bis Version 6.2 verwendet wurde<br /> (/libs/cq/workflow/content/notifications.html)</td> 
   <td>Workflow-Posteingang /aem/inbox</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>Die Funktion zum Exportieren von PDF in das PDF/E-1-Format mit PDF Generator wurde entfernt.</td> 
   <td>PDF Generator unterstützt weiterhin das Exportieren von PDF-Dateien in die Formate PDF/A-1a/b, PDF/A-2a/b und PDF/A-3a/b.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>Die Unterstützung für den standardmäßigen AEM Captcha-Dienst in adaptiven Formularen wurde entfernt. </td> 
   <td>Verwenden Sie stattdessen reCAPTCHA von Google.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>Unterstützung für Bilder in Dokumentfragmenten wurde eingestellt. </td> 
   <td>Interaktive Kommunikation ermöglicht es, Bilder direkt in Print- und Web-Kanälen zu verwenden.<br /> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td> Nicht ersetzende Aktualisierung </td> 
   <td>Unterstützung für eine nicht ersetzende Aktualisierung ist nicht verfügbar <br/> </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td> Sidegrade für TarMK zu DocumentMK-Migrationen </td> 
   <td> Sie können die Daten aus einem älteren System exportieren und dann in ein frisch eingerichtetes System importieren. Detaillierte Anweisungen finden Sie in den Dokumentation zur Aktualisierung von AEM Forms on JEE <br/> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
 <td>Das 32-Bit-Installationsprogramm für AEM Forms on JEE ist nicht verfügbar.</td> 
   <td>Adobe hat den Versand des 32-Bit-Installationsprogramms für AEM Forms on JEE eingestellt. Sie können AEM Forms on JEE weiterhin mit dem 64-Bit-Installationsprogramm installieren. </td>  
  </tr>
    <tr>
    <td>Forms</td> 
    <td>Die Unterstützung für die Verwendung von DAM-Bildern in der Dokument Fragment-Komponente wurde entfernt.</td> 
    <td> Sie können die Bild- und Diagrammkomponente im Kanal "Drucken"der interaktiven Kommunikation verwenden. Wenn Sie die Dokument-Fragmentkomponente des adaptiven Dokuments in adaptiven Formularen verwenden, funktioniert sie nach der Aktualisierung auf AEM 6.4 Forms nicht mehr. </td>  
  </tr>
  <tr>
   <td>Forms</td> 
   <td> Die Funktion Adaptive Dokumente wurde entfernt</td> 
   <td> Mit der Funktion für interaktive Kommunikation können Sie gedruckte und webbasierte Kommunikation erstellen. Wenn Sie adaptive Dokumente verwenden, installieren Sie das Kompatibilitätspaket, um weiterhin vorhandene adaptive Dokumente zu verwenden<br/> </td> 
  </tr>
    <tr>
    <td>Forms</td> 
    <td>AEM Forms on JEE-spezifische Landingpage entfernt.</td> 
    <td>AEM Forms on JEE-Landingpage wird durch AEM Landingpage ersetzt (/aem/start.html) </td>  
  </tr>
   <tr>
   <td>Forms</td> 
   <td>Die Unterstützung für Captcha-Standarddateien wurde entfernt</td> 
   <td>Verwenden Sie den reCAPTCHA-Dienst von Google.</td> 
  </tr>
   <tr>
   <td>Forms</td> 
   <td>Die Unterstützung für Captcha-Standarddateien wurde entfernt</td> 
   <td>Verwenden Sie den reCAPTCHA-Dienst von Google.</td> 
  </tr>
  <tr>
   <td>Communities</td> 
   <td>Die Unterstützung für die Captcha-Überprüfung wurde entfernt.</td> 
   <td>Verwenden Sie zur Verifizierung benutzerdefinierte Captcha-Integration (z. B. reCAPTCHA von Google).</td> 
  </tr>
 </tbody>
</table>

## Vorankündigung für die nächste Version {#pre-announcement-for-next-release}

Dieser Abschnitt wird verwendet, um Änderungen in der zukünftigen Version vorab bekannt zu geben, bei denen es sich nicht um veraltete Funktionen handelt, die aber Auswirkungen für Kunden haben. Diese werden für Planungszwecke bereitgestellt.

<table> 
 <tbody>
  <tr>
   <td>Bereich<br /> </td> 
   <td>Funktion<br /> </td> 
   <td>Ankündigung</td> 
  </tr>
  <tr>
   <td>Browserunterstützung</td> 
   <td>Microsoft Internet Explorer</td> 
   <td>AEM 6.4 ist die letzte Version, die Microsoft Internet Explorer 11 unterstützt.</td> 
  </tr>
  <tr>
   <td>Foundation</td> 
   <td>UI-Framework</td> 
   <td>Adobe stellt die Komponenten der Coral UI 2 im Jahr 2019 ein. AEM 6.4 basiert vollständig auf Coral UI 3 (eingeführt mit AEM 6.2). Adobe empfiehlt seinen Kunden und Partnern, die benutzerdefinierte UIs mit Coral 2 erstellt haben, diese in Coral 3 umzuwandeln. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - <a href="/help/sites-developing/dialog-conversion.md">Read more</a>.</td> 
  </tr>
 </tbody>
</table>
