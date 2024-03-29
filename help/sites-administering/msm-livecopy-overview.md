---
title: Konsole „Live Copy-Übersicht“
seo-title: Live Copy Overview Console
description: Erfahren Sie mehr über die Grundlagen der Konsole "Live Copy-Übersicht".
seo-description: Learn about the basics of the Live Copy Overview Console.
uuid: 6b1841ec-950e-455b-9b30-b5f5050a67b8
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 3763e985-7dd8-47fd-bfdf-2368b424c270
feature: Multi Site Manager
exl-id: 96238d40-c19a-4c1f-9400-c7bb8636b448
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 52%

---

# Konsole „Live Copy-Übersicht“{#live-copy-overview-console}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die **Live Copy-Übersicht** ermöglicht Ihnen Folgendes:

* Anzeigen/Verwalten der Vererbung auf einer Site:

   * Anzeigen des Blueprint-Baums und der entsprechenden Live Copy-Struktur sowie des Vererbungsstatus
   * den Vererbungsstatus ändern; z. B. aussetzen, fortsetzen
   * Anzeigen von Blueprint- und Live Copy-Eigenschaften

* Rollout-Aktionen durchführen

## Öffnen der Live Copy-Übersicht {#opening-the-live-copy-overview}

Sie können die Live Copy-Übersicht wie folgt öffnen:

* [über das seitliche Bedienfeld „Verweise“ einer Blueprint-Seite (Sites-Konsole);](#opening-live-copy-overview-references-for-a-blueprint-page)
* [über die Eigenschaften der Blueprint-Seite.](#opening-live-copy-overview-properties-of-a-blueprint-page)

### Öffnen der Live Copy-Übersicht – Verweise für eine Blueprint-Seite {#opening-live-copy-overview-references-for-a-blueprint-page}

Die **Live Copy-Übersicht** wird über das seitliche Bedienfeld **Verweise** der Konsole **Sites** geöffnet:

1. Navigieren Sie in der Konsole **Sites** [zu Ihrer Blueprint-Seite und wählen Sie diese aus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie das Bedienfeld **[Verweise](/help/sites-authoring/basic-handling.md#references)** und wählen Sie **Live Copies** aus.

   ![chlimage_1-359](assets/chlimage_1-359.png)

   >[!NOTE]
   >
   >Sie können auch zuerst Verweise öffnen und dann den Blueprint auswählen.

1. Wählen Sie **Live Copy-Übersicht** aus, um eine Übersicht aller Live Copies mit Bezug zur ausgewählten Blueprint-Seite anzuzeigen und zu verwenden.
1. Verwenden Sie **Schließen**, um den Vorgang zu beenden, und kehren Sie zur **Sites-Konsole** zurück.

### Öffnen der Live Copy-Übersicht - Eigenschaften einer Blueprint-Seite {#opening-live-copy-overview-properties-of-a-blueprint-page}

Die **Live Copy-Übersicht** kann beim Anzeigen der Eigenschaften einer Blueprint-Seite geöffnet werden:

1. Öffnen **Eigenschaften** für die entsprechende Blueprint-Seite.
1. Öffnen Sie die **Blueprint** tab - das **Live Copy-Übersicht** wird in der oberen Symbolleiste angezeigt:

   ![chlimage_1-360](assets/chlimage_1-360.png)

1. Wählen Sie **Live Copy-Übersicht** aus, um eine Übersicht aller Live Copies mit Bezug zur aktuellen Blueprint-Seite anzuzeigen und zu verwenden.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie im Knowledge Base-Artikel . [Livecopy-Statusmeldung - Aktuell/Grün/In Sync](https://helpx.adobe.com/de/experience-manager/kb/livecopy-status-message---up-to-date-green-in-sync.html).

1. Verwenden Sie **Schließen**, um den Vorgang zu beenden, und kehren Sie zur **Sites-Konsole** zurück.

## Verwenden der Live Copy-Übersicht {#using-the-live-copy-overview}

Die **Live Copy-Übersicht** kann auch verwendet werden, um Aktionen für die Live Copy durchzuführen:

1. Öffnen Sie die **Live Copy-Übersicht**.
1. Wählen Sie die erforderliche Blueprint- oder Live Copy-Seite aus. Die Symbolleiste wird aktualisiert und zeigt die verfügbaren Aktionen an. Die [Aktionen](/help/sites-administering/msm.md#terms-used) Welche verfügbar sind, hängt davon ab, ob Sie eine [Blueprint](#actions-for-a-blueprint-page) oder [Live Copy](#actions-for-a-live-copy-page) Seite:

### Aktionen für Blueprint-Seiten {#actions-for-a-blueprint-page}

Bei Auswahl einer Blueprint-Seite sind die folgenden Aktionen verfügbar:

![chlimage_1-361](assets/chlimage_1-361.png)

* Bearbeiten

   * Öffnen Sie die Blueprint-Seite zur Bearbeitung.

* [Rollout](/help/sites-administering/msm.md#rollout-and-synchronize)

   * Führen Sie einen Rollout durch, um Änderungen von der Quelle an die Live Copy zu übertragen.

### Aktionen für eine Live Copy-Seite {#actions-for-a-live-copy-page}

Wenn Sie eine Live Copy-Seite auswählen, sind die folgenden Aktionen verfügbar:

![chlimage_1-362](assets/chlimage_1-362.png)

* Bearbeiten

   * Öffnen Sie die Live Copy-Seite zur Bearbeitung.

* [Beziehungsstatus](#relationship-status)

   * Zeigt Informationen zum Status und zur Vererbung an.

* [Synchronisieren](/help/sites-administering/msm.md#rollout-and-synchronize)

   * Synchronisieren Sie eine Live Copy, um Änderungen von der Quelle per Pull auf die Live Copy zu übertragen.

* [Zurücksetzen](/help/sites-administering/msm-livecopy.md#resetting-a-live-copy-page)

   * Setzt eine Live Copy-Seite zurück, um alle abgebrochenen Vererbungsvorgänge zu entfernen und die Seite wieder in denselben Status wie die Quellseite zu versetzen.

* [Aussetzen](/help/sites-administering/msm.md#suspending-and-cancelling-inheritance-and-synchronization)

   * Deaktiviert vorübergehend die Live-Beziehung zwischen einer Live Copy und der zugehörigen Blueprint-Seite.

* [Fortsetzen ](/help/sites-administering/msm-livecopy.md#resuming-inheritance-for-a-page)

   * Reaktiviert eine ausgesetzte Beziehung.

* [Trennen](/help/sites-administering/msm.md#detaching-a-live-copy)

   * Entfernt dauerhaft die Live-Beziehung zwischen einer Live Copy und der zugehörigen Blueprint-Seite.

## Beziehungsstatus {#relationship-status}

Die Konsole **Beziehungsstatus** verfügt über zwei Registerkarten mit verschiedenen Funktionen:

* [Informationen zum Beziehungsstatus](#relationship-status-information)
* [Informationen zur Live Copy](#live-copy-information)

### Informationen zum Beziehungsstatus {#relationship-status-information}

Dieser Tab enthält detaillierte Informationen zum Status der Beziehung zwischen dem Blueprint und der Live Copy:

![chlimage_1-363](assets/chlimage_1-363.png)

### Informationen zur Live Copy {#live-copy-information}

Auf dieser Registerkarte können Sie die Live Copy-Konfiguration anzeigen und bearbeiten:

![chlimage_1-364](assets/chlimage_1-364.png)
