---
title: Entfernen der Geometrixx Sites
seo-title: Removing the Geometrixx Sites
description: Erfahren Sie, wie Sie den Beispielinhalt des Geometrixx entfernen.
seo-description: Learn how to remove the sample Geometrixx content.
uuid: 07d20837-3375-4e64-bb07-3e4d10452335
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 56761a36-ce21-46e1-856f-75a7e94acae9
exl-id: 495031fb-b559-4071-abc4-93d238ce136d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 29%

---

# Entfernen der Geometrixx Sites{#removing-the-geometrixx-sites}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM enthält eine Reihe von Beispiel-Geometrixx-Websites. Sie können diese Beispielinhalte über den **Paket-Manager** entfernen.

Die einzelnen geometrixx-bezogenen Pakete sind:

* `cq-geometrixx-outdoors-ugc-pkg-*<version>*.zip`
* `cq-geometrixx-pkg-*<version>*.zip`
* `cq-content-mac-*<version>*.zip`
* `cq-geometrixx-login-pkg-*<version>*.zip`
* `cq-geometrixx-users-pkg-*<version>*.zip`
* `cq-geometrixx-workflow-pkg-*<version>*.zip`
* `cq-geometrixx-outdoors-pkg-*<version>*.zip`
* `cq-geometrixx-commons-pkg-*<version>*.zip`
* `cq-geometrixx-media-pkg-*<version>*.zip`

Um ein einzelnes Paket zu entfernen, klicken Sie einfach auf **Deinstallieren** auf das Paket.

Es gibt auch ein Super-Paket:

* `cq-geometrixx-all-pkg-5.6.12.zip`

Dieses Paket enthält alle oben genannten individuellen Pakete. Um alle geometrixx-bezogenen Inhalte gleichzeitig zu entfernen, klicken Sie auf **Deinstallieren** auf dieses Paket. Das Gesamtpaket wechselt in den Zustand „Deinstalliert“ und alle Einzelpakete verschwinden aus der Paket-Manager-Ansicht.

Sie verfügen nun über eine leere AEM-Instanz ohne jegliche Beispielwebsites.

>[!NOTE]
>
>Beim Upgrade werden Geometrixx-Sites automatisch neu installiert. Möglicherweise müssen Sie nach der Aktualisierung Geometrixx-Websites entfernen, wenn Sie diese Beispiele nicht benötigen.
