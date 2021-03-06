---
title: Anpassen von Ansichten von Seiteneigenschaften
seo-title: Customizing Views of Page Properties
description: Jede Seite verfügt über eine Reihe von Eigenschaften, die Sie nach Bedarf bearbeiten können.
seo-description: Every page has a set of properties that you can edit as required
uuid: cbfca6e6-cb9e-43b1-8889-09a7cc9f8a51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6f8e08d1-831e-441a-ad1a-f5c8788f32d7
exl-id: 25dad368-8227-424d-960b-1664d8e20a21
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 75%

---

# Anpassen von Ansichten von Seiteneigenschaften{#customizing-views-of-page-properties}

Jede Seite hat eine Reihe von [Eigenschaften](/help/sites-authoring/editing-page-properties.md), die von Nutzern angezeigt und bearbeitet werden können. Einige sind erforderlich, wenn die Seite erstellt wird (Erstellungsansicht), andere können später angezeigt und bearbeitet werden (Bearbeitungsansicht). Diese Seiteneigenschaften werden über das Dialogfeld (`cq:dialog`) der entsprechenden Seitenkomponente definiert und bereitgestellt.

>[!CAUTION]
>
>In der klassischen Benutzeroberfläche kann die Ansicht der Seiteneigenschaften nicht angepasst werden.

Der Standardstatus für jede Seiteneigenschaft ist wie folgt:

* In der Erstellungsansicht ausgeblendet (z. B. im **Seitenerstellungsassistenten**)

* In der Bearbeitungsansicht verfügbar (z. B. unter **Eigenschaften anzeigen**)

Felder müssen einzeln konfiguriert werden, wenn eine Änderung erforderlich ist. Dies erfolgt mithilfe der entsprechenden Knoteneigenschaften:

* Seiteneigenschaft, die in der Erstellungsansicht verfügbar sein soll (z. B. im **Seitenerstellungsassistenten**):

   * Name: `cq:showOnCreate`
   * Typ: `Boolean`

* Seiteneigenschaft, die in der Bearbeitungsansicht verfügbar sein soll (z. B. **Ansicht**/**Bearbeiten**) **Eigenschaften** -Option):

   * Name: `cq:hideOnEdit`
   * Typ: `Boolean`

Sehen Sie als Beispiel die Einstellungen für Felder, die unter **Weitere Titel und Beschreibungen** auf der Registerkarte **Allgemein** der Foundation-Seitenkomponente gruppiert sind. Sie sind im **Seitenerstellungsassistenten** verfügbar, da `cq:showOnCreate` auf `true` gesetzt ist:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>Siehe [Tutorial zum Erweitern der Seiteneigenschaften](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) für eine Anleitung zum Anpassen der Seiteneigenschaften.

## Konfiguration von Seiteneigenschaften {#configuring-your-page-properties}

Sie können diese Felder auch konfigurieren, indem Sie das Dialogfeld Ihrer Seitenkomponente konfigurieren und die entsprechenden Knoteneigenschaften anwenden.

Beispiel: Der [**Seitenerstellungsassistent**](/help/sites-authoring/managing-pages.md#creating-a-new-page) zeigt standardmäßig die Felder an, die unter **Weitere Titel und Beschreibungen** gruppiert sind. Um diese auszublenden, nehmen Sie folgende Konfiguration vor:

1. Erstellen Sie Ihre Seitenkomponente unter `/apps`.
1. Erstellen Sie eine Überschreibung (mithilfe von *dialog diff* von [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md)) für die `basic` -Abschnitt Ihrer Seitenkomponente; Beispiel:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >Siehe als Referenz:
   >
   >
   ```
   >/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog
   >```
   >
   >Sie ***must*** ändert nichts in der `/libs` Pfad.
   >
   >da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
   >
   >Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
   >
   >1. Erstellen Sie das erforderliche Element (d. h. wie es in vorhanden ist) neu. `/libs`) unter `/apps`
   >1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.


1. Legen Sie die `path` Eigenschaft auf `basic` , um auf die Außerkraftsetzung der Registerkarte &quot;Standard&quot;zu verweisen (siehe auch den nächsten Schritt). Beispiel:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Erstellen Sie eine Überschreibung der `basic` - `moretitles` Abschnitt am entsprechenden Pfad; Beispiel:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Wenden Sie die entsprechende Knoteneigenschaft an:

   * **Name**: `cq:showOnCreate`
   * **Typ**: `Boolean`
   * **Wert**: `false`

   Der Abschnitt **Weitere Titel und Beschreibungen** wird nicht mehr im **Seitenerstellungsassistenten** angezeigt.

>[!NOTE]
>
>Wenn Sie Seiteneigenschaften für die Verwendung mit Live Copies konfigurieren, finden Sie weitere Details unter [Konfiguration von MSM-Sperren für Seiteneigenschaften](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui).

## Beispielkonfiguration von Seiteneigenschaften {#sample-configuration-of-page-properties}

Dieses Beispiel zeigt die „dialog diff“-Technik von [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md), einschließlich der Verwendung von [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties). Außerdem wird die Verwendung beider `cq:showOnCreate` und `cq:hideOnEdit`.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-authoring-extension-page-dialog auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
