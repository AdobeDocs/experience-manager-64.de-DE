---
title: Konfigurieren von OSGi
seo-title: Configuring OSGi
description: OSGi ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfiguration verwendet. In diesem Artikel wird beschrieben, wie Sie die Konfigurationseinstellungen für solche Bundles verwalten können.
seo-description: OSGi is a fundamental element in the technology stack of Adobe Experience Manager (AEM). It is used to control the composite bundles of AEM and their configuration. This article details how you can manage the configuration settings for such bundles.
uuid: b39059a5-dd61-486a-869a-0d7a732c3a47
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: d701e4ba-417f-4b57-b103-27fd25290736
feature: Configuring
exl-id: 977d07d2-36cf-4799-bcfe-991cf89a612a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2006'
ht-degree: 58%

---

# Konfigurieren von OSGi{#configuring-osgi}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). Es wird zur Steuerung der zusammengesetzten AEM-Bundles und ihrer Konfiguration verwendet.

OSGi &quot;*bietet die standardisierten Grundbausteine, die die Erstellung von Anwendungen aus kleinen, wiederverwendbaren und kollaborativen Komponenten ermöglichen. Diese Komponenten können zu einem Programm zusammengefügt und bereitgestellt werden*&quot;.

Dies ermöglicht die einfache Verwaltung von Bundles, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente (siehe [OSGi-Spezifikation](https://docs.osgi.org/specification/)) ist in einem der Bundles enthalten.

Sie können die Konfigurationseinstellungen für solche Bundles wie folgt verwalten:

* mithilfe der [Adobe CQ-Webkonsole](#osgi-configuration-with-the-web-console)
* using [Konfigurationsdateien](#osgi-configuration-with-configuration-files)
* durch die Konfiguration von [Inhaltsknoten ( `sling:OsgiConfig`) im Repository](#osgi-configuration-in-the-repository)

Jede dieser Methoden kann verwendet werden, es gibt aber leichte Unterschiede vor allem in Bezug auf [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md):

* [Adobe CQ Web-Konsole](#osgi-configuration-with-the-web-console)

   * Die Web-Konsole ist die Standardschnittstelle für die OSGi-Konfiguration. Es bietet eine Benutzeroberfläche für die Bearbeitung der verschiedenen Eigenschaften, wo mögliche Werte aus vordefinierten Listen ausgewählt werden können.

      Dies ist die einfachste Methode.

   * Alle über die Web-Konsole durchgeführten Konfigurationen werden unmittelbar auf die aktuelle Instanz angewendet, und zwar unabhängig davon, welcher Ausführungsmodus gerade aktiv ist oder wie dieser zu einem späteren Zeitpunkt geändert werden könnte.

* [Konfigurationsdateien](#osgi-configuration-with-configuration-files)

   * Enthält in der Web-Konsole definierte Einstellungen.
   * Kann in Inhaltspakete zur Verwendung in anderen Instanzen enthalten sein.

* [Inhaltsknoten (sling:osgiConfig) im Repository](#osgi-configuration-in-the-repository)

   * Dies erfordert die manuelle Konfiguration mithilfe von CRXDE Lite.
   * Aufgrund der Namenskonventionen der `sling:OsgiConfig`-Knoten können Sie die Konfiguration an einen bestimmten [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) knüpfen. Sie können sogar Konfigurationen für mehr als einen Ausführungsmodus im selben Repository speichern.
   * Alle entsprechenden Konfigurationen werden sofort angewendet (abhängig vom Ausführungsmodus).

Unabhängig von der verwendeten Konfigurationsmethode bieten die Konfigurationen Folgendes: 

* Stellen Sie sicher, dass beim Kopieren oder Replizieren des Repository-Inhalts identische Konfigurationen neu erstellt werden.
* Ermöglicht Ihnen das Auschecken von Konfigurationen in FileVault oder Subversion; entweder für Sicherheits- oder weitere Updates.
* Kann in Paketen gespeichert werden, die beim Einrichten anderer Instanzen verwendet werden können.
* Ermöglicht Ihnen, Konfigurations-Rollouts mithilfe von Skripten durchzuführen, um die Konfigurationsdetails anzugeben.

>[!NOTE]
>
>Details wichtiger Einstellungen werden unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) aufgelistet. 

## OSGi-Konfiguration mit der Web-Konsole {#osgi-configuration-with-the-web-console}

Die [Webkonsole](/help/sites-deploying/web-console.md) in AEM bietet eine standardisierte Schnittstelle zum Konfigurieren der Bundles. Die **Konfiguration** -Tab wird zur Konfiguration der OSGi-Bundles verwendet und ist daher der zugrunde liegende Mechanismus zur Konfiguration AEM Systemparameter.

Alle vorgenommenen Änderungen werden sofort auf die entsprechende OSGi-Konfiguration angewendet. Ein Neustart ist nicht erforderlich.

>[!NOTE]
>
>In der Web-Konsole durchgeführte Änderungen werden im Repository als [Konfigurationsdateien](#osgi-configuration-with-configuration-files) gespeichert. Diese können in Inhaltspaketen zur Wiederverwendung in weiteren Installationen enthalten sein.

>[!NOTE]
>
>In der Webkonsole beziehen sich alle Beschreibungen, in denen Standardeinstellungen erwähnt werden, auf die Sling-Standardeinstellungen.
>
>Adobe Experience Manager verfügt über eigene Standardwerte. Deshalb können die eingestellten Standardwerte von den in der Konsole dokumentierten abweichen.

So aktualisieren Sie eine Konfiguration mit der Web-Konsole:

1. Zugriff auf **Konfiguration** Registerkarte der Web-Konsole durch:

   * Öffnen Sie die Web-Konsole über den Link im Menü **Tool > Vorgänge**. Nach der Anmeldung in der Konsole können Sie dieses Dropdown-Menü verwenden:

      **OSGi >**

   * Die direkte URL, zum Beispiel:

      `http://localhost:4502/system/console/configMgr`
   Eine Liste wird angezeigt. 

1. Wählen Sie das Bundle aus, das Sie konfigurieren möchten, indem Sie eine dieser Optionen auswählen:

   * Klicken Sie auf das Symbol **Bearbeiten** für dieses Bundle.
   * Klicken Sie auf **Name** des Bundles

1. Ein Dialogfeld wird geöffnet. Hier können Sie nach Bedarf Änderungen vornehmen. Beispielsweise können Sie für die **Protokollebene** `INFO` festlegen:

   ![chlimage_1-140](assets/chlimage_1-140.png)

   >[!NOTE]
   >
   >Aktualisierungen werden im Repository als [Konfigurationsdateien](#osgi-configuration-with-configuration-files) gespeichert. Um diese zu einem späteren Zeitpunkt zu finden (z. B. um sie in einem Inhaltspaket in einer anderen Instanz einzuschließen), sollten Sie sich die persistente Identität ( `PID`) notieren.

1. Klicken Sie auf **Speichern**.

   Ihre Änderungen werden unmittelbar auf die relevante OSGi-Konfiguration des aktuellen Systems angewendet. Es ist kein Neustart erforderlich. 

   >[!NOTE]
   >
   >Sie können jetzt die damit verbundenen [Konfigurationsdateien](#osgi-configuration-with-configuration-files) suchen, um sie beispielsweise in ein Inhaltspaket zur Verwendung in einer anderen Instanz einzuschließen.

## OSGi-Konfiguration mit Konfigurationsdateien {#osgi-configuration-with-configuration-files}

Mit der Web-Konsole durchgeführte Konfigurationsänderungen werden im Repository als Konfigurationsdateien ( `.config`) hier gespeichert:

`/apps`

Diese können in Inhaltspaketen eingeschlossen und in anderen Instanzen wiederverwendet werden.

>[!NOTE]
>
>Das Format der Konfigurationsdateien ist sehr spezifisch. Weitere Informationen finden Sie in der [Sling Apache-Dokumentation](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format).
>
>Aus diesem Grund wird empfohlen, die Konfigurationsdatei zu erstellen und zu verwalten, indem Sie tatsächliche Änderungen in der Web-Konsole vornehmen.

Die Web-Konsole zeigt nicht an, wo im Repository Ihre Änderungen gespeichert wurden. Sie kann jedoch leicht gefunden werden:

1. Erstellen Sie die Konfigurationsdatei durch [Erstmalige Änderung an der Web-Konsole](#osgi-configuration-with-the-web-console).
1. Öffnen Sie CRXDE Lite.
1. Im **Instrumente** Menüauswahl **Abfrage ...** .
1. Führen Sie eine Abfrage vom **Typ** `SQL` durch, um nach der PID der Konfiguration zu suchen, die Sie aktualisiert haben.

   Beispiel: **Apache Felix OSGi Management Console** hat den Persistent Identifier (PID):

   `org.apache.felix.webconsole.internal.servlet.OsgiManager`

   Die SQL-Abfrage könnte also wie folgt lauten:

   ```shell
   select * from nt:base where jcr:path like '/apps/%' and contains(*, 'org.apache.felix.webconsole.internal.servlet.OsgiManager')
   ```

1. Der Konfigurationsdatei-Knoten wird angezeigt.

   Für das obige Beispiel:

   `/apps/system/config/org.apache.felix.webconsole.internal.servlet.OsgiManager.config`

   >[!CAUTION]
   >
   >Sie können diese Datei öffnen, um Ihre Änderungen anzuzeigen. Um Tippfehler zu vermeiden, wird jedoch empfohlen, tatsächliche Änderungen mit der Konsole vorzunehmen.

1. Sie können jetzt ein Inhaltspaket erstellen, das diesen Knoten enthält, und nach Bedarf für Ihre anderen Instanzen verwenden.

## OSGi-Konfiguration im Repository {#osgi-configuration-in-the-repository}

Zusätzlich zur Verwendung der Web-Konsole können Sie auch Konfigurationsdetails im Repository definieren. Auf diese Weise können Sie Ihre verschiedenen Ausführungsmodi einfach konfigurieren.

Diese Konfigurationen werden vorgenommen, indem `sling:OsgiConfig`-Knoten im Repository erstellt werden, auf die das System verweist. Diese Knoten spiegeln die OSGi-Konfigurationen wider und bilden eine Benutzeroberfläche für sie. Um die Konfigurationsdaten zu aktualisieren, aktualisieren Sie die Knoteneigenschaften.

Wenn Sie die Konfigurationsdaten im Repository ändern, werden die Änderungen sofort auf die entsprechende OSGi-Konfiguration angewendet, so als ob die Änderungen über die Web-Konsole vorgenommen worden wären, mit den entsprechenden Validierungs- und Konsistenzprüfungen. Dies gilt auch für das Kopieren einer Konfiguration von `/libs/` nach `/apps/`.

Da derselbe Konfigurationsparameter an mehreren Orten gespeichert werden kann, geht das System folgendermaßen vor:

* nach allen Knoten des Typs `sling:OsgiConfig` sucht.
* Es filtert nach dem Dienstnamen;
* Es filtert nach dem Ausführungsmodus.

>[!NOTE]
>
>Lesen Sie auch [wie Sie eine Repository-basierte Konfiguration nur für eine bestimmte Instanz definieren](https://helpx.adobe.com/experience-manager/kb/RunModeDependentConfigAndInstall.html).

### Hinzufügen einer neuen Konfiguration zum Repository {#adding-a-new-configuration-to-the-repository}

#### Wissenswertes {#what-you-need-to-know}

Um dem Repository eine neue Konfiguration hinzuzufügen, müssen Sie Folgendes wissen:

1. Die **Persistente Identität** (PID) des Services.

   Referenzieren Sie das Feld **Konfigurationen** in der Web-Konsole. Der Name wird in Klammern hinter dem Bundle-Namen angezeigt (oder in den **Konfigurationsinformationen** am unteren Seitenrand).

   Erstellen Sie beispielsweise einen Knoten `com.day.cq.wcm.core.impl.VersionManagerImpl.` zum Konfigurieren von **AEM WCM-Versions-Manager**.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Ob ein bestimmter [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) erforderlich ist. Erstellen Sie den Ordner:

   * `config` – für alle Ausführungsmodi
   * `config.author` – für die Autorenumgebung
   * `config.publish` – für die Veröffentlichungsumgebung
   * `config.<run-mode>` – soweit erforderlich

1. Ob eine **Konfiguration** oder eine **Werkskonfiguration** nötig ist.
1. Die einzelnen Parameter, die konfiguriert werden müssen, einschließlich etwaiger vorhandener Parameterdefinitionen, die neu erstellt werden müssen.

   Referenzieren Sie das einzelne Parameterfeld in der Web-Konsole. Der Name wird für jeden Parameter in Klammern angezeigt.

   Erstellen Sie beispielsweise eine Eigenschaft
   `versionmanager.createVersionOnActivation`, um **Version bei Aktivierung erstellen** zu konfigurieren.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Gibt es bereits eine Konfiguration in `/libs`? Um alle Konfigurationsknoten in Ihrer Instanz aufzulisten, senden Sie über das **Abfrage**-Tool in CRXDE Lite die folgende SQL-Abfrage:

   `select * from sling:OsgiConfig`

   Wenn dies der Fall ist, kann diese Konfiguration nach ` /apps/<yourProject>/` kopiert und dann am neuen Ort angepasst werden.

#### Erstellen der Konfiguration im Repository {#creating-the-configuration-in-the-repository}

Um die neue Konfiguration zum Repository hinzuzufügen, gehen Sie folgendermaßen vor:

1. Navigieren Sie mithilfe der CRXDE Lite zu:

   ` /apps/<yourProject>`

1. Wenn der Ordner noch nicht vorhanden ist, erstellen Sie den `config`-Ordner ( `sling:Folder`):

   * `config` – anwendbar auf alle Ausführungsmodi
   * `config.<run-mode>` – für einen bestimmten Ausführungsmodus

1. Erstellen Sie unter diesem Ordner einen Knoten:

   * Typ: `sling:OsgiConfig`
   * Name: die persistente Identität (PID),

      Für den AEM WCM-Versions-Manager verwenden Sie z. B. `com.day.cq.wcm.core.impl.VersionManagerImpl`
   >[!NOTE]
   >
   >Wenn Sie eine Werkskonfiguration durchführen, hängen Sie an den Namen `-<identifier>` an.
   >
   >Wie in: `org.apache.sling.commons.log.LogManager.factory.config-<identifier>`
   >
   >Wobei `<identifier>` durch einen freien Text ersetzt wird, den Sie eingeben (müssen), um die Instanz zu identifizieren (diese Information darf nicht weggelassen werden); Beispiel:
   >
   >`org.apache.sling.commons.log.LogManager.factory.config-MINE`

1. Erstellen Sie für jeden Parameter, den Sie konfigurieren möchten, eine Eigenschaft für diesen Knoten:

   * Name: den Parameternamen, wie in der Web-Konsole angezeigt; wird der Name in Klammern am Ende der Feldbeschreibung angezeigt. Für `Create Version on Activation` verwenden sie z. B. `versionmanager.createVersionOnActivation`
   * Typ: entsprechend 
   * Wert: nach Bedarf.

   Sie müssen nur Eigenschaften für die Parameter erstellen, die Sie konfigurieren möchten. Andere verwenden weiterhin die von AEM festgelegten Standardwerte.

1. Speichern Sie alle Änderungen.

   Änderungen werden angewendet, sobald der Knoten aktualisiert wird, indem der Dienst neu gestartet wird (wie bei Änderungen in der Webkonsole).

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.

>[!CAUTION]
>
>Der vollständige Pfad einer Konfiguration muss korrekt sein, damit er beim Start gelesen werden kann.

## Konfigurationsdetails {#configuration-details}

### Auflösungsreihenfolge beim Start {#resolution-order-at-startup}

Die folgende Rangfolge wird verwendet:

1. Repository-Knoten unter `/apps/*/config...`, entweder vom Typ `sling:OsgiConfig` oder mit Eigenschaftsdateien.

1. Repository-Knoten vom Typ `sling:OsgiConfig` unter `/libs/*/config...`. (vorgefertigte Definitionen).

1. Alle `.config`-Dateien aus `<*cq-installation-dir*>/crx-quickstart/launchpad/config/...`. im lokalen Dateisystem.

Dies bedeutet, dass eine generische Konfiguration in `/libs` durch eine projektspezifische Konfiguration in `/apps` maskiert werden kann.

### Auflösungsreihenfolge zur Laufzeit {#resolution-order-at-runtime}

Konfigurationsänderungen, die während der Ausführung des Triggers vorgenommen werden, führen zu einer Neuladung mit der geänderten Konfiguration.

Dann gilt die folgende Rangfolge:

1. Die Änderung einer Konfiguration in der Web-Konsole wird sofort wirksam, da sie zur Laufzeit Vorrang hat.
1. Die Änderung einer Konfiguration in `/apps` tritt sofort in Kraft.
1. Die Änderung einer Konfiguration in `/libs` tritt sofort in Kraft, außer sie wird durch eine Konfiguration in `/apps` maskiert.

### Auflösung mehrerer Ausführungsmodi {#resolution-of-multiple-run-modes}

Für Ausführungsmodusspezifische Konfigurationen können mehrere Ausführungsmodi kombiniert werden. Sie können beispielsweise Konfigurationsordner im folgenden Stil erstellen:

`/apps/*/config.<runmode1>.<runmode2>/`

Konfigurationen in derartigen Ordnern werden angewendet, wenn alle Ausführungsmodi mit einem beim Start definierten Ausführungsmodus übereinstimmen.

Beispiel: Wenn eine Instanz mit den Ausführungsmodi `author,dev,emea` gestartet wurde, werden die Konfigurationsknoten in `/apps/*/config.emea`, `/apps/*/config.author.dev/` und `/apps/*/config.author.emea.dev/` angewendet, während die Konfigurationsknoten in `/apps/*/config.author.asean/` und `/config/author.dev.emea.noldap/` nicht angewendet werden.

Wenn mehrere Konfigurationen für dieselbe PID anwendbar sind, wird die Konfiguration mit der höchsten Anzahl an passenden Ausführungsmodi angewendet.

Wenn beispielsweise eine Instanz mit den Ausführungsmodi gestartet wurde `author,dev,emea`, und beide `/apps/*/config.author/` und `/apps/*/config.emea.author/` Konfiguration für\
`com.day.cq.wcm.core.impl.VersionManagerImpl`, die Konfiguration in `/apps/*/config.emea.author/` angewendet werden.

Die Granularität dieser Regel liegt auf PID-Ebene.\
Es ist nicht möglich, für dieselbe PID einige Eigenschaften in `/apps/*/config.author/` und spezifischere in `/apps/*/config.emea.author/` zu definieren.\
Die Konfiguration mit der höchsten Anzahl von übereinstimmenden Ausführungsmodi tritt für die gesamte PID in Kraft. 

### Standardkonfigurationen {#standard-configurations}

Die folgende Liste zeigt eine kleine Auswahl der verfügbaren Konfigurationen (in einer Standardinstallation) im Repository:

* Autor – AEM WCM-Filter:

   `libs/wcm/core/config.author/com.day.cq.wcm.core.WCMRequestFilter`

* Veröffentlichung – AEM WCM-Filter:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.WCMRequestFilter`

* Veröffentlichung – AEM WCM-Seitenstatistiken:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.stats.PageViewStatistics`

>[!NOTE]
>
>Da diese Konfigurationen in `/libs` gespeichert sind, dürfen sie nicht direkt bearbeitet werden, sondern müssen vor der Anpassung in Ihren Anwendungsbereich (`/apps`) kopiert werden.

Um alle Konfigurationsknoten in Ihrer Instanz aufzulisten, senden Sie über die **Abfrage**-Funktion in CRXDE Lite die folgende SQL-Abfrage:

`select * from sling:OsgiConfig`

### Persistenz von Konfigurationen {#configuration-persistence}

* Wenn Sie eine Konfiguration über die Web-Konsole ändern, wird sie (normalerweise) über folgenden Pfad in das Repository geschrieben:

   `/apps/{somewhere}`

   * Das standardmäßige `{somewhere}` ist `system/config`, sodass die Konfiguration in diesen Pfad geschrieben wird:

      `/apps/system/config`

   * Wenn Sie jedoch eine Konfiguration bearbeiten, die ursprünglich von einem anderen Ort im Repository stammte, zum Beispiel:

      /libs/foo/config/someconfig

      dann wird die aktualisierte Konfiguration unter dem ursprünglichen Speicherort geschrieben. Beispiel:

      `/apps/foo/config/someconfig`

* Einstellungen, die vom `admin` geändert werden, werden in `*.config`-Dateien gespeichert, und zwar unter:

   ```
      /crx-quickstart/launchpad/config
   ```

   * Dies ist der private Datenbereich der OSGi-Konfigurationsverwaltung. Er enthält alle Konfigurationsdetails, die durch `admin` spezifiziert wurden, und zwar unabhängig davon, wie sie in das System gelangt sind. 
   * Dies ist ein Implementierungsdetails und Sie dürfen dieses Verzeichnis nie direkt bearbeiten.
   * Es ist jedoch nützlich, den Speicherort dieser Konfigurationsdateien zu kennen, damit Kopien für eine Sicherung und/oder mehrere Installationen erstellt werden können:

      * Apache Felix OSGi-Management Console

         `../crx/org/apache/felix/webconsole/internal/servlet/OsgiManager.config`

      * CRX Sling Client Repository

         `../com/day/crx/sling/client/impl/CRXSlingClientRepository/<pid-nr>.config`

>[!CAUTION]
>
>Die Ordner oder Dateien an diesem Speicherort dürfen Sie ***niemals*** bearbeiten:
>
>`/crx-quickstart/launchpad/config`
