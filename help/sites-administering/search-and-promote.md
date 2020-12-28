---
title: Integrieren mit Adobe Search&Promote
seo-title: Integrieren mit Adobe Search&Promote
description: Erfahren Sie, wie Sie eine Integration mit Adobe Search&Promote vornehmen können.
seo-description: Erfahren Sie, wie Sie eine Integration mit Adobe Search&Promote vornehmen können.
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 55%

---


# Integrieren mit Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

Führen Sie zum Abrufen des Dienstes Adobe Search&amp;Promote von unserer Website die folgenden Aufgaben durch:

1. Geben Sie die URL der Cloud an.
1. Konfigurieren Sie die Verbindung mit dem Search&amp;Promote-Dienst.
1. hinzufügen Sie die Search&amp;Promote auf [!UICONTROL Sidekick].
1. Verwenden Sie die Komponenten für die Bearbeitung des Inhalts. (Siehe [Hinzufügen von Search&amp;Promote-Funktionen zu einer Webseite](/help/sites-authoring/search-and-promote.md).)
1. Fügen Sie Ihren Seiten Banner hinzu. Bannerbilder reagieren auf Search&amp;Promote-Daten.
1. Generieren Sie eine Sitemap für den Search&amp;Promote-Dienst.

>[!NOTE]
>
>Wenn Sie Search&amp;Promote mit einer benutzerdefinierten Proxy-Konfiguration verwenden, müssen Sie beide HTTP-Client-Proxy-Konfigurationen vornehmen, da manche AEM-Funktionen 3.x-APIs verwenden und andere wiederum 4.x-APIs:
>
>* 3.x wird mit [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) konfiguriert.
>* 4.x wird mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) konfiguriert.

>



## Ändern der URL des Search&amp;Promote-Diensts {#changing-the-search-promote-service-url}

Die Standard-URL, die für den Search&amp;Promote-Dienst konfiguriert ist, ist `https://searchandpromote.omniture.com/px/`. Verwenden Sie zur Verwendung eines anderen Diensts die OSGi-Konsole, um eine andere URL anzugeben.

**So ändern Sie die URL** des Search&amp;Promote:

1. Öffnen Sie die Konsole [!UICONTROL OSGi] und tippen Sie auf die Registerkarte **[!UICONTROL Konfiguration]**. ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. Klicken Sie auf das Element **[!UICONTROL Day CQ Search&amp;Promote Configuration]**.
1. Geben Sie im Textfeld **[!UICONTROL Remote-Server-URI]** die URL ein und tippen Sie dann auf **[!UICONTROL Speichern]**.

## Konfigurieren der Verbindung mit Search&amp;Promote {#configuring-the-connection-to-search-promote}

Konfigurieren Sie eine oder mehrere Verbindungen mit Search&amp;Promote, sodass Ihre Webseiten mit dem Dienst interagieren können. Für die Verbindung benötigen Sie die Mitgliedsidentifikations- und Kontonummer Ihres Search&amp;Promote-Kontos.

**So konfigurieren Sie die Verbindung zu Search&amp;Promote**:

1. Wählen Sie unter **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** **[!UICONTROL Cloud Services]** aus.

   Hierdurch werden Sie zum Dashboard der Cloud-Services weitergeleitet. Wenn auf einem lokalen Computer die URL des Dashboards in etwa wie folgt aussieht:

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. Tippen Sie auf der Seite [!UICONTROL Cloud Services] auf den Link **[!UICONTROL Adobe Search&amp;Promote]** oder auf das Symbol **[!UICONTROL Search&amp;Promote]**.

1. Wenn Sie die Search&amp;Promote der Adobe zum ersten Mal konfigurieren, tippen Sie auf **[!UICONTROL Jetzt konfigurieren]**, um das Bedienfeld [!UICONTROL Konfiguration erstellen] zu öffnen.

   Wenn Sie mehr über Search&amp;Promote erfahren möchten, klicken Sie stattdessen auf **[!UICONTROL Weitere Informationen]**.

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. Geben Sie einen **[!UICONTROL Titel]** ein, der für Seitenautoren erkennbar ist, und geben Sie einen eindeutigen **[!UICONTROL Name]** ein und tippen Sie dann auf **[!UICONTROL Erstellen]**.

   Darüber hinaus wird die neu erstellte Konfiguration unter **[!UICONTROL Verfügbare Konfigurationen]** im **[!UICONTROL Cloud-Services-Dashboard]** des Adobe Search&amp;Promote-Listenelements angezeigt.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. Fügen Sie im Dialogfeld [!UICONTROL Komponente bearbeiten] Folgendes zu den Feldern hinzu:

   * **[!UICONTROL Mitglieds-ID]**
   * **[!UICONTROL Kontonummer]**

   >[!NOTE]
   >
   >Um diese Informationen selbst zu erhalten, melden Sie sich an bei:
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >mithilfe Ihrer gültigen Seach&amp;Promote-Zugriffsberechtigung (E-Mail/Kennwort) anmelden.
   >
   >Beachten Sie die URL in der Adressleiste Ihres Browsers. Es sollte in etwa wie folgt aussehen:
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >Dabei entspricht **XXXXXX** Ihrer **[!UICONTROL Mitglieds-ID]** und **[!UICONTROL spYYYYYY]** Ihrer Kontonummer.

1. Tippen Sie auf **[!UICONTROL Mit Search&amp;Promote]** verbinden.

   Wenn die Verbindungserfolgmeldung angezeigt wird, tippen Sie auf **[!UICONTROL OK]**.

   (Nach der Verbindung ändert sich der Schaltflächen-Text zu **[!UICONTROL Erneut mit Search&amp;Promote verbinden]**.)

1. Tippen Sie auf **[!UICONTROL OK]**. Die Seite mit den Search&amp;Promote-Einstellungen wird für die gerade von Ihnen erstellte Konfiguration angezeigt.

## Konfigurieren des Datenzentrums {#configuring-the-data-center}

Wenn sich Ihr Search&amp;Promote in Asien oder Europa befindet, müssen Sie das Standarddatencenter so ändern, dass es auf das richtige verweist (das Standarddatencenter gilt für Nordamerika-Konten).

**Sie können das Datenzentrum wie folgt konfigurieren**:

1. Navigieren Sie zur Webkonsole unter `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. Ändern Sie den URI je nach Standort des Servers in einen der folgenden:

   * Nordamerika: [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC: [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. Tippen Sie auf **[!UICONTROL Speichern]**.

## Hinzufügen von Search&amp;Promote-Komponenten zum Sidekick {#adding-search-promote-components-to-sidekick}

Bearbeiten Sie im Modus [!UICONTROL Design] die Komponente **[!UICONTROL par]**, um die Search&amp;Promote in [!UICONTROL Sidekick] zuzulassen. (In der Dokumentation zu den [Komponenten](/help/sites-developing/components.md) finden Sie weitere Informationen.)

Informationen zur Verwendung der Komponenten finden Sie unter [Hinzufügen von Search&amp;Promote zu einer Webseite](/help/sites-authoring/search-and-promote.md).

## Angeben des von Ihren Seiten verwendeten Search&amp;Promote-Dienstes {#specifying-the-search-promote-service-that-your-pages-use}

Konfigurieren Sie Webseiten so, dass diese einen spezifischen Search&amp;Promote-Dienst verwenden. Search&amp;Promote-Komponenten verwenden automatisch den Dienst ihrer Hostseite.

Wenn Sie die Search&amp;Promote-Eigenschaften für eine Hostseite konfigurieren, übernehmen alle untergeordneten Seiten die Einstellungen. Bei Bedarf können Sie die untergeordneten Seiten so konfigurieren, dass sie die übernommenen Einstellungen außer Kraft setzen.

>[!NOTE]
>
>Die Dienstverbindung muss bereits konfiguriert sein. Siehe [Konfigurieren der Verbindung zu Search&amp;Promote](#configuring-the-connection-to-search-promote).

1. Öffnen Sie das Dialogfeld **[!UICONTROL Seiteneigenschaften]**. Klicken Sie beispielsweise mit der rechten Maustaste auf die Seite **[!UICONTROL Websites]** und klicken Sie auf **[!UICONTROL Eigenschaften]**.

1. Klicken Sie auf die Registerkarte **[!UICONTROL Cloud-Services.]**

1. Zum Deaktivieren der Vererbung der Cloud Service-Konfigurationen von einer übergeordneten Seite klicken Sie auf das Schlosssymbol neben dem Vererbungspfad.

   ![sandpinreferpadlock](assets/sandpinheritpadlock.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen Dienst]**, wählen Sie **[!UICONTROL Adobe Search&amp;Promote]** und klicken Sie dann auf **[!UICONTROL OK]**.

1. Wählen Sie die Verbindungskonfiguration für Ihr Search&amp;Promote aus und klicken Sie dann auf **[!UICONTROL OK]**.

## Produkt-Feed {#product-feed}

Mit der Search&amp;Promote-Integration haben Sie folgende Möglichkeiten:

* Verwenden Sie die API [!UICONTROL eCommerce], unabhängig von der zugrunde liegenden Repository-Struktur und Commerce-Plattform.
* Nutzen Sie die Funktion [!UICONTROL Index Connector] von Search&amp;Promote, um einen Produkt-Feed im XML-Format bereitzustellen.
* Nutzen Sie die Funktion [!UICONTROL Remote Control] von Search&amp;Promote, um Anforderungen nach Bedarf oder nach Zeitplan des Produkt-Feeds durchzuführen.
* Feed-Erstellung für verschiedene Search&amp;Promote, konfiguriert als Cloud-Services-Konfigurationen.

Weitere Informationen finden Sie unter [Produkt-Feed](/help/sites-administering/product-feed.md).
