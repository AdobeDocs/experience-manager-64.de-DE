---
title: Mehrere Mandanten für Sammlungen, Snippets und Snippet-Vorlagen
description: Trennen Sie Inhalte im CRX-Repository nach Kundenorganisation, um unbefugten Zugriff zu verhindern.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 34%

---


# Multi-tenancy for collections, snippets, and snippet templates {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Multi-Tenancy-Funktion können Sie Inhalte in CRX auf Basis von Präfix und ID der Organisation trennen, um die Inhalte vor unberechtigtem Zugriff durch Anwender von anderen Unternehmen zu schützen.

Adobe Experience Manager (AEM) Assets speichert Daten für jede Organisation in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Präfix und die Organisations-ID identifiziert.
die im traditionellen Speicherort enthalten ist, an dem verschiedene Asset-Typen in CRX gespeichert werden.

For example, if you create a folder named `Demo`, AEM assets by default stores the folder at `../content/dam/Demo` location in CRX. Bei aktivierter Funktion für mehrere Mandanten können Sie die Daten unter `../content/dam/<organization prefix>/<organization id>Demo`speichern.

For example, for Adobe Marketing Cloud users of AEM Assets (on-demand) that are assigned to `aodpremium` organization, you can use the multi-tenancy feature to configure the following path to `../content/dam/mac/aodpremiumDemo`, segregate the content. In diesem Beispiel `mac` ist das Organisations-Präfix und `aodpremium` die Organisations-ID.

Auf Basis von Organisation und ID des Benutzers wird dieser qualifizierte Pfad in der Benutzeroberfläche und in verschiedenen Assistenten von AEM Assets angezeigt, darunter die Assistenten für Verschiebung und Snippet-Erstellung zur Durchsetzung der Trennung.

Mit der Funktion für mehrere Mandanten können Sie die folgenden Assets und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten &quot;Seite Hinzufügen/auswählen&quot;)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
