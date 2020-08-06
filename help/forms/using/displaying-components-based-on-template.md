---
title: Anzeigen von Komponenten basierend auf der verwendeten Vorlage
seo-title: Anzeigen von Komponenten basierend auf der verwendeten Vorlage
description: Erfahren Sie, wie Sie bei der Erstellung eines Formulars Komponenten in der Seitenleiste basierend auf der ausgewählten Vorlage aktivieren können.
seo-description: Erfahren Sie, wie Sie bei der Erstellung eines Formulars Komponenten in der Seitenleiste basierend auf der ausgewählten Vorlage aktivieren können.
uuid: 4e87f400-fb45-413d-9be8-72edbe99f210
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
content-type: reference
discoiquuid: 940e45b4-dbf1-4207-bd4a-cf677d645fb4
translation-type: tm+mt
source-git-commit: 74d51d46d61b005930f382a33278ae0bea6435e2
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 76%

---


# Anzeigen von Komponenten basierend auf der verwendeten Vorlage {#displaying-components-based-on-the-template-used}

Wenn ein Formularersteller ein adaptives Formular anhand einer [Vorlage](/help/forms/using/template-editor.md) erstellt, kann der Formularersteller basierend auf der Vorlagenrichtlinie bestimmte Komponenten sehen und verwenden. Sie können eine Content-Richtlinie für Vorlagen angeben, mit der Sie eine Gruppe von Komponenten auswählen können, die Formularverfassern beim Formular-Authoring angezeigt wird.

## Ändern der Content-Richtlinie einer Vorlage {#changing-the-content-policy-of-a-template}

When you create a template, it is created under `/conf` in the content repository. Basierend auf den Ordnern, die Sie im `/conf` Ordner erstellt haben, lautet der Pfad zur Vorlage: `/conf/<your-folder>/settings/wcm/templates/<your-template>`.

Führen Sie die folgenden Schritte aus, um die Komponenten basierend auf der Content-Richtlinie einer Vorlage in der Seitenleiste anzuzeigen:

1. Öffnen Sie CRXDE Lite.

   URL: `https://<server>:<port>/crx/de/index.jsp`

1. Gehen Sie in CRXDE zu dem Ordner, in dem die Vorlage erstellt werden soll.

   Beispiel: `/conf/<your-folder>/`

1. In CRXDE, navigate to: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`

   Zum Auswählen einer Komponentengruppe ist eine neue Content-Richtlinie erforderlich. Kopieren Sie zum Erstellen einer neuen Richtlinie die Standardrichtlinie, fügen Sie sie ein und benennen Sie sie um.

   Pfad zur Standard-Inhaltsrichtlinie: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`

   Kopieren Sie im Ordner `gridFluidLayout` die Standardrichtlinie, fügen Sie sie ein und benennen Sie sie um. Beispiel: `myPolicy`.

   ![Kopieren von Standardrichtlinien](assets/crx-default1.png)

1. Select the new policy you create, and select the **components** property in the right-side panel with type `string[]`.

   Wenn Sie die Komponenteneigenschaft auswählen und öffnen, erscheint das Dialogfeld „Komponenten bearbeiten“. Im Dialogfeld „Komponenten bearbeiten“ können Sie Komponentengruppen mit den Tasten **+** und **-** hinzufügen oder entfernen. Sie können Komponentengruppen hinzufügen, die Komponenten enthalten, die von Autoren verwendet werden sollen.

   ![Hinzufügen oder Entfernen von Komponenten in der Richtlinie](assets/add-components-list1.png)

   Nachdem Sie eine Komponentengruppe hinzugefügt haben, klicken Sie auf **„OK“**, um die Liste zu aktualisieren, und klicken Sie dann auf **Alle speichern** über der CRXDE-Adressleiste und aktualisieren Sie.

1. Ändern Sie die Content-Richtlinie in der Vorlage vom Standard zu der neu erstellten Richtlinie. ( `myPolicy` in diesem Beispiel)

   Um die Richtlinie zu ändern, navigieren Sie in CRXDE zu `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items`.

   In the `cq:policy` property, change `default` to the new policy name ( `myPolicy`).

   ![Aktualisierte Content-Richtlinie für Vorlagen](assets/updated-policy.png)

   Wenn Sie ein Formular mit der Vorlage erstellen, werden die hinzugefügten Komponenten in der Seitenleiste angezeigt.

