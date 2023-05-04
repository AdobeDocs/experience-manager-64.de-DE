---
title: Bereitstellen der AEM Forms-App
seo-title: Distribute AEM Forms app
description: Verwenden Sie Mobile Device Management (MDM) für die Bereitstellung von Apps auf Mobilgeräten im großen Stil.
seo-description: Use Mobile Device Management (MDM) for the large-scale deployment of apps on mobile devices.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
exl-id: c1bf0a0e-70f7-41dd-8b1a-c114d89a265b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 23%

---

# Verteilen der AEM Forms-App {#distribute-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

Mobile Device Management (MDM) ermöglicht die Bereitstellung von Apps auf Mobilgeräten im großen Stil.

>[!NOTE]
>
>Diese Verteilung ist nur für iOS- und Android-Geräte verfügbar.

## Die wichtigsten Funktionen, die im Allgemeinen von MDM-Lösungen bereitgestellt werden: {#main-features-generally-provided-by-mdm-solutions}

* Aktivieren der Geräte-Einschreibung in der Unternehmensumgebung
* Zulassen der Konfiguration und Aktualisierung von Geräte-Einstellungen
* Erzwingen Sie die Sicherheitskompatibilität.
* Sicherer mobiler Zugriff auf Unternehmensressourcen

Mit einer MDM-Lösung sowie Mobile Application Management können Sie interne, öffentliche und erworbene Apps auf allen Mobilgeräten in Ihrem Unternehmen verwalten.

Der MDM-Administrator kann sowohl IPA- als auch APK-Dateien auf den MDM-Server hochladen und die Benutzer steuern, die auf die IPA- oder APK-Dateien zugreifen können. Der Administrator kann auch die Profileinstellung für jede Anwendung steuern.

## Profileinstellungen mit Auswirkung auf die AEM Forms-App {#profile-settings-affecting-the-aem-forms-app-br}

Die folgenden Profileinstellungen auf Ihrem Gerät wirken sich auf die Funktion der Mobile App von AEM Forms auf dem Gerät aus:

* **Verwendung der Kamera zulassen** im **Gerätefunktionalität** Abschnitt

Wenn Sie **Verwendung der Kamera zulassen**, die Kamerafunktion der [Fotoannotation](/help/forms/using/add-attachments.md) funktioniert nicht. Sie müssen diese Option aktivieren, um die Kamera in der App verwenden zu können.

* **Require passcode on device** im Abschnitt &quot;Passcode policies&quot;

Aktivieren **Verschlüsselung von Anwendungsdaten** wird empfohlen, die **passcode** auf Ihrem Gerät. Wenn auf dem Gerät kein Passcode festgelegt ist, werden auf dem Gerät gespeicherte Anwendungsdaten nicht verschlüsselt.
