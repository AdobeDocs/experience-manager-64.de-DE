---
title: Speichern einer Aufgabe oder eines Formulars als Entwurf
seo-title: Saving a task or form as a draft
description: Schritte zum Speichern eines Entwurfs für eine Aufgabe oder ein Formular in der AEM Forms-App
seo-description: Steps to save a draft copy of a task or a form in the AEM Forms app
uuid: 1192d2c2-05a4-4a96-9015-e56111aa2646
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 9950288c-b5a2-4945-afad-be9ce2abc8e9
exl-id: c21cddb3-d12d-4e1b-bd62-cf75946569be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 43%

---

# Speichern einer Aufgabe oder eines Formulars als Entwurf {#saving-a-task-or-form-as-a-draft}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Bei der Option „Als Entwurf speichern“ wird ein Schnappschuss einer Aufgabe oder eines Formulars zusammen mit den Daten im dazugehörigen Formular gespeichert. Sie können auch einen Entwurf aus einer Vorlage erstellen. Die Entwürfe werden auf dem Mobilgerät gespeichert und mit dem Adobe Experience Manager Forms-Server für einen späteren Abruf synchronisiert.

Sie können das [Formular aktualisieren](/help/forms/using/working-with-form.md), [mit Fotos versehen](/help/forms/using/add-attachments.md) und Notizen machen. Wenn Sie ein Formular aktualisieren, wird empfohlen, es als Entwurf zu speichern. In Situationen, in denen Sie sich entscheiden, ein ausgefülltes Formular zu einem späteren Zeitpunkt zu senden, ist es hilfreich, es als Entwurf zu speichern.

Um die Funktion „Als Entwurf speichern“ für Formulare, die im Forms-Portal gespeichert sind, zu aktivieren, siehe [Speichern eines HTML5-Formulars als Entwurf](/help/forms/using/saving-html5-form-draft.md).\
Siehe [Entwürfe und Übermittlungen-Komponente](/help/forms/using/draft-submission-component.md), um die Übermittlung von adaptiven Formularen zu konfigurieren. (Nicht gültig für Formulare, die mit dem AEM Forms auf JEE-Server synchronisiert werden.)

Um einen Entwurf zu erstellen, öffnen Sie das Formular und tippen Sie auf **Als Entwurf speichern** ![save-as-draft](assets/save-as-draft.png). Geben Sie den Namen des Entwurfs ein und tippen Sie auf **Speichern**. Der Entwurf wird im Ordner &quot;Entwürfe&quot;gespeichert und mit dem Server synchronisiert. Sie wird im Ordner &quot;Outbox&quot;gespeichert, wenn die App offline ist.

Wenn Sie das entsprechende Formular anschließend aktualisieren, werden die Änderungen sofort übernommen. Wenn Sie die AEM Forms App mit dem AEM Forms-Server synchronisieren, wird der Entwurf auf den AEM Forms-Server hochgeladen. Zudem wird der Entwurf aus der Outbox in den Aufgaben- oder Entwurfsordner verschoben. Neben ihm wird ein Bearbeitungssymbol angezeigt.

Während Sie weiterhin mehrere Aufgaben und Startpunkte bearbeiten und speichern, werden diese Entwürfe gespeichert. Jedes Mal, wenn Sie Ihre App mit den AEM Forms-Server synchronisieren, wird der Entwurf auf dem Server gespeichert. Dadurch wird sichergestellt, dass Sie die Entwürfe jederzeit basierend auf dem zuletzt gespeicherten Datum und der zuletzt gespeicherten Uhrzeit wiederherstellen können. Wenn Sie beispielsweise die App neu installieren oder Ihr Mobilgerät ändern, können Sie den Entwurf vom Server herunterladen.

## Entwurf löschen {#delete-a-draft}

Im Ordner &quot;Entwürfe&quot;werden alle Entwürfe aufgelistet. Sie können die Option Entwurf löschen verwenden, um die Entwürfe dauerhaft vom Mobilgerät und Server zu löschen.

Die Option zum Löschen von Entwürfen, die aus einer Aufgabe erstellt wurden, ist nicht verfügbar. Beim Löschen eines Entwurfs, der aus einer Aufgabe erstellt wurde, wird die Aufgabe abgebrochen.

Entwürfe können sowohl im Offline- als auch im Online-Modus verworfen werden. Beim Verwerfen der Entwürfe im Offline-Modus werden die Entwürfe nur dann vom Server gelöscht, wenn die Verbindung zum Server wiederhergestellt wurde.

Führen Sie die folgenden Schritte aus, um einen Entwurf zu löschen:

1. Navigieren Sie in der AEM Forms-App zu **Formulare**.
1. Wählen Sie **Entwürfe** aus der Dropdown-Liste neben „Suchen“. 
1. Bei einem Formular mit dem Bearbeitungssymbol ![edit-draft-app](assets/edit-draft-app.png) handelt es sich um einen Entwurf. Tippen Sie auf das horizontale Auslassungszeichen neben dem Entwurf.
1. Wählen Sie in den Optionen, die angezeigt werden, wenn Sie auf das horizontale Auslassungszeichen tippen, **Entwurf löschen**.
