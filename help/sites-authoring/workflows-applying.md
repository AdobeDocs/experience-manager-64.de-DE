---
title: Anwenden von Workflows auf Seiten
seo-title: Applying Workflows to Pages
description: Beim Authoring können Sie Workflows aufrufen, um auf Ihren Seiten Aktionen auszuführen. Es ist auch möglich, mehrere Workflows anzuwenden.
seo-description: When authoring, you can invoke workflows to take action on your pages; it is also possible to apply more than one workflow..
uuid: 8a1d16f8-69fc-4e3a-b72a-b799ea381024
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 8556d20a-99bd-4942-b7b8-2db69f64e67c
exl-id: 05c52802-adfd-4b5f-a273-d6a261a00659
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 66%

---

# Anwenden von Workflows auf Seiten{#applying-workflows-to-pages}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Beim Authoring können Sie Workflows aufrufen, um auf Ihren Seiten Maßnahmen zu ergreifen. Es ist auch möglich, mehrere Workflows anzuwenden.

Wenn Sie den Workflow anwenden, geben Sie die folgenden Informationen an:

* Der anzuwendende Workflow.

   Sie können jeden beliebigen Workflow anwenden (auf den Sie Zugriff haben, wie von Ihrem AEM-Administrator zugewiesen).

* Optional einen Titel, der dazu beiträgt, die Workflow-Instanz im Posteingang eines Benutzers zu identifizieren.
* Die Workflow-Payload. Hierbei kann es sich um eine oder mehrere Seiten handeln.

Workflows können wie folgt gestartet werden:

* die **[Sites](#starting-a-workflow-from-the-sites-console)** Konsole.
* beim Bearbeiten einer Seite von den **[Seiteninformationen](#starting-a-workflow-from-the-page-editor)** aus.

>[!NOTE]
>
>Siehe auch:
>
>* [Anwenden von Workflows auf DAM-Assets](/help/assets/assets-workflow.md).
>* [Arbeiten mit Projekt-Workflows](/help/sites-authoring/projects-with-workflows.md).
>


>[!NOTE]
>
>AEM Administratoren können [Workflows mit verschiedenen anderen Methoden starten](/help/sites-administering/workflows-starting.md).

## Starten eines Workflows von der Sites-Konsole aus {#starting-a-workflow-from-the-sites-console}

Sie können einen Workflow wie folgt starten:

* die **[Erstellen](#starting-a-workflow-from-the-sites-toolbar)** in der Sites-Symbolleiste.
* die **[Timeline](#starting-a-workflow-from-the-timeline)** -Leiste der Sites-Konsole.

In beiden Fällen müssen Sie:

* [Geben Sie die Workflow-Details im Assistenten &quot;Workflow erstellen&quot;an](#specifying-workflow-details-in-the-create-workflow-wizard).

### Starten eines Workflows von der Sites-Symbolleiste aus {#starting-a-workflow-from-the-sites-toolbar}

Sie können einen Workflow von der Symbolleiste der **Sites**-Konsole aus starten:

1. Gehen Sie zur gewünschten Seite und wählen Sie sie aus.

1. Von der Option **Erstellen** in der Symbolleiste aus können Sie jetzt **Workflow** auswählen.

   ![screen_shot_2019-03-06at121237pm](assets/screen_shot_2019-03-06at121237pm.png)

1. Der Assistent **Workflow erstellen** hilft Ihnen, [die Workflow-Details anzugeben](#specifying-workflow-details-in-the-create-workflow-wizard).

### Starten eines Workflows aus der Zeitleiste {#starting-a-workflow-from-the-timeline}

Aus der **Zeitleiste** können Sie einen Workflow starten, der auf Ihre ausgewählte Ressource angewendet werden soll.

1. [Wählen Sie die Ressource aus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) und öffnen Sie die [Zeitleiste](/help/sites-authoring/basic-handling.md#timeline) (oder öffnen Sie die Zeitleiste und wählen Sie dann die Ressource aus).
1. Der Pfeil neben dem Kommentarfeld kann verwendet werden, um **Workflow starten** anzuzeigen:

   ![wf-51](assets/wf-51.png)

1. Der Assistent **Workflow erstellen** hilft Ihnen, [die Workflow-Details anzugeben](#specifying-workflow-details-in-the-create-workflow-wizard).

### Angeben von Workflow-Details im Assistenten „Workflow erstellen“ {#specifying-workflow-details-in-the-create-workflow-wizard}

Die **Workflow erstellen** -Assistent hilft Ihnen bei der Auswahl des Workflows und der Angabe der erforderlichen Details.

Nach dem Öffnen **Workflow erstellen** Assistenten aus:

* die **[Erstellen](#starting-a-workflow-from-the-sites-toolbar)** in der Sites-Symbolleiste.
* die **[Timeline](#starting-a-workflow-from-the-timeline)** -Leiste der Sites-Konsole.

Sie können Details angeben:

1. Im **Eigenschaften** Schritt, werden die grundlegenden Optionen des Workflows definiert:

   * **Workflow-Modell**
   * **Workflow-Titel**

      * Sie können einen Titel für diese Instanz angeben, damit Sie sie später identifizieren können.

   Je nach Workflow-Modell stehen auch die folgenden Optionen zur Verfügung. Dadurch kann das als Payload erstellte Paket nach Abschluss des Workflows beibehalten werden.

   * **Workflow-Paket behalten**
   * **Paketname**

      * Sie können einen Titel für das Paket angeben, um die Identifizierung zu erleichtern.
   >[!NOTE]
   >
   >Die Option **Workflow-Paket behalten** ist verfügbar, wenn der Workflow für Unterstützung für mehrere [Ressourcen konfiguriert](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) wurde und mehrere Ressourcen ausgewählt wurden.

   Wenn Sie fertig sind, klicken Sie auf **Weiter**, um fortzufahren.

   ![wf-52](assets/wf-52.png)

1. Im Schritt **Umfang** können Sie Folgendes auswählen:

   * **Inhalt hinzufügen**, um den [Pfad-Browser](/help/sites-authoring/author-environment-tools.md#path-browser) zu öffnen und zusätzliche Ressourcen auszuwählen; im Browser klicken/tippen Sie auf **Auswählen**, um den Inhalt zur Workflow-Instanz hinzuzufügen.
   * Eine vorhandene Ressource, um weitere Aktionen zu sehen:

      * **Untergeordnete Elemente einbeziehen**, um anzugeben, dass untergeordnete Elemente der betreffenden Ressource im Workflow enthalten sind.

         Ein Dialogfeld wird geöffnet, in dem Sie die Auswahl verfeinern können:

         * Nur unmittelbar untergeordnete Elemente einbeziehen.
         * Nur geänderte Seiten einbeziehen.
         * Nur bereits veröffentlichte Seiten einbeziehen.

         Alle angegebenen untergeordneten Elemente werden der Liste der Ressourcen hinzugefügt, auf die der Workflow angewendet werden soll.

      * **Auswahl entfernen** , um diese Ressource aus dem Workflow zu entfernen.

   ![wf-53](assets/wf-53.png)

   >[!NOTE]
   >
   >Wenn Sie zusätzliche Ressourcen hinzufügen, können Sie **Zurück** verwenden, um die Einstellung für **Workflow-Paket behalten** im Schritt **Eigenschaften** anzupassen.

1. Verwenden Sie **Erstellen**, um den Assistenten zu schließen und die Workflow-Instanz zu erstellen. In der Sites-Konsole wird eine Benachrichtigung angezeigt.

## Starten eines Workflows aus dem Seiten-Editor {#starting-a-workflow-from-the-page-editor}

Wenn Sie eine Seite bearbeiten, können Sie die **Seiteninformationen** von der Symbolleiste aus aufrufen. Das Dropdown-Menü enthält die Option **Workflow starten**. Ein Dialogfeld wird geöffnet, in dem Sie den gewünschten Workflow ggf. zusammen mit einem Titel angeben können:

![wf-54](assets/wf-54.png)
