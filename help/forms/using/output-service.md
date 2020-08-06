---
title: Output-Dienst
seo-title: Output-Dienst
description: Dieser Artikel erläutert den Output-Dienst, eine Komponente der AEM Document Services.
seo-description: Dieser Artikel erläutert den Output-Dienst, eine Komponente der AEM Document Services.
uuid: acd64bbb-91df-49bc-9216-2e860812bbe9
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: 8b96ba2d-007e-472a-875f-2caedd35ecf4
translation-type: tm+mt
source-git-commit: de440f57091d814a0a7ff48e9a0383c5415a0a5b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 80%

---


# Output Service {#output-service}

## Übersicht {#overview}

Der OSGi-Dienst Output ist eine Komponente der AEM Document Services. Der Output-Dienst unterstützt verschiedene Ausgabeformate und Ausgabeentwurfsfunktionen von AEM Forms Designer. Mit dem Output-Dienst können Sie XFA-Vorlagen und XML-Daten in verschiedene Druckformate konvertieren.

Dabei können Sie mit dem Output-Dienst Anwendungen mit folgenden Funktionen erstellen:

* Generieren fertiger Formulardokumente durch Füllen von Vorlagendateien mit XML-Daten
* Generieren von Ausgabeformularen in verschiedenen Formaten einschließlich nicht interaktiver PDF-, PostScript-, PCL- und ZPL-Druckdatenströme
* Generieren von druckbaren PDFs aus XFA-Formular-PDFs
* Generieren Sie PDF-, PostScript-, PCL- und ZPL-Dokumente stapelweise, indem Sie mehrere Datensätze mit den bereitgestellten Vorlagen zusammenführen.

>[!NOTE]
>
>Ausgabedienst ist eine 32-Bit-Anwendung. Unter Microsoft Windows darf eine 32-Bit-Anwendung maximal 2 GB Arbeitsspeicher verwenden. Das Limit gilt auch für den Ausgabedienst.

## Erstellen nicht interaktiver Formulardokumente {#creating-non-interactive-form-documents}

![using_output_changed](assets/usingoutput_modified.png)

Normalerweise erstellen Sie Vorlagen mit AEM Forms Designer. Mit den APIs `generatePDFOutput` und `generatePrintedOutput` des Output-Dienstes können Sie diese Vorlagen direkt in verschiedene Formate wie PDF, PostScript, ZPL und PCL konvertieren.

Mit `generatePDFOutput` generieren Sie PDF-Dokumente, während `generatePrintedOutput` Dokumente in den Formaten PostScript, ZPL und PCL generiert. Der erste Parameter beider Vorgänge akzeptiert entweder den Namen der Vorlagendatei (z. B. `ExpenseClaim.xdp`) oder ein Dokumentobjekt, das die Vorlage enthält. Wenn Sie den Namen der Vorlagendatei angeben, vergessen Sie nicht, auch den Inhaltsstamm als Pfad zum Vorlagenordner anzugeben. You can specify content root using either the `PDFOutputOptions` or the `PrintedOutputOptions` parameter. In der Javadoc finden Sie Informationen zu weiteren Optionen, die Sie mit diesen Parametern angeben können.

Der zweite Parameter akzeptiert ein XML-Dokument, das bei der Generierung des Ausgabedokuments mit der Vorlage zusammengeführt wird.

Der Vorgang `generatePDFOutput` kann als Eingabe auch ein XFA-basiertes PDF-Formular akzeptieren und als Ausgabe eine nicht interaktive Version des PDF-Formulars zurückgeben.

## Generieren nicht interaktiver Formulardokumente {#generating-non-interactive-form-documents}

Angenommen, Sie haben eine oder mehrere Vorlagen und für jede Vorlage mehrere Datensätze mit XML-Daten.

In diesem Fall können Sie mit den Vorgängen `generatePDFOutputBatch` und `generatePrintedOutputBatch` des Output-Dienstes für jeden Datensatz ein Druckdokument erstellen.

Sie können die Datensätze auch zu einem Dokument zusammenfassen. Beide Vorgänge akzeptieren vier Parameter.

Der erste Parameter ist eine Zuordnung mit einer Zufallszeichenfolge als Schlüssel und dem Namen der Vorlagendatei als Wert.

Der zweite Parameter ist ebenfalls eine Zuordnung, deren Wert ein Dokumentobjekt für die XML-Daten ist. Der Schlüssel ist derselbe wie beim ersten Parameter.

The third parameter for `generatePDFOutputBatch` or `generatePrintedOutputBatch` is of type `PDFOutputOptions` or `PrintedOutputOptions` respectively.

The parameter types are the same as types of the parameters for the `generatePDFOutput` and `generatePrintedOutput` operations and have the same effect.

The fourth parameter is of type `BatchOptions`, which you use to specify whether a separate file can be generated for each record. Der Standardwert dieses Parameters ist „false“.

Both `generatePrintedOutputBatch` and `generatePDFOutputBatch` return a value of type `BatchResult`. Der Wert enthält eine Liste der generierten Dokumente. Außerdem enthält er ein Metadatendokument im XML-Format mit Informationen zu jedem generierten Dokument.
