---
title: Strukturierung von Multisite-Management für zielgerichtete Inhalte
seo-title: Strukturierung von Multisite-Management für zielgerichtete Inhalte
description: Im Diagramm ist der Aufbau der Multisite-Unterstützung für zielgerichtete Inhalte dargestellt.
seo-description: Im Diagramm ist der Aufbau der Multisite-Unterstützung für zielgerichtete Inhalte dargestellt.
uuid: 2d30cdf0-ab77-490d-aac0-db3a0d417a58
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 7dd851ab-3fa7-426e-89cb-08b67e9b5999
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Strukturierung von Multisite-Management für zielgerichtete Inhalte{#how-multisite-management-for-targeted-content-is-structured}

Im folgenden Diagramm ist der Aufbau der Multisite-Unterstützung für Targeting-Inhalte dargestellt.

Areas appear underneath **/content/campaigns/&lt;brand>** and by default each brand has a master area, which is created automatically. In jedem Gebiet ist ein eigener Satz Aktivitäten, Erlebnisse und Angebote enthalten.

![chlimage_1-268](assets/chlimage_1-268.png)

Seiten oder Sites können Gebieten zugeordnet werden, sodass sich Targeting-Inhalte nachschlagen lassen. Sollte kein Gebiet konfiguriert sein, bezieht sich AEM für diese Marke auf das Mastergebiet.

Im folgenden Diagramm finden Sie ein Beispiel dafür, wie die Logik im Falle der drei Seiten Site1, Site2 und Site3 funktioniert.

![chlimage_1-269](assets/chlimage_1-269.png)

* Site1 bezieht sich für Marke1 auf MeinGebiet1 und für Marke2 auf AnderesGebiet2, basierend auf der Gebietszuordnung.
* Site2 bezieht sich für Marke1 auf MeinGebiet1 und für Marke2 auf das Mastergebiet, da nur für Marke1 Gebiete zugewiesen wurden.
* Site3 bezieht sich für Marke1 und für Marke2 auf das Mastergebiet, weil für diese Site keine Gebietszuordnung vorgenommen wurde.

