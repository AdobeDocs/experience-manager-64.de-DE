---
title: Debugging von HTML5-Formularen
seo-title: Debugging HTML5 forms
description: Das Dokument listet Schritte zur Fehlerbehebung bei verschiedenen bekannten Problemen auf.
seo-description: The document list steps to troubleshoot various known issues.
uuid: df1835aa-6033-4ecb-97c8-4c3b7b96b943
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 5260d981-da40-40ab-834e-88e091840813
feature: Mobile Forms
exl-id: 8c75d395-1816-4b5a-869c-ec61069a54f6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 44%

---

# Debugging von HTML5-Formularen {#debugging-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Dieses Dokument enthält verschiedene Fehlerbehebungsszenarien. Für jedes Szenario werden einige Schritte bereitgestellt, um das Problem zu beheben. Führen Sie diese Schritte aus und, falls das Problem weiterhin besteht, konfigurieren Sie den Logger, um Protokolle auf Fehler/Warnungen abzurufen und zu überprüfen. Weitere Informationen zu Protokollen für HTML5 finden Sie unter [Generieren von Protokollen für HTML5-Formulare](/help/forms/using/enable-logs.md).

## Problem: Wenn ich das Formular rendere, erscheint die Ausnahmeseite „org.apache.sling.api.SlingException“. {#problem-when-rendering-the-form-i-see-org-apache-sling-api-slingexception-exception-page}

Suchen Sie in den Ausnahmedetails nach dem Begriff **„caused by“**.

Die wahrscheinliche Ursache ist, dass mindestens ein Parameter in der URL falsch ist.

Überprüfen Sie die folgenden Parameter:


<table> 
 <tbody> 
  <tr> 
   <td><strong>Parameter</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>template</td> 
   <td>Dateiname der Vorlage</td> 
  </tr> 
  <tr> 
   <td>contentRoot</td> 
   <td>Der Pfad, in dem sich Vorlage und zugehörige Ressourcen befinden</td> 
  </tr> 
  <tr> 
   <td>dataRef</td> 
   <td>Absoluter Pfad der Datendatei, die mit der Vorlage zusammengeführt werden soll.<br /> Hinweis: Der Pfad definiert den absoluten Pfad der Datendatei.</td> 
  </tr> 
  <tr> 
   <td>data</td> 
   <td>UTF-8-kodierte Datenbytes, die mit der Vorlage zusammengeführt werden sollen.</td> 
  </tr> 
 </tbody> 
</table>

## Problem: Formular kann nicht gerendert werden (eine Fehlermeldung wird angezeigt) {#problem-unable-to-render-a-form-an-error-message-is-displayed}

1. Stellen Sie sicher, dass die angegebenen Parameter korrekt sind. Detaillierte Informationen zu Parametern finden Sie unter [Render-Parameter](#problem-when-rendering-the-form-i-see-org-apache-sling-api-slingexception-exception-page).
1. Melden Sie sich bei CRX Package Manager an (unter http://&lt;server>:&lt;port>/crx/packmgr/index.jsp) und überprüfen Sie, ob die folgenden Pakete ordnungsgemäß installiert sind:

   * adobe-lc-forms-content-pkg-&lt;version>.zip
   * adobe-lc-forms-runtime-pkg-&lt;version>.zip

1. Melden Sie sich bei CQ Web Console (Felix Console) an unter http://&lt;server>:&lt;port>/system/console/bundles.

   Stellen Sie sicher, dass der Status der folgenden Pakete „active“ lautet:

   * scala-lang.bundle [osgi]

   (com.adobe.livecyclescala-lang.bundle)

   * Adobe XFA Forms Renderer

   (com.adobe.livecycle.adobe-lc-forms-core)

   * Adobe XFA Forms LC Connector

   (com.adobe.livecycle.adobe-lc-forms-lc-connector)

## Problem: Formular wird ohne Stile gerendert {#problem-form-renders-without-styles}

1. Öffnen Sie im Browser **Developer Tools**. Vergewissern Sie sich, dass „profile.css“ verfügbar ist.
1. Wenn die Datei „profile.css“ nicht verfügbar ist, melden Sie sich unter http://&lt;Server>:&lt;Port>/crx/de bei CRX DE an.
1. Navigieren Sie in der Ordnerhierarchie auf der linken Seite zu /etc/clientlibs/fd/xfaforms/. Öffnen Sie die in den Ordnern aufgelisteten css.txt-Dateien.

   * Profil
   * runtime
   * scrollnav
   * toolbar
   * xfalib

1. Vergewissern Sie sich, dass die in der Datei css.txt erwähnten Dateien in CRX DE Lite unter /libs/fd/xfaforms/clientlibs/xfalib/css vorhanden sind.

   ```css
   #base=css
   application.css
   dialog.css
   datepicker.css
   scribble.css
   listboxwidget.css
   ```

1. Wenn die genannten Dateien nicht verfügbar sind, installieren Sie adobe-lc-forms-runtime-pkg-&lt;version>.zip-Paket erneut.

### Problem: Unerwarteter Fehler gefunden {#problem-unexpected-error-encountered}

1. Fügen Sie in die Formular-URL den Abfrageparameter „debugClientLibs“ ein und legen Sie seinen Wert auf „true“ fest (z. B. http://&lt;Server>:&lt;Port>/content/xfaforms/profiles/test.html?contentRoot=&lt;eine Pfadangabe>&amp;template=&lt;Name der xdp-Datei>&amp;log=1-a9-b9-c9&amp;debugClientLibs=true)
1. Navigieren Sie im Desktop-Browser wie Chrome zu &quot;Developer Tools&quot;-> &quot;Console&quot;.
1. Öffnen Sie die Protokolle, um den Fehlertyp zu identifizieren. Detaillierte Informationen zu Protokollen finden Sie unter [Protokolle für HTML5-Formulare](/help/forms/using/enable-logs.md).
1. Navigieren Sie zu Entwicklertools > Konsole . Verwenden Sie die Stapelablaufverfolgung, um den Code zu finden, der den Fehler verursacht. Debuggen Sie den Fehler, um das Problem zu beheben.

   >[!NOTE]
   >
   >Wenn Skriptfehler vorliegt, überprüfen Sie, ob das gleiche Problem auch bei der PDF-Wiedergabe des Formulars auftritt. Falls ja, besteht ein Problem mit der Skriptlogik des Formulars.

## Problem: Formular kann nicht gesendet werden {#problem-unable-to-submit-the-form}

1. Stellen Sie sicher, dass Sie über Zugriffsberechtigungen für den AEM-Server verfügen und mit dem Server verbunden sind.
1. Überprüfen Sie, ob der Parameter „submitUrl“ korrekt ist.
1. Aktivieren Sie clientseitige Protokolle, wie unter [Protokolle für HTML5-Forms](/help/forms/using/enable-logs.md) beschrieben, und verwenden Sie als Debug-Option **1-a5-b5-c5**. Rendern Sie das Formular erneut und klicken Sie auf „Senden“. Öffnen Sie die Debug-Console im Browser und prüfen Sie, ob Fehler vorliegen.
1. Suchen Sie die Serverprotokolle, die erwähnt werden unter [Protokolle für die HTML5-Formulare](/help/forms/using/enable-logs.md). Überprüfen Sie, ob in den Serverprotokollen während der Übermittlung ein Fehler aufgetreten ist.

## Problem: Lokalisierte Fehlermeldungen werden nicht angezeigt {#problem-localized-error-messages-do-not-display}

1. Formular mit zusätzlichem Abfrageparameter rendern **debugClientLibs=true** im Desktop-Browser, navigieren Sie zu &quot;Developer Tools&quot;-> &quot;Ressourcen&quot;und suchen Sie nach der Datei &quot;I18N.css&quot;.
1. Wenn die Datei nicht verfügbar ist, melden Sie sich unter http://&lt;server>:&lt;port>/crx/de bei CRX DE an.
1. Navigieren Sie in der Ordnerhierarchie auf der linken Seite zu /libs/fd/xfaforms/clientlibs/I18N und stellen Sie sicher, dass die folgenden Dateien und Ordner vorhanden sind:

   * Namespace.js
   * LogMessages.js
   * Ordner für Sprachen

1. Wenn eine der oben genannten Dateien oder Ordner nicht vorhanden ist, installieren Sie die **adobe-lc-forms-runtime-pkg-&lt;version>.zip** Paket erneut.
1. Navigieren Sie zu dem Ordner, der denselben Namen wie das Gebietsschema hat, und überprüfen Sie den Inhalt. Der Ordner muss die folgenden Dateien enthalten:

   * I18N.js
   * js.txt

1. Überprüfen Sie den Inhalt von js.txt und stellen Sie sicher, dass die folgenden Einträge vorhanden sind.

   ```
   ../Namespace.js
   I18N.js
   ../LogMessages.js
   ```

## Problem: Bild wird nicht angezeigt {#problem-image-not-showing-up}

1. Stellen Sie sicher, dass die Bild-URL korrekt ist.
1. Überprüfen Sie, ob der Bildtyp von Ihrem Browser unterstützt wird.
1. Suchen Sie in den Ausnahmedetails nach dem Begriff **„caused by“**.

   Die wahrscheinliche Ursache ist, dass mindestens ein Parameter in der URL falsch ist.

   Überprüfen Sie die folgenden Parameter:

Schritttext

<table> 
 <tbody> 
  <tr> 
   <td><strong>Parameter</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>template</td> 
   <td>Dateiname der Vorlage</td> 
  </tr> 
  <tr> 
   <td>contentRoot</td> 
   <td>Der Pfad, in dem sich Vorlage und zugehörige Ressourcen befinden</td> 
  </tr> 
  <tr> 
   <td>dataRef</td> 
   <td>Absoluter Pfad der Datendatei, die mit der Vorlage zusammengeführt werden soll.<br /> Hinweis: Der Pfad definiert den absoluten Pfad der Datendatei.</td> 
  </tr> 
  <tr> 
   <td>data</td> 
   <td>UTF-8-kodierte Datenbytes, die mit der Vorlage zusammengeführt werden sollen.</td> 
  </tr> 
 </tbody> 
</table>

1. Navigieren Sie im Desktop-Browser zu &quot;Entwicklertools&quot;-> &quot;Ressourcen&quot;.

   Überprüfen Sie auf der linken Seite in Frames , ob dieses Bild angezeigt wird.
