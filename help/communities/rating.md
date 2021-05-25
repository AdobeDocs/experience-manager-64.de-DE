---
title: Verwenden von Bewertungen
seo-title: Verwenden von Bewertungen
description: Hinzufügen einer Bewertungskomponente zu einer Seite
seo-description: Hinzufügen einer Bewertungskomponente zu einer Seite
uuid: a986970b-1221-4648-9a69-410f4480e0ae
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a0e5491e-66bc-47b0-94a5-45a02bc558da
exl-id: 1de28140-5334-4ca2-a476-5ad253809808
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 38%

---

# Verwenden von Bewertungen {#using-ratings}

Die Komponente `Rating`wird eigenständig oder in Verbindung mit anderen Communities-Funktionen verwendet. Diese Komponente ermöglicht es angemeldeten Community-Mitgliedern, ihre Meinung durch Bewertung von Inhalten zu äußern.

## Hinzufügen einer Bewertung zu einer Seite {#adding-a-rating-to-a-page}

Um eine `Rating`Komponente zu einer Seite im Autorenmodus hinzuzufügen, suchen Sie die Komponente `Communities / Rating` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an eine Position relativ zur Funktion, die Mitglieder bewerten sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](rating-basics.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Rating` so angezeigt.

![chlimage_1-493](assets/chlimage_1-493.png)

## Konfigurieren einer Bewertung {#configuring-rating}

Wählen Sie die platzierte Komponente `Rating` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-494](assets/chlimage_1-494.png)

Legen Sie auf der Registerkarte **[!UICONTROL Texte &amp; Beschriftungen]** die interne ID der Bewertung fest.

![chlimage_1-495](assets/chlimage_1-495.png)

**[!UICONTROL Tally Name]**
 (*Erforderlich*) Ein einfacher Name für die ,  `Rating`die diese Instanz eindeutig identifiziert. Es muss sich um einen gültigen Knotennamen des Verzeichnisses handeln.

## Site-Besuchererlebnis  {#site-visitor-experience}

### Mitglieder {#members}

Pro Mitglied ist nur eine Bewertung zulässig.  Das Mitglied kann seine Meinung jedoch jederzeit ändern.

### Anonym {#anonymous}

Das anonyme Posten von Bewertungen wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Bewertungsgrundlagen](rating-basics.md) für Entwickler.
