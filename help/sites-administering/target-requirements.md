---
title: Voraussetzungen für das Integrieren mit Adobe Target
seo-title: Prerequisites for Integrating with Adobe Target
description: Erfahren Sie mehr über die Voraussetzungen für die Integration mit Adobe Target.
seo-description: Find out about the prerequisites for integrating with Adobe Target.
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
exl-id: f47e5c6a-ed52-4493-83bd-73e5e693d117
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 56%

---

# Voraussetzungen für das Integrieren mit Adobe Target{#prerequisites-for-integrating-with-adobe-target}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Als Teil der [Integration von AEM und Adobe Target](/help/sites-administering/target.md) müssen Sie sich bei Adobe Target registrieren, den Replikationsagenten konfigurieren und Aktivitätseinstellungen auf dem Veröffentlichungsknoten sichern.

## Registrieren bei Adobe Target {#registering-with-adobe-target}

Zur Integration von AEM in Adobe Target benötigen Sie ein gültiges Adobe Target-Konto. Dieses Konto muss mindestens über Berechtigungen der Stufe **Genehmiger* verfügen. Nach der Registrierung bei Adobe Target erhalten Sie einen Clientcode. Sie benötigen den Clientcode sowie Ihren Adobe Target-Anmeldenamen und Ihr Kennwort, um eine Verbindung AEM Adobe Target herzustellen.

Der Clientcode identifiziert das Adobe Target-Kundenkonto beim Aufrufen des Adobe Target-Servers.

>[!NOTE]
>
>Ihr Konto muss auch vom Target-Team aktiviert werden, damit die Integration genutzt werden kann.
>
>
>Sollte dies nicht der Fall sein, wenden Sie sich bitte an [Adobe Target-Kundenunterstützung](https://experienceleague.adobe.com/docs/target/using/cmp-resources-and-contact-information.html?lang=de).

## Aktivieren des Target-Replikationsagenten {#enabling-the-target-replication-agent}

Auf der Autoreninstanz muss der Test-and-Target-[Replikationsagent](/help/sites-deploying/replication.md) aktiviert werden. Dieser Replikationsagent ist standardmäßig deaktiviert, wenn Sie bei der Installation von AEM den Ausführungsmodus [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) verwendet haben. Weitere Informationen zum Schützen der Produktionsumgebung finden Sie im Abschnitt [Sicherheitscheckliste](/help/sites-administering/security-checklist.md).

1. Klicken oder tippen Sie auf der AEM Homepage auf **Instrumente** > **Implementierung** > **Replikation**.
1. Klicken oder tippen Sie auf **Agenten für Autor**.
1. Klicken oder tippen Sie auf **Test und Target (Test und Ziel)** Replikationsagent und klicken oder tippen Sie dann auf **Bearbeiten**.
1. Wählen Sie die Option Aktiviert aus und klicken oder tippen Sie auf **OK**.

   >[!NOTE]
   >
   >Bei der Konfiguration des Test &amp; Target-Replikationsagenten wird auf der Registerkarte **Transport** für den URI standardmäßig **tnt:///** festgelegt. Ersetzen Sie den URI nicht durch **https://admin.testandtarget.omniture.com**.
   >
   >Beim Testen der Verbindung mit **tnt:///** wird ein Fehler ausgegeben. Dieses Verhalten ist zu erwarten, da dieser URI ausschließlich zur internen Verwendung gedacht ist und nicht mit der Funktion **Verbindung testen** verwendet werden sollte.

## Sichern des Aktivitätseinstellungsknotens {#securing-the-activity-settings-node}

Sie müssen den Aktivitätseinstellungsknoten sichern **cq:ActivitySettings** auf der Veröffentlichungsinstanz, sodass sie für normale Benutzer nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Service zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.

Der Knoten **cq:ActivitySettings** steht in CRXDE Lite unter `/content/campaigns/*nameofbrand*`* *unter dem Aktivitätsknoten jcr:content zur Verfügung,* *z. B. `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dieser Knoten wird nur erstellt, wenn Sie eine Komponente als Ziel angeben.

Der Knoten **cq:ActivitySettings** unter dem Aktivitätsknoten jcr:content wird von folgenden ACLs geschützt:

* Alle für alle verweigern
* Zulassen von jcr:read,rep:write für &quot;target-activity-authors&quot;(der Autor ist standardmäßig Mitglied dieser Gruppe)
* Allow jcr:read,rep:write für &quot;targetservice&quot;

Diese Einstellungen stellen sicher, dass normale Benutzer keinen Zugriff auf die Knoteneigenschaften haben. Verwenden Sie dieselben ACLs für Autor und Veröffentlichung. Weitere Informationen finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).

## Konfigurieren des AEM Externalizers {#configuring-the-aem-externalizer}

Beim Bearbeiten einer Aktivität in Adobe Target verweist die URL auf **localhost**, außer Sie ändern die URL auf dem AEM-Autorenknoten.

Konfigurieren Sie den AEM-Externalizer wie folgt:

1. Navigieren Sie zur OSGi-Web-Konsole unter **https://&lt;server>:&lt;port>/system/console/configMgr**.
1. Suchen Sie nach **Day CQ Link Externalizer** und geben Sie die Domain des Autorenknotens an.

   ![chlimage_1-120](assets/chlimage_1-120.png)
