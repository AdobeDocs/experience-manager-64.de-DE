---
title: Häufig gestellte Fragen (FAQ) zu AEM
seo-title: Häufig gestellte Fragen zu AEM 6.4
description: Ziehen Sie diese FAQ heran, um allgemeine Workflows oder Probleme im Zusammenhang mit AEM nachzuvollziehen und zu beheben bzw. entsprechende Konfigurationen vorzunehmen.
seo-description: Ziehen Sie diese FAQ heran, um allgemeine Workflows oder Probleme im Zusammenhang mit AEM nachzuvollziehen und zu beheben bzw. entsprechende Konfigurationen vorzunehmen.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
translation-type: tm+mt
source-git-commit: f5b45b2c8bfcf9d82ddc08b05b5fff22937fa9fd

---


# Häufig gestellte Fragen (FAQ) zu AEM{#aem-faqs}

Auf dieser Seite erhalten Sie Antworten auf einige Probleme bei der Fehlerbehebung und Konfiguration von AEM.

## Sites {#sites}

### Wie konfiguriere ich eine Binary-Less-Verteilung? {#how-do-i-configure-binary-less-distribution}

Eine Binary-Less-Verteilung wird für Bereitstellungen über einen freigegebenen Datenspeicher unterstützt und beinhaltet die Verwendung von Agenten, die den Vault-basierten Package Builder „Distribution Package Exporter“ (werkseitige PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) nutzen.

Bei aktiviertem Binary-Less-Modus enthalten die verteilten Inhaltspakete Verweise auf Binärdaten und nicht die Bindärdaten selbst.

### Wie aktiviere ich die Binary-Less-Verteilung? {#how-do-i-enable-binary-less-distribution}

Stellen Sie zur Aktivierung der Binary-Less-Verteilung einen freigegebenen Blob-Speicher bereit.\
Check the `useBinaryReferences` property in the OSGI configuration with the factory PID ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*that your agent is using.

### Wie kann ich die Fehlermeldungen beim Navigieren durch die Seitenhierarchie in der AEM-Sites-Konsole anpassen? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Rufen Sie den Bereich „Netzwerk“ (des Chrome-Browsers) auf, um persönliche Einstellungen festzulegen (ohne minimierte JavaScript-Version).

Sehen Sie sich die Spalte `Initiator` an, um festzustellen, wer der Initiator einer Anfrage war. Sie enthält die Dateien und die Zeilennummern, von wo aus die AJAX-Aufrufe ausgeführt werden. Später können Sie die Fehlerverarbeitungsfunktion nachverfolgen und die Fehlermeldung gemäß Ihren Anforderungen ändern.

### Wie kann ich Berechtigungen aktivieren, während ich eine Sprachkopie für „content-authors“ in AEM erstelle? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

To create language copy feature, content-authors need permissions at `/content/projects` location.

If one requires the authors to manage projects as well, then the workaround is to add the author to `project-administrators` group.

### Wie ändere ich das Format während der Erstellung einer Sprachkopie für ein Projekt? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Vor dem Erstellen eines Übersetzungsprojekts müssen Sie einen Sprach-Stamm und eine Sprachkopie innerhalb des Stamms erstellen.

Beispiel:\
Create a language root at `/content/geometrixx` with name as `fr_LU` (and title as French (Luxembourg)). Erstellen Sie anschließend eine Sprachkopie der Seite aus dem Referenzen-Bedienfeld und navigieren Sie zur `Create structure only` Option in `Create & Translate`. Erstellen Sie abschließend ein Übersetzungsprojekt und fügen Sie dann die Sprachkopie zum Übersetzungsauftrag hinzu.

Weitere Informationen dazu finden Sie in den nachfolgenden Ressourcen:

* [Vorbereiten von Inhalten für die Übersetzung](/help/sites-administering/tc-prep.md)
* [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md)

### Wie lassen sich AEM-Funktionen im Zusammenhang mit Anmeldeversuchen und ACL- oder Berechtigungsänderungen prüfen? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM bietet nun die Möglichkeit, administrative Änderungen zu protokollieren, um Fehlerbehebungen und Audits zu erleichtern. By default, the information is logged in the `error.log` file. Um die Überwachung zu vereinfachen, empfiehlt es sich, diese Einträge in einer separaten Protokolldatei zu speichern.\
Informationen dazu, wie Sie Einträge in einer separaten Protokolldatei speichern, finden Sie unter [Prüfen von Benutzerverwaltungsvorgängen in AEM](/help/sites-administering/audit-user-management-operations.md).

### Wie lässt sich SSL standardmäßig aktivieren? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 bietet einen SSL-Assistenten sowie eine Benutzeroberfläche zum Konfigurieren der Jetty- und Granite Jetty-SSL-Unterstützung.

Informationen dazu, wie Sie SSL standardmäßig aktivieren können, finden Sie unter [Die Funktion „SSL By Default“ (SSL als Standard)](/help/sites-administering/ssl-by-default.md).

### Welche Architektur empfiehlt sich bei der Nutzung der AEM Content Services über eine mobilen App, idealerweise React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Die Content Services basieren auf den Sling-Modellen, und die AEM-Entwickler müssen für jede Komponente, die exportiert wird, ein Sling-Modell-Pojo bereitstellen.

Erläuterungen dazu, wie AEM Content Services von einer React-Anwendung genutzt werden, erhalten Sie im Tutorial [Erste Schritte mit AEM Content Services](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html).

Also, if the developers want to export a tree of components they can also implement the `ComponentExporter` and `ContainerExporter` interfaces as well as use the `ModelFactory` to iterate over the child components and return their model representation. Weitere Informationen dazu finden Sie in den nachfolgenden Ressourcen:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling:Sling-Modelle](https://sling.apache.org/documentation/bundles/models.html)

### Wie lässt sich das AEM 6.4-Umfrage-Popup deaktivieren? {#how-to-disable-aem-survey-pop-up}

Sie können die Sammlung von Nutzungsstatistiken über die Touch-optimierte Benutzeroberfläche oder die Web-Konsole aktivieren. Eine ausführliche Anleitung finden Sie unter [Aggregierte Sammlung von Nutzungsstatistiken aktivieren](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### Gibt es eine Übersicht über die wichtigsten Funktionen, die mit der Aktualisierung auf AEM 6.4 zur Verfügung stehen? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Refer to [Understanding Reasons to Upgrade AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) that describes high-level breakdown of key features for customers considering upgrading to the latest version of Adobe Experience Manager.

### Konfigurieren einer AEM-Instanz für die Verwendung des PorterStem-Filters {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

Der PorterStem-Filter wendet den Porter Stemming-Algorithmus für Englisch an. Die Ergebnisse sind ähnlich wie die Verwendung des Snowball Porter Stemmers mit dem *Argument language=&quot;English&quot;* . Aber dieser Stil ist direkt in Java kodiert und nicht auf Snowball basiert. Es akzeptiert keine Liste geschützter Wörter und ist nur für englischsprachigen Text geeignet.

Oak stellt eine Reihe von Analyzer-Konfigurationselementen mit Lucene-Unterstützung zur Verwendung in AEM bereit. Weitere Informationen zur Verwendung von Filtern finden Sie unter **Apache Oak Analyzers** im [Implementierungshandbuch](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)zur einfachen Suche.

### Wie führt man eine vollständige Neuindizierung durch? {#how-to-perform-a-full-re-indexing}

Vor einer Neuindizierung sollten die damit verbundenen Auswirkungen auf die AEM-Gesamtleistung angemessen berücksichtigt werden. Darüber hinaus sollte die Neuindizierung in Zeiträumen geringer Aktivität oder während Wartungsfenstern stattfinden.

Lesen Sie die [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md) , um die Gründe für die Neuindizierung zu verstehen.

### Unterstützen wir minimierte JS libs in Design Importer? {#do-we-support-minified-js-libs-in-design-importer}

Sie müssen die Eigenschaft &quot;JS-Prozessor default configs&quot;des Adobe Granite HTML Library Manager in ***min:gcc***&#x200B;ändern. Um das Design-Paket erfolgreich zu importieren, wird empfohlen, vorminimierte Drittanbieterbibliotheken in unsere clientseitigen Bibliotheken aufzunehmen.

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

### Wie lässt sich Asset Insights mit AEM 6.4-Instanzen konfigurieren? {#how-to-configure-asset-insights-with-aem-instance}

To setup and configure Asset Insights for Experience Manager deployed via Adobe Activation (DTM), refer to [Set up Asset Insights with AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### Wie lassen sich Admin-Konsolen anpassen? {#how-to-customize-admin-consoles}

AEM bietet verschiedene Mechanismen, mit denen Sie die Konsolen und die Seitenerstellungsfunktion Ihrer Authoring-Instanz anpassen können.
To learn how to create a custom console and customize a default view for a console, refer to [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md).

### Was ist der Unterschied zwischen CoralUI 2- und CoralUI 3-basierten Komponenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

A new set of Sling components of Granite UI Foundation is created for Coral3 and is located under [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) befinden. Es gibt einen Satz von CoralUI 2-basierten Komponenten und einen Satz von CoralUI 3-basierten Komponenten. Bei dem neuen Satz handelt es sich nicht um eine bloße Kopie des alten Satzes, sondern um eine bereinigte Version (u. .a optimiert und ohne veraltete Funktionen). Entsprechend empfiehlt es sich, dass eine Seite entweder ausschließlich den CoralUI 3-basierten oder aber den CoralUI 2-basierten Satz verwendet.

To learn more in detail, refer to [Migration Guide to CoralUI 3-based](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### Wie lässt sich die Suchkomponente in AEM Assets anpassen? {#how-to-customize-the-search-component-in-aem-assets}

To learn about search boost/ranking and further implementation information, refer to [Simple search implementation guide.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

Bei der Implementierung der einfachen Suche handelt es sich um die Materialien vom Summit Lab „AEM Search Demystified“ von 2017.

### Wenn ein Kunde nur Sites-Lizenzen in AEM kauft, hat er dann trotzdem Zugriff auf Assets? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

Nein, der Kunde kann nicht auf Assets (oder andere als Sites) zugreifen. Auch wenn alle lokalen Komponenten von Adobe Experience Manager (AEM) in der JAR enthalten sind, ist der Kunde berechtigt, nur auf die Komponenten in der JAR zuzugreifen, für die er in seinem Vertrag lizenziert ist. Wenn sie andere Komponenten erkunden möchten, können sie entweder das AEM-Testprogramm für bis zu 45 Tage verwenden oder eine Verkaufsbestellung für $0 unterzeichnen, mit der sie zum Auswerten (ohne Produktionsverwendung) benannter Komponenten wie Assets berechtigt sind.

Weitere Informationen zu AEM On-Premise-Software und Adobe Managed Services finden Sie in den folgenden Ressourcen:

* [Adobe Experience Manager-On-Premise-Software](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### Wie kann ein Kunde die Standardeigenschaften einer Seite oder eines Assets erweitern? {#how-to-extend-default-properties-page-or-asset}

Informationen zum Erweitern der Standardeigenschaften einer Seite oder eines Assets finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Metadaten-Schemas in Assets](/help/assets/metadata-schemas.md)
* [Anpassen von Ansichten von Seiteneigenschaften](/help/sites-developing/page-properties-views.md)
