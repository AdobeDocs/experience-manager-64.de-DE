---
title: Status der Funktionen der Touch-optimierten Benutzeroberfläche
seo-title: Touch UI Feature Status
description: Spezifische Versionshinweise zur Touch-optimierten Benutzeroberfläche von Adobe Experience Manager 6.3.
seo-description: Release notes specific to Adobe Experience Manager 6.3 Touch UI.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
exl-id: e1422581-143b-4fce-976e-e5aa3360e2d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 58%

---

# Status der Funktionen der Touch-optimierten Benutzeroberfläche {#touch-ui-feature-status}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!CAUTION]
>
>Mit Version 6.4 von AEM [Die klassische Benutzeroberfläche ist veraltet](/help/release-notes/deprecated-removed-features.md). Adobe plant keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. Es wird empfohlen, die leistungsstarken neuen Funktionen der Touch-optimierten Benutzeroberfläche zu nutzen.

Ab Version 6.0 führte AEM eine neue Benutzeroberfläche ein, die als &quot;Touch-optimierte Benutzeroberfläche&quot;bezeichnet wird (auch als &quot;Touch-optimierte Benutzeroberfläche&quot;bezeichnet), die an die Adobe Marketing Cloud und die allgemeinen Richtlinien für die Benutzeroberfläche der Adobe angepasst ist. Da nahezu die Funktionsparität erreicht wurde, ist dies zur Standard-Benutzeroberfläche in AEM geworden, mit der veralteten, Desktop-orientierten Benutzeroberfläche, die als &quot;klassische Benutzeroberfläche&quot;bezeichnet wird.

Die meisten Funktionen sind zwar in der Touch-optimierten Benutzeroberfläche vorhanden, allerdings ist die Entwicklung einiger Funktionen noch nicht abgeschlossen. Diese werden dann in künftigen Versionen hinzugefügt.

In der folgenden Liste ist der aktuelle Status der in AEM 6.4 verfügbaren Funktionen aufgeführt.

Empfehlungen für Kunden, die auf AEM 6.4 aktualisieren, finden Sie unter [Recommendations für Kunden](/help/sites-deploying/ui-recommendations.md) für Details.

>[!NOTE]
>
>Beachten Sie, dass auf dieser Seite nur die Funktionsparität mit der klassischen Benutzeroberfläche behandelt wird.
>
>Funktionen, die der Touch-optimierten Benutzeroberfläche hinzugefügt wurden und die nicht in der klassischen Benutzeroberfläche vorhanden sind, werden nicht aufgeführt.

>[!NOTE]
>
>Diese Liste ist vollständig, sollte jedoch nicht als vollständig betrachtet werden.

## Legende {#legend}

* **Fertig**: Die Funktion ist in der Touch-optimierten Benutzeroberfläche vollständig verfügbar
* **Nahezu umfassend**: Die Funktion ist nahezu umfassend in der Touch-optimierten Benutzeroberfläche verfügbar.
* **Fehlt**: Die Funktion ist in der Touch-optimierten Benutzeroberfläche nicht vorhanden. Für diese Aktion muss die klassische Benutzeroberfläche verwendet werden.
* **Ersetzt**: Die Funktion wurde durch eine neue Implementierung ersetzt, die anders funktioniert.
* **Entfernt**: Die Funktion ist nicht mehr in der Touch-optimierten Benutzeroberfläche verfügbar und wird nicht ersetzt.

## Funktionsstatus: Sites Admin {#feature-status-sites-admin}

Dies ist eine Liste der Sites Admin-Funktionen der klassischen Benutzeroberfläche (`/siteadmin` ) sowie deren Status in der Touch-optimierten Benutzeroberfläche ( `/sites.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion<br /> </strong></td> 
   <td><strong>Status<br /> </strong></td> 
   <td><strong>Kommentar</strong></td> 
  </tr>
  <tr>
   <td>Site-Hierarchie navigieren</td> 
   <td>Umfassend<br /> </td> 
   <td>Mit AEM 6.4 wurde eine <a href="/help/sites-authoring/basic-handling.md#content-tree">Inhalts-Baumstrukturbaumansicht</a> eingeführt.</td> 
  </tr>
  <tr>
   <td>Workflow starten</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Neue Seite erstellen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Neue Site erstellen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Neuen Launch erstellen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Neue Live Copy erstellen <br /> </td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ordner erstellen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichungsstatus anzeigen</td> 
   <td>Nahezu umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Suchen</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite kopieren/einfügen (Duplizieren)</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite(n) verschieben</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite(n) veröffentlichen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite(n) ohne Replikationsrechte veröffentlichen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Später veröffentlichen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichungsstruktur</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichung von Seiten rückgängig machen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichung von Seiten ohne Replikationsrechte rückgängig machen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichung später rückgängig machen</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Löschen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Sperren/Entsperren</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Eigenschaften anzeigen/bearbeiten</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Festlegen von Berechtigungen für Seiten</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Versionsverlauf</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Version wiederherstellen</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Baum wiederherstellen und gelöschte Seiten wiederherstellen</td> 
   <td>Fehlt</td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche.</td> 
  </tr>
  <tr>
   <td>Unterschied zwischen vorheriger und aktueller Version anzeigen<br /> </td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Live Copy-Aktionen (Roll-out)</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Siehe Sprachkopien</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Suchen und Ersetzen</td> 
   <td>Fehlt<br /> </td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche.</td> 
  </tr>
  <tr>
   <td>Benachrichtigungs-Posteingang (JCR-Ereignisse)</td> 
   <td>Fehlt</td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche. Wird durch eine andere Implementierung ersetzt.</td> 
  </tr>
  <tr>
   <td>Verweise</td> 
   <td>Nahezu umfassend</td> 
   <td>Die Anzeige eingehender Seitenlinks wird in der AEM-Version von 2019 hinzugefügt.</td> 
  </tr>
 </tbody>
</table>

## Funktionsstatus: Seiten-Editor {#feature-status-page-editor}

Dies ist eine Liste der Seiten-Editor-Funktionen der klassischen Benutzeroberfläche (`/cf#`) sowie deren Status in der Touch-optimierten Benutzeroberfläche ( `/editor.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td> 
   <td><strong>Status</strong></td> 
   <td><strong>Kommentar</strong></td> 
  </tr>
  <tr>
   <td>Webseiten bearbeiten</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mobile Webseiten bearbeiten<br /> </td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Per Design-Import-Tool importierte Inhalte bearbeiten<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>E-Mails bearbeiten</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mobile Apps bearbeiten</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Formulare bearbeiten</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Angebote bearbeiten</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Workflow-Modelle bearbeiten<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>ode: Bearbeiten und Vorschau</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Responsive Vorschau<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modus: Design bearbeiten</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modus: Strukturvorlage</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modus: Live Copy-Status<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Hinzufügen von Anmerkungen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Bearbeiten von Eigenschaften<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Rollout-Seite</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Workflow starten und anzeigen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Umgang mit Workflow-Paketen</td> 
   <td>Nahezu umfassend</td> 
   <td>Vollständiger Zugriff über die Touch-optimierte Benutzeroberfläche. In der klassischen Benutzeroberfläche werden weiterhin mehrere Workflow-Payloads angezeigt.<br /> </td> 
  </tr>
  <tr>
   <td>Seite sperren/entsperren</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite veröffentlichen <br /> </td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichen einer Seite aufheben</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Kopieren einer Seite</td> 
   <td>Entfernt<br /> </td> 
   <td>Verwenden Sie Sites Admin, um <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">Seiten zu kopieren</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Seite verschieben</td> 
   <td>Entfernt</td> 
   <td>Verwenden Sie Sites Admin, um <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">Seiten zu verschieben</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Seite löschen</td> 
   <td>Entfernt</td> 
   <td>Verwenden Sie Sites Admin, um <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">Seiten zu löschen</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Verweise einblenden</td> 
   <td>Entfernt</td> 
   <td>Verwenden Sie Sites Admin, um <a href="/help/sites-authoring/author-environment-tools.md#references">siehe detaillierte Referenzliste</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Auditprotokoll</td> 
   <td>Entfernt</td> 
   <td>Verwenden Sie Sites Admin und <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">öffnen Sie die Aktivitätsschiene</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Version erstellen</td> 
   <td>Entfernt</td> 
   <td>Verwenden Sie Sites Admin, um <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">neue Versionen zu erstellen</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Version wiederherstellen</td> 
   <td>Entfernt</td> 
   <td>Verwenden Sie Sites Admin, um <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">Versionen wiederherstellen</a>.</td> 
  </tr>
  <tr>
   <td>Launches wechseln</td> 
   <td>Entfernt</td> 
   <td>Verwenden Sie Sites Admin, um <a href="/help/sites-authoring/launches-promoting.md">zwischen Launches zu wechseln</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Seite übersetzen</td> 
   <td>Entfernt</td> 
   <td>Verwenden Sie Sites Admin, um <a href="/help/sites-administering/tc-manage.md">Seiten zu Übersetzungsprojekten hinzufügen</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Timewarp (Zeit auswählen und Site in vorherigem Zustand durchsuchen)<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Berechtigungen festlegen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>ClientContext-Benutzeroberfläche<br /> </td> 
   <td>Ersetzt</td> 
   <td>Verwenden Sie die <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> Benutzeroberfläche in Zukunft.</td> 
  </tr>
  <tr>
   <td>Inhaltssuche für die unterschiedlichen Medientypen<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Komponentenliste</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Komponenten kopieren und einfügen<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Liste der Komponenten in der Zwischenablage</td> 
   <td>Fehlt</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Rückgängig/Wiederholen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Inhalt in Komponenten-Platzhalter ziehen und ablegen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ziehen Sie Inhalte direkt in den ParSys-Platzhalter mit automatischer Komponentenerstellung.<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Funktionsstatus: Text-, Tabellen- und Bild-Editoren {#feature-status-text-table-and-image-editors}

Dies ist eine Liste der Funktionen der Text-, Tabellen- und Bild-Editoren der klassischen Benutzeroberfläche sowie deren Status in der Touch-optimierten Benutzeroberfläche.

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td> 
   <td><strong>Status </strong></td> 
   <td><strong>Kommentar<br /> </strong></td> 
  </tr>
  <tr>
   <td>Rich-Text-Editor</td> 
   <td>Umfassend</td> 
   <td>Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus.</td> 
  </tr>
  <tr>
   <td>RTE-Plug-ins aktivieren/deaktivieren</td> 
   <td>Umfassend<br /> </td> 
   <td>Kann mithilfe des <a href="/help/sites-authoring/templates.md">Vorlagen-Editors</a> erledigt werden.</td> 
  </tr>
  <tr>
   <td>RTE für Nur-Text verwenden</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Links und Anker</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Zeichenzuordnung</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Kopieren/Einfügen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Aus Microsoft Word einfügen<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Suchen und Ersetzen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Textformate (fett, ...)</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Hochgestellt</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Blocksatz</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Listen (Aufzählungszeichen/Zahlen)</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Absatzformat</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Textstile</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Quell-Editor (HTML bearbeiten)<br /> </td> 
   <td>Umfassend<br /> </td> 
   <td>Nur im Dialogfeld und im Vollbildmodus verfügbar.<br /> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Rechtschreibprüfung</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Tabelle (eingebetteter Tabellen-Editor)</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Rückgängig/Wiederherstellen<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Inline-Bilder zulassen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Tabelleneditor</td> 
   <td>Umfassend</td> 
   <td>Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus.<br /> </td> 
  </tr>
  <tr>
   <td>Bild in Tabellenzelle ziehen und ablegen<br /> </td> 
   <td>Umfassend</td> 
   <td>In-line-Funktion</td> 
  </tr>
  <tr>
   <td>Bildeditor<br /> </td> 
   <td>Umfassend</td> 
   <td>Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus.<br /> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-ins aktivieren/deaktivieren</td> 
   <td>Umfassend</td> 
   <td>Es gibt jetzt eine Benutzeroberfläche in der <a href="/help/sites-authoring/templates.md">Vorlagen-Editor</a>.</td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Zuschneiden</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Spiegeln</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Rückgängig/Wiederherstellen</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Imagemap</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Drehen</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Zoomen</td> 
   <td>Umfassend<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Funktionsstatus: Werkzeuge {#feature-status-tools}

Dies ist eine Liste der verschiedenen Tools, die die klassische Benutzeroberfläche hat, und des Status in der Touch-optimierten Benutzeroberfläche.

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion<br /> </strong></td> 
   <td><strong>Status<br /> </strong></td> 
   <td><strong>Kommentar</strong></td> 
  </tr>
  <tr>
   <td>Aufgabenverwaltung</td> 
   <td>Ersetzt</td> 
   <td>6.0 eingeführt <a href="/help/sites-authoring/projects.md">Projekte und Aufgaben</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Posteingangs-Workflow<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Konfiguration der Workflow-zu-Seite-Vorlage (<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>Fehlt<br /> </td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche.</td> 
  </tr>
  <tr>
   <td>Tagging der Admin-Benutzeroberfläche<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>MSM/Blueprint-Steuerungszentrale</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Blueprint-Manager-Benutzeroberfläche</td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Benutzeroberfläche für Rollout-Konfiguration</td> 
   <td>Fehlt</td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche.</td> 
  </tr>
  <tr>
   <td>Benutzeroberfläche für Benutzer, Gruppen und Berechtigungen<br /> </td> 
   <td>Nahezu umfassend<br /> </td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche für die erweiterte Bearbeitung von Berechtigungen.<br /> </td> 
  </tr>
  <tr>
   <td>Versionen bereinigen (<code>/etc/versioning/purge.html</code>)</td> 
   <td>Fehlt</td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche.</td> 
  </tr>
  <tr>
   <td>Prüfer für externe Links (<code>/etc/linkchecker.html</code>)</td> 
   <td>Fehlt</td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche.<br /> </td> 
  </tr>
  <tr>
   <td>Bulk Editor (<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>Fehlt<br /> </td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche.</td> 
  </tr>
 </tbody>
</table>
