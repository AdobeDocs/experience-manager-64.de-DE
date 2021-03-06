---
title: Erstellen eines Sprach-Stamms mithilfe der klassischen Benutzeroberfläche
seo-title: Creating a Language Root Using the Classic UI
description: Erfahren Sie, wie Sie einen Sprach-Stamm mithilfe der klassischen Benutzeroberfläche erstellen.
seo-description: Learn how to create a language root using the Classic UI.
uuid: d44a51a0-1507-4838-851c-cacff48ad825
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 237b8cc6-158e-4c51-970d-4c9cc74f6496
feature: Language Copy
exl-id: 316903a8-22cf-45e6-a9f3-ac1d75beddec
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 79%

---

# Erstellen eines Sprach-Stamms mithilfe der klassischen Benutzeroberfläche{#creating-a-language-root-using-the-classic-ui}

Im folgenden Verfahren wird die klassische Benutzeroberfläche zum Erstellen eines Sprach-Stamms einer Website verwendet. Weitere Informationen hierzu finden Sie unter [Erstellen eines Sprach-Stamms](/help/sites-administering/tc-prep.md#creating-a-language-root).

1. Wählen Sie in der Websites-Konsole in der Baumstruktur „Websites“ die Stammseite der Website aus. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Fügt eine neue untergeordnete Seite hinzu, welche die Sprachversion der Website darstellt:

   1. Klicken Sie auf „Neu“ > „Neue Seite“.
   1. Geben Sie in das Dialogfeld den Titel und den Namen ein. Der Name muss im Format `<language-code>` oder `<language-code>_<country-code>`, z. B. en, en_US, en_us, en_GB, en_gb.

      * Der unterstützte Sprachcode ist ein aus zwei Buchstaben bestehender Code in Kleinbuchstaben gemäß ISO-639-1
      * Der unterstützte Ländercode ist ein aus zwei Buchstaben bestehender Code in Klein- oder Großbuchstaben gemäß ISO-3166
   1. Wählen Sie die Vorlage aus und klicken Sie auf „Erstellen“.

   ![newpagefr](assets/newpagefr.png)

1. Wählen Sie in der Websites-Konsole in der Baumstruktur „Websites“ die Stammseite der Website aus.
1. Wählen Sie im Menü „Tools“ die Option „Sprachkopie“.

   ![toolslanguageCopy](assets/toolslanguagecopy.png)

   Das Dialogfeld „Sprachkopie“ zeigt eine Matrix der verfügbaren Sprachversionen und der Webseiten. Ein x in einer Sprachspalte bedeutet, dass die Seite in dieser Sprache verfügbar ist.

   ![languagecopydialog](assets/languagecopydialog.png)

1. Zum Kopieren einer vorhandenen Seite oder der Seitenbaumstruktur in eine Sprachversion wählen Sie die Zelle für diese Seite in der Sprachspalte aus. Klicken Sie auf den Pfeil und wählen Sie dann zum Erstellen die gewünschte Art der Kopie aus.

   Im folgenden Beispiel wird die Seite „Ausrüstung“/„Sonnenbrille“/„Irian“ in die französische Sprachversion kopiert.

   ![languageCopyDilogdown](assets/languagecopydilogdropdown.png)

   | Art der Sprachkopie | Beschreibung |
   |---|---|
   | auto | Verwendet das Verhalten von übergeordneten Seiten |
   | ignore | Erstellt keine Kopie dieser Seite und ihrer untergeordneten Elemente |
   | `<language>+` (z. B. Französisch+) | Kopiert die Seite und alle untergeordneten Elemente aus dieser Sprache |
   | `<language>` (z. B. Französisch) | Kopiert nur die Seite aus dieser Sprache |

1. Klicken Sie auf „OK“, um das Dialogfeld zu schließen.
1. Klicken Sie im nächsten Dialogfeld auf „Ja“, um die Kopie zu bestätigen.
