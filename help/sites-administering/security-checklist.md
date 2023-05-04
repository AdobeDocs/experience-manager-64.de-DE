---
title: Sicherheitscheckliste
seo-title: Security Checklist
description: Erfahren Sie mehr über die verschiedenen Sicherheitsüberlegungen beim Konfigurieren und Bereitstellen von AEM.
feature: Security
seo-description: Learn about the various security considerations when configuring and deploying AEM.
uuid: 8ecd0c35-249e-4f72-b7e9-97e72698b5c1
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: a91e1264-8441-42f8-aa83-1d9c983d214a
exl-id: 0be6d031-f8b8-458b-a910-ff05d2b1a155
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2866'
ht-degree: 89%

---

# Sicherheitscheckliste{#security-checklist}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Dieser Abschnitt behandelt die verschiedenen Schritte, mit denen Sie sicherstellen können, dass Ihre AEM-Installation bei der Bereitstellung sicher ist. Die Checkliste ist so konzipiert, dass sie von oben nach unten abgearbeitet werden sollte.

>[!NOTE]
>
>Weitere Informationen [ist auch über die gefährlichsten Sicherheitsbedrohungen verfügbar, die vom Open Web Application Security Project (OWASP) veröffentlicht wurden](https://www.owasp.org/index.php/OWASP_Top_Ten_Project).

>[!NOTE]
>
>Es gibt einige zusätzliche [Sicherheitsüberlegungen](/help/sites-developing/dev-guidelines-bestpractices.md#security-considerations), die in der Entwicklungsphase berücksichtig werden müssen.

## Hauptsicherheitsmaßnahmen {#main-security-measures}

### Ausführen von AEM im produktionsbereiten Modus {#run-aem-in-production-ready-mode}

Weitere Informationen finden Sie unter [Ausführen von AEM im produktionsbereiten Modus](/help/sites-administering/production-ready.md).

### Aktivieren von HTTPS für Transport Layer Security {#enable-https-for-transport-layer-security}

Die Aktivierung der HTTPS-Transportschicht (Transport Layer) in den Autoren- und Veröffentlichungsinstanzen ist obligatorisch, um eine sichere Instanz zu erhalten.

>[!NOTE]
>
>Weitere Informationen finden Sie im Abschnitt [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md).

### Installieren von Sicherheits-Hotfixes {#install-security-hotfixes}

Vergewissern Sie sich, dass Sie die neuesten [von Adobe bereitgestellten Sicherheits-Hotfixes](https://helpx.adobe.com/de/experience-manager/kb/aem63-available-hotfixes.html) installiert haben.

### Ändern von Standardkennwörtern für AEM- und OSGi Console-Administratorkonten {#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts}

Adobe empfiehlt dringend, dass Sie das Passwort für die mit allen Berechtigungen ausgestatteten [**`admin`-Konten von AEM**](#changing-the-aem-admin-password) nach der Installation ändern (in allen Instanzen).

Diese Konten beinhalten:

* Das `admin`-Konto von AEM

   Sobald Sie das Passwort für das Admin-Konto von AEM geändert haben, müssen Sie für den Zugriff auf CRX das neue Passwort verwenden.

* Das `admin`-Passwort für die OSGi-Web-Konsole

   Diese Änderung wird auch für das Admin-Konto übernommen, das für den Zugriff auf die Web-Konsole verwendet wird. Daher müssen Sie dafür dasselbe Passwort verwenden.

Diese beiden Konten nutzen separate Kontoanmeldeinformationen und die Verwendung von unterschiedlichen sicheren Passwörtern für jedes Konto ist für eine sichere Bereitstellung von entscheidender Bedeutung.

#### Ändern des AEM-Administratorkennworts {#changing-the-aem-admin-password}

Das Kennwort für das AEM-Administratorkonto kann über die Konsole für [Granite-Vorgänge – Benutzer](/help/sites-administering/granite-user-group-admin.md) geändert werden.

Dort können Sie das `admin`-Konto bearbeiten und [das Kennwort ändern](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user).

>[!NOTE]
>
>Durch das Ändern des Administratorkontos wird auch das OSGi-Web-Konsolenkonto geändert. Nachdem Sie das Administratorkonto geändert haben, sollten Sie das OSGi-Konto in etwas Anderes ändern.

#### Bedeutung der Änderung des Kennworts für die OSGi-Web-Konsole {#importance-of-changing-the-osgi-web-console-password}

Unabhängig vom `admin`-Konto von AEM kann eine Nichtänderung des Standardkennworts für die OSGi-Web-Konsole dazu führen, dass:

* Offenlegung des Servers mit einem Standardkennwort beim Start und beim Herunterfahren (was bei großen Servern mehrere Minuten dauern kann);
* Offenlegung des Servers, wenn das Repository heruntergefahren/ein Bundle neu gestartet wird – und OSGi ausgeführt wird.

Weitere Informationen zum Ändern des Kennworts für die Web-Konsole finden Sie unter [Ändern des Administratorkennworts der OSGi-Web-Konsole](/help/sites-administering/security-checklist.md#changing-the-osgi-web-console-admin-password) unten.

#### Ändern des Administratorkennworts der OSGi-Web-Konsole {#changing-the-osgi-web-console-admin-password}

Sie müssen auch das für den Zugriff auf die Web-Konsole verwendete Kennwort ändern. Konfigurieren Sie dazu die folgenden Eigenschaften der [Apache Felix OSGi Management Console](/help/sites-deploying/osgi-configuration-settings.md):

**Benutzername** und **Kennwort**: die Anmeldedaten für den Zugriff auf die Apache Felix Web Management Console.\
Das Kennwort muss nach der ersten Installation geändert werden, damit die Sicherheit Ihrer Instanz gewährleistet ist.

Gehen Sie hierfür wie folgt vor:

1. Navigieren Sie zur Web-Konsole unter `<server>:<port>/system/console/configMgr`.
1. Navigieren Sie zu &quot;Apache Felix OSGi Management Console&quot;und ändern Sie die **Benutzername** und **password**.

   ![chlimage_1-166](assets/chlimage_1-166.png)

1. Klicken Sie auf **Speichern**.

### Implementieren eines benutzerdefinierten Fehler-Handlers {#implement-custom-error-handler}

Adobe empfiehlt, benutzerdefinierte Fehler-Handler-Seiten zu definieren, insbesondere für 404- und 500-HTTP-Antwort-Codes, um die Offenlegung von Informationen zu verhindern.

>[!NOTE]
>
>Weitere Details finden Sie im Knowledgebase-Artikel [Erstellen von benutzerdefinierten Skripten oder Fehler-Handlern](https://helpx.adobe.com/experience-manager/kb/CustomErrorHandling.html).

### Vollständige Dispatcher-Sicherheits-Checkliste {#complete-dispatcher-security-checklist}

AEM Dispatcher ist ein wichtiger Teil Ihrer Infrastruktur. Adobe empfiehlt dringend, dass Sie die [Dispatcher-Sicherheitscheckliste](https://helpx.adobe.com/de/experience-manager/dispatcher/using/security-checklist.html) durchgehen.

>[!CAUTION]
>
>Mithilfe des Dispatchers müssen Sie den „.form“-Selektor deaktivieren.

## Überprüfungsschritte {#verification-steps}

### Konfigurieren von Replikations- und Transport-Benutzenden {#configure-replication-and-transport-users}

Bei einer Standardinstallation von AEM wird `admin` als Benutzer für die Transport-Anmeldedaten in den Standard-[Replikationsagenten](/help/sites-deploying/replication.md) angegeben. Außerdem werden Admin-Benutzende verwendet, um die Replikation auf dem Autorensystem zu beziehen.

Aus Sicherheitsgründen sollten beide geändert werden, um dem jeweiligen Anwendungsfall Rechnung zu tragen, wobei die beiden folgenden Aspekte zu berücksichtigen sind:

* **Transport-Benutzende** sollten keine Admin-Benutzenden sein. Richten Sie stattdessen einen Benutzer im Veröffentlichungssystem ein, der nur über Zugriffsrechte für die relevanten Teile des Veröffentlichungssystems verfügt, und verwenden Sie die Anmeldeinformationen dieses Benutzers für den Transport.

     Sie können mit dem gebündelten Benutzer „Replikations-Empfänger“ beginnen und die Zugriffsrechte dieses Benutzenden so konfigurieren, dass sie Ihren Anforderungen entsprechen.

* Der **Replikationsbenutzende** oder die **Agenten-Benutzer-ID** sollte auch nicht der Admin-User sein, sondern eine Benutzerin oder ein Benutzer, die bzw. der nur die Inhalte sehen kann, die repliziert werden sollen. Der Replikationsbenutzende wird auch zum Erfassen von Inhalten verwendet, die auf dem Autorensystem repliziert werden sollen, bevor sie an den Publisher gesendet werden.

### Überprüfen der Sicherheitskonsistenzprüfungen im Vorgangs-Dashboard {#check-the-operations-dashboard-security-health-checks}

Mit AEM 6 wird das neue Vorgangs-Dashboard eingeführt, das Systembetreibenden bei der Fehlerbehebung und der Überwachung des Status einer Instanz helfen soll.

Das Dashboard enthält außerdem eine Sammlung von Sicherheitskonsistenzprüfungen. Es wird empfohlen, den Status aller Sicherheitskonsistenzprüfungen zu überprüfen, bevor Sie mit Ihrer Produktionsinstanz live gehen. Weitere Informationen dazu finden Sie in der [Dokumentation zum Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

### Überprüfen, ob Beispielinhalte vorhanden sind {#check-if-example-content-is-present}

Alle Beispielinhalte und -benutzende (z. B. das Geometrixx-Projekt und seine Komponenten) sollten deinstalliert und vollständig von einem Produktionssystem gelöscht sein, bevor es öffentlich zugänglich gemacht wird.

>[!NOTE]
>
>Die We.Retail-Beispielanwendungen werden entfernt, wenn diese Instanz im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausgeführt wird. Wenn dies aus irgendeinem Grund nicht der Fall ist, können Sie den Beispielinhalt deinstallieren, indem Sie Package Manager aufrufen und dann nach allen We.Retail-Paketen suchen und diese deinstallieren. Weitere Informationen finden Sie unter [Arbeiten mit Paketen](package-manager.md).

### Überprüfen, ob die CRX-Entwicklungs-Bundles vorhanden sind {#check-if-the-crx-development-bundles-are-present}

Diese Entwicklungs-OSGi-Bundles sollten sowohl auf Autoren- als auch auf Veröffentlichungs-Produktionssystemen deinstalliert werden, bevor diese verfügbar gemacht werden.

* Adobe CRXDE-Unterstützung (com.adobe.granite.crxde-support)
* Adobe Granite CRX-Explorer (com.adobe.granite.crx-explorer)
* Adobe Granite CRXDE Lite (com.adobe.granite.crxde-lite)

### Überprüfen, ob das Sling-Entwicklungs-Bundle vorhanden ist {#check-if-the-sling-development-bundle-is-present}

Die [AEM Entwicklertools für Eclipse](/help/sites-developing/aem-eclipse.md) stellt die Installation der Apache Sling Tooling-Unterstützung bereit (org.apache.sling.tooling.support.install).

Dieses OSGi-Bundle sollte sowohl auf Autoren- als auch auf Veröffentlichungs-Produktionssystemen deinstalliert werden, bevor sie verfügbar gemacht werden.

### Schutz vor Cross-Site Request-Forgery {#protect-against-cross-site-request-forgery}

#### Das CSRF Protection Framework {#the-csrf-protection-framework}

AEM 6.1 verfügt über einen Mechanismus zum Schutz vor Cross-Site Request Forgery-Angriffen, die als **CSRF Protection Framework**. Weitere Informationen zur Verwendungsweise finden Sie in der entsprechenden [Dokumentation](/help/sites-developing/csrf-protection.md).

#### Der Sling Referrer-Filter {#the-sling-referrer-filter}

Um bekannte Sicherheitsprobleme mit Cross-Site Request-Forgery (CSRF) in CRX WebDAV und Apache Sling zu beheben, müssen Sie Konfigurationen für den Referrer-Filter hinzufügen, um ihn verwenden zu können.

Der Referrer-Filter-Service ist ein OSGi-Service, mit dem Sie Folgendes konfigurieren können:

* welche HTTP-Methoden gefiltert werden sollen
* Ob eine leere Referrer-Kopfzeile zulässig ist
* Eine Whitelist von Servern, die zusätzlich zum Serverhost zugelassen werden sollen.

   Standardmäßig sind alle Varianten von „localhost“ und die aktuellen Host-Namen, mit denen der Server verknüpft ist, in der Whitelist enthalten.

So konfigurieren Sie den Referrer-Filterdienst:

1. Öffnen Sie die Apache Felix-Konsole (**Konfigurationen**) unter:

   `https://<server>:<port_number>/system/console/configMgr`

1. Melden Sie sich als `admin` an.
1. Wählen Sie im Menü **Konfigurationen** folgende Option aus:

   `Apache Sling Referrer Filter`

1. Geben Sie im Feld `Allow Hosts` alle Hosts ein, die als Referrer zugelassen werden sollen. Jeder Eintrag muss folgendes Format aufweisen:

   &lt;Protokoll>://&lt;Server>:&lt;Port>

   Beispiel:

   * `https://allowed.server:80`: Alle Anfragen von diesem Server mit dem angegebenen Port sind zugelassen.
   * Wenn Sie auch HTTPS-Anfragen zulassen wollen, müssen Sie eine zweite Zeile eingeben.
   * Falls Sie alle Ports dieses Servers zulassen wollen, können Sie als Port-Nummer eine `0` eingeben.

1. Aktivieren Sie das Feld `Allow Empty`, wenn Sie leere/fehlende Referrer-Kopfzeilen zulassen möchten.

   >[!CAUTION]
   >
   >Es wird empfohlen, einen Referrer bereitzustellen, wenn Sie Befehlszeilen-Tools wie `cURL` verwenden, anstatt einen leeren Wert zuzulassen, da andernfalls das Risiko besteht, dass Ihr System CSRF-Angriffen ausgesetzt ist.

1. Bearbeiten Sie die Methoden, die dieser Filter für Prüfungen verwenden soll, über das Feld `Filter Methods`.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### OSGi-Einstellungen {#osgi-settings}

Einige OSGi-Einstellungen sind standardmäßig festgelegt, um das Debugging der Anwendung zu erleichtern. Diese müssen in Ihren Veröffentlichungs- und Autorenproduktionsinstanzen geändert werden, um zu verhindern, dass interne Informationen an die Öffentlichkeit weitergegeben werden.

>[!NOTE]
>
>Alle folgenden Einstellungen, mit Ausnahme des **Day CQ WCM Debug-Filters**, werden automatisch im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) angewendet. Daher empfehlen wir, alle Einstellungen zu überprüfen, bevor Sie Ihre Instanz in einer Produktionsumgebung bereitstellen.

Für jeden der folgenden Services müssen die angegebenen Einstellungen geändert werden:

* [Adobe Granite HTML Library Manager](/help/sites-deploying/osgi-configuration-settings.md):

   * Aktivieren Sie **Minimieren** (um CRLF- und Leerzeichen zu entfernen).
   * Aktivieren Sie **gzip** (damit Dateien ins gzip-Format komprimiert und mit einer Anfrage aufgerufen werden können).
   * Deaktivieren Sie **Debuggen**.
   * Deaktivieren Sie **Zeitplanung**.

* [Day CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md):

   * Entfernen Sie den Haken bei **Aktivieren**.

* [Day CQ WCM-Filter](/help/sites-deploying/osgi-configuration-settings.md):

   * Legen Sie die Option **WCM-Modus** nur auf der Veröffentlichungsinstanz auf „Deaktiviert“ fest.

* [Apache Sling Java Script Handler](/help/sites-deploying/osgi-configuration-settings.md):

   * Deaktivieren Sie **die Funktion zum Erzeugen von Debug-Informationen**.

* [Apache Sling JSP Script Handler](/help/sites-deploying/osgi-configuration-settings.md):

   * Deaktivieren Sie **Generate Debug Info**.
   * Deaktivieren Sie **Mapped Content**.

Weitere Informationen finden Sie unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md).

Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Services. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

## Weitere Informationen {#further-readings}

### Vermeiden von Denial-of-Service (DoS)-Angriffen {#mitigate-denial-of-service-dos-attacks}

Ein Denial-of-Service-Angriff (DoS) zielt darauf ab, eine Computer-Ressource für die vorgesehenen Benutzenden unzugänglich zu machen. Dies geschieht oft durch Überlastung der Ressource, zum Beispiel:

* Mit einer Flut von Anforderungen aus einer externen Quelle.
* Mit einer Anfrage nach mehr Informationen, als das System erfolgreich bereitstellen kann.

   Beispiel: Eine JSON-Darstellung des gesamten Repositorys.

* Wenn eine Seite mit einer unbegrenzten Anzahl an URLs angefordert wird, kann die URL einen Handler, einige Selektoren, eine Erweiterung und einen Suffix enthalten. Diese Elemente können alle geändert werden.

   So kann `.../en.html` angefordert werden als:

   * `.../en.ExtensionDosAttack`
   * `.../en.SelectorDosAttack.html`
   * `.../en.html/SuffixDosAttack`

   Alle gültigen Varianten (geben z. B. die Antwort `200` zurück und werden per Konfiguration zwischengespeichert) werden vom Dispatcher zwischengespeichert, was möglicherweise zu einem vollen Dateisystem führen kann, sodass kein Dienst für weitere Anfragen verfügbar ist.

Es gibt viele Konfigurationsmöglichkeiten, um solche Angriffe zu verhindern. Hier diskutieren wir nur die direkt mit AEM zusammenhängenden.

**Konfigurieren von Sling zum Verhindern von DoS**

Sling ist *inhaltzentriert*. Dies bedeutet, dass sich die Verarbeitung auf den Inhalt konzentriert, da jede (HTTP-)Anfrage auf den Inhalt in Form einer JCR-Ressource (eines Repository-Knotens) abgebildet wird:

* Das erste Ziel ist die Ressource (JCR-Knoten), die die Inhalte enthält..
* Zweitens wird der Renderer oder das Skript durch die Ressourceneigenschaften in Kombination mit bestimmten Teilen der Anfrage lokalisiert (z. B. mit Selektoren und/oder der Erweiterung).

>[!NOTE]
>
>Weitere Einzelheiten hierzu finden Sie unter [Verarbeitung von Sling-Anfragen](/help/sites-developing/the-basics.md#sling-request-processing).

Dieser Ansatz macht Sling sehr leistungsstark und sehr flexibel, aber wie immer muss mit der Flexibilität sorgfältig umgegangen werden.

So verhindern Sie einen Missbrauch infolge von DoS-Angriffen:

1. Binden Sie Kontrollen auf Anwendungsebene ein. Aufgrund der Anzahl der möglichen Varianten ist eine Standardkonfiguration nicht möglich.

   In Ihrem Programm sollten Sie Folgendes tun:

   * die Selektoren in der Anwendung steuern, sodass Sie *nur* die erforderlichen expliziten Selektoren verwenden und für alle anderen den Wert `404` zurückgeben.
   * Verhindern Sie die Ausgabe einer unbegrenzten Anzahl von Inhaltsknoten.

1. Überprüfen Sie die Konfiguration der Standard-Renderer, was ein Problembereich sein kann.

   * Insbesondere der JSON-Renderer, der die Baumstruktur über mehrere Ebenen hinweg durchlaufen kann.

      Beispiel: Die Anfrage

      `http://localhost:4502/.json`

      könnte das gesamte Repository in einer JSON-Darstellung ablegen. Dies würde zu erheblichen Server-Problemen führen. Aus diesem Grund legt Sling eine Begrenzung für die Anzahl der maximalen Ergebnisse fest. Um die Tiefe des JSON-Renderings zu begrenzen, können Sie den Wert für

      **Max. JSON-Ergebnisse** (`json.maximumresults`)

      in der Konfiguration für das [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md) festlegen. Wenn dieser Grenzwert überschritten wird, wird das Rendering ausgeblendet. Der Standardwert für Sling innerhalb von AEM ist `1000`.

   * Deaktivieren Sie als vorbeugende Maßnahme die anderen Standard-Renderer (HTML, einfacher Text, XML). Erneut durch das Konfigurieren des [Apache Sling-GET-Servlet](/help/sites-deploying/osgi-configuration-settings.md).
   >[!CAUTION]
   >
   >Deaktivieren Sie nicht den JSON-Renderer. Dieser ist für den normalen Betrieb von AEM erforderlich.

1. Verwenden Sie eine Firewall, um den Zugriff auf Ihre Instanz zu filtern.

   * Die Verwendung einer Firewall auf Betriebssystemebene ist erforderlich, um den Zugriff auf Punkte Ihrer Instanz zu filtern, die zu Denial-of-Service-Angriffen führen können, wenn sie ungeschützt bleiben.

**Abmildern von DoS mithilfe der Formularauswahl**

>[!NOTE]
>
>Diese Abmilderung sollte nur für AEM-Umgebungen durchgeführt werden, die keine Formulare verwenden.

Da AEM keine Standardindizes für `FormChooserServlet` bereitstellt, löst die Verwendung der Formularauswahl in Abfragen einen aufwendigen Repository-Durchlauf aus, der meist die AEM-Instanz stoppt. Formularauswahl-Instanzen können anhand der Zeichenfolge **&amp;ast;.form.&amp;ast;** in Abfragen erkannt werden.

Führen Sie zum Beheben dieses Problems die folgenden Schritte aus:

1. Gehen Sie zur Web-Konsole, indem Sie im Browser *https://&lt;Server-Adresse>:&lt;Serverport>/system/console/configMgr* aufrufen.

1. Suchen Sie nach **Day CQ WCM Form Chooser Servlet**.
1. Klicken Sie auf den Eintrag, deaktivieren Sie im folgenden Fenster die Option **Advanced Search Require** (Erweiterte Suche erforderlich).

1. Klicken Sie auf **Speichern**.

**Schützen gegen durch Asset-Download-Servlets ausgelöste DoS**

Das standardmäßige Asset-Download-Servlet in AEM ermöglicht es authentifizierten Benutzern, beliebig große, gleichzeitige Download-Anfragen zum Erstellen von ZIP-Dateien mit für sie sichtbaren Assets zu stellen, die den Server und/oder das Netzwerk überlasten können.

Um potenzielle DoS-Risiken zu reduzieren, die durch diese Funktion verursacht werden, `AssetDownloadServlet` Die OSGi-Komponente ist standardmäßig für Veröffentlichungsinstanzen in den neuesten AEM deaktiviert.

Wenn für Ihre Einrichtung die Aktivierung des Asset-Download-Servers erforderlich ist, finden Sie weitere Informationen unter [diesem Artikel](/help/assets/download-assets-from-aem.md#disable-asset-download-servlet) für weitere Informationen.

### Deaktivieren von WebDAV {#disable-webdav}

WebDAV sollte sowohl in der Autoren- als auch in der Veröffentlichungsumgebung deaktiviert sein. Dies kann durch Beenden der entsprechenden OSGi-Bundles erfolgen.

1. Stellen Sie eine Verbindung zur **Felix-Management-Konsole** her, ausgeführt unter:

   `https://<*host*>:<*port*>/system/console`

   Beispiel `http://localhost:4503/system/console/bundles`.

1. Suchen Sie in der Liste der Bundles nach einem Bundle mit dem folgenden Namen:

   `Apache Sling Simple WebDAV Access to repositories (org.apache.sling.jcr.webdav)`

1. Klicken Sie in der Spalte „Aktionen“ auf die Schaltfläche „Stopp“, um dieses Bundle zu stoppen.

1. Suchen Sie erneut in der Liste der Bundles nach einem Bundle mit dem folgenden Namen:

   `Apache Sling DavEx Access to repositories (org.apache.sling.jcr.davex)`

1. Klicken Sie auf die Schaltfläche „Stopp“, um dieses Bundle zu stoppen.

   >[!NOTE]
   >
   >Ein Neustart von AEM ist nicht erforderlich.

### Sicherstellen, dass keine personenbezogenen Informationen im Home-Pfad von Benutzern offengelegt werden {#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path}

Es ist wichtig, dass Sie Ihre Benutzer schützen, indem Sie sicherstellen, dass Sie keine persönlich identifizierbaren Informationen im Home-Pfad der Repository-Benutzer bereitstellen.

Ab AEM 6.1 ändert sich mit der neuen Implementierung der Schnittstelle `AuthorizableNodeName` die Art, wie Benutzer-ID-Knotennamen (auch als autorisierbare ID-Knotennamen bezeichnet) gespeichert werden. Die neue Benutzeroberfläche stellt die Benutzer-ID nicht mehr im Knotennamen bereit, sondern generiert stattdessen einen zufälligen Namen.

Zur Aktivierung ist keine Konfiguration erforderlich, da dies nun die Standardmethode zum Generieren autorisierbarer IDs in AEM ist.

Obwohl dies nicht empfohlen wird, können Sie es deaktivieren, falls Sie die alte Implementierung für die Abwärtskompatibilität mit Ihren vorhandenen Anwendungen benötigen. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie zur Web-Konsole und entfernen Sie den Eintrag **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** aus der Eigenschaft **requiredServicePids** in **Apache Jackrabbit Oak SecurityProvider**.

   Sie können den Oak Security Provider auch finden, indem Sie in den OSGi-Konfigurationen nach der PID **org.apache.jackrabbit.oak.security.internal.SecurityProviderRegistration** suchen.

1. Löschen Sie die OSGi-Konfiguration **Apache Jackrabbit Oak Random Authorizable Node Name** aus der Web-Konsole.

   Um die Suche zu vereinfachen, beachten Sie, dass die PID für diese Konfiguration **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** lautet.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Oak-Dokumentation unter [Namenserstellung für autorisierbare Knoten](https://jackrabbit.apache.org/oak/docs/security/user/authorizablenodename.html).

### Verhindern von Clickjacking {#prevent-clickjacking}

Um Clickjacking zu verhindern, sollten Sie Ihren Webserver so konfigurieren, dass er die HTTP-Kopfzeile `X-FRAME-OPTIONS` bereitstellt, die auf `SAMEORIGIN` festgelegt ist.

Weitere [Informationen zum Thema Clickjacking finden Sie auf der OWASP-Website](https://www.owasp.org/index.php/Clickjacking).

### Achten Sie bei Bedarf darauf, dass Verschlüsselungsschlüssel ordnungsgemäß repliziert werden. {#make-sure-you-properly-replicate-encryption-keys-when-needed}

Bestimmte AEM-Funktionen und Authentifizierungsschemata erfordern, dass Sie Ihre Verschlüsselungsschlüssel über alle AEM-Instanzen hinweg replizieren.

Beachten Sie zunächst, dass die Schlüsselreplikation zwischen verschiedenen Versionen unterschiedlich ausgeführt wird, da die Art und Weise, in der Schlüssel in 6.3 gespeichert werden, von älteren Versionen abweicht.

Nachfolgenden finden Sie weitere Informationen.

#### Replizieren von Schlüsseln für AEM 6.3 {#replicating-keys-for-aem}

Während in älteren Versionen die Replikationsschlüssel im Repository gespeichert wurden, werden sie ab AEM 6.3 im Dateisystem gespeichert.

Um Ihre Schlüssel über Instanzen hinweg zu replizieren, müssen Sie sie daher von der Quellinstanz an den Speicherort der Zielinstanzen im Dateisystem kopieren.

Im Einzelnen müssen Sie:

1. Greifen Sie auf die AEM-Instanz zu, auf der sich die zu kopierenden Schlüsseldaten befinden. In der Regel handelt es sich dabei um eine Autoreninstanz.
1. Suchen Sie im lokalen Dateisystem das Bundle com.adobe.granite.crypto.file. Es kann sich z. B. unter diesem Pfad befinden:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`

   Die Datei `bundle.info` in jedem Ordner identifiziert den Bundle-Namen.

1. Navigieren Sie zum Ordner „data“. Beispiel:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. die HMAC- und Master-Dateien kopieren.
1. Navigieren Sie dann zur Zielinstanz, auf der Sie den HMAC-Schlüssel duplizieren möchten, und dann zum Ordner „data“. Beispiel:

   * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Fügen Sie die beiden zuvor kopierten Dateien ein.
1. [Aktualisieren Sie das Crypto-Bundle](/help/communities/deploy-communities.md#refresh-the-granite-crypto-bundle), wenn die Zielinstanz bereits ausgeführt wird.
1. Wiederholen Sie die vorherigen Schritte für alle Instanzen, auf denen Sie den Schlüssel replizieren möchten.

>[!NOTE]
>
>Sie können zur Methode von vor 6.3 zum Speichern von Schlüsseln zurückkehren, indem Sie beim ersten Installieren von AEM den folgenden Parameter hinzufügen:
>
>`-Dcom.adobe.granite.crypto.file.disable=true`

#### Replizieren von Schlüsseln in AEM 6.2 und älteren Versionen {#replicating-keys-for-aem-and-older-versions}

In AEM 6.2 und älteren Versionen werden die Schlüssel im Repository im Knoten `/etc/key` gespeichert.

Die empfohlene Methode zur sicheren Replikation der Schlüssel in allen Ihren Instanzen besteht darin, nur diesen Knoten zu replizieren. Sie können Knoten selektiv über CRXDE Lite replizieren:

1. Öffnen Sie die CRXDE Lite, indem Sie *https://&lt;serrveraddress>:4502/crx/de/index.jsp*
1. Wählen Sie den `/etc/key`-Knoten aus.
1. Wechseln Sie zur Registerkarte **Replikation**.
1. Klicken Sie auf die Schaltfläche **Replikation**.

### Durchführen eines Penetrationstests {#perform-a-penetration-test}

Adobe empfiehlt dringend, Ihre AEM-Infrastruktur vor dem Einsatz in einer Produktionsumgebung einem Penetrationstest zu unterziehen.

### Best Practices für die Entwicklung {#development-best-practices}

Es ist von entscheidender Bedeutung, dass die neue Entwicklung dem [Best Practices für die Sicherheit](/help/sites-developing/security.md) um sicherzustellen, dass Ihre AEM Umgebung sicher bleibt.
