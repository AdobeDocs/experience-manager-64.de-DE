---
title: Einrichten einer Umgebung für die AEM Forms-App
seo-title: Einrichten einer Umgebung für die AEM Forms-App
description: Hardware, Software und Lizenzen, um die AEM Forms-App zu erstellen und zu bereitstellen.
seo-description: Hardware, Software und Lizenzen, um die AEM Forms-App zu erstellen und zu bereitstellen.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f

---


# Einrichten einer Umgebung für die AEM Forms-App {#set-up-environment-for-aem-forms-app}

Sie benötigen folgende Hardware, Software und Lizenzen, um die AEM Forms-App erstellen und bereitstellen zu können:

## Für Windows-Geräte {#for-windows-devices}

* Microsoft Windows 8.1 oder Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio-Tools für Apache Cordova

## Für iOS-Geräte {#for-ios-devices}

* Intel-basierte Apple Mac, auf dem Mac OS X 10.9.5 oder höher ausgeführt wird
* iOS SDK 8.4 oder höher
* Xcode-Version: Xcode 6.4 für OS X oder höher
* Mitgliedschaft im iOS Developer Enterprise Program
* Enterprise-Zertifikat zum Verteilen interner iOS-Apps
* Apple iPad mit iOS 8.4 oder höher

## Für Android-Geräte {#for-android-devices}

* Android Development Toolkit (ADT bundle) that can be downloaded from [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Wenn diese Umgebung auf einem MAC-System eingerichtet wird, sollte die ADT im Anwendungsordner installiert werden.
* If the ADT is installed in any other location on MAC, or if the environment is set up on a Windows system, the ADT SDK path needs to be updated in `local.properties` file that is available in `src\android` folder in the extracted the source archive `mobileworkspace-src.zip`. Zeigen Sie in dieser Datei die Variable `sdk.dir` auf den ADT SDK-Speicherort auf Ihrem Desktop.

>[!NOTE]
>
>Die Datei adobe-lc-mobileworkspace-src.zip enthält PhoneGap SDK 5.0. Stellen Sie sicher, dass PhoneGap SDK nicht vorinstalliert ist.
