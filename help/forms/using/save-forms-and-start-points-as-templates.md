---
title: Speichern von Formularen als Vorlagen
seo-title: Save forms as templates
description: Erfahren Sie, wie Sie Vorlagen aus Formularen mit wiederholt erforderlichen Daten erstellen.
seo-description: Learn how to create templates from forms with data required repeatedly.
uuid: 090c6271-4061-4adc-a063-9df4953b47ce
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e0df2f85-664a-47b3-a8c5-e986b975d421
exl-id: 355c4810-6e45-41cb-9b60-73225bd53526
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 35%

---

# Speichern von Formularen als Vorlagen {#save-forms-as-templates}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn Benutzer ein Formular ausfüllen, bleiben die Eingaben in einige Felder manchmal gleich. In solchen Fällen können Sie die Felder ausfüllen, für die in jeder Instanz identische Werte erforderlich sind, und das Formular oder den Entwurf als Vorlage speichern. Jedes Mal, wenn Sie eine Instanz der Vorlage erstellen, werden die angegebenen Felder bereits mit den in der Vorlage angegebenen Werten ausgefüllt. Auf diese Weise sparen Sie Zeit und Mühe beim Ausfüllen des Formulars.

Führen Sie die folgenden Schritte aus, um eine Vorlage zu erstellen: 

1. Öffnen Sie ein Formular und wählen Sie die Felder aus, für bei jeder Verwendung gleichbleibende Werte verwendet werden sollen, bzw. geben Sie diese Werte dort ein. Sie eine Anlage in die Vorlage einbeziehen, die normalerweise beim Ausfüllen des Formulars hinzugefügt wird.
1. Tippen Sie auf das **Als Vorlage speichern** ![save_as_template](assets/save_as_template.png)Symbol. Ein Dialogfeld, in dem Sie den Namen der Vorlage eingeben können, wird angezeigt.
1. Geben Sie den Namen der Vorlage ein und tippen Sie auf **Speichern**. Die Vorlage wird im Vorlagenordner angezeigt.

   Wenn eine Vorlage mit demselben Namen vorhanden ist, wird ein Dialogfeld angezeigt, in dem Sie bestätigen können, dass die vorhandene Vorlage überschrieben wird. Um die vorhandene Vorlage durch eine neue Vorlage zu ersetzen, tippen Sie auf **Weiter** oder tippen Sie auf , um die Vorlage mit einem anderen Namen zu speichern. **Abbrechen**.

Jetzt können Sie die gespeicherte Vorlage öffnen. Jedes Mal, wenn eine Vorlage geöffnet wird, wird ein neues Formular oder eine Aufgabe erstellt und das Formular zeigt die gespeicherten Daten und Optionen an. Mit Vorlagen können Sie die vorausgefüllten Daten bearbeiten, eine Anlage hinzufügen, als Entwurf speichern, die Aufgabe übermitteln oder andere Vorlagen erstellen. Vorlagen sind für Mobilgeräte spezifisch und werden nicht mit dem Adobe Experience Manager Forms-Server synchronisiert.

Sie können eine nicht mehr benötigte Vorlage auch löschen. Um eine Vorlage zu löschen, navigieren Sie zum Vorlagenordner, tippen Sie auf das Auslassungszeichen, und tippen Sie dann auf **Vorlage löschen**.

>[!NOTE]
>
>Eine Vorlage ist lokal verfügbar und wird nicht mit dem Server synchronisiert. Durch Löschen der lokalen Daten der App wird die Vorlage gelöscht.
