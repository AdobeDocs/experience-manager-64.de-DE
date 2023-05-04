---
title: Fallstricke beim Programmieren
seo-title: Code pitfalls
description: Häufige Fallstricke beim Programmieren bei der Entwicklung für AEM vermeiden
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 13%

---

# Fallstricke beim Programmieren{#code-pitfalls}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Vermeiden von Sling-Bindungen in Java-Code {#avoid-sling-bindings-in-java-code}

Sling-Bindungen sind in 90 % der Fälle eine ungeeignete Methode, auf einen Dienst zuzugreifen. Stattdessen sollten Sie *@reference* oder *@Inject* Anmerkungen.

## Thread.interrupt im Java-Code vermeiden {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* ist gefährlich, da Dateien, einschließlich Lucene-Dateien und persistente Cache-Dateien, geschlossen werden können, wenn sie zur falschen Zeit aufgerufen werden.

## Vermeiden Sie das Mischen von Java-Synchronisation mit ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Dies kann zu einer Wettlaufsituation führen, in der der Code schließlich zum Stillstand kommt.
