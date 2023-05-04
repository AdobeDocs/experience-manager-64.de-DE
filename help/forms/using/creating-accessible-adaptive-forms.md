---
title: Erstellen barrierefreier adaptiver Formulare
seo-title: Creating accessible adaptive forms
description: AEM Forms bietet Ihnen Tools und das Erstellen barrierefreier adaptiver Formulare und hilft bei der Einhaltung von Barrierefreiheitsstandards.
seo-description: AEM Forms provides you tools and to create accessible adaptive forms and helps comply with accessibility standards.
uuid: eceb3282-0b90-4e0a-8b89-137d27029747
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 96d9ad52-074b-4084-b818-abce79282776
feature: Adaptive Forms
exl-id: adad26fa-b27a-4bd7-806c-4ddfbaae7a37
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 34%

---

# Zugreifbare adaptive Formulare erstellen {#creating-accessible-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Ein barrierefreies Formular ist ein Formular, das jeder verwenden kann, einschließlich Benutzer mit Behinderungen. Adobe Experience Manager (AEM) umfasst eine Reihe von Funktionen, die die Nutzung adaptiver Formulare für Benutzer mit unterschiedlichen Fähigkeiten verbessern. Die Lösung unterstützt außerdem Verfasser von Strukturen bei der Erstellung anpassbarer Formulare.

Die Integration von Barrierefreiheit in adaptive Formulare ermöglicht nicht nur eine möglichst breite Zielgruppe für Inhalte, sondern ist auch eine Anforderung bei der Bereitstellung von Dokumenten in Ländern, in denen die Einhaltung von Barrierefreiheitsstandards vorgeschrieben ist. Mit AEM Forms können Formularentwickler die Barrierefreiheitsstandards einhalten.

Beim Erstellen eines adaptiven Formulars sollte der Autor die folgenden Punkte berücksichtigen, um barrierefreie adaptive Formulare zu erstellen:

* Angabe von angemessenen Beschriftungen für Formularsteuerelemente
* Angabe von Textäquivalenten für Bilder
* Sicherstellen von ausreichendem Farbkontrast
* Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können

## Angabe von angemessenen Beschriftungen für Formularsteuerelemente {#provide-proper-labels-for-form-controls}

Die Beschriftung oder der Titel einer Komponente gibt an, was die Formularkomponente darstellt. Beispielsweise teilt der Text &quot;Vorname&quot;Benutzern mit, dass sie ihren Vornamen in ein Textfeld eingeben müssen. Damit Bildschirmlesehilfen auf die Beschriftung zugreifen können, wird sie programmgesteuert mit einer Formularkomponente verknüpft. Alternativ kann das Formularsteuerelement mit zusätzlichen Barrierefreiheitsinformationen konfiguriert werden.

Die Beschriftung, die von Bildschirmlesehilfen wahrgenommen wird, muss nicht unbedingt mit der visuellen Beschriftung übereinstimmen. In einigen Fällen möchten Sie den Zweck des Steuerelements möglicherweise genauer untersuchen. Für jedes Feldobjekt in einem Formular können die Barrierefreiheitsoptionen verwendet werden, um anzugeben, was die Bildschirmlesehilfe ankündigt, um das spezifische Formularfeld zu identifizieren.

Gehen Sie wie folgt vor, um die Barrierefreiheitsoption zu verwenden:

1. Wählen Sie eine Komponente aus und tippen Sie auf ![cmppr](assets/cmppr.png).
1. Klicken Sie in der Seitenleiste auf **Ein-/Ausgabehilfe**, um die gewünschte Barrierefreiheitsoption auszuwählen.

### Barrierefreiheitsoptionen in Formularkomponenten {#accessibility-options-in-form-components}

![Barrierefreiheitsoptionen in Formularkomponenten](assets/accessibility-options.png)

**Eigener Text** Formularautoren geben den Inhalt im Textfeld „Eigener Text“ der Barrierefreiheitsoptionen an. Die Hilfstechnologie, wie Bildschirmlesegeräte, verwendet diesen benutzerdefinierten Text. Die Verwendung der Einstellung Titel ist in den meisten Szenarien die beste Option. Erwägen Sie die Erstellung von benutzerdefiniertem Bildschirmtext nur, wenn Sie den Reader oder eine Kurzbeschreibung nicht verwenden können.

**Kurzbeschreibung** Bei den meisten Komponenten wird die Kurzbeschreibung zur Laufzeit angezeigt, wenn der Benutzer den Mauszeiger über die Komponente hält. Sie können diese Option im Feld „Kurzbeschreibung“ unter der Option für den Hilfeinhalt festlegen.

**Titel** Verwenden Sie diese Option, damit AEM Forms die visuelle Beschriftung, die mit dem Formularfeld verknüpft ist, als Text für Bildschirmlesegeräte verwendet.

**Name** Sie können einen Wert im Feld „Name“ auf der Registerkarte „Bindung“ angeben. Der Name darf keine Leerzeichen enthalten.

**Kein** Bei Auswahl von „Kein“ verfügt das Formularobjekt im veröffentlichten Formular über keinen Namen. Die Einstellung „Kein“ empfiehlt sich nicht für Formularsteuerelemente.

>[!NOTE]
>
>Optionsfelder und Kontrollkästchen können nur zwei Optionen für die Barrierefreiheit aufweisen, nämlich „Eigener Text“ und „Titel“.

>[!NOTE]
>
>Bei XFA-basierten adaptiven Formularen wird die Barrierefreiheitsoption von den in der XDP festgelegten Barrierefreiheitsoptionen übernommen. QuickInfos aus XDP werden der Kurzbeschreibung zugeordnet und Beschriftung dem Titel zugeordnet. Die anderen Optionen funktionieren wie bisher.

## Angabe von Textäquivalenten für Bilder {#provide-text-equivalents-for-images}

Bilder können bei einigen Benutzern dazu beitragen, das Verständnis zu verbessern. Für Benutzer, die Bildschirmlesehilfen verwenden, verringern Bilder jedoch die Barrierefreiheit Ihres Formulars. Wenn Sie Bilder verwenden möchten, geben Sie Textbeschreibungen für alle Bilder an.

Stellen Sie sicher, dass der Text das Objekt und seinen Zweck im Formular beschreibt. Eine Bildschirmlesehilfe liest diesen alternativen Text, wenn ein Bild auftritt. Für ein Bild muss immer ein alternativer Text angegeben sein.

Wählen Sie eine Bildkomponente aus und tippen Sie auf ![cmppr](assets/cmppr.png). Geben Sie in der Seitenleiste unter „Eigenschaften“ einen Alternativtext für ein Bild ein.

![Alternativtext für ein Bild](assets/image-properties.png)

## Sicherstellen von ausreichendem Farbkontrast {#provide-sufficient-color-contrast}

Bei Barrierefreiheits-Designs müssen zusätzliche Richtlinien zur Farbverwendung beachtet werden. Formularautoren können Farben verwenden, um das Erscheinungsbild von Formularen zu verbessern, indem sie verschiedene Formularkomponenten hervorheben. Eine unsachgemäße Verwendung von Farbe kann jedoch das Lesen eines Formulars für Personen mit unterschiedlichen Fähigkeiten erschweren oder unmöglich machen.

Sehbehinderte Benutzer benötigen einen hohen Kontrast zwischen Text und Hintergrund, um digitale Inhalte zu lesen. Ohne ausreichenden Kontrast kann ein Formular für einige Benutzer schwierig, wenn nicht gar unmöglich zu lesen sein.

Es wird empfohlen, die standardmäßigen Schrift- und Hintergrundfarben zu verwenden - Inhalte in schwarzer Farbe auf einem weißen Hintergrund. Wenn Sie die Standardfarben ändern, wählen Sie entweder eine dunkle Vordergrundfarbe auf einer hellen Hintergrundfarbe oder umgekehrt.

Siehe [Erstellen benutzerdefinierter Designs für adaptive Formulare](/help/forms/using/creating-custom-adaptive-form-themes.md), um weitere Informationen zum Ändern des Farbkontrasts und Designs für adaptive Formulare zu erhalten.

## Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können {#ensure-that-form-controls-are-keyboard-accessible}

Ein barrierefreies Formular kann vollständig mit nur der Tastatur oder einem entsprechenden Eingabegerät ausgefüllt werden. Benutzer mit eingeschränkter Mobilität oder Sehfähigkeit haben möglicherweise keine andere Wahl, als die Tastatur zu verwenden, und viele Benutzer, die eine Maus verwenden können, bevorzugen die Eingabe über die Tastatur. Indem Sie die verschiedenen Eingabemethoden berücksichtigen, erstellen Sie nicht nur barrierefreie Formulare, sondern auch Formulare, die den Vorlieben aller Benutzer besser entsprechen.

Die folgenden Tastaturbefehle sind in AEM Forms verfügbar.

| Aktion | Tastaturbefehl |
|---|---|
| Den Cursor durch ein Formular bewegen | Tab |
| Den Cursor in einem Formular rückwärts bewegen | Umsch+Tab |
| Zum nächsten Bereich wechseln | Alt+Rechtspfeil |
| Zum vorherigen Bereich wechseln | Alt+Linkspfeil |
| Zurücksetzen der ausgefüllten Daten in einem Formular | Alt+R |
| Formular senden | Alt+S | configuring-watched-folder-endpoints.md |
