---
title: Übersetzen von Inhalten für mehrsprachige Sites
seo-title: Translating Content for Multilingual Sites
description: Erfahren Sie mehr zur Übersetzung von Inhalten für mehrsprachige Sites.
seo-description: Learn how to translate content for multilingual sites.
uuid: b8047f6f-e86a-495d-9b80-731ac7d83c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 67faa2ee-cb12-44b0-8bfb-534d1d6c360a
legacypath: /content/docs/en/aem/6-0/administer/integration/third-party-services/machine-translation
feature: Language Copy
exl-id: 3a3f5c4d-6c3f-4201-acc8-dbd138bb59ba
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 100%

---

# Übersetzen von Inhalten für mehrsprachige Sites{#translating-content-for-multilingual-sites}

Automatisieren Sie die Übersetzung von Seiteninhalten, Assets und benutzergenerierten Inhalten, um mehrsprachige Websites zu erstellen und zu pflegen. Zur Automatisierung von Übersetzungs-Workflows integrieren Sie die Übersetzungsdienstleister in AEM und erstellen Sie Projekte zur Übersetzung von Inhalten in mehrere Sprachen. AEM unterstützt Workflows für menschliche und maschinelle Übersetzungen.

* Menschliche Übersetzung: Inhalte werden an Ihren Übersetzungsdienstleister gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.
* Maschinelle Übersetzung: Der maschinelle Übersetzungs-Service übersetzt sofort Ihre Inhalte.

Die Übersetzung der Inhalte umfasst die folgenden Schritte:

1. [Stellen Sie eine Verbindung zwischen AEM und Ihrem Übersetzungsdienstleister her](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider) und [erstellen Sie Konfigurationen für die Integration des Übersetzungs-Frameworks](/help/sites-administering/tc-tic.md).

1. [Verknüpfen Sie die Seiten Ihres Sprachstamms](/help/sites-administering/tc-tic.md#configuring-pages-for-translation) mit dem Übersetzungsdienstleister und den Framework-Konfigurationen.
1. [Identifizieren Sie die Art der zu übersetzenden Inhalte](/help/sites-administering/tc-rules.md).
1. [Bereiten Sie die Inhalte für die Übersetzung vor](/help/sites-administering/tc-prep.md), indem Sie den Sprachstamm und die Stammseiten der Sprachkopien erstellen.
1. [Erstellen Sie Übersetzungsprojekte](/help/sites-administering/tc-manage.md), um die zu übersetzenden Inhalte zusammenzustellen und den Übersetzungsprozess vorzubereiten.
1. Verwenden Sie die Übersetzungsprojekte, um [den Prozess zur Übersetzung der Inhalte zu verwalten](/help/sites-administering/tc-manage.md).

Wenn Ihr Übersetzungsdienstleister keinen Connector für die Integration in AEM bereitstellt, unterstützt AEM auch die manuelle Extrahierung und das erneute Einfügen von Übersetzungsinhalten im XML-Format.

>[!NOTE]
>
>Ihr Benutzer muss Mitglied der Gruppe „project-administrators“ sein, um die Sprachkopie-Funktionen zu verwenden.

## Best Practices {#best-practices}

Die Seite [Best Practices für die Übersetzung](/help/sites-administering/tc-bp.md) enthält wichtige Informationen zur Implementierung.
