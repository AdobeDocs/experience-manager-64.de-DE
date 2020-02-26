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
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b

---


# Badges-Konsole {#badges-console}

## Info zu Abzeichen {#about-badges}

Die Communities Badges-Konsole bietet die Möglichkeit, benutzerdefinierte Abzeichen hinzuzufügen, die für ein Mitglied angezeigt werden können, wenn es verdient (verliehen) oder eine bestimmte Rolle in der Community übernimmt (zugewiesen).

### Sichtbarkeit der Abzeichen {#badge-visibility}

Derzeit werden Kennzeichen, die ein Community-Mitglied verdient oder zugewiesen wird, zusammen mit ihrem Namen und Avatar an folgenden Stellen angezeigt:

* Profile
* [Foren](forum.md)
* [Frage und Antwort](working-with-qna.md)
* [LEITPinnwände](enabling-leaderboard.md)
* [Ideen](ideation-feature.md)

In der Autorenumgebung, um die Badges-Konsole zu erreichen

* Aus globaler Navigation: **[!UICONTROL Werkzeuge > Communities > Abzeichen]**

Diese Konsole zeigt die derzeit verfügbaren Abzeichen an, aus denen neue Abzeichen hinzugefügt werden können.

![chlimage_1-242](assets/chlimage_1-242.png)

## Abzeichen erstellen {#create-badge}

Eine Markierung wird erstellt, indem ein entsprechend kleines Bild hochgeladen wird (72 dpi mit einer Höhe von 26-32 Pixel) und ein Name angegeben wird. Das Abzeichen wird im Repository gespeichert `/etc/community/badging/images` und automatisch in die Veröffentlichungsumgebung repliziert.

Wenn die Veröffentlichungsumgebung eine Herausgeberfarm ist, müssen Sie die [Benutzersynchronisierung](sync.md)konfigurieren.

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Bild hochladen]**

   (*Erforderlich*) Ein Badge-Bild mit einer empfohlenen Größe von 32 x 32 Pixel bei 72 dpi im JPEG- oder PNG-Format.

* **[!UICONTROL Name]**

   (*Erforderlich*) Der Markenname. Dies ist der Standardname `Display Name` sowie der Repository-Knotenname. Wenn der Knoten kein gültiger Repository-Knotenname `Name` ist, wird er geändert.

* **[!UICONTROL Anzeigename]**

   (*Optional*) Der Name, der für das Zeichen in der Benutzeroberfläche angezeigt wird. &quot;Standard&quot;ist der unveränderte Text, der für die `Name`Variable eingegeben wurde.

* **[!UICONTROL Beschreibung]**

   (*Optional*) Eine Beschreibung für das Zeichen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen zum Einrichten von Scoring- und Kennzeichnungsregeln finden Sie unter [Scoring and Badges](implementing-scoring.md).

Informationen zum Verwalten von Abzeichen für Mitglieder finden Sie unter [Mitglieder-Konsole](members.md).
