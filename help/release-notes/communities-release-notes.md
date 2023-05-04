---
title: Versionshinweise zu AEM Communities
seo-title: AEM Communities
description: Spezifische Versionshinweise für Adobe Experience Manager 6.4 Communities.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Communities.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
exl-id: 3a341e72-01c5-4c63-8942-6320e5b08440
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 9%

---

# Versionshinweise zu AEM Communities {#aem-communities-release-notes}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Dieser Abschnitt enthält Informationen zu den Verbesserungen an AEM Communities seit Version 6.3. Weitere Informationen zu den neuen Funktionen finden Sie unter [Neue Funktionen in AEM 6.4 Communities](/help/communities/whats-new-aem-communities.md).

Informationen dazu, wie Sie die neueste Version erhalten, finden Sie in der Dokumentation unter dem Abschnitt zur [Bereitstellung von Communities](/help/communities/deploy-communities.md#latest-releases).

## Wichtigste Verbesserungen {#main-improvements}

Community-Sites:

* Community-Administratoren können jetzt:

   * Community-Sites dauerhaft löschen
   * Wählen Sie einen kontextsensitiven Konfigurationsordner für Community-Sites aus.

Community-Gruppen:

* Community-Administratoren können jetzt:

   * Community-Gruppen dauerhaft löschen
   * Community-Gruppen in mehreren Sprachen erstellen
   * Hinzufügen von Aktivierungskatalogen und -zuweisungen in Community-Gruppen

* Aktivierungsmanager können jetzt

   * Erstellen und Zuweisen von Ressourcen und Lernpfaden in Community-Gruppen

Dateibibliothek:

* Community-Mitglieder haben jetzt mehrere Verbesserungen an der Dateibibliothek, z. B. Sortierreihenfolgen, Tagging..

Benachrichtigungen:

* Community-Mitglieder erhalten nun Benachrichtigungen nach Genehmigung von Beiträgen, die einen Moderationsprozess durchlaufen haben

Moderation:

* Automatisierte Spamerkennung - Filter
* Community-Moderatoren verfügen über zusätzliche Moderationsfilter (z. B. beantwortete/unbeantwortete Fragen)
* Community-Moderatoren können Moderationen mit Lesezeichen versehen und vordefinierten Filtern zuordnen (z. B. alle Beiträge, deren Genehmigung aussteht).

Gesamtkompatibilität mit grundlegenden Änderungen in AEM 6.4.

Hinweis: Alle diese Funktionen sind auch für AEM 6.3 verfügbar. Weitere Informationen finden Sie in den AEM Communities-Versionshinweisen unter [6,3](https://helpx.adobe.com/de/experience-manager/6-3/release-notes.html).

## Bekannte Probleme {#known-issues}

* **Moderation** - Übergeordneter Beitrag kann nicht als einzelner Löschvorgang aus der Massenmoderations-Benutzeroberfläche gelöscht werden. (CQ-4236797)
* **Konsole** - Der Link &quot;Benutzername vergessen&quot;oder &quot;Passwort vergessen&quot;leitet zur Anmeldeseite um, anstatt zum entsprechenden Kennwortabfrageformular. (CQ-4237682)

## Funktionen auswählen {#select-features}

Expertenbewertung (*Powered by Sensei*) - wird verwendet, um die Gamifizierung zu ermöglichen, die ein effektives Mittel ist, wertvolles Community-Verhalten zu fördern und zu belohnen. Sie kann auch verwendet werden, um Experten für Empfehlungs- oder Marketing-Zwecke zu identifizieren.

## Demonstrationen {#demonstrations}

Alle diese Funktionen können mit dem [AEM Demomaschine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) bei Verwendung des AEM Communities-Demoszenarios und auch innerhalb der neuen We.Retail-Referenzimplementierung öffentlich auf GitHub.com verfügbar.
