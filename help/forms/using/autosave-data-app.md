---
title: Verwenden der automatischen Speicherung in der AEM Forms-App
seo-title: Verwenden der automatischen Speicherung in der AEM Forms-App
description: 'Erfahren Sie, wie Sie in der AEM-App die automatische Speicherung verwenden, mit der Sie Datenverlust vermeiden können. '
seo-description: 'Erfahren Sie, wie Sie in der AEM-App die automatische Speicherung verwenden, mit der Sie Datenverlust vermeiden können. '
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 75%

---


# Verwenden der automatischen Speicherung in der AEM Forms-App {#using-autosave-in-aem-forms-app}

Wenn ein Benutzer Daten in die Adobe Experience Manager Forms-App eingibt, speichert die Funktion sie automatisch in regelmäßigen Abständen. Die automatische Speicherung in der AEM Forms-App hilft Ihnen, Datenverlust zu vermeiden, wenn die App versehentlich geschlossen wird.

Ihre App wird versehentlich geschlossen:

* Wenn sich Ihr Gerät aufgrund niedrigem Akku ausschaltet
* Wenn der Benutzer die App abbricht
* Wenn ein unerwarteter Absturz auftritt

Sie können die Intervalle angeben, in denen die App die eingegebenen Daten speichert.

>[!NOTE]
>
>Wählen Sie den Wert sorgfältig aus. Eine häufige automatische Speicherung kann spürbare Auswirkungen auf die Leistung Ihres Geräts haben.

Führen Sie die folgenden Schritte aus, um die automatische Speicherung in der AEM Forms-App zu verwenden:

1. Melden Sie sich bei der App und navigieren Sie zu **[!UICONTROL „Settings“ > „General“]**.
1. In the General screen, use the **[!UICONTROL Autosave Frequency]** option to select the intervals at which you want the app to save the entered data.
   [![Einstellung „Autosave Frequency“](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Wenn Sie die App neu starten und sich als derselbe Benutzer anmelden, werden Sie aufgefordert, Ihre Aufgabe mit dem Dialogfeld „Nicht gespeicherte Aufgabe wiederherstellen“ wiederherzustellen. Click **[!UICONTROL OK]** in the Recover Unsaved Task dialog to resume working with the saved task. Klicken Sie auf **[!UICONTROL Abbrechen]**, um die gespeicherten Daten entsprechend der zuletzt ausgelösten automatischen Speicherung zu löschen und an einer neuen Aufgabe zu arbeiten.

   Wenn Sie auf **[!UICONTROL OK]** klicken, wird die Aufgabe mit den Daten entsprechend der zuletzt ausgelösten automatischen Speicherung vor Absturz der App wiederhergestellt. Es enthält die Formulardaten und alle mit der Aufgabe verknüpften Anlagen.
   [ ![Eine Aufgabe](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**wiederherstellenA.**Ein derzeit bearbeitetes Formular** B.**App wurde** C.**App wurde mit dem Dialogfeld &quot;Nicht gespeicherte Aufgabe wiederherstellen&quot;** D erneut gestartet.**Formular mit Originaldaten wiederhergestellt

