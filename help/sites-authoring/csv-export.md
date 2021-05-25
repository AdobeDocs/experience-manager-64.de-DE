---
title: 'Exportieren in CSV  '
seo-title: 'Exportieren in CSV  '
description: Exportieren von Informationen zu Ihren Seiten in eine CSV-Datei auf Ihrem lokalen System
seo-description: Exportieren von Informationen zu Ihren Seiten in eine CSV-Datei auf Ihrem lokalen System
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 79%

---

# Exportieren in CSV  {#export-to-csv}

Mit **CSV-Export erstellen** können Sie Informationen über Ihre Seiten in eine CSV-Datei auf Ihrem lokalen System exportieren.

* Die heruntergeladene Datei erhält den Namen `export.csv`.
* Der Inhalt der Datei hängt davon ab, welche Eigenschaften Sie für den Export auswählen.
* Sie können den Pfad zusammen mit der Tiefe des Exports definieren.

>[!NOTE]
>
>Die Download-Funktion (und der Standard-Zielordner) Ihres Browsers werden verwendet.

Der Assistent zum Erstellen von CSV-Exporten bietet Ihnen folgende Auswahlmöglichkeiten:

* Zu exportierende Eigenschaften

   * Metadaten  

      * Geändert
      * Veröffentlicht
   * Analytics

      * Seitenansichten
      * Individuelle Besucher
      * Zeit auf Seite


* Depth

   * Übergeordneter Pfad
   * Nur direkte untergeordnete Elemente
   * Zusätzliche Ebenen von untergeordneten Elementen
   * Levels

Die resultierende Datei `export.csv` kann in Excel (oder einer anderen kompatiblen Anwendung) geöffnet werden.

![chlimage_1-58](assets/chlimage_1-58.png)

Die Option **CSV-Export** ist beim Durchsuchen der Konsole **Sites** verfügbar (in der Listenansicht): Es handelt sich um eine Option des Dropdown-Menüs **Erstellen**:

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

So erstellen Sie einen CSV-Export: 

1. Öffnen Sie die **Sites-Konsole** und wechseln Sie zum gewünschten Verzeichnis, falls erforderlich.
1. Wählen Sie in der Symbolleiste **Erstellen** und dann **CSV-Export** aus, um den Assistenten zu öffnen:

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. Wählen Sie die gewünschten Eigenschaften aus, die Sie exportieren möchten.
1. Wählen Sie **Erstellen**.
