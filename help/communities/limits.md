---
title: Beitragsgrenzen der Mitgliedstaaten
seo-title: Member Contribution Limits
description: Mit der Beitragsbegrenzungsfunktion können Sie die Beiträge zum Schutz vor Spam einschränken
seo-description: Contribution limits feature lets you limit the contributions to protect against spam
uuid: 99b2a855-3f0d-41a0-9572-517a7f29af9f
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d855aac2-f34d-402f-9dc3-c7ad494b45f2
role: Admin
exl-id: fc7ce4d0-2051-4a67-a0d6-baf615e09ca4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 3%

---

# Beitragsgrenzen der Mitgliedstaaten {#member-contribution-limits}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Die Beitragsbegrenzungsfunktion bietet die Möglichkeit, die Beiträge von Community-Mitgliedern zu beschränken, um sie vor Spam zu schützen.

Wenn ein Mitglied eingeschränkt ist, führen Beiträge, die die zulässige Anzahl von Beiträgen überschreiten, zu einem Warnhinweis, dass die Beschränkung überschritten wurde und der Beitrag abgelehnt wird. Das Community-Mitglied kann dann zum Community-Message-Center gehen und sich an einen Community-Manager wenden, der die Einschränkungen ggf. entfernen kann.

Beitragslimits können einzeln über die [Mitgliederkonsole](members.md) und/oder so konfiguriert sind, dass sie automatisch aktiviert werden, wenn Site-Besucher neue Mitglieder werden.

Mithilfe der Mitgliederkonsole können Beitragsbeschränkungen für ein Mitglied jederzeit von einem Community-Manager proaktiv entfernt oder reaktiv entfernt werden, wenn ein Mitglied eine Nachricht an einen Community-Manager sendet, der eine solche Anfrage sendet.

## Konfiguration benutzergenerierter Inhaltsbeiträge in AEM Communities - Einschränkungen {#aem-communities-user-generated-content-contribution-limits-configuration}

Diese OSGi-Konfiguration

* Definiert die Merkmale der Beitragslimits (Anzahl der Stellen innerhalb eines Zeitraums)
* Identifiziert, wer vom Mitglied benachrichtigt werden kann, wenn das Limit erreicht wurde
* Identifiziert Domänen, die nie eingeschränkt werden müssen

So erreichen Sie diese OSGi-Konfiguration:

* Im primären Herausgeber
* Anmelden mit Administratorrechten
* Zugriff auf [Web-Konsole](../../help/sites-deploying/configuring-osgi.md)

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen `AEM Communities User Generated Content Contribution Limits Configuration`
* Bearbeiten-Symbol auswählen

![chlimage_1-127](assets/chlimage_1-127.png)

* **[!UICONTROL Automatische Anwendung von UGC-Beitragslimits]**

   Wenn diese Option aktiviert ist, legen Sie Benutzern automatisch Beitragsbeschränkungen fest, wenn sie sich als Community-Mitglieder registrieren. Dies spiegelt sich im Profil des Community-Mitglieds wider und kann über die [Mitgliederkonsole](members.md). Neue Mitglieder mit einer E-Mail-Adresse aus einer Zulassungsliste von Domänen werden nie eingeschränkt.

   Die Option Standard ist deaktiviert.

* **[!UICONTROL UGC-Limit]**

   Maximale Anzahl der Beiträge.

   Der Standardwert beträgt 10 Beiträge.

* **[!UICONTROL UGC-Grenzfrequenz]**

   Der Zeitraum, der die UGC-Grenze einschränkt.

   Der Standardwert ist 60 Minuten.

* **[!UICONTROL Domänen]**

   Eine Zulassungsliste mit einer oder mehreren E-Mail-Domänen. Wählen Sie das Symbol + aus, um weitere Einträge vorzunehmen.

   Benutzer mit E-Mail-Adressen in der Zulassungsliste der Domänen sind nicht betroffen, wenn die UGC-Beitragsbeschränkungen automatisch angewendet werden. Wenn beispielsweise die Domäne `mycompany.com` der Liste der Domänen hinzugefügt wird, wird ein Mitglied mit E-Mail-Adresse `me@mycompany.com` ist nie vom Posten ausgeschlossen.

   Der Standardwert ist eine leere Zulassungsliste.

* **[!UICONTROL Messaging-Empfänger]**

   Liste mit einer oder mehreren autorisierbaren IDs von Mitgliedern, die die Beitragsbeschränkungen für Mitglieder ändern können. Wählen Sie das Symbol + aus, um weitere Einträge vorzunehmen.

   Die Mitglieder können nur an bestimmte Mitglieder Kontakt aufnehmen, wenn ihre Grenze erreicht ist.

   Der Standardwert ist kein Nachrichtenempfänger.

Hinweis: Die Standardkonfiguration führt innerhalb eines Zeitraums von einer Stunde zu maximal 10 Beiträgen.
