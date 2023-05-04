---
title: Anzeigen von Komponenten basierend auf der verwendeten Vorlage
seo-title: Displaying components based on the template used
description: Erfahren Sie beim Erstellen eines Formulars, wie Sie Komponenten in der Seitenleiste basierend auf der ausgewählten Vorlage aktivieren können.
seo-description: When you create a form, learn how you can enable components in the sidebar based on the template selected.
uuid: 4e87f400-fb45-413d-9be8-72edbe99f210
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
content-type: reference
discoiquuid: 940e45b4-dbf1-4207-bd4a-cf677d645fb4
exl-id: a4cee2e6-a56f-4355-8176-b3ed7478a775
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 59%

---

# Anzeigen von Komponenten basierend auf der verwendeten Vorlage {#displaying-components-based-on-the-template-used}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Wenn ein Formularautor ein adaptives Formular mithilfe einer [template](/help/forms/using/template-editor.md)festgelegt ist, kann der Formularverfasser bestimmte Komponenten basierend auf der Vorlagenrichtlinie anzeigen und verwenden. Sie können eine Inhaltsrichtlinie für Vorlagen angeben, mit der Sie eine Gruppe von Komponenten auswählen können, die dem Formularautor zum Zeitpunkt der Formularbearbeitung angezeigt werden.

## Inhaltsrichtlinie einer Vorlage ändern {#changing-the-content-policy-of-a-template}

Wenn Sie eine Vorlage erstellen, wird diese unter `/conf` im Content Repository erstellt. Basierend auf den Ordnern, die Sie im Verzeichnis `/conf` erstellt haben, lautet der Pfad zur Vorlage: `/conf/<your-folder>/settings/wcm/templates/<your-template>`.

Führen Sie die folgenden Schritte aus, um die Komponenten basierend auf der Content-Richtlinie einer Vorlage in der Seitenleiste anzuzeigen:

1. Öffnen Sie CRXDE Lite.

   URL: `https://<server>:<port>/crx/de/index.jsp`

1. Gehen Sie in CRXDE zu dem Ordner, in dem die Vorlage erstellt werden soll.

   Beispiel: `/conf/<your-folder>/`

1. Navigieren Sie in CRXDE zu: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`

   Um eine Gruppe von Komponenten auszuwählen, ist eine neue Inhaltsrichtlinie erforderlich. Um eine neue Richtlinie zu erstellen, kopieren Sie die Standardrichtlinie, fügen Sie sie ein und benennen Sie sie um.

   Der Pfad zur Standardinhaltsrichtlinie lautet: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`

   Kopieren Sie im Ordner `gridFluidLayout` die Standardrichtlinie, fügen Sie sie ein und benennen Sie sie um. Beispiel: `myPolicy`.

   ![Kopieren von Standardrichtlinien](assets/crx-default1.png)

1. Wählen Sie die neu zu erstellende Richtlinie und anschließend im rechten Bedienfeld die Eigenschaft **Komponenten** vom Typ `string[]` aus.

   Wenn Sie die Komponenteneigenschaft auswählen und öffnen, wird das Dialogfeld &quot;Komponenten bearbeiten&quot;angezeigt. Im Dialogfeld &quot;Komponenten bearbeiten&quot;können Sie Komponentengruppen mithilfe der **+** und **-** Schaltflächen. Sie können Komponentengruppen mit Komponenten hinzufügen, die Autoren für Formulare verwenden sollen. 

   ![Hinzufügen oder Entfernen von Komponenten in der Richtlinie](assets/add-components-list1.png)

   Nachdem Sie eine Komponentengruppe hinzugefügt haben, klicken Sie auf **„OK“**, um die Liste zu aktualisieren, und klicken Sie dann auf **Alle speichern** über der CRXDE-Adressleiste und aktualisieren Sie.

1. Ändern Sie die Content-Richtlinie in der Vorlage vom Standard zu der neu erstellten Richtlinie. ( `myPolicy` in diesem Beispiel.)

   Um die Richtlinie zu ändern, navigieren Sie in CRXDE zu `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items`.

   Ändern Sie in der Eigenschaft `cq:policy` den Eintrag `default` in den neuen Richtliniennamen (`myPolicy`).

   ![Aktualisierte Content-Richtlinie für Vorlagen](assets/updated-policy.png)

   Wenn Sie ein Formular mit der Vorlage erstellen, werden die hinzugefügten Komponenten in der Seitenleiste angezeigt.
