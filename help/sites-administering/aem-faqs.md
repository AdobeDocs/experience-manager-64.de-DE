---
title: Häufig gestellte Fragen (FAQ) zu AEM
seo-title: AEM 6.4 frequently asked questions
description: Ziehen Sie diese FAQ heran, um allgemeine Workflows oder Probleme im Zusammenhang mit AEM nachzuvollziehen und zu beheben bzw. entsprechende Konfigurationen vorzunehmen.
seo-description: Use these FAQs to understand, configure, and troubleshoot common workflows or issues in AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
exl-id: 76110cf4-0fd8-4203-b256-c0818a1b64d2
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 55%

---

# Häufig gestellte Fragen (FAQ) zu AEM{#aem-faqs}

Auf dieser Seite erhalten Sie Antworten auf einige AEM Probleme bei der Fehlerbehebung und Konfiguration.

## Sites {#sites}

### Wie konfiguriere ich eine Binary-Less-Verteilung? {#how-do-i-configure-binary-less-distribution}

Eine Binary-Less-Verteilung wird für Bereitstellungen über einen freigegebenen Datenspeicher unterstützt und beinhaltet die Verwendung von Agenten, die den Vault-basierten Package Builder „Distribution Package Exporter“ (werkseitige PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) nutzen.

Bei aktiviertem Binary-Less-Modus enthalten die verteilten Inhaltspakete Verweise auf Binärdaten und nicht die Bindärdaten selbst.

### Wie aktiviere ich die Binary-Less-Verteilung? {#how-do-i-enable-binary-less-distribution}

Stellen Sie zur Aktivierung der Binary-Less-Verteilung einen freigegebenen Blob-Speicher bereit.\
Überprüfen Sie die `useBinaryReferences` -Eigenschaft in der OSGi-Konfiguration mit der werkseitigen PID ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* , die Ihr Agent verwendet.

### Wie kann ich die Fehlermeldungen beim Navigieren durch die Seitenhierarchie in der AEM Sites-Konsole anpassen? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Rufen Sie den Bereich „Netzwerk“ (des Chrome-Browsers) auf, um persönliche Einstellungen festzulegen (ohne minimierte JavaScript-Version).

Sehen Sie sich die Spalte `Initiator` an, um festzustellen, wer der Initiator einer Anfrage war. Sie enthält die Dateien und die Zeilennummern, von wo aus die AJAX-Aufrufe ausgeführt werden. Später können Sie die Fehlerverarbeitungsfunktion nachverfolgen und die Fehlermeldung gemäß Ihren Anforderungen ändern.

### Wie kann ich Berechtigungen aktivieren, während ich eine Sprachkopie für „content-authors“ in AEM erstelle? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Um eine Sprachkopie-Funktion zu erstellen, benötigen Inhaltsautoren Berechtigungen unter `/content/projects` Standort.

Wenn es erforderlich ist, dass die Autoren auch Projekte verwalten, können Sie den Autor zu `project-administrators` hinzugefügt.

### Wie ändere ich das Format während der Erstellung einer Sprachkopie für ein Projekt? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Vor dem Erstellen eines Übersetzungsprojekts müssen Sie einen Sprach-Stamm und eine Sprachkopie innerhalb des Stamms erstellen.

Beispiel:\
Erstellen eines Sprachstamms unter `/content/geometrixx` mit dem Namen `fr_LU` (und Titel als Französisch (Luxemburg)). Erstellen Sie anschließend eine Sprachkopie der Seite aus dem Bereich &quot;Verweise&quot;und navigieren Sie zu `Create structure only` Option in `Create & Translate`. Erstellen Sie abschließend ein Übersetzungsprojekt und fügen Sie dann die Sprachkopie zum Übersetzungsauftrag hinzu.

Weitere Informationen dazu finden Sie in den nachfolgenden Ressourcen:

* [Vorbereiten von Inhalten für die Übersetzung](/help/sites-administering/tc-prep.md)
* [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md)

### Wie lassen sich AEM-Funktionen im Zusammenhang mit Anmeldeversuchen und ACL- oder Berechtigungsänderungen prüfen? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM bietet nun die Möglichkeit, administrative Änderungen zu protokollieren, um Fehlerbehebungen und Audits zu erleichtern. Standardmäßig werden die Informationen im `error.log` -Datei. Um die Überwachung zu vereinfachen, empfiehlt es sich, diese Einträge in einer separaten Protokolldatei zu speichern.\
Informationen dazu, wie Sie Einträge in einer separaten Protokolldatei speichern, finden Sie unter [Prüfen von Benutzerverwaltungsvorgängen in AEM](/help/sites-administering/audit-user-management-operations.md).

### Wie lässt sich SSL standardmäßig aktivieren? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 bietet einen SSL-Assistenten sowie eine Benutzeroberfläche zum Konfigurieren der Jetty- und Granite Jetty-SSL-Unterstützung.

Informationen dazu, wie Sie SSL standardmäßig aktivieren können, finden Sie unter [Die Funktion „SSL By Default“ (SSL als Standard)](/help/sites-administering/ssl-by-default.md).

### Welche Architektur empfiehlt sich bei der Nutzung der AEM Content Services über eine mobilen App, idealerweise React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Die Content Services basieren auf den Sling-Modellen und die AEM Entwickler müssen für jede exportierte Komponente ein Sling-Modell-Pojo bereitstellen.

Erläuterungen dazu, wie AEM Content Services von einer React-Anwendung genutzt werden, erhalten Sie im Tutorial [Erste Schritte mit AEM Content Services](https://helpx.adobe.com/de/experience-manager/kt/sites/using/content-services-tutorial-use.html).

Wenn die Entwickler außerdem eine Komponentenstruktur exportieren möchten, können sie auch die `ComponentExporter` und `ContainerExporter` -Schnittstellen sowie die Verwendung von `ModelFactory` um die untergeordneten Komponenten zu iterieren und ihre Modelldarstellung zurückzugeben. Weitere Informationen dazu finden Sie in den nachfolgenden Ressourcen:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling :: Sling-Modelle](https://sling.apache.org/documentation/bundles/models.html)

### Wie lässt sich das AEM 6.4-Umfrage-Popup deaktivieren? {#how-to-disable-aem-survey-pop-up}

Sie können die Sammlung von Nutzungsstatistiken über die Touch-optimierte Benutzeroberfläche oder die Web-Konsole aktivieren. Eine ausführliche Anleitung finden Sie unter [Aggregierte Sammlung von Nutzungsstatistiken aktivieren](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### Gibt es eine Übersicht über die wichtigsten Funktionen, die mit der Aktualisierung auf AEM 6.4 zur Verfügung stehen? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Siehe [Gründe für die Aktualisierung AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) beschreibt die allgemeine Aufschlüsselung der wichtigsten Funktionen für Kunden, die ein Upgrade auf die neueste Version von Adobe Experience Manager in Erwägung ziehen.

### Wie konfiguriere ich eine AEM-Instanz zur Verwendung des PorterStem-Filters? {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

Der Filter &quot;PorterStem&quot;wendet den Algorithmus für die Porterstemmung auf Englisch an. Die Ergebnisse ähneln der Verwendung des Snowball Porter Stemmers mit der *language=&quot;English&quot;* -Argument. Aber dieser Stil ist direkt in Java kodiert und nicht auf Snowball basiert. Es akzeptiert keine Liste geschützter Wörter und ist nur für englischsprachigen Text geeignet.

Oak stellt eine Reihe von Lucene-bereitgestellten Analyzer-Konfigurationselementen zur Verwendung in AEM bereit. Informationen zur Verwendung von Filtern finden Sie unter **Apache Oak Analyzers** in [Implementierungshandbuch für einfache Suchen](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

### Wie erfolgt eine vollständige Neuindizierung? {#how-to-perform-a-full-re-indexing}

Vor einer Neuindizierung sollten die damit verbundenen Auswirkungen auf die AEM-Gesamtleistung angemessen berücksichtigt werden. Darüber hinaus sollte die Neuindizierung in Zeiträumen geringer Aktivität oder während Wartungsfenstern stattfinden.

Siehe Abschnitt [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md) um die Gründe für die Neuindizierung zu verstehen.

### Unterstützen wir minimierte JS-Bibliotheken in Design Importer? {#do-we-support-minified-js-libs-in-design-importer}

Sie müssen die Eigenschaft der standardmäßigen JS-Prozessor-Konfigurationen der Adobe Granite HTML Library Manager in ***min:gcc***. Um das Designpaket erfolgreich zu importieren, wird empfohlen, vorminimierte Drittanbieterbibliotheken in unsere clientseitigen Bibliotheken aufzunehmen.

## Assets {#assets}

### Warum wiederholt sich der Assets-Workflow beim Hochladen von MP4-Dateien (z. B. bei Verwendung der Drag-and-Drop-Methode)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Wenn der Benutzer, der die Filmdateien hochlädt, nicht über die Berechtigungen zum Löschen für den Asset-Knoten verfügt, schlägt die Löschung von Chunk-Knoten fehl und der Upload wird neu gestartet.

### Wie viele digitale Assets können derzeit maximal gleichzeitig mit AEM 6.4 hochgeladen werden? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Mit Adobe Experience Manager (AEM) 6.4 können Sie derzeit jeweils bis zu 2 GB an Assets hochladen.

Weitere Informationen dazu, wie viele digitale Assets derzeit maximal gleichzeitig mit AEM 6.4 hochgeladen werden können, finden Sie im [Handbuch zur Assets-Dimensionierung](/help/assets/assets-sizing-guide.md).

### Was sind die Standardeinstellungen für OOTB -Konfigurationen beim Erstellen von Sprachkopien? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Beim Erstellen von Sprachkopien über die klassische Benutzeroberfläche werden Assets nicht unter die neue Sprachhierarchie verschoben, sondern über den Sprach-Master verwendet.

Wenn Sie hingegen eine Kopie über die Touch-optimierte Benutzeroberfläche erstellen (**Verweise** -> **Sprachkopie aktualisieren**), wird unter der neuen Sprache ein neuer DAM-Ordner erstellt und von dort aus auf Assets verwiesen.

Dies ist die Standardeinstellung für OOTB-Konfigurationen. Sie können in Übersetzungskonfigurationen für die Option **Seiten-Assets übersetzen** die Einstellung **Nicht übersetzen** festlegen.\
Klicken Sie dazu in AEM 6.4 auf **Tools** > **Cloud-Services** > **Übersetzungs-Cloud-Services**.

### Wie lässt sich eine AEM-Komponente deaktivieren, die zu einem exponentiellen Wachstum des AEM-Segmentspeichers führt (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Sie können den OSGi Component Disabler deaktivieren. Informationen zur Verwendung dieses Diensts finden Sie unter [OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Als Problemumgehung können Sie die Komponente auch manuell deaktivieren und zwar entweder über die Benutzeroberfläche oder per `curl`-Befehl (siehe nachstehendes Beispiel) nach jedem Neustart von AEM.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### Wie konfiguriere ich Assets Insights mit AEM 6.4-Instanz? {#how-to-configure-asset-insights-with-aem-instance}

Informationen zum Einrichten und Konfigurieren von Assets Insights für Experience Manager, der über Adobe Activation (DTM) bereitgestellt wird, finden Sie unter [Einrichten von Asset Insights mit AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### Wie lassen sich Admin-Konsolen anpassen? {#how-to-customize-admin-consoles}

AEM bietet verschiedene Mechanismen, mit denen Sie die Konsolen und die Seitenbearbeitungsfunktionen Ihrer Authoring-Instanz anpassen können.
Informationen zum Erstellen einer benutzerdefinierten Konsole und Anpassen einer Standardansicht für eine Konsole finden Sie unter [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md).

### Was ist der Unterschied zwischen CoralUI 2- und CoralUI 3-basierten Komponenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Ein neuer Satz von Sling-Komponenten von Granite UI Foundation wird für Coral3 erstellt und befindet sich unter [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) befinden. Es gibt einen Satz von CoralUI 2-basierten Komponenten und einen Satz von CoralUI 3-basierten Komponenten. Bei dem neuen Satz handelt es sich nicht um eine bloße Kopie des alten Satzes, sondern um eine bereinigte Version (u. .a optimiert und ohne veraltete Funktionen). Entsprechend empfiehlt es sich, dass eine Seite entweder ausschließlich den CoralUI 3-basierten oder aber den CoralUI 2-basierten Satz verwendet.

Weitere Informationen finden Sie unter [Migrationshandbuch für CoralUI 3-basiert](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### Wie lässt sich die Suchkomponente in AEM Assets anpassen? {#how-to-customize-the-search-component-in-aem-assets}

Weitere Informationen zur Suchsteigerung/Rangfolge und weitere Informationen zur Implementierung finden Sie unter [Einfache Anleitung zur Suchimplementierung.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

Bei der Implementierung der einfachen Suche handelt es sich um die Materialien vom Summit Lab „AEM Search Demystified“ von 2017.

### Wenn ein Kunde nur eine Sites-Lizenz in AEM kauft, hat er dann weiterhin Zugriff auf Assets? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

Nein, der Kunde kann nicht auf Assets (oder andere Elemente als Sites) zugreifen. Auch wenn die gesamte (AEM) Vor-Ort-Komponente von Adobe Experience Manager in der JAR enthalten ist, ist der Kunde berechtigt, nur auf die Komponenten der JAR-Datei zuzugreifen, für die er in seinem Vertrag lizenziert ist. Wenn sie andere Komponenten untersuchen möchten, können sie entweder das AEM-Testprogramm für bis zu 45 Tage verwenden oder einen 0-USD-Verkaufsauftrag unterzeichnen, mit dem sie benannte Komponenten wie Assets auswerten können (keine Produktionsverwendung).

Weitere Informationen zu AEM On-Premise-Software und Adobe Managed Services finden Sie in den folgenden Ressourcen:

* [On-Premise-Software von Adobe Experience Manager](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### Wie kann ein Kunde die Standardeigenschaften einer Seite oder eines Assets erweitern? {#how-to-extend-default-properties-page-or-asset}

Informationen zum Erweitern der Standardeigenschaften einer Seite oder eines Assets finden Sie in den folgenden Ressourcen:

* [Metadatenschemata in Assets](/help/assets/metadata-schemas.md)
* [Anpassen von Ansichten von Seiteneigenschaften](/help/sites-developing/page-properties-views.md)
