---
title: Bearbeiten von Launches
seo-title: Bearbeiten von Launches
description: 'Wenn ein Launch für eine Seite (oder eine Reihe von Seiten) erstellt wurde, können Sie den Inhalt in der Launch Copy der Seiten bearbeiten. '
seo-description: 'Wenn ein Launch für eine Seite (oder eine Reihe von Seiten) erstellt wurde, können Sie den Inhalt in der Launch Copy der Seiten bearbeiten. '
uuid: 851bcbbe-1dff-457f-a3bc-468ace9b4ac4
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: a28539fc-c1dd-43bf-a47b-5f158c5611a7
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 100%

---


# Bearbeiten von Launches{#editing-launches}

## Bearbeiten von Launch-Seiten {#editing-launch-pages}

Wenn ein Launch für eine Seite (oder eine Reihe von Seiten) erstellt wurde, können Sie den Inhalt in der Launch Copy der Seiten bearbeiten.

1. Rufen Sie [Launches aus Verweisen (Konsole „Sites“)](/help/sites-authoring/launches.md#launches-in-references-sites-console) auf, um die verfügbaren Aktionen anzuzeigen.
1. Wählen Sie **Gehe zu Seite** aus, um die Seite zur Bearbeitung zu öffnen.

### Bearbeiten von Launch-Seiten auf der Basis einer Live Copy   {#editing-launch-pages-subject-to-a-live-copy}

Wenn Ihr Launch auf einer [Live Copy](/help/sites-administering/msm.md) basiert, sehen Sie Folgendes:

* Schlosssymbole (kleine Vorhängeschlösser), wenn Sie eine Komponente bearbeiten (Inhalt und/oder Eigenschaften)
* die Registerkarte **Live Copy** in den **Seiteneigenschaften** 

Eine Livecopy wird verwendet, um Inhalte *von* der Quellverzweigung *mit* Ihrer Launch-Verzweigung zu synchronisieren (um Ihren Launch mit den Änderungen an der Quelle zu aktualisieren).

Sie können Änderungen auf dieselbe Weise vornehmen wie bei einer Standard-Live-Copy, z. B.:

* Durch Klicken auf ein geschlossenes Schloss wird die Synchronisierung unterbrochen und Sie haben die Möglichkeit, neue Aktualisierungen am Inhalt Ihres Launches vorzunehmen. Nach dem Entsperren (offenes Vorhängeschloss) werden Ihre Änderungen nicht von Änderungen überschrieben, die am selben Ort innerhalb der Startverzweigung vorgenommen werden.
* Sie können die Vererbung für eine bestimmte Seite **aussetzen** (und **fortsetzen**).

Siehe [Ändern des Live-Copy-Inhalts](/help/sites-administering/msm-livecopy.md#changing-live-copy-content).

## Vergleichen einer Launch-Seite mit ihrer Quellseite {#comparing-a-launch-page-to-its-source-page}

Um die vorgenommenen Änderungen zu verfolgen, können Sie den Launch in **Referenzen** anzeigen und die Launch- mit der Quellseite vergleichen:

1. Navigieren Sie in der **Sites-Konsole** [zur Quellseite Ihres Launches und wählen Sie sie aus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie das Fenster **[Verweise](/help/sites-authoring/basic-handling.md#references)**und wählen Sie **Launches**aus.
1. Wählen Sie dann Ihren spezifischen Launch und **Mit Quelle vergleichen** aus:

   ![chlimage_1-96](assets/chlimage_1-96.png)

1. Die beiden Seiten (Launch und Quelle) werden nebeneinander geöffnet.

   Weitere Informationen zur Verwendung dieser Funktion finden Sie unter [Seitenvergleich](/help/sites-authoring/page-diff.md).

## Ändern der verwendeten Quellseiten {#changing-the-source-pages-used}

Sie können jederzeit Seiten zum Bereich der Quellseiten für einen Launch hinzufügen oder daraus entfernen: 

1. Sie können auf den Launch wie folgt zugreifen und ihn auswählen:

   * die [Launch-Konsole](/help/sites-authoring/launches.md#the-launches-console):

      * Wählen Sie **Bearbeiten** aus.
   * [Verweise (Sites-Konsole)](/help/sites-authoring/launches.md#launches-in-references-sites-console) zum Anzeigen verfügbarer Aktionen:

      * Wählen Sie **Launch bearbeiten** aus.

   Die Quellseiten werden angezeigt.

1. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie dann mit **Speichern**.

   >[!NOTE]
   >
   >Damit Seiten zu einem Launch hinzugefügt werden können, müssen sich diese unter einem gemeinsamen Sprachstamm befinden, d. h. innerhalb einer einzelnen Website.

## Bearbeiten einer Launch-Konfiguration   {#editing-a-launch-configuration}

Sie können die Eigenschaften für einen Launch jederzeit bearbeiten:

1. Sie können auf den Launch wie folgt zugreifen und ihn auswählen:

   * die [Launch-Konsole](/help/sites-authoring/launches.md#the-launches-console):

      * Wählen Sie **Eigenschaften** aus.
   * [Verweise (Sites-Konsole)](/help/sites-authoring/launches.md#launches-in-references-sites-console) zum Anzeigen verfügbarer Aktionen:

      * Wählen Sie **Eigenschaften bearbeiten** aus.

   Die Details werden angezeigt.

1. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie dann mit **Speichern**.

   Unter [Launches – Reihenfolge der Ereignisse](/help/sites-authoring/launches.md#launches-the-order-of-events) finden Sie Informationen zum Zweck und zur Interaktion der Felder **Launch-Datum** und **Bereit für Produktion**.

## Ermitteln des Launch-Status einer Seite   {#discovering-the-launch-status-of-a-page}

Der Status wird angezeigt, wenn Sie einen bestimmten Launch auf der Registerkarte „Verweise“ auswählen (siehe [Launches in Verweisen (Sites-Konsole))](/help/sites-authoring/launches.md#launches-in-references-sites-console).

![chlimage_1-97](assets/chlimage_1-97.png)

