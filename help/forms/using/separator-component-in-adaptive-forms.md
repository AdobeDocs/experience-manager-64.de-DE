---
title: Trennzeichenkomponente in adaptiven Formularen
seo-title: Separator component in adaptive forms
description: Sie können die Trennzeichenkomponente verwenden, um Abschnitte eines Formulars visuell zu trennen.
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: d51c3797-8227-41ed-88cd-c56cc129eb86
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ba674a2d-7c78-430e-8e17-1a18619e71cb
feature: Adaptive Forms
exl-id: 7e37401a-8c63-4711-8a33-61e6bd4b419f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 39%

---

# Trennzeichenkomponenten in adaptiven Formularen {#separator-component-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können die Trennzeichenkomponente verwenden, um Bereiche eines Formulars visuell zu trennen. Sie können die Gesamtdarstellung und den Stil einer Trennzeichenkomponente definieren, indem Sie die folgenden Eigenschaften der Trennzeichenkomponente angeben:

* **Elementname:** Gibt den Namen der Komponente an. Die SOM-Ausdrücke richten sich an die Komponente mit dem im Feld Elementname angegebenen Wert.
* **Stärke:** Gibt die Stärke der Trennzeichenkomponente in Pixel an.
* **Colspan:** Gibt die Anzahl der Spalten an, die eine Trennzeichenkomponente umfasst.
* **CSS-Klasse:** Gibt die benutzerdefinierte CSS-Klasse für die Trennzeichenkomponente an.
* **Inline-Stile:** Mit AEM Forms können Sie jetzt CSS-Inline-Stile auf individuelle adaptive Formularkomponenten anwenden und eine Vorschau der Änderungen in Echtzeit anzeigen.

Angeben der Eigenschaften einer Trennzeichenkomponente:

1. Wählen Sie eine Trennzeichenkomponente aus und tippen Sie auf ![cmppr](assets/cmppr.png). Die Eigenschaften werden in der Seitenleiste geöffnet.
1. Klicken Sie auf eine Registerkarte im Abschnitt Inline-CSS-Eigenschaften , um CSS-Eigenschaften anzugeben. Beispiel: a. Klicken Sie auf der Registerkarte Feld auf **Element hinzufügen**. Eine Zeile mit zwei Feldern wird hinzugefügt.
1. Geben Sie im ersten Feld von links eine CSS3-Eigenschaft an, die Sie anwenden möchten. Beispiel: **border**. Sie können auch eine Eigenschaft auswählen, indem Sie auf die Nach-unten-Taste klicken. Die Dropdown-Liste ist nicht vollständig und Sie können einen beliebigen unterstützten CSS3-Eigenschaftennamen in dieses Feld eingeben.
1. Geben Sie im angrenzenden Feld einen gültigen Wert für die angegebene CSS3-Eigenschaft an. Beispiel: **3px solid black**.
1. Klicken Sie auf **Element hinzufügen**, um eine andere Eigenschaft und deren Wert anzugeben.
1. Klicken Sie auf **Vorschau**, um eine Vorschau der Änderungen im Formular anzuzeigen.
1. Klicken **OK** , um die Änderungen zu bestätigen, oder **Abbrechen**, um das Dialogfeld ohne Änderungen zu beenden.
