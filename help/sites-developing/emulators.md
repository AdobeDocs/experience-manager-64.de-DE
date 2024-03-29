---
title: Emulatoren
seo-title: Emulators
description: AEM ermöglicht es Autoren, eine Seite in einem Emulator anzuzeigen, der die Umgebung simuliert, in der ein Endbenutzer die Seite anzeigt
seo-description: AEM enables authors to view a page in an emulator that simulates the environment in which an end-user will view the page
uuid: ee1496a5-be68-4318-b5ce-b11c41e4485c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: mobile-web
content-type: reference
discoiquuid: c51fca81-5dfc-4838-9672-acb6de62778b
legacypath: /content/docs/en/aem/6-0/develop/mobile/emulators
exl-id: 2abbceaa-928e-47d8-81c9-ba5bc24f27e2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 69%

---

# Emulatoren{#emulators}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mit Adobe Experience Manager (AEM) können Autoren eine Seite in einem Emulator anzeigen, der die Umgebung simuliert, in der ein Endbenutzer die Seite anzeigt, z. B. auf einem Mobilgerät oder in einem E-Mail-Client.

Das AEM-Emulator-Framework:

* ermöglicht Content-Authoring in einer simulierten Benutzeroberfläche, z. B. auf einem mobilen Gerät oder in einem E-Mail-Client (zum Erstellen von Newslettern).
* passt den Seiteninhalt entsprechend der simulierten Benutzeroberfläche an.
* ermöglicht das Erstellen benutzerdefinierter Emulatoren.

>[!CAUTION]
>
>Diese Funktion wird nur in der klassischen Benutzeroberfläche unterstützt.

## Emulatormerkmale {#emulators-characteristics}

Emulator:

* basiert auf ExtJS.
* Bearbeitet das Seiten-DOM.
* Das Erscheinungsbild wird über CSS geregelt.
* Unterstützt Plug-ins (z. B. das Plug-in für die Mobilgeräterotation).
* Ist nur auf der Autoreninstanz aktiv.
* Die Basiskomponente befindet sich unter `/libs/wcm/emulator/components/base`.

### Umwandlung des Inhalts durch den Emulator {#how-the-emulator-transforms-the-content}

Der Emulator funktioniert durch Einschließen des HTML-Hauptinhalts in Emulator-DIVs. Der folgende HTML-Code:

```xml
<body>
<div id="wrapper" class="page mobilecontentpage ">
    <div class="topnav mobiletopnav">
    ...
    </div>
    ...
</div>
</body>
```

wird beispielsweise nach dem Starten des Emulators in folgenden HTML-Code geändert:

```xml
<body>
 <div id="cq-emulator-toolbar">
 ...
 </div>
 <div id="cq-emulator-wrapper">
  <div id="cq-emulator-device">
   <div class=" android vertical" id="cq-emulator">
    ...
    <div class=" android vertical" id="cq-emulator-content">
     ...
     <div id="wrapper" class="page mobilecontentpage">
     ...
     </div>
     ...
    </div>
   </div>
  </div>
 </div>
 ...
</body>
```

Zwei DIV-Tags wurden hinzugefügt:

* das DIV-Tag mit der ID `cq-emulator`, das den gesamten Emulator beinhaltet, und

* das DIV-Tag mit der ID `cq-emulator-content`, das den Viewport-, Bildschirm- oder Inhaltsbereich repräsentiert, in dem sich der Seiteninhalt befindet.

Den neuen DIV-Tags des Emulators werden auch neue CSS-Klassen zugewiesen. Sie stellen den Namen des aktuellen Emulators dar.

Die Plug-ins eines Emulators können die Liste der zugeordneten CSS-Klassen zusätzlich erweitern, wie beim Beispiel des Drehungs-Plug-ins, das je nach aktueller Drehung auf dem Gerät die Klasse „vertical“ oder „horizontal“ einfügen.

So kann die vollständige Darstellung des Emulators durch die Verwendung von CSS-Klassen gesteuert werden, die den IDs und CSS-Klassen der Emulator-DIVs entsprechen.

>[!NOTE]
>
>Es wird empfohlen, dass die Projekt-HTML den Hauptteilinhalt wie im obigen Beispiel in ein div einbindet. Wenn der Hauptteilinhalt mehrere Tags enthält, kann es zu unvorhersehbaren Ergebnissen kommen.

### Mobile Emulatoren {#mobile-emulators}

Die vorhandenen mobilen Emulatoren:

* Sie befinden sich unter /libs/wcm/mobile/components/emulators.
* sind über dasJSON-Servlet verfügbar unter:

   http://localhost:4502/bin/wcm/mobile/emulators.json

Wenn die Seitenkomponente auf die mobile Seitenkomponente (`/libs/wcm/mobile/components/page`) angewiesen ist, ist die Emulatorfunktion automatisch durch folgenden Mechanismus in die Seite integriert:

* Die mobile Seitenkomponente `head.jsp` beinhaltet die der Gerätegruppe zugeordnete Initialisierungskomponente des Emulators (nur im author-Modus) und Rendering-CSS durch:

   `deviceGroup.drawHead(pageContext);`

* Die Methode `DeviceGroup.drawHead(pageContext)` enthält die Inititialisierungskomponente des Emulators, d. h., sie ruft die `init.html.jsp` der Emulatorkomponente auf. Falls die Emulatorkomponente nicht über eine eigene `init.html.jsp` verfügt, sondern auf den mobilen Basisemulator (`wcm/mobile/components/emulators/base)`) angewiesen ist, wird das Initialisierungsskript des mobilen Basisemulators (`/libs/wcm/mobile/components/emulators/base/init.html.jsp`) aufgerufen.

* Das Initialisierungsskript des mobilen Basisemulators definiert über JavaScript Folgendes:

   * Die Konfiguration für alle Emulatoren, die für die Seite definiert sind (emulatorConfigs)
   * Der Emulator-Manager, der die Funktionalität des Emulators in die Seite über Folgendes integriert:

      `emulatorMgr.launch(config)`;

      Der Emulator-Manager wird durch Folgenders definiert:

      `/libs/wcm/emulator/widgets/source/EmulatorManager.js`

#### Erstellen eines benutzerdefinierten Mobile Emulators {#creating-a-custom-mobile-emulator}

So erstellen Sie einen benutzerdefinierten mobilen Emulator:

1. Erstellen Sie unterhalb von `/apps/myapp/components/emulators` die Komponente `myemulator` (Knotentyp: `cq:Component`).

1. Legen Sie die `sling:resourceSuperType`-Eigenschaft auf `/libs/wcm/mobile/components/emulators/base` fest.

1. Definieren Sie eine CSS-Client-Bibliothek mit der Kategorie `cq.wcm.mobile.emulator` für das Erscheinungsbild des Emulators: Name = `css`, Knotentyp = `cq:ClientLibrary`.

   Beispielsweise können Sie auf den Knoten `/libs/wcm/mobile/components/emulators/iPhone/css` verweisen.

1. Definieren Sie bei Bedarf eine JS-Client-Bibliothek, um beispielsweise ein bestimmtes Plug-in zu definieren: Name = js, Knotentyp = cq:ClientLibrary.

   Beispielsweise können Sie auf den Knoten `/libs/wcm/mobile/components/emulators/base/js` verweisen.

1. Wenn der Emulator bestimmte, durch Plug-ins definierte Funktionen unterstützt (z. B. Touch-Scrolling), erstellen Sie einen Konfigurationsknoten unterhalb des Emulators: Name = `cq:emulatorConfig`, Knotentyp = `nt:unstructured` und fügen Sie die Eigenschaft hinzu, die das Plug-in definiert:

   * Name = `canRotate`, Typ = `Boolean`, Wert = `true`: um die Rotationsfunktion einzuschließen.

   * Name = `touchScrolling`, Typ = `Boolean`, Wrt = `true`: fum die Funktion „Touch-Scrolling“ einzuschließen.
   Sie können weitere Funktionen hinzufügen, indem Sie eigene Plug-ins definieren.
