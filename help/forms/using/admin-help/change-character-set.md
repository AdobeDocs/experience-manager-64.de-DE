---
title: Ändern des Zeichensatzes
seo-title: Change the character set
description: Sie können den Zeichensatz angeben, der zum Kodieren des Ausgabe-Streams verwendet wird. Erfahren Sie, wie Sie den Zeichensatz ändern können.
seo-description: You can specify the character set used to encode the output stream. Learn how you can change the character set.
uuid: ecb0c3ff-368c-4553-80e4-aa35fc15af62
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 811b31f8-5465-4fb2-b1f9-513936041771
exl-id: 7961efc6-4b11-423a-871d-7b37e3f36781
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 55%

---

# Ändern des Zeichensatzes {#change-the-character-set}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können den Zeichensatz angeben, der zum Kodieren des Ausgabe-Streams verwendet wird.

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Services > Ausgabe]**.
1. Wählen Sie unter „Internationalisierung“ in der Liste „Zeichensatz“ einen Zeichensatz aus. Diese Einstellung ist von den Parametern `TransformationFormat` und `PrintFormat` abhängig, die über die API festgelegt werden. Um einen anderen Zeichensatz als die aufgelisteten anzugeben, wählen Sie „Benutzerdefiniert“ aus und geben Sie in dem angezeigten Feld einen kodierten Wert ein.

   Wenn `TransformationFormat` den Wert „PDF“ oder „PDF/A“ oder wenn `PrintFormat` den Wert „PCL“, „PostScript“, „Zebra label“, „IPL“, „DPL“, „TPCL“, „GenericColorPCL“ oder „GenericPSLevel3“ hat, werden nur bestimmte Zeichensätze unterstützt.

   Der Zeichensatz muss ein gültiger kanonischer Name sein. Der Standardwert ist ISO-8859-1.

1. Klicken Sie auf **[!UICONTROL Speichern]**.
