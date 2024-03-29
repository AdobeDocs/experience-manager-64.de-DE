---
title: Launches - Übersicht
seo-title: Launches Overview
description: Mit Launches können Sie effizient Inhalte für eine zukünftige Version entwickeln. So sind Sie in der Lage, Änderungen für eine spätere Veröffentlichung vorzunehmen – unter Beibehaltung der aktuellen Seiten.
seo-description: Launches enable you to efficiently develop content for a future release. They allow you to make changes ready for future publication, while maintaining your current pages
uuid: ff6a2898-7a77-4315-bb1f-efa9caa5f3b2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: a7ec190d-056e-4fc9-8f2d-f4164273674d
exl-id: a6dca5d7-21b5-4a7f-9e83-b0f5ea77bc88
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 51%

---

# Launches Übersicht{#launches}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit Launches können Sie effizient Inhalte für eine zukünftige Version entwickeln.

Ein Launch wird erstellt, damit Sie (unter Beibehaltung der aktuellen Seiten) Änderungen für eine spätere Veröffentlichung vornehmen können. Wenn Sie die Launch-Seiten bearbeitet und aktualisiert haben, leiten Sie diese wieder zurück in die Quelle und aktivieren dann die Quellseiten (auf der obersten Ebene). Durch die Weiterleitung wird der Launch-Inhalt wieder auf die Quellseiten kopiert und kann entweder manuell oder automatisch ausgeführt werden (abhängig von den Feldern, die beim Erstellen und Bearbeiten des Launches festgelegt wurden).

Beispiel: Die saisonalen Produktseiten in Ihrem Online-Shop werden einmal pro Quartal aktualisiert, damit die präsentierten Produkte der aktuellen Saison entsprechen. Zur Vorbereitung auf die nächste Quartals-Aktualisierung können Sie einen Launch der relevanten Web-Seiten erstellen. Im Laufe des Quartals werden die folgenden Änderungen in der Launch Copy zusammengefasst:

* Änderungen an den Quellseiten, die die Folge normaler Wartungsarbeiten sind. Diese Änderungen werden automatisch in den Launch-Seiten dupliziert.
* Änderungen, die direkt auf den Launch-Seiten in Vorbereitung auf das nächste Quartal vorgenommen werden.

Wenn ein neues Quartal beginnt, leiten Sie die Launch-Seiten weiter, damit Sie die Quellseiten veröffentlichen können, die den aktualisierten Inhalt enthalten. Sie können entweder alle Seiten weiterleiten oder nur die Seiten, die Sie geändert haben.

Launches können auch:

* Erstellt für mehrere Stammverzweigungen. Sie können zwar den Launch für die gesamte Site erstellen (und die Änderungen dort vornehmen), dies kann jedoch nicht praktikabel sein, da die gesamte Site kopiert werden muss. Wenn Hunderte oder sogar Tausende von Seiten beteiligt sind, wirken sich die Kopieraktion und später die für die Promotion-Aufgaben erforderlichen Vergleiche auf die Systemanforderungen und die Leistung aus.
* Verschachtelt (ein Launch innerhalb eines Launches), damit Sie einen Launch aus einem vorhandenen Launch erstellen können, damit Autoren bereits vorgenommene Änderungen nutzen können, anstatt dieselben Änderungen für jeden Launch mehrmals vornehmen zu müssen.

In diesem Abschnitt wird beschrieben, wie Sie (und falls erforderlich) [delete](/help/sites-authoring/launches-creating.md#deleting-a-launch)) Launch-Seiten über die Sites-Konsole oder [in der Konsole &quot;Launches&quot;](#the-launches-console):

* [Erstellen von Launches](/help/sites-authoring/launches-creating.md)
* [Bearbeiten von Launches](/help/sites-authoring/launches-editing.md)
* [Weiterleiten von Launches](/help/sites-authoring/launches-promoting.md)

## Der Ablauf eines Launches {#launches-the-order-of-events}

Mit Launches können Sie effizient den Inhalt für eine zukünftige Veröffentlichung einer oder mehrerer aktivierter Web-Seiten entwickeln.

Mit Launches können Sie:

* Erstellen Sie eine Kopie Ihrer Quellseiten:

   * Die Kopie ist Ihr Launch.
   * Die Quellseiten der höchsten Stufe werden als **Produktion** bezeichnet.

      * Die Quellseiten können aus mehreren (separaten) Zweigen stammen.
   >[!CAUTION]
   >
   >Mehrere Quellseiten für einen Launch sind in der klassischen Benutzeroberfläche nicht möglich.

   ![chlimage_1-233](assets/chlimage_1-233.png)

* Bearbeiten Sie die Launch-Konfiguration:

   * Hinzufügen oder Entfernen von Seiten und/oder Verzweigungen zum/vom Launch.
   * Sie können Launch-Eigenschaften bearbeiten, z. B. **Titel**, **Launch-Datum** und die Markierung **Produktionsbereit**.

* Sie können Inhalte entweder manuell oder automatisch weiterleiten und veröffentlichen:

   * Manuell:

      * Werben Sie Ihren Launch-Inhalt zurück in die **Target** (Quellseiten), wenn sie zur Veröffentlichung bereit ist.
      * Veröffentlichen Sie den Inhalt von den Quellseiten (nach der Promotion).
      * Fördern Sie entweder alle Seiten oder nur geänderte Seiten.
   * Automatisch (dies beinhaltet Folgendes):

      * Das Feld **Launch-Datum** (**Live**-**Datum)**: Dieses Feld kann beim Erstellen oder Bearbeiten eines Launches festgelegt werden.
      * Die **Produktionsbereit** Markierung: kann nur beim Bearbeiten eines Launches festgelegt werden.
      * Wenn das Flag **Produktionsbereit** gesetzt wurde, wird der Launch automatisch am angegebenen **Launch-Datum** (**Live**-**Datum**) an die Produktionsseiten weitergeleitet. Nach der Promotion werden die Produktionsseiten automatisch veröffentlicht.

         Wenn kein Datum ausgewählt wurde, hat die Markierung keine Auswirkungen.


* Paralleles Aktualisieren der Quell- und Launch-Seiten:

   * Änderungen an den Quellseiten werden automatisch in der Launch-Kopie implementiert (wenn sie mit Vererbung eingerichtet wurden, z. B. in Form einer Live Copy).
   * Änderungen an der Launch-Kopie können ohne Störung dieser automatischen Aktualisierungen oder der Quellseiten vorgenommen werden.

   ![chlimage_1-234](assets/chlimage_1-234.png)

* [Erstellen eines verschachtelten Launches](/help/sites-authoring/launches-creating.md#creating-a-nested-launch) - einen Launch innerhalb eines Launches:

   * Die Quelle ist ein vorhandener Launch.
   * Sie können [einen verschachtelten Launch bewerben](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch) für alle Zielgruppen; Hierbei kann es sich um einen übergeordneten Launch oder die Quellseiten der obersten Ebene (Produktion) handeln.

   ![chlimage_1-235](assets/chlimage_1-235.png)

   >[!CAUTION]
   >
   >Durch Löschen eines Launches werden der Launch selbst sowie alle nachfolgenden verschachtelten Launches entfernt.

>[!NOTE]
>
>Für das Erstellen und Bearbeiten von Launches sind Zugriffsrechte auf `/content/launches` erforderlich (wie bei der Standardgruppe `content-authors`).
>
>Wenden Sie sich an Ihren Systemadministrator, falls Probleme auftreten.

### Die Konsole „Launches“  {#the-launches-console}

Die Konsole „Launches“ bietet eine Zusammenfassung Ihrer Launches und ermöglicht es Ihnen, die aufgeführten Aktionen auszuführen. Auf die Konsole kann wie folgt zugegriffen werden:

* über die Konsole **Tools**: **Tools** > **Sites** > **Launches**.

* oder direkt mit [http://localhost:4502/libs/launches/content/launches.html](http://localhost:4502/libs/launches/content/launches.html)

## Launches in „Verweise“ (Sites-Konsole) {#launches-in-references-sites-console}

1. Im **Sites** zur Quelle der Launches navigieren.
1. Öffnen Sie die **Verweise** und wählen Sie die Quellseite aus.
1. Auswählen **Starts**, werden die vorhandenen Launches aufgelistet:

   ![chlimage_1-236](assets/chlimage_1-236.png)

1. Tippen/klicken Sie auf den entsprechenden Launch. Die Liste der möglichen Aktionen wird angezeigt:

   ![chlimage_1-237](assets/chlimage_1-237.png)
