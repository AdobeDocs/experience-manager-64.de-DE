---
title: JCR-Integration
seo-title: JCR Integration
description: Tipps, wann Sie auf JCR-Niveau integrieren müssen
seo-description: Tips for when you must integrate at the JCR level
uuid: 11518baf-521e-471d-ad4f-2baa76075cfa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: e6647a11-a36e-4808-bb61-29b2895c6b1d
exl-id: 3e9727a5-32f8-40ad-aa06-619f50d109b2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 87%

---

# JCR-Integration{#jcr-integration}

## Ziehen Sie die Sling-Ressourcen-API der JCR-API vor {#prefer-the-sling-resource-api-to-jcr-api}

Die Sling-API arbeitet auf einem höheren, abstrakteren Niveau als die JCR-API. Dadurch kann Ihr Code wiederverwendbar und unabhängig vom zugrunde liegenden Speicher sein. Dies erleichtert das Einbinden externer virtueller Daten über den ResourceProvider-Mechanismus bei Bedarf.

## Vermeiden Sie Abfragen, wo immer es möglich ist {#avoid-queries-wherever-possible}

Es ist immer schneller, das Repository zu durchsuchen, um Daten abzurufen, als eine Abfrage auszuführen. Es gibt Fälle, in denen Abfragen erforderlich sind, z. B. eine Endbenutzerabfrage oder die Suche nach strukturiertem Inhalt aus dem gesamten Repository, aber in allen anderen Fällen wird es bevorzugt, zu den erforderlichen Knoten zu navigieren. Abfragen sollten immer in der Renderlogik wie Navigationskomponenten, einer &quot;Liste der letzten Elemente&quot;, der Anzahl der Elemente usw. vermieden werden. In diesen Fällen ist es besser, durch die Hierarchie zu gehen oder das Ergebnis vorab zwischenzuspeichern, damit es direkt beim Rendern verwendet werden kann.

## Schränken Sie die JCR-Überwachung ein {#restrict-the-scope-of-jcr-observation}

Beim Lauschen auf Ereignisse im Repository ist es wichtig, den Umfang so weit wie möglich einzuschränken. Es ist beispielsweise viel besser, auf ein Ereignis zu warten unter `/etc/mycompany` als `/etc`. Lauschen Sie niemals auf Ereignisse am Repository-Stamm. Stellen Sie außerdem sicher, dass die Callback-Methoden so schnell wie möglich ausgeführt werden, wenn für sie nichts zu tun ist.

## Beseitigen Sie den JCR-Administratorzugriff {#eliminate-use-of-jcr-admin-access}

Ab AEM 6 ist die Anmeldung als Administrator veraltet, da eine Verwaltungssitzung von ResourceResolverFactory abgerufen wird. Stattdessen sollten Dienstkonten für die Back-Office-Vorgänge erstellt werden, die diese Art des Zugriffs erfordern, und mit der ResourceResolverFactory kann ein ResourceResolver für dieses Konto abgerufen werden.
