---
title: Mehrere Mandanten für Sammlungen, Snippets und Snippet-Vorlagen
description: Trennen Sie Inhalte im CRX-Repository nach Kundenorganisation, um unbefugten Zugriff zu verhindern.
contentOwner: AG
feature: Sammlungen
role: Architektur,Administrator,Leiter
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 34%

---


# Mehrere Mandanten für Sammlungen, Snippets und Snippet-Vorlagen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Multi-Tenancy-Funktion können Sie Inhalte in CRX auf Basis von Präfix und ID der Organisation trennen, um die Inhalte vor unberechtigtem Zugriff durch Anwender von anderen Unternehmen zu schützen.

Adobe Experience Manager (AEM) Assets speichert Daten für jede Organisation in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Präfix und die Organisations-ID identifiziert.
die im traditionellen Speicherort enthalten ist, an dem verschiedene Asset-Typen in CRX gespeichert werden.

Wenn Sie beispielsweise einen Ordner mit dem Namen `Demo` erstellen, speichert AEM Assets standardmäßig den Ordner unter `../content/dam/Demo` in CRX. Bei aktivierter Funktion für mehrere Mandanten können Sie die Daten unter `../content/dam/<organization prefix>/<organization id>Demo` speichern.

Beispielsweise können Sie für Adobe Marketing Cloud-Benutzer von AEM Assets (On-Demand), die `aodpremium`-Unternehmen zugewiesen sind, die Funktion für mehrere Mandanten verwenden, um den folgenden Pfad zu `../content/dam/mac/aodpremiumDemo` zu konfigurieren und den Inhalt zu trennen. In diesem Beispiel ist `mac` das Organisations-Präfix und `aodpremium` die Organisations-ID.

Auf Basis von Organisation und ID des Benutzers wird dieser qualifizierte Pfad in der Benutzeroberfläche und in verschiedenen Assistenten von AEM Assets angezeigt, darunter die Assistenten für Verschiebung und Snippet-Erstellung zur Durchsetzung der Trennung.

Mit der Funktion für mehrere Mandanten können Sie die folgenden Assets und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten &quot;Seite Hinzufügen/auswählen&quot;)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
