---
title: Multi-Tenancy für Sammlungen, Snippets und Snippet-Vorlagen
description: Trennen Sie Inhalte im CRX-Repository basierend auf der Kundenorganisation, um unbefugten Zugriff zu verhindern.
contentOwner: AG
feature: Sammlungen
role: Architect,Administrator,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 35%

---

# Multi-Tenancy für Sammlungen, Snippets und Snippet-Vorlagen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Multi-Tenancy-Funktion können Sie Inhalte in CRX auf Basis von Präfix und ID der Organisation trennen, um die Inhalte vor unberechtigtem Zugriff durch Anwender von anderen Unternehmen zu schützen.

Adobe Experience Manager (AEM) Assets speichert Daten für jede Organisation in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Präfix der Organisation und die Organisations-ID identifiziert.
, die am herkömmlichen Speicherort enthalten ist, an dem verschiedene Asset-Typen in CRX gespeichert sind.

Wenn Sie z. B. einen Ordner mit dem Namen `Demo` erstellen, werden AEM Assets standardmäßig unter `../content/dam/Demo` in CRX gespeichert. Wenn die Funktion für mehrere Mandanten aktiviert ist, können Sie die Daten unter `../content/dam/<organization prefix>/<organization id>Demo` speichern.

Beispielsweise können Sie für Adobe Marketing Cloud-Benutzer von AEM Assets (On-Demand), die der `aodpremium`-Organisation zugewiesen sind, die Funktion für mehrere Mandanten verwenden, um den folgenden Pfad zu `../content/dam/mac/aodpremiumDemo` zu konfigurieren und den Inhalt zu trennen. In diesem Beispiel ist `mac` das Organisationspräfix und `aodpremium` die Organisations-ID.

Auf Basis von Organisation und ID des Benutzers wird dieser qualifizierte Pfad in der Benutzeroberfläche und in verschiedenen Assistenten von AEM Assets angezeigt, darunter die Assistenten für Verschiebung und Snippet-Erstellung zur Durchsetzung der Trennung.

Mit der Multi-Tenancy-Funktion können Sie die folgenden Assettypen und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten &quot;Seite hinzufügen/auswählen&quot;)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
