---
title: Community-Gruppen
seo-title: Community Groups
description: Erstellen von Community-Gruppen
seo-description: Creating community groups
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
exl-id: 4b663228-9cb6-45c0-99dd-8dd7fc2aa4a6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 3%

---

# Community-Gruppen {#community-groups}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit der Funktion &quot;Community-Gruppen&quot;kann eine Unter-Community von autorisierten Benutzern (Community-Mitgliedern und Autoren) aus der Veröffentlichungs- und Autorenumgebung dynamisch auf einer Community-Site erstellt werden.

Diese Fähigkeit ist vorhanden, wenn die [Gruppenfunktion](functions.md#groups-function) ist im [Community-Site](sites-console.md) Struktur.

A [Community-Gruppenvorlage](tools-groups.md) stellt das Design der Community-Gruppenseite bereit, wenn eine Community-Gruppe dynamisch erstellt wird.

Eine oder mehrere Gruppenvorlagen werden für die Gruppenfunktion ausgewählt, wenn die Funktion zur Struktur einer Community-Site oder zu einer Community-Site-Vorlage hinzugefügt wird. Diese Liste von Gruppenvorlagen wird dem Mitglied oder Autor angezeigt, der dynamisch eine neue Gruppe aus der Community-Site erstellt.

## Erstellen einer neuen Gruppe {#creating-a-new-group}

Die Möglichkeit, eine neue Community-Gruppe zu erstellen, hängt von der Existenz einer Community-Site ab, die die Gruppenfunktion enthält, z. B. eine von der ` [Reference Site Template](sites.md)`.

Die folgenden Beispiele verwenden die Community-Site, die aus der `Reference Site Template` wie in [Erste Schritte mit AEM Communities](getting-started.md) Tutorial.

Dies ist die Seite, die beim Veröffentlichen geladen wird, wenn die **[!UICONTROL Gruppen]** Menüelement ausgewählt ist:

![chlimage_1-236](assets/chlimage_1-236.png)

Wenn Sie die **[!UICONTROL Neue Gruppe]** angezeigt, öffnet sich ein Dialogfeld &quot;Bearbeiten&quot;.

Unter dem **[!UICONTROL Einstellungen]** -Registerkarte die grundlegenden Funktionen der Gruppe bereitstellen:

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Gruppenname]**
Der Titel der Gruppe, die auf der Community-Site angezeigt werden soll.

* **[!UICONTROL Beschreibung]**
Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt werden soll.

* **[!UICONTROL Einladen]**
Eine Liste der Mitglieder, die zur Teilnahme an der Gruppe eingeladen werden sollen. Die Suche nach einem Typ bietet Vorschläge für Community-Mitglieder, die eingeladen werden sollen.

* **[!UICONTROL Gruppen-URL-Name]**
Der Name der Gruppenseite, die Teil der URL wird.

* **[!UICONTROL Gruppe öffnen]**
Auswählen 
`Open Group` gibt an, dass ein anonymer Site-Besucher den Inhalt anzeigen kann, und hebt die Auswahl auf `Member Only Group`.

* **[!UICONTROL Nur Mitgliedergruppe]**
Auswählen 
`Member Only Group` zeigt an, dass nur Mitglieder der Gruppe den Inhalt anzeigen können, und deaktiviert die Auswahl `Open Group`.

Unter dem **[!UICONTROL Vorlage]** tab bietet die Möglichkeit, aus der Liste von Community-Gruppenvorlagen auszuwählen, die angegeben wurden, als die Gruppenfunktion in der Struktur der Community-Site oder in einer Community-Site-Vorlage enthalten war.

![chlimage_1-238](assets/chlimage_1-238.png)

Unter dem **[!UICONTROL Bild]** -Tab bietet die Möglichkeit, ein Bild hochzuladen, das für die Gruppe auf der Seite Gruppen der Community-Site angezeigt wird. Das Standard-Stylesheet hat eine Bildgröße von 170 x 90 Pixel.

![chlimage_1-239](assets/chlimage_1-239.png)

Durch Auswahl der **[!UICONTROL Gruppe erstellen]** -Schaltfläche verwenden, werden die Seiten für die Gruppe auf der Grundlage der ausgewählten Vorlage erstellt und eine Benutzergruppe für die Mitgliedschaft erstellt. Die Seite Gruppen wird aktualisiert, um die neue Unter-Community anzuzeigen.

Beispielsweise wird die Seite &quot;Gruppen&quot;mit einer neuen Unter-Community mit dem Titel &quot;Fokusgruppe&quot;, für die eine Miniaturansicht hochgeladen wurde, wie folgt angezeigt (noch als Community-Gruppenadministrator angemeldet):

![chlimage_1-240](assets/chlimage_1-240.png)

Auswählen der `Focus Group` -Link öffnet die Seite &quot;Fokusgruppe&quot;im Browser, die basierend auf der ausgewählten Vorlage ein erstes Erscheinungsbild aufweist und ein Untermenü unter dem Menü der Haupt-Community-Site enthält:

![chlimage_1-241](assets/chlimage_1-241.png)

## Komponente &quot;Community Group Member List&quot; {#community-group-member-list-component}

Die `Community Group Member List` -Komponente ist für Entwickler von Gruppenvorlagen vorgesehen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Community-Gruppengrundlagen](essentials-groups.md) für Entwickler.

Weitere Informationen zu Community-Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).
