---
title: Verwenden von Bewertungen
seo-title: Using Ratings
description: Hinzufügen einer Bewertungskomponente zu einer Seite
seo-description: Adding a Rating component to a page
uuid: a986970b-1221-4648-9a69-410f4480e0ae
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a0e5491e-66bc-47b0-94a5-45a02bc558da
exl-id: 1de28140-5334-4ca2-a476-5ad253809808
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 6%

---

# Verwenden von Bewertungen {#using-ratings}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Die `Rating`-Komponente wird eigenständig oder in Verbindung mit anderen Communities-Funktionen verwendet. Diese Komponente ermöglicht es angemeldeten Community-Mitgliedern, ihre Meinung durch Bewertung von Inhalten zu äußern.

## Hinzufügen einer Bewertung zu einer Seite {#adding-a-rating-to-a-page}

So fügen Sie eine `Rating`Komponente auf einer Seite im Autorenmodus zu finden, die Komponente `Communities / Rating` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position relativ zur Funktion, die Mitglieder bewerten sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](rating-basics.md#essentials-for-client-side) eingeschlossen sind, wird die `Rating` wird angezeigt.

![chlimage_1-493](assets/chlimage_1-493.png)

## Konfigurieren der Bewertung {#configuring-rating}

Wählen Sie die platzierte `Rating` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-494](assets/chlimage_1-494.png)

Unter dem **[!UICONTROL Texte und Beschriftungen]** -Registerkarte geben Sie die interne Kennung für die Bewertung an.

![chlimage_1-495](assets/chlimage_1-495.png)

**[!UICONTROL Tally Name]**
(*Erforderlich*) Ein einfacher Name für `Rating`die diese Instanz eindeutig identifiziert. Muss ein gültiger Knotenname für das Repository sein.

## Site-Besuchererlebnis {#site-visitor-experience}

### Mitglieder {#members}

Pro Mitglied ist nur eine Bewertung zulässig. Das Mitglied kann sein Rating jederzeit ändern.

### Anonym {#anonymous}

Das anonyme Posten einer Bewertung wird nicht unterstützt. Besucher der Site müssen sich registrieren (Mitglied werden) und sich anmelden, um teilnehmen zu können.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Bewertungsgrundlagen](rating-basics.md) für Entwickler.
