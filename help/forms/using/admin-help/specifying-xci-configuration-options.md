---
title: Angeben der XCI-Konfigurationsoptionen
seo-title: Specifying XCI configuration options
description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen angeben.
seo-description: Learn how to specify XCI configuration options.
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
exl-id: 7a13b13f-3eee-4fc0-8957-bd42f43119e9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 14%

---

# Angeben der XCI-Konfigurationsoptionen {#specifying-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit Forms können Sie eine benutzerdefinierte XCI-Datei angeben, die für die Wiedergabe verwendet wird. (Siehe [Speicherorte für Forms konfigurieren](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms). Standardmäßig überschreibt Forms einige der in der XCI-Datei angegebenen Optionen, darunter die folgenden:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die das Außerkraftsetzen der oben aufgeführten Optionen verhindern. In diesem Fall verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Aktivieren oder deaktivieren Sie das Kontrollkästchen &quot;XCI-Systemstandardoptionen verwenden&quot;. Wenn diese Option aktiviert ist, verwendet Forms seine Standardwerte für die Einstellungen &quot;packet&quot;, &quot;creator&quot;, &quot;manufacturer&quot;und &quot;compressObjectStream&quot;. Wenn diese Option deaktiviert ist, verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf Speichern.
