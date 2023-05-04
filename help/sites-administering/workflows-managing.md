---
title: Verwalten des Zugriffs auf Workflows
seo-title: Managing Access to Workflows
description: Erfahren Sie, wie Sie den Zugriff auf Workflows verwalten.
seo-description: Learn how to manage access to Workflows.
uuid: 58f79b89-fe56-4565-a869-8179c1ac68de
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5150867a-02a9-45c9-b2fd-e536b60ffa8c
exl-id: 9c588691-0649-4d59-ab97-ebadfcd1252c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 49%

---

# Verwalten des Zugriffs auf Workflows{#managing-access-to-workflows}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Konfigurieren Sie ACLs entsprechend den Benutzerkonten, um den Start und die Teilnahme an Workflows zu ermöglichen (oder zu deaktivieren).

## Erforderliche Benutzerberechtigungen für Workflows {#required-user-permissions-for-workflows}

Maßnahmen in Bezug auf Workflows können durchgeführt werden, wenn:

* Sie mit dem `admin`-Konto arbeiten;
* das Konto der Standardgruppe `workflow-users` zugewiesen wurde:

   * Diese Gruppe verfügt über alle Berechtigungen, die Ihre Benutzer benötigen, um Workflow-Aktionen durchzuführen.
   * wenn sich das Konto in dieser Gruppe befindet, hat es nur Zugriff auf von ihm initiierte Workflows.

* das Konto der Standardgruppe `workflow-administrators` zugewiesen wurde:

   * Diese Gruppe verfügt über alle Berechtigungen, die erforderlich sind, damit Ihre berechtigten Benutzer Workflows überwachen und verwalten können.
   * wenn sich das Konto in dieser Gruppe befindet, hat es Zugriff auf alle Workflows.

>[!NOTE]
>
>Dies sind die Mindestanforderungen. Ihr Konto muss auch entweder der zugewiesene Teilnehmer oder ein Mitglied der zugewiesenen Gruppe sein, um bestimmte Schritte durchführen zu können.

## Zugriff auf Workflows konfigurieren {#configuring-access-to-workflows}

Workflow-Modelle übernehmen eine standardmäßige Zugriffssteuerungsliste (ACL), um zu steuern, wie Benutzer mit Workflows interagieren können. Um den Benutzerzugriff für einen Workflow anzupassen, ändern Sie die Zugriffssteuerungsliste (ACL) im Repository für den Ordner, der den Workflow-Modellknoten enthält:

* [Anwenden einer ACL für das spezifische Workflow-Modell unter /var/workflow/models](/help/sites-administering/workflows-managing.md#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models)
* [Erstellen eines Unterordners in /var/workflow/models und Anwenden der ACL auf diesen Ordner](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that)

>[!NOTE]
>
>Informationen zur Verwendung von CRXDE Lite zum Konfigurieren von ACLs finden Sie unter [Zugriffsberechtigungsverwaltung](/help/sites-administering/user-group-ac-admin.md#access-right-management).

### Anwenden einer ACL für das spezifische Workflow-Modell unter /var/workflow/models {#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models}

Falls das Workflow-Modell unter `/var/workflow/models` gespeichert ist, können Sie dem folgenden Ordner eine spezifische ACL zuweisen, die nur für diesen Workflow relevant ist:

1. Öffnen Sie die CRXDE Lite in Ihrem Webbrowser (z. B. [http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Wählen Sie in der Knotenstruktur den Knoten für den Ordner mit den Workflow-Modellen aus:

   `/var/workflow/models`

1. Klicken Sie auf die Registerkarte **Zugriffssteuerung**.
1. Klicken Sie in der Tabelle **Richtlinien zur lokalen Zugriffssteuerung** (**Zugriffssteuerungsliste**) auf das Plussymbol, um einen **Eintrag hinzuzufügen**.
1. Im **Neuen Eintrag hinzufügen** ein neues ACE mit den folgenden Eigenschaften hinzufügen:

   * **Prinzipal**: `content-authors`
   * **Typ**: `Deny`
   * **Berechtigungen**: `jcr:read`
   * **rep:glob**: Verweis auf den spezifischen Workflow

   ![wf-108](assets/wf-108.png)

   Die Tabelle **Zugriffssteuerungsliste** beinhaltet nun die Beschränkung für `content-authors` im Workflow-Modell `prototype-wfm-01`.

   ![wf-109](assets/wf-109.png)

1. Klicken Sie auf **Alle speichern**.

   Der Workflow `prototype-wfm-01` ist nicht länger für Mitglieder der Gruppe `content-authors` verfügbar.

### Erstellen eines Unterordners in /var/workflow/models und Anwenden der ACL auf diesen Ordner {#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that}

Ihre [Das Entwicklungsteam kann die Workflows in einem Unterordner erstellen](/help/sites-developing/workflows-models.md#creating-a-new-workflow) von

`/var/workflow/models`

Vergleichbar mit den DAM-Workflows, die im folgenden Ordner gespeichert sind:

`/var/workflow/models/dam/`

Sie können dann dem Ordner selbst eine ACL hinzufügen.

1. Öffnen Sie die CRXDE Lite in Ihrem Webbrowser (z. B. [http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Wählen Sie in der Knotenstruktur den Knoten für den einzelnen Ordner im Ordner mit Workflow-Modellen aus. Beispiel:

   `/var/workflow/models/prototypes`

1. Klicken Sie auf die Registerkarte **Zugriffssteuerung**.
1. Klicken Sie in der Tabelle **Gültige Richtlinie für die Zugriffssteuerung** auf das Pluszeichen, um einen Eintrag **hinzuzufügen**.
1. Klicken Sie in der Tabelle **Richtlinien zur lokalen Zugriffssteuerung** (**Zugriffssteuerungsliste**) auf das Plussymbol, um einen **Eintrag hinzuzufügen**.
1. Im **Neuen Eintrag hinzufügen** ein neues ACE mit den folgenden Eigenschaften hinzufügen:

   * **Prinzipal**: `content-authors`
   * **Typ**: `Deny`
   * **Berechtigungen**: `jcr:read`

   >[!NOTE]
   >
   >Wie im Abschnitt [Anwenden einer ACL für das spezifische Workflow-Modell unter /var/workflow/models](/help/sites-administering/workflows-managing.md#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models) können Sie ein „rep:glob“ einfügen, um den Zugriff auf einen spezifischen Workflow zu beschränken.

   ![wf-110](assets/wf-110.png)

   Die Tabelle **Zugriffssteuerungsliste** beinhaltet nun die Beschränkung für `content-authors` im Ordner `prototypes`.

   ![wf-111](assets/wf-111.png)

1. Klicken Sie auf **Alle speichern**.

   Die Modelle im `prototypes`-Ordner sind nicht länger für Mitglieder der Gruppe `content-authors` verfügbar.
