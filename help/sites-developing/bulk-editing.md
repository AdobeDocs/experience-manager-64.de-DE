---
title: Konfigurieren Sie Ihre Seite für die Massenbearbeitung von Seiteneigenschaften
seo-title: Configuring your Page for Bulk Editing of Page Properties
description: Durch die Massenbearbeitung von Seiteneigenschaften können Sie die Eigenschaften mehrerer Seiten gleichzeitig bearbeiten
seo-description: Bulk editing of page properties allows you to edit the properties of multiple pages at once
uuid: 1ad403d2-4b93-4943-ae45-74bf20705b81
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: fe61ee4b-51b6-4a6f-91d8-1c02b29cc1db
exl-id: 0aefe8c0-662e-4177-a369-feab174fa510
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 87%

---

# Konfigurieren Sie Ihre Seite für die Massenbearbeitung von Seiteneigenschaften {#configuring-your-page-for-bulk-editing-of-page-properties}

Durch die [Massenbearbeitung von Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md#from-the-sites-console-multiple-pages) können Sie die Eigenschaften mehrerer Seiten gleichzeitig bearbeiten.

Aufgrund der Möglichkeit unterschiedlicher Werte sind die Seiteneigenschaften für die Massenbearbeitung nicht standardmäßig aktiviert. Sie müssen explizit zugelassen (aktiviert) werden. Wenn Sie die Seiteneigenschaften definieren, die für die Massenbearbeitung verfügbar sein sollen, müssen Sie bestimmte Implikationen berücksichtigen, wie zum Beispiel:

* Bestimmte Felder sind normalerweise eindeutig; zum Beispiel ein Seitentitel. Sie müssen entscheiden, ob es sinnvoll ist, diese Felder für die Massenbearbeitung zu aktivieren, wenn ein Wert angewendet wird.
* Bestimmte Felder können mehrere Werte haben - dies erfordert eine sinnvolle Darstellung beim Rendern.

   Zum Beispiel ein Kontrollkästchen, das „Bereit zur Veröffentlichung“ anzeigt. Diese kann mehrere Werte vor der Massenbearbeitung aufweisen (z. B. bereit, in Überprüfung, in Bearbeitung).

>[!CAUTION]
>
>Massenbearbeitung von Seiteneigenschaften ist:
>
>* Nicht verfügbar in der klassischen Benutzeroberfläche.
>* Nicht verfügbar für Seiten innerhalb einer Live Copy.
>* Nur verfügbar für Seiten mit desselben Ressourcentyp.

>


>[!NOTE]
>
>Massenbearbeitung ist auch für Assets verfügbar. Dieses Verfahren ist sehr ähnlich, weicht aber in einigen Punkten ab. Genauere Informationen dazu finden Sie unter [Bearbeiten von Eigenschaften für mehrere Assets. ](/help/assets/managing-multiple-assets.md) Sie können die Felder im Editor für Metadaten-Massenbearbeitung für Assets mit der [Schema Editor](/help/assets/metadata-schemas.md).

## Aktivieren eines Felds {#enabling-a-field}

>[!NOTE]
>
>Bestimmte Felder können mehrere Werte haben - dies erfordert eine sinnvolle Darstellung beim Rendern. Aus diesem Grund sollten Sie nur die folgenden Feldtypen aktivieren:
>
>* `/libs/granite/ui/components/foundation/form/textfield`
>* `/libs/granite/ui/components/foundation/form/textarea`
>* `/libs/granite/ui/components/foundation/form/tagspicker`
>* `/libs/granite/ui/components/foundation/form/datepicker`
>* `/libs/granite/ui/components/foundation/form/pathbrowser`
>* `/libs/granite/ui/components/foundation/form/checkbox`

>


Felder werden in der Seitenkomponente aktiviert (*nicht* in der Vorlage):

1. Mit CRXDE Lite (oder einer entsprechenden Methode) öffnen Sie Ihre Seitenkomponente.

   Beispiel: `/apps/core/wcm/components/page/v1/page`

   >[!NOTE]
   >
   >Für das Beispiel wird angenommen, dass die Hauptkomponenten auf die Instanz installiert wurden, das der Fall ist, wenn die Instanz mit We.Retail-Beispielinhalt ausgeführt wird. Weitere Informationen finden Sie in der [Dokumentation zu Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html)

1. Navigieren Sie zum gewünschten Feld im `cq:dialog` Definition.
1. Definieren Sie die folgende Eigenschaft auf dem Feldknoten:

   * **Name**: `allowBulkEdit`
   * **Typ**: `Boolean`
   * **Wert**: `true`

   Beispiel: für die [Grundlagenkomponente](/help/sites-authoring/default-components-foundation.md) der Standardseite:

   `/libs/foundation/components/page`

   würde die Eigenschaft definiert werden auf:

   `cq:dialog/content/items/tabs/items/basic/items/column/items/onofftime/items/ondate`

   >[!CAUTION]
   >
   >Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
   >
   >da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
   >
   >Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
   >
   >    1. Erstellen Sie das erforderliche Element (d. h. wie es in vorhanden ist) neu. `/libs`) unter `/apps`
   >    1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.


1. Wählen Sie **Alle speichern**, um ihre Aktualisierungen beizubehalten.
