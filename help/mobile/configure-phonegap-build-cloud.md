---
title: Adobe PhoneGap Build Cloud Service konfigurieren
seo-title: Configure your Adobe PhoneGap Build Cloud Service
description: Auf dieser Seite finden Sie Informationen zum Konfigurieren der Cloud-Services und zum Erstellen Ihrer Anwendung mit PhoneGap-Build.
seo-description: Follow this page for configuring the cloud services and building your application with PhoneGap build.
uuid: 59aa99c3-1425-4cc5-9839-a57a6a545d45
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 3c84f4ec-d89b-4ad4-802e-ee3e2d49d916
exl-id: 87e64e2b-cced-45bc-9de8-477169c857b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 5%

---

# Adobe PhoneGap Build Cloud Service konfigurieren {#configure-your-adobe-phonegap-build-cloud-service}

>[!CAUTION]
>
>AEM 6.4 hat das Ende der erweiterten Unterstützung erreicht und diese Dokumentation wird nicht mehr aktualisiert. Weitere Informationen finden Sie in unserer [technische Unterstützung](https://helpx.adobe.com/de/support/programs/eol-matrix.html). Unterstützte Versionen suchen [here](https://experienceleague.adobe.com/docs/?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die **PhoneGap Build** im Anwendungs-Dashboard bietet die Möglichkeit, Ihre PhoneGap-Mobile App über den Adobe PhoneGap Build-Dienst zu erstellen und zu verteilen.

Alle unterstützten Plattformen, die innerhalb der **App verwalten** wird mit PhoneGap Build erstellt, wenn ein Remote-Build mit der **PhoneGap Build** Kachel.

Sie können einen Remote-Build an [https://build.phonegap.com](https://build.phonegap.com) oder laden Sie die Quelle herunter, mit der Sie lokal erstellen können. [PhoneGap-CLI](https://docs.phonegap.com/references/phonegap-cli/).

![PhoneGap Build](assets/chlimage_1-60.png)

## Konfigurieren des Cloud Service {#configuring-the-cloud-service}

Um die Vorteile von PhoneGap Build nutzen zu können, müssen Sie den AEM PhoneGap Build mit Ihren PhoneGap Build-Kontoinformationen konfigurieren.

Wenn Sie derzeit kein Konto haben, navigieren Sie zu [https://build.phonegap.com](https://build.phonegap.com) und melden Sie sich an! Wenn Sie über eine Adobe Creative Cloud-Mitgliedschaft verfügen, können Sie bis zu 25 private Apps (Nicht-Open-Source-Apps) unterstützen.

Nachdem Sie überprüft haben, ob Ihr PhoneGap Build-Konto aktiv ist, navigieren Sie zu Ihrer AEM Cloud Management Console, insbesondere zum [PhoneGap Build Cloud Service](http://localhost:4502/etc/cloudservices/phonegap-build.html) (http://localhost:4502/etc/cloudservices/phonegap-build.html).

Verwenden Sie die **Cloud Services verwalten** -Kachel zum Konfigurieren einer neuen Cloud Service-Konfiguration.

### Verwenden der Kachel Cloud Services verwalten {#using-manage-cloud-services-tile}

Bevor Sie mit der Erstellung Ihrer App beginnen, verwenden Sie **PhoneGap Build** -Kachel müssen Sie Ihre Cloud-Services mithilfe der **Cloud Services verwalten** im AEM Mobile-Dashboard.

Gehen Sie wie folgt vor, um Cloud-Services für Ihre App zu konfigurieren:

1. Klicken Sie oben rechts im **Cloud Services verwalten** Kachel.

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Auswählen **PhoneGap Build** -Option **Cloud Service hinzufügen oder bearbeiten** angezeigt.

   Klicken Sie auf **Weiter**.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Geben Sie Ihre Anmeldedaten ein, um eine neue Cloud-Konfiguration zu erstellen.

   Klicken Sie nach der Überprüfung auf **Einsenden**. Diese konfigurierte Cloud-Konfiguration wird jetzt im **Cloud Services verwalten** Kachel.

   ![chlimage_1-63](assets/chlimage_1-63.png)

### Erstellen einer Anwendung mit PhoneGap Build {#building-your-application-with-phonegap-build}

Nachdem Sie die Cloud-Services konfiguriert haben, können Sie Ihre Anwendung mit **PhoneGap Build** Kachel. Klicken Sie oben rechts auf , um aus dem **Remote-Build** oder **Quelle herunterladen** Optionen.

![chlimage_1-64](assets/chlimage_1-64.png)

Um einen Remote-Build mit Adobe PhoneGap Build aufzurufen, klicken Sie auf **Remote-Build**.

>[!NOTE]
>
>Wenn der Build aus irgendeinem Grund fehlschlägt (das rote iOS-Symbol unten zeigt an, dass die Plattform fehlgeschlagen ist), können Sie den Mauszeiger über das Symbol bewegen, um die Fehlermeldung zu erhalten. Alternativ können Sie auf den dreifachen Punkt &#39;...&#39; klicken unten in der Kachel, um direkt zu https://build.phonegap.com zu navigieren (Sie müssen sich authentifizieren) und Ihren Build direkt zu beobachten und zu verwalten.

### Erstellen Ihrer Anwendung mit PhoneGap CLI {#building-your-application-with-phonegap-cli}

PhoneGap bietet eine Befehlszeilenschnittstelle zum lokalen Erstellen Ihrer Anwendung.

Kompilieren Sie die PhoneGap-Anwendung mithilfe der PhoneGap-Befehlszeilenschnittstelle (CLI) auf Ihrem Computer. Um den AEM Inhalt in Ihre Anwendung aufzunehmen, erstellt AEM eine ZIP-Datei, die den Inhalt Ihrer Mobile App, Konfigurationen zur Inhaltssynchronisierung und andere erforderliche Assets enthält. Laden Sie die ZIP-Datei herunter und fügen Sie sie in Ihren Build ein.

Um die Befehlszeilenschnittstelle von PhoneGap nutzen zu können, müssen Sie Ihre lokale Umgebung so einrichten, dass Folgendes enthalten ist:

1. Platform SDK (iOS, Android, Windows Phone, ...) und
1. PhoneGap-CLI

Weitere Informationen [here](https://docs.phonegap.com/references/phonegap-cli/).

Nachdem Sie die Voraussetzungen installiert haben, testen Sie sie anhand eines einfachen Tests, indem Sie eine einfache App erstellen und sie entweder in Ihrem Simulator oder besser auf Ihrem Gerät ausführen lassen, und zwar von einem Terminal aus:

```xml
phonegap create myApp
cd myApp
phonegap run ios (or android, ...)
```

>[!NOTE]
>
>Fügen Sie am Ende dieser Zeile —emulate hinzu, wenn Sie sie nicht auf Ihrem verbundenen Gerät ausführen möchten.

Nachdem Sie überprüft haben, ob die oben genannten Funktionen funktionieren, verwenden Sie die **PhoneGap Build** Kachel zu **Quelle herunterladen**. Speichern und entpacken Sie die Datei auf Ihrem lokalen System. Danach:

* Navigieren zu dieser gespeicherten Datei (Ordner)
* Führen Sie &#39;phonegap run ios&#39; aus (oder android usw.)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Autoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Authoring für Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md)
