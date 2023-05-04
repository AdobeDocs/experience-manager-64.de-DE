---
title: Admin Consoles
seo-title: Admin Consoles
description: Erfahren Sie, wie Sie die in AEM verfügbaren Admin Consolen verwenden.
seo-description: Lear how to use the Admin Consoles available in AEM.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
exl-id: f3c03562-aaeb-4d43-aee1-d92d661ee329
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 34%

---

# Admin Consoles{#admin-consoles}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Standardmäßig wurde die Möglichkeit deaktiviert, über die Admin Console zur klassischen Benutzeroberfläche zu wechseln. Daher werden die Pop-up-Symbole, die beim Bewegen des Mauszeigers über bestimmte Konsolensymbole angezeigt wurden und den Zugriff auf die klassische Benutzeroberfläche ermöglichten, nicht mehr angezeigt.

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

Jede Konsole, die unter `/libs/cq/core/content/nav` über eine klassische Benutzeroberfläche verfügt, kann einzeln wieder aktiviert werden. Die Option **Klassische Benutzeroberfläche** wird für das Konsolensymbol dann wieder angezeigt, wenn Sie den Mauszeiger darauf bewegen.

In diesem Beispiel aktivieren wir die klassische Benutzeroberfläche wieder für die Sites-Konsole.

1. Suchen Sie mithilfe von CRXDE Lite den Knoten, der der Admin Console entspricht, für die Sie die klassische Benutzeroberfläche erneut aktivieren möchten. Sie finden ihn hier:

   `/libs/cq/core/content/nav`

   Beispiel

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Wählen Sie den Knoten aus, der der Konsole entspricht, für die Sie die klassische Benutzeroberfläche erneut aktivieren möchten. In unserem Beispiel wird die klassische Benutzeroberfläche für die Sites-Konsole erneut aktiviert.

   `/libs/cq/core/content/nav/sites`

1. Erstellen Sie eine Überlagerung mit der Option **Überlagerungsknoten**. Beispiel:

   * **Pfad**: `/apps/cq/core/content/nav/sites`
   * **Pfad für Überlagerung**: `/apps/`
   * **Knotentypen abgleichen**: active (aktivieren Sie das Kontrollkästchen)

1. Fügen Sie dem überlagerten Knoten die folgende boolesche Eigenschaft hinzu:

   `enableDesktopOnly = {Boolean}true`

1. Die **Klassische Benutzeroberfläche** ist in der Admin Console wieder als Popover-Option verfügbar.

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

Wiederholen Sie diese Schritte für jede Konsole, für die Sie den Zugriff auf die klassische Benutzeroberfläche erneut aktivieren möchten.
