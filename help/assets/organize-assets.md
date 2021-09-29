---
title: Digitale Assets organisieren
description: Organisieren Sie Ihre digitalen Assets, Bilder, Dateien, Ordner usw. mithilfe von Experience Manager.
contentOwner: AG
feature: Asset Management,Search
role: User
exl-id: 41e083b3-e956-4346-9a99-008de2c6a169
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 19%

---

# Digitale Assets organisieren {#organize-digital-assets}

Alle digitalen Assets, Metadaten und Inhalte von Microsoft Office- und PDF-Dokumenten werden extrahiert und für die Suche aufbereitet. Die Suche ermöglicht weitreichende Filtermöglichkeiten für Assets und hält dabei vollständig die korrekten Berechtigungen ein. Metadaten werden in den Metadaten in Digital Asset Management ausführlich erläutert.

[!DNL Experience Manager] Assets unterstützt verschiedene Methoden zum Organisieren von Inhalten. Sie können sie hierarchisch mithilfe von Ordnern organisieren oder ungeordnet und ad hoc organisieren, beispielsweise mithilfe von Tags. Benutzer können Tags im DAM Asset Editor bearbeiten, in dem Teil-Assets, Ausgabeformate und Metadaten angezeigt werden.

## Organisieren von Assets in Ordnern {#organize-using-folders}

Die einfachste Möglichkeit zum Organisieren von Assets besteht darin, diese in Ordnern zu speichern. Dies entspricht dem Organisieren von Dateien in Ordnern in unserem lokalen Dateisystem. Weitere Informationen zum Erstellen und Verwalten von Ordnern finden Sie unter [Verwalten von Assets](managing-assets-touch-ui.md). Wie Sie Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie die Dateien in diesen Ordnern verarbeiten, kann erhebliche Auswirkungen auf die Verarbeitung dieser Assets haben. Durch die Verwendung konsistenter und angemessener Strategien für die Datei- und Ordnernamen sowie guter Metadatenpraktiken können Sie das gesamte digitale Asset-Repository optimal nutzen.

* In den meisten Fällen wächst Ihr digitales Asset-Repository ständig. Daher ist es wichtig, die Metadatenverwendung, die Ordnerstruktur und die Dateibenennung frühzeitig im Erstellungszyklus des Inhalts zu formalisieren.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Diese Konsistenz hilft Ihrem Prozess und der besseren Verwaltung Ihrer Assets. Beispielsweise können Sie mithilfe von Assets, die in den folgenden Ordnertypen platziert werden, geeignete [Profile für die Asset-Verarbeitung verwenden](processing-profiles.md):

   * **Entwicklungsordner** – enthalten digitale Assets, an denen Sie derzeit arbeiten.
   * **Kundenordner** – enthalten digitale Assets basierend auf Kunden oder Projektnamen.
   * **Primäre Ordner**  - enthalten digitale Quell-Assets in Originalform.
   * **Ausgabeformatordner** – enthalten Ausgabeformate und Kopien der digitalen Quell-Assets in Originalform.
   * **Dateigrößenordner** – enthalten digitale Assets basierend auf kleinen, mittleren oder großen Dateien.
   * **Bereitstellungsordner** – enthalten digitale Assets, die für die Veröffentlichung auf Ihrer Website bereit sind.
   * **Ordner vom Typ MIME**  - enthalten digitale Assets, die für MIME-Typen spezifisch sind, z. B. Bilder, Dokumente und Multimedia.
   * **Archivordner** – enthalten veraltete digitale Assets.
   * **Datumsbasierte Ordner** – enthalten digitale Assets basierend auf einem Erstellungsdatum oder dem letzten Änderungsdatum.

* Erstellen Sie einen Ordner mit Ordnern, die sich wahrscheinlich nicht ändern werden, damit Anpassungen oder Automatisierungen weiterhin funktionieren. Beispielsweise funktionieren die zugewiesenen Verarbeitungsprofile weiterhin.
* Wenn ein Asset bereits veröffentlicht ist und Sie [!DNL Experience Manager] verwenden, um das Asset in einen anderen Ordner zu verschieben und es von seinem neuen Speicherort aus erneut zu veröffentlichen, ist der ursprünglich veröffentlichte Asset-Speicherort weiterhin verfügbar, zusammen mit dem neu veröffentlichten Asset. Das ursprünglich veröffentlichte Asset ist jedoch *lost* bis [!DNL Experience Manager] und kann nicht rückgängig gemacht werden. Daher empfiehlt es sich, zunächst die Veröffentlichung eines Assets rückgängig zu machen und es dann in einen anderen Ordner zu verschieben.

## Organisieren von Assets mit Tags {#use-tags-to-organize-assets}

Mithilfe von Tags als Metadaten können Sie mühelos Assets suchen, Sammlungen mithilfe der Suchergebnisse erstellen, das Suchangebot für einige Assets verbessern und die KI-Algorithmen von Adobe Sensei für die Asset-Erkennung nutzen.

Adobe Experience Manager Assets verwendet einen Self-Learning-Algorithmus, um hochgradig beschreibende Tags zu erstellen, mit denen Sie das richtige Asset in nur wenigen Klicks finden können. Smart Tagging nutzt Adobe Sensei, unser KI-Intelligence- und maschinelles Lernframework, das trainiert werden kann, um Standard- und geschäftsspezifische Tags zu erkennen und auf Bilder anzuwenden. Smart-Tags können auch Inhalte, einzelne Wörter oder Ausdrücke identifizieren und automatisch beschreibende Tags auf Assets anwenden

Weitere Informationen finden Sie in den folgenden Artikeln:

* [Über Tags in AEM](/help/sites-authoring/tags.md)
* [Bearbeiten von Asset-Metadaten](meta-edit.md)
* [Verbesserte Smart-Tags in Assets](enhanced-smart-tags.md)

## Organisieren als Sammlungen {#organize-as-collections}

Mit Asset-Sammlungen in Experience Manager Assets können Sie Assets einfacher erstellen, bearbeiten und für mehrere Benutzer freigeben. Erstellen Sie verschiedene Arten von Sammlungen basierend auf ihrer Verwendung, einschließlich Sammlungen, die eine statische Referenzliste von Assets, Ordnern und Sammlungen enthalten, sowie Sammlungen, die Assets basierend auf Suchkriterien abrufen.  Sie können auch Sammlungen mit Assets aus verschiedenen Speicherorten erstellen und sie für mehrere Benutzer mit unterschiedlichen Zugriffs-, Anzeige- und Bearbeitungsberechtigungen freigeben.

Weitere Informationen finden Sie unter [Verwalten von Sammlungen](managing-collections-touch-ui.md)

<!-- TBD items: add screenshots where applicable
Any hints/recommendations of when to use what method of organizing? Some examples of how organizing helps towards a better taxonomy and improved content velocity.
Add back links to blog posts by marketing?
-->

## Organisieren von Assets zur Verwendung von Profilen {#organize-to-use-profiles}

Ein Verarbeitungsprofil enthält Asset-Verarbeitungsbefehle, die für Assets gelten, die in vordefinierte Ordner hochgeladen werden. Profile werden verwendet, um die Verarbeitung von Inhalten eines Ordners oder von neu hochgeladenen Assets zu automatisieren. Sie können Profile nutzen, um Ihre Assets besser zu organisieren.

Durch die Standardisierung der Metadatennutzung, Dateibenennung und Ordnerstruktur wird sichergestellt, dass Sie bei einem wachsenden Pool digitaler Assets Verarbeitungsprofile präziser und konsistenter auf Ordner anwenden können.

Weitere Informationen zu verschiedenen Profilen, die Sie erstellen und verwalten können, um Assets zu verarbeiten, finden Sie unter

* [Profile zur Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md)
* [Metadatenprofile](metadata-profiles.md)
* [Videoprofile](video-profiles.md)
* [Dynamic Media-Bildprofile](image-profiles.md)
