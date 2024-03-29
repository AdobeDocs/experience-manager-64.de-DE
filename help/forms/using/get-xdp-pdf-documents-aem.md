---
title: Übernehmen von XDP- und PDF-Dokumenten in AEM Forms
seo-title: Getting XDP and PDF documents in AEM Forms
description: Mit AEM Forms können Sie Formulare und unterstützte Assets hochladen, um sie mit adaptiven Formularen zu verwenden. Sie können Formulare und zugehörige Ressourcen auch per Massen-Upload als ZIP-Datei hochladen.
seo-description: AEM Forms allows you to upload forms and supported assets to use with adaptive forms. You can also bulk upload forms and related resources as a ZIP.
uuid: c2a86d89-0c56-4d29-932a-dd09277fa7cb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 99da0d37-726e-42b9-b98a-5dd6c2165af6
role: Admin
exl-id: 50bf178d-7a3c-41df-9d13-99c74d944700
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 33%

---

# Übernehmen von XDP- und PDF-Dokumenten in AEM Forms {#getting-xdp-and-pdf-documents-in-aem-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Sie können Ihre Formulare aus Ihrem lokalen Dateisystem in das CRX-Repository importieren, indem Sie sie in AEM Forms hochladen. Der Upload-Vorgang wird für die folgenden Asset-Typen unterstützt:

* Formularvorlagen (XFA-Formulare)
* PDF forms
* Dokument (einfache PDF-Dokumente)

Sie können die unterstützten Assettypen einzeln oder als ZIP-Archiv hochladen. Sie können ein Asset des Typs `Resource` nur zusammen mit einem XFA-Formular in einem ZIP-Archiv hochladen.

>[!NOTE]
>
>Vergewissern Sie sich, dass Sie Mitglied der Gruppe `form-power-users` sind, um XDP-Dateien hochladen zu können. Wenden Sie sich an Ihren Administrator, um Mitglied der Gruppe zu werden.

## Hochladen von Formularen {#uploading-forms}

1. Melden Sie sich bei der Benutzeroberfläche von AEM Forms an, indem Sie auf `https://[server]:[port]/aem/forms.html` zugreifen.
1. Navigieren Sie zu dem Ordner, in den Sie das Formular oder den Ordner mit Formularen hochladen möchten.
1. Tippen Sie in der Aktionssymbolleiste auf **Erstellen > Datei-Upload**.

   ![Dateien von der Option „Lokaler Speicher“ unter „Erstellen“](assets/step.png)

1. Mit dem Uploadformular- oder Paketdialogfeld können Sie die Datei suchen und auswählen, die Sie hochladen möchten. Im Dateibrowser werden nur die unterstützten Dateiformate (ZIP, XDP und PDF) angezeigt.

   >[!NOTE]
   >
   >Dateinamen dürfen nur alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.

1. Klicken Sie nach der Dateiauswahl auf Hochladen , um die Dateien hochzuladen, oder klicken Sie auf Abbrechen , um den Upload abzubrechen. In einem Popup-Fenster werden die hinzugefügten Assets und die Assets aufgelistet, die am aktuellen Speicherort aktualisiert werden.

   >[!NOTE]
   >
   >Bei einer ZIP-Datei werden die relativen Pfade aller unterstützten Assets angezeigt. Nicht unterstützte Assets innerhalb der ZIP-Datei werden ignoriert und nicht aufgelistet. Wenn das ZIP-Archiv jedoch nur die nicht unterstützten Assets enthält, wird anstelle des Popup-Dialogfensters eine Fehlermeldung angezeigt.

   ![Upload-Dialogfenster beim Hochladen eines XFA-Formulars](assets/upload-scr.png)

1. Wenn der Dateiname von einem oder mehreren Assets ungültig ist, wird ein Fehler angezeigt. Korrigieren Sie die rot markierten Dateinamen und laden Sie die Dateien erneut hoch.

   ![Fehlermeldung beim Hochladen eines XFA-Formulars](assets/upload-scr-err.png)

Nach Abschluss des Uploads generiert ein Hintergrundworkflow Miniaturansichten für jedes Asset, basierend auf der Asset-Vorschau. Neuere Versionen von Assets überschreiben beim Hochladen vorhandene Assets.

### Geschützter Modus {#protected-mode}

Mit dem AEM Forms-Server können Sie JavaScript-Code ausführen. Ein bösartiger JavaScript-Code kann eine AEM Forms-Umgebung schädigen. Der geschützte Modus beschränkt AEM Forms darauf, XDP-Dateien nur aus vertrauenswürdigen Assets und Speicherorten auszuführen. Alle in der AEM Forms-Benutzeroberfläche verfügbaren XDP-Dateien gelten als vertrauenswürdige Assets.

Der geschützte Modus ist standardmäßig aktiviert. Bei Bedarf können Sie den geschützten Modus deaktivieren:

1. Melden Sie sich bei der AEM Web-Konsole als Administrator an. Die URL lautet `https://[server]:[port]/system/console/configMgr`.
1. Öffnen Sie Mobile Forms-Konfigurationen zur Bearbeitung.
1. Deaktivieren Sie die Option Geschützter Modus und klicken Sie auf **Speichern**. Der abgesicherte Modus ist deaktiviert.

## Aktualisieren referenzierter XFA-Formulare {#updating-referenced-xfa-forms}

In AEM Forms kann eine XFA-Formularvorlage durch ein adaptives Formular oder eine andere XFA-Formularvorlage referenziert werden. Eine Vorlage kann auch auf eine Ressource oder eine andere XFA-Vorlage verweisen.

Die Felder eines adaptiven Formulars, das auf eine XFA verweist, sind an die in der XFA verfügbaren Felder gebunden. Beim Aktualisieren einer Formularvorlage versucht das zugehörige adaptive Formular, mit der XFA zu synchronisieren. Weitere Informationen finden Sie unter [Synchronisieren von adaptiven Formularen mit der zugehörigen XFA](/help/forms/using/synchronizing-adaptive-forms-xfa.md).

Das Entfernen einer Formularvorlage beschädigt das abhängige adaptive Formular oder die Formularvorlage. Ein solches adaptives Formular wird manchmal informell als schmutziges Formular bezeichnet. In der Benutzeroberfläche von AEM Forms finden Sie die schmutzigen Formulare auf zwei Arten:

* Auf der Miniaturansicht des adaptiven Formulars in der Asset-Liste wird ein Warnsymbol angezeigt. Die folgende Meldung wird angezeigt, wenn Sie den Mauszeiger über das Warnsymbol bewegen.

   `Schema/Form Template for this adaptive form has been updated so please go to Authoring mode and rebase it with new version.`

![Warnung für ein unsynchronisiertes adaptives Formular nach dem Aktualisieren der zugehörigen XFA](assets/dirtyaf.png)

Ein Flag wird beibehalten, um anzugeben, ob ein adaptives Formular schmutzig ist. Diese Informationen sind auf der Seite mit den Formulareigenschaften neben den Formularmetadaten verfügbar. Lediglich für unsaubere adaptive Formulare zeigt eine Metadateneigenschaft `Model Refresh` den Wert `Recommended` an.

![Kennzeichnung eines adaptiven Formular, das mit dem XFA-Modell nicht synchronisiert ist](assets/model-refresh.png)
