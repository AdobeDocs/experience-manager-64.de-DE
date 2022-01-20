---
title: Externalisieren von URLs
seo-title: Externalizing URLs
description: Der Externalizer ist ein OSGi-Dienst, der es Ihnen ermöglicht, Ressourcenpfade programmgesteuert in externe, absolute URLs umzuwandeln.
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
exl-id: 123ef72b-f09b-47eb-9b5a-e0deb38799df
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 61%

---

# Externalisieren von URLs{#externalizing-urls}

In AEM **Externalizer** ist ein OSGi-Dienst, mit dem Sie einen Ressourcenpfad (z. B. `/path/to/my/page`) in eine externe und absolute URL (z. B. `https://www.mycompany.com/path/to/my/page`), indem dem Pfad ein vorkonfiguriertes DNS vorangestellt wird.

Dieser Dienst bietet einen zentralen Ort für die Konfiguration und Erstellung von externen URLs, weil eine Instanz ihre extern sichtbare URL nicht kennen kann, wenn sie hinter einer Web-Layer läuft, und weil manchmal ein Link außerhalb des Anfrageumfangs erstellt werden muss.

Auf dieser Seite wird beschrieben, wie Sie den **Externalizer**-Dienst konfigurieren und verwenden. Weitere Informationen finden Sie in den [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Konfigurieren des Externalizer-Diensts {#configuring-the-externalizer-service}

Die **Externalizer** -Dienst ermöglicht es Ihnen, zentral mehrere Domänen zu definieren, die zum programmatischen Präfix von Ressourcenpfaden verwendet werden können. Alle Domänen werden anhand eines eindeutigen Namens zum programmgesteuerten Verweisen auf die Domäne identifiziert.

Definieren Sie eine Domänenzuordnung für den **Externalizer**-Service wie folgt:

1. Navigieren Sie zum Konfigurationsmanager über **Instrumente**, dann **Web-Konsole** oder geben Sie `https://<host>:<port>/system/console/configMgr.`
1. Klicken Sie auf **Day CQ Link Externalizer**, um das Konfigurationsdialogfeld zu öffnen.

   >[!NOTE]
   >
   >Der Direkt-Link zur Konfiguration lautet `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Definieren Sie eine Domänenzuordnung: Eine Zuordnung besteht aus einem eindeutigen Namen, der im Code verwendet werden kann, um auf die Domäne, ein Leerzeichen und die Domäne zu verweisen:

   `<unique-name> [scheme://]server[:port][/contextpath]`, Hierbei gilt:

   * **schema** ist normalerweise http oder https, kann aber auch ftp usw. sein.Verwenden Sie https, um https-Verknüpfungen zu erzwingen, falls gewünscht. Es wird verwendet, wenn der Clientcode das Schema beim Anfordern der Externalisierung einer URL nicht außer Kraft setzt.
   * **server** ist der Hostname (kann ein Domänenname oder eine IP-Adresse sein).
   * **port** (optional) ist die Anschlussnummer.
   * **contextpath** (optional) wird nur festgelegt, wenn AEM als Web-App unter einem anderen Kontextpfad installiert ist.

   Beispiel: `production https://my.production.instance`

   Die folgenden Zuordnungsnamen sind vordefiniert und müssen immer festgelegt werden, da AEM auf sie angewiesen ist:

   * **lokal** - die lokale Instanz
   * **author** - DNS des Authoring-Systems
   * **publish** - das DNS der öffentlichen Website

   >[!NOTE]
   >
   >Eine benutzerdefinierte Konfiguration ermöglicht es Ihnen, eine neue Kategorie hinzuzufügen, z. B. „Produktion“, „Staging“ oder auch externe Nicht-AEM-Systeme, z. B. „mein-interner-Webdienst“. Auch ermöglicht sie es Ihnen, das Hartkodieren solcher URLs an verschiedenen Orten in einer Projektdatenbank zu vermeiden.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

>[!NOTE]
>
>Adobe empfiehlt, dass Sie [die Konfiguration zum Repository hinzufügen](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Verwenden des Externalizer-Diensts {#using-the-externalizer-service}

Dieser Abschnitt zeigt einige Beispiele dafür, wie der **Externalizer**-Dienst verwendet werden kann.

**Den Externalizer-Dienst rufen Sie in JSP wie folgt ab:**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Einen Pfad mit der publish-Domain externalisieren Sie wie folgt:**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

Angenommen, die Domänenzuordnung &quot; `publish https://www.website.com`&quot;, endet myExternalizedUrl mit dem Wert &quot; `https://www.website.com/contextpath/my/page.html`&quot;.

**So externalisieren Sie einen Pfad mit der Domain „author“:**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

Angenommen, die Domänenzuordnung &quot; `author https://author.website.com`&quot;, endet myExternalizedUrl mit dem Wert &quot; `https://author.website.com/contextpath/my/page.html`&quot;.

**So externalisieren Sie einen Pfad mit der Domain „local“:**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

Angenommen, die Domänenzuordnung &quot; `local https://publish-3.internal`&quot;, endet myExternalizedUrl mit dem Wert &quot; `https://publish-3.internal/contextpath/my/page.html`&quot;.

Weitere Beispiele finden Sie in den [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
