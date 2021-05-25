---
title: Das Seiten-Exporttool
seo-title: Das Seiten-Exporttool
description: Erfahren Sie, wie Sie das AEM-Seiten-Exporttool verwenden.
seo-description: Erfahren Sie, wie Sie das AEM-Seiten-Exporttool verwenden.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
exl-id: a5cb3b7b-d40f-4d86-8473-fb584f1d486c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 63%

---

# Das Seiten-Exporttool{#the-page-exporter}

AEM bietet Ihnen die Möglichkeit, eine Seite als vollständige Webseite einschließlich aller Grafiken, JS- und CSS-Dateien zu exportieren.

Wenn Sie den Export konfiguriert haben, können Sie einfach eine Seite im Browser anfordern. Ersetzen Sie dafür in der URL `html` durch `export.zip`. So erzeugen Sie den Download einer ZIP-Datei, in der die gerenderte Seite im HTML-Format und die referenzierten Assets enthalten sind. Alle in der Seite enthaltenen Pfade, z. B. Pfade zu Grafiken, werden umgeschrieben und verweisen entweder auf die in der ZIP-Datei enthaltenen Dateien oder auf die Ressourcen auf dem Server.

## Exportieren einer Seite {#exporting-a-page}

Die folgenden Schritte beschreiben, wie Sie eine Seite exportieren können. Vorausgesetzt wird, dass für Ihre Website eine Vorlage für die Exportkonfiguration vorliegt: Eine Konfigurationsvorlage legt fest, wie eine Seite exportiert wird, und gilt speziell für Ihre Website. Informationen zum Erstellen einer Konfigurationsvorlage finden Sie im Abschnitt [Erstellen einer Page Exporter-Konfiguration für Ihre Site](#creating-a-page-exporter-configuration-for-your-site) .

So exportieren Sie eine Seite:

1. Öffnen Sie die Seite im Browser. Beispiel:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Öffnen Sie das Dialogfeld „Seiteneigenschaften“, wählen Sie die Registerkarte **Erweitert** und erweitern Sie das Feld **Exportieren**.

1. Klicken Sie auf das Lupensymbol und wählen Sie eine Konfigurationsvorlage aus. Wählen Sie die **geometrixx**-Vorlage aus; sie ist die standardmäßige Vorlage für die Geometrixx-Website. Klicken Sie auf **OK**.

1. Klicken Sie auf **OK**, um das Dialogfeld „Seiteneigenschaften“ zu schließen.
1. Fordern Sie die Seite an, indem Sie `html` in der URL durch `export.zip` ersetzen.

1. Laden Sie die Datei `<page-name>.export.zip` in Ihr Dateisystem herunter.

1. Entpacken Sie in Ihrem Dateisystem die Datei:

   * Die HTML-Datei der Seite ( `<page-name>.html`) ist unter `<unzip-dir>/<page-path>` verfügbar.
   * Die anderen Ressourcen (JS- und CSS-Dateien, Grafiken usw.) befinden sich in den in der Exportvorlage festgelegten Verzeichnissen. In diesem Beispiel befinden sich einige Ressourcen unter `<unzip-dir>/etc`, einige unter `<unzip-dir>/<page-path>`.

1. Öffnen Sie die HTML-Datei der Seite ( `<unzip-dir>/<page-path>.html`) in Ihrem Browser, um das Rendering zu überprüfen.

## Erstellen einer Seiten-Exporttoolkonfiguration für Ihre Website {#creating-a-page-exporter-configuration-for-your-site}

Das Seiten-Exporttool basiert auf dem Inhaltssynchronisierungs-Framework. Die Konfigurationen, die im Dialogfeld &quot;Seiteneigenschaften&quot;verfügbar sind, sind Konfigurationsvorlagen. Sie definieren alle erforderlichen Abhängigkeiten einer Seite. Wenn ein Seitenexport ausgelöst wird, wird die Konfigurationsvorlage verwendet und sowohl der Seitenpfad als auch der Designpfad werden dynamisch auf die Konfiguration angewendet. Anschließend wird die ZIP-Datei erstellt, indem die Standardfunktion zur Inhaltssynchronisierung genutzt wird.

AEM bettet einige Vorlagen ein, darunter eine:

* Eine Standardeinstellung unter `/etc/contentsync/templates/default`. Diese Vorlage:

   * Dient als Fallback-Vorlage, wenn keine Konfigurationsvorlage im Repository gefunden wird
   * Kann als Grundlage für eine neue Konfigurationsvorlage dienen.

* Eine für die Site **Geometrixx** unter `/etc/contentsync/templates/geometrixx` reservierte Seite. Diese Vorlage kann als Beispiel verwendet werden, um eine neue zu erstellen.

So erstellen Sie eine Konfigurationsvorlage für das Seiten-Exporttool:

1. Erstellen Sie in **CRXDE Lite** einen Knoten unter `/etc/contentsync/templates`:

   * Name: z. B. `mysite`. Der Name wird im Dialogfeld &quot;Seiteneigenschaften&quot;angezeigt, wenn Sie die Vorlage &quot;Seitenexporteur&quot;auswählen.
   * Typ: `nt:unstructured`

1. Erstellen Sie unter dem Vorlagenknoten (in diesem Beispiel: `mysite`) eine Knotenstruktur mit den unten beschriebenen Konfigurationsknoten.

### Konfigurationsknoten für das Seiten-Exporttool {#page-exporter-configuration-nodes}

Die Konfigurationsvorlage besteht aus einer Knotenstruktur. Jeder Knoten verfügt über die Eigenschaft `type`, die eine spezifische Aktion beim Erstellungsprozess der ZIP-Datei definiert. Weitere Informationen zur type-Eigenschaft finden Sie im Abschnitt Übersicht über Konfigurationstypen auf der Framework-Seite zur Inhaltssynchronisierung .

Mit den folgenden Knoten können Sie eine Export-Konfigurationsvorlage erstellen:

**page** nodeDer Seitenknoten wird zum Kopieren des Seiten-HTML-Codes in die ZIP-Datei verwendet. Er weist die folgenden Eigenschaften auf:

* Er ist ein obligatorischer Knoten.
* Befindet sich unter `/etc/contentsync/templates/<sitename>`.
* Sein Name ist `page`.
* Sein Knotentyp ist `nt:unstructured`

Der Knoten `page` hat folgende Eigenschaften:

* Eine `type` -Eigenschaft mit dem Wert `pages`.

* Er verfügt nicht über die Eigenschaft `path`, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.

* Die anderen Eigenschaften werden im Abschnitt Übersicht der Konfigurationstypen des Content Sync-Frameworks beschrieben.

**rewrite-** Knoten Der rewrite-Knoten definiert, wie die Links auf der exportierten Seite neu geschrieben werden. Die neu geschriebenen Links können entweder auf die Dateien in der ZIP-Datei oder auf die Ressourcen auf dem Server verweisen.

Auf der Seite Inhaltssynchronisierung finden Sie eine vollständige Beschreibung des Knotens `rewrite`.

**design** nodeDer Designknoten wird zum Kopieren des für die exportierte Seite verwendeten Designs verwendet. Er weist die folgenden Eigenschaften auf:

* Er ist optional.
* Befindet sich unter `/etc/contentsync/templates/<sitename>`.
* Sein Name ist `design`.
* Sein Knotentyp ist `nt:unstructured`.

Der Knoten `design` hat folgende Eigenschaften:

* Eine `type` -Eigenschaft, die auf den Wert `copy` gesetzt ist.

* Er verfügt nicht über die Eigenschaft `path`, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.

**generic** nodeEin generischer Knoten wird verwendet, um Ressourcen wie clientlibs .js - oder .css -Dateien in die ZIP-Datei zu kopieren. Er weist die folgenden Eigenschaften auf:

* Er ist optional.
* Befindet sich unter `/etc/contentsync/templates/<sitename>`.
* Er weist keinen bestimmten Namen auf.
* Sein Knotentyp ist `nt:unstructured`.
* Hat eine `type`-Eigenschaft und alle `type` zugehörigen Eigenschaften, wie im Abschnitt Übersicht über Konfigurationstypen des Framework zur Inhaltssynchronisierung definiert.

Beispielsweise kopiert der folgende Konfigurationsknoten die JS-Dateien der Geometrixx-Clientlibs in die ZIP-Datei:

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

Die **Geometrixx**-Konfigurationsvorlage für das Seiten-Exporttool zeigt, wie Sie einen Seitenexport konfigurieren können. Um die Knotenstruktur der Vorlage in Ihrem Browser im JSON-Format anzuzeigen, fordern Sie die folgenden URL an:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Implementieren einer benutzerdefinierten Konfiguration**

Wie Sie vielleicht bei der Knotenstruktur bemerkt haben, verfügt die **Geometrixx**-Konfigurationsvorlage für das Seiten-Exporttool über den Knoten `logo`, bei dem die Eigenschaft `type`auf `image` festgelegt ist. Das ist ein spezieller Konfigurationstyp, der erstellt wurde, um das Grafiklogo in die ZIP-Datei zu kopieren. Um bestimmte Anforderungen zu erfüllen, müssen Sie möglicherweise eine benutzerdefinierte Eigenschaft `type` implementieren. Informationen hierzu finden Sie im Abschnitt Implementieren eines benutzerdefinierten Aktualisierungshandlers auf der Seite „Inhaltssynchronisierung“.

## Programmatisches Exportieren einer Seite {#programmatically-exporting-a-page}

Um eine Seite programmatisch zu exportieren, können Sie den OSGi-Dienst [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) nutzen. Mit diesem Dienst können Sie:

* eine Seite exportieren und in die HTTP-Servlet-Antwort schreiben
* eine Seite exportieren und die ZIP-Datei an einem bestimmten Ort speichern

Das Servlet, das an den Selektor `export` und die Erweiterung `zip` gebunden ist, verwendet den PageExporter-Dienst.

## Fehlerbehebung {#troubleshooting}

Wenn beim Herunterladen der ZIP-Datei ein Problem auftritt, können Sie den Knoten `/var/contentsync` im Repository löschen und die Exportanfrage erneut senden.
