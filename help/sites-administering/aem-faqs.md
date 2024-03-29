---
title: Häufig gestellte Fragen zu AEM
seo-title: AEM 6.4 frequently asked questions
description: Verwenden Sie diese häufig gestellten Fragen, um allgemeine Workflows oder Probleme in AEM zu verstehen, zu konfigurieren und zu beheben.
seo-description: Use these FAQs to understand, configure, and troubleshoot common workflows or issues in AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
exl-id: 76110cf4-0fd8-4203-b256-c0818a1b64d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 38%

---

# Häufig gestellte Fragen (FAQ) zu AEM{#aem-faqs}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Auf dieser Seite erhalten Sie Antworten auf einige AEM Probleme bei der Fehlerbehebung und Konfiguration.

## Sites {#sites}

### Wie konfiguriere ich eine Binary-Less-Verteilung? {#how-do-i-configure-binary-less-distribution}

Eine Binary-Less-Verteilung wird für Bereitstellungen über einen freigegebenen Datenspeicher unterstützt und beinhaltet die Verwendung von Agenten, die den Vault-basierten Package Builder „Distribution Package Exporter“ (werkseitige PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) nutzen.

Bei aktiviertem Binary-Less-Modus enthalten die verteilten Inhaltspakete Verweise auf Binärdaten und nicht die Binärdaten selbst.

### Wie aktiviere ich eine Binary-Less-Verteilung? {#how-do-i-enable-binary-less-distribution}

Stellen Sie zur Aktivierung der Binary-Less-Verteilung einen freigegebenen Blob-Speicher bereit.\
Überprüfen Sie die `useBinaryReferences`-Eigenschaft in der OSGi-Konfiguration mit der werkseitigen PID (`org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*, die der Agent verwendet.

### Wie kann ich die Fehlermeldungen beim Navigieren in der Seitenhierarchie in AEM Sites-Konsole anpassen? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Überprüfen Sie den Bereich Netzwerk (des Chrome-Browsers), in dem eine persönliche Einrichtung (JS) nicht minimiert wurde.

Sehen Sie sich die Spalte `Initiator` an, um festzustellen, wer der Initiator einer Anfrage war. Sie enthält die Dateien und die Zeilennummern, von wo aus die AJAX-Aufrufe ausgeführt werden. Später können Sie die Fehlerbearbeitungsfunktion nachverfolgen und die Fehlermeldung entsprechend Ihren Anforderungen ändern.

### Wie kann ich beim Erstellen von Sprachkopien für Inhaltsautoren in AEM Berechtigungen aktivieren? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Zum Erstellen der Sprachkopie-Funktion benötigen Autorinnen und Autoren Berechtigungen für den Speicherort `/content/projects`.

Wenn Autorinnen und Autoren auch Projekte verwalten müssen, fügen Sie sie als vorübergehende Lösung der Gruppe `project-administrators` hinzu.

### Wie kann das Format beim Erstellen der Sprachkopie für ein Projekt geändert werden? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Erstellen Sie einen Sprachstamm und eine Sprachkopie im Stammverzeichnis, bevor Sie ein Übersetzungsprojekt erstellen.

Beispiel:\
Erstellen eines Sprachstamms unter `/content/geometrixx` mit dem Namen `fr_LU` (und Titel als Französisch (Luxemburg)). Erstellen Sie anschließend eine Sprachkopie der Seite aus dem Bereich „Verweise“ und navigieren Sie zur Option `Create structure only` in `Create & Translate`. Erstellen Sie abschließend ein Übersetzungsprojekt und fügen Sie dann die Sprachkopie zum Übersetzungsauftrag hinzu.

Weitere Informationen finden Sie in den folgenden zusätzlichen Ressourcen:

* [Vorbereiten von Inhalten für die Übersetzung](/help/sites-administering/tc-prep.md)
* [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md)

### Wie lassen sich AEM-Funktionen im Zusammenhang mit Anmeldeversuchen und ACL- oder Berechtigungsänderungen prüfen? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM bietet nun die Möglichkeit, administrative Änderungen zu protokollieren, um Fehlerbehebungen und Audits zu erleichtern. Standardmäßig werden die Informationen in der Datei `error.log` protokolliert. Um die Überwachung zu vereinfachen, empfiehlt es sich, diese Einträge in einer separaten Protokolldatei zu speichern.\
Informationen dazu, wie Sie Einträge in einer separaten Protokolldatei speichern, finden Sie unter [Prüfen von Benutzerverwaltungsvorgängen in AEM](/help/sites-administering/audit-user-management-operations.md).

### Wie wird SSL standardmäßig aktiviert? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 ist im Lieferumfang des SSL-Assistenten enthalten und bietet eine Benutzeroberfläche zum Konfigurieren der Jetty- und Granite Jetty-SSL-Unterstützung.

Informationen zum Aktivieren von SSL standardmäßig finden Sie unter [SSL standardmäßig](/help/sites-administering/ssl-by-default.md).

### Welche Architektur wird empfohlen, wenn AEM Content Services von einer mobilen App, idealerweise React Native, verwendet werden? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Die Content Services basieren auf Sling-Modellen und AEM-Entwicklerinnen und -Entwickler müssen ein Sling-Modell-POJO für jede zu exportierende Komponente bereitstellen.

Erläuterungen dazu, wie AEM Content Services von einer React-Anwendung genutzt werden, erhalten Sie im Tutorial [Erste Schritte mit AEM Content Services](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de).

Wenn Entwicklerinnen und Entwickler zudem eine Komponentenstruktur exportieren möchten, können sie auch die Schnittstellen `ComponentExporter` und `ContainerExporter` implementieren sowie mithilfe von `ModelFactory` die untergeordneten Komponenten durchlaufen und ihre Modelldarstellung zurückgeben. Weitere Informationen dazu finden Sie in den nachfolgenden Ressourcen:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling :: Sling Models](https://sling.apache.org/documentation/bundles/models.html)

### Wie kann AEM 6.4 Umfrage-Popup deaktiviert werden? {#how-to-disable-aem-survey-pop-up}

Sie können die Erfassung von Nutzungsstatistiken über die Touch-Benutzeroberfläche oder die Web-Konsole aktivieren. Detaillierte Anweisungen finden Sie unter [Aggregierte Sammlung von Nutzungsstatistiken aktivieren](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### Gibt es eine gute Ressource, die die wichtigsten Funktionen für die Aktualisierung auf AEM 6.4 hervorhebt? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Siehe [Gründe für die Aktualisierung AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) beschreibt die allgemeine Aufschlüsselung der wichtigsten Funktionen für Kunden, die ein Upgrade auf die neueste Version von Adobe Experience Manager in Erwägung ziehen.

### Wie konfiguriere ich eine AEM-Instanz zur Verwendung des PorterStem-Filters? {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

Der Filter &quot;PorterStem&quot;wendet den Algorithmus für die Porterstemmung auf Englisch an. Die Ergebnisse ähneln der Verwendung des Snowball Porter Stemmers mit der *language=&quot;English&quot;* -Argument. Aber dieser Stil ist direkt in Java kodiert und nicht auf Snowball basiert. Es akzeptiert keine Liste geschützter Wörter und ist nur für englischsprachigen Text geeignet.

Oak stellt eine Reihe von Lucene-bereitgestellten Analyzer-Konfigurationselementen zur Verwendung in AEM bereit. Informationen zur Verwendung von Filtern finden Sie unter **Apache Oak Analyzers** in [Implementierungshandbuch für einfache Suchen](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/search-tutorial-develop.html?lang=de).

### Wie erfolgt eine vollständige Neuindizierung? {#how-to-perform-a-full-re-indexing}

Vor einer Neuindizierung sollten die damit verbundenen Auswirkungen auf die AEM-Gesamtleistung angemessen berücksichtigt werden. Darüber hinaus sollte die Neuindizierung in Zeiträumen geringer Aktivität oder während Wartungsfenstern stattfinden.

Siehe Abschnitt [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md) um die Gründe für die Neuindizierung zu verstehen.

### Unterstützen wir minimierte JS-Bibliotheken in Design Importer? {#do-we-support-minified-js-libs-in-design-importer}

Sie müssen die Eigenschaft der standardmäßigen JS-Prozessor-Konfigurationen der Adobe Granite HTML Library Manager in ***min:gcc***. Um das Designpaket erfolgreich zu importieren, wird empfohlen, vorminimierte Drittanbieterbibliotheken in unsere clientseitigen Bibliotheken aufzunehmen.

## Assets {#assets}

### Warum wiederholt sich der Assets-Workflow beim Hochladen von MP4-Dateien (z. B. mittels Drag &amp; Drop-Methode)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Wenn der Benutzer beim Hochladen der Filmdateien keine Löschberechtigungen unter dem Asset-Knoten hat, schlagen die Löschungs-Chunk-Knoten fehl und der Upload wird neu gestartet.

### Wie viele digitale Assets können maximal mit AEM 6.4 gleichzeitig verwendet werden? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Mit Adobe Experience Manager (AEM) 6.4 können Sie derzeit bis zu 2 GB Assets gleichzeitig hochladen.

Weitere Informationen zur maximalen Anzahl von Assets, die mit AEM 6.4 verwendet werden können, finden Sie unter [Handbuch zur Dimensionierung von Assets](/help/assets/assets-sizing-guide.md).

### Was sind die Standardeinstellungen für OOTB-Konfigurationen beim Erstellen von Sprachkopien? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Beim Erstellen von Sprachkopien über die klassische Benutzeroberfläche werden Assets nicht in die neue Sprachhierarchie verschoben, sondern über die Übergeordnete Sprachstruktur verwendet.

Wenn Sie hingegen eine Sprachkopie über die Touch-optimierte Benutzeroberfläche erstellen (**Verweise** -> **Sprachkopie aktualisieren**), wird unter der neuen Sprache ein neuer DAM-Ordner erstellt und von dort aus auf Assets verwiesen.

Dies ist die Standardeinstellung für OOTB-Konfigurationen. Sie können in Übersetzungskonfigurationen für die Option **Seiten-Assets übersetzen** die Einstellung **Nicht übersetzen** festlegen.\
Klicken Sie dazu in AEM 6.4 auf **Tools** > **Cloud-Services** > **Übersetzungs-Cloud-Services**.

### Wie lässt sich eine AEM-Komponente deaktivieren, die zu einem exponentiellen Wachstum des AEM-Segmentspeichers führt (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Sie können den OSGi Component Disabler deaktivieren. Informationen zur Verwendung dieses Dienstes finden Sie unter [OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Als Problemumgehung können Sie die Komponente auch manuell deaktivieren und zwar entweder über die Benutzeroberfläche oder per `curl`-Befehl (siehe nachstehendes Beispiel) nach jedem Neustart von AEM.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### Wie konfiguriere ich Assets Insights mit AEM 6.4-Instanz? {#how-to-configure-asset-insights-with-aem-instance}

Informationen zum Einrichten und Konfigurieren von Assets Insights für Experience Manager, der über Adobe Activation (DTM) bereitgestellt wird, finden Sie unter [Einrichten von Asset Insights mit AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### Wie lassen sich Admin-Konsolen anpassen? {#how-to-customize-admin-consoles}

AEM bietet verschiedene Methoden zum Anpassen von Konsolen und der Seitenbearbeitungsfunktionen Ihrer Autoreninstanz.
Informationen zum Erstellen einer benutzerdefinierten Konsole und Anpassen einer Standardansicht für eine Konsole finden Sie unter [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md).

### Was ist der Unterschied zwischen den auf CoralUI 2 und CoralUI 3 basierenden Komponenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Für Coral3 wurde ein neuer Satz Sling-Komponenten der Granite-Benutzeroberflächen-Foundation erstellt, die sich unter [/libs/granite/ui/components/coral/foundation](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Es gibt einen Satz für CoralUI 2-basierte Komponenten und einen Satz für CoralUI 3-basierte Komponenten. Der neue Satz ist nicht nur ein Copy &amp; Paste des alten Sets, sondern wird bereinigt (z. B. Straffung, Entfernung veralteter Funktionen). Daher wird empfohlen, dass eine Seite nur einen CoralUI 3-basierten oder CoralUI 2-basierten Satz verwendet.

Weitere Informationen finden Sie unter [Migrationshandbuch für CoralUI 3-basiert](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### Wie kann die Suchkomponente in AEM Assets angepasst werden? {#how-to-customize-the-search-component-in-aem-assets}

Weitere Informationen zur Suchsteigerung/Rangfolge und weitere Informationen zur Implementierung finden Sie unter [Einfache Anleitung zur Suchimplementierung.](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/search-tutorial-develop.html?lang=de)

Bei der Implementierung der einfachen Suche handelt es sich um die Materialien vom Summit Lab „AEM Search Demystified“ von 2017.

### Wenn ein Kunde nur eine Sites-Lizenz in AEM kauft, hat er dann weiterhin Zugriff auf Assets? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

Nein, der Kunde kann nicht auf Assets (oder andere Elemente als Sites) zugreifen. Auch wenn die gesamte (AEM) Vor-Ort-Komponente von Adobe Experience Manager in der JAR enthalten ist, ist der Kunde berechtigt, nur auf die Komponenten der JAR-Datei zuzugreifen, für die er in seinem Vertrag lizenziert ist. Wenn sie andere Komponenten untersuchen möchten, können sie entweder das AEM-Testprogramm für bis zu 45 Tage verwenden oder einen 0-USD-Verkaufsauftrag unterzeichnen, mit dem sie benannte Komponenten wie Assets auswerten können (keine Produktionsverwendung).

Weitere Informationen zu AEM On-Premise-Software und Adobe Managed Services finden Sie in den folgenden Ressourcen:

* [On-Premise-Software von Adobe Experience Manager](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### Wie kann ein Kunde die Standardeigenschaften einer Seite oder eines Assets erweitern? {#how-to-extend-default-properties-page-or-asset}

Informationen zum Erweitern der Standardeigenschaften einer Seite oder eines Assets finden Sie in den folgenden Ressourcen:

* [Metadatenschemata in Assets](/help/assets/metadata-schemas.md)
* [Anpassen der Ansichten von Seiteneigenschaften](/help/sites-developing/page-properties-views.md)
