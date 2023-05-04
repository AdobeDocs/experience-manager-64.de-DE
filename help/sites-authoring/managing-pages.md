---
title: Erstellen und Organisieren von Seiten
seo-title: Creating and Organizing Pages
description: So erstellen und verwalten Sie Seiten mit AEM
seo-description: How to create and manage pages with AEM
uuid: 9bdc3222-6a0c-48a2-be1d-79ceb3bbc828
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: a727c57c-87a9-46c2-8d9b-1348f1ed8ac4
exl-id: 0182155a-0156-458c-b89b-35ab3e27819e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2331'
ht-degree: 67%

---

# Erstellen und Organisieren von Seiten{#creating-and-organizing-pages}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

In diesem Abschnitt wird beschrieben, wie Sie Seiten mit Adobe Experience Manager (AEM) erstellen und verwalten, damit Sie dann [Inhalt erstellen](/help/sites-authoring/editing-content.md) auf diesen Seiten.

>[!NOTE]
>
>Ihr Konto muss [angemessene Zugriffsberechtigungen](/help/sites-administering/security.md) und [Berechtigungen](/help/sites-administering/security.md#permissions) , um Aktionen auf Seiten auszuführen, z. B. Erstellen, Kopieren, Verschieben, Bearbeiten und Löschen.
>
>Wenn Sie auf Probleme stoßen, empfehlen wir Ihnen, sich an den Systemadministrator zu wenden.

>[!NOTE]
>
>Es steht eine Reihe von [Tastaturbefehlen](/help/sites-authoring/keyboard-shortcuts.md) in der Websites-Konsole zur Verfügung, die eine effizientere Seitenorganisation ermöglichen.

## Website-Organisation {#organizing-your-website}

Als Autor müssen Sie Ihre Website in AEM organisieren. Dazu gehört die Erstellung und Benennung von Inhaltsseiten, sodass:

* Sie müssen leicht in der Authoring-Umgebung auffindbar sein.
* Besucher der Website müssen sie einfach in der Veröffentlichungsumgebung durchsuchen können.

Sie können Ihre Inhalte auch mithilfe von [Ordnern](#creating-a-new-folder) organisieren.

Die Struktur einer Website kann als Baumstruktur gesehen werden, die die Inhaltsseiten enthält. Die Namen dieser Inhaltsseiten werden zur Bildung der URLs verwendet. Der Titel wird zusammen mit dem Seiteninhalt angezeigt.

Im Folgenden sehen Sie ein Beispiel von der Website We.Retail, auf der eine Seite mit Cargo-Shorts (`desert-sky-shorts`) aufgerufen wird:

* Authoring-Umgebung: `http://localhost:4502/editor.html/content/we-retail/us/en/products/equipment/hiking/desert-sky-shorts.html`

* Publishing-Umgebung: `http://localhost:4503/content/we-retail/us/en/products/equipment/hiking/desert-sky-shorts.html`

Je nach Konfiguration Ihrer Instanz kann die Verwendung von `/content` in der Publishing-Umgebung optional sein.

```xml
 /content
 /we-retail
  /us
   /en
    /products
     /equipment
      /hiking
       /desert-sky-shorts
       /hiking-poles
       /... 
      /running...
      /surfing...
      /...
     /seasonal...
     /...
    /about-us
    /experience
    /...
   /es...
  /de...
  /fr...
  /...
 /...
```

Diese Struktur kann über die **Sites-Konsole** angezeigt werden. Von dort aus können Sie [durch die Seiten Ihrer Website navigieren](/help/sites-authoring/basic-handling.md#product-navigation) und Aktionen auf den Seiten durchführen. Sie können auch neue Sites und [neue Seiten](#creating-a-new-page) erstellen.

An jedem Punkt können Sie die Verzwigung nach oben in den Breadcrumbs in der Kopfzeilenleiste sehen:

![screen_shot_2018-03-22at104706](assets/screen_shot_2018-03-22at104706.png)

### Seitenbenennungskonventionen {#page-naming-conventions}

Beim Erstellen einer neuen Seite gibt es zwei Schlüsselfelder:

* **[Titel](#title)**:

   * Dieses Feld wird dem Benutzer bei der Bearbeitung im oberen Teil des Seiteninhalts in der Konsole angezeigt.
   * Dieses Feld ist obligatorisch.

* **[Name](#name)**:

   * Mit diesem Wert wird der URI generiert.
   * Benutzereingaben sind für dieses Feld optional. Wenn kein Name angegeben ist, wird der Name vom Titel abgeleitet. Weitere Informationen finden Sie unter [Seitennamen-Einschränkungen und Best Practices](/help/sites-authoring/managing-pages.md#page-name-restrictions-and-best-practices).

#### Einschränkungen und Best Practices bei der Seitenbenennung {#page-name-restrictions-and-best-practices}

Der **Seitentitel** und der **Seitenname** können separat erstellt werden, sind aber verwandt:

* Beim Erstellen einer Seite ist nur das **Titelfeld** erforderlich. Wenn bei der Erstellung von Seiten kein **Name** angegeben wird, generiert AEM einen Namen aus den ersten 64 Zeichen des Titels (entsprechend der nachfolgenden Validierung). Nur die ersten 64 Zeichen werden verwendet, um gängige Best Practices für kurze Seitennamen zu unterstützen.

* Wenn ein Seitenname manuell vom Autor angegeben wird, gilt die Beschränkung von 64 Zeichen nicht, aber andere technische Einschränkungen gelten unter Umständen für die Länge des Seitennamens.

>[!NOTE]
>
>Beim Definieren eines Seitennamens ist es sinnvoll, den Seitennamen so kurz wie möglich zu halten, aber so ausdruckstark und erinnerungsstark wie möglich, um ihn für den Leser verständlich zu machen. Weitere Informationen zum `title`-Element finden Sie im [W3C-Styleguide](https://www.w3.org/Provider/Style/TITLE.html).
>
>Denken Sie auch daran, dass einige Browser (z. B. ältere Versionen von IE) nur URLs bis zu einer bestimmten Länge akzeptieren, sodass auch technisch Gründe für die Verwendung von kurzen Seitennamen bestehen.

Beim Erstellen einer neuen Seite [validiert AEM den Seitennamen entsprechend den AEM- und JCR-Konventionen](/help/sites-developing/naming-conventions.md).

Mindestens zulässig sind die folgenden Zeichen:

* &quot;a&quot;bis &quot;z&quot;
* &quot;A&quot;bis &quot;Z&quot;
* &quot;0&quot;bis &quot;9&quot;
* _ (Unterstrich)
* `-` (Bindestrich/Minus)

Umfassende Informationen zu allen zulässigen Zeichen finden Sie in den [Benennungskonventionen](/help/sites-developing/naming-conventions.md).

>[!NOTE]
>
>Wenn AEM auf einer [MongoMK-Persistenz-Manager-Bereitstellung](/help/sites-deploying/recommended-deploys.md) ausgeführt wird, sind Seitennamen auf 150 Zeichen beschränkt.

#### Titel {#title}

Wenn Sie für eine neu erstellte Seite nur den **Titel** angeben, leitet AEM den **Namen** für die Seite von dieser Zeichenfolge ab und [validiert den Namen entsprechend den Konventionen von AEM und JCR. ](/help/sites-developing/naming-conventions.md) Im Feld **Titel** werden ungültige Zeichen akzeptiert, wobei die ungültigen Zeichen im abgeleiteten Namen jedoch ersetzt werden. Beispiel:

| Titel | Abgeleiteter Name |
|---|---|
| Schön | schoen.html |
| SC%&amp;&amp;ast;ç+ | sc---c-.html |

#### Name {#name}

Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, [validiert AEM den Namen gemäß den AEM- und JCR-Konventionen](/help/sites-developing/naming-conventions.md). Die Eingabe von ungültigen Zeichen im Feld **Name** ist nicht zulässig. Wenn AEM ungültige Zeichen erkennt, wird das Feld durch eine erläuternde Meldung hervorgehoben.

![screen_shot_2018-03-22at104817](assets/screen_shot_2018-03-22at104817.png)

>[!NOTE]
>
>Sie sollten es vermeiden, einen Zwei-Buchstaben-Code gemäß ISO-639-1 als Seitennamen zu verwenden, sofern es sich nicht um einen Sprachstamm handelt.
>
>Siehe [Vorbereiten von Inhalten für die Übersetzung](/help/sites-administering/tc-prep.md) für weitere Informationen.

### Vorlagen {#templates}

In AEM gibt eine Vorlage einen speziellen Seitentyp an. Eine Vorlage wird als Grundlage für jede neue Seite verwendet, die erstellt wird.

Die Vorlage definiert die Seitenstruktur, u. a. eine Miniatur und andere Eigenschaften. Beispielsweise könnten Sie unterschiedliche Vorlagen für Produktseiten, Sitemaps und Kontaktangaben verwenden. Vorlagen bestehen aus [Komponenten](#components).

Im Lieferumfang von AEM sind diverse Vorlagen enthalten. Die verfügbaren Vorlagen hängen von der jeweiligen Website ab. Die wichtigsten Felder sind:

* **Titel**
Der Titel, der auf der resultierenden Web-Seite angezeigt wird.

* **Name**
Wird beim Benennen der Seite verwendet.

* **Vorlage**
Eine Liste von Vorlagen, die für das Erstellen neuer Seiten verwendet werden können.

>[!NOTE]
>
>Sofern auf Ihrer Instanz konfiguriert, [können Vorlagenautoren Vorlagen mit dem Vorlageneditor erstellen](/help/sites-authoring/templates.md).

### Komponenten {#components}

Komponenten sind die Elemente, die von AEM bereitgestellt werden, damit Sie bestimmte Inhaltstypen hinzufügen können. AEM ist mit [einsatzbereiten Komponenten](/help/sites-authoring/default-components-console.md) ausgestattet, die umfangreiche Funktionen bieten. Dazu gehören unter anderem:

* Text
* Bild
* Bildschirmpräsentation
* Video
* Und viele weitere

Nachdem Sie eine Seite erstellt und geöffnet haben, können Sie [Inhalt mithilfe der Komponenten hinzufügen](/help/sites-authoring/editing-content.md#inserting-a-component), die im Abschnitt [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser).

>[!NOTE]
>
>Die [Komponentenkonsole](/help/sites-authoring/default-components-console.md) bietet einen Überblick über die Komponenten in Ihrer Instanz.

## Verwalten von Seiten {#managing-pages}

### Erstellen einer neuen Seite {#creating-a-new-page}

Wenn nicht alle Seiten für Sie erstellt wurden, müssen Sie eine Seite erstellen, bevor Sie mit der Erstellung von Inhalten beginnen können:

1. Öffnen Sie die Sites-Konsole (z. B. [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)).
1. Navigieren Sie zu der Position, an der Sie die neue Seite erstellen möchten.
1. Öffnen Sie das Dropdown-Menü über **Erstellen** in der Symbolleiste und wählen Sie in der Liste **Seite** aus:

   ![screen_shot_2018-03-22at104944](assets/screen_shot_2018-03-22at104944.png)

1. Im ersten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Wählen Sie die Vorlage, die Sie zum Erstellen der neuen Seite verwenden möchten, und klicken/tippen Sie auf **Weiter**, um fortzufahren.
   * Mit **Abbrechen** brechen Sie den Vorgang ab.

   ![chlimage_1-8](assets/chlimage_1-8.png)

1. Im letzten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Geben Sie auf den drei Registerkarten die [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) ein, die Sie der neuen Seite zuweisen möchten, und klicken bzw. tippen Sie dann auf **Erstellen**, um die Seite zu erstellen.
   * Verwendung **Zurück** , um zur Vorlagenauswahl zurückzukehren.

   Die Schlüsselfelder sind:

   * **Titel**:

      * Dies wird dem Benutzer angezeigt und ist obligatorisch.
   * **Name**:

      * Mit diesem Wert wird der URI generiert. Wenn kein Name angegeben ist, wird der Name vom Titel abgeleitet.
      * Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, validiert AEM [den Namen entsprechend den Konventionen](/help/sites-developing/naming-conventions.md) von AEM und JCR.
      * You **kann keine ungültigen Zeichen senden** im **Name** -Feld. Wenn AEM ungültige Zeichen erkennt, wird das Feld markiert und eine erklärende Meldung angezeigt, die angibt, welche Zeichen entfernt/ersetzt werden müssen.

   >[!NOTE]
   >
   >Siehe [Seitenbenennungskonventionen](#page-naming-conventions).

   Die zum Erstellen einer neuen Seite mindestens erforderlichen Informationen sind die **Titel**.

   ![chlimage_1-9](assets/chlimage_1-9.png)

1. Verwenden Sie **Erstellen**, um den Vorgang abzuschließen und die neue Seite zu erstellen. Im Bestätigungs-Dialogfeld werden Sie gefragt, ob Sie die Seite sofort **öffnen** oder zur Konsole zurückkehren möchten (**Fertig**):

   ![chlimage_1-10](assets/chlimage_1-10.png)

   >[!NOTE]
   >
   >Wenn Sie eine Seite erstellen und dabei einen in diesem Verzeichnis bereits vorhandenen Namen verwenden, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn beispielsweise `winter` bereits vorhanden ist, wird eine neue Seite `winter0` genannt.

1. Wenn Sie zur Konsole zurückkehren, wird die neue Seite angezeigt:

   ![screen_shot_2018-03-22at105321](assets/screen_shot_2018-03-22at105321.png)

>[!CAUTION]
>
>Nachdem eine Seite erstellt wurde, kann ihre Vorlage nicht mehr geändert werden - es sei denn, Sie [erstellen einen Launch mit einer neuen Vorlage](/help/sites-authoring/launches-creating.md#create-launch-with-new-template), wobei aber der gesamte bereits vorhandene Inhalt verloren geht.

### Öffnen einer Seite zur Bearbeitung {#opening-a-page-for-editing}

Nachdem Sie eine Seite erstellt haben oder zu einer vorhandenen Seite (in der Konsole) navigiert sind, können Sie sie zur Bearbeitung öffnen:

1. Öffnen Sie die **Sites** Konsole.
1. Navigieren Sie zu der Seite, die Sie bearbeiten möchten.
1. Wählen Sie Ihre Seite mit einer der folgenden Methoden aus:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#product-navigation) und Symbolleiste

   Wählen Sie anschließend das Symbol **Bearbeiten** aus:

   ![screen_shot_2018-03-22at105355](assets/screen_shot_2018-03-22at105355.png)

1. Die Seite wird geöffnet und Sie können [die Seite bearbeiten](/help/sites-authoring/editing-content.md).

>[!NOTE]
>
>Das Navigieren zu anderen Seiten ist im Seiteneditor nur im Vorschaumodus möglich, da Links im Bearbeitungsmodus des Seiteneditors nicht aktiv sind.

### Kopieren und Einfügen einer Seite {#copying-and-pasting-a-page}

Sie können eine Seite und alle zugehörigen Unterseiten an einen neuen Speicherort kopieren:

1. Im **Sites** -Konsole, navigieren Sie zu der Seite, die Sie kopieren möchten.
1. Wählen Sie Ihre Seite mit einer der folgenden Optionen aus:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#product-navigation) und Symbolleiste

   Und dann **Kopieren** Seitensymbol:

   ![screen_shot_2018-03-22at105425](assets/screen_shot_2018-03-22at105425.png)

   >[!NOTE]
   >
   >Wenn Sie sich im Auswahlmodus befinden, wird dies automatisch beendet, sobald die Seite kopiert wird.

1. Navigieren Sie zum Speicherort, an dem Sie die neue Kopie der Seite speichern möchten.
1. Verwenden Sie die **Einfügen** Seitensymbol:

   ![screen_shot_2018-03-22at105510](assets/screen_shot_2018-03-22at105510.png)

   An dieser Stelle wird eine Kopie der Originalseite und aller Unterseiten erstellt.

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort kopieren, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn `winter` beispielsweise bereits existiert, wird `winter` zu `winter1`.

### Verschieben oder Umbenennen einer Seite {#moving-or-renaming-a-page}

>[!NOTE]
>
>Das Umbenennen einer Seite unterliegt auch dem [Seitenbenennungskonventionen](#page-naming-conventions) beim Angeben des neuen Seitennamens.

>[!NOTE]
>
>Eine Seite kann nur an einen Ort verschoben werden, an dem die Vorlage, auf der die Seite basiert, zulässig ist. Weitere Informationen finden Sie unter [Formularverfügbarkeit](/help/sites-developing/templates.md#template-availability).

Die Vorgehensweise zum Verschieben oder Umbenennen einer Seite ist im Wesentlichen identisch und wird vom selben Assistenten verarbeitet. Dieser Assistent hilft Ihnen bei den folgenden Aktionen:

* Umbenennen einer Seite, ohne sie zu verschieben.
* Verschieben der Seite, ohne sie umzubenennen.
* Verschieben und gleichzeitiges Umbenennen der Seite.

AEM bietet die Möglichkeit, interne Links zu aktualisieren, die auf die Seite verweisen, die umbenannt/verschoben wird. Dies kann seitenweise erfolgen, um volle Flexibilität zu bieten.

1. Navigieren Sie zu der Seite, die Sie verschieben möchten.
1. Wählen Sie Ihre Seite mit einer der folgenden Optionen aus:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#product-navigation) und Symbolleiste

   Wählen Sie anschließend die **Verschieben** Seitensymbol:

   ![screen_shot_2018-03-22at105534](assets/screen_shot_2018-03-22at105534.png)

   Dadurch wird der Assistent zum Verschieben von Seiten geöffnet.

1. Aus dem **Umbenennen** Schritt des Assistenten können Sie entweder:

   * Geben Sie den Namen an, den die Seite nach dem Verschieben aufweisen soll, und tippen/klicken Sie dann auf **Weiter**, um den Vorgang fortzusetzen.
   * Mit **Abbrechen** brechen Sie den Vorgang ab.

   ![chlimage_1-11](assets/chlimage_1-11.png)

   Der Seitenname kann unverändert bleiben, wenn Sie nur die Seite verschieben.

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort verschieben, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn `winter` beispielsweise bereits existiert, wird `winter` zu `winter1`.

1. Aus dem **Ziel auswählen** Schritt des Assistenten können Sie entweder:

   * Verwenden Sie die [Spaltenansicht](/help/sites-authoring/basic-handling.md#column-view) , um zum neuen Speicherort für die Seite zu navigieren:

      * Wählen Sie das Ziel für die Seite aus, indem Sie auf die Miniatur des Ziels klicken.
      * Klicken Sie auf **Weiter**, um fortzufahren.
   * Verwendung **Zurück** , um zur Seitennamenspezifikation zurückzukehren.

   ![chlimage_1-12](assets/chlimage_1-12.png)

   >[!NOTE]
   >
   >Wenn Sie die Seite an einen Speicherort verschieben, an dem sich bereits eine Seite befindet, deren Name mit dem der ursprünglichen Seite übereinstimmt, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn `winter` beispielsweise bereits existiert, wird `winter` zu `winter1`.

1. Wenn die Seite verknüpft ist oder darauf verwiesen wird, werden diese Verweise im **Anpassen/Erneutes Veröffentlichen** Schritt. Sie können angeben, welche Änderungen ggf. angepasst und neu veröffentlicht werden sollen.

   ![chlimage_1-13](assets/chlimage_1-13.png)

1. Auswählen **Verschieben** schließt den Prozess ab und verschiebt/umbenennt Ihre Seite nach Bedarf.

>[!NOTE]
>
>Wenn die Seite bereits veröffentlicht wurde, wird das Veröffentlichen durch Verschieben der Seite automatisch rückgängig gemacht. Standardmäßig wird sie nach Abschluss des Verschiebevorgangs erneut veröffentlicht. Dies kann sich jedoch ändern, indem Sie die **Neu veröffentlichen** im Feld **Anpassen/Erneutes Veröffentlichen** Schritt.

>[!NOTE]
>
>Wenn es keine Verweise auf die Seite gibt, wird der Schritt **Anpassen/Erneut veröffentlichen** übersprungen.

### Löschen einer Seite {#deleting-a-page}

1. Navigieren Sie zu der Seite, die Sie löschen möchten.
1. Wählen Sie mit dem [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) die gewünschte Seite aus, bevor Sie in der Symbolleiste die Option **Löschen** auswählen:

   ![screen_shot_2018-03-22at105622](assets/screen_shot_2018-03-22at105622.png)

   >[!NOTE]
   >
   >Als Sicherheitsmaßnahme ist das Symbol **Löschen** nicht per Schnellzugriff verfügbar.

1. Ein Bestätigungsdialogfeld wird angezeigt.

   * **Möchten Sie Seiten vor dem Löschen archivieren?** – Wenn diese Option aktiviert ist, werden beim Löschen Versionen der zu löschenden Seiten erstellt.
      * [Versionen können zu einem späteren Zeitpunkt wiederhergestellt werden.](/help/sites-authoring/working-with-page-versions.md)
      * Seiten, die ohne vorherige Versionen gelöscht wurden, können nicht wiederhergestellt werden.
      * Diese Option ist nur ab AEM Version 6.4.7.0 verfügbar.
   * **Abbrechen** , um die Aktion abzubrechen
   * Mit **Löschen** bestätigen Sie die Aktion.

      * Wenn die Seite keine Verweise enthält, wird die Seite gelöscht.
      * Wenn die Seite Verweise enthält, werden Sie in einem Meldungsfeld darauf hingewiesen, dass **eine oder mehrere Seiten über einen Verweis verfügen**. Sie können **Löschen erzwingen** oder **Abbrechen** auswählen.

>[!NOTE]
>
>Wenn eine Seite bereits veröffentlicht wurde, wird sie vor dem Löschen automatisch depubliziert.

### Sperren einer Seite {#locking-a-page}

Sie können entweder in einer Konsole oder beim Bearbeiten einer Seite eine [Seite sperren/entsperren](/help/sites-authoring/editing-content.md#locking-a-page). Informationen darüber, ob eine Seite gesperrt ist, werden auch an beiden Stellen angezeigt.

![screen_shot_2018-03-22at105713](assets/screen_shot_2018-03-22at105713.png) ![screen_shot_2018-03-22at105720](assets/screen_shot_2018-03-22at105720.png)

### Erstellen eines neuen Ordners {#creating-a-new-folder}

Sie können Ordner erstellen, um Ihre Dateien und Seiten zu organisieren.

>[!NOTE]
>
>Ordner unterliegen auch dem [Seitenbenennungskonventionen](#page-naming-conventions) beim Angeben des neuen Ordnernamen.

>[!CAUTION]
>
>* Ordner können nur direkt unter **Sites** oder unter anderen Ordnern. Sie können nicht unter einer Seite erstellt werden.
>* Für einen Ordner können folgende Standardaktionen ausgeführt werden: Verschieben, Kopieren, Einfügen, Löschen, Veröffentlichen, Rückgängigmachen der Veröffentlichung und Anzeigen/Bearbeiten von Eigenschaften.
>* Ordner sind in einer Live Copy nicht als Auswahl verfügbar.
>


1. Öffnen Sie die **Sites** und navigieren Sie zum gewünschten Speicherort.
1. Um die Optionsliste zu öffnen, wählen Sie **Erstellen** über die Symbolleiste
1. Auswählen **Ordner** , um das Dialogfeld zu öffnen. Hier können Sie den **Namen** und den **Titel** eingeben:

   ![chlimage_1-14](assets/chlimage_1-14.png)

1. Wählen Sie **Erstellen**, um den Ordner zu erstellen.
