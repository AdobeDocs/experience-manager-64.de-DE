---
title: Speicher  Konfiguration
seo-title: Speicher  Konfiguration
description: Zugriff auf die Datenspeicherung Configuration Console
seo-description: Zugriff auf die Datenspeicherung Configuration Console
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 4%

---


# Speicherkonfiguration {#storage-configuration}

Die Konfiguration der Datenspeicherung ist das Mittel zur Identifizierung der Datenspeicherung, die für Community-Inhalte gewählt wurde, auch als benutzergenerierte Inhalte (UGC) bezeichnet.

Diese Einstellung informiert den AEM Communities-Code darüber, welche Implementierung des Datenspeicherung Resource Provider (SRP) beim Zugriff auf UGC verwendet werden soll, und muss die bei der Bereitstellung der AEM festgelegte Topologie widerspiegeln.

Eine Diskussion der Optionen für die Datenspeicherung und der Bereitstellungstopologien finden Sie unter

* [Community Content Store](working-with-srp.md)
* [Empfohlene Topologien](topologies.md)

## Datenspeicherung Configuration Console {#storage-configuration-console}

![chlimage_1-188](assets/chlimage_1-188.png)

In der Umgebung &quot;author&quot;zur Datenspeicherung-Konfigurationskonsole

* Aus globaler Navigation: **[!UICONTROL Tools > Communities > Datenspeicherung Configuration]**

So wählen Sie eine andere Datenspeicherung als die Standard-JCR-Option aus:

* Option auswählen
* Passend konfigurieren

   * Siehe Details zu [Auswahl von MSRP](msrp.md#select-msrp)
   * Siehe Details zur Auswahl von DSRP](dsrp.md#select-dsrp)[
   * Siehe Details zur Auswahl von ASRP](asrp.md#select-asrp)[

* Klicken Sie auf **[!UICONTROL Übermitteln]**

### Informationen zur JCR-Datenspeicherung {#about-jcr-storage}

Beachten Sie, dass bei fehlender Auswahl das AEM Repository JCR standardmäßig verwendet wird.

JCR ist *nicht* ein gemeinsamer Speicher, der von den Autor- und Veröffentlichungs-Umgebung freigegeben wird. Der Community-Inhalt ist nur von der Autor- oder Veröffentlichungsdatei sichtbar, in der er erstellt wurde.

Weitere Informationen finden Sie unter [JCR Store](jsrp.md).

>[!NOTE]
>
>Das Fehlen des Knotens `srpc`unter `/etc/socialconfig` gibt den standardmäßigen [JCR-Speicher](jsrp.md) an.

