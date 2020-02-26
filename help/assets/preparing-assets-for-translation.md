---
title: Vorbereiten von Assets für die Übersetzung
description: Erstellen Sie Stammordner für Sprachen, um die Übersetzung mehrsprachiger Assets vorzubereiten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Vorbereiten von Assets für die Übersetzung {#preparing-assets-for-translation}

Bei mehrsprachigen Assets handelt es sich um Assets mit Binärdateien, Metadaten und Tags in verschiedenen Sprachen. Im Allgemeinen liegen Binärdateien, Metadaten und Tags für Assets in einer Sprache vor, die dann in andere Sprachen für die Verwendung in mehrsprachigen Projekten übersetzt werden.

In Adobe Experience Manager (AEM) Assets sind mehrsprachige Assets in Ordnern enthalten, wobei jeder Ordner die Assets in einer anderen Sprache enthält.

Jeder Sprachordner wird als eine Sprachkopie bezeichnet. Der Stammordner einer Sprachkopie, auch als Sprachstamm bezeichnet, identifiziert die Sprache des Inhalts in der Sprachkopie. For example, */content/dam/it* is the Italian language root for the Italian language copy. Language copies must use a [correctly-configured language root](preparing-assets-for-translation.md#creating-a-language-root) so that the correct language is targeted when translations of source assets are performed.

Die Sprachkopie, für die Sie ursprünglich Assets hinzufügen, ist die Sprachmustervorlage. Die Sprachmustervorlage ist die Quelle, die in andere Sprachen übersetzt wird.

Die Beispielordnerhierarchie enthält mehrere Sprachstämme:

```java
/content
    /- dam
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

Führen Sie die folgenden Schritte aus, um Ihre Assets für die Übersetzung vorzubereiten:

1. Erstellen Sie den Sprachstamm für Ihren Sprach-Master. Beispielsweise ist der Sprachstamm der englischen Sprachkopie in der Beispielordnerhierarchie `/content/dam/en`. Ensure that the language root is correctly configured according to the information in [Creating a Language Root](preparing-assets-for-translation.md#creating-a-language-root).

1. Fügen Sie Assets zu Ihrer Sprachmustervorlage hinzu.
1. Erstellen Sie den Sprachstamm der jeweiligen Zielsprache, für die Sie eine Sprachkopie benötigen.

## Erstellen eines Sprachstamms {#creating-a-language-root}

Um den Sprachstamm zu erstellen, erstellen Sie einen Ordner und verwenden Sie einen ISO-Sprachcode als Wert für die Name-Eigenschaft. Nachdem Sie den Sprachstamm erstellt haben, können Sie eine Sprachkopie auf jeder beliebigen Ebene im Sprachstamm erstellen.

For example, the root page of the Italian language copy of the sample hierarchy has `it` as the Name property. The Name property is used as the name of the asset node in the repository, and therefore determines the path of the assets. (`https://[AEM_server]:[port]/assets.html/content/dam/it/*`)

1. Tippen/Klicken Sie in der Assets-Konsole auf **[!UICONTROL Erstellen]** und wählen Sie im Menü die Option **[!UICONTROL Ordner]** aus.

   ![chlimage_1-120](assets/chlimage_1-120.png)

1. In the Name field type the country code in the format of `<language-code>`.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Erstellen]**. Der Sprachstamm wird in der Konsole „Assets“ erstellt. 

## Anzeigen von Sprachstämmen {#viewing-language-roots}

Die Touch-optimierte Benutzeroberfläche bietet einen Bereich „Verweise“, der eine Liste von Sprachstämmen anzeigt, die in AEM Assets erstellt wurden.

1. In der Konsole „Assets“ wählen Sie die Sprachmustervorlage aus, für die Sie Sprachkopien erstellen möchten.
1. Klicken oder tippen Sie auf das GlobalNav-Symbol und wählen Sie **[!UICONTROL Verweise]** aus, um den Bereich „Verweise“ zu öffnen.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. Im Bereich „Verweise“ klicken oder tippen Sie auf **[!UICONTROL Sprachkopien]**. Der Bereich „Sprachkopien“ zeigt die Sprachkopien der Assets an.

   ![chlimage_1-123](assets/chlimage_1-123.png)

