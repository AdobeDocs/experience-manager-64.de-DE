---
title: Verwenden der automatischen Speicherung in der AEM Forms-App
seo-title: Using autosave in AEM Forms app
description: Erfahren Sie, wie Sie in der AEM Forms-App die automatische Speicherung verwenden, mit der Sie Datenverlust vermeiden können.
seo-description: Learn how to use autosave feature in AEM Forms app that lets you avoid data loss.
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
exl-id: 6eb00c31-6806-478a-99d1-55912798ea69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 63%

---

# Verwenden der automatischen Speicherung in der AEM Forms-App {#using-autosave-in-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn ein Benutzer Daten in die Adobe Experience Manager Forms-App eingibt, speichert die Funktion sie in regelmäßigen Abständen. Die Funktion zum automatischen Speichern in der AEM Forms-App hilft Ihnen, Datenverlust zu vermeiden, wenn die App versehentlich geschlossen wird.

Ihre App kann versehentlich geschlossen werden:

* Wenn Ihr Gerät aufgrund des niedrigen Akkus heruntergefahren wird
* Wenn der Benutzer die App abbricht
* Wenn ein unerwarteter Absturz auftritt

Sie können die Intervalle angeben, in denen die App die eingegebenen Daten speichert.

>[!NOTE]
>
>Wählen Sie den Wert sorgfältig aus. Eine häufige automatische Speicherung kann spürbare Auswirkungen auf die Leistung Ihres Geräts haben.

Führen Sie die folgenden Schritte aus, um die Funktion zum automatischen Speichern in der AEM Forms-App zu verwenden:

1. Melden Sie sich bei der App an und navigieren Sie zu **[!UICONTROL Einstellungen > Allgemein]**.
1. Verwenden Sie im Bildschirm „General“ die Option **[!UICONTROL Autosave Frequency]**, um die Intervalle auszuwählen, in denen das Programm die eingegebenen Daten speichern soll.
   [![Einstellung „Autosave Frequency“](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Wenn Sie die App neu starten und sich als derselbe Benutzer anmelden, werden Sie aufgefordert, Ihre Aufgabe mit dem Dialogfeld „Nicht gespeicherte Aufgabe wiederherstellen“ wiederherzustellen. Klicken Sie in diesem Dialogfeld auf **[!UICONTROL OK]**, um die Arbeit an der gespeicherten Aufgabe fortzusetzen. Klicken Sie auf **[!UICONTROL Abbrechen]**, um die gespeicherten Daten entsprechend der zuletzt ausgelösten automatischen Speicherung zu löschen und an einer neuen Aufgabe zu arbeiten.

   Wenn Sie auf **[!UICONTROL OK]** klicken, wird die Aufgabe mit den Daten entsprechend der zuletzt ausgelösten automatischen Speicherung vor Absturz der App wiederhergestellt. Sie enthält die Formulardaten und alle Anlagen, die mit der Aufgabe verbunden sind.
   [ ![Wiederherstellen einer Aufgabe ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** Ein Formular für laufende Arbeiten **B.** Programm wurde erzwungen **C.** Programm wurde mit dem Dialogfeld „Nicht gespeicherte Aufgabe wiederherstellen“ erneut gestartet **D.** Formular wurde mit Originaldaten wiederhergestellt
