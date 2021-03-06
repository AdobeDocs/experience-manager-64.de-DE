---
title: Erstellen einer sicheren AEM Forms-App für iOS
seo-title: Building a secure AEM Forms app for iOS
description: Schritte zum Erstellen einer sicheren AEM Forms-App.
seo-description: Steps to build a secure AEM Forms app.
uuid: 6c4b160f-4d0c-4976-9609-9196795b6c8e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 90cd8ba5-4f47-4074-bc54-6a7bb8afe256
exl-id: 7efc657e-b662-47db-8e70-62a37f3a3051
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 95%

---

# Erstellen einer sicheren AEM Forms-App für iOS {#building-a-secure-aem-forms-app-for-ios}

Sie müssen das Xcode-Projekt für AEM Forms-App archivieren, um das Installationsprogramm (eine .ipa-Datei) und eine Eigenschaftslistendatei (eine .plist-Datei) zu erstellen. Die Eigenschaftslistendatei enthält Konfigurationsinformationen der gehosteten internen App, z. B. den Namen und den Hostingort der App. Weitere Informationen zur Eigenschaftslistendatei finden Sie unter [About Information Property List Files](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Melden Sie sich bei der folgenden Webseite an:

   [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Erstellen Sie eine App-ID. Eine detaillierte Beschreibung zur Erstellung einer App-ID finden Sie unter [Erstellen und Konfigurieren von App-IDs](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Um den Bundle-Identifier für die iOS-Anwendung für Ihre App zu konfigurieren, klicken Sie auf **[!UICONTROL Configure App ID]**.
1. Wählen Sie unten auf der Webseite **[!UICONTROL Enable for Data Protection]**. Geben Sie die Datenschutzoptionen ein.

   Klicken Sie auf **[!UICONTROL Fertig]**.

1. Navigieren Sie zu „Provisioning->Distribution“ und erstellen Sie ein neues Profil mit der App-ID, die in Schritt 3 konfiguriert wurde.
1. Laden Sie das Profil für die Bereitstellung herunter und fügen Sie es zum Xcode und iPad hinzu.
1. Melden Sie sich bei Ihrem Mac-Computer an, auf dem Xcode und iOS SDK installiert und konfiguriert sind.
1. Öffnen Sie das Projekt `AEM Forms.xcodeproj` in Xcode.
1. Klicken Sie auf **[!UICONTROL AEM Forms]** und wählen Sie unter **[!UICONTROL TARGETS]** die Option **[!UICONTROL AEM Forms]**. Wählen Sie die Registerkarte **[!UICONTROL Build-Einstellungen]**, suchen Sie den Abschnitt **[!UICONTROL Code Signing- Berechtigung]** und wählen Sie in der Dropdown-Liste „Berechtigungen“ die Option **[!UICONTROL LC Enterprise]**.
1. Suchen und öffnen Sie die Datei `LC Enterprise.entitlements` im Xcode zur Bearbeitung. Fügen Sie unter &quot;XCode-Berechtigungen&quot;dasselbe Schlüssel-Wert-Paar hinzu, das auch in Ihrem Bereitstellungsprofil vorhanden ist.
1. Klicken Sie auf der Registerkarte **[!UICONTROL Build Settings]** auf **[!UICONTROL All]** und anschließend auf **[!UICONTROL Combined]**.
1. Erweitern Sie in der Liste **[!UICONTROL Settings]** das Element **[!UICONTROL Code Signing]**.
1. Wählen Sie für **[!UICONTROL Code Signing Identity]** die entsprechende Signatur. Achten Sie darauf, dass dieselbe Signatur für die Optionen **[!UICONTROL Debug]**, **[!UICONTROL Release]** und **[!UICONTROL Any iOS SDK]** ausgewählt wird.
1. Wählen Sie unter **[!UICONTROL PROJEKT]** die Option **[!UICONTROL AEM Forms]** und stellen Sie sicher, dass die entsprechende Signatur für **[!UICONTROL Code Signing Identity]**, **[!UICONTROL Debug]**, **[!UICONTROL Release]** und **[!UICONTROL Any iOS SDK]** ausgewählt ist.
1. Erstellen Sie die AEM Forms-App und stellen Sie sie bereit. Detaillierte Anweisungen zur Erstellung und Bereitstellung der AEM Forms-App finden Sie unter [Erstellen des Installationsprogramms für die AEM Forms-App](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app).
