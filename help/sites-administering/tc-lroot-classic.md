---
title: Erstellen eines Sprachstamms mithilfe der klassischen Benutzeroberfläche
seo-title: Creating a Language Root Using the Classic UI
description: Erfahren Sie, wie Sie mithilfe der klassischen Benutzeroberfläche einen Sprachstamm erstellen.
seo-description: Learn how to create a language root using the Classic UI.
uuid: d44a51a0-1507-4838-851c-cacff48ad825
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 237b8cc6-158e-4c51-970d-4c9cc74f6496
feature: Language Copy
exl-id: 316903a8-22cf-45e6-a9f3-ac1d75beddec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 32%

---

# Erstellen eines Sprachstamms mithilfe der klassischen Benutzeroberfläche{#creating-a-language-root-using-the-classic-ui}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Im folgenden Verfahren wird die klassische Benutzeroberfläche verwendet, um einen Sprachstamm einer Site zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Sprachstamms](/help/sites-administering/tc-prep.md#creating-a-language-root).

1. Wählen Sie in der Websites-Konsole in der Website-Struktur die Stammseite der Site aus. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Fügen Sie eine neue untergeordnete Seite hinzu, die die Sprachversion der Site darstellt:

   1. Klicken Sie auf Neu > Neue Seite.
   1. Geben Sie in das Dialogfeld den Titel und den Namen ein. Der Name muss im Format `<language-code>` oder `<language-code>_<country-code>`, vorliegen, wie beispielsweise en, en_US, en_us, en_GB, en_gb.

      * Der unterstützte Sprachcode ist ein aus zwei Buchstaben bestehender Code in Kleinbuchstaben gemäß ISO-639-1.
      * Der unterstützte Ländercode ist ein aus zwei Buchstaben bestehender Code in Kleinbuchstaben oder Großbuchstaben gemäß ISO 3166.
   1. Wählen Sie die Vorlage aus und klicken Sie auf Erstellen .

   ![newpagefr](assets/newpagefr.png)

1. Wählen Sie in der Websites-Konsole in der Website-Struktur die Stammseite der Site aus.
1. Wählen Sie im Menü Tools die Option Sprachkopie aus.

   ![toolslanguagecopy](assets/toolslanguagecopy.png)

   Das Dialogfeld Sprachkopie zeigt eine Matrix der verfügbaren Sprachversionen und Webseiten an. Ein x in einer Sprachspalte bedeutet, dass die Seite in dieser Sprache verfügbar ist.

   ![languagecopydialog](assets/languagecopydialog.png)

1. Um eine vorhandene Seite oder Seitenstruktur in eine Sprachversion zu kopieren, wählen Sie die Zelle für diese Seite in der Sprachspalte aus. Klicken Sie auf den Pfeil und wählen Sie den Typ der zu erstellenden Kopie aus.

   Im folgenden Beispiel wird die Seite &quot;Ausrüstung/Sonnenbrille/Irian&quot;in die französische Sprachversion kopiert.

   ![languagecopydilogdropdown](assets/languagecopydilogdropdown.png)

   | Art der Sprachkopie | Beschreibung |
   |---|---|
   | auto | Übernimmt das Verhalten der übergeordneten Seiten |
   | ignore | Erstellt keine Kopie dieser Seite und ihrer untergeordneten Elemente |
   | `<language>+` (z. B. French+) | Kopiert die Seite und alle untergeordneten Elemente aus dieser Sprache |
   | `<language>` (z. B. French) | Kopiert nur die Seite aus dieser Sprache |

1. Klicken Sie auf „OK“, um das Dialogfeld zu schließen.
1. Klicken Sie im nächsten Dialogfeld auf Ja , um die Kopie zu bestätigen.
