---
title: Konfigurieren von Ersatzschriftarten
seo-title: Configuring fallback fonts
description: Erfahren Sie, wie Sie Fallback-Schriftarten konfigurieren.
seo-description: Learn how to configure fallback fonts.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
feature: PDF Generator
exl-id: 6942b6fc-8d04-429f-8433-1ab74c68fcc1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 4%

---

# Konfigurieren von Ersatzschriftarten {#configuring-fallback-fonts}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können die Datei &quot;FontManagerResources.properties&quot;manuell konfigurieren, um die standardmäßigen AEM Forms-Schriftarten Fallback (oder Ersatz) zuzuordnen, wenn die Standardschriftarten nicht auf dem Server verfügbar sind. Diese Eigenschaftendatei befindet sich in der Datei &quot;adobe-fontmanager.jar&quot;.

>[!NOTE]
>
>Die Konfiguration von Ersatzschriftarten gilt auch für den Assembler-Dienst.

1. Navigieren Sie zum adobe-livecycle-*[appserver]*.ear-Datei im *[AEM-Forms-Stamm]* Ordner &quot;configurationManager/export&quot;, erstellen Sie eine Sicherungskopie und entpacken Sie das Original.
1. Suchen Sie die Datei &quot;adobe-fontmanager.jar&quot;und dekomprimieren Sie sie.
1. Suchen Sie die Datei &quot;FontManagerResources.properties&quot;und öffnen Sie sie in einem Texteditor.
1. Ändern Sie die Speicherorte und Namen der generischen und Fallback-Schriftart nach Bedarf und speichern Sie die Datei.

   Die Schriftarteinträge in der Datei &quot;FontManagerResources.properties&quot;sind relativ zum *[AEM-Forms-Stamm]* Ordner &quot;/fonts&quot;. Wenn Sie Schriftarten angeben, die keine standardmäßigen AEM Forms-Schriftarten sind, müssen Sie diese Schriftarten in dieser Ordnerstruktur installieren (entweder in einem vorhandenen Ordner oder in einem neu erstellten Ordner).

   >[!NOTE]
   >
   >Wenn die angegebene Schriftart oder Standardschriftart kein bestimmtes Unicode-Zeichen enthält oder nicht verfügbar ist, wird das Zeichen gemäß der folgenden Priorität aus einer Fallback-Schriftart übernommen:

   * Gebietsschemaspezifische Schriftart
   * ROOT-Schriftart, wenn Gebietsschema nicht festgelegt ist
   * Generische Schriftart, durchsucht nach der in der Fallback-Tabelle festgelegten Reihenfolge

1. Komprimieren Sie die Datei &quot;adobe-fontmanager.jar&quot;neu.
1. Komprimieren Sie die adobe-livecycle-*[appserver]*.ear -Datei und stellen Sie sie dann entweder manuell oder durch Ausführen von Configuration Manager erneut bereit.

>[!NOTE]
>
>Verwenden Sie Configuration Manager nicht, um die adobe-livecycle-[appserver].ear -Datei, da sie Ihre Änderungen mit den Standardwerten für AEM Formulare überschreibt.
