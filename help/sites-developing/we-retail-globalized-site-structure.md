---
title: Testen der globalisierten Site-Struktur von We.Retail
seo-title: Trying out the Globalized Site Structure in We.Retail
description: Testen der globalisierten Site-Struktur von We.Retail
seo-description: null
uuid: 5e5a809d-578f-4171-8226-cb65aa995754
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: d674458c-d5f3-4dee-a673-b0777c02ad30
exl-id: e26e8e58-3aa4-4e7a-ac9e-f274c4af0041
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 30%

---

# Testen der globalisierten Site-Struktur von We.Retail{#trying-out-the-globalized-site-structure-in-we-retail}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

We.Retail wurde mit einer globalisierten Site-Struktur erstellt, die Sprach-Master bietet, die live auf länderspezifische Websites kopiert werden können. Alles ist vorkonfiguriert, damit Sie mit dieser Struktur und den integrierten Übersetzungsfunktionen experimentieren können.

## Testen {#trying-it-out}

1. Öffnen Sie die Sites-Konsole über **Globale Navigation -> Sites**.
1. Wechseln Sie zur Spaltenansicht (falls noch nicht aktiv) und wählen Sie We.Retail aus. Beachten Sie die Beispiel-Landesstruktur inklusive Schweiz, USA, Frankreich usw. sowie die Sprach-Master.

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Wählen Sie die Schweiz aus und sehen Sie sich die Sprachstämme für die Sprachen dieses Landes an. Beachten Sie, dass unter diesen Wurzeln noch kein Inhalt vorhanden ist.

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Wechseln Sie in die Listenansicht, um zu sehen, dass es sich bei den Sprachkopien für die Länder um Live Copies handelt.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. Kehren Sie zur Spaltenansicht zurück und klicken Sie auf Übergeordnete Sprache und sehen Sie sich die Übergeordneten Sprachstämme mit Inhalt an. Beachten Sie, dass nur Englisch Inhalte enthält.

   We.Retail enthält keine übersetzten Inhalte, doch die Struktur und Konfiguration sind vorhanden, um Ihnen die Übersetzungsdienste zu demonstrieren.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Lassen Sie den englischen Sprach-Master ausgewählt, öffnen Sie die Leiste **Verweise** in der Sites-Konsole und wählen Sie **Sprachkopien** aus.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Aktivieren Sie das Kontrollkästchen neben dem **Sprachkopien** Beschriftung zur Auswahl aller Sprachkopien. Im **Sprachkopien aktualisieren** Wählen Sie in der Leiste die Option **Neues Übersetzungsprojekt erstellen**. Geben Sie einen Namen für das Projekt ein und klicken Sie auf **Aktualisieren**.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Für jede Sprachübersetzung wird ein Projekt erstellt. Anzeigen unter **Navigation -> Projekte**.

   ![chlimage_1-93](assets/chlimage_1-93.png)

1. Klicken Sie auf Deutsch , um die Details des Übersetzungsprojekts anzuzeigen. Beachten Sie, dass der Status in **Entwurf**. Um die Übersetzung mit dem Übersetzungsdienst von Microsoft zu starten, klicken Sie auf den Pfeil neben dem **Übersetzungsauftrag** Überschrift und Auswahl **Starten**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Das Übersetzungsprojekt beginnt. Klicken Sie unten auf der Karte mit der Bezeichnung Übersetzungsauftrag auf das Auslassungszeichen, um die Details anzuzeigen. Seiten mit dem Status **Bereit zur Überprüfung** wurden bereits vom Übersetzungsdienst übersetzt.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Wählen Sie in der Liste eine der Seiten und dann in der Symbolleiste die Option **Vorschau in Sites** aus, um die übersetzte Seite im Seiteneditor zu öffnen.

   ![chlimage_1-96](assets/chlimage_1-96.png)

>[!NOTE]
>
>Dieses Verfahren zeigt die integrierte Integration mit der maschinellen Übersetzung von Microsoft. Verwenden der [AEM Framework für die Übersetzungsintegration](/help/sites-administering/translation.md), können Sie mit vielen Standardübersetzungsdiensten integrieren, um die Übersetzung von AEM zu koordinieren.

## Weiterführende Informationen {#further-information}

Weitere Informationen sowie vollständige technische Details finden Sie im Dokument [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md).
