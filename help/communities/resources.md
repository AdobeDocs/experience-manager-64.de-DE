---
title: Konsole "Aktivierungsressourcen"
seo-title: Enablement Resources Console
description: In der Ressourcenkonsole erstellen, verwalten und weisen Aktivierungsmanager Ressourcen Mitgliedern einer Aktivierungs-Community-Site zu.
seo-description: The Resources console is where Enablement Managers create, manage, and assign resources to members of an enablement community site
uuid: 52445b39-c339-4b39-8004-eb36de99bced
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1ef15e76-fe7c-4ced-a20d-c0a9385e3ee4
role: Admin
exl-id: 67d80ec9-64c9-43a5-8cb1-9da819471797
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2993'
ht-degree: 5%

---

# Konsole &quot;Aktivierungsressourcen&quot; {#enablement-resources-console}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Bei AEM Communities befindet sich die Ressourcenkonsole an der Stelle [Aktivierungsmanager](users.md) Ressourcen erstellen, verwalten und Mitgliedern einer Aktivierungs-Community-Site zuweisen.

## Voraussetzungen {#requirements}

Bevor Sie Aktivierungsressourcen für eine Community-Site hinzufügen, müssen die AEM-Instanzen ordnungsgemäß konfiguriert werden, einschließlich:

* SCORM
* FFmpeg

Weitere Informationen finden Sie unter [Konfiguration der Aktivierung](enablement.md).

>[!CAUTION]
>
>Wenn SCORM nach der Erstellung der Community-Site installiert wird, müssen alle Aktivierungsressourcen, die vor der Installation von SCORM vorhanden sind, neu erstellt werden.

>[!NOTE]
>
>Mit der Veröffentlichung von [AEM 6.3](deploy-communities.md#latestfeaturepack) und den entsprechenden Communities Feature Packs [AEM 6.2 FP3](deploy-communities.md#latestfeaturepack) und [AEM 6.1 FP7](https://docs.adobe.com/content/docs/en/aem/6-1/deploy/communities.html#Latest Feature Pack), erfordert die Aktivierungsfunktion keine [MySQL-Datenbank](mysql.md).

## Terminologie {#terminology}

### Ressource {#resource}

Ressourcen sind für eine [Aktivierungs-Community](overview.md#enablement-community). Sie sind die Materialien, die den Mitgliedern zugewiesen sind, um sie in die Lage zu versetzen, ihre Fähigkeiten zu verbessern.

Eigenschaften einer Ressource:

* Kann vom Typ
   * Bild (JPG, PNG, GIF, BMP)
   * Video (MP4)
   * Flash (SWF)
   * Dokument (PDF)
   * Quiz (SCORM)
* Kann über einen oder mehrere Lernpfade referenziert werden

### Lernpfad {#learning-path}

Ein Lernpfad ist ein logischer Satz von Aktivierungsressourcen, die gruppiert werden, um die Zuweisung zu Mitgliedern zu erleichtern.

### Mitgliedergruppe {#members-group}

Wenn eine Community-Site erstellt wird, wird bei der Erstellung der [Site-spezifische Benutzergruppen](users.md) mit verschiedenen Berechtigungen für verschiedene Rollen konfiguriert. Alle diese automatisch erstellten Gruppen erhalten das Präfix `Community *<site-name>*`.

Eine dieser Benutzergruppen ist `Community *<site-name>* Members` -Gruppe, die registrierte Benutzer in der Veröffentlichungsumgebung als Community-Mitglieder identifiziert. Siehe Tutorial [Erste Schritte mit AEM Communities zur Aktivierung](getting-started-enablement.md) für ein Beispiel.

Für [Interaktionsgemeinschaften](overview.md#egagementcommunity), ist es sinnvoll, Site-Besuchern die Möglichkeit zu geben, sich selbst zu registrieren oder die Anmeldung über soziale Netzwerke zu verwenden. An diesem Punkt werden sie automatisch zur Mitgliedergruppe hinzugefügt.

Für [Aktivierungsgemeinschaften](overview.md#enablement-community), wird empfohlen, die Site privat zu gestalten, sodass dann ein Administrator Benutzer zur Mitgliedergruppe hinzufügen muss.

## Zugriff auf die Aktivierungsressourcen einer Community-Site {#accessing-a-community-site-s-enablement-resources}

### Navigieren zu Communities-Ressourcen {#navigate-to-communities-resources}

In der Autorenumgebung, um die Ressourcenkonsole zu erreichen

* Über die globale Navigation: **[!UICONTROL Navigation > Communities > Ressourcen]**

![chlimage_1-163](assets/chlimage_1-163.png)

### Community-Site auswählen {#select-a-community-site}

Die Communities-Ressourcen-Konsole zeigt alle Community-Sites an.

Aktivierungsressourcen werden für eine bestimmte Community-Site erstellt, nachdem Sie die Site in der Ressourcenkonsole ausgewählt haben.

Sobald eine bestimmte Community-Site ausgewählt ist, können alle vorhandenen Aktivierungsressourcen und Lernpfade für die Verwaltung und Änderung aufgerufen und neue Aktivierungsressourcen und Lernpfade erstellt werden.

![chlimage_1-164](assets/chlimage_1-164.png)

#### Suchen {#search-features}

![chlimage_1-165](assets/chlimage_1-165.png)

Wählen Sie das Umschalter-Symbol für das seitliche Bedienfeld aus, um nach einer Aktivierungsressource oder einem Lernpfad zu suchen. Wenn diese Option aktiviert ist, wird auf der linken Seite der Konsole ein Suchfeld geöffnet und ein Textfeld bereitgestellt, in das Suchbegriffe eingegeben werden können.

![chlimage_1-166](assets/chlimage_1-166.png)

#### Auswahlmodus {#selection-mode}

Um mehrere Aktivierungsressourcen auszuwählen, wählen Sie die erste aus, indem Sie den Mauszeiger über die Karte bewegen und das Häkchen-Symbol auswählen. Wenn Sie eine andere Karte auswählen, wird diese der Auswahlgruppe hinzugefügt. Wenn Sie ein zweites Mal auswählen, wird die Karte deaktiviert.

![chlimage_1-167](assets/chlimage_1-167.png)

## Erstellen einer Ressource {#create-a-resource}

![chlimage_1-168](assets/chlimage_1-168.png)

Hinzufügen einer neuen Aktivierungsressource zur Community-Site

* Wählen Sie die `Create` icon
* Wählen Sie aus dem angezeigten Untermenü die Option `Resource`

Dadurch wird ein schrittweiser Prozess von

* Beschreibung der Ressource (Name, Kartenbild und Text)
* Ressourceninhalt auswählen
* Titelbild für die Ressource auswählen
* Identifizieren von Ressourcenkontakten
* Zuweisen von Ressourcen zu Mitgliedern

Wenn die Ressource Teil eines Kurses, eines Lernpfads ist, sollten Mitglieder nur dem Lernpfad zugewiesen werden. Zuweisungen können hinzugefügt werden, nachdem die Aktivierungsressource erstellt wurde.

### 1 Grundlegende Informationen {#basic-info}

![chlimage_1-169](assets/chlimage_1-169.png)

* **[!UICONTROL Bild hinzufügen]**

   (*optional*) Ein Bild, das auf der Karte für die Aktivierungsressource auf der Zuweisungsseite des Mitglieds sowie in der Ressourcenkonsole angezeigt wird. Das Bild wird aus dem lokalen Dateisystem des Servers ausgewählt. Wenn kein Bild bereitgestellt wird, wird eine Miniaturansicht für die hochgeladene Ressource generiert.

   ***Hinweis***: Die empfohlene Bildgröße beträgt nicht einfach 480 x 480 Pixel. Aufgrund des responsiven Designs der Karten mit verschiedenen Browser-Abmessungen variiert die Anzeigegröße von 220 x 165 Pixel bis 400 x 165 Pixel.

* **[!UICONTROL Site-Name]**

   (*readonly*) Die Community-Site, der die Ressource hinzugefügt wird.

* **[!UICONTROL Resource Name&amp;ast;]**

   (*erforderlich*) Der Anzeigename für die Ressource. Ein gültiger Knotenname wird aus dem Anzeigenamen erstellt.

* **[!UICONTROL Tags]**

   (*optional*) Es können ein oder mehrere Tags ausgewählt werden, die die Aktivierungsressource mit einem oder mehreren Katalogen verknüpfen. Siehe [Tagging von Aktivierungsressourcen](tag-resources.md).

* **[!UICONTROL Im Katalog anzeigen]**

   Wenn diese Option deaktiviert ist, wird die Aktivierungsressource in keinem Katalog angezeigt. Wenn diese Option aktiviert ist, wird die Aktivierungsressource in allen Katalogen angezeigt, es sei denn, [vorgefiltert](catalog-developer-essentials.md#pre-filters) oder die Member-Filter aus der Benutzeroberfläche. Die Option Standard ist deaktiviert.

* **[!UICONTROL Beschreibung]**

   (*optional*) Die Beschreibung, die für die Aktivierungsressource angezeigt werden soll.

* **[!UICONTROL Kleines Asset]**

   (*optional*) Aus AEM Assets ausgewählt. Ein Miniaturbild, das die Ressource in der Veröffentlichungsumgebung darstellt, z. B. in einem Katalog.

* **[!UICONTROL Großes Asset]**

   (*optional*) Aus AEM Assets ausgewählt. Ein großes Bild, das die Ressource in der Veröffentlichungsumgebung darstellt, z. B. auf der Hauptseite einer Ressource.

* **[!UICONTROL Inhaltsfragment-Asset]**

   (*optional*) Aus AEM Assets ausgewählt. Ein Inhaltsfragment, auf das in der Veröffentlichungsumgebung verwiesen werden kann, das jedoch nicht standardmäßig verwendet wird.

* Wählen Sie **[!UICONTROL Weiter]** aus

### 2 Inhalt hinzufügen {#add-content}

![chlimage_1-170](assets/chlimage_1-170.png)

Es wird zwar so angezeigt, als ob mehrere Aktivierungsressourcen ausgewählt sein könnten, aber nur eine ist zulässig.

Wählen Sie die `'+' icon`in der oberen rechten Ecke, um mit der Auswahl der Ressource zu beginnen, indem die Quelle identifiziert wird.

![chlimage_1-171](assets/chlimage_1-171.png)

* **[!UICONTROL Hochladen aus meinen lokalen Dateien]**
Beim Hochladen aus dem lokalen Dateisystem wird der native Dateibrowser verwendet, um eine Datei auszuwählen und hochzuladen. Unterstützt werden die Dateitypen SCORM.zip (HTML 5 oder SWF), MP4-Video, SWF, PDF und Bildtypen (JPG, PNG, GIF, BMP). Der Dateiname wird zum Namen des Assets, das der Asset-Bibliothek hinzugefügt wird.

* **[!UICONTROL Asset-Bibliothek durchsuchen]**
Wählen Sie aus der Asset-Bibliothek aus. Die Auswahl ist auf diejenigen beschränkt, die auf der Community-Site sichtbar sind.

* **[!UICONTROL Externe URL hinzufügen]**

   Geben Sie einen Link zu Lerninhalten ein.

   Geben Sie in das sich öffnende Dialogfeld Folgendes ein:

   * **[!UICONTROL Titel]**

      Der Name des Assets für die Aktivierungsressource.

   * **[!UICONTROL URL]**

      Die URL zu einem Asset.

* **[!UICONTROL Adobe Connect-URL hinzufügen]**

   Geben Sie einen Link zu einer Adobe Connect-Sitzung ein.

   Geben Sie in das sich öffnende Dialogfeld Folgendes ein:

   * **[!UICONTROL Titel]**

      Der Name des Assets für die Aktivierungsressource.

   * **[!UICONTROL URL]**

      Die URL zu einer Adobe Connect-Sitzung.

* **[!UICONTROL Externe Ressource definieren]**

   Geben Sie an, wo das Material vorgestellt werden soll. Die Werte für Erfolgsstatus und Erfolgsbewertung werden manuell eingegeben (siehe [Berichte](reports.md)). Ein hochgeladenes Titelbild kann verwendet werden, um zusätzliche Informationen bereitzustellen.

   Geben Sie in das sich öffnende Dialogfeld Folgendes ein:

   * **[!UICONTROL Titel]**

      Der Name des Assets für die Aktivierungsressource.

   * **[!UICONTROL Speicherort]**

      Die Lage eines physischen Standorts, z. B. eines Klassenzimmers.

#### Beispiel einer hinzugefügten Videoressource {#example-of-an-added-video-resource}

![chlimage_1-172](assets/chlimage_1-172.png)

* **[!UICONTROL Ressourcen-Titelbild]**

   Das Titelbild ist ein Bild, das angezeigt wird, wenn die Aktivierungsressource zum ersten Mal angezeigt wird. Beispielsweise wird das Titelbild angezeigt, wenn eine Videoressource noch nicht wiedergegeben wird. Wenn kein benutzerdefiniertes Bild hochgeladen wird, wird ein Standardbild angezeigt. Bei Videoressourcen kann es möglich sein, [Miniaturansicht generieren](enablement.md#ffmpeg), jedoch nur beim Hochladen und nicht, wenn das Video als URL referenziert wird. Für Standortressourcen kann das Bild verwendet werden, um zusätzliche Informationen bereitzustellen.

   Die empfohlene Größe für das Titelbild beträgt 640 x 360 Pixel.

* Wählen Sie **[!UICONTROL Weiter]** aus

### 3 Einstellungen {#settings}

![chlimage_1-173](assets/chlimage_1-173.png)

>[!NOTE]
>
>Lernende sollten nicht direkt in Aktivierungsressourcen eingeschrieben werden, die aus einem Lernpfad referenziert werden sollen. Lernende müssen nur in den Lernpfad eingeschrieben werden.
>
>Wenn ein Mitglied sowohl in einer Ressource als auch in einem Lernpfad eingeschrieben ist, der auf diese Ressource verweist, zeigen seine Zuweisungen sowohl die einzelne Ressource als auch die Ressource im Lernpfad an.

* **[!UICONTROL Einstellungen für Social Media]**

   Diese Einstellungen steuern, ob Lernende Eingaben zur Aktivierungsressource bereitstellen können. Die [Moderationseinstellungen](sites-console.md#moderation) sind die der übergeordneten Community-Site.

   * **[!UICONTROL Kommentieren zulassen]**

      Wenn diese Option aktiviert ist, können Mitglieder die Ressource kommentieren. Die Option Standard ist aktiviert.

   * **[!UICONTROL Bewertungen zulassen]**

      Wenn diese Option aktiviert ist, dürfen Mitglieder die Ressource bewerten. Die Option Standard ist aktiviert.

   * **[!UICONTROL Anonymen Zugriff erlauben]**

      Wenn diese Option aktiviert ist, können anonyme Site-Besucher die Ressource in einem Katalog anzeigen, wenn die Community-Site auch einen anonymen Zugriff zulässt. Die Option Standard ist deaktiviert.

* **[!UICONTROL Fälligkeitsdatum]**

   *(Optional)* Es kann ein Datum ausgewählt werden, bis zu dem die Zuweisung abgeschlossen werden soll.

* **[!UICONTROL Ressourcen-Autor]**
   *(Optional)* Der Autor der Aktivierungsressource. Verwenden Sie das Pulldown-Menü, um aus den Benutzern auszuwählen, die Mitglieder des [Mitgliedergruppe](#members-group).

* **[!UICONTROL Resource Contact&amp;ast;]**
   *(Erforderlich)* Eine Person, die das Mitglied bezüglich der Aktivierungsressource kontaktieren kann. Verwenden Sie das Pulldown-Menü, um aus den Benutzern auszuwählen, die Mitglieder des [Mitgliedergruppe](#members-group).

* **[!UICONTROL Ressourcen-Experte]**
   *(Optional)* Eine Person, die das Mitglied kontaktieren kann, die über Fachwissen in Bezug auf die Aktivierungsressource verfügt. Wählen Sie über das Pulldown-Menü Benutzer aus, die Mitglieder des [Mitgliedergruppe](#members-group).

### 4 Zuweisung {#assignments}

![chlimage_1-174](assets/chlimage_1-174.png)

* **[!UICONTROL Zuweisende Stellen hinzufügen]**
Verwenden Sie das Pulldown-Menü, um aus [members](#members-group) - die Benutzer und Benutzergruppen (fettgedruckt), die als Lernende eingeschrieben werden sollen. Wenn sich Mitglieder bei der Community-Site anmelden, werden die Aktivierungsressourcen (und Lernpfade), in denen sie angemeldet sind, auf ihrer [Zuweisungen](functions.md#assignments-function) Seite.

* select **[!UICONTROL Erstellen]**

![chlimage_1-175](assets/chlimage_1-175.png)

Die erfolgreiche Erstellung der Aktivierungsressource kehrt mit der ausgewählten neu erstellten Ressource zur Ressourcenkonsole zurück. In dieser Konsole können Sie [Ressource verwalten](#managing-a-resource).

## Lernpfad erstellen {#create-a-learning-path}

![chlimage_1-176](assets/chlimage_1-176.png)

So fügen Sie einen neuen Lernpfad zur Community-Site hinzu

* Wählen Sie die `Create` icon
* Wählen Sie aus dem angezeigten Untermenü die Option `Learning Path`

Dadurch wird ein schrittweiser Prozess von

* Lernpfad identifizieren
* Bereitstellung eines Kartenbilds zur Darstellung des Lernpfads für die Lernenden
* Referenzierung der Aktivierungsressourcen, die in den Lernpfad aufgenommen werden sollen
* Ressourcen optional anordnen
* Optional Identifizieren von vorausgesetzten Lernpfaden
* Lernpfadkontakt identifizieren
* Abonnenten

Bei Aktivierungsressourcen, die in einem Lernpfad enthalten sind, sollten die Zuweisungen nur für den Lernpfad und nicht für die einzelnen Ressourcen vorgenommen werden.

### Grundlegende Informationen {#basic-info-1}

![chlimage_1-177](assets/chlimage_1-177.png)

* **[!UICONTROL Bild hinzufügen]**

   (*optional*) Ein Bild, das auf der Karte für den Lernpfad auf der Zuweisungsseite des Mitglieds sowie in der Ressourcenkonsole angezeigt wird. Das Bild wird aus dem lokalen Dateisystem des Servers ausgewählt. Wenn kein Bild bereitgestellt wird, wird eine Miniaturansicht für die hochgeladene Ressource generiert.

   ***Hinweis***: Die empfohlene Bildgröße beträgt nicht mehr einfach 480 x 480 Pixel. Aufgrund des responsiven Designs der Karten mit verschiedenen Browser-Abmessungen variiert die Anzeigegröße von 220 x 165 Pixel bis 400 x 165 Pixel.

* **[!UICONTROL Site-Name]**

   (*readonly*) Die Community-Site, der die Ressource hinzugefügt wird.

* **[!UICONTROL Lernpfad-Name]**

   (*erforderlich*) Der Anzeigename für den Lernpfad. Ein gültiger Knotenname wird aus dem Anzeigenamen erstellt.

* **[!UICONTROL Tags]**

   (*optional*) Es können ein oder mehrere Tags ausgewählt werden, die den Lernpfad mit einem oder mehreren Katalogen verknüpfen. Siehe [Tagging von Aktivierungsressourcen](tag-resources.md).

* **[!UICONTROL Im Katalog anzeigen]**

   Wenn diese Option deaktiviert ist, wird der Lernpfad in keinem Katalog angezeigt. Wenn diese Option aktiviert ist, wird der Lernpfad in allen Katalogen angezeigt, es sei denn, [vorgefiltert](catalog-developer-essentials.md#pre-filters) oder die Member-Filter aus der Benutzeroberfläche. Durch die Anzeige des Lernpfads in einem Katalog wird LESE indirekt Zugriff auf alle darin enthaltenen Ressourcen gewährt. Die Option Standard ist deaktiviert.

* **[!UICONTROL Beschreibung]**

   (*optional*) Die Beschreibung, die für die Aktivierungsressource angezeigt werden soll.

* **[!UICONTROL Kleines Asset]**

   (*optional*) Aus AEM Assets ausgewählt. Ein Miniaturbild, das die Ressource in der Veröffentlichungsumgebung darstellt, z. B. in einem Katalog.

* **[!UICONTROL Großes Asset]**

   (*optional*) Aus AEM Assets ausgewählt. Ein großes Bild, das die Ressource in der Veröffentlichungsumgebung darstellt, z. B. auf der Hauptseite einer Ressource.

* **[!UICONTROL Inhaltsfragment-Asset]**

   (*optional*) Aus AEM Assets ausgewählt. Ein Inhaltsfragment, auf das in der Veröffentlichungsumgebung verwiesen werden kann, das jedoch nicht standardmäßig verwendet wird.

* Wählen Sie **[!UICONTROL Weiter]** aus

### Voraussetzungen hinzufügen {#add-prerequisites}

![chlimage_1-178](assets/chlimage_1-178.png)

* **[!UICONTROL Erforderliche Lernpfade]**
(
*optional*) Wenn andere veröffentlichte Lernpfade ausgewählt werden, müssen sie abgeschlossen sein, bevor ein Lernender diesen Lernpfad auswählen kann.

* Wählen Sie **[!UICONTROL Weiter]** aus

### Ressourcen hinzufügen {#add-resources}

![chlimage_1-179](assets/chlimage_1-179.png)

* **[!UICONTROL Reihenfolge im Lernpfad erzwingen]**

   (*optional*) wenn auf &quot;Ein&quot;gesetzt, entspricht die Reihenfolge, in der die Aktivierungsressourcen hinzugefügt werden, der Reihenfolge, in der die Lernenden den Lernpfad durchlaufen müssen. Der Standardwert ist &quot;Aus&quot;.

* **[!UICONTROL Ressourcen]**

   Eine oder mehrere Ressourcen, die aus den *veröffentlichten *Aktivierungsressourcen ausgewählt wurden, die für die aktuelle Community-Site erstellt wurden.

>[!NOTE]
>
>Sie können nur die Ressourcen auswählen, die auf derselben Ebene wie der Lernpfad verfügbar sind. Beispielsweise sind für einen in einer Gruppe erstellten Lernpfad nur die Ressourcen auf Gruppenebene verfügbar. für einen Lernpfad, der auf einer Community-Site erstellt wurde, stehen die Ressourcen auf dieser Site zum Hinzufügen zum Lernpfad zur Verfügung.

* Wählen Sie **[!UICONTROL Weiter]** aus.

### Einstellungen {#settings-1}

![chlimage_1-180](assets/chlimage_1-180.png)

* **[!UICONTROL Einschreibungen hinzufügen]**

   Wählen Sie über das Pulldown-Menü aus den (fett gedruckten) Mitgliedern und Mitgliedergruppen aus, die Mitglieder der Community-Site sind. [Mitgliedergruppe](#members-group). Es ist nicht erforderlich, beim ersten Erstellen des Lernpfads Zuweisungen hinzuzufügen. Die Eigenschaften des Lernpfads können geändert werden, um Lernende zu einem späteren Zeitpunkt hinzuzufügen.

* **[!UICONTROL Lernpfad Kontakt&amp;ast;]**

   *(Erforderlich)* Eine Person, die das Mitglied bezüglich des Lernpfads kontaktieren kann. Verwenden Sie das Pulldown-Menü, um aus den Benutzern auszuwählen, die Mitglieder der Community-Site sind. [Mitgliedergruppe](#members-group).

* Wählen Sie **[!UICONTROL Erstellen]** aus

>[!NOTE]
>
>Aktivierungsressourcen, auf die über den Lernpfad verwiesen wird, sollten nicht dieselben Zuweisenden (Lernenden) auflisten, falls vorhanden.
>
>Wenn ein Mitglied sowohl in einer Aktivierungsressource als auch in einem Lernpfad eingeschrieben ist, der auf diese Ressource verweist, zeigen seine Zuweisungen sowohl die einzelne Ressource als auch die Ressource im Lernpfad an.

## Verwalten einer Ressource {#managing-a-resource}

So verwalten Sie eine einzelne Aktivierungsressource

* In der Ressourcenkonsole
* Wählen Sie die Community-Site aus, die die Ressource enthält
* Ressource auswählen

Für die ausgewählte Aktivierungsressource haben Sie folgende Möglichkeiten:

* Eigenschaften anzeigen (Standard)
* Bearbeiten von Eigenschaften
* Löschen
* Veröffentlichen
* Veröffentlichung aufheben

Um eine neue Version der Aktivierungsressource hochzuladen, wird empfohlen, eine neue Ressource zu erstellen, dann die Registrierung für Mitglieder aus der alten Version aufzuheben und sie in der neuen Version zu registrieren.

### Ressource bearbeiten {#edit-resource}

![chlimage_1-181](assets/chlimage_1-181.png)

Durch Auswahl des Stiftsymbols werden die Schritte zum Erstellen einer Aktivierungsressource verfügbar gemacht, sodass alle bereitgestellten Informationen geändert werden können.

Wenn die einzige Änderung darin besteht, Zuweisungen im Schritt Einstellungen zu ändern, werden die Änderungen durch Speichern veröffentlicht. Wenn andere Änderungen vorgenommen werden, muss die Ressource nach dem Speichern explizit veröffentlicht werden.

### Ressource löschen {#delete-resource}

![chlimage_1-182](assets/chlimage_1-182.png)

Durch Auswahl des Papierkorbsymbols wird die Aktivierungsressource `Delete`d nach Bestätigung.

### Veröffentlichen  {#publish}

![chlimage_1-183](assets/chlimage_1-183.png)

Bevor Lernende die zugewiesenen Aktivierungsressourcen sehen können, müssen sie veröffentlicht werden:

* Wählen Sie das Weltsymbol aus, um `Publish`
* Wählen Sie in dem sich öffnenden Dialogfeld **[!UICONTROL Veröffentlichen]** repeat
* Auswählen **[!UICONTROL Schließen]**

Obwohl im Dialogfeld angegeben wird, dass die Aktion in die Warteschlange gestellt wird, wird sie oft sofort veröffentlicht.

### Veröffentlichung aufheben {#unpublish}

![chlimage_1-184](assets/chlimage_1-184.png)

Wenn Sie die Aktivierungsressourcen vorübergehend für Mitglieder in der Veröffentlichungsumgebung unzugänglich machen möchten, ohne sie zu löschen, verwenden Sie das Symbol Welt , um `Unpublish`die Ressource.

### Bericht {#report}

![chlimage_1-185](assets/chlimage_1-185.png)

Über das Symbol Bericht können Sie auf die Berichte zugreifen, die bei der Interaktion der Lernenden mit den ihnen zugewiesenen Aktivierungsressourcen in der Veröffentlichungsumgebung erstellt wurden. Der Bericht variiert je nach Ressourcentyp.

Für alle Lernpfade ist es möglich, einen Bericht basierend auf Ressourcen oder Lernenden anzuzeigen ( `User Report`).

![chlimage_1-186](assets/chlimage_1-186.png)

Dieser Bericht ist speziell für die aktuelle Aktivierungsressource oder den Lernpfad gedacht. Die Tiefe der bereitgestellten Berichte hängt davon ab, ob [Adobe Analytics](analytics.md) ist für die Community-Site lizenziert und aktiviert. Die [Timeline](#timeline), [Interaktion des Betrachters](#viewer-engagement)und [Interaktion nach Gerät](#engagement-by-device) Berichte werden basierend auf dem [Abrufintervall](analytics.md#report-importer).

Für alle Aktivierungsressourcen werden Berichte zu [Status des Bevollmächtigten](#assignee-status) und [Bewertungen](#ratings) sowie [Berichtszusammenfassung](#report-summary) Tabelle.

![chlimage_1-187](assets/chlimage_1-187.png)

#### Zeitleiste {#timeline}

Der Bericht zur Analytics-Timeline zeigt an, wann Ereignisse im Laufe der Zeit für diese Aktivierungsressource auftreten:

* **Ansichten**

   Eine Ansicht ist, wenn ein Lernender die Seite mit den Ressourcendetails besucht

* **Wiedergaben**

   Eine Wiedergabe ist die Interaktion von alLernenden mit der Ressource, z. B. das Abspielen eines Videos oder das Öffnen einer PDF.

* **Bewertungen**

   Bei einer Bewertung weist ein Lernender einer Ressource eine Sternbewertung zu

* **Kommentare**

   Ein Kommentar ist, wenn AlLerner einen Kommentar hinzufügt

Die vertikale Achse ist die Anzahl der Ereignisse.

Die horizontale Achse ist die Kalenderzeit.

[Adobe Analytics erforderlich](sites-console.md#analytics).

#### Betrachterinteraktion {#viewer-engagement}

Der Bericht zur Interaktion mit Analytics-Viewern zeigt für Videoressourcen die Anzahl der Lernenden an, die die Ressource angesehen haben, und, falls sie nicht bis zum Ende wiedergegeben wurde, an welchem Punkt die Wiedergabe angehalten wurde.

Die vertikale Achse gibt die Anzahl der Lernenden an, die diese Ressource angesehen haben.

Die horizontale Achse ist die Dauer dieser Ressource.

[Marketing Cloud-Organisations-ID erforderlich](sites-console.md#enablement).

#### Interaktion nach Gerät {#engagement-by-device}

Der Bericht &quot;Analytics-Interaktion nach Gerät&quot;beschreibt für Videoressourcen den Prozentsatz der Ansichten, die vom Desktop und von Mobilgeräten aus wiedergegeben wurden.

[Marketing Cloud-Organisations-ID erforderlich](sites-console.md#enablement).

#### Status des Bevollmächtigten {#assignee-status}

Der Bericht zum Bevollmächtigten-Status beschreibt anhand der Anzahl der Lernenden, wie viele

* **Nicht gestartet**
* **In Bearbeitung**
* **Abgeschlossen**

#### Bewertungen {#ratings}

Der Bericht Bewertungen basiert auf der Anzahl der Lernenden, die die Aktivierungsressource bewertet haben, wobei die Anzahl der einzelnen Sternbewertungen sowie eine Zusammenfassung der Gesamtanzahl der Bewertungen und der durchschnittlichen Bewertung angezeigt werden.

#### Berichtszusammenfassung {#report-summary}

Bei einer Aktivierungsressource ist die Berichtszusammenfassung eine Tabellenliste

* Jeder Lernende, der mit der Ressource interagiert hat
   * Ihr Status
   * Ob ihnen die Ressource zugewiesen wurde
      * Anders als beim Suchen der Ressource in einem Katalog
   * Anzahl der geposteten Kommentare
   * gegebenenfalls die Angabe des Ratings

Bei einem Ressourcenbericht für Lernpfade ist die Berichtszusammenfassung eine Tabellenliste

* Jede Ressource im Lernpfad
   * Veröffentlichungsstatus
   * Anzahl der Ansichten
   * Anzahl der Wiedergaben
   * Durchschnittliche Bewertung
   * Format
   * Größe
   * Community-Site-Name

Für einen Lernpfad-Benutzerbericht ist die Berichtszusammenfassung eine Tabellenliste

* Jeder Lernende, der dem Lernpfad zugewiesen ist
   * Anzahl der abgeschlossenen Ressourcen
   * Ihr Status

Die Anzeige der Tabelle kann angepasst werden, indem Spalten mithilfe der Variablen `Show / hide columns` auswählen.

#### Bericht als CSV herunterladen {#download-report-as-csv}

Die Tabelle &quot;Berichtzusammenfassung&quot;kann im CSV-Format mithilfe einer Schaltfläche oben in der Konsole heruntergeladen werden.

* für eine Aktivierungsressource: `Download Resource Report as CSV` button
* für einen Lernpfad: `Download Learning Path Report as CSV` button

Die vollständige Berichtzusammenfassung wird unabhängig von den für die Anzeige ausgewählten Spalten heruntergeladen.
