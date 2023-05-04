---
title: Arbeiten mit einem Formular
seo-title: Working with a Form
description: Anzeigen und Aktualisieren des mit einer Aufgabe oder einem Startpunkt verknüpften Formulars in der AEM Forms-App
seo-description: View and update the form associated with a task or Startpoint in the AEM Forms app
uuid: 7481ca5c-a2c0-4697-9008-1e51bce2012e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 8a5e038e-b39a-41de-88a0-47642e5bd5bf
exl-id: ae565dbd-2631-4364-89f7-675700b43320
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 35%

---

# Arbeiten mit einem Formular {#working-with-a-form}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn ein Formular für die Synchronisierung in der Forms-App aktiviert ist, wird das Formular heruntergeladen und Sie können es direkt bearbeiten.

Die Formulare werden in Ihre App heruntergeladen und sind offline verfügbar. Angenommen, Sie haben ein Bankgeschäft und ein Kunde füllt auf Ihrer Website einen Antrag aus. Der Antrag ist ein adaptives Formular, das Informationen von Ihren Kunden akzeptiert und zur Überprüfung speichert. Der Administrator überprüft das Formular und erstellt ein Überprüfungsformular in AEM Autoreninstanz. Der Administrator aktiviert die Synchronisierung des Formulars mit der AEM Forms-App. Wenn das Überprüfungsformular in der AEM Forms-App verfügbar ist, kann Ihr Außendienstmitarbeiter die Kundendetails mithilfe eines Mobilgeräts überprüfen. Das Mobilgerät wird mit dem Server synchronisiert und das Überprüfungsformular wird in die App geladen. Ihr Außendienstmitarbeiter kann Ihren Kunden besuchen, die Details überprüfen, Daten als Entwurf speichern oder das Überprüfungsformular übermitteln. Das Formular wird jedes Mal, wenn Ihre App online ist, mit dem Server synchronisiert.

Formular in der AEM Forms-App synchronisieren

1. Wählen Sie in der Autoreninstanz ein Formular aus und klicken Sie auf **Eigenschaften anzeigen**.

1. Klicken Sie auf der Eigenschaftenseite auf **Erweitert**.
1. Aktivieren Sie unter „Erweitert“ die Option: **Mit AEM Forms-App synchronisieren** und tippen Sie auf **Speichern**.

Um mehrere Formulare zu synchronisieren, wählen Sie in der Autoreninstanz mehrere Formulare in Forms Manager aus und tippen Sie auf **Mit AEM Forms-App synchronisieren**. Wenn das Formular veröffentlicht wird, wird die AEM Forms App mit dem Server synchronisiert und ruft das Formular ab.

>[!NOTE]
>
>Unterstützte Formulare:
>
>* Adaptive Formulare (ohne verzögertes Laden)
>* Mobile Forms
>
>Anlagen auf Formularebene werden in den adaptiven Formularen, die in der mit dem AEM Forms OSGi-Server synchronisierten AEM Forms-App abgerufen werden, nicht unterstützt. Benutzer können Dateien in einem Feld anhängen, wenn der Autor zum Zeitpunkt der Formularbearbeitung Anlagen auf Feldebene aktiviert hat.

**So öffnen und aktualisieren Sie ein Formular**

1. Um ein Formular zu öffnen, tippen Sie auf dem Startbildschirm auf das Formular.
1. Sie können die Felder des Formulars aktualisieren, Anlagen auf Feldebene hinzufügen, das Formular als Entwurf speichern und es senden.
