---
title: Konfigurieren einer Umleitungsseite
seo-title: Configuring redirect page
description: Nachdem Sie ein adaptives Formular ausgefüllt haben, können Benutzer zu einer Webseite umgeleitet werden, die Formularverfasser beim Erstellen des Formulars konfigurieren können.
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 75%

---

# Konfigurieren einer Umleitungsseite {#configuring-redirect-page}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Formularersteller können für jedes Formular eine Seite konfigurieren, zu der die Formularbenutzer nach dem Absenden eines Formulars umgeleitet werden.

1. Wählen Sie im Bearbeitungsmodus eine Komponente aus, klicken Sie dann auf ![field-level](assets/field-level.png) > **Container für ein adaptives Formular** und anschließend auf ![cmppr](assets/cmppr.png).

1. Klicken Sie in der Seitenleiste auf **Übermittlung**.

1. Geben Sie die URL der Umleitungsseite unter der Danksagung im Bereich „Senden“ an.
1. Optional können Sie unter „Übermittlungsaktion“ für die Aktion „An REST-Endpunkt übermitteln“ den Parameter konfigurieren, der zur Umleitungsseite weitergeleitet wird.

![Konfigurieren der Umleitungsseite](assets/thank-you-setting-1.png)
**Abbildung:** *Konfiguration der Umleitungsseite*

Formularautoren können die folgenden Parameter verwenden, die an die Dankeseite übergeben werden. Bei allen verfügbaren Übermittlungsaktionen werden `status`- und `owner`-Parameter übergeben. Neben diesen beiden Parametern werden für die folgenden Übermittlungsaktionen einige weitere Parameter weitergeleitet:

* **Aktion für Inhaltsspeicherung** (veraltet): `contentPath` – der Pfad des Knotens im Repository, in dem gesendete Daten gespeichert werden – wird weitergeleitet.

* **Aktion zum Speichern einer PDF** (veraltet): `contentPath` – die gesendeten Daten und der Pfad des Knoten im Repository, in dem die PDF-Datei gespeichert wird, werden weitergeleitet.

* **An Formular-Workflow übermitteln**: Ausgabeparameter, die aus dem Formular-Workflow zurückgegeben wurden, werden weitergeleitet.

* **An REST-Endpunkt übermitteln**: Parameter, die für die Zuordnung feldinterner Werte zu Parametern hinzugefügt wurden, werden weitergeleitet. Die Parameter `status` und `owner` werden bei dieser Übermittlungsaktion nicht weitergeleitet. Weitere Informationen finden Sie unter [Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](/help/forms/using/configuring-submit-actions.md). 
