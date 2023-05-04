---
title: Best Practices für SEO und URL-Verwaltung
seo-title: SEO and URL Management Best Practices
description: Erfahren Sie mehr über Best Practices und Empfehlungen für SEO, um diese bei einer AEM Implementierung zu erreichen.
seo-description: Learn about SEO best practices and recommendations for achieving these on an AEM implementation.
uuid: 7fffbe30-7cf8-44ce-b275-e128732577dd
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 150b43e3-9fb3-4c1c-b1cd-ccfd162974ad
exl-id: d45fe856-4709-437b-b193-e8243a695d2c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3133'
ht-degree: 72%

---

# Best Practices für SEO und URL-Verwaltung{#seo-and-url-management-best-practices}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Suchmaschinen-Optimierung (SEO) ist zu einem wichtigen Thema für viele Marketing-Fachleute geworden. Deshalb müssen SEO-Thematiken bei vielen AEM-Projekten berücksichtigt werden.

Dieses Dokument beschreibt zunächst einige [Best Practices für SEO](#seo-best-practices) und Empfehlungen zu deren Erreichung bei einer AEM-Implementierung. Anschließend beschäftigt sich das Dokument intensiver mit einigen der [komplexeren Implementierungsschritte](#aem-configurations) aus dem ersten Abschnitt.

## Best Practices für SEO {#seo-best-practices}

Dieser Abschnitt beschreibt einige allgemeine Best Practices für SEO

### URLs {#urls}

Es gibt einige allgemein anerkannte Best Practices in Bezug auf URLs.

Wenn Sie URLs für Ihr AEM-Projekt bewerten, stellen Sie sich die folgenden Fragen:

* „Wäre ein Benutzer in der Lage zu beschreiben, worum es auf der Seite geht, wenn er nur die URL und nicht den Inhalt der Seite sähe?“

Falls ja, dann ist es wahrscheinlich, dass die URL für eine Suchmaschine gut funktioniert.

Im Folgenden finden Sie einige allgemeine Tipps zum Erstellen Ihrer URLs für SEO:

* Verwenden Sie Bindestriche, um Wörter zu trennen.

   * Benennen Sie Seiten mit Bindestrichen (-) als Trennzeichen.
   * Vermeiden Sie die Verwendung von Binnenmajuskeln, Unterstrichen und Leerzeichen.

* Vermeiden Sie, wenn möglich, die Verwendung von Abfrageparametern. Beschränken Sie sie bei Bedarf auf zwei oder weniger.

   * Verwenden Sie die Verzeichnisstruktur, um die Informationsarchitektur anzugeben, sofern verfügbar.
   * Wenn eine Verzeichnisstruktur keine Option ist, verwenden Sie Sling-Selektoren anstelle von Abfragefolgen. Zusätzlich zum SEO-Wert, den sie bereitstellen, machen Sling-Selektoren die Seiten auch für den Dispatcher zwischenspeicherbar.

* Je menschlesbarer eine URL ist, desto besser; Wenn Suchbegriffe in der URL vorhanden sind, wird der Wert erhöht.

   * Bei der Verwendung von Selektoren auf einer Seite werden Selektoren bevorzugt, die semantischen Wert bieten.
   * Wenn ein Mensch Ihre URL nicht lesen kann, kann eine Suchmaschine auch nicht lesen.
   * Beispiel: `mybrand.com/products/product-detail.product-category.product-name.html` wird vorgezogen `mybrand.com/products/product-detail.1234.html`

* Vermeiden Sie Sub-Domains wo möglich, da Suchmaschinen diese als unterschiedliche Einheiten einordnen und so den SEO-Wert der Website fragmentieren.

   * Nutzen Sie stattdessen Unterpfade auf erster Ebene. Verwenden Sie beispielsweise `www.mybrand.com/es/home.html` statt `es.mybrand.com/home.html`.
   * Planen Sie Ihre Inhaltshierarchie entsprechend dieser Richtlinie so, wie der Inhalt dargestellt wird.

* Die Effektivität von Keywords in URLs nimmt bei mit zunehmender Länge der URL und späterer Position des Keywords ab. Mit anderen Worten, kürzer ist besser.

   * Verwenden Sie die von AEM bereitgestellten Methoden und Funktionen zur URL-Verkürzung, um unnötige URL-Teile zu entfernen.
   * Beispiel: `mybrand.com/en/myPage.html` wird `mybrand.com/content/my-brand/en/myPage.html` vorgezogen.

* Verwenden Sie kanonische URLs.

   * Wenn eine URL von unterschiedlichen Pfaden aus oder mit unterschiedlichen Parametern oder Selektoren bedient werden kann, stellen Sie sicher, dass Sie ein Tag `rel=canonical` auf der Seite verwenden.
   * Dies kann im Code für die AEM-Vorlage enthalten sein.

* Passen Sie URLs nach Möglichkeit mit Seitentiteln an.

   * Autoren von Inhalten sollten ermutigt werden, diese Vorgehensweise zu befolgen.

* Unterstützung der Groß-/Kleinschreibung bei URL-Anfragen.

   * Konfigurieren Sie den Dispatcher so, dass alle eingehenden Anforderungen in Kleinbuchstaben umgeschrieben werden.
   * Trainieren Sie Inhaltsautoren, um alle Seiten mit Kleinbuchstaben zu erstellen.

* Stellen Sie sicher, dass jede Seite nur von einem Protokoll bedient wird.

   * Manchmal werden Websites über `http` bedient, bis ein Benutzer eine Seite erreicht, die beispielsweise ein Zahlungsformular oder Anmeldeformular enthält, weswegen die Seite in das `https`-Format wechselt. Wenn von dieser Seite aus verlinkt wird und der Benutzer auf `http`-Seiten zurückkehren und auf diese über `https` zugreifen kann, verfolgt die Suchmaschine diese als zwei getrennte Seiten.
   * Google bevorzugt derzeit `https`-Seiten gegenüber `http`-Seiten. Aus diesem Grund ist es häufig für alle Beteiligten einfacher, die ganze Website über `https` zu bedienen.

### Server-Konfiguration {#server-configuration}

Hinsichtlich der Server-Konfiguration können Sie mit den folgenden Schritten gewährleisten, dass nur korrekte Inhalte durchsucht werden:

* Verwenden Sie eine `robots.txt`-Datei, um Crawling von nicht indizierten Inhalten zu vermeiden.

   * Block **all** Crawling in Testumgebungen.

* Implementieren Sie beim Start einer neuen Website mit aktualisierten URLs 301-Umleitungen, um sicherzustellen, dass Ihr vorhandenes SEO-Ranking nicht verloren geht.
* Fügen Sie eine Favicon für Ihre Site hinzu.
* Implementieren Sie eine XML-Sitemap, um Suchmaschinen das Durchsuchen des Inhalts zu erleichtern. Stellen Sie sicher, dass eine mobile Sitemap für mobile und/oder responsive Sites enthalten ist.

## AEM-Konfigurationen {#aem-configurations}

In diesem Abschnitt werden die notwendigen Implementierungsschritte für die AEM-Konfiguration zur Befolgung dieser SEO-Empfehlungen erläutert.

### Verwenden von Sling-Selektoren {#using-sling-selectors}

Früher war die Verwendung von Abfrageparametern allgemein akzeptierte Praxis bei der Erstellung einer Web-Anwendung für Unternehmen.

In den letzten Jahren geht der Trend jedoch dahin, diese zu entfernen, um URLs lesbarer zu gestalten. Bei vielen Plattform beinhaltet dies die Einführung von Weiterleitungen auf dem Webserver oder dem Content Delivery Network (CDN), Sling macht dies jedoch zu einem geradlinigeren Prozess. Sling-Selektoren:

* Verbessern der URL-Lesbarkeit.
* Sie können Ihre Seiten auf dem Dispatcher zwischenspeichern und verbessern häufig die Sicherheit.
* ermöglichen es, Inhalte direkt zu bearbeiten, anstelle der Verwendung eines allgemeinen Servlets zur Inhaltsabfrage. Dadurch erhalten Sie die Vorteile von ACLs, die Sie auf Ihr Repository anwenden, sowie von Filtern, die Sie auf den Dispatcher anwenden.

#### Verwenden von Selektoren für Servlets {#using-selectors-for-servlets}

AEM bietet uns zwei Optionen beim Schreiben von Servlets:

* bin-Servlets
* Sling-Servlets

Die folgenden Beispiele veranschaulichen, wie Servlets registriert werden, die diesen beiden Mustern folgen, sowie den Nutzen, den die Verwendung von Sling-Servlets bietet.

#### Container-Servlets (eine Ebene nach unten) {#bin-servlets-one-level-down}

Container-Servlets folgen dem Muster, das viele Entwickler für die J2EE-Programmierung verwenden. Das Servlet wird an einem bestimmten Punkt des Pfades registriert, was im Falle von AEM häufig unter `/bin` geschieht, und Sie extrahieren die erforderlichen Abfrageparameter aus der Abfragezeichenfolge.

Der SCR-Vermerk für diese Art von Servlet sieht in etwa so aus:

```
@SlingServlet(paths = "/bin/myApp/myServlet", extensions = "json", methods = "GET")
```

Sie extrahieren dann die Parameter aus der Abfragezeichenfolge über das `SlingHttpServletRequest`-Objekt, das beispielsweise in der `doGet`-Methode mit eingeschlossen ist:

```
String myParam = req.getParameter("myParam");
```

Die daraus resultierende URL könnte beispielsweise in etwa so aussehen:

`https://www.mydomain.com/bin/myApp/myServlet.json?myParam=myValue`

Bei diesem Ansatz sind einige Punkte zu berücksichtigen:

* Die URL selbst verliert den SEO-Wert. Benutzer, die auf die Site zugreifen, einschließlich Suchmaschinen, erhalten keinen semantischen Wert aus der URL, da die URL einen programmatischen Pfad und nicht die Inhaltshierarchie darstellt.
* Das Vorhandensein von Abfrageparametern in der URL bedeutet, dass der Dispatcher die Antwort nicht zwischenspeichern kann.
* Wenn Sie dieses Servlet sicher möchten, müssen Sie Ihre eigene benutzerdefinierte Sicherheitslogik in dieses Servlet implementieren.
* Der Dispatcher muss (sorgfältig) konfiguriert sein, um `/bin/myApp/myServlet` freizulegen. Das Freilegen von `/bin` würde Zugang zu Servlets erlauben, die nicht für Besucher der Website offen sein sollten.

#### Sling-Servlets (eine Ebene nach unten) {#sling-servlets-one-level-down}

Sling-Servlets ermöglichen die Registrierung von Servlets auf gegensätzliche Art und Weise. Anstatt ein Servlet zu adressieren und den Inhalt anzugeben, den das Servlet basierend auf den Abfrageparametern rendern soll, adressieren Sie den gewünschten Inhalt und geben das Servlet an, das den Inhalt basierend auf Sling-Selektoren rendern soll.

Der SCR-Vermerk für diese Art von Servlet sieht in etwa so aus:

```
@SlingServlet(resourceTypes = "myBrand/components/pages/myPageType", selectors = "myRenderer", extensions = "json”, methods=”GET”)
```

In diesem Fall ist die Ressource, welche die URL bedient (eine Instanz der `myPageType`-Ressource) in dem Servlet automatisch zugänglich. Um darauf zuzugreifen, rufen Sie Folgendes auf:

```
Resource myPage = req.getResource();
```

Die daraus resultierende URL könnte beispielsweise in etwa so aussehen:

`https://www.mydomain.com/content/my-brand/my-page.myRenderer.json`

Die Vorteile dieses Ansatzes sind:

* Sie können den SEO-Wert, gewonnen durch die Semantik in Ihrer Site-Hierarchie und im Seitennamen, backen.
* Da keine Abfrageparameter vorhanden sind, kann der Dispatcher die Antwort zwischenspeichern. Darüber hinaus wird dieser Cache durch alle an der adressierten Seite vorgenommenen Aktualisierungen invalidiert, wenn die Seite aktiviert wird.
* Alle auf `/content/my-brand/my-page` angewandten ACLs werden aktiv, wenn ein Benutzer versucht, auf dieses Servlet zuzugreifen.
* Der Dispatcher ist bereits konfiguriert, um diesen Inhalt als Bestandteil der Bedienung der Website zu bedienen. Es ist keine zusätzliche Konfiguration erforderlich.

### Umschreiben der URL {#url-rewriting}

In AEM werden all Ihre Websites unter `/content/my-brand/my-content` gespeichert. Während dies aus der Perspektive der Repository-Datenverwaltung nützlich sein kann, ist dies nicht notwendigerweise die Art und Weise, wie Ihre Kunden die Website sehen sollen, und kann im Widerspruch zu den SEO-Richtlinien stehen, URLs so kurz wie möglich zu halten. Zusätzlich kann es sein, dass Sie mehrere Websites von derselben AEM-Instanz und zwei unterschiedlichen Domain-Namen aus bedienen.

Dieser Abschnitt erläutert die verfügbaren AEM-Optionen zum Verwalten und zur Präsentation dieser URLs gegenüber dem Benutzer auf leichter lesbare, SEO-freundliche Weise.

#### Vanity-URLs {#vanity-urls}

Wenn ein Autor wünscht, dass die Seite von einem zweiten Ort aus für Werbezwecke zugänglich ist, können die auf Seitenbasis definierten Vanity-URLs von AEM nützlich sein. Um einer Seite eine Vanity-URL hinzuzufügen, rufen Sie sie in der Konsole **[!UICONTROL Sites]** auf und bearbeiten Sie die Seiteneigenschaften. Unten auf der Registerkarte **[!UICONTROL Allgemein]** sehen Sie einen Abschnitt, dem Vanity-URLs hinzugefügt werden können. Bedenken Sie, dass die Zugänglichkeit einer Seite über mehr als eine URL den SEO-Wert der Seite fragmentiert. Der Seite sollte also ein kanonisches URL-Tag hinzugefügt werden, um dieses Problem zu vermeiden.

#### Lokalisierte Seitennamen {#localized-page-names}

Sie möchten eventuell lokalisierte Seitennamen für Benutzer übersetzter Inhalte anzeigen. Beispiel:

* Anstatt einen Spanisch sprechenden Benutzer zur folgenden URL zu leiten:

   `www.mydomain.com/es/home.html`

* wäre folgende URL besser:

   `www.mydomain.com/es/casa.html`.

Die Herausforderung bei der Lokalisierung des Seitennamens besteht darin, dass viele der für die AEM-Plattform erhältlichen Lokalisierungs-Tools für die Synchronisierung von Inhalten identische Seitennamen für verschiedene Sprachen benötigen.

Die Eigenschaft `sling:alias` ermöglicht beides. `sling:alias` kann jeder Ressource als Eigenschaft hinzugefügt werden, um einen Alias für die Ressource zu erlauben. Im vorangegangenen Beispiel hätten Sie Folgendes:

* Eine Seite im JCR unter:

   `…/es/home`

* Dieser fügen Sie dann eine Eigenschaft hinzu:

   `sling:alias` = `casa`

Dies würde es den AEM-Übersetzungs-Tools wie dem Multi-Site-Manager ermöglichen, eine Beziehung zwischen folgenden Seiten beizubehalten:

* `/en/home`

* `/es/home`

während es Benutzern ermöglicht wird, in ihrer Muttersprache mit dem Seitennamen zu interagieren.

>[!NOTE]
>
> Die `sling:alias`-Eigenschaft kann [beim Bearbeiten der Seiteneigenschaften mithilfe der Alias-Eigenschaft](/help/sites-authoring/editing-page-properties.md#advanced) festgelegt werden

#### /etc/map {#etc-map}

Bei der Standardinstallation von AEM:

* für die OSGi-Konfiguration:

   **Apache Sling Resource Resolver Factory**

   (`org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl`)

* ist der Standardwert der Eigenschaft:

   **Zuordnungsspeicherort**

   (`resource.resolver.map.location`)

* standardmäßig auf:

   `/etc/map`

Zuordnungsdefinitionen können in diesem Verzeichnis hinzugefügt werden, um eingehende Anfragen zuzuordnen, URLs auf Seiten in AEM umzuschreiben oder beides.

Um eine neue Zuordnung zu erstellen, erstellen Sie einen neuen Knoten `sling:Mapping` in diesem Verzeichnis unter `/http` oder `/https`. Basierend auf den Eigenschaften `sling:match` und `sling:internalRedirect`, die für diesen Knoten eingestellt sind, leitet AEM sämtlichen Traffic für die passende URL an den in der Eigenschaft `internalRedirect` spezifizierten Wert weiter.

Während dies der Ansatz ist, der in der offiziellen AEM- und Sling-Dokumentation aufgeführt wird, ist die von dieser Implementierung bereitgestellte Unterstützung für reguläre Ausdrücke im Vergleich zu den Optionen begrenzt, die durch die direkte Verwendung von `SlingResourceResolver` zur Verfügung gestellt werden. Darüber hinaus kann die Implementierung von Zuordnungen auf diese Weise zu Problemen bei der Invalidierung des Dispatcher-Caches führen.

Ein Beispiel dafür, wie dieses Problem auftritt:

1. Ein Besucher fordert auf Ihrer Website `https://www.mydomain.com/my-page.html` an.
1. Der Dispatcher leitet diese Anfrage an den Veröffentlichungs-Server weiter.
1. Der Veröffentlichungs-Server verwendet `/etc/map`, löst die Anfrage zu `/content/my-brand/my-page` auf und stellt die Seite dar.

1. Der Dispatcher speichert die Antwort unter `/my-page.html` und leitet die Antwort zurück an den Benutzer.
1. Ein Inhaltsautor ändert diese Seite und aktiviert sie.
1. Der Flush-Agent des Dispatchers sendet eine Anfrage zur Invalidierung von `/content/my-brand/my-page`**.** Da der Dispatcher auf diesem Pfad keine Seite gespeichert hat, bleibt der alte Inhalt gespeichert und ist nicht mehr aktuell.

Es gibt Möglichkeiten, benutzerdefinierte Dispatch-Flush-Regeln zu konfigurieren, die die kürzere URL zur Invalidierung des Caches der längeren URL zuordnen.

Es gibt jedoch auch eine einfachere Möglichkeit, dies zu verwalten:

1. **SlingResourceResolver-Regeln**

   Mithilfe der Webkonsole (z. B. localhost:4502/system/console/configMgr) können Sie den Sling Resource Resolver konfigurieren:

   * **Apache Sling Resource Resolver Factory**

      `(org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl)`.
   Es wird empfohlen, die zur Kürzung von URLs zu regulären Ausdrücken notwendigen Zuordnungen zu erstellen und diese Konfigurationen dann unter einem OsgiConfignode, `config.publish`, zu definieren, der im Build enthalten ist.

   Anstatt Zuordnungen in `/etc/map` zu definieren, können diese direkt den Eigenschaften der **URL-Zuordnungen** (`resource.resolver.mapping`) zugeordnet werden:

   ```xml
   resource.resolver.mapping="[/content/my-brand/(.*)</$1]"
   ```

   In diesem einfachen Beispiel entfernen Sie `/content/my-brand/` von der Position am Anfang einer beliebigen URL.

   Dadurch würde eine URL umgewandelt:

   * von `/content/my-brand/my-page.html`
   * in `/my-page.html`

   Dies entspricht der empfohlenen Vorgehensweise, URLs so kurz wie möglich zu halten.

1. **Zuordnen der URL-Ausgabe auf Seiten**

   Nachdem Sie die Zuordnungen im Apache Sling Resource Resolver definiert haben, müssen Sie diese Zuordnungen in den Komponenten verwenden, um zu gewährleisten, dass die URLs auf Ihren Seiten kurz und ordentlich sind. Sie können dies durch die Verwendung der Zuordnungsfunktion `ResourceResolver` tun.

   Wenn Sie beispielsweise eine benutzerdefinierte Navigationskomponente implementieren, welche die untergeordneten Elemente der aktuellen Seite auflistet, können Sie die Zuordnungsmethode wie folgt verwenden:

   ```
   for (Page child : children) {
     String childUrl = resourceResolver.map(request, child.getPath());
     //Output the childUrl on the page here
   }
   ```

#### Apache HTTP-Server mod_rewrite {#apache-http-server-mod-rewrite}

Bisher haben Sie die Zuordnungen gemeinsam mit der Logik in den Komponenten implementiert, um diese Zuordnungen bei der Ausgabe von URLs auf Seiten zu verwenden.

Das letzte Teil des Puzzles besteht darin, diese gekürzten URLs zu verwalten, wenn sie beim Dispatcher ankommen, wobei `mod_rewrite` ins Spiel kommt. Der größte Vorteil bei der Verwendung von `mod_rewrite` besteht darin, dass die URLs zurück in ihre Langform gebracht werden, *bevor* sie an das Dispatcher-Modul gesendet werden. Das bedeutet, dass der Dispatcher die lange URL vom Veröffentlichungs-Server abfragt und diese entsprechend zwischenspeichert. Sämtliche vom Veröffentlichungs-Server ausgehenden Dispatcher-Flush-Anfragen können diesen Inhalt erfolgreich ungültig machen.

Um diese Regeln zu implementieren, können Sie `RewriteRule`-Elemente unter Ihrem virtuellen Host in der Apache HTTP Server-Konfiguration hinzufügen. Wenn Sie gekürzte URLs aus dem vorherigen Beispiel erweitern möchten, können Sie eine Regel implementieren, die folgendermaßen aussieht:

```
<VirtualHost *:80>
  ServerName www.mydomain.com
  RewriteEngine on
  RewriteRule ^/(.*)$ /content/my-brand/$1 [PT,L]
  …
</VirtualHost>
```

### Kanonische URL-Tags {#canonical-url-tags}

Kanonische URL-Tags sind Link-Tags, die in der Kopfzeile des HTML-Dokuments eingegeben werden und festlegen, wie Suchmaschinen die Seite bei der Indizierung des Inhalts behandeln sollen. Der Vorteil, den sie bieten, besteht darin, sicherzustellen, dass eine Seite (verschiedene Versionen) als dieselbe indiziert wird, selbst wenn die URL zur Seite Unterschiede enthalten kann.

Bietet eine Website beispielsweise eine druckfreundliche Version einer Seite an, könnte eine Suchmaschine diese Seite getrennt von der regulären Version der Seite indizieren. Das kanonische Tag teilt der Suchmaschine mit, dass sie identisch sind.

Beispiele:

* `https://www.mydomain.com/my-brand/my-page.html`
* `https://www.mydomain.com/my-brand/my-page.print.html`

Bei beiden würde das folgende Tag der Kopfzeile der Seite hinzugefügt:

```xml
<link rel=”canonical” href=”my-brand/my-page.html”/>
```

Das `href`-Attribut kann relativ oder absolut sein. Der Code sollte im Seiten-Layout inbegriffen sein, um die kanonische URL und das Ausgabe-Tag zu bestimmen.

### Konfigurieren des Dispatchers für das Ignorieren von Groß- und Kleinschreibung {#configuring-the-dispatcher-for-case-insensitivity}

Die Best Practice besteht darin, alle Seiten mit Kleinbuchstaben zu bedienen. Sie möchten jedoch nicht, dass ein Benutzer einen 404-Wert erhält, wenn er mithilfe von Großbuchstaben in seiner URL auf Ihre Website zugreift. Aus diesem Grund empfiehlt Adobe, dass Sie eine Umschreiberegel in der Apache HTTP Server-Konfiguration hinzufügen, um alle eingehenden URLs in Kleinbuchstaben darzustellen. Darüber hinaus müssen Autoren dahingehend geschult werden, Seiten nur mit Namen in Kleinbuchstaben zu erstellen.

Um Apache so zu konfigurieren, dass sämtlicher eingehender Traffic in Kleinbuchstaben erfolgt, fügen Sie der Konfiguration `vhost` Folgendes hinzu:

```xml
RewriteEngine On
RewriteMap lowercase int:tolower
```

Fügen Sie zusätzlich Folgendes am Anfang der Datei `htaccess` hinzu:

```xml
RewriteCond $1 [A-Z]
RewriteRule ^(.*)$ /${lowercase:$1} [R=301,L]
```

### Implementieren von robots.txt zum Schutz von Entwicklungsumgebungen {#implementing-robots-txt-to-protect-development-environments}

Suchmaschinen *sollten* das Vorhandensein einer Datei `robots.txt` im Stammverzeichnis der Website überprüfen, bevor die Website durchsucht wird. „Sollten“ wird hier betont, weil die meistverwendeten Suchmaschinen wie Google, Yahoo oder Bing dies befolgen, einige andere Suchmaschinen jedoch nicht.

Die einfachste Möglichkeit, den Zugang zu der gesamten Website zu blockieren, ist eine Datei namens `robots.txt` im Stammverzeichnis der Website zu platzieren, die Folgendes enthält:

```xml
User-agent: *
Disallow: /
```

Wahlweise können Sie in einer Live-Umgebung bestimmte Pfade ablehnen, die nicht indiziert werden sollen.

Der Nachteil der Platzierung einer Datei `robots.txt` im Stammverzeichnis der Website besteht darin, dass Dispatcher-Flush-Anfragen diese Datei löschen könnten und die URL-Zuordnungen den Site-Stamm wahrscheinlich an einen anderen Ort als `DOCROOT` verschieben, wie in der Apache HTTP Server-Konfiguration festgelegt. Aus diesem Grund ist es üblich, diese Datei in der Autoreninstanz am Site-Stamm zu platzieren und sie in der Veröffentlichungsinstanz zu replizieren.

### Erstellen einer XML-Sitemap in AEM {#building-an-xml-sitemap-on-aem}

Crawler verwenden XML-Sitemaps, um die Website-Strukturen besser zu verstehen. Während es keine Garantie dafür gibt, dass die Bereitstellung einer Sitemap zu verbesserten SEO-Rankings führt, ist dies dennoch eine allgemein anerkannte Best Practice. Sie können eine XML-Datei auf dem Webserver manuell als Sitemap verwalten. Es wird jedoch empfohlen, die Sitemap programmatisch zu generieren. Dadurch wird sichergestellt, dass die Sitemap automatisch die Änderungen widerspiegelt, wenn Autoren neue Inhalte erstellen.

Um eine Sitemap programmatisch zu generieren, registrieren Sie einen Sling-Servlet-Listener für eine `sitemap.xml`-Anfrage. Das Servlet kann dann die über die Servlet-API bereitgestellten Ressourcen verwenden, um die aktuelle Seite und deren untergeordnete Elemente zu sehen, und gibt dabei XML aus. Die XML-Datei wird dann vom Dispatcher zwischengespeichert. Auf diesen Ort sollte in den Sitemap-Eigenschaften der Datei `robots.txt` verwiesen werden. Zusätzlich muss eine benutzerdefinierte Flush-Regel implementiert werden, um zu gewährleisten, dass diese Datei geleert wird, wann immer eine neue Seite aktiviert wird.

>[!NOTE]
>
>Sie können ein Sling-Servlet registrieren, um auf den `sitemap`-Selektor mit der Endung `xml` zu warten. Dies führt zur Verarbeitung der Anfrage durch das Servlet, wenn eine URL angefordert wird, die wie folgt endet:
>
>`/<*path-to*>/page.sitemap.xml`
>
>Anschließend können Sie die angeforderte Ressource aus der Anfrage abrufen und von diesem Punkt in der Inhaltsstruktur mithilfe der JCR-APIs eine Sitemap generieren.
>
>Ein solcher Ansatz ist dann vorteilhaft, wenn mehrere Sites von derselben Instanz bedient werden. Eine Anfrage an `/content/siteA.sitemap.xml` würde eine Sitemap für `siteA` generieren, während eine Anfrage an `/content/siteB.sitemap.xml` eine Sitemap für `siteB` generieren würde, ohne dass zusätzlicher Code geschrieben werden muss.

### Erstellen von 301-Weiterleitungen für veraltete URLs {#creating-redirects-for-legacy-urls}

Beim Start einer Website mit einer neuen Struktur ist die Implementierung und Prüfung von 301-Weiterleitungen in Apache HTTP Server aus zwei Gründen wichtig:

* Die veralteten URLs bauen über die Zeit hinweg SEO-Wert auf. Durch Implementierung einer Umleitung kann die Suchmaschine diesen Wert auf die neue URL anwenden.
* Benutzer der Website könnten Lesezeichen für diese Seiten erstellt haben. Durch Implementierung von Umleitungen können Sie sicherstellen, dass der Benutzer auf die Seite auf der neuen Site geleitet wird, die am ehesten dem entspricht, wo er versucht hat, auf die alte Site zu gelangen.

Überprüfen Sie unbedingt den folgenden Abschnitt mit zusätzlichen Ressourcen , um Anweisungen zur Implementierung von 301-Weiterleitungen sowie ein Tool zum Testen der erwarteten Funktionsweise Ihrer Weiterleitungen zu erhalten.

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen finden Sie in den folgenden zusätzlichen Ressourcen:

* [Ressourcenzuordnung](/help/sites-deploying/resource-mapping.md)
* [https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url](https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url)
* [https://moz.com/blog/15-seo-best-practices-for-structuring-urls](https://moz.com/blog/15-seo-best-practices-for-structuring-urls)
* [https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/](https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/)
* [https://sling.apache.org/documentation/the-sling-engine/servlets.html](https://sling.apache.org/documentation/the-sling-engine/servlets.html)
* [https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
* [https://httpd.apache.org/docs/current/mod/mod_rewrite.html](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)
* [https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps](https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps)
* [https://en.wikipedia.org/wiki/Robots_exclusion_standard](https://en.wikipedia.org/wiki/Robots_exclusion_standard)
* [https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/](https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/)
* [https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester)
* [https://adobe-consulting-services.github.io/](https://adobe-consulting-services.github.io/)
