---
title: Ausgewählten Benutzergruppen Zugriff auf den Regel-Editor gewähren
seo-title: Ausgewählten Benutzergruppen Zugriff auf den Regel-Editor gewähren
description: Gewähren Sie ausgewählten Benutzergruppen eingeschränkten Zugriff auf den Regel-Editor.
seo-description: Gewähren Sie ausgewählten Benutzergruppen eingeschränkten Zugriff auf den Regel-Editor.
uuid: 3d982858-b2b5-4370-a9d7-5a95842a7897
content-type: reference
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6bd58e37-085e-4057-8200-1404d54f41cc
translation-type: tm+mt
source-git-commit: 73d0dea62c294bea435364fb9c6892d80751d90d

---


# Ausgewählten Benutzergruppen Zugriff auf den Regel-Editor gewähren {#grant-rule-editor-access-to-select-user-groups}

## Überblick {#overview}

Möglicherweise sind unterschiedliche Typen von Benutzern mit unterschiedlichen Fähigkeiten vorhanden, die mit adaptiven Formularen arbeiten. Während professionelle Benutzer möglicherweise über die nötigen Kenntnisse zum Arbeiten mit Skripten und komplexen Regeln verfügen, genügt es für Benutzer, die nur über Grundkenntnisse verfügen, mit dem Layout und einfachen Eigenschaften adaptiver Formulare zu arbeiten.

AEM Forms ermöglicht es Ihnen, den Zugriff auf den Regel-Editor anhand der Rolle oder Funktion der Benutzer einzuschränken. In den Einstellungen für den Adaptive Forms Configuration Service können Sie festlegen, welche [Benutzergruppen](/help/sites-administering/security.md) den Regel-Editor anzeigen und auf ihn zugreifen können.

## Benutzergruppen für Zugriff auf Regel-Editor angeben {#specify-user-groups-that-can-access-rule-editor}

1. Melden Sie sich bei AEM Forms als Administrator an.
1. In the author instance, click ![adobeexperiencemanager](assets/adobeexperiencemanager.png)Adobe Experience Manager > Tools ![hammer](assets/hammer.png) > Operations > Web Console. Die Web-Konsole wird in einem neuen Fenster geöffnet.

   ![1](assets/1.png)

1. In Web Console Window, locate and click **Adaptive Form Configuration Service**. **Dialogfeld &quot;Konfigurationsdienst** für adaptive Formulare&quot;wird angezeigt. Behalten Sie die Werte bei und klicken Sie auf **Speichern**.

   Die Datei „/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config“ im CRX-Repository wird erstellt.

1. Melden Sie sich bei CRXDE als Administrator an. Öffnen Sie die Datei „/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config“ zum Bearbeiten.
1. Geben Sie mithilfe der folgenden Eigenschaft den Namen einer Gruppe an, die auf den Regel-Editor zugreifen kann (z. B. RuleEditorsUserGroup) und klicken Sie auf **Alle speichern**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Um den Zugriff für mehrere Gruppen zu ermöglichen, geben Sie eine Liste durch Komma getrennter Werte an:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![create-user](assets/create-user.png)

   Now, when a user that is not a part of the specified user group (here RuleEditorsUserGroup) taps a field, the Edit Rule icon ( ![edit-rules1](assets/edit-rules1.png)) is not available for her in the components toolbar:

   ![componentStuolbarwither](assets/componentstoolbarwithre.png)

   Komponentensymbolleiste für Benutzer mit Zugriff auf Regel-Editor

   ![componentStuolbarwithouter](assets/componentstoolbarwithoutre.png)

   Komponentensymbolleiste für Benutzer ohne Zugriff auf Regel-Editor

   For instructions on adding users to groups, see [User Administration and Security](/help/sites-administering/security.md).

