---
title: Exportieren in CSV
seo-title: Export to CSV
description: Exportieren von Informationen zu Ihren Seiten in eine CSV-Datei auf Ihrem lokalen System
seo-description: Export information about your pages to a CSV file on your local system
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 54%

---

# Exportieren in CSV{#export-to-csv}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

**CSV-Export erstellen** ermöglicht Ihnen, Informationen über Ihre Seiten in eine CSV-Datei auf Ihrem lokalen System zu exportieren.

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
   * Analyse

      * Seitenansichten
      * Unique Visitors
      * Zeit auf Seite


* Tiefe

   * Übergeordneter Pfad
   * Nur direkte untergeordnete Elemente
   * Zusätzliche Ebenen von untergeordneten Elementen
   * Ebenen

Die resultierende Datei `export.csv` kann in Excel (oder einer anderen kompatiblen Anwendung) geöffnet werden.

![chlimage_1-58](assets/chlimage_1-58.png)

Die Erstellung **CSV-Export** ist beim Durchsuchen der **Sites** Konsole (in der Listenansicht): ist eine Option der **Erstellen** Dropdown-Menü:

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

So erstellen Sie einen CSV-Export:

1. Öffnen Sie die **Sites-Konsole** und wechseln Sie zum gewünschten Verzeichnis, falls erforderlich.
1. Wählen Sie in der Symbolleiste **Erstellen** then **CSV-Export** um den Assistenten zu öffnen:

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. Wählen Sie die zu exportierenden Eigenschaften aus.
1. Wählen Sie **Erstellen**.
