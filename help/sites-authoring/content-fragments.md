---
title: Seitenbearbeitung mit Inhaltsfragmenten
seo-title: Page Authoring with Content Fragments
description: Inhaltsfragmente in AEM ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Verwenden von seitenunabhängigen Inhalten.
seo-description: AEM Content Fragments allow you to design, create, curate, and use page-independent content
uuid: 66ccdff8-1658-4374-8562-97f81f434488
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 076a3064-80c3-454b-93f9-6ae925c54328
exl-id: bbe4ae86-e9b8-4c3f-ada3-82470e371c4e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 98%

---

# Seitenbearbeitung mit Inhaltsfragmenten{#page-authoring-with-content-fragments}

>[!CAUTION]
>
>Einige Inhaltsfragmentfunktionen erfordern die Anwendung von [AEM 6.4 Service Pack 2 (6.4.2.0 oder höher)](/help/release-notes/sp-release-notes.md).

Content Fragments für Adobe Experience Manager (AEM) werden [als seitenunabhängige Assets erstellt und verwaltet](/help/assets/content-fragments.md).

Sie ermöglichen es Ihnen, kanalneutrale Inhalte zusammen mit (möglicherweise kanalspezifischen) Varianten zu erstellen. Sie können diese Fragmente und ihre Varianten bei der Erstellung Ihrer Inhaltsseiten verwenden.

In Verbindung mit dem aktualisierten JSON Exporter können strukturierte Inhaltsfragmente auch verwendet werden, um AEM-Inhalte über Content Services anderen Kanälen als AEM-Seiten bereitzustellen.

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-authoring/experience-fragments.md)** sind unterschiedliche Funktionen in AEM:
>
>* **Inhaltsfragmente** sind redaktionelle Inhalte, vor allem Text und zugehörige Bilder. Dabei handelt es sich um reinen Inhalt ohne Design und Layout.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.

>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.

>[!CAUTION]
>
>Lesen Sie diese Seite gemeinsam mit [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments.md) (und den zugehörigen Seiten), da dort grundlegende Termini und Konzepte sowie die Erstellung und Verwaltung von Fragmenten erklärt werden.

Inhaltsfragmente ermöglichen:

* **Marketing- und Kampagnenstrategie**

   * Überprüfen Sie Inhalte über zentral verwaltete Inhaltsfragmente.

* **Creative Pro**

   * Verfolgen Sie kreative Assets über Sammlungen, die mit Inhaltsfragmenten verbunden sind.

* **Copy Writer**

   * Schreiben Sie im AEM-Inhaltsfragmenteditor.
   * Kann Inhaltsvarianten erstellen.
   * Kann relevante Inhalte dem Inhaltsfragment zuweisen.
   * Kann Versionierung/Workflow verwenden.
   * Kann Inhaltsfragmente freigeben.
   * Kann Übersetzungen zentral verwalten.

* **Produzenten und Journey-Manager**

   * Wählen Sie bei der Erstellung in AEM aus vordefinierten Fragmenten und Varianten aus.
   * Kann darauf vertrauen, dass Fragment- und zugehörige Inhalte immer auf dem neuesten Stand sind, da Copy Writer und Kreative ihre Aktualisierungen in zentral verwalteten Fragmenten und Assets vornehmen.
   * Kann darauf vertrauen, dass zugehörige Medieninhalte auf Relevanz geprüft werden.
   * Kann Ad-hoc-Inhaltsvarianten direkt vornehmen und gleichzeitig sicherstellen, dass diese Varianten im Fragment weiter zentral verwaltet werden.

## Hinzufügen eines Inhaltsfragments zu Ihrer Seite {#adding-a-content-fragment-to-your-page}

1. Öffnen Sie Ihre Seite zum Bearbeiten.

1. Fügen Sie die **[!UICONTROL Inhaltsfragmentkomponente]** hinzu; entweder aus dem **[!UICONTROL Komponenten-Browser]** oder mit **[!UICONTROL Neue Komponente einfügen]**.

1. Wählen Sie eine der folgenden Möglichkeiten:

   * Öffnen Sie den **[!UICONTROL Assets]**-Browser und filtern Sie nach der Option **[!UICONTROL Inhaltsfragmente]** (die Standardeinstellung ist „Bilder“). Ziehen Sie dann das gewünschte Fragment in die Komponenteninstanz.
   * Wählen Sie die Inhaltsfragment-Komponente und dann **[!UICONTROL Konfigurieren]** in der Symbolleiste. Im daraufhin angezeigten Dialogfeld können Sie das Auswahldialogfeld zum Durchsuchen und Auswählen des gewünschten **[!UICONTROL Inhaltsfragments]** öffnen.

   >[!NOTE]
   >
   >Eine alternative Methode besteht darin, ein bestimmtes Inhaltsfragment direkt auf die Seite zu ziehen. Dabei wird automatisch die zugehörige Komponente (Inhaltsfragment) erstellt.

1. Anfangs wird der Inhalt aus den Elementen **[!UICONTROL Allgemein]** und **[!UICONTROL Primär]** (Variante) angezeigt. Sie können nach Bedarf aber [auch andere Elemente und/oder Varianten auswählen](#selecting-the-element-or-variation).

   ![cfm-6420-01](assets/cfm-6420-01.png)

   >[!NOTE]
   >
   >Weitere Informationen zur Bearbeitungsfunktion finden Sie unter:
   >
   >* [Responsives Layout](/help/sites-authoring/responsive-layout.md)
   >* [Bearbeiten des Seiteninhalts](/help/sites-authoring/editing-content.md)


## Auswählen des Elements oder der Variante {#selecting-the-element-or-variation}

Öffnen Sie das Dialogfeld **[!UICONTROL Konfiguration]** des Fragments, um das Fragment für die Verwendung auf der aktuellen Seite zu konfigurieren. Das Dialogfeld kann von der verwendeten Komponente abhängig sein.

Im entsprechenden Konfigurationsdialog können Sie die verfügbaren Parameter auswählen, einschließlich:

* **[!UICONTROL Inhaltsfragment]**

   Geben Sie das zu verwendende Fragment an.

* **[!UICONTROL Anzeigemodus]**:

   * **[!UICONTROL Einzelnes Textelement]**
   * **[!UICONTROL Mehrfachelement]**

* **[!UICONTROL Element]**

   * Die Voreinstellung **[!UICONTROL Haupt]** ist immer verfügbar.
   * Eine Auswahl ist verfügbar, wenn das Fragment mit einer entsprechenden Vorlage erstellt wurde. 

   >[!NOTE]
   >
   >Die verfügbaren Elemente hängen von der verwendeten Vorlage ab.

* **[!UICONTROL Variante]**

   * Die Standardversion **[!UICONTROL Primär]** ist immer verfügbar.
   * Eine Auswahl ist verfügbar, wenn Varianten für das Fragment erstellt wurden.

* **[!UICONTROL Absätze]**: Geben Sie den Bereich der einzubeziehenden Absätze an:

   * **[!UICONTROL Alle]**
   * **[!UICONTROL Bereich]**: Zum Beispiel `1`, `3-5`, `9-*`

      * **[!UICONTROL Überschriften als separate Absätze behandeln]**

* **[!UICONTROL Überschriften als separate Absätze behandeln]**

## Schnelle Verbindung zum Fragmenteditor     {#quick-connection-to-fragment-editor}

Sie können die Fragmentquelle zur Bearbeitung (das Asset) mithilfe des Symbols **[!UICONTROL Bearbeiten]** in der Komponenten-Symbolleiste öffnen. Auf diese Weise können Sie [das Inhaltsfragment bearbeiten und verwalten](/help/assets/content-fragments.md).

>[!CAUTION]
>
>Wie immer hat die Bearbeitung der Fragmentquelle Auswirkungen auf alle Seiten, auf die diese Inhaltsfragmente verweisen.

## Hinzufügen von Zwischeninhalten {#adding-in-between-content}

Wenn ein bestimmtes Inhaltsfragment der Seite hinzugefügt wird, wird der Platzhalter **[!UICONTROL Komponenten hierher ziehen]** zwischen allen HTML-Absätzen des Fragments (und oberhalb/unterhalb) eingefügt.

Damit können Sie zusätzlichen Inhalt [zwischen](/help/assets/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) den Fragmentinhalten (also Zwischeninhalte) einfügen (an jedem verfügbaren Punkt), ohne das Stammfragment ändern zu müssen.

Bei Zwischeninhalten können Sie:

* Komponenten aus dem [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) hinzufügen
* Assets aus dem [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser) hinzufügen
* [Zugehörige Inhalte](#using-associated-content) als Quelle für Zwischeninhalte verwenden.

>[!CAUTION]
>
>Bei Zwischeninhalten handelt es sich um Seiteninhalte. Sie werden nicht im Inhaltsfragment gespeichert.

![cfm-6420-02](assets/cfm-6420-02.png)

>[!NOTE]
>
>Sie können auch [visuelle Assets (Bilder) zum Fragment hinzufügen](/help/assets/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>Die in das Fragment eingefügten visuellen Assets werden mit dem vorangehenden Absatz im Fragment verbunden. Deshalb können Zwischeninhalte nicht zwischen einem visuellen Asset und dem vorangehenden Absatz platziert werden.

>[!CAUTION]
>
>Wenn Sie Zwischeninhalte zu einem Inhaltsfragment auf Ihrer Seite hinzugefügt haben, kann das Ändern der Struktur des zugrunde liegenden Inhaltsfragments (im Fragment-Editor) zu fehlerhaften/unerwarteten Ergebnissen führen.
>
>Wenn dies eintritt, wird der Zwischeninhalt unverändert beibehalten:
>
>* Zwischenkomponenten besitzen innerhalb der Abfolge der Komponenten im Fragmentfluss eine absolute Position. Diese Position ändert sich nicht, selbst wenn der Inhalt in den Absätzen des Fragments geändert wird.\
   >  Dies kann den Eindruck erwecken, als hätte sich die relative Position geändert, da Zwischenabsätze keinen kontextuellen Bezug zu den Absätzen (des Fragments) haben, neben denen sie sich befinden.
>* Wenn zwischen zwei Absatzstrukturen ein Konflikt besteht, wird der Zwischeninhalt nicht angezeigt (obwohl er intern noch vorhanden ist).

>


## Verwenden von zugehörigen Inhalten {#using-associated-content}

Wenn Sie [verknüpften Inhalt](/help/assets/content-fragments-assoc-content.md) für das [Inhaltsfragment](/help/assets/content-fragments.md) haben, stehen diese Elemente im Seitenbedienfeld zur Verfügung (nachdem Sie das Fragment auf der Inhaltsseite platziert haben). Verknüpfte Inhalte sind im Grunde eine besondere Inhaltsquelle für [dazwischen liegende Inhalte](#adding-in-between-content).

>[!NOTE]
>
>Es gibt verschiedene Methoden, um [visuelle Assets (z. B. Bilder)](/help/assets/content-fragments.md#fragments-with-visual-assets) einem Fragment und/oder einer Seite hinzuzufügen.

>[!NOTE]
>
>Wenn auf einer Seite mehrere Inhaltsfragmente vorhanden sind, werden in der Registerkarte **[!UICONTROL Zugehörige Inhalte]** die Assets angezeigt, die für alle Fragmente geeignet sind.

Nachdem Sie ein Fragment mit zugehörigen Inhalten zu Ihrer Seite hinzugefügt haben, wird eine neue Registerkarte (**[!UICONTROL Zugehörige Inhalte]**) im Seitenbereich geöffnet.

Von hier aus können Sie die Assets an die gewünschte Position ziehen (entweder zu einer vorhandenen Komponente oder an die gewünschte Position, an der die entsprechende Komponente erstellt wird):

![cfm-6420-03](assets/cfm-6420-03.png)

## In das Fragment eingefügte Assets {#assets-inserted-into-the-fragment}

Wenn [Assets (z. B. Bilder) in das Fragment eingefügt wurden](/help/assets/content-fragments-variations.md#inserting-assets-into-your-fragment), sind die Optionen zur Bearbeitung dieser Assets im Seiteneditor eingeschränkt.

Beispielsweise haben Sie zur Bearbeitung eines Bildes folgende Möglichkeiten:

* Zuschneiden, Drehen oder Spiegeln des Bildes
* Hinzufügen eines Titels oder eines Alternativtexts
* Definieren der Größe
* Konfigurieren des Layouts

Sonstige Änderungen wie Verschieben, Kopieren und Löschen müssen im Inhaltsfragmente-Editor vorgenommen werden.

## Veröffentlichung {#publishing}

Fragmente müssen veröffentlicht werden, damit sie auf Ihren veröffentlichten Web-Seiten verwendet werden können:

* Ein Fragment kann veröffentlicht werden, nachdem Sie [das Fragment in der Asset-Konsole erstellt haben](/help/assets/content-fragments-managing.md#publishing-and-referencing-a-fragment).
* Wenn ein *unveröffentlichtes Fragment* auf einer Seite verwendet wird, die veröffentlicht wird, kann das Fragment ebenfalls zu diesem Zeitpunkt veröffentlicht werden.
