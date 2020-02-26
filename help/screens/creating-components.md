---
title: Erstellen von Komponenten
seo-title: Erstellen von Komponenten
description: AEM-Komponenten werden verwendet, um den Inhalt, den Sie auf Ihren Web-Seiten bereitstellen, zu speichern, zu formatieren und zu rendern. Folgen Sie dieser Seite, um mehr über das Authoring von Kanälen und das Rendern von Komponenten zu erfahren.
seo-description: AEM-Komponenten werden verwendet, um den Inhalt, den Sie auf Ihren Web-Seiten bereitstellen, zu speichern, zu formatieren und zu rendern. Folgen Sie dieser Seite, um mehr über das Authoring von Kanälen und das Rendern von Komponenten zu erfahren.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
translation-type: tm+mt
source-git-commit: c50bb754fb99efdb4d54158614abe823d2cbc4d9

---


# Erstellen von Komponenten{#creating-components}

AEM-Komponenten werden verwendet, um den Inhalt, den Sie auf Ihren Web-Seiten bereitstellen, zu speichern, zu formatieren und zu rendern.

>[!NOTE]
>
>To learn about the details of creating AEM Components, see [Developing AEM Components].

## Authoring von Kanälen {#authoring-channels}

Der Kanal ist das zentrale Objekt für Inhalte, die für eine Reihe von Displays bereitgestellt werden. Daher muss ein Inhaltsautor normalerweise einen Kanal im Editor öffnen, um Inhalt hinzuzufügen oder zu ändern. Da der Kanal eine ***cq:Page*** ist, folgt er demselben herkömmlichen UX-Muster zum Hinzufügen und Bearbeiten von Komponenten des Kanals.

Da jedoch Komponenten innerhalb eines Kanals normalerweise im Vollbildmodus gerendert werden, ist beim Authoring die Bearbeitung von einzelnen Komponenten und das Erstellen eines neuen Auftrags beeinträchtigt. Deshalb nutzt der Kanal Selektoren, um verschiedene Ansichten der Komponenten zu rendern. In der Authoring-Umgebung wird der Bearbeitungs-Selektor genutzt, um die benutzerdefinierte Kanalwiedergabe zu aktivieren.

For example, * [http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html)*

Der Benutzer muss sich während des Bearbeitens nicht um das Hinzufügen des Selektors zur URL kümmern. Eine Client-seitige Logik wartet auf das Ebenen-Wechselereignis und fügt den Selektor hinzu, wenn der Kanal den dedizierten Ressourcentyp *screens/core/components/channel* aufweist.

>[!NOTE]
>
>To learn about the basics on developing your AEM application using CRXDE Lite, See [Developing with CRXDE Lite].

## Rendern von Komponenten {#rendering-components}

Um eine korrekte Inhaltserstellung zu ermöglichen, müssen die Komponenten die folgenden beiden Wiedergaben bereitstellen:

| **Komponente** | **Wiedergaben** |
|---|---|
| *my-component/my-component.html* | Produktionswiedergabe |
| *my-component/edit.html* | Bearbeiten der Wiedergabe in einer kleineren Ansicht |

Die integrierten Komponenten nutzen die folgenden Client-Bibliothekskategorien:

| **Komponente** | **Client-Bibliothek** |
|---|---|
| *cq.screens.components.edit* | CSS und JS, die bei der Inhaltserstellung geladen werden müssen |
| *cq.screens.components.production* | CSS und JS, die geladen werden müssen, wenn der Kanal ausgeführt wird |
| *cq.screens.components* | freigegebene CSS und JS |

>[!NOTE]
>
>Um eigene Komponenten zu entwickeln, verwenden Sie die [Beispielvorlage für AEM Screens-Komponenten](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

