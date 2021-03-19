---
title: Übersetzen von Inhalten für mehrsprachige Sites
seo-title: Übersetzen von Inhalten für mehrsprachige Sites
description: Erfahren Sie mehr zur Übersetzung von Inhalten für mehrsprachige Sites.
seo-description: Erfahren Sie mehr zur Übersetzung von Inhalten für mehrsprachige Sites.
uuid: b8047f6f-e86a-495d-9b80-731ac7d83c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 67faa2ee-cb12-44b0-8bfb-534d1d6c360a
legacypath: /content/docs/en/aem/6-0/administer/integration/third-party-services/machine-translation
feature: Sprachkopie
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 87%

---


# Übersetzen von Inhalten für mehrsprachige Sites{#translating-content-for-multilingual-sites}

Automatisieren Sie die Übersetzung von Seiteninhalten, Assets und benutzergenerierten Inhalten, um mehrsprachige Websites zu erstellen und zu pflegen. Zur Automatisierung von Übersetzungs-Workflows integrieren Sie die Übersetzungsdienstleister in AEM und erstellen Sie Projekte zur Übersetzung von Inhalten in mehrere Sprachen. AEM unterstützt menschliche und maschinelle Übersetzungs-Workflows.

* Menschliche Übersetzung: Inhalte werden an Ihren Übersetzungsdienstleister gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.
* Maschinelle Übersetzung: Der maschinelle Übersetzungsdienst übersetzt sofort Ihre Inhalte.

Die Übersetzung der Inhalte umfasst die folgenden Schritte:

1. [Stellen Sie eine Verbindung zwischen AEM und Ihrem Übersetzungsdienstleister her](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider) und [erstellen Sie Konfigurationen für die Integration des Übersetzungs-Frameworks](/help/sites-administering/tc-tic.md).

1. [Verknüpfen Sie die Seiten Ihres Sprach-Masters](/help/sites-administering/tc-tic.md#configuring-pages-for-translation) mit dem Übersetzungsdienstleister und den Framework-Konfigurationen.
1. [Identifizieren Sie den Typ des zu übersetzenden ](/help/sites-administering/tc-rules.md) Inhalts.
1. [Bereiten Sie die Inhalte für die Übersetzung vor](/help/sites-administering/tc-prep.md), indem Sie die Sprach-Master und die Stammseiten der Sprachkopien erstellen.
1. [Erstellen Sie Übersetzungsprojekte, ](/help/sites-administering/tc-manage.md) um die zu übersetzenden Inhalte zu sammeln und den Übersetzungsprozess vorzubereiten.
1. Verwenden Sie die Übersetzungsprojekte, um [den Prozess zur Übersetzung der Inhalte zu verwalten](/help/sites-administering/tc-manage.md).

Wenn Ihr Übersetzungsdienstleister keinen Connector für die Integration in AEM bereitstellt, unterstützt AEM auch die manuelle Extrahierung und das erneute Einfügen von Übersetzungsinhalten im XML-Format.

>[!NOTE]
>
>Ihr Benutzer muss Mitglied der Gruppe „project-administrators“ sein, um die Sprachkopie-Funktionen zu verwenden.

## Best Practices {#best-practices}

Die Seite [Best Practices für Übersetzung](/help/sites-administering/tc-bp.md) enthält wichtige Informationen zu Ihrer Implementierung.
