---
title: Betrachtungen beim Ausführen der Administration-Console
seo-title: Considerations when running AdministrationConsole
description: In diesem Dokument werden einige Punkte aufgeführt, die beim Ausführen von Administration Console zu beachten sind.
seo-description: This document lists a few points to consider when running Administration Console.
uuid: e260f187-4728-44f3-a5c1-7388ff3965c4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 525c4afc-e109-4546-b78c-1efee63edc43
exl-id: 991418fd-5ff8-491e-834e-2324e029e499
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 16%

---

# Überlegungen beim Ausführen von Administration Console {#considerations-when-running-administrationconsole}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Beachten Sie Folgendes beim Ausführen von Administration Console:

* Wenn Sie über die URL `https://*[hostname]*:*[port]*/adminui` auf die Administration-Console zugreifen, darf der angegebene Host-Name keine Unterstrichzeichen enthalten. Andernfalls funktionieren Links zu einigen Bereichen der Administration Console möglicherweise nicht ordnungsgemäß.
* Wenn Sie Administration Console in Windows Explorer unter einem japanischen Betriebssystem ausführen, können Sie auf folgende Probleme stoßen:

   * Wenn Sie auf einen Link klicken, kehren Sie zur Anmeldeseite zurück und nicht zum erwarteten Link.
   * Wenn Sie auf einen Link klicken, wird ein Berechtigungsfehler angezeigt.

   Es empfiehlt sich, Administration Console über einen anderen Browser wie Mozilla Firefox auszuführen, um sicherzustellen, dass keine Links fehlschlagen.

* Verwenden Sie bei Suchvorgängen in Administration Console keine umgekehrten Schrägstriche ().
