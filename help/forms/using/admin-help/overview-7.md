---
title: Grundlagen der Konfiguration von Formularen
seo-title: Basics of configuring forms
description: Erfahren Sie mehr über die verschiedenen Formulardienste, mit denen Sie interaktive Datenerfassungsanwendungen erstellen können.
seo-description: Learn about the various forms services that help you create interactive data capture applications.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
exl-id: 616cd550-c3bd-4daf-887d-0470f1b08389
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 11%

---

# Grundlagen der Konfiguration von Formularen {#basics-of-configuring-forms}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mit dem Forms-Dienst können Sie interaktive Clientanwendungen zur Datenerfassung erstellen, mit denen typischerweise in Designer erstellte Formulare validiert, verarbeitet, transformiert und bereitgestellt werden. Formularverfasser entwickeln einen einzelnen Formularentwurf, den der Forms-Dienst in verschiedenen Formaten wiedergibt:

* als PDF in Adobe Reader oder im Browser
* als HTML in verschiedenen Browserumgebungen, einschließlich eines kompatiblen XHTML 1.0-Renderings
* als Formular-Guides in verschiedenen Browserumgebungen, die Adobe Flash Player unterstützen.

Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

Auf der Seite &quot;Forms&quot;in Administration Console können Sie das Verhalten des Forms-Dienstes konfigurieren. Diese Einstellungen gelten für alle Aufrufe des Dienstes. Alle Parameter, die über das AEM Forms SDK gesendet werden, überschreiben die Einstellungen in Administration Console. Sie betreffen jedoch nur diesen bestimmten Aufruf.

Nachdem Sie die Forms-Einstellungen in Administration Console geändert haben, klicken Sie auf &quot;Speichern&quot;. Sie müssen den Server nicht neu starten, damit die Änderungen wirksam werden. Möglicherweise müssen Sie den Forms-Dienst jedoch beim Konfigurieren der Cachemodus-Einstellungen anhalten und neu starten. (Siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
