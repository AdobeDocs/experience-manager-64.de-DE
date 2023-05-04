---
title: Konfigurieren von RTE für die Erstellung zugriffsbereiter Sites
seo-title: Configuring RTE for Producing Accessible Sites
description: Erfahren Sie, wie Sie den AEM Rich-Text-Editor konfigurieren, um barrierefreie Websites zu erstellen.
seo-description: Learn how to configure the AEM Rich Text Editor to produce accessible sites.
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
exl-id: 245e1c28-f702-4300-81cf-5139db9d95ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 42%

---

# Konfigurieren von RTE für die Erstellung zugriffsbereiter Sites {#configuring-rte-for-producing-accessible-sites}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM unterstützt beide:

* Standardmäßige Barrierefreiheitsfunktionen, einschließlich Alternativtext für Bilder
* sowie zusätzliche Funktionen, auf die beim Erstellen von Inhalten mit Komponenten zugegriffen werden kann, die den Rich-Text-Editor (RTE) verwenden

>[!NOTE]
>
>* [Kurzanleitung zu WCAG 2.0](/help/managing/qg-wcag.md)
>* [Erstellen barrierefreier Inhalte (in Übereinstimmung mit den WCAG 2.0-Richtlinien)](/help/sites-authoring/creating-accessible-content.md)


Inhaltsautoren können Funktionen des RTE verwenden, um beim Hinzufügen von Inhalten zu einer Seite barrierefreie Informationen bereitzustellen. Dazu kann das Hinzufügen von Strukturinformationen über Überschriften und Absatzelemente gehören.

Sie können [Konfigurieren und Anpassen dieser Funktionen durch Konfigurieren von RTE-Plug-ins](#configuring-the-plugin-features) für die Komponente. Beispiel: die `paraformat` -Plug-in ermöglicht es Ihnen, zusätzliche semantische Blockebenenelemente hinzuzufügen, einschließlich der Erweiterung der Anzahl der unterstützten Überschriftenebenen über die einfache `H1`, `H2` und `H3` standardmäßig bereitgestellt.

Der RTE ist in verschiedenen Komponenten sowohl der Touch-optimierten als auch der klassischen Benutzeroberfläche verfügbar. Die primäre Komponente für die Verwendung des RTE ist jedoch die **Text** -Komponente.

Die **Text** -Komponente in AEM ist sowohl für die Touch-optimierte als auch für die klassische Benutzeroberfläche verfügbar. Die folgenden Abbildungen zeigen den Rich-Text-Editor mit einer Reihe von aktivierten Plug-ins, darunter `paraformat`:

* Die **Text** Komponente in der Touch-optimierten Benutzeroberfläche:

   ![Textkomponente (RTE) im Vollbildmodus in der Touch-optimierten Benutzeroberfläche.](assets/chlimage_1-206.png)

* Die **Text** -Komponente in der klassischen Benutzeroberfläche:

   ![Bearbeitungsdialogfeld (RTE) der Textkomponente in der klassischen Benutzeroberfläche.](assets/chlimage_1-207.png)

>[!NOTE]
>
>Es gibt Unterschiede zwischen den in der klassischen und der Touch-optimierten Benutzeroberfläche verfügbaren RTE-Funktionen. Weitere Informationen finden Sie unter
>
>* [Plug-ins und ihre Funktionen](/help/sites-administering/rich-text-editor.md#aboutplugins)
>* [Plug-ins und ihre Funktionen - Touch-optimierte Benutzeroberfläche](/help/sites-administering/rich-text-editor.md#aboutplugins)
>


## Konfigurieren der Plugin-Funktionen {#configuring-the-plugin-features}

Vollständige Anweisungen zur Konfiguration des RTE finden Sie im Abschnitt [Konfigurieren des Rich-Text-Editors](/help/sites-administering/rich-text-editor.md) Seite. Dies deckt alles ab, einschließlich der wichtigen Schritte:

* [Plug-ins und ihre Funktionen](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [Konfigurationsspeicherorte](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [Aktivieren eines Plug-ins und Konfigurieren der features-Eigenschaft](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [Konfigurieren anderer RTE-Funktionen](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

Durch Konfiguration eines Plug-ins in der entsprechenden `rtePlugins` in der CRXDE Lite (siehe folgende Abbildung), können Sie entweder alle oder bestimmte Funktionen für dieses Plug-in aktivieren.

![Beispiel für ein rtePlugin in CRXDE Lite](assets/chlimage_1-208.png)

### Beispiel - Angeben von im RTE-Auswahlfeld verfügbaren Absatzformaten {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Neue semantische Blockformate können wie folgt zur Auswahl bereitgestellt werden:

1. Legen Sie den [Konfigurationsspeicherort](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations) abhängig von Ihrem RTE fest und navigieren Sie dorthin.
1. [Absatzauswahlfeld aktivieren](/help/sites-administering/rich-text-editor.md); von [Aktivieren des Plug-ins](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Geben Sie die Formate an, die im Absatzauswahlfeld verfügbar sein sollen](/help/sites-administering/rich-text-editor.md).
1. Die Absatzformate sind dann für den Autor der Inhalte aus den Auswahlfeldern im RTE verfügbar. Auf sie kann wie folgt zugegriffen werden:

   * Verwenden des Absatzes ([Pilcrow](https://en.wikipedia.org/wiki/Pilcrow)) in der Touch-optimierten Benutzeroberfläche:

   ![Symbol &quot;Absatz&quot;(Pilcrow).](do-not-localize/chlimage_1-7.png)

   * Verwenden der **Format** -Feld (Dropdown-Auswahl) in der klassischen Benutzeroberfläche.


Mit Strukturelementen, die im RTE über die Absatzformatoptionen verfügbar sind, bietet AEM eine gute Grundlage für die Entwicklung barrierefreier Inhalte. Inhaltsautoren können den RTE für die Formatierung der Schriftgröße, der Farben oder anderer verwandter Attribute verwenden und dadurch die Erstellung einer Inline-Formatierung verhindern. Stattdessen müssen sie die entsprechenden Strukturelemente wie Überschriften auswählen und globale Stile verwenden, die über die Option Stile ausgewählt wurden. Dadurch wird das Markup bereinigt, Benutzer, die mit ihren eigenen Stylesheets navigieren, erhalten bessere Optionen und korrekt strukturierte Inhalte.

## Verwenden der Funktion „Quellenbearbeitung“   {#use-of-the-source-edit-feature}

In einigen Fällen halten Inhaltsautoren es für erforderlich, den mithilfe des RTE erstellten HTML-Quell-Code zu untersuchen und anzupassen. Beispielsweise kann ein innerhalb des RTE erstellter Inhalt zusätzliches Markup erfordern, um die Einhaltung von WCAG 2.0 sicherzustellen. Dies kann mit dem [Quellbearbeitung](/help/sites-administering/rich-text-editor.md#aboutplugins) -Option des RTE. Sie können die Funktion [`sourceedit` im Plug-in `misctools` angeben](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Gehen Sie beim Verwenden der Funktion `sourceedit` sorgfältig vor. Tippfehler und/oder nicht unterstützte Funktionen können zusätzliche Probleme hervorrufen.

## Hinzufügen der Unterstützung für weitere HTML-Elemente und -Attribute {#adding-support-for-additional-html-elements-and-attributes}

Um die Barrierefreiheitsfunktionen von AEM weiter auszubauen, ist es möglich, die vorhandenen Komponenten basierend auf dem RTE (wie die Komponenten **Text** und **Tabelle**) um zusätzliche Elemente und Attribute zu erweitern.

Die folgende Vorgehensweise stellt dar, wie die Komponente **Tabelle** mit einem Element **Beschriftung** erweitert werden kann, das Informationen zu einer Datentabelle für Benutzer von Hilfstechnologie bereitstellt:

### Beispiel: Hinzufügen der Beschriftung zum Dialogfeld &quot;Tabelleneigenschaften&quot; {#example-adding-the-caption-to-the-table-properties-dialog}

Fügen Sie im Konstruktor von `TablePropertiesDialog` ein zusätzliches Texteingabefeld hinzu, dass für die Bearbeitung der Beschriftung verwendet wird. Beachten Sie, dass `itemId` auf `caption` festgelegt sein muss (d. h. den Namen des DOM-Attributs), damit sein Inhalt automatisch verarbeitet wird.

In **Verzeichnis** Sie müssen das Attribut explizit auf/aus dem DOM-Element setzen oder entfernen. Der Wert wird vom Dialogfeld im `config`-Objekt weitergegeben. Beachten Sie, dass DOM-Attribute mithilfe der entsprechenden `CQ.form.rte.Common`-Methoden (`com` ist kurz für `CQ.form.rte.Common`) festgelegt/entfernt werden sollten, um die üblichen Fallstricke bei Browser-Implementierungen zu vermeiden.

>[!NOTE]
>
>Dieses Verfahren eignet sich nur für die klassische Benutzeroberfläche.

### Schrittweise Anleitungen {#step-by-step-instructions}

1. Starten Sie die CRXDE Lite. Beispiel: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. Kopieren Sie:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   in:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >Sie müssen Zwischenordner erstellen, falls diese nicht bereits vorhanden sind.

1. Kopieren Sie:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   in:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js` möglich.

1. Öffnen Sie die folgende Datei zur Bearbeitung (durch Doppelklicken öffnen):

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. In der `constructor`-Methode, vor dem Lesen der Zeilen:

   ```
   var dialogRef = this;
   ```

   Fügen Sie den folgenden Code hinzu:

   ```
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Öffnen Sie die folgende Datei:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js` möglich.

1. Fügen Sie den folgenden Code am Ende der `transferConfigToTable`-Methode hinzu:

   ```
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. Speichern Sie Ihre Änderungen mithilfe von **Alle speichern**

>[!NOTE]
>
>Ein „Nur Text“-Feld ist die einzige zulässige Eingabeart für den Wert des „caption“-Elements. Jedes ExtJS-Widget, das den Wert der Beschriftung durch seine `getValue()` -Methode verwendet werden.
>
>Um Bearbeitungsfunktionen für weitere Elemente und Attribute hinzuzufügen, stellen Sie sicher, dass sowohl:
>
>* Die `itemId`-Eigenschaft zu jedem entsprechenden Feld auf den Namen des entsprechenden DOM-Attributs (`TablePropertiesDialog`) eingestellt ist.
>* Das Attribut explizit für das DOM-Element festgelegt und/oder entfernt wird (`Table`).

