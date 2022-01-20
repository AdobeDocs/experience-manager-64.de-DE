---
title: Verwenden von "Gefällt mir"
seo-title: Using Liking
description: Hinzufügen und Konfigurieren der Komponente "Gefällt mir"
seo-description: Adding and configuring the Liking component
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: b5918a54-ef7b-4b3f-bca7-ed0344bab4aa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 7%

---

# Verwenden von &quot;Gefällt mir&quot; {#using-liking}

Die `Liking`-Komponente ist ein nützliches Tool, mit dem Benutzer zu einem bestimmten Inhalt Stellung nehmen können, z. B. zu einem Kommentar in einem Forum. Mit dem `Liking`-Komponente verwenden, wählen die Mitglieder das Herzsymbol aus, um eine positive Meinung anzuzeigen.

## Hinzufügen von &quot;Link&quot;zu einer Seite {#adding-liking-to-a-page}

So fügen Sie eine `Liking` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Liking`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position relativ zur Funktion, die den Benutzern gefällt.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](essentials-liking.md#essentials-for-client-side) eingeschlossen sind, wird die `Liking` wird angezeigt.

![chlimage_1-93](assets/chlimage_1-93.png)

## Konfigurieren der Verknüpfung {#configuring-liking}

Wählen Sie die platzierte `Liking` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![chlimage_1-94](assets/chlimage_1-94.png)

Unter dem **[!UICONTROL Texte und Beschriftungen]** -Registerkarte die Eigenschaften angeben, die zum Aufzeichnen von &quot;Gefällt mir&quot;verwendet werden.

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

Weitere Informationen finden Sie unter [Gefällt mir-Grundlagen](essentials-liking.md) für Entwickler.
