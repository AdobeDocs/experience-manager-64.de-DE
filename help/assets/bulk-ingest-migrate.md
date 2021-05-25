---
title: Installieren von Feature Pack 18912 für die Massenmigration von Assets
seo-title: Installieren von Feature Pack 18912 für die Massenmigration von Assets
description: Mit Feature Pack 18912 können Sie Assets entweder per FTP stapelweise erfassen oder Assets aus Dynamic Media Classic in AEM zu Dynamic Media migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
seo-description: Mit Feature Pack 18912 können Sie Assets entweder per FTP stapelweise erfassen oder Assets aus Dynamic Media Classic in AEM zu Dynamic Media migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: Konfiguration
role: Administrator,Business Practitioner
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 16%

---

# Installieren von Feature Pack 18912 für die Massenmigration von Assets {#installing-feature-pack}

Die Installation von Feature Pack 18912 ist _optional_.

Mit Feature Pack 18912 können Sie Assets entweder per FTP AEM direkt in Dynamic Media - Scene7 aufnehmen oder Assets aus Dynamic Media Classic in den Dynamic Media - Scene7 -Modus migrieren AEM. Das Feature Pack ist unter [Adobe Professional Services](https://www.adobe.com/de/experience-cloud/consulting-services.html) verfügbar.

>[!NOTE]
>
>Sie können das Feature Pack zwar verwenden, um Assets eigenständig von Dynamic Media Classic in den Dynamic Media-Scene7-Modus zu migrieren, AEM Assets mit der FTP-Funktion in Dynamic Media Classic stapelweise migrieren. Aufgrund der Komplexität empfiehlt die Adobe jedoch *nicht* diese Methode.
>
>Daher werden Migrationspaket-Packs wie dieses *nur* im Rahmen eines Migrationsprojekts über [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html) unterstützt.

Bevor Sie dieses Feature Pack installieren können, müssen Sie zunächst einen Dienstbenutzer erstellen und diese Informationen für die Adobe bereitstellen.

Siehe auch [Konfigurieren von Dynamic Media - Scene7-Modus](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html).

**So installieren Sie Feature Pack 18912 für die Massenmigration von Assets**:

1. Navigieren Sie in Ihrer AEM-Instanz zu **[!UICONTROL Tools > Sicherheit > Benutzer > Benutzer erstellen]**. Dieser Dienstbenutzer muss über Lese-/Schreibberechtigungen für `/content/dam` verfügen.
1. Geben Sie in die Felder **[!UICONTROL ID]** und **[!UICONTROL Kennwort]** einen Benutzernamen und ein Kennwort ein. z. B. `FTP User`. Dieser Name wird in der Zeitleiste als der Benutzer angezeigt, der das Asset erstellt hat. Wenn ein Asset über FTP hochgeladen wird, gilt es als erstellt, wenn es auf den FTP-Server hochgeladen und in AEM gepusht wurde.
1. Wenden Sie sich an [Adobe Enterprise Support for Experience Manager](https://helpx.adobe.com/de/contact/enterprise-support.ec.html), um den Zugriff auf Feature Pack 18912 zum Herunterladen anzufordern. Sie benötigen möglicherweise die folgenden Informationen, wenn Sie sich an den Support wenden:

   * Server-IP-Adresse für Ihre Autoreninstanz, einschließlich der Portnummer (standardmäßig ist die Portnummer 4502).
   * Benutzername und Kennwort AEM Dienstbenutzers aus dem vorherigen Schritt.

1. Adobe Enterprise Support für AEM bietet Ihnen die FTP-Anmeldedaten und Zugriff auf Feature Pack 18912.

1. Wenn Sie Feature Pack 18912 erhalten, installieren Sie es.

   Weitere Informationen zur Verwendung von Software Distribution und Paketen in AEM finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md) .
