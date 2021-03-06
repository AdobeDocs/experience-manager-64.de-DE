---
title: Empfohlene Vorgehensweisen für HTML5-Formulare
seo-title: Best practices for HTML5 forms
description: 'Stimmen Sie Ihre XFA-basierten HTML5-Formulare für optimale Leistung ab. '
seo-description: Learn how to tune your XFA-based HTML5 Forms for best performance.
uuid: 739700c7-4f88-4b53-9453-1be6d5bc8432
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
content-type: reference
discoiquuid: a5eba237-3aad-497a-8f77-061d5d3df371
feature: Mobile Forms
exl-id: 5f85882c-f7a7-448e-9946-e04a0d74dee1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1426'
ht-degree: 100%

---

# Empfohlene Vorgehensweisen für HTML5-Formulare  {#best-practices-for-html-forms}

Stimmen Sie Ihre XFA-basierten HTML5-Formulare für optimale Leistung ab.

## Übersicht {#overview}

AEM Forms bieten eine Komponente, die HTML5-Formulare genannt wird. Auf diese Weise können Sie vorhandene XFA-basierte PDF-Formulare (XDP-Dateien) im HTML5-Format rendern. Dieses Dokument enthält Richtlinien und Empfehlungen, um die Ladezeit zu verkürzen und die Leistung von HTML5-Formularen auf mobilen Geräten zu verbessern.

Die meisten Mobilgeräte haben eine begrenzten Verarbeitungsleistung und Arbeitsspeicher. Es trägt dazu bei, dass die Standby-Zeit von tragbaren Geräten verbessert wird. Die Webbrowser, die auf einem Mobilgerät ausgeführt werden, haben Zugriff auf beschränkte Ressourcen (begrenzter Arbeitsspeicher und Verarbeitungsfähigkeiten). Sobald das Limit erreicht ist, wird das Browserverhalten langsam. Dieses Dokument enthält Empfehlungen, um die Größe eines HTML5-Formulars zu kontrollieren. Ein kleineres Formular erreicht nicht das Limit des Arbeitsspeichers und der Verarbeitungsleistung eines Geräts und läuft mühelos.

Obwohl die Empfehlungen, die in diesem Artikel diskutiert werden, auf HTML5-Formulare abzielen, gelten diese aber auch für XFA-basierte PDF-Formulare. Diese bewährten Verfahren tragen zusammen zur Gesamtleistung von HTML5-Formularen bei. Es ist eine sorgfältige Planung erforderlich, um effiziente und produktive Formulare zu entwickeln. Erste Schritte:

## Knoten sind Währung der HTML5-Formulare, nutzen Sie diese sinnvoll {#nodes-are-currency-of-html-forms-spend-them-wisely}

Im Allgemeinen hat ein XFA-Formular mehrere Elemente. Beispiel: Tabelle, Text und Bilder. Jedes Element hat einige Eigenschaften, um das Verhalten und das Erscheinungsbild des Elements zu steuern. Wenn ein XFA-Formular im HTML5-Format wiedergegeben wird, werden alle XFA-Elemente und die entsprechenden Eigenschaften in Modell- oder HTML DOM-Knoten konvertiert. Diese Knoten werden zur Größe und Komplexität von DOM hinzugerechnet. HTML5-Formular langsamerer für die Wiedergabe machen.

Es ist einfacher für die Browser, schlanke DOM wiederzugeben. Sie können die folgenden Optimierungen auf einem XFA-Formular durchführen, um die Anzahl der Knoten zu reduzieren. Sie sollten daher eine schlanke DOM-Struktur erstellen:

* Mit der Titel-Eigenschaft können Sie einem Feld eine Beschriftung hinzuzufügen. Verwenden Sie kein separates Textelement, um eine Beschriftung hinzuzufügen. Es unterstützt zusätzliche Gewichtung loszuwerden, was zur Leistungssteigerung führt. Es werden außerdem Layout-Probleme vermieden.
* Halten Sie die Anzahl von Zeichen-Textelementen in einem Formular auf einem absoluten Minimum. Zeichenelemente sind hilfreich beim Verbessern der Lesbarkeit und des Erscheinungsbilds, aber haben keine Informationen zu Speicherfunktionen. Es wird empfohlen, mehrere Zeichen-Textelemente in ein einzelnes Zeichen-Textelement zusammenzuführen. Nutzen Sie alle Möglichkeiten, um ein Formular schlanker zu machen.

## Lite-Formulare funktionieren besser und komprimieren die Ressourcen {#lite-forms-perform-better-keep-the-resources-compressed}

Ein HTML5-Formular kann mehrere externe Ressourcen, z. B. Bilder, JavaScript- und CSS-Dateien, enthalten. Jedes Mal, wenn ein Browser ein Formular anfordert, werden die externen Ressourcen über das Netzwerk übertragen. Die Zeit, die benötigt wird, um die Übertragung über das Netzwerk durchzuführen, ist direkt zur Größe der Dateien proportional.

Deshalb ist die Reduzierung der Größe der externen Ressourcen und die Verwendung von nur absolut erforderlichen Ressourcen die bevorzugte Methode zur Verbesserung der Leistung der Formulare. Sie können die folgenden Optimierungen an einem XFA-Formular durchführen, um die Größe von externen Ressourcen eines Formulars zu verringern:

* Verwenden Sie[ komprimierte Bilder](/help/assets/best-practices-for-optimizing-the-quality-of-your-images.md). Außerdem werden die Netzwerkaktivitäten und der erforderliche Arbeitsspeicher reduziert, um ein Formular wiederzugeben. Deshalb verringert sich die Formularladezeit erheblich.
* Verwenden Sie die minify-Option im AEM Configuration Manager an (Day CQ HTML Library Manager), um JavaScript- und CSS-Dateien zu komprimieren. Weitere Informationen finden Sie unter[ OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md).
* Netzkompression aktivieren. Die Größe der Anforderungen und Antworten von einem Formular werden reduziert. Für andere Details finden Sie weitere Informationen im Abschnitt [Leistungsoptimierung des AEM Forms-Servers](https://helpx.adobe.com/de/aem-forms/6-3/performance-tuning-aem-forms.html).

## Halten Sie das Interesse wach, zeigen Sie nur erforderliche Felder  {#keep-the-interest-alive-show-only-required-fields}

Ein HTML5-Formular kann hunderte von Seiten umfassen. Ein Formular mit vielen Feldern lädt langsam im Browser. Sie können die folgenden Optimierungen in einem XFA-Formular durchführen, um die Formulare mit vielen Feldern und Seiten zu optimieren:

* Bewerten Sie das Teilen großer Formulare in mehrere Formulare. Sie können auch einen Formularsatz verwenden, um alle kleineren Formulare zusammen zu gruppieren und sie als einzelne Einheit darstellen. Ein Formularsatz lädt nur die erforderlichen Formulare. Sie können in einem Formularsatz gemeinsame Felder in verschiedenen Formularen konfigurieren, um Datenbindungen zu teilen. Mit den richtigen Datenbindungen müssen Benutzer allgemeine Informationen nur einmal ausfüllen. Diese werden dann in den nachfolgenden Formularen automatisch ausgefüllt. Weitere Informationen finden Sie unter[ Formularsatz in AEM Forms](https://helpx.adobe.com/de/aem-forms/6-3/formset-in-aem-forms.html).
* Erwägen Sie Abschnitte zu teilen und jeden Abschnitt auf eine andere Seite zu verschieben. HTML5-Formulare laden dynamisch jede Seite auf Seitenrollenantrag. Nur gescrollte Seiten (Seiten, die angezeigt werden, und die Seiten, die vorausgehen) werden im Arbeitsspeicher gespeichert. Die übrigen Seiten werden bei Bedarf geladen. Deshalb reduziert die Verringerung und das Verschieben eines Abschnitts auf eine Seite die Zeit, die zum Laden eines Formulars erforderlich ist. Sie können die erste Seite des Formulars als Einstiegsseite verwenden. Es ist mit dem Inhaltsverzeichnis eines Buchs vergleichbar. Eine Einstiegsseite des Formulars enthält nur Links zu den anderen Abschnitten des Formulars. Es verbessert deutlich die Ladezeit der ersten Seite des Formulars und führt zu einer Verbesserung der Benutzerfreundlichkeit.
* Halten Sie bedingte Bereiche, standardmäßig ausgeblendet. Machen Sie diese Abschnitte nur sichtbar, wenn eine bestimmte Bedingung erfüllt wird. Auf diese Weise können Sie die Größe des DOM auf ein Minimum beschränken. Sie können auch Navigation mit Registerkarten verwenden, um nur einen Abschnitt auf einmal anzuzeigen.

## Weniger ist mehr, reduzieren Sie die Anzahl der Seiten {#less-is-more-reduce-the-number-of-pages}

HTML5-Formulare können datenbasierte Felder enthalten (Tabellen und Unterformulare). Diese Felder erweitern die Größe des Formulars in der Laufzeitumgebung. So kann zum Beispiel eine datenbasierte Tabelle in einem HTML5-Formular tausende von Zeilen umfassen. Diese Tabellen können zu Layout- und Leistungsverringerung führen. Mit unten vorgeschlagenen Optimierungen können Sie die Ladezeiten von HTML5-Formularen mit datengesteuerten Felder verringern:

* Verwenden Sie XFA-Skipt zur ausgelagerten Navigation, um dynamische datengesteuerte Felder anzuzeigen (Tabellen und Unterformulare). In ausgelagerter Navigation werden nur bestimmte Daten auf einer Seite angezeigt. Dadurch wird der Vorgang des Zeichnens im Browser auf die jeweils angezeigten Felder beschränkt und die Navigation in einem Formular erleichtert. Außerdem sind die Benutzer auf Mobilgeräten nur an einer Untergruppe von Daten interessiert. Damit wird größere Benutzerfreundlichkeit geboten und die Zeit zum Laden der benötigten Daten wird verkürzt. Das Ergebnis sind zwei Lösungen. Beachten Sie auch, dass ausgelagerte Navigation nicht vorkonfiguriert verfügbar ist. Sie können XFA-Skripterstellung verwenden, um die ausgelagerte Navigation zu entwickeln.

* Bewerten Sie das Zusammenführen mehrerer schreibgeschützter Spalten zu einer einzelnen Spalte. Außerdem wird der Arbeitsspeicher, der benötigt wird, um das Formular anzuzeigen, reduziert. Vermeiden Sie es, die Spalten anzuzeigen, die keine Eingaben von den Benutzern erfordern.
* Bewerten Sie das Teilen des datengesteuerten Formulars in einen [Formularsatz](https://helpx.adobe.com/aem-forms/6-3/formset-in-aem-forms.html), wenn die obigen Vorschläge nicht viele Verbesserungen bringen. Wenn beispielsweise eine Tabelle mehr als 1000 Zeilen aufweist, verschieben Sie jede 100. Zeile zu ein anderes Formular. Das würde die Ladezeit und die Leistung der Formulare verbessern. Beachten Sie auch, dass ein Formularsatz eine konsolidierte Übermittlungs-XML für alle Formulare erzeugt. Um Daten für jedes Formular zu unterscheiden, verwenden Sie verschiedene Datenstämme. Weitere Informationen finden Sie unter[ Formularsatz in AEM Forms](https://helpx.adobe.com/aem-forms/6-3/formset-in-aem-forms.html).

## Zweierpotenz für Datensatzdokument (DOR) {#power-of-two-for-document-of-record-dor}

Ein XFA-Formular kann viele Abschnitte enthalten, die nur für Datensatzdokumente (DOR) verwendet werden. Um die Anzahl der Knoten zu reduzieren und die Leistung eines solchen Formulars zu verbessern, können Sie verschiedene Kopien des Formulars beibehalten – eine Kopie zum Ausfüllen des Formulars und eine weitere zum Erzeugen des Datensatzdokuments auf dem Server. Zeigen Sie Felder in der Kopie, die nur zum Erfassen von Daten erforderlich sind. Behalten Sie Felder, die nur in der gedruckten Ausgabe des Formulars erforderlich sind, im Datensatzdokumente-XFA bei. Bevor Sie den vorgeschlagene Ansatz wählen, bewerten Sie die Leistungssteigerung und die Wartung.

## Weiterführende Informationen  {#recommended-reads}

Mit Adobe Experience Manager (AEM) Forms können Sie komplexe Transaktionen in einfache, beeindruckende digitale Erlebnisse umwandeln. Es bedarf jedoch gemeinsamer Bemühungen, um effiziente und produktive Formulare zu entwickeln. Zusätzlich zu HTML5-Formularen finden Sie hier einige Informationen für bewährte Verfahren zu AEM:

* [Bewährte Verfahren für das Bereitstellen und Warten von AEM](/help/sites-deploying/best-practices.md)
* [Bewährte Verfahren zum Erstellen von Inhalten](/help/sites-authoring/best-practices.md)
* [Best Practices für die Verwaltung von AEM](/help/sites-administering/administer-best-practices.md)
* [Bewährte Verfahren zur Entwicklung von Lösungen](/help/sites-developing/best-practices.md)
* [Best Practices für die Arbeit mit adaptiven Formularen](/help/forms/using/adaptive-forms-best-practices.md)
* [AEM Forms-Server bettet Schriftarten nicht in ein dynamisches PDF-Formular ein](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-server-does-not-embed-fonts-to-dynamic-pdf-form.html)

## Schnellnachweiskarte {#quick-reference-card}

Sie können die folgende Karte (Klicken Sie auf „Karte“, um eine Version mit hoher Auflösung herunterzuladen) drucken, und auf Ihrem Schreibtisch als Referenz behalten.

[ ![Bewährte Verfahren für HTML5-Formular-Schnellnachweiskarte](do-not-localize/best-practices_reference_card.png)](assets/html5_forms_best_practices_reference_card.pdf)
