---
title: Badges-Konsole
seo-title: Badges-Konsole
description: Mit der Konsole "Communities-Badges"können Sie benutzerdefinierte Abzeichen hinzufügen, die Mitgliedern angezeigt werden können, wenn sie eine bestimmte Rolle in der Community übernehmen (zugewiesen)
seo-description: Mit der Konsole "Communities-Badges"können Sie benutzerdefinierte Abzeichen hinzufügen, die Mitgliedern angezeigt werden können, wenn sie eine bestimmte Rolle in der Community übernehmen (zugewiesen)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 5%

---


# Badges-Konsole {#badges-console}

## Info zu Kennzeichen {#about-badges}

Die Communities Badges-Konsole bietet die Möglichkeit, benutzerdefinierte Abzeichen hinzuzufügen, die für ein Mitglied angezeigt werden können, wenn es verdient (verliehen) oder eine bestimmte Rolle in der Community übernimmt (zugewiesen).

### Badge-Sichtbarkeit {#badge-visibility}

Derzeit werden Kennzeichen, die ein Community-Mitglied verdient oder zugewiesen wird, zusammen mit ihrem Namen und Avatar an den folgenden Orten angezeigt:

* Profile
* [Foren](forum.md)
* [Frage und Antwort](working-with-qna.md)
* [Leadership-Pinnwände](enabling-leaderboard.md)
* [Ideen](ideation-feature.md)

In der Umgebung &quot;Autor&quot;zur Konsole &quot;Badges&quot;

* Aus globaler Navigation: **[!UICONTROL Tools > Communities > Badges]**

Diese Konsole zeigt die derzeit verfügbaren Abzeichen an, aus denen neue Abzeichen hinzugefügt werden können.

![chlimage_1-242](assets/chlimage_1-242.png)

## Abzeichen erstellen {#create-badge}

Eine Markierung wird erstellt, indem ein entsprechend kleines Bild hochgeladen wird (72 dpi mit einer Höhe von 26-32 Pixel) und ein Name angegeben wird. Das Abzeichen wird im Repository unter `/etc/community/badging/images` gespeichert und automatisch in die Umgebung &quot;publish&quot;repliziert.

Wenn die Veröffentlichungs-Umgebung eine Herausgeberfarm ist, müssen Sie [Benutzersynchronisierung](sync.md) konfigurieren.

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Bild hochladen]**

   (*Erforderlich*) Ein Abzeichen mit einer empfohlenen Größe von 32 x 32 Pixel bei 72 dpi im JPEG- oder PNG-Format.

* **[!UICONTROL Name]**

   (*Erforderlich*) Der Markenname. Es handelt sich um den standardmäßigen `Display Name`- sowie den Repository-Knotennamen. Wenn `Name` kein gültiger Repository-Knotenname ist, wird er geändert.

* **[!UICONTROL Anzeigename]**

   (*Optional*) Der Name, der für das Zeichen in der Benutzeroberfläche angezeigt werden soll. Standard ist der unveränderte Text, der für `Name` eingegeben wird.

* **[!UICONTROL Beschreibung]**

   (*Optional*) Eine Beschreibung für das Zeichen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen zum Einrichten von Scoring- und Badging-Regeln finden Sie unter [Scoring and Badges](implementing-scoring.md).

Informationen zum Verwalten von Abzeichen für Mitglieder finden Sie unter [Mitgliederkonsole](members.md).
