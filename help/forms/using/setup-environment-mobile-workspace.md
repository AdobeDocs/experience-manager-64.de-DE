---
title: Einrichten einer Umgebung für die AEM Forms-App
seo-title: Set up environment for AEM Forms app
description: Hardware, Software und Lizenzen zum Erstellen und Bereitstellen der AEM Forms-App.
seo-description: Hardware, software, and licenses to build and deploy the AEM Forms app.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 53%

---

# Einrichten einer Umgebung für die AEM Forms-App {#set-up-environment-for-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Sie benötigen die folgende Hardware, Software und Lizenzen, um die AEM Forms-App zu erstellen und bereitzustellen:

## Für Windows-Geräte {#for-windows-devices}

* Microsoft Windows 8.1 oder Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools for Apache Cordova

## Für iOS-Geräte {#for-ios-devices}

* Intel-basierte Apple Mac mit Mac OS X 10.9.5 oder höher
* iOS SDK 8.4 oder höher
* Xcode-Version: Xcode 6.4 für OS X oder höher
* Mitgliedschaft im iOS Developer Enterprise Program
* Enterprise-Zertifikat zum Verteilen interner iOS-Apps
* Apple iPad mit iOS 8.4 oder höher

## Für Android-Geräte {#for-android-devices}

* Android Development Toolkit (ADT-Bundle), das von [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html) heruntergeladen werden kann
* Wenn diese Umgebung auf einem MAC-System eingerichtet wird, sollte die ADT im Anwendungsordner installiert werden.
* Wenn das ADT auf dem Mac auf einem anderen Speicherort installiert ist, oder wenn die Umgebung auf einem Windows-System eingerichtet ist, muss der ADT SDK-Pfad in der Datei `local.properties` aktualisiert werden, die im Ordner `src\android` im extrahierten Quellarchiv `mobileworkspace-src.zip` verfügbar ist. Zeigen Sie in dieser Datei die Variable `sdk.dir` auf den ADT SDK-Speicherort auf Ihrem Desktop.

>[!NOTE]
>
>Die Datei „adobe-lc-mobileworkspace-src.zip“ enthält PhoneGap SDK 5.0. Vergewissern Sie sich, dass PhoneGap SDK nicht vorinstalliert ist.
