---
title: Wiederverwenden adaptiver Formulare
seo-title: Reusing adaptive forms
description: Sie können ein vorhandenes adaptives Formular wiederverwenden, um neue adaptive Formulare zu erstellen.
seo-description: You can reuse an existing adaptive form to create new adaptive forms.
uuid: f1d0fb70-e255-4dd9-8e6d-fd65eaf2e81a
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ef564750-f107-41cb-887e-fc6d22b7d32e
feature: Adaptive Forms
exl-id: 9393fe94-002a-497b-9579-d6ad3bb3973e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 62%

---

# Wiederverwenden adaptiver Formulare {#reusing-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Einführung {#introduction}

Wenn Sie einige Eigenschaften eines vorhandenen adaptiven Formulars verwenden möchten, um ein neues zu generieren, können Sie einfach die Funktion zum Kopieren und Einfügen verwenden. Darüber hinaus können Sie das neue adaptive Formular in den gewünschten Ordnerpfad einfügen. Alle Metadateneigenschaften werden repliziert und die XFAs und XSDs für XFA- und XSD-basierte adaptive Formulare werden ebenfalls kopiert.

>[!NOTE]
>
>Status- und Überprüfungsdetails werden nicht kopiert. Wenn Ihr adaptives Formular beispielsweise veröffentlicht wird und Sie es dann kopieren, befindet sich das eingefügte adaptive Formular im unveröffentlichten Status. Ebenso wenig wird, wenn ein kopiertes Asset überprüft wird, das eingefügte Asset derselben Überprüfung unterzogen.

### Kopieren adaptiver Formulare {#copy-an-adaptive-form}

Kopieren Sie ein adaptives Formular mit einem der folgenden Methoden:

1. Klicken Sie in Schnellaktionen auf das Symbol ![aem6forms_copy](assets/aem6forms_copy.png) zum Kopieren.

   >[!NOTE]
   >
   >Schnellaktionen sind die Aktionselemente, die beim Zeigen mit der Maus auf eine Miniaturansicht angezeigt werden.

1. Wählen Sie das adaptive Formular aus. Der Auswahlprozess unterscheidet sich je nach Ansicht.

   Wenn Sie sich in der Kartenansicht befinden, wechseln Sie zum Auswahlmodus, indem Sie das Auswahlsymbol ![aem6forms_check-circle](assets/aem6forms_check-circle.png) und alle adaptiven Formulare anklicken, die Sie kopieren möchten.

   Wenn Sie sich in der Listenansicht befinden, aktivieren Sie die Kontrollkästchen der gewünschten adaptiven Formulare, um sie auszuwählen.

   >[!NOTE]
   >
   >Alle ausgewählten Assets müssen adaptive Formulare sein, da die Kopieren/Einfügen-Funktion nur bei adaptiven Formularen unterstützt wird. Außerdem müssen sich alle ausgewählten Elemente in demselben Ordner befinden.

   Nach dem Auswählen der Assets klicken Sie auf das Symbol ![aem6forms_copy](assets/aem6forms_copy.png) in der Symbolleiste, um das ausgewählte adaptive Formular zu kopieren.

### Einfügen adaptiver Formulare {#paste-an-adaptive-form}

Wenn Sie auf die Kopieraktion klicken, wird der Auswahlmodus automatisch beendet und das Symbol zum Einfügen ![aem6forms_paste](assets/aem6forms_paste.png) wird sichtbar. Gehen Sie nun zum gewünschten Ordnerpfad und klicken Sie auf das Symbol ![aem6forms_paste](assets/aem6forms_paste.png), um das kopierte adaptive Formular einzufügen.

Wenn Sie in denselben Ordner einfügen oder sich im Zielordner eine weitere Datei mit demselben Knotennamen (mit dem sie im CRX-Repository gespeichert ist) befindet, wird am Suffix eine 1 angehängt (zum Beispiel wird „myaf“ zu „myaf1“ und wenn sich „myaf1“ am selben Speicherort befindet, wird „myaf“ zu „myaf2“). Alle anderen Eigenschaften bleiben mit dem ursprünglichen adaptiven Formular identisch.

Nachdem Sie auf das Einfugen-Symbol ![aem6forms_paste](assets/aem6forms_paste.png) geklickt haben, wird es wieder ausgeblendet. Sie können jeweils nur einmal einfügen. Wenn Sie vom selben Asset erneut eine Kopie erstellen möchten, kopieren Sie es erneut.

### Inhalt des neuen adaptiven Formulars ändern {#change-contents-of-new-adaptive-form}

Der Inhalt eingefügter adaptiver Formulare kann mithilfe der folgenden Methoden geändert werden, um ihn vom kopierten Formular zu unterscheiden:

1. **Ändern der Metadateneigenschaften:**

   Sie können die Metadateneigenschaften des adaptiven Formulars ändern, z. B. Titel und Beschreibung. Weitere Informationen zu Metadateneigenschaften und dazu, wie diese geändert werden können, finden Sie unter [Verwalten von Formularmetadaten](/help/forms/using/manage-form-metadata.md).

1. **Ändern von XFA/XSD für XFA-/XSD-basierte adaptive Formulare:**

   Sie können die in adaptiven Formularen verwendete XFA/XSD ändern. Informationen zum Ändern dieser adaptiven Formulare finden Sie unter [Verwalten von Formularmetadaten](/help/forms/using/manage-form-metadata.md)

1. **Neu veröffentlichen:**

   Das eingefügte Asset unterscheidet sich vom kopierten. Sie können es als neues Asset veröffentlichen, um es für Endbenutzer verfügbar zu machen. Informationen zum Veröffentlichen eines Assets finden Sie unter [Veröffentlichen und Rückgängigmachen der Veröffentlichung von Formularen](/help/forms/using/publishing-unpublishing-forms.md)
