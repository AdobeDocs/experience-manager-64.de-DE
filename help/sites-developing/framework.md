---
title: AEM-Tagging-Framework
seo-title: AEM Tagging Framework
description: Versehen Sie Inhalte mit Tags und nutzen Sie die AEM-Tagging-Infrastruktur,
seo-description: Tag content and leverage the AEM Tagging infrastructure
uuid: 55ba5977-217b-4b0f-a794-ddb9216ee62b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 4b680d17-383b-4173-a444-0b7bdb24e6c8
feature: Tagging
exl-id: bae592db-dc36-409f-b841-0582c464c3f6
source-git-commit: 381e760d1634dec6c6cdb933fd4da6b4652e6ff7
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 66%

---

# AEM-Tagging-Framework{#aem-tagging-framework}

So taggen Sie Inhalte und nutzen die AEM Tagging-Infrastruktur :

* Das Tag muss unterhalb des [Stammknotens der Taxonomie](#taxonomy-root-node) als Knoten vom Typ [`cq:Tag`](#tags-cq-tag-node-type) vorhanden sein.
* Der `NodeType` des mit Tags versehenen Inhaltsknotens muss das Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) beinhalten.
* Die [TagID](#tagid) wird zum Inhaltsknoten hinzugefügt [`cq:tags`](#tagged-content-cq-tags-property) -Eigenschaft und wird in einen Knoten des Typs aufgelöst. [`cq:Tag`.](#tags-cq-tag-node-type)

## Tags: cq:Tag-Knotentyp  {#tags-cq-tag-node-type}

Die Funktion eines Tags wird im Repository in einem Knoten vom Typ `cq:Tag.` erfasst.

Ein Tag kann ein einfaches Wort sein (z. B. `fruit`) oder stellen eine hierarchische Taxonomie dar (z. B. `fruit/apple`, d. h. sowohl Obst im Allgemeinen als auch der spezifischere Apfel).

Tags werden anhand einer eindeutigen Tag-ID identifiziert.

Ein Tag verfügt über optionale Metainformationen wie einen Titel, lokalisierte Titel und eine Beschreibung. Der Titel sollte, falls vorhanden, auf Benutzeroberflächen anstelle der `TagID` angezeigt werden.

Das Tagging-Framework bietet außerdem die Möglichkeit, Autoren und Website-Besuchern die Verwendung bestimmter, vordefinierter Tags vorzugeben.

### Tag-Eigenschaften {#tag-characteristics}

* Der Knotentyp ist `cq:Tag`.
* Der Knotenname ist eine Komponente der [`TagID`.](#tagid)
* Die [`TagID`](#tagid) umfasst immer einen [Namespace](#tag-namespace).
* Optional `jcr:title` -Eigenschaft (der Titel, der in der Benutzeroberfläche angezeigt werden soll)
* Optional `jcr:description` property
* Wenn untergeordnete Knoten enthalten, wird dies als [Container-Tag.](#container-tags)
* Sie wird im Repository unter einem Basispfad gespeichert, der als [Stammknoten der Taxonomie.](#taxonomy-root-node)

### TagID (Tag-ID) {#tagid}

Eine `TagID` identifiziert einen Pfad, der einen Tag-Knoten im Repository ergibt.

In der Regel wird die `TagID` ist eine Kurzform, die mit dem -Namespace beginnt oder absolut beginnend mit der [Stammknoten der Taxonomie](#taxonomy-root-node).

Wenn Inhalt mit Tags versehen ist und noch nicht vorhanden ist, wird die [`cq:tags`](#tagged-content-cq-tags-property) -Eigenschaft zum Inhaltsknoten hinzugefügt wird und die `TagID` wird zum String-Array-Wert der Eigenschaft hinzugefügt.

Die `TagID` besteht aus einem [Namespace](#tag-namespace) gefolgt von der lokalen `TagID`. [Container-Tags](#container-tags) weisen untergeordnete Tags auf, die eine hierarchische Reihenfolge in der Taxonomie darstellen. Untergeordnete Tags können dazu verwendet werden, auf Tags genau wie auf eine andere lokale `TagID` zu verweisen. Beispielsweise ist es erlaubt, Inhalte mit dem Tag `fruit` zu versehen, auch wenn es sich um ein Container-Tag mit untergeordneten Tags handelt, z. B. `fruit/apple` oder `fruit/banana`.

### Stammknoten der Taxonomie {#taxonomy-root-node}

Der Stammknoten der Taxonomie ist der Basispfad für alle Tags im Repository. Der Stammknoten der Taxonomie darf kein Knoten vom Typ `cq:Tag` sein.

In AEM ist der Basispfad `/content/cq:tags` und der Stammknoten ist vom Typ `cq:Folder`.

### Tag-Namespace {#tag-namespace}

Namespaces erlauben Gruppeneinträge. Der häufigste Anwendungsfall besteht darin, einen Namespace pro Site (z. B. öffentlich, intern und portal) oder pro größerer Anwendung (z. B. Sites, Assets, Forms) zu verwenden. Namespaces können jedoch für verschiedene andere Anforderungen verwendet werden. Namespaces werden in der Benutzeroberfläche verwendet, um nur die Untergruppe von Tags (d. h. die Tags eines bestimmten Namespace) anzuzeigen, die auf den aktuellen Inhalt anwendbar sind.

Der Namespace des Tags ist die erste Ebene im Teilbaum der Taxonomie, der den Knoten direkt unterhalb des [Stammknotens der Taxonomie darstellt](#taxonomy-root-node). Ein Namespace ist ein Knoten vom Typ `cq:Tag`, dessen übergeordnetes Element nicht vom Knotentyp `cq:Tag` ist.

Alle Tags haben einen Namespace. Wenn kein Namespace angegeben ist, wird das Tag dem Standard-Namespace zugewiesen, der `TagID` `default` (Titel ist `Standard Tags`), das `/content/cq:tags/default`.

### Container-Tags {#container-tags}

Container-Tags sind Knoten vom Typ `cq:Tag`, die eine beliebige Anzahl untergeordneter Knoten von beliebigen Typen enthalten. Das ermöglicht die Erweiterung des Tag-Modells mit benutzerdefinierten Metadaten.

Darüber hinaus dienen Container-Tags (oder Super-Tags) in einer Taxonomie als Unter-Zusammenfassung aller Unter-Tags. Beispielsweise Inhalte, die mit `fruit/apple` wird als mit `fruit` sowie Das bedeutet, dass die Suche nach Inhalten nur mit `fruit` auch den Inhalt finden, mit dem `fruit/apple`.

### Auflösen von Tag-IDs {#resolving-tagids}

Wenn die Tag-ID einen Doppelpunkt enthält `:`, trennt der Doppelpunkt den Namespace vom Tag oder der Unter-Taxonomie, die dann durch normale Schrägstriche getrennt werden. `/`. Wenn in der Tag-ID kein Doppelpunkt vorkommt, ist der Standard-Namespace impliziert.

Der standardmäßige und einzige Speicherort von Tags befindet sich unter `/content/cq:tags`.

Verweisen auf nicht vorhandene Pfade oder Pfade, die nicht auf eine `cq:Tag` -Knoten werden als ungültig betrachtet und ignoriert.

Die folgende Tabelle zeigt einige Beispiele `TagIDs`, ihre Elemente und wie die `TagID` wird in einen absoluten Pfad im Repository aufgelöst.

| `TagID` | Namespace | Lokale ID | Container-Tag(s) | Leaf-Tag | Absoluter Repository-Pfad |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | Ohne | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | Ohne | Ohne | Ohne | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### Lokalisierung des Tag-Titels {#localization-of-tag-title}

Wenn das Tag den optionalen Titelstring enthält (`jcr:title`) ist es möglich, den Titel zur Anzeige zu lokalisieren, indem die Eigenschaft `jcr:title.<locale>` > hinzugefügt wird.

Weitere Informationen finden Sie unter:

* [Tags in verschiedenen Sprachen,](/help/sites-developing/building.md#tags-in-different-languages) beschreibt die Verwendung der APIs.
* [Verwalten von Tags in verschiedenen Sprachen](/help/sites-administering/tags.md#managing-tags-in-different-languages) beschreibt die Verwendung der Tagging-Konsole.

### Zugriffssteuerung {#access-control}

Tags bestehen als Knoten im Repository unter dem [Stammknoten der Taxonomie.](#taxonomy-root-node) Sie können Autoren und Site-Besuchern die Möglichkeit geben, Tags in einem bestimmten Namespace zu erstellen oder zu verweigern, indem Sie entsprechende ACLs im Repository festlegen.

Außerdem wird durch das Verweigern von Leseberechtigungen für bestimmte Tags oder Namespaces die Fähigkeit gesteuert, Tags auf bestimmte Inhalte anzuwenden.

Eine typische Konfiguration umfasst:

* Gewähren von Schreibzugriff auf alle Namespaces für die Gruppe/Rolle `tag-administrators` (unter `/content/cq:tags` hinzufügen/ändern). 
   * Diese Gruppe enthält AEM standardmäßig.
* Gewähren von Lesezugriff für Benutzer/Autoren auf alle Namespaces, die sie lesen können müssen (meist alle).
* Gewähren von Schreibzugriff für Benutzer/Autoren auf die Namespaces, bei denen Tags durch Benutzer/Autoren frei definierbar sein müssen (`add_node` unter `/content/cq:tags/some_namespace`).

## Tag-barer Inhalt: cq:Taggable-Mixin {#taggable-content-cq-taggable-mixin}

Damit Anwendungsentwickler einen Inhaltstyp mit Tags versehen können, muss die Registrierung eines Knotens ([CND](https://jackrabbit.apache.org/node-type-notation.html)) das Mixin `cq:Taggable` oder das Mixin `cq:OwnerTaggable` umfassen.

Das Mixin `cq:OwnerTaggable`, das von `cq:Taggable` übernimmt, soll anzeigen, dass der Inhalt vom Besitzer/Autor klassifiziert werden kann. In AEM handelt es sich hierbei nur um ein Attribut des Knotens `cq:PageContent`. Das Mixin `cq:OwnerTaggable` wird vom Tagging-Framework nicht benötigt.

>[!NOTE]
>
>Es wird empfohlen, Tags nur auf dem Knoten der obersten Ebene eines aggregierten Inhaltselements (oder dessen `jcr:content`-Knoten) zu aktivieren. Beispiele dafür sind:
>
>* Seiten ( `cq:Page`), wobei die `jcr:content`node is type `cq:PageContent` , der Folgendes umfasst: `cq:Taggable` Mixin.
>* Assets (`cq:Asset`), deren Knoten `jcr:content/metadata` immer das Mixin `cq:Taggable` umfassen


### Knotentypnotation (CND) {#node-type-notation-cnd}

Knotentypdefinitionen sind im Repository als CND-Dateien vorhanden. Die CND-Notation wird als Teil der JCR-Dokumentation [hier](https://jackrabbit.apache.org/node-type-notation.html) definiert.

Die wichtigsten Definitionen für die Knotentypen in AEM sind wie folgt:

```text
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## Inhalt mit Tags: cq:tags-Eigenschaft {#tagged-content-cq-tags-property}

Die `cq:tags` -Eigenschaft ist ein Zeichenfolgen-Array, mit dem eine oder mehrere `TagID`ist, wenn sie von Autoren oder Site-Besuchern auf Inhalte angewendet werden. Die Eigenschaft hat nur dann eine Bedeutung, wenn sie einem Knoten hinzugefügt wird, der mit dem Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) definiert wird.

>[!NOTE]
>
>Um die AEM-Tagging-Funktionalität zu nutzen, sollten benutzerdefinierte entwickelte Anwendungen keine anderen Tag-Eigenschaften als `cq:tags` definieren.

## Verschieben und Zusammenführen von Tags {#moving-and-merging-tags}

Im Folgenden finden Sie eine Beschreibung der Auswirkungen, die im Repository auftreten, wenn Sie Tags mit der [Tagging-Konsole](/help/sites-administering/tags.md) verschieben oder zusammenführen:

* Wenn ein Tag A verschoben oder mit Tag B unter `/content/cq:tags` zusammengeführt wird:

   * Tag A wird nicht gelöscht und erhält eine `cq:movedTo` -Eigenschaft.
   * Tag B wird erstellt (im Fall eines Verschiebevorgangs) und erhält eine `cq:backlinks` -Eigenschaft.

* `cq:movedTo` verweist auf Tag B.

   * Diese Eigenschaft bedeutet, dass Tag A in Tag B verschoben oder zusammengeführt wurde.
   * Durch Verschieben von Tag B wird diese Eigenschaft entsprechend aktualisiert. Tag A ist somit ausgeblendet und wird nur im Repository behalten, um Tag-IDs in Inhaltsknoten aufzulösen, die auf Tag A verweisen.
   * Der Garbage Collector für Tags entfernt Tags wie Tag A, sobald keine Inhaltsknoten mehr darauf verweisen.
   * Ein spezieller Wert für die Eigenschaft `cq:movedTo` ist `nirvana`: Er wird angewendet, wenn das Tag gelöscht wird, aber nicht aus dem Repository entfernt werden kann, weil untergeordnete Tags mit `cq:movedTo` vorhanden sind, die nicht entfernt werden dürfen.

      >[!NOTE]
      >
      >Die `cq:movedTo`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
      >
      >1. Das Tag wird im Inhalt verwendet (d. h. es wird darauf verwiesen).
      >1. Das Tag enthält bereits verschobene untergeordnete Elemente.


* `cq:backlinks` speichert Verweise in die andere Richtung, d. h. sie enthält eine Liste aller Tags, die verschoben oder mit Tag B zusammengeführt wurden.

   * Dies ist hauptsächlich erforderlich, um `cq:movedTo`-Eigenschaften auf dem aktuellen Stand zu halten, wenn Tag B auch verschoben/zusammengeführt/gelöscht oder aktiviert wird. In diesem Fall müssen all seine backlinks-Tags ebenso aktiviert werden.

>[!NOTE]
>
>Die `cq:backlinks`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
>
>1. Das Tag wird im Inhalt verwendet (d. h. es wird darauf verwiesen).
>1. Das Tag enthält bereits verschobene untergeordnete Elemente.


* Das Lesen einer `cq:tags`-Eigenschaft eines Inhaltsknotens umfasst die folgenden Auflösungen:

   1. Wenn unter `/content/cq:tags` keine Übereinstimmung verfügbar ist, wird kein Tag zurückgegeben.
   1. Wenn das Tag eine `cq:movedTo`-Eigenschaft aufweist, steht danach die referenzierte Tag-ID.

      * Dieser Schritt wird so lange wiederholt, wie das angehängte Tag eine `cq:movedTo`-Eigenschaft aufweist.
   1. Falls das angehängte Tag nicht über eine `cq:movedTo`-Eigenschaft verfügt, wird das Tag gelesen.


* Um eine Änderung zu veröffentlichen, wenn ein Tag verschoben oder zusammengeführt wurde, müssen der Knoten `cq:Tag` und all seine Backlinks repliziert werden.
   * Dies geschieht automatisch, wenn das Tag in der Tag-Verwaltungskonsole aktiviert wird.

* Spätere Aktualisierungen der `cq:tags`-Eigenschaft der Seite bereinigen automatisch die „alten“ Verweise.
   * Dies wird ausgelöst, da die Auflösung eines verschobenen Tags über die API das Ziel-Tag zurückgibt und so die Ziel-Tag-ID bereitstellt.

## Migration von Tags {#tags-migration}

Ab Adobe Experience Manager 6.4 werden Tags unter `/content/cq:tags`. In Fällen, in denen Adobe Experience Manager ein Upgrade von der vorherigen Version erhielt, sind die Tags jedoch immer noch unter dem alten Speicherort `/etc/tags` vorhanden. In aktualisierten Systemen müssen Tags in `/content/cq:tags`.

>[!NOTE]
>
>Auf der Seite Seiteneigenschaften der Tags wird empfohlen, Tag-ID zu verwenden (z. B. `geometrixx-outdoors:activity/biking`) anstatt den Tag-Basispfad fest zu kodieren (z. B. `/etc/tags/geometrixx-outdoors/activity/biking`).
>
>Zum Auflisten von Tags kann `com.day.cq.tagging.servlets.TagListServlet` verwendet werden.

>[!NOTE]
>
>Es wird empfohlen, die Tag-Manager-API als Ressource zu verwenden.

### Wenn die aktualisierte AEM-Instanz die TagManager-API unterstützt**

1. Zu Beginn der Komponente erkennt die TagManager-API, ob es sich um eine aktualisierte AEM handelt. In einem System mit Upgrade werden Tags unter `/etc/tags` gespeichert.

1. Die TagManager-API wird dann im Abwärtskompatibilitätsmodus ausgeführt, d. h. die API verwendet `/etc/tags` als Basispfad. Wenn nicht, wird ein neuer Speicherort `/content/cq:tags` verwendet.

1. Aktualisieren Sie den Tag-Speicherort.

1. Führen Sie nach der Migration von Tags an den neuen Speicherort das folgende Skript aus.

```java
import org.apache.sling.api.resource.*
import javax.jcr.*

ResourceResolverFactory resourceResolverFactory = osgi.getService(ResourceResolverFactory.class);
ResourceResolver resolver = resourceResolverFactory.getAdministrativeResourceResolver(null);
Session session = resolver.adaptTo(Session.class);

def queryManager = session.workspace.queryManager;
def statement = "/jcr:root/content/cq:tags//element(*, cq:Tag)[jcr:contains(@cq:movedTo,\'/etc/tags\') or jcr:contains(@cq:backlinks,\'/etc/tags\')]";
def query = queryManager.createQuery(statement, "xpath");

println "query = ${query.statement}\n";

def tags = query.execute().getNodes();


tags.each { node ->
        def tagPath = node.path;
        println "tag = ${tagPath}";

        if(node.hasProperty("cq:movedTo") && node.getProperty("cq:movedTo").getValue().toString().startsWith("/etc/tags")){

                def movedTo = node.getProperty("cq:movedTo").getValue().toString();

                println "cq:movedTo = ${movedTo} \n";

                movedTo = movedTo.replace("/etc/tags","/content/cq:tags");
                node.setProperty("cq:movedTo",movedTo);
        } else if(node.hasProperty("cq:backlinks")){

               String[] backLinks = node.getProperty("cq:backlinks").getValues();
               int count = 0;

               backLinks.each { value ->
                       if(value.startsWith("/etc/tags")){
                               println "cq:backlinks = ${value}\n";
                               backLinks[count] = value.replace("/etc/tags","/content/cq:tags");
    }
                       count++;
               }

               node.setProperty("cq:backlinks",backLinks);
  }
}
session.save();

println "---------------------------------Success-------------------------------------"
```

Das Skript ruft alle Tags ab, die `/etc/tags` im Wert der `cq:movedTo/cq:backLinks`-Eigenschaft haben. Anschließend wird der abgerufene Ergebnissatz schrittweise durchlaufen und die Eigenschaftswerte `cq:movedTo` und `cq:backlinks` werden in `/content/cq:tags` Pfade aufgelöst (in dem Fall, dass `/etc/tags` im Wert erkannt wird).

### Wenn die aktualisierte AEM auf der klassischen Benutzeroberfläche ausgeführt wird**

>[!NOTE]
>
>Die klassische Benutzeroberfläche ist nicht mit Ausfallzeiten kompatibel und unterstützt nicht den neuen Tag-Basispfad. Wenn Sie die klassische Benutzeroberfläche verwenden möchten, muss `/etc/tags` erstellt werden, gefolgt von einem Neustart der Komponente `cq-tagging`.

Falls die aktualisierten AEM-Instanzen von der TagManager-API unterstützt werden und in der klassischen Benutzeroberfläche ausgeführt werden:

1. Einmal verweist auf alten Tag-Basispfad `/etc/tags` werden durch TagId oder den neuen Tag-Speicherort ersetzt. `/content/cq:tags`, können Sie Tags an den neuen Speicherort migrieren `/content/cq:tags` in CRX DE gefolgt vom Komponenten-Neustart.

1. Nachdem Sie Tags an den neuen Speicherort migriert haben, führen Sie das oben genannte Skript aus.
