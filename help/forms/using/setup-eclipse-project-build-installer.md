---
title: Erstellen Sie die AEM Forms Android-App
seo-title: Build the AEM Forms Android app
description: Schritte zum Einrichten des Android Studio-Projekts und Erstellen der .apk-Datei für die AEM Forms-App für Android
seo-description: Steps to set up the Android Studio project and build the .apk file for the AEM Forms app for Android
uuid: 2e140aaf-5be5-4d5d-9941-9d1f4bf2debd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: f5d6d9bd-4f36-4a4f-8008-15fb853a9219
exl-id: dbeed62e-eff1-47bc-b6da-cad543295170
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 62%

---

# Erstellen Sie die AEM Forms Android-App {#build-the-aem-forms-android-app}

Führen Sie die folgenden Schritte in der empfohlenen Reihenfolge aus, um die Android-App für AEM Forms zu erstellen.

1. [Laden Sie das Quellcode-Paket der AEM Forms-App herunter](#download-android-zip)
1. [Legen Sie die Umgebungsvariable fest.](#set-environment-variable-android)
1. [Standardmäßige AEM Forms-App erstellen](#set-up-the-xcode-project)

## Laden Sie das Quellcode-Paket der AEM Forms-App herunter {#download-android-zip}

Das Quellcode-Paket der AEM Forms App bezieht sich auf die `adobe-lc-mobileworkspace-src-<version>.zip` Archiv. Dieses Archiv enthält den Quellcode, der zum Erstellen einer benutzerdefinierten AEM Forms-App erforderlich ist. Das Archiv ist im `adobe-aemfd-forms-app-src-pkg-<version>.zip`Paket verfügbar auf der Software Distribution.

Führen Sie die folgenden Schritte aus, um die `adobe-aemfd-forms-app-src-pkg-<version>.zip` Datei:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die **[!UICONTROL Suchdownloads]** Option zum Filtern der Ergebnisse.
1. Tippen Sie auf den Paketnamen für Ihr Betriebssystem und wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Download]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.
1. Um das Quellcodearchiv herunterzuladen, öffnen Sie **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in Ihrem Browser. Die ZIP-Datei der Android-App wird auf Ihr Gerät heruntergeladen.
1. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner in Ihrem lokalen Dateisystem. Beispiel: *C:\Folder Structure\adobe-lc-mobileworkspace-src-2.4.20*

Die folgende Abbildung zeigt die Struktur der `adobe-lc-mobileworkspace-src-<version>.zip\android`Ordner.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Legen Sie die Umgebungsvariable fest. {#set-environment-variable-android}

Legen Sie die folgenden Umgebungsvariablen fest, bevor Sie den Erstellungsprozess für die AEM Forms-App starten:

* Setzen Sie die Umgebungsvariable JAVA_HOME auf den Speicherort der JDK-Software im lokalen Dateisystem. Beispiel: C:\Programme\Java\jdk1.8.0_181
* Legen Sie die `ANDROID_SDK_ROOT` Systemumgebungsvariable zum SDK-Speicherort für Android. Beispiel: C:\Users\username\AppData\Local\Android\Sdk
* Legen Sie die Systemumgebungsvariable `Path` fest, um die Ordner „Plattform-Tools“ und „Tools“ für Android einzubeziehen . Beispiel: C:\Users\username\AppData\Local\Android\Sdk\platform-tools and C:\Users\username\AppData\Local\Android\Sdk\tools.

## Standardmäßige AEM Forms-App erstellen {#set-up-the-xcode-project}

Nachdem Sie die Datei adobe-lc-mobileworkspace-src- gespeichert haben&lt;version>Erstellen Sie die ZIP-Datei im lokalen Dateisystem und legen Sie die Umgebungsvariablen fest. Erstellen Sie dazu die standardmäßige AEM Forms Android-App mit einer der folgenden Optionen:

* [Erstellen Sie die AEM Forms-App mit Android Studio](#using-android-studio)
* [Generieren Sie die .apk-Datei mit Android Studio](#generate-apk-android-studio)

### Erstellen Sie die AEM Forms-App mit Android Studio {#using-android-studio}

Erstellen Sie die AEM Forms-App mit Android Studio über folgende Schritte:

1. Starten Sie die Android Studio-App auf Ihrem Computer.
1. Klicken Sie auf **Öffnen Sie ein vorhandenes Android Studio-Projekt**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die **android**-Option im linken Fensterbereich angezeigt.

   ![android_folder_studio](assets/android_folder_studio.png)

1. Auswählen **Android** Klicken Sie im linken Bereich auf **Ausführen** > **Ausführen von &#39;android&#39;**.
1. Wählen Sie das Android-Gerät im Abschnitt Connected Devices (Verbundene Geräte) im Dialogfeld Deployment Target auswählen aus und klicken Sie auf OK.

   Nachdem Sie die Entwicklungsumgebung erfolgreich erstellt haben, können Sie jetzt Anpassungen für die App vornehmen. Verwenden Sie die folgenden Artikel, um die App anzupassen:

   * [Branding-Anpassung](/help/forms/using/branding-customization.md)
   * [Designanpassung](/help/forms/using/theme-customization.md)
   * [Gestenanpassung](/help/forms/using/gesture-customization.md)

   Nach dem Anwenden entsprechender Anpassungen auf Ihre App können Sie die .apk-Datei für die Verteilung generieren.

### Generieren Sie die .apk-Datei mit Android Studio {#generate-apk-android-studio}

Führen Sie die folgenden Schritte aus, um die APK-Datei mit Android Studio zu generieren:

1. Starten Sie die Android Studio-App auf Ihrem Computer.
1. Auswählen **Öffnen eines vorhandenen Android Studio-Projekts**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die android-Option im linken Fensterbereich angezeigt.

1. Wählen Sie **Erstellen** > **APK erstellen**, um die APK-Datei zu generieren.

   Optional können Sie **Build** > **Signierte APK generieren** , um [signierte Version](https://developer.android.com/studio/publish/app-signing) der .apk-Datei.

## Verwenden von Android Debug Bridge {#build-android-debug-bridge}

Nachdem die APK-Datei generiert wurde, führen Sie den folgenden Befehl aus, um die Anwendung auf einem Android-Gerät mit dem [Android Debug Bridge](https://developer.android.com/tools/help/adb.html).

**Windows-Nutzer:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**Mac-Benutzer:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
