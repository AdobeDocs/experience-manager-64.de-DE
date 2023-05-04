---
title: Angeben der einzubettenden Schriften
seo-title: Specifying fonts to embed
description: Erfahren Sie, wie Sie die einzubettenden Schriftarten angeben.
seo-description: Learn how to specify fonts to embed.
uuid: 97de6f98-ed3b-4a93-854a-193a967b4672
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4c83694c-b00f-40be-9ac4-f5785cd60741
exl-id: 0bde7192-9d21-40b4-9164-314c9a30153b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 24%

---

# Angeben der einzubettenden Schriften {#specifying-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können angeben, welche Schriftarten immer oder nie in die Formulare eingebettet werden, die der Forms-Dienst generiert. Das Einbetten von Schriftarten erhöht die Dateigröße der Formulare. Betten Sie ungewöhnliche Schriftarten ein, die Benutzer selten auf ihren Systemen haben. Betten Sie keine gängigen Schriftarten ein, die sie normalerweise installiert haben.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für Forms angegeben haben, setzt die Option &quot;Schrift einbetten&quot;in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Speicherorte für Forms konfigurieren](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Services > Forms]**.
1. Geben Sie unter **[!UICONTROL Schrifteinbettungseinstellungen]** in das Feld **[!UICONTROL Schriftarten immer einbetten]** die Namen der Schriftarten ein (durch Kommas getrennt), die in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nur dann in das generierte Formular eingebettet, wenn sie im Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option &quot;Schrift einbetten&quot;in der XCI-Datei aktiviert wurde, die an den Dienst übergeben wird, da in diesem Fall alle Schriften, die auf dem PDF verwendet werden, immer eingebettet werden.
1. Geben Sie in das Feld **[!UICONTROL Schriften nie einbetten]** die Namen der Schriftarten ein (durch Kommas getrennt), die nicht in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriftarten werden nicht in die PDF eingebettet, selbst wenn sie auf der generierten PDF verwendet werden. Diese Einstellung wird ignoriert, wenn die Option &quot;Schrift einbetten&quot;in der XCI-Datei, die an den Dienst übergeben wird, deaktiviert wurde, da in diesem Fall keine der im PDF verwendeten Schriften eingebettet ist.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
