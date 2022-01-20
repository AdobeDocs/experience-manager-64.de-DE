---
title: Badges Console
seo-title: Badges Console
description: Mit der Communities Badges-Konsole können Sie benutzerdefinierte Abzeichen hinzufügen, die Mitgliedern angezeigt werden können, wenn sie eine bestimmte Rolle in der Community übernehmen (zugewiesen).
seo-description: The Communities Badges console lets you add custom badges that can be displayed for members when earned (awarded) or when they take on a specific role in the community (assigned)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Admin
exl-id: b6aa9d73-4e20-446a-a1fc-78f8968d6844
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 5%

---

# Badges Console {#badges-console}

## Über Abzeichen {#about-badges}

Die Communities-Badges-Konsole bietet die Möglichkeit, benutzerdefinierte Abzeichen hinzuzufügen, die einem Mitglied angezeigt werden können, wenn es eine bestimmte Rolle in der Community spielt (zugewiesen).

### Badge-Sichtbarkeit {#badge-visibility}

Derzeit werden Abzeichen, die ein Community-Mitglied erhält oder zugewiesen wird, zusammen mit seinem Namen und Avatar an den folgenden Stellen angezeigt:

* Profile
* [Foren](forum.md)
* [Frage und Antwort](working-with-qna.md)
* [Leaderboards](enabling-leaderboard.md)
* [Ideen](ideation-feature.md)

In der Autorenumgebung, um die Badges-Konsole zu erreichen

* Über die globale Navigation: **[!UICONTROL Tools > Communities > Abzeichen]**

In dieser Konsole werden die derzeit verfügbaren Abzeichen und die neuen Abzeichen angezeigt.

![chlimage_1-242](assets/chlimage_1-242.png)

## Abzeichen erstellen {#create-badge}

Ein Badge wird durch Hochladen eines entsprechend kleinen Bildes (72 dpi mit einer Höhe von 26-32 Pixel) und Angabe eines Namens erstellt. Das Badge-Bild wird im Repository unter `/etc/community/badging/images` und wird automatisch in die Veröffentlichungsumgebung repliziert.

Wenn es sich bei der Veröffentlichungsumgebung um eine Farm von Herausgebern handelt, müssen Sie [Benutzersynchronisierung](sync.md).

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Bild hochladen]**

   (*Erforderlich*) Ein Badge-Bild mit einer empfohlenen Größe von 32 x 32 Pixel bei 72 dpi im JPEG- oder PNG-Format.

* **[!UICONTROL Name]**

   (*Erforderlich*) Der Badge-Name. Dies ist die Standardeinstellung `Display Name` sowie den Repository-Knotennamen. Wenn die Variable `Name` kein gültiger Repository-Knotenname ist, wird er geändert.

* **[!UICONTROL Anzeigename]**

   (*Optional*) Der Name, der für das Zeichen in der Benutzeroberfläche angezeigt werden soll. Die Standardeinstellung ist der unveränderte Text, der für die `Name`.

* **[!UICONTROL Beschreibung]**

   (*Optional*) Eine Beschreibung für das Zeichen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen zum Einrichten von Scoring- und Badging-Regeln finden Sie unter [Scoring und Abzeichen](implementing-scoring.md).

Informationen zum Verwalten von Abzeichen für Mitglieder finden Sie unter [Mitgliederkonsole](members.md).
