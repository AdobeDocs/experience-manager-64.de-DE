---
title: Fehlerbehebung in AEM beim Authoring
seo-title: Troubleshooting AEM when Authoring
description: Einige Probleme bei der Verwendung von AEM
seo-description: Some issues that you might encounter when using AEM
uuid: 99af51ea-8628-4811-83f2-ab3f88f0279e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: da0a5644-2e1d-4394-a6aa-11bb41406ba6
exl-id: b0890070-c9e8-4ce4-9149-00c8c38298ce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 56%

---

# Fehlerbehebung in AEM beim Authoring{#troubleshooting-aem-when-authoring}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.

>[!NOTE]
>
>Bei Problemen sollten Sie auch die Liste der [Bekannte Probleme](/help/release-notes/known-issues.md) für Ihre Instanz (Release- und Service Packs).

>[!NOTE]
>
>Benutzer mit Administratorrechten, die Probleme in AEM beheben möchten, können die unter [Fehlerbehebung in AEM (für Administratoren)](/help/sites-administering/troubleshoot.md) beschriebenen Lösungen nutzen. Wenn Sie nicht über ausreichende Rechte verfügen, wenden Sie sich bezüglich der Problembehebung in AEM an Ihren Admin.

## Alte Seitenversion wird weiterhin auf der veröffentlichten Website angezeigt {#old-page-version-still-on-published-site}

* **Problem**:

   * Sie haben Änderungen an einer Seite vorgenommen und die Seite auf die Veröffentlichungs-Site repliziert, aber die *old* -Version der Seite wird weiterhin auf der Veröffentlichungs-Site angezeigt.

* **Grund**:

   * Dies kann verschiedene Ursachen haben, meist den Cache (entweder Ihren lokalen Browser oder den Dispatcher), obwohl es manchmal ein Problem mit der Replikationswarteschlange sein kann.

* **Lösungen**:

   * Hier gibt es verschiedene Möglichkeiten:
   * Überprüfen Sie, ob die Seite korrekt repliziert wurde. Überprüfen Sie den Seitenstatus und ggf. den Status der Replikationswarteschlange.
   * Löschen Sie den Cache des lokalen Browsers und rufen Sie die Seite erneut auf.
   * Fügen Sie dem Ende der Seiten-URL `?` hinzu:

      * `http://localhost:4502/sites.html/content?`
      * Dadurch wird die Seite direkt von AEM abgerufen und der Dispatcher wird umgangen. Wenn die aktualisierte Seite angezeigt wird, ist dies ein Hinweis darauf, dass Sie den Dispatcher-Cache löschen müssen.
   * Wenden Sie sich an den Systemadministrator, wenn Probleme mit den Replikationswarteschlangen vorliegen.


## Komponentenaktionen nicht in der Symbolleiste sichtbar {#component-actions-not-visible-on-toolbar}

* **Problem**:

   * Sämtliche entsprechenden Komponentenaktionen sind nicht sichtbar, wenn eine Seite in der Autorenumgebung bearbeitet wird.

* **Grund**:

   * In seltenen Fällen kann sich eine frühere Aktion auf die Symbolleiste auswirken.

* **Lösung**:

   * Aktualisieren Sie die Seite.
