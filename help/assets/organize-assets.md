---
title: Digitale Assets organisieren
description: Organisieren Sie mithilfe von Experience Manager Ihre digitalen Assets, Bilder, Dateien, Ordner usw.
contentOwner: AG
feature: Asset Management,Search
role: User
exl-id: 41e083b3-e956-4346-9a99-008de2c6a169
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 82%

---

# Digitale Assets organisieren {#organize-digital-assets}

Alle digitalen Assets, Metadaten und Inhalte von Microsoft Office- und PDF-Dokumenten werden extrahiert und für die Suche aufbereitet. Die Suche ermöglicht weitreichende Filtermöglichkeiten für Assets und hält dabei vollständig die korrekten Berechtigungen ein. Metadaten werden in „Metadaten in Digital Asset Management“ ausführlich behandelt.

[!DNL Experience Manager] Assets unterstützt verschiedene Methoden zum Organisieren von Inhalten. Sie können sie hierarchisch anhand von Ordnern organisieren oder in ungeordneter Ad-hoc-Manier ablegen, wobei zum Beispiel Tags verwendet werden können. Benutzer können Tags im DAM Asset Editor bearbeiten, in dem Teil-Assets, Ausgabeformate und Metadaten angezeigt werden.

## Organisieren von Assets in Ordnern {#organize-using-folders}

Die einfachste Möglichkeit zum Organisieren von Assets besteht darin, sie in Ordnern zu speichern. Dies entspricht dem Organisieren von Dateien in Ordnern in Ihrem lokalen Dateisystem. Weitere Informationen zum Erstellen und Verwalten von Ordnern finden Sie unter [Verwalten von Assets](managing-assets-touch-ui.md). Wie Sie Ihre Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie die Dateien in diesen Ordnern handhaben, hat daher eine erhebliche Auswirkung darauf, wie diese Assets verarbeitet werden. Durch die Verwendung konsistenter und angemessener Strategien für die Datei- und Ordnernamen sowie guter Metadatenpraktiken können Sie das gesamte Repository für digitale Assets optimal nutzen.

* In den meisten Fällen wächst Ihr Repository für digitale Assets ständig. Daher ist es wichtig, die Verwendung von Metadaten, die Ordnerstruktur und die Dateibenennung frühzeitig im Erstellungszyklus des Inhalts zu formalisieren.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Diese Konsistenz hilft Ihnen, Ihre Assets besser zu bearbeiten und zu verwalten. Beispielsweise können Assets, die in den folgenden Ordnern abgelegt sind, bei der [Verwendung geeigneter Profile für die Asset-Verarbeitung](processing-profiles.md) helfen:

   * **Entwicklungsordner** – enthalten digitale Assets, an denen Sie derzeit arbeiten.
   * **Kundenordner** – enthalten digitale Assets basierend auf Kunden oder Projektnamen.
   * **Primäre Ordner** - enthält digitale Quell-Assets in Originalform.
   * **Ausgabeformatordner** – enthalten Ausgabeformate und Kopien der digitalen Quell-Assets in Originalform.
   * **Dateigrößenordner** – enthalten digitale Assets basierend auf kleinen, mittleren oder großen Dateien.
   * **Bereitstellungsordner** – enthalten digitale Assets, die für die Veröffentlichung auf Ihrer Website bereit sind.
   * **Ordner vom Typ MIME** - enthält digitale Assets, die für MIME-Typen spezifisch sind, z. B. Bilder, Dokumente und Multimedia.
   * **Archivordner** – enthalten veraltete digitale Assets.
   * **Datumsbasierte Ordner** – enthalten digitale Assets basierend auf einem Erstellungsdatum oder dem letzten Änderungsdatum.

* Erstellen Sie ein Verzeichnis mit Ordnern, die sich wahrscheinlich nicht ändern werden, damit Anpassungen oder Automatisierungen weiterhin funktionieren. Beispielsweise funktionieren die zugewiesenen Verarbeitungsprofile weiterhin.
* Wenn Sie ein bereits veröffentlichtes Asset mithilfe von [!DNL Experience Manager] in einen anderen Ordner verschieben und anschließend vom neuen Speicherort aus erneut veröffentlichen, ist der ursprünglich veröffentlichte Asset-Speicherort neben dem neu veröffentlichten Asset weiterhin verfügbar. Das ursprünglich veröffentlichte Asset ist allerdings für [!DNL Experience Manager] *nicht mehr zugänglich*. Daher kann dessen Veröffentlichung nicht rückgängig gemacht werden. Daher empfiehlt es sich, zunächst die Veröffentlichung eines Assets rückgängig zu machen und es dann in einen anderen Ordner zu verschieben.

## Organisieren von Assets mit Tags {#use-tags-to-organize-assets}

Mithilfe von Tags als Metadaten können Sie mühelos Assets suchen, Sammlungen mithilfe der Suchergebnisse erstellen, das Suchangebot für einige Assets verbessern und die KI-Algorithmen von Adobe Sensei für die Asset-Erkennung nutzen.

Adobe Experience Manager Assets verwendet einen Self-Learning-Algorithmus, um hochgradig beschreibende Tags zu erstellen, mit denen Sie das richtige Asset in nur wenigen Klicks finden können. Smart-Tagging nutzt Adobe Sensei, unsere künstliche Intelligenz und ein Framework für maschinelles Lernen, das trainiert werden kann, um standardmäßige und geschäftsspezifische Tags zu erkennen und auf Bilder anzuwenden. Smart-Tags können auch Inhalte, einzelne Wörter oder Ausdrücke identifizieren und automatisch beschreibende Tags auf Assets anwenden.

Weitere Informationen finden Sie in den folgenden Artikeln:

* [Über Tags in AEM](/help/sites-authoring/tags.md)
* [Bearbeiten von Asset-Metadaten](meta-edit.md)
* [Erweiterte Smart-Tags in Assets](enhanced-smart-tags.md)

## Organisieren als Sammlungen {#organize-as-collections}

Mit Asset-Sammlungen in Experience Manager Assets können Sie die Möglichkeit optimieren, Assets zu erstellen, zu bearbeiten und zwischen Benutzern freizugeben. Erstellen Sie verschiedene Arten von Sammlungen basierend auf ihrer Verwendung, einschließlich Sammlungen, die eine statische Referenzliste von Assets, Ordnern und Sammlungen enthalten, und Sammlungen, die Assets basierend auf Suchkriterien abrufen.  Sie können Sammlungen mit Assets aus verschiedenen Speicherorten erstellen und sie für mehrere Benutzer mit unterschiedlichen Stufen von Zugriffs-, Anzeige- und Bearbeitungsberechtigungen freigeben.

Weitere Informationen finden Sie unter [Sammlungen verwalten](managing-collections-touch-ui.md)

<!-- TBD items: add screenshots where applicable
Any hints/recommendations of when to use what method of organizing? Some examples of how organizing helps towards a better taxonomy and improved content velocity.
Add back links to blog posts by marketing?
-->

## Organisieren von Assets, um Profile zu verwenden {#organize-to-use-profiles}

Ein Verarbeitungsprofil enthält Asset-Verarbeitungsbefehle, die für Assets gelten, die in vordefinierte Ordner hochgeladen werden. Profile werden verwendet, um die Verarbeitung von Inhalten eines Ordners oder von neu hochgeladenen Assets zu automatisieren. Sie können Profile verwenden, um Ihre Assets besser zu organisieren.

Indem Sie die Verwendung von Metadaten, die Benennung von Dateien und die Ordnerstruktur standardisieren, wird sichergestellt, dass Sie auch bei einem stets wachsenden Pool mit digitalen Assets Verarbeitungsprofile präziser und konsistenter auf Ordner anwenden können.

Weitere Informationen zu verschiedenen Profilen, die Sie erstellen und verwalten können, um Assets zu verarbeiten, finden Sie unter

* [Profile zur Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md)
* [Metadatenprofile](metadata-profiles.md)
* [Videoprofile](video-profiles.md)
* [Dynamic Media-Bildprofile](image-profiles.md)
