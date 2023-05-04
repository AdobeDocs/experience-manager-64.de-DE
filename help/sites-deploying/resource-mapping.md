---
title: Ressourcenzuordnung
seo-title: Resource Mapping
description: Erfahren Sie, wie Sie mithilfe der Ressourcenzuordnung Umleitungen, Vanity-URLs und virtuelle Hosts für AEM definieren.
seo-description: Learn how to define redirects, vanity URLs and virtual hosts for AEM by using resource mapping.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
feature: Configuring
exl-id: 81dddbab-1a9e-49ee-b2a5-a8e4de3630d1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 66%

---

# Ressourcenzuordnung{#resource-mapping}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die Ressourcenzuordnung wird verwendet, um Umleitungen, Vanity-URLs und virtuelle Hosts für AEM zu definieren.

Diese Zuordnungen können Sie beispielsweise verwenden, um:

* Allen Anfragen das Präfix `/content` voranzustellen, sodass die interne Struktur für Besucher Ihrer Website ausgeblendet wird.
* Eine Umleitung zu definieren, sodass alle Anfragen an die Seite `/content/en/gateway` Ihrer Website zu `https://gbiv.com/` umgeleitet werden.

Eine mögliche HTTP-Zuordnung [Präfixiert alle Anforderungen an localhost:4503 mit /content](#configuring-an-internal-redirect-to-content). Eine solche Zuordnung kann zum Ausblenden der internen Struktur für die Besucher der Website verwendet werden, da sie den Zugriff auf:

`localhost:4503/content/geometrixx/en/products.html`

mithilfe von:

`localhost:4503/geometrixx/en/products.html`

da die Zuordnung automatisch das Präfix `/content` zu `/geometrixx/en/products.html` hinzufügt.

>[!CAUTION]
>
>Vanity-URLs unterstützen keine Regex-Muster.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Sling-Dokumentation sowie unter [Zuordnungen für die Ressourcenauflösung](https://sling.apache.org/site/resources.html) und [Ressourcen](https://sling.apache.org/site/mappings-for-resource-resolution.html).

## Anzeigen von Zuordnungsdefinitionen {#viewing-mapping-definitions}

Die Zuordnungen bilden zwei Listen, die der JCR Resource Resolver auswertet (von oben nach unten), um eine Übereinstimmung zu finden.

Diese Listen können (zusammen mit Konfigurationsinformationen) unter der Option **JCR ResourceResolver** der Felix-Konsole angezeigt werden. Beispiel: `https://<host>:<port>/system/console/jcrresolver`:

* Konfiguration

   Zeigt die aktuelle Konfiguration an (wie für die Variable [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md).

* Konfigurationstest

   Hiermit können Sie eine URL oder einen Ressourcenpfad eingeben. Klicken Sie auf **Resolve** oder **Map**, um festzulegen, wie das System den Eintrag transformiert.

* **Resolver Map Entries**
Die Liste der Einträge, die von den ResourceResolver.resolve-Methoden für die Zuordnung von URLs zu Ressourcen verwendet wird.

* **Mapping Map Entries**
Die Liste der Einträge, die von den ResourceResolver.map-Methoden für die Zuordnung von Ressourcenpfaden zu URLs verwendet wird.

Die beiden Listen enthalten verschiedene Einträge, darunter die von der/den Anwendung/en als Standardwerte definierten. Diese zielen häufig darauf ab, URLs für den Benutzer zu vereinfachen.

Das Listen-Paar enthält eine **Muster**, einen regulären Ausdruck, der mit der Anfrage übereinstimmt, mit einer **Ersatz** die die Umleitung definiert, die durchgesetzt werden soll.

Beispiel:

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
>Es stehen eine Vielzahl von Ressourcen zur Verfügung, die das Definieren regulärer Ausdrücke erläutern, z. B. [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## Erstellen von Zuordnungsdefinitionen in AEM {#creating-mapping-definitions-in-aem}

In einer Standardinstallation von AEM finden Sie den Ordner:

`/etc/map/http`

Dies ist die Struktur, die beim Definieren von Zuordnungen für das HTTP-Protokoll verwendet wird. Wenn Sie Zuordnungen für weitere Protokolle erstellen möchten, können unter `/etc/map` weitere Ordner (`sling:Folder`) erstellt werden.

### Konfigurieren einer internen Umleitung an /content {#configuring-an-internal-redirect-to-content}

So erstellen Sie die Zuordnung, die einer Anforderung an http://localhost:4503/ vorangestellt ist mit `/content`:

1. Navigieren Sie mithilfe von CRXDE zu `/etc/map/http`.

1. Erstellen Sie einen neuen Knoten:

   * **Typ** `sling:Mapping`

      Dieser Knotentyp ist für solche Zuordnungen vorgesehen, seine Verwendung ist jedoch nicht obligatorisch.

   * **Name** `localhost_any`

1. Klicken Sie auf **Alle speichern**.
1. **Fügen Sie diesem Knoten die folgenden Eigenschaften hinzu:**

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
>Die Konfigurationen für die Veröffentlichungsumgebung können unter `/etc/map.publish` gespeichert werden. Diese müssen dann repliziert und der neue Speicherort (`/etc/map.publish`) muss für den **Zuordnungs-Speicherort** des [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) der Veröffentlichungsumgebung konfiguriert werden.
