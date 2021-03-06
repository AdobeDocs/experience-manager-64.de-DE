---
title: Verfassen einer Seite für Mobilgeräte
seo-title: Authoring a Page for Mobile Devices
description: Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen verschiedenen Emulatoren wechseln, um zu sehen, was der Endbenutzer sieht, wenn auf er die Seite zugreift.
seo-description: When authoring a mobile page, the page is displayed in a way that emulates the mobile device. When authoring the page, you can switch between several emulators to see what the end-user sees when accessing the page.
uuid: ca16979d-6e5f-444d-b959-ae92542039b2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 430a27b5-f344-404f-8bf8-0d91b49b605e
exl-id: 26324f89-f5e2-40bc-96b4-0f3faa08bdd1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 91%

---

# Verfassen einer Seite für Mobilgeräte{#authoring-a-page-for-mobile-devices}

Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen verschiedenen Emulatoren wechseln, um zu sehen, was der Endbenutzer sieht, wenn auf er die Seite zugreift.

Geräte sind entsprechend ihrer Fähigkeit zur Wiedergabe einer Seite in die Kategorien „Feature“, „Smart“ und „Touch“ eingeteilt. Wenn der Endbenutzer auf eine Seite für Mobilgeräte zugreift, ermittelt AEM das entsprechende Gerät und sendet die zu der entsprechenden Gerätegruppe gehörige Version der Seite.

>[!NOTE]
>
>Zur Erstellung einer Website für Mobilgeräte auf der Grundlage einer bestehenden Standard-Site erstellen Sie eine Live Copy der Standard-Site. (Siehe [Erstellen einer Live Copy für verschiedene Kanäle](/help/sites-administering/msm-livecopy.md).
>
>AEM-Entwickler können neue Gerätegruppen erstellen. (Siehe [Erstellen von Gerätegruppenfiltern.](/help/sites-developing/groupfilters.md))

Gehen Sie wie folgt vor, um eine Seite für Mobilgeräte zu erstellen:

1. Rufen Sie im Browser die Konsole **Siteadmin** auf.
1. Öffnen Sie die Seite **Produkte** unterhalb von **Websites** >> **Geometrixx Mobile Demo Site**  >>  **Englisch**.

1. Wechseln Sie zu einem anderen Emulator. Dazu haben Sie folgende Möglichkeiten:

   * Klicken auf das Gerätesymbol am oberen Seitenrand.
   * Klicken auf die Schaltfläche **Bearbeiten** im **Sidekick** und Auswahl des Geräts im Dropdown-Menü.

1. Ziehen Sie die Komponente **Text &amp; Bild** aus der Registerkarte „Mobil“ des Sidekicks der Seite und legen Sie sie ab.
1. Bearbeiten Sie die Komponente und fügen Sie Text hinzu. Klicken Sie auf **OK**, um die Änderungen zu speichern.

Die Seite nimmt die folgende Gestalt an:

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>Die Emulatoren sind deaktiviert, wenn eine Seite in der Autoreninstanz von einem Mobilgerät aus aufgerufen wird. Die Bearbeitung kann dann über die Touch-optimierte Benutzeroberfläche erfolgen.
