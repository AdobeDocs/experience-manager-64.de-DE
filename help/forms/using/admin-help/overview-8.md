---
title: Überblick über den Ausgabe-Service
seo-title: Overview of output service
description: Mit der Ausgabe können Sie XML-Formulardaten mit einem in Designer erstellten Formularentwurf zusammenführen, um einen Dokumentausgabestream in verschiedenen Formaten zu erstellen.
seo-description: Output lets you merge XML form data with a form design created in Designer to create a document output stream in various formats.
uuid: 7890b0a6-bae5-4ad5-ae41-503b988ba3da
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5a96f5ea-6fe3-44b1-b314-14097b9e9c01
exl-id: 00ca8bdf-77be-4f4c-a3d3-d61d13eeba7e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 10%

---

# Überblick über den Ausgabe-Service {#overview-of-output-service}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit der Ausgabe können Sie XML-Formulardaten mit einem in Designer erstellten Formularentwurf zusammenführen, um einen Dokumentausgabestream in verschiedenen Formaten zu erstellen. Der Ausgabestream kann an einen Netzwerkdrucker, einen lokalen Drucker oder eine Festplattendatei gesendet werden

Sie können die Output-Seite in Administration Console verwenden, um den Output-Dienst zu verwalten. Die konfigurierten Einstellungen werden zur Laufzeit verwendet, wenn die entsprechenden Einstellungen nicht über die AEM Forms-API angegeben wurden. Die über das AEM Forms SDK vorgenommene Konfiguration setzt die mithilfe von Administration Console konfigurierten Einstellungen außer Kraft.

Weitere Informationen zum Output-Dienst finden Sie unter [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_61_de).

Auf den Output-Seiten in Administration Console können Sie mehrere Aufgaben ausführen:

* Geben Sie Zeichensätze für die Internationalisierung an. (Siehe [Zeichensatz ändern](/help/forms/using/admin-help/change-character-set.md#change-the-character-set).
* Geben Sie absolute und relative Pfade für URLs, URIs, XCIs und Dateispeicherorte an. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).
* Konfigurieren Sie die Cachegrößen und -richtlinien. (Siehe [Festlegen des Cache-Modus](/help/forms/using/admin-help/configuring-caching-output.md#specifying-the-cache-mode) und [Cache-Einstellungen konfigurieren](/help/forms/using/admin-help/configuring-caching-output.md#configuring-cache-settings).
* Stellen Sie Schriftarten auf dem Anwendungsserver zur Verfügung. (Siehe [Schriftarten verfügbar machen](/help/forms/using/admin-help/make-fonts-available.md#make-fonts-available).
* Geben Sie die einzubettenden Schriften an. (Siehe [Einzubettende Schriften angeben](/help/forms/using/admin-help/specify-fonts-embed.md#specify-fonts-to-embed).
* Geben Sie die XCI-Konfigurationsoptionen an. (Siehe [XCI-Konfigurationsoptionen angeben](/help/forms/using/admin-help/specify-xci-configuration-options.md#specify-xci-configuration-options).
* Geben Sie die Sicherheitseinstellungen an. (Siehe [Sicherheitseinstellungen festlegen](/help/forms/using/admin-help/specify-security-settings.md#specify-security-settings).

Nachdem Sie die Einstellungen geändert haben, klicken Sie auf Speichern , um sie auf Output anzuwenden. Sie müssen den Server nicht neu starten, damit die Änderungen wirksam werden. Möglicherweise müssen Sie den Output-Dienst jedoch beim Konfigurieren der Cacheeinstellungen neu starten.
