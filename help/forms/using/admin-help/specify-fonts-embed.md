---
title: Einzubettende Schriften angeben
seo-title: Specify fonts to embed
description: Hier erfahren Sie, wie Sie Schriftarten angeben, die Sie einbetten möchten.
seo-description: Learn how to specify fonts to embed.
uuid: 02da5c00-0467-4633-a076-c36725cbfbad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 180f0448-d507-4b6d-bb8a-d12a434e1250
exl-id: e24f4123-bed3-4096-b3fb-22deb1c1e9b9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---

# Einzubettende Schriften angeben{#specify-fonts-to-embed}

Sie können angeben, welche Schriften immer oder nie in Formulare eingebettet werden sollen, die von Output verwendet werden. Das Einbetten von Schriften erhöht die Dateigröße von Formularen. Betten Sie ungewöhnliche Schriften ein, die Benutzer eher selten installiert haben, während gängige Schriften, die der Benutzer vermutlich installiert hat, nicht eingebettet werden sollten.

>[!NOTE]
>
>Wenn Sie eine benutzerdefinierte XCI-Datei für Output angegeben haben, setzt die Option „Schrift einbetten“ in der XCI-Datei diese Einstellungen außer Kraft. (Siehe [Dateispeicherorte für Output angeben](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. Klicken Sie in der Administration-Console auf Services > Ausgabe.
1. Geben Sie unter Schrifteinbettungseinstellungen in das Feld Schriftarten immer einbetten die Namen der Schriftarten ein (durch Kommas getrennt), die in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriften werden nur in dem erzeugten Formular eingebettet, wenn sie in dem Formular verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, aktiviert ist. In diesem Fall werden alle Schriften, die in der PDF-Datei verwendet werden, immer eingebettet.
1. Geben Sie in das Feld Schriften nie einbetten die Namen der Schriftarten ein (durch Kommas getrennt), die nicht in Formulare eingebettet werden sollen. Die von Ihnen angegebenen Schriften werden nicht in der PDF-Datei eingebettet, selbst wenn sie in der generierten PDF-Datei verwendet werden. Diese Einstellung wird ignoriert, wenn die Option „Schrift einbetten“ in der XCI-Datei, die an den Dienst übermittelt wird, deaktiviert ist. In diesem Fall wird keine der Schriften, die in der PDF-Datei verwendet werden, eingebettet.
1. Klicken Sie auf Speichern.
