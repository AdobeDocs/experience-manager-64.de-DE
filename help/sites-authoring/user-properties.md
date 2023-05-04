---
title: Konfigurieren der Kontoumgebung
seo-title: Configuring your account environment
description: AEM bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren
seo-description: AEM provides you with the capability to configure your account and certain aspects of the author environment
uuid: 01e76771-9ac8-4919-9e50-0a63826177d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6afbc889-c613-40e6-8a25-1570dff32d60
exl-id: f620e85e-8c77-41a3-a238-9b93c819909d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 61%

---

# Konfigurieren der Kontoumgebung{#configuring-your-account-environment}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

AEM bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren.

Verwenden der [Benutzer](/help/sites-authoring/user-properties.md#user-settings) in der [header](/help/sites-authoring/basic-handling.md#the-header) und die zugehörigen [Benutzereinstellungen](#my-preferences) -Dialogfeld können Sie Ihre Benutzeroptionen ändern.

## Benutzereinstellungen {#user-settings}

Die **Benutzer** Über das Dialogfeld &quot;Einstellungen&quot;haben Sie Zugriff auf:

* Identität annehmen als

   * Mit dem [Identität annehmen als](/help/sites-administering/security.md#impersonating-another-user) -Funktion kann ein Benutzer im Namen eines anderen Benutzers arbeiten.

* Profil

   * Über das Profil kann bequem über einen Link auf [Benutzereinstellungen](/help/sites-administering/security.md) zugegriffen werden.

* [Benutzereinstellungen](/help/sites-authoring/user-properties.md#my-preferences)

   * Hier können verschiedene auf den jeweiligen Benutzer zugeschnittene Einstellungen festgelegt werden.

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

## Benutzereinstellungen {#my-preferences}

Auf das Dialogfeld **Benutzereinstellungen** kann über die Option [Benutzer](/help/sites-authoring/user-properties.md#user-settings) in der Kopfzeile zugegriffen werden.

Jeder Benutzer kann bestimmte Eigenschaften für sich selbst festlegen.

![screen_shot_2018-03-20at102118](assets/screen_shot_2018-03-20at102118.png)

* **Sprache**

   Dadurch wird die Sprache definiert, die für die Benutzeroberfläche der Authoring-Umgebung verwendet werden soll. Wählen Sie in der Liste die gewünschte Sprache aus.

   Diese Konfiguration wird auch für die klassische Benutzeroberfläche verwendet.

* **Fensterverwaltung**

   Dies definiert das Verhalten oder das Öffnen von Fenstern. Wählen Sie eine der folgenden beiden Optionen aus:

   * **Mehrere Fenster** (Standard)

      * Seiten werden in einem neuen Fenster geöffnet.
   * **Einfaches Fenster**

      * Seiten werden im aktuellen Fenster geöffnet.


* **Desktop-Aktionen für Assets anzeigen**

   Für diese Option ist das AEM-Desktop-Programm erforderlich.

* **Anmerkungsfarbe**

   Dadurch wird die Standardfarbe definiert, die beim Erstellen von Anmerkungen verwendet wird.

   * Klicken Sie auf den Farbblock, um die Musterauswahl zu öffnen und eine Farbe auszuwählen.
   * Alternativ dazu können Sie in das Feld den Hexcode für die gewünschte Farbe eingeben.

* **Darstellung des relativen Datums**

   Um die Lesbarkeit zu verbessern, rendert AEM Datumsangaben innerhalb der letzten sieben Tage als relative Daten (z. B. vor drei Tagen) und ältere Daten als exakte Datumswerte (z. B. 20. März 2017).

   Diese Option definiert, wie Daten im System angezeigt werden. Die folgenden Optionen sind verfügbar:

   * **Immer exaktes Datum anzeigen**: Es wird immer das genaue Datum angezeigt (niemals ein relatives Datum).
   * **1 Tag**: Das relative Datum wird für Datumsangaben innerhalb eines Tages angezeigt; ansonsten wird das genaue Datum angegeben.
   * **7 Tage (Standard)**: Das relative Datum wird für Datumsangaben innerhalb eines Zeitraums von sieben Tages angezeigt; ansonsten wird das genaue Datum angegeben.
   * **1 Monat**: Das relative Datum wird für Datumsangaben innerhalb eines Monats angezeigt; ansonsten wird das genaue Datum angegeben.
   * **1 Jahr**: Das relative Datum wird für Datumsangaben innerhalb eines Jahres angezeigt; ansonsten wird das genaue Datum angegeben.
   * **Immer relatives Datum anzeigen**: Es werden niemals genaue Datumsangaben, sondern nur relative Daten angezeigt.

* **Tastaturbefehle aktivieren**

   AEM unterstützt verschiedene Tastaturbefehle, die eine effizientere Bearbeitung ermöglichen.

   * [Tastaturbefehle für die Seitenbearbeitung](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
   * [Tastaturbefehle für Konsolen](/help/sites-authoring/keyboard-shortcuts.md)

   Diese Option aktiviert Tastaturbefehle. Sie sind standardmäßig aktiviert, können aber deaktiviert werden, z. B. wenn ein Benutzer bestimmte Barrierefreiheitsanforderungen hat.

* **Klassisches Authoring-Erlebnis verwenden**

   Diese Option ermöglicht eine auf der [klassischen Benutzeroberfläche](/help/sites-classic-ui-authoring/home.md) basierende Seitenbearbeitung. Im Normalfall wird die Standard-Benutzeroberfläche verwendet.

* **Asset-Homepage aktivieren**

   Diese Option ist nur verfügbar, wenn der Systemadministrator die Asset-Homepage-Nutzung für das gesamte Unternehmen aktiviert hat.
