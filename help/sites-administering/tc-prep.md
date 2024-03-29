---
title: Vorbereiten von Inhalten für die Übersetzung
seo-title: Preparing Content for Translation
description: Erfahren Sie, wie Sie Inhalte für die Übersetzung vorbereiten.
seo-description: Learn how to prepare content for translation.
uuid: 369630a8-2ed7-48db-973e-bd8213231d49
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 8bd67d71-bcb7-4ca0-9751-3ff3ee054011
feature: Language Copy
exl-id: 1a7fe230-093b-4d2b-95cb-f9479c0febe5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 78%

---

# Vorbereiten von Inhalten für die Übersetzung{#preparing-content-for-translation}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Bei mehrsprachigen Websites wird in der Regel ein Teil der Inhalte in mehreren Sprachen bereitgestellt. Die Website wird in einer Sprache verfasst und anschließend in weitere Sprachen übersetzt. Im Allgemeinen bestehen mehrsprachige Websites aus Zweigen von Seiten, wobei jeder Zweig die Seiten der Website in einer anderen Sprache enthält.

Die Beispiel-Geometrixx Demosite enthält mehrere Sprachzweige und weist die folgende Struktur auf:

```xml
/content
    |- geometrixx
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

Jeder Sprachzweig einer Website wird als Sprachkopie bezeichnet. Die Stammseite einer Sprachkopie, auch als Sprachstamm bezeichnet, identifiziert die Sprache des Inhalts in der Sprachkopie. Beispielsweise stellt `/content/geometrixx/fr` den Sprachstamm der französischen Sprachkopie dar. Sprachkopien müssen einen [korrekt konfigurierten Sprachstamm](/help/sites-administering/tc-prep.md#creating-a-language-root) verwenden, damit die korrekte Sprache angesprochen wird, wenn Übersetzungen von einer Quell-Website durchgeführt werden.

Die Sprachkopie, für die Sie ursprünglich Inhalte verfassen, ist der Sprach-Master. Die Sprach-Master-Vorlage ist die Quelle, die in andere Sprachen übersetzt wird.

Führen Sie die folgenden Schritte aus, um Ihre Website für die Übersetzung vorzubereiten:

1. Erstellen Sie den Sprachstamm für Ihren Sprach-Master. Der Sprachstamm der englischen Beispiel-Geometrixx-Website ist z. B. /content/geometrixx/en. Stellen Sie sicher, dass der Sprachstamm entsprechend den Informationen unter [Erstellen eines Sprachstamms](/help/sites-administering/tc-prep.md#creating-a-language-root) konfiguriert ist.
1. Verfassen Sie den Inhalt des Sprach-Masters.
1. Erstellen Sie den Sprachstamm jeder Sprachkopie für die Website. Beispielsweise lautet die französische Sprachkopie der Geometrixx-Beispiel-Site /content/geometrixx/fr.

Wenn Sie die Inhalte für die Übersetzung vorbereitet haben, können Sie automatisch fehlende Seiten in den Sprachkopien und zugehörigen Übersetzungsprojekten erstellen. (Siehe [Erstellen eines Übersetzungsprojekts](/help/sites-administering/tc-manage.md).) Einen Überblick über den Prozess der Inhaltsübersetzung in AEM finden Sie unter [Übersetzen von Inhalten für mehrsprachige Websites](/help/sites-administering/translation.md).

## Erstellen eines Sprachstamms {#creating-a-language-root}

Erstellen Sie einen Sprachstamm als Stammseite einer Sprachkopie, die die Sprache der Inhalte identifiziert. Nachdem Sie den Sprachstamm erstellt haben, können Sie Übersetzungsprojekte erstellen, die die Sprachkopie umfassen.

Um den Sprachstamm zu erstellen, erstellen Sie eine Seite und verwenden Sie einen ISO-Sprach-Code als Wert für die Eigenschaft Name. Der Sprach-Code muss eines der folgenden Formate aufweisen:

* `<language-code>`Der unterstützte Sprach-Code ist ein Code mit zwei Buchstaben gemäß ISO-639-1, zum Beispiel `en`.

* `<language-code>_<country-code>` oder `<language-code>-<country-code>` – Der unterstützte Länder-Code ist ein Code mit zwei Groß- oder zwei Kleinbuchstaben gemäß ISO 3166, zum Beispiel `en_US`, `en_us`, `en_GB`, `en-gb`.

Sie können jedes dieser Formate verwenden, passend zur Struktur Ihrer globalen Website.  Beispielsweise verfügt die Stammseite der französischen Sprachkopie der Geometrixx-Website über die „Name“-Eigenschaft `fr`. Beachten Sie, dass die Eigenschaft Name als Name des Seitenknotens im Repository verwendet wird und daher den Pfad der Seite bestimmt. (http://localhost:4502/content/geometrixx/fr.html)

Im folgenden Verfahren wird die Touch-optimierte Benutzeroberfläche verwendet, um eine Sprachkopie einer Website zu erstellen. Anweisungen zur Verwendung der klassischen Benutzeroberfläche finden Sie unter [Erstellen eines Sprachstamms mithilfe der klassischen Benutzeroberfläche](/help/sites-administering/tc-lroot-classic.md).

1. Navigieren Sie zu Sites .
1. Klicken oder tippen Sie auf die Website, für die Sie eine Sprachkopie erstellen möchten.

   Wenn Sie beispielsweise eine Sprachkopie der Geometrixx Outdoors-Site erstellen möchten, klicken oder tippen Sie auf Geometrixx Outdoors-Site.

1. Klicken oder tippen Sie auf „Erstellen“ und anschließend auf „Seite erstellen“.

   ![chlimage_1-21](assets/chlimage_1-21.png)

1. Wählen Sie die Seitenvorlage aus und klicken oder tippen Sie auf Weiter.
1. Geben Sie in den Feldtyp Name den Länder-Code im Format `<language-code>` oder `<language-code>_<country-code>` ein, z. B. `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Geben Sie einen Titel für die Seite ein.

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Klicken oder tippen Sie auf Erstellen. Klicken oder tippen Sie im Bestätigungsdialogfeld auf **Fertig**, um zur Sites-Konsole zurückzukehren, oder auf **Öffnen**, um die Sprachkopie zu öffnen.

## Anzeigen des Status der Sprachstämme {#seeing-the-status-of-language-roots}

Die Touch-optimierte Benutzeroberfläche bietet einen Bereich &quot;Verweise&quot;, der eine Liste der erstellten Sprachstämme anzeigt.

![chlimage_1-23](assets/chlimage_1-23.png)

Das folgende Verfahren verwendet die Touch-optimierte Benutzeroberfläche, um den Bereich „Verweise“ für eine Seite anzuzeigen.

1. Wählen Sie in der Sites-Konsole eine Seite der Website aus und klicken oder tippen Sie auf **Verweise**.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Klicken oder tippen Sie im Bereich &quot;Verweise&quot;auf **Sprachkopien**. Im Bereich Sprachkopien werden die Sprachkopien der Website angezeigt.
