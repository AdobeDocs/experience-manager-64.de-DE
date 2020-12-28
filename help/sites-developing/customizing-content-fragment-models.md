---
title: NICHT VERÖFFENTLICHEN, SONDERN KEIN DELETE ZUM Anpassen von Inhaltsfragmentmodellen
seo-title: Anpassen von Inhaltsfragmentmodellen
description: Inhaltsfragmentmodelle können angepasst und erweitert werden.
seo-description: Inhaltsfragmentmodelle können angepasst und erweitert werden.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 3%

---


# NICHT VERÖFFENTLICHEN, SONDERN KEIN DELETE ZUM Anpassen von Inhaltsfragmentmodellen{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

Der Editor des Inhaltsfragmentmodells ist ein Assistent, der auf `Formbuilder` basiert und von Folgendem geerbt wird:

`granite/ui/components/foundation/form/formbuilder`

Diese Komponente verfügt über die Werkzeuge, die zum Rendern der Drag &amp; Drop-Schnittstelle des Modelleditors erforderlich sind, inklusive der Datentypen und Eigenschaften für jede Komponente.

## Standorte {#locations}

Modelle werden unter `/conf` unter einem Ordner gespeichert und erstellt, in dem die Eigenschaft [Inhaltsfragmentmodelle](/help/assets/content-fragments-models.md#enable-content-fragment-models) aktiviert ist. Diese Einstellung ist auch im **Konfigurationseigenschaften** sichtbar, auf den Sie im **[Konfigurationsbrowser](/help/sites-administering/configurations.md)** zugreifen können.

1. Navigieren Sie zum Browser über **Tools**, **Allgemein**, **Konfigurationsbrowser**
Beispiel: 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. Wählen Sie im Browser die entsprechende Konfiguration und dann **Eigenschaften** aus der Symbolleiste.

   Die Eigenschaften für `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

In der Modellkonsole werden alle Ordner mit der Eigenschaft **Inhaltsfragmentmodelle** angezeigt. Navigieren Sie über **Tools**, **Assets**, **Inhaltsfragmentmodelle**; zum Beispiel `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Ein Benutzer kann [ein Inhaltsfragmentmodell mit dem Assistenten **Modell erstellen** erstellen (mit **Erstellen** aus der Konsole).](/help/assets/content-fragments-models.md#creating-a-content-fragment-model)

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
>
>Der Grund dafür ist, dass der Inhalt von `/libs` beim nächsten Aktualisieren der Instanz überschrieben wird (und möglicherweise überschrieben wird, wenn Sie einen Hotfix oder ein Feature Pack anwenden).

## Struktur eines Modells {#structure-of-a-model}

Der Assistent erstellt einen Eintrag mit der folgenden Struktur:

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   Alle Modelle werden unter Unterordnern dieses Ordners gespeichert.

* `jcr:content`

   Jedes Modell enthält einen `jcr:content`-Knoten, der Folgendes enthält:

   * enthält Informationseigenschaften zum Modell wie `jcr:title`, `lastModified`, `lastModifiedBy`
   * hat normalerweise den Wert `sling:ResourceType` von `dam/cfm/models/console/components/data/entity/default`,

      mit dem `sling:ResourceSuperType` von `dam/cfm/models/console/components/data/entity`

* `model`

   Der Knoten `model` enthält die Eigenschaft `dataTypesConfig`, mit der die im Modelleditor verwendeten Datentypen bestimmt werden.

* `items`

   Unter der Node `items` werden alle dem Modell hinzugefügten Datentypen gespeichert (wie im Modelleditor gezogen und abgelegt). Jedem Element wird ein zufälliger Knotenname zugewiesen. Damit jedoch der Inhaltsfragmenteditor mit diesem Modell funktioniert, muss jedes Element über eine `name`-Eigenschaft verfügen. Außerdem werden auf diesem Knoten alle Konfigurationseigenschaften für einen bestimmten Datentyp gespeichert, einschließlich der zum Rendern der Komponenten erforderlichen Standardeigenschaften.

>[!CAUTION]
>
>Alle Datentypen, die in einen Modelleditor gezogen und abgelegt wurden und daher instanziiert werden, müssen **die**-Eigenschaft vom Benutzer eingeben.`name`
>
>Dies wird als **Eigenschaftsname&amp;ast;** auf der Registerkarte **Eigenschaften** des Modelleditors betrachtet.

## Struktur des Modelleditors {#structure-of-the-model-editor}

Der **Content Fragment Model Editor** besteht aus zwei Teilen:

* Das Bedienfeld &quot;Vorschau&quot;oder &quot;Ansicht&quot;auf der linken Seite, in dem Sie Elemente ablegen können. Dies:

   * Zeigt eine Vorschau des instanziierten **Datentyps** an.
   * Ermöglicht die Bestellung im Modelleditor.

* Die Registerkarten **Datentypen**/**Eigenschaften** im Bedienfeld auf der rechten Seite. Dies:

   * Zeigt eine Liste von Datentypen an, die gezogen und instanziiert werden können.
   * Für den vordefinierten Modelleditor ist die Liste vorhanden unter:

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Alle gerenderten Datentypen haben zwei Skript-Tags, die bei Instanziierung die Ansicht (die auf der linken Seite gerenderte Komponente) und die Registerkarte **Eigenschaften** bilden, auf der die Eigenschaften definiert werden, die ein Benutzer für eine bestimmte Komponente definieren kann.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
>
>Der Grund dafür ist, dass der Inhalt von `/libs` beim nächsten Aktualisieren der Instanz überschrieben wird (und möglicherweise überschrieben wird, wenn Sie einen Hotfix oder ein Feature Pack anwenden).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Wenn ein Datentyp instanziiert wird, werden HTML-Eingaben für jede Eigenschaft erstellt, die die Komponente in einem Inhaltsfragment wiedergegeben werden muss. Dazu gehören beispielsweise:

* **Eigenschaftsname&amp;ast;** (  `name`) - fungiert als Bezeichner für Komponenten

* **Render As** (  `metaType`): Geben Sie die Komponente als

* **Beschreibung** (  `fieldDescription`) - Beschreibung der Komponente im Inhaltsfragment

* und mehr.

