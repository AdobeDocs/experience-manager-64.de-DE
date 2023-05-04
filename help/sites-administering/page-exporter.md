---
title: Das Seiten-Export-Tool
seo-title: The Page Exporter
description: Erfahren Sie, wie Sie den AEM Page Exporter verwenden.
seo-description: Learn how to use the AEM Page Exporter.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
exl-id: a5cb3b7b-d40f-4d86-8473-fb584f1d486c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 28%

---

# Das Seiten-Export-Tool{#the-page-exporter}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM ermöglicht den Export einer Seite als vollständige Webseite mit Bildern, JS- und CSS-Dateien.

Nach der Konfiguration des Exports fordern Sie einfach eine Seite in Ihrem Browser an, indem Sie `html` mit `export.zip` in der URL ein und Sie erhalten einen ZIP-Datei-Download, der die wiedergegebene Seite im HTML-Format und die referenzierten Assets enthält. Alle Pfade auf der Seite, z. B. Pfade zu Bildern, werden umgeschrieben, um entweder auf die in der ZIP-Datei enthaltenen Dateien oder auf die Ressourcen auf dem Server zu verweisen.

## Exportieren einer Seite {#exporting-a-page}

In den folgenden Schritten wird beschrieben, wie Sie eine Seite exportieren und davon ausgehen, dass für Ihre Site eine Exportkonfigurationsvorlage vorhanden ist. Eine Konfigurationsvorlage definiert, wie eine Seite exportiert wird, und ist spezifisch für Ihre Site. Informationen zum Erstellen einer Konfigurationsvorlage finden Sie im Abschnitt [Erstellen einer Seiten-Exporter-Konfiguration für Ihre Site](#creating-a-page-exporter-configuration-for-your-site) Abschnitt.

So exportieren Sie eine Seite:

1. Öffnen Sie die Seite in Ihrem Browser. Beispiel:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Öffnen Sie das Dialogfeld &quot;Seiteneigenschaften&quot;, wählen Sie die **Erweitert** und erweitern Sie die **Export** Feldersatz.

1. Klicken Sie auf das Lupensymbol und wählen Sie eine Konfigurationsvorlage aus. Wählen Sie die **geometrixx** -Vorlage, da dies die Standardvorlage für die Geometrixx-Site ist. Klicken Sie auf **OK**.

1. Klicken **OK** , um das Dialogfeld &quot;Seiteneigenschaften&quot;zu schließen.
1. Anfordern der Seite durch Ersetzen `html` mit `export.zip` in der URL.

1. Laden Sie die `<page-name>.export.zip` in Ihr Dateisystem.

1. Dekomprimieren Sie die Datei in Ihrem Dateisystem:

   * die HTML-Datei der Seite ( `<page-name>.html`) ist unten verfügbar `<unzip-dir>/<page-path>`
   * Andere Ressourcen (.js-Dateien, .css-Dateien, Bilder usw.) befinden sich gemäß den Einstellungen in der Exportvorlage. In diesem Beispiel finden Sie einige Ressourcen unter `<unzip-dir>/etc`, einige unten `<unzip-dir>/<page-path>`.

1. Öffnen Sie die HTML-Datei der Seite (`<unzip-dir>/<page-path>.html`) im Browser, um das Rendering zu überprüfen.

## Erstellen einer Seiten-Export-Tool-Konfiguration für Ihre Website {#creating-a-page-exporter-configuration-for-your-site}

Das Seiten-Export-Tool basiert auf dem Inhaltssynchronisierungs-Framework. Die Konfigurationen, die im Dialogfeld &quot;Seiteneigenschaften&quot;verfügbar sind, sind Konfigurationsvorlagen. Sie definieren alle erforderlichen Abhängigkeiten für eine Seite. Wenn ein Seitenexport ausgelöst wird, wird die Konfigurationsvorlage verwendet und sowohl der Seitenpfad als auch der Designpfad werden dynamisch auf die Konfiguration angewendet. Anschließend wird die ZIP-Datei erstellt, indem die Standardfunktion zur Inhaltssynchronisierung genutzt wird.

AEM bettet einige Vorlagen ein, darunter:

* Eine Standardeinstellung unter `/etc/contentsync/templates/default`. Diese Vorlage:

   * ist die Fallback-Vorlage, wenn keine Konfigurationsvorlage im Repository gefunden wird.
   * Kann als Grundlage für eine neue Konfigurationsvorlage dienen.

* Eine für die **Geometrixx** Site, `/etc/contentsync/templates/geometrixx`. Diese Vorlage kann als Beispiel für die Erstellung einer neuen Vorlage verwendet werden.

So erstellen Sie eine Konfigurationsvorlage für den Seitenexporteur:

1. Erstellen Sie in **CRXDE Lite** einen Knoten unter `/etc/contentsync/templates`:

   * Name: z. B. `mysite`. Dieser Name wird im Dialogfeld „Seiteneigenschaften“ angezeigt, wenn Sie die Seiten-Export-Toolvorlage auswählen.
   * Typ: `nt:unstructured`

1. Erstellen Sie unter dem Vorlagenknoten (in diesem Beispiel: `mysite`) eine Knotenstruktur mit den unten beschriebenen Konfigurationsknoten.

### Konfigurationsknoten für das Seiten-Export-Tool {#page-exporter-configuration-nodes}

Die Konfigurationsvorlage besteht aus einer Knotenstruktur. Jeder Knoten verfügt über die Eigenschaft `type`, die eine spezifische Aktion beim Erstellungsprozess der ZIP-Datei definiert. Weitere Informationen zur type-Eigenschaft finden Sie im Abschnitt Übersicht über Konfigurationstypen auf der Framework-Seite zur Inhaltssynchronisierung .

Die folgenden Knoten können zum Erstellen einer Exportkonfigurationsvorlage verwendet werden:

**Seitenknoten** Der Seitenknoten wird zum Kopieren des Seiten-HTML-Codes in die ZIP-Datei verwendet. Er weist die folgenden Eigenschaften auf:

* Ist ein obligatorischer Knoten.
* Er befindet sich unterhalb von `/etc/contentsync/templates/<sitename>`.
* Der Name lautet `page`.
* Sein Knotentyp ist `nt:unstructured`

Der Knoten `page` hat folgende Eigenschaften:

* Die Eigenschaft `type` mit dem Wert `pages`.

* Er verfügt nicht über die Eigenschaft `path`, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.

* Die anderen Eigenschaften werden im Abschnitt Übersicht der Konfigurationstypen des Content Sync-Frameworks beschrieben.

**rewrite-Knoten** Der Knoten rewrite definiert, wie die Links auf der exportierten Seite neu geschrieben werden. Die neu geschriebenen Links können entweder auf die Dateien in der ZIP-Datei oder auf die Ressourcen auf dem Server verweisen.

Eine vollständige Beschreibung der `rewrite` Knoten.

**design node** Der Knoten &quot;design&quot;wird zum Kopieren des für die exportierte Seite verwendeten Designs verwendet. Er weist die folgenden Eigenschaften auf:

* Er ist optional.
* Er befindet sich unterhalb von `/etc/contentsync/templates/<sitename>`.
* Der Name lautet `design`.
* Sein Knotentyp ist `nt:unstructured`.

Der Knoten `design` hat folgende Eigenschaften:

* Die Eigenschaft `type` mit dem Wert `copy`.

* Er verfügt nicht über die Eigenschaft `path`, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.

**generic Knoten** Ein generischer Knoten wird verwendet, um Ressourcen wie .js- oder .css-Dateien clientlibs in die ZIP-Datei zu kopieren. Er weist die folgenden Eigenschaften auf:

* Er ist optional.
* Er befindet sich unterhalb von `/etc/contentsync/templates/<sitename>`.
* Er weist keinen bestimmten Namen auf.
* Sein Knotentyp ist `nt:unstructured`.
* Hat eine `type` -Eigenschaft und `type` verwandte Eigenschaften, wie im Abschnitt Übersicht über Konfigurationstypen des Content Sync-Frameworks definiert.

Beispielsweise kopiert der folgende Konfigurationsknoten die Dateien &quot;geometrixx clientlibs .js&quot;in die ZIP-Datei:

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

Die **Geometrixx** Die Konfigurationsvorlage für den Seitenexport zeigt Ihnen, wie ein Seitenexport konfiguriert werden kann. Um die Knotenstruktur der Vorlage in Ihrem Browser als JSON-Format anzuzeigen, fordern Sie die folgende URL an:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Implementieren einer benutzerdefinierten Konfiguration**

Wie Sie möglicherweise in der Knotenstruktur bemerkt haben, wird die **Geometrixx** Die Konfigurationsvorlage für den Seitenexport verfügt über eine `logo` Knoten mit `type` Eigenschaft auf `image`. Dies ist ein spezieller Konfigurationstyp, der erstellt wurde, um das Bildlogo in die ZIP-Datei zu kopieren. Um bestimmte Anforderungen zu erfüllen, müssen Sie möglicherweise einen benutzerdefinierten `type` Eigenschaft: Lesen Sie dazu den Abschnitt Implementieren eines benutzerdefinierten Update-Handlers auf der Seite Inhaltssynchronisierung .

## Programmgesteuertes Exportieren einer Seite {#programmatically-exporting-a-page}

Um eine Seite programmgesteuert zu exportieren, können Sie die [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGi-Dienst. Mit diesem Dienst können Sie:

* Exportieren Sie eine Seite und schreiben Sie in die HTTP-Servlet-Antwort.
* Exportieren Sie eine Seite und speichern Sie die ZIP-Datei an einem bestimmten Speicherort.

Das Servlet, das an den Selektor `export` und die Erweiterung `zip` gebunden ist, nutzt den PageExporter-Service.

## Fehlerbehebung {#troubleshooting}

Wenn beim Herunterladen der ZIP-Datei ein Fehler auftritt, können Sie den Knoten `/var/contentsync` im Repository löschen und die Exportanfrage erneut senden.
