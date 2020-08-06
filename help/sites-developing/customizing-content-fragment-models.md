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
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 3%

---


# NICHT VERÖFFENTLICHEN, SONDERN KEIN DELETE ZUM Anpassen von Inhaltsfragmentmodellen{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

Der Editor des Inhaltsfragmentmodells ist ein Assistent, der auf `Formbuilder`Folgendem basiert:

`granite/ui/components/foundation/form/formbuilder`

Diese Komponente verfügt über die Werkzeuge, die zum Rendern der Drag &amp; Drop-Schnittstelle des Modelleditors erforderlich sind, inklusive der Datentypen und Eigenschaften für jede Komponente.

## Standorte {#locations}

Modelle werden unter `/conf`einem Ordner gespeichert und erstellt, in dem die Eigenschaft &quot; [Inhaltsfragmentmodelle&quot;aktiviert ist](/help/assets/content-fragments-models.md#enable-content-fragment-models) . Diese Einstellung wird auch in den **Konfigurationseigenschaften** angezeigt, auf die über den **Konfigurationsbrowser** zugegriffen werden kann.

1. Navigieren Sie zum Browser über **Tools**, **General**, **Configuration Browser** z. B. 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. Wählen Sie im Browser die entsprechende Konfiguration und dann **Eigenschaften** aus der Symbolleiste aus.

   Die Eigenschaften für `global`Folgendes: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

In der Modellkonsole werden alle Ordner mit der **Eigenschaft &quot;Inhaltsfragmentmodelle** &quot;angezeigt. Navigieren über **Tools**, **Assets**, **Inhaltsfragmentmodelle**; zum Beispiel `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Ein Benutzer kann ein Inhaltsfragmentmodell [mithilfe des Assistenten zum](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) Erstellen des Modells **** erstellen (mithilfe von **Erstellen** aus der Konsole).

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
>
>This is because the content of `/libs` is overwritten the next time you upgrade your instance (and may be overwritten when you apply either a hotfix or feature pack).

## Struktur eines Modells {#structure-of-a-model}

Der Assistent erstellt einen Eintrag mit der folgenden Struktur:

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   Alle Modelle werden unter Unterordnern dieses Ordners gespeichert.

* `jcr:content`

   Jedes Modell enthält eine `jcr:content` Node, die:

   * enthält Informationseigenschaften zum Modell wie `jcr:title`, `lastModified`oder `lastModifiedBy`
   * in der Regel den `sling:ResourceType` Wert `dam/cfm/models/console/components/data/entity/default`,

      mit `sling:ResourceSuperType` der `dam/cfm/models/console/components/data/entity`

* `model`

   Die `model` Node enthält eine Eigenschaft, `dataTypesConfig`mit der die Datentypen bestimmt werden, die im Modelleditor verwendet werden.

* `items`

   Unter der `items` Node werden alle dem Modell hinzugefügten Datentypen gespeichert (als Drag &amp; Drop im Modelleditor). Jedem Element wird ein zufälliger Knotenname zugewiesen. Damit jedoch der Inhaltsfragmenteditor mit diesem Modell funktioniert, muss jedes Element über eine `name` Eigenschaft verfügen. Außerdem werden auf diesem Knoten alle Konfigurationseigenschaften für einen bestimmten Datentyp gespeichert, einschließlich der zum Rendern der Komponenten erforderlichen Standardeigenschaften.

>[!CAUTION]
>
>Alle Datentypen, die in einen Modelleditor gezogen und abgelegt werden und daher instanziiert werden, **müssen** über die Eigenschaftseingabe des Benutzers verfügen `name` .
>
>Dies wird als **Eigenschaftsname&amp;ast;** auf der Registerkarte &quot; **Eigenschaften** &quot;des Modelleditors.

## Struktur des Modelleditors {#structure-of-the-model-editor}

Der **Content Fragment Model Editor** besteht aus zwei Teilen:

* Das Bedienfeld &quot;Vorschau&quot;oder &quot;Ansicht&quot;auf der linken Seite, in dem Sie Elemente ablegen können. Dies:

   * Zeigt eine Vorschau des instanziierten **Datentyps** an.
   * Ermöglicht die Bestellung im Modelleditor.

* Die Registerkarten **Datentypen**/**Eigenschaften** im Bereich auf der rechten Seite. Dies:

   * Zeigt eine Liste von Datentypen an, die gezogen und instanziiert werden können.
   * Für den vordefinierten Modelleditor ist die Liste vorhanden unter:

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Alle gerenderten Datentypen haben zwei Skript-Tags, die bei Instanziierung die Ansicht (die auf der linken Seite gerenderte Komponente) und die Registerkarte &quot; **Eigenschaften** &quot;bilden, auf der die Eigenschaften definiert werden, die ein Benutzer für eine bestimmte Komponente definieren kann.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
>
>This is because the content of `/libs` is overwritten the next time you upgrade your instance (and may be overwritten when you apply either a hotfix or feature pack).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Wenn ein Datentyp instanziiert wird, werden HTML-Eingaben für jede Eigenschaft erstellt, die die Komponente in einem Inhaltsfragment wiedergegeben werden muss. Dazu gehören beispielsweise:

* **Eigenschaftsname&amp;ast;** ( `name`) - dient als Identifikator für Komponenten

* **Rendern als** ( `metaType`): Geben Sie die Komponente als

* **Beschreibung** ( `fieldDescription`) - Beschreibung der Komponente im Inhaltsfragment

* und mehr.

