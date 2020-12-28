---
title: Festlegen der Benutzeroberfläche
seo-title: Auswahl der Benutzeroberfläche
description: Zur Vereinfachung von Bearbeitungsvorgängen können Benutzer bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln.
seo-description: Zur Vereinfachung von Bearbeitungsvorgängen können Benutzer bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 59%

---


# Auswahl der Benutzeroberfläche{#selecting-your-ui}

Da die touchfähige Benutzeroberfläche die klassische Benutzeroberfläche ersetzt, muss der Benutzer oder Administrator der AEM Instanz eine aktive Entscheidung treffen, um die klassische Benutzeroberfläche weiter zu verwenden. Da die klassische Benutzeroberfläche nicht mehr gepflegt wird, kann der Authoring-Benutzer nicht einfach von der klassischen Benutzeroberfläche zur entsprechenden Benutzeroberfläche in der touchfähigen Benutzeroberfläche wechseln.

Zur Vereinfachung von Bearbeitungsvorgängen können Benutzer bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln. Weitere Informationen dazu finden Sie unter [Auswahl der Benutzeroberfläche](/help/sites-authoring/select-ui.md) in der Standarddokumentation zur Bearbeitung.

>[!NOTE]
>
>Instanzen, bei denen ein Upgrade aus einer früheren Version durchgeführt wurde, behalten die klassische Benutzeroberfläche bei der Seitenbearbeitung bei.
>
>Nach der Aktualisierung wird das Seiten-Authoring nicht automatisch auf die touchfähige Benutzeroberfläche umgestellt. Sie können dies jedoch mithilfe der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des **WCM Authoring UI Mode Service** ( `AuthoringUIMode`-Dienst) konfigurieren. Weitere Informationen dazu finden Sie unter [Benutzeroberflächenüberschreibung für den Editor](#uioverridesfortheeditor).

## Configuring the Default UI for Your Instance {#configuring-the-default-ui-for-your-instance}

Ein Systemadministrator kann die bei Start und Anmeldung angezeigte Benutzeroberfläche mit der [Root-Zuordnung](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) konfigurieren.

Diese Einstellungen kann durch Benutzerstandards oder Sitzungseinstellungen überschrieben werden.
