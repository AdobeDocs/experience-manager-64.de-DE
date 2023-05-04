---
title: Verfassen einer Seite für Mobilgeräte
seo-title: Authoring a Page for Mobile Devices
description: Beim Authoring für Mobilgeräte können Sie zwischen mehreren Emulatoren wechseln, um zu sehen, was der Endbenutzer sieht
seo-description: When authoring for mobile, you can switch between several emulators to see what the end-user sees
uuid: a7a1ba68-d608-4819-88d1-0dab5955d3f4
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 9554cdb3-b604-4d50-9760-89b9e7a7755f
exl-id: 97f0b0d2-7d7b-4a90-a4e5-348a306e1622
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 54%

---

# Verfassen einer Seite für Mobilgeräte{#authoring-a-page-for-mobile-devices}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen mehreren Emulatoren wechseln, um zu sehen, was der Endbenutzer beim Zugriff auf die Seite sieht.

Geräte sind entsprechend ihrer Fähigkeit zur Wiedergabe einer Seite in die Kategorien „Feature“, „Smart“ und „Touch“ eingeteilt. Wenn der Endbenutzer auf eine mobile Seite zugreift, erkennt AEM das Gerät und sendet die Darstellung, die der Gerätegruppe entspricht.

>[!NOTE]
>
>Zur Erstellung einer Website für Mobilgeräte auf der Grundlage einer bestehenden Standard-Site erstellen Sie eine Live Copy der Standard-Site. (Siehe [Erstellen einer Live Copy für unterschiedliche Kanäle](/help/sites-administering/msm-livecopy.md).)
>
>AEM-Entwickler können neue Gerätegruppen erstellen. (Siehe [Erstellen von Gerätegruppen-Filtern](/help/sites-developing/groupfilters.md).)

Gehen Sie wie folgt vor, um eine Seite für Mobilgeräte zu erstellen:

1. Öffnen Sie ausgehend von der globalen Navigation die **Sites-Konsole**.
1. Öffnen Sie die Seite **We.Retail** > **Vereinigte Staaten** > **Englisch**.

1. Wechseln Sie in den **Vorschaumodus**.
1. Wechseln Sie zum gewünschten Emulator, indem Sie auf das Gerätesymbol oben auf der Seite klicken.
1. Ziehen Sie Komponenten aus dem Komponenten-Browser auf die Seite.

Die Seite sieht in etwa wie folgt aus:

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>Die Emulatoren sind deaktiviert, wenn eine Seite in der Autoreninstanz von einem Mobilgerät aus aufgerufen wird.
