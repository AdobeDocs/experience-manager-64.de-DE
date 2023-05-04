---
title: Arbeiten mit Formularsätzen in AEM Forms Workspace
seo-title: Working with Formsets in AEM Forms workspace
description: Ein Formularsatz ist eine Sammlung von HTML5 Formularen, die gruppiert sind und Endbenutzern als Formularsatz präsentiert werden. Erfahren Sie, wie Sie in AEM Forms Workspace mit Formularsätzen arbeiten können.
seo-description: A formset is a collection of HTML5 forms grouped and presented as a single set of forms to end users. Learn how you can work with formsets in AEM Forms workspace.
uuid: 77f81465-bd60-4aee-8507-585fe08adb78
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c1793e2e-413c-4b6f-b96b-09e011f06263
exl-id: 4e39f6dd-b7a3-4c6c-be1f-66b9a5743352
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 61%

---

# Arbeiten mit Formularsätzen in AEM Forms Workspace {#working-with-formsets-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Ein Formularsatz ist eine Sammlung von HTML5 Formularen, die gruppiert sind und Endbenutzern als Formularsatz präsentiert werden. Wenn der Benutzer einen Formularsatz ausfüllt, werden diese Informationen von einem Formular auf ein anderes übertragen. Der Formularsatz kann dann mit nur einem Klick gesendet werden. Weitere Informationen zu Formularsätzen und dazu, wie sie eingerichtet werden, finden Sie unter [Formularsätze in AEM Forms](/help/forms/using/formset-in-aem-forms.md).

AEM Forms Workspace unterstützt Formularsätze. Mit Formularsätzen können mehrere mit einem Dienst oder Prozess verknüpfte Formulare gruppiert werden, um einen Geschäftsprozess zu automatisieren und den Endbenutzern vorzustellen. In einem solchen Szenario können die Benutzer den gesamten Satz als einen Satz ausfüllen und es ist nicht erforderlich, einzelne Formulare oder Prozesse zu archivieren, zu senden und zu verfolgen.

## Ein Formularsatz in der AEM Forms Workspace-App dem Startpunkt zuweisen  {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Erstellen Sie den Geschäftsprozess-Arbeitsablauf in Workbench. Weitere Informationen finden Sie in der [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).
1. In den Prozesseigenschaften des Startpunkts wählen Sie **Ein CRX-Element verwenden** in „Präsentation und Daten“ aus.

   ![1-1](assets/1-1.png)

1. Klicken Sie ![Durchsuchen](assets/browse.png) (Durchsuchen) neben dem CRX-Elementpfad. Das Dialogfeld „Formularelement“ wird angezeigt.

   ![2](assets/2.png)

1. Klicken Sie auf die Registerkarte **Formularsatz**, wählen Sie in der Liste den betreffenden Formularsatz aus und klicken Sie dann auf **OK**.

1. Stellen Sie das Programm bereit, nachdem Sie andere relevante Prozesseigenschaften aktualisiert haben. 

## Die Verwendung von Formularsätzen in AEM Forms Workspace {#using-formset-in-nbsp-aem-forms-workspace}

Sobald einem Startpunkt ein Formularsatz zugewiesen wurde, kann der Startpunkt wie jeder andere Startpunkt über AEM Forms Workspace aufgerufen werden.

Folgende Vorgänge von Formularsätzen werden von AEM Forms Workspace unterstützt:

* Als Entwurf speichern
* Sperren
* Abbrechen
* Absenden
* Add Attachments
* Anmerkungen hinzufügen
* Wechseln Sie zwischen den Formularen in einem Formularsatz mit den Schaltflächen „Zurück“ und „Weiter“

![3-1](assets/3-1.png)

>[!NOTE]
>
>Um eine Leistungsverbesserung zu erreichen, sind alle Workspace-Schaltflächen (Zurück, Weiter, Speichern, Senden und weitere) während des Wechselns zwischen Formularen innerhalb eines Formularsatzes deaktiviert, bis das entsprechende Formular vollständig generiert wird.
