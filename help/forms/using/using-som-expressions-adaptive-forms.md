---
title: Verwenden von SOM-Ausdrücken in adaptiven Formularen
seo-title: Verwenden von SOM-Ausdrücken in adaptiven Formularen
description: Erfahren Sie, wie Sie SOM-Ausdrücke eines Bereichs eines adaptiven Formulars extrahieren.
seo-description: Erfahren Sie, wie Sie SOM-Ausdrücke eines Bereichs eines adaptiven Formulars extrahieren.
uuid: 4bc80e2a-3563-48a3-996d-021b701bc2ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7dff7ef2-80d1-434a-b9b0-ac6654736602
translation-type: tm+mt
source-git-commit: f824b449b85ad7900aaf73fd79614f5e6140f873
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 89%

---


# Verwenden von SOM-Ausdrücken in adaptiven Formularen {#using-som-expressions-in-adaptive-forms}

Adaptive Formulare werden als AEM-Seite modelliert, die als JCR-Inhaltstruktur im AEM-Repository repräsentiert wird. Das Schlüsselelement der Inhaltstruktur ist der Knoten „guideContainer“. Unter „guideContainer“ befindet sich der Knoten „rootPanel“, der verschachtelte Bereiche und Felder enthalten kann.

Sie können ein Scripting Object Model (SOM) zum Referenzieren von Werten, Eigenschaften und Methoden innerhalb eines bestimmten Document Object Model (DOM) verwenden. Ein DOM organisiert die Speicherobjekte und -eigenschaften in einer hierarchischen Baumstruktur. Ein SOM-Ausdruck referenziert Felder/Zeichenelemente und Bereiche.

Die folgende Abbildung zeigt eine Knotenstruktur, in die ein adaptives Formular übersetzt wird, wenn Sie einem Formular Komponenten hinzufügen. Sie können beispielsweise dem Stammbereich einen Bereich und dann in dem Bereich ein Optionsfeld hinzufügen. Der Bereich wird dann zur Laufzeit in ein DOM transformiert. The SOM Expression for the radio-button field in adaptive form is specified as `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`.

![DOM-Baumstruktur](assets/hierarchy-1.png)

Einem SOM-Ausdruck für ein beliebiges Element in einem adaptiven Formular wird das Präfix `guide[0].guide1[0]` ] vorangestellt. Die Position einer Komponente in der hierarchischen Knotenstruktur wird zum Ableiten ihres SOM-Ausdrucks verwendet.

![DOM-Baumstruktur mit zwei Optionsfeldern](assets/hierarchy_radio_button.png)

Der SOM-Ausdruck ändert sich, wenn Sie die Position der Optionsfelder im adaptiven Formular ändern. Im Bearbeitungsmodus können Sie den SOM-Ausdruck eines Felds oder Elements in AEM Forms mithilfe der Option „SOM-Ausdruck anzeigen“ anzeigen. Die Option wird auf dem Bereich, und wenn Sie mit der rechten Maustaste auf das Feld oder Element klicken, angezeigt.

![Extrahieren von SOM-Ausdrücken in einem adaptiven Formular](assets/som-expressions.png)

Innerhalb von Bereichen können Sie von der Bereichssymbolleiste aus auf die Funktion zugreifen. Die Funktion vereinfacht die Skripterstellung durch Autoren adaptiver Formulare.

![Extrahieren von SOM-Ausdrücken mithilfe der Bereichssymbolleiste](assets/som-expression.png)

Einige in [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.md) aufgeführten APIs verwenden den SOM-Ausdruck eines Elements. Um beispielsweise ein bestimmtes Feld in einem adaptiven Formular hervorzuheben, muss der entsprechende SOM-Ausdruck an die `getFocus`-API in `guideBridge` übergeben werden.

