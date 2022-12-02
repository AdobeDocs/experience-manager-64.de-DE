---
title: Creative Project und PIM-Integration
seo-title: Creative Project and PIM Integration
description: Creative Project optimiert den gesamten Fotoaufnahme-Workflow, einschließlich Generierung einer Fotoshooting-Anfrage, Hochladen eines Fotoshootings, Zusammenarbeit bei einem Fotoshooting und Verpackung von bestätigten Assets
seo-description: Creative Project streamlines the entire photo shoot workflow that including generating a photo shoot request, uploading a photo shoot, collaborating on a photo shoot, and packaging approved assets
uuid: 09f27d36-e725-45cb-88d1-27383aedceed
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: projects
content-type: reference
discoiquuid: 0e5d0a45-c663-4d91-b793-03d39119d103
exl-id: b477d6ab-126a-489a-a13f-2b6f439ab85b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2980'
ht-degree: 77%

---

# Creative Project und PIM-Integration{#creative-project-and-pim-integration}

Als Marketer oder Kreativschaffender können Sie die Creative Project-Werkzeuge in Adobe Experience Manager (AEM) verwenden, um eCommerce-bezogene Produktfotografie und zugehörige kreative Prozesse innerhalb Ihrer Organisation zu verwalten.

Insbesondere können Sie Creative Project zur Optimierung der folgenden Aufgaben in Ihrem Fotoshooting-Workflow verwenden:

* Generieren einer Fotoshooting-Anfrage
* Hochladen eines Fotoshootings
* Zusammenarbeit an einem Fotoshooting
* Verpacken bestätigter Assets

>[!NOTE]
>
>Informationen zur Zuweisung von Benutzerrollen und Workflows zu bestimmen Benutzertypen finden Sie unter [Informationen zu Projekt-Benutzerrollen](/help/sites-authoring/projects.md#user-roles-in-a-project).

## Erkunden von Workflows für Produkt-Fotoshootings  {#exploring-product-photo-shoot-workflows}

Creative Project bietet mehrere Projektvorlagen, die unterschiedlichen Projektanforderungen gerecht werden. Die Vorlage &quot;Projekt für Produkt-Fotoshooting&quot;ist standardmäßig verfügbar. Diese Vorlage stellt Fotoshooting-Workflows bereit, mit denen Sie Anfragen für Produkt-Fotoshootings einleiten und verwalten können. Sie enthält darüber hinaus eine Reihe von Aufgaben, die es Ihnen ermöglichen, digitale Bilder für Produkte anhand geeigneter Bewertungs- und Bestätigungsabläufe zu erhalten.

Die Vorlage beinhaltet die folgenden Workflows:

* Workflow **Produkt-Fotoshooting (Commerce-Integration)**: Dieser Workflow nutzt die Commerce-Integration in das Produktinformationsmanagement (PIM)-System zur automatischen Generierung einer Aufnahmenliste auf Grundlage der ausgewählten Produkte (Hierarchie). Sie können die Produktdaten als Teil der Asset-Metadaten anzeigen, nachdem der Workflow abgeschlossen wurde.
* Workflow **Produkt-Fotoshooting**: Dieser Workflow ermöglicht es Ihnen, eine Aufnahmenliste bereitzustellen, anstatt sich auf die Commerce-Integration zu verlassen. Dabei werden die hochgeladenen Bilder in einer CSV-Datei im Assets-Ordner des Projekts protokolliert.

>[!NOTE]
>
>Die CSV-Datei, die in der Aufgabe „Aufnahmenliste hochladen“ des Workflows „Produkt-Fotoshooting“ hochgeladen wird, sollte den Namen „shotlist.csv“ haben.

## Erstellen eines Projekts für Produkt-Fotoshootings {#create-a-product-photo-shoot-project}

1. Im **Projekte** Konsole, tippen/klicken **Erstellen** und wählen Sie dann **Projekt erstellen** aus der Liste.

   ![chlimage_1-132](assets/chlimage_1-132.png)

1. Wählen Sie auf der Seite **Projekt erstellen** die Vorlage für Fotoshooting-Projekte aus und klicken/tippen Sie auf **Weiter**.

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. Geben Sie Details zum Projekt einschließlich Titel, Beschreibung und Fälligkeitsdaten ein. Fügen Sie Benutzer hinzu und weisen Sie ihnen verschiedene Rollen zu. Sie können auch ein Miniaturbild für das Projekt hinzufügen.

   ![chlimage_1-134](assets/chlimage_1-134.png)

1. Tippen oder klicken Sie auf **Erstellen**. Eine Bestätigungsmeldung informiert Sie, dass das Projekt erstellt wurde.
1. Tippen/klicken **Fertig** , um zur **Projekte** Konsole. Tippen/klicken Sie alternativ auf **Öffnen** , um die Assets im Fotoshooting-Projekt anzuzeigen.

## Beginn der Arbeit an einem Projekt für Produkt-Fotoshooting {#starting-work-in-a-product-photo-shoot-project}

Um eine Fotoshooting-Anfrage einzuleiten, klicken oder tippen Sie auf ein Projekt und klicken Sie danach auf der Seite mit den Projektdetails auf **Arbeit hinzufügen**, um einen Workflow zu starten.

![chlimage_1-135](assets/chlimage_1-135.png)

Im Lieferumfang eines Produkt-Fotoshooting-Projekts sind folgende Workflows enthalten:

* Workflow „Produkt-Fotoshooting (Commerce-Integration)“
* Workflow „Produkt-Fotoshooting“

Verwenden Sie den Workflow Produkt-Fotoshooting (Commerce-Integration) zur Zuordnung von Bild-Assets zu den Produkten in AEM. Dieser Workflow nutzt Commerce-Integration zur Verknüpfung der bestätigten Bilder mit den vorhandenen Produktdaten unter dem Speicherort */etc/commerce*.

Der Workflow Produkt-Fotoshooting (Commerce-Integration) umfasst die folgenden Aufgaben:

* Aufnahmenliste erstellen
* Fotoshooting hochladen
* Fotoaufnahme retuschieren
* Bewerten und bestätigen
* Zu Produktionsaufgabe wechseln

Wenn in AEM keine Produktinformationen verfügbar sind, verwenden Sie den Workflow Produkt-Fotoshooting, um Bild-Assets den Produkten auf der Basis der Informationen zuzuordnen, die Sie in eine CSV-Datei hochladen. Die CSV-Datei muss grundlegende Produktinformationen wie zum Beispiel Produkt-ID, Kategorie und Beschreibung enthalten. Der Workflow ruft bestätigte Assets für die Produkte ab.

Dieser Workflow umfasst die folgenden Aufgaben:

* Aufnahmenliste hochladen
* Fotoshooting hochladen
* Fotoaufnahme retuschieren
* Bewerten und bestätigen
* Zu Produktionsaufgabe wechseln

Sie können diesen Workflow mit der Workflow-Konfigurationsoption anpassen.

Beide Workflows umfassen Schritte zur Verknüpfung von Produkten mit ihren bestätigten Assets. Jeder Workflow umfasst die folgenden Schritte:

* Workflow-Konfiguration: Beschreibt die Optionen zur Anpassung des Workflows
* Starten eines Projekt-Workflows: Erläutert, wie ein Produkt-Fotoshooting gestartet wird
* Workflow-Aufgabendetails: Stellt Details von Aufgaben bereit, die im Workflow zur Verfügung stehen

## Verfolgen des Projektfortschritts {#tracking-project-progress}

Sie können den Fortschritt eines Projekts verfolgen, indem Sie die aktiven/abgeschlossenen Aufgaben im Projekt überwachen.

Verwenden Sie Folgendes, um den Fortschritt eines Projekts zu überwachen:

* **Aufgabenkarte**

* **Aufgabenliste**

Die Aufgabenkarte zeigt den Gesamtfortschritt des Projekts. Sie wird nur dann auf der Seite „Projektdetails“ angezeigt, wenn das Projekt zugehörige Aufgaben aufweist. Die Aufgabenkarte zeigt den aktuellen Abschlussstatus des Projekts auf der Basis der abgeschlossenen Aufgaben an. Zukünftige Aufgaben werden nicht berücksichtigt.

Die Aufgabenkarte stellt die folgenden Detailinformationen bereit:

* Prozentsatz der aktiven Aufgaben
* Prozentsatz der abgeschlossenen Aufgaben

![chlimage_1-136](assets/chlimage_1-136.png)

Die Aufgabenliste stellt detaillierte Information zur aktuell aktiven Workflow-Aufgabe für das Projekt bereit. Um die Liste anzuzeigen, tippen/klicken Sie auf die Aufgabenkarte. Die Aufgabenliste zeigt auch Metadaten, z. B. Startdatum, Fälligkeitsdatum, Beauftragter, Priorität und Status der Aufgabe an.

![chlimage_1-137](assets/chlimage_1-137.png)

## Workflow-Konfiguration {#workflow-configuration}

Diese Aufgabe schließt die Zuweisung von Workflow-Schritten zu Benutzern auf Grundlage ihrer Rollen ein.

So konfigurieren Sie den Workflow **Produkt-Fotoshooting**:

1. Navigieren Sie zu **Werkzeuge** > **Workflows** und tippen Sie anschließend auf den Bereich **Modelle**, um die Seite **Workflow-Modelle** zu öffnen.
1. Wählen Sie den Workflow **Produkt-Fotoshooting** aus und tippen Sie auf der Symbolleiste auf das Symbol **Bearbeiten**, um den Workflow im Bearbeitungsmodus zu öffnen.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. Öffnen Sie auf der Seite **Workflow „Produkt-Fotoshooting“** eine Projektaufgabe. Öffnen Sie z. B. die Aufgabe **Aufnahmenliste hochladen**.

   ![chlimage_1-139](assets/chlimage_1-139.png)

1. Klicken Sie auf die Registerkarte **Aufgabe**, um Folgendes zu konfigurieren:

   * Name der Aufgabe
   * Standardbenutzer(rolle), der/die die Aufgabe empfängt
   * Standardpriorität der Aufgabe, die in der Aufgabenliste des Benutzers angezeigt wird
   * Aufgabenbeschreibung, die angezeigt wird, wenn der Bevollmächtigte die Aufgabe öffnet
   * Fälligkeitsdatum für eine Aufgabe, das auf Grundlage des Zeitpunkts des Aufgabenbeginns berechnet wird

1. Klicken Sie auf **OK**, um die Konfigurationseinstellungen zu speichern.

   Auf ähnliche Weise können Sie die folgenden Aufgaben für den Workflow **Produkt-Fotoshooting** konfigurieren:

   * Fotoshooting hochladen
   * Produkt-Fotoshooting retuschieren
   * Fotoshooting-Bewertung
   * In Produktion verschieben

   Führen Sie ein ähnliches Verfahren aus, um die Aufgaben im **Workflow &quot;Produkt-Fotoshooting (Commerce-Integration)&quot;**.

In diesem Abschnitt wird beschrieben, wie das Produktinformations-Management in Ihr Creative-Projekt integriert wird.

## Starten eines Projekt-Workflows {#starting-a-project-workflow}

1. Navigieren Sie zu einem Projekt mit einem Produkt-Fotoshooting und tippen/klicken Sie auf das **Arbeit hinzufügen** auf **Workflows** Karte.
1. Wählen Sie die Workflow-Karte **Produkt-Fotoshooting (Commerce-Integration)** aus, um den entsprechenden Workflow zu starten. Wenn die Produktinformationen nicht unter /etc/commerce verfügbar sind, wählen Sie die **Produkt-Fotoshooting** und starten Sie den Workflow Produkt-Fotoshooting .

   ![chlimage_1-140](assets/chlimage_1-140.png)

1. Tippen/klicken Sie auf **Weiter**, um den Workflow im Projekt einzuleiten.
1. Geben Sie auf der nächsten Seite Details zum Workflow ein.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   Klicken Sie auf **Übermitteln**, um den Fotoshooting-Workflow zu starten. Die Seite mit den Details zum Fotoshooting-Projekt wird angezeigt.

   ![chlimage_1-142](assets/chlimage_1-142.png)

### Workflow-Aufgabendetails {#workflow-tasks-details}

Der Fotoshooting-Workflow umfasst mehrere Aufgaben. Jede Aufgabe wird auf Grundlage der für die Aufgabe definierten Konfiguration einer Benutzergruppe zugewiesen.

#### Aufnahmenlistenaufgabe erstellen {#create-shot-list-task}

Die Aufgabe **Aufnahmenliste erstellen** ermöglicht dem Projekteigentümer die Auswahl von Produkten, für die Bilder benötigt werden. Je nach vom Benutzer ausgewählter Option wird eine CSV-Datei generiert, die grundlegende Produktinformationen enthält.

1. Tippen oder klicken Sie im Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.

   ![chlimage_1-143](assets/chlimage_1-143.png)

1. Wählen Sie die Aufgabe **Aufnahmenliste erstellen** aus und tippen oder klicken Sie dann auf der Symbolleiste auf das Symbol **Öffnen**.

   ![chlimage_1-144](assets/chlimage_1-144.png)

1. Überprüfen Sie die Aufgabendetails und tippen/klicken Sie dann auf die Schaltfläche **Aufnahmenliste erstellen**.

   ![chlimage_1-145](assets/chlimage_1-145.png)

1. Wählen Sie Produkte, für die Produktdaten ohne verknüpfte Bilder vorhanden sind.

   ![chlimage_1-146](assets/chlimage_1-146.png)

1. Tippen/klicken Sie auf **Zur Aufnahmenliste hinzufügen** -Symbol, um eine CSV-Datei zu erstellen, die eine Liste all dieser Produkte enthält. Eine Meldung betätigt, dass die Aufnahmenliste für die ausgewählten Produkte erstellt wird. Klicken Sie auf **Schließen**, um den Workflow abzuschließen.
1. Nach dem Erstellen einer Aufnahmenliste wird der Link **Aufnahmenliste anzeigen** angezeigt. Um weitere Produkte zur Aufnahmenliste hinzuzufügen, tippen/klicken Sie auf **Zur Aufnahmenliste hinzufügen**. In diesem Fall werden die Daten an die anfangs erstellte Aufnahmenliste angehängt.

   ![chlimage_1-147](assets/chlimage_1-147.png)

1. Tippen/klicken Sie auf **Aufnahmenliste anzeigen**, um die neue Aufnahmenliste anzuzeigen.

   ![chlimage_1-148](assets/chlimage_1-148.png)

   Um die vorhandenen Daten zu bearbeiten oder neue Daten hinzuzufügen, tippen/klicken Sie in der Symbolleiste auf **Bearbeiten**. Sie können nur die Felder **Produkt** und **Beschreibung** bearbeiten.

   ![chlimage_1-149](assets/chlimage_1-149.png)

   Tippen/klicken Sie nach dem Aktualisieren der Datei auf **Speichern** in der Symbolleiste, um die Datei zu speichern.

1. Tippen/klicken Sie nach dem Hinzufügen der Produkte auf das **Fertig** auf der Seite &quot;Aufnahmenliste erstellen&quot;angezeigt, um die Aufgabe als abgeschlossen zu markieren. Sie können wahlweise einen Kommentar hinzufügen.

   Durch Abschluss der Aufgabe werden die folgenden Änderungen innerhalb des Projekts eingeführt:

   * Der Produkthierarchie entsprechende Assets werden in einem Ordner mit demselben Namen wie der Titel des Workflow erstellt.
   * Die Metadaten für die Assets werden in der Konsole „Assets“ bearbeitbar, sogar bevor der Fotograf die Bilder zur Verfügung stellt.
   * Es wird ein Fotoshooting-Ordner erstellt, in dem die vom Fotografen bereitgestellten Bilder gespeichert werden. Dieser Ordner enthält Unterordner für jeden Produkteintrag in der Aufnahmenliste.

   Für den Workflow „Produkt-Fotoshooting“ (ohne Commerce-Integration) ist „Aufnahmenliste hochladen“ die erste Aufgabe. Tippen/klicken Sie auf **Aufnahmenliste hochladen**, um eine Datei mit dem Namen **shotlist.csv** hochzuladen. Die CSV-Datei sollte die Produkt-ID enthalten. Die anderen Felder sind optional. Sie können sie für die Zuordnung von Assets zu Produkten verwenden.

### Aufnahmenlistenaufgabe hochladen {#upload-shot-list-task}

Diese Aufgabe ist Teil des Produkt-Fotoshooting-Workflows. Diese Aufgabe führen Sie aus, wenn in AEM keine Produktinformationen verfügbar sind. In diesem Fall laden Sie eine Liste von Produkten in einer CSV-Datei hoch, für die Bild-Assets erforderlich sind. Anhand der Informationen in der CSV-Datei ordnen Sie die Bild-Assets den Produkten zu.

Verwenden Sie den Link **Aufnahmenliste anzeigen** unter der Projektkarte im vorherigen Verfahren, um eine Beispieldatei im CSV-Format herunterzuladen. Überprüfen Sie die Beispieldatei, um sich mit dem üblichen Inhalt einer CSV-Datei vertraut zu machen.

Die Produktliste oder CSV-Datei kann Felder wie z. B. **Kategorie, Produkt, ID, Beschreibung** und **Pfad** enthalten. Das Feld **ID** ist obligatorisch und enthält die Produkt-ID. Die anderen Felder sind optional.

Ein Produkt kann zu einer bestimmten Kategorie gehören. Die Produktkategorie kann in der CSV-Datei unterhalb der Spalte **Kategorie** aufgeführt werden. Das Feld **Produkt** enthält den Namen des Produkts. Geben Sie im Feld **Beschreibung** die Produktbeschreibung oder Anleitungen für Fotografen ein.

>[!NOTE]
>
>Der Name der hochzuladenden Bilder sollte mit &quot;**&lt;productid>_&quot;** wobei die Produkt-ID über die **ID** im Feld *shotlist.csv* -Datei. Beispielsweise für ein Produkt in der Aufnahmenliste mit **Id 397122** können Sie Dateien mit Namen hochladen **397122_highcontrast.jpg**, **397122_lowlight.png** usw.

1. Tippen oder klicken Sie im Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) um die Liste der Aufgaben im Workflow anzuzeigen.
1. Wählen Sie die **Aufnahmenliste hochladen** und tippen/klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![chlimage_1-150](assets/chlimage_1-150.png)

1. Überprüfen Sie die Aufgabendetails und tippen/klicken Sie dann auf die **Aufnahmenliste hochladen** Schaltfläche.

   ![chlimage_1-151](assets/chlimage_1-151.png)

1. Tippen/klicken Sie auf **Aufnahmenliste hochladen** Schaltfläche zum Hochladen der CSV-Datei mit dem Dateinamen shotlist.csv. Der Workflow erkennt diese Datei als eine Quelle, die zum Extrahieren von Produktdaten für die nächste Aufgabe verwendet werden kann.
1. Laden Sie eine CSV-Datei hoch, die Produktinformationen im entsprechenden Format enthält. Der Link &quot;Hochgeladene Assets anzeigen&quot;wird unter der Karte angezeigt, nachdem die CSV-Datei hochgeladen wurde.

   ![chlimage_1-152](assets/chlimage_1-152.png)

   Klicken Sie auf das Symbol **Fertig stellen**, um diese Aufgabe abzuschließen.

1. Tippen/klicken Sie auf das Symbol **Fertigstellen**, um die Aufgabe abzuschließen.

### Aufgabe „Fotoshooting hochladen“ {#upload-photo-shoot-task}

Als Redakteur können Sie Aufnahmen für Produkte hochladen, die in der Datei **shotlist.csv** aufgeführt sind, welche in der vorherigen Aufgabe erstellt oder hochgeladen wurde.

Der Name der Bilder, die hochgeladen werden sollen, sollte mit **&quot;&lt;productid>_&quot;** wobei die Produkt-ID über die **ID** im Feld **shotlist.csv** -Datei. Beispiel: Für ein Produkt mit der **ID 397122** in der Aufnahmenliste können Sie Dateien mit den Namen **397122_highcontrast.jpg**,**397122_lowlight.png** usw. hochladen.

Sie können entweder die Bilder direkt hochladen oder eine ZIP-Datei hochladen, die die Bilder enthält. Basierend auf ihren Namen werden die Bilder in entsprechenden Produktordnern innerhalb des Ordners **Fotoshooting** abgelegt.

1. Tippen/klicken Sie unter dem Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Fotoshooting hochladen** und tippen/klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![chlimage_1-153](assets/chlimage_1-153.png)

1. Tippen/klicken Sie auf &quot;Fotoshooting hochladen&quot;und laden Sie die Fotoshooting-Bilder hoch.
1. Tippen/klicken Sie in der Symbolleiste auf das Symbol **Fertig stellen**, um die Aufgabe abzuschließen.

### Aufgabe „Fotoaufnahme retuschieren“ {#retouch-photo-shoot-task}

Wenn Sie Bearbeitungsrechte haben, führen Sie die Aufgabe „Fotoaufnahme retuschieren“ aus, um die in den Ordner „Fotoshooting“ hochgeladenen Bilder zu bearbeiten.

1. Tippen/klicken Sie unter dem Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die Aufgabe **Fotoaufnahme retuschieren** aus und tippen/klicken Sie dann auf der Symbolleiste auf das Symbol **Öffnen**.

   ![chlimage_1-154](assets/chlimage_1-154.png)

1. Tippen/klicken Sie auf **Hochgeladene Assets anzeigen** im **Fotoaufnahme retuschieren** Seite, um die hochgeladenen Bilder zu durchsuchen.

   ![chlimage_1-155](assets/chlimage_1-155.png)

   Falls erforderlich, bearbeiten Sie die Bilder mit einer Adobe Creative Cloud-Applikation.

   ![chlimage_1-156](assets/chlimage_1-156.png)

1. Tippen/klicken Sie in der Symbolleiste auf das Symbol **Fertig stellen**, um die Aufgabe abzuschließen.

### Aufgabe „Überprüfen und bestätigen“ {#review-and-approve-task}

In dieser Aufgabe prüfen Sie die Fotoaufnahmen, die von einem Fotografen hochgeladen wurden, und markieren die Aufnahmen als für die Nutzung freigegeben.

1. Tippen/klicken Sie unter dem Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Überprüfen und genehmigen** und tippen/klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. Im **Überprüfen und genehmigen** , weisen Sie die Überprüfungsaufgabe einer Rolle zu, z. B. &quot;Überprüfer&quot;, und tippen/klicken Sie dann auf &quot;Überprüfen&quot;, um mit der Überprüfung der hochgeladenen Produktbilder zu beginnen.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. Wählen Sie ein Produktbild aus und tippen/klicken Sie dann in der Symbolleiste auf das Symbol „Genehmigen“, um das Produktbild als genehmigt zu markieren.

   ![chlimage_1-159](assets/chlimage_1-159.png)

   Sobald Sie ein Bild genehmigt haben, wird darüber ein „Genehmigt“-Banner angezeigt.

   >[!NOTE]
   Sie können Produkte ohne Bilder übergehen. Zu einem späteren Zeitpunkt können Sie zur Aufgabe zurückkehren und sie nach Erledigung als abgeschlossen kennzeichnen.

1. Tippen/klicken Sie auf **Fertig stellen**. Die bestätigten Bilder werden mit den leeren Assets verknüpft, die erstellt wurden.

Mithilfe der Assets-Benutzeroberfläche können Sie zu den Projekt-Assets navigieren und die genehmigten Bilder überprüfen.

Klicken Sie auf die nächste Ebene, um Produkte entsprechend Ihrer Produktdatenhierarchie anzuzeigen.

Creative Project verbindet bestätigte Assets mit dem referenzierten Produkt. Die Asset-Metadaten werden mit der Produktreferenz und den grundlegenden Informationen auf der Registerkarte &quot;Produktdaten&quot;unter den Asset-Eigenschaften aktualisiert, die im Abschnitt AEM Asset-Metadaten angezeigt werden.

>[!NOTE]
Im Workflow Produkt-Fotoshooting (ohne Commerce-Integration) sind die bestätigten Bilder mit keinen Produkten verbunden.

### Zu Produktionsaufgabe wechseln {#move-to-production-task}

Mit dieser Aufgabe werden die bestätigten Assets in den produktionsbereiten Ordner verschoben, damit sie verwendet werden können.

1. Tippen/klicken Sie unter dem Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Zur Produktion wechseln** und tippen/klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. Um die bestätigten Assets für das Fotoshooting vor dem Verschieben in den produktionsbereiten Ordner anzuzeigen, klicken Sie auf den Link **Bestätigte Assets anzeigen** unter der Projektminiatur auf der Aufgabenseite **Zur Produktion wechseln**.

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. Geben Sie den Pfad des produktionsbereiten Ordners im Feld **Verschieben nach** ein.

   ![chlimage_1-162](assets/chlimage_1-162.png)

   Tippen/klicken **Zur Produktion wechseln**. Schließen Sie die Bestätigungsmeldung. Die Assets werden in den angegebenen Pfad verschoben und es wird automatisch ein Rotationsset für die bestätigten Assets für jedes Produkt basierend auf der Ordnerhierarchie erstellt.

1. Tippen/klicken Sie in der Symbolleiste auf das Symbol **Fertig stellen**. Der Workflow wird mit Kennzeichnung des letzten Schritts als fertig gestellt abgeschlossen.

## Anzeigen von DAM-Asset-Metadaten {#viewing-dam-asset-metadata}

Nach erfolgter Bestätigung werden die Assets mit den entsprechenden Produkten verknüpft. Die [Eigenschaftenseite](/help/assets/managing-assets-touch-ui.md#editing-properties) der bestätigten Assets weist nunmehr die zusätzliche Registerkarte **Produktdaten** (verknüpfte Produktinformationen) auf. Auf dieser Registerkarte werden die Produktdetails, SKU-Nummer und weitere produktbezogene Details angezeigt, die das Asset verknüpfen. Tippen/klicken Sie auf das Symbol **Bearbeiten**, um die Eigenschaften eines Assets zu aktualisieren. Die produktbezogenen Informationen sind stets schreibgeschützt.

Klicken Sie auf den angezeigten Link, um zur entsprechenden Produktdetailseite in der Produktekonsole zu navigieren, mit der das Asset verknüpft ist.

## Anpassen der Workflows für Projekt-Fotoshootings {#customizing-the-project-photo-shoot-workflows}

Sie können die Workflows für Projekt-Fotoshootings je nach Anforderung anpassen. Dies ist eine optionale rollenbasierte Aufgabe, die zum Festlegen des Werts einer Variablen innerhalb des Projekts durchgeführt wird. Sie können danach den konfigurierten Wert zur Entscheidungsfindung heranziehen.

1. Klicken/tippen Sie auf das AEM und navigieren Sie dann zu **Instrumente** > **Workflow** > **Modelle** , um die Seite &quot;Workflow-Modelle&quot;zu öffnen.
1. Wählen Sie den Workflow **Produkt-Fotoshooting (Commerce-Integration)** oder **Produkt-Fotoshooting** aus und klicken/tippen Sie in der Symbolleiste auf **Bearbeiten**, um den Workflow im Bearbeitungsmodus zu öffnen.
1. Öffnen Sie die Aufgaben **Projekte** im Sidekick und ziehen Sie den Schritt **Rollenbasierte Projektaufgabe erstellen** in den Workflow.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Öffnen Sie den Schritt **Rollenbasierte Aufgabe**.
1. Geben Sie auf der Registerkarte **Aufgabe** einen Namen für die Aufgabe ein, der in der Liste **Aufgabe** angezeigt wird. Sie können die Aufgabe auch einer Rolle zuweisen, die Standardpriorität festlegen, eine Beschreibung angeben und einen Fälligkeitszeitpunkt für die Aufgabe bestimmen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Geben Sie auf der Registerkarte **Routing** die Aktionen für die Aufgabe an. Um mehrere Aktionen hinzuzufügen, tippen/klicken Sie auf den Link &quot;Element hinzufügen&quot;.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Klicken Sie nach dem Hinzufügen der Optionen auf **OK**, um die Änderungen zum Schritt hinzuzufügen.

   >[!NOTE]
   Tippen/Klicken **OK** speichert die Änderungen nicht im Workflow. Tippen/klicken Sie zum Speichern der Änderungen im Workflow auf **Speichern**.

1. Öffnen Sie die **Workflow** Aufgaben aus dem Sidekick und fügen Sie eine **Goto** Aufgabe.
1. Öffnen Sie die Aufgabe **Gehe zu** und tippen/klicken Sie auf die Registerkarte **Prozess**.
1. Geben Sie den folgenden Code im Feld **Skript** an:

```
   function check() {

   if (workflowData.getMetaDataMap().get("lastTaskAction","") == "Reject All") {

   return true

   }

   // set copywriter user in metadata

   var previousId = workflowData.getMetaDataMap().get("lastTaskCompletedBy", "");

   workflowData.getMetaDataMap().put("copywriter", previousId);

   return false;

   }
```

>[!NOTE]
Weitere Informationen zur Skripterstellung in Workflow-Schritten finden Sie unter [Definieren einer Regel für eine ODER-Teilung](/help/sites-developing/workflows-models.md).

![chlimage_1-166](assets/chlimage_1-166.png)

1. Tippen/klicken Sie auf **OK**.

1. Tippen/klicken **Speichern** , um den Workflow zu speichern.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Nach der [Zur Produktionsaufgabe wechseln](#move-to-production-task) ist abgeschlossen und wird dem Eigentümer zugewiesen.

   Die Benutzerin oder der Benutzer mit der Eigentümerrolle kann die Aufgabe abschließen und eine Aktion (in der Liste der in den Workflow-Schrittkonfigurationen hinzugefügten Aktionen) in der Liste im Kommentar-Popup auswählen.

   ![chlimage_1-168](assets/chlimage_1-168.png)

   Wählen Sie die geeignete Option aus und klicken Sie auf **Fertig stellen**, um den **Gehe-zu-Schritt** im Workflow auszuführen.

>[!NOTE]
Wenn Sie einen Server starten, speichert das Servlet für die Projektaufgabenliste die Zuordnungen zwischen Aufgabentypen und den unter `/libs/cq/core/content/projects/tasktypes` definierten URLs im Zwischenspeicher. Sie können danach die übliche Überlagerung durchführen und benutzerdefinierte Aufgabentypen hinzufügen, indem Sie sie unter `/apps/cq/core/content/projects/tasktypes` ablegen.
