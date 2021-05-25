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
exl-id: 4b663228-9cb6-45c0-99dd-8dd7fc2aa4a6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 48%

---

# Community-Gruppen {#community-groups}

Mit der Funktion &quot;Community-Gruppen&quot;kann eine Unter-Community von autorisierten Benutzern (Community-Mitgliedern und Autoren) aus der Veröffentlichungs- und Autorenumgebung dynamisch auf einer Community-Site erstellt werden.

Diese Möglichkeit besteht, wenn die [Gruppenfunktion](functions.md#groups-function) in der [Community-Site](sites-console.md)-Struktur vorhanden ist.

Eine [Community-Gruppenvorlage](tools-groups.md) stellt das Design der Community-Gruppenseite bereit, wenn eine Community-Gruppe dynamisch erstellt wird.

Beim Hinzufügen der Gruppenfunktion zur Struktur oder Vorlage einer Community-Site werden eine oder mehrere Gruppenvorlagen ausgewählt. Die folgende Liste mit Gruppenvorlagen steht dem Mitglied oder Autor zur Verfügung, wenn auf der Community-Site dynamisch eine neue Gruppe erstellt wird.

## Neue Gruppe erstellen {#creating-a-new-group}

Die Möglichkeit, eine neue Community-Gruppe zu erstellen, hängt von der Existenz einer Community-Site ab, die die Gruppenfunktion enthält, z. B. eine, die über die Funktion ` [Reference Site Template](sites.md)` erstellt wurde.

Die folgenden Beispiele verwenden die Community-Site, die aus `Reference Site Template` erstellt wurde, wie im Tutorial [Erste Schritte mit AEM Communities](getting-started.md) beschrieben.

Dies ist die Seite, die bei der Veröffentlichung geladen wird, wenn das Menüelement **[!UICONTROL Gruppen]** ausgewählt wird:

![chlimage_1-236](assets/chlimage_1-236.png)

Wählen Sie das Symbol für **[!UICONTROL Neue Gruppe]** aus, öffnet sich das Bearbeitungsdialogfeld.

Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die grundlegenden Eigenschaften der Gruppe an:

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Gruppenname]** Der Titel der Gruppe, der auf der Community-Site angezeigt wird.

* **[!UICONTROL Beschreibung]** Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt wird.

* **[!UICONTROL Einladen]** Eine Auflistung der Mitglieder, die zum Beitritt zur Gruppe eingeladen werden können. Mithilfe der Vervollständigungsfunktion erhalten Sie Vorschläge für einzuladende Mitglieder.

* **[!UICONTROL Gruppen-URL-Name]** Der Name der Gruppenseite, der Teil ihrer URL ist.

* **[!UICONTROL Open]**
GroupSelecting 
`Open Group` gibt an, dass ein anonymer Site-Besucher den Inhalt anzeigen kann, und hebt die Auswahl  `Member Only Group`auf.

* **[!UICONTROL Nur Mitglied]**
GruppeAuswahl 
`Member Only Group` gibt an, dass nur Mitglieder der Gruppe den Inhalt anzeigen können, und hebt die Auswahl  `Open Group`auf.

Unter dem Tab **[!UICONTROL Vorlage]** können Sie aus der Liste der Community-Gruppenvorlagen auswählen, die angegeben wurden, als die Gruppenfunktion in der Struktur der Community-Site oder in einer Community-Site-Vorlage enthalten war.

![chlimage_1-238](assets/chlimage_1-238.png)

Auf der Registerkarte **[!UICONTROL Bild]** können Sie ein Bild hochladen, das auf der Seite „Gruppen“ der Community-Site angezeigt werden soll. Durch das Standard-Stylesheet wird das Bild auf eine Größe von 170 x 90 Pixeln zugeschnitten.

![chlimage_1-239](assets/chlimage_1-239.png)

Wählen Sie die Schaltfläche **[!UICONTROL Gruppe erstellen]** aus, werden die Gruppenseiten basierend auf der ausgewählten Vorlage erstellt. Es wird eine Gruppe für Mitglieder erstellt und die Seite „Gruppen“ wird so aktualisiert, dass die neue Unter-Community aufgeführt wird.

Die Seite „Gruppen“ mit einer neuen Unter-Community mit dem Namen „Focus Group“ (Gesprächsgruppe), für die ein Thumbnail hochgeladen wird, sieht beispielsweise wie folgt aus (der aktuelle Benutzer ist als Community-Gruppenadministrator angemeldet):

![chlimage_1-240](assets/chlimage_1-240.png)

Wenn Sie den Link `Focus Group` auswählen, wird die Seite &quot;Fokusgruppe&quot;im Browser geöffnet, die basierend auf der ausgewählten Vorlage ein erstes Erscheinungsbild aufweist und ein Untermenü unter dem Menü der Haupt-Community-Site enthält:

![chlimage_1-241](assets/chlimage_1-241.png)

## Komponente „Community-Gruppenmitgliederliste“{#community-group-member-list-component}

Die Komponente `Community Group Member List` ist für Entwickler von Gruppenvorlagen vorgesehen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Community-Gruppengrundlagen](essentials-groups.md) für Entwickler.

Weitere Informationen zu Community-Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).
