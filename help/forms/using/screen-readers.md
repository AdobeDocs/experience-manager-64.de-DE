---
title: Bildschirmlesehilfen für HTML5-Formulare
seo-title: Screen readers for HTML5 forms
description: Listet die von HTML5-Formularen unterstützten Bildschirmlesehilfen auf.
seo-description: Lists the screen readers supported with HTML5 forms.
uuid: 035354e2-957f-4eb6-bc16-4ca96ec7ac74
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 53c57180-7004-4534-9146-603f7770a6fe
feature: Mobile Forms
exl-id: c27eb771-d390-4534-8e67-f1277550e760
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 60%

---

# Bildschirmlesehilfen für HTML5-Formulare {#screen-readers-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

HTML5-Formularkomponenten rendern XFA-Formularvorlagen im HTML5-Format. Diese Formulare können von allen Standardbrowsern wiedergegeben werden, die HTML5 unterstützen. Um ein ähnliches Datenerfassungserlebnis in allen PDF- und HTML5-Formularen zu unterstützen, wird das Layout der PDF forms in HTML5-Formularen beibehalten.

HTML5-Formulare verwenden standardmäßige HTML-Konstrukte, sodass für diese Formulare barrierefreie HTML-Anwendungen verwendet werden können. Wenn ein Formular gemäß den Best Practices für barrierefreie Formulare entworfen wurde, funktioniert es mit jeder unterstützten Bildschirmlesehilfe. Darüber hinaus sind solche Formulare für die Tastaturnavigation aktiviert.

## Barrierefreiheitsstandards {#accessibility-standards}

HTML5-Formulare erfüllen Abschnitt 508 für Barrierefreiheit mit bekannten Ausnahmen. Siehe [VPAT für HTML5-Formulare](https://www.adobe.com/content/dam/cc1/en/accessibility/compliance/pdfs/adobe-livecycle-es4-section-508-vpat-portfolio.pdf) für Details.

## Zertifizierte Bildschirmlesehilfen für HTML5-Formulare {#certified-screen-readers-for-html-forms}

* JAWS 14.0 unter Microsoft Windows
* VoiceOver unter Mac OS X und iPad

### JAWS {#jaws}

In HTML5-Formularen funktionieren alle standardmäßigen Tasteneingaben und Tastaturbefehle. Weitere Informationen zur Verwendung von JAWS finden Sie unter [https://www.freedomscientific.com/jaws-hq.asp](https://www.freedomscientific.com/products/software/jaws/).

### VoiceOver {#voiceover}

HTML5-Formulare unterstützen alle Standard-Tasteneingaben und Gesten für VoiceOver. Weitere Informationen zum Einrichten und Verwenden von VoiceOver finden Sie unter [https://www.apple.com/accessibility/voiceover/](https://www.apple.com/accessibility/voiceover/).

## Bekannte Probleme {#known-issues}

* **(Ausschließlich Internet Explorer 9)** In HTML5-Formularen werden die Seiten bei Bedarf geladen (dynamisch). Das Laden von Seiten bei Bedarf verursacht Probleme mit Bildschirmlesehilfen. Wenn der Fokus der Bildschirmlesehilfe am letzten Seitenfeld angelangt ist und der Benutzer die Tabulator-Taste drückt, statt den Fokus auf das erste Feld der nächsten Seite zu legen, kehrt die Bildschirmlesehilfe auf das erste Feld der ersten Seite des Formulars zurück.
* **(Ausschließlich Internet Explorer 9)** Das Datumsauswahl-Steuerelement in HTML5-Formularen lässt sich nicht vollständig über die Tastatur steuern. Wenn Sie im Datumsauswahl -Steuerelement die Bild-Auf/Bild-Ab-Tasten mehrmals hintereinander drücken, wird das Datumsauswahl-Steuerelement geschlossen und der Fokus wird auf das nächste/letzte Feld gerichtet.

* VoiceOver kann Pfeiltasten auf dem Datumswidget auf iPad Safari nicht erkennen.
