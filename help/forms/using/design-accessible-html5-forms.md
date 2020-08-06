---
title: Entwerfen barrierefreier HTML5-Formulare
seo-title: Entwerfen barrierefreier HTML5-Formulare
description: HTML5-Formulare verwenden den ARIA-HTML5-Standard für Barrierefreiheit. Diese Formulare unterstützen Registerkartennavigation und sind zertifiziert für ihre Kompatibilität mit üblichen Bildschirmlesehilfen.
seo-description: HTML5-Formulare verwenden den ARIA-HTML5-Standard für Barrierefreiheit. Diese Formulare unterstützen Registerkartennavigation und sind zertifiziert für ihre Kompatibilität mit üblichen Bildschirmlesehilfen.
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 89%

---


# Entwerfen barrierefreier HTML5-Formulare {#designing-accessible-html-forms}

Für HTML5-Formulare wird der ARIA-HTML5-Standard für Barrierefreiheit verwendet, um die HTML-Formulare barrierefrei zu gestalten. Diese Formulare unterstützen Registerkartennavigation (außer Mozilla Firefox) und sind zertifiziert für ihre Kompatibilität mit üblichen Bildschirmlesehilfen. To generate an HTML5 form with good accessibility features, design the XFA form template based on some [basic designing guidelines](/help/forms/using/best-practices-for-html5-forms.md). Die Entwurfsrichtlinien umfassen das Konfigurieren der richtigen Registerkartenreihenfolge und die Bereitstellung des Sprechtext-Inhalts für jedes Formularsteuerelement. AEM Forms Designer unterstützt die Einstellung dieser Formularsteuerelementattribute zum Generieren eines barrierefreien PDF- und HTML5-Formulars.

*Hinweis: Die Registerkartennavigation deckt keine geschützten Felder ab, wie etwa Berechnungsfelder, die Wertesummen anzeigen. Damit die Bildschirmlesehilfe den Wert eines geschützten Felds liest, platzieren Sie ein leeres schreibgeschütztes Feld entweder auf oder neben dem geschützten Feld. Weisen Sie den Wert des geschützten Feldes dem neuen schreibgeschützten Feld zu. Die Bildschirmlesehilfe oder die Registerkartennavigation können dieses schreibgeschützte Feld erfassen und als Wert des geschützten Felds wiedergeben.*

AEM Forms Designer enthält einige Sprechtextoptionen, die an Bildschirmlesehilfen übergeben werden können. Für jedes Objekt in einem Formular kann der Benutzer eine oder mehrere Einstellungen für den Text der Bildschirmlesehilfe angeben:

* Benutzerdefinierter Bildschirmlesehilfen-Text, der mithilfe der Palette „Ein-/Ausgabehilfe“ festgelegt werden kann. Autoren können die Namen von Schaltflächen und Feldern sowie deren Zweck kommentieren.
* QuickInfos, die in der Palette „Ein-/Ausgabehilfe“ eingestellt werden können.
* Beschriftungen für Felder im Formular.
* Namen von Objekten (wie im Feld „Name“ der Registerkarte „Bindung“ angegeben).

![Zugänglichkeit](assets/accessibility.png)

Wenn mehrere Optionen wie QuickInfos Bildschirmlesehilfen-Text, und Beschriftung in einem Formularsteuerelement zur Verfügung stehen, verwendet die Bildschirmlesehilfe nur eine dieser Eigenschaften. Die Standardreihenfolge ist benutzerdefinierter Bildschirmlesehilfen-Text, QuickInfo, Beschriftung und Name. Diese Standardreihenfolge können Sie über die Option Bildschirmlesehilfen-**Rangfolge** in der Palette „Ein-/Ausgabehilfe“ außer Kraft setzen.
