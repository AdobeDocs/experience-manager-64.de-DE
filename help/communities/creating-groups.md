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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 49%

---

# Community-Gruppen {#community-groups}

Mit der Funktion &quot;Community-Gruppen&quot;kann eine Unter-Community von autorisierten Benutzern (Community-Mitgliedern und Autoren) aus der Veröffentlichungs- und Autorenumgebung dynamisch auf einer Community-Site erstellt werden.

Diese Fähigkeit ist vorhanden, wenn die [Gruppenfunktion](functions.md#groups-function) ist im [Community-Site](sites-console.md) Struktur.

A [Community-Gruppenvorlage](tools-groups.md) stellt das Design der Community-Gruppenseite bereit, wenn eine Community-Gruppe dynamisch erstellt wird.

Beim Hinzufügen der Gruppenfunktion zur Struktur oder Vorlage einer Community-Site werden eine oder mehrere Gruppenvorlagen ausgewählt. Die folgende Liste mit Gruppenvorlagen steht dem Mitglied oder Autor zur Verfügung, wenn auf der Community-Site dynamisch eine neue Gruppe erstellt wird.

## Neue Gruppe erstellen {#creating-a-new-group}

Die Möglichkeit, eine neue Community-Gruppe zu erstellen, hängt von der Existenz einer Community-Site ab, die die Gruppenfunktion enthält, z. B. eine von der ` [Reference Site Template](sites.md)`.

Die folgenden Beispiele verwenden die Community-Site, die aus der `Reference Site Template` wie in [Erste Schritte mit AEM Communities](getting-started.md) Tutorial.

Dies ist die Seite, die beim Veröffentlichen geladen wird, wenn die **[!UICONTROL Gruppen]** Menüelement ausgewählt ist:

![chlimage_1-236](assets/chlimage_1-236.png)

Wählen Sie das Symbol für **[!UICONTROL Neue Gruppe]** aus, öffnet sich das Bearbeitungsdialogfeld.

Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die grundlegenden Eigenschaften der Gruppe an:

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Gruppenname]** Der Titel der Gruppe, der auf der Community-Site angezeigt wird.

* **[!UICONTROL Beschreibung]** Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt wird.

* **[!UICONTROL Einladen]** Eine Auflistung der Mitglieder, die zum Beitritt zur Gruppe eingeladen werden können. Mithilfe der Vervollständigungsfunktion erhalten Sie Vorschläge für einzuladende Mitglieder.

* **[!UICONTROL Gruppen-URL-Name]** Der Name der Gruppenseite, der Teil ihrer URL ist.

* **[!UICONTROL Gruppe öffnen]**
Auswählen 
`Open Group` gibt an, dass ein anonymer Site-Besucher den Inhalt anzeigen kann, und hebt die Auswahl auf `Member Only Group`.

* **[!UICONTROL Nur Mitgliedergruppe]**
Auswählen 
`Member Only Group` zeigt an, dass nur Mitglieder der Gruppe den Inhalt anzeigen können, und deaktiviert die Auswahl `Open Group`.

Unter dem **[!UICONTROL Vorlage]** tab bietet die Möglichkeit, aus der Liste von Community-Gruppenvorlagen auszuwählen, die angegeben wurden, als die Gruppenfunktion in der Struktur der Community-Site oder in einer Community-Site-Vorlage enthalten war.

![chlimage_1-238](assets/chlimage_1-238.png)

Auf der Registerkarte **[!UICONTROL Bild]** können Sie ein Bild hochladen, das auf der Seite „Gruppen“ der Community-Site angezeigt werden soll. Durch das Standard-Stylesheet wird das Bild auf eine Größe von 170 x 90 Pixeln zugeschnitten.

![chlimage_1-239](assets/chlimage_1-239.png)

Wählen Sie die Schaltfläche **[!UICONTROL Gruppe erstellen]** aus, werden die Gruppenseiten basierend auf der ausgewählten Vorlage erstellt. Es wird eine Gruppe für Mitglieder erstellt und die Seite „Gruppen“ wird so aktualisiert, dass die neue Unter-Community aufgeführt wird.

Die Seite „Gruppen“ mit einer neuen Unter-Community mit dem Namen „Focus Group“ (Gesprächsgruppe), für die ein Thumbnail hochgeladen wird, sieht beispielsweise wie folgt aus (der aktuelle Benutzer ist als Community-Gruppenadministrator angemeldet):

![chlimage_1-240](assets/chlimage_1-240.png)

Auswählen der `Focus Group` -Link öffnet die Seite &quot;Fokusgruppe&quot;im Browser, die basierend auf der ausgewählten Vorlage ein erstes Erscheinungsbild aufweist und ein Untermenü unter dem Menü der Haupt-Community-Site enthält:

![chlimage_1-241](assets/chlimage_1-241.png)

## Komponente „Community-Gruppenmitgliederliste“ {#community-group-member-list-component}

Die `Community Group Member List` -Komponente ist für Entwickler von Gruppenvorlagen vorgesehen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Community-Gruppengrundlagen](essentials-groups.md) für Entwickler.

Weitere Informationen zu Community-Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).
