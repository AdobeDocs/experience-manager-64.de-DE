---
title: Ersatzschriftarten konfigurieren
seo-title: Configuring fallback fonts
description: Erfahren Sie, wie Sie Ersatzschriftarten konfigurieren.
seo-description: Learn how to configure fallback fonts.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
feature: PDF Generator
exl-id: 6942b6fc-8d04-429f-8433-1ab74c68fcc1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 69%

---

# Ersatzschriftarten konfigurieren {#configuring-fallback-fonts}

Sie können die Datei „FontManagerResources.properties“ zum Zuordnen der AEM Forms-Standardschriftarten zu Ersatzschriftarten manuell konfigurieren, falls die Standardschriftarten auf dem Server nicht verfügbar sind. Diese Eigenschaftendatei ist in der Datei „adobe-fontmanager.jar“ enthalten.

>[!NOTE]
>
>Die Konfiguration der Ersatzschriftarten gilt auch für den Assembler-Dienst.

1. Navigieren Sie zum adobe-livecycle-*[appserver]*.ear-Datei im *[AEM-Forms-Stamm]* Ordner &quot;configurationManager/export&quot;, erstellen Sie eine Sicherungskopie und entpacken Sie das Original.
1. Suchen Sie die Datei „adobe-fontmanager.jar“ und dekomprimieren Sie sie.
1. Suchen Sie die Datei „FontManagerResources.properties“ und öffnen Sie sie in einem Texteditor.
1. Ändern Sie die Speicherorte und Namen der Standard- und Ersatzschriftarten den Anforderungen entsprechend und speichern Sie die Datei.

   Die Schriftarteinträge in der Datei &quot;FontManagerResources.properties&quot;sind relativ zum *[AEM-Forms-Stamm]* Ordner &quot;/fonts&quot;. Wenn Sie Schriftarten angeben, die keine AEM Forms-Standardschriftarten sind, müssen Sie diese in dieser Ordnerstruktur installieren (entweder in einem vorhandenen oder einem neu erstelltem Ordner).

   >[!NOTE]
   >
   >Wenn die angegebene Schriftart bzw. Standardschriftart kein spezifisches Unicode-Zeichen enthält oder nicht verfügbar ist, wird das Zeichen gemäß der folgenden Priorität in einer Ersatzschriftart ausgewählt:

   * Gebietsschemaspezifische Schriftart
   * ROOT-Schriftart, wenn kein Gebietsschema festgelegt ist
   * Allgemeine Schriftart, die gemäß der in der Tabelle mit den Ersatzschriftarten festgelegten Reihenfolge gesucht wird

1. Komprimieren Sie die Datei „adobe-fontmanager.jar“ neu.
1. Komprimieren Sie die adobe-livecycle-*[appserver]*.ear -Datei und stellen Sie sie dann entweder manuell oder durch Ausführen von Configuration Manager erneut bereit.

>[!NOTE]
>
>Verwenden Sie Configuration Manager nicht, um die adobe-livecycle-[appserver].ear -Datei, da sie Ihre Änderungen mit den Standardwerten für AEM Formulare überschreibt.
