---
title: Community-Gruppen
seo-title: Community-Gruppen
description: Erstellen von Community-Gruppen
seo-description: Erstellen von Community-Gruppen
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87

---


# Community-Gruppen {#community-groups}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht es einer Unter-Community, dynamisch innerhalb einer Community-Site von autorisierten Benutzern (Community-Mitgliedern und Autoren) aus der Veröffentlichungs- und Autorenumgebung erstellt zu werden.

This ability is present when the [groups function](functions.md#groups-function) is present in the [community site](sites-console.md) structure.

A [community group template](tools-groups.md) provides the design of the community group page when a community group is dynamically created.

Beim Hinzufügen der Gruppenfunktion zur Struktur oder Vorlage einer Community-Site werden eine oder mehrere Gruppenvorlagen ausgewählt. Die folgende Liste mit Gruppenvorlagen steht dem Mitglied oder Autor zur Verfügung, wenn auf der Community-Site dynamisch eine neue Gruppe erstellt wird.

## Neue Gruppe erstellen {#creating-a-new-group}

The ability to create a new community group relies on the existance of a community site which includes the groups function, such as one created from the ` [Reference Site Template](sites.md)`.

The examples that follow use the community site created from the `Reference Site Template` as described in the [Getting Started with AEM Communities](getting-started.md) tutorial.

This is the page that loads on publish when the **[!UICONTROL Groups]** menu item is selected:

![chlimage_1-236](assets/chlimage_1-236.png)

Wählen Sie das Symbol für **[!UICONTROL Neue Gruppe]** aus, öffnet sich das Bearbeitungsdialogfeld.

Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die grundlegenden Eigenschaften der Gruppe an:

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Gruppenname]** Der Titel der Gruppe, der auf der Community-Site angezeigt wird.

* **[!UICONTROL Beschreibung]** Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt wird.

* **[!UICONTROL Einladen]** Eine Auflistung der Mitglieder, die zum Beitritt zur Gruppe eingeladen werden können. Mithilfe der Vervollständigungsfunktion erhalten Sie Vorschläge für einzuladende Mitglieder.

* **[!UICONTROL Gruppen-URL-Name]** Der Name der Gruppenseite, der Teil ihrer URL ist.

* **[!UICONTROL Gruppe]**&#x200B;öffnen Die Auswahl `Open Group` zeigt an, dass ein anonymer Site-Besucher den Inhalt anzeigen und die Auswahl aufheben kann `Member Only Group`.

* **[!UICONTROL &quot;Nur Gruppe]** auswählen&quot; `Member Only Group` bedeutet, dass nur Mitglieder der Gruppe den Inhalt anzeigen können und die Auswahl aufheben `Open Group`.

Under the **[!UICONTROL Template]** tab is the ability to select from the list of community group templates that were specified when the groups function was included in the community site&#39;s structure or in a community site template.

![chlimage_1-238](assets/chlimage_1-238.png)

Auf der Registerkarte **[!UICONTROL Bild]** können Sie ein Bild hochladen, das auf der Seite „Gruppen“ der Community-Site angezeigt werden soll. Durch das Standard-Stylesheet wird das Bild auf eine Größe von 170 x 90 Pixeln zugeschnitten.

![chlimage_1-239](assets/chlimage_1-239.png)

Wählen Sie die Schaltfläche **[!UICONTROL Gruppe erstellen]** aus, werden die Gruppenseiten basierend auf der ausgewählten Vorlage erstellt. Es wird eine Gruppe für Mitglieder erstellt und die Seite „Gruppen“ wird so aktualisiert, dass die neue Unter-Community aufgeführt wird.

Die Seite „Gruppen“ mit einer neuen Unter-Community mit dem Namen „Focus Group“ (Gesprächsgruppe), für die ein Thumbnail hochgeladen wird, sieht beispielsweise wie folgt aus (der aktuelle Benutzer ist als Community-Gruppenadministrator angemeldet):

![chlimage_1-240](assets/chlimage_1-240.png)

Selecting the `Focus Group` link will open the Focus Group page in the browser, which has an initial appearance based on the chosen template, and includes a sub-menu underneath the main community site&#39;s menu:

![chlimage_1-241](assets/chlimage_1-241.png)

## Komponente „Community-Gruppenmitgliederliste“{#community-group-member-list-component}

Die `Community Group Member List` Komponente ist für die Verwendung durch Entwickler von Gruppenvorlagen vorgesehen.

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Community Group Essentials](essentials-groups.md) page for developers.

For other information related to community groups, visit [Managing Users and User Groups](users.md).
