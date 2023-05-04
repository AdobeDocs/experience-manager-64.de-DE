---
title: Benennungskonventionen für das Testen von Assets
seo-title: Naming conventions for assets
description: Knoten im Repository unterliegen den Benennungskonventionen des Java Content Repository. Adobe Experience Manager schreibt jedoch weitere Konventionen für den Namen von Asset-Knoten vor.
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 50%

---

# Benennungskonventionen für das Testen von Assets{#naming-conventions-for-assets-testing}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Knoten im Repository unterliegen den Benennungskonventionen des [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Adobe Experience Manager schreibt aber weitere Konventionen für den Namen von Asset-Knoten vor.

## Klassische Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche enthält strengere Einschränkungen:

* Validiert den Asset-Namen, wenn entweder:

   * Ein Asset-Titel wird zur Konvertierung in den Knotennamen bereitgestellt
   * ein expliziter Knotenname angegeben ist

* Gültige Zeichen (nur diese Zeichen sind tatsächlich gültig, wenn ein Asset in der klassischen Benutzeroberfläche erstellt wird):

   * &quot;a&quot;bis &quot;z&quot;
   * &quot;A&quot;bis &quot;Z&quot;
   * &quot;0&quot;bis &quot;9&quot;
   * _ (Unterstrich)
   * `-` (Strich/Minus)
