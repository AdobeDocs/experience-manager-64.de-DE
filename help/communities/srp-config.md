---
title: Speicherkonfiguration
seo-title: Storage Configuration
description: Zugriff auf die Speicherkonfigurationskonsole
seo-description: How to access the Storage Configuration Console
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Admin
exl-id: 905b6dc5-cf17-4f58-a687-27e2910a0729
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 6%

---

# Speicherkonfiguration {#storage-configuration}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit der Speicherkonfiguration wird der für Community-Inhalte ausgewählte Speicher identifiziert, der auch als benutzergenerierte Inhalte (UGC) bezeichnet wird.

Diese Einstellung informiert den AEM Communities-Code darüber, welche Implementierung des Speicherressourcenanbieters (SRP) beim Zugriff auf UGC verwendet werden soll, und muss die bei der Bereitstellung von AEM festgelegte Topologie widerspiegeln.

Eine Diskussion der Speicheroptionen und Bereitstellungstopologien finden Sie unter

* [Community-Inhaltsspeicher](working-with-srp.md)
* [Empfohlene Topologien](topologies.md)

## Speicherkonfigurationskonsole {#storage-configuration-console}

![chlimage_1-188](assets/chlimage_1-188.png)

In der Autorenumgebung, um die Speicherkonfigurationskonsole zu erreichen

* Über die globale Navigation: **[!UICONTROL Tools > Communities > Speicherkonfiguration]**

So wählen Sie eine andere Speicheroption als das standardmäßige JCR aus:

* Auswählen einer Option
* Geeignete Konfiguration

   * Siehe Details für [Auswählen von MSRP](msrp.md#select-msrp)
   * Siehe Details für [Auswahl von DSRP](dsrp.md#select-dsrp)
   * Siehe Details für [Auswählen von ASRP](asrp.md#select-asrp)

* Klicken Sie auf **[!UICONTROL Übermitteln]**

### Über JCR-Speicher {#about-jcr-storage}

Beachten Sie, dass bei fehlender Auswahl das AEM-Repository JCR standardmäßig verwendet wird.

JCR ist *not* ein gemeinsamer Speicher, der von der Autoren- und Veröffentlichungsumgebung gemeinsam genutzt wird. Community-Inhalte sind nur in der Autoren- oder Veröffentlichungsumgebung sichtbar, in der sie erstellt wurden.

Besuch [JCR-Store](jsrp.md) für weitere Informationen.

>[!NOTE]
>
>Das Fehlen des Knotens `srpc`under `/etc/socialconfig` gibt den Standardwert an [JCR-Store](jsrp.md).
