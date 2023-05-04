---
title: NICHT VERÖFFENTLICHEN, ABER KEIN DELETE ZUM Anpassen von Inhaltsfragmentmodellen
seo-title: Customizing Content Fragment Models
description: Inhaltsfragmentmodelle können angepasst und erweitert werden.
seo-description: Content Fragment Models can be customized and extended.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: AEM Docs
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 13%

---


# NICHT VERÖFFENTLICHEN, ABER KEIN DELETE ZUM Anpassen von Inhaltsfragmentmodellen{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Inhaltsfragmentmodell-Editor ist ein Assistent, der auf `Formbuilder`, geerbt von:

`granite/ui/components/foundation/form/formbuilder`

Diese Komponente verfügt über die Tools, die zum Rendern der Drag-and-Drop-Oberfläche des Modell-Editors erforderlich sind, inklusive Datentypen und Eigenschaften für jede Komponente.

## Speicherorte {#locations}

Modelle werden gespeichert und unter `/conf`, in dem sich der Ordner [Eigenschaft &quot;Inhaltsfragmentmodelle&quot;](/help/assets/content-fragments-models.md#enable-content-fragment-models) aktiviert. Diese Einstellung ist auch im **Konfigurationseigenschaften**, auf die über die **[Konfigurationsbrowser](/help/sites-administering/configurations.md)**.

1. Navigieren Sie über zum Browser. **Instrumente**, **Allgemein**, **Konfigurationsbrowser**
Beispiel: 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. Wählen Sie im Browser die entsprechende Konfiguration aus und **Eigenschaften** aus der Symbolleiste.

   Beispielsweise die Eigenschaften für `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

In der Modellkonsole werden alle Ordner mit dem **Inhaltsfragmentmodelle** -Eigenschaft angezeigt. Navigieren über **Instrumente**, **Assets**, **Inhaltsfragmentmodelle**; Beispiel: `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Ein Benutzer kann [Inhaltsfragmentmodell erstellen](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) mithilfe der **Modell erstellen** Assistent (mit **Erstellen** aus der Konsole).

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal upgraden. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)

## Struktur eines Modells {#structure-of-a-model}

Der Assistent erstellt einen Eintrag mit dieser Struktur:

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   Alle Modelle werden in Unterordnern dieses Ordners gespeichert.

* `jcr:content`

   Jedes Modell enthält eine `jcr:content` Knoten, der:

   * enthält Informationseigenschaften zum Modell, z. B. `jcr:title`, `lastModified`, `lastModifiedBy`
   * in der Regel `sling:ResourceType` von `dam/cfm/models/console/components/data/entity/default`,

      mit dem `sling:ResourceSuperType` von `dam/cfm/models/console/components/data/entity`

* `model`

   Die `model` Knoten enthält eine Eigenschaft `dataTypesConfig`, mit dem die im Modell-Editor verwendeten Datentypen bestimmt werden.

* `items`

   Unter dem `items` -Knoten werden alle dem Modell hinzugefügten Datentypen gespeichert (als Drag-and-Drop im Modell-Editor). Jedem Element wird ein zufälliger Knotenname zugewiesen, aber damit der Inhaltsfragmente-Editor mit diesem Modell funktioniert, muss jedes Element über einen `name` -Eigenschaft. Außerdem werden auf diesem Knoten alle Konfigurationseigenschaften für einen bestimmten Datentyp gespeichert, einschließlich der Standardeigenschaften, die zum Rendern der Komponenten erforderlich sind.

>[!CAUTION]
>
>Alle Datentypen wurden in einen Modell-Editor gezogen und abgelegt und als solche instanziiert. **must** haben die `name` Eigenschaftseingabe durch den Benutzer.
>
>Dies wird als **Eigenschaftsname &amp;ast;** im **Eigenschaften** Registerkarte des Modell-Editors.

## Struktur des Modell-Editors {#structure-of-the-model-editor}

Die **Inhaltsfragmentmodell-Editor** hat zwei Teile:

* Das Vorschau- oder Ansichtsbedienfeld auf der linken Seite, in dem Sie Elemente ablegen können. Dies:

   * Zeigt eine Vorschau der **Datentyp** wird instanziiert.
   * Ermöglicht die Sortierung im Modell-Editor.

* Die **Datentypen**/**Eigenschaften** Registerkarten im Bedienfeld auf der rechten Seite. Dies:

   * Zeigt eine Liste der Datentypen an, die gezogen und instanziiert werden können.
   * Für den vordefinierten Modell-Editor ist die Liste vorhanden unter:

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Alle gerenderten Datentypen verfügen über zwei Skript-Tags, die, wenn sie instanziiert werden, die Ansicht bilden (die auf der linken Seite gerenderte Komponente) und die **Eigenschaften** -Registerkarte, die die Eigenschaften definiert, die ein Benutzer für eine bestimmte Komponente definieren kann.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal upgraden. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Wenn ein Datentyp instanziiert wird, werden HTML-Eingaben für jede Eigenschaft erstellt, für die die Komponente in einem Inhaltsfragment gerendert werden muss. Dazu gehören beispielsweise:

* **Eigenschaftsname &amp;ast;** ( `name`) - dient als ID für Komponenten.

* **Rendern als** ( `metaType`) - Geben Sie die Komponente ein, als

* **Beschreibung** ( `fieldDescription`) - Beschreibung der Komponente im Inhaltsfragment

* und andere.

