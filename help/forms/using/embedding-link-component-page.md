---
title: Einbetten einer Link-Komponente in eine Seite
seo-title: Embedding link component in a page
description: Sie können die Verknüpfungskomponente verwenden, um ein adaptives Dokument oder ein adaptives Formular von einer beliebigen Seite aus zu verknüpfen.
seo-description: You can use the link component to link an adaptive document or an adaptive form from any page.
uuid: fde56b5f-634c-406f-a026-875f972f7c8f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: a4a36e73-3f7a-4173-8807-931f26daa35a
exl-id: eb816a35-0773-4eda-95b2-1d351c71be8b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 36%

---

# Einbetten einer Link-Komponente in eine Seite{#embedding-link-component-in-a-page}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Voraussetzungen {#prerequisites}

Die Verknüpfungskomponente ist ein Mitglied der Document Services-Kategorie. Stellen Sie sicher, dass die Document Services-Kategorie im AEM-Komponentenbrowser verfügbar ist. Wenn die Kategorie nicht aufgeführt ist, führen Sie die Schritte unter [Aktivieren der Komponenten im Forms Portal](/help/forms/using/enabling-forms-portal-components.md).

## Link-Komponente {#link-component}

Mit der Komponente &quot;Link&quot;können Formularportalautoren von überall auf einer Seite einen Link zu einem adaptiven Formular erstellen. Die Komponente Link ist im Abschnitt Document Services im Komponenten-Browser verfügbar.

Führen Sie die folgenden Schritte aus, um der Seite eine Komponente Link hinzuzufügen:

1. Ziehen Sie die Komponente **Link** auf die Seite. Wählen Sie die Komponente aus und tippen Sie auf ![cmppr](assets/cmppr.png). Das Komponentendialogfeld „Link bearbeiten“ wird geöffnet.

   ![edit-link-component](assets/edit-link-component.png)

1. Geben Sie auf der Registerkarte **Anzeige** Folgendes an:

   * **Linkbeschriftung**: Linktext oder Beschriftung für den Link.
   * **Link-Tooltip**: QuickInfo für den Link.
   * **Layout-Vorlage**: Vorlage für das Layout der Komponente &quot;Link&quot;.

1. Öffnen Sie die **Asset-Informationen** und geben Sie den Typ des Assets an. Ein Asset kann ein **Formular** sein. Je nach ausgewähltem Assettyp können die unten aufgeführten Optionen angezeigt werden:

   * **Asset Path**: Pfad für das Repository, in dem das Asset gespeichert ist.
   * **Render Type**: Das Wiedergabeformat – PDF, HTML oder Auto Der Wiedergabetyp &quot;Auto&quot;erkennt die Benutzerumgebung und rendert das Formular entsprechend als HTML oder als PDF. Wenn das Formular beispielsweise von einem Mobilgerät aus aufgerufen wird, gibt der Wiedergabetyp &quot;Auto&quot;das Formular auf HTML wieder.
   * **Sende-URL**: URL zu dem Servlet, an das die Formulardaten gesendet werden.
   * **HTML-Profil**: Profil für die Wiedergabe des Formulars als HTML.
   * **PDF-Profil**: Profil für die Wiedergabe des Formulars als PDF-Dokument.

1. Öffnen Sie die Registerkarte **Erweitert**. Sie können zusätzliche Parameter in Form von Schlüssel-Wert-Paaren angeben. Wenn auf den Link geklickt wird, werden diese zusätzlichen Parameter zusammen mit dem Formular übergeben.

   Tippen Sie auf **Fertig**, um die Konfiguration zu speichern.

## Best Practices für die Verwendung der Komponente „Link“  {#best-practices-for-using-link-component-br}

* Stellen Sie sicher, dass Sie PDF als Rendertyp auswählen, wenn der im Formularpfad angegebene Pfad auf ein Dokument verweist, dessen Renderformat PDF ist.
* Die Sende-URL für ein Formular kann an mehreren Stellen angegeben werden und die Rangfolge lautet wie folgt:

   1. Die Sende-URL, die in das Formular eingebettet ist (in der Senden-Schaltfläche), hat die höchste Priorität.
   1. Die Sende-URL, die in Forms Manager erwähnt wird, hat die mittlere Priorität.
   1. Die Sende-URL, die im Forms Portal erwähnt wird, hat die niedrigste Priorität.
