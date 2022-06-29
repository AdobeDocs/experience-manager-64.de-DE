---
title: XCI-Konfigurationsoptionen angeben
seo-title: Specify XCI configuration options
description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen festlegen.
seo-description: Learn how to specify XCI configuration options.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
exl-id: 5156bb1c-8ad6-498c-aaf7-6474ffa8c83c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 100%

---

# XCI-Konfigurationsoptionen angeben {#specify-xci-configuration-options}

Output ermöglicht Ihnen, eine benutzerdefinierte XCI-Datei anzugeben, die für die Wiedergabe verwendet werden soll. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).) Standardmäßig setzt Output einige der in der XCI-Datei festgelegten Optionen außer Kraft:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die das Außerkraftsetzen der oben angegebenen Optionen verhindern. In diesem Fall verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in der Administration-Console auf Services > Ausgabe.
1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen „XCI-Systemstandardoptionen verwenden“. Wenn diese Option ausgewählt ist, verwendet Output seine Standardwerte für die packets-, creator-, producer- und compressObjectStream-Einstellungen. Bei deaktivierter Option verwendet Output die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf Speichern.
