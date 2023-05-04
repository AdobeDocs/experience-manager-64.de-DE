---
title: Die Tools-Konsolen
description: Erfahren Sie mehr über die verschiedenen Tools-Konsolen in Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
exl-id: 7566e1bc-8571-4b3c-b420-4324026bd4dd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 26%

---

# Die Tools-Konsolen {#tools-consoles}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die **Tools-Konsolen** bieten Zugriff auf viele spezialisierte Tools, mit denen Sie Ihre Websites, digitalen Assets und andere Bereiche Ihres Content-Repositorys verwalten können. Derzeit gibt es zwei Varianten der **Instrumente** abhängig von der verwendeten Benutzeroberfläche:

* [Tools – klassische Benutzeroberfläche](#tools-classic-ui)
* [Tools – Touch-optimierte Benutzeroberfläche](#tools-touch-optimized-ui)

## Tools – klassische Benutzeroberfläche {#tools-classic-ui}

<table> 
 <tbody> 
  <tr> 
   <th>Seite oder Ordner</th> 
   <th> </th> 
   <th>Zweck</th> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM Control Center</a></td> 
   <td> </td> 
   <td>Zentrale Stelle für die Verwaltung mehrerer Sites.</td> 
  </tr> 
  <tr> 
   <td>ClientContext-Konfigurationen<br /> </td> 
   <td> </td> 
   <td>Die <a href="/help/sites-developing/client-context.md">ClientContext</a> stellt eine dynamisch zusammengestellte Sammlung von Benutzerdaten dar. Die standardmäßigen und Marketing-Cloud-Konfigurationen finden Sie hier.<br /> </td> 
  </tr> 
  <tr> 
   <td>Cloud Services-Konfigurationen<br /> </td> 
   <td> </td> 
   <td>Lagerkonfigurationen für <a href="/help/sites-administering/marketing-cloud.md">Integration mit Adobe Marketing Cloud</a>.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/ecommerce.md">Commerce </a></td> 
   <td> </td> 
   <td>Ermöglicht den Zugriff auf Importeure und verschiedene Produktdaten.</td> 
  </tr> 
  <tr> 
   <td>DAM - Digital Rights Management<br /> </td> 
   <td> </td> 
   <td>Bietet Zugriff auf Informationen und Lizenzen zu digitalen Rechten.</td> 
  </tr> 
  <tr> 
   <td>DAM - Konsistenzprüfer<br /> </td> 
   <td> </td> 
   <td>Vergleich <code>/var/dam</code> und <code>/content/dam</code> und Kontrollen<br /> Inkonsistenzen. Alle aufgeführten Dateien/Ordner können dann synchronisiert oder gelöscht werden. Knotentypen für den Ordnervergleich können in der Web-Konsole konfiguriert werden.</td> 
  </tr> 
  <tr> 
   <td>DAM - Adobe InDesign<br /> </td> 
   <td> </td> 
   <td>Skripte zur Verwendung in Verbindung mit Adobe InDesign.</td> 
  </tr> 
  <tr> 
   <td>DAM - Videoprofile<br /> </td> 
   <td> </td> 
   <td>Konfigurierbare Profile für ffmpeg-Transkodierungen.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/dashboards.md">Dashboards</a></td> 
   <td> </td> 
   <td>Ermöglicht die Erstellung von Reporting-Dashboards. Diese bieten eine anpassbare Möglichkeit zur Festlegung von Seiten, die konsolidierte Daten anzeigen.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-developing/designer.md">Designs</a></td> 
   <td> </td> 
   <td>Enthält die Liste der definierten Designs, einschließlich der zu verwendenden Grafiken und CSS-Dateien.</td> 
  </tr> 
  <tr> 
   <td>Benutzerdefinierte Dokumentation</td> 
   <td> </td> 
   <td>Wird beim Erweitern der Dokumentation und der Onlinehilfe verwendet.</td> 
  </tr> 
  <tr> 
   <td>Formularübermittlungen</td> 
   <td> </td> 
   <td>Enthält die Liste der eingegangenen Formularübermittlungen.</td> 
  </tr> 
  <tr> 
   <td>Importeure - <a href="/help/sites-administering/bulk-editor.md">Bulk Editor</a></td> 
   <td> </td> 
   <td>Ermöglicht die Suche nach Elementen und deren Massenbearbeitung. Sie können auch Inhalte (stapelweise) exportieren und in das Repository importieren.</td> 
  </tr>
  <tr> 
   <td>Importer - Feed Importer</td> 
   <td> </td> 
   <td><p>Der Feed Importer ist ein Framework, mit dem Inhalte wiederholt aus externen Quellen in Ihr Repository importiert werden können. Der Feed-Importtool hat die Idee, eine Remote-Ressource in einem bestimmten Intervall abzurufen, sie zu analysieren und Knoten im Inhalts-Repository zu erstellen, die den Inhalt der Remote-Ressource darstellen.</p> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/external-link-checker.md">Externer Linkprüfer</a></td> 
   <td> </td> 
   <td>Scannt alle Inhaltsseiten in Ihrer AEM-Instanz und prüft alle externen Links. Eine Liste gültiger und ungültiger Links wird angezeigt.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/mobile.md">Mobilgerät</a></td> 
   <td> </td> 
   <td>Hilft Ihnen beim Erstellen von Websites für Mobilgeräte.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM</a></td> 
   <td> </td> 
   <td>Verarbeitet mehrsprachige und multinationale Inhalte und hilft Ihnen, zentralisiertes Branding mit lokalisierten Inhalten in Einklang zu bringen.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/notification.md">Benachrichtigung</a></td> 
   <td> </td> 
   <td>Benachrichtigungsvorlagen.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/package-manager.md">Pakete</a></td> 
   <td> </td> 
   <td>Ein alternativer Link zum Package Manager, der die Pakete anzeigt, die für AEM WCM geladen wurden. Ähnlich den Informationen, die im Paketmanager von CRX angezeigt werden.</td> 
  </tr> 
  <tr> 
   <td>Replikation - <a href="/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents">Replikationsagenten</a></td> 
   <td> </td> 
   <td>Wird verwendet, um Daten vom Autor zur Veröffentlichung zu replizieren, wenn Seiten veröffentlicht werden, oder mit Rückwärtsreplikation, um Benutzerkommentare aus der Veröffentlichungsumgebung an den Autor zurückzugeben.</td> 
  </tr> 
  <tr> 
   <td>Importeure - <a href="/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree">Baum aktivieren</a></td> 
   <td> </td> 
   <td>Auf der Registerkarte Websites können Sie die einzelnen Seiten aktivieren. Wenn Sie eine beträchtliche Anzahl von Inhaltsseiten eingegeben oder aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es einfacher sein, den gesamten Baum in einer Aktion zu aktivieren. Sie können auch einen Probelauf durchführen, um eine Aktivierung zu emulieren und hervorzuheben, welche Seiten aktiviert werden.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/reporting.md">Berichte</a></td> 
   <td> </td> 
   <td>AEM bietet eine Reihe benutzerdefinierter Berichte, mit denen Sie benutzerspezifische Berichte erstellen und/oder eigene Berichte entwickeln können.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/scaffolding.md">Strukturvorlage für Standardseite</a></td> 
   <td> </td> 
   <td>Mit Strukturvorlage können Sie ein Formular (eine Grundlage) mit Feldern erstellen, die die gewünschte Struktur für Ihre Seiten widerspiegeln. Mithilfe dieses Formulars können Sie dann einfach Seiten erstellen, die auf dieser Struktur basieren.</td> 
  </tr> 
  <tr> 
   <td>Sicherheit - <a href="/help/sites-administering/notification.md">Self-Service-Konfiguration </a> </td> 
   <td> </td> 
   <td>Ermöglicht die Konfiguration der E-Mails, die Benutzer automatisch erhalten, wenn sie ein Konto erstellen oder ein Kennwort zurücksetzen, sowie die Bestätigung eines zurückgesetzten Kennworts.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/campaign-segmentation.md">Segmentierung</a></td> 
   <td> </td> 
   <td>Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Diese Ziele zu verstehen und die Erwartungen zu erfüllen, ist ein wichtiger Erfolgsfaktor für Online-Marketing. Die Segmentierung hilft dabei, die Details eines Besuchers zu analysieren und zu charakterisieren.<br /> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/communities/working-with-srp.md">socialconfig</a></td> 
   <td> </td> 
   <td>Standard-SRP-Konfiguration. Siehe <a href="/help/communities/srp-config.md">Speicherkonfiguration</a> Konsole.</td> 
  </tr> 
  <tr> 
   <td>taskmanagement</td> 
   <td> </td> 
   <td>Keine aktive Funktion im Zusammenhang mit diesem Eintrag.</td> 
  </tr> 
  <tr> 
   <td>Mandanten</td> 
   <td> </td> 
   <td>Keine aktive Funktion im Zusammenhang mit diesem Eintrag.</td> 
  </tr> 
  <tr> 
   <td>Versionierung - <a href="/help/sites-deploying/version-purging.md">Versionen bereinigen</a></td> 
   <td> </td> 
   <td>Ermöglicht die Bereinigung der Seitenversionen nach Bedarf.</td> 
  </tr> 
  <tr> 
   <td>Virtuelle Repositorys</td> 
   <td> </td> 
   <td>Sie können ein virtuelles Repository mithilfe der Workspace-Bereitstellungsfunktion einrichten, um JCR-fähige Inhaltsanwendungen mit vereinfachtem Zugriff auf die JCR-Inhaltsinfrastruktur basierend auf CRX und den JCR-Connectoren bereitzustellen.</td> 
  </tr> 
  <tr> 
   <td>Schlagwörter</td> 
   <td> </td> 
   <td>Veraltet. Siehe <a href="/help/communities/moderate-ugc.md#watchwords">Moderieren von Community-Inhalten</a></td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/workflows.md">Workflow</a></td> 
   <td> </td> 
   <td>Workflows steuern eine Reihe von Aktionen auf Seiten oder digitalen Assets, die alle redaktionellen Prozesse unterstützen.</td> 
  </tr> 
 </tbody> 
</table>

## Tools – Touch-optimierte Benutzeroberfläche {#tools-touch-optimized-ui}

<table> 
 <tbody> 
  <tr> 
   <th>Abschnitt</th> 
   <th>Option</th> 
   <th>Zweck</th> 
  </tr> 
  <tr> 
   <td>Authoring</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-classic-ui-authoring/classic-personalization-campaigns.md">Kampagnen</a></td> 
   <td>Verwalten Sie Ihre Marketingkampagnen.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/launches.md">Launches</a></td> 
   <td>Marketing-Launches verwalten</td> 
  </tr> 
  <tr> 
   <td>Aufgaben</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/task-content.md">Posteingang</a></td> 
   <td>Verwalten Sie Ihre Posteingangselemente.</td> 
  </tr> 
  <tr> 
   <td>Betrieb</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/security.md">Benutzer und Gruppen </a></td> 
   <td>Benutzer und Gruppen verwalten.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/tags.md">Tag-Management</a></td> 
   <td>Tags und zugehörige Namespaces organisieren.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="https://helpx.adobe.com/cloud-manager/using/using-cloud-manager.html">Cloud Services</a></td> 
   <td>Mit Adobe Marketing Cloud verbinden.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/workflows.md">Workflows</a></td> 
   <td>Workflows modellieren und verwalten.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/replication.md">Replikation</a></td> 
   <td>Erstellen und verwalten Sie mehrere Websites.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/reporting.md">Berichte</a></td> 
   <td>Benutzerdefinierte Berichte erstellen und überwachen.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/hobbes.md">Testen</a></td> 
   <td>Für die Anwendung definierte Tests ausführen.</td> 
  </tr> 
  <tr> 
   <td>Granite-Vorgänge</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/developing-with-crxde-lite.md">CRXDE Lite</a></td> 
   <td>Anwendungen mit einer webbasierten IDE entwickeln.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md">Pakete</a></td> 
   <td>Anwendungen verpacken und freigeben.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md#package-share">Package Share</a></td> 
   <td>Anwendungen von Adobe und der Benutzer-Community herunterladen.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md#administering-topologies">Topologie-Browser</a></td> 
   <td>Instanzentopologie anzeigen.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md">Browser-Abladung</a></td> 
   <td>Verwalten der Abladung</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#backups">Sicherung</a></td> 
   <td>Hintergrundaufgaben durchführen.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Web-Konsole<br /> </td> 
   <td>Anwendungsplattform konfigurieren und verwalten.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Sicherungskopie der Web-Konsolen-Konfiguration<br /> </td> 
   <td>Laden Sie den Konfigurationsstatus von der Web-Konsole herunter.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Benutzer</td> 
   <td>Benutzer verwalten.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Gruppen</td> 
   <td>Gruppen verwalten.</td> 
  </tr> 
  <tr> 
   <td>Externe Ressourcen<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Dokumentation</td> 
   <td>Dokumentation für Web Experience Management aufrufen.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Entwicklungsressourcen</td> 
   <td>Ressourcen und Downloads für Entwickler.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Einige der oben genannten Optionen sind tatsächlich mit der klassischen Benutzeroberfläche verknüpft.
