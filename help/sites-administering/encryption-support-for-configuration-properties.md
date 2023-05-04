---
title: Verschlüsselungsunterstützung für Konfigurationseigenschaften
seo-title: Encryption Support for Configuration Properties
description: Verschlüsselungsunterstützung für Konfigurationseigenschaften
seo-description: null
uuid: 26dc5e46-9332-4d9b-8874-895b90391e8c
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: security
discoiquuid: 4e08c297-aa4b-44cf-84c8-1e11582d9ebb
exl-id: 077a940d-19de-4d19-ad99-61f465e68205
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 28%

---

# Verschlüsselungsunterstützung für Konfigurationseigenschaften{#encryption-support-for-configuration-properties}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Unterstützung für die Speicherung aller OSGi-Konfigurationseigenschaften in sicherer, verschlüsselter Form anstatt als Klartext. Das Formular in der Web Console-Benutzeroberfläche wird verwendet, um verschlüsselten Text aus Klartext mithilfe des systemweiten Übergeordneten Verschlüsselungsschlüssels zu erstellen.

Unterstützung für das OSGi-Konfigurations-Plugin wurde hinzugefügt, um die Eigenschaft zu entschlüsseln, bevor sie von einem Dienst verwendet wird.

>[!NOTE]
>
>Dienste, die einen verschlüsselten Wert erwarten, müssen die IsProtected-Prüfung verwenden, um zu sehen, ob der Wert verschlüsselt ist, bevor versucht wird, ihn zu entschlüsseln, da er möglicherweise bereits entschlüsselt wurde.

## Verschlüsselungsunterstützung aktivieren {#enabling-encryption-support}

Diese Schritte zeigen, wie Sie das SMTP-Kennwort für den Mail-Dienst verschlüsseln. Sie können diese Schritte für eine OSGi-Eigenschaft ausführen, die verschlüsselt werden soll.

1. Navigieren Sie zur AEM-Web-Konsole unter *https://&lt;Server-Adresse>:&lt;Serverport>/system/console/configMgr*
1. Gehen Sie in der oberen linken Ecke zu **Main - Crypto-Unterstützung.**

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. Die Seite **Adobe Experience Manager Web Console Crypto Support** wird angezeigt.

   ![screen_shot_2018-08-01at113417am](assets/screen_shot_2018-08-01at113417am.png)

1. Im **Nur Text** den Text der sensiblen Daten eingeben, die Sie schützen möchten.
1. Auswählen **Protect**. Der geschützte Text wird als verschlüsselter Text angezeigt.

   ![screen_shot_2018-08-01at113844am](assets/screen_shot_2018-08-01at113844am.png)

1. Kopieren Sie den geschützten Text aus Schritt 5 und fügen Sie ihn in den Wert des OSGi-Formulars ein. In diesem Beispiel wurde die **SMTP-Kennwort** wird zum *Day CQ Mail Service*.

   ![screen_shot_2016-12-18at105809pm](assets/screen_shot_2016-12-18at105809pm.png)

1. Speichern Sie die Eigenschaften des Day CQ Mail Service. Das SMTP-Kennwort wird jetzt als verschlüsselter Wert gesendet.

## Entschlüsselungsunterstützung {#decryption-support}

AEM stellt jetzt ein Configuration Plugin zum Entschlüsseln von Konfigurationseigenschaften bereit. Dieses AEM-Plug-in entschlüsselt und ruft automatisch die Klartext-Eigenschaften ab.
