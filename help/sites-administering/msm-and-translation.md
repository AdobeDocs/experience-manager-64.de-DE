---
title: Website-Administration
seo-title: Website Administration
description: Erfahren Sie, wie Sie mehrsprachige Websites in AEM verwalten.
seo-description: Learn how to manage multilingual websites in AEM.
uuid: a32d458b-a5ad-46ef-a68c-4717c63b4bdd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: fabaa3e8-1657-4ed4-abb2-990117bec39c
exl-id: e8f83d21-b55e-4415-a581-8df1b71a84b1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 55%

---

# Website-Administration{#website-administration}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die folgenden Administrations-Tools sind für die Verwaltung von Websites und Seiten verfügbar:

* Multi Site Manager (MSM) ermöglicht Ihnen die Verwendung derselben Website-Inhalte an mehreren Stellen und lässt gleichzeitig Varianten zu:

   * [Wiederverwenden von Inhalten: Multi Site Manager und Live Copy](/help/sites-administering/msm.md)

* Die Übersetzungsfunktion ermöglicht Ihnen die Automatisierung der Übersetzung von Seiteninhalten, Assets und benutzergenerierten Inhalten, um mehrsprachige Websites zu erstellen und zu pflegen:

   * [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md)

* Diese beiden Funktionen können kombiniert werden, um Websites zu unterstützen, die beide [Mehrsprachige und mehrsprachige Inhalte](#multinational-and-multilingual-sites).

## Internationale, mehrsprachige Websites {#multinational-and-multilingual-sites}

Sie können durch den kombinierten Einsatz von Multi Site Manager und Übersetzungs-Workflow auf effiziente Weise Inhalte für internationale, mehrsprachige Websites erstellen. Erstellen Sie eine Übergeordnete Site in einer Sprache für ein bestimmtes Land und verwenden Sie diese Inhalte dann als Grundlage für die anderen Sites, wobei Sie gegebenenfalls eine Übersetzung verwenden:

* [Übersetzen](/help/sites-administering/translation.md) Sie die primäre Website in verschiedene Sprachen.

* Verwenden Sie [Multi Site Manager](/help/sites-administering/msm.md) für Folgendes:

   * Verwenden Sie Inhalte von der Übergeordneten Site und den Übersetzungen erneut, um Seiten für andere Länder und Kulturen zu erstellen.
   * Stellen Sie sicher, dass Sie die Verwendung von Multi Site Manager auf Inhalte in einer Sprache beschränken, z. B. auf Englisch Übergeordnet -> Englisch Sprachzweige auf Länderseiten, Französisch Übergeordnet -> Französisch Sprachzweige auf Länderseiten.
   * Trennen Sie bei Bedarf die Elemente der Live Copies, um Lokalisierungsdetails hinzuzufügen.

Das folgende Diagramm veranschaulicht, wie sich die Hauptkonzepte überschneiden (es sind jedoch nicht alle beteiligten Ebenen/Elemente dargestellt):

![chlimage_1-71](assets/chlimage_1-71.png)

>[!NOTE]
>
>Bei diesem und vergleichbaren Szenarien verwaltet MSM nicht die verschiedenen Sprachversionen als solche.
>
>* [MSM](/help/sites-administering/msm.md) verwaltet die Bereitstellung übersetzter Inhalte von einem Blueprint (z. B. einem globalen Übergeordnete) zu den Live Copies (z. B. den lokalen Sites) innerhalb der Grenzen einer Sprache.
>* Die AEM-Integrationsfunktionen zur [Übersetzung](/help/sites-administering/translation.md) verwalten kombiniert mit Übersetzungs-Management-Services von Drittanbietern die Sprachen und die Übersetzung der Inhalte in diese verschiedenen Sprachen.
>
>Bei noch komplexeren Nutzungsszenarien kann MSM auch über Sprachstämme hinweg eingesetzt werden.

>[!NOTE]
>
>Bei allen Nutzungsszenarien wird empfohlen, die folgenden Best Practices zu lesen:
>
>* [Best Practices für MSM](/help/sites-administering/msm-best-practices.md); insbesondere:
   >
   >   * [Erstellen einer Website](/help/sites-administering/msm-best-practices.md#create-site)
   >   * [MSM und mehrsprachige Websites](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites)
>
>* [Best Practices für die Übersetzung](/help/sites-administering/tc-bp.md)

