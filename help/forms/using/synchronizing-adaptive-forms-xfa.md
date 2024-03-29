---
title: Synchronisieren von adaptiven Formularen mit XFA-Formularvorlagen
seo-title: Synchronizing Adaptive Forms with XFA Form Templates
description: Synchronisieren von adaptiven Formularen mit XFA-/XDP-Dateien.
seo-description: Synchronizing Adaptive forms with XFA/XDP files.
uuid: 6613a9bf-c862-4c18-a5b5-f574d301e936
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 29c0a78c-53b5-4ce7-a2f3-63e1b089b0d0
feature: Adaptive Forms
exl-id: 014c735e-84f8-4cdb-979e-bfab24b3f666
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1191'
ht-degree: 64%

---

# Synchronisieren von adaptiven Formularen mit XFA-Formularvorlagen {#synchronizing-adaptive-forms-with-xfa-form-templates}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Sie können adaptive Formulare basierend auf einer XFA-Formularvorlage (`*.XDP`-Datei) erstellen. Diese Wiederverwendung ermöglicht es Ihnen, Ihre in vorhandene XFA-Formulare getätigten Investitionen mehrmals zu nutzen. Informationen dazu, wie Sie eine XFA-Formularvorlage zum Erstellen eines adaptiven Formulars verwenden, finden Sie unter [Erstellen eines adaptiven Formulars basierend auf einer Vorlage](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p).

Sie können Felder aus der XDP-Datei in Ihrem adaptiven Formular wiederverwenden. Diese Felder werden als gebundene Felder bezeichnet. Die Eigenschaften der gebundenen Felder (z. B. Skripte, Beschriftungen und Anzeigeformat) werden aus der XDP-Datei kopiert. Sie können sich auch dafür entscheiden, die Werte einiger dieser Eigenschaften zu überschreiben.

AEM Forms bietet eine Möglichkeit, die Felder der adaptiven Formulare mit allen Änderungen zu synchronisieren, die später an den entsprechenden Feldern in der XDP-Datei vorgenommen werden. In diesem Artikel wird beschrieben, wie Sie diese Synchronisierung aktivieren können.

![Sie können Felder aus einem XFA-Formular in ein adaptives Formular ziehen.](assets/drag-drop-xfa.gif.gif)

In der AEM Forms-Authoring-Umgebung können Sie Felder aus einem XFA-Formular (links) in ein adaptives Formular (rechts) ziehen.

## Voraussetzungen {#prerequisites}

Um die Informationen in diesem Artikel nutzen zu können, sollten Sie mit den folgenden Themen vertraut sein:

* [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md)

* XFA (XML Forms Architecture)

Um die Assets für das Beispiel im Artikel zu verwenden, laden Sie das Beispielpaket wie im nächsten Abschnitt ([Beispielpaket](/help/forms/using/synchronizing-adaptive-forms-xfa.md#p-sample-package-p)) beschrieben herunter.

## Beispielpaket {#sample-package}

In diesem Artikel wird anhand eines Beispiels gezeigt, wie das adaptive Formular mit einer aktualisierten XFA-Formularvorlage synchronisiert wird. Die im Beispiel verwendeten Assets sind in einem Paket verfügbar, das aus dem Abschnitt [Downloads](/help/forms/using/synchronizing-adaptive-forms-xfa.md#p-downloads-p) in diesem Artikel heruntergeladen werden kann.

Nach dem Hochladen des Pakets können Sie diese Assets in der Benutzeroberfläche von AEM Forms anzeigen.

Installieren Sie das Paket mit dem Package Manager: `https://<server>:<port>/crx/packmgr/index.jsp`

Das Paket enthält die folgenden Assets:

1. `sample-form.xdp`: Die als Beispiel verwendete XFA-Formularvorlage

1. `sample-xfa-af`: Das adaptive Formular, das auf der Datei sample-form.xdp basiert. Dieses adaptive Formular enthält jedoch keine Felder. Im nächsten Schritt fügen wir diesem adaptiven Formular Inhalt hinzu.

### Hinzufügen von Inhalt zu einem adaptiven Formular {#add-content-to-adaptive-form-br}

1. Navigieren Sie zu https://&lt;server>:&lt;port>/aem/forms.html. Geben Sie auf Anfrage Ihre Anmeldedaten ein.
1. Öffnen Sie sample-af-xfa zur Bearbeitung im Autorenmodus.
1. Wählen Sie im Inhaltsbrowser in der Seitenleiste die Registerkarte Datenmodellobjekte . Ziehen Sie NumericField1 und TextField1 auf das adaptive Formular.
1. Ändern Sie den Titel von „NumericField1“ von **Numerisches Feld** zu **Numerisches AF-Feld**.

>[!NOTE]
>
>In den vorangegangenen Schritten haben wir eine Eigenschaft eines Felds in der XDP-Datei überschrieben. Diese Eigenschaft wird daher nicht synchronisiert, wenn die entsprechende Eigenschaft in der XDP-Datei später geändert wird.

## Erkennen von Änderungen in der XDP-Datei {#detecting-changes-in-xdp-file}

Bei jeder Änderung in einer XDP-Datei oder einem Fragment kennzeichnet die AEM Forms-Benutzeroberfläche alle adaptiven Formulare, die auf der XDP-Datei oder dem Fragment basieren.

Nachdem Sie eine XDP-Datei aktualisiert haben, müssen Sie sie erneut in die AEM Forms-Benutzeroberfläche hochladen, damit die Änderungen gekennzeichnet werden.

Als Beispiel aktualisieren wir die Datei `sample-form.xdp` mithilfe der folgenden Schritte:

1. Navigieren Sie zu `https://<server>:<port>/projects.html.`. Geben Sie bei Aufforderung Ihre Anmeldedaten ein.
1. Klicken Sie links auf die Registerkarte „Formulare“.
1. Laden Sie die Datei `sample-form.xdp` auf Ihren lokalen Computer herunter. Die XDP-Datei wird als `.zip`-Datei heruntergeladen, die mit einem beliebigen Entpackprogramm extrahiert werden kann.

1. Öffnen Sie die Datei `sample-form.xdp` und ändern Sie den Titel des Felds „TextField1“ von **Textfeld** zu **Mein Textfeld**.

1. Laden Sie die Datei `sample-form.xdp` wieder in die AEM Forms-Benutzeroberfläche hoch.

Wenn eine XDP-Datei aktualisiert wird, wird ein Symbol im Editor angezeigt, wenn Sie die adaptiven Formulare bearbeiten, die auf der XDP-Datei basieren. Dieses Symbol zeigt an, dass das adaptive Formular nicht mit der XDP-Datei synchronisiert ist. In der folgenden Abbildung sehen Sie das Symbol links in der Randleiste angezeigt.

![Symbol, das angibt, dass das adaptive Formular nicht mehr mit der XDP-Datei synchron ist](assets/sync-af-xfa.png)

## Synchronisieren von adaptiven Formularen mit der neuesten XDP-Datei {#synchronizing-adaptive-forms-with-the-latest-xdp-file}

Wenn ein adaptives Formular, das nicht mehr mit der XDP-Datei synchron ist, zum nächsten Mal für das Authoring geöffnet wird, wird die folgende Meldung angezeigt: **Schema/Form Template for the Adaptive Form has been updated. `Click Here` to rebase it with the new version.** (Schema/Formularvorlage für das adaptive Formular wurde geändert. Klicken Sie hier, um ein Rebase mit der neuen Version auszuführen.)

Durch Klicken auf die Meldung werden die Felder im adaptiven Formular mit den entsprechenden Feldern in der XDP-Datei synchronisiert.

Öffnen Sie für das in diesem Artikel verwendete Beispiel `sample-xfa-af` im Autorenmodus. Die Meldung wird am unteren Rand des adaptiven Formulars angezeigt.

![Meldung, die Sie auffordert, das adaptive Formular mit der XDP-Datei zu synchronisieren](assets/sync-af-xfa-1.png)

### Aktualisieren der Eigenschaften {#updating-the-properties}

Alle Eigenschaften, die aus der XDP-Datei in das adaptive Formular kopiert wurden, werden aktualisiert, mit Ausnahme der Eigenschaften, die explizit vom Autor im adaptiven Formular (aus dem Komponentendialogfeld) überschrieben wurden. Die Liste der Eigenschaften, die aktualisiert wurden, ist in den Serverprotokollen verfügbar.

Um die Eigenschaften im adaptiven Formular des Beispiels zu aktualisieren, klicken Sie auf den Link (mit `"Click Here"` gekennzeichnet) in der Nachricht. Der Titel von „TextField1“ ändert sich von **Textfeld** zu **Mein Textfeld**.

![update-property](assets/update-property.png)

>[!NOTE]
>
>Die Beschriftung „AF Numeric Field“ wurde nicht geändert, da Sie diese Eigenschaft im Dialogfeld für die Komponenteneigenschaften überschrieben haben, wie in [Hinzufügen von Inhalten zu adaptiven Formularen](#p-add-content-to-adaptive-form-br-p) beschrieben.

### Hinzufügen neuer Felder aus der XDP-Datei zum adaptiven Formular   {#adding-new-fields-from-xdp-file-to-adaptive-form-nbsp}

Alle Felder, die später zur ursprünglichen XDP-Datei hinzugefügt werden, werden auf der Registerkarte &quot;Formularhierarchie&quot;angezeigt und Sie können diese neuen Felder in das adaptive Formular ziehen.

Sie müssen nicht auf den Link in der Fehlermeldung klicken, um die Felder in der Registerkarte „Formularhierarchie“ zu aktualisieren.

### Gelöschte Felder in der XDP-Datei {#deleted-fields-in-xdp-file}

Wenn ein Feld, das zuvor in ein adaptives Formular kopiert wurde, aus einer XDP-Datei gelöscht wird, wird im Authoring-Modus eine Fehlermeldung angezeigt, die besagt, dass das Feld nicht in der XDP-Datei vorhanden ist. In diesem Fall müssen Sie das Feld manuell aus dem adaptiven Formular löschen oder die Eigenschaft `bindRef` im Komponentendialogfeld löschen.

Die folgenden Schritte veranschaulichen diesen Vorgang für die Assets, die in dem Beispiel in diesem Artikel verwendet wurden:

1. Aktualisieren Sie die Datei `sample-form.xdp` und löschen Sie „NumericField1“.
1. Laden Sie die Datei `sample-form.xdp` in die AEM Forms-Benutzeroberfläche hoch.
1. Öffnen Sie das adaptive Formular `sample-xfa-af` zum Authoring. Die folgende Fehlermeldung wird angezeigt: „Schema/Form Template for the Adaptive Form has been updated.“ `Click Here` to rebase it with the new version (Schema/Formularvorlage für das adaptive Formular wurde geändert. Klicken Sie hier, um ein Rebase mit der neuen Version auszuführen.)

1. Klicken Sie auf den (mit „`Click Here`“ beschrifteten) Link in der Meldung. Eine Fehlermeldung wird angezeigt, die besagt, dass das Feld in der XDP-Datei nicht mehr vorhanden ist.

![Fehler, der angezeigt wird, wenn Sie ein Element in der XDP-Datei löschen](assets/no-element-xdp.png)

Das gelöschte Feld wird außerdem mit einem Symbol gekennzeichnet, um einen Fehler im Feld anzuzeigen.

![Fehlersymbol in dem Feld](assets/error-field.png)

>[!NOTE]
>
>Die Felder im adaptiven Formular, die eine inkorrekte Bindung aufweisen (einen ungültigen `bindRef`-Wert im Bearbeitungsdialogfeld) werden ebenfalls als gelöschte Felder betrachtet. Wenn der Autor diese Fehler nicht behebt und das adaptive Formular veröffentlicht, wird das Feld als normales ungebundenes adaptives Formularfeld behandelt und in den unbinded-Abschnitt der Ausgabe-XML-Datei aufgenommen.

## Downloads {#downloads}

Inhaltspaket für das Beispiel in diesem Artikel

[Datei laden](assets/sample-xfa-af-sync-1.0.zip)
