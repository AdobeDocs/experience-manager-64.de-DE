---
title: Angeben von XCI-Konfigurationsoptionen
seo-title: Specify XCI configuration options
description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen angeben.
seo-description: Learn how to specify XCI configuration options.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
exl-id: 5156bb1c-8ad6-498c-aaf7-6474ffa8c83c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 14%

---

# Angeben von XCI-Konfigurationsoptionen {#specify-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit Output können Sie eine benutzerdefinierte XCI-Datei angeben, die für die Wiedergabe verwendet wird. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output). Standardmäßig überschreibt Output einige der in der XCI-Datei angegebenen Optionen, darunter die folgenden:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die die Überschreibung für die oben aufgeführten Optionen abbrechen. In diesem Fall verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Ausgabe“.
1. Aktivieren oder deaktivieren Sie das Kontrollkästchen &quot;XCI-Systemstandardoptionen verwenden&quot;. Wenn diese Option aktiviert ist, verwendet Output seine Standardwerte für die Einstellungen &quot;packet&quot;, &quot;creator&quot;, &quot;manufacturer&quot;und &quot;compressObjectStream&quot;. Wenn diese Option deaktiviert ist, verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf Speichern.
