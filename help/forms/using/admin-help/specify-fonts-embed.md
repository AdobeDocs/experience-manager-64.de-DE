---
title: Angeben der einzubettenden Schriftarten
seo-title: Specify fonts to embed
description: Erfahren Sie, wie Sie die einzubettenden Schriftarten angeben.
seo-description: Learn how to specify fonts to embed.
uuid: 02da5c00-0467-4633-a076-c36725cbfbad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 180f0448-d507-4b6d-bb8a-d12a434e1250
exl-id: e24f4123-bed3-4096-b3fb-22deb1c1e9b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 24%

---

# Angeben der einzubettenden Schriftarten{#specify-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können angeben, welche Schriftarten immer oder nie in die von Output verwendeten Formulare eingebettet werden. Das Einbetten von Schriftarten erhöht die Dateigröße der Formulare. Betten Sie ungewöhnliche Schriftarten ein, die Benutzer wahrscheinlich nicht auf ihren Systemen haben, und betten Sie keine gängigen Schriftarten ein, die sie installiert haben.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für die Ausgabe angegeben haben, setzt die Option &quot;Schrift einbetten&quot;in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Ausgabe“.
1. Geben Sie unter „Schrifteinbettungseinstellungen“ in das Feld „Schriftarten immer einbetten“ die Namen der Schriftarten (durch Kommas getrennt) ein, die in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nur dann in das generierte Formular eingebettet, wenn sie im Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option &quot;Schrift einbetten&quot;in der XCI-Datei aktiviert wurde, die an den Dienst übergeben wird. In diesem Fall werden alle im PDF verwendeten Schriftarten immer eingebettet.
1. Geben Sie in das Feld „Schriften nie einbetten“ die Namen der Schriftarten (durch Kommas getrennt) ein, die nicht in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nicht in die PDF eingebettet, selbst wenn sie auf der generierten PDF verwendet werden. Diese Einstellung wird ignoriert, wenn die Option &quot;Schrift einbetten&quot;in der XCI-Datei, die an den Dienst übergeben wird, deaktiviert wurde. In diesem Fall wird keine der im PDF verwendeten Schriftarten eingebettet.
1. Klicken Sie auf „Speichern“.
