---
title: Upgrade auf AEM 6.4 Communities
seo-title: Upgrade auf AEM 6.4 Communities
description: Upgrade von einer früheren Version auf AEM 6.4 Communities
seo-description: Upgrade von einer früheren Version auf AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 5%

---


# Upgrade auf AEM 6.4 Communities {#upgrading-to-aem-communities}

Abhängig von der Topologie und den Funktionen der einzelnen Sites können die folgenden Aktionen erforderlich sein, wenn Sie auf AEM Communities 6.4 aktualisieren oder das neueste Feature Pack installieren.

Dieser Abschnitt ist spezifisch für Communities und ergänzt die Informationen unter [Upgrade auf AEM 6.4](../../help/sites-deploying/upgrade.md) (Plattform).

## Upgrade von AEM 6.1 oder höher {#upgrading-from-aem-or-later}

### Reindex Solr {#reindex-solr}

Wenn Sie ein neues Communities Feature Pack in einer mit MSRP konfigurierten Bereitstellung installieren, müssen Sie Folgendes tun:

1. Installieren Sie das [neueste Feature Pack](deploy-communities.md#latestfeaturepack)
2. Installieren Sie die [neuesten Solr-Konfigurationsdateien](msrp.md#upgrading)
3. Reindex MSRP

   siehe Abschnitt [MSRP Reindex Tool](msrp.md#msrp-reindex-tool)

### Enablement 2.0 {#enablement}

Ab AEM 6.3 werden in den Aktivierungsfunktionen keine Informationen mehr zum Berichte in MySQL gespeichert. MySQL wird nur noch für die Nachverfolgung von SCORM-Inhalten benötigt.

Bitte wenden Sie sich an die [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html) , um Hilfe bei der Migration von Inhalten aus Version 1.0 zu erhalten.

## Upgrade von AEM 6.0 {#upgrading-from-aem}

Wenn bereits vorhandene UGC beibehalten werden müssen, hängt die Vorgehensweise davon ab, ob die Bereitstellung UGC [lokal](#on-premise-storage) oder in der [Adobe Cloud](#adobe-cloud-storage)gespeichert hat.

### Adobe Cloud-Datenspeicherung {#adobe-cloud-storage}

Wenn die aktualisierte Site für die Verwendung der Adobe Cloud-Datenspeicherung konfiguriert wurde, wird sie möglicherweise (falsch) so angezeigt, als wäre der gesamte UGC verloren gegangen, da die SRP-Methoden nicht in der Lage sind, die bereits vorhandene UGC am alten Speicherort zu finden.

So gibt es die Möglichkeit, ASRP anzuweisen, auf UGC `AEM 6.0 compatability-mode` zuzugreifen.

Für alle AEM 6.3 Autoren- und Veröffentlichungsinstanzen

1. Anmelden mit Administratorberechtigungen
2. Konfigurieren von [ASRP](asrp.md)
3. Führen Sie die folgenden Schritte aus, um das bereits vorhandene UGC sichtbar zu machen:
i. Navigieren Sie beispielsweise zur Webkonsole
   [https://&lt;Host>:&lt;Anschluss>/system/console/configMgr](http://localhost:4502/system/console/configMgr)ii. Suchen Sie nach **[!UICONTROL AEM Communities Utilities]** configurationiii. Zum Erweitern des Konfigurationsbedienfelds auswählen
   * *Deaktivieren* **`Cloud Storage`**
   * Wählen Sie **[!UICONTROL Speichern]** aus

![chlimage_1-126](assets/chlimage_1-126.png)

### Lokale Datenspeicherung {#on-premise-storage}

Wenn die aktualisierte Site keine Cloud-Datenspeicherung verwendet hat, müssen alle bereits vorhandenen UGC so konvertiert werden, dass sie der neuen Struktur entsprechen, die in AEM 6.1 Communities zur Unterstützung des gemeinsamen Speichers eingeführt wurde.

Zu diesem Zweck ist ein Open Source-Migrationswerkzeug auf GitHub verfügbar:\
[AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java-APIs {#java-apis}

Beachten Sie bei der Aktualisierung von AEM 6.0 Social Communities auf AEM 6.3 Communities, dass viele APIs in verschiedene Pakete umstrukturiert wurden. Die meisten Probleme sollten bei der Verwendung einer IDE zur Anpassung der Communities-Funktionen einfach gelöst werden.

Weitere Informationen zum nicht mehr unterstützten SocialUtils-Paket finden Sie unter [SocialUtils Refactoring](socialutils.md).

Siehe auch [Verwenden von Maven für Communities](maven.md).

### Keine JSP-Komponentenvorlagen {#no-jsp-component-templates}

Das [Social-Komponenten-Framework](scf.md) (SCF) verwendet die Vorlagensprache [HandlebarsJS](https://www.handlebarsjs.com/) (HBS) anstelle von Java Server Pages (JSP), die vor AEM 6.0 verwendet wurden.

In AEM 6.0 blieben die JSP-Komponenten neben den neuen HBS-Framework-Komponenten am selben Ort, wobei sich die HBS-Komponenten in der Regel in Unterordnern mit dem Namen &quot;hbs&quot;befanden.

Ab AEM 6.1 wurden die JSP-Komponenten vollständig entfernt. Für Communities wird empfohlen, alle JSP-Komponenten durch SCF-Komponenten zu ersetzen.

## AEM Communities UGC Migration Tool {#aem-communities-ugc-migration-tool}

Das [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) ist ein Open Source-Migrationswerkzeug, das auf GitHub verfügbar ist und angepasst werden kann, um UGC aus früheren Versionen AEM Social Communities zu exportieren und in AEM Communities 6.1 oder höher zu importieren.

Zusätzlich zum Verschieben von UGC von früheren Versionen ist es auch möglich, UGC von einem [SRP](working-with-srp.md) zu einem anderen zu verschieben, z. B. von MSRP zu DSRP.

## Upgrade von AEM 5.6.1 oder früher {#upgrading-from-aem-or-earlier}

Im Prinzip gibt es drei Generationen von Komponenten für Gemeinschaften:

**Gen 1**: ungefähr CQ 5.4 bis AEM 5.6.0 - dies sind die **Collab** -Komponenten, die UGC im lokalen Repository unter Verwendung der Replikation als Möglichkeit zur plattformübergreifenden Synchronisierung gespeichert haben. Weitere Unterschiede betreffen die Implementierung mit Java Server Pages (JSP) sowie die Blog-Funktion, die nur das Authoring in der Authoring-Umgebung beinhaltet.

**Gen 2**: von AEM 5.6.1 bis AEM 6.1 - das ist eine Mischung aus **Collab** - und **Social** -Komponenten. AEM 6.0 wurde das neue [Social-Komponenten-Framework](scf.md) (SCF) eingeführt und AEM 6.2 hat einen [gängigen UGC-Store](working-with-srp.md) eingeführt, in dem über einen [Datenspeicherung Resource Provider](srp.md) (SRP) auf UGC zugegriffen wird.

**Gen 3**: Ab AEM 6.2 gibt es nur noch **soziale** Komponenten, die in SCF als Handlebars (HBS)-Komponenten implementiert sind und eine Auswahl an SRP für UGC erfordern.
