---
title: Adaptive Formularvorlagen
seo-title: Adaptive Form Templates
description: Erstellen Sie Vorlagen für adaptive Formulare, indem Sie die grundlegende Struktur und den anfänglichen Formularinhalt mithilfe des Vorlagen-Editors definieren.
seo-description: Create adaptive form templates by defining the basic structure and initial form content using the Template Editor.
uuid: d011bf78-931d-4865-bce5-4328c39402b2
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 155aaf96-1e9c-4e73-8e43-d96878d69b16
feature: Adaptive Forms
exl-id: 8bb350f2-a160-4943-bd6a-00f87f4e6cbc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1999'
ht-degree: 52%

---

# Adaptive Formularvorlagen {#adaptive-form-templates}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Sie ein Formular erstellen, fügen Sie Felder und Komponenten hinzu, um Formularstruktur, Inhalt und Aktionen im Editor zu definieren. Sie können Felder und Komponenten im`guideRootPanel` des Formularcontainers hinzufügen. Mit dem Vorlagen-Editor können Sie eine Vorlage erstellen, die eine grundlegende Struktur und anfänglichen Inhalt enthält, die Autoren zum Erstellen von Formularen verwenden können.

Beispiel: Sie möchten, dass alle Autoren in einem Registrierungsformular bestimmte Textfelder, Navigationsschaltflächen und eine Schaltfläche zum Senden verwenden. Sie können eine Vorlage mit den Komponenten erstellen, die Autoren verwenden können, damit ihr Formular konsistent mit anderen Registrierungsformularen ist. Wenn Autoren die Vorlage zum Erstellen eines adaptiven Formulars verwenden, übernimmt das neue Formular die Struktur und die Komponenten, die Sie in der Vorlage angegeben haben. Mit dem Vorlagen-Editor können Sie:

* Fügen Sie Kopf- und Fußzeilenkomponenten eines Formulars in der Strukturebene hinzu.
* Den anfänglichen Inhalt für das Formular angeben.
* Geben Sie ein Design und Übermittlungsaktionen an.

## Arbeiten mit Vorlagen {#working-with-templates}

Sie können über das Menü Tools auf den Vorlagen-Editor zugreifen, indem Sie zu **[!UICONTROL Adobe Experience Manager > Tools > Vorlagen]**. Hier befinden sich die Vorlagen in Ordnern für bearbeitbare Vorlagen. AEM bietet einen globalen Ordner zum Organisieren von Vorlagen. Er ist jedoch nicht standardmäßig aktiviert. Sie können Ihren Administrator auffordern, den Ordner global zu aktivieren oder einen neuen Ordner für Vorlagen zu erstellen. Weitere Informationen zum Erstellen von Ordnern finden Sie unter [Vorlagenordner](/help/sites-developing/page-templates-editable.md).

Sobald Sie auf einen Ordner tippen, um ihn zu öffnen, wird eine Schaltfläche „Erstellen“ angezeigt, mit der Sie eine neue Vorlage für adaptive Formulare erstellen können.

### Erstellen einer Vorlage {#create-template}

Nachdem Sie einen Ordner erstellt haben, öffnen Sie den Ordner und führen Sie die folgenden Schritte aus, um eine Vorlage zu erstellen:

1. In der Vorlagenkonsole tippen Sie im erstellten Ordner auf **[!UICONTROL Erstellen]**.
1. Wählen Sie im Abschnitt „Vorlagentyp wählen“ **[!UICONTROL Adaptive Formularvorlage]** und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie im Abschnitt „Vorlagendetails“ einen Namen für die Vorlage an und tippen Sie auf **[!UICONTROL Erstellen]**.

   Sie können eine Beschreibung und eine Miniaturansicht hinzufügen, die angezeigt wird, wenn Sie die erstellte Vorlage beim Formular-Authoring auswählen.

1. Tippen Sie auf **[!UICONTROL Fertig]**, um zur Konsole zurückzukehren, oder auf **[!UICONTROL Öffnen]**, um die Vorlage im Editor zu öffnen.

### Benutzeroberfläche des Vorlageneditors {#template-editor-ui}

Wenn Sie eine Vorlage zum Bearbeiten öffnen, können Sie die folgenden AEM-Editor-Komponenten sehen:

* **Seitensymbolleiste**: Enthält die folgenden Optionen:

   * **Seitliches Bedienfeld ein/aus**: Hier können Sie die Seitenleiste ein- oder ausblenden.
   * **Seiteninformationen**: Ermöglicht Ihnen die Angabe von Informationen wie dem Zeitpunkt der Veröffentlichung oder der Zurücknahme der Veröffentlichung, Miniaturen, Client-seitigen Bibliotheken, einer Seitenrichtlinie und dem Seiten-Design einer Client-seitigen Bibliothek.
   * **Emulator**: Hier können Sie das Erscheinungsbild für verschiedene Geräte simulieren und anpassen.
   * **Ebenenselektor**: Hiermit können Sie die Ebene ändern.

      Sie können die Ebene **Struktur** oder die Ebene **Anfänglicher Inhalt** auswählen. In der Ebene „Struktur“ können Sie die Kopf- und Fußzeile hinzufügen und anpassen. In der Ebene „Anfänglicher Inhalt“ können Sie den Formularinhalt anpassen.

   * **Vorschau**: Hier können Sie das Aussehen der Vorlage bei Veröffentlichung in einer Vorschau simulieren. Sie können den Ebenenselektor und die Vorschau verwenden, um zwischen Bearbeitungs- und Vorschau-Modus zu wechseln.

* **Seitenleiste**: Enthält Inhalts-, Eigenschaften-, Elemente- und Komponenten-Browser.
* **Komponenten-Symbolleiste**: Wenn Sie eine Komponente auswählen, sehen Sie eine Symbolleiste, in der Sie die Komponente anpassen können.
* **Seite**: Der Bereich, in dem Sie Inhalt hinzufügen, um die Vorlage zu erstellen.

Weitere Informationen zum Touch UI-Editor finden Sie unter [Einführung in das Authoring adaptiver Formulare.](/help/forms/using/introduction-forms-authoring.md)

### Bearbeiten einer Vorlage {#editing-a-template}

Eine adaptive Formularvorlage wird mit zwei Ebenen erstellt:

* Struktur
* Anfänglicher Inhalt

Der Ebenenselektor ist neben der Option Vorschau in der oberen rechten Ecke des Bildschirms verfügbar.

### Struktur {#structure}

Wenn Sie die Strukturebene im Vorlageneditor auswählen, werden die Layout-Container über und unter dem Container für adaptive Formulare angezeigt. Autoren können diese Layout-Container für Kopf- und Fußzeilen verwenden. Sie können die Kopf- und Fußzeile hinzufügen, bearbeiten oder anpassen. Ziehen Sie die Kopfzeilenkomponente des adaptiven Formulars in den Layout-Container über dem Container des adaptiven Formulars, um die Vorlagenkopfzeile anzupassen. Ziehen Sie die Fußzeilenkomponente des adaptiven Formulars in den Layout-Container unter den Container des adaptiven Formulars, um die Vorlagenfußzeile anzupassen.

![Layout-Container in der Strukturebene](assets/header-layer-selector.png)

**Abbildung:** *Layout-Container in der Strukturebene*

**A.** Layout-Container für die Kopfzeilenkomponente **B.** Layout-Container für die Fußzeilenkomponente

Ziehen Sie die Kopfzeilenkomponente des adaptiven Formulars in den Layout-Container über dem Container des adaptiven Formulars. Nachdem Sie die Komponente hinzugefügt haben, können Sie deren Eigenschaften festlegen, mit denen Sie ein Logo hinzufügen und dessen Titel angeben können.

Wenn Sie die Fußzeilenkomponente in den Layout-Container unter dem Container des adaptiven Formulars ziehen, können Sie ebenso Urheberrechtsinformationen und Unternehmensdetails angeben.

![Kopf- und Fußzeile in der Strukturebene hinzugefügt](assets/header-and-footer.png)

**Abbildung:** *Kopf- und Fußzeile in der Strukturebene hinzugefügt*

#### Sperren/Entsperren von Komponenten in der Strukturebene {#locking-unlocking-components-in-the-structure-layer}

Wenn Sie die Vorlage bearbeiten, wenn die Strukturebene ausgewählt ist, können Sie die Kopf- und Fußzeile der Vorlage entsperren. Wenn eine Komponente in der Vorlage entsperrt ist, können Formularautoren die Komponente im adaptiven Formular bearbeiten, das die Vorlage verwendet. Das Sperren einer Komponente verhindert, dass Formularautoren sie im adaptiven Formular bearbeiten. Die Sperroption ist in der Komponenten-Symbolleiste verfügbar.

Beispielsweise können Sie die Kopfzeilenkomponente zur Vorlage hinzufügen. Wenn Sie die Komponente auswählen, wird in der Komponenten-Symbolleiste eine Sperroption angezeigt. In der Regel enthält die Kopfzeile den Firmennamen und das Logo und Sie möchten nicht, dass Formularautoren das Logo und die Kopfzeile in einer Vorlage ändern. In einem adaptiven Formular, das mit der Vorlage erstellt wurde, in der die Kopfzeilenkomponente gesperrt ist, können Formularautoren das Logo und den Unternehmensnamen nicht ändern.

>[!NOTE]
>
>Das einzelne Sperren oder Entsperren von Bildern oder Logos in der Kopfzeilenkomponente wird nicht empfohlen. Sie können die Kopfzeilenkomponente entsperren.

### Anfänglicher Inhalt {#initial-content}

Wenn die Option Anfänglicher Inhalt ausgewählt ist, wird der Container des adaptiven Formulars der Vorlage wie ein adaptives Formular zur Bearbeitung geöffnet. Wie beim Authoring eines adaptiven Formulars können Sie anfängliche Einstellungen festlegen, z. B. ein Design und Übermittlungsaktionen.

Formularverfasser verwenden es als Grundlage zum Erstellen eines Formulars. Die Struktur des Inhaltsflusses wird in der Ebene Anfänglicher Inhalt der Vorlage angegeben. Um zum Bearbeiten des anfänglichen Inhalts der Formularvorlage zu wechseln, bevor Sie die Vorschau in der Seitensymbolleiste anzeigen, tippen Sie auf ![canvas-drop-down](assets/canvas-drop-down.png)**[!UICONTROL  > Anfänglicher Inhalt ]**.

![Ebene „Anfänglicher Inhalt“ im Vorlageneditor](assets/initial-content-layer.png)

In der Ebene „Anfänglicher Inhalt“ im Vorlageneditor ist der Container des adaptiven Formulars zum Festlegen von Eigenschaften ausgewählt.

Auf der Ebene Anfänglicher Inhalt erstellen Sie die adaptive Formularvorlage, die Ihre Autoren als Grundlage verwenden. Das Erstellen einer Vorlage ähnelt dem Erstellen eines Formulars. Sie verwenden die in der Seitenleiste verfügbaren Optionen. Die Seitenleiste bietet Browser für Inhalte, Eigenschaften, Assets und Komponenten.

Weitere Informationen finden Sie unter [Randleiste](/help/forms/using/introduction-forms-authoring.md#sidebar).

>[!NOTE]
>
>Wenn Sie als Übermittlungsaktion „Inhalt speichern“ oder „PDF speichern“ auswählen, wird die Option zum Angeben des Speicherpfads angezeigt. Wenn Sie den Pfad in der Vorlage angeben, haben alle daraus erstellten Formulare denselben Pfad. Sie können den richtigen Speicherpfad angeben oder sicherstellen, dass Formularautoren ihn aktualisieren, um zu verhindern, dass Daten aus jedem Formular an demselben Speicherort gespeichert werden.

#### Erstellen einer Vorlage für ein adaptives Formular mit Registerkarten und Bedienfeldern  {#creating-an-adaptive-form-template-with-tabs-and-panels-nbsp}

Sie möchten beispielsweise eine Vorlage mit den folgenden Registerkarten erstellen:

* Allgemeine Informationen
* Berufliche Informationen

Sie haben ein Logo hinzugefügt, einen Titel angegeben und eine Fußzeile in der Strukturebene hinzugefügt. Sperren Sie die Kopf- und Fußzeile, damit Autoren sie nicht bearbeiten, wenn sie die Vorlage zum Erstellen von Formularen verwenden.

Ändern Sie die Ebene von Struktur in Anfänglicher Inhalt und beginnen Sie mit dem Hinzufügen von Inhalt zum Formular. Um eine Struktur mit Registerkarten zu erstellen, fügen Sie ein untergeordnetes Bedienfeld im guideRootPanel des Containers für adaptive Formulare hinzu. So fügen Sie einen Bereich hinzu:

* Sie können ein Bedienfeld hinzufügen, indem Sie auf die Schaltfläche **+** tippen, wenn Sie die Option **Komponenten hierher ziehen** auswählen.

* Sie können die Bedienfeldkomponente aus dem Komponenten-Browser in der Seitenleiste ziehen.
* Sie können ein untergeordnetes Bedienfeld von `guideRootPanel` aus der Symbolleiste hinzufügen.

Um die Registerkarten „Allgemeine Informationen“ und „Berufliche Informationen“ zu erstellen, fügen Sie zwei Bedienfelder im untergeordneten Bedienfeld von `guideRootPanel` hinzu. Wählen Sie die Bedienfelder aus und tippen Sie auf ![cmppr](assets/cmppr.png), um die Eigenschaften in der Seitenleiste zu öffnen. Ändern Sie die Elementnamen in `general-info` und `professional-info` und die Titel in „Allgemeine Informationen“ bzw. „Berufliche Informationen“. Klicken Sie in der Randleiste auf „Inhalt“, um den Inhalts-Browser zu öffnen. Wählen Sie in der Registerkarte „Formularobjekte“ `guideRootPanel` aus. Im Editor ist „guideRootPanel“ ausgewählt. Tippen Sie auf ![cmppr](assets/cmppr.png) in der Komponenten-Symbolleiste, um dessen Eigenschaften zu öffnen. Wählen Sie im Feld „Bedienfeldlayout“ **Registerkarten oben** und tippen Sie dann auf **Fertig**. Die Vorlagenstruktur mit Registerkarten wird angewendet.

#### Hinzufügen von Inhalten in Registerkarten {#adding-content-in-tabs}

![Hinzufügen von Feldern in Vorlagen für adaptive Formulare](assets/template-edit-initial-content.png)

Felder in der Vorlage hinzufügen

Nachdem Sie Bedienfelder hinzugefügt und als Registerkarten strukturiert haben, können Sie Felder in den Registerkarten hinzufügen. Wenn Sie eine Registerkarte im Editor auswählen, wird die **[!UICONTROL Komponenten hierher ziehen]** -Option. Sie können Komponenten wie Textboxen, Listenelemente und Schaltflächen per Drag-and-Drop verschieben. Sie können Komponenten aus dem Komponenten-Browser in die Seitenleiste ziehen und dort ablegen.

Jede Komponente verfügt über Eigenschaften, die die Datenerfassung und -bearbeitung verbessern. Beispielsweise können Sie die Eigenschaft **[!UICONTROL Erforderliches Feld]** einer Komponente aktivieren. Ihre Autoren können eine Nachricht angeben, die Ihre Kunden sehen, wenn sie das Ausfüllen eines erforderlichen Felds überspringen. Geben Sie die Meldung in der Eigenschaft **[!UICONTROL Erforderliches Feld]** an.

In der Beispielvorlage werden die Felder Name, Telefonnummer und Geburtsdatum im Tab Allgemeine Informationen hinzugefügt. Im Tab Berufliche Informationen werden die Felder Aktuell beschäftigt, Beschäftigungstyp und Bildungsabschluss hinzugefügt.

Nachdem Sie Felder hinzugefügt haben, können Sie Schaltflächen wie „Senden“ und „Zurücksetzen“ hinzufügen.

### Aktivieren der Vorlage {#enabling-the-template}

Wenn Sie eine Vorlage erstellen, wird sie als Entwurf hinzugefügt. Aktivieren Sie die Vorlage, um sie zum Erstellen adaptiver Formulare zu verwenden. Aktivieren einer Vorlage:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager > Werkzeuge > Vorlagen]** und öffnen Sie den Ordner, in dem Sie die Vorlage erstellt haben.

1. Die Vorlage, die Sie erstellt haben, ist als Entwurf gekennzeichnet.
1. Wählen Sie die Vorlage aus und tippen Sie auf **[!UICONTROL Aktivieren]** in der Symbolleiste.

   Wenn Sie ein adaptives Formular erstellen, wird die Vorlage aufgeführt, wenn Sie aufgefordert werden, eine Vorlage auszuwählen.

## Importieren oder Exportieren einer Vorlage {#importing-or-exporting-a-template}

Ein Formular funktioniert mit seiner Vorlage. Wenn Sie ein adaptives Formular herunterladen, das mit einer benutzerdefinierten Vorlage erstellt wurde, wird die Vorlage nicht heruntergeladen. Wenn Sie das Formular in eine andere AEM Forms-Instanz importieren, wird es ohne Vorlage importiert. Wenn ein Formular importiert wird, aber die Vorlage nicht verfügbar ist, wird das Formular nicht gerendert. Es ist auch möglich, die benutzerdefinierte Vorlage vom `/conf`-Knoten in `https://<server>:<port>/crx/packmgr` zu verpacken und es in die AEM Forms-Instanz zu importieren, in die Sie das Formular hochladen möchten.

## Erstellen eines adaptiven Formulars mithilfe der Vorlage {#creating-an-adaptive-form-using-the-template}

Nachdem Sie eine Vorlage erstellt und aktiviert haben, ist sie im Forms Manager verfügbar, wenn Sie ein adaptives Formular erstellen. Informationen zum Verwenden einer Vorlage und Erstellen eines adaptiven Formulars finden Sie unter [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md).

## Ändern der Anzeigeoption von nativen Vorlagen  {#change-display-option-of-out-of-the-box-templates}

Sie können benutzerdefinierte Vorlagen für adaptive Formulare erstellen, um die grundlegende Struktur und den anfänglichen Inhalt zu definieren. AEM Forms bietet außerdem eine Standardvorlage für adaptive Formulare. Sie können wählen, ob Sie die Vorlagen anzeigen oder ausblenden möchten.

Führen Sie die folgenden Schritte aus, um Vorlagen ein- und auszublenden:

1. Melden Sie sich bei der Autor-Instanz von AEM Forms an und navigieren Sie zu **[!UICONTROL Tools >  Vorgänge >  Web-Konsole]**.

   >[!NOTE]
   >
   >Die URL AEM Webkonsole lautet `https://[server]:[port]/system/console/configMgr`

1. Suchen und öffnen Sie die **[!UICONTROL FormsManager-Konfigurations]** einstellungen:

   * Um die adaptiven Formularvorlage ein- oder auszublenden, aktivieren oder deaktivieren Sie die Option **Einbeziehen der standardmäßigen AF- und AD-Vorlagen**.
   * Um die adaptiven Formularvorlage, die in AEM 6.0 Forms oder AEM 6.1 Forms hinzugefügt wurden, jetzt aber veraltet sind, ein- oder auszublenden, aktivieren oder deaktivieren Sie die Option **Einbeziehen der AEM 6.0 AF-Vorlagen**. Wenn diese Option aktiviert ist, muss die **[!UICONTROL Vordefinierte AF- und AD-Vorlagen einschließen]** Konfiguration zu aktivieren.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Die Anzeigeoptionen für die vordefinierten Vorlagen werden geändert.

## Empfehlungen {#recommendations}

* Wenn Sie Eigenschaften des Formulars im Vorlageneditor ändern, verwenden Sie nicht die Eigenschaft „BindReference“.
* Wenn Sie einen Haltepunkt hinzufügen möchten, erstellen Sie ihn, wenn Sie eine Vorlage für ein adaptives Formular bearbeiten.

   Weitere Informationen zu Haltepunkten finden Sie unter [Responsive Layout](/help/sites-authoring/responsive-layout.md).
