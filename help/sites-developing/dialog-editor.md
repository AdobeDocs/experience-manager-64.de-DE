---
title: Dialogfeldeditor
seo-title: Dialog Editor
description: Der Dialogfeldeditor bietet eine grafische Oberfläche zur einfachen Erstellung und Bearbeitung von Dialogfeldern und Strukturvorlagen.
seo-description: The dialog editor provides a graphical interface for easily creating and editing dialog boxes and scaffolds
uuid: 64d3fb12-8638-441b-8595-c590d48f3072
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: b7ac457d-3689-4f5d-9ceb-ff6a9944e7eb
exl-id: ee57a0c5-261e-4ffd-92ca-4804a9e1d132
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 39%

---

# Dialogfeldeditor{#dialog-editor}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der Dialogfeldeditor bietet eine grafische Oberfläche zur einfachen Erstellung und Bearbeitung von Dialogfeldern und Strukturvorlagen.

Sehen Sie sich die Funktionsweise genauer an, indem Sie CRXDE Lite aufrufen, in der Explorer-Struktur zu `/libs/foundation/components/chart` navigieren und auf den Knoten `dialog` doppelklicken:

![chlimage_1-247](assets/chlimage_1-247.png)

Der Dialogknoten wird anschließend im **Dialogfeldeditor** geöffnet:

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Übersicht über die Benutzeroberfläche {#user-interface-overview}

Die Benutzeroberfläche des Dialogfeldeditors besteht aus vier Bereichen:

* **Palette** links oben Dieser Bereich enthält die Widgets, die zum Erstellen eines Dialogfelds verfügbar sind, z. B. Registerkarten-Bedienfelder, Textfelder, Auswahllisten und Schaltflächen. Sie können die verschiedenen Kategorien in der Palette erweitern, indem Sie auf die gewünschte Trennleiste klicken.
* **Struktur** links unten Dieser Bereich zeigt die hierarchische Struktur von Knoten, aus denen die Dialogfelddefinition besteht. Sie können dieselbe Struktur sehen, indem Sie den Dialogfeldknoten in CRXDE Lite oder CRX Content Explorer erweitern.
* Der Fensterbereich **Rendern** befindet sich in der Mitte des Fensters. Dieser Bereich zeigt, wie die im Strukturbereich definierte Dialogfelddefinition als tatsächliches Dialogfeld dargestellt wird.
* Der Fensterbereich **Eigenschaften**. Dieser Bereich zeigt die Eigenschaften des Knotens an, der derzeit im Strukturbereich hervorgehoben ist.

### Verwenden des Dialogfeldeditors {#using-the-dialog-editor}

Um ein Dialogfeld zu erstellen, zieht der Benutzer Elemente aus der Palette in den Strukturbereich und legt sie innerhalb der Dialogfelddefinitionshierarchie an die gewünschte Position ab.

Sobald die gewünschte Struktur abgeschlossen ist, klickt der Benutzer auf **Speichern**, am oberen Rand des Renderbereichs.

>[!CAUTION]
>
>Beachten Sie, dass der Dialogfeldeditor für die Erstellung relativ einfache Dialogfelder vorgesehen ist und möglicherweise keine komplexeren Dialogfelddefinitionen bearbeiten kann. Wenn der Dialogfeldeditor die Bearbeitung einer Dialogfeldstruktur nicht zulässt, muss die Dialogfelddefinition manuell erstellt und/oder bearbeitet werden, indem die Knotenstruktur direkt bearbeitet wird, z. B. mit CRXDE Lite oder CRX Content Explorer.

### Erstellen eines neuen Dialogfelds {#creating-a-new-dialog}

Um ein neues Dialogfeld zu erstellen, müssen Sie die gewünschte Komponente auswählen. Klicken Sie auf **Erstellen...** und dann **Dialogfeld erstellen...**.

Geben Sie die erforderlichen Informationen ein und klicken Sie auf **Alle speichern**. Nun können Sie doppelt auf das Dialogfeld klicken, um es im Editor zu öffnen.

### Verwenden des Dialogfeldeditors für Strukturvorlagen {#using-the-dialog-editor-for-scaffolds}

Eine Strukturvorlage ist eine spezielle Seite mit einem Formular, das in einem Schritt ausgefüllt und gesendet werden kann. Auf diese Weise können Sie schnell eine Seite mit dem eingegebenen Inhalt erstellen.

Das Formular, aus dem eine Strukturvorlage besteht, wird durch eine Dialogfelddefinition definiert, im Grunde wie ein normales Dialogfeld, mit dem Unterschied, dass es auf der Strukturvorlagenseite in einer anderen Form erscheint. Da Dialogfelddefinitionen zum Definieren von Strukturvorlagen verwendet werden, können Sie Strukturvorlagen mit dem Dialogfeldeditor entwerfen. Beachten Sie, dass bei der Verwendung des Dialogfeldeditors auf diese Weise im Renderbereich die Dialogfelddefinition weiterhin in Form eines Dialogfelds und nicht als Grundlage angezeigt wird.

Weitere Informationen zum Erstellen von Strukturvorlagen mithilfe des Dialogfeldeditors finden Sie in [Strukturvorlagen](/help/sites-authoring/scaffolding.md).
