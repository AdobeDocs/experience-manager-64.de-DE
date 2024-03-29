---
title: Anpassen und Erweitern von Inhaltsfragmenten
seo-title: Customizing and Extending Content Fragments
description: Ein Inhaltsfragment erweitert ein Standard-Asset.
seo-description: A content fragment extends a standard asset.
uuid: f8d0bb22-0b51-4488-a1c8-29e50213c913
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: af95c6c7-0475-4f55-88a8-ec5e39a9ddcd
exl-id: 540391a8-b846-4e5e-bf77-ab20726f06d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2783'
ht-degree: 64%

---

# Anpassen und Erweitern von Inhaltsfragmenten{#customizing-and-extending-content-fragments}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!CAUTION]
>
>Einige Inhaltsfragmentfunktionen erfordern die Anwendung von [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md).

Ein Inhaltsfragment erweitert ein Standard-Asset. siehe:

* [Erstellen und Verwalten von Inhaltsfragmenten](/help/assets/content-fragments.md) und [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md).

* [Verwalten von Assets](/help/assets/managing-assets-touch-ui.md) und [Anpassen und Erweitern von Assets](/help/assets/extending-assets.md) für weitere Informationen zu Standard-Assets.

## Architektur {#architecture}

Ein Inhaltsfragment umfasst die folgenden grundlegenden [Bestandteile](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment):

* Ein *Inhaltsfragment,*,
* das ein oder mehrere *Inhaltselemente* enthält,
* und eine oder mehrere *Inhaltsvarianten* aufweisen kann.

Je nach Fragmenttyp werden außerdem Modelle oder Vorlagen verwendet:

>[!CAUTION]
>
>Es werden derzeit [Inhaltsfragmentmodelle](/help/assets/content-fragments-models.md) zum Erstellen aller Fragmente empfohlen.
>
>Inhaltsfragmentmodelle werden für alle Beispiele in We.Retail verwendet.

* Inhaltsfragmentmodelle:

   * Dient zum Definieren von Inhaltsfragmenten, die strukturierte Inhalte enthalten.
   * Inhaltsfragmentmodelle definieren die Struktur eines Inhaltsfragments, wenn dieses erstellt wird.
   * Ein Fragment verweist auf das Modell. Änderungen am Modell können sich daher auf alle abhängigen Fragmente auswirken.
   * Modelle werden anhand von Datentypen erstellt.
   * Funktionen zum Hinzufügen neuer Varianten und dergleichen müssen das Fragment entsprechend aktualisieren.

   >[!CAUTION]
   >
   >Alle Änderungen an einem vorhandenen Inhaltsfragmentmodell können sich auf abhängige Fragmente auswirken. Daher kann es zu verwaisten Eigenschaften in diesen Fragmenten kommen.

* Inhaltsfragmentvorlagen:

   * wird zum Definieren von einfachen Inhaltsfragmenten verwendet.
   * Vorlagen definieren die (einfache, schreibgeschützte) Struktur eines Inhaltsfragments bei seiner Erstellung.
   * Die Vorlage wird beim Erstellen in das Fragment kopiert. sodass weitere Änderungen an der Vorlage nicht in vorhandenen Fragmenten übernommen werden.
   * Funktionen zum Hinzufügen neuer Varianten und dergleichen müssen das Fragment entsprechend aktualisieren.
   * [Inhaltsfragmentvorlagen](/help/sites-developing/content-fragment-templates.md) arbeiten anders als die anderen Vorlagen in der AEM-Umgebung (z. B. Seitenvorlagen usw.). Daher sollten sie getrennt betrachtet werden.
   * Wenn der MIME-Typ des Inhalts auf einer Vorlage basiert, wird er anhand des tatsächlichen Inhalts verwaltet. Dies bedeutet, dass jedes Element und jede Variante einen anderen MIME-Typ haben kann.

## Integration mit Assets {#integration-with-assets}

Die Inhaltsfragmentverwaltung (Content Fragment Management, CFM) ist Teil von AEM Assets:

* Inhaltsfragmente sind Assets.
* Sie verwenden vorhandene Assets-Funktionen.
* Sie sind vollständig mit Assets integriert (Admin-Konsole usw.).

### Zuordnen von strukturierten Inhaltsfragmenten zu Assets {#mapping-structured-content-fragments-to-assets}

![fragment-to-assets-structured](assets/fragment-to-assets-structured.png)

Inhaltsfragmente mit strukturierten Inhalten (d. h. basierend auf einem Inhaltsfragmentmodell) werden einem einzelnen Asset zugeordnet:

* Alle Inhalte werden im Knoten `jcr:content/data` des Assets gespeichert:

   * Die Elementdaten werden im primären Unterknoten gespeichert:

      `jcr:content/data/master`

   * Varianten werden unter einem Unterknoten gespeichert, der den Namen der Variante trägt:

      z. B. `jcr:content/data/myvariation`

   * Die Daten der einzelnen Elemente werden im entsprechenden Unterknoten als Eigenschaft mit dem Elementnamen gespeichert:

      z. B. Inhalt des Elements `text` wird als Eigenschaft gespeichert `text` on `jcr:content/data/master`

* Metadaten und verknüpfte Inhalte werden unten gespeichert `jcr:content/metadata`

   Mit Ausnahme des Titels und der Beschreibung, die nicht als Metadaten im herkömmlichen Sinne gelten und in gespeichert werden `jcr:content`

### Zuordnen von einfachen Inhaltsfragmenten zu Assets {#mapping-simple-content-fragments-to-assets}

![chlimage_1-253](assets/chlimage_1-253.png)

Einfache Inhaltsfragmente (basierend auf einer Vorlage) werden einem Composite aus Haupt-Asset und (optionalen) Unter-Assets zugeordnet:

* Alle nicht inhaltsbezogenen Informationen eines Fragments (wie Titel, Beschreibung, Metadaten, Struktur) werden ausschließlich für das Haupt-Asset verwaltet.
* Der Inhalt des ersten Elements eines Fragments wird der ursprünglichen Ausgabe des Haupt-Assets zugeordnet.

   * Die Varianten (sofern vorhanden) des ersten Elements werden anderen Ausgabeformaten des Haupt-Assets zugeordnet.

* Zusätzliche Elemente (sofern vorhanden) werden Teil-Assets des Haupt-Assets zugeordnet.

   * Der Hauptinhalt dieser zusätzlichen Elemente wird dem ursprünglichen Ausgabeformat des jeweiligen Unter-Assets zugeordnet.
   * Andere Varianten (falls zutreffend) zusätzlicher Elemente werden anderen Ausgabeformaten der jeweiligen Unter-Assets zugeordnet.

### Asset-Speicherort {#asset-location}

Wie bei Standard-Assets wird das Inhaltsfragment gespeichert in:

* `/content/dam`

### Asset-Berechtigungen {#asset-permissions}

Weitere Informationen finden Sie unter [Inhaltsfragmente – Überlegungen zum Löschen](/help/assets/content-fragments-delete.md).

### Funktionsintegration {#feature-integration}

* Die Funktion &quot;Inhaltsfragmentverwaltung&quot;(Content Fragment Management, CFM) baut auf dem Assets-Kern auf, sollte jedoch so unabhängig wie möglich sein.
* CFM stellt eigene Implementierungen für Elemente in der Karten-, Spalten- und Listenansicht bereit. Diese sind mit den Ausgabeformatimplementierungen vorhandener Asset-Inhalte verknüpft.
* Einige Asset-Komponenten wurden für Inhaltsfragmente erweitert.

## Verwenden von Inhaltsfragmenten in Seiten {#using-content-fragments-in-pages}

>[!CAUTION]
>
>Derzeit wird die [Kernkomponente für Inhaltsfragmente](https://helpx.adobe.com/de/experience-manager/core-components/using/content-fragment-component.html) dafür empfohlen. Weitere Informationen finden Sie unter [Entwickeln von Kernkomponenten](https://helpx.adobe.com/de/experience-manager/core-components/using/developing.html).

AEM-Seiten können auf Inhaltsfragmente verweisen, ähnlich wie bei allen anderen Asset-Typen. AEM stellt die Kernkomponente für [**Inhaltsfragmente** bereit](https://helpx.adobe.com/de/experience-manager/core-components/using/content-fragment-component.html), eine [Komponente, mit der Sie Inhaltsfragmente in Seiten einfügen können](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page). Sie können die Kernkomponente für **Inhaltsfragmente** auch erweitern.

* Die Komponente verwendet die `fragmentPath`-Eigenschaft für Verweise auf das tatsächliche Inhaltsfragment. Die `fragmentPath`-Eigenschaft wird wie ähnliche Eigenschaften anderer Asset-Typen gehandhabt, beispielsweise wenn das Inhaltsfragment zu einem anderen Speicherort verschoben wird.

* Mit der Komponente können Sie die Variante auswählen, die angezeigt werden soll.
* Außerdem kann eine Reihe von Absätzen ausgewählt werden, um die Ausgabe zu beschränken, z. B. für die Ausgabe in mehreren Spalten.
* Die Komponente ermöglicht [Zwischeninhalt](/help/sites-developing/components-content-fragments.md#in-between-content):

   * Die Komponente ermöglicht es Ihnen, andere Assets (Bilder usw.) zwischen den Absätzen des Fragments zu platzieren, auf das verwiesen wird.
      * Bei Zwischeninhalten müssen Sie:

         * beachten, dass Verweise möglicherweise instabil sind. Bei der Seitenbearbeitung hinzugefügte Zwischeninhalte haben keine feste Beziehung zu dem Absatz, neben dem sie platziert werden; es wird ein neuer Absatz (im Inhaltsfragment-Editor) eingefügt, bevor der Zwischeninhalt die relative Position verlieren kann.
            * die zusätzlichen Parameter (z. B. Varianten und Absatzfilter) berücksichtigen, um falsche Positivwerte in Suchergebnissen zu vermeiden

>[!NOTE]
>
>**Inhaltsfragmentmodell:**
>
>Bei Verwendung eines Inhaltsfragments, das auf einem Inhaltsfragmentmodell auf einer Seite basiert, wird auf das Modell verwiesen. Falls das Modell also zum Zeitpunkt der Seitenveröffentlichung nicht veröffentlicht wurde, wird dies gekennzeichnet und das Modell zu den Ressourcen hinzugefügt, die mit der Seite veröffentlicht werden sollen.
>
>**Inhaltsfragmentvorlage:**
>
>Bei Verwendung eines auf einer Inhaltsfragmentvorlage basierten Inhaltsfragments auf einer Seite erfolgt kein Verweis, da die Vorlage beim Erstellen des Fragments kopiert wurde.

### Konfiguration mithilfe der OSGi-Konsole {#configuration-using-osgi-console}

Die Backend-Implementierung von Inhaltsfragmenten ist beispielsweise dafür verantwortlich, Instanzen eines Fragments zu erstellen, das auf einer durchsuchbaren Seiten verwendet wird, oder gemischte Medieninhalte zu verwalten. Diese Implementierung muss wissen, welche Komponenten zum Rendern von Fragmenten verwendet werden und wie das Rendering parametrisiert wird.

Die Parameter hierfür können im Abschnitt [Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console)für das OSGi-Bundle **Konfiguration von DAM-Inhaltsfragmenten**.

* **Ressourcentypen**

   Eine Liste von `sling:resourceTypes` kann bereitgestellt werden, um Komponenten zu definieren, die für die Wiedergabe von Inhaltsfragmenten verwendet werden und auf die die Hintergrundverarbeitung angewendet werden soll.

* **Referenzeigenschaften**

   Eine Liste von Eigenschaften kann konfiguriert werden, um anzugeben, wo der Verweis auf das Fragment für die jeweilige Komponente gespeichert wird.

>[!NOTE]
>
>Es gibt keine direkte Zuordnung zwischen Eigenschaft und Komponententyp.
>
>AEM verwendet einfach die erste Eigenschaft im Absatz. Daher sollten Sie die Eigenschaften sorgfältig auswählen.

![osgi-config](assets/osgi-config.png)

Es gibt noch einige weitere Richtlinien, die Sie befolgen müssen, um sicherzustellen, dass die Komponente mit der Hintergrundverarbeitung des Inhaltsfragments kompatibel ist:

* Der Name der Eigenschaft, die das Rendern der Elemente definiert, muss `element` oder `elementNames` lauten.

* Der Name der Eigenschaft, die das Rendern der Variante definiert, muss `variation` oder `variationName` lauten.

* Falls die Ausgabe mehrerer Elemente (durch Verwendung von `elementNames` zur Angabe mehrerer Elemente) unterstützt wird, wird der tatsächliche Anzeigemodus durch die `displayMode`-Eigenschaft definiert:

   * Falls der Wert `singleText` lautet (und nur ein Element konfiguriert ist), wird das Element als Text mit Zwischeninhalt, Layout-Unterstützung usw. gerendert. Dies ist die Standardeinstellung für Fragmente, in denen nur ein einzelnes Element gerendert wird.
   * Andernfalls wird ein viel einfacherer Ansatz verwendet (könnte als &quot;Formularansicht&quot;bezeichnet werden), bei dem kein Zwischeninhalt unterstützt wird und der Fragmentinhalt unverändert wiedergegeben wird.

* Falls das Fragment für `displayMode` == `singleText` (implizit oder explizit) gerendert wird, müssen auch folgende zusätzlichen Eigenschaften berücksichtigt werden:

   * `paragraphScope` definiert, ob alle Absätze oder nur ein Absatzbereich gerendert werden sollen (Werte: `all` oder `range`).
   * Falls `paragraphScope` == `range`, definiert die `paragraphRange`-Eigenschaft den Absatzbereich, der gerendert werden soll.

### Integration mit anderen Frameworks {#integration-with-other-frameworks}

Inhaltsfragmente können mit folgenden Frameworks integriert werden:

* **Übersetzungen**

   Inhaltsfragmente sind vollständig mit dem [AEM-Übersetzungs-Workflow](/help/sites-administering/tc-manage.md) integriert. Auf Architekturebene bedeutet dies:

   * Die einzelnen Übersetzungen eines Inhaltsfragments sind separate Fragmente, z. B.:

      * sie befinden sich unter verschiedenen Sprachstämmen:

         `/content/dam/<path>/en/<to>/<fragment>`

         im Vergleich zu

         `/content/dam/<path>/de/<to>/<fragment>`

      * sie verwenden jedoch genau denselben relativen Pfad unterhalb des Sprachstamms:

         `/content/dam/<path>/en/<to>/<fragment>`

         im Vergleich zu

         `/content/dam/<path>/de/<to>/<fragment>`
   * Außer den regelbasierten Pfaden besteht keinerlei Verbindung zwischen den unterschiedlichen Sprachversionen von Inhaltsfragmenten. Sie werden als zwei separate Fragmente behandelt, obwohl die Benutzeroberfläche Funktionen zum Navigieren zwischen den Sprachvarianten beinhaltet.
   >[!NOTE]
   >
   >Der AEM-Übersetzungs-Workflow arbeitet mit `/content`:
   >
   >  * Da sich die Inhaltsfragmentmodelle in `/conf` befinden, sind sie nicht in diesen Übersetzungen beinhaltet. Sie können [die Strings der Benutzeroberfläche internationalisieren](/help/sites-developing/i18n-dev.md).
   >  * Vorlagen werden kopiert, um Fragmente zu erstellen, sodass dies impliziert ist.


* **Metadatenschemata**

   * Inhaltsfragmente verwenden [Metadatenschemata](/help/assets/metadata-schemas.md) (wieder), die mit Standard-Assets definiert werden können.
* CFM bietet ein eigenes, spezifisches Schema:

   `/libs/dam/content/schemaeditors/forms/contentfragment`

   dieses kann bei Bedarf erweitert werden.
* Das entsprechende Schemaformular ist mit dem Fragmenteditor integriert.

## Server-seitige API für die Inhaltsfragmentverwaltung {#the-content-fragment-management-api-server-side}

Sie können die Server-seitige API für den Zugriff auf Inhaltsfragmente verwenden, siehe:

<pre><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/package-summary.html">com.adobe.cq.dam.cfm</a></pre>

>[!CAUTION]
>
>Es wird dringend empfohlen, die Server-seitige API zu verwenden, anstatt direkt auf die Inhaltsstruktur zuzugreifen.

### Hauptschnittstellen {#key-interfaces}

Die folgenden drei Schnittstellen können als Einstiegspunkte dienen:

* **Fragmentvorlage**

   <pre><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html">FragmentTemplate</a></pre>

   Verwenden Sie `FragmentTemplate.createFragment()` zum Erstellen eines neuen Fragments.

   ```
   Resource templateOrModelRsc = resourceResolver.getResource("...");
   FragmentTemplate tpl = templateOrModelRsc.adaptTo(FragmentTemplate.class);
   ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
   ```

   Diese Schnittstelle steht für:

   * ein Inhaltsfragmentmodell oder eine Inhaltsfragmentvorlage, aus dem bzw. der Sie ein Inhaltsfragment erstellen können,
   * und (nach dem Erstellen) die Strukturdaten des Fragments.

   Diese Daten können Folgendes beinhalten:

   * Zugriff auf grundlegende Daten (Titel, Beschreibung)
   * Zugriff auf Vorlagen/Modelle für die Elemente des Fragments:

      * Listenelementvorlagen
      * Abrufen von Strukturinformationen für ein bestimmtes Element
      * Zugriff auf die Elementvorlage (siehe `ElementTemplate`)
   * Zugriff auf Vorlagen für Varianten des Fragments:

      * Variantenvorlagen auflisten
      * Abrufen von Strukturdaten für eine bestimmte Variante
      * Zugriff auf die Variantenvorlage (siehe `VariationTemplate`)
   * Erste verknüpfte Inhalte abrufen

   Schnittstellen, die wichtige Informationen darstellen:

   * `ElementTemplate`

      * Abrufen grundlegender Daten (Name, Titel)
      * Abrufen des anfänglichen Elementinhalts
   * `VariationTemplate`

      * Abrufen grundlegender Daten (Name, Titel, Beschreibung)






* **Inhaltsfragment**

   <pre><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html">ContentFragment</a></pre>

   In dieser Schnittstelle können Sie abstrakt mit einem Inhaltsfragment arbeiten.

   >[!CAUTION]
   >
   >Es wird dringend empfohlen, über diese Benutzeroberfläche auf ein Fragment zuzugreifen. Eine direkte Änderung der Inhaltsstruktur sollte vermieden werden.

   Die Schnittstelle bietet folgende Möglichkeiten:

   * Verwalten grundlegender Daten (z. B. Abrufen von Namen, Abrufen/Festlegen von Titel, Beschreibung)
   * Zugriff auf Metadaten
   * Zugriff auf Elemente:

      * Auflisten von Elementen
      * Abrufen von Elementen nach Name
      * Erstellen neuer Elemente (siehe [Einschränkungen](#caveats))
      * Zugriff auf Elementdaten (siehe `ContentElement`)
   * Auflisten der für das Fragment definierten Varianten
   * Globales Erstellen neuer Varianten
   * Verwalten zugeordneter Inhalte:

      * Auflisten von Sammlungen
      * Hinzufügen von Sammlungen
      * Entfernen von Sammlungen
   * Zugreifen auf das Fragmentmodell   oder Vorlage

   Folgende Schnittstellen stehen für die Hauptelemente eines Fragments:

   * **Inhaltselement**

      <pre><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentElement.html">ContentElement</a></pre>

      * Abrufen grundlegender Daten (Name, Titel, Beschreibung)
      * Abrufen/Festlegen von Inhalten
      * Zugriff auf Varianten eines Elements:

         * Auflisten von Varianten
         * Abrufen von Varianten nach Name
         * Erstellen neuer Varianten (siehe [Einschränkungen](#caveats))
         * Entfernen von Varianten (siehe [Einschränkungen](#caveats))
         * Zugriff auf Variantendaten (siehe `ContentVariation`)
      * Tastaturbefehl zum Auflösen von Varianten (Anwenden zusätzlicher implementierungsspezifischer Ausweich-Logik, falls die angegebene Variante für ein Element nicht verfügbar ist)
   * **Inhaltsvariante**

      <pre><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html">ContentVariation</a></pre>

      * Abrufen grundlegender Daten (Name, Titel, Beschreibung)
      * Abrufen/Festlegen von Inhalten
      * Einfache Synchronisierung basierend auf den zuletzt geänderten Informationen

   Alle drei Schnittstellen (`ContentFragment`, `ContentElement`, `ContentVariation`) erweitern die `Versionable`-Schnittstelle durch zusätzliche, für Inhaltsfragmente erforderliche Versionierungsfunktionen:

   * Erstellen neuer Versionen des Elements
   * Auflisten der Versionen des Elements
   * Abrufen des Inhalts einer spezifischen Version des versionierten Elements







### Anpassen mit adaptTo() {#adapting-using-adaptto}

Folgendes kann angepasst werden:

* `ContentFragment` kann angepasst werden an:

   * `Resource` – die zugrunde liegende Sling-Ressource. Beachten Sie, dass beim direkten Aktualisieren der zugrunde liegenden `Resource` das `ContentFragment`-Objekt neu erstellt werden muss.
   * `Asset` – die DAM-`Asset`-Abstrahierung, die für das Inhaltsfragment steht. Beachten Sie, dass beim direkten Aktualisieren des `Asset` das `ContentFragment`-Objekt neu erstellt werden muss.

* `ContentElement` kann angepasst werden an:

   * `ElementTemplate` – für den Zugriff auf die Strukturdaten des Elements.

* `FragmentTemplate` kann angepasst werden an:

   * `Resource` – die `Resource`, die das Modell, auf das verwiesen wird, oder die ursprüngliche Vorlage, die kopiert wurde, bestimmt.

      * An der `Resource` vorgenommene Änderungen werden nicht automatisch für die `FragmentTemplate` übernommen.

* `Resource` kann angepasst werden an:

   * `ContentFragment`
   * `FragmentTemplate`

### Einschränkungen {#caveats}

Beachten Sie Folgendes:

* Die API ist implementiert, um Funktionen bereitzustellen, die von der Benutzeroberfläche unterstützt werden.
* Die gesamte API ist so konzipiert, dass Änderungen **nicht** automatisch persistent gespeichert werden (es sei denn, dies ist anders in der Java-Dokumentation der API angegeben). Daher müssen Sie immer den Ressourcenkonfliktlöser der entsprechenden Anfrage (oder den tatsächlich verwendeten Konfliktlöser) festlegen.
* Aufgaben, für die möglicherweise zusätzliche Arbeitsschritte erforderlich sind:

   * Durch das Erstellen/Entfernen neuer Elemente wird die Datenstruktur einfacher Fragmente (basierend auf einer Fragmentvorlage) nicht aktualisiert.
   * Beim Erstellen neuer Varianten auf Basis von `ContentElement` wird die Datenstruktur nicht aktualisiert (beim globalen Erstellen auf Basis von `ContentFragment` wird sie jedoch aktualisiert).
   * Durch das Entfernen vorhandener Varianten wird die Datenstruktur nicht aktualisiert.

## Client-seitige API für die Inhaltsfragmentverwaltung   {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>Bei AEM 6.4 ist die Client-seitige API intern.

### Zusätzliche Informationen {#additional-information}

Beachten Sie Folgendes:

* `filter.xml`

   `filter.xml` für die Inhaltsfragmentverwaltung ist so konfiguriert, dass es sich nicht mit dem Hauptinhaltspaket für Assets überschneidet.

## Bearbeitungssitzungen {#edit-sessions}

Eine Bearbeitungssitzung wird gestartet, wenn der Benutzer ein Inhaltsfragment in einer der Editor-Seiten öffnet. Die Bearbeitungssitzung ist beendet, wenn der Benutzer den Editor durch Auswählen von **Speichern** oder **Abbrechen** verlässt.

### Voraussetzungen {#requirements}

Für das Steuern einer Bearbeitungssitzung gelten folgende Voraussetzungen:

* Das Bearbeiten eines Inhaltsfragments, das mehrere Ansichten (d. h. HTML-Seiten) umspannen kann, sollte atomisch sein.
* Die Bearbeitung sollte auch *transactional*; am Ende der Bearbeitungssitzung müssen die Änderungen entweder übernommen (gespeichert) oder zurückgesetzt (abgebrochen) werden.
* Edge-Fälle sollten ordnungsgemäß behandelt werden. Dazu gehören Situationen, z. B. wenn der Benutzer die Seite verlässt, indem er manuell eine URL eingibt oder die globale Navigation verwendet.
* Es sollte eine regelmäßige automatische Speicherung (alle x Minuten) verfügbar sein, um Datenverlust zu vermeiden.
* Wenn ein Inhaltsfragment von zwei Benutzern gleichzeitig bearbeitet wird, sollten diese die Änderungen der anderen Benutzer nicht überschreiben.

### Prozesse {#processes}

Folgende Prozesse sind involviert:

* Starten einer Sitzung

   * Eine neue Version des Inhaltsfragments wird erstellt.
   * Das automatische Speichern wird gestartet.
   * Cookies werden festgelegt. Diese definieren das derzeit bearbeitete Fragment und den Status „offene Bearbeitungssitzung“.

* Beenden einer Sitzung

   * Die automatische Speicherung wird angehalten.
   * Beim Speichern:

      * Die zuletzt geänderten Informationen werden aktualisiert.
      * Cookies werden entfernt.
   * Beim Rollback:

      * Die Version des Inhaltsfragments, die beim Starten der Bearbeitungssitzung erstellt wurde, wird wiederhergestellt.
      * Cookies werden entfernt.


* Bearbeiten

   * Alle Änderungen (automatisches Speichern eingeschlossen) werden im aktiven Inhaltsfragment vorgenommen, nicht in einem separaten, geschützten Bereich.
   * Daher werden diese Änderungen sofort auf AEM Seiten angezeigt, die auf das entsprechende Inhaltsfragment verweisen

### Aktionen {#actions}

Die möglichen Aktionen sind:

* Einstieg in eine Seite

   * Überprüfen Sie, ob bereits eine Bearbeitungssitzung vorhanden ist. durch Überprüfung des entsprechenden Cookies.

      * Wenn eine existiert, überprüfen Sie, ob die Bearbeitungssitzung für das Inhaltsfragment gestartet wurde, das derzeit bearbeitet wird.

         * Wenn das aktuelle Fragment vorhanden ist, stellen Sie die Sitzung wieder her.
         * Wenn nicht, versuchen Sie, die Bearbeitung für das zuvor bearbeitete Inhaltsfragment abzubrechen und Cookies zu entfernen (danach ist keine Bearbeitungssitzung mehr vorhanden).
      * Wenn keine Bearbeitungssitzung vorhanden ist, warten Sie auf die erste vom Benutzer vorgenommene Änderung (siehe unten).
   * Überprüfen Sie, ob das Inhaltsfragment bereits auf einer Seite referenziert ist, und zeigen Sie entsprechende Informationen an, falls dies der Fall ist.



* Inhaltsänderung

   * Jedes Mal, wenn ein Benutzer Inhalte ändert und keine Bearbeitungssitzung vorhanden ist, wird eine Bearbeitungssitzung erstellt (siehe [Starten einer Sitzung](#processes)).

* Verlassen einer Seite

   * Falls eine Bearbeitungssitzung vorhanden ist und die Änderungen nicht persistent gespeichert wurden, wird ein Modal-Bestätigungsdialogfeld angezeigt, um den Benutzer über potenziell verloren gegangene Daten zu benachrichtigen und es ihm zu ermöglichen, auf der Seite zu bleiben.

## Beispiele {#examples}

### Beispiel: Zugreifen auf ein vorhandenes Inhaltsfragment {#example-accessing-an-existing-content-fragment}

Dazu können Sie die Ressource, die für die API steht, wie folgt anpassen:

`com.adobe.cq.dam.cfm.ContentFragment`

Beispiel:

```java
// first, get the resource
Resource fragmentResource = resourceResolver.getResource("/content/dam/fragments/my-fragment");
// then adapt it
if (fragmentResource != null) {
    ContentFragment fragment = fragmentResource.adaptTo(ContentFragment.class);
    // the resource is now accessible through the API
} 
```

### Beispiel: Erstellen eines neuen Inhaltsfragments {#example-creating-a-new-content-fragment}

Um programmgesteuert ein neues Inhaltsfragment zu erstellen, müssen Sie Folgendes verwenden:

`com.adobe.cq.dam.cfm.ContentFragmentManager#create`

Beispiel:

```java
Resource templateOrModelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = templateOrModelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### Beispiel: Angeben des Intervalls für das automatische Speichern {#example-specifying-the-auto-save-interval}

Das Intervall für das automatische Speichern (gemessen in Sekunden) kann mit dem Konfigurations-Manager (ConfMgr) definiert werden:

* Knoten: `<conf-root>/settings/dam/cfm/jcr:content`
* Eigenschaftsname: `autoSaveInterval`
* Typ: `Long`

* Standard: `600` (10 Minuten); wird definiert in `/libs/settings/dam/cfm/jcr:content`

Wenn Sie ein Intervall von 5 Minuten für das automatische Speichern festlegen möchten, müssen Sie die Eigenschaft auf dem Knoten definieren. Beispiel:

* Knoten: `/conf/global/settings/dam/cfm/jcr:content`
* Eigenschaftsname: `autoSaveInterval`

* Typ: `Long`

* Wert: `300` (5 Minuten entsprechen 300 Sekunden)

## Inhaltsfragmentvorlagen {#content-fragment-templates}

Siehe [Inhaltsfragmentvorlagen](/help/sites-developing/content-fragment-templates.md) für vollständige Informationen.

## Komponenten für die Seitenbearbeitung {#components-for-page-authoring}

Weitere Informationen finden Sie unter

* [Kernkomponenten – Inhaltsfragmentkomponente](https://helpx.adobe.com/de/experience-manager/core-components/using/content-fragment-component.html) (empfohlen)
* [Inhaltsfragmentkomponenten – Komponenten für die Seitenbearbeitung](/help/sites-developing/components-content-fragments.md#components-for-page-authoring)
