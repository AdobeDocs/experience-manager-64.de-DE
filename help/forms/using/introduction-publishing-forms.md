---
title: Einführung in das Veröffentlichen von Formularen in einem Portal
seo-title: Introduction to publishing forms on a portal
description: AEM Forms bietet Komponenten, mit denen Sie Ihr Formularportal erstellen können. In diesem Artikel werden die verfügbaren Forms Portal-Komponenten vorgestellt.
seo-description: AEM Forms provides with components that you can use to build your forms portal. This articles introduces you to the available forms portal components.
uuid: 96aa4fe2-a111-4675-a33c-7dee8b82cbc2
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 44871fe1-ddc9-492c-8784-5df3ca392f9b
exl-id: a91e23e8-339d-4090-9872-2e066ab66590
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 62%

---

# Einführung in das Veröffentlichen von Formularen in einem Portal {#introduction-to-publishing-forms-on-a-portal}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht über die Komponenten des AEM Forms-Portals {#aem-forms-portal-components-overview}

In einem typischen formularzentrierten Portal-Bereitstellungsszenario sind die Formularentwicklung und die Portalentwicklung zwei getrennte Aktivitäten. Während Formularentwickler Formulare in einem Repository entwerfen und speichern, erstellen Webentwickler eine Webanwendung, um Formulare aufzulisten und die Übermittlung von Formularen zu verarbeiten. Forms wird in die Webstufe kopiert, da keine Kommunikation zwischen dem Formular-Repository und der Webanwendung besteht.

Solche Szenarien führen oft zu Managementproblemen und Produktionsverzögerungen. Wenn beispielsweise eine neuere Version eines Formulars im Repository verfügbar ist, müssen Sie das Formular auf der Webstufe ersetzen, die Webanwendung ändern und das Formular erneut auf der öffentlichen Website bereitstellen. Die erneute Bereitstellung der Webanwendung kann zu Serverausfällen führen. In der Regel handelt es sich bei dem Serverausfall um eine geplante Aktivität, weshalb die Änderungen nicht sofort an die öffentliche Site gesendet werden können.

AEM Forms bietet Portalkomponenten, die den Verwaltungsaufwand und Produktionsverzögerungen reduzieren. Die Komponenten ermöglichen es Webentwicklern, ein Formularportal auf mit Adobe Experience Manager (AEM) erstellten Websites zu erstellen und anzupassen.

![AEM Forms-Portal](assets/aem-forms-portal.png)

Mit den Formularportalkomponenten können Sie die folgenden Funktionen hinzufügen:

* Auflisten von Formularen in benutzerdefinierten Layouts. Standardmäßig werden die Layouts für Listenansicht, Kartenansicht und Bereichsansicht bereitgestellt. Sie können auch eigene benutzerdefinierte Layouts erstellen.
* Ermöglicht die Anzeige benutzerdefinierter Metadaten sowie benutzerdefinierter Aktionen bei deren Auflistung.
* Auflisten von Formularen, die von der AEM Forms-Benutzeroberfläche auf der Veröffentlichungsinstanz veröffentlicht wurden, in der Formularportal-Komponenten verwendet werden.
* Endbenutzern ermöglichen, Formulare in HTML- und im PDF-Format anzuzeigen.
* Verwenden benutzerdefinierter HTML-Profile, um Formulare anzuzeigen.
* Aktivieren der Suche nach Formularen anhand einer Reihe von Kriterien, wie zum Beispiel Formulareigenschaften, Metadaten und Tags.
* Senden von Formulardaten an ein Servlet.
* Verwenden von benutzerdefiniertem CSS, um das Erscheinungsbild des Portals anzupassen.
* Erstellen von Links zu Formularen.
* Listet Entwürfe und Übermittlungen im Zusammenhang mit dem vom Endbenutzer erstellten adaptiven Formular auf.

## Verfügbare AEM Forms Portal-Komponenten {#available-aem-forms-portal-components}

AEM Forms bietet standardmäßig die folgenden Portalkomponenten, die in die Komponentengruppen **Dokumentdienst** und **Dokumentdienst-Eigenschaften** unterteilt sind:

### Suche und Auflister {#search-amp-lister}

Mit der Komponente &quot;Search &amp; Lister&quot;können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten und Konfigurationsoptionen bereitstellen, um Formulare basierend auf angegebenen Kriterien aufzulisten. Außerdem können Sie mit der Komponente Suchkriterien angeben, damit die Portalbenutzer die gesamte Liste der Formulare durchsuchen können.

### Entwürfe und Einsendungen {#drafts-amp-submissions}

Während die Komponente „Suche und Auflister“ Formulare anzeigt, die vom Formularautor veröffentlicht wurden, zeigt die Komponente „Entwürfe und Sendungen“ Formulare, die für den späteren Abschluss als Entwurf gespeichert wurden, sowie gesendete Formulare an. Diese Komponente bietet jedem angemeldeten Benutzer ein personalisiertes Erlebnis.

### Verknüpfung {#link}

Mit der Komponente &quot;Link&quot;können Sie einen Link zu einem Formular an einer beliebigen Stelle auf der Seite erstellen. Angenommen, Sie bieten ein Schulungsprogramm an und möchten, dass Ihre Benutzer ein Formular zur Registrierung für das Training einreichen. Auf Ihrer Website haben Sie die Programmdetails veröffentlicht. Unter den Details möchten Sie einen Link zum Registrierungsformular angeben. Die Komponente Link kann Ihnen beim Erstellen dieses Links helfen.

## Formularportal-Workflow {#forms-portal-workflow}

Im Formularportal können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten. Außerdem können Sie mit der Komponente Suchkriterien angeben, damit die Portalbenutzer die gesamte Liste der Formulare durchsuchen können. Sie können die Komponente „Drafts &amp; Submissions“ auch verwenden, um als Entwurf zum späteren Ausfüllen gespeicherte Formulare sowie übermittelte Formulare anzuzeigen. Sie müssen bestimmte Vorgänge ausführen, bevor diese Funktionen auf einer Sites-Seite verfügbar werden. Führen Sie die Schritte in der angegebenen Reihenfolge aus, um die Komponenten und die entsprechenden Funktionen auf einer Sites-Seite verfügbar zu machen:

1. **Aktivieren von Formularportalkomponenten**: Standardmäßig sind Formularportalkomponenten nicht verfügbar. [Aktivieren der Komponenten aus AEM Sidekick](/help/forms/using/enabling-forms-portal-components.md) für eine AEM Sites-Seite.
1. **Auflisten von Formularen auf einer Seite (Erstellen der Formularportalseite):** Sie können Formulare auf Seiten von AEM Sites und anderen Seiten auflisten. Die Liste enthält Formulare, die in der Veröffentlichungsinstanz verfügbar sind. Benutzer können Formulare öffnen und ausfüllen. Wenn ein Benutzer ein Formular öffnet, wird eine neue Instanz des Formulars erstellt:

   1. **Auflisten von Formularen auf einer AEM Sites-Seite**: Fügen Sie der Seite die Komponente **[Search &amp; Lister](/help/forms/using/creating-form-portal-page.md)** hinzu und konfigurieren Sie den darin enthaltenen **[Listenbereich](/help/forms/using/creating-form-portal-page.md#p-list-pane-p)**, sodass Formulare auf einer Seite aufgelistet werden. Fügen Sie der Komponente **Search &amp; Lister** auch die Komponente **[Suchbereich](/help/forms/using/creating-form-portal-page.md#search-pane)** hinzu und konfigurieren Sie diese, um der Seite Suchfunktionen hinzuzufügen. Die Seite mit der Formularportalkomponente wird als [Formularportalseite](/help/forms/using/creating-form-portal-page.md) bezeichnet.
   1. **Auflisten von Formularen auf einer Nicht-AEM Sites-Seite:** Verwenden Sie die [APIs für die Formularportalsuche](/help/forms/using/listing-forms-webpage-using-apis.md), um Formulare auf Seiten von anderen Sites als AEM Sites abzufragen, abzurufen und aufzulisten.

1. **Auflisten von Formularentwürfen und übermittelten Formularen auf einer Formularportalseite**: Fügen Sie der Formularportalseite die Komponente „Drafts &amp; Submissions“ hinzu und konfigurieren Sie sie. Mit der Komponente „“ können Sie alle Formulare auflisten, die den Status „Entwurf“ aufweisen, und diejenigen, die bereits gesendet wurden.

   Damit ein übermitteltes adaptives Formular auf der Registerkarte für Übermittlungen angezeigt werden kann, legen Sie als **Übermittlungsaktion** die Option **[Übermittlungsaktion für Formularportal](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/configuring-submit-actions.html) fest.** Sie können stattdessen auch die Option „Forms Portal Submit“ aktivieren. Wenn ein Benutzer das Formular übermittelt, wird dieses der Registerkarte „Übermittlungen“ hinzugefügt.

1. **Konfigurieren Sie den Speicher für die Daten von Formularentwürfen und gesendeten Formularen:** Standardmäßig werden die Daten von Entwürfen und Übermittlungen im AEM Repository gespeichert. In einer Produktionsumgebung wird empfohlen, keine Entwurfs- oder gesendete Formulardaten nicht im AEM-Repository zu speichern. [Konfigurieren der Formularportalkomponente zum Speichern von Daten an einem sicheren Speicherort](/help/forms/using/draft-submission-component.md#customizing-the-storage).
1. **(Optional) Anpassen der Formularportalkomponenten:** [Passen Sie Ihre Vorlagen für Formularportalseiten an](/help/forms/using/customizing-templates-forms-portal-components.md), um den Komponenten ein charakteristisches Erscheinungsbild zu verleihen.
1. **(Optional) Hinzufügen benutzerdefinierter Metadaten zu Formularen:** [Fügen Sie Formularen benutzerdefinierte Metadaten hinzu](/help/forms/using/customizing-templates-forms-portal-components.md), um die Auflistung und Suche zu verbessern.
1. **Veröffentlichen der Formularportalseite:** Ihre Formularportalseite ist jetzt bereit. Veröffentlichen Sie die Seite.

## Verwandte Artikel {#related-articles}

* [Aktivieren von Formularportalkomponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Erstellen einer Formularportalseite](/help/forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Verwenden der Komponente „Entwurf und Übermittlung“](/help/forms/using/draft-submission-component.md)
* [Anpassen der Speicherung von Entwürfen und gesendeten Formularen](/help/forms/using/draft-submission-component.md#customizing-the-storage)
* [Beispiel zur Integrierung der Komponente „Entwürfe und Sendungen“ in die Datenbank](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/integrate-draft-submission-database.html)

* [Anpassen von Vorlagen für Forms Portal-Komponenten](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md)
