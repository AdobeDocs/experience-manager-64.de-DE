---
title: Multi-Tenancy für Sammlungen, Snippets und Snippet-Vorlagen
description: Trennen Sie Inhalte im CRX-Repository basierend auf der Kundenorganisation, um unbefugten Zugriff zu verhindern.
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 34%

---

# Multi-Tenancy für Sammlungen, Snippets und Snippet-Vorlagen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Mit der Multi-Tenancy-Funktion können Sie Inhalte in CRX auf Basis von Präfix und ID der Organisation trennen, um die Inhalte vor unberechtigtem Zugriff durch Anwender von anderen Unternehmen zu schützen.

Adobe Experience Manager (AEM) Assets speichert Daten für jede Organisation in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Organisations-Präfix und die Organisations-ID identifiziert, die am herkömmlichen Speicherort enthalten sind, an dem verschiedene Asset-Typen in CRX gespeichert sind.

Wenn Sie beispielsweise einen Ordner mit dem Namen `Demo`, AEM Assets standardmäßig den Ordner unter `../content/dam/Demo` Speicherort in CRX. Wenn die Funktion für mehrere Mandanten aktiviert ist, können Sie die Daten unter `../content/dam/<organization prefix>/<organization id>Demo`.

Beispiel: für Adobe Marketing Cloud-Benutzer von AEM Assets (On-Demand), die `aodpremium` -Organisation, können Sie die Multi-Mandate-Funktion verwenden, um den folgenden Pfad zu konfigurieren: `../content/dam/mac/aodpremiumDemo`, trennen Sie den Inhalt. In diesem Beispiel `mac` ist das Organisations-Präfix und `aodpremium` ist die Organisations-ID.

Auf Basis von Organisation und ID des Benutzers wird dieser qualifizierte Pfad in der Benutzeroberfläche und in verschiedenen Assistenten von AEM Assets angezeigt, darunter die Assistenten für Verschiebung und Snippet-Erstellung zur Durchsetzung der Trennung.

Mit der Multi-Tenancy-Funktion können Sie die folgenden Assettypen und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten &quot;Seite hinzufügen/auswählen&quot;)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
