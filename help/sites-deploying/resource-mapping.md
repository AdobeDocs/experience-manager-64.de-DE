---
title: Ressourcenzuordnung
seo-title: Resource Mapping
description: Erfahren Sie, wie Sie mit der Ressourcenzuordnung Umleitungen, Vanity-URLs und virtuelle Hosts für AEM definieren.
seo-description: Learn how to define redirects, vanity URLs and virtual hosts for AEM by using resource mapping.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
feature: Configuring
exl-id: 81dddbab-1a9e-49ee-b2a5-a8e4de3630d1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 61%

---

# Ressourcenzuordnung{#resource-mapping}

Die Ressourcenzuordnung wird zur Definition von Umleitungen, Vanity-URLs und virtuellen Hosts für AEM verwendet.

Diese Zuordnungen können Sie beispielsweise folgendermaßen verwenden:

* Präfix für alle Anforderungen mit `/content` damit die interne Struktur für die Besucher Ihrer Website ausgeblendet wird.
* Definieren Sie eine Umleitung, sodass alle Anforderungen an die `/content/en/gateway` -Seite Ihrer Website werden zu `https://gbiv.com/`.

Bei einer möglichen HTTP-Zuordnung wird [allen Anforderungen an localhost:4503 das Präfix /content](#configuring-an-internal-redirect-to-content) vorangestellt. Eine solche Zuordnung kann zum Ausblenden der internen Struktur für die Besucher der Website verwendet werden, da sie den Zugriff auf:

`localhost:4503/content/geometrixx/en/products.html`

mithilfe von:

`localhost:4503/geometrixx/en/products.html`

da durch die Zuordnung automatisch das Präfix hinzugefügt wird `/content` nach `/geometrixx/en/products.html`.

>[!CAUTION]
>
>Vanity-URLs unterstützen keine Regex-Muster.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Sling-Dokumentation sowie unter [Zuordnungen für die Ressourcenauflösung](https://sling.apache.org/site/resources.html) und [Ressourcen](https://sling.apache.org/site/mappings-for-resource-resolution.html).

## Anzeigen von Zuordnungsdefinitionen {#viewing-mapping-definitions}

Die Zuordnungen bilden zwei Listen, die der JCR-Ressourcen-Resolver auswertet (von oben nach unten), um eine Übereinstimmung zu finden.

Diese Listen können (zusammen mit Konfigurationsinformationen) unter der **JCR ResourceResolver** Option der Felix-Konsole; Beispiel: `https://<host>:<port>/system/console/jcrresolver`:

* Konfiguration

   Zeigt die aktuelle Konfiguration an (wie für die Variable [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md).

* Konfigurationstest

    Hiermit können Sie eine URL oder einen Ressourcenpfad eingeben. Klicken Sie auf **Resolve** oder **Map**, um festzulegen, wie das System den Eintrag transformiert.

* **Resolver Map Entries** Die Liste der Einträge, die von den ResourceResolver.resolve-Methoden für die Zuordnung von URLs zu Ressourcen verwendet wird.

* **Mapping Map Entries** Die Liste der Einträge, die von den ResourceResolver.map-Methoden für die Zuordnung von Ressourcenpfaden zu URLs verwendet wird.

Die beiden Listen enthalten verschiedene Einträge, darunter die von der/den Anwendung/en als Standardwerte definierten. Sie dienen häufig dazu, URLs für die Benutzer zu vereinfachen.

Die Listen verbinden ein **Muster**, d. h. einen auf die Anforderung abgestimmten regulären Ausdruck, mit einer **Ersetzung**, die die anzuwendende Umleitung definiert.

So löst beispielsweise das

**Muster** `^[^/]+/[^/]+/welcome$`

das

**Ersatz** `/libs/cq/core/content/welcome.html`.

aus, um die Anforderung

`http://localhost:4503/welcome`

in:

`http://localhost:4503/libs/cq/core/content/welcome.html`

Neue Zuordnungsdefinitionen werden im Repository erstellt.

>[!NOTE]
>
>Es stehen viele Ressourcen zur Verfügung, mit denen erläutert wird, wie reguläre Ausdrücke definiert werden. Beispiel [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## Erstellen von Zuordnungsdefinitionen in AEM {#creating-mapping-definitions-in-aem}

Eine Standardinstallation von AEM umfasst folgenden Ordner:

`/etc/map/http`

Dies ist die Struktur, die beim Definieren von Zuordnungen für das HTPP-Protokoll verwendet wird. Andere Ordner ( `sling:Folder`) kann unter erstellt werden. `/etc/map` für alle anderen Protokolle, die Sie zuordnen möchten.

### Konfigurieren einer internen Umleitung an „/content“ {#configuring-an-internal-redirect-to-content}

So erstellen Sie die Zuordnung, die einer Anforderung an http://localhost:4503/ vorangestellt ist mit `/content`:

1. Navigieren Sie mit CRXDE zu `/etc/map/http`.

1. Erstellen Sie einen neuen Knoten:

   * **Typ** `sling:Mapping`

      Dieser Knotentyp ist für solche Zuordnungen vorgesehen, seine Verwendung ist jedoch nicht obligatorisch.

   * **Name** `localhost_any`

1. Klicken Sie auf **Alle speichern**.
1. **Fügen Sie** diesem Knoten die folgenden Eigenschaften hinzu:

   * **Name** `sling:match`

      * **Typ** `String`
      * **Wert** `localhost.4503/`
   * **Name** `sling:internalRedirect`

      * **Typ** `String`
      * **Wert** `/content/`


1. Klicken Sie auf **Alle speichern**.

Dadurch wird eine Anfrage verarbeitet, z. B.:\
`localhost:4503/geometrixx/en/products.html`\
wie wenn:\
`localhost:4503/content/geometrixx/en/products.html`\
wurden beantragt.

>[!NOTE]
>
>Weitere Informationen zu den verfügbaren Sling-Eigenschaften und wie diese konfiguriert werden können, finden Sie in der Sling-Dokumentation unter [Ressourcen](https://sling.apache.org/site/mappings-for-resource-resolution.html)

>[!NOTE]
>
>Sie können `/etc/map.publish` , um die Konfigurationen für die Veröffentlichungsumgebung zu speichern. Diese müssen dann repliziert werden und der neue Speicherort ( `/etc/map.publish`) für die **Zuordnungsort** des [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) der Veröffentlichungsumgebung.
