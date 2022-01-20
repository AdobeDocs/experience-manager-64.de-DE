---
title: Installieren von Feature Pack 18912 für die Massenmigration von Assets
seo-title: Installing Feature Pack 18912 for bulk asset migration
description: Mit Feature Pack 18912 können Sie Assets entweder per FTP stapelweise erfassen oder Assets von Dynamic Media Classic nach Dynamic Media in AEM migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
seo-description: Feature pack 18912 lets you either bulk ingest assets by way of FTP, or migrate assets from Dynamic Media Classic to Dynamic Media in AEM. This optional feature pack is available from Adobe support.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: Configuration
role: Admin,User
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 15%

---

# Installieren von Feature Pack 18912 für die Massenmigration von Assets {#installing-feature-pack}

Die Installation von Feature Pack 18912 ist _optional_.

Mit Feature Pack 18912 können Sie Assets entweder per FTP AEM direkt in Dynamic Media - Scene7 aufnehmen oder Assets aus Dynamic Media Classic in den Dynamic Media - Scene7 -Modus migrieren AEM. Das Feature Pack finden Sie unter [Adobe Professional Services](https://www.adobe.com/de/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Sie können das Feature Pack zwar verwenden, um Assets eigenständig von Dynamic Media Classic in den Dynamic Media-Scene7-Modus zu migrieren, AEM Assets jedoch mit der FTP-Funktion in Dynamic Media Classic stapelweise zu migrieren, die Adobe jedoch nicht. *not* empfiehlt diese Methode aufgrund der Komplexität, die damit verbunden ist.
>
>Daher sind die Migrationspaket-Packs wie dieses *only* unterstützt als Teil eines Migrationsprojekts durch [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

Bevor Sie dieses Feature Pack installieren können, müssen Sie zunächst einen Dienstbenutzer erstellen und diese Informationen für die Adobe bereitstellen.

Siehe auch [Konfigurieren von Dynamic Media - Scene7-Modus](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html).

**So installieren Sie Feature Pack 18912 für die Massenmigration von Assets**,

1. Navigieren Sie in Ihrer AEM-Instanz zu **[!UICONTROL Tools > Sicherheit > Benutzer > Benutzer erstellen]**. Dieser Dienstbenutzer muss Lese-/Schreibberechtigungen für `/content/dam`.
1. Im **[!UICONTROL ID]** und **[!UICONTROL Passwort]** -Felder einen Benutzernamen und ein Kennwort eingeben; Beispiel: `FTP User`. Dieser Name wird in der Zeitleiste als der Benutzer angezeigt, der das Asset erstellt hat. Wenn ein Asset über FTP hochgeladen wird, gilt es als erstellt, wenn es auf den FTP-Server hochgeladen und in AEM gepusht wurde.
1. Kontakt [Adobe-Kundenunterstützung für Experience Manager](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) , um Zugriff auf Feature Pack 18912 zum Herunterladen anzufordern. Sie benötigen möglicherweise die folgenden Informationen, wenn Sie sich an den Support wenden:

   * Server-IP-Adresse für Ihre Autoreninstanz, einschließlich der Portnummer (standardmäßig ist die Portnummer 4502).
   * Benutzername und Kennwort AEM Dienstbenutzers aus dem vorherigen Schritt.

1. Der Adobe-Kundensupport für AEM bietet FTP-Anmeldedaten und Zugriff auf Feature Pack 18912.

1. Wenn Sie Feature Pack 18912 erhalten, installieren Sie es.

   Siehe [Arbeiten mit Paketen](/help/sites-administering/package-manager.md) für weitere Informationen zur Verwendung von Softwareverteilung und -paketen in AEM.
