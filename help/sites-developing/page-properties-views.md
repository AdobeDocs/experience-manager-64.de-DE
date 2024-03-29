---
title: Anpassen der Ansichten von Seiteneigenschaften
seo-title: Customizing Views of Page Properties
description: Jede Seite verfügt über eine Reihe von Eigenschaften, die Sie nach Bedarf bearbeiten können
seo-description: Every page has a set of properties that you can edit as required
uuid: cbfca6e6-cb9e-43b1-8889-09a7cc9f8a51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6f8e08d1-831e-441a-ad1a-f5c8788f32d7
exl-id: 25dad368-8227-424d-960b-1664d8e20a21
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 69%

---

# Anpassen der Ansichten von Seiteneigenschaften{#customizing-views-of-page-properties}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Jede Seite verfügt über einen Satz von [properties](/help/sites-authoring/editing-page-properties.md) die von Benutzern angezeigt und bearbeitet werden können; Einige sind beim Erstellen der Seite erforderlich (Ansicht erstellen), andere können später angezeigt und bearbeitet (Ansicht bearbeiten) werden. Diese Seiteneigenschaften werden über das Dialogfeld (`cq:dialog`) der entsprechenden Seitenkomponente definiert und bereitgestellt.

>[!CAUTION]
>
>In der klassischen Benutzeroberfläche kann die Ansicht der Seiteneigenschaften nicht angepasst werden.

Der Standardstatus für jede Seiteneigenschaft ist wie folgt:

* In der Erstellungsansicht ausgeblendet (z. B. im **Seitenerstellungsassistenten**)

* In der Bearbeitungsansicht verfügbar (z. B. unter **Eigenschaften anzeigen**)

Felder müssen bei Bedarf spezifisch konfiguriert werden. Dies geschieht mithilfe der entsprechenden Knoteneigenschaften:

* Seiteneigenschaft, die in der Erstellungsansicht verfügbar sein soll (z. B. im **Seitenerstellungsassistenten**):

   * Name: `cq:showOnCreate`
   * Typ: `Boolean`

* Seiteneigenschaft, die in der Bearbeitungsansicht verfügbar sein soll (z. B. die Option **Anzeigen**/**Bearbeiten**) von **Eigenschaften**):

   * Name: `cq:hideOnEdit`
   * Typ: `Boolean`

Sehen Sie als Beispiel die Einstellungen für Felder, die unter **Weitere Titel und Beschreibungen** auf der Registerkarte **Allgemein** der Foundation-Seitenkomponente gruppiert sind. Sie sind im **Seitenerstellungsassistenten** verfügbar, da `cq:showOnCreate` auf `true` gesetzt ist:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>Eine Anleitung zum Anpassen der Seiteneigenschaften finden Sie im [Tutorial zum Erweitern der Seiteneigenschaften](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html?lang=de).

## Konfiguration von Seiteneigenschaften {#configuring-your-page-properties}

Sie können auch die verfügbaren Felder konfigurieren, indem Sie das Dialogfeld Ihrer Seitenkomponente konfigurieren und die entsprechenden Knoteneigenschaften anwenden.

Beispiel: Der [**Seitenerstellungsassistent**](/help/sites-authoring/managing-pages.md#creating-a-new-page) zeigt standardmäßig die Felder an, die unter **Weitere Titel und Beschreibungen** gruppiert sind. Um diese auszublenden, nehmen Sie folgende Konfiguration vor:

1. Erstellen Sie Ihre Seitenkomponente unter `/apps`.
1. Erstellen Sie eine Überschreibung (mit *dialog diff*, das von [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) bereitgestellt wird) für den Abschnitt `basic` der Seitenkomponente. Beispiel:

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
   >Sie dürfen jedoch ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
   >
   >da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
   >
   >Die empfohlene Methode für Konfigurations- und sonstige Änderungen sieht wie folgt aus:
   >
   >1. Erstellen Sie das erforderliche Element (d. h., wie unter `/libs`) unter `/apps` neu.
   >1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.


1. Legen Sie die Eigenschaft `path` auf `basic` fest, um auf die Überschreibung der Registerkarte „Standard“ zu verweisen (siehe auch den nächsten Schritt). Beispiel:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Erstellen Sie eine Überschreibung des Abschnitts `basic` - `moretitles` am entsprechenden Pfad; Beispiel:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Wenden Sie die entsprechende Knoteneigenschaft an:

   * **Name**: `cq:showOnCreate`
   * **Typ**: `Boolean`
   * **Wert**: `false`

   Die **Weitere Titel und Beschreibungen** wird nicht mehr im Abschnitt **Seite erstellen** Assistent.

>[!NOTE]
>
>Informationen zum Konfigurieren von Seiteneigenschaften für die Verwendung mit Live Copies finden Sie unter [Konfigurieren von MSM-Sperren für Seiteneigenschaften](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui) für weitere Details.

## Beispielkonfiguration von Seiteneigenschaften {#sample-configuration-of-page-properties}

Dieses Beispiel zeigt die „dialog diff“-Technik von [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md), einschließlich der Verwendung von [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties). Es zeigt auch die Verwendung von `cq:showOnCreate` und `cq:hideOnEdit`.

CODE FÜR GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-authoring-extension-page-dialog in GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
