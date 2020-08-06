---
title: Admin Consoles
seo-title: Admin Consoles
description: Es wird beschrieben, wie Sie die in AEM verfügbaren Admin Consoles verwenden.
seo-description: Es wird beschrieben, wie Sie die in AEM verfügbaren Admin Consoles verwenden.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 72%

---


# Admin Consoles{#admin-consoles}

In der Standardeinstellung ist die Option zum Wechseln zur klassischen Benutzeroberfläche über die Admin Consoles nun deaktiviert. Aus diesem Grund werden die Pop-up-Symbole, die beim Bewegen des Mauszeigers auf bestimmte Konsolensymbole angezeigt wurden, um den Zugriff auf die klassische Benutzeroberfläche zu ermöglichen, nicht mehr eingeblendet.

![screen_shot_2018-03-23at11956](assets/screen_shot_2018-03-23at111956.png)

Every console that has a Classic UI version in `/libs/cq/core/content/nav` can be re-enabled individually so that the **Classic UI** option once again pops up over the console icon when it is moused over.

In diesem Beispiel aktivieren wir die klassische Benutzeroberfläche wieder für die Sites-Konsole.

1. Suchen Sie mithilfe von CRXDE Lite den Knoten, der der Admin-Konsole entspricht, für die Sie die klassische Benutzeroberfläche erneut aktivieren möchten. Sie finden ihn hier:

   `/libs/cq/core/content/nav`

   Beispiel

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Wählen Sie den entsprechenden Knoten der Konsole aus, für die Sie die klassische Benutzeroberfläche wieder aktivieren möchten. Im Beispiel aktivieren wir die klassische Benutzeroberfläche für die Sites-Konsole.

   `/libs/cq/core/content/nav/sites`

1. Create an overlay using the **Overlay Node** option; for example:

   * **Pfad**: `/apps/cq/core/content/nav/sites`
   * **Pfad für Überlagerung**: `/apps/`
   * **Übereinstimmungstypen abgleichen**: aktiv (Kontrollkästchen aktivieren)

1. Fügen Sie dem überlagerten Knoten die folgende boolesche Eigenschaft hinzu:

   `enableDesktopOnly = {Boolean}true`

1. Die Option **Klassische Benutzeroberfläche** ist in der Admin Console jetzt wieder als Popover-Option verfügbar.

   ![screen_shot_2018-03-23at11924](assets/screen_shot_2018-03-23at111924.png)

Wiederholen Sie diese Schritte für jede Konsole, für die Sie den Zugriff auf die klassische Benutzeroberfläche wieder aktivieren möchten.
