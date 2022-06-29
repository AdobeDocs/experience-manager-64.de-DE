---
title: XCI-Konfigurationsoptionen angeben
seo-title: Specifying XCI configuration options
description: Erfahren Sie, wie Sie XCI-Konfigurationsoptionen festlegen.
seo-description: Learn how to specify XCI configuration options.
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
exl-id: 7a13b13f-3eee-4fc0-8957-bd42f43119e9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 100%

---

# XCI-Konfigurationsoptionen angeben {#specifying-xci-configuration-options}

Forms ermöglicht Ihnen, eine benutzerdefinierte XCI-Datei anzugeben, die für die Wiedergabe verwendet werden soll. (Siehe [Speicherorte für Forms konfigurieren](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Standardmäßig setzt Forms einige der in der XCI-Datei festgelegten Optionen außer Kraft:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Sie können Optionen auswählen, die das Außerkraftsetzen der oben angegebenen Optionen verhindern. In diesem Fall verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.

1. Klicken Sie in der Administration-Console auf Services > Forms.
1. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen „XCI-Systemstandardoptionen verwenden“. Wenn diese Option ausgewählt ist, verwendet Forms seine Standardwerte für die packets-, creator-, producer- und compressObjectStream-Einstellungen. Bei deaktivierter Option verwendet Forms die in der benutzerdefinierten XCI-Datei angegebenen Werte.
1. Klicken Sie auf Speichern.
