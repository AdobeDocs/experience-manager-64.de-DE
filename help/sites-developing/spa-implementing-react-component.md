---
title: Implementieren einer Reaktionskomponente für SPA
seo-title: Implementing a React Component for SPA
description: In diesem Artikel wird ein Beispiel dafür vorgestellt, wie eine einfache, vorhandene React-Komponente für die Verwendung mit dem AEM-SPA-Editor angepasst werden kann.
seo-description: This article presents an example of how to adapt a simple, existing React component to work with the AEM SPA Editor.
uuid: aebca2ea-a020-45e1-8043-f8c21154c660
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 86a981fe-25f3-451a-b262-8c497619e0ac
exl-id: da0e076b-afb7-4ebe-8e5e-48c00750e453
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 19%

---

# Implementieren einer Reaktionskomponente für SPA{#implementing-a-react-component-for-spa}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten in der Lage sein, Websites mithilfe von SPA-Frameworks zu erstellen, und Autoren möchten Inhalte innerhalb von AEM für eine Website, die mit SPA-Frameworks erstellt wurde, nahtlos bearbeiten.

Die SPA-Erstellungsfunktion bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. In diesem Artikel wird ein Beispiel dafür vorgestellt, wie eine einfache, vorhandene React-Komponente für die Verwendung mit dem AEM-SPA-Editor angepasst werden kann.

>[!NOTE]
>Für die Funktion &quot;Single Page Application (SPA) Editor&quot;ist AEM Service Pack 2 (oder höher) 6.4 erforderlich.
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, die SPA Framework-basiertes Client-seitiges Rendering erfordern (z. B. React oder Angular).

## Einführung {#introduction}

Dank des einfachen und leichten Vertrags, der von AEM benötigt und zwischen dem SPA und dem SPA Editor etabliert wird, ist es einfach, eine vorhandene JavaScript-Anwendung zu verwenden und sie für die Verwendung mit einer SPA in AEM anzupassen.

Dieser Artikel veranschaulicht das Beispiel der Wetterkomponente im Beispiel-SPA &quot;We.Retail Journal&quot;.

Sie sollten mit dem [Struktur einer SPA Anwendung für AEM](/help/sites-developing/spa-getting-started-react.md) vor dem Lesen dieses Artikels.

>[!CAUTION]
>Dieses Dokument verwendet die [We.Retail Journal-App](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) nur zu Demonstrationszwecken. Sie sollte nicht für Projektaufgaben verwendet werden.
>
>Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/overview.html) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA SDK verwendet.

## Die Wetterkomponente {#the-weather-component}

Die Wetterkomponente befindet sich oben links in der App &quot;We.Retail Journal&quot;. Es zeigt das aktuelle Wetter einer definierten Position an, wobei Wetterdaten dynamisch abgerufen werden.

### Verwenden des Wetter-Widgets {#using-the-weather-widget}

![screen_shot_2018-06-08at143224](assets/screen_shot_2018-06-08at143224.png)

Beim Bearbeiten von Inhalten des SPA im SPA Editor wird die Wetterkomponente wie jede andere AEM-Komponente angezeigt, mit einer Symbolleiste gefüllt und kann bearbeitet werden.

![screen_shot_2018-06-08at143304](assets/screen_shot_2018-06-08at143304.png)

Die Stadt kann in einem Dialogfeld wie jede andere AEM aktualisiert werden.

![screen_shot_2018-06-08at143446](assets/screen_shot_2018-06-08at143446.png)

Die Änderung wird beibehalten und die Komponente wird automatisch mit neuen Wetterdaten aktualisiert.

![screen_shot_2018-06-08at143524](assets/screen_shot_2018-06-08at143524.png)

### Implementierung der Wetterkomponente {#weather-component-implementation}

Die Wetterkomponente basiert tatsächlich auf einer öffentlich zugänglichen React-Komponente namens [React Open Weather](https://www.npmjs.com/package/react-open-weather), das an die Verwendung als Komponente in der SPA &quot;We.Retail Journal&quot;angepasst wurde.

Im Folgenden finden Sie Ausschnitte aus der NPM-Dokumentation zur Verwendung der React Open Weather-Komponente.

![screen_shot_2018-06-08at144723](assets/screen_shot_2018-06-08at144723.png) ![screen_shot_2018-06-08at144215](assets/screen_shot_2018-06-08at144215.png)

Überprüfen des Codes der angepassten Wetterkomponente ( `Weather.js`) in der Anwendung &quot;We.Retail Journal&quot;:

* **Zeile 16**: Das React Open Weather-Widget wird nach Bedarf geladen.
* **Zeile 46**: Die `MapTo` -Funktion verknüpft diese React-Komponente mit einer entsprechenden AEM, sodass sie im SPA Editor bearbeitet werden kann.

* **Zeilen 22-29**: Die `EditConfig` definiert ist, wird überprüft, ob die Stadt ausgefüllt wurde, und der Wert wird definiert, wenn leer.

* **Zeilen 31-44**: Die Wetterkomponente erweitert die `Component` -Klasse und stellt die erforderlichen Daten bereit, wie in der NPM-Nutzungsdokumentation für die React Open Weather-Komponente definiert, und rendert die Komponente.

```javascript
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 ~ Copyright 2018 Adobe Systems Incorporated
 ~
 ~ Licensed under the Apache License, Version 2.0 (the "License");
 ~ you may not use this file except in compliance with the License.
 ~ You may obtain a copy of the License at
 ~
 ~     https://www.apache.org/licenses/LICENSE-2.0
 ~
 ~ Unless required by applicable law or agreed to in writing, software
 ~ distributed under the License is distributed on an "AS IS" BASIS,
 ~ WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 ~ See the License for the specific language governing permissions and
 ~ limitations under the License.
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
import React, {Component} from 'react';
import ReactWeather from 'react-open-weather';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Weather.css');

const WeatherEditConfig = {

    emptyLabel: 'Weather',

    isEmpty: function() {
        return !this.props || !this.props.cq_model || !this.props.cq_model.city || this.props.cq_model.city.trim().length < 1;
    }
};

class Weather extends Component {

    render() {
        let apiKey = "12345678901234567890";
        let city;

        if (this.props.cq_model) {
            city = this.props.cq_model.city;
            return <ReactWeather key={'react-weather' + Date.now()} forecast="today" apikey={apiKey} type="city" city={city} />
        }

        return null;
    }
}

MapTo('we-retail-journal/global/components/weather')(Weather, WeatherEditConfig);
```

Obwohl bereits eine Back-End-Komponente vorhanden sein muss, kann der Frontend-Entwickler die React Open Weather-Komponente im We.Retail Journal-SPA mit sehr wenig Kodierung nutzen.

## Nächster Schritt {#next-step}

Weitere Informationen zur Entwicklung von SPA für AEM finden Sie in diesem Artikel [Entwickeln von SPA für AEM](/help/sites-developing/spa-architecture.md).
