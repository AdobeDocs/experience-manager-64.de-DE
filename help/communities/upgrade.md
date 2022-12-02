---
title: Upgrade auf AEM 6.4 Communities
seo-title: Upgrading to AEM 6.4 Communities
description: Upgrade von einer früheren Version auf AEM 6.4 Communities
seo-description: How to upgrade from an earlier version to AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: 0f82e82cf6e09a2734893a98d67ed1a84b1fec5e
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 4%

---

# Upgrade auf AEM 6.4 Communities {#upgrading-to-aem-communities}

Abhängig von der Topologie und den Funktionen der einzelnen Websites können beim Upgrade auf AEM Communities 6.4 oder bei der Installation des neuesten Feature Packs die folgenden Aktionen erforderlich sein:

Dieser Abschnitt ist spezifisch für Communities und ergänzt die in [Upgrade auf AEM 6.4](../../help/sites-deploying/upgrade.md) (Plattform).

## Upgrade von AEM 6.1 oder höher {#upgrading-from-aem-or-later}

### Reindex Solr {#reindex-solr}

Bei der Installation eines neuen Communities Feature Packs in einer mit MSRP konfigurierten Implementierung ist Folgendes erforderlich:

1. Installieren Sie die [neueste Feature Pack](deploy-communities.md#latestfeaturepack)
2. Installieren Sie die [aktuelle Solr-Konfigurationsdateien](msrp.md#upgrading)
3. Reindex MSRP

   siehe Abschnitt [MSRP-Reindex-Tool](msrp.md#msrp-reindex-tool)

### Aktivierung 2.0 {#enablement}

Ab AEM 6.3 speichern die Aktivierungsfunktionen keine Reporting-Informationen mehr in MySQL. MySQL wird nur noch für die Nachverfolgung von SCORM-Inhalten benötigt.

Bitte kontaktieren Sie uns [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html) für Unterstützung bei der Migration von Inhalten von Enablement 1.0.

## Upgrade von AEM 6.0 {#upgrading-from-aem}

Wenn bereits vorhandene UGC beibehalten werden müssen, hängt die Vorgehensweise davon ab, ob die gespeicherte UGC-Bereitstellung [On-Premise](#on-premise-storage) oder in [Adobe Cloud](#adobe-cloud-storage).

### Adobe Cloud Storage {#adobe-cloud-storage}

Wenn die aktualisierte Site für die Verwendung von Adobe Cloud Storage konfiguriert wurde, kann es (falsch) so aussehen, als wäre alles UGC verloren gegangen, da die SRP-Methoden die bereits vorhandene UGC nicht am alten Speicherort finden können.

Somit besteht die Möglichkeit, ASRP anzuweisen, `AEM 6.0 compatability-mode` , um auf UGC zuzugreifen.

Für alle AEM 6.3 Autoren- und Veröffentlichungsinstanzen:

1. Anmelden mit Administratorrechten und konfigurieren [ASRP](asrp.md).
1. Führen Sie die folgenden Schritte aus, um die vorhandene benutzergenerierte Anzeige sichtbar zu machen:

   i. Navigieren Sie zur Web-Konsole. Die Standardeinstellung ist
   `https://localhost:4502/system/console/configMgr` möglich.

   ii. Suchen **[!UICONTROL AEM Communities Utilities]** und wählen Sie aus, um das Konfigurationsfenster zu erweitern.

   iii. Deaktivieren **[!UICONTROL Cloud-Speicher]** und klicken Sie auf **[!UICONTROL Speichern]**.

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

Die [Social-Komponenten-Framework](scf.md) (SCF) verwendet die [HandlebarsJS](https://handlebarsjs.com/) (HBS) Vorlagensprache anstelle von Java Server Pages (JSP), die vor AEM 6.0 verwendet wurden.

In AEM 6.0 blieben die JSP-Komponenten neben den neuen HBS-Framework-Komponenten am selben Speicherort, wobei sich die HBS-Komponenten in der Regel in Unterordnern namens &quot;hbs&quot;befanden.

Ab AEM 6.1 wurden die JSP-Komponenten vollständig entfernt. Für Communities wird empfohlen, die gesamte Verwendung von JSP-Komponenten durch SCF-Komponenten zu ersetzen.

## AEM Communities UGC Migration Tool {#aem-communities-ugc-migration-tool}

Die [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) ist ein Open-Source-Migrationswerkzeug, das auf GitHub verfügbar ist und angepasst werden kann, um benutzergenerierte Inhalte aus früheren Versionen AEM Social Communities zu exportieren und in AEM Communities 6.1 oder höher zu importieren.

Zusätzlich zum Verschieben von UGC aus früheren Versionen ist es auch möglich, das Tool zu verwenden, um UGC von einer zu verschieben [SRP](working-with-srp.md) zu einem anderen, z. B. von MSRP zu DSRP.

## Upgrade von AEM 5.6.1 oder früher {#upgrading-from-aem-or-earlier}

Grundsätzlich gibt es drei Generationen von Communities-Komponenten:

**Gen 1**: ungefähr CQ 5.4 bis AEM 5.6.0 - dies sind die **collab** Komponenten, die benutzergenerierte Inhalte im lokalen Repository mithilfe der Replikation als Möglichkeit zur plattformübergreifenden Synchronisierung von benutzergenerierten Inhalten gespeichert haben. Weitere Unterschiede betreffen die Implementierung mit Java Server Pages (JSP) sowie die Blog-Funktion, die nur aus der Authoring-Umgebung besteht.

**Gen 2**: von AEM 5.6.1 bis AEM 6.1 - dies ist eine Mischung aus **collab** und **social** Komponenten. Mit AEM 6.0 wurde die neue [Social-Komponenten-Framework](scf.md) (SCF) und AEM 6.2 wurde eine [gängiger UGC-Speicher](working-with-srp.md) wo auf benutzergenerierte Inhalte über eine [Speicherressourcenanbieter](srp.md) (SRP).

**Gen 3**: Ab AEM 6.2 gibt es nur noch **social** Komponenten, die in SCF als Handlebars (HBS)-Komponenten implementiert sind und eine Auswahl von SRP für UGC erfordern.
