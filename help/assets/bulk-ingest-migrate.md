---
title: Installieren von Feature Pack 18912 für die Migration von Massenelementen
seo-title: Installieren von Feature Pack 18912 für die Migration von Massenelementen
description: Mit dem Feature Pack 18912 können Sie Assets per FTP stapelweise erfassen oder Assets aus Dynamic Media Classic in AEM migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
seo-description: Mit dem Feature Pack 18912 können Sie Assets per FTP stapelweise erfassen oder Assets aus Dynamic Media Classic in AEM migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
translation-type: tm+mt
source-git-commit: b1603091bb05493c9cfffa6067f414f73774edb2
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 15%

---


# Installing feature pack 18912 for bulk asset migration {#installing-feature-pack}

The installation of feature pack 18912 is _optional_.

Mit dem Feature Pack 18912 können Sie Assets entweder per FTP AEM direkt in den Modus &quot;Dynamische Medien - Scene7&quot;stapeln oder Assets von Dynamische Medien Classic in den Modus &quot;Dynamische Medien - Scene7&quot;AEM migrieren. Das Feature Pack ist in [Adobe Professional Services](https://www.adobe.com/de/experience-cloud/consulting-services.html)erhältlich.

>[!NOTE]
>
>Es ist zwar möglich, mit dem Feature Pack eigene Assets von Dynamic Media Classic zum Dynamic Media - Scene7-Modus zu migrieren, AEM Assets jedoch mit der FTP-Funktion in Dynamic Media Classic zu migrieren, jedoch wird diese Methode aufgrund der damit verbundenen Komplexität *nicht* empfohlen.
>
>Daher werden Migrationspaket wie dieses *nur* im Rahmen eines Migrationsprojektes über [Adobe Professional Services](https://www.adobe.com/de/experience-cloud/consulting-services.html)unterstützt.

Bevor Sie dieses Feature Pack installieren können, müssen Sie zunächst einen Dienstbenutzer erstellen und diese Informationen für die Adobe bereitstellen.

See also [Configuring Dynamic Media - Scene7 mode](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html).

**So installieren Sie Feature Pack 18912 für die Massenmigration** von Assets

1. In your AEM instance, navigate to **[!UICONTROL Tools > Security > Users > Create User]**. This service user must have read/write permissions to `/content/dam`.
1. In the **[!UICONTROL ID]** and **[!UICONTROL Password]** fields, enter a user name and password; for example, `FTP User`. Dieser Name wird in der Zeitleiste als der Benutzer angezeigt, der das Asset erstellt hat. Wenn ein Asset über FTP hochgeladen wird, gilt es als erstellt, wenn es auf den FTP-Server hochgeladen und in AEM gepusht wurde.
1. Wenden Sie sich an den Enterprise Support von [Adobe, um Experience Manager](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) um Zugriff auf Feature Pack 18912 zum Herunterladen zu bitten. Möglicherweise benötigen Sie beim Kontakt mit dem Support die folgenden Informationen:

   * Server-IP-Adresse für Ihre Autoreninstanz, einschließlich der Anschlussnummer (standardmäßig ist die Anschlussnummer 4502).
   * AEM Dienstbenutzer-Benutzername und Kennwort aus dem vorherigen Schritt.

1. Adobe Enterprise Support for AEM bietet Ihnen die FTP-Anmeldeinformationen und Zugriff auf Feature Pack 18912.

1. Wenn Sie Feature Pack 18912 erhalten, installieren Sie es.

   See [How to work with packages](/help/sites-administering/package-manager.md) for more information on using Software Distribution and packages in AEM.
