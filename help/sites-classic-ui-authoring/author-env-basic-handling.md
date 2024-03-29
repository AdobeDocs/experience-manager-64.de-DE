---
title: Grundlegende Handhabung
seo-title: Basic Handling
description: Eine Übersicht über die grundlegende Handhabung bei der Verwendung der AEM Autorenumgebung. Als Grundlage wird die Sites-Konsole verwendet.
seo-description: An overview of basic handling when using the AEM author environment. It uses the Sites console as a basis.
uuid: ab488d7c-7b7f-4a23-a80c-99d37ac84246
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9737ead9-e324-43c9-9780-7abd292f4e5b
exl-id: 49bf3e19-d299-4c99-896c-b12135f33fb7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1230'
ht-degree: 42%

---

# Grundlegende Handhabung{#basic-handling}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>* Auf dieser Seite erhalten Sie einen Überblick über die grundlegende Handhabung der AEM Autorenumgebung. Als Grundlage wird die **Sites-Konsole** verwendet.
>
>* Einige Funktionen sind nicht in allen Konsolen verfügbar und/oder zusätzliche Funktionen sind in einigen Konsolen verfügbar. Spezifische Informationen zu den einzelnen Konsolen und den zugehörigen Funktionen werden auf anderen Seiten ausführlicher behandelt.
>* In AEM stehen verschiedene Tastaturbefehle zur Verfügung, insbesondere bei [der Verwendung von Konsolen](/help/sites-classic-ui-authoring/author-env-keyboard-shortcuts.md) und [der Bearbeitung von Seiten](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md).
>


## Der Begrüßungsbildschirm {#the-welcome-screen}

Die klassische Benutzeroberfläche bietet eine Auswahl an Konsolen, die bekannte Mechanismen zum Navigieren und Initiieren von Aktionen verwenden, einschließlich Klicken, Doppelklicken und [Kontextmenüs](#context-menus).

Nach der Anmeldung wird der Begrüßungsbildschirm angezeigt, der eine Liste von Links zu Konsolen und Diensten bereitstellt:

![screen_shot_2012-01-30at61745pm](assets/screen_shot_2012-01-30at61745pm.png)

## Konsolen {#consoles}

Die Hauptkonsolen sind: 

<table> 
 <tbody> 
  <tr> 
   <td><strong>Konsole</strong></td> 
   <td><strong>Zweck</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Willkommen</strong></td> 
   <td>Bietet einen Überblick über und (über Links) direkten Zugriff auf die Hauptfunktionen von AEM.</td> 
  </tr> 
  <tr> 
   <td><strong>Digitale Assets</strong><br /> </td> 
   <td>In diesen Konsolen können Sie digitale Assets, wie Bilder, Videos, Dokumente und Audiodateien, importieren und <a href="/help/sites-classic-ui-authoring/classicui-assets.md">verwalten</a>. Diese Assets können dann von jeder Website verwendet werden, die auf derselben AEM-Instanz ausgeführt wird. </td> 
  </tr> 
  <tr> 
   <td><strong>Launches</strong></td> 
   <td>Hier können Sie Ihre <a href="/help/sites-classic-ui-authoring/classic-launches.md">Launches</a> verwalten. Damit können Sie Inhalte für eine künftige Version einer oder mehrerer aktivierter Webseiten entwickeln.<br /> <i>Hinweis: In der Touch-optimierten Benutzeroberfläche sind die meisten der Funktionen in der Sites-Konsole verfügbar ebenso wie die Leiste „Verweise“.</i> <i>Bei Bedarf ist diese Konsole über die Konsole „Tools“ erreichbar. Wählen Sie „Vorgänge“ gefolgt von „Launches“.</i></td> 
  </tr> 
  <tr> 
   <td><strong>Posteingang </strong></td> 
   <td>In vielen Fällen sind eine Reihe von Personen an den Unteraufgaben eines Workflows beteiligt, und jede Person muss ihren Schritt abschließen, bevor die Arbeit an die nächste Person übergeben wird. Im Posteingang werden Benachrichtigungen zu diesen Aufgaben angezeigt. Siehe <a href="/help/sites-administering/workflows.md">Arbeiten mit Workflows</a>. <br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Tagging</strong></td> 
   <td>In der Tagging-Konsole können Sie Tags verwalten. Bei Tags handelt es sich um kurze Namen oder Begriffe, mit denen Sie Inhaltsbereiche kommentieren können, sodass diese leichter gefunden und organisiert werden können. Weitere Informationen finden Sie unter <a href="/help/sites-classic-ui-authoring/classic-feature-tags.md">Verwenden und Verwalten von Tags</a>.</td> 
  </tr> 
  <tr> 
   <td><strong>Tools</strong></td> 
   <td>Die Konsolen <a href="/help/sites-administering/tools-consoles.md">Tools</a> bieten Zugriff auf eine Vielzahl spezialisierter Tools und Konsolen, mit denen Sie Websites, digitale Assets und andere Bereiche Ihres Inhalts-Repositorys verwalten können.</td> 
  </tr> 
  <tr> 
   <td><strong>Benutzer</strong></td> 
   <td>In diesen Konsolen können Sie Zugriffsberechtigungen für Benutzer und Gruppen verwalten. Ausführliche Informationen finden Sie unter <a href="/help/sites-administering/security.md">Benutzerverwaltung und Sicherheit</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Websites</strong></td> 
   <td>Mit der Konsole "Sites/Websites"können Sie <a href="/help/sites-classic-ui-authoring/classic-page-author.md">Websites erstellen, anzeigen und verwalten</a> auf Ihrer AEM Instanz ausgeführt werden. In diesen Konsolen können Sie Website-Seiten erstellen, kopieren und verschieben, Workflows starten und Seiten aktivieren (veröffentlichen). Sie können auch eine Seite zur Bearbeitung öffnen.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Workflows</strong></td> 
   <td>Bei einem Workflow handelt es sich um eine definierte Abfolge von Schritten, die zum Ausführen einer bestimmten Aufgabe erforderlich sind. In vielen Fällen sind mehrere Personen an einer Aufgabe beteiligt und jede Person muss Ihren Schritt abschließen, bevor die Arbeit an die nächste Person weitergegeben wird. In der Konsole „Workflow“ können Sie Workflow-Modelle erstellen und Workflow-Instanzen verwalten, die ausgeführt werden. Siehe <a href="/help/sites-administering/workflows.md">Arbeiten mit Workflows</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Die **Websites** -Konsole bietet zwei Bereiche zum Navigieren und Verwalten Ihrer Seiten:

* Linker Bereich

   Zeigt die Baumstruktur Ihrer Websites und die darin enthaltenen Seiten.

   Er enthält außerdem Informationen zu anderen Optionen in AEM, einschließlich Projekten, Blueprints und Assets.

* Rechter Bereich

   Zeigt die Seiten (an der im linken Bereich gewählten Position) und kann für die Durchführung von Aktionen genutzt werden.

Von hier aus können Sie [Seiten verwalten](/help/sites-authoring/managing-pages.md) über die Symbolleiste oder ein Kontextmenü oder durch Öffnen einer Seite für weitere Aktionen.

>[!NOTE]
>
>Die grundlegende Handhabung ist in allen Konsolen gleich. Dieser Abschnitt konzentriert sich auf die **Websites** -Konsole, da dies die primäre Konsole ist, die beim Authoring verwendet wird.

![chlimage_1-9](assets/chlimage_1-9.png)

## Zugreifen auf die Hilfe {#accessing-help}

In verschiedenen Konsolen (z. B. Websites) gibt es auch **Hilfe** verfügbar ist, wird entweder Package Share oder die Dokumentations-Site geöffnet.

![chlimage_1-10](assets/chlimage_1-10.png)

Beim Bearbeiten einer Seite muss die [Sidekick verfügt auch über eine Schaltfläche für den Zugriff auf die Hilfe](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#accessing-help).

## Navigieren mit der Websites-Konsole {#navigating-with-the-websites-console}

Die **Websites** Die Konsole listet Ihre Inhaltsseiten in einer Baumstruktur auf (linker Bereich). Um die Navigation zu vereinfachen, können Abschnitte der Baumstruktur nach Bedarf eingeblendet (+) oder ausgeblendet (-) werden:

* Ein Klick auf den Seitennamen (im linken Bereich) führt zu Folgendem:

   * Untergeordnete Seiten im rechten Bereich auflisten
   * Erweitern Sie auch die Struktur im linken Bereich.

      Aus Leistungsgründen hängt diese Aktion von der Anzahl der untergeordneten Knoten ab. Bei einer Standardinstallation wird die Baumstruktur eingeblendet, wenn höchstens `30` untergeordnete Knoten vorhanden sind.

* Durch Doppelklicken auf den Seitennamen (linker Bereich) wird die Baumstruktur ebenfalls eingeblendet, durch das gleichzeitige Öffnen der Seite ist dieser Effekt aber nicht so offensichtlich.

>[!NOTE]
>
>Der Standardwert (`30`) kann konsolenweise in den programmspezifischen Konfigurationen des SiteAdmin-Widgets geändert werden:
>
>Im Knoten siteadmin :
>
>Legen Sie den Wert der Eigenschaft fest:\
>`treeAutoExpandMax`\
>in:\
>`/apps/wcm/core/content/siteadmin`
>
>Oder global im Design:\
>Legen Sie den Wert von fest:\
>`TREE_AUTOEXPAND_MAX`\
>in:\
>`/apps/cq/ui/widgets/themes/default/widgets/wcm/SiteAdmin.js`
>
>Siehe [SiteAdmin in der CQ Widget-API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteAdmin) für weitere Details.

## Seiteninformationen in der Websites-Konsole {#page-information-on-the-websites-console}

Der rechte Bereich des **Websites** -Konsole bietet eine Listenansicht mit Informationen zu Seiten:

![page-info](assets/page-info.png)

Die folgenden sind verfügbar, ein Teil dieser Felder wird standardmäßig angezeigt:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Spalte</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr> 
  <tr> 
   <td>Miniaturansicht</td> 
   <td>Zeigt eine Miniaturansicht für die Seite an.</td> 
  </tr> 
  <tr> 
   <td>Titel</td> 
   <td>Der Titel, der auf der Seite angezeigt wird</td> 
  </tr> 
  <tr> 
   <td>Name</td> 
   <td>Der Name, AEM auf die Seite verweist</td> 
  </tr> 
  <tr> 
   <td>Veröffentlicht</td> 
   <td>Gibt an, ob die Seite veröffentlicht wurde, und gibt Datum und Uhrzeit der Veröffentlichung an.</td> 
  </tr> 
  <tr> 
   <td>Geändert</td> 
   <td>Gibt an, ob die Seite geändert wurde, und gibt Datum und Uhrzeit der Änderung an. Um Änderungen zu speichern, müssen Sie die Seite aktivieren.</td> 
  </tr> 
  <tr> 
   <td>Scene7 Publish</td> 
   <td>Gibt an, ob die Seite in Scene7 veröffentlicht wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Gibt den aktuellen Status der Seite an, z. B. ob die Seite Teil eines Workflows oder einer Live Copy ist oder ob eine Seite derzeit gesperrt ist.</td> 
  </tr> 
  <tr> 
   <td>Impressionen</td> 
   <td>Zeigt die Aktivität auf einer Seite in Anzahl der Treffer an.</td> 
  </tr> 
  <tr> 
   <td>Vorlage</td> 
   <td>Gibt die Vorlage an, auf der eine Seite basiert.</td> 
  </tr> 
  <tr> 
   <td>In Workflow</td> 
   <td>Gibt an, wann sich die Seite in einem Workflow befindet.</td> 
  </tr> 
  <tr> 
   <td>Gesperrt durch</td> 
   <td>Zeigt an, wann eine Seite gesperrt wurde und welches Benutzerkonto sie gesperrt hat.</td> 
  </tr> 
  <tr> 
   <td>Live Copy</td> 
   <td>Gibt an, wann die Seite Teil einer Live Copy ist.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Um die sichtbaren Spalten auszuwählen, bewegen Sie den Mauszeiger auf einen Spaltenkopf. Ein Dropdown-Menü wird angezeigt, über das Sie die **Spalten** -Option.

Die Farben neben den Seiten in **Veröffentlicht** und **Geändert** gibt den Veröffentlichungsstatus an:

| **Spalte** | **Farbe** | **Beschreibung** |
|---|---|---|
| Veröffentlicht | Grün | Die Veröffentlichung war erfolgreich. Der Inhalt wird veröffentlicht. |
| Veröffentlicht | Gelb | Die Veröffentlichung steht aus. Die Veröffentlichung wurde noch nicht durch das System bestätigt. |
| Veröffentlicht | Rot | Veröffentlichung fehlgeschlagen. Es besteht keine Verbindung zur Veröffentlichungsinstanz. Dies kann auch bedeuten, dass der Inhalt deaktiviert wurde. |
| Veröffentlicht | *blank* | Diese Seite wurde noch nie veröffentlicht. |
| Geändert | Blau | Die Seite wurde seit der letzten Veröffentlichung geändert. |
| Geändert | *blank* | Diese Seite wurde noch nie geändert oder wurde seit der letzten Veröffentlichung nicht geändert. |

## Kontextmenüs {#context-menus}

Die klassische Benutzeroberfläche nutzt für die Navigation und für das Starten von Aktionen vertraute Mechanismen wie Klicks oder Doppelklicks. Abhängig von der aktuellen Situation stehen auch verschiedene Kontextmenüs zur Verfügung (die normalerweise mit der rechten Maustaste geöffnet werden):

![chlimage_1-11](assets/chlimage_1-11.png)
