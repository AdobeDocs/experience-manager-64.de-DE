---
title: Tagging von Aktivierungsressourcen
seo-title: Tagging Enablement Resources
description: Das Tagging von Aktivierungsressourcen ermöglicht das Filtern von Ressourcen und Lernpfaden beim Durchsuchen von Katalogen durch Mitglieder.
seo-description: Tagging of enablement resources allows for filtering of resources and learning paths as members browse catalogs
uuid: daf8a4f4-486b-498c-99e9-d1533a830e64
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: c012d639-c6e6-4f73-bbd8-78a4baa38c17
role: Admin
exl-id: 89ca201e-23ad-4038-8f3e-7c9cd04f52e2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 2%

---

# Tagging von Aktivierungsressourcen {#tagging-enablement-resources}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Das Tagging von Aktivierungsressourcen ermöglicht das Filtern von Ressourcen und Lernpfaden beim Durchsuchen von Mitgliedern. [Kataloge](functions.md#catalog-function).

Im Wesentlichen:

* [Tag-Namespace erstellen](../../help/sites-administering/tags.md#creating-a-namespace) für jeden Katalog

   * [Festlegen von Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions)

      * Nur für Community-Mitglieder (geschlossene Community)

         * Lesezugriff für [Mitgliedergruppe der Community-Site](users.md#publish-group-roles)
      * Für alle Besucher der Site, ob angemeldet oder anonym (offene Community)

         * Lesezugriff für `Everyone`Gruppe
   * [Veröffentlichen der Tags](../../help/sites-administering/tags.md#publishing-tags)



* [Definieren des Umfangs von Tags für eine Community-Site](sites-console.md#tagging)

   * [Konfigurieren von Katalogen, die in der Site-Struktur vorhanden sind](functions.md#catalog-function)

      * Kann Tags zur Kataloginstanz hinzufügen, um die Liste der Tags zu steuern, die in den UI-Filtern angezeigt werden
      * Kann hinzufügen [Vorfilter](catalog-developer-essentials.md#pre-filters), um die in einem Katalog enthaltenen Ressourcen zu beschränken

* [Veröffentlichen der Community-Site](sites-console.md#publishing-the-site)
* [Anwenden von Tags auf Aktivierungsressourcen](resources.md#create-a-resource) sodass sie kategorisiert werden können
* [Ressourcen zur Aktivierung veröffentlichen](resources.md#publish)

## Community-Site-Tags {#community-site-tags}

Wenn Sie eine Community-Site erstellen oder bearbeiten, wird die [Tagging-Einstellung](sites-console.md#tagging) legt den Umfang der Tags fest, die für Funktionen der Site verfügbar sind, indem Sie eine Untergruppe der vorhandenen Tag-Namespaces auswählen.

Auch wenn Tags jederzeit erstellt und der Community-Site hinzugefügt werden können, wird empfohlen, zuvor eine Taxonomie zu entwickeln, die dem Aufbau einer Datenbank ähnelt. Weitere Informationen finden Sie unter [Verwenden von Tags](../../help/sites-authoring/tags.md).

Wenn Sie später Tags zu einer vorhandenen Community-Site hinzufügen, müssen Sie die Bearbeitung speichern, bevor Sie das neue Tag zu einer Katalogfunktion in der Struktur der Site hinzufügen können.

Für eine Community-Site ist es nach der Veröffentlichung der Site und der Veröffentlichung der Tags erforderlich, den Mitgliedern der Community Lesezugriff zu ermöglichen. Siehe [Festlegen von Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions).

Folgendes wird in CRXDE angezeigt, wenn ein Administrator Leseberechtigungen auf `/etc/tags/ski-catalog` für die Gruppe `Community Enable Members`.

![chlimage_1-420](assets/chlimage_1-420.png)

## Namensräume für Katalog-Tags {#catalog-tag-namespaces}

Die Katalogfunktion verwendet Tags, um sich selbst zu definieren. Beim Konfigurieren der Katalogfunktion auf einer Community-Site werden die Tag-Namespaces, aus denen Sie auswählen können, durch den Umfang der Tag-Namespaces definiert, die für die Community-Site festgelegt sind.

Die Katalogfunktion enthält eine Tag-Einstellung, die die in der Filter-Benutzeroberfläche für den Katalog aufgelisteten Tags definiert. Die Einstellung &quot;Alle Namespaces&quot;bezieht sich auf den Umfang der für die Community-Site ausgewählten Tag-Namespaces.

![chlimage_1-421](assets/chlimage_1-421.png)

## Anwenden von Tags auf Aktivierungsressourcen {#applying-tags-to-enablement-resources}

Aktivierungsressourcen und Lernpfade werden im gesamten Katalog angezeigt, wenn `Show in Catalog` aktiviert ist. Das Hinzufügen von Tags zu Ressourcen und Lernpfaden ermöglicht das Vorab-Filtern in bestimmte Kataloge sowie das Filtern in der Katalogbenutzeroberfläche.

Die Beschränkung von Aktivierungsressourcen und Lernpfaden auf bestimmte Kataloge wird durch Erstellen von [Vorfilter](catalog-developer-essentials.md#pre-filters).

Die Katalogbenutzeroberfläche ermöglicht es Besuchern, einen Tag-Filter auf die Liste der Ressourcen und Lernpfade anzuwenden, die in diesem Katalog angezeigt werden.

Der Administrator, der die Tags zur Aktivierung von Ressourcen anwendet, muss sich der mit den Katalogen verknüpften Tag-Namespaces sowie der Taxonomie bewusst sein, um ein Untertag für eine präzisere Kategorisierung auszuwählen.

Wenn beispielsweise eine `ski-catalog` -Namespace erstellt und in einem Katalog mit dem Namen `Ski Catalog`kann es zwei untergeordnete Tags haben: `lesson-1` und `lesson-2`.

Daher ist jede Aktivierungsressource mit einem der folgenden Tags versehen:

* Ski-Katalog:
* ski-catalog:less-1
* Ski-Katalog:Lektion-2

wird angezeigt in `Ski Catalog` nachdem die Aktivierungsressource veröffentlicht wurde.

![chlimage_1-422](assets/chlimage_1-422.png)

## Anzeigen des Katalogs in der Veröffentlichungsinstanz {#viewing-catalog-on-publish}

Sobald alles in der Autorenumgebung eingerichtet und veröffentlicht wurde, kann die Erfahrung mit der Verwendung des Katalogs zur Suche nach Aktivierungsressourcen in der Veröffentlichungsumgebung auftreten.

Wenn in der Dropdown-Liste keine Tag-Namespaces angezeigt werden, stellen Sie sicher, dass die Berechtigungen in der Veröffentlichungsumgebung ordnungsgemäß festgelegt wurden.

Wenn Tag-Namespaces hinzugefügt wurden und fehlen, stellen Sie sicher, dass die Tags und die Site erneut veröffentlicht wurden.

Wenn nach der Auswahl eines Tags beim Anzeigen des Katalogs keine Aktivierungsressourcen angezeigt werden, stellen Sie sicher, dass aus den Namespace(en) des Katalogs ein Tag vorhanden ist, das auf die Aktivierungsressource angewendet wird.

![chlimage_1-423](assets/chlimage_1-423.png)
