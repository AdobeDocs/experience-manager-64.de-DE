---
title: Verwalten von Bannern
seo-title: Managing Banners
description: Banner stellen normalerweise grafische Werbe-Links dar. Auf dieser Seite erfahren Sie mehr.
seo-description: Banners represent typically graphical promotional links. Follow this page to learn more.
uuid: 593fe2ef-84df-42e2-8a03-897fb67a896d
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: authoring-on-demand-services-app
discoiquuid: fb1abaa0-9c02-4f20-aa7c-073def067452
exl-id: 516a052d-dfe7-42fd-be38-397e92868814
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 6%

---

# Verwalten von Bannern{#managing-banners}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Inhaltsverwaltungsaktionen sind die Bausteine, mit denen Inhalte in einer Anwendung erstellt und verwaltet werden können. Die folgenden Aktionen werden für Inhalte in der Anwendung ausgeführt.

## Bannerübersicht {#banners-overview}

Banner stellen normalerweise grafische Werbe-Links dar.

>[!NOTE]
>
>Weitere Informationen zu den folgenden Themen in AEM Mobile-Apps finden Sie in den folgenden Ressourcen der Online-Hilfe:
>
>* [Designüberlegungen](https://helpx.adobe.com/digital-publishing-solution/help/design-app.html)
>
>* [Erstellen von Bannern](https://helpx.adobe.com/digital-publishing-solution/help/creating-banners.html)
>


## Erstellen eines Banners {#creating-a-banner}

Der allgemeine Workflow zum Erstellen eines Artikels sieht wie folgt aus:

1. Auswählen **Mobile** über die Seitenleiste aus.
1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie oben rechts im **Banner verwalten** Kachel.
1. Führen Sie die einzelnen Schritte des Assistenten aus, um mit der Erstellung des neuen Banners fortzufahren.
1. Wenn Sie bereit sind, klicken Sie auf **Erstellen**.
1. Ihr neues Banner wird im **Banner verwalten** Kachel.

![chlimage_1-6](assets/chlimage_1-6.gif)

## Importieren eines neuen Banners {#importing-a-new-banner}

Vorhandene On-Demand-Inhalte für Mobilgeräte können von Mobile On-Demand heruntergeladen (importiert) werden, um sie zu AEM. Dies ermöglicht die Bearbeitung und Anzeige lokaler Inhalte.

>[!NOTE]
>
>Beim Import sind keine Bilder enthalten.

Der Workflow zum Importieren eines neuen Artikels

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie oben rechts im **Banner verwalten** und wählen Sie &quot;Banner importieren&quot;aus.
1. Klicken **Importbanner** im Dialogfeld und dann Schließen.
1. Ihre On-Demand-Artikel für Mobilgeräte werden jetzt im **Banner verwalten** Kachel.

>[!CAUTION]
>
>Sie müssen zuerst eine Mobile On-Demand-Verbindung verknüpfen.

## Bearbeiten eines Banners {#editing-a-banner}

Verwenden Sie den integrierten AEM Drag &amp; Drop-Editor, um einen Artikel hinzuzufügen oder zu ändern. Komponenten wie Text und Bilder können hinzugefügt/entfernt werden. Bilder aus DAM-Assets können eingefügt werden.

>[!CAUTION]
>
>Im Editor können nur in AEM erstellte Banner geöffnet werden.

Der Workflow zum Bearbeiten eines Artikels:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie in der Kachel &quot;Banner verwalten&quot;ein aus AEM Quellen stammendes Banner aus.
1. Klicken Sie in der Listenansicht auf das hervorgehobene Banner, um es im Inhaltseditor zu öffnen.
1. Verwenden Sie den Inhaltseditor, um Bannerinhalte (Manuskripte, Bilder, Text usw.) zu ziehen.

### Anzeigen und Bearbeiten von Metadaten in einem Banner {#viewing-and-editing-the-metadata-within-a-banner}

Banner verfügen über zahlreiche Eigenschaften wie Titel, Beschreibungen und Bilder. Diese Aktion wird verwendet, um solche Eigenschaften anzuzeigen und zu ändern. Optional können diese Änderungen beim Speichern in Mobile On-Demand hochgeladen werden.

Allgemeiner Workflow zum Anzeigen/Bearbeiten eines Artikels:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie ein Banner aus dem **Banner verwalten** Kachel.

1. Wählen Sie in der Aktionsleiste **Eigenschaften** aus.
1. Zeigen Sie alle verfügbaren Metadaten für diesen Artikel an.
1. Bearbeiten Sie die Metadaten nach Bedarf und klicken Sie auf **Speichern** wann geschehen.
1. Optional können Sie die Änderungen sofort in Mobile On-Demand hochladen.

## Hochladen eines Banners {#uploading-a-banner}

Mit der Aktion &quot;Hochladen&quot;wird der ausgewählte Inhalt kopiert und zu einem Mobile On-Demand-Projekt hinzugefügt. Bereits vorhandene mobile On-Demand-Inhalte werden durch die neue Version ersetzt.

Der allgemeine Workflow zum Hochladen eines Banners:

1. Von **Mobile** wählen Sie Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Im **Banner verwalten** -Kachel ein Banner zum Hochladen auf Mobile On-Demand auswählen.
1. Fügen Sie bei Bedarf in der Listenansicht weitere Banner hinzu.
1. Auswählen **Hochladen** Klicken Sie in der Aktionsleiste auf Hochladen im Dialogfeld.
1. Ihre Banner werden jetzt in Mobile On-Demand hochgeladen.

![chlimage_1-7](assets/chlimage_1-7.gif)

## Löschen eines Banners {#deleting-a-banner}

Durch diesen Vorgang wird das ausgewählte Banner aus Mobile On-Demand und optional aus der lokalen AEM gelöscht.

Der allgemeine Workflow zum Löschen eines Banners:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie das zu löschende Banner im **Banner verwalten** Kachel.
1. Stellen Sie sicher, dass es in der Liste ausgewählt ist (wählen Sie nach Bedarf andere aus, die gelöscht werden sollen).
1. Klicken **Löschen** in der Aktionsleiste aus.
1. Überprüfen Sie, ob Sie sowohl AEM als auch Mobile On-Demand löschen möchten.
1. Klicken Sie auf **Löschen**.
1. Ihr Banner wird jetzt aus der Liste entfernt.

### Die nächsten Schritte {#the-next-steps}

Informationen zum Verwalten von Bannern finden Sie unter

* [Verwalten von Artikeln](/help/mobile/mobile-on-demand-managing-articles.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Veröffentlichung des Inhalts rückgängig machen](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
