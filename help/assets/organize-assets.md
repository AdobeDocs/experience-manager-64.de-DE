---
title: Digitale Assets organisieren
description: Organisieren Sie Ihre digitalen Assets, Bilder, Dateien, Ordner usw. mit Experience Manager.
contentOwner: AG
feature: Asset-Verwaltung, Suche
role: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 20%

---


# Digitale Assets organisieren {#organize-digital-assets}

Alle digitalen Assets, Metadaten und Inhalte von Microsoft Office- und PDF-Dokumenten werden extrahiert und für die Suche aufbereitet. Die Suche ermöglicht weitreichende Filtermöglichkeiten für Assets und hält dabei vollständig die korrekten Berechtigungen ein. Metadaten werden in den Metadaten in Digital Asset Management ausführlich behandelt.

AEM Assets unterstützt verschiedene Methoden zum Organisieren von Inhalten. Sie können sie hierarchisch organisieren, indem Sie Ordner verwenden oder sie auf ungeordnete, Ad-hoc-Weise organisieren, z. B. mithilfe von Tags. Benutzer können Tags im DAM Asset Editor bearbeiten, in dem Teil-Assets, Ausgabeformate und Metadaten angezeigt werden.

## Organisieren von Assets in Ordnern {#organize-using-folders}

Die einfachste Möglichkeit zum Organisieren von Assets besteht darin, diese in Ordnern zu speichern. Es entspricht dem Organisieren von Dateien in Ordnern in unserem lokalen Dateisystem. Weitere Informationen zum Erstellen und Verwalten von Ordnern finden Sie unter [Verwalten von Assets](managing-assets-touch-ui.md). Wie Sie Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie mit den Dateien in diesen Ordnern umgehen, kann erhebliche Auswirkungen auf die Verarbeitung dieser Assets haben. Durch die Verwendung konsistenter und geeigneter Strategien zur Datei- und Ordnerbenennung sowie einer bewährten Metadatenpraxis können Sie das Beste aus Ihrem digitalen Assets-Repository machen.

* In den meisten Fällen wächst Ihr Repository für digitale Assets immer. Daher ist es wichtig, die Verwendung von Metadaten, die Ordnerstruktur und die Dateibenennung zu einem frühen Zeitpunkt des Inhaltserstellungszyklus zu formalisieren.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Diese Konsistenz hilft Ihnen, Ihre Assets besser zu verwalten und zu verarbeiten. Beispielsweise können Sie mithilfe von Assets, die in den folgenden Ordnertypen platziert werden, geeignete [Profil für die Verarbeitung von Assets](processing-profiles.md) verwenden:

   * **Entwicklungsordner** – enthalten digitale Assets, an denen Sie derzeit arbeiten.
   * **Kundenordner** – enthalten digitale Assets basierend auf Kunden oder Projektnamen.
   * **Primär folders**  - enthält digitale Originalelemente.
   * **Ausgabeformatordner** – enthalten Ausgabeformate und Kopien der digitalen Quell-Assets in Originalform.
   * **Dateigrößenordner** – enthalten digitale Assets basierend auf kleinen, mittleren oder großen Dateien.
   * **Bereitstellungsordner** – enthalten digitale Assets, die für die Veröffentlichung auf Ihrer Website bereit sind.
   * **MIME-Typordner**  - enthält digitale Assets, die für MIME-Typen wie Bilder, Dokumente und Multimedia spezifisch sind.
   * **Archivordner** – enthalten veraltete digitale Assets.
   * **Datumsbasierte Ordner** – enthalten digitale Assets basierend auf einem Erstellungsdatum oder dem letzten Änderungsdatum.

* Erstellen Sie einen Ordner mit Ordnern, die sich wahrscheinlich nicht ändern, sodass Anpassungen oder Automatisierungen weiterhin funktionieren. Beispielsweise funktionieren die zugewiesenen Profil weiterhin.
* Wenn ein Asset bereits veröffentlicht wurde, verwenden Sie AEM, um das Asset in einen anderen Ordner zu verschieben und es erneut zu veröffentlichen, dann ist der ursprüngliche Speicherort des veröffentlichten Assets zusammen mit dem neu veröffentlichten Asset weiterhin verfügbar. Das ursprünglich veröffentlichte Asset ist jedoch *lost* zu AEM und kann nicht rückgängig gemacht werden. Als Best Practice sollten Sie daher zunächst die Veröffentlichung eines Assets rückgängig machen und es dann in einen anderen Ordner verschieben.

## Organisieren von Assets mit den Tags {#use-tags-to-organize-assets}

Mithilfe von Tags als Metadaten können Sie mühelos Assets suchen, Sammlungen mit den Suchergebnissen erstellen, die Suchrangliste für einige Assets verbessern und die AI-Algorithmen von Adobe Sensei zur Ermittlung von Assets nutzen.

Adobe Experience Manager Assets verwendet einen Selbstlernalgorithmus, um hochgradig beschreibende Tags zu erstellen, mit denen Sie das richtige Asset in nur wenigen Klicks finden können. Beim intelligenten Tagging werden Adobe Sensei, unser künstliches Intelligenz- und maschinelles Lernen-Framework, eingesetzt, das sowohl Standard- als auch unternehmensspezifische Tags erkennen und auf Bilder anwenden kann. Intelligente Tags können auch Inhalte, einzelne Wörter oder Ausdrücke identifizieren und automatisch beschreibende Tags auf Assets anwenden

Weitere Informationen finden Sie in den folgenden Artikeln:

* [Informationen zu Tags in AEM](/help/sites-authoring/tags.md)
* [Bearbeiten von Asset-Metadaten](meta-edit.md)
* [Verbesserte intelligente Tags in Assets](enhanced-smart-tags.md)

## Als Sammlungen organisieren {#organize-as-collections}

Mit Asset-Sammlungen in Experience Manager Assets können Sie die Erstellung, Bearbeitung und Freigabe von Assets optimieren. Erstellen Sie verschiedene Arten von Sammlungen basierend auf der Art und Weise, wie Sie sie verwenden, einschließlich Sammlungen, die eine statische Referenz-Liste von Assets, Ordnern und Sammlungen enthalten, sowie Sammlungen, die Assets basierend auf Suchkriterien abrufen.  Sie können auch Sammlungen mit Assets von verschiedenen Orten erstellen und sie für mehrere Benutzer mit unterschiedlichen Zugriffs-, Anzeige- und Bearbeitungsberechtigungen freigeben.

Weitere Informationen finden Sie unter [Sammlungen verwalten](managing-collections-touch-ui.md)

<!-- TBD items: add screenshots where applicable
Any hints/recommendations of when to use what method of organizing? Some examples of how organizing helps towards a better taxonomy and improved content velocity.
Add back links to blog posts by marketing?
-->

## Organisieren Sie Ihre Assets für die Verwendung von Profilen {#organize-to-use-profiles}

Ein verarbeitendes Profil enthält Verarbeitungsbefehle für Assets, die für Assets gelten, die in vordefinierte  hochgeladen werden. Mit Profilen wird die Verarbeitung von Ordnerinhalten oder neu hochgeladenen Assets automatisiert. Sie können Profil nutzen, um Ihre Assets besser zu organisieren.

Durch die Standardisierung der Metadaten-Nutzung, Dateibenennung und Ordnerstruktur wird sichergestellt, dass Sie mit zunehmender Anzahl digitaler Assets verarbeitende Profil präziser und konsistenter auf Ordner anwenden können.

Weitere Informationen zu den verschiedenen Profilen, die Sie zur Verarbeitung von Assets erstellen und verwalten können, finden Sie unter

* [Profile zur Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md)
* [Metadatenprofile](metadata-profiles.md)
* [Videoprofile](video-profiles.md)
* [Dynamic Media Image Profils](image-profiles.md)
