---
title: Erstellen und Verwalten einer Live Copy
seo-title: Verwalten einer Live Copy
description: Auf dieser Seite wird beschrieben, wie Live Copies von Kanälen erstellt und verwaltet werden.
seo-description: Auf dieser Seite erfahren Sie, wie Sie eine Live Copy eines Kanals erstellen, Eigenschaften anzeigen, den Status prüfen und Änderungen von einem Kanal auf dessen Live Copy übertragen.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Erstellen und Verwalten einer Live Copy{#creating-and-managing-a-live-copy}

Auf dieser Seite wird beschrieben, wie Live Copies von Kanälen erstellt und verwaltet werden.

Eine ***Live Copy*** ist eine Kopie spezifischer Site-Inhalte, für die eine Live-Beziehung zur ursprünglichen Quelle beibehalten wird. Durch diese Live-Beziehung kann die Live Copy Inhalts- und Seiteneigenschaften der Quelle übernehmen.

Auf dieser Seite wird beschrieben, wie eine Live Copy eines Kanals erstellt wird, Eigenschaften angezeigt werden, der Status überprüft und Änderungen von einem Kanal auf dessen Live Copy übertragen werden.

>[!NOTE]
>
>To learn more about Live Copy Sources and Blueprint Configurations, see [MSM Best Practices](/help/sites-administering/msm-best-practices.md).

## Erstellen von Live Copies {#creating-a-live-copy}

Gehen Sie wie folgt vor, um eine Live Copy eines Kanals in Ihrem Projektordner zu erstellen.

1. Wählen Sie den Adobe Experience Manager-Link (oben links) und dann **Screens** aus. Alternatively, you can ﻿go directly to: [http://localhost:4502/screens.html/content/screens](http://localhost:4502/screens.html/content/screens).

1. Navigieren Sie zum Screens-Projekt und klicken Sie auf **Kanäle**.
1. Klicken Sie auf **Erstellen** und wählen Sie **Live Copy** aus, um eine Live Copy des Kanals zu erstellen.

1. Wählen Sie das Ziel aus und klicken Sie auf **Weiter**.
1. Wählen Sie den Speicherort aus, an dem die Live Copy gespeichert werden soll.
1. Geben Sie auf der Seite **Live Copy erstellen** den **Titel** und den **Namen** ein.

1. Klicken Sie auf **Öffnen**, um den Inhalt der neuen Live Copy anzuzeigen oder klicken Sie auf **Fertig**, um zur Hauptseite zurückzukehren.

Sie haben auch die Möglichkeit, die folgenden Schritte für die visuelle Darstellung auszuführen, um eine neue Live Copy eines Kanals zu erstellen.

Im folgenden Beispiel wird gezeigt, wie eine Live Copy (***IdleLiveCopy***) für ***Idle Channel*** (inaktiver Kanal) mit dem Zielordner ***Kanäle*** erstellt wird.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Anzeigen des Inhalts des Live Copy-Kanals {#viewing-content-of-the-live-copy-channel}

Eine Live Copy ist eine Kopie eines Kanals, der bereits vorhanden ist.

Um den Inhalt einer Live Copy anzuzeigen, gehen Sie wie folgt vor:

1. Navigieren Sie zum Screens-Projekt und klicken Sie auf die Stelle, an der Sie die Live Copy ursprünglich wie im obigen Abschnitt gezeigt erstellt haben. (Hier wurde als Speicherort der Ordner **Kanäle** gewählt.)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Inhalt des Kanals anzuzeigen.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Wenn Sie Inhalte für einen Live Copy-Kanal anzeigen, sehen Sie im Menü ein zusätzliches Element als **Live Copy-Status**. Weitere Informationen finden Sie im folgenden Abschnitt.

### Anzeigen der Eigenschaften einer Live Copy      {#viewing-properties-of-a-live-copy}

Außerdem können Sie die Eigenschaften Ihres Live Copy-Kanals anzeigen.

1. Navigieren Sie zum Live Copy-Kanal und klicken Sie in der Aktionsleiste auf **Eigenschaften**.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Klicken Sie auf die Registerkarte **Live Copy**, um Details Ihres Kanals anzuzeigen.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Live Copy-Status {#live-copy-status}

Der in der folgenden Abbildung dargestellte Modus „Live Copy-Status“ erlaubt es Ihnen, den Beziehungsstatus aller Assets im Kanal anzuzeigen.

1. Klicken Sie auf **Bearbeiten**, um den **Live Copy-Status** auszuwählen, und zeigen Sie die Zuordnung des Kanalinhalts zum ursprünglichen Kanal an (aus dem die Live Copy erstellt wurde).

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Wählen Sie **Live Copy-Status**, um die Vorschauseite anzuzeigen.

   Bei allen Ressourcen mit grünem Rand wurde der Inhalt des ursprünglichen Kanals übernommen.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Aufheben der Vererbung {#breaking-the-inheritance}

Sie können auch die Vererbung der Live Copy aufheben, wodurch der Inhalt von der ursprünglichen Verzweigung unabhängig wird.

Das folgende Beispiel zeigt, wie Sie das Bild im Modus „Bearbeiten“ auswählen und oben rechts auf das Symbol zum Aufheben der Vererbung klicken.

![chlimage_1-24](assets/chlimage_1-24.png)

### Übertragen der Änderungen auf den Live Copy-Kanal {#propagating-changes-to-the-live-copy-channel}

Wenn Sie Änderungen am ursprünglichen Kanal vornehmen, müssen Sie diese Änderungen auch auf Ihren Live Copy-Kanal übertragen.

Führen Sie die folgenden Schritte aus, um sicherzustellen, dass Ihre Änderungen vom ursprünglichen Kanal auf den Live Copy-Kanal übertragen werden:

1. Wählen Sie den ursprünglichen Kanal (***Idle Channel*** (inaktiver Kanal)) aus und klicken Sie in der Aktionsleiste auf **Bearbeiten**.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Bearbeiten Sie den Kanalinhalt. Löschen Sie beispielsweise ein Bild aus diesem Kanal.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Wählen Sie die Live Copy des Kanals (***IdleLiveCopy***) aus und klicken Sie in der Aktionsleiste auf **Bearbeiten**. Beachten Sie, dass das von Ihnen gelöschte Bild noch in der Live Copy sichtbar ist.

   Um die Änderungen zu übertragen, müssen Sie den Kanal synchronisieren.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Um Änderungen in den Live Copy-Kanal zu übertragen, navigieren Sie zum AEM-Dashboard. Dann wählen Sie den Live Copy-Kanal aus und klicken Sie in der Aktionsleiste auf **Eigenschaften**.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Wählen Sie die Registerkarte **Live Copy** aus und klicken Sie in der Aktionsleiste auf **Synchronisieren**.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Klicken Sie auf **Synchronisieren**, um die Änderungen zu bestätigen. Klicken Sie auf **Speichern und schließen**, um zum AEM-Dashboard zurückzukehren.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Beachten Sie, dass das Bild jetzt auch aus dem Live Copy-Kanal gelöscht ist.

