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
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 5%

---

# Upgrade auf AEM 6.4 Communities {#upgrading-to-aem-communities}

Abhängig von der Topologie und den Funktionen der einzelnen Websites können beim Upgrade auf AEM Communities 6.4 oder bei der Installation des neuesten Feature Packs die folgenden Aktionen erforderlich sein:

Dieser Abschnitt ist spezifisch für Communities und ergänzt die Informationen unter [Aktualisierung auf AEM 6.4](../../help/sites-deploying/upgrade.md) (Plattform).

## Upgrade von AEM 6.1 oder höher {#upgrading-from-aem-or-later}

### Reindex Solr {#reindex-solr}

Bei der Installation eines neuen Communities Feature Packs in einer mit MSRP konfigurierten Implementierung ist Folgendes erforderlich:

1. Installieren Sie das [neueste Feature Pack](deploy-communities.md#latestfeaturepack)
2. Installieren Sie die [neuesten Solr-Konfigurationsdateien](msrp.md#upgrading)
3. Reindex MSRP

   Siehe Abschnitt [MSRP Reindex Tool](msrp.md#msrp-reindex-tool)

### Aktivierung 2.0 {#enablement}

Ab AEM 6.3 speichern die Aktivierungsfunktionen keine Reporting-Informationen mehr in MySQL. MySQL wird nur noch für die Nachverfolgung von SCORM-Inhalten benötigt.

Wenden Sie sich an [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html), um Unterstützung bei der Migration von Inhalten von Enablement 1.0 zu erhalten.

## Upgrade von AEM 6.0 {#upgrading-from-aem}

Wenn bereits vorhandene benutzergenerierte Inhalte beibehalten werden müssen, hängt die Vorgehensweise davon ab, ob die bereitgestellte Bereitstellung UGC [On-Premise](#on-premise-storage) oder in der [Adobe Cloud](#adobe-cloud-storage) speichert.

### Adobe Cloud Storage {#adobe-cloud-storage}

Wenn die aktualisierte Site für die Verwendung von Adobe Cloud Storage konfiguriert wurde, kann es (falsch) so aussehen, als wäre alles UGC verloren gegangen, da die SRP-Methoden die bereits vorhandene UGC nicht am alten Speicherort finden können.

Somit besteht die Möglichkeit, ASRP anzuweisen, `AEM 6.0 compatability-mode` für den Zugriff auf UGC zu verwenden.

Für alle AEM 6.3 Autoren- und Veröffentlichungsinstanzen

1. Anmelden mit Administratorrechten
2. Konfigurieren von [ASRP](asrp.md)
3. Führen Sie die folgenden Schritte aus, um bereits vorhandene benutzergenerierte Inhalte sichtbar zu machen:
i. Navigieren Sie zur Web-Konsole, z. B.
   [https://&lt;host>:&lt;port>/system/console/](http://localhost:4502/system/console/configMgr)
configMgrii. Suchen Sie nach der Konfiguration **[!UICONTROL AEM Communities Utilities]** .
iii. Zum Erweitern des Konfigurationsbereichs auswählen
   * *Deaktivieren* **`Cloud Storage`**
   * Wählen Sie **[!UICONTROL Speichern]** aus

![chlimage_1-126](assets/chlimage_1-126.png)

### On-Premise-Speicher {#on-premise-storage}

Wenn die aktualisierte Site keinen Cloud-Speicher verwendet, muss jeder bereits vorhandene benutzergenerierte Speicher entsprechend der neuen Struktur konvertiert werden, die in AEM 6.1 Communities eingeführt wurde, um den gemeinsamen Speicher zu unterstützen.

Zu diesem Zweck ist ein Open-Source-Migrationstool auf GitHub verfügbar:\
[AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java-APIs {#java-apis}

Beachten Sie bei der Aktualisierung von AEM 6.0 Social Communities auf AEM 6.3 Communities, dass viele APIs in verschiedene Pakete neu organisiert wurden. Die meisten sollten leicht gelöst werden, wenn eine IDE zur Anpassung von Communities-Funktionen verwendet wird.

Weitere Informationen zum veralteten SocialUtils-Paket finden Sie unter [SocialUtils-Refaktorierung](socialutils.md).

Siehe auch [Verwenden von Maven für Communities](maven.md).

### Keine JSP-Komponentenvorlagen {#no-jsp-component-templates}

Das [Social Component Framework](scf.md) (SCF) verwendet die `HandlebarsJS` (HBS)-Vorlagensprache anstelle von Java Server Pages (JSP), die vor AEM 6.0 verwendet wurden.

In AEM 6.0 blieben die JSP-Komponenten neben den neuen HBS-Framework-Komponenten am selben Speicherort, wobei sich die HBS-Komponenten in der Regel in Unterordnern namens &quot;hbs&quot;befanden.

Ab AEM 6.1 wurden die JSP-Komponenten vollständig entfernt. Für Communities wird empfohlen, die gesamte Verwendung von JSP-Komponenten durch SCF-Komponenten zu ersetzen.

## AEM Communities UGC Migration Tool {#aem-communities-ugc-migration-tool}

Das [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) ist ein auf GitHub verfügbares Open-Source-Migrationstool, das angepasst werden kann, um benutzergenerierte Inhalte aus früheren Versionen AEM Social Communities zu exportieren und in AEM Communities 6.1 oder höher zu importieren.

Zusätzlich zum Verschieben von UGC aus früheren Versionen ist es auch möglich, UGC mit dem Tool von einem [SRP](working-with-srp.md) in ein anderes zu verschieben, z. B. von MSRP zu DSRP.

## Upgrade von AEM 5.6.1 oder früher {#upgrading-from-aem-or-earlier}

Grundsätzlich gibt es drei Generationen von Communities-Komponenten:

**Gen 1**: ungefähr CQ 5.4 bis AEM 5.6.0 - dies sind die  **** Kooperationskomponenten, die UGC im lokalen Repository mithilfe der Replikation als Mittel zur plattformübergreifenden Synchronisierung von UGC gespeichert haben. Weitere Unterschiede betreffen die Implementierung mit Java Server Pages (JSP) sowie die Blog-Funktion, die nur aus der Authoring-Umgebung besteht.

**Gen 2**: von AEM 5.6.1 bis AEM 6.1 - dies ist eine Mischung aus  **** Social- **** Komponenten. Mit AEM 6.0 wurde das neue [Social-Komponenten-Framework](scf.md) (SCF) eingeführt und AEM 6.2 wurde ein [allgemeiner UGC-Speicher](working-with-srp.md) eingeführt, auf den über einen [Speicherressourcenanbieter](srp.md) (SRP) auf UGC zugegriffen wird.

**Gen 3**: Ab AEM 6.2 gibt es nur noch  **** Social-Komponenten, die in SCF als Handlebars (HBS)-Komponenten implementiert sind, die eine Auswahl von SRP für UGC erfordern.
