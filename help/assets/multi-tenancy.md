---
title: Multi-Mandantenfähigkeit für Sammlungen, Snippets sowie Snippet-Vorlagen
description: Trennen Sie Inhalte im CRX-Repository basierend auf der Kundenorganisation, um unbefugten Zugriff zu verhindern.
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 12%

---

# Multi-Mandantenfähigkeit für Sammlungen, Snippets sowie Snippet-Vorlagen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit der Multi-Tenancy-Funktion können Sie Inhalte in CRX basierend auf dem Organisations-Präfix und der Organisations-ID trennen, um den Inhalt vor unbefugtem Zugriff durch Benutzer anderer Organisationen zu schützen.

Adobe Experience Manager (AEM) Assets speichert Daten für jedes Unternehmen in einem anderen Pfad. Jeder organisationsspezifische Pfad wird durch das Organisations-Präfix und die Organisations-ID identifiziert, die am herkömmlichen Speicherort enthalten sind, an dem verschiedene Asset-Typen in CRX gespeichert sind.

Wenn Sie beispielsweise einen Ordner mit dem Namen `Demo`, AEM Assets standardmäßig den Ordner unter `../content/dam/Demo` Speicherort in CRX. Wenn die Funktion für mehrere Mandanten aktiviert ist, können Sie die Daten unter `../content/dam/<organization prefix>/<organization id>Demo`.

Beispiel: für Adobe Marketing Cloud-Benutzer von AEM Assets (On-Demand), die `aodpremium` -Organisation, können Sie die Multi-Mandate-Funktion verwenden, um den folgenden Pfad zu konfigurieren: `../content/dam/mac/aodpremiumDemo`, trennen Sie den Inhalt. In diesem Beispiel `mac` ist das Organisations-Präfix und `aodpremium` ist die Organisations-ID.

Basierend auf der Organisation und ID des Benutzers wird dieser qualifizierte Pfad in der AEM Assets-Benutzeroberfläche und in verschiedenen Assistenten angezeigt, darunter in den Assistenten zum Verschieben und Erstellen von Snippets , um die Segmentierung zu erzwingen.

Mit der Multi-Tenancy-Funktion können Sie die folgenden Assettypen und Komponenten trennen:

* Sammlungen
* Allgemeine Sammlungen
* Kataloge (einschließlich des Assistenten „Seite hinzufügen/auswählen“)
* Vorlagen
* Snippet-Vorlagen
* Lightbox
