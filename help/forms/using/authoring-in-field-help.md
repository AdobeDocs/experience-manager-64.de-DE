---
title: Verfassen von kontextsensitiver Hilfe für Formularfelder
seo-title: Authoring in-context help for form fields
description: 'Mit AEM Forms können Sie kontextbezogene Hilfe zu Feldern und Bereichen in adaptiven Formularen als Text oder Rich-Media, einschließlich Videos, hinzufügen. '
seo-description: AEM Forms allows you to add in-context help to adaptive form fields and panels, as text or rich media, including videos.
uuid: 07427ddd-9d35-41f6-a807-0e418aade199
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 893a72c7-d68f-464f-9765-ec2272189e58
feature: Adaptive Forms
exl-id: 0c761c0c-fbe4-4129-8a90-c4ef1127a762
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 100%

---

# Verfassen von kontextsensitiver Hilfe für Formularfelder {#authoring-in-context-help-for-form-fields}

## Einführung {#introduction}

Es gibt Situationen, in denen sich Endbenutzer, die ein Formular ausfüllen, nicht sicher sind, wie Informationen in ein bestimmtes Formularfeld einzugeben sind. Um diese Probleme zu beheben, bieten adaptive Formulare die Möglichkeit, Text oder interaktive kontextbezogene Hilfe zu einem Formularfeld hinzuzufügen. Dadurch werden das Ausfüllen des Formulars erleichtert und potenzielle Uneindeutigkeiten für Endbenutzer vermieden.

Dieser Artikel erläutert, wie Formularautoren Hilfe beim Authoring adaptiver Formulare hinzufügen können.

## Hinzufügen kontextbezogener Hilfe {#add-in-context-help}

Sie können kontextbezogene Hilfe mit den folgenden Optionen im Abschnitt „Hilfe-Inhalt“ der Registerkarte „Eigenschaften“ in der Seitenleiste angeben.

* [Kurzbeschreibung](/help/forms/using/authoring-in-field-help.md#p-short-description-p)
* [Lange Beschreibung](/help/forms/using/authoring-in-field-help.md#p-long-description-p)

![Kontextbezogene Hilfe für Formularfelder](assets/descriptions.png)

>[!NOTE]
>
>Die lange Beschreibung überschreibt die Kurzbeschreibung. Wenn Sie beide Optionen angegeben haben, wird nur die lange Beschreibung angezeigt.

### Kurzbeschreibung {#short-description}

Das Feld „Kurzbeschreibung“ dient zum Angeben schneller und kurzer Hinweise zum Ausfüllen eines Formularfelds. Der eingegebene Text im Feld „Kurzbeschreibung“ wird als QuickInfo beim Bewegen der Maus über das Feld angezeigt.

![Kurzbeschreibung zum Hinzufügen von kontextbezogener Hilfe für Formularfelder](assets/tooltip.png)

>[!NOTE]
>
>Wählen Sie **Kurzbeschreibung immer anzeigen** aus, um den Hilfetext unterhalb des Felds immer anzuzeigen.

![Dauerhafte kontextbezogene kurze Hilfe unter dem Feld](assets/short1.png)

### Lange Beschreibung {#long-description}

Sie können das Feld „Lange Beschreibung“ verwenden, um langen Text anzugeben oder Rich-Media-Inhalte (einschließlich Videos) als kontextbezogene Hilfe einzubetten. Beispiel: Das folgende Bild zeigt, wie Sie ein Video als kontextbezogene Hilfe einbetten können.

![Hinzufügen von Rich-Media als kontextbezogene Hilfe für Formularfelder](assets/long-descriptions.png)

Wenn Sie eine lange Beschreibung hinzufügen, wird das Symbol **„?“** neben dem Feld angezeigt. Durch Klicken auf das Symbol wird der Inhalt angezeigt, der im Abschnitt „Lange Beschreibung“ hinzugefügt wurde.

![Beispiel für kontextbezogene Rich-Media-Hilfe](assets/photoshop.png)

### Hilfe auf Bereichsebene {#panel-level-help}

Zusätzlich zur kontextbezogenen Hilfe für Formularfelder können Sie auf der Registerkarte „Hilfeinhalt“ des Dialogfelds zum Bearbeiten von Bereichen auch Hilfe auf Bereichsebene angeben.

![Hinzufügen von kontextbezogener Hilfe für einen Formularbereich](assets/panel-level-help.png)

Wenn Sie Hilfe für einen Bereich hinzufügen, wird das Symbol **„?“** neben der Bereichsbeschreibung angezeigt. Durch Klicken auf das Symbol wird der Inhalt angezeigt, der im Abschnitt „Hilfe-Inhalt“ des Dialogfelds zum Bearbeiten des Bereichs hinzugefügt wurde.

![Beispiel für kontextbezogene Hilfe auf Formularbereichsebene](assets/photoshop-1.png)
