---
title: Benennungskonventionen
seo-title: Naming Conventions
description: Knoten im Repository unterliegen Benennungskonventionen des Java Content Repository
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository
uuid: 0515c5c5-3e93-4710-983f-c08c146467fc
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 198098c0-432b-4a93-a94e-2552337435dd
exl-id: 741043c7-2ebb-455d-8163-a246b874a7b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 81%

---

# Benennungskonventionen{#naming-conventions}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Knoten im Repository unterliegen den Benennungskonventionen des [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). AEM erfordert jedoch weitere Konventionen für die Namen von Seitenknoten.

## Benennungskonventionen für Seiten {#naming-conventions-for-pages}

Diese Benennungskonventionen werden auf verschiedenen Ebenen implementiert:

* JcrUtil: die AEM-Implementierung der [JCR-Service-Programme](#jcr-utilities).
* PageManager: der [Seiten-Manager](#page-manager) stellt Methoden für Operationen auf Seitenebene bereit.
* Je nach verwendeter Benutzeroberfläche:

   * [Touch-optimierte Standard-Benutzeroberfläche](#standard-ui)
   * [Klassische Benutzeroberfläche](#classic-ui)

### JCR-Service-Programme {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) ist die AEM-Implementierung der JCR-Service-Programme. Bei der Namensvalidierung sind die Zeichenzuordnungen, die diese Implementierung steuert, und die folgenden Validierungen von besonderem Interesse:

* `isValidName`

   * Stellt sicher, dass der Name nicht leer ist und nur gültige Zeichen enthält.
   * Kann verwendet werden, um zu prüfen, ob ein vorgeschlagener Name gültig ist.

* `createValidName`

   * Erstellt eine gültige Beschriftung aus einer beliebigen Zeichenfolge.
   * Diese Funktion kann verwendet werden, um einen Namen aus einem Titel zu erstellen.

### Seiten-Manager {#page-manager}

[PageManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) stellt basierend auf [JCRUtil](#jcr-utilities) Methoden für Vorgänge auf Seitenebene bereit.

### Standard-Benutzeroberfläche {#standard-ui}

Die standardmäßige Touch-optimierte Benutzeroberfläche:

* Validiert den Namen entsprechend der Einschränkungen, die PageManager vorgibt, wenn entweder:

   * ein Seitentitel zum Konvertieren in den Knotennamen angegeben ist
   * ein expliziter Knotenname angegeben ist

### Klassische Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche enthält strengere Einschränkungen:

* Validiert den Namen, wenn entweder:

   * ein Seitentitel zum Konvertieren in den Knotennamen angegeben ist
   * ein expliziter Knotenname angegeben ist

* Gültige Zeichen (beim Erstellen innerhalb der klassischen Benutzeroberfläche sind nur diese Zeichen tatsächlich gültig, obwohl `PageManagerImpl` weitere Zeichen erlauben würde):

   * &quot;a&quot;bis &quot;z&quot;
   * &quot;A&quot;bis &quot;Z&quot;
   * &quot;0&quot;bis &quot;9&quot;
   * _ (Unterstrich)
   * `-` (Strich/Minus)
