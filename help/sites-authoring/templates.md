---
title: Erstellen von Seitenvorlagen
seo-title: Creating Page Templates
description: Eine Vorlage definiert die Struktur einer erstellten Seite und mit dem Vorlageneditor ist die Erstellung und Verwaltung von Vorlagen nicht mehr nur Entwicklern vorbehalten.
seo-description: The template defines the structure of the resultant page and with the template editor, creating and maintaining templates is no longer a developer-only task
uuid: ffdc760d-9504-4d13-9f74-a58499632b78
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 5a96c306-790a-4721-a146-86fbceb376db
exl-id: 2af8eaed-3963-4016-9efa-a630d16a982b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4820'
ht-degree: 62%

---

# Erstellen von Seitenvorlagen {#creating-page-templates}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Beim Erstellen einer Seite müssen Sie eine Vorlage auswählen, die als Grundlage für die Erstellung der neuen Seite verwendet wird. Die Vorlage definiert die Struktur der resultierenden Seite, den anfänglichen Inhalt und die Komponenten, die verwendet werden können.

Mit dem **Vorlageneditor** ist das Erstellen und Verwalten von Vorlagen nicht mehr nur eine Aufgabe für Entwickler. Auch ein Power User, der als **Vorlagenautor** bezeichnet wird, kann einbezogen werden. Entwickler müssen weiterhin die Umgebung einrichten, Clientbibliotheken erstellen und die zu verwendenden Komponenten erstellen. Sobald diese Grundlagen vorhanden sind, hat der **Vorlagenautor** jedoch die Flexibilität, Vorlagen ohne Entwicklungsprojekt zu erstellen und zu konfigurieren.

Die **Vorlagenkonsole** ermöglicht es Vorlagenautoren,

* eine neue Vorlage erstellen oder eine vorhandene Vorlage kopieren
* Verwalten Sie den Lebenszyklus der Vorlage.

Mit dem **Vorlageneditor** können Vorlagenautoren:

* Fügen Sie Komponenten zur Vorlage hinzu und positionieren Sie sie auf einem responsiven Raster.
* die Komponenten vorkonfigurieren
* Definieren Sie, welche Komponenten auf Seiten bearbeitet werden können, die mit der Vorlage erstellt wurden.

In diesem Dokument wird erklärt, wie ein **Vorlagenautor** die Vorlagenkonsole und den Vorlageneditor verwenden kann, um bearbeitbare Vorlagen zu erstellen und zu verwalten.

Ausführliche Informationen zur Funktionsweise von bearbeitbaren Vorlagen auf technischer Ebene finden Sie im Entwicklerdokument [Seitenvorlagen - bearbeitbar](/help/sites-developing/page-templates-editable.md) für weitere Informationen.

>[!NOTE]
>
>AEM 6.4.5.0 oder höher ist erforderlich, um bearbeitbare Vorlagen mit der [SPA Editor](/help/sites-developing/spa-overview.md).

>[!NOTE]
>
>Der **Vorlageneditor** unterstützt kein Targeting direkt auf Vorlagenstufe. Seiten, die auf Grundlage einer bearbeitbaren Vorlage erstellt wurden, können zielgerichtet sein, die Vorlagen selbst müssen das jedoch nicht sein.

>[!CAUTION]
>
>Die Seiten und Vorlagen, die mit der **Vorlagenkonsole** erstellt wurden, sind nicht zur Verwendung in der klassischen Benutzeroberfläche bestimmt und eine solche Verwendung wird nicht unterstützt.

## Bevor Sie beginnen {#before-you-start}

>[!NOTE]
>
>Ein Admin muss im **Konfigurations-Browser** einen Vorlagenordner konfigurieren und entsprechende Berechtigungen anwenden, bevor ein Vorlagenautor eine Vorlage in diesem Ordner erstellen kann.

Beachten Sie vor dem Start die folgenden Punkte:

* Das Erstellen einer neuen Vorlage erfordert Zusammenarbeit. Aus diesem Grund wird für jede Aufgabe eine [Rolle](#roles) angezeigt.

* Je nachdem, wie Ihre Instanz konfiguriert ist, kann es nützlich sein, sich darüber im Klaren zu sein, dass AEM jetzt [zwei grundlegende Vorlagentypen](/help/sites-authoring/templates.md#editable-and-static-templates). Dies hat keine Auswirkungen auf die tatsächliche [Verwenden einer Vorlage zum Erstellen einer Seite](#using-a-template-to-create-a-page), aber es wirkt sich auf den Typ der Vorlage aus, die Sie erstellen können, und darauf aus, wie eine Seite mit der Vorlage in Beziehung steht.

### Rollen {#roles}

Für das Erstellen einer neuen Vorlage mithilfe der **Vorlagenkonsole** und des **Vorlageneditors** ist eine Zusammenarbeit zwischen folgenden Rollen erforderlich:

* **Admin**:

   * Erstellt neue Ordner für Vorlagen, wofür `admin`-Berechtigungen erforderlich sind.
   * Solche Aufgaben können oft auch von einem Entwickler durchgeführt werden

* **Entwickler**:

   * Konzentriert sich auf die technischen/internen Details
   * Muss Erfahrung mit der Entwicklungsumgebung haben.
   * Versorgt den Vorlagenautor mit den erforderlichen Informationen.

* **Vorlagenautor**:

   * Dies ist ein bestimmter Autor, der Mitglied der Gruppe `template-authors` ist.

      * Weist die erforderlichen Berechtigungen zu.
   * Kann die Verwendung von Komponenten und anderen Details auf hoher Ebene konfigurieren, was Folgendes erfordert:

      * Einige technische Kenntnisse

         * Verwenden Sie beispielsweise Muster beim Definieren von Pfaden.
      * Technische Informationen vom Entwickler.



Aufgrund der Art einiger Aufgaben wie der Erstellung eines Ordners ist eine Entwicklungsumgebung erforderlich, die Wissen/Erfahrung erfordert.

Die in diesem Dokument beschriebenen Aufgaben werden mit der Rolle aufgelistet, die für ihre Durchführung verantwortlich ist.

### Bearbeitbare und statische Vorlagen {#editable-and-static-templates}

AEM bietet nun zwei grundlegende Arten von Vorlagen:

* Bearbeitbare Vorlagen

   * Können von Vorlagenautoren [erstellt](#creating-a-new-template-template-author) und [bearbeitet](#editing-templates-template-authors) werden, indem die **Vorlagenkonsole und der Vorlagen-Editor** verwendet werden. Auf die **Vorlagenkonsole** kann im Bereich **Allgemein** der Konsole **Werkzeuge** zugegriffen werden.
   * Nachdem die neue Seite erstellt wurde, wird eine dynamische Verbindung zwischen der Seite und der Vorlage aufrechterhalten. Das bedeutet, dass Änderungen an der Vorlagenstruktur und/oder an gesperrten Inhalten auf allen Seiten übernommen werden, die mit dieser Vorlage erstellt werden. Änderungen am entsperrten (d. h. anfänglichen) Inhalt werden nicht übernommen.
   * Verwenden Sie die Inhaltsrichtlinien, die Sie im Vorlagen-Editor definieren können, um die Designeigenschaften beizubehalten. Der Designmodus im Seiteneditor wird nicht mehr für bearbeitbare Vorlagen verwendet.

* Statische Vorlagen

   * Statische Vorlagen sind bereits seit längerem für diverse Versionen von AEM verfügbar.
   * Sie werden [von Ihren Entwicklern bereitgestellt](/help/sites-developing/page-templates-static.md) und können somit nicht von Autoren erstellt oder bearbeitet werden.
   * Sie werden kopiert, um die neue Seite zu erstellen, wobei danach keine dynamische Verbindung besteht (obwohl der Name der Vorlage zu Informationszwecken registriert ist).
   * Verwenden Sie den [Designmodus](/help/sites-authoring/default-components-designmode.md), um Designeigenschaften beizubehalten.
   * Da die Bearbeitung von statischen Vorlagen ausschließlich von einem Entwickler durchgeführt wird, lesen Sie das Entwicklerdokument [Statische Seitenvorlagen](/help/sites-developing/page-templates-static.md), um weitere Informationen zu erhalten.

Die Vorlagenkonsole und der Vorlagen-Editor ermöglichen standardmäßig nur die Erstellung und Bearbeitung bearbeitbarer Vorlagen. Deshalb konzentriert sich dieses Dokument ausschließlich auf bearbeitbare Vorlagen.

### Verwenden einer Vorlage zum Erstellen einer Seite {#using-a-template-to-create-a-page}

Bei Verwendung einer Vorlage für [eine neue Seite erstellen](/help/sites-authoring/managing-pages.md#creating-a-new-page) Es gibt keinen sichtbaren Unterschied und keinen Hinweis zwischen statischen und bearbeitbaren Vorlagen. Für die Seitenautoren ist der Prozess transparent.

## Erstellen und Verwalten von Vorlagen {#creating-and-managing-templates}

Gehen Sie zum Erstellen einer neuen bearbeitbaren Vorlage wie folgt vor:

* Verwenden Sie die **Vorlagenkonsole**, die im Bereich **Allgemein** der Konsole **Tools** verfügbar ist.

   * Oder direkt unter: [http://localhost:4502/libs/wcm/core/content/sites/templates.html/conf](http://localhost:4502/libs/wcm/core/content/sites/templates.html/conf)

* Erstellen Sie bei Bedarf [einen Ordner für die Vorlagen](#creating-a-template-folder-admin).
* [Erstellen Sie eine neue Vorlage](#creating-a-new-template-template-author), die anfangs leer ist.

* [Zusätzliche Eigenschaften definieren](#defining-template-properties-template-author) für die Vorlage, falls erforderlich
* [Vorlage bearbeiten](#editing-templates-template-authors) um Folgendes zu definieren:

   * [Struktur](#editing-a-template-structure-template-author) – vordefinierter Inhalt, der auf Seiten, die mit der Vorlage erstellt werden, nicht geändert werden kann.
   * [Anfänglicher Inhalt](#editing-a-template-initial-content-author) – vordefinierter Inhalt, der auf den Seiten geändert werden kann, die mit der Vorlage erstellt werden.
   * [Layout](#editing-a-template-layout-template-author) – für eine Vielzahl von Geräten.
   * [Stile](/help/sites-authoring/style-system.md) – zum Definieren der Stile für die Vorlage und ihre Komponenten.

* [Vorlage aktivieren](#enabling-a-template-template-author) zur Verwendung beim Erstellen einer Seite
* [Vorlage zulassen](#allowing-a-template-author) für die gewünschte Seite oder den Zweig Ihrer Website
* [Vorlage veröffentlichen](#publishing-a-template-template-author) , um sie in der Veröffentlichungsumgebung verfügbar zu machen

>[!NOTE]
>
>Die **zugelassenen Vorlagen** werden häufig vordefiniert, wenn Sie Ihre Website erstmals einrichten.

>[!CAUTION]
>
>Geben Sie in eine Vorlage nie Informationen ein, die [internationalisiert](/help/sites-developing/i18n.md) werden müssen.

### Erstellen eines Vorlagenordners – Administrator {#creating-a-template-folder-admin}

Für Ihr Projekt sollte ein Vorlagenordner für Ihre projektspezifischen Vorlagen erstellt werden. Dies ist eine Administratoraufgabe, die im Dokument beschrieben wird. [Seitenvorlagen - bearbeitbar](/help/sites-developing/page-templates-editable.md#template-folders).

### Erstellen einer neuen Vorlage – Vorlagenautor {#creating-a-new-template-template-author}

1. Öffnen Sie die **Vorlagenkonsole** (via **Instrumente** -> **Allgemein**) und navigieren Sie dann zum gewünschten Ordner.

   >[!NOTE]
   >
   >In einer Standard-AEM-Instanz ist der Ordner **Global** bereits in der Vorlagenkonsole vorhanden. Er enthält Standardvorlagen und dient als Ausweichlösung, wenn keine Richtlinien und/oder Vorlagentypen im aktuellen Ordner gefunden werden.
   >
   >Es wird empfohlen, eine [Vorlagenordner, der für Ihr Projekt erstellt wurde](/help/sites-developing/page-templates-editable.md#template-folders).

1. Wählen Sie **Erstellen** und anschließend **Vorlage erstellen**, um den Assistenten zu öffnen.

1. Auswählen einer **Vorlagentyp**, wählen Sie **Nächste**.

   >[!NOTE]
   >
   >Vorlagenarten sind vordefinierte Vorlagen, die als Vorlagen für eine Vorlage betrachtet werden können. Diese werden von Entwicklern oder dem Systemadministrator vordefiniert. Weitere Informationen finden Sie im Entwicklerdokument [Seitenvorlagen - bearbeitbar](/help/sites-developing/page-templates-editable.md#template-type).

1. Führen Sie die **Vorlagendetails**:

   * **Vorlagenname**
   * **Beschreibung**

1. Wählen Sie **Erstellen**. Eine Bestätigung wird angezeigt. Wählen Sie **Öffnen**, um die [Vorlage zu bearbeiten](#editing-templates-template-authors) oder **Fertig**, um zur Vorlagenkonsole zurückzukehren.

   >[!NOTE]
   >
   >Wenn eine neue Vorlage erstellt wird, wird sie in der Konsole als **Entwurf** markiert, was bedeutet, dass sie noch nicht für Seitenautoren zur Verfügung steht.

### Definieren von Vorlageneigenschaften – Vorlagenautor  {#defining-template-properties-template-author}

Eine Vorlage kann die folgenden Eigenschaften aufweisen:

* Bild

   * Bild, das als [Miniatur der Vorlage verwendet wird](/help/sites-authoring/templates.md#template-thumbnail-image), um die Auswahl zu vereinfachen, beispielsweise im Seitenerstellungsassistenten.

      * Kann hochgeladen werden
      * Kann basierend auf dem Vorlageninhalt generiert werden

* Titel

   * Ein Titel, der zur Identifizierung der Vorlage verwendet wird, z. B. im **Seite erstellen** Assistent.

* Beschreibung

   * Eine optionale Beschreibung, die weitere Informationen über die Vorlage und ihre Verwendung bereitstellt, die beispielsweise im **Seite erstellen** Assistent.

So zeigen Sie die Eigenschaften an bzw. bearbeiten sie:

1. Wählen Sie in der **Vorlagenkonsole** eine Vorlage aus.
1. Wählen Sie **Eigenschaften anzeigen** in der Symbolleiste oder in den Schnelloptionen aus, um das Dialogfeld zu öffnen.
1. Jetzt können Sie die Vorlageneigenschaften anzeigen oder bearbeiten.

>[!NOTE]
>
>Der Status einer Vorlage („Entwurf“, „Aktiviert“ oder „Deaktiviert“) wird in der Konsole angezeigt.

#### Vorlagenminiaturbild {#template-thumbnail-image}

So definieren Sie die Vorlagenminiatur:

1. Bearbeiten Sie die Vorlageneigenschaften.
1. Wählen Sie aus, ob Sie eine Miniaturansicht hochladen oder aus dem Vorlageninhalt generieren lassen möchten.

   * Wenn Sie eine Miniaturansicht hochladen möchten, klicken oder tippen Sie auf **Bild hochladen**
   * Wenn Sie eine Miniatur erzeugen möchten, klicken oder tippen Sie auf **Vorschau generieren**

1. Für beide Methoden wird eine Vorschau der Miniaturansicht angezeigt.

   Wenn sie nicht zufriedenstellend ist, klicken oder tippen Sie auf **Löschen** , um ein anderes Bild hochzuladen oder die Miniaturansicht neu zu generieren.

1. Wenn Sie mit der Miniaturansicht zufrieden sind, klicken oder tippen Sie auf **Speichern und schließen**.

### Aktivieren und Zulassen einer Vorlage – Vorlagenautor {#enabling-and-allowing-a-template-template-author}

Um beim Erstellen einer Seite eine Vorlage zu verwenden, gehen Sie wie folgt vor:

* [Aktivieren Sie die Vorlage](#enabling-a-template-template-author), um sie verfügbar zu machen, wenn Seiten erstellt werden.
* [Lassen Sie die Vorlage zu](#allowing-a-template-author), um die Inhaltsverzweigungen anzugeben, in denen die Vorlage verwendet werden kann.

#### Aktivieren einer Vorlage – Vorlagenautor {#enabling-a-template-template-author}

Eine Vorlage kann aktiviert oder deaktiviert werden, um sie im **Seite erstellen** Assistent.

>[!CAUTION]
>
>Sobald eine Vorlage aktiviert ist, wird eine Warnung angezeigt, wenn ein Vorlagenautor beginnt, die Vorlage weiter zu aktualisieren. Diese dient dazu, den Benutzer zu informieren, dass die Vorlage referenziert wird und damit sämtliche Änderungen, die die Vorlage referenzierenden Seiten beeinträchtigen könnten.

1. Wählen Sie in der **Vorlagenkonsole** eine Vorlage aus.
1. Wählen Sie in der Symbolleiste die Option **Aktivieren** oder **Deaktivieren** und bestätigen Sie Ihre Wahl im Bestätigungsdialogfeld.
1. Jetzt können Sie Ihre Vorlage verwenden, wenn Sie [eine neue Seite erstellen](/help/sites-authoring/managing-pages.md#creating-a-new-page), bzw. [die Vorlage bearbeiten](#editing-templates-template-authors), um sie an Ihre Anforderungen anzupassen.

>[!NOTE]
>
>Der Status einer Vorlage („Entwurf“, „Aktiviert“ oder „Deaktiviert“) wird in der Konsole angezeigt.

#### Zulassen einer Vorlage – Autor {#allowing-a-template-author}

Eine Vorlage kann für bestimmte Seitenverzweigungen verfügbar oder nicht verfügbar gemacht werden.

1. Öffnen Sie die [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) für die Stammseite der Verzweigung, in der die Vorlage verfügbar sein soll.

1. Öffnen Sie die Registerkarte **Erweitert**.

1. Klicken Sie unter **Vorlageneinstellungen** auf **Feld hinzufügen**, um den Pfad/die Pfade zu Ihren Vorlagen anzugeben.

   Der Pfad kann explizit sein oder Muster verwenden. Ein Beispiel:

   `/conf/<your-folder>/settings/wcm/templates/.*`

   Die Reihenfolge der Pfade ist irrelevant, alle Pfade werden geprüft und alle Vorlagen werden abgerufen.

   >[!NOTE]
   >
   >Wenn die Variable **Zulässige Vorlagen** leer ist, wird der Baum aufgerissen, bis ein Wert/eine Liste gefunden wird.
   >
   >Weitere Informationen finden Sie unter [Vorlagenverfügbarkeit](/help/sites-developing/templates.md#template-availability) – die Prinzipien für zugelassene Vorlagen bleiben gleich.

1. Klicken Sie auf **Speichern**, um die Änderungen an den Seiteneigenschaften zu speichern.

>[!NOTE]
>
>Häufig werden die zugelassenen Vorlagen für Ihre gesamte Site vordefiniert, wenn diese eingerichtet wird.

### Veröffentlichen einer Vorlage – Vorlagenautor {#publishing-a-template-template-author}

Da auf die Vorlage verwiesen wird, wenn eine Seite dargestellt wird, muss die voll konfigurierte Vorlage veröffentlicht werden, damit sie in der Veröffentlichungsumgebung verfügbar ist.

1. Wählen Sie in der **Vorlagenkonsole** eine Vorlage aus.
1. Wählen Sie **Veröffentlichen** in der Symbolleiste, um den Assistenten zu öffnen.
1. Wählen Sie die **Inhaltsrichtlinien**, die mit veröffentlicht werden sollen.

1. Wählen Sie **Veröffentlichen** in der Symbolleiste, um den Vorgang abzuschließen.

## Bearbeiten von Vorlagen   – Vorlagenautoren {#editing-templates-template-authors}

Beim Erstellen oder Bearbeiten einer Vorlage können verschiedene Aspekte definiert werden. Das Bearbeiten von Vorlagen ähnelt dem Bearbeiten von Seiten.

Die folgenden Aspekte einer Vorlage können bearbeitet werden:

* [Struktur](#editing-a-template-structure-template-author)

   Komponenten, die hier hinzugefügt werden, können von den Seitenautoren nicht von den resultierenden Seiten verschoben/entfernt werden. Wenn Seitenautoren in der Lage sein sollen, neue Komponenten zu resultierenden Seiten hinzuzufügen und daraus zu entfernen, müssen Sie der Vorlage ein Absatzsystem hinzufügen.

   Wenn Komponenten gesperrt sind, können Sie Inhalte hinzufügen, die von Seitenautoren nicht bearbeitet werden können. Sie können Komponenten entsperren, damit Sie [Anfänglicher Inhalt](#editing-a-template-initial-content-author).

   >[!NOTE]
   >
   >Im Strukturmodus können Komponenten, die einer entsperrten Komponente übergeordnet sind, nicht verschoben, ausgeschnitten oder gelöscht werden.

* [Anfänglicher Inhalt](#editing-a-template-initial-content-author)

   Wenn eine Komponente entsperrt wurde, können Sie den anfänglichen Inhalt definieren, der auf die resultierenden Seiten kopiert wird, die aus der Vorlage erstellt werden. Diese entsperrten Komponenten können auf den resultierenden Seiten bearbeitet werden.

   >[!NOTE]
   >
   >Im Modus **Anfänglicher Inhalt** und auf den resultierenden Seiten können alle entsperrten Komponenten, bei denen übergeordnete Elemente verfügbar sind (z. B. Komponenten in einem Layout-Container), gelöscht werden.

* [Layout](#editing-a-template-layout-template-author)

   Hier können Sie das Vorlagenlayout für die erforderlichen Geräteformate vordefinieren. Der Modus **Layout** für das Erstellen von Vorlagen bietet dieselben Funktionen wie der Modus **[Layout](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)** für das Erstellen von Seiten.

* [Seitenrichtlinien](#editing-a-template-structure-template-author)

   Unter „Seitenrichtlinien“ können Sie vordefinierte Seitenrichtlinien für die Seite verknüpfen. Diese Seitenrichtlinien definieren die verschiedenen Design-Konfigurationen.

* [Stile](/help/sites-authoring/style-system.md)

   Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.

   Weitere Informationen finden Sie in der [Dokumentation für das Stilsystem](/help/sites-authoring/style-system.md).

Mit der **Modus**-Auswahl in der Symbolleiste können Sie die jeweiligen Aspekte der Vorlage auswählen und bearbeiten:

* [Struktur](#editing-a-template-structure-template-author)
* [Anfänglicher Inhalt](#editing-a-template-initial-content-author)
* [Layout](#editing-a-template-layout-template-author)

![chlimage_1-363](assets/chlimage_1-363.png)

Mit der Option **Seitenrichtlinie** im Menü **Seiteninformationen** können Sie [die erforderlichen Seitenrichtlinien auswählen](#editing-a-template-structure-template-author):

![screen_shot_2018-03-23at120604](assets/screen_shot_2018-03-23at120604.png)

>[!CAUTION]
>
>Wenn ein Autor beginnt, eine bereits aktivierte Vorlage zu bearbeiten, wird eine Warnung angezeigt. Diese dient dazu, den Benutzer zu informieren, dass die Vorlage referenziert wird und damit sämtliche Änderungen, die die Vorlage referenzierenden Seiten beeinträchtigen könnten.

### Bearbeiten einer Vorlage – Struktur – Vorlagenautor {#editing-a-template-structure-template-author}

In **Struktur** -Modus definieren Sie Komponenten und Inhalte für Ihre Vorlage und definieren Sie Richtlinien für die Vorlage und ihre Komponenten.

* Komponenten, die in der Vorlagenstruktur definiert sind, können nicht auf einer resultierenden Seite verschoben oder von den resultierenden Seiten gelöscht werden.
* Wenn Seitenautoren Komponenten hinzufügen und entfernen können sollen, fügen Sie der Vorlage ein Absatzsystem hinzu.
* Komponenten lassen sich entsperren und erneut sperren, damit Sie den [anfänglichen Inhalt](#editing-a-template-initial-content-author) definieren können.

* Die Design-Richtlinien für die Komponenten und die Seite werden definiert.

![screen_shot_2018-03-23at120819](assets/screen_shot_2018-03-23at120819.png)

In **Struktur** Modus des Vorlageneditors:

* **Komponenten hinzufügen**

   Es gibt mehrere Möglichkeiten, Komponenten zur Vorlage hinzuzufügen:

   * Aus dem **Komponenten** im Seitenbereich.
   * über die Option **Komponente einfügen** (**Plussymbol**) in der Symbolleiste von Komponenten, die bereits in der Vorlage sind, oder dem Feld **Kompenenten hierher ziehen**
   * Durch Ziehen eines Assets (aus dem **Assets** -Browser im Seitenbereich) direkt auf die Vorlage klicken, um die entsprechende Komponente vor Ort zu generieren.

   Nach dem Hinzufügen wird jede Komponente mit folgenden Elementen markiert:

   * Rahmen
   * Eine Markierung, die den Komponententyp anzeigt
   * Eine Markierung, die anzeigt, wann die Komponente entsperrt wurde

   >[!NOTE]
   >
   >Wenn Sie eine vordefinierte **Titelkomponente** zur Vorlage hinzufügen, enthält sie den Standardtext **Struktur**.
   >
   >
   >Wenn Sie diesen ändern und Ihren eigenen Text einfügen, wird dieser aktualisierte Text verwendet, wenn eine Seite aus der Vorlage erstellt wird.
   >
   >
   >Wenn Sie den Standardtext (Struktur) nicht ändern, wird der Titel standardmäßig mit dem Namen der nachfolgenden Seite benannt.

   >[!NOTE]
   >
   >Das Hinzufügen von Komponenten und Assets zu einer Vorlage ist zwar nicht identisch, ähnelt jedoch in vielen Fällen ähnlichen Aktionen, wenn [Seitenbearbeitung](/help/sites-authoring/editing-content.md).

* **Komponenten-Aktionen**

   Nehmen Sie Aktionen für die Komponenten vor, nachdem sie der Vorlage hinzugefügt wurden. Jede einzelne Instanz verfügt über eine Symbolleiste, über die Sie auf die verfügbaren Aktionen zugreifen können. Die Symbolleiste hängt vom Komponententyp ab.

   ![screen_shot_2018-03-23at120909](assets/screen_shot_2018-03-23at120909.png)

   Sie kann auch von durchgeführten Aktionen abhängig sein. Wenn z. B. eine Richtlinie mit der Komponente verbunden wurde, ist das Design-Konfigurationssymbol verfügbar.

* **Bearbeiten und Konfigurieren**

   Mit diesen zwei Aktionen können Sie Inhalte zu Ihren Komponenten hinzufügen.

* **Rand für die Anzeige der Struktur**

   Bei der Arbeit in **Struktur** -Modus zeigt ein orangefarbener Rahmen die aktuell ausgewählte Komponente an. Eine gepunktete Linie zeigt auch die übergeordnete Komponente an.

   Im Screenshot weiter unten ist beispielsweise die Komponente **Text** in einem **Layout-Container** ausgewählt (responsivegrid).

   ![chlimage_1-364](assets/chlimage_1-364.png)

* **Richtlinien und Eigenschaften (Allgemein)**

   Die Inhalts- (oder Design-)Richtlinien definieren die Designeigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

   Erstellen Sie für eine Komponente eine Inhaltsrichtlinie oder wählen Sie eine vorhandene. Damit können Sie die Design-Details definieren.

   ![chlimage_1-365](assets/chlimage_1-365.png) ![chlimage_1-366](assets/chlimage_1-366.png)

   Das Konfigurationsfenster ist in zwei Hälften geteilt.

   * Auf der linken Seite des Dialogfelds können Sie unter **Richtlinie** eine vorhandene Richtlinie auswählen.
   * Auf der rechten Seite des Dialogfelds können Sie unter **Eigenschaften** die für den Komponententyp spezifischen Eigenschaften festlegen.

   Die verfügbaren Eigenschaften hängen von der ausgewählten Komponente ab. Beispielsweise definieren die Eigenschaften für eine Textkomponente die Optionen zum Kopieren und Einfügen, Formatierungsoptionen und den Absatzstil.

   ***Richtlinie***

   Die Inhalts- (oder Design-)Richtlinien definieren die Designeigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

   Unter **Richtlinie** können Sie eine vorhandene Richtlinie auswählen, die über das Dropdown-Menü auf die Komponente angewendet wird.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   Sie können eine neue Richtlinie hinzufügen, indem Sie auf die Schaltfläche „Hinzufügen“ klicken, die sich neben dem Dropdown-Menü **Richtlinie auswählen** befindet. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden.

   ![chlimage_1-368](assets/chlimage_1-368.png)

   Die im Dropdown-Menü **Richtlinie auswählen** ausgewählte vorhandene Richtlinie kann mithilfe der Schaltfläche „Kopieren“, die sich neben dem Dropdown-Menü befindet, kopiert werden. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden. Standardmäßig erhält die kopierte Richtlinie den Namen **Kopie von X**, wobei X der Name der kopierten Richtlinie ist.

   ![chlimage_1-369](assets/chlimage_1-369.png)

   Eine Beschreibung der Richtlinie im Feld **Richtlinienbeschreibung** ist optional.

   Im Abschnitt **Andere Vorlagen, die ebenfalls die ausgewählte Richtlinie verwenden** ist leicht ersichtlich, welche anderen Vorlagen die Richtlinie verwenden, die in der Dropdown-Liste **Richtlinie auswählen** ausgewählt wurde.

   ![chlimage_1-370](assets/chlimage_1-370.png)

   >[!NOTE]
   >
   >Wenn mehrere Komponenten des gleichen Typs als anfänglicher Inhalt hinzugefügt werden, gilt für alle Komponenten dieselbe Richtlinie. Dies entspricht der Einschränkung für statische Vorlagen im **[Designmodus](/help/sites-authoring/default-components-designmode.md)**.

   ***Eigenschaften***

   Unter dem **Eigenschaften** -Überschrift können Sie die Einstellungen der Komponente definieren. Die Überschrift hat zwei Registerkarten:

   * Allgemein
   * Funktionen

   *Allgemein*

   Auf der Registerkarte **Allgemein** sind die wichtigsten Einstellungen der Komponente definiert.

   Beispielsweise können für eine Bildkomponente die zulässigen Breiten definiert werden, zusammen mit der Aktivierung von verzögertem Laden.

   Wenn eine Einstellung mehrere Konfigurationen zulässt, klicken oder tippen Sie auf die **Hinzufügen** -Schaltfläche, um eine weitere Konfiguration hinzuzufügen.

   ![chlimage_1-371](assets/chlimage_1-371.png)

   Um eine Konfiguration zu entfernen, klicken oder tippen Sie auf die Schaltfläche **Löschen**, die sich rechts neben der Konfiguration befindet.

   Um eine Konfiguration zu entfernen, klicken oder tippen Sie auf die Schaltfläche **Löschen**.

   ![chlimage_1-372](assets/chlimage_1-372.png)

   *Funktionen*

   Die **Funktionen** -Tab können Sie zusätzliche Funktionen der Komponente aktivieren oder deaktivieren.

   Beispielsweise können Sie für eine Bildkomponente die Zuschneideproportionen und zulässigen Bildausrichtungen definieren und festlegen, ob Uploads zulässig sind.

   ![chlimage_1-373](assets/chlimage_1-373.png)

   >[!CAUTION]
   >
   >Beachten Sie, dass in AEM die Beschneidungsverhältnisse als **Höhe/Breite** definiert sind. Dies unterscheidet sich von der herkömmlichen Definition der Breite/Höhe und ist auf Kompatibilität mit Altsystemen zurückzuführen. Benutzer, die Seiten erstellen, bemerken keinen Unterschied, vorausgesetzt, dass Sie den **Namen** klar definieren, da dieser auf der Benutzeroberfläche angezeigt wird.

   >[!NOTE]
   >
   >[Inhaltsrichtlinien für Komponenten, die den Rich-Text-Editor implementieren](/help/sites-administering/rich-text-editor.md), können nur für Optionen definiert werden, die vom RTE über die UI-Einstellungen bereitgestellt werden.  

* **Richtlinien und Eigenschaften (Layout-Container)**

   Die Richtlinien- und Eigenschafteneinstellungen eines Layout-Containers ähneln der allgemeinen Verwendung, allerdings mit einigen Unterschieden.

   >[!NOTE]
   >
   >Die Konfiguration einer Richtlinie ist für Container-Komponenten obligatorisch, da sie es Ihnen ermöglicht, Komponenten zu definieren, die im Container verfügbar sein werden.

   Das Konfigurationsfenster ist in zwei Bereiche unterteilt, genau wie in der allgemeinen Nutzung des Fensters.

   ***Richtlinie***

   Die Inhalts- (oder Design-)Richtlinien definieren die Designeigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

   Unter **Richtlinie** können Sie eine vorhandene Richtlinie auswählen, die über das Dropdown-Menü auf die Komponente angewendet wird. Dies funktioniert ebenso wie bei der allgemeinen Verwendung des Fensters.

   ***Eigenschaften***

   Unter dem **Eigenschaften** -Überschrift können Sie auswählen, welche Komponenten für den Layout-Container verfügbar sind, und ihre Einstellungen definieren. Die Überschrift hat drei Registerkarten:

   * Zugelassene Komponenten
   * Standardkomponenten
   * Responsive Einstellungen

   *Zugelassene Komponenten*

   Im **Zugelassene Komponenten** definieren, legen Sie fest, welche Komponenten für den Layout-Container verfügbar sind.

   * Die Komponenten werden nach Komponentengruppen gruppiert, die sich erweitern und reduzieren lassen.
   * Es kann eine ganze Gruppe ausgewählt werden, indem der Gruppenname überprüft wird. Die Auswahl aller Gruppen kann durch Deaktivieren der Option aufgehoben werden.
   * Ein Minuszeichen steht für mindestens ein Element, es werden jedoch nicht alle Elemente einer Gruppe ausgewählt.
   * Es ist eine Suche verfügbar, um nach einer Komponente nach Namen zu filtern.
   * Die rechts neben dem Komponentengruppen-Namen aufgelisteten Zahlen geben die Gesamtanzahl der ausgewählten Komponenten in diesen Gruppen an, unabhängig vom Filter.

   ![chlimage_1-374](assets/chlimage_1-374.png)

   *Standardkomponenten*

   Im **Standardkomponenten** -Registerkarte definieren, definieren Sie, welche Komponenten automatisch bestimmten Medientypen zugeordnet werden. Wenn ein Autor ein Asset aus dem Asset-Browser zieht, weiß AEM, mit welcher Komponente es verknüpft werden soll. Beachten Sie, dass für diese Konfiguration nur Komponenten mit Ablageflächen verfügbar sind.

   Klicken oder tippen Sie auf **Zuordnung hinzufügen** , um eine völlig neue Komponente und MIME-Typzuordnung hinzuzufügen.

   Wählen Sie eine Komponente in der Liste aus und tippen/klicken Sie auf **Typ hinzufügen**, um einer bereits zugeordneten Komponente einen zusätzlichen MIME-Typ hinzuzufügen. Klicken Sie auf das Symbol **Löschen**, um einen MIME-Typ zu entfernen.

   ![chlimage_1-375](assets/chlimage_1-375.png)

   *Responsive Einstellungen*

   Auf der Registerkarte **Responsive Einstellungen** können Sie die Anzahl der Spalten im resultierenden Raster des Layout-Containers konfigurieren.

* **Komponenten entsperren/sperren**

   Komponenten werden entsperrt/gesperrt, um festzulegen, ob der Inhalt im Modus **Anfänglicher Inhalt** geändert werden darf.

   Wenn eine Komponente entsperrt wurde:

   * Im Rahmen wird eine offene Vorhängeschlossanzeige angezeigt.
   * Die Komponenten-Symbolleiste wird entsprechend angepasst.
   * Bereits eingegebener Inhalt wird nicht mehr in **Struktur** -Modus.

      * Bereits eingegebener Inhalt wird als anfänglicher Inhalt betrachtet und ist nur im Modus **Anfänglicher Inhalt** sichtbar.
   * Die Komponenten, die der entsperrten Komponente übergeordnet sind, können nicht verschoben, ausgeschnitten oder gelöscht werden.

   ![chlimage_1-376](assets/chlimage_1-376.png)

   Dies umfasst das Entsperren von Containerkomponenten, sodass weitere Komponenten hinzugefügt werden können, entweder im **Ursprüngliche Inhalte** oder auf den daraus resultierenden Seiten. Wenn Sie dem Container bereits Komponenten/Inhalte hinzugefügt haben, bevor Sie ihn entsperren, werden diese nicht mehr angezeigt, wenn Sie sich im Modus **Struktur** befinden, sondern im Modus **Ursprüngliche Inhalte**. Im **Strukturmodus** werden nur die Container-Komponente selbst und die zugehörige Liste der **zugelassenen Komponenten** angezeigt.

   ![chlimage_1-377](assets/chlimage_1-377.png)

   Um Speicherplatz zu sparen, wird der Layout-Container nicht an die Liste der zulässigen Komponenten angepasst. Stattdessen wird der Container zu einer bildlauffähigen Liste.

   Komponenten, die konfigurierbar sind, werden mit einem Symbol für **Richtlinien** angezeigt, auf das Sie tippen/klicken können, um die Richtlinie und Eigenschaften dieser Komponente zu bearbeiten.

   ![chlimage_1-378](assets/chlimage_1-378.png)

* **Beziehung zu vorhandenen Seiten**

   Auf diesen Seiten werden die Änderungen an der Vorlage widergespiegelt, wenn die Struktur aktualisiert wird, nachdem die Seiten auf der Grundlage der Vorlage erstellt wurden. In der Symbolleiste wird eine Warnung mit einem Bestätigungsdialog angezeigt, um Sie an diese Tatsache zu erinnern.

   ![chlimage_1-379](assets/chlimage_1-379.png)

### Bearbeiten einer Vorlage – Anfänglicher Inhalt – Autor {#editing-a-template-initial-content-author}

Der Modus **Anfänglicher Inhalt** wird für definierten Inhalt verwendet, der angezeigt wird, wenn eine Seite anfänglich auf der Grundlage einer Vorlage erstellt wird. Der anfängliche Inhalt kann dann von Seitenautoren bearbeitet werden.

Obwohl der gesamte Inhalt, der im Modus **Struktur** erstellt wird, im Modus **Anfänglicher Inhalt** sichtbar ist, können nur entsperrte Komponenten ausgewählt und bearbeitet werden.

>[!NOTE]
>
>Der Modus **Anfänglicher Inhalt** kann als Bearbeitungsmodus für Seiten betrachtet werden, die mit dieser Vorlage erstellt werden. Daher sind Richtlinien nicht im Modus **Anfänglicher Inhalt**, sondern im **[Strukturmodus](/help/sites-authoring/templates.md#editing-a-template-structure-template-author)** definiert.

* Entsperrte Komponenten, die zur Bearbeitung verfügbar sind, sind markiert. Wenn ausgewählt, wird ein blauer Rahmen angezeigt:

   ![chlimage_1-380](assets/chlimage_1-380.png)

* Entsperrte Komponenten haben eine Symbolleiste, mit der Sie den Inhalt bearbeiten und konfigurieren können:

   ![chlimage_1-381](assets/chlimage_1-381.png)

* Wenn eine Container-Komponente (im Modus **Struktur**) entsperrt wurde, können Sie neue Komponenten zum Container hinzufügen (im Modus **Anfänglicher Inhalt**). Komponenten, die im Modus **Anfänglicher Inhalt** hinzugefügt werden, können auf resultierende Seiten verschoben oder von diesen gelöscht werden.

   Sie können Komponenten über den Bereich **Komponenten hierher ziehen** oder mithilfe der Option **Neue Komponente einfügen** in der Symbolleiste des jeweiligen Containers hinzufügen.

   ![chlimage_1-382](assets/chlimage_1-382.png) ![chlimage_1-383](assets/chlimage_1-383.png)

* Wenn der anfängliche Inhalt der Vorlage aktualisiert wird, nachdem Seiten auf der Grundlage der Vorlage erstellt wurden, wirken sich die Änderungen am anfänglichen Inhalt der Vorlage nicht auf diese Seiten aus.

>[!NOTE]
>
>Der ursprüngliche Inhalt dient zum Vorbereiten von Komponenten und dem Seitenlayout, die als Ausgangspunkt für die Erstellung des Inhalts dienen. Dies soll nicht der eigentliche Inhalt sein, der unverändert bleibt. Aus diesem Grund können anfängliche Inhalte nicht übersetzt werden.

### Bearbeiten einer Vorlage – Layout – Vorlagenautor {#editing-a-template-layout-template-author}

Sie können das Vorlagen-Layout für verschiedene Geräte definieren. [Responsives Layout](/help/sites-authoring/responsive-layout.md) funktioniert für Vorlagen ebenso wie für die Seitenbearbeitung.

>[!NOTE]
>
>Änderungen am Layout werden im Modus **Anfänglicher Inhalt** widergespiegelt, doch im **Strukturmodus** sind keine Änderungen zu sehen.

![chlimage_1-384](assets/chlimage_1-384.png)

### Bearbeiten einer Vorlage – Seitendesign – Vorlagenautor/Entwickler {#editing-a-template-page-design-template-author-developer}

Der Seitenentwurf, einschließlich der erforderlichen Client-seitigen Bibliotheken und Seitenrichtlinien, wird unter der Option **Seitendesign** im Menü **Seiteninformationen** beibehalten.

So greifen Sie auf das Dialogfeld **Seitendesign** zu:

1. Wählen Sie im **Vorlagen-Editor** in der Symbolleiste die Option **Seiteninformationen** und anschließend **Seitendesign**, um das Dialogfeld zu öffnen.
1. Die **Seitendesign** wird geöffnet und ist in zwei Abschnitte unterteilt:

   * Die linke Hälfte definiert die [Seitenrichtlinien](/help/sites-authoring/templates.md#page-policies).
   * Die rechte Hälfte definiert die [Seiteneigenschaften](/help/sites-authoring/templates.md#page-properties).

   ![chlimage_1-385](assets/chlimage_1-385.png)

#### Seitenrichtlinien {#page-policies}

Sie können eine Inhaltsrichtlinie auf die Vorlage oder resultierende Seiten anwenden. So wird die Inhaltsrichtlinie für das Hauptabsatzsystem auf der Seite definiert.

![chlimage_1-386](assets/chlimage_1-386.png)

* Sie können eine vorhandene Richtlinie für die Seite im Dropdown-Menü **Richtlinie auswählen** auswählen.

   ![chlimage_1-387](assets/chlimage_1-387.png)

   Sie können eine neue Richtlinie hinzufügen, indem Sie auf die Schaltfläche „Hinzufügen“ klicken, die sich neben dem Dropdown-Menü **Richtlinie auswählen** befindet. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden.

   ![chlimage_1-388](assets/chlimage_1-388.png)

   Die im Dropdown-Menü **Richtlinie auswählen** ausgewählte vorhandene Richtlinie kann mithilfe der Schaltfläche „Kopieren“, die sich neben dem Dropdown-Menü befindet, kopiert werden. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden. Standardmäßig erhält die kopierte Richtlinie den Namen **Kopie von X**, wobei X der Name der kopierten Richtlinie ist.

   ![chlimage_1-389](assets/chlimage_1-389.png)

* Geben Sie im Feld **Richtlinienname** einen Namen für die Richtlinie an. Eine Richtlinie muss einen Namen tragen, damit sie mühelos im Dropdown-Menü **Richtlinie auswählen** ausgewählt werden kann.

   ![chlimage_1-390](assets/chlimage_1-390.png)

* Eine Beschreibung der Richtlinie im Feld **Richtlinienbeschreibung** ist optional.
* Im Abschnitt **Andere Vorlagen, die ebenfalls die ausgewählte Richtlinie verwenden** ist leicht ersichtlich, welche anderen Vorlagen die Richtlinie verwenden, die in der Dropdown-Liste **Richtlinie auswählen** ausgewählt wurde.

   ![chlimage_1-391](assets/chlimage_1-391.png)

#### Seiteneigenschaften {#page-properties}

Mithilfe der Seiteneigenschaften können Sie die erforderlichen Client-seitigen Bibliotheken definieren, indem Sie das Dialogfeld **Seiten-Design** verwenden. Diese Client-seitigen Bibliotheken enthalten Stylesheets und JavaScript, die zusammen mit der Vorlage und den mit der Vorlage erstellten Seiten geladen werden.

![chlimage_1-392](assets/chlimage_1-392.png)

* Geben Sie die Client-seitigen Bibliotheken an, die auf die mit dieser Vorlage erstellten Seiten angewendet werden sollen. Eingabe des Namens einer Bibliothek in das Textfeld im Bereich **Client-Bibliotheken**.

   ![chlimage_1-393](assets/chlimage_1-393.png)

* Wenn mehrere Bibliotheken erforderlich sind, klicken Sie auf die Schaltfläche „Hinzufügen“, um ein zusätzliches Textfeld für den Namen der Bibliothek hinzuzufügen.

   ![chlimage_1-394](assets/chlimage_1-394.png)

   Fügen Sie für Ihre Client-seitigen Bibliotheken so viele Textfelder wie nötig hinzu.

   ![chlimage_1-395](assets/chlimage_1-395.png)

* Definieren Sie bei Bedarf die relative Position der Bibliotheken, indem Sie die Felder mithilfe des Ziehpunkts ziehen.

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>Während der Vorlagenautor die Seitenrichtlinien in der Vorlage festlegt, benötigt er Angaben zu den jeweiligen Client-seitigen Bibliotheken vom Entwickler.

### Bearbeiten einer Vorlage – Anfängliche Seiteneigenschaften – Autor {#editing-a-template-initial-page-properties-author}

Mit der Option **Anfängliche Seiteneigenschaften** können Sie die anfänglichen [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) definieren, die bei der Erstellung einer neuen Seite gelten sollen.

1. Wählen Sie im Vorlageneditor **Seiteninformationen** aus der Symbolleiste und anschließend **Anfängliche Seiteneigenschaften**, um das Dialogfeld zu öffnen.

1. Im Dialogfeld können Sie Eigenschaften definieren, die für Seiten gelten sollen, die mit dieser Vorlage erstellt werden.

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. Bestätigen Sie Ihre Definitionen mit **Fertig**.

## Best Practices {#best-practices}

Beachten Sie beim Erstellen von Vorlagen Folgendes:

1. Die Auswirkungen von Änderungen an der Vorlage, sobald Seiten aus dieser Vorlage erstellt wurden.

   Im Folgenden finden Sie eine Liste der verschiedenen Vorgänge, die für Vorlagen möglich sind, sowie deren Auswirkungen auf die daraus erstellten Seiten:

   * Änderungen an der Struktur:

      * Diese werden sofort auf die resultierenden Seiten angewendet.
      * Die geänderte Vorlage muss veröffentlicht werden, damit Besucher die Änderungen sehen können.
   * Änderungen an Inhaltsrichtlinien und Designkonfigurationen:

      * Diese gelten sofort für die resultierenden Seiten.
      * Die Änderungen müssen veröffentlicht werden, damit Besucher die Änderungen sehen können.
   * Änderungen am anfänglichen Inhalt:

      * Diese gelten nur für Seiten, die nach den Änderungen an der Vorlage erstellt wurden.
   * Änderungen am Layout hängen davon ab, ob die geänderte Komponente Teil von ist:

      * Nur Struktur - sofort angewendet
      * Ursprünglichen Inhalt enthalten - nur auf Seiten, die nach der Änderung erstellt wurden

   Besondere Vorsicht ist erforderlich bei:

   * Sperren oder Entsperren von Komponenten in aktivierten Vorlagen.
   * Dies kann Nebeneffekte haben, da die Komponenten bereits von vorhandenen Seiten verwendet werden können. In der Regel:

      * Das Entsperren von Komponenten (die gesperrt waren) fehlt auf vorhandenen Seiten.
      * Durch das Sperren von Komponenten (die bearbeitbar waren) wird der Inhalt vor der Anzeige auf den Seiten ausgeblendet.

   >[!NOTE]
   >
   >AEM gibt explizite Warnungen aus, wenn der Sperrstatus von Komponenten in Vorlagen geändert wird, bei denen es sich nicht mehr um Entwürfe handelt.

1. [Erstellen eigener Ordner](#creating-a-template-folder-admin) für Ihre Site-spezifischen Vorlagen.
1. [Vorlagen veröffentlichen](#publishing-a-template-template-author) von **Vorlagen** Konsole.
