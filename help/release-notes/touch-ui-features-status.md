---
title: Status der Funktionen der Touch-optimierten Benutzeroberfläche
seo-title: Status der Funktionen der Touch-optimierten Benutzeroberfläche
description: Spezifische Versionshinweise zur Touch-optimierten Benutzeroberfläche von Adobe Experience Manager 6.3
seo-description: Spezifische Versionshinweise zur Touch-optimierten Benutzeroberfläche von Adobe Experience Manager 6.3
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
exl-id: e1422581-143b-4fce-976e-e5aa3360e2d0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 65%

---

# Status der Funktionen der Touch-optimierten Benutzeroberfläche {#touch-ui-feature-status}

>[!CAUTION]
>
>Ab Version 6.4 von AEM ist die [Klassische Benutzeroberfläche veraltet](/help/release-notes/deprecated-removed-features.md). Adobe plant keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. Es wird empfohlen, die leistungsstarken neuen Funktionen der Touch-optimierten Benutzeroberfläche zu nutzen.

Seit Einführung von Version 6.0 verfügt AEM über eine neue, Touch-optimierte Benutzeroberfläche, die auf Adobe Marketing Cloud und die allgemeinen Richtlinien für Adobe-Benutzeroberflächen abgestimmt ist. Da sich die Funktionalitäten der beiden Benutzeroberflächen inzwischen nahezu entsprechen, ist dies nun die Standardbenutzeroberfläche von AEM. Die alte, Desktop-artige Benutzeroberfläche wird hingegen als „klassische Benutzeroberfläche“ bezeichnet.

Die meisten Funktionen sind zwar in der Touch-optimierten Benutzeroberfläche vorhanden, allerdings ist die Entwicklung einiger Funktionen noch nicht abgeschlossen. Diese werden dann in künftigen Versionen hinzugefügt.

Die folgende Liste zeigt den aktuellen Status der in AEM 6.4 implementierten Funktionen.

Empfehlungen für Kunden, die auf AEM 6.4 aktualisieren, finden Sie unter [Benutzeroberfläche, Recommendations für Kunden](/help/sites-deploying/ui-recommendations.md).

>[!NOTE]
>
>Beachten Sie, dass auf dieser Seite nur auf die Entsprechungen der Funktionen der klassischen Benutzeroberfläche eingegangen wird.
>
>Zusätzliche spezifische Funktionen der Touch-optimierten Benutzeroberfläche, die nicht in der klassischen Benutzeroberfläche verfügbar sind, werden hier nicht aufgeführt.

>[!NOTE]
>
>Diese Liste erhebt keinen Anspruch auf Vollständigkeit.

## Legende {#legend}

* **Umfassend**: Die Funktion ist in vollem Umfang in der Touch-optimierten Benutzeroberfläche verfügbar.
* **Hauptsächlich**: Die Funktion ist größtenteils in der Touch-optimierten Benutzeroberfläche verfügbar.
* **Fehlt**: Die Funktion ist nicht in der Touch-optimierten Benutzeroberfläche verfügbar. Um die entsprechende Aktion durchzuführen, müssen Sie die klassische Benutzeroberfläche verwenden.
* **Ersetzt**: Diese Funktion wurde durch eine neue Implementierung ersetzt, die anders funktioniert.
* **Entfernt**: Die Funktion ist nicht mehr in der Touch-optimierten Benutzeroberfläche verfügbar und wird nicht ersetzt.

## Funktionsstatus: Sites Admin {#feature-status-sites-admin}

Dies ist eine Liste der Funktionen, die der Site-Administrator der klassischen Benutzeroberfläche ( `/siteadmin`) hat und den Status in der Touch-optimierten Benutzeroberfläche ( `/sites.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion<br /> </strong></td> 
   <td><strong>Status<br /> </strong></td> 
   <td><strong>Kommentar</strong></td> 
  </tr>
  <tr>
   <td>Site-Hierarchie navigieren</td> 
   <td>Fertig stellen<br /> </td> 
   <td>AEM 6.4 wurde eine <a href="/help/sites-authoring/basic-handling.md#content-tree">Inhaltsbaumansicht</a> eingeführt.</td> 
  </tr>
  <tr>
   <td>Workflow starten</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Neue Seite erstellen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Neue Site erstellen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Neuen Launch erstellen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Neue Live Copy erstellen <br /> </td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ordner erstellen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichungsstatus anzeigen</td> 
   <td>Nahezu umfassend</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Suchen</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite kopieren/einfügen (Duplikat)</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite(n) verschieben</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite(n) veröffentlichen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite(n) ohne Replikationsberechtigung veröffentlichen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Später veröffentlichen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Struktur veröffentlichen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichung der Seite(n) rückgängig machen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichung der Seite(n) ohne Replikationsberechtigungen rückgängig machen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichung später rückgängig machen</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Löschen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Sperren/Entsperren</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Eigenschaften anzeigen/bearbeiten</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Berechtigungen für Seite(n) festlegen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Versionsverlauf</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Version wiederherstellen</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Baum wiederherstellen und gelöschte Seiten wiederherstellen</td> 
   <td>Fehlt</td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche.</td> 
  </tr>
  <tr>
   <td>Unterschied zwischen vorheriger und aktueller Version anzeigen<br /> </td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Live Copy-Aktionen (Rollout)</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Sprachkopien anzeigen</td> 
   <td>Fertig stellen</td> 
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
   <td>Verwenden Sie die klassische Benutzeroberfläche. Wird durch andere Implementierung ersetzt.</td> 
  </tr>
  <tr>
   <td>Verweise</td> 
   <td>Nahezu umfassend</td> 
   <td>Die Anzeige eingehender Seitenlinks wird in der AEM-Version von 2019 hinzugefügt.</td> 
  </tr>
 </tbody>
</table>

## Funktionsstatus: Seiten-Editor {#feature-status-page-editor}

Dies ist eine Liste der Funktionen, die der Seiten-Editor der klassischen Benutzeroberfläche ( `/cf#`) aufweist, und der Status in der Touch-optimierten Benutzeroberfläche ( `/editor.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td> 
   <td><strong>Status</strong></td> 
   <td><strong>Kommentar</strong></td> 
  </tr>
  <tr>
   <td>Webseiten bearbeiten</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mobile Webseiten bearbeiten<br /> </td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Per Design-Importtool importierte Inhalte bearbeiten<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>E-Mails bearbeiten</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Apps bearbeiten</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Formulare bearbeiten</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Angebote bearbeiten</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Workflow-Modelle bearbeiten<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>ode: Bearbeiten und Vorschau</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Responsive Vorschau<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modus: Entwurf bearbeiten</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modus: Strukturvorlagen-Modus</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modus: Live Copy-Status<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Anmerkungen hinzufügen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Eigenschaften bearbeiten<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seiten-Rollout</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Workflow starten und anzeigen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Workflow-Paket-Handling</td> 
   <td>Nahezu umfassend</td> 
   <td>Vollständiger Zugriff über die Touch-optimierte Benutzeroberfläche. Mehrere Workflow-Nutzdaten werden weiterhin in der klassischen Benutzeroberfläche angezeigt.<br /> </td> 
  </tr>
  <tr>
   <td>Seite sperren/entsperren</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite veröffentlichen <br /> </td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Veröffentlichen einer Seite rückgängig machen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Seite kopieren</td> 
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
   <td>Verwenden Sie Sites Admin, um die <a href="/help/sites-authoring/author-environment-tools.md#references">detaillierte Verweisliste anzuzeigen</a>.<br /> </td> 
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
   <td>Verwenden Sie Sites Admin, um <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">Versionen wiederherzustellen</a>.</td> 
  </tr>
  <tr>
   <td>Zwischen Launches wechseln</td> 
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
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Berechtigungen festlegen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>ClientContext-Benutzeroberfläche<br /> </td> 
   <td>Ersetzt</td> 
   <td>Verwenden Sie künftig die <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a>-Benutzeroberfläche.</td> 
  </tr>
  <tr>
   <td>Inhaltssuche für die unterschiedlichen Medientypen<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Komponentenliste</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Komponenten kopieren und einfügen<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Komponentenliste in Zwischenablage kopieren</td> 
   <td>Fehlt</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Rückgängig/Wiederholen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Inhalte per Drag-and-Drop in den Komponentenplatzhalter einfügen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Inhalte mit der automatischen Komponentenerstellung direkt per Drag-and-Drop in den ParSys-Platzhalter einfügen<br /> </td> 
   <td>Umfassend</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Funktionsstatus: Text-, Tabellen- und Bild-Editoren {#feature-status-text-table-and-image-editors}

Dies ist eine Liste der Funktionen des Text-, Tabellen- und Bild-Editors der klassischen Benutzeroberfläche sowie des Status in der Touch-optimierten Benutzeroberfläche.

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td> 
   <td><strong>Status </strong></td> 
   <td><strong>Kommentar<br /> </strong></td> 
  </tr>
  <tr>
   <td>Rich-Text-Editor</td> 
   <td>Fertig stellen</td> 
   <td>Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus.</td> 
  </tr>
  <tr>
   <td>RTE-Plug-ins aktivieren/deaktivieren</td> 
   <td>Fertig stellen<br /> </td> 
   <td>Kann mit dem <a href="/help/sites-authoring/templates.md">Vorlagen-Editor</a> durchgeführt werden.</td> 
  </tr>
  <tr>
   <td>RTE für Nur-Text verwenden</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Links und Anker</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Zeichenzuordnung</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Kopieren/Einfügen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Aus Microsoft Word einfügen<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Suchen und Ersetzen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Textformate (fett, ...)</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Hochgestellt</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Blocksatz</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Listen (Aufzählungszeichen/Zahlen)</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Absatzformat</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Textstile</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Quell-Editor (HTML bearbeiten)<br /> </td> 
   <td>Fertig stellen<br /> </td> 
   <td>Nur im Dialogfeld und im Vollbildmodus verfügbar.<br /> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Rechtschreibprüfung</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Tabelle (eingebetteter Tabellen-Editor)</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Rückgängig/Wiederholen<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE-Plug-in: Inline-Bilder zulassen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Tabelleneditor</td> 
   <td>Fertig stellen</td> 
   <td>Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus.<br /> </td> 
  </tr>
  <tr>
   <td>Bild per Drag &amp; Drop in Tabellenzelle verschieben<br /> </td> 
   <td>Fertig stellen</td> 
   <td>In-line-Funktion</td> 
  </tr>
  <tr>
   <td>Bildeditor<br /> </td> 
   <td>Fertig stellen</td> 
   <td>Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus.<br /> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-ins aktivieren/deaktivieren</td> 
   <td>Fertig stellen</td> 
   <td>Im <a href="/help/sites-authoring/templates.md">Vorlagen-Editor</a> gibt es jetzt eine Benutzeroberfläche.</td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Zuschneiden</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Spiegeln</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Rückgängig/Wiederherstellen</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Imagemap</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Drehen</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE-Plug-in: Zoom</td> 
   <td>Fertig stellen<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Funktionsstatus: Werkzeuge {#feature-status-tools}

Dies ist eine Liste der verschiedenen Werkzeuge der klassischen Benutzeroberfläche sowie deren Status in der Touch-optimierten Benutzeroberfläche.

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
   <td>Workflow-Posteingang<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Workflow zur Konfiguration der Seitenvorlage (<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>Fehlt<br /> </td> 
   <td>Verwenden Sie die klassische Benutzeroberfläche.</td> 
  </tr>
  <tr>
   <td>Tagging der Admin-Benutzeroberfläche<br /> </td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>MSM/Blueprint Control Center</td> 
   <td>Fertig stellen</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Blueprint-Manager-Benutzeroberfläche</td> 
   <td>Fertig stellen</td> 
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
   <td>Verwenden Sie für erweiterte Berechtigungsbearbeitung die klassische Benutzeroberfläche.<br /> </td> 
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
