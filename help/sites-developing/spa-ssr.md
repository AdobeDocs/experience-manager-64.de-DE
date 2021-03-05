---
title: Single Page Applications (SPAs) und Server-seitiges Rendering
seo-title: Single Page Applications (SPAs) und Server-seitiges Rendering
description: 'null'
seo-description: 'null'
uuid: fbf7d0d1-865d-45d2-aeec-a7e3caf3fcb2
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 30d25772-0df7-468e-bcbd-c6fb2e962662
translation-type: tm+mt
source-git-commit: 226cd6688a579409371cb17f6ba31548bee312b3
workflow-type: tm+mt
source-wordcount: '1711'
ht-degree: 65%

---


# Single Page Applications (SPAs) und Server-seitiges Rendering {#spa-and-server-side-rendering}

>[!NOTE]
>Für die Funktion &quot;SPA-Editor&quot;für Einzelseitenanwendungen ist [AEM 6.4 Service Pack 2](https://helpx.adobe.com/de/experience-manager/6-4/release-notes/sp-release-notes.html) oder höher erforderlich.
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, bei denen SPA Framework-basiertes clientseitiges Rendering (z.B. React oder Angular) erforderlich ist.

>[!NOTE]
>
>AEM Version 6.4.5.0 oder höher ist erforderlich, um die Renderingfunktionen auf SPA Server zu verwenden, wie in diesem Dokument beschrieben.

## Überblick {#overview}

Einzelseitenanwendungen (SPA) können dem Benutzer ein umfangreiches, dynamisches Erlebnis bieten, das auf vertraute Weise reagiert und funktioniert, oft genau wie native Anwendungen. [Dies wird erreicht, indem man sich darauf verlässt, dass der Client den Inhalt im Voraus lädt und dann die Benutzerinteraktion erheblich erleichtert](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) und so den Kommunikationsaufwand zwischen Client und Server minimiert, wodurch die App reaktionsfähiger wird.

Dies kann jedoch zu längeren anfänglichen Ladezeiten führen, insbesondere wenn die SPA groß und inhaltsreich ist. Um die Ladezeit zu optimieren, können einige Inhalte Server-seitig gerendert werden. Die Verwendung von Server-seitigem Rendering (SSR) kann das anfängliche Laden der Seite beschleunigen und dann das weitere Rendering an den Client weitergeben.

## Verwendung von SSR {#when-to-use-ssr}

SSR ist nicht bei allen Projekten erforderlich. Obwohl AEM JS SSR für SPA vollständig unterstützt, empfiehlt Adobe nicht, es systematisch für jedes Projekt zu implementieren.

Wenn Sie sich für die Implementierung von SSR entscheiden, müssen Sie zunächst abschätzen, welche zusätzliche Komplexität, welchen Aufwand und welche Kosten das Hinzufügen von SSR für das Projekt realistisch darstellt, einschließlich der langfristigen Wartung. Eine SSR-Architektur sollte nur dann gewählt werden, wenn der Mehrwert die geschätzten Kosten deutlich übersteigt.

SSR bietet in der Regel einen gewissen Mehrwert, wenn eine der folgenden Fragen klar mit Ja beantwortet werden kann:

* **SEO:** Ist SSR tatsächlich noch erforderlich, damit Ihre Website von den Suchmaschinen, die Traffic bringen, richtig indiziert wird? Denken Sie daran, dass die wichtigsten Suchmaschinen-Crawler jetzt JS auswerten.
* **Seitengeschwindigkeit:** Bietet SSR eine messbare Geschwindigkeitsverbesserung in Echtzeit-Umgebungen? Steigert SSR das Kundenerlebnis insgesamt?

Nur wenn mindestens eine dieser beiden Fragen mit einem klaren Ja für Ihr Projekt beantwortet wird, empfiehlt Adobe die Implementierung von SSR. In den folgenden Abschnitten wird beschrieben, wie Sie dies mit Adobe I/O Runtime erreichen.

## Adobe I/O Runtime {#adobe-io-runtime}

Wenn Sie [sicher sind, dass Ihr Projekt die Implementierung von SSR](#when-to-use-ssr) erfordert, empfiehlt die Adobe die Verwendung von Adobe I/O Runtime.

Weitere Informationen zu Adobe I/O Runtime finden Sie unter

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) – Überblick über den Service
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) – ausführliche Dokumentation der Plattform.

In den folgenden Abschnitten wird erläutert, wie Sie mit Adobe I/O Runtime SSR für Ihre SPA in zwei verschiedenen Modellen implementieren können:

* [AEM-gesteuerter Kommunikationsfluss](#aem-driven-communication-flow)
* [Adobe I/O-Runtime-Driven Communication Flow](#adobe-io-driven-communication-flow)

>[!NOTE]
>
>Adobe empfiehlt für jede AEM-Umgebung eine separate Adobe I/O Runtime-Instanz (Autor, Veröffentlichung, Staging usw.).

## Remote Content Renderer-Konfiguration {#remote-content-renderer-configuration}

AEM muss wissen, wo der Remote-gerenderte Inhalt abgerufen werden kann. Unabhängig davon, welches Modell Sie für SSR](#adobe-io-runtime) implementieren, müssen Sie angeben, wie Sie auf diesen Remote-Rendering-Dienst zugreifen AEM.[

Dies geschieht über den **** RemoteContentRenderer – Configuration Factory OSGi-Service. Suchen Sie in der Konsole „Web-Konsolen-Konfiguration“ unter `http://<host>:<port>/system/console/configMgr` nach der Zeichenfolge „RemoteContentRenderer“.

![](assets/rendererconfig.png)

Folgende Felder stehen für die Konfiguration zur Verfügung:

* **Inhaltspfadmuster**: Regulärer Ausdruck, um bei Bedarf einen Inhaltsbereich zuzuordnen
* **Remote-Endpunkt-URL**: URL des Endpunkts, der für die Erstellung des Inhalts verantwortlich ist
   * Verwenden Sie das gesicherte HTTPS-Protokoll, wenn Sie sich nicht im lokalen Netzwerk befinden.
* **Zusätzliche Anfrage-Header**: Zusätzliche Header, die der an den Remote-Endpunkt gesendeten Anfrage hinzugefügt werden.
   * Muster: `key=value`
* **Zeitüberschreitung bei Anfrage**: Zeitüberschreitung bei Remote-Host-Anfragen in Millisekunden

>[!NOTE]
>
>Unabhängig davon, ob Sie den [AEM-basierten Kommunikationsfluss](#aem-driven-communication-flow) oder den [Adobe I/O Runtime-basierten Fluss](#adobe-io-driven-communication-flow) implementieren möchten, müssen Sie eine Remote-Konfiguration des Inhalts-Renderers definieren.
>
>Diese Konfiguration muss auch definiert werden, wenn Sie [einen benutzerdefinierten Node.js-Server](#using-node-js) verwenden.

>[!NOTE]
>
>Diese Konfiguration nutzt den [Remote Content Renderer](#remote-content-renderer), der über zusätzliche Erweiterungs- und Anpassungsoptionen verfügt.

## AEM-gesteuerter Kommunikationsfluss {#aem-driven-communication-flow}

Bei Verwendung von SSR umfasst der [Arbeitsablauf für Komponenteninteraktion](/help/sites-developing/spa-overview.md#workflow) von SPA in AEM eine Phase, in der der ursprüngliche Inhalt der App von Adobe I/O Runtime generiert wird.

1. Der Browser fordert den SSR-Inhalt von AEM an.
1. AEM sendet das Modell an Adobe I/O Runtime.
1. Adobe I/O Runtime gibt den generierten Inhalt zurück
1. AEM stellt den von Adobe I/O Runtime über die HTML-Vorlage der Backend-Seitenkomponente zurückgegebenen HTML-Code bereit.

![server-side-rendering-cms-drivenaemnode](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

### Adobe I/O Runtime-gesteuerter Kommunikationsfluss {#adobe-io-driven-communication-flow}

Der Abschnitt [AEM-Driven Communication Flow](#aem-driven-communication-flow) beschreibt die standardmäßige und empfohlene Implementierung des serverseitigen Renderings in Bezug auf SPA in AEM, bei dem AEM das Bootstrapping und Bereitstellen von Inhalten durchführt.

Alternativ kann SSR so implementiert werden, dass Adobe I/O Runtime für das Bootstrapping verantwortlich ist, wodurch der Kommunikationsfluss effektiv umgekehrt wird.

Beide Modelle sind gültig und werden von AEM unterstützt. Vor der Einführung eines bestimmten Modells sollten jedoch die Vor- und Nachteile jedes einzelnen Modells berücksichtigt werden.

| Bootstrapping | Vorteile | Nachteile |
|---|---|---|
| über AEM | AEM verwaltet injizierende Bibliotheken bei Bedarf<br>Ressourcen müssen nur auf AEM | Möglicherweise SPA-Entwicklern nicht bekannt |
| über Adobe I/O Runtime | SPA-Entwicklern besser bekannt | Clientlib-Ressourcen, die für die Anwendung erforderlich sind, wie CSS und JavaScript, müssen vom AEM-Entwickler über die [`allowProxy`-Eigenschaft](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)<br>Ressourcen bereitgestellt werden, die zwischen AEM und Adobe I/O Runtime<br>synchronisiert werden müssen, damit das Authoring der SPA aktiviert werden kann, muss möglicherweise ein Proxyserver für Adobe I/O Runtime erforderlich sein |

## Planung für SSR {#planning-for-ssr}

Im Allgemeinen muss nur ein Teil einer Anwendung Server-seitig gerendert werden. Das gängige Beispiel ist, dass der Inhalt, der über der Kante beim ersten Laden der Seite angezeigt wird, serverseitig gerendert werden muss. Das spart Zeit, indem bereits gerenderte Inhalte an den Client gesendet werden. Wenn der Benutzer mit der SPA interagiert, wird der zusätzliche Inhalt vom Client gerendert.

Wenn Sie erwägen, das serverseitige Rendering für Ihre SPA zu implementieren, müssen Sie überprüfen, welche Teile der App SSR erfordern.

## Entwickeln einer SPA mit SSR {#developing-an-spa-using-ssr}

SPA-Komponenten können vom Client (im Browser) oder vom Server gerendert werden. Beim Server-seitigen Rendern sind keine Browser-Eigenschaften wie Fenstergröße und -position vorhanden. Daher sollten SPA-Komponenten isomorph sein und keine Annahme darüber machen, wo sie gerendert werden.

Um SSR zu nutzen, müssen Sie Ihren Code sowohl in AEM als auch in Adobe I/O Runtime bereitstellen, das für das Server-seitige Rendering verantwortlich ist. Der größte Teil des Codes ist gleich, jedoch unterscheiden sich die Server-spezifischen Aufgaben.

## SSR für SPAs in AEM {#ssr-for-spas-in-aem}

SSR für SPAs in AEM erfordert Adobe I/O Runtime, das für das Rendering des App-Inhalts auf der Server-Seite aufgerufen wird. Innerhalb der HTL der App wird eine Ressource in Adobe I/O Runtime aufgerufen, um den Inhalt zu rendern.

So wie AEM die SPA-Frameworks Angular und React standardmäßig unterstützt, wird auch das Server-seitige Rendering für Angular- und React-Anwendungen unterstützt. Weitere Informationen finden Sie in der NPM-Dokumentation für beide Frameworks.

* Reaktion: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Ein einfaches Beispiel finden Sie in der [We.Retail-Protokoll-App](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Es rendert die gesamte Anwendungsserverseite. Obwohl dies kein echtes Beispiel ist, zeigt es doch, was zur Umsetzung der Reform des Sicherheitssektors erforderlich ist.

>[!CAUTION]
>Die [We.Retail-Protokoll-App](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) dient nur zu Demonstrationszwecken und verwendet daher Node.js als einfaches Beispiel anstelle des empfohlenen Adobe I/O Runtime. Dieses Beispiel sollte für keine Projektarbeit verwendet werden.

>[!NOTE]
>Jedes AEM-Projekt sollte den [AEM-Projektarchetyp](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/overview.html) nutzen, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA-SDK nutzt.

## Verwenden von Node.js {#using-node-js}

Adobe I/O Runtime ist die empfohlene Lösung für die Implementierung von SSR für SPA in AEM.

Bei Instanzen, die auf einer AEM ausgeführt werden, ist es auch möglich, SSR mit einer benutzerdefinierten Node.js-Instanz zu implementieren, wie oben beschrieben. Obwohl dies von Adobe unterstützt wird, wird es nicht empfohlen.

Node.js wird für Instanzen, die von Adoben gehostet AEM, nicht unterstützt.

>[!NOTE]
>
>Wenn SSR über Node.js implementiert werden muss, empfiehlt Adobe eine separate Node.js-Instanz für jede AEM Umgebung (Autor, Veröffentlichung, Stage usw.).

## Remote Content Renderer {#remote-content-renderer}

Die [Remote Content Renderer-Konfiguration](#remote-content-renderer-configuration), die für die Verwendung von SSR mit Ihrer SPA in AEM erforderlich ist, greift auf einen allgemeineren Rendering-Service zurück, der erweitert und an Ihre Bedürfnisse angepasst werden kann.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` ist ein OSGi-Service zum Abrufen von Inhalten, die auf einem Remote-Server wiedergegeben werden, z. B. von Adobe I/O. Der an den Remote-Server gesendete Inhalt basiert auf dem übergebenen Anfrageparameter.

`RemoteContentRenderingService` kann durch Umkehrung der Abhängigkeit entweder in ein benutzerdefiniertes Sling-Modell oder Servlet eingefügt werden, wenn zusätzliche Inhaltsmanipulationen erforderlich sind.

Dieser Service wird intern vom [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet) verwendet.

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

Mit dem `RemoteContentRendererRequestHandlerServlet` können Sie die Anfragekonfiguration programmgesteuert einstellen. `DefaultRemoteContentRendererRequestHandlerImpl`, die bereitgestellte standardmäßige Implementierung des Anfrage-Handlers, ermöglicht es Ihnen, mehrere OSGi-Konfigurationen zu erstellen, um einen Punkt in der Inhaltsstruktur einem Remote-Endpunkt zuzuordnen.

Implementieren Sie die `RemoteContentRendererRequestHandler`-Schnittstelle, um einen benutzerdefinierten Anfrage-Handler hinzuzufügen. Stellen Sie sicher, dass die Komponenteneigenschaft `Constants.SERVICE_RANKING` auf eine ganze Zahl größer als 100 gesetzt wird, was der Rangfolge von `DefaultRemoteContentRendererRequestHandlerImpl` entspricht.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Konfigurieren der OSGi-Konfiguration des Standard-Handlers {#configure-default-handler}

Die Konfiguration des Standard-Handlers muss wie im Abschnitt [Remote Content Renderer-Konfiguration](#remote-content-renderer-configuration) beschrieben konfiguriert werden.

###  Verwendung des Remote Content Renderers {#usage}

So lassen Sie ein Servlet Inhalte abrufen und zurückgeben, die in die Seite eingefügt werden können:

1. Stellen Sie sicher, dass auf den Remote-Server zugegriffen werden kann.
1. Fügen Sie der HTL-Vorlage einer AEM-Komponente eines der folgenden Snippets hinzu.
1. Optional können Sie die OSGi-Konfigurationen erstellen oder ändern.
1. Durchsuchen Sie den Inhalt Ihrer Site.

In der Regel ist die HTL-Vorlage einer Seitenkomponente der wichtigste Empfänger einer solchen Funktion.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Voraussetzungen {#requirements}

Die Servlets verwenden den Sling Model Exporter, um die Komponentendaten zu serialisieren. Standardmäßig werden sowohl `com.adobe.cq.export.json.ContainerExporter` als auch `com.adobe.cq.export.json.ComponentExporter` als Sling-Modell-Adapter unterstützt. Bei Bedarf können Sie Klassen hinzufügen, an die die Anfrage angepasst werden soll, um das `RemoteContentRendererServlet` zu verwenden und das `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses` zu implementieren. Die zusätzlichen Klassen müssen den `ComponentExporter` erweitern.
