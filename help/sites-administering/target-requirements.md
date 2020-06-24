---
title: Voraussetzungen für die Integration mit Adobe Target
seo-title: Voraussetzungen für die Integration mit Adobe Target
description: Hier finden Sie alle Informationen über die Voraussetzungen für die Integration mit Adobe Target.
seo-description: Hier finden Sie alle Informationen über die Voraussetzungen für die Integration mit Adobe Target.
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 75%

---


# Voraussetzungen für die Integration mit Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Als Teil der [Integration von AEM und Adobe Target](/help/sites-administering/target.md) müssen Sie sich bei Adobe Target registrieren, den Replikationsagenten konfigurieren und Aktivitätseinstellungen auf dem Veröffentlichungsknoten sichern.

## Registrieren bei Adobe Target {#registering-with-adobe-target}

Zur Integration von AEM mit Adobe Target müssen Sie über ein gültiges Adobe Target-Konto verfügen. Dieses Konto muss mindestens über **Genehmiger **Level-Berechtigungen verfügen. Nach der Registrierung bei Adobe Target erhalten Sie einen Clientcode. Dieser Clientcode und Ihre Adobe Target-Anmeldedaten sind erforderlich, um eine Verbindung zwischen AEM und Adobe Target herzustellen.

Der Clientcode identifiziert beim Aufrufen des Adobe Target-Servers das Adobe Target-Kundenkonto.

>[!NOTE]
>
>Ihr Konto muss auch vom Target-Team aktiviert werden, damit die Integration genutzt werden kann.
>
>
>Falls dies nicht der Fall ist, wenden Sie sich an den [Adobe Target-Kundendienst](https://docs.adobe.com/content/help/en/target/using/cmp-resources-and-contact-information.html).

## Aktivieren des Target-Replikationsagenten {#enabling-the-target-replication-agent}

The Test and Target [replication agent](/help/sites-deploying/replication.md) must be enabled on the author instance. Note that this replication agent is not enabled by default if you used the [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) run mode for installing AEM. Weitere Informationen zum Speichern Ihrer Produktionsumgebung finden Sie in der [Sicherheits-Checkliste](/help/sites-administering/security-checklist.md).

1. Klicken oder tippen Sie auf der AEM-Homepage auf **Tools** > **Bereitstellung** > **Replikation**.
1. Klicken oder tippen Sie auf **Agenten für Autor**.
1. Klicken oder tippen Sie auf den **Test &amp; Target**-Replikationsagenten und dann auf **Bearbeiten**.
1. Wählen Sie die Option „Aktiviert“ aus und klicken oder tippen Sie auf **OK**.

   >[!NOTE]
   >
   >Bei der Konfiguration des Test &amp; Target-Replikationsagenten wird auf der Registerkarte **Transport** für den URI standardmäßig **tnt:///** festgelegt. Do not replace this URI with **https://admin.testandtarget.omniture.com**.
   >
   >Beim Testen der Verbindung mit **tnt:///** wird ein Fehler ausgegeben. This is expected behavior as this URI is for internal use only and should not be used with **Test Connection**.

## Sichern des Aktivitätseinstellungsknotens {#securing-the-activity-settings-node}

Sie müssen den Aktivitätseinstellungsknoten **cq:ActivitySettings** auf der Veröffentlichungsinstanz sichern, sodass dieser für normale Benutzer nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Dienst zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.

The **cq:ActivitySettings** node is available in CRXDE lite under `/content/campaigns/*nameofbrand*`* *under the activities jcr:content node;* *for example `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dieser Knoten wird nur erstellt, wenn Sie eine Komponente als Ziel angeben.

The **cq:ActivitySettings** node under the activity&#39;s jcr:content is protected by the following ACLs:

* Alles für jeden verweigern
* „jcr:read,rep:write“ für „target-activity-authors“ zulassen („author“ ist standardmäßig ein Mitglied dieser Gruppe)
* „jcr:read,rep:write“ für „targetservice“ zulassen

Diese Einstellungen gewährleisten, dass normale Benutzer keinen Zugriff auf die Knoteneigenschaften haben. Verwenden Sie dieselben ACLs für „author“ und „publish“. See [User Administration and Security](/help/sites-administering/security.md) for more information.

## Konfigurieren des AEM-Externalizer {#configuring-the-aem-externalizer}

Beim Bearbeiten einer Aktivität in Adobe Target verweist die URL auf **localhost**, außer Sie ändern die URL auf dem AEM-Autorenknoten.

Konfigurieren Sie den AEM-Externalizer wie folgt:

1. Navigate to the OSGi web console at **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Suchen Sie nach **Day CQ Link Externalizer** und geben Sie die Domäne des Autorenknotens an.

   ![chlimage_1-120](assets/chlimage_1-120.png)

