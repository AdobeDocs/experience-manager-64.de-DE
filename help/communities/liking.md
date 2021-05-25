---
title: Verwenden von "Gefällt mir"
seo-title: Verwenden von "Gefällt mir"
description: Hinzufügen und Konfigurieren der Komponente "Gefällt mir"
seo-description: Hinzufügen und Konfigurieren der Komponente "Gefällt mir"
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: b5918a54-ef7b-4b3f-bca7-ed0344bab4aa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 7%

---

# Verwenden von &quot;Gefällt mir&quot;-Klicks {#using-liking}

Die Komponente `Liking`ist ein nützliches Tool, mit dem Benutzer eine Meinung zu einem bestimmten Inhaltselement, z. B. zu einem Kommentar in einem Forum, äußern können. Mit der Komponente `Liking`wählen die Mitglieder das Herzsymbol aus, um eine positive Meinung anzuzeigen.

## Hinzufügen von &quot;Link&quot;zu einer Seite {#adding-liking-to-a-page}

Um eine Komponente `Liking` im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Liking`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position relativ zur Funktion, die den Benutzern gefällt.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](essentials-liking.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Liking` so angezeigt.

![chlimage_1-93](assets/chlimage_1-93.png)

## Konfigurieren von Link {#configuring-liking}

Wählen Sie die platzierte Komponente `Liking` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![chlimage_1-94](assets/chlimage_1-94.png)

Geben Sie auf der Registerkarte **[!UICONTROL Texte und Beschriftungen]** die Eigenschaften an, die zum Aufzeichnen von &quot;Gefällt mir&quot;-Klicks verwendet werden.

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL Beschriftung für positive Antwort]**
(
*Erforderlich*) Der Eigenschaftsname für eine positive Antwort.

* **[!UICONTROL Beschriftung für negative Antwort]**
(
*Erforderlich*) Der Eigenschaftsname für eine negative Antwort.

* **[!UICONTROL Zählername]**
(
*Erforderlich*) Der interne, identifizierbare Eigenschaftsname für diese Instanz einer Abstimmungskomponente.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Die Mitglieder können ihre Art jederzeit ändern.

### Anonym {#anonymous}

Anonyme &quot;Gefällt mir&quot;-Klicks werden nicht unterstützt. Besucher der Site müssen sich registrieren (Mitglied werden) und sich anmelden, um an &quot;Gefällt mir&quot;-Klicks teilnehmen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Gefällt mir-Grundlagen](essentials-liking.md) für Entwickler.
