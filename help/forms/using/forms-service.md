---
title: Formularservice
seo-title: Forms Service
description: In diesem Artikel werden der Forms-Dienst und die formularbezogenen Aufgaben beschrieben, die Sie mit dem Forms-Dienst ausführen können.
seo-description: The article describes Forms service and the form-related tasks you can perform using Forms service.
uuid: 3258d3c2-8755-4815-8c97-b2cfb9a9dfd4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: a9695d10-43ec-40eb-942f-7720abaa0973
exl-id: a1c7c90f-6b50-4bc1-9972-1d3bdf8887ce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 47%

---

# Formularservice {#forms-service}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Mit dem Forms-Dienst können Sie interaktive Clientanwendungen zur Datenerfassung erstellen, mit denen typischerweise in Designer erstellte Formulare validiert, verarbeitet, transformiert und bereitgestellt werden. Der Forms-Dienst rendert als PDF Dokumente für jeden Formularentwurf, den Sie entwickeln.

Mit dem Forms-Dienst können Unternehmen ihre intelligenten Datenerfassungsprozesse auch erweitern, indem sie elektronische Formulare als Adobe-PDF bereitstellen. Sie können den Dienst auch verwenden, um Daten in bzw. aus vorhandenen PDF forms zu importieren und zu exportieren.

Der Forms-Dienst bietet folgende Funktionen:

* Rendern Sie PDF forms basierend auf Vorlage und XML-Daten.
* Aktivieren Sie die Formulardatenintegration, um Daten in PDF forms zu importieren und aus ihnen zu extrahieren.
* Wiedergabe von Formularen basierend auf Fragmenten.

## Erstellen von PDF forms  {#creating-pdf-forms-nbsp}

Verwenden Sie den Formulardienst, um PDF forms für die Datenerfassung zu erstellen. Als Grundlage verwenden Sie dazu in der Regel eine AEM Forms Designer-Vorlage. Mit dem Javadoc-Vorgang `renderPDFForm` des Forms-Dienstes konvertieren Sie diese Vorlage in ein PDF-Formular.

Als ersten Parameter des Vorgangs `renderPDFForm` geben Sie den Namen der Vorlagendatei ein (z. B. `ExpenseClaim.xdp`). Die Vorlagendatei kann in einem lokalen Dateisystem, in einem CRX-Repository oder auf einem HTTP- oder FTP-Server gespeichert sein. Den Speicherort der Vorlagendatei können Sie über den Inhaltsstamm im Parameter `PDFFormRenderOptions` des Vorgangs `renderPDFForm` festlegen. In der Javadoc finden Sie Informationen zu weiteren Optionen, die Sie mit dem Parameter `PDFFormRenderOptions` angeben können.

Der Vorgang `renderPDFForm` akzeptiert auch XML-Daten. Die XML-Daten werden bei der Erstellung eines PDF-Formulars mit der Vorlage zusammengeführt, sodass das generierte PDF-Formular die angegebenen Daten enthält. Der zweite Parameter des Vorgangs `renderPDFForm` akzeptiert ein Dokument- bzw. Javadoc-Objekt, das die gewünschten XML-Daten enthält.

## Extrahieren von Daten aus PDF-Formularen  {#extracting-data-from-pdf-forms-nbsp}

Zum Extrahieren von XML-Daten aus einem PDF-Formular verwenden Sie den Javadoc-Vorgang `exportData` des Forms-Dienstes. Dieser Vorgang akzeptiert ein Dokument als ersten Parameter. Sie können die Daten entweder als XDP-Dokument oder als XML-Datei exportieren. Wenn Sie die Daten als XML-Datei exportieren, entfernen die exportierten Daten den XDP-Umschlag und geben eine einfache XML-Datei zurück. Sie können diese Anordnung mit dem zweiten Parameter festlegen.

## Datenimport in PDF forms {#importing-data-into-pdf-forms}

Mit dem Forms-Dienst können Sie ein mit AEM Forms Designer oder `renderPDFForm` erstelltes PDF-Formular auch mit XML-Daten zusammenführen. Der Javadoc-Vorgang `importData` des Forms-Dienstes akzeptiert als Parameter das PDF-Formular sowie die XML-Daten und gibt ein PDF-Formular mit den XML-Daten zurück.

## Wiedergabe von Formularen basierend auf Fragmenten {#rendering-forms-based-on-fragments}

Der Forms-Dienst kann Formulare auch basierend auf Fragmenten wiedergeben, die mit AEM Forms Designer erstellt wurden. Ein Fragment ist ein wiederverwendbarer Teil eines Formulars. Es wird als separate XDP-Datei gespeichert, die in mehrere Formularentwürfe eingefügt werden kann. Beispielsweise kann ein Fragment einen Adressblock oder Copyright-Informationen enthalten.

Die Verwendung von Fragmenten vereinfacht und beschleunigt die Erstellung und Pflege großer Formularmengen. Fügen Sie beim Erstellen eines Formulars einen Verweis auf das erforderliche Fragment ein, damit das Fragment im Formular erscheint. Der Fragmentverweis enthält ein Teilformular, das auf die eigentliche XDP-Datei verweist.

Die Verwendung von Fragmenten hat folgende Vorteile:

* **Wiederverwendung von Inhalten**: Sie können Inhalte in mehreren Formularentwürfen wiederverwenden. Um Teile desselben Inhalts schnell in mehreren Formularen wiederzuverwenden, erstellen Sie ein Fragment. Das Kopieren oder Neuerstellen des Inhalts dauert länger. Durch die Verwendung von Fragmenten stellen Sie außerdem sicher, dass häufig verwendete Bestandteile eines Formularentwurfs in allen darauf verweisenden Formularen stets einen konsistenten Inhalt und ein einheitliches Erscheinungsbild besitzen.
* **Globale Aktualisierungen**: Sie können globale Änderungen an mehreren Formularen nur einmal in einer Datei vornehmen. Sie können den Inhalt, die Skriptobjekte, die Datenbindungen, das Layout oder die Stile eines Fragments ändern. Alle XDP-Formulare, die auf das Fragment verweisen, spiegeln die Änderungen wider.
* **Gemeinsame Formularerstellung**: Sie können die Erstellung von Formularen auf mehrere Ressourcen aufteilen. Formularentwickler, die mit Scripting oder anderen erweiterten Funktionen von AEM Forms Designer vertraut sind, können Fragmente, die Scripting und dynamische Eigenschaften nutzen, entwickeln und mit anderen teilen. Formularentwickler können die Fragmente zum Entwerfen von Formularen verwenden. Darüber hinaus können sie die Fragmente verwenden, um sicherzustellen, dass alle Teile eines Formulars über mehrere Formulare hinweg ein einheitliches Erscheinungsbild und eine einheitliche Funktionalität aufweisen.
