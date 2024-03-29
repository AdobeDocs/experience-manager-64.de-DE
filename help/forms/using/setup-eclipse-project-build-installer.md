---
title: Aufbauen der AEM Forms Android-App
seo-title: Build the AEM Forms Android app
description: Schritte zum Einrichten des Android Studio-Projekts und Erstellen der .apk-Datei für die AEM Forms-App für Android
seo-description: Steps to set up the Android Studio project and build the .apk file for the AEM Forms app for Android
uuid: 2e140aaf-5be5-4d5d-9941-9d1f4bf2debd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: f5d6d9bd-4f36-4a4f-8008-15fb853a9219
exl-id: dbeed62e-eff1-47bc-b6da-cad543295170
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 74%

---

# Erstellen Sie die AEM Forms Android-App {#build-the-aem-forms-android-app}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Führen Sie die folgenden Schritte in der empfohlenen Reihenfolge aus, um die Android-App für AEM Forms zu erstellen.

1. [Laden Sie das Quellcode-Paket der AEM Forms-App herunter](#download-android-zip)
1. [Legen Sie die Umgebungsvariable fest.](#set-environment-variable-android)
1. [Standardmäßige AEM Forms-App erstellen](#set-up-the-xcode-project)

## Laden Sie das Quellcode-Paket der AEM Forms-App herunter {#download-android-zip}

Das AEM Forms-App-Quellcodepaket verweist auf das Archiv `adobe-lc-mobileworkspace-src-<version>.zip`. Dieses Archiv enthält den Quellcode, der zum Erstellen einer benutzerdefinierten AEM Forms-App erforderlich ist. Das Archiv wird im Paket `adobe-aemfd-forms-app-src-pkg-<version>.zip` der Software Distribution bereitgestellt.

Führen Sie folgende Schritte aus, um die Datei `adobe-aemfd-forms-app-src-pkg-<version>.zip` herunterzuladen:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im **[!UICONTROL Filter]** Abschnitt:
   1. Auswählen **[!UICONTROL Forms]** von **[!UICONTROL Lösung]** Dropdown-Liste.
   2. Wählen Sie die Version aus und geben Sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den für Ihr Betriebssystem zutreffenden Paketnamen, wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.
1. Um das Quellcodearchiv herunterzuladen, öffnen Sie **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in Ihrem Browser. Die ZIP-Datei der Android-App wird auf Ihr Gerät heruntergeladen.
1. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner in Ihrem lokalen Dateisystem. Beispiel: *C:\Folder Structure\adobe-lc-mobileworkspace-src-2.4.20*

Das folgende Bild zeigt die Struktur des Ordners `adobe-lc-mobileworkspace-src-<version>.zip\android`.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Festlegen der Umgebungsvariablen {#set-environment-variable-android}

Legen Sie die folgenden Umgebungsvariablen fest, bevor Sie den Build-Prozess für die AEM Forms-App starten:

* Legen Sie die Umgebungsvariable JAVA_HOME auf den Speicherort der JDK-Software im lokalen Dateisystem fest. Beispiel: C:\Program Files\Java\jdk1.8.0_181
* Setzen Sie die Systemumgebungsvariable `ANDROID_SDK_ROOT` auf den Speicherort des SDK für Android. Beispiel: C:\Users\username\AppData\Local\Android\Sdk
* Legen Sie die Systemumgebungsvariable `Path` fest, um die Ordner „Plattform-Tools“ und „Tools“ für Android einzubeziehen. Beispiel: C:\Users\username\AppData\Local\Android\Sdk\platform-tools and C:\Users\username\AppData\Local\Android\Sdk\tools.

## Standardmäßige AEM Forms-App erstellen {#set-up-the-xcode-project}

Nachdem Sie die Datei adobe-lc-mobileworkspace-src-&lt;version>.zip im lokalen Dateisystem gespeichert und die Umgebungsvariablen festgelegt haben, erstellen Sie die standardmäßige AEM Forms Android-App mit einer der folgenden Optionen:

* [Erstellen Sie die AEM Forms-App mit Android Studio](#using-android-studio)
* [Generieren Sie die .apk-Datei mit Android Studio](#generate-apk-android-studio)

### Aufbauen der AEM Forms-App mit Android Studio {#using-android-studio}

Führen Sie die folgenden Schritte aus, um die AEM Forms-App mit Android Studio zu erstellen:

1. Starten Sie die Android Studio-Anwendung auf Ihrem Computer.
1. Klicken Sie auf **Öffnen Sie ein vorhandenes Android Studio-Projekt**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die **android**-Option im linken Fensterbereich angezeigt.

   ![android_folder_studio](assets/android_folder_studio.png)

1. Wählen Sie im linken Bereich **android** und aus klicken Sie auf **Run** > **&#39;android&#39; ausführen**.
1. Wählen Sie das Android-Gerät im Abschnitt „Verbundene Geräte“ im Dialogfeld „Ziel für die Bereitstellung auswählen“ aus und klicken Sie auf „OK“.

   Nachdem Sie die Entwicklungsumgebung erfolgreich erstellt haben, können Sie jetzt Anpassungen für die App vornehmen. Verwenden Sie die folgenden Artikel, um die App anzupassen:

   * [Branding-Anpassung](/help/forms/using/branding-customization.md)
   * [Designanpassung](/help/forms/using/theme-customization.md)
   * [Gestenanpassung](/help/forms/using/gesture-customization.md)

   Nachdem Sie die entsprechenden Anpassungen auf Ihre App angewendet haben, können Sie die .apk-Datei für die Verteilung generieren.

### Generieren der .apk-Datei mit Android Studio {#generate-apk-android-studio}

Führen Sie die folgenden Schritte aus, um die APK-Datei mit Android Studio zu generieren:

1. Starten Sie die Android Studio-Anwendung auf Ihrem Computer.
1. Wählen Sie **Ein vorhandenes Android Studio-Projekt öffnen**. Wenn das Dialogfeld zum Öffnen eines vorhandenen Projekts nicht automatisch angezeigt wird, wählen Sie **Datei** > **Öffnen**.
1. Navigieren Sie zu *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* auf dem lokalen Dateisystem und klicken Sie auf **OK**.

   Die android-Option im linken Fensterbereich angezeigt.

1. Wählen Sie **Erstellen** > **APK erstellen**, um die APK-Datei zu generieren.

   Wählen Sie optional **Erstellen** > **Signiertes APK generieren**, um eine [signierte Version](https://developer.android.com/studio/publish/app-signing) der APK-Datei zu generieren.

## Verwenden von Android Debug Bridge {#build-android-debug-bridge}

Sobald die APK-Datei generiert wurde, führen Sie den folgenden Befehl aus, um das Programm mithilfe von [Android Debug Bridge](https://developer.android.com/tools/help/adb.html) auf einem Android-Gerät zu installieren.

**Windows-Benutzer:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**Mac-Benutzer:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
