---
title: Fallstricke beim Programmieren
seo-title: Code pitfalls
description: Allgemeine Fallstricke beim Programmieren, die Sie bei der Entwicklung für AEM vermeiden sollten
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 100%

---

# Fallstricke beim Programmieren{#code-pitfalls}

## Sling-Bindungen im Java-Code vermeiden {#avoid-sling-bindings-in-java-code}

Sling-Bindungen sind in 90 Prozent der Fälle keine gute Möglichkeit, auf einen Dienst zuzugreifen. Verwenden Sie stattdessen die Anmerkungen *@Reference* oder *@Inject*.

## Thread.interrupt im Java-Code vermeiden {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* ist riskant, da es Dateien (darunter auch Lucene-Dateien und persistente Cache-Dateien) schließen kann, wenn es zum falschen Zeitpunkt aufgerufen wird.

## Mischen von Java-Synchronisierung mit ReadWriteLocks vermeiden {#avoid-mixing-java-synchronization-with-readwritelocks}

Dies kann zu Überschneidungen führen, bei denen der Code irgendwann zum Stillstand kommt.
