---
title: Aktualisieren von allgemeinen Einstellungen
seo-title: Updating general settings
description: Aktualisieren von AEM Forms-App-Einstellungen wie dem Startbildschirm und Abrufen von Startpunkten und Anlagenoptionen
seo-description: Update AEM Forms app settings such as the Home screen and fetch Startpoints and attachments options
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
exl-id: 5ca6212f-d3c7-4239-beba-9a0bdac4b1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 48%

---

# Aktualisieren von allgemeinen Einstellungen {#updating-general-settings}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In den allgemeinen Einstellungen des AEM Forms-Programms können Sie Einstellungen wie das Abrufen von Anhängen, den Offline-Modus, den Landingscreen, die Standardkategorie und die Häufigkeit der Austragung festlegen.

## Aktualisieren der allgemeinen Einstellungen in Ihrer App {#working-with-the-form}

Wenn Sie Ihre App mit dem AEM Forms-Server synchronisieren, werden alle Formulare und definierten Aufgaben auf Ihr Mobilgerät heruntergeladen.

Die sofort einsatzbereite Mobile App von AEM Forms lädt die mit den einzelnen Formularen verbundenen Anhänge nicht herunter, wenn Ihre Mobile App synchronisiert wird.

Ändern Sie auf der Registerkarte „Allgemein“ die Einstellungen für das Herunterladen von Anlagen, für den Offline-Modus, den Einstiegsbildschirm, die automatische Speicherung und die Synchronisierung. Sie können den [Startbildschirm](/help/forms/using/home-screen.md) der App ändern.

**Navigieren Sie zur Registerkarte Allgemein auf dem Bildschirm Einstellungen .**

1. Um zum Einstellungsbildschirm zu gelangen, tippen Sie auf die Schaltfläche &quot;Menü&quot;in der linken oberen Ecke des Startbildschirms und dann auf **Einstellungen**.
1. Tippen Sie im Bildschirm &quot;Einstellungen&quot;auf die Registerkarte Allgemein .

   ![Allgemeine Einstellungen in der AEM Forms-App](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >Die Optionen werden auf verschiedenen Mobilgeräten möglicherweise unterschiedlich angezeigt.

### Allgemeine Einstellungen {#general-settings}

Sie können folgende Änderungen an den Einstellungen der App vornehmen.

* **Fetch attachments**: Mit dieser Option geben Sie an, ob die verknüpften Anlagen heruntergeladen werden sollen, wenn eine Aufgabe in Ihre App heruntergeladen wird.

* **Offline mode**: Hiermit aktivieren bzw. deaktivieren Sie den Offlinedienst für die AEM Forms-App. Siehe [Arbeiten im Offline-Modus](/help/forms/using/work-offline-mode.md) für Details.

* **Landing screen**: Mit dieser Option legen Sie die Startposition ([Home screen](/help/forms/using/home-screen.md)) für die App fest.

   Verfügbare Optionen:

   * Formulare
   * Aufgaben
   * Favoriten

* **Standardkategorie**: Ermöglicht die Auswahl der Formularkategorie, die auf dem Startbildschirm angezeigt werden soll. Wenn Sie Alle auswählen, werden alle Formulare auf dem Startbildschirm angezeigt. Kategorien werden basierend auf den in der App geladenen Formularen ausgefüllt. Formulare sind in der App je nach den Formulareinstellungen im AEM Forms-Server verfügbar.

* **Häufigkeit der automatischen Speicherung**: Mit dieser Option legen Sie fest, wie häufig die [Mobile App Formulardaten lokal speichert](/help/forms/using/autosave-data-app.md).

* **Synchronisierungshäufigkeit**: So legen Sie die Häufigkeit fest, mit der Ihre [mobile App ist synchronisiert](/help/forms/using/sync-app.md) mit dem AEM Forms-Server im Online-Modus.

**Clear Local Data**: Löscht die Datenbank, einschließlich Einstellungen und lokaler Daten für alle Benutzer und Dateispeicher auf dem Gerät.

>[!NOTE]
>
>Das Löschen des Zwischenspeichers führt dazu, dass Sie sofort von der App abgemeldet werden.
>
>Sie erhalten jedoch eine Aufforderung zum Bestätigen des Cache-Löschvorgangs.
