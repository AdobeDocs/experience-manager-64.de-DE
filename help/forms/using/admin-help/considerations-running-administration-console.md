---
title: Betrachtungen beim Ausführen der Administration Console
seo-title: Betrachtungen beim Ausführen der Administration Console
description: In diesem Dokument werden einige Erwägungen zum Ausführen der Administration Console aufgeführt.
seo-description: In diesem Dokument werden einige Erwägungen zum Ausführen der Administration Console aufgeführt.
uuid: e260f187-4728-44f3-a5c1-7388ff3965c4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 525c4afc-e109-4546-b78c-1efee63edc43
exl-id: 991418fd-5ff8-491e-834e-2324e029e499
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 89%

---

# Erwägungen beim Ausführen von Administration Console {#considerations-when-running-administrationconsole}

Folgendes sollte beim Ausführen von Administration Console beachtet werden:

* Wenn Sie über die URL `https://*[hostname]*:*[port]*/adminui` auf Administration Console zugreifen, darf der angegebene Hostname keine Unterstrichzeichen enthalten. Andernfalls funktionieren Links zu einigen Bereichen von Administration Console eventuell nicht ordnungsgemäß.
* Wenn Sie Administration Console in Windows Explorer unter einem japanischen Betriebssystem ausführen, können Sie auf folgende Probleme stoßen:

   * Beim Klicken auf einen Link wechseln Sie zur Anmeldeseite zurück, nicht zum erwarteten Ziel des Links.
   * Beim Klicken auf einen Link wird ein Berechtigungsfehler angezeigt.

   Es wird empfohlen, Administration Console in einem anderen Browser auszuführen, z. B. Mozilla Firefox, um sicherzustellen, dass keine Links fehlerhaft funktionieren.

* Verwenden Sie bei Suchvorgängen in Administration Console keine umgekehrten Schrägstriche (\).
