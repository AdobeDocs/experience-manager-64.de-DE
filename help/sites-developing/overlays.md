---
title: Überlagerungen
seo-title: Overlays
description: AEM nutzt das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen zu erweitern und anzupassen.
seo-description: AEM uses the principle of overlays to allow you to extend and customize the consoles and other functionality
uuid: d14c08fe-04c0-4925-8c99-c6644357919d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0470b74c-2c34-4327-afed-b95eefb1d521
exl-id: c0678bb6-5e57-4ebb-b6dc-5240bafbc79e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 68%

---

# Überlagerungen{#overlays}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM (und davor, CQ) verwendet seit langem das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die [Konsolen](/help/sites-developing/customizing-consoles-touch.md) und anderen Funktionen (z. B. [Seitenbearbeitung](/help/sites-developing/customizing-page-authoring-touch.md)).

Der Begriff „Überlagerung“ kann in unterschiedlichen Zusammenhängen verwendet werden. In diesem Kontext (Erweiterung der AEM) bedeutet eine Überlagerung, die vordefinierten Funktionen zu übernehmen und eigene Definitionen darüber aufzuzwingen (um die Standardfunktionalität anzupassen).

In einer Standardinstanz befindet sich die vordefinierte Funktion unter `/libs` und es empfiehlt sich, die Überlagerung (Anpassungen) unter der Verzweigung `/apps` zu definieren. AEM verwendet einen Suchpfad, um eine Ressource zu finden, wobei zuerst die Verzweigung `/apps` und dann die Verzweigung `/libs` durchsucht wird ([der Suchpfad kann konfiguriert werden](#configuring-the-search-paths)). Durch diesen Mechanismus hat Ihre Überlagerung (und die dort definierten Anpassungen) Priorität.

Seit AEM 6.0 wurden Änderungen an der Implementierung und Verwendung von Überlagerungen vorgenommen:

* Ab AEM 6.0 – für [Granite](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)-bezogene Überlagerungen (d. h. Touch-optimierte Benutzeroberfläche)

   * Methode

      * Rekonstruieren Sie die entsprechende `/libs`-Struktur unter `/apps`.

         Dies erfordert keine 1:1-Kopie, der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) wird verwendet, um die erforderlichen Originaldefinitionen zu vergleichen. Der Sling Resource Merger stellt Services für den Zugriff auf und die Zusammenführung von Ressourcen mittels Vergleichsmechanismen bereit.

      * Nehmen Sie beliebige Änderungen unter `/apps` vor.
   * Vorteile

      * Robuster gegenüber Änderungen unter `/libs`.
      * Nur die erforderlichen Aspekte müssen neu definiert werden.


* Überlagerungen, die nicht aus Granite stammen, und Überlagerungen in Versionen vor AEM 6.0 

   * Methode

      * Kopieren der Inhalte von `/libs` nach `/apps`

         Sie müssen die gesamte Unterverzweigung einschließlich der Eigenschaften kopieren.

      * Nehmen Sie beliebige Änderungen unter `/apps` vor.
   * Nachteile

      * Obwohl Ihre Änderungen nicht verloren gehen, wenn sich etwas unter `/libs` ändert, müssen Sie möglicherweise bestimmte Änderungen in Ihrer Überlagerung unter `/apps` neu erstellen.


>[!CAUTION]
>
>Der [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) und die zugehörigen Methoden können nur mit [Granite](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html) verwendet werden. Das bedeutet, dass die Erstellung einer Überlagerung mit einem Strukturgerüst nur für die standardmäßige Touch-optimierte Benutzeroberfläche geeignet ist.
>
>Überlagerungen für andere Bereiche (einschließlich der klassischen Benutzeroberfläche) umfassen das Kopieren des entsprechenden Knotens und der gesamten Unterstruktur und dann die erforderlichen Änderungen.

Überlagerungen sind die empfohlene Methode für viele Änderungen, z. B. [Konfigurieren der Konsolen](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) oder [Erstellen der Auswahlkategorie für den Asset-Browser im Seitenbereich](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (wird beim Erstellen von Seiten verwendet). Sie sind aus folgenden Gründen erforderlich:

* Sie dürfen ***keine* Änderungen in der Verzweigung `/libs` vornehmen.**Jegliche Änderungen, die Sie vornehmen, können verloren gehen, da diese Verzweigung in den folgenden Fällen Änderungen unterliegt:

   * Aktualisierung auf Ihrer Instanz
   * Hotfix anwenden
   * Feature Pack installieren

* Überlagerungen bündeln Ihre Änderungen an zentraler Stelle und erleichtern es Ihnen, Ihre Änderungen zu verfolgen, zu migrieren, zu sichern und/oder zu debuggen.

## Konfigurieren der Suchpfade {#configuring-the-search-paths}

Bei Überlagerungen handelt es sich bei der bereitgestellten Ressource um ein Aggregat der abgerufenen Ressourcen und Eigenschaften, je nach den zu definierenden Suchpfaden:

* Der **Suchpfad des Ressourcen-Resolvers** wie in der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) für die **Apache Sling-Resource Resolver Factory** definiert

   * Die von oben nach unten sortierte Reihenfolge der Suchpfade gibt die jeweiligen Prioritäten an.
   * In einer Standardinstallation sind die primären Standardwerte `/apps`, `/libs` – der Inhalt von `/apps` hat also eine höhere Priorität als der von `/libs`, (d. h. er *überlagert* diesen).

* Zwei Dienstbenutzer benötigen JCR:READ-Zugriff auf den Speicherort der Skripte. Diese Benutzer sind: „components-search-service“ (verwendet von den com.day.cq.wcm.coreto access/cache-Komponenten) und „sling-scripting“ (verwendet von „org.apache.sling.servlets.resolver“, um Servlets zu finden).
* Die folgende Konfiguration muss außerdem so konfiguriert werden, dass sie dem Speicherort für Ihre Skripte entspricht (in diesem Beispiel unter /etc, /libs oder /apps).

   ```
   PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
   resource.resolver.searchpath=["/etc","/apps","/libs"]
   resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
   ```

* Schließlich muss noch der Servlet Resolver konfiguriert werden (in diesem Beispiel auch, um /etc hinzuzufügen).

   ```
   PID = org.apache.sling.servlets.resolver.SlingServletResolver  
   servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
   ```

## Anwendungsbeispiel {#example-of-usage}

Einige Beispiele werden behandelt, wenn:

* [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md)
* [Anpassung des Seiten-Authorings](/help/sites-developing/customizing-page-authoring-touch.md)
