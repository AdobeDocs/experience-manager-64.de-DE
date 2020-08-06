---
title: Externalisieren von URLs
seo-title: Externalisieren von URLs
description: Der Externalizer ist ein OSGi-Dienst, der es Ihnen ermöglicht, Ressourcenpfade programmgesteuert in externe, absolute URLs umzuwandeln.
seo-description: Der Externalizer ist ein OSGi-Dienst, der es Ihnen ermöglicht, Ressourcenpfade programmgesteuert in externe, absolute URLs umzuwandeln.
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 57%

---


# Externalisieren von URLs{#externalizing-urls}

In AEM, the **Externalizer** is an OSGI service that allows you to programmatically transform a resource path (e.g. `/path/to/my/page`) into an external and absolute URL (for example, `https://www.mycompany.com/path/to/my/page`) by prefixing the path with a pre-configured DNS.

Dieser Dienst bietet einen zentralen Ort für die Konfiguration und Erstellung von externen URLs, weil eine Instanz ihre extern sichtbare URL nicht kennen kann, wenn sie hinter einer Web-Layer läuft, und weil manchmal ein Link außerhalb des Anfrageumfangs erstellt werden muss.

Auf dieser Seite wird beschrieben, wie Sie den **Externalizer**-Dienst konfigurieren und verwenden. Weitere Informationen finden Sie in den [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Konfigurieren des Externalizer-Diensts {#configuring-the-externalizer-service}

The **Externalizer** service allows you to centrally define multiple domains that can be used to programmatically prefix resource paths. Alle Domänen werden anhand eines eindeutigen Namens zum programmgesteuerten Verweisen auf die Domäne identifiziert.

Definieren Sie eine Domänenzuordnung für den **Externalizer**-Service wie folgt:

1. Navigate to the configuration manager via **Tools**, then **Web Console**, or enter `https://<host>:<port>/system/console/configMgr.`
1. Click **Day CQ Link Externalizer** to open the configuration dialog box.

   >[!NOTE]
   >
   >The direct link to the configuration is `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Definieren Sie eine Domänenzuordnung: eine Zuordnung besteht aus einem eindeutigen Namen, der im Code verwendet werden kann, um auf die Domäne, einen Leerzeichen und die Domäne zu verweisen:

   `<unique-name> [scheme://]server[:port][/contextpath]`, wohin gehört:

   * **-Schema** ist normalerweise http oder https, kann aber auch ftp usw. sein.Verwenden Sie https, um https-Verknüpfungen zu erzwingen, falls gewünscht. Es wird verwendet, wenn der Clientcode das Schema beim Anfordern der Externalisierung einer URL nicht außer Kraft setzt.
   * **server** ist der Hostname (kann ein Domänenname oder eine IP-Adresse sein).
   * **port** (optional) ist die Anschlussnummer.
   * **contextpath** (optional) wird nur festgelegt, wenn AEM als Webapp unter einem anderen Kontextpfad installiert wird.

   Beispiel: `production https://my.production.instance`

   Die folgenden Zuordnungsnamen sind vordefiniert und müssen immer so eingestellt werden, wie AEM davon abhängt:

   * **lokal** - lokale Instanz
   * **author** - das Authoring-System DNS
   * **publish** - die öffentlich zugängliche Website-DNS

   >[!NOTE]
   >
   >Eine benutzerdefinierte Konfiguration ermöglicht es Ihnen, eine neue Kategorie hinzuzufügen, z. B. „Produktion“, „Staging“ oder auch externe Nicht-AEM-Systeme, z. B. „mein-interner-Webdienst“. Auch ermöglicht sie es Ihnen, das Hartkodieren solcher URLs an verschiedenen Orten in einer Projektdatenbank zu vermeiden.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

>[!NOTE]
>
>Adobe recommends that you [add the configuration to the repository](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Verwenden des Externalizer-Diensts {#using-the-externalizer-service}

Dieser Abschnitt zeigt einige Beispiele dafür, wie der **Externalizer**-Dienst verwendet werden kann.

**Den Externalizer-Dienst rufen Sie in JSP wie folgt ab:**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Einen Pfad mit der publish-Domäne externalisieren Sie wie folgt:**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

Unter der Voraussetzung, dass die Domänenzuordnung &quot; `publish https://www.website.com`&quot;verwendet wird, erhält myExternalizedUrl den Wert &quot; `https://www.website.com/contextpath/my/page.html`&quot;.

**Einen Pfad mit der author-Domäne externalisieren Sie wie folgt:**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

Unter der Voraussetzung, dass die Domänenzuordnung &quot; `author https://author.website.com`&quot;verwendet wird, erhält myExternalizedUrl den Wert &quot; `https://author.website.com/contextpath/my/page.html`&quot;.

**Einen Pfad mit der local-Domäne externalisieren Sie wie folgt:**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

Unter der Voraussetzung, dass die Domänenzuordnung &quot; `local https://publish-3.internal`&quot;verwendet wird, erhält myExternalizedUrl den Wert &quot; `https://publish-3.internal/contextpath/my/page.html`&quot;.

Weitere Beispiele finden Sie in den [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
