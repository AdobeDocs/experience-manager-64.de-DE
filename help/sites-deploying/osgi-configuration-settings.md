---
title: OSGi-Konfigurationseinstellungen
seo-title: OSGi Configuration Settings
description: In diesem Artikel werden die OSGi-Konfigurationseinstellungen (aufgeführt gemäß Bundle) beschrieben, die für die Projektimplementierung relevant sind. Die Liste dient als Leitlinie und ist nicht vollständig.
seo-description: This article details the OSGi configuration settings (listed according to bundle) that are relevant to project implementation. The list acts as a guideline and it is not exhaustive.
uuid: 817de76e-7ba6-4502-94f5-09046b878cfb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ccddb2cd-8e67-43aa-a495-8996ad349761
feature: Configuring
exl-id: 5c07c773-53a3-41fd-860a-da0cb14f8bc6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3496'
ht-degree: 71%

---

# OSGi-Konfigurationseinstellungen{#osgi-configuration-settings}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von AEM. Es wird zur Steuerung der zusammengesetzten AEM-Bundles und ihrer Konfiguration verwendet.

OSGi &quot;*bietet die standardisierten Grundbausteine, die die Erstellung von Anwendungen aus kleinen, wiederverwendbaren und kollaborativen Komponenten ermöglichen. Diese Komponenten können zu einem Programm zusammengefügt und bereitgestellt werden*&quot;.

Dies ermöglicht die einfache Verwaltung von Bundles, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente (siehe [OSGi-Spezifikation](https://docs.osgi.org/specification/)) ist in einem der Bundles enthalten. Beim Arbeiten mit AEM gibt es mehrere Methoden zum Verwalten der Konfigurationseinstellungen für solche Bundles. see [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md) für weitere Details und empfohlene Vorgehensweisen.

Die folgenden OSGi-Konfigurationseinstellungen (aufgeführt gemäß Bundle) sind für die Projektimplementierung relevant. Nicht alle aufgeführten Einstellungen müssen angepasst werden. Einige werden nur zum besseren Verständnis von AEM erwähnt.

>[!CAUTION]
>
>Die Liste soll als Leitlinie dienen und ist nicht vollständig. Es werden nicht alle Bundles aufgelistet und auch nicht alle Parameter für einige der Bundles, die vorhanden sind.
>
>Die erforderliche Konfiguration variiert von Projekt zu Projekt.
>
>In der Web-Konsole finden Sie verwendete Werte und detaillierte Informationen zu Parametern.

>[!NOTE]
>
>Das OSGi Configuration Diff-Tool, Teil der [AEM Tools](https://helpx.adobe.com/experience-manager/kb/tools/aem-tools.html), kann verwendet werden, um die standardmäßigen OSGi-Konfigurationen aufzulisten.

>[!NOTE]
>
>Für spezifische Funktionsbereiche in AEM sind möglicherweise weitere Bundles erforderlich. In solchen Fällen können Sie die Konfigurationsdetails der Seite entnehmen, die sich auf die entsprechende Funktion bezieht.

**AEM Replikations-Ereignis-Listener** Konfigurieren Sie:

* Die **Ausführungsmodi**, in denen Replikationsereignisse an Listener verteilt werden. Wenn beispielsweise als Autor definiert, ist dies das System, das die Replikation „initiiert“.

* Der Ausführungsmodus **veröffentlichen** muss hinzugefügt werden, wenn der Projekt-Code Replikationsereignisse (Rückwärtsreplikation) in einer Veröffentlichungsumgebung verarbeitet. Dies ist beispielsweise der Fall, wenn der Dispatcher zum Leeren aus der Veröffentlichungsumgebung verwendet wird oder wenn eine standardmäßige Replikation zuf anderen Veröffentlichungsinstanzen erfolgt.

**AEM-Repository-Änderungs-Listener** Konfigurieren Sie:

* Die **Pfade**, Speicherorte, an denen auf Repository-Ereignisse, die für die Verteilung bereit sind, gelauscht wird.

**CRX Sling Client Repository** Konfigurieren Sie den Zugriff auf das zugrunde liegende Inhalts-Repository.

* Das **Administratorkennwort** sollte nach der Installation geändert werden, um die [Sicherheit](/help/sites-administering/security-checklist.md) Ihrer Instanz zu gewährleisten.

* Andere Änderungen sollten nicht erforderlich sein und müssen mit Vorsicht erfolgen, da sie den Zugriff auf das Repository beeinträchtigen können.

**Apache Felix OSGi Management Console:** Konfigurieren Sie:

* **Plug-ins**: die Hauptnavigationselemente (Konsolen-Plug-ins), die als oberste Menüelemente in der **Apache Felix Web Management Console** verfügbar sein sollen. Deaktivieren Sie alle nicht benötigten Elemente, da sie sonst Platz und Ressourcen verbrauchen.

>[!CAUTION]
>
>Konfigurieren Sie Folgendes:
>
>**Benutzername** und **Kennwort**: die Anmeldedaten für den Zugriff auf die Apache Felix Web Management Console.\
>Das Kennwort muss nach der ersten Installation geändert werden, damit die [Sicherheit](/help/sites-administering/security-checklist.md) Ihrer Instanz gewährleistet ist.

>[!NOTE]
>
>Nehmen Sie diese Konfiguration in der Felix Console vor, die zum Starten erforderlich ist – bevor das Repository verfügbar ist.

**Apache Sling Customizable Request Data Logger** Konfigurieren Sie:

* **Name der Protokollfunktion** und **Protokollformat** für den Speicherort und das Format von Anforderungen und Zugriffsprotokollierung (Standard: `request.log`). Diese Protokolldatei ist sehr wichtig, wenn Sie die Leistung analysieren oder auf die Web-Kette bezogene Funktionen debuggen möchten.

   Dieser ist gepaart mit dem Apache Sling Request Logger.

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Eventing Thread Pool** Konfigurieren Sie:

* **Minimale Poolgröße** und **Maximale Poolgröße**, die Größe des Pools, der zum Speichern von Ereignis-Threads verwendet wird.

* **Warteschlangengröße**, die maximale Größe der Thread-Warteschlange, wenn der Pool erschöpft ist.

   Der empfohlene Wert lautet `-1`, da dies die Warteschlange auf unbegrenzt festlegt. Wenn ein Limit festgelegt ist, kann es bei Überschreitung zu Verlusten kommen.

* Das Ändern dieser Einstellungen kann die Leistung in Szenarien mit einer hohen Anzahl von Ereignissen verbessern, z. B. bei starker Nutzung von AEM DAM oder Workflows.
* Für Ihr Szenario spezifische Werte sollten mithilfe von Tests festgelegt werden.
* Diese Einstellungen können sich auf die Leistung Ihrer Instanz auswirken. Ändern Sie sie daher nicht ohne Grund und nur nach reiflicher Überlegung.

**Apache Sling GET Servlet** Konfigurieren Sie einige Aspekte des Renderings:

* **Auto Index** zum Aktivieren/Deaktivieren der Verzeichnisausgabe beim Browsen.
* **Aktivieren** (oder deaktivieren) Standardausgabeformate wie **HTML**, **Nur Text**, **JSON** oder **XML**.

   Sie sollten JSON nicht deaktivieren.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Apache Sling Java Script Handler** Konfigurieren Sie Einstellungen für die Kompilierung von Java-Dateien als Skripte (Servlets).

Bestimmte Einstellungen können die Leistung beeinträchtigen. Deaktivieren Sie diese, falls möglich, insbesondere für Produktionsinstanzen.

* S **Quell-VM** und **Target VM**, definieren Sie die JDK-Version als die als LaufzeitjVM verwendete.

* für Produktionsinstanzen:

   * Deaktivieren Sie **Generate Debug Info**.

**Apache Sling JCR Installer** Diese Parameter müssen wahrscheinlich nicht konfiguriert werden. Es ist jedoch nützlich, diese beim Entwickeln oder Debuggen zu kennen. Beispielsweise kann es nützlich sein, die Installationsordner ein- oder auszuchecken oder ein Paket zu erstellen.

* **Name des Installationsordners regexp** und **Maximale Hierarchietiefe von Installationsordnern** - Geben Sie an, wo und in welcher Tiefe Repository-Ordner nach Ressourcen gesucht werden, die installiert werden sollen. Wenn ein Platzhalter verwendet wird (wie in .&amp;ast;/install) werden alle passenden Treffer durchsucht, z. B. `/libs/sling/install` und `/libs/cq/core/install`.

* **Search Path** listet die Pfade auf, in denen jcrinstall nach zu installierenden Ressourcen sucht, und eine Ziffer, die den Gewichtungsfaktor für den Pfad angibt.

**Apache Sling Job Event Handler** Konfigurieren Sie Parameter, die die Auftragsplanung verwalten:

* **Wiederholungsintervall**, **Maximale Wiederholungen**, **Maximale Anzahl paralleler Aufträge**, **Wartezeit für Bestätigung**, unter anderem.

* Eine Änderung dieser Einstellungen kann die Leistung in Szenarien mit einer hohen Anzahl von Aufträgen verbessern. z. B. starke Nutzung von AEM DAM und Workflows.
* Für Ihr Szenario spezifische Werte sollten mithilfe von Tests festgelegt werden.
* Ändern Sie sie daher nicht ohne Grund und nur nach reiflicher Überlegung.

**Apache Sling JSP Script Handler** Konfigurieren Sie leistungsrelevante Einstellungen für den JSP-Skript-Handler. Um die Leistung zu verbessern, sollten Sie so weit wie möglich deaktivieren.

Insbesondere für Produktionsinstanzen:

* Deaktivieren Sie **Generate Debug Info**.
* disable **Generiertes Java beibehalten**
* Deaktivieren Sie **Mapped Content**.
* disable **Anzeigen von Quellfragmenten**

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Apache Sling Logging Configuration** Konfigurieren Sie:

* **Log Level** und **Log File** definieren den Speicherort und die Protokollebene der zentralen Protokollierungskonfiguration (error.log). Als Ebene kann `DEBUG`, `INFO`, `WARN`, `ERROR` und `FATAL` festgelegt werden.

* **Anzahl Protokolldateien** und **Schwellenwert für Protokolldateien** , um die Größe und Versionsrotation der Protokolldatei zu definieren.

* **Nachrichtenmuster** definiert das Format der Protokollmeldungen.

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md#global-logging) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Logging Logger Configuration (Factory Configuration)** Konfigurieren Sie:

* **Log Level**, **Log File** und **Message Format** definieren Details in den Protokolldateien und -meldungen.

* **Logger** gibt die Kategorie an, z. B. nur Protokollierungen für com.day.cq.

* Durch Verwendung von **Factory-Konfigurationen** können beliebig viele zusätzliche Konfigurationen hinzugefügt werden, um die verschiedenen erforderlichen Protokollebenen und Kategorien zu berücksichtigen.
* Solche Konfigurationen sind während der Entwicklung hilfreich. Beispielsweise um TRACE-Meldungen für einen bestimmten Dienst in einer bestimmten Protokolldatei zu protokollieren.
* Solche Konfigurationen sind in einer Produktionsumgebung hilfreich. Sie können beispielsweise Nachrichten über einen bestimmten Dienst in einer einzelnen Protokolldatei protokollieren, um die Überwachung zu erleichtern.

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Logging Writer Configuration (Factory Configuration)** Konfigurieren Sie:

* **Log File** gibt an, dass eine Protokolldatei vorhanden ist.
* **Number of Log Files** gibt die Versionsrotation an.

* Der Verfasser kann von **Apache Sling Logging Logger**-Konfigurationen verwendet werden.

* Solche Konfigurationen sind während der Entwicklung hilfreich. Beispielsweise um TRACE-Meldungen für einen bestimmten Dienst in einer bestimmten Protokolldatei zu protokollieren.
* Solche Konfigurationen sind in einer Produktionsumgebung hilfreich. Sie können beispielsweise Nachrichten über einen bestimmten Dienst in einer einzelnen Protokolldatei protokollieren, um die Überwachung zu erleichtern.

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Main Servlet** Konfigurieren Sie:

* **Number of Calls per Request** und **Recursion Depth**, um das System vor unendlichen Rekursionen und übermäßigen Skript-Aufrufen zu schützen.

**Apache Sling MIME Type Service** Konfigurieren Sie:

* **MIME-Typen**, um die für Ihr Projekt erforderlichen Typen hinzuzufügen. Dadurch kann eine `GET`-Anforderung einer Datei die richtige Kopfzeile für den Inhaltstyp zum Verknüpfen von Dateityp und Anwendung festlegen.

**Apache Sling Referrer Filter** Um bekannte Sicherheitsprobleme mit Site-übergreifenden Anfragefälschungen in CRX WebDAV und Apache Sling zu beheben, müssen Sie den Referrer-Filter konfigurieren.

Der Referrer-Filter-Service ist ein OSGi-Service, mit dem Sie Folgendes konfigurieren können:

* welche HTTP-Methoden gefiltert werden sollen
* Ob eine leere Referrer-Kopfzeile zulässig ist
* Eine Zulassungsliste von Servern, die zusätzlich zum Serverhost zugelassen werden sollen.

Weitere Informationen finden Sie unter [Sicherheitsprüfliste – Probleme mit Site-übergreifenden Anforderungsfälschungen](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery).

>[!NOTE]
>
>Für den Apache Sling Referrer-Filter muss ein Quick Fix-Paket installiert werden.

**Apache Sling Request Logger** Konfigurieren Sie:

* unterschiedliche Parameter, die festlegen, wie Anforderungen zugeordnet werden.
* **Enable Request Log** zum Aktivieren oder Deaktivieren.

* **Zugriffsprotokoll aktivieren**, um zu aktivieren oder zu deaktivieren.

Dies wird mit dem Apache Sling Customizable Request Data Logger gepaart.

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Resource Resolver Factory** Konfigurieren Sie zentrale Aspekte der Sling-Ressourcenauflösung:

* **Resource Search Path**(s) zum Hinzufügen beliebiger Projektpfade (`/libs` oder `/apps` dürfen nicht entfernt werden).

* **Virtual URLs** zum Definieren der Vanity-URL-Zuweisungen.

* **URL Mappings** zum Definieren beliebiger Aliasse, beispielsweise von `/content` zu `/`.

* **Mapping Location**, die Zuordnungskonfiguration, die in `/etc/map` externalisiert ist.

* Verwenden Sie die lokale Installation (z. B. `http://localhost:4502/system/console/jcrresolver`), um herauszufinden, welcher Ressourcenkonfliktlöser aktiv ist.

Weitere Informationen finden Sie unter [https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution.](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution)

>[!CAUTION]
>
>Insbesondere müssen diese Optionen im Repository konfiguriert werden.
>
>Andernfalls an **URL-Zuordnungen** Die Verwendung der Felix-Konsole kann beim nächsten Start durch AEM überschrieben werden.

**Apache Sling Servlet/Script Resolver and Error Handler** Das Sling-Servlet und der Skript-Resolver haben mehrere Aufgaben:

1. Sie werden als `ServletResolver` verwendet, die das Servlet oder Skript zum Abwickeln der Anforderung auswählen.

1. Sie dienen als `SlingScriptResolver`.

1. Sie sind für die Fehlerbehebung zuständig, indem sie die `ErrorHandler`-Schnittstelle implementieren und dabei denselben Algorithmus für Servlets und Skripts auswählen, der auch für Servlets und Skripts für die Anforderungsabwicklung verwendet wird.

Es können verschiedene Parameter festgelegt werden, darunter:

* **Ausführungspfade** listet die Pfade auf, nach ausführbaren Skripten zu suchen; durch die Konfiguration bestimmter Pfade können Sie einschränken, welche Skripte ausgeführt werden können. Falls kein Pfad konfiguriert ist, wird der Standard verwendet (`/` = Stammpfad) und es werden alle Skripts ausgeführt.

   Falls ein konfigurierter Pfadwert mit einem Schrägstrich endet, wird die gesamte Unterstruktur durchsucht. Ohne einen solchen Schrägstrich wird das Skript nur ausgeführt, wenn es eine exakte Übereinstimmung ist.

* **Skript-Benutzer** - Diese optionale Eigenschaft kann das Repository-Benutzerkonto angeben, das zum Lesen der Skripte verwendet wird. Falls kein Konto angegeben ist, wird standardmäßig das `admin`-Benutzerkonto verwendet.

* **Default Extensions**: Die Liste der Erweiterungen, für die das Standardverhalten verwendet wird. Dies bedeutet, dass das letzte Pfadsegment des Ressourcentyps als Skriptname verwendet werden kann.

* Definieren Sie den **Schriftenpfad**, in dem nach projektspezifischen Schriftarten gesucht werden soll.

   Beispiel: `/apps/myapp/fonts`.

**Apache HTTP Components Proxy Configuration** Proxy-Konfiguration für vom Apache-HTTP-Client bei einer HTTP-Anforderung verwendeten Code; zum Beispiel beim Replizieren.

Nehmen Sie beim Erstellen einer neuen Konfiguration keine Änderungen an der Werkskonfiguration vor, sondern erstellen Sie stattdessen eine neue Werkskonfiguration für diese Komponente mithilfe des Konfigurationsmanagers, der hier verfügbar ist: **http://localhost:4502/system/console/configMgr/**. Die Proxy-Konfiguration ist in **org.apache.http.proxyconfigurator** verfügbar.

>[!NOTE]
>
>In AEM 6.0 und früheren Versionen wurde der Proxy im Day Commons HTTP Client konfiguriert. Ab AEM Version 6.1 wurde die Proxy-Konfiguration in die &quot;Apache HTTP Components Proxy Configuration&quot;statt in die &quot;Day Commons HTTP Client&quot;-Konfiguration verschoben.

**Day CQ Antispam** Konfigurieren Sie den verwendeten Anti-Spam-Dienst (Akismet). Dazu müssen Sie Folgendes registrieren:

* **Provider**
* **API-Schlüssel**
* **Registrierte URL**

**Adobe Granite HTML Library Manager** Konfigurieren Sie dies, um die Verarbeitung von Client-Bibliotheken (css oder js) zu steuern, einschließlich der Anzeige der zugrunde liegenden Struktur.

* Für Produktionsinstanzen:

   * Aktivieren Sie **Minimieren** (um CRLF- und Leerzeichen zu entfernen).
   * Aktivieren Sie **gzip** (damit Dateien ins gzip-Format komprimiert und mit einer Anfrage aufgerufen werden können).
   * Deaktivieren Sie **Debuggen**.
   * Deaktivieren Sie **Zeitplanung**.

* Für die JS-Entwicklung (insbesondere beim Firebugging/Debugging):

   * disable **Minimieren**
   * enable **Debuggen** , um die Dateien für das Debugging und die Verwendung mit Firebug zu trennen.
   * enable **Zeit** im Fall des Interesses an einem Zeitplan.
   * enable **Debuggen** -Konsole, um die Protokollmeldungen der JS-Konsole anzuzeigen.

>[!CAUTION]
>
>Wenn Sie die Einstellung für **Minify** oder **Gzip** ändern, müssen Sie auch die Inhalte des Clientlibs-Cache löschen. Mehr Details finden Sie im [Knowledge-Base-Artikel](https://helpx.adobe.com/de/experience-manager/kb/How-to-force-a-recompilation-of-all-Sling-scripts-jsps-java-sightly-on-AEM-6-4.html).

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Day CQ HTTP Header Authentication Handler** Systemweite Einstellungen für die grundlegende Authentifizierungsmethode der HTTP-Anfrage.

Bei Verwendung von [geschlossene Benutzergruppen](/help/sites-administering/cug.md) Sie können (unter anderem) Folgendes konfigurieren:

* **HTTP-Bereich**
* Die **Standard-Anmeldeseite**

**Day CQ Link Checker Service** Überprüfen und konfigurieren Sie bei Bedarf Folgendes:

* **Scheduler Period**: definiert das Intervall, in dem externe Links automatisch überprüft werden.

* Überprüfen **Schlechtes Linktoleranzintervall** für den Zeitraum, nach dem ein nicht erfolgreicher externer Link als fehlerhaft betrachtet wird.
* **Link Check Override Patterns**, um alle Pfade zu definieren, die von der Linküberprüfung ausgeschlossen werden sollen.

**Day CQ Link Checker Task** Konfigurieren Sie die Einstellungen für eine Aufgabe mit einem einzelnen Link-Checker (eine Aufgabe, die einen externen Link überprüft):

* Überprüfen Sie die unter **Good Link Test Interval** und **Bad Link Test Interval** festgelegten Intervalle.

* Die diversen Parameter, die sich auf Proxys für den Internetzugriff und NTLM beziehen und beim Überprüfen eines Links für den externen Zugriff benötigt werden.

**Day CQ Mail Service** Konfigurieren Sie den Host-Namen und die Zugriffsdetails für den E-Mail-Server. Einzelheiten finden Sie im Abschnitt Konfigurieren des E-Mail-Dienstes.

**Day CQ MCM Newsletter** Konfigurieren Sie die verschiedenen Einstellungen, die für den Newsletter verwendet werden.

**Day CQ Root Mapping** Konfigurieren Sie:

* **Target Path**, um festzulegen, wohin eine an „`/`“ gerichtete Anfrage umgeleitet wird.

Es gibt [zwei Benutzeroberflächen](/help/sites-authoring/select-ui.md) verfügbar in AEM:

* Die Touch-optimierte Benutzeroberfläche wurde eingeführt
* und die klassische Benutzeroberfläche weiterhin voll funktionsfähig ist

Mit AEM Root Mapping können Sie die Benutzeroberfläche konfigurieren, die Sie als Standard für Ihre Instanz verwenden möchten:

* So verwenden Sie die Touch-optimierte Benutzeroberfläche als Standardbenutzeroberfläche **Zielpfad** sollte auf Folgendes verweisen:

   ```
      /projects.html
   ```

* Wenn Sie die klassische Benutzeroberfläche als Standard verwenden möchten, muss der **Zielpfad** auf Folgendes verweisen:

   ```
      /welcome.html
   ```

>[!NOTE]
>
>Nach einer Standardinstallation wird die Touch-optimierte Benutzeroberfläche zur Standardbenutzeroberfläche.

**Adobe Granite SSO Authentication Handler** Konfigurieren Sie die Single Sign On (SSO)-Details. Diese werden oft bei einem Enterprise-Autoren-Setup mit LDAP benötigt.

Verschiedene Eigenschaften können konfiguriert werden: 

* **Path** Der Pfad, für den dieser Authentifizierungs-Handler aktiv ist. Wenn dieser Parameter nicht angegeben wird, ist der Authentifizierungs-Handler deaktiviert. Beispielsweise wird beim Pfad / der Authentifizierungs-Handler für das gesamte Repository verwendet.

* **Service Ranking** Der Rangfolge-Wert für den OSGi-Framework-Dienst gibt die Reihenfolge an, in der dieser Dienst aufgerufen wird. Dies ist ein 
`int`-Wert, wobei höhere Werte eine höhere Priorität angeben.


   Der Standardwert ist `0`.

* **Header Names** Die Namen von Kopfzeilen, die möglicherweise eine Benutzer-ID enthalten.

* **Cookie Names** Die Namen von Cookies, die möglicherweise eine Benutzer-ID enthalten.

* **Parameter Names** Die Namen von Anforderungsparametern, die möglicherweise eine Benutzer-ID angeben.

* **User Map** Für bestimmte Benutzer kann der aus der HTTP-Anforderung extrahierte Benutzername im Anmeldedaten-Objekt durch einen anderen Namen ersetzt werden. Die Zuordnung ist hier definiert. Wenn der Benutzername 
`admin` auf beiden Seiten der Zuordnung angezeigt wird, wird die Zuordnung ignoriert. Beachten Sie, dass das Zeichen „=“ durch ein führendes „\“ geschützt werden muss.

* **Format** Gibt das Format an, in dem die Benutzer-ID angegeben ist. Verwenden Sie:

   * `Basic`, falls die Benutzer-ID im HTTP-Standard-Authentifizierungsformat kodiert ist
   * `AsIs`, falls die Benutzer-ID im Nur-Text-Format bereitgestellt wird, oder jeder für reguläre Ausdrücke gültige Wert unverändert bzw. jeder reguläre Ausdruck verwendet werden soll

**Day CQ WCM Debug Filter** Dies ist beim Entwickeln hilfreich, da Suffixe wie ?debug=layout beim Zugriff auf eine Seite verwendet werden können. Beispielsweise stellt http://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout Layoutinformationen bereit, die für den Entwickler von Interesse sein können.

* Deaktivieren Sie diese Option bei Produktionsinstanzen, um die Leistung und Sicherheit zu gewährleisten.

**Day CQ WCM Filter** Konfigurieren Sie:

* **WCM-Modus** , um den Standardmodus zu definieren.
* Auf einer Autoreninstanz kann dieser `edit`, `disable,preview` oder `analytics` lauten.


   Auf die anderen Modi kann aus dem Sidekick zugegriffen werden. Oder das Suffix `?wcmmode=disabled` kann zum Emulieren der Produktionsumgebung verwendet werden.

* Auf einer Veröffentlichungsinstanz muss für diesen Modus `disabled` festgelegt sein, um sicherzustellen, dass keine anderen Modi zugänglich sind.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Day CQ WCM Link Checker Configurator** Konfigurieren Sie:

* **Liste der Neuschreibungskonfigurationen** um eine Liste von Speicherorten für inhaltsbasierte Linkprüfer-Konfigurationen anzugeben. Die Konfigurationen können auf dem Ausführungsmodus basieren. Dies ist wichtig, um zwischen Autoren- und Veröffentlichungsumgebungen zu unterscheiden, da die Einstellungen des Linkprüfers unterschiedlich sein können.

**Day CQ WCM Page Processor** Konfigurieren Sie:

* **Paths**, eine Liste der Speicherorte, die das System auf Seitenänderungen überwacht, bevor ein `jcr:Event` ausgelöst wird.

**Adobe Page Impressions Tracker** Konfigurieren Sie für eine Autoreninstanz Folgendes:

* **sling.auth.requirements**: legen Sie für diese Eigenschaft den Wert auf `-/libs/wcm/stats/tracker` fest.

>[!CAUTION]
>
>Diese Konfiguration ermöglicht anonyme Anfragen an den Tracking-Dienst.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Seitenimpressionen](/help/sites-deploying/configuring.md#enabling-page-impressions).

**Day CQ WCM Page Statistics** Konfigurieren Sie für eine Veröffentlichungsinstanz Folgendes:

* **URL to send data**: konfiguriert die zum Nachverfolgen der Seitenstatistiken verwendete URL (wichtig, falls eine Nachverfolgungsanforderung über den Dispatcher geleitet wird); der Standardwert lautet beispielsweise `http://localhost:4502/libs/wcm/stats/tracker`.

* **Tracking script enabled**: aktiviert (`true`) oder deaktiviert (`false`) den Einschluss der Nachverfolgungsskripts auf den Seiten. Der Standardwert ist `false`.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Seitenimpressionen](/help/sites-deploying/configuring.md#enabling-page-impressions).

**Day CQ WCM Version Manager** Steuern Sie, ob und wie Versionen in Ihrem System verwaltet werden:

* **Create Version on Activation** ist bei der Standardinstallation aktiviert.
* **Enable Purging**

* **Purge Paths**: die von einem Suchvorgang durchsuchten Pfade.
* **Implicit Versioning Paths**: die Pfade, bei denen die implizite Versionierung aktiv ist.

* **Max Version Age**: das maximale Alter (in Tagen) einer Version.

* **Max Number Versions**: die maximale Anzahl der beizubehaltender Versionen.

Weitere Informationen finden Sie unter [Löschen von Versionen](/help/sites-deploying/version-purging.md).

**Day CQ Workflow Email Notification Service** Konfigurieren Sie die E-Mail-Einstellungen für Benachrichtigungen, die von einem Workflow gesendet werden.

**CQ Rewriter HTML Parser Factory**

Steuert den HTML-Parser für den CQ-Rewriter.

* **Zusätzliche Tags zur Verarbeitung** - Sie können HTML-Tags hinzufügen oder entfernen, die vom Parser verarbeitet werden sollen. Standardmäßig werden die folgenden Tags verarbeitet: A,IMG,AREA,FORM,BASE,LINK,SCRIPT,BODY,HEAD.
* **Preserve Camel Case**: Standardmäßig wandelt der HTML-Parser Attribute in gemischter Groß-/Kleinschreibung (z. B. eBay) in Kleinschreibung (z. B. ebay) um. Sie können dies deaktivieren, um die Attribute der Binnenmajuskel-Groß-/Kleinschreibung beizubehalten. Dies ist nützlich bei der Verwendung von Frontend-Frameworks wie Angular 2.

**Day Commons JDBC Connections Pool** Konfigurieren Sie den Zugriff auf eine externe Datenbank, die als Quelle für Inhalte verwendet wird.

Dies ist eine Factory-Konfiguration, sodass mehrere Instanzen konfiguriert werden. 

**CDN Rewriter** Die Kommunikation zwischen AEM und einem CDN muss sichergestellt sein, damit Assets/Binärdateien sicher an den Endbenutzer übermittelt werden. Dies umfasst zwei Aufgaben:

* Zugriff auf die Ressource von AEM über das CDN beim ersten Mal (oder nachdem sie im Cache abgelaufen ist).
* Sicherer Zugriff auf die im CDN zwischengespeicherte Ressource, da die Anforderung nach dem Zwischenspeichern der Ressource im CDN nicht an AEM gesendet wird und alle Benutzer, die Zugriff auf diese Ressource haben, vom CDN bereitgestellt werden sollten.

AEM bietet einen Rewriter zum Neuschreiben interner Asset-URLs in externe CDN-URLs. Es schreibt Links, die an das CDN weitergegeben werden sollen, einschließlich einer JWS-Signatur, und läuft die Zeit ab, damit der Asset sicher aufgerufen werden kann. Diese Funktion wird in Autoreninstanzen verwendet.

Der Gesamtdurchsatz sieht wie folgt aus:

1. Der Benutzer authentifiziert sich bei AEM und fordert eine Seite mit Assets an.
1. Die angefragte Seite enthält ein Asset, das dem `/content/dam/geometrixx-media/articles/paladin_trailer.jpg/jcr:content/renditions/cq5dam.thumbnail.319.319.png` ähnelt.
1. Rewriter wandelt den Link in eine CDN-URL um, die eine JWS-Signatur enthält:

   `CDN_domain/content/dam/geometrixx-media/articles/paladin_trailer.jpg/_jcr_content/renditions/cq5dam.thumbnail.319.319.png?cdn_sign=JWS_SIGNATURE`

1. Der Browser des Benutzers leitet die Asset-Anforderung an den CDN-Server weiter.
1. CDN sollte so konfiguriert werden, dass die Anforderung zusammen mit dem `cdn_sign`-Parameter an AEM weitergeleitet wird.
1. Ein Authentifizierungs-Handler validiert den `cdn_sign`-Parameter und gibt das Asset an CDN zurück. Von dort wird es an den Benutzer übermittelt.

Der Fluss zwischen dem Browser des Benutzers, dem CDN und AEM sieht wie folgt aus:

![chlimage_1-118](assets/chlimage_1-118.png)

>[!NOTE]
>
>Diese Funktion ist derzeit nur für AEM-Autoreninstanzen aktiviert.

**CDNConfigServiceImpl** Bietet CDN-Konfigurationen

Sie können die CDN-Rewriter-Funktion aktivieren, indem Sie den **Domain-Namen der CDN-Verteilung** in der Konfiguration für com.adobe.cq.cdn.rewriter.impl.CDNConfigServiceImpl angeben.

Der Service enthält auch andere Konfigurationsoptionen wie das Aktivieren/Deaktivieren der CDN-Neuschreib-Funktion, Pfad-Präfixe für das Neuschreiben durch CDN, TTL-Werte und Protokolle (HTTP oder HTTPS).

**CDNRewriter** Ein Rewriter für das Neuschreiben interner Image-URLs als CDN-URLs

Der Wert **Tag Attributes** in com.adobe.cq.cdn.rewriter.impl.CDNRewriter kann so definiert werden, dass nur bestimmte Image-Links neu geschrieben werden.
