---
title: Löschen von Formularen und zugehörigen Ressourcen
seo-title: Deleting forms and related resources
description: Löschen eines Formulars oder Assets in AEM Forms und Auswirkungen auf referenzierte und verweisende Assets und XFA-Formulare.
seo-description: How to delete a form or an asset in AEM Forms and the impact on referenced and referring assets and XFA forms.
uuid: df522b87-59d8-4678-922d-c9aab82b1381
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: c8519eec-f841-4867-baa9-a9e03042755e
role: Admin
exl-id: 94a66d83-b359-4be6-b668-4b4ba024b1e7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 35%

---

# Löschen von Formularen und zugehörigen Ressourcen {#deleting-forms-and-related-resources}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie können die Formulare und Assets löschen, um diese Assets aus dem Repository zu entfernen. Der Löschvorgang funktioniert bei allen Asset-Typen und -Ordnern.

Wenn Sie ein Asset aus der Autoreninstanz löschen, wird das Asset auch aus der Veröffentlichungsinstanz gelöscht. Der AEM Forms-Server besteht aus der Authoring- und der Veröffentlichungsinstanz. Die Autoreninstanz dient der Erstellung und Verwaltung von Formular-Assets und -Ressourcen. Die Veröffentlichungsinstanz enthält die veröffentlichten Formular-Assets und die zugehörigen Ressourcen, die für Endbenutzer verfügbar sind.

## Löschen eines Formulars {#how-to-delete-a-form}

1. Melden Sie sich bei der AEM Forms-Benutzeroberfläche an, indem Sie auf `https://[hostname]:[portport]/aem/forms.html.` zugreifen
1. Navigieren Sie zum Formular, das Sie löschen möchten, und wählen Sie es aus. Klicken Sie in der Symbolleiste auf „Löschen“ ![aem6forms_delete2](assets/aem6forms_delete2.png) und bestätigen Sie den Löschvorgang.

   >[!NOTE]
   >
   >Es kann jeweils nur ein Formular gelöscht werden. Löschen Sie mehrere Formulare einzeln oder löschen Sie den übergeordneten Ordner.

1. Bevor Sie ein Asset löschen, sucht AEM Forms nach Verweisen und fordert eine explizite Bestätigung an. Klicken Sie auf Löschen erzwingen , wenn Sie das Asset unabhängig vom Beziehungsstatus löschen möchten.

   >[!NOTE]
   >
   >Wenn Sie ein Asset löschen, auf das andere Assets verweisen, kann dies zu Funktionsproblemen führen.

   >[!NOTE]
   >
   >Wenn es sich bei dem ausgewählten Asset um einen Ordner handelt, der ein solches Asset in seiner Hierarchie enthält, löschen Sie andere Assets einzeln oder löschen Sie den gesamten Ordner.

## Auswirkungen des Löschens eines referenzierten XFA-Formulars {#impact-of-deleting-a-referenced-xfa-form}

In AEM Forms kann eine XFA-Formularvorlage durch ein adaptives Formular oder eine andere XFA-Formularvorlage referenziert werden. Eine Vorlage kann auch auf eine Ressource oder eine andere XFA-Vorlage verweisen.

Es ist nicht ratsam, ein XFA-Formular zu löschen, auf das von einem adaptiven Formular verwiesen wird, da es das adaptive Formular beschädigen kann. Wenn ein adaptives Formular auf ein XFA-Formular verweist, sind deren Felder gebunden. Nach dem Löschen des XFA-Formulars kann das adaptive Formular seine Felder nicht mit den XFA-Feldern synchronisieren und zeigt eine Fehlermeldung für diese Felder an. Weitere Informationen zur Auswirkung beim Löschen referenzierter XFA-Formulare und zu beschädigten adaptiven Formularen finden Sie unter [Aktualisieren referenzierter XFA-Formulare](/help/forms/using/get-xdp-pdf-documents-aem.md#p-updating-referenced-xfa-forms-p).

Um ein solches XFA-Formular zu löschen, aktualisieren Sie das adaptive Formular und entfernen Sie die Bindungen mit den XFA-Feldern.
