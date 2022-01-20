---
title: 'Verbessern der Performance umfangreicher Formulare durch verzögertes Laden '
seo-title: Improve performance of large forms with lazy loading
description: Verzögertes Laden verbessert die Leistung von großen und komplexen adaptiven Formularen erheblich, weil Formularfragmente erst initialisiert und geladen werden, wenn sie sichtbar sind.
seo-description: Lazy loading significantly improves the performance of large and complex adaptive forms by deferring initialization and loading of form fragments until they are visible.
uuid: 3ead2b82-f895-4a7b-9683-495fcd94fade
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: d570ead9-8f9c-4668-8b23-e8984d9b25e9
feature: Adaptive Forms
exl-id: 92d88888-343c-4edb-9b11-8e876539573a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 95%

---

# Verbessern der Performance umfangreicher Formulare durch verzögertes Laden  {#improve-performance-of-large-forms-with-lazy-loading}

## Einführung in das verzögerte Laden {#introduction-to-lazy-loading}

Wenn Formulare infolge von Hunderten oder Tausenden von Feldern groß und komplex werden, bemerken die Endbenutzer während des Renderns von Formularen zur Laufzeit lange Reaktionszeiten. Um die Reaktionszeiten zu minimieren, können Sie adaptive Formulare in logische Fragmente unterteilen und konfigurieren, dass die Initialisierung oder das Laden von Fragmenten aufgeschoben wird, bis das Fragment sichtbar sein soll. Dies wird als „verzögertes Laden“ bezeichnet. Darüber hinaus werden die für verzögertes Laden konfigurierten Fragmente entladen, sobald der Benutzer zu anderen Abschnitten im Formular navigiert und die Fragmente nicht mehr sichtbar sind.

Im Folgenden werden zunächst die Anforderungen und vorbereitenden Schritte vor dem Konfigurieren des verzögerten Ladens erklärt.

## Vorbereiten der Konfiguration von verzögertem Laden {#preparing-to-configure-lazy-loading}

Bevor Sie verzögertes Laden von Fragmenten in Ihrem adaptiven Formular konfigurieren, müssen Sie Strategien entwickeln für das Erstellen von Fragmenten, Identifizieren von Werten, die in den Skripten verwendet oder in andere Fragment referenziert werden, und Definieren von Regeln, die die Sichtbarkeit von Feldern in verzögert geladenen Fragmenten steuern.

* **Fragmente identifizieren und erstellen**
Sie können nur adaptive Formularfragmente für verzögertes Laden konfigurieren. Ein Fragment ist ein eigenständiges Segment, das sich außerhalb eines adaptiven Formulars befindet und über mehrere Formulare hinweg wiederverwendet werden kann. Somit besteht der erste Schritt beim Implementieren des verzögerten Ladens in der Bestimmung der logischen Abschnitte in einem Formular und deren Konvertierung in Fragmente. Sie können ein Fragment von Grund auf neu erstellen oder einen vorhandenen Formularbereich als Fragment speichern.

    Weitere Informationen zum Erstellen von Fragmenten finden Sie unter [Adaptive Formularfragmente](/help/forms/using/adaptive-form-fragments.md).

* **Identifizieren und Markieren globaler Werte**
Zu formularbasierten Transaktionen gehören dynamische Elemente, die relevante Daten von Benutzern erfassen und verarbeiten und dadurch das Ausfüllen des Formulars vereinfachen. Beispiel: Ihr Formular enthält Feld A in Fragment X, dessen Wert die Gültigkeit von Feld B in einem anderen Fragment bestimmt. Wenn in diesem Fall Fragment X für verzögertes Laden markiert ist, muss der Wert von Feld A verfügbar sein, um Feld B zu validieren, selbst wenn Fragment X nicht geladen wird. Um dies zu erreichen, können Sie Feld A als „global“ markieren, wodurch gewährleistet wird, dass der entsprechende Wert für die Validierung von Feld B verfügbar ist, wenn Fragment X nicht geladen wird.

   Weitere Informationen dazu, wie Sie einen Feldwert als „global“ kennzeichnen, finden Sie unter [Konfigurieren von verzögertem Laden](/help/forms/using/lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Erstellen von Regeln zur Steuerung der Sichtbarkeit von Feldern**
Formulare enthalten Felder und Abschnitte, die nicht für alle Benutzer und Bedingungen gelten. Formularersteller und Entwickler verwenden Regeln für Sichtbarkeit oder Einblenden/Ausblenden, um die Sichtbarkeit je nach Benutzereingabe zu steuern. Beispielsweise wird das Feld „Firmenanschrift“ Benutzern, die im Feld „Beschäftigungsstatus“ „Erwerbslos“ ausgewählt haben, nicht angezeigt. Weitere Informationen zum Erstellen von Regeln finden Sie unter [Verwenden des Regeleditors](/help/forms/using/rule-editor.md).

   Sie können Sichtbarkeitsregeln in verzögert geladenen Fragmenten so einsetzen, dass bedingte Felder nur angezeigt werden, wenn sie benötigt werden. Markieren Sie außerdem das bedingte Feld als „global“, um im Ausdruck für die Sichtbarkeit des verzögert geladenen Fragments darauf zu verweisen.

## Konfigurieren von verzögertem Laden {#configuring-lazy-loading}

Führen Sie zum Aktivieren des verzögerten Ladens in einem adaptiven Formularfragment folgende Schritte durch:

1. Öffnen Sie im Bearbeitungsmodus das adaptive Formular, das das Fragment enthält, für das Sie verzögertes Laden aktivieren möchten.
1. Wählen Sie das adaptive Formularfragment aus und tippen Sie auf ![cmppr](assets/cmppr.png).
1. Aktivieren Sie in der Randleiste **[!UICONTROL Laden des Fragments träge]** und tippen Sie auf **Fertig**.

   ![Verzögertes Laden für das adaptive Formularfragment aktivieren](assets/lazy-loading-fragment.png)

   Das Fragment ist jetzt für verzögertes Laden aktiviert.

Sie können die Werte von Objekten im verzögert geladenen Fragment als „global“ markieren, sodass sie für die Verwendung in Skripten verfügbar sind, selbst wenn das enthaltende Fragment nicht geladen wird. Gehen Sie folgendermaßen vor:

1. Öffnen Sie das adaptive Formularfragment im Bearbeitungsmodus.
1. Tippen Sie auf das Feld, dessen Wert Sie als „global“ markieren möchten, und tippen Sie dann auf ![](assets/cmppr.png).
1. Aktivieren Sie in der Randleiste **[!UICONTROL Wert bei verzögertem Laden verwenden]**.
   ![Feld „Verzögertes Laden“ in der Randleiste](assets/enable-lazy-loading.png)

   Der Wert ist jetzt als „global“ markiert und ist für die Verwendung in Skripten verfügbar, selbst wenn das enthaltene Fragment entladen wird.

## Aspekte und empfohlene Vorgehensweisen beim Konfigurieren von verzögertem Laden {#considerations-and-best-practices-for-configuring-lazy-loading}

Einige der folgenden Einschränkungen, Empfehlungen und wichtigen Aspekte sind beim Arbeiten mit verzögertem Laden zu beachten:

* Es wird empfohlen, XSD-schemabasierte statt XFA-basierte adaptive Formulare für die Konfiguration von verzögertem Laden bei großen Formularen zu verwenden. Die Leistungsverbesserung aufgrund von verzögertem Laden ist in XFA-basierten adaptiven Formularen verhältnismäßiger geringer als in XSD-basierten adaptiven Formularen.
* Konfigurieren Sie kein verzögertes Laden in Fragmenten in einem bedarfsgesteuerten Rasterlayout. Dies kann zu einer beeinträchtigten Leistung führen.
* Es wird empfohlen, verzögertes Laden nicht in Fragmenten im ersten Bereich zu konfigurieren, das beim Laden des adaptiven Formulars angezeigt wird.
* Verzögertes Laden wird für bis zu zwei Ebenen in der Fragmenthierarchie unterstützt.
* Vergewissern Sie sich, dass als „global“ markierte Felder im gesamten adaptiven Formular eindeutig sind.
* Erwägen Sie, Sichtbarkeitsregeln für Fragmente zu erstellen, die basierend auf einer Bedingung ein- bzw. ausgeblendet werden sollen. Beispielsweise können Sie je nach dem vom Benutzer angegebenen Familienstand das Fragment zum Ehepartner ein- oder ausblenden.
* In verzögert geladenen Fragmenten werden keine Komponenten für Dateianhänge und Geschäftsbedingungen unterstützt.

### Empfohlene Vorgehensweisen für das Entwerfen von Skripten von verzögertem Laden {#scripting-best-practices-for-configuring-lazy-loading}

Weiterhin sollten Sie Folgendes beim Entwickeln von Skripten für das verzögerte Laden beachten:

* Stellen Sie sicher, dass die initialisierten und berechneten Skripte, die in den Feldern des verzögert geladenen Fragments verwendet werden, idempotent sind. Idempotente Skripte sind diejenigen, die den gleichen Effekt auch nach mehreren Implementierungen haben.
* Verwenden Sie die global verfügbare Eigenschaft von Feldern, um den Wert der Felder, die sich in einem verzögert geladenen Bereich befinden, für alle anderen Bereiche eines Formulars verfügbar zu machen.
* Leiten Sie nicht den Referenzwert eines Feld innerhalb eines verzögert geladenen Bereichs weiter, egal ob das Feld als global in allen Fragmenten markiert ist oder nicht.
* Über die Funktion zum Zurücksetzen des Bereichs können Sie alle sichtbaren Elemente im Bereich zurückzusetzen, indem Sie den folgenden Ausdruck für ein Klickereignis verwenden.

   guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;})).resetData()
