---
title: Anmerkungen beim Bearbeiten einer Seite
seo-title: Annotations when Editing a Page
description: Oft muss das Hinzufügen von Inhalten zu den Seiten Ihrer Website vor der tatsächlichen Veröffentlichung besprochen werden. Um dies zu unterstützen, können Sie mit vielen Komponenten, die sich direkt auf Inhalte beziehen, Anmerkungen hinzufügen.
seo-description: Adding content to the pages of your website is often subject to discussions prior to it actually being published. To aid this, many components directly related to content allow you to add an annotation.
page-status-flag: de-activated
uuid: d8d6ba76-f2aa-4044-98bf-5d506742d90d
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 9bee0197-f275-49cc-922d-62cba826c4e5
exl-id: 76e36d3b-4a8a-45ee-bb4e-28b150ec089c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 43%

---

# Anmerkungen beim Bearbeiten einer Seite{#annotations-when-editing-a-page}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Oft muss das Hinzufügen von Inhalten zu den Seiten Ihrer Website vor der tatsächlichen Veröffentlichung besprochen werden. Um dies zu unterstützen, können Sie mit vielen Komponenten, die sich direkt auf Inhalte beziehen (im Gegensatz zum Layout), Anmerkungen hinzufügen.

Bei einer Anmerkung wird eine farbige Markierung/Haftnotiz auf der Seite platziert. Mit einer Anmerkung können Sie (oder andere Benutzer) Kommentare und/oder Fragen für andere Autoren/Prüfer hinterlassen.

>[!NOTE]
>
>Die Definition einer einzelnen Komponente bestimmt, ob Anmerkungen in Instanzen dieser Komponente möglich sind oder nicht.

>[!NOTE]
>
>In der klassischen Benutzeroberfläche erstellte Anmerkungen werden auch in der Touch-optimierten Benutzeroberfläche angezeigt. Zeichnungen sind jedoch benutzeroberflächenspezifisch und werden nur in der Benutzeroberfläche angezeigt, in der sie erstellt wurden.

>[!CAUTION]
>
>Durch Löschen einer Ressource (z. B. eines Absatzes) werden alle Anmerkungen und Zeichnungen gelöscht, die mit dieser Ressource verbunden sind (unabhängig von ihrer Position auf der Seite als Ganzes).

>[!NOTE]
>
>Je nach Ihren Anforderungen können Sie auch einen Workflow erstellen, damit Benachrichtigungen gesendet werden, wenn Anmerkungen hinzugefügt, aktualisiert oder gelöscht werden.

## Anmerkungen {#annotations}

Je nach Absatzdesign sind Anmerkungen entweder als Option im Kontextmenü (in der Regel über die rechte Maustaste, wenn sich der Absatz über dem gewünschten Absatz befindet) oder als Schaltfläche in der Absatzbearbeitungsleiste verfügbar.

Wählen Sie in beiden Fällen **Anmerken** aus. Auf den Absatz wird eine farbige Kurznotiz angewendet. Sie befinden sich unmittelbar im Bearbeitungsmodus und können Text direkt hinzufügen:

![chlimage_1-137](assets/chlimage_1-137.png)

Sie können die Anmerkung an eine neue Position auf der Seite verschieben. Klicken Sie auf den oberen Rahmenbereich, halten Sie die Maustaste gedrückt und ziehen Sie gleichzeitig die Anmerkung an die neue Position. Dies kann sich an einer beliebigen Stelle auf der Seite befinden, es ist jedoch in der Regel sinnvoll, sie in irgendeiner Weise mit dem Absatz zu verbinden.

Anmerkungen (einschließlich zugehöriger Zeichnungen) sind auch in allen Kopier-, Ausschneide- oder Löschaktionen enthalten, die für den Absatz durchgeführt werden, dem sie zugeordnet sind. Bei Kopier- oder Ausschneideaktionen behält die Position der Anmerkung (und der zugehörigen Zeichnungen) ihre Position in Bezug auf den ursprünglichen Absatz bei.

Die Anmerkung kann auch durch Ziehen der Anmerkung in der unteren rechten Ecke vergrößert oder verkleinert werden.

Aus Gründen der Nachverfolgung werden in der Fußzeile der Benutzer, der die Anmerkung erstellt hat, sowie das Datum angegeben. Nachfolgende Autoren können dieselbe Anmerkung bearbeiten (die Fußzeile wird aktualisiert) oder eine neue Anmerkung für denselben Absatz erstellen.

Wenn Sie die Anmerkung löschen möchten, wird eine Bestätigung angefordert (beim Löschen einer Anmerkung werden auch alle mit dieser Anmerkung verknüpften Zeichnungen gelöscht).

Über die drei Symbole oben links können Sie die Anmerkung (zusammen mit allen damit verbundenen Zeichnungen) minimieren, die Farbe ändern und Zeichnungen hinzufügen.

>[!NOTE]
>
>Anmerkungen sind nur im Bearbeitungsmodus der Autorenumgebung sichtbar. 
>
>In einer Veröffentlichungsumgebung oder im Vorschau- oder Designmodus einer Autorenumgebung sind sie nicht sichtbar.

>[!NOTE]
>
>Anmerkungen können nicht zu einer Seite hinzugefügt werden, die von einem anderen Benutzer gesperrt wurde.


## Anmerkungszeichnungen {#annotation-sketches}

>[!NOTE]
>
>Zeichnungen sind in Internet Explorer nicht verfügbar, daher:
>
>* wird das Symbol nicht angezeigt.
>* vorhandene Zeichnungen, die in einem anderen Browser erstellt wurden, werden nicht angezeigt.
>


Zeichnungen sind eine Funktion von Anmerkungen, mit denen Sie einfache Liniengrafiken an einer beliebigen Stelle im Browser-Fenster (sichtbarer Teil) erstellen können:

![chlimage_1-138](assets/chlimage_1-138.png)

* Wenn Sie sich im Zeichenmodus befinden, wird der Cursor in ein Kreuz geändert. Sie können mehrere separate Linien zeichnen.
* Die Zeichnungslinie spiegelt die Anmerkungsfarbe wider und kann entweder:

   * Freehand

      den Standardmodus; Schließen Sie, indem Sie die Maustaste loslassen.

   * gerade:

      Halten Sie die `ALT`-Taste gedrückt, und klicken Sie auf die Start- und Endpunkte; schließen Sie den Vorgang mit einem Doppelklick ab.

* Nachdem Sie den Zeichenmodus beendet haben, können Sie auf eine Zeichnung klicken, um diese Zeichnung auszuwählen.
* Verschieben Sie eine Zeichnung, indem Sie die Zeichnung auswählen und sie dann an die gewünschte Position ziehen.
* Eine Zeichnung überlagert den Inhalt. Dies bedeutet, dass sie innerhalb der vier Ecken der Zeichnung nicht auf den darunter liegenden Absatz klicken können, wenn Sie beispielsweise einen Link bearbeiten oder darauf zugreifen möchten. Wenn dies zu einem Problem wird (z. B. wenn eine Zeichnung einen großen Bereich der Seite umfasst), minimieren Sie die entsprechende Anmerkung, da dadurch auch alle zugehörigen Zeichnungen minimiert werden, sodass Sie Zugriff auf den zugrunde liegenden Bereich erhalten.
* So löschen Sie eine einzelne Zeichnung: Wählen Sie die gewünschte Zeichnung aus und drücken Sie dann die **Löschen** key (**fn**-**backspace** auf einer MAC).

* Wenn Sie einen Absatz verschieben oder kopieren, werden auch alle zugehörigen Anmerkungen und deren Zeichnungen verschoben oder kopiert. ihre Position in Bezug auf den Absatz bleibt unverändert.
* Wenn Sie eine Anmerkung löschen, werden auch alle Zeichnungen gelöscht, die mit dieser Anmerkung verbunden sind.
