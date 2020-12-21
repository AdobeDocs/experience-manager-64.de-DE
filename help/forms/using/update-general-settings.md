---
title: Aktualisieren von allgemeinen Einstellungen
seo-title: Aktualisieren von allgemeinen Einstellungen
description: AEM Forms-App-Einstellungen wie den Startbildschirm aktualisieren und Optionen für Startpunkte und Anlagen abrufen
seo-description: AEM Forms-App-Einstellungen wie den Startbildschirm aktualisieren und Optionen für Startpunkte und Anlagen abrufen
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 85%

---


# Aktualisieren von allgemeinen Einstellungen {#updating-general-settings}

Allgemeine Einstellungen des AEM Forms App können Sie die Einstellungen, z. B. Abrufen von Anlagen, running, von Landungsbildschirm, Standardkategorie und autsave Frequenz angeben.

## Aktualisieren von allgemeinen Einstellungen in der App {#working-with-the-form}

Wenn Sie die App mit dem AEM Forms-Server synchronisieren, werden alle Formulare und definierten Aufgaben auf Ihr mobiles Gerät heruntergeladen.

Die im Lieferumfang enthaltene AEM Forms-App-Lösung lädt die mit den einzelnen Formularen verknüpften Anlagen nicht herunter, wenn die App synchronisiert wird.

Ändern Sie auf der Registerkarte „Allgemein“ die Einstellungen für das Herunterladen von Anlagen, für den Offline-Modus, den Einstiegsbildschirm, die automatische Speicherung und die Synchronisierung. Sie können den [Startbildschirm](/help/forms/using/home-screen.md) der App ändern.

**Navigieren Sie zur Registerkarte „General“ auf dem Startbildschirm.**

1. Um den Einstellungsbildschirm aufzurufen, tippen Sie links unten auf dem Startbildschirm auf die Schaltfläche „Menü“ und dann auf **Einstellungen**.
1. Tippen Sie auf dem Bildschirm „Settings“ auf die Registerkarte „General“.

   ![Allgemeine Einstellungen in der AEM Forms-App](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >Die Optionen werden auf verschiedenen Mobilgeräten möglicherweise unterschiedlich angezeigt.

### Allgemeine Einstellungen {#general-settings}

Sie können folgende Änderungen an den Einstellungen der App vornehmen.

* **Fetch attachments**: Mit dieser Option geben Sie an, ob die verknüpften Anlagen heruntergeladen werden sollen, wenn eine Aufgabe in Ihre App heruntergeladen wird.

* **Offline mode**: Hiermit aktivieren bzw. deaktivieren Sie den Offlinedienst für die AEM Forms-App. Weitere Informationen finden Sie unter [Arbeiten im Offlinemodus](/help/forms/using/work-offline-mode.md).

* **Landing screen**: Mit dieser Option legen Sie die Startposition ([Home screen](/help/forms/using/home-screen.md)) für die App fest.

   Verfügbare Optionen:

   * Formulare
   * Aufgaben
   * Favoriten

* **Default category**: Wählen Sie hier die Kategorie der Formulare aus, die auf dem Startbildschirm angezeigt wird. Wenn Sie „All“ auswählen, können Sie alle Formulare auf dem Startbildschirm sehen. Kategorien werden basierend auf den Formularen ausgefüllt, die in der App geladen werden. Formulare sind in der App je nach den Formulareinstellungen im AEM Forms-Server verfügbar.

* **Autosave Frequency**: So legen Sie fest, wie oft die  [mobile App ](/help/forms/using/autosave-data-app.md) Formulardaten speichert.

* **Synchronisierungshäufigkeit**: So legen Sie die Häufigkeit fest, mit der die  [mobile App im Online-Modus mit dem AEM Forms-Server ](/help/forms/using/sync-app.md) synchronisiert wird.

**Clear Local Data**: Löscht die Datenbank, einschließlich Einstellungen und lokaler Daten für alle Benutzer und Dateispeicher auf dem Gerät.

>[!NOTE]
>
>Das Löschen des Zwischenspeichers führt dazu, dass Sie sofort von der App abgemeldet werden.
>
>Sie erhalten jedoch eine Aufforderung zum Bestätigen des Cache-Löschvorgangs.
