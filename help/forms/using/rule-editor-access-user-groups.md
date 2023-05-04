---
title: Ausgewählten Benutzergruppen Zugriff auf den Regel-Editor gewähren
seo-title: Grant rule editor access to select user groups
description: Gewähren Sie ausgewählten Benutzergruppen eingeschränkten Zugriff auf den Regeleditor.
seo-description: Grant restricted access to rule editor to select user groups.
uuid: 3d982858-b2b5-4370-a9d7-5a95842a7897
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6bd58e37-085e-4057-8200-1404d54f41cc
feature: Adaptive Forms
exl-id: 5e2960f2-b172-48a7-bba3-4561a5f9c7bc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 70%

---

# Ausgewählten Benutzergruppen Zugriff auf den Regel-Editor gewähren {#grant-rule-editor-access-to-select-user-groups}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

## Übersicht {#overview}

Sie können verschiedene Arten von Benutzern mit unterschiedlichen Fähigkeiten haben, die mit Adaptive Forms arbeiten. Während professionelle Benutzer möglicherweise über die nötigen Kenntnisse zum Arbeiten mit Skripten und komplexen Regeln verfügen, genügt es für Benutzer, die nur über Grundkenntnisse verfügen, mit dem Layout und einfachen Eigenschaften adaptiver Formulare zu arbeiten.

AEM Forms ermöglicht es Ihnen, den Zugriff auf den Regel-Editor anhand der Rolle oder Funktion der Benutzer einzuschränken. In den Einstellungen für den Konfigurations-Service für adaptive Formular können Sie festlegen, welche [Benutzergruppen](/help/sites-administering/security.md) den Regeleditor anzeigen und auf ihn zugreifen können.

## Angeben von Benutzergruppen für Zugriff auf Regeleditor {#specify-user-groups-that-can-access-rule-editor}

1. Melden Sie sich bei AEM Forms als Admin an.
1. Klicken Sie in der Autoreninstanz auf ![adobeexperiencemanager](assets/adobeexperiencemanager.png)„Adobe Experience Manager“ > „Tools“ ![hammer](assets/hammer.png) > „Vorgänge“ > „Web-Konsole“. Die Webkonsole wird in einem neuen Fenster geöffnet.

   ![1](assets/1.png)

1. Suchen Sie im Fenster „Web-Konsole“ nach **[!UICONTROL Konfiguration von adaptiven Formularen und Web-Kanälen für interaktive Kommunikation]** und klicken Sie darauf. Das Dialogfeld **[!UICONTROL Konfiguration von adaptiven Formularen und Web-Kanälen für interaktive Kommunikation]** wird angezeigt. Behalten Sie die Werte bei und klicken Sie auf **[!UICONTROL Speichern]**.

   Es wird eine Datei /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config im CRX-Repository erstellt.

1. Melden Sie sich als Administrator bei CRXDE an. Öffnen Sie die Datei /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config zur Bearbeitung.
1. Geben Sie mithilfe folgender Eigenschaft den Namen einer Gruppe an, die auf den Regeleditor zugreifen kann (z. B. RuleEditorsUserGroup), und klicken Sie auf **Alle speichern**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Um den Zugriff für mehrere Gruppen zu ermöglichen, geben Sie eine Liste durch Komma getrennter Werte an:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![create-user](assets/create-user.png)

   Wenn nun ein Benutzer, der nicht zur angegebenen Benutzergruppe (hier RuleEditorsUserGroup) gehört, auf ein Feld tippt, wird das Symbol Regel bearbeiten ( ![edit-rules1](assets/edit-rules1.png)) ist für sie nicht in der Komponenten-Symbolleiste verfügbar:

   ![componentstoolbarwithre](assets/componentstoolbarwithre.png)

   Komponentensymbolleiste für Benutzer mit Zugriff auf Regeleditor

   ![componentstoolbarwithoutre](assets/componentstoolbarwithoutre.png)

   Komponentensymbolleiste für Benutzer ohne Zugriff auf Regeleditor:

   Anweisungen zum Hinzufügen von Benutzern zu Gruppen finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).
