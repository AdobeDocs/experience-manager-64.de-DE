---
title: Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche
seo-title: Creating a New Granite UI Field Component
description: Die Granite-Benutzeroberfläche bietet eine Reihe von Komponenten, die für die Verwendung in Formularen entwickelt wurden, so genannte Felder
seo-description: Granite UI provides a range of components designed to be used in forms, called fields
uuid: cf26e057-4b0c-45f4-8975-2c658517f20e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 94b9eeee-aae3-4b28-9d6f-1be0e4acd982
exl-id: 9a6cc25e-e54e-4b8a-8fdd-bcd65d8fe601
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 40%

---

# Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche{#creating-a-new-granite-ui-field-component}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Granite-Benutzeroberfläche bietet eine Reihe von Komponenten, die für die Verwendung in Formularen entwickelt wurden. diese *fields* im Vokabular der Granite-Benutzeroberfläche. Die standardmäßigen Granite-Formularkomponenten sind unter verfügbar:

`/libs/granite/ui/components/foundation/form/*`

>[!NOTE]
>
>Diese Formularfelder der Granite-Benutzeroberfläche sind von besonderem Interesse, da sie für [Komponentendialogfelder](/help/sites-developing/developing-components.md).

>[!NOTE]
>
>Ausführliche Informationen zu Feldern finden Sie im [Dokumentation zur Granite-Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html).

Verwenden Sie das Foundation-Framework der Granite-Benutzeroberfläche, um Granite-Komponenten zu entwickeln und/oder zu erweitern. Dies umfasst zwei Elemente:

* Server-seitig:

   * eine Sammlung von Foundation-Komponenten

      * foundation - modular, zusammenstellbar, schichtfähig, wiederverwendbar
      * Komponenten – Sling-Komponenten
   * Helfer zur Unterstützung der Anwendungsentwicklung


* clientseitig:

   * eine Sammlung von Client-Bibliotheken, die ein Vokabular bereitstellen (d. h. Erweiterung der HTML-Sprache), um generische Interaktionsmuster über eine durch Hypermedia gesteuerte Benutzeroberfläche zu erreichen.

Die generische Komponente `field` der Granite-Benutzeroberfläche beinhaltet zwei wichtige Dateien:

* `init.jsp`: Übernimmt die generische Verarbeitung sowie Beschriftung und Beschreibung und liefert den für das Rendern des Felds erforderlichen Formularwert.
* `render.jsp`: Übernimmt das tatsächliche Rendern des Felds und muss für das benutzerdefinierte Feld überschrieben werden; ist in `init.jsp` enthalten.

Weitere Informationen finden Sie unter [Granite-UI-Dokumentation - Feld](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/field/index.html) , wenn Sie weitere Details wünschen.

Beispiele finden Sie hier:

* `cqgems/customizingfield/components/colorpicker`

   * im Abschnitt [Codebeispiel](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `granite/ui/components/foundation/form`

>[!NOTE]
>
>Da dieser Mechanismus JSP verwendet, werden i18n und XSS nicht nativ bereitgestellt. Das bedeutet, dass Sie Ihre Zeichenfolgen internationalisieren und maskieren müssen. Das folgende Verzeichnis enthält die generischen Felder einer Standardinstanz. Sie können diese als Referenz verwenden:
>
>`/libs/granite/ui/components/foundation/form`-Verzeichnis

## Erstellen des serverseitigen Skripts für die Komponente {#creating-the-server-side-script-for-the-component}

Das benutzerdefinierte Feld sollte das `render.jsp`-Skript nur überschreiben, wenn Sie das Markup für die Komponente angeben. Das JSP (d. h. das Render-Skript) ist dabei quasi der Wrapper für das Markup.

1. Erstellen Sie eine neue Komponente, die die `sling:resourceSuperType`-Eigenschaft zum Erben aus

   `/libs/granite/ui/components/foundation/form/field`

1. Überschreiben Sie das Skript:

   `render.jsp`

   In diesem Skript müssen Sie das Hypermedia-Markup (d. h. angereichertes Markup, das die Hypermedia-Bezahlbarkeit enthält) generieren, damit der Client weiß, wie er mit dem generierten Element interagiert. Dies sollte dem serverseitigen Kodierungsstil der Granite-Benutzeroberfläche entsprechen.

   Bei der Anpassung *müssen* Sie nur festlegen, dass der (in `init.jsp` initialisierte) Formularwert wie folgt aus der Anforderung gelesen wird:

   ```
   // Delivers the value of the field (read from the content)
   ValueMap vm = (ValueMap) request.getAttribute(Field.class.getName());
   vm.get("value, String.class"); 
   ```

   Weitere Informationen finden Sie im Abschnitt zur Implementierung von vorkonfigurierten Feldern der Granite-Benutzeroberfläche, beispielsweise `/libs/granite/ui/components/foundation/form/textfield`.

   >[!NOTE]
   >
   >Derzeit ist JSP die bevorzugte Skriptmethode, da die Übergabe von Informationen von einer Komponente an eine andere (was im Kontext von Formular/Feldern recht häufig vorkommt) in HTL nicht einfach möglich ist.

## Erstellen der Client-Bibliothek für die Komponente {#creating-the-client-library-for-the-component}

Gehen Sie wie folgt vor, um der Komponente ein bestimmtes Client-seitiges Verhalten hinzuzufügen:

1. Erstellen Sie eine Client-Bibliothek der Kategorie `cq.authoring.dialog`.
1. Erstellen Sie eine Client-Bibliothek der Kategorie `cq.authoring.dialog` und definieren Sie darin Ihr `JS`/ `CSS` darin.

   Definieren Sie Ihr `JS`/ `CSS` in der Client-Bibliothek.

   >[!NOTE]
   >
   >Derzeit bietet die Granite-Benutzeroberfläche keine nativen Listener oder Hooks, die Sie direkt zum Hinzufügen von JS-Verhalten verwenden können. Um Ihrer Komponente also zusätzliches JS-Verhalten hinzuzufügen, müssen Sie einen JS-Hook in eine benutzerdefinierte Klasse implementieren, die Sie dann während der Markup-Generierung Ihrer Komponente zuweisen.
