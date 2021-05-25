---
title: NICHT VERÖFFENTLICHEN, ABER KEIN DELETE ZUM Anpassen von Inhaltsfragmentmodellen
seo-title: Anpassen von Inhaltsfragmentmodellen
description: Inhaltsfragmentmodelle können angepasst und erweitert werden.
seo-description: Inhaltsfragmentmodelle können angepasst und erweitert werden.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 3%

---


# NICHT VERÖFFENTLICHEN, ABER KEIN DELETE ZUM Anpassen von Inhaltsfragmentmodellen{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

Der Inhaltsfragmentmodelleditor ist ein Assistent, der auf `Formbuilder` basiert und von folgenden Elementen übernommen wird:

`granite/ui/components/foundation/form/formbuilder`

Diese Komponente verfügt über die Tools, die zum Rendern der Drag-and-Drop-Oberfläche des Modell-Editors erforderlich sind, inklusive Datentypen und Eigenschaften für jede Komponente.

## Standorte {#locations}

Modelle werden gespeichert und unter `/conf` in einem Ordner erstellt, in dem die [Eigenschaft für Inhaltsfragmentmodelle](/help/assets/content-fragments-models.md#enable-content-fragment-models) aktiviert ist. Diese Einstellung ist auch im **Konfigurationseigenschaften** sichtbar, auf den Sie über den **[Konfigurationsbrowser](/help/sites-administering/configurations.md)** zugreifen können.

1. Navigieren Sie zum Browser über **Tools**, **Allgemein**, **Konfigurations-Browser**.
Beispiel: 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. Wählen Sie im Browser die entsprechende Konfiguration und dann **Eigenschaften** in der Symbolleiste aus.

   Beispielsweise die Eigenschaften für `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

In der Modellkonsole werden alle Ordner mit der Eigenschaft **Inhaltsfragmentmodelle** angezeigt. Navigieren Sie über **Tools**, **Assets**, **Inhaltsfragmentmodelle**. z. B. `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Ein Benutzer kann [ein Inhaltsfragmentmodell](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) mithilfe des Assistenten **Modell erstellen** erstellen (mithilfe von **Erstellen** aus der Konsole).

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
>
>Dies liegt daran, dass der Inhalt von `/libs` beim nächsten Upgrade Ihrer Instanz überschrieben wird (und möglicherweise überschrieben wird, wenn Sie einen Hotfix oder ein Feature Pack anwenden).

## Struktur eines Modells {#structure-of-a-model}

Der Assistent erstellt einen Eintrag mit dieser Struktur:

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   Alle Modelle werden in Unterordnern dieses Ordners gespeichert.

* `jcr:content`

   Jedes Modell enthält einen `jcr:content` -Knoten, der Folgendes ermöglicht:

   * enthält Informationseigenschaften zum Modell wie `jcr:title`, `lastModified`, `lastModifiedBy`
   * hat normalerweise den `sling:ResourceType` von `dam/cfm/models/console/components/data/entity/default`,

      mit dem `sling:ResourceSuperType` von `dam/cfm/models/console/components/data/entity`

* `model`

   Der Knoten `model` enthält eine Eigenschaft `dataTypesConfig`, mit der die im Modelleditor verwendeten Datentypen bestimmt werden.

* `items`

   Unter dem Knoten `items` werden alle dem Modell hinzugefügten Datentypen gespeichert (als Drag-and-Drop im Modelleditor). Jedem Element wird ein zufälliger Knotenname zugewiesen, aber damit der Inhaltsfragmente-Editor mit diesem Modell funktioniert, muss jedes Element über eine `name` -Eigenschaft verfügen. Außerdem werden auf diesem Knoten alle Konfigurationseigenschaften für einen bestimmten Datentyp gespeichert, einschließlich der Standardeigenschaften, die zum Rendern der Komponenten erforderlich sind.

>[!CAUTION]
>
>Alle Datentypen, die in einen Modell-Editor gezogen und abgelegt wurden und daher instanziiert sind, muss **** vom Benutzer die Eigenschaft `name` haben.
>
>Dies wird als **Eigenschaftsname &amp;ast;** auf der Registerkarte **Eigenschaften** des Modell-Editors angezeigt.

## Struktur des Modell-Editors {#structure-of-the-model-editor}

Der **Inhaltsfragmentmodell-Editor** besteht aus zwei Teilen:

* Das Vorschau- oder Ansichtsbedienfeld auf der linken Seite, in dem Sie Elemente ablegen können. Dies:

   * Zeigt eine Vorschau des instanziierten **Datentyps** an.
   * Ermöglicht die Sortierung im Modell-Editor.

* Die Registerkarten **Datentypen**/**Eigenschaften** im Bereich auf der rechten Seite. Dies:

   * Zeigt eine Liste der Datentypen an, die gezogen und instanziiert werden können.
   * Für den vordefinierten Modell-Editor ist die Liste vorhanden unter:

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Alle gerenderten Datentypen haben zwei Skript-Tags, die bei der Instanziierung die Ansicht bilden (die auf der linken Seite gerenderte Komponente) und die Registerkarte **Eigenschaften** , die die Eigenschaften definiert, die ein Benutzer für eine bestimmte Komponente definieren kann.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
>
>Dies liegt daran, dass der Inhalt von `/libs` beim nächsten Upgrade Ihrer Instanz überschrieben wird (und möglicherweise überschrieben wird, wenn Sie einen Hotfix oder ein Feature Pack anwenden).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Wenn ein Datentyp instanziiert wird, werden HTML-Eingaben für jede Eigenschaft erstellt, für die die Komponente in einem Inhaltsfragment gerendert werden muss. Dazu gehören beispielsweise:

* **Eigenschaftsname &amp;ast;**  (  `name`) - dient als Identifikator für Komponenten

* **Render As** (  `metaType`) - Geben Sie die Komponente ein, als

* **Beschreibung** (  `fieldDescription`) - Beschreibung der Komponente im Inhaltsfragment

* und mehr.

