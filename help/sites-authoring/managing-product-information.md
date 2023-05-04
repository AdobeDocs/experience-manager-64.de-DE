---
title: Creative Project und PIM-Integration
seo-title: Creative Project and PIM Integration
description: Creative Project optimiert den gesamten Fotoshooting-Workflow, einschließlich der Generierung einer Fotoshooting-Anfrage, des Hochladens eines Fotoshootings, der Zusammenarbeit bei einem Fotoshooting und der Verpackung genehmigter Assets
seo-description: Creative Project streamlines the entire photo shoot workflow that including generating a photo shoot request, uploading a photo shoot, collaborating on a photo shoot, and packaging approved assets
uuid: 09f27d36-e725-45cb-88d1-27383aedceed
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: projects
content-type: reference
discoiquuid: 0e5d0a45-c663-4d91-b793-03d39119d103
exl-id: b477d6ab-126a-489a-a13f-2b6f439ab85b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3016'
ht-degree: 33%

---

# Creative Project und PIM-Integration{#creative-project-and-pim-integration}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Als Marketer oder Kreativschaffender können Sie die Creative Project-Werkzeuge in Adobe Experience Manager (AEM) verwenden, um eCommerce-bezogene Produktfotografie und zugehörige kreative Prozesse innerhalb Ihrer Organisation zu verwalten.

Insbesondere können Sie mit Creative Project die folgenden Aufgaben in Ihrem Fotoshooting-Workflow optimieren:

* Erstellen einer Fotoshooting-Anfrage
* Hochladen eines Fotoshootings
* Zusammenarbeit bei einem Fotoshooting
* Verpacken genehmigter Assets

>[!NOTE]
>
>Informationen zur Zuweisung von Benutzerrollen und Workflows zu bestimmen Benutzertypen finden Sie unter [Informationen zu Projekt-Benutzerrollen](/help/sites-authoring/projects.md#user-roles-in-a-project).

## Workflows für Produkt-Fotoshootings  {#exploring-product-photo-shoot-workflows}

Creative Project bietet mehrere Projektvorlagen, die unterschiedlichen Projektanforderungen gerecht werden. Die Vorlage &quot;Projekt für Produkt-Fotoshooting&quot;ist standardmäßig verfügbar. Diese Vorlage enthält Fotoshooting-Workflows, mit denen Sie Anfragen zu Produktfotos einleiten und verwalten können. Sie enthält darüber hinaus eine Reihe von Aufgaben, die es Ihnen ermöglichen, digitale Bilder für Produkte anhand geeigneter Bewertungs- und Bestätigungsabläufe zu erhalten.

Die Vorlage umfasst die folgenden Workflows:

* **Workflow &quot;Produkt-Fotoshooting (Commerce-Integration)&quot;**: Dieser Workflow nutzt die Commerce-Integration in das PIM-System (Product Information Management), um automatisch eine Aufnahmenliste für die ausgewählten Produkte (Hierarchie) zu erstellen. Sie können die Produktdaten als Teil der Asset-Metadaten anzeigen, nachdem der Workflow abgeschlossen wurde.
* **Workflow &quot;Produkt-Fotoshooting&quot;**: Mit diesem Workflow können Sie eine Aufnahmenliste bereitstellen, anstatt von der Commerce-Integration abhängig zu sein. Dabei werden die hochgeladenen Bilder in einer CSV-Datei im Assets-Ordner des Projekts protokolliert.

>[!NOTE]
>
>Die CSV-Datei, die in die Aufgabe Aufnahmenliste hochladen des Workflows Produkt-Fotoshooting hochgeladen wird, sollte den Dateinamen shotlist.csv haben.

## Erstellen eines Projekts &quot;Produkt-Fotoshooting&quot; {#create-a-product-photo-shoot-project}

1. Im **Projekte** Konsole, tippen/klicken **Erstellen** und wählen Sie dann **Projekt erstellen** aus der Liste.

   ![chlimage_1-132](assets/chlimage_1-132.png)

1. Im **Projekt erstellen** Seite, wählen Sie die Fotoshooting-Projektvorlage aus und tippen/klicken Sie auf **Nächste**.

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. Geben Sie Projektdetails ein, einschließlich Titel, Beschreibung und Fälligkeitsdatum. Fügen Sie Benutzer hinzu und weisen Sie ihnen verschiedene Rollen zu. Sie können auch eine Miniaturansicht für das Projekt hinzufügen.

   ![chlimage_1-134](assets/chlimage_1-134.png)

1. Tippen oder klicken Sie auf **Erstellen**. Eine Bestätigungsmeldung informiert Sie, dass das Projekt erstellt wurde.
1. Tippen/klicken **Fertig** , um zur **Projekte** Konsole. Tippen/klicken Sie alternativ auf **Öffnen** , um die Assets im Fotoshooting-Projekt anzuzeigen.

## Beginn der Arbeit an einem Projekt für Produkt-Fotoshooting {#starting-work-in-a-product-photo-shoot-project}

Um eine Fotoshooting-Anfrage zu starten, tippen oder klicken Sie auf ein Projekt und dann auf **Arbeit hinzufügen** auf der Seite mit den Projektdetails , um einen Workflow zu starten.

![chlimage_1-135](assets/chlimage_1-135.png)

Ein Produkt-Fotoshooting-Projekt umfasst die folgenden vordefinierten Workflows:

* Workflow &quot;Produkt-Fotoshooting (Commerce-Integration)&quot;
* Workflow für Produkt-Fotoshooting

Verwenden Sie den Workflow Produkt-Fotoshooting (Commerce-Integration) zur Zuordnung von Bild-Assets zu den Produkten in AEM. Dieser Workflow nutzt Commerce Integration , um die genehmigten Bilder mit den vorhandenen Produktdaten am Speicherort zu verknüpfen */etc/commerce*.

Der Workflow Produkt-Fotoshooting (Commerce-Integration) umfasst die folgenden Aufgaben:

* Aufnahmenliste erstellen
* Fotoshooting hochladen
* Fotoaufnahme retuschieren
* Überprüfen und genehmigen
* Zu Produktionsaufgabe wechseln

Wenn in AEM keine Produktinformationen verfügbar sind, verwenden Sie den Workflow Produkt-Fotoshooting, um Bild-Assets den Produkten auf der Basis der Informationen zuzuordnen, die Sie in eine CSV-Datei hochladen. Die CSV-Datei muss grundlegende Produktinformationen wie Produkt-ID, Kategorie und Beschreibung enthalten. Der Workflow ruft genehmigte Assets für die Produkte ab.

Dieser Workflow umfasst die folgenden Aufgaben:

* Aufnahmenliste hochladen
* Fotoshooting hochladen
* Fotoaufnahme retuschieren
* Überprüfen und genehmigen
* Zu Produktionsaufgabe wechseln

Sie können diesen Workflow mithilfe der Workflow-Konfigurationsoption anpassen.

Beide Workflows enthalten Schritte zur Verknüpfung von Produkten mit den genehmigten Assets. Jeder Workflow umfasst die folgenden Schritte:

* Workflow-Konfiguration: Beschreibt die Optionen zum Anpassen des Workflows
* Starten eines Projekt-Workflows: Erklärt, wie ein Produkt-Fotoshooting gestartet wird
* Workflow-Aufgabendetails: Enthält Details zu den im Workflow verfügbaren Aufgaben

## Verfolgen des Projektfortschritts {#tracking-project-progress}

Sie können den Fortschritt eines Projekts verfolgen, indem Sie die aktiven/abgeschlossenen Aufgaben innerhalb eines Projekts überwachen.

Verwenden Sie Folgendes, um den Fortschritt eines Projekts zu überwachen:

* **Aufgabenkarte**

* **Aufgabenliste**

Die Aufgabenkarte zeigt den Gesamtfortschritt des Projekts. Sie wird nur dann auf der Seite Projektdetails angezeigt, wenn das Projekt verwandte Aufgaben hat. Auf der Aufgabenkarte wird der aktuelle Abschlussstatus des Projekts basierend auf der Anzahl der abgeschlossenen Aufgaben angezeigt. Zukünftige Aufgaben werden nicht berücksichtigt.

Die Aufgabenkarte enthält die folgenden Details:

* Prozentsatz der aktiven Aufgaben
* Prozentsatz der abgeschlossenen Aufgaben

![chlimage_1-136](assets/chlimage_1-136.png)

Die Aufgabenliste enthält detaillierte Informationen zur derzeit aktiven Workflow-Aufgabe für das Projekt. Um die Liste anzuzeigen, tippen/klicken Sie auf die Aufgabenkarte. In der Aufgabenliste werden auch Metadaten wie Startdatum, Fälligkeitsdatum, Bevollmächtigter, Priorität und Status der Aufgabe angezeigt.

![chlimage_1-137](assets/chlimage_1-137.png)

## Workflow-Konfiguration {#workflow-configuration}

Diese Aufgabe umfasst die Zuweisung von Workflow-Schritten an Benutzer basierend auf ihren Benutzerrollen.

So konfigurieren Sie die **Produkt-Fotoshooting** workflow:

1. Navigieren Sie zu **Werkzeuge** > **Workflows** und tippen Sie anschließend auf den Bereich **Modelle**, um die Seite **Workflow-Modelle** zu öffnen.
1. Wählen Sie den Workflow **Produkt-Fotoshooting** aus und tippen Sie auf der Symbolleiste auf das Symbol **Bearbeiten**, um den Workflow im Bearbeitungsmodus zu öffnen.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. Öffnen Sie auf der Seite **Workflow „Produkt-Fotoshooting“** eine Projektaufgabe. Öffnen Sie z. B. die Aufgabe **Aufnahmenliste hochladen**.

   ![chlimage_1-139](assets/chlimage_1-139.png)

1. Klicken Sie auf **Aufgabe** -Registerkarte, um Folgendes zu konfigurieren:

   * Name der Aufgabe
   * Standardbenutzer (Rolle), der die Aufgabe erhält
   * Standardpriorität der Aufgabe, die in der Aufgabenliste des Benutzers angezeigt wird
   * Aufgabenbeschreibung, die angezeigt wird, wenn der Verantwortliche die Aufgabe öffnet
   * Fälligkeitsdatum für eine Aufgabe, das auf der Grundlage des Zeitpunkts berechnet wird, zu dem die Aufgabe gestartet wurde

1. Klicken **OK** , um die Konfigurationseinstellungen zu speichern.

   Ebenso können Sie die folgenden Aufgaben für die **Produkt-Fotoshooting** workflow:

   * Fotoshooting hochladen
   * Produkt-Fotoshooting retuschieren
   * Fotoshooting-Kommentar
   * Zur Produktion wechseln

   Führen Sie ein ähnliches Verfahren aus, um die Aufgaben im **Workflow &quot;Produkt-Fotoshooting (Commerce-Integration)&quot;**.

In diesem Abschnitt wird beschrieben, wie das Produktinformations-Management in Ihr Creative-Projekt integriert wird.

## Starten eines Projekt-Workflows {#starting-a-project-workflow}

1. Navigieren Sie zu einem Projekt mit einem Produkt-Fotoshooting und tippen/klicken Sie auf das **Arbeit hinzufügen** auf **Workflows** Karte.
1. Wählen Sie die Workflow-Karte **Produkt-Fotoshooting (Commerce-Integration)** aus, um den entsprechenden Workflow zu starten. Wenn die Produktinformationen nicht unter /etc/commerce verfügbar sind, wählen Sie die **Produkt-Fotoshooting** und starten Sie den Workflow Produkt-Fotoshooting .

   ![chlimage_1-140](assets/chlimage_1-140.png)

1. Tippen/klicken **Nächste** , um den Workflow im Projekt zu starten.
1. Geben Sie auf der nächsten Seite Details zum Workflow ein.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   Klicken **Einsenden** , um den Fotoshooting-Workflow zu starten. Die Seite mit den Details zum Fotoshooting-Projekt wird angezeigt.

   ![chlimage_1-142](assets/chlimage_1-142.png)

### Workflow-Aufgabendetails {#workflow-tasks-details}

Der Fotoshooting-Workflow umfasst mehrere Aufgaben. Jede Aufgabe wird basierend auf der für die Aufgabe definierten Konfiguration einer Benutzergruppe zugewiesen.

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

1. Tippen/klicken Sie auf **Zur Aufnahmenliste hinzufügen** -Symbol, um eine CSV-Datei zu erstellen, die eine Liste all dieser Produkte enthält. Eine Meldung bestätigt, dass die Aufnahmenliste für die ausgewählten Produkte erstellt wurde. Klicken **Schließen** , um den Workflow abzuschließen.
1. Nachdem Sie eine Aufnahmenliste erstellt haben, wird die **Aufnahmenliste anzeigen** angezeigt. Um weitere Produkte zur Aufnahmenliste hinzuzufügen, tippen/klicken Sie auf **Zur Aufnahmenliste hinzufügen**. In diesem Fall werden die Daten an die anfangs erstellte Aufnahmenliste angehängt.

   ![chlimage_1-147](assets/chlimage_1-147.png)

1. Tippen/klicken **Aufnahmenliste anzeigen** um die neue Aufnahmenliste anzuzeigen.

   ![chlimage_1-148](assets/chlimage_1-148.png)

   Um die vorhandenen Daten zu bearbeiten oder neue Daten hinzuzufügen, tippen/klicken Sie in der Symbolleiste auf **Bearbeiten**. Sie können nur die Felder **Produkt** und **Beschreibung** bearbeiten.

   ![chlimage_1-149](assets/chlimage_1-149.png)

   Tippen/klicken Sie nach dem Aktualisieren der Datei auf **Speichern** in der Symbolleiste, um die Datei zu speichern.

1. Tippen/klicken Sie nach dem Hinzufügen der Produkte auf das **Fertig** auf der Seite &quot;Aufnahmenliste erstellen&quot;angezeigt, um die Aufgabe als abgeschlossen zu markieren. Sie können einen optionalen Kommentar hinzufügen.

   Nach Abschluss der Aufgabe werden die folgenden Änderungen innerhalb des Projekts eingeführt:

   * Assets, die der Produkthierarchie entsprechen, werden in einem Ordner mit demselben Namen wie der Workflow-Titel erstellt.
   * Die Metadaten für die Assets können über die Konsole &quot;Assets&quot;bearbeitet werden, selbst bevor der Fotograf die Bilder bereitstellt.
   * Es wird ein Ordner &quot;Fotoshooting&quot;erstellt, in dem die vom Fotografen bereitgestellten Bilder gespeichert werden. Der Ordner Fotoshooting enthält Unterordner für jeden Produkteintrag in der Aufnahmenliste.

   Für den Workflow Produkt-Fotoshooting (ohne Commerce-Integration) ist &quot;Aufnahmenliste hochladen&quot;die erste Aufgabe. Tippen/klicken **Aufnahmenliste hochladen** , um **shotlist.csv** -Datei. Die CSV-Datei sollte die Produkt-ID enthalten. Die anderen Felder sind optional. Sie können sie verwenden, um Assets Produkten zuzuordnen.

### Aufnahmenlistenaufgabe hochladen {#upload-shot-list-task}

Diese Aufgabe ist Teil des Produkt-Fotoshooting-Workflows. Diese Aufgabe führen Sie aus, wenn in AEM keine Produktinformationen verfügbar sind. In diesem Fall laden Sie eine Liste von Produkten in eine CSV-Datei hoch, für die Bild-Assets erforderlich sind. Anhand der Informationen in der CSV-Datei ordnen Sie die Bild-Assets den Produkten zu.

Verwenden Sie den Link **Aufnahmenliste anzeigen** unter der Projektkarte im vorherigen Verfahren, um eine Beispieldatei im CSV-Format herunterzuladen. Überprüfen Sie die Beispieldatei, um den üblichen Inhalt einer CSV-Datei zu ermitteln.

Die Produktliste oder die CSV-Datei kann Felder wie **Kategorie, Produkt, ID, Beschreibung** und **Pfad**. Das Feld **ID** ist obligatorisch und enthält die Produkt-ID. Die anderen Felder sind optional.

Ein Produkt kann zu einer bestimmten Kategorie gehören. Die Produktkategorie kann in der CSV-Datei unterhalb der Spalte **Kategorie** aufgeführt werden. Das Feld **Produkt** enthält den Namen des Produkts. Geben Sie im Feld **Beschreibung** die Produktbeschreibung oder Anleitungen für Fotografen ein.

>[!NOTE]
>
>Der Name der hochzuladenden Bilder sollte mit &quot;**&lt;productid>_&quot;** wobei die Produkt-ID über die **ID** im Feld *shotlist.csv* -Datei. Beispielsweise für ein Produkt in der Aufnahmenliste mit **Id 397122** können Sie Dateien mit Namen hochladen **397122_highcontrast.jpg**, **397122_lowlight.png** usw.

1. Tippen oder klicken Sie im Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) um die Liste der Aufgaben im Workflow anzuzeigen.
1. Wählen Sie die **Aufnahmenliste hochladen** und tippen/klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![chlimage_1-150](assets/chlimage_1-150.png)

1. Überprüfen Sie die Aufgabendetails und tippen/klicken Sie dann auf die **Aufnahmenliste hochladen** Schaltfläche.

   ![chlimage_1-151](assets/chlimage_1-151.png)

1. Tippen/klicken Sie auf **Aufnahmenliste hochladen** Schaltfläche zum Hochladen der CSV-Datei mit dem Dateinamen shotlist.csv. Der Workflow erkennt diese Datei als Quelle, die zum Extrahieren von Produktdaten für die nächste Aufgabe verwendet werden kann.
1. Laden Sie eine CSV-Datei hoch, die Produktinformationen im entsprechenden Format enthält. Der Link &quot;Hochgeladene Assets anzeigen&quot;wird unter der Karte angezeigt, nachdem die CSV-Datei hochgeladen wurde.

   ![chlimage_1-152](assets/chlimage_1-152.png)

   Klicken Sie auf das Symbol **Fertig stellen**, um diese Aufgabe abzuschließen.

1. Tippen/klicken Sie auf das Symbol **Fertigstellen**, um die Aufgabe abzuschließen.

### Aufgabe „Fotoshooting hochladen“ {#upload-photo-shoot-task}

Als Redakteur können Sie Aufnahmen für Produkte hochladen, die in der Datei **shotlist.csv** aufgeführt sind, welche in der vorherigen Aufgabe erstellt oder hochgeladen wurde.

Der Name der Bilder, die hochgeladen werden sollen, sollte mit **&quot;&lt;productid>_&quot;** wobei die Produkt-ID über die **ID** im Feld **shotlist.csv** -Datei. Beispiel: für ein Produkt mit **ID 397122** in der Aufnahmenliste können Sie Dateien mit Namen hochladen **397122_highcontrast.jpg**, **397122_lowlight.png** usw.

Sie können entweder die Bilder direkt hochladen oder eine ZIP-Datei hochladen, die die Bilder enthält. Basierend auf ihren Namen werden die Bilder in den jeweiligen Produktordnern innerhalb der **Fotoshooting** Ordner.

1. Tippen/klicken Sie unter dem Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Fotoshooting hochladen** und tippen/klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![chlimage_1-153](assets/chlimage_1-153.png)

1. Tippen/klicken Sie auf &quot;Fotoshooting hochladen&quot;und laden Sie die Fotoshooting-Bilder hoch.
1. Tippen/klicken Sie auf **Fertig** in der Symbolleiste, um die Aufgabe abzuschließen.

### Aufgabe „Fotoaufnahme retuschieren“ {#retouch-photo-shoot-task}

Wenn Sie über Bearbeitungsrechte verfügen, führen Sie die Aufgabe Fotoaufnahme retuschieren aus, um die Bilder zu bearbeiten, die in den Ordner Fotoshooting hochgeladen wurden.

1. Tippen/klicken Sie unter dem Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die Aufgabe **Fotoaufnahme retuschieren** aus und tippen/klicken Sie dann auf der Symbolleiste auf das Symbol **Öffnen**.

   ![chlimage_1-154](assets/chlimage_1-154.png)

1. Tippen/klicken Sie auf **Hochgeladene Assets anzeigen** im **Fotoaufnahme retuschieren** Seite, um die hochgeladenen Bilder zu durchsuchen.

   ![chlimage_1-155](assets/chlimage_1-155.png)

   Falls erforderlich, bearbeiten Sie die Bilder mit einer Adobe Creative Cloud-Applikation.

   ![chlimage_1-156](assets/chlimage_1-156.png)

1. Tippen/klicken Sie auf **Fertig** in der Symbolleiste, um die Aufgabe abzuschließen.

### Aufgabe überprüfen und genehmigen {#review-and-approve-task}

In dieser Aufgabe überprüfen Sie die von einem Fotografen hochgeladenen Fotoshootbilder und markieren Bilder als zur Verwendung freigegeben.

1. Tippen/klicken Sie unter dem Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Überprüfen und genehmigen** und tippen/klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. Im **Überprüfen und genehmigen** , weisen Sie die Überprüfungsaufgabe einer Rolle zu, z. B. &quot;Überprüfer&quot;, und tippen/klicken Sie dann auf &quot;Überprüfen&quot;, um mit der Überprüfung der hochgeladenen Produktbilder zu beginnen.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. Wählen Sie ein Produktbild aus und tippen/klicken Sie in der Symbolleiste auf das Symbol Genehmigen , um es als genehmigt zu markieren.

   ![chlimage_1-159](assets/chlimage_1-159.png)

   Sobald Sie ein Bild genehmigt haben, wird darüber ein „Genehmigt“-Banner angezeigt.

   >[!NOTE]
   Sie können einige Produkte ohne Bilder auslassen. Später können Sie die Aufgabe erneut aufrufen und nach Abschluss markieren.

1. Tippen/klicken **Fertig**. Die bestätigten Bilder werden mit den leeren Assets verknüpft, die erstellt wurden.

Mithilfe der Assets-Benutzeroberfläche können Sie zu den Projekt-Assets navigieren und die genehmigten Bilder überprüfen.

Tippen/klicken Sie auf die nächste Ebene, um Produkte gemäß Ihrer Produktdatenhierarchie anzuzeigen.

Creative Project verbindet bestätigte Assets mit dem referenzierten Produkt. Die Asset-Metadaten werden mit der Produktreferenz und den grundlegenden Informationen auf der Registerkarte &quot;Produktdaten&quot;unter den Asset-Eigenschaften aktualisiert, die im Abschnitt AEM Asset-Metadaten angezeigt werden.

>[!NOTE]
Im Workflow Produkt-Fotoshooting (ohne Commerce-Integration) sind die bestätigten Bilder mit keinen Produkten verbunden.

### Zu Produktionsaufgabe wechseln {#move-to-production-task}

Durch diese Aufgabe werden die genehmigten Assets in den produktionsbereiten Ordner verschoben, damit sie zur Verwendung verfügbar sind.

1. Tippen/klicken Sie unter dem Projektordner auf die Auslassungspunkte im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Zur Produktion wechseln** und tippen/klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. Um die bestätigten Assets für das Fotoshooting vor dem Verschieben in den produktionsbereiten Ordner anzuzeigen, klicken Sie auf den Link **Bestätigte Assets anzeigen** unter der Projektminiatur auf der Aufgabenseite **Zur Produktion wechseln**.

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. Geben Sie den Pfad des produktionsbereiten Ordners im Feld **Verschieben nach** ein.

   ![chlimage_1-162](assets/chlimage_1-162.png)

   Tippen/klicken **Zur Produktion wechseln**. Schließen Sie die Bestätigungsmeldung. Die Assets werden in den genannten Pfad verschoben und für jedes Produkt wird basierend auf der Ordnerhierarchie automatisch ein Rotationsset für die genehmigten Assets erstellt.

1. Tippen/klicken Sie in der Symbolleiste auf das Symbol **Fertig stellen**. Der Workflow wird abgeschlossen, wenn der letzte Schritt als abgeschlossen markiert ist.

## Anzeigen von DAM-Asset-Metadaten {#viewing-dam-asset-metadata}

Nach erfolgter Bestätigung werden die Assets mit den entsprechenden Produkten verknüpft. Die [Eigenschaftenseite](/help/assets/managing-assets-touch-ui.md#editing-properties) der bestätigten Assets weist nunmehr die zusätzliche Registerkarte **Produktdaten** (verknüpfte Produktinformationen) auf. Auf dieser Registerkarte werden die Produktdetails, SKU-Nummer und weitere produktbezogene Details angezeigt, die das Asset verknüpfen. Tippen/klicken Sie auf **Bearbeiten** -Symbol, um eine Asset-Eigenschaft zu aktualisieren. Die produktbezogenen Informationen sind stets schreibgeschützt.

Tippen/klicken Sie auf den angezeigten Link, um zur entsprechenden Produktdetailseite in der Produktkonsole zu navigieren, mit der das Asset verknüpft ist.

## Anpassen der Workflows für Projekt-Fotoshootings {#customizing-the-project-photo-shoot-workflows}

Sie können die Workflows für Projekt-Fotoshootings basierend auf Anforderungen anpassen. Dies ist eine optionale rollenbasierte Aufgabe, die Sie ausführen, um den Wert einer Variablen innerhalb des Projekts festzulegen. Später können Sie dann den konfigurierten Wert verwenden, um zu einer Entscheidung zu gelangen.

1. Klicken/tippen Sie auf das AEM und navigieren Sie dann zu **Instrumente** > **Workflow** > **Modelle** , um die Seite &quot;Workflow-Modelle&quot;zu öffnen.
1. Wählen Sie die **Produkt-Fotoshooting (Commerce-Integration)** oder **Produkt-Fotoshooting** und klicken/tippen Sie auf **Bearbeiten** in der Symbolleiste, um den Workflow im Bearbeitungsmodus zu öffnen.
1. Öffnen Sie die **Projekte** Aufgaben im Sidekick und ziehen Sie die **Rollenbasierte Projektaufgabe erstellen** in den Workflow.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Öffnen Sie den Schritt **Rollenbasierte Aufgabe**.
1. Im **Aufgabe** Geben Sie einen Namen für die Aufgabe an, die im **Aufgabe** Liste. Sie können die Aufgabe auch einer Rolle zuweisen, die Standardpriorität festlegen, eine Beschreibung angeben und einen Fälligkeitszeitpunkt für die Aufgabe bestimmen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Im **Routing** Registerkarte die Aktionen für die Aufgabe angeben. Um mehrere Aktionen hinzuzufügen, tippen/klicken Sie auf den Link &quot;Element hinzufügen&quot;.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Klicken Sie nach dem Hinzufügen der Optionen auf **OK**, um die Änderungen zum Schritt hinzuzufügen.

   >[!NOTE]
   Tippen/Klicken **OK** speichert die Änderungen nicht im Workflow. Um Änderungen im Workflow zu speichern, tippen/klicken Sie auf **Speichern**.

1. Öffnen Sie die **Workflow** Aufgaben aus dem Sidekick und fügen Sie eine **Goto** Aufgabe.
1. Öffnen Sie die **Goto** Aufgabe und tippen/klicken Sie auf **Prozess** Registerkarte.
1. Geben Sie den folgenden Code im **Skript** Feld:

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

1. Tippen/klicken **OK**.

1. Tippen/klicken **Speichern** , um den Workflow zu speichern.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Nach der [Zur Produktionsaufgabe wechseln](#move-to-production-task) ist abgeschlossen und wird dem Eigentümer zugewiesen.

   Die Benutzerin oder der Benutzer mit der Eigentümerrolle kann die Aufgabe abschließen und eine Aktion (in der Liste der in den Workflow-Schrittkonfigurationen hinzugefügten Aktionen) in der Liste im Kommentar-Popup auswählen.

   ![chlimage_1-168](assets/chlimage_1-168.png)

   Wählen Sie die entsprechende Option aus und klicken Sie auf **Fertig** zum Ausführen der **Zum Schritt wechseln** im Workflow.

>[!NOTE]
Wenn Sie einen Server starten, speichert das Servlet für die Projektaufgabenliste die Zuordnungen zwischen Aufgabentypen und den unter `/libs/cq/core/content/projects/tasktypes` definierten URLs im Zwischenspeicher. Sie können danach die übliche Überlagerung durchführen und benutzerdefinierte Aufgabentypen hinzufügen, indem Sie sie unter `/apps/cq/core/content/projects/tasktypes` ablegen.
