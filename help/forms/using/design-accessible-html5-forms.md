---
title: Entwerfen barrierefreier HTML5-Formulare
seo-title: Designing accessible HTML5 forms
description: HTML5-Formulare verwenden den ARIA HTML5-Barrierefreiheitsstandard. Diese Formulare unterstützen die Navigation mit Registerkarten und sind zertifiziert für die Kompatibilität mit gängigen Bildschirmlesehilfen.
seo-description: HTML5 forms use the ARIA HTML5 accessibility standard. These forms support tabbed navigation and are certified to be compatible with common screen readers.
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
feature: Mobile Forms
exl-id: 64d8cf2c-8180-49ce-a725-48cd03476fb8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 21%

---

# Entwerfen barrierefreier HTML5-Formulare {#designing-accessible-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Für HTML5-Formulare wird der ARIA-HTML5-Standard für Barrierefreiheit verwendet, um die HTML-Formulare barrierefrei zu gestalten. Diese Formulare unterstützen Registerkartennavigation (außer Mozilla FireFox) und sind für die Kompatibilität mit gängigen Bildschirmlesehilfen zertifiziert. Um ein HTML5-Formular mit Barrierefreiheitsfunktionen zu generieren, entwerfen Sie die XFA-Formularvorlage auf Basis einiger [grundlegende Richtlinien für die Entwicklung](/help/forms/using/best-practices-for-html5-forms.md). Die Entwurfsrichtlinien umfassen das Konfigurieren der richtigen Registerkartenreihenfolge und die Bereitstellung des Sprechtext-Inhalts für jedes Formularsteuerelement. AEM Forms Designer unterstützt das Festlegen dieser Formularsteuerungsattribute zum Erstellen eines barrierefreien PDF- und HTML5-Formulars.

*Hinweis:Die Registerkartennavigation deckt keine geschützten Felder ab, z. B. Berechnungsfelder, die die Summe der Werte anzeigen. Damit die Bildschirmlesehilfe den Wert eines geschützten Felds lesen kann, platzieren Sie ein leeres schreibgeschütztes Feld entweder auf dem geschützten Feld oder neben dem Feld. Weisen Sie den Wert des geschützten Felds dem neuen schreibgeschützten Feld zu. Die Bildschirmlesehilfe oder die Registerkartennavigation können dieses schreibgeschützte Feld auswählen und als Wert des geschützten Felds ausdrücken.*

AEM Forms Designer enthält eine Reihe von Sprachtext-Optionen, die an Bildschirmlesehilfen übergeben werden können. Für jedes Objekt in einem Formular kann der Benutzer eine von mehreren Einstellungen für den Text der Bildschirmlesehilfe angeben:

* Benutzerdefinierter Bildschirmlesehilfen-Text, der über die Palette &quot;Ein-/Ausgabehilfe&quot;festgelegt werden kann. Autoren können die Namen von Schaltflächen und Feldern sowie ihren Zweck kommentieren.
* QuickInfos, die in der Palette &quot;Ein-/Ausgabehilfe&quot;festgelegt werden können.
* Beschriftungen für Felder im Formular.
* Namen von Objekten, wie in der Option &quot;Name&quot;der Registerkarte &quot;Bindung&quot;angegeben.

![Barrierefreiheit](assets/accessibility.png)

Wenn in einem Formularsteuerelement mehrere Optionen wie QuickInfos, Bildschirmtext und Beschriftung verfügbar sind, verwendet der Reader &quot;Reader&quot;nur eine dieser Eigenschaften. Die Standardreihenfolge lautet &quot;Benutzerdefinierter Bildschirmtext&quot;, &quot;QuickInfo&quot;, &quot;Beschriftung&quot;und &quot;Reader&quot;. Diese Standardreihenfolge können Sie über die Option Bildschirmlesehilfen-**Rangfolge** in der Palette „Ein-/Ausgabehilfe“ außer Kraft setzen.
