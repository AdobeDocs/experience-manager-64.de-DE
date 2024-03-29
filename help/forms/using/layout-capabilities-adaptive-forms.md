---
title: Layout-Möglichkeiten für adaptive Formulare
seo-title: Layout capabilities of adaptive forms
description: Layout und Erscheinungsbild adaptiver Formulare auf verschiedenen Geräten werden durch die Layouteinstellungen gesteuert. Machen Sie sich mit den verschiedenen Layouts und ihrer Anwendung vertraut.
seo-description: Layout and appearances of adaptive forms on various devices are governed by the layout settings. Understand the various layouts and how to apply them.
uuid: 7df2d234-e2e3-432a-9720-e73296424302
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 10bf1d44-9660-44d9-b2c3-dd9a252efc3a
feature: Adaptive Forms
exl-id: 887e88c6-4c2b-4ef3-b268-8956fdb4535f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 57%

---

# Layout-Möglichkeiten für adaptive Formulare {#layout-capabilities-of-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit Adobe Experience Manager (AEM) können Sie benutzerfreundliche adaptive Formulare erstellen, die Endbenutzern dynamische Erlebnisse bieten. Das Formularlayout steuert, wie Elemente oder Komponenten in einem adaptiven Formular angezeigt werden.

## Vorausgesetzte Kenntnisse {#prerequisite-knowledge}

Bevor Sie die verschiedenen Layoutfunktionen adaptiver Formulare kennenlernen, lesen Sie die folgenden Artikel, um mehr über adaptive Formulare zu erfahren.

[Einführung in AEM Forms](/help/forms/using/introduction-aem-forms.md)

[Einführung in die Erstellung von Formularen](/help/forms/using/introduction-forms-authoring.md)

## Typen von Layouts {#types-of-layouts}

Ein adaptives Formular bietet Ihnen die folgenden Layouttypen:

**Bereichslayout** Steuert, wie in einem Bereich befindliche Elemente oder Komponenten auf einem Gerät angezeigt werden.

**Layout für Mobilgeräte** Steuert die Navigation eines Formulars auf einem mobilen Gerät. Wenn das Gerät eine Breite von mindestens 768 Pixel aufweist, wird das Layout als Layout für Mobilgeräte betrachtet und für Mobilgeräte optimiert.

**Symbolleisten-Layout** Steuert die Platzierung von Aktionsschaltflächen in der Symbolleiste bzw. in der Bereichssymbolleiste in einem Formular.

Alle diese Bedienfeldlayouts werden in den folgenden Verzeichnissen definiert:

`/libs/fd/af/layouts`.

>[!NOTE]
>
>Um das Layout eines adaptiven Formulars zu ändern, verwenden Sie den Bearbeitungsmodus in AEM.

![Speicherort von Layouts im CRX-Repository](assets/layouts_location_in_crx.png)

## Bereichslayout {#panel-layout}

Ein Formularautor kann jedem Bereich eines adaptiven Formulars ein Layout zuweisen, einschließlich des Stammbereichs.

Die Bereichslayouts stehen unter `/libs/fd/af/layouts/panel` zur Verfügung.

![Liste der Bedienfeldlayouts für das Stammbedienfeld eines adaptiven Formulars](assets/layouts.png)
**Abbildung:** *Liste der Bereichslayouts in adaptiven Formularen*

### Responsiv – alles auf einer Seite ohne Navigation {#responsive-everything-on-one-page-without-navigation-br}

Verwenden Sie dieses Bereichslayout, um ein responsives Layout zu erstellen, das sich ohne spezielle Navigation an die Bildschirmgröße Ihres Geräts anpasst.

Mithilfe dieses Layouts können Sie in das Bedienfeld nacheinander mehrere Komponenten für **[!UICONTROL Bedienfelder für adaptive Formulare]** einfügen.

![So sieht ein Formular mit einem responsiven Layout auf einem kleinen Bildschirm aus](assets/responsive_layout_seen_on_small_screen.png)

**Abbildung:** *Ein Formular mit einem responsiven Layout, wie auf einem kleinen Bildschirm dargestellt*

![Formular mit einem reaktionsfähigem Layout auf einem großen Bildschirm](assets/responsive_layout_seen_on_large_screen.png)

**Abbildung:** *Ein Formular, das ein responsives Layout verwendet, wie es auf einem großen Bildschirm angezeigt wird*

### Assistent - ein mehrstufiges Formular, das jeweils einen Schritt anzeigt {#wizard-a-multi-step-form-showing-one-step-at-a-time}

Verwenden Sie dieses Bereichslayout, um innerhalb eines Formulars eine geführte Navigation anzubieten. Beispielsweise können Sie dieses Layout verwenden, wenn Sie in einem Formular obligatorische Informationen erfassen und dabei die Benutzer Schritt für Schritt anleiten möchten.

Verwenden Sie die `Panel adaptive form`-Komponente, um in einem Bedienfeld eine schrittweise Navigation zur Verfügung zu stellen. Wenn Sie dieses Layout verwenden, gehen Benutzer erst dann zum nächsten Schritt über, wenn der aktuelle Schritt abgeschlossen ist.

```
window.guideBridge.validate([], this.panel.navigationContext.currentItem.somExpression)
```

![Ausdruck für das Abschließen von Schritten im Assistentenlayout für ein Mehrstufenformular](assets/layout-sidebar.png)

**Abbildung:** *Ausdruck zum Abschluss von Schritten im Assistentenlayout für ein mehrstufiges Formular*

![Ein Formular mit dem Assistentenlayout](assets/wizard-layout.png)

**Abbildung:** *Ein Formular mit dem Assistenten*

### Layout für Akkordeon-Design {#layout-for-accordion-design}

Mit diesem Layout können Sie die `Panel adaptive form`-Komponente in ein Bedienfeld mit Navigation im Akkordeonstil einfügen. Mit diesem Layout können Sie außerdem wiederholbare Bereiche erstellen. Wiederholbare Bereiche ermöglichen es Ihnen, Bereiche nach Bedarf hinzuzufügen oder zu entfernen. Sie können dabei festlegen, wie oft sich ein Bereich mindestens oder maximal wiederholen darf. Außerdem kann anhand der in den Bereichselementen angegebenen Informationen der Titel des Bereichs dynamisch festgelegt werden.

Ein Zusammenfassungsausdruck kann verwendet werden, um im Titel des minimierten Bereichs die vom Endbenutzer eingegebenen Werte anzuzeigen.

![Wiederholbare Bedienfelder mit Akkordeonlayout in adaptiven Formularen](assets/repeatable_panels_using_accordion_layout.png)

**Abbildung:** *Mit dem Akkordeon-Layout erstellte wiederholbare Bedienfelder*

### Layout mit Registerkarten – Registerkarten werden auf der linken Seite angezeigt {#tabbed-layout-tabs-appear-on-the-left}

Mithilfe dieses Layouts können Sie die `Panel adaptive form`-Komponente in ein Bedienfeld mit Registerkartennavigation einfügen. Die Registerkarten befinden sich auf der linken Seite der Bereichsinhalte.

![Im Layout mit Registerkarten werden die Registerkarten links angezeigt](assets/tabbed_layout_left.png)

**Abbildung:** *Registerkarten links von einem Bedienfeld*

### Layout mit Registerkarten – Registerkarten werden oben angezeigt {#tabbed-layout-tabs-appear-on-the-top}

Mithilfe dieses Layouts können Sie die `Panel adaptive form`-Komponente in ein Bedienfeld mit Registerkartennavigation einfügen. Die Registerkarten befinden sich oberhalb der Bereichsinhalte.

![Layout mit Registerkarten in adaptiven Formen mit Registerkarten am oberen Rand](assets/tabbed_layout_top.png)

**Abbildung:** *Registerkarten, die oben in einem Bedienfeld angezeigt werden*

## Layouts für Mobilgeräte {#mobile-layouts}

Layouts für Mobilgeräte ermöglichen eine benutzerfreundliche Navigation auf Mobilgeräten mit relativ kleineren Bildschirmen. Layouts für Mobilgeräte verwenden für die Formularnavigation entweder Registerkarten- oder Assistentenstile. Das Anwenden eines Layouts für Mobilgeräte bietet ein einzelnes Layout für das gesamte Formular.

Dieses Layout steuert die Navigation mithilfe einer Navigationsleiste und eines Navigationsmenüs. In der Navigationsleiste befinden sich die Symbole **&lt;** und **>**, um den **nächsten** und den **vorigen** Navigationsschritt im Formular anzuzeigen.

Die Layouts für Mobilgeräte sind unter `/libs/fd/af/layouts/mobile/` verfügbar. Die folgenden Layouts für Mobilgeräte stehen für adaptive Formulare standardmäßig zur Verfügung.

![Liste der Layouts für Mobilgeräte in adaptiven Formularen](assets/mobile-navigation.png)

**Abbildung:** *Liste der Layouts für Mobilgeräte in adaptiven Formularen*

Bei einem Layout für Mobilgeräte ist das Formularmenü (über das auf verschiedene Formularbereiche zugegriffen werden kann) per Klick auf das Symbol ![aem6forms_form_menu](assets/aem6forms_form_menu.png) verfügbar.

### Layout mit Bereichstiteln in der Formularkopfzeile {#layout-with-panel-titles-in-the-form-header}

Wie der Name schon sagt, werden bei diesem Layout neben dem Navigationsmenü und der Navigationsleiste Bedienfeldtitel angezeigt. Dieses Layout enthält auch die Symbole Weiter und Zurück zur Navigation.

![Layouts für Mobilgeräte mit Bereichstiteln in den Formularkopfzeilen](assets/mobile_layout_with.png)

**Abbildung:** *Layouts für Mobilgeräte mit Bedienfeldtiteln in den Formularkopfzeilen*

### Layout ohne Bereichstitel in der Formularkopfzeile {#layout-without-panel-titles-in-the-form-header}

Wie der Name schon sagt, werden bei diesem Layout nur das Navigationsmenü und die Navigationsleiste ohne Bedienfeldtitel angezeigt. Dieses Layout enthält auch die Symbole Weiter und Zurück zur Navigation.

![Layouts für Mobilgeräte ohne Bereichstitel in den Formularkopfzeilen](assets/mobile_layout_without.png)

**Abbildung:** *Layouts für Mobilgeräte ohne Bedienfeldtitel in den Formularkopfzeilen*

## Symbolleistenlayouts {#toolbar-layouts}

Mit einem Symbolleistenlayout werden Positionierung und Anzeige aller Aktionsschaltflächen gesteuert, die Sie Ihren adaptiven Formularen hinzufügen. Das Layout kann auf Formular- oder Bedienfeldebene hinzugefügt werden.

![Liste der Symbolleistenlayouts in adaptiven Formularen zur Steuerung des Schaltflächenlayouts](assets/toolbar-layouts.png)

**Abbildung:** *Liste der Symbolleistenlayouts in adaptiven Formularen*

Die Symbolleistenlayouts befinden sich unter `/libs/fd/af/layouts/toolbar`. Adaptive Formulare stehen in den folgenden Symbolleistenlayouts standardmäßig zur Verfügung.

### Standardlayout für Symbolleiste {#default-layout-for-toolbar}

Dieses Layout wird als Standardlayout ausgewählt, wenn Sie Aktionsschaltflächen in einem adaptiven Formular hinzufügen. Bei Auswahl dieses Layouts wird für Desktop- und Mobilgeräte dasselbe Layout angezeigt.

Außerdem können Sie mehrere Symbolleisten mit Aktionsschaltflächen hinzufügen, die mit diesem Layout konfiguriert sind. Eine Aktionsschaltfläche ist mit einem Formularsteuerelement verknüpft. Sie können die Symbolleisten so konfigurieren, dass sie sich vor oder nach einem Bedienfeld befinden.

![Standardansicht für Symbolleiste](assets/toolbar_layout_default.png)

**Abbildung:** *Standardansicht der Symbolleiste*

### Festes Layout für Mobilgeräte für Symbolleiste {#mobile-fixed-layout-for-toolbar}

Wählen Sie dieses Layout aus, um alternative Layouts für Desktop- und Mobilgeräte bereitzustellen.

Für das Desktop-Layout können Sie Aktionsschaltflächen mithilfe bestimmter Beschriftungen hinzufügen. Mit diesem Layout kann nur eine Symbolleiste konfiguriert werden. Wenn mehr als eine Symbolleiste mit diesem Layout konfiguriert ist, gibt es eine Überschneidung für Mobilgeräte und nur eine Symbolleiste ist sichtbar. Sie können beispielsweise eine Symbolleiste am unteren oder oberen Rand des Formulars oder, nach oder vor den Bereichen im Formular einfügen.

Für das Layout für Mobilgeräte können Sie mithilfe von Symbolen Aktionsschaltflächen hinzufügen.

![Festes Layout für Mobilgeräte für Symbolleiste](assets/toolbar_layout_mobile_fixed.png)

**Abbildung:** *Festes mobiles Layout für Symbolleiste*
