---
title: Social Component Framework
seo-title: Social Component Framework
description: Das Social Component Framework (SCF) vereinfacht den Prozess der Konfiguration, Anpassung und Erweiterung von Communities-Komponenten
seo-description: The social component framework (SCF) simplifies the process of configuring, customizing, and extending Communities components
uuid: 23b4418d-b91c-46fc-bf42-1154ef79fe5a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d7b5b5e3-2d84-4a6b-bcc2-d490882ff3ed
exl-id: 9264c888-a583-40eb-9178-273146f8a12b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1524'
ht-degree: 2%

---

# Social Component Framework {#social-component-framework}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Das Social Component Framework (SCF) vereinfacht die Konfiguration, Anpassung und Erweiterung von Communities-Komponenten auf Server- und Client-Seite.

Vorteile des Frameworks:

* **Funktionell**: Native Integration mit wenig oder gar keiner Anpassung für 80 % der Anwendungsfälle
* **Skinnierfähig**: Konsistente Verwendung von HTML-Attributen für CSS-Stile
* **Erweiterbar**: Die Komponentenimplementierung ist objektorientiert und basiert auf der Geschäftslogik - einfach hinzuzufügen, um eine inkrementelle Geschäftsanmeldung auf dem Server durchzuführen
* **Flexibel**: Einfache JavaScript-Vorlagen ohne Logik, die einfach überlagert und angepasst werden können
* **Zugänglich**: Die HTTP-API unterstützt das Posten von jedem Client, einschließlich mobiler Apps
* **Tragbar**: Integrieren/Einbetten in jede auf einer beliebigen Technologie basierende Webseite

Durchsuchen einer Autoren- oder Veröffentlichungsinstanz mithilfe des interaktiven [Handbuch zu Community-Komponenten](components-guide.md).

## Übersicht {#overview}

In SCF besteht eine Komponente aus einem SocialComponent POJO, einer Handlebars-JS-Vorlage (zum Rendern der Komponente) und CSS (zum Formatieren der Komponente).

Eine Handlebars-JS-Vorlage kann die JS-Komponenten model/view erweitern, um die Benutzerinteraktion mit der Komponente auf dem Client zu handhaben.

Wenn eine Komponente die Änderung von Daten unterstützen muss, kann die Implementierung der SocialComponent-API geschrieben werden, um die Bearbeitung/Speicherung von Daten ähnlich den Modell-/Datenobjekten in herkömmlichen Webanwendungen zu unterstützen. Darüber hinaus können Vorgänge (Controller) und ein Vorgangsdienst hinzugefügt werden, um Vorgangsanfragen zu verarbeiten, Geschäftslogik auszuführen und die APIs für die Modell-/Datenobjekte aufzurufen.

Die SocialComponent-API kann erweitert werden, um Daten bereitzustellen, die von einem Client für eine Ansichtsebene oder einen HTTP-Client benötigt werden.

### Darstellung von Seiten für Client {#how-pages-are-rendered-for-client}

![chlimage_1-25](assets/chlimage_1-25.png)

### Komponentenanpassung und -erweiterung {#component-customization-and-extension}

Um die Komponenten anzupassen oder zu erweitern, schreiben Sie nur die Überlagerungen und Erweiterungen in Ihr /apps-Verzeichnis, was die Aktualisierung auf zukünftige Versionen vereinfacht.

* für Skins
   * Nur die [Bearbeitung von CSS-Anforderungen](client-customize.md#skinning-css)
* Für Look and Feel
   * JS-Vorlage und CSS ändern
* Für Look, Feel und UX
   * JS-Vorlage, CSS und [Javascript erweitern/überschreiben](client-customize.md#extending-javascript)
* So ändern Sie die Informationen, die für die JS-Vorlage oder für den GET-Endpunkt verfügbar sind
   * Erweitern Sie die [SocialComponent](server-customize.md#socialcomponent-interface)
* Hinzufügen einer benutzerdefinierten Verarbeitung während Vorgängen
   * Eine [OperationExtension](server-customize.md#operationextension-class)
* So fügen Sie einen neuen benutzerdefinierten Vorgang hinzu
   * Erstellen Sie eine neue [Sling Post Operation](server-customize.md#postoperation-class)
   * Vorhandene verwenden [OperationServices](server-customize.md#operationservice-class) nach Bedarf
   * Fügen Sie bei Bedarf JavaScript-Code hinzu, um Ihren Vorgang vom Client aus aufzurufen.

## Server-seitiges Framework {#server-side-framework}

Das Framework stellt APIs für den Zugriff auf Funktionen auf dem Server und die Interaktion zwischen Client und Server bereit.

### Java-APIs {#java-apis}

Die Java-APIs bieten abstrakte Klassen und Schnittstellen, die einfach geerbt oder unterteilt werden können.

Die Hauptklassen werden im Abschnitt [Serverseitige Anpassung](server-customize.md) Seite.

Besuch [Übersicht über den Speicheranbieter](srp.md) , um mehr über die Arbeit mit UGC zu erfahren.

### HTTP-API {#http-api}

Die HTTP-API unterstützt die einfache Anpassung und Auswahl von Client-Plattformen für PhoneGap-Apps, native Apps und andere Integrationen und Mashups. Darüber hinaus ermöglicht die HTTP-API es einer Community-Site, als Dienst ohne Client ausgeführt zu werden, sodass Framework-Komponenten in jede auf einer beliebigen Technologie aufbauende Webseite integriert werden können.

### HTTP-API - GET-Anfragen {#http-api-get-requests}

Für jede SocialComponent stellt das Framework einen HTTP-basierten API-Endpunkt bereit. Der Zugriff auf den Endpunkt erfolgt durch Senden einer GET-Anfrage an die Ressource mit der Selektor + Erweiterung &quot;.social.json&quot;. Mit Sling wird die Anfrage an die `DefaultSocialGetServlet`.

Die `DefaultSocialGetServlet`

1. Übergibt die Ressource (resourceType) an die `SocialComponentFactoryManager`und erhält eine SocialComponentFactory, die eine `SocialComponent`die Ressource repräsentieren.

1. Ruft die Fabrik auf und erhält eine `SocialComponent`kann die Ressource und Anfrage verarbeiten.
1. Ruft die `SocialComponent`, der die Anfrage verarbeitet und eine JSON-Darstellung der Ergebnisse zurückgibt.
1. Gibt die JSON-Antwort an den Client zurück.

**`GET Request`**

Ein standardmäßiges GET-Servlet überwacht .social.json -Anfragen, auf die die SocialComponent mit anpassbarer JSON antwortet.

![chlimage_1-26](assets/chlimage_1-26.png)

### HTTP-API - POST-Anfragen {#http-api-post-requests}

Zusätzlich zu den GET (Lesen)-Vorgängen definiert das Framework ein Endpunktmuster, um andere Vorgänge für eine Komponente zu aktivieren, darunter Erstellen, Aktualisieren und Löschen. Diese Endpunkte sind HTTP-APIs, die Eingaben akzeptieren und entweder mit HTTP-Statuscodes oder mit einem JSON-Antwortobjekt antworten.

Dieses Framework-Endpunktmuster macht CUD-Vorgänge erweiterbar, wiederverwendbar und prüfbar.

**`POST Request`**

Für jeden Vorgang &quot;SocialComponent&quot;gibt es einen Sling-Vorgang POST:operation. Die Geschäftslogik und der Wartungscode für jeden Vorgang sind in einen OperationService eingeschlossen, auf den über die HTTP-API oder von einem anderen Ort aus als OSGi-Dienst zugegriffen werden kann. Erweiterungen von Plug-ins für Vor-/Nach-Aktionen werden über Erweiterungen von Erweiterungen bereitgestellt.

![chlimage_1-27](assets/chlimage_1-27.png)

### Storage Resource Provider (SRP) {#storage-resource-provider-srp}

Informationen zum Umgang mit benutzergenerierten Inhalten, die im [Community-Inhaltsspeicher](working-with-srp.md), siehe

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Repository-Nutzung - Übersicht
* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - Methoden und Beispiele für SRP-API-Dienstprogramme
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Kodierungsrichtlinien

### Serverseitige Anpassungen {#server-side-customizations}

Besuch [Serverseitige Anpassungen](server-customize.md) Informationen zum Anpassen der Geschäftslogik und des Verhaltens einer Communities-Komponente auf der Server-Seite.

## Handlebars JS-Vorlagensprache {#handlebars-js-templating-language}

Eine der auffälligsten Änderungen im neuen Framework ist die Verwendung der [Handlebars JS](https://handlebarsjs.com/) Vorlagensprache (HBS), eine beliebte Open-Source-Technologie für Server-Client-Rendering.

HBS-Skripte sind einfach, logiklos, auf dem Server und Client kompiliert, einfach zu überlagern und anzupassen und sind natürlich mit der Client-UX verbunden, da HBS das Client-seitige Rendering unterstützt.

Das Framework bietet mehrere [Handlebars-Helfer](handlebars-helpers.md) die bei der Entwicklung von SocialComponents nützlich sind.

Wenn Sling auf dem Server eine GET-Anfrage auflöst, identifiziert er das Skript, das zur Beantwortung der Anfrage verwendet wird. Wenn das Skript eine HBS-Vorlage (.hbs) ist, delegiert Sling die Anforderung an die Handlebars-Engine. Die Handlebars-Engine ruft dann die SocialComponent von der entsprechenden SocialComponentFactory ab, erstellt einen Kontext und rendert die HTML.

### Keine Zugriffsbeschränkung {#no-access-restriction}

Handlebars (HBS)-Vorlagendateien (.hbs) entsprechen .jsp- und .html-Vorlagendateien, können jedoch sowohl im Client-Browser als auch auf dem Server für die Wiedergabe verwendet werden. Daher erhält ein Client-Browser, der eine clientseitige Vorlage anfordert, eine .hbs-Datei vom Server.

Dies erfordert, dass alle HBS-Vorlagen im Sling-Suchpfad (alle .hbs-Dateien unter /libs/ oder /apps) von jedem Benutzer aus der Autoren- oder Veröffentlichungsinstanz abgerufen werden können.

HTTP-Zugriff auf .hbs-Dateien ist möglicherweise nicht verboten.

### Hinzufügen oder Einschließen einer Communities-Komponente {#add-or-include-a-communities-component}

Die meisten Communities-Komponenten müssen *hinzugefügt* als adressierbare Sling-Ressource. Einige der Communities-Komponenten können *enthalten* in einer Vorlage als nicht vorhandene Ressource, um eine dynamische Einbindung und Anpassung des Speicherorts zu ermöglichen, an dem benutzergenerierte Inhalte geschrieben werden (UGC).

In beiden Fällen wird die [erforderliche Client-Bibliotheken](clientlibs.md) auch vorhanden sein.

**Hinzufügen einer Komponente**

Das Hinzufügen einer Komponente bezieht sich auf den Prozess des Hinzufügens einer Instanz einer Ressource (Komponente), z. B. wenn diese aus dem Komponenten-Browser (Sidekick) auf eine Seite im Bearbeitungsmodus für Autoren gezogen wird.

Das Ergebnis ist ein untergeordneter JCR-Knoten unter einem par -Knoten, der Sling-adressierbar ist.

**Komponente einschließen**

Das Einschließen einer Komponente bezieht sich auf den Prozess des Hinzufügens eines Verweises zu einer [&quot;nicht vorhandene&quot;Ressource](srp.md#for-non-existing-resources-ners) (kein JCR-Knoten) innerhalb der Vorlage, z. B. mithilfe einer Skriptsprache.

Ab AEM 6.1 ist es möglich, die Eigenschaften der Komponente im Authoring *design *mode zu bearbeiten, wenn eine Komponente dynamisch eingeschlossen statt hinzugefügt wird.

Es können nur einige ausgewählte AEM Communities-Komponenten dynamisch eingeschlossen werden. Sie sind:

* [Kommentare](essentials-comments.md)
* [Bewertung](rating-basics.md)
* [Bewertungen](reviews-basics.md)
* [Abstimmung](essentials-voting.md)

Die [Handbuch zu Community-Komponenten](components-guide.md) ermöglicht es, einbeziehbare Komponenten von der Hinzufügung zur Einbindung umzuschalten.

**Bei Verwendung von Handlebars** Vorlagensprache: Die nicht vorhandene Ressource wird mithilfe der [include helper](handlebars-helpers.md#include) durch Angabe des Ressourcentyps:

`{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}`

**Bei Verwendung von JSP**, wird eine Ressource mithilfe des Tags eingeschlossen. [cq:include](../../help/sites-developing/taglib.md#lt-cq-include):

```
<cq:include path="votes" 
 resourceType="social/tally/components/voting" />
```

>[!NOTE]
>
>Informationen zum dynamischen Hinzufügen einer Komponente zu einer Seite finden Sie unter [Komponenten-Sideloading](sideloading.md).

### Handlebars Helpers {#handlebars-helpers}

Siehe [SCF Handlebars Helpers](handlebars-helpers.md) für eine Liste und Beschreibung der in SCF verfügbaren benutzerdefinierten Helfer.

## Client-seitiges Framework {#client-side-framework}

### JavaScript-Framework für Modellansichten {#model-view-javascript-framework}

Das Framework umfasst eine Erweiterung von [Backbone.js](https://www.backbonejs.org/), ein JavaScript-Framework zur Modellansicht, um die Entwicklung von komplexen, interaktiven Komponenten zu erleichtern. Die objektorientierte Natur unterstützt ein erweiterbares/wiederverwendbares Framework. Die Kommunikation zwischen Client und Server wird mithilfe der HTTP-API vereinfacht.

Das Framework nutzt serverseitige Handlebars-Vorlagen, um die Komponenten für den Client zu rendern. Die Modelle basieren auf den von der HTTP-API generierten JSON-Antworten. Die Ansichten binden sich an HTML, die von den Handlebars-Vorlagen generiert wurde, und bieten Interaktivität.

### CSS-Konventionen {#css-conventions}

Die folgenden Konventionen werden zum Definieren und Verwenden von CSS-Klassen empfohlen:

* Verwenden Sie eindeutig Namespace-CSS-Klassenselektornamen und vermeiden Sie allgemeine Namen wie &quot;Überschrift&quot;, &quot;Bild&quot;usw.
* Definieren Sie bestimmte Stile für Klassenselektoren, damit die CSS-Stylesheets mit anderen Elementen und Stilen auf der Seite gut funktionieren. Beispiel: `.social-forum .topic-list .li { color: blue; }`
* Halten Sie CSS-Klassen für die Formatierung getrennt von CSS-Klassen für UX, die von JavaScript gesteuert werden

### Clientseitige Anpassungen {#client-side-customizations}

Informationen zum Anpassen des Erscheinungsbilds und Verhaltens einer Communities-Komponente auf Client-Seite finden Sie unter [Clientseitige Anpassungen](client-customize.md), der Informationen zu enthält:

* [Überlagerungen](client-customize.md#overlays)
* [Erweiterungen](client-customize.md#extensions)
* [HTML Markup](client-customize.md#htmlmarkup)
* [Gestalten von CSS](client-customize.md#skinning-css)
* [JavaScript erweitern](client-customize.md#extending-javascript)
* [Clientlibs für SCF](client-customize.md#clientlibs-for-scf)

## Funktionen und Komponentengrundlagen {#feature-and-component-essentials}

Wesentliche Informationen für Entwickler werden im Abschnitt [Funktionen und Komponentengrundlagen](essentials.md) Abschnitt.

Weitere Entwicklerinformationen finden Sie im Abschnitt [Kodierungsrichtlinien](code-guide.md) Abschnitt.

## Fehlerbehebung {#troubleshooting}

Die allgemeinen Bedenken und bekannten Probleme werden im Abschnitt [Fehlerbehebung](troubleshooting.md) Abschnitt.
