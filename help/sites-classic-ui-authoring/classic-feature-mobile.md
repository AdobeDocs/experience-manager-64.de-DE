---
title: Verfassen einer Seite für Mobilgeräte
seo-title: Authoring a Page for Mobile Devices
description: Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen mehreren Emulatoren wechseln, um zu sehen, was der Endbenutzer beim Zugriff auf die Seite sieht.
seo-description: When authoring a mobile page, the page is displayed in a way that emulates the mobile device. When authoring the page, you can switch between several emulators to see what the end-user sees when accessing the page.
uuid: ca16979d-6e5f-444d-b959-ae92542039b2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 430a27b5-f344-404f-8bf8-0d91b49b605e
exl-id: 26324f89-f5e2-40bc-96b4-0f3faa08bdd1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 50%

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

1. Navigieren Sie in Ihrem Browser zum **Siteadmin** Konsole.
1. Öffnen Sie die Seite **Produkte** unterhalb von **Websites** >> **Geometrixx Mobile Demo Site** >> **Englisch**.

1. Wechseln Sie zu einem anderen Emulator. Dazu haben Sie folgende Möglichkeiten:

   * Klicken Sie oben auf der Seite auf das Gerätesymbol.
   * Klicken Sie auf **Bearbeiten** im **Sidekick** und wählen Sie das Gerät im Dropdown-Menü aus.

1. Ziehen Sie die **Text und Bild** auf der Registerkarte &quot;Mobil&quot;des Sidekicks zur Seite hinzugefügt.
1. Bearbeiten Sie die Komponente und fügen Sie Text hinzu. Klicken Sie auf **OK**, um die Änderungen zu speichern.

Die Seite sieht wie folgt aus:

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>Die Emulatoren sind deaktiviert, wenn eine Seite in der Autoreninstanz von einem Mobilgerät aus aufgerufen wird. Das Erstellen kann in diesem Fall in der Touch-optimierten Benutzeroberfläche erfolgen.
