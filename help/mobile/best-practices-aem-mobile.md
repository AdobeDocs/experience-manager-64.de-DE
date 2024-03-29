---
title: Best Practices
seo-title: Best Practices
description: Auf dieser Seite erfahren Sie Best Practices und Richtlinien, die erfahrenen AEM-Entwicklern für Sites helfen, die Vorlagen und Komponenten für mobile Apps erstellen möchten.
seo-description: Follow this page to  learn best practices and guidelines that will help experienced AEM developers for sites, who want to build mobile app templates and components.
uuid: 7733c8b1-a88c-455c-8080-f7add4205b92
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: a0647696-72c3-409b-85ba-9275d8f99cff
exl-id: 042974ee-2c0a-411d-accf-6a17b8e95f90
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 5%

---

# Best Practices {#best-practices}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Das Erstellen einer AEM Mobile On-demand Services-App unterscheidet sich vom Erstellen einer App, die direkt in der Cordova- (oder PhoneGap-)Shell ausgeführt wird. Die Entwickler sollten mit folgenden Themen vertraut sein:

* Plug-ins, die standardmäßig unterstützt werden, sowie die AEM Mobile-spezifischen Plug-ins.

>[!NOTE]
>
>Ausführliche Informationen zu Plug-ins finden Sie in den folgenden Ressourcen:
>
>* [Verwenden von Cordova-Plug-ins in AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/cordova-api.html)
>* [Verwenden von AEM Mobile-spezifischen Cordova-aktivierten Plug-ins](https://helpx.adobe.com/digital-publishing-solution/help/app-runtime-api.html)
>


* Vorlagen, die Plug-in-Funktionen verwenden, sollten so geschrieben werden, dass sie im Browser noch autorierbar sind, ohne dass die Plug-in-Verbindung vorhanden ist.

   * Achten Sie beispielsweise darauf, auf die *Abflussgetreide* -Funktion, bevor versucht wird, auf die API eines Plug-ins zuzugreifen.

## Richtlinien für AEM Entwickler {#guidelines-for-aem-developers}

Die folgenden Richtlinien helfen erfahrenen AEM-Entwicklern für Sites, die mobile App-Vorlagen und -Komponenten erstellen möchten:

**Strukturieren AEM Sites-Vorlagen zur Förderung der Wiederverwendung und Erweiterbarkeit**

* Mehrere Komponentenskriptdateien über eine einzige monolithische

   * Es werden eine Reihe leerer Erweiterungspunkte bereitgestellt, z. B. *customheaderlibs.html* und *customfooterlibs.html*, die es dem Entwickler ermöglichen, die Seitenvorlage zu ändern und dabei möglichst wenig Kerncode zu duplizieren
   * Vorlagen können dann über die von Sling *sling:resourceSuperType* Mechanismus

* Sightly/HTL über JSP als Vorlagensprache bevorzugen

   * Dadurch wird eine Trennung von Code und Markup gefördert, bietet integrierten XSS-Schutz und verfügt über eine vertrautere Syntax.

**Optimieren der Leistung auf dem Gerät**

* Artikelspezifische Skript- und Stylesheets sollten in die Artikelnutzlast aufgenommen werden, indem die Vorlage contentsync des Artikels dps-article verwendet wird.
* Skript- und Stylesheets, die von mehr als einem Artikel gemeinsam verwendet werden, sollten über die Vorlage &quot;dps-HTMLResources contentsync&quot;in freigegebenen Ressourcen enthalten sein
* Referenzieren Sie keine externen Skripte, die Render-Blocking sind

>[!NOTE]
>
>Ausführlichere Informationen zu Render-Blocking-externen Skripten [here](https://developers.google.com/speed/docs/insights/BlockingJS).

**App-spezifische clientseitige JS- und CSS-Bibliotheken im Vergleich zu webspezifischen**

* So vermeiden Sie Mehraufwand in Bibliotheken wie jQuery Mobile für die Verarbeitung einer großen Bandbreite von Geräten und Browsern
* Wenn eine Vorlage in der Webansicht einer App ausgeführt wird, haben Sie die Kontrolle über die Plattformen und Versionen, die von der App unterstützt werden, sowie über das Wissen, dass JavaScript-Unterstützung vorhanden sein wird. Nehmen wir beispielsweise an, dass Sie Ionic (vielleicht nur CSS) gegenüber jQuery Mobile und Onsen UI vorziehen.

>[!NOTE]
>
>Um mehr über jQuery Mobile zu erfahren, klicken Sie auf [here](https://jquerymobile.com/browser-support/1.4/).

**Mikrobibliotheken über Vollstapel bevorzugen**

* Die Zeit, die benötigt wird, um Ihren Inhalt auf das Glas des Geräts zu bringen, wird durch jede Bibliothek, von der Ihre Artikel abhängen, verlangsamt. Diese Verlangsamung wird verstärkt, wenn eine neue Webansicht zum Rendern jedes Artikels verwendet wird. Daher muss jede Bibliothek von Grund auf neu initialisiert werden
* Wenn Ihre Artikel nicht als SPA (Einzelseiten-Apps) erstellt wurden, müssen Sie wahrscheinlich keine vollständige Stapelbibliothek wie Angular einschließen.
* Verwenden Sie kleinere Bibliotheken mit einem Zweck, um die Interaktivität hinzuzufügen, die Ihre Seite benötigt, z. B. [Fastclick](https://github.com/ftlabs/fastclick) oder [Velocity.js](https://velocityjs.org)

**Minimieren der Artikelnutzlast**

* Verwenden Sie die kleinstmöglichen Assets, die den größten von Ihnen unterstützten Viewport effektiv abdecken können, und zwar bei einer angemessenen Auflösung.
* Verwenden Sie ein Tool wie *ImageOptim* auf Ihren Bildern, um überschüssige Metadaten zu entfernen

## Erste Schritte {#getting-ahead}

Weitere Informationen zu den beiden anderen Rollen und Zuständigkeiten finden Sie in den folgenden Ressourcen:

* [Administrator](/help/mobile/aem-mobile.md)
* [Autor](/help/mobile/aem-mobile-on-demand.md)
